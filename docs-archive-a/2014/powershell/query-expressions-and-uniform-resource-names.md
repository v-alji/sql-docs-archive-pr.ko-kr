---
title: 쿼리 식 및 URN | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
helpviewer_keywords:
- query expressions
- unique resource names
- URN
ms.assetid: e0d30dbe-7daf-47eb-8412-1b96792b6fb9
author: stevestein
ms.author: sstein
ms.openlocfilehash: db6e311dd7d8a824b0e2f22e538e15eefa9fd9ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650152"
---
# <a name="query-expressions-and-uniform-resource-names"></a><span data-ttu-id="84475-102">쿼리 식 및 URN</span><span class="sxs-lookup"><span data-stu-id="84475-102">Query Expressions and Uniform Resource Names</span></span>
  <span data-ttu-id="84475-103">SMO( [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Object) 모델 및 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 스냅인은 XPath 식과 유사한 두 가지 유형의 식 문자열을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-103">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Object (SMO) models and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell snap-ins use two types of expression strings that are similar to XPath expressions.</span></span> <span data-ttu-id="84475-104">쿼리 식은 개체 모델 계층 구조에 있는 하나 이상의 개체를 열거하는 데 사용되는 조건 집합을 지정하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="84475-104">Query expressions are strings that specify a set of criteria used to enumerate one or more objects in an object model hierarchy.</span></span> <span data-ttu-id="84475-105">URN(Uniform Resource Name)은 단일 개체를 고유하게 식별하는 특정 유형의 쿼리 식 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="84475-105">A Uniform Resource Name (URN) is a specific type of query expression string that uniquely identifies a single object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84475-106">구문</span><span class="sxs-lookup"><span data-stu-id="84475-106">Syntax</span></span>  
  
```
      Object1  
      [<FilterExpression1>]/ ... /ObjectN[<FilterExpressionN>]<FilterExpression>::=  
<PropertyExpression> [and <PropertyExpression>][...n]  
  
<PropertyExpression>::=@BooleanPropertyName=true()  
 | @BooleanPropertyName=false()  
 | contains(@StringPropertyName, 'PatternString')  
  | @StringPropertyName='String'  
 | @DatePropertyName=datetime('DateString')  
 | is_null(@PropertyName)  
 | not(<PropertyExpression>)  
```  
  
## <a name="arguments"></a><span data-ttu-id="84475-107">인수</span><span class="sxs-lookup"><span data-stu-id="84475-107">Arguments</span></span>  
 <span data-ttu-id="84475-108">*Object*</span><span class="sxs-lookup"><span data-stu-id="84475-108">*Object*</span></span>  
 <span data-ttu-id="84475-109">식 문자열의 Object 노드에서 나타내는 개체 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-109">Specifies the type of object that is represented at that node of the expression string.</span></span> <span data-ttu-id="84475-110">각 개체는 이러한 SMO 개체 모델 네임스페이스의 컬렉션 클래스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="84475-110">Each object represents a collection class from these SMO object model namespaces:</span></span>  
  
 <xref:Microsoft.SqlServer.Management.Smo>  
  
 <xref:Microsoft.SqlServer.Management.Smo.Agent>  
  
 <xref:Microsoft.SqlServer.Management.Smo.Broker>  
  
 <xref:Microsoft.SqlServer.Management.Smo.Mail>  
  
 <xref:Microsoft.SqlServer.Management.Dmf>  
  
 <xref:Microsoft.SqlServer.Management.Facets>  
  
 <xref:Microsoft.SqlServer.Management.RegisteredServers>  
  
 <xref:Microsoft.SqlServer.Management.Smo.RegSvrEnum>  
  
 <span data-ttu-id="84475-111">예를 들어 **ServerCollection** 클래스에 대한 서버, **DatabaseCollection** 클래스에 대한 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-111">For example, specify Server for the **ServerCollection** class, Database for the **DatabaseCollection** class.</span></span>  
  
 <span data-ttu-id="84475-112">\@*PropertyName*</span><span class="sxs-lookup"><span data-stu-id="84475-112">\@*PropertyName*</span></span>  
 <span data-ttu-id="84475-113">*Object*에서 지정된 개체와 연결되는 클래스 속성 중 하나의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-113">Specifies the name of one of the properties of the class that is associated with the object specified in *Object*.</span></span> <span data-ttu-id="84475-114">속성 이름은 \@ 문자로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-114">The name of the property must be prefixed with the \@ character.</span></span> <span data-ttu-id="84475-115">예를 들어 \@ **데이터베이스** 클래스 속성 **isansinull**에 대해 isansinull을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-115">For example, specify \@IsAnsiNull for the **Database** class property **IsAnsiNull**.</span></span>  
  
 <span data-ttu-id="84475-116">\@*BooleanPropertyName*= true ()</span><span class="sxs-lookup"><span data-stu-id="84475-116">\@*BooleanPropertyName*=true()</span></span>  
 <span data-ttu-id="84475-117">지정된 부울 속성이 TRUE로 설정된 개체를 모두 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-117">Enumerates all objects where the specified Boolean property is set to TRUE.</span></span>  
  
 <span data-ttu-id="84475-118">\@*BooleanPropertyName*= false ()</span><span class="sxs-lookup"><span data-stu-id="84475-118">\@*BooleanPropertyName*=false()</span></span>  
 <span data-ttu-id="84475-119">지정된 부울 속성이 FALSE로 설정된 개체를 모두 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-119">Enumerates all objects where the specified Boolean property is set to FALSE.</span></span>  
  
 <span data-ttu-id="84475-120">contains ( \@ *stringpropertyname*, '*PatternString*')</span><span class="sxs-lookup"><span data-stu-id="84475-120">contains(\@*StringPropertyName*, '*PatternString*')</span></span>  
 <span data-ttu-id="84475-121">지정된 문자열 속성에 '*PatternString*'에 지정된 문자열 집합이 하나 이상 포함되어 있는 개체를 모두 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-121">Enumerates all objects where the specified string property contains at least one occurrence of the set of characters that is specified in '*PatternString*'.</span></span>  
  
 <span data-ttu-id="84475-122">\@*StringPropertyName*='*PatternString*'</span><span class="sxs-lookup"><span data-stu-id="84475-122">\@*StringPropertyName*='*PatternString*'</span></span>  
 <span data-ttu-id="84475-123">지정된 문자열 속성 값이 '*PatternString*'에 지정된 문자 패턴과 정확하게 같은 개체를 모두 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-123">Enumerates all objects where the value of the specified string property is exactly the same as the character pattern that is specified in '*PatternString*'.</span></span>  
  
 <span data-ttu-id="84475-124">\@*DatePropertyName*= datetime('*DateString*')</span><span class="sxs-lookup"><span data-stu-id="84475-124">\@*DatePropertyName*= datetime('*DateString*')</span></span>  
 <span data-ttu-id="84475-125">지정된 날짜 속성 값이 '*DateString*'에 지정된 날짜와 일치하는 개체를 모두 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-125">Enumerates all objects where the value of the specified date property matches the date that is specified in '*DateString*'.</span></span> <span data-ttu-id="84475-126">*DateString* 은 yyyy-mm-dd hh:mi:ss.mmm 형식을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-126">*DateString* must follow the format yyyy-mm-dd hh:mi:ss.mmm</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="84475-127">yyyy</span><span class="sxs-lookup"><span data-stu-id="84475-127">yyyy</span></span>|<span data-ttu-id="84475-128">4자리 연도</span><span class="sxs-lookup"><span data-stu-id="84475-128">Four digit year.</span></span>|  
|<span data-ttu-id="84475-129">MM</span><span class="sxs-lookup"><span data-stu-id="84475-129">mm</span></span>|<span data-ttu-id="84475-130">두 자리 월(01 - 12)</span><span class="sxs-lookup"><span data-stu-id="84475-130">Two digit month (01 through 12).</span></span>|  
|<span data-ttu-id="84475-131">dd</span><span class="sxs-lookup"><span data-stu-id="84475-131">dd</span></span>|<span data-ttu-id="84475-132">두 자리 날짜(01 - 31)</span><span class="sxs-lookup"><span data-stu-id="84475-132">Two digit date (01 through 31).</span></span>|  
|<span data-ttu-id="84475-133">hh</span><span class="sxs-lookup"><span data-stu-id="84475-133">hh</span></span>|<span data-ttu-id="84475-134">24시간제를 사용하는 두 자리 시간(01 - 23)</span><span class="sxs-lookup"><span data-stu-id="84475-134">Two digit hour using a 24 hour clock (01 through 23).</span></span>|  
|<span data-ttu-id="84475-135">mi</span><span class="sxs-lookup"><span data-stu-id="84475-135">mi</span></span>|<span data-ttu-id="84475-136">두 자리 분(01 - 59)</span><span class="sxs-lookup"><span data-stu-id="84475-136">Two digit minutes (01 through 59).</span></span>|  
|<span data-ttu-id="84475-137">ss</span><span class="sxs-lookup"><span data-stu-id="84475-137">ss</span></span>|<span data-ttu-id="84475-138">두 자리 초(01 - 59)</span><span class="sxs-lookup"><span data-stu-id="84475-138">Two digit seconds (01 through 59).</span></span>|  
|<span data-ttu-id="84475-139">mmm</span><span class="sxs-lookup"><span data-stu-id="84475-139">mmm</span></span>|<span data-ttu-id="84475-140">밀리초 수(001 - 999)</span><span class="sxs-lookup"><span data-stu-id="84475-140">Number of milliseconds (001 through 999).</span></span>|  
  
 <span data-ttu-id="84475-141">이 형식으로 지정된 날짜를 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에 저장된 모든 날짜 형식에 대해 평가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84475-141">The dates that are specified in this format can be evaluated against any date format that is stored in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="84475-142">is_null ( \@ *PropertyName*)</span><span class="sxs-lookup"><span data-stu-id="84475-142">is_null(\@*PropertyName*)</span></span>  
 <span data-ttu-id="84475-143">지정된 속성 값이 NULL인 개체를 모두 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-143">Enumerates all objects where the specified property has a value of NULL.</span></span>  
  
 <span data-ttu-id="84475-144">not ( \<*PropertyExpression*> )</span><span class="sxs-lookup"><span data-stu-id="84475-144">not(\<*PropertyExpression*>)</span></span>  
 <span data-ttu-id="84475-145">*PropertyExpression*의 평가 값을 부정하고 *PropertyExpression*에 지정된 조건과 일치하지 않는 개체를 모두 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-145">Negates the evaluation value of the *PropertyExpression*, enumerating all objects that do not match the condition specified in *PropertyExpression*.</span></span> <span data-ttu-id="84475-146">예를 들어 not(contains(\@Name, 'xyz'))는 이름에 xyz 문자열이 없는 개체를 모두 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-146">For example, not(contains(\@Name, 'xyz')) enumerates all objects that do not have the string xyz in their names.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84475-147">설명</span><span class="sxs-lookup"><span data-stu-id="84475-147">Remarks</span></span>  
 <span data-ttu-id="84475-148">쿼리 식은 SMO 모델 계층 구조에 있는 노드를 열거하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="84475-148">Query expressions are strings that enumerate the nodes in an SMO model hierarchy.</span></span> <span data-ttu-id="84475-149">각 노드에는 해당 노드에서 열거되는 개체를 결정하는 조건을 지정하는 필터 식이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84475-149">Each node has a filter expression that specifies the criteria for determining which objects at that node are enumerated.</span></span> <span data-ttu-id="84475-150">쿼리 식은 XPath 식 언어에서 모델링됩니다.</span><span class="sxs-lookup"><span data-stu-id="84475-150">Query expressions are modeled on the XPath expression language.</span></span> <span data-ttu-id="84475-151">쿼리 식은 XPath에서 지원하는 작은 식 집합을 구현하고 XPath에 없는 일부 확장도 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-151">Query expressions implement a small subset of the expressions that are supported by XPath, and also have some extensions that are not found in XPath.</span></span> <span data-ttu-id="84475-152">XPath 식은 XML 문서에서 하나 이상의 태그를 열거하는 데 사용되는 조건 집합을 지정하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="84475-152">XPath expressions are strings that specify a set of criteria that are used to enumerate one or more of the tags in an XML document.</span></span> <span data-ttu-id="84475-153">XPath에 대한 자세한 내용은 [W3C XPath Language](http://www.w3.org/TR/xpath20/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="84475-153">For more information about XPath, see [W3C XPath Language](http://www.w3.org/TR/xpath20/).</span></span>  
  
 <span data-ttu-id="84475-154">쿼리 식은 Server 개체에 대한 절대 참조로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-154">Query expressions must start with an absolute reference to the Server object.</span></span> <span data-ttu-id="84475-155">/로 시작하는 상대 식은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="84475-155">Relative expressions with a leading / are not allowed.</span></span> <span data-ttu-id="84475-156">쿼리 식에 지정된 개체 시퀀스는 관련 개체 모델에 있는 컬렉션 개체의 계층 구조를 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-156">The sequence of objects that are specified in a query expression must follow the hierarchy of collection objects in the associated object model.</span></span> <span data-ttu-id="84475-157">예를 들어 Microsoft.SqlServer.Management.Smo 네임스페이스의 개체를 참조하는 쿼리 식은 Server 노드로 시작하고 그 다음에 Database 노드 등이 와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-157">For example, a query expression that references objects in the Microsoft.SqlServer.Management.Smo namespace must start with a Server node followed by a Database node, and so on.</span></span>  
  
 <span data-ttu-id="84475-158">*\<FilterExpression>* 개체에 대해가 지정 되지 않은 경우 해당 노드의 모든 개체가 열거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84475-158">If a *\<FilterExpression>* is not specified for an object, all the objects at that node are enumerated.</span></span>  
  
## <a name="uniform-resource-names-urn"></a><span data-ttu-id="84475-159">URN(Uniform Resource Name)</span><span class="sxs-lookup"><span data-stu-id="84475-159">Uniform Resource Names (URN)</span></span>  
 <span data-ttu-id="84475-160">URN은 쿼리 식의 하위 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="84475-160">URNs are a subset of query expressions.</span></span> <span data-ttu-id="84475-161">각 URN은 단일 개체에 대한 정규화된 참조를 형성합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-161">Each URN forms a fully-qualified reference to a single object.</span></span> <span data-ttu-id="84475-162">일반적인 URN에서는 Name 속성을 사용하여 각 노드의 단일 개체를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-162">A typical URN uses the Name property to identify a single object at each node.</span></span> <span data-ttu-id="84475-163">예를 들어 이 URN은 특정 열을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-163">For example, this URN refers to a specific column:</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012']/Table[@Name='SalesPerson' and @Schema='Sales']/Column[@Name='SalesPersonID']  
```  
  
## <a name="examples"></a><span data-ttu-id="84475-164">예</span><span class="sxs-lookup"><span data-stu-id="84475-164">Examples</span></span>  
  
### <a name="a-enumerating-objects-using-false"></a><span data-ttu-id="84475-165">A.</span><span class="sxs-lookup"><span data-stu-id="84475-165">A.</span></span> <span data-ttu-id="84475-166">false()를 사용하여 개체 열거</span><span class="sxs-lookup"><span data-stu-id="84475-166">Enumerating objects using false()</span></span>  
 <span data-ttu-id="84475-167">이 쿼리 식은 **MyComputer** 의 기본 인스턴스에서 **AutoClose**특성이 false로 설정된 데이터베이스를 모두 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-167">This query expression enumerates all the databases that have the **AutoClose** attribute set to false in the default instance on **MyComputer**.</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@AutoClose=false()]  
```  
  
### <a name="b-enumerating-objects-using-contains"></a><span data-ttu-id="84475-168">B.</span><span class="sxs-lookup"><span data-stu-id="84475-168">B.</span></span> <span data-ttu-id="84475-169">contains를 사용하여 개체 열거</span><span class="sxs-lookup"><span data-stu-id="84475-169">Enumerating objects using contains</span></span>  
 <span data-ttu-id="84475-170">이 쿼리 식은 대/소문자를 구분하지 않고 이름에 'm' 문자가 있는 데이터베이스를 모두 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-170">This query expression enumerates all the databases that are case-insensitive and have the character 'm' in their name.</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@CaseSensitive=false() and contains(@Name, 'm')]   
```  
  
### <a name="c-enumerating-objects-using-not"></a><span data-ttu-id="84475-171">C.</span><span class="sxs-lookup"><span data-stu-id="84475-171">C.</span></span> <span data-ttu-id="84475-172">not을 사용하여 개체 열거</span><span class="sxs-lookup"><span data-stu-id="84475-172">Enumerating objects using not</span></span>  
 <span data-ttu-id="84475-173">이 쿼리 식은 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] Production **스키마에 없으며 테이블 이름에 History라는 단어를 포함하는** 테이블을 모두 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-173">This query expression enumerates all of [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] tables that are not in the **Production** schema and contain the word History in the table name:</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012']/Table[not(@Schema='Production') and contains(@Name, 'History')]  
```  
  
### <a name="d-not-supplying-a-filter-expression-for-the-final-node"></a><span data-ttu-id="84475-174">D.</span><span class="sxs-lookup"><span data-stu-id="84475-174">D.</span></span> <span data-ttu-id="84475-175">최종 노드에 대한 필터 식 제공 안 함</span><span class="sxs-lookup"><span data-stu-id="84475-175">Not supplying a filter expression for the final node</span></span>  
 <span data-ttu-id="84475-176">이 쿼리 식은 **AdventureWorks2012.Sales.SalesPerson** 테이블에서 모든 열을 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-176">This query expression enumerates all the columns in the **AdventureWorks2012.Sales.SalesPerson** table:</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012"]/Table[@Schema='Sales' and @Name='SalesPerson']/Columns  
```  
  
### <a name="e-enumerating-objects-using-datetime"></a><span data-ttu-id="84475-177">E.</span><span class="sxs-lookup"><span data-stu-id="84475-177">E.</span></span> <span data-ttu-id="84475-178">datetime을 사용하여 개체 열거</span><span class="sxs-lookup"><span data-stu-id="84475-178">Enumerating objects using datetime</span></span>  
 <span data-ttu-id="84475-179">이 쿼리 식은 특정 시간에 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 데이터베이스에서 만든 테이블을 모두 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-179">This query expression enumerates all the tables that are created in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database at a specific time:</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012"]/Table[@CreateDate=datetime('2008-03-21 19:49:32.647')]  
```  
  
### <a name="f-enumerating-objects-using-is_null"></a><span data-ttu-id="84475-180">F.</span><span class="sxs-lookup"><span data-stu-id="84475-180">F.</span></span> <span data-ttu-id="84475-181">is_null을 사용하여 개체 열거</span><span class="sxs-lookup"><span data-stu-id="84475-181">Enumerating objects using is_null</span></span>  
 <span data-ttu-id="84475-182">이 쿼리 식은 마지막 수정 날짜 속성에 대한 NULL이 없는 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 데이터베이스의 테이블을 모두 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="84475-182">This query expression enumerates all the tables in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database that do not have NULL for their date last modified property:</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012"]/Table[Not(is_null(@DateLastModified))]  
```  
  
## <a name="see-also"></a><span data-ttu-id="84475-183">참고 항목</span><span class="sxs-lookup"><span data-stu-id="84475-183">See Also</span></span>  
 <span data-ttu-id="84475-184">[호출-Polic옛 평가 cmdlet](../database-engine/invoke-policyevaluation-cmdlet.md) </span><span class="sxs-lookup"><span data-stu-id="84475-184">[Invoke-PolicyEvaluation cmdlet](../database-engine/invoke-policyevaluation-cmdlet.md) </span></span>  
 [<span data-ttu-id="84475-185">SQL Server Audit&#40;데이터베이스 엔진&#41;</span><span class="sxs-lookup"><span data-stu-id="84475-185">SQL Server Audit &#40;Database Engine&#41;</span></span>](../relational-databases/security/auditing/sql-server-audit-database-engine.md)  
