---
title: MSSQLSERVER_21892 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21892 (Database Engine error)
ms.assetid: 199818e8-28f4-440e-ad85-7bea88f51153
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5fd3bfa1213f0569293991d6bd759619c6e7b596
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740023"
---
# <a name="mssqlserver_21892"></a><span data-ttu-id="9c04e-102">MSSQLSERVER_21892</span><span class="sxs-lookup"><span data-stu-id="9c04e-102">MSSQLSERVER_21892</span></span>
    
## <a name="details"></a><span data-ttu-id="9c04e-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="9c04e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9c04e-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="9c04e-104">Product Name</span></span>|<span data-ttu-id="9c04e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9c04e-105">SQL Server</span></span>|  
|<span data-ttu-id="9c04e-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="9c04e-106">Event ID</span></span>|<span data-ttu-id="9c04e-107">21892</span><span class="sxs-lookup"><span data-stu-id="9c04e-107">21892</span></span>|  
|<span data-ttu-id="9c04e-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="9c04e-108">Event Source</span></span>|<span data-ttu-id="9c04e-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9c04e-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9c04e-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="9c04e-110">Component</span></span>|<span data-ttu-id="9c04e-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9c04e-111">SQLEngine</span></span>|  
|<span data-ttu-id="9c04e-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="9c04e-112">Symbolic Name</span></span>|<span data-ttu-id="9c04e-113">SQLErrorNum21892</span><span class="sxs-lookup"><span data-stu-id="9c04e-113">SQLErrorNum21892</span></span>|  
|<span data-ttu-id="9c04e-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="9c04e-114">Message Text</span></span>|<span data-ttu-id="9c04e-115">멤버 복제본의 서버 이름에 대해 가상 네트워크 이름 '%s'과(와) 연관된 가용성 그룹 주 복제본에서 sys.availability_replicas를 쿼리할 수 없습니다. 오류 = %d, 오류 메시지 = %s.',</span><span class="sxs-lookup"><span data-stu-id="9c04e-115">Unable to query sys.availability_replicas at the availability group primary associated with virtual network name '%s' for the server names of the member replicas: error = %d, error message = %s.',</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9c04e-116">설명</span><span class="sxs-lookup"><span data-stu-id="9c04e-116">Explanation</span></span>  
 <span data-ttu-id="9c04e-117">`sp_validate_replica_hosts_as_publishers`는 리디렉션된 게시자와 연관된 가용성 그룹의 현재 주 복제본을 쿼리하여 멤버 복제본을 호스팅하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9c04e-117">`sp_validate_replica_hosts_as_publishers` queries the current primary of the availability group associated with the redirected publisher, to determine the instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that host the member replicas.</span></span>  <span data-ttu-id="9c04e-118">이 쿼리에 실패하면 오류 21892가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c04e-118">When this query fails, error 21892 is returned.</span></span>  
  
 <span data-ttu-id="9c04e-119">`sp_validate_replica_hosts_as_publishers`는 일반적으로 임시 연결된 서버를 처음 사용할 때 수행되므로 연결 문제가 있을 경우 가장 먼저 `sp_validate_replica_hosts_as_publishers`에서 연결 문제가 나타날 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="9c04e-119">`sp_validate_replica_hosts_as_publishers` is typically on of the first use of the temporary linked server, so if there are connectivity problems they are likely to appear first with `sp_validate_replica_hosts_as_publishers`.</span></span> <span data-ttu-id="9c04e-120">`sp_validate_redirected_publisher`와 달리 `sp_validate_replica_hosts_as_publishers`에서 사용하는 연결된 서버는 항상 가용성 그룹 복제본 호스트에 연결할 때 호출자의 자격 증명을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9c04e-120">Unlike `sp_validate_redirected_publisher`, the linked server used by `sp_validate_replica_hosts_as_publishers` always uses the credentials of the caller when connecting to any of the availability group replica hosts.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9c04e-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="9c04e-121">User Action</span></span>  
 <span data-ttu-id="9c04e-122">이 저장 프로시저는 모든 복제본에서 유효한 로그인을 사용하여 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c04e-122">When running this stored procedure, made certain that you run from a login that is valid on all of the replicas.</span></span> <span data-ttu-id="9c04e-123">이 로그인에 충분한 권한이 있어야만 가용성 그룹 메타데이터 테이블 및 게시자 데이터베이스 복제본에 있는 구독 메타데이터 테이블을 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c04e-123">The login will require sufficient authorization to query availability group metadata tables as well as to query the subscription metadata tables in the publisher database replica.</span></span>  
  
 <span data-ttu-id="9c04e-124">참조된 원래 오류를 검토하여 실패 원인을 파악하고 적절한 수정 동작을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="9c04e-124">Examine the original referenced error to determine the cause of the failure and appropriate corrective action.</span></span>  
  
  
