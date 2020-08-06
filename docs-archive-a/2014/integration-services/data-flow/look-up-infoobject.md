---
title: InfoObject 조회 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e7f4c132-a5ec-49d8-a964-45775432731f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1616b4fcb368afc9e3f1157a3fc2511d4a7e8cce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731927"
---
# <a name="look-up-infoobject"></a><span data-ttu-id="84bd9-102">InfoObject 조회</span><span class="sxs-lookup"><span data-stu-id="84bd9-102">Look Up InfoObject</span></span>
  <span data-ttu-id="84bd9-103">**InfoObject 조회** 대화 상자에서는 SAP Netweaver BW 시스템에 정의된 InfoObject를 조회할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-103">Use the **Look Up InfoObject** dialog box to look up an InfoObject that is defined in the SAP Netweaver BW system.</span></span> <span data-ttu-id="84bd9-104">사용할 수 있는 InfoObject 목록이 표시될 때 원하는 InfoObject를 선택하면 관련 옵션이 SAP BW 대상의 값으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-104">When the list of available InfoObjects appears, select the InfoObject that you want, and the SAP BW destination will populate the associated options with the required values.</span></span>  
  
 <span data-ttu-id="84bd9-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW의 SAP BW 대상은 **InfoObject 조회** 대화 상자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-105">The SAP BW destination of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW uses the **Look Up InfoObject** dialog box.</span></span> <span data-ttu-id="84bd9-106">SAP BW 대상에 대한 자세한 내용은 [SAP BW Destination](sap-bw-destination.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="84bd9-106">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="84bd9-107">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-107">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="84bd9-108">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="84bd9-108">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="84bd9-109">**InfoObject 조회 대화 상자를 열려면**</span><span class="sxs-lookup"><span data-stu-id="84bd9-109">**To open the Look Up InfoObject dialog box**</span></span>  
  
1.  <span data-ttu-id="84bd9-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 SAP BW 대상이 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="84bd9-111">**데이터 흐름** 탭에서 SAP BW 대상을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-111">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="84bd9-112">**SAP BW 대상 편집기**에서 **연결 관리자** 를 클릭하여 편집기의 **연결 관리자** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-112">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="84bd9-113">**연결 관리자** 페이지의 **SAP BW 개체 만들기** 그룹 상자에서 다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-113">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, select one of the following options:</span></span>  
  
    1.  <span data-ttu-id="84bd9-114">**InfoCube**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-114">Select **InfoCube**.</span></span> <span data-ttu-id="84bd9-115">그런 다음 **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-115">Then, click **Create**.</span></span> <span data-ttu-id="84bd9-116">**트랜잭션 데이터용 InfoCube 만들기** 대화 상자에서 목록의 행 중 하나에 대해 **IObject** 열에서 **검색** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-116">In the **Create InfoCube for Transaction Data** dialog box, click **Search** in the **IObject** column for one of the rows in the list.</span></span> <span data-ttu-id="84bd9-117">각 행은 패키지의 데이터 흐름에 있는 열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-117">Each row represents a column in the data flow of the package.</span></span>  
  
    2.  <span data-ttu-id="84bd9-118">**InfoSource**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-118">Select **InfoSource**.</span></span> <span data-ttu-id="84bd9-119">그런 다음, **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-119">Then click **Create**.</span></span> <span data-ttu-id="84bd9-120">**InfoSource 만들기** 대화 상자에서 **트랜잭션 데이터**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-120">In the **Create InfoSource** dialog box, select **Transaction data**.</span></span> <span data-ttu-id="84bd9-121">**트랜잭션 데이터용 InfoSource 만들기** 대화 상자에서 목록의 행 중 하나에 대해 **IObject** 열에서 **검색** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-121">In the **Create InfoSource for Transaction Data** dialog box, click **Search** in the **IObject** column for one of the rows in the list.</span></span> <span data-ttu-id="84bd9-122">각 행은 패키지의 데이터 흐름에 있는 열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-122">Each row represents a column in the data flow of the package.</span></span>  
  
    3.  <span data-ttu-id="84bd9-123">**InfoSource**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-123">Select **InfoSource**.</span></span> <span data-ttu-id="84bd9-124">그런 다음, **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-124">Then click **Create**.</span></span> <span data-ttu-id="84bd9-125">**InfoSource 만들기** 대화 상자에서 **마스터 데이터**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-125">In the **Create InfoSource** dialog box, select **Master data**.</span></span> <span data-ttu-id="84bd9-126">**마스터 데이터용 InfoSource 만들기** 대화 상자에서 **조회**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-126">In the **Create InfoSource for Master Data** dialog box, click **Look up**.</span></span>  
  
 <span data-ttu-id="84bd9-127">**새 InfoObject 만들기** 대화 상자의 **특성** 섹션에서 **추가** 를 클릭하여 **InfoObject 조회** 대화 상자를 열 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-127">You can also open the **Look Up InfoObject** dialog box by clicking **Add** in the **Attributes** section of the **Create New InfoObject** dialog box.</span></span>  
  
## <a name="lookup-options"></a><span data-ttu-id="84bd9-128">조회 옵션</span><span class="sxs-lookup"><span data-stu-id="84bd9-128">Lookup Options</span></span>  
 <span data-ttu-id="84bd9-129">조회 필드 입력란에서 별표 와일드카드 문자(\*)를 사용하거나 문자열 일부를 별표 와일드카드 문자와 함께 사용하여 결과를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-129">In the lookup field text boxes, you can filter results by using the asterisk wildcard character (\*), or by using a partial string in combination with the asterisk wildcard character.</span></span> <span data-ttu-id="84bd9-130">조회 필드를 비워 두면 해당 필드에서 빈 문자열만 일치하는 항목으로 필터링됩니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-130">However, if you leave a lookup field empty, the lookup process will only match empty strings in that field.</span></span>  
  
 <span data-ttu-id="84bd9-131">**특성**</span><span class="sxs-lookup"><span data-stu-id="84bd9-131">**Characteristics**</span></span>  
 <span data-ttu-id="84bd9-132">특징을 나타내는 InfoObject를 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-132">Look up InfoObjects that represent characteristics.</span></span>  
  
 <span data-ttu-id="84bd9-133">**단위**</span><span class="sxs-lookup"><span data-stu-id="84bd9-133">**Units**</span></span>  
 <span data-ttu-id="84bd9-134">단위를 나타내는 InfoObject를 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-134">Look up InfoObjects that represent units.</span></span>  
  
 <span data-ttu-id="84bd9-135">**주요 수치**</span><span class="sxs-lookup"><span data-stu-id="84bd9-135">**Key figures**</span></span>  
 <span data-ttu-id="84bd9-136">주요 수치를 나타내는 InfoObject를 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-136">Look up InfoObjects that represent key figures.</span></span>  
  
 <span data-ttu-id="84bd9-137">**시간 특징**</span><span class="sxs-lookup"><span data-stu-id="84bd9-137">**Time characteristics**</span></span>  
 <span data-ttu-id="84bd9-138">시간 특징을 나타내는 InfoObject를 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-138">Look up InfoObjects that represent time characteristics.</span></span>  
  
 <span data-ttu-id="84bd9-139">**이름**</span><span class="sxs-lookup"><span data-stu-id="84bd9-139">**Name**</span></span>  
 <span data-ttu-id="84bd9-140">조회할 InfoObject의 이름을 입력하거나 이름의 일부와 별표 와일드카드 문자(\*)를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-140">Enter the name of the InfoObject that you want to look up, or a partial name with the asterisk wildcard character (\*).</span></span> <span data-ttu-id="84bd9-141">모든 InfoObject를 포함하려면 별표 와일드카드 문자만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-141">Or, use the asterisk wildcard character alone to include all InfoObjects.</span></span>  
  
 <span data-ttu-id="84bd9-142">**설명**</span><span class="sxs-lookup"><span data-stu-id="84bd9-142">**Description**</span></span>  
 <span data-ttu-id="84bd9-143">설명을 입력하거나 설명의 일부와 별표 와일드카드 문자(\*)를 함께 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-143">Enter the description, or a partial description with the asterisk wildcard character (\*).</span></span> <span data-ttu-id="84bd9-144">설명에 관계없이 모든 InfoObject를 포함하려면 별표 와일드카드 문자만 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-144">Or, use the asterisk wildcard character alone to include all InfoObjects regardless of description.</span></span>  
  
 <span data-ttu-id="84bd9-145">**조회**</span><span class="sxs-lookup"><span data-stu-id="84bd9-145">**Look up**</span></span>  
 <span data-ttu-id="84bd9-146">SAP Netweaver BW 시스템에 정의된 InfoObject 중 일치하는 InfoObject를 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-146">Look up matching InfoObjects that are defined in the SAP Netweaver BW system.</span></span>  
  
## <a name="lookup-results"></a><span data-ttu-id="84bd9-147">조회 결과</span><span class="sxs-lookup"><span data-stu-id="84bd9-147">Lookup Results</span></span>  
 <span data-ttu-id="84bd9-148">조회 단추를 클릭하면 SAP Netweaver BW 시스템의 InfoObject 목록이 다음 열 머리글과 함께 표에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-148">After you click the Look up button, a list of the InfoObjects in the SAP Netweaver BW system appears in a table with the following column headings.</span></span>  
  
 <span data-ttu-id="84bd9-149">**InfoObject**</span><span class="sxs-lookup"><span data-stu-id="84bd9-149">**InfoObject**</span></span>  
 <span data-ttu-id="84bd9-150">SAP Netweaver BW 시스템에 정의된 InfoObject의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-150">Displays the name of the InfoObject that is defined in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="84bd9-151">**짧은 텍스트**</span><span class="sxs-lookup"><span data-stu-id="84bd9-151">**Text (short)**</span></span>  
 <span data-ttu-id="84bd9-152">InfoObject와 연관된 짧은 텍스트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-152">Displays the short text that is associated with the InfoObject.</span></span>  
  
 <span data-ttu-id="84bd9-153">사용할 수 있는 InfoObject 목록이 표시될 때 원하는 InfoObject를 선택하면 관련 옵션이 대상의 값으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="84bd9-153">When the list of available InfoObjects appears, select the InfoObject that you want, and the destination will populate the associated options with the required values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84bd9-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="84bd9-154">See Also</span></span>  
 <span data-ttu-id="84bd9-155">[트랜잭션 데이터용 InfoCube 만들기](create-infocube-for-transaction-data.md) </span><span class="sxs-lookup"><span data-stu-id="84bd9-155">[Create InfoCube for Transaction Data](create-infocube-for-transaction-data.md) </span></span>  
 <span data-ttu-id="84bd9-156">[InfoSource 만들기](create-infosource.md) </span><span class="sxs-lookup"><span data-stu-id="84bd9-156">[Create InfoSource](create-infosource.md) </span></span>  
 <span data-ttu-id="84bd9-157">[트랜잭션 데이터용 InfoSource 만들기](create-infosource-for-transaction-data.md) </span><span class="sxs-lookup"><span data-stu-id="84bd9-157">[Create InfoSource for Transaction Data](create-infosource-for-transaction-data.md) </span></span>  
 <span data-ttu-id="84bd9-158">[마스터 데이터용 InfoSource 만들기](create-infosource-for-master-data.md) </span><span class="sxs-lookup"><span data-stu-id="84bd9-158">[Create InfoSource for Master Data](create-infosource-for-master-data.md) </span></span>  
 <span data-ttu-id="84bd9-159">[새 InfoObject 만들기](create-new-infoobject.md) </span><span class="sxs-lookup"><span data-stu-id="84bd9-159">[Create New InfoObject](create-new-infoobject.md) </span></span>  
 <span data-ttu-id="84bd9-160">[SAP BW 대상 편집기&#40;연결 관리자 페이지&#41;](sap-bw-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="84bd9-160">[SAP BW Destination Editor &#40;Connection Manager Page&#41;](sap-bw-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="84bd9-161">Microsoft Connector 1.1 for SAP BW F1 도움말</span><span class="sxs-lookup"><span data-stu-id="84bd9-161">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
