---
title: SQL Server XML 대량 로드 개체 모델 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], object model
- ErrorLogFile property
- SGDropTables property
- SGUseID property
- KeepNulls property
- ConnectionCommand property
- SchemaGen property
- XMLFragment property
- SQLXMLBulkLoad object
- ForceTableLock property
- CheckConstraints property
- BulkLoad property
- TempFilePath property
- IgnoreDuplicateKeys property
- Transaction property
- KeepIdentity property
- ConnectionString property
- FireTriggers property
- Execute method
- XML Bulk Load [SQLXML], object model
ms.assetid: a9efbbde-ed2b-4929-acc1-261acaaed19d
author: rothja
ms.author: jroth
ms.openlocfilehash: 364515afaea17ce403f8eb38cb10bbe6003dfe2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728131"
---
# <a name="sql-server-xml-bulk-load-object-model-sqlxml-40"></a><span data-ttu-id="385a6-102">SQL Server XML 대량 로드 개체 모델(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="385a6-102">SQL Server XML Bulk Load Object Model (SQLXML 4.0)</span></span>
  <span data-ttu-id="385a6-103">Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] XML 대량 로드 개체 모델은 SQLXMLBulkLoad 개체로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-103">The Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] XML Bulk Load object model consists of the SQLXMLBulkLoad object.</span></span> <span data-ttu-id="385a6-104">이 개체는 다음 메서드 및 속성을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-104">This object supports the following methods and properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="385a6-105">메서드</span><span class="sxs-lookup"><span data-stu-id="385a6-105">Methods</span></span>  
 <span data-ttu-id="385a6-106">실행</span><span class="sxs-lookup"><span data-stu-id="385a6-106">Execute</span></span>  
 <span data-ttu-id="385a6-107">매개 변수로 제공된 스키마 파일 및 데이터 파일(또는 스트림)을 사용하여 데이터를 대량 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-107">Bulk loads the data by using the schema file and data file (or stream) that are provided as parameters.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="385a6-108">속성</span><span class="sxs-lookup"><span data-stu-id="385a6-108">Properties</span></span>  
 <span data-ttu-id="385a6-109">BulkLoad</span><span class="sxs-lookup"><span data-stu-id="385a6-109">BulkLoad</span></span>  
 <span data-ttu-id="385a6-110">대량 로드를 수행할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-110">Specifies whether a Bulk Load should be performed.</span></span> <span data-ttu-id="385a6-111">이 속성은 스키마만 생성 하 고 (다음에 나오는 SchemaGen, SGDropTables 및 Sgdroptables 속성 참조) 대량 로드를 수행 하지 않으려는 경우에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-111">This property is useful if you want to generate only the schemas (see the SchemaGen, SGDropTables, and SGUseID properties that follow) and not perform a bulk load.</span></span> <span data-ttu-id="385a6-112">이 속성은 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-112">This is a Boolean property.</span></span> <span data-ttu-id="385a6-113">이 속성이 TRUE로 설정된 경우 XML 대량 로드가 실행되고</span><span class="sxs-lookup"><span data-stu-id="385a6-113">When the property is set to TRUE, XML Bulk Load executes.</span></span> <span data-ttu-id="385a6-114">FALSE로 설정된 경우 XML 대량 로드가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-114">When it is set to FALSE, XML Bulk Load does not execute.</span></span>  
  
 <span data-ttu-id="385a6-115">기본값은 TRUE입니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-115">The default value is TRUE.</span></span>  
  
 <span data-ttu-id="385a6-116">CheckConstraints</span><span class="sxs-lookup"><span data-stu-id="385a6-116">CheckConstraints</span></span>  
 <span data-ttu-id="385a6-117">XML 대량 로드에서 열에 데이터를 삽입할 때 열에 지정된 제약 조건(예: 열 간의 기본 키/외래 키 관계로 인한 제약 조건)을 검사할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-117">Specifies whether the constraints (such as constraints due to the primary key/foreign key relationship among columns) that are specified on the column should be checked when XML Bulk Load inserts data into the columns.</span></span> <span data-ttu-id="385a6-118">이 속성은 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-118">This is a Boolean property.</span></span>  
  
 <span data-ttu-id="385a6-119">이 속성이 TRUE로 설정된 경우 XML 대량 로드에서 삽입되는 각 값에 대해 제약 조건을 검사하며 제약 조건이 위반된 경우 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-119">When the property is set to TRUE, XML Bulk Load checks the constraints for each value inserted (which means that a constraint violation results in an error).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="385a6-120">이 속성을 FALSE로 유지 하려면 대상 테이블에 대 한 **ALTER TABLE** 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-120">To leave this property as FALSE, you must have **ALTER TABLE** permissions on target tables.</span></span> <span data-ttu-id="385a6-121">자세한 내용은 [ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="385a6-121">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
 <span data-ttu-id="385a6-122">기본값은 FALSE입니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-122">The default value is FALSE.</span></span> <span data-ttu-id="385a6-123">이 속성이 FALSE로 설정된 경우 XML 대량 로드에서 삽입 작업 중 제약 조건을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-123">When it is set to FALSE, XML Bulk Load ignores the constraints during an insert operation.</span></span> <span data-ttu-id="385a6-124">현재 구현에서는 매핑 스키마에서 기본 키 및 외래 키 관계의 순서로 테이블을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-124">In the current implementation, you must define the tables in the order of primary key and foreign key relationships in the mapping schema.</span></span> <span data-ttu-id="385a6-125">즉, 외래 키가 있는 대응되는 테이블을 정의하기 전에 기본 키가 있는 테이블을 정의해야 합니다. 그렇지 않으면 XML 대량 로드가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-125">That is, a table with a primary key must be defined before the corresponding table with the foreign key; otherwise, XML Bulk Load fails.</span></span>  
  
 <span data-ttu-id="385a6-126">ID 전파가 수행 중인 경우에는 이 옵션이 적용되지 않고 제약 조건 검사가 설정된 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-126">Note that if ID Propagation is being done, then this option does not apply and constraint checking will be left on.</span></span> <span data-ttu-id="385a6-127">이는 `KeepIdentity=False`이며, 부모가 ID 필드이고 자식이 생성될 때 자식에 값이 지정되는 관계가 정의된 경우에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-127">This occurs when `KeepIdentity=False` and there is a relationship defined where the parent is an identity field and the value is given to the child as it is generated.</span></span>  
  
 <span data-ttu-id="385a6-128">ConnectionCommand</span><span class="sxs-lookup"><span data-stu-id="385a6-128">ConnectionCommand</span></span>  
 <span data-ttu-id="385a6-129">XML 대량 로드에서 사용 해야 하는 기존 연결 개체 (예: ADO 또는 ICommand command 개체)를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-129">Identifies an existing connection object (for example, the ADO or ICommand command object) that XML Bulk Load should use.</span></span> <span data-ttu-id="385a6-130">ConnectionString 속성을 사용 하 여 연결 문자열을 지정 하는 대신 ConnectionCommand 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-130">You can use the ConnectionCommand property instead of specifying a connection string with the ConnectionString property.</span></span> <span data-ttu-id="385a6-131">ConnectionCommand를 사용 하는 경우 Transaction 속성을 TRUE로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-131">The Transaction property must be set to TRUE if you use ConnectionCommand.</span></span>  
  
 <span data-ttu-id="385a6-132">ConnectionString 및 ConnectionCommand 속성을 모두 사용 하는 경우 XML 대량 로드는 마지막으로 지정 된 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-132">If you use both the ConnectionString and ConnectionCommand properties, XML Bulk Load uses the last specified property.</span></span>  
  
 <span data-ttu-id="385a6-133">기본값은 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-133">The default value is NULL.</span></span>  
  
 <span data-ttu-id="385a6-134">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="385a6-134">ConnectionString</span></span>  
 <span data-ttu-id="385a6-135">데이터베이스 인스턴스에 대한 연결을 설정하는 데 필요한 정보를 제공하는 OLE DB 연결 문자열을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-135">Identifies the OLE DB connection string that provides the necessary information to establish a connection to an instance of the database.</span></span> <span data-ttu-id="385a6-136">ConnectionString 및 ConnectionCommand 속성을 모두 사용 하는 경우 XML 대량 로드는 마지막으로 지정 된 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-136">If you use both the ConnectionString and ConnectionCommand properties, XML Bulk Load uses the last specified property.</span></span>  
  
 <span data-ttu-id="385a6-137">기본값은 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-137">The default value is NULL.</span></span>  
  
 <span data-ttu-id="385a6-138">ErrorLogFile</span><span class="sxs-lookup"><span data-stu-id="385a6-138">ErrorLogFile</span></span>  
 <span data-ttu-id="385a6-139">XML 대량 로드에서 오류 및 메시지를 기록하는 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-139">Specifies the file name into which the XML Bulk Load logs errors and messages.</span></span> <span data-ttu-id="385a6-140">기본값은 빈 문자열이며 이 경우 로깅이 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-140">The default is an empty string, in which case no logging takes place.</span></span>  
  
 <span data-ttu-id="385a6-141">FireTriggers</span><span class="sxs-lookup"><span data-stu-id="385a6-141">FireTriggers</span></span>  
 <span data-ttu-id="385a6-142">대상 테이블에 정의된 트리거를 대량 로드 작업 중 실행할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-142">Specifies if triggers defined on target tables should fire during the Bulk Load operation.</span></span> <span data-ttu-id="385a6-143">기본값은 FALSE입니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-143">The default is FALSE.</span></span>  
  
 <span data-ttu-id="385a6-144">TRUE로 설정된 경우 삽입 작업 중 트리거가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-144">When set to TRUE, triggers will fire as per normal during insert operations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="385a6-145">이 속성을 FALSE로 유지 하려면 대상 테이블에 대 한 **ALTER TABLE** 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-145">To leave this property as FALSE, you must have **ALTER TABLE** permissions on target tables.</span></span> <span data-ttu-id="385a6-146">자세한 내용은 [ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="385a6-146">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
 <span data-ttu-id="385a6-147">ID 전파가 수행 중인 경우에는 이 옵션이 적용되지 않고 트리거가 설정된 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-147">Note that if ID Propagation is being done, then this option does not apply and triggers will be left on.</span></span> <span data-ttu-id="385a6-148">이는 `KeepIdentity=False`이며, 부모가 ID 필드이고 자식이 생성될 때 자식에 값이 지정되는 관계가 정의된 경우에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-148">This occurs when `KeepIdentity=False` and there is a relationship defined where the parent is an identity field and the value is given to the child as it is generated.</span></span>  
  
 <span data-ttu-id="385a6-149">ForceTableLock</span><span class="sxs-lookup"><span data-stu-id="385a6-149">ForceTableLock</span></span>  
 <span data-ttu-id="385a6-150">XML 대량 로드에서 대량 로드 작업이 진행되는 동안 데이터를 복사할 테이블을 잠글지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-150">Specifies whether the tables into which XML Bulk Load copies data should be locked for the duration of the Bulk Load.</span></span> <span data-ttu-id="385a6-151">이 속성은 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-151">This is a Boolean property.</span></span> <span data-ttu-id="385a6-152">이 속성이 TRUE로 설정된 경우 XML 대량 로드에서 대량 로드 작업이 진행되는 동안 테이블 잠금을 확보합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-152">When the property is set to TRUE, XML Bulk Load acquires table locks for the duration of the Bulk Load.</span></span> <span data-ttu-id="385a6-153">이 속성이 FALSE로 설정된 경우에는 XML 대량 로드에서 테이블에 레코드를 삽입할 때마다 테이블 잠금을 확보합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-153">When it is set to FALSE, XML Bulk Load acquires a table lock each time it inserts a record into a table.</span></span>  
  
 <span data-ttu-id="385a6-154">기본값은 FALSE입니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-154">The default value is FALSE.</span></span>  
  
 <span data-ttu-id="385a6-155">IgnoreDuplicateKeys</span><span class="sxs-lookup"><span data-stu-id="385a6-155">IgnoreDuplicateKeys</span></span>  
 <span data-ttu-id="385a6-156">중복 값을 키 열에 삽입하려고 할 때 수행할 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-156">Specifies what to do if an attempt is made to insert duplicate values in a key column.</span></span> <span data-ttu-id="385a6-157">이 속성이 TRUE로 설정된 경우 중복 값이 있는 레코드를 키 열에 삽입하려고 하면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 해당 레코드를 삽입하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-157">If this property is set to TRUE and an attempt is made to insert a record with a duplicate value in a key column, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not insert that record.</span></span> <span data-ttu-id="385a6-158">해당 레코드 이후의 레코드는 삽입하므로 대량 로드 작업이 실패하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-158">But it does insert the subsequent record; thus, the Bulk Load operation does not fail.</span></span> <span data-ttu-id="385a6-159">이 속성이 FALSE로 설정된 경우 중복 값을 키 열에 삽입하려고 하면 대량 로드가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-159">If this property is set to FALSE, Bulk Load fails when an attempt is made to insert a duplicate value in a key column.</span></span>  
  
 <span data-ttu-id="385a6-160">IgnoreDuplicateKeys 속성을 TRUE로 설정 하면 테이블에 삽입 된 모든 레코드에 대해 COMMIT 문이 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-160">When the IgnoreDuplicateKeys property is set to TRUE, a COMMIT statement is issued for every record inserted in the table.</span></span> <span data-ttu-id="385a6-161">이로 인해 성능이 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-161">This slows down the performance.</span></span> <span data-ttu-id="385a6-162">트랜잭션 동작이 파일을 사용 하 여 구현 되기 때문에 트랜잭션 속성이 FALSE로 설정 된 경우에만 속성을 TRUE로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-162">The property can be set to TRUE only when the Transaction property is set to FALSE, because the transactional behavior is implemented using files.</span></span>  
  
 <span data-ttu-id="385a6-163">기본값은 FALSE입니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-163">The default value is FALSE.</span></span>  
  
 <span data-ttu-id="385a6-164">KeepIdentity</span><span class="sxs-lookup"><span data-stu-id="385a6-164">KeepIdentity</span></span>  
 <span data-ttu-id="385a6-165">원본 파일의 ID 유형 열에 대한 값을 처리하는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-165">Specifies how to deal with the values for an Identity type column in the source file.</span></span> <span data-ttu-id="385a6-166">이 속성은 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-166">This is a Boolean property.</span></span> <span data-ttu-id="385a6-167">이 속성이 TRUE로 설정된 경우 XML 대량 로드에서 원본 파일에 지정된 값을 ID 열에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-167">When the property is set to TRUE, XML Bulk Load assigns the values that are specified in the source file to the identity column.</span></span> <span data-ttu-id="385a6-168">이 속성이 FALSE로 설정된 경우에는 대량 로드 작업에서 원본에 지정된 ID 열 값을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-168">When the property is set to FALSE, the bulk-load operation ignores the identity-column values that are specified in the source.</span></span> <span data-ttu-id="385a6-169">이 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 ID 열에 값을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-169">In this case, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] assigns a value to the identity column.</span></span>  
  
 <span data-ttu-id="385a6-170">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 생성한 값이 저장된 ID 열을 참조하는 외래 키 열이 대량 로드에 포함될 경우 대량 로드에서는 이러한 ID 값을 해당 외래 키 열에 적절하게 전파합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-170">If the Bulk Load involves a column that is a foreign key referring to an identity column in which [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-generated values are stored, Bulk Load appropriately propagates these identity values to the foreign key column.</span></span>  
  
 <span data-ttu-id="385a6-171">이 속성 값은 대량 로드에 포함된 모든 열에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-171">The value of this property applies to all columns involved in the bulk load.</span></span> <span data-ttu-id="385a6-172">기본값은 TRUE입니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-172">The default value is TRUE.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="385a6-173">이 속성을 TRUE로 유지 하려면 대상 테이블에 대 한 **ALTER TABLE** 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-173">To leave this property as TRUE, you must have **ALTER TABLE** permissions on target tables.</span></span> <span data-ttu-id="385a6-174">그렇지 않은 경우에는 값을 FALSE로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-174">Otherwise, it must be set to a value of FALSE.</span></span> <span data-ttu-id="385a6-175">자세한 내용은 [ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="385a6-175">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
 <span data-ttu-id="385a6-176">KeepNulls</span><span class="sxs-lookup"><span data-stu-id="385a6-176">KeepNulls</span></span>  
 <span data-ttu-id="385a6-177">XML 문서에서 해당 특성이나 자식 요소가 없는 열에 사용할 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-177">Specifies what value to use for a column that is missing a corresponding attribute or child element in the XML document.</span></span> <span data-ttu-id="385a6-178">이 속성은 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-178">This is a Boolean property.</span></span> <span data-ttu-id="385a6-179">이 속성이 TRUE로 설정된 경우 XML 대량 로드에서 서버에 설정된 열의 기본값(있는 경우)이 아닌</span><span class="sxs-lookup"><span data-stu-id="385a6-179">When the property is set to TRUE, XML Bulk Load assigns a null value to the column.</span></span> <span data-ttu-id="385a6-180">null 값을 열에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-180">It does not assign the column's default value, if any, as set on the server.</span></span> <span data-ttu-id="385a6-181">이 속성 값은 대량 로드에 포함된 모든 열에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-181">The value of this property applies to all columns involved in the bulk load.</span></span>  
  
 <span data-ttu-id="385a6-182">기본값은 FALSE입니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-182">The default value is FALSE.</span></span>  
  
 <span data-ttu-id="385a6-183">SchemaGen</span><span class="sxs-lookup"><span data-stu-id="385a6-183">SchemaGen</span></span>  
 <span data-ttu-id="385a6-184">대량 로드 작업을 수행하기 전에 필요한 테이블을 만들지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-184">Specifies whether to create the required tables before performing a Bulk Load operation.</span></span> <span data-ttu-id="385a6-185">이 속성은 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-185">This is a Boolean property.</span></span> <span data-ttu-id="385a6-186">이 속성이 TRUE로 설정된 경우 매핑 스키마에 식별된 테이블이 생성됩니다. 이 경우 데이터베이스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-186">If this property is set to TRUE, the tables identified in the mapping schema are created (the database must exist).</span></span> <span data-ttu-id="385a6-187">하나 이상의 테이블이 데이터베이스에 이미 있는 경우 SGDropTables 속성은 이러한 기존 테이블을 삭제 하 고 다시 만들지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-187">If one or more of the tables already exist in the database, the SGDropTables property determines whether these preexisting tables are to be dropped and re-created.</span></span>  
  
 <span data-ttu-id="385a6-188">SchemaGen 속성의 기본값은 FALSE입니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-188">The default value for the SchemaGen property is FALSE.</span></span> <span data-ttu-id="385a6-189">SchemaGen은 새로 만든 테이블에 PRIMARY KEY 제약 조건을 만들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-189">SchemaGen does not create PRIMARY KEY constraints on the newly created tables.</span></span> <span data-ttu-id="385a6-190">그러나 SchemaGen은 `sql:relationship` 매핑 스키마에서 일치 하는 및 주석을 찾을 수 `sql:key-fields` 있고 키 필드가 단일 열로 구성 된 경우 데이터베이스에서 FOREIGN KEY 제약 조건을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-190">SchemaGen does, however, create FOREIGN KEY constraints in the database if it can find matching `sql:relationship` and `sql:key-fields` annotations in the mapping schema and if the key field consists of a single column.</span></span>  
  
 <span data-ttu-id="385a6-191">SchemaGen 속성을 TRUE로 설정 하면 XML 대량 로드에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-191">Note that if you set the SchemaGen property to TRUE, XML Bulk Load does the following:</span></span>  
  
-   <span data-ttu-id="385a6-192">요소 및 특성 이름을 사용하여 필요한 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-192">Creates the necessary tables from the element and attribute names.</span></span> <span data-ttu-id="385a6-193">따라서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 예약어는 스키마의 요소 및 특성 이름으로 사용하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-193">Therefore, it is important that you do not use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] reserved words for element and attribute names in the schema.</span></span>  
  
-   <span data-ttu-id="385a6-194">[Xml 데이터 형식](/sql/t-sql/xml/xml-transact-sql) 형식의 [sql: 오버플로 필드](annotation-interpretation-sql-overflow-field.md) 를 사용 하 여 지정 된 모든 열에 대 한 오버플로 데이터를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-194">Returns overflow data for any column designated using the [sql:overflow-field](annotation-interpretation-sql-overflow-field.md) in [xml data type](/sql/t-sql/xml/xml-transact-sql) format.</span></span>  
  
 <span data-ttu-id="385a6-195">SGDropTables</span><span class="sxs-lookup"><span data-stu-id="385a6-195">SGDropTables</span></span>  
 <span data-ttu-id="385a6-196">기존 테이블을 삭제하고 다시 만들지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-196">Specifies whether existing tables should be dropped and re-created.</span></span> <span data-ttu-id="385a6-197">SchemaGen 속성이 TRUE로 설정 된 경우이 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-197">You use this property when the SchemaGen property is set to TRUE.</span></span> <span data-ttu-id="385a6-198">SGDropTables가 FALSE 이면 기존 테이블이 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-198">If SGDropTables is FALSE, the existing tables are retained.</span></span> <span data-ttu-id="385a6-199">이 속성이 TRUE이면 기존 테이블이 삭제되고 다시 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-199">When this property is TRUE, the existing tables are deleted and re-created.</span></span>  
  
 <span data-ttu-id="385a6-200">기본값은 FALSE입니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-200">The default value is FALSE.</span></span>  
  
 <span data-ttu-id="385a6-201">SGUseID</span><span class="sxs-lookup"><span data-stu-id="385a6-201">SGUseID</span></span>  
 <span data-ttu-id="385a6-202">매핑 스키마에서 `id` 유형으로 식별된 특성을 테이블 생성 시 PRIMARY KEY 제약 조건을 만드는 데 사용할 수 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-202">Specifies whether the attribute in the mapping schema that is identified as `id` type can be used in creating a PRIMARY KEY constraint when the table is created.</span></span> <span data-ttu-id="385a6-203">SchemaGen 속성이 TRUE로 설정 된 경우이 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-203">Use this property when the SchemaGen property is set to TRUE.</span></span> <span data-ttu-id="385a6-204">SGUseID가 TRUE 이면 SchemaGen 유틸리티는 `dt:type="id"` 기본 키 열로 지정 된 특성을 사용 하 고 테이블을 만들 때 적절 한 PRIMARY key 제약 조건을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-204">If SGUseID is TRUE, the SchemaGen utility uses an attribute for which `dt:type="id"` is specified as the primary key column and adds the appropriate PRIMARY KEY constraint when creating the table.</span></span>  
  
 <span data-ttu-id="385a6-205">기본값은 FALSE입니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-205">The default value is FALSE.</span></span>  
  
 <span data-ttu-id="385a6-206">TempFilePath</span><span class="sxs-lookup"><span data-stu-id="385a6-206">TempFilePath</span></span>  
 <span data-ttu-id="385a6-207">XML 대량 로드에서 트랜잭션된 대량 로드에 사용할 임시 파일을 만들 파일 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-207">Specifies the file path where XML Bulk Load creates the temporary files for a transacted bulk load.</span></span> <span data-ttu-id="385a6-208">이 속성은 Transaction 속성이 TRUE로 설정 된 경우에만 유용 합니다. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]XML 대량 로드에 사용 되는 계정에이 경로에 대 한 액세스 권한이 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-208">(This property is useful only when the Transaction property is set to TRUE.) You must ensure that the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] account that is used for XML Bulk Load has access to this path.</span></span> <span data-ttu-id="385a6-209">이 속성이 설정되지 않은 경우 XML 대량 로드에서는 임시 파일을 TEMP 환경 변수에 지정된 위치에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-209">If this property is not set, XML Bulk Load stores the temporary files in the location that is specified in the TEMP environment variable.</span></span>  
  
 <span data-ttu-id="385a6-210">트랜잭션</span><span class="sxs-lookup"><span data-stu-id="385a6-210">Transaction</span></span>  
 <span data-ttu-id="385a6-211">대량 로드를 트랜잭션으로 수행할지 여부를 지정합니다. 트랜잭션으로 수행하면 대량 로드가 실패할 경우 롤백이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-211">Specifies whether the Bulk Load should be done as a transaction, in which case the rollback is guaranteed if the Bulk Load fails.</span></span> <span data-ttu-id="385a6-212">이 속성은 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-212">This is a Boolean property.</span></span> <span data-ttu-id="385a6-213">이 속성이 TRUE로 설정된 경우 대량 로드가 트랜잭션 컨텍스트에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-213">If the property is set to TRUE, the Bulk Load occurs in a transactional context.</span></span> <span data-ttu-id="385a6-214">TempFilePath 속성은 Transaction이 TRUE로 설정 된 경우에만 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-214">The TempFilePath property is useful only when Transaction is set to TRUE.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="385a6-215">이진 데이터를 로드 하는 경우 (예: bin. hex, bin. base64 XML 데이터 형식에서 binary, image [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식으로) 트랜잭션 속성을 FALSE로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-215">If you are loading binary data (such as the bin.hex, bin.base64 XML data types to the binary, image [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types), the Transaction property must be set to FALSE.</span></span>  
  
 <span data-ttu-id="385a6-216">기본값은 FALSE입니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-216">The default value is FALSE.</span></span>  
  
 <span data-ttu-id="385a6-217">XMLFragment</span><span class="sxs-lookup"><span data-stu-id="385a6-217">XMLFragment</span></span>  
 <span data-ttu-id="385a6-218">원본 데이터가 XML 조각인지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-218">Specifies whether the source data is an XML fragment.</span></span> <span data-ttu-id="385a6-219">XML 조각은 단일 최상위(루트) 요소가 없는 XML 문서입니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-219">An XML fragment is an XML document with no single, top-level (root) element.</span></span> <span data-ttu-id="385a6-220">이 속성은 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-220">This is a Boolean property.</span></span> <span data-ttu-id="385a6-221">원본 파일이 XML 조각으로 구성되어 있으면 이 속성을 TRUE로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-221">This property must be set to TRUE if the source file consists of an XML fragment.</span></span>  
  
 <span data-ttu-id="385a6-222">기본값은 FALSE입니다.</span><span class="sxs-lookup"><span data-stu-id="385a6-222">The default value is FALSE.</span></span>  
  
  
