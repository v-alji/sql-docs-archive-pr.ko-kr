---
title: 보고서 작성기 (보고서 작성기)의 독립 실행형 버전을 설치 합니다. Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6b2291bb-1d20-4d08-81cb-a16dd8e01faf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2ba8c132125f56ad833a71a1c82221e2bf28d13e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652627"
---
# <a name="install-the-stand-alone-version-of-report-builder-report-builder"></a><span data-ttu-id="72fbd-102">독립 실행형 버전의 보고서 작성기 설치(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="72fbd-102">Install the Stand-Alone Version of Report Builder (Report Builder)</span></span>
  <span data-ttu-id="72fbd-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [Microsoft 다운로드 센터](https://www.microsoft.com/download/details.aspx?id=53613) 의 기능 팩에 있는 보고서 작성기를 설치 하거나 ReportBuilder3_x86.msi, 보고서 작성기 용 Windows Installer 패키지가 다운로드 된 공용 폴더 등의 위치를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-103">You can install Report Builder from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] feature pack on the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53613) or a location such as public folder to which the ReportBuilder3_x86.msi, the Windows Installer Package for Report Builder, has been downloaded.</span></span>  
  
 <span data-ttu-id="72fbd-104">보고서 작성기의 명령줄 설치를 수행하고 인수를 제공하여 설치를 사용자 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-104">You can also perform a command line installation of Report Builder and provide arguments to customize the installation.</span></span> <span data-ttu-id="72fbd-105">표준 MSI 내장 매개 변수 외에도 RBINSTALLDIR 및 REPORTSERVERURL 보고서 작성기 제공 하는 사용자 지정 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-105">In addition to the standard MSI intrinsic parameters, you can use the custom parameters that Report Builder provides: RBINSTALLDIR and REPORTSERVERURL.</span></span> <span data-ttu-id="72fbd-106">RBINSTALLDIR은 보고서 작성기의 루트 설치 폴더를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-106">RBINSTALLDIR specifies the root installation folder for Report Builder.</span></span> <span data-ttu-id="72fbd-107">REPORTSERVERURL은 보고서 작성기에서 보고서를 서버에 저장하기 위해 사용하는 기본 보고서 서버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-107">REPORTSERVERURL specifies the default report server that Report Builder uses to save reports on the server.</span></span>  
  
 <span data-ttu-id="72fbd-108">사용자 인터페이스의 상호 작용이 필요 없는 완전 자동 설치를 수행하려면 **/quiet** 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-108">If you want a completely silent installation, with no user interface interaction at all, specify the **/quiet** option.</span></span> <span data-ttu-id="72fbd-109">기본적으로 quiet 옵션 플래그를 사용하면 설치 오류가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-109">By design, the quiet option flag suppresses installation errors.</span></span> <span data-ttu-id="72fbd-110">따라서 quite 옵션을 사용할 때는 로깅을 지정하는 **/l** 옵션을 함께 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-110">It is therefore recommended that you include the **/l** option, which specifies logging, when you use the quiet option.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="72fbd-111">Windows Vista 및 Windows 7의 경우 보안 기능으로 인해 명령줄 작업을 실행하려면 높은 권한이 필요합니다. 따라서 명령줄을 실행할 경우 사용 권한을 요청하는 메시지가 표시되므로</span><span class="sxs-lookup"><span data-stu-id="72fbd-111">Windows Vista and Windows 7 security features require elevated permissions to run command line operations and will prompt for permission to run the command line.</span></span> <span data-ttu-id="72fbd-112">자동 설치를 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-112">The installation is not silent.</span></span> <span data-ttu-id="72fbd-113">자동 설치를 수행하려면 관리자 권한으로 명령줄을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-113">To make the installation silent, you need to run the command line as an administrator.</span></span>  
  
### <a name="to-install-report-builder-from-the-download-site"></a><span data-ttu-id="72fbd-114">다운로드 사이트에서 보고서 작성기를 설치하려면</span><span class="sxs-lookup"><span data-stu-id="72fbd-114">To install Report Builder from the download site</span></span>  
  
1.  <span data-ttu-id="72fbd-115">[Microsoft SQL Server 2012 보고서 작성기](https://go.microsoft.com/fwlink/?LinkID=219138) 으로 이동 하 여 웹 페이지의 보고서 작성기 섹션을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-115">Go to [Microsoft SQL Server 2012 Report Builder](https://go.microsoft.com/fwlink/?LinkID=219138) and locate the Report Builder section of the Web page.</span></span>  
  
2.  <span data-ttu-id="72fbd-116">**X86 패키지**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-116">Click **X86 Package**.</span></span>  
  
3.  <span data-ttu-id="72fbd-117">**파일 다운로드** 대화 상자에서 **실행**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-117">In the **File Download** dialog box, click **Run**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="72fbd-118">신뢰할 수 있는 출처에서 제공하는 파일만 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-118">Download only files from trusted sources.</span></span>  
  
4.  <span data-ttu-id="72fbd-119">Internet Explorer 대화 상자에서 **실행**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-119">In the Internet Explorer dialog box, click **Run**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="72fbd-120">신뢰할 수 있는 출처에서 제공하는 파일만 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-120">Run only files from trusted sources.</span></span>  
  
5.  <span data-ttu-id="72fbd-121">Microsoft SQL Server 보고서 작성기 마법사가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-121">The Microsoft SQL Server Report Builder Wizard is launched.</span></span>  
  
6.  <span data-ttu-id="72fbd-122">**설치 마법사 시작** 페이지에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-122">On the **Welcome to the Installation Wizard** page, click **Next**.</span></span>  
  
7.  <span data-ttu-id="72fbd-123">**사용권 계약** 페이지에서 규약을 읽은 **다음 동의 함 옵션을** 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-123">On the **License Agreement** page, read the agreement and then select the **I accept the terms in the license agreement** option.</span></span> <span data-ttu-id="72fbd-124">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-124">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="72fbd-125">사용자 이름과 회사 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-125">Provide your personal name and company name.</span></span> <span data-ttu-id="72fbd-126">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-126">Click **Next**.</span></span>  
  
9. <span data-ttu-id="72fbd-127">**기능 선택** 페이지에서 필요에 따라 **찾아보기** 또는 **디스크 비용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-127">On the **Feature Selection** page, optionally click **Browse** or **Disk Cost**.</span></span> <span data-ttu-id="72fbd-128">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-128">Click **Next**.</span></span>  
  
    -   <span data-ttu-id="72fbd-129">**찾아보기** 를 클릭 하 보고서 작성기 기본 위치를 확인 하 고 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-129">Click **Browse** to see the default location of Report Builder and update it.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="72fbd-130">보고서 작성기의 기본 설치 폴더는 \<drive> Program Files\Microsoft SQL Server입니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-130">The default installation folder for Report Builder is \<drive>Program Files\Microsoft SQL Server.</span></span>  
  
    -   <span data-ttu-id="72fbd-131">**디스크** 공간을 클릭 하 보고서 작성기 사용 하는 디스크 공간 크기를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-131">Click **Disk Cost** to learn how much disk space Report Builder consumes.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="72fbd-132">볼륨에 디스크 여유 공간이 충분하지 않은 경우 해당 볼륨이 강조 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-132">If a volume does not have sufficient amount of free disk space, the volume is highlighted.</span></span>  
  
10. <span data-ttu-id="72fbd-133">**기본 대상 서버** 페이지에서 필요 시 대상 보고서 서버의 URL을 제공합니다(기본값과 다른 경우).</span><span class="sxs-lookup"><span data-stu-id="72fbd-133">On the **Default Target Server** page, optionally provide the URL to the target report server if it is different from the default.</span></span> <span data-ttu-id="72fbd-134">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-134">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="72fbd-135">보고서 서버에 연결되었을 때 보고서 작성기로 작업할 계획이라면 이 단계에서 서버의 URL을 제공하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-135">If you plan to work with Report Builder when it is connected to a report server, it is convenient to provide the URL to the server at this time.</span></span> <span data-ttu-id="72fbd-136">그러나 보고서 작성기에서 작업할 때 **옵션** 대화 상자에서이 작업을 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-136">However, you can also do this from the **Options** dialog box when you are working in Report Builder.</span></span>  
  
11. <span data-ttu-id="72fbd-137">**설치** 를 클릭 하 보고서 작성기 설치를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-137">Click **Install** to complete the installation of Report Builder.</span></span>  
  
### <a name="to-install-report-builder-from-a-share"></a><span data-ttu-id="72fbd-138">공유에서 보고서 작성기를 설치하려면</span><span class="sxs-lookup"><span data-stu-id="72fbd-138">To install Report Builder from a share</span></span>  
  
1.  <span data-ttu-id="72fbd-139">로컬 컴퓨터에 보고서 작성기를 설치하기 위해 실행하는 ReportBuilder3_x86.msi.msi의 위치는 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="72fbd-139">Contact your administrator for the location of ReportBuilder3_x86.msi.msi that you run to install Report Builder on your local computer.</span></span>  
  
2.  <span data-ttu-id="72fbd-140">보고서 작성기의 Windows Installer 패키지(MSI)인 ReportBuilder3_x86.msi.msi를 찾아서 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-140">Browse to locate the ReportBuilder3_x86.msi.msi, the Windows Installer Package (MSI) for Report Builder, and click it.</span></span>  
  
     <span data-ttu-id="72fbd-141">Microsoft SQL Server 보고서 작성기 마법사가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-141">The Microsoft SQL Server Report Builder Wizard is launched.</span></span>  
  
3.  <span data-ttu-id="72fbd-142">**설치 마법사 시작** 페이지에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-142">On the **Welcome to the Installation Wizard** page, click **Next**.</span></span>  
  
4.  <span data-ttu-id="72fbd-143">**사용권 계약** 페이지에서 규약을 읽은 **다음 동의 함 옵션을** 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-143">On the **License Agreement** page, read the agreement and then select the **I accept the terms in the license agreement** option.</span></span> <span data-ttu-id="72fbd-144">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-144">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="72fbd-145">사용자 이름과 회사 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-145">Provide your personal name and company name.</span></span> <span data-ttu-id="72fbd-146">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-146">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="72fbd-147">**기능 선택** 페이지에서 필요에 따라 **찾아보기** 또는 **디스크 비용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-147">On the **Feature Selection** page, optionally click **Browse** or **Disk Cost**.</span></span> <span data-ttu-id="72fbd-148">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-148">Click **Next**.</span></span>  
  
    -   <span data-ttu-id="72fbd-149">**찾아보기** 를 클릭 하 보고서 작성기 기본 위치를 확인 하 고 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-149">Click **Browse** to see the default location of Report Builder and update it.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="72fbd-150">보고서 작성기의 기본 설치 폴더는 \<drive> Program Files\Microsoft SQL Server입니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-150">The default installation folder for Report Builder is \<drive>Program Files\Microsoft SQL Server.</span></span>  
  
    -   <span data-ttu-id="72fbd-151">**디스크** 공간을 클릭 하 보고서 작성기 사용 하는 디스크 공간 크기를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-151">Click **Disk Cost** to learn how much disk space Report Builder consumes.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="72fbd-152">볼륨에 디스크 여유 공간이 충분하지 않은 경우 해당 볼륨이 강조 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-152">If a volume does not have sufficient amount of free disk space, the volume is highlighted.</span></span>  
  
7.  <span data-ttu-id="72fbd-153">**기본 대상 서버** 페이지에서 필요 시 대상 보고서 서버의 URL을 제공합니다(기본값과 다른 경우).</span><span class="sxs-lookup"><span data-stu-id="72fbd-153">On the **Default Target Server** page, optionally provide the URL to the target report server if it is different from the default.</span></span> <span data-ttu-id="72fbd-154">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-154">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="72fbd-155">보고서 서버에 연결되었을 때 보고서 작성기로 작업할 계획이라면 이 단계에서 서버의 URL을 제공하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-155">If you plan to work with Report Builder when it is connected to a report server, it is convenient to provide the URL to the server at this time.</span></span> <span data-ttu-id="72fbd-156">그러나 보고서 작성기에서 작업할 때 **옵션** 대화 상자에서이 작업을 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-156">However, you can also do this from the **Options** dialog box when you are working in Report Builder.</span></span>  
  
8.  <span data-ttu-id="72fbd-157">**설치** 를 클릭 하 보고서 작성기 설치를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-157">Click **Install** to complete the installation of Report Builder.</span></span>  
  
### <a name="to-install-report-builder-from-the-command-line"></a><span data-ttu-id="72fbd-158">명령줄에서 보고서 작성기를 설치하려면</span><span class="sxs-lookup"><span data-stu-id="72fbd-158">To install Report Builder from the command line</span></span>  
  
1.  <span data-ttu-id="72fbd-159">[Microsoft SQL Server 2012 보고서 작성기](https://go.microsoft.com/fwlink/?LinkID=219138) 으로 이동 하 여 보고서 작성기 섹션을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-159">Go to [Microsoft SQL Server 2012 Report Builder](https://go.microsoft.com/fwlink/?LinkID=219138) and locate the Report Builder section.</span></span>  
  
2.  <span data-ttu-id="72fbd-160">**X86 패키지**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-160">Click **X86 Package**.</span></span>  
  
3.  <span data-ttu-id="72fbd-161">저장을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-161">Click Save.</span></span>  
  
4.  <span data-ttu-id="72fbd-162">필요에 따라 저장할 위치로 이동 하 고 다른 **이름으로 저장** 옵션이 **패키지 Windows Installer**있는지 확인 한 다음 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-162">Optionally, browse to the location to save to, verify the **Save as** option is **Windows Installer Package**, and then click **Save**.</span></span>  
  
5.  <span data-ttu-id="72fbd-163">**시작** 메뉴에서 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-163">On the **Start** menu, click **Run**.</span></span>  
  
6.  <span data-ttu-id="72fbd-164">열기 입력란에 을(를) 입력합니다.`cmd.`</span><span class="sxs-lookup"><span data-stu-id="72fbd-164">In the Open text box, type `cmd.`</span></span>  
  
7.  <span data-ttu-id="72fbd-165">명령 프롬프트 창에서 ReportBuilder3_x86.msi를 저장한 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-165">In the Command Prompt window, navigate to the folder where you saved ReportBuilder3_x86.msi.</span></span>  
  
8.  <span data-ttu-id="72fbd-166">다음 형식으로 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-166">Type a command with the following format:</span></span>  
  
     `msiexec/i ReportBuilder3_.msi /option [value] [/option [value]]`  
  
     <span data-ttu-id="72fbd-167">보고서 작성기 설치와 관련 된 두 가지 옵션은 RBINSTALLDIR 및 REPORTSERVERURL입니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-167">The two options specific to installing Report Builder are: RBINSTALLDIR and REPORTSERVERURL.</span></span> <span data-ttu-id="72fbd-168">이러한 인수는 명령줄에 포함하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-168">It not required that you include these arguments in the command line.</span></span> <span data-ttu-id="72fbd-169">기본 명령은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-169">The following is the baseline command:</span></span>  
  
     `msiexec /i ReportBuilder3_x86.msi /quiet`  
  
9. <span data-ttu-id="72fbd-170">명령을 실행하려면 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="72fbd-170">To run the command, press Enter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72fbd-171">참고 항목</span><span class="sxs-lookup"><span data-stu-id="72fbd-171">See Also</span></span>  
 <span data-ttu-id="72fbd-172">[설치, 제거 및 보고서 작성기 지원](../install-uninstall-and-report-builder-support.md) </span><span class="sxs-lookup"><span data-stu-id="72fbd-172">[Install, Uninstall, and Report Builder Support](../install-uninstall-and-report-builder-support.md) </span></span>  
 [<span data-ttu-id="72fbd-173">독립 실행형 버전의 보고서 작성기 &#40;보고서 작성기을 제거&#41;</span><span class="sxs-lookup"><span data-stu-id="72fbd-173">Uninstall the Stand-Alone Version of Report Builder &#40;Report Builder&#41;</span></span>](install-report-builder.md)  
  
  
