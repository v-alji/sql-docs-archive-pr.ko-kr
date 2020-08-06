---
title: 전체 텍스트 카탈로그 만들기 및 관리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text catalogs [SQL Server], creating
- full-text search [SQL Server], using SQL Server Management Studio
ms.assetid: 824b7131-44a6-4815-89e6-62b7bab060e3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 18efd79bc34beee94d4edc61e9165a986edba90b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660983"
---
# <a name="create-and-manage-full-text-catalogs"></a><span data-ttu-id="e6d34-102">전체 텍스트 카탈로그 만들기 및 관리</span><span class="sxs-lookup"><span data-stu-id="e6d34-102">Create and Manage Full-Text Catalogs</span></span>
  <span data-ttu-id="e6d34-103">전체 텍스트 카탈로그는 파일 그룹에 속하지 않는 가상 개체이며, 전체 텍스트 인덱스의 그룹을 가리키는 논리적인 개념입니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-103">A full-text catalog is a virtual object that does not belong to any filegroup; it is a logical concept that refers to a group of full-text indexes.</span></span>  
  
##  <a name="creating-a-full-text-catalog"></a><a name="creating"></a><span data-ttu-id="e6d34-104">전체 텍스트 카탈로그 만들기</span><span class="sxs-lookup"><span data-stu-id="e6d34-104">Creating a Full-Text Catalog</span></span>  
  
#### <a name="to-create-a-full-text-catalog"></a><span data-ttu-id="e6d34-105">전체 텍스트 카탈로그를 만들려면</span><span class="sxs-lookup"><span data-stu-id="e6d34-105">To create a full-text catalog</span></span>  
  
1.  <span data-ttu-id="e6d34-106">개체 탐색기에서 서버, **데이터베이스**를 차례로 확장한 다음 전체 텍스트 카탈로그를 만들려는 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-106">In Object Explorer, expand the server, expand **Databases**, and expand the database in which you want to create the full-text catalog.</span></span>  
  
2.  <span data-ttu-id="e6d34-107">**스토리지**를 확장한 다음 **전체 텍스트 카탈로그**를 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-107">Expand **Storage**, and then right-click **Full Text Catalogs**.</span></span>  
  
3.  <span data-ttu-id="e6d34-108">**새 전체 텍스트 카탈로그**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-108">Select **New Full-Text Catalog**.</span></span>  
  
4.  <span data-ttu-id="e6d34-109">**새 전체 텍스트 카탈로그** 대화 상자에서 다시 만들려는 카탈로그에 대한 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-109">In the **New Full-Text Catalog** dialog box, specify the information for the catalog that you are re-creating.</span></span> <span data-ttu-id="e6d34-110">자세한 내용은 [새 전체 텍스트 카탈로그&#40;일반 페이지&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6d34-110">For more information, see [New Full-Text Catalog &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e6d34-111">전체 텍스트 카탈로그 ID는 00005부터 시작하고 카탈로그를 새로 만들 때마다 1씩 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-111">Full-text catalog IDs begin at 00005 and are incremented by one for each new catalog created.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
  
##  <a name="viewing-the-properties-of-a-full-text-catalog"></a><a name="props"></a><span data-ttu-id="e6d34-112">전체 텍스트 카탈로그의 속성 보기</span><span class="sxs-lookup"><span data-stu-id="e6d34-112">Viewing the Properties of a Full-Text Catalog</span></span>  
 <span data-ttu-id="e6d34-113">FULLTEXTCATALOGPROPERTY와 같은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 함수를 사용하여 전체 텍스트 인덱싱에 관련된 다양한 속성의 값을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-113">[!INCLUDE[tsql](../../includes/tsql-md.md)] functions such as FULLTEXTCATALOGPROPERTY can be used to obtain the value of various properties related to full-text indexing.</span></span> <span data-ttu-id="e6d34-114">이 정보는 전체 텍스트 검색을 관리하고 이러한 검색에서 발생하는 문제를 해결하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-114">This information is useful for administering and troubleshooting full-text search.</span></span>  
  
 <span data-ttu-id="e6d34-115">다음 표에서는 전체 텍스트 카탈로그에 관련된 속성을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-115">The following table lists the properties that are related to full-text catalogs.</span></span>  
  
|<span data-ttu-id="e6d34-116">속성</span><span class="sxs-lookup"><span data-stu-id="e6d34-116">Property</span></span>|<span data-ttu-id="e6d34-117">Description</span><span class="sxs-lookup"><span data-stu-id="e6d34-117">Description</span></span>|<span data-ttu-id="e6d34-118">함수</span><span class="sxs-lookup"><span data-stu-id="e6d34-118">Function</span></span>|  
|--------------|-----------------|--------------|  
|`AccentSensitivity`|<span data-ttu-id="e6d34-119">악센트 구분 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-119">Accent-sensitivity setting.</span></span>|[<span data-ttu-id="e6d34-120">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="e6d34-120">FULLTEXTCATALOGPROPERTY</span></span>](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql)|  
|`ImportStatus`|<span data-ttu-id="e6d34-121">전체 텍스트 카탈로그를 가져올지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-121">Whether the full-text catalog is being imported.</span></span>|<span data-ttu-id="e6d34-122">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="e6d34-122">FULLTEXTCATALOGPROPERTY</span></span>|  
|`IndexSize`|<span data-ttu-id="e6d34-123">전체 텍스트 카탈로그의 크기(MB)입니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-123">Size of the full-text catalog in megabytes (MB).</span></span>|<span data-ttu-id="e6d34-124">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="e6d34-124">FULLTEXTCATALOGPROPERTY</span></span>|  
|`ItemCount`|<span data-ttu-id="e6d34-125">현재 전체 텍스트 카탈로그에 있는 전체 텍스트 인덱싱된 항목 수입니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-125">Number of full-text indexed items currently in the full-text catalog.</span></span>|<span data-ttu-id="e6d34-126">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="e6d34-126">FULLTEXTCATALOGPROPERTY</span></span>|  
|`MergeStatus`|<span data-ttu-id="e6d34-127">마스터 병합의 진행 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-127">Whether a master merge is in progress.</span></span>|<span data-ttu-id="e6d34-128">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="e6d34-128">FULLTEXTCATALOGPROPERTY</span></span>|  
|`PopulateCompletionAge`|<span data-ttu-id="e6d34-129">마지막 전체 텍스트 인덱스 채우기가 완료된 시간과 01/01/1990 00:00:00 사이의 차이(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-129">Difference in seconds between the completion of the last full-text index population and 01/01/1990 00:00:00.</span></span>|<span data-ttu-id="e6d34-130">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="e6d34-130">FULLTEXTCATALOGPROPERTY</span></span>|  
|`PopulateStatus`|<span data-ttu-id="e6d34-131">채우기 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-131">Populate status.</span></span><br /><br /> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]|<span data-ttu-id="e6d34-132">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="e6d34-132">FULLTEXTCATALOGPROPERTY</span></span>|  
|`UniqueKeyCount`|<span data-ttu-id="e6d34-133">전체 텍스트 카탈로그에서 고유 키 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-133">Number of unique keys in the full-text catalog.</span></span>|<span data-ttu-id="e6d34-134">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="e6d34-134">FULLTEXTCATALOGPROPERTY</span></span>|  
  
  
  
##  <a name="rebuilding-a-full-text-catalog"></a><a name="rebuildone"></a><span data-ttu-id="e6d34-135">전체 텍스트 카탈로그 다시 작성</span><span class="sxs-lookup"><span data-stu-id="e6d34-135">Rebuilding a Full-Text Catalog</span></span>  
  
#### <a name="to-rebuild-a-full-text-catalog"></a><span data-ttu-id="e6d34-136">전체 텍스트 카탈로그를 다시 작성하려면</span><span class="sxs-lookup"><span data-stu-id="e6d34-136">To rebuild a full-text catalog</span></span>  
  
1.  <span data-ttu-id="e6d34-137">개체 탐색기에서 서버, **데이터베이스**를 차례로 확장한 다음 다시 작성할 전체 텍스트 카탈로그가 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-137">In Object Explorer, expand the server, expand **Databases**, and then expand the database that contains the full-text catalog that you want to rebuild.</span></span>  
  
2.  <span data-ttu-id="e6d34-138">**스토리지**를 확장한 다음 **전체 텍스트 카탈로그**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-138">Expand **Storage**, and then expand **Full Text Catalogs**.</span></span>  
  
3.  <span data-ttu-id="e6d34-139">다시 작성하려는 전체 텍스트 카탈로그의 이름을 마우스 오른쪽 단추로 클릭하고 **다시 작성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-139">Right-click the name of the full-text catalog that you want to rebuild, and select **Rebuild**.</span></span>  
  
4.  <span data-ttu-id="e6d34-140">**전체 텍스트 카탈로그를 삭제하고 다시 작성하시겠습니까?** 라는 질문에 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-140">To the question **Do you want to delete the full-text catalog and rebuild it?**, click **OK**.</span></span>  
  
5.  <span data-ttu-id="e6d34-141">**전체 텍스트 카탈로그 다시 작성** 대화 상자에서 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-141">In the **Rebuild Full-Text Catalog** dialog box, click **Close**.</span></span>  
  
  
  
##  <a name="rebuilding-all-full-text-catalogs-for-a-database"></a><a name="rebuildall"></a><span data-ttu-id="e6d34-142">데이터베이스의 모든 전체 텍스트 카탈로그 다시 작성</span><span class="sxs-lookup"><span data-stu-id="e6d34-142">Rebuilding All Full-Text Catalogs for a Database</span></span>  
  
#### <a name="to-rebuild-the-full-text-catalogs-for-a-database"></a><span data-ttu-id="e6d34-143">데이터베이스의 전체 텍스트 카탈로그를 다시 작성하려면</span><span class="sxs-lookup"><span data-stu-id="e6d34-143">To rebuild the full-text catalogs for a database</span></span>  
  
1.  <span data-ttu-id="e6d34-144">개체 탐색기에서 서버, **데이터베이스**를 차례로 확장한 다음 다시 작성할 전체 텍스트 카탈로그가 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-144">In Object Explorer, expand the server, expand **Databases**, and then expand the database that contains the full-text catalogs that you want to rebuild.</span></span>  
  
2.  <span data-ttu-id="e6d34-145">**스토리지**를 확장한 다음 **전체 텍스트 카탈로그**를 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-145">Expand **Storage**, and then right-click **Full Text Catalogs**.</span></span>  
  
3.  <span data-ttu-id="e6d34-146">**모두 다시 작성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-146">Select **Rebuild All**.</span></span>  
  
4.  <span data-ttu-id="e6d34-147">**전체 텍스트 카탈로그를 모두 삭제하고 다시 작성하시겠습니까?** 라고 질문에 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-147">To the question, **Do you want to delete all full-text catalogs and rebuild them?**, click **OK**.</span></span>  
  
5.  <span data-ttu-id="e6d34-148">**전체 텍스트 카탈로그 모두 다시 작성** 대화 상자에서 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-148">In the **Rebuild All Full-Text Catalogs** dialog box, click **Close**.</span></span>  
  
  
  
##  <a name="removing-a-full-text-catalog-from-a-database"></a><a name="removing"></a><span data-ttu-id="e6d34-149">데이터베이스에서 전체 텍스트 카탈로그 제거</span><span class="sxs-lookup"><span data-stu-id="e6d34-149">Removing a Full-Text Catalog from a Database</span></span>  
  
#### <a name="to-remove-a-full-text-catalog-from-a-database"></a><span data-ttu-id="e6d34-150">데이터베이스에서 전체 텍스트 카탈로그를 제거하려면</span><span class="sxs-lookup"><span data-stu-id="e6d34-150">To remove a full-text catalog from a database</span></span>  
  
1.  <span data-ttu-id="e6d34-151">개체 탐색기에서 서버, **데이터베이스**를 차례로 확장한 다음 제거할 전체 텍스트 카탈로그가 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-151">In Object Explorer, expand the server, expand **Databases**, and expand the database that contains the full-text catalog you want to remove.</span></span>  
  
2.  <span data-ttu-id="e6d34-152">**스토리지**를 확장한 다음 **전체 텍스트 카탈로그**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-152">Expand **Storage**, and expand **Full Text Catalogs**.</span></span>  
  
3.  <span data-ttu-id="e6d34-153">제거할 전체 텍스트 카탈로그를 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-153">Right-click the full-text catalog that you want to remove, and then select **Delete**.</span></span>  
  
4.  <span data-ttu-id="e6d34-154">**개체 삭제** 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d34-154">In the **Delete Objects** dialog box, click **OK**.</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="e6d34-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e6d34-155">See Also</span></span>  
 [<span data-ttu-id="e6d34-156">CREATE FULLTEXT CATALOG&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e6d34-156">CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-catalog-transact-sql)  
  
  
