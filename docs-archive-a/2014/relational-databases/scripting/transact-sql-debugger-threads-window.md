---
title: 스레드 창
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Threads Window [Transact-SQL]
ms.assetid: e153f619-0049-4162-9076-c24a454f3278
author: rothja
ms.author: jroth
ms.openlocfilehash: 6f3460c892c182996a753c2a16076418a6b2008f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730456"
---
# <a name="threads-window"></a><span data-ttu-id="09330-102">스레드 창</span><span class="sxs-lookup"><span data-stu-id="09330-102">Threads Window</span></span>
  <span data-ttu-id="09330-103">**스레드** 창에서는 디버깅 중인 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기 세션에서 사용하는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 스레드에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09330-103">The **Threads** window displays information about the [!INCLUDE[ssDE](../../includes/ssde-md.md)] thread that is used by the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor session that is being debugged.</span></span> <span data-ttu-id="09330-104">스레드 정보를 표시하려면 디버그 모드여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="09330-104">You must be in debug mode to display the thread information.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="09330-105">작업 목록</span><span class="sxs-lookup"><span data-stu-id="09330-105">Task List</span></span>  
 <span data-ttu-id="09330-106">**스레드 창에 액세스하려면**</span><span class="sxs-lookup"><span data-stu-id="09330-106">**To access the Threads window**</span></span>  
  
-   <span data-ttu-id="09330-107">**디버그** 메뉴에서 **창**을 선택한 다음 **스레드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="09330-107">On the **Debug** menu, click **Windows**, and then click **Threads**.</span></span>  
  
## <a name="columns"></a><span data-ttu-id="09330-108">열</span><span class="sxs-lookup"><span data-stu-id="09330-108">Columns</span></span>  
 <span data-ttu-id="09330-109">**ID**</span><span class="sxs-lookup"><span data-stu-id="09330-109">**ID**</span></span>  
 <span data-ttu-id="09330-110">[!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거가 스레드에 할당하는 고유한 식별 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="09330-110">Is a unique identifying number that the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger assigns to the thread.</span></span> <span data-ttu-id="09330-111">sys.dm_os_threads 동적 관리 뷰에서 행을 선택하면 스레드에 대한 자세한 내용을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09330-111">You can find more information about the thread by selecting a row from the sys.dm_os_threads dynamic management view.</span></span>  
  
 <span data-ttu-id="09330-112">경량 풀링 모드로 실행 중이 아닌 경우 os_thread_id의 값이 **ID** 열 값과 일치하는 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="09330-112">If you are not running in lightweight pooling mode, select the row in which the value in os_thread_id matches the value in the **ID** column.</span></span> <span data-ttu-id="09330-113">경량 풀링 모드로 실행 중인 경우 fiber_context_address의 값이 **ID** 열 값과 일치하는 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="09330-113">If you are running in lightweight pooling mode, select the row in which the value in fiber_context_address matches the value in the **ID** column.</span></span>  
  
 <span data-ttu-id="09330-114">**이름**</span><span class="sxs-lookup"><span data-stu-id="09330-114">**Name**</span></span>  
 <span data-ttu-id="09330-115">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 세션에 대한 정보를 **컴퓨터 이름/인스턴스 이름 [SPID]** 형식으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09330-115">Displays information about the [!INCLUDE[ssDE](../../includes/ssde-md.md)] session in the format **ComputerName/InstanceName [SPID]**.</span></span>  
  
 <span data-ttu-id="09330-116">**컴퓨터 이름**</span><span class="sxs-lookup"><span data-stu-id="09330-116">**ComputerName**</span></span>  
 <span data-ttu-id="09330-117">쿼리 편집기 세션이 연결된 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스를 실행하는 컴퓨터의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="09330-117">The name of the computer that is running the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that the Query Editor session is connected to.</span></span>  
  
 <span data-ttu-id="09330-118">**InstanceName**</span><span class="sxs-lookup"><span data-stu-id="09330-118">**InstanceName**</span></span>  
 <span data-ttu-id="09330-119">쿼리 편집기 세션이 연결된 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="09330-119">The name of the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that the Query Editor session is connected to.</span></span>  
  
 <span data-ttu-id="09330-120">**[SPID]**</span><span class="sxs-lookup"><span data-stu-id="09330-120">**[SPID]**</span></span>  
 <span data-ttu-id="09330-121">이 세션을 고유하게 식별하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 세션 프로세스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="09330-121">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] session process ID that uniquely identifies this session.</span></span> <span data-ttu-id="09330-122">spid 열과 값이 값은 sys.sysprocesses 뷰의 행을 선택하면 세션에 대한 자세한 내용을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09330-122">You can obtain more information about the session by selecting the row in the sys.sysprocesses view that has the same value in the spid column.</span></span>  
  
 <span data-ttu-id="09330-123">**위치**</span><span class="sxs-lookup"><span data-stu-id="09330-123">**Location**</span></span>  
 <span data-ttu-id="09330-124">디버깅 중인 쿼리 편집기 세션에서 사용하는 스크립트 파일의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09330-124">Displays the name of the script file that is used in the Query Editor session that is being debugged.</span></span>  
  
 <span data-ttu-id="09330-125">**우선 순위**</span><span class="sxs-lookup"><span data-stu-id="09330-125">**Priority**</span></span>  
 <span data-ttu-id="09330-126">[!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거는 이 기능을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="09330-126">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger does not support this feature.</span></span>  
  
 <span data-ttu-id="09330-127">**일시 중지됨**</span><span class="sxs-lookup"><span data-stu-id="09330-127">**Suspend**</span></span>  
 <span data-ttu-id="09330-128">[!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거는 이 기능을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="09330-128">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger does not support this feature.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09330-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="09330-129">See Also</span></span>  
 <span data-ttu-id="09330-130">[Transact-SQL 디버거](transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="09330-130">[Transact-SQL Debugger](transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="09330-131">[Transact-SQL 디버거 정보](transact-sql-debugger-information.md) </span><span class="sxs-lookup"><span data-stu-id="09330-131">[Transact-SQL Debugger Information](transact-sql-debugger-information.md) </span></span>  
 <span data-ttu-id="09330-132">[sys.dm_os_threads&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="09330-132">[sys.dm_os_threads &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql) </span></span>  
 [<span data-ttu-id="09330-133">sys.sysprocesses&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="09330-133">sys.sysprocesses &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql)  
