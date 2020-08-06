---
title: System_function_schema |에서 사용자 정의 함수를 사용할 수 없습니다. Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- system functions [SQL Server]
- user-defined functions [SQL Server], system
ms.assetid: 3cb54053-ef65-4558-ae96-8686b6b22f4f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7242f9fda74288a2b7354ac0550ff4966e05c555
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742760"
---
# <a name="user-defined-functions-are-not-allowed-in-system_function_schema"></a><span data-ttu-id="d0369-102">system_function_schema에서 사용자 정의 함수가 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0369-102">User-defined functions are not allowed in system_function_schema</span></span>
  <span data-ttu-id="d0369-103">업그레이드 관리자가 문서화 되지 않은 사용자 **system_function_schema**소유 하 고 있는 사용자 정의 함수를 검색 했습니다.</span><span class="sxs-lookup"><span data-stu-id="d0369-103">The Upgrade Advisor detected user-defined functions that are owned by the undocumented user **system_function_schema**.</span></span> <span data-ttu-id="d0369-104">이 사용자를 지정해서는 사용자 정의 시스템 함수를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d0369-104">You cannot create a user-defined system function by specifying this user.</span></span> <span data-ttu-id="d0369-105">**System_function_schema** 사용자 이름이 존재 하지 않으며이 이름과 연결 된 사용자 ID (UID = 4)는 **sys** 스키마에 예약 되어 있으며 내부 에서만 사용 하도록 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0369-105">The **system_function_schema** user name does not exist, and the user ID that is associated with this name (UID = 4) is reserved for the **sys** schema and is restricted to internal use only.</span></span>  
  
## <a name="component"></a><span data-ttu-id="d0369-106">구성 요소</span><span class="sxs-lookup"><span data-stu-id="d0369-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="d0369-107">설명</span><span class="sxs-lookup"><span data-stu-id="d0369-107">Description</span></span>  
 <span data-ttu-id="d0369-108">시스템 개체 스토리지 및 액세스가 다음과 같이 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d0369-108">System object storage and access has changed in the following ways:</span></span>  
  
-   <span data-ttu-id="d0369-109">시스템 개체는 읽기 전용 **리소스** 데이터베이스에 저장 되며 시스템 개체의 직접 업데이트는 허용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0369-109">System objects are stored in the read-only **Resource** database, and direct system object updates are not permitted.</span></span>  
  
     <span data-ttu-id="d0369-110">시스템 개체는 모든 데이터베이스의 **sys** 스키마에 논리적으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d0369-110">System objects logically appear in the **sys** schema of every database.</span></span> <span data-ttu-id="d0369-111">이를 통해 모든 데이터베이스에서 한 부분으로 된 함수 이름을 지정하여 시스템 함수를 호출할 수 있는 기능이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0369-111">This maintains the ability to invoke system functions from any database by specifying a one-part function name.</span></span> <span data-ttu-id="d0369-112">예를 들어 모든 데이터베이스에서 `SELECT * FROM fn_helpcollations()` 문을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0369-112">For example, the statement `SELECT * FROM fn_helpcollations()` can be run from any database.</span></span>  
  
-   <span data-ttu-id="d0369-113">문서화 되지 않은 사용자 **system_function_schema** 제거 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d0369-113">The undocumented user **system_function_schema** has been removed.</span></span>  
  
-   <span data-ttu-id="d0369-114">**System_function_schema** 와 연결 된 사용자 ID (UID = 4)는 **sys** 스키마에 예약 되어 있으며 내부 에서만 사용 하도록 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0369-114">The user ID associated with **system_function_schema** (UID = 4) is reserved for the **sys** schema and is restricted to internal use only.</span></span>  
  
 <span data-ttu-id="d0369-115">이러한 변경 사항은 사용자 정의 시스템 함수에 다음과 같은 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d0369-115">These changes have the following effect on user-defined system functions:</span></span>  
  
-   <span data-ttu-id="d0369-116">**System_function_schema** 를 참조 하는 DDL (데이터 정의 언어) 문이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0369-116">Data Definition Language (DDL) statements that reference **system_function_schema** will fail.</span></span> <span data-ttu-id="d0369-117">예를 들어 `CREATE FUNCTION system` _ `function` \_ `schema.fn` \_ `MySystemFunction` ... 문을 사용할 경우 성공 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0369-117">For example, the statement `CREATE FUNCTION system`_`function`\_`schema.fn`\_`MySystemFunction` ... will not succeed.</span></span>  
  
-   <span data-ttu-id="d0369-118">로 업그레이드 한 후 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] **system_function_schema** 에서 소유 하는 기존 개체는 **master** 데이터베이스의 **sys** 스키마에만 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0369-118">After you upgrade to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], existing objects that are owned by **system_function_schema** are contained only in the **sys** schema of the **master** database.</span></span> <span data-ttu-id="d0369-119">시스템 개체는 수정할 수 없으므로 이러한 함수는 **master** 데이터베이스에서 변경 되거나 삭제 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0369-119">Because system objects cannot be modified, these functions can never be changed or dropped from the **master** database.</span></span> <span data-ttu-id="d0369-120">또한 이러한 함수는 다른 데이터베이스에서 한 부분으로 된 함수 이름을 지정하여 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d0369-120">Additionally, these functions cannot be invoked from other databases by specifying only a one-part function name.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="d0369-121">수정 동작</span><span class="sxs-lookup"><span data-stu-id="d0369-121">Corrective Action</span></span>  
 <span data-ttu-id="d0369-122">업그레이드하기 전에 다음 태스크를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="d0369-122">Before you upgrade , complete the following tasks:</span></span>  
  
1.  <span data-ttu-id="d0369-123">**Sp_changeobjectowner** 시스템 저장 프로시저를 사용 하 여 기존 사용자 정의 함수의 소유권을 **dbo** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0369-123">Change the ownership of existing user-defined functions to **dbo** by using the **sp_changeobjectowner** system stored procedure.</span></span>  
  
2.  <span data-ttu-id="d0369-124">'fn_' 접두사를 사용하지 않도록 함수 이름을 변경하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d0369-124">Consider renaming the function so that is does not use the prefix 'fn_'.</span></span> <span data-ttu-id="d0369-125">이렇게 하면 현재 또는 향후 시스템 함수와의 이름 충돌 가능성을 피할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0369-125">This will avoid potential name conflicts with current or future system functions.</span></span>  
  
3.  <span data-ttu-id="d0369-126">수정된 함수를 사용하는 모든 데이터베이스에 해당 함수의 복사본을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d0369-126">Add a copy of the modified functions in every database that uses them.</span></span>  
  
4.  <span data-ttu-id="d0369-127">사용자 정의 함수 DDL 문이 포함 된 모든 스크립트에서 **system_function_schema** 에 대 한 참조를 **dbo** 로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="d0369-127">Replace references to **system_function_schema** with **dbo** in all scripts that contain user-defined function DDL statements.</span></span>  
  
5.  <span data-ttu-id="d0369-128">이러한 함수를 호출 하는 스크립트를 수정 하 여 두 부분으로 구성 된 이름 dbo를 사용 합니다 **.** _function_name_또는 세 부분으로 구성 된 이름 _database_name_**입니다.** dbo. *function_name*.</span><span class="sxs-lookup"><span data-stu-id="d0369-128">Modify scripts that invoke these functions to use either the two-part name dbo **.**_function_name_, or the three-part name _database_name_**.** dbo.*function_name*.</span></span>  
  
 <span data-ttu-id="d0369-129">자세한 내용은 SQL Server 온라인 설명서에서 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0369-129">For more information, see the following topics in SQL Server Books Online:</span></span>  
  
-   <span data-ttu-id="d0369-130">"sp_changeobjectowner"</span><span class="sxs-lookup"><span data-stu-id="d0369-130">"sp_changeobjectowner"</span></span>  
  
-   <span data-ttu-id="d0369-131">"사용자와 스키마 분리"</span><span class="sxs-lookup"><span data-stu-id="d0369-131">"User-schema Separation"</span></span>  
  
-   <span data-ttu-id="d0369-132">"리소스 데이터베이스"</span><span class="sxs-lookup"><span data-stu-id="d0369-132">"Resource Database"</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0369-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d0369-133">See Also</span></span>  
 <span data-ttu-id="d0369-134">[SQL Server 2014 업그레이드 관리자 &#91;새&#93;](sql-server-2014-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="d0369-134">[SQL Server 2014 Upgrade Advisor &#91;new&#93;](sql-server-2014-upgrade-advisor.md) </span></span>  
 <span data-ttu-id="d0369-135">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="d0369-135">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 <span data-ttu-id="d0369-136">[시스템 개체를 수정 하는 문을 제거 합니다.](../../../2014/sql-server/install/remove-statements-that-modify-system-objects.md) </span><span class="sxs-lookup"><span data-stu-id="d0369-136">[Remove statements that modify system objects](../../../2014/sql-server/install/remove-statements-that-modify-system-objects.md) </span></span>  
 [<span data-ttu-id="d0369-137">시스템 개체를 삭제하는 문을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="d0369-137">Remove statements that drop system objects</span></span>](../../../2014/sql-server/install/remove-statements-that-drop-system-objects.md)  
  
  
