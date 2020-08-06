---
title: SQL Server 테이블에서 열 제거 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- removing columns
- DropColumn function
- SQL Server Native Client OLE DB provider, columns
ms.assetid: 210811b7-cbd6-421e-bc6e-df9482236768
author: rothja
ms.author: jroth
ms.openlocfilehash: 8f40c466910aae7e0d349cd4a65ab265282bc8eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652079"
---
# <a name="removing-a-column-from-a-sql-server-table"></a><span data-ttu-id="015a1-102">SQL Server 테이블에서 열 제거</span><span class="sxs-lookup"><span data-stu-id="015a1-102">Removing a Column from a SQL Server Table</span></span>
  <span data-ttu-id="015a1-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 **Itabledefinition::D ropcolumn** 함수를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="015a1-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **ITableDefinition::DropColumn** function.</span></span> <span data-ttu-id="015a1-104">이 함수를 사용하여 소비자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에서 열을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="015a1-104">This allows consumers to remove a column from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="015a1-105">소비자는 *pTableID* 매개 변수에서 *uName* 공용 구조체의 *pwszName* 멤버에서 테이블 이름을 유니코드 문자열로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="015a1-105">Consumers specify the table name as a Unicode character string in the *pwszName*member of the *uName* union in the *pTableID* parameter.</span></span> <span data-ttu-id="015a1-106">*pTableID*의 *eKind*멤버는 DBKIND_NAME이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="015a1-106">The *eKind*member of *pTableID* must be DBKIND_NAME.</span></span>  
  
 <span data-ttu-id="015a1-107">소비자는 *pColumnID* 매개 변수에서 *uName* 공용 구조체의 *pwszName* 구성원에 열 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="015a1-107">The consumer indicates a column name in the *pwszName*member of the *uName* union in the *pColumnID* parameter.</span></span> <span data-ttu-id="015a1-108">열 이름은 유니코드 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="015a1-108">The column name is a Unicode character string.</span></span> <span data-ttu-id="015a1-109">*pColumnID*의 *eKind*멤버는 DBKIND_NAME이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="015a1-109">The *eKind* member of *pColumnID* must be DBKIND_NAME.</span></span>  
  
## <a name="example"></a><span data-ttu-id="015a1-110">예제</span><span class="sxs-lookup"><span data-stu-id="015a1-110">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="015a1-111">코드</span><span class="sxs-lookup"><span data-stu-id="015a1-111">Code</span></span>  
  
```  
DBID TableID;  
DBID ColumnID;  
HRESULT hr;  
  
TableID.eKind = DBKIND_NAME;  
TableID.uName.pwszName = L"MyTableName";  
  
ColumnID.eKind = DBKIND_NAME;  
ColumnID.uName.pwszName = L"MyColumnName";  
  
hr = m_pITableDefinition->DropColumn(&TableID, &ColumnID);  
```  
  
## <a name="see-also"></a><span data-ttu-id="015a1-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="015a1-112">See Also</span></span>  
 [<span data-ttu-id="015a1-113">테이블 및 인덱스</span><span class="sxs-lookup"><span data-stu-id="015a1-113">Tables and Indexes</span></span>](tables-and-indexes.md)  
  
  
