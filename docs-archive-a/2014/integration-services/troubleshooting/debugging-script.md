---
title: 스크립트 디버깅 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Script task [Integration Services], debugging
- debugging [Integration Services], scripts
- scripts [Integration Services], debugging
ms.assetid: fddf57d8-8607-4f88-85a0-1b683087b491
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a7926f806f20f76c7aaac0c22b970addc5e93a78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736507"
---
# <a name="debugging-script"></a><span data-ttu-id="4da35-102">스크립트 디버깅</span><span class="sxs-lookup"><span data-stu-id="4da35-102">Debugging Script</span></span>
  <span data-ttu-id="4da35-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] VSTA([!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications)에서 스크립트 태스크 및 스크립트 구성 요소에 사용할 스크립트를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4da35-103">You write the scripts that the Script task and Script component use, in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).</span></span>  
  
 <span data-ttu-id="4da35-104">VSTA에서 중단점을 설정하고 스크립팅합니다.</span><span class="sxs-lookup"><span data-stu-id="4da35-104">You set and script breakpoints in VSTA.</span></span> <span data-ttu-id="4da35-105">VSTA에서 중단점을 관리할 수 있지만 **디자이너에서 제공하는** 중단점 설정 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 대화 상자를 사용하여 중단점을 관리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4da35-105">You can manage breakpoints in VSTA, but you can also manage the breakpoints using the **Set Breakpoints** dialog box that [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer provides.</span></span> <span data-ttu-id="4da35-106">자세한 내용은 [Debugging Control Flow](debugging-control-flow.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4da35-106">For more information, see [Debugging Control Flow](debugging-control-flow.md).</span></span>  
  
 <span data-ttu-id="4da35-107">**중단점 설정** 대화 상자에는 스크립트 중단점이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4da35-107">The **Set Breakpoints** dialog box includes the script breakpoints.</span></span> <span data-ttu-id="4da35-108">이러한 중단점은 중단점 목록의 아래에 표시되며, 중단점이 나타나는 함수의 이름과 줄 번호를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4da35-108">These breakpoints appear at the bottom of the breakpoint list, and display the line number and the name of the function in which the breakpoint appears.</span></span> <span data-ttu-id="4da35-109">**중단점 설정** 대화 상자에서 스크립트 중단점을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4da35-109">You can delete a script breakpoint from the **Set Breakpoints** dialog box.</span></span>  
  
 <span data-ttu-id="4da35-110">런타임 시 스크립트의 코드 줄에 설정된 중단점은 패키지 또는 패키지의 태스크 및 컨테이너에 설정된 중단점과 통합됩니다.</span><span class="sxs-lookup"><span data-stu-id="4da35-110">At run time, the breakpoints set on lines of code in script are integrated with the breakpoints set on the package or the tasks and containers in the package.</span></span> <span data-ttu-id="4da35-111">디버거는 스크립트의 특정 중단점에서부터 패키지, 태스크 및 컨테이너의 중단점까지 또는 그 반대로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4da35-111">The debugger can run from a breakpoint in the script to a breakpoint set on the package, task, or container, and vice versa.</span></span> <span data-ttu-id="4da35-112">예를 들어 패키지에서 **OnPreExecute** 및 **OnPostExecute** 이벤트를 받을 때 발생하는 중단 조건으로 설정된 중단점이 패키지에 포함되고, 스크립트의 줄에 중단점이 있는 스크립트 태스크가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4da35-112">For example, a package might have breakpoints set on the break conditions that occur when the package receives the **OnPreExecute** and **OnPostExecute** events, and also have a Script task that has breakpoints on lines of its script.</span></span> <span data-ttu-id="4da35-113">이 경우 패키지는 **OnPreExecute** 이벤트와 연결된 중단 조건에 따라 실행을 일시 중지하고, 스크립트의 중단점까지 실행한 다음 마지막으로, **OnPostExecute** 이벤트와 연결된 중단 조건까지 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4da35-113">In this scenario, the package can suspend execution on the break condition associated with the **OnPreExecute** event, run to the breakpoints in the script, and finally run to the break condition associated with the **OnPostExecute** event.</span></span>  
  
 <span data-ttu-id="4da35-114">스크립트 태스크 및 스크립트 구성 요소를 디버깅하는 방법은 [Coding and Debugging the Script Task](../extending-packages-scripting/task/coding-and-debugging-the-script-task.md) 및 [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4da35-114">For more information about debugging the Script task and Script component, see [Coding and Debugging the Script Task](../extending-packages-scripting/task/coding-and-debugging-the-script-task.md) and [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).</span></span>  
  
### <a name="to-set-a-breakpoint-in-visual-studio-for-applications"></a><span data-ttu-id="4da35-115">Visual Studio for Applications에서 중단점을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="4da35-115">To set a breakpoint in Visual Studio for Applications</span></span>  
  
-   [<span data-ttu-id="4da35-116">스크립트 태스크 및 스크립트 구성 요소에서 중단점을 설정하여 스크립트 디버깅</span><span class="sxs-lookup"><span data-stu-id="4da35-116">Debug a Script by Setting Breakpoints in a Script Task and Script Component</span></span>](../extending-packages-scripting/debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component.md)  
  
## <a name="see-also"></a><span data-ttu-id="4da35-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4da35-117">See Also</span></span>  
 [<span data-ttu-id="4da35-118">패키지 배포 문제 해결 도구</span><span class="sxs-lookup"><span data-stu-id="4da35-118">Troubleshooting Tools for Package Development</span></span>](troubleshooting-tools-for-package-development.md)  
  
  
