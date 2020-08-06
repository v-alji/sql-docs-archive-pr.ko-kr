---
title: 데이터를 가져오거나 내보내기 위해 유니코드 네이티브 형식 사용(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- Unicode [SQL Server], bulk importing and exporting
- data formats [SQL Server], Unicode native
ms.assetid: a6213308-f3d5-406e-9029-19d8bb3367f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: beae2f836de16dedf3be6d8c196910c53be02266
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741023"
---
# <a name="use-unicode-native-format-to-import-or-export-data-sql-server"></a><span data-ttu-id="cc74b-102">데이터를 가져오거나 내보내기 위해 유니코드 네이티브 형식 사용(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="cc74b-102">Use Unicode Native Format to Import or Export Data (SQL Server)</span></span>
  <span data-ttu-id="cc74b-103">유니코드 네이티브 형식은 한 곳의 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치에서 다른 설치로 정보를 복사해야 할 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-103">Unicode native format is helpful when information must be copied from one [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation to another.</span></span> <span data-ttu-id="cc74b-104">비문자 형식의 데이터에 네이티브 형식을 사용하면 문자 형식과 다른 데이터 형식 간의 불필요한 변환을 막고 시간을 절약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-104">The use of native format for noncharacter data saves time, eliminating unnecessary conversion of data types to and from character format.</span></span> <span data-ttu-id="cc74b-105">모든 문자 형식의 데이터에 유니코드 문자 형식을 사용하면 다른 코드 페이지를 사용하는 서버 간에 데이터를 대량 로드할 때 확장 문자의 손실을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-105">The use of Unicode character format for all character data prevents loss of any extended characters during bulk transfer of data between servers using different code pages.</span></span> <span data-ttu-id="cc74b-106">유니코드 네이티브 형식의 데이터 파일은 어떤 대량 가져오기 방법으로도 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-106">A data file in Unicode native format can be read by any bulk-import method.</span></span>  
  
 <span data-ttu-id="cc74b-107">확장 또는 DBCS 문자를 포함하는 데이터 파일을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 여러 인스턴트 사이에 대량의 데이터를 전송하는 경우 유니코드 네이티브 형식을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-107">Unicode native format is recommended for the bulk transfer of data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a data file that contains extended or DBCS characters.</span></span> <span data-ttu-id="cc74b-108">비문자 데이터의 경우 유니코드 네이티브 형식은 네이티브(데이터베이스) 데이터 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-108">For noncharacter data, Unicode native format uses native (database) data types.</span></span> <span data-ttu-id="cc74b-109">`char`, `nchar`, `varchar`, `nvarchar`, `text`, `varchar(max)`, `nvarchar(max)` 및 `ntext`와 같은 문자 데이터의 경우 유니코드 네이티브 형식은 유니코드 문자 데이터 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-109">For character data, such as `char`, `nchar`, `varchar`, `nvarchar`, `text`, `varchar(max)`, `nvarchar(max)`, and `ntext`, the Unicode native format uses Unicode character data format.</span></span>  
  
 <span data-ttu-id="cc74b-110">유니코드 네이티브 형식의 데이터 파일에 SQLVARIANT로 저장된 `sql_variant` 데이터는 `char` 및 `varchar` 값이 `nchar` 및 `nvarchar`로 변환되어 영향을 받은 열에 두 배의 스토리지 공간이 필요하다는 점을 제외하고 네이티브 형식의 데이터 파일과 같은 방법으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-110">The `sql_variant` data that is stored as a SQLVARIANT in a Unicode native-format data file operates in the same manner as it does in a native-format data file, except that `char` and `varchar` values are converted to `nchar` and `nvarchar`, which doubles the amount of storage required for the affected columns.</span></span> <span data-ttu-id="cc74b-111">테이블 열로 대량 가져오기를 수행하면 원래의 메타데이터는 유지되고 값은 원래의 `char` 및 `varchar` 데이터 형식으로 다시 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-111">The original metadata is preserved, and the values are converted back to their original `char` and `varchar` data type when bulk imported into a table column.</span></span>  
  
## <a name="command-options-for-unicode-native-format"></a><span data-ttu-id="cc74b-112">유니코드 네이티브 형식의 명령 옵션</span><span class="sxs-lookup"><span data-stu-id="cc74b-112">Command Options for Unicode Native Format</span></span>  
 <span data-ttu-id="cc74b-113">**Bcp**, BULK INSERT 또는 INSERT ...를 사용 하 여 테이블로 유니코드 네이티브 형식 데이터를 가져올 수 있습니다. SELECT \* FROM OPENROWSET (BULK ...)를 선택 합니다. **Bcp** 명령 또는 BULK INSERT 문의 경우 명령줄에서 데이터 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-113">You can import Unicode native format data into a table using **bcp**, BULK INSERT or INSERT ... SELECT \* FROM OPENROWSET(BULK...). For a **bcp** command or BULK INSERT statement, you can specify the data format on the command line.</span></span> <span data-ttu-id="cc74b-114">INSERT ... SELECT \* FROM OPENROWSET(BULK...) 문의 경우 서식 파일에서 데이터 형식을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-114">For an INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement, you must specify the data format in a format file.</span></span>  
  
 <span data-ttu-id="cc74b-115">다음 옵션으로 유니코드 네이티브 형식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-115">Unicode native format is supported by the following options:</span></span>  
  
|<span data-ttu-id="cc74b-116">명령</span><span class="sxs-lookup"><span data-stu-id="cc74b-116">Command</span></span>|<span data-ttu-id="cc74b-117">옵션</span><span class="sxs-lookup"><span data-stu-id="cc74b-117">Option</span></span>|<span data-ttu-id="cc74b-118">설명</span><span class="sxs-lookup"><span data-stu-id="cc74b-118">Description</span></span>|  
|-------------|------------|-----------------|  
|<span data-ttu-id="cc74b-119">**bcp**</span><span class="sxs-lookup"><span data-stu-id="cc74b-119">**bcp**</span></span>|<span data-ttu-id="cc74b-120">**-N**</span><span class="sxs-lookup"><span data-stu-id="cc74b-120">**-N**</span></span>|<span data-ttu-id="cc74b-121">**Bcp** 유틸리티는 모든 문자가 아닌 데이터에 네이티브 (데이터베이스) 데이터 형식을 사용 하 고 모든 문자 (,,,, `char` `nchar` `varchar` `nvarchar` `text` 및 `ntext` ) 데이터에 유니코드 문자 데이터 형식을 사용 하는 유니코드 네이티브 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-121">Causes the **bcp** utility to use the Unicode native format, which uses native (database) data types for all noncharacter data and Unicode character data format for all character (`char`, `nchar`, `varchar`, `nvarchar`, `text`, and `ntext`) data.</span></span>|  
|<span data-ttu-id="cc74b-122">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="cc74b-122">BULK INSERT</span></span>|<span data-ttu-id="cc74b-123">DATAFILETYPE **= '** widenative **'**</span><span class="sxs-lookup"><span data-stu-id="cc74b-123">DATAFILETYPE **='** widenative **'**</span></span>|<span data-ttu-id="cc74b-124">데이터를 대량으로 가져올 때 유니코드 네이티브 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-124">Use Unicode native format when bulk importing data.</span></span>|  
  
 <span data-ttu-id="cc74b-125">자세한 내용은 [bcp 유틸리티](../../tools/bcp-utility.md), [BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) 또는 [OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cc74b-125">For more information, see [bcp Utility](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), or [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cc74b-126">서식 파일에서 필드 단위로 서식을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-126">Alternatively, you can specify formatting on a per-field basis in a format file.</span></span> <span data-ttu-id="cc74b-127">자세한 내용은 [데이터를 가져오거나 내보내기 위한 서식 파일&#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cc74b-127">For more information, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="cc74b-128">예</span><span class="sxs-lookup"><span data-stu-id="cc74b-128">Examples</span></span>  
 <span data-ttu-id="cc74b-129">다음 예에서는 **bcp** 를 사용하여 네이티브 데이터의 대량 내보내기를 수행하고 내보낸 데이터에 BULK INSERT를 사용하여 대량 가져오기를 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-129">The following examples demonstrate how to bulk export native data using **bcp** and bulk import the same data using BULK INSERT.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="cc74b-130">예제 테이블</span><span class="sxs-lookup"><span data-stu-id="cc74b-130">Sample Table</span></span>  
 <span data-ttu-id="cc74b-131">이 예에서는 **dbo** 스키마의 **AdventureWorks** 예제 데이터베이스에 **myTestUniNativeData** 라는 테이블이 필요하며</span><span class="sxs-lookup"><span data-stu-id="cc74b-131">The examples require that a table named **myTestUniNativeData** table be created in the **AdventureWorks** sample database under the **dbo** schema.</span></span> <span data-ttu-id="cc74b-132">예를 실행하려면 이 테이블을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-132">Before you can run the examples, you must create this table.</span></span> <span data-ttu-id="cc74b-133">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-133">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE myTestUniNativeData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 <span data-ttu-id="cc74b-134">이 테이블을 채우고 결과 내용을 확인하려면 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-134">To populate this table and view the resulting contents execute the following statements:</span></span>  
  
```  
INSERT INTO myTestUniNativeData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3');  
INSERT INTO myTestUniNativeData(Col1,Col2,Col3)  
   VALUES(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestUniNativeData  
  
```  
  
### <a name="using-bcp-to-bulk-export-native-data"></a><span data-ttu-id="cc74b-135">bcp를 사용하여 네이티브 데이터 대량 내보내기</span><span class="sxs-lookup"><span data-stu-id="cc74b-135">Using bcp to Bulk Export Native Data</span></span>  
 <span data-ttu-id="cc74b-136">테이블의 데이터를 데이터 파일로 내보내려면 **out** 옵션 및 다음 한정자가 있는 **bcp** 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-136">To export data from the table to the data file, use **bcp** with the **out** option and the following qualifiers:</span></span>  
  
|<span data-ttu-id="cc74b-137">한정자</span><span class="sxs-lookup"><span data-stu-id="cc74b-137">Qualifiers</span></span>|<span data-ttu-id="cc74b-138">Description</span><span class="sxs-lookup"><span data-stu-id="cc74b-138">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="cc74b-139">**-N**</span><span class="sxs-lookup"><span data-stu-id="cc74b-139">**-N**</span></span>|<span data-ttu-id="cc74b-140">네이티브 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-140">Specifies native data types.</span></span>|  
|<span data-ttu-id="cc74b-141">**-T**</span><span class="sxs-lookup"><span data-stu-id="cc74b-141">**-T**</span></span>|<span data-ttu-id="cc74b-142">**bcp** 유틸리티가 통합 보안을 사용하는 트러스트된 연결을 통해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로 연결되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-142">Specifies that the **bcp** utility connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with a trusted connection using integrated security.</span></span> <span data-ttu-id="cc74b-143">**-T** 를 지정하지 않은 경우 성공적으로 로그인하려면 **-U** 와 **-P** 를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-143">If **-T** is not specified, you need to specify **-U** and **-P** to successfully log in.</span></span>|  
  
 <span data-ttu-id="cc74b-144">다음 예에서는 `myTestUniNativeData` 테이블에서 `myTestUniNativeData-N.Dat` 데이터 파일로 네이티브 형식의 데이터를 대량으로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-144">The following example bulk exports data in native format from the `myTestUniNativeData` table into a new data file named `myTestUniNativeData-N.Dat` data file.</span></span> <span data-ttu-id="cc74b-145">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 명령 프롬프트에 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-145">At the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks..myTestUniNativeData out C:\myTestUniNativeData-N.Dat -N -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-native-data"></a><span data-ttu-id="cc74b-146">BULK INSERT를 사용하여 네이티브 데이터 대량 가져오기</span><span class="sxs-lookup"><span data-stu-id="cc74b-146">Using BULK INSERT to Bulk Import Native Data</span></span>  
 <span data-ttu-id="cc74b-147">다음 예에서는 BULK INSERT를 사용하여 `myTestUniNativeData-N.Dat` 데이터 파일의 데이터를 `myTestUniNativeData` 테이블로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-147">The following example uses BULK INSERT to import the data in the `myTestUniNativeData-N.Dat` data file into the `myTestUniNativeData` table.</span></span> <span data-ttu-id="cc74b-148">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cc74b-148">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT myTestUniNativeData   
    FROM 'C:\myTestUniNativeData-N.Dat'   
   WITH (DATAFILETYPE='widenative');   
GO  
SELECT Col1,Col2,Col3 FROM myTestUniNativeData;  
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="cc74b-149">관련 작업</span><span class="sxs-lookup"><span data-stu-id="cc74b-149">Related Tasks</span></span>  
 <span data-ttu-id="cc74b-150">**대량 가져오기 또는 대량 내보내기를 위한 데이터 형식을 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="cc74b-150">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="cc74b-151">SQL Server 이전 버전으로부터 기본 및 문자 형식 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="cc74b-151">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [<span data-ttu-id="cc74b-152">문자 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cc74b-152">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="cc74b-153">네이티브 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cc74b-153">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="cc74b-154">유니코드 문자 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cc74b-154">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="cc74b-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cc74b-155">See Also</span></span>  
 <span data-ttu-id="cc74b-156">[bcp 유틸리티](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="cc74b-156">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="cc74b-157">[BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cc74b-157">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="cc74b-158">[OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cc74b-158">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 [<span data-ttu-id="cc74b-159">데이터 형식&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc74b-159">Data Types &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/data-types-transact-sql)  
  
  
