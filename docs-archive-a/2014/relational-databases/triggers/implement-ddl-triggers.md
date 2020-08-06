---
title: DDL 트리거 구현 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- DDL triggers, implementing
ms.assetid: f44e5340-1d18-40e9-828e-0ffcca091ae3
author: rothja
ms.author: jroth
ms.openlocfilehash: 110e69aca31df75d4b4d7a732de5c58556bd3e24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660388"
---
# <a name="implement-ddl-triggers"></a><span data-ttu-id="26ab4-102">DDL 트리거 구현</span><span class="sxs-lookup"><span data-stu-id="26ab4-102">Implement DDL Triggers</span></span>
  <span data-ttu-id="26ab4-103">이 항목에서는 DDL 트리거 생성, DDL 트리거 수정, DDL 트리거 해제 또는 삭제 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="26ab4-103">This topic provides information to help you create DDL triggers, modify DDL triggers, and disable or drop DDL triggers.</span></span>  
  
## <a name="creating-ddl-triggers"></a><span data-ttu-id="26ab4-104">DDL 트리거 만들기</span><span class="sxs-lookup"><span data-stu-id="26ab4-104">Creating DDL Triggers</span></span>  
 <span data-ttu-id="26ab4-105">DDL 트리거는 DDL 트리거에 대한 [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TRIGGER 문을 사용하여 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="26ab4-105">DDL triggers are created by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TRIGGER statement for DDL triggers.</span></span>  
  
 <span data-ttu-id="26ab4-106">**DDL 트리거를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="26ab4-106">**To create a DDL trigger**</span></span>  
  
-   [<span data-ttu-id="26ab4-107">CREATE TRIGGER&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26ab4-107">CREATE TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-trigger-transact-sql)  
  
> [!IMPORTANT]  
>  <span data-ttu-id="26ab4-108">나중 버전의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서는 트리거에서 결과 집합을 반환하는 기능이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="26ab4-108">The ability to return result sets from triggers will be removed in a future version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="26ab4-109">결과 집합을 반환하는 트리거는 트리거가 작동하지 않는 애플리케이션에 예기치 않은 동작을 유발할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ab4-109">Triggers that return result sets may cause unexpected behavior in applications that are not designed to work with them.</span></span> <span data-ttu-id="26ab4-110">향후 개발 작업에서는 트리거에서 결과 집합을 반환하지 않도록 하고 현재 이 기능을 사용하는 애플리케이션은 수정하세요.</span><span class="sxs-lookup"><span data-stu-id="26ab4-110">Avoid returning result sets from triggers in new development work, and plan to modify applications that currently do this.</span></span> <span data-ttu-id="26ab4-111">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 트리거가 결과 집합을 반환하지 않도록 하려면 [disallow results from triggers](../../database-engine/configure-windows/disallow-results-from-triggers-server-configuration-option.md) 옵션을 1로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="26ab4-111">To prevent triggers from returning result sets in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], set the [disallow results from triggers Option](../../database-engine/configure-windows/disallow-results-from-triggers-server-configuration-option.md) to 1.</span></span> <span data-ttu-id="26ab4-112">이후 버전의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서는 이 옵션이 기본적으로 1로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="26ab4-112">The default setting of this option will be 1 in a future version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="modifying-ddl-triggers"></a><span data-ttu-id="26ab4-113">DDL 트리거 수정</span><span class="sxs-lookup"><span data-stu-id="26ab4-113">Modifying DDL Triggers</span></span>  
 <span data-ttu-id="26ab4-114">트리거를 삭제하고 다시 만들거나 기존 트리거를 한 단계로 다시 정의하여 DDL 트리거 정의를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ab4-114">If you have to modify the definition of a DDL trigger, you can either drop and re-create the trigger or redefine the existing trigger in a single step.</span></span>  
  
 <span data-ttu-id="26ab4-115">DDL 트리거가 참조하는 개체의 이름을 변경하는 경우 트리거 텍스트에 새 개체 이름이 반영되도록 트리거를 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ab4-115">If you change the name of an object that is referenced by a DDL trigger, you must modify the trigger so that its text reflects the new name.</span></span> <span data-ttu-id="26ab4-116">따라서 개체 이름을 바꾸기 전에는 먼저 개체의 종속성을 표시하여 영향을 받는 트리거가 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ab4-116">Therefore, before renaming an object, display the dependencies of the object first to determine whether any triggers are affected by the proposed change.</span></span>  
  
 <span data-ttu-id="26ab4-117">트리거 정의를 암호화하도록 트리거가 수정될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ab4-117">A trigger can also be modified to encrypt its definition.</span></span>  
  
 <span data-ttu-id="26ab4-118">**트리거를 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="26ab4-118">**To modify a trigger**</span></span>  
  
-   [<span data-ttu-id="26ab4-119">ALTER TRIGGER&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26ab4-119">ALTER TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-trigger-transact-sql)  
  
 <span data-ttu-id="26ab4-120">**트리거의 종속 관계를 보려면**</span><span class="sxs-lookup"><span data-stu-id="26ab4-120">**To view the dependencies of a trigger**</span></span>  
  
-   [<span data-ttu-id="26ab4-121">sys.sql_expression_dependencies&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26ab4-121">sys.sql_expression_dependencies &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
-   [<span data-ttu-id="26ab4-122">sys.dm_sql_referenced_entities&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26ab4-122">sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)  
  
-   [<span data-ttu-id="26ab4-123">sys.dm_sql_referencing_entities&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26ab4-123">sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql)  
  
## <a name="disabling-and-dropping-ddl-triggers"></a><span data-ttu-id="26ab4-124">DDL 트리거 비활성화 및 삭제</span><span class="sxs-lookup"><span data-stu-id="26ab4-124">Disabling and Dropping DDL Triggers</span></span>  
 <span data-ttu-id="26ab4-125">더 이상 필요 없는 DDL 트리거는 비활성화하거나 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ab4-125">When a DDL trigger is no longer needed, you can disable it or delete it.</span></span>  
  
 <span data-ttu-id="26ab4-126">DDL 트리거를 비활성화해도 해당 트리거가 삭제되지 않으며</span><span class="sxs-lookup"><span data-stu-id="26ab4-126">Disabling a DDL trigger does not drop it.</span></span> <span data-ttu-id="26ab4-127">현재 데이터베이스의 개체로 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ab4-127">The trigger still exists as an object in the current database.</span></span> <span data-ttu-id="26ab4-128">그러나 해당 트리거가 프로그래밍된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행하는 경우에도 트리거는 발생되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="26ab4-128">However, the trigger will not fire when any [!INCLUDE[tsql](../../includes/tsql-md.md)] statements on which it was programmed are run.</span></span> <span data-ttu-id="26ab4-129">DDL 트리거를 해제했다가 다시 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ab4-129">DDL triggers that are disabled can be reenabled.</span></span> <span data-ttu-id="26ab4-130">DDL 트리거를 설정하면 처음 만들었을 때와 동일한 방법으로 트리거가 발생됩니다.</span><span class="sxs-lookup"><span data-stu-id="26ab4-130">Enabling a DDL trigger causes it to fire in the same way the trigger did when it was originally created.</span></span> <span data-ttu-id="26ab4-131">DDL 트리거를 만들면 기본적으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="26ab4-131">When DDL triggers are created, they are enabled by default.</span></span>  
  
 <span data-ttu-id="26ab4-132">DDL 트리거를 삭제하면 현재 데이터베이스에서 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="26ab4-132">When a DDL trigger is deleted, it is dropped from the current database.</span></span> <span data-ttu-id="26ab4-133">DDL 트리거가 적용된 개체 또는 데이터는 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="26ab4-133">Any objects or data upon which the DDL trigger is scoped are not affected.</span></span>  
  
 <span data-ttu-id="26ab4-134">**DDL 트리거를 비활성화하려면**</span><span class="sxs-lookup"><span data-stu-id="26ab4-134">**To disable a DDL trigger**</span></span>  
  
-   [<span data-ttu-id="26ab4-135">DISABLE TRIGGER&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26ab4-135">DISABLE TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/disable-trigger-transact-sql)  
  
-   [<span data-ttu-id="26ab4-136">ALTER TABLE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26ab4-136">ALTER TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-table-transact-sql)  
  
 <span data-ttu-id="26ab4-137">**DDL 트리거를 활성화하려면**</span><span class="sxs-lookup"><span data-stu-id="26ab4-137">**To enable a DDL trigger**</span></span>  
  
-   [<span data-ttu-id="26ab4-138">ENABLE TRIGGER&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26ab4-138">ENABLE TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/enable-trigger-transact-sql)  
  
-   [<span data-ttu-id="26ab4-139">ALTER TABLE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26ab4-139">ALTER TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-table-transact-sql)  
  
 <span data-ttu-id="26ab4-140">**DDL 트리거를 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="26ab4-140">**To delete a DDL trigger**</span></span>  
  
-   [<span data-ttu-id="26ab4-141">DROP TRIGGER&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26ab4-141">DROP TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-trigger-transact-sql)  
  
  
