---
title: 고정 서버 역할 이름과 일치 하는 로그인 이름 바꾸기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- user-defined login names [SQL Server]
- fixed server roles [SQL Server]
- renamed logins [SQL Server]
- logins [SQL Server], names
ms.assetid: 10a1d77c-3153-474f-a6a0-969556794467
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 296ae4d4051e79e3c5d3bc158ef3e87c9164ecd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735868"
---
# <a name="rename-logins-matching-fixed-server-role-names"></a><span data-ttu-id="d2095-102">고정 서버 역할 이름과 일치하는 로그인 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="d2095-102">Rename logins matching fixed server role names</span></span>
  <span data-ttu-id="d2095-103">업그레이드 관리자가 고정 서버 역할 이름과 일치하는 하나 이상의 사용자 정의 로그인 이름을 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="d2095-103">Upgrade Advisor detected one or more user-defined login names that match the names of fixed server roles.</span></span> <span data-ttu-id="d2095-104">고정 서버 역할 이름은 예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2095-104">Fixed server role names are reserved.</span></span> <span data-ttu-id="d2095-105">업그레이드하기 전에 로그인 이름을 바꾸십시오</span><span class="sxs-lookup"><span data-stu-id="d2095-105">Rename the login before you upgrade.</span></span>  
  
## <a name="component"></a><span data-ttu-id="d2095-106">구성 요소</span><span class="sxs-lookup"><span data-stu-id="d2095-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="d2095-107">설명</span><span class="sxs-lookup"><span data-stu-id="d2095-107">Description</span></span>  
 <span data-ttu-id="d2095-108">다음과 같은 고정 서버 역할 이름은 예약되어 있으므로 사용자 정의 로그인 이름으로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d2095-108">The following fixed server role names are reserved and cannot be used as user-defined login names.</span></span>  
  
-   <span data-ttu-id="d2095-109">**sysadmin**</span><span class="sxs-lookup"><span data-stu-id="d2095-109">**sysadmin**</span></span>  
  
-   <span data-ttu-id="d2095-110">**serveradmin**</span><span class="sxs-lookup"><span data-stu-id="d2095-110">**serveradmin**</span></span>  
  
-   <span data-ttu-id="d2095-111">**setupadmin**</span><span class="sxs-lookup"><span data-stu-id="d2095-111">**setupadmin**</span></span>  
  
-   <span data-ttu-id="d2095-112">**securityadmin**</span><span class="sxs-lookup"><span data-stu-id="d2095-112">**securityadmin**</span></span>  
  
-   <span data-ttu-id="d2095-113">**processadmin**</span><span class="sxs-lookup"><span data-stu-id="d2095-113">**processadmin**</span></span>  
  
-   <span data-ttu-id="d2095-114">**dbcreator**</span><span class="sxs-lookup"><span data-stu-id="d2095-114">**dbcreator**</span></span>  
  
-   <span data-ttu-id="d2095-115">**diskadmin**</span><span class="sxs-lookup"><span data-stu-id="d2095-115">**diskadmin**</span></span>  
  
-   <span data-ttu-id="d2095-116">**bulkadmin**</span><span class="sxs-lookup"><span data-stu-id="d2095-116">**bulkadmin**</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="d2095-117">수정 동작</span><span class="sxs-lookup"><span data-stu-id="d2095-117">Corrective Action</span></span>  
 <span data-ttu-id="d2095-118">업그레이드하기 전에 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d2095-118">Before upgrading, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="d2095-119">다음 문을 실행하여 로그인의 SID(보안 ID)를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="d2095-119">Record the security identifiers (SIDs) of the logins by executing the following statement.</span></span>  
  
    ```  
    SELECT name, sid   
    FROM master.dbo.syslogins   
    WHERE name IN('sysadmin', 'serveradmin','setupadmin', 'securityadmin','processadmin', 'dbcreator','diskadmin','bulkadmin')  
    ```  
  
2.  <span data-ttu-id="d2095-120">로그인을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="d2095-120">Drop the logins.</span></span>  
  
3.  <span data-ttu-id="d2095-121">**Sp_addlogin** 시스템 프로시저를 사용 하 여 새 로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d2095-121">Use the **sp_addlogin** system procedure to create new logins.</span></span> <span data-ttu-id="d2095-122">각 해당 로그인에 대 한 \*\* \@ sid\*\* 매개 변수에 1 단계에서 반환 된 sid를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2095-122">Specify the SID returned in step 1 in the **\@sid** parameter for each corresponding login.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2095-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d2095-123">See Also</span></span>  
 <span data-ttu-id="d2095-124">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="d2095-124">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="d2095-125">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="d2095-125">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
