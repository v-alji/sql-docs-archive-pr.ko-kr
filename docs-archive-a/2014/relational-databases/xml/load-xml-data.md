---
title: XML 데이터 로드 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XML data [SQL Server], loading
- loading XML data
ms.assetid: d1741e8d-f44e-49ec-9f14-10208b5468a7
author: rothja
ms.author: jroth
ms.openlocfilehash: c48d1d6feccb7df9fec9801ee56abcab99884754
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733672"
---
# <a name="load-xml-data"></a><span data-ttu-id="b74ef-102">XML 데이터 로드</span><span class="sxs-lookup"><span data-stu-id="b74ef-102">Load XML Data</span></span>
  <span data-ttu-id="b74ef-103">XML 데이터를 여러 가지 방법으로 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 으로 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-103">You can transfer XML data into [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in several ways.</span></span> <span data-ttu-id="b74ef-104">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-104">For example:</span></span>  
  
-   <span data-ttu-id="b74ef-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스의 [n]text 또는 image 열에 데이터가 있으면 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]를 사용하여 테이블을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-105">If you have your data in an [n]text or image column in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, you can import the table by using [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="b74ef-106">ALTER TABLE 문을 사용하여 열 유형을 XML로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-106">Change the column type to XML by using the ALTER TABLE statement.</span></span>  
  
-   <span data-ttu-id="b74ef-107">bcp out을 사용하여 다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에서 데이터를 대량 복사한 다음 bcp in을 사용하여 데이터를 최신 버전 데이터베이스로 대량 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-107">You can bulk copy your data from another [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database by using bcp out, and then bulk insert the data into the later version database by using bcp in.</span></span>  
  
-   <span data-ttu-id="b74ef-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스의 관계형 열에 데이터가 있는 경우 [n]text 열 및 행 식별자의 경우 기본 키 열(옵션)이 포함된 새 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-108">If you have data in relational columns in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, create a new table with an [n]text column and, optionally, a primary key column for a row identifier.</span></span> <span data-ttu-id="b74ef-109">클라이언트 쪽 프로그래밍을 사용하여 FOR XML로 서버에서 생성된 XML을 검색하고 이를 `[n]text` 열에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-109">Use client-side programming to retrieve the XML that is generated at the server with FOR XML and write it into the `[n]text` column.</span></span> <span data-ttu-id="b74ef-110">그런 다음 앞에서 언급한 기술을 사용하여 데이터를 최신 데이터베이스에 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-110">Then, use the previously mentioned techniques to transfer data to a later version database.</span></span> <span data-ttu-id="b74ef-111">최신 데이터베이스에 있는 XML 열로 XML을 직접 작성하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-111">You can choose to write the XML into an XML column in the later version database directly.</span></span>  
  
## <a name="bulk-loading-xml-data"></a><span data-ttu-id="b74ef-112">XML 데이터 대량 로드</span><span class="sxs-lookup"><span data-stu-id="b74ef-112">Bulk loading XML data</span></span>  
 <span data-ttu-id="b74ef-113">bcp와 같은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 대량 로드 기능을 사용하여 XML 데이터를 서버에 대량 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-113">You can bulk load XML data into the server by using the bulk loading capabilities of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], such as bcp.</span></span> <span data-ttu-id="b74ef-114">OPENROWSET을 사용하면 데이터를 파일에서 XML 열로 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-114">OPENROWSET allows you to load data into an XML column from files.</span></span> <span data-ttu-id="b74ef-115">다음 예에서는 이러한 점을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-115">The following example illustrates this point.</span></span>  
  
##### <a name="example-loading-xml-from-files"></a><span data-ttu-id="b74ef-116">예제: 파일에서 XML 로드</span><span class="sxs-lookup"><span data-stu-id="b74ef-116">Example: Loading XML from Files</span></span>  
 <span data-ttu-id="b74ef-117">이 예에서는 테이블 T에 행을 삽입하는 방법을 보여 줍니다. XML 열의 값은 C:\MyFile\xmlfile.xml 파일로부터 CLOB으로 로드되고 정수 열에는 값 10이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-117">This example shows how to insert a row in table T. The value of the XML column is loaded from file C:\MyFile\xmlfile.xml as CLOB, and the integer column is supplied the value 10.</span></span>  
  
```  
INSERT INTO T  
SELECT 10, xCol  
FROM    (SELECT *      
    FROM OPENROWSET (BULK 'C:\MyFile\xmlfile.xml', SINGLE_CLOB)   
 AS xCol) AS R(xCol)  
```  
  
## <a name="text-encoding"></a><span data-ttu-id="b74ef-118">텍스트 인코딩</span><span class="sxs-lookup"><span data-stu-id="b74ef-118">Text Encoding</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b74ef-119">는 XML 데이터를 유니코드(UTF-16)로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-119">stores XML data in Unicode (UTF-16).</span></span> <span data-ttu-id="b74ef-120">서버에서 검색된 XML 데이터는 UTF-16 인코딩으로 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-120">XML data retrieved from the server comes out in UTF-16 encoding.</span></span> <span data-ttu-id="b74ef-121">다른 인코딩이 필요한 경우 검색된 데이터에서 필요한 변환을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-121">If you want a different encoding, you have to perform the required conversion on the retrieved data.</span></span> <span data-ttu-id="b74ef-122">일부 경우 XML 데이터는 다른 인코딩으로 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-122">Sometimes, the XML data may be in a different encoding.</span></span> <span data-ttu-id="b74ef-123">이 경우 데이터를 로드하는 동안 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-123">If it is, you have to use care during data loading.</span></span> <span data-ttu-id="b74ef-124">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-124">For example:</span></span>  
  
-   <span data-ttu-id="b74ef-125">XML 텍스트가 유니코드(UCS-2, UTF-16)인 경우 문제 없이 이를 XML 열, 변수 또는 매개 변수에 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-125">If your text XML is in Unicode (UCS-2, UTF-16), you can assign it to an XML column, variable, or parameter  without any problems.</span></span>  
  
-   <span data-ttu-id="b74ef-126">인코딩이 유니코드가 아니고 암시적인 경우 원본 코드 페이지로 인해 데이터베이스의 문자열 코드 페이지는 로드하려는 코드 지점과 호환되거나 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-126">If the encoding is not Unicode and is implicit, because of the source code page, the string code page in the database should be the same as or compatible with the code points that you want to load.</span></span> <span data-ttu-id="b74ef-127">필요한 경우 COLLATE를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-127">If required, use COLLATE.</span></span> <span data-ttu-id="b74ef-128">이러한 서버 코드 페이지가 없는 경우 명시적 XML 선언을 올바른 인코딩으로 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-128">If no such server code page exists, you have to add an explicit XML declaration with the correct encoding.</span></span>  
  
-   <span data-ttu-id="b74ef-129">명시적 인코딩을 사용하려면 코드 페이지와 상호 작용이 없는 `varbinary()` 유형을 사용하거나 적합한 코드 페이지의 문자열 유형을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-129">To use an explicit encoding, use either the `varbinary()` type, which has no interaction with code pages, or use a string type of the appropriate code page.</span></span> <span data-ttu-id="b74ef-130">그런 다음 데이터를 XML 열, 변수 또는 매개 변수에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-130">Then, assign the data to an XML column, variable, or parameter.</span></span>  
  
### <a name="example-explicitly-specifying-an-encoding"></a><span data-ttu-id="b74ef-131">예제: 인코딩을 명시적으로 지정</span><span class="sxs-lookup"><span data-stu-id="b74ef-131">Example: Explicitly Specifying an Encoding</span></span>  
 <span data-ttu-id="b74ef-132">명시적 XML 선언 없이 `varchar(max)`로 저장된 XML 문서인 vcdoc가 있다고 가정해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="b74ef-132">Assume that you have an XML document, vcdoc, stored as `varchar(max)` that does not have an explicit XML declaration.</span></span> <span data-ttu-id="b74ef-133">다음 문은 "iso8859-1" 인코딩으로 XML 선언을 추가하고 XML 문서를 연결하고 결과를 `varbinary(max)`로 캐스팅하여 바이트 표현이 유지되도록 한 다음 마지막으로 XML로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-133">The following statement adds an XML declaration with the encoding "iso8859-1", concatenates the XML document, casts the result to `varbinary(max)` so that the byte representation is preserved, and then finally casts it to XML.</span></span> <span data-ttu-id="b74ef-134">이렇게 하면 XML 프로세서가 지정된 "iso8859-1" 인코딩에 따라 데이터를 구문 분석하고 문자열 값에 대한 해당 UTF-16 표현을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-134">This enables the XML processor to parse the data according to the specified encoding "iso8859-1" and generate the corresponding UTF-16 representation for string values.</span></span>  
  
```  
SELECT CAST(   
CAST (('<?xml version="1.0" encoding="iso8859-1"?>'+ vcdoc) AS VARBINARY (MAX))   
 AS XML)  
```  
  
### <a name="string-encoding-incompatibilities"></a><span data-ttu-id="b74ef-135">문자열 인코딩 비호환성</span><span class="sxs-lookup"><span data-stu-id="b74ef-135">String Encoding Incompatibilities</span></span>  
 <span data-ttu-id="b74ef-136">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 쿼리 편집기 창에서 XML을 문자열 리터럴로 복사 및 붙여 넣는 경우 [N]VARCHAR 문자열 인코딩이 호환되지 않는 경우가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-136">If you copy and paste XML as a string literal into the Query Editor window in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you might experience [N]VARCHAR string encoding incompatibilities.</span></span> <span data-ttu-id="b74ef-137">이것은 해당 XML 인스턴스의 인코딩에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-137">This will depend on the encoding of your XML instance.</span></span> <span data-ttu-id="b74ef-138">대부분의 경우 XML 선언을 제거해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-138">In many cases, you may want to remove the XML declaration.</span></span> <span data-ttu-id="b74ef-139">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-139">For example:</span></span>  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
  <xsd:schema ...  
```  
  
 <span data-ttu-id="b74ef-140">그런 다음 해당 XML 인스턴스를 유니코드 인스턴스로 만들기 위해 N을 포함시켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-140">You should then include an N to make the XML instance an instance of Unicode.</span></span> <span data-ttu-id="b74ef-141">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b74ef-141">For example:</span></span>  
  
```  
-- Assign XML instance to a variable.  
DECLARE @X XML  
SET @X = N'...'  
-- Insert XML instance into an xml type column.  
INSERT INTO T VALUES (N'...')  
-- Create an XML schema collection  
CREATE XML SCHEMA COLLECTION XMLCOLL1 AS N'<xsd:schema ... '  
```  
  
## <a name="see-also"></a><span data-ttu-id="b74ef-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b74ef-142">See Also</span></span>  
 [<span data-ttu-id="b74ef-143">XML 데이터&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b74ef-143">XML Data &#40;SQL Server&#41;</span></span>](xml-data-sql-server.md)  
  
  
