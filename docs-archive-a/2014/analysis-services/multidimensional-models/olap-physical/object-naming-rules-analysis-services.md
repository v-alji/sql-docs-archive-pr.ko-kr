---
title: 개체 명명 규칙 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Services], naming
ms.assetid: b338a60d-4802-4b68-862a-6dc6a3f75e48
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6adfd4b23b6fe9129641271fc3c2381e161119ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653587"
---
# <a name="object-naming-rules-analysis-services"></a><span data-ttu-id="2b339-102">개체 명명 규칙(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="2b339-102">Object Naming Rules (Analysis Services)</span></span>
  <span data-ttu-id="2b339-103">이 항목에서는 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]의 코드 또는 스크립트, 개체 이름에 사용할 수 없는 예약어 및 문자뿐만 아니라 개체 명명 규칙에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-103">This topic describes object naming conventions, as well as the reserved words and characters that cannot be used in any object name, in code or script in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
##  <a name="naming-conventions"></a><a name="bkmk_Names"></a><span data-ttu-id="2b339-104">명명 규칙</span><span class="sxs-lookup"><span data-stu-id="2b339-104">Naming Conventions</span></span>  
 <span data-ttu-id="2b339-105">모든 개체에는 부모 컬렉션의 범위 내에서 고유해야 하는 `Name` 및 `ID` 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-105">Every object has a `Name` and `ID` property that must be unique within the scope of the parent collection.</span></span> <span data-ttu-id="2b339-106">예를 들어 두 차원은 각각이 다른 데이터베이스에 상주하는 한 같은 이름을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-106">For example, two dimensions can have same name as long as each one resides in a different database.</span></span>  
  
 <span data-ttu-id="2b339-107">이름을 수동으로 지정할 수 있지만 `ID`는 개체를 만들 때 일반적으로 자동 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-107">Although you can specify it manually, the `ID` is typically auto-generated when the object is created.</span></span> <span data-ttu-id="2b339-108">모델을 만들었으면 `ID`를 변경해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-108">You should never change the `ID` once you have begun building a model.</span></span> <span data-ttu-id="2b339-109">모델 전반의 모든 개체 참조는 `ID`를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-109">All object references throughout a model are based on the `ID`.</span></span> <span data-ttu-id="2b339-110">따라서 `ID`를 변경하면 모델이 쉽게 손상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-110">Thus, changing an `ID` can easily result in model corruption.</span></span>  
  
 <span data-ttu-id="2b339-111">`DataSource` 및 `DataSourceView` 개체에는 명명 규칙에 대해 주목할 만한 예외가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-111">`DataSource` and `DataSourceView` objects have notable exceptions to naming conventions.</span></span> <span data-ttu-id="2b339-112">`DataSource` ID를 현재 데이터베이스에 대한 참조로 단일 점(.)으로 설정할 수 있지만 고유하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-112">`DataSource` ID can be set to a single dot (.), which is not unique, as a reference to the current database.</span></span> <span data-ttu-id="2b339-113">두 번째 예외는 `DataSourceView`로, .NET Framework의 `DataSet` 개체에 정의된 명명 규칙을 준수합니다. 여기서 `Name`은 식별자로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-113">A second exception is `DataSourceView`, which adheres to the naming conventions defined for `DataSet` objects in the .NET Framework, where the `Name` is used as the identifier.</span></span>  
  
 <span data-ttu-id="2b339-114">다음은 `Name` 및 `ID` 속성에 적용되는 추가 규칙입니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-114">The following rules apply to `Name` and `ID` properties.</span></span>  
  
-   <span data-ttu-id="2b339-115">이름은 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-115">Names are case insensitive.</span></span> <span data-ttu-id="2b339-116">이름이 "sales"이 고 이름이 "Sales" 인 큐브를 같은 데이터베이스에 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-116">You cannot have a cube named "sales" and another named "Sales" in the same database.</span></span>  
  
-   <span data-ttu-id="2b339-117">이름 내에 공백을 포함할 수 있더라도 개체 이름에 선행 또는 후행 공백을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-117">No leading or trailing spaces allowed in an object name, although you can embed spaces within a name.</span></span> <span data-ttu-id="2b339-118">선행 공백과 후행 공백은 암시적으로 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-118">Leading and trailing spaces are implicitly trimmed.</span></span> <span data-ttu-id="2b339-119">이는 개체의 `Name` 및 `ID`에 모두 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-119">This applies to both the `Name` and `ID` of an object.</span></span>  
  
-   <span data-ttu-id="2b339-120">최대 문자 수는 100자입니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-120">The maximum number of characters is 100.</span></span>  
  
-   <span data-ttu-id="2b339-121">식별자의 첫 문자에는 특별한 요구 사항이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-121">There is no special requirement for the first character of an identifier.</span></span> <span data-ttu-id="2b339-122">첫 문자는 모든 유효한 문자일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-122">The first character may be any valid character.</span></span>  
  
##  <a name="reserved-words-and-characters"></a><a name="bkmk_reserved"></a><span data-ttu-id="2b339-123">예약어 및 문자</span><span class="sxs-lookup"><span data-stu-id="2b339-123">Reserved Words and Characters</span></span>  
 <span data-ttu-id="2b339-124">예약어는 영어로 되어 있으며 캡션이 아닌 개체 이름에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-124">Reserved words are in English, and apply to object names, not Captions.</span></span> <span data-ttu-id="2b339-125">개체 이름에 실수로 예약어를 사용하는 경우 유효성 검사 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-125">If you inadvertently use a reserved word in an object name, a validation error will occur.</span></span> <span data-ttu-id="2b339-126">다차원 및 데이터 마이닝 모델의 경우 아래에 명시된 예약어를 어떤 경우에도 개체 이름에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-126">For multidimensional and data mining models, the reserved words described below cannot be used in any object name, at any time.</span></span>  
  
 <span data-ttu-id="2b339-127">테이블 형식 모델의 경우 데이터베이스 호환성이 1103으로 설정되어 있고 특정 개체에 대해 유효성 검사 규칙이 해제되었으며 확장 문자 요구 사항 및 특정 클라이언트 애플리케이션 명명 규칙을 준수하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-127">For tabular models, where the database compatibility is set to 1103, validation rules have been relaxed for certain objects, out of compliance for the extended character requirements and naming conventions of certain client applications.</span></span> <span data-ttu-id="2b339-128">이러한 조건을 충족하는 데이터베이스는 보다 덜 엄격한 유효성 검사 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-128">Databases that meet these criteria are subject to less stringent validation rules.</span></span> <span data-ttu-id="2b339-129">이 경우 개체 이름에 제한된 문자를 포함할 수 있으며 유효성 검사도 통과합니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-129">In this case, it's possible for an object name to include a restricted character and still pass validation.</span></span>  
  
 <span data-ttu-id="2b339-130">**예약어**</span><span class="sxs-lookup"><span data-stu-id="2b339-130">**Reserved Words**</span></span>  
  
-   <span data-ttu-id="2b339-131">AUX</span><span class="sxs-lookup"><span data-stu-id="2b339-131">AUX</span></span>  
  
-   <span data-ttu-id="2b339-132">CLOCK$</span><span class="sxs-lookup"><span data-stu-id="2b339-132">CLOCK$</span></span>  
  
-   <span data-ttu-id="2b339-133">COM1 - COM9(COM1, COM2, COM3 등)</span><span class="sxs-lookup"><span data-stu-id="2b339-133">COM1 through COM9 (COM1, COM2, COM3, and so on)</span></span>  
  
-   <span data-ttu-id="2b339-134">CON</span><span class="sxs-lookup"><span data-stu-id="2b339-134">CON</span></span>  
  
-   <span data-ttu-id="2b339-135">LPT1 - LPT9(LPT1, LPT2, LPT3 등)</span><span class="sxs-lookup"><span data-stu-id="2b339-135">LPT1 through LPT9 (LPT1, LPT2, LPT3, and so on)</span></span>  
  
-   <span data-ttu-id="2b339-136">NUL</span><span class="sxs-lookup"><span data-stu-id="2b339-136">NUL</span></span>  
  
-   <span data-ttu-id="2b339-137">PRN</span><span class="sxs-lookup"><span data-stu-id="2b339-137">PRN</span></span>  
  
-   <span data-ttu-id="2b339-138">XML 내의 문자열에는 NULL 문자를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-138">NULL is not allowed as a character in any string within the XML</span></span>  
  
 <span data-ttu-id="2b339-139">**예약 문자**</span><span class="sxs-lookup"><span data-stu-id="2b339-139">**Reserved Characters**</span></span>  
  
 <span data-ttu-id="2b339-140">다음 표에서는 개체별로 유효하지 않은 문자열 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-140">The following table lists invalid characters for specific objects.</span></span>  
  
|<span data-ttu-id="2b339-141">Object</span><span class="sxs-lookup"><span data-stu-id="2b339-141">Object</span></span>|<span data-ttu-id="2b339-142">잘못된 문자</span><span class="sxs-lookup"><span data-stu-id="2b339-142">Invalid characters</span></span>|  
|------------|------------------------|  
|`Server`|<span data-ttu-id="2b339-143">서버 개체 이름을 지정할 대 Windows 서버 명명 규칙을 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="2b339-143">Follow Windows server naming conventions when naming a server object.</span></span> <span data-ttu-id="2b339-144">자세한 내용은 [명명 규칙(Windows)](/windows/desktop/DNS/naming-conventions) 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2b339-144">See [Naming Conventions (Windows)](/windows/desktop/DNS/naming-conventions) for details.</span></span>|  
|`DataSource`| `: / \ * \| ? " () [] {} <>` |  
|<span data-ttu-id="2b339-145">`Level` 또는 `Attribute`</span><span class="sxs-lookup"><span data-stu-id="2b339-145">`Level` or `Attribute`</span></span>|````. , ; ' ` : / \ * & \| ? " & % $ ! + = [] {} < >````|  
|<span data-ttu-id="2b339-146">`Dimension` 또는 `Hierarchy`</span><span class="sxs-lookup"><span data-stu-id="2b339-146">`Dimension` or `Hierarchy`</span></span>|````. , ; ' ` : / \ * \| ? " & % $ ! + = () [] {} <,>````|  
|<span data-ttu-id="2b339-147">기타 모든 개체</span><span class="sxs-lookup"><span data-stu-id="2b339-147">All other objects</span></span>|````. , ; ' ` : / \ * \| ? " & % $ ! + = () [] {} < >````|  
  
 <span data-ttu-id="2b339-148">**예외: 예약 문자가 허용되는 경우**</span><span class="sxs-lookup"><span data-stu-id="2b339-148">**Exceptions: When Reserved Characters are Allowed**</span></span>  
  
 <span data-ttu-id="2b339-149">앞에서 설명한 것처럼 특정 형식 및 호환성 수준의 데이터베이스에는 예약 문자를 포함하는 개체 이름이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-149">As noted, databases of a specific modality and compatibility level can have object names that include reserved characters.</span></span> <span data-ttu-id="2b339-150">차원 특성, 계층 구조, 수준, 측정값 및 KPI 개체 이름은 예약 문자를 포함할 수 있으며 확장 문자 사용이 허용되는 테이블 형식 데이터베이스(1103 이상)의 경우 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-150">Dimension attribute, hierarchy, level, measure and KPI object names can include reserved characters, for tabular databases (1103 or higher) that allow the use of extended characters:</span></span>  
  
|<span data-ttu-id="2b339-151">서버 모드 및 데이터베이스 호환성 수준</span><span class="sxs-lookup"><span data-stu-id="2b339-151">Server mode and database compatibility level</span></span>|<span data-ttu-id="2b339-152">예약 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="2b339-152">Reserved characters allowed?</span></span>|  
|--------------------------------------------------|----------------------------------|  
|<span data-ttu-id="2b339-153">MOLAP(모든 버전)</span><span class="sxs-lookup"><span data-stu-id="2b339-153">MOLAP (all versions)</span></span>|<span data-ttu-id="2b339-154">아니요</span><span class="sxs-lookup"><span data-stu-id="2b339-154">No</span></span>|  
|<span data-ttu-id="2b339-155">테이블 형식 - 1050</span><span class="sxs-lookup"><span data-stu-id="2b339-155">Tabular - 1050</span></span>|<span data-ttu-id="2b339-156">아니요</span><span class="sxs-lookup"><span data-stu-id="2b339-156">No</span></span>|  
|<span data-ttu-id="2b339-157">테이블 형식 - 1100</span><span class="sxs-lookup"><span data-stu-id="2b339-157">Tabular - 1100</span></span>|<span data-ttu-id="2b339-158">아니요</span><span class="sxs-lookup"><span data-stu-id="2b339-158">No</span></span>|  
|<span data-ttu-id="2b339-159">테이블 형식-1130 이상</span><span class="sxs-lookup"><span data-stu-id="2b339-159">Tabular - 1130 and higher</span></span>|<span data-ttu-id="2b339-160">예</span><span class="sxs-lookup"><span data-stu-id="2b339-160">Yes</span></span>|  
  
 <span data-ttu-id="2b339-161">데이터베이스 기본 ModelType을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-161">Databases can have a ModelType of default.</span></span> <span data-ttu-id="2b339-162">기본값은 다차원과 같으므로 열 이름에 예약 문자를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b339-162">Default is equivalent to multidimensional, and thus does not support the use of reserved characters in column names.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b339-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2b339-163">See Also</span></span>  
 <span data-ttu-id="2b339-164">[MDX 예약어](/sql/mdx/mdx-reserved-words) </span><span class="sxs-lookup"><span data-stu-id="2b339-164">[MDX Reserved Words](/sql/mdx/mdx-reserved-words) </span></span>  
 <span data-ttu-id="2b339-165">[번역 &#40;Analysis Services&#41;](/analysis-services/translation-support-in-analysis-services) </span><span class="sxs-lookup"><span data-stu-id="2b339-165">[Translations &#40;Analysis Services&#41;](/analysis-services/translation-support-in-analysis-services) </span></span>  
 [<span data-ttu-id="2b339-166">XMLA&#41;&#40;XML for Analysis 준수</span><span class="sxs-lookup"><span data-stu-id="2b339-166">XML for Analysis Compliance &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-compliance-xmla)  
  
  
