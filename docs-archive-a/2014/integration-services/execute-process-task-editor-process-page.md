---
title: 프로세스 실행 태스크 편집기 (프로세스 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executeprocesstask.process.f1
helpviewer_keywords:
- Execute Process Task Editor
ms.assetid: 0fc22406-e79b-47a4-a7e4-108d4ce6202f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ce8629be2c07ae4caac4586b266936a908e71499
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727303"
---
# <a name="execute-process-task-editor-process-page"></a><span data-ttu-id="8bb28-102">프로세스 실행 태스크 편집기(프로세스 페이지)</span><span class="sxs-lookup"><span data-stu-id="8bb28-102">Execute Process Task Editor (Process Page)</span></span>
  <span data-ttu-id="8bb28-103">**프로세스 실행 태스크 편집기** 대화 상자의 **프로세스** 페이지를 사용하여 프로세스 실행 옵션을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bb28-103">Use the **Process** page of the **Execute Process Task Editor** dialog box to configure the options that execute the process.</span></span> <span data-ttu-id="8bb28-104">이러한 옵션에는 실행할 실행 파일, 해당 위치, 명령 프롬프트 인수, 입력 제공 및 출력 캡처 변수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8bb28-104">These options include the executable to run, its location, command prompt arguments, and the variables that provide input and capture output.</span></span>  
  
 <span data-ttu-id="8bb28-105">이 태스크에 대한 자세한 내용은 [Execute Process Task](control-flow/execute-process-task.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8bb28-105">To learn about this task, see [Execute Process Task](control-flow/execute-process-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="8bb28-106">옵션</span><span class="sxs-lookup"><span data-stu-id="8bb28-106">Options</span></span>  
 <span data-ttu-id="8bb28-107">**RequireFullFileName**</span><span class="sxs-lookup"><span data-stu-id="8bb28-107">**RequireFullFileName**</span></span>  
 <span data-ttu-id="8bb28-108">지정한 위치에 실행 파일이 없는 경우 태스크 실패 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8bb28-108">Indicate whether the task should fail if the executable is not found at the specified location.</span></span>  
  
 <span data-ttu-id="8bb28-109">**실행 파일**</span><span class="sxs-lookup"><span data-stu-id="8bb28-109">**Executable**</span></span>  
 <span data-ttu-id="8bb28-110">실행할 실행 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb28-110">Type the name of the executable to run.</span></span>  
  
 <span data-ttu-id="8bb28-111">**인수**</span><span class="sxs-lookup"><span data-stu-id="8bb28-111">**Arguments**</span></span>  
 <span data-ttu-id="8bb28-112">명령 프롬프트 인수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb28-112">Provide command prompt arguments.</span></span>  
  
 <span data-ttu-id="8bb28-113">**WorkingDirectory**</span><span class="sxs-lookup"><span data-stu-id="8bb28-113">**WorkingDirectory**</span></span>  
 <span data-ttu-id="8bb28-114">실행 파일이 들어 있는 폴더의 경로를 입력하거나 찾아보기 단추 **(...)** 를 클릭하여 해당 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8bb28-114">Type the path of the folder that contains the executable, or click the browse button **(...)** and locate the folder.</span></span>  
  
 <span data-ttu-id="8bb28-115">**StandardInputVariable**</span><span class="sxs-lookup"><span data-stu-id="8bb28-115">**StandardInputVariable**</span></span>  
 <span data-ttu-id="8bb28-116">프로세스에 입력을 제공할 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8bb28-116">Select a variable to provide the input to the process, or click \<**New variable...**> to create a new variable:</span></span>  
  
 <span data-ttu-id="8bb28-117">**관련 항목:**  [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="8bb28-117">**Related Topics:**  [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
 <span data-ttu-id="8bb28-118">**StandardOutputVariable**</span><span class="sxs-lookup"><span data-stu-id="8bb28-118">**StandardOutputVariable**</span></span>  
 <span data-ttu-id="8bb28-119">프로세스 출력을 캡처할 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8bb28-119">Select a variable to capture the output of the process, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="8bb28-120">**StandardErrorVariable**</span><span class="sxs-lookup"><span data-stu-id="8bb28-120">**StandardErrorVariable**</span></span>  
 <span data-ttu-id="8bb28-121">프로세서의 오류 출력을 캡처할 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8bb28-121">Select a variable to capture the error output of the processor, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="8bb28-122">**FailTaskIfReturnCodeIsNotSuccessValue**</span><span class="sxs-lookup"><span data-stu-id="8bb28-122">**FailTaskIfReturnCodeIsNotSuccessValue**</span></span>  
 <span data-ttu-id="8bb28-123">프로세스 종료 코드가 **SuccessValue**에 지정한 값과 다른 경우 태스크 실패 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8bb28-123">Indicate whether the task fails if the process exit code is different from the value specified in **SuccessValue**.</span></span>  
  
 <span data-ttu-id="8bb28-124">**SuccessValue**</span><span class="sxs-lookup"><span data-stu-id="8bb28-124">**SuccessValue**</span></span>  
 <span data-ttu-id="8bb28-125">성공을 표시하기 위해 실행 파일에서 반환하는 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb28-125">Specify the value returned by the executable to indicate success.</span></span> <span data-ttu-id="8bb28-126">기본적으로 이 값은 **0**으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8bb28-126">By default this value is set to **0**.</span></span>  
  
 <span data-ttu-id="8bb28-127">**TimeOut**</span><span class="sxs-lookup"><span data-stu-id="8bb28-127">**TimeOut**</span></span>  
 <span data-ttu-id="8bb28-128">프로세스가 실행될 수 있는 시간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb28-128">Specify the number of seconds that the process can run.</span></span> <span data-ttu-id="8bb28-129">값 **0** 은 제한 시간 값이 사용되지 않으며 프로세스가 완료되거나 오류가 발생할 때까지 실행됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8bb28-129">A value of **0** indicates that no time-out value is used, and the process runs until it is completed or until an error occurs.</span></span>  
  
 <span data-ttu-id="8bb28-130">**TerminateProcessAfterTimeOut**</span><span class="sxs-lookup"><span data-stu-id="8bb28-130">**TerminateProcessAfterTimeOut**</span></span>  
 <span data-ttu-id="8bb28-131">**TimeOut** 옵션에 지정한 제한 시간 후의 프로세스 강제 종료 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8bb28-131">Indicate whether the process is forced to end after the time-out period specified by the **TimeOut** option.</span></span> <span data-ttu-id="8bb28-132">이 옵션은 **TimeOut** 이 **0**이 아닌 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bb28-132">This option is available only if **TimeOut** is not **0**.</span></span>  
  
 <span data-ttu-id="8bb28-133">**WindowStyle**</span><span class="sxs-lookup"><span data-stu-id="8bb28-133">**WindowStyle**</span></span>  
 <span data-ttu-id="8bb28-134">프로세스를 실행할 창 스타일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb28-134">Specify the window style in which to run the process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bb28-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8bb28-135">See Also</span></span>  
 <span data-ttu-id="8bb28-136">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="8bb28-136">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="8bb28-137">식 페이지</span><span class="sxs-lookup"><span data-stu-id="8bb28-137">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
