---
title: Invoke-PolicyEvaluation cmdlet | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, Invoke-PolicyEvaluation
- Policy-Based Management, PowerShell
- Invoke-PolicyEvaluation cmdlet
- Cmdlets [SQL Server], Invoke-PolicyEvaluation
- PowerShell [SQL Server], Invoke-PolicyEvaluation
ms.assetid: 3e6d4f5a-59b7-4203-b95a-f7e692c0f131
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 656fdffea191c9cf6fc42d860164bc5af1e04561
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730880"
---
# <a name="invoke-policyevaluation-cmdlet"></a><span data-ttu-id="e1ffb-102">Invoke-PolicyEvaluation cmdlet</span><span class="sxs-lookup"><span data-stu-id="e1ffb-102">Invoke-PolicyEvaluation cmdlet</span></span>
  <span data-ttu-id="e1ffb-103">**Invoke-PolicyEvaluation** 은 SQL Server 개체의 대상 집합이 하나 이상의 정책 기반 관리 정책에 지정된 조건을 준수하는지 여부를 보고하는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-103">**Invoke-PolicyEvaluation** is a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlet that reports whether a target set of SQL Server objects complies with the conditions specified in one or more Policy-Based Management policies.</span></span>  
  
## <a name="using-invoke-policyevaluation"></a><span data-ttu-id="e1ffb-104">Invoke-PolicyEvaluation 사용</span><span class="sxs-lookup"><span data-stu-id="e1ffb-104">Using Invoke-PolicyEvaluation</span></span>  
 <span data-ttu-id="e1ffb-105">**Invoke-PolicyEvaluation** 은 대상 집합이라는 SQL Server 개체 집합에 대해 하나 이상의 정책을 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-105">**Invoke-PolicyEvaluation** evaluates one or more policies against a set of SQL Server objects called the target set.</span></span> <span data-ttu-id="e1ffb-106">대상 개체 집합은 대상 서버에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-106">The set of target objects comes from a target server.</span></span> <span data-ttu-id="e1ffb-107">각 정책은 대상 개체의 허용 상태인 조건을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-107">Each policy defines conditions, which are the allowed states for the target objects.</span></span> <span data-ttu-id="e1ffb-108">예를 들어 **Trustworthy Database** 정책은 TRUSTWORTHY 데이터베이스 속성을 OFF로 설정해야 한다고 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-108">For example, the **Trustworthy Database** policy states that the TRUSTWORTHY database property must be set to OFF.</span></span>  
  
 <span data-ttu-id="e1ffb-109">**-AdHocPolicyEvaluationMode** 매개 변수는 수행할 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-109">The **-AdHocPolicyEvaluationMode** parameter specifies the actions taken:</span></span>  
  
 <span data-ttu-id="e1ffb-110">확인</span><span class="sxs-lookup"><span data-stu-id="e1ffb-110">Check</span></span>  
 <span data-ttu-id="e1ffb-111">현재 로그인의 자격 증명을 사용하여 대상 개체의 준수 상태를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-111">Report the compliance status of the target objects using the credentials of your current login.</span></span> <span data-ttu-id="e1ffb-112">개체를 다시 구성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-112">Do no reconfigure any objects.</span></span> <span data-ttu-id="e1ffb-113">이 값은 기본 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-113">This is the default setting.</span></span>  
  
 <span data-ttu-id="e1ffb-114">CheckSqlScriptAsProxy</span><span class="sxs-lookup"><span data-stu-id="e1ffb-114">CheckSqlScriptAsProxy</span></span>  
 <span data-ttu-id="e1ffb-115">**##MS_PolicyTSQLExecutionLogin##** 프록시 로그인의 자격 증명을 사용하여 대상 개체의 준수 상태를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-115">Report the compliance status of the target objects using the credentials of the **##MS_PolicyTSQLExecutionLogin##** proxy login.</span></span> <span data-ttu-id="e1ffb-116">개체를 다시 구성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-116">Do no reconfigure any objects.</span></span>  
  
 <span data-ttu-id="e1ffb-117">구성</span><span class="sxs-lookup"><span data-stu-id="e1ffb-117">Configure</span></span>  
 <span data-ttu-id="e1ffb-118">현재 로그인의 자격 증명을 사용하여 대상 개체의 준수 상태를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-118">Report the compliance status of the target objects using the credentials of your current login.</span></span> <span data-ttu-id="e1ffb-119">정책을 준수하지 않는 설정할 수 있는 모든 결정적 옵션을 다시 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-119">Reconfigure any settable and deterministic options that are not in compliance with the policies.</span></span>  
  
## <a name="specifying-polices"></a><span data-ttu-id="e1ffb-120">정책 지정</span><span class="sxs-lookup"><span data-stu-id="e1ffb-120">Specifying Polices</span></span>  
 <span data-ttu-id="e1ffb-121">정책을 지정하는 방법은 정책 저장 위치에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-121">How you specify a policy depends on where the policy is stored.</span></span> <span data-ttu-id="e1ffb-122">정책은 다음 두 가지 형식으로 저장될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-122">Policies can be stored in two formats:</span></span>  
  
-   <span data-ttu-id="e1ffb-123">정책은 데이터베이스 엔진 인스턴스와 같은 정책 저장소에 저장되는 개체일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-123">They can be objects stored in a policy store, such as an instance of the Database Engine.</span></span> <span data-ttu-id="e1ffb-124">SQLSERVER:\SQLPolicy 폴더를 사용하여 정책 저장소에서 정책 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-124">You can use the SQLSERVER:\SQLPolicy folder to specify the location of policies in a policy store.</span></span> <span data-ttu-id="e1ffb-125">Where-Object를 사용하여 정책 범주에 대해 필터링하거나 Get-Item을 사용하여 정책 이름에 대해 필터링하는 경우와 같이 Windows PowerShell cmdlet을 사용하여 해당 속성을 기반으로 입력 정책을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-125">You can use Windows PowerShell cmdlets to filter the input polices based on their properties, such as using Where-Object to filter on the policy category or Get-Item to filter on policy name.</span></span>  
  
-   <span data-ttu-id="e1ffb-126">정책을 XML 파일로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-126">They can be exported as XML files.</span></span> <span data-ttu-id="e1ffb-127">D:와 같은 파일 시스템 드라이브를 사용하여 XML 파일의 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-127">You can use a file system drive, such as D:, to specify the location of the XML files.</span></span> <span data-ttu-id="e1ffb-128">Where-Object와 같은 Windows PowerShell cmdlet을 사용하여 파일 이름과 같은 해당 파일 속성을 기반으로 정책을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-128">You can use Windows PowerShell cmdlets such as Where-Object to filter the policies on their file properties, such as file name.</span></span>  
  
 <span data-ttu-id="e1ffb-129">정책이 정책 저장소에 저장되는 경우 평가할 정책을 가리키는 PSObjects 집합을 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-129">If the policies are stored in a policy store, you must pass in a set of PSObjects pointing to the policies to be evaluated.</span></span> <span data-ttu-id="e1ffb-130">이는 일반적으로 Get-Item과 같은 cmdlet의 출력을 **Invoke-PolicyEvaluation**으로 파이프하여 수행되며 **-Policy** 매개 변수를 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-130">This is typically done by piping the output of a cmdlet such as Get-Item to **Invoke-PolicyEvaluation**, and does not require that you specify the **-Policy** parameter.</span></span> <span data-ttu-id="e1ffb-131">예를 들어 Microsoft Best Practices 정책을 데이터베이스 엔진 인스턴스로 가져온 경우 이 명령은 **데이터베이스 상태** 정책을 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-131">For example, if you have imported the Microsoft Best Practices policies into your instance of the database engine, this command evaluates the **Database Status** policy:</span></span>  
  
```powershell
sl "SQLSERVER:\SQLPolicy\MyComputer\DEFAULT\Policies"  
Get-Item "Database Status" | Invoke-PolicyEvaluation -TargetServerName "MYCOMPUTER"  
```  
  
 <span data-ttu-id="e1ffb-132">이 예에서는 Where-Object를 사용하여 정책 저장소의 여러 정책을 해당 **PolicyCategory** 속성을 기반으로 필터링하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-132">This example shows using Where-Object to filter multiple policies from a policy store based on their **PolicyCategory** property.</span></span> <span data-ttu-id="e1ffb-133">**Where-Object** 의 파이프된 출력에서 가져온 개체가 **Invoke-PolicyEvaluation**에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-133">The objects from the piped output of **Where-Object** is consumed by **Invoke-PolicyEvaluation**.</span></span>  
  
```powershell
sl "SQLSERVER:\SQLPolicy\MyComputer\DEFAULT\Policies"  
gci | Where-Object {$_.PolicyCategory -eq "Microsoft Best Practices: Maintenance"} | Invoke-PolicyEvaluation -TargetServer "MYCOMPUTER"  
```  
  
 <span data-ttu-id="e1ffb-134">정책이 XML 파일로 저장되는 경우 **-Policy** 매개 변수를 사용하여 각 정책의 경로와 이름을 모두 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-134">If the policies are stored as XML files, you must use the **-Policy** parameter to supply both the path and name for each policy.</span></span> <span data-ttu-id="e1ffb-135">**-Policy** 매개 변수에 경로를 지정하지 않으면 **Invoke-PolicyEvaulation** 에서 **sqlps** 경로의 현재 설정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-135">If you do not specify a path in the **-Policy** parameter, **Invoke-PolicyEvaulation** uses the current setting of the **sqlps** path.</span></span> <span data-ttu-id="e1ffb-136">예를 들어 이 명령은 SQL Server와 함께 설치된 Microsoft Best Practice 정책 중 하나를 로그인의 기본 데이터베이스에 대해 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-136">For example, this command evaluates one of the Microsoft Best Practice policies installed with SQL Server against the default database for your login:</span></span>  
  
```powershell
Invoke-PolicyEvaluation -Policy "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033\Database Status.xml" -TargetServerName "MYCOMPUTER"  
```  
  
 <span data-ttu-id="e1ffb-137">이 명령은 동일한 작업을 수행하며 현재 **sqlps** 경로만 사용하여 정책 XML 파일의 위치를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-137">This command does the same thing, only it uses the current **sqlps** path to establish the location of the policy XML file:</span></span>  
  
```powershell
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033"  
Invoke-PolicyEvaluation -Policy "Database Status.xml" -TargetServerName "MYCOMPUTER"  
```  
  
 <span data-ttu-id="e1ffb-138">이 예에서는 **Get-ChildItem** cmdlet을 사용하여 여러 정책 XML 파일을 검색하고 개체를 **Invoke-PolicyEvaluation**으로 파이프하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-138">This example shows using the **Get-ChildItem** cmdlet to retrieve multiple policy XML files and pipe the objects into **Invoke-PolicyEvaluation**:</span></span>  
  
```powershell
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033"  
gci "Database Status.xml", "Trustworthy Database.xml" | Invoke-PolicyEvaluation -TargetServer "MYCOMPUTER"  
```  
  
## <a name="specifying-the-target-set"></a><span data-ttu-id="e1ffb-139">대상 집합 지정</span><span class="sxs-lookup"><span data-stu-id="e1ffb-139">Specifying the Target Set</span></span>  
 <span data-ttu-id="e1ffb-140">다음 3개의 매개 변수를 사용하여 대상 개체 집합을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-140">Use three parameters to specify the set of target objects:</span></span>  
  
-   <span data-ttu-id="e1ffb-141">**-TargetServerName** 은 대상 개체를 포함하는 SQL Server 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-141">**-TargetServerName** specifies the instance of SQL Server containing the target objects.</span></span> <span data-ttu-id="e1ffb-142">정보를 <xref:System.Data.SqlClient.SqlConnection> 클래스의 ConnectionString 속성에 대해 정의된 형식을 사용하는 문자열에 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-142">You can specify the information in a string that uses the format defined for the ConnectionString property of the <xref:System.Data.SqlClient.SqlConnection> class.</span></span> <span data-ttu-id="e1ffb-143"><xref:System.Data.SqlClient.SqlConnectionStringBuilder> 클래스를 사용하여 올바른 형식의 연결 문자열을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-143">You can use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> class to build a correctly formatted connection string.</span></span> <span data-ttu-id="e1ffb-144"><xref:Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection> 개체를 만든 다음 **-TargetServer**에 전달해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-144">You can also create a <xref:Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection> object and pass it to **-TargetServer**.</span></span> <span data-ttu-id="e1ffb-145">서버 이름만 포함하는 문자열을 제공하는 경우 **Invoke-PolicyEvaluation** 에서는 Windows 인증을 사용하여 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-145">If you supply a string that has only the name of the server, **Invoke-PolicyEvaluation** uses Windows Authentication to connect to the server.</span></span>  
  
-   <span data-ttu-id="e1ffb-146">**-TargetObjects** 는 대상 집합의 SQL Server 개체를 나타내는 개체 배열 또는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-146">**-TargetObjects** takes an object or array of objects that represent the SQL Server objects in the target set.</span></span> <span data-ttu-id="e1ffb-147">예를 들어 <xref:Microsoft.SqlServer.Management.Smo.Database> 클래스 개체의 배열을 만들어 **-TargetObjects**에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-147">For example, you could create an array of <xref:Microsoft.SqlServer.Management.Smo.Database> class objects to pass in to **-TargetObjects**.</span></span>  
  
-   <span data-ttu-id="e1ffb-148">**-TargetExpressions** 는 대상 집합의 개체를 지정하는 쿼리 식을 포함하는 문자열을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-148">**-TargetExpressions** takes a string containing a query expression that specifies the objects in the target set.</span></span> <span data-ttu-id="e1ffb-149">쿼리 식은 '/' 문자로 구분된 노드 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-149">The query expression is in the form of nodes separated by the '/' character.</span></span> <span data-ttu-id="e1ffb-150">각 노드의 형식은 ObjectType[Filter]입니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-150">Each node is in the form ObjectType[Filter].</span></span> <span data-ttu-id="e1ffb-151">개체 유형은 SMO (SQL Server Management Object) 개체 계층의 개체 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-151">Object type is one of the objects in a SQL Server Management Object (SMO) object hierarchy.</span></span> <span data-ttu-id="e1ffb-152">필터는 해당 노드에 있는 개체에 대해 필터링하는 식입니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-152">Filter is an expression that filters for objects at that node.</span></span> <span data-ttu-id="e1ffb-153">자세한 내용은 [Query Expressions and Uniform Resource Names](../powershell/query-expressions-and-uniform-resource-names.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-153">For more information, see [Query Expressions and Uniform Resource Names](../powershell/query-expressions-and-uniform-resource-names.md).</span></span>  
  
 <span data-ttu-id="e1ffb-154">**-TargetObjects** 또는 **-TargetExpression**중에서 하나만 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-154">Specify either **-TargetObjects** or **-TargetExpression**, not both.</span></span>  
  
 <span data-ttu-id="e1ffb-155">이 예에서는 Sfc.SqlStoreConnection 개체를 사용하여 대상 서버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-155">This example uses an Sfc.SqlStoreConnection object to specify the target server:</span></span>  
  
```powershell
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033"  
$conn = New-Object Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection("server='MYCOMPUTER';Trusted_Connection=True")  
Invoke-PolicyEvaluation -Policy "Database Status.xml" -TargetServerName $conn  
```  
  
 <span data-ttu-id="e1ffb-156">이 예에서는 **-TargetExpression** 을 사용하여 평가할 특정 데이터베이스를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-156">This example uses **-TargetExpression** to identify the specific database to evaluate:</span></span>  
  
```powershell
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033"  
Invoke-PolicyEvaluation -Policy "Database Status.xml" -TargetServerName "MyComputer" -TargetExpression "Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012']"  
```  
  
## <a name="evaluating-analysis-services-policies"></a><span data-ttu-id="e1ffb-157">Analysis Services 정책 평가</span><span class="sxs-lookup"><span data-stu-id="e1ffb-157">Evaluating Analysis Services Policies</span></span>  
 <span data-ttu-id="e1ffb-158">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스에 대해 정책을 평가하려면 어셈블리를 로드하여 PowerShell에 등록하고, Analysis Services 연결 개체를 사용하여 변수를 만들고, 변수를 **-TargetObject** 매개 변수에 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-158">To evaluate policies against an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], you must load and register an assembly into PowerShell, create a variable with an Analysis Services connection object, and pass the variable to the **-TargetObject** parameter.</span></span> <span data-ttu-id="e1ffb-159">이 예에서는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에 대한 최선의 구현 방법 노출 영역 구성 정책을 평가하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-159">This example shows evaluating the Best Practices surface area configuration policy for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]:</span></span>  
  
```powershell
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\AnalysisServices\1033"  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.AnalysisServices")  
$SSASsvr = New-Object Microsoft.AnalysisServices.Server  
$SSASsvr.Connect("Data Source=Localhost")  
Invoke-PolicyEvaluation -Policy "Surface Area Configuration for Analysis Services Features.xml" -TargetObject $SSASsvr  
```  
  
## <a name="evaluating-reporting-services-policies"></a><span data-ttu-id="e1ffb-160">Reporting Services 정책 평가</span><span class="sxs-lookup"><span data-stu-id="e1ffb-160">Evaluating Reporting Services Policies</span></span>  
 <span data-ttu-id="e1ffb-161">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 정책을 평가하려면 어셈블리를 로드하여 PowerShell에 등록하고, [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 연결 개체를 사용하여 변수를 만들고, 변수를 **-TargetObject** 매개 변수에 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-161">To evaluate [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] policies, you must load and register an assembly into PowerShell, create a variable with a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] connection object, and pass the variable to the **-TargetObject** parameter.</span></span> <span data-ttu-id="e1ffb-162">이 예에서는 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]에 대한 최선의 구현 방법 노출 영역 구성 정책을 평가하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-162">This example shows evaluating the Best Practices surface area configuration policy for [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]:</span></span>  
  
```powershell
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\ReportingServices\1033"  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.Dmf.Adapters")  
$SSRSsvr = new-object Microsoft.SqlServer.Management.Adapters.RSContainer('MyComputer')  
Invoke-PolicyEvaluation -Policy "Surface Area Configuration for Reporting Services 2008 Features.xml" -TargetObject $SSRSsvr  
```  
  
## <a name="formatting-output"></a><span data-ttu-id="e1ffb-163">출력의 형식 지정</span><span class="sxs-lookup"><span data-stu-id="e1ffb-163">Formatting Output</span></span>  
 <span data-ttu-id="e1ffb-164">기본적으로 **Invoke-PolicyEvaluation** 출력은 사람이 읽을 수 있는 형식의 간략한 보고서로 명령 프롬프트 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-164">By default, the output of **Invoke-PolicyEvaluation** is displayed in the command prompt window as a concise report in human-readable format.</span></span> <span data-ttu-id="e1ffb-165">**-OutputXML** 매개 변수를 사용하여 cmdlet에서 대신 XML 파일 형식의 세부 보고서를 생성하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-165">You can use the **-OutputXML** parameter to specify that the cmdlet instead produce a detailed report as an XML file.</span></span> <span data-ttu-id="e1ffb-166">**Invoke-PolicyEvaluation** 은 SML-IF 판독기에서 파일을 읽을 수 있도록 SML-IF(Systems Modeling Language Interchange Format) 스키마를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-166">**Invoke-PolicyEvaluation** uses the Systems Modeling Language Interchange Format (SML-IF) schema so the file can be read by SML-IF readers.</span></span>  
  
```powershell
sl "SQLSERVER:\SQLPolicy\MyComputer\DEFAULT\Policies"  
Invoke-PolicyEvaluation -Policy "Datbase Status" -TargetServer "MYCOMPUTER" -OutputXML > C:\MyReports\DatabaseStatusReport.xml  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1ffb-167">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e1ffb-167">See Also</span></span>  
 [<span data-ttu-id="e1ffb-168">데이터베이스 엔진 cmdlet 사용</span><span class="sxs-lookup"><span data-stu-id="e1ffb-168">Use the Database Engine cmdlets</span></span>](../../2014/database-engine/use-the-database-engine-cmdlets.md)  
