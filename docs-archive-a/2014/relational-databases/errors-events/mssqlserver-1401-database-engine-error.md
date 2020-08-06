---
title: MSSQLSERVER_1401 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1401 (Database Engine error)
ms.assetid: 02928770-aa63-4509-8713-406c73e4cedc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 720263939e2f1685649fc41896e8ea10907d92ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653959"
---
# <a name="mssqlserver_1401"></a><span data-ttu-id="3266a-102">MSSQLSERVER_1401</span><span class="sxs-lookup"><span data-stu-id="3266a-102">MSSQLSERVER_1401</span></span>
    
## <a name="details"></a><span data-ttu-id="3266a-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="3266a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3266a-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="3266a-104">Product Name</span></span>|<span data-ttu-id="3266a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="3266a-105">SQL Server</span></span>|  
|<span data-ttu-id="3266a-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="3266a-106">Event ID</span></span>|<span data-ttu-id="3266a-107">1401</span><span class="sxs-lookup"><span data-stu-id="3266a-107">1401</span></span>|  
|<span data-ttu-id="3266a-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="3266a-108">Event Source</span></span>|<span data-ttu-id="3266a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3266a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3266a-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="3266a-110">Component</span></span>|<span data-ttu-id="3266a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="3266a-111">SQLEngine</span></span>|  
|<span data-ttu-id="3266a-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="3266a-112">Symbolic Name</span></span>|<span data-ttu-id="3266a-113">DBM_MASTERSTARTUP</span><span class="sxs-lookup"><span data-stu-id="3266a-113">DBM_MASTERSTARTUP</span></span>|  
|<span data-ttu-id="3266a-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="3266a-114">Message Text</span></span>|<span data-ttu-id="3266a-115">다음과 같은 이유로 인해 데이터베이스 미러링 마스터 스레드 루틴을 시작하지 못했습니다: %ls.</span><span class="sxs-lookup"><span data-stu-id="3266a-115">Startup of the database-mirroring master thread routine failed for the following reason: %ls.</span></span> <span data-ttu-id="3266a-116">이 오류의 원인을 수정한 다음 SQL Server 서비스를 다시 시작하십시오.</span><span class="sxs-lookup"><span data-stu-id="3266a-116">Correct the cause of this error, and restart the SQL Server service.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3266a-117">설명</span><span class="sxs-lookup"><span data-stu-id="3266a-117">Explanation</span></span>  
 <span data-ttu-id="3266a-118">미러링 제어 스레드를 시작하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="3266a-118">Startup of the mirroring control thread failed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3266a-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="3266a-119">User Action</span></span>  
 <span data-ttu-id="3266a-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그에서 이 메시지 이전에 발생한 관련 오류를 찾으십시오.</span><span class="sxs-lookup"><span data-stu-id="3266a-120">In the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, look for the associated error that preceded this message.</span></span> <span data-ttu-id="3266a-121">이 오류의 원인을 수정한 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스(MSSQLSERVER)를 다시 시작하세요.</span><span class="sxs-lookup"><span data-stu-id="3266a-121">Correct the cause of this error, and then restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service (MSSQLSERVER).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3266a-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3266a-122">See Also</span></span>  
 [<span data-ttu-id="3266a-123">데이터베이스 엔진, SQL Server 에이전트 또는 SQL Server Browser 서비스 시작, 중지, 일시 중지, 재개 및 다시 시작</span><span class="sxs-lookup"><span data-stu-id="3266a-123">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
  
