---
title: 중앙 관리를 실행 하는 웹 프런트 엔드 서버에 ADOMD.NET 설치 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c2372180-e847-4cdb-b267-4befac3faf7e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0d9f52bf612c4878a8dacd4f5acfdcc135ae115e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646829"
---
# <a name="install-adomdnet-on-web-front-end-servers-running-central-administration"></a><span data-ttu-id="c876c-102">중앙 관리를 실행하는 웹 프런트 엔드 서버에 ADOMD.NET 설치</span><span class="sxs-lookup"><span data-stu-id="c876c-102">Install ADOMD.NET on Web Front-End Servers Running Central Administration</span></span>
  <span data-ttu-id="c876c-103">Excel Services 또는 SharePoint용 PowerPivot이 없는 중앙 관리의 토폴로지가 포함된 팜에 SharePoint용 PowerPivot을 설치하는 경우, PowerPivot 관리 대시보드의 모든 기본 제공 보고서에 액세스하려면 Microsoft ADOMD.NET 클라이언트 라이브러리를 다운로드하여 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c876c-103">If you install PowerPivot for SharePoint into a farm that has the topology of Central Administration, without Excel Services or PowerPivot for SharePoint, download and install the Microsoft ADOMD.NET client library if you want full access to the built-in reports in the PowerPivot management dashboard.</span></span> <span data-ttu-id="c876c-104">대시보드의 일부 보고서는 ADOMD.NET을 사용하여 팜의 PowerPivot 쿼리 처리 및 서버 상태에 대한 보고 데이터를 제공하는 내부 데이터에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="c876c-104">Some reports in the dashboard use ADOMD.NET to access internal data that provides reporting data on PowerPivot query processing and server health in the farm.</span></span>  
  
 <span data-ttu-id="c876c-105">**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="c876c-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010</span></span>  
  
 <span data-ttu-id="c876c-106">SharePoint 2013의 경우 공급자가 SQL Server 기능 팩에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c876c-106">For SharePoint 2013, the provider is included in the SQL Server feature pack.</span></span> <span data-ttu-id="c876c-107">spPowerPivot.msi를 다운로드하는 방법에 대한 자세한 내용은 [Microsoft SQL Server 2014 기능 팩](https://www.microsoft.com/download/details.aspx?id=35577)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c876c-107">For information on how to download spPowerPivot.msi, see [Microsoft SQL Server 2014 Feature Pack](https://www.microsoft.com/download/details.aspx?id=35577)</span></span>  
  
### <a name="download-and-install-the-client-library"></a><span data-ttu-id="c876c-108">클라이언트 라이브러리 다운로드 및 설치</span><span class="sxs-lookup"><span data-stu-id="c876c-108">Download and install the client library</span></span>  
  
1.  <span data-ttu-id="c876c-109">[SQL Server 2014 기능 팩 페이지](https://go.microsoft.com/fwlink/?LinkID=296473)에서 Microsoft ADOMD.NET을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="c876c-109">On the [SQL Server 2014 Feature Pack page](https://go.microsoft.com/fwlink/?LinkID=296473), find Microsoft ADOMD.NET.</span></span>  
  
2.  <span data-ttu-id="c876c-110">`SQL_AS_ADOMD.msi` 설치 프로그램의 x64 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="c876c-110">Download the x64 Package of the `SQL_AS_ADOMD.msi` installation program.</span></span>  
  
3.  <span data-ttu-id="c876c-111">.msi를 실행하여 라이브러리를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c876c-111">Run the .msi to install the library.</span></span>  
  
4.  <span data-ttu-id="c876c-112">설치가 완료되면 IIS를 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c876c-112">Reset IIS after installation is finished.</span></span> <span data-ttu-id="c876c-113">관리 명령 프롬프트를 열고 **IISRESET**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c876c-113">Open an administrative command prompt and type **IISRESET**.</span></span>  
  
### <a name="verify-installation"></a><span data-ttu-id="c876c-114">설치 확인</span><span class="sxs-lookup"><span data-stu-id="c876c-114">Verify installation</span></span>  
  
1.  <span data-ttu-id="c876c-115">Windows\Assembly로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="c876c-115">Go to Windows\Assembly.</span></span>  
  
2.  <span data-ttu-id="c876c-116">Microsoft.AnalysisServices.AdomdClient를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c876c-116">Right-click Microsoft.AnalysisServices.AdomdClient and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="c876c-117">**버전**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c876c-117">Click **Version**.</span></span>  
  
4.  <span data-ttu-id="c876c-118">버전에 12.00이 포함 되어 있는지 확인 합니다.\<build number></span><span class="sxs-lookup"><span data-stu-id="c876c-118">Verify that the version includes 12.00.\<build number></span></span> <span data-ttu-id="c876c-119">그리고 설명은 AnalysisService. Microsoft.analysisservices.adomdclient.cellset<입니다.</span><span class="sxs-lookup"><span data-stu-id="c876c-119">and that the description is Microsoft.AnalysisService.AdomdClient.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c876c-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c876c-120">See Also</span></span>  
 [<span data-ttu-id="c876c-121">PowerPivot 관리 대시보드 및 사용량 현황 데이터</span><span class="sxs-lookup"><span data-stu-id="c876c-121">PowerPivot Management Dashboard and Usage Data</span></span>](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data)  
  
  
