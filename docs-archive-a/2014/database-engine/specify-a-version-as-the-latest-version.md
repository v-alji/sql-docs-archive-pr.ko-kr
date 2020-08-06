---
title: 최신 버전으로 버전 지정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- version control services [SQL Server], latest version
- latest file version specified
- file versions [SQL Server]
ms.assetid: 407dffb1-3ecf-461e-835d-124781f26ee7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: dafe4f757e33a5db63340c3d3cc7c9151871d438
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646613"
---
# <a name="specify-a-version-as-the-latest-version"></a><span data-ttu-id="a3389-102">최신 버전으로 버전 지정</span><span class="sxs-lookup"><span data-stu-id="a3389-102">Specify a Version as the Latest Version</span></span>
  <span data-ttu-id="a3389-103">파일을 원본 제어에 체크 인하면 체크 인한 버전은 최신 버전이 됩니다. 최신 버전을 체크 아웃하거나 검색하는 사용자는 가장 최근에 체크 인된 항목의 로컬 복사본을 받게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3389-103">When you check a file into source control, the version you check in becomes the latest version; users who check out or retrieve the latest version receive local copies of the item most recently checked in.</span></span>  
  
 <span data-ttu-id="a3389-104">그러나 경우에 따라서는 이전 버전의 항목을 최신 버전으로 지정하려고 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3389-104">However, in some situations, you may want to designate an earlier version of an item as the latest version.</span></span> <span data-ttu-id="a3389-105">예를 들어 파일을 체크 아웃하고 수정한 다음 체크 인했는데</span><span class="sxs-lookup"><span data-stu-id="a3389-105">For example, you check out a file, modify the file, and then check the file in.</span></span> <span data-ttu-id="a3389-106">나중에 수정한 내용을 삭제하도록 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3389-106">You later decide to discard your modifications.</span></span> <span data-ttu-id="a3389-107">항목을 체크 인했기 때문에 원래 체크 아웃을 실행 취소하는 것은 가능하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a3389-107">Because you have checked in the item, undoing your original checkout is not an option.</span></span> <span data-ttu-id="a3389-108">이 경우에는 원래 체크 아웃했던 버전을 항목의 최신 버전으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3389-108">In this situation, you can designate the version you originally checked out as the latest version of the item.</span></span>  
  
 <span data-ttu-id="a3389-109">다음과 같은 방법으로 최신 버전을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3389-109">You can designate the latest version by:</span></span>  
  
-   <span data-ttu-id="a3389-110">**버전 고정**.</span><span class="sxs-lookup"><span data-stu-id="a3389-110">**Pinning a version**.</span></span> <span data-ttu-id="a3389-111">파일 버전을 고정하면 고정된 버전보다 최신인 버전은 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a3389-111">When you pin a file version, versions that are more recent than the pinned version are not deleted.</span></span> <span data-ttu-id="a3389-112">또한 이전에 고정했던 파일을 고정 해지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3389-112">In addition, you can unpin a file that you have previously pinned.</span></span> <span data-ttu-id="a3389-113">이렇게 하면 최근에 체크 인한 파일 버전이 최신 버전이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3389-113">When you do this, the most recently checked in version of the file becomes the latest version.</span></span> <span data-ttu-id="a3389-114">그러나 고정된 파일을 체크 아웃할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a3389-114">However, you cannot check out a pinned file.</span></span>  
  
-   <span data-ttu-id="a3389-115">**지정 된 버전으로 롤백합니다**.</span><span class="sxs-lookup"><span data-stu-id="a3389-115">**Rolling back to a specified version**.</span></span> <span data-ttu-id="a3389-116">특정 버전으로 롤백하면 롤백한 버전보다 최신인 모든 버전이 소스 제어에서 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3389-116">When you roll back to a version, all versions more recent than the one to which you have rolled back are deleted from source control.</span></span> <span data-ttu-id="a3389-117">그런 다음 나머지 최신 버전을 체크 아웃할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3389-117">You can then check out the latest remaining version.</span></span>  
  
### <a name="to-pin-a-version"></a><span data-ttu-id="a3389-118">버전을 고정하려면</span><span class="sxs-lookup"><span data-stu-id="a3389-118">To pin a version</span></span>  
  
1.  <span data-ttu-id="a3389-119">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 솔루션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a3389-119">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], open the solution.</span></span>  
  
2.  <span data-ttu-id="a3389-120">솔루션 탐색기에서 최신 버전으로 지정할 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a3389-120">In Solution Explorer, select the file that you want to specify as the latest version.</span></span>  
  
3.  <span data-ttu-id="a3389-121">**파일** 메뉴에서 **원본 제어** 를 가리킨 다음 **ViewHistory**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3389-121">On the **File** menu, point to **Source Control** and click **ViewHistory**.</span></span>  
  
4.  <span data-ttu-id="a3389-122">**기록** \<file> 대화 상자에서 최신 버전으로 지정할 버전을 선택 하 고 **고정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3389-122">In the **History of** \<file> dialog box, select the version that you want to specify as the latest, and click **Pin**.</span></span>  
  
     <span data-ttu-id="a3389-123">최신 파일 버전이라는 것을 나타내는 고정 기호가 선택한 버전 옆에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a3389-123">A pin symbol appears next to the version you have selected, indicating that it is the current file version.</span></span> <span data-ttu-id="a3389-124">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에 로드된 다른 버전이 있을 경우 파일을 다시 로드하라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a3389-124">If you have a different version loaded in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], you are prompted to reload the file.</span></span>  
  
### <a name="to-roll-back-to-a-version"></a><span data-ttu-id="a3389-125">특정 버전으로 롤백하려면</span><span class="sxs-lookup"><span data-stu-id="a3389-125">To roll back to a version</span></span>  
  
1.  <span data-ttu-id="a3389-126">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 솔루션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a3389-126">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], open the solution.</span></span>  
  
2.  <span data-ttu-id="a3389-127">솔루션 탐색기에서 최신 버전으로 지정할 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a3389-127">In Solution Explorer, select the item that you want to specify as the latest version.</span></span>  
  
3.  <span data-ttu-id="a3389-128">**파일** 메뉴에서 **소스 제어** 를 가리킨 다음 **기록**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3389-128">On the **File** menu, point to **Source Control** and click **History**.</span></span>  
  
4.  <span data-ttu-id="a3389-129">**기록 옵션** 대화 상자에서 **확인** 을 클릭 하 여 **파일의 기록** 대화 상자를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3389-129">In the **History Options** dialog box, click **OK** to display the **History of File** dialog box.</span></span>  
  
5.  <span data-ttu-id="a3389-130">**파일 기록** 상자에서 최신 버전으로 지정할 버전을 선택 하 고 **롤백**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3389-130">In the **History of File** box, select the version you want to specify as the latest version, and click **Rollback**.</span></span>  
  
     <span data-ttu-id="a3389-131">선택한 버전 이후의 모든 버전이 삭제된다는 것을 알리는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a3389-131">A message appears notifying you that all versions subsequent to the one you have selected will be deleted.</span></span>  
  
6.  <span data-ttu-id="a3389-132">**예** 를 클릭 하 여 선택한 버전으로 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="a3389-132">Click **Yes** to roll back to the selected version.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3389-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a3389-133">See Also</span></span>  
 <span data-ttu-id="a3389-134">[체크 인 관리](../../2014/database-engine/manage-checkins.md) </span><span class="sxs-lookup"><span data-stu-id="a3389-134">[Manage Checkins](../../2014/database-engine/manage-checkins.md) </span></span>  
 [<span data-ttu-id="a3389-135">파일 체크 인</span><span class="sxs-lookup"><span data-stu-id="a3389-135">Check In Files</span></span>](../../2014/database-engine/check-in-files.md)  
  
  
