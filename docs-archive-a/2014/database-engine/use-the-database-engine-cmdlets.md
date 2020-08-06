---
title: 데이터베이스 엔진 cmdlet 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Cmdlets [SQL Server], Encode-Sqlname
- Encode-Sqlname cmdlet
- PowerShell [SQL Server], Encode-Sqlname
- Convert-UrnToPath cmdlet
- PowerShell [SQL Server], cmdlets
- Cmdlets [SQL Server]
- PowerShell [SQL Server], Convert-UrnToPath
- Cmdlets [SQL Server], Convert-UrnToPath
- Decode-Sqlname cmdlet
- PowerShell [SQL Server], Decode-Sqlname
- Cmdlets [SQL Server], Decode-Sqlname
ms.assetid: 720aa982-09ae-41a3-b603-a91004cfbe3e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 015500c7c985f9f1a1d190954406844f3b184932
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646590"
---
# <a name="use-the-database-engine-cmdlets"></a><span data-ttu-id="58a91-102">데이터베이스 엔진 cmdlet 사용</span><span class="sxs-lookup"><span data-stu-id="58a91-102">Use the Database Engine cmdlets</span></span>
  <span data-ttu-id="58a91-103">Windows PowerShell cmdlet은 **Get-Help** 또는 **Set-MachineName**과 같이 일반적으로 동사-명사 명명 규칙을 사용하는 단일 함수 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="58a91-103">Windows PowerShell cmdlets are single-function commands that typically have a verb-noun naming convention, such as **Get-Help** or **Set-MachineName**.</span></span> <span data-ttu-id="58a91-104">Windows PowerShell의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 공급자는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]관련 cmdlet을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="58a91-104">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider for Windows PowerShell supplies cmdlets specific to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="database-engine-cmdlets"></a><span data-ttu-id="58a91-105">데이터베이스 엔진 cmdlet</span><span class="sxs-lookup"><span data-stu-id="58a91-105">Database Engine cmdlets</span></span>  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="58a91-106">은 적은 수의 [!INCLUDE[ssDE](../includes/ssde-md.md)]cmdlet을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="58a91-106">implements a small number of cmdlets for the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="58a91-107">이러한 cmdlet은 새 PowerShell 스크립트에서 기존 Transact-SQL 스크립트를 실행하고 정책 기반 관리 정책을 평가하며 SQL Server 공급자 경로에서 SQL Server 식별자 지정을 지원하는 데 주로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="58a91-107">These cmdlets are primarily used to run existing Transact-SQL scripts from new PowerShell scripts, evaluate policy-based management policies, and aid in specifying SQL Server identifiers in SQL Server Provider paths.</span></span>  
  
 <span data-ttu-id="58a91-108">대부분의 Windows PowerShell 스크립트는 SQL Server PowerShell 공급자 및 SQL Server 관리 효율성 개체 모델을 사용하여 [!INCLUDE[ssDE](../includes/ssde-md.md)] 에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="58a91-108">Most Windows PowerShell scripts work with the [!INCLUDE[ssDE](../includes/ssde-md.md)] by using the SQL Server PowerShell provider and the SQL Server manageability object models.</span></span> <span data-ttu-id="58a91-109">자세한 내용은 [SQL Server PowerShell](../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="58a91-109">For more information, see [SQL Server PowerShell](../powershell/sql-server-powershell.md).</span></span>  
  
### <a name="get-cmdlet-help"></a><span data-ttu-id="58a91-110">Cmdlet 도움말 보기</span><span class="sxs-lookup"><span data-stu-id="58a91-110">Get Cmdlet Help</span></span>  
 <span data-ttu-id="58a91-111">Windows PowerShell 환경에서 **Get-Help** cmdlet은 각 cmdlet에 대한 도움말 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="58a91-111">In the Windows PowerShell environment, the **Get-Help** cmdlet provides help information for each cmdlet.</span></span> <span data-ttu-id="58a91-112">**Get-Help** 는 구문, 매개 변수 정의, 입력 및 출력 유형, cmdlet에서 수행하는 동작에 대한 설명과 같은 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="58a91-112">**Get-Help** returns information such as the syntax, parameter definitions, input and output types, and a description of the action performed by the cmdlet.</span></span> <span data-ttu-id="58a91-113">자세한 내용은 [Get Help SQL Server PowerShell](../../2014/database-engine/get-help-sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="58a91-113">For more information, see [Get Help SQL Server PowerShell](../../2014/database-engine/get-help-sql-server-powershell.md).</span></span>  
  
### <a name="partial-parameter-names"></a><span data-ttu-id="58a91-114">부분 매개 변수 이름</span><span class="sxs-lookup"><span data-stu-id="58a91-114">Partial Parameter Names</span></span>  
 <span data-ttu-id="58a91-115">cmdlet 매개 변수의 전체 이름을 지정할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="58a91-115">You do not have to specify the entire name of a cmdlet parameter.</span></span> <span data-ttu-id="58a91-116">cmdlet에서 지원하는 다른 매개 변수와 고유하게 구분될 수 있도록 이름을 지정하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="58a91-116">You only have to specify enough of the name to uniquely separate it from the other parameters that are supported by the cmdlet.</span></span> <span data-ttu-id="58a91-117">예를 들어 이 예에서는 **Invoke-Sqlcmd -QueryTimeout** 매개 변수를 지정하는 3가지 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="58a91-117">For example, these examples show three ways of specifying the **Invoke-Sqlcmd -QueryTimeout** parameter:</span></span>  
  
```powershell
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryTimeout 3  
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryTime 3  
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryT 3  
```  
  
## <a name="database-engine-cmdlet-tasks"></a><span data-ttu-id="58a91-118">데이터베이스 엔진 cmdlet 태스크</span><span class="sxs-lookup"><span data-stu-id="58a91-118">Database Engine cmdlet Tasks</span></span>  
  
|<span data-ttu-id="58a91-119">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="58a91-119">Task Description</span></span>|<span data-ttu-id="58a91-120">항목</span><span class="sxs-lookup"><span data-stu-id="58a91-120">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="58a91-121">**Invoke-Sqlcmd** 를 사용하여 **또는 XQuery 문이 포함된** sqlcmd [!INCLUDE[tsql](../includes/tsql-md.md)] 스크립트 또는 명령을 실행하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="58a91-121">Describes using **Invoke-Sqlcmd** to run **sqlcmd** scripts or commands that contain [!INCLUDE[tsql](../includes/tsql-md.md)] or XQuery statements.</span></span> <span data-ttu-id="58a91-122">**sqlcmd** 입력을 문자열 입력 매개 변수 또는 열려는 스크립트 파일의 이름으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58a91-122">It can accept the **sqlcmd** input as either a character string input parameter, or as the name of a script file to open.</span></span>|[<span data-ttu-id="58a91-123">Invoke-Sqlcmd cmdlet</span><span class="sxs-lookup"><span data-stu-id="58a91-123">Invoke-Sqlcmd cmdlet</span></span>](../../2014/database-engine/invoke-sqlcmd-cmdlet.md)|  
|<span data-ttu-id="58a91-124">**Invoke-PolicyEvaluation** 을 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 개체의 대상 집합이 정책 기반 관리 정책에 정의된 조건을 준수하는지 여부를 보고하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="58a91-124">Describes using **Invoke-PolicyEvaluation** to report whether a target set of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects comply with the conditions that are defined in policy-based management policies.</span></span> <span data-ttu-id="58a91-125">필요에 따라 cmdlet을 사용하여 정책 조건을 준수하지 않는 대상 개체의 설정할 수 있는 옵션을 다시 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58a91-125">Optionally, the cmdlet can be used to reconfigure any settable options in the target objects that do not comply with the policy conditions.</span></span>|[<span data-ttu-id="58a91-126">Invoke-PolicyEvaluation cmdlet</span><span class="sxs-lookup"><span data-stu-id="58a91-126">Invoke-PolicyEvaluation cmdlet</span></span>](../../2014/database-engine/invoke-policyevaluation-cmdlet.md)|  
|<span data-ttu-id="58a91-127">`Encode-Sqlname` 및 `Decode-Sqlname`을 사용하여 Windows PowerShell 경로에서 지원되지 않는 문자가 포함된 SQL Server 식별자를 처리하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="58a91-127">Describes using `Encode-Sqlname` and `Decode-Sqlname` to handle SQL Server identifiers that contain characters not supported in Windows PowerShell paths.</span></span>|[<span data-ttu-id="58a91-128">SQL Server 식별자 인코딩 및 디코딩</span><span class="sxs-lookup"><span data-stu-id="58a91-128">Encode and Decode SQL Server Identifiers</span></span>](../powershell/encode-and-decode-sql-server-identifiers.md)|  
|<span data-ttu-id="58a91-129">`Convert-UrnToPath`를 사용하여 SQL Server 관리 효율성 개체 URN(Uniform Resource Name)을 해당 SQL Server 공급자 경로로 변환하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="58a91-129">Describes using `Convert-UrnToPath` to convert a SQL Server Manageability Object Uniform Resource Name (URN) to the equivalent SQL Server Provider path.</span></span>|[<span data-ttu-id="58a91-130">URN을 SQL Server 공급자 경로로 변환</span><span class="sxs-lookup"><span data-stu-id="58a91-130">Convert URNs to SQL Server Provider Paths</span></span>](../../2014/database-engine/convert-urns-to-sql-server-provider-paths.md)|  
  
## <a name="see-also"></a><span data-ttu-id="58a91-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="58a91-131">See Also</span></span>  
 <span data-ttu-id="58a91-132">[SQL Server PowerShell 공급자](../powershell/sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="58a91-132">[SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md) </span></span>  
 <span data-ttu-id="58a91-133">[SQL Server PowerShell](../powershell/sql-server-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="58a91-133">[SQL Server PowerShell](../powershell/sql-server-powershell.md) </span></span>  
 [<span data-ttu-id="58a91-134">AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 PowerShell Cmdlet 개요&#41;</span><span class="sxs-lookup"><span data-stu-id="58a91-134">Overview of PowerShell Cmdlets for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](availability-groups/windows/overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)  
  
  
