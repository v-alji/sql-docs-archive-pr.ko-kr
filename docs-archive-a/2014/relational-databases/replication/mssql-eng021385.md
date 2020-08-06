---
title: MSSQL_ENG021385 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021385 error
ms.assetid: a2c0444f-d97b-4760-8905-3574791c2e26
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b73d3216f07cb44d750a37149634258648f1bd48
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730496"
---
# <a name="mssql_eng021385"></a><span data-ttu-id="7da73-102">MSSQL_ENG021385</span><span class="sxs-lookup"><span data-stu-id="7da73-102">MSSQL_ENG021385</span></span>
    
## <a name="message-details"></a><span data-ttu-id="7da73-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="7da73-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7da73-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="7da73-104">Product Name</span></span>|<span data-ttu-id="7da73-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="7da73-105">SQL Server</span></span>|  
|<span data-ttu-id="7da73-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="7da73-106">Event ID</span></span>|<span data-ttu-id="7da73-107">21385</span><span class="sxs-lookup"><span data-stu-id="7da73-107">21385</span></span>|  
|<span data-ttu-id="7da73-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="7da73-108">Event Source</span></span>|<span data-ttu-id="7da73-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7da73-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7da73-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="7da73-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="7da73-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="7da73-111">Symbolic Name</span></span>||  
|<span data-ttu-id="7da73-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="7da73-112">Message Text</span></span>|<span data-ttu-id="7da73-113">스냅샷이 게시 '%s'을(를) 처리하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="7da73-113">Snapshot failed to process publication '%s'.</span></span> <span data-ttu-id="7da73-114">활성 스키마 변경 작업 또는 추가 중인 새 아티클 때문인 것 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7da73-114">Possibly due to active schema change activity or new articles being added.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7da73-115">설명</span><span class="sxs-lookup"><span data-stu-id="7da73-115">Explanation</span></span>  
 <span data-ttu-id="7da73-116">아티클 추가 또는 삭제 및 게시된 개체의 스키마 변경 등 게시 데이터베이스에 진행 중인 변경 내용이 있을 때 스냅샷 에이전트가 실행되면 이 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="7da73-116">This error is raised if the Snapshot Agent starts running when there are ongoing changes to the publication database, including adding or dropping articles and performing schema changes on published objects.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7da73-117">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="7da73-117">User Action</span></span>  
 <span data-ttu-id="7da73-118">게시 데이터베이스에 대한 변경이 완료된 후에 스냅샷 에이전트를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="7da73-118">Restart the Snapshot Agent after changes to the publication database are complete.</span></span> <span data-ttu-id="7da73-119">자세한 내용은 [복제 에이전트 시작 및 중지&#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) 및 [복제 에이전트 실행 파일 개념](concepts/replication-agent-executables-concepts.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7da73-119">For more information, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) and [Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7da73-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7da73-120">See Also</span></span>  
 [<span data-ttu-id="7da73-121">오류 및 이벤트 참조&#40;복제&#41;</span><span class="sxs-lookup"><span data-stu-id="7da73-121">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
