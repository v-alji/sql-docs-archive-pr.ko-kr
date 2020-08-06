---
title: 데이터 마이닝 아키텍처 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 105f52e1-ad3b-4cd0-b67b-06dbb451c304
author: minewiskan
ms.author: owend
ms.openlocfilehash: a372972fd7fa39f7bcfd2e10abbc4fbf8f8c10aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659737"
---
# <a name="data-mining-architecture"></a><span data-ttu-id="a9e28-102">데이터 마이닝 아키텍처</span><span class="sxs-lookup"><span data-stu-id="a9e28-102">Data Mining Architecture</span></span>
  <span data-ttu-id="a9e28-103">이 섹션에서는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]인스턴스에서 호스팅되는 데이터 마이닝 솔루션의 아키텍처에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a9e28-103">This section describes the architecture of data mining solutions that are hosted in an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="a9e28-104">이 섹션의 항목에서는 데이터 마이닝을 지원하는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스의 논리적 아키텍처와 물리적 아키텍처에 대해 설명하고, 데이터 마이닝 서버와 통신하는 데 사용하고 데이터 마이닝 개체에 대해 로컬 또는 원격으로 작업하는 데 사용할 수 있는 프로토콜, 클라이언트 및 공급자에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a9e28-104">The topics in this section describe the logical and physical architecture of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance that supports data mining, and also provide information about the clients, providers, and protocols that can be used to communicate with data mining servers, and to work with data mining objects either locally or remotely.</span></span>  
  
 <span data-ttu-id="a9e28-105">일반적으로 SQL Server 데이터 마이닝은 다차원 모드에서 실행 중인 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스의 일부로 제공되는 서비스로 작동하기 때문에 온라인 설명서에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 다차원 솔루션의 작업, 유지 관리 및 구성에 대해 설명하는 다음과 같은 섹션도 검토하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a9e28-105">In general, SQL Server Data Mining operates as a service that is provided as part of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance running in multidimensional mode; therefore, we recommend that you also review the following sections of Books Online that describe the operation, maintenance, and configuration of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] multidimensional solutions.</span></span>  
  
 [<span data-ttu-id="a9e28-106">다차원 모델 개체 처리</span><span class="sxs-lookup"><span data-stu-id="a9e28-106">Multidimensional Model Object Processing</span></span>](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)  
  
 [<span data-ttu-id="a9e28-107">Analysis Services에 연결</span><span class="sxs-lookup"><span data-stu-id="a9e28-107">Connect to Analysis Services</span></span>](../instances/connect-to-analysis-services.md)  
  
 [<span data-ttu-id="a9e28-108">데이터베이스 스토리지 위치</span><span class="sxs-lookup"><span data-stu-id="a9e28-108">Database Storage Location</span></span>](../multidimensional-models/database-storage-location.md)  
  
 [<span data-ttu-id="a9e28-109">ReadOnly 모드와 ReadWrite 모드 간 Analysis Services 데이터베이스 전환</span><span class="sxs-lookup"><span data-stu-id="a9e28-109">Switch an Analysis Services database between ReadOnly and ReadWrite modes</span></span>](../multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
 <span data-ttu-id="a9e28-110">비즈니스 인텔리전스 솔루션에서 데이터 마이닝을 구현하는 방법은 MSDN Library의 솔루션 가이드를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a9e28-110">For more information about how you can implement data mining in your business intelligence solution, see the Solution Guides section of the MSDN Library.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a9e28-111">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="a9e28-111">In This Section</span></span>  
 [<span data-ttu-id="a9e28-112">논리적 아키텍처&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="a9e28-112">Logical Architecture &#40;Analysis Services - Data Mining&#41;</span></span>](logical-architecture-analysis-services-data-mining.md)  
  
 [<span data-ttu-id="a9e28-113">물리적 아키텍처&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="a9e28-113">Physical Architecture &#40;Analysis Services - Data Mining&#41;</span></span>](physical-architecture-analysis-services-data-mining.md)  
  
 [<span data-ttu-id="a9e28-114">데이터 마이닝 서비스 및 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="a9e28-114">Data Mining Services and Data Sources</span></span>](data-mining-services-and-data-sources.md)  
  
 [<span data-ttu-id="a9e28-115">데이터 마이닝 솔루션 및 개체 관리</span><span class="sxs-lookup"><span data-stu-id="a9e28-115">Management of Data Mining Solutions and Objects</span></span>](management-of-data-mining-solutions-and-objects.md)  
  
 [<span data-ttu-id="a9e28-116">보안 개요&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="a9e28-116">Security Overview &#40;Data Mining&#41;</span></span>](security-overview-data-mining.md)  
  
## <a name="see-also"></a><span data-ttu-id="a9e28-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a9e28-117">See Also</span></span>  
 <span data-ttu-id="a9e28-118">[다차원 모델 프로그래밍](../multidimensional-models/multidimensional-model-programming.md) </span><span class="sxs-lookup"><span data-stu-id="a9e28-118">[Multidimensional Model Programming](../multidimensional-models/multidimensional-model-programming.md) </span></span>  
 [<span data-ttu-id="a9e28-119">데이터 마이닝 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="a9e28-119">Data Mining Programming</span></span>](../dev-guide/data-mining-programming.md)  
  
  
