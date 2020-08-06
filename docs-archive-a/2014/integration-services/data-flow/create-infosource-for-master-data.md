---
title: 마스터 데이터용 InfoSource 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b52a9a89-8380-4a02-8a83-dcfb46ae860e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bb90bc5cf27f37dc89df236b765db98088a5804a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728564"
---
# <a name="create-infosource-for-master-data"></a><span data-ttu-id="c9580-102">마스터 데이터용 InfoSource 만들기</span><span class="sxs-lookup"><span data-stu-id="c9580-102">Create InfoSource for Master Data</span></span>
  <span data-ttu-id="c9580-103">**마스터 데이터용 InfoSource 만들기** 대화 상자에서는 SAP Netweaver BW 시스템의 마스터 데이터에 대한 새 InfoSource를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c9580-103">Use the **Create InfoSource for Master Data** dialog box to create a new InfoSource for master data in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="c9580-104">**SAP BW 대상 편집기** 의 **연결 관리자** 페이지에서 **마스터 데이터용 InfoSource 만들기**대화 상자를 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9580-104">You can open the **Create InfoSource for Master Data** dialog box from the **Connection Manager** page of the **SAP BW Destination Editor**.</span></span> <span data-ttu-id="c9580-105">SAP BW 대상에 대한 자세한 내용은 [SAP BW Destination](sap-bw-destination.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c9580-105">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c9580-106">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="c9580-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="c9580-107">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c9580-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="c9580-108">**마스터 데이터용 InfoSource 만들기 대화 상자를 열려면**</span><span class="sxs-lookup"><span data-stu-id="c9580-108">**To open the Create InfoSource for Master Data dialog box**</span></span>  
  
1.  <span data-ttu-id="c9580-109">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 SAP BW 대상이 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c9580-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="c9580-110">**데이터 흐름** 탭에서 SAP BW 대상을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c9580-110">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="c9580-111">**SAP BW 대상 편집기**에서 **연결 관리자** 를 클릭하여 편집기의 **연결 관리자** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c9580-111">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="c9580-112">**연결 관리자** 페이지의 **SAP BW 개체 만들기** 그룹 상자에서 **InfoSource**를 선택한 다음 **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c9580-112">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, select **InfoSource**, and then click **Create**.</span></span>  
  
5.  <span data-ttu-id="c9580-113">**InfoSource 만들기** 대화 상자에서 **마스터 데이터**를 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c9580-113">In the **Create InfoSource** dialog box, select **Master data**, and then click **OK**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c9580-114">옵션</span><span class="sxs-lookup"><span data-stu-id="c9580-114">Options</span></span>  
 <span data-ttu-id="c9580-115">**InfoObject 이름**</span><span class="sxs-lookup"><span data-stu-id="c9580-115">**InfoObject name**</span></span>  
 <span data-ttu-id="c9580-116">새 InfoSource의 기준으로 사용할 InfoObject 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c9580-116">Enter the name of the InfoObject on which the new InfoSource should be based.</span></span>  
  
 <span data-ttu-id="c9580-117">**조회**</span><span class="sxs-lookup"><span data-stu-id="c9580-117">**Look up**</span></span>  
 <span data-ttu-id="c9580-118">InfoObject를 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="c9580-118">Look up the InfoObject.</span></span> <span data-ttu-id="c9580-119">이 옵션을 선택하면 InfoObject를 선택할 수 있는 **InfoObject 조회** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="c9580-119">This option opens the **Look Up InfoObject** dialog box in which you can select the InfoObject.</span></span> <span data-ttu-id="c9580-120">이 대화 상자에 대한 자세한 내용은 [Look Up InfoObject](look-up-infoobject.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c9580-120">For more information about this dialog box, see [Look Up InfoObject](look-up-infoobject.md).</span></span>  
  
 <span data-ttu-id="c9580-121">InfoObject를 선택하면 선택한 InfoObject 이름으로 **InfoObject 이름** 입력란이 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="c9580-121">After you select an InfoObject, the component populates the **InfoObject name** text box with the name of the selected InfoObject.</span></span>  
  
 <span data-ttu-id="c9580-122">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="c9580-122">**New**</span></span>  
 <span data-ttu-id="c9580-123">새 InfoObject를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c9580-123">Create a new InfoObject.</span></span> <span data-ttu-id="c9580-124">이 옵션을 선택하면 새 InfoObject를 만들 수 있는 **새 InfoObject 만들기** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="c9580-124">This option opens the **Create New InfoObject** dialog box in which you can create the new InfoObject.</span></span> <span data-ttu-id="c9580-125">이 대화 상자에 대한 자세한 내용은 [Create New InfoObject](create-new-infoobject.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c9580-125">For more information about this dialog box, see [Create New InfoObject](create-new-infoobject.md).</span></span>  
  
 <span data-ttu-id="c9580-126">InfoObject를 만들면 새 InfoObject 이름으로 **InfoObject 이름** 입력란이 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="c9580-126">After you create an InfoObject, the component populates the **InfoObject name** text box with the name of the new InfoObject.</span></span>  
  
 <span data-ttu-id="c9580-127">**간단한 설명**</span><span class="sxs-lookup"><span data-stu-id="c9580-127">**Short description**</span></span>  
 <span data-ttu-id="c9580-128">새 InfoSource에 대한 간단한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c9580-128">Enter a short description for the new InfoSource.</span></span>  
  
 <span data-ttu-id="c9580-129">**자세한 설명**</span><span class="sxs-lookup"><span data-stu-id="c9580-129">**Long description**</span></span>  
 <span data-ttu-id="c9580-130">새 InfoSource에 대한 자세한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c9580-130">Enter a long description for the new InfoSource.</span></span>  
  
 <span data-ttu-id="c9580-131">**원본 시스템**</span><span class="sxs-lookup"><span data-stu-id="c9580-131">**Source system**</span></span>  
 <span data-ttu-id="c9580-132">새 InfoSource에 연결할 원본 시스템을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c9580-132">Select the source system to be associated with the new InfoSource.</span></span>  
  
 <span data-ttu-id="c9580-133">**애플리케이션**</span><span class="sxs-lookup"><span data-stu-id="c9580-133">**Application**</span></span>  
 <span data-ttu-id="c9580-134">새 InfoSource에 연결할 애플리케이션의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9580-134">Enter the name of the application to be associated with the new InfoSource.</span></span>  
  
 <span data-ttu-id="c9580-135">**특성**</span><span class="sxs-lookup"><span data-stu-id="c9580-135">**Attributes**</span></span>  
 <span data-ttu-id="c9580-136">마스터 데이터가 특성으로 구성되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c9580-136">Indicates that the master data consists of attributes.</span></span>  
  
 <span data-ttu-id="c9580-137">**텍스트**</span><span class="sxs-lookup"><span data-stu-id="c9580-137">**Texts**</span></span>  
 <span data-ttu-id="c9580-138">마스터 데이터가 특성으로 구성되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c9580-138">Indicates that the master data consists of attributes.</span></span>  
  
 <span data-ttu-id="c9580-139">**저장 및 활성화**</span><span class="sxs-lookup"><span data-stu-id="c9580-139">**Save & Activate**</span></span>  
 <span data-ttu-id="c9580-140">새 InfoSource를 저장하고 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="c9580-140">Save and activate the new InfoSource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9580-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c9580-141">See Also</span></span>  
 <span data-ttu-id="c9580-142">[InfoSource 만들기](create-infosource.md) </span><span class="sxs-lookup"><span data-stu-id="c9580-142">[Create InfoSource](create-infosource.md) </span></span>  
 [<span data-ttu-id="c9580-143">Microsoft Connector 1.1 for SAP BW F1 도움말</span><span class="sxs-lookup"><span data-stu-id="c9580-143">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
