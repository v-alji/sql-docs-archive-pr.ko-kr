---
title: SharePoint용 PowerPivot 2010 설치 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 8d47dde7-c941-4280-a934-e2fe3f9a938f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ba04dfdc69b1c510a800c062586e45f8873c8e8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653712"
---
# <a name="powerpivot-for-sharepoint-2010-installation"></a><span data-ttu-id="164b9-102">SharePoint 2010용 PowerPivot 설치</span><span class="sxs-lookup"><span data-stu-id="164b9-102">PowerPivot for SharePoint 2010 Installation</span></span>
  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]<span data-ttu-id="164b9-103">는 SharePoint에 게시하는 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 통합 문서에 대한 쿼리 처리 및 관리 제어를 제공하는 서버 구성 요소의 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="164b9-103">is a collection of server components that provide query processing and management control over [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] workbooks that you publish to SharePoint.</span></span> <span data-ttu-id="164b9-104">서비스에는 Analysis Services 엔진 및 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 시스템 서비스가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="164b9-104">Services include the Analysis Services engine and [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System Service.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="164b9-105">[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 및 SharePoint Server 2013과 함께 설치에 대한 자세한 내용은 다음을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="164b9-105">For information regarding [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] and installation with SharePoint Server 2013, see the following:</span></span>  
>   
>  -   <span data-ttu-id="164b9-106">[SQL Server 서비스 설치 개요](../../../2014/sql-server/install/overview-of-sql-server-servicing-installation.md)의 "SQL SERVER 2012 SP1" 섹션.</span><span class="sxs-lookup"><span data-stu-id="164b9-106">The "SQL Server 2012 SP1" section of [Overview of SQL Server Servicing Installation](../../../2014/sql-server/install/overview-of-sql-server-servicing-installation.md).</span></span>  
  
 <span data-ttu-id="164b9-107">Analysis Services는 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터가 포함된 Excel 통합 문서에 대한 서버 쪽 처리를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="164b9-107">Analysis Services provides server-side processing for Excel workbooks that contain [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] data.</span></span> [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] <span data-ttu-id="164b9-108">시스템 서비스는 Analysis Services와 함께 작동하며 SharePoint 통합, 부하 분산 및 연결 관리 기능을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="164b9-108">System Service works alongside Analysis Services, adding SharePoint integration, load balancing and connection management.</span></span> [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]<span data-ttu-id="164b9-109">는 대규모 데이터 처리 기능과 Excel에서 제공 하는 데이터 렌더링 서비스를 쌍으로 연결 하 여 Excel 서비스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="164b9-109">extends Excel Services by pairing its large scale data processing capability with the data rendering services that Excel provides.</span></span>  
  
 <span data-ttu-id="164b9-110">[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]를 설치하려면 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]설치 미디어를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="164b9-110">To install [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], use the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]installation media.</span></span>  
  
 <span data-ttu-id="164b9-111">고급 배포 시나리오에 대 한 지침은 [배포 검사 목록: Reporting Services, 파워 뷰 및 SharePoint용 PowerPivot](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md) 및 [배포 검사 목록: SharePoint 2010 팜에 PowerPivot 서버를 추가 하 여 확장](../../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="164b9-111">For instructions on advanced deployment scenarios, see [Deployment Checklist: Reporting Services, Power View, and PowerPivot for SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md) and [Deployment Checklist: Scale-out by adding PowerPivot Servers to a SharePoint 2010 farm](../../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="164b9-112">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="164b9-112">In This Section</span></span>  
 [<span data-ttu-id="164b9-113">SharePoint 2010용 PowerPivot 설치</span><span class="sxs-lookup"><span data-stu-id="164b9-113">Install PowerPivot for SharePoint 2010</span></span>](../../../2014/sql-server/install/install-powerpivot-for-sharepoint-2010.md)  
  
 [<span data-ttu-id="164b9-114">SharePoint 서버에서 Analysis Services OLE DB Provider 설치</span><span class="sxs-lookup"><span data-stu-id="164b9-114">Install the Analysis Services OLE DB Provider on SharePoint Servers</span></span>](../../../2014/sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)  
  
 [<span data-ttu-id="164b9-115">중앙 관리를 실행하는 웹 프런트 엔드 서버에 ADOMD.NET 설치</span><span class="sxs-lookup"><span data-stu-id="164b9-115">Install ADOMD.NET on Web Front-End Servers Running Central Administration</span></span>](../../../2014/sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md)  
  
 [<span data-ttu-id="164b9-116">ADO.NET Data Services를 설치하여 SharePoint 목록의 데이터 피드 내보내기 지원</span><span class="sxs-lookup"><span data-stu-id="164b9-116">Install ADO.NET Data Services to support data feed exports of SharePoint lists</span></span>](../../../2014/sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md)  
  
 [<span data-ttu-id="164b9-117">명령 프롬프트에서 PowerPivot 설치</span><span class="sxs-lookup"><span data-stu-id="164b9-117">Install PowerPivot from the Command Prompt</span></span>](../../../2014/sql-server/install/install-powerpivot-from-the-command-prompt.md)  
  
 [<span data-ttu-id="164b9-118">SharePoint용 PowerPivot 제거</span><span class="sxs-lookup"><span data-stu-id="164b9-118">Uninstall PowerPivot for SharePoint</span></span>](../../../2014/sql-server/install/uninstall-power-pivot-for-sharepoint.md)  
  
 [<span data-ttu-id="164b9-119">PowerPivot for SharePoint 복구</span><span class="sxs-lookup"><span data-stu-id="164b9-119">Repair PowerPivot for SharePoint</span></span>](../../../2014/sql-server/install/repair-powerpivot-for-sharepoint.md)  
  
 [<span data-ttu-id="164b9-120">초기 구성 &#40;SharePoint용 PowerPivot&#41;</span><span class="sxs-lookup"><span data-stu-id="164b9-120">Initial Configuration &#40;PowerPivot for SharePoint&#41;</span></span>](../../../2014/sql-server/install/initial-configuration-powerpivot-for-sharepoint.md)  
  
## <a name="see-also"></a><span data-ttu-id="164b9-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="164b9-121">See Also</span></span>  
 [<span data-ttu-id="164b9-122">중앙 관리에서 PowerPivot 서버 관리 및 구성</span><span class="sxs-lookup"><span data-stu-id="164b9-122">PowerPivot Server Administration and Configuration in Central Administration</span></span>](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration)  
  
  
