---
title: 쿼리 매개 변수 대화 상자(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69645
- vdt.dlgbox.definequeryparameters
ms.assetid: 31cdaee2-d7cd-4d64-a45f-924b27e8b1f0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 76052876ad2899fc959aa7fc49f4299e08bac713
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730003"
---
# <a name="query-parameters-dialog-box-visual-database-tools"></a><span data-ttu-id="13c02-102">쿼리 매개 변수 대화 상자(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="13c02-102">Query Parameters Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="13c02-103">이 대화 상자를 사용하면 쿼리에 정의된 매개 변수에 사용할 값을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13c02-103">This dialog allows you to enter values for the parameters defined in the query.</span></span> <span data-ttu-id="13c02-104">이 대화 상자는 런타임에 최종 사용자가 입력해야 할 매개 변수가 포함된 쿼리를 실행할 때 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="13c02-104">This dialog box appears when you execute a query that contains parameters that require end-user input at run time.</span></span>  
  
## <a name="options"></a><span data-ttu-id="13c02-105">옵션</span><span class="sxs-lookup"><span data-stu-id="13c02-105">Options</span></span>  
 <span data-ttu-id="13c02-106">**이름**</span><span class="sxs-lookup"><span data-stu-id="13c02-106">**Name**</span></span>  
 <span data-ttu-id="13c02-107">실행할 쿼리에 대해 정의된 매개 변수를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="13c02-107">Lists the parameters defined for the query being executed.</span></span> <span data-ttu-id="13c02-108">쿼리에 명명된 매개 변수가 포함된 경우 목록에 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="13c02-108">If the query contains named parameters, the names appear in the list.</span></span> <span data-ttu-id="13c02-109">쿼리에 명명되지 않은 매개 변수가 포함된 경우 쿼리의 각 매개 변수에 대해 자동으로 지정된 매개 변수 이름이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="13c02-109">If the query contains unnamed parameters, system-defined parameter names are listed for each parameter in the query.</span></span>  
  
 <span data-ttu-id="13c02-110">**값**</span><span class="sxs-lookup"><span data-stu-id="13c02-110">**Value**</span></span>  
 <span data-ttu-id="13c02-111">**이름**아래에 나열된 각 매개 변수에 대한 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="13c02-111">Enter the value for each parameter listed under **Name**.</span></span> <span data-ttu-id="13c02-112">가장 최근에 사용한 값이 기본 매개 변수 값으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="13c02-112">The value used most recently appears as the default parameter value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13c02-113">예제</span><span class="sxs-lookup"><span data-stu-id="13c02-113">Example</span></span>  
 <span data-ttu-id="13c02-114">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스에서 SQL 창의 다음 쿼리를 실행하면 쿼리 매개 변수 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="13c02-114">The following query in the SQL Pane, opens the Query Parameters dialog box when executed in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
```  
SELECT   FirstName, LastName  
FROM    Person.Person AS Lastname  
WHERE   (LastName = @Param1);  
```  
  
## <a name="see-also"></a><span data-ttu-id="13c02-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="13c02-115">See Also</span></span>  
 [<span data-ttu-id="13c02-116">매개 변수를 사용하여 쿼리&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="13c02-116">Query with Parameters &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
