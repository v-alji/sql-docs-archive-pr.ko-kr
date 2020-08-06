---
title: MSSQLSERVER_3417 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3417 (Database Engine error)
ms.assetid: 005829c8-cf57-4828-818a-bbe8ee2e00f0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 680e5a4266c7d0d9aaacb7b3deb9525a002077e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653895"
---
# <a name="mssqlserver_3417"></a><span data-ttu-id="b4637-102">MSSQLSERVER_3417</span><span class="sxs-lookup"><span data-stu-id="b4637-102">MSSQLSERVER_3417</span></span>
    
## <a name="details"></a><span data-ttu-id="b4637-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="b4637-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b4637-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="b4637-104">Product Name</span></span>|<span data-ttu-id="b4637-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b4637-105">SQL Server</span></span>|  
|<span data-ttu-id="b4637-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="b4637-106">Event ID</span></span>|<span data-ttu-id="b4637-107">3417</span><span class="sxs-lookup"><span data-stu-id="b4637-107">3417</span></span>|  
|<span data-ttu-id="b4637-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="b4637-108">Event Source</span></span>|<span data-ttu-id="b4637-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b4637-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b4637-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="b4637-110">Component</span></span>|<span data-ttu-id="b4637-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b4637-111">SQLEngine</span></span>|  
|<span data-ttu-id="b4637-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="b4637-112">Symbolic Name</span></span>|<span data-ttu-id="b4637-113">REC_BADMASTER</span><span class="sxs-lookup"><span data-stu-id="b4637-113">REC_BADMASTER</span></span>|  
|<span data-ttu-id="b4637-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="b4637-114">Message Text</span></span>|<span data-ttu-id="b4637-115">master 데이터베이스를 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b4637-115">Cannot recover the master database.</span></span> <span data-ttu-id="b4637-116">SQL Server를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b4637-116">SQL Server is unable to run.</span></span> <span data-ttu-id="b4637-117">전체 백업에서 master 데이터베이스를 복원하거나 master 데이터베이스를 복구 또는 다시 작성하십시오.</span><span class="sxs-lookup"><span data-stu-id="b4637-117">Restore master from a full backup, repair it, or rebuild it.</span></span> <span data-ttu-id="b4637-118">master 데이터베이스를 다시 작성하는 방법은 SQL Server 온라인 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b4637-118">For more information about how to rebuild the master database, see SQL Server Books Online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b4637-119">설명</span><span class="sxs-lookup"><span data-stu-id="b4637-119">Explanation</span></span>  
 <span data-ttu-id="b4637-120">SQL Server에서 **master** 데이터베이스를 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b4637-120">SQL Server cannot start the **master** database.</span></span> <span data-ttu-id="b4637-121">**master** 또는 **tempdb**를 온라인 상태로 만들 수 없으면 SQL Server를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b4637-121">If the **master** or **tempdb** cannot be brought online, SQL Server cannot run.</span></span> <span data-ttu-id="b4637-122">이 오류는 보통 다른 오류 뒤에 나옵니다.</span><span class="sxs-lookup"><span data-stu-id="b4637-122">This error is usually preceded by other errors.</span></span> <span data-ttu-id="b4637-123">오류 로그를 검토하여 근본 원인을 찾으십시오.</span><span class="sxs-lookup"><span data-stu-id="b4637-123">Review error logs to find the root cause.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b4637-124">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="b4637-124">User Action</span></span>  
 <span data-ttu-id="b4637-125">데이터베이스 백업을 복원하거나 데이터베이스를 복구하십시오.</span><span class="sxs-lookup"><span data-stu-id="b4637-125">Restore backup of the database or repair the database.</span></span>  
  
  
