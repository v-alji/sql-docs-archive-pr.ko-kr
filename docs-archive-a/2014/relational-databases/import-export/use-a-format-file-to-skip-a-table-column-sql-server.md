---
title: 서식 파일을 사용하여 테이블 열 건너뛰기(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- skipping columns when importing
- format files [SQL Server], skipping columns
ms.assetid: 30e0e7b9-d131-46c7-90a4-6ccf77e3d4f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 153ef21209ff4261020e26aca3bc52d28dc852a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661655"
---
# <a name="use-a-format-file-to-skip-a-table-column-sql-server"></a><span data-ttu-id="0076e-102">서식 파일을 사용하여 테이블 열 건너뛰기(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0076e-102">Use a Format File to Skip a Table Column (SQL Server)</span></span>
  <span data-ttu-id="0076e-103">이 항목에서는 서식 파일에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-103">This topic describes format files.</span></span> <span data-ttu-id="0076e-104">필드가 데이터 파일에 없는 경우 서식 파일을 사용하여 테이블 열 가져오기를 건너뛸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-104">You can use a format file to skip importing a table column when the field does not exist in the data file.</span></span> <span data-ttu-id="0076e-105">건너뛴 열이 Null을 허용하거나 기본값을 가질 경우에만 데이터 파일에 테이블의 열 수보다 적은 수의 필드가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-105">A data file can contain fewer fields than the number of columns in the table only if the skipped columns are nullable and/or have default value.</span></span>

## <a name="sample-table-and-data-file"></a><span data-ttu-id="0076e-106">예제 테이블 및 데이터 파일</span><span class="sxs-lookup"><span data-stu-id="0076e-106">Sample Table and Data File</span></span>
 <span data-ttu-id="0076e-107">다음 예에서는 `myTestSkipCol` dbo [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 스키마의 **예제 데이터베이스에** 이라는 테이블이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-107">The following examples require a table named `myTestSkipCol` in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample database under the **dbo** schema.</span></span> <span data-ttu-id="0076e-108">이 테이블을 다음과 같이 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-108">Create this table as follows:</span></span>

```
USE AdventureWorks2012;
GO
CREATE TABLE myTestSkipCol 
   (
   Col1 smallint,
   Col2 nvarchar(50) NULL,
   Col3 nvarchar(50) not NULL
   );
GO
```

 <span data-ttu-id="0076e-109">다음 예에서는 해당 테이블에 3개의 열이 있지만 두 개의 필드만 있는 `myTestSkipCol2.dat`라는 예제 데이터 파일을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-109">The following examples use a sample data file, `myTestSkipCol2.dat`, which contains only two fields, although the corresponding table contains three columns:</span></span>

```
1,DataForColumn3
1,DataForColumn3
1,DataForColumn3

```

 <span data-ttu-id="0076e-110">`myTestSkipCol2.dat` 의 데이터를 `myTestSkipCol` 테이블로 대량 가져오려면 서식 파일이 첫 번째 데이터 필드를 `Col1`에 매핑하고 `Col3`는 건너뛴 채 두 번째 필드를 `Col2`에 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-110">To bulk import data from `myTestSkipCol2.dat` into the `myTestSkipCol` table, the format file must map the first data field to `Col1`, the second field to `Col3`, skipping `Col2`.</span></span>

## <a name="using-a-non-xml-format-file"></a><span data-ttu-id="0076e-111">비 XML 서식 파일 사용</span><span class="sxs-lookup"><span data-stu-id="0076e-111">Using a Non-XML Format File</span></span>
 <span data-ttu-id="0076e-112">비 XML 서식 파일을 수정하여 테이블 열을 건너뛸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-112">You can modify a non-XML format file to skip a table column.</span></span> <span data-ttu-id="0076e-113">이렇게 하려면 일반적으로 **bcp** 유틸리티를 사용하여 기본 비 XML 서식 파일을 만들고 텍스트 편집기에서 기본 파일을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-113">Typically, this involves using the **bcp** utility to create a default non-XML format file and the modifying the default file in a text editor.</span></span> <span data-ttu-id="0076e-114">수정된 서식 파일은 기존의 각 필드를 해당하는 테이블 열로 매핑하고 건너뛸 테이블 열을 나타내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-114">The modified format file must map each existing fields to its corresponding table column and indicate which table column or columns to skip.</span></span> <span data-ttu-id="0076e-115">기본 비 XML 데이터 파일을 수정할 수 있는 두 가지 다른 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-115">Two alternatives exist for modifying a default non-XML data file.</span></span> <span data-ttu-id="0076e-116">각 방법은 데이터 필드가 데이터 파일에 없고 데이터가 해당 테이블 열에 삽입되지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-116">Either alternative indicates that the data field does not exist in the data file and that no data will be inserted into the corresponding table column.</span></span>

### <a name="creating-a-default-non-xml-format-file"></a><span data-ttu-id="0076e-117">기본 비 XML 서식 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="0076e-117">Creating a Default Non-XML Format File</span></span>
 <span data-ttu-id="0076e-118">이 항목에서는 다음 `myTestSkipCol` bcp **명령을 사용하여** 예제 테이블에 대해 생성된 기본 비 XML 서식 파일을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-118">This topic uses the default non-XML format file that was created for the `myTestSkipCol` sample table by using the following **bcp** command:</span></span>

```
bcp AdventureWorks2012..myTestSkipCol format nul -f myTestSkipCol_Default.fmt -c -T
```

 <span data-ttu-id="0076e-119">위 명령은 `myTestSkipCol_Default.fmt`라는 비 XML 서식 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-119">The previous command creates a non-XML format file, `myTestSkipCol_Default.fmt`.</span></span> <span data-ttu-id="0076e-120">이 서식 파일은 *bcp* 에서 생성되는 형식이므로 **기본 서식 파일**이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-120">This format file is called a *default format file* because it is the form generated by **bcp**.</span></span> <span data-ttu-id="0076e-121">일반적으로 기본 서식 파일은 데이터 파일 필드와 테이블 열 간의 일 대 일 대응을 나타내는 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-121">Typically, a default format file describes a one-to-one correspondence between data-file fields and table columns.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="0076e-122">연결할 서버 인스턴스의 이름을 지정해야 할 수 있으며</span><span class="sxs-lookup"><span data-stu-id="0076e-122">You might have to specify the name of the server instance to which you are connecting.</span></span> <span data-ttu-id="0076e-123">사용자 이름과 암호를 지정해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-123">Also, you might have to specify the user name and password.</span></span> <span data-ttu-id="0076e-124">자세한 내용은 [bcp Utility](../../tools/bcp-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0076e-124">For more information, see [bcp Utility](../../tools/bcp-utility.md).</span></span>

 <span data-ttu-id="0076e-125">다음 그림에서는 이 예제 기본 서식 파일의 값을 보여 주며</span><span class="sxs-lookup"><span data-stu-id="0076e-125">The following illustration shows the values in this sample default format files.</span></span> <span data-ttu-id="0076e-126">각 서식 파일 필드의 이름도 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-126">The illustration also shows the name of each format-file field.</span></span>

 <span data-ttu-id="0076e-127">![myTestSkipCol에 대한 비 XML 형식 기본 파일](../../database-engine/media/mytestskipcol-f-c-default-fmt.gif "myTestSkipCol에 대한 비 XML 형식 기본 파일")</span><span class="sxs-lookup"><span data-stu-id="0076e-127">![default non-XML format file for myTestSkipCol](../../database-engine/media/mytestskipcol-f-c-default-fmt.gif "default non-XML format file for myTestSkipCol")</span></span>

> [!NOTE]
>  <span data-ttu-id="0076e-128">서식 파일 필드에 대한 자세한 내용은 [비 XML 서식 파일&#40;SQL Server&#41;](xml-format-files-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0076e-128">For more information about the format-file fields, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>

### <a name="methods-for-modifying-a-non-xml-format-file"></a><span data-ttu-id="0076e-129">비 XML 서식 파일 수정 방법</span><span class="sxs-lookup"><span data-stu-id="0076e-129">Methods for Modifying a Non-XML Format File</span></span>
 <span data-ttu-id="0076e-130">테이블 열을 건너뛰려면 기본 비 XML 서식 파일을 편집하고 다음 방법 중 하나를 사용하여 해당 파일을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-130">To skip a table column, edit the default non-XML format file and modify the file by using one of the following alternative methods:</span></span>

-   <span data-ttu-id="0076e-131">일반적인 방법에는 3가지 기본 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-131">The preferred method involves three basic steps.</span></span> <span data-ttu-id="0076e-132">먼저 데이터 파일에서 누락된 필드를 나타내는 모든 서식 파일 행을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-132">First, delete any format-file row that describes a field that is missing from the data file.</span></span> <span data-ttu-id="0076e-133">그런 다음 삭제된 행 뒤에 오는 각 서식 파일 행의 "호스트 파일 필드 순서" 값을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-133">Then, reduce the "Host file field order" value of each format-file row that follows a deleted row.</span></span> <span data-ttu-id="0076e-134">목표는 데이터 파일에서 각 데이터 필드의 실제 위치를 반영하는 1부터 *n*까지의 순차적인 "호스트 파일 필드 순서" 값을 얻는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-134">The goal is sequential "Host file field order" values, 1 through *n*, that reflect the actual position of each data field in the data file.</span></span> <span data-ttu-id="0076e-135">마지막으로 데이터 파일의 실제 필드 수를 반영하도록 "열 수" 필드의 값을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-135">Finally, reduce the value in the "Number of columns" field to reflect the actual number of fields in the data file.</span></span>

     <span data-ttu-id="0076e-136">다음 예는 이 항목의 앞부분에 나오는 "기본 비 XML 서식 파일 만들기"에서 생성된 `myTestSkipCol` 테이블에 대한 기본 서식 파일을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-136">The following example is based on the default format file for the `myTestSkipCol` table, which is created in "Creating a Default Non-XML Format File," earlier in this topic.</span></span> <span data-ttu-id="0076e-137">수정된 이 서식 파일은 첫 번째 데이터 필드를 `Col1`에 매핑하고 `Col2`를 건너뛴 다음 두 번째 데이터 필드를 `Col3`에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-137">This modified format file maps the first data field to `Col1`, skips `Col2`, and maps the second data field to `Col3`.</span></span> <span data-ttu-id="0076e-138">`Col2` 의 행은 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-138">The row for `Col2` has been deleted.</span></span> <span data-ttu-id="0076e-139">기타 수정 내용은 굵게 표시되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-139">Other modifications are indicated in bold:</span></span>

    ```
    9.0
    2
    1       SQLCHAR       0       7       "\t"     1     Col1         ""
    2       SQLCHAR       0       100     "\r\n"   3     Col3         SQL_Latin1_General_CP1_CI_AS
    ```

-   <span data-ttu-id="0076e-140">테이블 열을 건너뛰기 위해 테이블 열에 해당하는 서식 파일 행의 정의를 수정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-140">Alternatively, to skip a table column, you can modify the definition of the format-file row that corresponds to the table column.</span></span> <span data-ttu-id="0076e-141">이 서식 파일 행에서 "접두사 길이", "호스트 파일 데이터 길이" 및 "서버 열 순서" 값은 0으로 설정해야 하며</span><span class="sxs-lookup"><span data-stu-id="0076e-141">In this format-file row, the "prefix length," "host file data length," and "server column order" values must be set to 0.</span></span> <span data-ttu-id="0076e-142">"종결자" 및 "열 데이터 정렬" 필드는 ""(NULL)로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-142">Also, the "terminator" and "column collation" fields must be set to "" (NULL).</span></span>

     <span data-ttu-id="0076e-143">"실제 열 이름이 필요하지 않더라도 "서버 열 이름" 값에는 공백이 아닌 문자열이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-143">The "server column name" value requires a nonblank string, though the actual column name is not necessary.</span></span> <span data-ttu-id="0076e-144">나머지 서식 필드에는 해당 기본값이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-144">The remaining format fields require their default values.</span></span>

     <span data-ttu-id="0076e-145">다음 예도 `myTestSkipCol` 테이블에 대한 기본 서식 파일에서 파생된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-145">The following example is also derived from the default format file for the `myTestSkipCol` table.</span></span> <span data-ttu-id="0076e-146">0 또는 NULL이어야 하는 값은 굵게 표시되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-146">Values that must be 0 or NULL are indicated in bold.</span></span>

    ```
    9.0
    3
    1       SQLCHAR       0       7       "\t"     1     Col1         ""
    2       SQLCHAR       00""0     Col2         ""
    3       SQLCHAR       0       100     "\r\n"   3     Col3         SQL_Latin1_General_CP1_CI_AS
    ```

### <a name="examples"></a><span data-ttu-id="0076e-147">예</span><span class="sxs-lookup"><span data-stu-id="0076e-147">Examples</span></span>
 <span data-ttu-id="0076e-148">다음 예도 이 항목의 앞부분에 나오는 "예제 테이블 및 데이터 파일"에서 생성된 `myTestSkipCol` 예제 테이블과 `myTestSkipCol2.dat` 예제 데이터 파일을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-148">The following examples are also based on the `myTestSkipCol` sample table and the `myTestSkipCol2.dat` sample data file that are created in "Sample Table and Data File," earlier in this topic.</span></span>

#### <a name="using-bulk-insert"></a><span data-ttu-id="0076e-149">BULK INSERT 사용</span><span class="sxs-lookup"><span data-stu-id="0076e-149">Using BULK INSERT</span></span>
 <span data-ttu-id="0076e-150">이 예는 이 항목의 앞부분에 나오는 "비 XML 서식 파일 수정 방법"에서 생성된 수정 비 XML 서식 파일 중 하나를 사용하여 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-150">This example works by using either of the modified non-XML format files created in "Methods for Modifying a Non-XML Format File," earlier in this topic.</span></span> <span data-ttu-id="0076e-151">이 예에서 수정된 서식 파일의 이름은 `C:\myTestSkipCol2.fmt`입니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-151">In this example, the modified format file is named `C:\myTestSkipCol2.fmt`.</span></span> <span data-ttu-id="0076e-152">`BULK INSERT` 를 사용하여 `myTestSkipCol2.dat` 데이터 파일을 대량으로 가져오려면 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-152">To use `BULK INSERT` to bulk import the `myTestSkipCol2.dat` data file, in the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>

```
USE AdventureWorks2012;
GO
BULK INSERT myTestSkipCol 
   FROM 'C:\myTestSkipCol2.dat' 
   WITH (FORMATFILE = 'C:\myTestSkipCol2.fmt');
GO
SELECT * FROM myTestSkipCol;
GO
```

## <a name="using-an-xml-format-file"></a><span data-ttu-id="0076e-153">XML 서식 파일 사용</span><span class="sxs-lookup"><span data-stu-id="0076e-153">Using an XML Format File</span></span>
 <span data-ttu-id="0076e-154">XML 서식 파일을 사용하면 **bcp** 명령이나 BULK INSERT 문을 사용하여 테이블로 데이터를 직접 가져올 때 열을 건너뛸 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-154">With an XML format file, you cannot skip a column when you are importing directly into a table by using a **bcp** command or a BULK INSERT statement.</span></span> <span data-ttu-id="0076e-155">그러나 테이블의 마지막 열을 제외하고 모든 열로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-155">However, you can import into all but the last column of a table.</span></span> <span data-ttu-id="0076e-156">마지막 열을 제외하고 모든 열을 건너뛰어야 하는 경우 데이터 파일에 있는 열만 포함된 대상 테이블의 뷰를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-156">If you have to skip any but the last column, you must create a view of the target table that contains only the columns contained in the data file.</span></span> <span data-ttu-id="0076e-157">그런 다음 해당 파일의 데이터를 뷰로 대량 가져오기를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-157">Then, you can bulk import data from that file into the view.</span></span>

 <span data-ttu-id="0076e-158">XML 서식 파일을 통해 OPENROWSET(BULK...)을 사용하여 테이블 열을 건너뛰려면 SELECT 목록과 대상 테이블에 있는 명시적인 열 목록을 다음과 같이 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-158">To use an XML format file to skip a table column by using OPENROWSET(BULK...), you have to provide explicit list of columns in the select list and also in the target table, as follows:</span></span>

 <span data-ttu-id="0076e-159">INSERT ...<column_list> SELECT <column_list> FROM OPENROWSET(BULK...)</span><span class="sxs-lookup"><span data-stu-id="0076e-159">INSERT ...<column_list> SELECT <column_list> FROM OPENROWSET(BULK...)</span></span>

### <a name="creating-a-default-xml-format-file"></a><span data-ttu-id="0076e-160">기본 XML 서식 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="0076e-160">Creating a Default XML Format File</span></span>
 <span data-ttu-id="0076e-161">수정된 서식 파일의 예는 이 항목의 앞부분에 나오는 "예제 테이블 및 데이터 파일"에서 생성된 `myTestSkipCol` 예제 테이블과 데이터 파일을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-161">The examples of modified format files are based on the `myTestSkipCol` sample table and data file that are created in "Sample Table and Data File," earlier in this topic.</span></span> <span data-ttu-id="0076e-162">다음 **bcp** 명령은 `myTestSkipCol` 테이블에 대한 기본 XML 서식 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-162">The following **bcp** command creates a default XML format file for the `myTestSkipCol` table:</span></span>

```
bcp AdventureWorks2012..myTestSkipCol format nul -f myTestSkipCol_Default.xml -c -x -T
```

 <span data-ttu-id="0076e-163">결과로 생성된 기본 비 XML 서식 파일은 다음과 같이 데이터 파일 필드와 테이블 열 간의 일 대 일 대응을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-163">The resulting default non-XML format file describes a one-to-one correspondence between data-file fields and table columns, as follows:</span></span>

```
<?xml version="1.0"?>
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
 <RECORD>
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t" MAX_LENGTH="7"/>
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\t" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>
  <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>
 </RECORD>
 <ROW>
  <COLUMN SOURCE="1" NAME="Col1" xsi:type="SQLSMALLINT"/>
  <COLUMN SOURCE="2" NAME="Col2" xsi:type="SQLNVARCHAR"/>
  <COLUMN SOURCE="3" NAME="Col3" xsi:type="SQLNVARCHAR"/>
 </ROW>
</BCPFORMAT>
```

> [!NOTE]
>  <span data-ttu-id="0076e-164">XML 서식 파일의 구조에 대한 자세한 내용은 [XML 서식 파일&#40;SQL Server&#41;](xml-format-files-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0076e-164">For information about the structure of XML format files, see [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>

### <a name="examples"></a><span data-ttu-id="0076e-165">예</span><span class="sxs-lookup"><span data-stu-id="0076e-165">Examples</span></span>
 <span data-ttu-id="0076e-166">이 섹션의 예에서는 이 섹션의 예에서는 이 항목의 앞부분에 나오는 "예제 테이블 및 데이터 파일"에서 생성된 `myTestSkipCol` 예제 테이블과 `myTestSkipCol2.dat` 예제 데이터 파일을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-166">The examples in this section use the `myTestSkipCol` sample table and the `myTestSkipCol2.dat` sample data file that are created in "Sample Table and Data File," earlier in this topic.</span></span> <span data-ttu-id="0076e-167">`myTestSkipCol2.dat` 의 데이터를 `myTestSkipCol` 테이블로 가져오기 위해 이 예에서는 수정된 XML 서식 파일인 `myTestSkipCol2-x.xml`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-167">To import the data from `myTestSkipCol2.dat` into the `myTestSkipCol` table, the examples use the following modified XML format file, `myTestSkipCol2-x.xml`.</span></span> <span data-ttu-id="0076e-168">이 예는 이 항목의 앞부분에 나오는 "기본 XML 서식 파일 만들기"에서 생성된 서식 파일을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-168">This is based on the format file that is created in "Creating a Default XML Format File," earlier in this topic.</span></span>

```
<?xml version="1.0"?>
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
 <RECORD>
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>
 </RECORD>
 <ROW>
  <COLUMN SOURCE="1" NAME="Col1" xsi:type="SQLSMALLINT"/>
  <COLUMN SOURCE="2" NAME="Col3" xsi:type="SQLNVARCHAR"/>
 </ROW>
</BCPFORMAT>
```

#### <a name="using-openrowsetbulk"></a><span data-ttu-id="0076e-169">OPENROWSET(BULK...) 사용</span><span class="sxs-lookup"><span data-stu-id="0076e-169">Using OPENROWSET(BULK...)</span></span>
 <span data-ttu-id="0076e-170">다음 예에서는 `OPENROWSET` 대량 행 집합 공급자와 `myTestSkipCol2.xml` 서식 파일을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-170">The following example uses the `OPENROWSET` bulk rowset provider and the `myTestSkipCol2.xml` format file.</span></span> <span data-ttu-id="0076e-171">또한 `myTestSkipCol2.dat` 데이터 파일을 `myTestSkipCol` 테이블로 대량 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-171">The example bulk imports the `myTestSkipCol2.dat` data file into the `myTestSkipCol` table.</span></span> <span data-ttu-id="0076e-172">이 문에는 필요에 따라 SELECT 목록과 대상 테이블의 명시적인 열 목록이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-172">The statement contains an explicit list of columns in the select list and also in the target table, as required.</span></span>

 <span data-ttu-id="0076e-173">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-173">In the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>

```
USE AdventureWorks2012;
GO
INSERT INTO myTestSkipCol
  (Col1,Col3)
    SELECT Col1,Col3
      FROM  OPENROWSET(BULK  'C:\myTestSkipCol2.Dat',
      FORMATFILE='C:\myTestSkipCol2.Xml'  
       ) as t1 ;
GO
```

#### <a name="using-bulk-import-on-a-view"></a><span data-ttu-id="0076e-174">뷰에서 BULK IMPORT 사용</span><span class="sxs-lookup"><span data-stu-id="0076e-174">Using BULK IMPORT on a View</span></span>
 <span data-ttu-id="0076e-175">다음 예에서는 `v_myTestSkipCol` 테이블에 `myTestSkipCol` 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-175">The following example creates the `v_myTestSkipCol` on the `myTestSkipCol` table.</span></span> <span data-ttu-id="0076e-176">이 뷰는 두 번째 테이블 열인 `Col2`를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-176">This view skips the second table column, `Col2`.</span></span> <span data-ttu-id="0076e-177">그런 다음 이 예에서는 `BULK INSERT` 를 사용하여 `myTestSkipCol2.dat` 데이터 파일을 이 뷰로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-177">The example then uses `BULK INSERT` to import the `myTestSkipCol2.dat` data file into this view.</span></span>

 <span data-ttu-id="0076e-178">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0076e-178">In the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>

```
CREATE VIEW v_myTestSkipCol AS
    SELECT Col1,Col3
    FROM myTestSkipCol;
GO

USE AdventureWorks2012;
GO
BULK INSERT v_myTestSkipCol
FROM 'C:\myTestSkipCol2.dat'
WITH (FORMATFILE='C:\myTestSkipCol2.xml');
GO
```

## <a name="see-also"></a><span data-ttu-id="0076e-179">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0076e-179">See Also</span></span>
 <span data-ttu-id="0076e-180">[Bcp 유틸리티](../../tools/bcp-utility.md) [BULK INSERT &#40;transact-sql&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) [OPENROWSET &#40;transact-sql&#41;](/sql/t-sql/functions/openrowset-transact-sql) 서식 파일 [을 사용 하](use-a-format-file-to-skip-a-data-field-sql-server.md) 여 [테이블 열을 데이터 파일 필드에 매핑](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md) &#40;SQL Server 서식 파일을 사용 하 여&#41;&#40;데이터 [를 대량으로 가져오기](use-a-format-file-to-bulk-import-data-sql-server.md) SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0076e-180">[bcp Utility](../../tools/bcp-utility.md) [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) [Use a Format File to Skip a Data Field &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md) [Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md) [Use a Format File to Bulk Import Data &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)</span></span>


