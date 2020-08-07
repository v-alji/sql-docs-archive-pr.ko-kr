---
title: 스파스 열 지원 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 11ae959f-2fb6-4b85-ac5d-1476a82136d4
author: rothja
ms.author: jroth
ms.openlocfilehash: 076709f3f37e92492f7c3f8c20ee692416d9e867
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734024"
---
# <a name="sparse-columns-support-odbc"></a><span data-ttu-id="842f8-102">스파스 열 지원(ODBC)</span><span class="sxs-lookup"><span data-stu-id="842f8-102">Sparse Columns Support (ODBC)</span></span>
  <span data-ttu-id="842f8-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC의 스파스 열 지원에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="842f8-103">This topic describes [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC support for sparse columns.</span></span> <span data-ttu-id="842f8-104">스파스 열에 대 한 ODBC 지원을 보여 주는 샘플은 [스파스 열이 있는 테이블에 대해 Sqlcolumns 호출](../../native-client-odbc-how-to/call-sqlcolumns-on-a-table-with-sparse-columns.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="842f8-104">For a sample demonstrating ODBC support for sparse columns, see [Call SQLColumns on a Table with Sparse Columns](../../native-client-odbc-how-to/call-sqlcolumns-on-a-table-with-sparse-columns.md).</span></span> <span data-ttu-id="842f8-105">스파스 열에 대한 자세한 내용은 [Sparse Columns Support in SQL Server Native Client](../features/sparse-columns-support-in-sql-server-native-client.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="842f8-105">For more information about sparse columns, see [Sparse Columns Support in SQL Server Native Client](../features/sparse-columns-support-in-sql-server-native-client.md).</span></span>  
  
## <a name="statement-metadata"></a><span data-ttu-id="842f8-106">문 메타데이터</span><span class="sxs-lookup"><span data-stu-id="842f8-106">Statement Metadata</span></span>  
 <span data-ttu-id="842f8-107">APD(애플리케이션 매개 변수 설명자) 설명자 필드 및 SQL_SOPT_SS_NAME_SCOPE 문 특성에는 추가 값 SQL_SS_NAME_SCOPE_EXTENDED 및 SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="842f8-107">The application parameter descriptor (APD) descriptor field and SQL_SOPT_SS_NAME_SCOPE statement attribute accepts the additional values SQL_SS_NAME_SCOPE_EXTENDED and SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET.</span></span> <span data-ttu-id="842f8-108">이러한 값은 [SQLColumns](../../native-client-odbc-api/sqlcolumns.md)에서 반환하는 결과 집합에 포함할 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="842f8-108">These values specify which columns are included in the result set returned by [SQLColumns](../../native-client-odbc-api/sqlcolumns.md).</span></span> <span data-ttu-id="842f8-109">SQL_SOPT_SS_NAME_SCOPE에 대한 자세한 내용은 [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="842f8-109">For more information about SQL_SOPT_SS_NAME_SCOPE, see [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md).</span></span>  
  
 <span data-ttu-id="842f8-110">SQL_CA_SS_IS_COLUMN_SET이라는 읽기 전용 SQLSMALLINT 필드인 새 IRD(구현 행 설명자)를 사용하여 열이 XML `column_set` 값인지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="842f8-110">A new implementation row descriptor (IRD), a read-only SQLSMALLINT field called SQL_CA_SS_IS_COLUMN_SET, can be used to determine if a column is an XML `column_set` value.</span></span> <span data-ttu-id="842f8-111">SQL_CA_SS_IS_COLUMN_SET에는 SQL_TRUE 및 SQL_FALSE 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="842f8-111">SQL_CA_SS_IS_COLUMN_SET takes the values SQL_TRUE and SQL_FALSE.</span></span>  
  
## <a name="catalog-metadata"></a><span data-ttu-id="842f8-112">카탈로그 메타데이터</span><span class="sxs-lookup"><span data-stu-id="842f8-112">Catalog Metadata</span></span>  
 <span data-ttu-id="842f8-113">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Sqlcolumns](../../native-client-odbc-api/sqlcolumns.md)의 결과 집합에 두 개의 특정 열 (SS_IS_SPARSE 및 SS_IS_COLUMN_SET)이 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="842f8-113">Two [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] specific columns (SS_IS_SPARSE and SS_IS_COLUMN_SET) have been added to the result set for [SQLColumns](../../native-client-odbc-api/sqlcolumns.md).</span></span>  
  
## <a name="odbc-function-support-for-sparse-columns"></a><span data-ttu-id="842f8-114">스파스 열에 대한 ODBC 함수 지원</span><span class="sxs-lookup"><span data-stu-id="842f8-114">ODBC Function Support for Sparse Columns</span></span>  
 <span data-ttu-id="842f8-115">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client에서는 다음과 같은 ODBC 함수가 스파스 열을 지원하도록 업데이트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="842f8-115">The following ODBC functions have been updated to support sparse columns in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client:</span></span>  
  
-   [<span data-ttu-id="842f8-116">SQLColAttribute</span><span class="sxs-lookup"><span data-stu-id="842f8-116">SQLColAttribute</span></span>](../../native-client-odbc-api/sqlcolattribute.md)  
  
-   [<span data-ttu-id="842f8-117">SQLColumns</span><span class="sxs-lookup"><span data-stu-id="842f8-117">SQLColumns</span></span>](../../native-client-odbc-api/sqlcolumns.md)  
  
-   [<span data-ttu-id="842f8-118">SQLGetDescField</span><span class="sxs-lookup"><span data-stu-id="842f8-118">SQLGetDescField</span></span>](../../native-client-odbc-api/sqlgetdescfield.md)  
  
-   [<span data-ttu-id="842f8-119">SQLSetDescField</span><span class="sxs-lookup"><span data-stu-id="842f8-119">SQLSetDescField</span></span>](../../native-client-odbc-api/sqlsetdescfield.md)  
  
-   [<span data-ttu-id="842f8-120">SQLSetStmtAttr</span><span class="sxs-lookup"><span data-stu-id="842f8-120">SQLSetStmtAttr</span></span>](../../native-client-odbc-api/sqlsetstmtattr.md)  
  
## <a name="see-also"></a><span data-ttu-id="842f8-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="842f8-121">See Also</span></span>  
 [<span data-ttu-id="842f8-122">SQL Server Native Client &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="842f8-122">SQL Server Native Client &#40;ODBC&#41;</span></span>](sql-server-native-client-odbc.md)  
  
  
