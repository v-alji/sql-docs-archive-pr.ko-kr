---
title: MSSQL_ENG020572 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020572 error
ms.assetid: 636566db-ffcf-4109-8c11-15b8c7cb9cd9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5762f160e119012f4fdc0ca1a205ba0ecf690378
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661053"
---
# <a name="mssql_eng020572"></a><span data-ttu-id="7927a-102">MSSQL_ENG020572</span><span class="sxs-lookup"><span data-stu-id="7927a-102">MSSQL_ENG020572</span></span>
    
## <a name="message-details"></a><span data-ttu-id="7927a-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="7927a-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7927a-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="7927a-104">Product Name</span></span>|<span data-ttu-id="7927a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="7927a-105">SQL Server</span></span>|  
|<span data-ttu-id="7927a-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="7927a-106">Event ID</span></span>|<span data-ttu-id="7927a-107">20572</span><span class="sxs-lookup"><span data-stu-id="7927a-107">20572</span></span>|  
|<span data-ttu-id="7927a-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="7927a-108">Event Source</span></span>|<span data-ttu-id="7927a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7927a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7927a-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="7927a-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="7927a-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="7927a-111">Symbolic Name</span></span>||  
|<span data-ttu-id="7927a-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="7927a-112">Message Text</span></span>|<span data-ttu-id="7927a-113">게시 '%s'의 아티클 '%s'에 대한 구독자 '%s'의 구독이 유효성 검사 실패 후 다시 초기화되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7927a-113">Subscriber '%s' subscription to article '%s' in publication '%s' has been reinitialized after a validation failure.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7927a-114">설명</span><span class="sxs-lookup"><span data-stu-id="7927a-114">Explanation</span></span>  
 <span data-ttu-id="7927a-115">구독자의 데이터를 게시자의 데이터와 비교하여 유효성을 검사했는데 데이터가 일치하지 않아 유효성 검사가 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="7927a-115">The data at the Subscriber was validated against the data at the Publisher, and the data did not match; therefore validation failed.</span></span> <span data-ttu-id="7927a-116">유효성 검사를 수행해야 함을 지정할 경우 유효성 검사가 실패하면 구독을 다시 초기화해야 한다는 옵션을 선택했습니다.</span><span class="sxs-lookup"><span data-stu-id="7927a-116">When you specified that validation should be performed, you selected the option that a subscription should be reinitialized if validation failed.</span></span> <span data-ttu-id="7927a-117">구독을 다시 초기화하면 구독자에서 새 스냅샷을 적용하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7927a-117">Reinitializing a subscription involves applying a new snapshot at the Subscriber.</span></span> <span data-ttu-id="7927a-118">유효성 검사에 대한 자세한 내용은 [Validate Replicated Data](validate-data-at-the-subscriber.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7927a-118">For more information about validation, see [Validate Replicated Data](validate-data-at-the-subscriber.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7927a-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="7927a-119">User Action</span></span>  
 <span data-ttu-id="7927a-120">새 스냅샷이 구독자에 적용된 후에는 게시자와 구독자의 데이터가 일치할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7927a-120">Data at the Publisher and Subscriber will match after the new snapshot is applied at the Subscriber.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7927a-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7927a-121">See Also</span></span>  
 [<span data-ttu-id="7927a-122">오류 및 이벤트 참조&#40;복제&#41;</span><span class="sxs-lookup"><span data-stu-id="7927a-122">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
