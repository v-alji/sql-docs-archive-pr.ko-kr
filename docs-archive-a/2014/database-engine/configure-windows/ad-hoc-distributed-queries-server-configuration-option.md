---
title: ad hoc distributed queries 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- OPENROWSET function, ad hoc distributed queries option
- Ad Hoc Distributed Queries option
- ad hoc distributed queries
- 7415 (Database Engine Error)
- OPENDATASOURCE function, ad hoc distributed queries option
- ad hoc access
ms.assetid: 5b982015-e196-44c3-83b8-275fb9d769b2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d07b3c038597916cdaf026e24e90aab9d6b61616
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638993"
---
# <a name="ad-hoc-distributed-queries-server-configuration-option"></a><span data-ttu-id="87715-102">임시 분산 쿼리 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="87715-102">ad hoc distributed queries Server Configuration Option</span></span>
  <span data-ttu-id="87715-103">기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 OPENROWSET 및 OPENDATASOURCE를 사용하는 임시 분산 쿼리를 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="87715-103">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not allow ad hoc distributed queries using OPENROWSET and OPENDATASOURCE.</span></span> <span data-ttu-id="87715-104">이 옵션을 1로 설정하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 임시 액세스가 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="87715-104">When this option is set to 1, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] allows ad hoc access.</span></span> <span data-ttu-id="87715-105">이 옵션을 설정하지 않거나 0로 설정하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 임시 액세스가 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="87715-105">When this option is not set or is set to 0, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not allow ad hoc access.</span></span>  
  
 <span data-ttu-id="87715-106">임시 분산 쿼리에서는 OPENROWSET 및 OPENDATASOURCE 함수를 사용하여 OLE DB를 사용하는 원격 데이터 원본에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="87715-106">Ad hoc distributed queries use the OPENROWSET and OPENDATASOURCE functions to connect to remote data sources that use OLE DB.</span></span> <span data-ttu-id="87715-107">OPENROWSET과 OPENDATASOURCE는 자주 사용되지 않는 OLE DB 데이터 원본을 참조하기 위해서만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87715-107">OPENROWSET and OPENDATASOURCE should be used only to reference OLE DB data sources that are accessed infrequently.</span></span> <span data-ttu-id="87715-108">여러 번 액세스될 모든 데이터 원본에 대해서는 연결된 서버를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87715-108">For any data sources that will be accessed more than several times, define a linked server.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="87715-109">임시 이름 사용을 설정하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 대한 모든 인증된 로그인에서 공급자에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87715-109">Enabling the use of ad hoc names means that any authenticated login to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can access the provider.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="87715-110">관리자는 모든 로컬 로그인에서 액세스해도 안전한 공급자에 대해 이 기능을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87715-110">administrators should enable this feature for providers that are safe to be accessed by any local login.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87715-111">설명</span><span class="sxs-lookup"><span data-stu-id="87715-111">Remarks</span></span>  
 <span data-ttu-id="87715-112">**임시 분산 쿼리**가 설정되지 않은 임시 연결을 만들려고 하면 오류가 발생합니다. 메시지 7415, 수준 16, 상태 1, 줄 1</span><span class="sxs-lookup"><span data-stu-id="87715-112">Attempting to make an ad hoc connection with **Ad Hoc Distributed Queries** not enabled results in error: Msg 7415, Level 16, State 1, Line 1</span></span>  
  
 <span data-ttu-id="87715-113">OLE DB 공급자 'Microsoft.ACE.OLEDB.12.0'에 대한 임의 액세스가 거부되었습니다.</span><span class="sxs-lookup"><span data-stu-id="87715-113">Ad hoc access to OLE DB provider 'Microsoft.ACE.OLEDB.12.0' has been denied.</span></span> <span data-ttu-id="87715-114">연결된 서버를 통해 이 공급자에 액세스해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87715-114">You must access this provider through a linked server.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="87715-115">예제</span><span class="sxs-lookup"><span data-stu-id="87715-115">Examples</span></span>  
 <span data-ttu-id="87715-116">다음 예에서는 임시 분산 쿼리를 실행한 다음 `Seattle1` 함수를 사용하여 `OPENROWSET` 이라는 서버를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="87715-116">The following example enables ad hoc distributed queries and then queries a server named `Seattle1` using the `OPENROWSET` function.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
RECONFIGURE;  
sp_configure 'Ad Hoc Distributed Queries', 1;  
RECONFIGURE;  
GO  
  
SELECT a.*  
FROM OPENROWSET('SQLNCLI', 'Server=Seattle1;Trusted_Connection=yes;',  
     'SELECT GroupName, Name, DepartmentID  
      FROM AdventureWorks2012.HumanResources.Department  
      ORDER BY GroupName, Name') AS a;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="87715-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="87715-117">See Also</span></span>  
 <span data-ttu-id="87715-118">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="87715-118">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="87715-119">[연결된 서버&#40;데이터베이스 엔진&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="87715-119">[Linked Servers &#40;Database Engine&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md) </span></span>  
 <span data-ttu-id="87715-120">[OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="87715-120">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="87715-121">[OPENDATASOURCE&#40;Transact-SQL&#41;](/sql/t-sql/functions/opendatasource-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="87715-121">[OPENDATASOURCE &#40;Transact-SQL&#41;](/sql/t-sql/functions/opendatasource-transact-sql) </span></span>  
 [<span data-ttu-id="87715-122">sp_addlinkedserver&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="87715-122">sp_addlinkedserver &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)  
  
  
