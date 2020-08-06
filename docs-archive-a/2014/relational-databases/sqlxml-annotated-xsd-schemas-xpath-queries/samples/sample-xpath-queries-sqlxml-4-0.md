---
title: 예제 XPath 쿼리 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- examples [SQLXML], XPath
- sample applications [SQLXML]
- sample XPath queries [SQLXML]
- mapping schema [SQLXML], queries
- XPath queries [SQLXML], samples
ms.assetid: 1595c2d4-0e9c-4969-84c8-a793a32df57d
author: rothja
ms.author: jroth
ms.openlocfilehash: 08ed32433e9bed4cc1542d6700ad73dc96f3c2dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646289"
---
# <a name="sample-xpath-queries-sqlxml-40"></a><span data-ttu-id="6ea35-102">XPath 쿼리 예제(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="6ea35-102">Sample XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="6ea35-103">이 섹션에서는 SQLXML 4.0용 XPath 쿼리 예제를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6ea35-103">This section provides examples of XPath queries for SQLXML 4.0.</span></span> <span data-ttu-id="6ea35-104">이해를 돕기 위해 이 예제 XPath 쿼리는 ADO를 사용하여 실행한 템플릿에 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6ea35-104">For illustration purposes, these example XPath queries are specified in a template executed using ADO.</span></span> <span data-ttu-id="6ea35-105">따라서 이 섹션에 제공되는 SampleSchema1.xml이라는 매핑 스키마 파일을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ea35-105">Therefore, you must use a mapping schema file, SampleSchema1.xml, which is also provided in this section.</span></span> <span data-ttu-id="6ea35-106">이 파일을 템플릿이 저장된 디렉터리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6ea35-106">Save this file in the directory where your templates are stored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6ea35-107">이 섹션의 예제 쿼리는 쿼리에서 수행되는 XPath 작업의 유형별로 그룹화됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ea35-107">The sample queries in this section are grouped by the type of XPath operation that is performed by the query.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6ea35-108">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="6ea35-108">In This Section</span></span>  
 [<span data-ttu-id="6ea35-109">&#40;SQLXML 4.0의 XPath 예제에 대해 주석이 추가 된 샘플 XSD 스키마&#41;</span><span class="sxs-lookup"><span data-stu-id="6ea35-109">Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;</span></span>](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)  
 <span data-ttu-id="6ea35-110">이 섹션에 제공된 XPath 쿼리 예제에서 이 파일을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6ea35-110">Use this file with the XPath query examples provided in this section.</span></span>  
  
 [<span data-ttu-id="6ea35-111">XPath 쿼리에 축 지정 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="6ea35-111">Specifying Axes in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-axes-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="6ea35-112">XPath 쿼리에 축을 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6ea35-112">Illustrates how axes are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="6ea35-113">XPath 쿼리에서 부울 값 조건자 지정 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="6ea35-113">Specifying Boolean-Valued Predicates in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-boolean-valued-predicates-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="6ea35-114">XPath 쿼리에 부울 값 조건자를 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6ea35-114">Illustrates how Boolean-valued predicates are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="6ea35-115">XPath 쿼리에 관계형 연산자 지정 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="6ea35-115">Specifying Relational Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-relational-operators-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="6ea35-116">XPath 쿼리에 관계형 연산자를 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6ea35-116">Illustrates how relational operators are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="6ea35-117">XPath 쿼리에 산술 연산자 지정 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="6ea35-117">Specifying Arithmetic Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="6ea35-118">XPath 쿼리에 산술 연산자를 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6ea35-118">Illustrates how arithmetic operators are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="6ea35-119">XPath 쿼리에 명시적 변환 함수 지정 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="6ea35-119">Specifying Explicit Conversion Functions in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="6ea35-120">XPath 쿼리에 명시적 변환 함수를 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6ea35-120">Illustrates how explicit conversion functions are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="6ea35-121">XPath 쿼리에 부울 연산자 지정 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="6ea35-121">Specifying Boolean Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-boolean-operators-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="6ea35-122">XPath 쿼리에 부울 연산자를 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6ea35-122">Illustrates how Boolean operators are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="6ea35-123">XPath 쿼리에 부울 함수 지정 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="6ea35-123">Specifying Boolean Functions in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-boolean-functions-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="6ea35-124">XPath 쿼리에 부울 함수를 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6ea35-124">Illustrates how Boolean functions are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="6ea35-125">XPath 쿼리에 XPath 변수 지정 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="6ea35-125">Specifying XPath Variables in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-xpath-variables-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="6ea35-126">XPath 쿼리에 XPath 변수를 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6ea35-126">Illustrates how XPath variables are specified in XPath queries.</span></span>  
  
  
