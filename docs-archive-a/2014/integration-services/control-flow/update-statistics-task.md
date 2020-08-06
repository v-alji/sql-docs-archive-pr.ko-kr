---
title: 통계 업데이트 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.updatestatisticstask.f1
helpviewer_keywords:
- updating statistics
- Update Statistics task [Integration Services]
ms.assetid: 0247483b-f092-4511-8fa8-3610108bd1bc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1507ada1e4fa087901383930fce4996c191fb553
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638921"
---
# <a name="update-statistics-task"></a><span data-ttu-id="1a76a-102">통계 업데이트 태스크</span><span class="sxs-lookup"><span data-stu-id="1a76a-102">Update Statistics Task</span></span>
  <span data-ttu-id="1a76a-103">통계 업데이트 태스크는 지정된 테이블이나 인덱싱된 뷰에서 하나 이상의 통계 그룹(컬렉션)의 키 값 배포에 대한 정보를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="1a76a-103">The Update Statistics task updates information about the distribution of key values for one or more statistics groups (collections) in the specified table or indexed view.</span></span> <span data-ttu-id="1a76a-104">자세한 내용은 [통계](../../relational-databases/statistics/statistics.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1a76a-104">For more information, see [Statistics](../../relational-databases/statistics/statistics.md).</span></span>  
  
 <span data-ttu-id="1a76a-105">통계 업데이트 태스크를 사용하면 패키지가 단일 데이터베이스나 여러 데이터베이스의 통계를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a76a-105">By using the Update Statistics task, a package can update statistics for a single database or multiple databases.</span></span> <span data-ttu-id="1a76a-106">태스크가 단일 데이터베이스의 통계만 업데이트하는 경우 통계를 업데이트할 뷰 또는 테이블을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a76a-106">If the task updates only the statistics in a single database, you can choose the views or the tables whose statistics the task updates.</span></span> <span data-ttu-id="1a76a-107">모든 통계, 열 통계만 또는 인덱스 통계만 업데이트하도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a76a-107">You can configure the update to update all statistics, column statistics only, or index statistics only.</span></span>  
  
 <span data-ttu-id="1a76a-108">이 태스크는 다음 인수와 절을 포함하여 UPDATE STATISTICS 문을 캡슐화합니다.</span><span class="sxs-lookup"><span data-stu-id="1a76a-108">This task encapsulates an UPDATE STATISTICS statement, including the following arguments and clauses:</span></span>  
  
-   <span data-ttu-id="1a76a-109">*table_name* 또는 *view_name* 인수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a76a-109">The *table_name* or *view_name* argument.</span></span>  
  
-   <span data-ttu-id="1a76a-110">업데이트가 모든 통계에 적용되면 WITH ALL 절이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a76a-110">If the update applies to all statistics, the WITH ALL clause is implied.</span></span>  
  
-   <span data-ttu-id="1a76a-111">업데이트가 열에만 적용되면 WITH COLUMN 절이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a76a-111">If the update applies only to columns, the WITH COLUMN clause is included.</span></span>  
  
-   <span data-ttu-id="1a76a-112">업데이트가 인덱스에만 적용되면 WITH INDEX 절이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a76a-112">If the update applies only to indexes, the WITH INDEX clause is included.</span></span>  
  
 <span data-ttu-id="1a76a-113">통계 업데이트 태스크는 여러 데이터베이스의 통계를 업데이트하는 경우 각 테이블이나 뷰에 대해 하나씩, 여러 개의 UPDATE STATISTICS 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1a76a-113">If the Update Statistics task updates statistics in multiple databases, the task runs multiple UPDATE STATISTICS statements, one for each table or view.</span></span> <span data-ttu-id="1a76a-114">UPDATE STATISTICS의 모든 인스턴스는 동일한 절을 사용하지만 *table_name* 또는 *view_name* 값이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="1a76a-114">All instances of UPDATE STATISTICS use the same clause, but different *table_name* or *view_name* values.</span></span> <span data-ttu-id="1a76a-115">자세한 내용은 [CREATE STATISTICS&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql) 및 [UPDATE STATISTICS&#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1a76a-115">For more information, see [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql) and [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1a76a-116">태스크에서 실행할 Transact-SQL 문을 만드는 데 걸리는 시간은 태스크에서 업데이트하는 통계 수에 비례합니다.</span><span class="sxs-lookup"><span data-stu-id="1a76a-116">The time the task takes to create the Transact-SQL statement that the task runs is proportionate to the number of statistics the task updates.</span></span> <span data-ttu-id="1a76a-117">많은 수의 인덱스가 있는 데이터베이스의 모든 테이블과 뷰의 통계를 업데이트하거나 여러 데이터베이스의 통계를 업데이트하도록 태스크를 구성하면 Transact-SQL 문을 생성하는 데 시간이 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a76a-117">If the task is configured to update statistics in all the tables and views in a database with a large number of indexes, or to update statistics in multiple databases, the task can take a considerable amount of time to generate the Transact-SQL statement.</span></span>  
  
## <a name="configuration-of-the-update-statistics-task"></a><span data-ttu-id="1a76a-118">통계 업데이트 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="1a76a-118">Configuration of the Update Statistics Task</span></span>  
 <span data-ttu-id="1a76a-119">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a76a-119">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="1a76a-120">이 태스크는 **디자이너의** 도구 상자 **에 있는** 유지 관리 계획 태스크 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 섹션에서 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a76a-120">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="1a76a-121">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="1a76a-121">For information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="1a76a-122">통계 업데이트 태스크&#40;유지 관리 계획&#41;</span><span class="sxs-lookup"><span data-stu-id="1a76a-122">Update Statistics Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/update-statistics-task-maintenance-plan.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="1a76a-123">관련 작업</span><span class="sxs-lookup"><span data-stu-id="1a76a-123">Related Tasks</span></span>  
 <span data-ttu-id="1a76a-124">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="1a76a-124">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="1a76a-125">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="1a76a-125">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="1a76a-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1a76a-126">See Also</span></span>  
 <span data-ttu-id="1a76a-127">[Integration Services 태스크](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="1a76a-127">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="1a76a-128">제어 흐름</span><span class="sxs-lookup"><span data-stu-id="1a76a-128">Control Flow</span></span>](control-flow.md)  
  
  
