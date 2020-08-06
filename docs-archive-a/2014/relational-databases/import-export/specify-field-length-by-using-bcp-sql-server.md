---
title: bcp를 사용하여 필드 길이 지정(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- native data format [SQL Server]
- default field lengths
- field length [SQL Server]
- data formats [SQL Server], field length
- bcp utility [SQL Server], field length
ms.assetid: 240f33ca-ef4a-413a-a4de-831885cb505b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 13343b4f3778df1bbe7ef1c99b3d06338f18631c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729483"
---
# <a name="specify-field-length-by-using-bcp-sql-server"></a><span data-ttu-id="79a86-102">bcp를 사용하여 필드 길이 지정(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="79a86-102">Specify Field Length by Using bcp (SQL Server)</span></span>
  <span data-ttu-id="79a86-103">필드 길이는 데이터를 문자 형식으로 표시하는 데 필요한 최대 문자 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="79a86-103">The field length indicates the maximum number of characters that are required to represent data in character format.</span></span> <span data-ttu-id="79a86-104">데이터가 네이티브 형식으로 저장된 경우에는 필드 길이를 쉽게 알 수 있습니다. 예를 들어 `int` 데이터 형식의 길이는 4바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="79a86-104">The field length is already known if the data is stored in the native format; for example, the `int` data type takes 4 bytes.</span></span> <span data-ttu-id="79a86-105">접두사 길이에 대해 0을 지정한 경우 **bcp** 명령은 필드 길이, 기본 필드 길이, 데이터가 포함 된 데이터 파일의 데이터 저장소에 대 한 필드 길이의 영향을 묻는 메시지를 표시 합니다 `char` .</span><span class="sxs-lookup"><span data-stu-id="79a86-105">If you have indicated 0 for the prefix length, the **bcp** command prompts you for field length, the default field lengths, and the impact of field-length on data storage in data files that contain `char` data.</span></span>  
  
## <a name="the-bcp-prompt-for-field-length"></a><span data-ttu-id="79a86-106">필드 길이에 대한 bcp 프롬프트</span><span class="sxs-lookup"><span data-stu-id="79a86-106">The bcp Prompt for Field Length</span></span>  
 <span data-ttu-id="79a86-107">대화형 **bcp** 명령에 **in** 또는 **out** 옵션이 포함된 경우 서식 파일 스위치( **-f**) 또는 데이터 형식 스위치( **-n**, **-c**, **-w** 또는 **-N**)가 없으면 다음과 같이 각 데이터 필드의 필드 길이를 지정하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="79a86-107">If an interactive **bcp** command contains the **in** or **out** option without either the format file switch (**-f**) or a data-format switch (**-n**, **-c**, **-w**, or **-N**), the command prompts for the field length of each data field, as follows:</span></span>  
  
 `Enter length of field <field_name> [<default>]:`  
  
 <span data-ttu-id="79a86-108">컨텍스트에서 이 메시지가 표시되는 예제를 보려면 [bcp를 사용하여 데이터 형식을 호환 가능하도록 지정&#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79a86-108">For an example that shows this prompt in context, see [Specify Data Formats for Compatibility when Using bcp &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="79a86-109">**bcp** 명령의 모든 필드를 대화형으로 지정하면 명령에서 비 XML 서식 파일의 각 필드에 대한 응답을 저장하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="79a86-109">After you interactively specify all of the fields in a **bcp** command, the command prompts you save your responses for each field in a non-XML format file.</span></span> <span data-ttu-id="79a86-110">비 XML 서식 파일에 대한 자세한 내용은 [비 XML 서식 파일&#40;SQL Server&#41;](xml-format-files-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79a86-110">For more information on non-XML format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
 <span data-ttu-id="79a86-111">**bcp** 명령에서 필드 길이 입력 메시지를 표시하는지 여부는 다음과 같은 몇 가지 요인에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="79a86-111">Whether a **bcp** command prompts for field length depends on several factors, as follows:</span></span>  
  
-   <span data-ttu-id="79a86-112">고정 길이가 아닌 데이터 형식을 복사하며 접두사 길이 0을 지정하는 경우 **bcp** 에서 필드 길이를 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="79a86-112">When you copy data types that are not of fixed length and you specify a prefix length of 0, **bcp** prompts for a field length.</span></span>  
  
-   <span data-ttu-id="79a86-113">**bcp** 는 문자 형식 이외의 데이터를 문자 데이터로 변환하는 경우 데이터를 저장할 수 있을 만큼 큰 기본 필드 길이를 제시합니다.</span><span class="sxs-lookup"><span data-stu-id="79a86-113">When converting noncharacter data to character data, **bcp** suggests a default field length large enough to store the data.</span></span>  
  
-   <span data-ttu-id="79a86-114">파일 스토리지 유형이 문자 형식이 아니면 **bcp** 명령은 필드 길이 입력 메시지를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79a86-114">If the file storage type is noncharacter, the **bcp** command does not prompt for a field length.</span></span> <span data-ttu-id="79a86-115">데이터는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 네이티브 데이터 표현(원시 형식)으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="79a86-115">The data is stored in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native data representation (native format).</span></span>  
  
## <a name="using-default-field-lengths"></a><span data-ttu-id="79a86-116">기본 필드 길이 사용</span><span class="sxs-lookup"><span data-stu-id="79a86-116">Using Default Field Lengths</span></span>  
 <span data-ttu-id="79a86-117">일반적으로는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 의 권장 사항에 따라 **bcp**에서 제시하는 필드 길이의 기본값을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="79a86-117">Generally, [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommends that you accept the **bcp**-suggested default values for the field length.</span></span> <span data-ttu-id="79a86-118">문자 모드 데이터 파일을 만들 때 기본 필드 길이를 사용하면 데이터가 잘리지 않으며 숫자 오버플로 오류도 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79a86-118">When a character mode data file is created, using the default field length ensures that data is not truncated and that numeric overflow errors do not occur.</span></span>  
  
 <span data-ttu-id="79a86-119">필드 길이를 잘못 지정하면 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79a86-119">If you specify a field length that is incorrect, problems can occur.</span></span> <span data-ttu-id="79a86-120">예를 들어 숫자 데이터를 복사할 때 이 데이터의 필드 길이가 너무 짧으면 **bcp** 유틸리티는 오버플로 메시지를 표시하며 데이터를 복사하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79a86-120">For instance, if you copy numeric data and you specify a field length that is too short for the data, the **bcp** utility prints an overflow message and does not copy the data.</span></span> <span data-ttu-id="79a86-121">또한 데이터를 내보내고 `datetime` 문자열의 필드 길이를 26 바이트 미만으로 지정 하면 **bcp** 유틸리티는 오류 메시지 없이 데이터를 자릅니다.</span><span class="sxs-lookup"><span data-stu-id="79a86-121">Also, if you export `datetime` data and specify a field length of less than 26 bytes for the character string, the **bcp** utility truncates the data without an error message.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="79a86-122">기본 크기 옵션을 사용하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 전체 문자열을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="79a86-122">When the default size option is used, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] expects to read an entire string.</span></span> <span data-ttu-id="79a86-123">그러나 기본 필드 길이를 사용해도 "예기치 않은 파일의 끝입니다."라는 오류가 발생할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79a86-123">In some situations, use of a default field length can lead to an "unexpected end of file" error.</span></span> <span data-ttu-id="79a86-124">일반적으로이 오류는 예상 된 `money` `datetime` 필드의 일부만 데이터 파일에 있는 경우 및 데이터 형식에서 발생 합니다. 예를 들어 `datetime` *mm* / *dd* / *yy* 값이 시간 구성 요소 없이 지정 되어 형식의 값에 대 한 예상 24 문자 길이 보다 짧습니다 `datetime` `char` .</span><span class="sxs-lookup"><span data-stu-id="79a86-124">Typically, this error occurs with the `money` and `datetime` data types when only part of the expected field occurs in the data file; for example, when a `datetime` value of *mm*/*dd*/*yy* is specified without the time component and is, therefore, shorter than the expected 24 character length of a `datetime` value in `char` format.</span></span> <span data-ttu-id="79a86-125">이런 유형의 오류를 방지하려면 필드 종결자 또는 고정 길이 데이터 필드를 사용하거나 다른 값을 지정하여 기본 필드 길이를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="79a86-125">To avoid this type of error, use field terminators or fixed-length data fields, or change the default field length by specifying another value.</span></span>  
  
### <a name="default-field-lengths-for-character-file-storage"></a><span data-ttu-id="79a86-126">문자 파일 스토리지의 기본 필드 길이</span><span class="sxs-lookup"><span data-stu-id="79a86-126">Default Field Lengths for Character File Storage</span></span>  
 <span data-ttu-id="79a86-127">다음 표에서는 문자 파일 스토리지 유형으로 저장할 데이터의 기본 필드 길이를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="79a86-127">The following table lists the default field lengths for data to be stored as a character-file storage type.</span></span> <span data-ttu-id="79a86-128">Null 허용 데이터의 길이는 Null이 아닌 데이터와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="79a86-128">Nullable data is the same length as nonnull data.</span></span>  
  
|<span data-ttu-id="79a86-129">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="79a86-129">Data type</span></span>|<span data-ttu-id="79a86-130">기본 길이(문자)</span><span class="sxs-lookup"><span data-stu-id="79a86-130">Default length (characters)</span></span>|  
|---------------|-----------------------------------|  
|`char`|<span data-ttu-id="79a86-131">열에 정의된 길이</span><span class="sxs-lookup"><span data-stu-id="79a86-131">Length defined for the column</span></span>|  
|`varchar`|<span data-ttu-id="79a86-132">열에 정의된 길이</span><span class="sxs-lookup"><span data-stu-id="79a86-132">Length defined for the column</span></span>|  
|`nchar`|<span data-ttu-id="79a86-133">열에 정의된 길이의 2배</span><span class="sxs-lookup"><span data-stu-id="79a86-133">Twice the length defined for the column</span></span>|  
|`nvarchar`|<span data-ttu-id="79a86-134">열에 정의된 길이의 2배</span><span class="sxs-lookup"><span data-stu-id="79a86-134">Twice the length defined for the column</span></span>|  
|`Text`|<span data-ttu-id="79a86-135">0</span><span class="sxs-lookup"><span data-stu-id="79a86-135">0</span></span>|  
|`ntext`|<span data-ttu-id="79a86-136">0</span><span class="sxs-lookup"><span data-stu-id="79a86-136">0</span></span>|  
|`bit`|<span data-ttu-id="79a86-137">1</span><span class="sxs-lookup"><span data-stu-id="79a86-137">1</span></span>|  
|`binary`|<span data-ttu-id="79a86-138">열에 정의된 길이의 2배에 1을 더한 값</span><span class="sxs-lookup"><span data-stu-id="79a86-138">Twice the length defined for the column + 1</span></span>|  
|`varbinary`|<span data-ttu-id="79a86-139">열에 정의된 길이의 2배에 1을 더한 값</span><span class="sxs-lookup"><span data-stu-id="79a86-139">Twice the length defined for the column + 1</span></span>|  
|`image`|<span data-ttu-id="79a86-140">0</span><span class="sxs-lookup"><span data-stu-id="79a86-140">0</span></span>|  
|`datetime`|<span data-ttu-id="79a86-141">24</span><span class="sxs-lookup"><span data-stu-id="79a86-141">24</span></span>|  
|`smalldatetime`|<span data-ttu-id="79a86-142">24</span><span class="sxs-lookup"><span data-stu-id="79a86-142">24</span></span>|  
|`float`|<span data-ttu-id="79a86-143">30</span><span class="sxs-lookup"><span data-stu-id="79a86-143">30</span></span>|  
|`real`|<span data-ttu-id="79a86-144">30</span><span class="sxs-lookup"><span data-stu-id="79a86-144">30</span></span>|  
|`int`|<span data-ttu-id="79a86-145">12</span><span class="sxs-lookup"><span data-stu-id="79a86-145">12</span></span>|  
|`bigint`|<span data-ttu-id="79a86-146">19</span><span class="sxs-lookup"><span data-stu-id="79a86-146">19</span></span>|  
|`smallint`|<span data-ttu-id="79a86-147">7</span><span class="sxs-lookup"><span data-stu-id="79a86-147">7</span></span>|  
|`tinyint`|<span data-ttu-id="79a86-148">5</span><span class="sxs-lookup"><span data-stu-id="79a86-148">5</span></span>|  
|`money`|<span data-ttu-id="79a86-149">30</span><span class="sxs-lookup"><span data-stu-id="79a86-149">30</span></span>|  
|`smallmoney`|<span data-ttu-id="79a86-150">30</span><span class="sxs-lookup"><span data-stu-id="79a86-150">30</span></span>|  
|`decimal`|<span data-ttu-id="79a86-151">41\*</span><span class="sxs-lookup"><span data-stu-id="79a86-151">41\*</span></span>|  
|`numeric`|<span data-ttu-id="79a86-152">41\*</span><span class="sxs-lookup"><span data-stu-id="79a86-152">41\*</span></span>|  
|`uniqueidentifier`|<span data-ttu-id="79a86-153">37</span><span class="sxs-lookup"><span data-stu-id="79a86-153">37</span></span>|  
|`timestamp`|<span data-ttu-id="79a86-154">17</span><span class="sxs-lookup"><span data-stu-id="79a86-154">17</span></span>|  
|`varchar(max)`|<span data-ttu-id="79a86-155">0</span><span class="sxs-lookup"><span data-stu-id="79a86-155">0</span></span>|  
|`varbinary(max)`|<span data-ttu-id="79a86-156">0</span><span class="sxs-lookup"><span data-stu-id="79a86-156">0</span></span>|  
|`nvarchar(max)`|<span data-ttu-id="79a86-157">0</span><span class="sxs-lookup"><span data-stu-id="79a86-157">0</span></span>|  
|<span data-ttu-id="79a86-158">UDT</span><span class="sxs-lookup"><span data-stu-id="79a86-158">UDT</span></span>|<span data-ttu-id="79a86-159">UDT(사용자 정의 용어) 열의 길이</span><span class="sxs-lookup"><span data-stu-id="79a86-159">Length of the user-defined term (UDT) column</span></span>|  
|<span data-ttu-id="79a86-160">XML</span><span class="sxs-lookup"><span data-stu-id="79a86-160">XML</span></span>|<span data-ttu-id="79a86-161">0</span><span class="sxs-lookup"><span data-stu-id="79a86-161">0</span></span>|  
  
 <span data-ttu-id="79a86-162">\*및 데이터 형식에 대 한 자세한 내용은 `decimal` `numeric` [decimal 및 numeric &#40;transact-sql&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="79a86-162">\*For more information about the `decimal` and `numeric` data types, see [decimal and numeric &#40;Transact-SQL&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="79a86-163">`tinyint` 형식의 열은 0부터 255까지의 값을 가질 수 있으며 해당 범위의 수를 나타내는 데 필요한 최대 문자 수는 3개입니다(100부터 255까지를 표현).</span><span class="sxs-lookup"><span data-stu-id="79a86-163">A column of type `tinyint` can have values from 0 through 255; the maximum number of characters that are needed to represent any number in that range is three (representing values 100 through 255).</span></span>  
  
### <a name="default-field-lengths-for-native-file-storage"></a><span data-ttu-id="79a86-164">네이티브 File Storage의 기본 필드 길이</span><span class="sxs-lookup"><span data-stu-id="79a86-164">Default Field Lengths for Native File Storage</span></span>  
 <span data-ttu-id="79a86-165">다음 표에서는 네이티브 파일 스토리지 유형으로 저장할 데이터의 기본 필드 길이를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="79a86-165">The following table lists the default field lengths for data to be stored as native file storage type.</span></span> <span data-ttu-id="79a86-166">Null 허용 데이터의 길이는 Null이 아닌 데이터와 같으며 문자 데이터는 항상 문자 형식으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="79a86-166">Nullable data is the same length as nonnull data, and character data is always stored in character format.</span></span>  
  
|<span data-ttu-id="79a86-167">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="79a86-167">Data type</span></span>|<span data-ttu-id="79a86-168">기본 길이(문자)</span><span class="sxs-lookup"><span data-stu-id="79a86-168">Default length (characters)</span></span>|  
|---------------|-----------------------------------|  
|`bit`|<span data-ttu-id="79a86-169">1</span><span class="sxs-lookup"><span data-stu-id="79a86-169">1</span></span>|  
|`binary`|<span data-ttu-id="79a86-170">열에 정의된 길이</span><span class="sxs-lookup"><span data-stu-id="79a86-170">Length defined for the column</span></span>|  
|`varbinary`|<span data-ttu-id="79a86-171">열에 정의된 길이</span><span class="sxs-lookup"><span data-stu-id="79a86-171">Length defined for the column</span></span>|  
|`image`|<span data-ttu-id="79a86-172">0</span><span class="sxs-lookup"><span data-stu-id="79a86-172">0</span></span>|  
|`datetime`|<span data-ttu-id="79a86-173">8</span><span class="sxs-lookup"><span data-stu-id="79a86-173">8</span></span>|  
|`smalldatetime`|<span data-ttu-id="79a86-174">4</span><span class="sxs-lookup"><span data-stu-id="79a86-174">4</span></span>|  
|`float`|<span data-ttu-id="79a86-175">8</span><span class="sxs-lookup"><span data-stu-id="79a86-175">8</span></span>|  
|`real`|<span data-ttu-id="79a86-176">4</span><span class="sxs-lookup"><span data-stu-id="79a86-176">4</span></span>|  
|`int`|<span data-ttu-id="79a86-177">4</span><span class="sxs-lookup"><span data-stu-id="79a86-177">4</span></span>|  
|`bigint`|<span data-ttu-id="79a86-178">8</span><span class="sxs-lookup"><span data-stu-id="79a86-178">8</span></span>|  
|`smallint`|<span data-ttu-id="79a86-179">2</span><span class="sxs-lookup"><span data-stu-id="79a86-179">2</span></span>|  
|`tinyint`|<span data-ttu-id="79a86-180">1</span><span class="sxs-lookup"><span data-stu-id="79a86-180">1</span></span>|  
|`money`|<span data-ttu-id="79a86-181">8</span><span class="sxs-lookup"><span data-stu-id="79a86-181">8</span></span>|  
|`smallmoney`|<span data-ttu-id="79a86-182">4</span><span class="sxs-lookup"><span data-stu-id="79a86-182">4</span></span>|  
|<span data-ttu-id="79a86-183">`decimal` <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="79a86-183">`decimal` <sup>1</sup></span></span>|<sup>*</sup>|  
|<span data-ttu-id="79a86-184">`numeric` <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="79a86-184">`numeric` <sup>1</sup></span></span>|<sup>*</sup>|  
|`uniqueidentifier`|<span data-ttu-id="79a86-185">16</span><span class="sxs-lookup"><span data-stu-id="79a86-185">16</span></span>|  
|`timestamp`|<span data-ttu-id="79a86-186">8</span><span class="sxs-lookup"><span data-stu-id="79a86-186">8</span></span>|  
  
 <span data-ttu-id="79a86-187"><sup>1</sup> 및 데이터 형식에 대 한 자세한 내용은 `decimal` `numeric` [decimal 및 numeric &#40;transact-sql&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="79a86-187"><sup>1</sup> For more information about the `decimal` and `numeric` data types, see [decimal and numeric &#40;Transact-SQL&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql).</span></span>  
  
 <span data-ttu-id="79a86-188">앞의 모든 경우에서 나중에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로 다시 로드할 데이터 파일을 만들어 최소한의 스토리지 공간을 유지하려면 기본 파일 스토리지 유형의 길이 접두사와 기본 필드 길이를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="79a86-188">In all of the preceding cases, to create a data file for later reloading into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that keeps the storage space to a minimum, use a length prefix with the default file storage type and the default field length.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79a86-189">참고 항목</span><span class="sxs-lookup"><span data-stu-id="79a86-189">See Also</span></span>  
 <span data-ttu-id="79a86-190">[bcp 유틸리티](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="79a86-190">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="79a86-191">[데이터 형식&#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="79a86-191">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 <span data-ttu-id="79a86-192">[필드 및 행 종결자 지정&#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="79a86-192">[Specify Field and Row Terminators &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md) </span></span>  
 <span data-ttu-id="79a86-193">[bcp를 사용하여 데이터 파일에 접두사 길이 지정&#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="79a86-193">[Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md) </span></span>  
 <span data-ttu-id="79a86-194">[bcp를 사용하여 파일 스토리지 유형 지정&#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="79a86-194">[Specify File Storage Type by Using bcp &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md) </span></span>  
 [<span data-ttu-id="79a86-195">대량 가져오기 수행 중 Null 유지 또는 기본값 사용&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="79a86-195">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
  
