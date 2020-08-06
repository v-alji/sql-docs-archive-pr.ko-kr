---
title: LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: a7c5ce08-8841-49a3-b252-116807ba469a
author: stevestein
ms.author: sstein
ms.openlocfilehash: aa6db2af138bb2aeefb1a922e55db56c4ea821f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743288"
---
# <a name="localdb_error_instance_exists_with_lower_version"></a><span data-ttu-id="dd855-102">LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION</span><span class="sxs-lookup"><span data-stu-id="dd855-102">LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION</span></span>
    
## <a name="details"></a><span data-ttu-id="dd855-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="dd855-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dd855-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="dd855-104">Product Name</span></span>|<span data-ttu-id="dd855-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="dd855-105">SQL Server</span></span>|  
|<span data-ttu-id="dd855-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="dd855-106">Event ID</span></span>|<span data-ttu-id="dd855-107">258</span><span class="sxs-lookup"><span data-stu-id="dd855-107">258</span></span>|  
|<span data-ttu-id="dd855-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="dd855-108">Event Source</span></span>|<span data-ttu-id="dd855-109">SQL Server 로컬 데이터베이스 런타임 12.0</span><span class="sxs-lookup"><span data-stu-id="dd855-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="dd855-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="dd855-110">Component</span></span>|<span data-ttu-id="dd855-111">로컬 데이터베이스 런타임 API</span><span class="sxs-lookup"><span data-stu-id="dd855-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="dd855-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="dd855-112">Message Text</span></span>|<span data-ttu-id="dd855-113">지정된 버전의 로컬 데이터베이스 인스턴스를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dd855-113">Unable to create the Local Database instance with specified version.</span></span> <span data-ttu-id="dd855-114">같은 이름의 인스턴스가 이미 존재하지만 지정된 버전보다 하위 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="dd855-114">An instance with the same name already exists, but it has lower version than the specified version.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="dd855-115">설명</span><span class="sxs-lookup"><span data-stu-id="dd855-115">Explanation</span></span>  
 <span data-ttu-id="dd855-116">지정한 인스턴스가 이미 있지만 버전이 요청한 것보다 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="dd855-116">The specified instance already exists but its version is lower than requested.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dd855-117">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="dd855-117">User Action</span></span>  
 <span data-ttu-id="dd855-118">기존 인스턴스를 삭제하고 작업을 다시 시도하십시오.</span><span class="sxs-lookup"><span data-stu-id="dd855-118">Delete the existing instance and retry the operation.</span></span>  
  
  
