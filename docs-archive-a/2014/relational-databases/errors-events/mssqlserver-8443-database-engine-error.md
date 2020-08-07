---
title: MSSQLSERVER_8443 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8443 (Database Engine error)
ms.assetid: a3541b9c-b1a8-4280-add1-275f08696b62
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ae02cc0d9e5661f4069884c22bf6eea0697bd2d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735279"
---
# <a name="mssqlserver_8443"></a><span data-ttu-id="9f69e-102">MSSQLSERVER_8443</span><span class="sxs-lookup"><span data-stu-id="9f69e-102">MSSQLSERVER_8443</span></span>
    
## <a name="details"></a><span data-ttu-id="9f69e-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="9f69e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9f69e-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="9f69e-104">Product Name</span></span>|<span data-ttu-id="9f69e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9f69e-105">SQL Server</span></span>|  
|<span data-ttu-id="9f69e-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="9f69e-106">Event ID</span></span>|<span data-ttu-id="9f69e-107">8443</span><span class="sxs-lookup"><span data-stu-id="9f69e-107">8443</span></span>|  
|<span data-ttu-id="9f69e-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="9f69e-108">Event Source</span></span>|<span data-ttu-id="9f69e-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9f69e-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9f69e-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="9f69e-110">Component</span></span>|<span data-ttu-id="9f69e-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9f69e-111">SQLEngine</span></span>|  
|<span data-ttu-id="9f69e-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="9f69e-112">Symbolic Name</span></span>|<span data-ttu-id="9f69e-113">SB_DIALOG_WO_CONV_GROUP</span><span class="sxs-lookup"><span data-stu-id="9f69e-113">SB_DIALOG_WO_CONV_GROUP</span></span>|  
|<span data-ttu-id="9f69e-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="9f69e-114">Message Text</span></span>|<span data-ttu-id="9f69e-115">ID가 '%.\*ls'이고 시작자가 %d인 대화가 누락된 대화 그룹 '%.\*ls'을(를) 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="9f69e-115">The conversation with ID '%.\*ls' and initiator %d references a missing conversation group '%.\*ls'.</span></span> <span data-ttu-id="9f69e-116">DBCC CHECKDB를 실행하여 데이터베이스를 분석 및 복구하십시오.</span><span class="sxs-lookup"><span data-stu-id="9f69e-116">Run DBCC CHECKDB to analyze and repair the database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9f69e-117">설명</span><span class="sxs-lookup"><span data-stu-id="9f69e-117">Explanation</span></span>  
 <span data-ttu-id="9f69e-118">메타데이터 계층에서 대화 그룹에 대해 NULL을 반환했습니다.</span><span class="sxs-lookup"><span data-stu-id="9f69e-118">The metadata layer returned NULL for the conversation group.</span></span> <span data-ttu-id="9f69e-119">데이터베이스가 일부 손상되었으며</span><span class="sxs-lookup"><span data-stu-id="9f69e-119">The database has been corrupted in some way.</span></span> <span data-ttu-id="9f69e-120">가능한 손상 원인 중 하나는 디스크 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="9f69e-120">One possible source of corruption is a disk error.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9f69e-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="9f69e-121">User Action</span></span>  
 <span data-ttu-id="9f69e-122">DBCC CHECKDB를 복구 모드로 실행하여 데이터베이스를 일관된 상태로 복구하십시오.</span><span class="sxs-lookup"><span data-stu-id="9f69e-122">Run DBCC CHECKDB in repair mode to bring the database back into a consistent state.</span></span> <span data-ttu-id="9f69e-123">필요한 경우 일관성을 복원하기 위해 메시지를 삭제할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f69e-123">It may delete messages if necessary to restore consistency.</span></span> <span data-ttu-id="9f69e-124">시스템 오류 로그를 조사하여 시스템 내의 다른 실패로 인해 이 오류가 발생했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="9f69e-124">Investigate system error logs to see if this error was caused by another failure in the system.</span></span>  
  
  
