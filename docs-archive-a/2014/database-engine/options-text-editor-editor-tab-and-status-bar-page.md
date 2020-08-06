---
title: '옵션 (텍스트 편집기: 편집기 탭 및 상태 표시줄 페이지) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqleditors.editorcontextsettings
- VS.ToolsOptionsPages.Text_Editor.EditorTabAndStatusBar
ms.assetid: e4815678-7885-4631-878f-c6a2b857ee05
author: rothja
ms.author: jroth
ms.openlocfilehash: 920b7d48b5f7a2472a521af21c8217b1adba486a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659640"
---
# <a name="options-text-editor-editor-tab-and-status-bar-page"></a><span data-ttu-id="93e59-102">옵션(텍스트 편집기: 편집기 탭 및 상태 표시줄 페이지)</span><span class="sxs-lookup"><span data-stu-id="93e59-102">Options (Text Editor: Editor Tab and Status Bar Page)</span></span>
  <span data-ttu-id="93e59-103">**편집기 탭 및 상태 표시줄** 페이지를 사용하여 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 쿼리 편집기에 표시되는 정보를 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-103">The **Editor Tab and Status Bar Page** lets you customize the information displayed by the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] Query Editors.</span></span> <span data-ttu-id="93e59-104">쿼리 편집기 창의 탭 및 상태 표시줄에 표시되는 정보의 수준을 지정하고 상태 표시줄을 편집기 창의 위쪽에 표시할지, 아래쪽에 표시할지를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-104">You can specify the level of information displayed in the tab and status bar of the Query Editor window, and whether the status bar appears at the top or bottom of the editor window.</span></span>  
  
## <a name="option-settings-by-editor"></a><span data-ttu-id="93e59-105">편집기별 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="93e59-105">Option Settings by Editor</span></span>  
 <span data-ttu-id="93e59-106">편집기 탭 및 상태 표시줄은 모든 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 편집기에서 사용할 수 있지만 기능 수준은 저마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-106">The editor tab and the status bar are available in all of the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] editors, but have different levels of functionality.</span></span>  
  
 <span data-ttu-id="93e59-107">데이터베이스 엔진 쿼리 편집기는 서버 그룹에 연결하므로 서버 그룹에 있는 모든 인스턴스에 대한 연결을 열고 각 연결에서 동일한 쿼리를 동시에 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-107">The Database Engine Query Editor can connect to a server group, in which case it opens connections to all the instances in the Server Group and can simultaneously run the same query on each connection.</span></span> <span data-ttu-id="93e59-108">하나의 인스턴스가 아닌 여러 인스턴스에 연결하는 경우 이 대화 상자를 사용하여 상태 표시줄이 각기 다른 색으로 나타나도록 지정할 수 있습니다. 다중 서버 결과 옵션을 변경하려면 [옵션(쿼리 결과/SQL Server/다중 서버)](../../2014/database-engine/options-query-results-sql-server-multi-server.md) 페이지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-108">You can use this dialog to specify that the status bar has different colors when connected to multiple instances rather than one instance.To change the multi-server results options, use the [Options (Query Results/SQL Server/Multi-Server)](../../2014/database-engine/options-query-results-sql-server-multi-server.md) page.</span></span>  
  
## <a name="status-bar-content"></a><span data-ttu-id="93e59-109">상태 표시줄 내용</span><span class="sxs-lookup"><span data-stu-id="93e59-109">Status Bar Content</span></span>  
 <span data-ttu-id="93e59-110">쿼리 편집기 상태 표시줄에 표시할 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-110">Specifies the information that appears in the Query Editor status bar.</span></span>  
  
 <span data-ttu-id="93e59-111">**실행 시간 표시**</span><span class="sxs-lookup"><span data-stu-id="93e59-111">**Display execution time**</span></span>  
 <span data-ttu-id="93e59-112">스크립트 실행 시간을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-112">Includes the script execution time.</span></span> <span data-ttu-id="93e59-113">설정은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-113">The settings are as follows:</span></span>  
  
 <span data-ttu-id="93e59-114">**없음**</span><span class="sxs-lookup"><span data-stu-id="93e59-114">**None**</span></span>  
 <span data-ttu-id="93e59-115">상태 표시줄에서 시간 정보를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-115">The status bar displays no time information.</span></span>  
  
 <span data-ttu-id="93e59-116">**End**</span><span class="sxs-lookup"><span data-stu-id="93e59-116">**End**</span></span>  
 <span data-ttu-id="93e59-117">상태 표시줄에서 스크립트가 실행 중인 현재 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-117">The status bar displays the current time of day while the script is running.</span></span> <span data-ttu-id="93e59-118">스크립트가 완료되면 스크립트가 완료된 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-118">When the script completes, the display shows the time of day that the script completed.</span></span>  
  
 <span data-ttu-id="93e59-119">**시간**</span><span class="sxs-lookup"><span data-stu-id="93e59-119">**Elapsed**</span></span>  
 <span data-ttu-id="93e59-120">상태 표시줄에서 스크립트가 실행된 기간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-120">The status bar displays the length of time that the script has been running.</span></span> <span data-ttu-id="93e59-121">스크립트가 완료되면 스크립트를 실행하는 데 걸린 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-121">When the script completes, the display shows how much time was taken to run the script.</span></span>  
  
 <span data-ttu-id="93e59-122">**데이터베이스 이름 포함**</span><span class="sxs-lookup"><span data-stu-id="93e59-122">**Include database name**</span></span>  
 <span data-ttu-id="93e59-123">연결된 현재 데이터베이스의 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-123">Includes the name of the current database for the connection.</span></span> <span data-ttu-id="93e59-124">쿼리 편집기를 처음 연 경우 로그인의 기본 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-124">When the query editor is first opened, this is the default database for the login.</span></span> <span data-ttu-id="93e59-125">Transact-SQL USE 문을 사용하여 나중에 데이터베이스 컨텍스트를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-125">The database context can later be changed by using the Transact-SQL USE statement.</span></span>  
  
 <span data-ttu-id="93e59-126">**로그인 이름 포함**</span><span class="sxs-lookup"><span data-stu-id="93e59-126">**Include login name**</span></span>  
 <span data-ttu-id="93e59-127">로그인 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-127">Includes the login name.</span></span>  
  
 <span data-ttu-id="93e59-128">**행 개수 포함**</span><span class="sxs-lookup"><span data-stu-id="93e59-128">**Include row count**</span></span>  
 <span data-ttu-id="93e59-129">현재 실행하고 있는 스크립트에서 처리한 행 수를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-129">Includes a count of the rows that have been processed by the script that is currently executing.</span></span>  
  
 <span data-ttu-id="93e59-130">**서버 이름 포함**</span><span class="sxs-lookup"><span data-stu-id="93e59-130">**Include server name**</span></span>  
 <span data-ttu-id="93e59-131">서버 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-131">Includes the server name.</span></span> <span data-ttu-id="93e59-132">로컬 연결의 경우 인스턴스 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-132">For local connections, this is the instance name.</span></span> <span data-ttu-id="93e59-133">원격 연결의 경우 원격 컴퓨터 이름 및 인스턴스 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-133">For remote connections, this is the remote computer name and instance name.</span></span>  
  
## <a name="status-bar-layout-and-colors"></a><span data-ttu-id="93e59-134">상태 표시줄 레이아웃 및 색</span><span class="sxs-lookup"><span data-stu-id="93e59-134">Status Bar Layout and Colors</span></span>  
 <span data-ttu-id="93e59-135">쿼리 편집기 상태 표시줄에서 항목의 색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-135">Specifies the colors for items in the Query Editor status bar.</span></span>  
  
 <span data-ttu-id="93e59-136">**그룹 연결**</span><span class="sxs-lookup"><span data-stu-id="93e59-136">**Group connections**</span></span>  
 <span data-ttu-id="93e59-137">쿼리 편집기가 둘 이상의 서버에 연결된 경우 상태 표시줄 색을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-137">Set the color of the status bar when the Query Editor has more than one connection.</span></span>  
  
 <span data-ttu-id="93e59-138">**단일 서버 연결**</span><span class="sxs-lookup"><span data-stu-id="93e59-138">**Single server connections**</span></span>  
 <span data-ttu-id="93e59-139">쿼리 편집기가 하나의 서버에 연결된 경우 상태 표시줄 색을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-139">Set the color of the status bar when the Query Editor has one connection.</span></span>  
  
 <span data-ttu-id="93e59-140">**상태 표시줄 위치**</span><span class="sxs-lookup"><span data-stu-id="93e59-140">**Status bar location**</span></span>  
 <span data-ttu-id="93e59-141">상태 표시줄 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-141">Specifies the location of the status bar.</span></span> <span data-ttu-id="93e59-142">설정은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-142">The settings are as follows:</span></span>  
  
 <span data-ttu-id="93e59-143">**상위**</span><span class="sxs-lookup"><span data-stu-id="93e59-143">**Top**</span></span>  
 <span data-ttu-id="93e59-144">상태 표시줄이 쿼리 편집기 창 위쪽에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-144">The status bar appears at the top of the Query Editor window.</span></span>  
  
 <span data-ttu-id="93e59-145">**아래쪽**</span><span class="sxs-lookup"><span data-stu-id="93e59-145">**Bottom**</span></span>  
 <span data-ttu-id="93e59-146">상태 표시줄이 쿼리 편집기 창 아래쪽에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-146">The status bar appears at the bottom of the Query Editor window.</span></span>  
  
## <a name="tab-text"></a><span data-ttu-id="93e59-147">탭 텍스트</span><span class="sxs-lookup"><span data-stu-id="93e59-147">Tab Text</span></span>  
 <span data-ttu-id="93e59-148">쿼리 편집기 창 위쪽에 있는 탭에 표시할 텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-148">Specifies the text that appears in the tab at the top of a Query Editor window.</span></span> <span data-ttu-id="93e59-149">텍스트가 너무 길어 일부가 표시되지 않은 경우 마우스를 탭으로 이동하면 표시되는 도구 설명에서 전체 문자열을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-149">If the text is too long to display, you can view the full string in a tooltip that is displayed if you hover over the tab.</span></span>  
  
 <span data-ttu-id="93e59-150">**데이터베이스 이름 포함**</span><span class="sxs-lookup"><span data-stu-id="93e59-150">**Include database name**</span></span>  
 <span data-ttu-id="93e59-151">연결된 현재 데이터베이스의 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-151">Includes the name of the current database for the connection.</span></span> <span data-ttu-id="93e59-152">쿼리 편집기를 처음 연 경우 로그인의 기본 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-152">When the query editor is first opened, this is the default database for the login.</span></span> <span data-ttu-id="93e59-153">Transact-SQL USE 문을 사용하여 나중에 데이터베이스 컨텍스트를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-153">The database context can later be changed by using the Transact-SQL USE statement.</span></span>  
  
 <span data-ttu-id="93e59-154">**파일 이름 포함**</span><span class="sxs-lookup"><span data-stu-id="93e59-154">**Include file name**</span></span>  
 <span data-ttu-id="93e59-155">스크립트가 저장된 파일의 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-155">Includes the name of the file where the script is stored.</span></span>  
  
 <span data-ttu-id="93e59-156">**폴더 이름 포함**</span><span class="sxs-lookup"><span data-stu-id="93e59-156">**Include folder name**</span></span>  
 <span data-ttu-id="93e59-157">스크립트 파일이 저장된 폴더의 경로를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-157">Includes the path of the folder where the script file is stored.</span></span>  
  
 <span data-ttu-id="93e59-158">**로그인 이름 포함**</span><span class="sxs-lookup"><span data-stu-id="93e59-158">**Include login name**</span></span>  
 <span data-ttu-id="93e59-159">로그인 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-159">Includes the login name.</span></span>  
  
 <span data-ttu-id="93e59-160">**서버 이름 포함**</span><span class="sxs-lookup"><span data-stu-id="93e59-160">**Include server name**</span></span>  
 <span data-ttu-id="93e59-161">서버 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-161">Includes the server name.</span></span> <span data-ttu-id="93e59-162">로컬 연결의 경우 인스턴스 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-162">For local connections, this is the instance name.</span></span> <span data-ttu-id="93e59-163">원격 연결의 경우 원격 컴퓨터 이름 및 인스턴스 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="93e59-163">For remote connections, this is the remote computer name and instance name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93e59-164">참고 항목</span><span class="sxs-lookup"><span data-stu-id="93e59-164">See Also</span></span>  
 <span data-ttu-id="93e59-165">[옵션 &#40;환경: 글꼴 및 색 페이지&#41;](../ssms/menu-help/options-environment-fonts-and-colors-page.md) </span><span class="sxs-lookup"><span data-stu-id="93e59-165">[Options &#40;Environment: Fonts and Colors Page&#41;](../ssms/menu-help/options-environment-fonts-and-colors-page.md) </span></span>  
 [<span data-ttu-id="93e59-166">쿼리 편집기에서 코드 색상 지정</span><span class="sxs-lookup"><span data-stu-id="93e59-166">Color Coding in Query Editors</span></span>](../relational-databases/scripting/color-coding-in-query-editors.md)  
  
  
