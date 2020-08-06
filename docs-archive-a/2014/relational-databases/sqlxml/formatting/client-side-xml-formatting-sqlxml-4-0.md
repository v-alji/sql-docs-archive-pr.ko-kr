---
title: 클라이언트 쪽 XML 서식 지정 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- FOR XML clause, formatting
- middle tier XML formatting [SQLXML]
- client-side XML formatting
- client-side-xml attribute
ms.assetid: 9630a21d-a93b-4d3b-8a25-c4b32399f993
author: rothja
ms.author: jroth
ms.openlocfilehash: bf4a680d79a25d24ebdf779b41fd3be5a5d6a605
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652706"
---
# <a name="client-side-xml-formatting-sqlxml-40"></a><span data-ttu-id="59c96-102">클라이언트 쪽 XML 서식 지정(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="59c96-102">Client-side XML Formatting (SQLXML 4.0)</span></span>
  <span data-ttu-id="59c96-103">이 항목에서는 클라이언트 쪽 XML 서식 지정에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-103">This topic provides information about client-side XML formatting.</span></span> <span data-ttu-id="59c96-104">클라이언트 쪽 서식 지정은 중간 계층의 XML 서식 지정을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-104">Client-side formatting refers to the formatting of XML on the middle tier.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="59c96-105">이 항목에서는 이미 FOR XML 절에 익숙한 사용자를 대상으로 클라이언트 쪽의 FOR XML 절 사용에 대한 추가 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-105">This topic provides additional information about using the FOR XML clause on the client side, and assumes you are already familiar with the FOR XML clause.</span></span> <span data-ttu-id="59c96-106">FOR xml에 대 한 자세한 내용은 [FOR xml을 사용 하 여 Xml 생성](../../xml/for-xml-sql-server.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="59c96-106">For more information about FOR XML, see [Constructing XML Using FOR XML](../../xml/for-xml-sql-server.md).</span></span>  
  
 <span data-ttu-id="59c96-107">**중요** 클라이언트 쪽 FOR XML 기능을 새 데이터 형식과 함께 사용 하려면 `xml` 클라이언트는 항상 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SQLOLEDB 공급자 대신 Native CLIENT (SQLNCLI11) 데이터 공급자를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-107">**Important** To use client-side FOR XML functionality with the new `xml` data type, clients should always use the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) data provider instead of the SQLOLEDB provider.</span></span> <span data-ttu-id="59c96-108">SQLNCLI11은 최신 버전의 SQL Server 공급자이며 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]에 도입된 데이터 형식을 완전히 이해합니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-108">SQLNCLI11 is the latest version of the SQL Server provider and fully understands data types introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="59c96-109">SQLOLEDB 공급자를 사용하는 클라이언트 쪽 FOR XML의 동작에서는 `xml` 데이터 형식을 문자열로 취급합니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-109">The behavior for client side FOR XML with the SQLOLEDB provider will treat `xml` data types as strings.</span></span>  
  
## <a name="formatting-xml-documents-on-the-client-side"></a><span data-ttu-id="59c96-110">클라이언트 쪽에서 XML 문서 서식 지정</span><span class="sxs-lookup"><span data-stu-id="59c96-110">Formatting XML Documents on the Client Side</span></span>  
 <span data-ttu-id="59c96-111">클라이언트 애플리케이션에서 다음 쿼리를 실행하는 경우를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-111">When a client application executes the following query:</span></span>  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
FOR XML RAW  
```  
  
 <span data-ttu-id="59c96-112">다음 쿼리 부분만 서버로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-112">...only this part of the query is sent to the server:</span></span>  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
```  
  
 <span data-ttu-id="59c96-113">서버에서 쿼리를 실행 하 고 클라이언트에 행 집합 (FirstName 및 LastNamecolumns 포함)을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-113">The server executes the query and returns a rowset (which contains FirstName and LastNamecolumns) to the client.</span></span> <span data-ttu-id="59c96-114">그러면 중간 계층에서 행 집합에 FOR XML 변환을 적용하고 XML 서식을 클라이언트에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-114">The middle tier then applies the FOR XML transformation to the rowset and returns XML formatting to the client.</span></span>  
  
 <span data-ttu-id="59c96-115">마찬가지로, XPath 쿼리를 실행하면 서버는 클라이언트에 행 집합을 반환하고 FOR XML EXPLICIT 변환이 클라이언트의 행 집합에 적용되어 필요한 XML 서식을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-115">Similarly, when you execute an XPath query, the server returns the rowset to the client and the FOR XML EXPLICIT transformation is applied to the rowset on the client, generating the desired XML formatting.</span></span>  
  
 <span data-ttu-id="59c96-116">다음 표에서는 클라이언트 쪽 FOR XML에서 지정할 수 있는 모드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-116">The following table shows the modes you can specify with client-side FOR XML.</span></span>  
  
|<span data-ttu-id="59c96-117">클라이언트 쪽 FOR XML 모드</span><span class="sxs-lookup"><span data-stu-id="59c96-117">Client-side FOR XML mode</span></span>|<span data-ttu-id="59c96-118">의견</span><span class="sxs-lookup"><span data-stu-id="59c96-118">Comment</span></span>|  
|-------------------------------|-------------|  
|<span data-ttu-id="59c96-119">RAW</span><span class="sxs-lookup"><span data-stu-id="59c96-119">RAW</span></span>|<span data-ttu-id="59c96-120">클라이언트 쪽 또는 서버 쪽 FOR XML에 지정될 경우 동일한 결과를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-120">Produces identical results when specified in client-side or server-side FOR XML.</span></span>|  
|<span data-ttu-id="59c96-121">NESTED</span><span class="sxs-lookup"><span data-stu-id="59c96-121">NESTED</span></span>|<span data-ttu-id="59c96-122">서버 쪽의 FOR XML AUTO 모드와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-122">Is similar to FOR XML AUTO mode on the server-side.</span></span>|  
|<span data-ttu-id="59c96-123">EXPLICIT</span><span class="sxs-lookup"><span data-stu-id="59c96-123">EXPLICIT</span></span>|<span data-ttu-id="59c96-124">서버 쪽 FOR XML EXPLICIT 모드와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-124">Is similar to server-side FOR XML EXPLICIT mode.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="59c96-125">AUTO 모드를 지정하고 클라이언트 쪽 XML 서식 지정을 요청하는 경우 전체 쿼리가 서버로 전송됩니다. 즉, XML 서식 지정이 서버에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-125">If you specify AUTO mode and request client-side XML formatting, the entire query is sent to the server; that is, XML formatting occurs on the server.</span></span> <span data-ttu-id="59c96-126">이는 편의상 수행되는 기능이지만 NESTED 모드는 생성되는 XML 문서의 요소 이름으로 기본 테이블 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-126">This is done for convenience, but note that the NESTED mode returns base table names as element names in the XML document that is generated.</span></span> <span data-ttu-id="59c96-127">일부 애플리케이션에는 기본 테이블을 이름이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-127">Some of the applications you write might require base table names.</span></span> <span data-ttu-id="59c96-128">예를 들어 저장 프로시저를 실행하고 결과 데이터를 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework의 데이터 세트에 로드한 후 나중에 DiffGram을 생성하여 테이블의 데이터를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-128">For example, you might execute a stored procedure and load the resulting data in a Dataset (in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework), and then later generate a DiffGram to update data in the tables.</span></span> <span data-ttu-id="59c96-129">이러한 경우 기본 테이블 정보가 필요할 수 있으므로 NESTED 모드를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-129">In such a case, you would need the base table information and you would have to use the NESTED mode.</span></span>  
  
## <a name="benefits-of-client-side-xml-formatting"></a><span data-ttu-id="59c96-130">클라이언트 쪽 XML 서식 지정의 이점</span><span class="sxs-lookup"><span data-stu-id="59c96-130">Benefits of Client-side XML formatting</span></span>  
 <span data-ttu-id="59c96-131">다음은 클라이언트에서 XML 서식 지정을 할 때의 이점입니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-131">The following are some benefits of formatting XML on the client.</span></span>  
  
### <a name="if-you-have-stored-procedures-on-the-server-that-return-a-single-rowset-you-can-request-client-side-for-xml-transformation-to-generate-an-xml"></a><span data-ttu-id="59c96-132">서버에 단일 행 집합을 반환하는 저장 프로시저가 있는 경우 클라이언트 쪽 FOR XML 변환을 요청하여 XML을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-132">If you have stored procedures on the server that return a single rowset, you can request client-side FOR XML transformation to generate an XML.</span></span>  
 <span data-ttu-id="59c96-133">예를 들어 다음과 같은 저장 프로시저가 있다고 가정해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="59c96-133">For example, consider the following stored procedure.</span></span> <span data-ttu-id="59c96-134">이 프로시저는 AdventureWorks 데이터베이스의 Person.Contact 테이블에서 직원의 이름과 성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-134">This procedure returns the first and last names of employees from the Person.Contact table in the AdventureWorks database:</span></span>  
  
```  
IF EXISTS (SELECT name FROM sysobjects  
   WHERE name = 'GetContacts' AND type = 'P')  
   DROP PROCEDURE GetContacts  
GO  
CREATE PROCEDURE GetContacts  
AS  
    SELECT   FirstName, LastName  
    FROM     Person.Contact  
```  
  
 <span data-ttu-id="59c96-135">다음 예제 XML 템플릿은 저장 프로시저를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-135">The following sample XML template executes the stored procedure.</span></span> <span data-ttu-id="59c96-136">FOR XML 절은 저장 프로시저 이름 뒤에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-136">The FOR XML clause is specified after the stored procedure name.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    EXEC GetContacts FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="59c96-137">템플릿에서 **클라이언트-xml** 특성이 1 (true)로 설정 되어 있기 때문에 저장 프로시저는 서버에서 실행 되 고 서버에서 반환 되는 2 열 행 집합은 중간 계층에서 xml로 변환 된 후 클라이언트에 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-137">Because the **client-side-xml** attribute is set to 1 (true) in the template, the stored procedure is executed on the server and the two-column rowset that is returned by the server is transformed into XML on the middle tier and returned to the client.</span></span> <span data-ttu-id="59c96-138">이 문서에는 결과의 일부분만 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-138">(Only a partial result is shown here.)</span></span>  
  
```  
 <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact FirstName="Gustavo" LastName="Achong" />   
  <Person.Contact FirstName="Catherine" LastName="Abel" />  
</ROOT>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="59c96-139">SQLXMLOLEDB 공급자 또는 SQLXML 관리되는 클래스를 사용하는 경우 `ClientSideXml` 속성을 사용하여 클라이언트 쪽 XML 서식 지정을 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-139">When you are using the SQLXMLOLEDB Provider or SQLXML Managed Classes, you can use the `ClientSideXml` property to request client-side XML formatting.</span></span>  
  
### <a name="the-workload-is-more-balanced"></a><span data-ttu-id="59c96-140">작업의 균형이 더 잘 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-140">The workload is more balanced.</span></span>  
 <span data-ttu-id="59c96-141">클라이언트에서 XML 서식 지정을 수행하므로 서버와 클라이언트 간에 작업 균형이 이루어지고 서버에서 다른 작업을 할 수 있는 여유가 확보됩니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-141">Because the client does the XML formatting, the workload is balanced between the server and client, freeing the server to do other things.</span></span>  
  
## <a name="supporting-client-side-xml-formatting"></a><span data-ttu-id="59c96-142">클라이언트 쪽 XML 서식 지정 지원</span><span class="sxs-lookup"><span data-stu-id="59c96-142">Supporting Client-side XML Formatting</span></span>  
 <span data-ttu-id="59c96-143">클라이언트 쪽 XML 서식 지정 기능을 지원하기 위해 SQLXML은 다음을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-143">To support the client-side XML formatting functionality, SQLXML provides:</span></span>  
  
-   <span data-ttu-id="59c96-144">SQLXMLOLEDB 공급자</span><span class="sxs-lookup"><span data-stu-id="59c96-144">SQLXMLOLEDB Provider</span></span>  
  
-   <span data-ttu-id="59c96-145">SQLXML 관리되는 클래스</span><span class="sxs-lookup"><span data-stu-id="59c96-145">SQLXML Managed Classes</span></span>  
  
-   <span data-ttu-id="59c96-146">향상된 XML 템플릿 지원</span><span class="sxs-lookup"><span data-stu-id="59c96-146">Enhanced XML template support</span></span>  
  
-   <span data-ttu-id="59c96-147">SqlXmlCommand. ClientSideXml 속성</span><span class="sxs-lookup"><span data-stu-id="59c96-147">SqlXmlCommand.ClientSideXml property</span></span>  
  
     <span data-ttu-id="59c96-148">SQLXML 관리되는 클래스의 이 속성을 true로 설정하여 클라이언트 쪽 서식 지정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-148">You can specify client-side formatting by setting this property of the SQLXML managed classes to true.</span></span>  
  
## <a name="enhanced-xml-template-support"></a><span data-ttu-id="59c96-149">향상된 XML 템플릿 지원</span><span class="sxs-lookup"><span data-stu-id="59c96-149">Enhanced XML Template Support</span></span>  
 <span data-ttu-id="59c96-150">부터 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 의 xml 템플릿은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **클라이언트 쪽 xml** 특성을 추가 하 여 향상 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-150">Beginning with [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], the XML template in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] has been enhanced with the addition of the **client-side-xml** attribute.</span></span> <span data-ttu-id="59c96-151">이 특성을 true로 설정하면 XML 서식이 클라이언트에서 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-151">If this attribute is set to true, XML is formatted on the client.</span></span> <span data-ttu-id="59c96-152">이 템플릿 특성은 SQLXMLOLEDB 공급자별 Clientside-by-side Xml 속성의 기능과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-152">Note that this template attribute is identical in functionality to the SQLXMLOLEDB Provider-specific ClientSideXML property.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="59c96-153">SQLXMLOLEDB 공급자를 사용 하는 ADO 응용 프로그램에서 XML 템플릿을 실행 하 고 템플릿에서 **클라이언트 쪽 xml** 특성과 공급자 clientside xml 속성을 둘 다 지정 하는 경우 템플릿에 지정 된 값이 우선 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="59c96-153">If you execute an XML template in an ADO application that is using the SQLXMLOLEDB Provider, and you specify both the **client-side-xml** attribute in the template and the provider ClientSideXML property, the value specified in the template takes precedence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59c96-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="59c96-154">See Also</span></span>  
 <span data-ttu-id="59c96-155">[클라이언트 쪽 및 서버 쪽 XML 서식 &#40;SQLXML 4.0&#41;의 아키텍처](server-side-xml-formatting-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="59c96-155">[Architecture of Client-side and Server-side XML Formatting &#40;SQLXML 4.0&#41;](server-side-xml-formatting-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="59c96-156">[FOR XML &#40;SQL Server&#41;](../../xml/for-xml-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="59c96-156">[FOR XML &#40;SQL Server&#41;](../../xml/for-xml-sql-server.md) </span></span>  
 <span data-ttu-id="59c96-157">[XML 보안 고려 사항은 SQLXML 4.0을 &#40;&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/for-xml-security-considerations-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="59c96-157">[FOR XML Security Considerations &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/for-xml-security-considerations-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="59c96-158">[SQLXML 4.0의 xml 데이터 형식 지원](../xml-data-type-support-in-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="59c96-158">[xml Data Type Support in SQLXML 4.0](../xml-data-type-support-in-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="59c96-159">[SQLXML 관리 되는 클래스](../../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md) </span><span class="sxs-lookup"><span data-stu-id="59c96-159">[SQLXML Managed Classes](../../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md) </span></span>  
 <span data-ttu-id="59c96-160">[클라이언트 쪽 및 서버 쪽 XML 서식 지정 &#40;SQLXML 4.0&#41;](client-side-vs-server-side-xml-formatting-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="59c96-160">[Client-side vs. Server-side XML Formatting &#40;SQLXML 4.0&#41;](client-side-vs-server-side-xml-formatting-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="59c96-161">[SqlXmlCommand 개체 &#40;SQLXML 관리 되는 클래스&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-managed-classes-sqlxmlcommand-object.md) </span><span class="sxs-lookup"><span data-stu-id="59c96-161">[SqlXmlCommand Object &#40;SQLXML Managed Classes&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-managed-classes-sqlxmlcommand-object.md) </span></span>  
 [<span data-ttu-id="59c96-162">XML 데이터&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="59c96-162">XML Data &#40;SQL Server&#41;</span></span>](../../xml/xml-data-sql-server.md)  
  
  
