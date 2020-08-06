---
title: SAP BW 용 Microsoft Connector 1.1 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5281f080-53d5-4679-aa26-f4cd4ac7a2df
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ec5cfe83b201976be0512c54b77bc79f8aa824b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736543"
---
# <a name="microsoft-connector-11-for-sap-bw"></a><span data-ttu-id="0bc84-102">Microsoft Connector 1.1 for SAP BW</span><span class="sxs-lookup"><span data-stu-id="0bc84-102">Microsoft Connector 1.1 for SAP BW</span></span>
  <span data-ttu-id="0bc84-103">SAP BW용 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1은 SAP Netweaver BW 버전 7 시스템에서 데이터를 추출하거나 해당 시스템으로 데이터를 로드할 수 있도록 지원하는 3가지 구성 요소 집합으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="0bc84-103">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW consists of a set of three components that let you extract data from, or load data into, an SAP Netweaver BW version 7 system.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0bc84-104">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="0bc84-104">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="0bc84-105">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0bc84-105">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0bc84-106">SAP Netweaver BW에서 데이터를 추출하려면 추가 SAP 라이선스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0bc84-106">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="0bc84-107">SAP에서 이러한 요구 사항을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="0bc84-107">Check with SAP to verify these requirements.</span></span>  
  
## <a name="components"></a><span data-ttu-id="0bc84-108">구성 요소</span><span class="sxs-lookup"><span data-stu-id="0bc84-108">Components</span></span>  
 <span data-ttu-id="0bc84-109">SAP BW용 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1은 다음 구성 요소가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0bc84-109">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW has the following components:</span></span>  
  
-   <span data-ttu-id="0bc84-110">**SAP BW 원본**-SAP BW 원본은 SAP Netweaver BW 버전 7 시스템에서 데이터를 추출할 수 있도록 하는 데이터 흐름 원본 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0bc84-110">**SAP BW Source**-The SAP BW source is a data flow source component that lets you extract data from an SAP Netweaver BW version 7 system.</span></span>  
  
-   <span data-ttu-id="0bc84-111">**SAP BW 대상**-SAP BW 대상은 SAP Netweaver BW 버전 7 시스템으로 데이터를 로드할 수 있도록 하는 데이터 흐름 대상 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0bc84-111">**SAP BW Destination**-The SAP BW destination is a data flow destination component that lets you load data into an SAP Netweaver BW version 7 system.</span></span>  
  
-   <span data-ttu-id="0bc84-112">**SAP BW 연결 관리자**-SAP BW 연결 관리자는 SAP BW 원본 또는 SAP BW 대상을 SAP Netweaver BW 버전 7 시스템에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bc84-112">**SAP BW Connection Manager**-The SAP BW connection manager connects either an SAP BW source or SAP BW destination to an SAP Netweaver BW version 7 system.</span></span>  
  
 <span data-ttu-id="0bc84-113">SAP BW 연결 관리자, 원본 및 대상을 구성하고 사용하는 방법을 제시하는 연습은 [SAP BI 7.0에서 SQL Server Integration Services 사용](https://go.microsoft.com/fwlink/?LinkId=301897)백서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0bc84-113">For a walkthrough that demonstrates how to configure and use the SAP BW connection manager, source, and destination, see the white paper, [Using SQL Server Integration Services with SAP BI 7.0](https://go.microsoft.com/fwlink/?LinkId=301897).</span></span> <span data-ttu-id="0bc84-114">또한 이 백서는 SAP BW에 필요한 개체를 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0bc84-114">This white paper also shows how to configure the required objects in SAP BW.</span></span>  
  
## <a name="documentation"></a><span data-ttu-id="0bc84-115">설명서</span><span class="sxs-lookup"><span data-stu-id="0bc84-115">Documentation</span></span>  
 <span data-ttu-id="0bc84-116">SAP BW용 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1에 대한 도움말 파일에는 다음 항목과 섹션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bc84-116">This Help file for the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW contains the following topics and sections:</span></span>  
  
 [<span data-ttu-id="0bc84-117">Microsoft Connector for 1.1 SAP BW 설치</span><span class="sxs-lookup"><span data-stu-id="0bc84-117">Installing the Microsoft Connector for 1.1 SAP BW</span></span>](installing-the-microsoft-connector-for-sap-bw.md)  
 <span data-ttu-id="0bc84-118">SAP BW용 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1에 대한 설치 구성 요소를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0bc84-118">Describes the installation requirements for the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span>  
  
 [<span data-ttu-id="0bc84-119">Microsoft Connector 1.1 for SAP BW 구성 요소</span><span class="sxs-lookup"><span data-stu-id="0bc84-119">Microsoft Connector 1.1 for SAP BW Components</span></span>](microsoft-connector-for-sap-bw-components.md)  
 <span data-ttu-id="0bc84-120">SAP BW용 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1의 각 구성 요소를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0bc84-120">Describes each component of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span>  
  
 [<span data-ttu-id="0bc84-121">Microsoft Connector 1.1 for SAP BW F1 도움말</span><span class="sxs-lookup"><span data-stu-id="0bc84-121">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](microsoft-connector-for-sap-bw-f1-help.md)  
 <span data-ttu-id="0bc84-122">SAP BW용 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1의 각 구성 요소에 대한 사용자 인터페이스를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0bc84-122">Describes the user interface of each component of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span>  
  
  
