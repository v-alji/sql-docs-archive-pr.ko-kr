---
title: MSSQLSERVER_1458 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1458 (Database Engine error)
ms.assetid: adc78c59-a6f2-432b-9a07-fdd1dc2b9026
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: efa45177a92402b25099be5bb3e3dcc91a5fa6d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653948"
---
# <a name="mssqlserver_1458"></a><span data-ttu-id="14341-102">MSSQLSERVER_1458</span><span class="sxs-lookup"><span data-stu-id="14341-102">MSSQLSERVER_1458</span></span>
    
## <a name="details"></a><span data-ttu-id="14341-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="14341-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="14341-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="14341-104">Product Name</span></span>|<span data-ttu-id="14341-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="14341-105">SQL Server</span></span>|  
|<span data-ttu-id="14341-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="14341-106">Event ID</span></span>|<span data-ttu-id="14341-107">1458</span><span class="sxs-lookup"><span data-stu-id="14341-107">1458</span></span>|  
|<span data-ttu-id="14341-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="14341-108">Event Source</span></span>|<span data-ttu-id="14341-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="14341-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="14341-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="14341-110">Component</span></span>|<span data-ttu-id="14341-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="14341-111">SQLEngine</span></span>|  
|<span data-ttu-id="14341-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="14341-112">Symbolic Name</span></span>|<span data-ttu-id="14341-113">DBM_FAILREDO_ON_PRIMARY</span><span class="sxs-lookup"><span data-stu-id="14341-113">DBM_FAILREDO_ON_PRIMARY</span></span>|  
|<span data-ttu-id="14341-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="14341-114">Message Text</span></span>|<span data-ttu-id="14341-115">'%.\*ls' 데이터베이스의 주 복사본에 오류 %d, 상태 %d, 심각도 %d이(가) 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="14341-115">The principal copy of the '%.\*ls' database encountered error %d, status %d, severity %d.</span></span> <span data-ttu-id="14341-116">데이터베이스 미러링이 일시 중지되었습니다.</span><span class="sxs-lookup"><span data-stu-id="14341-116">Database mirroring has been suspended.</span></span> <span data-ttu-id="14341-117">오류 상태를 해결한 다음 미러링을 재개하십시오.</span><span class="sxs-lookup"><span data-stu-id="14341-117">Try to resolve the error condition, and resume mirroring.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="14341-118">설명</span><span class="sxs-lookup"><span data-stu-id="14341-118">Explanation</span></span>  
 <span data-ttu-id="14341-119">이 메시지는 주 데이터베이스에 오류가 발생하여 데이터베이스 미러링이 일시 중지되었음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="14341-119">This messages indicates that the principal database encountered an error that caused database mirroring to be suspended.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="14341-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="14341-120">User Action</span></span>  
 <span data-ttu-id="14341-121">이러한 오류의 대부분은 자체적으로 수정됩니다.</span><span class="sxs-lookup"><span data-stu-id="14341-121">Most cases of this error are self correcting.</span></span> <span data-ttu-id="14341-122">문제가 지속되는 경우 일반적으로 데이터베이스 또는 서버 인스턴스를 다시 시작하면 문제가 해결됩니다.</span><span class="sxs-lookup"><span data-stu-id="14341-122">If the problem persists, restarting the database or server instance typically corrects the problem.</span></span> <span data-ttu-id="14341-123">자세한 내용은 이 메시지 앞에 나오는 관련 오류에 대한 각 파트너의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="14341-123">For more information, look in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log on each partner for the associated error that preceded this message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14341-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="14341-124">See Also</span></span>  
 [<span data-ttu-id="14341-125">데이터베이스 미러링 모니터링&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="14341-125">Monitoring Database Mirroring &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
