---
title: SQL 실행 태스크 편집기 (결과 집합 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.resultset.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: d27000c8-8d91-4e1c-b45e-bca9a3c12f6d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 027f3c77e84b47958e9fb6567acdb308c14eb1e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649119"
---
# <a name="execute-sql-task-editor-result-set-page"></a><span data-ttu-id="b022a-102">SQL 실행 태스크 편집기(결과 집합 페이지)</span><span class="sxs-lookup"><span data-stu-id="b022a-102">Execute SQL Task Editor (Result Set Page)</span></span>
  <span data-ttu-id="b022a-103">**SQL 실행 태스크 편집기** 대화 상자의 **결과 집합** 페이지를 사용하여 SQL 문의 결과를 새 변수 또는 기존 변수로 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b022a-103">Use the **Result Set** page of the **Execute SQL Task Editor** dialog to map the result of the SQL statement to new or existing variables.</span></span> <span data-ttu-id="b022a-104">일반 페이지의 **ResultSet** 을 **없음**으로 설정한 경우에는 이 대화 상자의 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b022a-104">The options in this dialog box are disabled if **ResultSet** on the General page is set to **None**.</span></span>  
  
 <span data-ttu-id="b022a-105">이 태스크에 대한 자세한 내용은 [SQL 실행 태스크](control-flow/execute-sql-task.md) 및 [SQL 실행 태스크의 결과 집합](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b022a-105">For more information about this task, see [Execute SQL Task](control-flow/execute-sql-task.md) and [Result Sets in the Execute SQL Task](../../2014/integration-services/result-sets-in-the-execute-sql-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="b022a-106">옵션</span><span class="sxs-lookup"><span data-stu-id="b022a-106">Options</span></span>  
 <span data-ttu-id="b022a-107">**결과 이름**</span><span class="sxs-lookup"><span data-stu-id="b022a-107">**Result Name**</span></span>  
 <span data-ttu-id="b022a-108">**추가**를 클릭하여 결과 집합 매핑 집합을 추가한 다음 결과를 설명하는 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b022a-108">After you have added a result set mapping set by clicking **Add**, provide a name for the result.</span></span> <span data-ttu-id="b022a-109">결과 집합 유형에 따라 특정 결과 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b022a-109">Depending on the result set type, you must use specific result names.</span></span>  
  
 <span data-ttu-id="b022a-110">결과 집합 유형이 **단일 행**이면 쿼리에서 반환한 열 이름이나 쿼리에서 반환한 열의 열 목록에서 열 위치를 나타내는 숫자 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b022a-110">If the result set type is **Single row**, you can use either the name of a column returned by the query or the number that represents the position of a column in the column list of a column returned by the query.</span></span>  
  
 <span data-ttu-id="b022a-111">결과 집합 유형이 **전체 결과 집합** 이나 **XML**이면 결과 집합 이름으로 0을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b022a-111">If the result set type is **Full result set** or **XML**, you must use 0 as the result set name.</span></span>  
  
 <span data-ttu-id="b022a-112">**관련 항목**: [SQL 실행 태스크의 결과 집합](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)</span><span class="sxs-lookup"><span data-stu-id="b022a-112">**Related Topics**: [Result Sets in the Execute SQL Task](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)</span></span>  
  
 <span data-ttu-id="b022a-113">**변수 이름**</span><span class="sxs-lookup"><span data-stu-id="b022a-113">**Variable Name**</span></span>  
 <span data-ttu-id="b022a-114">변수를 선택하여 결과 집합을 변수로 매핑하거나 \<**New variable...**>를 클릭하여 **변수 추가** 대화 상자를 사용하여 새 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b022a-114">Map the result set to a variable by selecting a variable or click \<**New variable...**> to add a new variable by using the **Add Variable** dialog box.</span></span>  
  
 <span data-ttu-id="b022a-115">**추가**</span><span class="sxs-lookup"><span data-stu-id="b022a-115">**Add**</span></span>  
 <span data-ttu-id="b022a-116">결과 집합 매핑을 추가하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b022a-116">Click to add a result set mapping.</span></span>  
  
 <span data-ttu-id="b022a-117">**제거**</span><span class="sxs-lookup"><span data-stu-id="b022a-117">**Remove**</span></span>  
 <span data-ttu-id="b022a-118">목록에서 결과 집합 매핑을 선택한 다음 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b022a-118">Select a result set mapping in the list and then click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b022a-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b022a-119">See Also</span></span>  
 <span data-ttu-id="b022a-120">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b022a-120">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="b022a-121">[SQL 실행 태스크 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="b022a-121">[Execute SQL Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="b022a-122">[SQL 실행 태스크 편집기 &#40;매개 변수 매핑 페이지&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md) </span><span class="sxs-lookup"><span data-stu-id="b022a-122">[Execute SQL Task Editor &#40;Parameter Mapping Page&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md) </span></span>  
 [<span data-ttu-id="b022a-123">Transact-SQL 참조 &#40;데이터베이스 엔진&#41;</span><span class="sxs-lookup"><span data-stu-id="b022a-123">Transact-SQL Reference &#40;Database Engine&#41;</span></span>](/sql/t-sql/language-reference)  
  
  
