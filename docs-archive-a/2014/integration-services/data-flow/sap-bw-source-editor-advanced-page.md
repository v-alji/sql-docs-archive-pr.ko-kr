---
title: SAP BW 원본 편집기(고급 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 44f3c991-9e8f-4126-a9a2-2d9da779fb11
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7c78d40555a30031bf39abda18048fda9c648d01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740197"
---
# <a name="sap-bw-source-editor-advanced-page"></a><span data-ttu-id="6d994-102">SAP BW 원본 편집기(고급 페이지)</span><span class="sxs-lookup"><span data-stu-id="6d994-102">SAP BW Source Editor (Advanced Page)</span></span>
  <span data-ttu-id="6d994-103">**SAP BW 원본 편집기** 의 **고급** 페이지를 사용하여 문자열 변환 규칙과 제한 시간을 지정하고 특정 요청 ID의 상태를 다시 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d994-103">Use the **Advanced** page of the **SAP BW Source Editor** to specify the string conversion rule and the time-out period, and also to reset the status of a particular Request ID.</span></span>  
  
 <span data-ttu-id="6d994-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW의 SAP BW 원본 구성 요소에 대한 자세한 내용은 [SAP BW 원본](sap-bw-source.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6d994-104">To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6d994-105">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="6d994-105">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="6d994-106">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6d994-106">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6d994-107">SAP Netweaver BW에서 데이터를 추출하려면 추가 SAP 라이선스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6d994-107">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="6d994-108">SAP에서 이러한 요구 사항을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="6d994-108">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="6d994-109">**연결 관리자 페이지를 열려면**</span><span class="sxs-lookup"><span data-stu-id="6d994-109">**To open the Connection Manager page**</span></span>  
  
1.  <span data-ttu-id="6d994-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 SAP BW 원본이 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6d994-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="6d994-111">**데이터 흐름** 탭에서 SAP BW 원본을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6d994-111">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="6d994-112">**SAP BW 원본 편집기**에서 **고급** 을 클릭하여 편집기의 **고급** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6d994-112">In the **SAP BW Source Editor**, click **Advanced** to open the **Advanced** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6d994-113">옵션</span><span class="sxs-lookup"><span data-stu-id="6d994-113">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6d994-114">원본을 구성하는 데 필요한 값 중 모르는 것이 있으면 SAP 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="6d994-114">If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="6d994-115">**문자열 변환**</span><span class="sxs-lookup"><span data-stu-id="6d994-115">**String Conversion**</span></span>  
 <span data-ttu-id="6d994-116">문자열 변환을 위해 적용할 규칙을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6d994-116">Specify the rule to apply for string conversion.</span></span>  
  
|<span data-ttu-id="6d994-117">옵션</span><span class="sxs-lookup"><span data-stu-id="6d994-117">Option</span></span>|<span data-ttu-id="6d994-118">Description</span><span class="sxs-lookup"><span data-stu-id="6d994-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="6d994-119">**자동 문자열 변환**</span><span class="sxs-lookup"><span data-stu-id="6d994-119">**Automatic string conversion**</span></span>|<span data-ttu-id="6d994-120">SAP Netweaver BW 시스템이 유니코드 시스템이면 모든 문자열을 `nvarchar`로 변환하고,</span><span class="sxs-lookup"><span data-stu-id="6d994-120">Convert all strings to `nvarchar` when the SAP Netweaver BW system is a Unicode system.</span></span> <span data-ttu-id="6d994-121">그렇지 않으면 모든 문자열을 `varchar`로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="6d994-121">Otherwise, convert all strings to `varchar`.</span></span>|  
|<span data-ttu-id="6d994-122">**VarChar로 문자열 변환**</span><span class="sxs-lookup"><span data-stu-id="6d994-122">**Convert strings to varchar**</span></span>|<span data-ttu-id="6d994-123">모든 문자열을 `varchar`로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="6d994-123">Convert all strings to `varchar`.</span></span>|  
|<span data-ttu-id="6d994-124">**NVarChar로 문자열 변환**</span><span class="sxs-lookup"><span data-stu-id="6d994-124">**Convert strings to nvarchar**</span></span>|<span data-ttu-id="6d994-125">모든 문자열을 `nvarchar`로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="6d994-125">Convert all strings to `nvarchar`.</span></span>|  
  
 <span data-ttu-id="6d994-126">**제한 시간(초)**</span><span class="sxs-lookup"><span data-stu-id="6d994-126">**Timeout (seconds)**</span></span>  
 <span data-ttu-id="6d994-127">원본이 대기해야 하는 최대 시간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6d994-127">Specify the maximum number of seconds that the source should wait.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6d994-128">이 옵션은 편집기의 **연결 관리자** 페이지에서 **실행 모드** 의 값으로 **W - 알릴 때까지 대기** 를 선택한 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="6d994-128">This option is only valid if you have selected **W - Wait for Notify** as the value of **Execution Mode** on the **Connection Manager** page of the editor.</span></span> <span data-ttu-id="6d994-129">자세한 내용은 [SAP BW 원본 편집기&#40;연결 관리자 페이지&#41;](sap-bw-source-editor-connection-manager-page.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6d994-129">For more information, see [SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md).</span></span>  
  
 <span data-ttu-id="6d994-130">**요청 ID**</span><span class="sxs-lookup"><span data-stu-id="6d994-130">**Request ID**</span></span>  
 <span data-ttu-id="6d994-131">**다시 설정**을 클릭할 때 "G - 녹색"으로 상태를 다시 설정할 요청 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6d994-131">Specify the Request ID whose status you want to reset to "G - Green" when you click **Reset**.</span></span>  
  
 <span data-ttu-id="6d994-132">**재설정**</span><span class="sxs-lookup"><span data-stu-id="6d994-132">**Reset**</span></span>  
 <span data-ttu-id="6d994-133">확인 메시지를 표시한 후 지정된 요청 ID의 상태를 "G - 녹색"으로 다시 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d994-133">Lets you reset the status of the specified Request ID to "G - Green", after prompting you for confirmation.</span></span> <span data-ttu-id="6d994-134">이 옵션은 문제가 발생하고 SAP Netweaver BW 시스템에서 노란색 또는 빨간색 상태로 요청에 플래그를 지정한 경우에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d994-134">This can be useful when a problem has occurred, and the SAP Netweaver BW system has flagged the request with a yellow or red status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d994-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6d994-135">See Also</span></span>  
 <span data-ttu-id="6d994-136">[SAP BW 원본 편집기&#40;연결 관리자 페이지&#41;](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="6d994-136">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="6d994-137">[SAP BW 원본 편집기&#40;열 페이지&#41;](sap-bw-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="6d994-137">[SAP BW Source Editor &#40;Columns Page&#41;](sap-bw-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="6d994-138">[SAP BW 원본 편집기&#40;오류 출력 페이지&#41;](sap-bw-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="6d994-138">[SAP BW Source Editor &#40;Error Output Page&#41;](sap-bw-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="6d994-139">Microsoft Connector 1.1 for SAP BW F1 도움말</span><span class="sxs-lookup"><span data-stu-id="6d994-139">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
