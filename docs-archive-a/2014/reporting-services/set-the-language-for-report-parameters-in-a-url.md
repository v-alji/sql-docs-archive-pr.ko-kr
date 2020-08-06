---
title: URL에 보고서 매개 변수 언어 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- overriding report language settings
- report servers [Reporting Services], language settings
- languages [Reporting Services]
- URL access [Reporting Services], language overrides
- international considerations [Reporting Services]
- global considerations [Reporting Services]
ms.assetid: e1ccf22f-80d6-45bc-aae0-f5f263275092
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8087a181906517bb60d4cd6839eed0681f52a5eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732380"
---
# <a name="set-the-language-for-report-parameters-in-a-url"></a><span data-ttu-id="e9a63-102">URL에 보고서 매개 변수 언어 설정</span><span class="sxs-lookup"><span data-stu-id="e9a63-102">Set the Language for Report Parameters in a URL</span></span>
  <span data-ttu-id="e9a63-103">*rs:ParameterLanguage* URL액세스 매개 변수를 사용하면 날짜, 시간, 통화, 숫자 등의 culture 구분 보고서 매개 변수가 브라우저 언어를 사용하여 해석되는 문제가 완화됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9a63-103">The *rs:ParameterLanguage* URL access parameter alleviates a problem in which culture-sensitive report parameters, such as dates, times, currency, and numbers, are interpreted using the browser language.</span></span> <span data-ttu-id="e9a63-104">*rs:ParameterLanguage*를 사용하면 URL이 브라우저와 상관없이 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9a63-104">With *rs:ParameterLanguage*, the URL is now interpreted independently of the browser.</span></span> <span data-ttu-id="e9a63-105">예를 들어 보고서 서버가 독일어 지역 설정으로 설정되었지만 사용자가 영어-미국으로 설정된 브라우저를 사용하여 URL을 통해 보고서에 액세스한다면 보고서 서버에 전달되는 매개 변수 값이 잘못 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9a63-105">For example, if the report server is set to a regional setting of German, but a user is accessing a report via a URL using a browser that is set to English-United States, parameter values that are passed to a report server will be misinterpreted.</span></span>  
  
 <span data-ttu-id="e9a63-106">보고서에 대해 다음 URL을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="e9a63-106">Consider the following URL to a report:</span></span>  
  
```  
http://myrshost/Reportserver?/SampleReports/Product+Line+Sales&rs:Command=Render&StartDate=4/10/2008&EndDate=11/10/2008  
```  
  
 <span data-ttu-id="e9a63-107">위의 경우 "de-de" 문화권에서 실행되는 서버는 전자 메일 구독 또는 하이퍼링크를 통해 URL을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a63-107">In the above case, the server, running under a culture of "de-de", generates a URL either through an e-mail subscription or a hyperlink.</span></span> <span data-ttu-id="e9a63-108">하이퍼링크에서는 보고서가 독일어 날짜/시간 표준에 따라 시작 날짜 2008년 10월 4일과 종료 날짜 2008년 10월 11일로 매개 변수화되어야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e9a63-108">The hyperlink indicates that the report should be parameterized by a start date of October 4, 2008 and an end date of October 11, 2008 according to German date/time standards.</span></span> <span data-ttu-id="e9a63-109">하지만 사용자가 "en-us"로 설정된 브라우저를 통해 URL에 액세스하면 미국 영어 날짜/시간 표준에 따라 서버에서 값을 2008년 4월 10일과 2008년 11월 10일로 해석하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9a63-109">However, a user that is accessing the URL through a browser set to "en-us" forces the server to interpret the values as April 10, 2008 and November 10, 2008 under United States English date/time standards.</span></span> <span data-ttu-id="e9a63-110">이 문제를 해결하려면 *rs:ParameterLanguage* 를 사용하여 매개 변수 해석을 위한 브라우저 언어를 다시 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9a63-110">To fix the problem, *rs:ParameterLanguage* can be used to override the browser language for parameter interpretation:</span></span>  
  
```  
http://myrshost/Reportserver?/SampleReports/Product+Line+Sales&rs:Command=Render&StartDate=4/10/2008&EndDate=11/10/2008&rs:ParameterLanguage=de-DE  
```  
  
 <span data-ttu-id="e9a63-111">URL 액세스 매개 변수 **rc:Parameters** 에 대한 **true** 및 *false*값 이외에 이제 **Collapsed**값을 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9a63-111">In addition to a value of **true** and **false** for the URL access parameter *rc:Parameters*, you can now pass a value of **Collapsed**.</span></span> <span data-ttu-id="e9a63-112">URL에서 *rc:Parameters*=**Collapsed** 를 사용할 경우 HTML 뷰어의 매개 변수 프롬프트 영역이 보이지 않도록 축소되지만 사용자가 표시 여부를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9a63-112">When using *rc:Parameters*=**Collapsed** on a URL, the parameter prompt area of the HTML viewer is collapsed out of sight, but can still be toggled by the user.</span></span> <span data-ttu-id="e9a63-113">**false** 값을 사용하면 HTML 뷰어 도구 모음에서 매개 변수 프롬프트 영역이 제거되어 최종 사용자가 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e9a63-113">A value of **false** removes the parameter prompt area from the HTML viewer toolbar and makes it unavailable to the end-user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9a63-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e9a63-114">See Also</span></span>  
 <span data-ttu-id="e9a63-115">[URL 액세스&#40;SSRS&#41;](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e9a63-115">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="e9a63-116">URL 액세스 매개 변수 참조</span><span class="sxs-lookup"><span data-stu-id="e9a63-116">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
