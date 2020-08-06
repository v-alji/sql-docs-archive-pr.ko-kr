---
title: 읽기 전용 데이터베이스를 업그레이드할 수 없습니다. | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- database cannot be upgraded
ms.assetid: 27964211-ea30-4390-b791-dcf225fb9ae7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ba48ed2bd80961a4949dc13f04fed0637ecc27ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653699"
---
# <a name="read-only-databases-cannot-be-upgraded"></a><span data-ttu-id="5b0ab-102">읽기 전용 데이터베이스를 업그레이드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5b0ab-102">Read-only databases cannot be upgraded</span></span>
  <span data-ttu-id="5b0ab-103">업그레이드 관리자가 이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 있는 일부 데이터베이스를 업그레이드할 수 없음을 감지했습니다.</span><span class="sxs-lookup"><span data-stu-id="5b0ab-103">Upgrade Advisor has determined that some databases on this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot be upgraded.</span></span>  
  
## <a name="component"></a><span data-ttu-id="5b0ab-104">구성 요소</span><span class="sxs-lookup"><span data-stu-id="5b0ab-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="5b0ab-105">Description</span><span class="sxs-lookup"><span data-stu-id="5b0ab-105">Description</span></span>  
 <span data-ttu-id="5b0ab-106">읽기 전용 데이터베이스가 검색되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5b0ab-106">A read-only database has been detected.</span></span> <span data-ttu-id="5b0ab-107">데이터베이스를 업그레이드하려면 설치 프로그램이 데이터베이스에 쓸 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b0ab-107">To upgrade the database, Setup must be able to write to the database.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="5b0ab-108">수정 동작</span><span class="sxs-lookup"><span data-stu-id="5b0ab-108">Corrective Action</span></span>  
 <span data-ttu-id="5b0ab-109">데이터베이스를 사용 하 고 있지 않은 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 엔터프라이즈 관리자, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 또는 ALTER database 문을 사용 하 여 데이터베이스를 읽기/쓰기로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b0ab-109">When no one is using the database, use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Manager, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], or the ALTER DATABASE statement to change the database to read-write.</span></span> <span data-ttu-id="5b0ab-110">다음 문은 데이터베이스를 읽기/쓰기로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="5b0ab-110">The following statement changes the database to read-write.</span></span>  
  
```  
USE master;  
GO  
ALTER DATABASE <database name>  
SET READ_WRITE;  
GO  
```  
  
 <span data-ttu-id="5b0ab-111">ALTER DATABASE 문에 대한 자세한 내용은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 온라인 설명서에서 "ALTER DATABASE([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])" 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5b0ab-111">For more information about the ALTER DATABASE statement, see the "ALTER DATABASE ([!INCLUDE[tsql](../../includes/tsql-md.md)])" topic in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b0ab-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5b0ab-112">See Also</span></span>  
 <span data-ttu-id="5b0ab-113">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="5b0ab-113">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="5b0ab-114">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="5b0ab-114">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
