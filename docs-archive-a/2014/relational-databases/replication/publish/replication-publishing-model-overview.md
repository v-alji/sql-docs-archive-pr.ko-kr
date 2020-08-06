---
title: 복제 게시 모델 개요 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], publishing model
- subscriptions [SQL Server replication], about subscriptions
- articles [SQL Server replication]
- publications [SQL Server replication]
- Publishers [SQL Server replication], about Publishers
- Subscribers [SQL Server replication]
- Distributors [SQL Server replication], about Distributors
- Subscribers [SQL Server replication], about Subscribers
- articles [SQL Server replication], about articles
- publications [SQL Server replication], about publications
- Distributors [SQL Server replication]
ms.assetid: b9567832-e6a8-45b2-a3ed-ea12aa002f4b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a6b6bd555cf87a8dcb334db2c44e17ed99aa845d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651650"
---
# <a name="replication-publishing-model-overview"></a><span data-ttu-id="0b732-102">복제 게시 모델 개요</span><span class="sxs-lookup"><span data-stu-id="0b732-102">Replication Publishing Model Overview</span></span>
  <span data-ttu-id="0b732-103">복제는 복제 토폴로지의 구성 요소를 나타내는 데 게시자, 배포자, 구독자, 게시, 아티클 및 구독을 포함하는 게시 관련 산업의 메타포를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-103">Replication uses a publishing industry metaphor to represent the components in a replication topology, which include Publisher, Distributor, Subscribers, publications, articles, and subscriptions.</span></span> <span data-ttu-id="0b732-104">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 복제를 잡지의 개념으로 생각하면 이해가 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-104">It is helpful to think of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication in terms of a magazine:</span></span>

-   <span data-ttu-id="0b732-105">잡지사(게시자)에서는 하나 이상의 출판물(게시)을 생산합니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-105">A magazine publisher produces one or more publications</span></span>

-   <span data-ttu-id="0b732-106">출판물(게시)에는 기사(아티클)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-106">A publication contains articles</span></span>

-   <span data-ttu-id="0b732-107">잡지사(게시자)에서는 잡지를 직접 배포하거나 배급업자(배포자)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-107">The publisher either distributes the magazine directly or uses a distributor</span></span>

-   <span data-ttu-id="0b732-108">구독자는 각자가 구독하는 출판물(게시)을 받아 봅니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-108">Subscribers receive publications to which they have subscribed</span></span>

 <span data-ttu-id="0b732-109">복제를 이해하는 데 잡지 메타포가 도움이 되기는 하지만 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 복제에는 이 메타포에 나타나지 않은 기능, 특히 구독자가 업데이트를 하고 게시자가 게시의 아티클에 대해 증분 변경 내용을 보낼 수 있는 기능이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-109">Although the magazine metaphor is useful for understanding replication, it is important to note that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication includes functionality that is not represented in this metaphor, particularly the ability for a Subscriber to make updates and for a Publisher to send out incremental changes to the articles in a publication.</span></span>

 <span data-ttu-id="0b732-110">*복제 토폴로지* 는 서버와 데이터 복사본 간의 관계를 정의하고 서버 간 데이터 흐름 방식을 결정하는 논리를 명확히 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-110">A *replication topology* defines the relationship between servers and copies of data and clarifies the logic that determines how data flows between servers.</span></span> <span data-ttu-id="0b732-111">게시자와 구독자 간 데이터 복사 및 이동을 담당하는 여러 복제 프로세스( *에이전트*)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-111">There are several replication processes (referred to as *agents*) that are responsible for copying and moving data between the Publisher and Subscribers.</span></span> <span data-ttu-id="0b732-112">다음 그림에서는 복제와 관련된 구성 요소 및 프로세스를 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-112">The following illustration is an overview of the components and processes involved in replication.</span></span>

 <span data-ttu-id="0b732-113">![복제 구성 요소 및 데이터 흐름](../media/replintro1.gif "복제 구성 요소 및 데이터 흐름")</span><span class="sxs-lookup"><span data-stu-id="0b732-113">![Replication components and data flow](../media/replintro1.gif "Replication components and data flow")</span></span>

## <a name="publisher"></a><span data-ttu-id="0b732-114">게시자</span><span class="sxs-lookup"><span data-stu-id="0b732-114">Publisher</span></span>
 <span data-ttu-id="0b732-115">게시자는 복제를 통해 데이터를 다른 위치에서 사용할 수 있도록 만드는 데이터베이스 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-115">The Publisher is a database instance that makes data available to other locations through replication.</span></span> <span data-ttu-id="0b732-116">게시자는 각각 논리적으로 관련된 개체 집합 및 복제할 데이터를 정의하는 게시를 하나 이상 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-116">The Publisher can have one or more publications, each defining a logically related set of objects and data to replicate.</span></span>

## <a name="distributor"></a><span data-ttu-id="0b732-117">배포자</span><span class="sxs-lookup"><span data-stu-id="0b732-117">Distributor</span></span>
 <span data-ttu-id="0b732-118">배포자는 하나 이상의 게시자와 연결된 복제별 데이터에 대한 저장소 역할을 하는 데이터베이스 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-118">The Distributor is a database instance that acts as a store for replication specific data associated with one or more Publishers.</span></span> <span data-ttu-id="0b732-119">각 게시자는 배포자에서 단일 데이터베이스(배포 데이터베이스)와 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-119">Each Publisher is associated with a single database (known as a distribution database) at the Distributor.</span></span> <span data-ttu-id="0b732-120">배포 데이터베이스는 복제 상태 데이터와 게시에 대한 메타데이터를 저장하고 경우에 따라서는 게시자에서 구독자로 이동하는 데이터에 대한 큐 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-120">The distribution database stores replication status data, metadata about the publication, and, in some cases, acts as a queue for data moving from the Publisher to the Subscribers.</span></span> <span data-ttu-id="0b732-121">대부분의 경우 단일 데이터베이스 서버 인스턴스는 게시자와 배포자 역할을 모두 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-121">In many cases, a single database server instance acts as both the Publisher and the Distributor.</span></span> <span data-ttu-id="0b732-122">이를 *로컬 배포자*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-122">This is known as a *local Distributor*.</span></span> <span data-ttu-id="0b732-123">게시자 및 배포자가 서로 다른 데이터베이스 서버 인스턴스에 구성되어 있는 경우에는 배포자를 *원격 배포자*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-123">When the Publisher and the Distributor are configured on separate database server instances, the Distributor is known as a *remote Distributor*.</span></span>

## <a name="subscribers"></a><span data-ttu-id="0b732-124">게시자 속성</span><span class="sxs-lookup"><span data-stu-id="0b732-124">Subscribers</span></span>
 <span data-ttu-id="0b732-125">구독자는 복제된 데이터를 수신하는 데이터베이스 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-125">A Subscriber is a database instance that receives replicated data.</span></span> <span data-ttu-id="0b732-126">구독자는 여러 게시자 및 게시로부터 데이터를 수신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-126">A Subscriber can receive data from multiple Publishers and publications.</span></span> <span data-ttu-id="0b732-127">선택한 복제 유형에 따라 구독자는 데이터 변경 내용을 게시자에 다시 전달하거나 데이터를 다른 구독자로 다시 게시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-127">Depending on the type of replication chosen, the Subscriber can also pass data changes back to the Publisher or republish the data to other Subscribers.</span></span>

## <a name="article"></a><span data-ttu-id="0b732-128">아티클</span><span class="sxs-lookup"><span data-stu-id="0b732-128">Article</span></span>
 <span data-ttu-id="0b732-129">아티클은 게시에 포함된 데이터베이스 개체를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-129">An article identifies a database object that is included in a publication.</span></span> <span data-ttu-id="0b732-130">게시는 테이블, 뷰, 저장 프로시저 및 기타 개체를 포함한 여러 유형의 아티클을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-130">A publication can contain different types of articles, including tables, views, stored procedures, and other objects.</span></span> <span data-ttu-id="0b732-131">테이블이 아티클로 게시되면 필터를 사용하여 구독자로 보낼 데이터의 열 및 행을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-131">When tables are published as articles, filters can be used to restrict the columns and rows of the data sent to Subscribers.</span></span>

## <a name="publication"></a><span data-ttu-id="0b732-132">게시</span><span class="sxs-lookup"><span data-stu-id="0b732-132">Publication</span></span>
 <span data-ttu-id="0b732-133">게시는 하나의 데이터베이스에서 하나 이상의 아티클을 모은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-133">A publication is a collection of one or more articles from one database.</span></span> <span data-ttu-id="0b732-134">여러 아티클을 게시로 그룹화하면 논리적으로 관련된 데이터베이스 개체 집합 및 단위로 복제된 데이터를 쉽게 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-134">The grouping of multiple articles into a publication makes it easier to specify a logically related set of database objects and data that are replicated as a unit.</span></span>

## <a name="subscription"></a><span data-ttu-id="0b732-135">Subscription</span><span class="sxs-lookup"><span data-stu-id="0b732-135">Subscription</span></span>
 <span data-ttu-id="0b732-136">구독은 구독자에게 게시 복사본을 배달해 줄 것을 요청하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-136">A subscription is a request for a copy of a publication to be delivered to a Subscriber.</span></span> <span data-ttu-id="0b732-137">구독은 어떤 게시를 언제 어디서 받을 것인지를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-137">The subscription defines what publication will be received, where, and when.</span></span> <span data-ttu-id="0b732-138">밀어넣기와 끌어오기의 두 가지 구독 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b732-138">There are two types of subscriptions: push and pull.</span></span> <span data-ttu-id="0b732-139">밀어넣기 및 끌어오기 구독에 대한 자세한 내용은 [게시 구독](../subscribe-to-publications.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0b732-139">For more information about push and pull subscriptions, see [Subscribe to Publications](../subscribe-to-publications.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0b732-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0b732-140">See Also</span></span>
 <span data-ttu-id="0b732-141">[복제 에이전트 개요](../agents/replication-agents-overview.md) [복제 유형](../types-of-replication.md) [AlwaysOn 가용성 그룹 (SQL Server)에 대 한 복제 구성](../../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) [AlwaysOn 게시 데이터베이스를 유지 관리 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/maintaining-an-always-on-publication-database-sql-server.md)</span><span class="sxs-lookup"><span data-stu-id="0b732-141">[Replication Agents Overview](../agents/replication-agents-overview.md) [Types of Replication](../types-of-replication.md) [Configure Replication for AlwaysOn Availability Groups (SQL Server)](../../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) [Maintaining an AlwaysOn Publication Database &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/maintaining-an-always-on-publication-database-sql-server.md)</span></span>


