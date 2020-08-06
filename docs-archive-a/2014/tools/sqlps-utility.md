---
title: sqlps 유틸리티 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- sqlps utility
- PowerShell [SQL Server], sqlps utility
ms.assetid: 4b2515a6-12c3-44fb-b263-1c567681cd2b
author: stevestein
ms.author: sstein
ms.openlocfilehash: b445366b3fb99ad4beebdf7b203ada77afe90c8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727532"
---
# <a name="sqlps-utility"></a><span data-ttu-id="4ab31-102">sqlps 유틸리티</span><span class="sxs-lookup"><span data-stu-id="4ab31-102">sqlps Utility</span></span>
  <span data-ttu-id="4ab31-103">`sqlps` 유틸리티는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 공급자와 cmdlet이 로드 및 등록된 Windows PowerShell 2.0 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-103">The `sqlps` utility starts a Windows PowerShell 2.0 session with the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell provider and cmdlets loaded and registered.</span></span> <span data-ttu-id="4ab31-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 구성 요소를 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스 및 해당 개체와 함께 작동하는 PowerShell 명령 또는 스크립트를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-104">You can enter PowerShell commands or scripts that use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell components to work with instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and their objects.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../includes/ssnotedepfutureavoid-md.md)] <span data-ttu-id="4ab31-105">대신 `sqlps` PowerShell 모듈을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="4ab31-105">Use the `sqlps` PowerShell module instead.</span></span> <span data-ttu-id="4ab31-106">모듈에 대 한 자세한 내용은 `sqlps` [SQLPS 모듈 가져오기](../database-engine/import-the-sqlps-module.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4ab31-106">For more information about the `sqlps` module, see [Import the SQLPS Module](../database-engine/import-the-sqlps-module.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ab31-107">구문</span><span class="sxs-lookup"><span data-stu-id="4ab31-107">Syntax</span></span>  
  
```  
  
      sqlps   
[ [ [ -NoLogo ][ -NoExit ][ -NoProfile ]  
    [ -OutPutFormat { Text | XML } ] [ -InPutFormat { Text | XML } ]  
  ]  
  [ -Command { -  
             | script_block [ -argsargument_array ]  
             | string [ command_parameters ]  
             }  
  ]  
]  
[ -? | -Help ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4ab31-108">인수</span><span class="sxs-lookup"><span data-stu-id="4ab31-108">Arguments</span></span>  
 <span data-ttu-id="4ab31-109">**-NoLogo**</span><span class="sxs-lookup"><span data-stu-id="4ab31-109">**-NoLogo**</span></span>  
 <span data-ttu-id="4ab31-110">`sqlps` 유틸리티가 시작될 때 저작권 배너를 표시하지 않도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-110">Specifies that the `sqlps` utility hide the copyright banner when it starts.</span></span>  
  
 <span data-ttu-id="4ab31-111">**-NoExit**</span><span class="sxs-lookup"><span data-stu-id="4ab31-111">**-NoExit**</span></span>  
 <span data-ttu-id="4ab31-112">시작 명령이 완료된 후에도 `sqlps` 유틸리티가 계속 실행되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-112">Specifies that the `sqlps` utility continue running after the startup commands have completed.</span></span>  
  
 <span data-ttu-id="4ab31-113">**-NoProfile**</span><span class="sxs-lookup"><span data-stu-id="4ab31-113">**-NoProfile**</span></span>  
 <span data-ttu-id="4ab31-114">`sqlps` 유틸리티가 사용자 프로필을 로드하지 않도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-114">Specifies that the `sqlps` utility not load a user profile.</span></span> <span data-ttu-id="4ab31-115">사용자 프로필은 PowerShell 세션에서 사용하도록 공통적으로 사용되는 별칭, 함수 및 변수를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-115">User profiles record commonly used aliases, functions, and variables for use across PowerShell sessions.</span></span>  
  
 <span data-ttu-id="4ab31-116">**-OutPutFormat** { **Text** | **XML** }</span><span class="sxs-lookup"><span data-stu-id="4ab31-116">**-OutPutFormat** { **Text** | **XML** }</span></span>  
 <span data-ttu-id="4ab31-117">`sqlps`유틸리티 출력 형식이 텍스트 문자열 (**text**) 또는 직렬화 된 Export-clixml 형식 (**XML**)이 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-117">Specifies that the `sqlps` utility output be formatted as either text strings (**Text**) or in a serialized CLIXML format (**XML**).</span></span>  
  
 <span data-ttu-id="4ab31-118">**-InPutFormat** { **Text** | **XML** }</span><span class="sxs-lookup"><span data-stu-id="4ab31-118">**-InPutFormat** { **Text** | **XML** }</span></span>  
 <span data-ttu-id="4ab31-119">유틸리티에 대 한 입력 `sqlps` 형식이 텍스트 문자열 (**text**) 또는 직렬화 된 Export-clixml 형식 (**XML**)이 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-119">Specifies that input to the `sqlps` utility is formatted as either text strings (**Text**) or in a serialized CLIXML format (**XML**).</span></span>  
  
 <span data-ttu-id="4ab31-120">**-Command**</span><span class="sxs-lookup"><span data-stu-id="4ab31-120">**-Command**</span></span>  
 <span data-ttu-id="4ab31-121">`sqlps` 유틸리티에 대한 명령이 실행되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-121">Specifies the command for the `sqlps` utility to run.</span></span> <span data-ttu-id="4ab31-122">`sqlps`유틸리티는 **-noexit** 가 지정 되지 않은 경우 명령을 실행 한 다음 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-122">The `sqlps` utility runs the command and then exits, unless **-NoExit** is also specified.</span></span> <span data-ttu-id="4ab31-123">**-Command**뒤에는 다른 스위치를 지정하지 마세요. 이 경우 스위치가 명령 매개 변수로 읽힙니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-123">Do not specify any other switches after **-Command**, they will be read as command parameters.</span></span>  
  
 **-**  
 <span data-ttu-id="4ab31-124">**-Command-** `sqlps` 유틸리티에서 표준 입력의 입력을 읽도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-124">**-Command-** specifies that the `sqlps` utility read the input from the standard input.</span></span>  
  
 <span data-ttu-id="4ab31-125">*script_block* [ **-args**_argument_array_ ]</span><span class="sxs-lookup"><span data-stu-id="4ab31-125">*script_block* [ **-args**_argument_array_ ]</span></span>  
 <span data-ttu-id="4ab31-126">실행할 PowerShell 명령 블록을 지정합니다. 명령 블록은 중괄호 {}로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-126">Specifies a block of PowerShell commands to run, the block must be enclosed in braces: {}.</span></span> <span data-ttu-id="4ab31-127">*Script_block* `sqlps` 유틸리티를 **PowerShell** 또는 다른 유틸리티 세션에서 호출 하는 경우에만 Script_block 지정할 수 있습니다 `sqlps` .</span><span class="sxs-lookup"><span data-stu-id="4ab31-127">*Script_block* can only be specified when the `sqlps` utility is called from either **PowerShell** or another `sqlps` utility session.</span></span> <span data-ttu-id="4ab31-128">*argument_array* 는 *script_block*의 PowerShell 명령에 대한 인수를 포함하는 PowerShell 변수 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-128">The *argument_array* is an array of PowerShell variables containing the arguments for the PowerShell commands in the *script_block*.</span></span>  
  
 <span data-ttu-id="4ab31-129">*string* [ *command_parameters* ]</span><span class="sxs-lookup"><span data-stu-id="4ab31-129">*string* [ *command_parameters* ]</span></span>  
 <span data-ttu-id="4ab31-130">실행할 PowerShell 명령을 포함하는 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-130">Specifies a string that contains the PowerShell commands to be run.</span></span> <span data-ttu-id="4ab31-131">**"& { *`command`* }"** 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-131">Use the format **"&{*`command`*}"**.</span></span> <span data-ttu-id="4ab31-132">따옴표는 문자열을 나타내고 호출 연산자 (&)는 `sqlps` 유틸리티를 실행 하 여 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-132">The quotation marks indicate a string, and the invoke operator (&) causes the `sqlps` utility to run the command.</span></span>  
  
 <span data-ttu-id="4ab31-133">[ **-?**</span><span class="sxs-lookup"><span data-stu-id="4ab31-133">[ **-?**</span></span><span data-ttu-id="4ab31-134"> |  **-Help** ]</span><span class="sxs-lookup"><span data-stu-id="4ab31-134"> | **-Help** ]</span></span>  
 <span data-ttu-id="4ab31-135">`sqlps` 유틸리티 옵션의 구문 요약 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-135">Shows the syntax summary of the `sqlps` utility options.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ab31-136">설명</span><span class="sxs-lookup"><span data-stu-id="4ab31-136">Remarks</span></span>  
 <span data-ttu-id="4ab31-137">`sqlps`유틸리티는 powershell 환경 (PowerShell.exe)을 시작 하 고 powershell 모듈을 로드 합니다 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4ab31-137">The `sqlps` utility starts the PowerShell environment (PowerShell.exe) and loads the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell module.</span></span> <span data-ttu-id="4ab31-138">또한 라는 모듈은 `sqlps` 이러한 PowerShell 스냅인을 로드 하 고 등록 합니다 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4ab31-138">The module, also named `sqlps`, loads and registers these [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell snap-ins:</span></span>  
  
-   <span data-ttu-id="4ab31-139">Microsoft.SqlServer.Management.PSProvider.dll</span><span class="sxs-lookup"><span data-stu-id="4ab31-139">Microsoft.SqlServer.Management.PSProvider.dll</span></span>  
  
     <span data-ttu-id="4ab31-140">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 공급자 및 **Encode-SqlName** , **Decode-SqlName**과 같은 관련 cmdlet을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-140">Implements the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell provider and associated cmdlets such as **Encode-SqlName** and **Decode-SqlName**.</span></span>  
  
-   <span data-ttu-id="4ab31-141">Microsoft.SqlServer.Management.PSSnapin.dll</span><span class="sxs-lookup"><span data-stu-id="4ab31-141">Microsoft.SqlServer.Management.PSSnapin.dll</span></span>  
  
     <span data-ttu-id="4ab31-142">**Invoke-Sqlcmd** 및 **Invoke-PolicyEvaluation** cmdlet을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-142">Implements the **Invoke-Sqlcmd** and **Invoke-PolicyEvaluation** cmdlets.</span></span>  
  
 <span data-ttu-id="4ab31-143">다음과 같은 작업에 `sqlps` 유틸리티를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-143">You can use the `sqlps` utility to do the following:</span></span>  
  
-   <span data-ttu-id="4ab31-144">대화형으로 PowerShell 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-144">Interactively run PowerShell commands.</span></span>  
  
-   <span data-ttu-id="4ab31-145">PowerShell 스크립트 파일을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-145">Run PowerShell script files.</span></span>  
  
-   <span data-ttu-id="4ab31-146">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-146">Run [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlets.</span></span>  
  
-   <span data-ttu-id="4ab31-147">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 공급자 경로를 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 개체의 계층 구조를 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-147">Use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider paths to navigate through the hierarchy of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects.</span></span>  
  
 <span data-ttu-id="4ab31-148">기본적으로 유틸리티는 `sqlps` 스크립팅 실행 정책이 **제한**으로 설정 된 상태로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-148">By default, the `sqlps` utility runs with the scripting execution policy set to **Restricted**.</span></span> <span data-ttu-id="4ab31-149">이는 모든 PowerShell 스크립트의 실행을 차단합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-149">This prevents running any PowerShell scripts.</span></span> <span data-ttu-id="4ab31-150">**Set-ExecutionPolicy** cmdlet을 사용하면 서명된 스크립트나 모든 스크립트를 실행하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-150">You can use the **Set-ExecutionPolicy** cmdlet to enable running signed scripts, or any scripts.</span></span> <span data-ttu-id="4ab31-151">신뢰할 수 있는 출처에서 제공하는 스크립트만 실행하고 적절한 NTFS 권한을 사용하여 모든 입력 및 출력 파일을 보호하십시오.</span><span class="sxs-lookup"><span data-stu-id="4ab31-151">Only run scripts from trusted sources, and secure all input and output files by using the appropriate NTFS permissions.</span></span> <span data-ttu-id="4ab31-152">PowerShell 스크립트를 설정하는 방법은 [Windows PowerShell 스크립트 실행](https://www.tech-recipes.com/rx/2513/powershell_enable_script_support/)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4ab31-152">For more information about enabling PowerShell scripts, see [Running Windows PowerShell Scripts](https://www.tech-recipes.com/rx/2513/powershell_enable_script_support/).</span></span>  
  
 <span data-ttu-id="4ab31-153">[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 및 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]의 `sqlps` 유틸리티 버전은 Windows PowerShell 1.0 미니 셸로 구현되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-153">The version of the `sqlps` utility in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] and [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] was implemented as a Windows PowerShell 1.0 mini-shell.</span></span> <span data-ttu-id="4ab31-154">미니 셸에는 사용자가 미니 셸에서 로드하는 스냅인 이외의 스냅인을 로드할 수 없는 것과 같은 몇 가지 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-154">Mini-shells have certain restrictions, such as not allowing users to load snap-ins other than those loaded by the mini-shell.</span></span> <span data-ttu-id="4ab31-155">이러한 제한 사항은 `sqlps` 모듈을 사용하도록 변경된 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 이상 버전의 유틸리티에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-155">These restrictions do not apply to the [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] and higher versions of the utility, which have been changed to use the `sqlps` module.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4ab31-156">예</span><span class="sxs-lookup"><span data-stu-id="4ab31-156">Examples</span></span>  

### <a name="a-run-the-sqlps-utility-in-default-interactive-mode-without-the-copyright-banner"></a><span data-ttu-id="4ab31-157">A.</span><span class="sxs-lookup"><span data-stu-id="4ab31-157">A.</span></span> <span data-ttu-id="4ab31-158">저작권 배너를 표시하지 않고 sqlps 유틸리티를 기본 대화형 모드로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-158">Run the sqlps utility in default, interactive mode without the copyright banner</span></span>
  
```cmd
sqlps -NoLogo  
```  
  
### <a name="b-run-a-sql-server-powershell-script-from-the-command-prompt"></a><span data-ttu-id="4ab31-159">B.</span><span class="sxs-lookup"><span data-stu-id="4ab31-159">B.</span></span> <span data-ttu-id="4ab31-160">명령 프롬프트에서 SQL Server PowerShell 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-160">Run a SQL Server PowerShell script from the command prompt</span></span>
  
```cmd
sqlps -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
### <a name="c-run-a-sql-server-powershell-script-from-the-command-prompt-and-keep-running-after-the-script-completes"></a><span data-ttu-id="4ab31-161">C.</span><span class="sxs-lookup"><span data-stu-id="4ab31-161">C.</span></span> <span data-ttu-id="4ab31-162">명령 프롬프트에서 SQL Server PowerShell 스크립트를 실행하고 스크립트가 완료된 후에도 계속 실행되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ab31-162">Run a SQL Server PowerShell script from the command prompt, and keep running after the script completes</span></span>
  
```cmd
sqlps -NoExit -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
## <a name="see-also"></a><span data-ttu-id="4ab31-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4ab31-163">See Also</span></span>  
 <span data-ttu-id="4ab31-164">[서버 네트워크 프로토콜 설정 또는 해제](../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="4ab31-164">[Enable or Disable a Server Network Protocol](../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md) </span></span>  
 [<span data-ttu-id="4ab31-165">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="4ab31-165">SQL Server PowerShell</span></span>](../powershell/sql-server-powershell.md)  
