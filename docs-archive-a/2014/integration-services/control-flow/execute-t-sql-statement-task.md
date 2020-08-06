---
title: T-SQL 문 실행 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executetsqlstatementtask.f1
helpviewer_keywords:
- Transact-SQL statements, SSIS
- statements [Integration Services]
- Execute T-SQL Statement task [Integration Services]
ms.assetid: 7e9086ca-d27e-46c0-bfad-d61333ebd55e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7ebc73ad843ac7fcf1dfbe7699ecd8ea53edcdad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729704"
---
# <a name="execute-t-sql-statement-task"></a><span data-ttu-id="7147c-102">T-SQL 문 실행 태스크</span><span class="sxs-lookup"><span data-stu-id="7147c-102">Execute T-SQL Statement Task</span></span>
  <span data-ttu-id="7147c-103">T-SQL 문 실행 태스크는 Transact-SQL 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7147c-103">The Execute T-SQL Statement task runs Transact-SQL statements.</span></span> <span data-ttu-id="7147c-104">자세한 내용은 [Transact-SQL 참조&#40;데이터베이스 엔진&#41;](/sql/t-sql/language-reference) 및 [Integration Services&#40;SSIS&#41; 쿼리](../integration-services-ssis-queries.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7147c-104">For more information, see [Transact-SQL Reference &#40;Database Engine&#41;](/sql/t-sql/language-reference) and [Integration Services &#40;SSIS&#41; Queries](../integration-services-ssis-queries.md).</span></span>  
  
 <span data-ttu-id="7147c-105">이 태스크는 SQL 실행 태스크와 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="7147c-105">This task is similar to the Execute SQL task.</span></span> <span data-ttu-id="7147c-106">그러나 T-SQL 문 실행 태스크는 SQL 언어의 Transact-SQL 버전만 지원하며 이 태스크를 사용하여 SQL 언어의 다른 언어를 사용하는 문을 서버에서 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7147c-106">However, the Execute T-SQL Statement task supports only the Transact-SQL version of the SQL language and you cannot use this task to run statements on servers that use other dialects of the SQL language.</span></span> <span data-ttu-id="7147c-107">매개 변수가 있는 쿼리를 실행하거나 쿼리 결과를 변수에 저장하거나 속성 식을 사용해야 하는 경우 T-SQL 문 실행 태스크 대신 SQL 실행 태스크를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7147c-107">If you need to run parameterized queries, save the query results to variables, or use property expressions, you should use the Execute SQL task instead of the Execute T-SQL Statement task.</span></span> <span data-ttu-id="7147c-108">자세한 내용은 [Execute SQL Task](execute-sql-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7147c-108">For more information, see [Execute SQL Task](execute-sql-task.md).</span></span>  
  
## <a name="configuration-of-the-execute-t-sql-task"></a><span data-ttu-id="7147c-109">T-SQL 실행 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="7147c-109">Configuration of the Execute T-SQL Task</span></span>  
 <span data-ttu-id="7147c-110">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7147c-110">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="7147c-111">이 태스크는 **디자이너의** 도구 상자 **에 있는** 유지 관리 계획 태스크 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 섹션에서 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7147c-111">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="7147c-112">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="7147c-112">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="7147c-113">T-SQL 문 실행 태스크&#40;유지 관리 계획&#41;</span><span class="sxs-lookup"><span data-stu-id="7147c-113">Execute T-SQL Statement Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/execute-t-sql-statement-task-maintenance-plan.md)  
  
 <span data-ttu-id="7147c-114">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="7147c-114">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="7147c-115">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="7147c-115">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="7147c-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7147c-116">See Also</span></span>  
 <span data-ttu-id="7147c-117">[Integration Services 태스크](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="7147c-117">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 <span data-ttu-id="7147c-118">[제어 흐름](control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="7147c-118">[Control Flow](control-flow.md) </span></span>  
 [<span data-ttu-id="7147c-119">Integration Services 패키지의 MERGE</span><span class="sxs-lookup"><span data-stu-id="7147c-119">MERGE in Integration Services Packages</span></span>](merge-in-integration-services-packages.md)  
  
  
