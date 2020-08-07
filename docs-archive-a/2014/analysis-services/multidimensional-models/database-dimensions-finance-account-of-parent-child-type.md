---
title: 부모-자식 유형 차원의 재무 계정 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], account
- account dimensions [Analysis Services]
- adding account intelligence
- account intelligence [Analysis Services]
ms.assetid: 2ba74e81-5b4b-407e-acdf-deb2f6accf0a
author: minewiskan
ms.author: owend
ms.openlocfilehash: ba10e642425628426d9183be2b8d2c4ff751c3ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731000"
---
# <a name="create-a-finance-account-of-parent-child-type-dimension"></a><span data-ttu-id="e1913-102">부모-자식 유형 차원의 재무 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="e1913-102">Create a Finance Account of parent-child type Dimension</span></span>
  <span data-ttu-id="e1913-103">에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 계정 유형 차원은 재무 보고용 계정 차트를 나타내는 특성이 있는 차원입니다.</span><span class="sxs-lookup"><span data-stu-id="e1913-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], an account type dimension is a dimension whose attributes represent a chart of accounts for financial reporting purposes.</span></span>  
  
 <span data-ttu-id="e1913-104">계정 차원을 사용하여 여러 계정에 대한 시간별 집계 동작을 선택적으로 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1913-104">An account dimension lets you selectively manage aggregation behavior across accounts over time.</span></span> <span data-ttu-id="e1913-105">또한 계정 차원을 통해 표준 메커니즘을 사용하여 재무 데이터를 처리하는 비즈니스 인텔리전스 솔루션에서 일반적으로 발생하는 비표준 집계 문제를 대부분 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1913-105">An account dimension also lets use a standard mechanism to resolve most of the nonstandard aggregation issues typically encountered in business intelligence solutions that handle financial data.</span></span> <span data-ttu-id="e1913-106">표준 메커니즘이 없는 경우 이러한 비표준 집계 문제를 해결하려면 사용자 지정 롤업 수식, 계산 멤버 또는 MDX(Multidimensional Expressions) 스크립트가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e1913-106">If you did not have such a standard mechanism, resolving these nonstandard aggregation issues would require custom rollup formulas, calculated members, or Multidimensional Expressions (MDX) scripts.</span></span>  
  
 <span data-ttu-id="e1913-107">차원을 계정 차원으로 식별하려면 차원의 `Type` 속성을 `Accounts`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e1913-107">To identify a dimension as an account dimension, set the `Type` property of the dimension to `Accounts`.</span></span>  
  
## <a name="dimension-structure"></a><span data-ttu-id="e1913-108">차원 구조</span><span class="sxs-lookup"><span data-stu-id="e1913-108">Dimension Structure</span></span>  
 <span data-ttu-id="e1913-109">계정 차원에는 다음과 같은 두 개의 필수 특성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1913-109">An account dimension contains, at least, two attributes:</span></span>  
  
-   <span data-ttu-id="e1913-110">키 특성-계정 차원에 대 한 차원 테이블의 개별 계정을 식별 하는 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="e1913-110">A key attribute-an attribute that identifies individual accounts in the dimension table for the account dimension.</span></span>  
  
-   <span data-ttu-id="e1913-111">계정 특성-계정 차원에서 계정이 계층적으로 정렬 되는 방법을 설명 하는 부모 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="e1913-111">An account attribute-a parent attribute that describes how accounts are hierarchically arranged in the account dimension.</span></span>  
  
     <span data-ttu-id="e1913-112">특성을 계정 특성으로 식별하려면 특성의 `Type` 속성을 `Account`로 설정하고 `Usage` 속성을 `Parent`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e1913-112">To identify an attribute as an account attribute, set the `Type` property of the attribute to `Account` and the `Usage` property to `Parent`.</span></span>  
  
 <span data-ttu-id="e1913-113">계정 차원에는 다음과 같은 선택적 특성이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1913-113">Account dimensions can optionally contain the following attributes:</span></span>  
  
-   <span data-ttu-id="e1913-114">계정 유형 특성-차원의 각 계정에 대 한 계정 유형을 정의 하는 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="e1913-114">An account type attribute-an attribute that defines the account type for each account in the dimension.</span></span> <span data-ttu-id="e1913-115">계정 유형 특성의 멤버 이름은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스나 프로젝트에 정의된 계정 유형에 매핑되고 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 이러한 계정에 사용되는 집계 함수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e1913-115">The member names of the account type attribute map to the account types defined for the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database or project, and indicate the aggregation function used by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] for those accounts.</span></span> <span data-ttu-id="e1913-116">단항 연산자나 사용자 지정 롤업 수식을 사용하여 계정 특성에 대한 집계 동작을 결정할 수도 있으나 계정 유형을 사용하면 기본 관계형 데이터베이스를 변경하지 않고도 계정 차트에 일관된 동작을 쉽게 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1913-116">You can also use unary operators or custom rollup formulas to determine aggregation behavior for account attributes, but account types let you to easily apply consistent behavior to a chart of accounts without requiring changes to the underlying relational database.</span></span>  
  
     <span data-ttu-id="e1913-117">계정 유형 특성을 식별하려면 특성의 `Type` 속성을 `AccountType`으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e1913-117">To identify an account type attribute, set the `Type` property of the attribute to `AccountType`.</span></span>  
  
-   <span data-ttu-id="e1913-118">계정 이름 특성-보고 목적으로 사용 되는 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="e1913-118">An account name attribute-an attribute that is used for reporting purposes.</span></span> <span data-ttu-id="e1913-119">특성의 `Type` 속성을 `AccountName`으로 설정하여 계정 이름 특성을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="e1913-119">You identify an account name attribute by setting the `Type` property of the attribute to `AccountName`.</span></span>  
  
-   <span data-ttu-id="e1913-120">계정 번호 특성-보고 목적으로 사용 되는 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="e1913-120">An account number attribute-an attribute that is used for reporting purposes.</span></span> <span data-ttu-id="e1913-121">특성의 `Type` 속성을 `AccountNumber`로 설정하여 계정 번호 특성을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="e1913-121">You identify an account number attribute by setting the `Type` property of the attribute to `AccountNumber`.</span></span>  
  
 <span data-ttu-id="e1913-122">특성 유형에 대한 자세한 내용은 [특성 유형 구성](attribute-properties-configure-attribute-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e1913-122">For more information about attribute types, see [Configure Attribute Types](attribute-properties-configure-attribute-types.md).</span></span>  
  
## <a name="adding-account-intelligence-with-the-business-intelligence-wizard"></a><span data-ttu-id="e1913-123">비즈니스 인텔리전스 마법사로 계정 인텔리전스 추가</span><span class="sxs-lookup"><span data-stu-id="e1913-123">Adding Account Intelligence with the Business Intelligence Wizard</span></span>  
 <span data-ttu-id="e1913-124">계정 차원을 정의하고 큐브에 추가한 후에는 비즈니스 인텔리전스 마법사를 사용하여 계정 유형을 식별하고 매핑하는 등의 계정 인텔리전스 기능을 차원에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1913-124">After you have defined an account dimension and added that dimension to a cube, you can use the Business Intelligence Wizard to adding account intelligence functionality, such as identifying and mapping account types, to the dimension.</span></span> <span data-ttu-id="e1913-125">자세한 내용은 [차원에 계정 인텔리전스 추가](bi-wizard-add-account-intelligence-to-a-dimension.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e1913-125">For more information, see [Add Account Intelligence to a Dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1913-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e1913-126">See Also</span></span>  
 <span data-ttu-id="e1913-127">[특성 및 특성 계층](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="e1913-127">[Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span></span>  
 <span data-ttu-id="e1913-128">[비즈니스 인텔리전스 마법사 F1 도움말](../business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="e1913-128">[Business Intelligence Wizard F1 Help](../business-intelligence-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="e1913-129">차원 유형</span><span class="sxs-lookup"><span data-stu-id="e1913-129">Dimension Types</span></span>](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)  
  
  
