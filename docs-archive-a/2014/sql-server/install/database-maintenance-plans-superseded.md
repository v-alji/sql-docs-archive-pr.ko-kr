---
title: 데이터베이스 유지 관리 계획 대체 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- suspended database maintenance plans
- database maintenance plans [SQL Server Agent]
- maintenance plans [SQL Server Agent]
ms.assetid: efac127c-6c81-4c7a-a6c4-9aae5d15545d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3aea75cc4ecc94ccbaeb1f35cecd0b18ff3a65ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639252"
---
# <a name="database-maintenance-plans-superseded"></a><span data-ttu-id="69698-102">데이터베이스 유지 관리 계획이 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="69698-102">Database maintenance plans superseded</span></span>
    
## <a name="component"></a><span data-ttu-id="69698-103">구성 요소</span><span class="sxs-lookup"><span data-stu-id="69698-103">Component</span></span>  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="69698-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에이전트</span><span class="sxs-lookup"><span data-stu-id="69698-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent</span></span>  
  
## <a name="description"></a><span data-ttu-id="69698-105">Description</span><span class="sxs-lookup"><span data-stu-id="69698-105">Description</span></span>  
 <span data-ttu-id="69698-106">기존 데이터베이스 유지 관리 계획이 업그레이드되고 계속 작동하지만</span><span class="sxs-lookup"><span data-stu-id="69698-106">Existing database maintenance plans are upgraded and continue to work.</span></span> <span data-ttu-id="69698-107">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 새 데이터베이스 유지 관리 계획을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="69698-107">However, you will not be able to create new database maintenance plans by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="69698-108">개체 탐색기에서 유지 관리 계획을 보려면 관리, 레거시를 차례로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="69698-108">To view the maintenance plans in Object Explorer, expand Management, and then expand Legacy.</span></span> <span data-ttu-id="69698-109">데이터베이스 유지 관리 계획에 대 한 상황에 맞는 메뉴에서 **마이그레이션** 을 선택 하 여 기존 데이터베이스 유지 관리 계획을 새 형식으로 마이그레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69698-109">You can migrate existing database maintenance plans to the new format by selecting **Migrate** from the context menu for any database maintenance plan.</span></span> <span data-ttu-id="69698-110">새 유지 관리 계획 기능은 데이터베이스 유지 관리 계획을 완전히 대체하지는 않으므로 마이그레이션 후에 일부 기능이 손실될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69698-110">Because the new maintenance plan feature is not a direct replacement of database maintenance plans, some functionality might be lost after migration.</span></span> <span data-ttu-id="69698-111">데이터베이스 유지 관리 계획을 마이그레이션해도 이전 계획은 삭제되지 않으므로 이전 계획을 제거하기 전에 해당 기능을 유지 관리 계획으로 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69698-111">Migrating a database maintenance plan does not delete the old plan, so you can test its functionality as a maintenance plan before removing the old plan.</span></span>  
  
 <span data-ttu-id="69698-112">다음 기능은 데이터베이스 유지 관리 계획에서 더 이상 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="69698-112">The following features are no longer supported within database maintenance plans:</span></span>  
  
-   <span data-ttu-id="69698-113">로그 전달</span><span class="sxs-lookup"><span data-stu-id="69698-113">Log shipping</span></span>  
  
-   <span data-ttu-id="69698-114">**데이터베이스 무결성 검사** 태스크의 **사소한 문제를 복구 하려고** 합니다. 옵션</span><span class="sxs-lookup"><span data-stu-id="69698-114">The **Attempt to repair any minor problems** option of the **Database Integrity Check** task</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="69698-115">수정 동작</span><span class="sxs-lookup"><span data-stu-id="69698-115">Corrective Action</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="69698-116">에서 로그 전달이 데이터베이스 유지 관리 계획에 포함되지 않도록 방지됩니다.</span><span class="sxs-lookup"><span data-stu-id="69698-116">prevents log shipping from being included in a database maintenance plan.</span></span> <span data-ttu-id="69698-117">자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 "로그 전달"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="69698-117">For more information, see "Log Shipping" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
  
