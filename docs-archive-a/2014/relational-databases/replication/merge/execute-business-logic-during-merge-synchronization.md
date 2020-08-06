---
title: 병합 동기화 중 비즈니스 논리 실행 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- custom error resolution [SQL Server replication]
- custom change handling [SQL Server replication]
- errors [SQL Server replication], business logic handlers
- merge replication business logic handlers [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
- business logic handlers [SQL Server replication]
ms.assetid: 9d4da2ef-c17f-4a31-a1f6-5c3b7ca85f71
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1e082cbbb46ceae712cd39925c28fe89988a3793
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638714"
---
# <a name="execute-business-logic-during-merge-synchronization"></a><span data-ttu-id="aaa85-102">병합 동기화 중 비즈니스 논리 실행</span><span class="sxs-lookup"><span data-stu-id="aaa85-102">Execute Business Logic During Merge Synchronization</span></span>
  <span data-ttu-id="aaa85-103">비즈니스 논리 처리기 프레임워크를 사용하면 병합 동기화 과정 동안 호출되는 관리 코드 어셈블리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-103">The business logic handler framework allows you to write a managed code assembly that is called during the merge synchronization process.</span></span> <span data-ttu-id="aaa85-104">이 어셈블리에는 동기화 중 데이터 변경, 충돌, 오류 등의 여러 상황에 응답할 수 있는 비즈니스 논리가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-104">The assembly includes business logic that can respond to a number of conditions during synchronization: data changes, conflicts, and errors.</span></span> <span data-ttu-id="aaa85-105">비즈니스 논리 처리기 프레임워크에서 단순한 프로그래밍 모델을 제공하고 병합 프로세스에서 사용자 어셈블리에 ADO.NET 데이터 집합을 제공하므로 사용자는 소유 인터페이스를 새로 익히지 않고 ADO.NET에 대한 지식을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-105">The business logic handler framework provides a simple programming model, and the data that the merge process provides to your assembly is in the form of an ADO.NET data set, so you can leverage knowledge of ADO.NET rather than learning a proprietary interface.</span></span> <span data-ttu-id="aaa85-106">비즈니스 논리 처리기 프로그래밍에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="aaa85-106">For more information on programming business logic handlers, see:</span></span>  
  
-   <span data-ttu-id="aaa85-107">API(애플리케이션 프로그래밍 인터페이스) 참조: <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport></span><span class="sxs-lookup"><span data-stu-id="aaa85-107">The application programming interface (API) reference: <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport></span></span>  
  
-   <span data-ttu-id="aaa85-108">비즈니스 논리 처리기 구현 방법: [병합 아티클에 대한 비즈니스 논리 처리기 구현](../implement-a-business-logic-handler-for-a-merge-article.md)</span><span class="sxs-lookup"><span data-stu-id="aaa85-108">Instructions on how to implement a business logic handler: [Implement a Business Logic Handler for a Merge Article](../implement-a-business-logic-handler-for-a-merge-article.md)</span></span>  
  
## <a name="uses-for-business-logic-handlers"></a><span data-ttu-id="aaa85-109">비즈니스 논리 처리기 용도</span><span class="sxs-lookup"><span data-stu-id="aaa85-109">Uses for Business Logic Handlers</span></span>  
 <span data-ttu-id="aaa85-110">병합 동기화 프로세스는 비즈니스 논리 처리기를 호출하여 다음 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-110">The merge synchronization process can invoke business logic handlers to perform:</span></span>  
  
-   <span data-ttu-id="aaa85-111">사용자 지정 변경 처리</span><span class="sxs-lookup"><span data-stu-id="aaa85-111">Custom change handling</span></span>  
  
-   <span data-ttu-id="aaa85-112">사용자 지정 충돌 해결</span><span class="sxs-lookup"><span data-stu-id="aaa85-112">Custom conflict resolution</span></span>  
  
-   <span data-ttu-id="aaa85-113">사용자 지정 오류 해결</span><span class="sxs-lookup"><span data-stu-id="aaa85-113">Custom error resolution</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aaa85-114">사용자가 지정하는 비즈니스 논리 처리기는 동기화되는 모든 행에 대해 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-114">The business logic handler you specify is executed for every row that is synchronized.</span></span> <span data-ttu-id="aaa85-115">네트워크 서비스 또는 다른 애플리케이션에 대한 호출과 복잡한 논리가 성능에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-115">Complex logic and calls to other applications or network services can impact performance.</span></span>  
  
### <a name="custom-change-handling"></a><span data-ttu-id="aaa85-116">사용자 지정 변경 처리</span><span class="sxs-lookup"><span data-stu-id="aaa85-116">Custom Change Handling</span></span>  
 <span data-ttu-id="aaa85-117">비즈니스 논리 처리기는 충돌을 일으키지 않는 데이터 변경을 처리하는 중 호출할 수 있으며 다음 3가지 동작 중 하나를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-117">The business logic handler can be invoked during the processing of non-conflicting data changes and can perform one of three actions:</span></span>  
  
-   <span data-ttu-id="aaa85-118">데이터 거부</span><span class="sxs-lookup"><span data-stu-id="aaa85-118">Reject the data</span></span>  
  
     <span data-ttu-id="aaa85-119">이 작업은 지정된 구독자에서 변경 내용을 전파하지 않으려는 애플리케이션에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-119">This is useful for applications that do not want changes propagated to or from a given Subscriber.</span></span> <span data-ttu-id="aaa85-120">예를 들어 관리자는 구독자의 파티션에 속하지 않는 삽입을 필터링하거나 구독자에서 수행된 삭제를 거부할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-120">For example, an administrator could filter out inserts that do not belong in the Subscriber's partition, or possibly reject deletes performed at a Subscriber.</span></span> <span data-ttu-id="aaa85-121">또 다른 예로 재고가 없을 경우 애플리케이션은 구독자에서 입력한 주문을 거부할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-121">As another example, an application could reject an order entered at a Subscriber because the inventory is no longer available.</span></span>  
  
-   <span data-ttu-id="aaa85-122">데이터 적용</span><span class="sxs-lookup"><span data-stu-id="aaa85-122">Accept the data</span></span>  
  
     <span data-ttu-id="aaa85-123">이 작업은 게시자 또는 구독자에서의 데이터 변경 내용을 전파하기 전에 확인할 필요가 있는 애플리케이션에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-123">This is useful for applications in which it is necessary to review data changes made at either the Publisher or Subscriber before allowing them to be propagated.</span></span> <span data-ttu-id="aaa85-124">예를 들어 중간 계층 애플리케이션이 현장에서 들어오는 새 주문을 검사하고 이를 중간 계층의 입고 워크플로 프로세스에 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-124">For example, a mid-tier application could examine new orders coming in from the field and integrate with a procurement workflow process in the mid-tier.</span></span>  
  
-   <span data-ttu-id="aaa85-125">사용자 지정 데이터 적용</span><span class="sxs-lookup"><span data-stu-id="aaa85-125">Apply custom data</span></span>  
  
     <span data-ttu-id="aaa85-126">이 작업은 특정 데이터 값 또는 작업을 재정의할 필요가 있는 애플리케이션에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-126">This is useful for applications that need to override specific data values or operations.</span></span> <span data-ttu-id="aaa85-127">예를 들어 애플리케이션은 행의 **status** 열 값을 "deleted"로 설정한 다음 삭제를 수행하는 클라이언트 ID를 추적하는 특수 업데이트로 행 삭제를 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-127">For example, an application could transform a row delete into a special update that sets a **status** column in the row to a value of "deleted" and then tracks the identity of the client performing the delete.</span></span> <span data-ttu-id="aaa85-128">이 방법은 감사 또는 워크플로에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-128">This might be useful for auditing or workflow purposes.</span></span>  
  
### <a name="custom-conflict-resolution"></a><span data-ttu-id="aaa85-129">사용자 지정 충돌 해결</span><span class="sxs-lookup"><span data-stu-id="aaa85-129">Custom Conflict Resolution</span></span>  
 <span data-ttu-id="aaa85-130">사용자는 병합 복제에서 제공하는 충돌 감지 및 해결 기능을 사용하여 충돌에 대해 기본 해결 전략을 적용하거나 사용자 지정 해결을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-130">Merge replication provides conflict detection and resolution, allowing you to accept a default resolution strategy or choose custom resolution for conflicts.</span></span> <span data-ttu-id="aaa85-131">자세한 내용은 [고급 병합 복제 충돌 감지 및 해결](advanced-merge-replication-conflict-detection-and-resolution.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aaa85-131">For more information, see [Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md).</span></span> <span data-ttu-id="aaa85-132">비즈니스 논리 처리기는 충돌하는 데이터 변경을 처리하는 중 호출할 수 있으며 다음 두 가지 동작 중 하나를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-132">The business logic handler can be invoked during the processing of conflicting data changes and can perform one of two actions:</span></span>  
  
-   <span data-ttu-id="aaa85-133">기본 해결 적용</span><span class="sxs-lookup"><span data-stu-id="aaa85-133">Accept default resolution</span></span>  
  
     <span data-ttu-id="aaa85-134">이 작업은 충돌을 검토하고, 추가 동작을 수행하고, 사용자 지정 충돌 로그 메시지를 기록해야 하는 애플리케이션에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-134">This is useful for applications that might need to review the conflict, perform additional actions, and possibly log a custom conflict log message.</span></span>  
  
-   <span data-ttu-id="aaa85-135">사용자 지정 해결 수행</span><span class="sxs-lookup"><span data-stu-id="aaa85-135">Perform custom resolution</span></span>  
  
     <span data-ttu-id="aaa85-136">이 작업은 해당 비즈니스 논리와 관련된 데이터 값을 선택하고 동기화 프로세스에 이 사용자 지정 데이터 세트를 제공해야 하는 애플리케이션에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-136">This is useful for applications that might need to select data values that are specific to their business logic and supply the synchronization process with this custom dataset.</span></span> <span data-ttu-id="aaa85-137">예를 들어 애플리케이션은 게시자 데이터 집합의 값과 구독자 데이터 집합의 값을 결합하여 새 버전의 적용되는 행을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-137">For example, an application could provide a new version of the winning row by combining values from the Publisher and Subscriber data sets.</span></span>  
  
### <a name="custom-error-resolution"></a><span data-ttu-id="aaa85-138">사용자 지정 오류 해결</span><span class="sxs-lookup"><span data-stu-id="aaa85-138">Custom Error Resolution</span></span>  
 <span data-ttu-id="aaa85-139">오류를 일으키는 변경 내용을 전파하는 중 사용자 지정 논리를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-139">Custom logic can be invoked during the propagation of changes that result in errors.</span></span> <span data-ttu-id="aaa85-140">사용자 지정 논리는 다음 두 동작 중 하나를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-140">The logic can perform one of two actions:</span></span>  
  
-   <span data-ttu-id="aaa85-141">기본 오류 해결 적용</span><span class="sxs-lookup"><span data-stu-id="aaa85-141">Accept default error resolution</span></span>  
  
     <span data-ttu-id="aaa85-142">이 작업은 오류를 검토하고, 추가 동작을 수행하고, 사용자 지정 오류 로그 메시지를 기록해야 하는 애플리케이션에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-142">This is useful for applications that might need to review the error and perform additional action and possibly log a custom error log message.</span></span>  
  
-   <span data-ttu-id="aaa85-143">사용자 지정 오류 해결 적용</span><span class="sxs-lookup"><span data-stu-id="aaa85-143">Accept custom error resolution</span></span>  
  
     <span data-ttu-id="aaa85-144">이 작업은 해당 비즈니스 논리와 관련된 데이터 값을 선택하고 동기화 프로세스에 이 사용자 지정 데이터 세트를 제공해야 하는 애플리케이션에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-144">This is useful for applications that might need to select data values that are specific to their business logic and supply the synchronization process with this custom dataset.</span></span> <span data-ttu-id="aaa85-145">예를 들어 복제 프로세스에서 중복 키 위반이 발생하면 비즈니스 논리 처리기는 키가 충돌하지 않는 새 버전의 데이터 변경 내용을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-145">For example, if the replication process encounters a duplicate key violation, the business logic handler could provide a new version of the data change in which the key will no longer conflict.</span></span> <span data-ttu-id="aaa85-146">이렇게 하면 게시자 및 구독자에서 적용한 변경 내용이 데이터베이스에서 지속되며 복제 프로세스에서 삭제를 사용하여 실패한 삽입을 해결할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-146">Changes made at the Publisher and Subscriber can then persist in the database, and the replication process doesn't have to compensate for the failed insert with a delete.</span></span>  
  
## <a name="deployment-scenarios-for-business-logic-handlers"></a><span data-ttu-id="aaa85-147">비즈니스 논리 처리기의 배포 시나리오</span><span class="sxs-lookup"><span data-stu-id="aaa85-147">Deployment Scenarios for Business Logic Handlers</span></span>  
 <span data-ttu-id="aaa85-148">비즈니스 논리 처리기는 다음에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-148">Business logic handlers can be deployed at:</span></span>  
  
-   <span data-ttu-id="aaa85-149">배포자</span><span class="sxs-lookup"><span data-stu-id="aaa85-149">The Distributor.</span></span> <span data-ttu-id="aaa85-150">비즈니스 논리가 배포자에서 실행되도록 밀어넣기 구독을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-150">Use a push subscription so that business logic is executed at the Distributor.</span></span>  
  
-   <span data-ttu-id="aaa85-151">구독자.</span><span class="sxs-lookup"><span data-stu-id="aaa85-151">The Subscriber.</span></span> <span data-ttu-id="aaa85-152">비즈니스 논리가 구독자에서 실행되도록 끌어오기 구독을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-152">Use a pull subscription so that business logic is executed at the Subscriber.</span></span>  
  
-   <span data-ttu-id="aaa85-153">웹 동기화를 사용할 경우 인터넷 정보 서비스(IIS) 서버.</span><span class="sxs-lookup"><span data-stu-id="aaa85-153">An Internet Information Services (IIS) server if Web synchronization is used.</span></span> <span data-ttu-id="aaa85-154">웹 동기화를 통해 동기화된 끌어오기 구독을 사용하며 이로 인해 비즈니스 논리 처리기가 IIS 서버에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="aaa85-154">Use a pull subscription synchronized with Web synchronization, and the business logic handler will execute at the IIS Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaa85-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aaa85-155">See Also</span></span>  
 <span data-ttu-id="aaa85-156">[병합 복제](merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="aaa85-156">[Merge Replication](merge-replication.md) </span></span>  
 <span data-ttu-id="aaa85-157">[Subscribe to Publications](../subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="aaa85-157">[Subscribe to Publications](../subscribe-to-publications.md) </span></span>  
 <span data-ttu-id="aaa85-158">[데이터 동기화](../synchronize-data.md) </span><span class="sxs-lookup"><span data-stu-id="aaa85-158">[Synchronize Data](../synchronize-data.md) </span></span>  
 [<span data-ttu-id="aaa85-159">병합 복제에 대한 웹 동기화</span><span class="sxs-lookup"><span data-stu-id="aaa85-159">Web Synchronization for Merge Replication</span></span>](../web-synchronization-for-merge-replication.md)  
  
  
