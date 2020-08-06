---
title: 새 조건 만들기 또는 조건 열기 대화 상자, 일반 페이지 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.condition.f1
ms.assetid: 106954bf-e4ba-412b-9c1a-907d06153dcd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 72e4a77df553ac8e97609e82bd51c8fd93b64b23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661069"
---
# <a name="create-new-condition-or-open-condition-dialog-box-general-page"></a><span data-ttu-id="e90e9-102">새 조건 만들기 또는 조건 열기 대화 상자, 일반 페이지</span><span class="sxs-lookup"><span data-stu-id="e90e9-102">Create New Condition or Open Condition Dialog Box, General Page</span></span>
  <span data-ttu-id="e90e9-103">이 대화 상자를 사용하여 정책 기반 관리 조건을 만들거나 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e90e9-103">Use this dialog box to create or change a Policy-Based Management condition.</span></span> <span data-ttu-id="e90e9-104">조건은 패싯과 관련하여 정책 기반 관리로 관리되는 대상의 허용되는 상태 집합을 지정하는 부울 식입니다.</span><span class="sxs-lookup"><span data-stu-id="e90e9-104">A condition is a Boolean expression that specifies a set of allowed states of a Policy-Based Management managed target with regard to facets.</span></span> <span data-ttu-id="e90e9-105">**식/필드** 상자에서 선택할 수 있는 속성은 사용되는 패싯에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="e90e9-105">The properties that can be selected in the **Expression/Field** box depend upon the facet that is used.</span></span> <span data-ttu-id="e90e9-106">조건과 패싯 및 정책 간의 관계는 [정책 기반 관리를 사용하여 서버 관리](administer-servers-by-using-policy-based-management.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e90e9-106">For more information about how conditions relate to facets and policies, see [Administer Servers by Using Policy-Based Management](administer-servers-by-using-policy-based-management.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e90e9-107">옵션</span><span class="sxs-lookup"><span data-stu-id="e90e9-107">Options</span></span>  
 <span data-ttu-id="e90e9-108">**이름**</span><span class="sxs-lookup"><span data-stu-id="e90e9-108">**Name**</span></span>  
 <span data-ttu-id="e90e9-109">새 조건의 경우 새 조건 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e90e9-109">For a new condition, type the new condition name.</span></span> <span data-ttu-id="e90e9-110">기존 조건의 경우 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e90e9-110">For an existing condition, the name is displayed.</span></span>  
  
 <span data-ttu-id="e90e9-111">**패싯**</span><span class="sxs-lookup"><span data-stu-id="e90e9-111">**Facet**</span></span>  
 <span data-ttu-id="e90e9-112">이 조건에 사용되는 패싯입니다.</span><span class="sxs-lookup"><span data-stu-id="e90e9-112">The facet used by this condition.</span></span>  
  
 <span data-ttu-id="e90e9-113">**AndOr**</span><span class="sxs-lookup"><span data-stu-id="e90e9-113">**AndOr**</span></span>  
 <span data-ttu-id="e90e9-114">여러 식을 추가할 경우 식을 **And** 를 사용하여 조인할지, 아니면 **Or**를 사용하여 조인할지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e90e9-114">When you add multiple expressions, indicates whether the expressions should be joined by using **And** or **Or**.</span></span> <span data-ttu-id="e90e9-115">식이 하나만 있는 경우에는 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e90e9-115">Remains blank when there is only one expression.</span></span>  
  
 <span data-ttu-id="e90e9-116">**필드**</span><span class="sxs-lookup"><span data-stu-id="e90e9-116">**Field**</span></span>  
 <span data-ttu-id="e90e9-117">각 패싯은 설정할 수 있는 하나 이상의 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e90e9-117">Each facet exposes one or more properties that can be set.</span></span> <span data-ttu-id="e90e9-118">필드 상자에서 사용 가능한 속성 목록에 있는 속성을 선택하여 이 조건에 대한 식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e90e9-118">In the field box, select a property from the list of available properties to create an expression for this condition.</span></span>  
  
 <span data-ttu-id="e90e9-119">**연산자**</span><span class="sxs-lookup"><span data-stu-id="e90e9-119">**Operator**</span></span>  
 <span data-ttu-id="e90e9-120">이 식에 대한 비교 연산자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e90e9-120">Select a comparison operator for this expression.</span></span> <span data-ttu-id="e90e9-121">연산자는 =, !=, >, >=, <, <=, [NOT]LIKE, [NOT]IN과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e90e9-121">Operators are as follows: =, !=, >, >=, <, <=, [NOT]LIKE, [NOT]IN.</span></span> <span data-ttu-id="e90e9-122">일부 속성에서는 모든 연산자를 사용하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e90e9-122">Not all operators are available for some properties.</span></span>  
  
 <span data-ttu-id="e90e9-123">**값**</span><span class="sxs-lookup"><span data-stu-id="e90e9-123">**Value**</span></span>  
 <span data-ttu-id="e90e9-124">이 식에 대한 값 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="e90e9-124">The value setting for this expression.</span></span> <span data-ttu-id="e90e9-125">허용되는 값은 패싯에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="e90e9-125">The allowed values depend on the facet.</span></span> <span data-ttu-id="e90e9-126">값은 TRUE/FALSE, 문자열 또는 숫자일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e90e9-126">Values can be TRUE/FALSE, string, or numeric.</span></span> <span data-ttu-id="e90e9-127">문자열 값은 작은따옴표로 묶어야 합니다(예: **'AdventureWorks'**).</span><span class="sxs-lookup"><span data-stu-id="e90e9-127">String values must be enclosed in single quotation marks, for example: **'AdventureWorks'**.</span></span> <span data-ttu-id="e90e9-128">일부 속성에서는 모든 연산자를 사용하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e90e9-128">Not all operators are available for some properties.</span></span>  
  
## <a name="group-clauses"></a><span data-ttu-id="e90e9-129">절 그룹화</span><span class="sxs-lookup"><span data-stu-id="e90e9-129">Group Clauses</span></span>  
 <span data-ttu-id="e90e9-130">절을 그룹화하여 나머지 쿼리와 분리된 하나의 단위로 해당 절을 실행할 수 있습니다. 이는 수식이나 논리 문에서 식을 괄호로 묶는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e90e9-130">Clauses can be grouped to operate as a single unit separate from the rest of the query, just like putting parentheses around an expression in a mathematical equation or logic statement.</span></span> <span data-ttu-id="e90e9-131">절 그룹화는 복잡한 쿼리를 작성할 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="e90e9-131">Grouping clauses is useful when you are building complex queries.</span></span>  
  
 <span data-ttu-id="e90e9-132">**절을 그룹화하려면**</span><span class="sxs-lookup"><span data-stu-id="e90e9-132">**To group clauses**</span></span>  
  
-   <span data-ttu-id="e90e9-133">Shift 또는 Ctrl 키를 누른 다음 두 개 이상의 절을 클릭하여 범위를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e90e9-133">Press the SHIFT or CTRL keys, and then click two or more clauses to select a range.</span></span> <span data-ttu-id="e90e9-134">선택한 영역을 마우스 오른쪽 단추로 클릭한 다음 **절 그룹화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e90e9-134">Right-click the selected area, and then click **Group Clauses**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e90e9-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e90e9-135">See Also</span></span>  
 [<span data-ttu-id="e90e9-136">정책 기반 관리를 사용하여 서버 관리</span><span class="sxs-lookup"><span data-stu-id="e90e9-136">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
