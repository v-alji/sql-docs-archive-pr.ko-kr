---
title: 인덱스 다시 작성 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rebuildindextask.f1
helpviewer_keywords:
- rebuilding indexes
- indexes [Integration Services]
- Rebuild Index task
ms.assetid: 021884dd-e72d-47b2-99e8-b741410509c3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 33bbe25bc8c47f4f749f95dbb7096c3a76c25297
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652256"
---
# <a name="rebuild-index-task"></a><span data-ttu-id="24d69-102">인덱스 다시 작성 태스크</span><span class="sxs-lookup"><span data-stu-id="24d69-102">Rebuild Index Task</span></span>
  <span data-ttu-id="24d69-103">인덱스 다시 작성 태스크는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 테이블과 뷰의 인덱스를 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="24d69-103">The Rebuild Index task rebuilds indexes in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database tables and views.</span></span> <span data-ttu-id="24d69-104">인덱스 관리에 대한 자세한 내용은 [인덱스 다시 구성 및 다시 작성](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24d69-104">For more information about managing indexes, see [Reorganize and Rebuild Indexes](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).</span></span>  
  
 <span data-ttu-id="24d69-105">인덱스 다시 작성 태스크를 사용하면 패키지가 단일 데이터베이스나 여러 데이터베이스의 인덱스를 다시 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d69-105">By using the Rebuild Index task, a package can rebuild indexes in a single database or multiple databases.</span></span> <span data-ttu-id="24d69-106">태스크가 단일 데이터베이스의 인덱스만 다시 작성하는 경우 인덱스를 다시 작성할 뷰와 테이블을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d69-106">If the task rebuilds only the indexes in a single database, you can choose the views and tables whose indexes the task rebuilds.</span></span>  
  
 <span data-ttu-id="24d69-107">이 태스크는 ALTER INDEX REBUILD 문을 다음 인덱스 다시 작성 옵션과 함께 캡슐화합니다.</span><span class="sxs-lookup"><span data-stu-id="24d69-107">This task encapsulates an ALTER INDEX REBUILD statement with the following index rebuild options:</span></span>  
  
-   <span data-ttu-id="24d69-108">FILLFACTOR 비율을 지정하거나 원래 FILLFACTOR 수량을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="24d69-108">Specify a FILLFACTOR percentage or use the original FILLFACTOR amount.</span></span>  
  
-   <span data-ttu-id="24d69-109">PAD_INDEX = ON을 설정하여 FILLFACTOR로 지정된 사용 가능한 공간을 인덱스의 중간 수준 페이지에 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d69-109">Set PAD_INDEX = ON to allocate the free space specified by FILLFACTOR to the intermediate-level pages of the index.</span></span>  
  
-   <span data-ttu-id="24d69-110">SORT_IN_TEMPDB = ON을 설정하여 인덱스를 다시 작성하는 데 사용된 중간 정렬 결과를 tempdb에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d69-110">Set SORT_IN_TEMPDB = ON to store the intermediate sort result used to rebuild the index in tempdb.</span></span> <span data-ttu-id="24d69-111">중간 정렬 결과를 OFF로 설정하면 인덱스와 동일한 데이터베이스에 결과가 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="24d69-111">When the intermediate sort result is set to OFF, the result is stored in the same database as the index.</span></span>  
  
-   <span data-ttu-id="24d69-112">IGNORE_DUP_KEY = ON을 설정하여 UNIQUE 제약 조건을 위반하는 레코드가 포함된 다중 행 삽입 작업에서 UNIQUE 제약 조건을 위반하지 않는 레코드를 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d69-112">Set IGNORE_DUP_KEY = ON to allow a multirow insert operation that includes records that violate unique constraints to insert the records that do not violate the unique constraints.</span></span>  
  
-   <span data-ttu-id="24d69-113">ONLINE = ON을 설정하여 다시 인덱싱하는 동안 기본 테이블에 대한 쿼리 또는 업데이트가 진행될 수 있도록 테이블을 잠그지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d69-113">Set ONLINE = ON to not hold table locks so that queries or updates to the underlying table can proceed during re-indexing.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="24d69-114">온라인 인덱스 작업은 일부 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d69-114">Online index operations are not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="24d69-115">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="24d69-115">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="24d69-116">ALTER INDEX 문과 인덱스 다시 작성 옵션에 대한 자세한 내용은 [ALTER INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24d69-116">For more information about the ALTER INDEX statement and index rebuild options, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="24d69-117">태스크에서 실행할 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 만드는 데 걸리는 시간은 태스크에서 다시 작성하는 인덱스 수에 비례합니다.</span><span class="sxs-lookup"><span data-stu-id="24d69-117">The time the task takes to create the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that the task runs is proportionate to the number of indexes the task rebuilds.</span></span> <span data-ttu-id="24d69-118">많은 수의 인덱스가 있는 데이터베이스의 모든 테이블과 뷰의 인덱스를 다시 작성하거나 여러 데이터베이스의 인덱스를 다시 작성하도록 태스크를 구성하면 Transact-SQL 문을 생성하는 데 시간이 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d69-118">If the task is configured to rebuild indexes in all the tables and views in a database with a large number of indexes, or to rebuild indexes in multiple databases, the task can take a considerable amount of time to generate the Transact-SQL statement.</span></span>  
  
## <a name="configuration-of-the-rebuild-index-task"></a><span data-ttu-id="24d69-119">인덱스 다시 작성 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="24d69-119">Configuration of the Rebuild Index Task</span></span>  
 <span data-ttu-id="24d69-120">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d69-120">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="24d69-121">이 태스크는 **디자이너의** 도구 상자 **에 있는** 유지 관리 계획 태스크 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 섹션에서 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d69-121">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="24d69-122">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="24d69-122">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
 [<span data-ttu-id="24d69-123">인덱스 다시 작성 태스크&#40;유지 관리 계획&#41;</span><span class="sxs-lookup"><span data-stu-id="24d69-123">Rebuild Index Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/rebuild-index-task-maintenance-plan.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="24d69-124">관련 작업</span><span class="sxs-lookup"><span data-stu-id="24d69-124">Related Tasks</span></span>  
 <span data-ttu-id="24d69-125">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법에 대한 자세한 내용은 [태스크 또는 컨테이너의 속성 설정](../set-the-properties-of-a-task-or-container.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24d69-125">For more about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24d69-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="24d69-126">See Also</span></span>  
 <span data-ttu-id="24d69-127">[Integration Services 태스크](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="24d69-127">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="24d69-128">제어 흐름</span><span class="sxs-lookup"><span data-stu-id="24d69-128">Control Flow</span></span>](control-flow.md)  
  
  
