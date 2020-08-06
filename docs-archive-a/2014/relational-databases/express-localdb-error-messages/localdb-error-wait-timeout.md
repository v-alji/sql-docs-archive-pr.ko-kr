---
title: LOCALDB_ERROR_WAIT_TIMEOUT | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: e5b55efa-daa1-4c39-aa71-eeb7707ed601
author: stevestein
ms.author: sstein
ms.openlocfilehash: e3668b32fb48a3e12c33dc15224467307c696af4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728268"
---
# <a name="localdb_error_wait_timeout"></a><span data-ttu-id="6ded6-102">LOCALDB_ERROR_WAIT_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6ded6-102">LOCALDB_ERROR_WAIT_TIMEOUT</span></span>
    
## <a name="details"></a><span data-ttu-id="6ded6-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="6ded6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6ded6-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="6ded6-104">Product Name</span></span>|<span data-ttu-id="6ded6-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6ded6-105">SQL Server</span></span>|  
|<span data-ttu-id="6ded6-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="6ded6-106">Event ID</span></span>|<span data-ttu-id="6ded6-107">277</span><span class="sxs-lookup"><span data-stu-id="6ded6-107">277</span></span>|  
|<span data-ttu-id="6ded6-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="6ded6-108">Event Source</span></span>|<span data-ttu-id="6ded6-109">SQL Server 로컬 데이터베이스 런타임 12.0</span><span class="sxs-lookup"><span data-stu-id="6ded6-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="6ded6-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="6ded6-110">Component</span></span>|<span data-ttu-id="6ded6-111">로컬 데이터베이스 런타임 API</span><span class="sxs-lookup"><span data-stu-id="6ded6-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="6ded6-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="6ded6-112">Message Text</span></span>|<span data-ttu-id="6ded6-113">로컬 데이터베이스 인스턴스 API 메서드 내에서 시간 초과가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="6ded6-113">Timeout occurred inside the Local Database instance API method.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6ded6-114">설명</span><span class="sxs-lookup"><span data-stu-id="6ded6-114">Explanation</span></span>  
 <span data-ttu-id="6ded6-115">동기화 잠금을 획득하려고 시도하는 중에 시간 초과가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="6ded6-115">A time-out occurred while trying to acquire synchronization locks.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6ded6-116">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="6ded6-116">User Action</span></span>  
 <span data-ttu-id="6ded6-117">요청한 작업을 다시 시도하십시오.</span><span class="sxs-lookup"><span data-stu-id="6ded6-117">Retry the requested operation again.</span></span>  
  
  
