---
title: SAP BW 대상 편집기(고급 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 862957db-bbc6-4dda-bc0e-591457f1baa7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0c5ca943b804ad39cc391cb1cf7f06e056ddbe56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651813"
---
# <a name="sap-bw-destination-editor-advanced-page"></a><span data-ttu-id="49b80-102">SAP BW 대상 편집기(고급 페이지)</span><span class="sxs-lookup"><span data-stu-id="49b80-102">SAP BW Destination Editor (Advanced Page)</span></span>
  <span data-ttu-id="49b80-103">**SAP BW 대상 편집기** 의 **고급** 페이지를 사용하여 패키지 크기 및 제한 시간 정보와 같은 고급 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49b80-103">Use the **Advanced** page of the **SAP BW Destination Editor** to set advanced settings such as package size and time-out information.</span></span>  
  
 <span data-ttu-id="49b80-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW의 SAP BW 대상에 대한 자세한 내용은 [SAP BW 대상](sap-bw-destination.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="49b80-104">To learn more about the SAP BW destination of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="49b80-105">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="49b80-105">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="49b80-106">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="49b80-106">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="49b80-107">**고급 페이지를 열려면**</span><span class="sxs-lookup"><span data-stu-id="49b80-107">**To open the Advanced page**</span></span>  
  
1.  <span data-ttu-id="49b80-108">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 SAP BW 대상이 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="49b80-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="49b80-109">**데이터 흐름** 탭에서 SAP BW 대상을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49b80-109">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="49b80-110">**SAP BW 대상 편집기**에서 **고급** 을 클릭하여 편집기의 **고급** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="49b80-110">In the **SAP BW Destination Editor**, click **Advanced** to open the **Advanced** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="49b80-111">옵션</span><span class="sxs-lookup"><span data-stu-id="49b80-111">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="49b80-112">대상을 구성하는 데 필요한 값 중 모르는 것이 있으면 SAP 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="49b80-112">If you do not know all the values that are required to configure the destination, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="49b80-113">**패키지 크기**</span><span class="sxs-lookup"><span data-stu-id="49b80-113">**Package size**</span></span>  
 <span data-ttu-id="49b80-114">한 번에 전송될 데이터 행 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="49b80-114">Specify how many rows of data will be transferred at a time.</span></span> <span data-ttu-id="49b80-115">이 매개 변수에 대한 최적의 값은 SAP Netweaver BW 시스템과 발생할 수 있는 데이터의 추가 처리에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="49b80-115">The optimal value for this parameter depends on the SAP Netweaver BW system and on additional processing of the data that might occur.</span></span> <span data-ttu-id="49b80-116">일반적으로 2000과 20000 사이의 값이 최상의 성능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="49b80-116">Typically, values between 2000 and 20000 offer the best performance.</span></span>  
  
 <span data-ttu-id="49b80-117">**프로세스 체인 트리거**</span><span class="sxs-lookup"><span data-stu-id="49b80-117">**Trigger process chain**</span></span>  
 <span data-ttu-id="49b80-118">(선택 사항) 데이터 로드가 완료된 후 트리거될 프로세스 체인의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="49b80-118">(Optional) Specify the name of a process chain to be triggered after the loading of data is completed.</span></span>  
  
 <span data-ttu-id="49b80-119">**InfoPackage 대기 제한 시간**</span><span class="sxs-lookup"><span data-stu-id="49b80-119">**Timeout for waiting InfoPackage**</span></span>  
 <span data-ttu-id="49b80-120">대상이 InfoPackage가 완료될 때까지 대기해야 하는 최대 시간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="49b80-120">Specify the maximum number of seconds that the destination should wait for the InfoPackage to finish.</span></span>  
  
 <span data-ttu-id="49b80-121">**데이터 전송이 완료될 때까지 대기**</span><span class="sxs-lookup"><span data-stu-id="49b80-121">**Wait for data transfer to finish**</span></span>  
 <span data-ttu-id="49b80-122">대상이 SAP Netweaver BW 시스템에서 데이터 로드를 완료할 때까지 대기해야 하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="49b80-122">Specify whether the destination should wait until the SAP Netweaver BW system has finished loading the data.</span></span>  
  
 <span data-ttu-id="49b80-123">**InfoPackage 시작 안 함(대기만)**</span><span class="sxs-lookup"><span data-stu-id="49b80-123">**No InfoPackage Start (Only Wait)**</span></span>  
 <span data-ttu-id="49b80-124">대상이 InfoPackage를 트리거하지 않고 SAP Netweaver BW 시스템에서 데이터 로드를 시작했다는 알림을 받을 때까지 대기하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="49b80-124">Specify that the destination does not trigger an InfoPackage, but just waits for notification that the SAP Netweaver BW system has started loading the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49b80-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="49b80-125">See Also</span></span>  
 <span data-ttu-id="49b80-126">[SAP BW 대상 편집기&#40;연결 관리자 페이지&#41;](sap-bw-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="49b80-126">[SAP BW Destination Editor &#40;Connection Manager Page&#41;](sap-bw-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="49b80-127">[SAP BW 대상 편집기&#40;매핑 페이지&#41;](sap-bw-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="49b80-127">[SAP BW Destination Editor &#40;Mappings Page&#41;](sap-bw-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="49b80-128">[SAP BW 대상 편집기&#40;오류 출력 페이지&#41;](sap-bw-destination-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="49b80-128">[SAP BW Destination Editor &#40;Error Output Page&#41;](sap-bw-destination-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="49b80-129">Microsoft Connector 1.1 for SAP BW F1 도움말</span><span class="sxs-lookup"><span data-stu-id="49b80-129">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
