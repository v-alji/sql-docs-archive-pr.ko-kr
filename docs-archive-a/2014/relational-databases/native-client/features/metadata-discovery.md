---
title: 메타데이터 검색 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: ec3c0f4f-f838-43ce-85f2-cf2761e2aac5
author: rothja
ms.author: jroth
ms.openlocfilehash: 571df9f21ab46a53c8aba7907039ce02afd6ad05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730587"
---
# <a name="metadata-discovery"></a><span data-ttu-id="902a1-102">메타데이터 검색</span><span class="sxs-lookup"><span data-stu-id="902a1-102">Metadata Discovery</span></span>
  <span data-ttu-id="902a1-103">의 메타 데이터 검색 개선 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 기능을 사용 하면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 응용 프로그램에서 쿼리 실행 시 반환 된 열 또는 매개 변수 메타 데이터가 쿼리를 실행 하기 전에 지정한 메타 데이터 형식과 동일 하거나 호환 되는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="902a1-103">The metadata discovery improvement in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] allows [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client applications to ensure that column or parameter metadata returned from the execution of a query is identical to or compatible with the metadata format you specified before you executed the query.</span></span> <span data-ttu-id="902a1-104">쿼리 실행 후 반환된 메타데이터가 쿼리를 실행하기 전에 지정한 메타데이터 형식과 호환되지 않는 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="902a1-104">You will receive an error if the metadata returned after query execution is not compatible with the metadata format you specified before query execution.</span></span>  
  
 <span data-ttu-id="902a1-105">bcp 및 ODBC 함수와 IBCPSession 및 IBCPSession2 인터페이스에서는 이제 쿼리 출력 작업에서 메타데이터를 검색하지 않도록 지연된 읽기(지연된 메타데이터 검색)을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="902a1-105">In bcp and ODBC functions, and IBCPSession and IBCPSession2 interfaces, you can now specify a delayed read (delayed metadata discovery) to avoid metadata discovery for query out operations.</span></span> <span data-ttu-id="902a1-106">이로 인해 성능이 향상되고 메타데이터 검색 오류가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="902a1-106">This improves performance and eliminates metadata discovery failures.</span></span>  
  
 <span data-ttu-id="902a1-107">에서 Native Client를 사용 하 여 응용 프로그램을 개발 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 하지만 이전 버전의 서버에 연결 하는 경우 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 메타 데이터 검색 기능은 서버 버전에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="902a1-107">If you develop an application using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] but connect to a server version earlier than [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], metadata discovery functionality will correspond to the version of the server.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="902a1-108">설명</span><span class="sxs-lookup"><span data-stu-id="902a1-108">Remarks</span></span>  
 <span data-ttu-id="902a1-109">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]에서 다음 bcp 함수의 기능이 개선되어 메타데이터 검색 기능이 향상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="902a1-109">The following bcp functions have been enhanced in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] to provide improved metadata discovery:</span></span>  
  
-   [<span data-ttu-id="902a1-110">bcp_columns</span><span class="sxs-lookup"><span data-stu-id="902a1-110">bcp_columns</span></span>](../../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)  
  
-   [<span data-ttu-id="902a1-111">bcp_control</span><span class="sxs-lookup"><span data-stu-id="902a1-111">bcp_control</span></span>](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)  
  
-   [<span data-ttu-id="902a1-112">bcp_getcolfmt</span><span class="sxs-lookup"><span data-stu-id="902a1-112">bcp_getcolfmt</span></span>](../../native-client-odbc-extensions-bulk-copy-functions/bcp-getcolfmt.md)  
  
-   [<span data-ttu-id="902a1-113">bcp_readfmt</span><span class="sxs-lookup"><span data-stu-id="902a1-113">bcp_readfmt</span></span>](../../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)  
  
-   [<span data-ttu-id="902a1-114">bcp_setcolfmt</span><span class="sxs-lookup"><span data-stu-id="902a1-114">bcp_setcolfmt</span></span>](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md)  
  
 <span data-ttu-id="902a1-115">[Bcp_setbulkmode](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md)를 사용 하 여 메타 데이터 형식을 지정 하는 경우 성능 향상도 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="902a1-115">You will also see a performance improvement when specifying metadata format using [bcp_setbulkmode](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md).</span></span>  
  
 <span data-ttu-id="902a1-116">[bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) 에는 bcp_readfmt의 동작을 제어 하는 새로운 *eoption* 가 `BCPDELAYREADFMT` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="902a1-116">[bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) has a new *eOption* to control the behavior of bcp_readfmt: `BCPDELAYREADFMT`.</span></span>  
  
 <span data-ttu-id="902a1-117">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]에서 다음 ODBC 함수의 기능이 개선되어 메타데이터 검색 기능이 향상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="902a1-117">The following ODBC functions have been enhanced in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] to provide improved metadata discovery:</span></span>  
  
-   [<span data-ttu-id="902a1-118">SQLNumResultCols</span><span class="sxs-lookup"><span data-stu-id="902a1-118">SQLNumResultCols</span></span>](../../native-client-odbc-api/sqlnumresultcols.md)  
  
-   [<span data-ttu-id="902a1-119">SQLDescribeCol</span><span class="sxs-lookup"><span data-stu-id="902a1-119">SQLDescribeCol</span></span>](../../native-client-odbc-api/sqldescribecol.md)  
  
-   [<span data-ttu-id="902a1-120">SQLNumParams</span><span class="sxs-lookup"><span data-stu-id="902a1-120">SQLNumParams</span></span>](../../native-client-odbc-api/sqlnumparams.md)  
  
-   [<span data-ttu-id="902a1-121">SQLDescribeParam</span><span class="sxs-lookup"><span data-stu-id="902a1-121">SQLDescribeParam</span></span>](../../native-client-odbc-api/sqldescribeparam.md)  
  
 <span data-ttu-id="902a1-122">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]에서 다음 OLE DB 멤버 함수의 기능이 개선되어 메타데이터 검색 기능이 향상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="902a1-122">The following OLE DB member functions have been enhanced in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] to provide improved metadata discovery:</span></span>  
  
-   <span data-ttu-id="902a1-123">IColumnsInfo::GetColumnInfo</span><span class="sxs-lookup"><span data-stu-id="902a1-123">IColumnsInfo::GetColumnInfo</span></span>  
  
-   <span data-ttu-id="902a1-124">IColumnsRowset::GetColumnsRowset</span><span class="sxs-lookup"><span data-stu-id="902a1-124">IColumnsRowset::GetColumnsRowset</span></span>  
  
-   <span data-ttu-id="902a1-125">ICommandWithParameters::GetParameterInfo(자세한 내용은 [ICommandWithParameters](../../native-client-ole-db-interfaces/icommandwithparameters.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="902a1-125">ICommandWithParameters::GetParameterInfo (see [ICommandWithParameters](../../native-client-ole-db-interfaces/icommandwithparameters.md) for more information)</span></span>  
  
 <span data-ttu-id="902a1-126">또한 IBCPSession::BCPSetBulkMode를 사용하여 메타데이터 형식을 지정하는 경우 향상된 성능을 경험할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="902a1-126">You will also see a performance improvement when specifying metadata format using IBCPSession::BCPSetBulkMode</span></span>  
  
 <span data-ttu-id="902a1-127">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 다음과 같은 두 개의 저장 프로시저가 추가되어 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client에서 메타데이터 검색 기능이 향상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="902a1-127">The improved metadata discovery in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client is possible because of the addition of two stored procedures in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]:</span></span>  
  
-   <span data-ttu-id="902a1-128">sp_describe_first_result_set</span><span class="sxs-lookup"><span data-stu-id="902a1-128">sp_describe_first_result_set</span></span>  
  
-   <span data-ttu-id="902a1-129">sp_describe_undeclared_parameters</span><span class="sxs-lookup"><span data-stu-id="902a1-129">sp_describe_undeclared_parameters</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="902a1-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="902a1-130">See Also</span></span>  
 [<span data-ttu-id="902a1-131">SQL Server Native Client 기능</span><span class="sxs-lookup"><span data-stu-id="902a1-131">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
