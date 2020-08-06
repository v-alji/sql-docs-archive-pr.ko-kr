---
title: 패키지 실행 유틸리티 (DtExecUI) UI 참조 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtexecui.general.f1
- sql12.dts.dtexecui.executionoptions.f1
- sql12.dts.dtexecui.configuration.f1
- sql12.dts.dtexecui.setvalues.f1
- sql12.dts.dtexecui.commandline.f1
- sql12.dts.dtexecui.commandfiles.f1
- sql12.dts.dtexecui.verification.f1
- sql12.dts.dtexecui.datasources.f1
- sql12.dts.dtexecui.reporting.f1
- sql12.dts.dtexecui.logging.f1
helpviewer_keywords:
- DTExecUI utility
ms.assetid: 3d71df39-126b-4c8e-bd77-128bbd5b0887
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 13601983a4ab841a2b64ff8e4fc722fcf5ae496c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652195"
---
# <a name="execute-package-utility-dtexecui-ui-reference"></a><span data-ttu-id="1867d-102">패키지 실행 유틸리티(DtExecUI) UI 참조</span><span class="sxs-lookup"><span data-stu-id="1867d-102">Execute Package Utility (DtExecUI) UI Reference</span></span>
  <span data-ttu-id="1867d-103">**패키지 실행 유틸리티** 를 사용하여 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-103">Use the **Execute Package Utility** to run [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="1867d-104">이 유틸리티는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스, [!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지 저장소 및 파일 시스템의 세 위치 중 하나에 저장된 패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-104">The utility runs packages that are stored in one of three locations: [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store, and the file system.</span></span> <span data-ttu-id="1867d-105">에서 열거나 명령 프롬프트에서를 입력 하 여 열 수 있는이 사용자 인터페이스 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] `dtexecui` 는 **DTExec** 명령 프롬프트 도구를 사용 하 여 패키지를 실행 하는 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-105">This user interface, which can be opened from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or by typing `dtexecui` at a command prompt, is an alternative to running packages by using the **DTExec** command prompt tool.</span></span>  
  
 <span data-ttu-id="1867d-106">패키지는 **dtexecui.exe** 유틸리티와 같은 프로세스로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-106">Packages execute in the same process as the **dtexecui.exe** utility.</span></span> <span data-ttu-id="1867d-107">이 유틸리티는 32비트 도구이므로 패키지는 WOW(Windows on Win32)에서 실행되는 64비트 환경에서 **dtexecui.exe** 를 사용하여 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-107">Because this utility is a 32-bit tool, packages run by using **dtexecui.exe** in a 64-bit environment run in Windows on Win32 (WOW).</span></span> <span data-ttu-id="1867d-108">64비트 컴퓨터에서 dtexecui.exe 유틸리티를 사용하여 명령을 개발하고 테스트하는 경우에는 프로덕션 서버에서 명령을 배포하거나 예약하기 전에 64비트 버전의 **dtexec.exe** 를 사용하여 64비트 모드에서 명령을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-108">When developing and testing commands by using the dtexecui.exe utility on a 64-bit computer, you should test the commands in 64-bit mode by using the 64-bit version of **dtexec.exe** before deploying or scheduling the commands on a production server.</span></span>  
  
 <span data-ttu-id="1867d-109">**패키지 실행 유틸리티** 는 **DTExec** 명령 프롬프트 도구용 그래픽 사용자 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-109">The **Execute Package Utility** is a graphical user interface for the **DTExec** command prompt tool.</span></span> <span data-ttu-id="1867d-110">이 사용자 인터페이스를 사용하면 옵션을 쉽게 구성할 수 있으며 지정한 옵션으로 패키지 실행 시 **DTExec** 명령 프롬프트 도구에 전달되는 명령줄이 자동으로 조합됩니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-110">The user interface makes it easy to configure options and it automatically assembles the command line that is passed to the **DTExec** command prompt tool when you run the package from the specified options.</span></span>  
  
 <span data-ttu-id="1867d-111">**패키지 실행 유틸리티** 를 사용하여 **DTExec** 직접 실행 시 사용하는 명령줄을 조합할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-111">The **Execute Package Utility** can also be used to assemble command lines that you use when running **DTExec** directly.</span></span>  
  
### <a name="to-open-execute-package-utility-in-sql-server-management-studio"></a><span data-ttu-id="1867d-112">SQL Server Management Studio에서 패키지 실행 유틸리티를 열려면</span><span class="sxs-lookup"><span data-stu-id="1867d-112">To open Execute Package Utility in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="1867d-113">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 **보기** 메뉴에서 **개체 탐색기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-113">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Object Explorer**.</span></span>  
  
2.  <span data-ttu-id="1867d-114">개체 탐색기에서 **연결**을 클릭한 후 **Integration Services**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-114">In Object Explorer, click **Connect**, and then click **Integration Services**.</span></span>  
  
3.  <span data-ttu-id="1867d-115">**서버에 연결** 대화 상자의 **서버 이름** 목록에 서버 이름을 입력하고 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-115">In the **Connect to Server** dialog box, enter the server name in the **Server name** list, and then click **Connect**.</span></span>  
  
4.  <span data-ttu-id="1867d-116">**저장된 패키지**폴더 및 하위 폴더를 확장하고 실행할 패키지를 마우스 오른쪽 단추로 클릭한 다음 **패키지 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-116">Expand the **Stored Package**s folder and subfolders, right-click the package you want to run, and then click **Run Package**.</span></span>  
  
### <a name="to-open-the-execute-package-utility-at-the-command-prompt"></a><span data-ttu-id="1867d-117">명령 프롬프트에서 패키지 실행 유틸리티를 열려면</span><span class="sxs-lookup"><span data-stu-id="1867d-117">To open the Execute Package Utility at the Command Prompt</span></span>  
  
-   <span data-ttu-id="1867d-118">명령 프롬프트 창에서 `dtexecui`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-118">In a command prompt window, run `dtexecui`.</span></span>  
  
 <span data-ttu-id="1867d-119">다음 섹션에서는 **패키지 실행 유틸리티** 대화 상자의 페이지에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-119">The following sections describe pages of the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="general-page"></a><span data-ttu-id="1867d-120">일반 페이지</span><span class="sxs-lookup"><span data-stu-id="1867d-120">General Page</span></span>  
 <span data-ttu-id="1867d-121">**패키지 실행 유틸리티** 대화 상자의 **일반** 페이지를 사용하여 패키지 이름과 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-121">Use the **General** page of the **Execute Package Utility** dialog box to specify a package name and location.</span></span>  
  
 <span data-ttu-id="1867d-122">패키지 실행 유틸리티(dtexecui.exe)는 패키지가 원격 서버에 저장되어 있어도 항상 로컬 컴퓨터에서 패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-122">The Execute Package utility (dtexecui.exe) always runs a package on the local computer, even if the package is saved on a remote server.</span></span> <span data-ttu-id="1867d-123">원격 패키지가 원격 서버에 저장된 구성 파일을 사용하면 패키지 실행 유틸리티에서 해당 구성을 찾을 수 없으므로 패키지가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-123">If the remote package uses configuration files that also are saved on the remote server, then the Execute Package utility may not locate the configurations and the package fails.</span></span> <span data-ttu-id="1867d-124">이 문제를 방지하려면 \\\myserver\myfile과 같은 UNC(범용 명명 규칙) 공유 이름을 사용하여 구성을 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-124">To avoid this problem, the configurations must be referenced by using a Universal Naming Convention (UNC) share name like \\\myserver\myfile.</span></span>  
  
### <a name="static-options"></a><span data-ttu-id="1867d-125">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="1867d-125">Static Options</span></span>  
 <span data-ttu-id="1867d-126">**패키지 원본**</span><span class="sxs-lookup"><span data-stu-id="1867d-126">**Package source**</span></span>  
 <span data-ttu-id="1867d-127">다음 옵션을 사용하여 실행할 패키지의 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-127">Specify the location of the package to run, using the following options:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1867d-128">값</span><span class="sxs-lookup"><span data-stu-id="1867d-128">Value</span></span>|<span data-ttu-id="1867d-129">Description</span><span class="sxs-lookup"><span data-stu-id="1867d-129">Description</span></span>|  
|<span data-ttu-id="1867d-130">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="1867d-130">**SQL Server**</span></span>|<span data-ttu-id="1867d-131">패키지가 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 있으면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-131">Select this option when the package resides in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1867d-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 지정하고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증의 사용자 이름과 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-132">Specify an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and provide a user name and password for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="1867d-133">사용자 이름과 암호를 입력할 때마다 명령 프롬프트에 **/USER** _username_ 및 **/PASSWORD** _password_ 옵션이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-133">Each user name and password adds the **/USER** _username_ and **/PASSWORD** _password_ options to the command prompt.</span></span>|  
|<span data-ttu-id="1867d-134">**파일 시스템**</span><span class="sxs-lookup"><span data-stu-id="1867d-134">**File system**</span></span>|<span data-ttu-id="1867d-135">패키지가 파일 시스템에 있으면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-135">Select this option when the package resides in the file system.</span></span>|  
|<span data-ttu-id="1867d-136">**SSIS 패키지 저장소**</span><span class="sxs-lookup"><span data-stu-id="1867d-136">**SSIS Package Store**</span></span>|<span data-ttu-id="1867d-137">패키지가 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지 저장소에 있으면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-137">Select this option when the package resides in the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store.</span></span>|  
  
 <span data-ttu-id="1867d-138">각 선택 항목에는 다음 옵션 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-138">Each of these selections has the following set of options.</span></span>  
  
 <span data-ttu-id="1867d-139">**실행**</span><span class="sxs-lookup"><span data-stu-id="1867d-139">**Execute**</span></span>  
 <span data-ttu-id="1867d-140">패키지를 실행하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-140">Click to run the package.</span></span>  
  
 <span data-ttu-id="1867d-141">**닫기**</span><span class="sxs-lookup"><span data-stu-id="1867d-141">**Close**</span></span>  
 <span data-ttu-id="1867d-142">**패키지 실행 유틸리티** 대화 상자를 닫으려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-142">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
### <a name="dynamic-options"></a><span data-ttu-id="1867d-143">동적 옵션</span><span class="sxs-lookup"><span data-stu-id="1867d-143">Dynamic Options</span></span>  
  
#### <a name="package-source--sql-server"></a><span data-ttu-id="1867d-144">패키지 원본 = SQL Server</span><span class="sxs-lookup"><span data-stu-id="1867d-144">Package Source = SQL Server</span></span>  
 <span data-ttu-id="1867d-145">**Server**</span><span class="sxs-lookup"><span data-stu-id="1867d-145">**Server**</span></span>  
 <span data-ttu-id="1867d-146">패키지가 있는 서버 이름을 입력하거나 목록에서 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-146">Type the name of the server where the package resides, or select a server from the list.</span></span>  
  
 <span data-ttu-id="1867d-147">**서버에 로그온**</span><span class="sxs-lookup"><span data-stu-id="1867d-147">**Log on to the server**</span></span>  
 <span data-ttu-id="1867d-148">패키지에서 Windows 인증 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 연결할지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-148">Specify whether the package should use Windows Authentication or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1867d-149">보안을 강화하려면 Windows 인증을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-149">Windows Authentication is recommended for better security.</span></span> <span data-ttu-id="1867d-150">Windows 인증을 사용하면 사용자 이름과 암호를 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-150">With Windows Authentication you do not have to specify a user name and password.</span></span>  
  
 <span data-ttu-id="1867d-151">**Windows 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="1867d-151">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="1867d-152">Windows 인증을 사용하고 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 사용자 계정으로 로그온하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-152">Select this option to use Windows Authentication and log on using a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows user account.</span></span>  
  
 <span data-ttu-id="1867d-153">**SQL Server 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="1867d-153">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="1867d-154">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-154">Select this option to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="1867d-155">사용자가 지정한 로그인 이름과 암호를 사용하여 트러스트되지 않은 연결로부터 연결하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인 계정이 설정되었는지 및 지정한 암호가 전에 기록한 암호와 일치하는지를 확인하여 인증을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-155">When a user connects with a specified login name and password from a non-trusted connection, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs the authentication by checking to see if a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login account has been set up and if the specified password matches the one previously recorded.</span></span> <span data-ttu-id="1867d-156">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 로그인 계정을 찾을 수 없으면 인증이 실패하고 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-156">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot find the login account, authentication fails, and the user receives an error message.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1867d-157">가능하면 Windows 인증을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="1867d-157">When possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="1867d-158">**패키지**</span><span class="sxs-lookup"><span data-stu-id="1867d-158">**Package**</span></span>  
 <span data-ttu-id="1867d-159">패키지 이름을 입력하거나 줄임표 단추 **(...)** 를 클릭하여 **SSIS 패키지 선택** 대화 상자를 사용하여 패키지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-159">Type the name of the package, or click the ellipsis button **(...)** to locate a package using the **Select an SSIS Package** dialog box.</span></span>  
  
#### <a name="package-source--file-system"></a><span data-ttu-id="1867d-160">패키지 원본 = 파일 시스템</span><span class="sxs-lookup"><span data-stu-id="1867d-160">Package Source = File System</span></span>  
 <span data-ttu-id="1867d-161">**패키지**</span><span class="sxs-lookup"><span data-stu-id="1867d-161">**Package**</span></span>  
 <span data-ttu-id="1867d-162">패키지 이름을 입력하거나 줄임표 단추 **(...)** 를 클릭하여 열기 대화 상자에서 패키지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-162">Type the name of the package, or click the ellipsis button **(...)** to locate a package using the Open dialog box.</span></span> <span data-ttu-id="1867d-163">기본적으로 이 대화 상자는 .dtsx 확장명을 가진 파일만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-163">By default, the dialog box lists only files that have the .dtsx extension.</span></span>  
  
#### <a name="package-source--ssis-package-store"></a><span data-ttu-id="1867d-164">패키지 원본 = SSIS 패키지 저장소</span><span class="sxs-lookup"><span data-stu-id="1867d-164">Package Source = SSIS Package Store</span></span>  
 <span data-ttu-id="1867d-165">**Server**</span><span class="sxs-lookup"><span data-stu-id="1867d-165">**Server**</span></span>  
 <span data-ttu-id="1867d-166">패키지가 있는 컴퓨터 이름을 입력하거나 목록에서 컴퓨터를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-166">Type the name of the computer where the package resides, or select a computer from the list.</span></span>  
  
 <span data-ttu-id="1867d-167">**서버에 로그온**</span><span class="sxs-lookup"><span data-stu-id="1867d-167">**Log on to the server**</span></span>  
 <span data-ttu-id="1867d-168">패키지에서 Microsoft Windows 인증을 사용하여 패키지 원본에 연결할지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-168">Specify whether the package should use Microsoft Windows Authentication to connect to the package source.</span></span> <span data-ttu-id="1867d-169">보안을 강화하려면 Windows 인증을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-169">Windows Authentication is recommended for better security.</span></span> <span data-ttu-id="1867d-170">Windows 인증을 사용하면 사용자 이름과 암호를 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-170">With Windows Authentication you do not have to specify a user name and password.</span></span>  
  
 <span data-ttu-id="1867d-171">**Windows 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="1867d-171">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="1867d-172">Windows 인증을 사용하고 Microsoft Windows 사용자 계정으로 로그온하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-172">Select this option to use Windows Authentication and log on using a Microsoft Windows user account.</span></span>  
  
 <span data-ttu-id="1867d-173">**SQL Server 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="1867d-173">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="1867d-174">**SSIS 패키지 저장소**에 저장된 패키지를 실행하는 경우 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-174">This option is not available when you run a package stored in the **SSIS Package Store**.</span></span>  
  
 <span data-ttu-id="1867d-175">**패키지**</span><span class="sxs-lookup"><span data-stu-id="1867d-175">**Package**</span></span>  
 <span data-ttu-id="1867d-176">패키지 이름을 입력하거나 줄임표 단추 **(...)** 를 클릭하여 **SSIS 패키지 선택** 대화 상자를 사용하여 패키지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-176">Type the name of the package, or click the ellipsis button **(...)** to locate a package using the **Select an SSIS Package** dialog box.</span></span>  
  
## <a name="configurations-page"></a><span data-ttu-id="1867d-177">구성 페이지</span><span class="sxs-lookup"><span data-stu-id="1867d-177">Configurations Page</span></span>  
 <span data-ttu-id="1867d-178">**패키지 실행 유틸리티** 대화 상자의 **구성** 페이지를 사용하여 런타임에 로드할 구성 파일을 선택하고 이러한 파일의 로드 순서를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-178">Use the **Configurations** page of the **Execute Package Utility** dialog box to select the configuration files to load at run time, and to specify the order in which they load.</span></span>  
  
### <a name="options"></a><span data-ttu-id="1867d-179">옵션</span><span class="sxs-lookup"><span data-stu-id="1867d-179">Options</span></span>  
 <span data-ttu-id="1867d-180">**구성 파일**</span><span class="sxs-lookup"><span data-stu-id="1867d-180">**Configuration files**</span></span>  
 <span data-ttu-id="1867d-181">패키지가 사용하는 구성을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-181">Lists the configurations that the package uses.</span></span> <span data-ttu-id="1867d-182">구성 파일을 사용할 때마다 명령 프롬프트에 **/CONFIGFILE filename** 옵션이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-182">Each configuration file adds a **/CONFIGFILE filename** option to the command prompt.</span></span>  
  
 <span data-ttu-id="1867d-183">**화살표 키**</span><span class="sxs-lookup"><span data-stu-id="1867d-183">**Arrow keys**</span></span>  
 <span data-ttu-id="1867d-184">목록에서 구성 파일을 선택한 다음 오른쪽에 있는 화살표 키를 사용하여 로드 순서를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-184">Select a configuration file in the list, and use the arrow keys at right to change the loading order.</span></span> <span data-ttu-id="1867d-185">구성은 목록의 위에서부터 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-185">Configurations load in order starting from the top of the list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1867d-186">여러 구성에서 동일한 속성을 수정하는 경우 마지막으로 로드되는 구성이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-186">If multiple configurations modify the same property, the configuration that loads last is used.</span></span>  
  
 <span data-ttu-id="1867d-187">**추가**</span><span class="sxs-lookup"><span data-stu-id="1867d-187">**Add**</span></span>  
 <span data-ttu-id="1867d-188">**열기** 대화 상자를 사용하여 구성을 추가하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-188">Click to add configurations using the **Open** dialog box.</span></span> <span data-ttu-id="1867d-189">기본적으로 이 대화 상자에서는 확장명이 .dtsconfig인 파일만 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-189">By default, the dialog box lists only files that have the .dtsconfig extension.</span></span>  
  
 <span data-ttu-id="1867d-190">**제거**</span><span class="sxs-lookup"><span data-stu-id="1867d-190">**Remove**</span></span>  
 <span data-ttu-id="1867d-191">목록에서 구성 파일을 선택한 다음 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-191">Select a configuration file in the list and then click **Remove**.</span></span>  
  
 <span data-ttu-id="1867d-192">**실행**</span><span class="sxs-lookup"><span data-stu-id="1867d-192">**Execute**</span></span>  
 <span data-ttu-id="1867d-193">패키지를 실행하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-193">Click to run the package.</span></span>  
  
 <span data-ttu-id="1867d-194">**닫기**</span><span class="sxs-lookup"><span data-stu-id="1867d-194">**Close**</span></span>  
 <span data-ttu-id="1867d-195">**패키지 실행 유틸리티** 대화 상자를 닫으려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-195">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="command-files-page"></a><span data-ttu-id="1867d-196">명령 파일 페이지</span><span class="sxs-lookup"><span data-stu-id="1867d-196">Command Files Page</span></span>  
 <span data-ttu-id="1867d-197">**패키지 실행 유틸리티** 대화 상자의 **명령 파일** 페이지를 사용하여 런타임에 로드할 명령 파일을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-197">Use the **Command Files** page of the **Execute Package Utility** dialog box to select the command files to load at run time.</span></span>  
  
### <a name="options"></a><span data-ttu-id="1867d-198">옵션</span><span class="sxs-lookup"><span data-stu-id="1867d-198">Options</span></span>  
 <span data-ttu-id="1867d-199">**명령 파일**</span><span class="sxs-lookup"><span data-stu-id="1867d-199">**Command files**</span></span>  
 <span data-ttu-id="1867d-200">패키지에서 사용하는 명령 파일을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-200">Lists the command files that the package uses.</span></span> <span data-ttu-id="1867d-201">패키지는 여러 파일을 사용하여 명령줄 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-201">A package can use multiple files to set command-line options.</span></span>  
  
 <span data-ttu-id="1867d-202">**화살표 키**</span><span class="sxs-lookup"><span data-stu-id="1867d-202">**Arrow keys**</span></span>  
 <span data-ttu-id="1867d-203">목록에서 명령 파일을 선택한 다음 우측의 화살표 키를 사용하여 로드 순서를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-203">Select a command file in the list, and use the arrow keys at right to change the loading order.</span></span> <span data-ttu-id="1867d-204">명령 파일은 목록의 맨 위에서 시작하여 차례로 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-204">Command files load in order, starting from the top of the list.</span></span>  
  
 <span data-ttu-id="1867d-205">**추가**</span><span class="sxs-lookup"><span data-stu-id="1867d-205">**Add**</span></span>  
 <span data-ttu-id="1867d-206">**열기** 대화 상자를 사용하여 명령 파일을 추가하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-206">Click to add a command file, using the **Open** dialog box.</span></span>  
  
 <span data-ttu-id="1867d-207">**제거**</span><span class="sxs-lookup"><span data-stu-id="1867d-207">**Remove**</span></span>  
 <span data-ttu-id="1867d-208">입력란에서 명령 파일을 선택한 다음 **제거** 단추를 사용하여 선택한 명령 파일을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-208">Select a command file in the text box, and then remove it using the **Remove** button.</span></span>  
  
 <span data-ttu-id="1867d-209">**실행**</span><span class="sxs-lookup"><span data-stu-id="1867d-209">**Execute**</span></span>  
 <span data-ttu-id="1867d-210">패키지를 실행하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-210">Click to run the package.</span></span>  
  
 <span data-ttu-id="1867d-211">**닫기**</span><span class="sxs-lookup"><span data-stu-id="1867d-211">**Close**</span></span>  
 <span data-ttu-id="1867d-212">**패키지 실행 유틸리티** 대화 상자를 닫으려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-212">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="connection-managers-page"></a><span data-ttu-id="1867d-213">연결 관리자 페이지</span><span class="sxs-lookup"><span data-stu-id="1867d-213">Connection Managers Page</span></span>  
 <span data-ttu-id="1867d-214">**패키지 실행 유틸리티** 대화 상자의 **연결 관리자** 페이지를 사용하여 패키지가 사용하는 연결 관리자의 연결 문자열을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-214">Use the **Connection Managers** page of the **Execute Package Utility** dialog box to edit the connection strings of the connection managers that the package uses.</span></span>  
  
### <a name="options"></a><span data-ttu-id="1867d-215">옵션</span><span class="sxs-lookup"><span data-stu-id="1867d-215">Options</span></span>  
 <span data-ttu-id="1867d-216">**연결 관리자**</span><span class="sxs-lookup"><span data-stu-id="1867d-216">**Connection Manager**</span></span>  
 <span data-ttu-id="1867d-217">**연결 문자열** 열을 편집할 수 있도록 하려면 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-217">Select its check box to make the **Connection String** column editable.</span></span>  
  
 <span data-ttu-id="1867d-218">**설명**</span><span class="sxs-lookup"><span data-stu-id="1867d-218">**Description**</span></span>  
 <span data-ttu-id="1867d-219">각 연결 관리자에 대한 설명을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-219">View a description for each connection manager.</span></span> <span data-ttu-id="1867d-220">설명은 편집할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-220">Descriptions cannot be edited.</span></span>  
  
 <span data-ttu-id="1867d-221">**연결 문자열**</span><span class="sxs-lookup"><span data-stu-id="1867d-221">**Connection String**</span></span>  
 <span data-ttu-id="1867d-222">연결 관리자의 연결 문자열을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-222">Edit the connection string for a connection manager.</span></span> <span data-ttu-id="1867d-223">이 필드는 **연결 관리자** 확인란을 선택한 경우에만 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-223">This field is editable only when the **Connection Manager** check box is selected.</span></span>  
  
 <span data-ttu-id="1867d-224">**실행**</span><span class="sxs-lookup"><span data-stu-id="1867d-224">**Execute**</span></span>  
 <span data-ttu-id="1867d-225">패키지를 실행하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-225">Click to run the package.</span></span>  
  
 <span data-ttu-id="1867d-226">**닫기**</span><span class="sxs-lookup"><span data-stu-id="1867d-226">**Close**</span></span>  
 <span data-ttu-id="1867d-227">**패키지 실행 유틸리티** 대화 상자를 닫으려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-227">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="execution-options-page"></a><span data-ttu-id="1867d-228">실행 옵션 페이지</span><span class="sxs-lookup"><span data-stu-id="1867d-228">Execution Options Page</span></span>  
 <span data-ttu-id="1867d-229">**패키지 실행 유틸리티** 대화 상자의 **실행 옵션** 페이지를 사용하여 패키지에 대한 런타임 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-229">Use the **Execution Options** page of the **Execute Package Utility** dialog box to specify run-time options for the package.</span></span>  
  
### <a name="options"></a><span data-ttu-id="1867d-230">옵션</span><span class="sxs-lookup"><span data-stu-id="1867d-230">Options</span></span>  
 <span data-ttu-id="1867d-231">**유효성 검사 경고 발생 시 패키지 실패**</span><span class="sxs-lookup"><span data-stu-id="1867d-231">**Fail package on validation warnings**</span></span>  
 <span data-ttu-id="1867d-232">유효성 검사 경고가 발생할 경우 패키지가 실패하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-232">Indicate whether the package fails if a validation warning occurs.</span></span>  
  
 <span data-ttu-id="1867d-233">**패키지를 실행하지 않고 유효성 검사**</span><span class="sxs-lookup"><span data-stu-id="1867d-233">**Validate package without executing**</span></span>  
 <span data-ttu-id="1867d-234">패키지에 대해 유효성 검사만 수행할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-234">Indicate whether the package is validated only.</span></span>  
  
 <span data-ttu-id="1867d-235">**최대 동시 실행 파일 수**</span><span class="sxs-lookup"><span data-stu-id="1867d-235">**Maximum concurrent executables**</span></span>  
 <span data-ttu-id="1867d-236">패키지에서 동시에 실행할 수 있는 최대 실행 파일 수를 지정할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-236">Indicate whether you want to specify the maximum number of executables that can run in the package at the same time.</span></span> <span data-ttu-id="1867d-237">이 확인란을 선택하면 스핀 상자를 사용하여 최대 실행 파일 수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-237">After you select this check box, use the spin box to specify the maximum number of executables.</span></span>  
  
 <span data-ttu-id="1867d-238">**패키지 검사점 사용**</span><span class="sxs-lookup"><span data-stu-id="1867d-238">**Enable package checkpoints**</span></span>  
 <span data-ttu-id="1867d-239">패키지 검사점 사용 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-239">Indicate whether to enable package checkpoints.</span></span>  
  
 <span data-ttu-id="1867d-240">**검사점 파일**</span><span class="sxs-lookup"><span data-stu-id="1867d-240">**Checkpoint file**</span></span>  
 <span data-ttu-id="1867d-241">패키지 검사점을 사용하는 경우 패키지가 사용하는 검사점 파일을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-241">List the checkpoint file the package uses, if you enable package checkpoints.</span></span>  
  
 <span data-ttu-id="1867d-242">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="1867d-242">**Browse**</span></span>  
 <span data-ttu-id="1867d-243">패키지 검사점을 사용하는 경우 **열기** 대화 상자를 사용하여 찾아보기 단추 **(...)** 를 클릭하여 검사점 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-243">Click the browse button **(...)** to locate the checkpoint file using the **Open** dialog box, if you enable package checkpoints.</span></span> <span data-ttu-id="1867d-244">검사점 파일이 이미 지정되어 있는 경우에는 선택한 파일로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-244">If a checkpoint file is already specified, it is replaced by the selected file.</span></span>  
  
 <span data-ttu-id="1867d-245">**다시 시작 옵션 무시**</span><span class="sxs-lookup"><span data-stu-id="1867d-245">**Override restart options**</span></span>  
 <span data-ttu-id="1867d-246">패키지 검사점을 사용하는 경우 다시 시작 옵션을 무시할 것인지 여부를 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-246">Indicate whether to override restart options, if you enable package checkpoints.</span></span>  
  
 <span data-ttu-id="1867d-247">**다시 시작 옵션**</span><span class="sxs-lookup"><span data-stu-id="1867d-247">**Restart option**</span></span>  
 <span data-ttu-id="1867d-248">다시 시작 옵션을 무시하는 경우 검사점 사용 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-248">Select how to use checkpoints, if you override restart options.</span></span>  
  
 <span data-ttu-id="1867d-249">**실행**</span><span class="sxs-lookup"><span data-stu-id="1867d-249">**Execute**</span></span>  
 <span data-ttu-id="1867d-250">패키지를 실행하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-250">Click to run the package.</span></span>  
  
 <span data-ttu-id="1867d-251">**닫기**</span><span class="sxs-lookup"><span data-stu-id="1867d-251">**Close**</span></span>  
 <span data-ttu-id="1867d-252">**패키지 실행 유틸리티** 대화 상자를 닫으려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-252">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="reporting-page"></a><span data-ttu-id="1867d-253">보고 페이지</span><span class="sxs-lookup"><span data-stu-id="1867d-253">Reporting Page</span></span>  
 <span data-ttu-id="1867d-254">**패키지 실행 유틸리티** 대화 상자의 **보고** 페이지를 사용하여 패키지 실행 시 콘솔에 기록할 패키지 정보 및 이벤트를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-254">Use the **Reporting** page of the **Execute Package Utility** dialog box to specify the events and information about the package to log to the console when the package runs.</span></span>  
  
### <a name="options"></a><span data-ttu-id="1867d-255">옵션</span><span class="sxs-lookup"><span data-stu-id="1867d-255">Options</span></span>  
 <span data-ttu-id="1867d-256">**콘솔 이벤트**</span><span class="sxs-lookup"><span data-stu-id="1867d-256">**Console events**</span></span>  
 <span data-ttu-id="1867d-257">보고할 이벤트와 메시지 유형을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-257">Indicate the events and types of messages to report.</span></span>  
  
 <span data-ttu-id="1867d-258">**없음**</span><span class="sxs-lookup"><span data-stu-id="1867d-258">**None**</span></span>  
 <span data-ttu-id="1867d-259">보고하지 않으려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-259">Select for no reporting.</span></span>  
  
 <span data-ttu-id="1867d-260">**Errors**</span><span class="sxs-lookup"><span data-stu-id="1867d-260">**Errors**</span></span>  
 <span data-ttu-id="1867d-261">오류 메시지를 보고하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-261">Select to report error messages.</span></span>  
  
 <span data-ttu-id="1867d-262">**경고**</span><span class="sxs-lookup"><span data-stu-id="1867d-262">**Warnings**</span></span>  
 <span data-ttu-id="1867d-263">경고 메시지를 보고하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-263">Select to report warning messages.</span></span>  
  
 <span data-ttu-id="1867d-264">**사용자 지정 이벤트**</span><span class="sxs-lookup"><span data-stu-id="1867d-264">**Custom Events**</span></span>  
 <span data-ttu-id="1867d-265">사용자 지정 이벤트 메시지를 보고하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-265">Select to report custom event messages.</span></span>  
  
 <span data-ttu-id="1867d-266">**파이프라인 이벤트**</span><span class="sxs-lookup"><span data-stu-id="1867d-266">**Pipeline Events**</span></span>  
 <span data-ttu-id="1867d-267">데이터 흐름 이벤트 메시지를 보고하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-267">Select to report data flow events messages.</span></span>  
  
 <span data-ttu-id="1867d-268">**정보**</span><span class="sxs-lookup"><span data-stu-id="1867d-268">**Information**</span></span>  
 <span data-ttu-id="1867d-269">정보 메시지를 보고하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-269">Select to report information messages.</span></span>  
  
 <span data-ttu-id="1867d-270">**자세한 정보**</span><span class="sxs-lookup"><span data-stu-id="1867d-270">**Verbose**</span></span>  
 <span data-ttu-id="1867d-271">자세한 정보를 보고하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-271">Select to use verbose reporting.</span></span>  
  
 <span data-ttu-id="1867d-272">**콘솔 로깅**</span><span class="sxs-lookup"><span data-stu-id="1867d-272">**Console logging**</span></span>  
 <span data-ttu-id="1867d-273">선택한 이벤트 발생 시 로그에 기록할 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-273">Specify the information that you want written to the log when the selected event occurs.</span></span>  
  
 <span data-ttu-id="1867d-274">**이름**</span><span class="sxs-lookup"><span data-stu-id="1867d-274">**Name**</span></span>  
 <span data-ttu-id="1867d-275">패키지를 만든 사용자 이름을 보고하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-275">Select to report the name of the person who created the package.</span></span>  
  
 <span data-ttu-id="1867d-276">**컴퓨터**</span><span class="sxs-lookup"><span data-stu-id="1867d-276">**Computer**</span></span>  
 <span data-ttu-id="1867d-277">패키지를 실행 중인 컴퓨터 이름을 보고하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-277">Select to report the name of the computer the package is running on.</span></span>  
  
 <span data-ttu-id="1867d-278">**연산자**</span><span class="sxs-lookup"><span data-stu-id="1867d-278">**Operator**</span></span>  
 <span data-ttu-id="1867d-279">패키지를 시작한 사용자 이름을 보고하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-279">Select to report the name of the person who started the package.</span></span>  
  
 <span data-ttu-id="1867d-280">**원본 이름**</span><span class="sxs-lookup"><span data-stu-id="1867d-280">**Source name**</span></span>  
 <span data-ttu-id="1867d-281">패키지 이름을 보고하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-281">Select to report the package name.</span></span>  
  
 <span data-ttu-id="1867d-282">**원본 GUID**</span><span class="sxs-lookup"><span data-stu-id="1867d-282">**Source GUID**</span></span>  
 <span data-ttu-id="1867d-283">패키지 GUID를 보고하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-283">Select to report the package GUID.</span></span>  
  
 <span data-ttu-id="1867d-284">**실행 GUID**</span><span class="sxs-lookup"><span data-stu-id="1867d-284">**Execution GUID**</span></span>  
 <span data-ttu-id="1867d-285">패키지 실행 인스턴스의 GUID를 보고하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-285">Select to report the GUID of the package execution instance.</span></span>  
  
 <span data-ttu-id="1867d-286">**메시지**</span><span class="sxs-lookup"><span data-stu-id="1867d-286">**Message**</span></span>  
 <span data-ttu-id="1867d-287">메시지를 보고하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-287">Select to report messages.</span></span>  
  
 <span data-ttu-id="1867d-288">**시작/종료 시간**</span><span class="sxs-lookup"><span data-stu-id="1867d-288">**Start time and end time**</span></span>  
 <span data-ttu-id="1867d-289">패키지 시작 및 종료 시간을 보고하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-289">Select to report when the package began and finished.</span></span>  
  
 <span data-ttu-id="1867d-290">**실행**</span><span class="sxs-lookup"><span data-stu-id="1867d-290">**Execute**</span></span>  
 <span data-ttu-id="1867d-291">패키지를 실행하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-291">Click to run the package.</span></span>  
  
 <span data-ttu-id="1867d-292">**닫기**</span><span class="sxs-lookup"><span data-stu-id="1867d-292">**Close**</span></span>  
 <span data-ttu-id="1867d-293">**패키지 실행 유틸리티** 대화 상자를 닫으려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-293">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="logging-page"></a><span data-ttu-id="1867d-294">로깅 페이지</span><span class="sxs-lookup"><span data-stu-id="1867d-294">Logging Page</span></span>  
 <span data-ttu-id="1867d-295">**패키지 실행 유틸리티** 대화 상자의 **로깅** 페이지를 사용하여 런타임에 로그 공급자를 패키지에서 사용 가능하게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-295">Use the **Logging** page of the **Execute Package Utility** dialog box to make log providers available to the package at run time.</span></span> <span data-ttu-id="1867d-296">로그에 연결하는 데 사용할 패키지 로그 공급자 유형 및 연결 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-296">Provide the package log provider type and the connection string for connecting to the log.</span></span> <span data-ttu-id="1867d-297">로그 공급자를 입력할 때마다 명령 프롬프트에 **/LOGGER**_classid_ 옵션이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-297">Each log provider entry adds a **/LOGGER**_classid_ option to the command prompt.</span></span>  
  
### <a name="options"></a><span data-ttu-id="1867d-298">옵션</span><span class="sxs-lookup"><span data-stu-id="1867d-298">Options</span></span>  
 <span data-ttu-id="1867d-299">**로그 공급자**</span><span class="sxs-lookup"><span data-stu-id="1867d-299">**Log Provider**</span></span>  
 <span data-ttu-id="1867d-300">목록에서 로그 공급자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-300">Select a log provider from the list.</span></span>  
  
 <span data-ttu-id="1867d-301">**구성 문자열**</span><span class="sxs-lookup"><span data-stu-id="1867d-301">**Configuration String**</span></span>  
 <span data-ttu-id="1867d-302">로그 위치를 가리키는 패키지에서 연결 관리자의 이름을 선택하거나 해당 로그 공급자에 연결하는 데 사용할 연결 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-302">Select the name of the connection manager from the package that points to the log location, or type the connection string for connecting to the log provider.</span></span>  
  
 <span data-ttu-id="1867d-303">**제거**</span><span class="sxs-lookup"><span data-stu-id="1867d-303">**Remove**</span></span>  
 <span data-ttu-id="1867d-304">로그 공급자를 선택하여 제거하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-304">Select a log provider and click to remove it.</span></span>  
  
 <span data-ttu-id="1867d-305">**실행**</span><span class="sxs-lookup"><span data-stu-id="1867d-305">**Execute**</span></span>  
 <span data-ttu-id="1867d-306">패키지를 실행하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-306">Click to run the package.</span></span>  
  
 <span data-ttu-id="1867d-307">**닫기**</span><span class="sxs-lookup"><span data-stu-id="1867d-307">**Close**</span></span>  
 <span data-ttu-id="1867d-308">**패키지 실행 유틸리티** 대화 상자를 닫으려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-308">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="set-values-page"></a><span data-ttu-id="1867d-309">값 설정 페이지</span><span class="sxs-lookup"><span data-stu-id="1867d-309">Set Values Page</span></span>  
 <span data-ttu-id="1867d-310">**패키지 실행 유틸리티** 대화 상자의 **값 설정** 페이지에서 속성의 경로 및 해당 속성 값을 입력하여 패키지, 실행 파일, 연결, 변수 및 로그 공급자의 속성 값을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-310">Use the **Set Values** page of the **Execute Package Utility** dialog box to set the property values of packages, executables, connections, variables, and log providers by typing the paths of properties and the property values.</span></span> <span data-ttu-id="1867d-311">경로를 입력할 때마다 명령 프롬프트에 **/SET**_propertypath;value_ 옵션이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-311">Each path entry adds a **/SET**_propertypath;value_ option to the command prompt.</span></span>  
  
### <a name="options"></a><span data-ttu-id="1867d-312">옵션</span><span class="sxs-lookup"><span data-stu-id="1867d-312">Options</span></span>  
 <span data-ttu-id="1867d-313">**속성 경로**</span><span class="sxs-lookup"><span data-stu-id="1867d-313">**Property Path**</span></span>  
 <span data-ttu-id="1867d-314">속성의 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-314">Type the path of the property.</span></span> <span data-ttu-id="1867d-315">경로 구문에서는 백슬래시(\\)를 사용하여 다음 항목이 컨테이너임을 나타내고, 마침표(.)를 사용하여 다음 항목이 속성임을 나타내고, 대괄호를 사용하여 컬렉션 멤버임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-315">The path syntax uses a backslash (\\) to indicate that the following item is a container, the period (.) to indicate the following item is a property, and brackets to indicate a collection member.</span></span> <span data-ttu-id="1867d-316">멤버는 해당 멤버의 인덱스 또는 이름으로 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-316">The member can be identified by its index or its name.</span></span> <span data-ttu-id="1867d-317">예를 들어 패키지 변수의 속성 경로는 \Package.Variables[MyVariable].Value입니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-317">For example, the property path of a package variable is \Package.Variables[MyVariable].Value.</span></span>  
  
 <span data-ttu-id="1867d-318">**값**</span><span class="sxs-lookup"><span data-stu-id="1867d-318">**Value**</span></span>  
 <span data-ttu-id="1867d-319">속성 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-319">Type the value of the property.</span></span>  
  
 <span data-ttu-id="1867d-320">**제거**</span><span class="sxs-lookup"><span data-stu-id="1867d-320">**Remove**</span></span>  
 <span data-ttu-id="1867d-321">속성 경로를 선택하고 제거하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-321">Select a property path and click to remove it.</span></span>  
  
 <span data-ttu-id="1867d-322">**실행**</span><span class="sxs-lookup"><span data-stu-id="1867d-322">**Execute**</span></span>  
 <span data-ttu-id="1867d-323">패키지를 실행하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-323">Click to run the package.</span></span>  
  
 <span data-ttu-id="1867d-324">**닫기**</span><span class="sxs-lookup"><span data-stu-id="1867d-324">**Close**</span></span>  
 <span data-ttu-id="1867d-325">**패키지 실행 유틸리티** 대화 상자를 닫으려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-325">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="verification-page"></a><span data-ttu-id="1867d-326">확인 페이지</span><span class="sxs-lookup"><span data-stu-id="1867d-326">Verification Page</span></span>  
 <span data-ttu-id="1867d-327">**패키지 실행 유틸리티** 대화 상자의 **확인** 페이지를 사용하여 패키지 확인 조건을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-327">Use the **Verification** page of the **Execute Package** dialog box to set criteria for verifying the package.</span></span>  
  
### <a name="options"></a><span data-ttu-id="1867d-328">옵션</span><span class="sxs-lookup"><span data-stu-id="1867d-328">Options</span></span>  
 <span data-ttu-id="1867d-329">**서명된 패키지만 실행**</span><span class="sxs-lookup"><span data-stu-id="1867d-329">**Execute only signed packages**</span></span>  
 <span data-ttu-id="1867d-330">서명된 패키지만 실행하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-330">Select to execute only packages that have been signed.</span></span>  
  
 <span data-ttu-id="1867d-331">**패키지 빌드 확인**</span><span class="sxs-lookup"><span data-stu-id="1867d-331">**Verify package build**</span></span>  
 <span data-ttu-id="1867d-332">패키지 빌드를 확인하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-332">Select to verify the package build.</span></span>  
  
 <span data-ttu-id="1867d-333">빌드</span><span class="sxs-lookup"><span data-stu-id="1867d-333">Build</span></span>  
 <span data-ttu-id="1867d-334">빌드와 연결된 순차적 빌드 번호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-334">Specify the sequential Build number associated with the build.</span></span>  
  
 <span data-ttu-id="1867d-335">**패키지 ID 확인**</span><span class="sxs-lookup"><span data-stu-id="1867d-335">**Verify package ID**</span></span>  
 <span data-ttu-id="1867d-336">패키지 ID를 확인하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-336">Select to verify the package ID.</span></span>  
  
 <span data-ttu-id="1867d-337">패키지 ID</span><span class="sxs-lookup"><span data-stu-id="1867d-337">Package ID</span></span>  
 <span data-ttu-id="1867d-338">패키지 ID 번호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-338">Specify the package identification number.</span></span>  
  
 <span data-ttu-id="1867d-339">**버전 ID 확인**</span><span class="sxs-lookup"><span data-stu-id="1867d-339">**Verify version ID**</span></span>  
 <span data-ttu-id="1867d-340">버전 ID를 확인하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-340">Select to verify the version ID.</span></span>  
  
 <span data-ttu-id="1867d-341">버전 ID</span><span class="sxs-lookup"><span data-stu-id="1867d-341">Version ID</span></span>  
 <span data-ttu-id="1867d-342">버전 ID 번호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-342">Specify the version identification number.</span></span>  
  
 <span data-ttu-id="1867d-343">**실행**</span><span class="sxs-lookup"><span data-stu-id="1867d-343">**Execute**</span></span>  
 <span data-ttu-id="1867d-344">패키지를 실행하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-344">Click to run the package.</span></span>  
  
 <span data-ttu-id="1867d-345">**닫기**</span><span class="sxs-lookup"><span data-stu-id="1867d-345">**Close**</span></span>  
 <span data-ttu-id="1867d-346">**패키지 실행 유틸리티** 대화 상자를 닫으려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-346">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="command-line-page"></a><span data-ttu-id="1867d-347">명령줄 페이지</span><span class="sxs-lookup"><span data-stu-id="1867d-347">Command Line Page</span></span>  
 <span data-ttu-id="1867d-348">**패키지 실행 유틸리티** 대화 상자의 **명령줄** 노드를 사용하여 여러 대화 상자에서 만든 옵션으로 생성한 명령줄을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-348">Use the **Command Line** node of the **Execute Package Utility** dialog box to edit the command line that has been generated by the options created by the various dialogs.</span></span>  
  
### <a name="options"></a><span data-ttu-id="1867d-349">옵션</span><span class="sxs-lookup"><span data-stu-id="1867d-349">Options</span></span>  
 <span data-ttu-id="1867d-350">**원래 옵션 복원**</span><span class="sxs-lookup"><span data-stu-id="1867d-350">**Restore the original options**</span></span>  
 <span data-ttu-id="1867d-351">명령줄을 원래 상태로 복원하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-351">Click to restore the command line to its original state.</span></span> <span data-ttu-id="1867d-352">**수동으로 명령줄 편집** 옵션을 사용하여 수정했는데 원래 명령줄 옵션을 복원하려는 경우 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-352">Use this option if you have made modifications using the **Edit the command line manually** option and want to restore the original command-line options.</span></span>  
  
 <span data-ttu-id="1867d-353">**수동으로 명령줄 편집**</span><span class="sxs-lookup"><span data-stu-id="1867d-353">**Edit the command line manually**</span></span>  
 <span data-ttu-id="1867d-354">**명령줄** 입력란에서 명령줄을 편집하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-354">Click to edit the command line in the **Command line** text box.</span></span>  
  
 <span data-ttu-id="1867d-355">**명령줄**</span><span class="sxs-lookup"><span data-stu-id="1867d-355">**Command line**</span></span>  
 <span data-ttu-id="1867d-356">현재 명령줄을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-356">Displays the current command line.</span></span> <span data-ttu-id="1867d-357">명령줄을 수동으로 편집하는 옵션을 선택한 경우 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-357">Editable if you selected the option to edit the command line manually.</span></span>  
  
 <span data-ttu-id="1867d-358">**실행**</span><span class="sxs-lookup"><span data-stu-id="1867d-358">**Execute**</span></span>  
 <span data-ttu-id="1867d-359">패키지를 실행하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-359">Click to run the package.</span></span>  
  
 <span data-ttu-id="1867d-360">**닫기**</span><span class="sxs-lookup"><span data-stu-id="1867d-360">**Close**</span></span>  
 <span data-ttu-id="1867d-361">**패키지 실행 유틸리티** 대화 상자를 닫으려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1867d-361">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1867d-362">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1867d-362">See Also</span></span>  
 [<span data-ttu-id="1867d-363">dtexec 유틸리티</span><span class="sxs-lookup"><span data-stu-id="1867d-363">dtexec Utility</span></span>](dtexec-utility.md)  
  
  
