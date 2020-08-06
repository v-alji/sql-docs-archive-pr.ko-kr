---
title: Analysis Services 데이터베이스에 대한 확장 필드 속성(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1d7d87e2-bf0d-4ebb-a287-80b5a967a3f2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f5c0a8ebcb739cdf6b3fa34acf467309e7854db1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742875"
---
# <a name="extended-field-properties-for-an-analysis-services-database-ssrs"></a><span data-ttu-id="df409-102">Analysis Services 데이터베이스에 대한 확장 필드 속성(SSRS)</span><span class="sxs-lookup"><span data-stu-id="df409-102">Extended Field Properties for an Analysis Services Database (SSRS)</span></span>
  <span data-ttu-id="df409-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터 처리 확장 프로그램은 확장 필드 속성을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="df409-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data processing extension supports extended field properties.</span></span> <span data-ttu-id="df409-104">확장 필드 속성은 `Value` 및 `IsMissing` 외에 데이터 원본에서 사용할 수 있고 데이터 처리 확장 프로그램에서 지원되는 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="df409-104">Extended field properties are properties in addition to the field properties `Value` and `IsMissing` that are available on the data source and supported by the data processing extension.</span></span> <span data-ttu-id="df409-105">확장 속성은 보고서 데이터 세트에 대한 필드 컬렉션의 일부로 보고서 데이터 창에 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="df409-105">Extended properties do not appear in the Report Data pane as part of the field collection for a report dataset.</span></span> <span data-ttu-id="df409-106">기본 제공 `Fields` 컬렉션을 사용하여 이름으로 확장 필드 속성 값을 지정하는 식을 작성하면 보고서에 확장 필드 속성 값을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df409-106">You can include extended field property values in your report by writing expressions that specify them by name using the built-in `Fields` collection.</span></span>  
  
 <span data-ttu-id="df409-107">확장 속성에는 미리 정의된 속성과 사용자 지정 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="df409-107">Extended properties include predefined properties and custom properties.</span></span> <span data-ttu-id="df409-108">미리 정의된 속성은 여러 데이터 원본에 공통되는 속성으로, 특정 필드 속성 이름에 매핑되고 기본 제공 `Fields` 컬렉션을 통해 이름으로 액세스될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df409-108">Predefined properties are properties common to multiple data sources that are mapped to specific field property names and can be accessed through the built-in `Fields` collection by name.</span></span> <span data-ttu-id="df409-109">사용자 지정 속성은 각 데이터 공급자별로 정의되며 확장 속성 이름을 문자열로 사용하는 구문에 의해서만 기본 제공 `Fields` 컬렉션을 통해 액세스될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df409-109">Custom properties are specific to each data provider and can be accessed through the built-in `Fields` collection only through syntax using the extended property name as a string.</span></span>  
  
 <span data-ttu-id="df409-110">그래픽 모드에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] MDX 쿼리 디자이너를 사용하여 쿼리를 정의하면 미리 정의된 셀 속성 및 차원 속성 집합이 자동으로 MDX 쿼리에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="df409-110">When you use the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] MDX query designer in graphical mode to define your query, a predefined set of cell properties and dimension properties are automatically added to the MDX query.</span></span> <span data-ttu-id="df409-111">보고서의 MDX 쿼리에 구체적으로 나열된 확장 속성만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df409-111">You can only use extended properties that are specifically listed in the MDX query in your report.</span></span> <span data-ttu-id="df409-112">보고서에 따라 기본 MDX 명령 텍스트를 수정하여 큐브에 정의된 다른 차원 속성이나 사용자 지정 속성을 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df409-112">Depending on your report, you may want to modify the default MDX command text to include other dimension or custom properties defined in the cube.</span></span> <span data-ttu-id="df409-113">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터 원본에서 사용할 수 있는 확장 필드에 대한 자세한 내용은 [속성 값 만들기 및 사용&#40;MDX&#41;](../../analysis-services/creating-and-using-property-values-mdx.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df409-113">For more information about extended fields available in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data sources, see [Creating and Using Property Values &#40;MDX&#41;](../../analysis-services/creating-and-using-property-values-mdx.md).</span></span>  
  
## <a name="working-with-field-properties-in-a-report"></a><span data-ttu-id="df409-114">보고서에서 필드 속성 사용</span><span class="sxs-lookup"><span data-stu-id="df409-114">Working with Field Properties in a Report</span></span>  
 <span data-ttu-id="df409-115">확장 필드 속성에는 미리 정의된 속성과 데이터 공급자 관련 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="df409-115">Extended field properties include predefined properties and data provider-specific properties.</span></span> <span data-ttu-id="df409-116">필드 속성은 데이터 세트에 대해 작성된 쿼리에 포함되어 있어도 **보고서 데이터** 창의 필드 목록에 나타나지 않습니다. 따라서 필드 속성을 보고서 디자인 화면으로 끌 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="df409-116">Field properties do not appear with the field list in the **Report Data** pane, even though they are in the query built for a dataset; therefore, you cannot drag field properties onto your report design surface.</span></span> <span data-ttu-id="df409-117">대신 필드를 보고서로 끈 다음 필드의 `Value` 속성을 사용하려는 속성으로 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="df409-117">Instead, you must drag the field onto the report and then change the `Value` property of the field to the property that you want to use.</span></span> <span data-ttu-id="df409-118">예를 들어 큐브의 셀 데이터 형식이 이미 지정되어 있는 경우 `=Fields!FieldName.FormattedValue`식을 통해 FormattedValue 필드 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df409-118">For example, if the cell data from a cube has already been formatted, you can use the FormattedValue field property by using the following expression: `=Fields!FieldName.FormattedValue`.</span></span>  
  
 <span data-ttu-id="df409-119">미리 정의되지 않은 확장 속성을 참조하려면 식에 다음 구문을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="df409-119">To refer to an extended property that is not predefined, use the following syntax in an expression:</span></span>  
  
-   <span data-ttu-id="df409-120">*Fields!FieldName("PropertyName")*</span><span class="sxs-lookup"><span data-stu-id="df409-120">*Fields!FieldName("PropertyName")*</span></span>  
  
## <a name="predefined-field-properties"></a><span data-ttu-id="df409-121">미리 정의된 필드 속성</span><span class="sxs-lookup"><span data-stu-id="df409-121">Predefined Field Properties</span></span>  
 <span data-ttu-id="df409-122">대부분의 경우 미리 정의된 필드 속성은 측정값, 수준 또는 차원에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="df409-122">In most cases, predefined field properties apply to measures, levels, or dimensions.</span></span> <span data-ttu-id="df409-123">미리 정의된 필드 속성의 해당 값은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터 원본에 저장되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="df409-123">A predefined field property must have a corresponding value stored in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data source.</span></span> <span data-ttu-id="df409-124">예를 들어 값이 없거나 수준에서 측정값 전용 필드 속성을 지정한 경우에는 Null 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="df409-124">If a value does not exist, or if you specify a measure-only field property on a level (for example), the property returns a null value.</span></span>  
  
 <span data-ttu-id="df409-125">다음 구문 중 하나를 사용하여 식에서 미리 정의된 속성을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df409-125">You can use either of the following syntaxes to refer to a predefined property from an expression:</span></span>  
  
-   <span data-ttu-id="df409-126">*Fields!FieldName.PropertyName*</span><span class="sxs-lookup"><span data-stu-id="df409-126">*Fields!FieldName.PropertyName*</span></span>  
  
-   <span data-ttu-id="df409-127">*Fields!FieldName("PropertyName")*</span><span class="sxs-lookup"><span data-stu-id="df409-127">*Fields!FieldName("PropertyName")*</span></span>  
  
 <span data-ttu-id="df409-128">다음 표에서는 사용할 수 있는 미리 정의된 필드 속성 목록을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="df409-128">The following table provides a list of predefined field properties that you can use.</span></span>  
  
|<span data-ttu-id="df409-129">**속성**</span><span class="sxs-lookup"><span data-stu-id="df409-129">**Property**</span></span>|<span data-ttu-id="df409-130">**형식**</span><span class="sxs-lookup"><span data-stu-id="df409-130">**Type**</span></span>|<span data-ttu-id="df409-131">**설명 또는 필요한 값**</span><span class="sxs-lookup"><span data-stu-id="df409-131">**Description or expected value**</span></span>|  
|------------------|--------------|---------------------------------------|  
|`Value`|`Object`|<span data-ttu-id="df409-132">필드의 데이터 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="df409-132">Specifies the data value of the field.</span></span>|  
|`IsMissing`|`Boolean`|<span data-ttu-id="df409-133">필드가 결과 데이터 집합에 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="df409-133">Indicates whether the field was found in the resulting data set.</span></span>|  
|`UniqueName`|`String`|<span data-ttu-id="df409-134">수준의 정규화된 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="df409-134">Returns the fully qualified name of a level.</span></span> <span data-ttu-id="df409-135">예를 들어 `UniqueName` 직원의 값은 *[employee]. [ 직원 부서]. [학과]. [Sales]. & [북아메리카 Sales Manager]. & [272]를 &* 합니다.</span><span class="sxs-lookup"><span data-stu-id="df409-135">For example, the `UniqueName` value for an employee might be *[Employee].[Employee Department].[Department].&[Sales].&[North American Sales Manager].&[272]*.</span></span>|  
|`BackgroundColor`|`String`|<span data-ttu-id="df409-136">필드에 대해 데이터베이스에 정의된 배경색을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="df409-136">Returns the background color defined in the database for the field.</span></span>|  
|`Color`|`String`|<span data-ttu-id="df409-137">항목에 대해 데이터베이스에 정의된 전경색을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="df409-137">Returns the foreground color defined in the database for the item.</span></span>|  
|`FontFamily`|`String`|<span data-ttu-id="df409-138">항목에 대해 데이터베이스에 정의된 글꼴 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="df409-138">Returns the name of the font defined in the database for the item.</span></span>|  
|`FontSize`|`String`|<span data-ttu-id="df409-139">항목에 대해 데이터베이스에 정의된 글꼴 크기를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="df409-139">Returns the point size of the font defined in the database for the item.</span></span>|  
|`FontWeight`|`String`|<span data-ttu-id="df409-140">항목에 대해 데이터베이스에 정의된 글꼴 두께를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="df409-140">Returns the weight of the font defined in the database for the item.</span></span>|  
|`FontStyle`|`String`|<span data-ttu-id="df409-141">항목에 대해 데이터베이스에 정의된 글꼴 스타일을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="df409-141">Returns the style of the font defined in the database for the item.</span></span>|  
|`TextDecoration`|`String`|<span data-ttu-id="df409-142">항목에 대해 데이터베이스에 정의된 특수 텍스트 서식을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="df409-142">Returns special text formatting defined in the database for the item.</span></span>|  
|`FormattedValue`|`String`|<span data-ttu-id="df409-143">측정값 또는 주요 숫자 값의 형식화된 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="df409-143">Returns a formatted value for a measure or key figure.</span></span> <span data-ttu-id="df409-144">예를 들어 `FormattedValue` **Sales Amount Quota** 의 속성은 $1124400.00 같은 통화 형식을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="df409-144">For example, the `FormattedValue` property for **Sales Amount Quota** returns a currency format like $1,124,400.00.</span></span>|  
|`Key`|`Object`|<span data-ttu-id="df409-145">수준의 키를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="df409-145">Returns the key for a level.</span></span>|  
|`LevelNumber`|`Integer`|<span data-ttu-id="df409-146">부모-자식 계층에 대해 수준 또는 차원 번호를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="df409-146">For parent-child hierarchies, returns the level or dimension number.</span></span>|  
|`ParentUniqueName`|`String`|<span data-ttu-id="df409-147">부모-자식 계층에 대해 부모 수준의 정규화된 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="df409-147">For parent-child hierarchies, returns a fully qualified name of the parent level.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="df409-148">이러한 확장 필드 속성의 값은 보고서가 실행되어 해당 데이터 세트에 대한 데이터가 검색될 때 데이터 원본(예: [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 큐브)이 이러한 값을 제공하는 경우에만 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="df409-148">Values exist for these extended field properties only if the data source (for example, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] cube) provides these values when your report runs and retrieves the data for its datasets.</span></span> <span data-ttu-id="df409-149">이러한 값이 존재하는 경우 다음 섹션에 설명된 구문을 사용하여 모든 식에서 해당 필드 속성 값을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df409-149">You can then refer to those field property values from any expression using the syntax described in the following section.</span></span> <span data-ttu-id="df409-150">그러나 이러한 필드는 이 데이터 공급자에만 해당되므로 이러한 값을 변경해도 보고서 정의와 함께 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="df409-150">However, because these fields are specific to this data provider, changes that you make to these values are not saved with the report definition.</span></span>  
  
### <a name="example-extended-properties"></a><span data-ttu-id="df409-151">확장 속성 예</span><span class="sxs-lookup"><span data-stu-id="df409-151">Example Extended Properties</span></span>  
 <span data-ttu-id="df409-152">확장 속성을 설명하기 위해 다음 MDX 쿼리와 결과 집합에는 큐브에 대해 정의된 차원 특성에서 사용할 수 있는 몇 개의 멤버 속성이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df409-152">To illustrate extended properties, the following MDX query and result set include several member properties available from a dimension attribute defined for a cube.</span></span> <span data-ttu-id="df409-153">포함된 멤버 속성은 MEMBER_CAPTION, UNIQUENAME, Properties("Day Name"), MEMBER_VALUE, PARENT_UNIQUE_NAME 및 MEMBER_KEY입니다.</span><span class="sxs-lookup"><span data-stu-id="df409-153">The member properties included are MEMBER_CAPTION, UNIQUENAME, Properties("Day Name"), MEMBER_VALUE, PARENT_UNIQUE_NAME, and MEMBER_KEY.</span></span>  
  
 <span data-ttu-id="df409-154">이 MDX 쿼리는 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 예제 데이터베이스에 포함된 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] DW 데이터베이스의 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 큐브에 대해 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="df409-154">This MDX query runs against the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] cube in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] DW database, included with the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample databases.</span></span>  
  
```  
WITH MEMBER [Measures].[DateCaption]   
      AS '[Date].[Date].CURRENTMEMBER.MEMBER_CAPTION'   
   MEMBER [Measures].[DateUniqueName]   
      AS '[Date].[Date].CURRENTMEMBER.UNIQUENAME'   
   MEMBER [Measures].[DateDayName]   
      AS '[Date].[Date].Properties("Day Name")'   
   MEMBER [Measures].[DateValueinOriginalDatatype]   
      AS '[Date].[Date].CURRENTMEMBER.MEMBER_VALUE'   
   MEMBER [Measures].[DateParentUniqueName]   
      AS '[Date].[Date].CURRENTMEMBER.PARENT_UNIQUE_NAME'   
   MEMBER [Measures].[DateMemberKeyinOriginalDatatype]   
      AS '[Date].[Date].CURRENTMEMBER.MEMBER_KEY'   
SELECT {  
   [Measures].[DateCaption],   
   [Measures].[DateUniqueName],   
   [Measures].[DateDayName],   
   [Measures].[DateValueinOriginalDatatype],  
   [Measures].[DateParentUniqueName],  
   [Measures].[DateMemberKeyinOriginalDatatype]  
   } ON COLUMNS , [Date].[Date].ALLMEMBERS ON ROWS   
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="df409-155">MDX 쿼리 창에서 이 쿼리를 실행하면 1158개 행이 포함된 결과 집합이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="df409-155">When you run this query in an MDX query pane, you get a result set with 1158 rows.</span></span> <span data-ttu-id="df409-156">다음 표에서는 처음 4개 행을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="df409-156">The first four rows are shown in the following table.</span></span>  
  
|<span data-ttu-id="df409-157">DateCaption</span><span class="sxs-lookup"><span data-stu-id="df409-157">DateCaption</span></span>|<span data-ttu-id="df409-158">DateUniqueName</span><span class="sxs-lookup"><span data-stu-id="df409-158">DateUniqueName</span></span>|<span data-ttu-id="df409-159">DateDayName</span><span class="sxs-lookup"><span data-stu-id="df409-159">DateDayName</span></span>|<span data-ttu-id="df409-160">DateValueinOriginalDatatype</span><span class="sxs-lookup"><span data-stu-id="df409-160">DateValueinOriginalDatatype</span></span>|<span data-ttu-id="df409-161">DateParentUniqueName</span><span class="sxs-lookup"><span data-stu-id="df409-161">DateParentUniqueName</span></span>|<span data-ttu-id="df409-162">DateMemberKeyinOriginalDatatype</span><span class="sxs-lookup"><span data-stu-id="df409-162">DateMemberKeyinOriginalDatatype</span></span>|  
|-----------------|--------------------|-----------------|---------------------------------|--------------------------|-------------------------------------|  
|<span data-ttu-id="df409-163">All Periods</span><span class="sxs-lookup"><span data-stu-id="df409-163">All Periods</span></span>|<span data-ttu-id="df409-164">[Date].[Date].[All Periods]</span><span class="sxs-lookup"><span data-stu-id="df409-164">[Date].[Date].[All Periods]</span></span>|<span data-ttu-id="df409-165">(null)</span><span class="sxs-lookup"><span data-stu-id="df409-165">(null)</span></span>|<span data-ttu-id="df409-166">(null)</span><span class="sxs-lookup"><span data-stu-id="df409-166">(null)</span></span>|<span data-ttu-id="df409-167">(null)</span><span class="sxs-lookup"><span data-stu-id="df409-167">(null)</span></span>|<span data-ttu-id="df409-168">0</span><span class="sxs-lookup"><span data-stu-id="df409-168">0</span></span>|  
|<span data-ttu-id="df409-169">1-Jul-01</span><span class="sxs-lookup"><span data-stu-id="df409-169">1-Jul-01</span></span>|<span data-ttu-id="df409-170">[Date].[Date].&[1]</span><span class="sxs-lookup"><span data-stu-id="df409-170">[Date].[Date].&[1]</span></span>|<span data-ttu-id="df409-171">일요일</span><span class="sxs-lookup"><span data-stu-id="df409-171">Sunday</span></span>|<span data-ttu-id="df409-172">7/1/2001</span><span class="sxs-lookup"><span data-stu-id="df409-172">7/1/2001</span></span>|<span data-ttu-id="df409-173">[Date].[Date].[All Periods]</span><span class="sxs-lookup"><span data-stu-id="df409-173">[Date].[Date].[All Periods]</span></span>|<span data-ttu-id="df409-174">1</span><span class="sxs-lookup"><span data-stu-id="df409-174">1</span></span>|  
|<span data-ttu-id="df409-175">2-Jul-01</span><span class="sxs-lookup"><span data-stu-id="df409-175">2-Jul-01</span></span>|<span data-ttu-id="df409-176">[Date].[Date].&[2]</span><span class="sxs-lookup"><span data-stu-id="df409-176">[Date].[Date].&[2]</span></span>|<span data-ttu-id="df409-177">월요일</span><span class="sxs-lookup"><span data-stu-id="df409-177">Monday</span></span>|<span data-ttu-id="df409-178">7/2/2001</span><span class="sxs-lookup"><span data-stu-id="df409-178">7/2/2001</span></span>|<span data-ttu-id="df409-179">[Date].[Date].[All Periods]</span><span class="sxs-lookup"><span data-stu-id="df409-179">[Date].[Date].[All Periods]</span></span>|<span data-ttu-id="df409-180">2</span><span class="sxs-lookup"><span data-stu-id="df409-180">2</span></span>|  
|<span data-ttu-id="df409-181">3-Jul-01</span><span class="sxs-lookup"><span data-stu-id="df409-181">3-Jul-01</span></span>|<span data-ttu-id="df409-182">[Date].[Date].&[3]</span><span class="sxs-lookup"><span data-stu-id="df409-182">[Date].[Date].&[3]</span></span>|<span data-ttu-id="df409-183">화요일</span><span class="sxs-lookup"><span data-stu-id="df409-183">Tuesday</span></span>|<span data-ttu-id="df409-184">7/3/2001</span><span class="sxs-lookup"><span data-stu-id="df409-184">7/3/2001</span></span>|<span data-ttu-id="df409-185">[Date].[Date].[All Periods]</span><span class="sxs-lookup"><span data-stu-id="df409-185">[Date].[Date].[All Periods]</span></span>|<span data-ttu-id="df409-186">3</span><span class="sxs-lookup"><span data-stu-id="df409-186">3</span></span>|  
  
 <span data-ttu-id="df409-187">그래픽 모드로 MDX 쿼리 디자이너를 사용하여 작성한 기본 MDX 쿼리는 차원 속성으로 MEMBER_CAPTION과 UNIQUENAME만 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="df409-187">Default MDX queries built using the MDX Query Designer in graphical mode only include MEMBER_CAPTION and UNIQUENAME for dimension properties.</span></span> <span data-ttu-id="df409-188">기본적으로 이러한 값은 항상 `String` 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="df409-188">By default, these values always are data type `String`.</span></span>  
  
 <span data-ttu-id="df409-189">원래 데이터 형식에 멤버 속성이 필요한 경우 텍스트 기반 쿼리 디자이너에서 기본 MDX 문을 수정하여 추가 속성 MEMBER_VALUE를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df409-189">If you need a member property in its original data type, you can include an additional property MEMBER_VALUE by modifying the default MDX statement in the text-based query designer.</span></span> <span data-ttu-id="df409-190">간단한 다음 MDX 문에서 MEMBER_VALUE는 검색할 차원 속성 목록에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="df409-190">In the following simple MDX statement, MEMBER_VALUE has been added to the list of dimension properties to retrieve.</span></span>  
  
```  
SELECT NON EMPTY {[Measures].[Order Count]} ON COLUMNS,   
NON EMPTY { ([Date].[Month of Year].[Month of Year] ) }   
DIMENSION PROPERTIES   
   MEMBER_CAPTION, MEMBER_UNIQUE_NAME, MEMBER_VALUE ON ROWS   
FROM [Adventure Works]  
CELL PROPERTIES   
   VALUE, BACK_COLOR, FORE_COLOR,   
   FORMATTED_VALUE, FORMAT_STRING,   
   FONT_NAME, FONT_SIZE, FONT_FLAGS  
```  
  
 <span data-ttu-id="df409-191">다음 표에서는 MDX 결과 창에 나타나는 결과의 처음 4개 행을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="df409-191">The first four rows of the result in the MDX Results pane appear in the following table.</span></span>  
  
|<span data-ttu-id="df409-192">Month of Year</span><span class="sxs-lookup"><span data-stu-id="df409-192">Month of Year</span></span>|<span data-ttu-id="df409-193">Order Count</span><span class="sxs-lookup"><span data-stu-id="df409-193">Order Count</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="df409-194">January</span><span class="sxs-lookup"><span data-stu-id="df409-194">January</span></span>|<span data-ttu-id="df409-195">2,481</span><span class="sxs-lookup"><span data-stu-id="df409-195">2,481</span></span>|  
|<span data-ttu-id="df409-196">February</span><span class="sxs-lookup"><span data-stu-id="df409-196">February</span></span>|<span data-ttu-id="df409-197">2,684</span><span class="sxs-lookup"><span data-stu-id="df409-197">2,684</span></span>|  
|<span data-ttu-id="df409-198">3월</span><span class="sxs-lookup"><span data-stu-id="df409-198">March</span></span>|<span data-ttu-id="df409-199">2,749</span><span class="sxs-lookup"><span data-stu-id="df409-199">2,749</span></span>|  
|<span data-ttu-id="df409-200">April</span><span class="sxs-lookup"><span data-stu-id="df409-200">April</span></span>|<span data-ttu-id="df409-201">2,739</span><span class="sxs-lookup"><span data-stu-id="df409-201">2,739</span></span>|  
  
 <span data-ttu-id="df409-202">속성은 MDX SELECT 문의 일부이지만 결과 집합 열에 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="df409-202">Even though the properties are part of the MDX select statement, they do not appear in the result set columns.</span></span> <span data-ttu-id="df409-203">그러나 확장 속성 기능을 사용하여 이 데이터를 보고서에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df409-203">Nevertheless, the data is available for a report by using the extended properties feature.</span></span> <span data-ttu-id="df409-204">의 MDX 쿼리 결과 창에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 셀을 두 번 클릭 하 고 해당 셀이 큐브에 설정 된 경우 셀 속성 값을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df409-204">In an MDX query result pane in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you can double-click on the cell and see the cell property values if they are set in the cube.</span></span> <span data-ttu-id="df409-205">1,379가 포함된 첫 번째 Order Count 셀을 두 번 클릭하면 다음 셀 속성이 있는 팝업 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="df409-205">If you double-click on the first Order Count cell that contains 1,379, you will see a pop-up window with the following cell properties:</span></span>  
  
|<span data-ttu-id="df409-206">속성</span><span class="sxs-lookup"><span data-stu-id="df409-206">Property</span></span>|<span data-ttu-id="df409-207">값</span><span class="sxs-lookup"><span data-stu-id="df409-207">Value</span></span>|  
|--------------|-----------|  
|<span data-ttu-id="df409-208">CellOrdinal</span><span class="sxs-lookup"><span data-stu-id="df409-208">CellOrdinal</span></span>|<span data-ttu-id="df409-209">0</span><span class="sxs-lookup"><span data-stu-id="df409-209">0</span></span>|  
|<span data-ttu-id="df409-210">값</span><span class="sxs-lookup"><span data-stu-id="df409-210">VALUE</span></span>|<span data-ttu-id="df409-211">2481</span><span class="sxs-lookup"><span data-stu-id="df409-211">2481</span></span>|  
|<span data-ttu-id="df409-212">BACK_COLOR</span><span class="sxs-lookup"><span data-stu-id="df409-212">BACK_COLOR</span></span>|<span data-ttu-id="df409-213">(null)</span><span class="sxs-lookup"><span data-stu-id="df409-213">(null)</span></span>|  
|<span data-ttu-id="df409-214">FORE_COLOR</span><span class="sxs-lookup"><span data-stu-id="df409-214">FORE_COLOR</span></span>|<span data-ttu-id="df409-215">(null)</span><span class="sxs-lookup"><span data-stu-id="df409-215">(null)</span></span>|  
|<span data-ttu-id="df409-216">FORMATTED_VALUE</span><span class="sxs-lookup"><span data-stu-id="df409-216">FORMATTED_VALUE</span></span>|<span data-ttu-id="df409-217">2,481</span><span class="sxs-lookup"><span data-stu-id="df409-217">2,481</span></span>|  
|<span data-ttu-id="df409-218">FORMAT_STRING</span><span class="sxs-lookup"><span data-stu-id="df409-218">FORMAT_STRING</span></span>|<span data-ttu-id="df409-219">#,#</span><span class="sxs-lookup"><span data-stu-id="df409-219">#,#</span></span>|  
|<span data-ttu-id="df409-220">FONT_NAME</span><span class="sxs-lookup"><span data-stu-id="df409-220">FONT_NAME</span></span>|<span data-ttu-id="df409-221">(null)</span><span class="sxs-lookup"><span data-stu-id="df409-221">(null)</span></span>|  
|<span data-ttu-id="df409-222">FONT_SIZE</span><span class="sxs-lookup"><span data-stu-id="df409-222">FONT_SIZE</span></span>|<span data-ttu-id="df409-223">(null)</span><span class="sxs-lookup"><span data-stu-id="df409-223">(null)</span></span>|  
|<span data-ttu-id="df409-224">FONT_FLAGS</span><span class="sxs-lookup"><span data-stu-id="df409-224">FONT_FLAGS</span></span>|<span data-ttu-id="df409-225">(null)</span><span class="sxs-lookup"><span data-stu-id="df409-225">(null)</span></span>|  
  
 <span data-ttu-id="df409-226">이 쿼리를 사용하여 보고서 데이터 세트를 만들고 테이블에 바인딩하면 필드의 기본 VALUE 속성(예: `=Fields!Month_of_Year!Value`)을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df409-226">If you create a report dataset with this query and bind the dataset to a table, you can see the default VALUE property for a field, for example, `=Fields!Month_of_Year!Value`.</span></span> <span data-ttu-id="df409-227">이 식을 테이블에 대한 정렬 식으로 설정하면 Value 필드가 `String` 데이터 형식을 사용하므로 테이블이 월을 기준으로 사전순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="df409-227">If you set this expression as the sort expression for the table, your results will be to sort the table alphabetically by month because the Value field uses a `String` data type.</span></span> <span data-ttu-id="df409-228">월이 연도에서 발생하는 순서대로, 즉 1월이 처음이고 12월이 마지막이 되도록 테이블을 정렬하려면 다음 식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="df409-228">To sort the table in so that the months are in the order they occur in the year with January first and December last, use the following expression:</span></span>  
  
```  
=Fields!Month_of_Year("MEMBER_VALUE")  
```  
  
 <span data-ttu-id="df409-229">이렇게 하면 데이터 원본의 원래 정수 데이터 형식으로 필드 값이 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="df409-229">This sorts the value of the field in its original integer data type from the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df409-230">참고 항목</span><span class="sxs-lookup"><span data-stu-id="df409-230">See Also</span></span>  
 <span data-ttu-id="df409-231">[식&#40;보고서 작성기 및 SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="df409-231">[Expressions &#40;Report Builder and SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="df409-232">[식의 기본 제공 컬렉션은 보고서 작성기 및 SSRS를 &#40;&#41;](../report-design/built-in-collections-in-expressions-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="df409-232">[Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md) </span></span>  
 [<span data-ttu-id="df409-233">데이터 세트 필드 컬렉션&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="df409-233">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
  
  
