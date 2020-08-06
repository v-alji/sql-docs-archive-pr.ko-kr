---
title: MSSQLSERVER_21871 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21871 (Database Engine error)
ms.assetid: d3215378-9282-444f-a18b-00b96fd0133d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f26211da21829a0a898dfb36ff9fefd453c7ad44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731643"
---
# <a name="mssqlserver_21871"></a><span data-ttu-id="3aa1e-102">MSSQLSERVER_21871</span><span class="sxs-lookup"><span data-stu-id="3aa1e-102">MSSQLSERVER_21871</span></span>
    
## <a name="details"></a><span data-ttu-id="3aa1e-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="3aa1e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3aa1e-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="3aa1e-104">Product Name</span></span>|<span data-ttu-id="3aa1e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="3aa1e-105">SQL Server</span></span>|  
|<span data-ttu-id="3aa1e-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="3aa1e-106">Event ID</span></span>|<span data-ttu-id="3aa1e-107">21871</span><span class="sxs-lookup"><span data-stu-id="3aa1e-107">21871</span></span>|  
|<span data-ttu-id="3aa1e-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="3aa1e-108">Event Source</span></span>|<span data-ttu-id="3aa1e-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3aa1e-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3aa1e-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="3aa1e-110">Component</span></span>|<span data-ttu-id="3aa1e-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="3aa1e-111">SQLEngine</span></span>|  
|<span data-ttu-id="3aa1e-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="3aa1e-112">Symbolic Name</span></span>|<span data-ttu-id="3aa1e-113">SQLErrorNum21871</span><span class="sxs-lookup"><span data-stu-id="3aa1e-113">SQLErrorNum21871</span></span>|  
|<span data-ttu-id="3aa1e-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="3aa1e-114">Message Text</span></span>|<span data-ttu-id="3aa1e-115">데이터베이스 %s의 게시자 %s이(가) 리디렉션되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="3aa1e-115">Publisher %s of database %s has not been redirected.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3aa1e-116">설명</span><span class="sxs-lookup"><span data-stu-id="3aa1e-116">Explanation</span></span>  
 <span data-ttu-id="3aa1e-117">`sp_validate_replica_hosts_as_publishers`는 식별된 게시자 및 게시자 데이터베이스에 대한 항목이 있는지 확인하기 위해 배포 데이터베이스의 MSredirected_publishers 테이블을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3aa1e-117">`sp_validate_replica_hosts_as_publishers` checks the table MSredirected_publishers in the distribution database for an entry for the identified publisher and publisher database.</span></span>  <span data-ttu-id="3aa1e-118">항목이 없으면 `sp_validate_replica_hosts_as_publishers`가 오류 21871을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3aa1e-118">`sp_validate_replica_hosts_as_publishers` returns error 21871 when no entry is found.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3aa1e-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="3aa1e-119">User Action</span></span>  
 <span data-ttu-id="3aa1e-120">`sp_validate_replica_hosts_as_publishers`는 리디렉션된 게시자와만 관련됩니다.</span><span class="sxs-lookup"><span data-stu-id="3aa1e-120">`sp_validate_replica_hosts_as_publishers` is only relevant for redirected publishers.</span></span> <span data-ttu-id="3aa1e-121">게시자 데이터베이스가 가용성 그룹의 멤버인 경우에는 `sp_redirect_publisher` 저장 프로시저를 사용하여 게시자 및 게시자 데이터베이스에 가용성 그룹의 가용성 그룹 수신기 이름을 연결하십시오.</span><span class="sxs-lookup"><span data-stu-id="3aa1e-121">If the publisher database is a member of an availability group, use the stored procedure `sp_redirect_publisher` to associate the publisher and publisher database with the Availability Group Listener Name of the availability group.</span></span>  
  
  
