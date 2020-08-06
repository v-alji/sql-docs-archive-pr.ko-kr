---
title: 시스템 개체에 대 한 열 수준 사용 권한을 수정 하는 문을 제거 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- column-level permissions [SQL Server]
- removed statement permissions [SQL Server]
ms.assetid: 7f4fbbef-2696-4911-903b-63f6d9e4484a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e55af3dca0c55c2babd09bc6cfc48ed0ddf3ad7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653147"
---
# <a name="remove-statements-that-modify-column-level-permissions-on-system-objects"></a><span data-ttu-id="36232-102">시스템 개체에 대한 열 수준 사용 권한을 수정하는 문을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="36232-102">Remove statements that modify column-level permissions on system objects</span></span>
  <span data-ttu-id="36232-103">업그레이드 관리자가 시스템 개체에 대한 비표준 열 수준 사용 권한을 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="36232-103">The Upgrade Advisor detected nonstandard column-level permissions on system objects.</span></span> <span data-ttu-id="36232-104">이러한 권한 변경 내용은 업그레이드 시 유지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="36232-104">These permission changes will not be maintained when you upgrade.</span></span> <span data-ttu-id="36232-105">또한 시스템 개체에 대한 열 수준 사용 권한은 더 이상 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="36232-105">Additionally, column-level permissions on system objects are no longer supported.</span></span> <span data-ttu-id="36232-106">애플리케이션에서 시스템 개체에 대한 열 수준 사용 권한을 설정하는 문을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="36232-106">Remove statements from your applications that set column-level permissions on system objects.</span></span>  
  
## <a name="component"></a><span data-ttu-id="36232-107">구성 요소</span><span class="sxs-lookup"><span data-stu-id="36232-107">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="36232-108">수정 동작</span><span class="sxs-lookup"><span data-stu-id="36232-108">Corrective Action</span></span>  
 <span data-ttu-id="36232-109">애플리케이션에서 시스템 개체에 대한 열 수준 사용 권한을 부여, 거부 또는 취소하는 문을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="36232-109">Remove statements from your application that grant, deny, or revoke column-level permissions on system objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36232-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="36232-110">See Also</span></span>  
 <span data-ttu-id="36232-111">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="36232-111">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="36232-112">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="36232-112">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
