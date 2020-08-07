---
title: 속성 식의 열거 상수 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], expressions
- dynamic properties
- updating package properties
- enumerated constants [Integration Services]
- property expressions [Integration Services]
ms.assetid: a4418315-38e2-4ad3-8784-576163b25d6f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b9cb4ae32bf564e98d8cfc843e9497b15222fa79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732863"
---
# <a name="enumerated-constants-in-property-expressions"></a><span data-ttu-id="63d55-102">속성 식의 열거 상수</span><span class="sxs-lookup"><span data-stu-id="63d55-102">Enumerated Constants in Property Expressions</span></span>
  <span data-ttu-id="63d55-103">속성 식에 열거자 멤버 목록의 값이 포함된 경우 식에 멤버 이름 대신 열거자 멤버의 숫자 값을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-103">If property expressions include values from an enumerator member list, the expression must use the numeric value of the enumerator member instead of the friendly name of the member.</span></span> <span data-ttu-id="63d55-104">예를 들어 식에 `LoggingMode` 속성을 설정한 경우 이름인 Disabled 대신 숫자 값 2를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-104">For example, if an expression sets the `LoggingMode` property then you must use the numeric value 2 instead of the friendly name Disabled.</span></span>  
  
 <span data-ttu-id="63d55-105">이 항목에서는 해당 멤버가 속성 식에서 일반적으로 사용되는 열거자의 이름에 해당하는 숫자 값만 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-105">This topic lists only the numeric values equivalent to friendly names of enumerators whose members are commonly used in property expressions.</span></span> <span data-ttu-id="63d55-106">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 개체 모델에는 프로그래밍 방식으로 패키지를 작성하거나 태스크 및 데이터 흐름 구성 요소와 같은 사용자 지정 패키지 요소를 코딩하기 위해 개체 모델을 프로그래밍할 때 사용하는 여러 개의 추가 열거자가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-106">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] object model includes many additional enumerators that you use when you program the object model to build packages programmatically or code custom package elements such as tasks and data flow components.</span></span>  
  
 <span data-ttu-id="63d55-107">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 의 속성 창에는 패키지 및 패키지 개체의 사용자 지정 속성 외에 패키지, 태스크 및 Foreach 루프, For 루프, 시퀀스 컨테이너에 사용할 수 있는 속성 집합이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-107">In addition to the custom properties for packages and package objects, the Properties window in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] includes a set of properties that are available to packages, tasks, and the Foreach Loop, For Loop, and Sequence containers.</span></span> <span data-ttu-id="63d55-108">열거자의 값으로 설정 된 공용 속성인, `ForceExecutionResult` `LoggingMode` , `IsolationLevel` 및은 `Transaction Option` 공용 속성 섹션에 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-108">The common properties that are set by values from enumerators-`ForceExecutionResult`, `LoggingMode`, `IsolationLevel`, and `Transaction Option`-are listed in Common Properties section.</span></span>  
  
 <span data-ttu-id="63d55-109">다음 섹션에서는 열거 상수에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-109">The following sections provide information about enumerated constants:</span></span>  
  
 [<span data-ttu-id="63d55-110">패키지</span><span class="sxs-lookup"><span data-stu-id="63d55-110">Package</span></span>](#Package)  
  
 [<span data-ttu-id="63d55-111">Foreach 루프 열거자</span><span class="sxs-lookup"><span data-stu-id="63d55-111">Foreach Loop Enumerators</span></span>](#Foreach)  
  
 [<span data-ttu-id="63d55-112">작업</span><span class="sxs-lookup"><span data-stu-id="63d55-112">Tasks</span></span>](#Tasks)  
  
 [<span data-ttu-id="63d55-113">유지 관리 계획 태스크</span><span class="sxs-lookup"><span data-stu-id="63d55-113">Maintenance Plan Tasks</span></span>](#MaintenancePlanTasks)  
  
 [<span data-ttu-id="63d55-114">Common Properties</span><span class="sxs-lookup"><span data-stu-id="63d55-114">Common Properties</span></span>](#CommonProperties)  
  
##  <a name="package"></a><a name="Package"></a> <span data-ttu-id="63d55-115">패키지</span><span class="sxs-lookup"><span data-stu-id="63d55-115">Package</span></span>  
 <span data-ttu-id="63d55-116">다음 표에서는 열거자의 값을 사용하여 설정한 패키지 속성에 해당하는 숫자 값 및 이름을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-116">The following tables lists the friendly names and the numeric value equivalents for properties of packages that you set by using values from an enumerator.</span></span>  
  
 <span data-ttu-id="63d55-117">`PackageType`속성-열거형의 값을 사용 하 여 설정 `DTSPackageType` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-117">`PackageType` property-Set by using values from the `DTSPackageType` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-118">DTSPackageType의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-118">Friendly name in DTSPackageType</span></span>|<span data-ttu-id="63d55-119">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-119">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="63d55-120">기본값</span><span class="sxs-lookup"><span data-stu-id="63d55-120">Default</span></span>|<span data-ttu-id="63d55-121">0</span><span class="sxs-lookup"><span data-stu-id="63d55-121">0</span></span>|  
|<span data-ttu-id="63d55-122">DTSWizard</span><span class="sxs-lookup"><span data-stu-id="63d55-122">DTSWizard</span></span>|<span data-ttu-id="63d55-123">1</span><span class="sxs-lookup"><span data-stu-id="63d55-123">1</span></span>|  
|<span data-ttu-id="63d55-124">DTSDesigner</span><span class="sxs-lookup"><span data-stu-id="63d55-124">DTSDesigner</span></span>|<span data-ttu-id="63d55-125">2</span><span class="sxs-lookup"><span data-stu-id="63d55-125">2</span></span>|  
|<span data-ttu-id="63d55-126">SQLReplication</span><span class="sxs-lookup"><span data-stu-id="63d55-126">SQLReplication</span></span>|<span data-ttu-id="63d55-127">3</span><span class="sxs-lookup"><span data-stu-id="63d55-127">3</span></span>|  
|<span data-ttu-id="63d55-128">DTSDesigner100</span><span class="sxs-lookup"><span data-stu-id="63d55-128">DTSDesigner100</span></span>|<span data-ttu-id="63d55-129">5</span><span class="sxs-lookup"><span data-stu-id="63d55-129">5</span></span>|  
|<span data-ttu-id="63d55-130">SQLDBMaint</span><span class="sxs-lookup"><span data-stu-id="63d55-130">SQLDBMaint</span></span>|<span data-ttu-id="63d55-131">6</span><span class="sxs-lookup"><span data-stu-id="63d55-131">6</span></span>|  
  
 <span data-ttu-id="63d55-132">`CheckpointUsage`속성-열거형의 값을 사용 하 여 설정 `DTSCheckpointUsage` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-132">`CheckpointUsage` property-Set by using values from the `DTSCheckpointUsage` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-133">DTSCheckpointUsage의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-133">Friendly name in DTSCheckpointUsage</span></span>|<span data-ttu-id="63d55-134">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-134">Numeric value</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="63d55-135">안 함</span><span class="sxs-lookup"><span data-stu-id="63d55-135">Never</span></span>|<span data-ttu-id="63d55-136">0</span><span class="sxs-lookup"><span data-stu-id="63d55-136">0</span></span>|  
|<span data-ttu-id="63d55-137">IfExists</span><span class="sxs-lookup"><span data-stu-id="63d55-137">IfExists</span></span>|<span data-ttu-id="63d55-138">1</span><span class="sxs-lookup"><span data-stu-id="63d55-138">1</span></span>|  
|<span data-ttu-id="63d55-139">항상</span><span class="sxs-lookup"><span data-stu-id="63d55-139">Always</span></span>|<span data-ttu-id="63d55-140">2</span><span class="sxs-lookup"><span data-stu-id="63d55-140">2</span></span>|  
  
 <span data-ttu-id="63d55-141">`PackagePriorityClass`속성-열거형의 값을 사용 하 여 설정 `DTSPriorityClass` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-141">`PackagePriorityClass` property-Set by using values from the `DTSPriorityClass` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-142">DTSPriorityClass의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-142">Friendly name in DTSPriorityClass</span></span>|<span data-ttu-id="63d55-143">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-143">Numeric value</span></span>|  
|---------------------------------------|-------------------|  
|<span data-ttu-id="63d55-144">기본값</span><span class="sxs-lookup"><span data-stu-id="63d55-144">Default</span></span>|<span data-ttu-id="63d55-145">0</span><span class="sxs-lookup"><span data-stu-id="63d55-145">0</span></span>|  
|<span data-ttu-id="63d55-146">AboveNormal</span><span class="sxs-lookup"><span data-stu-id="63d55-146">AboveNormal</span></span>|<span data-ttu-id="63d55-147">1</span><span class="sxs-lookup"><span data-stu-id="63d55-147">1</span></span>|  
|<span data-ttu-id="63d55-148">정상</span><span class="sxs-lookup"><span data-stu-id="63d55-148">Normal</span></span>|<span data-ttu-id="63d55-149">2</span><span class="sxs-lookup"><span data-stu-id="63d55-149">2</span></span>|  
|<span data-ttu-id="63d55-150">BelowNormal</span><span class="sxs-lookup"><span data-stu-id="63d55-150">BelowNormal</span></span>|<span data-ttu-id="63d55-151">3</span><span class="sxs-lookup"><span data-stu-id="63d55-151">3</span></span>|  
|<span data-ttu-id="63d55-152">유휴 상태</span><span class="sxs-lookup"><span data-stu-id="63d55-152">Idle</span></span>|<span data-ttu-id="63d55-153">4</span><span class="sxs-lookup"><span data-stu-id="63d55-153">4</span></span>|  
  
 <span data-ttu-id="63d55-154">`ProtectionLevel`속성-열거형의 값을 사용 하 여 설정 `DTSProtectionLevel` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-154">`ProtectionLevel` property-Set by using values from the `DTSProtectionLevel` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-155">DTSProtectionLevel의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-155">Friendly name in DTSProtectionLevel</span></span>|<span data-ttu-id="63d55-156">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-156">Numeric value</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="63d55-157">DontSaveSensitive</span><span class="sxs-lookup"><span data-stu-id="63d55-157">DontSaveSensitive</span></span>|<span data-ttu-id="63d55-158">0</span><span class="sxs-lookup"><span data-stu-id="63d55-158">0</span></span>|  
|<span data-ttu-id="63d55-159">EncryptSensitiveWithUserKey</span><span class="sxs-lookup"><span data-stu-id="63d55-159">EncryptSensitiveWithUserKey</span></span>|<span data-ttu-id="63d55-160">1</span><span class="sxs-lookup"><span data-stu-id="63d55-160">1</span></span>|  
|<span data-ttu-id="63d55-161">EncryptSensitiveWithPassword</span><span class="sxs-lookup"><span data-stu-id="63d55-161">EncryptSensitiveWithPassword</span></span>|<span data-ttu-id="63d55-162">2</span><span class="sxs-lookup"><span data-stu-id="63d55-162">2</span></span>|  
|<span data-ttu-id="63d55-163">EncryptAllWithPassword</span><span class="sxs-lookup"><span data-stu-id="63d55-163">EncryptAllWithPassword</span></span>|<span data-ttu-id="63d55-164">3</span><span class="sxs-lookup"><span data-stu-id="63d55-164">3</span></span>|  
|<span data-ttu-id="63d55-165">EncryptAllWithUserKey</span><span class="sxs-lookup"><span data-stu-id="63d55-165">EncryptAllWithUserKey</span></span>|<span data-ttu-id="63d55-166">4</span><span class="sxs-lookup"><span data-stu-id="63d55-166">4</span></span>|  
|<span data-ttu-id="63d55-167">ServerStorage</span><span class="sxs-lookup"><span data-stu-id="63d55-167">ServerStorage</span></span>|<span data-ttu-id="63d55-168">5</span><span class="sxs-lookup"><span data-stu-id="63d55-168">5</span></span>|  
  
##  <a name="precedence-constraints"></a><a name="PrecedenceConstraints"></a> <span data-ttu-id="63d55-169">선행 제약 조건</span><span class="sxs-lookup"><span data-stu-id="63d55-169">Precedence Constraints</span></span>  
 <span data-ttu-id="63d55-170">`EvalOp`속성-열거형의 값을 사용 하 여 설정 `DTSPrecedenceEvalOp` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-170">`EvalOp` property-Set by using values from the `DTSPrecedenceEvalOp` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-171">DTSPrecedenceEvalOp의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-171">Friendly name in DTSPrecedenceEvalOp</span></span>|<span data-ttu-id="63d55-172">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-172">Numeric value</span></span>|  
|------------------------------------------|-------------------|  
|<span data-ttu-id="63d55-173">식</span><span class="sxs-lookup"><span data-stu-id="63d55-173">Expression</span></span>|<span data-ttu-id="63d55-174">1</span><span class="sxs-lookup"><span data-stu-id="63d55-174">1</span></span>|  
|<span data-ttu-id="63d55-175">제약 조건</span><span class="sxs-lookup"><span data-stu-id="63d55-175">Constraint</span></span>|<span data-ttu-id="63d55-176">2</span><span class="sxs-lookup"><span data-stu-id="63d55-176">2</span></span>|  
|<span data-ttu-id="63d55-177">ExpressionAndConstraint</span><span class="sxs-lookup"><span data-stu-id="63d55-177">ExpressionAndConstraint</span></span>|<span data-ttu-id="63d55-178">3</span><span class="sxs-lookup"><span data-stu-id="63d55-178">3</span></span>|  
|<span data-ttu-id="63d55-179">ExpressionOrConstraint</span><span class="sxs-lookup"><span data-stu-id="63d55-179">ExpressionOrConstraint</span></span>|<span data-ttu-id="63d55-180">4</span><span class="sxs-lookup"><span data-stu-id="63d55-180">4</span></span>|  
  
 <span data-ttu-id="63d55-181">`Value`속성-열거형의 값을 사용 하 여 설정 `DTSExecResult` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-181">`Value` property-Set by using values from the `DTSExecResult` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-182">친숙한 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-182">Friendly Name</span></span>|<span data-ttu-id="63d55-183">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-183">Numeric Value</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="63d55-184">Success</span><span class="sxs-lookup"><span data-stu-id="63d55-184">Success</span></span>|<span data-ttu-id="63d55-185">0</span><span class="sxs-lookup"><span data-stu-id="63d55-185">0</span></span>|  
|<span data-ttu-id="63d55-186">실패</span><span class="sxs-lookup"><span data-stu-id="63d55-186">Failure</span></span>|<span data-ttu-id="63d55-187">1</span><span class="sxs-lookup"><span data-stu-id="63d55-187">1</span></span>|  
|<span data-ttu-id="63d55-188">Completion</span><span class="sxs-lookup"><span data-stu-id="63d55-188">Completion</span></span>|<span data-ttu-id="63d55-189">2</span><span class="sxs-lookup"><span data-stu-id="63d55-189">2</span></span>|  
|<span data-ttu-id="63d55-190">취소됨</span><span class="sxs-lookup"><span data-stu-id="63d55-190">Canceled</span></span>|<span data-ttu-id="63d55-191">3</span><span class="sxs-lookup"><span data-stu-id="63d55-191">3</span></span>|  
  
##  <a name="foreach-loop-enumerators"></a><a name="Foreach"></a> <span data-ttu-id="63d55-192">Foreach 루프 열거자</span><span class="sxs-lookup"><span data-stu-id="63d55-192">Foreach Loop Enumerators</span></span>  
 <span data-ttu-id="63d55-193">Foreach 루프에는 속성 식으로 설정할 수 있는 속성을 가지는 열거자 집합이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-193">The Foreach Loop includes a set of enumerators with properties that can be set by property expressions.</span></span>  
  
### <a name="foreach-ado-enumerator"></a><span data-ttu-id="63d55-194">Foreach ADO 열거자</span><span class="sxs-lookup"><span data-stu-id="63d55-194">Foreach ADO Enumerator</span></span>  
 <span data-ttu-id="63d55-195">`Type`속성-열거형의 값을 사용 하 여 설정 `ADOEnumerationType` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-195">`Type` property-Set by using values from the `ADOEnumerationType` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-196">ADOEnumerationType의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-196">Friendly name in ADOEnumerationType</span></span>|<span data-ttu-id="63d55-197">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-197">Numeric value</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="63d55-198">EnumerateTables</span><span class="sxs-lookup"><span data-stu-id="63d55-198">EnumerateTables</span></span>|<span data-ttu-id="63d55-199">0</span><span class="sxs-lookup"><span data-stu-id="63d55-199">0</span></span>|  
|<span data-ttu-id="63d55-200">EnumerateAllRows</span><span class="sxs-lookup"><span data-stu-id="63d55-200">EnumerateAllRows</span></span>|<span data-ttu-id="63d55-201">1</span><span class="sxs-lookup"><span data-stu-id="63d55-201">1</span></span>|  
|<span data-ttu-id="63d55-202">EnumerateRowsInFirstTable</span><span class="sxs-lookup"><span data-stu-id="63d55-202">EnumerateRowsInFirstTable</span></span>|<span data-ttu-id="63d55-203">2</span><span class="sxs-lookup"><span data-stu-id="63d55-203">2</span></span>|  
  
### <a name="foreach-nodelist-enumerator"></a><span data-ttu-id="63d55-204">Foreach Nodelist 열거자</span><span class="sxs-lookup"><span data-stu-id="63d55-204">Foreach Nodelist Enumerator</span></span>  
 <span data-ttu-id="63d55-205">`SourceDocumentType`, `InnerXPathStringSourceType` 및 **OuterXPathStringSourceType** 속성-열거형의 값을 사용 하 여 설정 `SourceType` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-205">`SourceDocumentType`, `InnerXPathStringSourceType`, and **OuterXPathStringSourceType** properties-Set by using values from the `SourceType` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-206">SourceType의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-206">Friendly name in SourceType</span></span>|<span data-ttu-id="63d55-207">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-207">Numeric value</span></span>|  
|---------------------------------|-------------------|  
|<span data-ttu-id="63d55-208">FileConnection</span><span class="sxs-lookup"><span data-stu-id="63d55-208">FileConnection</span></span>|<span data-ttu-id="63d55-209">0</span><span class="sxs-lookup"><span data-stu-id="63d55-209">0</span></span>|  
|<span data-ttu-id="63d55-210">변수</span><span class="sxs-lookup"><span data-stu-id="63d55-210">Variable</span></span>|<span data-ttu-id="63d55-211">1</span><span class="sxs-lookup"><span data-stu-id="63d55-211">1</span></span>|  
|<span data-ttu-id="63d55-212">DirectInput</span><span class="sxs-lookup"><span data-stu-id="63d55-212">DirectInput</span></span>|<span data-ttu-id="63d55-213">2</span><span class="sxs-lookup"><span data-stu-id="63d55-213">2</span></span>|  
  
 <span data-ttu-id="63d55-214">`EnumerationType`속성-열거형의 값을 사용 하 여 설정 `EnumerationType` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-214">`EnumerationType` property-Set by using values from the `EnumerationType` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-215">EnumerationType의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-215">Friendly name in EnumerationType</span></span>|<span data-ttu-id="63d55-216">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-216">Numeric value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="63d55-217">탐색기</span><span class="sxs-lookup"><span data-stu-id="63d55-217">Navigator</span></span>|<span data-ttu-id="63d55-218">0</span><span class="sxs-lookup"><span data-stu-id="63d55-218">0</span></span>|  
|<span data-ttu-id="63d55-219">노드</span><span class="sxs-lookup"><span data-stu-id="63d55-219">Node</span></span>|<span data-ttu-id="63d55-220">1</span><span class="sxs-lookup"><span data-stu-id="63d55-220">1</span></span>|  
|<span data-ttu-id="63d55-221">NodeText</span><span class="sxs-lookup"><span data-stu-id="63d55-221">NodeText</span></span>|<span data-ttu-id="63d55-222">2</span><span class="sxs-lookup"><span data-stu-id="63d55-222">2</span></span>|  
|<span data-ttu-id="63d55-223">ElementCollection</span><span class="sxs-lookup"><span data-stu-id="63d55-223">ElementCollection</span></span>|<span data-ttu-id="63d55-224">3</span><span class="sxs-lookup"><span data-stu-id="63d55-224">3</span></span>|  
  
 <span data-ttu-id="63d55-225">`InnerElementType`속성-열거형의 값을 사용 하 여 설정 `InnerElementType` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-225">`InnerElementType` property-Set by using values from the `InnerElementType` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-226">InnerElementType의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-226">Friendly name in InnerElementType</span></span>|<span data-ttu-id="63d55-227">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-227">Numeric value</span></span>|  
|---------------------------------------|-------------------|  
|<span data-ttu-id="63d55-228">탐색기</span><span class="sxs-lookup"><span data-stu-id="63d55-228">Navigator</span></span>|<span data-ttu-id="63d55-229">0</span><span class="sxs-lookup"><span data-stu-id="63d55-229">0</span></span>|  
|<span data-ttu-id="63d55-230">노드</span><span class="sxs-lookup"><span data-stu-id="63d55-230">Node</span></span>|<span data-ttu-id="63d55-231">1</span><span class="sxs-lookup"><span data-stu-id="63d55-231">1</span></span>|  
|<span data-ttu-id="63d55-232">NodeText</span><span class="sxs-lookup"><span data-stu-id="63d55-232">NodeText</span></span>|<span data-ttu-id="63d55-233">2</span><span class="sxs-lookup"><span data-stu-id="63d55-233">2</span></span>|  
  
##  <a name="tasks"></a><a name="Tasks"></a> <span data-ttu-id="63d55-234">작업</span><span class="sxs-lookup"><span data-stu-id="63d55-234">Tasks</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="63d55-235">에는 속성 식으로 설정할 수 있는 속성을 가지는 여러 태스크가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-235">includes numerous tasks with properties that can be set by property expressions.</span></span>  
  
### <a name="analysis-services-execute-ddl-task"></a><span data-ttu-id="63d55-236">Analysis Services DDL 실행 태스크</span><span class="sxs-lookup"><span data-stu-id="63d55-236">Analysis Services Execute DDL Task</span></span>  
 <span data-ttu-id="63d55-237">`SourceType`속성-열거형의 값을 사용 하 여 설정 `DDLSourceType` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-237">`SourceType` property-Set by using values from the `DDLSourceType` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-238">DDLSourceType의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-238">Friendly name in DDLSourceType</span></span>|<span data-ttu-id="63d55-239">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-239">Numeric value</span></span>|  
|------------------------------------|-------------------|  
|<span data-ttu-id="63d55-240">DirectInput</span><span class="sxs-lookup"><span data-stu-id="63d55-240">DirectInput</span></span>|<span data-ttu-id="63d55-241">0</span><span class="sxs-lookup"><span data-stu-id="63d55-241">0</span></span>|  
|<span data-ttu-id="63d55-242">FileConnection</span><span class="sxs-lookup"><span data-stu-id="63d55-242">FileConnection</span></span>|<span data-ttu-id="63d55-243">1</span><span class="sxs-lookup"><span data-stu-id="63d55-243">1</span></span>|  
|<span data-ttu-id="63d55-244">변수</span><span class="sxs-lookup"><span data-stu-id="63d55-244">Variable</span></span>|<span data-ttu-id="63d55-245">2</span><span class="sxs-lookup"><span data-stu-id="63d55-245">2</span></span>|  
  
### <a name="bulk-insert-task"></a><span data-ttu-id="63d55-246">대량 삽입 태스크</span><span class="sxs-lookup"><span data-stu-id="63d55-246">Bulk Insert Task</span></span>  
 <span data-ttu-id="63d55-247">`DataFileType`속성-열거형의 값을 사용 하 여 설정 `DTSBulkInsert_DataFileType` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-247">`DataFileType` property-Set by using values from the `DTSBulkInsert_DataFileType` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-248">DTSBulkInsert_DataFileType의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-248">Friendly name in DTSBulkInsert_DataFileType</span></span>|<span data-ttu-id="63d55-249">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-249">Numeric value</span></span>|  
|--------------------------------------------------|-------------------|  
|<span data-ttu-id="63d55-250">DTSBulkInsert_DataFileType_Char</span><span class="sxs-lookup"><span data-stu-id="63d55-250">DTSBulkInsert_DataFileType_Char</span></span>|<span data-ttu-id="63d55-251">0</span><span class="sxs-lookup"><span data-stu-id="63d55-251">0</span></span>|  
|<span data-ttu-id="63d55-252">DTSBulkInsert_DataFileType_Native</span><span class="sxs-lookup"><span data-stu-id="63d55-252">DTSBulkInsert_DataFileType_Native</span></span>|<span data-ttu-id="63d55-253">1</span><span class="sxs-lookup"><span data-stu-id="63d55-253">1</span></span>|  
|<span data-ttu-id="63d55-254">DTSBulkInsert_DataFileType_WideChar</span><span class="sxs-lookup"><span data-stu-id="63d55-254">DTSBulkInsert_DataFileType_WideChar</span></span>|<span data-ttu-id="63d55-255">2</span><span class="sxs-lookup"><span data-stu-id="63d55-255">2</span></span>|  
|<span data-ttu-id="63d55-256">DTSBulkInsert_DataFileType_WideNative</span><span class="sxs-lookup"><span data-stu-id="63d55-256">DTSBulkInsert_DataFileType_WideNative</span></span>|<span data-ttu-id="63d55-257">3</span><span class="sxs-lookup"><span data-stu-id="63d55-257">3</span></span>|  
  
### <a name="execute-sql-task"></a><span data-ttu-id="63d55-258">SQL 실행 태스크</span><span class="sxs-lookup"><span data-stu-id="63d55-258">Execute SQL Task</span></span>  
 <span data-ttu-id="63d55-259">`ResultSetType`속성-열거형의 값을 사용 하 여 설정 `ResultSetType` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-259">`ResultSetType` property-Set by using values from the `ResultSetType` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-260">ResultSetType의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-260">Friendly name in ResultSetType</span></span>|<span data-ttu-id="63d55-261">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-261">Numeric Value</span></span>|  
|------------------------------------|-------------------|  
|<span data-ttu-id="63d55-262">ResultSetType_None</span><span class="sxs-lookup"><span data-stu-id="63d55-262">ResultSetType_None</span></span>|<span data-ttu-id="63d55-263">1</span><span class="sxs-lookup"><span data-stu-id="63d55-263">1</span></span>|  
|<span data-ttu-id="63d55-264">ResultSetType_SingleRow</span><span class="sxs-lookup"><span data-stu-id="63d55-264">ResultSetType_SingleRow</span></span>|<span data-ttu-id="63d55-265">2</span><span class="sxs-lookup"><span data-stu-id="63d55-265">2</span></span>|  
|<span data-ttu-id="63d55-266">ResultSetType_Rowset</span><span class="sxs-lookup"><span data-stu-id="63d55-266">ResultSetType_Rowset</span></span>|<span data-ttu-id="63d55-267">3</span><span class="sxs-lookup"><span data-stu-id="63d55-267">3</span></span>|  
|<span data-ttu-id="63d55-268">ResultSetType_XML</span><span class="sxs-lookup"><span data-stu-id="63d55-268">ResultSetType_XML</span></span>|<span data-ttu-id="63d55-269">4</span><span class="sxs-lookup"><span data-stu-id="63d55-269">4</span></span>|  
  
 <span data-ttu-id="63d55-270">`SqlStatementSourceType`속성-열거형의 값을 사용 하 여 설정 `SqlStatementSourceType` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-270">`SqlStatementSourceType` property-Set by using values from the `SqlStatementSourceType` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-271">SqlStatementSourceType의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-271">Friendly name in SqlStatementSourceType</span></span>|<span data-ttu-id="63d55-272">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-272">Numeric Value</span></span>|  
|---------------------------------------------|-------------------|  
|<span data-ttu-id="63d55-273">DirectInput</span><span class="sxs-lookup"><span data-stu-id="63d55-273">DirectInput</span></span>|<span data-ttu-id="63d55-274">1</span><span class="sxs-lookup"><span data-stu-id="63d55-274">1</span></span>|  
|<span data-ttu-id="63d55-275">FileConnection</span><span class="sxs-lookup"><span data-stu-id="63d55-275">FileConnection</span></span>|<span data-ttu-id="63d55-276">2</span><span class="sxs-lookup"><span data-stu-id="63d55-276">2</span></span>|  
|<span data-ttu-id="63d55-277">변수</span><span class="sxs-lookup"><span data-stu-id="63d55-277">Variable</span></span>|<span data-ttu-id="63d55-278">3</span><span class="sxs-lookup"><span data-stu-id="63d55-278">3</span></span>|  
  
### <a name="file-system-task"></a><span data-ttu-id="63d55-279">파일 시스템 태스크</span><span class="sxs-lookup"><span data-stu-id="63d55-279">File System Task</span></span>  
 <span data-ttu-id="63d55-280">`Operation`속성-열거형의 값을 사용 하 여 설정 `DTSFileSystemOperation` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-280">`Operation` property-Set by using values from the `DTSFileSystemOperation` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-281">DTSFileSystemOperation의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-281">Friendly name in DTSFileSystemOperation</span></span>|<span data-ttu-id="63d55-282">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-282">Numeric value</span></span>|  
|---------------------------------------------|-------------------|  
|<span data-ttu-id="63d55-283">CopyFile</span><span class="sxs-lookup"><span data-stu-id="63d55-283">CopyFile</span></span>|<span data-ttu-id="63d55-284">0</span><span class="sxs-lookup"><span data-stu-id="63d55-284">0</span></span>|  
|<span data-ttu-id="63d55-285">MoveFile</span><span class="sxs-lookup"><span data-stu-id="63d55-285">MoveFile</span></span>|<span data-ttu-id="63d55-286">1</span><span class="sxs-lookup"><span data-stu-id="63d55-286">1</span></span>|  
|<span data-ttu-id="63d55-287">DeleteFile</span><span class="sxs-lookup"><span data-stu-id="63d55-287">DeleteFile</span></span>|<span data-ttu-id="63d55-288">2</span><span class="sxs-lookup"><span data-stu-id="63d55-288">2</span></span>|  
|<span data-ttu-id="63d55-289">RenameFile</span><span class="sxs-lookup"><span data-stu-id="63d55-289">RenameFile</span></span>|<span data-ttu-id="63d55-290">3</span><span class="sxs-lookup"><span data-stu-id="63d55-290">3</span></span>|  
|<span data-ttu-id="63d55-291">SetAttributes</span><span class="sxs-lookup"><span data-stu-id="63d55-291">SetAttributes</span></span>|<span data-ttu-id="63d55-292">4</span><span class="sxs-lookup"><span data-stu-id="63d55-292">4</span></span>|  
|<span data-ttu-id="63d55-293">CreateDirectory</span><span class="sxs-lookup"><span data-stu-id="63d55-293">CreateDirectory</span></span>|<span data-ttu-id="63d55-294">5</span><span class="sxs-lookup"><span data-stu-id="63d55-294">5</span></span>|  
|<span data-ttu-id="63d55-295">CopyDirectory</span><span class="sxs-lookup"><span data-stu-id="63d55-295">CopyDirectory</span></span>|<span data-ttu-id="63d55-296">6</span><span class="sxs-lookup"><span data-stu-id="63d55-296">6</span></span>|  
|<span data-ttu-id="63d55-297">MoveDirectory</span><span class="sxs-lookup"><span data-stu-id="63d55-297">MoveDirectory</span></span>|<span data-ttu-id="63d55-298">7</span><span class="sxs-lookup"><span data-stu-id="63d55-298">7</span></span>|  
|<span data-ttu-id="63d55-299">DeleteDirectory</span><span class="sxs-lookup"><span data-stu-id="63d55-299">DeleteDirectory</span></span>|<span data-ttu-id="63d55-300">8</span><span class="sxs-lookup"><span data-stu-id="63d55-300">8</span></span>|  
|<span data-ttu-id="63d55-301">DeleteDirectoryContent</span><span class="sxs-lookup"><span data-stu-id="63d55-301">DeleteDirectoryContent</span></span>|<span data-ttu-id="63d55-302">9</span><span class="sxs-lookup"><span data-stu-id="63d55-302">9</span></span>|  
  
 <span data-ttu-id="63d55-303">`Attributes`속성-열거형의 값을 사용 하 여 설정 `DTSFileSystemAttributes` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-303">`Attributes` property-Set by using values from the `DTSFileSystemAttributes` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-304">DTSFileSystemAttributes의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-304">Friendly name in DTSFileSystemAttributes</span></span>|<span data-ttu-id="63d55-305">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-305">Numeric value</span></span>|  
|----------------------------------------------|-------------------|  
|<span data-ttu-id="63d55-306">정상</span><span class="sxs-lookup"><span data-stu-id="63d55-306">Normal</span></span>|<span data-ttu-id="63d55-307">0</span><span class="sxs-lookup"><span data-stu-id="63d55-307">0</span></span>|  
|<span data-ttu-id="63d55-308">보관</span><span class="sxs-lookup"><span data-stu-id="63d55-308">Archive</span></span>|<span data-ttu-id="63d55-309">1</span><span class="sxs-lookup"><span data-stu-id="63d55-309">1</span></span>|  
|<span data-ttu-id="63d55-310">숨김</span><span class="sxs-lookup"><span data-stu-id="63d55-310">Hidden</span></span>|<span data-ttu-id="63d55-311">2</span><span class="sxs-lookup"><span data-stu-id="63d55-311">2</span></span>|  
|<span data-ttu-id="63d55-312">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="63d55-312">ReadOnly</span></span>|<span data-ttu-id="63d55-313">4</span><span class="sxs-lookup"><span data-stu-id="63d55-313">4</span></span>|  
|<span data-ttu-id="63d55-314">시스템</span><span class="sxs-lookup"><span data-stu-id="63d55-314">System</span></span>|<span data-ttu-id="63d55-315">8</span><span class="sxs-lookup"><span data-stu-id="63d55-315">8</span></span>|  
  
### <a name="ftp-task"></a><span data-ttu-id="63d55-316">FTP 태스크</span><span class="sxs-lookup"><span data-stu-id="63d55-316">FTP Task</span></span>  
 <span data-ttu-id="63d55-317">`Operation`속성-열거형의 값을 사용 하 여 설정 `DTSFTPOp` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-317">`Operation` property-Set by using values from the `DTSFTPOp` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-318">DTSFTPOp의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-318">Friendly name in DTSFTPOp</span></span>|<span data-ttu-id="63d55-319">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-319">Numeric value</span></span>|  
|-------------------------------|-------------------|  
|<span data-ttu-id="63d55-320">보내기</span><span class="sxs-lookup"><span data-stu-id="63d55-320">Send</span></span>|<span data-ttu-id="63d55-321">0</span><span class="sxs-lookup"><span data-stu-id="63d55-321">0</span></span>|  
|<span data-ttu-id="63d55-322">수신</span><span class="sxs-lookup"><span data-stu-id="63d55-322">Receive</span></span>|<span data-ttu-id="63d55-323">1</span><span class="sxs-lookup"><span data-stu-id="63d55-323">1</span></span>|  
|<span data-ttu-id="63d55-324">DeleteLocal</span><span class="sxs-lookup"><span data-stu-id="63d55-324">DeleteLocal</span></span>|<span data-ttu-id="63d55-325">2</span><span class="sxs-lookup"><span data-stu-id="63d55-325">2</span></span>|  
|<span data-ttu-id="63d55-326">DeleteRemote</span><span class="sxs-lookup"><span data-stu-id="63d55-326">DeleteRemote</span></span>|<span data-ttu-id="63d55-327">3</span><span class="sxs-lookup"><span data-stu-id="63d55-327">3</span></span>|  
|<span data-ttu-id="63d55-328">MakeDirLocal</span><span class="sxs-lookup"><span data-stu-id="63d55-328">MakeDirLocal</span></span>|<span data-ttu-id="63d55-329">4</span><span class="sxs-lookup"><span data-stu-id="63d55-329">4</span></span>|  
|<span data-ttu-id="63d55-330">MakeDirRemote</span><span class="sxs-lookup"><span data-stu-id="63d55-330">MakeDirRemote</span></span>|<span data-ttu-id="63d55-331">5</span><span class="sxs-lookup"><span data-stu-id="63d55-331">5</span></span>|  
|<span data-ttu-id="63d55-332">RemoveDirLocal</span><span class="sxs-lookup"><span data-stu-id="63d55-332">RemoveDirLocal</span></span>|<span data-ttu-id="63d55-333">6</span><span class="sxs-lookup"><span data-stu-id="63d55-333">6</span></span>|  
|<span data-ttu-id="63d55-334">RemoveDirRemote</span><span class="sxs-lookup"><span data-stu-id="63d55-334">RemoveDirRemote</span></span>|<span data-ttu-id="63d55-335">7</span><span class="sxs-lookup"><span data-stu-id="63d55-335">7</span></span>|  
  
### <a name="message-queue-task"></a><span data-ttu-id="63d55-336">Message Queue Task</span><span class="sxs-lookup"><span data-stu-id="63d55-336">Message Queue Task</span></span>  
 <span data-ttu-id="63d55-337">`MessageType`속성-열거형의 값을 사용 하 여 설정 `MQMessageType` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-337">`MessageType` property-Set by using values from the `MQMessageType` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-338">MQMessageType의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-338">Friendly name in MQMessageType</span></span>|<span data-ttu-id="63d55-339">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-339">Numeric value</span></span>|  
|------------------------------------|-------------------|  
|<span data-ttu-id="63d55-340">DTSMQMessageType_String</span><span class="sxs-lookup"><span data-stu-id="63d55-340">DTSMQMessageType_String</span></span>|<span data-ttu-id="63d55-341">0</span><span class="sxs-lookup"><span data-stu-id="63d55-341">0</span></span>|  
|<span data-ttu-id="63d55-342">DTSMQMessageType_DataFile</span><span class="sxs-lookup"><span data-stu-id="63d55-342">DTSMQMessageType_DataFile</span></span>|<span data-ttu-id="63d55-343">1</span><span class="sxs-lookup"><span data-stu-id="63d55-343">1</span></span>|  
|<span data-ttu-id="63d55-344">DTSMQMessageType_Variables</span><span class="sxs-lookup"><span data-stu-id="63d55-344">DTSMQMessageType_Variables</span></span>|<span data-ttu-id="63d55-345">2</span><span class="sxs-lookup"><span data-stu-id="63d55-345">2</span></span>|  
|<span data-ttu-id="63d55-346">DTSMQMessagType_StringMessageToVariable</span><span class="sxs-lookup"><span data-stu-id="63d55-346">DTSMQMessagType_StringMessageToVariable</span></span>|<span data-ttu-id="63d55-347">3</span><span class="sxs-lookup"><span data-stu-id="63d55-347">3</span></span>|  
  
 <span data-ttu-id="63d55-348">`StringCompareType`속성-열거형의 값을 사용 하 여 설정 `MQStringMessageCompare` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-348">`StringCompareType` property-Set by using values from the `MQStringMessageCompare` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-349">MQStringMessageCompare의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-349">Friendly name in MQStringMessageCompare</span></span>|<span data-ttu-id="63d55-350">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-350">Numeric value</span></span>|  
|---------------------------------------------|-------------------|  
|<span data-ttu-id="63d55-351">DTSMQStringMessageCompare_None</span><span class="sxs-lookup"><span data-stu-id="63d55-351">DTSMQStringMessageCompare_None</span></span>|<span data-ttu-id="63d55-352">0</span><span class="sxs-lookup"><span data-stu-id="63d55-352">0</span></span>|  
|<span data-ttu-id="63d55-353">DTSMQStringMessageCompare_Exact</span><span class="sxs-lookup"><span data-stu-id="63d55-353">DTSMQStringMessageCompare_Exact</span></span>|<span data-ttu-id="63d55-354">1</span><span class="sxs-lookup"><span data-stu-id="63d55-354">1</span></span>|  
|<span data-ttu-id="63d55-355">DTSMQStringMessageCompare_IgnoreCase</span><span class="sxs-lookup"><span data-stu-id="63d55-355">DTSMQStringMessageCompare_IgnoreCase</span></span>|<span data-ttu-id="63d55-356">2</span><span class="sxs-lookup"><span data-stu-id="63d55-356">2</span></span>|  
|<span data-ttu-id="63d55-357">DTSMQStringMessageCompare_Contains</span><span class="sxs-lookup"><span data-stu-id="63d55-357">DTSMQStringMessageCompare_Contains</span></span>|<span data-ttu-id="63d55-358">3</span><span class="sxs-lookup"><span data-stu-id="63d55-358">3</span></span>|  
  
 <span data-ttu-id="63d55-359">`TaskType`속성-열거형의 값을 사용 하 여 설정 `MQType` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-359">`TaskType` property-Set by using values from the `MQType` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-360">MQType의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-360">Friendly name in MQType</span></span>|<span data-ttu-id="63d55-361">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-361">Numeric value</span></span>|  
|-----------------------------|-------------------|  
|<span data-ttu-id="63d55-362">DTSMQType_Sender</span><span class="sxs-lookup"><span data-stu-id="63d55-362">DTSMQType_Sender</span></span>|<span data-ttu-id="63d55-363">0</span><span class="sxs-lookup"><span data-stu-id="63d55-363">0</span></span>|  
|<span data-ttu-id="63d55-364">DTSMQType_Receiver</span><span class="sxs-lookup"><span data-stu-id="63d55-364">DTSMQType_Receiver</span></span>|<span data-ttu-id="63d55-365">1</span><span class="sxs-lookup"><span data-stu-id="63d55-365">1</span></span>|  
  
### <a name="send-mail-task"></a><span data-ttu-id="63d55-366">메일 보내기 태스크</span><span class="sxs-lookup"><span data-stu-id="63d55-366">Send Mail Task</span></span>  
 <span data-ttu-id="63d55-367">`MessageSourceType`속성-열거형의 값을 사용 하 여 설정 `SendMailMessageSourceType` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-367">`MessageSourceType` property-Set by using values from the `SendMailMessageSourceType` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-368">SendMailMessageSourceType의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-368">Friendly Name in SendMailMessageSourceType</span></span>|<span data-ttu-id="63d55-369">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-369">Numeric Value</span></span>|  
|------------------------------------------------|-------------------|  
|<span data-ttu-id="63d55-370">DirectInput</span><span class="sxs-lookup"><span data-stu-id="63d55-370">DirectInput</span></span>|<span data-ttu-id="63d55-371">0</span><span class="sxs-lookup"><span data-stu-id="63d55-371">0</span></span>|  
|<span data-ttu-id="63d55-372">FileConnection</span><span class="sxs-lookup"><span data-stu-id="63d55-372">FileConnection</span></span>|<span data-ttu-id="63d55-373">1</span><span class="sxs-lookup"><span data-stu-id="63d55-373">1</span></span>|  
|<span data-ttu-id="63d55-374">변수</span><span class="sxs-lookup"><span data-stu-id="63d55-374">Variable</span></span>|<span data-ttu-id="63d55-375">2</span><span class="sxs-lookup"><span data-stu-id="63d55-375">2</span></span>|  
  
 <span data-ttu-id="63d55-376">`Priority`속성-열거형의 값을 사용 하 여 설정 `MailPriority` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-376">`Priority` property-Set by using values from the `MailPriority` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-377">MailPriority의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-377">Friendly Name in MailPriority</span></span>|<span data-ttu-id="63d55-378">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-378">Numeric Value</span></span>|  
|-----------------------------------|-------------------|  
|<span data-ttu-id="63d55-379">높음</span><span class="sxs-lookup"><span data-stu-id="63d55-379">High</span></span>|<span data-ttu-id="63d55-380">1</span><span class="sxs-lookup"><span data-stu-id="63d55-380">1</span></span>|  
|<span data-ttu-id="63d55-381">정상</span><span class="sxs-lookup"><span data-stu-id="63d55-381">Normal</span></span>|<span data-ttu-id="63d55-382">3</span><span class="sxs-lookup"><span data-stu-id="63d55-382">3</span></span>|  
|<span data-ttu-id="63d55-383">낮음</span><span class="sxs-lookup"><span data-stu-id="63d55-383">Low</span></span>|<span data-ttu-id="63d55-384">5</span><span class="sxs-lookup"><span data-stu-id="63d55-384">5</span></span>|  
  
### <a name="transfer-database-task"></a><span data-ttu-id="63d55-385">데이터베이스 전송 태스크</span><span class="sxs-lookup"><span data-stu-id="63d55-385">Transfer Database Task</span></span>  
 <span data-ttu-id="63d55-386">`Action`속성-열거형의 값을 사용 하 여 설정 `TransferAction` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-386">`Action` property-Set by using values from the `TransferAction` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-387">TransferAction의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-387">Friendly name in TransferAction</span></span>|<span data-ttu-id="63d55-388">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-388">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="63d55-389">복사</span><span class="sxs-lookup"><span data-stu-id="63d55-389">Copy</span></span>|<span data-ttu-id="63d55-390">0</span><span class="sxs-lookup"><span data-stu-id="63d55-390">0</span></span>|  
|<span data-ttu-id="63d55-391">이동</span><span class="sxs-lookup"><span data-stu-id="63d55-391">Move</span></span>|<span data-ttu-id="63d55-392">1</span><span class="sxs-lookup"><span data-stu-id="63d55-392">1</span></span>|  
  
 <span data-ttu-id="63d55-393">`Method`속성-열거형의 값을 사용 하 여 설정 `TransferMethod` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-393">`Method` property-Set by using values from the `TransferMethod` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-394">TransferMethod의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-394">Friendly name in TransferMethod</span></span>|<span data-ttu-id="63d55-395">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-395">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="63d55-396">DatabaseOffline</span><span class="sxs-lookup"><span data-stu-id="63d55-396">DatabaseOffline</span></span>|<span data-ttu-id="63d55-397">0</span><span class="sxs-lookup"><span data-stu-id="63d55-397">0</span></span>|  
|<span data-ttu-id="63d55-398">DatabaseOnline</span><span class="sxs-lookup"><span data-stu-id="63d55-398">DatabaseOnline</span></span>|<span data-ttu-id="63d55-399">1</span><span class="sxs-lookup"><span data-stu-id="63d55-399">1</span></span>|  
  
### <a name="transfer-error-messages-task"></a><span data-ttu-id="63d55-400">오류 메시지 전송 태스크</span><span class="sxs-lookup"><span data-stu-id="63d55-400">Transfer Error Messages Task</span></span>  
 <span data-ttu-id="63d55-401">`IfObjectExists`속성-열거형의 값을 사용 하 여 설정 `IfObjectExists` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-401">`IfObjectExists` property-Set by using values from the `IfObjectExists` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-402">IfObjectExists의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-402">Friendly Name in IfObjectExists</span></span>|<span data-ttu-id="63d55-403">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-403">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="63d55-404">FailTask</span><span class="sxs-lookup"><span data-stu-id="63d55-404">FailTask</span></span>|<span data-ttu-id="63d55-405">0</span><span class="sxs-lookup"><span data-stu-id="63d55-405">0</span></span>|  
|<span data-ttu-id="63d55-406">Overwrite</span><span class="sxs-lookup"><span data-stu-id="63d55-406">Overwrite</span></span>|<span data-ttu-id="63d55-407">1</span><span class="sxs-lookup"><span data-stu-id="63d55-407">1</span></span>|  
|<span data-ttu-id="63d55-408">Skip</span><span class="sxs-lookup"><span data-stu-id="63d55-408">Skip</span></span>|<span data-ttu-id="63d55-409">2</span><span class="sxs-lookup"><span data-stu-id="63d55-409">2</span></span>|  
  
### <a name="transfer-jobs-task"></a><span data-ttu-id="63d55-410">작업 전송 태스크</span><span class="sxs-lookup"><span data-stu-id="63d55-410">Transfer Jobs Task</span></span>  
 <span data-ttu-id="63d55-411">`IfObjectExists`속성-열거형의 값을 사용 하 여 설정 `IfObjectExists` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-411">`IfObjectExists` property-Set by using values from the `IfObjectExists` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-412">IfObjectExists의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-412">Friendly Name in IfObjectExists</span></span>|<span data-ttu-id="63d55-413">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-413">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="63d55-414">FailTask</span><span class="sxs-lookup"><span data-stu-id="63d55-414">FailTask</span></span>|<span data-ttu-id="63d55-415">0</span><span class="sxs-lookup"><span data-stu-id="63d55-415">0</span></span>|  
|<span data-ttu-id="63d55-416">Overwrite</span><span class="sxs-lookup"><span data-stu-id="63d55-416">Overwrite</span></span>|<span data-ttu-id="63d55-417">1</span><span class="sxs-lookup"><span data-stu-id="63d55-417">1</span></span>|  
|<span data-ttu-id="63d55-418">Skip</span><span class="sxs-lookup"><span data-stu-id="63d55-418">Skip</span></span>|<span data-ttu-id="63d55-419">2</span><span class="sxs-lookup"><span data-stu-id="63d55-419">2</span></span>|  
  
### <a name="transfer-logins-task"></a><span data-ttu-id="63d55-420">로그인 전송 태스크</span><span class="sxs-lookup"><span data-stu-id="63d55-420">Transfer Logins Task</span></span>  
 <span data-ttu-id="63d55-421">`IfObjectExists`속성-열거형의 값을 사용 하 여 설정 `IfObjectExists` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-421">`IfObjectExists` property-Set by using values from the `IfObjectExists` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-422">IfObjectExists의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-422">Friendly name in IfObjectExists</span></span>|<span data-ttu-id="63d55-423">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-423">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="63d55-424">FailTask</span><span class="sxs-lookup"><span data-stu-id="63d55-424">FailTask</span></span>|<span data-ttu-id="63d55-425">0</span><span class="sxs-lookup"><span data-stu-id="63d55-425">0</span></span>|  
|<span data-ttu-id="63d55-426">Overwrite</span><span class="sxs-lookup"><span data-stu-id="63d55-426">Overwrite</span></span>|<span data-ttu-id="63d55-427">1</span><span class="sxs-lookup"><span data-stu-id="63d55-427">1</span></span>|  
|<span data-ttu-id="63d55-428">Skip</span><span class="sxs-lookup"><span data-stu-id="63d55-428">Skip</span></span>|<span data-ttu-id="63d55-429">2</span><span class="sxs-lookup"><span data-stu-id="63d55-429">2</span></span>|  
  
 <span data-ttu-id="63d55-430">`LoginsToTransfer`속성-열거형의 값을 사용 하 여 설정 `LoginsToTransfer` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-430">`LoginsToTransfer` property-Set by using values from the `LoginsToTransfer` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-431">LoginsToTransfer의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-431">Friendly name in LoginsToTransfer</span></span>|<span data-ttu-id="63d55-432">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-432">Numeric value</span></span>|  
|---------------------------------------|-------------------|  
|<span data-ttu-id="63d55-433">AllLogins</span><span class="sxs-lookup"><span data-stu-id="63d55-433">AllLogins</span></span>|<span data-ttu-id="63d55-434">0</span><span class="sxs-lookup"><span data-stu-id="63d55-434">0</span></span>|  
|<span data-ttu-id="63d55-435">SelectedLogins</span><span class="sxs-lookup"><span data-stu-id="63d55-435">SelectedLogins</span></span>|<span data-ttu-id="63d55-436">1</span><span class="sxs-lookup"><span data-stu-id="63d55-436">1</span></span>|  
|<span data-ttu-id="63d55-437">AllLoginsFromSelectedDatabases</span><span class="sxs-lookup"><span data-stu-id="63d55-437">AllLoginsFromSelectedDatabases</span></span>|<span data-ttu-id="63d55-438">2</span><span class="sxs-lookup"><span data-stu-id="63d55-438">2</span></span>|  
  
### <a name="transfer-master-stored-procedures-task"></a><span data-ttu-id="63d55-439">Master 저장 프로시저 전송 태스크</span><span class="sxs-lookup"><span data-stu-id="63d55-439">Transfer Master Stored Procedures Task</span></span>  
 <span data-ttu-id="63d55-440">`IfObjectExists`속성-열거형의 값을 사용 하 여 설정 `IfObjectExists` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-440">`IfObjectExists` property-Set by using values from the `IfObjectExists` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-441">IfObjectExists의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-441">Friendly name in IfObjectExists</span></span>|<span data-ttu-id="63d55-442">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-442">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="63d55-443">FailTask</span><span class="sxs-lookup"><span data-stu-id="63d55-443">FailTask</span></span>|<span data-ttu-id="63d55-444">0</span><span class="sxs-lookup"><span data-stu-id="63d55-444">0</span></span>|  
|<span data-ttu-id="63d55-445">Overwrite</span><span class="sxs-lookup"><span data-stu-id="63d55-445">Overwrite</span></span>|<span data-ttu-id="63d55-446">1</span><span class="sxs-lookup"><span data-stu-id="63d55-446">1</span></span>|  
|<span data-ttu-id="63d55-447">Skip</span><span class="sxs-lookup"><span data-stu-id="63d55-447">Skip</span></span>|<span data-ttu-id="63d55-448">2</span><span class="sxs-lookup"><span data-stu-id="63d55-448">2</span></span>|  
  
### <a name="transfer-sql-server-objects-task"></a><span data-ttu-id="63d55-449">SQL Server 개체 전송 태스크</span><span class="sxs-lookup"><span data-stu-id="63d55-449">Transfer SQL Server Objects Task</span></span>  
 <span data-ttu-id="63d55-450">`ExistingData`속성-열거형의 값을 사용 하 여 설정 `ExistingData` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-450">`ExistingData` property-Set by using values from the `ExistingData` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-451">ExistingData의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-451">Friendly name in ExistingData</span></span>|<span data-ttu-id="63d55-452">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-452">Numeric Value</span></span>|  
|-----------------------------------|-------------------|  
|<span data-ttu-id="63d55-453">Replace</span><span class="sxs-lookup"><span data-stu-id="63d55-453">Replace</span></span>|<span data-ttu-id="63d55-454">0</span><span class="sxs-lookup"><span data-stu-id="63d55-454">0</span></span>|  
|<span data-ttu-id="63d55-455">추가</span><span class="sxs-lookup"><span data-stu-id="63d55-455">Append</span></span>|<span data-ttu-id="63d55-456">1</span><span class="sxs-lookup"><span data-stu-id="63d55-456">1</span></span>|  
  
### <a name="web-service-task"></a><span data-ttu-id="63d55-457">웹 서비스 태스크</span><span class="sxs-lookup"><span data-stu-id="63d55-457">Web Service Task</span></span>  
 <span data-ttu-id="63d55-458">`OutputType`속성-열거형의 값을 사용 하 여 설정 `DTSOutputType` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-458">`OutputType` property-Set by using values from the `DTSOutputType` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-459">DTSOutputType의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-459">Friendly name in DTSOutputType</span></span>|<span data-ttu-id="63d55-460">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-460">Numeric value</span></span>|  
|------------------------------------|-------------------|  
|<span data-ttu-id="63d55-461">파일</span><span class="sxs-lookup"><span data-stu-id="63d55-461">File</span></span>|<span data-ttu-id="63d55-462">0</span><span class="sxs-lookup"><span data-stu-id="63d55-462">0</span></span>|  
|<span data-ttu-id="63d55-463">변수</span><span class="sxs-lookup"><span data-stu-id="63d55-463">Variable</span></span>|<span data-ttu-id="63d55-464">1</span><span class="sxs-lookup"><span data-stu-id="63d55-464">1</span></span>|  
  
### <a name="wmi-data-reader-task"></a><span data-ttu-id="63d55-465">WMI 데이터 판독기 태스크</span><span class="sxs-lookup"><span data-stu-id="63d55-465">WMI Data Reader Task</span></span>  
 <span data-ttu-id="63d55-466">`OverwriteDestination`속성-열거형의 값을 사용 하 여 설정 `OverwriteDestination` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-466">`OverwriteDestination` property-Set by using values from the `OverwriteDestination` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-467">OverwriteDestination의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-467">Friendly name in OverwriteDestination</span></span>|<span data-ttu-id="63d55-468">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-468">Numeric value</span></span>|  
|-------------------------------------------|-------------------|  
|<span data-ttu-id="63d55-469">OverwriteDestination</span><span class="sxs-lookup"><span data-stu-id="63d55-469">OverwriteDestination</span></span>|<span data-ttu-id="63d55-470">0</span><span class="sxs-lookup"><span data-stu-id="63d55-470">0</span></span>|  
|<span data-ttu-id="63d55-471">AppendToDestination</span><span class="sxs-lookup"><span data-stu-id="63d55-471">AppendToDestination</span></span>|<span data-ttu-id="63d55-472">1</span><span class="sxs-lookup"><span data-stu-id="63d55-472">1</span></span>|  
|<span data-ttu-id="63d55-473">KeepOriginal</span><span class="sxs-lookup"><span data-stu-id="63d55-473">KeepOriginal</span></span>|<span data-ttu-id="63d55-474">2</span><span class="sxs-lookup"><span data-stu-id="63d55-474">2</span></span>|  
  
 <span data-ttu-id="63d55-475">`OutputType`속성-열거형의 값을 사용 하 여 설정 `OutputType` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-475">`OutputType` property-Set by using values from the `OutputType` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-476">OutputType의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-476">Friendly name in OutputType</span></span>|<span data-ttu-id="63d55-477">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-477">Numeric value</span></span>|  
|---------------------------------|-------------------|  
|<span data-ttu-id="63d55-478">DataTable</span><span class="sxs-lookup"><span data-stu-id="63d55-478">DataTable</span></span>|<span data-ttu-id="63d55-479">0</span><span class="sxs-lookup"><span data-stu-id="63d55-479">0</span></span>|  
|<span data-ttu-id="63d55-480">PropertyValue</span><span class="sxs-lookup"><span data-stu-id="63d55-480">PropertyValue</span></span>|<span data-ttu-id="63d55-481">1</span><span class="sxs-lookup"><span data-stu-id="63d55-481">1</span></span>|  
|<span data-ttu-id="63d55-482">PropertyNameAndValue</span><span class="sxs-lookup"><span data-stu-id="63d55-482">PropertyNameAndValue</span></span>|<span data-ttu-id="63d55-483">2</span><span class="sxs-lookup"><span data-stu-id="63d55-483">2</span></span>|  
  
 <span data-ttu-id="63d55-484">`DestinationType`속성-열거형의 값을 사용 하 여 설정 `DestinationType` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-484">`DestinationType` property-Set by using values from the `DestinationType` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-485">DestinationType의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-485">Friendly name in DestinationType</span></span>|<span data-ttu-id="63d55-486">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-486">Numeric value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="63d55-487">FileConnection</span><span class="sxs-lookup"><span data-stu-id="63d55-487">FileConnection</span></span>|<span data-ttu-id="63d55-488">0</span><span class="sxs-lookup"><span data-stu-id="63d55-488">0</span></span>|  
|<span data-ttu-id="63d55-489">변수</span><span class="sxs-lookup"><span data-stu-id="63d55-489">Variable</span></span>|<span data-ttu-id="63d55-490">1</span><span class="sxs-lookup"><span data-stu-id="63d55-490">1</span></span>|  
  
 <span data-ttu-id="63d55-491">`WqlQuerySourceType`속성-열거형의 값을 사용 하 여 설정 `QuerySourceType` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-491">`WqlQuerySourceType` property-Set by using values from the `QuerySourceType` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-492">QuerySourceType의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-492">Friendly Name in QuerySourceType</span></span>|<span data-ttu-id="63d55-493">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-493">Numeric Value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="63d55-494">FileConnection</span><span class="sxs-lookup"><span data-stu-id="63d55-494">FileConnection</span></span>|<span data-ttu-id="63d55-495">0</span><span class="sxs-lookup"><span data-stu-id="63d55-495">0</span></span>|  
|<span data-ttu-id="63d55-496">DirectInput</span><span class="sxs-lookup"><span data-stu-id="63d55-496">DirectInput</span></span>|<span data-ttu-id="63d55-497">1</span><span class="sxs-lookup"><span data-stu-id="63d55-497">1</span></span>|  
|<span data-ttu-id="63d55-498">변수</span><span class="sxs-lookup"><span data-stu-id="63d55-498">Variable</span></span>|<span data-ttu-id="63d55-499">2</span><span class="sxs-lookup"><span data-stu-id="63d55-499">2</span></span>|  
  
 <span data-ttu-id="63d55-500">WMI 이벤트 감시자 `ActionAtEvent` 속성-열거 값을 사용 하 여 설정 `ActionAtEvent` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-500">WMI Event Watcher `ActionAtEvent` property-Set by using values from the `ActionAtEvent` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-501">ActionAtEvent의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-501">Friendly Name in ActionAtEvent</span></span>|<span data-ttu-id="63d55-502">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-502">Numeric Value</span></span>|  
|------------------------------------|-------------------|  
|<span data-ttu-id="63d55-503">LogTheEventAndFireDTSEvent</span><span class="sxs-lookup"><span data-stu-id="63d55-503">LogTheEventAndFireDTSEvent</span></span>|<span data-ttu-id="63d55-504">0</span><span class="sxs-lookup"><span data-stu-id="63d55-504">0</span></span>|  
|<span data-ttu-id="63d55-505">LogTheEvent</span><span class="sxs-lookup"><span data-stu-id="63d55-505">LogTheEvent</span></span>|<span data-ttu-id="63d55-506">1</span><span class="sxs-lookup"><span data-stu-id="63d55-506">1</span></span>|  
  
 <span data-ttu-id="63d55-507">`ActionAtTimeout`속성-열거형의 값을 사용 하 여 설정 `ActionAtTimeout` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-507">`ActionAtTimeout` property-Set by using values from the `ActionAtTimeout` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-508">ActionAtTimeout의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-508">Friendly name in ActionAtTimeout</span></span>|<span data-ttu-id="63d55-509">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-509">Numeric value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="63d55-510">LogTimeoutAndFireDTSEvent</span><span class="sxs-lookup"><span data-stu-id="63d55-510">LogTimeoutAndFireDTSEvent</span></span>|<span data-ttu-id="63d55-511">0</span><span class="sxs-lookup"><span data-stu-id="63d55-511">0</span></span>|  
|<span data-ttu-id="63d55-512">LogTimeout</span><span class="sxs-lookup"><span data-stu-id="63d55-512">LogTimeout</span></span>|<span data-ttu-id="63d55-513">1</span><span class="sxs-lookup"><span data-stu-id="63d55-513">1</span></span>|  
  
 <span data-ttu-id="63d55-514">`AfterEvent`속성-열거형의 값을 사용 하 여 설정 `AfterEvent` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-514">`AfterEvent` property-Set by using values from the `AfterEvent` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-515">AfterEvent의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-515">Friendly name in AfterEvent</span></span>|<span data-ttu-id="63d55-516">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-516">Numeric value</span></span>|  
|---------------------------------|-------------------|  
|<span data-ttu-id="63d55-517">ReturnWithSuccess</span><span class="sxs-lookup"><span data-stu-id="63d55-517">ReturnWithSuccess</span></span>|<span data-ttu-id="63d55-518">0</span><span class="sxs-lookup"><span data-stu-id="63d55-518">0</span></span>|  
|<span data-ttu-id="63d55-519">ReturnWithFailure</span><span class="sxs-lookup"><span data-stu-id="63d55-519">ReturnWithFailure</span></span>|<span data-ttu-id="63d55-520">1</span><span class="sxs-lookup"><span data-stu-id="63d55-520">1</span></span>|  
|<span data-ttu-id="63d55-521">WatchfortheEventAgain</span><span class="sxs-lookup"><span data-stu-id="63d55-521">WatchfortheEventAgain</span></span>|<span data-ttu-id="63d55-522">2</span><span class="sxs-lookup"><span data-stu-id="63d55-522">2</span></span>|  
  
 <span data-ttu-id="63d55-523">`AfterTimeout`속성-열거형의 값을 사용 하 여 설정 `AfterTimeout` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-523">`AfterTimeout` property-Set by using values from the `AfterTimeout` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-524">AfterTimeout의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-524">Friendly name in AfterTimeout</span></span>|<span data-ttu-id="63d55-525">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-525">Numeric value</span></span>|  
|-----------------------------------|-------------------|  
|<span data-ttu-id="63d55-526">ReturnWithSuccess</span><span class="sxs-lookup"><span data-stu-id="63d55-526">ReturnWithSuccess</span></span>|<span data-ttu-id="63d55-527">0</span><span class="sxs-lookup"><span data-stu-id="63d55-527">0</span></span>|  
|<span data-ttu-id="63d55-528">ReturnWithFailure</span><span class="sxs-lookup"><span data-stu-id="63d55-528">ReturnWithFailure</span></span>|<span data-ttu-id="63d55-529">1</span><span class="sxs-lookup"><span data-stu-id="63d55-529">1</span></span>|  
|<span data-ttu-id="63d55-530">WatchfortheEventAgain</span><span class="sxs-lookup"><span data-stu-id="63d55-530">WatchfortheEventAgain</span></span>|<span data-ttu-id="63d55-531">2</span><span class="sxs-lookup"><span data-stu-id="63d55-531">2</span></span>|  
  
 <span data-ttu-id="63d55-532">`WqlQuerySourceType`속성-열거형의 값을 사용 하 여 설정 `QuerySourceType` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-532">`WqlQuerySourceType` property-Set by using values from the `QuerySourceType` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-533">QuerySourceType의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-533">Friendly name in QuerySourceType</span></span>|<span data-ttu-id="63d55-534">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-534">Numeric value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="63d55-535">FileConnection</span><span class="sxs-lookup"><span data-stu-id="63d55-535">FileConnection</span></span>|<span data-ttu-id="63d55-536">0</span><span class="sxs-lookup"><span data-stu-id="63d55-536">0</span></span>|  
|<span data-ttu-id="63d55-537">DirectInput</span><span class="sxs-lookup"><span data-stu-id="63d55-537">DirectInput</span></span>|<span data-ttu-id="63d55-538">1</span><span class="sxs-lookup"><span data-stu-id="63d55-538">1</span></span>|  
|<span data-ttu-id="63d55-539">변수</span><span class="sxs-lookup"><span data-stu-id="63d55-539">Variable</span></span>|<span data-ttu-id="63d55-540">2</span><span class="sxs-lookup"><span data-stu-id="63d55-540">2</span></span>|  
  
### <a name="xml-task"></a><span data-ttu-id="63d55-541">XML 태스크</span><span class="sxs-lookup"><span data-stu-id="63d55-541">XML Task</span></span>  
 <span data-ttu-id="63d55-542">`OperationType`속성-열거형의 값을 사용 하 여 설정 `DTSXMLOperation` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-542">`OperationType` property-Set by using values from the `DTSXMLOperation` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-543">DTSXMLOperation의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-543">Friendly name in DTSXMLOperation</span></span>|<span data-ttu-id="63d55-544">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-544">Numeric value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="63d55-545">유효성 검사</span><span class="sxs-lookup"><span data-stu-id="63d55-545">Validate</span></span>|<span data-ttu-id="63d55-546">0</span><span class="sxs-lookup"><span data-stu-id="63d55-546">0</span></span>|  
|<span data-ttu-id="63d55-547">XSLT</span><span class="sxs-lookup"><span data-stu-id="63d55-547">XSLT</span></span>|<span data-ttu-id="63d55-548">1</span><span class="sxs-lookup"><span data-stu-id="63d55-548">1</span></span>|  
|<span data-ttu-id="63d55-549">XPATH</span><span class="sxs-lookup"><span data-stu-id="63d55-549">XPATH</span></span>|<span data-ttu-id="63d55-550">2</span><span class="sxs-lookup"><span data-stu-id="63d55-550">2</span></span>|  
|<span data-ttu-id="63d55-551">병합</span><span class="sxs-lookup"><span data-stu-id="63d55-551">Merge</span></span>|<span data-ttu-id="63d55-552">3</span><span class="sxs-lookup"><span data-stu-id="63d55-552">3</span></span>|  
|<span data-ttu-id="63d55-553">Diff</span><span class="sxs-lookup"><span data-stu-id="63d55-553">Diff</span></span>|<span data-ttu-id="63d55-554">4</span><span class="sxs-lookup"><span data-stu-id="63d55-554">4</span></span>|  
|<span data-ttu-id="63d55-555">패치</span><span class="sxs-lookup"><span data-stu-id="63d55-555">Patch</span></span>|<span data-ttu-id="63d55-556">5</span><span class="sxs-lookup"><span data-stu-id="63d55-556">5</span></span>|  
  
 <span data-ttu-id="63d55-557">`SourceType`, `SecondOperandType` 및 `XPathSourceType` 속성-열거형의 값을 사용 하 여 설정 `DTSXMLSourceType` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-557">`SourceType`, `SecondOperandType`, and `XPathSourceType` properties-Set by using values from the `DTSXMLSourceType` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-558">DTSXMLSourceType의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-558">Friendly name in DTSXMLSourceType</span></span>|<span data-ttu-id="63d55-559">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-559">Numeric value</span></span>|  
|---------------------------------------|-------------------|  
|<span data-ttu-id="63d55-560">FileConnection</span><span class="sxs-lookup"><span data-stu-id="63d55-560">FileConnection</span></span>|<span data-ttu-id="63d55-561">0</span><span class="sxs-lookup"><span data-stu-id="63d55-561">0</span></span>|  
|<span data-ttu-id="63d55-562">변수</span><span class="sxs-lookup"><span data-stu-id="63d55-562">Variable</span></span>|<span data-ttu-id="63d55-563">1</span><span class="sxs-lookup"><span data-stu-id="63d55-563">1</span></span>|  
|<span data-ttu-id="63d55-564">DirectInput</span><span class="sxs-lookup"><span data-stu-id="63d55-564">DirectInput</span></span>|<span data-ttu-id="63d55-565">2</span><span class="sxs-lookup"><span data-stu-id="63d55-565">2</span></span>|  
  
 <span data-ttu-id="63d55-566">`DestinationType`및 **DiffGramDestinationType** 속성-열거형의 값을 사용 하 여 설정 `DTSXMLSaveResultTo` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-566">`DestinationType` and **DiffGramDestinationType** properties-Set by using values from the `DTSXMLSaveResultTo` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-567">DTSXMLSaveResultTo의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-567">Friendly name in DTSXMLSaveResultTo</span></span>|<span data-ttu-id="63d55-568">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-568">Numeric value</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="63d55-569">FileConnection</span><span class="sxs-lookup"><span data-stu-id="63d55-569">FileConnection</span></span>|<span data-ttu-id="63d55-570">0</span><span class="sxs-lookup"><span data-stu-id="63d55-570">0</span></span>|  
|<span data-ttu-id="63d55-571">변수</span><span class="sxs-lookup"><span data-stu-id="63d55-571">Variable</span></span>|<span data-ttu-id="63d55-572">1</span><span class="sxs-lookup"><span data-stu-id="63d55-572">1</span></span>|  
  
 <span data-ttu-id="63d55-573">`ValidationType`속성-열거형의 값을 사용 하 여 설정 `DTSXMLValidationType` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-573">`ValidationType` property-Set by using values from the `DTSXMLValidationType` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-574">DTSXMLValidationType의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-574">Friendly name in DTSXMLValidationType</span></span>|<span data-ttu-id="63d55-575">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-575">Numeric value</span></span>|  
|-------------------------------------------|-------------------|  
|<span data-ttu-id="63d55-576">DTD</span><span class="sxs-lookup"><span data-stu-id="63d55-576">DTD</span></span>|<span data-ttu-id="63d55-577">0</span><span class="sxs-lookup"><span data-stu-id="63d55-577">0</span></span>|  
|<span data-ttu-id="63d55-578">XSD</span><span class="sxs-lookup"><span data-stu-id="63d55-578">XSD</span></span>|<span data-ttu-id="63d55-579">1</span><span class="sxs-lookup"><span data-stu-id="63d55-579">1</span></span>|  
  
 <span data-ttu-id="63d55-580">`XPathOperation`속성-열거형의 값을 사용 하 여 설정 `DTSXMLXPathOperation` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-580">`XPathOperation` property-Set by using values from the `DTSXMLXPathOperation` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-581">DTSXMLXPathOperation의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-581">Friendly name in DTSXMLXPathOperation</span></span>|<span data-ttu-id="63d55-582">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-582">Numeric Value</span></span>|  
|-------------------------------------------|-------------------|  
|<span data-ttu-id="63d55-583">평가</span><span class="sxs-lookup"><span data-stu-id="63d55-583">Evaluation</span></span>|<span data-ttu-id="63d55-584">0</span><span class="sxs-lookup"><span data-stu-id="63d55-584">0</span></span>|  
|<span data-ttu-id="63d55-585">값</span><span class="sxs-lookup"><span data-stu-id="63d55-585">Values</span></span>|<span data-ttu-id="63d55-586">1</span><span class="sxs-lookup"><span data-stu-id="63d55-586">1</span></span>|  
|<span data-ttu-id="63d55-587">NodeList</span><span class="sxs-lookup"><span data-stu-id="63d55-587">NodeList</span></span>|<span data-ttu-id="63d55-588">2</span><span class="sxs-lookup"><span data-stu-id="63d55-588">2</span></span>|  
  
 <span data-ttu-id="63d55-589">`DiffOptions`속성-열거형의 값을 사용 하 여 설정 `DTSXMLDiffOptions` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-589">`DiffOptions` property-Set by using values from the `DTSXMLDiffOptions` enumeration.</span></span> <span data-ttu-id="63d55-590">이 열거자의 옵션은 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-590">The options in this enumerator are not mutually exclusive.</span></span> <span data-ttu-id="63d55-591">여러 옵션을 사용하려면 적용할 옵션의 목록을 쉼표로 구분하여 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-591">To use multiple options, provide a comma-separated list of the options to apply.</span></span>  
  
|<span data-ttu-id="63d55-592">DTSXMLDiffOptions의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-592">Friendly name in DTSXMLDiffOptions</span></span>|<span data-ttu-id="63d55-593">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-593">Numeric Value</span></span>|  
|----------------------------------------|-------------------|  
|<span data-ttu-id="63d55-594">None</span><span class="sxs-lookup"><span data-stu-id="63d55-594">None</span></span>|<span data-ttu-id="63d55-595">0</span><span class="sxs-lookup"><span data-stu-id="63d55-595">0</span></span>|  
|<span data-ttu-id="63d55-596">IgnoreChildOrder</span><span class="sxs-lookup"><span data-stu-id="63d55-596">IgnoreChildOrder</span></span>|<span data-ttu-id="63d55-597">1</span><span class="sxs-lookup"><span data-stu-id="63d55-597">1</span></span>|  
|<span data-ttu-id="63d55-598">IgnoreComments</span><span class="sxs-lookup"><span data-stu-id="63d55-598">IgnoreComments</span></span>|<span data-ttu-id="63d55-599">2</span><span class="sxs-lookup"><span data-stu-id="63d55-599">2</span></span>|  
|<span data-ttu-id="63d55-600">IgnorePI</span><span class="sxs-lookup"><span data-stu-id="63d55-600">IgnorePI</span></span>|<span data-ttu-id="63d55-601">4</span><span class="sxs-lookup"><span data-stu-id="63d55-601">4</span></span>|  
|<span data-ttu-id="63d55-602">IgnoreWhitespace</span><span class="sxs-lookup"><span data-stu-id="63d55-602">IgnoreWhitespace</span></span>|<span data-ttu-id="63d55-603">8</span><span class="sxs-lookup"><span data-stu-id="63d55-603">8</span></span>|  
|<span data-ttu-id="63d55-604">IgnoreNamespaces</span><span class="sxs-lookup"><span data-stu-id="63d55-604">IgnoreNamespaces</span></span>|<span data-ttu-id="63d55-605">16</span><span class="sxs-lookup"><span data-stu-id="63d55-605">16</span></span>|  
|<span data-ttu-id="63d55-606">IgnorePrefixes</span><span class="sxs-lookup"><span data-stu-id="63d55-606">IgnorePrefixes</span></span>|<span data-ttu-id="63d55-607">32</span><span class="sxs-lookup"><span data-stu-id="63d55-607">32</span></span>|  
|<span data-ttu-id="63d55-608">IgnoreXmlDecl</span><span class="sxs-lookup"><span data-stu-id="63d55-608">IgnoreXmlDecl</span></span>|<span data-ttu-id="63d55-609">64</span><span class="sxs-lookup"><span data-stu-id="63d55-609">64</span></span>|  
|<span data-ttu-id="63d55-610">IgnoreDtd</span><span class="sxs-lookup"><span data-stu-id="63d55-610">IgnoreDtd</span></span>|<span data-ttu-id="63d55-611">128</span><span class="sxs-lookup"><span data-stu-id="63d55-611">128</span></span>|  
  
 <span data-ttu-id="63d55-612">`DiffAlgorithm`속성-열거형의 값을 사용 하 여 설정 `DTSXMLDiffAlgorithm` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-612">`DiffAlgorithm` property-Set by using values from the `DTSXMLDiffAlgorithm` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-613">DTSXMLDiffAlgorithm의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-613">Friendly name in DTSXMLDiffAlgorithm</span></span>|<span data-ttu-id="63d55-614">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-614">Numeric value</span></span>|  
|------------------------------------------|-------------------|  
|<span data-ttu-id="63d55-615">Auto</span><span class="sxs-lookup"><span data-stu-id="63d55-615">Auto</span></span>|<span data-ttu-id="63d55-616">0</span><span class="sxs-lookup"><span data-stu-id="63d55-616">0</span></span>|  
|<span data-ttu-id="63d55-617">빠름</span><span class="sxs-lookup"><span data-stu-id="63d55-617">Fast</span></span>|<span data-ttu-id="63d55-618">1</span><span class="sxs-lookup"><span data-stu-id="63d55-618">1</span></span>|  
|<span data-ttu-id="63d55-619">정확</span><span class="sxs-lookup"><span data-stu-id="63d55-619">Precise</span></span>|<span data-ttu-id="63d55-620">2</span><span class="sxs-lookup"><span data-stu-id="63d55-620">2</span></span>|  
  
##  <a name="maintenance-plan-tasks"></a><a name="MaintenancePlanTasks"></a> <span data-ttu-id="63d55-621">유지 관리 계획 태스크</span><span class="sxs-lookup"><span data-stu-id="63d55-621">Maintenance Plan Tasks</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="63d55-622">에는 유지 관리 계획 및 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지에서 사용할 SQL Server 태스크를 수행하는 태스크 집합이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-622">includes a set of tasks that perform SQL Server tasks for use in maintenance plans and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="63d55-623">에서는 이러한 태스크를 프로그래밍 방식으로 수행할 수 없으므로 프로그래밍 참조 설명서에 이러한 태스크 및 해당 열거자에 대한 API 설명서가 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-623">does not support working with these tasks programmatically and programming reference documentation does not include API documentation of these tasks and their enumerators.</span></span>  
  
### <a name="all-maintenance-tasks"></a><span data-ttu-id="63d55-624">모든 유지 관리 태스크</span><span class="sxs-lookup"><span data-stu-id="63d55-624">All Maintenance Tasks</span></span>  
 <span data-ttu-id="63d55-625">모든 유지 관리 태스크에서는 다음 열거를 사용하여 지정된 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-625">All maintenance tasks use the following enumerations to set the specified properties.</span></span>  
  
 <span data-ttu-id="63d55-626">`DatabaseSelectionType`속성-열거형의 값을 사용 하 여 설정 `DatabaseSelection` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-626">`DatabaseSelectionType` property-Set by using values from the `DatabaseSelection` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-627">DatabaseSelection의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-627">Friendly name in DatabaseSelection</span></span>|<span data-ttu-id="63d55-628">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-628">Numeric value</span></span>|  
|----------------------------------------|-------------------|  
|<span data-ttu-id="63d55-629">None</span><span class="sxs-lookup"><span data-stu-id="63d55-629">None</span></span>|<span data-ttu-id="63d55-630">0</span><span class="sxs-lookup"><span data-stu-id="63d55-630">0</span></span>|  
|<span data-ttu-id="63d55-631">모두</span><span class="sxs-lookup"><span data-stu-id="63d55-631">All</span></span>|<span data-ttu-id="63d55-632">1</span><span class="sxs-lookup"><span data-stu-id="63d55-632">1</span></span>|  
|<span data-ttu-id="63d55-633">시스템</span><span class="sxs-lookup"><span data-stu-id="63d55-633">System</span></span>|<span data-ttu-id="63d55-634">2</span><span class="sxs-lookup"><span data-stu-id="63d55-634">2</span></span>|  
|<span data-ttu-id="63d55-635">사용자</span><span class="sxs-lookup"><span data-stu-id="63d55-635">User</span></span>|<span data-ttu-id="63d55-636">3</span><span class="sxs-lookup"><span data-stu-id="63d55-636">3</span></span>|  
|<span data-ttu-id="63d55-637">특정</span><span class="sxs-lookup"><span data-stu-id="63d55-637">Specific</span></span>|<span data-ttu-id="63d55-638">4</span><span class="sxs-lookup"><span data-stu-id="63d55-638">4</span></span>|  
  
 <span data-ttu-id="63d55-639">`TableSelectionType`속성-열거형의 값을 사용 하 여 설정 `TableSelection` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-639">`TableSelectionType` property-Set by using values from the `TableSelection` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-640">TableSelection의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-640">Friendly name in TableSelection</span></span>|<span data-ttu-id="63d55-641">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-641">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="63d55-642">None</span><span class="sxs-lookup"><span data-stu-id="63d55-642">None</span></span>|<span data-ttu-id="63d55-643">0</span><span class="sxs-lookup"><span data-stu-id="63d55-643">0</span></span>|  
|<span data-ttu-id="63d55-644">모두</span><span class="sxs-lookup"><span data-stu-id="63d55-644">All</span></span>|<span data-ttu-id="63d55-645">1</span><span class="sxs-lookup"><span data-stu-id="63d55-645">1</span></span>|  
|<span data-ttu-id="63d55-646">특정</span><span class="sxs-lookup"><span data-stu-id="63d55-646">Specific</span></span>|<span data-ttu-id="63d55-647">2</span><span class="sxs-lookup"><span data-stu-id="63d55-647">2</span></span>|  
  
 <span data-ttu-id="63d55-648">`ObjectTypeSelection`속성-열거형의 값을 사용 하 여 설정 `ObjectType` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-648">`ObjectTypeSelection` property-Set by using values from the `ObjectType` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-649">ObjectType의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-649">Friendly name in ObjectType</span></span>|<span data-ttu-id="63d55-650">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-650">Numeric value</span></span>|  
|---------------------------------|-------------------|  
|<span data-ttu-id="63d55-651">테이블</span><span class="sxs-lookup"><span data-stu-id="63d55-651">Table</span></span>|<span data-ttu-id="63d55-652">0</span><span class="sxs-lookup"><span data-stu-id="63d55-652">0</span></span>|  
|<span data-ttu-id="63d55-653">보기</span><span class="sxs-lookup"><span data-stu-id="63d55-653">View</span></span>|<span data-ttu-id="63d55-654">1</span><span class="sxs-lookup"><span data-stu-id="63d55-654">1</span></span>|  
|<span data-ttu-id="63d55-655">TableView</span><span class="sxs-lookup"><span data-stu-id="63d55-655">TableView</span></span>|<span data-ttu-id="63d55-656">2</span><span class="sxs-lookup"><span data-stu-id="63d55-656">2</span></span>|  
  
### <a name="back-up-database-task"></a><span data-ttu-id="63d55-657">데이터베이스 백업 태스크</span><span class="sxs-lookup"><span data-stu-id="63d55-657">Back Up Database Task</span></span>  
 <span data-ttu-id="63d55-658">`DestinationCreationType`속성-열거형의 값을 사용 하 여 설정 `DestinationType` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-658">`DestinationCreationType` property-Set by using values from the `DestinationType` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-659">DestinationType의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-659">Friendly name in DestinationType</span></span>|<span data-ttu-id="63d55-660">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-660">Numeric value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="63d55-661">Auto</span><span class="sxs-lookup"><span data-stu-id="63d55-661">Auto</span></span>|<span data-ttu-id="63d55-662">0</span><span class="sxs-lookup"><span data-stu-id="63d55-662">0</span></span>|  
|<span data-ttu-id="63d55-663">설명서</span><span class="sxs-lookup"><span data-stu-id="63d55-663">Manual</span></span>|<span data-ttu-id="63d55-664">1</span><span class="sxs-lookup"><span data-stu-id="63d55-664">1</span></span>|  
  
 <span data-ttu-id="63d55-665">`ExistingBackupsAction`속성-열거형의 값을 사용 하 여 설정 `ActionForExistingBackups` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-665">`ExistingBackupsAction` property-Set by using values from the `ActionForExistingBackups` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-666">ActionForExistingBackups의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-666">Friendly name in ActionForExistingBackups</span></span>|<span data-ttu-id="63d55-667">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-667">Numeric value</span></span>|  
|-----------------------------------------------|-------------------|  
|<span data-ttu-id="63d55-668">추가</span><span class="sxs-lookup"><span data-stu-id="63d55-668">Append</span></span>|<span data-ttu-id="63d55-669">0</span><span class="sxs-lookup"><span data-stu-id="63d55-669">0</span></span>|  
|<span data-ttu-id="63d55-670">Overwrite</span><span class="sxs-lookup"><span data-stu-id="63d55-670">Overwrite</span></span>|<span data-ttu-id="63d55-671">1</span><span class="sxs-lookup"><span data-stu-id="63d55-671">1</span></span>|  
  
 <span data-ttu-id="63d55-672">`BackupAction`속성-열거형의 값을 사용 하 여 설정 `BackupTaskType` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-672">`BackupAction` property-Set by using values from the `BackupTaskType` enumeration.</span></span> <span data-ttu-id="63d55-673">이 속성은 `BackupIsIncremental` 속성과 함께 사용하여 태스크가 수행하는 백업 유형을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-673">This property works with the `BackupIsIncremental` property to define the type of backup that the task performs.</span></span>  
  
|<span data-ttu-id="63d55-674">BackupTaskType의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-674">Friendly name in BackupTaskType</span></span>|<span data-ttu-id="63d55-675">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-675">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="63d55-676">데이터베이스</span><span class="sxs-lookup"><span data-stu-id="63d55-676">Database</span></span>|<span data-ttu-id="63d55-677">0</span><span class="sxs-lookup"><span data-stu-id="63d55-677">0</span></span>|  
|<span data-ttu-id="63d55-678">파일</span><span class="sxs-lookup"><span data-stu-id="63d55-678">Files</span></span>|<span data-ttu-id="63d55-679">1</span><span class="sxs-lookup"><span data-stu-id="63d55-679">1</span></span>|  
|<span data-ttu-id="63d55-680">로그</span><span class="sxs-lookup"><span data-stu-id="63d55-680">Log</span></span>|<span data-ttu-id="63d55-681">2</span><span class="sxs-lookup"><span data-stu-id="63d55-681">2</span></span>|  
  
 <span data-ttu-id="63d55-682">`BackupDevice`속성- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SMO (Management Objects) 열거 값을 사용 하 여 설정 `DeviceType` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-682">`BackupDevice` property-Set by using values from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO) `DeviceType` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-683">DeviceType의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-683">Friendly name in DeviceType</span></span>|<span data-ttu-id="63d55-684">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-684">Numeric value</span></span>|  
|---------------------------------|-------------------|  
|<span data-ttu-id="63d55-685">LogicalDevice</span><span class="sxs-lookup"><span data-stu-id="63d55-685">LogicalDevice</span></span>|<span data-ttu-id="63d55-686">0</span><span class="sxs-lookup"><span data-stu-id="63d55-686">0</span></span>|  
|<span data-ttu-id="63d55-687">Tape</span><span class="sxs-lookup"><span data-stu-id="63d55-687">Tape</span></span>|<span data-ttu-id="63d55-688">1</span><span class="sxs-lookup"><span data-stu-id="63d55-688">1</span></span>|  
|<span data-ttu-id="63d55-689">파일</span><span class="sxs-lookup"><span data-stu-id="63d55-689">File</span></span>|<span data-ttu-id="63d55-690">2</span><span class="sxs-lookup"><span data-stu-id="63d55-690">2</span></span>|  
|<span data-ttu-id="63d55-691">Pipe</span><span class="sxs-lookup"><span data-stu-id="63d55-691">Pipe</span></span>|<span data-ttu-id="63d55-692">3</span><span class="sxs-lookup"><span data-stu-id="63d55-692">3</span></span>|  
|<span data-ttu-id="63d55-693">VirtualDevice</span><span class="sxs-lookup"><span data-stu-id="63d55-693">VirtualDevice</span></span>|<span data-ttu-id="63d55-694">4</span><span class="sxs-lookup"><span data-stu-id="63d55-694">4</span></span>|  
  
### <a name="maintenance-cleanup-task"></a><span data-ttu-id="63d55-695">유지 관리 정리 태스크</span><span class="sxs-lookup"><span data-stu-id="63d55-695">Maintenance Cleanup Task</span></span>  
 <span data-ttu-id="63d55-696">`FileTypeSelected`속성-열거형의 값을 사용 하 여 설정 `FileType` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-696">`FileTypeSelected` property-Set by using values from the `FileType` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-697">FileType의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-697">Friendly name in FileType</span></span>|<span data-ttu-id="63d55-698">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-698">Numeric value</span></span>|  
|-------------------------------|-------------------|  
|<span data-ttu-id="63d55-699">FileBackup</span><span class="sxs-lookup"><span data-stu-id="63d55-699">FileBackup</span></span>|<span data-ttu-id="63d55-700">0</span><span class="sxs-lookup"><span data-stu-id="63d55-700">0</span></span>|  
|<span data-ttu-id="63d55-701">FileReport</span><span class="sxs-lookup"><span data-stu-id="63d55-701">FileReport</span></span>|<span data-ttu-id="63d55-702">1</span><span class="sxs-lookup"><span data-stu-id="63d55-702">1</span></span>|  
  
 <span data-ttu-id="63d55-703">`OlderThanTimeUnitType`속성-열거형의 값을 사용 하 여 설정 `TimeUnitType` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-703">`OlderThanTimeUnitType` property-Set by using values from the `TimeUnitType` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-704">TimeUnitType의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-704">Friendly Name in TimeUnitType</span></span>|<span data-ttu-id="63d55-705">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-705">Numeric Value</span></span>|  
|-----------------------------------|-------------------|  
|<span data-ttu-id="63d55-706">일</span><span class="sxs-lookup"><span data-stu-id="63d55-706">Day</span></span>|<span data-ttu-id="63d55-707">0</span><span class="sxs-lookup"><span data-stu-id="63d55-707">0</span></span>|  
|<span data-ttu-id="63d55-708">Week</span><span class="sxs-lookup"><span data-stu-id="63d55-708">Week</span></span>|<span data-ttu-id="63d55-709">1</span><span class="sxs-lookup"><span data-stu-id="63d55-709">1</span></span>|  
|<span data-ttu-id="63d55-710">Month</span><span class="sxs-lookup"><span data-stu-id="63d55-710">Month</span></span>|<span data-ttu-id="63d55-711">2</span><span class="sxs-lookup"><span data-stu-id="63d55-711">2</span></span>|  
|<span data-ttu-id="63d55-712">Year</span><span class="sxs-lookup"><span data-stu-id="63d55-712">Year</span></span>|<span data-ttu-id="63d55-713">3</span><span class="sxs-lookup"><span data-stu-id="63d55-713">3</span></span>|  
  
### <a name="update-statistics-task"></a><span data-ttu-id="63d55-714">통계 업데이트 태스크</span><span class="sxs-lookup"><span data-stu-id="63d55-714">Update Statistics Task</span></span>  
 <span data-ttu-id="63d55-715">`UpdateType`속성- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SMO (Management Objects) 열거 값을 사용 하 여 설정 `StatisticsTarget` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-715">`UpdateType` property-Set by using values from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO) `StatisticsTarget` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-716">StatisticsTarget의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-716">Friendly name in StatisticsTarget</span></span>|<span data-ttu-id="63d55-717">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-717">Numeric value</span></span>|  
|---------------------------------------|-------------------|  
|<span data-ttu-id="63d55-718">열</span><span class="sxs-lookup"><span data-stu-id="63d55-718">Column</span></span>|<span data-ttu-id="63d55-719">1</span><span class="sxs-lookup"><span data-stu-id="63d55-719">1</span></span>|  
|<span data-ttu-id="63d55-720">인덱스</span><span class="sxs-lookup"><span data-stu-id="63d55-720">Index</span></span>|<span data-ttu-id="63d55-721">2</span><span class="sxs-lookup"><span data-stu-id="63d55-721">2</span></span>|  
|<span data-ttu-id="63d55-722">모두</span><span class="sxs-lookup"><span data-stu-id="63d55-722">All</span></span>|<span data-ttu-id="63d55-723">3</span><span class="sxs-lookup"><span data-stu-id="63d55-723">3</span></span>|  
  
##  <a name="common-properties"></a><a name="CommonProperties"></a> <span data-ttu-id="63d55-724">공용 속성</span><span class="sxs-lookup"><span data-stu-id="63d55-724">Common Properties</span></span>  
 <span data-ttu-id="63d55-725">패키지, 태스크, Foreach 루프 컨테이너, For 루프 컨테이너, 시퀀스 컨테이너에서는 다음 열거를 사용하여 지정된 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-725">Packages, tasks, and the Foreach Loop, For Loop, and Sequence containers can use the following enumerations to set the specified properties.</span></span>  
  
 <span data-ttu-id="63d55-726">`ForceExecutionResult`속성-열거형의 값을 사용 하 여 설정 `DTSForcedExecResult` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-726">`ForceExecutionResult` property-Set by using values from the `DTSForcedExecResult` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-727">DTSForcedExecResult의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-727">Friendly name in DTSForcedExecResult</span></span>|<span data-ttu-id="63d55-728">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-728">Numeric value</span></span>|  
|------------------------------------------|-------------------|  
|<span data-ttu-id="63d55-729">None</span><span class="sxs-lookup"><span data-stu-id="63d55-729">None</span></span>|<span data-ttu-id="63d55-730">-1</span><span class="sxs-lookup"><span data-stu-id="63d55-730">-1</span></span>|  
|<span data-ttu-id="63d55-731">Success</span><span class="sxs-lookup"><span data-stu-id="63d55-731">Success</span></span>|<span data-ttu-id="63d55-732">0</span><span class="sxs-lookup"><span data-stu-id="63d55-732">0</span></span>|  
|<span data-ttu-id="63d55-733">실패</span><span class="sxs-lookup"><span data-stu-id="63d55-733">Failure</span></span>|<span data-ttu-id="63d55-734">1</span><span class="sxs-lookup"><span data-stu-id="63d55-734">1</span></span>|  
|<span data-ttu-id="63d55-735">Completion</span><span class="sxs-lookup"><span data-stu-id="63d55-735">Completion</span></span>|<span data-ttu-id="63d55-736">2</span><span class="sxs-lookup"><span data-stu-id="63d55-736">2</span></span>|  
  
 <span data-ttu-id="63d55-737">`IsolationLevel`속성-.NET Framework 열거형에 의해 설정 `IsolationLevel` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-737">`IsolationLevel` property-Set by the .NET Framework `IsolationLevel` enumeration.</span></span> <span data-ttu-id="63d55-738">자세한 내용은 [MSDN Library](https://go.microsoft.com/fwlink?LinkId=17313)의 .NET Framework 클래스 라이브러리(.NET Framework Class Library)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="63d55-738">For more information, see the .NET Framework Class Library in the [MSDN Library](https://go.microsoft.com/fwlink?LinkId=17313).</span></span>  
  
 <span data-ttu-id="63d55-739">`LoggingMode`속성-열거형의 값을 사용 하 여 설정 `DTSLoggingMode` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-739">`LoggingMode` property-Set by using values from the `DTSLoggingMode` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-740">DTSLoggingMode의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-740">Friendly name in DTSLoggingMode</span></span>|<span data-ttu-id="63d55-741">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-741">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="63d55-742">UseParentSetting</span><span class="sxs-lookup"><span data-stu-id="63d55-742">UseParentSetting</span></span>|<span data-ttu-id="63d55-743">0</span><span class="sxs-lookup"><span data-stu-id="63d55-743">0</span></span>|  
|<span data-ttu-id="63d55-744">사용</span><span class="sxs-lookup"><span data-stu-id="63d55-744">Enabled</span></span>|<span data-ttu-id="63d55-745">1</span><span class="sxs-lookup"><span data-stu-id="63d55-745">1</span></span>|  
|<span data-ttu-id="63d55-746">사용 안 함</span><span class="sxs-lookup"><span data-stu-id="63d55-746">Disabled</span></span>|<span data-ttu-id="63d55-747">2</span><span class="sxs-lookup"><span data-stu-id="63d55-747">2</span></span>|  
  
 <span data-ttu-id="63d55-748">`TransactionOption`속성-열거형의 값을 사용 하 여 설정 `DTSTransactionOption` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d55-748">`TransactionOption` property-Set by using values from the `DTSTransactionOption` enumeration.</span></span>  
  
|<span data-ttu-id="63d55-749">DTSTransactionOption의 이름</span><span class="sxs-lookup"><span data-stu-id="63d55-749">Friendly name in DTSTransactionOption</span></span>|<span data-ttu-id="63d55-750">숫자 값</span><span class="sxs-lookup"><span data-stu-id="63d55-750">Numeric value</span></span>|  
|-------------------------------------------|-------------------|  
|<span data-ttu-id="63d55-751">NotSupported</span><span class="sxs-lookup"><span data-stu-id="63d55-751">NotSupported</span></span>|<span data-ttu-id="63d55-752">0</span><span class="sxs-lookup"><span data-stu-id="63d55-752">0</span></span>|  
|<span data-ttu-id="63d55-753">지원됨</span><span class="sxs-lookup"><span data-stu-id="63d55-753">Supported</span></span>|<span data-ttu-id="63d55-754">1</span><span class="sxs-lookup"><span data-stu-id="63d55-754">1</span></span>|  
|<span data-ttu-id="63d55-755">필수</span><span class="sxs-lookup"><span data-stu-id="63d55-755">Required</span></span>|<span data-ttu-id="63d55-756">2</span><span class="sxs-lookup"><span data-stu-id="63d55-756">2</span></span>|  
  
## <a name="related-tasks"></a><span data-ttu-id="63d55-757">관련 작업</span><span class="sxs-lookup"><span data-stu-id="63d55-757">Related Tasks</span></span>  
 [<span data-ttu-id="63d55-758">속성 식 추가 또는 변경</span><span class="sxs-lookup"><span data-stu-id="63d55-758">Add or Change a Property Expression</span></span>](add-or-change-a-property-expression.md)  
  
## <a name="see-also"></a><span data-ttu-id="63d55-759">참고 항목</span><span class="sxs-lookup"><span data-stu-id="63d55-759">See Also</span></span>  
 <span data-ttu-id="63d55-760">[패키지에서 속성 식 사용](use-property-expressions-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="63d55-760">[Use Property Expressions in Packages](use-property-expressions-in-packages.md) </span></span>  
 <span data-ttu-id="63d55-761">[Integration Services&#40;SSIS&#41; 패키지](../integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="63d55-761">[Integration Services &#40;SSIS&#41; Packages](../integration-services-ssis-packages.md) </span></span>  
 <span data-ttu-id="63d55-762">[Integration Services 컨테이너](../control-flow/integration-services-containers.md) </span><span class="sxs-lookup"><span data-stu-id="63d55-762">[Integration Services Containers](../control-flow/integration-services-containers.md) </span></span>  
 <span data-ttu-id="63d55-763">[Integration Services 태스크](../control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="63d55-763">[Integration Services Tasks](../control-flow/integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="63d55-764">선행 제약 조건</span><span class="sxs-lookup"><span data-stu-id="63d55-764">Precedence Constraints</span></span>](../control-flow/precedence-constraints.md)  
  
  
