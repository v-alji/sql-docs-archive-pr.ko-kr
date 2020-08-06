---
title: LOCALDB_ERROR_INSTANCE_ALREADY_SHARED | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: 35b4d6fa-ebb9-49d3-aaab-d4e37b6f3760
author: stevestein
ms.author: sstein
ms.openlocfilehash: 300f9753b721bc3e0a821a6b77929a9bec09312b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646477"
---
# <a name="localdb_error_instance_already_shared"></a><span data-ttu-id="decae-102">LOCALDB_ERROR_INSTANCE_ALREADY_SHARED</span><span class="sxs-lookup"><span data-stu-id="decae-102">LOCALDB_ERROR_INSTANCE_ALREADY_SHARED</span></span>
    
## <a name="details"></a><span data-ttu-id="decae-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="decae-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="decae-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="decae-104">Product Name</span></span>|<span data-ttu-id="decae-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="decae-105">SQL Server</span></span>|  
|<span data-ttu-id="decae-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="decae-106">Event ID</span></span>|<span data-ttu-id="decae-107">284</span><span class="sxs-lookup"><span data-stu-id="decae-107">284</span></span>|  
|<span data-ttu-id="decae-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="decae-108">Event Source</span></span>|<span data-ttu-id="decae-109">SQL Server 로컬 데이터베이스 런타임 12.0</span><span class="sxs-lookup"><span data-stu-id="decae-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="decae-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="decae-110">Component</span></span>|<span data-ttu-id="decae-111">로컬 데이터베이스 런타임 API</span><span class="sxs-lookup"><span data-stu-id="decae-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="decae-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="decae-112">Message Text</span></span>|<span data-ttu-id="decae-113">지정된 로컬 데이터베이스 인스턴스는 이미 공유되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="decae-113">The specified Local Database Instance is already shared.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="decae-114">설명</span><span class="sxs-lookup"><span data-stu-id="decae-114">Explanation</span></span>  
 <span data-ttu-id="decae-115">지정된 로컬 데이터베이스 인스턴스는 이미 다른 이름으로 공유되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="decae-115">The specified Local Database Instance is already shared with a different shared name.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="decae-116">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="decae-116">User Action</span></span>  
 <span data-ttu-id="decae-117">먼저 공유 인스턴스의 공유를 해제한 후 다른 공유 이름으로 다시 공유하십시오.</span><span class="sxs-lookup"><span data-stu-id="decae-117">Unshare the shared instance before sharing it again with a different shared name.</span></span>  
  
  
