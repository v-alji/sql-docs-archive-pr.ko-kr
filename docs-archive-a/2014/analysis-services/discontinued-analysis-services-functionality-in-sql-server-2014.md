---
title: SQL Server 2014에서 지원 되지 않는 Analysis Services 기능 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, backward compatibility
- SSAS, backward compatibility
- SQL Server Analysis Services, backward compatibility
- discontinued functionality [Analysis Services]
- unsupported features [Analysis Services]
ms.assetid: 39406be1-9819-4629-9c29-b32fb20bab2e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5414344eb65c907593c9077ee2ba5610b8b397c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660749"
---
# <a name="discontinued-analysis-services-functionality-in-sql-server-2014"></a><span data-ttu-id="e048e-102">SQL Server 2014에서 지원되지 않는 Analysis Services 기능</span><span class="sxs-lookup"><span data-stu-id="e048e-102">Discontinued Analysis Services Functionality in SQL Server 2014</span></span>
  <span data-ttu-id="e048e-103">이 항목에서는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서 더 이상 사용할 수 없는 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]기능에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e048e-103">This topic describes [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] features that are no longer available in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
## <a name="discontinued-features-in-sssql14"></a><span data-ttu-id="e048e-104">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e048e-104">Discontinued Features in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]</span></span>  
  
|<span data-ttu-id="e048e-105">범주</span><span class="sxs-lookup"><span data-stu-id="e048e-105">Category</span></span>|<span data-ttu-id="e048e-106">사용되지 않는 기능</span><span class="sxs-lookup"><span data-stu-id="e048e-106">Deprecated feature</span></span>|<span data-ttu-id="e048e-107">대체 기능</span><span class="sxs-lookup"><span data-stu-id="e048e-107">Replacement</span></span>|  
|--------------|------------------------|-----------------|  
|<span data-ttu-id="e048e-108">로컬 큐브</span><span class="sxs-lookup"><span data-stu-id="e048e-108">Local cubes</span></span>|<span data-ttu-id="e048e-109">InsertInto 연결 문자열 속성</span><span class="sxs-lookup"><span data-stu-id="e048e-109">InsertInto connection string property</span></span>|<span data-ttu-id="e048e-110">로컬 큐브를 채우기 위한 원래의 연결 문자열 구문이 Create Global Cube 문으로 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="e048e-110">Original connection string syntax for populating local cubes is replaced by the Create Global Cube statement.</span></span> <span data-ttu-id="e048e-111">자세한 내용은 [CREATE GLOBAL CUBE Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e048e-111">For more information, see [CREATE GLOBAL CUBE Statement  &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube).</span></span>|  
|<span data-ttu-id="e048e-112">로컬 큐브</span><span class="sxs-lookup"><span data-stu-id="e048e-112">Local cubes</span></span>|<span data-ttu-id="e048e-113">CreateCube 연결 문자열 속성</span><span class="sxs-lookup"><span data-stu-id="e048e-113">CreateCube connection string property</span></span>|<span data-ttu-id="e048e-114">로컬 큐브를 채우기 위한 원래의 연결 문자열 구문이 Create Global Cube 문으로 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="e048e-114">Original connection string syntax for populating local cubes is replaced by the Create Global Cube statement.</span></span> <span data-ttu-id="e048e-115">자세한 내용은 [CREATE GLOBAL CUBE Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e048e-115">For more information, see [CREATE GLOBAL CUBE Statement  &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube).</span></span>|  
|<span data-ttu-id="e048e-116">데이터 마이닝</span><span class="sxs-lookup"><span data-stu-id="e048e-116">Data Mining</span></span>|<span data-ttu-id="e048e-117">SQL Server 2000 PMML</span><span class="sxs-lookup"><span data-stu-id="e048e-117">SQL Server 2000 PMML</span></span>|<span data-ttu-id="e048e-118">SQL Server 2000 PMML 기능에서는 PMML 사양에서 사용할 수 없는 데이터 마이닝 알고리즘으로 제공된 고유 기능을 지원하기 위해 고유 확장 프로그램이 포함된 PMML 형식을 생성했습니다.</span><span class="sxs-lookup"><span data-stu-id="e048e-118">The SQL Server 2000 PMML feature produced a form of PMML that had proprietary extensions to support unique features provided by Data Mining algorithms that were not available in the PMML specification.</span></span> <span data-ttu-id="e048e-119">SQL Server 2005에서는 Analysis Services에서 PMML 기능이 새로운 PMML 2.1 표준으로 업데이트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e048e-119">In SQL Server 2005, Analysis Services updated the PMML feature to the newer PMML 2.1 standard.</span></span> <span data-ttu-id="e048e-120">따라서 SQL Server 2000에 추가된 고유 확장 프로그램은 이 버전에서도 계속 지원되지만 더 이상 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e048e-120">As a result, the proprietary extensions added in SQL Server 2000 are no longer needed, although they are still supported in this release.</span></span>|  
|<span data-ttu-id="e048e-121">MDX 문</span><span class="sxs-lookup"><span data-stu-id="e048e-121">MDX Statement</span></span>|<span data-ttu-id="e048e-122">Create Action 문</span><span class="sxs-lookup"><span data-stu-id="e048e-122">Create Action statement</span></span>|<span data-ttu-id="e048e-123">이 문은 이전 버전과의 호환성을 위해 포함되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e048e-123">This statement is included for backwards compatibility.</span></span> <span data-ttu-id="e048e-124">이 문은 동작 개체로 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="e048e-124">It is replaced by the Action object.</span></span> <span data-ttu-id="e048e-125">최신 버전의에서 작업을 만드는 방법에 대 한 자세한 내용은 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [작업 &#40;Analysis Services-다차원 데이터&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e048e-125">For more information about how to create actions in recent versions of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], see [Actions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md).</span></span>|  
  
## <a name="discontinued-features-in-previous-releases"></a><span data-ttu-id="e048e-126">이전 릴리스에서 지원되지 않는 기능</span><span class="sxs-lookup"><span data-stu-id="e048e-126">Discontinued Features in Previous Releases</span></span>  
 <span data-ttu-id="e048e-127">SQL Server 2000이 더 이상 지원되지 않으므로 SQL Server 2000 Analysis Services 데이터베이스를 새 버전으로 업그레이드하는 데 사용되었던 마이그레이션 마법사는 이제 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e048e-127">Migration Wizard, used to migrate SQL Server 2000 Analysis Services databases to newer versions, is discontinued because SQL Server 2000 is no longer supported.</span></span>  
  
 <span data-ttu-id="e048e-128">SQL Server 2000 Analysis Services 데이터베이스와의 호환성을 제공했던 DSO(의사 결정 지원 개체) 라이브러리도 지원되지 않으며 SQL Server에 더 이상 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e048e-128">Decision Support Objects (DSO) library that provided compatibility with SQL Server 2000 Analysis Services databases is also discontinued and no longer part of SQL Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e048e-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e048e-129">See Also</span></span>  
 [<span data-ttu-id="e048e-130">Analysis Services 이전 버전과의 호환성</span><span class="sxs-lookup"><span data-stu-id="e048e-130">Analysis Services Backward Compatibility</span></span>](analysis-services-backward-compatibility.md)  
  
  
