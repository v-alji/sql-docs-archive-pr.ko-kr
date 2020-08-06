---
title: Transact-SQL을 사용하여 FILESTREAM 데이터 액세스 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], Transact-SQL
ms.assetid: a6bf0ce7-7e5e-4a07-8917-ee526c9d0a05
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 06d395f1acc3723fc6b45fdfa08efbae354d8014
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734168"
---
# <a name="access-filestream-data-with-transact-sql"></a><span data-ttu-id="c51a2-102">Transact-SQL을 사용하여 FILESTREAM 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="c51a2-102">Access FILESTREAM Data with Transact-SQL</span></span>
  <span data-ttu-id="c51a2-103">이 항목에서는 [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT, UPDATE 및 DELETE 문을 사용하여 FILESTREAM 데이터를 관리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c51a2-103">This topic describes how to use the [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT, UPDATE, and DELETE statements to manage FILESTREAM data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c51a2-104">이 항목의 예에서는 [FILESTREAM 사용 데이터베이스 만들기](create-a-filestream-enabled-database.md) 및 [FILESTREAM 데이터 저장용 테이블 만들기](create-a-table-for-storing-filestream-data.md)에서 만든 FILESTREAM 사용 데이터베이스 및 테이블이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c51a2-104">The examples in this topic require the FILESTREAM-enabled database and table that are created in [Create a FILESTREAM-Enabled Database](create-a-filestream-enabled-database.md) and [Create a Table for Storing FILESTREAM Data](create-a-table-for-storing-filestream-data.md).</span></span>  
  
##  <a name="inserting-a-row-that-contains-filestream-data"></a><a name="ins"></a> <span data-ttu-id="c51a2-105">FILESTREAM 데이터가 들어 있는 행 삽입</span><span class="sxs-lookup"><span data-stu-id="c51a2-105">Inserting a Row That Contains FILESTREAM Data</span></span>  
 <span data-ttu-id="c51a2-106">FILESTREAM 데이터를 지원하는 테이블에 행을 추가하려면 [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c51a2-106">To add a row to a table that supports FILESTREAM data, use the [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT statement.</span></span> <span data-ttu-id="c51a2-107">FILESTREAM 열에 데이터를 삽입할 때 NULL 또는 `varbinary(max)` 값을 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c51a2-107">When you insert data into a FILESTREAM column, you can insert NULL or a `varbinary(max)` value.</span></span>  
  
### <a name="inserting-null"></a><span data-ttu-id="c51a2-108">NULL 삽입</span><span class="sxs-lookup"><span data-stu-id="c51a2-108">Inserting NULL</span></span>  
 <span data-ttu-id="c51a2-109">다음 예에서는 `NULL`을 삽입하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c51a2-109">The following example shows how to insert `NULL`.</span></span> <span data-ttu-id="c51a2-110">FILESTREAM 값이 `NULL`이면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 이 파일 시스템에 파일을 만들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c51a2-110">When the FILESTREAM value is `NULL`, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] does not create a file in the file system.</span></span>  
  
 [!code-sql[FILESTREAM#FS_InsertNULL](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_insertnull)]  
  
### <a name="inserting-a-zero-length-record"></a><span data-ttu-id="c51a2-111">길이가 0인 레코드 삽입</span><span class="sxs-lookup"><span data-stu-id="c51a2-111">Inserting a Zero-Length Record</span></span>  
 <span data-ttu-id="c51a2-112">다음 예에서는 `INSERT` 를 사용하여 길이가 0인 레코드를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c51a2-112">The following example shows how to use `INSERT` to create a zero-length record.</span></span> <span data-ttu-id="c51a2-113">길이가 0인 레코드는 파일 핸들을 가져와야 하지만 Win32 API를 사용하여 파일을 조작하는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="c51a2-113">This is useful for when you want to obtain a file handle, but will be manipulating the file by using Win32 APIs.</span></span>  
  
 [!code-sql[FILESTREAM#FS_InsertZero](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_insertzero)]  
  
### <a name="creating-a-data-file"></a><span data-ttu-id="c51a2-114">데이터 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="c51a2-114">Creating a Data File</span></span>  
 <span data-ttu-id="c51a2-115">다음 예에서는 `INSERT` 를 사용하여 데이터가 들어 있는 파일을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c51a2-115">The following example shows how to use `INSERT` to create a file that contains data.</span></span> <span data-ttu-id="c51a2-116">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 문자열 `Seismic Data` 를 `varbinary(max)` 값으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="c51a2-116">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] converts the string `Seismic Data` to a `varbinary(max)` value.</span></span> <span data-ttu-id="c51a2-117">FILESTREAM은 Windows 파일이 아직 없는 경우 이를 만든 다음 데이터를 데이터 파일에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c51a2-117">FILESTREAM creates the Windows file if it does not already exist.The data is then added to the data file.</span></span>  
  
 [!code-sql[FILESTREAM#FS_InsertData](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_insertdata)]  
  
 <span data-ttu-id="c51a2-118">`Archive``dbo.Records`</span><span class="sxs-lookup"><span data-stu-id="c51a2-118">When you select all data from the `Archive`.`dbo.Records`</span></span> <span data-ttu-id="c51a2-119">테이블의 데이터를 모두 선택하면 결과가 다음 표와 유사하지만</span><span class="sxs-lookup"><span data-stu-id="c51a2-119">table, the results are similar to the results that are shown in the following table.</span></span> <span data-ttu-id="c51a2-120">`Id` 열에는 다른 GUID가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c51a2-120">However, the `Id` column will contain different GUIDs.</span></span>  
  
|<span data-ttu-id="c51a2-121">Id</span><span class="sxs-lookup"><span data-stu-id="c51a2-121">Id</span></span>|<span data-ttu-id="c51a2-122">SerialNumber</span><span class="sxs-lookup"><span data-stu-id="c51a2-122">SerialNumber</span></span>|<span data-ttu-id="c51a2-123">다시 시작</span><span class="sxs-lookup"><span data-stu-id="c51a2-123">Resume</span></span>|  
|--------|------------------|------------|  
|`C871B90F-D25E-47B3-A560-7CC0CA405DAC`|`1`|`NULL`|  
|`F8F5C314-0559-4927-8FA9-1535EE0BDF50`|`2`|`0x`|  
|`7F680840-B7A4-45D4-8CD5-527C44D35B3F`|`3`|`0x536569736D69632044617461`|  
  
##  <a name="updating-filestream-data"></a><a name="upd"></a> <span data-ttu-id="c51a2-124">FILESTREAM 데이터 업데이트</span><span class="sxs-lookup"><span data-stu-id="c51a2-124">Updating FILESTREAM Data</span></span>  
 <span data-ttu-id="c51a2-125">[!INCLUDE[tsql](../../includes/tsql-md.md)] 을 사용하여 파일 시스템 파일의 데이터를 업데이트할 수 있지만 많은 양의 데이터를 파일로 스트리밍해야 하는 경우에는 이렇게 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c51a2-125">You can use [!INCLUDE[tsql](../../includes/tsql-md.md)] to update the data in the file system file; although, you might not want to do this when you have to stream large amounts of data to a file.</span></span>  
  
 <span data-ttu-id="c51a2-126">다음 예에서는 파일 레코드에 있는 임의의 텍스트를 `Xray 1`로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="c51a2-126">The following example replaces any text in the file record with the text `Xray 1`.</span></span>  
  
 [!code-sql[FILESTREAM#FS_UpdateData](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_updatedata)]  
  
##  <a name="deleting-filestream-data"></a><a name="del"></a> <span data-ttu-id="c51a2-127">FILESTREAM 데이터 삭제</span><span class="sxs-lookup"><span data-stu-id="c51a2-127">Deleting FILESTREAM Data</span></span>  
 <span data-ttu-id="c51a2-128">FILESTREAM 필드가 들어 있는 행을 삭제하면 해당 내부 파일 시스템 파일도 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="c51a2-128">When you delete a row that contains a FILESTREAM field, you also delete its underlying file system files.</span></span> <span data-ttu-id="c51a2-129">행과 그 안에 들어 있는 파일을 삭제하는 유일한 방법은 [!INCLUDE[tsql](../../includes/tsql-md.md)] DELETE 문을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c51a2-129">The only way to delete a row, and therefore the file, is to use the [!INCLUDE[tsql](../../includes/tsql-md.md)] DELETE statement.</span></span>  
  
 <span data-ttu-id="c51a2-130">다음 예에서는 행과 관련 파일 시스템 파일을 삭제하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c51a2-130">The following example shows how to delete a row and its associated file system files.</span></span>  
  
 [!code-sql[FILESTREAM#FS_DeleteData](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_deletedata)]  
  
 <span data-ttu-id="c51a2-131">`dbo.Archive` 테이블의 데이터를 모두 선택하면 해당 행이 삭제되고</span><span class="sxs-lookup"><span data-stu-id="c51a2-131">When you select all data from the `dbo.Archive` table, the row is gone.</span></span> <span data-ttu-id="c51a2-132">관련 파일도 더 이상 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c51a2-132">You can no longer use the associated file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c51a2-133">기본 파일은 FILESTREAM 가비지 수집기를 통해 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="c51a2-133">The underlying files are removed by the FILESTREAM garbage collector.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c51a2-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c51a2-134">See Also</span></span>  
 <span data-ttu-id="c51a2-135">[FILESTREAM 사용 및 구성](enable-and-configure-filestream.md) </span><span class="sxs-lookup"><span data-stu-id="c51a2-135">[Enable and Configure FILESTREAM](enable-and-configure-filestream.md) </span></span>  
 [<span data-ttu-id="c51a2-136">FILESTREAM 애플리케이션에서 데이터베이스 작업과의 충돌 방지</span><span class="sxs-lookup"><span data-stu-id="c51a2-136">Avoid Conflicts with Database Operations in FILESTREAM Applications</span></span>](avoid-conflicts-with-database-operations-in-filestream-applications.md)  
  
  
