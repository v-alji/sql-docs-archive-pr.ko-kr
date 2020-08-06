---
title: 첫 번째 및 마지막 트리거 지정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- first triggers [SQL Server]
- last triggers
- DML triggers, first or last triggers
- INSTEAD OF triggers
- AFTER triggers
ms.assetid: 9e6c7684-3dd3-46bb-b7be-523b33fae4d5
author: rothja
ms.author: jroth
ms.openlocfilehash: 8ddb352b00dc759362c8f6ef1e861e55b6f184f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660381"
---
# <a name="specify-first-and-last-triggers"></a><span data-ttu-id="eae3a-102">첫 번째 및 마지막 트리거 지정</span><span class="sxs-lookup"><span data-stu-id="eae3a-102">Specify First and Last Triggers</span></span>
  <span data-ttu-id="eae3a-103">테이블과 연결된 AFTER 트리거 중 하나를 각 INSERT, DELETE 및 UPDATE 트리거 동작에 대한 첫 번째 AFTER 트리거나 마지막 AFTER 트리거로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eae3a-103">You can specify that one of the AFTER triggers associated with a table be either the first AFTER trigger or the last AFTER trigger that is fired for each INSERT, DELETE, and UPDATE triggering actions.</span></span> <span data-ttu-id="eae3a-104">첫 번째 트리거와 마지막 트리거 사이에 실행되는 AFTER 트리거는 정의되지 않은 순서로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="eae3a-104">The AFTER triggers that are fired between the first and last triggers are executed in undefined order.</span></span>  
  
 <span data-ttu-id="eae3a-105">AFTER 트리거의 순서를 지정하려면 **sp_settriggerorder** 저장 프로시저를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="eae3a-105">To specify the order for an AFTER trigger, use the **sp_settriggerorder** stored procedure.</span></span> <span data-ttu-id="eae3a-106">**sp_settriggerorder** 에는 다음과 같은 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eae3a-106">**sp_settriggerorder** has the following options.</span></span>  
  
|<span data-ttu-id="eae3a-107">옵션</span><span class="sxs-lookup"><span data-stu-id="eae3a-107">Option</span></span>|<span data-ttu-id="eae3a-108">Description</span><span class="sxs-lookup"><span data-stu-id="eae3a-108">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="eae3a-109">**첫째**</span><span class="sxs-lookup"><span data-stu-id="eae3a-109">**First**</span></span>|<span data-ttu-id="eae3a-110">DML 트리거를 트리거 동작에 대해 실행할 첫 번째 AFTER 트리거로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eae3a-110">Specifies that the DML trigger is the first AFTER trigger fired for a triggering action.</span></span>|  
|<span data-ttu-id="eae3a-111">**마지막**</span><span class="sxs-lookup"><span data-stu-id="eae3a-111">**Last**</span></span>|<span data-ttu-id="eae3a-112">DML 트리거를 트리거 동작에 대해 실행할 마지막 AFTER 트리거로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eae3a-112">Specifies that the DML trigger is the last AFTER trigger fired for a triggering action.</span></span>|  
|<span data-ttu-id="eae3a-113">**없음**</span><span class="sxs-lookup"><span data-stu-id="eae3a-113">**None**</span></span>|<span data-ttu-id="eae3a-114">DML 트리거가 실행되는 특정 순서가 없음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eae3a-114">Specifies that there is no specific order in which the DML trigger should be fired.</span></span> <span data-ttu-id="eae3a-115">주로 첫 번째 트리거나 마지막 트리거를 다시 설정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="eae3a-115">Used mainly to reset a trigger from being either first or last.</span></span>|  
  
 <span data-ttu-id="eae3a-116">다음 예에서는 **sp_settriggerorder**를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="eae3a-116">The following example shows using **sp_settriggerorder**:</span></span>  
  
```  
sp_settriggerorder @triggername = 'MyTrigger', @order = 'first', @stmttype = 'UPDATE'  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="eae3a-117">첫 번째 트리거와 마지막 트리거는 서로 다른 DML 트리거여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eae3a-117">The first and last triggers must be two different DML triggers.</span></span>  
  
 <span data-ttu-id="eae3a-118">한 테이블에 INSERT, UPDATE 및 DELETE 트리거를 동시에 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eae3a-118">A table can have INSERT, UPDATE, and DELETE triggers defined on it at the same time.</span></span> <span data-ttu-id="eae3a-119">문 유형마다 자체의 첫 번째 트리거와 마지막 트리거가 있을 수 있지만 두 트리거가 서로 달라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eae3a-119">Each statement type can have its own first and last triggers, but they cannot be the same triggers.</span></span>  
  
 <span data-ttu-id="eae3a-120">테이블에 정의된 첫 번째 트리거나 마지막 트리거가 FOR UPDATE, FOR DELETE 또는 FOR INSERT에 적용되지 않는 경우와 같이 특정 트리거 동작에 적용되지 않으면 이렇게 누락된 작업에 대한 첫 번째 트리거나 마지막 트리거는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eae3a-120">If the first or last trigger defined for a table does not cover a triggering action, such as not covering FOR UPDATE, FOR DELETE, or FOR INSERT, there is no first or last trigger for the missing actions.</span></span>  
  
 <span data-ttu-id="eae3a-121">첫 번째 트리거나 마지막 트리거로 INSTEAD OF 트리거를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eae3a-121">INSTEAD OF triggers cannot be specified as first or last triggers.</span></span> <span data-ttu-id="eae3a-122">INSTEAD OF 트리거는 기본 테이블이 업데이트되기 전에 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="eae3a-122">INSTEAD OF triggers are fired before updates are made to the underlying tables.</span></span> <span data-ttu-id="eae3a-123">기본 테이블이 INSTEAD OF 트리거에 의해 업데이트될 경우 테이블에 정의된 AFTER 트리거가 실행되기 전에 업데이트가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="eae3a-123">If updates are made by an INSTEAD OF trigger to underlying tables, the updates occur before any AFTER triggers defined on the table are fired.</span></span> <span data-ttu-id="eae3a-124">예를 들어 뷰의 INSTEAD OF INSERT 트리거가 기본 테이블에 데이터를 삽입하고 기본 테이블 자체에 한 개의 INSTEAD OF INSERT 트리거와 세 개의 AFTER INSERT 트리거가 있는 경우 삽입 동작 대신 기본 테이블의 INSTEAD OF INSERT 트리거가 실행되고 기본 테이블의 AFTER 트리거는 기본 테이블의 삽입 작업 후에 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="eae3a-124">For example, if an INSTEAD OF INSERT trigger on a view inserts data into a base table and the base table itself contains an INSTEAD OF INSERT trigger and three AFTER INSERT triggers, the INSTEAD OF INSERT trigger on the base table is fired instead of the inserting action, and the AFTER triggers on the base table are fired after any inserting action on the base table.</span></span> <span data-ttu-id="eae3a-125">자세한 내용은 [DML Triggers](dml-triggers.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eae3a-125">For more information, see [DML Triggers](dml-triggers.md).</span></span>  
  
 <span data-ttu-id="eae3a-126">ALTER TRIGGER 문에 의해 첫 번째 트리거나 마지막 트리거가 변경되는 경우 **첫 번째** 나 **마지막** 특성이 삭제되고 순서 값은 **없음**으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="eae3a-126">If an ALTER TRIGGER statement changes a first or last trigger, the **First** or **Last** attribute is dropped and the order value is set to **None**.</span></span> <span data-ttu-id="eae3a-127">순서는 **sp_settriggerorder**를 사용하여 다시 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eae3a-127">The order must be reset by using **sp_settriggerorder**.</span></span>  
  
 <span data-ttu-id="eae3a-128">OBJECTPROPERTY 함수의 **ExecIsFirstTrigger** 및 **ExecIsLastTrigger**속성을 통해 트리거가 첫 번째 트리거인지 또는 마지막 트리거인지 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eae3a-128">The OBJECTPROPERTY function reports whether a trigger is a first or last trigger by using the properties **ExecIsFirstTrigger** and **ExecIsLastTrigger**.</span></span>  
  
 <span data-ttu-id="eae3a-129">복제 시 즉시 업데이트 구독이나 지연 업데이트 구독에 포함된 테이블에 대해 첫 번째 트리거가 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="eae3a-129">Replication automatically generates a first trigger for any table that is included in an immediate updating or queued updating subscription.</span></span> <span data-ttu-id="eae3a-130">복제의 트리거는 첫 번째 트리거여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eae3a-130">Replication requires that its trigger be the first trigger.</span></span> <span data-ttu-id="eae3a-131">첫 번째 트리거가 있는 테이블을 즉시 업데이트 구독이나 지연 업데이트 구독에 포함시키면 복제 시 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="eae3a-131">Replication raises an error when you try to include a table with a first trigger in an immediate updating or queued updating subscription.</span></span> <span data-ttu-id="eae3a-132">테이블이 구독에 포함된 후 트리거를 첫 번째 트리거로 만들려고 하면 **sp_settriggerorder** 에서 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="eae3a-132">If you try to make a trigger a first trigger after a table has been included in a subscription, **sp_settriggerorder** returns an error.</span></span> <span data-ttu-id="eae3a-133">복제 트리거에 ALTER를 사용하거나 **sp_settriggerorder** 를 사용하여 복제 트리거를 마지막 트리거나 없음 트리거로 변경하면 구독이 제대로 작동하지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eae3a-133">If you use ALTER on the replication trigger or use **sp_settriggerorder** to change the replication trigger to a last or none trigger, the subscription will not function correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eae3a-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eae3a-134">See Also</span></span>  
 <span data-ttu-id="eae3a-135">[OBJECTPROPERTY&#40;Transact-SQL&#41;](/sql/t-sql/functions/objectpropertyex-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eae3a-135">[OBJECTPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectpropertyex-transact-sql) </span></span>  
 [<span data-ttu-id="eae3a-136">sp_settriggerorder&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eae3a-136">sp_settriggerorder &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-settriggerorder-transact-sql)  
  
  
