---
title: XML 태스크를 사용하여 XML 유효성 검사 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- XML validation
- XML, validating
ms.assetid: 224fc025-c21f-4d43-aa9d-5ffac337f9b0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 633a269f53c85353c956b33bff8fd3af518dad56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638914"
---
# <a name="validate-xml-with-the-xml-task"></a><span data-ttu-id="50ddf-102">Validate XML with the XML Task</span><span class="sxs-lookup"><span data-stu-id="50ddf-102">Validate XML with the XML Task</span></span>
  <span data-ttu-id="50ddf-103">XML 태스크의 `ValidationDetails` 속성을 사용하도록 설정하여 XML 문서의 유효성을 검사하고 풍부한 오류 출력을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50ddf-103">Validate XML documents and get rich error output by enabling the `ValidationDetails` property of the XML Task.</span></span>

 <span data-ttu-id="50ddf-104">다음 스크린샷에는 다양한 오류 출력을 제공하는 XML 유효성 검사에 필요한 설정이 포함된 **XML 태스크 편집기** 가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50ddf-104">The following screen shot shows the **XML Task Editor** with the settings required for XML validation with rich error output.</span></span>

 <span data-ttu-id="50ddf-105">![XML 태스크 편집기의 XML 태스크 속성](../media/xmltaskproperties.jpg "XML 태스크 편집기의 XML 태스크 속성")</span><span class="sxs-lookup"><span data-stu-id="50ddf-105">![XML task properties in the XML Task Editor](../media/xmltaskproperties.jpg "XML task properties in the XML Task Editor")</span></span>

 <span data-ttu-id="50ddf-106">`ValidationDetails` 속성을 사용할 수 있게 되기 전에 먼저 XML 태스크에 의해 수행된 XML 유효성 검사가 오류 또는 해당 위치에 대한 정보 없이 true 또는 false 결과만 반환했습니다.</span><span class="sxs-lookup"><span data-stu-id="50ddf-106">Before the `ValidationDetails` property was available, XML validation by the XML Task returned only a true or false result, with no information about errors or their locations.</span></span> <span data-ttu-id="50ddf-107">이제 `ValidationDetails`를 true로 설정할 경우 출력 파일에는 줄 번호 및 위치를 포함하여 모든 오류에 대한 자세한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="50ddf-107">Now, when you set `ValidationDetails` to true, the output file contains detailed information about every error including the line number and the position.</span></span> <span data-ttu-id="50ddf-108">이 정보를 사용하여 XML 문서의 오류를 이해하고, 찾고, 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50ddf-108">You can use this information to understand, locate, and fix errors in XML documents.</span></span>

 <span data-ttu-id="50ddf-109">대형 XML 문서 및 많은 수의 오류에 사용할 수 있도록 XML 유효성 검사 기능을 쉽게 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50ddf-109">The XML validation functionality scales easily for large XML documents and large numbers of errors.</span></span> <span data-ttu-id="50ddf-110">출력 파일 자체가 XML 형식이므로 출력을 쿼리하고 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50ddf-110">Since the output file itself is in XML format, you can query and analyze the output.</span></span> <span data-ttu-id="50ddf-111">예를 들어 출력에 오류가 많이 포함되어 있으면 이 항목에서 설명하는 대로 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 쿼리를 사용하여 오류를 그룹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50ddf-111">For example, if the output contains a large number of errors, you can group the errors by using a [!INCLUDE[tsql](../../../includes/tsql-md.md)] query, as described in this topic.</span></span>

> [!NOTE]
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="50ddf-112">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]( [!INCLUDE[ssIS](../../includes/ssis-md.md)] ) `ValidationDetails` 서비스 팩 2의 속성을 도입 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 했습니다.</span><span class="sxs-lookup"><span data-stu-id="50ddf-112">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) introduced the `ValidationDetails` property in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Service Pack 2.</span></span> <span data-ttu-id="50ddf-113">속성은 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 및 SQL Server 2016에서 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50ddf-113">The property is also available in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] and in SQL Server 2016.</span></span>

## <a name="sample-output-for-xml-thats-valid"></a><span data-ttu-id="50ddf-114">유효한 XML의 샘플 출력</span><span class="sxs-lookup"><span data-stu-id="50ddf-114">Sample output for XML that's valid</span></span>
 <span data-ttu-id="50ddf-115">아래에는 유효한 XML 파일의 유효성 결과가 포함된 샘플 출력 파일이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50ddf-115">Here is a sample output file with validation results for a valid XML file.</span></span>

```xml

<root xmlns:ns="https://schemas.microsoft.com/xmltools/2002/xmlvalidation">
    <metadata>
        <result>true</result>
        <errors>0</errors>
        <warnings>0</warnings>
        <startTime>2015-05-28T10:27:22.087</startTime>
        <endTime>2015-05-28T10:29:07.007</endTime>
        <xmlFile>d:\Temp\TestData.xml</xmlFile>
        <xsdFile>d:\Temp\TestSchema.xsd</xsdFile>
    </metadata>
    <messages />
</root>
```

## <a name="sample-output-for-xml-thats-not-valid"></a><span data-ttu-id="50ddf-116">유효하지 않은 XML의 샘플 출력</span><span class="sxs-lookup"><span data-stu-id="50ddf-116">Sample output for XML that's not valid</span></span>
 <span data-ttu-id="50ddf-117">아래에는 오류가 많지 않은 XML 파일의 유효성 결과가 포함된 샘플 출력 파일이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50ddf-117">Here is a sample output file with validation results for an XML file that contains a small number of errors.</span></span> <span data-ttu-id="50ddf-118">코드를 쉽게 확인할 수 있도록 \<error> 요소의 텍스트에 줄 바꿈이 적용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50ddf-118">The text of the \<error> elements has been wrapped for readability.</span></span>

```xml

<root xmlns:ns="https://schemas.microsoft.com/xmltools/2002/xmlvalidation">
    <metadata>
        <result>false</result>
        <errors>2</errors>
        <warnings>0</warnings>
        <startTime>2015-05-28T10:45:09.538</startTime>
        <endTime>2015-05-28T10:45:09.558</endTime>
        <xmlFile>C:\Temp\TestData.xml</xmlFile>
        <xsdFile>C:\Temp\TestSchema.xsd</xsdFile>
    </metadata>
    <messages>
        <error line="5" position="26">The 'ApplicantRole' element is invalid - The value 'wer3' is invalid
    according to its datatype 'ApplicantRoleType' - The Enumeration constraint failed.</error>
        <error line="16" position="28">The 'Phone' element is invalid - The value 'we3056666666' is invalid
     according to its datatype 'phone' - The Pattern constraint failed.</error>
    </messages>
</root>
```

## <a name="analyze-xml-validation-output-with-a-transact-sql-query"></a><span data-ttu-id="50ddf-119">Transact-SQL 쿼리를 통해 XML 유효성 검사 출력 분석</span><span class="sxs-lookup"><span data-stu-id="50ddf-119">Analyze XML validation output with a Transact-SQL query</span></span>
 <span data-ttu-id="50ddf-120">XML 유효성 검사의 출력에 오류가 많이 포함되어 있으면 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 쿼리를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 출력을 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50ddf-120">If the output of XML validation contains a large number of errors, you can use a [!INCLUDE[tsql](../../../includes/tsql-md.md)] query to load the output in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="50ddf-121">그런 다음 WHERE, GROUP BY, ORDER BY, JOIN 등을 비롯한 T-SQL 언어의 모든 기능을 사용하여 오류 목록을 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50ddf-121">Then you can analyze the error list with all the capabilities of the T-SQL language including WHERE, GROUP BY, ORDER BY, JOIN, and so forth.</span></span>

```sql
DECLARE @xml XML;

SELECT @xml = XmlDoc   
FROM OPENROWSET (BULK N'C:\Temp\XMLValidation_2016-02-212T10-41-00.xml', SINGLE_BLOB) AS Tab(XmlDoc);

-- Query # 1, flat list of errors
-- convert to relational/rectangular
;WITH XMLNAMESPACES ('https://schemas.microsoft.com/xmltools/2002/xmlvalidation' AS ns), rs AS
(
SELECT col.value('@line','INT') AS line
     , col.value('@position','INT') AS position
     , col.value('.','VARCHAR(1024)') AS error
FROM @XML.nodes('/root/messages/error') AS tab(col)
)
SELECT * FROM rs;
-- WHERE error LIKE '%whatever_string%'

-- Query # 2, count of errors grouped by the error message
-- convert to relational/rectangular
;WITH XMLNAMESPACES ('https://schemas.microsoft.com/xmltools/2002/xmlvalidation' AS ns), rs AS
(
SELECT col.value('@line','INT') AS line
     , col.value('@position','INT') AS position
     , col.value('.','VARCHAR(1024)') AS error
FROM @XML.nodes('/root/messages/error') AS tab(col)
)
SELECT COALESCE(error,'Total # of errors:') AS [error], COUNT(*) AS [counter]
FROM rs
GROUP BY GROUPING SETS ((error), ())
ORDER BY 2 DESC, COALESCE(error, 'Z');

```

 <span data-ttu-id="50ddf-122">위 텍스트에 나와 있는 두 번째 샘플 쿼리를 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 에서 표시한 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="50ddf-122">Here is the result in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] of the second sample query shown in the preceding text.</span></span>

 <span data-ttu-id="50ddf-123">![Management Studio에서 XML 오류를 그룹화하는 쿼리](../media/queryforxmlerrors.jpg "Management Studio에서 XML 오류를 그룹화하는 쿼리")</span><span class="sxs-lookup"><span data-stu-id="50ddf-123">![Query to group XML errors in Management Studio](../media/queryforxmlerrors.jpg "Query to group XML errors in Management Studio")</span></span>

## <a name="see-also"></a><span data-ttu-id="50ddf-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="50ddf-124">See Also</span></span>
 <span data-ttu-id="50ddf-125">[Xml 태스크](xml-task.md) [xml 태스크 편집기 &#40;일반 페이지&#41;](../xml-task-editor-general-page.md)</span><span class="sxs-lookup"><span data-stu-id="50ddf-125">[XML Task](xml-task.md) [XML Task Editor &#40;General Page&#41;](../xml-task-editor-general-page.md)</span></span>


