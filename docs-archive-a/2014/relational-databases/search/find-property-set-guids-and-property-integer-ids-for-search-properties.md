---
title: 검색 속성의 속성 집합 GUID 및 속성 정수 ID 찾기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- search property lists [SQL Server], configuring
ms.assetid: 7db79165-8bcc-4be6-8d40-12d44deda79f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 53c08d3a2f86c7e412fbdb1caa6d55d7d23bf407
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732527"
---
# <a name="find-property-set-guids-and-property-integer-ids-for-search-properties"></a><span data-ttu-id="7ebde-102">검색 속성의 속성 집합 GUID 및 속성 정수 ID찾기</span><span class="sxs-lookup"><span data-stu-id="7ebde-102">Find Property Set GUIDs and Property Integer IDs for Search Properties</span></span>
  <span data-ttu-id="7ebde-103">이 항목에서는 검색 속성 목록에 속성을 추가하고 전체 텍스트 검색으로 검색할 수 있도록 설정하기 전에 필요한 값을 가져오는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-103">This topic discusses how to obtain the values that are required before you can add a property to a search property list and make it searchable by full-text search.</span></span> <span data-ttu-id="7ebde-104">이러한 값에는 문서 속성의 속성 집합 GUID와 속성 정수 식별자가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-104">These values include the property set GUID and property integer identifier of a document property.</span></span>  
  
 <span data-ttu-id="7ebde-105">이진 데이터에서 Ifilter로 추출 된 문서 속성 `varbinary` (즉, `varbinary(max)` 포함 `FILESTREAM` ) 또는 데이터 형식 열에 저장 된 데이터에서 `image` 전체 텍스트 검색에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-105">Document properties that are extracted by IFilters from binary data - that is, from data stored in a `varbinary`, `varbinary(max)` (including `FILESTREAM`), or `image` data type column - can be made available for full-text search.</span></span> <span data-ttu-id="7ebde-106">추출된 속성을 검색할 수 있도록 설정하려면 속성을 검색 속성 목록에 수동으로 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-106">To make an extracted property searchable, the property must be manually added to a search property list.</span></span> <span data-ttu-id="7ebde-107">또한 검색 속성 목록은 하나 이상의 전체 텍스트 인덱스와 연결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-107">The search property list must also be associated with one or more full-text indexes.</span></span> <span data-ttu-id="7ebde-108">자세한 내용은 [검색 속성 목록을 사용하여 문서 속성 검색](search-document-properties-with-search-property-lists.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ebde-108">For more information, see [Search Document Properties with Search Property Lists](search-document-properties-with-search-property-lists.md).</span></span>  
  
 <span data-ttu-id="7ebde-109">사용 가능한 속성을 속성 목록에 추가하려면 먼저 속성에 대한 다음 두 가지 정보를 찾아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-109">Before you can add an available property to a property list, you have to find 2 pieces of information about the property:</span></span>  
  
-   <span data-ttu-id="7ebde-110">속성의 속성 집합 GUID</span><span class="sxs-lookup"><span data-stu-id="7ebde-110">The property set GUID of the property.</span></span>  
  
-   <span data-ttu-id="7ebde-111">속성의 정수 ID</span><span class="sxs-lookup"><span data-stu-id="7ebde-111">The integer ID of the property.</span></span>  
  
 <span data-ttu-id="7ebde-112">속성 목록에 속성을 추가할 때 이름과 설명도 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-112">(When you add a property to a property list, you also have to provide a name and description.</span></span> <span data-ttu-id="7ebde-113">그러나 속성의 정식 이름과 설명을 사용할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-113">However you do not have to use the canonical name and description of the property.)</span></span>  
  
 <span data-ttu-id="7ebde-114">이 항목에서는 사용 가능한 속성, 특히 Microsoft에서 정의한 속성에 대한 정보를 찾기 위해 일반적으로 사용되는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-114">This topic describes the commonly-used methods to find information about available properties, especially about properties that are defined by Microsoft.</span></span> <span data-ttu-id="7ebde-115">타사에서 정의한 속성에 대한 자세한 내용은 타사 설명서를 참조하거나 해당 공급업체에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="7ebde-115">For information about properties that have been defined by a third party, refer to the third-party documentation or contact the vendor.</span></span>  
  
##  <a name="finding-information-about-widely-used-well-known-microsoft-properties"></a><a name="wellknown"></a> <span data-ttu-id="7ebde-116">널리 사용되고 잘 알려진 Microsoft 속성에 대한 정보 찾기</span><span class="sxs-lookup"><span data-stu-id="7ebde-116">Finding Information about Widely Used, Well-Known Microsoft Properties</span></span>  
 <span data-ttu-id="7ebde-117">Microsoft에서는 여러 컨텍스트에서 사용할 수 있도록 수백 개의 문서 속성을 정의하지만 각 파일 형식에서는 사용 가능한 속성 중 일부만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-117">Microsoft defines hundreds of document properties for use in many contexts, but only a small subset of the available properties are used by each file format.</span></span> <span data-ttu-id="7ebde-118">자주 사용되는 Windows 속성 중에는 작은 일반 속성 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-118">Among the frequently used Windows properties is a small set of generic properties.</span></span> <span data-ttu-id="7ebde-119">다음 표에서는 잘 알려진 일반 속성의 몇 가지 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-119">Some examples of well-known generic properties are shown in the following table.</span></span> <span data-ttu-id="7ebde-120">이 표에는 잘 알려진 이름, Windows 정식 이름(Microsoft에서 게시한 속성 설명에 포함됨), 속성 집합 GUID, 속성 정수 식별자 및 간단한 설명이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-120">The table shows the well-known name, the Windows canonical name (from the property description published by Microsoft), the property set GUID, the property integer identifier, and a brief description.</span></span>  
  
|<span data-ttu-id="7ebde-121">잘 알려진 이름</span><span class="sxs-lookup"><span data-stu-id="7ebde-121">Well-known name</span></span>|<span data-ttu-id="7ebde-122">Windows 정식 이름</span><span class="sxs-lookup"><span data-stu-id="7ebde-122">Windows canonical name</span></span>|<span data-ttu-id="7ebde-123">속성 집합 GUID</span><span class="sxs-lookup"><span data-stu-id="7ebde-123">Property set GUID</span></span>|<span data-ttu-id="7ebde-124">정수 ID</span><span class="sxs-lookup"><span data-stu-id="7ebde-124">Integer ID</span></span>|<span data-ttu-id="7ebde-125">Description</span><span class="sxs-lookup"><span data-stu-id="7ebde-125">Description</span></span>|  
|----------------------|----------------------------|-----------------------|----------------|-----------------|  
|<span data-ttu-id="7ebde-126">Authors</span><span class="sxs-lookup"><span data-stu-id="7ebde-126">Authors</span></span>|`System.Author`|<span data-ttu-id="7ebde-127">F29F85E0-4FF9-1068-AB91-08002B27B3D9</span><span class="sxs-lookup"><span data-stu-id="7ebde-127">F29F85E0-4FF9-1068-AB91-08002B27B3D9</span></span>|<span data-ttu-id="7ebde-128">4</span><span class="sxs-lookup"><span data-stu-id="7ebde-128">4</span></span>|<span data-ttu-id="7ebde-129">지정된 항목의 작성자입니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-129">Author or authors of a given item.</span></span>|  
|<span data-ttu-id="7ebde-130">태그들</span><span class="sxs-lookup"><span data-stu-id="7ebde-130">Tags</span></span>|`System.Keywords`|<span data-ttu-id="7ebde-131">F29F85E0-4FF9-1068-AB91-08002B27B3D9</span><span class="sxs-lookup"><span data-stu-id="7ebde-131">F29F85E0-4FF9-1068-AB91-08002B27B3D9</span></span>|<span data-ttu-id="7ebde-132">5</span><span class="sxs-lookup"><span data-stu-id="7ebde-132">5</span></span>|<span data-ttu-id="7ebde-133">항목에 할당된 키워드(태그라고도 함) 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-133">Set of keywords (also known as tags) assigned to the item.</span></span>|  
|<span data-ttu-id="7ebde-134">Type</span><span class="sxs-lookup"><span data-stu-id="7ebde-134">Type</span></span>|`System.PerceivedType`|<span data-ttu-id="7ebde-135">28636AA6-953D-11D2-B5D6-00C04FD918D0</span><span class="sxs-lookup"><span data-stu-id="7ebde-135">28636AA6-953D-11D2-B5D6-00C04FD918D0</span></span>|<span data-ttu-id="7ebde-136">9</span><span class="sxs-lookup"><span data-stu-id="7ebde-136">9</span></span>|<span data-ttu-id="7ebde-137">정식 유형을 기반으로 인식되는 파일 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-137">Perceived file type based on its canonical type.</span></span>|  
|<span data-ttu-id="7ebde-138">title</span><span class="sxs-lookup"><span data-stu-id="7ebde-138">Title</span></span>|`System.Title`|<span data-ttu-id="7ebde-139">F29F85E0-4FF9-1068-AB91-08002B27B3D9</span><span class="sxs-lookup"><span data-stu-id="7ebde-139">F29F85E0-4FF9-1068-AB91-08002B27B3D9</span></span>|<span data-ttu-id="7ebde-140">2</span><span class="sxs-lookup"><span data-stu-id="7ebde-140">2</span></span>|<span data-ttu-id="7ebde-141">항목의 제목입니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-141">Title of the item.</span></span> <span data-ttu-id="7ebde-142">예를 들어 문서의 제목, 메시지의 제목, 사진의 캡션 또는 음악 트랙의 이름이 여기에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-142">For example, the title of a document, the subject of a message, the caption of a photo, or the name of a music track.</span></span>|  
  
 <span data-ttu-id="7ebde-143">파일 형식 간 일관성을 유지하기 위해 Microsoft에서는 몇 가지 문서 범주에 대해 자주 사용되고 우선 순위가 높은 문서 속성의 하위 집합을 식별했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-143">To encourage consistency among file formats, Microsoft has identified subsets of frequently used, high-priority document properties for several categories of documents.</span></span> <span data-ttu-id="7ebde-144">여기에는 통신, 연락처, 문서, 음악 파일, 그림 및 동영상이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-144">These include communications, contacts, documents, music files, pictures, and videos.</span></span> <span data-ttu-id="7ebde-145">각 범주에서 순위가 높은 속성에 대한 자세한 내용은 Windows Search 설명서에서 [사용자 지정 파일 형식에 대한 시스템 정의 속성](https://go.microsoft.com/fwlink/?LinkId=144336) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ebde-145">For more information about the top-ranked properties for each category, see [system-defined properties for custom file formats](https://go.microsoft.com/fwlink/?LinkId=144336) in the Windows Search documentation.</span></span>  
  
 <span data-ttu-id="7ebde-146">특정 파일 형식은 세 가지 유형의 속성을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-146">A specific file format might implement properties of three types:</span></span>  
  
-   <span data-ttu-id="7ebde-147">[!INCLUDE[msCoName](../../includes/msconame-md.md)]에서 정의한 일반 속성</span><span class="sxs-lookup"><span data-stu-id="7ebde-147">Generic properties defined by [!INCLUDE[msCoName](../../includes/msconame-md.md)].</span></span>  
  
-   <span data-ttu-id="7ebde-148">[!INCLUDE[msCoName](../../includes/msconame-md.md)]에서 정의한 범주별 속성</span><span class="sxs-lookup"><span data-stu-id="7ebde-148">Category-specific properties defined by [!INCLUDE[msCoName](../../includes/msconame-md.md)].</span></span>  
  
-   <span data-ttu-id="7ebde-149">소프트웨어 공급업체에서 정의한 애플리케이션별 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="7ebde-149">Custom, application-specific properties defined by the software vendor.</span></span>  
  
##  <a name="finding-information-about-available-properties-by-using-filtdumpexe"></a><a name="filtdump"></a> <span data-ttu-id="7ebde-150">FILTDUMP.EXE를 사용하여 사용 가능한 속성에 대한 정보 찾기</span><span class="sxs-lookup"><span data-stu-id="7ebde-150">Finding Information about Available Properties by using FILTDUMP.EXE</span></span>  
 <span data-ttu-id="7ebde-151">설치된 IFilter를 통해 검색되고 추출된 속성을 알아 보려면 **Windows SDK의 일부인** filtdump.exe [!INCLUDE[msCoName](../../includes/msconame-md.md)] 유틸리티를 설치하고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-151">To learn what properties are discovered and extracted by an installed IFilter, you can install and run the **filtdump.exe** utility, which is part of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows SDK.</span></span>  
  
 <span data-ttu-id="7ebde-152">명령 프롬프트에서 **filtdump.exe** 를 실행하고 단일 인수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-152">You run **filtdump.exe** from the command prompt and provide a single argument.</span></span> <span data-ttu-id="7ebde-153">이 인수는 IFilter가 설치된 파일 형식을 사용하는 개별 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-153">This argument is the name of an individual file that has a file type for which an IFilter is installed.</span></span> <span data-ttu-id="7ebde-154">이 유틸리티는 문서에서 IFilter를 통해 검색된 모든 속성의 목록을 속성 집합 GUID, 정수 ID 및 추가 정보와 함께 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-154">The utility displays a list of all the properties discovered by the IFilter in the document, with their property set GUIDs, integer IDs, and additional information.</span></span>  
  
 <span data-ttu-id="7ebde-155">이 소프트웨어 설치에 대한 자세한 내용은 [Windows 7 및 .NET Framework 4용 Microsoft Windows SDK](https://www.microsoft.com/download/details.aspx?id=8279)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7ebde-155">For information about installing this software, see [Microsoft Windows SDK for Windows 7 and .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=8279).</span></span> <span data-ttu-id="7ebde-156">SDK를 다운로드하여 설치한 후 다음 폴더에서 filtdump.exe 유틸리티를 찾으십시오.</span><span class="sxs-lookup"><span data-stu-id="7ebde-156">After you download and install the SDK, look in the following folders for the filtdump.exe utility.</span></span>  
  
-   <span data-ttu-id="7ebde-157">64비트 버전의 경우 `C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\x64`을 찾아봅니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-157">For the 64-bit version, look in `C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\x64`.</span></span>  
  
-   <span data-ttu-id="7ebde-158">32비트 버전의 경우 `C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin`을 찾아봅니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-158">For the 32-bit version, look in `C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin`.</span></span>  
  
##  <a name="finding-values-for-a-search-property-from-a-windows-property-description"></a><a name="propdesc"></a><span data-ttu-id="7ebde-159">Windows 속성 설명에서 검색 속성 값 찾기</span><span class="sxs-lookup"><span data-stu-id="7ebde-159">Finding Values for a Search Property from a Windows Property Description</span></span>  
 <span data-ttu-id="7ebde-160">잘 알려진 Windows 검색 속성의 경우 속성 설명(`formatID`)의 `propID` 및 `propertyDescription` 특성에서 필요한 정보를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-160">For a well-known Windows search property, you can obtain the information that you need from the `formatID` and `propID` attributes of the property description (`propertyDescription`).</span></span>  
  
 <span data-ttu-id="7ebde-161">다음 예에서는 일반적인 Microsoft 속성(이 경우 `System.Author` 속성) 설명의 관련 부분을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-161">The following example shows the relevant part of a typical Microsoft property description, in this case, of the `System.Author` property.</span></span> <span data-ttu-id="7ebde-162">`formatID` 특성은 속성 집합 GUID로 `F29F85E0-4FF9-1068-AB91-08002B27B3D9`를 지정하고, `propID` 특성은 속성 정수 ID로 `4.` 를 지정합니다. `name` 특성은 Windows 정식 속성 이름으로 `System.Author`를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-162">The `formatID` attribute specifies the property set GUID, `F29F85E0-4FF9-1068-AB91-08002B27B3D9`, and the `propID` attribute specifies the property integer ID, `4.` Notice that the `name` attribute specifies the Windows canonical property name, `System.Author`.</span></span> <span data-ttu-id="7ebde-163">이 예에서는 관련되지 않은 속성 설명의 부분을 생략합니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-163">(This example omits portions of the property description that are not relevant.)</span></span>  
  
```  
.  
propertyDescription  
name = System.Author  
...  
formatID = F29F85E0-4FF9-1068-AB91-08002B27B3D9  
propID = 4  
...  
```  
  
 <span data-ttu-id="7ebde-164">이 속성의 전체 설명은 Windows 검색 설명서에서 [System.Author](https://go.microsoft.com/fwlink/?LinkId=144337)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7ebde-164">For the complete description of this property, see [System.Author](https://go.microsoft.com/fwlink/?LinkId=144337) in the Windows Search documentation.</span></span>  
  
 <span data-ttu-id="7ebde-165">Windows 속성의 전체 목록을 보려면 Windows 검색 설명서에서 [Windows 속성](https://go.microsoft.com/fwlink/?LinkId=215013)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7ebde-165">For a complete list of Windows properties, see [Windows Properties](https://go.microsoft.com/fwlink/?LinkId=215013), also in the Windows Search documentation.</span></span>  
  
##  <a name="adding-a-property-to-a-search-property-list"></a><a name="examples"></a><span data-ttu-id="7ebde-166">검색 속성 목록에 속성 추가</span><span class="sxs-lookup"><span data-stu-id="7ebde-166">Adding a Property to a Search Property List</span></span>  
 <span data-ttu-id="7ebde-167">다음 예에서는 속성을 검색 속성 목록에 추가하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-167">The following example shows how to add a property to a search property list.</span></span> <span data-ttu-id="7ebde-168">이 예에서는 [ALTER SEARCH PROPERTY LIST](/sql/t-sql/statements/alter-search-property-list-transact-sql) 문을 사용하여 `System.Author` 속성을 `PropertyList1`이라는 검색 속성 목록에 추가하고 속성에 `Author`라는 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7ebde-168">The example uses an [ALTER SEARCH PROPERTY LIST](/sql/t-sql/statements/alter-search-property-list-transact-sql) statement to add the `System.Author` property to a search property list named `PropertyList1`, and provides a user friendly name for the property, `Author`.</span></span>  
  
```  
ALTER SEARCH PROPERTY LIST PropertyList1   
  ADD 'Author'  
    WITH (  
          PROPERTY_SET_GUID = 'F29F85E0-4FF9-1068-AB91-08002B27B3D9',  
          PROPERTY_INT_ID = 4,   
          PROPERTY_DESCRIPTION = 'System.Author - the author or authors of the item'   
         )  
GO  
```  
  
 <span data-ttu-id="7ebde-169">검색 속성 목록을 만들어 전체 텍스트 인덱스와 연결하는 방법은 [검색 속성 목록을 사용하여 문서 속성 검색](search-document-properties-with-search-property-lists.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ebde-169">For more information about creating a search property list and associating it with a full-text index, see [Search Document Properties with Search Property Lists](search-document-properties-with-search-property-lists.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ebde-170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ebde-170">See Also</span></span>  
 <span data-ttu-id="7ebde-171">[검색 속성 목록을 사용 하 여 문서 속성 검색](search-document-properties-with-search-property-lists.md) </span><span class="sxs-lookup"><span data-stu-id="7ebde-171">[Search Document Properties with Search Property Lists](search-document-properties-with-search-property-lists.md) </span></span>  
 [<span data-ttu-id="7ebde-172">검색 필터 구성 및 관리</span><span class="sxs-lookup"><span data-stu-id="7ebde-172">Configure and Manage Filters for Search</span></span>](configure-and-manage-filters-for-search.md)  
  
  
