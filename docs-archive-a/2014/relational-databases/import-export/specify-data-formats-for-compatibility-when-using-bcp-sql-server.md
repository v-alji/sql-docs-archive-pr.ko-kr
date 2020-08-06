---
title: bcp를 사용하여 데이터 형식을 호환 가능하도록 지정(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk exporting [SQL Server], compatibility
- bulk importing [SQL Server], compatibility
- compatibility [SQL Server], data formats
- data formats [SQL Server], compatibility
- bcp utility [SQL Server], compatibility
ms.assetid: cd5fc8c8-eab1-4165-9468-384f31e53f0a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5d12456760f32ddbd8cc434d474aebb0e0ecf141
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738422"
---
# <a name="specify-data-formats-for-compatibility-when-using-bcp-sql-server"></a><span data-ttu-id="2a22c-102">bcp를 사용하여 데이터 형식을 호환 가능하도록 지정(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2a22c-102">Specify Data Formats for Compatibility when Using bcp (SQL Server)</span></span>
  <span data-ttu-id="2a22c-103">이 항목에서는 데이터 형식 특성과 필드별 프롬프트에 대해 설명 하 고 명령의 비 xml 서식 파일에 필드 단위로 데이터를 저장 하는 방법에 대해 설명 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `bcp` .</span><span class="sxs-lookup"><span data-stu-id="2a22c-103">This topic describes the data-format attributes, field-specific prompts, and storing field-by-field data in a non-xml format file of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`bcp` command.</span></span> <span data-ttu-id="2a22c-104">이러한 개념을 잘 알고 있으면 다른 데이터베이스 프로그램과 같은 다른 프로그램으로 대량으로 가져오기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터를 대량으로 내보낼 때 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-104">Understanding these can be helpful when you bulk export [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data for bulk import into another program, such as another database program.</span></span> <span data-ttu-id="2a22c-105">원본 테이블의 기본 데이터 형식(네이티브, 문자 또는 유니코드)이 다른 프로그램에서 필요한 데이터 레이아웃과 호환되지 않을 수 있습니다. 호환되지 않는 경우 데이터를 내보낼 때는 데이터 레이아웃을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-105">The default data formats (native, character, or Unicode) in the source table might be incompatible with the data layout expected by the other program If an incompatibility exists, when you export the data, you must describe the data layout.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2a22c-106">데이터를 가져오거나 내보내기 위한 데이터 형식에 익숙하지 않은 경우 [대량 가져오기 또는 대량 내보내기를 위한 데이터 형식&#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a22c-106">If you are unfamiliar with data formats for importing or exporting data, see [Data Formats for Bulk Import or Bulk Export &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md).</span></span>  
  
 <span data-ttu-id="2a22c-107">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="2a22c-107">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="2a22c-108">bcp 데이터 형식 특성</span><span class="sxs-lookup"><span data-stu-id="2a22c-108">bcp Data-Format Attributes</span></span>](#bcpDataFormatAttr)  
  
-   [<span data-ttu-id="2a22c-109">필드별 프롬프트 개요</span><span class="sxs-lookup"><span data-stu-id="2a22c-109">Overview of the Field-Specific Prompts</span></span>](#FieldSpecificPrompts)  
  
-   [<span data-ttu-id="2a22c-110">비 XML 서식 파일에 필드 필드 데이터 저장</span><span class="sxs-lookup"><span data-stu-id="2a22c-110">Storing Field-by-Field Data in a Non-XML Format File</span></span>](#FieldByFieldNonXmlFF)  
  
-   [<span data-ttu-id="2a22c-111">관련 작업</span><span class="sxs-lookup"><span data-stu-id="2a22c-111">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="bcp-data-format-attributes"></a><a name="bcpDataFormatAttr"></a> <span data-ttu-id="2a22c-112">bcp 데이터 형식 특성</span><span class="sxs-lookup"><span data-stu-id="2a22c-112">bcp Data-Format Attributes</span></span>  
 <span data-ttu-id="2a22c-113">`bcp` 명령을 사용하여 데이터 파일 내 각 필드의 구조를 다음 데이터 형식 특성에 따라 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-113">The `bcp` command allows you to specify the structure of each field in a data file in terms of the following data-format attributes:</span></span>  
  
-   <span data-ttu-id="2a22c-114">파일 스토리지 유형</span><span class="sxs-lookup"><span data-stu-id="2a22c-114">File storage type</span></span>  
  
     <span data-ttu-id="2a22c-115">*파일 스토리지 유형* 은 데이터 파일에서 데이터가 저장되는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-115">The *file storage type* describes how data is stored in the data file.</span></span> <span data-ttu-id="2a22c-116">데이터는 데이터베이스 테이블 형식(네이티브 형식), 문자 표시(문자 형식) 또는 암시적 변환을 지원하는 모든 데이터 형식의 데이터 파일로 내보낼 수 있습니다. 예를 들어 `smallint`를 `int`로 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-116">Data can be exported to a data file as its database table type (native format), in its character representation (character format), or as any data type where implicit conversion is supported; for example, copying a `smallint` as an `int`.</span></span> <span data-ttu-id="2a22c-117">사용자 정의 데이터 형식은 해당 기본 형식으로 내보내집니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-117">User-defined data types are exported as their base types.</span></span> <span data-ttu-id="2a22c-118">자세한 내용은 [bcp를 사용하여 파일 스토리지 유형 지정&#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a22c-118">For more information, see [Specify File Storage Type by Using bcp &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md).</span></span>  
  
-   <span data-ttu-id="2a22c-119">접두사 길이</span><span class="sxs-lookup"><span data-stu-id="2a22c-119">Prefix length</span></span>  
  
     <span data-ttu-id="2a22c-120">네이티브 형식의 데이터를 데이터 파일로 대량 내보내는 작업에서 가장 압축된 형식으로 파일을 스토리지하려면 각 필드에 필드 길이를 나타내는 하나 이상의 문자와 함께 `bcp` 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-120">To provide the most compact file storage for the bulk export of data in native format to a data file, the `bcp` command precedes each field with one or more characters that indicates the length of the field.</span></span> <span data-ttu-id="2a22c-121">이러한 문자를 *길이 접두사 문자*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-121">These characters are called *length prefix characters*.</span></span> <span data-ttu-id="2a22c-122">자세한 내용은 [bcp를 사용하여 데이터 파일에 접두사 길이 지정&#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a22c-122">For more information, see [Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md).</span></span>  
  
-   <span data-ttu-id="2a22c-123">필드 길이</span><span class="sxs-lookup"><span data-stu-id="2a22c-123">Field length</span></span>  
  
     <span data-ttu-id="2a22c-124">필드 길이는 데이터를 문자 형식으로 표시하는 데 필요한 최대 문자 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-124">The field length indicates the maximum number of characters that are required to represent data in character format.</span></span> <span data-ttu-id="2a22c-125">데이터가 네이티브 형식으로 저장된 경우에는 필드 길이를 미리 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-125">The field length is already known if the data is stored in the native format.</span></span> <span data-ttu-id="2a22c-126">자세한 내용은 [bcp를 사용하여 필드 길이 지정&#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a22c-126">For more information, see [Specify Field Length by Using bcp &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md).</span></span>  
  
-   <span data-ttu-id="2a22c-127">필드 종결자</span><span class="sxs-lookup"><span data-stu-id="2a22c-127">Field terminator</span></span>  
  
     <span data-ttu-id="2a22c-128">문자 데이터 필드에서 필요에 따라 종료 문자를 사용하면 데이터 파일 내 각 필드( *필드 종결자*사용)와 행( *행 종결자*사용)의 끝을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-128">For character data fields, optional terminating characters allow you to mark the end of each field in a data file (using a *field terminator*) and the end of each row (using a *row terminator*).</span></span> <span data-ttu-id="2a22c-129">종결 문자는 한 필드나 행이 끝나고 다른 필드나 행이 시작하는 부분을 표시하여 데이터 파일을 읽는 프로그램에 전달하는 한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-129">Terminating characters are one way to indicate to programs reading the data file where one field or row ends and another begins.</span></span> <span data-ttu-id="2a22c-130">자세한 내용은 [필드 및 행 종결자 지정&#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a22c-130">For more information, see [Specify Field and Row Terminators &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).</span></span>  
  
##  <a name="overview-of-the-field-specific-prompts"></a><a name="FieldSpecificPrompts"></a> <span data-ttu-id="2a22c-131">필드별 프롬프트 개요</span><span class="sxs-lookup"><span data-stu-id="2a22c-131">Overview of the Field-Specific Prompts</span></span>  
 <span data-ttu-id="2a22c-132">대화형 `bcp` 명령 **에 in** 또는 **out** 옵션이 포함 되어 있지만 형식 파일 스위치 (**-f**) 또는 데이터 형식 스위치 (**-n**, **-c**, **-w**또는 **-n**)가 포함 되어 있지 않은 경우 원본 또는 대상 테이블의 각 열에 대해 명령에서 각 이전 특성에 대해 차례로 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-132">If an interactive `bcp` command contains the **in** or **out** option but does not also contain either the format file switch (**-f**) or a data-format switch (**-n**, **-c**, **-w**, or **-N**),  each column in the source or target table, the command prompts for each of the preceding attributes, in turn.</span></span> <span data-ttu-id="2a22c-133">각 프롬프트에서 `bcp` 명령은 테이블 열의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식에 따라 기본값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-133">In each prompt, the `bcp` command provides a default value based on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type of the table column.</span></span> <span data-ttu-id="2a22c-134">모든 메시지에서 기본값을 그대로 사용하면 명령줄에서 네이티브 형식( **-n**)을 지정한 것과 동일한 결과가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-134">Accepting the default value for all of the prompts produces the same result as specifying native format (**-n**) on the command line.</span></span> <span data-ttu-id="2a22c-135">각 프롬프트에서 기본값은 [*default*]와 같이 대괄호에 묶여 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-135">Each prompt displays a default value in brackets: [*default*].</span></span> <span data-ttu-id="2a22c-136">표시된 기본값을 적용하려면 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-136">Pressing ENTER accepts the displayed default.</span></span> <span data-ttu-id="2a22c-137">기본값 이외의 값을 지정하려면 프롬프트에서 새 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-137">To specify a value other than the default, enter the new value at the prompt.</span></span>  
  
### <a name="example"></a><span data-ttu-id="2a22c-138">예제</span><span class="sxs-lookup"><span data-stu-id="2a22c-138">Example</span></span>  
 <span data-ttu-id="2a22c-139">다음 예에서는 `bcp` 명령을 사용하여 대화형으로 `HumanResources.myTeam` 테이블에서 `myTeam.txt` 파일로 데이터를 대량 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-139">The following example uses the `bcp` command to bulk export data from the `HumanResources.myTeam` table interactively to the `myTeam.txt` file.</span></span> <span data-ttu-id="2a22c-140">예를 실행하려면 이 테이블을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-140">Before you can run the example, you must create this table.</span></span> <span data-ttu-id="2a22c-141">테이블 및 테이블을 만드는 방법은 [HumanResources.myTeam 예제 테이블&#40;SQL Server&#41;](humanresources-myteam-sample-table-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a22c-141">For information about the table and how to create it, see [HumanResources.myTeam Sample Table &#40;SQL Server&#41;](humanresources-myteam-sample-table-sql-server.md).</span></span>  
  
 <span data-ttu-id="2a22c-142">명령에서 서식 파일이나 데이터 형식을 지정하지 않기 때문에 `bcp`는 데이터 형식 정보를 묻는 프롬프트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-142">The command specifies neither a format file nor a data type, causing `bcp` to prompt for data-format information.</span></span> <span data-ttu-id="2a22c-143">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 명령 프롬프트에 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-143">At the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks.HumanResources.myTeam out myTeam.txt -T  
```  
  
 <span data-ttu-id="2a22c-144">각 열에 대해 bcp는 필드별 값을 묻는 프롬프트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-144">For each column, bcp prompts for field-specific values.</span></span> <span data-ttu-id="2a22c-145">다음 예는 테이블의 `EmployeeID` 및 `Name` 열에 대한 필드별 프롬프트를 보여 주며 각 열에 대한 기본 파일 스토리지 유형(네이티브 형식)을 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-145">The following example shows the field-specific prompts for the `EmployeeID` and `Name` columns of the table, and suggests the default file storage type (the native format) for each column.</span></span> <span data-ttu-id="2a22c-146">`EmployeeID` 및 `Name` 열의 접두사 길이는 각각 0, 2입니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-146">The prefix lengths of the `EmployeeID` and `Name` column are 0 and 2, respectively.</span></span> <span data-ttu-id="2a22c-147">사용자는 각 필드의 종결자로 쉼표(`,`)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-147">The user specifies a comma (`,`) as the terminator of each field.</span></span>  
  
 `Enter the file storage type of field EmployeeID [smallint]:`  
  
 `Enter prefix-length of field EmployeeID [0]:`  
  
 `Enter field terminator [none]:,`  
  
 `Enter the file storage type of field Name [nvarchar]:`  
  
 `Enter prefix length of field Name [2]:`  
  
 `Enter field terminator [none]:,`  
  
 `.`  
  
 `.`  
  
 `.`  
  
 <span data-ttu-id="2a22c-148">각 테이블 열에 대한 프롬프트(필요한 경우에만)가 순서대로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-148">Equivalent prompts (as needed) are displayed for each of the table columns in order.</span></span>  
  
##  <a name="storing-field-by-field-data-in-a-non-xml-format-file"></a><a name="FieldByFieldNonXmlFF"></a> <span data-ttu-id="2a22c-149">비 XML 서식 파일에 필드 단위 데이터 저장</span><span class="sxs-lookup"><span data-stu-id="2a22c-149">Storing Field-by-Field Data in a Non-XML Format File</span></span>  
 <span data-ttu-id="2a22c-150">테이블 열이 모두 지정된 후 `bcp` 명령은 방금 제공된 필드 단위 정보를 저장할 비 XML 서식 파일을 만들 것인지 묻는 메시지를 표시합니다(이전 예 참조).</span><span class="sxs-lookup"><span data-stu-id="2a22c-150">After all of the table columns are specified, the `bcp` command prompts you to optionally generate a non-XML format file that stores the field-by-field information just supplied (see the preceding example).</span></span> <span data-ttu-id="2a22c-151">서식 파일 생성하도록 선택하면 해당 테이블에서 데이터를 내보내거나 구조가 비슷한 데이터를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 가져올 때마다 서식 파일을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-151">If you choose to generate a format file, you can whenever you export data out of that table or import like-structured data into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2a22c-152">서식 파일을 사용하면 데이터 파일에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 인스턴스로 데이터를 대량 가져오거나 테이블에서 데이터를 대량 내보낼 때 서식을 다시 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-152">You can use the format file to bulk import data from the data file into an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or to bulk export data from the table, without needing to respecify the format.</span></span> <span data-ttu-id="2a22c-153">자세한 내용은 [데이터를 가져오거나 내보내기 위한 서식 파일&#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a22c-153">For more information, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="2a22c-154">다음 예에서는 `myFormatFile.fmt`라는 비 XML 서식 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-154">The following example creates a non-XML format file named `myFormatFile.fmt`:</span></span>  
  
 `Do you want to save this format information in a file? [Y/n] y`  
  
 `Host filename: [bcp.fmt]myFormatFile.fmt`  
  
 <span data-ttu-id="2a22c-155">서식 파일의 기본 이름은 bcp.fmt지만 필요하다면 다른 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-155">The default name for the format file is bcp.fmt, but you can specify a different file name if you choose.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2a22c-156">문자 또는 네이티브 형식과 같은 하나의 데이터 형식으로 파일을 스토리지하는 데이터 파일의 경우 **format** 옵션을 사용하면 데이터를 내보내거나 가져올 필요 없이 즉시 형식 파일을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-156">For a data file that uses a single data format for its file-storage type, such as character or native format, you can quickly create a format file without exporting or importing data by using the **format** option.</span></span> <span data-ttu-id="2a22c-157">이 방법은 쉽고, XML 서식 파일뿐 아니라 비 XML 서식 파일도 만들 수 있다는 장점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a22c-157">This approach has the advantages of being easy and of allowing you to create either an XML format file or a non-XML format file.</span></span> <span data-ttu-id="2a22c-158">자세한 내용은 [서식 파일 만들기&#40;SQL Server&#41;](create-a-format-file-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a22c-158">For more information, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="2a22c-159">관련 작업</span><span class="sxs-lookup"><span data-stu-id="2a22c-159">Related Tasks</span></span>  
  
-   [<span data-ttu-id="2a22c-160">bcp를 사용하여 파일 스토리지 유형 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2a22c-160">Specify File Storage Type by Using bcp &#40;SQL Server&#41;</span></span>](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
-   [<span data-ttu-id="2a22c-161">bcp를 사용하여 데이터 파일에 접두사 길이 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2a22c-161">Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;</span></span>](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
-   [<span data-ttu-id="2a22c-162">bcp를 사용하여 필드 길이 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2a22c-162">Specify Field Length by Using bcp &#40;SQL Server&#41;</span></span>](specify-field-length-by-using-bcp-sql-server.md)  
  
-   [<span data-ttu-id="2a22c-163">필드 및 행 종결자 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2a22c-163">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](specify-field-and-row-terminators-sql-server.md)  
  
## <a name="related-content"></a><span data-ttu-id="2a22c-164">관련 내용</span><span class="sxs-lookup"><span data-stu-id="2a22c-164">Related Content</span></span>  
 <span data-ttu-id="2a22c-165">없음</span><span class="sxs-lookup"><span data-stu-id="2a22c-165">None.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a22c-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2a22c-166">See Also</span></span>  
 <span data-ttu-id="2a22c-167">[데이터 대량 가져오기 및 내보내기&#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2a22c-167">[Bulk Import and Export of Data &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span></span>  
 <span data-ttu-id="2a22c-168">[대량 가져오기 또는 대량 내보내기를 위한 데이터 형식&#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2a22c-168">[Data Formats for Bulk Import or Bulk Export &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md) </span></span>  
 <span data-ttu-id="2a22c-169">[bcp 유틸리티](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="2a22c-169">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 [<span data-ttu-id="2a22c-170">데이터 형식&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2a22c-170">Data Types &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/data-types-transact-sql)  
  
  
