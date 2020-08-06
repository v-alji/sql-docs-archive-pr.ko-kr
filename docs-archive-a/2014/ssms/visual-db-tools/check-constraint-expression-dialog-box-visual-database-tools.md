---
title: CHECK 제약 조건 식 대화 상자(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.checkconstraintexpression
ms.assetid: beb6ce43-3913-4d66-8826-8e885335b790
author: stevestein
ms.author: sstein
ms.openlocfilehash: 38268d4e49a9c674c100bc22c0782e3e61477967
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638503"
---
# <a name="check-constraint-expression-dialog-box-visual-database-tools"></a><span data-ttu-id="6c883-102">CHECK 제약 조건 식 대화 상자(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="6c883-102">Check Constraint Expression Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="6c883-103">CHECK 제약 조건을 테이블이나 열에 연결하려면 SQL 식을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-103">When you attach a check constraint to a table or column, you must include an SQL expression.</span></span> <span data-ttu-id="6c883-104">제공된 입력란에 CHECK 제약 조건 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-104">Type the check constraint expression in the box provided.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="6c883-105">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="6c883-105">UI element list</span></span>  
 <span data-ttu-id="6c883-106">식</span><span class="sxs-lookup"><span data-stu-id="6c883-106">Expression</span></span>  
 <span data-ttu-id="6c883-107">식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-107">Enter the expression</span></span>  
  
 <span data-ttu-id="6c883-108">간단한 조건에 대한 데이터를 검사하기 위한 간단한 제약 조건 식을 만들거나 여러 조건에 대한 데이터를 검사하기 위한 복잡한 식을 부울 연산자를 사용하여 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-108">You can create a simple constraint expression to check data for a simple condition; or you can create a complex expression, using Boolean operators, to check data for several conditions.</span></span> <span data-ttu-id="6c883-109">예를 들어 authors 테이블에 zip 열이 있고, 이 열에 5자리 문자로 구성된 문자열이 필요한 경우를 가정해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-109">For example, suppose the authors table has a zip column where a 5-digit character string is required.</span></span> <span data-ttu-id="6c883-110">다음과 같은 제약 조건 식을 사용하면 5자리 수만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-110">This sample constraint expression guarantees that only 5-digit numbers are allowed:</span></span>  
  
```  
zip LIKE '[0-9][0-9][0-9][0-9][0-9]'  
```  
  
 <span data-ttu-id="6c883-111">또는 sales 테이블에 qty라는 열이 있고, 이 열에 0보다 큰 값이 필요한 경우를 가정해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-111">Or suppose the sales table has a column called qty which requires a value greater than 0.</span></span> <span data-ttu-id="6c883-112">다음 예제와 같은 제약 조건을 사용하면 양수 값만 허용되도록 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-112">This sample constraint guarantees that only positive values are allowed:</span></span>  
  
```  
qty > 0  
```  
  
 <span data-ttu-id="6c883-113">또는 orders 테이블에서 모든 신용 카드 주문에 허용되는 신용 카드의 종류를 제한하는 경우를 가정해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-113">Or suppose the orders table limits the type of credit cards accepted for all credit card orders.</span></span> <span data-ttu-id="6c883-114">다음과 같은 제약 조건을 사용하면 신용 카드로 주문하는 경우 Visa, MasterCard 또는 American Express만 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-114">This sample constraint guarantees that if the order is placed on a credit card, then only Visa, MasterCard, or American Express is accepted:</span></span>  
  
```  
NOT (payment_method = 'credit card') OR  
   (card_type IN ('VISA', 'MASTERCARD', 'AMERICAN EXPRESS'))  
```  
  
## <a name="to-define-a-constraint-expression"></a><span data-ttu-id="6c883-115">제약 조건 식을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="6c883-115">To define a constraint expression</span></span>  
 <span data-ttu-id="6c883-116">속성 페이지의 CHECK 제약 조건 탭에서 다음 구문을 사용하여 제약 조건 식 상자에 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-116">In the Check Constraints tab of the property pages, type an expression in the Constraint expression box using the following syntax:</span></span>  
  
 `{constant | column_name | function | (subquery)}`  
  
 `[{operator | AND | OR | NOT}`  
  
 `{constant | column_name | function | (subquery)}...]`  
  
 <span data-ttu-id="6c883-117">이 SQL 구문은 다음 매개 변수로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-117">The SQL syntax is made up of the following parameters:</span></span>  
  
|<span data-ttu-id="6c883-118">매개 변수</span><span class="sxs-lookup"><span data-stu-id="6c883-118">Parameter</span></span>|<span data-ttu-id="6c883-119">Description</span><span class="sxs-lookup"><span data-stu-id="6c883-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6c883-120">constant</span><span class="sxs-lookup"><span data-stu-id="6c883-120">constant</span></span>|<span data-ttu-id="6c883-121">숫자 또는 문자 데이터 같은 리터럴 값입니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-121">A literal value, such as numeric or character data.</span></span> <span data-ttu-id="6c883-122">문자 데이터는 작은따옴표(')로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-122">Character data must be enclosed within single quotation marks (').</span></span>|  
|<span data-ttu-id="6c883-123">column_name</span><span class="sxs-lookup"><span data-stu-id="6c883-123">column_name</span></span>|<span data-ttu-id="6c883-124">열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-124">Specifies a column.</span></span>|  
|<span data-ttu-id="6c883-125">function</span><span class="sxs-lookup"><span data-stu-id="6c883-125">function</span></span>|<span data-ttu-id="6c883-126">기본 제공 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-126">A built-in function.</span></span>|  
|<span data-ttu-id="6c883-127">operator</span><span class="sxs-lookup"><span data-stu-id="6c883-127">operator</span></span>|<span data-ttu-id="6c883-128">산술 연산자, 비트 연산자, 비교 연산자 또는 문자열 연산자입니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-128">Arithmetic, bitwise, comparison, or string operators.</span></span>|  
|<span data-ttu-id="6c883-129">AND</span><span class="sxs-lookup"><span data-stu-id="6c883-129">AND</span></span>|<span data-ttu-id="6c883-130">두 식을 연결하기 위해 부울 식에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-130">Use in Boolean expressions to connect two expressions.</span></span> <span data-ttu-id="6c883-131">두 식이 모두 참인 경우에 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-131">Results are returned when both expressions are true.</span></span><br /><br /> <span data-ttu-id="6c883-132">문 하나에 AND와 OR를 모두 사용하는 경우 AND가 먼저 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-132">When AND and OR are both used in a statement, AND is processed first.</span></span> <span data-ttu-id="6c883-133">계산 순서를 변경하려면 괄호를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-133">You can change the order of execution by using parentheses.</span></span>|  
|<span data-ttu-id="6c883-134">또는</span><span class="sxs-lookup"><span data-stu-id="6c883-134">OR</span></span>|<span data-ttu-id="6c883-135">여러 조건을 연결하기 위해 부울 식에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-135">Use in Boolean expressions to connect two or more conditions.</span></span> <span data-ttu-id="6c883-136">한 조건이라도 참이면 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-136">Results are returned when either condition is true.</span></span><br /><br /> <span data-ttu-id="6c883-137">문 하나에 AND와 OR를 모두 사용하는 경우 OR는 AND보다 늦게 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-137">When AND and OR are both used in a statement, OR is evaluated after AND.</span></span> <span data-ttu-id="6c883-138">계산 순서를 변경하려면 괄호를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-138">You can change the order of execution by using parentheses.</span></span>|  
|<span data-ttu-id="6c883-139">NOT</span><span class="sxs-lookup"><span data-stu-id="6c883-139">NOT</span></span>|<span data-ttu-id="6c883-140">모든 부울 식을 부정합니다. 여기에는 LIKE, NULL, BETWEEN, IN 및 EXISTS 등과 같은 키워드가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-140">Negates any Boolean expression (which can include keywords, such as LIKE, NULL, BETWEEN, IN, and EXISTS).</span></span><br /><br /> <span data-ttu-id="6c883-141">문 하나에 논리 연산자를 두 개 이상 사용하는 경우 NOT은 제일 먼저 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-141">When more than one logical operator is used in a statement, NOT is processed first.</span></span> <span data-ttu-id="6c883-142">계산 순서를 변경하려면 괄호를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6c883-142">You can change the order of execution by using parentheses.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6c883-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6c883-143">See Also</span></span>  
 <span data-ttu-id="6c883-144">[Unique 제약 조건 및 Check 제약 조건](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="6c883-144">[Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span></span>  
 [<span data-ttu-id="6c883-145">UNIQUE 제약 조건 만들기</span><span class="sxs-lookup"><span data-stu-id="6c883-145">Create Unique Constraints</span></span>](../../relational-databases/tables/create-unique-constraints.md)  
  
  
