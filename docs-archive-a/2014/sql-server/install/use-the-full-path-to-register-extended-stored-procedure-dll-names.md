---
title: 전체 경로를 사용 하 여 확장 저장 프로시저 DLL 이름을 등록 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- registering DLL names
- extended stored procedures [SQL Server], registering
- DLL names [SQL Server]
- full path DLL name registration [SQL Server]
ms.assetid: f648d57c-af32-4c71-9882-47b6766f3c2b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5ec4ef3fc2e0f2c4834ffa7479a00562ae15d07f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732263"
---
# <a name="use-the-full-path-to-register-extended-stored-procedure-dll-names"></a><span data-ttu-id="ae1b5-102">전체 경로를 사용하여 확장 저장 프로시저 DLL 이름을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="ae1b5-102">Use the full path to register extended stored procedure DLL names</span></span>
  <span data-ttu-id="ae1b5-103">DLL 이름에 대한 전체 경로 없이 이전에 등록된 확장 저장 프로시저는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae1b5-103">Extended stored procedures that were previously registered without the full path for the DLL name may not work in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="component"></a><span data-ttu-id="ae1b5-104">구성 요소</span><span class="sxs-lookup"><span data-stu-id="ae1b5-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="ae1b5-105">설명</span><span class="sxs-lookup"><span data-stu-id="ae1b5-105">Description</span></span>  
 <span data-ttu-id="ae1b5-106">업그레이드한 후 DLL 이름에 대한 전체 경로 없이 이전에 등록된 확장 저장 프로시저는 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae1b5-106">Extended stored procedures that were previously registered without the full path for the DLL name may not work after you upgrade.</span></span> <span data-ttu-id="ae1b5-107">이는 업그레이드 중에 이전 BINN 디렉터리가 새 경로에 추가되지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="ae1b5-107">This is because the old BINN directory is not added to the new path during the upgrade process.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="ae1b5-108">에서 확장 저장 프로시저를 찾지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae1b5-108">may not be able to locate the extended stored procedures.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="ae1b5-109">수정 동작</span><span class="sxs-lookup"><span data-stu-id="ae1b5-109">Corrective Action</span></span>  
 <span data-ttu-id="ae1b5-110">업그레이드하기 전에 전체 경로 이름으로 등록되지 않은 각 확장 저장 프로시저에 대해 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ae1b5-110">Before you upgrade, follow these steps for each extended stored procedure that was not registered with a full path name:</span></span>  
  
1.  <span data-ttu-id="ae1b5-111">sp_dropextendedproc을 실행하여 확장 저장 프로시저를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="ae1b5-111">Run sp_dropextendedproc to remove the extended stored procedure.</span></span>  
  
2.  <span data-ttu-id="ae1b5-112">sp_addextendedproc을 실행하여 전체 경로 이름으로 확장 저장 프로시저를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="ae1b5-112">Run sp_addextendedproc to register the extended stored procedure with the full path name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae1b5-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ae1b5-113">See Also</span></span>  
 <span data-ttu-id="ae1b5-114">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="ae1b5-114">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="ae1b5-115">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="ae1b5-115">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
