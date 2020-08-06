---
title: SAP BW 대상 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a612ed91-b89b-4173-a0b1-0bce381e1e28
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8a0d7c5b75da89e665dbe60bbd7e29ce74da67db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652977"
---
# <a name="sap-bw-destination"></a><span data-ttu-id="26725-102">SAP BW 대상</span><span class="sxs-lookup"><span data-stu-id="26725-102">SAP BW Destination</span></span>
  <span data-ttu-id="26725-103">SAP BW 대상은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW의 대상 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="26725-103">The SAP BW destination is the destination component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span> <span data-ttu-id="26725-104">따라서 SAP BW 대상은 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지의 데이터 흐름에서 SAP Netweaver BW 버전 7 시스템으로 데이터를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="26725-104">Thus, the SAP BW destination loads data from the data flow in an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package into an SAP Netweaver BW version 7 system.</span></span>  
  
 <span data-ttu-id="26725-105">이 대상에는 하나의 입력과 하나의 오류 출력이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="26725-105">This destination has one input and one error output.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="26725-106">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="26725-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="26725-107">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="26725-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="26725-108">SAP BW 대상을 사용하려면 다음 태스크를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26725-108">To use the SAP BW destination, you have to do the following tasks:</span></span>  
  
-   [<span data-ttu-id="26725-109">SAP Netweaver BW 개체 준비</span><span class="sxs-lookup"><span data-stu-id="26725-109">Prepare the SAP Netweaver BW objects</span></span>](#bkmk_Prepare_Objects)  
  
-   [<span data-ttu-id="26725-110">SAP Netweaver BW 시스템에 연결</span><span class="sxs-lookup"><span data-stu-id="26725-110">Connect to the SAP Netweaver BW system</span></span>](#bkmk_Connect_Database)  
  
-   [<span data-ttu-id="26725-111">SAP BW 대상 구성</span><span class="sxs-lookup"><span data-stu-id="26725-111">Configure the SAP BW destination</span></span>](#bkmk_Configure_Destination)  
  
##  <a name="preparing-the-sap-netweaver-bw-objects-that-the-destination-requires"></a><a name="bkmk_Prepare_Objects"></a> <span data-ttu-id="26725-112">대상에 필요한 SAP Netweaver BW 개체 준비</span><span class="sxs-lookup"><span data-stu-id="26725-112">Preparing the SAP Netweaver BW Objects That the Destination Requires</span></span>  
 <span data-ttu-id="26725-113">SAP BW 대상이 작동하려면 특정 개체가 SAP Netweaver BW 시스템에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26725-113">The SAP BW destination requires that certain objects are in the SAP Netweaver BW system before the destination can function.</span></span> <span data-ttu-id="26725-114">이러한 개체가 없는 경우 다음 단계를 수행하여 SAP Netweaver BW 시스템에서 이러한 개체를 만들고 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26725-114">If these objects do not already exist, you have to follow these steps to create and configure these objects in the SAP Netweaver BW system.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="26725-115">이러한 개체와 구성 단계에 대한 자세한 내용은 SAP Netweaver BW 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="26725-115">For additional details about these objects and these configuration steps, see the SAP Netweaver BW documentation.</span></span>  
  
1.  <span data-ttu-id="26725-116">새 원본 시스템을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="26725-116">Create a new Source System:</span></span>  
  
    1.  <span data-ttu-id="26725-117">**"Third Party/Staging BAPIs"** 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="26725-117">Select the type, **"Third Party/Staging BAPIs"**.</span></span>  
  
    2.  <span data-ttu-id="26725-118">**Communication Type with Target System**(대상 시스템과 통신 유형)에서 **Non-Unicode (Inactive MDMP Settings)** (비유니코드(비활성 MDMP 설정))를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="26725-118">For **Communication Type with Target System**, select **Non-Unicode (Inactive MDMP Settings)**.</span></span>  
  
    3.  <span data-ttu-id="26725-119">적절한 프로그램 ID를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="26725-119">Assign an appropriate Program ID.</span></span>  
  
2.  <span data-ttu-id="26725-120">InfoSource에 원본 시스템을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="26725-120">Assign the Source System to an InfoSource.</span></span>  
  
3.  <span data-ttu-id="26725-121">InfoPackage를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="26725-121">Create an InfoPackage.</span></span>  
  
     <span data-ttu-id="26725-122">InfoPackage는 SAP BW 대상에 필요한 가장 중요한 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="26725-122">The InfoPackage is the most important object that is required by the SAP BW destination.</span></span>  
  
 <span data-ttu-id="26725-123">SAP Netweaver BW 시스템으로의 데이터 로드를 지원하는 데 필요한 InfoObject, InfoCube, InfoSource 및 InfoPackage를 추가로 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26725-123">You can also create additional InfoObjects, InfoCubes, InfoSources, and InfoPackages that are required to support loading data into the SAP Netweaver BW system.</span></span>  
  
##  <a name="connecting-to-the-sap-netweaver-bw-system"></a><a name="bkmk_Connect_Database"></a> <span data-ttu-id="26725-124">SAP Netweaver BW 시스템에 연결</span><span class="sxs-lookup"><span data-stu-id="26725-124">Connecting to the SAP Netweaver BW System</span></span>  
 <span data-ttu-id="26725-125">SAP Netweaver BW 버전 7 시스템에 연결하기 위해 SAP BW 대상은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 패키지의 일부인 SAP BW 연결 관리자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="26725-125">To connect to the SAP Netweaver BW version 7 system, the SAP BW destination uses the SAP BW connection manager that is part of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW package.</span></span> <span data-ttu-id="26725-126">SAP BW 연결 관리자는 SAP BW 대상이 사용할 수 있는 유일한 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 연결 관리자입니다.</span><span class="sxs-lookup"><span data-stu-id="26725-126">The SAP BW connection manager is the only [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] connection manager that the SAP BW destination can use.</span></span>  
  
 <span data-ttu-id="26725-127">SAP BW 연결 관리자에 대한 자세한 내용은 [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="26725-127">For more information about the SAP BW connection manager, see [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md).</span></span>  
  
##  <a name="configuring-the-sap-bw-destination"></a><a name="bkmk_Configure_Destination"></a> <span data-ttu-id="26725-128">SAP BW 대상 구성</span><span class="sxs-lookup"><span data-stu-id="26725-128">Configuring the SAP BW Destination</span></span>  
 <span data-ttu-id="26725-129">다음과 같은 방법으로 SAP BW 대상을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26725-129">You can configure the SAP BW destination in the following ways:</span></span>  
  
-   <span data-ttu-id="26725-130">데이터를 로드하는 데 사용할 InfoPackage를 조회하고 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="26725-130">Look up and select the InfoPackage to use to load data.</span></span>  
  
-   <span data-ttu-id="26725-131">데이터 흐름의 각 열을 InfoPackage의 적절한 InfoObject에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="26725-131">Map each column in the data flow to the appropriate InfoObject in the InfoPackage.</span></span>  
  
-   <span data-ttu-id="26725-132">`PackageSize` 속성을 구성하여 한 번에 전송될 데이터 행 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="26725-132">Specify how many rows of data will be transferred at a time by configuring the `PackageSize` property.</span></span>  
  
-   <span data-ttu-id="26725-133">SAP Netweaver BW 시스템에서 데이터 로드가 완료될 때까지 대기하도록 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="26725-133">Choose to wait until the loading of data is completed by the SAP Netweaver BW system.</span></span>  
  
-   <span data-ttu-id="26725-134">InfoPackage를 트리거하지 않고 SAP Netweaver BW 시스템에서 데이터 로드를 시작했다는 알림을 받을 때까지 대기하도록 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="26725-134">Choose not to trigger the InfoPackage, but to wait for notification that the SAP Netweaver BW system has started the loading of data.</span></span>  
  
-   <span data-ttu-id="26725-135">데이터 로드가 완료된 후 필요에 따라 다른 프로세스 체인을 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="26725-135">Optionally, trigger another process chain after the loading of data is completed.</span></span>  
  
-   <span data-ttu-id="26725-136">필요에 따라 대상에 필요한 SAP Netweaver BW 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="26725-136">Optionally, create the SAP Netweaver BW objects that are required by the destination.</span></span> <span data-ttu-id="26725-137">여기에는 InfoObject, InfoCube, InfoSource 및 InfoPackage를 만드는 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="26725-137">This includes creating InfoObjects, InfoCubes, InfoSources, and InfoPackages.</span></span>  
  
-   <span data-ttu-id="26725-138">선택한 옵션을 사용하여 데이터 로드를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="26725-138">Test the loading of data with the options that you have selected.</span></span>  
  
 <span data-ttu-id="26725-139">대상에 의한 RFC 함수 호출의 로깅을 사용하도록 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26725-139">You can also enable logging of RFC function calls by the destination.</span></span> <span data-ttu-id="26725-140">이 로깅은 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지에서 사용하도록 설정할 수 있는 선택적 로깅과 별개입니다. 대상이 사용할 SAP BW 연결 관리자를 구성할 때 RFC 함수 호출의 로깅을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="26725-140">(This logging is separate from the optional logging that you can enable on [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.) You enable logging of RFC function calls when you configure the SAP BW connection manager that the destination will use.</span></span> <span data-ttu-id="26725-141">SAP BW 연결 관리자를 구성하는 방법은 [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="26725-141">For more information about how to configure the SAP BW connection manager, see [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md).</span></span>  
  
 <span data-ttu-id="26725-142">대상을 구성하는 데 필요한 값 중 모르는 것이 있으면 SAP 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="26725-142">If you do not know all the values that are required to configure the destination, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="26725-143">SAP BW 연결 관리자, 원본 및 대상을 구성하고 사용하는 방법을 제시하는 연습은 [SAP BI 7.0에서 SQL Server 2008 Integration Services 사용](https://go.microsoft.com/fwlink/?LinkID=137090)백서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="26725-143">For a walkthrough that demonstrates how to configure and use the SAP BW connection manager, source, and destination, see the white paper, [Using SQL Server 2008 Integration Services with SAP BI 7.0](https://go.microsoft.com/fwlink/?LinkID=137090).</span></span> <span data-ttu-id="26725-144">또한 이 백서는 SAP BW에 필요한 개체를 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="26725-144">This white paper also shows how to configure the required objects in SAP BW.</span></span>  
  
### <a name="using-the-ssis-designer-to-configure-the-destination"></a><span data-ttu-id="26725-145">SSIS 디자이너를 사용하여 대상 구성</span><span class="sxs-lookup"><span data-stu-id="26725-145">Using the SSIS Designer to Configure the Destination</span></span>  
 <span data-ttu-id="26725-146">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 SAP BW 대상의 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="26725-146">For more information about the properties of the SAP BW destination that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="26725-147">SAP BW 대상 편집기&#40;연결 관리자 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="26725-147">SAP BW Destination Editor &#40;Connection Manager Page&#41;</span></span>](sap-bw-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="26725-148">SAP BW 대상 편집기&#40;매핑 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="26725-148">SAP BW Destination Editor &#40;Mappings Page&#41;</span></span>](sap-bw-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="26725-149">SAP BW 대상 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="26725-149">SAP BW Destination Editor &#40;Error Output Page&#41;</span></span>](sap-bw-destination-editor-error-output-page.md)  
  
-   [<span data-ttu-id="26725-150">SAP BW 대상 편집기&#40;고급 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="26725-150">SAP BW Destination Editor &#40;Advanced Page&#41;</span></span>](sap-bw-destination-editor-advanced-page.md)  
  
 <span data-ttu-id="26725-151">SAP BW 대상을 구성하는 동안 다양한 대화 상자를 사용하여 SAP Netweaver BW 개체를 조회하거나 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26725-151">While you are configuring the SAP BW destination, you can also use various dialog boxes to look up or to create SAP Netweaver BW objects.</span></span> <span data-ttu-id="26725-152">이러한 대화 상자에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="26725-152">For more information about these dialog boxes, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="26725-153">InfoPackage 조회</span><span class="sxs-lookup"><span data-stu-id="26725-153">Look Up InfoPackage</span></span>](look-up-infopackage.md)  
  
-   [<span data-ttu-id="26725-154">새 InfoObject 만들기</span><span class="sxs-lookup"><span data-stu-id="26725-154">Create New InfoObject</span></span>](create-new-infoobject.md)  
  
-   [<span data-ttu-id="26725-155">트랜잭션 데이터용 InfoCube 만들기</span><span class="sxs-lookup"><span data-stu-id="26725-155">Create InfoCube for Transaction Data</span></span>](create-infocube-for-transaction-data.md)  
  
-   [<span data-ttu-id="26725-156">InfoObject 조회</span><span class="sxs-lookup"><span data-stu-id="26725-156">Look Up InfoObject</span></span>](look-up-infoobject.md)  
  
-   [<span data-ttu-id="26725-157">InfoSource 만들기</span><span class="sxs-lookup"><span data-stu-id="26725-157">Create InfoSource</span></span>](create-infosource.md)  
  
-   [<span data-ttu-id="26725-158">트랜잭션 데이터용 InfoSource 만들기</span><span class="sxs-lookup"><span data-stu-id="26725-158">Create InfoSource for Transaction Data</span></span>](create-infosource-for-transaction-data.md)  
  
-   [<span data-ttu-id="26725-159">마스터 데이터용 InfoSource 만들기</span><span class="sxs-lookup"><span data-stu-id="26725-159">Create InfoSource for Master Data</span></span>](create-infosource-for-master-data.md)  
  
-   [<span data-ttu-id="26725-160">InfoPackage 만들기</span><span class="sxs-lookup"><span data-stu-id="26725-160">Create InfoPackage</span></span>](create-infopackage.md)  
  
## <a name="see-also"></a><span data-ttu-id="26725-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="26725-161">See Also</span></span>  
 [<span data-ttu-id="26725-162">Microsoft Connector 1.1 for SAP BW 구성 요소</span><span class="sxs-lookup"><span data-stu-id="26725-162">Microsoft Connector 1.1 for SAP BW Components</span></span>](../microsoft-connector-for-sap-bw-components.md)  
  
  
