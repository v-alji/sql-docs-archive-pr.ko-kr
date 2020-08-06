---
title: 설치 Distributed Replay (설치) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 64479cdc-661a-4e32-a381-8f8b5a238337
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 029737874fdab53669aab3be25b139d98d2907df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740732"
---
# <a name="install-distributed-replay-setup"></a><span data-ttu-id="5e522-102">Distributed Replay 설치(설치)</span><span class="sxs-lookup"><span data-stu-id="5e522-102">Install Distributed Replay (Setup)</span></span>
  <span data-ttu-id="5e522-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 마법사를 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Distributed Replay 기능을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-103">Install the [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay features with the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Installation Wizard.</span></span> <span data-ttu-id="5e522-104">기능 설치 위치를 계획할 때는 다음 사항을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="5e522-104">When planning where to install the features, consider the following:</span></span>  
  
-   <span data-ttu-id="5e522-105">관리 도구는 Distributed Replay Controller와 동일한 컴퓨터 또는 다른 컴퓨터에 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-105">You can install the administration tool on the same computer as the Distributed Replay controller, or on different computers.</span></span>  
  
-   <span data-ttu-id="5e522-106">각 Distributed Replay 환경에는 컨트롤러가 하나만 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-106">There can only be one controller in each Distributed Replay environment.</span></span>  
  
-   <span data-ttu-id="5e522-107">최대 16개 컴퓨터(실제 컴퓨터 또는 가상 컴퓨터)에 클라이언트 서비스를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-107">You can install the client service on up to 16 (physical or virtual) computers.</span></span>  
  
-   <span data-ttu-id="5e522-108">Distributed Replay 컴퓨터에는 클라이언트 서비스 인스턴스를 하나만 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-108">Only one instance of the client service can be installed on the Distributed Replay controller computer.</span></span> <span data-ttu-id="5e522-109">Distributed Replay 환경에 클라이언트가 여러 개 있는 경우에는 컨트롤러와 같은 컴퓨터에 클라이언트 서비스를 설치하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-109">If your Distributed Replay environment will have more than one client, we do not recommend installing the client service on the same computer as the controller.</span></span> <span data-ttu-id="5e522-110">이렇게 하면 전체적인 분산 재생 속도가 느려질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-110">Doing so may decrease the overall speed of the distributed replay.</span></span>  
  
-   <span data-ttu-id="5e522-111">성능 테스트 시나리오의 경우에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 대상 인스턴스에 관리 도구, Distributed Replay 컨트롤러 서비스 또는 Client 서비스를 설치하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-111">For performance testing scenarios, we do not recommend installing the administration tool, Distributed Replay controller service, or client service on the target instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5e522-112">애플리케이션 호환성을 위한 기능 테스트 시에만 이러한 모든 기능을 대상 서버에 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-112">Installing all of these features on the target server should be limited to functional testing for application compatibility.</span></span>  
  
-   <span data-ttu-id="5e522-113">설치 후에는 클라이언트에서 Distributed Replay  Client 서비스를 시작하기 전에 컨트롤러 서비스인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-113">After installation, the controller service, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay controller, must be running before you start the Distributed Replay client service on the clients.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5e522-114">Distributed Replay 기능을 제거하거나 변경하려면 Windows **제어판** 의 **프로그램 및 기능**창을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-114">To remove or change the Distributed Replay features, use the Windows **Programs and Features** window in **Control Panel**.</span></span> <span data-ttu-id="5e522-115">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 프로그램 제거 또는 변경 **창에서** 를 선택한 다음 **제거** 를 클릭하면 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 설치 마법사가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-115">Select [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in the **Uninstall or change a program** window, and then click **Remove** to open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Installation Wizard.</span></span> <span data-ttu-id="5e522-116">**기능 선택** 페이지에서 제거할 Distributed Replay 기능을 선택하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-116">On the **Select Features** page, check the Distributed Replay features you want to remove.</span></span>  
  
 <span data-ttu-id="5e522-117">**사전 요구 사항:**</span><span class="sxs-lookup"><span data-stu-id="5e522-117">**Prerequisites:**</span></span>  
  
-   <span data-ttu-id="5e522-118">사용하려는 컴퓨터가 [Distributed Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md)항목에 설명된 요구 사항을 충족하는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="5e522-118">Make sure that the computers that you want to use meet the requirements that are described in the topic [Distributed Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md).</span></span>  
  
-   <span data-ttu-id="5e522-119">이 절차를 시작하기 전에 컨트롤러와 클라이언트 서비스를 실행할 도메인 사용자 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-119">Before you begin this procedure, you create the domain user accounts that the controller and client services will run under.</span></span> <span data-ttu-id="5e522-120">Windows Administrators 그룹의 멤버가 아닌 계정을 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-120">We recommend that these accounts are not members of the Windows Administrators group.</span></span> <span data-ttu-id="5e522-121">자세한 내용은 [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md) 항목에서 사용자 및 서비스 계정 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5e522-121">For more information, see the User and Service Accounts section in the [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md) topic.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5e522-122">관리 도구, 컨트롤러 서비스 및 클라이언트 서비스를 같은 컴퓨터에서 실행하는 경우에는 로컬 사용자 계정을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-122">You can use local user accounts if you are running the administration tool, controller service, and client service on the same computer.</span></span>  
  
 <span data-ttu-id="5e522-123">**설치 위치:**</span><span class="sxs-lookup"><span data-stu-id="5e522-123">**Installation Locations:**</span></span>  
  
 <span data-ttu-id="5e522-124">기본 파일 위치 및 표준 설치를 사용한다고 가정할 때 기본 디렉터리는 C:\Program Files\Microsoft SQL Server입니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-124">Assuming you use the default file locations and a standard installation, the base directory is found at C:\Program Files\Microsoft SQL Server.</span></span> <span data-ttu-id="5e522-125">이진 파일과 어셈블리는 이 디렉터리 내의 다음 위치에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-125">Within that, following are where the binaries and assemblies are installed to:</span></span>  
  
-   <span data-ttu-id="5e522-126">32비트 시스템:</span><span class="sxs-lookup"><span data-stu-id="5e522-126">On a 32-bit system:</span></span>  
  
     [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]<span data-ttu-id="5e522-127">Tools</span><span class="sxs-lookup"><span data-stu-id="5e522-127">Tools</span></span>  
  
     <span data-ttu-id="5e522-128">\- 또는 -</span><span class="sxs-lookup"><span data-stu-id="5e522-128">\- OR -</span></span>  
  
     <span data-ttu-id="5e522-129">\<Share Feature Directory>\Tools \\ (사용자가 제공한 대체 공유 기능 디렉터리)</span><span class="sxs-lookup"><span data-stu-id="5e522-129">\<Share Feature Directory>\Tools\\(user-supplied alternative shared feature directory)</span></span>  
  
-   <span data-ttu-id="5e522-130">64비트 시스템:</span><span class="sxs-lookup"><span data-stu-id="5e522-130">On a 64-bit system:</span></span>  
  
     <span data-ttu-id="5e522-131">C:\Program files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (x86) \120\Tools</span><span class="sxs-lookup"><span data-stu-id="5e522-131">C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (x86) \120\Tools</span></span>  
  
     <span data-ttu-id="5e522-132">\- 또는 -</span><span class="sxs-lookup"><span data-stu-id="5e522-132">\- OR -</span></span>  
  
     <span data-ttu-id="5e522-133">\<Share Feature Directory (x86)>\Tools \\ (사용자가 제공한 대체 공유 기능 (x86) 디렉터리)</span><span class="sxs-lookup"><span data-stu-id="5e522-133">\<Share Feature Directory (x86)>\Tools\\(user-supplied alternative shared feature (x86) directory)</span></span>  
  
### <a name="to-install-distributed-replay-features"></a><span data-ttu-id="5e522-134">Distributed Replay 기능을 설치하려면</span><span class="sxs-lookup"><span data-stu-id="5e522-134">To install Distributed Replay features</span></span>  
  
1.  <span data-ttu-id="5e522-135">Distributed Replay 기능 설치를 시작하려면 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 설치 마법사를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-135">To start the installation of any of the Distributed Replay features, start the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Installation Wizard.</span></span>  
  
2.  <span data-ttu-id="5e522-136">**설치 지원 규칙** 페이지에는 SQL Server 설치 지원 파일을 설치할 때 발생할 수 있는 문제가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-136">The **Setup Support Rules** page identifies issues that might occur when installing the SQL Server Setup support files.</span></span> <span data-ttu-id="5e522-137">설치를 계속하려면 모든 설치 지원 오류를 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-137">You must correct any Setup support failures before continuing with Setup.</span></span>  
  
3.  <span data-ttu-id="5e522-138">**제품 키** 페이지에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]무료 버전을 설치할지 아니면 PID 키가 있는 제품의 프로덕션 버전을 설치할지를 나타내는 옵션 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-138">On the **Product Key** page, select an option button to indicate whether you are installing a free edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or a production version of the product that has a PID key.</span></span> <span data-ttu-id="5e522-139">자세한 내용은 [SQL Server 2014의 버전 및 구성 요소](../editions-and-components-of-sql-server-2016.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5e522-139">For more information, see [Editions and Components of SQL Server 2014](../editions-and-components-of-sql-server-2016.md).</span></span>  
  
4.  <span data-ttu-id="5e522-140">**사용 조건** 페이지에서 사용권 계약을 읽은 다음 사용 조건과 계약 조건에 동의하면 해당 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-140">On the **License Terms** page, read the license agreement, and then select the check box to accept the license terms and conditions.</span></span> <span data-ttu-id="5e522-141">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 개선을 돕기 위해 기능 사용 옵션을 사용하도록 설정하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)]로 보고서를 보낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-141">To help improve [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can also enable the feature usage option and send reports to [!INCLUDE[msCoName](../../includes/msconame-md.md)].</span></span>  
  
5.  <span data-ttu-id="5e522-142">**설치 지원 파일** 페이지에서 **설치** 를 클릭하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]의 설치 지원 파일을 설치 또는 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-142">On the **Setup Support Files** page, click **Install** to install or update the Setup Support files for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
6.  <span data-ttu-id="5e522-143">**설치 역할** 페이지에서 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기능 설치**를 선택하고 **다음** 을 클릭하여 **기능 선택** 페이지를 계속 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-143">On the **Setup Role** page, select **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Feature Installation**, and then click **Next** to continue to the **Feature Selection** page.</span></span>  
  
7.  <span data-ttu-id="5e522-144">**기능 선택** 페이지에서 설치할 기능을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-144">On the **Feature Selection** page, configure which features you want to install.</span></span>  
  
    -   <span data-ttu-id="5e522-145">관리 도구를 설치하려면 **관리 도구 - 기본**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-145">To install the administration tool, select **Management Tools - Basic**.</span></span>  
  
    -   <span data-ttu-id="5e522-146">컨트롤러 서비스를 설치하려면 **Distributed Replay Controller**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-146">To install the controller service, select **Distributed Replay Controller**.</span></span>  
  
    -   <span data-ttu-id="5e522-147">클라이언트 서비스를 설치하려면 **Distributed Replay Client**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-147">To install the client service, select **Distributed Replay Client**.</span></span>  
  
     <span data-ttu-id="5e522-148">**중요**: Distributed Replay Controller를 구성할 때 Distributed Replay Client 서비스를 실행하는 데 사용할 사용자 계정을 하나 이상 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-148">**Important**: When you configure Distributed Replay controller, you can specify one or more user accounts that will be used to run the Distributed Replay client services.</span></span> <span data-ttu-id="5e522-149">다음은 지원되는 계정 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-149">The following is the list of supported accounts:</span></span>  
  
    -   <span data-ttu-id="5e522-150">도메인 사용자 계정</span><span class="sxs-lookup"><span data-stu-id="5e522-150">Domain user account</span></span>  
  
    -   <span data-ttu-id="5e522-151">사용자가 만든 로컬 사용자 계정</span><span class="sxs-lookup"><span data-stu-id="5e522-151">User created local user account</span></span>  
  
    -   <span data-ttu-id="5e522-152">관리자</span><span class="sxs-lookup"><span data-stu-id="5e522-152">Administrator</span></span>  
  
    -   <span data-ttu-id="5e522-153">가상 계정 및 MSA(관리 서비스 계정)</span><span class="sxs-lookup"><span data-stu-id="5e522-153">Virtual account and MSA (Managed Service Account)</span></span>  
  
    -   <span data-ttu-id="5e522-154">Network Services, 로컬 서비스 및 시스템</span><span class="sxs-lookup"><span data-stu-id="5e522-154">Network Services, Local Services, and System</span></span>  
  
     <span data-ttu-id="5e522-155">그룹 계정(로컬 또는 도메인) 및 다른 기본 제공 계정(예: Everyone)은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-155">Group accounts (local or domain) and other built-in accounts (like Everyone) are not accepted.</span></span>  
  
8.  <span data-ttu-id="5e522-156">필요에 따라 줄임표(...) 단추를 클릭하여 공유 기능 디렉터리 경로를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-156">Optionally, click the ellipsis (...) button to change the shared feature directory path.</span></span>  
  
    1.  <span data-ttu-id="5e522-157">32비트 컴퓨터의 기본 설치 경로는 **C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\**</span><span class="sxs-lookup"><span data-stu-id="5e522-157">On 32-bit computers, the default installation path is **C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\**</span></span>  
  
    2.  <span data-ttu-id="5e522-158">64비트 컴퓨터의 기본 설치 경로는 **C:\Program Files (x86)\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\** 입니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-158">On 64-bit computers, the default installation path is **C:\Program Files (x86)\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\**</span></span>  
  
9. <span data-ttu-id="5e522-159">작업을 마쳤으면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-159">When you are finished, click **Next**.</span></span>  
  
10. <span data-ttu-id="5e522-160">**설치 규칙** 페이지에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 프로그램이 컴퓨터 구성의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-160">On the **Installation Rules** page, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup validates your computer configuration.</span></span> <span data-ttu-id="5e522-161">유효성 검사 프로세스가 완료되면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-161">Once the validation process is completed, click **Next**.</span></span>  
  
11. <span data-ttu-id="5e522-162">**디스크 공간 요구 사항** 페이지에서는 지정한 기능에 필요한 디스크 공간을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-162">The **Disk Space Requirements** page calculates the required disk space for the features that you specify.</span></span> <span data-ttu-id="5e522-163">그런 다음 사용 가능한 디스크 공간과 필요한 디스크 공간을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-163">Then it compares the required space to the available disk space.</span></span>  
  
12. <span data-ttu-id="5e522-164">**오류 보고** 페이지에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 개선에 도움이 되도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 보낼 정보를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-164">On the **Error Reporting** page, specify the information that you want to send to [!INCLUDE[msCoName](../../includes/msconame-md.md)] to help improve [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5e522-165">오류 보고 옵션은 기본적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-165">By default, option for error reporting is enabled.</span></span>  
  
13. <span data-ttu-id="5e522-166">**설치 구성 규칙** 페이지에서는 시스템 구성 검사기가 규칙 집합을 하나 더 실행하여 지정한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기능에 대한 컴퓨터 구성의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-166">On the **Installation Configuration Rules** page, the System Configuration Checker will run one more set of rules to validate your computer configuration with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features that you have specified.</span></span>  
  
14. <span data-ttu-id="5e522-167">**프로그램 설치 준비 완료** 페이지에서 **설치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-167">On the **Ready to Install the Program** page, click **Install**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="5e522-168">Distributed Replay를 설치한 후에는 컨트롤러 및 클라이언트 컴퓨터에서 방화벽 규칙을 만들고 각 클라이언트 컴퓨터에 대상 서버에 대한 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-168">After you install Distributed Replay you must create firewall rules on the controller and client computers, and grant each client computer permissions on the target server.</span></span> <span data-ttu-id="5e522-169">자세한 내용은 [설치 후 단계 완료](../../tools/distributed-replay/complete-the-post-installation-steps.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5e522-169">For more information, see [Complete the Post-Installation Steps](../../tools/distributed-replay/complete-the-post-installation-steps.md).</span></span>  
  
 <span data-ttu-id="5e522-170">다음의 추가 항목에 Distributed Replay를 설치하는 다른 방법이 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-170">These additional topics document other ways to install Distributed Replay:</span></span>  
  
-   [<span data-ttu-id="5e522-171">명령 프롬프트에서 Distributed Replay 설치</span><span class="sxs-lookup"><span data-stu-id="5e522-171">Install Distributed Replay from the Command Prompt</span></span>](../../tools/distributed-replay/install-distributed-replay-overview.md)  
  
-   [<span data-ttu-id="5e522-172">구성 파일을 사용하여 Distributed Replay 설치</span><span class="sxs-lookup"><span data-stu-id="5e522-172">Install Distributed Replay Using a Configuration File</span></span>](../../../2014/sql-server/install/install-distributed-replay-using-a-configuration-file.md)  
  
## <a name="net-framework-security"></a><span data-ttu-id="5e522-173">.NET Framework 보안</span><span class="sxs-lookup"><span data-stu-id="5e522-173">.NET Framework Security</span></span>  
 <span data-ttu-id="5e522-174">Distributed Replay 기능을 설치하려면 관리 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-174">You must have administrative permissions in order to install any of the Distributed Replay features.</span></span> <span data-ttu-id="5e522-175">sysadmin 권한을 가진 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인만 테스트 서버의 sysadmin 서버 역할에 클라이언트 서비스 계정을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e522-175">Only a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login having sysadmin permissions can add the client service accounts to the sysadmin server role of the test server.</span></span> <span data-ttu-id="5e522-176">Distributed Replay 보안 고려 사항에 대한 자세한 내용은 [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5e522-176">For more information about Distributed Replay security considerations, see [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e522-177">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5e522-177">See Also</span></span>  
 <span data-ttu-id="5e522-178">[SQL Server 2014 버전에서 지 원하는 기능](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="5e522-178">[Features Supported by the Editions of SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span></span>  
 <span data-ttu-id="5e522-179">[SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md) </span><span class="sxs-lookup"><span data-stu-id="5e522-179">[SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md) </span></span>  
 <span data-ttu-id="5e522-180">[Distributed Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md) </span><span class="sxs-lookup"><span data-stu-id="5e522-180">[Distributed Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md) </span></span>  
 <span data-ttu-id="5e522-181">[관리 도구 명령줄 옵션&#40;Distributed Replay Utility&#41;](../../tools/distributed-replay/administration-tool-command-line-options-distributed-replay-utility.md) </span><span class="sxs-lookup"><span data-stu-id="5e522-181">[Administration Tool Command-line Options &#40;Distributed Replay Utility&#41;](../../tools/distributed-replay/administration-tool-command-line-options-distributed-replay-utility.md) </span></span>  
 [<span data-ttu-id="5e522-182">Distributed Replay 구성</span><span class="sxs-lookup"><span data-stu-id="5e522-182">Configure Distributed Replay</span></span>](../../tools/distributed-replay/configure-distributed-replay.md)  
  
  
