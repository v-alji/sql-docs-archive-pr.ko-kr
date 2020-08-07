---
title: SQL Server 이전 버전과의 호환성 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ac47cb74-5578-417d-bcef-f970d9527705
author: rothja
ms.author: jroth
ms.openlocfilehash: a4d38041ce4daa12911dc706d382460324931c90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730847"
---
# <a name="sql-server-backward-compatibility"></a><span data-ttu-id="6522d-102">이전 SQL Server 버전과의 호환성</span><span class="sxs-lookup"><span data-stu-id="6522d-102">SQL Server Backward Compatibility</span></span>
  <span data-ttu-id="6522d-103">이전 버전과의 호환성 섹션의 항목에서는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 버전 간에 변경된 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]동작을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6522d-103">Topics in the backward compatibility section describe changes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] behavior between versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="6522d-104">이 항목에 포함되어 있는 기능에는 데이터 프로그래밍 기능, 노출 영역 구성 도구, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 설치 프로그램, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 서비스 및 기타 광범위한 기능 변경 내용이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6522d-104">Features included in this topic area include data programmability, surface area configuration tools, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Setup, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] services, and other broad functionality changes.</span></span>  
  
|<span data-ttu-id="6522d-105">항목</span><span class="sxs-lookup"><span data-stu-id="6522d-105">Topic</span></span>|<span data-ttu-id="6522d-106">설명</span><span class="sxs-lookup"><span data-stu-id="6522d-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="6522d-107">SQL Server 2014 이후에는 사용되지 않는 SQL Server 기능</span><span class="sxs-lookup"><span data-stu-id="6522d-107">Deprecated SQL Server Features in SQL Server 2014</span></span>](../../2014/getting-started/deprecated-sql-server-features-in-sql-server-2014.md)|<span data-ttu-id="6522d-108">이 릴리스에서 더 이상 지원되지 않는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 기능.</span><span class="sxs-lookup"><span data-stu-id="6522d-108">Deprecated [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] features in this release.</span></span> <span data-ttu-id="6522d-109">이 항목에서는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 구성 및 설치 기능을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6522d-109">This topic covers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration, and Setup functionality.</span></span>|  
|[<span data-ttu-id="6522d-110">SQL Server 2014에서 지원되지 않는 SQL Server 기능</span><span class="sxs-lookup"><span data-stu-id="6522d-110">Discontinued SQL Server Features in SQL Server 2014</span></span>](../../2014/getting-started/discontinued-sql-server-features-in-sql-server-2014.md)|<span data-ttu-id="6522d-111">이 릴리스에서 더 이상 지원되지 않는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 기능.</span><span class="sxs-lookup"><span data-stu-id="6522d-111">Discontinued [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] functionality in this release.</span></span> <span data-ttu-id="6522d-112">이 항목에서는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 구성 및 설치 기능을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6522d-112">This topic covers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration, and Setup functionality.</span></span>|  
|[<span data-ttu-id="6522d-113">SQL Server 2014에서 SQL Server 기능의 주요 변경 내용</span><span class="sxs-lookup"><span data-stu-id="6522d-113">Breaking Changes to SQL Server Features in SQL Server 2014</span></span>](../../2014/getting-started/breaking-changes-to-sql-server-features-in-sql-server-2014.md)|<span data-ttu-id="6522d-114">애플리케이션을 변경해야 할 수도 있는 변경 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="6522d-114">Changes that might require changes to applications.</span></span> <span data-ttu-id="6522d-115">이 항목에서는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 구성 및 설치 기능을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6522d-115">This topic covers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration, and Setup functionality.</span></span>|  
|[<span data-ttu-id="6522d-116">SQL Server 2014에서 SQL Server 기능의 동작 변경 내용</span><span class="sxs-lookup"><span data-stu-id="6522d-116">Behavior Changes to SQL Server Features in SQL Server 2014</span></span>](../../2014/getting-started/behavior-changes-to-sql-server-features-in-sql-server-2014.md)|<span data-ttu-id="6522d-117">이 릴리스에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 기능의 동작 변경 내용.</span><span class="sxs-lookup"><span data-stu-id="6522d-117">Behavioral  changes to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] features in this release.</span></span> <span data-ttu-id="6522d-118">이 항목에서는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 구성 및 설치 기능을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6522d-118">This topic covers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration, and Setup functionality.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6522d-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6522d-119">See Also</span></span>  
 [<span data-ttu-id="6522d-120">이전 버전과의 호환성</span><span class="sxs-lookup"><span data-stu-id="6522d-120">Backward Compatibility</span></span>](../../2014/getting-started/backward-compatibility.md)  
  
  
