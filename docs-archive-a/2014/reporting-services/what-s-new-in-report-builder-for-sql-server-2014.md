---
title: SQL Server 2014에 대 한 보고서 작성기의 새로운 기능&#39;Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8223c19b-4b0d-4b1d-a042-9a726c18e708
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0ce72af225130bc3f081a53008a303c5213db636
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652005"
---
# <a name="what39s-new-in-report-builder-for-sql-server-2014"></a><span data-ttu-id="154d4-102">SQL Server 2014에 대 한 보고서 작성기의 새로운 기능&#39;</span><span class="sxs-lookup"><span data-stu-id="154d4-102">What&#39;s New in Report Builder for SQL Server 2014</span></span>
  <span data-ttu-id="154d4-103">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]에는 많은 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 기능이 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="154d4-103">The [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] introduces a number of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features.</span></span>  
  
 <span data-ttu-id="154d4-104">다른 제품 및 기술에 대 한이 릴리스의 기능에 대 한 자세한 내용은 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [SQL Server 2014의 새로운](../sql-server/what-s-new-in-sql-server-2016.md)기능을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="154d4-104">For information about features in this release for other [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] products and technologies, see [What's New in SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="154d4-105">이 릴리스의 새로운 기능에 대 한 최신 정보 및 리소스는 [SQL Server Reporting Services (SSRS)의 새로운 기능에 대 한 추가 정보](https://go.microsoft.com/fwlink/?LinkId=207147)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="154d4-105">For the most recent information and resources regarding new features in this release, see [Additional information on what is new in SQL Server Reporting Services (SSRS)](https://go.microsoft.com/fwlink/?LinkId=207147).</span></span>  
  
##  <a name="excel-renderer-for-microsoft-excel-2007-2010-and-microsoft-excel-2003"></a><a name="ExcelRenderer"></a><span data-ttu-id="154d4-106">Microsoft Excel 2007-2010 및 Microsoft Excel 2003 용 excel 렌더러</span><span class="sxs-lookup"><span data-stu-id="154d4-106">Excel Renderer for Microsoft Excel 2007-2010 and Microsoft Excel 2003</span></span>  
 <span data-ttu-id="154d4-107">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]의 새로운 기능인 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Excel 렌더링 확장 프로그램은 Word, Excel 및 PowerPoint용 Microsoft Office 호환 기능 팩이 설치된 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2003뿐만 아니라 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2007-2010과도 호환되는 Excel 문서로 보고서를 렌더링합니다</span><span class="sxs-lookup"><span data-stu-id="154d4-107">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Excel rendering extension, new in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], renders a report as an Excel document that is compatible with [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2007-2010 as well as [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint installed.</span></span> <span data-ttu-id="154d4-108">형식은 Office Open XML이고 파일 확장명은 .xlsx입니다.</span><span class="sxs-lookup"><span data-stu-id="154d4-108">The format is Office Open XML and the file extension of files is .xlsx.</span></span>  
  
 <span data-ttu-id="154d4-109">이 Excel 렌더링 확장 프로그램은 Excel 2003과 호환되는 이전 버전의 제한 사항을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="154d4-109">This Excel-rendering extension removes limitations of the earlier version, compatible with Excel 2003.</span></span> <span data-ttu-id="154d4-110">다음은 렌더링 확장 프로그램에서 향상된 내용을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="154d4-110">The following lists the improvement in the rendering extension:</span></span>  
  
-   <span data-ttu-id="154d4-111">워크시트당 최대 행 수는 1,048,576입니다.</span><span class="sxs-lookup"><span data-stu-id="154d4-111">Maximum rows per worksheet is 1,048,576.</span></span>  
  
-   <span data-ttu-id="154d4-112">워크시트당 최대 열 수는 16,384입니다.</span><span class="sxs-lookup"><span data-stu-id="154d4-112">Maximum columns per worksheet is 16,384.</span></span>  
  
-   <span data-ttu-id="154d4-113">워크시트에서 허용되는 색상 수는 약 1600만개(24비트 색)입니다.</span><span class="sxs-lookup"><span data-stu-id="154d4-113">Number of colors allowed in a worksheet is approximately 16 million (24-bit color).</span></span>  
  
-   <span data-ttu-id="154d4-114">ZIP 압축을 통해 파일 크기를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="154d4-114">ZIP compression provides smaller files sizes.</span></span>  
  
 <span data-ttu-id="154d4-115">자세한 내용은 [Microsoft Excel로 내보내기&#40;보고서 작성기 및 SSRS&#41;](report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md)에서 이 데이터로 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="154d4-115">For more information, see [Exporting to Microsoft Excel &#40;Report Builder and SSRS&#41;](report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="word-renderer-for-microsoft-word-2007-2010-and-microsoft-word-2003"></a><a name="WordRenderer"></a><span data-ttu-id="154d4-116">Microsoft Word 2007-2010 및 Microsoft Word 2003 용 word 렌더러</span><span class="sxs-lookup"><span data-stu-id="154d4-116">Word Renderer for Microsoft Word 2007-2010 and Microsoft Word 2003</span></span>  
 <span data-ttu-id="154d4-117">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]의 새로운 기능인 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Word 렌더링 확장 프로그램은 Word, Excel 및 PowerPoint용 [!INCLUDE[ofprword](../includes/ofprword-md.md)] Office 호환 기능 팩이 설치된 [!INCLUDE[ofprword](../includes/ofprword-md.md)] 2003뿐만 아니라 [!INCLUDE[msCoName](../includes/msconame-md.md)] 2007-2010과도 호환되는 Word 문서로 보고서를 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="154d4-117">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Word rendering extension, new in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], renders a report as a Word document that is compatible with [!INCLUDE[ofprword](../includes/ofprword-md.md)] 2007-2010 as well as [!INCLUDE[ofprword](../includes/ofprword-md.md)] 2003 with the [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Compatibility Pack for Word, Excel, and PowerPoint installed.</span></span> <span data-ttu-id="154d4-118">형식은 Office Open XML이고 파일 확장명은 docx입니다.</span><span class="sxs-lookup"><span data-stu-id="154d4-118">The format is Office Open XML and the file extension of files is docx.</span></span>  
  
 <span data-ttu-id="154d4-119">Word 2007-2010의 새로운 기능을 내보낸 보고서에서 사용할 수 있을 뿐만 아니라 보고서를 \*.docx 파일로 내보낼 경우 크기를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="154d4-119">In addition to making the features that are new in Word 2007-2010 available to exported reports, \*.docx files of exported reports tend to be smaller.</span></span> <span data-ttu-id="154d4-120">Word 렌더러를 사용하여 내보낸 보고서는 일반적으로 동일한 보고서를 Word 2003 렌더러를 사용하여 내보낼 때보다 매우 작습니다.</span><span class="sxs-lookup"><span data-stu-id="154d4-120">Reports exported by using the Word renderer are typically significantly smaller than the same reports exported by using the Word 2003 renderer.</span></span>  
  
 <span data-ttu-id="154d4-121">자세한 내용은 [Microsoft Word로 내보내기&#40;보고서 작성기 및 SSRS&#41;](report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md)에서 이 데이터로 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="154d4-121">For more information, see [Exporting to Microsoft Word &#40;Report Builder and SSRS&#41;](report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="154d4-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="154d4-122">See Also</span></span>  
 [<span data-ttu-id="154d4-123">SQL Server 2014의 보고서 작성기</span><span class="sxs-lookup"><span data-stu-id="154d4-123">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
