---
title: Microsoft OLAP 아키텍처 이해 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- multidimensional data [Analysis Services], about multidimensional data
ms.assetid: a2eaaee8-7b06-48af-ba44-e21a3678c4c4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1abbbbd7c2f7caa99407bbcd17ace07deac5dfeb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652406"
---
# <a name="understanding-microsoft-olap-architecture"></a><span data-ttu-id="46b9a-102">Microsoft OLAP 아키텍처 이해</span><span class="sxs-lookup"><span data-stu-id="46b9a-102">Understanding Microsoft OLAP Architecture</span></span>
  <span data-ttu-id="46b9a-103">다음 항목을 통해 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 다차원 데이터베이스를 더 잘 이해하고 비즈니스 인텔리전스 솔루션에서 다차원 데이터베이스를 구현하는 방법을 계획할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46b9a-103">Use these topics to better understand [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] multidimensional databases and plan how to implement multidimensional databases in your business intelligence solution.</span></span>  
  
 <span data-ttu-id="46b9a-104">![작은 파일 폴더 아이콘](../../../integration-services/media/filefolder-small.gif "작은 파일 폴더 아이콘") **논리적 아키텍처**</span><span class="sxs-lookup"><span data-stu-id="46b9a-104">![Small File Folder Icon](../../../integration-services/media/filefolder-small.gif "Small File Folder Icon") **Logical Architecture**</span></span>  
 [<span data-ttu-id="46b9a-105">서버 개체 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="46b9a-105">Server Objects &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../olap-logical/server-objects-analysis-services-multidimensional-data.md)  
  
 [<span data-ttu-id="46b9a-106">차원 개체 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="46b9a-106">Dimension Objects &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../../multidimensional-models-olap-logical-dimension-objects/dimension-objects-analysis-services-multidimensional-data.md)  
  
 [<span data-ttu-id="46b9a-107">큐브 개체는 Analysis Services 다차원 데이터를 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="46b9a-107">Cube Objects &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../../multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
 [<span data-ttu-id="46b9a-108">자세히 ...</span><span class="sxs-lookup"><span data-stu-id="46b9a-108">More...</span></span>](../olap-logical/understanding-microsoft-olap-logical-architecture.md)  
  
 <span data-ttu-id="46b9a-109">![작은 파일 폴더 아이콘](../../../integration-services/media/filefolder-small.gif "작은 파일 폴더 아이콘") **실제 아키텍처**</span><span class="sxs-lookup"><span data-stu-id="46b9a-109">![Small File Folder Icon](../../../integration-services/media/filefolder-small.gif "Small File Folder Icon") **Physical Architecture**</span></span>  
 [<span data-ttu-id="46b9a-110">OLAP 엔진 서버 구성 요소</span><span class="sxs-lookup"><span data-stu-id="46b9a-110">OLAP Engine Server Components</span></span>](olap-engine-server-components.md)  
  
 [<span data-ttu-id="46b9a-111">로컬 큐브 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="46b9a-111">Local Cubes &#40;Analysis Services - Multidimensional Data&#41;</span></span>](local-cubes-analysis-services-multidimensional-data.md)  
  
 [<span data-ttu-id="46b9a-112">자세히 ...</span><span class="sxs-lookup"><span data-stu-id="46b9a-112">More...</span></span>](understanding-microsoft-olap-physical-architecture.md)  
  
 <span data-ttu-id="46b9a-113">![작은 파일 폴더 아이콘](../../../integration-services/media/filefolder-small.gif "작은 파일 폴더 아이콘") **프로그래밍 아키텍처**</span><span class="sxs-lookup"><span data-stu-id="46b9a-113">![Small File Folder Icon](../../../integration-services/media/filefolder-small.gif "Small File Folder Icon") **Programming Architecture**</span></span>  
 [<span data-ttu-id="46b9a-114">AMO&#40;Analysis Management Objects&#41;를 사용하여 개발</span><span class="sxs-lookup"><span data-stu-id="46b9a-114">Developing with Analysis Management Objects &#40;AMO&#41;</span></span>](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)  
  
 [<span data-ttu-id="46b9a-115">ASSL&#40;Analysis Services Scripting Language&#41;을 사용하여 개발</span><span class="sxs-lookup"><span data-stu-id="46b9a-115">Developing with Analysis Services Scripting Language &#40;ASSL&#41;</span></span>](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
  
 [<span data-ttu-id="46b9a-116">ADOMD.NET를 사용하여 개발</span><span class="sxs-lookup"><span data-stu-id="46b9a-116">Developing with ADOMD.NET</span></span>](https://docs.microsoft.com/bi-reference/adomd/developing-with-adomd-net)  
  
 <span data-ttu-id="46b9a-117">![작은 파일 폴더 아이콘](../../../integration-services/media/filefolder-small.gif "작은 파일 폴더 아이콘") **국가별 고려 사항**</span><span class="sxs-lookup"><span data-stu-id="46b9a-117">![Small File Folder Icon](../../../integration-services/media/filefolder-small.gif "Small File Folder Icon") **International Considerations**</span></span>  
 [<span data-ttu-id="46b9a-118">Analysis Services 다차원에 대한 세계화 시나리오</span><span class="sxs-lookup"><span data-stu-id="46b9a-118">Globalization scenarios for Analysis Services Multiidimensional</span></span>](../../globalization-scenarios-for-analysis-services-multiidimensional.md)  
  
## <a name="see-also"></a><span data-ttu-id="46b9a-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="46b9a-119">See Also</span></span>  
 [<span data-ttu-id="46b9a-120">SSAS&#41;&#40;기술 참조</span><span class="sxs-lookup"><span data-stu-id="46b9a-120">Technical Reference &#40;SSAS&#41;</span></span>](../../powershell/technical-reference-ssas.md)  
  
  
