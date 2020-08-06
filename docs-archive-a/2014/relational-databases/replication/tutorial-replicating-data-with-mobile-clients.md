---
title: '자습서: 모바일 클라이언트와의 데이터 복제 | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: af673514-30c7-403a-9d18-d01e1a095115
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2cdf8be7cb0da11f0aa1022ba656d50c10826ad2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660994"
---
# <a name="tutorial-replicating-data-with-mobile-clients"></a><span data-ttu-id="1de88-102">자습서: 모바일 클라이언트와의 데이터 복제</span><span class="sxs-lookup"><span data-stu-id="1de88-102">Tutorial: Replicating Data with Mobile Clients</span></span>
  <span data-ttu-id="1de88-103">복제는 가끔 연결되는 중앙 서버와 모바일 클라이언트간에 데이터를 이동할 때 발생하는 문제를 해결하는 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="1de88-103">Replication is a good solution to the problem of moving data between a central server and mobile clients that are only occasionally connected.</span></span> <span data-ttu-id="1de88-104">복제 마법사를 사용하면 복제 토폴로지를 쉽게 구성하고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1de88-104">Using replication's wizards, you can easily configure and administer a replication topology.</span></span> <span data-ttu-id="1de88-105">이 자습서에서는 모바일 클라이언트에 대해 복제 토폴로지를 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1de88-105">This tutorial shows you how to configure a replication topology for mobile clients.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="1de88-106">학습 내용</span><span class="sxs-lookup"><span data-stu-id="1de88-106">What You Will Learn</span></span>  
 <span data-ttu-id="1de88-107">이 자습서에서는 각 사용자가 고유하게 필터링된 데이터의 하위 집합을 얻을 수 있도록 병합 복제를 사용하여 중앙 데이터베이스의 데이터를 여러 모바일 사용자에게 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="1de88-107">In this tutorial you will use merge replication to publish data from a central database to one or more mobile users so that each user gets a uniquely filtered subset of the data.</span></span> <span data-ttu-id="1de88-108">첫 단원에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 사용하여 게시를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1de88-108">The first lesson shows how to use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to create a publication.</span></span> <span data-ttu-id="1de88-109">이후의 단원에서는 구독을 만들고 이를 동기화하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1de88-109">Later lessons show how to create and synchronize a subscription.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1de88-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="1de88-110">Requirements</span></span>  
 <span data-ttu-id="1de88-111">이 자습서는 기본적인 데이터베이스 작업에는 익숙하지만 복제에 대한 경험은 풍부하지 않은 사용자를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1de88-111">This tutorial is intended for users familiar with fundamental database operations, but who have limited experience with replication.</span></span> <span data-ttu-id="1de88-112">이 자습서를 시작하려면 이전 자습서인 [자습서: 복제용 서버 준비](tutorial-preparing-the-server-for-replication.md)를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1de88-112">Before you start this tutorial, you must complete [Tutorial: Preparing the Server for Replication](tutorial-preparing-the-server-for-replication.md).</span></span>  
  
 <span data-ttu-id="1de88-113">이 자습서를 사용하려면 시스템에 다음 구성 요소가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1de88-113">To use this tutorial, your system must have the following components installed:</span></span>  
  
-   <span data-ttu-id="1de88-114">게시자 서버(원본)</span><span class="sxs-lookup"><span data-stu-id="1de88-114">At the Publisher server (source):</span></span>  
  
    -   <span data-ttu-id="1de88-115">Express( [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) 또는[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]를 제외한 [!INCLUDE[ssEW](../../includes/ssew-md.md)]의 모든 버전.</span><span class="sxs-lookup"><span data-stu-id="1de88-115">Any edition of [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], except for Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) or [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span> <span data-ttu-id="1de88-116">이러한 버전은 복제 게시자가 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1de88-116">These editions cannot be a replication Publisher.</span></span>  
  
    -   <span data-ttu-id="1de88-117">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 예제 데이터베이스.</span><span class="sxs-lookup"><span data-stu-id="1de88-117">The [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="1de88-118">보안을 위해 예제 데이터베이스는 기본적으로 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1de88-118">To enhance security, the sample databases are not installed by default.</span></span>  
  
-   <span data-ttu-id="1de88-119">구독자 서버(대상)</span><span class="sxs-lookup"><span data-stu-id="1de88-119">Subscriber server (destination):</span></span>  
  
    -   <span data-ttu-id="1de88-120">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]을 제외한 [!INCLUDE[ssEW](../../includes/ssew-md.md)]의 모든 버전.</span><span class="sxs-lookup"><span data-stu-id="1de88-120">Any edition of [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], except for [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span> [!INCLUDE[ssEW](../../includes/ssew-md.md)] <span data-ttu-id="1de88-121">을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1de88-121">is not supported by the publication created in this tutorial.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1de88-122">복제는 기본적으로 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]에 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1de88-122">Replication is not installed by default on [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1de88-123">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서는 sysadmin 고정 서버 역할의 멤버인 로그인을 사용하여 게시자 및 구독자에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1de88-123">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you must connect to the Publisher and Subscriber using a login that is a member of the sysadmin fixed server role.</span></span>  
  
 <span data-ttu-id="1de88-124">**이 자습서를 완료 하는 데 소요 되는 예상 시간: 30 분**</span><span class="sxs-lookup"><span data-stu-id="1de88-124">**Estimated time to complete this tutorial: 30 minutes.**</span></span>  
  
## <a name="lessons-in-this-tutorial"></a><span data-ttu-id="1de88-125">이 자습서의 단원</span><span class="sxs-lookup"><span data-stu-id="1de88-125">Lessons in This Tutorial</span></span>  
  
-   [<span data-ttu-id="1de88-126">1단원: 병합 복제를 사용하여 데이터 게시</span><span class="sxs-lookup"><span data-stu-id="1de88-126">Lesson 1: Publishing Data Using Merge Replication</span></span>](lesson-1-publishing-data-using-merge-replication.md)  
  
-   [<span data-ttu-id="1de88-127">2단원: 병합 게시에 대한 구독 만들기</span><span class="sxs-lookup"><span data-stu-id="1de88-127">Lesson 2: Creating a Subscription to the Merge Publication</span></span>](lesson-2-creating-a-subscription-to-the-merge-publication.md)  
  
 [<span data-ttu-id="1de88-128">자습서 시작</span><span class="sxs-lookup"><span data-stu-id="1de88-128">Start the Tutorial</span></span>](merge/merge-replication.md)  
  
## <a name="see-also"></a><span data-ttu-id="1de88-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1de88-129">See Also</span></span>  
 [<span data-ttu-id="1de88-130">복제 프로그래밍 개념</span><span class="sxs-lookup"><span data-stu-id="1de88-130">Replication Programming Concepts</span></span>](concepts/replication-programming-concepts.md)  
  
  
