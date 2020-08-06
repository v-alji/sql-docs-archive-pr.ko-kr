---
title: TSQL 이벤트 범주 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, TSQL event category
- TSQL event category [SQL Server]
- event classes [SQL Server], TSQL event category
ms.assetid: 215f8747-64b5-4bf3-9845-d476b10cda3a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 763d5f31fd3562f54b274a74324ed4715b623a18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728283"
---
# <a name="tsql-event-category"></a><span data-ttu-id="4f993-102">TSQL 이벤트 범주</span><span class="sxs-lookup"><span data-stu-id="4f993-102">TSQL Event Category</span></span>
  <span data-ttu-id="4f993-103">**TSQL** 이벤트 범주에는 일반 TSQL 이벤트가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f993-103">The **TSQL** event category contains general TSQL events.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4f993-104">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="4f993-104">In This Section</span></span>  
  
|<span data-ttu-id="4f993-105">항목</span><span class="sxs-lookup"><span data-stu-id="4f993-105">Topic</span></span>|<span data-ttu-id="4f993-106">Description</span><span class="sxs-lookup"><span data-stu-id="4f993-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="4f993-107">Exec Prepared SQL 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="4f993-107">Exec Prepared SQL Event Class</span></span>](exec-prepared-sql-event-class.md)|<span data-ttu-id="4f993-108">SqlClient, ODBC, OLE DB 또는 DB-Library가 준비된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4f993-108">Indicates that the SqlClient, ODBC, OLE DB, or DB-Library has executed a prepared [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or statements.</span></span>|  
|[<span data-ttu-id="4f993-109">Prepare SQL 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="4f993-109">Prepare SQL Event Class</span></span>](prepare-sql-event-class.md)|<span data-ttu-id="4f993-110">SqlClient, ODBC, OLE DB 또는 DB-Library가 사용할 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 준비했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4f993-110">Indicates that SqlClient, ODBC, OLE DB, or DB-Library has prepared a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or statements for use.</span></span>|  
|[<span data-ttu-id="4f993-111">SQL:BatchCompleted 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="4f993-111">SQL:BatchCompleted Event Class</span></span>](sql-batchcompleted-event-class.md)|<span data-ttu-id="4f993-112">[!INCLUDE[tsql](../../includes/tsql-md.md)] 일괄 처리를 완료했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4f993-112">Indicates that the [!INCLUDE[tsql](../../includes/tsql-md.md)] batch has completed.</span></span>|  
|[<span data-ttu-id="4f993-113">SQL:BatchStarting 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="4f993-113">SQL:BatchStarting Event Class</span></span>](sql-batchstarting-event-class.md)|<span data-ttu-id="4f993-114">[!INCLUDE[tsql](../../includes/tsql-md.md)] 일괄 처리를 시작했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4f993-114">Indicates that the [!INCLUDE[tsql](../../includes/tsql-md.md)] batch is starting.</span></span>|  
|[<span data-ttu-id="4f993-115">SQL:StmtCompleted 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="4f993-115">SQL:StmtCompleted Event Class</span></span>](sql-stmtcompleted-event-class.md)|<span data-ttu-id="4f993-116">[!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 완료했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4f993-116">Indicates that a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement has completed.</span></span>|  
|[<span data-ttu-id="4f993-117">SQL:StmtRecompile 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="4f993-117">SQL:StmtRecompile Event Class</span></span>](sql-stmtrecompile-event-class.md)|<span data-ttu-id="4f993-118">모든 유형의 일괄 처리로 인해 발생한 문 수준의 다시 컴파일을 나타냅니다. 여기에는 저장 프로시저, 트리거, 임시 일괄 처리 및 쿼리가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f993-118">Indicates statement-level recompilations caused by all types of batches: stored procedures, triggers, ad hoc batches, and queries.</span></span>|  
|[<span data-ttu-id="4f993-119">SQL:StmtStarting 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="4f993-119">SQL:StmtStarting Event Class</span></span>](sql-stmtstarting-event-class.md)|<span data-ttu-id="4f993-120">[!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 시작했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4f993-120">Indicates that a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is starting.</span></span>|  
|[<span data-ttu-id="4f993-121">Unprepare SQL 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="4f993-121">Unprepare SQL Event Class</span></span>](unprepare-sql-event-class.md)|<span data-ttu-id="4f993-122">SqlClient, ODBC, OLE DB 또는 DB-Library가 준비된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 삭제했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4f993-122">Indicates that the SqlClient, ODBC, OLE DB, or DB-Library has deleted a prepared [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or statements.</span></span>|  
|[<span data-ttu-id="4f993-123">XQuery Static Type 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="4f993-123">XQuery Static Type Event Class</span></span>](xquery-static-type-event-class.md)|<span data-ttu-id="4f993-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 XQuery 식을 실행할 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4f993-124">Occurs when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executes an XQuery expression.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4f993-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4f993-125">See Also</span></span>  
 [<span data-ttu-id="4f993-126">Transact-SQL 참조&#40;데이터베이스 엔진&#41;</span><span class="sxs-lookup"><span data-stu-id="4f993-126">Transact-SQL Reference &#40;Database Engine&#41;</span></span>](/sql/t-sql/language-reference)  
  
  
