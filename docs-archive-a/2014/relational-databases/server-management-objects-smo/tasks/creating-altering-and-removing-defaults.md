---
title: 기본값 생성, 변경 및 제거 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- defaults [SMO]
ms.assetid: c30ac3b9-8150-4264-ba4c-c549f44261ab
author: stevestein
ms.author: sstein
ms.openlocfilehash: 747f7ff60122c5265cd68060063946a3e22d0301
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739645"
---
# <a name="creating-altering-and-removing-defaults"></a><span data-ttu-id="0652d-102">기본값 생성, 변경 및 제거</span><span class="sxs-lookup"><span data-stu-id="0652d-102">Creating, Altering, and Removing Defaults</span></span>
  <span data-ttu-id="0652d-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects(SMO)에서 기본 제약 조건은 <xref:Microsoft.SqlServer.Management.Smo.Default> 개체로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0652d-103">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO), the default constraint is represented by the <xref:Microsoft.SqlServer.Management.Smo.Default> object.</span></span>  
  
 <span data-ttu-id="0652d-104"><xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> 개체의 <xref:Microsoft.SqlServer.Management.Smo.Default> 속성은 삽입할 값을 설정하는 데 사용되며,</span><span class="sxs-lookup"><span data-stu-id="0652d-104">The <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Default> object is used to set the value to be inserted.</span></span> <span data-ttu-id="0652d-105">상수 또는 상수 값을 반환하는 GETDATE()와 같은 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0652d-105">This can be a constant or a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement that returns a constant value, such as GETDATE().</span></span> <span data-ttu-id="0652d-106"><xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> 속성은 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> 메서드로 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0652d-106">The <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> property cannot be modified by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> method.</span></span> <span data-ttu-id="0652d-107">대신 <xref:Microsoft.SqlServer.Management.Smo.Default> 개체를 삭제하고 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0652d-107">Instead, the <xref:Microsoft.SqlServer.Management.Smo.Default> object must be dropped and re-created.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0652d-108">예제</span><span class="sxs-lookup"><span data-stu-id="0652d-108">Example</span></span>  
 <span data-ttu-id="0652d-109">제공된 코드 예제를 사용하려면 애플리케이션을 만들 프로그래밍 환경, 프로그래밍 템플릿 및 프로그래밍 언어를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0652d-109">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="0652d-110">자세한 내용은 visual [studio .net에서 VISUAL BASIC SMO 프로젝트 만들기](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) 또는 [visual Studio .Net에서 VISUAL C&#35; smo 프로젝트 만들기](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0652d-110">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-altering-and-removing-a-default-in-visual-basic"></a><span data-ttu-id="0652d-111">Visual Basic에서 기본값 생성, 변경 및 제거</span><span class="sxs-lookup"><span data-stu-id="0652d-111">Creating, Altering, and Removing a Default in Visual Basic</span></span>  
 <span data-ttu-id="0652d-112">이 코드 예제는 기본값을 하나는 단순 텍스트로 만들고 다른 하나는 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문으로 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0652d-112">This code example shows how to create one default that is simple text, and another default that is a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="0652d-113">기본값은 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> 메서드를 사용하여 열에 연결하고 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> 메서드를 사용하여 분리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0652d-113">The default must be attached to the column by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> method and detached by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> method.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDefaults1](SMO How to#SMO_VBDefaults1)]  -->  
  
## <a name="creating-altering-and-removing-a-default-in-visual-c"></a><span data-ttu-id="0652d-114">Visual C#에서 기본값 생성, 변경 및 제거</span><span class="sxs-lookup"><span data-stu-id="0652d-114">Creating, Altering, and Removing a Default in Visual C#</span></span>  
 <span data-ttu-id="0652d-115">이 코드 예제는 기본값을 하나는 단순 텍스트로 만들고 다른 하나는 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문으로 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0652d-115">This code example shows how to create one default that is simple text, and another default that is a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="0652d-116">기본값은 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> 메서드를 사용하여 열에 연결하고 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> 메서드를 사용하여 분리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0652d-116">The default must be attached to the column by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> method and detached by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> method.</span></span>  
  
```csharp
{
          Server srv = new Server();  
  
            //Reference the AdventureWorks2012 database.   
            Database  db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Default object variable by supplying the parent database and the default name   
            //in the constructor.   
            Default def = new Default(db, "Test_Default2");  
  
            //Set the TextHeader and TextBody properties that define the default.   
            def.TextHeader = "CREATE DEFAULT [Test_Default2] AS";  
            def.TextBody = "GetDate()";  
  
            //Create the default on the instance of SQL Server.   
            def.Create();  
  
            //Bind the default to a column in a table in AdventureWorks2012  
            def.BindToColumn("SpecialOffer", "StartDate", "Sales");  
  
            //Unbind the default from the column and remove it from the database.   
            def.UnbindFromColumn("SpecialOffer", "StartDate", "Sales");  
            def.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-default-in-powershell"></a><span data-ttu-id="0652d-117">PowerShell에서 기본값 생성, 변경 및 제거</span><span class="sxs-lookup"><span data-stu-id="0652d-117">Creating, Altering, and Removing a Default in PowerShell</span></span>  
 <span data-ttu-id="0652d-118">이 코드 예제는 기본값을 하나는 단순 텍스트로 만들고 다른 하나는 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문으로 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0652d-118">This code example shows how to create one default that is simple text, and another default that is a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="0652d-119">기본값은 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> 메서드를 사용하여 열에 연결하고 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> 메서드를 사용하여 분리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0652d-119">The default must be attached to the column by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> method and detached by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> method.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
#Define a Default object variable by supplying the parent database and the default name in the constructor.  
$def = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Default `  
-argumentlist $db, "Test_Default2"  
  
#Set the TextHeader and TextBody properties that define the default.   
$def.TextHeader = "CREATE DEFAULT [Test_Default2] AS"  
$def.TextBody = "GetDate()"  
  
#Create the default on the instance of SQL Server.   
$def.Create()  
  
#Bind the default to the column.   
$def.BindToColumn("SpecialOffer", "StartDate", "Sales")  
  
#Unbind the default from the column and remove it from the database.   
$def.UnbindFromColumn("SpecialOffer", "StartDate", "Sales")  
$def.Drop()  
```  
  
## <a name="see-also"></a><span data-ttu-id="0652d-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0652d-120">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Default>  
