---
title: SQL Server Service Broker | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.SSBQUEUEPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBREMSVCBINDPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBMSGTYPEPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBROUTEPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBCONTRACTPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBSERVICEPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBPRIORITYPROPERTIES.GENERAL.F1
helpviewer_keywords:
- Broker See Service Broker
- SQL Server Service Broker
- Service Broker
ms.assetid: 8b8b3b57-fd46-44de-9a4e-e3a8e3999c1e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3d3877dd8311e0fe5b65bd4b1e7f9c40fbd84751
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740384"
---
# <a name="sql-server-service-broker"></a><span data-ttu-id="e8569-102">SQL Server Service Broker</span><span class="sxs-lookup"><span data-stu-id="e8569-102">SQL Server Service Broker</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="e8569-103">[!INCLUDE[ssSB](../../includes/sssb-md.md)]에서 메시징 및 큐 응용 프로그램에 대 한 기본 지원을 제공 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8569-103">[!INCLUDE[ssSB](../../includes/sssb-md.md)] provides native support for messaging and queuing applications in the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="e8569-104">이러한 지원을 통해 개발자는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 구성 요소를 사용하여 서로 다른 데이터베이스 간에 통신하는 복잡한 애플리케이션을 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8569-104">This makes it easier for developers to create sophisticated applications that use the [!INCLUDE[ssDE](../../includes/ssde-md.md)] components to communicate between disparate databases.</span></span> <span data-ttu-id="e8569-105">개발자는 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 를 사용하여 신뢰할 수 있는 분산 애플리케이션을 간단하게 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8569-105">Developers can use [!INCLUDE[ssSB](../../includes/sssb-md.md)] to easily build distributed and reliable applications.</span></span>  
  
 <span data-ttu-id="e8569-106">[!INCLUDE[ssSB](../../includes/sssb-md.md)] 를 사용하는 애플리케이션 개발자는 복잡한 통신 및 메시징 내부 사항을 프로그래밍하지 않고도 데이터 작업을 여러 데이터베이스에 분산시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8569-106">Application developers who use [!INCLUDE[ssSB](../../includes/sssb-md.md)] can distribute data workloads across several databases without programming complex communication and messaging internals.</span></span> <span data-ttu-id="e8569-107">이렇게 하면 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 가 대화 컨텍스트에서 통신 경로를 처리하므로 개발 및 테스트 작업이 줄어들 뿐만 아니라</span><span class="sxs-lookup"><span data-stu-id="e8569-107">This reduces development and test work because [!INCLUDE[ssSB](../../includes/sssb-md.md)] handles the communication paths in the context of a conversation.</span></span> <span data-ttu-id="e8569-108">성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8569-108">It also improves performance.</span></span> <span data-ttu-id="e8569-109">예를 들어, 웹 사이트를 지원하는 프런트 엔드 데이터베이스는 정보를 기록하고 프로세스를 많이 사용하는 태스크를 백 엔드 데이터베이스의 큐로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8569-109">For example, front-end databases supporting Web sites can record information and send process intensive tasks to queue in back-end databases.</span></span> [!INCLUDE[ssSB](../../includes/sssb-md.md)] <span data-ttu-id="e8569-110">는 모든 태스크가 트랜잭션 컨텍스트에서 관리되도록 하여 안정성과 기술 일관성을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="e8569-110">ensures that all tasks are managed in the context of transactions to assure reliability and technical consistency.</span></span>  
  
## <a name="where-is-the-documentation-for-service-broker"></a><span data-ttu-id="e8569-111">Service Broker 설명서의 위치</span><span class="sxs-lookup"><span data-stu-id="e8569-111">Where is the documentation for Service Broker?</span></span>  
 <span data-ttu-id="e8569-112">[!INCLUDE[ssSB](../../includes/sssb-md.md)] 에 대한 참조 설명서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 설명서에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8569-112">The reference documentation for [!INCLUDE[ssSB](../../includes/sssb-md.md)] is included in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] documentation.</span></span> <span data-ttu-id="e8569-113">이 참조 설명서는 다음과 같은 섹션으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8569-113">This reference documentation includes the following sections:</span></span>  
  
-   <span data-ttu-id="e8569-114">CREATE, ALTER 및 DROP 문에 대한 [DDL&#40;데이터 정의 언어&#41; 문&#40;Transact-SQL&#41;](/sql/odbc/reference/develop-app/ddl-statements)</span><span class="sxs-lookup"><span data-stu-id="e8569-114">[Data Definition Language &#40;DDL&#41; Statements &#40;Transact-SQL&#41;](/sql/odbc/reference/develop-app/ddl-statements) for CREATE, ALTER, and DROP statements</span></span>  
  
-   [<span data-ttu-id="e8569-115">Service Broker 카탈로그 뷰&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e8569-115">Service Broker Catalog Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/service-broker-catalog-views-transact-sql)  
  
-   [<span data-ttu-id="e8569-116">Service Broker 관련 동적 관리 뷰&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e8569-116">Service Broker Related Dynamic Management Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql)  
  
-   [<span data-ttu-id="e8569-117">ssbdiagnose 유틸리티&#40;Service Broker&#41;</span><span class="sxs-lookup"><span data-stu-id="e8569-117">ssbdiagnose Utility &#40;Service Broker&#41;</span></span>](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
 <span data-ttu-id="e8569-118">[개념과 개발 및 관리 태스크에 대한 자세한 내용은](https://go.microsoft.com/fwlink/?LinkId=231312) 이전에 게시된 설명서 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e8569-118">See the [previously published documentation](https://go.microsoft.com/fwlink/?LinkId=231312) for [!INCLUDE[ssSB](../../includes/sssb-md.md)] concepts and for development and management tasks.</span></span> <span data-ttu-id="e8569-119">이 설명서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 의 변경 사항이 적기 때문에 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]설명서에서 다시 작성되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="e8569-119">This documentation is not reproduced in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] documentation due to the small number of changes in [!INCLUDE[ssSB](../../includes/sssb-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="whats-new-in-service-broker"></a><span data-ttu-id="e8569-120">Service Broker의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="e8569-120">What's new in Service Broker</span></span>  
 <span data-ttu-id="e8569-121">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에 도입된 큰 변경 내용은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8569-121">No significant changes are introduced in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  <span data-ttu-id="e8569-122">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]에서의 변경 내용은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e8569-122">The following changes were introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span>  
  
### <a name="messages-can-be-sent-to-multiple-target-services-multicast"></a><span data-ttu-id="e8569-123">메시지를 여러 대상 서비스에 보낼 수 있음(멀티캐스트)</span><span class="sxs-lookup"><span data-stu-id="e8569-123">Messages can be sent to multiple target services (multicast)</span></span>  
 <span data-ttu-id="e8569-124">[SEND&#40;Transact-SQL&#41;](/sql/t-sql/statements/send-transact-sql) 문의 구문은 여러 대화 핸들을 지원하여 멀티캐스트를 설정하기 위해 확장되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8569-124">The syntax of the [SEND &#40;Transact-SQL&#41;](/sql/t-sql/statements/send-transact-sql) statement has been extended to enable multicast by supporting multiple conversation handles.</span></span>  
  
### <a name="queues-expose-the-message-enqueued-time"></a><span data-ttu-id="e8569-125">메시지가 큐에 유지된 시간이 큐에서 노출됨</span><span class="sxs-lookup"><span data-stu-id="e8569-125">Queues expose the message enqueued time</span></span>  
 <span data-ttu-id="e8569-126">메시지가 큐에 유지된 시간을 보여 주는 **message_enqueue_time**이라는 새 열이 큐에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8569-126">Queues have a new column, **message_enqueue_time**, that shows how long a message has been in the queue.</span></span>  
  
### <a name="poison-message-handling-can-be-disabled"></a><span data-ttu-id="e8569-127">포이즌 메시지 처리를 해제할 수 있음</span><span class="sxs-lookup"><span data-stu-id="e8569-127">Poison message handling can be disabled</span></span>  
 <span data-ttu-id="e8569-128">[CREATE QUEUE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-queue-transact-sql) 및 [ALTER QUEUE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-queue-transact-sql) 문은 이제 `POISON_MESSAGE_HANDLING (STATUS = ON | OFF)` 절을 추가하여 포이즌 메시지 처리를 설정하거나 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8569-128">The [CREATE QUEUE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-queue-transact-sql) and [ALTER QUEUE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-queue-transact-sql) statements now have the ability to enable or disable poison message handling by adding the clause, `POISON_MESSAGE_HANDLING (STATUS = ON | OFF)`.</span></span> <span data-ttu-id="e8569-129">카탈로그 뷰 **sys.service_queues** 에는 이제 포이즌 메시지가 설정되었는지, 아니면 해제되었는지를 나타내는 **is_poison_message_handling_enabled** 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8569-129">The catalog view **sys.service_queues** now has the column **is_poison_message_handling_enabled** to indicate whether poison message is enabled or disabled.</span></span>  
  
### <a name="alwayson-support-in-service-broker"></a><span data-ttu-id="e8569-130">Service Broker의 AlwaysOn 지원</span><span class="sxs-lookup"><span data-stu-id="e8569-130">AlwaysOn support in Service Broker</span></span>  
 <span data-ttu-id="e8569-131">자세한 내용은 [AlwaysOn 가용성 그룹이 포함된 Service Broker&#40;SQL Server&#41;](../availability-groups/windows/service-broker-with-always-on-availability-groups-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8569-131">For more information, see [Service Broker with AlwaysOn Availability Groups &#40;SQL Server&#41;](../availability-groups/windows/service-broker-with-always-on-availability-groups-sql-server.md).</span></span>  
  
  
