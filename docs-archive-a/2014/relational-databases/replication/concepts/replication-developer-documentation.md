---
title: 개발자&#39;s 가이드 (복제) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: reference
helpviewer_keywords:
- developer's guide [SQL Server replication]
- programming [SQL Server replication]
- replication [SQL Server], development
ms.assetid: 7ee134ae-1cab-4a35-8017-8ac6d8fc64b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d9651aec1f02d19ea3494abf242f75049a4f33f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736243"
---
# <a name="developer39s-guide-replication"></a><span data-ttu-id="d6595-102">개발자&#39;s 가이드 (복제)</span><span class="sxs-lookup"><span data-stu-id="d6595-102">Developer&#39;s Guide (Replication)</span></span>
  <span data-ttu-id="d6595-103">복제 토폴로지를 프로그래밍 방식으로 구성, 유지 관리 및 모니터링하면 반복되는 복제 태스크를 간소화하고 복제 기반 애플리케이션의 사용자 환경을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6595-103">The ability to programmatically configure, maintain, and monitor a replication topology enables you to both simplify repeated replication tasks and improve the user experience for your replication-based applications.</span></span> <span data-ttu-id="d6595-104">복제를 프로그래밍하면 최종 사용자가 복제 저장 프로시저와 복제 에이전트 실행 파일에 대해 잘 알지 못하거나 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 구현된 복제 사용자 인터페이스를 사용하지 않아도 사용자 지정 복제 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6595-104">By programming replication, your end-users can be provided with customized replication functionalities without having to be familiar with replication stored procedures and replication agent executables or having to using the replication user interface implemented by [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="d6595-105">다음과 같은 시나리오에서는 애플리케이션에서 복제 서비스에 대한 프로그래밍 방식 액세스의 장점을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6595-105">The following are scenarios in which your applications might benefit from programmatic access to replication services:</span></span>  
  
-   <span data-ttu-id="d6595-106">사용자가 단추를 클릭했을 때 끌어오기 구독을 동기화하는 것과 같은 복제 기능을 기존 최종 사용자 애플리케이션에 추가하는 경우</span><span class="sxs-lookup"><span data-stu-id="d6595-106">Adding replication functionalities to an existing end-user application, such as synchronizing a pull subscription when the user clicks a button.</span></span>   
-   <span data-ttu-id="d6595-107">복제를 원격으로 관리하기 위한 웹 기반 사용자 인터페이스를 만드는 경우</span><span class="sxs-lookup"><span data-stu-id="d6595-107">Creating a Web-based user interface for remotely administering replication.</span></span>    
-   <span data-ttu-id="d6595-108">관리 기능의 일부만 제공하거나, 한 곳에서 여러 복제 토폴로지를 원격으로 관리하거나, 관리 및 동기화 기능을 결합하는 사용자 지정 인터페이스를 만드는 경우</span><span class="sxs-lookup"><span data-stu-id="d6595-108">Creating a custom user interface that exposes only a subset of administration functionality, can be used to remotely administer multiple replication topologies from a single location, or that combine administration and synchronization functionalities.</span></span>    
-   <span data-ttu-id="d6595-109">게시, 구독 또는 배포자에 대한 상태 모니터링 기능을 추가하여 기존의 모니터링 도구를 향상시키는 경우</span><span class="sxs-lookup"><span data-stu-id="d6595-109">Improving an existing monitoring tool by adding the ability to monitor the status of a publication, subscription, or at the Distributor.</span></span>    
-   <span data-ttu-id="d6595-110">Oracle 게시자에 대해 구독을 동기화하거나 관리하는 사용자 지정 애플리케이션을 만드는 경우</span><span class="sxs-lookup"><span data-stu-id="d6595-110">Creating a custom application to administer or synchronize subscriptions to an Oracle publisher.</span></span>    
-   <span data-ttu-id="d6595-111">병합 구독이 동기화될 때 실행되는 사용자 지정 비즈니스 규칙을 작성하는 경우</span><span class="sxs-lookup"><span data-stu-id="d6595-111">Writing customized business rules that are executed when a merge subscription is synchronized.</span></span>    
-   <span data-ttu-id="d6595-112">새 구독자를 구성할 때 반복 실행될 수 있는 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 스크립트를 생성하는 경우</span><span class="sxs-lookup"><span data-stu-id="d6595-112">Generating [!INCLUDE[tsql](../../../includes/tsql-md.md)] scripts that can be run repeated when configuring new Subscribers.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="d6595-113">에서는 복제 에이전트를 프로그래밍 방식으로 제어하고 복제 토폴로지를 프로그래밍 방식으로 관리 및 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6595-113">enables you to programmatically control replication agents and to programmatically administer and monitor a replication topology.</span></span> <span data-ttu-id="d6595-114">복제 프로그래밍에 대한 자세한 내용은 [복제 프로그래밍 개념](replication-programming-concepts.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d6595-114">To learn more about programming replication, see [Replication Programming Concepts](replication-programming-concepts.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d6595-115">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="d6595-115">In This Section</span></span>  
 [<span data-ttu-id="d6595-116">복제 프로그래밍 개념</span><span class="sxs-lookup"><span data-stu-id="d6595-116">Replication Programming Concepts</span></span>](replication-programming-concepts.md)  
 <span data-ttu-id="d6595-117">복제를 사용하는 애플리케이션을 개발하기 위한 계획 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d6595-117">Describes the planning steps to develop an application that uses replication.</span></span>  
  
 [<span data-ttu-id="d6595-118">Replication System Stored Procedures Concepts</span><span class="sxs-lookup"><span data-stu-id="d6595-118">Replication System Stored Procedures Concepts</span></span>](replication-system-stored-procedures-concepts.md)  
 <span data-ttu-id="d6595-119">시스템 저장 프로시저를 사용하여 복제 토폴로지에서 프로그래밍 방식 액세스를 제공하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d6595-119">Describes how system stored procedures can be used to proivide programmatic access in a replication topology.</span></span>  
  
 [<span data-ttu-id="d6595-120">복제 관리 개체 개념</span><span class="sxs-lookup"><span data-stu-id="d6595-120">Replication Management Objects Concepts</span></span>](replication-management-objects-concepts.md)  
 <span data-ttu-id="d6595-121">RMO(복제 관리 개체) 사용과 관련된 개념에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d6595-121">Explains the concepts for using Replication Management Objects (RMO).</span></span> <span data-ttu-id="d6595-122">RMO는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 복제 기능을 캡슐화하는 관리 코드 어셈블리입니다.</span><span class="sxs-lookup"><span data-stu-id="d6595-122">This is a managed code assembly that encapsulates replication functionalities for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="d6595-123">Replication Agent Executables Concepts</span><span class="sxs-lookup"><span data-stu-id="d6595-123">Replication Agent Executables Concepts</span></span>](replication-agent-executables-concepts.md)  
 <span data-ttu-id="d6595-124">복제 에이전트 실행 파일 사용 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d6595-124">Describes the use of Replication Agent Executable files.</span></span>  

  
  
