---
title: 업그레이드 프로세스 중에 모든 파일 그룹이 쓰기 가능한 지 확인 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- filegroups [SQL Server], writeable
- writeable filegroups [SQL Server]
ms.assetid: 2985efc1-4b14-46c3-abbd-a656b159f23c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8146efb876bf97c36c549a2b58d104592df611e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742748"
---
# <a name="verify-all-filegroups-are-writeable-during-the-upgrade-process"></a><span data-ttu-id="9d6c8-102">업그레이드 프로세스 중에 모든 파일 그룹이 쓰기 가능한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6c8-102">Verify all filegroups are writeable during the upgrade process</span></span>
  <span data-ttu-id="9d6c8-103">업그레이드 관리자가 하나 이상의 파일 그룹이 있는 데이터베이스를 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="9d6c8-103">Upgrade Advisor detected a database that has one or more read-only filegroups.</span></span> <span data-ttu-id="9d6c8-104">업그레이드하기 전에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 있는 모든 데이터베이스의 파일 그룹을 READ_WRITE로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6c8-104">All databases in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must have filegroups set to READ_WRITE before upgrading.</span></span>  
  
## <a name="component"></a><span data-ttu-id="9d6c8-105">구성 요소</span><span class="sxs-lookup"><span data-stu-id="9d6c8-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="9d6c8-106">수정 동작</span><span class="sxs-lookup"><span data-stu-id="9d6c8-106">Corrective Action</span></span>  
 <span data-ttu-id="9d6c8-107">ALTER DATABASE를 사용하여 파일을 그룹을 READ_WRITE로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6c8-107">Use ALTER DATABASE to set the filegroup to READ_WRITE.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d6c8-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9d6c8-108">See Also</span></span>  
 <span data-ttu-id="9d6c8-109">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="9d6c8-109">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="9d6c8-110">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="9d6c8-110">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
