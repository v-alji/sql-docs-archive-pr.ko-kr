---
title: MSSQLSERVER_18264 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18264 (Database Engine error)
ms.assetid: 3050fc56-2be5-43cf-916b-50a3ac5f89aa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3edfeb82601e254c02df87cc4a978b9ab5e653e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652141"
---
# <a name="mssqlserver_18264"></a><span data-ttu-id="2ed05-102">MSSQLSERVER_18264</span><span class="sxs-lookup"><span data-stu-id="2ed05-102">MSSQLSERVER_18264</span></span>
    
## <a name="details"></a><span data-ttu-id="2ed05-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="2ed05-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2ed05-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="2ed05-104">Product Name</span></span>|<span data-ttu-id="2ed05-105">Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="2ed05-105">Microsoft SQL Server</span></span>|  
|<span data-ttu-id="2ed05-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="2ed05-106">Event ID</span></span>|<span data-ttu-id="2ed05-107">18264</span><span class="sxs-lookup"><span data-stu-id="2ed05-107">18264</span></span>|  
|<span data-ttu-id="2ed05-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="2ed05-108">Event Source</span></span>|<span data-ttu-id="2ed05-109">MSSQLENGINE</span><span class="sxs-lookup"><span data-stu-id="2ed05-109">MSSQLENGINE</span></span>|  
|<span data-ttu-id="2ed05-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="2ed05-110">Component</span></span>|<span data-ttu-id="2ed05-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2ed05-111">SQLEngine</span></span>|  
|<span data-ttu-id="2ed05-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="2ed05-112">Symbolic Name</span></span>|<span data-ttu-id="2ed05-113">STRMIO_DBDUMP</span><span class="sxs-lookup"><span data-stu-id="2ed05-113">STRMIO_DBDUMP</span></span>|  
|<span data-ttu-id="2ed05-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="2ed05-114">Message Text</span></span>|<span data-ttu-id="2ed05-115">데이터베이스가 백업되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2ed05-115">Database backed up.</span></span> <span data-ttu-id="2ed05-116">데이터베이스: %s, 만든 날짜(시간): %s(%s), 덤프한 페이지 수: %d, 첫 번째 LSN: %s, 마지막 LSN: %s, 덤프 디바이스 수: %d, 디바이스 정보: (%s).</span><span class="sxs-lookup"><span data-stu-id="2ed05-116">Database: %s, creation date(time): %s(%s), pages dumped: %d, first LSN: %s, last LSN: %s, number of dump devices: %d, device information: (%s).</span></span> <span data-ttu-id="2ed05-117">이 메시지는 정보 제공용이므로</span><span class="sxs-lookup"><span data-stu-id="2ed05-117">This is an informational message only.</span></span> <span data-ttu-id="2ed05-118">추가적인 조치가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2ed05-118">No user action is required.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2ed05-119">설명</span><span class="sxs-lookup"><span data-stu-id="2ed05-119">Explanation</span></span>  
 <span data-ttu-id="2ed05-120">기본적으로 백업을 성공적으로 수행할 때마다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그와 시스템 이벤트 로그에 이 정보 메시지가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ed05-120">By default, every successful backup adds this informational message to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and the system event log.</span></span> <span data-ttu-id="2ed05-121">트랜잭션 로그를 자주 백업하는 경우 이러한 메시지는 바로 누적되므로 엄청난 오류 로그가 쌓여 다른 메시지를 찾기 힘들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ed05-121">If you very frequently back up the transaction log, these messages can accumulate quickly, creating very large error logs that can make finding other messages difficult.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2ed05-122">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="2ed05-122">User Action</span></span>  
 <span data-ttu-id="2ed05-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 추적 플래그 **3226**을 사용하여 이러한 로그 항목을 표시하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ed05-123">You can suppress these log entries by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trace flag **3226**.</span></span> <span data-ttu-id="2ed05-124">로그 백업을 자주 실행하거나 이러한 항목에 종속되는 스크립트가 없는 경우 이 추적 플래그를 설정하면 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed05-124">Enabling this trace flag is useful if you are running frequent log backups and if none of your scripts depend on those entries.</span></span>  
  
 <span data-ttu-id="2ed05-125">추적 플래그를 사용하는 방법은 SQL Server 온라인 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2ed05-125">For information about using trace flags, see SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ed05-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2ed05-126">See Also</span></span>  
 [<span data-ttu-id="2ed05-127">추적 플래그&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2ed05-127">Trace Flags &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)  
  
  
