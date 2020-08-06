---
title: 데이터베이스 축소 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.shrinkdatabasetask.f1
helpviewer_keywords:
- Shrink Database task
- database shrinking [Integration Services]
- shrinking databases
ms.assetid: e66286f8-97b1-4e5a-86b4-e56f1932b7d5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 587777928e362e87e4b691e3c46167c1239984cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659595"
---
# <a name="shrink-database-task"></a><span data-ttu-id="8bc31-102">데이터베이스 축소 태스크</span><span class="sxs-lookup"><span data-stu-id="8bc31-102">Shrink Database Task</span></span>
  <span data-ttu-id="8bc31-103">데이터베이스 축소 태스크는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 데이터와 로그 파일의 크기를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="8bc31-103">The Shrink Database task reduces the size of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database data and log files.</span></span>  
  
 <span data-ttu-id="8bc31-104">데이터베이스 축소 태스크를 사용하면 패키지가 단일 데이터베이스나 여러 데이터베이스의 파일을 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc31-104">By using the Shrink Database task, a package can shrink files for a single database or multiple databases.</span></span>  
  
 <span data-ttu-id="8bc31-105">파일 끝에 있는 데이터 페이지를 파일 앞의 사용되지 않은 공간으로 이동하여 데이터 파일을 축소하면 공간이 복구됩니다.</span><span class="sxs-lookup"><span data-stu-id="8bc31-105">Shrinking data files recovers space by moving pages of data from the end of the file to unoccupied space closer to the front of the file.</span></span> <span data-ttu-id="8bc31-106">파일 끝에 사용 가능한 공간을 충분히 확보한 다음 파일 끝에 있는 데이터 페이지를 할당 해제하고 파일 시스템에 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc31-106">When enough free space is created at the end of the file, data pages at end of the file can deallocated and returned to the file system.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="8bc31-107">파일 축소를 위해 이동되는 데이터는 파일 내의 모든 사용 가능한 위치로 분산될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc31-107">Data that is moved to shrink a file can be scattered to any available location in the file.</span></span> <span data-ttu-id="8bc31-108">이로 인해 인덱스 조각화가 발생하여 인덱스 범위를 검색하는 쿼리 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc31-108">This causes index fragmentation and can slow the performance of queries that search a range of the index.</span></span> <span data-ttu-id="8bc31-109">조각화를 방지하려면 축소 후 파일에 대한 인덱스를 다시 작성하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc31-109">To eliminate the fragmentation, consider rebuilding the indexes on the file after shrinking.</span></span>  
  
## <a name="commands"></a><span data-ttu-id="8bc31-110">명령</span><span class="sxs-lookup"><span data-stu-id="8bc31-110">Commands</span></span>  
 <span data-ttu-id="8bc31-111">데이터베이스 축소 태스크는 다음 인수와 옵션을 포함하여 DBCC SHRINKDATABASE 명령을 캡슐화합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc31-111">The Shrink Database task encapsulates a DBCC SHRINKDATABASE command, including the following arguments and options:</span></span>  
  
-   <span data-ttu-id="8bc31-112">*database_name*</span><span class="sxs-lookup"><span data-stu-id="8bc31-112">*database_name*</span></span>  
  
-   <span data-ttu-id="8bc31-113">*target_percent*</span><span class="sxs-lookup"><span data-stu-id="8bc31-113">*target_percent*</span></span>  
  
-   <span data-ttu-id="8bc31-114">NOTRUNCATE 또는 TRUNCATEONLY</span><span class="sxs-lookup"><span data-stu-id="8bc31-114">NOTRUNCATE or TRUNCATEONLY.</span></span>  
  
 <span data-ttu-id="8bc31-115">데이터베이스 축소 태스크에서 여러 데이터베이스를 축소하는 경우 각 데이터베이스에 대해 하나씩, 여러 개의 SHRINKDATABASE 명령이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="8bc31-115">If the Shrink Database task shrinks multiple databases, the task runs multiple SHRINKDATABASE commands, one for each database.</span></span> <span data-ttu-id="8bc31-116">SHRINKDATABASE 명령의 각 인스턴스는 *database_name* 인수를 제외하고 모두 동일한 인수 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc31-116">All instances of the SHRINKDATABASE command use the same argument values, except for the *database_name* argument.</span></span> <span data-ttu-id="8bc31-117">자세한 내용은 [DBCC SHRINKDATABASE&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8bc31-117">For more information, see [DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql).</span></span>  
  
## <a name="configuration-of-the-shrink-database-task"></a><span data-ttu-id="8bc31-118">데이터베이스 축소 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="8bc31-118">Configuration of the Shrink Database Task</span></span>  
 <span data-ttu-id="8bc31-119">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc31-119">You can set properties through the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="8bc31-120">이 태스크는 **디자이너의** 도구 상자 **에 있는** 유지 관리 계획 태스크 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 섹션에서 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc31-120">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="8bc31-121">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="8bc31-121">For more information about the properties that you can set in the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="8bc31-122">데이터베이스 축소 태스크&#40;유지 관리 계획&#41;</span><span class="sxs-lookup"><span data-stu-id="8bc31-122">Shrink Database Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/shrink-database-task-maintenance-plan.md)  
  
 <span data-ttu-id="8bc31-123">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="8bc31-123">For more information about setting these properties in the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="8bc31-124">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="8bc31-124">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
  
