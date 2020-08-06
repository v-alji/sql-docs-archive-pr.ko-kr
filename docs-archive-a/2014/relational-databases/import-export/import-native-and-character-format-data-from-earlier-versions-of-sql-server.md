---
title: SQL Server 이전 버전으로부터 기본 및 문자 형식 데이터 가져오기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- earlier versions [SQL Server], import and export data formats
- -V switch
- data formats [SQL Server], earlier versions
- previous versions [SQL Server], import and export data formats
ms.assetid: e644696f-9017-428e-a5b3-d445d1c630b3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 274c984d6ecec8af8f5bea27496450a45fc2f1df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653373"
---
# <a name="import-native-and-character-format-data-from-earlier-versions-of-sql-server"></a><span data-ttu-id="c6709-102">SQL Server 이전 버전으로부터 기본 및 문자 형식 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="c6709-102">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>
  <span data-ttu-id="c6709-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 **bcp** 를 사용하면 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]-V [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]스위치를 통해 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , **또는** 에서 원시 및 문자 형식 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6709-103">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can use **bcp** to import native and character format data from [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] by using the **-V** switch.</span></span> <span data-ttu-id="c6709-104">**-V[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 스위치를 사용하면** 에서 지정된 이전 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 버전의 데이터 형식이 사용되며, 데이터 파일 형식은 해당 이전 버전의 형식과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="c6709-104">The **-V** switch causes [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to use data types from the specified earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and the data file format are the same as the format in that earlier version.</span></span>  
  
 <span data-ttu-id="c6709-105">데이터 파일에 대해 이전 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전을 지정하려면 다음 한정자 중 하나와 함께 **-V** 스위치를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c6709-105">To specify an earlier [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version for a data file, use the **-V** switch with one of the following qualifiers:</span></span>  
  
|<span data-ttu-id="c6709-106">SQL Server 버전</span><span class="sxs-lookup"><span data-stu-id="c6709-106">SQL Server version</span></span>|<span data-ttu-id="c6709-107">한정자</span><span class="sxs-lookup"><span data-stu-id="c6709-107">Qualifier</span></span>|  
|------------------------|---------------|  
|[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]|<span data-ttu-id="c6709-108">**-V80**</span><span class="sxs-lookup"><span data-stu-id="c6709-108">**-V80**</span></span>|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|<span data-ttu-id="c6709-109">**-V90**</span><span class="sxs-lookup"><span data-stu-id="c6709-109">**-V90**</span></span>|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|<span data-ttu-id="c6709-110">**-V100**</span><span class="sxs-lookup"><span data-stu-id="c6709-110">**-V100**</span></span>|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|<span data-ttu-id="c6709-111">**-V 110**</span><span class="sxs-lookup"><span data-stu-id="c6709-111">**-V 110**</span></span>|  
  
## <a name="interpretation-of-data-types"></a><span data-ttu-id="c6709-112">데이터 형식 해석</span><span class="sxs-lookup"><span data-stu-id="c6709-112">Interpretation of Data Types</span></span>  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="c6709-113">이후 버전에서는 몇 가지 새로운 형식을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c6709-113">and later versions have support for some new types.</span></span> <span data-ttu-id="c6709-114">새 데이터 형식을 이전 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전으로 가져오려면 이전 **bcp** 클라이언트에서 읽을 수 있는 형식으로 저장되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6709-114">When you want to import a new data type into an earlier [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version, the data type must be stored in a format that readable by the older **bcp** clients.</span></span> <span data-ttu-id="c6709-115">다음 표에서는 새 데이터 형식을 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 호환되도록 변환하는 방법을 요약합니다.</span><span class="sxs-lookup"><span data-stu-id="c6709-115">The following table summarizes how the new data types are converted for compatibility with the earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="c6709-116">SQL Server 2005의 새로운 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="c6709-116">New data types in SQL Server 2005</span></span>|<span data-ttu-id="c6709-117">6*x*버전의 호환 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="c6709-117">Compatible data types in version 6*x*</span></span>|<span data-ttu-id="c6709-118">70 버전의 호환 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="c6709-118">Compatible data types in version 70</span></span>|<span data-ttu-id="c6709-119">80 버전의 호환 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="c6709-119">Compatible data types in version 80</span></span>|  
|---------------------------------------|-------------------------------------------|-----------------------------------------|-----------------------------------------|  
|`bigint`|`decimal`|`decimal`|*|  
|`sql_variant`|`text`|`nvarchar(4000)`|*|  
|`varchar(max)`|`text`|`text`|`text`|  
|`nvarchar(max)`|`ntext`|`ntext`|`ntext`|  
|`varbinary(max)`|`image`|`image`|`image`|  
|<span data-ttu-id="c6709-120">XML</span><span class="sxs-lookup"><span data-stu-id="c6709-120">XML</span></span>|`ntext`|`ntext`|`ntext`|  
|<span data-ttu-id="c6709-121">UDT<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="c6709-121">UDT<sup>1</sup></span></span>|`image`|`image`|`image`|  
  
 <span data-ttu-id="c6709-122">\*이 형식은 기본적으로 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6709-122">\* This type is natively supported.</span></span>  
  
 <span data-ttu-id="c6709-123"><sup>1</sup> UDT는 사용자 정의 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6709-123"><sup>1</sup> UDT indicates a user defined type.</span></span>  
  
## <a name="exporting-using--v-80"></a><span data-ttu-id="c6709-124">–V 80을 사용하여 내보내기</span><span class="sxs-lookup"><span data-stu-id="c6709-124">Exporting using -V 80</span></span>  
 <span data-ttu-id="c6709-125">**-V80** 스위치를 사용 하 여 데이터를 대량으로 내보내는 경우 기본 `nvarchar(max)` 모드의,, `varchar(max)` `varbinary(max)` , XML 및 UDT 데이터는 `text` `image` `ntext` 이상 버전의 기본값인 8 바이트 접두사가 아니라, 및 데이터와 같은 4 바이트 접두사를 사용 하 여 저장 됩니다 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c6709-125">When you bulk export data by using the **-V80** switch, `nvarchar(max)`, `varchar(max)`, `varbinary(max)`, XML, and UDT data in native mode are stored with a 4-byte prefix, like `text`, `image`, and `ntext` data, rather than with an 8-byte prefix, which is the default for [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions.</span></span>  
  
## <a name="copying-date-values"></a><span data-ttu-id="c6709-126">날짜 값 복사</span><span class="sxs-lookup"><span data-stu-id="c6709-126">Copying Date Values</span></span>  
 <span data-ttu-id="c6709-127">**bcp** 는 ODBC 대량 복사 API를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c6709-127">**bcp** uses the ODBC bulk copy API.</span></span> <span data-ttu-id="c6709-128">따라서 데이터 값을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 가져오기 위해 **bcp** 는 ODBC 날짜 형식(*yyyy-mm-dd hh:mm:ss*[ *.f...* ])을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c6709-128">Therefore, to import date values into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], **bcp** uses the ODBC date format (*yyyy-mm-dd hh:mm:ss*[*.f...*]).</span></span>  
  
 <span data-ttu-id="c6709-129">**Bcp** 명령은 및 값에 대해 ODBC 기본 형식을 사용 하 여 문자 형식 데이터 파일을 내보냅니다 `datetime` `smalldatetime` .</span><span class="sxs-lookup"><span data-stu-id="c6709-129">The **bcp** command exports character format data files using the ODBC default format for `datetime` and `smalldatetime` values.</span></span> <span data-ttu-id="c6709-130">예를 들어 `12 Aug 1998`이라는 날짜가 포함된 `datetime` 열은 `1998-08-12 00:00:00.000` 문자열로 데이터 파일에 대량 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6709-130">For example, a `datetime` column containing the date `12 Aug 1998` is bulk copied to a data file as the character string `1998-08-12 00:00:00.000`.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c6709-131">`smalldatetime` **Bcp**를 사용 하 여 필드로 데이터를 가져올 때 초 값이 00.000 인지 확인할 수 있습니다. 그렇지 않으면 작업이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6709-131">When importing data into a `smalldatetime` field using **bcp**, be sure the value for seconds is 00.000; otherwise the operation will fail.</span></span> <span data-ttu-id="c6709-132">`smalldatetime` 데이터 형식은 가장 근접한 분 값만 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="c6709-132">The `smalldatetime` data type only holds values to the nearest minute.</span></span> <span data-ttu-id="c6709-133">이 경우 BULK INSERT 및 INSERT ... SELECT \* FROM OPENROWSET(BULK...)는 이 경우 실패하지 않지만 초 값이 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="c6709-133">BULK INSERT and INSERT ... SELECT \* FROM OPENROWSET(BULK...) will not fail in this instance but will truncate the seconds value.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="c6709-134">관련 작업</span><span class="sxs-lookup"><span data-stu-id="c6709-134">Related Tasks</span></span>  
 <span data-ttu-id="c6709-135">**대량 가져오기 또는 대량 내보내기를 위한 데이터 형식을 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="c6709-135">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="c6709-136">문자 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c6709-136">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="c6709-137">네이티브 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c6709-137">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="c6709-138">유니코드 문자 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c6709-138">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="c6709-139">유니코드 네이티브 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c6709-139">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 
  
## <a name="see-also"></a><span data-ttu-id="c6709-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6709-140">See Also</span></span>  
 <span data-ttu-id="c6709-141">[bcp 유틸리티](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="c6709-141">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="c6709-142">[BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c6709-142">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="c6709-143">[OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c6709-143">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="c6709-144">[데이터 형식&#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c6709-144">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 <span data-ttu-id="c6709-145">[SQL Server 데이터베이스 엔진의 이전 버전과의 호환성](../../database-engine/sql-server-database-engine-backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="c6709-145">[SQL Server Database Engine Backward Compatibility](../../database-engine/sql-server-database-engine-backward-compatibility.md) </span></span>  
 [<span data-ttu-id="c6709-146">CAST 및 CONVERT&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c6709-146">CAST and CONVERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/cast-and-convert-transact-sql)  
  
  
