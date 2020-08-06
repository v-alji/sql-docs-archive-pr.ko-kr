---
title: 스케일 아웃 배포의 암호화 키 추가 및 제거 (SSRS Configuration Manager) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- encryption keys [Reporting Services]
- deleting encryption keys
- removing encryption keys
- adding encryption keys
- rskeymgmt utility
- scale-out deployments [Reporting Services]
ms.assetid: 2da86fb3-4b4d-407f-9825-74dcc42486f5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3926e57c1ad3bb884af8debf7f831092b223a3cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742971"
---
# <a name="add-and-remove-encryption-keys-for-scale-out-deployment-ssrs-configuration-manager"></a><span data-ttu-id="0b61e-102">확장 배포의 암호화 키 추가 및 제거(SSRS 구성 관리자)</span><span class="sxs-lookup"><span data-stu-id="0b61e-102">Add and Remove Encryption Keys for Scale-Out Deployment (SSRS Configuration Manager)</span></span>
  <span data-ttu-id="0b61e-103">여러 보고서 서버에서 공유 보고서 서버 데이터베이스를 사용하도록 구성하여 스케일 아웃 배포 모델에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-103">You can run [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in a scale-out deployment model by configuring multiple report servers to use a shared report server database.</span></span> <span data-ttu-id="0b61e-104">스케일 아웃 배포의 멤버 자격은 보고서 서버가 암호화 키를 보고서 서버 데이터베이스에 저장하는지 여부에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-104">Membership in a scale-out deployment is based on whether the report server stores an encryption key in the report server database.</span></span> <span data-ttu-id="0b61e-105">특정 보고서 서버 인스턴스에 대한 암호화 키를 추가 및 제거하여 스케일 아웃 배포 멤버 자격을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-105">You can control scale-out deployment membership by adding and removing encryption keys for specific report server instances.</span></span> <span data-ttu-id="0b61e-106">배포에서 노드를 제거하는 경우 순서에 관계없이 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-106">If you are removing nodes from the deployment, you can remove them in any order.</span></span> <span data-ttu-id="0b61e-107">배포에 노드를 추가할 경우 이미 배포에 포함되어 있는 보고서 서버로부터 새 인스턴스를 조인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-107">If you are adding nodes to a deployment, you must join any new instances from a report server that is already part of the deployment.</span></span>  
  
## <a name="using-the-reporting-services-configuration-tool-to-configure-scale-out-deployment"></a><span data-ttu-id="0b61e-108">Reporting Services 구성 도구를 사용하여 확장 배포 구성</span><span class="sxs-lookup"><span data-stu-id="0b61e-108">Using the Reporting Services Configuration Tool to Configure Scale-Out Deployment</span></span>  
 <span data-ttu-id="0b61e-109">스케일 아웃 배포를 구성하는 가장 쉬운 방법은 Reporting Services 구성 도구를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-109">The easiest way to configure a scale-out deployment is to use the Reporting Services Configuration tool.</span></span> <span data-ttu-id="0b61e-110">자세한 내용 및 단계별 지침은 [기본 모드 보고서 서버 스케일 아웃 배포 구성&#40;SSRS 구성 관리자&#41;](configure-a-native-mode-report-server-scale-out-deployment.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0b61e-110">For more information and step-by-step instructions, see [Configure a Native Mode Report Server Scale-Out Deployment &#40;SSRS Configuration Manager&#41;](configure-a-native-mode-report-server-scale-out-deployment.md).</span></span>  
  
## <a name="using-rskeymgmt-to-configure-scale-out-deployment"></a><span data-ttu-id="0b61e-111">Rskeymgmt를 사용하여 확장 배포 구성</span><span class="sxs-lookup"><span data-stu-id="0b61e-111">Using Rskeymgmt to Configure Scale-Out Deployment</span></span>  
 <span data-ttu-id="0b61e-112">**rskeymgmt** 유틸리티를 사용하여 공유 보고서 서버 데이터베이스를 사용하도록 보고서 서버 인스턴스를 초기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-112">Use the **rskeymgmt** utility to initialize a report server instance to use a shared report server database.</span></span> <span data-ttu-id="0b61e-113">스케일 아웃 배포에 보고서 서버를 추가하려면 보고서 서버를 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-113">Adding a report server to a scale-out deployment requires that you initialize the report server.</span></span> <span data-ttu-id="0b61e-114">초기화를 위해서는 관리자 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-114">Initialization requires administrator permissions.</span></span> <span data-ttu-id="0b61e-115">배포에 참여시킬 보고서 서버를 호스팅하는 원격 컴퓨터에 대해 관리자 자격 증명이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-115">You must have administrator credentials for the remote computer that hosts the report server you are joining to the deployment.</span></span>  
  
#### <a name="how-to-join-a-report-server-to-a-scale-out-deployment-rskeymgmt"></a><span data-ttu-id="0b61e-116">스케일 아웃 배포에 보고서 서버를 참여시키는 방법(rskeymgmt)</span><span class="sxs-lookup"><span data-stu-id="0b61e-116">How to join a report server to a scale-out deployment (rskeymgmt)</span></span>  
  
1.  <span data-ttu-id="0b61e-117">이미 보고서 서버 스케일 아웃 배포의 멤버인 보고서 서버를 호스트하는 컴퓨터에서 로컬로 **rskeymgmt.exe** 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-117">Run **rskeymgmt.exe** locally on the computer that hosts a report server that is already a member of the report server scale-out deployment.</span></span>  
  
2.  <span data-ttu-id="0b61e-118">`-j` 인수를 사용하여 보고서 서버를 보고서 서버 데이터베이스에 참여시킵니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-118">Use the `-j` argument to join a report server to the report server database.</span></span> <span data-ttu-id="0b61e-119">`-m` 및 `-n` 인수를 사용하여 배포에 추가할 원격 보고서 서버 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-119">Use the `-m` and `-n` arguments to specify the remote report server instance you want to add to the deployment.</span></span> <span data-ttu-id="0b61e-120">`-u` 및 `-v` 인수를 사용하여 원격 컴퓨터의 관리자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-120">Use the `-u` and `-v` arguments to specify an administrator account on the remote computer.</span></span> <span data-ttu-id="0b61e-121">같은 컴퓨터에서 여러 보고서 서버 인스턴스를 사용하여 스케일 아웃 배포를 만드는 경우 사용하는 구문이 약간 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-121">If you are creating a scale-out deployment using multiple report server instances on the same computer, the syntax to use is slightly different.</span></span> <span data-ttu-id="0b61e-122">사용해야 할 구문에 대한 자세한 내용은 [rskeymgmt 유틸리티&#40;SSRS&#41;](../tools/rskeymgmt-utility-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0b61e-122">For more information about the syntax you should use, see [rskeymgmt Utility &#40;SSRS&#41;](../tools/rskeymgmt-utility-ssrs.md).</span></span>  
  
     <span data-ttu-id="0b61e-123">다음 예에서는 원격 보고서 서버를 스케일 아웃 배포에 조인하려는 경우 지정해야 하는 인수에 대해 설명합니다. 원격 컴퓨터에서 관리자 권한이 있으면 자격 증명을 생략해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-123">The following example illustrates the arguments you must specify if you are joining a remote report server to a scale-out deployment (you can omit credentials if you have administrator permissions on the remote computer):</span></span>  
  
    ```  
    rskeymgmt -j -m <remotecomputer> -n <namedreportserverinstance> -u <administratoraccount> -v <administratorpassword>  
    ```  
  
#### <a name="how-to-remove-a-report-server-from-a-scale-out-deployment-rskeymgmt"></a><span data-ttu-id="0b61e-124">스케일 아웃 배포에서 보고서 서버를 제거하는 방법(rskeymgmt)</span><span class="sxs-lookup"><span data-stu-id="0b61e-124">How to remove a report server from a scale-out deployment (rskeymgmt)</span></span>  
  
1.  <span data-ttu-id="0b61e-125">제거하려는 보고서 서버의 reportserver.config 파일을 열고 설치 ID를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-125">Open the rsreportserver.config file of the report server you want to remove and find the installation ID.</span></span> <span data-ttu-id="0b61e-126">이 파일의 기본 위치는 Program Files\Microsoft SQL Server\MSSQL.*n*\Reporting Services\ReportServer입니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-126">By default, this file is located at Program Files\Microsoft SQL Server\MSSQL.*n*\Reporting Services\ReportServer).</span></span>  
  
     <span data-ttu-id="0b61e-127">단일 인스턴스를 설치한 경우 컴퓨터에는 rsreportserver.config 파일이 하나만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-127">If you installed a single instance, there will only be one rsreportserver.config file on the computer.</span></span> <span data-ttu-id="0b61e-128">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인스턴스를 여러 개 설치한 경우 Reporting Services 구성 도구의 서버 상태 페이지를 사용하여 제거하려는 보고서 서버의 인스턴스 식별자(예: MSSQL.2)를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-128">If multiple instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] are installed, use the Server Status page in the Reporting Services Configuration tool to find the instance identifier (for example, MSSQL.2) for the report server that you want to remove.</span></span> <span data-ttu-id="0b61e-129">보고서 서버 인스턴스에 대한 프로그램 파일을 저장하는 폴더 이름은 인스턴스 식별자를 기반으로 합니다(예: Program Files\Microsoft SQL Server\MSSQL.2).</span><span class="sxs-lookup"><span data-stu-id="0b61e-129">The name of the folder that stores the program files for the report server instance will be based on the instance identifier (for example, Program Files\Microsoft SQL Server\MSSQL.2).</span></span>  
  
2.  <span data-ttu-id="0b61e-130">**rskeymgmt.exe**를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-130">Run **rskeymgmt.exe**.</span></span> <span data-ttu-id="0b61e-131">보고서 서버 스케일 아웃 배포에 속하는 어떠한 보고서 서버에 대해서도 이 프로그램을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-131">You can run it on any report server that is part of the report server scale-out deployment.</span></span>  
  
3.  <span data-ttu-id="0b61e-132">ph x="1" /&gt; 인수를 사용하여 스케일 아웃 배포에서 보고서 서버 인스턴스를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-132">Use the `-r` argument to release the report server instance from the scale-out deployment.</span></span> <span data-ttu-id="0b61e-133">다음은 인수 지정 예입니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-133">The following example illustrates the arguments you must specify:</span></span>  
  
    ```  
    rskeymgmt -r <installation ID>  
    ```  
  
 <span data-ttu-id="0b61e-134">이 단계를 수행하면 스케일 아웃 배포에서 보고서 서버가 제거되지만, 보고서 서버에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인스턴스의 설치가 제거되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-134">These steps remove the report server from a scale-out deployment, but they do not uninstall the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance on the report server.</span></span> <span data-ttu-id="0b61e-135">스케일 아웃 배포에서 보고서 서버를 제거한 후 해당 서버에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]가 더 이상 필요하지 않은 경우 서버에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b61e-135">After you remove the report server from the scale-out deployment, you can uninstall [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] from the server if you no longer need [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] on that server.</span></span> <span data-ttu-id="0b61e-136">자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 [SQL Server의 기존 인스턴스 제거&#40;설치 프로그램&#41;](../../sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0b61e-136">For information, see [Uninstall an Existing Instance of SQL Server &#40;Setup&#41;](../../sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b61e-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0b61e-137">See Also</span></span>  
 <span data-ttu-id="0b61e-138">[SSRS Configuration Manager &#40;암호화 키 구성 및 관리&#41;](ssrs-encryption-keys-manage-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="0b61e-138">[Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;](ssrs-encryption-keys-manage-encryption-keys.md) </span></span>  
 [<span data-ttu-id="0b61e-139">보고서 서버 초기화&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="0b61e-139">Initialize a Report Server &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-initialize-a-report-server.md)  
  
  
