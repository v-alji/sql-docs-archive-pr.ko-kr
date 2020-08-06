---
title: 데이터베이스 스냅샷 스파스 파일의 크기 보기(Transact-SQL) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server database snapshots], sparse files
- space [SQL Server], sparse files
- sparse files [SQL Server]
- size [SQL Server], sparse files
- maximum sparse file size
- database snapshots [SQL Server], sparse files
- space [SQL Server], database snapshots
ms.assetid: 1867c5f8-d57c-46d3-933d-3642ab0a8e24
author: stevestein
ms.author: sstein
ms.openlocfilehash: 424399b9915c8e7e26e1076fd2e553aafe06fcf0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735311"
---
# <a name="view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql"></a><span data-ttu-id="3be0b-102">데이터베이스 스냅샷 스파스 파일의 크기 보기(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3be0b-102">View the Size of the Sparse File of a Database Snapshot (Transact-SQL)</span></span>
  <span data-ttu-id="3be0b-103">이 항목에서는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 파일이 스파스 파일인지 확인하고 이 파일의 실제 크기 및 최대 크기를 찾는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3be0b-103">This topic describes how to use [!INCLUDE[tsql](../../includes/tsql-md.md)] to verify that a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database file is a sparse file and to find out its actual and maximum sizes.</span></span> <span data-ttu-id="3be0b-104">NTFS 파일 시스템의 기능인 스파스 파일은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 스냅샷에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3be0b-104">Sparse files, which are a feature of the NTFS file system, are used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database snapshots.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3be0b-105">데이터베이스 스냅샷을 만드는 동안 CREATE DATABASE 문의 파일 이름을 사용하여 스파스 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3be0b-105">During database snapshot creation, sparse files are created by using the file names in the CREATE DATABASE statement.</span></span> <span data-ttu-id="3be0b-106">이러한 파일 이름은 **physical_name** 열의 **sys.master_files** 에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="3be0b-106">These file names are stored in **sys.master_files** in the **physical_name** column.</span></span> <span data-ttu-id="3be0b-107">**sys.database_files** (원본 데이터베이스 또는 스냅샷에 있음)의 **physical_name** 열에는 항상 원본 데이터베이스 파일 이름이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3be0b-107">In **sys.database_files** (whether in the source database or in a snapshot), the **physical_name** column always contains the names of the source database files.</span></span>  
  
## <a name="verify-that-a-database-file-is-a-sparse-file"></a><span data-ttu-id="3be0b-108">데이터베이스 파일이 스파스 파일인지 확인</span><span class="sxs-lookup"><span data-stu-id="3be0b-108">Verify that a Database File is a Sparse File</span></span>  
  
1.  <span data-ttu-id="3be0b-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3be0b-109">On the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
     <span data-ttu-id="3be0b-110">데이터베이스 스냅샷의 **sys.database_files** 또는 **sys.master_files** 에서 **is_sparse**열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3be0b-110">Select the **is_sparse** column from either **sys.database_files** in the database snapshot or from **sys.master_files**.</span></span> <span data-ttu-id="3be0b-111">이 값은 다음과 같이 파일이 스파스 파일인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3be0b-111">The value indicates whether the file is a sparse file, as follows:</span></span>  
  
     <span data-ttu-id="3be0b-112">1 = 스파스 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="3be0b-112">1 = File is a sparse file.</span></span>  
  
     <span data-ttu-id="3be0b-113">0 = 스파스 파일이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="3be0b-113">0 = File is not a sparse file.</span></span>  
  
## <a name="find-out-the-actual-size-of-a-sparse-file"></a><span data-ttu-id="3be0b-114">스파스 파일의 실제 크기 확인</span><span class="sxs-lookup"><span data-stu-id="3be0b-114">Find Out the Actual Size of a Sparse File</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3be0b-115">스파스 파일은 64KB씩 증분되므로 디스크상의 스파스 파일 크기는 항상 64KB의 배수입니다.</span><span class="sxs-lookup"><span data-stu-id="3be0b-115">Sparse files grow in 64-kilobyte (KB) increments; thus, the size of a sparse file on disk is always a multiple of 64 KB.</span></span>  
  
 <span data-ttu-id="3be0b-116">스냅숏의 각 스파스 파일이 현재 디스크에서 사용 중인 바이트 수를 보려면 **size_on_disk_bytes** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [dm_io_virtual_file_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-virtual-file-stats-transact-sql) 동적 관리 뷰의 size_on_disk_bytes 열을 쿼리 합니다.</span><span class="sxs-lookup"><span data-stu-id="3be0b-116">To view the number of bytes that each sparse file of a snapshot is currently using on disk, query the **size_on_disk_bytes** column of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][sys.dm_io_virtual_file_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-virtual-file-stats-transact-sql) dynamic management view.</span></span>  
  
 <span data-ttu-id="3be0b-117">스파스 파일이 사용하는 디스크 공간을 보려면 Microsoft Windows에서 파일을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭하여 **디스크 할당 크기** 값을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="3be0b-117">To view the disk space used by a sparse file, right-click the file in Microsoft Windows, click **Properties**, and look at the **Size on disk** value.</span></span>  
  
## <a name="find-out-the-maximum-size-of-a-sparse-file"></a><span data-ttu-id="3be0b-118">스파스 파일의 최대 크기 확인</span><span class="sxs-lookup"><span data-stu-id="3be0b-118">Find Out the Maximum Size of a Sparse File</span></span>  
 <span data-ttu-id="3be0b-119">스파스 파일이 증가할 수 있는 최대 크기는 스냅샷을 작성한 시점의 해당 원본 데이터베이스 파일 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="3be0b-119">The maximum size to which a sparse can grow is the size of the corresponding source database file at the time of the snapshot creation.</span></span> <span data-ttu-id="3be0b-120">이 크기를 확인하는 데 사용할 수 있는 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3be0b-120">To learn this size, you can use one of the following alternatives:</span></span>  
  
-   <span data-ttu-id="3be0b-121">Windows 명령 프롬프트 사용:</span><span class="sxs-lookup"><span data-stu-id="3be0b-121">Using Windows Command Prompt:</span></span>  
  
    1.  <span data-ttu-id="3be0b-122">Windows **dir** 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3be0b-122">Use Windows **dir** commands.</span></span>  
  
    2.  <span data-ttu-id="3be0b-123">Windows에서 스파스 파일을 선택하고 **속성** 대화 상자를 연 다음 **크기** 값을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="3be0b-123">Select the sparse file, open the file **Properties** dialog box in Windows, and look at the **Size** value.</span></span>  
  
-   <span data-ttu-id="3be0b-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3be0b-124">On the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
     <span data-ttu-id="3be0b-125">데이터베이스 스냅샷의 **sys.database_files** 또는 **sys.master_files** 에서 **size**열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3be0b-125">Select the **size** column from either **sys.database_files** in the database snapshot or from **sys.master_files**.</span></span> <span data-ttu-id="3be0b-126">**size** 열의 값은 SQL 페이지에서 스냅샷이 사용할 수 있는 최대 공간을 반영합니다. 이 값은 파일의 SQL 페이지 수를 기준으로 표시된다는 점을 제외하고 Windows **크기** 필드에 해당하며 바이트 단위의 크기는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3be0b-126">The value of **size** column reflects the maximum space, in SQL pages, that the snapshot can ever use; this value is equivalent to the Windows **Size** field, except that it is represented in terms of the number of SQL pages in the file; the size in bytes is:</span></span>  
  
     <span data-ttu-id="3be0b-127">( *number_of_pages* \* 8192)</span><span class="sxs-lookup"><span data-stu-id="3be0b-127">( *number_of_pages* \* 8192)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3be0b-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3be0b-128">See Also</span></span>  
 <span data-ttu-id="3be0b-129">[데이터베이스 스냅샷&#40;SQL Server&#41;](database-snapshots-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3be0b-129">[Database Snapshots &#40;SQL Server&#41;](database-snapshots-sql-server.md) </span></span>  
 <span data-ttu-id="3be0b-130">[sys.fn_virtualfilestats&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-virtualfilestats-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3be0b-130">[sys.fn_virtualfilestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-virtualfilestats-transact-sql) </span></span>  
 <span data-ttu-id="3be0b-131">[sys.database_files&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3be0b-131">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span></span>  
 [<span data-ttu-id="3be0b-132">sys.master_files&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3be0b-132">sys.master_files &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)  
  
  
