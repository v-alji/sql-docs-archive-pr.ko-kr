---
title: 데이터베이스 속성(파일 그룹 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.filegroups.f1
ms.assetid: 8d06e859-73dd-4019-b6e8-99c5c5297697
author: stevestein
ms.author: sstein
ms.openlocfilehash: d0546a17491ed5d3b36890a605c5faa922c24fe6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650097"
---
# <a name="database-properties-filegroups-page"></a><span data-ttu-id="dea51-102">데이터베이스 속성(파일 그룹 페이지)</span><span class="sxs-lookup"><span data-stu-id="dea51-102">Database Properties (Filegroups Page)</span></span>
  <span data-ttu-id="dea51-103">이 페이지를 사용하여 파일 그룹을 확인하거나 선택한 데이터베이스에 새 파일 그룹을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dea51-103">Use this page to view the filegroups or add a new filegroup to the selected database.</span></span> <span data-ttu-id="dea51-104">파일 그룹 유형은 *행* 파일 그룹, FILESTREAM 데이터 및 메모리 최적화 파일 그룹으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="dea51-104">Filegroup types are separated into *row* filegroups, FILESTREAM data, and memory-optimized filegroups.</span></span>  
  
 <span data-ttu-id="dea51-105">행 파일 그룹에는 일반 데이터 파일 및 로그 파일이 있고,</span><span class="sxs-lookup"><span data-stu-id="dea51-105">Row filegroups contain regular data and log files.</span></span> <span data-ttu-id="dea51-106">FILESTREAM 데이터 파일 그룹에는 FILESTREAM 데이터 파일이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dea51-106">FILESTREAM data filegroups contain FILESTREAM data files.</span></span> <span data-ttu-id="dea51-107">이러한 데이터 파일은 FILESTREAM 스토리지를 사용할 경우 BLOB(Binary Large Object) 데이터가 파일 시스템에 저장되는 방식에 대한 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="dea51-107">These data files store information about how binary large object (BLOB) data is stored on the file system when you are using FILESTREAM storage.</span></span> <span data-ttu-id="dea51-108">옵션은 두 가지 파일 그룹 유형에서 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="dea51-108">The options are the same for both types of filegroups.</span></span>  
  
 <span data-ttu-id="dea51-109">FILESTREAM이 설정되지 않은 경우 **Filestream** 섹션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dea51-109">If FILESTREAM is not enabled, the **Filestream** section will not be available.</span></span> <span data-ttu-id="dea51-110">[서버 속성(고급 페이지)](../../database-engine/configure-windows/server-properties-advanced-page.md)을 사용하여 FILESTREAM 스토리지를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dea51-110">You can enable FILESTREAM storage by using [Server Properties (Advanced Page)](../../database-engine/configure-windows/server-properties-advanced-page.md).</span></span>  
  
 <span data-ttu-id="dea51-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 행 파일 그룹을 사용하는 방법은 [데이터베이스 파일 및 파일 그룹](database-files-and-filegroups.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dea51-111">For information about how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses row filegroups, see [Database Files and Filegroups](database-files-and-filegroups.md).</span></span> <span data-ttu-id="dea51-112">FILESTREAM 데이터 및 파일 그룹에 대한 자세한 내용은 [FILESTREAM&#40;SQL Server&#41;](../blob/filestream-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dea51-112">For more information about FILESTREAM data and filegroups, see [FILESTREAM &#40;SQL Server&#41;](../blob/filestream-sql-server.md).</span></span>  
  
 <span data-ttu-id="dea51-113">데이터베이스가 메모리 최적화 테이블을 하나 이상 포함하려면 메모리 최적화 파일 그룹이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="dea51-113">Memory-optimized file groups are required for a database to contain one or more memory-optimized tables.</span></span>  
  
## <a name="row-and-filestream-data-filegroup-options"></a><span data-ttu-id="dea51-114">행 및 FILESTREAM 데이터 파일 그룹 옵션</span><span class="sxs-lookup"><span data-stu-id="dea51-114">Row and FILESTREAM Data Filegroup Options</span></span>  
 <span data-ttu-id="dea51-115">**이름**</span><span class="sxs-lookup"><span data-stu-id="dea51-115">**Name**</span></span>  
 <span data-ttu-id="dea51-116">파일 그룹의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dea51-116">Enter the name of the filegroup.</span></span>  
  
 <span data-ttu-id="dea51-117">**파일**</span><span class="sxs-lookup"><span data-stu-id="dea51-117">**Files**</span></span>  
 <span data-ttu-id="dea51-118">파일 그룹의 파일 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="dea51-118">Displays the count of files in the filegroup.</span></span>  
  
 <span data-ttu-id="dea51-119">**읽기 전용**</span><span class="sxs-lookup"><span data-stu-id="dea51-119">**Read-only**</span></span>  
 <span data-ttu-id="dea51-120">파일 그룹을 읽기 전용 상태로 설정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dea51-120">Select to set the filegroup to a read-only status.</span></span>  
  
 <span data-ttu-id="dea51-121">**기본값**</span><span class="sxs-lookup"><span data-stu-id="dea51-121">**Default**</span></span>  
 <span data-ttu-id="dea51-122">이 파일 그룹을 기본 파일 그룹으로 만들려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dea51-122">Select to make this filegroup the default filegroup.</span></span> <span data-ttu-id="dea51-123">행 및 FILESTREAM 데이터에 대해 각각 한 개의 기본 파일 그룹을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dea51-123">You can have one default filegroup for rows and one default filegroup for FILESTREAM data.</span></span>  
  
 <span data-ttu-id="dea51-124">**추가**</span><span class="sxs-lookup"><span data-stu-id="dea51-124">**Add**</span></span>  
 <span data-ttu-id="dea51-125">데이터베이스에 대한 파일 그룹을 나열하는 표에 빈 행을 새로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dea51-125">Adds a new blank row to the grid listing filegroups for the database.</span></span>  
  
 <span data-ttu-id="dea51-126">**제거**</span><span class="sxs-lookup"><span data-stu-id="dea51-126">**Remove**</span></span>  
 <span data-ttu-id="dea51-127">표에서 선택한 파일 그룹 행을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="dea51-127">Removes the selected filegroup row from the grid.</span></span>  
  
## <a name="memory-optimized-data-filegroup-options"></a><span data-ttu-id="dea51-128">메모리 액세스에 최적화된 데이터 파일 그룹 옵션</span><span class="sxs-lookup"><span data-stu-id="dea51-128">Memory-Optimized Data Filegroup Options</span></span>  
 <span data-ttu-id="dea51-129">**이름**</span><span class="sxs-lookup"><span data-stu-id="dea51-129">**Name**</span></span>  
 <span data-ttu-id="dea51-130">메모리 최적화 파일 그룹의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dea51-130">Enter the name of the memory-optimized filegroup.</span></span>  
  
 <span data-ttu-id="dea51-131">**Filestream 파일**</span><span class="sxs-lookup"><span data-stu-id="dea51-131">**Filestream Files**</span></span>  
 <span data-ttu-id="dea51-132">메모리 최적화 데이터 파일 그룹에 있는 파일(컨테이너)의 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="dea51-132">Displays the number of files (containers) in the memory-optimized data filegroup.</span></span> <span data-ttu-id="dea51-133">**파일** 페이지에서 컨테이너를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dea51-133">You can add containers in the **Files** page.</span></span>  
  
 <span data-ttu-id="dea51-134">**추가**</span><span class="sxs-lookup"><span data-stu-id="dea51-134">**Add**</span></span>  
 <span data-ttu-id="dea51-135">데이터베이스에 대한 파일 그룹을 나열하는 표에 빈 행을 새로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dea51-135">Adds a new blank row to the grid listing filegroups for the database.</span></span>  
  
 <span data-ttu-id="dea51-136">**제거**</span><span class="sxs-lookup"><span data-stu-id="dea51-136">**Remove**</span></span>  
 <span data-ttu-id="dea51-137">표에서 선택한 파일 그룹 행을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="dea51-137">Removes the selected filegroup row from the grid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dea51-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dea51-138">See Also</span></span>  
 <span data-ttu-id="dea51-139">[ALTER DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dea51-139">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="dea51-140">sys.databases&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dea51-140">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
