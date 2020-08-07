---
title: MSSQLSERVER_9001 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9001 (Database Engine error)
ms.assetid: a54de936-90c6-4845-aa96-29d32f154601
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0e61894d0d071fbdb36dcfb77895c46c61d0bbd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735276"
---
# <a name="mssqlserver_9001"></a><span data-ttu-id="80f13-102">MSSQLSERVER_9001</span><span class="sxs-lookup"><span data-stu-id="80f13-102">MSSQLSERVER_9001</span></span>
    
## <a name="details"></a><span data-ttu-id="80f13-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="80f13-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="80f13-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="80f13-104">Product Name</span></span>|<span data-ttu-id="80f13-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="80f13-105">SQL Server</span></span>|  
|<span data-ttu-id="80f13-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="80f13-106">Event ID</span></span>|<span data-ttu-id="80f13-107">9001</span><span class="sxs-lookup"><span data-stu-id="80f13-107">9001</span></span>|  
|<span data-ttu-id="80f13-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="80f13-108">Event Source</span></span>|<span data-ttu-id="80f13-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="80f13-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="80f13-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="80f13-110">Component</span></span>|<span data-ttu-id="80f13-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="80f13-111">SQLEngine</span></span>|  
|<span data-ttu-id="80f13-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="80f13-112">Symbolic Name</span></span>|<span data-ttu-id="80f13-113">LOG_NOT_AVAIL</span><span class="sxs-lookup"><span data-stu-id="80f13-113">LOG_NOT_AVAIL</span></span>|  
|<span data-ttu-id="80f13-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="80f13-114">Message Text</span></span>|<span data-ttu-id="80f13-115">데이터베이스 '%.\*ls'의 로그를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="80f13-115">The log for database '%.\*ls' is not available.</span></span> <span data-ttu-id="80f13-116">관련 오류 메시지의 이벤트 로그를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="80f13-116">Check the event log for related error messages.</span></span> <span data-ttu-id="80f13-117">모든 오류를 해결하고 데이터베이스를 다시 시작하십시오.</span><span class="sxs-lookup"><span data-stu-id="80f13-117">Resolve any errors and restart the database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="80f13-118">설명</span><span class="sxs-lookup"><span data-stu-id="80f13-118">Explanation</span></span>  
 <span data-ttu-id="80f13-119">데이터베이스 로그가 오프라인 상태가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="80f13-119">The database log was taken offline.</span></span> <span data-ttu-id="80f13-120">일반적으로 이 상태는 데이터베이스를 다시 시작해야 하는 치명적인 오류가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="80f13-120">Usually this signifies a catastrophic failure that requires the database to restart.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="80f13-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="80f13-121">User Action</span></span>  
 <span data-ttu-id="80f13-122">다른 오류를 진단하고 SQL Server 인스턴스가 아직 다시 시작되지 않은 경우 이를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="80f13-122">Diagnose other errors and restart the instance of SQL Server if it has not already restarted itself.</span></span>  
  
  
