---
title: OLE DB 대상 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbdest.f1
helpviewer_keywords:
- fast-load data access mode [Integration Services]
- OLE DB destination [Integration Services]
- fast load options [Integration Services]
- fast-load options [Integration Services]
- destinations [Integration Services], OLE DB
- fast load data access mode [Integration Services]
- inserting data
ms.assetid: 873a2fa0-2a02-41fc-a80a-ec9767f36a8a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a5227175e80db3a8f31a8b8db8c3d6bee3061bae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648477"
---
# <a name="ole-db-destination"></a><span data-ttu-id="76dad-102">OLE DB 대상</span><span class="sxs-lookup"><span data-stu-id="76dad-102">OLE DB Destination</span></span>
  <span data-ttu-id="76dad-103">OLE DB 대상은 데이터베이스 테이블이나 뷰 또는 SQL 명령을 사용하여 다양한 OLE DB 호환 데이터베이스로 데이터를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-103">The OLE DB destination loads data into a variety of OLE DB-compliant databases using a database table or view or an SQL command.</span></span> <span data-ttu-id="76dad-104">예를 들어 OLE DB 원본은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스의 테이블로 데이터를 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-104">For example, the OLE DB source can load data into tables in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
 <span data-ttu-id="76dad-105">OLE DB 대상은 데이터 로드를 위한 5가지 데이터 액세스 모드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-105">The OLE DB destination provides five different data access modes for loading data:</span></span>  
  
-   <span data-ttu-id="76dad-106">테이블 또는 뷰</span><span class="sxs-lookup"><span data-stu-id="76dad-106">A table or view.</span></span> <span data-ttu-id="76dad-107">기존 테이블이나 뷰를 지정하거나 새 테이블을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-107">You can specify an existing table or view, or you create a new table.</span></span>  
  
-   <span data-ttu-id="76dad-108">빠른 로드 옵션을 사용하는 테이블 또는 뷰.</span><span class="sxs-lookup"><span data-stu-id="76dad-108">A table or view using fast-load options.</span></span> <span data-ttu-id="76dad-109">기존 테이블을 지정하거나 새 테이블을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-109">You can specify an existing table or create a new table.</span></span>  
  
-   <span data-ttu-id="76dad-110">변수에 지정된 테이블 또는 뷰</span><span class="sxs-lookup"><span data-stu-id="76dad-110">A table or view specified in a variable.</span></span>  
  
-   <span data-ttu-id="76dad-111">빠른 로드 옵션을 사용하는 변수에 지정된 테이블 또는 뷰</span><span class="sxs-lookup"><span data-stu-id="76dad-111">A table or view specified in a variable using fast-load options.</span></span>  
  
-   <span data-ttu-id="76dad-112">SQL 문의 결과</span><span class="sxs-lookup"><span data-stu-id="76dad-112">The results of an SQL statement.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="76dad-113">OLE DB 대상은 매개 변수를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-113">The OLE DB destination does not support parameters.</span></span> <span data-ttu-id="76dad-114">매개 변수가 있는 INSERT 문을 실행해야 하는 경우 OLE DB 명령 변환을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="76dad-114">If you need to execute a parameterized INSERT statement, consider the OLE DB Command transformation.</span></span> <span data-ttu-id="76dad-115">자세한 내용은 [OLE DB Command Transformation](transformations/ole-db-command-transformation.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="76dad-115">For more information, see [OLE DB Command Transformation](transformations/ole-db-command-transformation.md).</span></span>  
  
 <span data-ttu-id="76dad-116">OLE DB 대상에서 DBCS(더블바이트 문자 집합)를 사용하는 문자 집합이 로드되는 경우 데이터 액세스 모드에 빠른 로드 옵션이 사용되지 않고 OLE DB 연결 관리자에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLOLEDB(OLE DB Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] )가 사용되는 경우 데이터가 손상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-116">When the OLE DB destination loads data that uses a double-byte character set (DBCS), the data may be corrupted if the data access mode does not use the fast load option and if the OLE DB connection manager uses the [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQLOLEDB).</span></span> <span data-ttu-id="76dad-117">DBCS 데이터의 무결성을 보장하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client가 사용되도록 OLE DB 연결 관리자를 구성하거나 **테이블 또는 뷰 - 빠른 로드** 또는 **테이블 이름 또는 뷰 이름 변수 - 빠른 로드**와 같은 빠른 로드 액세스 모드 중 하나를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-117">To ensure the integrity of DBCS data you should configure the OLE DB connection manager to use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, or use one of the fast-load access modes: **Table or view - fast load** or **Table name or view name variable - fast load**.</span></span> <span data-ttu-id="76dad-118">두 옵션은 모두 **OLE DB 대상 편집기** 대화 상자에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-118">Both options are available from the **OLE DB Destination Editor** dialog box.</span></span> <span data-ttu-id="76dad-119">개체 모델을 프로그래밍 하는 경우 [!INCLUDE[ssIS](../../includes/ssis-md.md)] AccessMode 속성을 또는로 설정 해야 합니다 `OpenRowset Using FastLoad` `OpenRowset Using FastLoad From Variable` .</span><span class="sxs-lookup"><span data-stu-id="76dad-119">When programming the [!INCLUDE[ssIS](../../includes/ssis-md.md)] object model, you should set the AccessMode property to `OpenRowset Using FastLoad`, or `OpenRowset Using FastLoad From Variable`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="76dad-120">OLE DB 대상에서 데이터를 삽입할 대상 테이블을 만들기 위해 **디자이너에서** OLE DB 대상 편집기 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 대화 상자를 사용하는 경우에는 새로 만든 테이블을 수동으로 선택해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-120">If you use the **OLE DB Destination Editor** dialog box in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer to create the destination table into which the OLE DB destination inserts data, you may have to select the newly created table manually.</span></span> <span data-ttu-id="76dad-121">DB2용 OLE DB 공급자와 같은 OLE DB 공급자에서 테이블 이름에 스키마 식별자를 자동으로 추가하는 경우에는 이렇게 테이블을 수동으로 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-121">The need for manual selection occurs when an OLE DB provider, such as the OLE DB provider for DB2, automatically adds schema identifiers to the table name.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="76dad-122">**OLE DB 대상 편집기** 대화 상자를 사용하여 생성하는 CREATE TABLE 문은 대상 유형에 따라 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-122">The CREATE TABLE statement that the **OLE DB Destination Editor** dialog box generates may require modification depending on the destination type.</span></span> <span data-ttu-id="76dad-123">예를 들어 일부 대상은 CREATE TABLE 문에서 사용하는 데이터 형식을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-123">For example, some destinations do not support the data types that the CREATE TABLE statement uses.</span></span>  
  
 <span data-ttu-id="76dad-124">이 대상은 OLE DB 연결 관리자를 사용하여 데이터 원본에 연결하며 연결 관리자가 사용할 OLE DB 공급자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-124">This destination uses an OLE DB connection manager to connect to a data source and the connection manager specifies the OLE DB provider to use.</span></span> <span data-ttu-id="76dad-125">자세한 내용은 [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="76dad-125">For more information, see [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="76dad-126">또한 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트는 OLE DB 연결 관리자를 만들 수 있는 데이터 원본 개체를 제공하여 OLE DB 대상에서 데이터 원본과 데이터 원본 뷰를 사용할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-126">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project also provides the data source object from which you can create an OLE DB connection manager, to make data sources and data source views available to the OLE DB destination.</span></span>  
  
 <span data-ttu-id="76dad-127">OLE DB 대상에는 입력 열과 대상 데이터 원본 열 사이의 매핑이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-127">An OLE DB destination includes mappings between input columns and columns in the destination data source.</span></span> <span data-ttu-id="76dad-128">입력 열을 모든 대상 열로 매핑할 필요는 없지만 입력 열이 대상 열에 매핑되지 않은 경우 대상 열의 속성에 따라 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-128">You do not have to map input columns to all destination columns, but depending on the properties of the destination columns, errors can occur if no input columns are mapped to the destination columns.</span></span> <span data-ttu-id="76dad-129">예를 들어 대상 열에 Null 값이 허용되지 않는 경우에는 입력 열을 해당 열에 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-129">For example, if a destination column does not allow null values, an input column must be mapped to that column.</span></span> <span data-ttu-id="76dad-130">또한 매핑된 열의 데이터 형식이 호환되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-130">In addition, the data types of mapped columns must be compatible.</span></span> <span data-ttu-id="76dad-131">예를 들어 문자열 데이터 형식의 입력 열은 숫자 데이터 형식의 대상 열로 매핑할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-131">For example, you cannot map an input column with a string data type to a destination column with a numeric data type.</span></span>  
  
 <span data-ttu-id="76dad-132">OLE DB 대상에는 하나의 일반 입력과 하나의 오류 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-132">The OLE DB destination has one regular input and one error output.</span></span>  
  
 <span data-ttu-id="76dad-133">데이터 형식에 대한 자세한 내용은 [Integration Services Data Types](integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="76dad-133">For more information about data types, see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
## <a name="fast-load-options"></a><span data-ttu-id="76dad-134">빠른 로드 옵션</span><span class="sxs-lookup"><span data-stu-id="76dad-134">Fast Load Options</span></span>  
 <span data-ttu-id="76dad-135">OLE DB 대상에서 빠른 로드 데이터 액세스 모드를 사용하는 경우 대상에 대해 사용자 인터페이스 **OLE DB 대상 편집기**에서 다음과 같은 빠른 로드 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-135">If the OLE DB destination uses a fast-load data access mode, you can specify the following fast load options in the user interface, **OLE DB Destination Editor**, for the destination:</span></span>  
  
-   <span data-ttu-id="76dad-136">가져온 데이터 파일에서 ID 값을 유지하거나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 할당된 고유 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-136">Keep identity values from the imported data file or use unique values assigned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="76dad-137">대량 로드 작업 중에 발생한 Null 값을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-137">Retain a null value during the bulk load operation.</span></span>  
  
-   <span data-ttu-id="76dad-138">대상 테이블의 제약 조건을 검사하거나 대량 가져오기 작업을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-138">Check constraints on the target table or view during the bulk import operation.</span></span>  
  
-   <span data-ttu-id="76dad-139">대량 로드 작업이 지속되는 동안 테이블 수준 잠금을 획득합니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-139">Acquire a table-level lock for the duration of the bulk load operation.</span></span>  
  
-   <span data-ttu-id="76dad-140">일괄 처리의 행 수 및 커밋 크기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-140">Specify the number of rows in the batch and the commit size.</span></span>  
  
 <span data-ttu-id="76dad-141">일부 빠른 로드 옵션은 OLE DB 대상의 특정 속성에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-141">Some fast load options are stored in specific properties of the OLE DB destination.</span></span> <span data-ttu-id="76dad-142">예를 들어 FastLoadKeepIdentity는 ID 값을 유지할지 여부를 지정하고, FastLoadKeepNulls는 Null 값을 유지할지 여부를 지정하며, FastLoadMaxInsertCommitSize는 일괄 처리로 커밋할 행 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-142">For example, FastLoadKeepIdentity specifies whether to keep identify values, FastLoadKeepNulls specifies whether to keep null values, and FastLoadMaxInsertCommitSize specifies the number of rows to commit as a batch.</span></span> <span data-ttu-id="76dad-143">기타 빠른 로드 옵션은 쉼표로 구분된 목록으로 FastLoadOptions 속성에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-143">Other fast load options are stored in a comma-separated list in the FastLoadOptions property.</span></span> <span data-ttu-id="76dad-144">OLE DB 대상에서 FastLoadOptions에 저장 되 고 **OLE DB 대상 편집기** 대화 상자에 나열 된 빠른 로드 옵션을 모두 사용 하는 경우 속성 값이로 설정 됩니다 `TABLOCK, CHECK_CONSTRAINTS, ROWS_PER_BATCH=1000` .</span><span class="sxs-lookup"><span data-stu-id="76dad-144">If the OLE DB destination uses all the fast load options that are stored in FastLoadOptions and listed in the **OLE DB Destination Editor** dialog box, the value of the property is set to `TABLOCK, CHECK_CONSTRAINTS, ROWS_PER_BATCH=1000`.</span></span> <span data-ttu-id="76dad-145">값 1000은 대상이 1000개의 행을 일괄적으로 사용하도록 구성되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-145">The value 1000 indicates that the destination is configured to use batches of 1000 rows.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="76dad-146">대상에서 제약 조건에 맞지 않아 오류가 발생하면 FastLoadMaxInsertCommitSize에 의해 정의된 행에 대한 전체 일괄 처리가 실패하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-146">Any constraint failure at the destination causes the entire batch of rows defined by FastLoadMaxInsertCommitSize to fail.</span></span>  
  
 <span data-ttu-id="76dad-147">**OLE DB 대상 편집기** 대화 상자에 표시된 빠른 로드 옵션 외에도 **고급 편집기** 대화 상자의 FastLoadOptions 속성에 옵션을 입력하여 다음과 같은 대량 로드 옵션을 사용하도록 OLE DB 대상을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-147">In addition to the fast load options exposed in the **OLE DB Destination Editor** dialog box,you can configure the OLE DB destination to use the following bulk load options by typing the options in FastLoadOptions property in the **Advanced Editor** dialog box.</span></span>  
  
|<span data-ttu-id="76dad-148">빠른 로드 옵션</span><span class="sxs-lookup"><span data-stu-id="76dad-148">Fast load option</span></span>|<span data-ttu-id="76dad-149">Description</span><span class="sxs-lookup"><span data-stu-id="76dad-149">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="76dad-150">KILOBYTES_PER_BATCH</span><span class="sxs-lookup"><span data-stu-id="76dad-150">KILOBYTES_PER_BATCH</span></span>|<span data-ttu-id="76dad-151">삽입할 크기(KB)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-151">Specifies the size in kilobytes to insert.</span></span> <span data-ttu-id="76dad-152">옵션에는 `KILOBYTES_PER_BATCH`  =  \<positive integer value**> \* \* 형식이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-152">The option has the form `KILOBYTES_PER_BATCH` = \<positive integer value**>\*\*.</span></span>|  
|<span data-ttu-id="76dad-153">FIRE_TRIGGERS</span><span class="sxs-lookup"><span data-stu-id="76dad-153">FIRE_TRIGGERS</span></span>|<span data-ttu-id="76dad-154">테이블 삽입에 대한 트리거 시작 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-154">Specifies whether triggers fire on the insert table.</span></span> <span data-ttu-id="76dad-155">이 옵션은 **FIRE_TRIGGERS**형식으로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-155">The option has the form **FIRE_TRIGGERS**.</span></span> <span data-ttu-id="76dad-156">이 옵션이 있으면 트리거가 시작됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-156">The presence of the option indicates that triggers fire.</span></span>|  
|<span data-ttu-id="76dad-157">ORDER</span><span class="sxs-lookup"><span data-stu-id="76dad-157">ORDER</span></span>|<span data-ttu-id="76dad-158">입력 데이터 저장 방식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-158">Specifies how the input data is sorted.</span></span> <span data-ttu-id="76dad-159">이 옵션은 ORDER \<column name> ASC&#124;DESC 형식으로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-159">The option has the form ORDER \<column name> ASC&#124;DESC.</span></span> <span data-ttu-id="76dad-160">열 수에 상관없이 나열할 수 있으며 정렬 순서를 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-160">Any number of columns may be listed and it is optional to include the sort order.</span></span> <span data-ttu-id="76dad-161">정렬 순서를 생략하면 삽입 작업에서는 데이터가 정렬되지 않은 것으로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-161">If sort order is omitted, the insert operation assumes the data is unsorted.</span></span><br /><br /> <span data-ttu-id="76dad-162">참고: ORDER 옵션을 사용하여 테이블의 클러스터형 인덱스에 따라 입력 데이터를 정렬하면 성능을 개선할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-162">Note: Performance can be improved if you use the ORDER option to sort the input data according to the clustered index on the table.</span></span>|  
  
 <span data-ttu-id="76dad-163">[!INCLUDE[tsql](../../includes/tsql-md.md)] 키워드는 일반적으로 대문자를 사용하여 입력하지만 키워드는 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-163">The [!INCLUDE[tsql](../../includes/tsql-md.md)] keywords are traditionally typed using uppercase letters, but the keywords are not case sensitive.</span></span>  
  
 <span data-ttu-id="76dad-164">빠른 로드 옵션에 대한 자세한 내용은 [BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="76dad-164">To learn more about fast load options, see [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
## <a name="troubleshooting-the-ole-db-destination"></a><span data-ttu-id="76dad-165">OLE DB 대상 문제 해결</span><span class="sxs-lookup"><span data-stu-id="76dad-165">Troubleshooting the OLE DB Destination</span></span>  
 <span data-ttu-id="76dad-166">OLE DB 대상이 외부 데이터 공급자에 대해 수행하는 호출을 로깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-166">You can log the calls that the OLE DB destination makes to external data providers.</span></span> <span data-ttu-id="76dad-167">이 로깅 기능을 사용하면 OLE DB 대상이 외부 데이터 원본에 데이터를 저장할 때 발생하는 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-167">You can use this logging capability to troubleshoot the saving of data to external data sources that the OLE DB destination performs.</span></span> <span data-ttu-id="76dad-168">OLE DB 대상이 외부 데이터 공급자에 대해 수행하는 호출을 로깅하려면 패키지 로깅을 설정하고 패키지 수준에서 **Diagnostic** 이벤트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-168">To log the calls that the OLE DB destination makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="76dad-169">자세한 내용은 [패키지 실행 문제 해결 도구](../troubleshooting/troubleshooting-tools-for-package-execution.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="76dad-169">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
## <a name="configuring-the-ole-db-destination"></a><span data-ttu-id="76dad-170">OLE DB 대상 구성</span><span class="sxs-lookup"><span data-stu-id="76dad-170">Configuring the OLE DB Destination</span></span>  
 <span data-ttu-id="76dad-171">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-171">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="76dad-172">**OLE DB 대상 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="76dad-172">For more information about the properties that you can set in the **OLE DB Destination Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="76dad-173">OLE DB 대상 편집기&#40;연결 관리자 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="76dad-173">OLE DB Destination Editor &#40;Connection Manager Page&#41;</span></span>](../ole-db-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="76dad-174">OLE DB 대상 편집기&#40;매핑 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="76dad-174">OLE DB Destination Editor &#40;Mappings Page&#41;</span></span>](../ole-db-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="76dad-175">OLE DB 대상 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="76dad-175">OLE DB Destination Editor &#40;Error Output Page&#41;</span></span>](../ole-db-destination-editor-error-output-page.md)  
  
 <span data-ttu-id="76dad-176">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="76dad-176">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="76dad-177">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="76dad-177">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="76dad-178">Common Properties</span><span class="sxs-lookup"><span data-stu-id="76dad-178">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="76dad-179">OLE DB 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="76dad-179">OLE DB Custom Properties</span></span>](ole-db-custom-properties.md)  
  
 <span data-ttu-id="76dad-180">속성 설정 방법을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="76dad-180">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="76dad-181">OLE DB 대상을 사용하여 데이터 로드</span><span class="sxs-lookup"><span data-stu-id="76dad-181">Load Data by Using the OLE DB Destination</span></span>](ole-db-destination.md)  
  
-   [<span data-ttu-id="76dad-182">데이터 흐름 구성 요소의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="76dad-182">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a><span data-ttu-id="76dad-183">관련 내용</span><span class="sxs-lookup"><span data-stu-id="76dad-183">Related Content</span></span>  
 [<span data-ttu-id="76dad-184">OLE DB 원본</span><span class="sxs-lookup"><span data-stu-id="76dad-184">OLE DB Source</span></span>](ole-db-source.md)  
  
 [<span data-ttu-id="76dad-185">Integration Services&#40;SSIS&#41; 변수</span><span class="sxs-lookup"><span data-stu-id="76dad-185">Integration Services &#40;SSIS&#41; Variables</span></span>](../integration-services-ssis-variables.md)  
  
 [<span data-ttu-id="76dad-186">데이터 흐름</span><span class="sxs-lookup"><span data-stu-id="76dad-186">Data Flow</span></span>](data-flow.md)  
  
  
