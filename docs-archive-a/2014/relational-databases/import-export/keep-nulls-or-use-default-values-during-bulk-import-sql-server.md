---
title: 대량 가져오기 수행 중 Null 유지 또는 기본값 사용(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk importing [SQL Server], null values
- bulk importing [SQL Server], default values
- data formats [SQL Server], null values
- bulk rowset providers [SQL Server]
- bcp utility [SQL Server], null values
- BULK INSERT statement
- default values
- OPENROWSET function, bulk importing
- data formats [SQL Server], default values
ms.assetid: 6b91d762-337b-4345-a159-88abb3e64a81
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 856aa12f6ad5e5094324e0df65941bc63d611451
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741052"
---
# <a name="keep-nulls-or-use-default-values-during-bulk-import-sql-server"></a><span data-ttu-id="e0e08-102">대량 가져오기 수행 중 Null 유지 또는 기본값 사용(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e0e08-102">Keep Nulls or Use Default Values During Bulk Import (SQL Server)</span></span>
  <span data-ttu-id="e0e08-103">기본적으로 데이터를 테이블로 가져올 때 **bcp** 명령 및 BULK INSERT 문은 해당 테이블의 열에 대해 정의된 기본값을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-103">By default, when data is imported into a table, the **bcp** command and BULK INSERT statement observe any defaults that are defined for the columns in the table.</span></span> <span data-ttu-id="e0e08-104">예를 들어 데이터 파일에 null 필드가 있으면 열의 기본값이 대신 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-104">For example, if there is a null field in a data file, the default value for the column is loaded instead.</span></span> <span data-ttu-id="e0e08-105">**bcp** 명령 및 BULK INSERT 문을 사용하면 Null 값을 유지하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-105">The **bcp** command and BULK INSERT statement both allow you to specify that nulls values be retained.</span></span>  
  
 <span data-ttu-id="e0e08-106">반대로 일반 INSERT 문은 기본값을 삽입하는 대신 Null 값을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-106">In contrast, a regular INSERT statement retains the null value instead of inserting a default value.</span></span> <span data-ttu-id="e0e08-107">INSERT ... SELECT \* FROM OPENROWSET(BULK...) 문은 일반 INSERT와 같은 기본 동작을 제공하지만 기본값 삽입에 대한 테이블 힌트를 추가로 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-107">The INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement provides the same basic behavior as regular INSERT but additionally supports a table hint for inserting the default values.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e0e08-108">테이블 열 건너뛰기 예제 서식 파일은 [서식 파일을 사용하여 테이블 열 건너뛰기&#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0e08-108">For sample format files that skip a table column, see [Use a Format File to Skip a Table Column &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md).</span></span>  
  
## <a name="sample-table-and-data-file"></a><span data-ttu-id="e0e08-109">예제 테이블 및 데이터 파일</span><span class="sxs-lookup"><span data-stu-id="e0e08-109">Sample Table and Data File</span></span>  
 <span data-ttu-id="e0e08-110">이 항목의 예를 실행하려면 예제 테이블 및 데이터 파일을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-110">To run the examples in this topic, you need to create a sample table and data file.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="e0e08-111">예제 테이블</span><span class="sxs-lookup"><span data-stu-id="e0e08-111">Sample Table</span></span>  
 <span data-ttu-id="e0e08-112">이 예에서는 **dbo** 스키마의 **AdventureWorks** 예제 데이터베이스에서 **MyTestDefaultCol2** 라는 이름의 테이블을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-112">The examples require that a table named **MyTestDefaultCol2** be created in the **AdventureWorks** sample database under the **dbo** schema.</span></span> <span data-ttu-id="e0e08-113">이 테이블을 만들려면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-113">To create this table, in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE MyTestDefaultCol2   
(Col1 smallint,  
Col2 nvarchar(50) DEFAULT 'Default value of Col2',  
Col3 nvarchar(50)   
);  
GO  
  
```  
  
 <span data-ttu-id="e0e08-114">두 번째 테이블 열 `Col2`는 기본값을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-114">Notice that the second table column, `Col2`, has a default value.</span></span>  
  
### <a name="sample-format-file"></a><span data-ttu-id="e0e08-115">예제 서식 파일</span><span class="sxs-lookup"><span data-stu-id="e0e08-115">Sample Format File</span></span>  
 <span data-ttu-id="e0e08-116">일부 대량 가져오기 예에서는 XML이 아닌 서식 파일(`MyTestDefaultCol2-f-c.Fmt`)을 사용하는데 이 파일은 `MyTestDefaultCol2` 테이블과 정확히 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-116">Some of the bulk-import examples use a non-XML format file, `MyTestDefaultCol2-f-c.Fmt` that corresponds exactly to the `MyTestDefaultCol2` table.</span></span> <span data-ttu-id="e0e08-117">이 서식 파일을 만들려면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-117">To create this format file, at the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks..MyTestDefaultCol2 format nul -c -f C:\MyTestDefaultCol2-f-c.Fmt -t, -r\n -T  
  
```  
  
 <span data-ttu-id="e0e08-118">서식 파일을 만드는 방법은 [서식 파일 만들기&#40;SQL Server&#41;](create-a-format-file-sql-server.md)를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="e0e08-118">For more information about creating format files, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
### <a name="sample-data-file"></a><span data-ttu-id="e0e08-119">예제 데이터 파일</span><span class="sxs-lookup"><span data-stu-id="e0e08-119">Sample Data File</span></span>  
 <span data-ttu-id="e0e08-120">이 예에서는 예제 데이터 파일( `MyTestEmptyField2-c.Dat`)을 사용하는데 이 파일은 두 번째 필드에 값이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-120">The example uses a sample data file, `MyTestEmptyField2-c.Dat`, that contains no values in the second field.</span></span> <span data-ttu-id="e0e08-121">`MyTestEmptyField2-c.Dat` 데이터 파일에는 다음 레코드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-121">The `MyTestEmptyField2-c.Dat` data file contains the following records.</span></span>  
  
```  
1,,DataField3  
2,,DataField3  
  
```  
  
## <a name="keeping-null-values-with-bcp-or-bulk-insert"></a><span data-ttu-id="e0e08-122">bcp 또는 BULK INSERT로 Null 값 유지</span><span class="sxs-lookup"><span data-stu-id="e0e08-122">Keeping Null Values with bcp or BULK INSERT</span></span>  
 <span data-ttu-id="e0e08-123">다음 한정자는 대량 가져오기 작업 중 테이블 열에 대한 기본값(있는 경우)을 상속하기보다는 데이터 파일의 빈 필드에 Null 값을 유지하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-123">The following qualifiers specify that an empty field in the data file retains its null value during the bulk-import operation, rather than inheriting a default value (if any) for the table columns.</span></span>  
  
|<span data-ttu-id="e0e08-124">명령</span><span class="sxs-lookup"><span data-stu-id="e0e08-124">Command</span></span>|<span data-ttu-id="e0e08-125">한정자</span><span class="sxs-lookup"><span data-stu-id="e0e08-125">Qualifier</span></span>|<span data-ttu-id="e0e08-126">한정자 유형</span><span class="sxs-lookup"><span data-stu-id="e0e08-126">Qualifier type</span></span>|  
|-------------|---------------|--------------------|  
|<span data-ttu-id="e0e08-127">**bcp**</span><span class="sxs-lookup"><span data-stu-id="e0e08-127">**bcp**</span></span>|`-k`|<span data-ttu-id="e0e08-128">스위치</span><span class="sxs-lookup"><span data-stu-id="e0e08-128">Switch</span></span>|  
|<span data-ttu-id="e0e08-129">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="e0e08-129">BULK INSERT</span></span>|<span data-ttu-id="e0e08-130">KEEPNULLS<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e0e08-130">KEEPNULLS<sup>1</sup></span></span>|<span data-ttu-id="e0e08-131">인수</span><span class="sxs-lookup"><span data-stu-id="e0e08-131">Argument</span></span>|  
  
 <span data-ttu-id="e0e08-132"><sup>1</sup> BULK INSERT의 경우 기본값을 사용할 수 없으면 null 값을 허용 하도록 테이블 열을 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-132"><sup>1</sup> For BULK INSERT, if default values are not available, the table column must be defined to allow null values.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e0e08-133">이러한 한정자는 대량 가져오기 명령을 통해 테이블에서 DEFAULT 정의 확인을 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-133">These qualifiers disable checking of DEFAULT definitions on a table by these bulk-import commands.</span></span> <span data-ttu-id="e0e08-134">그러나 동시 INSERT 문의 경우 DEFAULT 정의가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-134">However, for any concurrent INSERT statements, DEFAULT definitions are expected.</span></span>  
  
 <span data-ttu-id="e0e08-135">자세한 내용은 [bcp 유틸리티](../../tools/bcp-utility.md) 및 [BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0e08-135">For more information, see [bcp Utility](../../tools/bcp-utility.md) and [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
### <a name="examples"></a><span data-ttu-id="e0e08-136">예</span><span class="sxs-lookup"><span data-stu-id="e0e08-136">Examples</span></span>  
 <span data-ttu-id="e0e08-137">이 섹션의 예에서는 **bcp** 또는 BULK INSERT를 사용하여 대량 가져오기를 수행하고 Null 값을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-137">The examples in this section bulk import using **bcp** or BULK INSERT and keep null values.</span></span>  
  
 <span data-ttu-id="e0e08-138">두 번째 테이블 열 **Col2**는 기본값을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-138">The second table column, **Col2**, has a default value.</span></span> <span data-ttu-id="e0e08-139">데이터 파일의 해당되는 필드에는 빈 문자열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-139">The corresponding field of the data file contains an empty string.</span></span> <span data-ttu-id="e0e08-140">기본적으로 **bcp** 또는 BULK INSERT를 사용하여 이 데이터 파일에서 **MyTestDefaultCol2** 테이블로 데이터를 가져오면 **Col2** 의 기본값이 삽입되어 다음과 같은 결과가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-140">By default, when **bcp** or BULK INSERT is used to import data from this data file into the **MyTestDefaultCol2** table, the default value of **Col2** is inserted, producing the following result:</span></span>  
  
||||  
|-|-|-|  
|`1`|`Default value of Col2`|`DataField3`|  
|`2`|`Default value of Col2`|`DataField3`|  
  
 <span data-ttu-id="e0e08-141">"" 대신 ""을 삽입 하려면 `NULL` `Default value of Col2` `-k` 다음 **bcp** 및 BULK INSERT 예제에서 보여 주는 것 처럼 switch 또는 keepnull 옵션을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-141">To insert "`NULL`" instead of "`Default value of Col2`", you need to use the `-k` switch or KEEPNULL option, as demonstrated in the following **bcp** and BULK INSERT examples.</span></span>  
  
#### <a name="using-bcp-and-keeping-null-values"></a><span data-ttu-id="e0e08-142">bcp 사용 및 Null 값 유지</span><span class="sxs-lookup"><span data-stu-id="e0e08-142">Using bcp and Keeping Null Values</span></span>  
 <span data-ttu-id="e0e08-143">다음 예에서는 **bcp** 명령에서 Null 값을 유지하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-143">The following example demonstrates how to keep null values in a **bcp** command.</span></span> <span data-ttu-id="e0e08-144">**Bcp** 명령에는 다음 스위치가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-144">The **bcp** command contains the following switches:</span></span>  
  
|<span data-ttu-id="e0e08-145">스위치</span><span class="sxs-lookup"><span data-stu-id="e0e08-145">Switch</span></span>|<span data-ttu-id="e0e08-146">Description</span><span class="sxs-lookup"><span data-stu-id="e0e08-146">Description</span></span>|  
|------------|-----------------|  
|`-f`|<span data-ttu-id="e0e08-147">해당 명령에서 서식 파일을 사용하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-147">Specifies that the command is using a format file..</span></span>|  
|`-k`|<span data-ttu-id="e0e08-148">작업 시 삽입된 열에 기본값이 지정되지 않고 빈 열이 Null 값을 보유하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-148">Specifies that empty columns should retain a null value during the operation, rather than have any default values for the columns inserted.</span></span>|  
|`-T`|<span data-ttu-id="e0e08-149">bcp 유틸리티가 트러스트된 연결을 통해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 연결되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-149">Specifies that the bcp utility connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with a trusted connection.</span></span>|  
  
 <span data-ttu-id="e0e08-150">Windows 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-150">At the Windows command prompt, enter.</span></span>  
  
```  
bcp AdventureWorks..MyTestDefaultCol2 in C:\MyTestEmptyField2-c.Dat -f C:\MyTestDefaultCol2-f-c.Fmt -k -T  
  
```  
  
#### <a name="using-bulk-insert-and-keeping-null-values"></a><span data-ttu-id="e0e08-151">BULK INSERT 사용 및 Null 값 유지</span><span class="sxs-lookup"><span data-stu-id="e0e08-151">Using BULK INSERT and Keeping Null Values</span></span>  
 <span data-ttu-id="e0e08-152">다음 예에서는 BULK INSERT 문에서 KEEPNULLS 옵션을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-152">The following example demonstrates how to use the KEEPNULLS option in a BULK INSERT statement.</span></span> <span data-ttu-id="e0e08-153">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 쿼리 편집기 같은 쿼리 도구에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-153">From a query tool, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT MyTestDefaultCol2  
   FROM 'C:\MyTestEmptyField2-c.Dat'  
   WITH (  
      DATAFILETYPE = 'char',  
      FIELDTERMINATOR = ',',  
      KEEPNULLS  
   );  
GO  
  
```  
  
## <a name="keeping-default-values-with-insert--select--from-openrowsetbulk"></a><span data-ttu-id="e0e08-154">INSERT를 사용 하 여 기본값 유지 ... SELECT \* FROM OPENROWSET (BULK ...)</span><span class="sxs-lookup"><span data-stu-id="e0e08-154">Keeping Default Values with INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>  
 <span data-ttu-id="e0e08-155">대량 로드 작업에 지정 되지 않은 모든 열은 기본적으로 NULL로 설정 됩니다. SELECT \* FROM OPENROWSET (BULK ...)를 선택 합니다. 그러나 데이터 파일의 빈 필드에 대해 해당 테이블 열에서 기본값 (있는 경우)을 사용 하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-155">By default, any columns that are not specified in the bulk-load operation are set to NULL by INSERT ... SELECT \* FROM OPENROWSET(BULK...). However, you can specify that for an empty field in the data file, the corresponding table column uses its default value (if any).</span></span> <span data-ttu-id="e0e08-156">기본값을 사용하려면 다음 테이블 힌트를 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="e0e08-156">To use default values, specify the following table hint:</span></span>  
  
|<span data-ttu-id="e0e08-157">명령</span><span class="sxs-lookup"><span data-stu-id="e0e08-157">Command</span></span>|<span data-ttu-id="e0e08-158">한정자</span><span class="sxs-lookup"><span data-stu-id="e0e08-158">Qualifier</span></span>|<span data-ttu-id="e0e08-159">한정자 유형</span><span class="sxs-lookup"><span data-stu-id="e0e08-159">Qualifier Type</span></span>|  
|-------------|---------------|--------------------|  
|<span data-ttu-id="e0e08-160">INSERT ... 선택 \* OPENROWSET (BULK)에서</span><span class="sxs-lookup"><span data-stu-id="e0e08-160">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>|<span data-ttu-id="e0e08-161">WITH(KEEPDEFAULTS)</span><span class="sxs-lookup"><span data-stu-id="e0e08-161">WITH(KEEPDEFAULTS)</span></span>|<span data-ttu-id="e0e08-162">테이블 힌트</span><span class="sxs-lookup"><span data-stu-id="e0e08-162">Table hint</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="e0e08-163">자세한 내용은 sql [&#41;&#40;INSERT ](/sql/t-sql/statements/insert-transact-sql)를 참조 하 고 transact-sql [&#41;&#40;Transact-sql ](/sql/t-sql/queries/select-transact-sql), [OPENROWSET &#40;transact-sql&#41;](/sql/t-sql/functions/openrowset-transact-sql)및 [테이블 힌트 &#40;transact-sql](/sql/t-sql/queries/hints-transact-sql-table)&#41;</span><span class="sxs-lookup"><span data-stu-id="e0e08-163">for more information, see [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql), [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql), [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql), and [Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)</span></span>  
  
### <a name="examples"></a><span data-ttu-id="e0e08-164">예</span><span class="sxs-lookup"><span data-stu-id="e0e08-164">Examples</span></span>  
 <span data-ttu-id="e0e08-165">다음 INSERT ... SELECT \* FROM OPENROWSET (BULK ...) 예제에서는 데이터를 대량으로 가져오고 기본값을 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-165">The following INSERT ... SELECT \* FROM OPENROWSET(BULK...) example bulk imports data and keeps the default values.</span></span>  
  
 <span data-ttu-id="e0e08-166">이 예를 실행하려면 **MyTestDefaultCol2** 예제 테이블과 `MyTestEmptyField2-c.Dat` 데이터 파일을 만들고 `MyTestDefaultCol2-f-c.Fmt`서식 파일을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-166">To run the examples, you need to create the **MyTestDefaultCol2** sample table, the `MyTestEmptyField2-c.Dat` data file, and use a format file, `MyTestDefaultCol2-f-c.Fmt`.</span></span> <span data-ttu-id="e0e08-167">이러한 예제를 만드는 방법은 이 항목의 앞 부분에 있는 "예제 테이블 및 데이터 파일"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e0e08-167">For information on creating these samples, see "Sample Table and Data File," earlier in this topic.</span></span>  
  
 <span data-ttu-id="e0e08-168">두 번째 테이블 열 **Col2**는 기본값을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-168">The second table column, **Col2**, has a default value.</span></span> <span data-ttu-id="e0e08-169">데이터 파일의 해당되는 필드에는 빈 문자열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-169">The corresponding field of the data file contains an empty string.</span></span> <span data-ttu-id="e0e08-170">INSERT ... SELECT \* FROM OPENROWSET (BULK ...)이 데이터 파일의 필드를 **MyTestDefaultCol2** 테이블에 가져옵니다. 기본적으로 NULL은 기본값 대신 **Col2** 에 삽입 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-170">When INSERT ... SELECT \* FROM OPENROWSET(BULK...) import the fields of this data file into the **MyTestDefaultCol2** table, by default, NULL is inserted into **Col2** instead of the default value.</span></span> <span data-ttu-id="e0e08-171">이 기본 동작을 통해 다음과 같은 결과가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-171">This default behavior produces the following result:</span></span>  
  
||||  
|-|-|-|  
|`1`|`NULL`|`DataField3`|  
|`2`|`NULL`|`DataField3`|  
  
 <span data-ttu-id="e0e08-172">"`Default value of Col2`" 대신 기본값인 "`NULL`" 를 삽입하려면 다음 예에서 예시하는 대로 KEEPDEFAULTS 테이블 힌트를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-172">To insert the default value, "`Default value of Col2`", instead of "`NULL`", you need to use KEEPDEFAULTS table hint, as demonstrated in the following example.</span></span> <span data-ttu-id="e0e08-173">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 쿼리 편집기 같은 쿼리 도구에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e08-173">From a query tool, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
INSERT INTO MyTestDefaultCol2  
    WITH (KEEPDEFAULTS)  
    SELECT *  
      FROM OPENROWSET(BULK  'C:\MyTestEmptyField2-c.Dat',  
      FORMATFILE='C:\MyTestDefaultCol2-f-c.Fmt'       
      ) as t1 ;  
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="e0e08-174">관련 작업</span><span class="sxs-lookup"><span data-stu-id="e0e08-174">Related Tasks</span></span>  
  
-   [<span data-ttu-id="e0e08-175">데이터 대량 가져오기 중 ID 값 유지&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e0e08-175">Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;</span></span>](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [<span data-ttu-id="e0e08-176">대량 내보내기 또는 가져오기를 위한 데이터 준비&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e0e08-176">Prepare Data for Bulk Export or Import &#40;SQL Server&#41;</span></span>](prepare-data-for-bulk-export-or-import-sql-server.md)  
  
 <span data-ttu-id="e0e08-177">**서식 파일을 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="e0e08-177">**To use a format file**</span></span>  
  
-   [<span data-ttu-id="e0e08-178">서식 파일 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e0e08-178">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="e0e08-179">서식 파일을 사용하여 데이터 대량 가져오기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e0e08-179">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="e0e08-180">서식 파일을 사용하여 테이블 열을 데이터 파일 필드에 매핑&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e0e08-180">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
-   [<span data-ttu-id="e0e08-181">서식 파일을 사용하여 데이터 필드 건너뛰기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e0e08-181">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="e0e08-182">서식 파일을 사용하여 테이블 열 건너뛰기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e0e08-182">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 <span data-ttu-id="e0e08-183">**대량 가져오기 또는 대량 내보내기를 위한 데이터 형식을 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="e0e08-183">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="e0e08-184">SQL Server 이전 버전으로부터 기본 및 문자 형식 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="e0e08-184">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [<span data-ttu-id="e0e08-185">문자 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e0e08-185">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="e0e08-186">네이티브 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e0e08-186">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="e0e08-187">유니코드 문자 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e0e08-187">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="e0e08-188">유니코드 네이티브 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e0e08-188">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 <span data-ttu-id="e0e08-189">**bcp를 사용할 때 데이터 형식의 호환 가능성을 지정하려면**</span><span class="sxs-lookup"><span data-stu-id="e0e08-189">**To specify data formats for compatibility when using bcp**</span></span>  
  
-   [<span data-ttu-id="e0e08-190">필드 및 행 종결자 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e0e08-190">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](specify-field-and-row-terminators-sql-server.md)  
  
-   [<span data-ttu-id="e0e08-191">bcp를 사용하여 데이터 파일에 접두사 길이 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e0e08-191">Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;</span></span>](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
-   [<span data-ttu-id="e0e08-192">bcp를 사용하여 파일 스토리지 유형 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e0e08-192">Specify File Storage Type by Using bcp &#40;SQL Server&#41;</span></span>](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="e0e08-193">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e0e08-193">See Also</span></span>  
 <span data-ttu-id="e0e08-194">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e0e08-194">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="e0e08-195">[OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e0e08-195">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="e0e08-196">[bcp 유틸리티](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="e0e08-196">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="e0e08-197">[BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e0e08-197">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 [<span data-ttu-id="e0e08-198">테이블 힌트&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e0e08-198">Table Hints &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/hints-transact-sql-table)  
  
  
