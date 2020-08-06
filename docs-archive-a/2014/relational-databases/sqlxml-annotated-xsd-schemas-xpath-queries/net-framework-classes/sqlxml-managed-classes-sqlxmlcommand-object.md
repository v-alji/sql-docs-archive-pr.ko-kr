---
title: SqlXmlCommand 개체 (SQLXML 관리 되는 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- void ExecuteNonQuery() method
- namespaces property
- Stream ExecuteStream() method
- CommandType property
- RootTag property
- OutputEncoding property
- XmlReader ExecuteXmlReader() method
- Managed Classes [SQLXML], SqlXmlCommand object
- SQLXML Managed Classes, SqlXmlCommand object
- Base Path property
- void ClearParameters() method
- public void ExecuteToStream(Stream outputStream) method
- SqlXmlCommand object
- CommandText property
- XslPath property
- SchemaPath property
- SqlXmlParameter CreateParameter() method
- ClientSideXML property
- CommandStream property
ms.assetid: c1f9e0bb-a89d-4d6a-a96e-289ef516a3a6
author: rothja
ms.author: jroth
ms.openlocfilehash: 78b72581f549ea007dae0cdc7044fd9a809920af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651567"
---
# <a name="sqlxmlcommand-object-sqlxml-managed-classes"></a><span data-ttu-id="ce6e9-102">SqlXmlCommand 개체(SQLXML 관리되는 클래스)</span><span class="sxs-lookup"><span data-stu-id="ce6e9-102">SqlXmlCommand Object (SQLXML Managed Classes)</span></span>
  <span data-ttu-id="ce6e9-103">SqlXmlCommand 개체에 대 한 생성자입니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-103">This is the constructor for the SqlXmlCommand object:</span></span>  
  
```  
public SqlXmlCommand(string cnString)  
```  
  
 <span data-ttu-id="ce6e9-104">여기서 `cnString` 는 서버, 데이터베이스 및 로그인 정보를 식별 하는 ADO 또는 OLEDB 연결 문자열입니다 (예:) `Provider=SQLOLEDB; Server=(local); database=AdventureWorks; Integrated Security=SSPI"` .</span><span class="sxs-lookup"><span data-stu-id="ce6e9-104">Where `cnString` is the ADO or OLEDB connection string that identifies the server, database, and the login information-for example, `Provider=SQLOLEDB; Server=(local); database=AdventureWorks; Integrated Security=SSPI"`.</span></span>  
  
 <span data-ttu-id="ce6e9-105">연결 문자열에서 `Provider`는 SQLOLEDB여야 하고 `Data Provider`는 공급자 문자열에 포함되면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-105">In the connection string, the `Provider` must be SQLOLEDB and the `Data Provider` should not be included in the provider string).</span></span>  
  
 <span data-ttu-id="ce6e9-106">작업 예제는 [SQL 쿼리 실행 &#40;SQLXML 관리 되는 클래스&#41;](sqlxml-4-0-net-framework-support-managed-classes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-106">For a working sample, see [Executing SQL Queries &#40;SQLXML Managed Classes&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ce6e9-107">메서드</span><span class="sxs-lookup"><span data-stu-id="ce6e9-107">Methods</span></span>  
 <span data-ttu-id="ce6e9-108">TheSqlXmlCommand 개체는 명령을 실행 하기 위해 다음 메서드를 비롯 한 여러 메서드를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-108">TheSqlXmlCommand object supports several methods, including the following methods for executing a command:</span></span>  
  
 <span data-ttu-id="ce6e9-109">void ExecuteNonQuery ()</span><span class="sxs-lookup"><span data-stu-id="ce6e9-109">void ExecuteNonQuery()</span></span>  
 <span data-ttu-id="ce6e9-110">명령을 실행하지만 아무것도 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-110">Executes the command, but does not return anything.</span></span> <span data-ttu-id="ce6e9-111">이 메서드는 쿼리를 사용하지 않는 명령, 즉 아무것도 반환하지 않는 명령을 실행하려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-111">This method is useful if you want to execute a nonquery command (that is, a command that does not return anything).</span></span> <span data-ttu-id="ce6e9-112">예를 들어 레코드를 업데이트하지만 아무것도 반환하지 않는 DiffGram 또는 updategram이 이러한 메서드에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-112">An example is executing an updategram or a DiffGram that updates records but returns nothing.</span></span>  
  
 <span data-ttu-id="ce6e9-113">Stream ExecuteStream ()</span><span class="sxs-lookup"><span data-stu-id="ce6e9-113">Stream ExecuteStream()</span></span>  
 <span data-ttu-id="ce6e9-114">새 스트림 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-114">Returns a new Stream object.</span></span> <span data-ttu-id="ce6e9-115">이 메서드는 쿼리 결과를 새 스트림에 반환하려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-115">This method is useful when you want the query results returned to you in a new stream.</span></span> <span data-ttu-id="ce6e9-116">작업 예제는 [SQL 쿼리 실행 &#40;SQLXML 관리 되는 클래스&#41;](sqlxml-4-0-net-framework-support-managed-classes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-116">For a working sample, see [Executing SQL Queries &#40;SQLXML Managed Classes&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).</span></span>  
  
 <span data-ttu-id="ce6e9-117">public void ExecuteToStream (Stream outputStream)</span><span class="sxs-lookup"><span data-stu-id="ce6e9-117">public void ExecuteToStream(Stream outputStream)</span></span>  
 <span data-ttu-id="ce6e9-118">쿼리 결과를 기존 스트림에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-118">Writes the query results to an existing stream.</span></span> <span data-ttu-id="ce6e9-119">이 메서드는 결과를 추가 해야 하는 스트림이 있는 경우에 유용 합니다 (예: 쿼리 결과가 OutputStream에 기록 되도록 하려면).</span><span class="sxs-lookup"><span data-stu-id="ce6e9-119">This method is useful when you have a stream to which you need the results appended (for example, to have the query results written to the System.Web.HttpResponse.OutputStream).</span></span> <span data-ttu-id="ce6e9-120">작업 예제는 [SQL 쿼리 실행 &#40;SQLXML 관리 되는 클래스&#41;](sqlxml-4-0-net-framework-support-managed-classes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-120">For a working sample, see [Executing SQL Queries &#40;SQLXML Managed Classes&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).</span></span>  
  
 <span data-ttu-id="ce6e9-121">XmlReader ExecuteXmlReader ()</span><span class="sxs-lookup"><span data-stu-id="ce6e9-121">XmlReader ExecuteXmlReader()</span></span>  
 <span data-ttu-id="ce6e9-122">XmlReader 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-122">Returns an XmlReader object.</span></span> <span data-ttu-id="ce6e9-123">이 메서드를 사용 하 여 XmlReader 개체의 데이터를 직접 조작 하거나 System.Xml 연결 가능한 아키텍처에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-123">You can use this method to either manipulate data in the XmlReader object directly or plug in the chainable architecture of System.Xml.</span></span> <span data-ttu-id="ce6e9-124">자세한 내용은 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-124">For more information, see the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework documentation.</span></span> <span data-ttu-id="ce6e9-125">작업 예제는 [ExecuteXMLReader 메서드를 사용 하 여 SQL 쿼리 실행](executing-sql-queries-by-using-the-executexmlreader-method.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-125">For a working sample, see [Executing SQL Queries by Using the ExecuteXMLReader Method](executing-sql-queries-by-using-the-executexmlreader-method.md).</span></span>  
  
 <span data-ttu-id="ce6e9-126">TheSqlXmlCommand 개체는 다음과 같은 추가 메서드도 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-126">TheSqlXmlCommand object also supports these additional methods:</span></span>  
  
 <span data-ttu-id="ce6e9-127">SqlXmlParameter CreateParameter ()</span><span class="sxs-lookup"><span data-stu-id="ce6e9-127">SqlXmlParameter CreateParameter()</span></span>  
 <span data-ttu-id="ce6e9-128">SqlXmlParameter 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-128">Creates an SqlXmlParameter object.</span></span> <span data-ttu-id="ce6e9-129">이 개체의 *Name* 및 *Value* 매개 변수에 대 한 값을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-129">You can set values for the *Name* and *Value* parameters of this object.</span></span> <span data-ttu-id="ce6e9-130">이 메서드는 명령에 매개 변수를 전달하려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-130">This method is useful if you want to pass parameters to a command.</span></span> <span data-ttu-id="ce6e9-131">작업 예제는 [SQL 쿼리 실행 &#40;SQLXML 관리 되는 클래스&#41;](sqlxml-4-0-net-framework-support-managed-classes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-131">For a working sample, see [Executing SQL Queries &#40;SQLXML Managed Classes&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).</span></span>  
  
 <span data-ttu-id="ce6e9-132">void ClearParameters ()</span><span class="sxs-lookup"><span data-stu-id="ce6e9-132">void ClearParameters()</span></span>  
 <span data-ttu-id="ce6e9-133">지정된 명령 개체에 대해 만든 매개 변수를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-133">Clears parameter(s) that were created for a given command object.</span></span> <span data-ttu-id="ce6e9-134">이 메서드는 동일한 명령 개체에 여러 개의 쿼리를 실행하려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-134">This method is useful if you want to execute multiple queries on the same command object.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ce6e9-135">속성</span><span class="sxs-lookup"><span data-stu-id="ce6e9-135">Properties</span></span>  
 <span data-ttu-id="ce6e9-136">SqlXmlCommand 개체는 다음 속성도 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-136">The SqlXmlCommand object also supports these properties:</span></span>  
  
 <span data-ttu-id="ce6e9-137">ClientSideXml</span><span class="sxs-lookup"><span data-stu-id="ce6e9-137">ClientSideXml</span></span>  
 <span data-ttu-id="ce6e9-138">True로 설정할 경우 행 집합과 XML 사이의 변환을 서버 대신 클라이언트에서 수행하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-138">When set to True, specifies that conversion of the rowset to XML is to occur on the client instead of on the server.</span></span> <span data-ttu-id="ce6e9-139">이 속성은 성능 부하를 중간 계층으로 이동하려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-139">This property is useful when you want to move the performance load to the middle tier.</span></span> <span data-ttu-id="ce6e9-140">이 속성을 사용하면 기존의 저장 프로시저를 FOR XML에 래핑하여 XML 출력을 얻을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-140">The property also allows you to wrap the existing stored procedures with FOR XML to get XML output.</span></span>  
  
 <span data-ttu-id="ce6e9-141">SchemaPath</span><span class="sxs-lookup"><span data-stu-id="ce6e9-141">SchemaPath</span></span>  
 <span data-ttu-id="ce6e9-142">디렉터리 경로를 포함한 매핑 스키마의 이름입니다(예: C:\x\y\MySchema.xml).</span><span class="sxs-lookup"><span data-stu-id="ce6e9-142">The name of the mapping schema along with the directory path (for example, C:\x\y\MySchema.xml).</span></span> <span data-ttu-id="ce6e9-143">이 속성은 XPath 쿼리의 매핑 스키마를 지정할 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-143">This property is useful for specifying a mapping schema for XPath queries.</span></span> <span data-ttu-id="ce6e9-144">이 속성에는 절대 경로 또는 상대 경로를 지정할 수 있으며</span><span class="sxs-lookup"><span data-stu-id="ce6e9-144">The path that is specified can be absolute or relative.</span></span> <span data-ttu-id="ce6e9-145">경로가 상대 경로 이면 기본 경로에 지정 된 기본 경로를 사용 하 여 상대 경로를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-145">If the path is relative, the base path that is specified in Base Path is used to resolve the relative path.</span></span> <span data-ttu-id="ce6e9-146">기본 경로가 지정되어 있지 않으면 상대 경로는 현재 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-146">If no base path is specified, the relative path is relative to the current directory.</span></span> <span data-ttu-id="ce6e9-147">작업 예제는 [.Net 환경에서 SQLXML 기능에 액세스](accessing-sqlxml-functionality-in-the-net-environment.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-147">For a working sample, see [Accessing SQLXML Functionality in the .NET Environment](accessing-sqlxml-functionality-in-the-net-environment.md).</span></span>  
  
 <span data-ttu-id="ce6e9-148">XslPath</span><span class="sxs-lookup"><span data-stu-id="ce6e9-148">XslPath</span></span>  
 <span data-ttu-id="ce6e9-149">디렉터리 경로를 포함한 XSL 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-149">The name of the XSL file along with the directory path.</span></span> <span data-ttu-id="ce6e9-150">이 속성에는 절대 경로 또는 상대 경로를 지정할 수 있으며</span><span class="sxs-lookup"><span data-stu-id="ce6e9-150">The path that is specified can be absolute or relative.</span></span> <span data-ttu-id="ce6e9-151">경로가 상대 경로 이면 기본 경로에 지정 된 기본 경로를 사용 하 여 상대 경로를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-151">If the path is relative, the base path that is specified in Base Path is used to resolve the relative path.</span></span> <span data-ttu-id="ce6e9-152">기본 경로가 지정되어 있지 않으면 상대 경로는 현재 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-152">If no base path is specified, the relative path is relative to the current directory.</span></span> <span data-ttu-id="ce6e9-153">작업 예제는 [XSL 변환 적용 &#40;SQLXML 관리 되는 클래스&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-153">For a working sample, see [Applying an XSL Transformation &#40;SQLXML Managed Classes&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md).</span></span>  
  
 <span data-ttu-id="ce6e9-154">기본 경로</span><span class="sxs-lookup"><span data-stu-id="ce6e9-154">Base Path</span></span>  
 <span data-ttu-id="ce6e9-155">기본 경로(디렉터리 경로)입니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-155">The base path (a directory path).</span></span> <span data-ttu-id="ce6e9-156">이 속성은 XslPath 속성을 사용 하 여 XSL 파일에 대해 지정 된 상대 경로를 확인 하거나, SchemaPath 속성을 사용 하 여 매핑 스키마 파일을 확인 하거나, 특성을 사용 하 여 지정 된 XML 템플릿의 외부 스키마 참조를 확인 하는 데 유용 `mapping-schema` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-156">This property is useful for resolving a relative path that is specified for an XSL file (by using the XslPath property), a mapping schema file (by using the SchemaPath property), or an external schema reference in an XML template (specified by using the `mapping-schema` attribute).</span></span>  
  
 <span data-ttu-id="ce6e9-157">OutputEncoding</span><span class="sxs-lookup"><span data-stu-id="ce6e9-157">OutputEncoding</span></span>  
 <span data-ttu-id="ce6e9-158">명령을 실행하여 반환되는 스트림의 인코딩을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-158">Specifies the encoding for the stream that is returned when the command executes.</span></span> <span data-ttu-id="ce6e9-159">이 속성은 반환되는 스트림에 특정 인코딩을 사용하려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-159">This property is useful for requesting a specific encoding for the stream that is returned.</span></span> <span data-ttu-id="ce6e9-160">일반적으로 UTF-8, ANSI 및 유니코드와 같은 인코딩이 사용되며</span><span class="sxs-lookup"><span data-stu-id="ce6e9-160">Some commonly used encodings are UTF-8, ANSI, and Unicode.</span></span> <span data-ttu-id="ce6e9-161">기본 인코딩은 UTF-8입니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-161">UTF-8 is the default encoding.</span></span>  
  
 <span data-ttu-id="ce6e9-162">네임스페이스</span><span class="sxs-lookup"><span data-stu-id="ce6e9-162">Namespaces</span></span>  
 <span data-ttu-id="ce6e9-163">네임스페이스를 사용하는 XPath 쿼리를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-163">Enables the execution of XPath queries that use namespaces.</span></span> <span data-ttu-id="ce6e9-164">네임 스페이스가 포함 된 XPath 쿼리에 대 한 자세한 내용은 [SQLXML 관리 되는&#41;클래스 &#40;네임 스페이스를 사용 하 여 Xpath 쿼리 실행 ](executing-xpath-queries-with-namespaces-sqlxml-managed-classes.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-164">For more information about XPath queries with namespaces, see [Executing XPath Queries with Namespaces &#40;SQLXML Managed Classes&#41;](executing-xpath-queries-with-namespaces-sqlxml-managed-classes.md).</span></span> <span data-ttu-id="ce6e9-165">작업 예제는 [&#41;SQLXML 관리 되는 클래스 &#40;XPath 쿼리 실행 ](executing-xpath-queries-sqlxml-managed-classes.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-165">For a working sample, see [Executing XPath Queries &#40;SQLXML Managed Classes&#41;](executing-xpath-queries-sqlxml-managed-classes.md).</span></span>  
  
 <span data-ttu-id="ce6e9-166">RootTag</span><span class="sxs-lookup"><span data-stu-id="ce6e9-166">RootTag</span></span>  
 <span data-ttu-id="ce6e9-167">명령을 실행하여 생성된 XML의 단일 루트 요소를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-167">Provides the single root element for XML generated by command execution.</span></span> <span data-ttu-id="ce6e9-168">유효한 XML 문서에는 루트 수준의 단일 태그가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-168">A valid XML document requires a single root-level tag.</span></span> <span data-ttu-id="ce6e9-169">명령을 실행하여 XML 조각(단일 최상위 요소가 없음)이 생성된 경우, 반환되는 XML의 루트 요소를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-169">If the command executed generates an XML fragment (without a single top-level element) you can specify a root element for the returning XML.</span></span> <span data-ttu-id="ce6e9-170">작업 예제는 [XSL 변환 적용 &#40;SQLXML 관리 되는 클래스&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-170">For a working sample, see [Applying an XSL Transformation &#40;SQLXML Managed Classes&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md).</span></span>  
  
 <span data-ttu-id="ce6e9-171">CommandText</span><span class="sxs-lookup"><span data-stu-id="ce6e9-171">CommandText</span></span>  
 <span data-ttu-id="ce6e9-172">명령 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-172">The text of the command.</span></span> <span data-ttu-id="ce6e9-173">이 속성은 실행할 명령의 텍스트를 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-173">This property is used for specifying the text of the command you want to execute.</span></span> <span data-ttu-id="ce6e9-174">작업 예제는 [SQL 쿼리 실행 &#40;SQLXML 관리 되는 클래스&#41;](sqlxml-4-0-net-framework-support-managed-classes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-174">For a working sample, see [Executing SQL Queries &#40;SQLXML Managed Classes&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).</span></span>  
  
 <span data-ttu-id="ce6e9-175">CommandStream</span><span class="sxs-lookup"><span data-stu-id="ce6e9-175">CommandStream</span></span>  
 <span data-ttu-id="ce6e9-176">명령 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-176">The command stream.</span></span> <span data-ttu-id="ce6e9-177">이 속성은 파일(예: XML 템플릿)에서 명령을 실행하려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-177">This property is useful if you want to execute a command from a file (for example, an XML template).</span></span> <span data-ttu-id="ce6e9-178">CommandStream을 사용 하는 경우 **"Template"**, **"UpdateGram"** 및 **"DiffGram" CommandType** 값만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-178">When you are using CommandStream, only **"Template"**, **"UpdateGram"** and **"DiffGram"CommandType** values are supported.</span></span> <span data-ttu-id="ce6e9-179">작업 예제는 [CommandStream 속성을 사용 하 여 템플릿 파일 실행](executing-template-files-by-using-the-commandstream-property.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-179">For a working sample, see [Executing Template Files by Using the CommandStream Property](executing-template-files-by-using-the-commandstream-property.md).</span></span>  
  
 <span data-ttu-id="ce6e9-180">CommandType</span><span class="sxs-lookup"><span data-stu-id="ce6e9-180">CommandType</span></span>  
 <span data-ttu-id="ce6e9-181">명령의 형식을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-181">Identifies the type of command.</span></span> <span data-ttu-id="ce6e9-182">이 속성은 실행할 명령의 형식을 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-182">This property is used for specifying the type of command you want to execute.</span></span> <span data-ttu-id="ce6e9-183">명령 형식은 다음 표에 나와 있는 값에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-183">The values in the following table determine the type of the command.</span></span> <span data-ttu-id="ce6e9-184">작업 예제는 [.Net 환경에서 SQLXML 기능에 액세스](accessing-sqlxml-functionality-in-the-net-environment.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-184">For a working sample, see [Accessing SQLXML Functionality in the .NET Environment](accessing-sqlxml-functionality-in-the-net-environment.md).</span></span>  
  
|<span data-ttu-id="ce6e9-185">값</span><span class="sxs-lookup"><span data-stu-id="ce6e9-185">Value</span></span>|<span data-ttu-id="ce6e9-186">Description</span><span class="sxs-lookup"><span data-stu-id="ce6e9-186">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ce6e9-187">SqlXmlCommandType .Sql</span><span class="sxs-lookup"><span data-stu-id="ce6e9-187">SqlXmlCommandType.Sql</span></span>|<span data-ttu-id="ce6e9-188">SQL 명령(예: `SELECT * FROM Employees FOR XML AUTO`)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-188">Executes an SQL command (for example, `SELECT * FROM Employees FOR XML AUTO`).</span></span>|  
|<span data-ttu-id="ce6e9-189">SqlXmlCommandType XPath</span><span class="sxs-lookup"><span data-stu-id="ce6e9-189">SqlXmlCommandType.XPath</span></span>|<span data-ttu-id="ce6e9-190">XPath 명령(예: `Employees[@EmployeeID=1]`)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-190">Executes an XPath command (for example, `Employees[@EmployeeID=1]`).</span></span>|  
|<span data-ttu-id="ce6e9-191">SqlXmlCommandType 템플릿</span><span class="sxs-lookup"><span data-stu-id="ce6e9-191">SqlXmlCommandType.Template</span></span>|<span data-ttu-id="ce6e9-192">XML 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-192">Executes an XML template.</span></span>|  
|<span data-ttu-id="ce6e9-193">SqlXmlCommandType 파일</span><span class="sxs-lookup"><span data-stu-id="ce6e9-193">SqlXmlCommandType.TemplateFile</span></span>|<span data-ttu-id="ce6e9-194">지정된 경로에 있는 템플릿 파일을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-194">Executes a template file at the specified path.</span></span>|  
|<span data-ttu-id="ce6e9-195">SqlXmlCommandType</span><span class="sxs-lookup"><span data-stu-id="ce6e9-195">SqlXmlCommandType.UpdateGram</span></span>|<span data-ttu-id="ce6e9-196">Updategram을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-196">Executes an updategram.</span></span>|  
|<span data-ttu-id="ce6e9-197">SqlXmlCommandType Diffgram</span><span class="sxs-lookup"><span data-stu-id="ce6e9-197">SqlXmlCommandType.Diffgram</span></span>|<span data-ttu-id="ce6e9-198">DiffGram을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6e9-198">Executes a DiffGram.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce6e9-199">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ce6e9-199">See Also</span></span>  
 <span data-ttu-id="ce6e9-200">[SqlXmlParameter 개체 &#40;SQLXML 관리 되는 클래스&#41;](sqlxml-managed-classes-sqlxmlparameter-object.md) </span><span class="sxs-lookup"><span data-stu-id="ce6e9-200">[SqlXmlParameter Object &#40;SQLXML Managed Classes&#41;](sqlxml-managed-classes-sqlxmlparameter-object.md) </span></span>  
 [<span data-ttu-id="ce6e9-201">SqlXmlAdapter 개체 &#40;SQLXML 관리 되는 클래스&#41;</span><span class="sxs-lookup"><span data-stu-id="ce6e9-201">SqlXmlAdapter Object &#40;SQLXML Managed Classes&#41;</span></span>](sqlxml-managed-classes-sqlxmladapter-object.md)  
  
  
