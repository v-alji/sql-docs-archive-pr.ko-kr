---
title: 오류 목록 창
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- error list window
- SQL Server Management Studio [SQL Server], error list window
ms.assetid: fae6327d-e268-44ae-a474-4a8f8f843129
author: rothja
ms.author: jroth
ms.openlocfilehash: 00455c339344b7b38a48500c49d139aa52df6116
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660472"
---
# <a name="error-list-window-management-studio"></a><span data-ttu-id="4dfd5-102">오류 목록 창(Management Studio)</span><span class="sxs-lookup"><span data-stu-id="4dfd5-102">Error List Window (Management Studio)</span></span>
  <span data-ttu-id="4dfd5-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **오류 목록**은 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기의 IntelliSense 코드에서 생성된 구문 및 의미 체계 오류를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-103">The [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Error List** displays the syntax and semantic errors that are generated from the IntelliSense code in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span>  
  
## <a name="features-of-the-error-list"></a><span data-ttu-id="4dfd5-104">오류 목록의 기능</span><span class="sxs-lookup"><span data-stu-id="4dfd5-104">Features of the Error List</span></span>  
 <span data-ttu-id="4dfd5-105">**오류 목록** 은 다음 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-105">The **Error List** provides the following functionality:</span></span>  
  
-   <span data-ttu-id="4dfd5-106">스크립트를 편집할 때 **오류 목록** 은 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기의 IntelliSense에 의해 생성되는 오류 및 경고를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-106">As you edit scripts, the **Error List** displays the errors and warnings produced by IntelliSense in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span>  
  
-   <span data-ttu-id="4dfd5-107">오류 메시지 항목을 두 번 클릭하여 오류를 생성한 스크립트 파일의 탭에 포커스를 두고 오류 위치로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-107">You can double-click any error message entry to focus on the tab for the script file that generated the error, and move to the error location.</span></span>  
  
-   <span data-ttu-id="4dfd5-108">표시되는 항목 및 각 항목에 대해 표시되는 정보 열을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-108">You can filter which entries you want to display, and which columns of information you want appear for each entry.</span></span>  
  
-   <span data-ttu-id="4dfd5-109">오류를 수정하면 해당 오류 항목이 **오류 목록**에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-109">After you fix an error, the error entry is removed from the **Error List**.</span></span>  
  
-   <span data-ttu-id="4dfd5-110">[!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트 파일 탭을 닫으면 해당 파일에 대한 오류가 **오류 목록**에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-110">When you close the tab for a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file, the errors for that file are removed from the **Error List**.</span></span>  
  
## <a name="working-with-the-error-list"></a><span data-ttu-id="4dfd5-111">오류 목록 작업</span><span class="sxs-lookup"><span data-stu-id="4dfd5-111">Working with the Error List</span></span>  
 <span data-ttu-id="4dfd5-112">**오류 목록**을 표시하려면 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-112">To display the **Error List**, do one of the following:</span></span>  
  
-   <span data-ttu-id="4dfd5-113">**보기** 메뉴에서 **오류 목록**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-113">On the **View** menu, click **Error List**.</span></span>  
  
-   <span data-ttu-id="4dfd5-114">Ctrl+\\, Ctrl+E 바로 가기 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-114">Enter the keyboard shortcut CTRL+\\, CTRL+E.</span></span>  
  
 <span data-ttu-id="4dfd5-115">**오류 목록**을 연 후에는 다음 동작을 수행하여 보기를 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-115">After you open the **Error List**, you can customize your view by performing the following actions:</span></span>  
  
-   <span data-ttu-id="4dfd5-116">목록을 정렬하려면 열 머리글을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-116">To sort the list, click any column header.</span></span> <span data-ttu-id="4dfd5-117">추가 열을 기준으로 다시 정렬하려면 Shift 키를 누른 상태에서 다른 열 머리글을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-117">To sort again by an additional column, press and hold the SHIFT key, and then click another column header.</span></span>  
  
-   <span data-ttu-id="4dfd5-118">표시할 열과 숨길 열을 선택하려면 바로 가기 메뉴에서 **열 표시** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-118">To select which columns are displayed and which are hidden, select **Show Columns** from the shortcut menu.</span></span>  
  
-   <span data-ttu-id="4dfd5-119">열이 표시되는 순서를 변경하려면 열 머리글을 왼쪽이나 오른쪽으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-119">To change the order in which columns are displayed, drag any column header to the left or right.</span></span>  
  
 <span data-ttu-id="4dfd5-120">**오류 목록** 은 특정 오류에 대한 추가 정보로 연결되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-120">The **Error List** does not link to additional information about specific errors.</span></span>  
  
## <a name="transact-sql-errors-in-management-studio"></a><span data-ttu-id="4dfd5-121">Management Studio의 Transact-SQL 오류</span><span class="sxs-lookup"><span data-stu-id="4dfd5-121">Transact-SQL Errors in Management Studio</span></span>  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="4dfd5-122">는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트에 대한 오류를 다음 위치에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-122">displays errors for [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts in the following locations:</span></span>  
  
-   <span data-ttu-id="4dfd5-123">**오류 목록** 에는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 편집기의 IntelliSense에서 발견한 모든 구문 및 의미 체계 오류가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-123">The **Error List** contains all syntax and semantic errors found by IntelliSense in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Editor.</span></span> <span data-ttu-id="4dfd5-124">이 오류 목록은 사용자가 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트를 편집할 때 동적으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-124">This list of errors is dynamically updated as you edit [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts.</span></span> <span data-ttu-id="4dfd5-125">목록에는 편집기가 각 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트에서 발견한 모든 오류가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-125">The list includes all errors that the editor has found in each [!INCLUDE[tsql](../../includes/tsql-md.md)] script.</span></span> <span data-ttu-id="4dfd5-126">편집기는 스크립트에서 오류를 발견해도 파일의 구문 분석을 중지하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-126">The editor does not stop parsing a file after encountering errors in a script.</span></span> <span data-ttu-id="4dfd5-127">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 편집기의 IntelliSense는 일부 [!INCLUDE[tsql](../../includes/tsql-md.md)] 구문 요소를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-127">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], IntelliSense in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Editor does not support all [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax elements.</span></span> <span data-ttu-id="4dfd5-128">**오류 목록** 에는 IntelliSense에서 지원하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 구문의 오류만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-128">The **Error List** contains only errors from the [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax that is supported by IntelliSense.</span></span>  
  
-   <span data-ttu-id="4dfd5-129">**쿼리 편집기 창의 아래쪽에 있는** 메시지 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 탭에는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 스크립트가 실행될 때 [!INCLUDE[tsql](../../includes/tsql-md.md)] 에서 반환하는 모든 오류 및 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-129">The **Messages** tab at the bottom of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window displays all errors and messages that are returned by the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] when a [!INCLUDE[tsql](../../includes/tsql-md.md)] script is executed.</span></span> <span data-ttu-id="4dfd5-130">이 목록은 스크립트를 다시 실행하기 전에는 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-130">This list does not change until you execute the script again.</span></span> <span data-ttu-id="4dfd5-131">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 한 개 또는 두 개의 컴파일 오류를 발견한 경우 일괄 처리 구문 분석을 중지하므로 **메시지** 탭에 포함되지 않는 스크립트 오류가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-131">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] stops parsing a batch after it finds one or two compile errors; therefore, the **Messages** tab might not list all errors in a script.</span></span>  
  
 <span data-ttu-id="4dfd5-132">두 위치 모두에 오류가 나열되는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-132">Sometimes errors are listed in both locations.</span></span> <span data-ttu-id="4dfd5-133">예를 들어 스크립트 파일에 **오류 목록**에 나열된 구문 오류가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-133">For example, a script file might have a syntax error that is listed in the **Error List**.</span></span> <span data-ttu-id="4dfd5-134">이 오류를 수정하기 전에 스크립트를 실행하면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 파서가 동일한 조건을 검색하고 **메시지** 탭에 똑같은 오류 메시지를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-134">If you execute the script before you correct the error, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] parser can detect the same condition and return another copy of the error message in the **Messages** tab.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4dfd5-135">**오류 목록** 에는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기의 오류만 표시되며 MDX, DMX 또는 XML/A 편집기의 오류는 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-135">The **Error List** only displays errors from the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor; it does not display errors from the MDX, DMX, or XML/A Editors.</span></span> <span data-ttu-id="4dfd5-136">모든 MDX, DMX 및 XML/A 오류는 해당 편집기의 **메시지** 탭에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-136">All MDX, DMX, and XML/A errors are displayed in the **Messages** tab in those editors.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="4dfd5-137">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="4dfd5-137">UI element list</span></span>  
 <span data-ttu-id="4dfd5-138">**오류 목록** 을 열면 다음 열에 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-138">When the **Error List** is open, the information is displayed in the following columns:</span></span>  
  
 <span data-ttu-id="4dfd5-139">**기본 순서**</span><span class="sxs-lookup"><span data-stu-id="4dfd5-139">**Default Order**</span></span>  
 <span data-ttu-id="4dfd5-140">항목이 생성된 순서를 나타내는 정수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-140">Displays an integer that indicates the order in which an entry was generated.</span></span>  
  
 <span data-ttu-id="4dfd5-141">**설명**</span><span class="sxs-lookup"><span data-stu-id="4dfd5-141">**Description**</span></span>  
 <span data-ttu-id="4dfd5-142">오류 항목의 텍스트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-142">Displays the text of the error entry.</span></span> <span data-ttu-id="4dfd5-143">설명이 길어지면 다음 줄로 줄 바꿈됩니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-143">Lengthy descriptions wrap onto additional lines.</span></span>  
  
 <span data-ttu-id="4dfd5-144">**최근에 사용한 파일**</span><span class="sxs-lookup"><span data-stu-id="4dfd5-144">**File**</span></span>  
 <span data-ttu-id="4dfd5-145">오류를 생성한 스크립트 파일의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-145">Displays the name of the script file that generated the error.</span></span>  
  
 <span data-ttu-id="4dfd5-146">**선**</span><span class="sxs-lookup"><span data-stu-id="4dfd5-146">**Line**</span></span>  
 <span data-ttu-id="4dfd5-147">오류가 포함된 코드 줄을 나타내는 정수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-147">Displays an integer that indicates which line of the code includes the error.</span></span>  
  
 <span data-ttu-id="4dfd5-148">**열**</span><span class="sxs-lookup"><span data-stu-id="4dfd5-148">**Column**</span></span>  
 <span data-ttu-id="4dfd5-149">코드 줄에서 오류의 위치를 나타내는 정수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-149">Displays an integer that indicates the position of the error in the line of code.</span></span>  
  
 <span data-ttu-id="4dfd5-150">**프로젝트**</span><span class="sxs-lookup"><span data-stu-id="4dfd5-150">**Project**</span></span>  
 <span data-ttu-id="4dfd5-151">스크립트 파일이 포함된 프로젝트의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4dfd5-151">Displays the name of the project that includes the script file.</span></span>  
