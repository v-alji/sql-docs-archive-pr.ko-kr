---
title: MSSQLSERVER_825 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 825 (Database Engine error)
ms.assetid: f69f8214-5af1-4769-878b-117ad6eaff52
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3b17dfac371ad3c805fdbb0b5d3269fc451dd9d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650050"
---
# <a name="mssqlserver_825"></a><span data-ttu-id="43f18-102">MSSQLSERVER_825</span><span class="sxs-lookup"><span data-stu-id="43f18-102">MSSQLSERVER_825</span></span>
    
## <a name="details"></a><span data-ttu-id="43f18-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="43f18-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="43f18-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="43f18-104">Product Name</span></span>|<span data-ttu-id="43f18-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="43f18-105">SQL Server</span></span>|  
|<span data-ttu-id="43f18-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="43f18-106">Event ID</span></span>|<span data-ttu-id="43f18-107">825</span><span class="sxs-lookup"><span data-stu-id="43f18-107">825</span></span>|  
|<span data-ttu-id="43f18-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="43f18-108">Event Source</span></span>|<span data-ttu-id="43f18-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="43f18-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="43f18-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="43f18-110">Component</span></span>|<span data-ttu-id="43f18-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="43f18-111">SQLEngine</span></span>|  
|<span data-ttu-id="43f18-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="43f18-112">Symbolic Name</span></span>|<span data-ttu-id="43f18-113">B_RETRYWORKED</span><span class="sxs-lookup"><span data-stu-id="43f18-113">B_RETRYWORKED</span></span>|  
|<span data-ttu-id="43f18-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="43f18-114">Message Text</span></span>|<span data-ttu-id="43f18-115">오류로 인해 읽기 시도를 %d번 실패한 후 오프셋 %#016I64x에서 파일 '%ls'의 읽기 작업이 성공했습니다: %ls.</span><span class="sxs-lookup"><span data-stu-id="43f18-115">A read of the file '%ls' at offset %#016I64x succeeded after failing %d time(s) with error: %ls.</span></span> <span data-ttu-id="43f18-116">SQL Server 오류 로그 및 시스템 이벤트 로그의 추가 메시지에서 더 자세한 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43f18-116">Additional messages in the SQL Server error log and system event log may provide more detail.</span></span> <span data-ttu-id="43f18-117">이 오류 조건은 데이터베이스 무결성을 침해할 수 있으므로 수정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="43f18-117">This error condition threatens database integrity and must be corrected.</span></span> <span data-ttu-id="43f18-118">전체 데이터베이스 일관성 확인(DBCC CHECKDB)을 완료하십시오.</span><span class="sxs-lookup"><span data-stu-id="43f18-118">Complete a full database consistency check (DBCC CHECKDB).</span></span> <span data-ttu-id="43f18-119">이 오류는 여러 요인으로 인해 발생할 수 있습니다. 자세한 내용은 SQL Server 온라인 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="43f18-119">This error can be caused by many factors; for more information, see SQL Server Books Online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="43f18-120">설명</span><span class="sxs-lookup"><span data-stu-id="43f18-120">Explanation</span></span>  
 <span data-ttu-id="43f18-121">이 메시지는 읽기 작업이 적어도 한 번 이상 다시 실행되어야 했음을 나타내며 디스크 하드웨어에 중요한 문제가 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="43f18-121">This message indicates that the read operation had to be reissued at least one time, and indicates a major problem with the disk hardware.</span></span> <span data-ttu-id="43f18-122">현재 이 메시지는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 문제를 나타내고 있지 않지만 문제가 해결되지 않을 경우 데이터 손실 또는 데이터베이스 손상을 일으킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43f18-122">This message does not currently indicate a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] problem, but the disk problem could cause data loss or database corruption if it is not resolved.</span></span> <span data-ttu-id="43f18-123">시스템 이벤트 로그에 문제의 진단에 도움이 되는 관련 이벤트가 포함되어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43f18-123">The system event log may contain related events that help to diagnose the problem.</span></span> <span data-ttu-id="43f18-124">I/O 오류에 대한 자세한 내용은 [Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))(Microsoft SQL Server I/O 기본 사항, 2장)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="43f18-124">For more information about I/O errors, see [Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="43f18-125">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="43f18-125">User Action</span></span>  
 <span data-ttu-id="43f18-126">다음은 기본 문제를 확인하고 해결하는 데 도움이 되는 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="43f18-126">The following actions may help you identify and resolve the underlying problem:</span></span>  
  
-   <span data-ttu-id="43f18-127">이 메시지의 오류 로그 및 변수 텍스트를 검토하여 문제를 파악합니다.</span><span class="sxs-lookup"><span data-stu-id="43f18-127">Review the error log and the variable text in this message for clues that explain the problem.</span></span>  
  
-   <span data-ttu-id="43f18-128">디스크 시스템을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="43f18-128">Check your disk system.</span></span> <span data-ttu-id="43f18-129">디스크, 디스크 컨트롤러, 배열 카드 또는 디스크 드라이버에 관련된 문제일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43f18-129">The problem could be related to the disks, the disk controllers, array cards, or disk drivers.</span></span>  
  
-   <span data-ttu-id="43f18-130">최신 유틸리티의 디스크 제조업체에 문의하여 사용자의 디스크 시스템 상태를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="43f18-130">Contact the disk manufacturer for the latest utilities for checking the status of your disk system.</span></span>  
  
-   <span data-ttu-id="43f18-131">최신 드라이버 업데이트에 대해 디스크 제조업체에 문의합니다.</span><span class="sxs-lookup"><span data-stu-id="43f18-131">Contact the disk manufacturer for the latest driver updates.</span></span>  
  
  
