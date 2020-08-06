---
title: SAP BW 원본 편집기(오류 출력 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b6e23b0c-949a-46d1-8424-4dc3d9035e79
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a4ad2d02d3f5ec5c1a786019e18fa01665fdc0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728535"
---
# <a name="sap-bw-source-editor-error-output-page"></a><span data-ttu-id="1bb2d-102">SAP BW 원본 편집기(오류 출력 페이지)</span><span class="sxs-lookup"><span data-stu-id="1bb2d-102">SAP BW Source Editor (Error Output Page)</span></span>
  <span data-ttu-id="1bb2d-103">**SAP BW 원본 편집기** 의 **오류 출력** 페이지에서는 오류 처리 옵션을 선택하고 오류 출력 열에 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bb2d-103">Use the **Error Output** page of the **SAP BW Source Editor** to select error handling options and to set properties on error output columns.</span></span>  
  
 <span data-ttu-id="1bb2d-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW의 SAP BW 원본 구성 요소에 대한 자세한 내용은 [SAP BW 원본](sap-bw-source.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1bb2d-104">To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1bb2d-105">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="1bb2d-105">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="1bb2d-106">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1bb2d-106">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1bb2d-107">SAP Netweaver BW에서 데이터를 추출하려면 추가 SAP 라이선스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1bb2d-107">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="1bb2d-108">SAP에서 이러한 요구 사항을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="1bb2d-108">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="1bb2d-109">**오류 출력 페이지를 열려면**</span><span class="sxs-lookup"><span data-stu-id="1bb2d-109">**To open the Error Output page**</span></span>  
  
1.  <span data-ttu-id="1bb2d-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 SAP BW 원본이 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1bb2d-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="1bb2d-111">**데이터 흐름** 탭에서 SAP BW 원본을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1bb2d-111">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="1bb2d-112">**SAP BW 원본 편집기**에서 **오류 출력** 을 클릭하여 편집기의 **오류 출력** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1bb2d-112">In the **SAP BW Source Editor**, click **Error Output** to open the **Error Output** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1bb2d-113">옵션</span><span class="sxs-lookup"><span data-stu-id="1bb2d-113">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1bb2d-114">원본을 구성하는 데 필요한 값 중 모르는 것이 있으면 SAP 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="1bb2d-114">If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="1bb2d-115">**입력 또는 출력**</span><span class="sxs-lookup"><span data-stu-id="1bb2d-115">**Input or Output**</span></span>  
 <span data-ttu-id="1bb2d-116">데이터 원본의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1bb2d-116">View the name of the data source.</span></span>  
  
 <span data-ttu-id="1bb2d-117">**열**</span><span class="sxs-lookup"><span data-stu-id="1bb2d-117">**Column**</span></span>  
 <span data-ttu-id="1bb2d-118">**SAP BW 원본 편집기** 대화 상자의 **열** 페이지에서 선택한 외부(원본) 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1bb2d-118">View the external (source) columns that you selected on the **Columns** page of the **SAP BW Source Editor** dialog box.</span></span> <span data-ttu-id="1bb2d-119">이 대화 상자에 대한 자세한 내용은 [SAP BW 원본 편집기&#40;열 페이지&#41;](sap-bw-source-editor-columns-page.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1bb2d-119">For more information about this dialog box, see [SAP BW Source Editor &#40;Columns Page&#41;](sap-bw-source-editor-columns-page.md).</span></span>  
  
 <span data-ttu-id="1bb2d-120">**오류**</span><span class="sxs-lookup"><span data-stu-id="1bb2d-120">**Error**</span></span>  
 <span data-ttu-id="1bb2d-121">오류가 발생할 경우 수행해야 할 SAP BW 원본을 지정합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bb2d-121">Specify what the SAP BW source component should do when there is an error: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="1bb2d-122">**잘림**</span><span class="sxs-lookup"><span data-stu-id="1bb2d-122">**Truncation**</span></span>  
 <span data-ttu-id="1bb2d-123">잘림이 발생할 경우 수행해야 할 SAP BW 원본을 지정합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bb2d-123">Specify what the SAP BW source component should do when a truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="1bb2d-124">**설명**</span><span class="sxs-lookup"><span data-stu-id="1bb2d-124">**Description**</span></span>  
 <span data-ttu-id="1bb2d-125">오류에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1bb2d-125">View the description of the error.</span></span>  
  
 <span data-ttu-id="1bb2d-126">**이 값을 선택한 셀에 설정**</span><span class="sxs-lookup"><span data-stu-id="1bb2d-126">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="1bb2d-127">오류나 잘림이 발생한 경우 선택한 모든 셀에 수행할 SAP BW 원본을 지정합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bb2d-127">Specify what the SAP BW source component should do to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="1bb2d-128">**적용**</span><span class="sxs-lookup"><span data-stu-id="1bb2d-128">**Apply**</span></span>  
 <span data-ttu-id="1bb2d-129">선택한 셀에 오류 처리 옵션을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="1bb2d-129">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bb2d-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1bb2d-130">See Also</span></span>  
 <span data-ttu-id="1bb2d-131">[SAP BW 원본 편집기&#40;연결 관리자 페이지&#41;](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="1bb2d-131">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="1bb2d-132">[SAP BW 원본 편집기&#40;열 페이지&#41;](sap-bw-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="1bb2d-132">[SAP BW Source Editor &#40;Columns Page&#41;](sap-bw-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="1bb2d-133">[SAP BW 원본 편집기&#40;고급 페이지&#41;](sap-bw-source-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="1bb2d-133">[SAP BW Source Editor &#40;Advanced Page&#41;](sap-bw-source-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="1bb2d-134">Microsoft Connector 1.1 for SAP BW F1 도움말</span><span class="sxs-lookup"><span data-stu-id="1bb2d-134">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
