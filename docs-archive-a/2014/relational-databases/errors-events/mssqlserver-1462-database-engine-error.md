---
title: MSSQLSERVER_1462 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1462 (Database Engine error)
ms.assetid: 680e9c1c-a9d6-4765-b601-956d0a83324c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 704b847bde2d7b4da9da91b4b24bfe2b9e2afa07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653945"
---
# <a name="mssqlserver_1462"></a><span data-ttu-id="e9ca6-102">MSSQLSERVER_1462</span><span class="sxs-lookup"><span data-stu-id="e9ca6-102">MSSQLSERVER_1462</span></span>
    
## <a name="details"></a><span data-ttu-id="e9ca6-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="e9ca6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e9ca6-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="e9ca6-104">Product Name</span></span>|<span data-ttu-id="e9ca6-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e9ca6-105">SQL Server</span></span>|  
|<span data-ttu-id="e9ca6-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="e9ca6-106">Event ID</span></span>|<span data-ttu-id="e9ca6-107">1462</span><span class="sxs-lookup"><span data-stu-id="e9ca6-107">1462</span></span>|  
|<span data-ttu-id="e9ca6-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="e9ca6-108">Event Source</span></span>|<span data-ttu-id="e9ca6-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e9ca6-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e9ca6-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="e9ca6-110">Component</span></span>|<span data-ttu-id="e9ca6-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e9ca6-111">SQLEngine</span></span>|  
|<span data-ttu-id="e9ca6-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="e9ca6-112">Symbolic Name</span></span>|<span data-ttu-id="e9ca6-113">DBM_DISABLED_DUE_TO_FAILED_REDO</span><span class="sxs-lookup"><span data-stu-id="e9ca6-113">DBM_DISABLED_DUE_TO_FAILED_REDO</span></span>|  
|<span data-ttu-id="e9ca6-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="e9ca6-114">Message Text</span></span>|<span data-ttu-id="e9ca6-115">실패한 다시 실행 작업으로 인해 데이터베이스 미러링이 비활성화되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e9ca6-115">Database mirroring is disabled due to a failed redo operation.</span></span> <span data-ttu-id="e9ca6-116">재개할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e9ca6-116">Unable to resume.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e9ca6-117">설명</span><span class="sxs-lookup"><span data-stu-id="e9ca6-117">Explanation</span></span>  
 <span data-ttu-id="e9ca6-118">데이터베이스 미러링이 미러의 로그 레코드를 다시 실행하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="e9ca6-118">Database mirroring failed to redo a log record on the mirror.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="e9ca6-119">가능한 원인</span><span class="sxs-lookup"><span data-stu-id="e9ca6-119">Possible Causes</span></span>  
 <span data-ttu-id="e9ca6-120">주 데이터베이스에서는 파일 추가 작업을 완료했지만 파일 이름 또는 디렉터리 구조가 주 서버 및 미러 서버와 다르기 때문에 미러 데이터베이스에서는 파일 추가 작업에 실패했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9ca6-120">The most likely cause is that an add-file operation completed on the principal database but then failed on the mirror database because file names or directory structures differ on the principal server and mirror server.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e9ca6-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="e9ca6-121">User Action</span></span>  
 <span data-ttu-id="e9ca6-122">이 오류의 원인에 대한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ca6-122">Look in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log for the cause of this error.</span></span> <span data-ttu-id="e9ca6-123">원인을 해결하고 데이터베이스의 미러링을 재개합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ca6-123">Try to resolve the cause and resume mirroring on the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9ca6-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e9ca6-124">See Also</span></span>  
 [<span data-ttu-id="e9ca6-125">데이터베이스 미러링 구성 문제 해결&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e9ca6-125">Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/troubleshoot-database-mirroring-configuration-sql-server.md)  
  
  
