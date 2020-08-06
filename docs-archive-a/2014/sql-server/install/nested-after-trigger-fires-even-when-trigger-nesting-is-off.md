---
title: 트리거 중첩이 OFF 일 때도 중첩 AFTER 트리거가 발생 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- DML triggers, nested
- nested triggers option
- triggers [SQL Server], nested
ms.assetid: 94d72960-676e-40d9-81bc-08bffe778110
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f91c04e8d69880b451c1479e2907cd1910e8f9c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742816"
---
# <a name="nested-after-trigger-fires-even-when-trigger-nesting-is-off"></a><span data-ttu-id="fd585-102">트리거 중첩이 OFF일 때도 중첩 AFTER 트리거가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="fd585-102">Nested AFTER trigger fires even when trigger nesting is OFF</span></span>
  <span data-ttu-id="fd585-103">업그레이드 관리자가 하나 이상의 테이블에 정의되어 있는 INSTEAD OF 트리거 내부에서 중첩 AFTER 트리거를 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="fd585-103">Upgrade Advisor detected an AFTER trigger nested inside an INSTEAD OF trigger that is defined on one or more tables.</span></span> <span data-ttu-id="fd585-104">`nested triggers` 서버 구성 옵션이 0으로 설정되어 있는 경우에도 중첩된 AFTER 트리거가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd585-104">Nested AFTER triggers may fire even when the `nested triggers` server configuration option is set to 0.</span></span>  
  
## <a name="component"></a><span data-ttu-id="fd585-105">구성 요소</span><span class="sxs-lookup"><span data-stu-id="fd585-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="fd585-106">설명</span><span class="sxs-lookup"><span data-stu-id="fd585-106">Description</span></span>  
 <span data-ttu-id="fd585-107">INSTEAD OF 트리거 내부에 중첩된 첫 번째 AFTER 트리거는 `nested triggers` 서버 구성 옵션이 0으로 설정되어 있는 경우에도 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd585-107">The first AFTER trigger nested inside an INSTEAD OF trigger fires even if the `nested triggers` server configuration option is set to 0.</span></span> <span data-ttu-id="fd585-108">그러나 이 설정에서는 이후의 AFTER 트리거는 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fd585-108">However, under this setting, subsequent AFTER triggers do not fire.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="fd585-109">수정 동작</span><span class="sxs-lookup"><span data-stu-id="fd585-109">Corrective Action</span></span>  
 <span data-ttu-id="fd585-110">중첩 트리거에 대한 애플리케이션을 검토하여 `nested triggers` 서버 구성 옵션이 0으로 설정된 경우 이 새 동작과 관련된 비즈니스 규칙을 애플리케이션이 여전히 준수하는지 확인한 다음 적절하게 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="fd585-110">Review your applications for nested triggers to determine whether the applications still comply with your business rules with regard to this new behavior when the `nested triggers` server configuration option is set to 0, and then make appropriate modifications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd585-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fd585-111">See Also</span></span>  
 <span data-ttu-id="fd585-112">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="fd585-112">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="fd585-113">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="fd585-113">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
