---
title: InfoPackage 조회 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7c0cb7a4-cd07-44cc-85cb-eb1ad91f85fd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1e45477e8faeed07faa114850e10a3bc4bbcf170
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731924"
---
# <a name="look-up-infopackage"></a><span data-ttu-id="8214d-102">InfoPackage 조회</span><span class="sxs-lookup"><span data-stu-id="8214d-102">Look Up InfoPackage</span></span>
  <span data-ttu-id="8214d-103">**InfoPackage 조회** 대화 상자에서는 SAP Netweaver BW 시스템에 정의된 InfoPackage를 조회할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-103">Use the **Look Up InfoPackage** dialog box to look up an InfoPackage that is defined in the SAP Netweaver BW system.</span></span> <span data-ttu-id="8214d-104">InfoPackage 목록이 표시될 때 원하는 InfoPackage를 선택하면 관련 옵션이 대상의 값으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-104">When the list of InfoPackages appears, select the InfoPackage that you want, and the destination will populate the associated options with the required values.</span></span>  
  
 <span data-ttu-id="8214d-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW의 SAP BW 대상은 **프로세스 체인 조회** 대화 상자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-105">The SAP BW destination of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW uses the **Look Up Process Chain** dialog box.</span></span> <span data-ttu-id="8214d-106">SAP BW 대상에 대한 자세한 내용은 [SAP BW Destination](sap-bw-destination.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8214d-106">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8214d-107">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-107">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="8214d-108">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8214d-108">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="8214d-109">**InfoPackage 조회 대화 상자를 열려면**</span><span class="sxs-lookup"><span data-stu-id="8214d-109">**To open the Look Up InfoPackage dialog box**</span></span>  
  
1.  <span data-ttu-id="8214d-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 SAP BW 대상이 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="8214d-111">**데이터 흐름** 탭에서 SAP BW 대상을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-111">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="8214d-112">**SAP BW 대상 편집기**에서 **연결 관리자** 를 클릭하여 편집기의 **연결 관리자** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-112">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="8214d-113">**연결 관리자** 페이지의 **InfoPackage/InfoSource** 그룹 상자에서 **조회** 를 클릭하여 **InfoPackage 조회** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-113">On the **Connection Manager** page, in the **InfoPackage/InfoSource** group box, click **Look up** to display the **Look Up InfoPackage** dialog box.</span></span>  
  
## <a name="lookup-options"></a><span data-ttu-id="8214d-114">조회 옵션</span><span class="sxs-lookup"><span data-stu-id="8214d-114">Lookup Options</span></span>  
 <span data-ttu-id="8214d-115">조회 필드에 별표 와일드카드 문자(\*)를 사용하거나 문자열 일부를 별표 와일드카드 문자와 함께 사용하여 결과를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-115">In the lookup fields, you can filter results by using the asterisk wildcard character (\*), or by using a partial string in combination with the asterisk wildcard character.</span></span> <span data-ttu-id="8214d-116">조회 필드를 비워 두면 해당 필드에서 빈 문자열만 일치하는 항목으로 필터링됩니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-116">However, if you leave a lookup field empty, the lookup operation will only match empty strings in that field.</span></span>  
  
 <span data-ttu-id="8214d-117">**InfoPackage**</span><span class="sxs-lookup"><span data-stu-id="8214d-117">**InfoPackage**</span></span>  
 <span data-ttu-id="8214d-118">조회할 InfoPackage의 이름을 입력하거나 이름의 일부와 별표 와일드카드 문자(\*)를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-118">Enter the name of the InfoPackage that you want to look up, or a partial name with the asterisk wildcard character (\*).</span></span> <span data-ttu-id="8214d-119">모든 InfoPackage를 포함하려면 별표 와일드카드 문자만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-119">Or, use the asterisk wildcard character alone to include all InfoPackages.</span></span>  
  
 <span data-ttu-id="8214d-120">**InfoSource**</span><span class="sxs-lookup"><span data-stu-id="8214d-120">**InfoSource**</span></span>  
 <span data-ttu-id="8214d-121">InfoSource의 이름을 입력하거나 이름의 일부와 별표 와일드카드 문자(\*)를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-121">Enter the name of the InfoSource, or a partial name with the asterisk wildcard character (\*).</span></span> <span data-ttu-id="8214d-122">InfoSource에 관계없이 모든 InfoPackage를 포함하려면 별표 와일드카드 문자만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-122">Or, use the asterisk wildcard character alone to include all InfoPackages regardless of InfoSource.</span></span>  
  
 <span data-ttu-id="8214d-123">**원본 시스템**</span><span class="sxs-lookup"><span data-stu-id="8214d-123">**Source system**</span></span>  
 <span data-ttu-id="8214d-124">원본 시스템의 이름을 입력하거나 이름의 일부와 별표 와일드카드 문자(\*)를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-124">Enter the name of the source system, or a partial name with the asterisk wildcard character (\*).</span></span> <span data-ttu-id="8214d-125">원본 시스템에 관계없이 모든 InfoPackage를 포함하려면 별표 와일드카드 문자만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-125">Or, use the asterisk wildcard character alone to include all InfoPackages regardless of source systems.</span></span>  
  
 <span data-ttu-id="8214d-126">**조회**</span><span class="sxs-lookup"><span data-stu-id="8214d-126">**Look up**</span></span>  
 <span data-ttu-id="8214d-127">SAP Netweaver BW 시스템에 정의된 InfoPackage 중 일치하는 InfoPackage를 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-127">Look up matching InfoPackages that are defined in the SAP Netweaver BW system.</span></span>  
  
## <a name="lookup-results"></a><span data-ttu-id="8214d-128">조회 결과</span><span class="sxs-lookup"><span data-stu-id="8214d-128">Lookup Results</span></span>  
 <span data-ttu-id="8214d-129">조회 단추를 클릭하면 SAP Netweaver BW 시스템의 InfoPackage 목록이 다음 열 머리글과 함께 표에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-129">After you click the Look up button, a list of the InfoPackages in the SAP Netweaver BW system appears in a table with the following column headings.</span></span>  
  
 <span data-ttu-id="8214d-130">**InfoPackage**</span><span class="sxs-lookup"><span data-stu-id="8214d-130">**InfoPackage**</span></span>  
 <span data-ttu-id="8214d-131">SAP Netweaver BW 시스템에 정의된 InfoPackage의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-131">Displays the name of the InfoPackage that is defined in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="8214d-132">**형식**</span><span class="sxs-lookup"><span data-stu-id="8214d-132">**Type**</span></span>  
 <span data-ttu-id="8214d-133">InfoPackage의 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-133">Displays the type of the InfoPackage.</span></span> <span data-ttu-id="8214d-134">다음 표에서는 유형에 사용할 수 있는 값을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-134">The following table lists the possible values for the type.</span></span>  
  
|<span data-ttu-id="8214d-135">값</span><span class="sxs-lookup"><span data-stu-id="8214d-135">Value</span></span>|<span data-ttu-id="8214d-136">Description</span><span class="sxs-lookup"><span data-stu-id="8214d-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8214d-137">Trans.</span><span class="sxs-lookup"><span data-stu-id="8214d-137">Trans.</span></span>|<span data-ttu-id="8214d-138">트랜잭션 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-138">Transaction data.</span></span>|  
|<span data-ttu-id="8214d-139">Attr.</span><span class="sxs-lookup"><span data-stu-id="8214d-139">Attr.</span></span>|<span data-ttu-id="8214d-140">특성 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-140">Attribute data.</span></span>|  
|<span data-ttu-id="8214d-141">텍스트</span><span class="sxs-lookup"><span data-stu-id="8214d-141">Texts</span></span>|<span data-ttu-id="8214d-142">텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-142">Texts.</span></span>|  
  
 <span data-ttu-id="8214d-143">**설명**</span><span class="sxs-lookup"><span data-stu-id="8214d-143">**Description**</span></span>  
 <span data-ttu-id="8214d-144">InfoPackage에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-144">Displays the description of the InfoPackage.</span></span>  
  
 <span data-ttu-id="8214d-145">**InfoSource**</span><span class="sxs-lookup"><span data-stu-id="8214d-145">**InfoSource**</span></span>  
 <span data-ttu-id="8214d-146">InfoPackage와 연결된 InfoSource의 이름을 표시합니다(있는 경우).</span><span class="sxs-lookup"><span data-stu-id="8214d-146">Displays the name of the InfoSource, if any, that is associated with the InfoPackage.</span></span>  
  
 <span data-ttu-id="8214d-147">**Source System**</span><span class="sxs-lookup"><span data-stu-id="8214d-147">**Source System**</span></span>  
 <span data-ttu-id="8214d-148">원본 시스템의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-148">Displays the name of the source system.</span></span>  
  
 <span data-ttu-id="8214d-149">InfoPackage 목록이 표시될 때 원하는 InfoPackage를 선택하면 관련 옵션이 대상의 값으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="8214d-149">When the list of InfoPackages appears, select the InfoPackage that you want, and the destination will populate the associated options with the required values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8214d-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8214d-150">See Also</span></span>  
 <span data-ttu-id="8214d-151">[SAP BW 대상 편집기&#40;연결 관리자 페이지&#41;](sap-bw-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="8214d-151">[SAP BW Destination Editor &#40;Connection Manager Page&#41;](sap-bw-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="8214d-152">Microsoft Connector 1.1 for SAP BW F1 도움말</span><span class="sxs-lookup"><span data-stu-id="8214d-152">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
