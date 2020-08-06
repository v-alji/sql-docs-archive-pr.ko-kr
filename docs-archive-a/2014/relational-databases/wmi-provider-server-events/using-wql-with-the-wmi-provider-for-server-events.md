---
title: 서버 이벤트 용 WMI 공급자에 WQL 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- queries [WMI]
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Server Events, WQL
ms.assetid: 58b67426-1e66-4445-8e2c-03182e94c4be
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: df2bbf5c6031781494695f95116441fde34bf4f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650835"
---
# <a name="using-wql-with-the-wmi-provider-for-server-events"></a><span data-ttu-id="78fa3-102">서버 이벤트용 WMI 공급자에 WQL 사용</span><span class="sxs-lookup"><span data-stu-id="78fa3-102">Using WQL with the WMI Provider for Server Events</span></span>
  <span data-ttu-id="78fa3-103">관리 애플리케이션은 서버 이벤트용 WMI 공급자를 통해 WQL(WMI Query Language) 문을 실행하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이벤트에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-103">Management applications access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events using the WMI Provider for Server Events by issuing WMI Query Language (WQL) statements.</span></span> <span data-ttu-id="78fa3-104">WQL은 몇 가지 WMI 관련 확장 기능이 포함된 SQL(구조적 쿼리 언어)의 단순화된 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-104">WQL is a simplified subset of structured query language (SQL), with some WMI-specific extensions.</span></span> <span data-ttu-id="78fa3-105">WQL을 사용할 경우 애플리케이션은 특정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스, 데이터베이스 또는 데이터베이스 개체(현재 지원되는 유일한 개체는 큐임)에 대해 이벤트 유형을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-105">In using WQL, an application retrieves an event type against a specific instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a database, or a database object (the only object currently supported is queue).</span></span> <span data-ttu-id="78fa3-106">서버 이벤트 용 WMI 공급자는 데이터베이스 범위 또는 개체 범위 이벤트 알림의 경우 대상 데이터베이스에 생성 되는 이벤트 알림이나 서버 범위 이벤트 알림의 경우 **master** 데이터베이스에 생성 되는 이벤트 알림으로 쿼리를 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-106">The WMI Provider for Server Events translates the query into an event notification that is created in the target database for database-scoped or object-scoped event notifications, or in the **master** database for server-scoped event notifications.</span></span>  
  
 <span data-ttu-id="78fa3-107">예를 들어 다음 WQL 쿼리를 살펴보십시오.</span><span class="sxs-lookup"><span data-stu-id="78fa3-107">For example, consider the following WQL query:</span></span>  
  
```  
SELECT * FROM DDL_DATABASE_LEVEL_EVENTS WHERE DatabaseName = 'AdventureWorks'  
```  
  
 <span data-ttu-id="78fa3-108">이 쿼리에서 WMI 공급자는 대상 서버에서 이벤트 알림과 동등한 항목을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-108">From this query, the WMI Provider tries to produce the equivalent of this event notification on the target server:</span></span>  
  
```  
USE AdventureWorks ;  
GO  
  
CREATE EVENT NOTIFICATION SQLWEP_76CF38C1_18BB_42DD_A7DC_C8820155B0E9  
    ON DATABASE  
    WITH FAN_IN  
    FOR DDL_DATABASE_LEVEL_EVENTS  
    TO SERVICE   
        'SQL/Notifications/ProcessWMIEventProviderNotification/v1.0',  
        'A7E5521A-1CA6-4741-865D-826F804E5135';  
GO  
```  
  
 <span data-ttu-id="78fa3-109">WQL 쿼리(`FROM`)의 `DDL_DATABASE_LEVEL_EVENTS` 절에 있는 인수는 이벤트 알림을 만들 수 있는 유효한 모든 이벤트일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-109">The argument in the `FROM` clause of the WQL query (`DDL_DATABASE_LEVEL_EVENTS`) can be any valid event upon which an event notification can be created.</span></span> <span data-ttu-id="78fa3-110">`SELECT` 및 `WHERE` 절의 인수는 이벤트 또는 해당 부모 이벤트와 연결된 이벤트 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-110">The arguments in the `SELECT` and `WHERE` clauses can specify any event property associated with an event or its parent event.</span></span> <span data-ttu-id="78fa3-111">유효한 이벤트 및 이벤트 속성 목록은 [이벤트 알림 (데이터베이스 엔진)](https://technet.microsoft.com/library/ms182602.aspx)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="78fa3-111">For a list of valid events and event properties, see [Event Notifications (Database Engine)](https://technet.microsoft.com/library/ms182602.aspx).</span></span>  
  
 <span data-ttu-id="78fa3-112">서버 이벤트용 WMI 공급자가 명시적으로 지원하는 WQL 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-112">The following WQL syntax is supported explicitly by the WMI Provider for Server Events.</span></span> <span data-ttu-id="78fa3-113">추가 WQL 구문을 지정할 수도 있지만 해당 구문은 이 공급자와 관련이 없으며 대신 WMI 호스트 서비스에 의해 구문 분석됩니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-113">Additional WQL syntax may be specified, but it is not specific to this provider and is parsed instead by the WMI host service.</span></span> <span data-ttu-id="78fa3-114">WMI 쿼리 언어에 대한 자세한 내용은 MSDN(Microsoft Developer Network)의 WQL 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="78fa3-114">For more information about the WMI Query Language, see the WQL documentation on the Microsoft Developer Network (MSDN).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78fa3-115">구문</span><span class="sxs-lookup"><span data-stu-id="78fa3-115">Syntax</span></span>  
  
```  
  
SELECT { event_property [ ,...n ] | * }  
FROM event_type   
WHERE where_condition  
```  
  
## <a name="arguments"></a><span data-ttu-id="78fa3-116">인수</span><span class="sxs-lookup"><span data-stu-id="78fa3-116">Arguments</span></span>  
 <span data-ttu-id="78fa3-117">*event_property*</span><span class="sxs-lookup"><span data-stu-id="78fa3-117">*event_property*</span></span>  
 <span data-ttu-id="78fa3-118">이벤트의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-118">Is a property of an event.</span></span> <span data-ttu-id="78fa3-119">이러한 예로 `PostTime`, `SPID` 및 `LoginName`이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-119">Examples include `PostTime`, `SPID`, and `LoginName`.</span></span> <span data-ttu-id="78fa3-120">[서버 이벤트 용 WMI 공급자 클래스 및 속성](wmi-provider-for-server-events-classes-and-properties.md) 에 나열 된 각 이벤트를 조회 하 여 보유 한 속성을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-120">Look up each event listed in [WMI Provider for Server Events Classes and Properties](wmi-provider-for-server-events-classes-and-properties.md) to determine which properties it holds.</span></span> <span data-ttu-id="78fa3-121">예를 들어 DDL_DATABASE_LEVEL_EVENTS 이벤트는 `DatabaseName` 및 `UserName` 속성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-121">For example, the DDL_DATABASE_LEVEL_EVENTS event holds the `DatabaseName` and `UserName` properties.</span></span> <span data-ttu-id="78fa3-122">또한 부모 이벤트에서 `SQLInstance`, `LoginName`, `PostTime`, `SPID` 및 `ComputerName` 속성을 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-122">It also inherits the `SQLInstance`, `LoginName`, `PostTime`, `SPID`, and `ComputerName` properties from its parent events.</span></span>  
  
 <span data-ttu-id="78fa3-123">**,** *... n*</span><span class="sxs-lookup"><span data-stu-id="78fa3-123">**,** *...n*</span></span>  
 <span data-ttu-id="78fa3-124">*Event_property* 를 쉼표로 구분 하 여 여러 번 쿼리할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-124">Indicates that *event_property* can be queried multiple times, separated by commas.</span></span>  
  
 \*  
 <span data-ttu-id="78fa3-125">이벤트와 관련된 모든 속성이 쿼리되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-125">Specifies that all properties associated with an event are queried.</span></span>  
  
 <span data-ttu-id="78fa3-126">*event_type*</span><span class="sxs-lookup"><span data-stu-id="78fa3-126">*event_type*</span></span>  
 <span data-ttu-id="78fa3-127">이벤트 알림을 만들 수 있는 모든 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-127">Is any event against which an event notification can be created.</span></span> <span data-ttu-id="78fa3-128">사용 가능한 이벤트 목록은 [서버 이벤트 용 WMI 공급자 클래스 및 속성](https://technet.microsoft.com/library/ms186449.aspx)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="78fa3-128">For a list of available events, see [WMI Provider for Server Events Classes and Properties](https://technet.microsoft.com/library/ms186449.aspx).</span></span> <span data-ttu-id="78fa3-129">이벤트 *유형* 이름은 *event_type*  |  create event notification을 사용 하 여 수동으로 이벤트 알림을 만들 때 지정할 수 있는 동일한 event_type*event_group* 에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-129">Note that *event type* names correspond to the same *event_type* | *event_group* that can be specified when you manually create an event notification by using CREATE EVENT NOTIFICATION.</span></span> <span data-ttu-id="78fa3-130">*이벤트 유형의* 예로는 CREATE_TABLE, LOCK_DEADLOCK, DDL_USER_EVENTS 및 TRC_DATABASE가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-130">Examples of *event type* include CREATE_TABLE, LOCK_DEADLOCK, DDL_USER_EVENTS, and TRC_DATABASE.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="78fa3-131">DDL과 같은 작업을 수행하는 특정 시스템 저장 프로시저에서 이벤트 알림이 발생할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-131">Certain system stored procedures that perform DDL-like operations can also fire event notifications.</span></span> <span data-ttu-id="78fa3-132">이벤트 알림을 테스트하여 실행된 시스템 저장 프로시저에 대한 응답을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-132">Test your event notifications to determine their responses to system stored procedures that are run.</span></span> <span data-ttu-id="78fa3-133">예를 들어 CREATE TYPE 문과 **sp_addtype** 저장 프로시저는 모두 CREATE_TYPE 이벤트에 대해 생성 되는 이벤트 알림을 발생 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-133">For example, the CREATE TYPE statement and **sp_addtype** stored procedure will both fire an event notification that is created on a CREATE_TYPE event.</span></span> <span data-ttu-id="78fa3-134">그러나 **sp_rename** 저장 프로시저는 이벤트 알림을 발생 시 지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-134">However, the **sp_rename** stored procedure does not fire any event notifications.</span></span> <span data-ttu-id="78fa3-135">자세한 내용은[DDL Events](../triggers/ddl-events.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="78fa3-135">For more information, see[DDL Events](../triggers/ddl-events.md).</span></span>  
  
 <span data-ttu-id="78fa3-136">*where_condition*</span><span class="sxs-lookup"><span data-stu-id="78fa3-136">*where_condition*</span></span>  
 <span data-ttu-id="78fa3-137">*Event_property* 이름 및 논리 and 비교 연산자로 구성 된 where 절 쿼리 조건자입니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-137">Is a WHERE clause query predicate made up of *event_property* names and logical and comparison operators.</span></span> <span data-ttu-id="78fa3-138">*Where_condition* 는 대상 데이터베이스에 해당 이벤트 알림이 등록 되는 범위를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-138">The *where_condition* determines the scope in which the corresponding event notification is registered in the target database.</span></span> <span data-ttu-id="78fa3-139">또한 event_type 쿼리할 특정 스키마 또는 개체를 대상으로 하는 필터 역할을 할 수 있습니다 *.*</span><span class="sxs-lookup"><span data-stu-id="78fa3-139">It can also act as a filter to target a particular schema or object from which to query *event_type.*</span></span> <span data-ttu-id="78fa3-140">자세한 내용은 이 항목의 뒷부분에 나오는 주의 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="78fa3-140">For more information, see the Remarks section later in this topic.</span></span>  
  
 <span data-ttu-id="78fa3-141">`=` 피연산자만 `DatabaseName`, `SchemaName` 및 `ObjectName`과 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-141">Only the `=` operand can be used together with `DatabaseName`, `SchemaName`, and `ObjectName`.</span></span> <span data-ttu-id="78fa3-142">다른 식은 이러한 이벤트 속성과 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-142">Other expressions cannot be used with these event properties.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78fa3-143">설명</span><span class="sxs-lookup"><span data-stu-id="78fa3-143">Remarks</span></span>  
 <span data-ttu-id="78fa3-144">서버 이벤트 용 WMI 공급자 구문의 *where_condition* 은 다음을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-144">The *where_condition* of the WMI Provider for Server Events syntax determines the following:</span></span>  
  
-   <span data-ttu-id="78fa3-145">공급자가 지정 된 *event_type*를 검색 하려고 하는 범위입니다. 서버 수준, 데이터베이스 수준 또는 개체 수준 (현재 지원 되는 유일한 개체는 큐)입니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-145">The scope by which the provider tries to retrieve the specified *event_type*: the server level, database level, or object level (the only object currently supported is queue).</span></span> <span data-ttu-id="78fa3-146">궁극적으로 이 범위는 대상 데이터베이스에 생성되는 이벤트 알림 유형을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-146">Ultimately, this scope determines the type of event notification created in the target database.</span></span> <span data-ttu-id="78fa3-147">이 프로세스를 이벤트 알림 등록이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-147">This process called event notification registration.</span></span>  
  
-   <span data-ttu-id="78fa3-148">필요한 경우 등록이 수행되는 데이터베이스, 스키마 및 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-148">The database, schema, and object, where appropriate, on which to register.</span></span>  
  
 <span data-ttu-id="78fa3-149">서버 이벤트용 WMI 공급자는 아래에서 위로, 첫 번째 일치 알고리즘을 사용하여 기본 EVENT NOTIFICATION에 대한 가능한 가장 좁은 범위를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-149">The WMI Provider for Server Events uses a bottom-up, first-fit algorithm to produce the narrowest possible scope for the underlying EVENT NOTIFICATION.</span></span> <span data-ttu-id="78fa3-150">이 알고리즘은 서버의 내부 활동과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 WMI 호스트 프로세스 인스턴스 간의 네트워크 트래픽을 최소화합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-150">The algorithm tries to minimize internal activity on the server and network traffic between the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the WMI host process.</span></span> <span data-ttu-id="78fa3-151">공급자는 FROM 절에 지정 된 *event_type* 와 where 절의 조건을 검사 하 고 가능한 가장 좁은 범위를 사용 하 여 기본 이벤트 알림을 등록 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-151">The provider examines the *event_type* specified in the FROM clause and the conditions in the WHERE clause, and tries to register the underlying EVENT NOTIFICATION with the narrowest possible scope.</span></span> <span data-ttu-id="78fa3-152">공급자는 가장 좁은 범위를 등록할 수 없는 경우 등록에 성공할 때까지 연속적으로 더 높은 범위에 등록을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-152">If the provider cannot register at the narrowest scope, it tries to register at successively higher scopes until a registration finally succeeds.</span></span> <span data-ttu-id="78fa3-153">가장 높은 범위인 서버 수준에 도달했지만 실패하는 경우 소비자에게 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-153">If it reaches the highest scope the server-level) and fails, it returns an error to the consumer.</span></span>  
  
 <span data-ttu-id="78fa3-154">예를 들어 WHERE 절에 DatabaseName =**'** AdventureWorks **'** 를 지정 하면 공급자는 데이터베이스에 이벤트 알림을 등록 하려고 합니다 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="78fa3-154">For example, if DatabaseName=**'** AdventureWorks **'** is specified in the WHERE clause, the provider tries to register an event notification in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="78fa3-155">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스가 있고 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]에 이벤트 알림을 만드는 데 필요한 권한이 호출 클라이언트에 있으면 등록이 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-155">If the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database exists and the calling client has the required permissions to create an event notification in [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], the registration is successful.</span></span> <span data-ttu-id="78fa3-156">그렇지 않으면 서버 수준에서 이벤트 알림이 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-156">Otherwise, an attempt is made to register the event notification at the server level.</span></span> <span data-ttu-id="78fa3-157">WMI 클라이언트에 필요한 사용 권한이 있으면 등록이 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-157">The registration succeeds if the WMI client has the required permissions.</span></span> <span data-ttu-id="78fa3-158">하지만 이 시나리오에서는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스를 만들 때까지 이벤트가 클라이언트에 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-158">However, under this scenario, events are not returned to the client until the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database has been created.</span></span>  
  
 <span data-ttu-id="78fa3-159">또한 *where_condition* 는 필터 역할을 하 여 쿼리를 특정 데이터베이스, 스키마 또는 개체로 추가로 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-159">The *where_condition* can also act as a filter to additionally limit the query to a specific database, schema, or object.</span></span> <span data-ttu-id="78fa3-160">예를 들어 다음 WQL 쿼리를 살펴보십시오.</span><span class="sxs-lookup"><span data-stu-id="78fa3-160">For example, consider the following WQL query:</span></span>  
  
```  
SELECT * FROM ALTER_TABLE   
WHERE DatabaseName = 'AdventureWorks' AND SchemaName = 'Sales'   
    AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'  
```  
  
 <span data-ttu-id="78fa3-161">등록 프로세스의 결과에 따라 이 WOL 쿼리를 데이터베이스 또는 서버 수준에서 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-161">Depending on the outcome of the registration process, this WQL query may be registered either at the database or server level.</span></span> <span data-ttu-id="78fa3-162">하지만 서버 수준에서 등록된 경우에도 공급자는 궁극적으로 `ALTER_TABLE` 테이블에 적용되지 않는 모든 `AdventureWorks.Sales.SalesOrderDetail` 이벤트를 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-162">However, even if it is registered at the server level, the provider ultimately filters any `ALTER_TABLE` events that do not apply to the `AdventureWorks.Sales.SalesOrderDetail` table.</span></span> <span data-ttu-id="78fa3-163">즉, 공급자는 특정 테이블에서 발생하는 `ALTER_TABLE` 이벤트의 속성만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-163">In other words, the provider returns only the properties of the `ALTER_TABLE` events that occur on that specific table.</span></span>  
  
 <span data-ttu-id="78fa3-164">`DatabaseName='AW1'` OR `DatabaseName='AW2'`와 같은 복합 식을 지정하면 두 개의 개별 이벤트 알림 대신 서버 범위에서 단일 이벤트 알림이 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-164">If a compound expression such as `DatabaseName='AW1'` OR `DatabaseName='AW2'` is specified, an attempt is made to register a single event notification at the server scope instead of two separate event notifications.</span></span> <span data-ttu-id="78fa3-165">호출 클라이언트에 사용 권한이 있으면 등록이 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-165">The registration succeeds if the calling client has permissions.</span></span>  
  
 <span data-ttu-id="78fa3-166">`SchemaName='X' AND ObjectType='Y' AND ObjectName='Z'`절에이 모두 지정 된 경우 `WHERE` 스키마의 개체에 직접 이벤트 알림을 등록 하려고 시도 합니다 `Z` `X` .</span><span class="sxs-lookup"><span data-stu-id="78fa3-166">If `SchemaName='X' AND ObjectType='Y' AND ObjectName='Z'` are all specified in the `WHERE` clause, an attempt is made to register the event notification directly on object `Z` in schema `X`.</span></span> <span data-ttu-id="78fa3-167">클라이언트에 사용 권한이 있으면 등록이 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-167">The registration succeeds if the client has permissions.</span></span> <span data-ttu-id="78fa3-168">현재 개체 수준 이벤트는 큐 에서만 지원 되 고 QUEUE_ACTIVATION *event_type*에 대해서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-168">Note that currently, object-level events are supported only on queues, and only for the QUEUE_ACTIVATION *event_type*.</span></span>  
  
 <span data-ttu-id="78fa3-169">임의의 특정 범위에서 모든 이벤트를 쿼리할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-169">Note that not all events can be queried at any particular scope.</span></span> <span data-ttu-id="78fa3-170">예를 들어 Lock_Deadlock과 같은 추적 이벤트나 TRC_LOCKS와 같은 추적 이벤트 그룹의 WQL 쿼리는 서버 수준에서만 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-170">For example, a WQL query on a trace event such as Lock_Deadlock, or a trace event group such as TRC_LOCKS, can only be registered at the server level.</span></span> <span data-ttu-id="78fa3-171">이와 유사하게, CREATE_ENDPOINT 이벤트 및 DDL_ENDPOINT_EVENTS 이벤트 그룹도 서버 수준에서만 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-171">Similarly, the CREATE_ENDPOINT event and the DDL_ENDPOINT_EVENTS event group can also be registered only at the server level.</span></span> <span data-ttu-id="78fa3-172">이벤트 등록에 적합 한 범위에 대 한 자세한 내용은 [이벤트 알림 디자인](https://technet.microsoft.com/library/ms175854\(v=sql.105\).aspx)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="78fa3-172">For more information about the appropriate scope for registering events, see [Designing Event Notifications](https://technet.microsoft.com/library/ms175854\(v=sql.105\).aspx).</span></span> <span data-ttu-id="78fa3-173">서버 수준 에서만 *event_type* 등록 될 수 있는 WQL 쿼리를 등록 하려는 시도는 항상 서버 수준에서 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-173">An attempt to register a WQL query whose *event_type* can only be registered at the server level is always made at the server level.</span></span> <span data-ttu-id="78fa3-174">WMI 클라이언트에 사용 권한이 있으면 등록이 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-174">Registration succeeds if the WMI client has permissions.</span></span> <span data-ttu-id="78fa3-175">그렇지 않으면 오류가 클라이언트에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-175">Otherwise, an error is returned to the client.</span></span> <span data-ttu-id="78fa3-176">하지만 경우에 따라 이벤트에 해당하는 속성을 기반으로 WHERE 절을 서버 수준 이벤트의 필터로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-176">In some cases, however, you can still use the WHERE clause as a filter for server-level events based on the properties that correspond to the event.</span></span> <span data-ttu-id="78fa3-177">예를 들어 많은 추적 이벤트에는 WHERE 절에 필터로 사용할 수 있는 `DatabaseName` 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-177">For example, many trace events have a `DatabaseName` property that can be used in the WHERE clause as a filter.</span></span>  
  
 <span data-ttu-id="78fa3-178">서버 범위 이벤트 알림은 **master** 데이터베이스에 생성 되며, [server_event_notifications](/sql/relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql) 카탈로그 뷰를 사용 하 여 메타 데이터에 대해 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-178">Server-scoped event notifications are created in the **master** database and can be queried for metadata by using the [sys.server_event_notifications](/sql/relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="78fa3-179">데이터베이스 범위 또는 개체 범위 이벤트 알림은 지정 된 데이터베이스에 생성 되며, [event_notifications](/sql/relational-databases/system-catalog-views/sys-event-notifications-transact-sql) 카탈로그 뷰를 사용 하 여 메타 데이터에 대해 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-179">Database-scoped or object-scoped event notifications are created in the specified database and can be queried for metadata by using the [sys.event_notifications](/sql/relational-databases/system-catalog-views/sys-event-notifications-transact-sql) catalog view.</span></span> <span data-ttu-id="78fa3-180">카탈로그 뷰에 해당 데이터베이스 이름을 접두사로 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-180">(You must prefix the catalog view with the corresponding database name.)</span></span>  
  
## <a name="examples"></a><span data-ttu-id="78fa3-181">예</span><span class="sxs-lookup"><span data-stu-id="78fa3-181">Examples</span></span>  
  
### <a name="a-querying-for-events-at-the-server-scope"></a><span data-ttu-id="78fa3-182">A.</span><span class="sxs-lookup"><span data-stu-id="78fa3-182">A.</span></span> <span data-ttu-id="78fa3-183">서버 범위에서 이벤트 쿼리</span><span class="sxs-lookup"><span data-stu-id="78fa3-183">Querying for events at the server scope</span></span>  
 <span data-ttu-id="78fa3-184">다음 WQL 쿼리는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 발생하는 `SERVER_MEMORY_CHANGE` 추적 이벤트의 모든 이벤트 속성을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-184">The following WQL query retrieves all event properties for any `SERVER_MEMORY_CHANGE` trace event that occurs on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
```  
SELECT * FROM SERVER_MEMORY_CHANGE  
```  
  
### <a name="b-querying-for-events-at-the-database-scope"></a><span data-ttu-id="78fa3-185">B.</span><span class="sxs-lookup"><span data-stu-id="78fa3-185">B.</span></span> <span data-ttu-id="78fa3-186">데이터베이스 범위에서 이벤트 쿼리</span><span class="sxs-lookup"><span data-stu-id="78fa3-186">Querying for events at the database scope</span></span>  
 <span data-ttu-id="78fa3-187">다음 WQL 쿼리는 `AdventureWorks` 데이터베이스에서 발생하고 `DDL_DATABASE_LEVEL_EVENTS` 이벤트 그룹에 속한 이벤트의 특정 이벤트 속성을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-187">The following WQL query retrieves specific event properties for any event that occurs in the `AdventureWorks` database and exists under the `DDL_DATABASE_LEVEL_EVENTS` event group.</span></span>  
  
```  
SELECT SPID, SQLInstance, DatabaseName FROM DDL_DATABASE_LEVEL_EVENTS   
WHERE DatabaseName = 'AdventureWorks'   
```  
  
### <a name="c-querying-for-events-at-the-database-scope-filtering-by-schema-and-object"></a><span data-ttu-id="78fa3-188">C.</span><span class="sxs-lookup"><span data-stu-id="78fa3-188">C.</span></span> <span data-ttu-id="78fa3-189">스키마 및 개체로 필터링하여 데이터베이스 범위에서 이벤트 쿼리</span><span class="sxs-lookup"><span data-stu-id="78fa3-189">Querying for events at the database scope, filtering by schema and object</span></span>  
 <span data-ttu-id="78fa3-190">다음 쿼리는 `ALTER_TABLE` 테이블에서 발생하는 `AdventureWorks.Sales.SalesOrderDetail` 이벤트의 모든 이벤트 속성을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="78fa3-190">The following query retrieves all event properties for any `ALTER_TABLE` event that occurs on table `AdventureWorks.Sales.SalesOrderDetail`.</span></span>  
  
```  
SELECT * FROM ALTER_TABLE   
WHERE DatabaseName = 'AdventureWorks' AND SchemaName = 'Sales'   
    AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'  
```  
  
## <a name="see-also"></a><span data-ttu-id="78fa3-191">참고 항목</span><span class="sxs-lookup"><span data-stu-id="78fa3-191">See Also</span></span>  
 <span data-ttu-id="78fa3-192">[서버 이벤트 용 WMI 공급자 개념](https://technet.microsoft.com/library/ms180560.aspx) </span><span class="sxs-lookup"><span data-stu-id="78fa3-192">[WMI Provider for Server Events Concepts](https://technet.microsoft.com/library/ms180560.aspx) </span></span>  
 [<span data-ttu-id="78fa3-193">이벤트 알림(데이터베이스 엔진)</span><span class="sxs-lookup"><span data-stu-id="78fa3-193">Event Notifications (Database Engine)</span></span>](https://technet.microsoft.com/library/ms182602.aspx)  
  
  
