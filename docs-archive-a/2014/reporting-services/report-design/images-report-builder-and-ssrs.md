---
title: 이미지(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fcc2db5c-5c26-4607-ae2b-f65c80360536
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4f0840a10cc1082ba8dc7912862f7cf34c64972d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730184"
---
# <a name="images-report-builder-and-ssrs"></a><span data-ttu-id="71fed-102">이미지(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="71fed-102">Images (Report Builder and SSRS)</span></span>
  <span data-ttu-id="71fed-103">이미지는 보고서에 포함되어 있거나, 데이터베이스에 저장되어 있거나, 보고서 서버에 저장되어 있거나, 웹의 기타 위치에 저장되어 있는 이미지에 대한 참조를 포함하는 보고서 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-103">An image is a report item that contains a reference to an image that is embedded in the report, stored in a database, stored on the report server, or stored elsewhere on the Web.</span></span> <span data-ttu-id="71fed-104">이미지는 데이터 행이 반복되는 그림이 될 수 있습니다</span><span class="sxs-lookup"><span data-stu-id="71fed-104">An image can be a picture that is repeated with rows of data.</span></span> <span data-ttu-id="71fed-105">특정 보고서 항목의 배경으로 이미지를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-105">You can also use an image as a background for certain report items.</span></span>  
  
 <span data-ttu-id="71fed-106">로고를 서버에 저장하면 같은 로고를 여러 보고서에 사용할 수 있으므로 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-106">Storing logos on a server is a good idea because you can use the same logo in many reports.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="comparing-external-embedded-and-data-bound-images"></a><a name="ComparingImages"></a> <span data-ttu-id="71fed-107">외부 이미지, 포함 이미지 및 데이터 바인딩된 이미지 비교</span><span class="sxs-lookup"><span data-stu-id="71fed-107">Comparing External, Embedded, and Data-Bound Images</span></span>  
 <span data-ttu-id="71fed-108">보고서에서 서버 기반 이미지나 기타 외부 이미지를 사용하면 이미지 항목은 보고서 서버 또는 웹의 이미지를 가리키는 경로를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-108">When you use a server-based or other external image in a report, the image item contains a path that points to an image on the report server or wherever it exists on the Web.</span></span> <span data-ttu-id="71fed-109">하지만 포함 이미지를 사용하면 이미지 데이터가 별도의 파일로 존재하지 않고 보고서 정의 안에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-109">When you use an embedded image, however, the image data is stored within the report definition and does not exist as a separate file.</span></span>  
  
 <span data-ttu-id="71fed-110">서버 기반 이미지는 여러 보고서 또는 웹 페이지가 공유하는 로고 및 정적 그림에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-110">Server-based images work well for logos and static pictures that are shared among several reports or Web pages.</span></span> <span data-ttu-id="71fed-111">포함 이미지를 사용하면 이미지를 항상 보고서에서 사용할 수 있지만 공유할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-111">Embedded images ensure that the images are always available to the report, but they cannot be shared.</span></span> <span data-ttu-id="71fed-112">외부 이미지가 포함된 보고서 정의는 포함 이미지가 있는 정의보다 크기가 작습니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-112">Report definitions with external images are smaller than definitions with embedded images.</span></span>  
  
 <span data-ttu-id="71fed-113">데이터베이스에 저장된 이진 데이터로부터 데이터 바인딩된 이미지를 표시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-113">Data-bound images can also be displayed from binary data stored in a database.</span></span> <span data-ttu-id="71fed-114">예를 들어 제목 목록에 제품 이름과 함께 표시되는 그림은 데이터베이스 이미지입니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-114">For example, the pictures that appear alongside product names in a product list are database images.</span></span> <span data-ttu-id="71fed-115">다음 그림에서는 자전거 이미지를 데이터베이스에 저장하고 보고서에서 검색하여 각 제품을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-115">In the following picture, the images of bicycles are stored in a database and retrieved in the report to illustrate each product.</span></span>  
  
 <span data-ttu-id="71fed-116">![rs_DataboundBikes](../media/rs-databoundbikes.gif "rs_DataboundBikes")</span><span class="sxs-lookup"><span data-stu-id="71fed-116">![rs_DataboundBikes](../media/rs-databoundbikes.gif "rs_DataboundBikes")</span></span>  
  

  
##  <a name="images-as-report-parts"></a><a name="ImagesReportParts"></a> <span data-ttu-id="71fed-117">보고서 파트인 이미지</span><span class="sxs-lookup"><span data-stu-id="71fed-117">Images as Report Parts</span></span>  
 <span data-ttu-id="71fed-118">이미지를 보고서와는 별도로 보고서 파트로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-118">You can save images separately from a report as report parts.</span></span> [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
 
  
##  <a name="embedding-images"></a><a name="EmbedImages"></a> <span data-ttu-id="71fed-119">포함 이미지</span><span class="sxs-lookup"><span data-stu-id="71fed-119">Embedding Images</span></span>  
 <span data-ttu-id="71fed-120">모든 이미지 데이터가 보고서 정의 안에 저장되도록 보고서에 이미지를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-120">You can embed images in a report so that all image data is stored within the report definition.</span></span> <span data-ttu-id="71fed-121">이미지를 포함하면 이미지가 MIME로 인코딩되어 보고서 정의에 텍스트로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-121">When you embed an image, the image is MIME-encoded and stored as text in the report definition.</span></span> <span data-ttu-id="71fed-122">포함 이미지를 사용하면 보고서에서 항상 이미지를 사용할 수 있지만 보고서 정의의 크기도 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-122">Using an embedded image ensures that the image is always available to the report, but it also increases the size of the report definition.</span></span>  
  
 <span data-ttu-id="71fed-123">이미지 포함에 대한 자세한 내용은 [보고서에 이미지 포함&#40;보고서 작성기 및 SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="71fed-123">For more information about embedding an image, see [Embed an Image in a Report &#40;Report Builder and SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="external-images"></a><a name="ExternalImages"></a> <span data-ttu-id="71fed-124">외부 이미지</span><span class="sxs-lookup"><span data-stu-id="71fed-124">External Images</span></span>  
 <span data-ttu-id="71fed-125">이미지에 URL을 지정하여 저장된 이미지를 보고서에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-125">You can include stored images in a report by specifying a URL to the image.</span></span> <span data-ttu-id="71fed-126">보고서에 외부 이미지를 사용하는 경우 이미지 원본은 `External`로 설정되고 이미지 값은 이미지에 대한 URL 주소 또는 경로가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-126">When you use an external image in a report, the image source is set to `External` and the value for the image is the URL address or path to the image.</span></span>  
  
 <span data-ttu-id="71fed-127">자세한 내용은 [외부 항목에 대한 경로 지정&#40;보고서 작성기 및 SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="71fed-127">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="71fed-128">보고서 작성기 또는 보고서 디자이너에서 보고서를 실행하면 미리 보기 기능은 사용자의 자격 증명을 사용하여 이미지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-128">When the report is run in Report Builder or Report Designer, preview uses the credentials of the user to display the image.</span></span> <span data-ttu-id="71fed-129">보고서 서버에서 보고서를 실행할 경우 이미지에 액세스하는 데 필요한 서버 자격 증명이 없으면 보고서의 이미지가 표시되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-129">When the report is run on the report server, the image in the report may not be displayed if the server credentials are not sufficient to access the image.</span></span> <span data-ttu-id="71fed-130">이 경우 시스템 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="71fed-130">In that case, contact your system administrator.</span></span>  
  
 <span data-ttu-id="71fed-131">보고서에 외부 이미지를 추가하는 방법은 [외부 이미지 추가&#40;보고서 작성기 및 SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="71fed-131">For more information about adding an external image to a report, see [Add an External Image &#40;Report Builder and SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md).</span></span>  
  
 
  
##  <a name="background-images"></a><a name="BackgroundImages"></a> <span data-ttu-id="71fed-132">배경 이미지</span><span class="sxs-lookup"><span data-stu-id="71fed-132">Background Images</span></span>  
 <span data-ttu-id="71fed-133">보고서의 본문이나 사각형, 입력란, 목록, 행렬 또는 테이블의 배경 이미지로 이미지를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-133">You can use an image as a background image in the body of the report or in a rectangle, text box, list, matrix, or table.</span></span> <span data-ttu-id="71fed-134">배경 이미지와 이미지는 속성이 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-134">A background image and an image have similar properties.</span></span> <span data-ttu-id="71fed-135">또한 항목의 배경을 채울 때 이미지가 반복되는 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-135">You can also specify how the image is repeated to fill the background of the item.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="71fed-136">HTML 렌더링 확장 프로그램과 같은 일부 렌더링 확장 프로그램은 본문, 페이지 머리글 및 페이지 바닥글에 보고서 본문의 배경 이미지를 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-136">Some rendering extensions, like the HTML rendering extension, render the background image for the report body in the body, the page header, and the page footer.</span></span> <span data-ttu-id="71fed-137">페이지 머리글 및 바닥글에 각각 배경 이미지를 정의할 수 있지만 이미지를 정의하지 않으면 보고서에서 본문의 배경 이미지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-137">You can define a separate background image for the page header and footer, but if no image is defined, the report uses the background image of the body.</span></span> <span data-ttu-id="71fed-138">이미지 렌더링 확장 프로그램과 같은 기타 렌더링 확장 프로그램은 페이지 머리글 및 바닥글에 본문의 배경 이미지를 렌더링하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-138">Other rendering extensions, like the Image rendering extension, do not render the body background image in the page header and footer.</span></span>  
  
 <span data-ttu-id="71fed-139">배경 이미지 추가에 대한 자세한 내용은 [배경 이미지 추가&#40;보고서 작성기 및 SSRS&#41;](add-a-background-image-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="71fed-139">For more information about adding a background image, see [Add a Background Image &#40;Report Builder and SSRS&#41;](add-a-background-image-report-builder-and-ssrs.md).</span></span>  
  
 
  
##  <a name="data-bound-images"></a><a name="DataboundImages"></a> <span data-ttu-id="71fed-140">데이터 바인딩된 이미지</span><span class="sxs-lookup"><span data-stu-id="71fed-140">Data-bound Images</span></span>  
 <span data-ttu-id="71fed-141">데이터베이스에 저장된 이미지를 보고서에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-141">You can add images that are stored in a database to your report.</span></span> <span data-ttu-id="71fed-142">정적 이미지에 사용된 것과 같은 이미지 보고서 항목을 이미지가 데이터베이스에 저장되어 있음을 나타내는 속성 집합과 함께 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="71fed-142">You use the same image report item as the one used for static images, but with a set of properties that indicate that the image is stored in a database.</span></span> <span data-ttu-id="71fed-143">데이터 바인딩된 이미지를 사용하는 방법은 [데이터 바인딩된 이미지 추가&#40;보고서 작성기 및 SSRS&#41;](add-a-data-bound-image-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="71fed-143">To view instructions about working with data-bound images, see [Add a Data-Bound Image &#40;Report Builder and SSRS&#41;](add-a-data-bound-image-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="how-to-topics"></a><a name="HowTo"></a> <span data-ttu-id="71fed-144">방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="71fed-144">How-to Topics</span></span>  
 [<span data-ttu-id="71fed-145">외부 이미지 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="71fed-145">Add an External Image &#40;Report Builder and SSRS&#41;</span></span>](add-an-external-image-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="71fed-146">보고서에 이미지 포함&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="71fed-146">Embed an Image in a Report &#40;Report Builder and SSRS&#41;</span></span>](embed-an-image-in-a-report-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="71fed-147">배경 이미지 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="71fed-147">Add a Background Image &#40;Report Builder and SSRS&#41;</span></span>](add-a-background-image-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="71fed-148">데이터 바인딩된 이미지 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="71fed-148">Add a Data-Bound Image &#40;Report Builder and SSRS&#41;</span></span>](add-a-data-bound-image-report-builder-and-ssrs.md)  
  
  
  
## <a name="see-also"></a><span data-ttu-id="71fed-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="71fed-149">See Also</span></span>  
 <span data-ttu-id="71fed-150">[이미지 파일로 내보내기&#40;보고서 작성기 및 SSRS&#41;](../report-builder/exporting-to-an-image-file-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="71fed-150">[Exporting to an Image File &#40;Report Builder and SSRS&#41;](../report-builder/exporting-to-an-image-file-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="71fed-151">렌더링 동작&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="71fed-151">Rendering Behaviors &#40;Report Builder  and SSRS&#41;</span></span>](rendering-behaviors-report-builder-and-ssrs.md)  
  
  
