---
title: bcp를 사용하여 파일 스토리지 유형 지정(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bcp utility [SQL Server], file storage types
- importing data, file storage types
- native data format [SQL Server]
- file storage types [SQL Server]
- data formats [SQL Server], file storage types
ms.assetid: 85e12df8-1be7-4bdc-aea9-05aade085c06
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c1f3ad2a94ffe3e0f1db19a8e66f85497e7143dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647008"
---
# <a name="specify-file-storage-type-by-using-bcp-sql-server"></a><span data-ttu-id="c9908-102">bcp를 사용하여 파일 스토리지 유형 지정(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c9908-102">Specify File Storage Type by Using bcp (SQL Server)</span></span>
  <span data-ttu-id="c9908-103">*파일 스토리지 유형* 은 데이터 파일에서 데이터가 저장되는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c9908-103">The *file storage type* describes how data is stored in the data file.</span></span> <span data-ttu-id="c9908-104">데이터는 데이터베이스 테이블 형식(네이티브 형식), 문자 표시(문자 형식) 또는 암시적 변환을 지원하는 모든 데이터 형식의 데이터 파일로 내보낼 수 있습니다. 예를 들어 `smallint`를 `int`로 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9908-104">Data can be exported to a data file as its database table type (native format), in its character representation (character format), or as any data type where implicit conversion is supported; for example, copying a `smallint` as an `int`.</span></span> <span data-ttu-id="c9908-105">사용자 정의 데이터 형식은 해당 기본 형식으로 내보내집니다.</span><span class="sxs-lookup"><span data-stu-id="c9908-105">User-defined data types are exported as their base types.</span></span>  
  
## <a name="the-bcp-prompt-for-file-storage-type"></a><span data-ttu-id="c9908-106">파일 스토리지 유형에 대한 bcp 프롬프트</span><span class="sxs-lookup"><span data-stu-id="c9908-106">The bcp Prompt for File Storage Type</span></span>  
 <span data-ttu-id="c9908-107">대화형 **bcp** 명령에 **in** 또는 **out** 옵션이 포함된 경우 서식 파일 스위치( **-f**) 또는 데이터 형식 스위치( **-n**, **-c**, **-w**또는 **-N**)가 없으면 각 데이터 필드의 파일 스토리지 유형을 다음과 같이 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9908-107">If an interactive **bcp** command contains the **in** or **out** option without either the format file switch (**-f**) or a data-format switch (**-n**, **-c**, **-w**, or **-N**), the command prompts for the file storage type of each data field, as follows:</span></span>  
  
 `Enter the file storage type of field <field_name> [<default>]:`  
  
 <span data-ttu-id="c9908-108">이 프롬프트에 대한 사용자 응답은 수행하는 태스크에 따라 다음과 같이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="c9908-108">Your response to this prompt depends on the task you perform, as follows:</span></span>  
  
-   <span data-ttu-id="c9908-109">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 데이터를 최대한 압축된 스토리지(원시 데이터 형식)의 데이터 파일로 대량 내보내려면 **bcp**에서 제공되는 기본 파일 스토리지 유형을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="c9908-109">To bulk export data from an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to a data file in the most compact storage possible (native data format), accept the default file storage types that are provided by **bcp**.</span></span> <span data-ttu-id="c9908-110">네이티브 스토리지 저장 유형 목록은 이 항목 뒷부분에 있는 "네이티브 파일 스토리지 유형"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c9908-110">For a list of the native file storage types, see "Native File Storage Types," later in this topic.</span></span>  
  
-   <span data-ttu-id="c9908-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 데이터를 문자 형식으로 데이터 파일에 대량으로 내보내려면 `char`를 테이블의 모든 열에 대한 파일 스토리지 유형으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c9908-111">To bulk export data from an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to a data file in character format, specify `char` as the file storage type for all columns in the table.</span></span>  
  
-   <span data-ttu-id="c9908-112">데이터 파일에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 인스턴스로 데이터를 대량으로 가져오려면 문자 형식으로 저장된 유형에 대해 `char`를 파일 스토리지 유형으로 지정하고 네이티브 데이터 형식으로 저장된 데이터의 경우 적절한 파일 저장 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c9908-112">To bulk import data to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a data file, specify the file storage type as `char` for types stored in character format and, for data stored in native data type format, specify one of the file storage types, as appropriate:</span></span>  
  
    |<span data-ttu-id="c9908-113">파일 스토리지 유형</span><span class="sxs-lookup"><span data-stu-id="c9908-113">File storage type</span></span>|<span data-ttu-id="c9908-114">명령 프롬프트에 입력할 내용</span><span class="sxs-lookup"><span data-stu-id="c9908-114">Enter at command prompt</span></span>|  
    |-----------------------|-----------------------------|  
    |<span data-ttu-id="c9908-115">`char` <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="c9908-115">`char` <sup>1</sup></span></span>|<span data-ttu-id="c9908-116">`c`[`har`]</span><span class="sxs-lookup"><span data-stu-id="c9908-116">`c`[`har`]</span></span>|  
    |`varchar`|`c[har]`|  
    |`nchar`|`w`|  
    |`nvarchar`|`w`|  
    |<span data-ttu-id="c9908-117">`text` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="c9908-117">`text` <sup>2</sup></span></span>|<span data-ttu-id="c9908-118">`T`[`ext`]</span><span class="sxs-lookup"><span data-stu-id="c9908-118">`T`[`ext`]</span></span>|  
    |`ntext2`|`W`|  
    |`binary`|`x`|  
    |`varbinary`|`x`|  
    |<span data-ttu-id="c9908-119">`image` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="c9908-119">`image` <sup>2</sup></span></span>|<span data-ttu-id="c9908-120">`I`[`mage`]</span><span class="sxs-lookup"><span data-stu-id="c9908-120">`I`[`mage`]</span></span>|  
    |`datetime`|<span data-ttu-id="c9908-121">**d[ate]**</span><span class="sxs-lookup"><span data-stu-id="c9908-121">**d[ate]**</span></span>|  
    |`smalldatetime`|`D`|  
    |`time`|`te`|  
    |`date`|`de`|  
    |`datetime2`|`d2`|  
    |`datetimeoffset`|`do`|  
    |`decimal`|`n`|  
    |`numeric`|`n`|  
    |`float`|<span data-ttu-id="c9908-122">**f[loat]**</span><span class="sxs-lookup"><span data-stu-id="c9908-122">**f[loat]**</span></span>|  
    |`real`|`r`|  
    |`Int`|<span data-ttu-id="c9908-123">**i[nt]**</span><span class="sxs-lookup"><span data-stu-id="c9908-123">**i[nt]**</span></span>|  
    |`bigint`|`B[igint]`|  
    |`smallint`|<span data-ttu-id="c9908-124">**s[mallint]**</span><span class="sxs-lookup"><span data-stu-id="c9908-124">**s[mallint]**</span></span>|  
    |`tinyint`|<span data-ttu-id="c9908-125">**t[inyint]**</span><span class="sxs-lookup"><span data-stu-id="c9908-125">**t[inyint]**</span></span>|  
    |`money`|<span data-ttu-id="c9908-126">**m[oney]**</span><span class="sxs-lookup"><span data-stu-id="c9908-126">**m[oney]**</span></span>|  
    |`smallmoney`|`M`|  
    |`bit`|`b[it]`|  
    |`uniqueidentifier`|`u`|  
    |`sql_variant`|`V[ariant]`|  
    |`timestamp`|`x`|  
    |<span data-ttu-id="c9908-127">`UDT`(사용자 정의 데이터 형식)</span><span class="sxs-lookup"><span data-stu-id="c9908-127">`UDT` (a user-defined data type)</span></span>|`U`|  
    |`XML`|`X`|  
  
     <span data-ttu-id="c9908-128"><sup>1</sup> 필드 길이, 접두사 길이 및 종결자의 상호 작용은 파일 저장 유형으로 내보낸 문자가 아닌 데이터에 대 한 데이터 파일에 할당 되는 저장 공간의 크기를 결정 합니다 `char` .</span><span class="sxs-lookup"><span data-stu-id="c9908-128"><sup>1</sup> The interaction of field length, prefix length, and terminators determines the amount of storage space that is allocated in a data file for noncharacter data that is exported as the `char` file storage type.</span></span>  
  
     <span data-ttu-id="c9908-129"><sup>2</sup> `ntext` , `text` 및 `image` 데이터 형식은 이후 버전의에서 제거 될 예정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 입니다.</span><span class="sxs-lookup"><span data-stu-id="c9908-129"><sup>2</sup> The `ntext`, `text`, and `image` data types will be removed in a future version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c9908-130">향후 개발 작업에서는 이 데이터 형식을 사용하지 않도록 하고 현재 이 데이터 형식을 사용하는 애플리케이션은 수정하십시오.</span><span class="sxs-lookup"><span data-stu-id="c9908-130">In new development work, avoid using these data types, and plan to modify applications that currently use them.</span></span> <span data-ttu-id="c9908-131">대신 `nvarchar(max)`, `varchar(max)` 및 `varbinary(max)`를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9908-131">Use `nvarchar(max)`, `varchar(max)`, and `varbinary(max)` instead.</span></span>  
  
## <a name="native-file-storage-types"></a><span data-ttu-id="c9908-132">네이티브 파일 스토리지 유형</span><span class="sxs-lookup"><span data-stu-id="c9908-132">Native File Storage Types</span></span>  
 <span data-ttu-id="c9908-133">각 네이티브 파일 스토리지 유형은 해당 호스트 파일 데이터 형식으로 서식 파일에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9908-133">Each native file storage type is recorded in the format file as a corresponding host file data type.</span></span>  
  
|<span data-ttu-id="c9908-134">파일 스토리지 유형</span><span class="sxs-lookup"><span data-stu-id="c9908-134">File storage type</span></span>|<span data-ttu-id="c9908-135">호스트 파일 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="c9908-135">Host file data type</span></span>|  
|-----------------------|-------------------------|  
|<span data-ttu-id="c9908-136">`char` <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="c9908-136">`char` <sup>1</sup></span></span>|<span data-ttu-id="c9908-137">SQLCHAR</span><span class="sxs-lookup"><span data-stu-id="c9908-137">SQLCHAR</span></span>|  
|`varchar`|<span data-ttu-id="c9908-138">SQLCHAR</span><span class="sxs-lookup"><span data-stu-id="c9908-138">SQLCHAR</span></span>|  
|`nchar`|<span data-ttu-id="c9908-139">SQLNCHAR</span><span class="sxs-lookup"><span data-stu-id="c9908-139">SQLNCHAR</span></span>|  
|`nvarchar`|<span data-ttu-id="c9908-140">SQLNCHAR</span><span class="sxs-lookup"><span data-stu-id="c9908-140">SQLNCHAR</span></span>|  
|<span data-ttu-id="c9908-141">`text` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="c9908-141">`text` <sup>2</sup></span></span>|<span data-ttu-id="c9908-142">SQLCHAR</span><span class="sxs-lookup"><span data-stu-id="c9908-142">SQLCHAR</span></span>|  
|<span data-ttu-id="c9908-143">`ntext` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="c9908-143">`ntext` <sup>2</sup></span></span>|<span data-ttu-id="c9908-144">SQLNCHAR</span><span class="sxs-lookup"><span data-stu-id="c9908-144">SQLNCHAR</span></span>|  
|`binary`|<span data-ttu-id="c9908-145">SQLBINARY</span><span class="sxs-lookup"><span data-stu-id="c9908-145">SQLBINARY</span></span>|  
|`varbinary`|<span data-ttu-id="c9908-146">SQLBINARY</span><span class="sxs-lookup"><span data-stu-id="c9908-146">SQLBINARY</span></span>|  
|<span data-ttu-id="c9908-147">`image` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="c9908-147">`image` <sup>2</sup></span></span>|<span data-ttu-id="c9908-148">SQLBINARY</span><span class="sxs-lookup"><span data-stu-id="c9908-148">SQLBINARY</span></span>|  
|`datetime`|<span data-ttu-id="c9908-149">SQLDATETIME</span><span class="sxs-lookup"><span data-stu-id="c9908-149">SQLDATETIME</span></span>|  
|`smalldatetime`|<span data-ttu-id="c9908-150">SQLDATETIM4</span><span class="sxs-lookup"><span data-stu-id="c9908-150">SQLDATETIM4</span></span>|  
|`decimal`|<span data-ttu-id="c9908-151">SQLDECIMAL</span><span class="sxs-lookup"><span data-stu-id="c9908-151">SQLDECIMAL</span></span>|  
|`numeric`|<span data-ttu-id="c9908-152">SQLNUMERIC</span><span class="sxs-lookup"><span data-stu-id="c9908-152">SQLNUMERIC</span></span>|  
|`float`|<span data-ttu-id="c9908-153">SQLFLT8</span><span class="sxs-lookup"><span data-stu-id="c9908-153">SQLFLT8</span></span>|  
|`real`|<span data-ttu-id="c9908-154">SQLFLT4</span><span class="sxs-lookup"><span data-stu-id="c9908-154">SQLFLT4</span></span>|  
|`int`|<span data-ttu-id="c9908-155">SQLINT</span><span class="sxs-lookup"><span data-stu-id="c9908-155">SQLINT</span></span>|  
|`bigint`|<span data-ttu-id="c9908-156">SQLBIGINT</span><span class="sxs-lookup"><span data-stu-id="c9908-156">SQLBIGINT</span></span>|  
|`smallint`|<span data-ttu-id="c9908-157">SQLSMALLINT</span><span class="sxs-lookup"><span data-stu-id="c9908-157">SQLSMALLINT</span></span>|  
|`tinyint`|<span data-ttu-id="c9908-158">SQLTINYINT</span><span class="sxs-lookup"><span data-stu-id="c9908-158">SQLTINYINT</span></span>|  
|`money`|<span data-ttu-id="c9908-159">SQLMONEY</span><span class="sxs-lookup"><span data-stu-id="c9908-159">SQLMONEY</span></span>|  
|`smallmoney`|<span data-ttu-id="c9908-160">SQLMONEY4</span><span class="sxs-lookup"><span data-stu-id="c9908-160">SQLMONEY4</span></span>|  
|`bit`|<span data-ttu-id="c9908-161">SQLBIT</span><span class="sxs-lookup"><span data-stu-id="c9908-161">SQLBIT</span></span>|  
|`uniqueidentifier`|<span data-ttu-id="c9908-162">SQLUNIQUEID</span><span class="sxs-lookup"><span data-stu-id="c9908-162">SQLUNIQUEID</span></span>|  
|`sql_variant`|<span data-ttu-id="c9908-163">SQLVARIANT</span><span class="sxs-lookup"><span data-stu-id="c9908-163">SQLVARIANT</span></span>|  
|`timestamp`|<span data-ttu-id="c9908-164">SQLBINARY</span><span class="sxs-lookup"><span data-stu-id="c9908-164">SQLBINARY</span></span>|  
|<span data-ttu-id="c9908-165">UDT(사용자 정의 데이터 형식)</span><span class="sxs-lookup"><span data-stu-id="c9908-165">UDT (a user-defined data type)</span></span>|<span data-ttu-id="c9908-166">SQLUDT</span><span class="sxs-lookup"><span data-stu-id="c9908-166">SQLUDT</span></span>|  
  
 <span data-ttu-id="c9908-167"><sup>1</sup> 문자 형식으로 저장 된 데이터 파일은 `char` 파일 저장 유형으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9908-167"><sup>1</sup> Data files that are stored in character format use `char` as the file storage type.</span></span> <span data-ttu-id="c9908-168">그러므로 문자 데이터 파일의 경우 SQLCHAR는 서식 파일에 나타나는 유일한 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="c9908-168">Therefore, for character data files, SQLCHAR is the only data type that appears in a format file.</span></span>  
  
 <span data-ttu-id="c9908-169"><sup>2</sup> `text` `ntext` 기본값을 가진, 및 열로 데이터를 대량으로 가져올 수 없습니다 `image` .</span><span class="sxs-lookup"><span data-stu-id="c9908-169"><sup>2</sup> You cannot bulk import data into `text`, `ntext`, and `image` columns that have DEFAULT values.</span></span>  
  
## <a name="additional-considerations-for-file-storage-types"></a><span data-ttu-id="c9908-170">파일 스토리지 유형에 대한 추가 고려 사항</span><span class="sxs-lookup"><span data-stu-id="c9908-170">Additional Considerations for File Storage Types</span></span>  
 <span data-ttu-id="c9908-171">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 인스턴스에서 데이터 파일로 데이터를 대량으로 내보내는 경우 다음을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="c9908-171">When you bulk export data from an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to a data file:</span></span>  
  
-   <span data-ttu-id="c9908-172">`char`를 항상 파일 스토리지 유형으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9908-172">You can always specify `char` as the file storage type.</span></span>  
  
-   <span data-ttu-id="c9908-173">잘못 된 암시적 변환을 나타내는 파일 저장 유형을 입력 하면 **bcp** 가 실패 합니다. 예를 들어 데이터에 대해를 지정할 수는 있지만 `int` `smallint` 데이터를 지정 하는 경우 `smallint` `int` 오버플로 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9908-173">If you enter a file storage type that represents an invalid implicit conversion, **bcp** fails; for example, though you can specify `int` for `smallint` data, if you specify `smallint` for `int` data, overflow errors result.</span></span>  
  
-   <span data-ttu-id="c9908-174">`float`, `money`, `datetime` 또는 `int`와 같이 문자가 아닌 데이터 형식이 데이터베이스 형식으로 저장되면 데이터는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 네이티브 형식으로 데이터 파일에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9908-174">When noncharacter data types such as `float`, `money`, `datetime`, or `int` are stored as their database types, the data is written to the data file in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native format.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c9908-175">**bcp** 명령의 모든 필드를 대화형으로 지정하면 명령에서 비 XML 서식 파일의 각 필드에 대한 응답을 저장하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c9908-175">After you interactively specify all of the fields in a **bcp** command, the command prompts you save your responses for each field in a non-XML format file.</span></span> <span data-ttu-id="c9908-176">비 XML 서식 파일에 대한 자세한 내용은 [비 XML 서식 파일&#40;SQL Server&#41;](xml-format-files-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c9908-176">For more information on non-XML format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9908-177">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c9908-177">See Also</span></span>  
 <span data-ttu-id="c9908-178">[bcp 유틸리티](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="c9908-178">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="c9908-179">[데이터 형식&#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c9908-179">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 <span data-ttu-id="c9908-180">[bcp를 사용하여 필드 길이 지정&#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c9908-180">[Specify Field Length by Using bcp &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md) </span></span>  
 <span data-ttu-id="c9908-181">[필드 및 행 종결자 지정&#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c9908-181">[Specify Field and Row Terminators &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md) </span></span>  
 [<span data-ttu-id="c9908-182">bcp를 사용하여 데이터 파일에 접두사 길이 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c9908-182">Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;</span></span>](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
  
