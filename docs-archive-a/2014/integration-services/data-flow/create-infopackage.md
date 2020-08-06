---
title: InfoPackage 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9cd4a848-409f-4681-a390-1c49a2aadbd7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 95f6ddce4e97c0c21d9f77c432231d414770dbce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728568"
---
# <a name="create-infopackage"></a><span data-ttu-id="f903b-102">InfoPackage 만들기</span><span class="sxs-lookup"><span data-stu-id="f903b-102">Create InfoPackage</span></span>
  <span data-ttu-id="f903b-103">**InfoPackage 만들기** 대화 상자를 사용하여 SAP Netweaver BW 시스템에서 새 InfoPackage를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f903b-103">Use the **Create InfoPackage** dialog box to create a new InfoPackage in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="f903b-104">**InfoPackage 만들기** 대화 상자는 **SAP BW 대상 편집기** 의 **연결 관리자**페이지에서 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f903b-104">You can open the **Create InfoPackage** dialog box from the **Connection Manager** page of the **SAP BW Destination Editor**.</span></span> <span data-ttu-id="f903b-105">SAP BW 대상에 대한 자세한 내용은 [SAP BW Destination](sap-bw-destination.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f903b-105">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f903b-106">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="f903b-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="f903b-107">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f903b-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="f903b-108">**InfoPackage 만들기 대화 상자를 열려면**</span><span class="sxs-lookup"><span data-stu-id="f903b-108">**To open the Create InfoPackage dialog box**</span></span>  
  
1.  <span data-ttu-id="f903b-109">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 SAP BW 대상이 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f903b-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="f903b-110">**데이터 흐름** 탭에서 SAP BW 대상을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f903b-110">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="f903b-111">**SAP BW 대상 편집기**에서 **연결 관리자** 를 클릭하여 편집기의 **연결 관리자** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f903b-111">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="f903b-112">**연결 관리자** 페이지의 **SAP BW 개체 만들기** 그룹 상자에서 **InfoPackage**를 선택한 다음 **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f903b-112">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, select **InfoPackage**, and then click **Create**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f903b-113">옵션</span><span class="sxs-lookup"><span data-stu-id="f903b-113">Options</span></span>  
 <span data-ttu-id="f903b-114">**InfoSource**</span><span class="sxs-lookup"><span data-stu-id="f903b-114">**InfoSource**</span></span>  
 <span data-ttu-id="f903b-115">새 InfoPackage의 기준으로 사용할 InfoSource의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f903b-115">Enter the name of the InfoSource on which the new InfoPackage should be based.</span></span>  
  
 <span data-ttu-id="f903b-116">**간단한 설명**</span><span class="sxs-lookup"><span data-stu-id="f903b-116">**Short description**</span></span>  
 <span data-ttu-id="f903b-117">새 InfoPackage에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f903b-117">Enter a description for the new InfoPackage.</span></span>  
  
 <span data-ttu-id="f903b-118">**원본 시스템**</span><span class="sxs-lookup"><span data-stu-id="f903b-118">**Source system**</span></span>  
 <span data-ttu-id="f903b-119">새 InfoPackage에 연결할 원본 시스템을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f903b-119">Select the source system with which the new InfoPackage should be associated.</span></span>  
  
 <span data-ttu-id="f903b-120">**특성**</span><span class="sxs-lookup"><span data-stu-id="f903b-120">**Attributes**</span></span>  
 <span data-ttu-id="f903b-121">InfoPackage가 특성 데이터를 로드함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f903b-121">Indicates that the InfoPackage will load attribute data.</span></span>  
  
 <span data-ttu-id="f903b-122">**텍스트**</span><span class="sxs-lookup"><span data-stu-id="f903b-122">**Texts**</span></span>  
 <span data-ttu-id="f903b-123">InfoPackage가 텍스트 데이터를 로드함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f903b-123">Indicates that the InfoPackage will load text data.</span></span>  
  
 <span data-ttu-id="f903b-124">**트랜잭션**</span><span class="sxs-lookup"><span data-stu-id="f903b-124">**Transaction**</span></span>  
 <span data-ttu-id="f903b-125">InfoPackage가 트랜잭션 데이터를 로드함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f903b-125">Indicates that the InfoPackage will load transaction data.</span></span>  
  
 <span data-ttu-id="f903b-126">**저장 및 활성화**</span><span class="sxs-lookup"><span data-stu-id="f903b-126">**Save & Activate**</span></span>  
 <span data-ttu-id="f903b-127">새 InfoPackage를 저장하고 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="f903b-127">Save and activate the new InfoPackage.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f903b-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f903b-128">See Also</span></span>  
 [<span data-ttu-id="f903b-129">Microsoft Connector 1.1 for SAP BW F1 도움말</span><span class="sxs-lookup"><span data-stu-id="f903b-129">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
