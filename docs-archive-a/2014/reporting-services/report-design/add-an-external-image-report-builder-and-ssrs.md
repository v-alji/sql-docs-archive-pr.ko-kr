---
title: 외부 이미지 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 81fd4a1f-79a9-4967-86d6-6229413c0995
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8d0030c8f29b14b2c62048be306daa15948cd8d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729052"
---
# <a name="add-an-external-image-report-builder-and-ssrs"></a><span data-ttu-id="4e679-102">외부 이미지 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="4e679-102">Add an External Image (Report Builder and SSRS)</span></span>
  <span data-ttu-id="4e679-103">외부 이미지는 기본 모드나 SharePoint 통합 모드에 있는 보고서 서버 또는 다른 웹 사이트에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e679-103">External images can be on a report server in native mode or SharePoint integrated mode, or on any other Web site.</span></span> <span data-ttu-id="4e679-104">보고서에 외부 이미지를 포함할 때는 해당 이미지가 존재하며 보고서를 읽는 사용자에게 해당 이미지에 액세스할 수 있는 권한이 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e679-104">When you include external images in your report, you must verify that the image exists and that the report reader has permissions to access the image.</span></span> <span data-ttu-id="4e679-105">자세한 내용은 [이미지&#40;보고서 작성기 및 SSRS&#41;](images-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4e679-105">For more information, see [Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-external-image"></a><span data-ttu-id="4e679-106">외부 이미지를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="4e679-106">To add an external image</span></span>  
  
1.  <span data-ttu-id="4e679-107">보고서 디자인 뷰의 **삽입** 탭에서 **이미지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4e679-107">In report design view, on the **Insert** tab, click **Image**.</span></span>  
  
2.  <span data-ttu-id="4e679-108">디자인 화면에서 상자를 클릭한 다음 끌어 원하는 크기의 이미지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4e679-108">On the design surface, click and then drag a box to the desired size of the image.</span></span>  
  
3.  <span data-ttu-id="4e679-109">**이미지 속성** 대화 상자의 **일반** 탭에 있는 **이름** 입력란에 이름을 입력하거나 기본값을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="4e679-109">On the **General** tab of the **Image Properties** dialog box, type a name in the **Name** text box or accept the default.</span></span>  
  
4.  <span data-ttu-id="4e679-110">(옵션) **도구 설명** 입력란에서 HTML용으로 렌더링된 보고서에서 사용자가 마우스로 이미지를 가리킬 때 표시할 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4e679-110">(Optional) In the **Tooltip** text box, type text to display when the user hovers over the image in a report rendered for HTML.</span></span>  
  
5.  <span data-ttu-id="4e679-111">**이미지 원본 선택**에서 **외부**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4e679-111">In **Select the image source**, select **External**.</span></span>  
  
     <span data-ttu-id="4e679-112">기본 모드의 보고서 서버에 있는 이미지를 지정하려면 **이 이미지 사용** 상자에 이미지의 상대 경로(예: ../images/image1.jpg)를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4e679-112">For an image on a report server in native mode, type a relative path to the image in the **Use this image** box-for example, ../images/image1.jpg.</span></span>  
  
     <span data-ttu-id="4e679-113">SharePoint 통합 모드의 보고서 서버 또는 다른 웹 사이트의 이미지에 대해 **이 이미지 사용** 상자에 이미지의 전체 URL을 입력 합니다 (예: http:// \<SharePointservername> / \<site> /Documents/images/image1.jpg).</span><span class="sxs-lookup"><span data-stu-id="4e679-113">For an image on a report server in SharePoint integrated mode, or any other Web site, type a full URL to the image in the **Use this image** box-for example, http://\<SharePointservername>/\<site>/Documents/images/image1.jpg.</span></span>  
  
     <span data-ttu-id="4e679-114">자세한 내용은 [외부 항목에 대한 경로 지정&#40;보고서 작성기 및 SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4e679-114">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
6.  <span data-ttu-id="4e679-115">(옵션) **크기**, **표시 유형**, **동작**또는 **테두리** 를 클릭하여 이미지 보고서 항목의 추가 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4e679-115">(Optional) Click **Size**, **Visibility**, **Action**, or **Border** to set additional properties for the image report item.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4e679-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4e679-116">See Also</span></span>  
 <span data-ttu-id="4e679-117">[보고서에 이미지 포함&#40;보고서 작성기 및 SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4e679-117">[Embed an Image in a Report &#40;Report Builder and SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4e679-118">[배경 이미지 추가&#40;보고서 작성기 및 SSRS&#41;](add-a-background-image-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4e679-118">[Add a Background Image &#40;Report Builder and SSRS&#41;](add-a-background-image-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="4e679-119">이미지 속성 대화 상자, 일반&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4e679-119">Image Properties Dialog Box, General &#40;Report Builder and SSRS&#41;</span></span>](../image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
