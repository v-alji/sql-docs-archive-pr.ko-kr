---
title: MSSQLSERVER_3437 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3437 (Database Engine error)
ms.assetid: b38216e2-b650-43bd-97af-061d54f60031
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ed8f2050f6f1b38bc5f3fcb7a9700b80e52f2763
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653888"
---
# <a name="mssqlserver_3437"></a><span data-ttu-id="ea577-102">MSSQLSERVER_3437</span><span class="sxs-lookup"><span data-stu-id="ea577-102">MSSQLSERVER_3437</span></span>
    
## <a name="details"></a><span data-ttu-id="ea577-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="ea577-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ea577-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="ea577-104">Product Name</span></span>|<span data-ttu-id="ea577-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ea577-105">SQL Server</span></span>|  
|<span data-ttu-id="ea577-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="ea577-106">Event ID</span></span>|<span data-ttu-id="ea577-107">3437</span><span class="sxs-lookup"><span data-stu-id="ea577-107">3437</span></span>|  
|<span data-ttu-id="ea577-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="ea577-108">Event Source</span></span>|<span data-ttu-id="ea577-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ea577-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ea577-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="ea577-110">Component</span></span>|<span data-ttu-id="ea577-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ea577-111">SQLEngine</span></span>|  
|<span data-ttu-id="ea577-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="ea577-112">Symbolic Name</span></span>|<span data-ttu-id="ea577-113">NODTC</span><span class="sxs-lookup"><span data-stu-id="ea577-113">NODTC</span></span>|  
|<span data-ttu-id="ea577-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="ea577-114">Message Text</span></span>|<span data-ttu-id="ea577-115">데이터베이스 '%.\*ls'을(를) 복구하는 중 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="ea577-115">An error occurred while recovering database '%.\*ls'.</span></span> <span data-ttu-id="ea577-116">MS DTC(Microsoft Distributed Transaction Coordinator)에 연결하여 트랜잭션 %S_XID의 완료 상태를 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ea577-116">Unable to connect to Microsoft Distributed Transaction Coordinator (MS DTC) to check the completion status of transaction %S_XID.</span></span> <span data-ttu-id="ea577-117">MS DTC를 수정하고 복구 작업을 다시 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="ea577-117">Fix MS DTC, and run recovery again.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ea577-118">설명</span><span class="sxs-lookup"><span data-stu-id="ea577-118">Explanation</span></span>  
 <span data-ttu-id="ea577-119">데이터베이스가 종료될 때 MS DTC([!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator)를 사용하는 하나 이상의 분산 트랜잭션이 완전하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ea577-119">One or more distributed transactions that were using [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) were incomplete when the database was shut down.</span></span> <span data-ttu-id="ea577-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 트랜잭션을 완료하거나 롤백하기 위해 MS DTC에 연결할 수 없으므로 이 데이터베이스를 복구하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="ea577-120">Recovery of this database failed because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot connect to MS DTC to complete or roll back the transactions.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ea577-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="ea577-121">User Action</span></span>  
 <span data-ttu-id="ea577-122">이 데이터베이스를 복구하려면 MS DTC 문제를 먼저 해결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea577-122">To recover this database, you must first resolve the problem with MS DTC.</span></span> <span data-ttu-id="ea577-123">MS DTC 문제를 확인하려면 Windows 이벤트 로그를 검사하십시오.</span><span class="sxs-lookup"><span data-stu-id="ea577-123">To investigate the problem with MS DTC, examine the Windows event logs.</span></span> <span data-ttu-id="ea577-124">MS DTC 문제를 해결할 수 없어 데이터베이스를 복구할 수 없는 경우 데이터베이스의 백업을 복원하십시오.</span><span class="sxs-lookup"><span data-stu-id="ea577-124">If you cannot resolve the problem with MS DTC and recover the database, restore a backup of database.</span></span>  
  
  
