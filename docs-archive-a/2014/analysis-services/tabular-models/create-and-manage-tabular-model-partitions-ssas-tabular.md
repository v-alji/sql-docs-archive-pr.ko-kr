---
title: 테이블 형식 모델 파티션 만들기 및 관리 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: dab72cf0-95bc-4b63-95dc-505b5cd881c1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 58c408c712d6ac4b6bd590bd0f8c895dc1a88700
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653522"
---
# <a name="create-and-manage-tabular-model-partitions-ssas-tabular"></a><span data-ttu-id="c2745-102">테이블 형식 모델 파티션 만들기 및 관리(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="c2745-102">Create and Manage Tabular Model Partitions (SSAS Tabular)</span></span>
  <span data-ttu-id="c2745-103">파티션은 테이블을 논리적 부분으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="c2745-103">Partitions divide a table into logical parts.</span></span> <span data-ttu-id="c2745-104">각 파티션은 다른 파티션과 별개로 처리(새로 고침)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2745-104">Each partition can then be processed (Refreshed) independent of other partitions.</span></span> <span data-ttu-id="c2745-105">모델 제작 중에 모델에 대해 정의한 파티션은 배포된 모델에서 복제됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2745-105">Partitions defined for a model during model authoring are duplicated in a deployed model.</span></span> <span data-ttu-id="c2745-106">배포된 후에는 **의** 파티션 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 대화 상자를 사용하거나 스크립트를 사용하여 해당 파티션을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2745-106">Once deployed, you can manage those partitions by using the **Partitions** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or by using a script.</span></span> <span data-ttu-id="c2745-107">이 항목에서 제공하는 태스크에서는 배포된 모델에 대해 파티션을 만들고 관리하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c2745-107">Tasks provided in this topic describe how to create and manage partitions for a deployed model.</span></span>  
  
 <span data-ttu-id="c2745-108">이 항목에는 다음 태스크가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2745-108">This topic includes the following tasks:</span></span>  
  
-   [<span data-ttu-id="c2745-109">새 파티션을 만들려면</span><span class="sxs-lookup"><span data-stu-id="c2745-109">To create a new partition</span></span>](#bkmk_create_new)  
  
-   [<span data-ttu-id="c2745-110">파티션을 복사하려면</span><span class="sxs-lookup"><span data-stu-id="c2745-110">To copy a partition</span></span>](#bkmk_copy)  
  
-   [<span data-ttu-id="c2745-111">두 개 이상의 파티션을 병합 하려면</span><span class="sxs-lookup"><span data-stu-id="c2745-111">To merge two or more partitions</span></span>](#bkmk_merge)  
  
-   [<span data-ttu-id="c2745-112">파티션을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="c2745-112">To delete a partition</span></span>](#bkmk_delete)  
  
## <a name="tasks"></a><span data-ttu-id="c2745-113">작업</span><span class="sxs-lookup"><span data-stu-id="c2745-113">Tasks</span></span>  
 <span data-ttu-id="c2745-114">배포된 테이블 형식 모델 데이터베이스에 대해 파티션을 만들고 관리하려면 **의** 파티션 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]대화 상자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c2745-114">To create and manage partitions for a deployed tabular model database, you will use the **Partitions** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="c2745-115">**파티션** 대화 상자를 보려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 테이블을 마우스 오른쪽 단추로 클릭한 다음 **파티션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2745-115">To view the **Partitions** dialog box, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click on a table, and then click **Partitions**.</span></span>  
  
###  <a name="to-create-a-new-partition"></a><a name="bkmk_create_new"></a><span data-ttu-id="c2745-116">새 파티션을 만들려면</span><span class="sxs-lookup"><span data-stu-id="c2745-116">To create a new partition</span></span>  
  
1.  <span data-ttu-id="c2745-117">**파티션** 대화 상자에서 **새로 만들기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2745-117">In the **Partitions** dialog box, click the **New** button.</span></span>  
  
2.  <span data-ttu-id="c2745-118">**파티션 이름**에 파티션의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c2745-118">In **Partition Name**, type a name for the partition.</span></span> <span data-ttu-id="c2745-119">기본적으로 기본 파티션의 이름은 새 파티션마다 증분 번호로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2745-119">By default, the name of the default partition will be incrementally numbered for each new partition.</span></span>  
  
3.  <span data-ttu-id="c2745-120">**SQL 문**에서 파티션에 포함할 열과 절을 정의하는 SQL 쿼리 문을 쿼리 창에 입력하거나 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="c2745-120">In **SQL Statement**, type or paste a SQL query statement that defines the columns and any clauses you want to include in the partition into the query window.</span></span>  
  
4.  <span data-ttu-id="c2745-121">문의 유효성을 검사하려면 **구문 검사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2745-121">To validate the statement, click **Check Syntax**.</span></span>  
  
###  <a name="to-copy-a-partition"></a><a name="bkmk_copy"></a><span data-ttu-id="c2745-122">파티션을 복사 하려면</span><span class="sxs-lookup"><span data-stu-id="c2745-122">To copy a partition</span></span>  
  
1.  <span data-ttu-id="c2745-123">**파티션** 대화 상자의 **파티션** 목록에서 복사할 파티션을 선택한 다음 **복사** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2745-123">In the **Partitions** dialog box, in the **Partitions** list, select the partition you want to copy, and then click the **Copy** button.</span></span>  
  
2.  <span data-ttu-id="c2745-124">**파티션 이름**에 파티션의 새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c2745-124">In **Partition Name**, type a new name for the partition.</span></span>  
  
3.  <span data-ttu-id="c2745-125">**SQL 문**에서 SQL 쿼리 문을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="c2745-125">In **SQL Statement**, edit the SQL query statement.</span></span>  
  
###  <a name="to-merge-two-or-more-partitions"></a><a name="bkmk_merge"></a> <span data-ttu-id="c2745-126">두 개 이상의 파티션을 병합하려면</span><span class="sxs-lookup"><span data-stu-id="c2745-126">To merge two or more partitions</span></span>  
  
-   <span data-ttu-id="c2745-127">**파티션** 대화 상자의 **파티션** 목록에서 Ctrl+클릭을 사용하여 병합할 파티션을 선택한 다음 **병합** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2745-127">In the **Partitions** dialog box, in the **Partitions** list, use Ctrl+click to select the partitions you want to merge, and then click the **Merge** button.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c2745-128">파티션을 병합해도 파티션 메타데이터가 업데이트되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c2745-128">Merging partitions does not update the partition metadata.</span></span> <span data-ttu-id="c2745-129">처리 작업으로 병합된 파티션의 모든 데이터가 처리되도록 관리자가 결과 파티션에 대해 SQL 문을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2745-129">Administrators must alter the SQL Statement for the resulting partition to make sure processing operations process all data in the merged partition.</span></span>  
  
###  <a name="to-delete-a-partition"></a><a name="bkmk_delete"></a><span data-ttu-id="c2745-130">파티션을 삭제 하려면</span><span class="sxs-lookup"><span data-stu-id="c2745-130">To delete a partition</span></span>  
  
-   <span data-ttu-id="c2745-131">**파티션** 대화 상자의 **파티션** 목록에서 삭제할 파티션을 선택한 다음 **삭제** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2745-131">In the **Partitions** dialog box, in the **Partitions** list, select the partition you want to delete, and then click the **Delete** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2745-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c2745-132">See Also</span></span>  
 <span data-ttu-id="c2745-133">[테이블 형식 모델 파티션이 SSAS 테이블 형식&#41;을 &#40;](partitions-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="c2745-133">[Tabular Model Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="c2745-134">테이블 형식 모델 파티션 처리&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="c2745-134">Process Tabular Model Partitions &#40;SSAS Tabular&#41;</span></span>](process-tabular-model-partitions-ssas-tabular.md)  
  
  
