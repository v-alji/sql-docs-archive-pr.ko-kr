---
title: MSSQL_ENG014144 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014144 error
ms.assetid: fdc744d5-530e-48c4-9420-cca032fd482b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0d93f06a585bcc01c52438ff7b99bbd635532402
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638678"
---
# <a name="mssql_eng014144"></a><span data-ttu-id="2aa9c-102">MSSQL_ENG014144</span><span class="sxs-lookup"><span data-stu-id="2aa9c-102">MSSQL_ENG014144</span></span>
    
## <a name="message-details"></a><span data-ttu-id="2aa9c-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="2aa9c-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2aa9c-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="2aa9c-104">Product Name</span></span>|<span data-ttu-id="2aa9c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2aa9c-105">SQL Server</span></span>|  
|<span data-ttu-id="2aa9c-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="2aa9c-106">Event ID</span></span>|<span data-ttu-id="2aa9c-107">14144</span><span class="sxs-lookup"><span data-stu-id="2aa9c-107">14144</span></span>|  
|<span data-ttu-id="2aa9c-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="2aa9c-108">Event Source</span></span>|<span data-ttu-id="2aa9c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2aa9c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2aa9c-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="2aa9c-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="2aa9c-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="2aa9c-111">Symbolic Name</span></span>||  
|<span data-ttu-id="2aa9c-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="2aa9c-112">Message Text</span></span>|<span data-ttu-id="2aa9c-113">구독자 '%s'을(를) 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2aa9c-113">Cannot drop Subscriber '%s'.</span></span> <span data-ttu-id="2aa9c-114">게시 데이터베이스 '%s'에 이 구독자에 대한 구독이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aa9c-114">There are subscriptions for it in the publication database '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2aa9c-115">설명</span><span class="sxs-lookup"><span data-stu-id="2aa9c-115">Explanation</span></span>  
 <span data-ttu-id="2aa9c-116">구독자로 구성된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대해 구성된 활성 구독이 있으면 해당 인스턴스를 구독자 역할에서 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2aa9c-116">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that is configured as a Subscriber cannot be removed from the role of Subscriber while there are active subscriptions configured for the instance.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2aa9c-117">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="2aa9c-117">User Action</span></span>  
 <span data-ttu-id="2aa9c-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 구독자 상태를 변경하기 전에 연결된 구독을 모두 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="2aa9c-118">Drop all associated subscriptions before attempting to change the Subscriber status of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance:</span></span>  
  
1.  <span data-ttu-id="2aa9c-119">게시자의 게시 데이터베이스에서 [sp_helpsubscription&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)을 실행하여 구독을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2aa9c-119">Execute [sp_helpsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql) in the publication database at the Publisher to find subscriptions.</span></span>  
  
2.  <span data-ttu-id="2aa9c-120">게시 데이터베이스에서 [sp_dropsubscription&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql)을 실행하여 구독을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="2aa9c-120">Execute [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql) in the publication database to drop subscriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aa9c-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2aa9c-121">See Also</span></span>  
 <span data-ttu-id="2aa9c-122">[오류 및 이벤트 참조&#40;복제&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="2aa9c-122">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 [<span data-ttu-id="2aa9c-123">게시 구독</span><span class="sxs-lookup"><span data-stu-id="2aa9c-123">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
