---
title: MSSQLSERVER_3151 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3151 (Database Engine error)
ms.assetid: a8657a91-ec75-4649-a09a-21920e0030ff
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c34414754ea9d25ad89f6aba767197eb1dfc10d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651025"
---
# <a name="mssqlserver_3151"></a><span data-ttu-id="1b300-102">MSSQLSERVER_3151</span><span class="sxs-lookup"><span data-stu-id="1b300-102">MSSQLSERVER_3151</span></span>
    
## <a name="details"></a><span data-ttu-id="1b300-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="1b300-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1b300-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="1b300-104">Product Name</span></span>|<span data-ttu-id="1b300-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1b300-105">SQL Server</span></span>|  
|<span data-ttu-id="1b300-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="1b300-106">Event ID</span></span>|<span data-ttu-id="1b300-107">3151</span><span class="sxs-lookup"><span data-stu-id="1b300-107">3151</span></span>|  
|<span data-ttu-id="1b300-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="1b300-108">Event Source</span></span>|<span data-ttu-id="1b300-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1b300-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1b300-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="1b300-110">Component</span></span>|<span data-ttu-id="1b300-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1b300-111">SQLEngine</span></span>|  
|<span data-ttu-id="1b300-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="1b300-112">Symbolic Name</span></span>|<span data-ttu-id="1b300-113">LDDB_MASTER_LOAD_FAILED</span><span class="sxs-lookup"><span data-stu-id="1b300-113">LDDB_MASTER_LOAD_FAILED</span></span>|  
|<span data-ttu-id="1b300-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="1b300-114">Message Text</span></span>|<span data-ttu-id="1b300-115">master 데이터베이스를 복원하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="1b300-115">Failed to restore master database.</span></span> <span data-ttu-id="1b300-116">SQL Server를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="1b300-116">Shutting down SQL Server.</span></span> <span data-ttu-id="1b300-117">Check the error logs, and rebuild the master database.</span><span class="sxs-lookup"><span data-stu-id="1b300-117">Check the error logs, and rebuild the master database.</span></span> <span data-ttu-id="1b300-118">master 데이터베이스를 다시 작성하는 방법은 SQL Server 온라인 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1b300-118">For more information about how to rebuild the master database, see SQL Server Books Online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1b300-119">설명</span><span class="sxs-lookup"><span data-stu-id="1b300-119">Explanation</span></span>  
 <span data-ttu-id="1b300-120">**master** 데이터베이스에서 발생하는 다양한 문제를 나타내는 일반적인 오류 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="1b300-120">This is a general error message indicating various problems with the **master** database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1b300-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="1b300-121">User Action</span></span>  
 <span data-ttu-id="1b300-122">자세한 내용은 오류 로그를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="1b300-122">Check the error logs for more information.</span></span> <span data-ttu-id="1b300-123">사용 가능한 **master** 데이터베이스를 만들려면 REBUILDDATABASE 옵션을 사용하여 Setup.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1b300-123">To create a usable **master** database, run Setup.exe with the REBUILDDATABASE option.</span></span> <span data-ttu-id="1b300-124">자세한 내용은 SQL Server 온라인 설명서에서 "방법: 명령 프롬프트에서 SQL Server 설치"를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1b300-124">For more information see "How to: Install SQL Server from the Command Prompt" in SQL Server Books Online.</span></span>  
  
  
