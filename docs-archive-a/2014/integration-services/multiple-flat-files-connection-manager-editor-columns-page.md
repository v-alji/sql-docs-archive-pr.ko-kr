---
title: 다중 플랫 파일 연결 관리자 편집기 (열 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.multifile.columns.f1
helpviewer_keywords:
- Multiple Flat Files Connection Manager Editor
ms.assetid: ad0cb668-0df2-4d4e-9a20-d20692a0b67a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5a7f4936f0722754b414076820eda7dcf2dc8dc5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647092"
---
# <a name="multiple-flat-files-connection-manager-editor-columns-page"></a><span data-ttu-id="1e1d3-102">다중 플랫 파일 연결 관리자 편집기(열 페이지)</span><span class="sxs-lookup"><span data-stu-id="1e1d3-102">Multiple Flat Files Connection Manager Editor (Columns Page)</span></span>
  <span data-ttu-id="1e1d3-103">**다중 플랫 파일 연결 관리자 편집기** 대화 상자의 **열** 노드를 사용하여 행 정보 및 열 정보를 지정하고 선택한 첫 번째 파일을 미리 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-103">Use the **Columns** node of the **Multiple Flat Files Connection Manager Editor** dialog box to specify the row and column information, and to preview the first selected file.</span></span>  
  
 <span data-ttu-id="1e1d3-104">다중 플랫 파일 연결 관리자에 대한 자세한 내용은 [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-104">To learn more about the Multiple Flat Files connection manager, see [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="1e1d3-105">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="1e1d3-105">Static Options</span></span>  
 <span data-ttu-id="1e1d3-106">**연결 관리자 이름**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-106">**Connection manager name**</span></span>  
 <span data-ttu-id="1e1d3-107">워크플로에서의 다중 플랫 파일 연결에 대한 고유 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-107">Provide a unique name for the Multiple Flat Files connection in the workflow.</span></span> <span data-ttu-id="1e1d3-108">제공한 이름은 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-108">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="1e1d3-109">**설명**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-109">**Description**</span></span>  
 <span data-ttu-id="1e1d3-110">연결에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-110">Describe the connection.</span></span> <span data-ttu-id="1e1d3-111">해당 연결의 용도를 설명하여 패키지를 이해하기 쉽고 유지 관리하기 편하도록 만드는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-111">As a best practice, describe the connection in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
## <a name="flat-file-format-dynamic-options"></a><span data-ttu-id="1e1d3-112">플랫 파일 형식 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="1e1d3-112">Flat File Format Dynamic Options</span></span>  
  
### <a name="format--delimited"></a><span data-ttu-id="1e1d3-113">형식 = 구분 기호로 분리됨</span><span class="sxs-lookup"><span data-stu-id="1e1d3-113">Format = Delimited</span></span>  
 <span data-ttu-id="1e1d3-114">**행 구분 기호**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-114">**Row delimiter**</span></span>  
 <span data-ttu-id="1e1d3-115">사용 가능한 행 구분 기호의 목록에서 선택하거나 구분 기호 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-115">Select from the list of available row delimiters, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="1e1d3-116">값</span><span class="sxs-lookup"><span data-stu-id="1e1d3-116">Value</span></span>|<span data-ttu-id="1e1d3-117">Description</span><span class="sxs-lookup"><span data-stu-id="1e1d3-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1e1d3-118">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-118">**{CR}{LF}**</span></span>|<span data-ttu-id="1e1d3-119">행이 캐리지 리턴-줄 바꿈 조합으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-119">Rows are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="1e1d3-120">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-120">**{CR}**</span></span>|<span data-ttu-id="1e1d3-121">행이 캐리지 리턴으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-121">Rows are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="1e1d3-122">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-122">**{LF}**</span></span>|<span data-ttu-id="1e1d3-123">행이 줄 바꿈으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-123">Rows are delimited by a line feed.</span></span>|  
|<span data-ttu-id="1e1d3-124">**세미콜론 {;}**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-124">**Semicolon {;}**</span></span>|<span data-ttu-id="1e1d3-125">행이 세미콜론으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-125">Rows are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="1e1d3-126">**콜론 {:}**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-126">**Colon {:}**</span></span>|<span data-ttu-id="1e1d3-127">행이 콜론으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-127">Rows are delimited by a colon.</span></span>|  
|<span data-ttu-id="1e1d3-128">**쉼표 {,}**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-128">**Comma {,}**</span></span>|<span data-ttu-id="1e1d3-129">행이 쉼표로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-129">Rows are delimited by a comma.</span></span>|  
|<span data-ttu-id="1e1d3-130">**탭 {t}**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-130">**Tab {t}**</span></span>|<span data-ttu-id="1e1d3-131">행이 탭으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-131">Rows are delimited by a tab.</span></span>|  
|<span data-ttu-id="1e1d3-132">**세로 막대{&#124;}**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-132">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="1e1d3-133">행이 세로 막대로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-133">Rows are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="1e1d3-134">**열 구분 기호**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-134">**Column delimiter**</span></span>  
 <span data-ttu-id="1e1d3-135">사용 가능한 열 구분 기호의 목록에서 선택하거나 구분 기호 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-135">Select from the list of available column delimiters, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="1e1d3-136">값</span><span class="sxs-lookup"><span data-stu-id="1e1d3-136">Value</span></span>|<span data-ttu-id="1e1d3-137">Description</span><span class="sxs-lookup"><span data-stu-id="1e1d3-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1e1d3-138">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-138">**{CR}{LF}**</span></span>|<span data-ttu-id="1e1d3-139">열이 캐리지 리턴-줄 바꿈 조합으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-139">Columns are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="1e1d3-140">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-140">**{CR}**</span></span>|<span data-ttu-id="1e1d3-141">열이 캐리지 리턴으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-141">Columns are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="1e1d3-142">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-142">**{LF}**</span></span>|<span data-ttu-id="1e1d3-143">열이 줄 바꿈으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-143">Columns are delimited by a line feed.</span></span>|  
|<span data-ttu-id="1e1d3-144">**세미콜론 {;}**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-144">**Semicolon {;}**</span></span>|<span data-ttu-id="1e1d3-145">열이 세미콜론으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-145">Columns are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="1e1d3-146">**콜론 {:}**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-146">**Colon {:}**</span></span>|<span data-ttu-id="1e1d3-147">열이 콜론으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-147">Columns are delimited by a colon.</span></span>|  
|<span data-ttu-id="1e1d3-148">**쉼표 {,}**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-148">**Comma {,}**</span></span>|<span data-ttu-id="1e1d3-149">열이 쉼표로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-149">Columns are delimited by a comma.</span></span>|  
|<span data-ttu-id="1e1d3-150">**탭 {t}**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-150">**Tab {t}**</span></span>|<span data-ttu-id="1e1d3-151">열이 탭으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-151">Columns are delimited by a tab.</span></span>|  
|<span data-ttu-id="1e1d3-152">**세로 막대{&#124;}**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-152">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="1e1d3-153">열이 세로 막대로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-153">Columns are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="1e1d3-154">**열 다시 설정**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-154">**Reset Columns**</span></span>  
 <span data-ttu-id="1e1d3-155">**열 다시 설정**을 클릭하여 원래 열을 제외한 모든 열을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-155">Remove all but the original columns by clicking **Reset Columns**.</span></span>  
  
### <a name="format--fixed-width"></a><span data-ttu-id="1e1d3-156">형식 = 고정 폭</span><span class="sxs-lookup"><span data-stu-id="1e1d3-156">Format = Fixed Width</span></span>  
 <span data-ttu-id="1e1d3-157">**글꼴**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-157">**Font**</span></span>  
 <span data-ttu-id="1e1d3-158">미리 보기 데이터를 표시할 글꼴을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-158">Select the font in which to display the preview data.</span></span>  
  
 <span data-ttu-id="1e1d3-159">**원본 데이터 열**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-159">**Source data columns**</span></span>  
 <span data-ttu-id="1e1d3-160">세로 행 표식을 밀어 행 너비를 조정하고 미리 보기 창의 맨 위에 있는 눈금자를 클릭하여 열 너비를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-160">Adjust the width of the row by sliding the vertical row marker, and adjust the width of the columns by clicking the ruler at the top of the preview window</span></span>  
  
 <span data-ttu-id="1e1d3-161">**행 너비**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-161">**Row width**</span></span>  
 <span data-ttu-id="1e1d3-162">개별 열의 구분 기호를 추가하기 전에 행 길이를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-162">Specify the length of the row before adding delimiters for individual columns.</span></span> <span data-ttu-id="1e1d3-163">또는 미리 보기 창에서 세로줄을 끌어 행의 끝을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-163">Or, drag the vertical line in the preview window to mark the end of the row.</span></span> <span data-ttu-id="1e1d3-164">행 너비 값이 자동으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-164">The row width value is automatically updated.</span></span>  
  
 <span data-ttu-id="1e1d3-165">**열 다시 설정**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-165">**Reset Columns**</span></span>  
 <span data-ttu-id="1e1d3-166">**열 다시 설정**을 클릭하여 원래 열을 제외한 모든 열을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-166">Remove all but the original columns by clicking **Reset Columns**.</span></span>  
  
### <a name="format--ragged-right"></a><span data-ttu-id="1e1d3-167">형식 = 왼쪽 정렬</span><span class="sxs-lookup"><span data-stu-id="1e1d3-167">Format = Ragged Right</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1e1d3-168">왼쪽 정렬 파일에서는 마지막 열을 제외한 모든 열에 고정 폭이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-168">Ragged right files are those in which every column has a fixed width, except for the last column.</span></span> <span data-ttu-id="1e1d3-169">마지막 열은 행 구분 기호로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-169">It is delimited by the row delimiter.</span></span>  
  
 <span data-ttu-id="1e1d3-170">**글꼴**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-170">**Font**</span></span>  
 <span data-ttu-id="1e1d3-171">미리 보기 데이터를 표시할 글꼴을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-171">Select the font in which to display the preview data.</span></span>  
  
 <span data-ttu-id="1e1d3-172">**원본 데이터 열**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-172">**Source data columns**</span></span>  
 <span data-ttu-id="1e1d3-173">세로 행 표식을 밀어 행 너비를 조정하고 미리 보기 창의 맨 위에 있는 눈금자를 클릭하여 열 너비를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-173">Adjust the width of the row by sliding the vertical row marker, and adjust the width of the columns by clicking the ruler at the top of the preview window</span></span>  
  
 <span data-ttu-id="1e1d3-174">**행 구분 기호**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-174">**Row delimiter**</span></span>  
 <span data-ttu-id="1e1d3-175">사용 가능한 행 구분 기호의 목록에서 선택하거나 구분 기호 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-175">Select from the list of available row delimiters, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="1e1d3-176">값</span><span class="sxs-lookup"><span data-stu-id="1e1d3-176">Value</span></span>|<span data-ttu-id="1e1d3-177">Description</span><span class="sxs-lookup"><span data-stu-id="1e1d3-177">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1e1d3-178">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-178">**{CR}{LF}**</span></span>|<span data-ttu-id="1e1d3-179">행이 캐리지 리턴-줄 바꿈 조합으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-179">Rows are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="1e1d3-180">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-180">**{CR}**</span></span>|<span data-ttu-id="1e1d3-181">행이 캐리지 리턴으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-181">Rows are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="1e1d3-182">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-182">**{LF}**</span></span>|<span data-ttu-id="1e1d3-183">행이 줄 바꿈으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-183">Rows are delimited by a line feed.</span></span>|  
|<span data-ttu-id="1e1d3-184">**세미콜론 {;}**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-184">**Semicolon {;}**</span></span>|<span data-ttu-id="1e1d3-185">행이 세미콜론으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-185">Rows are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="1e1d3-186">**콜론 {:}**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-186">**Colon {:}**</span></span>|<span data-ttu-id="1e1d3-187">행이 콜론으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-187">Rows are delimited by a colon.</span></span>|  
|<span data-ttu-id="1e1d3-188">**쉼표 {,}**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-188">**Comma {,}**</span></span>|<span data-ttu-id="1e1d3-189">행이 쉼표로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-189">Rows are delimited by a comma.</span></span>|  
|<span data-ttu-id="1e1d3-190">**탭 {t}**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-190">**Tab {t}**</span></span>|<span data-ttu-id="1e1d3-191">행이 탭으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-191">Rows are delimited by a tab.</span></span>|  
|<span data-ttu-id="1e1d3-192">**세로 막대{&#124;}**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-192">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="1e1d3-193">행이 세로 막대로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-193">Rows are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="1e1d3-194">**열 다시 설정**</span><span class="sxs-lookup"><span data-stu-id="1e1d3-194">**Reset Columns**</span></span>  
 <span data-ttu-id="1e1d3-195">**열 다시 설정**을 클릭하여 원래 열을 제외한 모든 열을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1d3-195">Remove all but the original columns by clicking **Reset Columns**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e1d3-196">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1e1d3-196">See Also</span></span>  
 <span data-ttu-id="1e1d3-197">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="1e1d3-197">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="1e1d3-198">[다중 플랫 파일 연결 관리자 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="1e1d3-198">[Multiple Flat Files Connection Manager Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="1e1d3-199">[다중 플랫 파일 연결 관리자 편집기 &#40;고급 페이지&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="1e1d3-199">[Multiple Flat Files Connection Manager Editor &#40;Advanced Page&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="1e1d3-200">다중 플랫 파일 연결 관리자 편집기&#40;미리 보기 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="1e1d3-200">Multiple Flat Files Connection Manager Editor &#40;Preview Page&#41;</span></span>](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)  
  
  
