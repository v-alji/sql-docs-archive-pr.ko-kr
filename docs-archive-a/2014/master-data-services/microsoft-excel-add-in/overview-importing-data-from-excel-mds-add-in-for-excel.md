---
title: 데이터 게시 (Excel용 MDS 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: ea84a9aa-aeec-411b-ab8d-bc1b14f864a3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ab37a353469d1902394a3e2cd8060d9be82abb40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735452"
---
# <a name="publishing-data-mds-add-in-for-excel"></a><span data-ttu-id="e8ab2-102">데이터 게시(Excel용 MDS 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="e8ab2-102">Publishing Data (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="e8ab2-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]에서 데이터를 다른 사용자와 공유하려는 경우 데이터를 MDS 리포지토리에 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], publish data to the MDS repository when you want to share it with other users.</span></span> <span data-ttu-id="e8ab2-104">데이터가 게시되는 즉시 추가 기능의 다른 사용자가 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-104">As soon as data is published, it is available for other users of the Add-in to download.</span></span>  
  
 <span data-ttu-id="e8ab2-105">데이터를 게시하면 사용자가 이전에 추가했거나 업데이트한 모든 데이터가 MDS 저장소에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-105">When you publish data, any data you've added or updated is published to the MDS repository.</span></span> <span data-ttu-id="e8ab2-106">삭제한 데이터가 게시되지 않았습니다. 데이터를 개별적으로 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-106">Data you've deleted is not published-you must delete data separately.</span></span> <span data-ttu-id="e8ab2-107">자세한 내용은 [행 삭제&#40;Excel용 MDS 추가 기능&#41;](delete-a-row-mds-add-in-for-excel.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-107">For more information, see [Delete a Row &#40;MDS Add-in for Excel&#41;](delete-a-row-mds-add-in-for-excel.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8ab2-108">게시는 새 엔터티를 만드는 방법으로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-108">Publishing cannot be used to create a new entity.</span></span> <span data-ttu-id="e8ab2-109">엔터티를 만드는 방법에 대한 자세한 내용은 [엔터티 만들기&#40;Excel용 MDS 추가 기능&#41;](create-an-entity-mds-add-in-for-excel.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-109">For more information about creating entities, see [Create an Entity &#40;MDS Add-in for Excel&#41;](create-an-entity-mds-add-in-for-excel.md).</span></span>  
  
## <a name="when-multiple-users-publish-at-the-same-time"></a><span data-ttu-id="e8ab2-110">동시에 여러 사용자가 게시하는 경우</span><span class="sxs-lookup"><span data-stu-id="e8ab2-110">When Multiple Users Publish at the Same Time</span></span>  
 <span data-ttu-id="e8ab2-111">여러 사용자가 동일 데이터에 업데이트를 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-111">Multiple users can publish updates to the same data.</span></span> <span data-ttu-id="e8ab2-112">각 사용자가 게시할 때마다 업데이트가 데이터베이스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-112">As each user publishes, the update is saved to the database.</span></span> <span data-ttu-id="e8ab2-113">즉, 최신 업데이트된 데이터를 사용 중이 아닌 사용자도 자신이 게시를 수행할 때 값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-113">This means that a user who was not working with the most recently-updated data can still change the value when he or she publishes.</span></span>  
  
 <span data-ttu-id="e8ab2-114">자신이 작성한 업데이트만 데이터베이스에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-114">Only the updates you make are published to the database.</span></span> <span data-ttu-id="e8ab2-115">워크시트에서 오래된 데이터는 게시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-115">Any out-of-date data in the worksheet is not published.</span></span>  
  
## <a name="transactions-and-annotations"></a><span data-ttu-id="e8ab2-116">트랜잭션 및 주석</span><span class="sxs-lookup"><span data-stu-id="e8ab2-116">Transactions and Annotations</span></span>  
 <span data-ttu-id="e8ab2-117">게시된 각 변경 내용은 트랜잭션으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-117">Each published change is saved as a transaction.</span></span> <span data-ttu-id="e8ab2-118">필요에 따라 트랜잭션에 변경 이유에 대해 설명하는 주석(설명)을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-118">If you choose, you can add annotations (comments) to a transaction, to explain why you made the change.</span></span>  
  
-   <span data-ttu-id="e8ab2-119">삭제도 관리자가 다시 되돌릴 수 있는 트랜잭션으로 저장되지만 삭제에 대해서는 주석을 달 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-119">You cannot annotate deletions, although deletions are saved as transactions that can be reversed by an administrator.</span></span>  
  
-   <span data-ttu-id="e8ab2-120">멤버의 **코드** 값을 변경 하는 경우에는 트랜잭션으로 기록 되지 않으며 해당 멤버에 대 한 모든 이전 트랜잭션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-120">If you change the **Code** value for a member, it is not recorded as a transaction, and all previous transactions for the member are unavailable.</span></span>  
  
-   <span data-ttu-id="e8ab2-121">다른 사용자가 멤버에 대해 수행한 트랜잭션을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-121">You can view transactions made to a member by other users.</span></span> <span data-ttu-id="e8ab2-122">또한 사용자에게 특정 특성에 대한 권한이 없더라도 멤버에 대해 자신이 수행한 모든 트랜잭션을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-122">You can also view all transactions you've made to a member, even if you no longer have permission to specific attributes.</span></span>  
  
 <span data-ttu-id="e8ab2-123">멤버에 대한 모든 트랜잭션을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-123">You can view all transactions made to a member.</span></span> <span data-ttu-id="e8ab2-124">자세한 내용은 [멤버에 대한 모든 주석 또는 트랜잭션 보기&#40;Excel용 MDS 추가 기능&#41;](view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-124">For more information, see [View All Annotations or Transactions for a Member &#40;MDS Add-in for Excel&#41;](view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e8ab2-125">주석을 500자 이상으로 입력하면 주석이 자동으로 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-125">If you enter an annotation of more than 500 characters, the annotation is automatically truncated.</span></span>  
  
## <a name="business-rule-and-other-validation"></a><span data-ttu-id="e8ab2-126">비즈니스 규칙 및 기타 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="e8ab2-126">Business Rule and Other Validation</span></span>  
 <span data-ttu-id="e8ab2-127">데이터를 게시할 때는 데이터를 MDS 저장소에 추가하기 전에 데이터가 정확한지 확인하기 위해 유효성 검사가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-127">When you publish data, validation is performed to ensure data is accurate before it's added to the MDS repository.</span></span> <span data-ttu-id="e8ab2-128">데이터가 지정된 조건에 맞지 않으면 저장소에 게시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-128">If the data does not meet specified criteria, it will not be published to the repository.</span></span> <span data-ttu-id="e8ab2-129">자세한 내용은 [데이터 유효성 검사&#40;Excel용 MDS 추가 기능&#41;](validating-data-mds-add-in-for-excel.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-129">For more information, see [Validating Data &#40;MDS Add-in for Excel&#41;](validating-data-mds-add-in-for-excel.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="e8ab2-130">관련 작업</span><span class="sxs-lookup"><span data-stu-id="e8ab2-130">Related Tasks</span></span>  
  
|<span data-ttu-id="e8ab2-131">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="e8ab2-131">Task Description</span></span>|<span data-ttu-id="e8ab2-132">항목</span><span class="sxs-lookup"><span data-stu-id="e8ab2-132">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="e8ab2-133">활성 워크시트에서 다시 MDS 저장소로 데이터를 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-133">Publish data from the active worksheet back to the MDS repository.</span></span>|[<span data-ttu-id="e8ab2-134">Excel의 데이터를 MDS &#40;Excel용 MDS 추가 기능에 게시&#41;</span><span class="sxs-lookup"><span data-stu-id="e8ab2-134">Publish Data from Excel to MDS &#40;MDS Add-in for Excel&#41;</span></span>](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)|  
|<span data-ttu-id="e8ab2-135">MDS 저장소에서 행을 삭제하고 동시에 워크시트에서도 행을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ab2-135">Delete a row from the MDS repository and from the worksheet at the same time.</span></span>|[<span data-ttu-id="e8ab2-136">행 삭제&#40;Excel용 MDS 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="e8ab2-136">Delete a Row &#40;MDS Add-in for Excel&#41;</span></span>](delete-a-row-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a><span data-ttu-id="e8ab2-137">관련 내용</span><span class="sxs-lookup"><span data-stu-id="e8ab2-137">Related Content</span></span>  
  
-   [<span data-ttu-id="e8ab2-138">데이터 새로 고침&#40;Excel용 MDS 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="e8ab2-138">Refreshing Data &#40;MDS Add-in for Excel&#41;</span></span>](refreshing-data-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="e8ab2-139">Microsoft Excel용 Master Data Services 추가 기능</span><span class="sxs-lookup"><span data-stu-id="e8ab2-139">Master Data Services Add-in for Microsoft Excel</span></span>](master-data-services-add-in-for-microsoft-excel.md)  
  
  
