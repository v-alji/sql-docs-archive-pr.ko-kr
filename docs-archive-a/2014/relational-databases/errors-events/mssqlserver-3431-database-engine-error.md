---
title: MSSQLSERVER_3431 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3431 (Database Engine error)
ms.assetid: 9541217f-e5c6-4a12-a19a-006058f1d3f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9b62047a25d71ca05dc3ab03651e5672353bc0a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653893"
---
# <a name="mssqlserver_3431"></a><span data-ttu-id="17167-102">MSSQLSERVER_3431</span><span class="sxs-lookup"><span data-stu-id="17167-102">MSSQLSERVER_3431</span></span>
    
## <a name="details"></a><span data-ttu-id="17167-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="17167-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="17167-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="17167-104">Product Name</span></span>|<span data-ttu-id="17167-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="17167-105">SQL Server</span></span>|  
|<span data-ttu-id="17167-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="17167-106">Event ID</span></span>|<span data-ttu-id="17167-107">3431</span><span class="sxs-lookup"><span data-stu-id="17167-107">3431</span></span>|  
|<span data-ttu-id="17167-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="17167-108">Event Source</span></span>|<span data-ttu-id="17167-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="17167-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="17167-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="17167-110">Component</span></span>|<span data-ttu-id="17167-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="17167-111">SQLEngine</span></span>|  
|<span data-ttu-id="17167-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="17167-112">Symbolic Name</span></span>|<span data-ttu-id="17167-113">UNRESOLVED_XACT</span><span class="sxs-lookup"><span data-stu-id="17167-113">UNRESOLVED_XACT</span></span>|  
|<span data-ttu-id="17167-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="17167-114">Message Text</span></span>|<span data-ttu-id="17167-115">해결되지 않은 트랜잭션 결과로 인해 데이터베이스 '%.\*ls'(데이터베이스 ID %d)을(를) 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="17167-115">Could not recover database '%.\*ls' (database ID %d) because of unresolved transaction outcomes.</span></span> <span data-ttu-id="17167-116">MS DTC(Microsoft Distributed Transaction Coordinator) 트랜잭션이 준비되었지만 문제를 해결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="17167-116">Microsoft Distributed Transaction Coordinator (MS DTC) transactions were prepared, but MS DTC was unable to determine the resolution.</span></span> <span data-ttu-id="17167-117">문제를 해결하려면 MS DTC를 수정하거나, 전체 백업에서 데이터베이스를 복원하거나, 데이터베이스를 복구하십시오.</span><span class="sxs-lookup"><span data-stu-id="17167-117">To resolve, either fix MS DTC, restore from a full backup, or repair the database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="17167-118">설명</span><span class="sxs-lookup"><span data-stu-id="17167-118">Explanation</span></span>  
 <span data-ttu-id="17167-119">데이터베이스가 종료될 때 MS DTC([!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator)를 사용하는 하나 이상의 분산 트랜잭션이 완전하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17167-119">One or more distributed transactions that were using [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) were incomplete when the database was shut down.</span></span> <span data-ttu-id="17167-120">MS DTC의 자세한 정보 없이는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 트랜잭션을 완료하거나 롤백할 수 없으므로 이 데이터베이스를 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="17167-120">Recovery of this database failed because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot complete the transactions or roll back the transactions without more information from MS DTC.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="17167-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="17167-121">User Action</span></span>  
 <span data-ttu-id="17167-122">이 데이터베이스를 복구하려면 MS DTC 문제를 먼저 해결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17167-122">To recover this database, you must first resolve the problem with MS DTC.</span></span> <span data-ttu-id="17167-123">MS DTC 문제를 확인하려면 Windows 이벤트 로그를 검사하십시오.</span><span class="sxs-lookup"><span data-stu-id="17167-123">To investigate the problem with MS DTC, examine the Windows event logs.</span></span> <span data-ttu-id="17167-124">MS DTC 문제를 해결할 수 없어 데이터베이스를 복구할 수 없는 경우 데이터베이스의 백업을 복원하십시오.</span><span class="sxs-lookup"><span data-stu-id="17167-124">If you cannot resolve the problem with MS DTC and recover the database, restore a backup of database.</span></span>  
  
  
