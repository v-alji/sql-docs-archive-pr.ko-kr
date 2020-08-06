---
title: 테이블 행 필터 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.filtertablerows.f1
ms.assetid: 005f5c71-0401-490e-8823-adc54a2e9675
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9adeb2501adfd37658ddf05aa9956d6c3922bb80
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646893"
---
# <a name="filter-table-rows"></a><span data-ttu-id="51060-102">테이블 행 필터</span><span class="sxs-lookup"><span data-stu-id="51060-102">Filter Table Rows</span></span>
  <span data-ttu-id="51060-103">**테이블 행 필터** 페이지를 사용하여 다음 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51060-103">The **Filter Table Rows** page allows you to:</span></span>  
  
-   <span data-ttu-id="51060-104">스냅샷, 트랜잭션 및 병합 게시의 테이블 아티클에 정적 행 필터를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="51060-104">Apply static row filters to table articles in snapshot, transactional, and merge publications.</span></span>  
  
-   <span data-ttu-id="51060-105">병합 게시의 테이블 아티클에 매개 변수가 있는 행 필터를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="51060-105">Apply parameterized row filters to table articles in merge publications.</span></span>  
  
-   <span data-ttu-id="51060-106">조인 필터를 사용하여 병합 테이블 아티클의 필터를 관련 테이블 아티클로 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51060-106">Use join filters to extend filters on merge table articles to related table articles.</span></span>  
  
 <span data-ttu-id="51060-107">필터링 옵션에 대한 자세한 내용은 [게시된 데이터 필터링](publish/filter-published-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="51060-107">For more information about filtering options, see [Filter Published Data](publish/filter-published-data.md).</span></span> <span data-ttu-id="51060-108">**게시 속성** 대화 상자의 **행 필터** 페이지에서 필터링을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51060-108">Filtering can be changed in the **Filter Rows** page of the **Publication Properties** dialog box.</span></span>  
  
 <span data-ttu-id="51060-109">애플리케이션 성능을 최대화하고 필요한 원격 스토리지를 줄이거나 특정 구독자가 사용할 수 있는 데이터를 제한하려면 필요한 데이터만 게시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51060-109">To maximize application performance and reduce the amount of remote storage required, or to restrict the availability of certain data to specific Subscribers, you should publish only the data required.</span></span> <span data-ttu-id="51060-110">게시에는 필터링되지 않은 테이블과 필터링된 테이블이 모두 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51060-110">Your publication can include both unfiltered and filtered tables.</span></span> <span data-ttu-id="51060-111">예를 들어 필터링되지 않은 전체 회사 제품 테이블을 포함할 수도 있고 행 필터를 사용하여 특정 영역으로 필터링된 고객 테이블을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51060-111">For example, you could include the complete (unfiltered) table of company products and use row filters to provide a filtered table of customers for a specific region.</span></span> <span data-ttu-id="51060-112">게시된 데이터를 필터링하여 다음 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51060-112">By filtering published data, you can:</span></span>  
  
-   <span data-ttu-id="51060-113">네트워크로 보내지는 데이터 양을 최소화합니다.</span><span class="sxs-lookup"><span data-stu-id="51060-113">Minimize the amount of data sent over the network.</span></span>  
  
-   <span data-ttu-id="51060-114">구독자에 필요한 스토리지 공간을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="51060-114">Reduce the amount of storage space required at the Subscriber.</span></span>  
  
-   <span data-ttu-id="51060-115">개별 구독자 요구 사항에 기초하여 게시 및 애플리케이션을 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51060-115">Customize publications and applications based on individual Subscriber requirements.</span></span>  
  
-   <span data-ttu-id="51060-116">서로 다른 구독자에 서로 다른 데이터 파티션을 보낼 수 있으므로 구독자가 데이터를 업데이트할 때 충돌을 방지하거나 충돌 횟수를 줄일 수 있습니다. 즉, 두 개의 구독자가 같은 데이터 값을 업데이트하지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51060-116">Avoid or reduce conflicts if Subscribers are updating data, because different data partitions can be sent to different Subscribers (no two Subscribers will be updating the same data values).</span></span>  
  
-   <span data-ttu-id="51060-117">중요한 데이터를 전송하지 못하게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51060-117">Avoid transmitting sensitive data.</span></span> <span data-ttu-id="51060-118">행 필터와 열 필터를 사용하여 구독자의 데이터 액세스를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51060-118">Row filters and column filters can be used to restrict a Subscriber's access to data.</span></span> <span data-ttu-id="51060-119">병합 복제에서 HOST_NAME()을 포함하는 매개 변수가 있는 필터를 사용할 경우 보안 고려 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51060-119">For merge replication, there are security considerations if you use a parameterized filter that includes HOST_NAME().</span></span> <span data-ttu-id="51060-120">자세한 내용은 [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md)의 "HOST_NAME()으로 필터링" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="51060-120">For more information, see the section "Filtering with HOST_NAME()" in [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 <span data-ttu-id="51060-121">필터는 행 식별을 위해 복제에 사용된 `rowguidcol`을 포함하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51060-121">A filter must not include the `rowguidcol` used by replication to identify rows.</span></span> <span data-ttu-id="51060-122">기본적으로 이 열은 병합 복제를 설정할 때 추가된 열이며 이름은 **rowguid**입니다.</span><span class="sxs-lookup"><span data-stu-id="51060-122">By default this is the column added at the time you set up merge replication and is named **rowguid**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="51060-123">옵션</span><span class="sxs-lookup"><span data-stu-id="51060-123">Options</span></span>  
 <span data-ttu-id="51060-124">**필터링된 테이블**</span><span class="sxs-lookup"><span data-stu-id="51060-124">**Filtered Tables**</span></span>  
 <span data-ttu-id="51060-125">이 창은 게시의 테이블 아티클에 필터를 추가하면 추가된 필터로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="51060-125">This pane is populated with filters as you add them to table articles in the publication.</span></span> <span data-ttu-id="51060-126">행 필터가 있는 테이블은 창에서 최상위 노드로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="51060-126">Tables with row filters are shown as top-level nodes in the pane.</span></span> <span data-ttu-id="51060-127">병합 게시의 경우 조인 필터를 통해 필터링이 확장된 테이블은 자식 노드로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="51060-127">For merge publications, tables to which filtering has been extended through a join filter are shown as child nodes.</span></span>  
  
 <span data-ttu-id="51060-128">**추가**</span><span class="sxs-lookup"><span data-stu-id="51060-128">**Add**</span></span>  
 <span data-ttu-id="51060-129">**추가** 를 클릭하면 테이블 아티클을 필터링할 수 있는 대화 상자가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="51060-129">Click **Add** to launch a dialog box that enables you to filter table articles.</span></span> <span data-ttu-id="51060-130">스냅샷 또는 트랜잭션 게시에 대해 **추가** 를 클릭하면 대화 상자가 바로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="51060-130">Clicking **Add** for a snapshot or transactional publication launches a dialog box immediately.</span></span> <span data-ttu-id="51060-131">병합 게시에 대해 **추가**를 클릭하면 **필터 추가**, **선택한 필터 확장을 위해 조인 추가**, **자동으로 필터 생성**의 세 가지 선택 사항이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="51060-131">Clicking **Add** for a merge publication displays three choices: **Add Filter**; **Add Join to Extend the Selected Filter**; **Automatically Generate Filters**.</span></span>  
  
-   <span data-ttu-id="51060-132">**필터 추가** 를 선택하면 **필터 추가** 대화 상자가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="51060-132">Select **Add Filter** to launch the **Add Filter** dialog box.</span></span> <span data-ttu-id="51060-133">이 대화 상자를 사용하여 테이블 아티클에 행 필터를 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51060-133">This dialog box allows you to apply row filters to a table article.</span></span> <span data-ttu-id="51060-134">예를 들어 **필터 추가** 대화 상자에서 고객 데이터가 들어 있는 테이블을 구독자로 복제할 때 프랑스 고객의 데이터만 포함되도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51060-134">In the **Add Filter** dialog box, you could, for example, specify that a table with customer data should only contain data on French customers when it is replicated to Subscribers.</span></span>  
  
-   <span data-ttu-id="51060-135">**선택한 필터 확장을 위해 조인 추가** 를 선택하면 **조인 추가** 대화 상자가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="51060-135">Select **Add Join to Extend the Selected Filter** to launch the **Add Join** dialog box.</span></span> <span data-ttu-id="51060-136">**조인 추가** 대화 상자를 사용하여 행 필터가 있는 테이블과 관련된 테이블의 데이터를 필터링하도록 행 필터를 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51060-136">The **Add Join** dialog box allows you to extend a row filter so that it filters data in tables related to the table with the row filter.</span></span> <span data-ttu-id="51060-137">예를 들어 프랑스 고객의 데이터만 포함하도록 고객 테이블을 필터링하고 고객 주문과 관련된 테이블이 있으면 주문 테이블에 프랑스 고객의 주문만 포함되도록 두 테이블 간 조인을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51060-137">For example, if a customer table is filtered so that it only contains data on French customers and there is a related table for customer orders, you can define a join between the two tables so that the orders table only includes orders from French customers.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="51060-138">이 옵션을 사용하려면 먼저 필터 창에서 조인의 기본 테이블을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51060-138">This option is available only if you first select the base table of the join in the filter pane.</span></span>  
  
-   <span data-ttu-id="51060-139">**자동으로 필터 생성** 을 선택하면 **필터 생성** 대화 상자가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="51060-139">Select **Automatically Generate Filters** to launch the **Generate Filters** dialog box.</span></span> <span data-ttu-id="51060-140">이 대화 상자를 사용하여 외래 키 관계를 통해 관련된 다른 테이블로 복제가 자동으로 확장되는 병합 게시의 한 테이블에 행 필터를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51060-140">This dialog box allows you to define a row filter on one table in a merge publication that replication automatically extends to other tables that are related through foreign key relationships.</span></span> <span data-ttu-id="51060-141">예를 들어 게시에 고객 테이블, 고객 테이블에 대한 외래 키가 있는 주문 테이블, 주문 테이블에 대한 외래 키가 있는 주문 세부 정보 테이블 등 3개의 테이블이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51060-141">For example, a publication could include three tables: a customer table, an orders table (with a foreign key to the customer table), and an order details table (with a foreign key to the orders table).</span></span> <span data-ttu-id="51060-142">고객 테이블에 행 필터를 정의하면 복제가 해당 필터를 다른 테이블로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="51060-142">Define a row filter on the customer table, and replication will extend it to the other tables.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="51060-143">복제 시 필터가 자동으로 생성되면 게시의 기존 필터는 모두 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="51060-143">When filters are automatically generated by replication, any existing filters on the publication are deleted.</span></span> <span data-ttu-id="51060-144">자동으로 생성된 필터와 수동으로 지정한 필터를 모두 포함하려면 먼저 필터를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="51060-144">To include both filters generated automatically and ones specified manually, generate filters first.</span></span> <span data-ttu-id="51060-145">각 게시에 대해 자동으로 생성된 필터 집합을 하나만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51060-145">You can only specify one set of automatically generated filters for each publication.</span></span>  
  
 <span data-ttu-id="51060-146">**편집**</span><span class="sxs-lookup"><span data-stu-id="51060-146">**Edit**</span></span>  
 <span data-ttu-id="51060-147">필터 창에서 행 필터 또는 조인 필터를 선택하고 **편집** 을 클릭하면 **필터 편집** 또는 **조인 편집** 대화 상자가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="51060-147">Select a row filter or join filter in the filter pane and click **Edit** to launch the **Edit Filter** or **Edit Join** dialog box.</span></span>  
  
 <span data-ttu-id="51060-148">**Delete**</span><span class="sxs-lookup"><span data-stu-id="51060-148">**Delete**</span></span>  
 <span data-ttu-id="51060-149">필터 창에서 행 필터 또는 조인 필터를 선택하고 **삭제** 를 클릭하면 필터가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="51060-149">Select a row filter or join filter in the filter pane and click **Delete** to delete the filter.</span></span>  
  
 <span data-ttu-id="51060-150">**테이블 찾기**</span><span class="sxs-lookup"><span data-stu-id="51060-150">**Find Table**</span></span>  
 <span data-ttu-id="51060-151">조인 필터만 사용하여 게시를 병합합니다.</span><span class="sxs-lookup"><span data-stu-id="51060-151">Merge publications with join filters only.</span></span> <span data-ttu-id="51060-152">**테이블 찾기** 를 클릭하여 복잡한 필터 트리에서 테이블을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51060-152">Click **Find Table** to find a table in a complex filter tree.</span></span> <span data-ttu-id="51060-153">관계가 복잡하게 설정된 데이터베이스에서는 한 테이블이 여러 테이블에 조인될 수 있으므로 필터 트리에서 두 개 이상의 위치에 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51060-153">In a database with complex relationships, a table can be joined to multiple tables, and therefore can appear in more than one place in the filter tree.</span></span>  
  
 <span data-ttu-id="51060-154">실제 테이블은 트리의 한 위치에만 표시되고 나머지 위치에서는 바로 가기로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="51060-154">The actual table appears in only one place in the tree, and in other places, the table is represented by a shortcut.</span></span> <span data-ttu-id="51060-155">테이블 바로 가기는 테이블에 대한 참조일 뿐이므로 해당 테이블의 자식 노드는 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51060-155">A shortcut to a table is only a reference to the table; it does not show the child nodes of the table.</span></span> <span data-ttu-id="51060-156">바로 가기 노드는 바로 가기 화살표로 표시되며 해당 노드를 확장하면 **\<tablename>의 테이블을 보려면 테이블 찾기를 클릭하세요**라는 텍스트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="51060-156">A shortcut node is marked with a shortcut arrow, and expanding that node shows the text **Click Find Table to see table for \<tablename>**.</span></span>  
  
 <span data-ttu-id="51060-157">창에서 바로 가기 노드를 선택하고 **테이블 찾기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="51060-157">Select a shortcut node in the pane and click **Find Table**.</span></span> <span data-ttu-id="51060-158">창이 확장되고 해당 테이블이 강조 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="51060-158">The pane is expanded and the table is highlighted.</span></span> <span data-ttu-id="51060-159">바로 가기 노드를 선택하지 않고 **테이블 찾기** 를 클릭하면 **테이블 찾기** 대화 상자가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="51060-159">If you click **Find Table** without a shortcut node selected, a **Find Table** dialog box is launched.</span></span>  
  
 <span data-ttu-id="51060-160">**Filter**</span><span class="sxs-lookup"><span data-stu-id="51060-160">**Filter**</span></span>  
 <span data-ttu-id="51060-161">필터 창에서 선택한 필터의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 정의를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="51060-161">Contains the [!INCLUDE[tsql](../../includes/tsql-md.md)] definition for the filter selected in the filter pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51060-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="51060-162">See Also</span></span>  
 <span data-ttu-id="51060-163">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="51060-163">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="51060-164">[게시 속성 보기 및 수정](publish/view-and-modify-publication-properties.md) </span><span class="sxs-lookup"><span data-stu-id="51060-164">[View and Modify Publication Properties](publish/view-and-modify-publication-properties.md) </span></span>  
 <span data-ttu-id="51060-165">[게시된 데이터 필터링](publish/filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="51060-165">[Filter Published Data](publish/filter-published-data.md) </span></span>  
 <span data-ttu-id="51060-166">[Join Filters](merge/join-filters.md) </span><span class="sxs-lookup"><span data-stu-id="51060-166">[Join Filters](merge/join-filters.md) </span></span>  
 <span data-ttu-id="51060-167">[매개 변수가 있는 행 필터](merge/parameterized-filters-parameterized-row-filters.md) </span><span class="sxs-lookup"><span data-stu-id="51060-167">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span></span>  
 [<span data-ttu-id="51060-168">데이터 및 데이터베이스 개체 게시</span><span class="sxs-lookup"><span data-stu-id="51060-168">Publish Data and Database Objects</span></span>](publish/publish-data-and-database-objects.md)  
  
  
