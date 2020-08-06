---
title: SAP BW 원본 편집기(연결 관리자 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 2a6dc531-85ca-43c5-a65f-3ad3f7d537c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8c6b1782daf8c00b3b3d3a7d13b5ffa00adeeba2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728539"
---
# <a name="sap-bw-source-editor-connection-manager-page"></a><span data-ttu-id="ce5da-102">SAP BW 원본 편집기(연결 관리자 페이지)</span><span class="sxs-lookup"><span data-stu-id="ce5da-102">SAP BW Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="ce5da-103">**SAP BW 원본 편집기** 의 **연결 관리자** 페이지를 사용하여 SAP BW 원본의 SAP BW 연결 관리자를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-103">Use the **Connection Manager** page of the **SAP BW Source Editor** to select the SAP BW connection manager for the SAP BW source.</span></span> <span data-ttu-id="ce5da-104">이 페이지에서는 SAP Netweaver BW 시스템에서 데이터를 추출하기 위한 실행 모드와 매개 변수도 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-104">On this page, you also select the execution mode and the parameters for extracting the data from the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="ce5da-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW의 SAP BW 원본 구성 요소에 대한 자세한 내용은 [SAP BW 원본](sap-bw-source.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce5da-105">To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ce5da-106">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="ce5da-107">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ce5da-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ce5da-108">SAP Netweaver BW에서 데이터를 추출하려면 추가 SAP 라이선스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-108">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="ce5da-109">SAP에서 이러한 요구 사항을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="ce5da-109">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="ce5da-110">**연결 관리자 페이지를 열려면**</span><span class="sxs-lookup"><span data-stu-id="ce5da-110">**To open the Connection Manager page**</span></span>  
  
1.  <span data-ttu-id="ce5da-111">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 SAP BW 원본이 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-111">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="ce5da-112">**데이터 흐름** 탭에서 SAP BW 원본을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-112">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="ce5da-113">**SAP BW 원본 편집기**에서 **연결 관리자** 를 클릭하여 편집기의 **연결 관리자** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-113">In the **SAP BW Source Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="ce5da-114">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="ce5da-114">Static Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ce5da-115">원본을 구성하는 데 필요한 값 중 모르는 것이 있으면 SAP 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="ce5da-115">If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="ce5da-116">**SAP BW 연결 관리자**</span><span class="sxs-lookup"><span data-stu-id="ce5da-116">**SAP BW connection manager**</span></span>  
 <span data-ttu-id="ce5da-117">목록에서 기존 연결 관리자를 선택하거나 **새로 만들기**를 클릭하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-117">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="ce5da-118">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="ce5da-118">**New**</span></span>  
 <span data-ttu-id="ce5da-119">**SAP BW 연결 관리자** 대화 상자를 사용하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-119">Create a new connection manager by using the **SAP BW Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="ce5da-120">이 대화 상자에 대한 자세한 내용은 [SAP BW Connection Manager Editor](../sap-bw-connection-manager-editor.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ce5da-120">For more information about this dialog box, see [SAP BW Connection Manager Editor](../sap-bw-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="ce5da-121">**OHS 대상**</span><span class="sxs-lookup"><span data-stu-id="ce5da-121">**OHS destination**</span></span>  
 <span data-ttu-id="ce5da-122">원본에서 데이터를 추출하는 데 사용할 OHS(Open Hub Service) 대상을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-122">Select the Open Hub Service (OHS) destination to use to extract data from the source.</span></span>  
  
 <span data-ttu-id="ce5da-123">**실행 모드**</span><span class="sxs-lookup"><span data-stu-id="ce5da-123">**Execution mode**</span></span>  
 <span data-ttu-id="ce5da-124">원본에서 데이터를 추출하는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-124">Specify the method for extracting data from the source.</span></span>  
  
|<span data-ttu-id="ce5da-125">옵션</span><span class="sxs-lookup"><span data-stu-id="ce5da-125">Option</span></span>|<span data-ttu-id="ce5da-126">Description</span><span class="sxs-lookup"><span data-stu-id="ce5da-126">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ce5da-127">**P - 프로세스 체인 트리거**</span><span class="sxs-lookup"><span data-stu-id="ce5da-127">**P - Trigger Process Chain**</span></span>|<span data-ttu-id="ce5da-128">프로세스 체인을 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-128">Trigger a process chain.</span></span> <span data-ttu-id="ce5da-129">이 경우 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지는 추출 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-129">In this case, the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package starts the extraction process.</span></span>|  
|<span data-ttu-id="ce5da-130">**W - 알릴 때까지 대기**</span><span class="sxs-lookup"><span data-stu-id="ce5da-130">**W - Wait for Notify**</span></span>|<span data-ttu-id="ce5da-131">SAP Netweaver BW 시스템에서 데이터 추출 시작 알림을 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-131">Wait for notification from the SAP Netweaver BW system to begin extracting the data.</span></span> <span data-ttu-id="ce5da-132">이 경우 SAP Netweaver BW 시스템은 추출 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-132">In this case, the SAP Netweaver BW system starts the extraction process.</span></span>|  
|<span data-ttu-id="ce5da-133">**E - 추출만**</span><span class="sxs-lookup"><span data-stu-id="ce5da-133">**E - Extract Only**</span></span>|<span data-ttu-id="ce5da-134">특정 요청 ID와 연결된 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-134">Retrieve the data that is associated with a particular Request ID.</span></span> <span data-ttu-id="ce5da-135">이 경우 SAP Netweaver BW 시스템에서 데이터를 내부 테이블에 이미 추출했으므로 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지는 데이터를 읽기만 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-135">In this case, the SAP Netweaver BW system has already extracted the data into an internal table, and the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package just reads the data.</span></span>|  
  
 <span data-ttu-id="ce5da-136">**미리 보기**</span><span class="sxs-lookup"><span data-stu-id="ce5da-136">**Preview**</span></span>  
 <span data-ttu-id="ce5da-137">결과를 미리 볼 수 있는 **미리 보기** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-137">Open the **Preview** dialog box in which you can preview results.</span></span> <span data-ttu-id="ce5da-138">자세한 내용은 [Preview](preview.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce5da-138">For more information, see [Preview](preview.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ce5da-139">SAP BW 원본 편집기의 **연결 관리자** 페이지에서 사용할 수 있는 **미리 보기** 옵션은 데이터를 실제로 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-139">The **Preview** option, that is available on the **Connection Manager** page of the SAP BW Source Editor, actually extracts data.</span></span> <span data-ttu-id="ce5da-140">이전 추출 이후에 변경된 데이터만 추출하도록 SAP Netweaver BW를 구성한 경우 **미리 보기** 를 선택하면 미리 본 데이터가 다음 추출에서 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-140">If you have configured SAP Netweaver BW to extract only data that has changed since the previous extraction, selecting **Preview** will exclude the previewed data from the next extraction.</span></span>  
  
 <span data-ttu-id="ce5da-141">**미리 보기**를 클릭하면 **요청 로그** 대화 상자도 열립니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-141">When you click **Preview**, you also open the **Request Log** dialog box.</span></span> <span data-ttu-id="ce5da-142">이 대화 상자를 사용하여 샘플 데이터에 대해 SAP Netweaver BW 시스템에 요청하는 동안 기록된 이벤트를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-142">You can use this dialog box to view the events that are logged during the request that is made to the SAP Netweaver BW system for sample data.</span></span> <span data-ttu-id="ce5da-143">자세한 내용은 [Request Log](request-log.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce5da-143">For more information, see [Request Log](request-log.md).</span></span>  
  
## <a name="execution-mode-dynamic-options"></a><span data-ttu-id="ce5da-144">실행 모드 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="ce5da-144">Execution Mode Dynamic Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ce5da-145">원본을 구성하는 데 필요한 값 중 모르는 것이 있으면 SAP 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="ce5da-145">If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.</span></span>  
  
### <a name="execution-mode--p---trigger-process-chain"></a><span data-ttu-id="ce5da-146">실행 모드 = P - 프로세스 체인 트리거</span><span class="sxs-lookup"><span data-stu-id="ce5da-146">Execution Mode = P - Trigger Process Chain</span></span>  
  
#### <a name="rfc-destination-options"></a><span data-ttu-id="ce5da-147">RFC 대상 옵션</span><span class="sxs-lookup"><span data-stu-id="ce5da-147">RFC Destination Options</span></span>  
 <span data-ttu-id="ce5da-148">이러한 값을 미리 알고 입력할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-148">You do not have to know and enter these values in advance.</span></span> <span data-ttu-id="ce5da-149">**조회** 단추를 사용하여 적절한 RFC 대상을 찾고 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-149">Use the **Look up** button to find and select the appropriate RFC destination.</span></span> <span data-ttu-id="ce5da-150">RFC 대상을 선택하면 이러한 옵션의 적절한 값이 입력됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-150">After you select an RFC destination, the component enters the appropriate values for these options.</span></span>  
  
 <span data-ttu-id="ce5da-151">**게이트웨이 호스트**</span><span class="sxs-lookup"><span data-stu-id="ce5da-151">**Gateway host**</span></span>  
 <span data-ttu-id="ce5da-152">게이트웨이 호스트의 서버 이름 또는 IP 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-152">Enter the server name or IP address of the gateway host.</span></span> <span data-ttu-id="ce5da-153">일반적으로 이름 또는 IP 주소는 SAP 애플리케이션 서버와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-153">Usually, the name or IP address is the same as the SAP application server.</span></span>  
  
 <span data-ttu-id="ce5da-154">**게이트웨이 서비스**</span><span class="sxs-lookup"><span data-stu-id="ce5da-154">**Gateway service**</span></span>  
 <span data-ttu-id="ce5da-155">게이트웨이 서비스 이름을 `sapgwNN` 형식으로 입력합니다. 여기서 `NN`은 시스템 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-155">Enter the name of the gateway service, in the format `sapgwNN`, where `NN` is the system number.</span></span>  
  
 <span data-ttu-id="ce5da-156">**프로그램 ID**</span><span class="sxs-lookup"><span data-stu-id="ce5da-156">**Program ID**</span></span>  
 <span data-ttu-id="ce5da-157">RFC 대상과 연결된 프로그램 ID를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-157">Enter the Program ID that is associated with the RFC destination.</span></span>  
  
 <span data-ttu-id="ce5da-158">**조회**</span><span class="sxs-lookup"><span data-stu-id="ce5da-158">**Look up**</span></span>  
 <span data-ttu-id="ce5da-159">**RFC 대상 조회** 대화 상자를 사용하여 RFC 대상을 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-159">Look up the RFC destination by using the **Look Up RFC Destination** dialog box.</span></span> <span data-ttu-id="ce5da-160">이 대화 상자에 대한 자세한 내용은 [Look Up RFC Destination](look-up-rfc-destination.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ce5da-160">For more information about this dialog box, see [Look Up RFC Destination](look-up-rfc-destination.md).</span></span>  
  
#### <a name="process-chain-options"></a><span data-ttu-id="ce5da-161">프로세스 체인 옵션</span><span class="sxs-lookup"><span data-stu-id="ce5da-161">Process Chain Options</span></span>  
 <span data-ttu-id="ce5da-162">이러한 값을 미리 알고 입력할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-162">You do not have to know and enter these values in advance.</span></span> <span data-ttu-id="ce5da-163">**조회** 단추를 사용하여 적절한 프로세스 체인을 찾고 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-163">Use the **Look up** button to find and select the appropriate process chain.</span></span> <span data-ttu-id="ce5da-164">프로세스 체인을 선택하면 이 옵션의 적절한 값이 입력됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-164">After you select a process chain, the component enters the appropriate value for the option.</span></span>  
  
 <span data-ttu-id="ce5da-165">**프로세스 체인**</span><span class="sxs-lookup"><span data-stu-id="ce5da-165">**Process chain**</span></span>  
 <span data-ttu-id="ce5da-166">원본에 의해 트리거될 프로세스 체인의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-166">Enter the name of the process chain to be triggered by the source.</span></span>  
  
 <span data-ttu-id="ce5da-167">**조회**</span><span class="sxs-lookup"><span data-stu-id="ce5da-167">**Look up**</span></span>  
 <span data-ttu-id="ce5da-168">**프로세스 체인 조회** 대화 상자를 사용하여 프로세스 체인을 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-168">Look up the process chain by using the **Look Up Process Chain** dialog box.</span></span> <span data-ttu-id="ce5da-169">이 대화 상자에 대한 자세한 내용은 [Look Up Process Chain](look-up-process-chain.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ce5da-169">For more information about this dialog box, see [Look Up Process Chain](look-up-process-chain.md).</span></span>  
  
### <a name="execution-mode--w---wait-for-notify"></a><span data-ttu-id="ce5da-170">실행 모드 = W - 알릴 때까지 대기</span><span class="sxs-lookup"><span data-stu-id="ce5da-170">Execution Mode = W - Wait for Notify</span></span>  
  
#### <a name="rfc-destination-options"></a><span data-ttu-id="ce5da-171">RFC 대상 옵션</span><span class="sxs-lookup"><span data-stu-id="ce5da-171">RFC Destination Options</span></span>  
 <span data-ttu-id="ce5da-172">이러한 값을 미리 알고 입력할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-172">You do not have to know and enter these values in advance.</span></span> <span data-ttu-id="ce5da-173">**조회** 단추를 사용하여 적절한 RFC 대상을 찾고 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-173">Use the **Look up** button to find and select the appropriate RFC destination.</span></span> <span data-ttu-id="ce5da-174">RFC 대상을 선택하면 이러한 옵션의 적절한 값이 입력됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-174">After you select an RFC destination, the component enters the appropriate values for the options.</span></span>  
  
 <span data-ttu-id="ce5da-175">**게이트웨이 호스트**</span><span class="sxs-lookup"><span data-stu-id="ce5da-175">**Gateway host**</span></span>  
 <span data-ttu-id="ce5da-176">게이트웨이 호스트의 서버 이름 또는 IP 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-176">Enter the server name or IP address of the gateway host.</span></span> <span data-ttu-id="ce5da-177">일반적으로 이름 또는 IP 주소는 SAP 애플리케이션 서버와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-177">Usually, the name or IP address is the same as the SAP application server.</span></span>  
  
 <span data-ttu-id="ce5da-178">**게이트웨이 서비스**</span><span class="sxs-lookup"><span data-stu-id="ce5da-178">**Gateway service**</span></span>  
 <span data-ttu-id="ce5da-179">게이트웨이 서비스 이름을 `sapgwNN` 형식으로 입력합니다. 여기서 `NN`은 시스템 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-179">Enter the name of the gateway service, in the format `sapgwNN`, where `NN` is the system number.</span></span>  
  
 <span data-ttu-id="ce5da-180">**프로그램 ID**</span><span class="sxs-lookup"><span data-stu-id="ce5da-180">**Program ID**</span></span>  
 <span data-ttu-id="ce5da-181">RFC 대상과 연결된 프로그램 ID를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-181">Enter the Program ID that is associated with the RFC destination.</span></span>  
  
 <span data-ttu-id="ce5da-182">**조회**</span><span class="sxs-lookup"><span data-stu-id="ce5da-182">**Look up**</span></span>  
 <span data-ttu-id="ce5da-183">**RFC 대상 조회** 대화 상자를 사용하여 RFC 대상을 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-183">Look up the RFC destination by using the **Look Up RFC Destination** dialog box.</span></span> <span data-ttu-id="ce5da-184">이 대화 상자에 대한 자세한 내용은 [Look Up RFC Destination](look-up-rfc-destination.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ce5da-184">For more information about this dialog box, see [Look Up RFC Destination](look-up-rfc-destination.md).</span></span>  
  
### <a name="execution-mode--e---extract-only"></a><span data-ttu-id="ce5da-185">실행 모드 = E - 추출만</span><span class="sxs-lookup"><span data-stu-id="ce5da-185">Execution Mode = E - Extract Only</span></span>  
 <span data-ttu-id="ce5da-186">**요청 ID**</span><span class="sxs-lookup"><span data-stu-id="ce5da-186">**Request ID**</span></span>  
 <span data-ttu-id="ce5da-187">추출과 연결된 요청 ID를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5da-187">Enter the Request ID that is associated with the extraction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce5da-188">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ce5da-188">See Also</span></span>  
 <span data-ttu-id="ce5da-189">[SAP BW 원본 편집기&#40;열 페이지&#41;](sap-bw-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="ce5da-189">[SAP BW Source Editor &#40;Columns Page&#41;](sap-bw-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="ce5da-190">[SAP BW 원본 편집기&#40;오류 출력 페이지&#41;](sap-bw-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="ce5da-190">[SAP BW Source Editor &#40;Error Output Page&#41;](sap-bw-source-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="ce5da-191">[SAP BW 원본 편집기&#40;고급 페이지&#41;](sap-bw-source-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="ce5da-191">[SAP BW Source Editor &#40;Advanced Page&#41;](sap-bw-source-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="ce5da-192">Microsoft Connector 1.1 for SAP BW F1 도움말</span><span class="sxs-lookup"><span data-stu-id="ce5da-192">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
