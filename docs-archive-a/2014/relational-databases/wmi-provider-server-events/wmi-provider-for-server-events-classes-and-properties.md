---
title: 서버 이벤트 용 WMI 공급자 클래스 및 속성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- event classes [WMI]
- WMI Provider for Server Events, events listed
- classes [WMI]
ms.assetid: e2916cd7-a3ed-41e6-97b4-2ee060754cbe
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 471e77cb7afa4e6aed441dcbbc8b3b70064f6737
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739615"
---
# <a name="wmi-provider-for-server-events-classes-and-properties"></a><span data-ttu-id="e166d-102">서버 이벤트용 WMI 공급자 클래스 및 속성</span><span class="sxs-lookup"><span data-stu-id="e166d-102">WMI Provider for Server Events Classes and Properties</span></span>
  <span data-ttu-id="e166d-103">서버 이벤트용 WMI 공급자의 프로그래밍 모델을 구성하는 서버 이벤트에는</span><span class="sxs-lookup"><span data-stu-id="e166d-103">The following server events make up the programming model for the WMI Provider for Server Events.</span></span> <span data-ttu-id="e166d-104">공급자에 대해 WQL 쿼리를 실행하여 쿼리할 수 있는 두 가지 주요 범주의 이벤트인</span><span class="sxs-lookup"><span data-stu-id="e166d-104">There are two main categories of events that can be queried by issuing WQL queries against the provider.</span></span> <span data-ttu-id="e166d-105">DDL(데이터 정의 언어) 이벤트와 추적 이벤트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e166d-105">These are data definition language (DDL) events and trace events.</span></span> <span data-ttu-id="e166d-106">QUEUE_ACTIVATION 및 BROKER_QUEUE_DISABLED Service Broker 이벤트도 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e166d-106">The QUEUE_ACTIVATION and BROKER_QUEUE_DISABLED service broker events can also be queried.</span></span> <span data-ttu-id="e166d-107">다음 트리 다이어그램의 포함 특성에 유의하십시오.</span><span class="sxs-lookup"><span data-stu-id="e166d-107">Note the inclusive nature of the following tree diagrams.</span></span> <span data-ttu-id="e166d-108">예를 들어 DDL_ASSEMBLY_EVENTS 이벤트는 모든 ALTER_ASSEMBLY, CREATE_ASSEMBLY 및 DROP_ASSEMBLY 이벤트를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e166d-108">The DDL_ASSEMBLY_EVENTS event, for example, includes any ALTER_ASSEMBLY, CREATE_ASSEMBLY, and DROP_ASSEMBLY event.</span></span> <span data-ttu-id="e166d-109">마찬가지로 TRC_FULL_TEXT 이벤트는 모든 FT_CRAWL_ABORTED, FT_CRAWL_STARTED 및 FT_CRAWL_STOPPED 이벤트를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e166d-109">Similarly, the TRC_FULL_TEXT event includes any FT_CRAWL_ABORTED, FT_CRAWL_STARTED, and FT_CRAWL_STOPPED event.</span></span> <span data-ttu-id="e166d-110">ALL_EVENTS는 모든 DDL 이벤트, 추적 이벤트, QUEUE_ACTIVATION 및 BROKER_QUEUE_DISABLED를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e166d-110">ALL_EVENTS covers all DDL events, trace events, QUEUE_ACTIVATION, and BROKER_QUEUE_DISABLED.</span></span>  
  
 <span data-ttu-id="e166d-111">이벤트나 이벤트 그룹에서 쿼리할 수 있는 속성에 대해서는 이벤트 스키마를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e166d-111">To learn which properties can be queried from an event or event group, refer to the event schema.</span></span> <span data-ttu-id="e166d-112">기본적으로 이벤트 스키마는 다음 디렉터리에 설치 됩니다. [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)] Tools\Binn\schemas\sqlserver\2006\11\events\events.xsd.</span><span class="sxs-lookup"><span data-stu-id="e166d-112">By default, the event schema is installed in the following directory: [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]Tools\Binn\schemas\sqlserver\2006\11\events\events.xsd.</span></span>  
  
 <span data-ttu-id="e166d-113">또는에 게시 된 이벤트 스키마를 참조할 수 있습니다 [https://schemas.microsoft.com/sqlserver](https://go.microsoft.com/fwlink/?linkid=43100) .</span><span class="sxs-lookup"><span data-stu-id="e166d-113">Alternatively, you can refer to the event schema published at [https://schemas.microsoft.com/sqlserver](https://go.microsoft.com/fwlink/?linkid=43100).</span></span>  
  
 <span data-ttu-id="e166d-114">예를 들어 ALTER_DATABASE 이벤트를 참조하면 부모 이벤트가 DDL_SERVER_LEVEL_EVENTS이고 속성은 `TSQLCommand`와 `DatabaseName`이라는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e166d-114">For example, by referring to the ALTER_DATABASE event, you will learn that its parent event is DDL_SERVER_LEVEL_EVENTS and its properties are `TSQLCommand` and `DatabaseName`.</span></span> <span data-ttu-id="e166d-115">또한 이 이벤트는 `SQLInstance`, `PostTime`, `ComputerName`, `SPID` 및 `LoginName` 속성을 상속하며</span><span class="sxs-lookup"><span data-stu-id="e166d-115">The event also inherits the properties `SQLInstance`, `PostTime`, `ComputerName`, `SPID`, and `LoginName`.</span></span> <span data-ttu-id="e166d-116">자식 이벤트가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e166d-116">The event has no children events.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e166d-117">DDL과 같은 작업을 수행하는 시스템 저장 프로시저에서 이벤트 알림을 발생시킬 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e166d-117">System stored procedures that perform DDL-like operations can also fire event notifications.</span></span> <span data-ttu-id="e166d-118">이벤트 알림을 테스트하여 실행된 시스템 저장 프로시저에 대한 응답을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e166d-118">Test your event notifications to determine their responses to system stored procedures that are run.</span></span> <span data-ttu-id="e166d-119">예를 들어 CREATE TYPE 문과 **sp_addtype** 저장 프로시저는 모두 CREATE_TYPE 이벤트에 대해 생성 되는 이벤트 알림을 발생 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="e166d-119">For example, the CREATE TYPE statement and **sp_addtype** stored procedure will both fire an event notification that is created on a CREATE_TYPE event.</span></span> <span data-ttu-id="e166d-120">자세한 내용은[DDL Events](../../relational-databases/triggers/ddl-events.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e166d-120">For more information, see[DDL Events](../../relational-databases/triggers/ddl-events.md).</span></span>  
  
 <span data-ttu-id="e166d-121">**데이터 정의 언어 이벤트 및 이벤트 그룹**</span><span class="sxs-lookup"><span data-stu-id="e166d-121">**Data Definition Language Events and Event Groups**</span></span>  
  
 <span data-ttu-id="e166d-122">![서버 이벤트용 WMI 공급자의 이벤트 트리](../../../2014/database-engine/dev-guide/media/sql-wmi-ddl-events-ktm.gif "서버 이벤트용 WMI 공급자의 이벤트 트리")</span><span class="sxs-lookup"><span data-stu-id="e166d-122">![WMI Provider for Server Events Event Tree](../../../2014/database-engine/dev-guide/media/sql-wmi-ddl-events-ktm.gif "WMI Provider for Server Events Event Tree")</span></span>  
  
 <span data-ttu-id="e166d-123">**추적 이벤트 및 이벤트 그룹**</span><span class="sxs-lookup"><span data-stu-id="e166d-123">**Trace Events and Event Groups**</span></span>  
  
 <span data-ttu-id="e166d-124">![추적 이벤트 및 이벤트 그룹](../../../2014/database-engine/dev-guide/media/sql-wmi-trc-all-events.gif "추적 이벤트 및 이벤트 그룹")</span><span class="sxs-lookup"><span data-stu-id="e166d-124">![Trace events and event groups](../../../2014/database-engine/dev-guide/media/sql-wmi-trc-all-events.gif "Trace events and event groups")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e166d-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e166d-125">See Also</span></span>  
 <span data-ttu-id="e166d-126">[서버 이벤트 용 WMI 공급자 개념](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="e166d-126">[WMI Provider for Server Events Concepts](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md) </span></span>  
 [<span data-ttu-id="e166d-127">서버 이벤트용 WMI 공급자에 WQL 사용</span><span class="sxs-lookup"><span data-stu-id="e166d-127">Using WQL with the WMI Provider for Server Events</span></span>](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md)  
  
  
