---
title: 데이터베이스 파일 및 파일 그룹 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], files
- filegroups [SQL Server]
- transaction logs [SQL Server], about
- transaction logs [SQL Server], files
- .mdf files
- data files [SQL Server]
- default filegroups
- files [SQL Server], about files and filegroups
- secondary files [SQL Server]
- log files [SQL Server]
- .ndf files
- files [SQL Server]
- .ldf files
- database files [SQL Server]
- databases [SQL Server], filegroups
- filegroups [SQL Server], types
- primary filegroups [SQL Server]
- user-defined filegroups [SQL Server]
- filegroups [SQL Server], about filegroups
- primary files [SQL Server]
- file types [SQL Server]
ms.assetid: 9ca11918-480d-4838-9198-cec221ef6ad0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 91e22e536a91878609feedf2977ffa7d78a54d61
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650112"
---
# <a name="database-files-and-filegroups"></a><span data-ttu-id="4ab5b-102">데이터베이스 파일 및 파일 그룹</span><span class="sxs-lookup"><span data-stu-id="4ab5b-102">Database Files and Filegroups</span></span>
  <span data-ttu-id="4ab5b-103">모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에는 최소한 두 개의 운영 체제 파일인 데이터 파일과 로그 파일이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-103">At a minimum, every [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database has two operating system files: a data file and a log file.</span></span> <span data-ttu-id="4ab5b-104">데이터 파일은 테이블, 인덱스, 저장 프로시저 및 뷰 등의 개체와 데이터를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-104">Data files contain data and objects such as tables, indexes, stored procedures, and views.</span></span> <span data-ttu-id="4ab5b-105">로그 파일은 데이터베이스의 모든 트랜잭션을 복구하는 데 필요한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-105">Log files contain the information that is required to recover all transactions in the database.</span></span> <span data-ttu-id="4ab5b-106">데이터 파일은 할당 및 관리를 간편하게 수행하기 위해 파일 그룹으로 그룹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-106">Data files can be grouped together in filegroups for allocation and administration purposes.</span></span>  
  
## <a name="database-files"></a><span data-ttu-id="4ab5b-107">데이터베이스 파일</span><span class="sxs-lookup"><span data-stu-id="4ab5b-107">Database Files</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4ab5b-108">데이터베이스에는 다음 표에 설명된 것처럼 세 가지 유형의 파일이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-108">databases have three types of files, as shown in the following table.</span></span>  
  
|<span data-ttu-id="4ab5b-109">파일</span><span class="sxs-lookup"><span data-stu-id="4ab5b-109">File</span></span>|<span data-ttu-id="4ab5b-110">Description</span><span class="sxs-lookup"><span data-stu-id="4ab5b-110">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="4ab5b-111">주</span><span class="sxs-lookup"><span data-stu-id="4ab5b-111">Primary</span></span>|<span data-ttu-id="4ab5b-112">주 데이터 파일은 데이터베이스의 시작 정보를 포함하며 데이터베이스의 나머지 파일을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-112">The primary data file contains the startup information for the database and points to the other files in the database.</span></span> <span data-ttu-id="4ab5b-113">사용자 데이터와 개체를 이 파일에 저장하거나 보조 데이터 파일에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-113">User data and objects can be stored in this file or in secondary data files.</span></span> <span data-ttu-id="4ab5b-114">모든 데이터베이스에는 하나의 주 데이터 파일이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-114">Every database has one primary data file.</span></span> <span data-ttu-id="4ab5b-115">권장되는 주 데이터 파일 확장명은 .mdf입니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-115">The recommended file name extension for primary data files is .mdf.</span></span>|  
|<span data-ttu-id="4ab5b-116">보조</span><span class="sxs-lookup"><span data-stu-id="4ab5b-116">Secondary</span></span>|<span data-ttu-id="4ab5b-117">보조 데이터 파일은 선택적으로 사용하는 사용자 정의 데이터 파일이며 사용자 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-117">Secondary data files are optional, are user-defined, and store user data.</span></span> <span data-ttu-id="4ab5b-118">보조 파일은 각 파일을 서로 다른 디스크 드라이브에 배치하여 데이터를 여러 디스크에 분산시키는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-118">Secondary files can be used to spread data across multiple disks by putting each file on a different disk drive.</span></span> <span data-ttu-id="4ab5b-119">또한 데이터베이스가 단일 Windows 파일의 최대 크기를 초과할 경우 보조 데이터 파일을 사용하여 데이터베이스 크기를 계속해서 늘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-119">Additionally, if a database exceeds the maximum size for a single Windows file, you can use secondary data files so the database can continue to grow.</span></span><br /><br /> <span data-ttu-id="4ab5b-120">권장되는 보조 데이터 파일 확장명은 .ndf입니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-120">The recommended file name extension for secondary data files is .ndf.</span></span>|  
|<span data-ttu-id="4ab5b-121">트랜잭션 로그</span><span class="sxs-lookup"><span data-stu-id="4ab5b-121">Transaction Log</span></span>|<span data-ttu-id="4ab5b-122">트랜잭션 로그 파일은 데이터베이스 복구에 사용되는 로그 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-122">The transaction log files hold the log information that is used to recover the database.</span></span> <span data-ttu-id="4ab5b-123">데이터베이스마다 최소한 하나의 로그 파일이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-123">There must be at least one log file for each database.</span></span> <span data-ttu-id="4ab5b-124">권장되는 트랜잭션 로그 파일 확장명은 .ldf입니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-124">The recommended file name extension for transaction logs is .ldf.</span></span>|  
  
 <span data-ttu-id="4ab5b-125">예를 들어 모든 데이터와 개체를 하나의 주 파일에 저장하고 트랜잭션 로그 정보를 로그 파일에 저장하는 **Sales** 라는 단순한 데이터베이스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-125">For example, a simple database named **Sales** can be created that includes one primary file that contains all data and objects and a log file that contains the transaction log information.</span></span> <span data-ttu-id="4ab5b-126">또는 한 개의 주 파일과 5개의 보조 파일을 포함하는 **Orders** 라는 더 복잡한 데이터베이스를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-126">Alternatively, a more complex database named **Orders** can be created that includes one primary file and five secondary files.</span></span> <span data-ttu-id="4ab5b-127">데이터베이스 내의 데이터와 개체는 6개의 파일에 분산되고 트랜잭션 로그 정보는 4개의 로그 파일에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-127">The data and objects within the database spread across all six files, and the four log files contain the transaction log information.</span></span>  
  
 <span data-ttu-id="4ab5b-128">기본적으로 데이터와 트랜잭션 로그는 동일한 드라이브와 경로에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-128">By default, the data and transaction logs are put on the same drive and path.</span></span> <span data-ttu-id="4ab5b-129">이것은 단일 디스크 시스템의 경우에 해당하며</span><span class="sxs-lookup"><span data-stu-id="4ab5b-129">This is done to handle single-disk systems.</span></span> <span data-ttu-id="4ab5b-130">프로덕션 환경에서는 최적이 아닐 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-130">However, this may not be optimal for production environments.</span></span> <span data-ttu-id="4ab5b-131">데이터와 로그 파일은 서로 다른 디스크에 배치하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-131">We recommend that you put data and log files on separate disks.</span></span>  
  
## <a name="filegroups"></a><span data-ttu-id="4ab5b-132">파일 그룹</span><span class="sxs-lookup"><span data-stu-id="4ab5b-132">Filegroups</span></span>  
 <span data-ttu-id="4ab5b-133">모든 데이터베이스에는 주 파일 그룹이 한 개씩 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-133">Every database has a primary filegroup.</span></span> <span data-ttu-id="4ab5b-134">주 파일 그룹은 주 데이터 파일과 다른 파일 그룹에 배치되지 않은 보조 파일을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-134">This filegroup contains the primary data file and any secondary files that are not put into other filegroups.</span></span> <span data-ttu-id="4ab5b-135">사용자 정의 파일 그룹을 만들어 데이터 파일을 그룹화함으로써 관리, 데이터 할당 및 배치를 간편하게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-135">User-defined filegroups can be created to group data files together for administrative, data allocation, and placement purposes.</span></span>  
  
 <span data-ttu-id="4ab5b-136">예를 들어 3개의 파일(Data1.ndf, Data2.ndf 및 Data3.ndf)을 3개의 디스크 드라이브에 하나씩 만들어서 **fgroup1**이라는 파일 그룹에 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-136">For example, three files, Data1.ndf, Data2.ndf, and Data3.ndf, can be created on three disk drives, respectively, and assigned to the filegroup **fgroup1**.</span></span> <span data-ttu-id="4ab5b-137">그런 다음 **fgroup1**파일 그룹에 한 개의 테이블을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-137">A table can then be created specifically on the filegroup **fgroup1**.</span></span> <span data-ttu-id="4ab5b-138">이렇게 하면 해당 테이블의 데이터에 대한 쿼리가 3개의 디스크로 분산되므로 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-138">Queries for data from the table will be spread across the three disks; this will improve performance.</span></span> <span data-ttu-id="4ab5b-139">RAID(Redundant Array of Independent Disks) 스트라이프 세트에 단일 파일을 만들어 사용해도 이와 동일한 수준으로 성능이 향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-139">The same performance improvement can be accomplished by using a single file created on a RAID (redundant array of independent disks) stripe set.</span></span> <span data-ttu-id="4ab5b-140">그러나 파일과 파일 그룹을 사용하면 새 디스크에 새 파일을 쉽게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-140">However, files and filegroups let you easily add new files to new disks.</span></span>  
  
 <span data-ttu-id="4ab5b-141">모든 데이터 파일은 다음 표에 나열된 파일 그룹에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-141">All data files are stored in the filegroups listed in the following table.</span></span>  
  
|<span data-ttu-id="4ab5b-142">파일 그룹</span><span class="sxs-lookup"><span data-stu-id="4ab5b-142">Filegroup</span></span>|<span data-ttu-id="4ab5b-143">Description</span><span class="sxs-lookup"><span data-stu-id="4ab5b-143">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4ab5b-144">주</span><span class="sxs-lookup"><span data-stu-id="4ab5b-144">Primary</span></span>|<span data-ttu-id="4ab5b-145">주 파일을 포함하는 파일 그룹.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-145">The filegroup that contains the primary file.</span></span> <span data-ttu-id="4ab5b-146">주 파일 그룹에는 모든 시스템 테이블이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-146">All system tables are allocated to the primary filegroup.</span></span>|  
|<span data-ttu-id="4ab5b-147">사용자 정의</span><span class="sxs-lookup"><span data-stu-id="4ab5b-147">User-defined</span></span>|<span data-ttu-id="4ab5b-148">사용자가 데이터베이스를 처음 만들 때 또는 나중에 수정할 때 만드는 파일 그룹</span><span class="sxs-lookup"><span data-stu-id="4ab5b-148">Any filegroup that is specifically created by the user when the user first creates or later modifies the database.</span></span>|  
  
### <a name="default-filegroup"></a><span data-ttu-id="4ab5b-149">기본 파일 그룹</span><span class="sxs-lookup"><span data-stu-id="4ab5b-149">Default Filegroup</span></span>  
 <span data-ttu-id="4ab5b-150">데이터베이스에서 개체를 만들 때 어떤 파일 그룹에 속하는지 지정하지 않으면 기본 파일 그룹에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-150">When objects are created in the database without specifying which filegroup they belong to, they are assigned to the default filegroup.</span></span> <span data-ttu-id="4ab5b-151">언제든지 정확하게 하나의 파일 그룹이 기본 파일 그룹으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-151">At any time, exactly one filegroup is designated as the default filegroup.</span></span> <span data-ttu-id="4ab5b-152">기본 파일 그룹의 파일은 다른 파일 그룹에 할당되지 않은 모든 새로운 개체를 보관할 수 있을 만큼 크기가 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-152">The files in the default filegroup must be large enough to hold any new objects not allocated to other filegroups.</span></span>  
  
 <span data-ttu-id="4ab5b-153">PRIMARY 파일 그룹은 ALTER DATABASE 문을 사용하여 변경하지 않으면 기본 파일 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-153">The PRIMARY filegroup is the default filegroup unless it is changed by using the ALTER DATABASE statement.</span></span> <span data-ttu-id="4ab5b-154">시스템 개체 및 테이블에 대한 할당은 새 기본 파일 그룹이 아니라 PRIMARY 파일 그룹에 남게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-154">Allocation for the system objects and tables remains within the PRIMARY filegroup, not the new default filegroup.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="4ab5b-155">관련 내용</span><span class="sxs-lookup"><span data-stu-id="4ab5b-155">Related Content</span></span>  
 [<span data-ttu-id="4ab5b-156">CREATE DATABASE&#40;SQL Server Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4ab5b-156">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
 [<span data-ttu-id="4ab5b-157">ALTER DATABASE 파일 및 파일 그룹 옵션&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4ab5b-157">ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)  
  
 [<span data-ttu-id="4ab5b-158">데이터베이스 분리 및 연결&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4ab5b-158">Database Detach and Attach &#40;SQL Server&#41;</span></span>](database-detach-and-attach-sql-server.md)  
  
  
