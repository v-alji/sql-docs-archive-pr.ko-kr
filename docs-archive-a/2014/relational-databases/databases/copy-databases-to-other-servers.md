---
title: 데이터베이스를 다른 서버로 복사 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- servers [SQL Server], copying databases between
- bulk exporting [SQL Server], between servers
- database copying [SQL Server]
- migrating databases [SQL Server]
- moving databases
- copying databases
- bulk importing [SQL Server], between servers
ms.assetid: 978406d6-a3c8-4902-b1f4-4ced75234be5
author: stevestein
ms.author: sstein
ms.openlocfilehash: bcde6185f25129596b4be7a150d4ee230c54c1a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731720"
---
# <a name="copy-databases-to-other-servers"></a><span data-ttu-id="6342c-102">데이터베이스를 다른 서버로 복사</span><span class="sxs-lookup"><span data-stu-id="6342c-102">Copy Databases to Other Servers</span></span>
  <span data-ttu-id="6342c-103">데이터베이스를 한 컴퓨터에서 다른 컴퓨터로 복사하는 기능은 경우에 따라 유용하게 사용됩니다(예: 테스트, 일관성 검사, 소프트웨어 개발, 보고서 실행, 미러 데이터베이스 만들기 또는 원격 분기 작업에서 사용할 수 있도록 데이터베이스 설정 등).</span><span class="sxs-lookup"><span data-stu-id="6342c-103">It is sometimes useful to copy a database from one computer to another, whether for testing, checking consistency, developing software, running reports, creating a mirror database, or, possibly, to make the database available to remote-branch operations.</span></span>  
  
 <span data-ttu-id="6342c-104">다음과 같은 여러 방법으로 데이터베이스를 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6342c-104">There are several ways to copy a database:</span></span>  
  
-   <span data-ttu-id="6342c-105">데이터베이스 복사 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="6342c-105">Using the Copy Database Wizard</span></span>  
  
     <span data-ttu-id="6342c-106">데이터베이스 복사 마법사를 사용하여 서버 간에 데이터베이스를 복사 또는 이동하거나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스를 이후 버전으로 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6342c-106">You can use the Copy Database Wizard to copy or move databases between servers or to upgrade a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database to a later version.</span></span> <span data-ttu-id="6342c-107">자세한 내용은 [Use the Copy Database Wizard](use-the-copy-database-wizard.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6342c-107">For more information, see [Use the Copy Database Wizard](use-the-copy-database-wizard.md).</span></span>  
  
-   <span data-ttu-id="6342c-108">데이터베이스 백업 복원</span><span class="sxs-lookup"><span data-stu-id="6342c-108">Restoring a database backup</span></span>  
  
     <span data-ttu-id="6342c-109">전체 데이터베이스를 복사하려면 BACKUP 및 RESTORE [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6342c-109">To copy an entire database, you can use the BACKUP and RESTORE [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="6342c-110">일반적으로 데이터베이스의 전체 백업 복원은 여러 가지 이유로 데이터베이스를 한 컴퓨터에서 다른 컴퓨터로 복사하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6342c-110">Typically, restoring a full backup of a database is used to copy the database from one computer to another for a variety of reasons.</span></span> <span data-ttu-id="6342c-111">백업 및 복원을 사용하여 데이터베이스를 복사하는 방법은 [백업 및 복원으로 데이터베이스 복사](copy-databases-with-backup-and-restore.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6342c-111">For information on using backup and restore to copy a database, see [Copy Databases with Backup and Restore](copy-databases-with-backup-and-restore.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6342c-112">데이터베이스 미러링에 사용할 미러 데이터베이스를 설정하려면 RESTORE DATABASE *<database_name>* WITH NORECOVERY를 사용하여 데이터베이스를 미러 서버로 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6342c-112">To set up a mirror database for database mirroring, you must restore the database onto the mirror server by using RESTORE DATABASE *<database_name>* WITH NORECOVERY.</span></span> <span data-ttu-id="6342c-113">자세한 내용은 [미러 데이터베이스의 미러링 준비&#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6342c-113">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
-   <span data-ttu-id="6342c-114">스크립트 생성 마법사를 사용하여 데이터베이스 게시</span><span class="sxs-lookup"><span data-stu-id="6342c-114">Using the Generate Scripts Wizard to publish databases</span></span>  
  
     <span data-ttu-id="6342c-115">스크립트 생성 마법사를 사용하여 데이터베이스를 로컬 컴퓨터에서 웹 호스팅 공급자로 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6342c-115">You can use the Generate Scripts Wizard to transfer a database from a local computer to a Web hosting provider.</span></span> <span data-ttu-id="6342c-116">자세한 내용은 [스크립트 생성 및 게시 마법사](../scripting/generate-and-publish-scripts-wizard.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6342c-116">For more information, see [Generate and Publish Scripts Wizard](../scripting/generate-and-publish-scripts-wizard.md).</span></span>  
  
  
