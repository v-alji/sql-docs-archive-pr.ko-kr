---
title: 특성 계층에 대 한 (All) 수준 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- All members
- IsAggregatable property
- topmost levels [Analysis Services]
- (All) levels
- AttributeAllMemberName property
- levels [Analysis Services]
- members [Analysis Services], All
- AllMemberName property
ms.assetid: 0cb35e6f-b10f-483d-b893-78f6ca3979fd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9874a8c8a6861bc7d9e44271b089e8af3a4c0ae2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731004"
---
# <a name="configure-the-all-level-for-attribute-hierarchies"></a><span data-ttu-id="a6c08-102">특성 계층에 대해 (All) 수준 구성</span><span class="sxs-lookup"><span data-stu-id="a6c08-102">Configure the (All) Level for Attribute Hierarchies</span></span>
  <span data-ttu-id="a6c08-103">에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (All) 수준은 선택적인 시스템 생성 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="a6c08-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the (All) level is an optional, system-generated level.</span></span> <span data-ttu-id="a6c08-104">이 수준에는 바로 아래 종속되는 수준의 모든 멤버 값의 집계를 값으로 갖는 멤버 하나만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6c08-104">It contains only one member whose value is the aggregation of the values of all members in the immediately subordinate level.</span></span> <span data-ttu-id="a6c08-105">이 멤버를 All 멤버라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c08-105">This member is called the All member.</span></span> <span data-ttu-id="a6c08-106">All 멤버는 차원 테이블에 포함되지 않은 시스템 생성 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="a6c08-106">It is a system-generated member that is not contained in the dimension table.</span></span> <span data-ttu-id="a6c08-107">(All) 수준의 멤버는 계층의 맨 위에 있기 때문에 이 멤버의 값은 해당 계층의 모든 멤버 값을 통합하여 집계한 값입니다.</span><span class="sxs-lookup"><span data-stu-id="a6c08-107">Because the member in the (All) level is at the top of the hierarchy, the member's value is the consolidated aggregation of the values of all members in the hierarchy.</span></span> <span data-ttu-id="a6c08-108">All 멤버는 대개 계층의 기본 멤버 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c08-108">The All member often serves as the default member of a hierarchy.</span></span>  
  
 <span data-ttu-id="a6c08-109">특성 계층에서 (All) 수준의 존재는 특성에 대한 `IsAggregatable` 속성 설정에 따라 다르며 사용자 정의 계층에서 (All) 수준의 존재는 사용자 정의 계층의 최상위 수준에 있는 특성의 `IsAggregatable` 속성에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="a6c08-109">The presence of an (All) level in an attribute hierarchy depends on the `IsAggregatable` property setting for the attribute and the presence of an (All) level in a user-defined hierarchy depends on the `IsAggregatable` property of the attribute at the top-most level of user-defined hierarchy.</span></span> <span data-ttu-id="a6c08-110">`IsAggregatable` 속성이 `True`로 설정되어 있으면 (All) 수준이 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c08-110">If the `IsAggregatable` property is set to `True`, an (All) level will exist.</span></span> <span data-ttu-id="a6c08-111">`IsAggregatable` 속성이 `False`로 설정되어 있으면 계층에 (All) 수준이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a6c08-111">A hierarchy has no (All) level if the `IsAggregatable` property is set to `False`.</span></span>  
  
## <a name="establishing-the-topmost-level"></a><span data-ttu-id="a6c08-112">최상위 수준 설정</span><span class="sxs-lookup"><span data-stu-id="a6c08-112">Establishing the Topmost Level</span></span>  
 <span data-ttu-id="a6c08-113">계층에서 수준의 원본 특성에 `IsAggregatable` 속성이 `False`로 설정되어 있으면 계층에서 해당 수준 위에 집계할 수 있는 수준이 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a6c08-113">If the `IsAggregatable` property is set to `False` on the source attribute of a level in a hierarchy, then no aggregatable level can appear in the hierarchy above that level.</span></span> <span data-ttu-id="a6c08-114">집계할 수 없는 수준은 계층의 최상위 수준이어야 합니다. 또는 해당 수준 위의 모든 수준에 대한 원본 특성의 `IsAggregatable` 속성이 `False`로 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c08-114">A non-aggregatable level must be the topmost level of any hierarchy or the `IsAggregatable` property of the source attributes for any levels above it must also be set to `False`.</span></span>  
  
## <a name="all-member-and-all-level"></a><span data-ttu-id="a6c08-115">All 멤버 및 (All) 수준</span><span class="sxs-lookup"><span data-stu-id="a6c08-115">All Member and (All) Level</span></span>  
 <span data-ttu-id="a6c08-116">(All) 수준의 단일 멤버를 All 멤버라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c08-116">The single member of the (All) level is called the All member.</span></span> <span data-ttu-id="a6c08-117">`AttributeAllMemberName`차원의 속성은 차원의 특성에 대 한 All 멤버의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c08-117">The `AttributeAllMemberName`property on a dimension specifies the name of the All member for attributes in a dimension.</span></span> <span data-ttu-id="a6c08-118">계층의 `AllMemberName` 속성은 계층에 대한 All 멤버의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c08-118">The `AllMemberName` property on a hierarchy specifies the name of the All member for the hierarchy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6c08-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a6c08-119">See Also</span></span>  
 [<span data-ttu-id="a6c08-120">기본 멤버 정의</span><span class="sxs-lookup"><span data-stu-id="a6c08-120">Define a Default Member</span></span>](attribute-properties-define-a-default-member.md)  
  
  
