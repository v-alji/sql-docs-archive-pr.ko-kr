---
title: 구독 초기화 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshot replication [SQL Server], initializing subscriptions
- transactional replication, initializing subscriptions
- initializing subscriptions [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], about initializing subscriptions
- merge replication [SQL Server replication], initializing subscriptions
ms.assetid: d6013845-cb7a-4203-8e21-edce32f1d330
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1f024d360fdeab477ace09970b4f140a97696c2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646877"
---
# <a name="initialize-a-subscription"></a><span data-ttu-id="9f919-102">구독 초기화</span><span class="sxs-lookup"><span data-stu-id="9f919-102">Initialize a Subscription</span></span>
  <span data-ttu-id="9f919-103">복제 토폴로지의 구독자는 구독한 게시에 있는 각 아티클의 스키마 복사본과 저장 프로시저, 트리거 및 메타데이터 테이블과 같이 필요한 모든 복제 개체를 포함하도록 초기화되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f919-103">Subscribers in a replication topology must be initialized, so that they have a copy of the schema from each article in the publication they have subscribed to and any replication objects that are required, such as stored procedures, triggers, and metadata tables.</span></span> <span data-ttu-id="9f919-104">일반적으로 구독자를 초기화하면 초기 데이터 세트도 구독자로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f919-104">In addition, the Subscriber typically receives an initial dataset.</span></span> <span data-ttu-id="9f919-105">기본 초기화 메서드는 스키마, 복제 개체 및 데이터를 포함하는 전체 스냅샷을 사용하지만 전체 스냅샷 없이도 게시를 초기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f919-105">The default initialization method uses a full snapshot that includes schema, replication objects, and data, but publications can also be initialized without a full snapshot.</span></span>  
  
 <span data-ttu-id="9f919-106">자세한 내용은 [Initialize a Subscription with a Snapshot](initialize-a-subscription-with-a-snapshot.md) 및 [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9f919-106">For more information, see [Initialize a Subscription with a Snapshot](initialize-a-subscription-with-a-snapshot.md) and [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
  
