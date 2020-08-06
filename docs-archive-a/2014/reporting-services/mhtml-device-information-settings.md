---
title: MHTML 디바이스 정보 설정 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], MHTML rendering
- MHTML [Reporting Services]
ms.assetid: 60b85dd8-b4fb-4ad9-be6a-e7c89ac076fe
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 076a0179871775984799fc8ce5366a220f812867
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653241"
---
# <a name="mhtml-device-information-settings"></a><span data-ttu-id="4ba27-102">MHTML 디바이스 정보 설정</span><span class="sxs-lookup"><span data-stu-id="4ba27-102">MHTML Device Information Settings</span></span>
  <span data-ttu-id="4ba27-103">다음 표는 웹 보관 파일(MHTML) 형식으로 보고서를 렌더링하기 위한 디바이스 정보 설정을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba27-103">The following table lists the device information settings for rendering reports in Web archive (MHTML) format.</span></span>  
  
|<span data-ttu-id="4ba27-104">설정</span><span class="sxs-lookup"><span data-stu-id="4ba27-104">Setting</span></span>|<span data-ttu-id="4ba27-105">값</span><span class="sxs-lookup"><span data-stu-id="4ba27-105">Value</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="4ba27-106">**JavaScript**</span><span class="sxs-lookup"><span data-stu-id="4ba27-106">**JavaScript**</span></span>|<span data-ttu-id="4ba27-107">렌더링된 보고서에서 JavaScript가 지원되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4ba27-107">Indicates whether JavaScript is supported in the rendered report.</span></span>|  
|<span data-ttu-id="4ba27-108">**OutlookCompat**</span><span class="sxs-lookup"><span data-stu-id="4ba27-108">**OutlookCompat**</span></span>|<span data-ttu-id="4ba27-109">Outlook에서 보고서를 보기 좋게 만들어 주는 메타데이터와 함께 렌더링할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4ba27-109">Indicates whether to render with extra metadata that makes the report look better in Outlook.</span></span> <span data-ttu-id="4ba27-110">기본값은 `true`입니다.</span><span class="sxs-lookup"><span data-stu-id="4ba27-110">The default value is `true`.</span></span>|  
|<span data-ttu-id="4ba27-111">**MHTML 조각**</span><span class="sxs-lookup"><span data-stu-id="4ba27-111">**MHTML Fragment**</span></span>|<span data-ttu-id="4ba27-112">전체 MHTML 문서 대신 MHTML 조각이 만들어지는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4ba27-112">Indicates whether an MHTML fragment is created in place of a full MHTML document.</span></span> <span data-ttu-id="4ba27-113">MHTML 조각은 TABLE 요소에 보고서 내용을 포함하고 HTML 및 BODY 요소를 생략합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba27-113">An MHTML fragment includes the report content in a TABLE element and omits the HTML and BODY elements.</span></span> <span data-ttu-id="4ba27-114">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="4ba27-114">The default value is `false`.</span></span>|  
|<span data-ttu-id="4ba27-115">**DataVisualizationFitSizing**</span><span class="sxs-lookup"><span data-stu-id="4ba27-115">**DataVisualizationFitSizing**</span></span>|<span data-ttu-id="4ba27-116">테이블릭스 안에 있을 경우 데이터 시각화 맞춤 동작을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4ba27-116">Indicates data visualization fit behavior when inside a tablix.</span></span> <span data-ttu-id="4ba27-117">여기에는 차트, 계기 및 지도가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ba27-117">This includes chart, gauge, and map.</span></span><br /><br /> <span data-ttu-id="4ba27-118">가능한 값은 **근사치** 및 **정확한 수치**입니다.</span><span class="sxs-lookup"><span data-stu-id="4ba27-118">The possible values are **Approximate** and **Exact**.</span></span><br /><br /> <span data-ttu-id="4ba27-119">기본값은 **근사치**입니다.</span><span class="sxs-lookup"><span data-stu-id="4ba27-119">The default value is **Approximate**.</span></span> <span data-ttu-id="4ba27-120">**rsreportserver.config** 파일에서 설정이 제거될 경우 기본 동작은 **정확한 수치**입니다.</span><span class="sxs-lookup"><span data-stu-id="4ba27-120">If the setting is removed from the **rsreportserver.config** file then the default behavior is **Exact**.</span></span><br /><br /> <span data-ttu-id="4ba27-121">정확한 크기를 결정하기 위한 처리는 더 오래 걸릴 수 있기 때문에 **정확한 수치** 를 설정하면 성능에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ba27-121">Enabling **Exact** may have performance impact because the processing to determine the exact size may take longer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4ba27-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4ba27-122">See Also</span></span>  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 <span data-ttu-id="4ba27-123">[디바이스 정보 설정을 렌더링 확장 프로그램에 전달](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="4ba27-123">[Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span></span>  
 <span data-ttu-id="4ba27-124">[RSReportServer.Config의 렌더링 확장 프로그램 매개 변수를 사용자 지정](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="4ba27-124">[Customize Rendering Extension Parameters in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span></span>  
 [<span data-ttu-id="4ba27-125">기술 참조&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4ba27-125">Technical Reference &#40;SSRS&#41;</span></span>](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
