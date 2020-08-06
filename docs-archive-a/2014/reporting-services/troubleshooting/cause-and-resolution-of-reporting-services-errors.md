---
title: Reporting Services 오류의 원인 및 해결 방법 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- messages [Reporting Services]
- errors [Reporting Services]
- troubleshooting [Reporting Services], errors
ms.assetid: 3db0fef3-37f8-40d0-acc7-1928760dc0e9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fa98b9f760485b80f4fa4ac74f3b8008dc3bbec3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732308"
---
# <a name="cause-and-resolution-of-reporting-services-errors"></a><span data-ttu-id="ddc48-102">Reporting Services 오류의 원인 및 해결 방법</span><span class="sxs-lookup"><span data-stu-id="ddc48-102">Cause and Resolution of Reporting Services Errors</span></span>
  <span data-ttu-id="ddc48-103">이 항목에는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]와 관련한 몇 가지 오류의 원인 및 해결 방법 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddc48-103">This topic contains cause and resolution information for a number of errors related to [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="ddc48-104">이 섹션의 오류 메시지 항목에서는 오류 메시지, 가능한 원인 및 문제 해결을 위해 수행할 수 있는 동작에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc48-104">The error message topics in this section provide an explanation of the error message, possible causes, and any actions you can take to correct the problem.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ddc48-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="ddc48-105">In This Section</span></span>  
  
|<span data-ttu-id="ddc48-106">Error</span><span class="sxs-lookup"><span data-stu-id="ddc48-106">Error</span></span>|<span data-ttu-id="ddc48-107">메시지</span><span class="sxs-lookup"><span data-stu-id="ddc48-107">Message</span></span>|  
|-----------|-------------|  
|[<span data-ttu-id="ddc48-108">rsAccessedDenied - Reporting Services 오류</span><span class="sxs-lookup"><span data-stu-id="ddc48-108">rsAccessedDenied - Reporting Services Error</span></span>](rsaccesseddenied-reporting-services-error.md)|<span data-ttu-id="ddc48-109">'mydomain\myAccount' 사용자에게 부여된 권한으로는 이 작업을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ddc48-109">The permissions granted to user 'mydomain\myAccount' are insufficient for performing this operation.</span></span> <span data-ttu-id="ddc48-110">(rsAccessDenied) (ReportingServicesLibrary).</span><span class="sxs-lookup"><span data-stu-id="ddc48-110">(rsAccessDenied) (ReportingServicesLibrary).</span></span>|  
|[<span data-ttu-id="ddc48-111">rsInternalError - Reporting Services 오류</span><span class="sxs-lookup"><span data-stu-id="ddc48-111">rsInternalError - Reporting Services Error</span></span>](rsinternalerror-reporting-services-error.md)|<span data-ttu-id="ddc48-112">보고서 서버에서 내부 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="ddc48-112">An internal error occurred on the report server.</span></span> <span data-ttu-id="ddc48-113">자세한 내용은 오류 로그를 참고하세요.</span><span class="sxs-lookup"><span data-stu-id="ddc48-113">See the error log for more details.</span></span>|  
|[<span data-ttu-id="ddc48-114">rsModelGenerationError - Reporting Services 오류</span><span class="sxs-lookup"><span data-stu-id="ddc48-114">rsModelGenerationError - Reporting Services Error</span></span>](rsmodelgenerationerror-reporting-services-error.md)|<span data-ttu-id="ddc48-115">모델을 생성하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="ddc48-115">An error occurred while generating model.</span></span> <span data-ttu-id="ddc48-116">(rsModelGenerationError) (ReportingServicesLibrary) %1.</span><span class="sxs-lookup"><span data-stu-id="ddc48-116">(rsModelGenerationError) (ReportingServicesLibrary) %1.</span></span>|  
|[<span data-ttu-id="ddc48-117">rsProcessingError - Reporting Services 오류</span><span class="sxs-lookup"><span data-stu-id="ddc48-117">rsProcessingError - Reporting Services Error</span></span>](rsprocessingerror-reporting-services-error.md)|<span data-ttu-id="ddc48-118">보고서를 처리하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="ddc48-118">Errors have occurred in report processing.</span></span>|  
|[<span data-ttu-id="ddc48-119">rsServerConfigurationError - Reporting Services 오류</span><span class="sxs-lookup"><span data-stu-id="ddc48-119">rsServerConfigurationError - Reporting Services Error</span></span>](rsserverconfigurationerror-reporting-services-error.md)|<span data-ttu-id="ddc48-120">보고서 서버에서 구성 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="ddc48-120">The report server has encountered a configuration error.</span></span>|  
|[<span data-ttu-id="ddc48-121">rrRenderingError - Reporting Services 오류</span><span class="sxs-lookup"><span data-stu-id="ddc48-121">rrRenderingError - Reporting Services Error</span></span>](rrrenderingerror-reporting-services-error.md)|<span data-ttu-id="ddc48-122">보고서를 렌더링하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="ddc48-122">An error occurred during rendering of the report.</span></span> <span data-ttu-id="ddc48-123">(rrRenderingError) %1.</span><span class="sxs-lookup"><span data-stu-id="ddc48-123">(rrRenderingError) %1.</span></span>|  
|[<span data-ttu-id="ddc48-124">보고서 서버 Windows 서비스&#40;MSSQLServer&#41; 107</span><span class="sxs-lookup"><span data-stu-id="ddc48-124">Report Server Windows Service &#40;MSSQLServer&#41; 107</span></span>](../../relational-databases/errors-events/mssqlserver-107-database-engine-error.md)|<span data-ttu-id="ddc48-125">Report Server Windows service (MSSQLSERVER)에서 보고서 서버 데이터베이스에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ddc48-125">Report Server Windows service (MSSQLSERVER) cannot connect to the report server database.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ddc48-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ddc48-126">See Also</span></span>  
 <span data-ttu-id="ddc48-127">[Reporting Services 로그 파일 및 소스](../report-server/reporting-services-log-files-and-sources.md) </span><span class="sxs-lookup"><span data-stu-id="ddc48-127">[Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md) </span></span>  
 [<span data-ttu-id="ddc48-128">오류 및 이벤트 참조&#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ddc48-128">Errors and Events Reference &#40;Reporting Services&#41;</span></span>](errors-and-events-reference-reporting-services.md)  
  
  
