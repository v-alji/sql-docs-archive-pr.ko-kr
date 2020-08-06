---
title: MSSQLSERVER_1803 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1803 (Database Engine error)
ms.assetid: d4315390-82f1-4c4c-8d1b-1a4989537cca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 11302f882846c49c6e9998608967e7042ac9860c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652150"
---
# <a name="mssqlserver_1803"></a><span data-ttu-id="10715-102">MSSQLSERVER_1803</span><span class="sxs-lookup"><span data-stu-id="10715-102">MSSQLSERVER_1803</span></span>
    
## <a name="details"></a><span data-ttu-id="10715-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="10715-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="10715-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="10715-104">Product Name</span></span>|<span data-ttu-id="10715-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="10715-105">SQL Server</span></span>|  
|<span data-ttu-id="10715-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="10715-106">Event ID</span></span>|<span data-ttu-id="10715-107">1803</span><span class="sxs-lookup"><span data-stu-id="10715-107">1803</span></span>|  
|<span data-ttu-id="10715-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="10715-108">Event Source</span></span>|<span data-ttu-id="10715-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="10715-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="10715-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="10715-110">Component</span></span>|<span data-ttu-id="10715-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="10715-111">SQLEngine</span></span>|  
|<span data-ttu-id="10715-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="10715-112">Symbolic Name</span></span>|<span data-ttu-id="10715-113">NO_SPACE</span><span class="sxs-lookup"><span data-stu-id="10715-113">NO_SPACE</span></span>|  
|<span data-ttu-id="10715-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="10715-114">Message Text</span></span>|<span data-ttu-id="10715-115">CREATE DATABASE가 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="10715-115">CREATE DATABASE failed.</span></span> <span data-ttu-id="10715-116">model 데이터베이스의 복사본을 수용하려면 주 파일이 최소한 %dMB여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10715-116">Primary file must be at least %d MB to accommodate a copy of the model database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="10715-117">설명</span><span class="sxs-lookup"><span data-stu-id="10715-117">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="10715-118">는 모델 데이터베이스의 복사본을 만들어 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="10715-118">creates a database by making a copy of the model database.</span></span> <span data-ttu-id="10715-119">그런 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 복사본의 이름을 바꾸고 새 데이터베이스를 요청된 크기로 확대합니다.</span><span class="sxs-lookup"><span data-stu-id="10715-119">Then [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] renames the copy, and enlarges the new database to the requested size.</span></span> <span data-ttu-id="10715-120">이 경우 사용자가 model 데이터베이스보다 작은 데이터베이스를 만들려고 시도했습니다.</span><span class="sxs-lookup"><span data-stu-id="10715-120">In this case, the user tried to create a database smaller than the model database.</span></span> <span data-ttu-id="10715-121">그러나 model 데이터베이스 복사본이 주 데이터 파일에 맞지 않거나 파일이 model 데이터베이스보다 작기 때문에 이 작업이 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="10715-121">The operation failed because the copy of the model database could not fit on the primary data file, because the file was smaller than the model database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="10715-122">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="10715-122">User Action</span></span>  
 <span data-ttu-id="10715-123">더 큰 데이터베이스 파일 크기를 사용하여 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="10715-123">Create the database by using a larger database file size.</span></span> <span data-ttu-id="10715-124">그런 다음 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 DBCC SHRINKDATABASE 문을 사용하여 원하는 경우 데이터베이스를 축소합니다.</span><span class="sxs-lookup"><span data-stu-id="10715-124">Then shrink the database if you want by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or the DBCC SHRINKDATABASE statement.</span></span>  
  
  
