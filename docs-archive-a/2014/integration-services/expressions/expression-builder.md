---
title: 식 작성기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.expressionbuilder.f1
helpviewer_keywords:
- Expression Builder dialog box
ms.assetid: 4717ce33-bd4e-44bc-81e0-002de075b4d1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 812b0d744d415d5419d54176359ddcd5837dd206
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650211"
---
# <a name="expression-builder"></a><span data-ttu-id="b5fa2-102">식 작성기</span><span class="sxs-lookup"><span data-stu-id="b5fa2-102">Expression Builder</span></span>
  <span data-ttu-id="b5fa2-103">**식 작성기** 대화 상자를 사용하여 변수를 나열하고 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 식 언어에 포함된 함수, 유형 변환 및 연산자에 대한 참조를 기본적으로 제공하는 그래픽 사용자 인터페이스로 변수 값을 설정하는 식을 작성하거나 속성 식을 생성 및 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa2-103">Use the **Expression Builder** dialog box to create and edit a property expression or write the expression that sets the value of a variable using a graphical user interface that lists variables and provides a built-in reference to the functions, type casts, and operators that the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expression language includes.</span></span>  
  
 <span data-ttu-id="b5fa2-104">속성 식은 속성에 할당된 식입니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa2-104">A property expression is an expression that is assigned to a property.</span></span> <span data-ttu-id="b5fa2-105">식을 평가하면 속성이 식의 평가 결과를 사용하도록 동적으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa2-105">When the expression is evaluated, the property is dynamically updated to use the evaluation result of the expression.</span></span> <span data-ttu-id="b5fa2-106">마찬가지로 변수에 사용된 식을 통해 식의 평가 결과로 변수 값을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa2-106">Likewise, an expression that is used in a variable enables the variable value to be updated with the evaluation result of the expression.</span></span>  
  
 <span data-ttu-id="b5fa2-107">여러 가지 방법으로 식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa2-107">There are many ways to use expressions:</span></span>  
  
-   <span data-ttu-id="b5fa2-108">**태스크** 변수에 저장된 메일 주소를 삽입하여 메일 보내기 태스크에 사용되는 받는 사람 줄을 업데이트하거나 "Sales for:" 등의 문자열과 GETDATE 함수에서 반환된 현재 날짜를 연결하여 제목 줄을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa2-108">**Tasks** Update the To line that a Send Mail task uses by inserting an e-mail address that is stored in a variable; or update the Subject line by concatenating a string such as "Sales for: " and the current date returned by the GETDATE function.</span></span>  
  
-   <span data-ttu-id="b5fa2-109">**변수**`DATEPART("mm",GETDATE())`와 같은 식을 사용하여 변수 값을 현재 월로 설정하거나 `"Today's date is " + (DT_WSTR,30)(GETDATE())` 식을 사용하여 문자열 리터럴과 현재 날짜를 연결하여 문자열 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa2-109">**Variables** Set the value of a variable to the current month by using an expression like `DATEPART("mm",GETDATE())`; or set the value of a string by concatenating the string literal and the current date by using the expression `"Today's date is " + (DT_WSTR,30)(GETDATE())`.</span></span>  
  
-   <span data-ttu-id="b5fa2-110">**연결 관리자** 다른 코드 페이지 식별자가 포함된 변수를 사용하여 플랫 파일 연결 관리자의 코드 페이지를 설정하거나 식에 3과 같은 양의 정수를 입력하여 데이터 파일의 행 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa2-110">**Connection Managers** Set the code page of a Flat File connection manager by using a variable that contains a different code page identifier; or specify the number of rows in the data file to skip by entering a positive integer like 3 in the expression.</span></span>  
  
 <span data-ttu-id="b5fa2-111">속성 식에 대한 자세한 내용과 식을 작성하는 방법에 대한 자세한 내용은 [패키지에서 속성 식 사용](use-property-expressions-in-packages.md) 및 [Integration Services&#40;SSIS&#41; 식](integration-services-ssis-expressions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5fa2-111">To learn more about property expressions and writing expressions, see [Use Property Expressions in Packages](use-property-expressions-in-packages.md) and [Integration Services &#40;SSIS&#41; Expressions](integration-services-ssis-expressions.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="b5fa2-112">옵션</span><span class="sxs-lookup"><span data-stu-id="b5fa2-112">Options</span></span>  
  
|<span data-ttu-id="b5fa2-113">용어</span><span class="sxs-lookup"><span data-stu-id="b5fa2-113">Term</span></span>|<span data-ttu-id="b5fa2-114">정의</span><span class="sxs-lookup"><span data-stu-id="b5fa2-114">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="b5fa2-115">**변수**</span><span class="sxs-lookup"><span data-stu-id="b5fa2-115">**Variables**</span></span>|<span data-ttu-id="b5fa2-116">**변수** 폴더를 확장한 다음 변수를 **식** 상자로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa2-116">Expand the **Variables** folder and drag variables to the **Expression** box.</span></span>|  
|<span data-ttu-id="b5fa2-117">**수치 연산 함수**</span><span class="sxs-lookup"><span data-stu-id="b5fa2-117">**Mathematical Functions**</span></span><br /><br /> <span data-ttu-id="b5fa2-118">**문자열 함수**</span><span class="sxs-lookup"><span data-stu-id="b5fa2-118">**String Functions**</span></span><br /><br /> <span data-ttu-id="b5fa2-119">**날짜/시간 함수**</span><span class="sxs-lookup"><span data-stu-id="b5fa2-119">**Date/Time Functions**</span></span><br /><br /> <span data-ttu-id="b5fa2-120">**NULL 함수**</span><span class="sxs-lookup"><span data-stu-id="b5fa2-120">**NULL Functions**</span></span><br /><br /> <span data-ttu-id="b5fa2-121">**유형 변환**</span><span class="sxs-lookup"><span data-stu-id="b5fa2-121">**Type Casts**</span></span><br /><br /> <span data-ttu-id="b5fa2-122">**연산자**</span><span class="sxs-lookup"><span data-stu-id="b5fa2-122">**Operators**</span></span>|<span data-ttu-id="b5fa2-123">폴더를 확장한 다음 함수, 유형 변환 및 연산자를 **식** 상자로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa2-123">Expand the folders and drag functions, type casts, and operators to the **Expression** box.</span></span>|  
|<span data-ttu-id="b5fa2-124">**식**</span><span class="sxs-lookup"><span data-stu-id="b5fa2-124">**Expression**</span></span>|<span data-ttu-id="b5fa2-125">식을 편집하거나 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa2-125">Edit or type an expression.\`</span></span>|  
|<span data-ttu-id="b5fa2-126">**평가 값**</span><span class="sxs-lookup"><span data-stu-id="b5fa2-126">**Evaluated value**</span></span>|<span data-ttu-id="b5fa2-127">식의 평가 결과를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa2-127">Lists the evaluation result of the expression.</span></span>|  
|<span data-ttu-id="b5fa2-128">**식 계산**</span><span class="sxs-lookup"><span data-stu-id="b5fa2-128">**Evaluate Expression**</span></span>|<span data-ttu-id="b5fa2-129">식의 계산 결과를 보려면 **식 계산** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa2-129">Click **Evaluate Expression** to view the evaluation result of the expression.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b5fa2-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b5fa2-130">See Also</span></span>  
 <span data-ttu-id="b5fa2-131">[식 페이지](expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="b5fa2-131">[Expressions Page](expressions-page.md) </span></span>  
 <span data-ttu-id="b5fa2-132">[속성 식 편집기](property-expressions-editor.md) </span><span class="sxs-lookup"><span data-stu-id="b5fa2-132">[Property Expressions Editor](property-expressions-editor.md) </span></span>  
 <span data-ttu-id="b5fa2-133">[Integration Services&#40;SSIS&#41; 변수](../integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="b5fa2-133">[Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) </span></span>  
 [<span data-ttu-id="b5fa2-134">시스템 변수</span><span class="sxs-lookup"><span data-stu-id="b5fa2-134">System Variables</span></span>](../system-variables.md)  
  
  
