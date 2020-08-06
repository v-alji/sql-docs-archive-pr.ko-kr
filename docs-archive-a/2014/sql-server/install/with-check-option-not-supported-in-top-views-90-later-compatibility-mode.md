---
title: 90 이상 호환성 모드의 TOP이 포함 된 뷰에서는 WITH CHECK OPTION이 지원 되지 않습니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- TOP clause
- WITH CHECK OPTION clause
ms.assetid: 1b9581d0-bad9-43e0-b8fc-f32d8a8a04ca
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ee7775c875e33f104341a1da39f5fe6c9326f284
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650381"
---
# <a name="with-check-option-is-not-supported-in-views-that-contain-top-in-90-or-later-compatibility-modes"></a><span data-ttu-id="b8be9-102">호환성 모드 90 이상의 TOP이 포함된 뷰에서는 WITH CHECK OPTION이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b8be9-102">WITH CHECK OPTION is not supported in views that contain TOP in 90 or later compatibility modes</span></span>
  <span data-ttu-id="b8be9-103">업그레이드 관리자가 뷰의 SELECT 문이나 참조된 뷰에서 WITH CHECK OPTION 및 TOP 절을 사용하는 뷰를 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="b8be9-103">Upgrade Advisor detected a view that uses the WITH CHECK OPTION and a TOP clause in the SELECT statement of the view or in a referenced view.</span></span> <span data-ttu-id="b8be9-104">데이터베이스 호환성 모드를 80 이하 모드로 설정한 상태에서 뷰를 이러한 방식으로 정의하면 해당 뷰를 통해 데이터가 잘못 수정될 수 있으며 부정확한 결과가 나올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8be9-104">Views defined this way incorrectly allow data to be modified through the view and may produce inaccurate results when the database compatibility mode is set to 80 and earlier.</span></span> <span data-ttu-id="b8be9-105">뷰 또는 참조된 뷰가 TOP 절을 사용하고 데이터베이스 호환성 모드가 90 이상으로 설정된 경우에는 뷰를 통해 데이터를 삽입하거나 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b8be9-105">Data cannot be inserted or updated through a view that uses WITH CHECK OPTION when the view or a referenced view uses the TOP clause and the database compatibility mode is set to 90 or later.</span></span>  
  
## <a name="component"></a><span data-ttu-id="b8be9-106">구성 요소</span><span class="sxs-lookup"><span data-stu-id="b8be9-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="b8be9-107">수정 동작</span><span class="sxs-lookup"><span data-stu-id="b8be9-107">Corrective Action</span></span>  
 <span data-ttu-id="b8be9-108">업그레이드할 때 사용자 데이터베이스는 호환성 모드를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="b8be9-108">When you upgrade, user databases maintain their compatibility mode.</span></span> <span data-ttu-id="b8be9-109">뷰를 통해 데이터를 수정해야 하는 경우 데이터베이스 호환성 모드를 100 이상으로 변경하기 전에 WITH CHECK OPTION과 TOP를 둘 다 사용하는 뷰를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8be9-109">Before you change the database compatibility mode to 100 or later, modify views that use both WITH CHECK OPTION and TOP if data modification through the view is required.</span></span> <span data-ttu-id="b8be9-110">자세한 내용은 [sp_dbcmptlevel &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-dbcmptlevel-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b8be9-110">For more information, see [sp_dbcmptlevel &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbcmptlevel-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8be9-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b8be9-111">See Also</span></span>  
 <span data-ttu-id="b8be9-112">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="b8be9-112">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="b8be9-113">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="b8be9-113">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
