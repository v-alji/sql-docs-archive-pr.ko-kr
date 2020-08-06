---
title: 배경 이미지 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c777fefb-8695-44a7-b5cd-a18c587583f2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d7bc15e1b063a73c463cdb1e7e99075af2a3dce9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739388"
---
# <a name="add-a-background-image-report-builder-and-ssrs"></a><span data-ttu-id="3c4ec-102">배경 이미지 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="3c4ec-102">Add a Background Image (Report Builder and SSRS)</span></span>
  <span data-ttu-id="3c4ec-103">사각형, 입력란, 목록, 행렬, 테이블 및 차트의 일부분과 같은 보고서 항목이나 페이지 머리글, 페이지 바닥글 또는 보고서 본문과 같은 보고서 섹션에 배경 이미지를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c4ec-103">You can add a background image to a report item such as a rectangle, text box, list, matrix, table, and some parts of a chart, or a report section such as the page header, page footer, or report body.</span></span> <span data-ttu-id="3c4ec-104">속성 창에 **BackgroundImage** 가 표시되는 보고서 디자인 화면의 모든 선택 항목에 대해 배경 이미지를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c4ec-104">You can define a background image for any selected item on the report design surface that displays **BackgroundImage** in the Properties pane.</span></span> <span data-ttu-id="3c4ec-105">배경 이미지는 다른 이미지와 마찬가지로 보고서 서버의 이미지, 데이터 세트 필드의 이미지 또는 보고서 정의에 포함된 이미지에 대한 URL일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c4ec-105">Like other images, the background image can be a URL to an image on the report server, an image from a dataset field, or an image embedded in the report definition.</span></span> <span data-ttu-id="3c4ec-106">보고서에 포함된 이미지를 사용하려면 먼저 보고서 정의에 이미지를 추가해야만 디자인 화면에 이미지를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c4ec-106">To use an image embedded in the report, you must first add the image to the report definition before you can add the image to the design surface.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-embed-an-image-in-the-report-definition"></a><span data-ttu-id="3c4ec-107">보고서 정의에 이미지를 포함하려면</span><span class="sxs-lookup"><span data-stu-id="3c4ec-107">To embed an image in the report definition</span></span>  
  
1.  <span data-ttu-id="3c4ec-108">보고서 데이터 창에서 **이미지** 노드를 마우스 오른쪽 단추로 클릭한 다음 **이미지 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3c4ec-108">In the Report Data pane, right-click the **Images** node, and then click **Add Image**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3c4ec-109">보고서 데이터 창이 표시되지 않는 경우 **보기** 탭에서 **보고서 데이터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3c4ec-109">If the Report Data pane is not visible, on the **View** tab, click **Report Data**.</span></span>  
  
2.  <span data-ttu-id="3c4ec-110">보고서 정의에 포함할 이미지를 탐색한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3c4ec-110">Navigate to the image you want to embed in your report definition, and then click **OK**.</span></span>  
  
### <a name="to-add-a-background-image"></a><span data-ttu-id="3c4ec-111">배경 이미지를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="3c4ec-111">To add a background image</span></span>  
  
1.  <span data-ttu-id="3c4ec-112">보고서 디자인 뷰에서 배경 이미지를 추가할 보고서 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3c4ec-112">In report design view, select the report item to which you want to add a background image.</span></span>  
  
2.  <span data-ttu-id="3c4ec-113">속성 창이 표시되지 않으면 **보기** 탭에서 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3c4ec-113">If the Properties pane is not visible, on the **View** tab, select **Properties**.</span></span>  
  
3.  <span data-ttu-id="3c4ec-114">속성 창에서 **BackgroundImage**를 확장하고 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3c4ec-114">In the Properties pane, expand **BackgroundImage**, and then do the following:</span></span>  
  
    -   <span data-ttu-id="3c4ec-115">포함 이미지의 경우</span><span class="sxs-lookup"><span data-stu-id="3c4ec-115">For an embedded image:</span></span>  
  
         <span data-ttu-id="3c4ec-116">**Source** 를 **Embedded**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c4ec-116">Set **Source** to **Embedded**.</span></span>  
  
         <span data-ttu-id="3c4ec-117">**값** 을 보고서에 포함된 이미지의 이름으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c4ec-117">Set **Value** to the name of an image that is embedded in the report.</span></span>  
  
    -   <span data-ttu-id="3c4ec-118">외부 이미지의 경우</span><span class="sxs-lookup"><span data-stu-id="3c4ec-118">For an external image:</span></span>  
  
         <span data-ttu-id="3c4ec-119">**Source** 를 **External**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c4ec-119">Set **Source** to **External**.</span></span>  
  
         <span data-ttu-id="3c4ec-120">**값** 을 이미지에 대한 올바른 경로로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c4ec-120">Set **Value** to a valid path to an image.</span></span> <span data-ttu-id="3c4ec-121">이미지는 기본 모드나 SharePoint 통합 모드에 있는 보고서 서버 또는 다른 웹 사이트에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c4ec-121">This can be on a report server in native mode or SharePoint integrated mode, or it can be on any other Web site.</span></span> <span data-ttu-id="3c4ec-122">자세한 내용은 [외부 이미지 추가&#40;보고서 작성기 및 SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3c4ec-122">For more information, see [Add an External Image &#40;Report Builder and SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md).</span></span>  
  
    -   <span data-ttu-id="3c4ec-123">보고서 항목이 연결된 데이터베이스의 필드에 포함되어 있는 이미지의 경우</span><span class="sxs-lookup"><span data-stu-id="3c4ec-123">For an image is that is contained in a field in the database to which the report item is connected:</span></span>  
  
         <span data-ttu-id="3c4ec-124">**Source** 를 **Database**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c4ec-124">Set **Source** to **Database**.</span></span>  
  
         <span data-ttu-id="3c4ec-125">**값**을 보고서 데이터 세트에 있는 필드의 이름으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c4ec-125">Set **Value** to the name of a field in the report dataset.</span></span> <span data-ttu-id="3c4ec-126">자세한 내용은 [데이터 바인딩된 이미지 추가&#40;보고서 작성기 및 SSRS&#41;](add-a-data-bound-image-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3c4ec-126">For more information, see [Add a Data-Bound Image &#40;Report Builder and SSRS&#41;](add-a-data-bound-image-report-builder-and-ssrs.md).</span></span>  
  
         <span data-ttu-id="3c4ec-127">**MIMEType** 또는 파일 형식의 경우 이미지에 해당하는 MIME 형식(예: .bmp)을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3c4ec-127">For **MIMEType**, or file format, select the appropriate MIME type for the image-for example, .bmp.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="3c4ec-128">MIMEType은 **Source** 속성을 **Database**로 설정한 경우에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c4ec-128">MIMEType applies only if the **Source** property is set to **Database**.</span></span> <span data-ttu-id="3c4ec-129">**원본** 속성을 **외부** 또는 **포함**으로 설정한 경우에는 **MIMEType** 값이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c4ec-129">If the **Source** property is set to **External** or **Embedded**, the value of **MIMEType** is ignored.</span></span>  
  
    -   <span data-ttu-id="3c4ec-130">**BackgroundRepeat**에 대해 **Default**, **Repeat**, **RepeatX**, or **RepeatY**또는 **Clip**식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3c4ec-130">For **BackgroundRepeat**, select an expression, **Default**, **Repeat**, **RepeatX**, or **RepeatY**, or **Clip**.</span></span>  
  
         <span data-ttu-id="3c4ec-131">차트의 배경 이미지에 대해 **BackgroundRepeat** 를 **Default**, **Repeat**, **Fit**및 **Clip**으로 설정할 수 있지만 **RepeatX** 나 **RepeatY**로 설정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3c4ec-131">For background images in a chart, **BackgroundRepeat** can be set to **Default**, **Repeat**, **Fit**, and **Clip**, but not **RepeatX** or **RepeatY**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c4ec-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3c4ec-132">See Also</span></span>  
 <span data-ttu-id="3c4ec-133">[이미지&#40;보고서 작성기 및 SSRS&#41;](images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3c4ec-133">[Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="3c4ec-134">이미지 속성 대화 상자, 일반&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3c4ec-134">Image Properties Dialog Box, General &#40;Report Builder and SSRS&#41;</span></span>](../image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
