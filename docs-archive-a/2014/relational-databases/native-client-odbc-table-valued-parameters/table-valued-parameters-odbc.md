---
title: 테이블 반환 매개 변수 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC)
- ODBC, table-valued parameters
ms.assetid: ef06cd13-18e2-4c65-8ede-c3955d820e54
author: rothja
ms.author: jroth
ms.openlocfilehash: fedfd63f7cbafd68d39aeb62dd29c046df8ab100
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646391"
---
# <a name="table-valued-parameters-odbc"></a><span data-ttu-id="05f43-102">테이블 반환 매개 변수(ODBC)</span><span class="sxs-lookup"><span data-stu-id="05f43-102">Table-Valued Parameters (ODBC)</span></span>
  <span data-ttu-id="05f43-103">ODBC의 테이블 반환 매개 변수 지원을 통해 한 번의 호출로 여러 행을 서버로 보냄으로써 클라이언트 애플리케이션에서 서버로 매개 변수가 있는 데이터를 보다 효율적으로 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-103">ODBC support for table-valued parameters lets a client application send parameterized data to the server more efficiently, by sending multiple rows to the server with one call.</span></span>  
  
 <span data-ttu-id="05f43-104">서버에 있는 테이블 반환 매개 변수에 대 한 자세한 내용은 [테이블 반환 매개 변수 &#40;사용 하 여 데이터베이스 엔진&#41;](../tables/use-table-valued-parameters-database-engine.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="05f43-104">For information about table-valued parameters on the server, see [Use Table-Valued Parameters &#40;Database Engine&#41;](../tables/use-table-valued-parameters-database-engine.md).</span></span>  
  
 <span data-ttu-id="05f43-105">ODBC에서 다음 두 가지 방법으로 테이블 반환 매개 변수를 서버로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-105">In ODBC, there are two ways that you can send table-valued parameters to the server:</span></span>  
  
-   <span data-ttu-id="05f43-106">SQLExecDirect 또는 SQLExecute를 호출할 때 모든 테이블 반환 매개 변수 데이터는 메모리에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-106">All the table-valued parameter data can be in memory at the time SQLExecDirect or SQLExecute is called.</span></span> <span data-ttu-id="05f43-107">테이블 반환에 행이 여러 개 있으면 이 데이터가 배열로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-107">This data is stored in arrays if there are multiple rows in the table-value.</span></span>  
  
-   <span data-ttu-id="05f43-108">SQLExecDirect 또는 SQLExecute를 호출 하는 경우 응용 프로그램은 테이블 반환 매개 변수에 대해 실행 시 데이터를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-108">An application can specify data-at-execution for a table-valued parameter when SQLExecDirect or SQLExecute is called.</span></span> <span data-ttu-id="05f43-109">이 경우 테이블 반환의 데이터 행을 일괄 처리로 제공하거나, 한 번에 하나씩 제공해 메모리 사용량을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-109">In this case, rows of data for the table-value can be provided in batches, or one at a time to reduce memory requirements.</span></span>  
  
 <span data-ttu-id="05f43-110">첫 번째 옵션을 사용하면 저장 프로시저가 비즈니스 논리를 더 많이 캡슐화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-110">The first option enables stored procedures to encapsulate more business logic.</span></span> <span data-ttu-id="05f43-111">예를 들어 주문 항목이 테이블 반환 매개 변수로 전달된 경우 단일 저장 프로시저가 전체 주문 입력 트랜잭션을 캡슐화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-111">For example, a single stored procedure could encapsulate a whole order entry transaction when the order items are passed as a table-valued parameter.</span></span> <span data-ttu-id="05f43-112">이 옵션은 서버로의 왕복이 한 번만 필요하기 때문에 매우 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-112">This option is very efficient, because only a single round trip to the server is required.</span></span> <span data-ttu-id="05f43-113">또는 다른 프로시저를 사용하여 주문 헤더와 주문 항목을 각각 별도로 처리할 수도 있습니다. 이 경우 코드가 더 많이 필요하고 클라이언트와 서버 간의 계약이 복잡해집니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-113">Alternatively, you could use different procedures to handle the order header and order items separately, which would require more code and a more complex contract between the client and server.</span></span>  
  
 <span data-ttu-id="05f43-114">두 번째 방법은 매우 많은 양의 데이터로 대량 작업을 수행할 때 효율적인 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-114">The second method provides an efficient mechanism for bulk operations with very large amounts of data.</span></span> <span data-ttu-id="05f43-115">이 방법을 사용하면 애플리케이션에서 먼저 메모리에 데이터를 모두 버퍼링하지 않고도 서버로 데이터 행을 스트리밍할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-115">This enables an application to stream rows of data to the server without having to buffer them all in memory first.</span></span>  
  
 <span data-ttu-id="05f43-116">테이블 변수를 만들 때 제약 조건과 기본 키를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-116">You can create constraints and primary keys when you create the table variable.</span></span> <span data-ttu-id="05f43-117">제약 조건은 테이블의 데이터가 특정 요구 사항을 충족하는지 확인하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-117">Constraints are a good way to ensure that the data in a table meets specific requirements.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="05f43-118">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="05f43-118">In This Section</span></span>  
 [<span data-ttu-id="05f43-119">ODBC 테이블 반환 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="05f43-119">Uses of ODBC Table-Valued Parameters</span></span>](uses-of-odbc-table-valued-parameters.md)  
 <span data-ttu-id="05f43-120">테이블 반환 매개 변수 및 ODBC의 기본 사용자 시나리오를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-120">Describes the primary user scenarios for table-valued parameters and ODBC.</span></span>  
  
 [<span data-ttu-id="05f43-121">테이블 반환 매개 변수의 ODBC SQL 유형</span><span class="sxs-lookup"><span data-stu-id="05f43-121">ODBC SQL Type for Table-Valued Parameters</span></span>](odbc-sql-type-for-table-valued-parameters.md)  
 <span data-ttu-id="05f43-122">SQL_SS_TABLE 형식에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-122">Describes the SQL_SS_TABLE type.</span></span> <span data-ttu-id="05f43-123">테이블 반환 매개 변수를 지원하는 새로운 ODBC SQL 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-123">This is a new ODBC SQL type that supports table-valued parameters.</span></span>  
  
 [<span data-ttu-id="05f43-124">테이블 반환 매개 변수 설명자 필드</span><span class="sxs-lookup"><span data-stu-id="05f43-124">Table-Valued Parameter Descriptor Fields</span></span>](table-valued-parameter-descriptor-fields.md)  
 <span data-ttu-id="05f43-125">테이블 반환 매개 변수를 지원하는 설명자 필드에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-125">Describes descriptor fields that support table-valued parameters.</span></span>  
  
 [<span data-ttu-id="05f43-126">테이블 반환 매개 변수 구성 열의 설명자 필드</span><span class="sxs-lookup"><span data-stu-id="05f43-126">Descriptor Fields for Table-Valued Parameter Constituent Columns</span></span>](descriptor-fields-for-table-valued-parameter-constituent-columns.md)  
 <span data-ttu-id="05f43-127">테이블 반환 매개 변수에 대한 의미를 갖는 설명자 필드에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-127">Describes descriptor fields that have meaning for table-valued parameters.</span></span>  
  
 [<span data-ttu-id="05f43-128">테이블 반환 매개 변수 진단 레코드 필드</span><span class="sxs-lookup"><span data-stu-id="05f43-128">Table-Valued Parameter Diagnostic Record Fields</span></span>](table-valued-parameter-diagnostic-record-fields.md)  
 <span data-ttu-id="05f43-129">테이블 반환 매개 변수를 지원하기 위해 진단 레코드에 추가된 두 진단 필드에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-129">Describes two diagnostic fields that have been added to diagnostic records to support table-valued parameters.</span></span>  
  
 [<span data-ttu-id="05f43-130">테이블 반환 매개 변수에 영향을 주는 문 특성</span><span class="sxs-lookup"><span data-stu-id="05f43-130">Statement Attributes that Affect Table-Valued Parameters</span></span>](statement-attributes-that-affect-table-valued-parameters.md)  
 <span data-ttu-id="05f43-131">테이블 반환 매개 변수 열에 번호를 지정할 수 있도록 하는 새로운 설명자 헤더 필드에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-131">Describes a new descriptor header field that enables table-valued parameters columns to be addressed.</span></span>  
  
 [<span data-ttu-id="05f43-132">테이블 반환 매개 변수 및 열 값에 대한 바인딩 및 데이터 전송</span><span class="sxs-lookup"><span data-stu-id="05f43-132">Binding and Data Transfer of Table-Valued Parameters and Column Values</span></span>](binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)  
 <span data-ttu-id="05f43-133">테이블 반환 매개 변수를 서버로 전달하는 방법과 매개 변수 바인딩에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-133">Describes parameter binding and how to pass a table-valued parameter to the server.</span></span>  
  
 [<span data-ttu-id="05f43-134">준비된 문의 테이블 반환 매개 변수 메타데이터</span><span class="sxs-lookup"><span data-stu-id="05f43-134">Table-Valued Parameter Metadata for Prepared Statements</span></span>](table-valued-parameter-metadata-for-prepared-statements.md)  
 <span data-ttu-id="05f43-135">애플리케이션에서 준비된 프로시저 호출의 메타데이터를 가져오는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-135">Describes how an application can obtain metadata for a prepared procedure call.</span></span>  
  
 [<span data-ttu-id="05f43-136">추가 테이블 반환 매개 변수 메타데이터</span><span class="sxs-lookup"><span data-stu-id="05f43-136">Additional Table-Valued Parameter Metadata</span></span>](additional-table-valued-parameter-metadata.md)  
 <span data-ttu-id="05f43-137">SQLProcedureColumns, SQLTables 및 Sqltables를 사용 하 여 테이블 반환 매개 변수의 메타 데이터를 검색 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-137">Describes how to use SQLProcedureColumns, SQLTables, and SQLColumns to retrieve metadata for a table-valued parameter.</span></span>  
  
 [<span data-ttu-id="05f43-138">테이블 반환 매개 변수 데이터 변환과 기타 오류 및 경고</span><span class="sxs-lookup"><span data-stu-id="05f43-138">Table-Valued Parameter Data Conversion and Other Errors and Warnings</span></span>](table-valued-parameter-data-conversion-and-other-errors-and-warnings.md)  
 <span data-ttu-id="05f43-139">테이블 반환 매개 변수 열 값에서 발생한 오류를 처리하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-139">Describes how to process errors on table-valued parameter column values.</span></span>  
  
 [<span data-ttu-id="05f43-140">버전 간 호환성</span><span class="sxs-lookup"><span data-stu-id="05f43-140">Cross-Version Compatibility</span></span>](cross-version-compatibility.md)  
 <span data-ttu-id="05f43-141">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]보다 이전 버전의 클라이언트나 서버에서 테이블 반환 매개 변수를 사용할 때 발생할 수 있는 충돌에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-141">Describes conflicts that can occur when table-valued parameters are used by a client or server of a version earlier than [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
 [<span data-ttu-id="05f43-142">ODBC 테이블 반환 매개 변수 API 요약</span><span class="sxs-lookup"><span data-stu-id="05f43-142">ODBC Table-Valued Parameter API Summary</span></span>](odbc-table-valued-parameter-api-summary.md)  
 <span data-ttu-id="05f43-143">테이블 반환 매개 변수를 지원하는 ODBC 함수 목록을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-143">Lists the ODBC functions that support table-valued parameters.</span></span>  
  
 [<span data-ttu-id="05f43-144">ODBC 테이블 반환 매개 변수 프로그래밍 예제</span><span class="sxs-lookup"><span data-stu-id="05f43-144">ODBC Table-Valued Parameter Programming Examples</span></span>](../../database-engine/dev-guide/odbc-table-valued-parameter-programming-examples.md)  
 <span data-ttu-id="05f43-145">일반적인 태스크를 수행하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="05f43-145">Describes how to perform common tasks.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05f43-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="05f43-146">See Also</span></span>  
 <span data-ttu-id="05f43-147">[ODBC&#41;SQL Server Native Client &#40;](../native-client/odbc/sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="05f43-147">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span></span>  
 [<span data-ttu-id="05f43-148">테이블 반환 매개 변수 SQL Server Native Client &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="05f43-148">Table-Valued Parameters &#40;SQL Server Native Client&#41;</span></span>](../native-client/features/table-valued-parameters-sql-server-native-client.md)  
  
  
