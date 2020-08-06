---
title: MSSQLSERVER_41030 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41030 (Database Engine error)
ms.assetid: c85341ae-0fbf-42ae-9275-4cfe678238f0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b137b739d4c1641b88983708df62d2e52fd0eab5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736370"
---
# <a name="mssqlserver_41030"></a><span data-ttu-id="cd2d6-102">MSSQLSERVER_41030</span><span class="sxs-lookup"><span data-stu-id="cd2d6-102">MSSQLSERVER_41030</span></span>
    
## <a name="details"></a><span data-ttu-id="cd2d6-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="cd2d6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cd2d6-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="cd2d6-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="cd2d6-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="cd2d6-105">Event ID</span></span>|<span data-ttu-id="cd2d6-106">41030</span><span class="sxs-lookup"><span data-stu-id="cd2d6-106">41030</span></span>|  
|<span data-ttu-id="cd2d6-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="cd2d6-107">Event Source</span></span>|<span data-ttu-id="cd2d6-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="cd2d6-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="cd2d6-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="cd2d6-109">Component</span></span>|<span data-ttu-id="cd2d6-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="cd2d6-110">SQLEngine</span></span>|  
|<span data-ttu-id="cd2d6-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="cd2d6-111">Symbolic Name</span></span>|<span data-ttu-id="cd2d6-112">OPEN_CLUSTER_SUB_KEY</span><span class="sxs-lookup"><span data-stu-id="cd2d6-112">OPEN_CLUSTER_SUB_KEY</span></span>|  
|<span data-ttu-id="cd2d6-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="cd2d6-113">Message Text</span></span>|<span data-ttu-id="cd2d6-114">Windows Server 장애 조치(Failover) 클러스터링 레지스트리 하위 키 '%.\*ls'을(를) 열지 못했습니다(오류 코드 %d).</span><span class="sxs-lookup"><span data-stu-id="cd2d6-114">Failed to open the Windows Server Failover Clustering registry subkey '%.\*ls' (Error code %d).</span></span>  <span data-ttu-id="cd2d6-115">부모 키는 클러스터 루트 키입니다.</span><span class="sxs-lookup"><span data-stu-id="cd2d6-115">The parent key is the cluster root key.</span></span>  <span data-ttu-id="cd2d6-116">WSFC 서비스가 실행 중이 아니거나 현재 상태에서 액세스할 수 없거나 지정된 인수가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cd2d6-116">The WSFC service may not be running or may not be accessible in its current state, or the specified arguments are invalid.</span></span> <span data-ttu-id="cd2d6-117">해당 가용성 그룹이 삭제된 경우 이 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd2d6-117">If the corresponding availability group has been dropped, this error is expected.</span></span> <span data-ttu-id="cd2d6-118">이 오류 코드에 대한 자세한 내용은 Windows 개발 설명서의 "시스템 오류 코드"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="cd2d6-118">For information about this error code, see "System Error Codes" in the Windows Development documentation.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cd2d6-119">설명</span><span class="sxs-lookup"><span data-stu-id="cd2d6-119">Explanation</span></span>  
 <span data-ttu-id="cd2d6-120">WSFC 클러스터가 제거된 경우 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]과 관련된 모든 레지스트리 키가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd2d6-120">If a WSFC cluster is destroyed, it removes all registry keys related to [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cd2d6-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="cd2d6-121">User Action</span></span>  
 <span data-ttu-id="cd2d6-122">WSFC 클러스터를 다시 만든 후 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 인스턴스가 AlwaysOn에 설정된 모든 클러스터 노드에서 AlwaysOn을 해제한 다음 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cd2d6-122">After re-creating a WSFC cluster, disable and then re-enable AlwaysOn on every cluster node on which an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is enabled for AlwaysOn.</span></span> <span data-ttu-id="cd2d6-123">이 태스크에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd2d6-123">You can use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager for this task.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd2d6-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cd2d6-124">See Also</span></span>  
 <span data-ttu-id="cd2d6-125">[AlwaysOn 가용성 그룹 &#40;SQL Server 사용 및 사용 안 함&#41;](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cd2d6-125">[Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="cd2d6-126">SQL Server의 WSFC&#40;Windows Server 장애 조치(failover) 클러스터링&#41;</span><span class="sxs-lookup"><span data-stu-id="cd2d6-126">Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server</span></span>](../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)  
  
  
