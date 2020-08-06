---
title: 프로세스 체인 조회 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f6303ea4-fbbf-4cba-bc60-828df62be8c2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2e0d3743071d018a8a82f60eeaf04fd86dec3e63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731923"
---
# <a name="look-up-process-chain"></a><span data-ttu-id="8108f-102">프로세스 체인 조회</span><span class="sxs-lookup"><span data-stu-id="8108f-102">Look Up Process Chain</span></span>
  <span data-ttu-id="8108f-103">**프로세스 체인 조회** 대화 상자에서는 SAP Netweaver BW 시스템에 정의된 프로세스 체인을 조회할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8108f-103">Use the **Look Up Process Chain** dialog box to look up a process chain that is defined in the SAP Netweaver BW system.</span></span> <span data-ttu-id="8108f-104">사용할 수 있는 프로세스 체인 목록이 표시될 때 원하는 체인을 선택하면 관련 옵션이 원본의 값으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="8108f-104">When the list of available process chains appears, select the chain that you want, and the source will populate the associated options with the required values.</span></span>  
  
 <span data-ttu-id="8108f-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW의 SAP BW 원본은 **프로세스 체인 조회** 대화 상자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8108f-105">The SAP BW source of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW uses the **Look Up Process Chain** dialog box.</span></span> <span data-ttu-id="8108f-106">SAP BW 원본에 대한 자세한 내용은 [SAP BW Source](sap-bw-source.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8108f-106">To learn more about the SAP BW source, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8108f-107">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="8108f-107">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="8108f-108">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8108f-108">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="8108f-109">**프로세스 체인 조회 대화 상자를 열려면**</span><span class="sxs-lookup"><span data-stu-id="8108f-109">**To open the Look Up Process Chain dialog box**</span></span>  
  
1.  <span data-ttu-id="8108f-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 SAP BW 원본이 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8108f-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="8108f-111">**데이터 흐름** 탭에서 SAP BW 원본을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8108f-111">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="8108f-112">**SAP BW 원본 편집기**에서 **연결 관리자** 를 클릭하여 편집기의 **연결 관리자** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8108f-112">In the **SAP BW Source Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="8108f-113">**프로세스 체인** 그룹 상자에서 **조회** 를 클릭하여 **프로세스 체인 조회** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8108f-113">In the **Process Chain** group box, click **Look up** to display the **Look Up Process Chain** dialog box.</span></span>  
  
     <span data-ttu-id="8108f-114">**프로세스 체인** 그룹 상자는 **실행 모드** 의 값이 **P - 프로세스 체인 트리거**인 경우에만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8108f-114">The **Process Chain** group box appears only if the value for **Execution mode** is **P - Trigger process chain**.</span></span>  
  
## <a name="lookup-options"></a><span data-ttu-id="8108f-115">조회 옵션</span><span class="sxs-lookup"><span data-stu-id="8108f-115">Lookup Options</span></span>  
 <span data-ttu-id="8108f-116">조회 필드에 별표 와일드카드 문자(\*)를 사용하거나 문자열 일부를 별표 와일드카드 문자와 함께 사용하여 결과를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8108f-116">In the lookup fields, you can filter results by using the asterisk wildcard character (\*), or by using a partial string in combination with the asterisk wildcard character.</span></span> <span data-ttu-id="8108f-117">조회 필드를 비워 두면 해당 필드에서 빈 문자열만 일치하는 항목으로 필터링됩니다.</span><span class="sxs-lookup"><span data-stu-id="8108f-117">However, if you leave a lookup field empty, the lookup operation will only match empty strings in that field.</span></span>  
  
 <span data-ttu-id="8108f-118">**프로세스 체인**</span><span class="sxs-lookup"><span data-stu-id="8108f-118">**Process chain**</span></span>  
 <span data-ttu-id="8108f-119">조회할 프로세스 체인의 이름을 입력하거나 이름의 일부와 별표 와일드카드 문자(\*)를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8108f-119">Enter the name of the process chain that you want to look up, or enter a partial name with the asterisk wildcard character (\*).</span></span> <span data-ttu-id="8108f-120">모든 프로세스 체인을 포함하려면 별표 와일드카드 문자만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8108f-120">Or, use the asterisk wildcard character alone to include all process chains.</span></span>  
  
 <span data-ttu-id="8108f-121">**조회**</span><span class="sxs-lookup"><span data-stu-id="8108f-121">**Look up**</span></span>  
 <span data-ttu-id="8108f-122">SAP Netweaver BW 시스템에 정의된 프로세스 체인 중 일치하는 프로세스 체인을 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="8108f-122">Look up matching process chains that are defined in the SAP Netweaver BW system.</span></span>  
  
## <a name="lookup-results"></a><span data-ttu-id="8108f-123">조회 결과</span><span class="sxs-lookup"><span data-stu-id="8108f-123">Lookup Results</span></span>  
 <span data-ttu-id="8108f-124">조회 단추를 클릭하면 SAP Netweaver BW 시스템의 프로세스 체인 목록이 다음 열 머리글과 함께 표에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8108f-124">After you click the Look up button, a list of the process chains in the SAP Netweaver BW system appears in a table with the following column headings:</span></span>  
  
 <span data-ttu-id="8108f-125">**프로세스 체인**</span><span class="sxs-lookup"><span data-stu-id="8108f-125">**Process Chain**</span></span>  
 <span data-ttu-id="8108f-126">SAP Netweaver BW 시스템에 정의된 프로세스 체인의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8108f-126">Displays the name of the process chain that is defined in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="8108f-127">**설명**</span><span class="sxs-lookup"><span data-stu-id="8108f-127">**Description**</span></span>  
 <span data-ttu-id="8108f-128">프로세스 체인에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8108f-128">Displays the description of the process chain.</span></span>  
  
 <span data-ttu-id="8108f-129">사용할 수 있는 프로세스 체인 목록이 표시될 때 원하는 체인을 선택하면 관련 옵션이 원본의 값으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="8108f-129">When the list of available process chains appears, select the chain that you want, and the source will populate the associated options with the required values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8108f-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8108f-130">See Also</span></span>  
 <span data-ttu-id="8108f-131">[SAP BW 원본 편집기&#40;연결 관리자 페이지&#41;](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="8108f-131">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="8108f-132">Microsoft Connector 1.1 for SAP BW F1 도움말</span><span class="sxs-lookup"><span data-stu-id="8108f-132">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
