---
title: 요청 로그 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 165d3833-0493-490c-9f63-8a134a7fafb8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 024012878ae94c5ba6276648e289e6e6f7c93d7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648454"
---
# <a name="request-log"></a><span data-ttu-id="9837e-102">요청 로그</span><span class="sxs-lookup"><span data-stu-id="9837e-102">Request Log</span></span>
  <span data-ttu-id="9837e-103">**요청 로그** 대화 상자를 사용하여 샘플 데이터에 대해 SAP Netweaver BW 시스템에 요청하는 동안 기록된 이벤트를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9837e-103">Use the **Request Log** dialog box to view the events that are logged during the request that is made to the SAP Netweaver BW system for sample data.</span></span> <span data-ttu-id="9837e-104">SAP BW 원본의 구성 문제를 해결해야 하는 경우 이 정보가 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9837e-104">This information can be useful if you have to troubleshoot your configuration of the SAP BW source.</span></span>  
  
 <span data-ttu-id="9837e-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW의 SAP BW 원본 구성 요소에 대한 자세한 내용은 [SAP BW 원본](sap-bw-source.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9837e-105">To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9837e-106">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="9837e-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="9837e-107">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9837e-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9837e-108">SAP Netweaver BW에서 데이터를 추출하려면 추가 SAP 라이선스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9837e-108">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="9837e-109">SAP에서 이러한 요구 사항을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="9837e-109">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="9837e-110">**요청 로그 대화 상자를 열려면**</span><span class="sxs-lookup"><span data-stu-id="9837e-110">**To open the Request Log dialog box**</span></span>  
  
1.  <span data-ttu-id="9837e-111">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 SAP BW 원본이 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9837e-111">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="9837e-112">**데이터 흐름** 탭에서 SAP BW 원본을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9837e-112">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="9837e-113">**SAP BW 원본 편집기**에서 **연결 관리자** 를 클릭하여 편집기의 **연결 관리자** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9837e-113">In the **SAP BW Source Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="9837e-114">SAP BW 원본을 구성한 후 **미리 보기** 를 클릭하여 **요청 로그** 대화 상자에서 이벤트를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="9837e-114">After you configure the SAP BW source, click **Preview** to preview the events in the **Request Log** dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9837e-115">**미리 보기** 를 클릭하면 **미리 보기** 대화 상자도 열립니다.</span><span class="sxs-lookup"><span data-stu-id="9837e-115">Clicking **Preview** also opens the **Preview** dialog box.</span></span> <span data-ttu-id="9837e-116">이 대화 상자에 대한 자세한 내용은 [Preview](preview.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9837e-116">For more information about this dialog box, see [Preview](preview.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="9837e-117">옵션</span><span class="sxs-lookup"><span data-stu-id="9837e-117">Options</span></span>  
 <span data-ttu-id="9837e-118">**Time**</span><span class="sxs-lookup"><span data-stu-id="9837e-118">**Time**</span></span>  
 <span data-ttu-id="9837e-119">이벤트가 기록된 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9837e-119">Displays the time that the event that was logged.</span></span>  
  
 <span data-ttu-id="9837e-120">**형식**</span><span class="sxs-lookup"><span data-stu-id="9837e-120">**Type**</span></span>  
 <span data-ttu-id="9837e-121">기록된 이벤트의 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9837e-121">Displays the type of the event that was logged.</span></span> <span data-ttu-id="9837e-122">다음 표에서는 가능한 이벤트 유형을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="9837e-122">The following table lists the possible event types.</span></span>  
  
|<span data-ttu-id="9837e-123">값</span><span class="sxs-lookup"><span data-stu-id="9837e-123">Value</span></span>|<span data-ttu-id="9837e-124">Description</span><span class="sxs-lookup"><span data-stu-id="9837e-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9837e-125">S</span><span class="sxs-lookup"><span data-stu-id="9837e-125">S</span></span>|<span data-ttu-id="9837e-126">성공 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="9837e-126">Success message.</span></span>|  
|<span data-ttu-id="9837e-127">E</span><span class="sxs-lookup"><span data-stu-id="9837e-127">E</span></span>|<span data-ttu-id="9837e-128">오류 메시지</span><span class="sxs-lookup"><span data-stu-id="9837e-128">Error message</span></span>|  
|<span data-ttu-id="9837e-129">W</span><span class="sxs-lookup"><span data-stu-id="9837e-129">W</span></span>|<span data-ttu-id="9837e-130">경고 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="9837e-130">Warning message.</span></span>|  
|<span data-ttu-id="9837e-131">I</span><span class="sxs-lookup"><span data-stu-id="9837e-131">I</span></span>|<span data-ttu-id="9837e-132">정보 메시지.</span><span class="sxs-lookup"><span data-stu-id="9837e-132">Informational message.</span></span>|  
|<span data-ttu-id="9837e-133">A</span><span class="sxs-lookup"><span data-stu-id="9837e-133">A</span></span>|<span data-ttu-id="9837e-134">작업이 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9837e-134">The operation was aborted.</span></span>|  
  
 <span data-ttu-id="9837e-135">**메시지**</span><span class="sxs-lookup"><span data-stu-id="9837e-135">**Message**</span></span>  
 <span data-ttu-id="9837e-136">기록된 이벤트와 관련된 메시지 텍스트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9837e-136">Displays the message text that is associated with the logged event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9837e-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9837e-137">See Also</span></span>  
 <span data-ttu-id="9837e-138">[SAP BW 원본 편집기&#40;연결 관리자 페이지&#41;](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="9837e-138">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="9837e-139">Microsoft Connector 1.1 for SAP BW F1 도움말</span><span class="sxs-lookup"><span data-stu-id="9837e-139">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
