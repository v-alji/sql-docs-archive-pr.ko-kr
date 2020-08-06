---
title: MSSQLSERVER_5245 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5245 (Database Engine error)
ms.assetid: 6005c9ec-ccdd-4def-9eb4-37cdb599ddb3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f98c831642580587552bf60c604d84c38fffca8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653880"
---
# <a name="mssqlserver_5245"></a><span data-ttu-id="8e2b7-102">MSSQLSERVER_5245</span><span class="sxs-lookup"><span data-stu-id="8e2b7-102">MSSQLSERVER_5245</span></span>
    
## <a name="details"></a><span data-ttu-id="8e2b7-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="8e2b7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8e2b7-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="8e2b7-104">Product Name</span></span>|<span data-ttu-id="8e2b7-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8e2b7-105">SQL Server</span></span>|  
|<span data-ttu-id="8e2b7-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="8e2b7-106">Event ID</span></span>|<span data-ttu-id="8e2b7-107">5245</span><span class="sxs-lookup"><span data-stu-id="8e2b7-107">5245</span></span>|  
|<span data-ttu-id="8e2b7-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="8e2b7-108">Event Source</span></span>|<span data-ttu-id="8e2b7-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8e2b7-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8e2b7-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="8e2b7-110">Component</span></span>|<span data-ttu-id="8e2b7-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8e2b7-111">SQLEngine</span></span>|  
|<span data-ttu-id="8e2b7-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="8e2b7-112">Symbolic Name</span></span>|<span data-ttu-id="8e2b7-113">DBCC4_TABLE_LOCK_TIMEOUT_EXCEEDED</span><span class="sxs-lookup"><span data-stu-id="8e2b7-113">DBCC4_TABLE_LOCK_TIMEOUT_EXCEEDED</span></span>|  
|<span data-ttu-id="8e2b7-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="8e2b7-114">Message Text</span></span>|<span data-ttu-id="8e2b7-115">개체 ID O_ID(개체 'NAME'): 잠금 요청 제한 시간이 초과되었으므로 DBCC가 이 개체를 잠글 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8e2b7-115">Object ID O_ID (object 'NAME'): DBCC could not obtain a lock on this object because the lock request time-out period was exceeded.</span></span> <span data-ttu-id="8e2b7-116">이 개체를 건너뛰었으므로 처리되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8e2b7-116">This object has been skipped and will not be processed.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8e2b7-117">설명</span><span class="sxs-lookup"><span data-stu-id="8e2b7-117">Explanation</span></span>  
 <span data-ttu-id="8e2b7-118">DBCC가 지정된 개체에 대한 테이블을 잠그기 위해 기다리는 동안 잠금 제한 시간이 초과되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8e2b7-118">A lock time-out occurred while DBCC was waiting on a table lock for the specified object.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8e2b7-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="8e2b7-119">User Action</span></span>  
 <span data-ttu-id="8e2b7-120">DBCC 명령을 다시 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="8e2b7-120">Rerun the DBCC command.</span></span>  
  
  
