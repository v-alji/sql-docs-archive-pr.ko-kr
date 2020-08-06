---
title: 미리 보기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 551494c4-9e27-4592-9200-c6bf19e80c9a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5a795338122c1e7a37a23fdb6af6153f74b927e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648464"
---
# <a name="preview"></a><span data-ttu-id="8ba0d-102">미리 보기</span><span class="sxs-lookup"><span data-stu-id="8ba0d-102">Preview</span></span>
  <span data-ttu-id="8ba0d-103">**미리 보기** 대화 상자를 사용하여 SAP BW 원본이 추출할 데이터를 미리 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba0d-103">Use the **Preview** dialog box to preview the data that the SAP BW source will extract.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8ba0d-104">**SAP BW 원본 편집기** 의 **연결 관리자** 페이지에서 사용할 수 있는 **미리 보기**옵션은 데이터를 실제로 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba0d-104">The **Preview** option, that is available on the **Connection Manager** page of the **SAP BW Source Editor**, actually extracts data.</span></span> <span data-ttu-id="8ba0d-105">이전 추출 이후에 변경된 데이터만 추출하도록 SAP Netweaver BW를 구성한 경우 **미리 보기** 를 선택하면 미리 본 데이터가 다음 추출에서 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ba0d-105">If you have configured SAP Netweaver BW to extract only data that has changed since the previous extraction, selecting **Preview** will exclude the previewed data from the next extraction.</span></span>  
  
 <span data-ttu-id="8ba0d-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW의 SAP BW 원본 구성 요소에 대한 자세한 내용은 [SAP BW 원본](sap-bw-source.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ba0d-106">To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8ba0d-107">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba0d-107">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="8ba0d-108">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8ba0d-108">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8ba0d-109">SAP Netweaver BW에서 데이터를 추출하려면 추가 SAP 라이선스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba0d-109">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="8ba0d-110">SAP에서 이러한 요구 사항을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="8ba0d-110">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="8ba0d-111">**미리 보기 대화 상자를 열려면**</span><span class="sxs-lookup"><span data-stu-id="8ba0d-111">**To open the Preview dialog box**</span></span>  
  
1.  <span data-ttu-id="8ba0d-112">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 SAP BW 원본이 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8ba0d-112">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="8ba0d-113">**데이터 흐름** 탭에서 SAP BW 원본을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba0d-113">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="8ba0d-114">**SAP BW 원본 편집기**에서 **연결 관리자** 를 클릭하여 편집기의 **연결 관리자** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8ba0d-114">In the **SAP BW Source Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="8ba0d-115">SAP BW 원본을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba0d-115">Configure the SAP BW source.</span></span>  
  
5.  <span data-ttu-id="8ba0d-116">SAP BW 원본을 구성한 후 **연결 관리자** 페이지에서 **미리 보기** 를 클릭하여 **미리 보기** 대화 상자에서 데이터를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="8ba0d-116">After you configure the SAP BW source, on the **Connection Manager** page, click **Preview** to preview the data in the **Preview** dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8ba0d-117">**미리 보기** 를 클릭하면 **요청 로그** 대화 상자도 열립니다.</span><span class="sxs-lookup"><span data-stu-id="8ba0d-117">Clicking **Preview** also opens the **Request Log** dialog box.</span></span> <span data-ttu-id="8ba0d-118">이 대화 상자에 대한 자세한 내용은 [Request Log](request-log.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8ba0d-118">For more information about this dialog box, see [Request Log](request-log.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="8ba0d-119">옵션</span><span class="sxs-lookup"><span data-stu-id="8ba0d-119">Options</span></span>  
 <span data-ttu-id="8ba0d-120">**미리 보기** 대화 상자에는 SAP Netweaver BW 시스템에서 요청된 행이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ba0d-120">The **Preview** dialog box displays the rows that are requested from the SAP Netweaver BW system.</span></span> <span data-ttu-id="8ba0d-121">표시되는 열은 원본 데이터에 정의된 열입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba0d-121">The columns that are displayed are the columns that are defined in the source data.</span></span>  
  
 <span data-ttu-id="8ba0d-122">이 대화 상자에 다른 옵션은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba0d-122">There are no other options in this dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ba0d-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8ba0d-123">See Also</span></span>  
 <span data-ttu-id="8ba0d-124">[SAP BW 원본 편집기&#40;연결 관리자 페이지&#41;](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="8ba0d-124">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="8ba0d-125">Microsoft Connector 1.1 for SAP BW F1 도움말</span><span class="sxs-lookup"><span data-stu-id="8ba0d-125">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
