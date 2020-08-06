---
title: Hello World Ready 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: 1cb94266-f702-4a57-a1ae-689a89c98757
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7cc3088af258962a4cec615214147d1f4f09c431
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742511"
---
# <a name="hello-world-ready-sample"></a><span data-ttu-id="37693-102">Hello World Ready 예제</span><span class="sxs-lookup"><span data-stu-id="37693-102">Hello World Ready Sample</span></span>
  <span data-ttu-id="37693-103">Hello World Ready 예제는 간단한 World Ready CLR(공용 언어 런타임) 통합 기반 저장 프로시저 만들기, 배포 및 테스트와 관련된 기본 작업을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="37693-103">The Hello World Ready sample demonstrates the basic operations that are involved in creating, deploying, and testing a simple world ready common language runtime (CLR) integration-based stored procedure.</span></span> <span data-ttu-id="37693-104">World Ready 구성 요소는 구성 요소의 원본 코드를 변경할 필요 없이 세계 곳곳의 다양한 시장에서 다양한 언어로 쉽게 지역화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37693-104">A world-ready component can be easily localized into different languages for different markets around the world without changing the component's source code.</span></span> <span data-ttu-id="37693-105">또한 이 예제에서는 저장 프로시저에 의해 동적으로 생성되고 클라이언트로 반환되는 레코드 및 출력 매개 변수를 통해 데이터를 반환하는 방법을 보여 줍니다. 이 예제는 Hello World 예제와 거의 동일하지만 훨씬 더 쉽고 안전하게 이 애플리케이션을 지역화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37693-105">This sample also demonstrates how to return data through an output parameter and through a record, which is dynamically constructed by the stored procedure and returned to the client.This sample is almost identical to the Hello World Sample except that it is much easier and safer to localize this application.</span></span> <span data-ttu-id="37693-106">지역화된 텍스트를 변경하려면 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37693-106">To change localized text requires the following:</span></span>  
  
1.  <span data-ttu-id="37693-107">XML 파일 변경 (.`resx`</span><span class="sxs-lookup"><span data-stu-id="37693-107">Changing an XML file (the .`resx`</span></span> <span data-ttu-id="37693-108">파일)에 대 한 리소스 디렉터리의 특정 문화권</span><span class="sxs-lookup"><span data-stu-id="37693-108">file) for the particular culture in the resources directory</span></span>  
  
2.  <span data-ttu-id="37693-109">`resgen`을 사용하여 해당 culture의 리소스 파일 빌드</span><span class="sxs-lookup"><span data-stu-id="37693-109">Building the culture's resources file by using `resgen`</span></span>  
  
3.  <span data-ttu-id="37693-110">해당 culture에 대한 업데이트된 위성 DLL 빌드</span><span class="sxs-lookup"><span data-stu-id="37693-110">Building the updated satellite DLL for that culture</span></span>  
  
4.  <span data-ttu-id="37693-111">SQL Server에서 해당 어셈블리 삭제 및 추가</span><span class="sxs-lookup"><span data-stu-id="37693-111">Dropping and adding that assembly in SQL Server</span></span>  
  
 <span data-ttu-id="37693-112">CLR 저장 프로시저 자체에 대한 원본 코드 및 어셈블리는 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37693-112">The source code and assembly for the CLR stored procedure itself does not change.</span></span> <span data-ttu-id="37693-113">리소스 어셈블리를 컴파일하고 연결하는 방법을 보여 주는 `build.cmd` 스크립트가 제공됩니다. 애플리케이션의 원본 코드는 현재 실행 중인 어셈블리에 기반하는 리소스 관리자를 만들지만 저장 프로시저를 포함하는 DLL에 culture 중립 리소스를 포함해야 할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="37693-113">A `build.cmd` script is provided which demonstrates how to compile and link the resource assemblies.Although the source code for the application creates a resource manager based the currently executing assembly, you do not have to embed the culture neutral resources in the DLL that contains the stored procedure.</span></span> <span data-ttu-id="37693-114">`System.Resources.NeutralResourcesLanguage attribute` 특성이 있으면 위성 DLL에 culture 중립 리소스가 존재할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37693-114">The `System.Resources.NeutralResourcesLanguage attribute` permits the culture-neutral resources to exist in a satellite DLL.</span></span> <span data-ttu-id="37693-115">이 경우 지역화된 텍스트를 추가 또는 변경할 때 CLR 저장 프로시저가 포함된 기본 DLL을 변경할 필요가 없도록 별도의 DLL을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="37693-115">It is much better to use a separate DLL for this purpose so that when localized text needs to be added or changed, the primary DLL that contains the CLR stored procedure does not have to be changed.</span></span> <span data-ttu-id="37693-116">특히 열 및 기타 종속성을 갖고 있어 유형을 삭제하고 다시 추가하기가 어려운 CLR 사용자 정의 형식의 경우 이 방법이 유용합니다. 일반적으로 위성 DLL 버전은 주 어셈블리 버전과 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37693-116">This is especially useful for CLR user-defined types that might have columns and other dependencies which would make it difficult to drop and re-add the type.Ordinarily, the satellite DLL versions must be identical to the main assembly version.</span></span> <span data-ttu-id="37693-117">하지만 `SatelliteContractVersion` 특성을 사용하여 위성 어셈블리를 업데이트하지 않고 주 어셈블리만 업데이트하도록 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37693-117">However, you can use the `SatelliteContractVersion` attribute to allow the main assembly to be updated without updating the satellite assemblies too.</span></span> <span data-ttu-id="37693-118">자세한 내용은 Microsoft .NET 설명서에서 `ResourceManager` 클래스를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="37693-118">For more information, see the `ResourceManager` class in the Microsoft .NET documentation.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="37693-119">전제 조건</span><span class="sxs-lookup"><span data-stu-id="37693-119">Prerequisites</span></span>  
 <span data-ttu-id="37693-120">이 예제는 SQL Server 2005 이상 버전에서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="37693-120">This sample works only with SQL Server 2005 and later versions.</span></span>  
  
 <span data-ttu-id="37693-121">이 프로젝트를 만들고 실행하려면 다음 소프트웨어가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37693-121">To create and run this project the following the following software must be installed:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="37693-122">또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express</span><span class="sxs-lookup"><span data-stu-id="37693-122">or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express.</span></span> <span data-ttu-id="37693-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express 설명서 및 예제 [웹 사이트](https://www.microsoft.com/sql-server/sql-server-editions-express)에서 무료로 구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37693-123">You can obtain [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express free of charge from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express Documentation and Samples [Web site](https://www.microsoft.com/sql-server/sql-server-editions-express)</span></span>  
  
-   <span data-ttu-id="37693-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개발자 [웹 사이트](https://go.microsoft.com/fwlink/?linkid=62796)에서 제공되는 AdventureWorks 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="37693-124">The AdventureWorks database that is available at the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Developer [Web site](https://go.microsoft.com/fwlink/?linkid=62796)</span></span>  
  
-   <span data-ttu-id="37693-125">.NET Framework SDK 2.0 이상 또는 Microsoft Visual Studio 2005 이상.</span><span class="sxs-lookup"><span data-stu-id="37693-125">.NET Framework SDK 2.0 or later or Microsoft Visual Studio 2005 or later.</span></span> <span data-ttu-id="37693-126">.NET Framework SDK는 무료로 구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37693-126">You can obtain .NET Framework SDK free of charge.</span></span>  
  
-   <span data-ttu-id="37693-127">또한 다음 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37693-127">In addition, the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="37693-128">사용하고 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대해 CLR 통합이 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37693-128">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using must have CLR integration enabled.</span></span>  
  
-   <span data-ttu-id="37693-129">CLR 통합을 설정하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="37693-129">In order to enable CLR integration, perform the following steps:</span></span>  
  
    #### <a name="enabling-clr-integration"></a><span data-ttu-id="37693-130">CLR 통합 사용</span><span class="sxs-lookup"><span data-stu-id="37693-130">Enabling CLR Integration</span></span>  
  
    -   <span data-ttu-id="37693-131">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="37693-131">Execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] commands:</span></span>  
  
     `sp_configure 'clr enabled', 1`  
  
     `GO`  
  
     `RECONFIGURE`  
  
     `GO`  
  
    > [!NOTE]  
    >  <span data-ttu-id="37693-132">CLR을 사용하도록 설정하려면 `ALTER SETTINGS` 서버 수준 사용 권한이 있어야 합니다. 이 사용 권한은 `sysadmin` 및 `serveradmin` 고정 서버 역할의 멤버가 암시적으로 소유합니다.</span><span class="sxs-lookup"><span data-stu-id="37693-132">To enable CLR, you must have `ALTER SETTINGS` server level permission, which is implicitly held by members of the `sysadmin` and `serveradmin` fixed server roles.</span></span>  
  
-   <span data-ttu-id="37693-133">사용하고 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 AdventureWorks 데이터베이스를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37693-133">The AdventureWorks database must be installed on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using.</span></span>  
  
-   <span data-ttu-id="37693-134">사용 중인 인스턴스의 관리자가 아닌 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치를 완료 하려면 관리자에 게 **createassembly** 권한을 부여 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37693-134">If you are not an administrator for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using, you must have an administrator grant you **CreateAssembly**  permission to complete the installation.</span></span>  
  
## <a name="building-the-sample"></a><span data-ttu-id="37693-135">예제 빌드</span><span class="sxs-lookup"><span data-stu-id="37693-135">Building the Sample</span></span>  
  
#### <a name="create-and-run-the-sample-by-using-the-following-instructions"></a><span data-ttu-id="37693-136">다음 지침을 사용하여 예제를 만들고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="37693-136">Create and run the sample by using the following instructions:</span></span>  
  
1.  <span data-ttu-id="37693-137">Visual Studio 또는 .NET Framework 명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="37693-137">Open a Visual Studio or .NET Framework command prompt.</span></span>  
  
2.  <span data-ttu-id="37693-138">필요한 경우 예제에 대한 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="37693-138">If necessary, create a directory for your sample.</span></span> <span data-ttu-id="37693-139">이 예에서는 C:\MySample을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="37693-139">For this example, we will use C:\MySample.</span></span>  
  
3.  <span data-ttu-id="37693-140">c:\MySample에서 `HelloWorld.vb`(Visual Basic 예제용) 또는 `HelloWorld.cs`(C# 예제용)를 만들고 적합한 Visual Basic 또는 C# 예제 코드(아래)를 파일에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="37693-140">In c:\MySample, create `HelloWorld.vb` (for the Visual Basic sample) or `HelloWorld.cs` (for the C# sample) and copy the appropriate Visual Basic or C# sample code (below) into the file.</span></span>  
  
4.  <span data-ttu-id="37693-141">c:\MySample에서 `messages.resx` 파일을 만들고 예제 코드를 파일에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="37693-141">In c:\MySample, create the file `messages.resx` and copy the sample code into the file.</span></span>  
  
5.  <span data-ttu-id="37693-142">C:\MySample에서 `messages.de.resx` `messages.resx` 줄을 변경한 후 파일을로 저장 하 여 파일을 만듭니다. `messages.de.resx`</span><span class="sxs-lookup"><span data-stu-id="37693-142">In c:\MySample, create the file `messages.de.resx` by saving the file `messages.resx` as `messages.de.resx` after changing the line</span></span>  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   <span data-ttu-id="37693-143">아래와 같이 읽으려면</span><span class="sxs-lookup"><span data-stu-id="37693-143">To read</span></span>  
  
    -   `<value xml:space="preserve">Hallo Welt!</value>`  
  
6.  <span data-ttu-id="37693-144">C:\MySample에서 `messages.es.resx` `messages.resx` 줄을 변경한 후 파일을로 저장 하 여 파일을 만듭니다. `messages.es.resx`</span><span class="sxs-lookup"><span data-stu-id="37693-144">In c:\MySample, create the file `messages.es.resx` by saving the file `messages.resx` as `messages.es.resx` after changing the line</span></span>  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   <span data-ttu-id="37693-145">아래와 같이 읽으려면</span><span class="sxs-lookup"><span data-stu-id="37693-145">To read</span></span>  
  
    -   `<value xml:space="preserve">Hola a todos</value>`  
  
7.  <span data-ttu-id="37693-146">C:\MySample에서 `messages.fr.resx` `messages.resx` 줄을 변경한 후 파일을로 저장 하 여 파일을 만듭니다. `messages.fr.resx`</span><span class="sxs-lookup"><span data-stu-id="37693-146">In c:\MySample, create the file `messages.fr.resx` by saving the file `messages.resx` as `messages.fr.resx` after changing the line</span></span>  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   <span data-ttu-id="37693-147">아래와 같이 읽으려면</span><span class="sxs-lookup"><span data-stu-id="37693-147">To read</span></span>  
  
    -   `<value xml:space="preserve">BonjourÂ !</value>`  
  
8.  <span data-ttu-id="37693-148">C:\MySample에서 `messages.fr-FR.resx` `messages.resx` 줄을 변경한 후 파일을로 저장 하 여 파일을 만듭니다. `messages.fr-FR.resx`</span><span class="sxs-lookup"><span data-stu-id="37693-148">In c:\MySample, create the file `messages.fr-FR.resx` by saving the file `messages.resx` as `messages.fr-FR.resx` after changing the line</span></span>  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   <span data-ttu-id="37693-149">아래와 같이 읽으려면</span><span class="sxs-lookup"><span data-stu-id="37693-149">To read</span></span>  
  
    -   `<value xml:space="preserve">Bonjour de France!</value>`  
  
9. <span data-ttu-id="37693-150">C:\MySample에서 `messages.it.resx` `messages.resx` 줄을 변경한 후 파일을로 저장 하 여 파일을 만듭니다. `messages.it.resx`</span><span class="sxs-lookup"><span data-stu-id="37693-150">In c:\MySample, create the file `messages.it.resx` by saving the file `messages.resx` as `messages.it.resx` after changing the line</span></span>  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   <span data-ttu-id="37693-151">아래와 같이 읽으려면</span><span class="sxs-lookup"><span data-stu-id="37693-151">To read</span></span>  
  
    -   `<value xml:space="preserve">Buongiorno</value>`  
  
10. <span data-ttu-id="37693-152">C:\MySample에서 `messages.ja.resx` `messages.resx` 줄을 변경한 후 파일을로 저장 하 여 파일을 만듭니다. `messages.ja.resx`</span><span class="sxs-lookup"><span data-stu-id="37693-152">In c:\MySample, create the file `messages.ja.resx` by saving the file `messages.resx` as `messages.ja.resx` after changing the line</span></span>  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   <span data-ttu-id="37693-153">아래와 같이 읽으려면</span><span class="sxs-lookup"><span data-stu-id="37693-153">To read</span></span>  
  
    -   <span data-ttu-id="37693-154">`<value xml:space="preserve">` `ã"ã‚"ã«ã¡ã¯</value>`</span><span class="sxs-lookup"><span data-stu-id="37693-154">`<value xml:space="preserve">` `ã"ã‚"ã«ã¡ã¯</value>`</span></span>  
  
11. <span data-ttu-id="37693-155">c:\MySample에서 `build.com` 파일을 만들고 예제 코드를 파일에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="37693-155">In c:\MySample, create the file `build.com` and copy the sample code into the file</span></span>  
  
12. <span data-ttu-id="37693-156">명령 프롬프트에서 파일 빌드를 실행하여 위성 어셈블리를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="37693-156">Build the satellite assembles by executing the file build at the command prompt.</span></span>  
  
13. <span data-ttu-id="37693-157">다음 중 하나를 실행하여 명령줄 프롬프트에서 예제 코드를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="37693-157">Compile the sample code from the command line prompt by executing the one of the following:</span></span>  
  
    -   `Vbc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Xml.dll /out:HelloWorldReady.dll /target:library HelloWorld.vb`  
  
    -   `Csc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.XML.dll /out:HelloWorldReady.dll /target:library Hello.csCopy the tsql installation code into a file and save it as Install.sql in the sample directory.`  
  
14. <span data-ttu-id="37693-158">예제가 `C:\MySample\`이외의 디렉터리에 설치된 경우 해당 위치를 가리키도록 표시된 대로 `Install.sql` 파일을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="37693-158">If the sample is installed in a directory other then `C:\MySample\`, edit the file `Install.sql` as indicated to point to that location.</span></span>  
  
15. <span data-ttu-id="37693-159">다음을 실행하여 어셈블리 및 저장 프로시저를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="37693-159">Deploy the assembly and stored procedure by executing</span></span>  
  
    -   `sqlcmd -E -I -i install.sql`  
  
16. <span data-ttu-id="37693-160">[!INCLUDE[tsql](../../includes/tsql-md.md)] 테스트 명령 스크립트를 파일에 복사하고 해당 파일을 예제 디렉터리에 `test.sql` 로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="37693-160">Copy [!INCLUDE[tsql](../../includes/tsql-md.md)] test command script into a file and save it as `test.sql` in the sample directory.</span></span>  
  
17. <span data-ttu-id="37693-161">다음 명령으로 테스트 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="37693-161">Execute the test script with the following command</span></span>  
  
    -   `sqlcmd -E -I -i test.sql`  
  
18. <span data-ttu-id="37693-162">[!INCLUDE[tsql](../../includes/tsql-md.md)] 정리 스크립트를 파일에 복사하고 해당 파일을 예제 디렉터리에 `cleanup.sql` 로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="37693-162">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] cleanup script into a file and save it as `cleanup.sql` in the sample directory.</span></span>  
  
19. <span data-ttu-id="37693-163">다음 명령으로 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="37693-163">Execute the script with the  following command</span></span>  
  
    -   `sqlcmd -E -I -i cleanup.sql`  
  
## <a name="sample-code"></a><span data-ttu-id="37693-164">샘플 코드</span><span class="sxs-lookup"><span data-stu-id="37693-164">Sample Code</span></span>  
 <span data-ttu-id="37693-165">다음은 이 예제에 대한 코드 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="37693-165">The following are the code listings for this sample.</span></span>  
  
 <span data-ttu-id="37693-166">C#</span><span class="sxs-lookup"><span data-stu-id="37693-166">C#</span></span>  
  
```  
using System;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
using System.Globalization;  
using System.Threading;  
using System.Resources;  
using System.Reflection;  
using System.Runtime.CompilerServices;  
  
[assembly: System.Resources.NeutralResourcesLanguage("", System.Resources.UltimateResourceFallbackLocation.Satellite)]  
[assembly: System.Security.Permissions.SecurityPermissionAttribute(System.Security.Permissions.SecurityAction.RequestMinimum)]  
[assembly: System.Runtime.ConstrainedExecution.ReliabilityContract(System.Runtime.ConstrainedExecution.Consistency.MayCorruptInstance, System.Runtime.ConstrainedExecution.Cer.None)]  
  
    public sealed partial class StoredProcedures  
    {  
        private StoredProcedures()  
        {  
        }  
  
        [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1021:AvoidOutParameters"), Microsoft.SqlServer.Server.SqlProcedure]  
        public static void HelloWorldReady(string culture, out string greeting)  
        {  
ResourceManager rm   
= new ResourceManager("Messages",   
Assembly.GetExecutingAssembly());  
  
string message = rm.GetString("HelloWorld", CultureInfo.GetCultureInfo(culture));  
  
            Microsoft.SqlServer.Server.SqlMetaData columnInfo  
                = new Microsoft.SqlServer.Server.SqlMetaData("Column1", SqlDbType.NVarChar, 24);  
            SqlDataRecord greetingRecord  
                = new SqlDataRecord(new Microsoft.SqlServer.Server.SqlMetaData[] { columnInfo });  
            greetingRecord.SetString(0, message);  
            SqlContext.Pipe.Send(greetingRecord);  
            greeting = message;  
        }  
    }  
  
```  
  
 <span data-ttu-id="37693-167">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="37693-167">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Globalization  
Imports System.Resources  
Imports System.Reflection  
Imports System.Runtime.InteropServices  
<Assembly: AssemblyVersion("1.0.*")>   
<Assembly: System.Runtime.InteropServices.ComVisible(False)>   
<Assembly: System.CLSCompliant(True)>   
<Assembly: System.Resources.NeutralResourcesLanguage("", System.Resources.UltimateResourceFallbackLocation.Satellite)>   
<Assembly: System.Security.Permissions.SecurityPermissionAttribute(System.Security.Permissions.SecurityAction.RequestMinimum)>   
<Assembly: System.Runtime.ConstrainedExecution.ReliabilityContract(System.Runtime.ConstrainedExecution.Consistency.WillNotCorruptState, Runtime.ConstrainedExecution.Cer.None)>   
  
Partial Public NotInheritable Class StoredProcedures  
    Private Sub New()  
    End Sub  
    <Microsoft.SqlServer.Server.SqlProcedure()> _  
    Public Shared Sub HelloWorldReady(ByVal culture As String, ByRef greeting As String)  
        Dim rm As New ResourceManager("Messages", Assembly.GetExecutingAssembly())  
        Dim message As String = rm.GetString("HelloWorld", CultureInfo.GetCultureInfo(culture))  
        Dim columnInfo As New Microsoft.SqlServer.Server.SqlMetaData("Column1", _  
            SqlDbType.NVarChar, 24)  
        Dim greetingRecord As New SqlDataRecord(New  _  
            Microsoft.SqlServer.Server.SqlMetaData() {columnInfo})  
        greetingRecord.SetString(0, message)  
        SqlContext.Pipe.Send(greetingRecord)  
        greeting = message  
    End Sub  
End Class  
  
```  
  
 <span data-ttu-id="37693-168">이는 위성 어셈블리를 빌드하는 `build.com`입니다.</span><span class="sxs-lookup"><span data-stu-id="37693-168">This is `build.com`, which builds the satellite assemblies.</span></span>  
  
```  
resgen Messages.resx  
resgen Messages.de.resx  
resgen Messages.es.resx  
resgen Messages.fr.resx  
resgen Messages.fr-Fr.resx  
resgen Messages.it.resx  
resgen Messages.ja.resx  
if not exist de/ mkdir de  
if not exist es/ mkdir es  
if not exist fr/ mkdir fr  
if not exist fr-FR/ mkdir fr-FR  
if not exist it/ mkdir it  
if not exist ja/ mkdir ja  
al /t:lib /culture:de /embed:Messages.de.resources /out:de\HelloWorldReady.resources.dll  
al /t:lib /culture:es /embed:Messages.es.resources /out:es\HelloWorldReady.resources.dll  
al /t:lib /culture:fr /embed:Messages.fr.resources /out:fr\HelloWorldReady.resources.dll  
al /t:lib /culture:fr-FR /embed:Messages.fr-FR.resources /out:fr-FR\HelloWorldReady.resources.dll  
al /t:lib /culture:it /embed:Messages.it.resources /out:it\HelloWorldReady.resources.dll  
al /t:lib /culture:ja /embed:Messages.ja.resources /out:ja\HelloWorldReady.resources.dll  
al /t:lib /culture:"" /embed:Messages.resources /out:HelloWorldReady.resources.dll  
```  
  
 <span data-ttu-id="37693-169">이는 어셈블리를 배포하고 데이터베이스 내에서 저장 프로시저를 만드는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 설치 스크립트(`Install.sql`)입니다.</span><span class="sxs-lookup"><span data-stu-id="37693-169">This is the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation script (`Install.sql`), which deploys the assemblies and creates the stored procedure within the database.</span></span>  
  
```  
USE AdventureWorks  
GO  
  
-- Drop existing sproc and assembly if any.  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorldReady')  
DROP PROCEDURE usp_HelloWorldReady;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady')  
DROP ASSEMBLY HelloWorldReady;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.neutral')  
DROP ASSEMBLY [HelloWorldReady.resources.neutral]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.de')  
DROP ASSEMBLY [HelloWorldReady.resources.de]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.es')  
DROP ASSEMBLY [HelloWorldReady.resources.es]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.fr')  
DROP ASSEMBLY [HelloWorldReady.resources.fr]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.fr-FR')  
DROP ASSEMBLY [HelloWorldReady.resources.fr-FR]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.it')  
DROP ASSEMBLY [HelloWorldReady.resources.it]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.ja')  
DROP ASSEMBLY [HelloWorldReady.resources.ja]  
GO  
  
DECLARE @SamplesPath nvarchar(1024)  
-- You may need to modify the value of this variable if you have installed the sample someplace other than the default location.  
Set @SamplesPath = N'C:\MySample\'  
  
-- Add the assembly and CLR integration based stored procedure  
  
CREATE ASSEMBLY HelloWorldReady  
FROM @SamplesPath + 'HelloWorldReady.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.neutral]  
FROM @SamplesPath + 'HelloWorldReady.resources.dll'  
WITH permission_set = Safe;   
  
CREATE ASSEMBLY [HelloWorldReady.resources.de]  
FROM @SamplesPath + '\de\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.es]  
FROM @SamplesPath + '\es\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.fr]  
FROM @SamplesPath + '\fr\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.fr-FR]  
FROM @SamplesPath + '\fr-FR\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.it]  
FROM @SamplesPath + '\it\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.ja]  
FROM @SamplesPath + '\ja\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
GO  
  
CREATE PROCEDURE usp_HelloWorldReady  
(  
@Culture NVarchar(12),  
@Greeting NVarchar(24) OUTPUT  
)  
AS EXTERNAL NAME HelloWorldReady.StoredProcedures.HelloWorldReady;  
GO  
  
USE master;  
GO  
```  
  
 <span data-ttu-id="37693-170">이는 각 로캘에서 함수를 실행하여 예제를 테스트하는 `test.sql`입니다.</span><span class="sxs-lookup"><span data-stu-id="37693-170">This is `test.sql`, which tests the sample by executing the functions on each locale.</span></span>  
  
```  
USE AdventureWorks  
GO  
  
DECLARE @GreetingDe nvarchar(24);  
DECLARE @GreetingDe_CH nvarchar(24);  
DECLARE @GreetingEn nvarchar(24);  
DECLARE @GreetingEs nvarchar(24);  
DECLARE @GreetingFr nvarchar(24);  
DECLARE @GreetingFr_FR nvarchar(24);  
DECLARE @GreetingIt nvarchar(24);  
DECLARE @GreetingJa nvarchar(24);  
  
--German as spoken anywhere in the world (the neutral German culture)  
EXEC usp_HelloWorldReady 'de', @GreetingDe OUTPUT;  
--German as spoken in Switzerland.  Because we don't have a specific assembly  
--for this case, the .NET Framework will automatically fall back to the neutral German culture DLL.  
EXEC usp_HelloWorldReady 'de-CH', @GreetingDe_CH OUTPUT;  
EXEC usp_HelloWorldReady 'en', @GreetingEn OUTPUT;  
EXEC usp_HelloWorldReady 'es', @GreetingEs OUTPUT;  
--French as spoken anywhere in the world (the neutral French culture)  
EXEC usp_HelloWorldReady 'fr', @GreetingFr OUTPUT  
--French as spoken in France.  Since we do have a specific assembly for this case, a specific   
--greeting is provided from that DLL.  The neutral French culture DLL is not used in this case.  
EXEC usp_HelloWorldReady 'fr-FR', @GreetingFr_FR OUTPUT  
EXEC usp_HelloWorldReady 'it', @GreetingIt OUTPUT;  
EXEC usp_HelloWorldReady 'ja', @GreetingJa OUTPUT;  
  
SELECT @GreetingDe AS OUTPUT_PARAMETER_DE;  
SELECT @GreetingDe_CH AS OUTPUT_PARAMETER_De_CH;  
SELECT @GreetingEn AS OUTPUT_PARAMETER_EN;  
SELECT @GreetingEs AS OUTPUT_PARAMETER_ES;  
SELECT @GreetingFr AS OUTPUT_PARAMETER_FR;  
SELECT @GreetingFr_FR AS OUTPUT_PARAMETER_Fr_FR;  
SELECT @GreetingIt AS OUTPUT_PARAMETER_IT;  
SELECT @GreetingJa AS OUTPUT_PARAMETER_JA;  
  
GO  
```  
  
 <span data-ttu-id="37693-171">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)]은 데이터베이스에서 어셈블리 및 저장 프로시저를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="37693-171">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] removes the assemblies and stored procedure from the database.</span></span>  
  
```  
USE AdventureWorks;  
GO  
  
-- Drop existing sproc and assembly if any.  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorldReady')  
DROP PROCEDURE usp_HelloWorldReady;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady')  
DROP ASSEMBLY HelloWorldReady;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.neutral')  
DROP ASSEMBLY [HelloWorldReady.resources.neutral]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.de')  
DROP ASSEMBLY [HelloWorldReady.resources.de]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.es')  
DROP ASSEMBLY [HelloWorldReady.resources.es]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.fr')  
DROP ASSEMBLY [HelloWorldReady.resources.fr]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.fr-FR')  
DROP ASSEMBLY [HelloWorldReady.resources.fr-FR]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.it')  
DROP ASSEMBLY [HelloWorldReady.resources.it]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.ja')  
DROP ASSEMBLY [HelloWorldReady.resources.ja]  
GO  
  
USE master;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="37693-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="37693-172">See Also</span></span>  
 [<span data-ttu-id="37693-173">공용 언어 런타임 &#40;CLR&#41; 통합에 대한 사용 시나리오 및 예제</span><span class="sxs-lookup"><span data-stu-id="37693-173">Usage Scenarios and Examples for Common Language Runtime &#40;CLR&#41; Integration</span></span>](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  
