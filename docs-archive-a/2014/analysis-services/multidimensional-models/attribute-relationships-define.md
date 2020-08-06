---
title: 특성 관계 정의 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Analysis Services], relationships
- relationships [Analysis Services], attributes
ms.assetid: 9184d344-e96d-4025-ad6f-3f75129746df
author: minewiskan
ms.author: owend
ms.openlocfilehash: a694c68a55de2533c4ce7791d3be865008b6321f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646701"
---
# <a name="define-attribute-relationships"></a><span data-ttu-id="c8761-102">특성 관계 정의</span><span class="sxs-lookup"><span data-stu-id="c8761-102">Define Attribute Relationships</span></span>
  <span data-ttu-id="c8761-103">에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 특성은 차원의 기본 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c8761-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], attributes are the fundamental building block of a dimension.</span></span> <span data-ttu-id="c8761-104">차원은 특성 관계를 기반으로 구성되는 특성 집합을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c8761-104">A dimension contains a set of attributes that are organized based on attribute relationships.</span></span>  
  
 <span data-ttu-id="c8761-105">차원에 포함된 테이블마다 테이블의 키 특성을 해당 테이블의 다른 특성과 연결하는 특성 관계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8761-105">For each table included in a dimension, there is an attribute relationship that relates the table's key attribute to other attributes from that table.</span></span> <span data-ttu-id="c8761-106">이 관계는 차원을 만들 때 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8761-106">You create this relationship when you create the dimension.</span></span>  
  
 <span data-ttu-id="c8761-107">특성 관계의 이점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c8761-107">An attribute relationship provides the following advantages:</span></span>  
  
-   <span data-ttu-id="c8761-108">차원 처리에 필요한 메모리 양이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="c8761-108">Reduces the amount of memory needed for dimension processing.</span></span> <span data-ttu-id="c8761-109">따라서 차원, 파티션 및 쿼리 처리가 빨라집니다.</span><span class="sxs-lookup"><span data-stu-id="c8761-109">This speeds up dimension, partition, and query processing.</span></span>  
  
-   <span data-ttu-id="c8761-110">스토리지 액세스가 보다 빨라지고 실행 계획이 보다 최적화되므로 쿼리 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8761-110">Increases query performance because storage access is faster and execution plans are better optimized.</span></span>  
  
-   <span data-ttu-id="c8761-111">사용자 정의 계층이 관계 경로에 정의된 경우 집계 디자인 알고리즘에 따라 보다 효율적인 집계를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8761-111">Results in the selection of more effective aggregates by the aggregation design algorithms, provided that user-defined hierarchies have been defined along the relationship paths.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c8761-112">특성 관계 정의 및 구성의 중요도 및 의미에 대 한 자세한 내용은 [SQL Server 2005 Analysis Services 성능 가이드](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide)의 "쿼리 성능 향상" 섹션을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c8761-112">For more information about the importance and implications of defining and configuring attribute relationships, see the section, "Enhancing query performance," in the [SQL Server 2005 Analysis Services Performance Guide](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).</span></span>  
  
## <a name="attribute-relationship-considerations"></a><span data-ttu-id="c8761-113">특성 관계 고려 사항</span><span class="sxs-lookup"><span data-stu-id="c8761-113">Attribute Relationship Considerations</span></span>  
 <span data-ttu-id="c8761-114">기본 데이터가 특성 관계를 지원하는 경우 특성 간의 고유한 특성 관계도 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8761-114">When the underlying data supports it, you should also define unique attribute relationships between attributes.</span></span> <span data-ttu-id="c8761-115">고유한 특성 관계를 정의하려면 차원 디자이너의 **특성 관계** 탭을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="c8761-115">To define unique attribute relationships, use the **Attribute Relationships** tab of Dimension Designer.</span></span>  
  
 <span data-ttu-id="c8761-116">나가는 관계가 있는 특성에는 관련 특성에 대한 고유 키가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8761-116">Any attribute that has an outgoing relationship must have a unique key relative to its related attribute.</span></span> <span data-ttu-id="c8761-117">즉, 원본 특성의 멤버는 관련 특성의 멤버를 한 개만 식별해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8761-117">In other words, a member in a source attribute must identify one and only one member in a related attribute.</span></span> <span data-ttu-id="c8761-118">예를 들어 City -> State 관계를 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="c8761-118">For example, consider the relationship, City -> State.</span></span> <span data-ttu-id="c8761-119">이 관계에서 원본 특성은 City이고 관련 특성은 State입니다.</span><span class="sxs-lookup"><span data-stu-id="c8761-119">In this relationship, the source attribute is City and the related attribute is State.</span></span> <span data-ttu-id="c8761-120">원본 특성은 다 대 일 관계의 "다" 쪽 이며 관련 된 쪽은 "일" 쪽입니다.</span><span class="sxs-lookup"><span data-stu-id="c8761-120">The source attribute is the "many" side and the related side is the "one" side of the many-to-one relationship.</span></span> <span data-ttu-id="c8761-121">원본 특성에 대한 키는 City + State입니다.</span><span class="sxs-lookup"><span data-stu-id="c8761-121">The key for the source attribute would be City + State.</span></span> <span data-ttu-id="c8761-122">자세한 내용은 [특성 관계 만들기, 수정 또는 삭제](attribute-relationships-create-modify-or-delete-relationship.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c8761-122">For more information, see [Create, Modify, or Delete an Attribute Relationship](attribute-relationships-create-modify-or-delete-relationship.md).</span></span>  
  
 <span data-ttu-id="c8761-123">특성 관계의 속성에 대한 자세한 내용은 [특성 관계 속성 구성](attribute-relationships-configure-attribute-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c8761-123">For more information about properties of an attribute relationship, see [Configure Attribute Relationship Properties](attribute-relationships-configure-attribute-properties.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c8761-124">특성 관계를 잘못 정의하면 유효하지 않은 쿼리 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8761-124">Defining attribute relationships incorrectly can cause invalid query results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8761-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c8761-125">See Also</span></span>  
 [<span data-ttu-id="c8761-126">의 차원 디자이너에 있는 차원 구조 뷰의</span><span class="sxs-lookup"><span data-stu-id="c8761-126">Attribute Relationships</span></span>](../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)  
  
  
