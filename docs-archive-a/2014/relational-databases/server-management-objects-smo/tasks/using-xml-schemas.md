---
title: XML 스키마 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- XML [SMO]
ms.assetid: 9d04de01-efeb-4b2d-8c28-3234bc7ff2f3
author: stevestein
ms.author: sstein
ms.openlocfilehash: a0e5c58bb05da7025651a4e55e29541d694ba1ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741676"
---
# <a name="using-xml-schemas"></a><span data-ttu-id="e6441-102">XML 스키마 사용</span><span class="sxs-lookup"><span data-stu-id="e6441-102">Using XML Schemas</span></span>
  <span data-ttu-id="e6441-103">SMO에서 XML 프로그래밍은 XML 데이터 형식, XML 네임스페이스 및 XML 데이터 형식 열의 단순 인덱스를 제공하는 것으로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6441-103">XML programming in SMO is limited to providing XML data types, XML namespaces, and simple indexing on XML data type columns.</span></span>  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)]<span data-ttu-id="e6441-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]는 XML 문서 인스턴스에 대 한 기본 저장소를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6441-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provides native storage for XML document instances.</span></span> <span data-ttu-id="e6441-105">XML 스키마를 사용하여 데이터 무결성 보장을 위해 XML 문서의 유효성 검사에 사용할 수 있는 복잡한 XML 데이터 형식을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6441-105">XML schemas let you define complex XML data types, which can be used to validate XML documents to ensure data integrity.</span></span> <span data-ttu-id="e6441-106">XML 스키마는 <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> 개체에 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6441-106">The XML schema is defined in the <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6441-107">예제</span><span class="sxs-lookup"><span data-stu-id="e6441-107">Example</span></span>  
 <span data-ttu-id="e6441-108">제공된 코드 예제를 사용하려면 애플리케이션을 만들 프로그래밍 환경, 프로그래밍 템플릿 및 프로그래밍 언어를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6441-108">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="e6441-109">자세한 내용은 visual [studio .net에서 VISUAL BASIC SMO 프로젝트 만들기](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) 또는 [visual Studio .Net에서 VISUAL C&#35; smo 프로젝트 만들기](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e6441-109">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-an-xml-schema-in-visual-basic"></a><span data-ttu-id="e6441-110">Visual Basic에서 XML 스키마 만들기</span><span class="sxs-lookup"><span data-stu-id="e6441-110">Creating an XML Schema in Visual Basic</span></span>  
 <span data-ttu-id="e6441-111">이 코드 예제는 <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> 개체를 사용하여 XML 스키마를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e6441-111">This code example shows how to create an XML schema by using the <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> object.</span></span> <span data-ttu-id="e6441-112">XML 스키마 컬렉션을 정의하는 <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A> 속성은 여러 개의 큰따옴표를 포함하고</span><span class="sxs-lookup"><span data-stu-id="e6441-112">The <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A> property, which defines the XML schema collection, contains several double quotation marks.</span></span> <span data-ttu-id="e6441-113">이들은 `chr(34)` 문자열로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="e6441-113">These are replaced by the `chr(34)` string.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBXMLSchema1](SMO How to#SMO_VBXMLSchema1)]  -->  
  
## <a name="creating-an-xml-schema-in-visual-c"></a><span data-ttu-id="e6441-114">Visual C#에서 XML 스키마 만들기</span><span class="sxs-lookup"><span data-stu-id="e6441-114">Creating an XML Schema in Visual C#</span></span>  
 <span data-ttu-id="e6441-115">이 코드 예제는 <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> 개체를 사용하여 XML 스키마를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e6441-115">This code example shows how to create an XML schema by using the <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> object.</span></span> <span data-ttu-id="e6441-116">XML 스키마 컬렉션을 정의하는 <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A> 속성은 여러 개의 큰따옴표를 포함하고</span><span class="sxs-lookup"><span data-stu-id="e6441-116">The <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A> property, which defines the XML schema collection, contains several double quotation marks.</span></span> <span data-ttu-id="e6441-117">이들은 `chr(34)` 문자열로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="e6441-117">These are replaced by the `chr(34)` string.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = default(Server);  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db = default(Database);  
            db = srv.Databases["AdventureWorks2012"];  
            //Define an XmlSchemaCollection object by supplying the parent  
            // database and name arguments in the constructor.   
            XmlSchemaCollection xsc = default(XmlSchemaCollection);  
            xsc = new XmlSchemaCollection(db, "MySampleCollection");  
            xsc.Text = "<schema xmlns=" + Strings.Chr(34) + "http://www.w3.org/2001/XMLSchema" + Strings.Chr(34) + " xmlns:ns=" + Strings.Chr(34) + "http://ns" + Strings.Chr(34) + "><element name=" + Strings.Chr(34) + "e" + Strings.Chr(34) + " type=" + Strings.Chr(34) + "dateTime" + Strings.Chr(34) + "/></schema>";  
            //Create the XML schema collection on the instance of SQL Server.   
            xsc.Create();  
        }  
```  
  
## <a name="creating-an-xml-schema-in-powershell"></a><span data-ttu-id="e6441-118">PowerShell에서 XML 스키마 만들기</span><span class="sxs-lookup"><span data-stu-id="e6441-118">Creating an XML Schema in PowerShell</span></span>  
 <span data-ttu-id="e6441-119">이 코드 예제는 <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> 개체를 사용하여 XML 스키마를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e6441-119">This code example shows how to create an XML schema by using the <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> object.</span></span> <span data-ttu-id="e6441-120">XML 스키마 컬렉션을 정의하는 <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A> 속성은 여러 개의 큰따옴표를 포함하고</span><span class="sxs-lookup"><span data-stu-id="e6441-120">The <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A> property, which defines the XML schema collection, contains several double quotation marks.</span></span> <span data-ttu-id="e6441-121">이들은 `chr(34)` 문자열로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="e6441-121">These are replaced by the `chr(34)` string.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance replace LocalMachine with the physical server  
cd \sql\LocalHost  
$srv = Get-Item default  
  
#Reference the AdventureWorks database.  
$db = $srv.Databases["AdventureWorks2012"]  
  
#Create a new schema collection  
$xsc = New-Object -TypeName Microsoft.SqlServer.Management.SMO.XmlSchemaCollection `  
-argumentlist $db,"MySampleCollection"  
  
#Add the xml  
$dq = '"' # the double quote character  
$xsc.Text = "<schema xmlns=" + $dq + "http://www.w3.org/2001/XMLSchema" + $dq + `  
"  xmlns:ns=" + $dq + "http://ns" + $dq + "><element name=" + $dq + "e" + $dq +`  
 " type=" + $dq + "dateTime" + $dq + "/></schema>"  
  
#Create the XML schema collection on the instance of SQL Server.  
$xsc.Create()  
```  
