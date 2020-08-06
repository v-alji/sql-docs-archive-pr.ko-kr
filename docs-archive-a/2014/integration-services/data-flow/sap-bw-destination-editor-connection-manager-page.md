---
title: SAP BW 대상 편집기(연결 관리자 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 04ae38f8-5287-45a3-826a-8aac5dd15a91
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0dd628f1a0fec09490e0d3720610d1232882ed92
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728551"
---
# <a name="sap-bw-destination-editor-connection-manager-page"></a><span data-ttu-id="ec29f-102">SAP BW 대상 편집기(연결 관리자 페이지)</span><span class="sxs-lookup"><span data-stu-id="ec29f-102">SAP BW Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="ec29f-103">**SAP BW 대상 편집기** 의 **연결 관리자** 페이지를 사용하여 SAP BW 대상이 사용할 SAP BW 연결 관리자를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-103">Use the **Connection Manager** page of the **SAP BW Destination Editor** to select the SAP BW connection manager that the SAP BW destination will use.</span></span> <span data-ttu-id="ec29f-104">이 페이지에서는 SAP Netweaver BW 시스템으로 데이터를 로드하기 위한 매개 변수도 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-104">On this page, you also select the parameters for loading the data into the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="ec29f-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW의 SAP BW 대상에 대한 자세한 내용은 [SAP BW 대상](sap-bw-destination.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ec29f-105">To learn more about the SAP BW destination of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ec29f-106">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="ec29f-107">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ec29f-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="ec29f-108">**연결 관리자 페이지를 열려면**</span><span class="sxs-lookup"><span data-stu-id="ec29f-108">**To open the Connection Manager page**</span></span>  
  
1.  <span data-ttu-id="ec29f-109">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 SAP BW 대상이 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="ec29f-110">**데이터 흐름** 탭에서 SAP BW 대상을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-110">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="ec29f-111">**SAP BW 대상 편집기**에서 **연결 관리자** 를 클릭하여 편집기의 **연결 관리자** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-111">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ec29f-112">옵션</span><span class="sxs-lookup"><span data-stu-id="ec29f-112">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ec29f-113">대상을 구성하는 데 필요한 값 중 모르는 것이 있으면 SAP 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="ec29f-113">If you do not know all the values that are required to configure the destination, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="ec29f-114">**SAP BW 연결 관리자**</span><span class="sxs-lookup"><span data-stu-id="ec29f-114">**SAP BW connection manager**</span></span>  
 <span data-ttu-id="ec29f-115">목록에서 기존 연결 관리자를 선택하거나 **새로 만들기**를 클릭하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-115">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="ec29f-116">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="ec29f-116">**New**</span></span>  
 <span data-ttu-id="ec29f-117">**SAP BW 연결 관리자** 대화 상자를 사용하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-117">Create a new connection manager by using the **SAP BW Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="ec29f-118">**테스트 로드**</span><span class="sxs-lookup"><span data-stu-id="ec29f-118">**Test Load**</span></span>  
 <span data-ttu-id="ec29f-119">사용자가 선택한 설정을 사용하고 0 행을 로드하는 로드 프로세스의 테스트를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-119">Perform a test of the loading process that uses the settings that you have selected and loads zero rows.</span></span>  
  
### <a name="infopackageinfosource-options"></a><span data-ttu-id="ec29f-120">InfoPackage/InfoSource 옵션</span><span class="sxs-lookup"><span data-stu-id="ec29f-120">InfoPackage/InfoSource Options</span></span>  
 <span data-ttu-id="ec29f-121">이러한 값을 미리 알고 입력할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-121">You do not have to know and enter these values in advance.</span></span> <span data-ttu-id="ec29f-122">**조회** 단추를 사용하여 적절한 InfoPackage를 찾고 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-122">Use the **Look up** button to find and select the appropriate InfoPackage.</span></span> <span data-ttu-id="ec29f-123">InfoPackage를 선택하면 이러한 옵션의 적절한 값이 입력됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-123">After you select an InfoPackage, the component enters the appropriate values for these options.</span></span>  
  
 <span data-ttu-id="ec29f-124">**InfoPackage**</span><span class="sxs-lookup"><span data-stu-id="ec29f-124">**InfoPackage**</span></span>  
 <span data-ttu-id="ec29f-125">InfoPackage의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-125">Enter the name of the InfoPackage.</span></span>  
  
 <span data-ttu-id="ec29f-126">**InfoSource**</span><span class="sxs-lookup"><span data-stu-id="ec29f-126">**InfoSource**</span></span>  
 <span data-ttu-id="ec29f-127">InfoSource의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-127">Enter the name of the InfoSource.</span></span>  
  
 <span data-ttu-id="ec29f-128">**형식**</span><span class="sxs-lookup"><span data-stu-id="ec29f-128">**Type**</span></span>  
 <span data-ttu-id="ec29f-129">InfoSource의 유형을 식별하는 단일 문자를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-129">Enter the single-character that identifies the type of the InfoSource.</span></span> <span data-ttu-id="ec29f-130">다음 표에서는 허용 가능한 단일 문자 값을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-130">The following table lists the acceptable single-character values.</span></span>  
  
|<span data-ttu-id="ec29f-131">값</span><span class="sxs-lookup"><span data-stu-id="ec29f-131">Value</span></span>|<span data-ttu-id="ec29f-132">Description</span><span class="sxs-lookup"><span data-stu-id="ec29f-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ec29f-133">**D**</span><span class="sxs-lookup"><span data-stu-id="ec29f-133">**D**</span></span>|<span data-ttu-id="ec29f-134">트랜잭션 데이터</span><span class="sxs-lookup"><span data-stu-id="ec29f-134">Transaction data</span></span>|  
|<span data-ttu-id="ec29f-135">**M**</span><span class="sxs-lookup"><span data-stu-id="ec29f-135">**M**</span></span>|<span data-ttu-id="ec29f-136">마스터 데이터</span><span class="sxs-lookup"><span data-stu-id="ec29f-136">Master data</span></span>|  
|<span data-ttu-id="ec29f-137">**T**</span><span class="sxs-lookup"><span data-stu-id="ec29f-137">**T**</span></span>|<span data-ttu-id="ec29f-138">텍스트</span><span class="sxs-lookup"><span data-stu-id="ec29f-138">Texts</span></span>|  
|<span data-ttu-id="ec29f-139">**H**</span><span class="sxs-lookup"><span data-stu-id="ec29f-139">**H**</span></span>|<span data-ttu-id="ec29f-140">계층 데이터</span><span class="sxs-lookup"><span data-stu-id="ec29f-140">Hierarchy data</span></span>|  
  
 <span data-ttu-id="ec29f-141">**논리 시스템**</span><span class="sxs-lookup"><span data-stu-id="ec29f-141">**Logical system**</span></span>  
 <span data-ttu-id="ec29f-142">InfoPackage와 연결된 논리 시스템의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-142">Enter the name of the logical system that is associated with the InfoPackage.</span></span>  
  
 <span data-ttu-id="ec29f-143">**조회**</span><span class="sxs-lookup"><span data-stu-id="ec29f-143">**Look up**</span></span>  
 <span data-ttu-id="ec29f-144">**InfoPackage 조회** 대화 상자를 사용하여 InfoPackage를 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-144">Look up the InfoPackage by using the **Look Up InfoPackage** dialog box.</span></span> <span data-ttu-id="ec29f-145">이 대화 상자에 대한 자세한 내용은 [Look Up InfoPackage](look-up-infopackage.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ec29f-145">For more information about this dialog box, see [Look Up InfoPackage](look-up-infopackage.md).</span></span>  
  
### <a name="rfc-destination-options"></a><span data-ttu-id="ec29f-146">RFC 대상 옵션</span><span class="sxs-lookup"><span data-stu-id="ec29f-146">RFC Destination Options</span></span>  
 <span data-ttu-id="ec29f-147">이러한 값을 미리 알고 입력할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-147">You do not have to know and enter these values in advance.</span></span> <span data-ttu-id="ec29f-148">**조회** 단추를 사용하여 적절한 RFC 대상을 찾고 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-148">Use the **Look up** button to find and select the appropriate RFC destination.</span></span> <span data-ttu-id="ec29f-149">RFC 대상을 선택하면 이러한 옵션의 적절한 값이 입력됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-149">After you select an RFC destination, the component enters the appropriate values for these options.</span></span>  
  
 <span data-ttu-id="ec29f-150">**게이트웨이 호스트**</span><span class="sxs-lookup"><span data-stu-id="ec29f-150">**Gateway host**</span></span>  
 <span data-ttu-id="ec29f-151">게이트웨이 호스트의 서버 이름 또는 IP 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-151">Enter the server name or IP address of the gateway host.</span></span> <span data-ttu-id="ec29f-152">일반적으로 이름 또는 IP 주소는 SAP 애플리케이션 서버와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-152">Usually, the name or IP address is the same as the SAP application server.</span></span>  
  
 <span data-ttu-id="ec29f-153">**게이트웨이 서비스**</span><span class="sxs-lookup"><span data-stu-id="ec29f-153">**Gateway service**</span></span>  
 <span data-ttu-id="ec29f-154">게이트웨이 서비스 이름을 `sapgwNN` 형식으로 입력합니다. 여기서 `NN`은 시스템 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-154">Enter the name of the gateway service, in the format `sapgwNN`, where `NN` is the system number.</span></span>  
  
 <span data-ttu-id="ec29f-155">**프로그램 ID**</span><span class="sxs-lookup"><span data-stu-id="ec29f-155">**Program ID**</span></span>  
 <span data-ttu-id="ec29f-156">RFC 대상과 연결된 프로그램 ID를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-156">Enter the Program ID that is associated with the RFC destination.</span></span>  
  
 <span data-ttu-id="ec29f-157">**조회**</span><span class="sxs-lookup"><span data-stu-id="ec29f-157">**Look up**</span></span>  
 <span data-ttu-id="ec29f-158">**RFC 대상 조회** 대화 상자를 사용하여 RFC 대상을 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-158">Look up the RFC destination by using the **Look Up RFC Destination** dialog box.</span></span> <span data-ttu-id="ec29f-159">이 대화 상자에 대한 자세한 내용은 [Look Up RFC Destination](look-up-rfc-destination.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ec29f-159">For more information about this dialog box, see [Look Up RFC Destination](look-up-rfc-destination.md).</span></span>  
  
### <a name="create-sap-bw-objects-options"></a><span data-ttu-id="ec29f-160">SAP BW 개체 만들기 옵션</span><span class="sxs-lookup"><span data-stu-id="ec29f-160">Create SAP BW Objects Options</span></span>  
 <span data-ttu-id="ec29f-161">**개체 유형 선택**</span><span class="sxs-lookup"><span data-stu-id="ec29f-161">**Select object type**</span></span>  
 <span data-ttu-id="ec29f-162">만들려는 SAP Netweaver BW 개체의 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-162">Select the type of SAP Netweaver BW object that you want to create.</span></span> <span data-ttu-id="ec29f-163">다음 유형 중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-163">You can select one of the following types:</span></span>  
  
-   <span data-ttu-id="ec29f-164">InfoObject</span><span class="sxs-lookup"><span data-stu-id="ec29f-164">InfoObject</span></span>  
  
-   <span data-ttu-id="ec29f-165">InfoCube</span><span class="sxs-lookup"><span data-stu-id="ec29f-165">InfoCube</span></span>  
  
-   <span data-ttu-id="ec29f-166">InfoSource</span><span class="sxs-lookup"><span data-stu-id="ec29f-166">InfoSource</span></span>  
  
-   <span data-ttu-id="ec29f-167">InfoPackage</span><span class="sxs-lookup"><span data-stu-id="ec29f-167">InfoPackage</span></span>  
  
 <span data-ttu-id="ec29f-168">**만들기**</span><span class="sxs-lookup"><span data-stu-id="ec29f-168">**Create**</span></span>  
 <span data-ttu-id="ec29f-169">선택된 유형의 SAP Netweaver BW 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-169">Create the selected type of SAP Netweaver BW object.</span></span>  
  
|<span data-ttu-id="ec29f-170">개체 유형</span><span class="sxs-lookup"><span data-stu-id="ec29f-170">Object Type</span></span>|<span data-ttu-id="ec29f-171">결과</span><span class="sxs-lookup"><span data-stu-id="ec29f-171">Result</span></span>|  
|-----------------|------------|  
|<span data-ttu-id="ec29f-172">**InfoObject**</span><span class="sxs-lookup"><span data-stu-id="ec29f-172">**InfoObject**</span></span>|<span data-ttu-id="ec29f-173">**새 InfoObject 만들기** 대화 상자를 사용하여 새 InfoObject를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-173">Create a new InfoObject by using the **Create New InfoObject** dialog box.</span></span> <span data-ttu-id="ec29f-174">이 대화 상자에 대한 자세한 내용은 [Create New InfoObject](create-new-infoobject.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ec29f-174">For more information about this dialog box, see [Create New InfoObject](create-new-infoobject.md).</span></span>|  
|<span data-ttu-id="ec29f-175">**InfoCube**</span><span class="sxs-lookup"><span data-stu-id="ec29f-175">**InfoCube**</span></span>|<span data-ttu-id="ec29f-176">**트랜잭션 데이터용 InfoCube 만들기** 대화 상자를 사용하여 새 InfoCube를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-176">Create a new InfoCube by using the **Create InfoCube for Transaction Data** dialog box.</span></span> <span data-ttu-id="ec29f-177">이 대화 상자에 대한 자세한 내용은 [Create InfoCube for Transaction Data](create-infocube-for-transaction-data.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ec29f-177">For more information about this dialog box, see [Create InfoCube for Transaction Data](create-infocube-for-transaction-data.md).</span></span>|  
|<span data-ttu-id="ec29f-178">**InfoSource**</span><span class="sxs-lookup"><span data-stu-id="ec29f-178">**InfoSource**</span></span>|<span data-ttu-id="ec29f-179">**InfoSource 만들기** 대화 상자를 사용한 다음 **트랜잭션 데이터용 InfoSource 만들기** 또는 **마스터 데이터용 InfoSource 만들기** 대화 상자를 사용하여 새 InfoSource를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-179">Create a new InfoSource by using the **Create InfoSource** dialog box, and then by using the **Create InfoSource for Transaction Data** or the **Create InfoSource for Master Data** dialog box.</span></span> <span data-ttu-id="ec29f-180">이러한 대화 상자에 대한 자세한 내용은 [Create InfoSource](create-infosource.md), [Create InfoSource for Transaction Data](create-infosource-for-transaction-data.md) 및 [Create InfoSource for Master Data](create-infosource-for-master-data.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ec29f-180">For more information about these dialog boxes, see [Create InfoSource](create-infosource.md), [Create InfoSource for Transaction Data](create-infosource-for-transaction-data.md) and [Create InfoSource for Master Data](create-infosource-for-master-data.md).</span></span>|  
|<span data-ttu-id="ec29f-181">**InfoPackage**</span><span class="sxs-lookup"><span data-stu-id="ec29f-181">**InfoPackage**</span></span>|<span data-ttu-id="ec29f-182">**InfoPackage 만들기** 대화 상자를 사용하여 새 InfoPackage를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ec29f-182">Create a new InfoPackage by using the **Create InfoPackage** dialog box.</span></span> <span data-ttu-id="ec29f-183">이 대화 상자에 대한 자세한 내용은 [Create InfoPackage](create-infopackage.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ec29f-183">For more information about this dialog box, see [Create InfoPackage](create-infopackage.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ec29f-184">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ec29f-184">See Also</span></span>  
 <span data-ttu-id="ec29f-185">[SAP BW 대상 편집기&#40;매핑 페이지&#41;](sap-bw-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="ec29f-185">[SAP BW Destination Editor &#40;Mappings Page&#41;](sap-bw-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="ec29f-186">[SAP BW 대상 편집기&#40;오류 출력 페이지&#41;](sap-bw-destination-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="ec29f-186">[SAP BW Destination Editor &#40;Error Output Page&#41;](sap-bw-destination-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="ec29f-187">[SAP BW 대상 편집기&#40;고급 페이지&#41;](sap-bw-destination-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="ec29f-187">[SAP BW Destination Editor &#40;Advanced Page&#41;](sap-bw-destination-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="ec29f-188">Microsoft Connector 1.1 for SAP BW F1 도움말</span><span class="sxs-lookup"><span data-stu-id="ec29f-188">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
