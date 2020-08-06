---
title: 동의어 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- synonyms [SMO]
ms.assetid: db0a9022-9549-43e5-b6b3-deb236f05fb8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5e8416dc3daea3b173fae92e5454a8a65c399e53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660976"
---
# <a name="using-synonyms"></a><span data-ttu-id="d85f5-102">동의어 사용</span><span class="sxs-lookup"><span data-stu-id="d85f5-102">Using Synonyms</span></span>
  <span data-ttu-id="d85f5-103">동의어는 스키마 범위 개체의 다른 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="d85f5-103">A synonym is an alternative name for a schema-scoped object.</span></span> <span data-ttu-id="d85f5-104">SMO에서 동의어는 <xref:Microsoft.SqlServer.Management.Smo.Synonym> 개체로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d85f5-104">In SMO, synonyms are represented by the <xref:Microsoft.SqlServer.Management.Smo.Synonym> object.</span></span> <span data-ttu-id="d85f5-105"><xref:Microsoft.SqlServer.Management.Smo.Synonym> 개체는 <xref:Microsoft.SqlServer.Management.Smo.Database> 개체의 자식입니다.</span><span class="sxs-lookup"><span data-stu-id="d85f5-105">The <xref:Microsoft.SqlServer.Management.Smo.Synonym> object is a child of the <xref:Microsoft.SqlServer.Management.Smo.Database> object.</span></span> <span data-ttu-id="d85f5-106">이는 동의어가 정의된 데이터베이스 범위 내에서만 유효함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="d85f5-106">This means that synonyms are valid only within the scope of the database in which they are defined.</span></span> <span data-ttu-id="d85f5-107">그러나 동의어가 다른 데이터베이스 또는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 원격 인스턴스의 개체를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d85f5-107">However, the synonym can refer to objects on another database, or on a remote instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d85f5-108">대체 이름이 주어지는 개체를 기준 개체라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="d85f5-108">The object that is given an alternative name is known as the base object.</span></span> <span data-ttu-id="d85f5-109"><xref:Microsoft.SqlServer.Management.Smo.Synonym> 개체의 이름 속성이 기준 개체에 부여되는 대체 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="d85f5-109">The name property of the <xref:Microsoft.SqlServer.Management.Smo.Synonym> object is the alternative name given to the base object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d85f5-110">예제</span><span class="sxs-lookup"><span data-stu-id="d85f5-110">Example</span></span>  
 <span data-ttu-id="d85f5-111">다음 코드 예제를 사용하려면 애플리케이션을 만들 프로그래밍 환경, 프로그래밍 템플릿 및 프로그래밍 언어를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d85f5-111">For the following code example, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="d85f5-112">자세한 내용은 visual studio [.net에서 VISUAL BASIC SMO 프로젝트 만들기](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) 및 visual [Studio .Net에서 VISUAL C&#35; smo 프로젝트 만들기](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d85f5-112">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-a-synonym-in-visual-basic"></a><span data-ttu-id="d85f5-113">Visual Basic에서 동의어 만들기</span><span class="sxs-lookup"><span data-stu-id="d85f5-113">Creating a Synonym in Visual Basic</span></span>  
 <span data-ttu-id="d85f5-114">코드 예제는 스키마 범위 개체에 대한 동의어 또는 대체 이름을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d85f5-114">The code example shows how to create a synonym or an alternate name for a schema scoped object.</span></span> <span data-ttu-id="d85f5-115">클라이언트 애플리케이션에서 기준 개체를 참조하기 위해 여러 부분으로 된 이름을 사용하는 대신 동의어를 통해 기준 개체의 단일 참조를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d85f5-115">Client applications can use a single reference for the base object via a synonym instead of using a multiple part name to reference the base object.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBSynonyms1](SMO How to#SMO_VBSynonyms1)]  -->  
  
## <a name="creating-a-synonym-in-visual-c"></a><span data-ttu-id="d85f5-116">Visual C#에서 동의어 만들기</span><span class="sxs-lookup"><span data-stu-id="d85f5-116">Creating a Synonym in Visual C#</span></span>  
 <span data-ttu-id="d85f5-117">코드 예제는 스키마 범위 개체에 대한 동의어 또는 대체 이름을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d85f5-117">The code example shows how to create a synonym or an alternate name for a schema scoped object.</span></span> <span data-ttu-id="d85f5-118">클라이언트 애플리케이션에서 기준 개체를 참조하기 위해 여러 부분으로 된 이름을 사용하는 대신 동의어를 통해 기준 개체의 단일 참조를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d85f5-118">Client applications can use a single reference for the base object via a synonym instead of using a multiple part name to reference the base object.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
  
            //Reference the AdventureWorks2012 database.   
            Database db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Synonym object variable by supplying the   
            //parent database, name, and schema arguments in the constructor.   
            //The name is also a synonym of the name of the base object.   
            Synonym syn = new Synonym(db, "Shop", "Sales");  
  
            //Specify the base object, which is the object on which   
            //the synonym is based.   
            syn.BaseDatabase = "AdventureWorks2012";  
            syn.BaseSchema = "Sales";  
            syn.BaseObject = "Store";  
            syn.BaseServer = srv.Name;  
  
            //Create the synonym on the instance of SQL Server.   
            syn.Create();  
        }  
```  
  
## <a name="creating-a-synonym-in-powershell"></a><span data-ttu-id="d85f5-119">PowerShell에서 동의어 만들기</span><span class="sxs-lookup"><span data-stu-id="d85f5-119">Creating a Synonym in PowerShell</span></span>  
 <span data-ttu-id="d85f5-120">코드 예제는 스키마 범위 개체에 대한 동의어 또는 대체 이름을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d85f5-120">The code example shows how to create a synonym or an alternate name for a schema scoped object.</span></span> <span data-ttu-id="d85f5-121">클라이언트 애플리케이션에서 기준 개체를 참조하기 위해 여러 부분으로 된 이름을 사용하는 대신 동의어를 통해 기준 개체의 단일 참조를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d85f5-121">Client applications can use a single reference for the base object via a synonym instead of using a multiple part name to reference the base object.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#And the database object corresponding to Adventureworks  
$db = $srv.Databases["AdventureWorks2012"]  
  
$syn = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Synonym -ArgumentList $db, "Shop", "Sales"  
  
#Specify the base object, which is the object on which the synonym is based.  
$syn.BaseDatabase = "AdventureWorks2012"  
$syn.BaseSchema = "Sales"  
$syn.BaseObject = "Store"  
$syn.BaseServer = $srv.Name  
  
#Create the synonym on the instance of SQL Server.  
$syn.Create()  
```  
  
## <a name="see-also"></a><span data-ttu-id="d85f5-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d85f5-122">See Also</span></span>  
 [<span data-ttu-id="d85f5-123">CREATE SYNONYM &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d85f5-123">CREATE SYNONYM &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-synonym-transact-sql)  
