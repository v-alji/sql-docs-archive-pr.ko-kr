---
title: 병합 복제의 게시된 데이터 필터링 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication [SQL Server replication], filtering published data
- replication [SQL Server], filtering published data
ms.assetid: 46c5023d-7a3b-4455-becc-e159fcb5d6c4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ad9ad45a64f57a6bef8255373180ea943af9893f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638710"
---
# <a name="filter-published-data-for-merge-replication"></a><span data-ttu-id="6b805-102">병합 복제의 게시된 데이터 필터링</span><span class="sxs-lookup"><span data-stu-id="6b805-102">Filter Published Data for Merge Replication</span></span>
  <span data-ttu-id="6b805-103">다른 복제 유형으로 정의할 수 있는 정적 행 필터와 열 필터 이외에 병합 복제는 매개 변수가 있는 행 필터 및 조인 필터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6b805-103">In addition to the static row filters and column filters you can define with other types of replication, merge replication offers parameterized row filters and join filters.</span></span> <span data-ttu-id="6b805-104">정적 행 필터와 열 필터에 대한 자세한 내용은 [게시된 데이터 필터링](../publish/filter-published-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6b805-104">For more information about static row filters and column filters, see [Filter Published Data](../publish/filter-published-data.md).</span></span>  
  
 <span data-ttu-id="6b805-105">병합 복제는 모바일 사용자를 지원하는 여러 애플리케이션에서 사용됩니다. 이러한 애플리케이션에는 대개 많은 구독이 있으며 각 구독은 고유한 데이터 집합을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="6b805-105">Merge replication is used in many applications that support mobile users; these applications usually have a large number of subscriptions with each subscription receiving a unique data set.</span></span> <span data-ttu-id="6b805-106">매개 변수가 있는 필터를 조인 필터와 함께 사용하면 관리자는 하나의 게시 또는 적은 수의 게시를 설정한 다음에도 다양한 데이터 집합을 사용자에게 제공할 수 있으므로 여러 게시를 만들 때 발생하는 관리 오버헤드를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b805-106">Parameterized filters combined with join filters allow an administrator to set up one publication (or at most a small number of publications) and yet provide different data sets to users, reducing the management overhead introduced by creating multiple publications.</span></span>  
  
-   <span data-ttu-id="6b805-107">매개 변수가 있는 필터를 사용하면 게시를 여러 개 만들지 않아도 데이터의 다른 파티션을 다른 구독자에게 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b805-107">Parameterized filters allow different partitions of data to be sent to different Subscribers without requiring multiple publications to be created.</span></span> <span data-ttu-id="6b805-108">예를 들어 지정된 판매 담당자의 데이터가 해당 담당자에게만 복제되도록 테이블을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b805-108">For example, a table can be filtered so that data for a given sales representative is replicated only to that representative.</span></span> <span data-ttu-id="6b805-109">매개 변수가 있는 필터의 다양한 옵션을 활용하여 성능을 최적화하고 데이터 및 애플리케이션 요구 사항에 가장 적합한 필터링을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b805-109">Parameterized filters have a variety of options that allow you to tailor filtering to optimize performance and best match your data and application requirements.</span></span> <span data-ttu-id="6b805-110">자세한 내용은 [매개 변수가 있는 행 필터](parameterized-filters-parameterized-row-filters.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6b805-110">For more information, see [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md).</span></span>  
  
-   <span data-ttu-id="6b805-111">조인 필터는 일반적으로 필터를 관련 테이블로 확장하기 위해 매개 변수가 있는 필터와 함께 사용되며 정적 필터와 함께 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b805-111">Join filters are typically used in conjunction with parameterized filters to extend filtering to related tables (they can also be used in conjunction with static filters).</span></span> <span data-ttu-id="6b805-112">예를 들어 판매 담당자는 일반적으로 고객 테이블 및 주문 테이블과 같은 다른 테이블에 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6b805-112">For example, the sales representative typically has data in other tables such as customer and order tables.</span></span> <span data-ttu-id="6b805-113">판매 담당자가 자신의 고객 및 고객의 주문에 대한 정보만을 받을 수 있도록 이러한 정보를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b805-113">This data can be filtered so the sales representative receives only the data on her customers and her customers' orders.</span></span> <span data-ttu-id="6b805-114">자세한 내용은 [Join Filters](join-filters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6b805-114">For more information, see [Join Filters](join-filters.md).</span></span>  
  
 <span data-ttu-id="6b805-115">필터는 행 식별을 위해 복제에 사용된 `rowguidcol`을 포함하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b805-115">A filter must not include the `rowguidcol` used by replication to identify rows.</span></span> <span data-ttu-id="6b805-116">기본적으로 이 열은 병합 복제를 설정할 때 추가된 열이며 이름은 **rowguid**입니다.</span><span class="sxs-lookup"><span data-stu-id="6b805-116">By default this is the column added at the time you set up merge replication and is named **rowguid**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b805-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6b805-117">See Also</span></span>  
 [<span data-ttu-id="6b805-118">데이터 및 데이터베이스 개체 게시</span><span class="sxs-lookup"><span data-stu-id="6b805-118">Publish Data and Database Objects</span></span>](../publish/publish-data-and-database-objects.md)  
  
  
