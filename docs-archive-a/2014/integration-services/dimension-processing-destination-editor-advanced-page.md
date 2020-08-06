---
title: 차원 처리 대상 편집기 (고급 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dimprocessingtransformation.advanced.f1
helpviewer_keywords:
- Dimension Processing Destination Editor
ms.assetid: 2b30835a-2680-4d98-89a4-4f17e29e3818
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5be80cbbfb6871594d7481ccc0f9444d014885e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660068"
---
# <a name="dimension-processing-destination-editor-advanced-page"></a><span data-ttu-id="db154-102">차원 처리 대상 편집기(고급 페이지)</span><span class="sxs-lookup"><span data-stu-id="db154-102">Dimension Processing Destination Editor (Advanced Page)</span></span>
  <span data-ttu-id="db154-103">**차원 처리 대상 편집기** 대화 상자의 **고급** 페이지를 사용하여 오류 처리 방법을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db154-103">Use the **Advanced** page of the **Dimension Processing Destination Editor** dialog box to configure error handling.</span></span>  
  
 <span data-ttu-id="db154-104">차원 처리 대상에 대한 자세한 내용은 [Dimension Processing Destination](data-flow/dimension-processing-destination.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="db154-104">To learn more about the Dimension Processing destination, see [Dimension Processing Destination](data-flow/dimension-processing-destination.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="db154-105">옵션</span><span class="sxs-lookup"><span data-stu-id="db154-105">Options</span></span>  
 <span data-ttu-id="db154-106">**기본 오류 구성 사용**</span><span class="sxs-lookup"><span data-stu-id="db154-106">**Use default error configuration.**</span></span>  
 <span data-ttu-id="db154-107">기본 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 오류 처리를 사용할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-107">Specify whether to use the default [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] error handling.</span></span> <span data-ttu-id="db154-108">이 값은 기본적으로 `True`입니다.</span><span class="sxs-lookup"><span data-stu-id="db154-108">By default, this value is `True`.</span></span>  
  
 <span data-ttu-id="db154-109">**키 오류 동작**</span><span class="sxs-lookup"><span data-stu-id="db154-109">**Key error action**</span></span>  
 <span data-ttu-id="db154-110">사용할 수 없는 키 값이 있는 레코드의 처리 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-110">Specify how to handle records that have unacceptable key values.</span></span>  
  
|<span data-ttu-id="db154-111">값</span><span class="sxs-lookup"><span data-stu-id="db154-111">Value</span></span>|<span data-ttu-id="db154-112">Description</span><span class="sxs-lookup"><span data-stu-id="db154-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="db154-113">**ConvertToUnknown**</span><span class="sxs-lookup"><span data-stu-id="db154-113">**ConvertToUnknown**</span></span>|<span data-ttu-id="db154-114">사용할 수 없는 키 값을 `UnknownMember` 값으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-114">Convert the unacceptable key value to the `UnknownMember` value.</span></span>|  
|<span data-ttu-id="db154-115">**DiscardRecord**</span><span class="sxs-lookup"><span data-stu-id="db154-115">**DiscardRecord**</span></span>|<span data-ttu-id="db154-116">레코드를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-116">Discard the record.</span></span>|  
  
 <span data-ttu-id="db154-117">**오류 무시**</span><span class="sxs-lookup"><span data-stu-id="db154-117">**Ignore errors**</span></span>  
 <span data-ttu-id="db154-118">오류를 무시하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-118">Specify that errors should be ignored.</span></span>  
  
 <span data-ttu-id="db154-119">**오류 발생 시 중지**</span><span class="sxs-lookup"><span data-stu-id="db154-119">**Stop on error**</span></span>  
 <span data-ttu-id="db154-120">오류가 발생하면 처리를 중지하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-120">Specify that processing should stop when an error occurs.</span></span>  
  
 <span data-ttu-id="db154-121">**오류 개수**</span><span class="sxs-lookup"><span data-stu-id="db154-121">**Number of errors**</span></span>  
 <span data-ttu-id="db154-122">**오류 발생 시 중지**를 선택한 경우 처리를 중지하는 데 기준이 되는 오류 임계값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-122">Specify the error threshold at which processing should stop, if you have selected **Stop on errors**.</span></span>  
  
 <span data-ttu-id="db154-123">**오류 시 수행할 동작**</span><span class="sxs-lookup"><span data-stu-id="db154-123">**On error action**</span></span>  
 <span data-ttu-id="db154-124">**오류 발생 시 중지**를 선택한 경우 오류 임계값에 도달했을 때 수행할 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-124">Specify the action to take when the error threshold is reached, if you have selected **Stop on errors**.</span></span>  
  
|<span data-ttu-id="db154-125">값</span><span class="sxs-lookup"><span data-stu-id="db154-125">Value</span></span>|<span data-ttu-id="db154-126">Description</span><span class="sxs-lookup"><span data-stu-id="db154-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="db154-127">**StopProcessing**</span><span class="sxs-lookup"><span data-stu-id="db154-127">**StopProcessing**</span></span>|<span data-ttu-id="db154-128">처리를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-128">Stop processing.</span></span>|  
|<span data-ttu-id="db154-129">**StopLogging**</span><span class="sxs-lookup"><span data-stu-id="db154-129">**StopLogging**</span></span>|<span data-ttu-id="db154-130">오류 기록을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-130">Stop logging errors.</span></span>|  
  
 <span data-ttu-id="db154-131">**키를 찾을 수 없는 경우**</span><span class="sxs-lookup"><span data-stu-id="db154-131">**Key not found**</span></span>  
 <span data-ttu-id="db154-132">키를 찾을 수 없을 때 수행할 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-132">Specify the action to take for a key not found error.</span></span> <span data-ttu-id="db154-133">기본적으로 이 값은 **ReportAndContinue**입니다.</span><span class="sxs-lookup"><span data-stu-id="db154-133">By default, this value is **ReportAndContinue**.</span></span>  
  
|<span data-ttu-id="db154-134">값</span><span class="sxs-lookup"><span data-stu-id="db154-134">Value</span></span>|<span data-ttu-id="db154-135">Description</span><span class="sxs-lookup"><span data-stu-id="db154-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="db154-136">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="db154-136">**IgnoreError**</span></span>|<span data-ttu-id="db154-137">오류를 무시하고 처리를 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-137">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="db154-138">**ReportAndContinue**</span><span class="sxs-lookup"><span data-stu-id="db154-138">**ReportAndContinue**</span></span>|<span data-ttu-id="db154-139">오류를 보고하고 처리를 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-139">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="db154-140">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="db154-140">**ReportAndStop**</span></span>|<span data-ttu-id="db154-141">오류를 보고하고 처리를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-141">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="db154-142">**중복 키**</span><span class="sxs-lookup"><span data-stu-id="db154-142">**Duplicate key**</span></span>  
 <span data-ttu-id="db154-143">중복 키 오류가 발생할 때 수행할 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-143">Specify the action to take for a duplicate key error.</span></span> <span data-ttu-id="db154-144">기본적으로 이 값은 **IgnoreError**입니다.</span><span class="sxs-lookup"><span data-stu-id="db154-144">By default, this value is **IgnoreError**.</span></span>  
  
|<span data-ttu-id="db154-145">값</span><span class="sxs-lookup"><span data-stu-id="db154-145">Value</span></span>|<span data-ttu-id="db154-146">Description</span><span class="sxs-lookup"><span data-stu-id="db154-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="db154-147">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="db154-147">**IgnoreError**</span></span>|<span data-ttu-id="db154-148">오류를 무시하고 처리를 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-148">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="db154-149">**ReportAndContinue**</span><span class="sxs-lookup"><span data-stu-id="db154-149">**ReportAndContinue**</span></span>|<span data-ttu-id="db154-150">오류를 보고하고 처리를 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-150">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="db154-151">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="db154-151">**ReportAndStop**</span></span>|<span data-ttu-id="db154-152">오류를 보고하고 처리를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-152">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="db154-153">**Null 키가 알 수 없음으로 변환 되었습니다.**</span><span class="sxs-lookup"><span data-stu-id="db154-153">**Null key converted to unknown**</span></span>  
 <span data-ttu-id="db154-154">Null 키가 `UnknownMember` 값으로 변환된 경우 수행할 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-154">Specify the action to take when a null key has been converted to the `UnknownMember` value.</span></span> <span data-ttu-id="db154-155">기본적으로 이 값은 **IgnoreError**입니다.</span><span class="sxs-lookup"><span data-stu-id="db154-155">By default, this value is **IgnoreError**.</span></span>  
  
|<span data-ttu-id="db154-156">값</span><span class="sxs-lookup"><span data-stu-id="db154-156">Value</span></span>|<span data-ttu-id="db154-157">Description</span><span class="sxs-lookup"><span data-stu-id="db154-157">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="db154-158">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="db154-158">**IgnoreError**</span></span>|<span data-ttu-id="db154-159">오류를 무시하고 처리를 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-159">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="db154-160">**ReportAndContinue**</span><span class="sxs-lookup"><span data-stu-id="db154-160">**ReportAndContinue**</span></span>|<span data-ttu-id="db154-161">오류를 보고하고 처리를 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-161">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="db154-162">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="db154-162">**ReportAndStop**</span></span>|<span data-ttu-id="db154-163">오류를 보고하고 처리를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-163">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="db154-164">**Null 키가 허용 되지 않습니다.**</span><span class="sxs-lookup"><span data-stu-id="db154-164">**Null key not allowed**</span></span>  
 <span data-ttu-id="db154-165">Null 키가 허용되지 않는데 Null 키가 있는 경우에 수행할 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-165">Specify the action to take when null keys are not allowed and a null key is encountered.</span></span> <span data-ttu-id="db154-166">기본적으로 이 값은 **ReportAndContinue**입니다.</span><span class="sxs-lookup"><span data-stu-id="db154-166">By default, this value is **ReportAndContinue**.</span></span>  
  
|<span data-ttu-id="db154-167">값</span><span class="sxs-lookup"><span data-stu-id="db154-167">Value</span></span>|<span data-ttu-id="db154-168">Description</span><span class="sxs-lookup"><span data-stu-id="db154-168">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="db154-169">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="db154-169">**IgnoreError**</span></span>|<span data-ttu-id="db154-170">오류를 무시하고 처리를 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-170">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="db154-171">**ReportAndContinue**</span><span class="sxs-lookup"><span data-stu-id="db154-171">**ReportAndContinue**</span></span>|<span data-ttu-id="db154-172">오류를 보고하고 처리를 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-172">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="db154-173">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="db154-173">**ReportAndStop**</span></span>|<span data-ttu-id="db154-174">오류를 보고하고 처리를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-174">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="db154-175">**오류 로그 경로**</span><span class="sxs-lookup"><span data-stu-id="db154-175">**Error log path**</span></span>  
 <span data-ttu-id="db154-176">오류 로그의 경로를 입력 하거나 **찾아보기 (...)** 단추를 클릭 하 여 대상을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-176">Type the path of the error log, or click the **browse(...)** button to select a destination.</span></span>  
  
 <span data-ttu-id="db154-177">**찾아보기(...)**</span><span class="sxs-lookup"><span data-stu-id="db154-177">**Browse (...)**</span></span>  
 <span data-ttu-id="db154-178">오류 로그의 경로를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="db154-178">Select a path for the error log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db154-179">참고 항목</span><span class="sxs-lookup"><span data-stu-id="db154-179">See Also</span></span>  
 <span data-ttu-id="db154-180">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="db154-180">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="db154-181">[차원 처리 대상 편집기 &#40;연결 관리자 페이지&#41;](../../2014/integration-services/dimension-processing-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="db154-181">[Dimension Processing Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/dimension-processing-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="db154-182">차원 처리 대상 편집기&#40;매핑 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="db154-182">Dimension Processing Destination Editor &#40;Mappings Page&#41;</span></span>](../../2014/integration-services/dimension-processing-destination-editor-mappings-page.md)  
  
  
