---
title: 유니코드 압축 구현 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Unicode data compression
- compression [SQL Server], Unicode data
ms.assetid: 44e69e60-9b35-43fe-b9c7-8cf34eaea62a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4c928062169ed7feb03f1031362530474109976a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659458"
---
# <a name="unicode-compression-implementation"></a><span data-ttu-id="962be-102">유니코드 압축 구현</span><span class="sxs-lookup"><span data-stu-id="962be-102">Unicode Compression Implementation</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="962be-103">는 SCSU(Standard Compression Scheme for Unicode) 알고리즘 구현을 사용하여 행 또는 페이지 압축 개체에 저장된 유니코드 값을 압축합니다.</span><span class="sxs-lookup"><span data-stu-id="962be-103">uses an implementation of the Standard Compression Scheme for Unicode (SCSU) algorithm to compress Unicode values that are stored in row or page compressed objects.</span></span> <span data-ttu-id="962be-104">이러한 압축 개체의 경우 `nchar(n)` 및 `nvarchar(n)` 열에 유니코드 압축이 자동으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="962be-104">For these compressed objects, Unicode compression is automatic for `nchar(n)` and `nvarchar(n)` columns.</span></span> <span data-ttu-id="962be-105">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서는 로캘에 관계없이 유니코드 데이터가 2바이트로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="962be-105">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] stores Unicode data as 2 bytes, regardless of locale.</span></span> <span data-ttu-id="962be-106">이 방식을 UCS-2 인코딩이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="962be-106">This is known as UCS-2 encoding.</span></span> <span data-ttu-id="962be-107">일부 로캘의 경우 SQL Server에서 SCSU 압축을 구현하면 스토리지 공간을 최대 50% 절약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="962be-107">For some locales, the implementation of SCSU compression in SQL Server can save up to 50 percent in storage space.</span></span>  
  
## <a name="supported-data-types"></a><span data-ttu-id="962be-108">지원되는 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="962be-108">Supported Data Types</span></span>  
 <span data-ttu-id="962be-109">유니코드 압축은 고정 길이의 `nchar(n)` 및 `nvarchar(n)` 데이터 형식을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="962be-109">Unicode compression supports the fixed-length `nchar(n)` and `nvarchar(n)` data types.</span></span> <span data-ttu-id="962be-110">행 외부 또는 `nvarchar(max)` 열에 저장된 데이터 값은 압축되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="962be-110">Data values that are stored off row or in `nvarchar(max)` columns are not compressed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="962be-111">`nvarchar(max)` 데이터는 행에 저장되어 있더라도 유니코드 압축이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="962be-111">Unicode compression is not supported for `nvarchar(max)` data even if it is stored in row.</span></span> <span data-ttu-id="962be-112">하지만 이 데이터 형식에서 페이지 압축을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="962be-112">However, this data type can still benefit from page compression.</span></span>  
  
## <a name="upgrading-from-earlier-versions-of-sql-server"></a><span data-ttu-id="962be-113">이전 버전의 SQL Server에서 업그레이드</span><span class="sxs-lookup"><span data-stu-id="962be-113">Upgrading from Earlier Versions of SQL Server</span></span>  
 <span data-ttu-id="962be-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스가 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드되는 경우 유니코드 압축과 관련된 변경 내용은 압축 여부에 관계 없이 모든 데이터베이스 개체에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="962be-114">When a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database is upgraded to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], Unicode compression-related changes are not made to any database object, compressed or uncompressed.</span></span> <span data-ttu-id="962be-115">데이터베이스가 업그레이드되면 개체는 다음과 같이 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="962be-115">After the database is upgraded, objects are affected as follows:</span></span>  
  
-   <span data-ttu-id="962be-116">압축되지 않은 개체의 경우 변경 내용이 적용되지 않고 이전과 같은 방식으로 계속 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="962be-116">If the object is not compressed, no changes are made and the object continues to function as it did previously.</span></span>  
  
-   <span data-ttu-id="962be-117">행 또는 페이지 압축 개체는 이전과 같은 방식으로 계속 동작하고</span><span class="sxs-lookup"><span data-stu-id="962be-117">Row- or page-compressed objects continue to function as they did previously.</span></span> <span data-ttu-id="962be-118">압축되지 않은 데이터는 값이 업데이트될 때까지 압축되지 않은 형식으로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="962be-118">Uncompressed data remains in uncompressed form until its value is updated.</span></span>  
  
-   <span data-ttu-id="962be-119">행 또는 페이지 압축 테이블에 삽입된 새 행은 유니코드 압축을 사용하여 압축됩니다.</span><span class="sxs-lookup"><span data-stu-id="962be-119">New rows that are inserted into a row- or page-compressed table are compressed using Unicode compression.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="962be-120">유니코드 압축의 장점을 모두 활용하려면 페이지 또는 행 압축을 사용하여 개체를 다시 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="962be-120">To take full advantage of the benefits of Unicode compression, the object must be rebuilt with page or row compression.</span></span>  
  
## <a name="how-unicode-compression-affects-data-storage"></a><span data-ttu-id="962be-121">유니코드 압축이 데이터 스토리지에 주는 영향</span><span class="sxs-lookup"><span data-stu-id="962be-121">How Unicode Compression Affects Data Storage</span></span>  
 <span data-ttu-id="962be-122">인덱스를 만들거나 다시 작성하는 경우 또는 행/페이지 압축을 사용하여 압축된 테이블에서 값을 변경하는 경우 영향을 받는 인덱스나 값은 압축된 크기가 현재 크기보다 작은 경우에만 압축 형식으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="962be-122">When an index is created or rebuilt or when a value is changed in a table that was compressed with row or page compression, the affected index or value is stored compressed only if its compressed size is less than its current size.</span></span> <span data-ttu-id="962be-123">이렇게 되면 유니코드 압축 때문에 테이블의 행 또는 인덱스의 크기가 증가하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="962be-123">This prevents rows in a table or index from increasing in size because of Unicode compression.</span></span>  
  
 <span data-ttu-id="962be-124">압축을 통해 절약할 수 있는 스토리지 공간은 압축하고 있는 데이터의 특성과 데이터 로캘에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="962be-124">The storage space that compression saves depends on the characteristics of the data that is being compressed and the locale of the data.</span></span> <span data-ttu-id="962be-125">다음 표에서는 로캘별로 절약할 수 있는 저장 공간을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="962be-125">The following table lists the space savings that can be achieved for several locales.</span></span>  
  
|<span data-ttu-id="962be-126">Locale</span><span class="sxs-lookup"><span data-stu-id="962be-126">Locale</span></span>|<span data-ttu-id="962be-127">압축률</span><span class="sxs-lookup"><span data-stu-id="962be-127">Compression percent</span></span>|  
|------------|-------------------------|  
|<span data-ttu-id="962be-128">영어</span><span class="sxs-lookup"><span data-stu-id="962be-128">English</span></span>|<span data-ttu-id="962be-129">50%</span><span class="sxs-lookup"><span data-stu-id="962be-129">50%</span></span>|  
|<span data-ttu-id="962be-130">독일어</span><span class="sxs-lookup"><span data-stu-id="962be-130">German</span></span>|<span data-ttu-id="962be-131">50%</span><span class="sxs-lookup"><span data-stu-id="962be-131">50%</span></span>|  
|<span data-ttu-id="962be-132">힌디어</span><span class="sxs-lookup"><span data-stu-id="962be-132">Hindi</span></span>|<span data-ttu-id="962be-133">50%</span><span class="sxs-lookup"><span data-stu-id="962be-133">50%</span></span>|  
|<span data-ttu-id="962be-134">터키어</span><span class="sxs-lookup"><span data-stu-id="962be-134">Turkish</span></span>|<span data-ttu-id="962be-135">48%</span><span class="sxs-lookup"><span data-stu-id="962be-135">48%</span></span>|  
|<span data-ttu-id="962be-136">베트남어</span><span class="sxs-lookup"><span data-stu-id="962be-136">Vietnamese</span></span>|<span data-ttu-id="962be-137">39%</span><span class="sxs-lookup"><span data-stu-id="962be-137">39%</span></span>|  
|<span data-ttu-id="962be-138">일본어</span><span class="sxs-lookup"><span data-stu-id="962be-138">Japanese</span></span>|<span data-ttu-id="962be-139">15%</span><span class="sxs-lookup"><span data-stu-id="962be-139">15%</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="962be-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="962be-140">See Also</span></span>  
 <span data-ttu-id="962be-141">[데이터 압축](data-compression.md) </span><span class="sxs-lookup"><span data-stu-id="962be-141">[Data Compression](data-compression.md) </span></span>  
 <span data-ttu-id="962be-142">[sp_estimate_data_compression_savings&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="962be-142">[sp_estimate_data_compression_savings &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql) </span></span>  
 <span data-ttu-id="962be-143">[페이지 압축 구현](page-compression-implementation.md) </span><span class="sxs-lookup"><span data-stu-id="962be-143">[Page Compression Implementation](page-compression-implementation.md) </span></span>  
 [<span data-ttu-id="962be-144">sys.dm_db_persisted_sku_features&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="962be-144">sys.dm_db_persisted_sku_features &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-persisted-sku-features-transact-sql)  
  
  
