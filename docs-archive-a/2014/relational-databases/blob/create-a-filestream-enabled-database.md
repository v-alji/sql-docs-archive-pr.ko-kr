---
title: FILESTREAM 사용 데이터베이스 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], FILESTREAM-enabled databases
ms.assetid: 0fc16356-76f7-44b8-a58b-f0b7c43694ec
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0fe6e5bc6e4f60bc0703482f3bf4d761104b3c5f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732699"
---
# <a name="create-a-filestream-enabled-database"></a><span data-ttu-id="52de9-102">FILESTREAM 사용 데이터베이스 만들기</span><span class="sxs-lookup"><span data-stu-id="52de9-102">Create a FILESTREAM-Enabled Database</span></span>
  <span data-ttu-id="52de9-103">이 항목에서는 FILESTREAM을 지원하는 데이터베이스를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="52de9-103">This topic shows how to create a database that supports FILESTREAM.</span></span> <span data-ttu-id="52de9-104">FILESTREAM이 특별한 유형의 파일 그룹을 사용하므로 데이터베이스를 만들 때 하나 이상의 파일 그룹에 대해 CONTAINS FILESTREAM 절을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52de9-104">Because FILESTREAM uses a special type of filegroup, when you create the database, you must specify the CONTAINS FILESTREAM clause for at least one filegroup.</span></span>  
  
 <span data-ttu-id="52de9-105">FILESTREAM 파일 그룹은 두 개 이상의 파일을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52de9-105">A FILESTREAM filegroup can contain more than one file.</span></span> <span data-ttu-id="52de9-106">여러 파일을 포함하는 FILESTREAM 파일 그룹을 만드는 방법을 보여 주는 코드 예제는 [CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52de9-106">For a code example that demonstrates how to create a FILESTREAM filegroup that contains multiple files, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span>  
  
### <a name="to-create-a-filestream-enabled-database"></a><span data-ttu-id="52de9-107">FILESTREAM 사용 데이터베이스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="52de9-107">To create a FILESTREAM-enabled database</span></span>  
  
1.  <span data-ttu-id="52de9-108">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 **새 쿼리** 를 클릭하여 쿼리 편집기를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="52de9-108">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], click **New Query** to display the Query Editor.</span></span>  
  
2.  <span data-ttu-id="52de9-109">코드 복사 [!INCLUDE[tsql](../../includes/tsql-md.md)] Archive 라는 FILESTREAM 사용 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="52de9-109">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] code creates a FILESTREAM-enabled database called Archive.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="52de9-110">이 스크립트의 경우 C:\Data 디렉터리가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52de9-110">For this script, the directory C:\Data must exist.</span></span>  
  
3.  <span data-ttu-id="52de9-111">데이터베이스를 작성하려면 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="52de9-111">To build the database, click **Execute**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52de9-112">예제</span><span class="sxs-lookup"><span data-stu-id="52de9-112">Example</span></span>  
 <span data-ttu-id="52de9-113">다음 코드 예에서는 `Archive`라는 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="52de9-113">The following code example creates a database that is named `Archive`.</span></span> <span data-ttu-id="52de9-114">이 데이터베이스는 3개의 파일 그룹 `PRIMARY`, `Arch1`및 `FileStreamGroup1`을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="52de9-114">The database contains three filegroups: `PRIMARY`, `Arch1`, and `FileStreamGroup1`.</span></span> <span data-ttu-id="52de9-115">`PRIMARY` 및 `Arch1` 은 FILESTREAM 데이터를 포함할 수 없는 일반 파일 그룹이고,</span><span class="sxs-lookup"><span data-stu-id="52de9-115">`PRIMARY` and `Arch1` are regular filegroups that cannot contain FILESTREAM data.</span></span> <span data-ttu-id="52de9-116">`FileStreamGroup1` 은 `FILESTREAM` 파일 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="52de9-116">`FileStreamGroup1` is the `FILESTREAM` filegroup.</span></span>  
  
```sql  
CREATE DATABASE Archive   
ON  
PRIMARY ( NAME = Arch1,  
    FILENAME = 'c:\data\archdat1.mdf'),  
FILEGROUP FileStreamGroup1 CONTAINS FILESTREAM( NAME = Arch3,  
    FILENAME = 'c:\data\filestream1')  
LOG ON  ( NAME = Archlog1,  
    FILENAME = 'c:\data\archlog1.ldf')  
GO  
```  
  
 <span data-ttu-id="52de9-117">`FILESTREAM` 은 `FILENAME` 파일 그룹의 경로를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="52de9-117">For a `FILESTREAM` filegroup, `FILENAME` refers to a path.</span></span> <span data-ttu-id="52de9-118">따라서 마지막 폴더 바로 위의 경로까지 있어야 하고 마지막 폴더 자체는 있으면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52de9-118">The path up to the last folder must exist, and the last folder must not exist.</span></span> <span data-ttu-id="52de9-119">이 예제에서는 `c:\data` 가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52de9-119">In this example, `c:\data` must exist.</span></span> <span data-ttu-id="52de9-120">그러나 `filestream1` 문을 실행할 때 `CREATE DATABASE` 하위 폴더는 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52de9-120">However, the `filestream1` subfolder cannot exist when you execute the `CREATE DATABASE` statement.</span></span> <span data-ttu-id="52de9-121">구문에 대한 자세한 내용은 [CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52de9-121">For more information about the syntax, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span>  
  
 <span data-ttu-id="52de9-122">위의 예를 실행하고 나면 c:\Data\filestream1 폴더에 filestream.hdr 파일과 $FSLOG 폴더가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="52de9-122">After you run the previous example, a filestream.hdr file and an $FSLOG folder appears in the c:\Data\filestream1 folder.</span></span> <span data-ttu-id="52de9-123">filestream.hdr 파일은 FILESTREAM 컨테이너 헤더 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="52de9-123">The filestream.hdr file is a header file for the FILESTREAM container.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="52de9-124">filestream.hdr 파일은 중요한 시스템 파일이므로</span><span class="sxs-lookup"><span data-stu-id="52de9-124">The filestream.hdr file is an important system file.</span></span> <span data-ttu-id="52de9-125">FILESTREAM 헤더 정보를 포함하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52de9-125">It contains FILESTREAM header information.</span></span> <span data-ttu-id="52de9-126">이 파일은 제거하거나 수정하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52de9-126">Do not remove or modify this file.</span></span>  
  
 <span data-ttu-id="52de9-127">기존 데이터베이스의 경우 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) 문을 사용하여 FILESTREAM 파일 그룹을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52de9-127">For existing databases, you can use the [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement to add a FILESTREAM filegroup.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52de9-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="52de9-128">See Also</span></span>  
 <span data-ttu-id="52de9-129">[CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="52de9-129">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 [<span data-ttu-id="52de9-130">ALTER DATABASE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="52de9-130">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
