---
title: 원본 제어 옵션 설정 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Source_Control.Visual_SourceSafe
- VS.ToolsOptionsPages.Source_Control.General
- VS.ToolsOptionsPages.Source_Control.Environment
helpviewer_keywords:
- source controls [SQL Server Management Studio], options
ms.assetid: b2c6ca00-46f0-4f86-b067-07bae779c147
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d4ca19180a7291763780f300172bb2292a98c8c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646621"
---
# <a name="set-source-control-options"></a><span data-ttu-id="13658-102">원본 제어 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="13658-102">Set Source Control Options</span></span>
  <span data-ttu-id="13658-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에 내장된 원본 제어 기능을 활용하기 전에 작업을 수행하는 다양한 환경에 대한 원본 제어 옵션을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-103">Before you take advantage of the source control features built into [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], you should configure your source control options for the various environments in which you work.</span></span>  
  
 <span data-ttu-id="13658-104">**옵션** 대화 상자를 사용 하 여 소스 제어 역할을 하나 이상 구성 하 여 원본 제어 옵션을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-104">You configure source control options by using the **Options** dialog box to configure one or more source control roles.</span></span> <span data-ttu-id="13658-105">역할은 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에 적용되는 설정에 대한 일반적인 설명과 해당 설정에 연결된 원본 제어 옵션으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="13658-105">A role consists of a general description of the setting in which you use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], and the source control options associated with that setting.</span></span>  
  
 <span data-ttu-id="13658-106">예를 들어 독자적 데이터베이스 개발자인 경우 일반적으로 파일을 체크 인한 후에 파일을 체크 아웃된 상태로 유지함으로써 다른 사용자와의 충돌을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-106">For example, if you are an independent database developer, you generally do not create conflicts with other users by keeping files checked out after you check them in.</span></span> <span data-ttu-id="13658-107">결과적으로 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]는 독자적 개발자 역할을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-107">Consequently, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] defines an Independent Developer role.</span></span> <span data-ttu-id="13658-108">이 역할의 경우는 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] **체크 인할 때 항목을 체크 아웃 상태로 유지** 옵션을 자동으로 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-108">For this role, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] automatically selects the **Keep items checked out when checking in** option.</span></span>  
  
 <span data-ttu-id="13658-109">역할을 정의하고 사용자 지정할 수 있기 때문에 특정 설정에서 다른 설정으로 이동할 때마다 원본 제어를 완전히 다시 구성할 필요 없이 다양한 개발 설정에서 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13658-109">Because you can define and customize roles, you can work in varying development settings without having to completely reconfigure source control every time you move from one setting to another.</span></span>  
  
### <a name="to-set-source-control-options"></a><span data-ttu-id="13658-110">원본 제어 옵션을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="13658-110">To set source control options</span></span>  
  
1.  <span data-ttu-id="13658-111">**도구** 메뉴에서 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-111">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="13658-112">**옵션** 대화 상자에서 **소스 제어**를 확장 한 다음 **플러그 인 선택** 페이지를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-112">In the **Options** dialog box, expand **Source Control**, and then click the **Plug-in Selection** page.</span></span>  
  
     <span data-ttu-id="13658-113">**현재 원본 제어 플러그 인**</span><span class="sxs-lookup"><span data-stu-id="13658-113">**Current source control plug-in**</span></span>  
     <span data-ttu-id="13658-114">사용할 원본 제어를 이 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-114">Select the source control you want to use from this list.</span></span> <span data-ttu-id="13658-115">컴퓨터에 설치되어 있는 원본 제어 제품 클라이언트만 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="13658-115">The source control product client must be installed on this computer to appear on the list.</span></span> <span data-ttu-id="13658-116">컴퓨터에 원본 제어 클라이언트가 설치되어 있지 않으면 없음만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="13658-116">If no source control clients are installed on the computer, the only selection available will be None.</span></span> <span data-ttu-id="13658-117">Microsoft Source Safe를 설치한 경우 다음 플러그 인이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="13658-117">If you have installed Microsoft Source Safe, then the following plug ins are displayed:</span></span>  
  
    -   <span data-ttu-id="13658-118">Microsoft Visual SourceSafe</span><span class="sxs-lookup"><span data-stu-id="13658-118">Microsoft Visual SourceSafe</span></span>  
  
    -   <span data-ttu-id="13658-119">Microsoft Visual SourceSafe(Internet)</span><span class="sxs-lookup"><span data-stu-id="13658-119">Microsoft Visual SourceSafe(Internet)</span></span>  
  
3.  <span data-ttu-id="13658-120">사용하려는 각 원본 제어 역할에 대한 로그인 자격 증명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-120">Set login credentials for each source control role that you want to use.</span></span> <span data-ttu-id="13658-121">이 페이지는 원본 제어 플러그 인이 설치된 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13658-121">This page is only available if a source control plug-in is installed.</span></span>  
  
     <span data-ttu-id="13658-122">**역할 설명**</span><span class="sxs-lookup"><span data-stu-id="13658-122">**Role Description**</span></span>  
     <span data-ttu-id="13658-123">이 역할 중 하나를 선택하면 적절한 원본 제어 옵션이 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="13658-123">Selecting one of these roles causes the appropriate source control options to be selected automatically.</span></span>  
  
    |<span data-ttu-id="13658-124">역할</span><span class="sxs-lookup"><span data-stu-id="13658-124">Role</span></span>|<span data-ttu-id="13658-125">설명</span><span class="sxs-lookup"><span data-stu-id="13658-125">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="13658-126">**Visual SourceSafe**</span><span class="sxs-lookup"><span data-stu-id="13658-126">**Visual SourceSafe**</span></span>|<span data-ttu-id="13658-127">Visual SourceSafe 사용자가 가장 일반적으로 사용 하는 설정을 사용 하도록 지정 합니다 [!INCLUDE[msCoName](../includes/msconame-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="13658-127">Specifies that you want to use the settings most commonly used by [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe users.</span></span>|  
    |<span data-ttu-id="13658-128">**독자적 개발자**</span><span class="sxs-lookup"><span data-stu-id="13658-128">**Independent Developer**</span></span>|<span data-ttu-id="13658-129">사용자가 독자적으로 작업하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-129">Specifies that you are working independently.</span></span>|  
    |<span data-ttu-id="13658-130">**사용자 지정**</span><span class="sxs-lookup"><span data-stu-id="13658-130">**Custom**</span></span>|<span data-ttu-id="13658-131">사용자가 역할에 대한 설정을 수정했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="13658-131">Specifies that you have modified the settings for a role.</span></span>|  
  
     <span data-ttu-id="13658-132">**백그라운드 상태 업데이트 수행**</span><span class="sxs-lookup"><span data-stu-id="13658-132">**Perform background status updates**</span></span>  
     <span data-ttu-id="13658-133">항목의 상태가 변경될 때 솔루션 탐색기의 원본 제어 신호 아이콘을 자동으로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-133">Automatically updates the source control signal icons in Solution Explorer as an item's status changes.</span></span> <span data-ttu-id="13658-134">특히 원본 제어에서 솔루션이나 프로젝트를 열 때와 같이 서버를 많이 사용하는 작업을 수행할 때 지연이 발생하면 이 확인란의 선택을 취소하여 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13658-134">If you experience delays when performing server-intensive operations, especially when opening a solution or project from source control, clearing this check box could improve performance.</span></span>  
  
     <span data-ttu-id="13658-135">**로그인 ID**</span><span class="sxs-lookup"><span data-stu-id="13658-135">**Login ID**</span></span>  
     <span data-ttu-id="13658-136">소스 제어 공급자에 로그인하는 데 사용할 사용자 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-136">Specifies the user name to use to log in to the source control provider.</span></span> <span data-ttu-id="13658-137">원본 제어 공급자가 지 원하는 경우이 이름은 **로그인** 대화 상자에 자동으로 입력 되어 원본 제어 서버에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="13658-137">If supported by your source control provider, this name will be filled in automatically in the **Login** dialog box to reach your source control server.</span></span> <span data-ttu-id="13658-138">이 옵션을 활성화하려면 원본 제어 공급자의 관리자 프로그램을 사용하여 자동 사용자 로그인을 비활성화한 다음 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-138">To make this option active, disable automatic user logins by using your source control provider's administrator program, and then restart [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
     <span data-ttu-id="13658-139">**고급**</span><span class="sxs-lookup"><span data-stu-id="13658-139">**Advanced**</span></span>  
     <span data-ttu-id="13658-140">소스 제어에 항목을 추가하기 위한 추가 옵션을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-140">Displays additional options for adding items to source control.</span></span> <span data-ttu-id="13658-141">이러한 옵션은 원본 제어 공급자에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="13658-141">These options vary depending on your source control provider.</span></span> <span data-ttu-id="13658-142">이러한 옵션에 대한 도움말은 원본 제어 프로그램에서 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-142">Help for these options is provided by the source control program.</span></span>  
  
4.  <span data-ttu-id="13658-143">**환경** 페이지를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-143">Select the **Environment** page.</span></span>  
  
5.  <span data-ttu-id="13658-144">**원본 제어 환경 설정** 상자에서 소스 제어 옵션을 설정 하려는 역할을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-144">In the **Source Control Environment Settings** box, select the role on which you want to set source control options.</span></span>  
  
     [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]<span data-ttu-id="13658-145">는 선택한 역할에 대한 기본 원본 제어 옵션을 자동으로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-145">automatically selects the default source control options for the role you have selected.</span></span> <span data-ttu-id="13658-146">기본 옵션을 선택 취소 하면 **원본 제어 환경 설정** 상자에 **사용자 지정** 옵션이 표시 되어 원래 선택한 역할을 사용자 지정 했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="13658-146">If you clear any of the default options, the **Source Control Environment Settings** box displays the **Custom** option to indicate that you have customized the originally selected role.</span></span>  
  
     <span data-ttu-id="13658-147">**소스 제어 환경 설정**</span><span class="sxs-lookup"><span data-stu-id="13658-147">**Source Control Environment Settings**</span></span>  
     <span data-ttu-id="13658-148">사용할 역할을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-148">Specifies the role that you want to use.</span></span> [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]<span data-ttu-id="13658-149">는 다음 역할을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-149">defines the following roles.</span></span>  
  
    |<span data-ttu-id="13658-150">역할</span><span class="sxs-lookup"><span data-stu-id="13658-150">Role</span></span>|<span data-ttu-id="13658-151">설명</span><span class="sxs-lookup"><span data-stu-id="13658-151">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="13658-152">**Visual SourceSafe**</span><span class="sxs-lookup"><span data-stu-id="13658-152">**Visual SourceSafe**</span></span>|<span data-ttu-id="13658-153">Visual SourceSafe 사용자가 가장 일반적으로 사용 하는 설정을 사용 하도록 지정 합니다 [!INCLUDE[msCoName](../includes/msconame-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="13658-153">Specifies that you want to use the settings most commonly used by [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe users.</span></span>|  
    |<span data-ttu-id="13658-154">**독자적 개발자**</span><span class="sxs-lookup"><span data-stu-id="13658-154">**Independent Developer**</span></span>|<span data-ttu-id="13658-155">사용자가 독자적으로 작업하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-155">Specifies that you are working independently.</span></span>|  
    |<span data-ttu-id="13658-156">**사용자 지정**</span><span class="sxs-lookup"><span data-stu-id="13658-156">**Custom**</span></span>|<span data-ttu-id="13658-157">사용자가 역할에 대한 설정을 수정했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="13658-157">Specifies that you have modified the settings for a role.</span></span>|  
  
     <span data-ttu-id="13658-158">이 역할 중 하나를 선택하면 적절한 원본 제어 옵션이 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="13658-158">Selecting one of these roles causes the appropriate source control options to be selected automatically.</span></span>  
  
     <span data-ttu-id="13658-159">**체크 인할 때 항목을 체크 아웃 상태로 유지**</span><span class="sxs-lookup"><span data-stu-id="13658-159">**Keep items checked out when checking in**</span></span>  
     <span data-ttu-id="13658-160">소스 제어 저장소를 업데이트하기 위해 항목을 체크 인할 때 사용자에게는 해당 항목이 체크 아웃된 상태로 유지되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-160">Specifies that when you check in items to update the source control store, the items should remain checked out to you.</span></span> <span data-ttu-id="13658-161">특정 체크 인에 대해이 옵션을 변경 하려면 **체크** 인 대화 상자에서 **옵션** 화살표를 클릭 한 다음 **체크 아웃 유지** 확인란의 선택을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-161">If you want to change this option for a specific check-in, click the **Options** arrow in the **Check in** dialog box, and then clear the **Keep checked out** check box.</span></span>  
  
     <span data-ttu-id="13658-162">**체크 인된 항목**</span><span class="sxs-lookup"><span data-stu-id="13658-162">**Checked-in items**</span></span>  
     <span data-ttu-id="13658-163">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]체크 아웃 되지 않은 항목을 편집 하려고 할 때 동작을 수행 하는 방법을 지정 하는 옵션 목록을 표시 합니다. 다음 표에서는 사용 가능한 옵션에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-163">Displays a list of options that specify how [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] should behave when you attempt to edit an item that is not checked out. The following tables describe the available options.</span></span>  
  
     <span data-ttu-id="13658-164">**Saving**</span><span class="sxs-lookup"><span data-stu-id="13658-164">**Saving**</span></span>  
  
    |<span data-ttu-id="13658-165">작업</span><span class="sxs-lookup"><span data-stu-id="13658-165">Action</span></span>|<span data-ttu-id="13658-166">설명</span><span class="sxs-lookup"><span data-stu-id="13658-166">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="13658-167">**체크 아웃 확인**</span><span class="sxs-lookup"><span data-stu-id="13658-167">**Prompt for check out**</span></span>|<span data-ttu-id="13658-168">**체크 아웃** 대화 상자를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-168">Displays the **Check Out** dialog box.</span></span>|  
    |<span data-ttu-id="13658-169">**자동으로 체크 아웃**</span><span class="sxs-lookup"><span data-stu-id="13658-169">**Check out automatically**</span></span>|<span data-ttu-id="13658-170">**체크 아웃** 대화 상자를 표시 하지 않고 항목을 체크 아웃 합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-170">Checks out the item without displaying the **Check Out** dialog box.</span></span> <span data-ttu-id="13658-171">기본 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="13658-171">This is the default option.</span></span>|  
    |<span data-ttu-id="13658-172">**다른 이름으로 저장**</span><span class="sxs-lookup"><span data-stu-id="13658-172">**Save as**</span></span>|<span data-ttu-id="13658-173">새 파일로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-173">Saves as a new file.</span></span>|  
  
     <span data-ttu-id="13658-174">**편집 중**</span><span class="sxs-lookup"><span data-stu-id="13658-174">**Editing**</span></span>  
  
    |<span data-ttu-id="13658-175">작업</span><span class="sxs-lookup"><span data-stu-id="13658-175">Action</span></span>|<span data-ttu-id="13658-176">설명</span><span class="sxs-lookup"><span data-stu-id="13658-176">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="13658-177">**체크 아웃 확인**</span><span class="sxs-lookup"><span data-stu-id="13658-177">**Prompt for check out**</span></span>|<span data-ttu-id="13658-178">**체크 아웃** 대화 상자를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-178">Displays the **Check Out** dialog box.</span></span>|  
    |<span data-ttu-id="13658-179">**단독 체크 아웃 확인**</span><span class="sxs-lookup"><span data-stu-id="13658-179">**Prompt for exclusive checkouts**</span></span>|<span data-ttu-id="13658-180">**체크 아웃** 대화 상자를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-180">Displays the **Check Out** dialog box.</span></span>|  
    |<span data-ttu-id="13658-181">**자동으로 체크 아웃**</span><span class="sxs-lookup"><span data-stu-id="13658-181">**Check out automatically**</span></span>|<span data-ttu-id="13658-182">**체크 아웃** 대화 상자를 표시 하지 않고 항목을 체크 아웃 합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-182">Checks out the item without displaying the **Check Out** dialog box.</span></span> <span data-ttu-id="13658-183">기본 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="13658-183">This is the default option.</span></span>|  
    |<span data-ttu-id="13658-184">**아무 작업도 수행하지 않음**</span><span class="sxs-lookup"><span data-stu-id="13658-184">**Do nothing**</span></span>|<span data-ttu-id="13658-185">파일을 체크 아웃하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="13658-185">Does not check out the file.</span></span>|  
  
     <span data-ttu-id="13658-186">**체크 인한 항목 편집 허용**</span><span class="sxs-lookup"><span data-stu-id="13658-186">**Allow checked-in items to be edited**</span></span>  
     <span data-ttu-id="13658-187">체크 인한 항목을 메모리에서 편집할 수 있도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-187">Specifies that items that are checked in can be edited in memory.</span></span> <span data-ttu-id="13658-188">이 확인란을 선택 하면 체크 인 된 항목을 편집 하려고 할 때 **체크 아웃** 대화 상자에 **편집** 단추가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="13658-188">If you select this check box, an **Edit** button appears in the **Check Out** dialog box when you attempt to edit a checked-in item.</span></span> <span data-ttu-id="13658-189">이 단추를 클릭한 후 항목을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13658-189">After clicking this button, you can edit the item.</span></span> <span data-ttu-id="13658-190">항목을 저장하려면 체크 아웃하거나 다른 위치에 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13658-190">If you attempt to save the item, you must check it out or save it to a different location.</span></span>  
  
     <span data-ttu-id="13658-191">**재설정**</span><span class="sxs-lookup"><span data-stu-id="13658-191">**Reset**</span></span>  
     <span data-ttu-id="13658-192">소스 제어 환경 대화 상자의 설정을 기본 설정으로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="13658-192">Resets source control confirmation dialog boxes to their default settings.</span></span> <span data-ttu-id="13658-193">예를 들어 원본 제어 대화 상자에서 **이 대화 상자를 다시 표시 안 함** 확인란을 선택한 경우 **다시 설정** 옵션을 선택 하면 해당 작업이 취소 됩니다.</span><span class="sxs-lookup"><span data-stu-id="13658-193">For example, if you have selected the **Don't show this dialog again** check box in a source control dialog box, selecting the **Reset** option reverses that action.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13658-194">참고 항목</span><span class="sxs-lookup"><span data-stu-id="13658-194">See Also</span></span>  
 <span data-ttu-id="13658-195">[원본 제어 기본 사항](../../2014/database-engine/source-control-basics.md) </span><span class="sxs-lookup"><span data-stu-id="13658-195">[Source Control Basics](../../2014/database-engine/source-control-basics.md) </span></span>  
 <span data-ttu-id="13658-196">[원본 제어 연결 변경](../../2014/database-engine/change-source-control-connections.md) </span><span class="sxs-lookup"><span data-stu-id="13658-196">[Change Source Control Connections](../../2014/database-engine/change-source-control-connections.md) </span></span>  
 [<span data-ttu-id="13658-197">소스 제어에서 파일 제외</span><span class="sxs-lookup"><span data-stu-id="13658-197">Exclude Files from Source Control</span></span>](../../2014/database-engine/exclude-files-from-source-control.md)  
  
  
