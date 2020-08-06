---
title: Resource 데이터베이스 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- system objects [SQL Server]
- read-only databases
- mssqlsystemresource.mdf file
- Resource database [SQL Server]
ms.assetid: d592b2b4-bc36-4eb9-9385-8fe4dff0dced
author: stevestein
ms.author: sstein
ms.openlocfilehash: cca2f9e1ff6069a608beb1df1880b37e15f4e869
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650091"
---
# <a name="resource-database"></a><span data-ttu-id="9c497-102">Resource 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="9c497-102">Resource Database</span></span>
  <span data-ttu-id="9c497-103">Resource 데이터베이스는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 포함된 시스템 개체가 모두 들어 있는 읽기 전용 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="9c497-103">The Resource database is a read-only database that contains all the system objects that are included with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9c497-104">시스템 개체(예: sys.objects)는 실제로는 Resource 데이터베이스에 저장되지만 논리적으로는 모든 데이터베이스의 sys 스키마에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="9c497-104">system objects, such as sys.objects, are physically persisted in the Resource database, but they logically appear in the sys schema of every database.</span></span> <span data-ttu-id="9c497-105">Resource 데이터베이스에는 사용자 데이터 또는 사용자 메타데이터가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9c497-105">The Resource database does not contain user data or user metadata.</span></span>  
  
 <span data-ttu-id="9c497-106">Resource 데이터베이스를 새 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로 빠르고 쉽게 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="9c497-106">The Resource database makes upgrading to a new version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] an easier and faster procedure.</span></span> <span data-ttu-id="9c497-107">이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 업그레이드를 수행하려면 시스템 개체를 삭제한 다음 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c497-107">In earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], upgrading required dropping and creating system objects.</span></span> <span data-ttu-id="9c497-108">이제 Resource 데이터베이스 파일에 모든 시스템 개체가 들어 있으므로 단일 Resource 데이터베이스 파일을 로컬 서버에 복사하면 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c497-108">Because the Resource database file contains all system objects, an upgrade is now accomplished simply by copying the single Resource database file to the local server.</span></span>  
  
## <a name="physical-properties-of-resource"></a><span data-ttu-id="9c497-109">Resource의 물리적 속성</span><span class="sxs-lookup"><span data-stu-id="9c497-109">Physical Properties of Resource</span></span>  
 <span data-ttu-id="9c497-110">Resource 데이터베이스의 물리적 파일 이름은 mssqlsystemresource.mdf 및 mssqlsystemresource.ldf입니다.</span><span class="sxs-lookup"><span data-stu-id="9c497-110">The physical file names of the Resource database are mssqlsystemresource.mdf and mssqlsystemresource.ldf.</span></span> <span data-ttu-id="9c497-111">이러한 파일은 \<*drive*>:\Program Files\Microsoft SQL Server\MSSQL\<version>.\<*instance_name*>\MSSQL\Binn\에 있으며 이동하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c497-111">These files are located in \<*drive*>:\Program Files\Microsoft SQL Server\MSSQL\<version>.\<*instance_name*>\MSSQL\Binn\ and should not be moved.</span></span> <span data-ttu-id="9c497-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 각 인스턴스에는 관련된 mssqlsystemresource.mdf 파일이 하나만 있으며 인스턴스에서 이 파일을 공유하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9c497-112">Each instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has one and only one associated mssqlsystemresource.mdf file, and instances do not share this file.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="9c497-113">업그레이드와 서비스 팩은 BINN 폴더에 설치되는 새 리소스 데이터베이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9c497-113">Upgrades and service packs sometimes provide a new resource database which is installed to the BINN folder.</span></span> <span data-ttu-id="9c497-114">리소스 데이터베이스의 위치 변경은 지원되지 않거나 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9c497-114">Changing the location of the resource database is not supported or recommended.</span></span>  
  
## <a name="backing-up-and-restoring-the-resource-database"></a><span data-ttu-id="9c497-115">Resource 데이터베이스 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="9c497-115">Backing Up and Restoring the Resource Database</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9c497-116">에서는 Resource 데이터베이스를 백업할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9c497-116">cannot back up the Resource database.</span></span> <span data-ttu-id="9c497-117">mssqlsystemresource.mdf 파일을 데이터베이스 파일이 아닌 이진(.EXE) 파일인 것처럼 처리하여 자체 파일 기반 또는 디스크 기반 백업을 수행할 수 있지만 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 백업을 복원할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9c497-117">You can perform your own file-based or a disk-based backup by treating the mssqlsystemresource.mdf file as if it were a binary (.EXE) file, rather than a database file, but you cannot use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to restore your backups.</span></span> <span data-ttu-id="9c497-118">수동으로만 mssqlsystemresource.mdf 백업 복사본을 복원할 수 있으며 현재 Resource 데이터베이스를 오래된 버전이나 안전하지 않은 버전으로 덮어쓰지 않도록 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c497-118">Restoring a backup copy of mssqlsystemresource.mdf can only be done manually, and you must be careful not to overwrite the current Resource database with an out-of-date or potentially insecure version.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9c497-119">mssqlsystemresource.mdf 백업을 복원한 후에 후속 업데이트를 다시 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c497-119">After restoring a backup of mssqlsystemresource.mdf, you must reapply any subsequent updates.</span></span>  
  
## <a name="accessing-the-resource-database"></a><span data-ttu-id="9c497-120">Resource 데이터베이스 액세스</span><span class="sxs-lookup"><span data-stu-id="9c497-120">Accessing the Resource Database</span></span>  
 <span data-ttu-id="9c497-121">Resource 데이터베이스는 Microsoft CSS(고객 지원 서비스) 전문가가 직접 수정하거나 전문가의 지도를 받아 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c497-121">The Resource database should only be modified by or at the direction of a Microsoft Customer Support Services (CSS) specialist.</span></span> <span data-ttu-id="9c497-122">Resource 데이터베이스의 ID는 항상 32767입니다.</span><span class="sxs-lookup"><span data-stu-id="9c497-122">The ID of the Resource database is always 32767.</span></span> <span data-ttu-id="9c497-123">Resource 데이터베이스와 관련된 다른 중요한 값은 버전 번호 및 데이터베이스가 마지막으로 업데이트된 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="9c497-123">Other important values associated with the Resource database are the version number and the last time that the database was updated.</span></span>  
  
 <span data-ttu-id="9c497-124">Resource **데이터베이스의 버전 번호를** **확인하려면 다음 문을 사용합니다**.</span><span class="sxs-lookup"><span data-stu-id="9c497-124">**To determine the version number of the** Resource **database, use**:</span></span>  
  
```  
SELECT SERVERPROPERTY('ResourceVersion');  
GO  
```  
  
 <span data-ttu-id="9c497-125">Resource **데이터베이스가 마지막으로 업데이트된** **시기를 확인하려면 다음 문을 사용합니다**.</span><span class="sxs-lookup"><span data-stu-id="9c497-125">**To determine when the** Resource **database was last updated, use**:</span></span>  
  
```  
SELECT SERVERPROPERTY('ResourceLastUpdateDateTime');  
GO  
```  
  
 <span data-ttu-id="9c497-126">**시스템 개체의 SQL 정의에 액세스하려면 OBJECT_DEFINITION 함수를 사용합니다.**</span><span class="sxs-lookup"><span data-stu-id="9c497-126">**To access SQL definitions of system objects, use the OBJECT_DEFINITION function:**</span></span>  
  
```  
SELECT OBJECT_DEFINITION(OBJECT_ID('sys.objects'));  
GO  
```  
  
## <a name="related-content"></a><span data-ttu-id="9c497-127">관련 내용</span><span class="sxs-lookup"><span data-stu-id="9c497-127">Related Content</span></span>  
 [<span data-ttu-id="9c497-128">시스템 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="9c497-128">System Databases</span></span>](system-databases.md)  
  
 [<span data-ttu-id="9c497-129">데이터베이스 관리자를 위한 진단 연결</span><span class="sxs-lookup"><span data-stu-id="9c497-129">Diagnostic Connection for Database Administrators</span></span>](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)  
  
 [<span data-ttu-id="9c497-130">OBJECT_DEFINITION&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9c497-130">OBJECT_DEFINITION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/object-definition-transact-sql)  
  
 [<span data-ttu-id="9c497-131">SERVERPROPERTY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9c497-131">SERVERPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/serverproperty-transact-sql)  
  
 [<span data-ttu-id="9c497-132">단일 사용자 모드로 SQL Server 시작</span><span class="sxs-lookup"><span data-stu-id="9c497-132">Start SQL Server in Single-User Mode</span></span>](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)  
  
  
