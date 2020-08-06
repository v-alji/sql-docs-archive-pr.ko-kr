---
title: 호환성 모드 90 이상에서는 CREATE STATISTICS 문에 WITH ROWS를 사용할 수 없습니다. Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- WITH ROWS in CREATE STATISTICS statement
ms.assetid: 197b2ecf-a1a3-4a3a-a523-a0ee919c1dde
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d28a05e7cd025e213e2cebdce9d582a9df446fea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650380"
---
# <a name="with-rows-is-not-supported-in-create-statistics-statements-in-the-compatibility-mode-of-90-or-later"></a><span data-ttu-id="0313e-102">호환성 모드 90 이상에서는 CREATE STATISTICS 문에 WITH ROWS를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0313e-102">WITH ROWS is not supported in CREATE STATISTICS statements in the compatibility mode of 90 or later</span></span>
  <span data-ttu-id="0313e-103">호환성 모드가 90 이상으로 설정된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 실행할 때 CREATE STATISTICS 문에 WITH ROWS를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0313e-103">Specifying WITH ROWS in CREATE STATISTICS statements is not supported when you run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] set to the compatibility mode of 90 or later.</span></span>  
  
## <a name="component"></a><span data-ttu-id="0313e-104">구성 요소</span><span class="sxs-lookup"><span data-stu-id="0313e-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="0313e-105">수정 동작</span><span class="sxs-lookup"><span data-stu-id="0313e-105">Corrective Action</span></span>  
 <span data-ttu-id="0313e-106">WITH SAMPLE *number* ROWS를 지정하거나 문서화된 구문에 따라 다른 옵션을 지정하여 WITH ROWS가 포함된 CREATE STATISTICS 문을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="0313e-106">Modify CREATE STATISTICS statements that include WITH ROWS by specifying WITH SAMPLE *number* ROWS, or by specifying other options that comply with the documented syntax.</span></span> <span data-ttu-id="0313e-107">자세한 내용은 SQL Server 온라인 설명서에서 "CREATE STATISTICS(Transact-SQL)" 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0313e-107">For more information, see the topic "CREATE STATISTICS (Transact-SQL) in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0313e-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0313e-108">See Also</span></span>  
 <span data-ttu-id="0313e-109">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="0313e-109">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="0313e-110">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="0313e-110">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
