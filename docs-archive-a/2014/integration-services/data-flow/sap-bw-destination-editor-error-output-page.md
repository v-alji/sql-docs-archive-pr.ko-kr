---
title: SAP BW 대상 편집기(오류 출력 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a543d811-0bd2-4890-a0d3-f5fdcd4524b8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9ffd58580865a71626252aa2d177530e41156537
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728543"
---
# <a name="sap-bw-destination-editor-error-output-page"></a><span data-ttu-id="9451f-102">SAP BW 대상 편집기(오류 출력 페이지)</span><span class="sxs-lookup"><span data-stu-id="9451f-102">SAP BW Destination Editor (Error Output Page)</span></span>
  <span data-ttu-id="9451f-103">**SAP BW 대상 편집기** 의 **오류 출력** 페이지를 사용하여 오류 처리 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9451f-103">Use the **Error Output** page of the **SAP BW Destination Editor** to specify error handling options.</span></span>  
  
 <span data-ttu-id="9451f-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW의 SAP BW 대상에 대한 자세한 내용은 [SAP BW 대상](sap-bw-destination.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9451f-104">To learn more about the SAP BW destination of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9451f-105">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="9451f-105">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="9451f-106">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9451f-106">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="9451f-107">**오류 출력 페이지를 열려면**</span><span class="sxs-lookup"><span data-stu-id="9451f-107">**To open the Error Output page**</span></span>  
  
1.  <span data-ttu-id="9451f-108">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 SAP BW 대상이 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9451f-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="9451f-109">**데이터 흐름** 탭에서 SAP BW 대상을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9451f-109">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="9451f-110">**SAP BW 대상 편집기**에서 **오류 출력** 을 클릭하여 편집기의 **오류 출력** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9451f-110">In the **SAP BW Destination Editor**, click **Error Output** to open the **Error Output** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9451f-111">옵션</span><span class="sxs-lookup"><span data-stu-id="9451f-111">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9451f-112">대상을 구성하는 데 필요한 값 중 모르는 것이 있으면 SAP 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="9451f-112">If you do not know all the values that are required to configure the destination, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="9451f-113">**입력 또는 출력**</span><span class="sxs-lookup"><span data-stu-id="9451f-113">**Input or Output**</span></span>  
 <span data-ttu-id="9451f-114">입력 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9451f-114">View the name of the input.</span></span>  
  
 <span data-ttu-id="9451f-115">**열**</span><span class="sxs-lookup"><span data-stu-id="9451f-115">**Column**</span></span>  
 <span data-ttu-id="9451f-116">이 옵션은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9451f-116">This option is not used.</span></span>  
  
 <span data-ttu-id="9451f-117">**오류**</span><span class="sxs-lookup"><span data-stu-id="9451f-117">**Error**</span></span>  
 <span data-ttu-id="9451f-118">오류가 발생할 경우 수행해야 할 대상을 지정합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9451f-118">Specify what the destination should do when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="9451f-119">**잘림**</span><span class="sxs-lookup"><span data-stu-id="9451f-119">**Truncation**</span></span>  
 <span data-ttu-id="9451f-120">이 옵션은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9451f-120">This option is not used.</span></span>  
  
 <span data-ttu-id="9451f-121">**설명**</span><span class="sxs-lookup"><span data-stu-id="9451f-121">**Description**</span></span>  
 <span data-ttu-id="9451f-122">작업에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9451f-122">View the description of the operation.</span></span>  
  
 <span data-ttu-id="9451f-123">**이 값을 선택한 셀에 설정**</span><span class="sxs-lookup"><span data-stu-id="9451f-123">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="9451f-124">오류나 잘림이 발생한 경우 선택한 모든 셀에 수행할 대상을 지정합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9451f-124">Specify what the destination should do to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="9451f-125">**적용**</span><span class="sxs-lookup"><span data-stu-id="9451f-125">**Apply**</span></span>  
 <span data-ttu-id="9451f-126">선택한 셀에 오류 처리 옵션을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="9451f-126">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9451f-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9451f-127">See Also</span></span>  
 <span data-ttu-id="9451f-128">[SAP BW 대상 편집기&#40;연결 관리자 페이지&#41;](sap-bw-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="9451f-128">[SAP BW Destination Editor &#40;Connection Manager Page&#41;](sap-bw-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="9451f-129">[SAP BW 대상 편집기&#40;매핑 페이지&#41;](sap-bw-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="9451f-129">[SAP BW Destination Editor &#40;Mappings Page&#41;](sap-bw-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="9451f-130">[SAP BW 대상 편집기&#40;고급 페이지&#41;](sap-bw-destination-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="9451f-130">[SAP BW Destination Editor &#40;Advanced Page&#41;](sap-bw-destination-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="9451f-131">Microsoft Connector 1.1 for SAP BW F1 도움말</span><span class="sxs-lookup"><span data-stu-id="9451f-131">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
