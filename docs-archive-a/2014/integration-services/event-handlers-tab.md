---
title: 이벤트 처리기 탭 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.eventhandlerwindow.f1
ms.assetid: 94fc8916-8032-490c-b9d5-ded8b6217e49
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a5f25a9b0d602a3189feab797b7ef9c333decabb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651806"
---
# <a name="event-handlers-tab"></a><span data-ttu-id="3c7a9-102">이벤트 처리기 탭</span><span class="sxs-lookup"><span data-stu-id="3c7a9-102">Event Handlers Tab</span></span>
  <span data-ttu-id="3c7a9-103">**디자이너의** 이벤트 처리기 [!INCLUDE[ssIS](../includes/ssis-md.md)] 탭을 사용하여 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지에 제어 흐름을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c7a9-103">Use the **Event Handlers** tab of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to build a control flow in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package.</span></span> <span data-ttu-id="3c7a9-104">이벤트 처리기는 패키지 또는 패키지의 태스크나 컨테이너에 의해 발생한 이벤트에 대한 응답으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c7a9-104">An event handler runs in response to an event raised by the package or by a task or container in the package.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3c7a9-105">옵션</span><span class="sxs-lookup"><span data-stu-id="3c7a9-105">Options</span></span>  
 <span data-ttu-id="3c7a9-106">**실행 파일**</span><span class="sxs-lookup"><span data-stu-id="3c7a9-106">**Executable**</span></span>  
 <span data-ttu-id="3c7a9-107">이벤트 처리기를 작성할 실행 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7a9-107">Select the executable for which you want to build an event handler.</span></span> <span data-ttu-id="3c7a9-108">실행 파일은 패키지 또는 패키지의 태스크나 컨테이너가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c7a9-108">The executable can be the package, or a task or containers in the package.</span></span>  
  
 <span data-ttu-id="3c7a9-109">**이벤트 처리기**</span><span class="sxs-lookup"><span data-stu-id="3c7a9-109">**Event handler**</span></span>  
 <span data-ttu-id="3c7a9-110">이벤트 처리기의 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7a9-110">Select a type of event handler.</span></span> <span data-ttu-id="3c7a9-111">**도구 상자**에서 항목을 끌어 이벤트 처리기를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3c7a9-111">Create the event handler by dragging items from the **Toolbox**.</span></span>  
  
 <span data-ttu-id="3c7a9-112">**Delete**</span><span class="sxs-lookup"><span data-stu-id="3c7a9-112">**Delete**</span></span>  
 <span data-ttu-id="3c7a9-113">이벤트 처리기를 선택하고 **삭제**를 클릭하여 해당 처리기를 패키지에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7a9-113">Select an event handler, and remove it from the package by clicking **Delete**.</span></span>  
  
 <span data-ttu-id="3c7a9-114">**실행 파일 \<executable name>에 대한 \<event handler name>를 만들려면 여기를 클릭하세요.**</span><span class="sxs-lookup"><span data-stu-id="3c7a9-114">**Click here to create an \<event handler name> for the executable \<executable name>**</span></span>  
 <span data-ttu-id="3c7a9-115">이벤트 처리기를 만들려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7a9-115">Click to create the event handler.</span></span>  
  
 <span data-ttu-id="3c7a9-116">[!INCLUDE[ssIS](../includes/ssis-md.md)] 태스크 및 컨테이너를 나타내는 그래픽 개체를 **도구 상자** 에서 **이벤트 처리기** 탭의 디자인 화면으로 끌어 온 다음 이러한 태스크 및 컨테이너가 실행되는 순서를 정의하는 선행 제약 조건으로 이러한 개체를 연결하여 제어 흐름을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3c7a9-116">Create the control flow by dragging graphical objects that represent [!INCLUDE[ssIS](../includes/ssis-md.md)] tasks and containers from the **Toolbox** to the design surface of the **Event Handlers** tab, and then connecting the objects by using precedence constraints to define the sequence in which they run.</span></span>  
  
 <span data-ttu-id="3c7a9-117">또한 주석을 추가하려면 디자인 화면을 마우스 오른쪽 단추로 클릭한 다음 메뉴에서 **주석 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7a9-117">Additionally, to add annotations, right-click the design surface, and then on the menu, click **Add Annotation**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c7a9-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3c7a9-118">See Also</span></span>  
 <span data-ttu-id="3c7a9-119">[Integration Services&#40;SSIS&#41; 이벤트 처리기](integration-services-ssis-event-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="3c7a9-119">[Integration Services &#40;SSIS&#41; Event Handlers](integration-services-ssis-event-handlers.md) </span></span>  
 <span data-ttu-id="3c7a9-120">[제어 흐름](control-flow/control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="3c7a9-120">[Control Flow](control-flow/control-flow.md) </span></span>  
 <span data-ttu-id="3c7a9-121">[SSIS 디자이너](ssis-designer.md) </span><span class="sxs-lookup"><span data-stu-id="3c7a9-121">[SSIS Designer](ssis-designer.md) </span></span>  
 [<span data-ttu-id="3c7a9-122">Integration Services&#40;SSIS&#41; 이벤트 처리기</span><span class="sxs-lookup"><span data-stu-id="3c7a9-122">Integration Services &#40;SSIS&#41; Event Handlers</span></span>](integration-services-ssis-event-handlers.md)  
  
  
