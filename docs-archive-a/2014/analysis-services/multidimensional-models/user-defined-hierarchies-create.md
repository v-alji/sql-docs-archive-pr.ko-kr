---
title: 사용자 정의 계층 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- user-defined hierarchies [Analysis Services]
ms.assetid: 16715b85-0630-4a8e-99b0-c0d213cade26
author: minewiskan
ms.author: owend
ms.openlocfilehash: 17e870a2b20125132342db1845689b7c2481d623
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732091"
---
# <a name="create-user-defined-hierarchies"></a><span data-ttu-id="74cb9-102">사용자 정의 계층 만들기</span><span class="sxs-lookup"><span data-stu-id="74cb9-102">Create User-Defined Hierarchies</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="74cb9-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]사용자 정의 계층을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74cb9-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] lets you create user-defined hierarchies.</span></span> <span data-ttu-id="74cb9-104">계층은 특성을 기반으로 하는 수준 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="74cb9-104">A hierarchy is a collection of levels based on attributes.</span></span> <span data-ttu-id="74cb9-105">예를 들어 시간 계층에는 년, 분기, 월, 주 및 일 수준이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74cb9-105">For example, a time hierarchy might contain the Year, Quarter, Month, Week, and Day levels.</span></span> <span data-ttu-id="74cb9-106">각 멤버 특성이 상위 멤버 특성을 고유하게 내재하고 있는 계층도 있는데</span><span class="sxs-lookup"><span data-stu-id="74cb9-106">In some hierarchies, each member attribute uniquely implies the member attribute above it.</span></span> <span data-ttu-id="74cb9-107">이를 자연 계층이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="74cb9-107">This is sometimes referred to as a natural hierarchy.</span></span> <span data-ttu-id="74cb9-108">최종 사용자가 계층을 사용하여 큐브 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74cb9-108">A hierarchy can be used by end users to browse cube data.</span></span> <span data-ttu-id="74cb9-109">계층은 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 차원 디자이너의 계층 창을 사용하여 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="74cb9-109">Define hierarchies by using the Hierarchies pane of Dimension Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="74cb9-110">사용자 정의 계층 구조를 만들 때 *비정형*계층 구조가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74cb9-110">When you create a user-defined hierarchy, the hierarchy might become *ragged*.</span></span> <span data-ttu-id="74cb9-111">비정형 계층에서는 최소한 한 멤버의 논리적 부모 멤버가 해당 멤버 바로 위 수준에 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="74cb9-111">A ragged hierarchy is where the logical parent member of at least one member is not in the level immediately above the member.</span></span> <span data-ttu-id="74cb9-112">비정형 계층일 경우 누락된 멤버 표시 여부와 누락된 멤버 표시 방법을 제어하는 설정이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74cb9-112">If you have a ragged hierarchy, there are settings that control whether the missing members are visible and how to display the missing members.</span></span> <span data-ttu-id="74cb9-113">자세한 내용은 [비정형 계층 구조](user-defined-hierarchies-ragged-hierarchies.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="74cb9-113">For more information, see [Ragged Hierarchies](user-defined-hierarchies-ragged-hierarchies.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="74cb9-114">사용자 정의 계층 구조의 디자인 및 구성과 관련된 성능 문제에 대한 자세한 내용은 [SQL Server 2005 Analysis Services Performance Guide](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide)(SQL Server 2005 Analysis Services 성능 가이드)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="74cb9-114">For more information about performance issues related to the design and configuration of user-defined hierarchies, see the [SQL Server 2005 Analysis Services Performance Guide](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74cb9-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="74cb9-115">See Also</span></span>  
 <span data-ttu-id="74cb9-116">[사용자 계층 속성](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md) </span><span class="sxs-lookup"><span data-stu-id="74cb9-116">[User Hierarchy Properties](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md) </span></span>  
 <span data-ttu-id="74cb9-117">[수준 속성 &#91;Paved Over&#93;](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md) </span><span class="sxs-lookup"><span data-stu-id="74cb9-117">[Level Properties &#91;Paved Over&#93;](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md) </span></span>  
 [<span data-ttu-id="74cb9-118">부모-자식 계층</span><span class="sxs-lookup"><span data-stu-id="74cb9-118">Parent-Child Hierarchy</span></span>](parent-child-dimension.md)  
  
  
