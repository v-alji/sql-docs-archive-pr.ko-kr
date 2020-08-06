---
title: OPENROWSET 대량 행 집합 공급자 (SQL Server)를 사용 하 여 대용량 개체 데이터 대량 가져오기 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- SINGLE_NCLOB option
- bulk rowset providers [SQL Server]
- bulk importing [SQL Server], data formats
- OPENROWSET function, bulk importing large data
- SINGLE_CLOB option
- data formats [SQL Server], large-object data
- large data, bulk imports
- SINGLE_BLOB option
ms.assetid: 171cdd5c-1e47-4bd7-b99a-4f0fd4e10526
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0f43aa2fa5e7f7ef0b2c8f1f6e5e6ff28e02f9f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649993"
---
# <a name="bulk-import-large-object-data-by-using-the-openrowset-bulk-rowset-provider-sql-server"></a><span data-ttu-id="0babb-102">OPENROWSET 대량 행 집합 공급자를 사용하여 큰 개체 데이터 대량 가져오기(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0babb-102">Bulk Import Large-Object Data by using the OPENROWSET Bulk Rowset Provider (SQL Server)</span></span>
  <span data-ttu-id="0babb-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OPENROWSET 대량 행 집합 공급자를 사용하여 데이터 파일을 큰 개체 데이터로 대량으로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0babb-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OPENROWSET Bulk Rowset Provider enables you to bulk import a data file as large-object data.</span></span>  
  
 <span data-ttu-id="0babb-104">OPENROWSET 대량 행 집합 공급자에서 지원되는 큰 개체 데이터 형식은 **varbinary**(max) 또는 **image**, **varchar**(max) 또는 **text**, **nvarchar**(max) 또는 **ntext**입니다.</span><span class="sxs-lookup"><span data-stu-id="0babb-104">The large-object data types supported by OPENROWSET Bulk Rowset Provider are **varbinary**(max) or **image**, **varchar**(max) or **text**, and **nvarchar**(max) or **ntext**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0babb-105">**image**, **text** 및 **ntext** 데이터 형식은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0babb-105">The **image**, **text** and **ntext** data types are deprecated.</span></span>  
  
 <span data-ttu-id="0babb-106">OPENROWSET BULK 절은 데이터 파일의 내용을 단일 행/단일 열로 된 행 집합으로 가져올 수 있는 3개의 옵션을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="0babb-106">The OPENROWSET BULK clause supports three options for importing the contents of a data file as a single-row, single-column rowset.</span></span> <span data-ttu-id="0babb-107">서식 파일을 사용하는 대신 이 큰 개체 옵션 중 하나를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0babb-107">You can specify one of these large-object options instead of using a format file.</span></span> <span data-ttu-id="0babb-108">옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0babb-108">These options are as follows:</span></span>  
  
 <span data-ttu-id="0babb-109">SINGLE_BLOB</span><span class="sxs-lookup"><span data-stu-id="0babb-109">SINGLE_BLOB</span></span>  
 <span data-ttu-id="0babb-110">*data_file* 의 내용을 단일 행으로 읽은 후 **varbinary(max)** 형식의 단일 열로 된 행 집합으로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0babb-110">Reads the contents of *data_file* as a single-row, returns the contents as a single-column rowset of type **varbinary(max)**.</span></span>  
  
 <span data-ttu-id="0babb-111">SINGLE_CLOB</span><span class="sxs-lookup"><span data-stu-id="0babb-111">SINGLE_CLOB</span></span>  
 <span data-ttu-id="0babb-112">지정한 데이터 파일의 내용을 문자로 읽은 후 텍스트나 **Word 문서와 같은 현재 데이터베이스의 데이터 정렬을 사용하여**varchar(max) [!INCLUDE[msCoName](../../includes/msconame-md.md)] 형식의 단일 행/열로 된 행 집합으로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0babb-112">Reads the contents of the specified data file as characters, returns the contents as a single-row, single-column rowset of type **varchar(max)**, using the collation of the current database; such as a text or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word document.</span></span>  
  
 <span data-ttu-id="0babb-113">SINGLE_NCLOB</span><span class="sxs-lookup"><span data-stu-id="0babb-113">SINGLE_NCLOB</span></span>  
 <span data-ttu-id="0babb-114">지정한 데이터 파일의 내용을 유니코드로 읽은 후 현재 데이터베이스의 데이터 정렬을 사용하여 **nvarchar(max)** 형식의 단일 행/열로 된 행 집합으로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0babb-114">Reads the contents of the specified data file as Unicode, returns the contents as a single-row, single-column rowset of type **nvarchar(max)**, using the collation of the current database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0babb-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0babb-115">See Also</span></span>  
 <span data-ttu-id="0babb-116">[BULK INSERT 또는 OPENROWSET&#40;BULK...&#41;를 사용하여 데이터 대량 가져오기&#40;SQL Server&#41;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0babb-116">[Import Bulk Data by Using BULK INSERT or OPENROWSET&#40;BULK...&#41; &#40;SQL Server&#41;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md) </span></span>  
 <span data-ttu-id="0babb-117">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0babb-117">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="0babb-118">[OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0babb-118">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="0babb-119">[대량 가져오기 수행 중 Null 유지 또는 기본값 사용&#40;SQL Server&#41;](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0babb-119">[Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md) </span></span>  
 <span data-ttu-id="0babb-120">[bcp 유틸리티](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="0babb-120">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 [<span data-ttu-id="0babb-121">BULK INSERT&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0babb-121">BULK INSERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/bulk-insert-transact-sql)  
  
  
