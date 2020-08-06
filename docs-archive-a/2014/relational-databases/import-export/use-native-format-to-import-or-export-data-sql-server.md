---
title: 네이티브 형식을 사용하여 데이터 가져오기 및 내보내기(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- native data format [SQL Server]
- data formats [SQL Server], native
ms.assetid: eb279b2f-0f1f-428f-9b8f-2a7fc495b79f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ab42ba3eb6468aac3da2fa780d371818c8776690
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741036"
---
# <a name="use-native-format-to-import-or-export-data-sql-server"></a><span data-ttu-id="52360-102">네이티브 형식을 사용하여 데이터 가져오기 및 내보내기(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="52360-102">Use Native Format to Import or Export Data (SQL Server)</span></span>
  <span data-ttu-id="52360-103">확장/DBCS(더블바이트 문자 집합) 문자가 포함되어 있지 않은 데이터 파일을 사용하여 여러 개의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 간에 데이터를 대량 전송할 때는 네이티브 형식을 사용하는 것이 바람직합니다.</span><span class="sxs-lookup"><span data-stu-id="52360-103">Native format is recommended when you bulk transfer data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using a data file that does not contain any extended/double-byte character set (DBCS) characters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="52360-104">확장 또는 DBCS 문자가 포함되어 있는 데이터 파일을 사용하여 여러 개의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 간에 데이터를 대량 전송하려면 유니코드 네이티브 형식을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52360-104">To bulk transfer data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a data file that contains extended or DBCS characters, you should use the Unicode native format.</span></span> <span data-ttu-id="52360-105">자세한 내용은 [유니코드 네이티브 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52360-105">For more information, see [Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="52360-106">네이티브 형식은 데이터베이스의 원래 데이터 형식을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="52360-106">Native format maintains the native data types of a database.</span></span> <span data-ttu-id="52360-107">네이티브 형식은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블 간에 데이터를 빠르게 전송하기 위한 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="52360-107">Native format is intended for high-speed data transfer of data between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables.</span></span> <span data-ttu-id="52360-108">서식 파일을 사용할 경우 원본 및 대상 테이블의 형식이 동일할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52360-108">If you use a format file, the source and target tables do not need to be identical.</span></span> <span data-ttu-id="52360-109">데이터 전송은 두 단계로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="52360-109">The data transfer involves two steps:</span></span>  
  
1.  <span data-ttu-id="52360-110">원본 테이블에서 데이터 파일로 데이터 대량 내보내기</span><span class="sxs-lookup"><span data-stu-id="52360-110">Bulk exporting the data from a source table into a data file</span></span>  
  
2.  <span data-ttu-id="52360-111">데이터 파일에서 대상 테이블로 데이터 대량 가져오기</span><span class="sxs-lookup"><span data-stu-id="52360-111">Bulk importing the data from the data file into the target table</span></span>  
  
 <span data-ttu-id="52360-112">형식이 동일한 테이블에서는 네이티브 형식을 사용하여 문자 형식의 불필요한 변환을 없애고 시간과 공간을 절약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52360-112">The use of native format between identical tables avoids unnecessary conversion of data types to and from character format, saving time and space.</span></span> <span data-ttu-id="52360-113">이때 최적의 전송 속도를 얻기 위해 데이터 형식을 거의 검사하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="52360-113">To achieve the optimum transfer rate, however, few checks are performed regarding data formatting.</span></span> <span data-ttu-id="52360-114">로드된 데이터와 관련된 문제를 방지하려면 다음 제한 사항 목록을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="52360-114">To prevent problems with the loaded data, see the following restrictions list.</span></span>  
  
## <a name="restrictions"></a><span data-ttu-id="52360-115">제한 사항</span><span class="sxs-lookup"><span data-stu-id="52360-115">Restrictions</span></span>  
 <span data-ttu-id="52360-116">데이터를 네이티브 형식으로 가져오려면 다음 사항을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="52360-116">To import data in native format successfully, ensure that:</span></span>  
  
-   <span data-ttu-id="52360-117">데이터 파일이 네이티브 형식인지 여부</span><span class="sxs-lookup"><span data-stu-id="52360-117">The data file is in native format.</span></span>  
  
-   <span data-ttu-id="52360-118">대상 테이블이 데이터 파일과 호환되는지 여부(예: 올바른 열 수, 데이터 형식, 길이, NULL 상태 등). 호환되지 않을 경우 각 필드를 해당 열에 매핑하기 위해 서식 파일을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52360-118">Either the target table must be compatible with the data file (having the correct number of columns, data type, length, NULL status, and so forth), or you must use a format file to map each field to its corresponding columns.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="52360-119">대상 테이블과 형식이 일치하지 않는 파일의 데이터를 가져오면 가져오기 작업에 성공하더라도 대상 테이블에 삽입된 데이터 값이 올바르지 않을 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="52360-119">If you import data from a file that is mismatched with the target table, the import operation might succeed but the data values inserted into the target table are likely to be incorrect.</span></span> <span data-ttu-id="52360-120">이는 파일의 데이터가 대상 테이블의 서식을 사용하여 해석되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="52360-120">This is because the data from the file is interpreted by using the format of the target table.</span></span> <span data-ttu-id="52360-121">따라서 형식이 일치하지 않으면 잘못된 값이 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="52360-121">Therefore, any mismatch results in the insertion of incorrect values.</span></span> <span data-ttu-id="52360-122">하지만 어떤 경우에도 이러한 불일치가 데이터베이스와의 논리적 또는 물리적 불일치를 유발하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="52360-122">However, under no circumstances can such a mismatch cause logical or physical inconsistencies in the database.</span></span>  
  
     <span data-ttu-id="52360-123">서식 파일 사용에 대한 자세한 내용은 [데이터를 가져오거나 내보내기 위한 서식 파일&#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52360-123">For information on using format files, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="52360-124">데이터를 성공적으로 가져온 경우 대상 테이블은 손상되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="52360-124">A successful import will not corrupt the target table.</span></span>  
  
## <a name="how-bcp-handles-data-in-native-format"></a><span data-ttu-id="52360-125">bcp의 네이티브 형식 데이터 처리 방법</span><span class="sxs-lookup"><span data-stu-id="52360-125">How bcp Handles Data in Native Format</span></span>  
 <span data-ttu-id="52360-126">이 섹션에서는 **bcp** 유틸리티가 데이터를 네이티브 형식으로 내보내고 가져오는 방법에 대한 특별한 고려 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="52360-126">This section discusses special considerations for how the **bcp** utility exports and imports data in native format.</span></span>  
  
-   <span data-ttu-id="52360-127">문자가 아닌 데이터</span><span class="sxs-lookup"><span data-stu-id="52360-127">Noncharacter data</span></span>  
  
     <span data-ttu-id="52360-128">bcp 유틸리티는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 내부 binary 데이터 형식을 사용하여 문자가 아닌 테이블의 데이터를 데이터 파일에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="52360-128">The bcp utility uses the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] internal binary data format to write noncharacter data from a table to a data file.</span></span>  
  
-   <span data-ttu-id="52360-129">`char` 또는 `varchar` 데이터</span><span class="sxs-lookup"><span data-stu-id="52360-129">`char` or `varchar` data</span></span>  
  
     <span data-ttu-id="52360-130">Bcp는 각 또는 필드가 시작 될 때 `char` `varchar` 접두사 길이를 추가 합니다. **bcp**</span><span class="sxs-lookup"><span data-stu-id="52360-130">At the beginning of each `char` or `varchar` field, **bcp** adds the prefix length.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="52360-131">기본 모드를 사용 하는 경우 기본적으로 **bcp** 유틸리티는 문자 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 데이터 파일에 복사 하기 전에 OEM 문자로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="52360-131">When native mode is used, by default, the **bcp** utility converts characters from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to OEM characters before it copies them to a data file.</span></span> <span data-ttu-id="52360-132">**Bcp** 유틸리티는 데이터 파일의 문자를 테이블에 대량으로 가져오기 전에 문자를 ANSI 문자로 변환 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="52360-132">The **bcp** utility converts characters from a data file to ANSI characters before it bulk imports them into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="52360-133">이러한 변환 과정에서 확장 문자 데이터가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52360-133">During these conversions, extended character data can be lost.</span></span> <span data-ttu-id="52360-134">확장 문자의 경우 유니코드 네이티브 형식을 사용하거나 코드 페이지를 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="52360-134">For extended characters, either use Unicode native format or specify a code page.</span></span>  
  
-   <span data-ttu-id="52360-135">`sql_variant` 데이터</span><span class="sxs-lookup"><span data-stu-id="52360-135">`sql_variant` data</span></span>  
  
     <span data-ttu-id="52360-136">`sql_variant` 데이터가 네이티브 형식 데이터 파일에 SQLVARIANT로 저장되면 해당 데이터는 그 특성을 모두 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="52360-136">If `sql_variant` data is stored as a SQLVARIANT in a native-format data file, the data maintains all of its characteristics.</span></span> <span data-ttu-id="52360-137">각 데이터 값의 데이터 형식을 기록하는 메타데이터는 데이터 값과 함께 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="52360-137">The metadata that records the data type of each data value is stored along with the data value.</span></span> <span data-ttu-id="52360-138">이 메타데이터는 대상 `sql_variant` 열에 동일한 데이터 형식을 가진 데이터 값을 다시 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="52360-138">This metadata is used to re-create the data value with the same data type in a destination `sql_variant` column.</span></span>  
  
     <span data-ttu-id="52360-139">대상 열의 데이터 형식이 `sql_variant`가 아닌 경우 기본적인 암시적 데이터 변환 규칙에 따라 각 데이터 값이 대상 열의 데이터 형식으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="52360-139">If the data type of the destination column is not `sql_variant`, each data value is converted to the data type of the destination column, following the normal rules of implicit data conversion.</span></span> <span data-ttu-id="52360-140">데이터 변환 중에 오류가 발생하면 현재 일괄 처리가 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="52360-140">If an error occurs during data conversion, the current batch is rolled back.</span></span> <span data-ttu-id="52360-141">`char` 열 간에 전송되는 모든 `varchar` 및 `sql_variant` 값에는 코드 페이지 변환 문제가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52360-141">Any `char` and `varchar` values that are transferred between `sql_variant` columns may have code page conversion issues.</span></span>  
  
     <span data-ttu-id="52360-142">데이터 변환에 대한 자세한 내용은 [데이터 형식 변환&#40;데이터베이스 엔진&#41;](/sql/t-sql/data-types/data-type-conversion-database-engine)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52360-142">For more information about data conversion, see [Data Type Conversion &#40;Database Engine&#41;](/sql/t-sql/data-types/data-type-conversion-database-engine).</span></span>  
  
## <a name="command-options-for-native-format"></a><span data-ttu-id="52360-143">네이티브 형식의 명령 옵션</span><span class="sxs-lookup"><span data-stu-id="52360-143">Command Options for Native Format</span></span>  
 <span data-ttu-id="52360-144">**Bcp**, BULK INSERT 또는 INSERT ...를 사용 하 여 네이티브 형식 데이터를 테이블로 가져올 수 있습니다. SELECT \* FROM OPENROWSET (BULK ...)를 선택 합니다. **Bcp** 명령 또는 BULK INSERT 문의 경우 명령줄에서 데이터 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52360-144">You can import native format data into a table using **bcp**, BULK INSERT or INSERT ... SELECT \* FROM OPENROWSET(BULK...). For a **bcp** command or BULK INSERT statement, you can specify the data format on the command line.</span></span> <span data-ttu-id="52360-145">INSERT ... SELECT \* FROM OPENROWSET(BULK...) 문의 경우 서식 파일에서 데이터 형식을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52360-145">For an INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement, you must specify the data format in a format file.</span></span>  
  
 <span data-ttu-id="52360-146">네이티브 형식에 대해 지원되는 명령줄 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="52360-146">Native format is supported by the following command line options:</span></span>  
  
|<span data-ttu-id="52360-147">명령</span><span class="sxs-lookup"><span data-stu-id="52360-147">Command</span></span>|<span data-ttu-id="52360-148">옵션</span><span class="sxs-lookup"><span data-stu-id="52360-148">Option</span></span>|<span data-ttu-id="52360-149">설명</span><span class="sxs-lookup"><span data-stu-id="52360-149">Description</span></span>|  
|-------------|------------|-----------------|  
|<span data-ttu-id="52360-150">**bcp**</span><span class="sxs-lookup"><span data-stu-id="52360-150">**bcp**</span></span>|<span data-ttu-id="52360-151">**-n**</span><span class="sxs-lookup"><span data-stu-id="52360-151">**-n**</span></span>|<span data-ttu-id="52360-152">**Bcp** 유틸리티에서 데이터의 네이티브 데이터 형식을 사용 하도록 합니다. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="52360-152">Causes the **bcp** utility to use the native data types of the data.<sup>1</sup></span></span>|  
|<span data-ttu-id="52360-153">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="52360-153">BULK INSERT</span></span>|<span data-ttu-id="52360-154">DATAFILETYPE **= '** native **'**</span><span class="sxs-lookup"><span data-stu-id="52360-154">DATAFILETYPE **='** native **'**</span></span>|<span data-ttu-id="52360-155">데이터의 네이티브 또는 와이드 네이티브 데이터 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="52360-155">Uses the native or wide native data types of the data.</span></span> <span data-ttu-id="52360-156">서식 파일로 데이터 형식을 지정하면 DATAFILETYPE은 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="52360-156">Note that DATAFILETYPE is not needed if a format file specifies the data types.</span></span>|  
  
 <span data-ttu-id="52360-157"><sup>1</sup> 네이티브 (**-n**) 데이터를 이전 버전의 클라이언트와 호환 되는 형식으로 로드 하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **-V** 스위치를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="52360-157"><sup>1</sup> To load native (**-n**) data to a format compatible with earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] clients, use the **-V** switch.</span></span> <span data-ttu-id="52360-158">자세한 내용은 [SQL Server 이전 버전으로부터 기본 및 문자 형식 데이터 가져오기](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52360-158">For more information, see [Import Native and Character Format Data from Earlier Versions of SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md).</span></span>  
  
 <span data-ttu-id="52360-159">자세한 내용은 [bcp 유틸리티](../../tools/bcp-utility.md), [BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) 또는 [OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52360-159">For more information, see [bcp Utility](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), or [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="52360-160">서식 파일에서 필드 단위로 서식을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52360-160">Alternatively, you can specify formatting on a per-field basis in a format file.</span></span> <span data-ttu-id="52360-161">자세한 내용은 [데이터를 가져오거나 내보내기 위한 서식 파일&#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52360-161">For more information, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="52360-162">예</span><span class="sxs-lookup"><span data-stu-id="52360-162">Examples</span></span>  
 <span data-ttu-id="52360-163">다음 예에서는 **bcp** 를 사용하여 네이티브 데이터의 대량 내보내기를 수행하고 내보낸 데이터에 BULK INSERT를 사용하여 대량 가져오기를 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="52360-163">The following examples demonstrate how to bulk export native data using **bcp** and bulk import the same data using BULK INSERT.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="52360-164">예제 테이블</span><span class="sxs-lookup"><span data-stu-id="52360-164">Sample Table</span></span>  
 <span data-ttu-id="52360-165">이 예에서는 **dbo** 스키마에서 **AdventureWorks** 예제 데이터베이스에 **myTestNativeData** 라는 이름의 테이블을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52360-165">The examples require that a table named **myTestNativeData** table be created in the **AdventureWorks** sample database under the **dbo** schema.</span></span> <span data-ttu-id="52360-166">예를 실행하려면 이 테이블을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52360-166">Before you can run the examples, you must create this table.</span></span> <span data-ttu-id="52360-167">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="52360-167">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE myTestNativeData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 <span data-ttu-id="52360-168">이 테이블을 채우고 결과 내용을 확인하려면 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="52360-168">To populate this table and view the resulting contents execute the following statements:</span></span>  
  
```  
INSERT INTO myTestNativeData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3');  
INSERT INTO myTestNativeData(Col1,Col2,Col3)  
   VALUES(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestNativeData  
  
```  
  
### <a name="using-bcp-to-bulk-export-native-data"></a><span data-ttu-id="52360-169">bcp를 사용하여 네이티브 데이터 대량 내보내기</span><span class="sxs-lookup"><span data-stu-id="52360-169">Using bcp to Bulk Export Native Data</span></span>  
 <span data-ttu-id="52360-170">테이블의 데이터를 데이터 파일로 내보내려면 **out** 옵션 및 다음 한정자가 있는 **bcp** 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="52360-170">To export data from the table to the data file, use **bcp** with the **out** option and the following qualifiers:</span></span>  
  
|<span data-ttu-id="52360-171">한정자</span><span class="sxs-lookup"><span data-stu-id="52360-171">Qualifiers</span></span>|<span data-ttu-id="52360-172">설명</span><span class="sxs-lookup"><span data-stu-id="52360-172">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="52360-173">**-n**</span><span class="sxs-lookup"><span data-stu-id="52360-173">**-n**</span></span>|<span data-ttu-id="52360-174">네이티브 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="52360-174">Specifies native data types.</span></span>|  
|<span data-ttu-id="52360-175">**-T**</span><span class="sxs-lookup"><span data-stu-id="52360-175">**-T**</span></span>|<span data-ttu-id="52360-176">**bcp** 유틸리티가 통합 보안을 사용하는 트러스트된 연결을 통해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로 연결되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="52360-176">Specifies that the **bcp** utility connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with a trusted connection using integrated security.</span></span> <span data-ttu-id="52360-177">**-T** 를 지정하지 않은 경우 성공적으로 로그인하려면 **-U** 와 **-P** 를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52360-177">If **-T** is not specified, you need to specify **-U** and **-P** to successfully log in.</span></span>|  
  
 <span data-ttu-id="52360-178">다음 예에서는 `myTestNativeData` 테이블에서 `myTestNativeData-n.Dat` 데이터 파일로 네이티브 형식의 데이터를 대량으로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="52360-178">The following example bulk exports data in native format from the `myTestNativeData` table into a new data file named `myTestNativeData-n.Dat` data file.</span></span> <span data-ttu-id="52360-179">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 명령 프롬프트에 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="52360-179">At the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks..myTestNativeData out C:\myTestNativeData-n.Dat -n -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-native-data"></a><span data-ttu-id="52360-180">BULK INSERT를 사용하여 네이티브 데이터 대량 가져오기</span><span class="sxs-lookup"><span data-stu-id="52360-180">Using BULK INSERT to Bulk Import Native Data</span></span>  
 <span data-ttu-id="52360-181">다음 예에서는 BULK INSERT를 사용하여 `myTestNativeData-n.Dat` 데이터 파일의 데이터를 `myTestNativeData` 테이블로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="52360-181">The following example uses BULK INSERT to import the data in the `myTestNativeData-n.Dat` data file into the `myTestNativeData` table.</span></span> <span data-ttu-id="52360-182">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="52360-182">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT myTestNativeData   
    FROM 'C:\myTestNativeData-n.Dat'   
   WITH (DATAFILETYPE='native');   
GO  
SELECT Col1,Col2,Col3 FROM myTestNativeData  
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="52360-183">관련 작업</span><span class="sxs-lookup"><span data-stu-id="52360-183">Related Tasks</span></span>  
 <span data-ttu-id="52360-184">**대량 가져오기 또는 대량 내보내기를 위한 데이터 형식을 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="52360-184">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="52360-185">SQL Server 이전 버전으로부터 기본 및 문자 형식 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="52360-185">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [<span data-ttu-id="52360-186">문자 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="52360-186">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="52360-187">유니코드 문자 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="52360-187">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="52360-188">유니코드 네이티브 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="52360-188">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="52360-189">참고 항목</span><span class="sxs-lookup"><span data-stu-id="52360-189">See Also</span></span>  
 <span data-ttu-id="52360-190">[bcp 유틸리티](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="52360-190">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="52360-191">[BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="52360-191">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="52360-192">[데이터 형식&#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="52360-192">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 <span data-ttu-id="52360-193">[sql_variant&#40;Transact-SQL&#41;](/sql/t-sql/data-types/sql-variant-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="52360-193">[sql_variant &#40;Transact-SQL&#41;](/sql/t-sql/data-types/sql-variant-transact-sql) </span></span>  
 <span data-ttu-id="52360-194">[SQL Server 이전 버전으로부터 기본 및 문자 형식 데이터 가져오기](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="52360-194">[Import Native and Character Format Data from Earlier Versions of SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md) </span></span>  
 <span data-ttu-id="52360-195">[OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="52360-195">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 [<span data-ttu-id="52360-196">유니코드 네이티브 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="52360-196">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
  
