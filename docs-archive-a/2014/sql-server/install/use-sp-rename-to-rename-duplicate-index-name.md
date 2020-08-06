---
title: Sp_rename를 사용 하 여 중복 인덱스 이름 바꾸기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- table names [SQL Server]
- duplicate table names
- index names [SQL Server]
- sp_rename
- duplicate index names
ms.assetid: ee66c7a5-eb6d-4fcf-970c-ab099d78c8d9
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b8ffe3b9befd0c7239d32094e5738e0fb2947c5a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742763"
---
# <a name="use-sp_rename-to-rename-duplicate-index-name"></a><span data-ttu-id="f7391-102">sp_rename을 사용하여 중복 인덱스 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="f7391-102">Use sp_rename to rename duplicate index name</span></span>
  <span data-ttu-id="f7391-103">업그레이드 관리자가 중복된 테이블 또는 뷰 인덱스 이름을 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="f7391-103">Upgrade Advisor has detected duplicate table or view index names.</span></span> <span data-ttu-id="f7391-104">업그레이드하기 전에 인덱스 이름을 바꾸어 중복을 제거하십시오.</span><span class="sxs-lookup"><span data-stu-id="f7391-104">Rename the indexes to remove duplicates before upgrading.</span></span>  
  
## <a name="component"></a><span data-ttu-id="f7391-105">구성 요소</span><span class="sxs-lookup"><span data-stu-id="f7391-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="f7391-106">수정 동작</span><span class="sxs-lookup"><span data-stu-id="f7391-106">Corrective Action</span></span>  
  
1.  <span data-ttu-id="f7391-107">다음 쿼리를 실행하여 중복 인덱스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f7391-107">Locate the duplicate indexes by executing the following query.</span></span>  
  
    ```  
    SELECT DISTINCT OBJECT_NAME(o.id), name  
    FROM sysindexes as o  
    WHERE EXISTS   
        (SELECT name FROM sysindexes  as i  
          WHERE i.id = o.id  
          AND i.name = o.name and i.indid < o.indid);  
    ```  
  
2.  <span data-ttu-id="f7391-108">**sp_rename** 을 사용하여 인덱스 이름 중 하나를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f7391-108">Use **sp_rename** to change one of the index names.</span></span> <span data-ttu-id="f7391-109">인덱스 이름이 같기 때문에 이름이 변경될 인덱스를 결정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f7391-109">Because the index names are the same, you cannot determine which index will be renamed.</span></span> <span data-ttu-id="f7391-110">이 단계로 인덱스를 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7391-110">This step allows you to differentiate the indexes.</span></span>  
  
    ```  
    EXEC sp_rename N'table_name.index_name', N'new_index_name', N'INDEX'  
    ```  
  
3.  <span data-ttu-id="f7391-111">다음 쿼리를 실행하여 인덱스 이름이 변경되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f7391-111">Verify which index was renamed by executing the following query.</span></span> <span data-ttu-id="f7391-112">이 쿼리는 지정한 테이블이나 뷰의 모든 인덱스(키 열 이름 포함)를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f7391-112">This query returns all indexes (including key column names) on the specified table or view.</span></span>  
  
    ```  
    SELECT i.name AS IndexName, c.name AS ColumnName, ik.colid, ik.keyno  
    FROM sysindexes i  
    JOIN sysindexkeys ik ON i.id = ik.id and i.indid = ik.indid   
    JOIN syscolumns c ON c.id = ik.id and ik.colid = c.colid  
    WHERE i.id = OBJECT_ID('table_or_view_name')  
    ```  
  
4.  <span data-ttu-id="f7391-113">필요한 경우 **sp_rename** 을 다시 사용하여 인덱스 이름을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7391-113">If necessary, use **sp_rename** again to correct the index names.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7391-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f7391-114">See Also</span></span>  
 <span data-ttu-id="f7391-115">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="f7391-115">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="f7391-116">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="f7391-116">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
