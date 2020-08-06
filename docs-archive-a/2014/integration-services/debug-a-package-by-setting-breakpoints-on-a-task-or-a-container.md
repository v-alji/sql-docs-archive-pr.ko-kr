---
title: 태스크 또는 컨테이너에 중단점을 설정 하 여 패키지 디버그 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], breakpoints
- breakpoints [Integration Services]
- tasks [Integration Services], breakpoints
ms.assetid: e7fa106a-2221-403a-bb74-efc9f12bb450
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 21e334faff95e63e59bbf9c40fdf7e479de949da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647762"
---
# <a name="debug-a-package-by-setting-breakpoints-on-a-task-or-a-container"></a><span data-ttu-id="e3442-102">태스크 또는 컨테이너에 중단점을 설정하여 패키지 디버깅</span><span class="sxs-lookup"><span data-stu-id="e3442-102">Debug a Package by Setting Breakpoints on a Task or a Container</span></span>
  <span data-ttu-id="e3442-103">이 절차에서는 패키지, 태스크, For 루프 컨테이너, Foreach 루프 컨테이너 또는 시퀀스 컨테이너에 중단점을 설정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e3442-103">This procedure describes how to set breakpoints in a package, a task, a For Loop container, a Foreach Loop container, or a Sequence container.</span></span>  
  
### <a name="to-set-breakpoints-in-a-package-a-task-or-a-container"></a><span data-ttu-id="e3442-104">패키지, 태스크 또는 컨테이너에 중단점을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="e3442-104">To set breakpoints in a package, a task, or a container</span></span>  
  
1.  <span data-ttu-id="e3442-105">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e3442-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="e3442-106">중단점을 설정할 패키지를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e3442-106">Double-click the package in which you want to set breakpoints.</span></span>  
  
3.  <span data-ttu-id="e3442-107">SSIS 디자이너에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e3442-107">In SSIS Designer, do the following:</span></span>  
  
    -   <span data-ttu-id="e3442-108">패키지 개체에 중단점을 설정하려면 **제어 흐름** 탭을 클릭하고 디자인 화면에 아무 곳에 커서를 놓고 마우스 오른쪽 단추를 클릭한 다음 **중단점 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e3442-108">To set breakpoints in the package object, click the **Control Flow** tab, place the cursor anywhere on the background of the design surface, right-click, and then click **Edit Breakpoints**.</span></span>  
  
    -   <span data-ttu-id="e3442-109">패키지 제어 흐름에 중단점을 설정하려면 **제어 흐름** 탭을 클릭하고 태스크, For 루프 컨테이너, Foreach 루프 컨테이너 또는 시퀀스 컨테이너를 마우스 오른쪽 단추로 클릭한 다음 **중단점 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e3442-109">To set breakpoints in a package control flow, click the **Control Flow** tab, right-click a task, a For Loop container, a Foreach Loop container, or a Sequence container, and then click **Edit Breakpoints**.</span></span>  
  
    -   <span data-ttu-id="e3442-110">이벤트 처리기에 중단점을 설정하려면 **이벤트 처리기** 탭을 클릭하고 태스크, For 루프 컨테이너, Foreach 루프 컨테이너 또는 시퀀스 컨테이너를 마우스 오른쪽 단추로 클릭한 다음 **중단점 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e3442-110">To set breakpoints in an event handler, click the **Event Handler** tab, right-click a task, a For Loop container, a Foreach Loop container, or a Sequence container, and then click **Edit Breakpoints**.</span></span>  
  
4.  <span data-ttu-id="e3442-111">**중단점 설정 \<container name>** 대화 상자에서 활성화할 중단점을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e3442-111">In the **Set Breakpoints \<container name>** dialog box, select the breakpoints to enable.</span></span>  
  
5.  <span data-ttu-id="e3442-112">필요에 따라 각 중단점의 적중 횟수 형식 및 적중 횟수를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="e3442-112">Optionally, modify the hit count type and the hit count number for each breakpoint.</span></span>  
  
6.  <span data-ttu-id="e3442-113">패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e3442-113">To save the package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3442-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e3442-114">See Also</span></span>  
 <span data-ttu-id="e3442-115">[패키지 배포 문제 해결 도구](troubleshooting/troubleshooting-tools-for-package-development.md) </span><span class="sxs-lookup"><span data-stu-id="e3442-115">[Troubleshooting Tools for Package Development](troubleshooting/troubleshooting-tools-for-package-development.md) </span></span>  
 <span data-ttu-id="e3442-116">[스크립트 태스크 및 스크립트 구성 요소에서 중단점을 설정 하 여 스크립트 디버깅](data-flow/transformations/script-component.md) </span><span class="sxs-lookup"><span data-stu-id="e3442-116">[Debug a Script by Setting Breakpoints in a Script Task and Script Component](data-flow/transformations/script-component.md) </span></span>  
 <span data-ttu-id="e3442-117">[스크립트 태스크 코딩 및 디버깅](control-flow/script-task.md) </span><span class="sxs-lookup"><span data-stu-id="e3442-117">[Coding and Debugging the Script Task](control-flow/script-task.md) </span></span>  
 [<span data-ttu-id="e3442-118">스크립트 구성 요소 코딩 및 디버깅</span><span class="sxs-lookup"><span data-stu-id="e3442-118">Coding and Debugging the Script Component</span></span>](extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
  
  
