---
title: 데이터베이스 크기 예측 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- space allocation [SQL Server], database size
- calculating database size
- increasing database size
- database size [SQL Server], estimating
- predicting database size
- size [SQL Server], databases
- estimating database size
- designing databases [SQL Server], estimating size
ms.assetid: 5b240161-eba4-44b0-946c-61a8fc00fc8c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6e3a390c4ade2c2dc08f67d2d1461955516e866c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650095"
---
# <a name="estimate-the-size-of-a-database"></a><span data-ttu-id="28d71-102">데이터베이스 크기 예측</span><span class="sxs-lookup"><span data-stu-id="28d71-102">Estimate the Size of a Database</span></span>
  <span data-ttu-id="28d71-103">데이터베이스를 디자인할 때는 데이터베이스가 데이터로 가득 찰 때 얼마나 커질 수 있는지를 추정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28d71-103">When you design a database, you may have to estimate how large the database will be when filled with data.</span></span> <span data-ttu-id="28d71-104">데이터베이스의 크기를 추정하면 다음을 수행하는 데 필요한 하드웨어 구성을 결정하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28d71-104">Estimating the size of the database can help you determine the hardware configuration you will require to do the following:</span></span>  
  
-   <span data-ttu-id="28d71-105">애플리케이션에서 필요한 성능을 확보합니다.</span><span class="sxs-lookup"><span data-stu-id="28d71-105">Achieve the performance required by your applications.</span></span>  
  
-   <span data-ttu-id="28d71-106">데이터 및 인덱스를 저장하는 데 필요한 물리적 디스크 공간을 충분히 확보합니다.</span><span class="sxs-lookup"><span data-stu-id="28d71-106">Guarantee the appropriate physical amount of disk space required to store the data and indexes.</span></span>  
  
 <span data-ttu-id="28d71-107">또한 데이터베이스의 크기를 추정하면 데이터베이스 디자인을 수정해야 할지 여부를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28d71-107">Estimating the size of a database can also help you determine whether the database design needs refining.</span></span> <span data-ttu-id="28d71-108">예를 들어 예상 크기가 회사에서 실제로 구현하기에 너무 큰 경우에는 정규화가 더 필요하다는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28d71-108">For example, you may determine that the estimated size of the database is too large to implement in your organization and that more normalization is required.</span></span> <span data-ttu-id="28d71-109">반대로 예상 크기가 생각보다 더 작을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28d71-109">Conversely, the estimated size may be smaller than expected.</span></span> <span data-ttu-id="28d71-110">이 경우 데이터베이스를 비정규화하여 쿼리 성능을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28d71-110">This would allow you to denormalize the database to improve query performance.</span></span>  
  
 <span data-ttu-id="28d71-111">데이터베이스의 크기를 추정하려면 각 테이블의 크기를 따로 추정한 다음 그 값을 더하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28d71-111">To estimate the size of a database, estimate the size of each table individually and then add the values obtained.</span></span> <span data-ttu-id="28d71-112">테이블의 크기는 테이블에 인덱스가 있는지 여부와 인덱스 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="28d71-112">The size of a table depends on whether the table has indexes and, if they do, what type of indexes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="28d71-113">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="28d71-113">In This Section</span></span>  
  
|<span data-ttu-id="28d71-114">항목</span><span class="sxs-lookup"><span data-stu-id="28d71-114">Topic</span></span>|<span data-ttu-id="28d71-115">Description</span><span class="sxs-lookup"><span data-stu-id="28d71-115">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="28d71-116">테이블 크기 예측</span><span class="sxs-lookup"><span data-stu-id="28d71-116">Estimate the Size of a Table</span></span>](estimate-the-size-of-a-table.md)|<span data-ttu-id="28d71-117">테이블 및 연결된 인덱스에 데이터를 저장하는 데 필요한 공간을 예측하는 단계와 필요한 계산을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="28d71-117">Defines the steps and calculations needed to estimate the amount of space required to store the data in a table and associated indexes.</span></span>|  
|[<span data-ttu-id="28d71-118">힙 크기 예측</span><span class="sxs-lookup"><span data-stu-id="28d71-118">Estimate the Size of a Heap</span></span>](estimate-the-size-of-a-heap.md)|<span data-ttu-id="28d71-119">힙에 데이터를 저장하는 데 필요한 공간을 예측하는 단계와 필요한 계산을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="28d71-119">Defines the steps and calculations needed to estimate the amount of space required to store the data in a heap.</span></span> <span data-ttu-id="28d71-120">힙은 클러스터형 인덱스가 없는 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="28d71-120">A heap is a table that does not have a clustered index.</span></span>|  
|[<span data-ttu-id="28d71-121">클러스터형 인덱스의 크기 예측</span><span class="sxs-lookup"><span data-stu-id="28d71-121">Estimate the Size of a Clustered Index</span></span>](estimate-the-size-of-a-clustered-index.md)|<span data-ttu-id="28d71-122">클러스터형 인덱스에 데이터를 저장하는 데 필요한 공간을 예측하는 단계와 필요한 계산을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="28d71-122">Defines the steps and calculations needed to estimate the amount of space required to store the data in a clustered index.</span></span>|  
|[<span data-ttu-id="28d71-123">비클러스터형 인덱스의 크기 예측</span><span class="sxs-lookup"><span data-stu-id="28d71-123">Estimate the Size of a Nonclustered Index</span></span>](estimate-the-size-of-a-nonclustered-index.md)|<span data-ttu-id="28d71-124">비클러스터형 인덱스에 데이터를 저장하는 데 필요한 공간을 예측하는 단계와 필요한 계산을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="28d71-124">Defines the steps and calculations needed to estimate the amount of space required to store the data in a nonclustered index.</span></span>|  
  
  
