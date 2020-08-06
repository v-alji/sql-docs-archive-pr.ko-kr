---
title: 채우기 대화 상자 (보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.reportbody.fill.f1
- "10065"
- "10501"
- sql12.rtp.rptdesigner.shared.filldv.f1
- sql12.rtp.rptdesigner.rectangleproperties.fill.f1
- "10064"
- sql12.rtp.rptdesigner.textboxproperties.fill.f1
- "10124"
ms.assetid: 93a91d02-d558-4a0e-8d17-3fdf21e208d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ae7f2b05d4d108c77f1dcae9ce7fefe5073e2522
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651504"
---
# <a name="fill-dialog-box-report-builder-and-ssrs"></a><span data-ttu-id="86318-102">채우기 대화 상자(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="86318-102">Fill Dialog Box (Report Builder and SSRS)</span></span>
  <span data-ttu-id="86318-103">**채우기** 탭에서 데이터 영역이나 입력란 내의 단일 셀 또는 여러 셀의 배경에 대한 색 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86318-103">On the **Fill** tab, you can specify color options for the background of a single cell or multiple cells within a data region or a text box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="86318-104">옵션</span><span class="sxs-lookup"><span data-stu-id="86318-104">Options</span></span>  
 <span data-ttu-id="86318-105">**채우기 색**</span><span class="sxs-lookup"><span data-stu-id="86318-105">**Fill Color**</span></span>  
 <span data-ttu-id="86318-106">사각형의 채우기 색을 선택하려면 색 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="86318-106">Click the color button to select a fill color for the rectangle.</span></span> <span data-ttu-id="86318-107">식을 편집하려면 **식**_(fx)_ 단추를 클릭합니다. 식은 RGB 색을 나타내는 16진수 값이거나 **식** 대화 상자에 제공되는 미리 정의된 색 이름 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86318-107">Click the **Expression**_(fx)_ button to edit the expression, which can be a hexadecimal value for the RGB color or one of the predefined color names that are provided in the **Expression** dialog box.</span></span> <span data-ttu-id="86318-108">미리 정의된 색 목록을 보려면 **항목** 창에서 **웹**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="86318-108">To see a list of predefined colors, in the **Item** pane, select **Web**.</span></span> <span data-ttu-id="86318-109">**제목** 창에 나열된 색 이름을 식 텍스트 창에 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86318-109">The color names listed in the **Title** pane can be typed into the expression text pane.</span></span> <span data-ttu-id="86318-110">색 이름을 입력할 때 등호(=) 또는 큰따옴표("")를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="86318-110">Do not use an equal sign (=) or quotation marks ("") when typing the color name.</span></span>  
  
 <span data-ttu-id="86318-111">**이미지 원본 선택**</span><span class="sxs-lookup"><span data-stu-id="86318-111">**Select the image source**</span></span>  
 <span data-ttu-id="86318-112">이미지를 저장할 위치를 나타내어 보고서를 렌더링할 때 보고서 처리기에서 이미지를 표시할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="86318-112">Indicate where the image is stored so that when the report is rendered, the report processor can display it.</span></span>  
  
-   <span data-ttu-id="86318-113">**외부** 보고서 서버 또는 웹 서버에서 이미지를 파일로 유지하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="86318-113">**External** Choose this option when you want the image to continue to exist as a file on a report server or Web server.</span></span>  
  
-   <span data-ttu-id="86318-114">**포함** 이미지를 보고서에 포함하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="86318-114">**Embedded** Choose this option when you want to embed the image into the report.</span></span>  
  
-   <span data-ttu-id="86318-115">**데이터베이스** 보고서에 포함할 이미지를 나타내는 데이터베이스 필드 이름을 포함하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="86318-115">**Database** Choose this option when you want to include a database field name that represents the images that you want to include in your report.</span></span>  
  
 <span data-ttu-id="86318-116">**이 이미지 사용**</span><span class="sxs-lookup"><span data-stu-id="86318-116">**Use this image**</span></span>  
 <span data-ttu-id="86318-117">**포함** 또는 **외부** 옵션을 선택하면 이 옵션이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="86318-117">This option appears when you select the **Embedded** or **External** option.</span></span>  
  
 <span data-ttu-id="86318-118">이미지를 포함하려는 경우 드롭다운 목록에서 보고서에 추가할 그림을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="86318-118">If you are embedding the image, choose the picture that you want to add to the report from the drop-down list.</span></span> <span data-ttu-id="86318-119">**가져오기** 를 클릭하여 드롭다운 목록에 이미지를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="86318-119">Click **Import** to add the image to the drop-down list.</span></span> <span data-ttu-id="86318-120">**데이터** 창에 이미지를 추가한 경우 **포함** 을 선택한 다음 드롭다운 목록에서 해당 이미지를 선택하여 이미지를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86318-120">If you added an image to the **Data** pane, you can select that image by choosing **Embedded** and then selecting the image from the drop-down list.</span></span>  
  
 <span data-ttu-id="86318-121">**외부** 옵션을 선택할 경우 이미지의 URL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="86318-121">If you select the **External** option, type the URL of the image.</span></span> <span data-ttu-id="86318-122">기본 모드로 구성 된 보고서 서버에 게시 된 보고서의 경우 전체 경로나 상대 경로를 사용 합니다 (예: http:// *\<servername>* /images/image1.jpg).</span><span class="sxs-lookup"><span data-stu-id="86318-122">For a report published to a report server configured for native mode, use a full or relative path (for example, http://*\<servername>*/images/image1.jpg).</span></span> <span data-ttu-id="86318-123">SharePoint 통합 모드로 구성 된 보고서 서버에 게시 된 보고서의 경우 정규화 된 URL (예: http:// *\<SharePointservername>/\<site>* /Documents/images/image1.jpg)을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="86318-123">For a report published to a report server configured in SharePoint integrated mode, use a fully qualified URL (for example, http://*\<SharePointservername>/\<site>*/Documents/images/image1.jpg).</span></span>  
  
 <span data-ttu-id="86318-124">**가져오기**</span><span class="sxs-lookup"><span data-stu-id="86318-124">**Import**</span></span>  
 <span data-ttu-id="86318-125">**포함**을 선택하면 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86318-125">Available when you select **Embedded**.</span></span> <span data-ttu-id="86318-126">**이 이미지 사용** 드롭다운 목록에 이미지를 추가하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="86318-126">Click to add an image to the **Use this image** drop-down list.</span></span>  
  
 <span data-ttu-id="86318-127">**이 필드 사용**</span><span class="sxs-lookup"><span data-stu-id="86318-127">**Use this field**</span></span>  
 <span data-ttu-id="86318-128">**데이터베이스**를 선택하면 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86318-128">Available when you select **Database**.</span></span> <span data-ttu-id="86318-129">필드 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="86318-129">Select the field name.</span></span>  
  
 <span data-ttu-id="86318-130">**이 MIME 형식 사용**</span><span class="sxs-lookup"><span data-stu-id="86318-130">**Use this MIME type**</span></span>  
 <span data-ttu-id="86318-131">데이터베이스에 포함된 그림에 적합한 형식을 선택합니다(예: .bmp, .jpeg, .gif, .png, .x-png).</span><span class="sxs-lookup"><span data-stu-id="86318-131">Choose the appropriate format of the pictures contained in the database (for example, .bmp, .jpeg, .gif, .png, or .x-png).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86318-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="86318-132">See Also</span></span>  
 <span data-ttu-id="86318-133">[보고서 항목 서식 지정 &#40;보고서 작성기 및 SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="86318-133">[Formatting Report Items &#40;Report Builder and SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="86318-134">[텍스트 및 자리 표시자 서식 지정 &#40;보고서 작성기 및 SSRS&#41;](report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="86318-134">[Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="86318-135">이미지&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="86318-135">Images &#40;Report Builder and SSRS&#41;</span></span>](report-design/images-report-builder-and-ssrs.md)  
  
  
