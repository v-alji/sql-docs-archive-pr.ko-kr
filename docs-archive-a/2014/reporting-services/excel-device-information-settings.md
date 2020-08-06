---
title: Excel 디바이스 정보 설정 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], Excel rendering
- Excel [Reporting Services], rendering
ms.assetid: bb5f3566-f033-4470-be87-1f52fb7a4ab6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d71c83195c8f91984bbbce95bd00402928fdb36e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735051"
---
# <a name="excel-device-information-settings"></a><span data-ttu-id="8d7f7-102">Excel 디바이스 정보 설정</span><span class="sxs-lookup"><span data-stu-id="8d7f7-102">Excel Device Information Settings</span></span>
  <span data-ttu-id="8d7f7-103">다음 표는 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 형식으로 렌더링하기 위한 디바이스 정보 설정을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8d7f7-103">The following table lists the device information settings for rendering in [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] format.</span></span>  
  
|<span data-ttu-id="8d7f7-104">설정</span><span class="sxs-lookup"><span data-stu-id="8d7f7-104">Setting</span></span>|<span data-ttu-id="8d7f7-105">값</span><span class="sxs-lookup"><span data-stu-id="8d7f7-105">Value</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="8d7f7-106">**OmitDocumentMap**</span><span class="sxs-lookup"><span data-stu-id="8d7f7-106">**OmitDocumentMap**</span></span>|<span data-ttu-id="8d7f7-107">지원하는 보고서에 대한 문서 구조를 생략할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8d7f7-107">Indicates whether to omit the document map for reports that support it.</span></span> <span data-ttu-id="8d7f7-108">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="8d7f7-108">The default value is `false`.</span></span>|  
|<span data-ttu-id="8d7f7-109">**OmitFormulas**</span><span class="sxs-lookup"><span data-stu-id="8d7f7-109">**OmitFormulas**</span></span>|<span data-ttu-id="8d7f7-110">렌더링된 보고서에서 수식을 생략할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8d7f7-110">Indicates whether to omit formulas from the rendered report.</span></span> <span data-ttu-id="8d7f7-111">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="8d7f7-111">The default value is `false`.</span></span>|  
|<span data-ttu-id="8d7f7-112">`SimplePageHeade`rs</span><span class="sxs-lookup"><span data-stu-id="8d7f7-112">`SimplePageHeade`rs</span></span>|<span data-ttu-id="8d7f7-113">보고서의 페이지 머리글이 Excel 페이지 머리글로 렌더링되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8d7f7-113">Indicates whether the page header of the report is rendered to the Excel page header.</span></span> <span data-ttu-id="8d7f7-114">`false` 값은 페이지 머리글이 워크시트의 첫 행에 렌더링됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8d7f7-114">A value of `false` indicates that the page header is rendered to the first row of the worksheet.</span></span> <span data-ttu-id="8d7f7-115">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="8d7f7-115">The default value is `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8d7f7-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8d7f7-116">See Also</span></span>  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 <span data-ttu-id="8d7f7-117">[장치 정보 설정을 렌더링 확장 프로그램에 전달](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="8d7f7-117">[Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span></span>  
 <span data-ttu-id="8d7f7-118">[RSReportServer.Config에서 렌더링 확장 프로그램 매개 변수 사용자 지정](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="8d7f7-118">[Customize Rendering Extension Parameters in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span></span>  
 [<span data-ttu-id="8d7f7-119">기술 참조&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8d7f7-119">Technical Reference &#40;SSRS&#41;</span></span>](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
