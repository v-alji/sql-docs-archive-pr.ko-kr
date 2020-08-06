---
title: XML 서식 파일(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- format files [SQL Server], XML format files
- bulk importing [SQL Server], format files
- XML format files [SQL Server]
ms.assetid: 69024aad-eeea-4187-8fea-b49bc2359849
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7cc1e8de30fa582898ef8516b9767dec14c4fa81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653873"
---
# <a name="xml-format-files-sql-server"></a><span data-ttu-id="df8b5-102">XML 서식 파일(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="df8b5-102">XML Format Files (SQL Server)</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="df8b5-103">에서는 *테이블에 데이터를 대량으로 가져오는 데 사용할* XML 형식 파일 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 을 작성하기 위한 구문을 정의하는 XML 스키마를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-103">provides an XML schema that defines syntax for writing *XML format files* to use for bulk importing data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="df8b5-104">XML 서식 파일은 XSDL(XML Schema Definition Language)에 정의되어 있는 이 스키마에 충실해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-104">XML format files must adhere to this schema, which is defined in the XML Schema Definition Language (XSDL).</span></span> <span data-ttu-id="df8b5-105">XML 서식 파일은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 도구를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client와 함께 설치한 경우에만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-105">XML format files are only supported when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tools are installed together with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="df8b5-106">XML 서식 파일은 **bcp** 명령, BULK INSERT 문 또는 INSERT ... SELECT \* FROM OPENROWSET(BULK...)과 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-106">You can use an XML format file with a **bcp** command, BULK INSERT statement, or INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement.</span></span> <span data-ttu-id="df8b5-107">**bcp** 명령을 사용하면 테이블에 대해 XML 형식 파일을 자동으로 생성할 수 있습니다. 자세한 내용은 [bcp Utility](../../tools/bcp-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df8b5-107">The **bcp** command allows you to automatically generate an XML format file for a table; for more information, see [bcp Utility](../../tools/bcp-utility.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="df8b5-108">*비 XML 서식 파일* 및 *XML 서식 파일*의 두 가지 서식 파일 유형을 대량으로 내보내고 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-108">Two types of format files are supported for bulk exporting and importing: *non-XML format files* and *XML format files*.</span></span> <span data-ttu-id="df8b5-109">XML 서식 파일은 비 XML 서식 파일 대신 사용할 수 있는 보다 융통성 있고 강력한 파일 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-109">XML format files provide a flexible and powerful alternative to non-XML format files.</span></span> <span data-ttu-id="df8b5-110">비 XML 서식 파일에 대한 자세한 내용은 [비 XML 서식 파일&#40;SQL Server&#41;](xml-format-files-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df8b5-110">For information about non-XML format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  

  
##  <a name="benefits-of-xml-format-files"></a><a name="BenefitsOfXmlFFs"></a> <span data-ttu-id="df8b5-111">XML 형식 파일의 이점</span><span class="sxs-lookup"><span data-stu-id="df8b5-111">Benefits of XML Format Files</span></span>  
  
-   <span data-ttu-id="df8b5-112">XML 형식 파일은 자체 설명적인 파일로, 쉽게 읽고 만들고 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-112">XML format files are self-describing, making them easy to read, create, and extend.</span></span> <span data-ttu-id="df8b5-113">또한 사람이 읽을 수 있는 형태이기 때문에 대량 작업 중에 데이터가 해석되는 방식을 쉽게 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-113">They are human readable, making it easy to understand how data is interpreted during bulk operations.</span></span>  
  
-   <span data-ttu-id="df8b5-114">XML 형식 파일에는 대상 열의 데이터 형식이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-114">XML format files contain the data types of target columns.</span></span>  <span data-ttu-id="df8b5-115">XML 인코딩은 데이터 파일의 데이터 형식과 데이터 요소뿐만 아니라 데이터 요소와 테이블 열 간의 매핑도 명확하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-115">The XML encoding clearly describes the data types and data elements of the data file and also the mapping between data elements and table columns.</span></span>  
  
     <span data-ttu-id="df8b5-116">이 특성은 데이터 파일에 데이터가 기록된 방식과 파일 내의 각 필드와 연결된 데이터 형식을 달리 지정할 수 있게 해줍니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-116">This enables separation between how data is represented in the data file and what data type is associated with each field in the file.</span></span> <span data-ttu-id="df8b5-117">예를 들어 데이터 파일이 데이터의 문자 표시를 포함하면 해당 SQL 열 형식은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-117">For example, if a data file contains a character representation of the data, the corresponding SQL column type is lost.</span></span>  
  
-   <span data-ttu-id="df8b5-118">XML 형식 파일을 사용하면 데이터 파일에서 단일 LOB(Large Object) 데이터 형식이 포함된 필드를 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-118">An XML format file allows for loading of a field that contains a single large object (LOB) data type from a data file.</span></span>  
  
-   <span data-ttu-id="df8b5-119">XML 서식 파일은 이전 버전과의 호환성을 유지하면서 향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-119">An XML format file can be enhanced yet remain compatible with its earlier versions.</span></span> <span data-ttu-id="df8b5-120">또한 XML 인코딩은 명확하기 때문에 지정된 데이터 파일에 대해 다수의 서식 파일을 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-120">Furthermore, the clarity of XML encoding facilitates the creation of multiple format files for a given data file.</span></span> <span data-ttu-id="df8b5-121">데이터 필드 전체나 일부를 서로 다른 테이블이나 뷰에 매핑해야 하는 경우 이 기능이 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-121">This is useful if you have to map all or some of the data fields to columns in different tables or views.</span></span>  
  
-   <span data-ttu-id="df8b5-122">XML 구문은 작업 방향과 무관합니다. 즉, 대량 내보내기와 대량 가져오기의 구문은 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-122">The XML syntax is independent of the direction of the operation; that is, the syntax is the same for bulk export and bulk import.</span></span>  
  
-   <span data-ttu-id="df8b5-123">XML 서식 파일을 사용하여 데이터를 대량으로 테이블이나 파티션이 없는 뷰로 가져오고 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-123">You can use XML format files to bulk import data into tables or non-partitioned views and to bulk export data.</span></span>  
  
-   <span data-ttu-id="df8b5-124">OPENROWSET(BULK...) 함수의 경우 대상 테이블 지정은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-124">For the OPENROWSET(BULK...) function specifying a target table is optional.</span></span> <span data-ttu-id="df8b5-125">이 함수는 XML 형식 파일을 이용하여 데이터 파일에서 데이터를 읽기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-125">This is because the function relies on the XML format file to read data from a data file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="df8b5-126">**bcp** 명령과 BULK INSERT 문의 경우 대상 테이블 열을 사용하여 형식 변환을 수행하므로 대상 테이블이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-126">A target table is necessary with the **bcp** command and the BULK INSERT statement, which uses the target table columns to do the type conversion.</span></span>  
  
##  <a name="structure-of-xml-format-files"></a><a name="StructureOfXmlFFs"></a> <span data-ttu-id="df8b5-127">XML 서식 파일의 구조</span><span class="sxs-lookup"><span data-stu-id="df8b5-127">Structure of XML Format Files</span></span>  
 <span data-ttu-id="df8b5-128">비 XML 서식 파일과 마찬가지로 XML 서식 파일도 데이터 파일의 데이터 필드 형식과 구조를 정의하며 해당 데이터 필드를 단일 대상 테이블의 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-128">Like a non-XML format file, an XML format file defines the format and structure of the data fields in a data file and maps those data fields to columns in a single target table.</span></span>  
  
 <span data-ttu-id="df8b5-129">XML 서식 파일에는 두 개의 주요 구성 요소, \<RECORD>와 \<ROW>가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-129">An XML format file possesses two main components, \<RECORD> and \<ROW>:</span></span>  
  
-   <span data-ttu-id="df8b5-130">\<RECORD>는 데이터 파일에 저장되어 있는 데이터를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-130">\<RECORD> describes the data as it is stored in the data file.</span></span>  
  
     <span data-ttu-id="df8b5-131">각 \<RECORD> 요소는 하나 이상의 \<FIELD> 요소 집합을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-131">Each \<RECORD> element contains a set of one or more \<FIELD> elements.</span></span> <span data-ttu-id="df8b5-132">이러한 요소는 데이터 파일의 필드에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-132">These elements correspond to fields in the data file.</span></span> <span data-ttu-id="df8b5-133">기본 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-133">The basic syntax is as follows:</span></span>  
  
     \<RECORD>  
  
     <span data-ttu-id="df8b5-134">\<FIELD .../> [ ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="df8b5-134">\<FIELD .../> [ ...*n* ]</span></span>  
  
     \</RECORD>  
  
     <span data-ttu-id="df8b5-135">각 \<FIELD> 요소는 특정 데이터 필드의 콘텐츠를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-135">Each \<FIELD> element describes the contents of a specific data field.</span></span> <span data-ttu-id="df8b5-136">필드 하나는 테이블의 열 하나에만 매핑할 수 있지만</span><span class="sxs-lookup"><span data-stu-id="df8b5-136">A field can only be mapped to one column in the table.</span></span> <span data-ttu-id="df8b5-137">모든 필드를 열에 매핑해야 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-137">Not all fields need to be mapped to columns.</span></span>  
  
     <span data-ttu-id="df8b5-138">데이터 파일의 필드는 고정/가변 길이이거나 종료된 문자일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-138">A field in a data file can be either of fixed/variable length or character terminated.</span></span> <span data-ttu-id="df8b5-139">*필드 값* 은 문자(1바이트 표현 사용), 와이드 문자(유니코드 2바이트 표현 사용), 네이티브 데이터베이스 형식 또는 파일 이름으로 표현될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-139">A *field value* can be represented as: a character (using single-byte representation), a wide character (using Unicode two-byte representation), native database format, or a file name.</span></span> <span data-ttu-id="df8b5-140">필드 값이 파일 이름으로 표현되는 경우 파일 이름은 대상 테이블의 BLOB 열 값이 포함된 파일을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-140">If a field value is represented as a file name, the file name points to the file that contains the value of a BLOB column in the target table.</span></span>  
  
-   <span data-ttu-id="df8b5-141">\<ROW>는 파일의 데이터를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블로 가져올 때 데이터 파일의 데이터 행을 구성하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-141">\<ROW> describes how to construct data rows from a data file when the data from the file is imported into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
     <span data-ttu-id="df8b5-142">\<ROW> 요소에는 \<COLUMN> 열 집합이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-142">A \<ROW> element contains a set of \<COLUMN> elements.</span></span> <span data-ttu-id="df8b5-143">이러한 요소는 테이블 열에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-143">These elements correspond to table columns.</span></span> <span data-ttu-id="df8b5-144">기본 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-144">The basic syntax is as follows:</span></span>  
  
     \<ROW>  
  
     <span data-ttu-id="df8b5-145">\<COLUMN .../> [ ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="df8b5-145">\<COLUMN .../> [ ...*n* ]</span></span>  
  
     \</ROW>  
  
     <span data-ttu-id="df8b5-146">각 \<COLUMN> 요소는 데이터 파일의 필드 하나에만 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-146">Each \<COLUMN> element can be mapped to only one field in the data file.</span></span> <span data-ttu-id="df8b5-147">\<ROW> 요소에서 \<COLUMN> 요소의 순서에 따라 대량 작업에서 반환되는 순서가 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-147">The order of the \<COLUMN> elements in the \<ROW> element defines the order in which they are returned by the bulk operation.</span></span> <span data-ttu-id="df8b5-148">XML 서식 파일은 각 \<COLUMN> 요소에 대량 가져오기 작업의 대상 테이블에 있는 열과 관계가 없는 로컬 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-148">The XML format file assigns each \<COLUMN> element a local name that has no relationship to the column in the target table of a bulk import operation.</span></span>  
  
##  <a name="schema-syntax-for-xml-format-files"></a><a name="SchemaSyntax"></a> <span data-ttu-id="df8b5-149">XML 서식 파일의 스키마 구문</span><span class="sxs-lookup"><span data-stu-id="df8b5-149">Schema Syntax for XML Format Files</span></span>  
 <span data-ttu-id="df8b5-150">이 섹션에서는 XML 형식 파일의 XML 스키마 요소 및 특성에 대한 요약을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-150">This section contains a summary of the elements and attributes of the XML schema for XML format files.</span></span> <span data-ttu-id="df8b5-151">서식 파일의 구문은 작업 방향과는 무관합니다. 즉, 대량 내보내기와 대량 가져오기의 구문은 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-151">The syntax of a format file is independent of the direction of the operation; that is, the syntax is the same for bulk export and bulk import.</span></span> <span data-ttu-id="df8b5-152">또한 이 섹션에서는 대량 가져오기에서 \<ROW> 및 \<COLUMN> 요소를 사용하는 방법과 요소의 xsi:type 값을 데이터 집합에 포함시키는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-152">This section also considers how bulk import uses the \<ROW> and \<COLUMN> elements and how to put the xsi:type value of an element into a data set.</span></span>  
  
 <span data-ttu-id="df8b5-153">구문이 실제 XML 형식 파일과 일치하는지 보려면 이 항목 뒷부분에 있는 [예제 XML 형식 파일](#SampleXmlFFs)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df8b5-153">To see how the syntax corresponds to actual XML format files, see [Sample XML Format Files](#SampleXmlFFs), later in this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="df8b5-154">필드와 테이블 열의 번호 또는 순서가 서로 다른 데이터 파일로부터 대량 가져오기를 수행하도록 서식 파일을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-154">You can modify a format file to let you bulk import from a data file in which the number and/or order of the fields differ from the number and/or order of table columns.</span></span> <span data-ttu-id="df8b5-155">자세한 내용은 [데이터를 가져오거나 내보내기 위한 서식 파일&#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df8b5-155">For more information, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
  
  
###  <a name="basic-syntax-of-the-xml-schema"></a><a name="BasicSyntax"></a> <span data-ttu-id="df8b5-156">XML 스키마의 기본 구문</span><span class="sxs-lookup"><span data-stu-id="df8b5-156">Basic Syntax of the XML Schema</span></span>  
 <span data-ttu-id="df8b5-157">이 구문은 요소(\<BCPFORMAT>, \<RECORD>, \<FIELD>, \<ROW>, \<COLUMN>) 및 그 기본 특성만 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-157">This syntax statements show only the elements (\<BCPFORMAT>, \<RECORD>, \<FIELD>, \<ROW>, and \<COLUMN>) and their basic attributes.</span></span>  
  
 \<BCPFORMAT ...>  
  
 \<RECORD>  
  
 <span data-ttu-id="df8b5-158">\<FIELD ID = "*fieldID*" xsi:type = "*fieldType*" [...]</span><span class="sxs-lookup"><span data-stu-id="df8b5-158">\<FIELD ID = "*fieldID*" xsi:type = "*fieldType*" [...]</span></span>  
  
 />  
  
 \</RECORD>  
  
 \<ROW>  
  
 <span data-ttu-id="df8b5-159">\<COLUMN SOURCE = "*fieldID*" NAME = "*columnName*" xsi:type = "*columnType*" [...]</span><span class="sxs-lookup"><span data-stu-id="df8b5-159">\<COLUMN SOURCE = "*fieldID*" NAME = "*columnName*" xsi:type = "*columnType*" [...]</span></span>  
  
 />  
  
 \</ROW>  
  
 \</BCPFORMAT>  
  
> [!NOTE]  
>  <span data-ttu-id="df8b5-160">\<FIELD> 또는 \<COLUMN> 요소의 xsi:type 값에 연결된 추가 특성은 이 항목의 뒷부분에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-160">Additional attributes that are associated with the value of the xsi:type in a \<FIELD> or \<COLUMN> element are described later in this topic.</span></span>  
  

  
####  <a name="schema-elements"></a><a name="SchemaElements"></a> <span data-ttu-id="df8b5-161">스키마 요소</span><span class="sxs-lookup"><span data-stu-id="df8b5-161">Schema Elements</span></span>  
 <span data-ttu-id="df8b5-162">이 섹션에서는 XML 스키마가 XML 서식 파일에 대해 정의하는 각 요소의 목적에 대해 요약합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-162">This section summarizes the purpose of each element that the XML schema defines for XML format files.</span></span> <span data-ttu-id="df8b5-163">특성은 뒷부분의 다른 섹션에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-163">The attributes are described in separate sections later in this topic.</span></span>  
  
 \<BCPFORMAT>  
 <span data-ttu-id="df8b5-164">지정된 데이터 파일의 레코드 구조와 테이블 행의 열과의 일치를 정의하는 서식 파일 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-164">Is the format-file element that defines the record structure of a given data file and its correspondence to the columns of a table row in the table.</span></span>  
  
 \<RECORD .../>  
 <span data-ttu-id="df8b5-165">하나 이상의 \<FIELD> 요소를 포함하는 복잡한 요소를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-165">Defines a complex element containing one or more \<FIELD> elements.</span></span> <span data-ttu-id="df8b5-166">서식 파일에서 필드가 선언되는 순서는 이들 필드가 데이터 파일에 나열되는 순서입니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-166">The order in which the fields are declared in the format file is the order in which those fields appear in the data file.</span></span>  
  
 \<FIELD .../>  
 <span data-ttu-id="df8b5-167">데이터를 포함하는 데이터 파일의 필드를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-167">Defines a field in data file, which contains data.</span></span>  
  
 <span data-ttu-id="df8b5-168">이 요소의 특성은 이 항목의 뒷부분에 나오는 [\<FIELD> 요소의 특성](#AttrOfFieldElement)에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-168">The attributes of this element are discussed in [Attributes of the \<FIELD> Element](#AttrOfFieldElement), later in this topic.</span></span>  
  
 \<ROW .../>  
 <span data-ttu-id="df8b5-169">하나 이상의 \<COLUMN> 요소를 포함하는 복잡한 요소를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-169">Defines a complex element containing one or more \<COLUMN> elements.</span></span> <span data-ttu-id="df8b5-170">\<COLUMN> 요소의 순서는 RECORD 정의에 있는 \<FIELD> 요소의 순서와는 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-170">The order of the \<COLUMN> elements is independent of the order of \<FIELD> elements in a RECORD definition.</span></span> <span data-ttu-id="df8b5-171">반면, 서식 파일에 있는 \<COLUMN> 요소의 순서는 결과 행 집합의 열 순서를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-171">Rather, the order of the \<COLUMN> elements in a format file determines the column order of the resultant rowset.</span></span> <span data-ttu-id="df8b5-172">데이터 필드는 해당 \<COLUMN> 요소가 \<COLUMN> 요소에서 선언되는 순서대로 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-172">Data fields are loaded in the order in which the corresponding \<COLUMN> elements are declared in the \<COLUMN> element.</span></span>  
  
 <span data-ttu-id="df8b5-173">자세한 내용은 뒷부분의 [대량 가져오기에서 \<ROW> 요소를 사용하는 방법](#HowUsesROW)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df8b5-173">For more information, see [How Bulk Import Uses the \<ROW> Element](#HowUsesROW), later in this topic.</span></span>  
  
 \<COLUMN>  
 <span data-ttu-id="df8b5-174">열을 요소(\<COLUMN>)로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-174">Defines a column as an element (\<COLUMN>).</span></span> <span data-ttu-id="df8b5-175">각 \<COLUMN> 요소는 ID가 \<COLUMN> 요소의 SOURCE 특성에서 지정되는 \<FIELD> 요소에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-175">Each \<COLUMN> element corresponds to a \<FIELD> element (whose ID is specified in the SOURCE attribute of the \<COLUMN> element).</span></span>  
  
 <span data-ttu-id="df8b5-176">이 요소의 특성은 이 항목의 뒷부분에 나오는 [\<COLUMN> 요소의 특성](#AttrOfColumnElement)에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-176">The attributes of this element are discussed in [Attributes of the \<COLUMN> Element](#AttrOfColumnElement), later in this topic.</span></span> <span data-ttu-id="df8b5-177">자세한 내용은 뒷부분의 [대량 가져오기에서 \<COLUMN> 요소를 사용하는 방법](#HowUsesColumn)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df8b5-177">Also see, [How Bulk Import Uses the \<COLUMN> Element](#HowUsesColumn), later in this topic.</span></span>  
  
 \</BCPFORMAT>  
 <span data-ttu-id="df8b5-178">서식 파일을 끝내는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-178">Required to end the format file.</span></span>  
  
####  <a name="attributes-of-the-field-element"></a><a name="AttrOfFieldElement"></a> <span data-ttu-id="df8b5-179">\<FIELD> 요소의 특성</span><span class="sxs-lookup"><span data-stu-id="df8b5-179">Attributes of the \<FIELD> Element</span></span>  
 <span data-ttu-id="df8b5-180">이 섹션에서는 \<FIELD> 요소의 특성에 대해 설명합니다. 다음 스키마 구문으로 요약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-180">This section describes the attributes of the \<FIELD> element, which are summarized in the following schema syntax:</span></span>  
  
 <span data-ttu-id="df8b5-181"><FIELD</span><span class="sxs-lookup"><span data-stu-id="df8b5-181"><FIELD</span></span>  
  
 <span data-ttu-id="df8b5-182">ID **= " *`fieldID`* "**</span><span class="sxs-lookup"><span data-stu-id="df8b5-182">ID **="*`fieldID`*"**</span></span>  
  
 <span data-ttu-id="df8b5-183">xsi **:** type **= " *`fieldType`* "**</span><span class="sxs-lookup"><span data-stu-id="df8b5-183">xsi **:** type **="*`fieldType`*"**</span></span>  
  
 <span data-ttu-id="df8b5-184">[ LENGTH **="*`n`*"** ]</span><span class="sxs-lookup"><span data-stu-id="df8b5-184">[ LENGTH **="*`n`*"** ]</span></span>  
  
 <span data-ttu-id="df8b5-185">[PREFIX_LENGTH **= " *`p`* "** ]</span><span class="sxs-lookup"><span data-stu-id="df8b5-185">[ PREFIX_LENGTH **="*`p`*"** ]</span></span>  
  
 <span data-ttu-id="df8b5-186">[MAX_LENGTH **= " *`m`* "** ]</span><span class="sxs-lookup"><span data-stu-id="df8b5-186">[ MAX_LENGTH **="*`m`*"** ]</span></span>  
  
 <span data-ttu-id="df8b5-187">[COLLATION **= " *`collationName`* "** ]</span><span class="sxs-lookup"><span data-stu-id="df8b5-187">[ COLLATION **="*`collationName`*"** ]</span></span>  
  
 <span data-ttu-id="df8b5-188">[종결자 **= " *`terminator`* "** ]</span><span class="sxs-lookup"><span data-stu-id="df8b5-188">[ TERMINATOR **="*`terminator`*"** ]</span></span>  
  
 />  
  
 <span data-ttu-id="df8b5-189">각 \<FIELD> 요소는 다른 요소와는 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-189">Each \<FIELD> element is independent of the others.</span></span> <span data-ttu-id="df8b5-190">필드는 다음 특성에 따라 설명됩니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-190">A field is described in terms of the following attributes:</span></span>  
  
|<span data-ttu-id="df8b5-191">FIELD 특성</span><span class="sxs-lookup"><span data-stu-id="df8b5-191">FIELD Attribute</span></span>|<span data-ttu-id="df8b5-192">Description</span><span class="sxs-lookup"><span data-stu-id="df8b5-192">Description</span></span>|<span data-ttu-id="df8b5-193">선택 /</span><span class="sxs-lookup"><span data-stu-id="df8b5-193">Optional /</span></span><br /><br /> <span data-ttu-id="df8b5-194">필수</span><span class="sxs-lookup"><span data-stu-id="df8b5-194">Required</span></span>|  
|---------------------|-----------------|------------------------------|  
|<span data-ttu-id="df8b5-195">ID **= " *`fieldID`* "**</span><span class="sxs-lookup"><span data-stu-id="df8b5-195">ID **="*`fieldID`*"**</span></span>|<span data-ttu-id="df8b5-196">데이터 파일에서 필드의 논리적 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-196">Specifies the logical name of the field in the data file.</span></span> <span data-ttu-id="df8b5-197">필드의 ID는 필드를 참조하는 데 사용되는 키입니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-197">The ID of a field is the key used to refer to the field.</span></span><br /><br /> <span data-ttu-id="df8b5-198"><FIELD ID **= " *`fieldID`* "**/> <열 SOURCE **= " *`fieldID`* "** 에 매핑됩니다./></span><span class="sxs-lookup"><span data-stu-id="df8b5-198"><FIELD ID **="*`fieldID`*"**/> maps to <COLUMN SOURCE **="*`fieldID`*"**/></span></span>|<span data-ttu-id="df8b5-199">필수</span><span class="sxs-lookup"><span data-stu-id="df8b5-199">Required</span></span>|  
|<span data-ttu-id="df8b5-200">xsi: type **= " *`fieldType`* "**</span><span class="sxs-lookup"><span data-stu-id="df8b5-200">xsi:type **="*`fieldType`*"**</span></span>|<span data-ttu-id="df8b5-201">요소의 인스턴스 유형을 식별하는 XML 구문(특성처럼 사용)입니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-201">This is an XML construct (used like an attribute) that identifies the type of the instance of the element.</span></span> <span data-ttu-id="df8b5-202">*fieldType* 값은 지정한 인스턴스에서 필요한 옵션 특성(아래)을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-202">The value of *fieldType* determines which of the optional attributes (below) you need in a given instance.</span></span>|<span data-ttu-id="df8b5-203">필수(데이터 형식에 따라 다름)</span><span class="sxs-lookup"><span data-stu-id="df8b5-203">Required (depending on the data type)</span></span>|  
|<span data-ttu-id="df8b5-204">LENGTH **= " *`n`* "**</span><span class="sxs-lookup"><span data-stu-id="df8b5-204">LENGTH **="*`n`*"**</span></span>|<span data-ttu-id="df8b5-205">이 특성은 고정 길이 데이터 형식의 인스턴스 길이를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-205">This attribute defines the length for an instance of a fixed-length data type.</span></span><br /><br /> <span data-ttu-id="df8b5-206">*n* 값은 양의 정수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-206">The value of *n* must be a positive integer.</span></span>|<span data-ttu-id="df8b5-207">선택(xsi:type 값에서 필요로 하지 않는 경우)</span><span class="sxs-lookup"><span data-stu-id="df8b5-207">Optional unless required by the xsi:type value</span></span>|  
|<span data-ttu-id="df8b5-208">PREFIX_LENGTH **= " *`p`* "**</span><span class="sxs-lookup"><span data-stu-id="df8b5-208">PREFIX_LENGTH **="*`p`*"**</span></span>|<span data-ttu-id="df8b5-209">이 특성은 이진 데이터 표현의 접두사 길이를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-209">This attribute defines the prefix length for a binary data representation.</span></span> <span data-ttu-id="df8b5-210">PREFIX_LENGTH 값인 *p*는 1, 2, 4 또는 8 중 하나를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-210">The PREFIX_LENGTH value, *p*, must be one of the following: 1, 2, 4, or 8.</span></span>|<span data-ttu-id="df8b5-211">선택(xsi:type 값에서 필요로 하지 않는 경우)</span><span class="sxs-lookup"><span data-stu-id="df8b5-211">Optional unless required by the xsi:type value</span></span>|  
|<span data-ttu-id="df8b5-212">MAX_LENGTH **= " *`m`* "**</span><span class="sxs-lookup"><span data-stu-id="df8b5-212">MAX_LENGTH **="*`m`*"**</span></span>|<span data-ttu-id="df8b5-213">이 특성은 지정된 필드에 저장할 수 있는 최대 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-213">This attribute is the maximum number of bytes that can be stored in a given field.</span></span> <span data-ttu-id="df8b5-214">대상 테이블이 없는 경우 열의 최대 길이를 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-214">Without a target table, the column max-length is not known.</span></span> <span data-ttu-id="df8b5-215">MAX_LENGTH 특성은 출력 문자 열의 최대 길이를 제한하여 열 값에 할당된 스토리지를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-215">The MAX_LENGTH attribute restricts the maximum length of an output character column, limiting the storage allocated for the column value.</span></span> <span data-ttu-id="df8b5-216">특히 SELECT FROM 절에서 OPENROWSET 함수의 BULK 옵션을 사용할 때 편리합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-216">This is especially convenient when using the OPENROWSET function's BULK option in a SELECT FROM clause.</span></span><br /><br /> <span data-ttu-id="df8b5-217">*m* 값은 양의 정수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-217">The value of *m* must be a positive integer.</span></span> <span data-ttu-id="df8b5-218">기본적으로 최대 길이는 **char** 열의 경우 8000자, **nchar** 열의 경우 4000자입니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-218">By default, the maximum length is 8000 characters for a **char** column and 4000 characters for an **nchar** column.</span></span>|<span data-ttu-id="df8b5-219">옵션</span><span class="sxs-lookup"><span data-stu-id="df8b5-219">Optional</span></span>|  
|<span data-ttu-id="df8b5-220">COLLATION **= " *`collationName`* "**</span><span class="sxs-lookup"><span data-stu-id="df8b5-220">COLLATION **="*`collationName`*"**</span></span>|<span data-ttu-id="df8b5-221">COLLATION은 문자 필드에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-221">COLLATION is only allowed for character fields.</span></span> <span data-ttu-id="df8b5-222">SQL 데이터 정렬 이름 목록은 [SQL Server 데이터 정렬 이름&#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df8b5-222">For a list of the SQL collation names, see [SQL Server Collation Name &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql).</span></span>|<span data-ttu-id="df8b5-223">옵션</span><span class="sxs-lookup"><span data-stu-id="df8b5-223">Optional</span></span>|  
|<span data-ttu-id="df8b5-224">종결자 **= " *`terminator`* "**</span><span class="sxs-lookup"><span data-stu-id="df8b5-224">TERMINATOR **= "*`terminator`*"**</span></span>|<span data-ttu-id="df8b5-225">이 특성은 데이터 필드의 종결자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-225">This attribute specifies the terminator of a data field.</span></span> <span data-ttu-id="df8b5-226">종결자는 어떠한 문자도 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-226">The terminator can be any character.</span></span> <span data-ttu-id="df8b5-227">종결자는 데이터의 일부가 아닌 고유 문자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-227">The terminator must be a unique character that is not part of the data.</span></span><br /><br /> <span data-ttu-id="df8b5-228">기본적으로 필드 종결자는 탭 문자(\t로 표시)입니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-228">By default, the field terminator is the tab character (represented as \t).</span></span> <span data-ttu-id="df8b5-229">단락 기호를 표시하려면 \r\n을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="df8b5-229">To represent a paragraph mark, use \r\n.</span></span>|<span data-ttu-id="df8b5-230">이 특성이 필요한 문자 데이터의 xsi:type에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-230">Used only with an xsi:type of character data, which requires this attribute</span></span>|  
  
#####  <a name="xsitype-values-of-the-field-element"></a><a name="XsiTypeValuesOfFIELD"></a><span data-ttu-id="df8b5-231">\<FIELD> 요소의 xsi:type 값</span><span class="sxs-lookup"><span data-stu-id="df8b5-231">Xsi:type values of the \<FIELD> Element</span></span>  
 <span data-ttu-id="df8b5-232">xsi:type 값은 요소 인스턴스의 데이터 형식을 식별하는 XML 구문(특성처럼 사용)입니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-232">The xsi:type value is an XML construct (used like an attribute) that identifies the data type of an instance of an element.</span></span> <span data-ttu-id="df8b5-233">xsi:type 값의 사용 방법은 이 섹션의 뒷부분에 나오는 "데이터 집합에 xsi:type 값 넣기"를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df8b5-233">For information on using the "Putting the xsi:type Value into a Data Set," later in this section.</span></span>  
  
 <span data-ttu-id="df8b5-234">\<FIELD> 요소의 xsi:type 값은 다음 데이터 형식을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-234">The xsi:type value of the \<FIELD> element supports the following data types.</span></span>  
  
|<span data-ttu-id="df8b5-235">\<FIELD> xsi:type 값</span><span class="sxs-lookup"><span data-stu-id="df8b5-235">\<FIELD> xsi:type values</span></span>|<span data-ttu-id="df8b5-236">데이터 형식의</span><span class="sxs-lookup"><span data-stu-id="df8b5-236">Required XML Attribute(s)</span></span><br /><br /> <span data-ttu-id="df8b5-237">선택적 XML 특성</span><span class="sxs-lookup"><span data-stu-id="df8b5-237">for Data Type</span></span>|<span data-ttu-id="df8b5-238">데이터 형식의</span><span class="sxs-lookup"><span data-stu-id="df8b5-238">Optional XML Attribute(s)</span></span><br /><br /> <span data-ttu-id="df8b5-239">선택적 XML 특성</span><span class="sxs-lookup"><span data-stu-id="df8b5-239">for Data Type</span></span>|  
|-------------------------------|---------------------------------------------------|---------------------------------------------------|  
|<span data-ttu-id="df8b5-240">**NativeFixed**</span><span class="sxs-lookup"><span data-stu-id="df8b5-240">**NativeFixed**</span></span>|`LENGTH`|<span data-ttu-id="df8b5-241">없음</span><span class="sxs-lookup"><span data-stu-id="df8b5-241">None.</span></span>|  
|<span data-ttu-id="df8b5-242">**NativePrefix**</span><span class="sxs-lookup"><span data-stu-id="df8b5-242">**NativePrefix**</span></span>|`PREFIX_LENGTH`|<span data-ttu-id="df8b5-243">MAX_LENGTH</span><span class="sxs-lookup"><span data-stu-id="df8b5-243">MAX_LENGTH</span></span>|  
|<span data-ttu-id="df8b5-244">**CharFixed**</span><span class="sxs-lookup"><span data-stu-id="df8b5-244">**CharFixed**</span></span>|`LENGTH`|<span data-ttu-id="df8b5-245">COLLATION</span><span class="sxs-lookup"><span data-stu-id="df8b5-245">COLLATION</span></span>|  
|<span data-ttu-id="df8b5-246">**NCharFixed**</span><span class="sxs-lookup"><span data-stu-id="df8b5-246">**NCharFixed**</span></span>|`LENGTH`|<span data-ttu-id="df8b5-247">COLLATION</span><span class="sxs-lookup"><span data-stu-id="df8b5-247">COLLATION</span></span>|  
|<span data-ttu-id="df8b5-248">**CharPrefix**</span><span class="sxs-lookup"><span data-stu-id="df8b5-248">**CharPrefix**</span></span>|`PREFIX_LENGTH`|<span data-ttu-id="df8b5-249">MAX_LENGTH, COLLATION</span><span class="sxs-lookup"><span data-stu-id="df8b5-249">MAX_LENGTH, COLLATION</span></span>|  
|<span data-ttu-id="df8b5-250">**NCharPrefix**</span><span class="sxs-lookup"><span data-stu-id="df8b5-250">**NCharPrefix**</span></span>|`PREFIX_LENGTH`|<span data-ttu-id="df8b5-251">MAX_LENGTH, COLLATION</span><span class="sxs-lookup"><span data-stu-id="df8b5-251">MAX_LENGTH, COLLATION</span></span>|  
|<span data-ttu-id="df8b5-252">**CharTerm**</span><span class="sxs-lookup"><span data-stu-id="df8b5-252">**CharTerm**</span></span>|`TERMINATOR`|<span data-ttu-id="df8b5-253">MAX_LENGTH, COLLATION</span><span class="sxs-lookup"><span data-stu-id="df8b5-253">MAX_LENGTH, COLLATION</span></span>|  
|<span data-ttu-id="df8b5-254">**NCharTerm**</span><span class="sxs-lookup"><span data-stu-id="df8b5-254">**NCharTerm**</span></span>|`TERMINATOR`|<span data-ttu-id="df8b5-255">MAX_LENGTH, COLLATION</span><span class="sxs-lookup"><span data-stu-id="df8b5-255">MAX_LENGTH, COLLATION</span></span>|  
  
 <span data-ttu-id="df8b5-256">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식에 대한 자세한 내용은 [데이터 형식&#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df8b5-256">For more information about [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
####  <a name="attributes-of-the-column-element"></a><a name="AttrOfColumnElement"></a> <span data-ttu-id="df8b5-257">\<COLUMN> 요소의 특성</span><span class="sxs-lookup"><span data-stu-id="df8b5-257">Attributes of the \<COLUMN> Element</span></span>  
 <span data-ttu-id="df8b5-258">이 섹션에서는 \<COLUMN> 요소의 특성에 대해 설명합니다. 다음 스키마 구문으로 요약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-258">This section describes the attributes of the \<COLUMN> element, which are summarized in the following schema syntax:</span></span>  
  
 <span data-ttu-id="df8b5-259">\<요소의 Xsi:type 값</span><span class="sxs-lookup"><span data-stu-id="df8b5-259">\<COLUMN</span></span>  
  
 <span data-ttu-id="df8b5-260">SOURCE = "*fieldID*"</span><span class="sxs-lookup"><span data-stu-id="df8b5-260">SOURCE = "*fieldID*"</span></span>  
  
 <span data-ttu-id="df8b5-261">NAME = "*columnName*"</span><span class="sxs-lookup"><span data-stu-id="df8b5-261">NAME = "*columnName*"</span></span>  
  
 <span data-ttu-id="df8b5-262">xsi:type = "*columnType*"</span><span class="sxs-lookup"><span data-stu-id="df8b5-262">xsi:type = "*columnType*"</span></span>  
  
 <span data-ttu-id="df8b5-263">[ LENGTH = "*n*" ]</span><span class="sxs-lookup"><span data-stu-id="df8b5-263">[ LENGTH = "*n*" ]</span></span>  
  
 <span data-ttu-id="df8b5-264">[ PRECISION = "*n*" ]</span><span class="sxs-lookup"><span data-stu-id="df8b5-264">[ PRECISION = "*n*" ]</span></span>  
  
 <span data-ttu-id="df8b5-265">[ SCALE = "*value*" ]</span><span class="sxs-lookup"><span data-stu-id="df8b5-265">[ SCALE = "*value*" ]</span></span>  
  
 <span data-ttu-id="df8b5-266">[ NULLABLE = { "YES"</span><span class="sxs-lookup"><span data-stu-id="df8b5-266">[ NULLABLE = { "YES"</span></span>  
  
 <span data-ttu-id="df8b5-267">"NO" } ]</span><span class="sxs-lookup"><span data-stu-id="df8b5-267">"NO" } ]</span></span>  
  
 />  
  
 <span data-ttu-id="df8b5-268">필드는 다음 특성을 사용하여 대상 테이블의 열에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-268">A field is mapped to a column in the target table using the following attributes:</span></span>  
  
|<span data-ttu-id="df8b5-269">COLUMN 특성</span><span class="sxs-lookup"><span data-stu-id="df8b5-269">COLUMN Attribute</span></span>|<span data-ttu-id="df8b5-270">Description</span><span class="sxs-lookup"><span data-stu-id="df8b5-270">Description</span></span>|<span data-ttu-id="df8b5-271">선택 /</span><span class="sxs-lookup"><span data-stu-id="df8b5-271">Optional /</span></span><br /><br /> <span data-ttu-id="df8b5-272">필수</span><span class="sxs-lookup"><span data-stu-id="df8b5-272">Required</span></span>|  
|----------------------|-----------------|------------------------------|  
|<span data-ttu-id="df8b5-273">SOURCE **= " *`fieldID`* "**</span><span class="sxs-lookup"><span data-stu-id="df8b5-273">SOURCE **="*`fieldID`*"**</span></span>|<span data-ttu-id="df8b5-274">열에 매핑되는 필드의 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-274">Specifies the ID of the field being mapped to the column.</span></span><br /><br /> <span data-ttu-id="df8b5-275"><열 원본 **= " *`fieldID`* "**/> <필드 ID **= " *`fieldID`* "** 에 매핑됩니다./></span><span class="sxs-lookup"><span data-stu-id="df8b5-275"><COLUMN SOURCE **="*`fieldID`*"**/> maps to <FIELD ID **="*`fieldID`*"**/></span></span>|<span data-ttu-id="df8b5-276">필수</span><span class="sxs-lookup"><span data-stu-id="df8b5-276">Required</span></span>|  
|<span data-ttu-id="df8b5-277">NAME = "*columnName*"</span><span class="sxs-lookup"><span data-stu-id="df8b5-277">NAME = "*columnName*"</span></span>|<span data-ttu-id="df8b5-278">서식 파일에 의해 표현된 행 집합의 열 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-278">Specifies the name of the column in the row set represented by the format file.</span></span> <span data-ttu-id="df8b5-279">이 열 이름은 결과 집합에서 열을 식별하는 데 사용되며 대상 테이블에서 사용되는 열 이름과 일치할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-279">This column name is used to identify the column in the result set, and it need not correspond to the column name used in the target table.</span></span>|<span data-ttu-id="df8b5-280">필수</span><span class="sxs-lookup"><span data-stu-id="df8b5-280">Required</span></span>|  
|<span data-ttu-id="df8b5-281">xsi **:** type **= " *`ColumnType`* "**</span><span class="sxs-lookup"><span data-stu-id="df8b5-281">xsi **:** type **="*`ColumnType`*"**</span></span>|<span data-ttu-id="df8b5-282">요소의 인스턴스 데이터 형식을 식별하는 XML 구문(특성처럼 사용)입니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-282">This is an XML construct (used like an attribute) that identifies the data type of the instance of the element.</span></span> <span data-ttu-id="df8b5-283">*ColumnType* 값은 지정한 인스턴스에서 필요한 옵션 특성(아래)을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-283">The value of *ColumnType* determines which of the optional attributes (below) you need in a given instance.</span></span><br /><br /> <span data-ttu-id="df8b5-284">참고: *ColumnType* 의 가능한 값 및 관련 특성은 다음 표에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-284">Note: The possible values of *ColumnType* and their associated attributes are listed in the next table.</span></span>|<span data-ttu-id="df8b5-285">선택 사항</span><span class="sxs-lookup"><span data-stu-id="df8b5-285">Optional</span></span>|  
|<span data-ttu-id="df8b5-286">LENGTH **= " *`n`* "**</span><span class="sxs-lookup"><span data-stu-id="df8b5-286">LENGTH **="*`n`*"**</span></span>|<span data-ttu-id="df8b5-287">고정 길이 데이터 형식의 인스턴스 길이를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-287">Defines the length for an instance of a fixed-length data type.</span></span> <span data-ttu-id="df8b5-288">LENGTH는 xsi:type이 문자열 데이터 형식인 경우에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-288">LENGTH is used only when the xsi:type is a string data type.</span></span><br /><br /> <span data-ttu-id="df8b5-289">*n* 값은 양의 정수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-289">The value of *n* must be a positive integer.</span></span>|<span data-ttu-id="df8b5-290">선택(xsi:type이 문자열 데이터 형식인 경우에만 사용 가능)</span><span class="sxs-lookup"><span data-stu-id="df8b5-290">Optional (available only if the xsi:type is a string data type)</span></span>|  
|<span data-ttu-id="df8b5-291">PRECISION **="*`n`*"**</span><span class="sxs-lookup"><span data-stu-id="df8b5-291">PRECISION **="*`n`*"**</span></span>|<span data-ttu-id="df8b5-292">숫자의 전체 자릿수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-292">Indicates the number of digits in a number.</span></span> <span data-ttu-id="df8b5-293">예를 들어 123.45의 전체 자릿수는 5입니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-293">For example, the number 123.45 has a precision of 5.</span></span><br /><br /> <span data-ttu-id="df8b5-294">값은 양의 정수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-294">The value must be a positive integer.</span></span>|<span data-ttu-id="df8b5-295">선택(xsi:type이 가변 숫자 데이터 형식인 경우에만 사용 가능)</span><span class="sxs-lookup"><span data-stu-id="df8b5-295">Optional (available only if the xsi:type is a variable-number data type)</span></span>|  
|<span data-ttu-id="df8b5-296">SCALE **= " *`int`* "**</span><span class="sxs-lookup"><span data-stu-id="df8b5-296">SCALE **="*`int`*"**</span></span>|<span data-ttu-id="df8b5-297">숫자에서 소수점 이하 자릿수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-297">Indicates the number of digits to the right of the decimal point in a number.</span></span> <span data-ttu-id="df8b5-298">예를 들어 123.45의 소수 자릿수는 2입니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-298">For example, the number 123.45 has a scale of 2.</span></span><br /><br /> <span data-ttu-id="df8b5-299">값은 정수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-299">The value must be an integer.</span></span>|<span data-ttu-id="df8b5-300">선택(xsi:type이 가변 숫자 데이터 형식인 경우에만 사용 가능)</span><span class="sxs-lookup"><span data-stu-id="df8b5-300">Optional (available only if the xsi:type is a variable-number data type)</span></span>|  
|<span data-ttu-id="df8b5-301">NULLABLE **=** { **"** YES **"**</span><span class="sxs-lookup"><span data-stu-id="df8b5-301">NULLABLE **=** { **"** YES **"**</span></span><br /><br /> <span data-ttu-id="df8b5-302">**"** NO **"** }</span><span class="sxs-lookup"><span data-stu-id="df8b5-302">**"** NO **"** }</span></span>|<span data-ttu-id="df8b5-303">열이 NULL 값을 허용하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-303">Indicates whether a column can assume NULL values.</span></span> <span data-ttu-id="df8b5-304">이 특성은 FIELDS와는 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-304">This attribute is completely independent of FIELDS.</span></span> <span data-ttu-id="df8b5-305">그러나 열이 NULLABLE이 아닌 경우 필드에서 NULL을 지정하면(아무 값도 지정하지 않음) 런타임 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-305">However, if a column is not NULLABLE and field specifies NULL (by not specifying any value), a run-time error results.</span></span><br /><br /> <span data-ttu-id="df8b5-306">NULLABLE 특성은 일반 SELECT FROM OPENROWSET(BULK...) 문의 경우에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-306">The NULLABLE attribute is used only if you do a plain SELECT FROM OPENROWSET(BULK...) statement.</span></span>|<span data-ttu-id="df8b5-307">선택 사항(모든 데이터 형식에 사용 가능)</span><span class="sxs-lookup"><span data-stu-id="df8b5-307">Optional (available for any data type)</span></span>|  
  
#####  <a name="xsitype-values-of-the-column-element"></a><a name="XsiTypeValuesOfCOLUMN"></a> <span data-ttu-id="df8b5-308">\<COLUMN> 요소의 xsi:type 값</span><span class="sxs-lookup"><span data-stu-id="df8b5-308">Xsi:type values of the \<COLUMN> Element</span></span>  
 <span data-ttu-id="df8b5-309">xsi:type 값은 요소 인스턴스의 데이터 형식을 식별하는 XML 구문(특성처럼 사용)입니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-309">The xsi:type value is an XML construct (used like an attribute) that identifies the data type of an instance of an element.</span></span> <span data-ttu-id="df8b5-310">xsi:type 값의 사용 방법은 이 섹션의 뒷부분에 나오는 "데이터 집합에 xsi:type 값 넣기"를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df8b5-310">For information on using the "Putting the xsi:type Value into a Data Set," later in this section.</span></span>  
  
 <span data-ttu-id="df8b5-311">\<COLUMN> 요소는 다음과 같이 원시 SQL 데이터 형식을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-311">The \<COLUMN> element supports native SQL data types, as follows:</span></span>  
  
|<span data-ttu-id="df8b5-312">형식 범주</span><span class="sxs-lookup"><span data-stu-id="df8b5-312">Type Category</span></span>|<span data-ttu-id="df8b5-313">\<COLUMN> 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="df8b5-313">\<COLUMN> Data Types</span></span>|<span data-ttu-id="df8b5-314">데이터 형식의</span><span class="sxs-lookup"><span data-stu-id="df8b5-314">Required XML Attribute(s)</span></span><br /><br /> <span data-ttu-id="df8b5-315">선택적 XML 특성</span><span class="sxs-lookup"><span data-stu-id="df8b5-315">for Data Type</span></span>|<span data-ttu-id="df8b5-316">데이터 형식의</span><span class="sxs-lookup"><span data-stu-id="df8b5-316">Optional XML Attribute(s)</span></span><br /><br /> <span data-ttu-id="df8b5-317">선택적 XML 특성</span><span class="sxs-lookup"><span data-stu-id="df8b5-317">for Data Type</span></span>|  
|-------------------|---------------------------|---------------------------------------------------|---------------------------------------------------|  
|<span data-ttu-id="df8b5-318">수정됨</span><span class="sxs-lookup"><span data-stu-id="df8b5-318">Fixed</span></span>|<span data-ttu-id="df8b5-319">`SQLBIT`, `SQLTINYINT`, `SQLSMALLINT`, `SQLINT`, `SQLBIGINT`, `SQLFLT4`, `SQLFLT8`, `SQLDATETIME`, `SQLDATETIM4`, `SQLDATETIM8`, `SQLMONEY`, `SQLMONEY4`, `SQLVARIANT` 및 `SQLUNIQUEID`</span><span class="sxs-lookup"><span data-stu-id="df8b5-319">`SQLBIT`, `SQLTINYINT`, `SQLSMALLINT`, `SQLINT`, `SQLBIGINT`, `SQLFLT4`, `SQLFLT8`, `SQLDATETIME`, `SQLDATETIM4`, `SQLDATETIM8`, `SQLMONEY`, `SQLMONEY4`, `SQLVARIANT`, and `SQLUNIQUEID`</span></span>|<span data-ttu-id="df8b5-320">없음</span><span class="sxs-lookup"><span data-stu-id="df8b5-320">None.</span></span>|<span data-ttu-id="df8b5-321">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="df8b5-321">NULLABLE</span></span>|  
|<span data-ttu-id="df8b5-322">가변 숫자</span><span class="sxs-lookup"><span data-stu-id="df8b5-322">Variable Number</span></span>|<span data-ttu-id="df8b5-323">`SQLDECIMAL` 및 `SQLNUMERIC`</span><span class="sxs-lookup"><span data-stu-id="df8b5-323">`SQLDECIMAL` and `SQLNUMERIC`</span></span>|<span data-ttu-id="df8b5-324">없음</span><span class="sxs-lookup"><span data-stu-id="df8b5-324">None.</span></span>|<span data-ttu-id="df8b5-325">NULLABLE, PRECISION, SCALE</span><span class="sxs-lookup"><span data-stu-id="df8b5-325">NULLABLE, PRECISION, SCALE</span></span>|  
|<span data-ttu-id="df8b5-326">LOB</span><span class="sxs-lookup"><span data-stu-id="df8b5-326">LOB</span></span>|<span data-ttu-id="df8b5-327">`SQLIMAGE`, `CharLOB`, `SQLTEXT` 및 `SQLUDT`</span><span class="sxs-lookup"><span data-stu-id="df8b5-327">`SQLIMAGE`, `CharLOB`, `SQLTEXT`, and `SQLUDT`</span></span>|<span data-ttu-id="df8b5-328">없음</span><span class="sxs-lookup"><span data-stu-id="df8b5-328">None.</span></span>|<span data-ttu-id="df8b5-329">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="df8b5-329">NULLABLE</span></span>|  
|<span data-ttu-id="df8b5-330">문자 LOB</span><span class="sxs-lookup"><span data-stu-id="df8b5-330">Character LOB</span></span>|`SQLNTEXT`|<span data-ttu-id="df8b5-331">없음</span><span class="sxs-lookup"><span data-stu-id="df8b5-331">None.</span></span>|<span data-ttu-id="df8b5-332">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="df8b5-332">NULLABLE</span></span>|  
|<span data-ttu-id="df8b5-333">이진 문자열</span><span class="sxs-lookup"><span data-stu-id="df8b5-333">Binary string</span></span>|<span data-ttu-id="df8b5-334">`SQLBINARY` 및 `SQLVARYBIN`</span><span class="sxs-lookup"><span data-stu-id="df8b5-334">`SQLBINARY` and `SQLVARYBIN`</span></span>|<span data-ttu-id="df8b5-335">없음</span><span class="sxs-lookup"><span data-stu-id="df8b5-335">None.</span></span>|<span data-ttu-id="df8b5-336">NULLABLE, LENGTH</span><span class="sxs-lookup"><span data-stu-id="df8b5-336">NULLABLE, LENGTH</span></span>|  
|<span data-ttu-id="df8b5-337">문자열</span><span class="sxs-lookup"><span data-stu-id="df8b5-337">Character string</span></span>|<span data-ttu-id="df8b5-338">`SQLCHAR`, `SQLVARYCHAR`, `SQLNCHAR` 및 `SQLNVARCHAR`</span><span class="sxs-lookup"><span data-stu-id="df8b5-338">`SQLCHAR`, `SQLVARYCHAR`, `SQLNCHAR`, and `SQLNVARCHAR`</span></span>|<span data-ttu-id="df8b5-339">없음</span><span class="sxs-lookup"><span data-stu-id="df8b5-339">None.</span></span>|<span data-ttu-id="df8b5-340">NULLABLE, LENGTH</span><span class="sxs-lookup"><span data-stu-id="df8b5-340">NULLABLE, LENGTH</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="df8b5-341">SQLXML 데이터를 대량으로 내보내거나 가져오려면 서식 파일에서 다음 데이터 형식 중 하나를 사용합니다. SQLCHAR 또는 SQLVARYCHAR(데이터 정렬에 의해 포함된 코드 페이지나 클라이언트 코드 페이지로 데이터가 전송됨), SQLNCHAR 또는 SQLNVARCHAR(데이터가 유니코드로 전송됨), SQLBINARY 또는 SQLVARYBIN(데이터가 변환되지 않고 전송됨) 데이터 형식 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-341">To bulk export or import SQLXML data, use one of the following data types in your format file: SQLCHAR or SQLVARYCHAR (the data is sent in the client code page or in the code page implied by the collation), SQLNCHAR or SQLNVARCHAR (the data is sent as Unicode), or SQLBINARY or SQLVARYBIN (the data is sent without any conversion).</span></span>  
  
 <span data-ttu-id="df8b5-342">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식에 대한 자세한 내용은 [데이터 형식&#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df8b5-342">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
###  <a name="how-bulk-import-uses-the-row-element"></a><a name="HowUsesROW"></a> <span data-ttu-id="df8b5-343">대량 가져오기에서 \<ROW> 요소를 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="df8b5-343">How Bulk Import Uses the \<ROW> Element</span></span>  
 <span data-ttu-id="df8b5-344">일부 컨텍스트에서는 \<ROW> 요소가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-344">The \<ROW> element is ignored in some contexts.</span></span> <span data-ttu-id="df8b5-345">\<ROW> 요소가 대량 가져오기 작업에 영향을 주는지 여부는 작업 수행 방법에 따라 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-345">Whether the \<ROW> element affects a bulk-import operation depends on how the operation is performed:</span></span>  
  
-   <span data-ttu-id="df8b5-346">**bcp** 명령</span><span class="sxs-lookup"><span data-stu-id="df8b5-346">the **bcp** command</span></span>  
  
     <span data-ttu-id="df8b5-347">데이터가 대상 테이블에 로드되면 **bcp**는 \<ROW> 구성 요소를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-347">When data is loaded into a target table, **bcp** ignores the \<ROW> component.</span></span> <span data-ttu-id="df8b5-348">대신 **bcp** 는 대상 테이블의 열 유형을 기반으로 하는 데이터를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-348">Instead, **bcp** loads the data based on the column types of the target table.</span></span>  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="df8b5-349">문(BULK INSERT 및 OPENROWSET의 대량 행 집합 공급자)</span><span class="sxs-lookup"><span data-stu-id="df8b5-349">statements (BULK INSERT and OPENROWSET's Bulk rowset provider)</span></span>  
  
     <span data-ttu-id="df8b5-350">대량의 데이터를 테이블로 가져오는 경우 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문은 \<ROW> 구성 요소를 사용하여 입력 행 집합을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-350">When bulk importing data into a table, [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements use the \<ROW> component to generate the input rowset.</span></span> <span data-ttu-id="df8b5-351">또한 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문은 \<ROW>에서 지정된 열 유형과 대상 테이블에 있는 해당 열에 따라 적절한 형식 변환을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-351">Also, [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements perform appropriate type conversions based on the column types specified under \<ROW> and the corresponding column in the target table.</span></span> <span data-ttu-id="df8b5-352">서식 파일에서 지정된 열 유형과 대상 테이블에서 지정된 열 유형이 일치하지 않는 경우 추가 형식 변환이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-352">If a mismatch exists between column types as specified in the format file and in the target table, an extra type conversion occurs.</span></span> <span data-ttu-id="df8b5-353">**bcp**와 비교할 때 이 추가 형식 변환으로 인해 BULK INSERT 또는 OPENROWSET의 대량 행 집합 공급자 동작에서 다소 불일치(전체 자릿수 손실)가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-353">This extra type conversion may lead to some discrepancy (that is, a loss of precision) in behavior in BULK INSERT or OPENROWSET's Bulk rowset provider as compared to **bcp**.</span></span>  
  
     <span data-ttu-id="df8b5-354">\<ROW> 요소의 정보를 사용하면 추가 정보 없이 행을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-354">The information in the \<ROW> element allows a row to be constructed without requiring any additional information.</span></span> <span data-ttu-id="df8b5-355">따라서 SELECT 문(SELECT \* FROM OPENROWSET(BULK *datafile* FORMATFILE=*xmlformatfile*)을 사용하여 행 집합을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-355">For this reason, you can generate a rowset using a SELECT statement (SELECT \* FROM OPENROWSET(BULK *datafile* FORMATFILE=*xmlformatfile*).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="df8b5-356">OPENROWSET BULK 절에는 서식 파일이 필요합니다. XML 서식 파일을 사용해야만 필드 데이터 형식에서 열 데이터 형식으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-356">The OPENROWSET BULK clause requires a format file (note that converting from the data type of the field to the data type of a column is available only with an XML format file).</span></span>  
  
###  <a name="how-bulk-import-uses-the-column-element"></a><a name="HowUsesColumn"></a> <span data-ttu-id="df8b5-357">대량 가져오기에서 \<COLUMN> 요소를 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="df8b5-357">How Bulk Import Uses the \<COLUMN> Element</span></span>  
 <span data-ttu-id="df8b5-358">대량의 데이터를 테이블로 가져오는 경우 서식 파일의 \<COLUMN> 요소는 다음을 지정하여 데이터 파일 필드를 테이블 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-358">For bulk importing data into a table, the \<COLUMN> elements in a format file map a data-file field to table columns by specifying:</span></span>  
  
-   <span data-ttu-id="df8b5-359">데이터 파일의 행 내의 각 필드 위치</span><span class="sxs-lookup"><span data-stu-id="df8b5-359">The position of each field within a row in the data file.</span></span>  
  
-   <span data-ttu-id="df8b5-360">필드 데이터 형식을 원하는 열 데이터 형식으로 변환하는 데 사용되는 열 유형</span><span class="sxs-lookup"><span data-stu-id="df8b5-360">The column type, which is used to convert the field data type to the desired column data type.</span></span>  
  
 <span data-ttu-id="df8b5-361">열이 필드에 매핑되지 않으면 해당 필드는 생성된 행에 복사되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-361">If no column is mapped to a field, the field is not copied into the generated row(s).</span></span> <span data-ttu-id="df8b5-362">이 동작을 통해 데이터 파일은 다른 열(다른 테이블)을 포함하는 행을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-362">This behavior allows a data file to generate rows with different columns (in different tables).</span></span>  
  
 <span data-ttu-id="df8b5-363">마찬가지로 테이블에서 데이터를 대량으로 내보내는 경우 서식 파일의 각 \<COLUMN>은 입력 테이블 행의 열을 출력 데이터 파일의 해당 필드에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-363">Similarly, for bulk exporting data from a table, each \<COLUMN> in the format file maps the column from the input table row to its corresponding field in the output data file.</span></span>  
  
###  <a name="putting-the-xsitype-value-into-a-data-set"></a><a name="PutXsiTypeValueIntoDataSet"></a> <span data-ttu-id="df8b5-364">데이터 집합에 xsi:type 값 넣기</span><span class="sxs-lookup"><span data-stu-id="df8b5-364">Putting the xsi:type Value into a Data Set</span></span>  
 <span data-ttu-id="df8b5-365">XSD(XML 스키마 정의) 언어를 통해 XML 문서의 유효성이 검사된 경우 xsi:type 값을 데이터 집합에 넣을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-365">When an XML document is validated through the XML Schema Definition (XSD) language, the xsi:type value is not put into the data set.</span></span> <span data-ttu-id="df8b5-366">그러나 다음 코드 조각의 설명과 같이 XML 서식 파일을 XML 문서(예: `myDoc`)에 로드하여 xsi:type 정보를 데이터 집합에 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-366">However, you can put the xsi:type information into the data set by loading the XML format file into an XML document (for example, `myDoc`), as illustrated in the following code snippet:</span></span>  
  
```  
...;  
myDoc.LoadXml(xmlFormat);  
XmlNodeList ColumnList = myDoc.GetElementsByTagName("COLUMN");  
for(int i=0;i<ColumnList.Count;i++)  
{  
   Console.Write("COLUMN: xsi:type=" +ColumnList[i].Attributes["type",  
      "http://www.w3.org/2001/XMLSchema-instance"].Value+"\n");  
}  
```  
  
##  <a name="sample-xml-format-files"></a><a name="SampleXmlFFs"></a> <span data-ttu-id="df8b5-367">예제 XML 형식 파일</span><span class="sxs-lookup"><span data-stu-id="df8b5-367">Sample XML Format Files</span></span>  
 <span data-ttu-id="df8b5-368">이 섹션에는 [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] 의 예를 포함하여 다양한 경우의 XML 형식 파일 사용에 대한 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-368">This section contains information on using XML format files in a variety of cases, including an [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] example.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="df8b5-369">다음 예의 데이터 파일에서 `<tab>` 은 데이터 파일의 탭 문자를 나타내며 `<return>` 은 캐리지 리턴을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-369">In the data files shown in the following examples, `<tab>` indicates a tab character in a data file, and `<return>` indicates a carriage return.</span></span>  
  

  
> [!NOTE]  
>  <span data-ttu-id="df8b5-370">서식 파일을 만드는 방법은 [서식 파일 만들기&#40;SQL Server&#41;](create-a-format-file-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df8b5-370">For information about how to create format files, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
###  <a name="a-ordering-character-data-fields-the-same-as-table-columns"></a><a name="OrderCharFieldsSameAsCols"></a> <span data-ttu-id="df8b5-371">1.</span><span class="sxs-lookup"><span data-stu-id="df8b5-371">A.</span></span> <span data-ttu-id="df8b5-372">테이블 열과 동일하게 문자 데이터 필드 정렬</span><span class="sxs-lookup"><span data-stu-id="df8b5-372">Ordering character-data fields the same as table columns</span></span>  
 <span data-ttu-id="df8b5-373">다음 예에서는 3개의 문자 데이터 필드가 포함된 데이터 파일을 설명하는 XML 서식 파일을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-373">The following example shows an XML format file that describes a data file containing three fields of character data.</span></span> <span data-ttu-id="df8b5-374">서식 파일은 데이터 파일을 3개의 열이 포함된 테이블로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-374">The format file maps the data file to a table that contains three columns.</span></span> <span data-ttu-id="df8b5-375">데이터 필드는 테이블 열과 일 대 일로 대응합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-375">The data fields correspond one-to-one with the columns of the table.</span></span>  
  
 <span data-ttu-id="df8b5-376">**테이블(행):** Person(Age int, FirstName varchar(20), LastName varchar(30))</span><span class="sxs-lookup"><span data-stu-id="df8b5-376">**Table (row):** Person (Age int, FirstName varchar(20), LastName varchar(30))</span></span>  
  
 <span data-ttu-id="df8b5-377">**데이터 파일(레코드):** Age\<tab>Firstname\<tab>Lastname\<return></span><span class="sxs-lookup"><span data-stu-id="df8b5-377">**Data file (record):** Age\<tab>Firstname\<tab>Lastname\<return></span></span>  
  
 <span data-ttu-id="df8b5-378">다음 XML 서식 파일은 데이터 파일의 데이터를 테이블로 읽어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-378">The following XML format file reads from the data file to the table.</span></span>  
  
 <span data-ttu-id="df8b5-379">서식 파일은 `<RECORD>` 요소에서 3개의 필드에 있는 데이터 값을 문자 데이터로 표현합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-379">In the `<RECORD>` element, the format file represents the data values in all three fields as character data.</span></span> <span data-ttu-id="df8b5-380">각 필드에서 `TERMINATOR` 특성은 데이터 값 다음에 오는 종결자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-380">For each field, the `TERMINATOR` attribute indicates the terminator that follows the data value.</span></span>  
  
 <span data-ttu-id="df8b5-381">데이터 필드는 테이블 열과 일 대 일로 대응합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-381">The data fields correspond one-to-one with the columns of the table.</span></span> <span data-ttu-id="df8b5-382">서식 파일은 `<ROW>` 요소의 `Age` 열을 첫 번째 필드에, `FirstName` 열을 두 번째 필드에, `LastName` 열을 세 번째 필드에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-382">In the `<ROW>` element, the format file maps the column `Age` to the first field, the column `FirstName` to the second field, and the column `LastName` to the third field.</span></span>  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT   
xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <RECORD>  
    <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="12"/>   
    <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="20" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
    <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n"   
      MAX_LENGTH="30"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  </RECORD>  
  <ROW>  
    <COLUMN SOURCE="1" NAME="age" xsi:type="SQLINT"/>  
    <COLUMN SOURCE="2" NAME="firstname" xsi:type="SQLVARYCHAR"/>  
    <COLUMN SOURCE="3" NAME="lastname" xsi:type="SQLVARYCHAR"/>  
  </ROW>  
</BCPFORMAT>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="df8b5-383">해당하는 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 예제는 [서식 파일 만들기&#40;SQL Server&#41;](create-a-format-file-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df8b5-383">For an equivalent [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] example, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
###  <a name="b-ordering-data-fields-and-table-columns-differently"></a><a name="OrderFieldsAndColsDifferently"></a> <span data-ttu-id="df8b5-384">2.</span><span class="sxs-lookup"><span data-stu-id="df8b5-384">B.</span></span> <span data-ttu-id="df8b5-385">데이터 필드와 테이블 열을 서로 다르게 정렬</span><span class="sxs-lookup"><span data-stu-id="df8b5-385">Ordering data fields and table columns differently</span></span>  
 <span data-ttu-id="df8b5-386">다음 예에서는 3개의 문자 데이터 필드가 포함된 데이터 파일을 설명하는 XML 서식 파일을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-386">The following example shows an XML format file that describes a data file containing three fields of character data.</span></span> <span data-ttu-id="df8b5-387">서식 파일은 데이터 파일을 데이터 파일의 필드와 다르게 정렬된 3개의 열을 포함하는 테이블로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-387">The format file maps the data file to a table that contains three columns that are ordered differently from the fields of the data file.</span></span>  
  
 <span data-ttu-id="df8b5-388">**테이블(행):** Person(Age int, FirstName varchar(20), LastName varchar(30))</span><span class="sxs-lookup"><span data-stu-id="df8b5-388">**Table (row):** Person (Age int, FirstName varchar(20), LastName varchar(30))</span></span>  
  
 <span data-ttu-id="df8b5-389">**데이터 파일**(레코드): Age\<tab>Lastname\<tab>Firstname\<return></span><span class="sxs-lookup"><span data-stu-id="df8b5-389">**Data file** (record): Age\<tab>Lastname\<tab>Firstname\<return></span></span>  
  
 <span data-ttu-id="df8b5-390">서식 파일은 `<RECORD>` 요소에서 3개의 필드에 있는 데이터 값을 문자 데이터로 표현합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-390">In the `<RECORD>` element, the format file represents the data values in all three fields as character data.</span></span>  
  
 <span data-ttu-id="df8b5-391">서식 파일은 `<ROW>` 요소의 `Age` 열을 첫 번째 필드에, `FirstName` 열을 세 번째 필드에, `LastName` 열을 두 번째 필드에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-391">In the `<ROW>` element, the format file maps the column `Age` to the first field, the column `FirstName` to the third field, and the column `LastName` to the second field.</span></span>  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT   
xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <RECORD>  
    <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="12"/>  
    <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\t" MAX_LENGTH="20"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
    <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n"   
      MAX_LENGTH="30" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  </RECORD>  
  <ROW>  
    <COLUMN SOURCE="1" NAME="age" xsi:type="SQLINT"/>  
    <COLUMN SOURCE="3" NAME="firstname" xsi:type="SQLVARYCHAR"/>  
    <COLUMN SOURCE="2" NAME="lastname" xsi:type="SQLVARYCHAR"/>  
  </ROW>  
</BCPFORMAT>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="df8b5-392">해당하는 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 예제는 [서식 파일을 사용하여 테이블 열을 데이터 파일 필드에 매핑&#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df8b5-392">For an equivalent [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] example, see [Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md).</span></span>  
  
### <a name="c-omitting-a-data-field"></a><span data-ttu-id="df8b5-393">C.</span><span class="sxs-lookup"><span data-stu-id="df8b5-393">C.</span></span> <span data-ttu-id="df8b5-394">데이터 필드 생략</span><span class="sxs-lookup"><span data-stu-id="df8b5-394">Omitting a data field</span></span>  
 <span data-ttu-id="df8b5-395">다음 예에서는 4개의 문자 데이터 필드가 포함된 데이터 파일을 설명하는 XML 서식 파일을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-395">The following example shows an XML format file that describes a data file containing four fields of character data.</span></span> <span data-ttu-id="df8b5-396">서식 파일은 데이터 파일을 3개의 열이 포함된 테이블로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-396">The format file maps the data file to a table that contains three columns.</span></span> <span data-ttu-id="df8b5-397">두 번째 데이터 필드는 대응되는 테이블 열이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-397">The second data field does not correspond to any table column.</span></span>  
  
 <span data-ttu-id="df8b5-398">**테이블(행):** Person(Age int, FirstName Varchar(20), LastName Varchar(30))</span><span class="sxs-lookup"><span data-stu-id="df8b5-398">**Table (row):** Person (Age int, FirstName Varchar(20), LastName Varchar(30))</span></span>  
  
 <span data-ttu-id="df8b5-399">**데이터 파일(레코드):** Age\<tab>employeeID\<tab>Firstname\<tab>Lastname\<return></span><span class="sxs-lookup"><span data-stu-id="df8b5-399">**Data file (record):** Age\<tab>employeeID\<tab>Firstname\<tab>Lastname\<return></span></span>  
  
 <span data-ttu-id="df8b5-400">서식 파일은 `<RECORD>` 요소에서 4개의 필드에 있는 데이터 값을 문자 데이터로 표현합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-400">In the `<RECORD>` element, the format file represents the data values in all four fields as character data.</span></span> <span data-ttu-id="df8b5-401">각 필드에서 TERMINATOR 특성은 데이터 값 다음에 오는 종결자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-401">For each field, the TERMINATOR attribute indicates the terminator that follows the data value.</span></span>  
  
 <span data-ttu-id="df8b5-402">서식 파일은 `<ROW>` 요소의 `Age` 열을 첫 번째 필드에, `FirstName` 열을 세 번째 필드에, `LastName` 열을 네 번째 필드에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-402">In the `<ROW>` element, the format file maps the column `Age` to the first field, the column `FirstName` to the third field, and the column `LastName` to the fourth field.</span></span>  
  
```  
<BCPFORMAT   
xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <RECORD>  
    <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="12"/>  
    <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="10"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
    <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="20"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
    <FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n"   
      MAX_LENGTH="30"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  </RECORD>  
  <ROW>  
    <COLUMN SOURCE="1" NAME="age" xsi:type="SQLINT"/>  
    <COLUMN SOURCE="3" NAME="firstname" xsi:type="SQLVARYCHAR"/>  
    <COLUMN SOURCE="4" NAME="lastname" xsi:type="SQLVARYCHAR"/>  
  </ROW>  
</BCPFORMAT>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="df8b5-403">해당하는 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 예제는 [서식 파일을 사용하여 데이터 필드 건너뛰기&#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df8b5-403">For an equivalent [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] example, see [Use a Format File to Skip a Data Field &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md).</span></span>  
  
###  <a name="d-mapping-field-xsitype-to-column-xsitype"></a><a name="MapXSItype"></a> <span data-ttu-id="df8b5-404">4.</span><span class="sxs-lookup"><span data-stu-id="df8b5-404">D.</span></span> <span data-ttu-id="df8b5-405">\<FIELD> xsi:type을 \<COLUMN> xsi: type에 매핑</span><span class="sxs-lookup"><span data-stu-id="df8b5-405">Mapping \<FIELD> xsi:type to \<COLUMN> xsi:type</span></span>  
 <span data-ttu-id="df8b5-406">다음 예에서는 다양한 형식의 필드와 함께 해당 필드와 열의 매핑을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-406">The following example shows different types of fields and their mappings to columns.</span></span>  
  
```  
<?xml version = "1.0"?>  
<BCPFORMAT  
xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
   <RECORD>  
      <FIELD xsi:type="CharTerm" ID="C1" TERMINATOR="\t"   
            MAX_LENGTH="4"/>  
      <FIELD xsi:type="CharFixed" ID="C2" LENGTH="10"   
         COLLATION="SQL_LATIN1_GENERAL_CP1_CI_AS"/>  
      <FIELD xsi:type="CharPrefix" ID="C3" PREFIX_LENGTH="2"   
         MAX_LENGTH="32" COLLATION="SQL_LATIN1_GENERAL_CP1_CI_AS"/>  
      <FIELD xsi:type="NCharTerm" ID="C4" TERMINATOR="\t"   
         MAX_LENGTH="4"/>  
      <FIELD xsi:type="NCharFixed" ID="C5" LENGTH="10"   
         COLLATION="SQL_LATIN1_GENERAL_CP1_CI_AS"/>  
      <FIELD xsi:type="NCharPrefix" ID="C6" PREFIX_LENGTH="2"   
         MAX_LENGTH="32" COLLATION="SQL_LATIN1_GENERAL_CP1_CI_AS"/>  
      <FIELD xsi:type="NativeFixed" ID="C7" LENGTH="4"/>  
   </RECORD>  
   <ROW>  
      <COLUMN SOURCE="C1" NAME="Age" xsi:type="SQLTINYINT"/>  
      <COLUMN SOURCE="C2" NAME="FirstName" xsi:type="SQLVARYCHAR"   
      LENGTH="16" NULLABLE="NO"/>  
      <COLUMN SOURCE="C3" NAME="LastName" />  
      <COLUMN SOURCE="C4" NAME="Salary" xsi:type="SQLMONEY"/>  
      <COLUMN SOURCE="C5" NAME="Picture" xsi:type="SQLIMAGE"/>  
      <COLUMN SOURCE="C6" NAME="Bio" xsi:type="SQLTEXT"/>  
      <COLUMN SOURCE="C7" NAME="Interest"xsi:type="SQLDECIMAL"   
      PRECISION="5" SCALE="3"/>  
   </ROW>  
</BCPFORMAT>  
```  
  
###  <a name="e-mapping-xml-data-to-a-table"></a><a name="MapXMLDataToTbl"></a> <span data-ttu-id="df8b5-407">5.</span><span class="sxs-lookup"><span data-stu-id="df8b5-407">E.</span></span> <span data-ttu-id="df8b5-408">XML 데이터를 테이블에 매핑</span><span class="sxs-lookup"><span data-stu-id="df8b5-408">Mapping XML data to a table</span></span>  
 <span data-ttu-id="df8b5-409">다음 예에서는 두 개의 빈 열을 가진 테이블(`t_xml`)을 만듭니다. 테이블의 첫 번째 열은 `int` 데이터 형식에, 두 번째 열은 `xml` 데이터 형식에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-409">The following example creates an empty two-column table (`t_xml`), in which the first column maps to the `int` data type and the second column maps to the `xml` data type.</span></span>  
  
```  
CREATE TABLE t_xml (c1 int, c2 xml)  
```  
  
 <span data-ttu-id="df8b5-410">다음 XML 서식 파일에서는 `t_xml`테이블에 데이터 파일을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-410">The following XML format file would load a data file into table `t_xml`.</span></span>  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="NativePrefix" PREFIX_LENGTH="1"/>  
  <FIELD ID="2" xsi:type="NCharPrefix" PREFIX_LENGTH="8"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="c1" xsi:type="SQLINT"/>  
  <COLUMN SOURCE="2" NAME="c2" xsi:type="SQLNCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
###  <a name="f-importing-fixed-length-or-fixed-width-fields"></a><a name="ImportFixedFields"></a> <span data-ttu-id="df8b5-411">6.</span><span class="sxs-lookup"><span data-stu-id="df8b5-411">F.</span></span> <span data-ttu-id="df8b5-412">고정 길이 또는 고정 너비 필드 가져오기</span><span class="sxs-lookup"><span data-stu-id="df8b5-412">Importing fixed-length or fixed-width fields</span></span>  
 <span data-ttu-id="df8b5-413">다음 예에서는 `10` 자 또는 `6` 자의 각 고정 필드에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-413">The following example describes fixed fields of `10` or `6` characters each.</span></span> <span data-ttu-id="df8b5-414">서식 파일은 이러한 필드 길이/너비를 각각 `LENGTH="10"` 및 `LENGTH="6"`으로 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-414">The format file represents these field lengths/widths as `LENGTH="10"` and `LENGTH="6"`, respectively.</span></span> <span data-ttu-id="df8b5-415">데이터 파일의 모든 행은 캐리지 리턴-줄바꿈 조합 {CR}{LF}로 끝납니다. 여기서 서식 파일은 `TERMINATOR="\r\n"`로 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="df8b5-415">Every row of the data files ends with a carriage return-line feed combination, {CR}{LF}, which the format file represents as `TERMINATOR="\r\n"`.</span></span>  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT  
       xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"  
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <RECORD>  
    <FIELD ID="1" xsi:type="CharFixed" LENGTH="10"/>  
    <FIELD ID="2" xsi:type="CharFixed" LENGTH="6"/>  
    <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n"  
  </RECORD>  
  <ROW>  
    <COLUMN SOURCE="1" NAME="C1" xsi:type="SQLINT" />  
    <COLUMN SOURCE="2" NAME="C2" xsi:type="SQLINT" />  
  </ROW>  
</BCPFORMAT>  
```  
  
###  <a name="additional-examples"></a><a name="AdditionalExamples"></a> <span data-ttu-id="df8b5-416">추가 예</span><span class="sxs-lookup"><span data-stu-id="df8b5-416">Additional Examples</span></span>  
 <span data-ttu-id="df8b5-417">비 XML 서식 파일과 XML 서식 파일의 추가 예를 보려면 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df8b5-417">For additional examples of both non-XML format files and XML format files, see the following topics:</span></span>  
  
-   [<span data-ttu-id="df8b5-418">서식 파일을 사용하여 테이블 열 건너뛰기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="df8b5-418">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [<span data-ttu-id="df8b5-419">서식 파일을 사용하여 데이터 필드 건너뛰기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="df8b5-419">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="df8b5-420">서식 파일을 사용하여 테이블 열을 데이터 파일 필드에 매핑&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="df8b5-420">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="df8b5-421">관련 작업</span><span class="sxs-lookup"><span data-stu-id="df8b5-421">Related Tasks</span></span>  
  
-   [<span data-ttu-id="df8b5-422">서식 파일 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="df8b5-422">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="df8b5-423">서식 파일을 사용하여 데이터 대량 가져오기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="df8b5-423">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="df8b5-424">서식 파일을 사용하여 테이블 열 건너뛰기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="df8b5-424">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [<span data-ttu-id="df8b5-425">서식 파일을 사용하여 데이터 필드 건너뛰기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="df8b5-425">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="df8b5-426">서식 파일을 사용하여 테이블 열을 데이터 파일 필드에 매핑&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="df8b5-426">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="df8b5-427">관련 내용</span><span class="sxs-lookup"><span data-stu-id="df8b5-427">Related Content</span></span>  
 <span data-ttu-id="df8b5-428">없음</span><span class="sxs-lookup"><span data-stu-id="df8b5-428">None.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df8b5-429">참고 항목</span><span class="sxs-lookup"><span data-stu-id="df8b5-429">See Also</span></span>  
 <span data-ttu-id="df8b5-430">[데이터 대량 가져오기 및 내보내기&#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="df8b5-430">[Bulk Import and Export of Data &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span></span>  
 <span data-ttu-id="df8b5-431">[데이터 형식&#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="df8b5-431">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 <span data-ttu-id="df8b5-432">[비 XML 서식 파일&#40;SQL Server&#41;](xml-format-files-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="df8b5-432">[Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md) </span></span>  
 [<span data-ttu-id="df8b5-433">데이터를 가져오거나 내보내기 위한 서식 파일&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="df8b5-433">Format Files for Importing or Exporting Data &#40;SQL Server&#41;</span></span>](format-files-for-importing-or-exporting-data-sql-server.md)  
  
  
