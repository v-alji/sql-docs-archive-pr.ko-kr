---
title: 명명 규칙 지정 (스키마 생성 마법사) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.schemagenwizard.namingconventions.f1
ms.assetid: 02d830ea-5b1f-4485-9f94-d64b8bea592b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2e9588b49331934041cad888142d29d189fc1a7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653553"
---
# <a name="specify-naming-conventions-schema-generation-wizard-analysis-services---multidimensional-data"></a><span data-ttu-id="11d79-102">명명 규칙 지정(스키마 생성 마법사)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="11d79-102">Specify Naming Conventions (Schema Generation Wizard) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="11d79-103">**명명 규칙 지정** 페이지를 사용하여 스키마 생성 마법사에서 스키마 개체를 만들 때 사용하는 명명 규칙을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11d79-103">Use the **Specify Naming Conventions** page to define the naming conventions that the Schema Generation Wizard uses when creating schema objects.</span></span>  
  
## <a name="options"></a><span data-ttu-id="11d79-104">옵션</span><span class="sxs-lookup"><span data-stu-id="11d79-104">Options</span></span>  
 <span data-ttu-id="11d79-105">**옵션**</span><span class="sxs-lookup"><span data-stu-id="11d79-105">**Option**</span></span>  
 <span data-ttu-id="11d79-106">마법사에서 사용할 명명 규칙을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="11d79-106">Specify the naming conventions for the wizard to use.</span></span> <span data-ttu-id="11d79-107">다음 표에서는 지정할 수 있는 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="11d79-107">The following table describes the options you can specify.</span></span>  
  
|<span data-ttu-id="11d79-108">옵션</span><span class="sxs-lookup"><span data-stu-id="11d79-108">Option</span></span>|<span data-ttu-id="11d79-109">Description</span><span class="sxs-lookup"><span data-stu-id="11d79-109">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="11d79-110">**구분 기호**</span><span class="sxs-lookup"><span data-stu-id="11d79-110">**Separator**</span></span>|<span data-ttu-id="11d79-111">개체 이름에서 단어를 구분하는 문자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="11d79-111">Specifies the character that separates words in an object name.</span></span> <span data-ttu-id="11d79-112">**값** 열에서 **밑줄**, **공백**또는 **없음**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="11d79-112">In the **Value** column, select **Underscore**, **Space**, or **None**.</span></span> <span data-ttu-id="11d79-113">기본값은 **밑줄**입니다.</span><span class="sxs-lookup"><span data-stu-id="11d79-113">The default is **Underscore**.</span></span>|  
|<span data-ttu-id="11d79-114">**기본 키 열 접두사**</span><span class="sxs-lookup"><span data-stu-id="11d79-114">**Primary key column prefix**</span></span>|<span data-ttu-id="11d79-115">각 기본 키 열의 이름 접두사로 사용할 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="11d79-115">Specifies the string to prefix the name of each primary key column.</span></span> <span data-ttu-id="11d79-116">기본값은 **PK**입니다.</span><span class="sxs-lookup"><span data-stu-id="11d79-116">The default is **PK**.</span></span>|  
|<span data-ttu-id="11d79-117">**외래 키 열 접두사**</span><span class="sxs-lookup"><span data-stu-id="11d79-117">**Foreign key column prefix**</span></span>|<span data-ttu-id="11d79-118">각 외래 키 열의 이름 접두사로 사용할 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="11d79-118">Specifies the string to prefix the name of each foreign key column.</span></span> <span data-ttu-id="11d79-119">기본값은 **FK**입니다.</span><span class="sxs-lookup"><span data-stu-id="11d79-119">The default is **FK**.</span></span>|  
|<span data-ttu-id="11d79-120">**특성 이름 접미사**</span><span class="sxs-lookup"><span data-stu-id="11d79-120">**Attribute name suffix**</span></span>|<span data-ttu-id="11d79-121">각 특성 열의 이름에 추가할 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="11d79-121">Specifies the string to be appended to the name of each attribute column.</span></span> <span data-ttu-id="11d79-122">기본값은 **Name**입니다.</span><span class="sxs-lookup"><span data-stu-id="11d79-122">The default is **Name**.</span></span>|  
|<span data-ttu-id="11d79-123">**사용자 지정 롤업 접미사**</span><span class="sxs-lookup"><span data-stu-id="11d79-123">**Custom rollup suffix**</span></span>|<span data-ttu-id="11d79-124">각 롤업 열의 이름에 추가할 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="11d79-124">Specifies the string to be appended to the name of each rollup column.</span></span> <span data-ttu-id="11d79-125">기본값은 **CustomRollup**입니다.</span><span class="sxs-lookup"><span data-stu-id="11d79-125">The default is **CustomRollup**.</span></span>|  
|<span data-ttu-id="11d79-126">**사용자 지정 롤업 속성 접미사**</span><span class="sxs-lookup"><span data-stu-id="11d79-126">**Custom rollup Properties suffix**</span></span>|<span data-ttu-id="11d79-127">각 롤업 속성 열의 이름에 추가할 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="11d79-127">Specifies the string to be appended to the name of each rollup property column.</span></span> <span data-ttu-id="11d79-128">기본값은 **CustomRollupProperties**입니다.</span><span class="sxs-lookup"><span data-stu-id="11d79-128">The default is **CustomRollupProperties**.</span></span>|  
|<span data-ttu-id="11d79-129">**단항 연산자 접미사**</span><span class="sxs-lookup"><span data-stu-id="11d79-129">**Unary operator suffix**</span></span>|<span data-ttu-id="11d79-130">각 단항 연산자 열의 이름에 추가할 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="11d79-130">Specifies the string to be appended to the name of each unary operator column.</span></span> <span data-ttu-id="11d79-131">기본값은 **UnaryOperator**입니다.</span><span class="sxs-lookup"><span data-stu-id="11d79-131">The default is **UnaryOperator**.</span></span>|  
  
 <span data-ttu-id="11d79-132">**값**</span><span class="sxs-lookup"><span data-stu-id="11d79-132">**Value**</span></span>  
 <span data-ttu-id="11d79-133">**옵션** 에서 스키마 생성 시 사용할 옵션 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="11d79-133">Specify a value for the option specified in **Option** that you want to use when the schema is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11d79-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="11d79-134">See Also</span></span>  
 <span data-ttu-id="11d79-135">[스키마 생성 마법사 F1 도움말 &#40;Analysis Services 다차원 데이터&#41;](schema-generation-wizard-f1-help-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="11d79-135">[Schema Generation Wizard F1 Help &#40;Analysis Services - Multidimensional Data&#41;](schema-generation-wizard-f1-help-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="11d79-136">다차원 데이터를 &#40;마법사 Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="11d79-136">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
