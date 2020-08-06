---
title: FILESTREAM 데이터 저장용 테이블 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], table storage
ms.assetid: 029c3059-5c83-43e2-a859-9027031b7de1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 484d7b58ce949df79dc7e17ee4dc7307b70c0154
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731728"
---
# <a name="create-a-table-for-storing-filestream-data"></a><span data-ttu-id="56cf7-102">FILESTREAM 데이터 저장용 테이블 만들기</span><span class="sxs-lookup"><span data-stu-id="56cf7-102">Create a Table for Storing FILESTREAM Data</span></span>
  <span data-ttu-id="56cf7-103">이 항목에서는 FILESTREAM 데이터 저장용 테이블을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="56cf7-103">This topic shows how to create a table for storing FILESTREAM data.</span></span>  
  
 <span data-ttu-id="56cf7-104">데이터베이스에 FILESTREAM 파일 그룹이 있으면 FILESTREAM 데이터를 저장하는 테이블을 만들거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56cf7-104">When the database has a FILESTREAM filegroup, you can create or modify tables to store FILESTREAM data.</span></span> <span data-ttu-id="56cf7-105">FILESTREAM 데이터를 포함하는 열을 지정하려면 `varbinary(max)` 열을 만들고 FILESTREAM 특성을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="56cf7-105">To specify that a column contains FILESTREAM data, you create a `varbinary(max)` column and add the FILESTREAM attribute.</span></span>  
  
### <a name="to-create-a-table-to-store-filestream-data"></a><span data-ttu-id="56cf7-106">FILESTREAM 데이터를 저장할 테이블을 만들려면</span><span class="sxs-lookup"><span data-stu-id="56cf7-106">To create a table to store FILESTREAM data</span></span>  
  
1.  <span data-ttu-id="56cf7-107">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 **새 쿼리** 를 클릭하여 쿼리 편집기를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="56cf7-107">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], click **New Query** to display the Query Editor.</span></span>  
  
2.  <span data-ttu-id="56cf7-108">다음 예에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드를 복사하여 쿼리 편집기에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="56cf7-108">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] code from the following example into the Query Editor.</span></span> <span data-ttu-id="56cf7-109">이 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드는 Records라는 FILESTREAM 사용 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="56cf7-109">This [!INCLUDE[tsql](../../includes/tsql-md.md)] code creates a FILESTREAM-enabled table called Records.</span></span>  
  
3.  <span data-ttu-id="56cf7-110">테이블을 만들려면 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="56cf7-110">To create the table, click **Execute**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56cf7-111">예제</span><span class="sxs-lookup"><span data-stu-id="56cf7-111">Example</span></span>  
 <span data-ttu-id="56cf7-112">다음 코드 예에서는 `Records`라는 테이블을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="56cf7-112">The following code example shows how to create a table that is named `Records`.</span></span> <span data-ttu-id="56cf7-113">`Id` 열은 `ROWGUIDCOL` 열로서 Win32 API에서 FILESTREAM 데이터를 사용하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="56cf7-113">The `Id` column is a `ROWGUIDCOL` column and is required to use FILESTREAM data with Win32 APIs.</span></span> <span data-ttu-id="56cf7-114">`SerialNumber` 열은 `UNIQUE INTEGER`입니다.</span><span class="sxs-lookup"><span data-stu-id="56cf7-114">The `SerialNumber` column is a `UNIQUE INTEGER`.</span></span> <span data-ttu-id="56cf7-115">`Chart` 열은 `FILESTREAM` 열로서 파일 시스템에 `Chart` 를 저장하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="56cf7-115">The `Chart` column is a `FILESTREAM` column and is used to store the `Chart` in the file system.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="56cf7-116">이 예제에서는 [FILESTREAM 사용 데이터베이스 만들기](create-a-filestream-enabled-database.md)에서 만든 Archive 데이터베이스를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="56cf7-116">This example refers to the Archive database that is created in [Create a FILESTREAM-Enabled Database](create-a-filestream-enabled-database.md).</span></span>  
  
 [!code-sql[FILESTREAM#FS_CreateTable](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_createtable)]  
  
## <a name="see-also"></a><span data-ttu-id="56cf7-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="56cf7-117">See Also</span></span>  
 <span data-ttu-id="56cf7-118">[CREATE TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="56cf7-118">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span></span>  
 [<span data-ttu-id="56cf7-119">ALTER TABLE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="56cf7-119">ALTER TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-table-transact-sql)  
  
  
