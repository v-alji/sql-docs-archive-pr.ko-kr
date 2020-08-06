---
title: 이미지 파일로 내보내기(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 020d8ea2-de07-4212-a2bb-2ed0df2c8db8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dc1c8539b39a99c252ebfcb0275b674f657de6c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650785"
---
# <a name="exporting-to-an-image-file-report-builder-and-ssrs"></a><span data-ttu-id="9f6c5-102">이미지 파일로 내보내기(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="9f6c5-102">Exporting to an Image File (Report Builder and SSRS)</span></span>
  <span data-ttu-id="9f6c5-103">이미지 렌더링 확장 프로그램은 보고서를 비트맵이나 메타파일로 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="9f6c5-103">The Image rendering extension renders a report to a bitmap or metafile.</span></span> <span data-ttu-id="9f6c5-104">기본적으로 이미지 렌더링 확장 프로그램은 보고서를 여러 페이지로 볼 수 있도록 TIFF 파일로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9f6c5-104">By default, the Image rendering extension produces a TIFF file of the report, which can be viewed in multiple pages.</span></span> <span data-ttu-id="9f6c5-105">클라이언트가 이미지를 수신하면 이미지 뷰어에서 확인하거나 인쇄할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f6c5-105">When the client receives the image, it can be displayed in an image viewer and printed.</span></span> <span data-ttu-id="9f6c5-106">이 항목에서는 이미지 렌더러 관련 정보를 제공하고 렌더링 규칙의 예외를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9f6c5-106">This topic provides Image renderer-specific information and describes exceptions to the rendering rules.</span></span>  
  
 <span data-ttu-id="9f6c5-107">이미지 렌더링 확장 프로그램은 [!INCLUDE[ndptecgdiplus](../../includes/ndptecgdiplus-md.md)]에서 지원하는 BMP, EMF, EMFPlus, GIF, JPEG, PNG 및 TIFF 형식으로 파일을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f6c5-107">The Image rendering extension can generate files in any of the formats supported by [!INCLUDE[ndptecgdiplus](../../includes/ndptecgdiplus-md.md)]: BMP, EMF, EMFPlus, GIF, JPEG, PNG, and TIFF.</span></span> <span data-ttu-id="9f6c5-108">TIFF 형식의 경우 기본 스트림의 파일 이름은 *ReportName*.tif입니다.</span><span class="sxs-lookup"><span data-stu-id="9f6c5-108">For TIFF format, the file name of the primary stream is *ReportName*.tif.</span></span> <span data-ttu-id="9f6c5-109">파일당 한 페이지로 렌더링되는 기타 모든 형식의 경우 파일 이름은 *ReportName_Page.ext* 입니다.</span><span class="sxs-lookup"><span data-stu-id="9f6c5-109">For all other formats, which render as a single page per file, the file name is *ReportName_Page.ext* where.</span></span> <span data-ttu-id="9f6c5-110">여기서*ext* 는 선택한 형식의 파일 확장명입니다.</span><span class="sxs-lookup"><span data-stu-id="9f6c5-110">*ext* is the file extension for the chosen format.</span></span> <span data-ttu-id="9f6c5-111">다른 이미지 지원 형식으로 파일을 생성하려면 위에 나와 있는 문자열 중 하나를 **OutputFormatDeviceInfo** 설정에 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9f6c5-111">To produce a file in another Image-supported format, specify any of the above listed strings in the **OutputFormatDeviceInfo** setting.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="supported-image-formats"></a><a name="SupportedImageFormats"></a> <span data-ttu-id="9f6c5-112">지원되는 이미지 형식</span><span class="sxs-lookup"><span data-stu-id="9f6c5-112">Supported Image Formats</span></span>  
 <span data-ttu-id="9f6c5-113">다음 표에는 각 이미지 렌더러 형식에 대한 파일 확장명과 MIMEType이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f6c5-113">The following table shows the file extension and MimeType for each Image renderer format.</span></span>  
  
|<span data-ttu-id="9f6c5-114">**형식**</span><span class="sxs-lookup"><span data-stu-id="9f6c5-114">**Type**</span></span>|<span data-ttu-id="9f6c5-115">**내선 번호**</span><span class="sxs-lookup"><span data-stu-id="9f6c5-115">**Extension**</span></span>|<span data-ttu-id="9f6c5-116">**MIMEType**</span><span class="sxs-lookup"><span data-stu-id="9f6c5-116">**MIMEType**</span></span>|  
|--------------|-------------------|------------------|  
|<span data-ttu-id="9f6c5-117">BMP</span><span class="sxs-lookup"><span data-stu-id="9f6c5-117">BMP</span></span>|<span data-ttu-id="9f6c5-118">bmp</span><span class="sxs-lookup"><span data-stu-id="9f6c5-118">bmp</span></span>|<span data-ttu-id="9f6c5-119">image/bmp</span><span class="sxs-lookup"><span data-stu-id="9f6c5-119">image/bmp</span></span>|  
|<span data-ttu-id="9f6c5-120">GIF</span><span class="sxs-lookup"><span data-stu-id="9f6c5-120">GIF</span></span>|<span data-ttu-id="9f6c5-121">GIF</span><span class="sxs-lookup"><span data-stu-id="9f6c5-121">gif</span></span>|<span data-ttu-id="9f6c5-122">image/gif</span><span class="sxs-lookup"><span data-stu-id="9f6c5-122">image/gif</span></span>|  
|<span data-ttu-id="9f6c5-123">JPEG</span><span class="sxs-lookup"><span data-stu-id="9f6c5-123">JPEG</span></span>|<span data-ttu-id="9f6c5-124">jpeg</span><span class="sxs-lookup"><span data-stu-id="9f6c5-124">jpeg</span></span>|<span data-ttu-id="9f6c5-125">image/jpeg</span><span class="sxs-lookup"><span data-stu-id="9f6c5-125">image/jpeg</span></span>|  
|<span data-ttu-id="9f6c5-126">PNG</span><span class="sxs-lookup"><span data-stu-id="9f6c5-126">PNG</span></span>|<span data-ttu-id="9f6c5-127">png</span><span class="sxs-lookup"><span data-stu-id="9f6c5-127">png</span></span>|<span data-ttu-id="9f6c5-128">image/png</span><span class="sxs-lookup"><span data-stu-id="9f6c5-128">image/png</span></span>|  
|<span data-ttu-id="9f6c5-129">TIFF</span><span class="sxs-lookup"><span data-stu-id="9f6c5-129">TIFF</span></span>|<span data-ttu-id="9f6c5-130">tif</span><span class="sxs-lookup"><span data-stu-id="9f6c5-130">tif</span></span>|<span data-ttu-id="9f6c5-131">image/tiff</span><span class="sxs-lookup"><span data-stu-id="9f6c5-131">image/tiff</span></span>|  
|<span data-ttu-id="9f6c5-132">EMF</span><span class="sxs-lookup"><span data-stu-id="9f6c5-132">EMF</span></span>|<span data-ttu-id="9f6c5-133">EMF</span><span class="sxs-lookup"><span data-stu-id="9f6c5-133">emf</span></span>|<span data-ttu-id="9f6c5-134">image/emf</span><span class="sxs-lookup"><span data-stu-id="9f6c5-134">image/emf</span></span>|  
|<span data-ttu-id="9f6c5-135">EMFPlus</span><span class="sxs-lookup"><span data-stu-id="9f6c5-135">EMFPlus</span></span>|<span data-ttu-id="9f6c5-136">EMF</span><span class="sxs-lookup"><span data-stu-id="9f6c5-136">emf</span></span>|<span data-ttu-id="9f6c5-137">image/emf</span><span class="sxs-lookup"><span data-stu-id="9f6c5-137">image/emf</span></span>|  
  
  
##  <a name="rendering-multiple-pages"></a><a name="RenderingMultiplePages"></a> <span data-ttu-id="9f6c5-138">여러 페이지 렌더링</span><span class="sxs-lookup"><span data-stu-id="9f6c5-138">Rendering Multiple Pages</span></span>  
 <span data-ttu-id="9f6c5-139">TIFF는 파일 하나에 여러 페이지 문서를 포함할 수 있는 유일한 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="9f6c5-139">TIFF is the only format that supports multiple page documents in a single file.</span></span> <span data-ttu-id="9f6c5-140">JPG나 PNG 같은 다른 형식은 한 번에 한 페이지만 출력하며 매번 각 페이지에 대한 렌더링 확장 프로그램을 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f6c5-140">Other formats, such as JPG or PNG, output one page at a time and require a separate call to the rendering extension for each page.</span></span>  
  
  
##  <a name="interactivity"></a><a name="Interactivity"></a><span data-ttu-id="9f6c5-141">대화형 작업</span><span class="sxs-lookup"><span data-stu-id="9f6c5-141">Interactivity</span></span>  
 <span data-ttu-id="9f6c5-142">상호 작용은 이 렌더러를 통해 생성되는 어떤 이미지 형식에서도 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9f6c5-142">Interactivity is not supported in any Image formats generated by this renderer.</span></span> <span data-ttu-id="9f6c5-143">다음 대화형 요소는 렌더링되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9f6c5-143">The following interactive elements are not rendered:</span></span>  
  
-   <span data-ttu-id="9f6c5-144">하이퍼링크</span><span class="sxs-lookup"><span data-stu-id="9f6c5-144">Hyperlinks</span></span>  
  
-   <span data-ttu-id="9f6c5-145">표시 또는 숨기기</span><span class="sxs-lookup"><span data-stu-id="9f6c5-145">Show or Hide</span></span>  
  
-   <span data-ttu-id="9f6c5-146">문서 구조</span><span class="sxs-lookup"><span data-stu-id="9f6c5-146">Document Map</span></span>  
  
-   <span data-ttu-id="9f6c5-147">드릴스루 또는 클릭 광고 링크</span><span class="sxs-lookup"><span data-stu-id="9f6c5-147">Drillthrough or clickthrough links</span></span>  
  
-   <span data-ttu-id="9f6c5-148">최종 사용자 정렬</span><span class="sxs-lookup"><span data-stu-id="9f6c5-148">End user sort</span></span>  
  
-   <span data-ttu-id="9f6c5-149">고정 머리글</span><span class="sxs-lookup"><span data-stu-id="9f6c5-149">Fixed headers</span></span>  
  
-   <span data-ttu-id="9f6c5-150">책갈피</span><span class="sxs-lookup"><span data-stu-id="9f6c5-150">Bookmarks</span></span>  
  
  
##  <a name="device-information-settings"></a><a name="DeviceInfo"></a><span data-ttu-id="9f6c5-151">장치 정보 설정</span><span class="sxs-lookup"><span data-stu-id="9f6c5-151">Device Information Settings</span></span>  
 <span data-ttu-id="9f6c5-152">디바이스 정보 설정을 변경하여 이 렌더러의 기본 설정을 일부 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f6c5-152">You can change some default settings for this renderer by changing the device information settings.</span></span> <span data-ttu-id="9f6c5-153">자세한 내용은 [Image Device Information Settings](../image-device-information-settings.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9f6c5-153">For more information, see [Image Device Information Settings](../image-device-information-settings.md).</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="9f6c5-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9f6c5-154">See Also</span></span>  
 <span data-ttu-id="9f6c5-155">[Reporting Services &#40;보고서 작성기 및 SSRS의 페이지 매김&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9f6c5-155">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9f6c5-156">[보고서 작성기 및 SSRS&#41;&#40;렌더링 동작](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9f6c5-156">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9f6c5-157">[여러 보고서 렌더링 확장 프로그램에 대 한 대화형 기능 &#40;보고서 작성기 및 SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="9f6c5-157">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 <span data-ttu-id="9f6c5-158">[보고서 항목 &#40;보고서 작성기 및 SSRS&#41;렌더링](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9f6c5-158">[Rendering Report Items &#40;Report Builder and SSRS&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="9f6c5-159">테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9f6c5-159">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
  
  
