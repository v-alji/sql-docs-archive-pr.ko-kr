---
title: 90 이상 호환성 모드의 뷰에서는 FOR BROWSE를 사용할 수 없습니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], FOR BROWSE clause
- FOR BROWSE clause
ms.assetid: 8f49b1c1-d877-4c46-b988-f8cdd8ac0925
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 251e0ae2ff6f19dfcff3b0f8056f6697c1bfc40d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653172"
---
# <a name="for-browse-is-not-allowed-in-views-in-90-or-later-compatibility-modes"></a><span data-ttu-id="29d61-102">FOR BROWSE는 90 이상 호환성 모드의 뷰에서 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="29d61-102">FOR BROWSE is not allowed in views in 90 or later compatibility modes</span></span>
  <span data-ttu-id="29d61-103">업그레이드 관리자가 뷰에서 FOR BROWSE 절이 사용되는 것을 감지했습니다.</span><span class="sxs-lookup"><span data-stu-id="29d61-103">Upgrade Advisor detected the use of the FOR BROWSE clause in a view.</span></span> <span data-ttu-id="29d61-104">데이터베이스 호환성 모드가 80으로 설정되어 있는 경우 FOR BROWSE 절은 뷰에서 허용 및 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="29d61-104">The FOR BROWSE clause is allowed (and ignored) in views when the database compatibility mode is set to 80.</span></span> <span data-ttu-id="29d61-105">데이터베이스 호환성 모드가 90 이상으로 설정된 경우에는 뷰에 FOR BROWSE 절이 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="29d61-105">The FOR BROWSE clause is not allowed in views when the database compatibility mode is set to 90 or later.</span></span>  
  
## <a name="component"></a><span data-ttu-id="29d61-106">구성 요소</span><span class="sxs-lookup"><span data-stu-id="29d61-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="29d61-107">수정 동작</span><span class="sxs-lookup"><span data-stu-id="29d61-107">Corrective Action</span></span>  
 <span data-ttu-id="29d61-108">업그레이드할 때 사용자 데이터베이스는 호환성 모드를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="29d61-108">When you upgrade, user databases maintain their compatibility mode.</span></span> <span data-ttu-id="29d61-109">데이터베이스 호환성 모드를 90 이상으로 변경하기 전에 뷰 정의에서 FOR BROWSE 절을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="29d61-109">Before you change the database compatibility mode to 90 or later, remove the FOR BROWSE clause from view definitions.</span></span> <span data-ttu-id="29d61-110">자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 "sp_dbcmptlevel"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="29d61-110">For more information, see "sp_dbcmptlevel" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29d61-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="29d61-111">See Also</span></span>  
 <span data-ttu-id="29d61-112">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="29d61-112">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="29d61-113">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="29d61-113">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
