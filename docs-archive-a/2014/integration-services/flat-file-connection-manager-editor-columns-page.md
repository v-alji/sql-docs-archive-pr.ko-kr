---
title: 플랫 파일 연결 관리자 편집기 (열 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ffileconnection.columns.f1
helpviewer_keywords:
- Flat File Connection Manager Editor
ms.assetid: 40ce7537-abd0-4973-97fd-6ccb90fddfa0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f6ce579f73922d2eaa2c48e98a98f52cd5836f5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647150"
---
# <a name="flat-file-connection-manager-editor-columns-page"></a><span data-ttu-id="9462c-102">플랫 파일 연결 관리자 편집기(열 페이지)</span><span class="sxs-lookup"><span data-stu-id="9462c-102">Flat File Connection Manager Editor (Columns Page)</span></span>
  <span data-ttu-id="9462c-103">**플랫 파일 연결 관리자 편집기** 대화 상자의 **열** 페이지를 사용하여 행 및 열 정보를 지정하고 파일을 미리 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-103">Use the **Columns** page of the **Flat File Connection Manager Editor** dialog box to specify the row and column information, and to preview the file.</span></span>  
  
 <span data-ttu-id="9462c-104">플랫 파일 연결 관리자에 대한 자세한 내용은 [Flat File Connection Manager](connection-manager/file-connection-manager.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9462c-104">To learn more about the Flat File connection manager, see [Flat File Connection Manager](connection-manager/file-connection-manager.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="9462c-105">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="9462c-105">Static Options</span></span>  
 <span data-ttu-id="9462c-106">**연결 관리자 이름**</span><span class="sxs-lookup"><span data-stu-id="9462c-106">**Connection manager name**</span></span>  
 <span data-ttu-id="9462c-107">워크플로의 플랫 파일 연결에 고유한 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-107">Provide a unique name for the Flat File connection in the workflow.</span></span> <span data-ttu-id="9462c-108">제공한 이름은 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-108">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="9462c-109">**설명**</span><span class="sxs-lookup"><span data-stu-id="9462c-109">**Description**</span></span>  
 <span data-ttu-id="9462c-110">연결에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-110">Describe the connection.</span></span> <span data-ttu-id="9462c-111">해당 연결의 용도를 설명하여 패키지를 이해하기 쉽고 유지 관리하기 편하도록 만드는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-111">As a best practice, describe the connection in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
## <a name="flat-file-format-dynamic-options"></a><span data-ttu-id="9462c-112">플랫 파일 형식 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="9462c-112">Flat File Format Dynamic Options</span></span>  
  
### <a name="format--delimited"></a><span data-ttu-id="9462c-113">형식 = 구분 기호로 분리됨</span><span class="sxs-lookup"><span data-stu-id="9462c-113">Format = Delimited</span></span>  
 <span data-ttu-id="9462c-114">**행 구분 기호**</span><span class="sxs-lookup"><span data-stu-id="9462c-114">**Row delimiter**</span></span>  
 <span data-ttu-id="9462c-115">사용 가능한 행 구분 기호의 목록에서 선택하거나 구분 기호 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-115">Select from the list of available row delimiters, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="9462c-116">값</span><span class="sxs-lookup"><span data-stu-id="9462c-116">Value</span></span>|<span data-ttu-id="9462c-117">Description</span><span class="sxs-lookup"><span data-stu-id="9462c-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9462c-118">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="9462c-118">**{CR}{LF}**</span></span>|<span data-ttu-id="9462c-119">행이 캐리지 리턴-줄 바꿈 조합으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-119">Rows are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="9462c-120">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="9462c-120">**{CR}**</span></span>|<span data-ttu-id="9462c-121">행이 캐리지 리턴으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-121">Rows are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="9462c-122">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="9462c-122">**{LF}**</span></span>|<span data-ttu-id="9462c-123">행이 줄 바꿈으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-123">Rows are delimited by a line feed.</span></span>|  
|<span data-ttu-id="9462c-124">**세미콜론 {;}**</span><span class="sxs-lookup"><span data-stu-id="9462c-124">**Semicolon {;}**</span></span>|<span data-ttu-id="9462c-125">행이 세미콜론으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-125">Rows are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="9462c-126">**콜론 {:}**</span><span class="sxs-lookup"><span data-stu-id="9462c-126">**Colon {:}**</span></span>|<span data-ttu-id="9462c-127">행이 콜론으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-127">Rows are delimited by a colon.</span></span>|  
|<span data-ttu-id="9462c-128">**쉼표 {,}**</span><span class="sxs-lookup"><span data-stu-id="9462c-128">**Comma {,}**</span></span>|<span data-ttu-id="9462c-129">행이 쉼표로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-129">Rows are delimited by a comma.</span></span>|  
|<span data-ttu-id="9462c-130">**탭 {t}**</span><span class="sxs-lookup"><span data-stu-id="9462c-130">**Tab {t}**</span></span>|<span data-ttu-id="9462c-131">행이 탭으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-131">Rows are delimited by a tab.</span></span>|  
|<span data-ttu-id="9462c-132">**세로 막대{&#124;}**</span><span class="sxs-lookup"><span data-stu-id="9462c-132">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="9462c-133">행이 세로 막대로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-133">Rows are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="9462c-134">**열 구분 기호**</span><span class="sxs-lookup"><span data-stu-id="9462c-134">**Column delimiter**</span></span>  
 <span data-ttu-id="9462c-135">사용 가능한 열 구분 기호의 목록에서 선택하거나 구분 기호 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-135">Select from the list of available column delimiters, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="9462c-136">값</span><span class="sxs-lookup"><span data-stu-id="9462c-136">Value</span></span>|<span data-ttu-id="9462c-137">Description</span><span class="sxs-lookup"><span data-stu-id="9462c-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9462c-138">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="9462c-138">**{CR}{LF}**</span></span>|<span data-ttu-id="9462c-139">열이 캐리지 리턴-줄 바꿈 조합으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-139">Columns are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="9462c-140">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="9462c-140">**{CR}**</span></span>|<span data-ttu-id="9462c-141">열이 캐리지 리턴으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-141">Columns are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="9462c-142">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="9462c-142">**{LF}**</span></span>|<span data-ttu-id="9462c-143">열이 줄 바꿈으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-143">Columns are delimited by a line feed.</span></span>|  
|<span data-ttu-id="9462c-144">**세미콜론 {;}**</span><span class="sxs-lookup"><span data-stu-id="9462c-144">**Semicolon {;}**</span></span>|<span data-ttu-id="9462c-145">열이 세미콜론으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-145">Columns are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="9462c-146">**콜론 {:}**</span><span class="sxs-lookup"><span data-stu-id="9462c-146">**Colon {:}**</span></span>|<span data-ttu-id="9462c-147">열이 콜론으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-147">Columns are delimited by a colon.</span></span>|  
|<span data-ttu-id="9462c-148">**쉼표 {,}**</span><span class="sxs-lookup"><span data-stu-id="9462c-148">**Comma {,}**</span></span>|<span data-ttu-id="9462c-149">열이 쉼표로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-149">Columns are delimited by a comma.</span></span>|  
|<span data-ttu-id="9462c-150">**탭 {t}**</span><span class="sxs-lookup"><span data-stu-id="9462c-150">**Tab {t}**</span></span>|<span data-ttu-id="9462c-151">열이 탭으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-151">Columns are delimited by a tab.</span></span>|  
|<span data-ttu-id="9462c-152">**세로 막대{&#124;}**</span><span class="sxs-lookup"><span data-stu-id="9462c-152">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="9462c-153">열이 세로 막대로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-153">Columns are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="9462c-154">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="9462c-154">**Refresh**</span></span>  
 <span data-ttu-id="9462c-155">**새로 고침**을 클릭하여 건너뛸 구분 기호의 변경 결과를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-155">View the effect of changing the delimiters to skip by clicking **Refresh**.</span></span> <span data-ttu-id="9462c-156">이 단추는 다른 연결 옵션을 변경한 후에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-156">This button only becomes visible after you have changed other connection options.</span></span>  
  
 <span data-ttu-id="9462c-157">**행 미리 보기**</span><span class="sxs-lookup"><span data-stu-id="9462c-157">**Preview rows**</span></span>  
 <span data-ttu-id="9462c-158">선택한 옵션을 사용하여 열과 행으로 구분된 플랫 파일로 샘플 데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-158">View sample data in the flat file, divided into columns and rows by using the options selected.</span></span>  
  
 <span data-ttu-id="9462c-159">**열 다시 설정**</span><span class="sxs-lookup"><span data-stu-id="9462c-159">**Reset Columns**</span></span>  
 <span data-ttu-id="9462c-160">**열 다시 설정**을 클릭하여 원래 열을 제외한 모든 열을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-160">Remove all but the original columns by clicking **Reset Columns**.</span></span>  
  
### <a name="format--fixed-width"></a><span data-ttu-id="9462c-161">형식 = 고정 폭</span><span class="sxs-lookup"><span data-stu-id="9462c-161">Format = Fixed Width</span></span>  
 <span data-ttu-id="9462c-162">**글꼴**</span><span class="sxs-lookup"><span data-stu-id="9462c-162">**Font**</span></span>  
 <span data-ttu-id="9462c-163">미리 보기 데이터를 표시할 글꼴을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-163">Select the font in which to display the preview data.</span></span>  
  
 <span data-ttu-id="9462c-164">**원본 데이터 열**</span><span class="sxs-lookup"><span data-stu-id="9462c-164">**Source data columns**</span></span>  
 <span data-ttu-id="9462c-165">빨간색 세로 행 표식을 밀어 행 너비를 조절하고 미리 보기 창의 맨 위에 있는 눈금자를 클릭하여 열 너비를 조절합니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-165">Adjust the width of the row by sliding the vertical red row marker, and adjust the width of the columns by clicking the ruler at the top of the preview window</span></span>  
  
 <span data-ttu-id="9462c-166">**행 너비**</span><span class="sxs-lookup"><span data-stu-id="9462c-166">**Row width**</span></span>  
 <span data-ttu-id="9462c-167">개별 열의 구분 기호를 추가하기 전에 행 길이를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-167">Specify the length of the row before adding delimiters for individual columns.</span></span> <span data-ttu-id="9462c-168">또는 미리 보기 창에서 빨간색 세로줄을 끌어 행의 끝을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-168">Or, drag the vertical red line in the preview window to mark the end of the row.</span></span> <span data-ttu-id="9462c-169">행 너비 값이 자동으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-169">The row width value is automatically updated.</span></span>  
  
 <span data-ttu-id="9462c-170">**열 다시 설정**</span><span class="sxs-lookup"><span data-stu-id="9462c-170">**Reset Columns**</span></span>  
 <span data-ttu-id="9462c-171">**열 다시 설정**을 클릭하여 원래 열을 제외한 모든 열을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-171">Remove all but the original columns by clicking **Reset Columns**.</span></span>  
  
### <a name="format--ragged-right"></a><span data-ttu-id="9462c-172">형식 = 왼쪽 정렬</span><span class="sxs-lookup"><span data-stu-id="9462c-172">Format = Ragged Right</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9462c-173">왼쪽 정렬 파일은 마지막 열을 제외한 모든 열에 고정 폭이 지정된 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-173">Ragged right files are files in which every column has a fixed width, except for the last column.</span></span> <span data-ttu-id="9462c-174">마지막 열은 행 구분 기호로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-174">It is delimited by the row delimiter.</span></span>  
  
 <span data-ttu-id="9462c-175">**글꼴**</span><span class="sxs-lookup"><span data-stu-id="9462c-175">**Font**</span></span>  
 <span data-ttu-id="9462c-176">미리 보기 데이터를 표시할 글꼴을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-176">Select the font in which to display the preview data.</span></span>  
  
 <span data-ttu-id="9462c-177">**원본 데이터 열**</span><span class="sxs-lookup"><span data-stu-id="9462c-177">**Source data columns**</span></span>  
 <span data-ttu-id="9462c-178">빨간색 세로 행 표식을 밀어 행 너비를 조절하고 미리 보기 창의 맨 위에 있는 눈금자를 클릭하여 열 너비를 조절합니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-178">Adjust the width of the row by sliding the vertical red row marker, and adjust the width of the columns by clicking the ruler at the top of the preview window</span></span>  
  
 <span data-ttu-id="9462c-179">**행 구분 기호**</span><span class="sxs-lookup"><span data-stu-id="9462c-179">**Row delimiter**</span></span>  
 <span data-ttu-id="9462c-180">사용 가능한 행 구분 기호의 목록에서 선택하거나 구분 기호 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-180">Select from the list of available row delimiters, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="9462c-181">값</span><span class="sxs-lookup"><span data-stu-id="9462c-181">Value</span></span>|<span data-ttu-id="9462c-182">Description</span><span class="sxs-lookup"><span data-stu-id="9462c-182">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9462c-183">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="9462c-183">**{CR}{LF}**</span></span>|<span data-ttu-id="9462c-184">행이 캐리지 리턴-줄 바꿈 조합으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-184">Rows are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="9462c-185">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="9462c-185">**{CR}**</span></span>|<span data-ttu-id="9462c-186">행이 캐리지 리턴으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-186">Rows are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="9462c-187">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="9462c-187">**{LF}**</span></span>|<span data-ttu-id="9462c-188">행이 줄 바꿈으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-188">Rows are delimited by a line feed.</span></span>|  
|<span data-ttu-id="9462c-189">**세미콜론 {;}**</span><span class="sxs-lookup"><span data-stu-id="9462c-189">**Semicolon {;}**</span></span>|<span data-ttu-id="9462c-190">행이 세미콜론으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-190">Rows are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="9462c-191">**콜론 {:}**</span><span class="sxs-lookup"><span data-stu-id="9462c-191">**Colon {:}**</span></span>|<span data-ttu-id="9462c-192">행이 콜론으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-192">Rows are delimited by a colon.</span></span>|  
|<span data-ttu-id="9462c-193">**쉼표 {,}**</span><span class="sxs-lookup"><span data-stu-id="9462c-193">**Comma {,}**</span></span>|<span data-ttu-id="9462c-194">행이 쉼표로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-194">Rows are delimited by a comma.</span></span>|  
|<span data-ttu-id="9462c-195">**탭 {t}**</span><span class="sxs-lookup"><span data-stu-id="9462c-195">**Tab {t}**</span></span>|<span data-ttu-id="9462c-196">행이 탭으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-196">Rows are delimited by a tab.</span></span>|  
|<span data-ttu-id="9462c-197">**세로 막대{&#124;}**</span><span class="sxs-lookup"><span data-stu-id="9462c-197">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="9462c-198">행이 세로 막대로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-198">Rows are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="9462c-199">**열 다시 설정**</span><span class="sxs-lookup"><span data-stu-id="9462c-199">**Reset Columns**</span></span>  
 <span data-ttu-id="9462c-200">**열 다시 설정**을 클릭하여 원래 열을 제외한 모든 열을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="9462c-200">Remove all but the original columns by clicking **Reset Columns**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9462c-201">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9462c-201">See Also</span></span>  
 <span data-ttu-id="9462c-202">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9462c-202">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="9462c-203">[플랫 파일 연결 관리자 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="9462c-203">[Flat File Connection Manager Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="9462c-204">[플랫 파일 연결 관리자 편집기 &#40;고급 페이지&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="9462c-204">[Flat File Connection Manager Editor &#40;Advanced Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="9462c-205">플랫 파일 연결 관리자 편집기&#40;미리 보기 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="9462c-205">Flat File Connection Manager Editor &#40;Preview Page&#41;</span></span>](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)  
  
  
