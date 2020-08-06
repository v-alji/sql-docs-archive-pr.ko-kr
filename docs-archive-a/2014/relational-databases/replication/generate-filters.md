---
title: 필터 생성 | Microsoft 문서
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.generatefilters.f1
ms.assetid: be28515c-5d6d-467b-b933-d7c8d97a45b4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b0e484c89c97d3f32f3e41197800202f796a25d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646886"
---
# <a name="generate-filters"></a><span data-ttu-id="c1370-102">필터 생성</span><span class="sxs-lookup"><span data-stu-id="c1370-102">Generate Filters</span></span>
  <span data-ttu-id="c1370-103">**필터 생성** 대화 상자를 사용하여 병합 게시의 테이블에 행 필터를 정의할 수 있습니다. 그러면 복제에서 외래 키 관계를 통해 관련된 다른 테이블로 해당 필터를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c1370-103">The **Generate Filters** dialog box allows you to define a row filter on one table in a merge publication; replication then automatically extends the filter to other tables that are related through foreign key relationships.</span></span> <span data-ttu-id="c1370-104">예를 들어 프랑스 고객에 대한 데이터만 포함되도록 고객 테이블에 필터를 정의하면 복제에서는 관련된 주문 및 주문 세부 정보 테이블에 프랑스 고객과 관련된 정보만 포함되도록 해당 필터를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c1370-104">For example, if you define a filter on a customer table so that it only contains data on French customers, replication extends that filter so that related orders and order details tables contain only information related to French customers.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c1370-105">옵션</span><span class="sxs-lookup"><span data-stu-id="c1370-105">Options</span></span>  
 <span data-ttu-id="c1370-106">이 대화 상자에서는 3단계로 이루어진 프로세스를 통해 테이블에 행 필터를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c1370-106">This dialog box involves a three-step process to create a row filter on a table.</span></span> <span data-ttu-id="c1370-107">그러면 기본 키와 외래 키 간의 관계를 통해 필터링된 테이블과 관련된 테이블로 필터가 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1370-107">The filter is then extended to the tables related to the filtered table through primary key and foreign key relationships.</span></span> <span data-ttu-id="c1370-108">예를 들어 **Customer**, **SalesOrderHeader**및 **SalesOrderDetail**테이블이 있는데 **Customer** 와 **SalesOrderHeader**간에 관계가 있고 **SalesOrderHeader** 와 **SalesOrderDetail**간에 관계가 있을 때 **Customer**에 행 필터를 적용하면 복제에서는 해당 필터를 **SalesOrderHeader** 및 **SalesOrderDetail**로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c1370-108">For example, given the three tables **Customer**, **SalesOrderHeader**, and **SalesOrderDetail**, with a relationship between **Customer** and **SalesOrderHeader**, and a relationship between **SalesOrderHeader** and **SalesOrderDetail**, apply a row filter to **Customer**, and replication extends that filter to **SalesOrderHeader** and **SalesOrderDetail**.</span></span>  
  
1.  <span data-ttu-id="c1370-109">**필터링할 테이블을 선택하십시오.**</span><span class="sxs-lookup"><span data-stu-id="c1370-109">**Select the table to filter.**</span></span>  
  
     <span data-ttu-id="c1370-110">드롭다운 목록 상자에서 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c1370-110">Select a table from the drop-down list box.</span></span> <span data-ttu-id="c1370-111">**아티클** 페이지에서 선택한 테이블만 목록 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1370-111">Tables appear in the list box only if they were selected on the **Articles** page.</span></span>  
  
2.  <span data-ttu-id="c1370-112">**구독자가 받을 테이블 행을 식별하는 필터 문을 작성하십시오.**</span><span class="sxs-lookup"><span data-stu-id="c1370-112">**Complete the filter statement to identify which table rows Subscribers will receive.**</span></span>  
  
     <span data-ttu-id="c1370-113">새 필터 문을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c1370-113">Define a new filter statement.</span></span> <span data-ttu-id="c1370-114">**열** 목록 상자는 **필터링할 테이블을 선택하십시오**에서 선택한 테이블에서 게시 중인 열을 모두 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c1370-114">The **Columns** list box lists all the columns that you are publishing from the table you selected in **Select the table to filter**.</span></span> <span data-ttu-id="c1370-115">**필터 문** 텍스트 영역에는 다음 형식의 기본 텍스트가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1370-115">The **Filter statement** text area includes the default text, which is in the form of:</span></span>  
  
     `SELECT <published_columns> FROM [tableowner].[tablename] WHERE`  
  
     <span data-ttu-id="c1370-116">이 텍스트는 변경할 수 없습니다. 표준 [!INCLUDE[tsql](../../includes/tsql-md.md)] 구문을 사용하여 WHERE 키워드 뒤에 필터 절을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c1370-116">This text cannot be changed; type the filter clause after the WHERE keyword using standard [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="c1370-117">성능상의 이유로 `LEFT([MyColumn]) = SUSER_SNAME()`과 같은 매개 변수가 있는 행 필터 절의 열 이름에는 함수를 적용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c1370-117">For performance reasons, we recommended that you not apply functions to column names in parameterized row filter clauses, such as `LEFT([MyColumn]) = SUSER_SNAME()`.</span></span> <span data-ttu-id="c1370-118">필터 절에 HOST_NAME을 사용하고 HOST_NAME 값을 재지정할 경우 CONVERT를 사용하여 데이터 형식을 변환해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1370-118">If you use HOST_NAME in a filter clause and override the HOST_NAME value, it might be necessary to convert data types using CONVERT.</span></span> <span data-ttu-id="c1370-119">이를 위한 최선의 구현 방법은 [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md)항목의 "HOST_NAME() 값 재정의" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c1370-119">For more information about best practices for this case, see the section "Overriding the HOST_NAME() Value" in the topic [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
3.  <span data-ttu-id="c1370-120">**이 테이블의 데이터를 받을 구독 수를 지정하십시오.**</span><span class="sxs-lookup"><span data-stu-id="c1370-120">**Specify how many subscriptions will receive data from this table.**</span></span>  
  
     [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="c1370-121">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에만 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1370-121">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="c1370-122">병합 복제를 사용하면 데이터 및 애플리케이션에 가장 적합한 파티션 유형을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1370-122">Merge replication allows you to specify the type of partitions that are best suited to your data and application.</span></span> <span data-ttu-id="c1370-123">**이 테이블의 행을 단일 구독으로 이동**을 선택하면 병합 복제에서 겹치지 않는 파티션 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c1370-123">If you select **A row from this table will go to only one subscription**, merge replication sets the nonoverlapping partitions option.</span></span> <span data-ttu-id="c1370-124">겹치지 않는 파티션을 사전 계산 파티션과 함께 사용하면 겹치지 않는 파티션이 사전 계산 파티션과 연관된 업로드 비용을 최소화하므로 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1370-124">Nonoverlapping partitions work in conjunction with precomputed partitions to improve performance, with nonoverlapping partitions minimizing the upload cost associated with precomputed partitions.</span></span> <span data-ttu-id="c1370-125">사용하는 매개 변수가 있는 필터와 조인 필터가 복잡할수록 겹치지 않는 파티션의 성능상 이점이 더욱 분명하게 드러납니다.</span><span class="sxs-lookup"><span data-stu-id="c1370-125">The performance benefit of nonoverlapping partitions is more noticeable when the parameterized filters and join filters used are more complex.</span></span> <span data-ttu-id="c1370-126">이 옵션을 선택하면 행을 둘 이상의 구독자에 복제할 수 없는 방식으로 데이터를 분할해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1370-126">If you select this option, you must ensure that the data is partitioned in such a way that a row cannot be replicated to more than one Subscriber.</span></span> <span data-ttu-id="c1370-127">자세한 내용은 [매개 변수가 있는 행 필터](merge/parameterized-filters-parameterized-row-filters.md)항목의 "'partition options' 설정" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c1370-127">For more information, see the section "Setting 'partition options'" in the topic [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 <span data-ttu-id="c1370-128">필터를 추가한 후에는 **확인** 을 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="c1370-128">After you have added a filter, click **OK** to exit and close the dialog box.</span></span> <span data-ttu-id="c1370-129">지정한 필터가 구문 분석되고 SELECT 절의 테이블에 대해 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1370-129">The filter you specified is parsed and run against the table in the SELECT clause.</span></span> <span data-ttu-id="c1370-130">필터 문에 구문 오류나 기타 문제가 있으면 알림 메시지가 표시되며 이를 보고 필터 문을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1370-130">If the filter statement contains syntax errors or other problems, you will be notified and will be able to edit the filter statement.</span></span>  
  
 <span data-ttu-id="c1370-131">문이 구문 분석되면 복제에서는 필요한 조인 필터를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c1370-131">After the statement is parsed, replication creates the necessary join filters.</span></span> <span data-ttu-id="c1370-132">이 마법사가 실행 중인 게시자에 대해 배포자를 아직 구성하지 않은 경우 배포자를 구성하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1370-132">If you have not yet configured the Distributor for the Publisher against which this wizard is running, you are prompted to configure it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1370-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c1370-133">See Also</span></span>  
 <span data-ttu-id="c1370-134">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="c1370-134">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="c1370-135">[게시 속성 보기 및 수정](publish/view-and-modify-publication-properties.md) </span><span class="sxs-lookup"><span data-stu-id="c1370-135">[View and Modify Publication Properties](publish/view-and-modify-publication-properties.md) </span></span>  
 <span data-ttu-id="c1370-136">[게시된 데이터 필터링](publish/filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="c1370-136">[Filter Published Data](publish/filter-published-data.md) </span></span>  
 <span data-ttu-id="c1370-137">[Join Filters](merge/join-filters.md) </span><span class="sxs-lookup"><span data-stu-id="c1370-137">[Join Filters](merge/join-filters.md) </span></span>  
 <span data-ttu-id="c1370-138">[매개 변수가 있는 행 필터](merge/parameterized-filters-parameterized-row-filters.md) </span><span class="sxs-lookup"><span data-stu-id="c1370-138">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span></span>  
 [<span data-ttu-id="c1370-139">데이터 및 데이터베이스 개체 게시</span><span class="sxs-lookup"><span data-stu-id="c1370-139">Publish Data and Database Objects</span></span>](publish/publish-data-and-database-objects.md)  
  
  
