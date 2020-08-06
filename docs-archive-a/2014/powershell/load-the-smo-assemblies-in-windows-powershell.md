---
title: Windows PowerShell에서 SMO 어셈블리 로드 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 8ca42b69-da5a-47f4-9085-34e443f0e389
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9886d80c305dba251e6e3ab22ddb4dfb39783748
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728376"
---
# <a name="load-the-smo-assemblies-in-windows-powershell"></a><span data-ttu-id="37dd0-102">Windows PowerShell에서 SMO 어셈블리 로드</span><span class="sxs-lookup"><span data-stu-id="37dd0-102">Load the SMO Assemblies in Windows PowerShell</span></span>
  <span data-ttu-id="37dd0-103">이 항목에서는 SQL Server PowerShell 공급자를 사용하지 않는 Windows PowerShell 스크립트에서 SMO(SQL Server Management Object) 어셈블리를 로드하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="37dd0-103">This topic describes how to load the SQL Server Management Object (SMO) assemblies in Windows PowerShell scripts that do not use the SQL Server PowerShell provider.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="37dd0-104">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="37dd0-104">Before You Begin</span></span>  
 <span data-ttu-id="37dd0-105">SMO 어셈블리를 로드하는 기본 메커니즘은 `sqlps` 모듈을 로드하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="37dd0-105">The preferred mechanism for loading the SMO assemblies is to load the `sqlps` module.</span></span> <span data-ttu-id="37dd0-106">모듈에 포함된 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 공급자는 SMO 어셈블리를 자동으로 로드하며 PowerShell 스크립트에서 SMO 개체의 유용성을 확장하는 기능도 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="37dd0-106">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider included in the module automatically loads the SMO assemblies, and also implements features that extend the usefulness of the SMO objects in PowerShell scripts.</span></span>  
  
 <span data-ttu-id="37dd0-107">SMO 어셈블리를 직접 로드해야 할 수 있는 두 가지 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37dd0-107">There are two cases where you may need to load the SMO assemblies directly:</span></span>  
  
-   <span data-ttu-id="37dd0-108">스크립트에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 스냅인의 cmdlet 또는 공급자를 참조하는 첫 번째 명령 전에 SMO 개체를 참조하는 경우</span><span class="sxs-lookup"><span data-stu-id="37dd0-108">If your script references a SMO object before the first command that references the provider or cmdlets from the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] snap-ins.</span></span>  
  
-   <span data-ttu-id="37dd0-109">공급자 또는 cmdlet을 사용하지 않는 C# 또는 Visual Basic과 같은 다른 언어에서 SMO 코드를 이식하려는 경우</span><span class="sxs-lookup"><span data-stu-id="37dd0-109">You want to port SMO code from another language, such as C# or Visual Basic, which does not use the provider or cmdlets.</span></span>  
  
## <a name="example-loading-the-sql-server-management-objects"></a><span data-ttu-id="37dd0-110">예제: SQL Server 관리 개체 로드</span><span class="sxs-lookup"><span data-stu-id="37dd0-110">Example: Loading the SQL Server Management Objects</span></span>  
 <span data-ttu-id="37dd0-111">다음 코드는 SMO 어셈블리를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="37dd0-111">The following code loads the SMO assemblies:</span></span>  
  
```powershell
# Loads the SQL Server Management Objects (SMO)  
  
$ErrorActionPreference = "Stop"  
  
$sqlpsreg = "HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.SqlServer.Management.PowerShell.sqlps"  
  
if (Get-ChildItem $sqlpsreg -ErrorAction "SilentlyContinue")  
{  
    throw "SQL Server Provider for Windows PowerShell is not installed."  
}  
else  
{  
    $item = Get-ItemProperty $sqlpsreg  
    $sqlpsPath = [System.IO.Path]::GetDirectoryName($item.Path)  
}  
  
$assemblylist =   
"Microsoft.SqlServer.Management.Common",  
"Microsoft.SqlServer.Smo",  
"Microsoft.SqlServer.Dmf ",  
"Microsoft.SqlServer.Instapi ",  
"Microsoft.SqlServer.SqlWmiManagement ",  
"Microsoft.SqlServer.ConnectionInfo ",  
"Microsoft.SqlServer.SmoExtended ",  
"Microsoft.SqlServer.SqlTDiagM ",  
"Microsoft.SqlServer.SString ",  
"Microsoft.SqlServer.Management.RegisteredServers ",  
"Microsoft.SqlServer.Management.Sdk.Sfc ",  
"Microsoft.SqlServer.SqlEnum ",  
"Microsoft.SqlServer.RegSvrEnum ",  
"Microsoft.SqlServer.WmiEnum ",  
"Microsoft.SqlServer.ServiceBrokerEnum ",  
"Microsoft.SqlServer.ConnectionInfoExtended ",  
"Microsoft.SqlServer.Management.Collector ",  
"Microsoft.SqlServer.Management.CollectorEnum",  
"Microsoft.SqlServer.Management.Dac",  
"Microsoft.SqlServer.Management.DacEnum",  
"Microsoft.SqlServer.Management.Utility"  
  
foreach ($asm in $assemblylist)  
{  
    $asm = [Reflection.Assembly]::LoadWithPartialName($asm)  
}  
  
Push-Location  
cd $sqlpsPath  
Update-FormatData -PrependPath SQLProvider.Format.ps1xml
Pop-Location  
```  
  
## <a name="see-also"></a><span data-ttu-id="37dd0-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="37dd0-112">See Also</span></span>  
 [<span data-ttu-id="37dd0-113">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="37dd0-113">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
