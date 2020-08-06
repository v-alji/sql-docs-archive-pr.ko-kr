---
title: MSSQLSERVER_9004 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9004 (Database Engine error)
ms.assetid: b528bb49-340c-4a81-9c8d-cefce6562f16
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 910665b4349e5b13c5abb4fd687dcf0c6fc122cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650039"
---
# <a name="mssqlserver_9004"></a><span data-ttu-id="bf90f-102">MSSQLSERVER_9004</span><span class="sxs-lookup"><span data-stu-id="bf90f-102">MSSQLSERVER_9004</span></span>
    
## <a name="details"></a><span data-ttu-id="bf90f-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="bf90f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bf90f-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="bf90f-104">Product Name</span></span>|<span data-ttu-id="bf90f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="bf90f-105">SQL Server</span></span>|  
|<span data-ttu-id="bf90f-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="bf90f-106">Event ID</span></span>|<span data-ttu-id="bf90f-107">9004</span><span class="sxs-lookup"><span data-stu-id="bf90f-107">9004</span></span>|  
|<span data-ttu-id="bf90f-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="bf90f-108">Event Source</span></span>|<span data-ttu-id="bf90f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="bf90f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="bf90f-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="bf90f-110">Component</span></span>|<span data-ttu-id="bf90f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="bf90f-111">SQLEngine</span></span>|  
|<span data-ttu-id="bf90f-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="bf90f-112">Symbolic Name</span></span>|<span data-ttu-id="bf90f-113">LOG_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="bf90f-113">LOG_CORRUPT</span></span>|  
|<span data-ttu-id="bf90f-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="bf90f-114">Message Text</span></span>|<span data-ttu-id="bf90f-115">데이터베이스 '%.\*ls'의 로그를 처리하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="bf90f-115">An error occurred while processing the log for database '%.\*ls'.</span></span>  <span data-ttu-id="bf90f-116">가능하면 백업을 사용하여 복원하십시오.</span><span class="sxs-lookup"><span data-stu-id="bf90f-116">If possible, restore from backup.</span></span> <span data-ttu-id="bf90f-117">백업이 없을 경우 로그를 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf90f-117">If a backup is not available, it might be necessary to rebuild the log.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bf90f-118">설명</span><span class="sxs-lookup"><span data-stu-id="bf90f-118">Explanation</span></span>  
 <span data-ttu-id="bf90f-119">롤백, 복구 또는 복제 중 로그를 처리하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="bf90f-119">An error was encountered while processing the log during rollback, recovery, or replication.</span></span> <span data-ttu-id="bf90f-120">운영 체제에서 발견한 오류이거나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 발견한 내부 일관성 오류일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf90f-120">This could indicate an error detected by the operating system-or an internal consistency error detected by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bf90f-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="bf90f-121">User Action</span></span>  
 <span data-ttu-id="bf90f-122">이 오류를 수정하려면 다음 중 하나를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="bf90f-122">One of the following actions will correct this error:</span></span>  
  
-   <span data-ttu-id="bf90f-123">백업에서 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="bf90f-123">Restore from a backup.</span></span>  
  
-   <span data-ttu-id="bf90f-124">로그를 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="bf90f-124">Rebuild the log.</span></span>  
  
 <span data-ttu-id="bf90f-125">또한 시스템 이벤트나 오류 로그를 검사하여 문제를 일으킬 수 있는 시스템 내의 문제를 파악하십시오.</span><span class="sxs-lookup"><span data-stu-id="bf90f-125">Also, check system event and error logs to identify issues within the system that may have caused the problem.</span></span>  
  
  
