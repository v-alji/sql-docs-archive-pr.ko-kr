---
title: 인덱스 다시 구성 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.reorganizeindextask.f1
helpviewer_keywords:
- reorganizing indexes
- Reorganize Index task [Integration Services]
- indexes [Integration Services]
ms.assetid: 9ed87861-e5c3-4fcd-8760-d112f4c0af0c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3f910391bd3a5a35770bb677bc17c91a00ace457
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652254"
---
# <a name="reorganize-index-task"></a><span data-ttu-id="f39a6-102">인덱스 다시 구성 태스크</span><span class="sxs-lookup"><span data-stu-id="f39a6-102">Reorganize Index Task</span></span>
  <span data-ttu-id="f39a6-103">인덱스 다시 구성 태스크는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 테이블과 뷰의 인덱스를 다시 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f39a6-103">The Reorganize Index task reorganizes indexes in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database tables and views.</span></span> <span data-ttu-id="f39a6-104">인덱스 관리에 대한 자세한 내용은 [인덱스 다시 구성 및 다시 작성](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f39a6-104">For more information about managing indexes, see [Reorganize and Rebuild Indexes](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).</span></span>  
  
 <span data-ttu-id="f39a6-105">인덱스 다시 구성 태스크를 사용하면 패키지가 단일 데이터베이스나 여러 데이터베이스의 인덱스를 다시 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f39a6-105">By using the Reorganize Index task, a package can reorganize indexes in a single database or multiple databases.</span></span> <span data-ttu-id="f39a6-106">태스크가 단일 데이터베이스의 인덱스만 다시 구성하는 경우 인덱스를 다시 구성할 뷰와 테이블을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f39a6-106">If the task reorganizes only the indexes in a single database, you can choose the views or the tables whose indexes the task reorganizes.</span></span> <span data-ttu-id="f39a6-107">인덱스 다시 구성 태스크에는 큰 개체 데이터를 압축하는 옵션도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f39a6-107">The Reorganize Index task also includes an option to compact large object data.</span></span> <span data-ttu-id="f39a6-108">큰 개체 데이터는 `image`, `text`, `ntext`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)` 또는 `xml` 데이터 형식의 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="f39a6-108">Large object data is data with the `image`, `text`, `ntext`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, or `xml` data type.</span></span> <span data-ttu-id="f39a6-109">자세한 내용은 [데이터 형식&#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f39a6-109">For more information, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
 <span data-ttu-id="f39a6-110">인덱스 다시 구성 태스크는 Transact-SQL ALTER INDEX 문을 캡슐화합니다.</span><span class="sxs-lookup"><span data-stu-id="f39a6-110">The Reorganize Index task encapsulates the Transact-SQL ALTER INDEX statement.</span></span> <span data-ttu-id="f39a6-111">큰 개체 데이터를 압축하도록 선택하면 이 문은 REORGANIZE WITH (LOB_COMPACTION = ON) 절을 사용하고 그렇지 않으면 LOB_COMPACTION이 OFF로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f39a6-111">If you choose to compact large object data, the statement uses the REORGANIZE WITH (LOB_COMPACTION = ON) clause, otherwise LOB_COMPACTION is set to OFF.</span></span> <span data-ttu-id="f39a6-112">자세한 내용은 [ALTER INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f39a6-112">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f39a6-113">태스크에서 실행할 Transact-SQL 문을 만드는 데 걸리는 시간은 태스크에서 다시 구성하는 인덱스 수에 비례합니다.</span><span class="sxs-lookup"><span data-stu-id="f39a6-113">The time the task takes to create the Transact-SQL statement that the task runs is proportionate to the number of indexes the task reorganizes.</span></span> <span data-ttu-id="f39a6-114">많은 수의 인덱스가 있는 데이터베이스의 모든 테이블과 뷰의 인덱스를 다시 구성하거나 여러 데이터베이스의 인덱스를 다시 구성하도록 태스크를 구성하면 Transact-SQL 문을 생성하는 데 시간이 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f39a6-114">If the task is configured to reorganize indexes in all the tables and views in a database that holds a large number of indexes, or to reorganize indexes in multiple databases, the task can take a considerable amount of time to generate the Transact-SQL statement.</span></span>  
  
## <a name="configuration-of-the-reorganize-index-task"></a><span data-ttu-id="f39a6-115">인덱스 다시 구성 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="f39a6-115">Configuration of the Reorganize Index Task</span></span>  
 <span data-ttu-id="f39a6-116">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f39a6-116">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="f39a6-117">이 태스크는 **디자이너의** 도구 상자 **에 있는** 유지 관리 계획 태스크 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 섹션에서 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f39a6-117">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="f39a6-118">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="f39a6-118">For information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="f39a6-119">인덱스 다시 구성 태스크&#40;유지 관리 계획&#41;</span><span class="sxs-lookup"><span data-stu-id="f39a6-119">Reorganize Index Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/reorganize-index-task-maintenance-plan.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="f39a6-120">관련 작업</span><span class="sxs-lookup"><span data-stu-id="f39a6-120">Related Tasks</span></span>  
 <span data-ttu-id="f39a6-121">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법에 대한 자세한 내용은 [태스크 또는 컨테이너의 속성 설정](../set-the-properties-of-a-task-or-container.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f39a6-121">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f39a6-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f39a6-122">See Also</span></span>  
 <span data-ttu-id="f39a6-123">[Integration Services 태스크](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="f39a6-123">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="f39a6-124">제어 흐름</span><span class="sxs-lookup"><span data-stu-id="f39a6-124">Control Flow</span></span>](control-flow.md)  
  
  
