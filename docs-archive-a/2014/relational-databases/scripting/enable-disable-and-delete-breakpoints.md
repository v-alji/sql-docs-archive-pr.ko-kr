---
title: 중단점 설정, 해제 및 삭제
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 357b5874-273f-43a9-8e30-83872bdea5dc
author: rothja
ms.author: jroth
ms.openlocfilehash: 17e83c6488b9d9026fb78e5fb8f50e22533fa61e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660491"
---
# <a name="enable-disable-and-delete-breakpoints"></a><span data-ttu-id="2e45b-102">중단점 설정, 해제 및 삭제</span><span class="sxs-lookup"><span data-stu-id="2e45b-102">Enable, Disable, and Delete Breakpoints</span></span>
  <span data-ttu-id="2e45b-103">열려 있는 모든 중단점을 보고 관리하려면 **중단점** 창을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-103">To view and manage all the open breakpoints, you can use the **Breakpoints** window.</span></span> <span data-ttu-id="2e45b-104">이 창을 사용하여 중단점 정보를 보고 중단점 삭제, 해제, 설정 등과 같은 동작을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-104">Use the window to view breakpoint information and to take actions such as deleting, disabling, or enabling breakpoints.</span></span>  
  
## <a name="the-breakpoints-window"></a><span data-ttu-id="2e45b-105">중단점 창</span><span class="sxs-lookup"><span data-stu-id="2e45b-105">The Breakpoints Window</span></span>  
 <span data-ttu-id="2e45b-106">**중단점** 창에는 중단점이 위치한 코드 줄과 같은 정보가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-106">The **Breakpoints** window lists information such as which line of code the breakpoint is located on.</span></span> <span data-ttu-id="2e45b-107">**중단점** 창에서 중단점을 삭제, 해제 및 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-107">In the **Breakpoints** window, you can also delete, disable, and enable breakpoints.</span></span> <span data-ttu-id="2e45b-108">**중단점** 창에 대한 자세한 내용은 [중단점 Window](transact-sql-debugger-breakpoints-window.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2e45b-108">For more information about the **Breakpoints** window, see [Breakpoints Window](transact-sql-debugger-breakpoints-window.md)</span></span>  
  
 <span data-ttu-id="2e45b-109">중단점을 해제하면 실행이 일시 중지되지 않지만 사용자가 나중에 중단점을 설정할 경우를 위해 정의는 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-109">Disabling a breakpoint prevents it from pausing execution, but leaves the definition in place in case you want to enable the breakpoint later.</span></span> <span data-ttu-id="2e45b-110">중단점을 삭제하면 영구적으로 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-110">Deleting a breakpoint removes it permanently.</span></span> <span data-ttu-id="2e45b-111">문에서 실행을 일시 중지하려면 새 중단점을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-111">You must toggle a new breakpoint to pause execution on the statement.</span></span>  
  
## <a name="to-open-the-breakpoints-window"></a><span data-ttu-id="2e45b-112">중단점 창을 열려면</span><span class="sxs-lookup"><span data-stu-id="2e45b-112">To Open the Breakpoints Window</span></span>  
 <span data-ttu-id="2e45b-113">**To open the Breakpoints window**</span><span class="sxs-lookup"><span data-stu-id="2e45b-113">**To open the Breakpoints window**</span></span>  
  
 <span data-ttu-id="2e45b-114">다음 방법 중 하나를 사용하여 **중단점** 창을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-114">You can open the **Breakpoints** window in one of the following ways:</span></span>  
  
-   <span data-ttu-id="2e45b-115">**디버그** 메뉴에서 **창**을 클릭한 다음 **중단점**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-115">On the **Debug** menu, click **Windows**, and then click **Breakpoints**.</span></span>  
  
-   <span data-ttu-id="2e45b-116">**디버그** 도구 모음에서 **중단점** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-116">On the **Debug** toolbar, click the **Breakpoints** button.</span></span>  
  
-   <span data-ttu-id="2e45b-117">Ctrl+Alt+B를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-117">Press CTRL+ALT+B.</span></span>  
  
## <a name="to-disable-a-single-breakpoint"></a><span data-ttu-id="2e45b-118">단일 중단점을 해제하려면</span><span class="sxs-lookup"><span data-stu-id="2e45b-118">To Disable a Single Breakpoint</span></span>  
 <span data-ttu-id="2e45b-119">**To disable a single breakpoint**</span><span class="sxs-lookup"><span data-stu-id="2e45b-119">**To disable a single breakpoint**</span></span>  
  
 <span data-ttu-id="2e45b-120">다음 방법 중 하나를 사용하여 단일 중단점을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-120">You can disable a single breakpoint in one of the following ways:</span></span>  
  
-   <span data-ttu-id="2e45b-121">쿼리 편집기 창에서 중단점을 마우스 오른쪽 단추로 클릭한 다음 **중단점 해제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-121">In the Query Editor window, right-click the breakpoint, and then click **Disable Breakpoint**.</span></span>  
  
-   <span data-ttu-id="2e45b-122">중단점 창에서 중단점 왼쪽에 있는 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-122">In the Breakpoints window, clear the check box to the left of the breakpoint.</span></span>  
  
## <a name="to-disable-all-breakpoints"></a><span data-ttu-id="2e45b-123">모든 중단점을 해제하려면</span><span class="sxs-lookup"><span data-stu-id="2e45b-123">To Disable All Breakpoints</span></span>  
 <span data-ttu-id="2e45b-124">**To disable all breakpoints**</span><span class="sxs-lookup"><span data-stu-id="2e45b-124">**To disable all breakpoints**</span></span>  
  
 <span data-ttu-id="2e45b-125">다음 방법 중 하나를 사용하여 모든 중단점을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-125">You can disable all breakpoints in one of the following ways:</span></span>  
  
-   <span data-ttu-id="2e45b-126">**디버그** 메뉴에서 **모든 중단점 해제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-126">On the **Debug** menu, click **Disable All Breakpoints**.</span></span>  
  
-   <span data-ttu-id="2e45b-127">**중단점** 창의 도구 모음에서 **모든 중단점 해제** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-127">On the toolbar of the **Breakpoints** window, click the **Disable All Breakpoints** button.</span></span>  
  
## <a name="to-enable-a-single-breakpoint"></a><span data-ttu-id="2e45b-128">단일 중단점을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="2e45b-128">To Enable a Single Breakpoint</span></span>  
 <span data-ttu-id="2e45b-129">**To enable a single breakpoint**</span><span class="sxs-lookup"><span data-stu-id="2e45b-129">**To enable a single breakpoint**</span></span>  
  
 <span data-ttu-id="2e45b-130">다음 방법 중 하나를 사용하여 단일 중단점을 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-130">You can enable a single breakpoint in one of the following ways:</span></span>  
  
-   <span data-ttu-id="2e45b-131">쿼리 편집기 창에서 중단점을 마우스 오른쪽 단추로 클릭한 다음 **중단점 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-131">In the Query Editor window, right-click the breakpoint, and then click **Enable Breakpoint**.</span></span>  
  
-   <span data-ttu-id="2e45b-132">중단점 창에서 중단점 왼쪽에 있는 상자를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-132">In the Breakpoints window, click the box to the left of the breakpoint.</span></span>  
  
## <a name="to-enable-all-breakpoints"></a><span data-ttu-id="2e45b-133">모든 중단점을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="2e45b-133">To Enable All Breakpoints</span></span>  
 <span data-ttu-id="2e45b-134">**To enable all breakpoints**</span><span class="sxs-lookup"><span data-stu-id="2e45b-134">**To enable all breakpoints**</span></span>  
  
 <span data-ttu-id="2e45b-135">다음 방법 중 하나를 사용하여 모든 중단점을 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-135">You can enable all breakpoints in one of the following ways:</span></span>  
  
-   <span data-ttu-id="2e45b-136">**디버그** 메뉴에서 **모든 중단점 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-136">On the **Debug** menu, click **Enable All Breakpoints**.</span></span>  
  
-   <span data-ttu-id="2e45b-137">**중단점** 창의 도구 모음에서 **모든 중단점 설정** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-137">On the toolbar of the **Breakpoints** window, click the **Enable All Breakpoints** button.</span></span>  
  
## <a name="to-delete-a-single-breakpoint"></a><span data-ttu-id="2e45b-138">단일 중단점을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="2e45b-138">To Delete a Single Breakpoint</span></span>  
 <span data-ttu-id="2e45b-139">**To delete a single breakpoint**</span><span class="sxs-lookup"><span data-stu-id="2e45b-139">**To delete a single breakpoint**</span></span>  
  
 <span data-ttu-id="2e45b-140">다음 방법 중 하나를 사용하여 단일 중단점을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-140">You can delete a single breakpoint in one of the following ways:</span></span>  
  
-   <span data-ttu-id="2e45b-141">쿼리 편집기 창에서 중단점을 마우스 오른쪽 단추로 클릭한 다음 **중단점 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-141">In the Query Editor window, right-click the breakpoint, and then click **Delete Breakpoint**.</span></span>  
  
-   <span data-ttu-id="2e45b-142">중단점 창에서 중단점을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **삭제** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-142">In the Breakpoints window, right-click the breakpoint, and then click **Delete** on the shortcut menu.</span></span>  
  
-   <span data-ttu-id="2e45b-143">중단점 창에서 중단점을 선택한 다음 Delete 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-143">In the Breakpoints window, select the breakpoint, and then press DELETE.</span></span>  
  
## <a name="to-delete-all-breakpoints"></a><span data-ttu-id="2e45b-144">모든 중단점을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="2e45b-144">To Delete All Breakpoints</span></span>  
 <span data-ttu-id="2e45b-145">**To delete all breakpoints**</span><span class="sxs-lookup"><span data-stu-id="2e45b-145">**To delete all breakpoints**</span></span>  
  
 <span data-ttu-id="2e45b-146">다음 방법 중 하나를 사용하여 모든 중단점을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-146">You can delete all breakpoints in one of the following ways:</span></span>  
  
-   <span data-ttu-id="2e45b-147">**디버그** 메뉴에서 **모든 중단점 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-147">On the **Debug** menu, cllick **Delete All Breakpoints**.</span></span>  
  
-   <span data-ttu-id="2e45b-148">**중단점** 창의 도구 모음에서 **모든 중단점 삭제** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2e45b-148">On the toolbar of the **Breakpoints** window, click the **Delete All Breakpoints** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e45b-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2e45b-149">See Also</span></span>  
 [<span data-ttu-id="2e45b-150">중단점 설정/해제</span><span class="sxs-lookup"><span data-stu-id="2e45b-150">Toggle a Breakpoint</span></span>](../spatial/point.md)  
  
  
