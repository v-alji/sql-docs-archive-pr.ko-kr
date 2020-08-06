---
title: 행 수준 보안 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- row level security described
- row level security
- access control predicates
- security [SQL Server], predicate based access control
- predicate based security
ms.assetid: 7221fa4e-ca4a-4d5c-9f93-1b8a4af7b9e8
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: c67f84723e79b66d0454fb509f2fa9ced03dac7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730344"
---
# <a name="row-level-security"></a><span data-ttu-id="a0340-102">행 수준 보안</span><span class="sxs-lookup"><span data-stu-id="a0340-102">Row-Level Security</span></span>
  <span data-ttu-id="a0340-103">행 수준 보안을 통해 고객은 쿼리를 실행하는 사용자의 특성(예: 그룹 멤버 자격 또는 실행 컨텍스트)을 기반으로 하여 데이터베이스 테이블의 행에 대한 액세스를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0340-103">Row-Level Security enables customers to control access to rows in a database table based on the characteristics of the user executing a query (e.g., group membership or execution context).</span></span> <span data-ttu-id="a0340-104">행 수준 보안은 이제 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0340-104">Row-Level Security is now available in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016.</span></span> <span data-ttu-id="a0340-105">이 기능에 대한 최신 설명을 보려면 최신 설명서에서 [행 수준 보안](https://msdn.microsoft.com/library/dn765131.aspx) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a0340-105">See [Row-Level Security](https://msdn.microsoft.com/library/dn765131.aspx) in the current documentation for the current description of this feature.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0340-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a0340-106">See Also</span></span>  
 <span data-ttu-id="a0340-107">[Azure SQL Database&#41;&#40;보안 정책 만들기](/sql/t-sql/statements/create-security-policy-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a0340-107">[CREATE SECURITY POLICY &#40;Azure SQL Database&#41;](/sql/t-sql/statements/create-security-policy-transact-sql) </span></span>  
 <span data-ttu-id="a0340-108">[ALTER SECURITY POLICY &#40;Azure SQL Database&#41;](/sql/t-sql/statements/alter-security-policy-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a0340-108">[ALTER SECURITY POLICY &#40;Azure SQL Database&#41;](/sql/t-sql/statements/alter-security-policy-transact-sql) </span></span>  
 <span data-ttu-id="a0340-109">[DROP SECURITY POLICY &#40;Azure SQL Database&#41;](/sql/t-sql/statements/drop-security-policy-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a0340-109">[DROP SECURITY POLICY &#40;Azure SQL Database&#41;](/sql/t-sql/statements/drop-security-policy-transact-sql) </span></span>  
 <span data-ttu-id="a0340-110">[CREATE FUNCTION&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a0340-110">[CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) </span></span>  
 <span data-ttu-id="a0340-111">[security_policies &#40;Azure SQL Database&#41;](/sql/relational-databases/system-catalog-views/sys-security-policies-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a0340-111">[sys.security_policies &#40;Azure SQL Database&#41;](/sql/relational-databases/system-catalog-views/sys-security-policies-transact-sql) </span></span>  
 <span data-ttu-id="a0340-112">[security_predicates &#40;Azure SQL Database&#41;](/sql/relational-databases/system-catalog-views/sys-security-predicates-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a0340-112">[sys.security_predicates &#40;Azure SQL Database&#41;](/sql/relational-databases/system-catalog-views/sys-security-predicates-transact-sql) </span></span>  
 [<span data-ttu-id="a0340-113">사용자 정의 함수 만들기&#40;데이터베이스 엔진&#41;</span><span class="sxs-lookup"><span data-stu-id="a0340-113">Create User-defined Functions &#40;Database Engine&#41;</span></span>](../user-defined-functions/create-user-defined-functions-database-engine.md)  
  
  
