---
title: 트랜잭션 데이터용 InfoSource 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ab5f23e2-cd4e-4507-83d9-ac5ef721c171
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3e3a60bb93da17e79087982473e92c35fa0856d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728556"
---
# <a name="create-infosource-for-transaction-data"></a><span data-ttu-id="17d5b-102">트랜잭션 데이터용 InfoSource 만들기</span><span class="sxs-lookup"><span data-stu-id="17d5b-102">Create InfoSource for Transaction Data</span></span>
  <span data-ttu-id="17d5b-103">**트랜잭션 데이터용 InfoSource 만들기** 대화 상자를 사용하여 SAP Netweaver BW 시스템에서 트랜잭션 데이터용으로 새 InfoSource를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-103">Use the **Create InfoSource for Transaction Data** dialog box to create a new InfoSource for transaction data in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="17d5b-104">**트랜잭션 데이터용 InfoSource 만들기** 대화 상자는 **SAP BW 대상 편집기** 의 **연결 관리자**페이지에서 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-104">You can open the **Create InfoSource for Transaction Data** dialog box from the **Connection Manager** page of the **SAP BW Destination Editor**.</span></span> <span data-ttu-id="17d5b-105">SAP BW 대상에 대한 자세한 내용은 [SAP BW Destination](sap-bw-destination.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17d5b-105">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="17d5b-106">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="17d5b-107">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="17d5b-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="17d5b-108">**트랜잭션 데이터용 InfoSource 만들기 대화 상자를 열려면**</span><span class="sxs-lookup"><span data-stu-id="17d5b-108">**To open the Create InfoSource for Transaction Data dialog box**</span></span>  
  
1.  <span data-ttu-id="17d5b-109">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 SAP BW 대상이 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="17d5b-110">**데이터 흐름** 탭에서 SAP BW 대상을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-110">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="17d5b-111">**SAP BW 대상 편집기**에서 **연결 관리자** 를 클릭하여 편집기의 **연결 관리자** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-111">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="17d5b-112">**연결 관리자** 페이지의 **SAP BW 개체 만들기** 그룹 상자에서 **InfoSource**를 선택한 다음 **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-112">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, select **InfoSource**, and then click **Create**.</span></span>  
  
5.  <span data-ttu-id="17d5b-113">**InfoSource 만들기** 대화 상자에서 **트랜잭션 데이터**를 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-113">In the **Create InfoSource** dialog box, select **Transaction data**, and then click **OK**.</span></span>  
  
## <a name="general-options"></a><span data-ttu-id="17d5b-114">일반 옵션</span><span class="sxs-lookup"><span data-stu-id="17d5b-114">General Options</span></span>  
 <span data-ttu-id="17d5b-115">**InfoSource 이름**</span><span class="sxs-lookup"><span data-stu-id="17d5b-115">**InfoSource name**</span></span>  
 <span data-ttu-id="17d5b-116">새 InfoSource의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-116">Enter a name for the new InfoSource.</span></span>  
  
 <span data-ttu-id="17d5b-117">**간단한 설명**</span><span class="sxs-lookup"><span data-stu-id="17d5b-117">**Short description**</span></span>  
 <span data-ttu-id="17d5b-118">새 InfoSource에 대한 간단한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-118">Enter a short description for the new InfoSource.</span></span>  
  
 <span data-ttu-id="17d5b-119">**자세한 설명**</span><span class="sxs-lookup"><span data-stu-id="17d5b-119">**Long description**</span></span>  
 <span data-ttu-id="17d5b-120">새 InfoSource에 대한 자세한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-120">Enter a long description for the new InfoSource.</span></span>  
  
 <span data-ttu-id="17d5b-121">**원본 시스템**</span><span class="sxs-lookup"><span data-stu-id="17d5b-121">**Source system**</span></span>  
 <span data-ttu-id="17d5b-122">InfoSource와 연결된 원본 시스템을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-122">Select the source system associated with the InfoSource.</span></span>  
  
 <span data-ttu-id="17d5b-123">**저장 및 활성화**</span><span class="sxs-lookup"><span data-stu-id="17d5b-123">**Save & Activate**</span></span>  
 <span data-ttu-id="17d5b-124">새 InfoSource를 저장하고 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-124">Save and activate the new InfoSource.</span></span>  
  
## <a name="infosource-transfer-structure-options"></a><span data-ttu-id="17d5b-125">InfoSource 전송 구조 옵션</span><span class="sxs-lookup"><span data-stu-id="17d5b-125">InfoSource Transfer Structure Options</span></span>  
 <span data-ttu-id="17d5b-126">InfoSource 전송 구조에서 데이터 흐름 열을 InfoSource에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-126">The InfoSource transfer structure lets you associate data flow columns to InfoSources.</span></span>  
  
 <span data-ttu-id="17d5b-127">**PipelineElement**</span><span class="sxs-lookup"><span data-stu-id="17d5b-127">**PipelineElement**</span></span>  
 <span data-ttu-id="17d5b-128">SAP BW 대상에 연결된 열을 데이터 흐름의 출력에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-128">Displays the column in the output of the data flow that is connected to the SAP BW destination.</span></span>  
  
 <span data-ttu-id="17d5b-129">**PipelineDataType**</span><span class="sxs-lookup"><span data-stu-id="17d5b-129">**PipelineDataType**</span></span>  
 <span data-ttu-id="17d5b-130">데이터 흐름 열의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 데이터 형식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-130">Displays the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type of the data flow column.</span></span>  
  
 <span data-ttu-id="17d5b-131">**Iobject - 검색**</span><span class="sxs-lookup"><span data-stu-id="17d5b-131">**Iobject - Search**</span></span>  
 <span data-ttu-id="17d5b-132">기존 InfoObject를 현재 행의 데이터 흐름 열에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-132">Associate an existing InfoObject to the data flow column in the current row.</span></span> <span data-ttu-id="17d5b-133">이 연결을 만들려면 **검색**을 클릭한 다음 **InfoObject 조회** 대화 상자를 사용하여 기존 InfoObject를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-133">To make this association, click **Search**, and then use the **Look Up InfoObject** dialog box to select the existing InfoObject.</span></span> <span data-ttu-id="17d5b-134">이 대화 상자에 대한 자세한 내용은 [Look Up InfoObject](look-up-infoobject.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="17d5b-134">For more information about this dialog box, see [Look Up InfoObject](look-up-infoobject.md).</span></span>  
  
 <span data-ttu-id="17d5b-135">기존 InfoObject를 선택한 후 **InfoObject** 및 **유형** 열이 선택한 값으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-135">After you select an existing InfoObject, the component populates the **InfoObject** and **Type** columns with the selected values.</span></span>  
  
 <span data-ttu-id="17d5b-136">**Iobject - 새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="17d5b-136">**Iobject - New**</span></span>  
 <span data-ttu-id="17d5b-137">새 InfoObject를 만들고 이 InfoObject를 현재 행의 데이터 흐름 열에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-137">Create a new InfoObject and associate this new InfoObect to the data flow column in the current row.</span></span> <span data-ttu-id="17d5b-138">새 InfoObject를 만들려면 **새로 만들기**를 클릭한 다음 **새 InfoObject 만들기** 대화 상자를 사용하여 InfoObject를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-138">To create the new InfoObject, click **New**, and then use the **Create New InfoObject** dialog box to create the InfoObject.</span></span> <span data-ttu-id="17d5b-139">이 대화 상자에 대한 자세한 내용은 [Create New InfoObject](create-new-infoobject.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="17d5b-139">For more information about this dialog box, see [Create New InfoObject](create-new-infoobject.md).</span></span>  
  
 <span data-ttu-id="17d5b-140">새 InfoObject를 만든 후 **InfoObject** 및 **유형** 열이 새 값으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-140">After you create a new InfoObject, the component populates the **InfoObject** and **Type** columns with the new values.</span></span>  
  
 <span data-ttu-id="17d5b-141">**Iobject - 제거**</span><span class="sxs-lookup"><span data-stu-id="17d5b-141">**Iobject - Remove**</span></span>  
 <span data-ttu-id="17d5b-142">InfoObject와 현재 행의 데이터 흐름 열 간의 연결을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-142">Remove the association between the InfoObject and the data flow column for the current row.</span></span> <span data-ttu-id="17d5b-143">이 연결을 제거하려면 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-143">To remove this association, click **Remove**.</span></span>  
  
 <span data-ttu-id="17d5b-144">**InfoObject**</span><span class="sxs-lookup"><span data-stu-id="17d5b-144">**InfoObject**</span></span>  
 <span data-ttu-id="17d5b-145">데이터 흐름 열과 연결된 InfoObject의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-145">Displays the name of the InfoObject that is associated with the data flow column.</span></span>  
  
 <span data-ttu-id="17d5b-146">**형식**</span><span class="sxs-lookup"><span data-stu-id="17d5b-146">**Type**</span></span>  
 <span data-ttu-id="17d5b-147">데이터 흐름 열과 연결된 InfoObject의 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-147">Displays the type of the InfoObject that is associated with the data flow column.</span></span> <span data-ttu-id="17d5b-148">다음 표에서는 유형에 사용할 수 있는 값을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-148">The following table lists the possible values for the type.</span></span>  
  
|<span data-ttu-id="17d5b-149">값</span><span class="sxs-lookup"><span data-stu-id="17d5b-149">Value</span></span>|<span data-ttu-id="17d5b-150">Description</span><span class="sxs-lookup"><span data-stu-id="17d5b-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="17d5b-151">CHA</span><span class="sxs-lookup"><span data-stu-id="17d5b-151">CHA</span></span>|<span data-ttu-id="17d5b-152">특징</span><span class="sxs-lookup"><span data-stu-id="17d5b-152">Characteristics</span></span>|  
|<span data-ttu-id="17d5b-153">UNI</span><span class="sxs-lookup"><span data-stu-id="17d5b-153">UNI</span></span>|<span data-ttu-id="17d5b-154">Units</span><span class="sxs-lookup"><span data-stu-id="17d5b-154">Units</span></span>|  
|<span data-ttu-id="17d5b-155">KYF</span><span class="sxs-lookup"><span data-stu-id="17d5b-155">KYF</span></span>|<span data-ttu-id="17d5b-156">주요 수치</span><span class="sxs-lookup"><span data-stu-id="17d5b-156">Key figures</span></span>|  
|<span data-ttu-id="17d5b-157">TIM</span><span class="sxs-lookup"><span data-stu-id="17d5b-157">TIM</span></span>|<span data-ttu-id="17d5b-158">시간 특징</span><span class="sxs-lookup"><span data-stu-id="17d5b-158">Time characteristics</span></span>|  
  
 <span data-ttu-id="17d5b-159">**단위 필드**</span><span class="sxs-lookup"><span data-stu-id="17d5b-159">**Unit Field**</span></span>  
 <span data-ttu-id="17d5b-160">InfoObject가 사용할 단위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17d5b-160">Specify the units that the InfoObject will use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17d5b-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="17d5b-161">See Also</span></span>  
 <span data-ttu-id="17d5b-162">[InfoSource 만들기](create-infosource.md) </span><span class="sxs-lookup"><span data-stu-id="17d5b-162">[Create InfoSource](create-infosource.md) </span></span>  
 [<span data-ttu-id="17d5b-163">Microsoft Connector 1.1 for SAP BW F1 도움말</span><span class="sxs-lookup"><span data-stu-id="17d5b-163">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
