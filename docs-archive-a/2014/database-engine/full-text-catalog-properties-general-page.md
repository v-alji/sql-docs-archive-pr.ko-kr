---
title: 전체 텍스트 카탈로그 속성 (일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftcatalogproperties.general.f1
ms.assetid: d1f66762-2d40-4f24-b635-a417d22ee79a
author: rothja
ms.author: jroth
ms.openlocfilehash: 483601c53db6c8a806ea8c53f771fd4f2608293b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740300"
---
# <a name="full-text-catalog-properties-general-page"></a><span data-ttu-id="3f840-102">전체 텍스트 카탈로그 속성(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="3f840-102">Full-Text Catalog Properties (General Page)</span></span>
  <span data-ttu-id="3f840-103">이 섹션에서는 **전체 텍스트 카탈로그 속성** 대화 상자의 **일반** 페이지에서 사용할 수 있는 옵션과 기능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3f840-103">This section shows the options and functions available on the **General** page of the **Full-Text Catalog Properties** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3f840-104">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 데이터베이스에서 전체 텍스트 카탈로그는 전체 텍스트 인덱스 그룹을 나타내는 논리적 개념입니다.</span><span class="sxs-lookup"><span data-stu-id="3f840-104">For [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] databases, a full-text catalog is a logical concept that refers to a group of full-text indexes.</span></span> <span data-ttu-id="3f840-105">전체 텍스트 카탈로그는 어떠한 파일 그룹에도 속하지 않는 가상 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="3f840-105">The full-text catalog is a virtual object that does not belong to any filegroup.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3f840-106">옵션</span><span class="sxs-lookup"><span data-stu-id="3f840-106">Options</span></span>  
  
### <a name="properties"></a><span data-ttu-id="3f840-107">속성</span><span class="sxs-lookup"><span data-stu-id="3f840-107">Properties</span></span>  
 <span data-ttu-id="3f840-108">**기본 카탈로그**</span><span class="sxs-lookup"><span data-stu-id="3f840-108">**Default Catalog**</span></span>  
 <span data-ttu-id="3f840-109">카탈로그가 데이터베이스의 기본 카탈로그인지 여부를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3f840-109">Displays whether the catalog is the default catalog for the database.</span></span>  
  
 <span data-ttu-id="3f840-110">**채우기 상태**</span><span class="sxs-lookup"><span data-stu-id="3f840-110">**Population Status**</span></span>  
 <span data-ttu-id="3f840-111">카탈로그의 상태를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3f840-111">Indicates the status of the catalog.</span></span> <span data-ttu-id="3f840-112">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3f840-112">Possible values are:</span></span>  
  
-   <span data-ttu-id="3f840-113">**유휴 상태**</span><span class="sxs-lookup"><span data-stu-id="3f840-113">**Idle**</span></span>  
  
-   <span data-ttu-id="3f840-114">**탐색 진행 중**</span><span class="sxs-lookup"><span data-stu-id="3f840-114">**Crawl in Progress**</span></span>  
  
-   <span data-ttu-id="3f840-115">**일시 중지됨**</span><span class="sxs-lookup"><span data-stu-id="3f840-115">**Paused**</span></span>  
  
-   <span data-ttu-id="3f840-116">**정체됨**</span><span class="sxs-lookup"><span data-stu-id="3f840-116">**Throttled**</span></span>  
  
-   <span data-ttu-id="3f840-117">**복구**</span><span class="sxs-lookup"><span data-stu-id="3f840-117">**Recovering**</span></span>  
  
-   <span data-ttu-id="3f840-118">**종료**</span><span class="sxs-lookup"><span data-stu-id="3f840-118">**Shutdown**</span></span>  
  
-   <span data-ttu-id="3f840-119">**증분 채우기 진행 중**</span><span class="sxs-lookup"><span data-stu-id="3f840-119">**Incremental population in progress**</span></span>  
  
-   <span data-ttu-id="3f840-120">**인덱스 작성 중**</span><span class="sxs-lookup"><span data-stu-id="3f840-120">**Building index**</span></span>  
  
-   <span data-ttu-id="3f840-121">**디스크가 꽉 참-일시 중지 됨**</span><span class="sxs-lookup"><span data-stu-id="3f840-121">**Disk is full-Paused**</span></span>  
  
-   <span data-ttu-id="3f840-122">**Change tracking**</span><span class="sxs-lookup"><span data-stu-id="3f840-122">**Change tracking**</span></span>  
  
 <span data-ttu-id="3f840-123">**항목 개수**</span><span class="sxs-lookup"><span data-stu-id="3f840-123">**Item Count**</span></span>  
 <span data-ttu-id="3f840-124">카탈로그의 전체 텍스트 항목 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3f840-124">Displays the number of full-text items in the catalog.</span></span>  
  
 <span data-ttu-id="3f840-125">**카탈로그 크기**</span><span class="sxs-lookup"><span data-stu-id="3f840-125">**Catalog Size**</span></span>  
 <span data-ttu-id="3f840-126">전체 텍스트 카탈로그의 크기(MB)를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3f840-126">Displays the size, in megabytes, of the full-text catalog.</span></span>  
  
 <span data-ttu-id="3f840-127">**이름**</span><span class="sxs-lookup"><span data-stu-id="3f840-127">**Name**</span></span>  
 <span data-ttu-id="3f840-128">전체 텍스트 카탈로그의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="3f840-128">The name of the full-text catalog.</span></span>  
  
 <span data-ttu-id="3f840-129">**악센트 구분**</span><span class="sxs-lookup"><span data-stu-id="3f840-129">**Accent Sensitive**</span></span>  
 <span data-ttu-id="3f840-130">카탈로그가 물결표 ( **~** ), 악센트 부호 (**́**) 또는 움라우트 (?)와 같은 분음 부호를 구분 하는지 여부를 확인 하거나 수정 합니다.**¨**</span><span class="sxs-lookup"><span data-stu-id="3f840-130">View or modify whether the catalog is sensitive to diacritical marks, such as a tilde (**~**), acute accent mark (**´**), or umlaut (**¨**).</span></span> <span data-ttu-id="3f840-131">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3f840-131">Valid values are:</span></span>  
  
-   <span data-ttu-id="3f840-132">**아니요**</span><span class="sxs-lookup"><span data-stu-id="3f840-132">**No**</span></span>  
  
-   <span data-ttu-id="3f840-133">**예**</span><span class="sxs-lookup"><span data-stu-id="3f840-133">**Yes**</span></span>  
  
-   <span data-ttu-id="3f840-134">분음 부호에 대 한 자세한 내용은 Merriam-Webster 사전의 [분음 부호](https://www.merriam-webster.com/dictionary/diacritic) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3f840-134">For information about diacritical marks, see [Diacritic](https://www.merriam-webster.com/dictionary/diacritic) in the Merriam-Webster dictionary.</span></span>  
  
 <span data-ttu-id="3f840-135">**마지막 채우기 날짜**</span><span class="sxs-lookup"><span data-stu-id="3f840-135">**Last Population Date**</span></span>  
 <span data-ttu-id="3f840-136">마지막으로 카탈로그를 채운 날짜를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3f840-136">Displays the date the catalog was last populated.</span></span>  
  
 <span data-ttu-id="3f840-137">**소유자**</span><span class="sxs-lookup"><span data-stu-id="3f840-137">**Owner**</span></span>  
 <span data-ttu-id="3f840-138">전체 텍스트 카탈로그의 소유자입니다.</span><span class="sxs-lookup"><span data-stu-id="3f840-138">The owner of the full-text catalog.</span></span>  
  
 <span data-ttu-id="3f840-139">**고유 키 수**</span><span class="sxs-lookup"><span data-stu-id="3f840-139">**Unique Key Count**</span></span>  
 <span data-ttu-id="3f840-140">카탈로그의 전체 텍스트 인덱스를 구성하는 고유한 단어 수입니다.</span><span class="sxs-lookup"><span data-stu-id="3f840-140">The number of unique words that make up the full-text index for the catalog.</span></span>  
  
### <a name="catalog-action"></a><span data-ttu-id="3f840-141">카탈로그 동작</span><span class="sxs-lookup"><span data-stu-id="3f840-141">Catalog Action</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3f840-142">**없음**</span><span class="sxs-lookup"><span data-stu-id="3f840-142">**None**</span></span>|<span data-ttu-id="3f840-143">**카탈로그 최적화**, **카탈로그 다시 작성**또는 **카탈로그 다시 채우기** 작업을 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f840-143">Does not perform **Optimize catalog**, **Rebuild catalog**, or **Repopulate catalog** operations.</span></span>|  
|<span data-ttu-id="3f840-144">**카탈로그 최적화**</span><span class="sxs-lookup"><span data-stu-id="3f840-144">**Optimize catalog**</span></span>|<span data-ttu-id="3f840-145">카탈로그의 공간 사용률을 최적화하고 쿼리 성능을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="3f840-145">Optimizes the space utilization of the catalog and improves query performance.</span></span> <span data-ttu-id="3f840-146">카탈로그를 최적화하면 검색 결과의 검색 순위 정확도도 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f840-146">It also improves the accuracy of relevance ranking of search results.</span></span><br /><br /> <span data-ttu-id="3f840-147">이 동작은 ALTER FULLTEXT CATALOG *catalog_name* REORGANIZE를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3f840-147">This action executes ALTER FULLTEXT CATALOG *catalog_name* REORGANIZE.</span></span>|  
|<span data-ttu-id="3f840-148">**카탈로그 다시 작성**</span><span class="sxs-lookup"><span data-stu-id="3f840-148">**Rebuild catalog**</span></span>|<span data-ttu-id="3f840-149">전체 텍스트 카탈로그를 삭제하고 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="3f840-149">Deletes and rebuilds the full-text catalog.</span></span> <span data-ttu-id="3f840-150">악센트 구분과 같은 기본 카탈로그 속성이 변경된 경우에는 이 작업을 반드시 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f840-150">This operation must be performed if a fundamental catalog property is changed, such as accent sensitivity.</span></span><br /><br /> <span data-ttu-id="3f840-151">카탈로그를 다시 작성하려면 전체 텍스트 카탈로그가 있는 파일 그룹이 온라인 상태 또는 읽고 쓸 수 있는 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f840-151">For the rebuild to succeed, the filegroup the full-text catalog resides in must be online or read-writeable.</span></span> <span data-ttu-id="3f840-152">다시 작성 후 전체 텍스트 인덱스가 다시 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="3f840-152">After the rebuild, the full-text index will be repopulated.</span></span><br /><br /> <span data-ttu-id="3f840-153">이 동작은 ALTER FULLTEXT CATALOG *catalog_name* REBUILD를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3f840-153">This action executes ALTER FULLTEXT CATALOG *catalog_name* REBUILD.</span></span>|  
|<span data-ttu-id="3f840-154">**카탈로그 다시 채우기**</span><span class="sxs-lookup"><span data-stu-id="3f840-154">**Repopulate catalog**</span></span>|<span data-ttu-id="3f840-155">데이터의 최근 변경 내용을 적용하여 카탈로그를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="3f840-155">Updates the catalog with recent changes to the data.</span></span> <span data-ttu-id="3f840-156">이 작업을 수행하는 동안에는 카탈로그를 사용하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f840-156">This option does require catalog downtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3f840-157">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3f840-157">See Also</span></span>  
 [<span data-ttu-id="3f840-158">전체 텍스트 인덱스 채우기</span><span class="sxs-lookup"><span data-stu-id="3f840-158">Populate Full-Text Indexes</span></span>](../relational-databases/indexes/indexes.md)  
  
  
