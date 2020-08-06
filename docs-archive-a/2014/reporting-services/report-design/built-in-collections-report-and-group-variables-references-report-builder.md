---
title: 보고서 및 그룹 변수 컬렉션 참조(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10404"
- sql12.rtp.rptdesigner.categorygroupproperties.variables.f1
- "10083"
- sql12.rtp.rptdesigner.seriesgroupproperties.variables.f1
- sql12.rtp.rptdesigner.reportproperties.variables.f1
- sql12.rtp.rptdesigner.groupproperties.variables.f1
- "10292"
- "10412"
ms.assetid: 4be5b463-3ce2-483d-a3c6-dae752cb543e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 41dd652bf39721b13801131a5ec268495edf9d29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728051"
---
# <a name="report-and-group-variables-collections-references-report-builder-and-ssrs"></a><span data-ttu-id="23f18-102">보고서 및 그룹 변수 컬렉션 참조(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="23f18-102">Report and Group Variables Collections References (Report Builder and SSRS)</span></span>
  <span data-ttu-id="23f18-103">보고서의 식에서 두 번 이상 사용되는 복잡한 계산이 있는 경우 변수를 만들어 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-103">When you have a complex calculation that is used more than once in expressions in a report, you might want to create a variable.</span></span> <span data-ttu-id="23f18-104">보고서 변수 또는 그룹 변수를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-104">You can create a report variable or a group variable.</span></span> <span data-ttu-id="23f18-105">변수 이름은 보고서에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-105">Variable names must be unique in a report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="report-variables"></a><span data-ttu-id="23f18-106">보고서 변수</span><span class="sxs-lookup"><span data-stu-id="23f18-106">Report Variables</span></span>  
 <span data-ttu-id="23f18-107">보고서 변수를 사용하여 환율이나 타임스탬프와 같이 시간에 종속되는 계산 또는 여러 번 참조되는 복잡한 계산에 대한 값을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-107">Use a report variable to hold a value for time-dependent calculations, such as currency rates or time stamps, or for a complex calculation that is referenced multiple times.</span></span> <span data-ttu-id="23f18-108">기본적으로 보고서 변수는 한 번 계산한 후 보고서 전체의 식에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-108">By default, a report variable is calculated once and can be used in expressions throughout a report.</span></span> <span data-ttu-id="23f18-109">보고서 변수는 기본적으로 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-109">Report variables are read-only by default.</span></span> <span data-ttu-id="23f18-110">기본값을 변경하여 보고서 변수를 읽기/쓰기 가능하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-110">You can change the default to enable a report variable as read-write.</span></span> <span data-ttu-id="23f18-111">보고서 변수의 값은 보고서를 다시 처리할 때까지 세션 전체에서 보존됩니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-111">The value in a report variable is preserved throughout a session, until the report is processed again.</span></span>  
  
 <span data-ttu-id="23f18-112">보고서 변수를 추가하려면 **보고서 속성** 대화 상자를 열고 **변수**를 클릭한 후 이름과 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-112">To add a report variable, open the **ReportProperties** dialog box, click **Variables**, and provide a name and a value.</span></span> <span data-ttu-id="23f18-113">이름은 문자로 시작하고 공백을 포함하지 않는 대/소문자를 구분하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-113">Names are case-sensitive strings that begin with a letter and have no spaces.</span></span> <span data-ttu-id="23f18-114">이름에는 문자, 숫자 또는 밑줄(_)을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-114">A name can include letters, numbers, or underscores (_).</span></span>  
  
 <span data-ttu-id="23f18-115">식에서 변수를 참조하려면 전역 컬렉션 구문을 사용합니다(예: `=Variables!CustomTimeStamp.Value`).</span><span class="sxs-lookup"><span data-stu-id="23f18-115">To refer to the variable in an expression, use the global collection syntax, for example, `=Variables!CustomTimeStamp.Value`.</span></span> <span data-ttu-id="23f18-116">디자인 화면에서 값은 입력란에 `<<Expr>>`로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-116">On the design surface, the value appears in a text box as `<<Expr>>`.</span></span>  
  
 <span data-ttu-id="23f18-117">다음 방법으로 보고서 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-117">You can use report variables in the following ways:</span></span>  
  
-   <span data-ttu-id="23f18-118">**읽기 전용으로 사용** 값을 한 번 설정하여 보고서 세션에 대해 상수를 만듭니다(예: 타임스탬프 만들기).</span><span class="sxs-lookup"><span data-stu-id="23f18-118">**Read-only use** Set a value once to create a constant for the report session, for example, to create a time stamp.</span></span>  
  
     <span data-ttu-id="23f18-119">입력란의 식은 보고서를 읽는 사용자의 요청에 따라 계산되므로 동적 값(예: 현재 시간을 반환하는 함수인 `Now()` 를 포함하는 식)은 사용자가 **뒤로** 단추를 사용하여 앞뒤 페이지로 이동하는 경우 다른 값을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-119">Because expressions in text boxes are evaluated on-demand as a user pages through a report, dynamic values (for example, an expression that includes the `Now()` function, which returns the time of day) can return different values if you page forward and backward by using the **Back** button.</span></span> <span data-ttu-id="23f18-120">보고서 변수의 값을 `=Now()`식으로 설정하고 변수를 식에 추가하면 보고서를 처리하는 동안 내내 동일한 값이 사용되도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-120">By setting a the value of a report variable to the expression `=Now()`, and then adding the variable to your expression, you ensure the same value is used throughout report processing.</span></span>  
  
-   <span data-ttu-id="23f18-121">**읽기/쓰기로 사용** 값을 한 번 설정하고 보고서 세션 내에서 값을 직렬화합니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-121">**Read-write use** Set a value once and serialize the value within a report session.</span></span> <span data-ttu-id="23f18-122">변수에 대해 읽기/쓰기 옵션을 사용하는 것이 보고서 정의의 코드 블록에서 정적 변수를 사용하는 것보다 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-122">The read-write option for variables provides a better alternative than using a static variable in the Code block in the report definition.</span></span>  
  
     <span data-ttu-id="23f18-123">변수에 대 한 **읽기 전용** 옵션을 선택 취소 하면 변수에 대 한 쓰기 가능 속성이로 설정 됩니다 `true` .</span><span class="sxs-lookup"><span data-stu-id="23f18-123">When you clear the **Read-Only** option for a variable, the Writable property for the variable is set to `true`.</span></span> <span data-ttu-id="23f18-124">식에서 값을 업데이트하려면 SetValue 메서드(예: `=Variables!MyVariable.SetValue("123")`)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-124">To update the value from an expression, use the SetValue method, for example, `=Variables!MyVariable.SetValue("123")`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="23f18-125">보고서 프로세서가 변수를 초기화하는 시기 또는 변수를 업데이트하는 식을 계산하는 시기는 제어할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-125">You cannot control when the report processor initializes a variable or evaluates an expression that updates a variable.</span></span> <span data-ttu-id="23f18-126">변수 초기화 실행 순서는 정의되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-126">The order of execution for variable initialization is undefined.</span></span>  
  
 <span data-ttu-id="23f18-127">세션에 대한 자세한 내용은 [Previewing Reports in Report Builder](../report-builder/previewing-reports-in-report-builder.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="23f18-127">For more information about sessions, see [Previewing Reports in Report Builder](../report-builder/previewing-reports-in-report-builder.md).</span></span>  
  
## <a name="group-variables"></a><span data-ttu-id="23f18-128">그룹 변수</span><span class="sxs-lookup"><span data-stu-id="23f18-128">Group Variables</span></span>  
 <span data-ttu-id="23f18-129">그룹 변수를 사용하여 복잡한 식을 그룹 범위에서 한 번에 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-129">Use a group variable to calculate a complex expression once in the scope of a group.</span></span> <span data-ttu-id="23f18-130">그룹 변수는 그룹 및 해당 자식 그룹의 범위 내에서만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-130">A group variable is valid only in the scope of the group and its child groups.</span></span>  
  
 <span data-ttu-id="23f18-131">예를 들어 서로 다른 세금 범주에 속한 항목에 대한 재고 데이터를 표시하는 데이터 영역이 있고 각 범주에 대해 서로 다른 세율을 적용하려는 경우를 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-131">For example, suppose a data region displays inventory data for items that are in different tax categories and you want to apply different tax rates for each category.</span></span> <span data-ttu-id="23f18-132">Category에서 데이터를 그룹화하고 부모 그룹에서 *Tax* 변수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-132">You would group the data on Category and define a *Tax* variable on the parent group.</span></span> <span data-ttu-id="23f18-133">그런 다음 *ItemTax* 에 대한 그룹 변수를 각 세금 범주에 정의하고 서로 다른 각 Category 하위 그룹을 적절한 그룹 변수에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-133">Then you would define a group variable for *ItemTax* for each tax category and assign each of the different Category subgroups to the correct group variable.</span></span> <span data-ttu-id="23f18-134">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-134">For example:</span></span>  
  
-   <span data-ttu-id="23f18-135">`[Category]`기반의 부모 그룹에 대해 *Tax* 변수를 `[Tax]`값으로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-135">For the parent group based on `[Category]`, define the variable *Tax* with a value `[Tax]`.</span></span> <span data-ttu-id="23f18-136">범주 값은 Food와 Clothing이라고 가정하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-136">Assume the category values are Food and Clothing.</span></span>  
  
-   <span data-ttu-id="23f18-137">`[Subcategory]`기반의 자식 그룹에 대해 *ItemsTax* 변수를 `=Variables!Tax.Value * Sum(Fields!Price.Value)`으로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-137">For the child group based on `[Subcategory]`, define the variable *ItemsTax* as `=Variables!Tax.Value * Sum(Fields!Price.Value)`.</span></span> <span data-ttu-id="23f18-138">Food 범주의 하위 범주 값은 Beverages 및 Bread라고 가정하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-138">Assume the subcategory values for the category Food are Beverages and Bread.</span></span> <span data-ttu-id="23f18-139">Clothing의 하위 범주 값은 Shirts 및 Hats라고 가정하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-139">Assume the subcategory values for Clothing are Shirts and Hats.</span></span>  
  
-   <span data-ttu-id="23f18-140">자식 그룹의 행에 있는 입력란에 대해 `=Variables!ItemsTax.Value`식을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-140">For a text box in a row in the child group, add the expression `=Variables!ItemsTax.Value`.</span></span>  
  
     <span data-ttu-id="23f18-141">입력란에는 Beverages 및 Bread에 대해 Food 세금을 사용하고 Shirts 및 Hats에 대해 Clothing 세금을 사용한 총 세금이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-141">The text box displays the total tax for Beverages and Bread using the Food tax and for Shirts and Hats using the Clothing tax.</span></span>  
  
 <span data-ttu-id="23f18-142">그룹 변수를 추가하려면 **테이블릭스 그룹 속성** 대화 상자를 열고 **변수**를 클릭하고 이름과 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-142">To add a group variable, open the **Tablix Group Properties** dialog box, click **Variables**, and provide a name and a value.</span></span> <span data-ttu-id="23f18-143">그룹 변수는 고유 그룹 값별로 한 번 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-143">The group variable is calculated once per unique group value.</span></span>  
  
 <span data-ttu-id="23f18-144">식에서 변수를 참조하려면 전역 컬렉션 구문을 사용합니다(예: `=Variables!GroupDescription.Value`).</span><span class="sxs-lookup"><span data-stu-id="23f18-144">To refer to the variable in an expression, use the global collection syntax, for example, `=Variables!GroupDescription.Value`.</span></span> <span data-ttu-id="23f18-145">디자인 화면에서 값은 입력란에 `<<Expr>>`로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="23f18-145">On the design surface, the value appears in a text box as `<<Expr>>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23f18-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="23f18-146">See Also</span></span>  
 <span data-ttu-id="23f18-147">[데이터 필터링, 그룹화 및 정렬&#40;보고서 작성기 및 SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="23f18-147">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="23f18-148">[식의 기본 제공 컬렉션&#40;보고서 작성기 및 SSRS&#41;](built-in-collections-in-expressions-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="23f18-148">[Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](built-in-collections-in-expressions-report-builder.md) </span></span>  
 [<span data-ttu-id="23f18-149">식 예&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="23f18-149">Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)  
  
  
