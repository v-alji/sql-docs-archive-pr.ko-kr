---
title: 보고서 서버 Windows 서비스(MSSQLServer) 107 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- MSSQLServer 107 error
ms.assetid: 52b5704b-27f9-400a-a821-d8fa0786afe4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8651f98b47b698fbe3cfb6a152b9220a84ed7256
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649930"
---
# <a name="report-server-windows-service-mssqlserver-107"></a><span data-ttu-id="be499-102">Report Server Windows Service (MSSQLServer) 107</span><span class="sxs-lookup"><span data-stu-id="be499-102">Report Server Windows Service (MSSQLServer) 107</span></span>
    
## <a name="details"></a><span data-ttu-id="be499-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="be499-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="be499-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="be499-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="be499-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="be499-105">Event ID</span></span>|<span data-ttu-id="be499-106">107</span><span class="sxs-lookup"><span data-stu-id="be499-106">107</span></span>|  
|<span data-ttu-id="be499-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="be499-107">Event Source</span></span>|<span data-ttu-id="be499-108">Report Server Windows Service</span><span class="sxs-lookup"><span data-stu-id="be499-108">Report Server Windows Service</span></span>|  
|<span data-ttu-id="be499-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="be499-109">Component</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="be499-110">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="be499-110">Message Text</span></span>|<span data-ttu-id="be499-111">Report Server Windows Service (MSSQLSERVER)에서 보고서 서버 데이터베이스에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="be499-111">Report Server Windows Service (MSSQLSERVER) cannot connect to the report server database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="be499-112">설명</span><span class="sxs-lookup"><span data-stu-id="be499-112">Explanation</span></span>  
 <span data-ttu-id="be499-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 보고서 서버 서비스를 보고서 서버 데이터베이스에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="be499-113">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Report Server service cannot connect to the report server database.</span></span> <span data-ttu-id="be499-114">이 오류는 보고서 서버 데이터베이스에 연결할 수 없는 경우 서비스를 다시 시작하면 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="be499-114">This error occurs during a service restart if a connection to the report server database cannot be established.</span></span> <span data-ttu-id="be499-115">이 오류가 발생하는 조건은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="be499-115">Conditions under which this error occurs include the following:</span></span>  
  
-   <span data-ttu-id="be499-116">보고서 서버 서비스가 시작될 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 서비스가 실행되고 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="be499-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] service is not running when the Report Server service starts.</span></span>  
  
-   <span data-ttu-id="be499-117">원격 연결 또는 TCP/IP 프로토콜이 설정되지 않아 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 서비스에 대한 연결이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="be499-117">The connection to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service fails because remote connections or the TCP/IP protocol is not enabled.</span></span>  
  
-   <span data-ttu-id="be499-118">보고서 서버 데이터베이스가 올바르게 구성되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="be499-118">The report server database is not configured correctly.</span></span>  
  
-   <span data-ttu-id="be499-119">서비스 계정이 올바르게 구성되어 있지 않거나 계정에 보고서 서버 데이터베이스에 대한 사용 권한이 더 이상 없습니다.</span><span class="sxs-lookup"><span data-stu-id="be499-119">The service account is not configured correctly, or the account no longer has permissions on the report server database.</span></span> <span data-ttu-id="be499-120">이 조건은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 사용하지 않고 계정 또는 보고서 서버 데이터베이스를 설정한 경우에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be499-120">This can occur if you do not use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool to set up the account or the report server database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="be499-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="be499-121">User Action</span></span>  
 <span data-ttu-id="be499-122">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 서비스가 실행되고 있지 않은 경우 해당 서비스를 시작하고 TCP/IP에 대한 원격 연결이 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="be499-122">Start the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service if it is not running and check that remote connections are enabled for TCP/IP protocol.</span></span>  
  
 <span data-ttu-id="be499-123">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 사용하여 보고서 서버 데이터베이스와 서비스 계정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="be499-123">Use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool to configure the report server database and service account.</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="be499-124">내부 전용</span><span class="sxs-lookup"><span data-stu-id="be499-124">Internal-Only</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be499-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="be499-125">See Also</span></span>  
 <span data-ttu-id="be499-126">[보고서 서버 서비스 계정 구성&#40;SSRS 구성 관리자&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="be499-126">[Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="be499-127">[Reporting Services 구성 관리자&#40;기본 모드&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="be499-127">[Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span></span>  
 [<span data-ttu-id="be499-128">보고서 서버 서비스 시작 및 중지</span><span class="sxs-lookup"><span data-stu-id="be499-128">Start and Stop the Report Server Service</span></span>](../report-server/start-and-stop-the-report-server-service.md)  
  
  
