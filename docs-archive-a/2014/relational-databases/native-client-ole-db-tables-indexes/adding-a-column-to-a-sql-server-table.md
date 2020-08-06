---
title: SQL Server 테이블에 열 추가 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- AddColumn function
- SQL Server Native Client OLE DB provider, columns
- adding columns
ms.assetid: 22bae18a-bc9d-4617-8660-ed8b17a468d4
author: rothja
ms.author: jroth
ms.openlocfilehash: 97aa2656ccde662a34e1dd80fd662b22f601d4ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739801"
---
# <a name="adding-a-column-to-a-sql-server-table"></a><span data-ttu-id="35d0f-102">SQL Server 테이블에 열 추가</span><span class="sxs-lookup"><span data-stu-id="35d0f-102">Adding a Column to a SQL Server Table</span></span>
  <span data-ttu-id="35d0f-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 **Itabledefinition:: addcolumn** 함수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="35d0f-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **ITableDefinition::AddColumn** function.</span></span> <span data-ttu-id="35d0f-104">소비자가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에 열을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35d0f-104">This allows consumers to add a column to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="35d0f-105">테이블에 열을 추가할 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자 소비자는 다음과 같이 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35d0f-105">When you add a column to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer is constrained as follows:</span></span>  
  
-   <span data-ttu-id="35d0f-106">DBPROP_COL_AUTOINCREMENT가 VARIANT_TRUE이면 DBPROP_COL_NULLABLE은 VARIANT_FALSE여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35d0f-106">If DBPROP_COL_AUTOINCREMENT is VARIANT_TRUE, DBPROP_COL_NULLABLE must be VARIANT_FALSE.</span></span>  
  
-   <span data-ttu-id="35d0f-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **timestamp** 데이터 형식을 사용하여 열을 정의하는 경우 DBPROP_COL_NULLABLE은 VARIANT_FALSE여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35d0f-107">If the column is defined by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **timestamp** data type, DBPROP_COL_NULLABLE must be VARIANT_FALSE.</span></span>  
  
-   <span data-ttu-id="35d0f-108">다른 모든 열 정의에서 DBPROP_COL_NULLABLE은 VARIANT_TRUE여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35d0f-108">For any other column definition, DBPROP_COL_NULLABLE must be VARIANT_TRUE.</span></span>  
  
 <span data-ttu-id="35d0f-109">소비자는 *pTableID* 매개 변수에서 *uName* 공용 구조체의 *pwszName* 멤버에 테이블 이름을 유니코드 문자열로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35d0f-109">Consumers specify the table name as a Unicode character string in the *pwszName* member of the *uName* union in the *pTableID* parameter.</span></span> <span data-ttu-id="35d0f-110">*pTableID*의 *eKind* 멤버는 DBKIND_NAME이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35d0f-110">The *eKind* member of *pTableID* must be DBKIND_NAME.</span></span>  
  
 <span data-ttu-id="35d0f-111">새로운 열 이름은 DBCOLUMNDESC 매개 변수 *pColumnDesc*의 *dbcid* 멤버에 있는 *uName* 공용 구조체의 *pwszName* 멤버에서 유니코드 문자열로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="35d0f-111">The new column name is specified as a Unicode character string in the *pwszName* member of the *uName* union in the *dbcid* member of the DBCOLUMNDESC parameter *pColumnDesc*.</span></span> <span data-ttu-id="35d0f-112">*eKind* 멤버는 DBKIND_NAME이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35d0f-112">The *eKind* member must be DBKIND_NAME.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35d0f-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="35d0f-113">See Also</span></span>  
 <span data-ttu-id="35d0f-114">[테이블 및 인덱스](tables-and-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="35d0f-114">[Tables and Indexes](tables-and-indexes.md) </span></span>  
 [<span data-ttu-id="35d0f-115">ALTER TABLE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="35d0f-115">ALTER TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-table-transact-sql)  
  
  
