---
title: Performance 이벤트 범주 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Performance event category
- Performance event category [SQL Server]
- event classes [SQL Server], Performance event category
ms.assetid: 708f3585-d8be-4980-bbff-672d7c59397e
author: stevestein
ms.author: sstein
ms.openlocfilehash: b0c076a4132298797313ecbf0874d9d2d4e453cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652810"
---
# <a name="performance-event-category"></a><span data-ttu-id="e44d4-102">Performance 이벤트 범주</span><span class="sxs-lookup"><span data-stu-id="e44d4-102">Performance Event Category</span></span>
  <span data-ttu-id="e44d4-103">**Performance** 이벤트 범주를 사용하여 **Showplan** 이벤트 클래스 및 SQL DML(데이터 조작 언어) 연산자 실행으로 생성된 이벤트 클래스를 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e44d4-103">Use the **Performance** event category to monitor **Showplan** event classes and event classes that are produced from the execution of SQL data manipulation language (DML) operators.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e44d4-104">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="e44d4-104">In This Section</span></span>  
  
|<span data-ttu-id="e44d4-105">항목</span><span class="sxs-lookup"><span data-stu-id="e44d4-105">Topic</span></span>|<span data-ttu-id="e44d4-106">Description</span><span class="sxs-lookup"><span data-stu-id="e44d4-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="e44d4-107">Auto Stats 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="e44d4-107">Auto Stats Event Class</span></span>](auto-stats-event-class.md)|<span data-ttu-id="e44d4-108">인덱스 및 열 통계가 자동으로 업데이트되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e44d4-108">Indicates that an automatic updating of index and column statistics has occurred.</span></span>|  
|[<span data-ttu-id="e44d4-109">Degree of Parallelism&#40;7.0 Insert&#41; 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="e44d4-109">Degree of Parallelism &#40;7.0 Insert&#41; Event Class</span></span>](degree-of-parallelism-7-0-insert-event-class.md)|<span data-ttu-id="e44d4-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 직렬 또는 병렬 계획을 사용하여 SELECT, INSERT, UPDATE 또는 DELETE 문을 실행했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e44d4-110">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has executed a SELECT, INSERT, UPDATE, or DELETE statement using either a serial or parallel plan.</span></span> <span data-ttu-id="e44d4-111">또한 작업에 사용된 CPU 수도 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="e44d4-111">The number of CPUs used to perform the operation is also reported.</span></span>|  
|[<span data-ttu-id="e44d4-112">Performance Statistics 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="e44d4-112">Performance Statistics Event Class</span></span>](performance-statistics-event-class.md)|<span data-ttu-id="e44d4-113">실행 중인 쿼리의 성능을 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="e44d4-113">Monitors performance of the queries that are being executed.</span></span>|  
|[<span data-ttu-id="e44d4-114">Showplan All 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="e44d4-114">Showplan All Event Class</span></span>](showplan-all-event-class.md)|<span data-ttu-id="e44d4-115">SQL 문 내의 **Showplan** 연산자를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="e44d4-115">Identifies **Showplan** operators within a SQL statement.</span></span>|  
|[<span data-ttu-id="e44d4-116">Showplan All for Query Compile 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="e44d4-116">Showplan All for Query Compile Event Class</span></span>](showplan-all-for-query-compile-event-class.md)|<span data-ttu-id="e44d4-117">**Showplan** 연산자에 대한 컴파일 시간 데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e44d4-117">Displays compile time data for **Showplan** operators.</span></span>|  
|[<span data-ttu-id="e44d4-118">Showplan Statistics Profile 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="e44d4-118">Showplan Statistics Profile Event Class</span></span>](showplan-statistics-profile-event-class.md)|<span data-ttu-id="e44d4-119">쿼리의 예상 비용을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e44d4-119">Displays the estimated cost of a query.</span></span>|  
|[<span data-ttu-id="e44d4-120">Showplan XML 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="e44d4-120">Showplan XML Event Class</span></span>](showplan-xml-event-class.md)|<span data-ttu-id="e44d4-121">SQL 문 내의 **Showplan** 연산자를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="e44d4-121">Identifies the **Showplan** operators in a SQL statement.</span></span> <span data-ttu-id="e44d4-122">이 이벤트 클래스는 각 이벤트를 잘 정의된 XML 문서로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e44d4-122">The event class stores each event as a well defined XML document.</span></span>|  
|[<span data-ttu-id="e44d4-123">Showplan XML for Query Compile 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="e44d4-123">Showplan XML for Query Compile Event Class</span></span>](showplan-xml-for-query-compile-event-class.md)|<span data-ttu-id="e44d4-124">**Showplan** 연산자에 대한 컴파일 시간 데이터를 XML 형식으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e44d4-124">Displays compile time data for **Showplan** operators in XML format.</span></span>|  
|[<span data-ttu-id="e44d4-125">Showplan XML Statistics Profile 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="e44d4-125">Showplan XML Statistics Profile Event Class</span></span>](showplan-xml-statistics-profile-event-class.md)|<span data-ttu-id="e44d4-126">SQL 문에 연결된 **Showplan** 연산자를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="e44d4-126">Identifies the **Showplan** operators associated with a SQL statement.</span></span> <span data-ttu-id="e44d4-127">출력은 XML 문서입니다.</span><span class="sxs-lookup"><span data-stu-id="e44d4-127">The output is an XML document.</span></span>|  
|[<span data-ttu-id="e44d4-128">SQL:FullTextQuery 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="e44d4-128">SQL:FullTextQuery Event Class</span></span>](sql-fulltextquery-event-class.md)|<span data-ttu-id="e44d4-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 전체 텍스트 쿼리를 실행했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e44d4-129">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has executed a full-text query.</span></span>|  
|[<span data-ttu-id="e44d4-130">Plan Guide Successful 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="e44d4-130">Plan Guide Successful Event Class</span></span>](plan-guide-successful-event-class.md)|<span data-ttu-id="e44d4-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 계획 지침이 포함된 쿼리 또는 일괄 처리에 대한 실행 계획을 성공적으로 만들었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e44d4-131">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] successfully produced an execution plan for a query or batch that contained a plan guide.</span></span>|  
|[<span data-ttu-id="e44d4-132">Plan Guide Unsuccessful 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="e44d4-132">Plan Guide Unsuccessful Event Class</span></span>](plan-guide-unsuccessful-event-class.md)|<span data-ttu-id="e44d4-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 계획 지침이 포함된 쿼리 또는 일괄 처리에 대한 실행 계획을 만들지 못했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e44d4-133">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] could not produce an execution plan for a query or batch that contained a plan guide.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e44d4-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e44d4-134">See Also</span></span>  
 [<span data-ttu-id="e44d4-135">확장 이벤트</span><span class="sxs-lookup"><span data-stu-id="e44d4-135">Extended Events</span></span>](../extended-events/extended-events.md)  
  
  
