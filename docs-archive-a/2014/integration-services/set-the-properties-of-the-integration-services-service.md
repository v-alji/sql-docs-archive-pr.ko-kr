---
title: Integration Services 서비스의 속성 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services service, configuring
- Integration Services service, properties
ms.assetid: 3a8ad546-0f58-4b31-ab56-58d6313b1098
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 055eadd9a1d59c59dd40675b142eae480763f6f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742364"
---
# <a name="set-the-properties-of-the-integration-services-service"></a><span data-ttu-id="79735-102">Integration Services 서비스 속성 설정</span><span class="sxs-lookup"><span data-stu-id="79735-102">Set the Properties of the Integration Services Service</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="79735-103">이 항목에서는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 관리하는 Windows 서비스인 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="79735-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="79735-104">는 이전 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]버전과의 호환성을 위한 서비스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="79735-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="79735-105">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]부터는 Integration Services 서버의 패키지와 같은 개체를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79735-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 <span data-ttu-id="79735-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스는 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]의 패키지를 관리하고 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="79735-106">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service manages and monitors packages in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="79735-107">를 처음 설치 하면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스가 시작 되 고 서비스의 시작 유형이 자동으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79735-107">When you first install [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is started and the startup type of the service is set to automatic.</span></span>  
  
 <span data-ttu-id="79735-108">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스가 설치된 후에는 SQL Server 구성 관리자나 서비스 MMC 스냅인을 사용하여 서비스의 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79735-108">After the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service has been installed, you can set the properties of the service by using either SQL Server Configuration Manager or the Services MMC snap-in.</span></span>  
  
 <span data-ttu-id="79735-109">서비스가 패키지를 저장하고 관리하는 위치 등 서비스의 다른 중요한 기능을 구성하려면 서비스의 구성 파일을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79735-109">To configure other important features of the service, including the locations where it stores and manages packages, you must modify the configuration file of the service.</span></span> <span data-ttu-id="79735-110">자세한 내용은 [Integration Services 서비스 구성&#40;SSIS 서비스&#41;](service/integration-services-service-ssis-service.md)버전과의 호환성을 위한 서비스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="79735-110">For more information, see [Configuring the Integration Services Service &#40;SSIS Service&#41;](service/integration-services-service-ssis-service.md).</span></span>  
  
### <a name="to-set-properties-of-the-integration-services-service-by-using-sql-server-configuration-manager"></a><span data-ttu-id="79735-111">SQL Server 구성 관리자를 사용하여 Integration Services 서비스의 속성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="79735-111">To set properties of the Integration Services service by using SQL Server Configuration Manager</span></span>  
  
1.  <span data-ttu-id="79735-112">**시작** 메뉴에서 **모든 프로그램**, **Microsoft SQL Server**, **구성 도구**를 차례로 가리킨 다음 **SQL Server 구성 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="79735-112">On the **Start** menu, point to **All Programs**, point to **Microsoft SQL Server**, point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="79735-113">**SQL Server 구성 관리자** 스냅인의 서비스 목록에서 **SQL Server Integration Services** 를 찾아 **SQL Server Integration Services**를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="79735-113">In the **SQL Server Configuration Manager** snap-in, locate **SQL Server Integration Services** in the list of services, right-click **SQL Server Integration Services**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="79735-114">**SQL Server Integration Services 속성** 대화 상자에서 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79735-114">In the **SQL Server Integration Services Properties** dialog box you can do the following:</span></span>  
  
    -   <span data-ttu-id="79735-115">**로그온** 탭을 클릭하여 계정 이름과 같은 로그온 정보를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="79735-115">Click the **Log On** tab to view the logon information such as the account name.</span></span>  
  
    -   <span data-ttu-id="79735-116">**서비스** 탭을 클릭하여 호스트 컴퓨터 이름과 같은 서비스에 대한 정보를 확인하고 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스의 시작 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="79735-116">Click the **Service** tab to view information about the service such as the name of the host computer and to specify the start mode of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="79735-117">**고급** 탭에는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스에 대한 정보가 들어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79735-117">The **Advanced** tab contains no information for [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span>  
  
4.  <span data-ttu-id="79735-118">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="79735-118">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="79735-119">**파일** 메뉴에서 **끝내기** 를 클릭하여 **SQL Server 구성 관리자** 스냅인을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="79735-119">On the **File** menu, click **Exit** to close the **SQL Server Configuration Manager** snap-in.</span></span>  
  
### <a name="to-set-properties-of-the-integration-services-service-by-using-services"></a><span data-ttu-id="79735-120">서비스를 사용하여 Integration Services 서비스의 속성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="79735-120">To set properties of the Integration Services service by using Services</span></span>  
  
1.  <span data-ttu-id="79735-121">클래식 보기를 사용할 경우에는 **제어판**에서 **관리 도구**를 클릭하고 종류별 보기를 사용할 경우에는 제어판에서 **성능 및 유지 관리** 를 클릭한 후 **관리 도구**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="79735-121">In **Control Panel**, if you are using Classic View, click **Administrative Tools**, or, if you are using Category View, click **Performance and Maintenance** and then click **Administrative Tools**.</span></span>  
  
2.  <span data-ttu-id="79735-122">**서비스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="79735-122">Click **Services**.</span></span>  
  
3.  <span data-ttu-id="79735-123">**서비스** 스냅인에서 서비스 목록의 **SQL Server Integration Services** 를 찾은 다음 **SQL Server Integration Services**를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="79735-123">In the **Services** snap-in, locate **SQL Server Integration Services** in the list of services, right-click **SQL Server Integration Services**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="79735-124">**SQL Server Integration Services 속성** 대화 상자에서 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79735-124">In the **SQL Server Integration Services Properties** dialog box, you can do the following:</span></span>  
  
    -   <span data-ttu-id="79735-125">**일반** 탭을 클릭 합니다. 서비스를 사용 하도록 설정 하려면 수동 또는 자동 시작 유형을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="79735-125">Click the **General** tab. To enable the service, select either the manual or automatic startup type.</span></span> <span data-ttu-id="79735-126">서비스를 사용하지 않으려면 **시작 유형** 상자에서 사용 안 함을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="79735-126">To disable the service, select Disable in the **Startup type** box.</span></span> <span data-ttu-id="79735-127">사용 안 함을 선택해도 현재 실행 중인 서비스가 중지되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79735-127">Selecting Disable does not stop the service if it is currently running.</span></span>  
  
         <span data-ttu-id="79735-128">서비스를 이미 사용하고 있는 경우 **중지** 를 클릭하여 서비스를 중지하거나 **시작** 을 클릭하여 서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="79735-128">If the service is already enabled, you can click **Stop** to stop the service, or click **Start** to start the service.</span></span>  
  
    -   <span data-ttu-id="79735-129">**로그온** 탭을 클릭하여 로그온 정보를 보거나 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="79735-129">Click the **Log On** tab to view or edit the logon information.</span></span>  
  
    -   <span data-ttu-id="79735-130">**복구** 탭을 클릭하여 서비스 실패 시 기본 컴퓨터의 응답을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="79735-130">Click the **Recovery** tab to view the default computer responses to service failure.</span></span> <span data-ttu-id="79735-131">사용자 환경에 맞게 이러한 옵션을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79735-131">You can modify these options to suit your environment.</span></span>  
  
    -   <span data-ttu-id="79735-132">**종속성** 탭을 클릭하여 종속 서비스 목록을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="79735-132">Click the **Dependencies** tab to view a list of dependent services.</span></span> <span data-ttu-id="79735-133">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스에는 종속성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="79735-133">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service has no dependencies.</span></span>  
  
5.  <span data-ttu-id="79735-134">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="79735-134">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="79735-135">시작 유형이 수동이거나 자동인 경우 필요에 따라 **SQL Server Integration Services** 를 마우스 오른쪽 단추로 클릭하고 **시작, 중지 또는 다시 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="79735-135">Optionally, if the startup type is Manual or Automatic, you can right-click **SQL Server Integration Services** and click **Start, Stop, or Restart**.</span></span>  
  
7.  <span data-ttu-id="79735-136">**파일** 메뉴에서 **끝내기** 를 클릭하여 **서비스** 스냅인을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="79735-136">On the **File** menu, click **Exit** to close the **Services** snap-in.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79735-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="79735-137">See Also</span></span>  
 [<span data-ttu-id="79735-138">Integration Services 서비스 관리</span><span class="sxs-lookup"><span data-stu-id="79735-138">Manage the Integration Services Service</span></span>](../../2014/integration-services/manage-the-integration-services-service.md)  
  
  
