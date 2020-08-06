---
title: MSSQLSERVER_8642 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8642 (Database Engine error)
ms.assetid: fc498059-202f-4d0b-8599-4e784b47c186
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e30296fa569599b91ca74edc7535d330119e1680
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652853"
---
# <a name="mssqlserver_8642"></a><span data-ttu-id="a645a-102">MSSQLSERVER_8642</span><span class="sxs-lookup"><span data-stu-id="a645a-102">MSSQLSERVER_8642</span></span>
    
## <a name="details"></a><span data-ttu-id="a645a-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="a645a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a645a-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="a645a-104">Product Name</span></span>|<span data-ttu-id="a645a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a645a-105">SQL Server</span></span>|  
|<span data-ttu-id="a645a-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="a645a-106">Event ID</span></span>|<span data-ttu-id="a645a-107">8642</span><span class="sxs-lookup"><span data-stu-id="a645a-107">8642</span></span>|  
|<span data-ttu-id="a645a-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="a645a-108">Event Source</span></span>|<span data-ttu-id="a645a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a645a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a645a-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="a645a-110">Component</span></span>|<span data-ttu-id="a645a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a645a-111">SQLEngine</span></span>|  
|<span data-ttu-id="a645a-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="a645a-112">Symbolic Name</span></span>|<span data-ttu-id="a645a-113">EXCHNGSTART_ERR</span><span class="sxs-lookup"><span data-stu-id="a645a-113">EXCHNGSTART_ERR</span></span>|  
|<span data-ttu-id="a645a-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="a645a-114">Message Text</span></span>|<span data-ttu-id="a645a-115">쿼리 프로세서에서 병렬 쿼리 실행에 필요한 스레드 리소스를 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a645a-115">The query processor could not start the necessary thread resources for parallel query execution.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a645a-116">설명</span><span class="sxs-lookup"><span data-stu-id="a645a-116">Explanation</span></span>  
 <span data-ttu-id="a645a-117">서버의 스레드 리소스가 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="a645a-117">Thread resources are low in the server.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a645a-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="a645a-118">User Action</span></span>  
 <span data-ttu-id="a645a-119">서버의 로드를 줄이고 쿼리를 다시 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="a645a-119">Reduce load on the server, and run the query again.</span></span>  
  
  
