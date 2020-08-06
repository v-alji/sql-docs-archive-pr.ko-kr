---
title: 업그레이드 후 계획 지침의 유효성 검사 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- plan guides [SQL Server], validating after upgrade
ms.assetid: a55ebd88-6f58-454d-b1c4-991b88add522
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 18cc0f93ddec46025f659bcb9489bfff3ca846ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732583"
---
# <a name="validate-plan-guides-after-upgrade"></a><span data-ttu-id="2a9f7-102">업그레이드 후 계획 지침의 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="2a9f7-102">Validate Plan Guides After Upgrade</span></span>
  <span data-ttu-id="2a9f7-103">새로운 릴리스의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 애플리케이션을 업그레이드할 때는 계획 지침 정의를 다시 평가하고 테스트하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2a9f7-103">We recommend re-evaluating and testing plan guide definitions when you upgrade your application to a new release of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2a9f7-104">성능 조정 요구 사항과 계획 지침 일치 동작은 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a9f7-104">Performance tuning requirements and plan guide matching behavior may change.</span></span> <span data-ttu-id="2a9f7-105">잘못된 계획 지침으로 인해 쿼리가 실패하지는 않지만 이 경우 계획 지침을 사용하지 않은 채 계획이 컴파일되므로 최상의 선택이 아닐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a9f7-105">Although an invalid plan guide will not cause a query to fail, the plan is compiled without using the plan guide and may not be the best choice.</span></span> <span data-ttu-id="2a9f7-106">데이터베이스를 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드한 후에는 다음 태스크를 수행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2a9f7-106">After upgrading a database to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], we recommend that you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="2a9f7-107">[sys.fn_validate_plan_guide](/sql/relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql) 함수를 사용하여 기존 계획 지침의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9f7-107">Validate existing plan guides by using the [sys.fn_validate_plan_guide](/sql/relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql) function.</span></span>  
  
-   <span data-ttu-id="2a9f7-108">확장 이벤트에서 [Plan Guide Unsuccessful](../event-classes/plan-guide-unsuccessful-event-class.md) 이벤트를 사용하여 일정 기간 동안 잘못된 계획 지침이 있는지 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9f7-108">Use extended events to monitor for misguided plans for some period of time by using the [Plan Guide Unsuccessful](../event-classes/plan-guide-unsuccessful-event-class.md) event.</span></span>  
  
  
