---
title: 병합 아티클 간의 조인 필터 집합 자동 생성 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- automatic join filter generation
- join filters
ms.assetid: 7ef419f4-c17f-42a5-9068-174a3ec08941
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4bfdbf93aad134e4da873a6aade307754a2637e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638652"
---
# <a name="automatically-generate-a-set-of-join-filters-between-merge-articles-sql-server-management-studio"></a><span data-ttu-id="7fcdf-102">병합 아티클 간의 조인 필터 집합 자동 생성(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="7fcdf-102">Automatically Generate a Set of Join Filters Between Merge Articles (SQL Server Management Studio)</span></span>
  <span data-ttu-id="7fcdf-103">새 게시 마법사의 **테이블 행 필터** 페이지 또는 **게시 속성 - \<Publication>** 대화 상자의 **행 필터** 페이지에서 자동으로 조인 필터 집합을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-103">Automatically generate a set of join filters on the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="7fcdf-104">마법사 사용 및 대화 상자 액세스에 대한 자세한 내용은 [게시 만들기](create-a-publication.md) 및 [게시 속성 보기 및 수정](view-and-modify-publication-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-104">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7fcdf-105">게시에 대한 구독이 초기화된 후 **게시 속성 - \<Publication>** 대화 상자에서 조인 필터 집합을 자동으로 생성한 경우에는 변경 내용을 적용한 후에 새 스냅샷을 생성하고 모든 구독을 다시 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-105">If you automatically generate a set of join filters in the **Publication Properties - \<Publication>** dialog box after subscriptions to the publication have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change.</span></span> <span data-ttu-id="7fcdf-106">속성 변경 요구 사항에 대한 자세한 내용은 [게시 및 아티클 속성 변경](change-publication-and-article-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-106">For more information about requirements for property changes, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
 <span data-ttu-id="7fcdf-107">테이블 집합에 대해 수동으로 조인 필터를 만들거나 테이블에 정의된 외래 키와 기본 키 간의 관계를 기반으로 복제에서 필터를 자동으로 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-107">Join filters can be created manually for a set of tables, or replication can generate the filters automatically based on the foreign key to primary key relationships defined on the tables.</span></span> <span data-ttu-id="7fcdf-108">조인 필터를 수동으로 만드는 방법에 대한 자세한 내용은 [병합 아티클 사이에서 조인 필터 정의 및 수정](define-and-modify-a-join-filter-between-merge-articles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-108">For more information about creating join filters manually, see [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
### <a name="to-automatically-generate-a-set-of-join-filters-between-merge-articles"></a><span data-ttu-id="7fcdf-109">병합 아티클 간의 조인 필터 집합을 자동으로 생성하려면</span><span class="sxs-lookup"><span data-stu-id="7fcdf-109">To automatically generate a set of join filters between merge articles</span></span>  
  
1.  <span data-ttu-id="7fcdf-110">새 게시 마법사의 **테이블 행 필터** 페이지 또는 **게시 속성 - \<Publication>** 의 **행 필터** 페이지에서 **추가**를 클릭하고 **자동으로 필터 생성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-110">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, click **Add**, and then click **Automatically Generate Filters**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7fcdf-111">자동으로 필터를 생성하면 게시의 기존 행 필터나 조인 필터가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-111">Automatically generating filters deletes any existing row filters or join filters in the publication.</span></span> <span data-ttu-id="7fcdf-112">필터 집합을 자동으로 생성한 후에 필터를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-112">You can add filters after automatically generating a set of filters.</span></span>  
  
2.  <span data-ttu-id="7fcdf-113">**필터 생성** 대화 상자의 프로세스를 따라 행 필터를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-113">Follow the process in the **Generate Filters** dialog box to create a row filter.</span></span> <span data-ttu-id="7fcdf-114">그러면 기본 키와 외래 키 간의 관계를 통해 필터링된 테이블과 관련된 테이블로 행 필터가 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-114">The row filter is then extended to the tables related to the filtered table through primary key and foreign key relationships.</span></span>  
  
    1.  <span data-ttu-id="7fcdf-115">드롭다운 목록 상자에서 필터링할 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-115">Select a table to filter from the drop-down list box.</span></span>  
  
    2.  <span data-ttu-id="7fcdf-116">**필터 문** 입력란에서 필터 문을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-116">Create a filter statement in the **Filter statement** text box.</span></span> <span data-ttu-id="7fcdf-117">텍스트 영역에 직접 입력할 수도 있고 **열** 목록 상자에서 열을 끌어서 놓을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-117">You can type directly in the text area, and you can also drag and drop columns from the **Columns** list box.</span></span>  
  
         <span data-ttu-id="7fcdf-118">**필터 문** 텍스트 영역에는 다음 형식의 기본 텍스트가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-118">The **Filter statement** text area includes the default text, which is in the form of:</span></span>  
  
        ```  
        SELECT <published_columns> FROM [tableowner].[tablename] WHERE  
        ```  
  
         <span data-ttu-id="7fcdf-119">기본 텍스트는 변경할 수 없습니다. 표준 SQL 구문을 사용하여 WHERE 키워드 다음에 정적 행 필터 또는 매개 변수가 있는 행 필터에 대한 필터 절을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-119">The default text cannot be changed; type the filter clause for a static row filter or a parameterized row filter after the WHERE keyword using standard SQL syntax.</span></span> <span data-ttu-id="7fcdf-120">매개 변수가 있는 행 필터에 대한 전체 필터 절은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-120">The complete filter clause for a parameterized row filter would look like:</span></span>  
  
        ```  
        SELECT <published_columns> FROM [HumanResources].[Employee] WHERE LoginID = SUSER_SNAME()  
        ```  
  
         <span data-ttu-id="7fcdf-121">WHERE 절은 두 부분으로 구성된 이름을 사용해야 하며 세 부분 또는 네 부분으로 구성된 이름은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-121">The WHERE clause should use two-part naming; three-part naming and four-part naming are not supported.</span></span>  
  
    3.  <span data-ttu-id="7fcdf-122">필터 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-122">Specify filter options.</span></span>  
  
         <span data-ttu-id="7fcdf-123">구독자 간에 데이터를 공유하는 방식과 일치하는 옵션을 선택합니다. **이 테이블의 행을 여러 구독으로 이동** 또는 **이 테이블의 행을 단일 구독으로 이동**.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-123">Select the option that matches how data will be shared among Subscribers: **A row from this table will go to multiple subscriptions** or **A row from this table will go to only one subscription**.</span></span> <span data-ttu-id="7fcdf-124">**이 테이블의 행을 단일 구독으로 이동**을 선택하면 병합 복제에서는 보다 작은 메타데이터를 저장하고 처리하여 성능을 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-124">If you select **A row from this table will go to only one subscription**, merge replication can optimize performance by storing and processing less metadata.</span></span> <span data-ttu-id="7fcdf-125">그러나 한 행이 둘 이상의 구독자로 복제될 수 없도록 데이터가 분할되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-125">However, you must ensure that the data is partitioned in such a way that a row cannot be replicated to more than one Subscriber.</span></span> <span data-ttu-id="7fcdf-126">자세한 내용은 [매개 변수가 있는 행 필터](../merge/parameterized-filters-parameterized-row-filters.md)항목의 "'partition options' 설정" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-126">For more information, see the section "Setting 'partition options'" in the topic [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="7fcdf-127">지정한 필터가 구문 분석되고 SELECT 절의 테이블에 대해 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-127">The filter you specified is parsed and run against the table in the SELECT clause.</span></span> <span data-ttu-id="7fcdf-128">필터 문에 구문 오류나 기타 문제가 있으면 알림 메시지가 표시되며 이를 보고 필터 문을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-128">If the filter statement contains syntax errors or other problems, you will be notified and will be able to edit the filter statement.</span></span>  
  
     <span data-ttu-id="7fcdf-129">문이 구문 분석된 후에 복제는 필요한 조인 필터를 만들고 **테이블 행 필터** 또는 **행 필터** 페이지의 **필터링된 테이블** 창에 이러한 필터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-129">After the statement is parsed, replication creates the necessary join filters and displays them in the **Filtered Tables** pane on the **Filter Table Rows** or **Filter Rows** page.</span></span> <span data-ttu-id="7fcdf-130">새 게시 마법사에서 필터를 생성할 때 이 마법사가 실행 중인 게시자에 대한 배포자를 아직 구성하지 않은 경우에는 구성을 요청하는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-130">If you are generating filters from the New Publication Wizard and have not yet configured the Distributor for the Publisher against which this wizard is running, you are prompted to configure it.</span></span>  
  
4.  <span data-ttu-id="7fcdf-131">**게시 속성 - \<Publication>** 대화 상자에서 **확인**을 클릭하여 저장하고 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-131">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
### <a name="to-modify-a-filter-that-was-automatically-generated"></a><span data-ttu-id="7fcdf-132">자동으로 생성된 필터를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="7fcdf-132">To modify a filter that was automatically generated</span></span>  
  
1.  <span data-ttu-id="7fcdf-133">새 게시 마법사의 **테이블 행 필터** 페이지 또는 **게시 속성 - \<Publication>** 대화 상자의 **행 필터** 페이지에 있는 **필터링된 테이블** 창에서 필터를 선택하고 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-133">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select a filter in the **Filtered Tables** pane, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="7fcdf-134">**필터 편집** 또는 **조인 편집** 대화 상자에서 필터를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-134">In the **Edit Filter** or **Edit Join** dialog box, modify the filter.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-filter-that-was-automatically-generated"></a><span data-ttu-id="7fcdf-135">자동으로 생성된 필터를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="7fcdf-135">To delete a filter that was automatically generated</span></span>  
  
1.  <span data-ttu-id="7fcdf-136">새 게시 마법사의 **테이블 행 필터** 페이지 또는 **게시 속성 - \<Publication>** 대화 상자의 **행 필터** 페이지에 있는 **필터링된 테이블** 창에서 필터를 선택하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcdf-136">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select a filter in the **Filtered Tables** pane, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fcdf-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7fcdf-137">See Also</span></span>  
 <span data-ttu-id="7fcdf-138">[Join Filters](../merge/join-filters.md) </span><span class="sxs-lookup"><span data-stu-id="7fcdf-138">[Join Filters](../merge/join-filters.md) </span></span>  
 [<span data-ttu-id="7fcdf-139">매개 변수가 있는 행 필터</span><span class="sxs-lookup"><span data-stu-id="7fcdf-139">Parameterized Row Filters</span></span>](../merge/parameterized-filters-parameterized-row-filters.md)  
  
  
