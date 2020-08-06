---
title: 다중 플랫 파일 연결 관리자 편집기 (일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.multifile.general.f1
helpviewer_keywords:
- Multiple Flat Files Connection Manager Editor
ms.assetid: 00129d43-2772-413b-bdf8-ac5de81cf4a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f30a422794723f216d30e05f0750fb1e974e0920
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736526"
---
# <a name="multiple-flat-files-connection-manager-editor-general-page"></a><span data-ttu-id="1888b-102">다중 플랫 파일 연결 관리자 편집기(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="1888b-102">Multiple Flat Files Connection Manager Editor (General Page)</span></span>
  <span data-ttu-id="1888b-103">**다중 플랫 파일 연결 관리자 편집기** 대화 상자의 **일반** 페이지를 사용하여 데이터 형식이 같은 파일 그룹을 선택하고 데이터 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-103">Use the **General** page of the **Multiple Flat Files Connection Manager Editor** dialog box to select a group of files that have the same data format, and to specify their data format.</span></span> <span data-ttu-id="1888b-104">다중 플랫 파일 연결 기능을 사용하면 패키지를 같은 형식의 텍스트 파일 그룹에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-104">A multiple flat files connection enables a package to connect to a group of text files that have the same format.</span></span>  
  
 <span data-ttu-id="1888b-105">다중 플랫 파일 연결 관리자에 대한 자세한 내용은 [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1888b-105">To learn more about the Multiple Flat Files connection manager, see [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="1888b-106">옵션</span><span class="sxs-lookup"><span data-stu-id="1888b-106">Options</span></span>  
 <span data-ttu-id="1888b-107">**연결 관리자 이름**</span><span class="sxs-lookup"><span data-stu-id="1888b-107">**Connection manager name**</span></span>  
 <span data-ttu-id="1888b-108">워크플로에서의 다중 플랫 파일 연결에 대한 고유 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-108">Provide a unique name for the Multiple Flat Files connection in the workflow.</span></span> <span data-ttu-id="1888b-109">제공한 이름은 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-109">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="1888b-110">**설명**</span><span class="sxs-lookup"><span data-stu-id="1888b-110">**Description**</span></span>  
 <span data-ttu-id="1888b-111">연결에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-111">Describe the connection.</span></span> <span data-ttu-id="1888b-112">해당 연결의 용도를 설명하여 패키지를 이해하기 쉽고 유지 관리하기 편하도록 만드는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-112">As a best practice, describe the connection in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="1888b-113">**파일 이름**</span><span class="sxs-lookup"><span data-stu-id="1888b-113">**File names**</span></span>  
 <span data-ttu-id="1888b-114">다중 플랫 파일 연결에 사용할 경로와 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-114">Type the path and file names to use in the Multiple Flat Files connection.</span></span> <span data-ttu-id="1888b-115">"C:\\*.txt"와 같이 와일드카드 문자를 사용하거나 파일 이름을 구분하는 세로줄 문자(|)를 사용하여 다중 파일을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-115">You can specify multiple files by using wildcard characters, as in the example "C:\\*.txt", or by using the vertical pipe character (|) to separate multiple file names.</span></span> <span data-ttu-id="1888b-116">모든 파일의 데이터 형식은 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-116">All files must have the same data format.</span></span>  
  
 <span data-ttu-id="1888b-117">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="1888b-117">**Browse**</span></span>  
 <span data-ttu-id="1888b-118">다중 플랫 파일 연결에 사용할 파일 이름을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-118">Browse the file names to use in the Multiple Flat Files connection.</span></span> <span data-ttu-id="1888b-119">여러 파일을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-119">You can select multiple files.</span></span> <span data-ttu-id="1888b-120">모든 파일의 데이터 형식은 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-120">All files must have the same data format.</span></span>  
  
 <span data-ttu-id="1888b-121">**로캘**</span><span class="sxs-lookup"><span data-stu-id="1888b-121">**Locale**</span></span>  
 <span data-ttu-id="1888b-122">정렬 순서와 날짜 및 시간 변환 정보를 제공하는 지역을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-122">Specify the location to provide information for ordering and for date and time conversion.</span></span>  
  
 <span data-ttu-id="1888b-123">**유니코드**</span><span class="sxs-lookup"><span data-stu-id="1888b-123">**Unicode**</span></span>  
 <span data-ttu-id="1888b-124">유니코드를 사용할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-124">Indicate whether to use Unicode.</span></span> <span data-ttu-id="1888b-125">유니코드를 사용하면 코드 페이지를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-125">Using Unicode precludes specifying a code page.</span></span>  
  
 <span data-ttu-id="1888b-126">**코드 페이지**</span><span class="sxs-lookup"><span data-stu-id="1888b-126">**Code page**</span></span>  
 <span data-ttu-id="1888b-127">비유니코드 텍스트에 대한 코드 페이지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-127">Specify the code page for non-Unicode text.</span></span>  
  
 <span data-ttu-id="1888b-128">**형식**</span><span class="sxs-lookup"><span data-stu-id="1888b-128">**Format**</span></span>  
 <span data-ttu-id="1888b-129">구분 기호로 분리됨, 고정 폭, 왼쪽 정렬 중 어떤 서식을 사용할지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-129">Indicate whether to use delimited, fixed width, or ragged right formatting.</span></span> <span data-ttu-id="1888b-130">모든 파일의 데이터 형식은 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-130">All files must have the same data format.</span></span>  
  
|<span data-ttu-id="1888b-131">값</span><span class="sxs-lookup"><span data-stu-id="1888b-131">Value</span></span>|<span data-ttu-id="1888b-132">Description</span><span class="sxs-lookup"><span data-stu-id="1888b-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1888b-133">구분됨</span><span class="sxs-lookup"><span data-stu-id="1888b-133">Delimited</span></span>|<span data-ttu-id="1888b-134">**열** 페이지에 지정된 구분 기호로 열을 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-134">Columns are separated by delimiters, specified on the **Columns** page.</span></span>|  
|<span data-ttu-id="1888b-135">고정 폭</span><span class="sxs-lookup"><span data-stu-id="1888b-135">Fixed width</span></span>|<span data-ttu-id="1888b-136">열에 고정 폭이 지정됩니다. 폭은 **열** 페이지의 표식 줄을 끌어 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-136">Columns have a fixed width, specified by dragging marker lines on the **Columns** page.</span></span>|  
|<span data-ttu-id="1888b-137">왼쪽 정렬</span><span class="sxs-lookup"><span data-stu-id="1888b-137">Ragged right</span></span>|<span data-ttu-id="1888b-138">왼쪽 정렬 파일은 마지막 열을 제외한 모든 열에 고정 폭이 지정된 파일입니다. 마지막 열은 **열** 페이지에서 지정한 행 구분 기호로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-138">Ragged right files are files in which every column has a fixed width, except for the last column, which is delimited by the row delimiter, specified on the **Columns** page.</span></span>|  
  
 <span data-ttu-id="1888b-139">**텍스트 한정자**</span><span class="sxs-lookup"><span data-stu-id="1888b-139">**Text qualifier**</span></span>  
 <span data-ttu-id="1888b-140">사용할 텍스트 한정자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-140">Specify the text qualifier to use.</span></span> <span data-ttu-id="1888b-141">예를 들어 텍스트 필드를 따옴표로 묶도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-141">For example, you can specify to enclose text with quotation marks.</span></span>  
  
 <span data-ttu-id="1888b-142">**머리글 행 구분 기호**</span><span class="sxs-lookup"><span data-stu-id="1888b-142">**Header row delimiter**</span></span>  
 <span data-ttu-id="1888b-143">구분 기호 목록에서 머리글 행 구분 기호를 선택하거나 구분 기호 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-143">Select from the list of delimiters for header rows, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="1888b-144">값</span><span class="sxs-lookup"><span data-stu-id="1888b-144">Value</span></span>|<span data-ttu-id="1888b-145">설명</span><span class="sxs-lookup"><span data-stu-id="1888b-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1888b-146">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="1888b-146">**{CR}{LF}**</span></span>|<span data-ttu-id="1888b-147">머리글 행을 캐리지 리턴-줄 바꿈 조합으로 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-147">The header row is delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="1888b-148">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="1888b-148">**{CR}**</span></span>|<span data-ttu-id="1888b-149">머리글 행을 캐리지 리턴으로 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-149">The header row is delimited by a carriage return.</span></span>|  
|<span data-ttu-id="1888b-150">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="1888b-150">**{LF}**</span></span>|<span data-ttu-id="1888b-151">머리글 행을 줄 바꿈으로 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-151">The header row is delimited by a line feed.</span></span>|  
|<span data-ttu-id="1888b-152">**세미콜론 {;}**</span><span class="sxs-lookup"><span data-stu-id="1888b-152">**Semicolon {;}**</span></span>|<span data-ttu-id="1888b-153">머리글 행을 세미콜론으로 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-153">The header row is delimited by a semicolon.</span></span>|  
|<span data-ttu-id="1888b-154">**콜론 {:}**</span><span class="sxs-lookup"><span data-stu-id="1888b-154">**Colon {:}**</span></span>|<span data-ttu-id="1888b-155">머리글 행을 콜론으로 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-155">The header row is delimited by a colon.</span></span>|  
|<span data-ttu-id="1888b-156">**쉼표 {,}**</span><span class="sxs-lookup"><span data-stu-id="1888b-156">**Comma {,}**</span></span>|<span data-ttu-id="1888b-157">머리글 행을 쉼표로 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-157">The header row is delimited by a comma.</span></span>|  
|<span data-ttu-id="1888b-158">**탭 {t}**</span><span class="sxs-lookup"><span data-stu-id="1888b-158">**Tab {t}**</span></span>|<span data-ttu-id="1888b-159">머리글 행을 탭으로 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-159">The header row is delimited by a tab.</span></span>|  
|<span data-ttu-id="1888b-160">**세로 막대{&#124;}**</span><span class="sxs-lookup"><span data-stu-id="1888b-160">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="1888b-161">머리글 행을 세로 막대로 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-161">The header row is delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="1888b-162">**건너뛸 머리글 행**</span><span class="sxs-lookup"><span data-stu-id="1888b-162">**Header rows to skip**</span></span>  
 <span data-ttu-id="1888b-163">건너뛸 머리글 행 수를 지정합니다(있는 경우).</span><span class="sxs-lookup"><span data-stu-id="1888b-163">Specify the number of header rows to skip, if any.</span></span>  
  
 <span data-ttu-id="1888b-164">**첫 번째 데이터 행의 열 이름**</span><span class="sxs-lookup"><span data-stu-id="1888b-164">**Column names in the first data row**</span></span>  
 <span data-ttu-id="1888b-165">첫 번째 데이터 행에 열 이름을 제공할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1888b-165">Indicate whether to expect or provide column names in the first data row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1888b-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1888b-166">See Also</span></span>  
 <span data-ttu-id="1888b-167">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="1888b-167">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="1888b-168">[다중 플랫 파일 연결 관리자 편집기 &#40;열 페이지&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="1888b-168">[Multiple Flat Files Connection Manager Editor &#40;Columns Page&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-columns-page.md) </span></span>  
 <span data-ttu-id="1888b-169">[다중 플랫 파일 연결 관리자 편집기 &#40;고급 페이지&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="1888b-169">[Multiple Flat Files Connection Manager Editor &#40;Advanced Page&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="1888b-170">다중 플랫 파일 연결 관리자 편집기&#40;미리 보기 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="1888b-170">Multiple Flat Files Connection Manager Editor &#40;Preview Page&#41;</span></span>](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)  
  
  
