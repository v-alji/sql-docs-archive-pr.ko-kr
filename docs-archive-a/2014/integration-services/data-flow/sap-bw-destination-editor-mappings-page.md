---
title: SAP BW 대상 편집기(매핑 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: dfa1f1d6-6b64-4331-bdc5-eaa8b7aa41a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7c4c2803be3e2649f7425a2974dae8ac0a80fae7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728540"
---
# <a name="sap-bw-destination-editor-mappings-page"></a><span data-ttu-id="3dc85-102">SAP BW 대상 편집기(매핑 페이지)</span><span class="sxs-lookup"><span data-stu-id="3dc85-102">SAP BW Destination Editor (Mappings Page)</span></span>
  <span data-ttu-id="3dc85-103">**SAP BW 대상 편집기** 의 **매핑** 페이지를 사용하여 입력 열을 대상 열에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3dc85-103">Use the **Mappings** page of the **SAP BW Destination Editor** to map input columns to destination columns.</span></span>  
  
 <span data-ttu-id="3dc85-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW의 SAP BW 대상에 대한 자세한 내용은 [SAP BW 대상](sap-bw-destination.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3dc85-104">To learn more about the SAP BW destination of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3dc85-105">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc85-105">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="3dc85-106">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3dc85-106">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="3dc85-107">**매핑 페이지를 열려면**</span><span class="sxs-lookup"><span data-stu-id="3dc85-107">**To open the Mappings page**</span></span>  
  
1.  <span data-ttu-id="3dc85-108">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 SAP BW 대상이 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3dc85-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="3dc85-109">**데이터 흐름** 탭에서 SAP BW 대상을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc85-109">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="3dc85-110">**SAP BW 대상 편집기**에서 **매핑** 을 클릭하여 편집기의 **매핑** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3dc85-110">In the **SAP BW Destination Editor**, click **Mappings** to open the **Mappings** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3dc85-111">옵션</span><span class="sxs-lookup"><span data-stu-id="3dc85-111">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3dc85-112">대상을 구성하는 데 필요한 값 중 모르는 것이 있으면 SAP 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="3dc85-112">If you do not know all the values that are required to configure the destination, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="3dc85-113">**SAP BW 대상 편집기** 의 **매핑** 페이지는 두 개의 섹션으로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3dc85-113">The **Mappings** page of the **SAP BW Destination Editor consists** of two sections:</span></span>  
  
-   <span data-ttu-id="3dc85-114">위쪽 섹션에는 사용 가능한 입력 및 대상 열이 표시되고 이 두 종류의 열 사이에 매핑을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3dc85-114">The upper section shows the available input and destination columns and lets you create mappings between these two types of columns.</span></span>  
  
-   <span data-ttu-id="3dc85-115">아래쪽 섹션은 입력 열과 출력 열 사이의 매핑을 보여 주는 표입니다.</span><span class="sxs-lookup"><span data-stu-id="3dc85-115">The lower section is a table that lists which input columns have been mapped to which output columns.</span></span>  
  
### <a name="upper-section-options"></a><span data-ttu-id="3dc85-116">위쪽 섹션 옵션</span><span class="sxs-lookup"><span data-stu-id="3dc85-116">Upper Section Options</span></span>  
 <span data-ttu-id="3dc85-117">위쪽 섹션에는 다음과 같은 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3dc85-117">The upper section has the following options:</span></span>  
  
 <span data-ttu-id="3dc85-118">**사용 가능한 입력 열**</span><span class="sxs-lookup"><span data-stu-id="3dc85-118">**Available Input Columns**</span></span>  
 <span data-ttu-id="3dc85-119">사용 가능한 입력 열 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc85-119">View the list of available input columns.</span></span>  
  
 <span data-ttu-id="3dc85-120">입력 열을 대상 열에 매핑하려면 **사용 가능한 입력 열** 목록의 열을 **사용 가능한 대상 열** 목록으로 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="3dc85-120">To map an input column to a destination column, drag a column from the **Available Input Columns** list and drop that column onto a column in the **Available Destination Columns** list.</span></span>  
  
 <span data-ttu-id="3dc85-121">**사용 가능한 대상 열**</span><span class="sxs-lookup"><span data-stu-id="3dc85-121">**Available Destination Columns**</span></span>  
 <span data-ttu-id="3dc85-122">사용 가능한 대상 열의 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc85-122">View the list of available destination columns.</span></span>  
  
 <span data-ttu-id="3dc85-123">입력 열을 대상 열에 매핑하려면 **사용 가능한 입력 열** 목록의 열을 **사용 가능한 대상 열** 목록으로 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="3dc85-123">To map an input column to destination column, drag a column from the **Available Input Columns** list and drop that column onto a column in the **Available Destination Columns** list.</span></span>  
  
 <span data-ttu-id="3dc85-124">위쪽 섹션에는 백그라운드에서 마우스 오른쪽 단추를 클릭하여 열 수 있는 상황에 맞는 메뉴도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3dc85-124">The upper section also has a context menu that you can open by right-clicking on the background.</span></span> <span data-ttu-id="3dc85-125">상황에 맞는 메뉴에는 다음 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3dc85-125">This context menu contains the following options:</span></span>  
  
-   <span data-ttu-id="3dc85-126">**모든 매핑 선택**</span><span class="sxs-lookup"><span data-stu-id="3dc85-126">**Select All Mappings**</span></span>  
  
-   <span data-ttu-id="3dc85-127">**선택한 매핑 삭제**</span><span class="sxs-lookup"><span data-stu-id="3dc85-127">**Delete Selected Mappings**</span></span>  
  
-   <span data-ttu-id="3dc85-128">**일치하는 이름별 항목 매핑**</span><span class="sxs-lookup"><span data-stu-id="3dc85-128">**Map Items by Matching Names**</span></span>  
  
### <a name="lower-section-columns"></a><span data-ttu-id="3dc85-129">아래쪽 섹션 열</span><span class="sxs-lookup"><span data-stu-id="3dc85-129">Lower Section Columns</span></span>  
 <span data-ttu-id="3dc85-130">아래쪽 섹션은 매핑 표이며, 다음과 같은 열로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3dc85-130">The lower section is a table of the mappings, and has the following columns:</span></span>  
  
 <span data-ttu-id="3dc85-131">**입력 열**</span><span class="sxs-lookup"><span data-stu-id="3dc85-131">**Input Column**</span></span>  
 <span data-ttu-id="3dc85-132">선택한 입력 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc85-132">View the input columns that you have selected.</span></span>  
  
 <span data-ttu-id="3dc85-133">다른 입력 열을 동일한 대상 열에 매핑하려면 목록에서 다른 입력 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc85-133">To map a different input column to the same destination column, select a different input column in the list.</span></span> <span data-ttu-id="3dc85-134">매핑을 제거하려면 **\<ignore>** 를 선택하여 해당 입력 열을 출력에서 제외합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc85-134">To remove a mapping, select **\<ignore>** to exclude the input column from the output.</span></span>  
  
 <span data-ttu-id="3dc85-135">**대상 열**</span><span class="sxs-lookup"><span data-stu-id="3dc85-135">**Destination Column**</span></span>  
 <span data-ttu-id="3dc85-136">열의 매핑 여부에 관계없이 사용 가능한 각 대상 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc85-136">View each available destination column, regardless of whether that column is mapped or not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dc85-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3dc85-137">See Also</span></span>  
 <span data-ttu-id="3dc85-138">[SAP BW 대상 편집기&#40;연결 관리자 페이지&#41;](sap-bw-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="3dc85-138">[SAP BW Destination Editor &#40;Connection Manager Page&#41;](sap-bw-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="3dc85-139">[SAP BW 대상 편집기&#40;오류 출력 페이지&#41;](sap-bw-destination-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="3dc85-139">[SAP BW Destination Editor &#40;Error Output Page&#41;](sap-bw-destination-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="3dc85-140">[SAP BW 대상 편집기&#40;고급 페이지&#41;](sap-bw-destination-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="3dc85-140">[SAP BW Destination Editor &#40;Advanced Page&#41;](sap-bw-destination-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="3dc85-141">Microsoft Connector 1.1 for SAP BW F1 도움말</span><span class="sxs-lookup"><span data-stu-id="3dc85-141">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
