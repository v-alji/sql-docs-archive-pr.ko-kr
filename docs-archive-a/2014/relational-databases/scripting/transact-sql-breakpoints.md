---
title: Transact-SQL 중단점
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoints
ms.assetid: c234430f-bd94-4d0d-9e74-2bf11681fa50
author: rothja
ms.author: jroth
ms.openlocfilehash: c9595c9627ac3cc445b1193881c2d5b772e9b71d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653793"
---
# <a name="transact-sql-breakpoints"></a><span data-ttu-id="3c7f3-102">Transact-SQL 중단점</span><span class="sxs-lookup"><span data-stu-id="3c7f3-102">Transact-SQL Breakpoints</span></span>
  <span data-ttu-id="3c7f3-103">중단점은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거가 특정 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에서 실행을 일시 중지하도록 지정하여 사용자가 해당 지점에 있는 코드 요소의 상태를 확인할 수 있게 해 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3c7f3-103">Breakpoints specify that the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger pause execution on a specific [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, you can then view the state of the code elements at that point.</span></span>  
  
## <a name="breakpoints"></a><span data-ttu-id="3c7f3-104">중단점</span><span class="sxs-lookup"><span data-stu-id="3c7f3-104">Breakpoints</span></span>  
 <span data-ttu-id="3c7f3-105">[!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거를 실행하는 경우 특정 문에 대해 중단점을 설정/해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c7f3-105">When running the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger, you can toggle a breakpoint on specific statements.</span></span> <span data-ttu-id="3c7f3-106">실행 중에 중단점이 있는 문에 도달하면 디버거는 변수 및 매개 변수 값과 같은 디버깅 정보를 볼 수 있도록 실행을 일시 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7f3-106">When execution reaches a statement with a breakpoint, the debugger pauses execution so you can view debugging information, such as the values present in variables and parameters.</span></span>  
  
 <span data-ttu-id="3c7f3-107">중단점은 편집기 창에서 개별적으로 관리하거나 **중단점** 창을 사용하여 전체적으로 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c7f3-107">You can manage breakpoints individually in the editor window, or collectively by using the **Breakpoints** window.</span></span> <span data-ttu-id="3c7f3-108">실행을 일시 중지할 특정 조건, 중단점이 실행되는 경우에 수행할 동작 등과 같은 항목을 지정하여 중단점을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c7f3-108">You can edit breakpoints to specify items such as specific conditions under which execution should pause, or the actions to be taken if the breakpoint is executed.</span></span>  
  
## <a name="breakpoint-tasks"></a><span data-ttu-id="3c7f3-109">중단점 태스크</span><span class="sxs-lookup"><span data-stu-id="3c7f3-109">Breakpoint Tasks</span></span>  
  
|<span data-ttu-id="3c7f3-110">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="3c7f3-110">Task Description</span></span>|<span data-ttu-id="3c7f3-111">항목</span><span class="sxs-lookup"><span data-stu-id="3c7f3-111">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="3c7f3-112">디버거를 일시 중지할 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7f3-112">Describes how to specify the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement on which you want the debugger to pause.</span></span>|[<span data-ttu-id="3c7f3-113">중단점 설정/해제</span><span class="sxs-lookup"><span data-stu-id="3c7f3-113">Toggle a Breakpoint</span></span>](../spatial/point.md)|  
|<span data-ttu-id="3c7f3-114">중단점을 일시적으로 비활성화하고 나중에 다시 활성화하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7f3-114">Describes how to temporarily deactivate a breakpoint, and later reactivate it.</span></span> <span data-ttu-id="3c7f3-115">또한 중단점을 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7f3-115">Also describes how to delete a breakpoint.</span></span>|[<span data-ttu-id="3c7f3-116">중단점 설정, 해제 및 삭제</span><span class="sxs-lookup"><span data-stu-id="3c7f3-116">Enable, Disable, and Delete Breakpoints</span></span>](enable-disable-and-delete-breakpoints.md)|  
|<span data-ttu-id="3c7f3-117">지정한 Transact-SQL 식의 평가 결과에 따라 중단점을 적용할지 여부를 정의하는 조건을 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7f3-117">Describes how to specify a condition, which defines whether breakpoint breaks based on the evaluation of a specified Transact-SQL expression.</span></span>|[<span data-ttu-id="3c7f3-118">중단점 조건 지정</span><span class="sxs-lookup"><span data-stu-id="3c7f3-118">Specify a Breakpoint Condition</span></span>](specify-a-breakpoint-condition.md)|  
|<span data-ttu-id="3c7f3-119">중단점을 포함하는 문이 지정한 횟수만큼 실행된 경우에만 중단점을 적용하도록 적중 횟수를 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7f3-119">Describes how to specify a hit count, which causes a breakpoint to break only when the statement containing the breakpoint has been executed a specified number of times.</span></span>|[<span data-ttu-id="3c7f3-120">적중 횟수 지정</span><span class="sxs-lookup"><span data-stu-id="3c7f3-120">Specify a Hit Count</span></span>](specify-a-hit-count.md)|  
|<span data-ttu-id="3c7f3-121">중단점이 지정된 프로세스 또는 스레드에서만 작동하도록 필터를 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7f3-121">Describes how to specify a filter, which causes a breakpoint to break for only specified processes or threads.</span></span>|[<span data-ttu-id="3c7f3-122">중단점 필터 지정</span><span class="sxs-lookup"><span data-stu-id="3c7f3-122">Specify a Breakpoint Filter</span></span>](specify-a-breakpoint-filter.md)|  
|<span data-ttu-id="3c7f3-123">중단점 문이 실행될 때 수행되는 사용자 지정 작업인 **적중될 때** 동작을 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7f3-123">Describes how to specify a **When Hit** action, which is a custom operation that is performed when the breakpoint statement is executed.</span></span> <span data-ttu-id="3c7f3-124">예에서는 메시지를 인쇄합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7f3-124">An example would be to print a message.</span></span>|[<span data-ttu-id="3c7f3-125">중단점 동작 지정</span><span class="sxs-lookup"><span data-stu-id="3c7f3-125">Specify a Breakpoint Action</span></span>](specify-a-breakpoint-action.md)|  
|<span data-ttu-id="3c7f3-126">중단점의 위치를 편집하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7f3-126">Describes how to edit the location of a breakpoint.</span></span>|[<span data-ttu-id="3c7f3-127">중단점 위치 편집</span><span class="sxs-lookup"><span data-stu-id="3c7f3-127">Edit a Breakpoint Location</span></span>](edit-a-breakpoint-location.md)|  
  
## <a name="see-also"></a><span data-ttu-id="3c7f3-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3c7f3-128">See Also</span></span>  
 [<span data-ttu-id="3c7f3-129">Transact-SQL 디버거 정보</span><span class="sxs-lookup"><span data-stu-id="3c7f3-129">Transact-SQL Debugger Information</span></span>](transact-sql-debugger-information.md)  
  
  
