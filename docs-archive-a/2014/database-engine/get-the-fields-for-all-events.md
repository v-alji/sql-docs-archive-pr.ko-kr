---
title: 모든 이벤트에 대 한 필드 가져오기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], getting fields
- xe
ms.assetid: 4e4ee03f-5bca-42ed-a37c-db1c82e3aad2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 01d98e827121a0c47111dd601c6e1772f796849d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732927"
---
# <a name="get-the-fields-for-all-events"></a><span data-ttu-id="dc05a-102">모든 이벤트에 대한 필드 가져오기</span><span class="sxs-lookup"><span data-stu-id="dc05a-102">Get the Fields for All Events</span></span>
  <span data-ttu-id="dc05a-103">이 태스크를 수행하려면 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 쿼리 편집기를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dc05a-103">Accomplishing this task involves using Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="dc05a-104">이 프로시저의 문이 끝나면 쿼리 편집기의 **결과** 탭에 다음 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc05a-104">After the statements in this procedure finish, the **Results** tab of Query Editor displays the following columns:</span></span>  
  
-   <span data-ttu-id="dc05a-105">package_name</span><span class="sxs-lookup"><span data-stu-id="dc05a-105">package_name</span></span>  
  
-   <span data-ttu-id="dc05a-106">event_name</span><span class="sxs-lookup"><span data-stu-id="dc05a-106">event_name</span></span>  
  
-   <span data-ttu-id="dc05a-107">event_field</span><span class="sxs-lookup"><span data-stu-id="dc05a-107">event_field</span></span>  
  
-   <span data-ttu-id="dc05a-108">field_type</span><span class="sxs-lookup"><span data-stu-id="dc05a-108">field_type</span></span>  
  
-   <span data-ttu-id="dc05a-109">column_type</span><span class="sxs-lookup"><span data-stu-id="dc05a-109">column_type</span></span>  
  
 <span data-ttu-id="dc05a-110">위의 정보는 버킷팅 대상을 사용하는 이벤트 세션을 구성하는 경우 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc05a-110">You can use the preceding information when configuring event sessions that use the bucketing target.</span></span> <span data-ttu-id="dc05a-111">자세한 내용은 [SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc05a-111">For more information, see [SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md).</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="dc05a-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="dc05a-112">Before you Begin</span></span>  
 <span data-ttu-id="dc05a-113">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 확장 이벤트 세션을 만들기 전에 이벤트와 연관된 필드에 대한 정보를 얻는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dc05a-113">Before you create a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Extended Events session, it is useful to get information about the fields associated with events.</span></span>  
  
## <a name="to-get-the-fields-for-all-events-using-query-editor"></a><span data-ttu-id="dc05a-114">쿼리 편집기를 사용하여 모든 이벤트에 대한 필드를 가져오려면</span><span class="sxs-lookup"><span data-stu-id="dc05a-114">To get the fields for all events using Query Editor</span></span>  
  
-   <span data-ttu-id="dc05a-115">쿼리 편집기에서 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="dc05a-115">In Query Editor, issue the following statements.</span></span>  
  
    ```  
    select p.name package_name, o.name event_name, c.name event_field, c.type_name field_type, c.column_type column_type  
    from sys.dm_xe_objects o  
    join sys.dm_xe_packages p  
          on o.package_guid = p.guid  
    join sys.dm_xe_object_columns c  
          on o.name = c.object_name  
    where o.object_type = 'event'  
    order by package_name, event_name  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="dc05a-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dc05a-116">See Also</span></span>  
 <span data-ttu-id="dc05a-117">[sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dc05a-117">[sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql) </span></span>  
 [<span data-ttu-id="dc05a-118">sys.dm_xe_packages&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dc05a-118">sys.dm_xe_packages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
