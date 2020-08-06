---
title: ODBC API 구현 세부 정보 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, functions
- SQL Server Native Client ODBC driver, SQL Server-specific behaviors
- ODBC, SQL Server-specific behaviors
- functions [ODBC]
ms.assetid: dca92489-f179-4b1f-997c-adcc46aa17a3
author: rothja
ms.author: jroth
ms.openlocfilehash: 1af47924090e7cb1df8ed7907ba0f793b9df2420
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740928"
---
# <a name="odbc-api-implementation-details"></a><span data-ttu-id="c94bf-102">ODBC API 구현 정보</span><span class="sxs-lookup"><span data-stu-id="c94bf-102">ODBC API Implementation Details</span></span>
  <span data-ttu-id="c94bf-103">이 섹션에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버와 함께 사용할 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관련 동작을 수행하는 ODBC 함수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c94bf-103">This section documents the ODBC functions that exhibit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific behaviors when used with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="c94bf-104">여기에서 모든 ODBC 함수를 설명하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="c94bf-104">Not all ODBC functions are documented here.</span></span> <span data-ttu-id="c94bf-105">개별 항목에서는 ODBC 함수의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관련 문제에 대해서만 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c94bf-105">The individual topics only discuss the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific issues for an ODBC function.</span></span> <span data-ttu-id="c94bf-106">즉 ODBC 함수에 대한 완전한 참조 자료가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="c94bf-106">They are not a complete reference for the ODBC functions.</span></span>  
  
 <span data-ttu-id="c94bf-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 ODBC 3.51 사양을 준수하며, 사용자가 Windows 7 SDK를 사용하고 있는 경우 ODBC 3.8 사양을 준수합니다.</span><span class="sxs-lookup"><span data-stu-id="c94bf-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver complies with the ODBC 3.51 specification and, if you are using the Windows 7 SDK, with the ODBC 3.8 specification.</span></span> <span data-ttu-id="c94bf-108">포괄적인 ODBC 참조는 온라인에서 [Odbc 프로그래머 참조](https://go.microsoft.com/fwlink/?LinkId=45250) 를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="c94bf-108">For a comprehensive ODBC reference, view the [ODBC Programmer's Reference](https://go.microsoft.com/fwlink/?LinkId=45250) online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c94bf-109">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="c94bf-109">In This Section</span></span>  
  
-   [<span data-ttu-id="c94bf-110">SQLBindCol</span><span class="sxs-lookup"><span data-stu-id="c94bf-110">SQLBindCol</span></span>](sqlbindcol.md)  
  
-   [<span data-ttu-id="c94bf-111">SQLBindParameter</span><span class="sxs-lookup"><span data-stu-id="c94bf-111">SQLBindParameter</span></span>](sqlbindparameter.md)  
  
-   [<span data-ttu-id="c94bf-112">SQLBrowseConnect</span><span class="sxs-lookup"><span data-stu-id="c94bf-112">SQLBrowseConnect</span></span>](sqlbrowseconnect.md)  
  
-   [<span data-ttu-id="c94bf-113">SQLCancel</span><span class="sxs-lookup"><span data-stu-id="c94bf-113">SQLCancel</span></span>](sqlcancel.md)  
  
-   [<span data-ttu-id="c94bf-114">SQLCloseCursor</span><span class="sxs-lookup"><span data-stu-id="c94bf-114">SQLCloseCursor</span></span>](sqlclosecursor.md)  
  
-   [<span data-ttu-id="c94bf-115">SQLColAttribute</span><span class="sxs-lookup"><span data-stu-id="c94bf-115">SQLColAttribute</span></span>](sqlcolattribute.md)  
  
-   [<span data-ttu-id="c94bf-116">SQLColumnPrivileges</span><span class="sxs-lookup"><span data-stu-id="c94bf-116">SQLColumnPrivileges</span></span>](sqlcolumnprivileges.md)  
  
-   [<span data-ttu-id="c94bf-117">SQLColumns</span><span class="sxs-lookup"><span data-stu-id="c94bf-117">SQLColumns</span></span>](sqlcolumns.md)  
  
-   [<span data-ttu-id="c94bf-118">SQLConfigDataSource</span><span class="sxs-lookup"><span data-stu-id="c94bf-118">SQLConfigDataSource</span></span>](sqlconfigdatasource.md)  
  
-   [<span data-ttu-id="c94bf-119">SQLConnect</span><span class="sxs-lookup"><span data-stu-id="c94bf-119">SQLConnect</span></span>](sqlconnect.md)  
  
-   [<span data-ttu-id="c94bf-120">SQLDescribeCol</span><span class="sxs-lookup"><span data-stu-id="c94bf-120">SQLDescribeCol</span></span>](sqldescribecol.md)  
  
-   [<span data-ttu-id="c94bf-121">SQLDescribeParam</span><span class="sxs-lookup"><span data-stu-id="c94bf-121">SQLDescribeParam</span></span>](sqldescribeparam.md)  
  
-   [<span data-ttu-id="c94bf-122">SQLDriverConnect</span><span class="sxs-lookup"><span data-stu-id="c94bf-122">SQLDriverConnect</span></span>](sqldriverconnect.md)  
  
-   [<span data-ttu-id="c94bf-123">SQLDrivers</span><span class="sxs-lookup"><span data-stu-id="c94bf-123">SQLDrivers</span></span>](sqldrivers.md)  
  
-   [<span data-ttu-id="c94bf-124">SQLEndTran</span><span class="sxs-lookup"><span data-stu-id="c94bf-124">SQLEndTran</span></span>](sqlendtran.md)  
  
-   [<span data-ttu-id="c94bf-125">SQLExecDirect</span><span class="sxs-lookup"><span data-stu-id="c94bf-125">SQLExecDirect</span></span>](sqlexecdirect.md)  
  
-   [<span data-ttu-id="c94bf-126">SQLExecute</span><span class="sxs-lookup"><span data-stu-id="c94bf-126">SQLExecute</span></span>](sqlexecute.md)  
  
-   [<span data-ttu-id="c94bf-127">SQLFetch</span><span class="sxs-lookup"><span data-stu-id="c94bf-127">SQLFetch</span></span>](sqlfetch.md)  
  
-   [<span data-ttu-id="c94bf-128">SQLFetchScroll</span><span class="sxs-lookup"><span data-stu-id="c94bf-128">SQLFetchScroll</span></span>](sqlfetchscroll.md)  
  
-   [<span data-ttu-id="c94bf-129">SQLForeignKeys</span><span class="sxs-lookup"><span data-stu-id="c94bf-129">SQLForeignKeys</span></span>](sqlforeignkeys.md)  
  
-   [<span data-ttu-id="c94bf-130">SQLFreeHandle</span><span class="sxs-lookup"><span data-stu-id="c94bf-130">SQLFreeHandle</span></span>](sqlfreehandle.md)  
  
-   [<span data-ttu-id="c94bf-131">SQLFreeStmt</span><span class="sxs-lookup"><span data-stu-id="c94bf-131">SQLFreeStmt</span></span>](sqlfreestmt.md)  
  
-   [<span data-ttu-id="c94bf-132">SQLGetConnectAttr</span><span class="sxs-lookup"><span data-stu-id="c94bf-132">SQLGetConnectAttr</span></span>](sqlgetconnectattr.md)  
  
-   [<span data-ttu-id="c94bf-133">SQLGetCursorName</span><span class="sxs-lookup"><span data-stu-id="c94bf-133">SQLGetCursorName</span></span>](sqlgetcursorname.md)  
  
-   [<span data-ttu-id="c94bf-134">SQLGetData</span><span class="sxs-lookup"><span data-stu-id="c94bf-134">SQLGetData</span></span>](sqlgetdata.md)  
  
-   [<span data-ttu-id="c94bf-135">SQLGetDescField</span><span class="sxs-lookup"><span data-stu-id="c94bf-135">SQLGetDescField</span></span>](sqlgetdescfield.md)  
  
-   [<span data-ttu-id="c94bf-136">SQLGetDescRec</span><span class="sxs-lookup"><span data-stu-id="c94bf-136">SQLGetDescRec</span></span>](sqlgetdescrec.md)  
  
-   [<span data-ttu-id="c94bf-137">SQLGetDiagField</span><span class="sxs-lookup"><span data-stu-id="c94bf-137">SQLGetDiagField</span></span>](sqlgetdiagfield.md)  
  
-   [<span data-ttu-id="c94bf-138">SQLGetFunctions</span><span class="sxs-lookup"><span data-stu-id="c94bf-138">SQLGetFunctions</span></span>](sqlgetfunctions.md)  
  
-   [<span data-ttu-id="c94bf-139">SQLGetInfo</span><span class="sxs-lookup"><span data-stu-id="c94bf-139">SQLGetInfo</span></span>](sqlgetinfo.md)  
  
-   [<span data-ttu-id="c94bf-140">SQLGetStmtAttr</span><span class="sxs-lookup"><span data-stu-id="c94bf-140">SQLGetStmtAttr</span></span>](sqlgetstmtattr.md)  
  
-   [<span data-ttu-id="c94bf-141">SQLGetTypeInfo</span><span class="sxs-lookup"><span data-stu-id="c94bf-141">SQLGetTypeInfo</span></span>](sqlgettypeinfo.md)  
  
-   [<span data-ttu-id="c94bf-142">SQLMoreResults</span><span class="sxs-lookup"><span data-stu-id="c94bf-142">SQLMoreResults</span></span>](sqlmoreresults.md)  
  
-   [<span data-ttu-id="c94bf-143">SQLNativeSql</span><span class="sxs-lookup"><span data-stu-id="c94bf-143">SQLNativeSql</span></span>](sqlnativesql.md)  
  
-   [<span data-ttu-id="c94bf-144">SQLNumParams</span><span class="sxs-lookup"><span data-stu-id="c94bf-144">SQLNumParams</span></span>](sqlnumparams.md)  
  
-   [<span data-ttu-id="c94bf-145">SQLNumResultCols</span><span class="sxs-lookup"><span data-stu-id="c94bf-145">SQLNumResultCols</span></span>](sqlnumresultcols.md)  
  
-   [<span data-ttu-id="c94bf-146">SQLParamData</span><span class="sxs-lookup"><span data-stu-id="c94bf-146">SQLParamData</span></span>](sqlparamdata.md)  
  
-   [<span data-ttu-id="c94bf-147">SQLPrimaryKeys</span><span class="sxs-lookup"><span data-stu-id="c94bf-147">SQLPrimaryKeys</span></span>](sqlprimarykeys.md)  
  
-   [<span data-ttu-id="c94bf-148">SQLProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="c94bf-148">SQLProcedureColumns</span></span>](sqlprocedurecolumns.md)  
  
-   [<span data-ttu-id="c94bf-149">SQLProcedures</span><span class="sxs-lookup"><span data-stu-id="c94bf-149">SQLProcedures</span></span>](sqlprocedures.md)  
  
-   [<span data-ttu-id="c94bf-150">SQLPutData</span><span class="sxs-lookup"><span data-stu-id="c94bf-150">SQLPutData</span></span>](sqlputdata.md)  
  
-   [<span data-ttu-id="c94bf-151">SQLRowCount</span><span class="sxs-lookup"><span data-stu-id="c94bf-151">SQLRowCount</span></span>](sqlrowcount.md)  
  
-   [<span data-ttu-id="c94bf-152">SQLSetConnectAttr</span><span class="sxs-lookup"><span data-stu-id="c94bf-152">SQLSetConnectAttr</span></span>](sqlsetconnectattr.md)  
  
-   [<span data-ttu-id="c94bf-153">SQLSetDescField</span><span class="sxs-lookup"><span data-stu-id="c94bf-153">SQLSetDescField</span></span>](sqlsetdescfield.md)  
  
-   [<span data-ttu-id="c94bf-154">SQLSetDescRec</span><span class="sxs-lookup"><span data-stu-id="c94bf-154">SQLSetDescRec</span></span>](sqlsetdescrec.md)  
  
-   [<span data-ttu-id="c94bf-155">SQLSetEnvAttr</span><span class="sxs-lookup"><span data-stu-id="c94bf-155">SQLSetEnvAttr</span></span>](sqlsetenvattr.md)  
  
-   [<span data-ttu-id="c94bf-156">SQLSetStmtAttr</span><span class="sxs-lookup"><span data-stu-id="c94bf-156">SQLSetStmtAttr</span></span>](sqlsetstmtattr.md)  
  
-   [<span data-ttu-id="c94bf-157">SQLSpecialColumns</span><span class="sxs-lookup"><span data-stu-id="c94bf-157">SQLSpecialColumns</span></span>](sqlspecialcolumns.md)  
  
-   [<span data-ttu-id="c94bf-158">SQLStatistics</span><span class="sxs-lookup"><span data-stu-id="c94bf-158">SQLStatistics</span></span>](../statistics/statistics.md)  
  
-   [<span data-ttu-id="c94bf-159">SQLTablePrivileges</span><span class="sxs-lookup"><span data-stu-id="c94bf-159">SQLTablePrivileges</span></span>](sqltableprivileges.md)  
  
-   [<span data-ttu-id="c94bf-160">SQLTables</span><span class="sxs-lookup"><span data-stu-id="c94bf-160">SQLTables</span></span>](sqltables.md)  
  
## <a name="see-also"></a><span data-ttu-id="c94bf-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c94bf-161">See Also</span></span>  
 <span data-ttu-id="c94bf-162">[ODBC&#41; 참조 &#40;SQL Server Native Client](../../database-engine/dev-guide/sql-server-native-client-odbc-reference.md) </span><span class="sxs-lookup"><span data-stu-id="c94bf-162">[SQL Server Native Client &#40;ODBC&#41; Reference](../../database-engine/dev-guide/sql-server-native-client-odbc-reference.md) </span></span>  
 [<span data-ttu-id="c94bf-163">SQL Server Native Client를 사용하여 애플리케이션 빌드</span><span class="sxs-lookup"><span data-stu-id="c94bf-163">Building Applications with SQL Server Native Client</span></span>](../native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
