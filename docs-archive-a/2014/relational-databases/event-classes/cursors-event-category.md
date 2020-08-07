---
title: Cursors 이벤트 범주 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Cursors event category [SQL Server]
- event classes [SQL Server], Cursors event category
- SQL Server event classes, Cursors event category
ms.assetid: 752e0695-b464-4720-93be-5b9b53b7ab21
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3b31ff8ccb9c662a2f0ea54adc9cd2d466103be2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731579"
---
# <a name="cursors-event-category"></a><span data-ttu-id="ba3f3-102">Cursors 이벤트 범주</span><span class="sxs-lookup"><span data-stu-id="ba3f3-102">Cursors Event Category</span></span>
  <span data-ttu-id="ba3f3-103">**Cursors** 이벤트 범주에는 커서 동작을 모니터링하는 데 사용하는 이벤트 클래스가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba3f3-103">The **Cursors** event category contains event classes that are used to monitor the behavior of cursors.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ba3f3-104">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="ba3f3-104">In This Section</span></span>  
  
|<span data-ttu-id="ba3f3-105">항목</span><span class="sxs-lookup"><span data-stu-id="ba3f3-105">Topic</span></span>|<span data-ttu-id="ba3f3-106">Description</span><span class="sxs-lookup"><span data-stu-id="ba3f3-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ba3f3-107">CursorClose 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="ba3f3-107">CursorClose Event Class</span></span>](cursorclose-event-class.md)|<span data-ttu-id="ba3f3-108">API(애플리케이션 프로그래밍 인터페이스) 커서에서 발생하는 커서 닫기 이벤트에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ba3f3-108">Describes cursor close events that occur in application programming interface (API) cursors.</span></span>|  
|[<span data-ttu-id="ba3f3-109">CursorExecute 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="ba3f3-109">CursorExecute Event Class</span></span>](cursorexecute-event-class.md)|<span data-ttu-id="ba3f3-110">API 커서에서 발생하는 커서 실행 이벤트에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ba3f3-110">Describes cursor execute events that occur in API cursors.</span></span>|  
|[<span data-ttu-id="ba3f3-111">CursorImplicitConversion 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="ba3f3-111">CursorImplicitConversion Event Class</span></span>](cursorimplicitconversion-event-class.md)|<span data-ttu-id="ba3f3-112">API 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 커서에서 발생하는 커서 암시적 변환 이벤트에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ba3f3-112">Describes cursor implicit conversion events that occur in API or [!INCLUDE[tsql](../../includes/tsql-md.md)] cursors.</span></span>|  
|[<span data-ttu-id="ba3f3-113">CursorOpen 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="ba3f3-113">CursorOpen Event Class</span></span>](cursoropen-event-class.md)|<span data-ttu-id="ba3f3-114">API 커서에서 발생하는 커서 열기 이벤트에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ba3f3-114">Describes cursor open events that occur in API cursors.</span></span>|  
|[<span data-ttu-id="ba3f3-115">CursorPrepare 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="ba3f3-115">CursorPrepare Event Class</span></span>](cursorprepare-event-class.md)|<span data-ttu-id="ba3f3-116">API 커서에서 발생하는 커서 준비 이벤트에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ba3f3-116">Describes cursor prepare events that occur in API cursors.</span></span>|  
|[<span data-ttu-id="ba3f3-117">CursorRecompile 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="ba3f3-117">CursorRecompile Event Class</span></span>](cursorrecompile-event-class.md)|<span data-ttu-id="ba3f3-118">API 커서에서 발생하는 커서 다시 컴파일 이벤트에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ba3f3-118">Describes cursor recompile events that occur in API cursors.</span></span>|  
|[<span data-ttu-id="ba3f3-119">CursorUnprepare 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="ba3f3-119">CursorUnprepare Event Class</span></span>](cursorunprepare-event-class.md)|<span data-ttu-id="ba3f3-120">API 커서에서 발생하는 커서 준비 취소 이벤트에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ba3f3-120">Describes cursor unprepare events that occur in API cursors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba3f3-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ba3f3-121">See Also</span></span>  
 [<span data-ttu-id="ba3f3-122">확장 이벤트</span><span class="sxs-lookup"><span data-stu-id="ba3f3-122">Extended Events</span></span>](../extended-events/extended-events.md)  
  
  
