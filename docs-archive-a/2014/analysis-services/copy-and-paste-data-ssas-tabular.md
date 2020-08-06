---
title: 데이터 복사 및 붙여넣기 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.pastepreviewdb.f1
ms.assetid: 2f8d8b3d-810b-4c31-98f2-341015e13da8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 30df733377f3cb6f7583d380fbb8e92a0ea69e88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647992"
---
# <a name="copy-and-paste-data-ssas-tabular"></a><span data-ttu-id="0febc-102">데이터 복사 및 붙여넣기(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="0febc-102">Copy and Paste Data (SSAS Tabular)</span></span>
  <span data-ttu-id="0febc-103">외부 애플리케이션에서 테이블 형식의 데이터를 복사하여 모델 디자이너의 신규 또는 기존 테이블에 붙여넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-103">You can copy table data from external applications and paste it into a new or existing table in the model designer.</span></span> <span data-ttu-id="0febc-104">Excel 또는 Word에서 복사한 데이터와 같은 클립보드에서 붙여넣는 데이터는 HTML 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-104">The data that you paste from the Clipboard must be in HTML format, for example, data that is copied from Excel or Word.</span></span> <span data-ttu-id="0febc-105">모델 디자이너는 데이터 형식을 자동으로 감지하여 붙여넣은 데이터에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-105">The model designer will automatically detect and apply data types to the pasted data.</span></span> <span data-ttu-id="0febc-106">사용자가 직접 열의 데이터 형식이나 서식을 수정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-106">You can also manually modify the data type or display formatting of a column.</span></span>  
  
 <span data-ttu-id="0febc-107">데이터 원본에 연결된 테이블과 달리 붙여넣은 테이블에는 연결 이름 또는 원본 데이터 속성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-107">Unlike tables with a data source connection, pasted tables do not have a Connection Name or Source Data property.</span></span> <span data-ttu-id="0febc-108">붙여넣은 데이터는 Model.bim 파일에 보관됩니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-108">Pasted data is persisted in the Model.bim file.</span></span> <span data-ttu-id="0febc-109">프로젝트 또는 Model.bim 파일이 저장되면 붙여넣은 데이터도 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-109">When the project or Model.bim file is saved, the pasted data is also saved.</span></span>  
  
 <span data-ttu-id="0febc-110">모델이 배포될 때 모델의 처리 여부에 관계없이 붙여넣은 데이터도 함께 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-110">When a model is deployed, pasted data will also be deployed with it regardless if the model is processed with the deployment.</span></span>  
  
 <span data-ttu-id="0febc-111">이 항목의 섹션:</span><span class="sxs-lookup"><span data-stu-id="0febc-111">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="0febc-112">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="0febc-112">Prerequisites</span></span>](#bkmk_prerequisites)  
  
-   [<span data-ttu-id="0febc-113">데이터 붙여넣기</span><span class="sxs-lookup"><span data-stu-id="0febc-113">Paste Data</span></span>](#bkmk_paste_data)  
  
-   [<span data-ttu-id="0febc-114">붙여넣기 미리 보기 대화 상자</span><span class="sxs-lookup"><span data-stu-id="0febc-114">Paste Preview Dialog Box</span></span>](#bkmk_paste_preview)  
  
##  <a name="prerequisites"></a><a name="bkmk_prerequisites"></a> <span data-ttu-id="0febc-115">필수 조건</span><span class="sxs-lookup"><span data-stu-id="0febc-115">Prerequisites</span></span>  
 <span data-ttu-id="0febc-116">데이터를 붙여넣을 때 몇 가지 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-116">There are some restrictions when pasting data:</span></span>  
  
-   <span data-ttu-id="0febc-117">붙여넣은 테이블은 10,000개 이상의 행을 가질 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-117">Pasted tables cannot have more than 10,000 rows.</span></span>  
  
-   <span data-ttu-id="0febc-118">붙여넣은 테이블은 분할할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-118">Pasted tables cannot be partitioned.</span></span>  
  
-   <span data-ttu-id="0febc-119">붙여넣은 테이블은 DirectQuery 모드에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-119">Pasted tables are not supported in DirectQuery mode.</span></span>  
  
-   <span data-ttu-id="0febc-120">**추가하여 붙여넣기** 및 **바꿔서 붙여넣기** 옵션은 처음에 클립보드에서 데이터를 붙여넣는 방법으로 만든 테이블로 작업할 때만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-120">The **Paste Append** and **Paste Replace** options are only available when working with a table that was initially created by pasting data from the Clipboard.</span></span> <span data-ttu-id="0febc-121">가져온 데이터의 테이블에 **추가하여 붙여넣기** 또는 **바꿔서 붙여넣기** 를 사용하여 데이터 원본의 형식이 다른 데이터를 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-121">You cannot use **Paste Append** or **Paste Replace** to add data into a table of imported data from another type of data source.</span></span>  
  
-   <span data-ttu-id="0febc-122">**추가하여 붙여넣기** 또는 **바꿔서 붙여넣기**를 사용할 때는 새 데이터의 열 수가 원래 데이터의 열 수와 정확하게 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-122">When you use **Paste Append** or **Paste Replace**, the new data must contain exactly the same number of columns as the original data.</span></span> <span data-ttu-id="0febc-123">또한 붙여넣거나 추가하는 데이터 열이 대상 테이블의 데이터 열과 같거나 호환되는 데이터 형식인 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-123">Preferably, the columns of data that you paste or append should also be of the same or compatible data type as those in the destination table.</span></span> <span data-ttu-id="0febc-124">경우에 따라서는 다른 데이터 형식을 사용할 수도 있지만 **형식 불일치** 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-124">In some cases you can use a different data type, but a **Type mismatch** error may be displayed.</span></span>  
  
##  <a name="paste-data"></a><a name="bkmk_paste_data"></a> <span data-ttu-id="0febc-125">데이터 붙여넣기</span><span class="sxs-lookup"><span data-stu-id="0febc-125">Paste Data</span></span>  
  
#### <a name="to-paste-data-into-the-designer"></a><span data-ttu-id="0febc-126">디자이너에 데이터를 붙여넣으려면</span><span class="sxs-lookup"><span data-stu-id="0febc-126">To paste data into the designer</span></span>  
  
-   <span data-ttu-id="0febc-127">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]의 **편집** 메뉴를 클릭한 후 다음 중 하나를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-127">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Edit** menu, and then clicke of the following:</span></span>  
  
    -   <span data-ttu-id="0febc-128">클립보드의 내용을 새 테이블에 붙여넣으려면 **붙여넣기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-128">Click **Paste** to paste the contents of the Clipboard into a new table.</span></span>  
  
    -   <span data-ttu-id="0febc-129">클립보드의 내용을 선택한 테이블에 추가 행으로 붙여넣으려면 **추가하여 붙여넣기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-129">Click **Paste Append** to paste the contents of the Clipboard as additional rows into the selected table.</span></span> <span data-ttu-id="0febc-130">새 행이 테이블의 끝에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-130">The new rows will be added to the end of the table.</span></span>  
  
    -   <span data-ttu-id="0febc-131">선택한 테이블을 클립보드의 내용으로 바꾸려면 **바꿔서 붙여넣기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-131">Click **Paste Replace** to replace the selected table with the contents of the Clipboard.</span></span> <span data-ttu-id="0febc-132">모든 기존 열 머리글 이름이 테이블에서 유지되고 관계가 보존됩니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-132">All existing column header names will remain in the table, and relationships are preserved.</span></span>  
  
##  <a name="paste-preview-dialog-box"></a><a name="bkmk_paste_preview"></a><span data-ttu-id="0febc-133">붙여넣기 미리 보기 대화 상자</span><span class="sxs-lookup"><span data-stu-id="0febc-133">Paste Preview Dialog Box</span></span>  
 <span data-ttu-id="0febc-134">**붙여넣기 미리 보기** 대화 상자에서는 디자이너 창에 복사할 데이터를 미리 보고 데이터가 올바르게 복사되는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-134">The **Paste Preview** dialog box enables you to see a preview of data that is copied into the designer window and to ensure that the data is copied correctly.</span></span> <span data-ttu-id="0febc-135">이 대화 상자를 열려면 HTML 형식의 테이블 기반 데이터를 클립보드에 복사하고 디자이너에서 **편집** 메뉴를 클릭한 다음 **붙여넣기**, **추가하여 붙여넣기**또는 **바꿔서 붙여넣기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-135">To access this dialog box, copy table-based data in the HTML format to the clipboard, and then in the designer, click on the **Edit** menu, and then click **Paste**, **Paste Append**, or **Paste Replace**.</span></span> <span data-ttu-id="0febc-136">**추가하여 붙여넣기** 및 **바꿔서 붙여넣기** 옵션은 클립보드에서 복사하여 붙여넣는 방법으로 만든 테이블의 데이터를 추가하거나 바꿀 때만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-136">The **Paste Append** and **Paste Replace** options are only available when you add or replace data in a table that was created by copying and pasting from the Clipboard.</span></span> <span data-ttu-id="0febc-137">**추가하여 붙여넣기** 또는 **바꿔서 붙여넣기** 를 사용하여 가져온 데이터의 테이블에 데이터를 추가할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-137">You cannot use **Paste Append** or **Paste Replace** to add data into a table of imported data.</span></span>  
  
 <span data-ttu-id="0febc-138">이 대화 상자의 옵션은 데이터를 완전히 새 테이블에 붙여넣는지, 데이터를 기존 테이블에 붙여넣고 기존 데이터를 새 데이터로 바꾸는지, 데이터를 기존 테이블에 추가하는지에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-138">The options for this dialog box are different depending on whether you paste data into a completely new table, paste data into an existing table and then replace the existing data with the new data, or whether you append data to an existing table.</span></span>  
  
### <a name="paste-to-new-table"></a><span data-ttu-id="0febc-139">새 테이블에 붙여넣기</span><span class="sxs-lookup"><span data-stu-id="0febc-139">Paste to New Table</span></span>  
 <span data-ttu-id="0febc-140">**테이블 이름**</span><span class="sxs-lookup"><span data-stu-id="0febc-140">**Table name**</span></span>  
 <span data-ttu-id="0febc-141">디자이너에서 만들 테이블의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-141">Specify the name of the table that will be created in the designer.</span></span>  
  
 <span data-ttu-id="0febc-142">**붙여넣을 데이터**</span><span class="sxs-lookup"><span data-stu-id="0febc-142">**Data to be pasted**</span></span>  
 <span data-ttu-id="0febc-143">대상 테이블에 추가할 클립보드 내용의 예제를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-143">Shows a sample of the Clipboard contents that will be added to the destination table.</span></span>  
  
### <a name="paste-append"></a><span data-ttu-id="0febc-144">추가하여 붙여넣기</span><span class="sxs-lookup"><span data-stu-id="0febc-144">Paste Append</span></span>  
 <span data-ttu-id="0febc-145">**테이블의 기존 데이터**</span><span class="sxs-lookup"><span data-stu-id="0febc-145">**Existing data in the table**</span></span>  
 <span data-ttu-id="0febc-146">열, 데이터 형식 등을 확인할 수 있도록 테이블의 기존 데이터 예제를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-146">Shows a sample of the existing data in the table so that you can verify the columns, data types, etc.</span></span>  
  
 <span data-ttu-id="0febc-147">**붙여넣을 데이터**</span><span class="sxs-lookup"><span data-stu-id="0febc-147">**Data to be pasted**</span></span>  
 <span data-ttu-id="0febc-148">클립보드 내용의 예제를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-148">Shows a sample of the Clipboard contents.</span></span> <span data-ttu-id="0febc-149">기존 데이터에 이 데이터가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-149">The existing data will be appended by this data.</span></span>  
  
### <a name="paste-replace"></a><span data-ttu-id="0febc-150">바꿔서 붙여넣기</span><span class="sxs-lookup"><span data-stu-id="0febc-150">Paste Replace</span></span>  
 <span data-ttu-id="0febc-151">**테이블의 기존 데이터**</span><span class="sxs-lookup"><span data-stu-id="0febc-151">**Existing data in the table**</span></span>  
 <span data-ttu-id="0febc-152">열, 데이터 형식 등을 확인할 수 있도록 테이블의 기존 데이터 예제를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-152">Shows a sample of the existing data in the table so that you can verify the columns, data types, etc.</span></span>  
  
 <span data-ttu-id="0febc-153">**붙여넣을 데이터**</span><span class="sxs-lookup"><span data-stu-id="0febc-153">**Data to be pasted**</span></span>  
 <span data-ttu-id="0febc-154">클립보드 내용의 예제를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-154">Shows a sample of the Clipboard contents.</span></span> <span data-ttu-id="0febc-155">대상 테이블의 기존 데이터가 삭제되고 새 행이 테이블에 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="0febc-155">The existing data in the destination table will be deleted and the new rows will be inserted into the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0febc-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0febc-156">See Also</span></span>  
 <span data-ttu-id="0febc-157">[SSAS 테이블 형식&#41;&#40;데이터 가져오기](import-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="0febc-157">[Import Data &#40;SSAS Tabular&#41;](import-data-ssas-tabular.md) </span></span>  
 <span data-ttu-id="0febc-158">[SSAS 테이블 형식&#41;&#40;지원 되는 데이터 원본](tabular-models/data-sources-supported-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="0febc-158">[Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="0febc-159">열 데이터 형식 설정&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="0febc-159">Set the Data Type of a Column &#40;SSAS Tabular&#41;</span></span>](tabular-models/set-the-data-type-of-a-column-ssas-tabular.md)  
  
  
