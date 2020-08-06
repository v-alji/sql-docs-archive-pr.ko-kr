---
title: SQL Server 인덱스 삭제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- removing indexes
- deleting indexes
- DropIndex function
- dropping indexes
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: add3ba14-10b1-4723-b7c0-3e83689e9fdd
author: rothja
ms.author: jroth
ms.openlocfilehash: 1267cc92645ff8b28757ad2d266e58917fcb4b28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652081"
---
# <a name="dropping-a-sql-server-index"></a><span data-ttu-id="fa6f9-102">SQL Server 인덱스 삭제</span><span class="sxs-lookup"><span data-stu-id="fa6f9-102">Dropping a SQL Server Index</span></span>
  <span data-ttu-id="fa6f9-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 **Iindexdefinition::D ropindex** 함수를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6f9-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **IIndexDefinition::DropIndex** function.</span></span> <span data-ttu-id="fa6f9-104">이 함수를 사용하여 소비자는 인덱스를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에서 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6f9-104">This allows consumers to remove an index from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="fa6f9-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 일부 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기본 키 및 UNIQUE 제약 조건을 인덱스로 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6f9-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes some [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PRIMARY KEY and UNIQUE constraints as indexes.</span></span> <span data-ttu-id="fa6f9-106">테이블 소유자, 데이터베이스 소유자 및 일부 관리 역할 멤버는 제약 조건을 삭제하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6f9-106">The table owner, database owner, and some administrative role members can modify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table, dropping a constraint.</span></span> <span data-ttu-id="fa6f9-107">기본적으로 테이블 소유자만 기존 인덱스를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6f9-107">By default, only the table owner can drop an existing index.</span></span> <span data-ttu-id="fa6f9-108">따라서 **DropIndex** 성공 또는 실패 여부는 애플리케이션 사용자의 액세스 권한뿐만 아니라 해당 인덱스의 유형에 따라서도 좌우됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa6f9-108">Therefore, **DropIndex** success or failure depends not only on the application user's access rights but also on the type of index indicated.</span></span>  
  
 <span data-ttu-id="fa6f9-109">소비자는 *pTableID* 매개 변수에서 *uName* 공용 구조체의 *pwszName* 멤버에 테이블 이름을 유니코드 문자열로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6f9-109">Consumers specify the table name as a Unicode character string in the *pwszName* member of the *uName* union in the *pTableID* parameter.</span></span> <span data-ttu-id="fa6f9-110">*pTableID*의 *eKind* 멤버는 DBKIND_NAME이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6f9-110">The *eKind* member of *pTableID* must be DBKIND_NAME.</span></span>  
  
 <span data-ttu-id="fa6f9-111">소비자는 *pIndexID* 매개 변수에서 *uName* 공용 구조체의 *pwszName* 멤버에 인덱스 이름을 유니코드 문자열로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6f9-111">Consumers specify the index name as a Unicode character string in the *pwszName* member of the *uName* union in the *pIndexID* parameter.</span></span> <span data-ttu-id="fa6f9-112">*pIndexID*의 *eKind* 멤버는 DBKIND_NAME이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6f9-112">The *eKind* member of *pIndexID* must be DBKIND_NAME.</span></span> <span data-ttu-id="fa6f9-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 *Pindexid* 가 null 인 경우 테이블에 있는 모든 인덱스를 삭제 하는 OLE DB 기능을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6f9-113">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support the OLE DB feature of dropping all indexes on a table when *pIndexID* is null.</span></span> <span data-ttu-id="fa6f9-114">*pIndexID*가 null이면 E_INVALIDARG가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa6f9-114">If *pIndexID* is null, E_INVALIDARG is returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa6f9-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fa6f9-115">See Also</span></span>  
 <span data-ttu-id="fa6f9-116">[테이블 및 인덱스](tables-and-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="fa6f9-116">[Tables and Indexes](tables-and-indexes.md) </span></span>  
 <span data-ttu-id="fa6f9-117">[ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fa6f9-117">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 [<span data-ttu-id="fa6f9-118">DROP INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fa6f9-118">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
  
