---
title: InfoSource 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e7db233b-5464-43de-9d26-6dd24c7ac1b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9620d3170310322c79679e8298ffe465067ae7d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728552"
---
# <a name="create-infosource"></a><span data-ttu-id="2d2a7-102">InfoSource 만들기</span><span class="sxs-lookup"><span data-stu-id="2d2a7-102">Create InfoSource</span></span>
  <span data-ttu-id="2d2a7-103">**InfoSource 만들기** 대화 상자에서는 새 InfoSource를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d2a7-103">Use the **Create InfoSource** dialog box to create a new InfoSource.</span></span> <span data-ttu-id="2d2a7-104">새 InfoSource를 만들려면 **트랜잭션 데이터용 InfoSource 만들기** 또는 **마스터 데이터용 InfoSource 만들기** 대화 상자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2d2a7-104">To create the new InfoSource, you use either the **Create InfoSource for Transaction Data** or the **Create InfoSource for Master Data** dialog box.</span></span>  
  
 <span data-ttu-id="2d2a7-105">**InfoSource 만들기** 대화 상자는 **SAP BW 대상 편집기** 의 **연결 관리자**페이지에서 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d2a7-105">You can open the **Create InfoSource** dialog box from the **Connection Manager** page of the **SAP BW Destination Editor**.</span></span> <span data-ttu-id="2d2a7-106">SAP BW 대상에 대한 자세한 내용은 [SAP BW Destination](sap-bw-destination.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2d2a7-106">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2d2a7-107">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="2d2a7-107">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="2d2a7-108">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2d2a7-108">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="2d2a7-109">**InfoSource 만들기 대화 상자를 열려면**</span><span class="sxs-lookup"><span data-stu-id="2d2a7-109">**To open the Create InfoSource dialog box**</span></span>  
  
1.  <span data-ttu-id="2d2a7-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 SAP BW 대상이 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2d2a7-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="2d2a7-111">**데이터 흐름** 탭에서 SAP BW 대상을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2d2a7-111">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="2d2a7-112">**SAP BW 대상 편집기**에서 **연결 관리자** 를 클릭하여 편집기의 **연결 관리자** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2d2a7-112">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="2d2a7-113">**연결 관리자** 페이지의 **SAP BW 개체 만들기** 그룹 상자에서 **InfoSource**를 선택한 다음 **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2d2a7-113">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, select **InfoSource**, and then click **Create**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2d2a7-114">옵션</span><span class="sxs-lookup"><span data-stu-id="2d2a7-114">Options</span></span>  
 <span data-ttu-id="2d2a7-115">**트랜잭션 데이터**</span><span class="sxs-lookup"><span data-stu-id="2d2a7-115">**Transaction data**</span></span>  
 <span data-ttu-id="2d2a7-116">트랜잭션 데이터용 새 InfoSource를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2d2a7-116">Create a new InfoSource for transaction data.</span></span>  
  
 <span data-ttu-id="2d2a7-117">이 옵션을 선택하는 경우 **트랜잭션 데이터용 InfoSource 만들기** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="2d2a7-117">If you select this option, the **Create InfoSource for Transaction Data** dialog box opens.</span></span> <span data-ttu-id="2d2a7-118">**트랜잭션 데이터용 InfoSource 만들기** 대화 상자를 사용하여 새 InfoSource를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d2a7-118">You use the **Create InfoSource for Transaction Data** dialog box to create the new InfoSource.</span></span> <span data-ttu-id="2d2a7-119">이 대화 상자에 대한 자세한 내용은 [Create InfoSource for Transaction Data](create-infosource-for-transaction-data.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2d2a7-119">For more information about this dialog box, see [Create InfoSource for Transaction Data](create-infosource-for-transaction-data.md).</span></span>  
  
 <span data-ttu-id="2d2a7-120">**마스터 데이터**</span><span class="sxs-lookup"><span data-stu-id="2d2a7-120">**Master data**</span></span>  
 <span data-ttu-id="2d2a7-121">마스터 데이터용 새 InfoSource를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2d2a7-121">Create a new InfoSource for master data.</span></span>  
  
 <span data-ttu-id="2d2a7-122">이 옵션을 선택하는 경우 **마스터 데이터용 InfoSource 만들기** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="2d2a7-122">If you select this option, the **Create InfoSource for Master Data** dialog box opens.</span></span> <span data-ttu-id="2d2a7-123">**마스터 데이터용 InfoSource 만들기** 대화 상자를 사용하여 새 InfoSource를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d2a7-123">You use the **Create InfoSource for Master Data** dialog box to create the new InfoSource.</span></span> <span data-ttu-id="2d2a7-124">이 대화 상자에 대한 자세한 내용은 [Create InfoSource for Master Data](create-infosource-for-master-data.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2d2a7-124">For more information about this dialog box, see [Create InfoSource for Master Data](create-infosource-for-master-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d2a7-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2d2a7-125">See Also</span></span>  
 [<span data-ttu-id="2d2a7-126">Microsoft Connector 1.1 for SAP BW F1 도움말</span><span class="sxs-lookup"><span data-stu-id="2d2a7-126">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
