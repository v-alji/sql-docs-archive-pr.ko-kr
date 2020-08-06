---
title: SQL 실행 태스크 편집기 (매개 변수 매핑 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.parametermapping.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: 8ebe020a-7921-46b2-8823-398748f379b2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cfbb4468cb69947dfa54fb519b7698286393d578
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649120"
---
# <a name="execute-sql-task-editor-parameter-mapping-page"></a><span data-ttu-id="3ee91-102">SQL 실행 태스크 편집기(매개 변수 매핑 페이지)</span><span class="sxs-lookup"><span data-stu-id="3ee91-102">Execute SQL Task Editor (Parameter Mapping Page)</span></span>
  <span data-ttu-id="3ee91-103">**SQL 실행 태스크 편집기** 대화 상자의 **매개 변수 매핑** 페이지를 사용하여 변수를 SQL 문의 매개 변수에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ee91-103">Use the **Parameter Mapping** page of the **Execute SQL Task Editor** dialog box to map variables to parameters in the SQL statement.</span></span>  
  
 <span data-ttu-id="3ee91-104">이 태스크에 대해 알아보려면 [SQL 실행 태스크](control-flow/execute-sql-task.md) 및 [SQL 실행 태스크의 매개 변수 및 반환 코드](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3ee91-104">To learn about this task, see [Execute SQL Task](control-flow/execute-sql-task.md) and [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="3ee91-105">옵션</span><span class="sxs-lookup"><span data-stu-id="3ee91-105">Options</span></span>  
 <span data-ttu-id="3ee91-106">**변수 이름**</span><span class="sxs-lookup"><span data-stu-id="3ee91-106">**Variable Name**</span></span>  
 <span data-ttu-id="3ee91-107">**추가**를 클릭하여 매개 변수 매핑을 추가했으면 **변수 추가** 대화 상자를 사용하여 목록에서 시스템 또는 사용자 정의 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3ee91-107">After you have added a parameter mapping by clicking **Add**, select a system or user-defined variable from the list or click \<**New variable...**> to add a new variable by using the **Add Variable** dialog box.</span></span>  
  
 <span data-ttu-id="3ee91-108">**관련 항목:** [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md)</span><span class="sxs-lookup"><span data-stu-id="3ee91-108">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md)</span></span>  
  
 <span data-ttu-id="3ee91-109">**Direction**</span><span class="sxs-lookup"><span data-stu-id="3ee91-109">**Direction**</span></span>  
 <span data-ttu-id="3ee91-110">매개 변수의 방향을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3ee91-110">Select the direction of the parameter.</span></span> <span data-ttu-id="3ee91-111">각 변수를 입력 매개 변수, 출력 매개 변수 또는 반환 코드에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="3ee91-111">Map each variable to an input parameter, output parameter, or a return code.</span></span>  
  
 <span data-ttu-id="3ee91-112">**데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="3ee91-112">**Data Type**</span></span>  
 <span data-ttu-id="3ee91-113">매개 변수의 데이터 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3ee91-113">Select the data type of the parameter.</span></span> <span data-ttu-id="3ee91-114">사용 가능한 데이터 형식의 목록은 태스크에서 사용하는 연결 관리자에서 선택한 공급자에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ee91-114">The list of available data types is specific to the provider selected in the connection manager used by the task.</span></span>  
  
 <span data-ttu-id="3ee91-115">**매개 변수 이름**</span><span class="sxs-lookup"><span data-stu-id="3ee91-115">**Parameter Name**</span></span>  
 <span data-ttu-id="3ee91-116">매개 변수 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3ee91-116">Provide a parameter name.</span></span>  
  
 <span data-ttu-id="3ee91-117">태스크에서 사용하는 연결 관리자 유형에 따라 숫자 또는 매개 변수 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ee91-117">Depending on the connection manager type that the task uses, you must use numbers or parameter names.</span></span> <span data-ttu-id="3ee91-118">일부 연결 관리자 유형의 경우 매개 변수 이름의 첫 문자가 \@ 기호여야 하거나, 이름이 \@Param1과 같은 특정 이름이어야 하거나, 열 이름을 매개 변수 이름으로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ee91-118">Some connection manager types require that the first character of the parameter name is the \@ sign , specific names like \@Param1, or column names as parameter names.</span></span>  
  
 <span data-ttu-id="3ee91-119">**관련 항목:** [SQL 실행 태스크의 매개 변수 및 반환 코드](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)</span><span class="sxs-lookup"><span data-stu-id="3ee91-119">**Related Topics:** [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)</span></span>  
  
 <span data-ttu-id="3ee91-120">**매개 변수 크기**</span><span class="sxs-lookup"><span data-stu-id="3ee91-120">**Parameter Size**</span></span>  
 <span data-ttu-id="3ee91-121">문자열 및 이진 필드와 같은 가변 길이를 가지는 매개 변수의 크기를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3ee91-121">Provide the size of parameters that have variable length, such as strings and binary fields.</span></span>  
  
 <span data-ttu-id="3ee91-122">이 설정을 사용하면 공급자에서 가변 길이 매개 변수 값에 대해 충분한 공간을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="3ee91-122">This setting ensures that the provider allocates sufficient space for variable-length parameter values.</span></span>  
  
 <span data-ttu-id="3ee91-123">**추가**</span><span class="sxs-lookup"><span data-stu-id="3ee91-123">**Add**</span></span>  
 <span data-ttu-id="3ee91-124">매개 변수 매핑을 추가하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3ee91-124">Click to add a parameter mapping.</span></span>  
  
 <span data-ttu-id="3ee91-125">**제거**</span><span class="sxs-lookup"><span data-stu-id="3ee91-125">**Remove**</span></span>  
 <span data-ttu-id="3ee91-126">목록에서 매개 변수 매핑을 선택한 다음 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3ee91-126">Select a parameter mapping in the list and then click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ee91-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3ee91-127">See Also</span></span>  
 <span data-ttu-id="3ee91-128">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="3ee91-128">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="3ee91-129">[SQL 실행 태스크 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="3ee91-129">[Execute SQL Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="3ee91-130">[SQL 실행 태스크 편집기 &#40;결과 집합 페이지&#41;](../../2014/integration-services/execute-sql-task-editor-result-set-page.md) </span><span class="sxs-lookup"><span data-stu-id="3ee91-130">[Execute SQL Task Editor &#40;Result Set Page&#41;](../../2014/integration-services/execute-sql-task-editor-result-set-page.md) </span></span>  
 [<span data-ttu-id="3ee91-131">Transact-SQL 참조 &#40;데이터베이스 엔진&#41;</span><span class="sxs-lookup"><span data-stu-id="3ee91-131">Transact-SQL Reference &#40;Database Engine&#41;</span></span>](/sql/t-sql/language-reference)  
  
  
