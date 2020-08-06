---
title: 데이터베이스 파일 이동 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- disaster recovery [SQL Server], moving database files
- files [SQL Server], moving
- data files [SQL Server], moving
- file moving [SQL Server]
- moving full-text catalogs
- moving databases
- full-text catalogs [SQL Server], moving
- moving database files
- scheduled disk maintenance [SQL Server]
- moving files
- relocating database files
- planned database relocations [SQL Server]
- databases [SQL Server], moving
ms.assetid: 89f01b10-5fae-4ed8-b0fb-a4b9f540fd28
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5491f3c4dfd47cac4047d0409c78001be80d6f13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736369"
---
# <a name="move-database-files"></a><span data-ttu-id="3159e-102">데이터베이스 파일 이동</span><span class="sxs-lookup"><span data-stu-id="3159e-102">Move Database Files</span></span>
  <span data-ttu-id="3159e-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) 문의 FILENAME 절에 새 파일 위치를 지정하여 시스템 및 사용자 데이터베이스를 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3159e-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can move system and user databases by specifying the new file location in the FILENAME clause of the [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement.</span></span> <span data-ttu-id="3159e-104">데이터, 로그 및 전체 텍스트 카탈로그 파일도 이런 식으로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3159e-104">Data, log, and full-text catalog files can be moved in this way.</span></span> <span data-ttu-id="3159e-105">이 방법은 다음과 같은 경우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="3159e-105">This may be useful in the following situations:</span></span>  
  
-   <span data-ttu-id="3159e-106">오류 복구.</span><span class="sxs-lookup"><span data-stu-id="3159e-106">Failure recovery.</span></span> <span data-ttu-id="3159e-107">하드웨어 오류로 인해 데이터베이스가 주의 대상 모드에 있거나 종료된 경우를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3159e-107">For example, the database is in suspect mode or has shut down, because of a hardware failure.</span></span>  
  
-   <span data-ttu-id="3159e-108">계획된 재배치</span><span class="sxs-lookup"><span data-stu-id="3159e-108">Planned relocation.</span></span>  
  
-   <span data-ttu-id="3159e-109">예약된 디스크 유지 관리를 위한 재배치</span><span class="sxs-lookup"><span data-stu-id="3159e-109">Relocation for scheduled disk maintenance.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3159e-110">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="3159e-110">In This Section</span></span>  
  
|<span data-ttu-id="3159e-111">항목</span><span class="sxs-lookup"><span data-stu-id="3159e-111">Topic</span></span>|<span data-ttu-id="3159e-112">Description</span><span class="sxs-lookup"><span data-stu-id="3159e-112">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="3159e-113">사용자 데이터베이스 이동</span><span class="sxs-lookup"><span data-stu-id="3159e-113">Move User Databases</span></span>](move-user-databases.md)|<span data-ttu-id="3159e-114">사용자 데이터베이스 파일과 전체 텍스트 카탈로그 파일을 새 위치로 이동하는 절차에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3159e-114">Describes the procedures for moving user database files and full-text catalog files to a new location.</span></span>|  
|[<span data-ttu-id="3159e-115">시스템 데이터베이스 이동</span><span class="sxs-lookup"><span data-stu-id="3159e-115">Move System Databases</span></span>](system-databases.md)|<span data-ttu-id="3159e-116">시스템 데이터베이스 파일을 새 위치로 이동하는 절차에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3159e-116">Describes the procedures for moving system database files to a new location.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3159e-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3159e-117">See Also</span></span>  
 <span data-ttu-id="3159e-118">[ALTER DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3159e-118">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="3159e-119">[CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3159e-119">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 [<span data-ttu-id="3159e-120">데이터베이스 분리 및 연결&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3159e-120">Database Detach and Attach &#40;SQL Server&#41;</span></span>](database-detach-and-attach-sql-server.md)  
  
  
