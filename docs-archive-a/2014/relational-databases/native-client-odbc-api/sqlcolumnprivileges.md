---
title: SQLColumnPrivileges | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLColumnPrivileges function
ms.assetid: c78acd4e-8668-4abc-9bc9-6ad381965863
author: rothja
ms.author: jroth
ms.openlocfilehash: bf46fed47817ed94ea2382f2147df254f2986aec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647676"
---
# <a name="sqlcolumnprivileges"></a><span data-ttu-id="7de82-102">SQLColumnPrivileges</span><span class="sxs-lookup"><span data-stu-id="7de82-102">SQLColumnPrivileges</span></span>
  <span data-ttu-id="7de82-103">**Sqlcolumnprivileges** *CatalogName*, *SchemaName*, *TableName*또는 *ColumnName* 매개 변수에 대 한 값이 있는지 여부를 SQL_SUCCESS를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7de82-103">**SQLColumnPrivileges** returns SQL_SUCCESS whether or not values exist for the*CatalogName*, *SchemaName*, *TableName*, or *ColumnName* parameters.</span></span> <span data-ttu-id="7de82-104">이러한 매개 변수에 잘못 된 값이 사용 되는 경우 **Sqlfetch** SQL_NO_DATA 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7de82-104">**SQLFetch** returns SQL_NO_DATA when invalid values are used in these parameters.</span></span>  
  
 <span data-ttu-id="7de82-105">**Sqlcolumnprivileges** 정적 서버 커서에 대해 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7de82-105">**SQLColumnPrivileges** can be executed on a static server cursor.</span></span> <span data-ttu-id="7de82-106">업데이트할 수 있는 (동적 또는 키 집합) 커서에 대해 **Sqlcolumnprivileges** 실행 시도는 커서 유형이 변경 되었음을 나타내는 SQL_SUCCESS_WITH_INFO 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7de82-106">An attempt to execute **SQLColumnPrivileges** on an updatable (dynamic or keyset) cursor will return SQL_SUCCESS_WITH_INFO indicating that the cursor type has been changed.</span></span>  
  
 <span data-ttu-id="7de82-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 *CatalogName* 매개 변수의 두 부분으로 구성된 이름인 *Linked_Server_Name.Catalog_Name*을 사용하여 연결된 서버의 테이블에 대한 정보를 보고할 수 있도록 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7de82-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports reporting information for tables on linked servers by accepting a two-part name for the *CatalogName* parameter: *Linked_Server_Name.Catalog_Name*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7de82-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7de82-108">See Also</span></span>  
 <span data-ttu-id="7de82-109">[SQLColumnPrivileges 함수](https://go.microsoft.com/fwlink/?LinkId=59335) </span><span class="sxs-lookup"><span data-stu-id="7de82-109">[SQLColumnPrivileges Function](https://go.microsoft.com/fwlink/?LinkId=59335) </span></span>  
 [<span data-ttu-id="7de82-110">ODBC API 구현 정보</span><span class="sxs-lookup"><span data-stu-id="7de82-110">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
