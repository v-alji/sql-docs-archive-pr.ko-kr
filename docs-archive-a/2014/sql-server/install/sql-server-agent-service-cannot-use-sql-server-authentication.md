---
title: SQL Server 에이전트 서비스에서 SQL Server 인증을 사용할 수 없습니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- authentication [SQL Server Agent]
- SQL Server Authentication [SQL Server Agent]
ms.assetid: c39f3ec3-fc2c-4c12-940f-60d8d3d17660
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 32188b1c47168aefbca914fa15f71850df716153
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652551"
---
# <a name="sql-server-agent-service-cannot-use-sql-server-authentication"></a><span data-ttu-id="7d2b2-102">SQL Server 에이전트 서비스는 SQL Server 인증을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7d2b2-102">SQL Server Agent Service cannot use SQL Server Authentication</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7d2b2-103">에이전트에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 인스턴스에 연결될 때 Windows 인증만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d2b2-103">Agent only supports Windows Authentication when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service connects to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="component"></a><span data-ttu-id="7d2b2-104">구성 요소</span><span class="sxs-lookup"><span data-stu-id="7d2b2-104">Component</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7d2b2-105">에이전트</span><span class="sxs-lookup"><span data-stu-id="7d2b2-105">Agent</span></span>  
  
## <a name="description"></a><span data-ttu-id="7d2b2-106">Description</span><span class="sxs-lookup"><span data-stu-id="7d2b2-106">Description</span></span>  
 <span data-ttu-id="7d2b2-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스는 Windows 인증을 사용해서만 데이터베이스에 로그온할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d2b2-107">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service can only log on to the database using Windows Authentication.</span></span> <span data-ttu-id="7d2b2-108">즉, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스 계정이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d2b2-108">This means that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account must be a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user.</span></span>  
  
 <span data-ttu-id="7d2b2-109">자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 "자동 관리를 위한 보안" 및 " [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 보안 구현"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7d2b2-109">For more information, see the topics "Security for Automatic Administration" and "Implementing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Security" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d2b2-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7d2b2-110">See Also</span></span>  
 [<span data-ttu-id="7d2b2-111">SQL Server 에이전트 업그레이드 문제</span><span class="sxs-lookup"><span data-stu-id="7d2b2-111">SQL Server Agent Upgrade Issues</span></span>](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
