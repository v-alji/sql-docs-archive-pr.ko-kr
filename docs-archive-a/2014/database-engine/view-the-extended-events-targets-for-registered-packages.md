---
title: 등록 된 패키지의 확장 이벤트 대상 보기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- targets [SQL Server extended events]
- viewing event targets
- extended events [SQL Server], viewing targets
ms.assetid: 4985aa5f-ac99-49f6-852c-9d25916549e9
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8e796d141ef943399fc2469c232b34b1956cef3b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661276"
---
# <a name="view-the-extended-events-targets-for-registered-packages"></a><span data-ttu-id="c2134-102">등록된 패키지의 확장 이벤트 대상 보기</span><span class="sxs-lookup"><span data-stu-id="c2134-102">View the Extended Events Targets for Registered Packages</span></span>
  <span data-ttu-id="c2134-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 확장 이벤트 세션을 만들기 전에 사용 가능한 확장 이벤트 대상을 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c2134-103">Before you create a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Extended Events session, it is useful to determine what Extended Events targets are available.</span></span> <span data-ttu-id="c2134-104">이 태스크를 수행하려면 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 에서 쿼리 편집기를 사용하여 다음 절차를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2134-104">This task involves using Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to perform the following procedure.</span></span>  
  
 <span data-ttu-id="c2134-105">이 프로시저의 문이 끝나면 쿼리 편집기의 **결과** 탭에 다음 두 개의 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2134-105">After the statements in this procedure finish, the **Results** tab of Query Editor displays the following two columns:</span></span>  
  
-   <span data-ttu-id="c2134-106">package_name</span><span class="sxs-lookup"><span data-stu-id="c2134-106">package_name</span></span>  
  
-   <span data-ttu-id="c2134-107">target_name</span><span class="sxs-lookup"><span data-stu-id="c2134-107">target_name</span></span>  
  
## <a name="to-view-the-extended-events-targets-for-registered-packages-using-query-editor"></a><span data-ttu-id="c2134-108">쿼리 편집기를 사용하여 등록된 패키지에 대한 확장 이벤트 대상을 보려면</span><span class="sxs-lookup"><span data-stu-id="c2134-108">To view the Extended Events targets for registered packages using Query Editor</span></span>  
  
-   <span data-ttu-id="c2134-109">쿼리 편집기에서 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c2134-109">In Query Editor, issue the following statements.</span></span>  
  
    ```  
    USE msdb  
    SELECT p.name package_name, o.name target_name  
    FROM sys.dm_xe_objects o  
    JOIN sys.dm_xe_packages p  
         ON o.package_guid = p.guid  
    WHERE o.object_type = 'target'  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c2134-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c2134-110">See Also</span></span>  
 <span data-ttu-id="c2134-111">[SQL Server 확장 이벤트 대상](../../2014/database-engine/sql-server-extended-events-targets.md) </span><span class="sxs-lookup"><span data-stu-id="c2134-111">[SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) </span></span>  
 <span data-ttu-id="c2134-112">[sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c2134-112">[sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql) </span></span>  
 [<span data-ttu-id="c2134-113">sys.dm_xe_packages&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c2134-113">sys.dm_xe_packages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
