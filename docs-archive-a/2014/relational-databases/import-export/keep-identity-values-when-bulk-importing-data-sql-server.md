---
title: 데이터 대량 가져오기 중 ID 값 유지(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- identity values [SQL Server], bulk imports
- data formats [SQL Server], identity values
- bulk importing [SQL Server], identity values
ms.assetid: 45894a3f-2d8a-4edd-9568-afa7d0d3061f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 07f6714f27f60afda91134034509ff439d92f071
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653372"
---
# <a name="keep-identity-values-when-bulk-importing-data-sql-server"></a><span data-ttu-id="deb3b-102">데이터 대량 가져오기 중 ID 값 유지(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="deb3b-102">Keep Identity Values When Bulk Importing Data (SQL Server)</span></span>
  <span data-ttu-id="deb3b-103">Id 값을 포함 하는 데이터 파일을 인스턴스로 대량으로 가져올 수 있습니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="deb3b-103">Data files that contain identity values can be bulk imported into an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="deb3b-104">기본적으로 가져온 데이터 파일의 ID 열 값은 무시되고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 자동으로 고유 값을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-104">By default, the values for the identity column in the data file that is imported are ignored and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assigns unique values automatically.</span></span> <span data-ttu-id="deb3b-105">고유 값은 테이블 작성 중에 지정된 초기 및 증분 값을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-105">The unique values are based on the seed and increment values that are specified during table creation.</span></span>  
  
 <span data-ttu-id="deb3b-106">데이터 파일에 테이블의 ID 열에 대한 값이 없으면 서식 파일을 사용하여 데이터를 가져올 때 테이블의 ID 열을 건너뛰어야 함을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-106">If the data file does not contain values for the identifier column in the table, use a format file to specify that the identifier column in the table should be skipped when importing data.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="deb3b-107">는 자동으로 열에 고유 값을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-107">assigns unique values for the column automatically.</span></span>  
  
 <span data-ttu-id="deb3b-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 ID 값을 할당하지 않으면서 테이블에 데이터 행을 대량으로 가져오려면 적절한 ID 유지 명령 한정자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-108">To prevent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from assigning identity values while bulk importing data rows into a table, use the appropriate keep-identity command qualifier.</span></span> <span data-ttu-id="deb3b-109">ID 유지 한정자를 지정하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 데이터 파일의 ID 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-109">When you specify a keep-identity qualifier, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses the identity values in the data file.</span></span> <span data-ttu-id="deb3b-110">이러한 한정자는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-110">These qualifiers are as follows:</span></span>  
  
|<span data-ttu-id="deb3b-111">명령</span><span class="sxs-lookup"><span data-stu-id="deb3b-111">Command</span></span>|<span data-ttu-id="deb3b-112">ID 유지 한정자</span><span class="sxs-lookup"><span data-stu-id="deb3b-112">Keep-identity qualifier</span></span>|<span data-ttu-id="deb3b-113">한정자 유형</span><span class="sxs-lookup"><span data-stu-id="deb3b-113">Qualifier type</span></span>|  
|-------------|------------------------------|--------------------|  
|`bcp`|<span data-ttu-id="deb3b-114">**-E**</span><span class="sxs-lookup"><span data-stu-id="deb3b-114">**-E**</span></span>|<span data-ttu-id="deb3b-115">스위치</span><span class="sxs-lookup"><span data-stu-id="deb3b-115">Switch</span></span>|  
|<span data-ttu-id="deb3b-116">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="deb3b-116">BULK INSERT</span></span>|<span data-ttu-id="deb3b-117">KEEPIDENTITY</span><span class="sxs-lookup"><span data-stu-id="deb3b-117">KEEPIDENTITY</span></span>|<span data-ttu-id="deb3b-118">인수</span><span class="sxs-lookup"><span data-stu-id="deb3b-118">Argument</span></span>|  
|<span data-ttu-id="deb3b-119">INSERT ... 선택 \* OPENROWSET (BULK)에서</span><span class="sxs-lookup"><span data-stu-id="deb3b-119">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>|<span data-ttu-id="deb3b-120">KEEPIDENTITY</span><span class="sxs-lookup"><span data-stu-id="deb3b-120">KEEPIDENTITY</span></span>|<span data-ttu-id="deb3b-121">테이블 힌트</span><span class="sxs-lookup"><span data-stu-id="deb3b-121">Table hint</span></span>|  
  
 <span data-ttu-id="deb3b-122">자세한 내용은 [bcp 유틸리티](../../tools/bcp-utility.md), [BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), [OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql), [INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql), [SELECT&#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) 및 [테이블 힌트&#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="deb3b-122">For more information, see [bcp Utility](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql), [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql), [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql), and [Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="deb3b-123">여러 테이블에서 사용할 수 있거나 테이블을 참조하지 않고 애플리케이션에서 호출할 수 있는 자동으로 증가하는 번호를 만들려면 [시퀀스 번호](../sequence-numbers/sequence-numbers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="deb3b-123">To create an automatically incrementing number that can be used in multiple tables or that can be called from applications without referencing any table, see [Sequence Numbers](../sequence-numbers/sequence-numbers.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="deb3b-124">예</span><span class="sxs-lookup"><span data-stu-id="deb3b-124">Examples</span></span>  
 <span data-ttu-id="deb3b-125">이 항목의 예제에서는 INSERT ...를 사용 하 여 데이터를 대량으로 가져옵니다. SELECT \* FROM OPENROWSET (BULK ...) 및 default 값을 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-125">The examples in this topic bulk import data using INSERT ... SELECT \* FROM OPENROWSET(BULK...) and keeping default values.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="deb3b-126">예제 테이블</span><span class="sxs-lookup"><span data-stu-id="deb3b-126">Sample Table</span></span>  
 <span data-ttu-id="deb3b-127">대량 가져오기 예제에서는 **dbo** 스키마의 **AdventureWorks** 샘플 데이터베이스에 **myTestKeepNulls** 테이블을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-127">The bulk-import examples require that a table named **myTestKeepNulls** table be created in the **AdventureWorks** sample database under the **dbo** schema.</span></span> <span data-ttu-id="deb3b-128">이 테이블을 만들려면</span><span class="sxs-lookup"><span data-stu-id="deb3b-128">To create this table.</span></span> <span data-ttu-id="deb3b-129">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-129">in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
SELECT * INTO HumanResources.myDepartment   
   FROM HumanResources.Department  
      WHERE 1=0;  
GO  
SELECT * FROM HumanResources.myDepartment;  
```  
  
 <span data-ttu-id="deb3b-130">`myDepartment`의 기반이 되는 **Department** 테이블은 IDENTITY_INSERT가 OFF로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-130">The **Department** table on which `myDepartment` is based has IDENTITY_INSERT is set to OFF.</span></span> <span data-ttu-id="deb3b-131">따라서 ID 열로 데이터를 가져오려면 KEEPIDENTITY 또는 **-E**를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-131">Therefore, to import data into an identity column you must specify KEEPIDENTITY or **-E**.</span></span>  
  
### <a name="sample-data-file"></a><span data-ttu-id="deb3b-132">예제 데이터 파일</span><span class="sxs-lookup"><span data-stu-id="deb3b-132">Sample Data File</span></span>  
 <span data-ttu-id="deb3b-133">대량 가져오기 예에 사용된 데이터 파일에는 `HumanResources.Department` 테이블에서 네이티브 형식으로, 대량으로 내보낸 데이터가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-133">The data file used in the bulk-import examples contains data bulk exported from the `HumanResources.Department` table in native format.</span></span> <span data-ttu-id="deb3b-134">데이터 파일을 만들려면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-134">To create the data file, at the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks.HumanResources.Department out myDepartment-n.Dat -n -T  
```  
  
### <a name="sample-format-file"></a><span data-ttu-id="deb3b-135">예제 서식 파일</span><span class="sxs-lookup"><span data-stu-id="deb3b-135">Sample Format File</span></span>  
 <span data-ttu-id="deb3b-136">이 대량 가져오기 예에서는 네이티브 데이터 형식을 사용하는 XML 서식 파일인 `myDepartment-f-x-n.Xml`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-136">This bulk-import examples use an XML format file, `myDepartment-f-x-n.Xml`, which uses native data formats.</span></span> <span data-ttu-id="deb3b-137">이 예에서는 `bcp`를 사용하여 `HumanResources.Department` 데이터베이스의 `AdventureWorks` 테이블에서 이 서식 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-137">This example uses `bcp` to create to generate this format file from the `HumanResources.Department` table of the `AdventureWorks` database.</span></span> <span data-ttu-id="deb3b-138">Windows 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-138">At the Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks.HumanResources.Department format nul -n -x -f myDepartment-f-n-x.Xml -T  
```  
  
 <span data-ttu-id="deb3b-139">서식 파일을 만드는 방법은 [서식 파일 만들기&#40;SQL Server&#41;](create-a-format-file-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="deb3b-139">For more information about creating a format file, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
### <a name="a-using-bcp-and-keeping-identity-values"></a><span data-ttu-id="deb3b-140">A.</span><span class="sxs-lookup"><span data-stu-id="deb3b-140">A.</span></span> <span data-ttu-id="deb3b-141">bcp 사용 및 ID 값 유지</span><span class="sxs-lookup"><span data-stu-id="deb3b-141">Using bcp and Keeping Identity Values</span></span>  
 <span data-ttu-id="deb3b-142">다음 예에서는 `bcp`를 사용하여 데이터를 대량으로 가져올 때 ID 값을 유지하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-142">The following example demonstrates how to keep identity values when using `bcp` to bulk import data.</span></span> <span data-ttu-id="deb3b-143">`bcp` 명령은 서식 파일인 `myDepartment-f-n-x.Xml`을 사용하며 다음 스위치를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-143">The `bcp` command uses the format file, `myDepartment-f-n-x.Xml`, and contains the following switches:</span></span>  
  
|<span data-ttu-id="deb3b-144">한정자</span><span class="sxs-lookup"><span data-stu-id="deb3b-144">Qualifiers</span></span>|<span data-ttu-id="deb3b-145">Description</span><span class="sxs-lookup"><span data-stu-id="deb3b-145">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="deb3b-146">**-E**</span><span class="sxs-lookup"><span data-stu-id="deb3b-146">**-E**</span></span>|<span data-ttu-id="deb3b-147">데이터 파일의 ID 값이 ID 열에 사용되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-147">Specifies that identity value or values in the data file are to be used for the identity column.</span></span>|  
|<span data-ttu-id="deb3b-148">**-T**</span><span class="sxs-lookup"><span data-stu-id="deb3b-148">**-T**</span></span>|<span data-ttu-id="deb3b-149">`bcp`유틸리티가 트러스트 된 연결을 통해에 연결 되도록 지정 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="deb3b-149">Specifies that the `bcp` utility connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with a trusted connection.</span></span>|  
  
 <span data-ttu-id="deb3b-150">Windows 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-150">At the Windows command prompt, enter.</span></span>  
  
```  
bcp AdventureWorks.HumanResources.myDepartment in C:\myDepartment-n.Dat -f C:\myDepartment-f-n-x.Xml -E -T  
  
```  
  
### <a name="b-using-bulk-insert-and-keeping-identity-values"></a><span data-ttu-id="deb3b-151">B.</span><span class="sxs-lookup"><span data-stu-id="deb3b-151">B.</span></span> <span data-ttu-id="deb3b-152">BULK INSERT 사용 및 ID 값 유지</span><span class="sxs-lookup"><span data-stu-id="deb3b-152">Using BULK INSERT and Keeping Identity Values</span></span>  
 <span data-ttu-id="deb3b-153">다음 예에서는 BULK INSERT를 사용하여 `myDepartment-c.Dat` 데이터 파일에서 `AdventureWorks.HumanResources.myDepartment` 테이블로 데이터를 대량으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-153">The following example uses BULK INSERT to bulk import data from the `myDepartment-c.Dat` file into the `AdventureWorks.HumanResources.myDepartment` table.</span></span> <span data-ttu-id="deb3b-154">해당 문은 `myDepartment-f-n-x.Xml` 서식 파일을 사용하며 KEEPIDENTITY 옵션을 포함하여 데이터 파일의 모든 ID를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-154">The statement uses the `myDepartment-f-n-x.Xml` format file and includes the KEEPIDENTITY option to ensure that any identity values in the data file are retained.</span></span>  
  
 <span data-ttu-id="deb3b-155">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-155">In the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
DELETE HumanResources.myDepartment;  
GO  
BULK INSERT HumanResources.myDepartment  
   FROM 'C:\myDepartment-n.Dat'  
   WITH (  
      KEEPIDENTITY,  
      FORMATFILE='C:\myDepartment-f-n-x.Xml'  
   );  
GO  
SELECT * FROM HumanResources.myDepartment;  
  
```  
  
### <a name="c-using-openrowset-and-keeping-identity-values"></a><span data-ttu-id="deb3b-156">C.</span><span class="sxs-lookup"><span data-stu-id="deb3b-156">C.</span></span> <span data-ttu-id="deb3b-157">OPENROWSET 사용 및 ID 값 유지</span><span class="sxs-lookup"><span data-stu-id="deb3b-157">Using OPENROWSET and Keeping Identity Values</span></span>  
 <span data-ttu-id="deb3b-158">다음 예에서는 OPENROWSET 대량 행 집합 공급자를 사용하여 `myDepartment-c.Dat` 파일에서 `AdventureWorks.HumanResources.myDepartment` 테이블로 데이터를 대량으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-158">The following example uses the OPENROWSET bulk rowset provider to bulk import data from the `myDepartment-c.Dat` file into the `AdventureWorks.HumanResources.myDepartment` table.</span></span> <span data-ttu-id="deb3b-159">해당 문은 `myDepartment-f-n-x.Xml` 서식 파일을 사용하고 KEEPIDENTITY 힌트를 포함하여 데이터 파일의 모든 ID 값을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-159">The statement uses the `myDepartment-f-n-x.Xml` format file and includes the KEEPIDENTITY hint to ensure that any identity values in the data file are retained.</span></span>  
  
 <span data-ttu-id="deb3b-160">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="deb3b-160">In the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
DELETE HumanResources.myDepartment;  
GO  
  
INSERT INTO HumanResources.myDepartment  
   with (KEEPIDENTITY)  
   (DepartmentID, Name, GroupName, ModifiedDate)  
   SELECT *  
      FROM  OPENROWSET(BULK 'C:\myDepartment-n.Dat',  
      FORMATFILE='C:\myDepartment-f-n-x.Xml') as t1;  
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="deb3b-161">관련 작업</span><span class="sxs-lookup"><span data-stu-id="deb3b-161">Related Tasks</span></span>  
  
-   [<span data-ttu-id="deb3b-162">대량 가져오기 수행 중 Null 유지 또는 기본값 사용&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="deb3b-162">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [<span data-ttu-id="deb3b-163">대량 내보내기 또는 가져오기를 위한 데이터 준비&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="deb3b-163">Prepare Data for Bulk Export or Import &#40;SQL Server&#41;</span></span>](prepare-data-for-bulk-export-or-import-sql-server.md)  
  
 <span data-ttu-id="deb3b-164">**서식 파일을 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="deb3b-164">**To use a format file**</span></span>  
  
-   [<span data-ttu-id="deb3b-165">서식 파일 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="deb3b-165">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="deb3b-166">서식 파일을 사용하여 데이터 대량 가져오기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="deb3b-166">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="deb3b-167">서식 파일을 사용하여 테이블 열을 데이터 파일 필드에 매핑&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="deb3b-167">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
-   [<span data-ttu-id="deb3b-168">서식 파일을 사용하여 데이터 필드 건너뛰기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="deb3b-168">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="deb3b-169">서식 파일을 사용하여 테이블 열 건너뛰기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="deb3b-169">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 <span data-ttu-id="deb3b-170">**대량 가져오기 또는 대량 내보내기를 위한 데이터 형식을 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="deb3b-170">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="deb3b-171">SQL Server 이전 버전으로부터 기본 및 문자 형식 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="deb3b-171">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [<span data-ttu-id="deb3b-172">문자 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="deb3b-172">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="deb3b-173">네이티브 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="deb3b-173">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="deb3b-174">유니코드 문자 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="deb3b-174">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="deb3b-175">유니코드 네이티브 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="deb3b-175">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 <span data-ttu-id="deb3b-176">**bcp를 사용할 때 데이터 형식의 호환 가능성을 지정하려면**</span><span class="sxs-lookup"><span data-stu-id="deb3b-176">**To specify data formats for compatibility when using bcp**</span></span>  
  
1.  [<span data-ttu-id="deb3b-177">필드 및 행 종결자 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="deb3b-177">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](specify-field-and-row-terminators-sql-server.md)  
  
2.  [<span data-ttu-id="deb3b-178">bcp를 사용하여 데이터 파일에 접두사 길이 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="deb3b-178">Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;</span></span>](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
3.  [<span data-ttu-id="deb3b-179">bcp를 사용하여 파일 스토리지 유형 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="deb3b-179">Specify File Storage Type by Using bcp &#40;SQL Server&#41;</span></span>](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="deb3b-180">참고 항목</span><span class="sxs-lookup"><span data-stu-id="deb3b-180">See Also</span></span>  
 <span data-ttu-id="deb3b-181">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="deb3b-181">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="deb3b-182">[bcp 유틸리티](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="deb3b-182">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="deb3b-183">[BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="deb3b-183">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="deb3b-184">[OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="deb3b-184">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 [<span data-ttu-id="deb3b-185">테이블 힌트&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="deb3b-185">Table Hints &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/hints-transact-sql-table)  
  
  
