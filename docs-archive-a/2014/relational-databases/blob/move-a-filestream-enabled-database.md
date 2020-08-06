---
title: FILESTREAM 사용 데이터베이스 이동 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], moving a FILESTREAM-enabled database
ms.assetid: dd4d270d-9283-431a-aa6b-e571fced1893
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 79740ee86a89566113650865e3fd6ec54c7cb918
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728371"
---
# <a name="move-a-filestream-enabled-database"></a><span data-ttu-id="2c9cd-102">FILESTREAM 사용 데이터베이스 이동</span><span class="sxs-lookup"><span data-stu-id="2c9cd-102">Move a FILESTREAM-Enabled Database</span></span>
  <span data-ttu-id="2c9cd-103">이 항목에서는 FILESTREAM 사용 데이터베이스를 이동하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2c9cd-103">This topic shows how to move a FILESTREAM-enabled database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2c9cd-104">이 항목의 예제에는 [FILESTREAM 사용 데이터베이스 만들기](create-a-filestream-enabled-database.md)에서 만들어진 Archive 데이터베이스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2c9cd-104">The examples in this topic require the Archive database that is created in [Create a FILESTREAM-Enabled Database](create-a-filestream-enabled-database.md).</span></span>  
  
### <a name="to-move-a-filestream-enabled-database"></a><span data-ttu-id="2c9cd-105">FILESTREAM 사용 데이터베이스를 이동하려면</span><span class="sxs-lookup"><span data-stu-id="2c9cd-105">To move a FILESTREAM-enabled database</span></span>  
  
1.  <span data-ttu-id="2c9cd-106">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 **새 쿼리** 를 클릭하여 쿼리 편집기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2c9cd-106">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], click **New Query** to open the Query Editor.</span></span>  
  
2.  <span data-ttu-id="2c9cd-107">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트를 쿼리 편집기에 복사한 다음 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c9cd-107">Copy the following [!INCLUDE[tsql](../../includes/tsql-md.md)] script into the Query Editor, and then click **Execute**.</span></span> <span data-ttu-id="2c9cd-108">이 스크립트는 FILESTREAM 데이터베이스에서 사용하는 실제 데이터베이스 파일의 위치를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2c9cd-108">This script displays the location of the physical database files that the FILESTREAM database uses.</span></span>  
  
    ```sql  
    USE Archive  
    GO  
    SELECT type_desc, name, physical_name from sys.database_files  
    ```  
  
3.  <span data-ttu-id="2c9cd-109">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트를 쿼리 편집기에 복사한 다음 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c9cd-109">Copy the following [!INCLUDE[tsql](../../includes/tsql-md.md)] script into the Query Editor, and then click **Execute**.</span></span> <span data-ttu-id="2c9cd-110">이 코드는 `Archive` 데이터베이스를 오프라인 상태로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2c9cd-110">This code takes the `Archive` database offline.</span></span>  
  
    ```sql  
    USE master  
    EXEC sp_detach_db Archive  
    GO  
    ```  
  
4.  <span data-ttu-id="2c9cd-111">`C:\moved_location`이라는 폴더를 만든 다음 2단계에 나와 있는 파일과 폴더를 이 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="2c9cd-111">Create the folder `C:\moved_location`, and then move the files and folders that are listed in step 2 into it.</span></span>  
  
5.  <span data-ttu-id="2c9cd-112">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트를 쿼리 편집기에 복사한 다음 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c9cd-112">Copy the following [!INCLUDE[tsql](../../includes/tsql-md.md)] script into the Query Editor, and then click **Execute**.</span></span> <span data-ttu-id="2c9cd-113">이 스크립트는 `Archive` 데이터베이스를 온라인 상태로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2c9cd-113">This script sets the `Archive` database online.</span></span>  
  
    ```sql  
    CREATE DATABASE Archive ON  
    PRIMARY ( NAME = Arch1,  
        FILENAME = 'c:\moved_location\archdat1.mdf'),  
    FILEGROUP FileStreamGroup1 CONTAINS FILESTREAM( NAME = Arch3,  
        FILENAME = 'c:\moved_location\filestream1')  
    LOG ON  ( NAME = Archlog1,  
        FILENAME = 'c:\moved_location\archlog1.ldf')  
    FOR ATTACH  
    GO  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2c9cd-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2c9cd-114">See Also</span></span>  
 [<span data-ttu-id="2c9cd-115">sp_detach_db&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2c9cd-115">sp_detach_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql)  
  
  
