---
title: SQLPrimaryKeys | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLPrimaryKeys function
ms.assetid: bc61cd5b-d2f4-4f87-abc7-743cf9ea772d
author: rothja
ms.author: jroth
ms.openlocfilehash: 67a932996ccbf52f5ab21fd6aa62381184ebc510
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660527"
---
# <a name="sqlprimarykeys"></a><span data-ttu-id="74cb4-102">SQLPrimaryKeys</span><span class="sxs-lookup"><span data-stu-id="74cb4-102">SQLPrimaryKeys</span></span>
  <span data-ttu-id="74cb4-103">테이블에는 고유한 행 식별자로 사용할 수 있는 열이 있을 수 있으며, PRIMARY KEY 제약 조건 없이 만든 테이블은 SQLPrimaryKeys에 빈 결과 집합을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="74cb4-103">A table might have a column or columns that can serve as unique row identifiers, and tables created without a PRIMARY KEY constraint return an empty result set to SQLPrimaryKeys.</span></span> <span data-ttu-id="74cb4-104">ODBC 함수 [SQLSpecialColumns](sqlspecialcolumns.md) 는 기본 키가 없는 테이블에 대 한 행 식별자 후보를 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="74cb4-104">The ODBC function [SQLSpecialColumns](sqlspecialcolumns.md) reports row identifier candidates for tables without primary keys.</span></span>  
  
 <span data-ttu-id="74cb4-105">SQLPrimaryKeys는 *CatalogName*, *SchemaName*또는 *TableName* 매개 변수에 대 한 값이 있는지 여부를 SQL_SUCCESS를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="74cb4-105">SQLPrimaryKeys returns SQL_SUCCESS whether or not values exist for *CatalogName*, *SchemaName*, or *TableName* parameters.</span></span> <span data-ttu-id="74cb4-106">이 매개 변수에 잘못된 값이 사용되면 SQLFetch는 SQL_NO_DATA를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="74cb4-106">SQLFetch returns SQL_NO_DATA when invalid values are used in these parameters.</span></span>  
  
 <span data-ttu-id="74cb4-107">SQLPrimaryKeys는 정적 서버 커서에 대해 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74cb4-107">SQLPrimaryKeys can be executed on a static server cursor.</span></span> <span data-ttu-id="74cb4-108">업데이트할 수 있는 (동적 또는 키 집합) 커서에 대해 SQLPrimaryKeys를 실행 하려고 하면 커서 유형이 변경 되었음을 나타내는 SQL_SUCCESS_WITH_INFO 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74cb4-108">An attempt to execute SQLPrimaryKeys on an updatable (dynamic or keyset) cursor will return SQL_SUCCESS_WITH_INFO indicating that the cursor type has been changed.</span></span>  
  
 <span data-ttu-id="74cb4-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 *CatalogName* 매개 변수의 두 부분으로 구성된 이름인 *Linked_Server_Name.Catalog_Name*을 사용하여 연결된 서버의 테이블에 대한 정보를 보고할 수 있도록 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="74cb4-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports reporting information for tables on linked servers by accepting a two-part name for the *CatalogName* parameter: *Linked_Server_Name.Catalog_Name*.</span></span>  
  
## <a name="sqlprimarykeys-and-table-valued-parameters"></a><span data-ttu-id="74cb4-110">SQLPrimaryKeys 및 테이블 반환 매개 변수</span><span class="sxs-lookup"><span data-stu-id="74cb4-110">SQLPrimaryKeys and Table-Valued Parameters</span></span>  
 <span data-ttu-id="74cb4-111">Statement 특성 SQL_SOPT_SS_NAME_SCOPE의 기본값 SQL_SS_NAME_SCOPE_TABLE이 아닌 SQL_SS_NAME_SCOPE_TABLE_TYPE 값이 있으면 SQLPrimaryKeys는 테이블 형식의 기본 키 열에 대 한 정보를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="74cb4-111">If the statement attribute SQL_SOPT_SS_NAME_SCOPE has the value SQL_SS_NAME_SCOPE_TABLE_TYPE, rather than its default value of SQL_SS_NAME_SCOPE_TABLE, SQLPrimaryKeys will return information about primary key columns of table types.</span></span> <span data-ttu-id="74cb4-112">SQL_SOPT_SS_NAME_SCOPE에 대 한 자세한 내용은 [SQLSetStmtAttr](sqlsetstmtattr.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="74cb4-112">For more information on SQL_SOPT_SS_NAME_SCOPE, see [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span>  
  
 <span data-ttu-id="74cb4-113">테이블 반환 매개 변수에 대 한 자세한 내용은 [ODBC&#41;&#40;테이블 반환 매개 변수 ](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="74cb4-113">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74cb4-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="74cb4-114">See Also</span></span>  
 <span data-ttu-id="74cb4-115">[SQLPrimaryKeys 함수](https://go.microsoft.com/fwlink/?LinkId=59361) </span><span class="sxs-lookup"><span data-stu-id="74cb4-115">[SQLPrimaryKeys Function](https://go.microsoft.com/fwlink/?LinkId=59361) </span></span>  
 [<span data-ttu-id="74cb4-116">ODBC API 구현 정보</span><span class="sxs-lookup"><span data-stu-id="74cb4-116">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
