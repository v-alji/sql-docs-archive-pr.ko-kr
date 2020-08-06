---
title: 대량 가져오기 또는 대량 내보내기를 위한 데이터 형식(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- data formats [SQL Server], choosing
- bulk importing [SQL Server], data formats
ms.assetid: 73fe6741-9437-4b26-b030-28b863e74399
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1b92ac8c038362ff18a1459a8bf3c55b6b596a17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638769"
---
# <a name="data-formats-for-bulk-import-or-bulk-export-sql-server"></a><span data-ttu-id="d1532-102">대량 가져오기 또는 대량 내보내기를 위한 데이터 형식(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d1532-102">Data Formats for Bulk Import or Bulk Export (SQL Server)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d1532-103">에서는 문자 데이터 형식 또는 네이티브 이진 데이터 형식으로 데이터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1532-103">can accept data in character data format or native binary data format.</span></span> <span data-ttu-id="d1532-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 다른 애플리케이션(예: [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel) 또는 다른 데이터베이스 서버(예: Oracle 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) 간에 데이터를 이동할 때 문자 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d1532-104">Use character format when you move data between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and another application (such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel) or another database server (such as Oracle or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]).</span></span> <span data-ttu-id="d1532-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 인스턴스 간에 데이터를 전송할 때만 네이티브 형식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1532-105">You can use native format only when you transfer data between instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d1532-106">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="d1532-106">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="d1532-107">대량 내보내기 또는 가져오기를 위한 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="d1532-107">Data Formats for Bulk Import or Export</span></span>](#ComponentsAndConcepts)  
  
-   [<span data-ttu-id="d1532-108">관련 작업</span><span class="sxs-lookup"><span data-stu-id="d1532-108">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="data-formats-for-bulk-import-or-export"></a><a name="ComponentsAndConcepts"></a> <span data-ttu-id="d1532-109">대량 내보내기 또는 가져오기를 위한 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="d1532-109">Data Formats for Bulk Import or Export</span></span>  
 <span data-ttu-id="d1532-110">다음 표에서는 데이터 표시 방식 및 작업의 원본 또는 대상에 따라 일반적으로 적절히 사용할 수 있는 데이터 형식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d1532-110">The following table indicates what data format is generally appropriate to use depending on how the data is represented and the source or target of the operation.</span></span>  
  
|<span data-ttu-id="d1532-111">작업(Operation)</span><span class="sxs-lookup"><span data-stu-id="d1532-111">Operation</span></span>|<span data-ttu-id="d1532-112">네이티브</span><span class="sxs-lookup"><span data-stu-id="d1532-112">Native</span></span>|<span data-ttu-id="d1532-113">유니코드 네이티브</span><span class="sxs-lookup"><span data-stu-id="d1532-113">Unicode native</span></span>|<span data-ttu-id="d1532-114">문자</span><span class="sxs-lookup"><span data-stu-id="d1532-114">Character</span></span>|<span data-ttu-id="d1532-115">유니코드 문자</span><span class="sxs-lookup"><span data-stu-id="d1532-115">Unicode character</span></span>|  
|---------------|------------|--------------------|---------------|-----------------------|  
|<span data-ttu-id="d1532-116">확장 또는 DBCS(더블바이트 문자 집합) 문자가 들어 있지 않는 데이터 파일을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 다수 인스턴스 간에 데이터를 대량으로 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="d1532-116">Bulk transfers of data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a data file that does not contain any extended or double-byte character set (DBCS) characters.</span></span> <span data-ttu-id="d1532-117">서식 파일을 사용하지 않는 한 테이블을 동일하게 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1532-117">Unless a format file is used, these tables must be identically defined.</span></span>|<span data-ttu-id="d1532-118">예<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d1532-118">Yes<sup>1</sup></span></span>|-|-|-|  
|<span data-ttu-id="d1532-119">`sql_variant` 열의 경우 문자 또는 유니코드 형식과는 달리 네이티브 데이터 형식이 각 `sql_variant` 값에 대해 메타데이터를 보존하기 때문에 네이티브 데이터 형식을 사용하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d1532-119">For `sql_variant` columns, use of native data format is best, because native data format preserves the metadata for each `sql_variant` value, unlike character or Unicode formats.</span></span>|<span data-ttu-id="d1532-120">예</span><span class="sxs-lookup"><span data-stu-id="d1532-120">Yes</span></span>|-|-|-|  
|<span data-ttu-id="d1532-121">확장 또는 DBCS 문자가 들어 있는 데이터 파일을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 다수 인스턴스 간에 데이터를 대량으로 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="d1532-121">Bulk transfers of data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a data file that contains extended or DBCS characters.</span></span>|-|<span data-ttu-id="d1532-122">예</span><span class="sxs-lookup"><span data-stu-id="d1532-122">Yes</span></span>|-|-|  
|<span data-ttu-id="d1532-123">다른 프로그램으로 생성된 텍스트 파일에서 데이터를 대량으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d1532-123">Bulk import of data from a text file that is generated by another program.</span></span>|-|-|<span data-ttu-id="d1532-124">예</span><span class="sxs-lookup"><span data-stu-id="d1532-124">Yes</span></span>|-|  
|<span data-ttu-id="d1532-125">다른 프로그램에서 사용할 텍스트 파일로 데이터를 대량으로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="d1532-125">Bulk export of data to a text file that is to be used in another program.</span></span>|-|-|<span data-ttu-id="d1532-126">예</span><span class="sxs-lookup"><span data-stu-id="d1532-126">Yes</span></span>|-|  
|<span data-ttu-id="d1532-127">유니코드 데이터가 들어 있으나 확장 또는 DBCS 문자는 들어 있지 않는 데이터 파일을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 다수 인스턴스 간에 데이터를 대량으로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="d1532-127">Bulk transfers of data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a data file that contains Unicode data and does not contain any extended or DBCS characters.</span></span>|-|-|-|<span data-ttu-id="d1532-128">예</span><span class="sxs-lookup"><span data-stu-id="d1532-128">Yes</span></span>|  
  
 <span data-ttu-id="d1532-129"><sup>1</sup> 가장 빠른 방법으로 bcp를 사용 하는 경우에서 데이터를 대량으로 내보냅니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . **bcp**</span><span class="sxs-lookup"><span data-stu-id="d1532-129"><sup>1</sup> Fastest method for the bulk export of data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] when using **bcp**.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="d1532-130">관련 작업</span><span class="sxs-lookup"><span data-stu-id="d1532-130">Related Tasks</span></span>  
  
-   [<span data-ttu-id="d1532-131">네이티브 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d1532-131">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="d1532-132">문자 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d1532-132">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="d1532-133">유니코드 네이티브 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d1532-133">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="d1532-134">유니코드 문자 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d1532-134">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="d1532-135">SQL Server 이전 버전으로부터 기본 및 문자 형식 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="d1532-135">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="d1532-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d1532-136">See Also</span></span>  
 <span data-ttu-id="d1532-137">[데이터 형식&#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d1532-137">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 [<span data-ttu-id="d1532-138">bcp를 사용하여 데이터 형식을 호환 가능하도록 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d1532-138">Specify Data Formats for Compatibility when Using bcp &#40;SQL Server&#41;</span></span>](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)  
  
  
