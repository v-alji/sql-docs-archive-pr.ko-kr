---
title: 주의 대상 페이지가 있는 데이터베이스의 무결성 검사 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3b1ec9fe-f6c5-46f7-aa63-6e671be1572d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3cc1f87917c78f34ec7722fa21a1a67fda40a8c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728220"
---
# <a name="check-integrity-of-database-with-suspect-pages"></a><span data-ttu-id="1afa7-102">주의 대상 페이지가 있는 데이터베이스의 무결성 검사</span><span class="sxs-lookup"><span data-stu-id="1afa7-102">Check Integrity of Database with Suspect Pages</span></span>
  <span data-ttu-id="1afa7-103">이 규칙은 데이터베이스 상태가 주의 대상으로 설정된 사용자 데이터베이스를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="1afa7-103">This rule checks for user databases that have the database status set to suspect.</span></span> <span data-ttu-id="1afa7-104">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 이 824 오류가 포함된 데이터베이스 페이지를 읽는 경우 페이지는 주의 대상 페이지로 간주되고 페이지 ID는 msdb의 suspect_pages 테이블에 기록되며 해당 페이지를 포함하는 데이터베이스는 주의 대상으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="1afa7-104">When the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] reads a database page that contains an 824 error, the page is considered suspect, its page ID is recorded in the suspect_pages table in msdb, and the database that contains the page is set to suspect.</span></span>  
  
 <span data-ttu-id="1afa7-105">824 오류는 읽기 작업 중에 논리적 일관성 오류가 검색되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1afa7-105">Error 824 indicates that a logical consistency error was detected during a read operation.</span></span> <span data-ttu-id="1afa7-106">이 오류는 잘못된 I/O 하위 시스템 구성 요소로 인한 데이터 손상을 나타내는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="1afa7-106">This error frequently indicates data corruption caused by a faulty I/O subsystem component.</span></span> <span data-ttu-id="1afa7-107">이는 데이터베이스 무결성을 위협하는 심각한 오류 상태이며 즉시 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1afa7-107">This is a severe error condition that threatens database integrity and must be corrected immediately.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="1afa7-108">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="1afa7-108">Best Practices Recommendations</span></span>  
  
-   <span data-ttu-id="1afa7-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그에서 이 데이터베이스에 대한 824 오류의 세부 정보를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="1afa7-109">Review the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log for the details of the 824 error for this database.</span></span>  
  
-   <span data-ttu-id="1afa7-110">전체 데이터베이스 일관성 검사([DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql))를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="1afa7-110">Complete a full database consistency check ([DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)).</span></span>  
  
-   <span data-ttu-id="1afa7-111">[MSSQLSERVER_824](https://go.microsoft.com/fwlink/?LinkId=81397)에 정의된 사용자 동작을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="1afa7-111">Implement the user actions that are defined in [MSSQLSERVER_824](https://go.microsoft.com/fwlink/?LinkId=81397).</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="1afa7-112">참조 항목</span><span class="sxs-lookup"><span data-stu-id="1afa7-112">For More Information</span></span>  
 [<span data-ttu-id="1afa7-113">suspect_pages 테이블 관리&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1afa7-113">Manage the suspect_pages Table &#40;SQL Server&#41;</span></span>](../backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
