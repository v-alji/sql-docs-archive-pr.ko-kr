---
title: MSSQLSERVER_18752 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18752 (Database Engine error)
ms.assetid: 234c58d8-7a1e-4b07-a64b-32a311527980
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a463e4019875f4a233ae2920f32bc2252376a41c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650074"
---
# <a name="mssqlserver_18752"></a><span data-ttu-id="81304-102">MSSQLSERVER_18752</span><span class="sxs-lookup"><span data-stu-id="81304-102">MSSQLSERVER_18752</span></span>
    
## <a name="details"></a><span data-ttu-id="81304-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="81304-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="81304-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="81304-104">Product Name</span></span>|<span data-ttu-id="81304-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="81304-105">SQL Server</span></span>|  
|<span data-ttu-id="81304-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="81304-106">Event ID</span></span>|<span data-ttu-id="81304-107">18752</span><span class="sxs-lookup"><span data-stu-id="81304-107">18752</span></span>|  
|<span data-ttu-id="81304-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="81304-108">Event Source</span></span>|<span data-ttu-id="81304-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="81304-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="81304-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="81304-110">Component</span></span>|<span data-ttu-id="81304-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="81304-111">SQLEngine</span></span>|  
|<span data-ttu-id="81304-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="81304-112">Symbolic Name</span></span>|<span data-ttu-id="81304-113">REPL_INUSE</span><span class="sxs-lookup"><span data-stu-id="81304-113">REPL_INUSE</span></span>|  
|<span data-ttu-id="81304-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="81304-114">Message Text</span></span>|<span data-ttu-id="81304-115">한 번에 하나의 로그 판독기 에이전트 또는 로그 관련 프로시저(sp_repldone, sp_replcmds 및 sp_replshowcmds)만 데이터베이스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81304-115">Only one Log Reader Agent or log-related procedure (sp_repldone, sp_replcmds, and sp_replshowcmds) can connect to a database at a time.</span></span> <span data-ttu-id="81304-116">로그 관련 프로시저를 실행한 경우 로그 판독기 에이전트를 시작하거나 다른 로그 관련 프로시저를 실행하기 전에 프로시저가 실행된 연결을 삭제하거나 해당 연결에 대해 sp_replflush를 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="81304-116">If you executed a log-related procedure, drop the connection over which the procedure was executed or execute sp_replflush over that connection before starting the Log Reader Agent or executing another log-related procedure.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="81304-117">설명</span><span class="sxs-lookup"><span data-stu-id="81304-117">Explanation</span></span>  
 <span data-ttu-id="81304-118">한 번에 하나의 로그 판독기 에이전트 또는 로그 관련 프로시저만 데이터베이스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81304-118">Only one Log Reader agent or log-related procedure can connect to a database at a time.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="81304-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="81304-119">User Action</span></span>  
 <span data-ttu-id="81304-120">동일한 게시 데이터베이스에 대해 다른 로그 판독기가 실행되고 있지 않은지, 그리고 다른 활성 연결에서 연결을 끊거나 sp_replflush를 실행하지 않고 먼저 sp_replcmds/sp_repltrans/sp_repldone을 실행하지 않았는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="81304-120">Make sure no other logreader is running for the same publishing database, and no other active connection had previously run sp_replcmds/sp_repltrans/sp_repldone without running sp_replflush afterwards or disconnecting.</span></span>  
  
  
