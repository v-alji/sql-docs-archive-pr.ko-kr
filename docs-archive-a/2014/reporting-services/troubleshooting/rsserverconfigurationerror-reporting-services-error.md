---
title: rsServerConfigurationError - Reporting Services 오류 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsServerConfigurationError
ms.assetid: 0913afc2-34b4-4713-b570-cfd5718975ac
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 02f8a18c42715d1f118920614eb425820130dacb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737858"
---
# <a name="rsserverconfigurationerror---reporting-services-error"></a><span data-ttu-id="1ccbb-102">rsServerConfigurationError - Reporting Services 오류</span><span class="sxs-lookup"><span data-stu-id="1ccbb-102">rsServerConfigurationError - Reporting Services Error</span></span>
    
## <a name="details"></a><span data-ttu-id="1ccbb-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="1ccbb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1ccbb-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="1ccbb-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="1ccbb-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="1ccbb-105">Event ID</span></span>|<span data-ttu-id="1ccbb-106">rsServerConfiguration</span><span class="sxs-lookup"><span data-stu-id="1ccbb-106">rsServerConfiguration</span></span>|  
|<span data-ttu-id="1ccbb-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="1ccbb-107">Event Source</span></span>|<span data-ttu-id="1ccbb-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span><span class="sxs-lookup"><span data-stu-id="1ccbb-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span></span>|  
|<span data-ttu-id="1ccbb-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="1ccbb-109">Component</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="1ccbb-110">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="1ccbb-110">Message Text</span></span>|<span data-ttu-id="1ccbb-111">보고서 서버에서 구성 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="1ccbb-111">The report server has encountered a configuration error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1ccbb-112">설명</span><span class="sxs-lookup"><span data-stu-id="1ccbb-112">Explanation</span></span>  
 <span data-ttu-id="1ccbb-113">이는 보고서 도구 또는 보고서 제작 도구에 잘못된 구성 설정이 있는 경우에 일반적으로 발생하는 오류로서,</span><span class="sxs-lookup"><span data-stu-id="1ccbb-113">This is a general purpose error that occurs when either the report server or a report authoring tool has invalid configuration settings.</span></span> <span data-ttu-id="1ccbb-114">일반적으로 오류의 실제 원인을 나타내는 두 번째 메시지와 함께 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ccbb-114">The error is usually accompanied by a second message that states the actual cause of the error.</span></span>  
  
 <span data-ttu-id="1ccbb-115">가능한 원인은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1ccbb-115">The following list summarizes possible causes:</span></span>  
  
-   <span data-ttu-id="1ccbb-116">RSReportServer.config 또는 RSReportDesigner.config 파일을 찾을 수 없거나 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1ccbb-116">The RSReportServer.config or RSReportDesigner.config file cannot be found or read.</span></span>  
  
-   <span data-ttu-id="1ccbb-117">구성 파일의 XML 요소가 누락되었거나 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1ccbb-117">XML elements in either configuration file are missing or invalid.</span></span>  
  
-   <span data-ttu-id="1ccbb-118">하나 이상의 XML 요소에 대한 값이 누락되었거나 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1ccbb-118">Values for one or more XML elements are missing or invalid.</span></span>  
  
-   <span data-ttu-id="1ccbb-119">레지스트리 설정이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1ccbb-119">Registry settings are invalid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1ccbb-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="1ccbb-120">User Action</span></span>  
 <span data-ttu-id="1ccbb-121">구성 파일을 수동으로 편집한 후에 이 오류가 발생하기 시작했다면 변경 내용을 제거하고 이전 값을 입력하거나 백업이 있는 경우 이전 버전을 복원하세요.</span><span class="sxs-lookup"><span data-stu-id="1ccbb-121">If this error began to occur after you manually edited a configuration file, remove your changes and enter the previous value, or restore a previous version if you have a backup.</span></span>  
  
 <span data-ttu-id="1ccbb-122">오류와 함께 발생 하는 추가 오류 메시지 정보를 검토 하려면 `rsServerConfiguration` \MICROSOFT SQL Server\MSRS12. \<instancename > 에 있는 보고서 서버 추적 로그 파일을 검토 합니다. \Reporting Services\logfiles</span><span class="sxs-lookup"><span data-stu-id="1ccbb-122">To review additional error message information that accompanies the `rsServerConfiguration` error, review the report server trace log files, which are located at \Microsoft SQL Server\MSRS12.\<instancename >\Reporting Services\LogFiles.</span></span> <span data-ttu-id="1ccbb-123">자세한 내용은 [Reporting Services 로그 파일 및 소스](../report-server/reporting-services-log-files-and-sources.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ccbb-123">For more information, see [Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md).</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="1ccbb-124">내부 전용</span><span class="sxs-lookup"><span data-stu-id="1ccbb-124">Internal-Only</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ccbb-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1ccbb-125">See Also</span></span>  
 <span data-ttu-id="1ccbb-126">[Reporting Services 구성 파일](../report-server/reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="1ccbb-126">[Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) </span></span>  
 [<span data-ttu-id="1ccbb-127">Reporting Services 구성 파일 수정&#40;RSreportserver.config&#41;</span><span class="sxs-lookup"><span data-stu-id="1ccbb-127">Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;</span></span>](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)  
  
  
