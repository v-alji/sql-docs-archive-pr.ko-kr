---
title: 웹 서비스 태스크 편집기 (입력 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.input.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 93529c88-f540-47f2-a10a-12c87318ed6f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0ae876572747b9bb1088fe8b0a1c2c2fdde9f4f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660033"
---
# <a name="web-service-task-editor-input-page"></a><span data-ttu-id="40c79-102">웹 서비스 태스크 편집기(입력 페이지)</span><span class="sxs-lookup"><span data-stu-id="40c79-102">Web Service Task Editor (Input Page)</span></span>
  <span data-ttu-id="40c79-103">**웹 서비스 태스크 편집기** 대화 상자의 **입력** 페이지를 사용하여 웹 서비스, 웹 메서드 및 웹 메서드에 입력으로 제공할 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40c79-103">Use the **Input** page of the **Web Service Task Editor** dialog box to specify the Web Service, the Web method, and the values to provide to the Web method as input.</span></span> <span data-ttu-id="40c79-104">문자열을 값 열에 직접 입력하거나 값 열에서 변수를 선택하여 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40c79-104">The values can be provided either by typing strings directly in the Value column, or by selecting variables in the Value column.</span></span>  
  
 <span data-ttu-id="40c79-105">이 태스크에 대한 자세한 내용은 [웹 서비스 태스크](control-flow/web-service-task.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="40c79-105">To learn about this task, see [Web Service Task](control-flow/web-service-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="40c79-106">옵션</span><span class="sxs-lookup"><span data-stu-id="40c79-106">Options</span></span>  
 <span data-ttu-id="40c79-107">**서비스**</span><span class="sxs-lookup"><span data-stu-id="40c79-107">**Service**</span></span>  
 <span data-ttu-id="40c79-108">목록에서 웹 메서드를 실행하는 데 사용할 웹 서비스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="40c79-108">Select a Web service from the list to use to execute the Web method.</span></span>  
  
 <span data-ttu-id="40c79-109">**메서드**</span><span class="sxs-lookup"><span data-stu-id="40c79-109">**Method**</span></span>  
 <span data-ttu-id="40c79-110">목록에서 실행할 태스크에 사용할 웹 메서드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="40c79-110">Select a Web method from the list for the task to execute.</span></span>  
  
 <span data-ttu-id="40c79-111">**WebMethodDocumentation**</span><span class="sxs-lookup"><span data-stu-id="40c79-111">**WebMethodDocumentation**</span></span>  
 <span data-ttu-id="40c79-112">웹 방식에 대한 설명을 입력하거나 찾아보기 단추 **(...)** 를 클릭하여 **웹 메서드 설명서** 대화 상자에 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="40c79-112">Type a description of Web method, or the click the browse button **(...)** and then type the description in the **Web Method Documentation** dialog box.</span></span>  
  
 <span data-ttu-id="40c79-113">**이름**</span><span class="sxs-lookup"><span data-stu-id="40c79-113">**Name**</span></span>  
 <span data-ttu-id="40c79-114">웹 메서드에 대한 입력의 이름을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="40c79-114">Lists the names of the inputs to the Web method.</span></span>  
  
 <span data-ttu-id="40c79-115">**형식**</span><span class="sxs-lookup"><span data-stu-id="40c79-115">**Type**</span></span>  
 <span data-ttu-id="40c79-116">입력의 데이터 형식을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="40c79-116">Lists the data type of the inputs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="40c79-117">웹 서비스 태스크는 정수 및 문자열과 같은 기본 형식, 기본 형식의 배열 및 시퀀스, 열거 등과 같은 데이터 형식의 매개 변수만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="40c79-117">The Web Service task supports parameters of the following data types only: primitive types such as integers and strings; arrays and sequences of primitive types; and enumerations.</span></span>  
  
 <span data-ttu-id="40c79-118">**변수**</span><span class="sxs-lookup"><span data-stu-id="40c79-118">**Variable**</span></span>  
 <span data-ttu-id="40c79-119">확인란을 선택하여 입력을 제공하기 위한 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="40c79-119">Select the check boxes to use variables to provide inputs.</span></span>  
  
 <span data-ttu-id="40c79-120">**값**</span><span class="sxs-lookup"><span data-stu-id="40c79-120">**Value**</span></span>  
 <span data-ttu-id="40c79-121">Variable 확인란이 선택된 경우 목록에서 변수를 선택하여 입력을 제공하고 선택되지 않은 경우 입력에 사용할 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="40c79-121">If the Variable check-boxes are selected, select the variables in the list to provide the inputs; otherwise, type the values to use in the inputs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c79-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="40c79-122">See Also</span></span>  
 <span data-ttu-id="40c79-123">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="40c79-123">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="40c79-124">[웹 서비스 태스크 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="40c79-124">[Web Service Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="40c79-125">[웹 서비스 태스크 편집기 &#40;출력 페이지&#41;](../../2014/integration-services/web-service-task-editor-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="40c79-125">[Web Service Task Editor &#40;Output Page&#41;](../../2014/integration-services/web-service-task-editor-output-page.md) </span></span>  
 [<span data-ttu-id="40c79-126">식 페이지</span><span class="sxs-lookup"><span data-stu-id="40c79-126">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
