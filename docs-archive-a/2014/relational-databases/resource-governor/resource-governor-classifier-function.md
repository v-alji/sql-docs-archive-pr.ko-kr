---
title: 리소스 관리자 분류자 함수 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, classifier function
- user-defined functions [SQL Server], classifier function
- classifier function [SQL Server]
- classifier function [SQL Server], overview
ms.assetid: 64c25012-7068-476f-afa2-0b4f3adde9a4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 69b6fd10ac0adc6f76925e0d41f110b917111466
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731467"
---
# <a name="resource-governor-classifier-function"></a><span data-ttu-id="ff5a2-102">Resource Governor Classifier Function</span><span class="sxs-lookup"><span data-stu-id="ff5a2-102">Resource Governor Classifier Function</span></span>
  <span data-ttu-id="ff5a2-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 리소스 관리자 분류 프로세스는 세션 특징에 기초하여 들어오는 세션을 작업 그룹에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource governor classification process assigns incoming sessions to a workload group based on the characteristics of the session.</span></span> <span data-ttu-id="ff5a2-104">분류자 함수라고 하는 사용자 정의 함수를 작성하여 원하는 분류 논리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-104">You can tailor the classification logic by writing a user-defined function, called a classifier function.</span></span>  
  
## <a name="classification"></a><span data-ttu-id="ff5a2-105">분류</span><span class="sxs-lookup"><span data-stu-id="ff5a2-105">Classification</span></span>  
 <span data-ttu-id="ff5a2-106">리소스 관리자는 들어오는 세션의 분류를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-106">Resource Governor supports the classification of incoming sessions.</span></span> <span data-ttu-id="ff5a2-107">분류는 함수에 포함된 사용자 작성 조건 집합을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-107">Classification is based on a set of user-written criteria contained in a function.</span></span> <span data-ttu-id="ff5a2-108">함수 논리의 결과는 리소스 관리자가 세션을 기존 작업 그룹으로 분류할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-108">The results of the function logic enable Resource Governor to classify sessions into existing workload groups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ff5a2-109">내부 작업 그룹은 내부 전용 요청으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-109">The internal workload group is populated with requests that are for internal use only.</span></span> <span data-ttu-id="ff5a2-110">이러한 요청을 라우팅하는 데 사용되는 조건은 변경할 수 없으며, 요청을 내부 작업 그룹으로 분류할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-110">You cannot change the criteria used for routing these requests and you cannot classify requests into the internal workload group.</span></span>  
  
 <span data-ttu-id="ff5a2-111">들어오는 세션을 작업 그룹에 할당하는 데 사용되는 논리가 포함된 스칼라 함수를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-111">You can write a scalar function that contains the logic that is used to assign incoming sessions to a workload group.</span></span> <span data-ttu-id="ff5a2-112">이 함수를 사용하려면 우선 다음 동작을 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-112">Before you can use this function, you must complete the following actions:</span></span>  
  
-   <span data-ttu-id="ff5a2-113">ALTER RESOURCE GOVERNOR 문을 사용하여 함수를 만들고 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-113">Create and register the function using the ALTER RESOURCE GOVERNOR statement.</span></span> <span data-ttu-id="ff5a2-114">자세한 내용은 [ALTER RESOURCE GOVERNOR&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-114">For more information, see [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql).</span></span>  
  
-   <span data-ttu-id="ff5a2-115">ALTER RESOURCE GOVERNOR 문을 RECONFIGURE 매개 변수와 함께 사용하여 리소스 관리자 구성을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-115">Update the Resource Governor configuration using the ALTER RESOURCE GOVERNOR statement with the RECONFIGURE parameter.</span></span>  
  
 <span data-ttu-id="ff5a2-116">함수를 만들고 구성 변경 내용을 적용하면 리소스 관리자 분류자는 함수에서 반환한 작업 그룹 이름을 사용하여 적절한 작업 그룹으로 새 요청을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-116">After you create the function and apply the configuration changes, the Resource Governor classifier will use the workload group name returned by the function to send a new request to the appropriate workload group.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ff5a2-117">지정된 로그인 제한 시간 내에 분류 함수가 완료되지 않으면 클라이언트 세션이 시간 초과될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-117">The client session may time out if the classification function does not complete within the specified time-out for the login.</span></span> <span data-ttu-id="ff5a2-118">로그인 시간 제한은 클라이언트 속성이기 때문에 서버에서는 시간 제한을 인식하지 못합니다. 장기 실행 분류자 함수는 서버를 오랫동안 연결되지 않은 상태로 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-118">Login time-out is a client property and as such, the server is unaware of a time-out. A long-running classifier function can leave the server with orphaned connections for long periods.</span></span> <span data-ttu-id="ff5a2-119">따라서 연결 시간 제한 전에 실행을 종료하는 분류자 함수를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-119">It is important that you create classifier functions that finish executing before a connection time-out.</span></span>  
  
 <span data-ttu-id="ff5a2-120">사용자 정의 함수에는 다음과 같은 특징과 동작이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-120">The user-defined function has the following characteristics and behaviors:</span></span>  
  
-   <span data-ttu-id="ff5a2-121">사용자 정의 함수는 모든 새 세션에 대해 평가됩니다. 연결 풀링이 사용되는 경우에도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-121">The user-defined function is evaluated for every new session, even when connection pooling is enabled.</span></span>  
  
-   <span data-ttu-id="ff5a2-122">사용자 정의 함수는 세션에 작업 그룹 컨텍스트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-122">The user-defined function gives workload group context for the session.</span></span> <span data-ttu-id="ff5a2-123">그룹 멤버가 확인되면 세션은 세션이 사용되는 기간 동안 작업 그룹에 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-123">After group membership is determined, the session is bound to the workload group for the lifetime of the session.</span></span>  
  
-   <span data-ttu-id="ff5a2-124">사용자 정의 함수가 NULL, 기본값 또는 존재하지 않는 그룹의 이름을 반환하면 기본 작업 그룹 컨텍스트가 세션에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-124">If the user-defined function returns NULL, default, or the name of non-existent group the session is given the default workload group context.</span></span> <span data-ttu-id="ff5a2-125">또한 어떤 이유로든 함수가 실패하는 경우에도 세션에 기본 컨텍스트가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-125">The session is also given the default context if the function fails for any reason.</span></span>  
  
-   <span data-ttu-id="ff5a2-126">함수는 서버 범위(master 데이터베이스)로 정의되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-126">The function should be defined with server scope (master database).</span></span>  
  
-   <span data-ttu-id="ff5a2-127">분류자 사용자 정의 함수 지정은 ALTER RESOURCE GOVERNOR RECONFIGURE가 실행된 후에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-127">The classifier user-defined function designation only takes effect after ALTER RESOURCE GOVERNOR RECONFIGURE is executed.</span></span>  
  
-   <span data-ttu-id="ff5a2-128">한 번에 하나의 사용자 정의 함수만 분류자로 지정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-128">Only one user-defined function can be designated as a classifier at a time.</span></span>  
  
-   <span data-ttu-id="ff5a2-129">해당 분류자 상태가 제거되지 않는 한 분류자 사용자 정의 함수는 삭제하거나 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-129">The classifier user-defined function cannot be dropped or altered unless its classifier status is removed.</span></span>  
  
-   <span data-ttu-id="ff5a2-130">분류자 사용자 정의 함수가 없으면 모든 세션이 기본 그룹으로 분류됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-130">In the absence of a classifier user-defined function, all sessions are classified into the default group.</span></span>  
  
-   <span data-ttu-id="ff5a2-131">분류자 함수에서 반환한 작업 그룹은 스키마 바인딩 제한의 범위를 벗어납니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-131">The workload group returned by the classifier function is outside the scope of the schema-binding restriction.</span></span> <span data-ttu-id="ff5a2-132">예를 들어 테이블은 삭제할 수 없지만 작업 그룹은 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-132">For example, you cannot drop a table, but you can drop a workload group.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ff5a2-133">서버에서 DAC(관리자 전용 연결)를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-133">We recommend enabling the Dedicated Administrator Connection (DAC) on the server.</span></span> <span data-ttu-id="ff5a2-134">DAC는 리소스 관리자 분류의 영향을 받지 않으며 분류자 함수의 모니터링 및 문제 해결에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-134">The DAC is not subject to Resource Governor classification and can be used to monitor and troubleshoot a classifier function.</span></span> <span data-ttu-id="ff5a2-135">자세한 내용은 [데이터베이스 관리자를 위한 진단 연결](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-135">For more information, see [Diagnostic Connection for Database Administrators](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md).</span></span> <span data-ttu-id="ff5a2-136">문제 해결에 DAC를 사용할 수 없는 경우 사용 가능한 다른 방법은 단일 사용자 모드로 시스템을 다시 시작하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-136">If a DAC is not available for troubleshooting, the other option is to restart the system in single user mode.</span></span> <span data-ttu-id="ff5a2-137">단일 사용자 모드는 분류의 영향을 받지 않지만 이렇게 해도 리소스 관리자 분류가 실행 중일 때 이를 진단하는 기능은 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-137">Although single user mode is not subject to classification, it does not give you the ability to diagnose Resource Governor classification while it is running.</span></span>  
  
### <a name="classification-process"></a><span data-ttu-id="ff5a2-138">분류 프로세스</span><span class="sxs-lookup"><span data-stu-id="ff5a2-138">Classification Process</span></span>  
 <span data-ttu-id="ff5a2-139">리소스 관리자 컨텍스트에서 세션에 대한 로그인 프로세스는 다음 단계로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-139">In the context of Resource Governor, the login process for a session consists of the following steps:</span></span>  
  
1.  <span data-ttu-id="ff5a2-140">로그인 인증</span><span class="sxs-lookup"><span data-stu-id="ff5a2-140">Login authentication</span></span>  
  
2.  <span data-ttu-id="ff5a2-141">LOGON 트리거 실행</span><span class="sxs-lookup"><span data-stu-id="ff5a2-141">LOGON trigger execution</span></span>  
  
3.  <span data-ttu-id="ff5a2-142">분류</span><span class="sxs-lookup"><span data-stu-id="ff5a2-142">Classification</span></span>  
  
 <span data-ttu-id="ff5a2-143">분류가 시작되면 리소스 관리자는 분류자 함수를 실행하고 이 함수에서 반환된 값을 사용하여 적절한 작업 그룹으로 요청을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-143">When classification starts, Resource Governor executes the classifier function and uses the value returned by the function to send requests to the appropriate workload group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ff5a2-144">분류자 함수 및 LOGON 트리거 실행에 대한 자세한 내용은 [sys.dm_exec_sessions](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) 및 [sys.dm_exec_requests](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-144">Information about the execution of the classifier function and LOGON triggers is exposed in [sys.dm_exec_sessions](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) and [sys.dm_exec_requests](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql).</span></span>  
  
## <a name="classification-function-tasks"></a><span data-ttu-id="ff5a2-145">분류 함수 태스크</span><span class="sxs-lookup"><span data-stu-id="ff5a2-145">Classification Function Tasks</span></span>  
  
|<span data-ttu-id="ff5a2-146">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="ff5a2-146">Task Description</span></span>|<span data-ttu-id="ff5a2-147">항목</span><span class="sxs-lookup"><span data-stu-id="ff5a2-147">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="ff5a2-148">분류자 사용자 정의 함수를 만들고 테스트하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ff5a2-148">Describes how to create and test a classifier user-defined function.</span></span>|[<span data-ttu-id="ff5a2-149">분류자 사용자 정의 함수 만들기 및 테스트</span><span class="sxs-lookup"><span data-stu-id="ff5a2-149">Create and Test a Classifier User-Defined Function</span></span>](create-and-test-a-classifier-user-defined-function.md)|  
  
## <a name="see-also"></a><span data-ttu-id="ff5a2-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ff5a2-150">See Also</span></span>  
 <span data-ttu-id="ff5a2-151">[리소스 관리자](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="ff5a2-151">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="ff5a2-152">[리소스 관리자 사용](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="ff5a2-152">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="ff5a2-153">[리소스 관리자 리소스 풀](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="ff5a2-153">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="ff5a2-154">[리소스 관리자 작업 그룹](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="ff5a2-154">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="ff5a2-155">[템플릿을 사용하여 리소스 관리자 구성](configure-resource-governor-using-a-template.md) </span><span class="sxs-lookup"><span data-stu-id="ff5a2-155">[Configure Resource Governor Using a Template](configure-resource-governor-using-a-template.md) </span></span>  
 [<span data-ttu-id="ff5a2-156">리소스 관리자 속성 보기</span><span class="sxs-lookup"><span data-stu-id="ff5a2-156">View Resource Governor Properties</span></span>](view-resource-governor-properties.md)  
  
  
