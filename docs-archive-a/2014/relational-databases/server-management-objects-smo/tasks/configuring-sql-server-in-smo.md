---
title: SMO에서 SQL Server 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server, configuring
- configuration options [SMO]
ms.assetid: 0a372643-15cb-45a7-8665-04f1215df8ed
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6da1bca0aec650c01553b42bc2f3628b0bf7282e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739675"
---
# <a name="configuring-sql-server-in-smo"></a><span data-ttu-id="90d1f-102">SMO에서 SQL Server 구성</span><span class="sxs-lookup"><span data-stu-id="90d1f-102">Configuring SQL Server in SMO</span></span>
  <span data-ttu-id="90d1f-103">SMO에서 개체, 개체, 개체 <xref:Microsoft.SqlServer.Management.Smo.Information> <xref:Microsoft.SqlServer.Management.Smo.Settings> <xref:Microsoft.SqlServer.Management.Smo.UserOptions> 및 <xref:Microsoft.SqlServer.Management.Smo.Configuration> 개체는 인스턴스에 대 한 설정 및 정보를 포함 합니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="90d1f-103">In SMO, the <xref:Microsoft.SqlServer.Management.Smo.Information> object, the <xref:Microsoft.SqlServer.Management.Smo.Settings> object, the <xref:Microsoft.SqlServer.Management.Smo.UserOptions> object, and the <xref:Microsoft.SqlServer.Management.Smo.Configuration> object contain settings and information for the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="90d1f-104">에는 설치된 인스턴스의 동작을 설명하는 다양한 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-104">has numerous properties that describe the behavior of the installed instance.</span></span> <span data-ttu-id="90d1f-105">이러한 속성은 시작 옵션, 서버 기본값, 파일 및 디렉터리, 시스템 및 프로세서 정보, 제품 및 버전, 연결 정보, 메모리 옵션, 언어 및 데이터 정렬 선택, 인증 모드에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-105">The properties describe the startup options, the server defaults, files and directories, system and processor information, product and versions, connection information, memory options, language and collation selections, and the authentication mode.</span></span>  
  
## <a name="sql-server-configuration"></a><span data-ttu-id="90d1f-106">SQL Server 구성</span><span class="sxs-lookup"><span data-stu-id="90d1f-106">SQL Server Configuration</span></span>  
 <span data-ttu-id="90d1f-107"><xref:Microsoft.SqlServer.Management.Smo.Information> 개체 속성은 프로세서 및 플랫폼과 같은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-107">The <xref:Microsoft.SqlServer.Management.Smo.Information> object properties contain information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], such as processor and platform.</span></span>  
  
 <span data-ttu-id="90d1f-108"><xref:Microsoft.SqlServer.Management.Smo.Settings> 개체 속성은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-108">The <xref:Microsoft.SqlServer.Management.Smo.Settings> object properties contain information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="90d1f-109">기본 데이터베이스 파일 및 디렉터리를 메일 프로필 및 서버 계정과 더불어 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-109">The default database file and directory can be modified in addition to the Mail Profile and the Server Account.</span></span> <span data-ttu-id="90d1f-110">이러한 속성은 연결 기간 동안 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-110">These properties remain for the duration of the connection.</span></span>  
  
 <span data-ttu-id="90d1f-111"><xref:Microsoft.SqlServer.Management.Smo.UserOptions> 개체 속성은 산술 연산, ANSI 표준 및 트랜잭션과 관련된 현재 연결 동작에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-111">The <xref:Microsoft.SqlServer.Management.Smo.UserOptions> object properties contain information about the current connections behavior relating to arithmetic, ANSI standards, and transactions.</span></span>  
  
 <span data-ttu-id="90d1f-112"><xref:Microsoft.SqlServer.Management.Smo.Configuration> 개체로 표시되는 일련의 구성 옵션도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-112">There is also a set of configuration options that is represented by the <xref:Microsoft.SqlServer.Management.Smo.Configuration> object.</span></span> <span data-ttu-id="90d1f-113">이 개체는 `sp_configure` 저장 프로시저로 수정할 수 있는 옵션을 나타내는 일련의 속성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-113">It contains a set of properties that represent the options that can be modified by the `sp_configure` stored procedure.</span></span> <span data-ttu-id="90d1f-114">**우선 순위 높임**, **복구 간격** 및 **네트워크 패킷 크기**와 같은 옵션은 인스턴스의 성능을 제어 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-114">Options such as **Priority Boost**, **Recovery Interval** and **Network Packet Size**control the performance of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="90d1f-115">이러한 옵션은 대부분 동적으로 변경할 수 있지만, 먼저 값이 구성된 다음 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스가 다시 시작될 때 변경되는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-115">Many of these options can be changed dynamically, but in some cases the value is first configured and then changed when the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is restarted.</span></span>  
  
 <span data-ttu-id="90d1f-116">모든 구성 옵션에는 <xref:Microsoft.SqlServer.Management.Smo.Configuration> 개체 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-116">There is a <xref:Microsoft.SqlServer.Management.Smo.Configuration> object property for every configuration option.</span></span> <span data-ttu-id="90d1f-117"><xref:Microsoft.SqlServer.Management.Smo.ConfigProperty> 개체를 사용하여 전역 구성 설정을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-117">Using the <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty> object you can modify the global configuration setting.</span></span> <span data-ttu-id="90d1f-118">대부분의 속성에는 최대값 및 최소값이 있으며 이것 역시 <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty> 속성으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-118">Many properties have maximum and minimum values that are also stored as <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty> properties.</span></span> <span data-ttu-id="90d1f-119">이러한 속성에는 <xref:Microsoft.SqlServer.Management.Smo.ConfigurationBase.Alter%2A> 인스턴스에 변경 내용을 커밋하는 메서드가 필요 합니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="90d1f-119">These properties require the <xref:Microsoft.SqlServer.Management.Smo.ConfigurationBase.Alter%2A> method to commit the change to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="90d1f-120"><xref:Microsoft.SqlServer.Management.Smo.Configuration> 개체의 모든 구성 옵션은 시스템 관리자가 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-120">All of the configuration options in the <xref:Microsoft.SqlServer.Management.Smo.Configuration> object must be changed by the system administrator.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="90d1f-121">예</span><span class="sxs-lookup"><span data-stu-id="90d1f-121">Examples</span></span>  
 <span data-ttu-id="90d1f-122">다음 코드 예제를 사용하려면 애플리케이션을 만들 프로그래밍 환경, 프로그래밍 템플릿 및 프로그래밍 언어를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-122">For the following code examples, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="90d1f-123">자세한 내용은 visual studio [.net에서 VISUAL BASIC SMO 프로젝트 만들기](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) 및 visual [Studio .Net에서 VISUAL C&#35; smo 프로젝트 만들기](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="90d1f-123">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="modifying-sql-server-configuration-options-in-visual-basic"></a><span data-ttu-id="90d1f-124">Visual Basic에서 SQL Server 구성 옵션 수정</span><span class="sxs-lookup"><span data-stu-id="90d1f-124">Modifying SQL Server Configuration Options in Visual Basic</span></span>  
 <span data-ttu-id="90d1f-125">코드 예제는 Visual Basic .NET에서 구성 옵션을 업데이트하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-125">The code example shows how to update a configuration option in Visual Basic .NET.</span></span> <span data-ttu-id="90d1f-126">또한 지정된 구성 옵션에 대한 최대값 및 최소값 정보를 검색하고 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-126">It also retrieves and displays information about maximum and minimum values for the specified configuration option.</span></span> <span data-ttu-id="90d1f-127">마지막으로 프로그램에서 사용자에게 변경이 동적으로 이루어졌는지, 또는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스가 다시 시작될 때까지 변경 내용이 저장되는지를 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-127">Finally, the program informs the user if the change has been made dynamically, or if it is stored until the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is restarted.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBConfigure2](SMO How to#SMO_VBConfigure2)]  -->  
  
## <a name="modifying-sql-server-settings-in-visual-basic"></a><span data-ttu-id="90d1f-128">Visual Basic에서 SQL Server 설정 수정</span><span class="sxs-lookup"><span data-stu-id="90d1f-128">Modifying SQL Server Settings in Visual Basic</span></span>  
 <span data-ttu-id="90d1f-129">코드 예에서는 및의 인스턴스에 대 한 정보를 표시 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <xref:Microsoft.SqlServer.Management.Smo.Information> <xref:Microsoft.SqlServer.Management.Smo.Settings> 하 고 및 개체 속성의 설정을 수정 <xref:Microsoft.SqlServer.Management.Smo.Settings> <xref:Microsoft.SqlServer.Management.Smo.UserOptions> 합니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-129">The code example displays information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in <xref:Microsoft.SqlServer.Management.Smo.Information> and <xref:Microsoft.SqlServer.Management.Smo.Settings>, and modifies settings in <xref:Microsoft.SqlServer.Management.Smo.Settings> and <xref:Microsoft.SqlServer.Management.Smo.UserOptions>object properties.</span></span>  
  
 <span data-ttu-id="90d1f-130">이 예에서 <xref:Microsoft.SqlServer.Management.Smo.UserOptions> 개체 및 <xref:Microsoft.SqlServer.Management.Smo.Settings> 개체에는 모두 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-130">In the example the <xref:Microsoft.SqlServer.Management.Smo.UserOptions> object and the <xref:Microsoft.SqlServer.Management.Smo.Settings> object both have an <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> method.</span></span> <span data-ttu-id="90d1f-131">이들에 대한 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> 메서드를 개별적으로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-131">You can run the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> methods for these individually.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBConfigure1](SMO How to#SMO_VBConfigure1)]  -->  
  
## <a name="modifying-sql-server-settings-in-visual-c"></a><span data-ttu-id="90d1f-132">Visual C#에서 SQL Server 설정 수정</span><span class="sxs-lookup"><span data-stu-id="90d1f-132">Modifying SQL Server Settings in Visual C#</span></span>  
 <span data-ttu-id="90d1f-133">코드 예에서는 및의 인스턴스에 대 한 정보를 표시 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <xref:Microsoft.SqlServer.Management.Smo.Information> <xref:Microsoft.SqlServer.Management.Smo.Settings> 하 고 및 개체 속성의 설정을 수정 <xref:Microsoft.SqlServer.Management.Smo.Settings> <xref:Microsoft.SqlServer.Management.Smo.UserOptions> 합니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-133">The code example displays information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in <xref:Microsoft.SqlServer.Management.Smo.Information> and <xref:Microsoft.SqlServer.Management.Smo.Settings>, and modifies settings in <xref:Microsoft.SqlServer.Management.Smo.Settings> and <xref:Microsoft.SqlServer.Management.Smo.UserOptions>object properties.</span></span>  
  
 <span data-ttu-id="90d1f-134">이 예에서 <xref:Microsoft.SqlServer.Management.Smo.UserOptions> 개체 및 <xref:Microsoft.SqlServer.Management.Smo.Settings> 개체에는 모두 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-134">In the example the <xref:Microsoft.SqlServer.Management.Smo.UserOptions> object and the <xref:Microsoft.SqlServer.Management.Smo.Settings> object both have an <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> method.</span></span> <span data-ttu-id="90d1f-135">이들에 대한 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> 메서드를 개별적으로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-135">You can run the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> methods for these individually.</span></span>  
  
 `//Connect to the local, default instance of SQL Server.`  
  
```csharp
{  
            Server srv = new Server();  
            //Display all the configuration options.   
  
            foreach (ConfigProperty p in srv.Configuration.Properties)  
            {  
                Console.WriteLine(p.DisplayName);  
            }  
            Console.WriteLine("There are " + srv.Configuration.Properties.Count.ToString() + " configuration options.");  
            //Display the maximum and minimum values for ShowAdvancedOptions.   
            int min = 0;  
            int max = 0;  
            min = srv.Configuration.ShowAdvancedOptions.Minimum;  
            max = srv.Configuration.ShowAdvancedOptions.Maximum;  
            Console.WriteLine("Minimum and Maximum values are " + min + " and " + max + ".");  
            //Modify the value of ShowAdvancedOptions and run the Alter method.   
            srv.Configuration.ShowAdvancedOptions.ConfigValue = 0;  
            srv.Configuration.Alter();  
            //Display when the change takes place according to the IsDynamic property.   
            if (srv.Configuration.ShowAdvancedOptions.IsDynamic == true)  
            {  
                Console.WriteLine("Configuration option has been updated.");  
            }  
            else  
            {  
                Console.WriteLine("Configuration option will be updated when SQL Server is restarted.");  
            }  
        }  
```  
  
## <a name="modifying-sql-server-settings-in-powershell"></a><span data-ttu-id="90d1f-136">PowerShell에서 SQL Server 설정 수정</span><span class="sxs-lookup"><span data-stu-id="90d1f-136">Modifying SQL Server Settings in PowerShell</span></span>  
 <span data-ttu-id="90d1f-137">코드 예에서는 및의 인스턴스에 대 한 정보를 표시 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <xref:Microsoft.SqlServer.Management.Smo.Information> <xref:Microsoft.SqlServer.Management.Smo.Settings> 하 고 및 개체 속성의 설정을 수정 <xref:Microsoft.SqlServer.Management.Smo.Settings> <xref:Microsoft.SqlServer.Management.Smo.UserOptions> 합니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-137">The code example displays information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in <xref:Microsoft.SqlServer.Management.Smo.Information> and <xref:Microsoft.SqlServer.Management.Smo.Settings>, and modifies settings in <xref:Microsoft.SqlServer.Management.Smo.Settings> and <xref:Microsoft.SqlServer.Management.Smo.UserOptions>object properties.</span></span>  
  
 <span data-ttu-id="90d1f-138">이 예에서 <xref:Microsoft.SqlServer.Management.Smo.UserOptions> 개체 및 <xref:Microsoft.SqlServer.Management.Smo.Settings> 개체에는 모두 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-138">In the example the <xref:Microsoft.SqlServer.Management.Smo.UserOptions> object and the <xref:Microsoft.SqlServer.Management.Smo.Settings> object both have an <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> method.</span></span> <span data-ttu-id="90d1f-139">이들에 대한 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> 메서드를 개별적으로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-139">You can run the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> methods for these individually.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = Get-Item default  
  
#Display information about the instance of SQL Server in Information and Settings.  
"OS Version = " + $srv.Information.OSVersion  
"State = "+ $srv.Settings.State.ToString()  
  
#Display information specific to the current user in UserOptions.  
"Quoted Identifier support = " + $srv.UserOptions.QuotedIdentifier  
  
#Modify server settings in Settings.  
$srv.Settings.LoginMode = [Microsoft.SqlServer.Management.SMO.ServerLoginMode]::Integrated  
  
#Modify settings specific to the current connection in UserOptions.  
$srv.UserOptions.AbortOnArithmeticErrors = $true  
  
#Run the Alter method to make the changes on the instance of SQL Server.  
$srv.Alter()  
```  
  
## <a name="modifying-sql-server-configuration-options-in-powershell"></a><span data-ttu-id="90d1f-140">PowerShell에서 SQL Server 구성 옵션 수정</span><span class="sxs-lookup"><span data-stu-id="90d1f-140">Modifying SQL Server Configuration Options in PowerShell</span></span>  
 <span data-ttu-id="90d1f-141">코드 예제는 Visual Basic .NET에서 구성 옵션을 업데이트하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-141">The code example shows how to update a configuration option in Visual Basic .NET.</span></span> <span data-ttu-id="90d1f-142">또한 지정된 구성 옵션에 대한 최대값 및 최소값 정보를 검색하고 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-142">It also retrieves and displays information about maximum and minimum values for the specified configuration option.</span></span> <span data-ttu-id="90d1f-143">마지막으로 프로그램에서 사용자에게 변경이 동적으로 이루어졌는지, 또는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스가 다시 시작될 때까지 변경 내용이 저장되는지를 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="90d1f-143">Finally, the program informs the user if the change has been made dynamically, or if it is stored until the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is restarted.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance replace LocalMachine with the physical server  
cd \sql\LocalMachine  
$svr = Get-Item default  
  
#enumerate its properties  
foreach ($Item in $Svr.Configuration.Properties)   
{  
 $Item.DisplayName  
}  
  
"There are " + $svr.Configuration.Properties.Count.ToString() + " configuration options."  
  
#Display the maximum and minimum values for ShowAdvancedOptions.  
$min = $svr.Configuration.ShowAdvancedOptions.Minimum  
$max = $svr.Configuration.ShowAdvancedOptions.Maximum  
"Minimum and Maximum values are " + $min.ToString() + " and " + $max.ToString() + "."  
  
#Modify the value of ShowAdvancedOptions and run the Alter method.  
$svr.Configuration.ShowAdvancedOptions.ConfigValue = 0  
$svr.Configuration.Alter()  
  
#Display when the change takes place according to the IsDynamic property.  
If ($svr.Configuration.ShowAdvancedOptions.IsDynamic -eq $true)  
 {
   "Configuration option has been updated."  
 }  
Else  
 {  
    "Configuration option will be updated when SQL Server is restarted."  
 }  
```  
