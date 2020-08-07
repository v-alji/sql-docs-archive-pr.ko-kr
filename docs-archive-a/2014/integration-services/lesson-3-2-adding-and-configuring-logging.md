---
title: '2단계: 로깅 추가 및 구성 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 56105f3f-e500-4669-8c8e-acf434527727
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0f2cdce6f34a19e22830d357d20f5d99cff8c14f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731883"
---
# <a name="step-2-adding-and-configuring-logging"></a><span data-ttu-id="a5f83-102">2단계: 로깅 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="a5f83-102">Step 2: Adding and Configuring Logging</span></span>
  <span data-ttu-id="a5f83-103">이 태스크에서는 Lesson 3.dtsx 패키지의 데이터 흐름에 로깅을 설정한 다음</span><span class="sxs-lookup"><span data-stu-id="a5f83-103">In this task, you will enable logging for the data flow in the Lesson 3.dtsx package.</span></span> <span data-ttu-id="a5f83-104">PipelineExecutionPlan 및 PipelineExecuteTrees 이벤트를 로그하도록 텍스트 파일 로그 공급자를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-104">Then, you will configure a Text File log provider to log the PipelineExecutionPlan and PipelineExecuteTrees events.</span></span> <span data-ttu-id="a5f83-105">텍스트 파일 로그 공급자는 쉽게 보고 변환할 수 있는 로그를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-105">The Text Files log provider creates logs that are easy to view and easily transportable.</span></span> <span data-ttu-id="a5f83-106">이러한 로그 파일은 단순하기 때문에 특히 패키지의 기본 테스트 단계에서 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-106">The simplicity of these log files makes these files especially useful during the basic testing phase of a package.</span></span> <span data-ttu-id="a5f83-107">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너의 로그 이벤트 창에서도 로그 항목을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-107">You can also view the log entries in the Log Events window of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
### <a name="to-add-logging-to-the-package"></a><span data-ttu-id="a5f83-108">패키지에 로깅을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="a5f83-108">To add logging to the package</span></span>  
  
1.  <span data-ttu-id="a5f83-109">**SSIS** 메뉴에서 **로깅**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-109">On the **SSIS** menu, click **Logging**.</span></span>  
  
2.  <span data-ttu-id="a5f83-110">**SSIS 로그 구성** 대화 상자의 **컨테이너** 창에서 3단원 패키지를 나타내는 최상위 개체가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-110">In the **Configure SSIS Logs** dialog box, in the **Containers** pane, make sure that the topmost object, which represents the Lesson 3 package, is selected.</span></span>  
  
3.  <span data-ttu-id="a5f83-111">**공급자 및 로그** 탭의 **공급자 유형** 상자에서 **텍스트 파일용 SSIS 로그 공급자**를 선택한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-111">On the **Providers and Logs** tab, in the **Provider type** box, select **SSIS log provider for Text files**, and then click **Add**.</span></span>  
  
     <span data-ttu-id="a5f83-112">Integration Services 새 텍스트 파일 로그 공급자를 패키지에 추가 하 고 기본 이름 **SSIS 로그 공급자를 텍스트 파일로**추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-112">Integration Services adds a new Text File log provider to the package with the default name **SSIS log provider for text files**.</span></span> <span data-ttu-id="a5f83-113">이제 새 로그 공급자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-113">You can now configure the new log provider.</span></span>  
  
4.  <span data-ttu-id="a5f83-114">**이름** 열에을 입력 `Lesson 3 Log File` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-114">In the **Name** column, type `Lesson 3 Log File`.</span></span>  
  
5.  <span data-ttu-id="a5f83-115">**설명**을 수정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-115">Optionally, modify the **Description**.</span></span>  
  
6.  <span data-ttu-id="a5f83-116">**구성** 열에서 **\<New Connection>** 을 클릭하여 로그 정보가 쓰여질 대상을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-116">In the **Configuration** column, click **\<New Connection>** to specify the destination to which the log information is written.</span></span>  
  
     <span data-ttu-id="a5f83-117">**파일 연결 관리자 편집기** 대화 상자의 **사용 유형**에서 **파일 만들기**를 선택한 다음 **찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-117">In the **File Connection Manager Editor** dialog box, for **Usage type**, select **Create file**, and then click **Browse**.</span></span> <span data-ttu-id="a5f83-118">기본적으로 **파일 선택** 대화 상자에 프로젝트 폴더가 열리지만 임의의 위치에 로그 정보를 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-118">By default, the **Select File** dialog box opens the project folder, but you can save log information to any location.</span></span>  
  
7.  <span data-ttu-id="a5f83-119">**파일 선택** 대화 상자의 **파일 이름** 상자에 `TutorialLog.log` 를 입력 하 고 **열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-119">In the **Select File** dialog box, in the **File name** box type `TutorialLog.log`, and click **Open**.</span></span>  
  
8.  <span data-ttu-id="a5f83-120">**확인** 을 클릭하여 **파일 연결 관리자 편집기** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-120">Click **OK** to close the **File Connection Manager Editor** dialog box.</span></span>  
  
9. <span data-ttu-id="a5f83-121">**컨테이너** 창에서 패키지 컨테이너 계층의 모든 노드를 확장한 다음 **Extract Sample Currency Data** 확인란을 포함한 모든 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-121">In the **Containers** pane, expand all nodes of the package container hierarchy, and then clear all check boxes, including the **Extract Sample Currency Data** check box.</span></span> <span data-ttu-id="a5f83-122">이제 **Extract Sample Currency Data** 의 확인란을 선택하여 이 노드에 대한 이벤트만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-122">Now select the check box for **Extract Sample Currency Data** to get only the events for this node.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a5f83-123">**Extract Sample Currency Data** 확인란이 선택되지 않고 흐리게 표시되어 있는 경우에는 태스크에서 부모 컨테이너의 로그 설정을 사용하여 해당 작업과 관련된 로그 이벤트를 설정할 수 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-123">If the state of the **Extract Sample Currency Data** check box is dimmed instead of selected, the task uses the log settings of the parent container and you cannot enable the log events that are specific to the task.</span></span>  
  
10. <span data-ttu-id="a5f83-124">**자세히** 탭의 **이벤트** 열에서 **PipelineExecutionPlan** 및 **PipelineExecutionTrees** 이벤트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-124">On the **Details** tab, in the **Events** column, select the **PipelineExecutionPlan** and **PipelineExecutionTrees** events.</span></span>  
  
11. <span data-ttu-id="a5f83-125">**고급** 을 클릭하여 로그 공급자가 각 이벤트의 로그에 쓸 세부 사항을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-125">Click **Advanced** to review the details that the log provider will write to the log for each event.</span></span> <span data-ttu-id="a5f83-126">기본적으로 지정된 이벤트에 대해 모든 정보 범주가 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-126">By default, all information categories are automatically selected for the events you specify.</span></span>  
  
12. <span data-ttu-id="a5f83-127">**기본** 을 클릭하여 정보 범주를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-127">Click **Basic** to hide the information categories.</span></span>  
  
13. <span data-ttu-id="a5f83-128">**공급자 및 로그** 탭의 **이름** 열에서을 선택 `Lesson 3 Log File` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-128">On the **Provider and Logs** tab, in the **Name** column, select `Lesson 3 Log File`.</span></span> <span data-ttu-id="a5f83-129">패키지의 로그 공급자를 만든 후에는 로그 공급자를 삭제한 후 다시 만들지 않아도 이 로그 공급자를 선택 취소하여 잠시 로깅을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-129">Once you have created a log provider for your package, you can optionally deselect it to temporarily turn off logging, without having to delete and re-create a log provider.</span></span>  
  
14. <span data-ttu-id="a5f83-130">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f83-130">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a5f83-131">다음 단계</span><span class="sxs-lookup"><span data-stu-id="a5f83-131">Next Steps</span></span>  
 [<span data-ttu-id="a5f83-132">3단계: 3단원 자습서 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="a5f83-132">Step 3: Testing the Lesson 3 Tutorial Package</span></span>](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
  
