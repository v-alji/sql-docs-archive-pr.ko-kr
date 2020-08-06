---
title: 서버 이벤트에 대 한 WMI 공급자 이해 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- architecture [WMI]
- SQL Server Agent [WMI]
- WMI Provider for Server Events, about WMI Provider for Server Events
ms.assetid: 8fd7bd18-76d0-4b28-8fee-8ad861441ab2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ef583d479e473b6f5e71fef59f2221697248b45f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739634"
---
# <a name="understanding-the-wmi-provider-for-server-events"></a><span data-ttu-id="0fb9e-102">서버 이벤트용 WMI 공급자 이해</span><span class="sxs-lookup"><span data-stu-id="0fb9e-102">Understanding the WMI Provider for Server Events</span></span>
  <span data-ttu-id="0fb9e-103">서버 이벤트용 WMI 공급자는 WMI(Windows Management Instrumentation)를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 이벤트를 모니터링할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-103">The WMI Provider for Server Events lets you use the Windows Management Instrumentation (WMI) to monitor events in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0fb9e-104">이 공급자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 관리 WMI 개체로 전환하여 작동됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-104">The provider works by turning [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] into a managed WMI object.</span></span> <span data-ttu-id="0fb9e-105">WMI에서는 이 공급자를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 이벤트 알림을 생성할 수 있는 모든 이벤트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-105">Any event that can generate an event notification in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can be leveraged by the WMI by using this provider.</span></span> <span data-ttu-id="0fb9e-106">또한 WMI와 상호 작용하는 관리 애플리케이션인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 이러한 이벤트에 응답할 수 있기 때문에 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 처리하던 이벤트보다 다양한 이벤트를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-106">Additionally, as a management application that interacts with the WMI, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can respond to these events, increasing the scope of events covered by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent over earlier releases.</span></span>

 <span data-ttu-id="0fb9e-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트와 같은 관리 애플리케이션에서는 서버 이벤트용 WMI 공급자를 통해 WQL(WMI Query Language) 문을 실행하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이벤트에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-107">Management applications such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events using the WMI Provider for Server Events by issuing WMI Query Language (WQL) statements.</span></span> <span data-ttu-id="0fb9e-108">WQL은 몇 가지 WMI 관련 확장 기능이 포함된 SQL(구조적 쿼리 언어)의 단순화된 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-108">WQL is a simplified subset of structured query language (SQL), with some WMI-specific extensions.</span></span> <span data-ttu-id="0fb9e-109">WQL을 사용할 경우 애플리케이션에서는 특정 데이터베이스나 데이터베이스 개체에 대해 이벤트 유형을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-109">In using WQL, an application retrieves an event type against a specific database or database object.</span></span> <span data-ttu-id="0fb9e-110">서버 이벤트용 WMI 공급자는 쿼리를 이벤트 알림으로 변환하여 대상 데이터베이스의 이벤트 알림을 효율적으로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-110">The WMI Provider for Server Events translates the query into an event notification, effectively creating an event notification in the target database.</span></span> <span data-ttu-id="0fb9e-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 이벤트 알림이 작동하는 방식은 [서버 이벤트용 WMI 공급자 개념](https://technet.microsoft.com/library/ms180560.aspx)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-111">For more information about how event notifications work in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [WMI Provider for Server Events Concepts](https://technet.microsoft.com/library/ms180560.aspx).</span></span> <span data-ttu-id="0fb9e-112">쿼리할 수 이벤트는 [서버 이벤트용 WMI 공급자 클래스 및 라이브러리](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-classes-and-properties.md)에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-112">The events that can be queried are listed in [WMI Provider for Server Events Classes and Properties](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-classes-and-properties.md).</span></span>

 <span data-ttu-id="0fb9e-113">이벤트 알림으로 하여금 메시지를 보내도록 트리거하는 이벤트가 발생하면 메시지는 **SQL/Notifications/ProcessWMIEventProviderNotification/v1.0** 이라는 **msdb**에 미리 정의된 대상 서비스로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-113">When an event occurs that triggers the event notification to send a message, the message goes to a predefined target service in **msdb** that is named **SQL/Notifications/ProcessWMIEventProviderNotification/v1.0**.</span></span> <span data-ttu-id="0fb9e-114">대상 서비스는 **WMIEventProviderNotificationQueue** 라는 **msdb**에 미리 정의된 큐에 이 이벤트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-114">The service puts the event into a predefined queue in **msdb** that is named **WMIEventProviderNotificationQueue**.</span></span> <span data-ttu-id="0fb9e-115">서비스와 큐는 모두 공급자가에 처음 연결할 때 동적으로 만들어집니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . 그런 다음 공급자는이 큐에서 이벤트 데이터를 읽고 MOF (managed object format)로 변환한 후 응용 프로그램에 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-115">(Both the service and the queue are created dynamically by the provider when it first connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].) The provider then reads the event data from this queue and transforms it into managed object format (MOF) before returning it to the application.</span></span> <span data-ttu-id="0fb9e-116">다음 그림에서 이 프로세스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-116">The following illustration shows this process.</span></span>

 <span data-ttu-id="0fb9e-117">![서버 이벤트용 WMI 공급자 흐름 다이어그램](../../../2014/database-engine/dev-guide/media/wmi-provider-functional-spec.gif "서버 이벤트용 WMI 공급자 흐름 다이어그램")</span><span class="sxs-lookup"><span data-stu-id="0fb9e-117">![Flow diagram of the WMI Provider for Server Events](../../../2014/database-engine/dev-guide/media/wmi-provider-functional-spec.gif "Flow diagram of the WMI Provider for Server Events")</span></span>

 <span data-ttu-id="0fb9e-118">예를 들어 다음 WQL 쿼리를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-118">For example, consider the following WQL Query:</span></span>

```
SELECT * FROM DDL_DATABASE_LEVEL_EVENTS
WHERE DatabaseName = 'AdventureWorks'
```

 <span data-ttu-id="0fb9e-119">이 쿼리에 대한 응답으로 서버 이벤트용 WMI 공급자는 대상 데이터베이스에 해당 이벤트 알림을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-119">In response to this query, the WMI Provider for Server Events creates the equivalent event notification in the target database:</span></span>

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

 <span data-ttu-id="0fb9e-120">이 예에서 `SQLWEP_76CF38C1_18BB_42DD_A7DC_C8820155B0E9` 는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 접두사와 GUID로 구성된 `SQLWEP_` 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-120">In this example, `SQLWEP_76CF38C1_18BB_42DD_A7DC_C8820155B0E9` is a [!INCLUDE[tsql](../../includes/tsql-md.md)] identifier that is made up of the prefix `SQLWEP_` and a GUID.</span></span> <span data-ttu-id="0fb9e-121">`SQLWEP`는 각 식별자의 GUID를 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-121">`SQLWEP` creates a new GUID for each identifier.</span></span> <span data-ttu-id="0fb9e-122">`A7E5521A-1CA6-4741-865D-826F804E5135` 절의 `TO SERVICE` 값은 **msdb** 데이터베이스의 Broker 인스턴스를 식별하는 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-122">The value `A7E5521A-1CA6-4741-865D-826F804E5135` in the `TO SERVICE` clause is the GUID that identifies the broker instance in the **msdb** database.</span></span>

 <span data-ttu-id="0fb9e-123">WQL로 작업하는 방법은 [서버 이벤트용 WMI 공급자에 WQL 사용](https://technet.microsoft.com/library/ms180524\(v=sql.105\).aspx)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-123">For more information about how to work with WQL, see [Using WQL with the WMI Provider for Server Events](https://technet.microsoft.com/library/ms180524\(v=sql.105\).aspx).</span></span>

 <span data-ttu-id="0fb9e-124">관리 애플리케이션에서는 공급자가 정의한 WMI 네임스페이스에 연결하여 서버 이벤트용 WMI 공급자를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-124">Management applications direct the WMI Provider for Server Events to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by connecting to a WMI namespace that is defined by the provider.</span></span> <span data-ttu-id="0fb9e-125">Windows WMI 서비스는 이 네임스페이스를 공급자 DLL인 Sqlwep.dll에 매핑하여 메모리에 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-125">The Windows WMI service maps this namespace to the provider DLL, Sqlwep.dll, and loads it into memory.</span></span> <span data-ttu-id="0fb9e-126">공급자는 각 인스턴스에 대 한 서버 이벤트에 대 한 WMI 네임 스페이스를 관리 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 하며 형식은 \\ \\ \\ 입니다. *root*\Microsoft\SqlServer\ServerEvents \\ *instance_name*입니다. 여기서 *instance_name* 은 MSSQLSERVER입니다.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-126">The provider manages a WMI namespace for Server Events for each instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and the format is: \\\\.\\*root*\Microsoft\SqlServer\ServerEvents\\*instance_name*, where *instance_name* defaults to MSSQLSERVER.</span></span> <span data-ttu-id="0fb9e-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스의 WMI 네임스페이스에 연결하는 방법은 [서버 이벤트용 WMI 공급자에 WQL 사용](https://technet.microsoft.com/library/ms180524\(v=sql.105\).aspx)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-127">For more information about how to connect to a WMI namespace for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Using WQL with the WMI Provider for Server Events](https://technet.microsoft.com/library/ms180524\(v=sql.105\).aspx).</span></span>

 <span data-ttu-id="0fb9e-128">공급자 DLL인 Sqlwep.dll은 서버에 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 수에 관계없이 서버 운영 체제의 WMI 호스트 서비스에 한 번만 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-128">The provider DLL, Sqlwep.dll, is loaded only one time into the WMI host service of the operating system of the server, regardless of how many instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are on the server.</span></span>

 <span data-ttu-id="0fb9e-129">서버 이벤트용 WMI 공급자를 사용하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 관리 애플리케이션에 대한 예는 [예제: 서버 이벤트용 WMI 공급자를 사용하여 SQL Server 에이전트 경고 만들기](https://technet.microsoft.com/library/ms186385.aspx)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-129">For an example of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent management application that uses the WMI Provider for Server Events, see [Sample: Creating a SQL Server Agent Alert Using the WMI Provider for Server Events](https://technet.microsoft.com/library/ms186385.aspx).</span></span> <span data-ttu-id="0fb9e-130">관리 코드에서 서버 이벤트용 WMI 공급자를 사용하는 관리 애플리케이션에 대한 예는 [예제: 관리 코드에서 WMI 이벤트 공급자 사용](https://technet.microsoft.com/library/ms179315.aspx)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0fb9e-130">For an example of a management application that uses the WMI Provider for Server Events in managed code, see [Sample: Using the WMI Event Provider in Managed Code](https://technet.microsoft.com/library/ms179315.aspx).</span></span> <span data-ttu-id="0fb9e-131">SDK에 대 한 자세한 내용은 SDK에도 제공 됩니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0fb9e-131">More information is also available about WMI in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.</span></span>

## <a name="see-also"></a><span data-ttu-id="0fb9e-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0fb9e-132">See Also</span></span>
 [<span data-ttu-id="0fb9e-133">서버 이벤트용 WMI 공급자 개념</span><span class="sxs-lookup"><span data-stu-id="0fb9e-133">WMI Provider for Server Events Concepts</span></span>](https://technet.microsoft.com/library/ms180560.aspx)


