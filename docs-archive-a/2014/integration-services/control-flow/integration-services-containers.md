---
title: Integration Services 컨테이너 | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS containers
- containers [Integration Services]
- containers [Integration Services], about containers
- control flow [Integration Services], containers
- SQL Server Integration Services containers
ms.assetid: 1b725922-ec59-4a47-9d55-e079463058f3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1b8c3904d74427d5f70bd3ae81890adf66e9f818
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649623"
---
# <a name="integration-services-containers"></a><span data-ttu-id="79dc4-102">Integration Services 컨테이너</span><span class="sxs-lookup"><span data-stu-id="79dc4-102">Integration Services Containers</span></span>
  <span data-ttu-id="79dc4-103">컨테이너는 패키지에 구조를 제공하고 태스크에 서비스를 제공하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]의 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-103">Containers are objects in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] that provide structure to packages and services to tasks.</span></span> <span data-ttu-id="79dc4-104">패키지의 반복 제어 흐름을 지원하고 태스크와 컨테이너를 의미 있는 작업 단위로 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-104">They support repeating control flows in packages, and they group tasks and containers into meaningful units of work.</span></span> <span data-ttu-id="79dc4-105">컨테이너는 태스크 외에도 다른 컨테이너를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-105">Containers can include other containers in addition to tasks.</span></span>  
  
 <span data-ttu-id="79dc4-106">패키지는 컨테이너를 다음 용도로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-106">Packages use containers for the following purposes:</span></span>  
  
-   <span data-ttu-id="79dc4-107">폴더의 파일, 스키마 또는 SMO( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects) 개체와 같은 컬렉션의 각 요소에 대해 태스크를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-107">Repeat tasks for each element in a collection, such as files in a folder, schemas, or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO) objects.</span></span> <span data-ttu-id="79dc4-108">예를 들어 패키지는 여러 파일에 있는 Transact-SQL 문을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-108">For example, a package can run Transact-SQL statements that reside in multiple files.</span></span>  
  
-   <span data-ttu-id="79dc4-109">지정한 식이 `false`가 될 때까지 태스크를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-109">Repeat tasks until a specified expression evaluates to `false`.</span></span> <span data-ttu-id="79dc4-110">예를 들어 패키지는 하루에 한 번씩 매일 다른 전자 메일 메시지를 일주일 동안 7번 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-110">For example, a package can send a different e-mail message seven times, one time for every day of the week.</span></span>  
  
-   <span data-ttu-id="79dc4-111">하나의 단위로 성공하거나 실패해야 하는 태스크와 컨테이너를 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-111">Group tasks and containers that must succeed or fail as a unit.</span></span> <span data-ttu-id="79dc4-112">예를 들어 패키지는 데이터베이스 테이블에서 행을 삭제하고 추가하는 태스크를 그룹화한 다음 특정 태스크가 실패하면 모든 태스크를 커밋하거나 롤백할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-112">For example, a package can group tasks that delete and add rows in a database table, and then commit or roll back all the tasks when one fails.</span></span>  
  
## <a name="container-types"></a><span data-ttu-id="79dc4-113">컨테이너 유형</span><span class="sxs-lookup"><span data-stu-id="79dc4-113">Container Types</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="79dc4-114">는 패키지 빌드를 위해 4가지 컨테이너 유형을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-114">provides four types of containers for building packages.</span></span> <span data-ttu-id="79dc4-115">다음 표에서는 각 컨테이너 유형을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-115">The following table lists the container types.</span></span>  
  
|<span data-ttu-id="79dc4-116">컨테이너</span><span class="sxs-lookup"><span data-stu-id="79dc4-116">Container</span></span>|<span data-ttu-id="79dc4-117">Description</span><span class="sxs-lookup"><span data-stu-id="79dc4-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="79dc4-118">Foreach 루프 컨테이너</span><span class="sxs-lookup"><span data-stu-id="79dc4-118">Foreach Loop Container</span></span>](foreach-loop-container.md)|<span data-ttu-id="79dc4-119">열거자를 사용하여 제어 흐름을 반복적으로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-119">Runs a control flow repeatedly by using an enumerator.</span></span>|  
|[<span data-ttu-id="79dc4-120">For 루프 컨테이너</span><span class="sxs-lookup"><span data-stu-id="79dc4-120">For Loop Container</span></span>](for-loop-container.md)|<span data-ttu-id="79dc4-121">조건을 테스트하여 제어 흐름을 반복적으로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-121">Runs a control flow repeatedly by testing a condition.</span></span>|  
|[<span data-ttu-id="79dc4-122">시퀀스 컨테이너</span><span class="sxs-lookup"><span data-stu-id="79dc4-122">Sequence Container</span></span>](sequence-container.md)|<span data-ttu-id="79dc4-123">태스크와 컨테이너를 패키지 제어 흐름의 하위 집합인 제어 흐름으로 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-123">Groups tasks and containers into control flows that are subsets of the package control flow.</span></span>|  
|[<span data-ttu-id="79dc4-124">태스크 호스트 컨테이너</span><span class="sxs-lookup"><span data-stu-id="79dc4-124">Task Host Container</span></span>](task-host-container.md)|<span data-ttu-id="79dc4-125">단일 태스크에 서비스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-125">Provides services to a single task.</span></span>|  
  
 <span data-ttu-id="79dc4-126">패키지와 이벤트 처리기도 컨테이너 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-126">Packages and events handlers are also types of containers.</span></span> <span data-ttu-id="79dc4-127">자세한 내용은 [Integration Services&#40;SSIS&#41; 패키지](../integration-services-ssis-packages.md) 및 [Integration Services&#40;SSIS&#41; 이벤트 처리기](../integration-services-ssis-event-handlers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79dc4-127">For information see [Integration Services &#40;SSIS&#41; Packages](../integration-services-ssis-packages.md) and [Integration Services &#40;SSIS&#41; Event Handlers](../integration-services-ssis-event-handlers.md).</span></span>  
  
### <a name="summary-of-container-properties"></a><span data-ttu-id="79dc4-128">컨테이너 속성 요약</span><span class="sxs-lookup"><span data-stu-id="79dc4-128">Summary of Container Properties</span></span>  
 <span data-ttu-id="79dc4-129">모든 컨테이너 유형에는 공통된 속성 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-129">All container types have a set of properties in common.</span></span> <span data-ttu-id="79dc4-130">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 에서 제공되는 그래픽 도구를 사용하여 패키지를 만들 경우 속성 창에는 Foreach 루프, For 루프 및 시퀀스 컨테이너에 대한 다음 속성이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-130">If you create packages using the graphical tools that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides, the Properties window lists the following properties for the Foreach Loop, For Loop, and Sequence containers.</span></span> <span data-ttu-id="79dc4-131">태스크 호스트 컨테이너 속성은 태스크 호스트가 캡슐화하는 태스크를 구성하는 과정의 일부로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-131">The task host container properties are configured as part of configuring the task that the task host encapsulates.</span></span> <span data-ttu-id="79dc4-132">이 태스크를 구성할 때 태스크 호스트 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-132">You set the Task Host properties when you configure the task.</span></span>  
  
|<span data-ttu-id="79dc4-133">속성</span><span class="sxs-lookup"><span data-stu-id="79dc4-133">Property</span></span>|<span data-ttu-id="79dc4-134">Description</span><span class="sxs-lookup"><span data-stu-id="79dc4-134">Description</span></span>|  
|--------------|-----------------|  
|`DelayValidation`|<span data-ttu-id="79dc4-135">컨테이너의 유효성 검사가 런타임까지 지연되는지 여부를 나타내는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-135">A Boolean value that indicates whether validation of the container is delayed until run time.</span></span> <span data-ttu-id="79dc4-136">이 속성의 기본값은 `False`입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-136">The default value for this property is `False`.</span></span><br /><br /> <span data-ttu-id="79dc4-137">자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.DelayValidation%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79dc4-137">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.DelayValidation%2A>.</span></span>|  
|`Description`|<span data-ttu-id="79dc4-138">컨테이너 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-138">The container description.</span></span> <span data-ttu-id="79dc4-139">이 속성에는 문자열이 포함되지만 비워 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-139">The property contains a string, but may be blank.</span></span><br /><br /> <span data-ttu-id="79dc4-140">자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.Description%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79dc4-140">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.Description%2A>.</span></span>|  
|`Disable`|<span data-ttu-id="79dc4-141">컨테이너가 실행되는지 여부를 나타내는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-141">A Boolean value that indicates whether the container runs.</span></span> <span data-ttu-id="79dc4-142">이 속성의 기본값은 `False`입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-142">The default value for this property is `False`.</span></span><br /><br /> <span data-ttu-id="79dc4-143">자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.Disable%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79dc4-143">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.Disable%2A>.</span></span>|  
|`DisableEventHandlers`|<span data-ttu-id="79dc4-144">컨테이너와 연결된 이벤트 처리기가 실행되는지 여부를 나타내는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-144">A Boolean value that indicates whether the event handlers associated with the container run.</span></span> <span data-ttu-id="79dc4-145">이 속성의 기본값은 `False`입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-145">The default value for this property is `False`.</span></span>|  
|`FailPackageOnFailure`|<span data-ttu-id="79dc4-146">컨테이너에서 오류가 발생하는 경우 패키지가 실패하는지 여부를 지정하는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-146">A Boolean value that specifies whether the package fails if an error occurs in the container.</span></span> <span data-ttu-id="79dc4-147">이 속성의 기본값은 `False`입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-147">The default value for this property is `False`.</span></span><br /><br /> <span data-ttu-id="79dc4-148">자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.FailPackageOnFailure%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79dc4-148">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.FailPackageOnFailure%2A>.</span></span>|  
|`FailParentOnFailure`|<span data-ttu-id="79dc4-149">컨테이너에서 오류가 발생하는 경우 부모 컨테이너가 실패하는지 여부를 지정하는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-149">A Boolean value that specifies whether the parent container fails if an error occurs in the container.</span></span> <span data-ttu-id="79dc4-150">이 속성의 기본값은 `False`입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-150">The default value for this property is `False`.</span></span><br /><br /> <span data-ttu-id="79dc4-151">자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.FailParentOnFailure%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79dc4-151">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.FailParentOnFailure%2A>.</span></span>|  
|`ForcedExecutionValue`|<span data-ttu-id="79dc4-152">`ForceExecutionValue`가 `True`로 설정된 경우 컨테이너의 선택적 실행 값을 포함하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-152">If `ForceExecutionValue` is set to `True`, the object that contains the optional execution value for the container.</span></span> <span data-ttu-id="79dc4-153">이 속성의 기본값은 **0**입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-153">The default value of this property is **0**.</span></span><br /><br /> <span data-ttu-id="79dc4-154">자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ForcedExecutionValue%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79dc4-154">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ForcedExecutionValue%2A>.</span></span>|  
|`ForcedExecutionValueType`|<span data-ttu-id="79dc4-155">`ForcedExecutionValue`의 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-155">The data type of `ForcedExecutionValue`.</span></span> <span data-ttu-id="79dc4-156">이 속성의 기본값은 `Int32`입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-156">The default value of this property is `Int32`.</span></span>|  
|`ForceExecutionResult`|<span data-ttu-id="79dc4-157">패키지 또는 컨테이너 강제 실행 결과를 지정하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-157">A value that specifies the forced result of running the package or container.</span></span> <span data-ttu-id="79dc4-158">가능한 값은 `None`, `Success`, `Failure` 및 `Completion`입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-158">The values are `None`, `Success`, `Failure`, and `Completion`.</span></span> <span data-ttu-id="79dc4-159">이 속성의 기본값은 `None`입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-159">The default value for this property is `None`.</span></span><br /><br /> <span data-ttu-id="79dc4-160">자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ForceExecutionResult%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79dc4-160">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ForceExecutionResult%2A>.</span></span>|  
|`ForceExecutionValue`|<span data-ttu-id="79dc4-161">컨테이너의 선택적 실행 값에 특정 값이 포함되도록 강제해야 하는지 여부를 나타내는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-161">A Boolean value that specifies whether the optional execution value of the container should be forced to contain a particular value.</span></span> <span data-ttu-id="79dc4-162">이 속성의 기본값은 `False`입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-162">The default value of this property is `False`.</span></span><br /><br /> <span data-ttu-id="79dc4-163">자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ForceExecutionValue%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79dc4-163">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ForceExecutionValue%2A>.</span></span>|  
|`ID`|<span data-ttu-id="79dc4-164">패키지를 만들 때 할당된 컨테이너 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-164">The container GUID, which is assigned when the package is created.</span></span> <span data-ttu-id="79dc4-165">이 속성은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-165">This property is read-only.</span></span><br /><br /> <span data-ttu-id="79dc4-166"><xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ID%2A>.</span><span class="sxs-lookup"><span data-stu-id="79dc4-166"><xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ID%2A>.</span></span>|  
|`IsolationLevel`|<span data-ttu-id="79dc4-167">컨테이너 트랜잭션의 격리 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-167">The isolation level of the container transaction.</span></span> <span data-ttu-id="79dc4-168">가능한 값은 `Unspecified`, `Chaos`, `ReadUncommitted`, `ReadCommitted`, `RepeatableRead`, `Serializable` 및 `Snapshot`입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-168">The values are `Unspecified`, `Chaos`, `ReadUncommitted`, `ReadCommitted`, `RepeatableRead`, `Serializable`, and `Snapshot`.</span></span> <span data-ttu-id="79dc4-169">이 속성의 기본값은 `Serializable`입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-169">The default value of this property is `Serializable`.</span></span> <span data-ttu-id="79dc4-170">자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.IsolationLevel%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79dc4-170">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.IsolationLevel%2A>.</span></span>|  
|`LocaleID`|<span data-ttu-id="79dc4-171">Microsoft Win32 로캘입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-171">A Microsoft Win32 locale.</span></span> <span data-ttu-id="79dc4-172">이 속성의 기본값은 로컬 컴퓨터 운영 체제의 로캘입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-172">The default value of this property is the locale of the operating system on the local computer.</span></span><br /><br /> <span data-ttu-id="79dc4-173">자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LocaleID%2A>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79dc4-173">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LocaleID%2A>.</span></span>|  
|`LoggingMode`|<span data-ttu-id="79dc4-174">컨테이너의 로깅 동작을 지정하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-174">A value that specifies the logging behavior of the container.</span></span> <span data-ttu-id="79dc4-175">가능한 값은 `Disabled`, `Enabled` 및 `UseParentSetting`입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-175">The values are `Disabled`, `Enabled`, and `UseParentSetting`.</span></span> <span data-ttu-id="79dc4-176">이 속성의 기본값은 `UseParentSetting`입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-176">The default value of this property is `UseParentSetting`.</span></span> <span data-ttu-id="79dc4-177">자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79dc4-177">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode>.</span></span>|  
|`MaximumErrorCount`|<span data-ttu-id="79dc4-178">컨테이너 실행이 중지될 때까지 발생할 수 있는 최대 오류 수입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-178">The maximum number of errors that can occur before a container stops running.</span></span> <span data-ttu-id="79dc4-179">이 속성의 기본값은 **1**입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-179">The default value of this property is **1**.</span></span><br /><br /> <span data-ttu-id="79dc4-180">자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.MaximumErrorCount%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79dc4-180">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.MaximumErrorCount%2A>.</span></span>|  
|`Name`|<span data-ttu-id="79dc4-181">컨테이너의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-181">The name of the container.</span></span><br /><br /> <span data-ttu-id="79dc4-182">자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.Name%2A>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79dc4-182">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.Name%2A>.</span></span>|  
|`TransactionOption`|<span data-ttu-id="79dc4-183">컨테이너의 트랜잭션 참여 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-183">The transactional participation of the container.</span></span> <span data-ttu-id="79dc4-184">가능한 값은 `NotSupported`, `Supported` 및 `Required`입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-184">The values are `NotSupported`, `Supported`, `Required`.</span></span> <span data-ttu-id="79dc4-185">이 속성의 기본값은 `Supported`입니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-185">The default value of this property is `Supported`.</span></span> <span data-ttu-id="79dc4-186">자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.DTSTransactionOption>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79dc4-186">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DTSTransactionOption>.</span></span>|  
  
 <span data-ttu-id="79dc4-187">프로그래밍 방식으로 구성할 경우 Foreach 루프, For 루프, 시퀀스 및 태스크 호스트 컨테이너에 사용할 수 있는 모든 속성에 대한 자세한 내용은 다음 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] API 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="79dc4-187">To learn about all the properties that are available to Foreach Loop, For Loop, Sequence, and Task Host containers when configure them programmatically, see the following [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] API topics:</span></span>  
  
-   <span data-ttu-id="79dc4-188">T:Microsoft.SqlServer.Dts.Runtime.ForEachLoop</span><span class="sxs-lookup"><span data-stu-id="79dc4-188">T:Microsoft.SqlServer.Dts.Runtime.ForEachLoop</span></span>  
  
-   <span data-ttu-id="79dc4-189">T:Microsoft.SqlServer.Dts.Runtime.ForLoop</span><span class="sxs-lookup"><span data-stu-id="79dc4-189">T:Microsoft.SqlServer.Dts.Runtime.ForLoop</span></span>  
  
-   <span data-ttu-id="79dc4-190">T:Microsoft.SqlServer.Dts.Runtime.Sequence</span><span class="sxs-lookup"><span data-stu-id="79dc4-190">T:Microsoft.SqlServer.Dts.Runtime.Sequence</span></span>  
  
-   <span data-ttu-id="79dc4-191">T:Microsoft.SqlServer.Dts.Runtime.TaskHost</span><span class="sxs-lookup"><span data-stu-id="79dc4-191">T:Microsoft.SqlServer.Dts.Runtime.TaskHost</span></span>  
  
## <a name="objects-that-extend-container-functionality"></a><span data-ttu-id="79dc4-192">컨테이너 기능을 확장하는 개체</span><span class="sxs-lookup"><span data-stu-id="79dc4-192">Objects that Extend Container Functionality</span></span>  
 <span data-ttu-id="79dc4-193">컨테이너는 실행 파일과 선행 제약 조건으로 구성된 제어 흐름을 포함하며 이벤트 처리기와 변수를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-193">Containers include control flows that consist of executables and precedence constraints, and may use event handlers, and variables.</span></span> <span data-ttu-id="79dc4-194">단, 태스크 호스트 컨테이너는 예외입니다. 태스크 호스트 컨테이너는 단일 태스크를 캡슐화하기 때문에 선행 제약 조건을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-194">The task host container is an exception: because the task host container encapsulates a single task, it does not use precedence constraints.</span></span>  
  
### <a name="executables"></a><span data-ttu-id="79dc4-195">실행 파일</span><span class="sxs-lookup"><span data-stu-id="79dc4-195">Executables</span></span>  
 <span data-ttu-id="79dc4-196">실행 파일은 컨테이너 수준 태스크와 해당 컨테이너에 있는 모든 컨테이너를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-196">Executables refers to the container-level tasks and any containers within the container.</span></span> <span data-ttu-id="79dc4-197">실행 파일은 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 에서 제공하는 태스크 및 컨테이너 중 하나이거나 사용자 지정 태스크일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-197">An executable can be one of the tasks and containers that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides or a custom task.</span></span> <span data-ttu-id="79dc4-198">자세한 내용은 [Integration Services 작업](integration-services-tasks.md) 및 [Integration Services 컨테이너](integration-services-containers.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="79dc4-198">For more information, see [Integration Services Tasks](integration-services-tasks.md) and [Integration Services Containers](integration-services-containers.md).</span></span>  
  
### <a name="precedence-constraints"></a><span data-ttu-id="79dc4-199">선행 제약 조건</span><span class="sxs-lookup"><span data-stu-id="79dc4-199">Precedence Constraints</span></span>  
 <span data-ttu-id="79dc4-200">선행 제약 조건은 부모 컨테이너가 같은 컨테이너와 태스크를 정렬된 제어 흐름으로 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-200">Precedence constraints link containers and tasks within the same parent container into an ordered control flow.</span></span> <span data-ttu-id="79dc4-201">자세한 내용은 [Precedence Constraints](precedence-constraints.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79dc4-201">For more information, see [Precedence Constraints](precedence-constraints.md).</span></span>  
  
### <a name="event-handlers"></a><span data-ttu-id="79dc4-202">이벤트 처리기</span><span class="sxs-lookup"><span data-stu-id="79dc4-202">Event Handlers</span></span>  
 <span data-ttu-id="79dc4-203">컨테이너 수준의 이벤트 처리기는 컨테이너 또는 컨테이너에 포함된 개체에 의해 발생한 이벤트에 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-203">Event handlers at the container level respond to events raised by the container or the objects it includes.</span></span> <span data-ttu-id="79dc4-204">자세한 내용은 [Integration Services&#40;SSIS&#41; 이벤트 처리기](../integration-services-ssis-event-handlers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79dc4-204">For more information, see [Integration Services &#40;SSIS&#41; Event Handlers](../integration-services-ssis-event-handlers.md).</span></span>  
  
### <a name="variables"></a><span data-ttu-id="79dc4-205">variables</span><span class="sxs-lookup"><span data-stu-id="79dc4-205">Variables</span></span>  
 <span data-ttu-id="79dc4-206">컨테이너에서 사용되는 변수는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 에서 제공하는 컨테이너 수준의 시스템 변수와 해당 컨테이너가 사용하는 사용자 정의 변수를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-206">Variables that are used in containers include the container-level system variables that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides and the user-defined variables that the container uses.</span></span> <span data-ttu-id="79dc4-207">자세한 내용은 [Integration Services&#40;SSIS&#41; 변수](../integration-services-ssis-variables.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79dc4-207">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
## <a name="break-points"></a><span data-ttu-id="79dc4-208">중단점</span><span class="sxs-lookup"><span data-stu-id="79dc4-208">Break Points</span></span>  
 <span data-ttu-id="79dc4-209">컨테이너의 중단점을 설정할 때 중단 조건이 **컨테이너가 OnVariableValueChanged 이벤트를 받는 경우 중단**인 경우 컨테이너 범위의 변수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="79dc4-209">When you set a breakpoint on a container and the break condition is **Break when the container recevies the OnVariableValueChanged event**, define the variable in the container scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79dc4-210">참고 항목</span><span class="sxs-lookup"><span data-stu-id="79dc4-210">See Also</span></span>  
 [<span data-ttu-id="79dc4-211">제어 흐름</span><span class="sxs-lookup"><span data-stu-id="79dc4-211">Control Flow</span></span>](control-flow.md)  
  
  