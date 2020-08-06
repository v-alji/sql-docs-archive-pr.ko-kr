---
title: 업그레이드 프로세스 중에 데이터베이스 파일이 압축 된 드라이브에 없는지 확인 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- compressed drives [SQL Server]
ms.assetid: 63be6853-c54a-42b2-ae1a-db2175f1d28e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9c04f7890ba8d8efe64afaf11b922af156c5de46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646814"
---
# <a name="verify-that-no-database-files-are-on-compressed-drives-during-the-upgrade-process"></a><span data-ttu-id="7c8e6-102">업그레이드 프로세스 중에 데이터베이스 파일이 압축된 드라이브에 없는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7c8e6-102">Verify that no database files are on compressed drives during the upgrade process</span></span>
  <span data-ttu-id="7c8e6-103">업그레이드 관리자가 압축된 드라이브에서 데이터베이스 파일을 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="7c8e6-103">Upgrade Advisor detected database files on a compressed drive.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="7c8e6-104">은 압축된 드라이브에서 데이터베이스를 만들거나 업그레이드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7c8e6-104">cannot create or upgrade databases on compressed drives.</span></span>  
  
## <a name="component"></a><span data-ttu-id="7c8e6-105">구성 요소</span><span class="sxs-lookup"><span data-stu-id="7c8e6-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="7c8e6-106">수정 동작</span><span class="sxs-lookup"><span data-stu-id="7c8e6-106">Corrective Action</span></span>  
 <span data-ttu-id="7c8e6-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]을 설치할 때 시스템 데이터베이스에 대해 압축되지 않은 드라이브를 선택하고 업그레이드할 데이터베이스가 압축된 드라이브에 없는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7c8e6-107">When you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], select an uncompressed drive for system databases and verify that databases to be upgraded are not on compressed drives.</span></span> <span data-ttu-id="7c8e6-108">데이터베이스를 업그레이드한 후에는 NTFS 압축 파일 시스템에 읽기 전용 데이터베이스 및 읽기 전용 보조 파일 그룹을 보관할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c8e6-108">However, note that after the database has been upgraded, you can put read-only databases and read-only secondary filegroups on an NTFS compressed file system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c8e6-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7c8e6-109">See Also</span></span>  
 <span data-ttu-id="7c8e6-110">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="7c8e6-110">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="7c8e6-111">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="7c8e6-111">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
