---
title: 확장 이벤트 세션 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 34b1e95a-a80e-4aca-9201-abde47f2ca74
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: aadc79dc4287faf57ed3b50a989e3d042cdb9b1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651248"
---
# <a name="create-an-extended-events-session"></a><span data-ttu-id="bee90-102">확장 이벤트 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="bee90-102">Create an Extended Events Session</span></span>
  <span data-ttu-id="bee90-103">쿼리 편집기를 사용하거나 개체 탐색기에서 확장 이벤트 세션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bee90-103">You can create an Extended Events session by using the Query Editor, or you can create a session in Object Explorer.</span></span> <span data-ttu-id="bee90-104">개체 탐색기 확장 이벤트는 이벤트 세션 데이터를 생성, 수정 및 보는 데 사용할 수 있는 두 가지 사용자 인터페이스를 제공 합니다. 마법사는 이벤트 세션 만들기 프로세스를 안내 하는 마법사와 고급 구성 옵션을 제공 하는 새 세션 UI를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="bee90-104">In Object Explorer, Extended Events provides two user interfaces you can use to create, modify, and view event session data - a wizard that guides you through the event session creation process, and a New Session UI that provides more advanced configuration options.</span></span> <span data-ttu-id="bee90-105">확장 이벤트 세션을 만들어 SQL Server 추적을 진단하면 다음과 같은 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bee90-105">You can create Extended Events sessions to diagnose SQL Server tracing, which enables you to resolve issues such as the following:</span></span>  
  
-   <span data-ttu-id="bee90-106">가장 비용이 많이 드는 쿼리 찾기</span><span class="sxs-lookup"><span data-stu-id="bee90-106">Find your most expensive queries</span></span>  
  
-   <span data-ttu-id="bee90-107">래치 경합의 근본 원인 찾기</span><span class="sxs-lookup"><span data-stu-id="bee90-107">Find root causes of latch contention</span></span>  
  
-   <span data-ttu-id="bee90-108">다른 쿼리를 차단하는 쿼리 찾기</span><span class="sxs-lookup"><span data-stu-id="bee90-108">Find a query that is blocking other queries</span></span>  
  
-   <span data-ttu-id="bee90-109">쿼리 재컴파일에 의해 발생하는 과도한 CPU 사용 문제 해결</span><span class="sxs-lookup"><span data-stu-id="bee90-109">Troubleshoot excessive CPU usage caused by query recompilation</span></span>  
  
-   <span data-ttu-id="bee90-110">교착 상태 해결</span><span class="sxs-lookup"><span data-stu-id="bee90-110">Troubleshoot deadlocks</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bee90-111">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="bee90-111">In This Section</span></span>  
 [<span data-ttu-id="bee90-112">쿼리 편집기를 사용하여 확장 이벤트 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="bee90-112">Create an Extended Events Session Using Query Editor</span></span>](../../2014/database-engine/create-an-extended-events-session-using-query-editor.md)  
  
 [<span data-ttu-id="bee90-113">마법사 &#40;개체 탐색기를 사용 하 여 확장 이벤트 세션을 만듭니다&#41;</span><span class="sxs-lookup"><span data-stu-id="bee90-113">Create an Extended Events Session Using the Wizard &#40;Object Explorer&#41;</span></span>](../ssms/object/object-explorer.md)  
  
 [<span data-ttu-id="bee90-114">새 세션 대화 상자를 사용하여 확장 이벤트 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="bee90-114">Create an Extended Events Session Using the New Session Dialog</span></span>](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md)  
  
  
