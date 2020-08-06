---
title: 플랫 파일에 연결 (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connflatfile.f1
ms.assetid: a365991e-eded-4cd8-89c0-0daf6d658d15
author: minewiskan
ms.author: owend
ms.openlocfilehash: e6bee3c8f7f4b255e6985e8d783365bc8a47599e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648021"
---
# <a name="connect-to-a-flat-file-ssas"></a><span data-ttu-id="b8066-102">플랫 파일에 연결(SSAS)</span><span class="sxs-lookup"><span data-stu-id="b8066-102">Connect to a Flat File (SSAS)</span></span>
  <span data-ttu-id="b8066-103">**테이블 가져오기 마법사** 의 이 페이지를 사용하면 플랫 파일(.txt), 탭으로 구분된 파일(.tab) 또는 쉼표로 구분된 파일(.csv)에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8066-103">This page of the **Table Import Wizard** enables you to connect to a flat file (.txt), tab-separated file (.tab), or a comma-separated file (.csv).</span></span> <span data-ttu-id="b8066-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 마법사에 액세스하려면 **모델** 메뉴에서 **데이터 원본에서 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8066-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="b8066-105">플랫 파일에 연결하려면 컴퓨터에 적절한 ACE 공급자를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8066-105">To connect to a flat file, you must have the ACE provider installed on your computer.</span></span> <span data-ttu-id="b8066-106">자세한 내용은 [지원되는 데이터 원본&#40;SSAS 테이블 형식&#41;](tabular-models/data-sources-supported-ssas-tabular.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b8066-106">For more information, see [Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b8066-107">이 페이지에서 파일을 선택하는 경우 현재 사용자의 자격 증명이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8066-107">The credentials of the current user are used when selecting a file in this page.</span></span> <span data-ttu-id="b8066-108">하지만 가장 정보 페이지에 지정된 사용자에게 선택한 파일을 읽을 수 있는 권한이 없는 경우에는 가져오기 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="b8066-108">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected file.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="b8066-109">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="b8066-109">UI element list</span></span>  
 <span data-ttu-id="b8066-110">**연결 이름**</span><span class="sxs-lookup"><span data-stu-id="b8066-110">**Friendly connection name**</span></span>  
 <span data-ttu-id="b8066-111">이 데이터 원본 연결의 고유 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b8066-111">Type a unique name for this data source connection.</span></span> <span data-ttu-id="b8066-112">이 이름은 반드시 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8066-112">This is a required field.</span></span>  
  
 <span data-ttu-id="b8066-113">**파일 경로**</span><span class="sxs-lookup"><span data-stu-id="b8066-113">**File Path**</span></span>  
 <span data-ttu-id="b8066-114">파일의 전체 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8066-114">Specify a full path for the file.</span></span>  
  
 <span data-ttu-id="b8066-115">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="b8066-115">**Browse**</span></span>  
 <span data-ttu-id="b8066-116">파일을 사용할 수 있는 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="b8066-116">Navigate to a location where a file is available.</span></span>  
  
 <span data-ttu-id="b8066-117">**열 구분 기호**</span><span class="sxs-lookup"><span data-stu-id="b8066-117">**Column Separator**</span></span>  
 <span data-ttu-id="b8066-118">사용 가능한 열 구분 기호의 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b8066-118">Select from a list of available column separators.</span></span> <span data-ttu-id="b8066-119">텍스트에 거의 사용되지 않는 구분 기호를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b8066-119">Choose a separator that is not likely to occur in the text.</span></span>  
  
|<span data-ttu-id="b8066-120">값</span><span class="sxs-lookup"><span data-stu-id="b8066-120">Value</span></span>|<span data-ttu-id="b8066-121">Description</span><span class="sxs-lookup"><span data-stu-id="b8066-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b8066-122">탭(t)</span><span class="sxs-lookup"><span data-stu-id="b8066-122">Tab (t)</span></span>|<span data-ttu-id="b8066-123">열이 탭(t)으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8066-123">Columns are separated by a tab (t).</span></span>|  
|<span data-ttu-id="b8066-124">쉼표(,)</span><span class="sxs-lookup"><span data-stu-id="b8066-124">Comma (,)</span></span>|<span data-ttu-id="b8066-125">열이 쉼표(,)로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8066-125">Columns are separated by a comma (,).</span></span>|  
|<span data-ttu-id="b8066-126">세미콜론(;)</span><span class="sxs-lookup"><span data-stu-id="b8066-126">Semicolon (;)</span></span>|<span data-ttu-id="b8066-127">열이 세미콜론(;)으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8066-127">Columns are separated by a semicolon (;).</span></span>|  
|<span data-ttu-id="b8066-128">공백( )</span><span class="sxs-lookup"><span data-stu-id="b8066-128">Space ( )</span></span>|<span data-ttu-id="b8066-129">열이 공백( )으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8066-129">Columns are separated by a space ( ).</span></span>|  
|<span data-ttu-id="b8066-130">콜론(:)</span><span class="sxs-lookup"><span data-stu-id="b8066-130">Colon (:)</span></span>|<span data-ttu-id="b8066-131">열이 콜론(:)으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8066-131">Columns are separated by a colon (:).</span></span>|  
|<span data-ttu-id="b8066-132">세로 막대(&#124;)</span><span class="sxs-lookup"><span data-stu-id="b8066-132">Vertical Bar (&#124;)</span></span>|<span data-ttu-id="b8066-133">열이 세로 막대(&#124;)로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8066-133">Columns are separated by a vertical bar (&#124;).</span></span>|  
  
 <span data-ttu-id="b8066-134">**고급**</span><span class="sxs-lookup"><span data-stu-id="b8066-134">**Advanced**</span></span>  
 <span data-ttu-id="b8066-135">플랫 파일에 대한 인코딩 및 로캘 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8066-135">Specify the encoding and locale options for the flat file.</span></span>  
  
 <span data-ttu-id="b8066-136">**첫 행을 열 머리글로 사용**</span><span class="sxs-lookup"><span data-stu-id="b8066-136">**Use first row as column headers**</span></span>  
 <span data-ttu-id="b8066-137">첫 번째 데이터 행을 대상 테이블의 열 머리글로 사용할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8066-137">Specify whether to use the first data row as the column headers of the destination table.</span></span>  
  
 <span data-ttu-id="b8066-138">**데이터 미리 보기**</span><span class="sxs-lookup"><span data-stu-id="b8066-138">**Data preview**</span></span>  
 <span data-ttu-id="b8066-139">선택한 파일의 데이터를 미리 보고 다음 옵션을 사용하여 데이터 가져오기를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8066-139">Preview the data in the selected file, and use the following options to modify the data import.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b8066-140">파일의 첫 50행만 이 미리 보기에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8066-140">Only the first 50 rows in the file are displayed in this preview.</span></span>  
  
|<span data-ttu-id="b8066-141">옵션</span><span class="sxs-lookup"><span data-stu-id="b8066-141">Option</span></span>|<span data-ttu-id="b8066-142">Description</span><span class="sxs-lookup"><span data-stu-id="b8066-142">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b8066-143">**열 머리글의 확인란**</span><span class="sxs-lookup"><span data-stu-id="b8066-143">**Checkbox in the column header**</span></span>|<span data-ttu-id="b8066-144">데이터 가져오기에 열을 포함하려면 이 확인란을 선택하고,</span><span class="sxs-lookup"><span data-stu-id="b8066-144">Select the checkbox to include the column in the data import.</span></span> <span data-ttu-id="b8066-145">데이터 가져오기에서 열을 제거하려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="b8066-145">Clear the checkbox to remove the column from the data import.</span></span>|  
|<span data-ttu-id="b8066-146">**열 머리글의 아래쪽 화살표 단추**</span><span class="sxs-lookup"><span data-stu-id="b8066-146">**Down-arrow button in the column header**</span></span>|<span data-ttu-id="b8066-147">열의 데이터를 정렬하고 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="b8066-147">Sort and filter data in the column.</span></span>|  
  
 <span data-ttu-id="b8066-148">**행 필터 지우기**</span><span class="sxs-lookup"><span data-stu-id="b8066-148">**Clear Row Filters**</span></span>  
 <span data-ttu-id="b8066-149">열의 데이터에 적용된 모든 필터를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="b8066-149">Remove all filters that were applied to the data in the columns.</span></span>  
  
  
