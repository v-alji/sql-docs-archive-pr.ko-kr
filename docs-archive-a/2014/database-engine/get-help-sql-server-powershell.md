---
title: SQL Server PowerShell 도움말 보기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Help [PowerShell]
- Help [SQL Server], PowerShell
- PowerShell [SQL Server], help
ms.assetid: 968c316d-db83-4c24-8ea6-9f18736842f7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f1d97a3b694eebb924f9e1ff228d4d38da4f45ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732931"
---
# <a name="get-help-sql-server-powershell"></a><span data-ttu-id="40e58-102">Get Help SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="40e58-102">Get Help SQL Server PowerShell</span></span>
  <span data-ttu-id="40e58-103">Windows PowerShell의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 공급자 및 cmdlet 사용에 대한 정보를 얻을 수 있는 몇 가지 도움말이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40e58-103">There are several sources of information about using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider for Windows PowerShell and cmdlets.</span></span> <span data-ttu-id="40e58-104">여기서는 Windows PowerShell 환경에서 사용 가능한 도움말에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="40e58-104">This includes the help that is available in the Windows PowerShell environment.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="40e58-105">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="40e58-105">Before You Begin</span></span>  
 <span data-ttu-id="40e58-106">Windows PowerShell에 대한 자세한 내용은 [Windows PowerShell 시작 가이드](https://technet.microsoft.com/library/hh857337.aspx)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="40e58-106">To learn about Windows PowerShell, see [Windows PowerShell Getting Started Guide](https://technet.microsoft.com/library/hh857337.aspx).</span></span>  
  
 <span data-ttu-id="40e58-107">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlet 및 공급자에 대한 개요는 [SQL Server PowerShell](../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="40e58-107">For an overview of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlets and provider, see [SQL Server PowerShell](../powershell/sql-server-powershell.md).</span></span>  
  
### <a name="help-in-the-windows-powershell-environment"></a><span data-ttu-id="40e58-108">Windows PowerShell 환경의 도움말</span><span class="sxs-lookup"><span data-stu-id="40e58-108">Help in the Windows PowerShell Environment</span></span>  
 <span data-ttu-id="40e58-109">Windows PowerShell 환경에서 **Get-Help** cmdlet을 사용하여 도움말을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40e58-109">Use the **Get-Help** cmdlet to get help in the Windows PowerShell environment.</span></span> <span data-ttu-id="40e58-110">**Get-Help** 는 Windows PowerShell에서 제공되는 다양한 cmdlet 및 공급자와 Windows PowerShell 언어에 대한 기본적인 도움말을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="40e58-110">**Get-Help** provides basic help for the Windows PowerShell language and the various cmdlets and providers available in Windows PowerShell.</span></span>  
  
 <span data-ttu-id="40e58-111">**Get-Help**를 사용할 수 있는 방법은 [Get-Help: 도움말 보기](https://go.microsoft.com/fwlink/?LinkId=102136)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="40e58-111">For more information on the ways you can use **Get-Help**, see [Get-Help: Getting Help](https://go.microsoft.com/fwlink/?LinkId=102136).</span></span>  
  
### <a name="sql-server-powershell-provider-help"></a><span data-ttu-id="40e58-112">SQL Server PowerShell 공급자 도움말</span><span class="sxs-lookup"><span data-stu-id="40e58-112">SQL Server PowerShell Provider Help</span></span>  
 <span data-ttu-id="40e58-113">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 공급자는 SQLSERVER 가상 드라이브에서 여러 폴더(예: SQLSERVER:\SQL 및 SQLSERVER:\DAC 폴더)를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="40e58-113">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell provider implements several folders on a SQLSERVER virtual drive, such as the SQLSERVER:\SQL and SQLSERVER:\DAC folders.</span></span> <span data-ttu-id="40e58-114">각 폴더는 SQL Server 관리 효율성 개체 모델 중 하나에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="40e58-114">Each folder is associated with one of the SQL Server manageability object models.</span></span> <span data-ttu-id="40e58-115">SQL Server 경로에 각 노드에 연결된 메서드 및 속성을 나열할 수 있지만 PowerShell 환경에서 해당 메서드와 속성에 대한 도움말을 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="40e58-115">While you can list the methods and properties associated with each node in a SQL Server path, you cannot get help for them in the PowerShell environment.</span></span> <span data-ttu-id="40e58-116">연결된 프로그래밍 참조에 대한 링크를 제공하는 폴더 테이블은 [SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="40e58-116">For a table of the folders with links to the associated programming reference, see [SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md).</span></span>  
  
### <a name="invoke-sqlcmd-help"></a><span data-ttu-id="40e58-117">Invoke-Sqlcmd 도움말</span><span class="sxs-lookup"><span data-stu-id="40e58-117">Invoke-Sqlcmd Help</span></span>  
 <span data-ttu-id="40e58-118">**Invoke-Sqlcmd** cmdlet은 **sqlcmd** 유틸리티를 통해 실행할 수 있는 모든 쿼리 또는 스크립트 파일을 입력으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="40e58-118">The **Invoke-Sqlcmd** cmdlet takes as input any query or script file that can be run by the **sqlcmd** utility.</span></span> <span data-ttu-id="40e58-119">**Get-Help** 를 사용하면 **Invoke-Sqlcmd** 및 해당 매개 변수에 대한 정보는 확인할 수 있지만, **Get-Help** 를 통해 **sqlcmd** 쿼리에 대한 정보를 확인할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="40e58-119">You can use **Get-Help** to get information about **Invoke-Sqlcmd** and its parameters, but there is no **Get-Help** coverage for the **sqlcmd** queries.</span></span>  
  
 <span data-ttu-id="40e58-120">*-Query* 또는 *-QueryFromFile* 입력에는 다음이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40e58-120">The *-Query* or *-QueryFromFile* input can contain:</span></span>  
  
-   <span data-ttu-id="40e58-121">**sqlcmd** 변수 및 명령.</span><span class="sxs-lookup"><span data-stu-id="40e58-121">**sqlcmd** variables and commands.</span></span> <span data-ttu-id="40e58-122">이러한 변수 및 명령에 대한 자세한 내용은 [sqlcmd Utility](../tools/sqlcmd-utility.md)의 주의 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="40e58-122">For information about these variables and commands, see the Remarks section of [sqlcmd Utility](../tools/sqlcmd-utility.md).</span></span>  
  
-   [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="40e58-123">문.</span><span class="sxs-lookup"><span data-stu-id="40e58-123">statements.</span></span> <span data-ttu-id="40e58-124">[!INCLUDE[tsql](../includes/tsql-md.md)] 언어에 대한 자세한 내용은 [Transact-SQL 참조&#40;데이터베이스 엔진&#41;](/sql/t-sql/language-reference)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="40e58-124">For more information about the [!INCLUDE[tsql](../includes/tsql-md.md)] language, see [Transact-SQL Reference &#40;Database Engine&#41;](/sql/t-sql/language-reference).</span></span>  
  
-   <span data-ttu-id="40e58-125">XQuery 문.</span><span class="sxs-lookup"><span data-stu-id="40e58-125">XQuery statements.</span></span> <span data-ttu-id="40e58-126">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 지원하는 XQuery 언어에 대한 자세한 내용은 [XQuery 언어 참조&#40;SQL Server&#41;](/sql/xquery/xquery-language-reference-sql-server)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="40e58-126">For more information about the XQuery language supported by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [XQuery Language Reference &#40;SQL Server&#41;](/sql/xquery/xquery-language-reference-sql-server).</span></span>  
  
## <a name="get-help-for-a-sql-server-cmdlet"></a><span data-ttu-id="40e58-127">SQL Server cmdlet에 대한 도움말 보기</span><span class="sxs-lookup"><span data-stu-id="40e58-127">Get Help for a SQL Server cmdlet</span></span>  
 <span data-ttu-id="40e58-128">**cmdlet에 대한 도움말을 보려면**</span><span class="sxs-lookup"><span data-stu-id="40e58-128">**To get help for a cmdlet**</span></span>  
  
-   <span data-ttu-id="40e58-129">cmdlet의 이름과 반환할 도움말의 수준을 지정하여 Get-Help를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="40e58-129">Run Get-Help specifying the name of the cmdlet and the level of help to be returned.</span></span>  
  
### <a name="example-cmdlet-get-help"></a><span data-ttu-id="40e58-130">예: Get-Help cmdlet</span><span class="sxs-lookup"><span data-stu-id="40e58-130">Example: cmdlet Get-Help</span></span>  
 <span data-ttu-id="40e58-131">다음 예에서는 **Invoke-Sqlcmd**에 대한 다양한 수준의 도움말을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="40e58-131">The following examples return various levels of help for **Invoke-Sqlcmd**:</span></span>  
  
```powershell
## Get the basic help.  
Get-Help Invoke-Sqlcmd  
  
## Get the full help.  
Get-Help Invoke-Sqlcmd -Full  
  
## Get the parameter descriptions.  
Get-Help Invoke-Sqlcmd -Parameter *  
  
## Get the code examples.  
Get-Help Invoke-Sqlcmd -Examples  
  
## Get the syntax diagram.  
Get-Help Invoke-Sqlcmd -Syntax  
```  
  
## <a name="get-a-list-of-providers"></a><span data-ttu-id="40e58-132">공급자 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="40e58-132">Get a List of Providers</span></span>  

### <a name="to-get-a-list-of-active-providers"></a><span data-ttu-id="40e58-133">활성 공급자 목록을 가져오려면</span><span class="sxs-lookup"><span data-stu-id="40e58-133">To get a list of active providers</span></span>
  
1.  <span data-ttu-id="40e58-134">공급자 범주를 지정하여 Get-Help를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="40e58-134">Run Get-Help specifying the provider category.</span></span>  
  
 <span data-ttu-id="40e58-135">Windows PowerShell에서 공급자 도움말을 보는 방법은 [드라이브 및 공급자(Drives and Providers)](https://go.microsoft.com/fwlink/?LinkId=102137)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="40e58-135">For more information about getting provider help in Windows PowerShell, see [Drives and Providers](https://go.microsoft.com/fwlink/?LinkId=102137).</span></span>  
  
### <a name="example-get-a-list-of-providers"></a><span data-ttu-id="40e58-136">예: 공급자 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="40e58-136">Example: Get a List of Providers</span></span>  
 <span data-ttu-id="40e58-137">다음 코드는 Windows PowerShell 세션에서 현재 사용 가능한 공급자의 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="40e58-137">This code returns a list of the providers currently enabled in your Windows PowerShell session:</span></span>  
  
```powershell
Get-Help -Category provider  
```  
  
## <a name="get-help-about-the-sql-server-provider"></a><span data-ttu-id="40e58-138">SQL Server 공급자에 대한 도움말 가져오기</span><span class="sxs-lookup"><span data-stu-id="40e58-138">Get Help About the SQL Server Provider</span></span>  
 <span data-ttu-id="40e58-139">**공급자에 대한 도움말을 가져오려면**</span><span class="sxs-lookup"><span data-stu-id="40e58-139">**To get help about the provider**</span></span>  
  
1.  <span data-ttu-id="40e58-140">이름을 SQLServer로 지정하여 Get-Help를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="40e58-140">Run Get-Help specifying the name SQLServer</span></span>  
  
### <a name="example-get-sql-server-provider-help"></a><span data-ttu-id="40e58-141">예: SQL Server 공급자 도움말 가져오기</span><span class="sxs-lookup"><span data-stu-id="40e58-141">Example: Get SQL Server Provider Help</span></span>  
 <span data-ttu-id="40e58-142">이 예에서는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 공급자에 대한 기본 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="40e58-142">This example returns basic information about the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider:</span></span>  
  
```powershell
Get-Help SQLServer  
```  
  
## <a name="list-methods-and-properties"></a><span data-ttu-id="40e58-143">메서드 및 속성 나열</span><span class="sxs-lookup"><span data-stu-id="40e58-143">List Methods and Properties</span></span>  
 <span data-ttu-id="40e58-144">**SQL Server 공급자 경로에서 노드에 대한 메서드와 속성을 나열하려면**</span><span class="sxs-lookup"><span data-stu-id="40e58-144">**To list the methods and properties for a node in a SQL Server provider path**</span></span>  
  
1.  <span data-ttu-id="40e58-145">CD 명령으로 SQL Server 경로의 노드로 이동하거나 해당 위치로 설정된 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="40e58-145">Either CD to a node in the SQL Server path, or create a variable set to that location.</span></span>  
  
2.  <span data-ttu-id="40e58-146">-Type 매개 변수를 메서드 또는 속성으로 설정 하 여 **Get Member** cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="40e58-146">Run the **Get-Member** cmdlet with the -Type parameter set to either Methods or Properties</span></span>  
  
### <a name="examples-listing-methods-and-properties"></a><span data-ttu-id="40e58-147">예: 메서드 및 속성 나열</span><span class="sxs-lookup"><span data-stu-id="40e58-147">Examples: Listing Methods and Properties</span></span>  
 <span data-ttu-id="40e58-148">이 예에서는 Databases 노드에 지원되는 메서드를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="40e58-148">This example lists the methods supported for the Databases node:</span></span>  
  
```powershell
Set-Location SQL:\MyComputer\DEFAULT\Databases  
Get-Item . | Get-Member -Type Methods  
```  
  
 <span data-ttu-id="40e58-149">이 예에서는 SMO Table 개체에 설정된 변수의 속성을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="40e58-149">This example lists the properties for a variable that has been set to an SMO Table object:</span></span>  
  
```powershell
$MyVar = New-Object Microsoft.SqlServer.Management.SMO.Table  
$MyVar | Get-Member -Type Properties  
```  
  
## <a name="see-also"></a><span data-ttu-id="40e58-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="40e58-150">See Also</span></span>  
 <span data-ttu-id="40e58-151">[SQL Server PowerShell 공급자](../powershell/sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="40e58-151">[SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="40e58-152">데이터베이스 엔진 cmdlet 사용</span><span class="sxs-lookup"><span data-stu-id="40e58-152">Use the Database Engine cmdlets</span></span>](../../2014/database-engine/use-the-database-engine-cmdlets.md)  
