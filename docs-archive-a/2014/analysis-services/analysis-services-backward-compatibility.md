---
title: Analysis Services 이전 버전과의 호환성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- installing Analysis Services, backward compatibility
- backward compatibility [Analysis Services]
- compatibility [Analysis Services]
- Analysis Services, backward compatibility
- upgrading Analysis Services
- SSAS, backward compatibility
- SQL Server Analysis Services, backward compatibility
ms.assetid: 618b6c3a-e20d-47a9-b2c6-6d848dfba05a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44a5296bfbd2bae746eb9936d416fd696de16cb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648212"
---
# <a name="analysis-services-backward-compatibility"></a><span data-ttu-id="4dde7-102">Analysis Services 이전 버전과의 호환성</span><span class="sxs-lookup"><span data-stu-id="4dde7-102">Analysis Services Backward Compatibility</span></span>
  <span data-ttu-id="4dde7-103">이 섹션의 항목에서는 버전 간의 변경 된 동작에 대해 설명 합니다 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4dde7-103">The topics in this section describe the changes in behavior between versions of  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4dde7-104">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="4dde7-104">In This Section</span></span>  
  
|<span data-ttu-id="4dde7-105">토픽</span><span class="sxs-lookup"><span data-stu-id="4dde7-105">Topics</span></span>|<span data-ttu-id="4dde7-106">Description</span><span class="sxs-lookup"><span data-stu-id="4dde7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4dde7-107">SQL Server 2014에서 사용 되지 않는 Analysis Services 기능</span><span class="sxs-lookup"><span data-stu-id="4dde7-107">Deprecated Analysis Services Features in SQL Server 2014</span></span>](deprecated-analysis-services-features-in-sql-server-2014.md)|<span data-ttu-id="4dde7-108">이전 버전과의 호환성을 위해 현재 버전에 유지되었지만 나중 버전의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서는 제거될 기능을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4dde7-108">Describes features that have been retained in the current version to maintain backward compatibility,  but which will be removed in a future version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="4dde7-109">SQL Server 2014에서 지원되지 않는 Analysis Services 기능</span><span class="sxs-lookup"><span data-stu-id="4dde7-109">Discontinued Analysis Services Functionality in SQL Server 2014</span></span>](discontinued-analysis-services-functionality-in-sql-server-2014.md)|<span data-ttu-id="4dde7-110">이전 버전의  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에는 있지만 나중 버전에서 제거된 기능을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4dde7-110">Describes features that existed in earlier versions of  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] but that have since been removed in later versions.</span></span>|  
|[<span data-ttu-id="4dde7-111">SQL Server 2014에서 Analysis Services 기능의 주요 변경 내용</span><span class="sxs-lookup"><span data-stu-id="4dde7-111">Breaking Changes to Analysis Services Features in SQL Server 2014</span></span>](breaking-changes-to-analysis-services-features-in-sql-server-2014.md)|<span data-ttu-id="4dde7-112">이 릴리스의 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에 도입되어 잠재적으로 모델을 손상할 수 있는 코드 변경 내용 또는 이전 버전의 소프트웨어에서 만든 스크립트 또는 사용자 지정 애플리케이션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4dde7-112">Describes code changes introduced in this release of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that could potentially break a model or custom applications or script created in previous versions of the software .</span></span>|  
|[<span data-ttu-id="4dde7-113">SQL Server 2014 Analysis Services 기능의 동작 변경 내용</span><span class="sxs-lookup"><span data-stu-id="4dde7-113">Behavior Changes to Analysis Services Features in SQL Server 2014</span></span>](behavior-changes-to-analysis-services-features-in-sql-server-2014.md)|<span data-ttu-id="4dde7-114">이 릴리스에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서 동작이 다른 기존 기능에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4dde7-114">Describes existing features that have different behaviors in this release of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="4dde7-115">일반적인 예로 기본값을 새 값이나 다른 값으로 변경, 이전에 허용되던 작업 또는 구성 허용 안 함, 업그레이드 중 손실된 설정 또는 구성을 수동으로 변경하거나 바꾸어야 하는 요구 사항 도입 등을 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dde7-115">Common examples include changing a default to a new or different value, disallowing a previously allowable operation or configuration, or a introducing a requirement to manually revise or replace a setting or configuration that is lost during upgrade.</span></span><br /> <span data-ttu-id="4dde7-116">.</span><span class="sxs-lookup"><span data-stu-id="4dde7-116">.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4dde7-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4dde7-117">See Also</span></span>  
 <span data-ttu-id="4dde7-118">[Analysis Services 및 비즈니스 인텔리전스의 새로운 기능](what-s-new-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="4dde7-118">[What's New in Analysis Services and Business Intelligence](what-s-new-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="4dde7-119">Analysis Services 업그레이드</span><span class="sxs-lookup"><span data-stu-id="4dde7-119">Upgrade Analysis Services</span></span>](../database-engine/install-windows/upgrade-analysis-services.md)  
  
  
