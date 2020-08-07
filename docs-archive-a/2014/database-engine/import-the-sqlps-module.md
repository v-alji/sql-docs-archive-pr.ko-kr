---
title: SQLPS 모듈 가져오기 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: a972c56e-b2af-4fe6-abbd-817406e2c93a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 37e66db05615ce8a285a80e5ac26b0cae411abeb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734444"
---
# <a name="import-the-sqlps-module"></a><span data-ttu-id="5d468-102">SQLPS 모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="5d468-102">Import the SQLPS Module</span></span>
  <span data-ttu-id="5d468-103">PowerShell에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]를 관리하는 데 권장되는 방법은 `sqlps` 모듈을 Windows PowerShell 2.0 환경으로 가져오는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5d468-103">The recommended way to manage [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] from PowerShell is to import the `sqlps` module into a Windows PowerShell 2.0 environment.</span></span> <span data-ttu-id="5d468-104">이 모듈은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 스냅인 및 관리 효율성 어셈블리를 로드하고 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="5d468-104">The module loads and registers the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] snap-ins and manageability assemblies.</span></span>  
  
1.  <span data-ttu-id="5d468-105">**시작 하기 전 주의:**  [보안](#Security)</span><span class="sxs-lookup"><span data-stu-id="5d468-105">**Before You Begin:**  [Security](#Security)</span></span>  
  
2.  <span data-ttu-id="5d468-106">**모듈을 로드하려면**  [sqlps 모듈 로드](#LoadSqlps)</span><span class="sxs-lookup"><span data-stu-id="5d468-106">**To load the module:**  [Load the sqlps Module](#LoadSqlps)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="5d468-107">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="5d468-107">Before You Begin</span></span>  
 <span data-ttu-id="5d468-108">`sqlps` 모듈을 Windows PowerShell로 가져온 후 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d468-108">After importing the `sqlps` module into Windows PowerShell, you can then:</span></span>  
  
-   <span data-ttu-id="5d468-109">대화형으로 Windows PowerShell 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5d468-109">Interactively run Windows PowerShell commands.</span></span>  
  
-   <span data-ttu-id="5d468-110">Windows PowerShell 스크립트 파일을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5d468-110">Run Windows PowerShell script files.</span></span>  
  
-   <span data-ttu-id="5d468-111">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5d468-111">Run [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlets.</span></span>  
  
-   <span data-ttu-id="5d468-112">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 공급자 경로를 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 개체의 계층 구조를 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="5d468-112">Use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider paths to navigate through the hierarchy of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects.</span></span>  
  
-   <span data-ttu-id="5d468-113">Microsoft.SqlServer.Management.Smo 같은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 관리 효율성 개체 모델을 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 개체를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="5d468-113">Use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] manageability object models (such as Microsoft.SqlServer.Management.Smo) to manage [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5d468-114">두 SQL Server cmdlet(`Encode-Sqlname` 및 `Decode-Sqlname`)의 이름에 사용되는 동사는 Windows PowerShell 2.0에 대해 승인된 동사와 일치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5d468-114">The verbs used in the names of two SQL Server cmdlets (`Encode-Sqlname` and `Decode-Sqlname`) do not match the approved verbs for Windows PowerShell 2.0.</span></span> <span data-ttu-id="5d468-115">이로 인해 작동에는 영향을 주지 않지만 `sqlps` 모듈을 세션으로 가져올 때 Windows PowerShell에서 경고를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5d468-115">This has no effect on their operation, but Windows PowerShell raises a warning when the `sqlps` module is imported to a session.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5d468-116">보안</span><span class="sxs-lookup"><span data-stu-id="5d468-116">Security</span></span>  
 <span data-ttu-id="5d468-117">기본적으로 Windows PowerShell은 모든 Windows PowerShell 스크립트 실행을 방지하는 **제한됨**으로 설정된 스크립팅 실행 정책과 함께 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d468-117">By default, Windows PowerShell runs with the scripting execution policy set to **Restricted**, which prevents running any Windows PowerShell scripts.</span></span> <span data-ttu-id="5d468-118">`sqlps` 모듈을 로드하려면 `Set-ExecutionPolicy` cmdlet을 사용하여 서명된 스크립트나 기타 스크립트를 실행할 수 있도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5d468-118">To load the `sqlps` module, you can use the `Set-ExecutionPolicy` cmdlet to enable running signed scripts, or any scripts.</span></span> <span data-ttu-id="5d468-119">신뢰할 수 있는 출처에서 제공하는 스크립트만 실행하고 적절한 NTFS 권한을 사용하여 모든 입력 및 출력 파일을 보호하십시오.</span><span class="sxs-lookup"><span data-stu-id="5d468-119">Only run scripts from trusted sources, and secure all input and output files using the appropriate NTFS permissions.</span></span> <span data-ttu-id="5d468-120">Windows PowerShell 스크립트를 사용하도록 설정하는 방법은 [Windows PowerShell 스크립트 실행](https://docs.microsoft.com/powershell/scripting/getting-started/starting-windows-powershell?view=powershell-6#how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5d468-120">For more information about enabling Windows PowerShell scripts, see [Running Windows PowerShell Scripts](https://docs.microsoft.com/powershell/scripting/getting-started/starting-windows-powershell?view=powershell-6#how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows).</span></span>  
  
##  <a name="load-the-sqlps-module"></a><a name="LoadSqlps"></a> <span data-ttu-id="5d468-121">sqlps 모듈 로드</span><span class="sxs-lookup"><span data-stu-id="5d468-121">Load the sqlps Module</span></span>  

### <a name="to-load-the-sqlps-module-in-windows-powershell"></a><span data-ttu-id="5d468-122">Windows PowerShell에서 sqlps 모듈을 로드하려면</span><span class="sxs-lookup"><span data-stu-id="5d468-122">To load the sqlps module in Windows PowerShell</span></span>
  
1.  <span data-ttu-id="5d468-123">`Set-ExecutionPolicy` cmdlet을 사용하여 적절한 스크립트 실행 정책을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5d468-123">Use the `Set-ExecutionPolicy` cmdlet to set the appropriate script execution policy.</span></span>  
  
2.  <span data-ttu-id="5d468-124">`Import-Module` cmdlet을 사용하여 sqlps 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5d468-124">Use the `Import-Module` cmdlet to import the sqlps module.</span></span> <span data-ttu-id="5d468-125">`DisableNameChecking` 및 `Encode-Sqlname`에 대한 경고를 억제하려면 `Decode-Sqlname` 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5d468-125">Specify the `DisableNameChecking` parameter if you want to suppress the warning about `Encode-Sqlname` and `Decode-Sqlname`.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="5d468-126">예제(PowerShell)</span><span class="sxs-lookup"><span data-stu-id="5d468-126">Example (PowerShell)</span></span>  
 <span data-ttu-id="5d468-127">이 예에서는 이름 확인을 해제한 상태로 `sqlps` 모듈을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="5d468-127">This example loads the `sqlps` module with name checking turned off.</span></span>  
  
```powershell
## Import the SQL Server Module.  
  
Import-Module "sqlps" -DisableNameChecking  
```  

## <a name="see-also"></a><span data-ttu-id="5d468-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5d468-128">See Also</span></span>  
 <span data-ttu-id="5d468-129">[SQL Server PowerShell](../powershell/sql-server-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="5d468-129">[SQL Server PowerShell](../powershell/sql-server-powershell.md) </span></span>  
 <span data-ttu-id="5d468-130">[SQL Server PowerShell 공급자](../powershell/sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="5d468-130">[SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="5d468-131">데이터베이스 엔진 cmdlet 사용</span><span class="sxs-lookup"><span data-stu-id="5d468-131">Use the Database Engine cmdlets</span></span>](../../2014/database-engine/use-the-database-engine-cmdlets.md)  
