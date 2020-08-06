---
title: Master 및 model 데이터베이스와 일치 하도록 사용자 정의 데이터베이스의 데이터 정렬을 설정 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: c686446f-dae1-4b05-a3df-837b3422988d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b48696fb56c40062d62f04845715170887f84fda
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728664"
---
# <a name="set-the-collation-of-user-defined-databases-to-match-those-of-the-master-and-model-databases"></a><span data-ttu-id="311f4-102">master 및 model 데이터베이스와 일치하도록 사용자 정의 데이터베이스의 데이터 정렬 설정</span><span class="sxs-lookup"><span data-stu-id="311f4-102">Set the Collation of User-defined Databases to Match Those of the master and model Databases</span></span>
  <span data-ttu-id="311f4-103">이 규칙은 사용자 정의 데이터베이스가 master 또는 model의 데이터 정렬과 동일한 데이터베이스 데이터 정렬을 사용하여 정의되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="311f4-103">This rule checks whether user-defined databases are defined by using a database collation that is the same as the collation for master or model.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="311f4-104">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="311f4-104">Best Practices Recommendations</span></span>  
 <span data-ttu-id="311f4-105">사용자 정의 데이터베이스의 데이터 정렬을 master 또는 model의 데이터 정렬과 맞추는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="311f4-105">We recommend that the collations of user-defined databases match the collation of master or model.</span></span> <span data-ttu-id="311f4-106">그렇지 않으면 데이터 정렬 충돌이 발생하여 코드가 실행되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="311f4-106">Otherwise, collation conflicts can occur that might prevent code from executing.</span></span> <span data-ttu-id="311f4-107">예를 들어 저장 프로시저가 한 테이블을 임시 테이블에 조인할 경우 사용자 정의 데이터베이스의 데이터 정렬과 model 데이터베이스의 데이터 정렬이 서로 다르면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]가 일괄 처리를 종료하고 데이터 정렬 충돌 오류를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="311f4-107">For example, when a stored procedure joins one table to a temporary table, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] might end the batch and return a collation conflict error if the collations of the user-defined database and the model database are different.</span></span> <span data-ttu-id="311f4-108">이러한 오류가 발생하는 것은 model의 데이터 정렬을 기본으로 사용하는 tempdb에서 임시 테이블이 생성되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="311f4-108">This occurs because temporary tables are created in tempdb, which bases its collation on that of model.</span></span>  
  
 <span data-ttu-id="311f4-109">데이터 정렬 충돌 오류가 발생하면 다음 중 한 가지 해결 방법을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="311f4-109">If you experience collation conflict errors, consider one of the following solutions:</span></span>  
  
-   <span data-ttu-id="311f4-110">사용자 데이터베이스의 데이터를 내보내고 master 및 model 데이터베이스와 데이터 정렬이 동일한 새로운 테이블로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="311f4-110">Export the data from the user database and import it into new tables that have the same collation as the master and model databases.</span></span>  
  
-   <span data-ttu-id="311f4-111">사용자 데이터베이스 데이터 정렬과 일치하는 데이터 정렬을 사용하도록 시스템 데이터베이스를 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="311f4-111">Rebuild the system databases to use a collation that matches the user database collation.</span></span> <span data-ttu-id="311f4-112">시스템 데이터베이스를 다시 작성 하는 방법에 대 한 자세한 내용은 [시스템 데이터베이스 다시 작성](../relational-databases/databases/system-databases.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="311f4-112">For more information about how to rebuild the system databases, see [Rebuild System Databases](../relational-databases/databases/system-databases.md).</span></span>  
  
-   <span data-ttu-id="311f4-113">사용자 테이블을 tempdb의 테이블에 조인하는 저장 프로시저는 사용자 데이터베이스의 데이터 정렬을 사용하여 tempdb에 테이블을 만들도록 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="311f4-113">Modify any stored procedures that join user tables to tables in tempdb to create the tables in tempdb by using the collation of the user database.</span></span> <span data-ttu-id="311f4-114">이렇게 하려면 다음 예에서와 같이 임시 테이블의 열 정의에 `COLLATE database_default` 절을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="311f4-114">To do this, add the `COLLATE database_default` clause to the column definitions of the temporary table, as shown in the following example:</span></span>  
  
    ```  
    CREATE TABLE #temp1 ( c1 int, c2 varchar(30) COLLATE database_default )  
    ```  
  
## <a name="for-more-information"></a><span data-ttu-id="311f4-115">참조 항목</span><span class="sxs-lookup"><span data-stu-id="311f4-115">For More Information</span></span>  
 [<span data-ttu-id="311f4-116">데이터베이스 데이터 정렬 설정 또는 변경</span><span class="sxs-lookup"><span data-stu-id="311f4-116">Set or Change the Database Collation</span></span>](../relational-databases/collations/set-or-change-the-database-collation.md)  
  
 [<span data-ttu-id="311f4-117">열 데이터 정렬 설정 또는 변경</span><span class="sxs-lookup"><span data-stu-id="311f4-117">Set or Change the Column Collation</span></span>](../relational-databases/collations/set-or-change-the-column-collation.md)  
  
 [<span data-ttu-id="311f4-118">ALTER DATABASE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="311f4-118">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
 [<span data-ttu-id="311f4-119">COLLATE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="311f4-119">COLLATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/collations)  
  
 [<span data-ttu-id="311f4-120">sys.databases&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="311f4-120">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
 [<span data-ttu-id="311f4-121">Microsoft 기술 자료 문서 325335</span><span class="sxs-lookup"><span data-stu-id="311f4-121">Microsoft Knowledge Base article 325335</span></span>](https://go.microsoft.com/fwlink/?linkid=117751)  
  
 [<span data-ttu-id="311f4-122">방법: 명령 프롬프트에서 SQL Server 2008 설치</span><span class="sxs-lookup"><span data-stu-id="311f4-122">How to: Install SQL Server 2008 from the Command Prompt</span></span>](https://go.microsoft.com/fwlink/?LinkId=81585)  
  
## <a name="see-also"></a><span data-ttu-id="311f4-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="311f4-123">See Also</span></span>  
 [<span data-ttu-id="311f4-124">정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용</span><span class="sxs-lookup"><span data-stu-id="311f4-124">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
