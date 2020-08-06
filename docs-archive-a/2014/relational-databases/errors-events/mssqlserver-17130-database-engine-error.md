---
title: MSSQLSERVER_17130 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17130 (Database Engine error)
ms.assetid: 7ce6afca-221d-402f-89df-da7e74a339a8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b63be325273e4df33d837ec1548ed46701323977
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731676"
---
# <a name="mssqlserver_17130"></a><span data-ttu-id="531fd-102">MSSQLSERVER_17130</span><span class="sxs-lookup"><span data-stu-id="531fd-102">MSSQLSERVER_17130</span></span>
    
## <a name="details"></a><span data-ttu-id="531fd-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="531fd-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="531fd-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="531fd-104">Product Name</span></span>|<span data-ttu-id="531fd-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="531fd-105">SQL Server</span></span>|  
|<span data-ttu-id="531fd-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="531fd-106">Event ID</span></span>|<span data-ttu-id="531fd-107">17130</span><span class="sxs-lookup"><span data-stu-id="531fd-107">17130</span></span>|  
|<span data-ttu-id="531fd-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="531fd-108">Event Source</span></span>|<span data-ttu-id="531fd-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="531fd-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="531fd-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="531fd-110">Component</span></span>|<span data-ttu-id="531fd-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="531fd-111">SQLEngine</span></span>|  
|<span data-ttu-id="531fd-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="531fd-112">Symbolic Name</span></span>|<span data-ttu-id="531fd-113">INIT_NOLOCKSPACE</span><span class="sxs-lookup"><span data-stu-id="531fd-113">INIT_NOLOCKSPACE</span></span>|  
|<span data-ttu-id="531fd-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="531fd-114">Message Text</span></span>|<span data-ttu-id="531fd-115">구성된 잠금 수에 대한 메모리가 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="531fd-115">Not enough memory for the configured number of locks.</span></span> <span data-ttu-id="531fd-116">더 작은 수의 잠금 해시 테이블로 시작되며 이 경우 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="531fd-116">Attempting to start with a smaller lock hash table, which may impact performance.</span></span> <span data-ttu-id="531fd-117">데이터베이스 엔진의 이 인스턴스에 대한 추가 메모리를 구성해 줄 것을 데이터베이스 관리자에게 요청하십시오.</span><span class="sxs-lookup"><span data-stu-id="531fd-117">Contact the database administrator to configure more memory for this instance of the Database Engine.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="531fd-118">설명</span><span class="sxs-lookup"><span data-stu-id="531fd-118">Explanation</span></span>  
 <span data-ttu-id="531fd-119">메모리가 부족하여 원하는 크기의 잠금 관리자 해시 테이블을 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="531fd-119">Not enough memory for the desired lock manager hash table size.</span></span>  <span data-ttu-id="531fd-120">더 작은 해시 테이블을 할당하려는 시도가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="531fd-120">An attempt will be made to allocate a smaller hash table.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="531fd-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="531fd-121">User Action</span></span>  
 <span data-ttu-id="531fd-122">서버 메모리 구성 매개 변수(min/max server memory)를 확인하고 메모리가 부족한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="531fd-122">Check server memory configuration parameters (min/max server memory), check for memory pressures.</span></span> <span data-ttu-id="531fd-123">SQL Server에서 사용할 수 있는 메모리를 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="531fd-123">Provide SQL Server more memory.</span></span>  
  
  
