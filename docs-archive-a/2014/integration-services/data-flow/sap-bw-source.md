---
title: SAP BW 원본 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 749afb64-3567-4dc9-8431-783d650c25db
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d64af5e0d881e3b7dbbd2cc4e005aa3dbef3c43a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659584"
---
# <a name="sap-bw-source"></a><span data-ttu-id="bd352-102">SAP BW 원본</span><span class="sxs-lookup"><span data-stu-id="bd352-102">SAP BW Source</span></span>
  <span data-ttu-id="bd352-103">SAP BW 원본은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW의 원본 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-103">The SAP BW source is the source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span> <span data-ttu-id="bd352-104">따라서 SAP BW 원본은 SAP Netweaver BW 버전 7 시스템에서 데이터를 추출하고 이 데이터를 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지의 데이터 흐름에서 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-104">Thus, the SAP BW source extracts data from an SAP Netweaver BW version 7 system and makes this data available to the data flow in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span>  
  
 <span data-ttu-id="bd352-105">이 원본에는 출력 한 개와 오류 출력 한 개가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-105">This source has one output and one error output.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bd352-106">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="bd352-107">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bd352-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bd352-108">SAP Netweaver BW에서 데이터를 추출하려면 추가 SAP 라이선스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-108">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="bd352-109">SAP에서 이러한 요구 사항을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="bd352-109">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="bd352-110">SAP BW 원본을 사용하려면 다음 태스크를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-110">To use the SAP BW source, you have to do the following tasks:</span></span>  
  
-   [<span data-ttu-id="bd352-111">SAP Netweaver BW 개체 준비</span><span class="sxs-lookup"><span data-stu-id="bd352-111">Prepare the SAP Netweaver BW objects</span></span>](#bkmk_Prepare_Objects)  
  
-   [<span data-ttu-id="bd352-112">SAP Netweaver BW 시스템에 연결</span><span class="sxs-lookup"><span data-stu-id="bd352-112">Connect to the SAP Netweaver BW system</span></span>](#bkmk_Connect_Database)  
  
-   [<span data-ttu-id="bd352-113">SAP BW 원본 구성</span><span class="sxs-lookup"><span data-stu-id="bd352-113">Configure the SAP BW source</span></span>](#bkmk_Configure_Source)  
  
##  <a name="preparing-the-sap-netweaver-bw-objects-that-the-source-requires"></a><a name="bkmk_Prepare_Objects"></a> <span data-ttu-id="bd352-114">원본에 필요한 SAP Netweaver BW 개체 준비</span><span class="sxs-lookup"><span data-stu-id="bd352-114">Preparing the SAP Netweaver BW Objects That the Source Requires</span></span>  
 <span data-ttu-id="bd352-115">SAP BW 원본이 작동하려면 특정 개체가 SAP Netweaver BW 시스템에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-115">The SAP BW source requires that certain objects are in the SAP Netweaver BW system before the source can function.</span></span> <span data-ttu-id="bd352-116">이러한 개체가 없는 경우 다음 단계를 수행하여 SAP Netweaver BW 시스템에서 이러한 개체를 만들고 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-116">If these objects do not already exist, you have to follow these steps to create and configure these objects in the SAP Netweaver BW system.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bd352-117">이러한 개체와 구성 단계에 대한 자세한 내용은 SAP Netweaver BW 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bd352-117">For additional details about these objects and these configuration steps, see the SAP Netweaver BW documentation.</span></span>  
  
1.  <span data-ttu-id="bd352-118">SAP GUI를 통해 SAP Netweaver BW에 로그온하고 트랜잭션 코드 SM59를 입력한 다음 RFC 대상을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-118">Log on to SAP Netweaver BW through the SAP GUI, enter transaction code SM59, and create an RFC destination:</span></span>  
  
    1.  <span data-ttu-id="bd352-119">**Connection Type**에서 **TCP/IP**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-119">For **Connection Type**, select **TCP/IP**.</span></span>  
  
    2.  <span data-ttu-id="bd352-120">**Activation Type**에서 **Registered Server Program**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-120">For **Activation Type**, select **Registered Server Program**.</span></span>  
  
    3.  <span data-ttu-id="bd352-121">**Communication Type with Target System**(대상 시스템과 통신 유형)에서 **Non-Unicode (Inactive MDMP Settings)** (비유니코드(비활성 MDMP 설정))를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-121">For **Communication Type with Target System**, select **Non-Unicode (Inactive MDMP Settings)**.</span></span>  
  
    4.  <span data-ttu-id="bd352-122">적절한 프로그램 ID를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-122">Assign an appropriate Program ID.</span></span>  
  
2.  <span data-ttu-id="bd352-123">오픈 허브 대상을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-123">Create an Open Hub Destination:</span></span>  
  
    1.  <span data-ttu-id="bd352-124">Administrator Workbench(트랜잭션 코드 RSA1)로 이동하고 왼쪽 창에서 **Open Hub Destination**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-124">Go to the Administrator Workbench (transaction code RSA1) and, in the left pane, select **Open Hub Destination**.</span></span>  
  
    2.  <span data-ttu-id="bd352-125">가운데 창에서 InfoArea를 마우스 오른쪽 단추로 클릭한 다음 **"Create Open Hub Destination"** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-125">In the middle pane, right-click an InfoArea, and then select **"Create Open Hub Destination"**.</span></span>  
  
    3.  <span data-ttu-id="bd352-126">**Destination Type**에서 **"Third Party Tool"** 을 선택한 다음 이전에 만든 RFC 대상을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-126">For **Destination Type**, select **"Third Party Tool"**, and then enter the previously created RFC Destination.</span></span>  
  
    4.  <span data-ttu-id="bd352-127">새 오픈 허브 대상을 저장하고 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-127">Save and activate the new Open Hub Destination.</span></span>  
  
3.  <span data-ttu-id="bd352-128">DTP(데이터 전송 프로세스)를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-128">Create a Data Transfer Process (DTP):</span></span>  
  
    1.  <span data-ttu-id="bd352-129">InfoArea의 가운데 창에서 이전에 만든 대상을 마우스 오른쪽 단추로 클릭한 다음 **"Create data transfer process"** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-129">In the middle pane of the InfoArea, right-click the previously created destination, and then select **"Create data transfer process"**.</span></span>  
  
    2.  <span data-ttu-id="bd352-130">DTP를 구성하고 저장하고 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-130">Configure, save, and activate the DTP.</span></span>  
  
    3.  <span data-ttu-id="bd352-131">메뉴에서 **Goto**를 클릭한 다음 **Settings for Batch Manager**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-131">On the menu, click **Goto**, and then click **Settings for Batch Manager**.</span></span>  
  
    4.  <span data-ttu-id="bd352-132">순차 처리의 경우 **Number of processes** 를 1로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-132">Update **Number of processes** to 1 for serial processing.</span></span>  
  
4.  <span data-ttu-id="bd352-133">프로세스 체인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-133">Create a process chain:</span></span>  
  
    1.  <span data-ttu-id="bd352-134">프로세스 체인을 구성할 때 **Start Using Metadata Chain or API** 를 **Start Process** 의 **Scheduling Options**로 선택한 다음 이전에 만든 DTP를 후속 노드로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-134">When configuring the process chain, select the **Start Using Metadata Chain or API** as the **Scheduling Options** of the **Start Process**, and then add the previously created DTP as the subsequent node.</span></span>  
  
    2.  <span data-ttu-id="bd352-135">프로세스 체인을 저장하고 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-135">Save and activate the process chain.</span></span>  
  
     <span data-ttu-id="bd352-136">SAP BW 원본은 프로세스 체인을 호출하여 데이터 전송 프로세스를 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-136">The SAP BW source can call the process chain to activate the data transfer process.</span></span>  
  
##  <a name="connecting-to-the-sap-netweaver-bw-system"></a><a name="bkmk_Connect_Database"></a> <span data-ttu-id="bd352-137">SAP Netweaver BW 시스템에 연결</span><span class="sxs-lookup"><span data-stu-id="bd352-137">Connecting to the SAP Netweaver BW System</span></span>  
 <span data-ttu-id="bd352-138">SAP Netweaver BW 버전 7 시스템에 연결하기 위해 SAP BW 원본은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 패키지의 일부인 SAP BW 연결 관리자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-138">To connect to the SAP Netweaver BW version 7 system, the SAP BW source uses the SAP BW connection manager that is part of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW package.</span></span> <span data-ttu-id="bd352-139">SAP BW 연결 관리자는 SAP BW 원본이 사용할 수 있는 유일한 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 연결 관리자입니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-139">The SAP BW connection manager is the only [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] connection manager that the SAP BW source can use.</span></span>  
  
 <span data-ttu-id="bd352-140">SAP BW 연결 관리자에 대한 자세한 내용은 [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bd352-140">For more information about the SAP BW connection manager, see [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md).</span></span>  
  
##  <a name="configuring-the-sap-bw-source"></a><a name="bkmk_Configure_Source"></a> <span data-ttu-id="bd352-141">SAP BW 원본 구성</span><span class="sxs-lookup"><span data-stu-id="bd352-141">Configuring the SAP BW Source</span></span>  
 <span data-ttu-id="bd352-142">다음과 같은 방법으로 SAP BW 원본을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-142">You can configure the SAP BW source in the following ways:</span></span>  
  
-   <span data-ttu-id="bd352-143">데이터를 추출하는 데 사용할 OHS(Open Hub Service) 대상을 조회하고 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-143">Look up and select the Open Hub Service (OHS) destination to use to extract data.</span></span>  
  
-   <span data-ttu-id="bd352-144">데이터를 추출하는 방법으로 다음 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-144">Select one of the following methods for extracting data:</span></span>  
  
    -   <span data-ttu-id="bd352-145">프로세스 체인을 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-145">Trigger a process chain.</span></span> <span data-ttu-id="bd352-146">이 경우 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지는 추출 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-146">In this case, the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package starts the extraction process.</span></span>  
  
    -   <span data-ttu-id="bd352-147">SAP Netweaver BW 시스템에서 추출 시작 알림을 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-147">Wait for notification from the SAP Netweaver BW system to begin an extraction.</span></span> <span data-ttu-id="bd352-148">이 경우 SAP Netweaver BW 시스템은 추출 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-148">In this case, the SAP Netweaver BW system starts the extraction process.</span></span>  
  
    -   <span data-ttu-id="bd352-149">특정 요청 ID와 연결된 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-149">Retrieve the data that is associated with a particular Request ID.</span></span> <span data-ttu-id="bd352-150">이 경우 SAP Netweaver BW 시스템에서 데이터를 내부 테이블에 이미 추출했으므로 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지는 데이터를 읽기만 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-150">In this case, the SAP Netweaver BW system has already extracted the data to an internal table, and the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package just reads the data.</span></span>  
  
-   <span data-ttu-id="bd352-151">선택한 데이터 추출 방법에 따라 다음 추가 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-151">Depending on the method selected for extracting data, provide the following additional information:</span></span>  
  
    -   <span data-ttu-id="bd352-152">**P - 프로세스 체인 트리거** 옵션의 경우 게이트웨이 호스트 이름, 게이트웨이 서비스 이름, RFC 대상의 프로그램 ID 및 프로세스 체인의 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-152">For the **P - Trigger Process Chain** option, provide the gateway host name, gateway service name, program ID for the RFC destination, and name of the process chain.</span></span>  
  
    -   <span data-ttu-id="bd352-153">**W - 알릴 때까지 대기** 옵션의 경우 게이트웨이 호스트 이름, 게이트웨이 서버 이름 및 RFC 대상의 프로그램 ID를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-153">For the **W - Wait for Notify** option, provide the gateway host name, the gateway server name, and the program ID for the RFC destination.</span></span> <span data-ttu-id="bd352-154">제한 시간(초)도 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-154">You can also specify the timeout (in seconds).</span></span> <span data-ttu-id="bd352-155">제한 시간은 원본이 알림을 받을 때까지 대기할 최대 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-155">The timeout is the maximum period of time that the source will wait to be notified.</span></span>  
  
    -   <span data-ttu-id="bd352-156">**E - 추출만** 옵션의 경우 요청 ID를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-156">For the **E - Extract Only** option, provide the Request ID.</span></span>  
  
-   <span data-ttu-id="bd352-157">문자열 변환의 규칙을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-157">Specify rules for string conversion.</span></span> <span data-ttu-id="bd352-158">예를 들어 SAP Netweaver BW 시스템이 유니코드인지 여부에 따라 모든 문자열을 변환하거나 모든 문자열을 `varchar` 또는 `nvarchar`로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-158">(For example, convert all strings depending on whether the SAP Netweaver BW system is Unicode or not, or convert all strings to `varchar` or `nvarchar`).</span></span>  
  
-   <span data-ttu-id="bd352-159">선택한 옵션을 사용하여 추출할 데이터를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-159">Use the options that you have selected to preview the data to be extracted.</span></span>  
  
 <span data-ttu-id="bd352-160">원본에 의한 RFC 함수 호출의 로깅을 사용하도록 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-160">You can also enable logging of RFC function calls by the source.</span></span> <span data-ttu-id="bd352-161">이 로깅은 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지에서 사용하도록 설정할 수 있는 선택적 로깅과 별개입니다. 원본이 사용할 SAP BW 연결 관리자를 구성할 때 RFC 함수 호출의 로깅을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-161">(This logging is separate from the optional logging that you can enable on [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.) You enable logging of RFC function calls when you configure the SAP BW connection manager that the source will use.</span></span> <span data-ttu-id="bd352-162">SAP BW 연결 관리자를 구성하는 방법은 [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bd352-162">For more information about how to configure the SAP BW connection manager, see [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md).</span></span>  
  
 <span data-ttu-id="bd352-163">원본을 구성하는 데 필요한 값 중 모르는 것이 있으면 SAP 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="bd352-163">If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="bd352-164">SAP BW 연결 관리자, 원본 및 대상을 구성하고 사용하는 방법을 제시하는 연습은 [SAP BI 7.0에서 SQL Server 2008 Integration Services 사용](https://go.microsoft.com/fwlink/?LinkID=137090)백서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bd352-164">For a walkthrough that demonstrates how to configure and use the SAP BW connection manager, source, and destination, see the white paper, [Using SQL Server 2008 Integration Services with SAP BI 7.0](https://go.microsoft.com/fwlink/?LinkID=137090).</span></span> <span data-ttu-id="bd352-165">또한 이 백서는 SAP BW에 필요한 개체를 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-165">This white paper also shows how to configure the required objects in SAP BW.</span></span>  
  
### <a name="using-the-ssis-designer-to-configure-the-source"></a><span data-ttu-id="bd352-166">SSIS 디자이너를 사용하여 원본 구성</span><span class="sxs-lookup"><span data-stu-id="bd352-166">Using the SSIS Designer to Configure the Source</span></span>  
 <span data-ttu-id="bd352-167">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 SAP BW 원본의 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="bd352-167">For more information about the properties of the SAP BW source that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="bd352-168">SAP BW 원본 편집기&#40;연결 관리자 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="bd352-168">SAP BW Source Editor &#40;Connection Manager Page&#41;</span></span>](sap-bw-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="bd352-169">SAP BW 원본 편집기&#40;열 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="bd352-169">SAP BW Source Editor &#40;Columns Page&#41;</span></span>](sap-bw-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="bd352-170">SAP BW 원본 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="bd352-170">SAP BW Source Editor &#40;Error Output Page&#41;</span></span>](sap-bw-source-editor-error-output-page.md)  
  
-   [<span data-ttu-id="bd352-171">SAP BW 원본 편집기&#40;고급 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="bd352-171">SAP BW Source Editor &#40;Advanced Page&#41;</span></span>](sap-bw-source-editor-advanced-page.md)  
  
 <span data-ttu-id="bd352-172">SAP BW 원본을 구성하는 동안 다양한 대화 상자를 사용하여 SAP Netweaver BW 개체를 조회하거나 원본 데이터를 미리 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd352-172">While you are configuring the SAP BW source, you can also use various dialog boxes to look up SAP Netweaver BW objects or to preview the source data.</span></span> <span data-ttu-id="bd352-173">이러한 대화 상자에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="bd352-173">For more information about these dialog boxes, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="bd352-174">RFC 대상 조회</span><span class="sxs-lookup"><span data-stu-id="bd352-174">Look Up RFC Destination</span></span>](look-up-rfc-destination.md)  
  
-   [<span data-ttu-id="bd352-175">프로세스 체인 조회</span><span class="sxs-lookup"><span data-stu-id="bd352-175">Look Up Process Chain</span></span>](look-up-process-chain.md)  
  
-   [<span data-ttu-id="bd352-176">요청 로그</span><span class="sxs-lookup"><span data-stu-id="bd352-176">Request Log</span></span>](request-log.md)  
  
-   [<span data-ttu-id="bd352-177">미리 보기</span><span class="sxs-lookup"><span data-stu-id="bd352-177">Preview</span></span>](preview.md)  
  
## <a name="see-also"></a><span data-ttu-id="bd352-178">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bd352-178">See Also</span></span>  
 [<span data-ttu-id="bd352-179">Microsoft Connector 1.1 for SAP BW 구성 요소</span><span class="sxs-lookup"><span data-stu-id="bd352-179">Microsoft Connector 1.1 for SAP BW Components</span></span>](../microsoft-connector-for-sap-bw-components.md)  
  
  
