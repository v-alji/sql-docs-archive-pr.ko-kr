---
title: 파티션 처리 대상 편집기 (고급 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partprocessingtransformation.advanced.f1
helpviewer_keywords:
- Partition Processing Destination Editor
ms.assetid: 2039ee0f-069d-479d-90b2-2a12481b1162
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 12845ecd644eabd949ea37fbb18ba6cc9cf342f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647094"
---
# <a name="partition-processing-destination-editor-advanced-page"></a><span data-ttu-id="b4763-102">파티션 처리 대상 편집기(고급 페이지)</span><span class="sxs-lookup"><span data-stu-id="b4763-102">Partition Processing Destination Editor (Advanced Page)</span></span>
  <span data-ttu-id="b4763-103">**파티션 처리 대상 편집기** 대화 상자의 **고급** 페이지를 사용하여 오류 처리 방법을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-103">Use the **Advanced** page of the **Partition Processing Destination Editor** dialog box to configure error handling.</span></span>  
  
 <span data-ttu-id="b4763-104">파티션 처리 대상에 대한 자세한 내용은 [Partition Processing Destination](data-flow/partition-processing-destination.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b4763-104">To learn more about the Partition Processing destination, see [Partition Processing Destination](data-flow/partition-processing-destination.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b4763-105">여기에서 설명하는 태스크는 Analysis Services 테이블 형식 모델에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-105">Tasks described here do not apply to Analysis Services tabular models.</span></span>  <span data-ttu-id="b4763-106">테이블 형식 모델의 경우 입력 열을 파티션 열에 매핑할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-106">You cannot map input columns to partition columns for tabular models.</span></span> <span data-ttu-id="b4763-107">대신 [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) 를 사용하여 파티션을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-107">You can instead use the Analysis Services Execute DDL task [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) to process the partition.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b4763-108">옵션</span><span class="sxs-lookup"><span data-stu-id="b4763-108">Options</span></span>  
 <span data-ttu-id="b4763-109">**기본 오류 구성 사용**</span><span class="sxs-lookup"><span data-stu-id="b4763-109">**Use default error configuration.**</span></span>  
 <span data-ttu-id="b4763-110">기본 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 오류 처리를 사용할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-110">Specify whether to use the default [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] error handling.</span></span> <span data-ttu-id="b4763-111">이 값은 기본적으로 `True`입니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-111">By default, this value is `True`.</span></span>  
  
 <span data-ttu-id="b4763-112">**키 오류 동작**</span><span class="sxs-lookup"><span data-stu-id="b4763-112">**Key error action**</span></span>  
 <span data-ttu-id="b4763-113">사용할 수 없는 키 값이 있는 레코드의 처리 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-113">Specify how to handle records that have unacceptable key values.</span></span>  
  
|<span data-ttu-id="b4763-114">값</span><span class="sxs-lookup"><span data-stu-id="b4763-114">Value</span></span>|<span data-ttu-id="b4763-115">Description</span><span class="sxs-lookup"><span data-stu-id="b4763-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b4763-116">**ConvertToUnknown**</span><span class="sxs-lookup"><span data-stu-id="b4763-116">**ConvertToUnknown**</span></span>|<span data-ttu-id="b4763-117">사용할 수 없는 키 값을 Unknown 값으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-117">Convert the unacceptable key value to the Unknown value.</span></span>|  
|<span data-ttu-id="b4763-118">**DiscardRecord**</span><span class="sxs-lookup"><span data-stu-id="b4763-118">**DiscardRecord**</span></span>|<span data-ttu-id="b4763-119">레코드를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-119">Discard the record.</span></span>|  
  
 <span data-ttu-id="b4763-120">**오류 무시**</span><span class="sxs-lookup"><span data-stu-id="b4763-120">**Ignore errors**</span></span>  
 <span data-ttu-id="b4763-121">오류를 무시하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-121">Specify that errors should be ignored.</span></span>  
  
 <span data-ttu-id="b4763-122">**오류 발생 시 중지**</span><span class="sxs-lookup"><span data-stu-id="b4763-122">**Stop on error**</span></span>  
 <span data-ttu-id="b4763-123">오류가 발생하면 처리를 중지하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-123">Specify that processing should stop when an error occurs.</span></span>  
  
 <span data-ttu-id="b4763-124">**오류 개수**</span><span class="sxs-lookup"><span data-stu-id="b4763-124">**Number of errors**</span></span>  
 <span data-ttu-id="b4763-125">**오류 발생 시 중지**를 선택한 경우 처리를 중지하는 데 기준이 되는 오류 임계값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-125">Specify the error threshold at which processing should stop, if you have selected **Stop on error**.</span></span>  
  
 <span data-ttu-id="b4763-126">**오류 시 수행할 동작**</span><span class="sxs-lookup"><span data-stu-id="b4763-126">**On error action**</span></span>  
 <span data-ttu-id="b4763-127">**오류 발생 시 중지**를 선택한 경우 오류 임계값에 도달했을 때 수행할 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-127">Specify the action to take when the error threshold is reached, if you have selected **Stop on error**.</span></span>  
  
|<span data-ttu-id="b4763-128">값</span><span class="sxs-lookup"><span data-stu-id="b4763-128">Value</span></span>|<span data-ttu-id="b4763-129">Description</span><span class="sxs-lookup"><span data-stu-id="b4763-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b4763-130">**StopProcessing**</span><span class="sxs-lookup"><span data-stu-id="b4763-130">**StopProcessing**</span></span>|<span data-ttu-id="b4763-131">처리를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-131">Stop processing.</span></span>|  
|<span data-ttu-id="b4763-132">**StopLogging**</span><span class="sxs-lookup"><span data-stu-id="b4763-132">**StopLogging**</span></span>|<span data-ttu-id="b4763-133">오류 기록을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-133">Stop logging errors.</span></span>|  
  
 <span data-ttu-id="b4763-134">**키를 찾을 수 없는 경우**</span><span class="sxs-lookup"><span data-stu-id="b4763-134">**Key not found**</span></span>  
 <span data-ttu-id="b4763-135">키를 찾을 수 없을 때 수행할 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-135">Specify the action to take for a key not found error.</span></span> <span data-ttu-id="b4763-136">기본적으로 이 값은 **ReportAndContinue**입니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-136">By default, this value is **ReportAndContinue**.</span></span>  
  
|<span data-ttu-id="b4763-137">값</span><span class="sxs-lookup"><span data-stu-id="b4763-137">Value</span></span>|<span data-ttu-id="b4763-138">Description</span><span class="sxs-lookup"><span data-stu-id="b4763-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b4763-139">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="b4763-139">**IgnoreError**</span></span>|<span data-ttu-id="b4763-140">오류를 무시하고 처리를 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-140">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="b4763-141">**ReportAndContinue**</span><span class="sxs-lookup"><span data-stu-id="b4763-141">**ReportAndContinue**</span></span>|<span data-ttu-id="b4763-142">오류를 보고하고 처리를 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-142">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="b4763-143">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="b4763-143">**ReportAndStop**</span></span>|<span data-ttu-id="b4763-144">오류를 보고하고 처리를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-144">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="b4763-145">**중복 키**</span><span class="sxs-lookup"><span data-stu-id="b4763-145">**Duplicate key**</span></span>  
 <span data-ttu-id="b4763-146">중복 키 오류가 발생할 때 수행할 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-146">Specify the action to take for a duplicate key error.</span></span> <span data-ttu-id="b4763-147">기본적으로 이 값은 **IgnoreError**입니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-147">By default, this value is **IgnoreError**.</span></span>  
  
|<span data-ttu-id="b4763-148">값</span><span class="sxs-lookup"><span data-stu-id="b4763-148">Value</span></span>|<span data-ttu-id="b4763-149">Description</span><span class="sxs-lookup"><span data-stu-id="b4763-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b4763-150">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="b4763-150">**IgnoreError**</span></span>|<span data-ttu-id="b4763-151">오류를 무시하고 처리를 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-151">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="b4763-152">**ReportAndContinue**</span><span class="sxs-lookup"><span data-stu-id="b4763-152">**ReportAndContinue**</span></span>|<span data-ttu-id="b4763-153">오류를 보고하고 처리를 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-153">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="b4763-154">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="b4763-154">**ReportAndStop**</span></span>|<span data-ttu-id="b4763-155">오류를 보고하고 처리를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-155">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="b4763-156">**Null 키가 알 수 없음으로 변환 되었습니다.**</span><span class="sxs-lookup"><span data-stu-id="b4763-156">**Null key converted to unknown**</span></span>  
 <span data-ttu-id="b4763-157">Null 키가 Unknown 값으로 변환된 경우 수행할 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-157">Specify the action to take when a null key has been converted to the Unknown value.</span></span> <span data-ttu-id="b4763-158">기본적으로 이 값은 **IgnoreError**입니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-158">By default, this value is **IgnoreError**.</span></span>  
  
|<span data-ttu-id="b4763-159">값</span><span class="sxs-lookup"><span data-stu-id="b4763-159">Value</span></span>|<span data-ttu-id="b4763-160">Description</span><span class="sxs-lookup"><span data-stu-id="b4763-160">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b4763-161">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="b4763-161">**IgnoreError**</span></span>|<span data-ttu-id="b4763-162">오류를 무시하고 처리를 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-162">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="b4763-163">**ReportAndContinue**</span><span class="sxs-lookup"><span data-stu-id="b4763-163">**ReportAndContinue**</span></span>|<span data-ttu-id="b4763-164">오류를 보고하고 처리를 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-164">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="b4763-165">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="b4763-165">**ReportAndStop**</span></span>|<span data-ttu-id="b4763-166">오류를 보고하고 처리를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-166">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="b4763-167">**Null 키가 허용 되지 않습니다.**</span><span class="sxs-lookup"><span data-stu-id="b4763-167">**Null key not allowed**</span></span>  
 <span data-ttu-id="b4763-168">Null 키가 허용되지 않는데 Null 키가 있는 경우에 수행할 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-168">Specify the action to take when null keys are not allowed and a null key is encountered.</span></span> <span data-ttu-id="b4763-169">기본적으로 이 값은 **ReportAndContinue**입니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-169">By default, this value is **ReportAndContinue**.</span></span>  
  
|<span data-ttu-id="b4763-170">값</span><span class="sxs-lookup"><span data-stu-id="b4763-170">Value</span></span>|<span data-ttu-id="b4763-171">Description</span><span class="sxs-lookup"><span data-stu-id="b4763-171">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b4763-172">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="b4763-172">**IgnoreError**</span></span>|<span data-ttu-id="b4763-173">오류를 무시하고 처리를 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-173">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="b4763-174">**ReportAndContinue**</span><span class="sxs-lookup"><span data-stu-id="b4763-174">**ReportAndContinue**</span></span>|<span data-ttu-id="b4763-175">오류를 보고하고 처리를 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-175">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="b4763-176">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="b4763-176">**ReportAndStop**</span></span>|<span data-ttu-id="b4763-177">오류를 보고하고 처리를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-177">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="b4763-178">**오류 로그 경로**</span><span class="sxs-lookup"><span data-stu-id="b4763-178">**Error log path**</span></span>  
 <span data-ttu-id="b4763-179">오류 로그의 경로를 입력하거나 찾아보기 단추 **(...)** 를 사용하여 대상을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-179">Type the path for the error log, or select a destination by using the browse **(...)** button.</span></span>  
  
 <span data-ttu-id="b4763-180">**찾아보기(...)**</span><span class="sxs-lookup"><span data-stu-id="b4763-180">**Browse (...)**</span></span>  
 <span data-ttu-id="b4763-181">오류 로그의 경로를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b4763-181">Select a path for the error log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4763-182">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b4763-182">See Also</span></span>  
 <span data-ttu-id="b4763-183">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b4763-183">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="b4763-184">파티션 처리 대상 편집기&#40;매핑 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="b4763-184">Partition Processing Destination Editor &#40;Mappings Page&#41;</span></span>](../../2014/integration-services/partition-processing-destination-editor-mappings-page.md)  
  
  
