---
title: SQL Server 2014에서 사용 되지 않는 관리 도구 기능 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: a08d1354-cc91-4ab7-a73f-3ad815af3d5a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 484e4078e25249e17a1d8b87426a395c3cfa1725
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648551"
---
# <a name="deprecated-management-tools-features-in-sql-server-2014"></a><span data-ttu-id="7c8f2-102">SQL Server 2014에서 사용되지 않는 관리 도구 기능</span><span class="sxs-lookup"><span data-stu-id="7c8f2-102">Deprecated Management Tools Features in SQL Server 2014</span></span>
  <span data-ttu-id="7c8f2-103">이 항목에서는 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]에서 계속 제공되지만 더 이상 사용되지 않는 관리 도구 기능에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7c8f2-103">This topic describes the deprecated Management Tools features that are still available in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="7c8f2-104">이러한 기능은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 이후 릴리스에서 제거될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="7c8f2-104">These features are scheduled to be removed in a future release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7c8f2-105">새 애플리케이션에는 이러한 기능을 사용하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c8f2-105">Deprecated features should not be used in new applications.</span></span>  
  
|<span data-ttu-id="7c8f2-106">기능</span><span class="sxs-lookup"><span data-stu-id="7c8f2-106">Feature</span></span>|<span data-ttu-id="7c8f2-107">사용 중단 단계</span><span class="sxs-lookup"><span data-stu-id="7c8f2-107">Deprecation stage</span></span>|  
|-------------|-----------------------|  
|[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]<span data-ttu-id="7c8f2-108">등록 된 서버 API</span><span class="sxs-lookup"><span data-stu-id="7c8f2-108">Registered Server API</span></span>|<span data-ttu-id="7c8f2-109">알림</span><span class="sxs-lookup"><span data-stu-id="7c8f2-109">Announcement</span></span>|  
|<span data-ttu-id="7c8f2-110">sqlps.exe</span><span class="sxs-lookup"><span data-stu-id="7c8f2-110">sqlps.exe</span></span>|<span data-ttu-id="7c8f2-111">경고</span><span class="sxs-lookup"><span data-stu-id="7c8f2-111">Warning</span></span>|  
|<span data-ttu-id="7c8f2-112">osql.exe</span><span class="sxs-lookup"><span data-stu-id="7c8f2-112">osql.exe</span></span>|<span data-ttu-id="7c8f2-113">경고</span><span class="sxs-lookup"><span data-stu-id="7c8f2-113">Warning</span></span>|  
|<span data-ttu-id="7c8f2-114">SQLMail</span><span class="sxs-lookup"><span data-stu-id="7c8f2-114">SQLMail</span></span>|<span data-ttu-id="7c8f2-115">경고</span><span class="sxs-lookup"><span data-stu-id="7c8f2-115">Warning</span></span>|  
|<span data-ttu-id="7c8f2-116">SMO 클래스: Microsoft.SQLServer.Management.Smo.Information 클래스</span><span class="sxs-lookup"><span data-stu-id="7c8f2-116">SMO class: Microsoft.SQLServer.Management.Smo.Information class</span></span>|<span data-ttu-id="7c8f2-117">알림</span><span class="sxs-lookup"><span data-stu-id="7c8f2-117">Announcement</span></span>|  
|<span data-ttu-id="7c8f2-118">SMO 클래스: Microsoft.SQLServer.Management.Smo.Settings 클래스</span><span class="sxs-lookup"><span data-stu-id="7c8f2-118">SMO class: Microsoft.SQLServer.Management.Smo.Settings class</span></span>|<span data-ttu-id="7c8f2-119">알림</span><span class="sxs-lookup"><span data-stu-id="7c8f2-119">Announcement</span></span>|  
|<span data-ttu-id="7c8f2-120">SMO 클래스: Microsoft.SQLServer.Management.Smo.DatabaseOptions 클래스</span><span class="sxs-lookup"><span data-stu-id="7c8f2-120">SMO Class: Microsoft.SQLServer.Management.Smo.DatabaseOptions class</span></span>|<span data-ttu-id="7c8f2-121">알림</span><span class="sxs-lookup"><span data-stu-id="7c8f2-121">Announcement</span></span>|  
|<span data-ttu-id="7c8f2-122">SMO 클래스: Microsoft.SqlServer.Management.Smo.DatabaseDdlTrigger.NotForReplication 속성</span><span class="sxs-lookup"><span data-stu-id="7c8f2-122">SMO Class: Microsoft.SqlServer.Management.Smo.DatabaseDdlTrigger.NotForReplication property</span></span>|<span data-ttu-id="7c8f2-123">알림</span><span class="sxs-lookup"><span data-stu-id="7c8f2-123">Announcement</span></span>|  
|<span data-ttu-id="7c8f2-124">SSMS의 데이터베이스 프로젝트 시스템(예: 원본 제어 통합)</span><span class="sxs-lookup"><span data-stu-id="7c8f2-124">The Database Project System, including source-control integration, in SSMS</span></span>|<span data-ttu-id="7c8f2-125">알림</span><span class="sxs-lookup"><span data-stu-id="7c8f2-125">Announcement</span></span>|  
|<span data-ttu-id="7c8f2-126">Net send 알림([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트)</span><span class="sxs-lookup"><span data-stu-id="7c8f2-126">Net send notifications ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent)</span></span>|<span data-ttu-id="7c8f2-127">알림</span><span class="sxs-lookup"><span data-stu-id="7c8f2-127">Announcement</span></span>|  
|<span data-ttu-id="7c8f2-128">호출기 알림([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트)</span><span class="sxs-lookup"><span data-stu-id="7c8f2-128">Pager notifications ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent)</span></span>|<span data-ttu-id="7c8f2-129">알림</span><span class="sxs-lookup"><span data-stu-id="7c8f2-129">Announcement</span></span>|  
|<span data-ttu-id="7c8f2-130">ActiveX 하위 시스템([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트)</span><span class="sxs-lookup"><span data-stu-id="7c8f2-130">The ActiveX subsystem ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent)</span></span>|<span data-ttu-id="7c8f2-131">알림</span><span class="sxs-lookup"><span data-stu-id="7c8f2-131">Announcement</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7c8f2-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7c8f2-132">See Also</span></span>  
 [<span data-ttu-id="7c8f2-133">이전 버전과의 호환성</span><span class="sxs-lookup"><span data-stu-id="7c8f2-133">Backward Compatibility</span></span>](../../2014/getting-started/backward-compatibility.md)  
  
  
