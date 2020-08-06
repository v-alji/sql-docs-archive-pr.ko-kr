---
title: 식 페이지 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.expressionspage.f1
helpviewer_keywords:
- Expressions Page dialog box
ms.assetid: c9016ec6-11c1-4ebd-b2a7-0fa6631fd9e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ba4e73ea495456e8f9e452108ab09106a65543ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650212"
---
# <a name="expressions-page"></a><span data-ttu-id="e0d7f-102">식 페이지</span><span class="sxs-lookup"><span data-stu-id="e0d7f-102">Expressions Page</span></span>
  <span data-ttu-id="e0d7f-103">**식** 페이지를 사용하여 속성 식을 편집하고 **속성 식 편집기** 및 **식 작성기** 대화 상자에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0d7f-103">Use the **Expressions** page to edit property expressions and to access the **Property Expressions Editor** and **Property Expression Builder** dialog boxes.</span></span>  
  
 <span data-ttu-id="e0d7f-104">속성 식은 패키지 실행 시 속성 값을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d7f-104">Property expressions update the values of properties when the package is run.</span></span> <span data-ttu-id="e0d7f-105">패키지, 태스크, 컨테이너, 연결 관리자 및 일부 데이터 흐름 구성 요소의 속성에 속성 식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0d7f-105">Property expressions can be used with the properties of packages, tasks, containers, connection managers, as well as some data flow components.</span></span> <span data-ttu-id="e0d7f-106">식이 평가되고 그 결과가 패키지 및 패키지 개체를 구성할 때 설정한 속성 값 대신 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0d7f-106">The expressions are evaluated and their results are used instead of the values to which you set the properties when you configured the package and package objects.</span></span> <span data-ttu-id="e0d7f-107">식에는 식 언어가 제공하는 함수 및 연산자와 변수가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0d7f-107">The expressions can include variables and the functions and operators that the expression language provides.</span></span> <span data-ttu-id="e0d7f-108">예를 들어 "Weather forecast for " 문자열이 포함된 변수 값과 GETDATE() 함수의 반환 결과를 연결하여 "Weather forecast for 4/5/2006" 문자열을 만들면 메일 보내기 태스크의 제목 줄을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0d7f-108">For example, you can generate the subject line for the Send Mail task by concatenating the value of a variable that contains the string "Weather forecast for " and the return results of the GETDATE() function to make the string "Weather forecast for 4/5/2006".</span></span>  
  
 <span data-ttu-id="e0d7f-109">식을 작성하고 속성 식을 사용하는 방법은 [Integration Services&#40;SSIS&#41; 식](integration-services-ssis-expressions.md) 및 [패키지에서 속성 식 사용](use-property-expressions-in-packages.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0d7f-109">To learn more about writing expressions and using property expressions, see [Integration Services &#40;SSIS&#41; Expressions](integration-services-ssis-expressions.md) and [Use Property Expressions in Packages](use-property-expressions-in-packages.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e0d7f-110">옵션</span><span class="sxs-lookup"><span data-stu-id="e0d7f-110">Options</span></span>  
 <span data-ttu-id="e0d7f-111">**식(...)**</span><span class="sxs-lookup"><span data-stu-id="e0d7f-111">**Expressions (...)**</span></span>  
 <span data-ttu-id="e0d7f-112">**속성 식 편집기** 대화 상자를 열려면 줄임표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d7f-112">Click the ellipsis to open the **Property Expressions Editor** dialog box.</span></span> <span data-ttu-id="e0d7f-113">자세한 내용은 [Property Expressions Editor](property-expressions-editor.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0d7f-113">For more information, see [Property Expressions Editor](property-expressions-editor.md).</span></span>  
  
 **\<property name>**  
 <span data-ttu-id="e0d7f-114">**식 작성기** 대화 상자를 열려면 줄임표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d7f-114">Click the ellipsis to open the **Expression Builder** dialog box.</span></span> <span data-ttu-id="e0d7f-115">자세한 내용은 [Expression Builder](expression-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0d7f-115">For more information, see [Expression Builder](expression-builder.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0d7f-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e0d7f-116">See Also</span></span>  
 <span data-ttu-id="e0d7f-117">[Integration Services&#40;SSIS&#41; 변수](../integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="e0d7f-117">[Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="e0d7f-118">[시스템 변수](../system-variables.md) </span><span class="sxs-lookup"><span data-stu-id="e0d7f-118">[System Variables](../system-variables.md) </span></span>  
 [<span data-ttu-id="e0d7f-119">Integration Services&#40;SSIS&#41; 식</span><span class="sxs-lookup"><span data-stu-id="e0d7f-119">Integration Services &#40;SSIS&#41; Expressions</span></span>](integration-services-ssis-expressions.md)  
  
  
