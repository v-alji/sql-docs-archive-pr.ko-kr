---
title: 구성 파일을 사용 하 여 SQL Server 2014 설치 | Microsoft Docs
ms.custom: ''
ms.date: 01/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: a832153a-6775-4bed-83f0-55790766d885
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a2f09ad6253762fe5b525f6c918931f4806c84c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729756"
---
# <a name="install-sql-server-2014-using-a-configuration-file"></a><span data-ttu-id="d3e45-102">구성 파일을 사용하여 SQL Server 2014 설치</span><span class="sxs-lookup"><span data-stu-id="d3e45-102">Install SQL Server 2014 Using a Configuration File</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d3e45-103">설치 시 시스템 기본값 및 런타임 입력을 기반으로 구성 파일을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-103">Setup provides the ability to generate a configuration file based upon the system default and run-time inputs.</span></span> <span data-ttu-id="d3e45-104">구성 파일을 사용하면 동일한 구성으로 회사 전체에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-104">You can use the configuration file to deploy [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] throughout the enterprise with the same configuration.</span></span> <span data-ttu-id="d3e45-105">또한 Setup.exe를 실행하는 배치 파일을 만들어 수동 설치를 전사적으로 표준화할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-105">You can also standardize manual installations throughout the enterprise, by creating a batch file that launches Setup.exe.</span></span>  
  
 <span data-ttu-id="d3e45-106">구성 파일은 명령 프롬프트에서 설치할 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-106">Setup supports the use of the configuration file only through the command prompt.</span></span> <span data-ttu-id="d3e45-107">구성 파일을 사용할 때 매개 변수의 처리 순서는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-107">The processing order of the parameters while using the configuration file is outlined below:</span></span>  
  
-   <span data-ttu-id="d3e45-108">구성 파일이 패키지의 기본값을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-108">The configuration file overwrites the defaults in a package</span></span>  
  
-   <span data-ttu-id="d3e45-109">명령줄 값이 구성 파일의 값을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-109">Command-line values overwrite the values in the configuration file</span></span>  
  
 <span data-ttu-id="d3e45-110">구성 파일을 사용하여 각 설치의 매개 변수와 값을 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-110">The configuration file can be used to track the parameters and values for each installation.</span></span> <span data-ttu-id="d3e45-111">따라서 구성 파일은 설치를 검사 및 감사할 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-111">This makes the configuration file useful for verifying and auditing the installations.</span></span>  
  
## <a name="configuration-file-structure"></a><span data-ttu-id="d3e45-112">구성 파일 구조</span><span class="sxs-lookup"><span data-stu-id="d3e45-112">Configuration File Structure</span></span>  
 <span data-ttu-id="d3e45-113">ConfigurationFile.ini 파일은 매개 변수(이름/값 쌍)와 설명이 있는 텍스트 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-113">The ConfigurationFile.ini file is a text file with parameters (name/value pair) and descriptive comments.</span></span>  
  
 <span data-ttu-id="d3e45-114">다음은 ConfigurationFile.ini 파일의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-114">The following is an example of a ConfigurationFile.ini file:</span></span>  
  
```  
; Microsoft SQL Server Configuration file  
[OPTIONS]  
; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE.   
; This is a required parameter.   
ACTION="Install"  
; Specifies features to install, uninstall, or upgrade.   
; The list of top-level features include SQL, AS, RS, IS, and Tools.   
; The SQL feature will install the database engine, replication, and full-text.   
; The Tools feature will install Management Tools, Books online,   
; SQL Server Data Tools, and other shared components.   
FEATURES=SQL,Tools  
```  
  
#### <a name="how-to-generate-a-configuration-file"></a><span data-ttu-id="d3e45-115">구성 파일을 생성하는 방법</span><span class="sxs-lookup"><span data-stu-id="d3e45-115">How to generate a configuration file</span></span>  
  
1.  <span data-ttu-id="d3e45-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 미디어를 넣고</span><span class="sxs-lookup"><span data-stu-id="d3e45-116">Insert the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation media.</span></span> <span data-ttu-id="d3e45-117">루트 폴더에서 Setup.exe를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-117">From the root folder, double-click Setup.exe.</span></span> <span data-ttu-id="d3e45-118">네트워크 공유에서 설치하려면 공유에서 루트 폴더를 찾은 다음 Setup.exe를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-118">To install from a network share, locate the root folder on the share, and then double-click Setup.exe.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d3e45-119">Express Edition 설치 프로그램이 구성 파일을 자동으로 만들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-119">Express Edition setup does not create a configuration file automatically.</span></span> <span data-ttu-id="d3e45-120">다음 명령으로 설치 프로그램을 시작하고 구성 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-120">The following command will start  setup and create a configuration file.</span></span>  
    >   
    >  <span data-ttu-id="d3e45-121">SETUP.exe /UIMODE = Normal /ACTION = INSTALL</span><span class="sxs-lookup"><span data-stu-id="d3e45-121">SETUP.exe /UIMODE=Normal /ACTION=INSTALL</span></span>  
  
2.  <span data-ttu-id="d3e45-122">마법사의 안내에 따르면 **설치 준비 완료** 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-122">Follow the wizard through to the **Ready to Install** page.</span></span> <span data-ttu-id="d3e45-123">구성 파일의 경로는 **설치 준비 완료** 페이지의 구성 파일 경로 섹션에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-123">The path to the configuration file is specified in the **Ready to Install** page in the configuration file path section.</span></span> <span data-ttu-id="d3e45-124">을 설치 하는 방법에 대 한 자세한 내용은 설치 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [마법사 &#40;설치&#41;에서 SQL Server 2014 설치 ](install-sql-server-from-the-installation-wizard-setup.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d3e45-124">For more information about how to install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](install-sql-server-from-the-installation-wizard-setup.md).</span></span>  
  
3.  <span data-ttu-id="d3e45-125">설치를 실제로 완료하지는 않고 INI 파일을 생성하기 위해 설치를 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-125">Cancel the setup without actually completing the installation, to generate the INI file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d3e45-126">설치 프로그램은 암호 등과 같은 기밀 정보를 제외하고 수행했던 동작에 적합한 모든 매개 변수를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-126">The setup infrastructure writes out all the appropriate parameters for the actions that were run, with the exception of sensitive information such as passwords.</span></span> <span data-ttu-id="d3e45-127">/IAcceptSQLServerLicenseTerms 매개 변수도 구성 파일에 기록되지 않기 때문에 구성 파일을 수정하거나 명령 프롬프트에서 값을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-127">The /IAcceptSQLServerLicenseTerms parameter is also not written out to the configuration file and requires either a modification of the configuration file or a value to be supplied at the command prompt.</span></span> <span data-ttu-id="d3e45-128">자세한 내용은 [명령 프롬프트에서 SQL Server 2014 설치](install-sql-server-from-the-command-prompt.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d3e45-128">For more information, see [Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md).</span></span> <span data-ttu-id="d3e45-129">또한 일반적으로 명령 프롬프트에서 값을 입력하지 않는 부울 매개 변수에 대한 값도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-129">In addition, a value is included for Boolean parameters where a value is usually not supplied through the command prompt.</span></span>  
  
## <a name="using-the-configuration-file-to-install-ssnoversion"></a><span data-ttu-id="d3e45-130">구성 파일을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3e45-130">Using the Configuration File to Install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 <span data-ttu-id="d3e45-131">구성 파일은 명령줄 설치에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-131">You can only use the configuration file on command-line installations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3e45-132">구성 파일을 변경해야 할 경우 구성 파일을 복사한 후 이 복사본을 변경하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-132">If you need to make changes to the configuration file, we recommend that you make a copy and work with the copy.</span></span>  
  
#### <a name="how-to-use-a-configuration-file-to-install-a-stand-alone-ssnoversion-instance"></a><span data-ttu-id="d3e45-133">구성 파일을 사용하여 독립 실행형 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 설치하는 방법</span><span class="sxs-lookup"><span data-stu-id="d3e45-133">How to use a configuration file to install a stand-alone [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance</span></span>  
  
-   <span data-ttu-id="d3e45-134">명령 프롬프트에서 설치를 실행하고 *ConfigurationFile* 매개 변수를 사용하여 ConfigurationFile.ini를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-134">Run the installation through the command prompt and supply the ConfigurationFile.ini using the *ConfigurationFile* parameter.</span></span>  
  
#### <a name="how-to-use-a-configuration-file-to-prepare-and-complete-an-image-of-a-stand-alone-ssnoversion-instance-sysprep"></a><span data-ttu-id="d3e45-135">구성 파일을 사용하여 독립 실행형 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스(SysPrep)의 이미지를 준비하고 완료하는 방법</span><span class="sxs-lookup"><span data-stu-id="d3e45-135">How to use a configuration file to prepare and complete an image of a stand-alone [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance (SysPrep)</span></span>  
  
1.  <span data-ttu-id="d3e45-136">같은 시스템에 하나 이상의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 준비하고 구성하려면</span><span class="sxs-lookup"><span data-stu-id="d3e45-136">To prepare one or more instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and configure them on the same machine.</span></span>  
  
    -   <span data-ttu-id="d3e45-137">설치 센터의 **고급** 페이지에서 **독립 실행형 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이미지 준비**를 실행하고 이미지 준비 구성 파일을 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-137">Run **Image preparation of a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** from the **Advanced** page of the Installation Center and capture the prepare image configuration file.</span></span>  
  
    -   <span data-ttu-id="d3e45-138">템플릿과 동일한 이미지 준비 구성 파일을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-138">Use the same prepare image configuration file as a template to prepare more instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
    -   <span data-ttu-id="d3e45-139">설치 센터의 **고급** 페이지에서 **독립 실행형 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 준비 인스턴스의 이미지 완료**를 실행하여 시스템에서 준비 인스턴스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-139">Run **Image completion of a prepared stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** from the **Advanced** page of the Installation Center to configure a prepared instances on the machine.</span></span>  
  
2.  <span data-ttu-id="d3e45-140">Windows SysPrep 도구를 사용하여 구성되지 않은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 준비 인스턴스를 포함한 운영 체제 이미지를 준비하려면</span><span class="sxs-lookup"><span data-stu-id="d3e45-140">To prepare an image of the operating system including an unconfigured prepared instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], using Windows SysPrep tool.</span></span>  
  
    -   <span data-ttu-id="d3e45-141">설치 센터의 고급 페이지에서 **독립 실행형 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이미지 준비**를 실행하고 이미지 준비 구성 파일을 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-141">Run the **Image preparation of a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** from the Advanced page of the Installation Center and capture the prepare image configuration file.</span></span>  
  
    -   <span data-ttu-id="d3e45-142">설치 센터의 **고급** 페이지에서 **독립 실행형 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 준비 인스턴스의 이미지 완료**를 실행하지만 완료된 구성 파일을 캡처한 다음 **완료 준비** 페이지에서 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-142">Run the **Image completion of a prepared stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** from the **Advanced** page of the Installation Center, but cancel it on the **Ready to Complete** page after capturing the complete configuration file.</span></span>  
  
    -   <span data-ttu-id="d3e45-143">이미지 완료 구성 파일은 Windows 이미지와 함께 저장하여 준비 인스턴스의 구성을 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-143">The complete image configuration file can be stored with the Windows image for automating the configuration of the prepared instances.</span></span>  
  
#### <a name="how-to-install-a-ssnoversion-failover-cluster-using-the-configuration-file"></a><span data-ttu-id="d3e45-144">구성 파일을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치(Failover) 클러스터를 설치하는 방법</span><span class="sxs-lookup"><span data-stu-id="d3e45-144">How to install a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster using the configuration file</span></span>  
  
1.  <span data-ttu-id="d3e45-145">통합 설치 옵션(한 노드에 하나의 노드 장애 조치(Failover) 클러스터를 만들고, 추가할 노드에서 AddNode를 실행하여 노드를 추가함):</span><span class="sxs-lookup"><span data-stu-id="d3e45-145">Integrated Install option (create a single node failover cluster on a node and for additional nodes, run AddNode on them):</span></span>  
  
    -   <span data-ttu-id="d3e45-146">"장애 조치(Failover) 클러스터 설치" 옵션을 실행하고 모든 설치 설정이 나열된 구성 파일을 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-146">Run the "Install a Failover Cluster" option and capture the configuration file that lists all the installation settings.</span></span>  
  
    -   <span data-ttu-id="d3e45-147">*ConfigurationFile* 매개 변수를 입력하여 명령줄 장애 조치(failover) 클러스터 설치를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-147">Run the command-line failover cluster install by supplying the *ConfigurationFile* parameter.</span></span>  
  
    -   <span data-ttu-id="d3e45-148">추가할 노드에서 AddNode를 실행하여 기존 장애 조치(Failover) 클러스터에 적용되는 ConfigurationFile.ini 파일을 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-148">On an additional node to be added, run AddNode to capture the ConfigurationFile.ini file applicable to the existing failover cluster.</span></span>  
  
    -   <span data-ttu-id="d3e45-149">ConfigurationFile 매개 변수를 사용하여 동일한 구성 파일을 입력함으로써 장애 조치(Failover) 클러스터에 추가할 모든 노드에서 명령줄 AddNode를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-149">Run the command-line AddNode on all the additional nodes that will join the failover cluster, by supplying the same configuration file using the ConfigurationFile parameter.</span></span>  
  
2.  <span data-ttu-id="d3e45-150">고급 설치 옵션(모든 장애 조치(Failover) 클러스터 노드에 장애 조치(Failover) 클러스터를 준비하고 모든 노드를 준비한 후 공유 디스크를 소유하는 노드에서 실행을 완료함):</span><span class="sxs-lookup"><span data-stu-id="d3e45-150">Advanced install option (prepare failover cluster on all failover cluster nodes, then, after preparing all the nodes, run complete on the node that owns the shared disk):</span></span>  
  
    -   <span data-ttu-id="d3e45-151">노드 중 하나에서 **준비** 를 실행하고 ConfigurationFile.ini 파일을 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-151">Run **Prepare** on one of the nodes, and capture the ConfigurationFile.ini file.</span></span>  
  
    -   <span data-ttu-id="d3e45-152">동일한 ConfigurationFile.ini 파일을 입력하여 장애 조치(Failover) 클러스터를 위해 준비할 모든 노드에서 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-152">Supply the same ConfigurationFile.ini file to Setup on all the nodes that will be prepared for the failover cluster.</span></span>  
  
    -   <span data-ttu-id="d3e45-153">모든 노드를 준비한 후 공유 디스크를 소유하는 노드에서 전체 장애 조치(Failover) 클러스터 작업을 실행하고 ConfigurationFile.ini 파일을 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-153">After all the nodes have been prepared, run a complete failover cluster operation on the node that owns the shared disk and capture the ConfigurationFile.ini file.</span></span>  
  
    -   <span data-ttu-id="d3e45-154">그런 다음 이 ConfigurationFile.ini 파일을 입력하여 장애 조치(Failover) 클러스터를 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-154">You can then supply this ConfigurationFile.ini file to complete the failover cluster.</span></span>  
  
#### <a name="how-to-add-or-remove-a-node-to-a-ssnoversion-failover-cluster-using-the-configuration-file"></a><span data-ttu-id="d3e45-155">구성 파일을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치(Failover) 클러스터에 대해 노드를 추가하거나 제거하는 방법</span><span class="sxs-lookup"><span data-stu-id="d3e45-155">How to add or remove a node to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster using the configuration file</span></span>  
  
-   <span data-ttu-id="d3e45-156">이전에 장애 조치(Failover) 클러스터에 대해 노드를 추가하거나 제거할 때 사용했던 구성 파일이 있을 경우 이 파일을 다시 사용하여 노드를 추가하거나 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-156">If you have a configuration file that was previously used to add a node to or remove a node from a failover cluster, you can reuse that same file to add or remove additional nodes.</span></span>  
  
#### <a name="how-to-upgrade-a-ssnoversion-failover-cluster-using-the-configuration-file"></a><span data-ttu-id="d3e45-157">구성 파일을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치(Failover) 클러스터를 업그레이드하는 방법</span><span class="sxs-lookup"><span data-stu-id="d3e45-157">How to upgrade a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster using the configuration file</span></span>  
  
1.  <span data-ttu-id="d3e45-158">패시브 노드에서 업그레이드를 실행하고 ConfigurationFile.ini 파일을 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-158">Run upgrade on the passive node and capture the ConfigurationFile.ini file.</span></span> <span data-ttu-id="d3e45-159">실제 업그레이드를 수행하거나, 실제 업그레이드를 수행하지 않고 종료 시 끝내는 방법을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-159">You can do this either by performing the actual upgrade, or exiting at the end without doing the actual upgrade.</span></span>  
  
2.  <span data-ttu-id="d3e45-160">업그레이드할 모든 추가 노드에서 ConfigurationFile.ini 파일을 입력하여 프로세스를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-160">On all the additional nodes to be upgraded, supply the ConfigurationFile.ini file to complete the process.</span></span>  
  
## <a name="sample-syntax"></a><span data-ttu-id="d3e45-161">예제 구문</span><span class="sxs-lookup"><span data-stu-id="d3e45-161">Sample Syntax</span></span>  
 <span data-ttu-id="d3e45-162">다음은 구성 파일을 사용하는 방법을 보여 주는 예입니다.</span><span class="sxs-lookup"><span data-stu-id="d3e45-162">Following are some examples on how to use the configuration file:</span></span>  
  
-   <span data-ttu-id="d3e45-163">명령 프롬프트에 구성 파일을 지정하기</span><span class="sxs-lookup"><span data-stu-id="d3e45-163">To specify the configuration file at the command prompt:</span></span>  
  
```  
Setup.exe /ConfigurationFile=MyConfigurationFile.INI  
```  
  
-   <span data-ttu-id="d3e45-164">구성 파일 대신 명령 프롬프트에 암호 지정하기</span><span class="sxs-lookup"><span data-stu-id="d3e45-164">To specify passwords at the command prompt instead of in the configuration file:</span></span>  
  
```  
Setup.exe /SQLSVCPASSWORD="************" /AGTSVCPASSWORD="************" /ASSVCPASSWORD="************" /ISSVCPASSWORD="************" /RSSVCPASSWORD="************" /ConfigurationFile=MyConfigurationFile.INI  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3e45-165">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d3e45-165">See Also</span></span>  
 <span data-ttu-id="d3e45-166">[명령 프롬프트에서 SQL Server 2014 설치](install-sql-server-from-the-command-prompt.md) </span><span class="sxs-lookup"><span data-stu-id="d3e45-166">[Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md) </span></span>  
 <span data-ttu-id="d3e45-167">[SQL Server 장애 조치(Failover) 클러스터 설치](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md) </span><span class="sxs-lookup"><span data-stu-id="d3e45-167">[SQL Server Failover Cluster Installation](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md) </span></span>  
 [<span data-ttu-id="d3e45-168">SQL Server 장애 조치(Failover) 클러스터 업그레이드</span><span class="sxs-lookup"><span data-stu-id="d3e45-168">Upgrade a SQL Server Failover Cluster</span></span>](../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance.md)  
  
  
