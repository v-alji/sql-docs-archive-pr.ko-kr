---
title: 규칙 생성, 변경 및 제거 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- rules [SMO]
ms.assetid: 16981459-524e-4b39-a899-4370eaf763cc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7742a9cb718bdde4f268d5226c45eba475f44ddd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653253"
---
# <a name="creating-altering-and-removing-rules"></a><span data-ttu-id="c555c-102">규칙 생성, 변경 및 제거</span><span class="sxs-lookup"><span data-stu-id="c555c-102">Creating, Altering, and Removing Rules</span></span>
  <span data-ttu-id="c555c-103">SMO에서 규칙은 <xref:Microsoft.SqlServer.Management.Smo.Rule> 개체로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c555c-103">In SMO, rules are represented by the <xref:Microsoft.SqlServer.Management.Smo.Rule> object.</span></span> <span data-ttu-id="c555c-104">규칙은 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> 속성, 즉 IN, LIKE, BETWEEN과 같은 연산자나 조건자를 사용하는 조건식이 포함된 텍스트 문자열로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c555c-104">The rule is defined by the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> property, which is a text string that contains a condition expression that uses operators or predicates, such as IN, LIKE, or BETWEEN.</span></span> <span data-ttu-id="c555c-105">규칙은 열 또는 기타 데이터베이스 개체를 참조할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c555c-105">A rule cannot reference columns or other database objects.</span></span> <span data-ttu-id="c555c-106">데이터베이스 개체를 참조하지 않는 기본 제공 함수는 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c555c-106">Built-in functions that do not reference database objects can be included.</span></span>  
  
 <span data-ttu-id="c555c-107"><xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> 속성 정의에는 입력한 데이터 값을 참조하는 변수가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c555c-107">The definition in the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> property must contain a variable that refers to the data value entered.</span></span> <span data-ttu-id="c555c-108">규칙을 만들 때 모든 이름 또는 기호를 사용 하 여 값을 나타낼 수 있지만 첫 번째 문자는 기호 여야 합니다 \@ .</span><span class="sxs-lookup"><span data-stu-id="c555c-108">Any name or symbol can be used to represent the value when creating the rule, but the first character must be the \@ symbol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c555c-109">예제</span><span class="sxs-lookup"><span data-stu-id="c555c-109">Example</span></span>  
 <span data-ttu-id="c555c-110">제공된 코드 예제를 사용하려면 애플리케이션을 만들 프로그래밍 환경, 프로그래밍 템플릿 및 프로그래밍 언어를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c555c-110">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="c555c-111">자세한 내용은 visual [studio .net에서 VISUAL BASIC SMO 프로젝트 만들기](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) 또는 [visual Studio .Net에서 VISUAL C&#35; smo 프로젝트 만들기](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c555c-111">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-altering-and-removing-a-rule-in-visual-basic"></a><span data-ttu-id="c555c-112">Visual Basic에서 규칙 생성, 변경 및 제거</span><span class="sxs-lookup"><span data-stu-id="c555c-112">Creating, Altering, and Removing a Rule in Visual Basic</span></span>  
 <span data-ttu-id="c555c-113">이 코드 예제는 규칙을 만들고, 규칙을 열에 연결하고, <xref:Microsoft.SqlServer.Management.Smo.Rule> 개체의 속성을 수정하고, 열에서 규칙을 분리하고, 규칙을 삭제하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c555c-113">This code sample shows how to create a rule, attach it to a column, modify properties of the <xref:Microsoft.SqlServer.Management.Smo.Rule> object, detach it from the column, and then drop it.</span></span>  
  
 <span data-ttu-id="c555c-114">System.Data 어셈블리의 <xref:Microsoft.SqlServer.Management.Smo.Rule> 개체와 혼동을 피하기 위해 이 <xref:Microsoft.SqlServer.Management.Smo.Rule> 개체의 `Dim` 문은 전체 어셈블리 경로로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c555c-114">The `Dim` statement for the <xref:Microsoft.SqlServer.Management.Smo.Rule> object is specified with the full assembly path to avoid ambiguity with a <xref:Microsoft.SqlServer.Management.Smo.Rule> object in the System.Data assembly.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBRules1](SMO How to#SMO_VBRules1)]  -->  
  
## <a name="creating-altering-and-removing-a-rule-in-visual-c"></a><span data-ttu-id="c555c-115">Visual C#에서 규칙 생성, 변경 및 제거</span><span class="sxs-lookup"><span data-stu-id="c555c-115">Creating, Altering, and Removing a Rule in Visual C#</span></span>  
 <span data-ttu-id="c555c-116">이 코드 예제는 규칙을 만들고, 규칙을 열에 연결하고, <xref:Microsoft.SqlServer.Management.Smo.Rule> 개체의 속성을 수정하고, 열에서 규칙을 분리하고, 규칙을 삭제하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c555c-116">This code sample shows how to create a rule, attach it to a column, modify properties of the <xref:Microsoft.SqlServer.Management.Smo.Rule> object, detach it from the column, and then drop it.</span></span>  
  
 <span data-ttu-id="c555c-117">System.Data 어셈블리의 <xref:Microsoft.SqlServer.Management.Smo.Rule> 개체와 혼동을 피하기 위해 이 <xref:Microsoft.SqlServer.Management.Smo.Rule> 개체의 `Dim` 문은 전체 어셈블리 경로로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c555c-117">The `Dim` statement for the <xref:Microsoft.SqlServer.Management.Smo.Rule> object is specified with the full assembly path to avoid ambiguity with a <xref:Microsoft.SqlServer.Management.Smo.Rule> object in the System.Data assembly.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Rule object variable by supplying the parent database, name and schema in the constructor.   
            //Note that the full namespace must be given for the Rule type to differentiate it from other Rule types.   
            Microsoft.SqlServer.Management.Smo.Rule ru;  
            ru = new Rule(db, "TestRule", "Production");  
            //Set the TextHeader and TextBody properties to define the rule.   
            ru.TextHeader = "CREATE RULE [Production].[TestRule] AS";  
            ru.TextBody = "@value BETWEEN GETDATE() AND DATEADD(year,4,GETDATE())";  
            //Create the rule on the instance of SQL Server.   
            ru.Create();  
            //Bind the rule to a column in the Product table by supplying the table, schema, and   
            //column as arguments in the BindToColumn method.   
            ru.BindToColumn("Product", "SellEndDate", "Production");  
            //Unbind from the column before removing the rule from the database.   
            ru.UnbindFromColumn("Product", "SellEndDate", "Production");  
            ru.Drop();  
  
        }  
```  
  
## <a name="creating-altering-and-removing-a-rule-in-powershell"></a><span data-ttu-id="c555c-118">PowerShell에서 규칙 생성, 변경 및 제거</span><span class="sxs-lookup"><span data-stu-id="c555c-118">Creating, Altering, and Removing a Rule in PowerShell</span></span>  
 <span data-ttu-id="c555c-119">이 코드 예제는 규칙을 만들고, 규칙을 열에 연결하고, <xref:Microsoft.SqlServer.Management.Smo.Rule> 개체의 속성을 수정하고, 열에서 규칙을 분리하고, 규칙을 삭제하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c555c-119">This code sample shows how to create a rule, attach it to a column, modify properties of the <xref:Microsoft.SqlServer.Management.Smo.Rule> object, detach it from the column, and then drop it.</span></span>  
  
 <span data-ttu-id="c555c-120">System.Data 어셈블리의 <xref:Microsoft.SqlServer.Management.Smo.Rule> 개체와 혼동을 피하기 위해 이 <xref:Microsoft.SqlServer.Management.Smo.Rule> 개체의 `Dim` 문은 전체 어셈블리 경로로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c555c-120">The `Dim` statement for the <xref:Microsoft.SqlServer.Management.Smo.Rule> object is specified with the full assembly path to avoid ambiguity with a <xref:Microsoft.SqlServer.Management.Smo.Rule> object in the System.Data assembly.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
# Define a Rule object variable by supplying the parent database, name and schema in the constructor.
$ru = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Rule -argumentlist $db, "TestRule", "Production"  
  
#Set the TextHeader and TextBody properties to define the rule.
$ru.TextHeader = "CREATE RULE [Production].[TestRule] AS"  
$ru.TextBody = "@value BETWEEN GETDATE() AND DATEADD(year,4,GETDATE())"  
  
#Create the rule on the instance of SQL Server.
$ru.Create()  
  
# Bind the rule to a column in the Product table by supplying the table, schema, and column as arguments in the BindToColumn method.
$ru.BindToColumn("Product", "SellEndDate", "Production")  
  
#Unbind from the column before removing the rule from the database.
$ru.UnbindFromColumn("Product", "SellEndDate", "Production")  
$ru.Drop()  
```  
  
## <a name="see-also"></a><span data-ttu-id="c555c-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c555c-121">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Rule>  
