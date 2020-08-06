---
title: Database 이벤트 범주 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- event classes [SQL Server], Database event category
- Database event category [SQL Server]
- SQL Server event classes, Database event category
ms.assetid: b61af738-f144-4992-b0b2-d44cb7240991
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2860e1434611393c941a639280343f736073c709
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652834"
---
# <a name="database-event-category"></a><span data-ttu-id="a6662-102">Database 이벤트 범주</span><span class="sxs-lookup"><span data-stu-id="a6662-102">Database Event Category</span></span>
  <span data-ttu-id="a6662-103">**Database** 이벤트 범주에는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]을 모니터링하는 이벤트 클래스가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6662-103">The **Database** event category contains event classes to monitor the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a6662-104">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="a6662-104">In This Section</span></span>  
  
|<span data-ttu-id="a6662-105">항목</span><span class="sxs-lookup"><span data-stu-id="a6662-105">Topic</span></span>|<span data-ttu-id="a6662-106">Description</span><span class="sxs-lookup"><span data-stu-id="a6662-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a6662-107">Data File Auto Grow 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="a6662-107">Data File Auto Grow Event Class</span></span>](data-file-auto-grow-event-class.md)|<span data-ttu-id="a6662-108">데이터 파일이 자동으로 증가함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a6662-108">Indicates that the data file grew automatically.</span></span> <span data-ttu-id="a6662-109">데이터 파일이 ALTER DATABASE를 통해 명시적으로 증가하는 경우 이 이벤트는 트리거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a6662-109">This event is not triggered if the data file is grown explicitly through ALTER DATABASE.</span></span>|  
|[<span data-ttu-id="a6662-110">Data File Auto Shrink 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="a6662-110">Data File Auto Shrink Event Class</span></span>](data-file-auto-shrink-event-class.md)|<span data-ttu-id="a6662-111">데이터 파일이 축소되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a6662-111">Indicates that the data file has been shrunk.</span></span>|  
|[<span data-ttu-id="a6662-112">데이터베이스 미러링 Connection 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="a6662-112">Database Mirroring Connection Event Class</span></span>](database-mirroring-connection-event-class.md)|<span data-ttu-id="a6662-113">데이터베이스 미러링에서 관리하는 전송 연결 상태를 보고하기 위해 생성되는 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="a6662-113">An event generated to report the status of a transport connection for database mirroring.</span></span>|  
|[<span data-ttu-id="a6662-114">Database Mirroring State Change 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="a6662-114">Database Mirroring State Change Event Class</span></span>](database-mirroring-state-change-event-class.md)|<span data-ttu-id="a6662-115">미러된 데이터베이스의 상태가 변경되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a6662-115">Indicates when the state of a mirrored database changes.</span></span>|  
|[<span data-ttu-id="a6662-116">Database Suspect Data Page 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="a6662-116">Database Suspect Data Page Event Class</span></span>](database-suspect-data-page-event-class.md)|<span data-ttu-id="a6662-117">**msdb** 데이터베이스의 **suspect_pages** 테이블에 페이지가 추가된 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a6662-117">Indicates when a page is added to the **suspect_pages** table in the **msdb** database.</span></span>|  
|[<span data-ttu-id="a6662-118">Log File Auto Grow 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="a6662-118">Log File Auto Grow Event Class</span></span>](log-file-auto-grow-event-class.md)|<span data-ttu-id="a6662-119">로그 파일이 자동으로 증가함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a6662-119">Indicates that the log file grew automatically.</span></span> <span data-ttu-id="a6662-120">이 이벤트는 ALTER DATABASE 문의 명시적인 실행으로 로그 파일이 증가하는 경우에는 트리거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a6662-120">This event is not triggered if the log file is grown explicitly through ALTER DATABASE.</span></span>|  
|[<span data-ttu-id="a6662-121">Log File Auto Shrink 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="a6662-121">Log File Auto Shrink Event Class</span></span>](log-file-auto-shrink-event-class.md)|<span data-ttu-id="a6662-122">로그 파일이 자동으로 증가함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a6662-122">Indicates that the log file grew automatically.</span></span> <span data-ttu-id="a6662-123">로그 파일이 ALTER DATABASE를 통해 명시적으로 축소되는 경우 이 이벤트는 트리거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a6662-123">This event is not triggered if the log file shrinks explicitly through ALTER DATABASE.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6662-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a6662-124">See Also</span></span>  
 [<span data-ttu-id="a6662-125">확장 이벤트</span><span class="sxs-lookup"><span data-stu-id="a6662-125">Extended Events</span></span>](../extended-events/extended-events.md)  
  
  
