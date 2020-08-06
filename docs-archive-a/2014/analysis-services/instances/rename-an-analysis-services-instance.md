---
title: Analysis Services 인스턴스 이름 바꾸기 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- instances of Analysis Services, renaming
- renaming instances of Analysis Services
- names [Analysis Services], renaming instances
- names [Analysis Services]
ms.assetid: 87494741-4a2e-4fed-8061-418fd1e111c3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 763986d82dda7424f2187daf401424fd256ddd64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733251"
---
# <a name="rename-an-analysis-services-instance"></a><span data-ttu-id="fcc8a-102">Analysis Services 인스턴스 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="fcc8a-102">Rename an Analysis Services Instance</span></span>
  <span data-ttu-id="fcc8a-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] **인스턴스 이름 바꾸기** 대화 상자를 사용 하 여의 기존 인스턴스 이름을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-103">You can rename an existing instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] by using the **Rename Instance** dialog box.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fcc8a-104">인스턴스의 이름을 바꾸는 동안 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스 이름 바꾸기 도구는 승격된 권한으로 실행되어 해당 인스턴스와 연결된 레지스트리 항목, Windows 서비스 이름 및 보안 계정을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-104">While renaming the instance, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instance Rename tool runs under elevated privileges, updating the Windows service name, security accounts, and registry entries associated with that instance.</span></span> <span data-ttu-id="fcc8a-105">이러한 동작이 수행되도록 하려면 이 도구를 로컬 시스템 관리자로 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-105">To ensure that these actions are performed, be sure to run this tool as a local system administrator.</span></span>  
  
 <span data-ttu-id="fcc8a-106">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스 이름 바꾸기 도구는 원래 인스턴스에 대해 생성된 프로그램 폴더를 수정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-106">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instance Rename tool does not modify the program folder that was created for the original instance.</span></span> <span data-ttu-id="fcc8a-107">이름을 바꾸는 인스턴스와 일치하도록 프로그램 폴더 이름을 수정하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-107">Do not modify the program folder name to match the instance you are renaming.</span></span> <span data-ttu-id="fcc8a-108">프로그램 폴더 이름을 변경하면 설치 프로그램이 설치를 복구하거나 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-108">Changing a program folder name can prevent Setup from repairing or uninstalling the installation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fcc8a-109">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스 이름 바꾸기 도구는 클러스터 환경에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-109">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instance Rename tool is not supported for use in a cluster environment.</span></span>  
  
### <a name="to-rename-an-instance-of-analysis-services"></a><span data-ttu-id="fcc8a-110">Analysis Services의 인스턴스 이름을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="fcc8a-110">To rename an instance of Analysis Services</span></span>  
  
1.  <span data-ttu-id="fcc8a-111">C:\Program Files\Microsoft SQL Server\110\tools\binn\managementstudio에서 **인스턴스 이름 바꾸기** 도구인 **asinstancerename.exe**를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-111">Launch the **Instance Rename** tool, **asinstancerename.exe**, from C:\Program Files\Microsoft SQL Server\110\Tools\Binn\ManagementStudio.</span></span>  
  
2.  <span data-ttu-id="fcc8a-112">**인스턴스 이름 바꾸기** 대화 상자의 **이름을 바꿀 인스턴스** 목록에서 이름을 바꿀 인스턴스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-112">In the **Rename Instance** dialog box, in the **Instance to rename** list, select the instance that you want to rename.</span></span>  
  
3.  <span data-ttu-id="fcc8a-113">**새 인스턴스 이름** 입력란에 인스턴스의 새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-113">In the **New instance name** box, enter the new name for the instance.</span></span>  
  
4.  <span data-ttu-id="fcc8a-114">사용자 이름과 암호가 올바른지 확인하고 **이름 바꾸기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-114">Verify that the user name and password are correct, and then click **Rename**.</span></span>  
  
     <span data-ttu-id="fcc8a-115">이름을 변경하는 동안 Analysis Services 인스턴스가 중지되고 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-115">The Analysis Services instance will be stopped and restarted as part of the name change.</span></span>  
  
### <a name="post-rename-checklist"></a><span data-ttu-id="fcc8a-116">이름을 바꾼 후 검사할 목록</span><span class="sxs-lookup"><span data-stu-id="fcc8a-116">Post-rename checklist</span></span>  
  
1.  <span data-ttu-id="fcc8a-117">이름을 바꾼 인스턴스에서 실행되는 데이터베이스에 대한 액세스를 다시 시작하려면 Excel 또는 다른 클라이언트 애플리케이션에서 데이터 연결을 수동으로 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-117">To resume access to databases that are running on the renamed instance, you will need to manually update the data connections in Excel or other client applications.</span></span> <span data-ttu-id="fcc8a-118">이름을 바꾼 인스턴스를 참조할 수 있는 Reporting Services 공유 데이터 원본, Excel ODC 파일 또는 BI 의미 체계 모델 연결 파일 등 미리 정의된 연결도 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-118">Also check any predefined connections, such as Reporting Services shared data sources, Excel ODC files, or BI Semantic Model connection files that might reference the instance you just renamed.</span></span> <span data-ttu-id="fcc8a-119">자세한 내용은 [Analysis Services에 연결](connect-to-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-119">For more information, see [Connect to Analysis Services](connect-to-analysis-services.md).</span></span>  
  
2.  <span data-ttu-id="fcc8a-120">데이터베이스를 백업, 동기화 또는 처리하는 데 일상적으로 사용하는 PowerShell 스크립트 또는 AMO 스크립트를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-120">Update PowerShell scripts or AMO scripts that you routinely use to backup, synchronize, or process databases.</span></span>  
  
3.  <span data-ttu-id="fcc8a-121">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 사용하는 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]프로젝트의 프로젝트 속성을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-121">Update project properties for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projects that you work with in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="fcc8a-122">테이블 형식 모드 서버 인스턴스의 경우 model.bim 파일의 작업 영역 서버 속성과 프로젝트의 서버 속성을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-122">For tabular mode server instances, be sure to update the Workspace Server property on the model.bim file, as well as the Server property on the project.</span></span>  
  
4.  <span data-ttu-id="fcc8a-123">서비스 계정을 지정한 방법에 따라 서비스에 데이터 액세스 권한을 부여하는 데이터베이스 로그인 또는 파일 사용 권한을 업데이트해야 할 수도 있습니다. 예를 들어 서비스 계정을 사용하여 데이터를 처리하거나 다른 서버의 연결된 개체에 액세스 하는 경우가 여기에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-123">Depending on how you specified the service account, you might need to update database logins or file permissions that grant data access rights to the service (for example, if you use the service account to process data or access linked objects on another server).</span></span>  
  
     <span data-ttu-id="fcc8a-124">가상 계정을 사용하여 서비스를 프로비전하는 경우 데이터베이스 로그인 또는 파일 사용 권한을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-124">Updating a database login or file permissions will be necessary if you used a virtual account to provision the service.</span></span> <span data-ttu-id="fcc8a-125">가상 계정은 인스턴스 이름을 사용하여 생성되므로 인스턴스의 이름을 바꾸는 경우 가상 계정도 동시에 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-125">Virtual accounts are based on the instance name, so if you rename the instance, the virtual account is also updated at the same time.</span></span> <span data-ttu-id="fcc8a-126">즉 이전 인스턴스에 대해 만든 이전 로그인 또는 사용 권한은 더 이상 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-126">This means that any previous logins or permissions that you created for the previous instance are no longer valid.</span></span>  
  
     <span data-ttu-id="fcc8a-127">다음 예제에서 이에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-127">The following example provides an illustration.</span></span> <span data-ttu-id="fcc8a-128">기본 가상 계정을 사용 하 여 "Tabular" 라는 인스턴스로 테이블 형식 모드 서버를 설치 했다고 가정 합니다. 그러면 다음과 같은 구성이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-128">Suppose you installed a tabular mode server as an instance named "Tabular" using the default virtual account, resulting in the following configuration:</span></span>  
  
    1.  <span data-ttu-id="fcc8a-129">인스턴스 이름 = \<server> \Tabular</span><span class="sxs-lookup"><span data-stu-id="fcc8a-129">Instance name = \<server>\TABULAR</span></span>  
  
    2.  <span data-ttu-id="fcc8a-130">Service name = MSOLAP$TABULAR</span><span class="sxs-lookup"><span data-stu-id="fcc8a-130">Service name = MSOLAP$TABULAR</span></span>  
  
    3.  <span data-ttu-id="fcc8a-131">Virtual account = NT Service\ MSOLAP$TABULAR</span><span class="sxs-lookup"><span data-stu-id="fcc8a-131">Virtual account = NT Service\ MSOLAP$TABULAR</span></span>  
  
     <span data-ttu-id="fcc8a-132">이제 인스턴스의 이름을 "TAB2"로 변경 한다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-132">Now suppose you rename the instance to "TAB2".</span></span> <span data-ttu-id="fcc8a-133">이름을 변경하면 구성이 다음과 같이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-133">As a result of the name change, your configuration would now look like the following:</span></span>  
  
    1.  <span data-ttu-id="fcc8a-134">인스턴스 이름 = \<server> \Tab2</span><span class="sxs-lookup"><span data-stu-id="fcc8a-134">Instance name = \<server>\TAB2</span></span>  
  
    2.  <span data-ttu-id="fcc8a-135">Service name = MSOLAP$TAB2</span><span class="sxs-lookup"><span data-stu-id="fcc8a-135">Service name = MSOLAP$TAB2</span></span>  
  
    3.  <span data-ttu-id="fcc8a-136">Virtual account = NT Service\ MSOLAP$TAB2</span><span class="sxs-lookup"><span data-stu-id="fcc8a-136">Virtual account = NT Service\ MSOLAP$TAB2</span></span>  
  
     <span data-ttu-id="fcc8a-137">여기에서 볼 수 있듯이 이전에 "NT Service \ MSOLAP $ TABULAR"에 부여 된 데이터베이스 및 파일 사용 권한은 더 이상 유효 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-137">As you can see, database and file permissions that were previously granted to "NT Service\ MSOLAP$TABULAR" are no longer valid.</span></span> <span data-ttu-id="fcc8a-138">서비스에서 수행 하는 태스크 및 작업이 이전과 같이 실행 되도록 하려면 이제 "NT Service \ MSOLAP $ TAB2"에 새 데이터베이스 및 파일 사용 권한을 부여 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcc8a-138">To ensure that tasks and operations performed by the service run as before, you would now need to grant new database and file permissions to "NT Service\ MSOLAP$TAB2".</span></span>  
  
  
