---
title: 확장 이벤트 세션 스크립팅 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 80f9fdde-1f13-4292-a4fc-55da826be3b4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 11adc60ae7c7e0f8b8012d06f56c83874d3708ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649667"
---
# <a name="script-an-extended-event-session"></a><span data-ttu-id="5f7a3-102">확장 이벤트 세션 스크립팅</span><span class="sxs-lookup"><span data-stu-id="5f7a3-102">Script an Extended Event Session</span></span>
  <span data-ttu-id="5f7a3-103">이 항목에서는 이벤트 세션을 스크립팅하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5f7a3-103">This topic describes how to script an event session.</span></span> <span data-ttu-id="5f7a3-104">이벤트 세션을 내보내거나 변경 또는 삭제할 수도 있고 다음에 대한 이벤트 세션을 삭제하고 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f7a3-104">You can export, alter, or drop the event session, or drop and create the event session to the following:</span></span>  
  
-   <span data-ttu-id="5f7a3-105">**새 쿼리 편집기 창**</span><span class="sxs-lookup"><span data-stu-id="5f7a3-105">**New Query Editor Window**</span></span>  
  
-   <span data-ttu-id="5f7a3-106">**파일**</span><span class="sxs-lookup"><span data-stu-id="5f7a3-106">**File**</span></span>  
  
-   <span data-ttu-id="5f7a3-107">**클립보드**</span><span class="sxs-lookup"><span data-stu-id="5f7a3-107">**Clipboard**</span></span>  
  
-   <span data-ttu-id="5f7a3-108">**에이전트 작업**</span><span class="sxs-lookup"><span data-stu-id="5f7a3-108">**Agent Job**</span></span>  
  
### <a name="to-script-an-existing-event-session"></a><span data-ttu-id="5f7a3-109">기존 이벤트 세션을 스크립팅하려면</span><span class="sxs-lookup"><span data-stu-id="5f7a3-109">To script an existing event session</span></span>  
  
1.  <span data-ttu-id="5f7a3-110">개체 탐색기에서 **관리** 노드를 확장하고 **확장 이벤트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5f7a3-110">In Object Explorer, expand the **Management** node, and then expand **Extended Events**.</span></span>  
  
2.  <span data-ttu-id="5f7a3-111">스크립팅할 세션을 마우스 오른쪽 단추로 클릭하고 **세션 스크립팅**, **CREATE**를 차례로 가리킨 다음 세션을 스크립팅할 위치를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5f7a3-111">Right-click the session you want to script, point to **Script Session as**, point to **CREATE to**, and then select where you want to script the session.</span></span>  
  
### <a name="to-script-a-new-event-session"></a><span data-ttu-id="5f7a3-112">새 이벤트 세션을 스크립팅하려면</span><span class="sxs-lookup"><span data-stu-id="5f7a3-112">To script a new event session</span></span>  
  
1.  <span data-ttu-id="5f7a3-113">개체 탐색기에서 **관리** 노드를 확장하고 **확장 이벤트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5f7a3-113">In Object Explorer, expand the **Management** node, and then expand **Extended Events**.</span></span>  
  
2.  <span data-ttu-id="5f7a3-114">**세션**을 마우스 오른쪽 단추로 클릭하고 **새 세션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f7a3-114">Right-click **Sessions**, and then click **New Session**.</span></span>  
  
3.  <span data-ttu-id="5f7a3-115">**새 세션** UI에서 이벤트 세션을 만들고 **스크립트** 드롭다운 목록에서 이벤트 세션을 스크립팅할 위치를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5f7a3-115">In the **New Session** UI, create the event session, and then select where you want to script the event session from the **Script** drop-down list.</span></span>  
  
### <a name="to-script-a-modified-event-session"></a><span data-ttu-id="5f7a3-116">수정한 이벤트 세션을 스크립팅하려면</span><span class="sxs-lookup"><span data-stu-id="5f7a3-116">To script a modified event session</span></span>  
  
1.  <span data-ttu-id="5f7a3-117">개체 탐색기에서 **관리** 노드를 확장하고 **확장 이벤트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5f7a3-117">In Object Explorer, expand the **Management** node, and then expand **Extended Events**.</span></span>  
  
2.  <span data-ttu-id="5f7a3-118">수정할 세션을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f7a3-118">Right-click the session you want to modify, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="5f7a3-119">**세션 속성** 대화 상자에서 이벤트 세션을 수정하고 **스크립트** 드롭다운 목록에서 수정한 세션을 스크립팅할 위치를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5f7a3-119">In the **Session Properties** dialog box, modify the event session, and then select where you want to script the modified session from the **Script** drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f7a3-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5f7a3-120">See Also</span></span>  
 [<span data-ttu-id="5f7a3-121">확장 이벤트</span><span class="sxs-lookup"><span data-stu-id="5f7a3-121">Extended Events</span></span>](../relational-databases/extended-events/extended-events.md)  
  
  
