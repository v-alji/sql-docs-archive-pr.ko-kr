---
title: XTP (메모리 내 OLTP) 성능 카운터 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: fe3cbaf4-65f4-44c5-acc6-7b735cda0c5d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4363a526ada3694e92d18cac0d7abe8a26f6a92f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730571"
---
# <a name="xtp-in-memory-oltp-performance-counters"></a><span data-ttu-id="4792d-102">XTP(메모리 내 OLTP) 성능 카운터</span><span class="sxs-lookup"><span data-stu-id="4792d-102">XTP (In-Memory OLTP) Performance Counters</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4792d-103">는 메모리 내 OLTP 작업을 모니터링하기 위해 성능 모니터에서 사용할 수 있는 개체 및 카운터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4792d-103">provides objects and counters that can be used by Performance Monitor to monitor In-Memory OLTP activity.</span></span>  
  
##  <a name="xtp-in-memory-oltp-performance-objects"></a><a name="SQLServerPOs"></a><span data-ttu-id="4792d-104">XTP (메모리 내 OLTP) 성능 개체</span><span class="sxs-lookup"><span data-stu-id="4792d-104">XTP (In-Memory OLTP) Performance Objects</span></span>  
 <span data-ttu-id="4792d-105">다음 표에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4792d-105">The following table describes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects.</span></span>  
  
|<span data-ttu-id="4792d-106">성능 개체</span><span class="sxs-lookup"><span data-stu-id="4792d-106">Performance object</span></span>|<span data-ttu-id="4792d-107">Description</span><span class="sxs-lookup"><span data-stu-id="4792d-107">Description</span></span>|  
|------------------------|-----------------|  
|[<span data-ttu-id="4792d-108">XTP 커서</span><span class="sxs-lookup"><span data-stu-id="4792d-108">XTP Cursors</span></span>](../cursors.md)|<span data-ttu-id="4792d-109">XTP 커서 성능 개체에는 내부 XTP 엔진 커서와 관련된 카운터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4792d-109">The XTP Cursors performance object contains counters related to internal XTP engine cursors.</span></span> <span data-ttu-id="4792d-110">커서는 XTP 엔진이 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리를 처리하기 위해 사용하는 하위 수준의 기본 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4792d-110">Cursors are the low-level building blocks the XTP engine uses to process [!INCLUDE[tsql](../../includes/tsql-md.md)] queries.</span></span> <span data-ttu-id="4792d-111">따라서 사용자는 일반적으로 이를 직접 제어하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4792d-111">As such, you do not typically have direct control over them.</span></span>|  
|[<span data-ttu-id="4792d-112">XTP 가비지 수집</span><span class="sxs-lookup"><span data-stu-id="4792d-112">XTP Garbage Collection</span></span>](sql-server-xtp-garbage-collection.md)|<span data-ttu-id="4792d-113">XTP 가비지 수집 성능 개체에는 XTP 엔진의 가비지 수집기와 관련된 카운터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4792d-113">The XTP Garbage Collection performance object contains counters related to the XTP engine's garbage collector.</span></span>|  
|[<span data-ttu-id="4792d-114">XTP 가상 프로세서</span><span class="sxs-lookup"><span data-stu-id="4792d-114">XTP Phantom Processor</span></span>](sql-server-xtp-phantom-processor.md)|<span data-ttu-id="4792d-115">XTP 가상 프로세서 성능 개체에는 XTP 엔진의 가상 처리 하위 시스템과 관련된 카운터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4792d-115">The XTP Phantom Processor performance object contains counters related to the XTP engine's phantom processing subsystem.</span></span> <span data-ttu-id="4792d-116">이 구성 요소는 SERIALIZABLE 격리 수준에서 실행되는 트랜잭션에서 가상 행을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="4792d-116">This component is responsible for detecting phantom rows in transactions running at the SERIALIZABLE isolation level.</span></span>|  
|[<span data-ttu-id="4792d-117">XTP 스토리지</span><span class="sxs-lookup"><span data-stu-id="4792d-117">XTP Storage</span></span>](sql-server-xtp-storage.md)|<span data-ttu-id="4792d-118">XTP 스토리지 성능 개체에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 XTP 스토리지와 관련된 카운터가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4792d-118">The XTP Storage performance object contains counters related to XTP storage in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="4792d-119">XTP 트랜잭션 로그</span><span class="sxs-lookup"><span data-stu-id="4792d-119">XTP Transaction Log</span></span>](sql-server-xtp-transaction-log.md)|<span data-ttu-id="4792d-120">XTP 트랜잭션 로그 성능 개체에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 XTP 트랜잭션 로깅과 관련된 카운터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4792d-120">The XTP Transaction Log performance object contains counters related to XTP transaction logging in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="4792d-121">XTP 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="4792d-121">XTP Transactions</span></span>](sql-server-xtp-transactions.md)|<span data-ttu-id="4792d-122">XTP 트랜잭션 성능 개체에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 XTP 엔진 트랜잭션과 관련된 카운터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4792d-122">The XTP Transactions performance object contains counters related to XTP engine transactions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
  
  
