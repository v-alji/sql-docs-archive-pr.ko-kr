---
title: LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: c1595263-6264-4a43-9535-5eb76ece3a57
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0896f3e70e6c65a1fcd0de4169249fb622e6b5f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646471"
---
# <a name="localdb_error_too_many_shared_instances"></a><span data-ttu-id="ae078-102">LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES</span><span class="sxs-lookup"><span data-stu-id="ae078-102">LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES</span></span>
    
## <a name="details"></a><span data-ttu-id="ae078-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="ae078-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ae078-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="ae078-104">Product Name</span></span>|<span data-ttu-id="ae078-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ae078-105">SQL Server</span></span>|  
|<span data-ttu-id="ae078-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="ae078-106">Event ID</span></span>|<span data-ttu-id="ae078-107">287</span><span class="sxs-lookup"><span data-stu-id="ae078-107">287</span></span>|  
|<span data-ttu-id="ae078-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="ae078-108">Event Source</span></span>|<span data-ttu-id="ae078-109">SQL Server 로컬 데이터베이스 런타임 12.0</span><span class="sxs-lookup"><span data-stu-id="ae078-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="ae078-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="ae078-110">Component</span></span>|<span data-ttu-id="ae078-111">로컬 데이터베이스 런타임 API</span><span class="sxs-lookup"><span data-stu-id="ae078-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="ae078-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="ae078-112">Message Text</span></span>|<span data-ttu-id="ae078-113">공유 인스턴스가 너무 많아 고유한 사용자 인스턴스 이름을 생성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ae078-113">There are too many shared instance and we cannot generate unique User Instance Name.</span></span> <span data-ttu-id="ae078-114">기존 공유 인스턴스 중 일부의 공유를 해제하십시오.</span><span class="sxs-lookup"><span data-stu-id="ae078-114">Unshare some of the existing shared instances.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ae078-115">설명</span><span class="sxs-lookup"><span data-stu-id="ae078-115">Explanation</span></span>  
 <span data-ttu-id="ae078-116">공유 인스턴스가 너무 많아 고유한 사용자 인스턴스 이름을 생성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ae078-116">There are too many shared instance and we cannot generate unique User Instance Name.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ae078-117">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="ae078-117">User Action</span></span>  
 <span data-ttu-id="ae078-118">하나 이상의 공유 로컬 데이터베이스 런타임 인스턴스의 공유를 해제하고 다시 시도하십시오.</span><span class="sxs-lookup"><span data-stu-id="ae078-118">Unshare one or more of the shared Local Database Runtime instances and try again.</span></span>  
  
  
