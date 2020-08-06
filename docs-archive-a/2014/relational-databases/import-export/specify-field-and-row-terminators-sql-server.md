---
title: 필드 및 행 종결자 지정(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bcp utility [SQL Server], terminators
- field terminators [SQL Server]
- data formats [SQL Server], terminators
- row terminators [SQL Server]
- terminators [SQL Server]
ms.assetid: f68b6782-f386-4947-93c4-e89110800704
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 548beeae68f5585c5cf2ba56b67027532ab43b71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741043"
---
# <a name="specify-field-and-row-terminators-sql-server"></a><span data-ttu-id="c14ae-102">필드 및 행 종결자 지정(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c14ae-102">Specify Field and Row Terminators (SQL Server)</span></span>
  <span data-ttu-id="c14ae-103">문자 데이터 필드의 경우 데이터 파일의 각 필드 끝은 *필드 종결자* 를, 그리고 각 행의 끝은 필요에 따라 *행 종결자*를 사용해 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-103">For character data fields, optional terminating characters allow you to mark the end of each field in a data file with a *field terminator* and the end of each row with a *row terminator*.</span></span> <span data-ttu-id="c14ae-104">종결 문자는 프로그램이 한 개의 필드 또는 행이 끝나고 다른 필드 또는 행이 시작되는 부분을 읽도록 나타내는 한 가지 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-104">Terminating characters are one way to indicate to programs that read the data file where one field or row ends and another field or row begins.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c14ae-105">네이티브 또는 유니코드 네이티브 형식을 사용할 때는 필드 종결자보다는 길이 접두사를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="c14ae-105">When you use native or Unicode native format, use length prefixes rather than field terminators.</span></span> <span data-ttu-id="c14ae-106">원시 형식 데이터 파일은 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 내부 이진 데이터 형식으로 저장되므로 원시 형식 데이터와 종결자가 충돌할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-106">Native format data can conflict with terminators because a native-format data file is stored in the [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] internal binary data format.</span></span>  
  
## <a name="characters-supported-as-terminators"></a><span data-ttu-id="c14ae-107">종결자로 지원되는 문자</span><span class="sxs-lookup"><span data-stu-id="c14ae-107">Characters Supported As Terminators</span></span>  
 <span data-ttu-id="c14ae-108">**bcp** 명령, BULK INSERT 문 및 OPENROWSET 대량 행 집합 공급자는 다양한 문자를 필드 또는 행 종결자로 지원하며 항상 각 종결자의 첫 번째 인스턴스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-108">The **bcp** command, BULK INSERT statement, and the OPENROWSET bulk rowset provider support a variety of characters as field or row terminators and always look for the first instance of each terminator.</span></span> <span data-ttu-id="c14ae-109">다음 표에서는 종결자로 지원되는 문자를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-109">The following table lists the supported characters for terminators.</span></span>  
  
|<span data-ttu-id="c14ae-110">종결 문자</span><span class="sxs-lookup"><span data-stu-id="c14ae-110">Terminating character</span></span>|<span data-ttu-id="c14ae-111">표시</span><span class="sxs-lookup"><span data-stu-id="c14ae-111">Indicated by</span></span>|  
|---------------------------|------------------|  
|<span data-ttu-id="c14ae-112">탭</span><span class="sxs-lookup"><span data-stu-id="c14ae-112">Tab</span></span>|<span data-ttu-id="c14ae-113">\t</span><span class="sxs-lookup"><span data-stu-id="c14ae-113">\t</span></span><br /><br /> <span data-ttu-id="c14ae-114">기본 필드 종결자입니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-114">This is the default field terminator.</span></span>|  
|<span data-ttu-id="c14ae-115">줄 바꿈 문자</span><span class="sxs-lookup"><span data-stu-id="c14ae-115">Newline character</span></span>|<span data-ttu-id="c14ae-116">\n</span><span class="sxs-lookup"><span data-stu-id="c14ae-116">\n</span></span><br /><br /> <span data-ttu-id="c14ae-117">기본 행 종결자입니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-117">This is the default row terminator.</span></span>|  
|<span data-ttu-id="c14ae-118">캐리지 리턴/줄 바꿈</span><span class="sxs-lookup"><span data-stu-id="c14ae-118">Carriage return/line feed</span></span>|<span data-ttu-id="c14ae-119">\r</span><span class="sxs-lookup"><span data-stu-id="c14ae-119">\r</span></span>|  
|<span data-ttu-id="c14ae-120">백슬래시<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="c14ae-120">Backslash<sup>1</sup></span></span>|\\\|  
|<span data-ttu-id="c14ae-121">Null 종결자 (표시 되지 않는 종결자)<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="c14ae-121">Null terminator (nonvisible terminator)<sup>2</sup></span></span>|<span data-ttu-id="c14ae-122">\0</span><span class="sxs-lookup"><span data-stu-id="c14ae-122">\0</span></span>|  
|<span data-ttu-id="c14ae-123">인쇄 가능한 모든 문자(Null, 탭, 줄 바꿈, 캐리지 리턴을 제외한 모든 제어 문자는 인쇄되지 않음)</span><span class="sxs-lookup"><span data-stu-id="c14ae-123">Any printable character (control characters are not printable, except null, tab, newline, and carriage return)</span></span>|<span data-ttu-id="c14ae-124">(\*, A, t, l 등)</span><span class="sxs-lookup"><span data-stu-id="c14ae-124">(\*, A, t, l, and so on)</span></span>|  
|<span data-ttu-id="c14ae-125">앞에서 나열된 종결 문자 중 일부 또는 전체를 포함한 최고 10개까지의 출력 가능한 문자열</span><span class="sxs-lookup"><span data-stu-id="c14ae-125">String of up to 10 printable characters, including some or all of the terminators listed earlier</span></span>|<span data-ttu-id="c14ae-126">(\*\*\t\*\*, end, !!!!!!!!!!, \t-\n 등)</span><span class="sxs-lookup"><span data-stu-id="c14ae-126">(\*\*\t\*\*, end, !!!!!!!!!!, \t-\n, and so on)</span></span>|  
  
 <span data-ttu-id="c14ae-127"><sup>1</sup> t, n, r, 0 및 ' \ 0 ' 문자만 백슬래시 이스케이프 문자와 함께 사용 하 여 제어 문자를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-127"><sup>1</sup> Only the t, n, r, 0 and '\0' characters work with the backslash escape character to produce a control character.</span></span>  
  
 <span data-ttu-id="c14ae-128"><sup>2</sup> null 제어 문자 (\ 0)는 인쇄할 때 표시 되지 않지만 데이터 파일의 고유한 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-128"><sup>2</sup> Even though the null control character (\0) is not visible when printed, it is a distinct character in the data file.</span></span> <span data-ttu-id="c14ae-129">즉, Null 제어 문자를 필드 또는 행 종결자로 사용하는 것은 필드 또는 행 종결자를 아예 사용하지 않는 것과는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-129">This means that using the null control character as a field or row terminator is different than having no field or row terminator at all.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c14ae-130">데이터 안에서 종결 문자가 나타나면 데이터가 아닌 종결자로 해석되며 종결 문자 뒤의 데이터는 다음 필드 또는 레코드에 속한 것으로 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-130">If a terminator character occurs within the data, it is interpreted as a terminator, not as data, and the data after that character is interpreted as belonging to the next field or record.</span></span> <span data-ttu-id="c14ae-131">그러므로 종결자가 데이터 안에 나타나지 않도록 신중히 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="c14ae-131">Therefore, choose your terminators carefully to make sure that they never appear in your data.</span></span> <span data-ttu-id="c14ae-132">예를 들어 데이터에 하위 서로게이트가 포함되어 있으면 필드 종결자로 하위 서로게이트 필드 종결자는 적합하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-132">For example, a low surrogate field terminator would not be a good choice for a field terminator if the data contains that low surrogate.</span></span>  
  
## <a name="using-row-terminators"></a><span data-ttu-id="c14ae-133">행 종결자 사용</span><span class="sxs-lookup"><span data-stu-id="c14ae-133">Using Row Terminators</span></span>  
 <span data-ttu-id="c14ae-134">행 종결자가 마지막 필드의 종결자와 동일한 문자일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-134">The row terminator can be the same character as the terminator for the last field.</span></span> <span data-ttu-id="c14ae-135">하지만 보통 행 종결자를 구분해 사용하는 것이 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-135">Generally, however, a distinct row terminator is useful.</span></span> <span data-ttu-id="c14ae-136">예를 들어 표로 출력하려면 각 행의 마지막 필드는 줄 바꿈 문자(\n)를 사용해 종결하고 그 밖의 필드는 탭 문자(\t)를 사용해 종결합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-136">For example, to produce tabular output, terminate the last field in each row with the newline character (\n) and all other fields with the tab character (\t).</span></span> <span data-ttu-id="c14ae-137">데이터 파일에 각 데이터 레코드를 별도의 줄로 배치하려면 행 종결자로 \r\n 조합을 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="c14ae-137">To place each data record on its own line in the data file, specify the combination \r\n as the row terminator.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c14ae-138">**bcp** 를 대화형으로 사용하고 \n(줄 바꿈)을 행 종결자로 지정하면 **bcp** 가 \r(캐리지 리턴) 문자를 접두사로 자동 지정하므로 \r\n이 행 종결자가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-138">When you use **bcp** interactively and specify \n (newline) as the row terminator, **bcp** automatically prefixes it with a \r (carriage return) character, which results in a row terminator of \r\n.</span></span>  
  
## <a name="specifying-terminators-for-bulk-export"></a><span data-ttu-id="c14ae-139">대량 내보내기를 위한 종결자 지정</span><span class="sxs-lookup"><span data-stu-id="c14ae-139">Specifying Terminators for Bulk Export</span></span>  
 <span data-ttu-id="c14ae-140">`char`또는 데이터를 대량으로 내보내거나 `nchar` 기본 종결자 이외의 종결자를 사용 하려는 경우 **bcp** 명령에 종결자를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-140">When you bulk export `char` or `nchar` data, and want to use a non-default terminator, you must specify the terminator to the **bcp** command.</span></span> <span data-ttu-id="c14ae-141">다음 중 한 가지 방법으로 종결자를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-141">You can specify terminators in any of the following ways:</span></span>  
  
-   <span data-ttu-id="c14ae-142">필드별로 종결자를 지정하는 서식 파일을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-142">With a format file that specifies the terminator on a field-by-field basis.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c14ae-143">서식 파일을 사용하는 방법에 대한 자세한 내용은 [데이터를 가져오거나 내보내기 위한 서식 파일&#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c14ae-143">For information about how to use format files, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
-   <span data-ttu-id="c14ae-144">서식 파일을 사용하지 않을 경우 다음과 같은 대체 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-144">Without a format file, the following alternatives exist:</span></span>  
  
    -   <span data-ttu-id="c14ae-145">**-t** 스위치를 사용하여 행의 마지막 필드를 제외한 모든 필드에 행 종결자를 지정하고 **-r** 스위치를 사용하여 행 종결자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-145">Using the **-t** switch to specify the row terminator for all the fields except the last field in the row and using the **-r** switch to specify a row terminator.</span></span>  
  
    -   <span data-ttu-id="c14ae-146">필드 종결자를 탭 문자 \t로 설정하는 **-t** 스위치 없이 문자 형식 스위치( **-c**또는 **-w** )를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-146">Using a character-format switch (**-c** or **-w**) without the **-t** switch, which sets the field terminator to the tab character, \t.</span></span> <span data-ttu-id="c14ae-147">이 방식은 **-t**\t를 지정하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-147">This is the same as specifying **-t**\t.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="c14ae-148">**-n** (네이티브 데이터) 또는 **-N** (유니코드 네이티브 데이터) 스위치를 지정하면 종결자는 삽입되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-148">If you specify the **-n** (native data) or **-N** (Unicode native) switch, terminators are not inserted.</span></span>  
  
    -   <span data-ttu-id="c14ae-149">대화형 **bcp** 명령에 **in** 또는 **out** 옵션이 서식 파일 스위치( **-f**) 또는 데이터 형식 스위치( **-n**, **-c**, **-w**또는 **-N**) 없이 포함되어 있고 접두사 길이 및 필드 길이를 지정하지 않도록 선택했다면 명령에서 각 필드의 필드 종결자를 지정하라는 메시지가 표시됩니다. 기본값은 none입니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-149">If an interactive **bcp** command contains the **in** or **out** option without either the format file switch (**-f**) or a data-format switch (**-n**, **-c**, **-w**, or **-N**), and you have chosen not to specify prefix length and field length, the command prompts for the field terminator of each field, with a default of none:</span></span>  
  
         `Enter field terminator [none]:`  
  
         <span data-ttu-id="c14ae-150">일반적으로 기본값을 사용하면 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-150">Generally, the default is a suitable choice.</span></span> <span data-ttu-id="c14ae-151">하지만 `char` 또는 `nchar` 데이터 필드의 경우 다음 하위 섹션인 "종결자 사용 지침"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c14ae-151">However, for `char` or `nchar` data fields, see the following subsection, "Guidelines for Using Terminators."</span></span> <span data-ttu-id="c14ae-152">컨텍스트에서 이 메시지가 표시되는 예제를 보려면 [bcp를 사용하여 데이터 형식을 호환 가능하도록 지정&#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c14ae-152">For an example that shows this prompt in context, see [Specify Data Formats for Compatibility when Using bcp &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md).</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="c14ae-153">**bcp** 명령의 모든 필드를 대화형으로 지정하면 명령에서 비 XML 서식 파일의 각 필드에 대한 응답을 저장하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-153">After you interactively specify all of the fields in a **bcp** command, the command prompts you save your responses for each field in a non-XML format file.</span></span> <span data-ttu-id="c14ae-154">비 XML 서식 파일에 대한 자세한 내용은 [비 XML 서식 파일&#40;SQL Server&#41;](xml-format-files-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c14ae-154">For more information about non-XML format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
### <a name="guidelines-for-using-terminators"></a><span data-ttu-id="c14ae-155">종결자 사용 지침</span><span class="sxs-lookup"><span data-stu-id="c14ae-155">Guidelines for Using Terminators</span></span>  
 <span data-ttu-id="c14ae-156">상황에 따라 종결자는 `char` 또는 `nchar` 데이터 필드에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-156">In some situations, a terminator is useful for a `char` or `nchar` data field.</span></span> <span data-ttu-id="c14ae-157">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-157">For example:</span></span>  
  
-   <span data-ttu-id="c14ae-158">접두사 길이 정보를 인식하지 못하는 프로그램으로 가져올 데이터 파일에서 Null 값을 포함하는 데이터 열</span><span class="sxs-lookup"><span data-stu-id="c14ae-158">For a data column that contains a null value in a data file that will be imported into a program that does not understand the prefix length information.</span></span>  
  
     <span data-ttu-id="c14ae-159">Null 값을 포함하는 모든 데이터 열은 가변 길이로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-159">Any data column that contains a null value is considered variable length.</span></span> <span data-ttu-id="c14ae-160">접두사 길이가 없는 경우 데이터가 올바르게 해석되도록 Null 필드의 끝을 식별하는 종결자가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-160">In the absence of prefix lengths, a terminator is necessary to identify the end of a null field, making sure that the data is correctly interpreted.</span></span>  
  
-   <span data-ttu-id="c14ae-161">긴 고정 길이 열. 이러한 열에 포함된 공백은 대부분의 행에서 일부만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-161">For a long fixed-length column whose space is only partially used by many rows.</span></span>  
  
     <span data-ttu-id="c14ae-162">이 경우 종결자를 지정하면 스토리지 공간이 최소화되어 필드를 가변 길이 필드로 취급할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-162">In this situation, specifying a terminator can minimize storage space allowing the field to be treated as a variable-length field.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="c14ae-163">예</span><span class="sxs-lookup"><span data-stu-id="c14ae-163">Examples</span></span>  
 <span data-ttu-id="c14ae-164">이 예에서는 `AdventureWorks``HumanResources.Department` 테이블의 데이터를 문자 형식을 사용하는 `Department-c-t.txt` 데이터 파일로 대량으로 내보내며 쉼표를 필드 종결자로, 줄 바꿈 문자(\n)를 행 종결자로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-164">This example bulk exports the data from the `AdventureWorks``HumanResources.Department` table to the `Department-c-t.txt` data file using character format, with a comma as a field terminator and the newline character (\n) as the row terminator.</span></span>  
  
 <span data-ttu-id="c14ae-165">**bcp** 명령에는 다음 스위치가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-165">The **bcp** command contains the following switches.</span></span>  
  
|<span data-ttu-id="c14ae-166">스위치</span><span class="sxs-lookup"><span data-stu-id="c14ae-166">Switch</span></span>|<span data-ttu-id="c14ae-167">Description</span><span class="sxs-lookup"><span data-stu-id="c14ae-167">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c14ae-168">**-c**</span><span class="sxs-lookup"><span data-stu-id="c14ae-168">**-c**</span></span>|<span data-ttu-id="c14ae-169">데이터 필드가 데이터 문자로 로드되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-169">Specifies that the data fields be loaded as character data.</span></span>|  
|<span data-ttu-id="c14ae-170">**-t** `,`</span><span class="sxs-lookup"><span data-stu-id="c14ae-170">**-t** `,`</span></span>|<span data-ttu-id="c14ae-171">쉼표(,)를 필드 종결자로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-171">Specifies a comma (,) as the field terminator.</span></span>|  
|<span data-ttu-id="c14ae-172">**-r** \n</span><span class="sxs-lookup"><span data-stu-id="c14ae-172">**-r** \n</span></span>|<span data-ttu-id="c14ae-173">행 종결자를 줄 바꿈 문자로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-173">Specifies the row terminator as a newline character.</span></span> <span data-ttu-id="c14ae-174">이것은 기본 행 종결자이므로 이를 지정하는 것은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-174">This is the default row terminator, so specifying it is optional.</span></span>|  
|<span data-ttu-id="c14ae-175">**-T**</span><span class="sxs-lookup"><span data-stu-id="c14ae-175">**-T**</span></span>|<span data-ttu-id="c14ae-176">**bcp** 유틸리티가 통합 보안을 사용하는 트러스트된 연결을 통해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로 연결되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-176">Specifies that the **bcp** utility connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with a trusted connection using integrated security.</span></span> <span data-ttu-id="c14ae-177">**-T** 를 지정하지 않은 경우 성공적으로 로그인하려면 **-U** 와 **-P** 를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-177">If **-T** is not specified, you need to specify **-U** and **-P** to successfully log in.</span></span>|  
  
 <span data-ttu-id="c14ae-178">자세한 내용은 [bcp Utility](../../tools/bcp-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c14ae-178">For more information, see [bcp Utility](../../tools/bcp-utility.md).</span></span>  
  
 <span data-ttu-id="c14ae-179">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 명령 프롬프트에 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-179">At the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt enter:</span></span>  
  
```  
bcp AdventureWorks.HumanResources.Department out C:\myDepartment-c-t.txt -c -t, -r \n -T  
```  
  
 <span data-ttu-id="c14ae-180">이렇게 하면 각각 4개 필드로 된 16개의 레코드가 포함된 `Department-c-t.txt`가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-180">This creates `Department-c-t.txt`, which contains 16 records with four fields each.</span></span> <span data-ttu-id="c14ae-181">필드는 열로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-181">The fields are separated by a comma.</span></span>  
  
## <a name="specifying-terminators-for-bulk-import"></a><span data-ttu-id="c14ae-182">대량 가져오기를 위한 종결자 지정</span><span class="sxs-lookup"><span data-stu-id="c14ae-182">Specifying Terminators for Bulk Import</span></span>  
 <span data-ttu-id="c14ae-183">`char` 또는 `nchar` 데이터를 대량으로 가져올 때 대량 가져오기 명령이 데이터 파일에 사용된 종결자를 인식해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-183">When you bulk import `char` or `nchar` data, the bulk-import command must recognize the terminators that are used in the data file.</span></span> <span data-ttu-id="c14ae-184">종결자 지정 방법은 대량 가져오기 명령에 따라 다르며 다음과 같이 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-184">How terminators can be specified depends on the bulk-import command, as follows:</span></span>  
  
-   <span data-ttu-id="c14ae-185">**bcp**</span><span class="sxs-lookup"><span data-stu-id="c14ae-185">**bcp**</span></span>  
  
     <span data-ttu-id="c14ae-186">가져오기 작업을 위해 종결자를 지정하는 구문은 내보내기 작업을 위해 종결자를 지정하는 구문과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-186">Specifying terminators for an import operation uses the same syntax as for an export operation.</span></span> <span data-ttu-id="c14ae-187">자세한 내용은 이 항목의 앞부분에 나오는 "대량 내보내기를 위한 종결자 지정"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c14ae-187">For more information, see "Specifying Terminators for Bulk Export," earlier in this topic.</span></span>  
  
-   <span data-ttu-id="c14ae-188">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="c14ae-188">BULK INSERT</span></span>  
  
     <span data-ttu-id="c14ae-189">다음 표에서 나타나는 한정자를 사용하여 서식 파일에서 필드별로 종결자를 지정하거나 전체 데이터 파일에 대해 종결자를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-189">Terminators can be specified for individual fields in a format file or for the whole data file by using the qualifiers shown in the following table.</span></span>  
  
    |<span data-ttu-id="c14ae-190">한정자</span><span class="sxs-lookup"><span data-stu-id="c14ae-190">Qualifier</span></span>|<span data-ttu-id="c14ae-191">설명</span><span class="sxs-lookup"><span data-stu-id="c14ae-191">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="c14ae-192">FIELDTERMINATOR **= ' *`field_terminator`* '**</span><span class="sxs-lookup"><span data-stu-id="c14ae-192">FIELDTERMINATOR **='*`field_terminator`*'**</span></span>|<span data-ttu-id="c14ae-193">문자 및 유니코드 문자 데이터 파일에 사용할 필드 종결자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-193">Specifies the field terminator to be used for character and Unicode character data files.</span></span><br /><br /> <span data-ttu-id="c14ae-194">기본값은 \t(탭 문자)입니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-194">The default is \t (tab character).</span></span>|  
    |<span data-ttu-id="c14ae-195">ROWTERMINATOR **= ' *`row_terminator`* '**</span><span class="sxs-lookup"><span data-stu-id="c14ae-195">ROWTERMINATOR **='*`row_terminator`*'**</span></span>|<span data-ttu-id="c14ae-196">문자 및 유니코드 문자 데이터 파일에 사용할 행 종결자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-196">Specifies the row terminator to be used for character and Unicode character data files.</span></span><br /><br /> <span data-ttu-id="c14ae-197">기본값은 \n(줄 바꿈 문자)입니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-197">The default is \n (newline character).</span></span>|  
  
     <span data-ttu-id="c14ae-198">자세한 내용은 [BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c14ae-198">For more information, see [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
-   <span data-ttu-id="c14ae-199">INSERT ... 선택 \* OPENROWSET (BULK)에서</span><span class="sxs-lookup"><span data-stu-id="c14ae-199">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>  
  
     <span data-ttu-id="c14ae-200">OPENROWSET 대량 행 집합 공급자의 경우 종결자는 서식 파일에서만 지정할 수 있습니다(큰 개체 데이터 형식 이외의 형식에 필요).</span><span class="sxs-lookup"><span data-stu-id="c14ae-200">For the OPENROWSET bulk rowset provider, terminators can be specified only in the format file (which is required except for large-object data types).</span></span> <span data-ttu-id="c14ae-201">문자 데이터 파일이 기본 종결자 이외의 종결자를 사용하면 이를 서식 파일에 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-201">If a character data file uses a non-default terminator, it must be defined in the format file.</span></span> <span data-ttu-id="c14ae-202">자세한 내용은 [서식 파일 만들기&#40;SQL Server&#41;](create-a-format-file-sql-server.md) 및 [서식 파일을 사용하여 데이터 대량 가져오기&#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c14ae-202">For more information, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md) and [Use a Format File to Bulk Import Data &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md).</span></span>  
  
     <span data-ttu-id="c14ae-203">OPENROWSET BULK 절에 대한 자세한 내용은 [OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)를 사용해 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-203">For more information about the OPENROWSET BULK clause, see [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
### <a name="examples"></a><span data-ttu-id="c14ae-204">예</span><span class="sxs-lookup"><span data-stu-id="c14ae-204">Examples</span></span>  
 <span data-ttu-id="c14ae-205">이 섹션의 예에서는 앞의 예에서 생성한 `Department-c-t.txt` 데이터 파일의 문자 데이터를 `myDepartment` 예제 데이터베이스의 [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] 테이블로 대량으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-205">The examples in this section bulk import character data form the `Department-c-t.txt` data file created in the preceding example into the `myDepartment` table in the [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] sample database.</span></span> <span data-ttu-id="c14ae-206">예를 실행하려면 이 테이블을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-206">Before you can run the examples, you must create this table.</span></span> <span data-ttu-id="c14ae-207">**dbo** 스키마 아래에 이 테이블을 만들려면 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-207">To create this table under the **dbo** schema, in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>  
  
```  
USE AdventureWorks;  
GO  
DROP TABLE myDepartment;  
CREATE TABLE myDepartment   
(DepartmentID smallint,  
Name nvarchar(50),  
GroupName nvarchar(50) NULL,  
ModifiedDate datetime not NULL CONSTRAINT DF_AddressType_ModifiedDate DEFAULT (GETDATE())  
);  
GO  
  
```  
  
#### <a name="a-using-bcp-to-interactively-specify-terminators"></a><span data-ttu-id="c14ae-208">A.</span><span class="sxs-lookup"><span data-stu-id="c14ae-208">A.</span></span> <span data-ttu-id="c14ae-209">bcp를 사용하여 대화형으로 종결자 지정</span><span class="sxs-lookup"><span data-stu-id="c14ae-209">Using bcp to interactively specify terminators</span></span>  
 <span data-ttu-id="c14ae-210">다음 예에서는 `Department-c-t.txt` 명령을 사용하여 `bcp` 데이터 파일을 대량으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-210">The following example bulk imports the `Department-c-t.txt` data file using a `bcp` command.</span></span> <span data-ttu-id="c14ae-211">이 명령은 대량 내보내기 명령과 동일한 명령 스위치를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-211">This command uses the same command switches as the bulk export command.</span></span> <span data-ttu-id="c14ae-212">자세한 내용은 이 항목의 앞부분에 나오는 "대량 내보내기를 위한 종결자 지정"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c14ae-212">For more information, see "Specifying Terminators for Bulk Export," earlier in this topic.</span></span>  
  
 <span data-ttu-id="c14ae-213">Windows 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-213">At the Windows command prompt enter:</span></span>  
  
```  
bcp AdventureWorks..myDepartment in C:\myDepartment-c-t.txt -c -t , -r \n -T  
```  
  
#### <a name="b-using-bulk-insert-to-interactively-specify-terminators"></a><span data-ttu-id="c14ae-214">B.</span><span class="sxs-lookup"><span data-stu-id="c14ae-214">B.</span></span> <span data-ttu-id="c14ae-215">BULK INSERT를 사용하여 대화형으로 종결자 지정</span><span class="sxs-lookup"><span data-stu-id="c14ae-215">Using BULK INSERT to interactively specify terminators</span></span>  
 <span data-ttu-id="c14ae-216">다음 예에서는 다음 표에 나타나는 한정자를 사용하는 `Department-c-t.txt` 문을 사용하여 `BULK INSERT` 데이터 파일을 대량으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-216">The following example bulk imports the `Department-c-t.txt` data file using a `BULK INSERT` statement that uses the qualifiers shown in the following table.</span></span>  
  
|<span data-ttu-id="c14ae-217">옵션</span><span class="sxs-lookup"><span data-stu-id="c14ae-217">Option</span></span>|<span data-ttu-id="c14ae-218">attribute</span><span class="sxs-lookup"><span data-stu-id="c14ae-218">Attribute</span></span>|  
|------------|---------------|  
|<span data-ttu-id="c14ae-219">DATAFILETYPE **= ' `char` '**</span><span class="sxs-lookup"><span data-stu-id="c14ae-219">DATAFILETYPE **='`char`'**</span></span>|<span data-ttu-id="c14ae-220">데이터 필드가 데이터 문자로 로드되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-220">Specifies that the data fields be loaded as character data.</span></span>|  
|<span data-ttu-id="c14ae-221">FIELDTERMINATOR **='** `,` **'**</span><span class="sxs-lookup"><span data-stu-id="c14ae-221">FIELDTERMINATOR **='**`,`**'**</span></span>|<span data-ttu-id="c14ae-222">쉼표(`,`)를 필드 종결자로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-222">Specifies a comma (`,`) as the field terminator.</span></span>|  
|<span data-ttu-id="c14ae-223">ROWTERMINATOR **='** `\n` **'**</span><span class="sxs-lookup"><span data-stu-id="c14ae-223">ROWTERMINATOR **='**`\n`**'**</span></span>|<span data-ttu-id="c14ae-224">행 종결자를 줄 바꿈 문자로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-224">Specifies the row terminator as a newline character.</span></span>|  
  
 <span data-ttu-id="c14ae-225">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c14ae-225">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT myDepartment FROM 'C:\myDepartment-c-t.txt'  
   WITH (  
      DATAFILETYPE = 'char',  
      FIELDTERMINATOR = ',',  
      ROWTERMINATOR = '\n'  
);  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="c14ae-226">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c14ae-226">See Also</span></span>  
 <span data-ttu-id="c14ae-227">[bcp 유틸리티](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="c14ae-227">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="c14ae-228">[BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c14ae-228">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="c14ae-229">[OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c14ae-229">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="c14ae-230">[bcp를 사용하여 필드 길이 지정&#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c14ae-230">[Specify Field Length by Using bcp &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md) </span></span>  
 <span data-ttu-id="c14ae-231">[bcp를 사용하여 데이터 파일에 접두사 길이 지정&#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c14ae-231">[Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md) </span></span>  
 [<span data-ttu-id="c14ae-232">bcp를 사용하여 파일 스토리지 유형 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c14ae-232">Specify File Storage Type by Using bcp &#40;SQL Server&#41;</span></span>](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
  
