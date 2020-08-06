---
title: OLE DB 원본 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbsource.f1
helpviewer_keywords:
- sources [Integration Services], OLE DB
- OLE DB source [Integration Services]
ms.assetid: f87cc5f6-b078-40f3-9d87-7a65e13e4c86
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ce0d2a95639dc31ee8cf4dd9cdaca6844ad4a1d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648475"
---
# <a name="ole-db-source"></a><span data-ttu-id="34caf-102">OLE DB 원본</span><span class="sxs-lookup"><span data-stu-id="34caf-102">OLE DB Source</span></span>
  <span data-ttu-id="34caf-103">OLE DB 원본은 데이터베이스 테이블, 뷰 또는 SQL 명령을 사용하여 다양한 OLE DB 호환 관계형 데이터베이스에서 데이터를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-103">The OLE DB source extracts data from a variety of OLE DB-compliant relational databases by using a database table, a view, or an SQL command.</span></span> <span data-ttu-id="34caf-104">예를 들어 OLE DB 원본은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스의 테이블에서 데이터를 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-104">For example, the OLE DB source can extract data from tables in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
 <span data-ttu-id="34caf-105">OLE DB 원본은 데이터 추출을 위한 4가지 데이터 액세스 모델을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-105">The OLE DB source provides four different data access modes for extracting data:</span></span>  
  
-   <span data-ttu-id="34caf-106">테이블 또는 뷰</span><span class="sxs-lookup"><span data-stu-id="34caf-106">A table or view.</span></span>  
  
-   <span data-ttu-id="34caf-107">변수에 지정된 테이블 또는 뷰</span><span class="sxs-lookup"><span data-stu-id="34caf-107">A table or view specified in a variable.</span></span>  
  
-   <span data-ttu-id="34caf-108">SQL 문의 결과</span><span class="sxs-lookup"><span data-stu-id="34caf-108">The results of an SQL statement.</span></span> <span data-ttu-id="34caf-109">쿼리는 매개 변수가 있는 쿼리일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-109">The query can be a parameterized query.</span></span>  
  
-   <span data-ttu-id="34caf-110">변수에 저장된 SQL 문의 결과</span><span class="sxs-lookup"><span data-stu-id="34caf-110">The results of an SQL statement stored in a variable.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="34caf-111">SQL 문을 사용하여 임시 테이블의 결과를 반환하는 저장 프로시저를 호출하는 경우 WITH RESULT SETS 옵션을 사용하여 결과 집합의 메타데이터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-111">When you use an SQL statement to invoke a stored procedure that returns results from a temporary table, use the WITH RESULT SETS option to define metadata for the result set.</span></span>  
  
 <span data-ttu-id="34caf-112">매개 변수가 있는 쿼리를 사용하는 경우 변수를 매개 변수에 매핑하여 SQL 문의 개별 매개 변수에 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-112">If you use a parameterized query, you can map variables to parameters to specify the values for individual parameters in the SQL statements.</span></span>  
  
 <span data-ttu-id="34caf-113">이 원본은 OLE DB 연결 관리자를 사용하여 데이터 원본에 연결하며 이 연결 관리자는 사용할 OLE DB Provider를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-113">This source uses an OLE DB connection manager to connect to a data source, and the connection manager specifies the OLE DB provider to use.</span></span> <span data-ttu-id="34caf-114">자세한 내용은 [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="34caf-114">For more information, see [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="34caf-115">또한 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트는 OLE DB 연결 관리자를 만들 수 있는 데이터 원본 개체를 제공하여 OLE DB 원본에서 데이터 원본과 데이터 원본 뷰를 사용할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-115">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project also provides the data source object from which you can create an OLE DB connection manager, making data sources and data source views available to the OLE DB source.</span></span>  
  
 <span data-ttu-id="34caf-116">OLE DB Provider에 따라 OLE DB 원본에는 다음 몇 가지 제한이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-116">Depending on the OLE DB provider, some limitations apply to the OLE DB source:</span></span>  
  
-   <span data-ttu-id="34caf-117">Oracle용 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider는 Oracle 데이터 형식 BLOB, CLOB, NCLOB, BFILE 또는 UROWID를 지원하지 않으며 OLE DB 원본은 이러한 데이터 형식의 열이 포함된 테이블에서 데이터를 추출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-117">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB provider for Oracle does not support the Oracle data types BLOB, CLOB, NCLOB, BFILE, OR UROWID, and the OLE DB source cannot extract data from tables that contain columns with these data types.</span></span>  
  
-   <span data-ttu-id="34caf-118">IBM OLE DB DB2 공급자와 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB DB2 공급자는 저장 프로시저를 호출하는 SQL 명령의 사용을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-118">The IBM OLE DB DB2 provider and [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB DB2 provider do not support using an SQL command that calls a stored procedure.</span></span> <span data-ttu-id="34caf-119">이러한 종류의 명령을 사용하면 OLE DB 원본에서 열 메타데이터를 만들 수 없으므로 데이터 흐름에서 OLE DB 원본을 따르는 데이터 흐름 구성 요소가 열 데이터를 사용할 수 없으며 데이터 흐름의 실행이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-119">When this kind of command is used, the OLE DB source cannot create the column metadata and, as a result, the data flow components that follow the OLE DB source in the data flow have no column data available and the execution of the data flow fails.</span></span>  
  
 <span data-ttu-id="34caf-120">OLE DB 원본에는 하나의 일반 출력 및 하나의 오류 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-120">The OLE DB source has one regular output and one error output.</span></span>  
  
## <a name="using-parameterized-sql-statements"></a><span data-ttu-id="34caf-121">매개 변수가 있는 SQL 문 사용</span><span class="sxs-lookup"><span data-stu-id="34caf-121">Using Parameterized SQL Statements</span></span>  
 <span data-ttu-id="34caf-122">OLE DB 원본은 SQL 문을 사용하여 데이터를 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-122">The OLE DB source can use an SQL statement to extract data.</span></span> <span data-ttu-id="34caf-123">이 문은 SELECT 또는 EXEC 문일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-123">The statement can be a SELECT or an EXEC statement.</span></span>  
  
 <span data-ttu-id="34caf-124">OLE DB 원본은 OLE DB 연결 관리자를 사용하여 데이터를 추출할 데이터 원본에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-124">The OLE DB source uses an OLE DB connection manager to connect to the data source from which it extracts data.</span></span> <span data-ttu-id="34caf-125">OLE DB 연결 관리자가 사용하는 공급자 및 연결하는 RDBMS(관계형 데이터베이스 관리 시스템)에 따라 매개 변수 명명 및 나열 작업에 적용되는 규칙이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-125">Depending on the provider that the OLE DB connection manager uses and the Relational Database Management System (RDBMS) that the connection manager connects to, different rules apply to the naming and listing of parameters.</span></span> <span data-ttu-id="34caf-126">RDBMS에서 매개 변수 이름을 반환하는 경우 매개 변수 이름을 사용하여 매개 변수 목록의 매개 변수를 SQL 문의 매개 변수에 매핑할 수 있습니다. 그렇지 않으면 매개 변수가 매개 변수 목록에서의 서수 위치별로 SQL 문의 매개 변수에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-126">If the parameter names are returned from the RDBMS, you can use parameter names to map parameters in a parameter list to parameters in an SQL statement; otherwise, the parameters are mapped to the parameter in the SQL statement by their ordinal position in the parameter list.</span></span> <span data-ttu-id="34caf-127">지원되는 매개 변수 이름 유형은 공급자에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-127">The types of parameter names that are supported vary by provider.</span></span> <span data-ttu-id="34caf-128">예를 들어 일부 공급자의 경우 변수 또는 열 이름을 사용해야 하지만 0 또는 Param0과 같은 심볼 이름을 사용해야 하는 공급자도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-128">For example, some providers require that you use the variable or column names, whereas some providers require that you use symbolic names such as 0 or Param0.</span></span> <span data-ttu-id="34caf-129">SQL 문에서 사용할 매개 변수 이름에 대한 자세한 내용은 공급자별 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="34caf-129">You should see the provider-specific documentation for information about the parameter names to use in SQL statements.</span></span>  
  
 <span data-ttu-id="34caf-130">OLE DB 연결 관리자를 사용하는 경우에는 OLE DB 원본이 OLE DB Provider를 통해 매개 변수 정보를 파생할 수 없으므로 매개 변수가 있는 하위 쿼리를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-130">When you are use an OLE DB connection manager, you cannot use parameterized subqueries, because the OLE DB source cannot derive parameter information through the OLE DB provider.</span></span> <span data-ttu-id="34caf-131">하지만 식을 사용하여 매개 변수 값을 쿼리 문자열에 연결하고 원본의 SqlCommand 속성을 설정할 수 있습니다. [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 **OLE DB 원본 편집기** 대화 상자를 사용하여 OLE DB 원본을 구성하고 **쿼리 매개 변수 설정** 대화 상자에서 매개 변수를 변수에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-131">However, you can use an expression to concatenate the parameter values into the query string and to set the SqlCommand property of the source.In [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, you configure an OLE DB source by using the **OLE DB Source Editor** dialog box and map the parameters to variables in the **Set Query Parameter** dialog box.</span></span>  
  
### <a name="specifying-parameters-by-using-ordinal-positions"></a><span data-ttu-id="34caf-132">서수 위치를 사용하여 매개 변수 지정</span><span class="sxs-lookup"><span data-stu-id="34caf-132">Specifying Parameters by Using Ordinal Positions</span></span>  
 <span data-ttu-id="34caf-133">매개 변수 이름이 반환되지 않는 경우 매개 변수가 **쿼리 매개 변수 설정** 대화 상자의 **매개 변수** 목록에 나열되는 순서에 따라 런타임에 매핑되는 대상 매개 변수 표식이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-133">If no parameter names are returned, the order in which the parameters are listed in the **Parameters** list in the **Set Query Parameter** dialog box governs which parameter marker they are mapped to at run time.</span></span> <span data-ttu-id="34caf-134">목록의 첫 번째 매개 변수는 SQL 문의 첫 번째 ?에 매핑되고</span><span class="sxs-lookup"><span data-stu-id="34caf-134">The first parameter in the list maps to the first ?</span></span> <span data-ttu-id="34caf-135">두 번째 매개 변수는 두 번째 ?에 매핑되는 식입니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-135">in the SQL statement, the second to the second ?, and so on.</span></span>  
  
 <span data-ttu-id="34caf-136">다음 SQL 문은 **데이터베이스의** Product [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] 테이블에서 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-136">The following SQL statement selects rows from the **Product** table in the [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] database.</span></span> <span data-ttu-id="34caf-137">**매핑** 목록의 첫 번째 매개 변수는 **Color** 열의 첫 번째 매개 변수에 매핑되고 두 번째 매개 변수는 **Size** 열에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-137">The first parameter in the **Mappings** list maps to the first parameter to the **Color** column, the second parameter to the **Size** column.</span></span>  
  
 `SELECT * FROM Production.Product WHERE Color = ? AND Size = ?`  
  
 <span data-ttu-id="34caf-138">매개 변수 이름은 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-138">The parameter names have no effect.</span></span> <span data-ttu-id="34caf-139">예를 들어 매개 변수의 이름이 적용될 열의 이름과 같지만 해당 매개 변수가 **매개 변수** 목록의 올바른 서수 위치에 배치되어 있지 않은 경우 런타임에 매개 변수 매핑이 수행될 때는 매개 변수의 이름이 아니라 매개 변수의 서수 위치가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-139">For example, if a parameter is named the same as the column to which it applies, but not put in the correct ordinal position in the **Parameters** list, the parameter mapping that occurs at run time will use the ordinal position of the parameter, not the parameter name.</span></span>  
  
 <span data-ttu-id="34caf-140">EXEC 명령을 사용하려면 일반적으로 프로시저의 매개 변수 값을 매개 변수 이름으로 제공하는 변수의 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-140">The EXEC command typically requires that you use the names of the variables that provide parameter values in the procedure as parameter names.</span></span>  
  
### <a name="specifying-parameters-by-using-names"></a><span data-ttu-id="34caf-141">이름을 사용하여 매개 변수 지정</span><span class="sxs-lookup"><span data-stu-id="34caf-141">Specifying Parameters by Using Names</span></span>  
 <span data-ttu-id="34caf-142">RDBMS에서 실제 매개 변수 이름을 반환하는 경우 SELECT 및 EXEC 문에서 사용하는 매개 변수가 이름별로 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-142">If the actual parameter names are returned from the RDBMS, the parameters used by a SELECT and EXEC statement are mapped by name.</span></span> <span data-ttu-id="34caf-143">매개 변수 이름은 SELECT 문이나 EXEC 문으로 실행되는 저장 프로시저에 필요한 이름과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-143">The parameter names must match the names that the stored procedure, run by the SELECT statement or the EXEC statement, expects.</span></span>  
  
 <span data-ttu-id="34caf-144">다음 SQL 문은 **데이터베이스에서 사용할 수 있는** uspGetWhereUsedProductID [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] 저장 프로시저를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-144">The following SQL statement runs the **uspGetWhereUsedProductID** stored procedure, available in the [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] database.</span></span>  
  
 `EXEC uspGetWhereUsedProductID ?, ?`  
  
 <span data-ttu-id="34caf-145">이 저장 프로시저에는 매개 변수 값을 제공할 변수 `@StartProductID` 및 `@CheckDate`가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-145">The stored procedure expects the variables, `@StartProductID` and `@CheckDate`, to provide parameter values.</span></span> <span data-ttu-id="34caf-146">**매핑** 목록에 매개 변수가 나타나는 순서는 상관없으며</span><span class="sxs-lookup"><span data-stu-id="34caf-146">The order in which the parameters appear in the **Mappings** list is irrelevant.</span></span> <span data-ttu-id="34caf-147">\@ 기호를 포함한 매개 변수 이름이 저장 프로시저의 변수 이름과 일치하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-147">The only requirement is that the parameter names match the variable names in the stored procedure, including the \@ sign.</span></span>  
  
### <a name="mapping-parameters-to-variables"></a><span data-ttu-id="34caf-148">변수에 매개 변수 매핑</span><span class="sxs-lookup"><span data-stu-id="34caf-148">Mapping Parameters to Variables</span></span>  
 <span data-ttu-id="34caf-149">매개 변수는 런타임에 매개 변수 값을 제공하는 변수에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-149">The parameters are mapped to variables that provide the parameter values at run time.</span></span> <span data-ttu-id="34caf-150">변수는 일반적으로 사용자 정의 변수이지만 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 에서 제공하는 시스템 변수를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-150">The variables are typically user-defined variables, although you can also use the system variables that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides.</span></span> <span data-ttu-id="34caf-151">사용자 정의 변수를 사용하는 경우에는 매핑된 매개 변수가 참조하는 열의 데이터 형식과 호환되는 형식으로 데이터 형식을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-151">If you use user-defined variables, make sure that you set the data type to a type that is compatible with the data type of the column that the mapped parameter references.</span></span> <span data-ttu-id="34caf-152">자세한 내용은 [Integration Services&#40;SSIS&#41; 변수](../integration-services-ssis-variables.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="34caf-152">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
## <a name="troubleshooting-the-ole-db-source"></a><span data-ttu-id="34caf-153">OLE DB 원본 문제 해결</span><span class="sxs-lookup"><span data-stu-id="34caf-153">Troubleshooting the OLE DB Source</span></span>  
 <span data-ttu-id="34caf-154">OLE DB 원본이 외부 데이터 공급자에 대해 수행하는 호출을 로깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-154">You can log the calls that the OLE DB source makes to external data providers.</span></span> <span data-ttu-id="34caf-155">이 로깅 기능을 사용하면 OLE DB 원본이 외부 데이터 원본에서 데이터를 로드할 때 발생하는 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-155">You can use this logging capability to troubleshoot the loading of data from external data sources that the OLE DB source performs.</span></span> <span data-ttu-id="34caf-156">OLE DB 원본이 외부 데이터 공급자에 대해 수행하는 호출을 로깅하려면 패키지 로깅을 설정하고 패키지 수준에서 **Diagnostic** 이벤트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-156">To log the calls that the OLE DB source makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="34caf-157">자세한 내용은 [패키지 실행 문제 해결 도구](../troubleshooting/troubleshooting-tools-for-package-execution.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="34caf-157">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
## <a name="configuring-the-ole-db-source"></a><span data-ttu-id="34caf-158">OLE DB 원본 구성</span><span class="sxs-lookup"><span data-stu-id="34caf-158">Configuring the OLE DB Source</span></span>  
 <span data-ttu-id="34caf-159">프로그래밍 방식을 통해 또는 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하여 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-159">You can set properties programmatically or through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="34caf-160">**OLE DB 원본 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="34caf-160">For more information about the properties that you can set in the **OLE DB Source Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="34caf-161">OLE DB 원본 편집기&#40;연결 관리자 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="34caf-161">OLE DB Source Editor &#40;Connection Manager Page&#41;</span></span>](../ole-db-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="34caf-162">OLE DB 원본 편집기&#40;열 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="34caf-162">OLE DB Source Editor &#40;Columns Page&#41;</span></span>](../ole-db-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="34caf-163">OLE DB 원본 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="34caf-163">OLE DB Source Editor &#40;Error Output Page&#41;</span></span>](../ole-db-source-editor-error-output-page.md)  
  
 <span data-ttu-id="34caf-164">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="34caf-164">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="34caf-165">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="34caf-165">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="34caf-166">Common Properties</span><span class="sxs-lookup"><span data-stu-id="34caf-166">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="34caf-167">OLE DB 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="34caf-167">OLE DB Custom Properties</span></span>](ole-db-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="34caf-168">관련 작업</span><span class="sxs-lookup"><span data-stu-id="34caf-168">Related Tasks</span></span>  
  
-   [<span data-ttu-id="34caf-169">OLE DB 원본을 사용하여 데이터 추출</span><span class="sxs-lookup"><span data-stu-id="34caf-169">Extract Data by Using the OLE DB Source</span></span>](ole-db-source.md)  
  
-   [<span data-ttu-id="34caf-170">쿼리 매개 변수를 데이터 흐름 구성 요소의 변수에 매핑</span><span class="sxs-lookup"><span data-stu-id="34caf-170">Map Query Parameters to Variables in a Data Flow Component</span></span>](map-query-parameters-to-variables-in-a-data-flow-component.md)  
  
-   [<span data-ttu-id="34caf-171">데이터 흐름 구성 요소의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="34caf-171">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
-   [<span data-ttu-id="34caf-172">병합 및 병합 조인 변환을 위한 데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="34caf-172">Sort Data for the Merge and Merge Join Transformations</span></span>](transformations/sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## <a name="related-content"></a><span data-ttu-id="34caf-173">관련 내용</span><span class="sxs-lookup"><span data-stu-id="34caf-173">Related Content</span></span>  
 <span data-ttu-id="34caf-174">social.technet.microsoft.com의 Wiki 문서 - [Oracle 커넥터가 있는 SSIS](https://go.microsoft.com/fwlink/?LinkId=220670)</span><span class="sxs-lookup"><span data-stu-id="34caf-174">Wiki article, [SSIS with Oracle Connectors](https://go.microsoft.com/fwlink/?LinkId=220670), on social.technet.microsoft.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34caf-175">참고 항목</span><span class="sxs-lookup"><span data-stu-id="34caf-175">See Also</span></span>  
 <span data-ttu-id="34caf-176">[OLE DB 대상](ole-db-destination.md) </span><span class="sxs-lookup"><span data-stu-id="34caf-176">[OLE DB Destination](ole-db-destination.md) </span></span>  
 <span data-ttu-id="34caf-177">[Integration Services&#40;SSIS&#41; 변수](../integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="34caf-177">[Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) </span></span>  
 [<span data-ttu-id="34caf-178">데이터 흐름</span><span class="sxs-lookup"><span data-stu-id="34caf-178">Data Flow</span></span>](data-flow.md)  
  
  
