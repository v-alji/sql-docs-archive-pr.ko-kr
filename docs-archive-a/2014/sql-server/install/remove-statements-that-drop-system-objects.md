---
title: 시스템 개체를 삭제 하는 문을 제거 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- drop system objects [SQL Server]
ms.assetid: cdfc3c50-c801-4039-a4bf-b35f876f1c61
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d9e8fbfd4a436e87cee413d95468ccf5dd36b9dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639250"
---
# <a name="remove-statements-that-drop-system-objects"></a><span data-ttu-id="6ebf2-102">시스템 개체를 삭제하는 문을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="6ebf2-102">Remove statements that drop system objects</span></span>
  <span data-ttu-id="6ebf2-103">업그레이드 관리자가 시스템 개체를 삭제하는 문을 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="6ebf2-103">Upgrade Advisor detected statements that drop system objects.</span></span> <span data-ttu-id="6ebf2-104">확장 저장 프로시저를 비롯한 시스템 개체는 읽기 전용 **리소스** 데이터베이스(mssqlsystemresource)에 배포되므로 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6ebf2-104">System objects, including extended stored procedures, are deployed in the read-only **resource** database (mssqlsystemresource) and cannot be dropped.</span></span> <span data-ttu-id="6ebf2-105">애플리케이션을 수정하여 시스템 개체에 대한 EXECUTE 권한을 취소하거나 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="6ebf2-105">Modify your applications to either revoke or deny EXECUTE permission on system objects.</span></span>  
  
## <a name="component"></a><span data-ttu-id="6ebf2-106">구성 요소</span><span class="sxs-lookup"><span data-stu-id="6ebf2-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="6ebf2-107">Description</span><span class="sxs-lookup"><span data-stu-id="6ebf2-107">Description</span></span>  
 <span data-ttu-id="6ebf2-108">시스템 개체는 읽기 전용 **리소스** 데이터베이스에 배포되므로 DROP TABLE, DROP PROCEDURE 및 **sp_dropextendedproc** 과 같은 문을 사용하여 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6ebf2-108">Statements such as DROP TABLE, DROP PROCEDURE, and **sp_dropextendedproc** cannot be used to remove system objects, because these objects are deployed in the read-only **resource** database.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="6ebf2-109">수정 동작</span><span class="sxs-lookup"><span data-stu-id="6ebf2-109">Corrective Action</span></span>  
 <span data-ttu-id="6ebf2-110">애플리케이션에서 시스템 개체를 삭제하는 문을 모두 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="6ebf2-110">Remove all statements that try to drop system objects from your applications.</span></span> <span data-ttu-id="6ebf2-111">애플리케이션을 수정하여 시스템 개체에 대한 EXECUTE 권한을 취소하거나 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="6ebf2-111">Modify your applications to either revoke or deny EXECUTE permission on system objects.</span></span> <span data-ttu-id="6ebf2-112">또는 SAC(노출 영역 구성) 도구를 사용하여 이러한 개체 중 일부를 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ebf2-112">Alternatively, you can use the Surface Area Configuration (SAC) tool to disable some of these objects.</span></span> <span data-ttu-id="6ebf2-113">예를 들어 SAC 도구를 사용하여 **xp_cmdshell** 확장 저장 프로시저를 활성화하거나 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ebf2-113">For example, the **xp_cmdshell** extended stored procedure can be disabled or enabled using the SAC tool.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ebf2-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6ebf2-114">See Also</span></span>  
 <span data-ttu-id="6ebf2-115">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="6ebf2-115">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="6ebf2-116">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="6ebf2-116">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
