---
title: Sys 사용자 이름 바꾸기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sys user names [SQL Server]
ms.assetid: d622d646-83e4-4b6f-9a21-77b301af04b5
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3af9d31a54adc5645cab6fcc7104ae7ff27a61b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639249"
---
# <a name="rename-user-sys"></a><span data-ttu-id="5d632-102">sys 사용자 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="5d632-102">Rename user sys</span></span>
  <span data-ttu-id="5d632-103">업그레이드 관리자가 데이터베이스에서 **sys** 사용자 이름을 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="5d632-103">Upgrade Advisor detected the user name **sys** in a database.</span></span> <span data-ttu-id="5d632-104">이 이름은 예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d632-104">This name is reserved.</span></span> <span data-ttu-id="5d632-105">업그레이드하기 전에 사용자 이름을 바꾸십시오.</span><span class="sxs-lookup"><span data-stu-id="5d632-105">Rename the user before you upgrade.</span></span> <span data-ttu-id="5d632-106">사용자 이름을 바꾸지 않으면 업그레이드 후 데이터베이스가 주의 대상 상태가 되며 온라인 상태가 될 때까지 데이터베이스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5d632-106">If the user is not renamed, the database will be in a suspect state after the upgrade process and will be unavailable until the database is brought online.</span></span>  
  
## <a name="component"></a><span data-ttu-id="5d632-107">구성 요소</span><span class="sxs-lookup"><span data-stu-id="5d632-107">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="5d632-108">Description</span><span class="sxs-lookup"><span data-stu-id="5d632-108">Description</span></span>  
 <span data-ttu-id="5d632-109">**sys** 사용자는 예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d632-109">User **sys** is reserved.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="5d632-110">수정 동작</span><span class="sxs-lookup"><span data-stu-id="5d632-110">Corrective Action</span></span>  
  
### <a name="before-upgrade-procedure"></a><span data-ttu-id="5d632-111">업그레이드 전 절차</span><span class="sxs-lookup"><span data-stu-id="5d632-111">Before Upgrade Procedure</span></span>  
 <span data-ttu-id="5d632-112">업그레이드하기 전에 **sys**사용자가 포함된 각 데이터베이스에서 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="5d632-112">Before you upgrade, in each database that contains user **sys**, do the following:</span></span>  
  
1.  <span data-ttu-id="5d632-113">새 사용자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5d632-113">Create a new user.</span></span>  
  
2.  <span data-ttu-id="5d632-114">다음 문을 사용하여 **sys** 사용자가 부여한 사용 권한과 **sys**사용자에게 부여된 사용 권한을 모두 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5d632-114">Use the following statements to display all permissions that are granted by user **sys** and granted to user **sys**.</span></span>  
  
    ```  
    -- Return permissions granted by user sys.  
    SELECT * FROM sysprotects WHERE grantor = USER_ID('sys')  
    -- Return permissions granted to user sys.  
    SELECT * FROM sysprotects WHERE uid = USER_ID('sys')  
    ```  
  
3.  <span data-ttu-id="5d632-115">**sp_changeobjectowner** 를 사용하여 **sys**가 소유한 모든 개체의 소유권을 새 사용자로 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="5d632-115">To transfer ownership of all objects owned by **sys** to the new user, use **sp_changeobjectowner**.</span></span>  
  
4.  <span data-ttu-id="5d632-116">**sys**사용자를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="5d632-116">Drop user **sys**.</span></span>  
  
5.  <span data-ttu-id="5d632-117">GRANT 문의 AS *new_user* 절을 사용하여 2단계에서 캡처된 원래 사용 권한을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="5d632-117">To restore the original permissions captured in step 2, use the AS *new_user* clause of the GRANT statement.</span></span>  
  
6.  <span data-ttu-id="5d632-118">새 사용자를 참조하도록 스크립트를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="5d632-118">Modify scripts to reference the new user.</span></span> <span data-ttu-id="5d632-119">예를 들어 `SELECT * FROM sys.my`_`table` 과 같은 문이 포함된 스크립트를 `SELECT * FROM new_user.my_table`로 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d632-119">For example, scripts that contain statements such as `SELECT * FROM sys.my`_`table` must be changed to `SELECT * FROM new_user.my_table`.</span></span>  
  
### <a name="after-upgrade-procedure"></a><span data-ttu-id="5d632-120">업그레이드 후 절차</span><span class="sxs-lookup"><span data-stu-id="5d632-120">After Upgrade Procedure</span></span>  
 <span data-ttu-id="5d632-121">업그레이드하기 전에 **sys** 사용자의 이름을 바꾸지 않았다면 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="5d632-121">If the user **sys** was not renamed prior to upgrading, do the following:</span></span>  
  
1.  <span data-ttu-id="5d632-122">`ALTER DATABASE db_name SET ONLINE`문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5d632-122">Execute the statement `ALTER DATABASE db_name SET ONLINE`.</span></span> <span data-ttu-id="5d632-123">데이터베이스는 SINGLE_USER 모드가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d632-123">The database will be in SINGLE_USER mode.</span></span>  
  
2.  <span data-ttu-id="5d632-124">"업그레이드 전 절차" 섹션의 모든 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="5d632-124">Follow all steps in the Before Upgrade Procedure section.</span></span>  
  
3.  <span data-ttu-id="5d632-125">`ALTER DATABASE db_name SET MULTI_USER`문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5d632-125">Execute the statement `ALTER DATABASE db_name SET MULTI_USER`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d632-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5d632-126">See Also</span></span>  
 <span data-ttu-id="5d632-127">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="5d632-127">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="5d632-128">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="5d632-128">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
