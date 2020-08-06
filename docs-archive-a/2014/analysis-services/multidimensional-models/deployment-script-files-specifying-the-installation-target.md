---
title: 설치 대상 지정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input files [Analysis Services]
- installation targets [Analysis Services]
- Analysis Services deployments, installation targets
- Analysis Services Deployment Wizard, installation targets
- deploying [Analysis Services], installation targets
- modifying installation targets
ms.assetid: cb706817-6f63-4771-92c3-b70030bbce3d
author: minewiskan
ms.author: owend
ms.openlocfilehash: e830fc353898e3ec835b338e84765a0cad0de43f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651934"
---
# <a name="specifying-the-installation-target"></a><span data-ttu-id="0e81b-102">설치 대상 지정</span><span class="sxs-lookup"><span data-stu-id="0e81b-102">Specifying the Installation Target</span></span>
  <span data-ttu-id="0e81b-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]배포 마법사는 deploymenttargets 파일에서 설치 대상 정보를 읽습니다. \<*project name*></span><span class="sxs-lookup"><span data-stu-id="0e81b-103">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard reads the installation target information from the \<*project name*>.deploymenttargets file.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="0e81b-104">프로젝트를 빌드할 때이 파일을 만듭니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0e81b-104">creates this file when you build the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="0e81b-105">속성 페이지 대화 상자의 **배포** 페이지에 지정 된 데이터베이스 및 서버를 사용 하 여 *\<project name>* **Properties Pages** \<*project name*> .targets 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0e81b-105">uses the database and server specified on the **Deployment** page of the *\<project name>* **Properties Pages** dialog box to create the \<*project name*>.targets file.</span></span>  
  
## <a name="modifying-the-installation-target-for-deployment"></a><span data-ttu-id="0e81b-106">배포를 위한 설치 대상 수정</span><span class="sxs-lookup"><span data-stu-id="0e81b-106">Modifying the Installation Target for Deployment</span></span>  
 <span data-ttu-id="0e81b-107">일부 경우에 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 배포 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 페이지에 지정된 것과 다른 데이터베이스 또는 **인스턴스에** 프로젝트를 배포해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e81b-107">In some situations, you may need to deploy an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project to a database or [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance that is different than the one specified on the **Deployment** page.</span></span> <span data-ttu-id="0e81b-108">예를 들어 배포 전에 테스트를 위해 서버에 프로젝트를 배포한 다음 테스트를 마친 후에 프로덕션 서버에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e81b-108">For example, you may want to deploy the project to a server for testing before deployment, and then deploy it to a production server after testing is finished.</span></span> <span data-ttu-id="0e81b-109">또한 네트워크 로드 균형 조정 클러스터의 여러 프로덕션 서버나 준비 서버(staging server) 및 프로덕션 서버에 완료되고 테스트를 마친 프로젝트를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e81b-109">You may also want to deploy a completed and tested project to multiple production servers in a Network Load Balancing cluster, or to a staging server and a production server.</span></span>  
  
 <span data-ttu-id="0e81b-110">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트를 다른 데이터베이스나 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 배포할 경우 다음 절차에 설명된 방법 중 하나를 사용하여 입력 파일에 있는 설치 대상을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e81b-110">To deploy an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project to a different database or [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, you can change the installation target in the input file by using one of the methods described in the following procedure.</span></span>  
  
#### <a name="to-change-the-installation-target-after-the-input-files-have-been-generated"></a><span data-ttu-id="0e81b-111">입력 파일을 생성한 다음 설치 대상을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="0e81b-111">To change the installation target after the input files have been generated</span></span>  
  
-   <span data-ttu-id="0e81b-112">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 배포 마법사를 대화형으로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0e81b-112">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard interactively.</span></span> <span data-ttu-id="0e81b-113">**설치 대상** 페이지에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스 및 데이터베이스에 대한 새 대상을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0e81b-113">On the **Installation Target** page, specify a new destination for the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and database.</span></span>  
  
     <span data-ttu-id="0e81b-114">또는</span><span class="sxs-lookup"><span data-stu-id="0e81b-114">-or-</span></span>  
  
-   <span data-ttu-id="0e81b-115">명령 프롬프트에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 배포 마법사를 실행하여 응답 파일 모드에서 마법사를 실행하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0e81b-115">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard at the command prompt and set the wizard to run in answer file mode.</span></span> <span data-ttu-id="0e81b-116">응답 파일 모드에 대한 자세한 내용은 [Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0e81b-116">For more information about answer file mode, see [Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md).</span></span>  
  
     <span data-ttu-id="0e81b-117">또는</span><span class="sxs-lookup"><span data-stu-id="0e81b-117">-or-</span></span>  
  
-   <span data-ttu-id="0e81b-118">\<*project name*>텍스트 편집기를 사용 하 여 deploymenttargets 파일을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e81b-118">Modify the \<*project name*>.deploymenttargets file by using any text editor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e81b-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0e81b-119">See Also</span></span>  
 <span data-ttu-id="0e81b-120">[파티션 및 역할 배포 옵션 지정](deployment-script-files-partition-and-role-deployment-options.md) </span><span class="sxs-lookup"><span data-stu-id="0e81b-120">[Specifying Partition and Role Deployment Options](deployment-script-files-partition-and-role-deployment-options.md) </span></span>  
 <span data-ttu-id="0e81b-121">[솔루션 배포를 위한 구성 설정 지정](deployment-script-files-solution-deployment-config-settings.md) </span><span class="sxs-lookup"><span data-stu-id="0e81b-121">[Specifying Configuration Settings for Solution Deployment](deployment-script-files-solution-deployment-config-settings.md) </span></span>  
 [<span data-ttu-id="0e81b-122">처리 옵션 지정</span><span class="sxs-lookup"><span data-stu-id="0e81b-122">Specifying Processing Options</span></span>](deployment-script-files-specifying-processing-options.md)  
  
  
