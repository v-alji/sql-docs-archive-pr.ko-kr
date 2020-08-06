---
title: Reporting Services 이전 버전과의 호환성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- SSRS, backward compatibility
- SQL Server Reporting Services, backward compatibility
- backward compatibility [Reporting Services]
ms.assetid: 675b0e0e-cfee-4790-9675-80fc3ea6d30f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7203740ba7f52dfc2cd3793a20fed9fecf5f9468
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734980"
---
# <a name="reporting-services-backward-compatibility"></a><span data-ttu-id="fa147-102">Reporting Services의 이전 버전과의 호환성</span><span class="sxs-lookup"><span data-stu-id="fa147-102">Reporting Services Backward Compatibility</span></span>
  <span data-ttu-id="fa147-103">이 섹션에서는 버전 간의 변경 된 동작에 대해 설명 합니다 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="fa147-103">This section describes changes in behavior between versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="fa147-104">더 이상 사용되지 않거나 후속 릴리스에서 제거될 예정인 기능을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="fa147-104">It covers features that are no longer available or are scheduled to be removed in a future release.</span></span> <span data-ttu-id="fa147-105">또한 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 기능을 포함하는 사용자 지정 애플리케이션의 작동을 중단시키는 것으로 알려진 근본적인 제품 변경 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fa147-105">It also describes fundamental changes to the product that are known to break a custom application that includes [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fa147-106">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="fa147-106">In This Section</span></span>  
  
|<span data-ttu-id="fa147-107">항목</span><span class="sxs-lookup"><span data-stu-id="fa147-107">Topic</span></span>|<span data-ttu-id="fa147-108">Description</span><span class="sxs-lookup"><span data-stu-id="fa147-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="fa147-109">SQL Server 2014의 SQL Server Reporting Services에서 중단된 기능</span><span class="sxs-lookup"><span data-stu-id="fa147-109">Discontinued Functionality to SQL Server Reporting Services in SQL Server 2014</span></span>](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)|<span data-ttu-id="fa147-110">이전 버전의 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 에는 있지만 나중 버전에서 제거된 기능을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fa147-110">Describes features that existed in earlier versions of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] but that have been removed in later versions.</span></span>|  
|[<span data-ttu-id="fa147-111">SQL Server 2014의 SQL Server Reporting Services에서 지원되지 않는 기능</span><span class="sxs-lookup"><span data-stu-id="fa147-111">Deprecated Features in SQL Server Reporting Services in SQL Server 2014</span></span>](deprecated-features-in-sql-server-reporting-services-ssrs.md)|<span data-ttu-id="fa147-112">이전 버전과의 호환성을 위해 이 버전의 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 에 유지되었지만 나중 버전의 SQL Server에서는 제거될 기능을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fa147-112">Describes features that exist this release of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] for backward compatibility, but which will be removed in a future version of SQL Server.</span></span>|  
|[<span data-ttu-id="fa147-113">SQL Server 2014에서 SQL Server Reporting Services의 주요 변경 내용</span><span class="sxs-lookup"><span data-stu-id="fa147-113">Breaking Changes in SQL Server Reporting Services in SQL Server 2014</span></span>](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)|<span data-ttu-id="fa147-114">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]로 업그레이드할 때 발생할 수 있는 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fa147-114">Describes issues that you might encounter when you upgrade [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="fa147-115">SQL Server 2014에서 SQL Server Reporting Services의 동작 변경 내용</span><span class="sxs-lookup"><span data-stu-id="fa147-115">Behavior Changes to SQL Server Reporting Services  in SQL Server 2014</span></span>](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)|<span data-ttu-id="fa147-116">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]에서 변경된 기능을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fa147-116">Describes features that have changed in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fa147-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fa147-117">See Also</span></span>  
 <span data-ttu-id="fa147-118">[이전 버전과의 호환성](../../2014/getting-started/backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="fa147-118">[Backward Compatibility](../../2014/getting-started/backward-compatibility.md) </span></span>  
 [<span data-ttu-id="fa147-119">Analysis Services 이전 버전과의 호환성</span><span class="sxs-lookup"><span data-stu-id="fa147-119">Analysis Services Backward Compatibility</span></span>](../../2014/analysis-services/analysis-services-backward-compatibility.md)  
  
  
