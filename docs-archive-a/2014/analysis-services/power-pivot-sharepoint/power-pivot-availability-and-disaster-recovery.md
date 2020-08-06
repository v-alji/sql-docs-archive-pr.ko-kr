---
title: PowerPivot 가용성 및 재해 복구 (SQL Server 2014) | Microsoft Docs
ms.custom: ''
ms.date: 03/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4aaf008c-3bcb-4dbf-862c-65747d1a668c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 51a48470887f83515ddee8d01c1bb209dfa94008
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728859"
---
# <a name="powerpivot-availability-and-disaster-recovery-sql-server-2014"></a><span data-ttu-id="3979a-102">PowerPivot Availability and Disaster Recovery (SQL Server 2014)</span><span class="sxs-lookup"><span data-stu-id="3979a-102">PowerPivot Availability and Disaster Recovery (SQL Server 2014)</span></span>
  <span data-ttu-id="3979a-103">[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 에 대한 가용성 및 재해 복구 계획은 주로 SharePoint 팜 디자인, 다른 구성 요소에 허용되는 작동 중단 시간 및 SharePoint 가용성에 구현하는 도구 및 최선의 방법에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-103">Availability and disaster recovery plans for [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] depend primarily on the design of your SharePoint farm, the amount of downtime acceptable for different components, and the tools and best practices you implement for SharePoint availability.</span></span> <span data-ttu-id="3979a-104">이 항목에서는 기술을 요약 하 고 배포에 대 한 가용성 및 재해 복구를 계획할 때 고려할 예제 토폴로지 다이어그램을 포함 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-104">This topic summarizes technologies and includes example topology diagrams to consider when planning availability and disaster recovery for a [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] deployment.</span></span>

||
|-|
|<span data-ttu-id="3979a-105">**[!INCLUDE[applies](../../includes/applies-md.md)]** Sharepoint 2013 &#124; SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="3979a-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010</span></span>|

 <span data-ttu-id="3979a-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="3979a-106">**In this topic:**</span></span>

-   [<span data-ttu-id="3979a-107">PowerPivot 고가용성에 대한 SharePoint 2013 토폴로지 예제</span><span class="sxs-lookup"><span data-stu-id="3979a-107">Example SharePoint 2013 topology for PowerPivot high availability</span></span>](#bkmk_sharepoint2013)

-   [<span data-ttu-id="3979a-108">PowerPivot 고가용성에 대한 SharePoint 2010 토폴로지 예제</span><span class="sxs-lookup"><span data-stu-id="3979a-108">Example SharePoint 2010 topology for PowerPivot high availability</span></span>](#bkmk_sharepoint2010)

-   [<span data-ttu-id="3979a-109">PowerPivot 서비스 애플리케이션 데이터베이스 및 SQL Server 가용성 및 복구 기술</span><span class="sxs-lookup"><span data-stu-id="3979a-109">PowerPivot service application database and SQL Server availability and recovery technologies</span></span>](#bkmk_sql_server_technologies)

-   [<span data-ttu-id="3979a-110">추가 정보 링크</span><span class="sxs-lookup"><span data-stu-id="3979a-110">Links to more information</span></span>](#bkmk_more_resources)

##  <a name="example-sharepoint-2013-topology-for-powerpivot-high-availability"></a><a name="bkmk_sharepoint2013"></a><span data-ttu-id="3979a-111">PowerPivot 고가용성에 대 한 SharePoint 2013 토폴로지 예</span><span class="sxs-lookup"><span data-stu-id="3979a-111">Example SharePoint 2013 topology for PowerPivot high availability</span></span>
 <span data-ttu-id="3979a-112">[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 배포에서 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 가용성을 디자인하는 방법에 더 많은 유연성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-112">In a [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 deployment there is more flexibility in how you design [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] availability.</span></span> <span data-ttu-id="3979a-113">SharePoint 2013에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 서버라고도 하는 SharePoint 모드로 배포된 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 인스턴스는 SharePoint 팜 외부에서 실행되고 별도의 서버에 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-113">In SharePoint 2013, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance deployed in SharePoint mode, also referred to as the [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] server, runs outside the SharePoint farm and can be installed on separate servers.</span></span> <span data-ttu-id="3979a-114">SharePoint 모드의 각 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스는 Excel Services에 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-114">Each instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in SharePoint mode is registered with Excel Services.</span></span> <span data-ttu-id="3979a-115">[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 공유 서비스 및 서비스 애플리케이션은 SharePoint 애플리케이션 서버에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-115">The [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] shared service and service application run on SharePoint application servers.</span></span>

 <span data-ttu-id="3979a-116">다음 다이어그램에서는 예제 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 배포를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-116">The following diagram illustrates an example [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 deployment.</span></span> <span data-ttu-id="3979a-117">이 예제는 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 서비스의 적합한 가용성을 지원하고 데이터베이스가 정기적으로 백업된다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-117">This example supports good availability of the [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] services and assumes the databases are backed up on a regular basis.</span></span>

 <span data-ttu-id="3979a-118">![2013에서 PowerPivot 가용성](../media/ssas-powerpivot-services-2013.png "2013에서 PowerPivot 가용성")</span><span class="sxs-lookup"><span data-stu-id="3979a-118">![powerpivot availability in 2013](../media/ssas-powerpivot-services-2013.png "powerpivot availability in 2013")</span></span>

-   <span data-ttu-id="3979a-119">**(1)** 웹 프런트 엔드 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-119">**(1)** The Web front-end servers.</span></span> <span data-ttu-id="3979a-120">[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 추가 기능을 사용하여 각 서버에 데이터 공급자를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-120">Use the [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 Add-in to install the data providers on each server.</span></span> <span data-ttu-id="3979a-121">자세한 내용은 [SharePoint 2013&#41;&#40;SharePoint용 PowerPivot 추가 기능 설치 또는 제거 ](../instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3979a-121">For more information, see [Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;](../instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md).</span></span>

-   <span data-ttu-id="3979a-122">**(2)**[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 공유 서비스는 **각** 애플리케이션 서버에서 실행되고 서비스 애플리케이션을 애플리케이션 서버 **간에** 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-122">**(2)** The [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] shared service runs **on each** application server and allows the service application to run **across** application servers.</span></span> <span data-ttu-id="3979a-123">따라서 단일 애플리케이션 서버가 오프라인이 되는 경우 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 애플리케이션을 여전히 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-123">Therefore if a single application server goes offline, the [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] application will still be available.</span></span>

-   <span data-ttu-id="3979a-124">**(3)** Excel 계산 서비스는 애플리케이션 서버를 각각 하나씩 실행하고 서비스 애플리케이션을 애플리케이션 서버 간에 실행할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-124">**(3)** Excel Calculation Services runs one each application server and allows the service application to run across application servers.</span></span> <span data-ttu-id="3979a-125">따라서 단일 애플리케이션 서버가 오프라인이 되는 경우 Excel 계산 서비스를 여전히 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-125">Therefore if a single application server goes offline, Excel Calculation Services will still be available.</span></span>

-   <span data-ttu-id="3979a-126">**(4)** 및 **(6)** sharepoint 모드의 인스턴스는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sharepoint 팜 외부의 서버에서 실행 됩니다. 여기에는 Windows 서비스 **SQL Server Analysis Services (POWERPIVOT)** 이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-126">**(4)** and **(6)** Instances of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ins SharePoint mode run on servers outside the SharePoint farm, this includes the Windows Service **SQL Server Analysis Services (POWERPIVOT)**.</span></span> <span data-ttu-id="3979a-127">이러한 각각의 인스턴스는 Excel Services **(3)** 에 등록되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-127">Each of these instances is registered with Excel Services **(3)**.</span></span> <span data-ttu-id="3979a-128">Excel Services는 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 서버 요청의 부하 분산을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-128">Excel Services manages load balancing of requests to the [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] servers.</span></span> <span data-ttu-id="3979a-129">[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 아키텍처를 사용하면 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 에 대한 여러 서버를 가질 수 있으므로 필요한 만큼 더 많은 인스턴스를 쉽게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-129">The [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 architecture enables you to have multiple servers for [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] so you can easily add more instances as needed.</span></span> <span data-ttu-id="3979a-130">자세한 내용은 [Excel Services 데이터 모델 설정 관리(SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780\(v=office.15\).aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3979a-130">For more information, see [Manage Excel Services data model settings (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780\(v=office.15\).aspx).</span></span>

-   <span data-ttu-id="3979a-131">**(5)** 콘텐츠, 구성 및 애플리케이션 데이터베이스에 사용되는 SQL Server 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-131">**(5)** The SQL Server databases used for content, configuration, and application databases.</span></span> <span data-ttu-id="3979a-132">여기에는 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 애플리케이션 데이터베이스가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-132">This includes the [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] service application database.</span></span> <span data-ttu-id="3979a-133">DR 계획에는 데이터베이스 계층이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-133">Your DR plan should include the database layer.</span></span> <span data-ttu-id="3979a-134">이 디자인에서 데이터베이스는 **(4)**[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 인스턴스 중 하나와 동일한 서버에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-134">In this design the databases run on the same server as **(4)** one of the [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] instances.</span></span> <span data-ttu-id="3979a-135">**(4)** 및 **(5)** 는 다른 서버에 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-135">**(4)** and **(5)** could also be on different servers.</span></span>

-   <span data-ttu-id="3979a-136">**(7)** SQL Server 데이터베이스 백업 또는 중복성의 일부 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-136">**(7)** Some form of SQL Server database backup or redundancy.</span></span>

##  <a name="example-sharepoint-2010-topology-for-powerpivot-high-availability"></a><a name="bkmk_sharepoint2010"></a><span data-ttu-id="3979a-137">PowerPivot 고가용성에 대 한 SharePoint 2010 토폴로지 예</span><span class="sxs-lookup"><span data-stu-id="3979a-137">Example SharePoint 2010 topology for PowerPivot high availability</span></span>
 <span data-ttu-id="3979a-138">[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010 아키텍처에서 모든 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 구성 요소가 같은 SharePoint 애플리케이션 서버에서 실행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-138">The [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010 architecture requires all [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] components run on the same SharePoint application servers.</span></span> <span data-ttu-id="3979a-139">여기에는 SharePoint 모드에서 배포된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스와 SharePoint 2013 배포 중 하나와만 비교되는 공유 서비스 2개가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-139">This includes the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance deployed in SharePoint mode and two shared services compared to only one in a SharePoint 2013 deployment.</span></span>

 <span data-ttu-id="3979a-140">다음 다이어그램에서는 예제 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010 배포를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-140">The following diagram illustrates an example [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010 deployment.</span></span> <span data-ttu-id="3979a-141">이 예제는 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 서비스의 적합한 가용성을 지원하고 데이터베이스가 정기적으로 백업된다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-141">This example supports good availability of the [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] services and assumes the databases are backed up on a regular basis.</span></span>

 <span data-ttu-id="3979a-142">![SharePoint 2010에서 PowerPivot 가용성](../media/ssas-powerpivot-services-2010.png "SharePoint 2010에서 PowerPivot 가용성")</span><span class="sxs-lookup"><span data-stu-id="3979a-142">![powerpivot availability in sharepoint 2010](../media/ssas-powerpivot-services-2010.png "powerpivot availability in sharepoint 2010")</span></span>

-   <span data-ttu-id="3979a-143">**(1)** 웹 프런트 엔드 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-143">**(1)** The Web front-end servers.</span></span> <span data-ttu-id="3979a-144">각 서버에서 데이터 공급자를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-144">Install the data providers on each server.</span></span> <span data-ttu-id="3979a-145">자세한 내용은 [SharePoint 서버에서 Analysis Services OLE DB 공급자 설치](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3979a-145">For more information, see [Install the Analysis Services OLE DB Provider on SharePoint Servers](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).</span></span>

-   <span data-ttu-id="3979a-146">**(2)** 두 개의 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 공유 서비스 및 **(4)** Windows 서비스 **SQL Server Analysis Services (POWERPIVOT)** 이 SharePoint 응용 프로그램 서버에 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-146">**(2)** The two [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] shared services and **(4)** the Windows Service **SQL Server Analysis Services (POWERPIVOT)** are installed on the SharePoint application servers.</span></span>

     <span data-ttu-id="3979a-147">[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 시스템 서비스는 **각** 애플리케이션 서버에서 실행되고 서비스 애플리케이션을 애플리케이션 서버 **간에** 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-147">The [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System Service runs **on each** application server and allows the service application to run **across** application servers.</span></span> <span data-ttu-id="3979a-148">단일 애플리케이션 서버가 오프라인이 되는 경우 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 서비스 애플리케이션을 여전히 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-148">If a single application server goes offline, the [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] service application will still be available.</span></span>

     <span data-ttu-id="3979a-149">SharePoint 2010에서 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 용량을 늘리려면 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 시스템 서비스를 실행하는 SharePoint 애플리케이션 서버를 추가로 배포하세요.</span><span class="sxs-lookup"><span data-stu-id="3979a-149">To increase [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] capacity in a SharePoint 2010, deploy more SharePoint application servers running the [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System Service.</span></span>

-   <span data-ttu-id="3979a-150">**(3)** Excel 계산 서비스는 각각의 애플리케이션 서버에서 실행되고 서비스 애플리케이션을 애플리케이션 서버 간에 실행할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-150">**(3)** Excel Calculation Services runs on each application server and allows the service application to run across application servers.</span></span> <span data-ttu-id="3979a-151">따라서 단일 애플리케이션 서버가 오프라인이 되는 경우 Excel 계산 서비스를 여전히 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-151">Therefore if a single application server goes offline, Excel Calculation Services will still be available.</span></span>

-   <span data-ttu-id="3979a-152">**(5)** 콘텐츠, 구성 및 애플리케이션 데이터베이스에 사용되는 SQL Server 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-152">**(5)** The SQL Server databases used for content, configuration, and application databases.</span></span> <span data-ttu-id="3979a-153">여기에는 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 애플리케이션 데이터베이스가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-153">This includes the [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] service application database.</span></span> <span data-ttu-id="3979a-154">DR 계획에는 데이터베이스 계층이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-154">Your DR plan should include the database layer.</span></span>

-   <span data-ttu-id="3979a-155">**(6)** SQL Server 데이터베이스 백업 또는 중복성의 일부 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-155">**(6)** Some form of SQL Server database backup or redundancy.</span></span>

##  <a name="powerpivot-service-application-database-and-sql-server-availability-and-recovery-technologies"></a><a name="bkmk_sql_server_technologies"></a><span data-ttu-id="3979a-156">PowerPivot 서비스 응용 프로그램 데이터베이스 및 SQL Server 가용성 및 복구 기술</span><span class="sxs-lookup"><span data-stu-id="3979a-156">PowerPivot service application database and SQL Server availability and recovery technologies</span></span>
 <span data-ttu-id="3979a-157">SharePoint 고가용성 계획에 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 서비스 애플리케이션 데이터베이스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-157">Include the [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] service application database in you SharePoint high availability planning.</span></span> <span data-ttu-id="3979a-158">이 데이터베이스 기본 이름은 `DefaultPowerPivotServiceApplicationDB-<GUID>`입니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-158">The default name of the database is `DefaultPowerPivotServiceApplicationDB-<GUID>`.</span></span> <span data-ttu-id="3979a-159">다음은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가용성 기술과, [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 데이터베이스에 사용할 때의 권장 사항에 대한 요약입니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-159">The following is a summary of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] availability technologies and recommendations when used with the [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] database.</span></span> <span data-ttu-id="3979a-160">자세한 내용은 [SharePoint 데이터베이스에 지원되는 고가용성 및 재해 복구 옵션(SharePoint 2013)](https://technet.microsoft.com/library/jj841106.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3979a-160">For more information, see [Supported high availability and disaster recovery options for SharePoint databases (SharePoint 2013)](https://technet.microsoft.com/library/jj841106.aspx).</span></span>

||<span data-ttu-id="3979a-161">주석</span><span class="sxs-lookup"><span data-stu-id="3979a-161">Comments</span></span>|
|-|--------------|
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] <span data-ttu-id="3979a-162">(4) [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 동기화 미러링.</span><span class="sxs-lookup"><span data-stu-id="3979a-162">and [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] synchronous mirroring in a farm for availability.</span></span>|<span data-ttu-id="3979a-163">지원되나 이 옵션은 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-163">Supported but not recommended.</span></span> <span data-ttu-id="3979a-164">동기-커밋 모드에서 AlwaysOn을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-164">The recommendation is to use AlwaysOn in Synchronous - commit mode.</span></span>|
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="3979a-165">[!INCLUDE[ssHADR](../../includes/sshadr-md.md)]동기-커밋 모드에서</span><span class="sxs-lookup"><span data-stu-id="3979a-165">[!INCLUDE[ssHADR](../../includes/sshadr-md.md)] in Synchronous-Commit mode</span></span>|<span data-ttu-id="3979a-166">지원 및 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="3979a-166">Supported and recommended.</span></span>|
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] <span data-ttu-id="3979a-167">비동기 미러링 또는 재해 복구를 위해 다른 팜으로 로그 전달.</span><span class="sxs-lookup"><span data-stu-id="3979a-167">asynchronous mirroring or log-shipping to another farm for disaster recovery.</span></span>|<span data-ttu-id="3979a-168">지원됨.</span><span class="sxs-lookup"><span data-stu-id="3979a-168">Supported.</span></span>|
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="3979a-169">[!INCLUDE[ssHADR](../../includes/sshadr-md.md)]재해 복구를 위한 비동기 커밋 사용</span><span class="sxs-lookup"><span data-stu-id="3979a-169">[!INCLUDE[ssHADR](../../includes/sshadr-md.md)] with asynchronous-commit for disaster recovery</span></span>|<span data-ttu-id="3979a-170">지원됨</span><span class="sxs-lookup"><span data-stu-id="3979a-170">Supported</span></span>|

-   [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]

-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3979a-171">로그 전달</span><span class="sxs-lookup"><span data-stu-id="3979a-171">Log Shipping</span></span>

 <span data-ttu-id="3979a-172">[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]을 사용하여 코드 대기 시나리오를 계획하는 방법에 대한 자세한 내용은 [PowerPivot 재해 복구](https://social.technet.microsoft.com/wiki/contents/articles/22137.sharepoint-powerpivot-disaster-recovery.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3979a-172">For more information on how to plan a cold standby scenario with [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], see [PowerPivot Disaster Recovery](https://social.technet.microsoft.com/wiki/contents/articles/22137.sharepoint-powerpivot-disaster-recovery.aspx).</span></span>

## <a name="verification"></a><span data-ttu-id="3979a-173">확인</span><span class="sxs-lookup"><span data-stu-id="3979a-173">Verification</span></span>
 <span data-ttu-id="3979a-174">재해 복구 주기 전후에 배포를 확인 하는 데 도움이 되는 지침과 스크립트는 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] [검사 목록: PowerShell을 사용 하 여 SharePoint용 PowerPivot 확인](../instances/install-windows/checklist-use-powershell-to-verify-power-pivot-for-sharepoint.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3979a-174">For guidance and scripts to help you verify a [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] deployment before and after a disaster recovery cycle, see [CheckList: Use PowerShell to Verify PowerPivot for SharePoint](../instances/install-windows/checklist-use-powershell-to-verify-power-pivot-for-sharepoint.md).</span></span>

##  <a name="links-to-more-information"></a><a name="bkmk_more_resources"></a><span data-ttu-id="3979a-175">추가 정보에 대 한 링크</span><span class="sxs-lookup"><span data-stu-id="3979a-175">Links to more information</span></span>

-   [<span data-ttu-id="3979a-176">SharePoint 데이터베이스에 지원되는 고가용성 및 재해 복구 옵션(SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="3979a-176">Supported high availability and disaster recovery options for SharePoint databases (SharePoint 2013)</span></span>](https://technet.microsoft.com/library/jj841106.aspx)

-   <span data-ttu-id="3979a-177">[재해 복구 계획(SharePoint Server 2010)](https://technet.microsoft.com/library/ff628971\(v=office.14\).aspx)</span><span class="sxs-lookup"><span data-stu-id="3979a-177">[Plan for disaster recovery (SharePoint Server 2010)](https://technet.microsoft.com/library/ff628971\(v=office.14\).aspx)</span></span>



