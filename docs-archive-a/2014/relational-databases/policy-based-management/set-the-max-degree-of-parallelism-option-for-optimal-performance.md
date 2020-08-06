---
title: 최적 성능을 위해 최대 병렬 처리 수준 옵션 설정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: ec908006-67ae-4674-9a61-25ea741d6197
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3043a656cbe1ac1ec40f0d0a67b6eac057005af4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740848"
---
# <a name="set-the-max-degree-of-parallelism-option-for-optimal-performance"></a><span data-ttu-id="dabff-102">최적 성능을 위해 최대 병렬 처리 수준 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="dabff-102">Set the Max Degree of Parallelism Option for Optimal Performance</span></span>
  <span data-ttu-id="dabff-103">이 규칙은 8보다 큰 값에 대한 MAXDOP(max degree of parallelism) 옵션을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="dabff-103">This rule determines whether the max degree of parallelism (MAXDOP) option for a value greater than 8.</span></span> <span data-ttu-id="dabff-104">이 옵션을 큰 값으로 설정하면 불필요하게 리소스가 소비되고 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dabff-104">Setting this option to a larger value often causes unwanted resource consumption and performance degradation.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="dabff-105">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="dabff-105">Best Practices Recommendations</span></span>  
 <span data-ttu-id="dabff-106">sp_configure를 사용하여 최대 병렬 처리 수준 옵션을 8 이하로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dabff-106">Set the max degree of parallelism option to 8 or less by using sp_configure.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="dabff-107">참조 항목</span><span class="sxs-lookup"><span data-stu-id="dabff-107">For More Information</span></span>  
 [<span data-ttu-id="dabff-108">Microsoft 기술 자료 문서 329204</span><span class="sxs-lookup"><span data-stu-id="dabff-108">Microsoft Knowledge Base article 329204</span></span>](https://go.microsoft.com/fwlink/?linkid=117786)  
  
 [<span data-ttu-id="dabff-109">max degree of parallelism 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="dabff-109">Configure the max degree of parallelism Server Configuration Option</span></span>](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)  
  
 [<span data-ttu-id="dabff-110">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dabff-110">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
