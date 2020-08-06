---
title: 다른 애플리케이션에서 보고서 인쇄(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a5560581-fd57-4a45-b7ea-43b21a8a7419
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 58fee2cf31601dc638eebd69a13727a805408ac0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733659"
---
# <a name="print-reports-from-other-applications-report-builder-and-ssrs"></a><span data-ttu-id="182fc-102">다른 애플리케이션에서 보고서 인쇄(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="182fc-102">Print Reports from Other Applications (Report Builder and SSRS)</span></span>
  <span data-ttu-id="182fc-103">보고서 작성기는 다른 애플리케이션에서 보고서를 쉽게 볼 수 있도록 내보내기 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="182fc-103">Report Builder provides an export option that allows you to easily view a report in other applications.</span></span> <span data-ttu-id="182fc-104">브라우저나 웹 기반의 애플리케이션에서 보고서를 열면 보고서 위쪽에 나타나는 보고서 도구 모음에서 `Export` 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="182fc-104">The `Export` command is available on the report toolbar that appears at the top of a report when you open it in a browser or Web-based application.</span></span> <span data-ttu-id="182fc-105">보고서를 내보내면 다른 애플리케이션에서 보고서가 표시됩니다. 예를 들어 보고서를 Excel로 내보내면 해당 보고서가 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="182fc-105">Exporting a report displays it in a different application (for example, exporting a report to Excel opens the report in [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]).</span></span> <span data-ttu-id="182fc-106">애플리케이션에 사용하려는 특정 인쇄 기능이 있는 경우에만 인쇄 목적으로 보고서를 내보내는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="182fc-106">For printing purposes, exporting a report is recommended only if the application has specific printing features that you want to use.</span></span>  
  
 <span data-ttu-id="182fc-107">다른 애플리케이션으로 보고서를 내보내려면 해당 애플리케이션이 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="182fc-107">To export a report to another application, you must have that application installed.</span></span> <span data-ttu-id="182fc-108">예를 들어 Acrobat(PDF) 형식으로 보고서를 내보내려면 컴퓨터에 Adobe Acrobat Reader가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="182fc-108">For example, you must have Adobe Acrobat Reader installed on your computer before you can export to the Acrobat (PDF) format.</span></span> <span data-ttu-id="182fc-109">TIFF 형식으로 보고서를 내보내도록 선택하면 TIFF 파일 형식에 연결된 보기 애플리케이션에서 보고서가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="182fc-109">If you choose to export a report to TIFF format, the report server places the report in a viewing application that is associated with the TIFF file type.</span></span> <span data-ttu-id="182fc-110">사용되는 애플리케이션은 설치되어 있는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 버전에 따라 다르지만 일반적으로 Windows 사진 및 팩스 뷰어가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="182fc-110">Although the application used depends on which version of [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows you have, typically this tool is Windows Picture and Fax Viewer.</span></span> <span data-ttu-id="182fc-111">기본 해상도는 96DPI의 화면 해상도에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="182fc-111">The default resolution corresponds to a screen resolution of 96 dots per inch (DPI).</span></span> <span data-ttu-id="182fc-112">프린터의 기능에 맞도록 Windows 사진 및 팩스 뷰어에서 해상도를 300DPI나 600DPI로 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="182fc-112">You can increase the resolution in Windows Picture and Fax Viewer to 300 DPI or 600 DPI to match the capabilities of your printer.</span></span> <span data-ttu-id="182fc-113">해상도를 조정하는 방법은 Windows 제품 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="182fc-113">For more information about adjusting the resolution, see the Windows product documentation.</span></span>  
  
 <span data-ttu-id="182fc-114">MHTML이라고도 하는 웹 보관 파일을 선택하면 보고서가 기본 브라우저로 내보내집니다.</span><span class="sxs-lookup"><span data-stu-id="182fc-114">If you choose Web archive (also known as MHTML), the report is exported to your default browser.</span></span> <span data-ttu-id="182fc-115">브라우저에서 인쇄하면 모든 페이지의 아래쪽에 보고서 경로 정보가 추가될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="182fc-115">Printing from the browser may result in report path information being added at the bottom of every page.</span></span> <span data-ttu-id="182fc-116">대부분의 경우 브라우저 옵션에서 경로 정보가 인쇄되지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="182fc-116">In most cases, you can set browser options to omit path information on a printed page.</span></span> <span data-ttu-id="182fc-117">자세한 내용은 사용하는 브라우저의 제품 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="182fc-117">For more information, see the product documentation for the browser you are using.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="182fc-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="182fc-118">See Also</span></span>  
 <span data-ttu-id="182fc-119">[보고서 &#40;보고서 작성기 및 SSRS를 인쇄&#41;](print-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="182fc-119">[Print a Report &#40;Report Builder and SSRS&#41;](print-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="182fc-120">[인쇄 컨트롤 &#40;보고서 작성기 및 SSRS를 사용 하 여 브라우저에서 보고서 인쇄&#41;](print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="182fc-120">[Print Reports from a Browser with the Print Control &#40;Report Builder and SSRS&#41;](print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="182fc-121">[보고서 &#40;보고서 작성기 및 SSRS&#41;내보내기](export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="182fc-121">[Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="182fc-122">[다른 파일 형식으로 보고서 내보내기 &#40;보고서 작성기 및 SSRS&#41;](../export-a-report-as-another-file-type-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="182fc-122">[Export a Report as Another File Type &#40;Report Builder and SSRS&#41;](../export-a-report-as-another-file-type-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="182fc-123">보고서 찾기, 보기 및 관리&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="182fc-123">Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;</span></span>](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
