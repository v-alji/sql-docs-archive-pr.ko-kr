---
title: 보고서 서버 컴퓨터 이름 바꾸기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- renaming report servers
ms.assetid: 82fc4ba2-291a-4939-a025-271b8d687c54
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fe8f699c17f9e5f1e11406ac6e5c161488767ed1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660899"
---
# <a name="rename-a-report-server-computer"></a><span data-ttu-id="d6b50-102">보고서 서버 컴퓨터 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="d6b50-102">Rename a Report Server Computer</span></span>
  <span data-ttu-id="d6b50-103">컴퓨터 이름을 바꾸면 웹 서버 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 같은 컴퓨터에 있는 경우 이에 해당하는 이름이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6b50-103">Renaming a computer causes a corresponding name change for the Web server and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance (if it is on the same computer).</span></span> <span data-ttu-id="d6b50-104">컴퓨터 이름을 변경한 후 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에 액세스할 수 없는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6b50-104">In some cases, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] may not be accessible after a computer name change.</span></span> <span data-ttu-id="d6b50-105">컴퓨터 이름을 변경한 다음에는 이 항목의 단계를 사용하여 보고서 서버를 다시 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d6b50-105">Use the steps provided in this topic to reconfigure a report server after a computer name change.</span></span>  
  
## <a name="renaming-a-sql-server-database-engine"></a><span data-ttu-id="d6b50-106">SQL Server 데이터베이스 엔진 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="d6b50-106">Renaming a SQL Server Database Engine</span></span>  
 <span data-ttu-id="d6b50-107">보고서 서버 데이터베이스를 실행하는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스의 이름을 바꾸는 경우 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="d6b50-107">If you rename the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] instance that runs the report server database, do the following:</span></span>  
  
1.  <span data-ttu-id="d6b50-108">Reporting Services 구성 도구를 시작한 다음 이름이 바뀐 서버에 있는 보고서 서버 데이터베이스를 사용하는 보고서 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d6b50-108">Start the Reporting Services Configuration tool and connect to the report server that uses the report server database on the renamed server.</span></span>  
  
2.  <span data-ttu-id="d6b50-109">데이터베이스 설치 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d6b50-109">Open the Database Setup page.</span></span>  
  
3.  <span data-ttu-id="d6b50-110">**서버 이름**에서 해당 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이름을 입력하거나 선택한 다음 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d6b50-110">In **Server Name**, type or select the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] name, and then click **Connect**.</span></span>  
  
4.  <span data-ttu-id="d6b50-111">**적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d6b50-111">Click **Apply**.</span></span>  
  
 <span data-ttu-id="d6b50-112">보고서 서버에서 로컬 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스를 사용하는 경우 *(local)* 또는 *(local)\instancename* 을 사용하여 서버를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6b50-112">If the report server is using a local [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance, you can use *(local)* or *(local)\instancename* to specify the server.</span></span> <span data-ttu-id="d6b50-113">*(local)* 을 사용하여 서버를 참조하는 경우에는 서버 이름을 바꿔도 연결에 문제가 생기지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d6b50-113">If you use *(local)* to refer to the server, you can rename the server and the connections will continue to work.</span></span> <span data-ttu-id="d6b50-114">원격 서버를 사용하거나 서버 이름을 사용하여 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 구성하는 경우에는 서버 이름을 변경할 때마다 데이터베이스 연결 정보를 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6b50-114">If you are using a remote server, or if [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is configured using the server name, you must update the database connection information whenever the server name is changed.</span></span>  
  
## <a name="renaming-a-report-server-computer"></a><span data-ttu-id="d6b50-115">보고서 서버 컴퓨터 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="d6b50-115">Renaming a Report Server Computer</span></span>  
 <span data-ttu-id="d6b50-116">보고서 서버를 실행하는 컴퓨터의 이름을 바꾸는 경우 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="d6b50-116">If you rename a computer that runs a report server, do the following:</span></span>  
  
1.  <span data-ttu-id="d6b50-117">텍스트 편집기에서 **RSReportServer.config** 를 열고 `UrlRoot` 설정을 수정 하 여 새 서버 이름을 반영 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6b50-117">Open **RSReportServer.config** in a text editor and modify the `UrlRoot` setting to reflect the new server name.</span></span> <span data-ttu-id="d6b50-118">`UrlRoot` 설정은 배달 확장 프로그램에서 보고서 서버에 저장된 항목 액세스에 사용하는 URL을 작성하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6b50-118">The `UrlRoot` setting is used by delivery extensions to compose the URL used to access items stored on the report server.</span></span> <span data-ttu-id="d6b50-119">보고서 서버 URL 주소를 변경하려면 구독이 계속 보고서를 배달하도록 `UrlRoot` 설정을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6b50-119">Changing the report server URL address requires that you update the `UrlRoot` setting so that subscriptions continue to deliver reports as expected.</span></span>  
  
2.  <span data-ttu-id="d6b50-120">동일한 파일에서 설정하는 경우 `ReportServerUrl` 설정을 수정하여 새 서버 이름을 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="d6b50-120">In the same file, if it is set, modify the `ReportServerUrl` setting to reflect the new server name.</span></span> <span data-ttu-id="d6b50-121">이 설정이 모든 설치에 사용되는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="d6b50-121">Note that this setting is not used in every installation.</span></span> <span data-ttu-id="d6b50-122">이 설정이 비어 있는 경우 아무 작업도 수행하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="d6b50-122">If it is empty, do nothing.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d6b50-123">회사 네트워크에서 WINS(Windows Internet Naming Service)를 사용하는 경우 보고서 서버와 보고서 관리자가 일정 기간 동안 이전 이름으로 사용 가능하다고 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6b50-123">If you are using Windows Internet Naming Service (WINS) on your corporate network, the report server and Report Manager may continue to be available under the previous name for a period of time.</span></span> <span data-ttu-id="d6b50-124">WINS에서는 서비스하는 각 컴퓨터에 IP 주소를 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="d6b50-124">WINS maps an IP address to each computer it services.</span></span> <span data-ttu-id="d6b50-125">WINS에서 이름이 바뀐 컴퓨터의 IP 주소를 새로 고친 다음에는 더 이상 이전 컴퓨터 이름을 사용하여 보고서 서버나 보고서 관리자에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d6b50-125">After WINS refreshes the IP address for the renamed computer, the old computer name can no longer be used to access a report server or Report Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6b50-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d6b50-126">See Also</span></span>  
 <span data-ttu-id="d6b50-127">[Rsreportserver.config 구성 파일](rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="d6b50-127">[RSReportServer Configuration File](rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="d6b50-128">[Reporting Services 구성 관리자&#40;기본 모드&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="d6b50-128">[Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span></span>  
 <span data-ttu-id="d6b50-129">[Reporting Services 보고서 서버&#40;기본 모드&#41;](reporting-services-report-server-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="d6b50-129">[Reporting Services Report Server &#40;Native Mode&#41;](reporting-services-report-server-native-mode.md) </span></span>  
 <span data-ttu-id="d6b50-130">[보고서 서버 서비스 시작 및 중지](start-and-stop-the-report-server-service.md) </span><span class="sxs-lookup"><span data-stu-id="d6b50-130">[Start and Stop the Report Server Service](start-and-stop-the-report-server-service.md) </span></span>  
 [<span data-ttu-id="d6b50-131">rsconfig 유틸리티&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d6b50-131">rsconfig Utility &#40;SSRS&#41;</span></span>](../tools/rsconfig-utility-ssrs.md)  
  
  
