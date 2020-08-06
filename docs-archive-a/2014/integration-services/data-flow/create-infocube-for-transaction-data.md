---
title: 트랜잭션 데이터용 InfoCube 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 673cea01-a260-4fce-a1a0-f73839289805
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a20fe051cfdd3e6afe285279996fcf696a83c21b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728572"
---
# <a name="create-infocube-for-transaction-data"></a><span data-ttu-id="9ff66-102">트랜잭션 데이터용 InfoCube 만들기</span><span class="sxs-lookup"><span data-stu-id="9ff66-102">Create InfoCube for Transaction Data</span></span>
  <span data-ttu-id="9ff66-103">**트랜잭션 데이터용 InfoCube 만들기** 대화 상자를 사용하여 SAP Netweaver BW 시스템에서 트랜잭션 데이터용으로 새 InfoCube를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff66-103">Use the **Create InfoCube for Transaction Data** dialog box to create a new InfoCube for transaction data in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="9ff66-104">**SAP BW 대상 편집기** 의 **연결 관리자** 페이지에서 **트랜잭션 데이터용 InfoCube 만들기**대화 상자를 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff66-104">You can open the **Create InfoCube for Transaction Data** dialog box from the **Connection Manager** page of the **SAP BW Destination Editor**.</span></span> <span data-ttu-id="9ff66-105">SAP BW 대상에 대한 자세한 내용은 [SAP BW Destination](sap-bw-destination.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9ff66-105">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9ff66-106">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff66-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="9ff66-107">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9ff66-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="9ff66-108">**트랜잭션 데이터용 InfoCube 만들기 대화 상자를 열려면**</span><span class="sxs-lookup"><span data-stu-id="9ff66-108">**To open the Create InfoCube for Transaction Data dialog box**</span></span>  
  
1.  <span data-ttu-id="9ff66-109">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 SAP BW 대상이 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9ff66-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="9ff66-110">**데이터 흐름** 탭에서 SAP BW 대상을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff66-110">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="9ff66-111">**SAP BW 대상 편집기**에서 **연결 관리자** 를 클릭하여 편집기의 **연결 관리자** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9ff66-111">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="9ff66-112">**연결 관리자** 페이지의 **SAP BW 개체 만들기** 그룹 상자에서 **InfoCube**를 선택한 다음 **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff66-112">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, select **InfoCube**, and then click **Create**.</span></span>  
  
## <a name="general-options"></a><span data-ttu-id="9ff66-113">일반 옵션</span><span class="sxs-lookup"><span data-stu-id="9ff66-113">General Options</span></span>  
 <span data-ttu-id="9ff66-114">**InfoCube 이름**</span><span class="sxs-lookup"><span data-stu-id="9ff66-114">**InfoCube name**</span></span>  
 <span data-ttu-id="9ff66-115">새 InfoCube의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff66-115">Enter a name for the new InfoCube.</span></span>  
  
 <span data-ttu-id="9ff66-116">**자세한 설명**</span><span class="sxs-lookup"><span data-stu-id="9ff66-116">**Long description**</span></span>  
 <span data-ttu-id="9ff66-117">새 InfoCube에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff66-117">Enter a description for the new InfoCube.</span></span>  
  
 <span data-ttu-id="9ff66-118">**저장 및 활성화**</span><span class="sxs-lookup"><span data-stu-id="9ff66-118">**Save & Activate**</span></span>  
 <span data-ttu-id="9ff66-119">새 InfoCube를 저장하고 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff66-119">Save and activate the new InfoCube.</span></span>  
  
## <a name="infocube-transfer-structure-options"></a><span data-ttu-id="9ff66-120">InfoCube 전송 구조 옵션</span><span class="sxs-lookup"><span data-stu-id="9ff66-120">InfoCube Transfer Structure Options</span></span>  
 <span data-ttu-id="9ff66-121">InfoCube 전송 구조 섹션에서 데이터 흐름 열을 InfoObject에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff66-121">The InfoCube transfer structure section lets you associate data flow columns to InfoObjects.</span></span>  
  
 <span data-ttu-id="9ff66-122">**PipelineElement**</span><span class="sxs-lookup"><span data-stu-id="9ff66-122">**PipelineElement**</span></span>  
 <span data-ttu-id="9ff66-123">SAP BW 대상에 연결된 열을 데이터 흐름의 출력에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff66-123">Displays the column in the output of the data flow that is connected to the SAP BW destination.</span></span>  
  
 <span data-ttu-id="9ff66-124">**PipelineDataType**</span><span class="sxs-lookup"><span data-stu-id="9ff66-124">**PipelineDataType**</span></span>  
 <span data-ttu-id="9ff66-125">데이터 흐름 열의 데이터 형식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff66-125">Displays the data type of the data flow column.</span></span>  
  
 <span data-ttu-id="9ff66-126">**InfoObject**</span><span class="sxs-lookup"><span data-stu-id="9ff66-126">**InfoObject**</span></span>  
 <span data-ttu-id="9ff66-127">데이터 흐름 열과 연결된 InfoObject의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff66-127">Displays the name of the InfoObject that is associated with the data flow column.</span></span>  
  
 <span data-ttu-id="9ff66-128">**형식**</span><span class="sxs-lookup"><span data-stu-id="9ff66-128">**Type**</span></span>  
 <span data-ttu-id="9ff66-129">데이터 흐름 열과 연결된 InfoObject의 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff66-129">Displays the type of the InfoObject that is associated with the data flow column.</span></span> <span data-ttu-id="9ff66-130">다음 표에서는 유형에 사용할 수 있는 값을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff66-130">The following table lists the possible values for the type.</span></span>  
  
|<span data-ttu-id="9ff66-131">값</span><span class="sxs-lookup"><span data-stu-id="9ff66-131">Value</span></span>|<span data-ttu-id="9ff66-132">Description</span><span class="sxs-lookup"><span data-stu-id="9ff66-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9ff66-133">CHA</span><span class="sxs-lookup"><span data-stu-id="9ff66-133">CHA</span></span>|<span data-ttu-id="9ff66-134">특징</span><span class="sxs-lookup"><span data-stu-id="9ff66-134">Characteristics</span></span>|  
|<span data-ttu-id="9ff66-135">UNI</span><span class="sxs-lookup"><span data-stu-id="9ff66-135">UNI</span></span>|<span data-ttu-id="9ff66-136">Units</span><span class="sxs-lookup"><span data-stu-id="9ff66-136">Units</span></span>|  
|<span data-ttu-id="9ff66-137">KYF</span><span class="sxs-lookup"><span data-stu-id="9ff66-137">KYF</span></span>|<span data-ttu-id="9ff66-138">주요 수치</span><span class="sxs-lookup"><span data-stu-id="9ff66-138">Key figures</span></span>|  
|<span data-ttu-id="9ff66-139">TIM</span><span class="sxs-lookup"><span data-stu-id="9ff66-139">TIM</span></span>|<span data-ttu-id="9ff66-140">시간 특징</span><span class="sxs-lookup"><span data-stu-id="9ff66-140">Time characteristics</span></span>|  
  
 <span data-ttu-id="9ff66-141">**Iobject - 검색**</span><span class="sxs-lookup"><span data-stu-id="9ff66-141">**Iobject - Search**</span></span>  
 <span data-ttu-id="9ff66-142">기존 InfoObject를 현재 행의 데이터 흐름 열에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff66-142">Associate an existing InfoObject to the data flow column for the current row.</span></span> <span data-ttu-id="9ff66-143">이 연결을 만들려면 **검색**을 클릭한 다음 **InfoObject 조회** 대화 상자를 사용하여 기존 InfoObject를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff66-143">To make this association, click **Search**, and then use the **Look Up InfoObject** dialog box to select the existing InfoObject.</span></span> <span data-ttu-id="9ff66-144">이 대화 상자에 대한 자세한 내용은 [Look Up InfoObject](look-up-infoobject.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9ff66-144">For more information about this dialog box, see [Look Up InfoObject](look-up-infoobject.md).</span></span>  
  
 <span data-ttu-id="9ff66-145">기존 InfoObject를 선택한 후 **InfoObject** 및 **유형** 열이 선택한 값으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="9ff66-145">After you select an existing InfoObject, the component populates the **InfoObject** and **Type** columns with the selected values.</span></span>  
  
 <span data-ttu-id="9ff66-146">**Iobject - 새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="9ff66-146">**Iobject - New**</span></span>  
 <span data-ttu-id="9ff66-147">새 InfoObject를 만들고 이 InfoObject를 현재 행의 데이터 흐름 열에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff66-147">Create a new InfoObject and associate this new InfoObject to the data flow column in the current row.</span></span> <span data-ttu-id="9ff66-148">새 InfoObject를 만들려면 **새로 만들기**를 클릭한 다음 **새 InfoObject 만들기** 대화 상자를 사용하여 InfoObject를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9ff66-148">To create the new InfoObject, click **New**, and then use the **Create New InfoObject** dialog box to create the InfoObject.</span></span> <span data-ttu-id="9ff66-149">이 대화 상자에 대한 자세한 내용은 [Create New InfoObject](create-new-infoobject.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9ff66-149">For more information about this dialog box, see [Create New InfoObject](create-new-infoobject.md).</span></span>  
  
 <span data-ttu-id="9ff66-150">새 InfoObject를 만든 후 **InfoObject** 및 **유형** 열이 새 값으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="9ff66-150">After you create a new InfoObject, the component populates the **InfoObject** and **Type** columns with the new values.</span></span>  
  
 <span data-ttu-id="9ff66-151">**Iobject - 제거**</span><span class="sxs-lookup"><span data-stu-id="9ff66-151">**Iobject - Remove**</span></span>  
 <span data-ttu-id="9ff66-152">InfoObject와 현재 행의 데이터 흐름 열 간의 연결을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff66-152">Remove the association between the InfoObject and the data flow column for the current row.</span></span> <span data-ttu-id="9ff66-153">이 연결을 제거하려면 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff66-153">To remove this association, click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ff66-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9ff66-154">See Also</span></span>  
 [<span data-ttu-id="9ff66-155">Microsoft Connector 1.1 for SAP BW F1 도움말</span><span class="sxs-lookup"><span data-stu-id="9ff66-155">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
