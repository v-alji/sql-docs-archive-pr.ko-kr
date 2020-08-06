---
title: MSSQLSERVER_1807 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1807 (Database Engine error)
ms.assetid: 13c1b240-098b-4d9e-89aa-21599548e074
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 261d352084e490fb7f9216e1a7e352542e85a6f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650076"
---
# <a name="mssqlserver_1807"></a><span data-ttu-id="b8be8-102">MSSQLSERVER_1807</span><span class="sxs-lookup"><span data-stu-id="b8be8-102">MSSQLSERVER_1807</span></span>
    
## <a name="details"></a><span data-ttu-id="b8be8-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="b8be8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b8be8-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="b8be8-104">Product Name</span></span>|<span data-ttu-id="b8be8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b8be8-105">SQL Server</span></span>|  
|<span data-ttu-id="b8be8-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="b8be8-106">Event ID</span></span>|<span data-ttu-id="b8be8-107">1807</span><span class="sxs-lookup"><span data-stu-id="b8be8-107">1807</span></span>|  
|<span data-ttu-id="b8be8-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="b8be8-108">Event Source</span></span>|<span data-ttu-id="b8be8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b8be8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b8be8-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="b8be8-110">Component</span></span>|<span data-ttu-id="b8be8-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b8be8-111">SQLEngine</span></span>|  
|<span data-ttu-id="b8be8-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="b8be8-112">Symbolic Name</span></span>|<span data-ttu-id="b8be8-113">CANNOT_EX_LOCK</span><span class="sxs-lookup"><span data-stu-id="b8be8-113">CANNOT_EX_LOCK</span></span>|  
|<span data-ttu-id="b8be8-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="b8be8-114">Message Text</span></span>|<span data-ttu-id="b8be8-115">데이터베이스 '%.\*ls'에 대한 배타적 잠금을 얻을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b8be8-115">Could not obtain exclusive lock on database '%.\*ls'.</span></span> <span data-ttu-id="b8be8-116">나중에 작업을 다시 시도하십시오.</span><span class="sxs-lookup"><span data-stu-id="b8be8-116">Retry the operation later.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b8be8-117">설명</span><span class="sxs-lookup"><span data-stu-id="b8be8-117">Explanation</span></span>  
 <span data-ttu-id="b8be8-118">데이터베이스에 대한 단독 액세스를 필요로 하는 작업에서 배타적 잠금을 얻을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b8be8-118">An operation that required exclusive access to the database was unable to obtain it.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b8be8-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="b8be8-119">User Action</span></span>  
 <span data-ttu-id="b8be8-120">해당 데이터베이스에 대한 모든 연결을 끊거나 나중에 쿼리를 다시 시도하십시오.</span><span class="sxs-lookup"><span data-stu-id="b8be8-120">Disconnect all the connections to that database or try the query again later.</span></span>  
  
  
