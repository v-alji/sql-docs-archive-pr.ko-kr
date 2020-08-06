---
title: Sysperfinfo에서 bigint 값을 필요로 하도록 응용 프로그램을 수정 합니다. cntr_value | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sysperfinfo
- bigint values [SQL Server]
ms.assetid: b0345303-6e9a-4078-8148-6e1bce207b8c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 108a9b981debc95e182b16847c39a03d4b242088
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740696"
---
# <a name="modify-applications-to-expect-bigint-values-from-sysperfinfocntr_value"></a><span data-ttu-id="d1c24-102">sysperfinfo.cntr_value에서 bigint 값을 예상할 수 있도록 애플리케이션을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="d1c24-102">Modify applications to expect bigint values from sysperfinfo.cntr_value</span></span>
  <span data-ttu-id="d1c24-103">sysperfinfo `bigint` cntr_value 열에 대 한 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1c24-103">sysperfinfo returns a `bigint` value for the cntr_value column.</span></span>  
  
## <a name="component"></a><span data-ttu-id="d1c24-104">구성 요소</span><span class="sxs-lookup"><span data-stu-id="d1c24-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="d1c24-105">수정 동작</span><span class="sxs-lookup"><span data-stu-id="d1c24-105">Corrective Action</span></span>  
 <span data-ttu-id="d1c24-106">cntr_value 열의 `bigint` 값을 처리할 수 있도록 sysperfinfo를 사용하는 애플리케이션을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="d1c24-106">Modify applications that use sysperfinfo to ensure that they can handle the `bigint` values of the cntr_value column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d1c24-107">sysperfinfo는 호환성 뷰입니다.</span><span class="sxs-lookup"><span data-stu-id="d1c24-107">sysperfinfo is a compatibility view.</span></span> <span data-ttu-id="d1c24-108">sys.dm_os_performance_counter 동적 관리 뷰를 대신 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1c24-108">You should use the sys.dm_os_performance_counter dynamic management view instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1c24-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d1c24-109">See Also</span></span>  
 <span data-ttu-id="d1c24-110">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="d1c24-110">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="d1c24-111">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="d1c24-111">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
