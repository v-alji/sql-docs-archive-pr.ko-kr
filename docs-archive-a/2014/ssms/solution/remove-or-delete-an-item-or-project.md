---
title: 항목이나 프로젝트 제거 또는 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- deleting project items
- projects [SQL Server Management Studio], item removal
- removing project items
ms.assetid: 3fd92434-70f5-466e-bef0-7e0fd73ddb1c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 679911f15d6c47f4274180602a5376c4ec03c77b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649310"
---
# <a name="remove-or-delete-an-item-or-project"></a><span data-ttu-id="0a19d-102">항목이나 프로젝트 제거 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="0a19d-102">Remove or Delete an Item or Project</span></span>
  <span data-ttu-id="0a19d-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 프로젝트의 프로젝트 항목은 쿼리, 연결 및 기타 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="0a19d-103">Project items in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] projects are Queries, Connections, and Miscellaneous files.</span></span> <span data-ttu-id="0a19d-104">스토리지에서 파일을 지우지 않고 솔루션에서 프로젝트 쿼리 및 기타 파일을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a19d-104">You can remove project queries and miscellaneous files from your solution without erasing the files from storage.</span></span> <span data-ttu-id="0a19d-105">프로젝트 또는 항목이 현재 솔루션에는 유용하지 않지만 다른 솔루션에 포함하려는 경우 해당 프로젝트 또는 항목을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="0a19d-105">Remove a project or item when it is not useful in the current solution but you want to include it in another solution.</span></span>  
  
### <a name="to-remove-a-project-item"></a><span data-ttu-id="0a19d-106">프로젝트 항목을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="0a19d-106">To remove a project item</span></span>  
  
1.  <span data-ttu-id="0a19d-107">솔루션 탐색기에서 제거할 프로젝트 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0a19d-107">In Solution Explorer, select the project item you want to remove.</span></span>  
  
2.  <span data-ttu-id="0a19d-108">**편집** 메뉴에서 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a19d-108">On the **Edit** menu, click **Remove**.</span></span>  
  
3.  <span data-ttu-id="0a19d-109">확인 대화 상자에서 **제거** 를 클릭하여 프로젝트에서 항목을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="0a19d-109">On the confirmation dialog, click **Remove** to remove the item from the project.</span></span>  
  
 <span data-ttu-id="0a19d-110">제거된 항목은 계속 파일 시스템에 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="0a19d-110">A removed item still exists on the file system.</span></span> <span data-ttu-id="0a19d-111">따라서 제거된 항목을 원본 솔루션이나 다른 솔루션에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a19d-111">Therefore, you can add a removed item to its original solution or to another solution.</span></span>  
  
#### <a name="to-remove-a-project"></a><span data-ttu-id="0a19d-112">프로젝트를 제거하려면</span><span class="sxs-lookup"><span data-stu-id="0a19d-112">To remove a project</span></span>  
  
1.  <span data-ttu-id="0a19d-113">솔루션 탐색기에서 제거할 프로젝트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0a19d-113">In Solution Explorer, select the project you want to remove.</span></span>  
  
2.  <span data-ttu-id="0a19d-114">**편집** 메뉴에서 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a19d-114">On the **Edit** menu, click **Remove**.</span></span>  
  
3.  <span data-ttu-id="0a19d-115">확인 대화 상자에서 **확인**을 클릭하여 솔루션에서 프로젝트를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="0a19d-115">On the confirmation dialog, click **OK**, to remove the project from the solution.</span></span>  
  
 <span data-ttu-id="0a19d-116">프로젝트를 영구히 삭제할 수 있지만 그러기 위해서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 솔루션에서 프로젝트에 대한 참조를 먼저 제거한 다음 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Widows 탐색기를 사용하여 연결된 파일을 스토리지에서 영구히 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a19d-116">You can delete a project permanently, but you first need to remove any references to the project from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] solutions, and then use [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Explorer to permanently delete the associated files from storage.</span></span>  
  
#### <a name="to-delete-a-project"></a><span data-ttu-id="0a19d-117">프로젝트를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="0a19d-117">To delete a project</span></span>  
  
1.  <span data-ttu-id="0a19d-118">솔루션 탐색기에서 솔루션에서 삭제할 프로젝트를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="0a19d-118">In Solution Explorer, remove the project you want to delete from the solution.</span></span>  
  
2.  <span data-ttu-id="0a19d-119">Windows 탐색기에서 삭제할 프로젝트 또는 항목과 연결된 파일을 찾아서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0a19d-119">In Windows Explorer, locate and select the files associated with the project or item you want to delete.</span></span>  
  
3.  <span data-ttu-id="0a19d-120">**파일** 메뉴에서 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a19d-120">On the **File** menu, click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a19d-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0a19d-121">See Also</span></span>  
 <span data-ttu-id="0a19d-122">[솔루션 탐색기](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="0a19d-122">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="0a19d-123">[프로젝트에 새 항목 추가](add-new-items-to-a-project.md) </span><span class="sxs-lookup"><span data-stu-id="0a19d-123">[Add New Items to a Project](add-new-items-to-a-project.md) </span></span>  
 [<span data-ttu-id="0a19d-124">프로젝트에 기존 항목 추가</span><span class="sxs-lookup"><span data-stu-id="0a19d-124">Add Existing Items to a Project</span></span>](add-existing-items-to-a-project.md)  
  
  
