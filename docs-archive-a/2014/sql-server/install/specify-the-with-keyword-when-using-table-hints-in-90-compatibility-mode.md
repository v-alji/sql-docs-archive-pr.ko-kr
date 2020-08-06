---
title: 90 호환성 모드에서 테이블 힌트를 사용할 경우 WITH 키워드를 지정 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- WITH keyword
- table hints [SQL Server]
ms.assetid: 7636cc85-5155-44db-baf6-df807761adb8
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0ecd13475395cef4257d97eb7480f32420932e22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650444"
---
# <a name="specify-the-with-keyword-when-using-table-hints-in-90-compatibility-mode"></a><span data-ttu-id="3c96b-102">호환성 모드 90에서 테이블 힌트를 사용할 경우 WITH 키워드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c96b-102">Specify the WITH keyword when using table hints in 90 compatibility mode</span></span>
  <span data-ttu-id="3c96b-103">일부 예외는 있으나 WITH 키워드를 사용하여 테이블 힌트를 지정한 경우에만 쿼리의 FROM 절에서 테이블 힌트가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c96b-103">With some exceptions, table hints are supported in the FROM clause of a query only when the hints are specified by using the WITH keyword.</span></span> <span data-ttu-id="3c96b-104">자세한 내용은[!INCLUDE[tsql](../../includes/tsql-md.md)]온라인 설명서에서 "FROM([!INCLUDE[tsql](../../includes/tsql-md.md)])" 및 "테이블 힌트( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] )"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3c96b-104">For more information, see the topics "FROM ([!INCLUDE[tsql](../../includes/tsql-md.md)])" and "Table Hint ([!INCLUDE[tsql](../../includes/tsql-md.md)])" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="component"></a><span data-ttu-id="3c96b-105">구성 요소</span><span class="sxs-lookup"><span data-stu-id="3c96b-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="3c96b-106">수정 동작</span><span class="sxs-lookup"><span data-stu-id="3c96b-106">Corrective Action</span></span>  
 <span data-ttu-id="3c96b-107">테이블 힌트 앞에 WITH 키워드를 포함하여 FROM 절에서 테이블 힌트가 들어 있는 쿼리를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c96b-107">Modify queries that include table hints in the FROM clause by including the WITH keyword before the table hints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c96b-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3c96b-108">See Also</span></span>  
 <span data-ttu-id="3c96b-109">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="3c96b-109">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="3c96b-110">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="3c96b-110">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
