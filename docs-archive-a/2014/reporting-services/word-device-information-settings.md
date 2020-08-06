---
title: Word 디바이스 정보 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Word [Reporting Services]
- device information settings [Reporting Services], Word
ms.assetid: 28146498-fae7-4b13-b47f-6ec05aa8e057
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ddd145c5073003a8dc189e3ed9b1bbb25dc11d09
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639266"
---
# <a name="word-device-information-settings"></a><span data-ttu-id="04096-102">Word 디바이스 정보 설정</span><span class="sxs-lookup"><span data-stu-id="04096-102">Word Device Information Settings</span></span>
  <span data-ttu-id="04096-103">다음 표는 [!INCLUDE[ofprword](../includes/ofprword-md.md)] 형식으로 렌더링하기 위한 디바이스 정보 설정을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="04096-103">The following table lists the device information settings for rendering in [!INCLUDE[ofprword](../includes/ofprword-md.md)] format.</span></span>  
  
|<span data-ttu-id="04096-104">설정</span><span class="sxs-lookup"><span data-stu-id="04096-104">Setting</span></span>|<span data-ttu-id="04096-105">값</span><span class="sxs-lookup"><span data-stu-id="04096-105">Value</span></span>|  
|-------------|-----------|  
|`AutoFit`|<span data-ttu-id="04096-106">`False`.</span><span class="sxs-lookup"><span data-stu-id="04096-106">`False`.</span></span> <span data-ttu-id="04096-107">자동 맞춤이 임의의 Word 테이블에서 `false`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="04096-107">AutoFit is set to `false` set on any Word table.</span></span><br /><br /> <span data-ttu-id="04096-108">`True`.</span><span class="sxs-lookup"><span data-stu-id="04096-108">`True`.</span></span> <span data-ttu-id="04096-109">자동 맞춤이 모든 Word 테이블에서 `true`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="04096-109">AutoFit is set to `true` on every Word table.</span></span><br /><br /> <span data-ttu-id="04096-110">`Never`.</span><span class="sxs-lookup"><span data-stu-id="04096-110">`Never`.</span></span> <span data-ttu-id="04096-111">자동 맞춤 값이 Word 테이블에서 설정되지 않으며 Word 기본값으로 되돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="04096-111">AutoFit values are not set on any Word table and behavior reverts to the Word default.</span></span><br /><br /> <span data-ttu-id="04096-112">`Default`.</span><span class="sxs-lookup"><span data-stu-id="04096-112">`Default`.</span></span> <span data-ttu-id="04096-113">자동 맞춤이 논리 페이지당 실제 그리기 영역(여백을 제외한 실제 페이지 너비)보다 좁은 테이블에서 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="04096-113">AutoFit is set on tables that are narrower than the physical drawing area (physical page width excluding margins) per logical page.</span></span>|  
|`ExpandToggles`|<span data-ttu-id="04096-114">표시하거나 숨길 수 있는 모든 항목이 전체 확장 상태로 렌더링되어야 하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="04096-114">Indicates whether all items that can be toggled should render in their fully-expanded state.</span></span> <span data-ttu-id="04096-115">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="04096-115">The default value is `false`.</span></span>|  
|`FixedPageWidth`|<span data-ttu-id="04096-116">DOC 파일에 적용되는 페이지 너비가 보고서 본문의 가장 큰 페이지 너비에 맞게 늘어나는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="04096-116">Indicates whether the Page Width written to the DOC file will grow to accommodate the width of the largest page in the Report Body.</span></span> <span data-ttu-id="04096-117">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="04096-117">The default value is `false`.</span></span>|  
|<span data-ttu-id="04096-118">**OmitHyperlinks**</span><span class="sxs-lookup"><span data-stu-id="04096-118">**OmitHyperlinks**</span></span>|<span data-ttu-id="04096-119">하이퍼링크 동작이 설정된 모든 항목에 대한 하이퍼링크 동작을 생략할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="04096-119">Indicates whether to omit the Hyperlink action on all items where it is set.</span></span> <span data-ttu-id="04096-120">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="04096-120">The default value is `false`</span></span>|  
|`OmitDrillthroughs`|<span data-ttu-id="04096-121">드릴스루 동작이 설정된 모든 항목에 대한 드릴스루 동작을 생략할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="04096-121">Indicates whether to omit the Drillthrough action on all items where it is set.</span></span> <span data-ttu-id="04096-122">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="04096-122">The default value is `false`</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04096-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="04096-123">See Also</span></span>  
 <span data-ttu-id="04096-124">[장치 정보 설정을 렌더링 확장 프로그램에 전달](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="04096-124">[Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span></span>  
 <span data-ttu-id="04096-125">[RSReportServer.Config에서 렌더링 확장 프로그램 매개 변수 사용자 지정](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="04096-125">[Customize Rendering Extension Parameters in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span></span>  
 [<span data-ttu-id="04096-126">기술 참조&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="04096-126">Technical Reference &#40;SSRS&#41;</span></span>](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
