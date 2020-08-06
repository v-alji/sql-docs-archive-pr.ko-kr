---
title: 스크립트 태스크 및 스크립트 구성 요소에서 중단점을 설정하여 스크립트 디버깅 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- breakpoints [Integration Services]
- scripts [Integration Services], breakpoints
ms.assetid: 6c03464f-3f7d-4882-b7f8-8e396f8e2944
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 45e7ffc6680c33e3b17b9b39fba0aabd8fa4028c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648446"
---
# <a name="debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component"></a><span data-ttu-id="b7685-102">스크립트 태스크 및 스크립트 구성 요소에서 중단점을 설정하여 스크립트 디버깅</span><span class="sxs-lookup"><span data-stu-id="b7685-102">Debug a Script by Setting Breakpoints in a Script Task and Script Component</span></span>
  <span data-ttu-id="b7685-103">이 절차에서는 스크립트 태스크 및 스크립트 구성 요소에 사용되는 스크립트에서 중단점을 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b7685-103">This procedure describes how to set breakpoints in the scripts that are used in the Script task and Script component.</span></span>  
  
 <span data-ttu-id="b7685-104">스크립트에 중단점을 설정하면 중단점이 기본 제공 중단점과 **함께 중단점 설정 - \<object name>** 대화 상자에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7685-104">After you set breakpoints in the script, the **Set Breakpoints - \<object name>** dialog box lists the breakpoints, along with the built-in breakpoints.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b7685-105">스크립트 태스크 및 스크립트 구성 요소의 중단점이 무시되는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7685-105">Under certain circumstances, breakpoints in the Script task and Script component are ignored.</span></span> <span data-ttu-id="b7685-106">자세한 내용은 스크립트 [태스크 코딩 및 디버깅](../control-flow/script-task.md) 의 스크립트 **태스크 디버깅** 섹션 및 [스크립트 구성 요소 코딩 및 디버깅]의 스크립트 **구성 요소 디버깅** 섹션을 참조 하십시오. /extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md.</span><span class="sxs-lookup"><span data-stu-id="b7685-106">For more information, see the **Debugging the Script Task** section in [Coding and Debugging the Script Task](../control-flow/script-task.md) and the **Debugging the Script Component** section in [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md.</span></span>  
  
### <a name="to-set-a-breakpoint-in-script"></a><span data-ttu-id="b7685-107">스크립트에 중단점을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="b7685-107">To set a breakpoint in script</span></span>  
  
1.  <span data-ttu-id="b7685-108">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b7685-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="b7685-109">중단점을 설정하려는 스크립트를 포함하는 패키지를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b7685-109">Double-click the package that contains the script in which you want to set breakpoints.</span></span>  
  
3.  <span data-ttu-id="b7685-110">**제어 흐름** 탭을 클릭하고 스크립트 태스크를 두 번 클릭하여 스크립트 태스크를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b7685-110">To open the Script task, click the **Control Flow** tab, and then double-click the Script task.</span></span>  
  
4.  <span data-ttu-id="b7685-111">**데이터 흐름** 탭을 클릭하고 스크립트 구성 요소를 두 번 클릭하여 스크립트 구성 요소를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b7685-111">To open the Script component, click the **Data Flow** tab, and then double-click the Script component.</span></span>  
  
5.  <span data-ttu-id="b7685-112">**스크립트**를 클릭한 다음 **스크립트 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b7685-112">Click **Script** and then click **Edit Script**.</span></span>  
  
6.  <span data-ttu-id="b7685-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)] VSTA([!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications)에서 중단점을 설정할 스크립트 줄을 찾아 마우스 오른쪽 단추로 클릭하고 **중단점**을 가리킨 다음 **중단점 삽입**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b7685-113">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA), locate the line of script on which you want to set a breakpoint, right-click that line, point to **Breakpoint**, and then click **Insert Breakpoint**.</span></span>  
  
     <span data-ttu-id="b7685-114">코드 줄에 중단점 아이콘이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b7685-114">The breakpoint icon appears on the line of code.</span></span>  
  
7.  <span data-ttu-id="b7685-115">**파일** 메뉴에서 **끝내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b7685-115">On the **File** menu, click **Exit**.</span></span>  
  
8.  <span data-ttu-id="b7685-116">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b7685-116">Click **OK**.</span></span>  
  
9. <span data-ttu-id="b7685-117">패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b7685-117">To save the package, click **Save Selected Items** on the **File** menu.</span></span>  
  
  
