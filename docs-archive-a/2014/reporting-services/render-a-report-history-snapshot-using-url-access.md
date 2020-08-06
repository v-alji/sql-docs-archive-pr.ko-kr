---
title: URL 액세스를 사용하여 보고서 기록 스냅샷 렌더링 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- URL access [Reporting Services], report history
- history snapshots [Reporting Services]
- historical data [Reporting Services]
- snapshots [Reporting Services], URL access
- snapshots [Reporting Services], rendering report history
ms.assetid: 3f87f82d-0e61-4492-9c4b-f5238c39e8cd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 67854a39ab7e38289627d03ac00cc4b2a6dca6f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650786"
---
# <a name="render-a-report-history-snapshot-using-url-access"></a><span data-ttu-id="c4276-102">URL 액세스를 사용하여 보고서 기록 스냅샷 렌더링</span><span class="sxs-lookup"><span data-stu-id="c4276-102">Render a Report History Snapshot Using URL Access</span></span>
  <span data-ttu-id="c4276-103">*rs:Snapshot* 매개 변수를 제공하고 이 값을 유효한 스냅샷 ID로 설정하여 보고서 기록 스냅샷을 기반으로 한 보고서를 렌더링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4276-103">You can render a report based on a report history snapshot by supplying the *rs:Snapshot* parameter and setting its value to a valid snapshot ID.</span></span> <span data-ttu-id="c4276-104">매개 변수 값은 ISO(국제 표준화 기구) 8601 표준을 기반으로 하여 YYYY-MM-DDTHH:MM:SS 형식으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c4276-104">The parameter value is in the format YYYY-MM-DDTHH:MM:SS, based on the International Organization for Standardization (ISO) 8601 standard.</span></span>  
  
 <span data-ttu-id="c4276-105">이 매개 변수를 생략할 경우 보고서는 보고서 서버의 보고서 실행 및 캐시 관리 옵션 설정에 따라 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4276-105">If you omit this parameter, the report is rendered according to the report execution and cache management option settings of the report server.</span></span> <span data-ttu-id="c4276-106">보고서 실행에 대한 자세한 내용은 [보고서 처리 속성 설정](report-server/set-report-processing-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c4276-106">For more information about report execution, see [Set Report Processing Properties](report-server/set-report-processing-properties.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4276-107">예제</span><span class="sxs-lookup"><span data-stu-id="c4276-107">Example</span></span>  
 <span data-ttu-id="c4276-108">다음 예는 보고서 기록 스냅샷을 검색하는 URL을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c4276-108">The following example shows a URL that retrieves a report history snapshot:</span></span>  
  
```  
http://myrshost/reportserver?/SampleReports/Company Sales&rs:Snapshot=2003-04-07T13:40:02  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4276-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c4276-109">See Also</span></span>  
 <span data-ttu-id="c4276-110">[URL 액세스&#40;SSRS&#41;](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c4276-110">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="c4276-111">URL 액세스 매개 변수 참조</span><span class="sxs-lookup"><span data-stu-id="c4276-111">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
