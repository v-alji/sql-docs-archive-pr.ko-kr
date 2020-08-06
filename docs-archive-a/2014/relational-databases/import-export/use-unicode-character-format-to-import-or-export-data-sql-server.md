---
title: 유니코드 문자 형식을 사용하여 데이터 가져오기 및 내보내기(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- data formats [SQL Server], Unicode character
- Unicode [SQL Server], bulk importing and exporting
ms.assetid: 74342a11-c1c0-4746-b482-7f3537744a70
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 520ce1b4eed8dc11d6d3fe038969257aea1e90fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741032"
---
# <a name="use-unicode-character-format-to-import-or-export-data-sql-server"></a><span data-ttu-id="03eb0-102">유니코드 문자 형식을 사용하여 데이터 가져오기 및 내보내기(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="03eb0-102">Use Unicode Character Format to Import or Export Data (SQL Server)</span></span>
  <span data-ttu-id="03eb0-103">확장/DBCS 문자를 포함하는 데이터 파일을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 여러 인스턴스 간에 대량 데이터 전송을 수행하는 경우에는 유니코드 문자 형식을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-103">Unicode character format is recommended for bulk transfer of data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a data file that contains extended/DBCS characters.</span></span> <span data-ttu-id="03eb0-104">유니코드 문자 데이터 형식을 사용하면 작업을 수행 중인 클라이언트에서 사용되는 코드 페이지와 다른 코드 페이지를 사용하여 서버에서 데이터를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-104">The Unicode character data format allows data to be exported from a server by using a code page that differs from the code page used by the client that is performing the operation.</span></span> <span data-ttu-id="03eb0-105">이런 경우 유니코드 문자 형식을 사용하면 다음과 같은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-105">In such cases, use of Unicode character format has the following advantages:</span></span>  
  
-   <span data-ttu-id="03eb0-106">원본 및 대상 데이터가 유니코드 데이터 형식이면 유니코드 문자 형식을 사용하여 모든 문자 데이터를 보존할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-106">If the source and destination data are Unicode data types, use of Unicode character format preserves all of the character data.</span></span>  
  
-   <span data-ttu-id="03eb0-107">원본 및 대상 데이터가 유니코드 데이터 형식이 아니면 유니코드 문자 형식을 사용하여 원본 데이터에 있지만 대상에서 표현할 수 없는 확장 문자의 손실을 최소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-107">if the source and destination data are not Unicode data types, use of Unicode character format minimizes the loss of extended characters in the source data that cannot be represented at the destination.</span></span>  
  
 <span data-ttu-id="03eb0-108">유니코드 문자 형식 데이터 파일은 유니코드 파일의 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-108">Unicode character format data files follow the conventions for Unicode files.</span></span> <span data-ttu-id="03eb0-109">파일의 처음 두 바이트는 16진수 0xFFFE입니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-109">The first two bytes of the file are hexadecimal numbers, 0xFFFE.</span></span> <span data-ttu-id="03eb0-110">이 두 바이트는 바이트 순서 표시로서 제공되며 높은 순서 바이트가 파일의 처음에 저장될지 마지막에 저장될지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-110">These bytes serve as byte-order marks, specifying whether the high-order byte is stored first or last in the file.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="03eb0-111">유니코드 문자 데이터 파일에 서식 파일을 사용하려면 모든 입력 필드가 유니코드 텍스트 문자열(고정 크기 또는 문자 종료 유니코드 문자열)이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-111">For a format file to work with a Unicode character data file, all the input fields must be Unicode text strings (that is, either fixed-size or character-terminated Unicode strings).</span></span>  
  
 <span data-ttu-id="03eb0-112">유니코드 문자 형식 데이터 파일에 저장되어 있는 `sql_variant` 데이터는 데이터가 `nchar` 데이터 대신 `char`로 저장된다는 것을 제외하면 문자 형식 데이터 파일과 같은 방식으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-112">The `sql_variant` data that is stored in a Unicode character-format data file operates in the same way it operates in a character-format data file, except that the data is stored as `nchar` instead of `char` data.</span></span> <span data-ttu-id="03eb0-113">문자 형식에 대한 자세한 내용은 [Collation and Unicode Support](../collations/collation-and-unicode-support.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="03eb0-113">For more information about character format, see [Collation and Unicode Support](../collations/collation-and-unicode-support.md).</span></span>  
  
 <span data-ttu-id="03eb0-114">유니코드 문자 형식으로 제공되는 기본값과 다른 필드 또는 행 종결자를 사용하려면 [필드 및 행 종결자 지정&#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="03eb0-114">To use a field or row terminator other than the default that is provided with Unicode character format, see [Specify Field and Row Terminators &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).</span></span>  
  
## <a name="command-options-for-unicode-character-format"></a><span data-ttu-id="03eb0-115">유니코드 문자 형식의 명령 옵션</span><span class="sxs-lookup"><span data-stu-id="03eb0-115">Command Options for Unicode Character Format</span></span>  
 <span data-ttu-id="03eb0-116">**Bcp**, BULK INSERT 또는 INSERT ...를 사용 하 여 테이블에 유니코드 문자 형식 데이터를 가져올 수 있습니다. SELECT \* FROM OPENROWSET (BULK ...)를 선택 합니다. **Bcp** 명령 또는 BULK INSERT 문의 경우 명령줄에서 데이터 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-116">You can import Unicode character format data into a table using **bcp**, BULK INSERT or INSERT ... SELECT \* FROM OPENROWSET(BULK...). For a **bcp** command or BULK INSERT statement, you can specify the data format on the command line.</span></span> <span data-ttu-id="03eb0-117">INSERT ... SELECT \* FROM OPENROWSET(BULK...) 문의 경우 서식 파일에서 데이터 형식을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-117">For an INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement, you must specify the data format in a format file.</span></span>  
  
 <span data-ttu-id="03eb0-118">다음 명령줄 옵션에서 유니코드 문자 형식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-118">Unicode character format is supported by the following command line options:</span></span>  
  
|<span data-ttu-id="03eb0-119">명령</span><span class="sxs-lookup"><span data-stu-id="03eb0-119">Command</span></span>|<span data-ttu-id="03eb0-120">옵션</span><span class="sxs-lookup"><span data-stu-id="03eb0-120">Option</span></span>|<span data-ttu-id="03eb0-121">설명</span><span class="sxs-lookup"><span data-stu-id="03eb0-121">Description</span></span>|  
|-------------|------------|-----------------|  
|<span data-ttu-id="03eb0-122">**bcp**</span><span class="sxs-lookup"><span data-stu-id="03eb0-122">**bcp**</span></span>|<span data-ttu-id="03eb0-123">**-w**</span><span class="sxs-lookup"><span data-stu-id="03eb0-123">**-w**</span></span>|<span data-ttu-id="03eb0-124">유니코드 문자 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-124">Uses the Unicode character format.</span></span>|  
|<span data-ttu-id="03eb0-125">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="03eb0-125">BULK INSERT</span></span>|<span data-ttu-id="03eb0-126">DATAFILETYPE **= '** widechar **'**</span><span class="sxs-lookup"><span data-stu-id="03eb0-126">DATAFILETYPE **='** widechar **'**</span></span>|<span data-ttu-id="03eb0-127">대량으로 데이터를 가져올 때 유니코드 문자 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-127">Uses Unicode character format when bulk importing data.</span></span>|  
  
 <span data-ttu-id="03eb0-128">자세한 내용은 [bcp 유틸리티](../../tools/bcp-utility.md), [BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) 또는 [OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="03eb0-128">For more information, see [bcp Utility](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), or [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="03eb0-129">서식 파일에서 필드 단위로 서식을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-129">Alternatively, you can specify formatting on a per-field basis in a format file.</span></span> <span data-ttu-id="03eb0-130">자세한 내용은 [데이터를 가져오거나 내보내기 위한 서식 파일&#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="03eb0-130">For more information, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="03eb0-131">예</span><span class="sxs-lookup"><span data-stu-id="03eb0-131">Examples</span></span>  
 <span data-ttu-id="03eb0-132">다음 예에서는 **bcp** 를 사용하여 유니코드 문자 데이터를 대량으로 내보내는 방법과 BULK INSERT를 사용하여 동일한 데이터를 대량으로 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-132">The following examples demonstrate how to bulk export Unicode character data using **bcp** and to bulk import the same data using BULK INSERT.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="03eb0-133">예제 테이블</span><span class="sxs-lookup"><span data-stu-id="03eb0-133">Sample Table</span></span>  
 <span data-ttu-id="03eb0-134">이 예에서는 `myTestUniCharData` 스키마의 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 예제 데이터베이스에 생성된 `dbo` 라는 테이블이 필요하며</span><span class="sxs-lookup"><span data-stu-id="03eb0-134">The examples require that a table named `myTestUniCharData` table be created in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample database under the `dbo` schema.</span></span> <span data-ttu-id="03eb0-135">예를 실행하려면 이 테이블을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-135">Before you can run the examples, you must create this table.</span></span> <span data-ttu-id="03eb0-136">이 테이블을 만들려면 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-136">To create this table, in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestUniCharData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 <span data-ttu-id="03eb0-137">이 테이블을 채우고 결과 내용을 확인하려면 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-137">To populate this table and view the resulting contents execute the following statements:</span></span>  
  
```  
INSERT INTO myTestUniCharData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3')   
        ,(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestUniCharData;  
  
```  
  
### <a name="using-bcp-to-bulk-export-unicode-character-data"></a><span data-ttu-id="03eb0-138">bcp를 사용하여 유니코드 문자 데이터 대량 내보내기</span><span class="sxs-lookup"><span data-stu-id="03eb0-138">Using bcp to Bulk Export Unicode Character Data</span></span>  
 <span data-ttu-id="03eb0-139">테이블의 데이터를 데이터 파일로 내보내려면 **out** 옵션 및 다음 한정자가 있는 **bcp** 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-139">To export data from the table to the data file, use **bcp** with the **out** option and the following qualifiers:</span></span>  
  
|<span data-ttu-id="03eb0-140">한정자</span><span class="sxs-lookup"><span data-stu-id="03eb0-140">Qualifiers</span></span>|<span data-ttu-id="03eb0-141">Description</span><span class="sxs-lookup"><span data-stu-id="03eb0-141">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="03eb0-142">**-w**</span><span class="sxs-lookup"><span data-stu-id="03eb0-142">**-w**</span></span>|<span data-ttu-id="03eb0-143">유니코드 문자 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-143">Specifies Unicode character format.</span></span>|  
|<span data-ttu-id="03eb0-144">**-t** `,`</span><span class="sxs-lookup"><span data-stu-id="03eb0-144">**-t** `,`</span></span>|<span data-ttu-id="03eb0-145">쉼표(`,`)를 필드 종결자로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-145">Specifies a comma (`,`) as the field terminator.</span></span><br /><br /> <span data-ttu-id="03eb0-146">참고: 기본 필드 종결자는 탭 유니코드 문자 (\t)입니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-146">Note: The default field terminator is the tab Unicode character (\t).</span></span> <span data-ttu-id="03eb0-147">자세한 내용은 [필드 및 행 종결자 지정&#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="03eb0-147">For more information, see [Specify Field and Row Terminators &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).</span></span>|  
|<span data-ttu-id="03eb0-148">**-T**</span><span class="sxs-lookup"><span data-stu-id="03eb0-148">**-T**</span></span>|<span data-ttu-id="03eb0-149">**bcp** 유틸리티가 통합 보안을 사용하는 트러스트된 연결을 통해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로 연결되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-149">Specifies that the **bcp** utility connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with a trusted connection using integrated security.</span></span> <span data-ttu-id="03eb0-150">**-T** 를 지정하지 않은 경우 성공적으로 로그인하려면 **-U** 와 **-P** 를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-150">If **-T** is not specified, you need to specify **-U** and **-P** to successfully log in.</span></span>|  
  
 <span data-ttu-id="03eb0-151">다음 예에서는 `myTestUniCharData` 테이블의 유니코드 문자 형식 데이터를 필드 종결자로 쉼표(`myTestUniCharData-w.Dat`)를 사용하는 새 데이터 파일인 `,`로 대량으로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-151">The following example bulk exports data in Unicode character format from the `myTestUniCharData` table into a new data file named `myTestUniCharData-w.Dat` data file that uses the comma (`,`) as the field terminator.</span></span> <span data-ttu-id="03eb0-152">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 명령 프롬프트에 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-152">At the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks2012..myTestUniCharData out C:\myTestUniCharData-w.Dat -w -t, -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-unicode-character-data"></a><span data-ttu-id="03eb0-153">BULK INSERT를 사용하여 유니코드 문자 데이터 대량 가져오기</span><span class="sxs-lookup"><span data-stu-id="03eb0-153">Using BULK INSERT to Bulk Import Unicode Character Data</span></span>  
 <span data-ttu-id="03eb0-154">다음 예에서는 `BULK INSERT`를 사용하여 `myTestUniCharData-w.Dat` 데이터 파일의 데이터를 `myTestUniCharData` 테이블로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-154">The following example uses `BULK INSERT` to import the data in the `myTestUniCharData-w.Dat` data file into the `myTestUniCharData` table.</span></span> <span data-ttu-id="03eb0-155">기본 필드 종결자(`,`)가 아닌 필드 종결자는 문에서 선언해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-155">The nondefault field terminator (`,`) must be declared in the statement.</span></span> <span data-ttu-id="03eb0-156">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="03eb0-156">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
BULK INSERT myTestUniCharData   
   FROM 'C:\myTestUniCharData-w.Dat'   
   WITH (  
      DATAFILETYPE='widechar',  
      FIELDTERMINATOR=','  
   );   
GO  
SELECT Col1,Col2,Col3 FROM myTestUniCharData;  
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="03eb0-157">관련 작업</span><span class="sxs-lookup"><span data-stu-id="03eb0-157">Related Tasks</span></span>  
 <span data-ttu-id="03eb0-158">**대량 가져오기 또는 대량 내보내기를 위한 데이터 형식을 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="03eb0-158">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="03eb0-159">SQL Server 이전 버전으로부터 기본 및 문자 형식 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="03eb0-159">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [<span data-ttu-id="03eb0-160">문자 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="03eb0-160">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="03eb0-161">네이티브 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="03eb0-161">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="03eb0-162">유니코드 네이티브 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="03eb0-162">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="03eb0-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="03eb0-163">See Also</span></span>  
 <span data-ttu-id="03eb0-164">[bcp 유틸리티](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="03eb0-164">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="03eb0-165">[BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="03eb0-165">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="03eb0-166">[OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="03eb0-166">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="03eb0-167">[데이터 형식&#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="03eb0-167">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 [<span data-ttu-id="03eb0-168">데이터 정렬 및 유니코드 지원</span><span class="sxs-lookup"><span data-stu-id="03eb0-168">Collation and Unicode Support</span></span>](../collations/collation-and-unicode-support.md)  
  
  
