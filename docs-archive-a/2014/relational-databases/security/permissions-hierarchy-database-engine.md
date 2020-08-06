---
title: 사용 권한 계층(데이터베이스 엔진) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.server.permissions.f1--May use common.permissions
helpviewer_keywords:
- security [SQL Server], denying access
- hierarchies [SQL Server], permissions
- securables [SQL Server]
- security [SQL Server], permissions
- permissions [SQL Server], hierarchy
- security [SQL Server], granting access
ms.assetid: f6d20a55-ef03-4e14-85f9-009902889866
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 9a04e5595e509de63b362b31b240e113e635581d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730375"
---
# <a name="permissions-hierarchy-database-engine"></a><span data-ttu-id="411a6-102">사용 권한 계층(데이터베이스 엔진)</span><span class="sxs-lookup"><span data-stu-id="411a6-102">Permissions Hierarchy (Database Engine)</span></span>
  <span data-ttu-id="411a6-103">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] 는 사용 권한으로 보호될 수 있는 엔터티의 계층적 컬렉션을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="411a6-103">The [!INCLUDE[ssDE](../../../includes/ssde-md.md)] manages a hierarchical collection of entities that can be secured with permissions.</span></span> <span data-ttu-id="411a6-104">이러한 엔터티를 *보안 개체*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="411a6-104">These entities are known as *securables*.</span></span> <span data-ttu-id="411a6-105">가장 두드러진 보안 개체는 서버와 데이터베이스이지만 별개의 사용 권한을 보다 세부적인 수준으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="411a6-105">The most prominent securables are servers and databases, but discrete permissions can be set at a much finer level.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="411a6-106">는 적합한 권한이 부여되었는지 확인하여 보안 개체에 대한 보안 주체의 동작을 규제합니다.</span><span class="sxs-lookup"><span data-stu-id="411a6-106">regulates the actions of principals on securables by verifying that they have been granted appropriate permissions.</span></span>

 <span data-ttu-id="411a6-107">다음 그림에서는 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 사용 권한 계층 간의 관계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="411a6-107">The following illustration shows the relationships among the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] permissions hierarchies.</span></span>

 <span data-ttu-id="411a6-108">![데이터베이스 엔진 권한 계층 구조 다이어그램](../../database-engine/media/wj-security-layers.gif "데이터베이스 엔진 권한 계층 구조 다이어그램")</span><span class="sxs-lookup"><span data-stu-id="411a6-108">![Diagram of Database Engine permissions hierarchies](../../database-engine/media/wj-security-layers.gif "Diagram of Database Engine permissions hierarchies")</span></span>

## <a name="chart-of-sql-server-permissions"></a><span data-ttu-id="411a6-109">SQL Server 사용 권한 차트</span><span class="sxs-lookup"><span data-stu-id="411a6-109">Chart of SQL Server Permissions</span></span>
 <span data-ttu-id="411a6-110">pdf 형식의 모든 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 권한에 대한 포스터 크기의 차트를 보려면 [https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="411a6-110">For a poster sized chart of all [!INCLUDE[ssDE](../../../includes/ssde-md.md)] permissions in pdf format, see [https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf).</span></span>

## <a name="working-with-permissions"></a><span data-ttu-id="411a6-111">사용 권한 작업</span><span class="sxs-lookup"><span data-stu-id="411a6-111">Working with Permissions</span></span>
 <span data-ttu-id="411a6-112">익숙한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리인 GRANT, DENY 및 REVOKE를 사용하여 사용 권한을 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="411a6-112">Permissions can be manipulated with the familiar [!INCLUDE[tsql](../../includes/tsql-md.md)] queries GRANT, DENY, and REVOKE.</span></span> <span data-ttu-id="411a6-113">사용 권한에 대한 정보는 [sys.server_permissions](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql) 및 [sys.database_permissions](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql) 카탈로그 뷰에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="411a6-113">Information about permissions is visible in the [sys.server_permissions](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql) and [sys.database_permissions](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql) catalog views.</span></span> <span data-ttu-id="411a6-114">또한 기본 제공 함수를 사용한 사용 권한 정보 쿼리도 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="411a6-114">There is also support for querying permissions information by using built-in functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="411a6-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="411a6-115">See Also</span></span>
 <span data-ttu-id="411a6-116">[SQL Server](securing-sql-server.md) [사용 권한 &#40;데이터베이스 엔진&#41;](permissions-database-engine.md) [보안 개체](securables.md) [보안 주체 &#40;](authentication-access/principals-database-engine.md) 데이터베이스 엔진&#41;[transact-sql &#40;&#41;](/sql/t-sql/statements/grant-transact-sql) transact-sql &#40;[DENY](/sql/t-sql/statements/deny-transact-sql) [&#41;transact-sql](/sql/t-sql/statements/revoke-transact-sql) [&#40;&#41;HAS_PERMS_BY_NAME](/sql/t-sql/functions/has-perms-by-name-transact-sql) transact-sql &#40;&#41;[fn_builtin_permissions transact-sql &#40;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql)&#41;server_permissions [transact-sql &#40;&#41;](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql) database_permissions &#40;&#41;. [transact-sql](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="411a6-116">[Securing SQL Server](securing-sql-server.md) [Permissions &#40;Database Engine&#41;](permissions-database-engine.md) [Securables](securables.md) [Principals &#40;Database Engine&#41;](authentication-access/principals-database-engine.md) [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) [REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql) [DENY &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-transact-sql) [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/has-perms-by-name-transact-sql) [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql) [sys.server_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql) [sys.database_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql)</span></span>


