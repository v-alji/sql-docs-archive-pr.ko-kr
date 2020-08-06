---
title: ATOM 디바이스 정보 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fe4a56a4-5552-423c-85c1-895e2e212fee
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bdbac1500063accf868d4b538b82ba9f3b5aebb0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650814"
---
# <a name="atom-device-information-settings"></a><span data-ttu-id="045a6-102">ATOM 디바이스 정보 설정</span><span class="sxs-lookup"><span data-stu-id="045a6-102">ATOM Device Information Settings</span></span>
  <span data-ttu-id="045a6-103">Atom 렌더링 확장 프로그램의 디바이스 정보 설정은 사용할 문자 인코딩 및 Atom 피드 이름 전송을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="045a6-103">The device information settings for the Atom rendering extension support submittal of the name of an Atom feed and character encoding to use.</span></span>  
  
 <span data-ttu-id="045a6-104">다음 표에서는 데이터 서비스 문서로 렌더링하기 위한 디바이스 정보 설정을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="045a6-104">The following table lists the device information settings for rendering to a data service document.</span></span>  
  
|<span data-ttu-id="045a6-105">설정</span><span class="sxs-lookup"><span data-stu-id="045a6-105">Setting</span></span>|<span data-ttu-id="045a6-106">값</span><span class="sxs-lookup"><span data-stu-id="045a6-106">Value</span></span>|  
|-------------|-----------|  
|`DataFeed`|<span data-ttu-id="045a6-107">지정되면 이 설정에 제공된 피드 이름에 해당하는 Atom 피드를 렌더링하고,</span><span class="sxs-lookup"><span data-stu-id="045a6-107">If specified, renders the Atom feed corresponding to the feed name provided in this setting.</span></span> <span data-ttu-id="045a6-108">지정되지 않으면 보고서의 Atom 서비스 문서를 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="045a6-108">If not, renders the Atom service document for the report.</span></span> <span data-ttu-id="045a6-109">데이터 피드의 고유한 자동 생성 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="045a6-109">The unique auto-generated identifier of the data feed.</span></span> <span data-ttu-id="045a6-110">이 값은 내부적으로 사용되며 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="045a6-110">This  value is used internally and you should not change it.</span></span>|  
|<span data-ttu-id="045a6-111">**인코딩**</span><span class="sxs-lookup"><span data-stu-id="045a6-111">**Encoding**</span></span>|<span data-ttu-id="045a6-112">.NET Framework에서 지원하는 문자 인코딩의 IANA(Internet Assigned Numbers Authority) 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="045a6-112">The Internet Assigned Numbers Authority (IANA) name of a character encoding that is supported by the .NET Framework.</span></span> <span data-ttu-id="045a6-113">기본값은 `UTF-8`입니다.</span><span class="sxs-lookup"><span data-stu-id="045a6-113">The default value is `UTF-8`.</span></span> <span data-ttu-id="045a6-114">다른 값의 예로 ASCII, UTF-7 및 UTF-16을 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="045a6-114">Examples of other values include ASCII, UTF-7, and UTF-16.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="045a6-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="045a6-115">See Also</span></span>  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 <span data-ttu-id="045a6-116">[장치 정보 설정을 렌더링 확장 프로그램에 전달](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="045a6-116">[Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span></span>  
 <span data-ttu-id="045a6-117">[RSReportServer.Config에서 렌더링 확장 프로그램 매개 변수 사용자 지정](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="045a6-117">[Customize Rendering Extension Parameters in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span></span>  
 [<span data-ttu-id="045a6-118">기술 참조&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="045a6-118">Technical Reference &#40;SSRS&#41;</span></span>](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
