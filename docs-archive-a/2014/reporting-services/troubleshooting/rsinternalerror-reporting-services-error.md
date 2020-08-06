---
title: rsInternalError - Reporting Services 오류 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsInternalError
ms.assetid: 52613d52-fc78-4870-93f0-7d393ab9c335
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 85b88519df810f60c580ad2d6eb355dde236d081
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651456"
---
# <a name="rsinternalerror---reporting-services-error"></a><span data-ttu-id="60ceb-102">rsInternalError - Reporting Services 오류</span><span class="sxs-lookup"><span data-stu-id="60ceb-102">rsInternalError - Reporting Services Error</span></span>
    
## <a name="details"></a><span data-ttu-id="60ceb-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="60ceb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="60ceb-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="60ceb-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="60ceb-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="60ceb-105">Event ID</span></span>|<span data-ttu-id="60ceb-106">rsInternalError</span><span class="sxs-lookup"><span data-stu-id="60ceb-106">rsInternalError</span></span>|  
|<span data-ttu-id="60ceb-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="60ceb-107">Event Source</span></span>|<span data-ttu-id="60ceb-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span><span class="sxs-lookup"><span data-stu-id="60ceb-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span></span>|  
|<span data-ttu-id="60ceb-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="60ceb-109">Component</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="60ceb-110">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="60ceb-110">Message Text</span></span>|<span data-ttu-id="60ceb-111">보고서 서버에서 내부 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="60ceb-111">An internal error occurred on the report server.</span></span> <span data-ttu-id="60ceb-112">자세한 내용은 오류 로그를 참고하세요.</span><span class="sxs-lookup"><span data-stu-id="60ceb-112">See the error log for more details.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="60ceb-113">설명</span><span class="sxs-lookup"><span data-stu-id="60ceb-113">Explanation</span></span>  
 <span data-ttu-id="60ceb-114">이 메시지는 일반 오류 메시지이며 세부 정보를 제공하는 보다 자세한 오류가 제공되는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60ceb-114">This is a generic error message that is often followed by a more descriptive error that provides more detail.</span></span>  
  
 <span data-ttu-id="60ceb-115">내부 오류는 일반적인 오류가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="60ceb-115">Internal errors are uncommon.</span></span> <span data-ttu-id="60ceb-116">따라서 이 오류가 발생할 경우 보고서 서버 추적 로그에서 자세한 내용을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60ceb-116">If you get this error, more information is available in report server trace logs.</span></span> <span data-ttu-id="60ceb-117">또한 오류가 발생한 동일한 컴퓨터에서 로컬 관리자로 실행 중인 경우 호출 스택에서 자세한 내용을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60ceb-117">In addition, if you are running as local administrator on the same computer on which the error occurs, you can view the call stack for more information.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="60ceb-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="60ceb-118">User Action</span></span>  
 <span data-ttu-id="60ceb-119">이 메시지의 특정 원인을 확인 하려면 \Microsoft SQL Server\MSRS12. \<instancename > 에 있는 보고서 서버 로그 파일을 검토 합니다. \Reporting Services\logfiles</span><span class="sxs-lookup"><span data-stu-id="60ceb-119">To determine the specific cause for this message, review the report server log files, which are located at \Microsoft SQL Server\MSRS12.\<instancename >\Reporting Services\LogFiles.</span></span> <span data-ttu-id="60ceb-120">자세한 내용은 [Reporting Services 로그 파일 및 소스](../report-server/reporting-services-log-files-and-sources.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="60ceb-120">For more information, see [Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md).</span></span>  
  
 <span data-ttu-id="60ceb-121">호출 스택을 보려면 오류가 발생한 페이지를 마우스 오른쪽 단추로 클릭한 다음 **원본 보기**를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="60ceb-121">To view the call stack, right-click the page on which the error occurs and point to **View Source**.</span></span> <span data-ttu-id="60ceb-122">호출 스택을 보려면 오류가 발생한 컴퓨터에서 관리자 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="60ceb-122">Viewing the call stack requires administrator permissions on the same computer on which the error occurs.</span></span>  
  
 <span data-ttu-id="60ceb-123">추가로 제공되는 정보가 없는 경우 요청을 다시 시도할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60ceb-123">If there is no additional information available, you can try your request again.</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="60ceb-124">내부 전용</span><span class="sxs-lookup"><span data-stu-id="60ceb-124">Internal-Only</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60ceb-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="60ceb-125">See Also</span></span>  
 [<span data-ttu-id="60ceb-126">보고서 서버 서비스 시작 및 중지</span><span class="sxs-lookup"><span data-stu-id="60ceb-126">Start and Stop the Report Server Service</span></span>](../report-server/start-and-stop-the-report-server-service.md)  
  
  
