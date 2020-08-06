---
title: 보고서 서버 서비스 시작 및 중지 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- stopping Report Server service
- Report Server Windows service, starting
- Report Server service, starting
- starting Report Server service
ms.assetid: 6ec69ac3-27b0-472d-91e1-733af9078ed2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b751fd1a31830ffdc96cb296fa39d08e396c8c50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650625"
---
# <a name="start-and-stop-the-report-server-service"></a><span data-ttu-id="9bfbb-102">보고서 서버 서비스 시작 및 중지</span><span class="sxs-lookup"><span data-stu-id="9bfbb-102">Start and Stop the Report Server Service</span></span>
  <span data-ttu-id="9bfbb-103">보고서 서버는 보고서 서버 웹 서비스, 보고서 관리자 및 백그라운드 처리 애플리케이션을 포함하는 Windows 서비스로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-103">A report server is implemented as a Windows service that contains the Report Server Web service, Report Manager, and a background processing application.</span></span> <span data-ttu-id="9bfbb-104">보고서 서버 기능을 사용하려면 서비스를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-104">The service must be running if you want to use any report server functionality.</span></span> <span data-ttu-id="9bfbb-105">서비스를 중지하면 모든 보고서 서버 작업이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-105">Stopping the service stops all report server operations.</span></span>  
  
 <span data-ttu-id="9bfbb-106">서비스가 중지된 동안 서비스 실행 중에 발생했을 수 있는 예약된 보고서 및 구독 처리 요청이 큐에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-106">While the service is stopped, requests for scheduled report and subscription processing that would have occurred had the service been running are added to the queue.</span></span> <span data-ttu-id="9bfbb-107">이는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 실행한 작업이 이벤트를 만들기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-107">This is because jobs that are run by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent create the events.</span></span> <span data-ttu-id="9bfbb-108">서비스가 해제된 동안 작업 백로그가 발생하지 않도록 하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트도 중지하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-108">If you want to avoid a backlog of operations while the service is off, consider stopping [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent as well.</span></span>  
  
 <span data-ttu-id="9bfbb-109">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자 및 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows의 서비스 도구를 비롯한 다양한 도구를 사용하여 보고서 서버 서비스를 시작 또는 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-109">You can use a variety of tools to start or stop the Report Server service, including the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, and the Services tool provided in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.</span></span>  
  
 <span data-ttu-id="9bfbb-110">서비스 계정을 바꾸는 경우처럼 서비스를 시작하거나 중지하는 것 외에 다른 작업을 수행하려면 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-110">If you are doing more than starting or stopping the service, such as changing the service account, you must use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool.</span></span> <span data-ttu-id="9bfbb-111">다른 도구를 사용하여 서비스 계정을 변경하면 설치된 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-111">Using other tools to change the service account can break your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation.</span></span> <span data-ttu-id="9bfbb-112">자세한 내용은 [보고서 서버 서비스 계정 구성&#40;SSRS 구성 관리자&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-112">For more information, see [Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="9bfbb-113">이 서비스를 일시 중지하고 다시 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-113">You cannot pause and resume the service.</span></span> <span data-ttu-id="9bfbb-114">시작 매개 변수가 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-114">There are no start parameters.</span></span> <span data-ttu-id="9bfbb-115">명시적 종속 관계는 없지만 보고서 서버에서 구독이나 예약된 보고서 작업을 지원하는 경우에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 실행 중이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-115">Although there are no explicit dependencies, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be running if you support any subscriptions or scheduled report operations on the report server.</span></span>  
  
### <a name="to-start-or-stop-the-service-using-the-reporting-services-configuration-tool"></a><span data-ttu-id="9bfbb-116">Reporting Services 구성 도구를 사용하여 서비스를 시작하거나 중지하려면</span><span class="sxs-lookup"><span data-stu-id="9bfbb-116">To start or stop the service using the Reporting Services Configuration tool</span></span>  
  
1.  <span data-ttu-id="9bfbb-117">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 시작한 후 보고서 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-117">Start [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and connect to the report server.</span></span>  
  
2.  <span data-ttu-id="9bfbb-118">보고서 서버 상태 페이지에서 **중지** 또는 **시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-118">On the Report Server Status page, click **Stop** or **Start**.</span></span>  
  
### <a name="to-start-or-stop-the-service-using-services-in-administrative-tools"></a><span data-ttu-id="9bfbb-119">관리 도구의 서비스를 사용하여 서비스를 시작하거나 중지하려면</span><span class="sxs-lookup"><span data-stu-id="9bfbb-119">To start or stop the service using Services in Administrative Tools</span></span>  
  
-   <span data-ttu-id="9bfbb-120">관리 도구, 서비스를 차례로 열고 **SQL Server Reporting Services(MSSQLSERVER)** 를 마우스 오른쪽 단추로 클릭한 다음 **중지** 또는 **다시 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-120">In Administrative Tools, open Services, right-click **SQL Server Reporting Services (MSSQLSERVER)**, and click **Stop** or **Restart**.</span></span>  
  
 <span data-ttu-id="9bfbb-121">여러 인스턴스를 실행하고 있거나 보고서 서버를 명명된 인스턴스로 실행하는 경우 괄호 안의 인스턴스 이름이 중지 또는 다시 시작하려는 보고서 서버 인스턴스에 해당하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-121">If you are running multiple instance or if the report server is running as a named instance, verify that the instance name in parentheses corresponds to the report server instance you want to stop or restart.</span></span>  
  
### <a name="to-start-or-stop-the-service-using-sql-server-configuration-manager"></a><span data-ttu-id="9bfbb-122">SQL Server 구성 관리자를 사용하여 서비스를 시작하거나 중지하려면</span><span class="sxs-lookup"><span data-stu-id="9bfbb-122">To start or stop the service using SQL Server Configuration Manager</span></span>  
  
1.  <span data-ttu-id="9bfbb-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-123">Start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
2.  <span data-ttu-id="9bfbb-124">SQL Server 서비스를 선택하고 **SQL Server Reporting Services**를 마우스 오른쪽 단추로 클릭한 다음 **중지** 또는 **다시 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-124">Select SQL Server Services, right-click **SQL Server Reporting Services**, and click **Stop** or **Restart**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bfbb-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9bfbb-125">See Also</span></span>  
 [<span data-ttu-id="9bfbb-126">Reporting Services 구성 관리자&#40;기본 모드&#41;</span><span class="sxs-lookup"><span data-stu-id="9bfbb-126">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
