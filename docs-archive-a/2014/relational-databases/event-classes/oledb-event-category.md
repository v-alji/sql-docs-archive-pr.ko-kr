---
title: OLEDB 이벤트 범주 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- OLEDB event category
- SQL Server event classes, OLEDB event category
- event classes [SQL Server], OLEDB event category
ms.assetid: cf93e424-3dac-462d-b3da-92e7d0b064d4
author: stevestein
ms.author: sstein
ms.openlocfilehash: bd55294966448f8976dc20198381918e163cc0d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648397"
---
# <a name="oledb-event-category"></a><span data-ttu-id="c6194-102">OLEDB 이벤트 범주</span><span class="sxs-lookup"><span data-stu-id="c6194-102">OLEDB Event Category</span></span>
  <span data-ttu-id="c6194-103">**OLEDB** 이벤트 범주는 일반적인 OLEDB 이벤트를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c6194-103">The **OLEDB** event category contains general OLEDB events.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c6194-104">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="c6194-104">In This Section</span></span>  
  
|<span data-ttu-id="c6194-105">항목</span><span class="sxs-lookup"><span data-stu-id="c6194-105">Topic</span></span>|<span data-ttu-id="c6194-106">Description</span><span class="sxs-lookup"><span data-stu-id="c6194-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c6194-107">OLEDB Call 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="c6194-107">OLEDB Call Event Class</span></span>](oledb-call-event-class.md)|<span data-ttu-id="c6194-108">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 분산 쿼리 및 원격 저장 프로시저 실행을 위해 비데이터 또는 비**QueryInterface** OLE DB 공급자 호출을 수행했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6194-108">Indicates that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has made a non-data or non-**QueryInterface** call to an OLE DB provider for distributed queries and remote stored procedures.</span></span>|  
|[<span data-ttu-id="c6194-109">OLEDB DataRead 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="c6194-109">OLEDB DataRead Event Class</span></span>](oledb-dataread-event-class.md)|<span data-ttu-id="c6194-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 분산 쿼리 및 원격 저장 프로시저 실행을 위해 OLE DB 공급자를 호출했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6194-110">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has called an OLE DB provider for distributed queries and remote stored procedures.</span></span>|  
|[<span data-ttu-id="c6194-111">OLEDB Errors 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="c6194-111">OLEDB Errors Event Class</span></span>](oledb-errors-event-class.md)|<span data-ttu-id="c6194-112">OLE DB 공급자 호출에서 오류가 반환되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6194-112">Indicates that a call to an OLE DB provider returned an error.</span></span>|  
|[<span data-ttu-id="c6194-113">OLEDB Provider Information 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="c6194-113">OLEDB Provider Information Event Class</span></span>](oledb-provider-information-event-class.md)|<span data-ttu-id="c6194-114">분산 쿼리가 실행되어 공급자 연결에 해당하는 정보를 수집했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6194-114">Indicates that a distributed query has run and has collected information that corresponds to the provider connection.</span></span>|  
|[<span data-ttu-id="c6194-115">OLEDB QueryInterface 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="c6194-115">OLEDB QueryInterface Event Class</span></span>](oledb-queryinterface-event-class.md)|<span data-ttu-id="c6194-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 분산 쿼리 및 원격 저장 프로시저 실행을 위해 OLE DB **QueryInterface** 호출을 실행했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6194-116">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has issued an OLE DB **QueryInterface** call for distributed queries and remote stored procedures.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c6194-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6194-117">See Also</span></span>  
 [<span data-ttu-id="c6194-118">확장 이벤트</span><span class="sxs-lookup"><span data-stu-id="c6194-118">Extended Events</span></span>](../extended-events/extended-events.md)  
  
  
