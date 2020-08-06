---
title: 양방향 트랜잭션 복제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- bidirectional replication
- transactional replication, bidirectional replication
- bidirectional transactional replication
ms.assetid: 98772e95-67ed-4010-8108-5113dbe709ff
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 57b18dde2e7134e0ba9eb6a9b2e8f5357d171a55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651632"
---
# <a name="bidirectional-transactional-replication"></a><span data-ttu-id="98e94-102">양방향 트랜잭션 복제</span><span class="sxs-lookup"><span data-stu-id="98e94-102">Bidirectional Transactional Replication</span></span>
  <span data-ttu-id="98e94-103">양방향 트랜잭션 복제는 두 개의 서버가 서로 변경 내용을 교환할 수 있는 특수 트랜잭션 복제 토폴로지입니다. 각 서버는 데이터를 게시한 다음 상대 서버에서 게시한 것과 동일한 데이터가 포함된 게시를 구독합니다.</span><span class="sxs-lookup"><span data-stu-id="98e94-103">Bidirectional transactional replication is a specific transactional replication topology that allows two servers to exchange changes with each other: each server publishes data and then subscribes to a publication with the same data from the other server.</span></span> <span data-ttu-id="98e94-104">**@loopback_detection** [Sp_addsubscription &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) 매개 변수를 TRUE로 설정 하 여 변경 내용이 구독자에만 전송 되 고 변경 내용이 게시자로 다시 전송 되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="98e94-104">The **@loopback_detection** parameter of [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) is set to TRUE to ensure that changes are only sent to the Subscriber and do not result in the change being sent back to the Publisher.</span></span>  
  
 <span data-ttu-id="98e94-105">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 이상 버전에서는 피어 투 피어 트랜잭션 복제에서도 이 토폴로지가 지원되지만 양방향 복제를 사용하면 성능이 향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98e94-105">In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] and later versions, this topology is also supported by peer-to-peer transactional replication, but bidirectional replication can provide improved performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98e94-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="98e94-106">See Also</span></span>  
 [<span data-ttu-id="98e94-107">@loopback_detection</span><span class="sxs-lookup"><span data-stu-id="98e94-107">Peer-to-Peer Transactional Replication</span></span>](peer-to-peer-transactional-replication.md)  
  
  
