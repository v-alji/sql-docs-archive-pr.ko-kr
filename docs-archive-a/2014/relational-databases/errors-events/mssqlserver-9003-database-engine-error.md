---
title: MSSQLSERVER_9003 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9003 (Database Engine error)
ms.assetid: 7fdfb391-5c6f-428b-b434-6c3d0b30fd7b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6f67e4184ea54be6bcd5c2a74d3c0e0711b702f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652845"
---
# <a name="mssqlserver_9003"></a><span data-ttu-id="f4b64-102">MSSQLSERVER_9003</span><span class="sxs-lookup"><span data-stu-id="f4b64-102">MSSQLSERVER_9003</span></span>
    
## <a name="details"></a><span data-ttu-id="f4b64-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="f4b64-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f4b64-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="f4b64-104">Product Name</span></span>|<span data-ttu-id="f4b64-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f4b64-105">SQL Server</span></span>|  
|<span data-ttu-id="f4b64-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="f4b64-106">Event ID</span></span>|<span data-ttu-id="f4b64-107">9003</span><span class="sxs-lookup"><span data-stu-id="f4b64-107">9003</span></span>|  
|<span data-ttu-id="f4b64-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="f4b64-108">Event Source</span></span>|<span data-ttu-id="f4b64-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f4b64-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f4b64-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="f4b64-110">Component</span></span>|<span data-ttu-id="f4b64-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f4b64-111">SQLEngine</span></span>|  
|<span data-ttu-id="f4b64-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="f4b64-112">Symbolic Name</span></span>|<span data-ttu-id="f4b64-113">LOG_INVALID_LSN</span><span class="sxs-lookup"><span data-stu-id="f4b64-113">LOG_INVALID_LSN</span></span>|  
|<span data-ttu-id="f4b64-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="f4b64-114">Message Text</span></span>|<span data-ttu-id="f4b64-115">데이터베이스 '%.\*ls'의 로그 검색으로 전달된 로그 검색 번호 %S_LSN이(가) 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f4b64-115">The log scan number %S_LSN passed to log scan in database '%.\*ls' is not valid.</span></span> <span data-ttu-id="f4b64-116">데이터가 손상되었거나 로그 파일(.ldf)과 데이터 파일(.mdf)이 일치하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f4b64-116">This error may indicate data corruption or that the log file (.ldf) does not match the data file (.mdf).</span></span> <span data-ttu-id="f4b64-117">복제하는 동안 이 오류가 발생한 경우 게시를 다시 만드십시오.</span><span class="sxs-lookup"><span data-stu-id="f4b64-117">If this error occurred during replication, re-create the publication.</span></span> <span data-ttu-id="f4b64-118">그 외의 경우 이 문제로 인해 시작하는 동안 오류가 발생하면 백업을 사용하여 복원하십시오.</span><span class="sxs-lookup"><span data-stu-id="f4b64-118">Otherwise, restore from backup if the problem results in a failure during startup.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f4b64-119">설명</span><span class="sxs-lookup"><span data-stu-id="f4b64-119">Explanation</span></span>  
 <span data-ttu-id="f4b64-120">구성 요소가 데이터베이스의 로그 관리자에 잘못된 로그 시퀀스 번호를 전달했습니다.</span><span class="sxs-lookup"><span data-stu-id="f4b64-120">A component passed an invalid log sequence number to the log manager for the database.</span></span> <span data-ttu-id="f4b64-121">이는 복제, 손상 또는 주 데이터 파일과 로그 간의 불일치일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4b64-121">This could be replication, corruption, or an inconsistency between the primary data file and the log.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f4b64-122">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="f4b64-122">User Action</span></span>  
 <span data-ttu-id="f4b64-123">복제하는 동안 이 오류가 발생한 경우 게시를 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f4b64-123">If this occurred during replication, recreate the publication.</span></span> <span data-ttu-id="f4b64-124">그렇지 않으면 백업에서 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="f4b64-124">Otherwise, restore from backup.</span></span>  
  
  
