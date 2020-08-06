---
title: 중단점 필터 지정
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint filter
ms.assetid: 7bf1dddd-7b0b-4c47-8a7b-28a5569b4fa5
author: rothja
ms.author: jroth
ms.openlocfilehash: 9fc320397da1bddc0d28191c359c4d311b23e044
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651617"
---
# <a name="specify-a-breakpoint-filter"></a><span data-ttu-id="71775-102">중단점 필터 지정</span><span class="sxs-lookup"><span data-stu-id="71775-102">Specify a Breakpoint Filter</span></span>
  <span data-ttu-id="71775-103">중단점 필터는 중단점이 지정된 컴퓨터, 운영 체제 프로세스 및 스레드에서만 작동하도록 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="71775-103">A breakpoint filter limits the breakpoint to acting only on specified computers, operating system processes, and threads.</span></span> <span data-ttu-id="71775-104">중단점 필터는 일반적으로 병렬 애플리케이션을 디버깅할 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="71775-104">Breakpoint filters are typically used when debugging parallel applications.</span></span>  
  
##  <a name="filter-considerations"></a><a name="BKMK_ActionConsiderations"></a> <span data-ttu-id="71775-105">필터 고려 사항</span><span class="sxs-lookup"><span data-stu-id="71775-105">Filter Considerations</span></span>  
 <span data-ttu-id="71775-106">중단점 필터는 일반적으로 [!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거에서는 사용되지 않는데 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트 및 저장 프로시저는 병렬 애플리케이션이 아니기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="71775-106">Breakpoint filters are not typically used with the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger because [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts and stored procedures are not parallel applications.</span></span>  
  
#### <a name="to-specify-a-breakpoint-filter"></a><span data-ttu-id="71775-107">중단점 필터를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="71775-107">To Specify a Breakpoint Filter</span></span>  
  
1.  <span data-ttu-id="71775-108">편집기 창에서 중단점 문자 모양을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **필터** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="71775-108">In the editor window, right-click the breakpoint glyph, and then click **Filter** on the shortcut menu.</span></span>  
  
     <span data-ttu-id="71775-109">또는</span><span class="sxs-lookup"><span data-stu-id="71775-109">-or-</span></span>  
  
     <span data-ttu-id="71775-110">**중단점** 창에서 중단점 문자 모양을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **필터** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="71775-110">In the **Breakpoints** window, right-click the breakpoint glyph, and then click **Filter** on the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="71775-111">**중단점 필터** 대화 상자의 **필터** 상자에 컴퓨터 이름을 지정하거나 운영 체제 프로세스 및 스레드를 이름이나 ID 번호로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="71775-111">In the **Breakpoint Filters** dialog box, use the **Filter** box to specify computers by name, or operating system processes and threads by either name or ID number:</span></span>  
  
    -   <span data-ttu-id="71775-112">`MachineName`은 데이터베이스 엔진 인스턴스를 실행 중인 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="71775-112">`MachineName` is the computer running the instance of the Database Engine.</span></span>  
  
    -   <span data-ttu-id="71775-113">`ProcessID` 및 `ProcessName`은 데이터베이스 엔진 인스턴스를 실행 중인 운영 체제 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="71775-113">`ProcessID`, and `ProcessName` are the operating system process running the instance of the Database Engine.</span></span>  
  
    -   <span data-ttu-id="71775-114">`ThreadID` 및 `ThreadName`은 데이터베이스 엔진 인스턴스에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 일괄 처리, 프로시저 또는 함수를 실행 중인 운영 체제 스레드입니다.</span><span class="sxs-lookup"><span data-stu-id="71775-114">`ThreadID` and `ThreadName` are the operating system thread running the [!INCLUDE[tsql](../../includes/tsql-md.md)] batch, procedure, or function in the instance of the Database Engine.</span></span>  
  
3.  <span data-ttu-id="71775-115">**확인** 을 클릭하여 변경 내용을 구현하거나 **취소** 를 클릭하여 변경 내용을 적용하지 않고 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="71775-115">Click **OK** to implement the changes, or **Cancel** to exit without applying the changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71775-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="71775-116">See Also</span></span>  
 <span data-ttu-id="71775-117">[중단점 조건 지정](specify-a-breakpoint-condition.md) </span><span class="sxs-lookup"><span data-stu-id="71775-117">[Specify a Breakpoint Condition](specify-a-breakpoint-condition.md) </span></span>  
 <span data-ttu-id="71775-118">[적중 횟수 지정](specify-a-hit-count.md) </span><span class="sxs-lookup"><span data-stu-id="71775-118">[Specify a Hit Count](specify-a-hit-count.md) </span></span>  
 [<span data-ttu-id="71775-119">중단점 동작 지정</span><span class="sxs-lookup"><span data-stu-id="71775-119">Specify a Breakpoint Action</span></span>](specify-a-breakpoint-action.md)  
