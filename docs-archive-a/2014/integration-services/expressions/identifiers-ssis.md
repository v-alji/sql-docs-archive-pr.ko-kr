---
title: 식별자(SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- regular identifiers [Integration Services]
- variables [Integration Services], expressions
- identifiers [Integration Services]
- expressions [Integration Services], variables
- lineage identifiers
- columns [Integration Services], identifiers
- names [Integration Services]
- expressions [Integration Services], identifiers
- qualified identifiers [Integration Services]
ms.assetid: 56af984d-88b4-4db8-b6a2-6b07315a699e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 751830d30f26e9b182b3b926549760d1df517914
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732847"
---
# <a name="identifiers-ssis"></a><span data-ttu-id="9fa7e-102">식별자(SSIS)</span><span class="sxs-lookup"><span data-stu-id="9fa7e-102">Identifiers (SSIS)</span></span>
  <span data-ttu-id="9fa7e-103">식에서 식별자는 연산에 사용할 수 있는 열과 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-103">In expressions, identifiers are columns and variables that are available to the operation.</span></span> <span data-ttu-id="9fa7e-104">식은 일반 식별자와 정규화된 식별자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-104">Expressions can use regular and qualified identifiers.</span></span>  
  
## <a name="regular-identifiers"></a><span data-ttu-id="9fa7e-105">일반 식별자</span><span class="sxs-lookup"><span data-stu-id="9fa7e-105">Regular Identifiers</span></span>  
 <span data-ttu-id="9fa7e-106">일반 식별자는 추가 한정자가 필요 없는 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-106">A regular identifier is an identifier that needs no additional qualifiers.</span></span> <span data-ttu-id="9fa7e-107">예를 들어 **AdventureWorks**데이터베이스의 **Contacts** 테이블에 있는 **MiddleName** 열은 일반 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-107">For example, **MiddleName**, a column in the **Contacts** table of the **AdventureWorks** database, is a regular identifier.</span></span>  
  
 <span data-ttu-id="9fa7e-108">일반 식별자 이름은 다음 규칙을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-108">The naming of regular identifiers must follow these rules:</span></span>  
  
-   <span data-ttu-id="9fa7e-109">이름의 첫 글자는 Unicode Standard 2.0에서 정의한 문자이거나 밑줄(_)이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-109">The first character of the name must be a letter as defined by the Unicode Standard 2.0, or an underscore (_).</span></span>  
  
-   <span data-ttu-id="9fa7e-110">후속 글자는 Unicode Standard 2.0에서 정의한 문자나 숫자이거나 밑줄(_), \@, $ 및 # 문자일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-110">Subsequent characters can be letters or numbers as defined in the Unicode Standard 2.0, the underscore (_), \@, $, and # characters.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9fa7e-111">공백과 목록에 없는 특수 문자는 일반 식별자에 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-111">Embedded spaces and special characters, other than the ones listed, are not valid in regular identifiers.</span></span> <span data-ttu-id="9fa7e-112">공백과 특수 문자를 사용하려면 일반 식별자 대신 정규화된 식별자를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-112">In order to use spaces and special characters, you must use a qualified identifier instead of a regular identifier.</span></span>  
  
## <a name="qualified-identifiers"></a><span data-ttu-id="9fa7e-113">정규화된 식별자</span><span class="sxs-lookup"><span data-stu-id="9fa7e-113">Qualified Identifiers</span></span>  
 <span data-ttu-id="9fa7e-114">정규화된 식별자는 대괄호로 구분된 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-114">A qualified identifier is an identifier that is delimited by brackets.</span></span> <span data-ttu-id="9fa7e-115">식별자 이름에 공백이 포함되어 있거나 식별자 이름이 문자나 밑줄로 시작하지 않기 때문에 식별자에 구분 기호가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-115">An identifier may require a delimiter because the name of the identifier includes spaces, or because the identifier name does not begin with either a letter or the underscore character.</span></span> <span data-ttu-id="9fa7e-116">예를 들어 열 이름이 **Middle Name** 인 경우 대괄호로 묶어서 식에 [Middle Name] 형식으로 써야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-116">For example, the column name **Middle Name** must be qualified by brackets and written as [Middle Name] in an expression.</span></span>  
  
 <span data-ttu-id="9fa7e-117">식별자 이름에 공백이 있거나 올바른 일반 식별자 이름이 아니면 식별자를 정규화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-117">If the name of the identifier includes spaces, or if the name is not a valid regular identifier name, the identifier must be qualified.</span></span> <span data-ttu-id="9fa7e-118">식 계산기는 여는 대괄호와 닫는 대괄호([])를 사용하여 식별자를 정규화합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-118">The expression evaluator uses the opening and closing ([]) brackets to qualify identifiers.</span></span> <span data-ttu-id="9fa7e-119">대괄호는 문자열의 시작 위치와 끝 위치에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-119">The brackets are put in the first and the last position of the string.</span></span> <span data-ttu-id="9fa7e-120">예를 들어 식별자 5$>는 [5$>]가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-120">For example, the identifier 5$> becomes [5$>].</span></span> <span data-ttu-id="9fa7e-121">대괄호는 열 이름, 변수 이름 및 함수 이름에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-121">Brackets can be used with column names, variable names, and function names.</span></span>  
  
 <span data-ttu-id="9fa7e-122">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너 대화 상자를 사용하여 식을 작성하면 자동으로 일반 식별자가 대괄호로 묶입니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-122">If you build expressions using the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer dialog boxes, regular identifiers are automatically enclosed in brackets.</span></span> <span data-ttu-id="9fa7e-123">그러나 이름에 잘못된 문자가 포함된 경우에만 대괄호가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-123">However, brackets are required only if the name include invalid characters.</span></span> <span data-ttu-id="9fa7e-124">예를 들어 이름이 **MiddleName** 인 열은 대괄호가 없어도 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-124">For example, the column named **MiddleName** is valid without brackets.</span></span>  
  
 <span data-ttu-id="9fa7e-125">대괄호가 포함된 열 이름은 식에서 참조할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-125">You cannot reference column names that include brackets in expressions.</span></span> <span data-ttu-id="9fa7e-126">예를 들어 열 이름 **Column[1]** 은 식에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-126">For example, the column name **Column[1]** cannot be used in an expression.</span></span> <span data-ttu-id="9fa7e-127">식에 이 열을 사용하려면 대괄호가 없는 이름으로 바꾸어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-127">To use the column in an expression it must be renamed to a name without brackets.</span></span>  
  
## <a name="lineage-identifiers"></a><span data-ttu-id="9fa7e-128">계보 식별자</span><span class="sxs-lookup"><span data-stu-id="9fa7e-128">Lineage Identifiers</span></span>  
 <span data-ttu-id="9fa7e-129">식은 계보 식별자를 사용하여 열을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-129">Expressions can use lineage identifiers to refer to columns.</span></span> <span data-ttu-id="9fa7e-130">계보 식별자는 처음 패키지를 만들 때 자동으로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-130">The lineage identifiers are assigned automatically when you first create the package.</span></span> <span data-ttu-id="9fa7e-131">**디자이너의** 고급 편집기 **대화 상자에 있는** 열 속성 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 탭에서 열의 계보 식별자를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-131">You can view the lineage identifier for a column on the **Column Properties** tab of the **Advanced Editor** dialog box in the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="9fa7e-132">계보 식별자를 사용하여 열을 참조하는 경우 해당 식별자에 파운드(#) 문자 접두사를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-132">If you refer to a column using its lineage identifier, the identifier must include the pound (#) character prefix.</span></span> <span data-ttu-id="9fa7e-133">예를 들어 계보 식별자가 147인 열은 #147로 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-133">For example, a column with the lineage identifier 147 must be referenced as #147.</span></span>  
  
 <span data-ttu-id="9fa7e-134">식이 성공적으로 구문 분석되면 식 계산기는 계보 식별자를 대화 상자에 표시된 열 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-134">If an expression parses successfully, the expression evaluator replaces the lineage identifiers with column names in the dialog box.</span></span>  
  
## <a name="unique-column-names"></a><span data-ttu-id="9fa7e-135">고유 열 이름</span><span class="sxs-lookup"><span data-stu-id="9fa7e-135">Unique Column Names</span></span>  
 <span data-ttu-id="9fa7e-136">패키지에 사용된 여러 개의 구성 요소가 동일한 이름을 가진 열을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-136">Multiple components used in a package can expose columns with the same name.</span></span> <span data-ttu-id="9fa7e-137">이러한 열을 식에 사용하는 경우 열을 명확히 구분해야만 식이 성공적으로 구문 분석될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-137">If these columns are used in expressions, they must be disambiguated before the expressions can be parsed successfully.</span></span> <span data-ttu-id="9fa7e-138">식 계산기는 열 원본을 식별하기 위한 점 표기법을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-138">The expression evaluator supports the dotted notation for identifying the source of the column.</span></span> <span data-ttu-id="9fa7e-139">예를 들어 **Age** 라는 이름의 두 개 열은 각각 **FlatFileSource.Age** 와 **OLEDBSource.Age**가 되어 해당 원본이 FlatFileSource 또는 OLEDBSource임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-139">For example, two columns named **Age** become **FlatFileSource.Age** and **OLEDBSource.Age**, which indicates that their sources are FlatFileSource or OLEDBSource.</span></span> <span data-ttu-id="9fa7e-140">구문 분석기는 정규화된 이름을 단일 열 이름으로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-140">The parser treats the fully qualified name as a single column name.</span></span>  
  
 <span data-ttu-id="9fa7e-141">원본 구성 요소 이름과 열 이름은 별도로 정규화됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-141">Source component names and column names are qualified separately.</span></span> <span data-ttu-id="9fa7e-142">다음 예에서는 점 표기법에서 대괄호의 올바른 사용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-142">The following examples show valid use of brackets in a dotted notation:</span></span>  
  
-   <span data-ttu-id="9fa7e-143">원본 구성 요소 이름에 공백이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-143">The source component name includes spaces.</span></span>  
  
    ```  
    [MySo urce].Age  
    ```  
  
-   <span data-ttu-id="9fa7e-144">열 이름의 첫 문자가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-144">The first character in the column name is not valid.</span></span>  
  
    ```  
    MySource.[#Age]  
    ```  
  
-   <span data-ttu-id="9fa7e-145">원본 구성 요소와 열 이름에 유효하지 않은 문자가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-145">The source component and the column names contain invalid characters.</span></span>  
  
    ```  
    [MySource?].[#Age]  
    ```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9fa7e-146">점 표기법에서 두 요소가 한 쌍의 대괄호로 묶여 있으면 식 계산기는 이 쌍을 원본-열 조합이 아닌 단일 식별자로 해석합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-146">If both elements in dotted notation are enclosed in one pair of brackets, the expression evaluator interprets the pair as a single identifier, not a source-column combination.</span></span>  
  
## <a name="variables-in-expressions"></a><span data-ttu-id="9fa7e-147">식의 변수</span><span class="sxs-lookup"><span data-stu-id="9fa7e-147">Variables in Expressions</span></span>  
 <span data-ttu-id="9fa7e-148">식에서 참조된 변수는 \@ 접두사를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-148">Variables, when referenced in expressions, must include the \@ prefix.</span></span> <span data-ttu-id="9fa7e-149">예를 들어 **Counter** 변수는 \@Counter를 사용하여 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-149">For example, the **Counter** variable is referenced by using \@Counter.</span></span> <span data-ttu-id="9fa7e-150">\@ 문자는 변수 이름의 일부가 아니라 식 계산기에 해당 변수를 식별하는 역할만 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-150">The \@ character is not part of the variable name; it only identifies the variable to the expression evaluator.</span></span> <span data-ttu-id="9fa7e-151">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 제공하는 대화 상자를 사용하여 식을 작성하면 변수 이름에 \@ 문자가 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-151">If you build expressions by using the dialog boxes that [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer provides, the \@ character is automatically added to the variable name.</span></span> <span data-ttu-id="9fa7e-152">\@ 문자와 변수 이름 사이에는 공백을 넣을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-152">It is not valid to include spaces between the \@ character and the variable name.</span></span>  
  
 <span data-ttu-id="9fa7e-153">변수 이름은 다른 일반 식별자의 이름과 동일한 규칙을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-153">Variable names follow the same rules as those for other regular identifiers:</span></span>  
  
-   <span data-ttu-id="9fa7e-154">이름의 첫 글자는 Unicode Standard 2.0에서 정의한 문자이거나 밑줄(_)이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-154">The first character of the name must be a letter as defined by the Unicode Standard 2.0, or an underscore (_).</span></span>  
  
-   <span data-ttu-id="9fa7e-155">후속 글자는 Unicode Standard 2.0에서 정의한 문자나 숫자이거나 밑줄(_), \@, $ 및 # 문자일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-155">Subsequent characters can be letters or numbers as defined in the Unicode Standard 2.0, the underscore (_), \@, $, and # characters.</span></span>  
  
 <span data-ttu-id="9fa7e-156">목록에 없는 문자가 변수 이름에 포함되어 있으면 해당 변수를 대괄호로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-156">If a variable name contains characters other than those listed, the variable must be enclosed in brackets.</span></span> <span data-ttu-id="9fa7e-157">예를 들어 공백이 포함된 변수 이름은 대괄호로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-157">For example, variable names with spaces must be enclosed in brackets.</span></span> <span data-ttu-id="9fa7e-158">여는 대괄호는 \@ 문자 뒤에 옵니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-158">The opening bracket follows the \@ character.</span></span> <span data-ttu-id="9fa7e-159">예를 들어 **My Name** 변수는 \@[My Name]으로 참조됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-159">For example, the **My Name** variable is referenced as \@[My Name].</span></span> <span data-ttu-id="9fa7e-160">변수 이름과 대괄호 사이에는 공백을 넣을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-160">It is not valid to include spaces between the variable name and the brackets.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9fa7e-161">사용자 정의 변수 및 시스템 변수의 이름은 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-161">The names of user-defined and system variables are case-sensitive.</span></span>  
  
## <a name="unique-variable-names"></a><span data-ttu-id="9fa7e-162">고유 변수 이름</span><span class="sxs-lookup"><span data-stu-id="9fa7e-162">Unique Variable Names</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="9fa7e-163">는 사용자 지정 변수를 지원하며 시스템 변수 집합을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-163">supports custom variables and provides a set of system variables.</span></span> <span data-ttu-id="9fa7e-164">기본적으로 사용자 지정 변수는 **User** 네임스페이스에 속하고 시스템 변수는 **System** 네임스페이스에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-164">By default, custom variables belong to the **User** namespace, and system variables belong to the **System** namespace.</span></span> <span data-ttu-id="9fa7e-165">사용자 지정 변수용 네임스페이스를 추가로 만들고 애플리케이션의 요구에 맞게 기존 네임스페이스 이름을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-165">You can create additional namespaces for custom variables and update the namespace names to suit the needs of your application.</span></span> <span data-ttu-id="9fa7e-166">식 작성기는 모든 네임스페이스의 범위 내 변수 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-166">The expression builder lists in-scope variables in all namespaces.</span></span>  
  
 <span data-ttu-id="9fa7e-167">모든 변수는 범위를 가지고 있고 하나의 네임스페이스에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-167">All variables have scope and belong to a namespace.</span></span> <span data-ttu-id="9fa7e-168">변수 범위는 패키지 범위이거나 패키지의 컨테이너 또는 태스크 범위입니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-168">A variable has package scope or the scope of a container or task in the package.</span></span> <span data-ttu-id="9fa7e-169">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너의 식 작성기는 범위 내 변수 목록만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-169">The expression builder in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer lists only the in-scope variables.</span></span> <span data-ttu-id="9fa7e-170">자세한 내용은 [Integration Services&#40;SSIS&#41; 변수](../integration-services-ssis-variables.md) 및 [패키지에서 변수 사용](../use-variables-in-packages.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-170">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
 <span data-ttu-id="9fa7e-171">식에 사용된 변수의 이름이 고유해야 식 계산기에서 식을 올바로 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-171">Variables used in expressions must have unique names for the expression evaluator to evaluate the expression correctly.</span></span> <span data-ttu-id="9fa7e-172">패키지에서 이름이 같은 변수를 여러 개 사용할 경우 해당 네임스페이스가 서로 달라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-172">If a package uses multiple variables with the same name, their namespaces must be different.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="9fa7e-173">두 개의 콜론으로 구성된(::) 네임스페이스 확인 연산자를 사용하여 네임스페이스로 변수를 정규화합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-173">provides a namespace resolution operator, consisting of two colons (::), for qualifying a variable with its namespace.</span></span> <span data-ttu-id="9fa7e-174">예를 들어 다음 식에서는 **Count**라는 이름을 가진 변수 두 개를 사용합니다. 하나는 **User** 네임스페이스에 속하고 다른 하나는 **MyNamespace** 네임스페이스에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-174">For example, the following expression uses two variables named **Count**; one belongs to the **User** namespace and one to the **MyNamespace** namespace.</span></span>  
  
```  
@[User::Count] > @[MyNamespace::Count]  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9fa7e-175">식 계산기에서 변수를 인식할 수 있도록 네임스페이스와 정규화된 변수 이름 조합을 대괄호로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-175">You must enclose the combination of namespace and qualified variable name in brackets for the expression evaluator to recognize the variable.</span></span>  
  
 <span data-ttu-id="9fa7e-176">**사용자** 네임 스페이스의 **count** 값이 10이 고 **MyNamespace** 의 **count** 값이 2 이면 식 `true` 계산기에서 두 개의 다른 변수를 인식 하므로 식이로 평가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-176">If the value of **Count** in the **User** namespace is 10 and the value of **Count** in **MyNamespace** is 2, the expression evaluates to `true` because the expression evaluator recognizes two different variables.</span></span>  
  
 <span data-ttu-id="9fa7e-177">고유한 변수 이름을 사용하지 않아도 오류가 발생하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-177">If variable names are not unique, no error occurs.</span></span> <span data-ttu-id="9fa7e-178">대신 식 계산기가 해당 변수의 한 개 인스턴스만 사용하여 식을 계산하고 잘못된 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-178">Instead, the expression evaluator uses only one instance of the variable to evaluate the expression and returns an incorrect result.</span></span> <span data-ttu-id="9fa7e-179">예를 들어 다음 식은 두 개의 별도 **Count** 변수에 대 한 값 (10과 2)을 비교 하기 위한 것 이지만 `false` 식 계산기에서 **Count** 변수의 같은 인스턴스를 두 번 사용 하므로 식이로 계산 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fa7e-179">For example, the following expression was intended to compare the values (10 and 2) for two separate **Count** variables but the expression evaluates to `false` because the expression evaluator uses the same instance of the **Count** variable two times.</span></span>  
  
```  
@Count > @Count  
```  
  
## <a name="related-content"></a><span data-ttu-id="9fa7e-180">관련 내용</span><span class="sxs-lookup"><span data-stu-id="9fa7e-180">Related Content</span></span>  
 <span data-ttu-id="9fa7e-181">pragmaticworks.com의 기술 문서 - [SSIS 식 치트 시트](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet)</span><span class="sxs-lookup"><span data-stu-id="9fa7e-181">Technical article, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet), on pragmaticworks.com</span></span>  
  
  
