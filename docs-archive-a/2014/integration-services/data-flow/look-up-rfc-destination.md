---
title: RFC 대상 조회 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: db9404d8-4c42-45e5-a100-c7a84b056109
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 397298fce16509e667aa4baccaee62c6ff0f5cca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741151"
---
# <a name="look-up-rfc-destination"></a><span data-ttu-id="61d00-102">RFC 대상 조회</span><span class="sxs-lookup"><span data-stu-id="61d00-102">Look Up RFC Destination</span></span>
  <span data-ttu-id="61d00-103">**RFC 대상 조회** 대화 상자에서는 SAP Netweaver BW 시스템에 정의된 RFC 대상을 조회할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61d00-103">Use the **Look Up RFC Destination** dialog box to look up an RFC destination that is defined in the SAP Netweaver BW system.</span></span> <span data-ttu-id="61d00-104">사용할 수 있는 RFC 대상 목록이 표시될 때 원하는 대상을 선택하면 관련 옵션이 필요한 값으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="61d00-104">When the list of available RFC destinations appears, select the destination that you want, and the component will populate the associated options with the required values.</span></span>  
  
 <span data-ttu-id="61d00-105">SAP BW 원본과 SAP BW 대상은 모두 **RFC 대상 조회** 대화 상자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="61d00-105">Both the SAP BW source and the SAP BW destination use the **Look Up RFC Destination** dialog box.</span></span> <span data-ttu-id="61d00-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW의 구성 요소에 대한 자세한 내용은 [SAP BW 원본](sap-bw-source.md) 및 [SAP BW 대상](sap-bw-destination.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="61d00-106">For more information about these components of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md) and [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="61d00-107">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="61d00-107">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="61d00-108">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="61d00-108">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="61d00-109">**RFC 대상 조회 대화 상자를 열려면**</span><span class="sxs-lookup"><span data-stu-id="61d00-109">**To open the Look Up RFC Destination dialog box**</span></span>  
  
1.  <span data-ttu-id="61d00-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 SAP BW 원본 또는 대상이 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="61d00-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source or destination.</span></span>  
  
2.  <span data-ttu-id="61d00-111">**데이터 흐름** 탭에서 SAP BW 원본 또는 대상을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="61d00-111">On the **Data Flow** tab, double-click the SAP BW source or destination.</span></span>  
  
3.  <span data-ttu-id="61d00-112">**SAP BW 원본 편집기** 또는 **SAP BW 대상 편집기**에서 **연결 관리자** 를 클릭하여 편집기의 **연결 관리자** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="61d00-112">In the **SAP BW Source Editor** or the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="61d00-113">**연결 관리자** 페이지의 **RFC 대상** 그룹 상자에서 **조회** 를 클릭하여 **RFC 대상 조회** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="61d00-113">On the **Connection Manager** page, in the **RFC Destination** group box, click **Look up** to display the **Look Up RFC Destination** dialog box.</span></span>  
  
     <span data-ttu-id="61d00-114">**SAP BW 원본 편집기**에서 **RFC 대상** 그룹 상자는 **실행 모드** 가 **P - 프로세스 체인 트리거** 또는 **W - 알릴 때까지 대기**인 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="61d00-114">In the **SAP BW Source Editor**, the **RFC Destination** group box appears only if the value for **Execution mode** is **P - Trigger process chain** or **W - Wait for notify**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="61d00-115">옵션</span><span class="sxs-lookup"><span data-stu-id="61d00-115">Options</span></span>  
 <span data-ttu-id="61d00-116">**대상**</span><span class="sxs-lookup"><span data-stu-id="61d00-116">**Destination**</span></span>  
 <span data-ttu-id="61d00-117">SAP Netweaver BW 시스템에 정의된 RFC 대상의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="61d00-117">View the name of the RFC destination that is defined in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="61d00-118">**게이트웨이 호스트**</span><span class="sxs-lookup"><span data-stu-id="61d00-118">**Gateway Host**</span></span>  
 <span data-ttu-id="61d00-119">게이트웨이 호스트의 서버 이름 또는 IP 주소를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="61d00-119">View the server name or IP address of the gateway host.</span></span> <span data-ttu-id="61d00-120">일반적으로 이름 또는 IP 주소는 SAP 애플리케이션 서버와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="61d00-120">Usually, the name or IP address is the same as the SAP application server.</span></span>  
  
 <span data-ttu-id="61d00-121">**게이트웨이 서비스**</span><span class="sxs-lookup"><span data-stu-id="61d00-121">**Gateway Service**</span></span>  
 <span data-ttu-id="61d00-122">게이트웨이 서비스 이름을 `sapgwNN` 형식으로 봅니다. 여기서 `NN`은 시스템 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="61d00-122">View the name of the gateway service, in the format `sapgwNN`, where `NN` is the system number.</span></span>  
  
 <span data-ttu-id="61d00-123">**프로그램 ID**</span><span class="sxs-lookup"><span data-stu-id="61d00-123">**Program ID**</span></span>  
 <span data-ttu-id="61d00-124">RFC 대상과 연결된 프로그램 ID를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="61d00-124">View the Program ID that is associated with the RFC destination.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61d00-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="61d00-125">See Also</span></span>  
 <span data-ttu-id="61d00-126">[SAP BW 원본 편집기&#40;연결 관리자 페이지&#41;](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="61d00-126">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="61d00-127">[SAP BW 대상 편집기&#40;연결 관리자 페이지&#41;](sap-bw-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="61d00-127">[SAP BW Destination Editor &#40;Connection Manager Page&#41;](sap-bw-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="61d00-128">Microsoft Connector 1.1 for SAP BW F1 도움말</span><span class="sxs-lookup"><span data-stu-id="61d00-128">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
