---
title: 보고서에 이미지 포함(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.embeddedimages.f1
- "10060"
ms.assetid: aed77345-5eeb-41f0-96c9-db6b4a11ec6f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6599092e0ef37dd9bbc15f4815c0315c77e7943b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728044"
---
# <a name="embed-an-image-in-a-report-report-builder-and-ssrs"></a><span data-ttu-id="07016-102">보고서에 이미지 포함(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="07016-102">Embed an Image in a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="07016-103">보고서에 포함 이미지를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07016-103">A report can include an embedded image.</span></span> <span data-ttu-id="07016-104">이미지를 포함하면 보고서에서 항상 이미지를 사용할 수 있지만 보고서 정의 즉, 보고서를 정의하는 파일의 크기도 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="07016-104">Embedding an image ensures that the image is always available to a report, but can affect the size of the report definition, the file that defines the report.</span></span> <span data-ttu-id="07016-105">보고서에 포함된 이미지는 보고서 데이터 창에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="07016-105">The images embedded in a report are listed in the Report Data pane.</span></span>  
  
 <span data-ttu-id="07016-106">디자인 화면에 이미지를 추가하기 전에 보고서 정의에 이미지를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07016-106">You might want to embed an image in the report definition before adding the image to the design surface.</span></span> <span data-ttu-id="07016-107">자세한 내용은 [배경 이미지 추가&#40;보고서 작성기 및 SSRS&#41;](add-a-background-image-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07016-107">For more information, see [Add a Background Image &#40;Report Builder and SSRS&#41;](add-a-background-image-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-embed-an-image-in-a-report"></a><span data-ttu-id="07016-108">보고서에 이미지를 포함하려면</span><span class="sxs-lookup"><span data-stu-id="07016-108">To embed an image in a report</span></span>  
  
1.  <span data-ttu-id="07016-109">보고서 디자인 뷰의 **삽입** 탭에서 **이미지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="07016-109">In report design view, on the **Insert** tab, click **Image**.</span></span>  
  
2.  <span data-ttu-id="07016-110">디자인 화면에서 상자를 클릭한 다음 끌어 원하는 크기의 이미지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="07016-110">On the design surface, click and then drag a box to the desired size of the image.</span></span>  
  
3.  <span data-ttu-id="07016-111">**이미지 속성** 대화 상자의 **일반** 페이지에 있는 **이름** 입력란에 이름을 입력하거나 기본값을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="07016-111">In the **General** page of the **Image Properties** dialog box, type a name in the **Name** text box or accept the default.</span></span>  
  
4.  <span data-ttu-id="07016-112">(옵션) 렌더링된 보고서에서 사용자가 마우스로 이미지를 가리킬 때 표시할 텍스트를 **도구 설명** 입력란에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="07016-112">(Optional) In the **ToolTip** text box, type the text that you want to appear when the user hovers over the image in the rendered report.</span></span>  
  
5.  <span data-ttu-id="07016-113">**이미지 원본 선택**에서 **포함**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07016-113">In **Select the image source**, select **Embedded**.</span></span>  
  
6.  <span data-ttu-id="07016-114">**이 이미지 사용** 입력란 옆의 **가져오기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="07016-114">Click the **Import** button next to the **Use this image** text box</span></span>  
  
7.  <span data-ttu-id="07016-115">**파일 형식**에서 이미지 파일 형식을 선택하고 파일을 탐색한 다음 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="07016-115">In **Files of type**, select the image file type, navigate to the file, and then click **Open**.</span></span>  
  
8.  <span data-ttu-id="07016-116">**이미지 속성** 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="07016-116">In the **Image Properties** dialog box, click **OK**.</span></span>  
  
     <span data-ttu-id="07016-117">디자인 화면에 그린 상자에 이미지가 표시되고 보고서 데이터 창의 이미지 폴더 아래에 파일이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07016-117">The image is displayed in the box you drew on the design surface, and the file is displayed under the Images folder in the Report Data pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="07016-118">이미지를 가져오면 MIME 형식(예: bmp)도 자동으로 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="07016-118">The MIME type (for example, bmp) is derived automatically when the image is imported.</span></span> <span data-ttu-id="07016-119">MIME 형식을 변경하려면 다음 절차를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="07016-119">To change the MIME type, see the next procedure.</span></span>  
  
### <a name="optional-to-change-the-mime-type-of-an-imported-image"></a><span data-ttu-id="07016-120">가져온 이미지의 MIME 형식을 변경하려면(옵션)</span><span class="sxs-lookup"><span data-stu-id="07016-120">(optional) To change the MIME type of an imported image</span></span>  
  
1.  <span data-ttu-id="07016-121">디자인 뷰에서 보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="07016-121">Open the report in Design view.</span></span>  
  
2.  <span data-ttu-id="07016-122">디자인 화면에서 이미지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07016-122">Select the image on the design surface.</span></span> <span data-ttu-id="07016-123">**속성** 창에 이미지 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07016-123">The **Properties** pane displays the image properties.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="07016-124">속성 창이 표시되지 않으면 **보기** 탭에서 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="07016-124">If the Properties pane is not visible, on the **View** tab, click **Properties**.</span></span>  
  
3.  <span data-ttu-id="07016-125">**MIMEType** 속성 옆의 입력란을 클릭하고 드롭다운 목록에서 새 MIME 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07016-125">Click in the text box next to the **MIMEType** property and select a new MIME type from the drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07016-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="07016-126">See Also</span></span>  
 <span data-ttu-id="07016-127">[이미지&#40;보고서 작성기 및 SSRS&#41;](images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="07016-127">[Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="07016-128">[데이터 바인딩된 이미지 추가&#40;보고서 작성기 및 SSRS&#41;](add-a-data-bound-image-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="07016-128">[Add a Data-Bound Image &#40;Report Builder and SSRS&#41;](add-a-data-bound-image-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="07016-129">이미지 속성 대화 상자, 일반&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="07016-129">Image Properties Dialog Box, General &#40;Report Builder and SSRS&#41;</span></span>](../image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
