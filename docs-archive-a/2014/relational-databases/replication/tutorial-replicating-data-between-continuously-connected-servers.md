---
title: '자습서: 계속 연결된 서버 간 데이터 복제 | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- tutorials [SQL Server replication]
- replication [SQL Server], tutorials
- wizards [SQL Server replication]
ms.assetid: 7b18a04a-2c3d-4efe-a0bc-c3f92be72fd0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 415cac62112c1c1d2aa6c42ec189c2614ec03923
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660996"
---
# <a name="tutorial-replicating-data-between-continuously-connected-servers"></a><span data-ttu-id="f3b7e-102">자습서: 계속 연결된 서버 간 데이터 복제</span><span class="sxs-lookup"><span data-stu-id="f3b7e-102">Tutorial: Replicating Data Between Continuously Connected Servers</span></span>
  <span data-ttu-id="f3b7e-103">복제는 계속 연결된 서버 간에 데이터를 이동할 때 발생하는 문제를 해결하는 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="f3b7e-103">Replication is a good solution to the problem of moving data between continuously connected servers.</span></span> <span data-ttu-id="f3b7e-104">복제 마법사를 사용하면 복제 토폴로지를 쉽게 구성하고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3b7e-104">Using replication's wizards, you can easily configure and administer a replication topology.</span></span> <span data-ttu-id="f3b7e-105">이 자습서에서는 계속 연결된 서버에 대해 복제 토폴로지를 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f3b7e-105">This tutorial shows you how to configure a replication topology for continuously connected servers.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="f3b7e-106">학습 내용</span><span class="sxs-lookup"><span data-stu-id="f3b7e-106">What You Will Learn</span></span>  
 <span data-ttu-id="f3b7e-107">이 자습서에서는 트랜잭션 복제를 사용하여 한 데이터베이스의 데이터를 다른 데이터베이스에 게시하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f3b7e-107">This tutorial will show you how to publish data from one database to another using transactional replication.</span></span> <span data-ttu-id="f3b7e-108">첫 단원에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 사용하여 게시를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f3b7e-108">The first lesson shows how to use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to create a publication.</span></span> <span data-ttu-id="f3b7e-109">이후 단원에서는 구독을 만들고 이에 대해 유효성을 검사하는 방법과 대기 시간을 측정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f3b7e-109">Later lessons show how to create and validate a subscription and how to measure latency.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3b7e-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="f3b7e-110">Requirements</span></span>  
 <span data-ttu-id="f3b7e-111">이 자습서는 기본적인 데이터베이스 작업에는 익숙하지만 복제에 대한 경험은 풍부하지 않은 사용자를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f3b7e-111">This tutorial is intended for users who are familiar with basic database operations, but who have limited experience with replication.</span></span> <span data-ttu-id="f3b7e-112">이 자습서를 사용하려면 이전 자습서인 [복제용 서버 준비](tutorial-preparing-the-server-for-replication.md)를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3b7e-112">This tutorial requires that you have completed the previous tutorial, [Preparing the Server for Replication](tutorial-preparing-the-server-for-replication.md).</span></span>  
  
 <span data-ttu-id="f3b7e-113">이 자습서를 사용하려면 시스템에 다음 구성 요소가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3b7e-113">To use this tutorial, your system must have the following components:</span></span>  
  
-   <span data-ttu-id="f3b7e-114">게시자 서버(원본)</span><span class="sxs-lookup"><span data-stu-id="f3b7e-114">At the Publisher server (source):</span></span>  
  
    -   <span data-ttu-id="f3b7e-115">Express( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) 또는[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]를 제외한 [!INCLUDE[ssEW](../../includes/ssew-md.md)]의 모든 버전.</span><span class="sxs-lookup"><span data-stu-id="f3b7e-115">Any edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], except Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) or [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span> <span data-ttu-id="f3b7e-116">이들 버전은 복제 게시자가 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3b7e-116">These editions cannot be replication Publishers.</span></span>  
  
    -   [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] <span data-ttu-id="f3b7e-117">예제 데이터베이스.</span><span class="sxs-lookup"><span data-stu-id="f3b7e-117">sample database.</span></span> <span data-ttu-id="f3b7e-118">보안을 위해 예제 데이터베이스는 기본적으로 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3b7e-118">To enhance security, the sample databases are not installed by default.</span></span>  
  
-   <span data-ttu-id="f3b7e-119">구독자 서버(대상)</span><span class="sxs-lookup"><span data-stu-id="f3b7e-119">Subscriber server (destination):</span></span>  
  
    -   <span data-ttu-id="f3b7e-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 제외한 [!INCLUDE[ssEW](../../includes/ssew-md.md)]의 모든 버전.</span><span class="sxs-lookup"><span data-stu-id="f3b7e-120">Any edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], except [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span> [!INCLUDE[ssEW](../../includes/ssew-md.md)] <span data-ttu-id="f3b7e-121">는 트랜잭션 복제에서 구독자가 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3b7e-121">cannot be a Subscriber in transactional replication.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f3b7e-122">복제는 기본적으로 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 에 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3b7e-122">Replication is not installed on [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] by default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3b7e-123">에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **sysadmin** 고정 서버 역할의 멤버인 로그인을 사용 하 여 게시자 및 구독자에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3b7e-123">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you must connect to the Publisher and Subscriber using a login that is a member of the **sysadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="f3b7e-124">**이 자습서를 완료 하는 데 소요 되는 예상 시간: 30 분**</span><span class="sxs-lookup"><span data-stu-id="f3b7e-124">**Estimated time to complete this tutorial: 30 minutes.**</span></span>  
  
## <a name="lessons-in-this-tutorial"></a><span data-ttu-id="f3b7e-125">이 자습서의 단원</span><span class="sxs-lookup"><span data-stu-id="f3b7e-125">Lessons in This Tutorial</span></span>  
  
-   [<span data-ttu-id="f3b7e-126">1단원: 트랜잭션 복제를 사용하여 데이터 게시</span><span class="sxs-lookup"><span data-stu-id="f3b7e-126">Lesson 1: Publishing Data Using Transactional Replication</span></span>](lesson-1-publishing-data-using-transactional-replication.md)  
  
-   [<span data-ttu-id="f3b7e-127">2단원: 트랜잭션 게시에 구독 만들기</span><span class="sxs-lookup"><span data-stu-id="f3b7e-127">Lesson 2: Creating a Subscription to the Transactional Publication</span></span>](lesson-2-creating-a-subscription-to-the-transactional-publication.md)  
  
-   [<span data-ttu-id="f3b7e-128">3단원: 구독 유효성 검사 및 대기 시간 측정</span><span class="sxs-lookup"><span data-stu-id="f3b7e-128">Lesson 3: Validating the Subscription and Measuring Latency</span></span>](lesson-3-validating-the-subscription-and-measuring-latency.md)  
  
 [<span data-ttu-id="f3b7e-129">자습서 시작</span><span class="sxs-lookup"><span data-stu-id="f3b7e-129">Start the Tutorial</span></span>](transactional/transactional-replication.md)  
  
## <a name="see-also"></a><span data-ttu-id="f3b7e-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f3b7e-130">See Also</span></span>  
 [<span data-ttu-id="f3b7e-131">복제 프로그래밍 개념</span><span class="sxs-lookup"><span data-stu-id="f3b7e-131">Replication Programming Concepts</span></span>](concepts/replication-programming-concepts.md)  
  
  
