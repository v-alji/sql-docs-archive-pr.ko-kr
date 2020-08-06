---
title: 인덱싱된 뷰 정의의 테이블 힌트는 80 호환성 모드에서 무시 되며 90 모드 이상에서 허용 되지 않습니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- query hints [SQL Server]
- indexed views [SQL Server], query hints
ms.assetid: 405dfcff-a3a6-4e6d-a53a-ed77bbacdd13
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cf3cb2b06dc477d93c8fd42312b4835ded42afb4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735843"
---
# <a name="table-hints-in-indexed-view-definitions-are-ignored-in-80-compatibility-mode-and-are-not-allowed-in-90-mode-or-later"></a><span data-ttu-id="cd1f8-102">인덱싱된 뷰 정의의 테이블 힌트는 호환성 모드 80에서는 무시되고 호환성 모드 90 이상에서는 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1f8-102">Table hints in indexed view definitions are ignored in 80 compatibility mode and are not allowed in 90 mode or later</span></span>
  <span data-ttu-id="cd1f8-103">인덱싱된 뷰 정의에서 테이블 힌트는 호환성 모드 90 이상에서 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1f8-103">Table hints in the definitions of indexed views are not permitted in the compatibility mode of 90 or later.</span></span> <span data-ttu-id="cd1f8-104">자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서의 "인덱싱된 뷰 디자인", "인덱싱된 뷰 만들기" 및 "쿼리 힌트 ()" 항목을 참조 하십시오 [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="cd1f8-104">For more information, see the following topics in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online: "Designing Indexed Views," "Creating Indexed Views," and "Query Hint ([!INCLUDE[tsql](../../includes/tsql-md.md)])."</span></span>  
  
## <a name="component"></a><span data-ttu-id="cd1f8-105">구성 요소</span><span class="sxs-lookup"><span data-stu-id="cd1f8-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="cd1f8-106">수정 동작</span><span class="sxs-lookup"><span data-stu-id="cd1f8-106">Corrective Action</span></span>  
 <span data-ttu-id="cd1f8-107">인덱싱된 뷰 정의에서 테이블 힌트를 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1f8-107">Table hints must be removed from the definitions of indexed views.</span></span> <span data-ttu-id="cd1f8-108">사용하는 호환성 모드에 관계없이 애플리케이션을 테스트하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1f8-108">Regardless of which compatibility mode is used, we recommend that you test the application.</span></span> <span data-ttu-id="cd1f8-109">애플리케이션을 테스트하면 인덱싱된 뷰가 쿼리와 일치될 때를 비롯하여 인덱싱된 뷰가 작성, 업데이트 및 액세스될 때 애플리케이션이 예상대로 실행되는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1f8-109">By testing the application, you can make sure it performs as expected when indexed views are created, updated, and accessed, including when indexed views are matched to queries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd1f8-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cd1f8-110">See Also</span></span>  
 <span data-ttu-id="cd1f8-111">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="cd1f8-111">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="cd1f8-112">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="cd1f8-112">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
