---
title: 아티클 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.articles.f1
ms.assetid: 7c743dc6-6c6d-4c92-b711-842e1b0b273e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 91336314a9538633af7c528d756d8461f7e8fe13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741867"
---
# <a name="articles"></a><span data-ttu-id="c145c-102">아티클</span><span class="sxs-lookup"><span data-stu-id="c145c-102">Articles</span></span>
  <span data-ttu-id="c145c-103">**아티클** 페이지에서 게시에 아티클로 포함할 데이터베이스 개체를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-103">On the **Articles** page, you specify which database objects to include as articles in the publication.</span></span> <span data-ttu-id="c145c-104">하나 이상의 다른 데이터베이스 개체에 종속된 데이터베이스 개체를 게시하는 경우 참조된 개체를 모두 게시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-104">If you are publishing a database object that depends on one or more other database objects, you must publish all referenced objects.</span></span> <span data-ttu-id="c145c-105">예를 들어 테이블에 종속된 뷰를 게시하는 경우 테이블도 게시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-105">For example, if you publish a view that depends on a table, you must publish the table also.</span></span>  
  
 <span data-ttu-id="c145c-106">게시할 수 없는 개체는 옆에 빨간색 아이콘이 표시되며 마법사 페이지 아래쪽의 정보 패널에 설명이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-106">Objects that cannot be published have a red icon next to them, with an explanation in the information panel at the bottom of the wizard page.</span></span> <span data-ttu-id="c145c-107">다음 개체는 게시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-107">The following objects cannot be published:</span></span>  
  
-   <span data-ttu-id="c145c-108">암호화된 개체는 게시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-108">Encrypted objects.</span></span>  
  
-   <span data-ttu-id="c145c-109">기본 키가 없는 테이블은 트랜잭션 게시에 게시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-109">Tables without primary keys cannot be published in transactional publications.</span></span>  
  
-   <span data-ttu-id="c145c-110">지연 업데이트 구독이 설정된 트랜잭션 게시와 병합 게시에 테이블을 모두 게시할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-110">Tables cannot be published in both a merge publication and a transactional publication enabled for queued updating subscriptions.</span></span> <span data-ttu-id="c145c-111">둘 이상의 게시에 아티클을 게시하는 방법은 [데이터 및 데이터베이스 개체 게시](publish/publish-data-and-database-objects.md)의 "둘 이상의 게시에 테이블 게시" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c145c-111">For more information about publishing an article in more than one publication, see the "Publishing Tables in More Than One Publication" section in [Publish Data and Database Objects](publish/publish-data-and-database-objects.md).</span></span>  
  
## <a name="oracle-publishers"></a><span data-ttu-id="c145c-112">Oracle 게시자</span><span class="sxs-lookup"><span data-stu-id="c145c-112">Oracle Publishers</span></span>  
 <span data-ttu-id="c145c-113">Oracle 게시자의 경우 다음 사항을 추가로 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-113">There are additional considerations for Oracle Publishers:</span></span>  
  
-   <span data-ttu-id="c145c-114">Oracle에서 게시할 수 있는 개체 목록은 [Design Considerations and Limitations for Oracle Publishers](non-sql/design-considerations-and-limitations-for-oracle-publishers.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c145c-114">For a list of objects that can be published from Oracle, see [Design Considerations and Limitations for Oracle Publishers](non-sql/design-considerations-and-limitations-for-oracle-publishers.md).</span></span> <span data-ttu-id="c145c-115">게시할 수 없는 개체는 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-115">Objects that cannot be published are not displayed.</span></span>  
  
-   <span data-ttu-id="c145c-116">게시할 수 있는 데이터 형식 목록은 [Data Type Mapping for Oracle Publishers](non-sql/data-type-mapping-for-oracle-publishers.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c145c-116">For a list of data types that can be published, see [Data Type Mapping for Oracle Publishers](non-sql/data-type-mapping-for-oracle-publishers.md).</span></span> <span data-ttu-id="c145c-117">게시할 수 없는 데이터 형식이 있는 열은 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-117">Columns with data types that cannot be published are not displayed.</span></span>  
  
## <a name="column-filters"></a><span data-ttu-id="c145c-118">열 필터</span><span class="sxs-lookup"><span data-stu-id="c145c-118">Column Filters</span></span>  
 <span data-ttu-id="c145c-119">이 페이지의 **게시할 개체** 창에서 테이블을 확장한 다음 필요한 열만 선택하여 열을 필터링할 수 있습니다. 이 마법사의 **테이블 행 필터** 페이지에서는 행을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-119">Filter columns on this page by expanding a table in the **Objects to publish** pane and then selecting only the columns required (rows can be filtered in the **Filter Table Rows** page of this wizard).</span></span> <span data-ttu-id="c145c-120">열 필터링은 보안(예: 중요한 데이터의 복제 방지) 및 성능(예: 큰 BLOB(Binary Large Object) 열의 복제 방지)을 비롯하여 다양한 범위에서 유용하게 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-120">Filtering columns is useful for a number of reasons, including security (preventing sensitive data from being replicated) and performance (avoiding replication of large binary large object (BLOB) columns, for example).</span></span> <span data-ttu-id="c145c-121">필터링할 수 없는 열 유형 목록 등 열 필터링에 대한 자세한 내용은 [게시된 데이터 필터링](publish/filter-published-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c145c-121">For more information about column filtering, including a list of column types that cannot be filtered, see [Filter Published Data](publish/filter-published-data.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="c145c-122">옵션</span><span class="sxs-lookup"><span data-stu-id="c145c-122">Options</span></span>  
 <span data-ttu-id="c145c-123">**게시할 개체** 창을 사용하여 다음 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-123">The **Objects to publish** pane allows you to:</span></span>  
  
-   <span data-ttu-id="c145c-124">복제에 사용 가능한 모든 개체를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-124">View all objects available for replication.</span></span>  
  
-   <span data-ttu-id="c145c-125">해당 개체 옆에 있는 확인란을 선택하여 개체를 게시에 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-125">Include an object in a publication by selecting the check box next to that object.</span></span>  
  
-   <span data-ttu-id="c145c-126">개체 유형(예: **테이블**) 옆의 확인란을 선택하여 특정 유형(예: 테이블)의 개체를 모두 게시에 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-126">Include all objects of a particular type (such as a table) in the publication by selecting the check box next to that object type (such as **Tables**).</span></span>  
  
-   <span data-ttu-id="c145c-127">테이블 노드를 확장하여 테이블에 있는 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-127">Expand table nodes to see the columns in the table.</span></span>  
  
-   <span data-ttu-id="c145c-128">해당 열 옆에 있는 확인란 선택을 취소하여 게시에서 테이블 열을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-128">Filter table columns out of a publication by clearing the check box next to the column.</span></span>  
  
-   <span data-ttu-id="c145c-129">창에서 개체를 마우스 오른쪽 단추로 클릭하여 해당 개체의 명령 메뉴를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-129">Right-click an object in the pane to see a menu of commands for that object.</span></span>  
  
 <span data-ttu-id="c145c-130">**아티클 속성**</span><span class="sxs-lookup"><span data-stu-id="c145c-130">**Article Properties**</span></span>  
 <span data-ttu-id="c145c-131">**아티클 속성**을 클릭한 후 다음 중 하나를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-131">Click **Article Properties**, and then click one of the following:</span></span>  
  
-   <span data-ttu-id="c145c-132">**선택한 \<ObjectType> 아티클 속성 설정**을 클릭하여 **아티클 속성 - \<ObjectName>** 대화 상자를 엽니다. 이 대화 상자에서 변경한 속성은 **아티클** 페이지의 개체 창에 강조 표시된 개체에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-132">Click **Set Properties of Highlighted \<ObjectType> Article** to launch the **Article Properties - \<ObjectName>** dialog box; property changes made in this dialog box are applied only to the object that is highlighted in the object pane on the **Articles** page.</span></span>  
  
-   <span data-ttu-id="c145c-133">**모든 \<ObjectType> 아티클 속성 설정**을 클릭하여 **모든 \<ObjectType> 아티클의 속성** 대화 상자를 엽니다. 이 대화 상자에서 변경한 속성은 게시용으로, 아직 선택하지 않은 개체를 비롯하여 **아티클** 페이지의 개체 창에서 해당 형식을 갖는 모든 개체에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-133">Click **Set Properties of All \<ObjectType> Articles**, to launch the **Properties for All \<ObjectType> Articles** dialog box; property changes made in this dialog box are applied to all objects of that type in the object pane on the **Articles** page, including ones not yet selected for publication.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c145c-134">**모든 \<ObjectType> 아티클의 속성** 대화 상자에서 변경한 속성은 이전에 **아티클 속성 - \<ObjectName>** 대화 상자에서 지정한 내용을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-134">Property changes made in the **Properties for All \<ObjectType> Articles** dialog box override any made previously in the **Article Properties - \<ObjectName>** dialog box.</span></span> <span data-ttu-id="c145c-135">예를 들어 특정 개체 유형의 모든 아티클에 대해 여러 기본값을 설정하고 개별 개체에 대해 일부 속성도 설정하려면 먼저 모든 아티클의 기본값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-135">If, for example, you want to set a number of defaults for all articles of an object type, but also want to set some properties for individual objects, set the defaults for all articles first.</span></span> <span data-ttu-id="c145c-136">그런 다음 개별 개체에 대해 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-136">Then set the properties for the individual objects.</span></span>  
  
 <span data-ttu-id="c145c-137">**강조 표시된 테이블은 다운로드 전용**</span><span class="sxs-lookup"><span data-stu-id="c145c-137">**Highlighted table is download-only**</span></span>  
 <span data-ttu-id="c145c-138">병합 복제에 대해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-138">Merge replication only.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="c145c-139">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에만 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-139">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="c145c-140">클라이언트 구독이 사용 중일 때는 구독자에서 변경 작업을 수행할 수 없게 지정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-140">Select to specify that changes are disallowed at the Subscriber if a client subscription is used.</span></span> <span data-ttu-id="c145c-141">다운로드 전용 아티클은 구독자에서 업데이트할 수 없으므로 추적 메타데이터가 구독자로 전송되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-141">Because download-only articles cannot be updated at the Subscriber, tracking metadata is not sent to Subscribers.</span></span> <span data-ttu-id="c145c-142">이로 인해 구독자의 스토리지 용량 및 성능상 이점이 줄어들 수 있으며 특히 네트워크 연결 속도가 느릴 경우 더욱 그렇습니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-142">This can lead to reduced storage on the Subscribers and a performance benefit, especially if the network connection is slow.</span></span> <span data-ttu-id="c145c-143">이 옵션은 **아티클 속성** 대화 상자에 있는 **동기화 방향** 옵션의 **구독자로 다운로드 전용, 구독자 변경 금지** 값과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-143">This option corresponds to a value of **Download-only to Subscriber, prohibit Subscriber changes** for the option **Synchronization direction** in the **Article Properties** dialog box.</span></span> <span data-ttu-id="c145c-144">자세한 내용은 [다운로드 전용 아티클로 병합 복제 성능 최적화](merge/optimize-merge-replication-performance-with-download-only-articles.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c145c-144">For more information, see [Optimize Merge Replication Performance with Download-Only Articles](merge/optimize-merge-replication-performance-with-download-only-articles.md).</span></span>  
  
 <span data-ttu-id="c145c-145">**선택 표시된 개체만 목록에 표시**</span><span class="sxs-lookup"><span data-stu-id="c145c-145">**Show only checked objects in the list**</span></span>  
 <span data-ttu-id="c145c-146">개체 창에서 선택한 아티클만 표시하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c145c-146">Select this check box to show only those articles that are selected in the object pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c145c-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c145c-147">See Also</span></span>  
 <span data-ttu-id="c145c-148">[데이터 및 데이터베이스 개체 게시](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="c145c-148">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="c145c-149">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="c145c-149">[Create a Publication](publish/create-a-publication.md) </span></span>  
 [<span data-ttu-id="c145c-150">게시 속성 보기 및 수정</span><span class="sxs-lookup"><span data-stu-id="c145c-150">View and Modify Publication Properties</span></span>](publish/view-and-modify-publication-properties.md)  
  
  
