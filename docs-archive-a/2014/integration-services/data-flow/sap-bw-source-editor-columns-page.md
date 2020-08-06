---
title: SAP BW 원본 편집기(열 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c2ec8bb7-be9b-4783-ad88-32512de784b0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ba605360d01abc520cedfbc457dd89319ed83c52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738553"
---
# <a name="sap-bw-source-editor-columns-page"></a><span data-ttu-id="4b0eb-102">SAP BW 원본 편집기(열 페이지)</span><span class="sxs-lookup"><span data-stu-id="4b0eb-102">SAP BW Source Editor (Columns Page)</span></span>
  <span data-ttu-id="4b0eb-103">**SAP BW 원본 편집기** 의 **열** 페이지를 사용하여 출력 열을 각 외부(원본) 열에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b0eb-103">Use the **Columns** page of the **SAP BW Source Editor** to map an output column to each external (source) column.</span></span>  
  
 <span data-ttu-id="4b0eb-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW의 SAP BW 원본 구성 요소에 대한 자세한 내용은 [SAP BW 원본](sap-bw-source.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4b0eb-104">To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4b0eb-105">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="4b0eb-105">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="4b0eb-106">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4b0eb-106">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4b0eb-107">SAP Netweaver BW에서 데이터를 추출하려면 추가 SAP 라이선스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4b0eb-107">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="4b0eb-108">SAP에서 이러한 요구 사항을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="4b0eb-108">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="4b0eb-109">**열 페이지를 열려면**</span><span class="sxs-lookup"><span data-stu-id="4b0eb-109">**To open the Columns page**</span></span>  
  
1.  <span data-ttu-id="4b0eb-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 SAP BW 원본이 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4b0eb-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="4b0eb-111">**데이터 흐름** 탭에서 SAP BW 원본을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4b0eb-111">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="4b0eb-112">**SAP BW 원본 편집기**에서 **열** 을 클릭하여 편집기의 **열** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4b0eb-112">In the **SAP BW Source Editor**, click **Columns** to open the **Columns** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4b0eb-113">옵션</span><span class="sxs-lookup"><span data-stu-id="4b0eb-113">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4b0eb-114">원본을 구성하는 데 필요한 값 중 모르는 것이 있으면 SAP 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="4b0eb-114">If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="4b0eb-115">**사용 가능한 외부 열**</span><span class="sxs-lookup"><span data-stu-id="4b0eb-115">**Available External Columns**</span></span>  
 <span data-ttu-id="4b0eb-116">데이터 원본에서 사용 가능한 외부 열의 목록을 확인한 다음 데이터 흐름에 포함할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4b0eb-116">View the list of available external columns in the data source, and then select the columns to be included in the data flow.</span></span>  
  
 <span data-ttu-id="4b0eb-117">데이터 흐름에 열을 포함하려면 포함하려는 열에 해당하는 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4b0eb-117">To include a column in the data flow, select the check box that corresponds to that column.</span></span> <span data-ttu-id="4b0eb-118">확인란을 선택하는 순서에 따라 열이 출력되는 순서가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b0eb-118">The order in which you select the check boxes determines the order in which columns will be output.</span></span> <span data-ttu-id="4b0eb-119">즉, 선택하는 첫 번째 확인란이 첫 번째 출력 열이 되고 두 번째 확인란이 두 번째 출력 열이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b0eb-119">That is, the first check box that you select will be the first output column, the second check box will be the second output columns, and so on.</span></span>  
  
 <span data-ttu-id="4b0eb-120">**외부 열**</span><span class="sxs-lookup"><span data-stu-id="4b0eb-120">**External Column**</span></span>  
 <span data-ttu-id="4b0eb-121">선택된 외부(원본) 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4b0eb-121">View the selected external (source) columns.</span></span> <span data-ttu-id="4b0eb-122">이 원본의 데이터를 소비하는 다운스트림 구성 요소를 구성할 때 선택된 열의 순서대로 해당 출력 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b0eb-122">The selected columns appear in the order in which you will see their corresponding output columns when you configure downstream components that consume data from this source.</span></span>  
  
 <span data-ttu-id="4b0eb-123">열 순서를 변경하려면 **사용 가능한 외부 열** 목록에서 모든 열에 대한 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="4b0eb-123">To change the order of the columns, in the **Available External Columns** list, clear the check boxes for all columns.</span></span> <span data-ttu-id="4b0eb-124">그런 다음 표시할 순서대로 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4b0eb-124">Then, select the columns in the order that you want them to appear.</span></span>  
  
 <span data-ttu-id="4b0eb-125">**출력 열**</span><span class="sxs-lookup"><span data-stu-id="4b0eb-125">**Output Column**</span></span>  
 <span data-ttu-id="4b0eb-126">각 출력 열에 고유한 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4b0eb-126">Provide a unique name for each output column.</span></span> <span data-ttu-id="4b0eb-127">기본값은 선택된 외부(원본) 열의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="4b0eb-127">The default is the name of the selected external (source) column.</span></span> <span data-ttu-id="4b0eb-128">하지만 설명이 포함된 고유 이름을 입력할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b0eb-128">However, you can enter any unique, descriptive name.</span></span> [!INCLUDE[ssIS](../../includes/ssis-md.md)] <span data-ttu-id="4b0eb-129">디자이너에는 해당 열에 대한 **출력 열** 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b0eb-129">Designer will display the **Output Column** names for the columns when you configure downstream components that consume data from this source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b0eb-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b0eb-130">See Also</span></span>  
 <span data-ttu-id="4b0eb-131">[SAP BW 원본 편집기&#40;연결 관리자 페이지&#41;](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="4b0eb-131">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="4b0eb-132">[SAP BW 원본 편집기&#40;오류 출력 페이지&#41;](sap-bw-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="4b0eb-132">[SAP BW Source Editor &#40;Error Output Page&#41;](sap-bw-source-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="4b0eb-133">[SAP BW 원본 편집기&#40;고급 페이지&#41;](sap-bw-source-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="4b0eb-133">[SAP BW Source Editor &#40;Advanced Page&#41;](sap-bw-source-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="4b0eb-134">Microsoft Connector 1.1 for SAP BW F1 도움말</span><span class="sxs-lookup"><span data-stu-id="4b0eb-134">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
