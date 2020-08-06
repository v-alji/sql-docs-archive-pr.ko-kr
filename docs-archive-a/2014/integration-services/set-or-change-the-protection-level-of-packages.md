---
title: 패키지의 보호 수준을 설정 하거나 변경 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- passwords [Integration Services]
- packages [Integration Services],security
- security [Integration Services],protection levels
- protection level for packages [Integration Services]
ms.assetid: 904a5580-82ba-4a26-b0c5-d1c989975f61
author: chugugrace
ms.author: chugu
ms.openlocfilehash: da8e63028498097b4321e4ef1383fbc8aa5845b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741127"
---
# <a name="set-or-change-the-protection-level-of-packages"></a><span data-ttu-id="86432-102">패키지 보호 수준 설정 또는 변경</span><span class="sxs-lookup"><span data-stu-id="86432-102">Set or Change the Protection Level of Packages</span></span>
  <span data-ttu-id="86432-103">패키지 내용과 패키지에 포함된 중요한 값(예: 암호)에 대한 액세스를 제어하려면 `ProtectionLevel` 속성의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="86432-103">To control access to the contents of packages and to the sensitive values that they contain, such as passwords, set the value of the `ProtectionLevel` property.</span></span> <span data-ttu-id="86432-104">프로젝트에 포함된 패키지는 프로젝트 생성을 위해 프로젝트와 보호 수준이 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86432-104">The packages contained in a project need to have the same protection level as the project, to build the project.</span></span> <span data-ttu-id="86432-105">프로젝트에서 `ProtectionLevel` 속성을 변경한 경우 패키지에 대한 프록시 설정을 수동으로 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86432-105">If you change the `ProtectionLevel` property setting on the project, you need to manually update the property setting for the packages.</span></span>  
  
 <span data-ttu-id="86432-106">`ProtectionLevel`패키지 수명 주기의 여러 단계에서 패키지에 적합 한 설정을 확인 하는 방법에 대 한 자세한 내용은 [패키지의 중요 한 데이터에 대 한 Access Control](security/access-control-for-sensitive-data-in-packages.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="86432-106">For information about how to determine the `ProtectionLevel` settings that are appropriate for your packages at different stages in the package life cycle, see [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md).</span></span> <span data-ttu-id="86432-107">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]의 보안 기능에 대한 개요는 [보안 개요&#40;Integration Services&#41;](security/security-overview-integration-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="86432-107">For an overview of security features in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], see [Security Overview &#40;Integration Services&#41;](security/security-overview-integration-services.md).</span></span>  
  
 <span data-ttu-id="86432-108">이 항목의 절차에서는 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 또는 dtutil 명령 프롬프트 유틸리티를 사용하여 `ProtectionLevel` 속성을 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="86432-108">The procedures in this topic describe how to use either [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] or the dtutil command prompt utility to change the `ProtectionLevel` property.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="86432-109">이 항목의 절차 외에도 일반적으로 패키지를 가져오거나 내보낼 때 패키지의 `ProtectionLevel` 속성을 설정하거나 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86432-109">In addition to the procedures in this topic, you can typically set or change the `ProtectionLevel` property of a package when you import or export the package.</span></span> <span data-ttu-id="86432-110">또한 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사를 사용하여 패키지를 저장할 때도 패키지의 `ProtectionLevel` 속성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86432-110">You can also change the `ProtectionLevel` property of a package when you use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard to save a package.</span></span>  
  
### <a name="to-set-or-change-the-protection-level-of-a-package-in-sql-server-data-tools"></a><span data-ttu-id="86432-111">SQL Server Data Tools에서 패키지 보호 수준을 설정하거나 변경하려면</span><span class="sxs-lookup"><span data-stu-id="86432-111">To set or change the protection level of a package in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="86432-112">항목의 속성에 사용할 수 있는 값을 검토 하 `ProtectionLevel` 고 패키지 [의 보호 수준을 설정](security/access-control-for-sensitive-data-in-packages.md)하 고 패키지에 대 한 적절 한 값을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="86432-112">Review the available values for the `ProtectionLevel` property in the topic, [Setting the Protection Level of Packages](security/access-control-for-sensitive-data-in-packages.md), and determine the appropriate value for your package.</span></span>  
  
2.  <span data-ttu-id="86432-113">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="86432-113">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package.</span></span>  
  
3.  <span data-ttu-id="86432-114">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="86432-114">Open the package in the [!INCLUDE[ssIS](../includes/ssis-md.md)] designer.</span></span>  
  
4.  <span data-ttu-id="86432-115">속성 창에 패키지 속성이 표시되지 않으면 디자인 화면을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="86432-115">If the Properties window does not show the properties of the package, click the design surface.</span></span>  
  
5.  <span data-ttu-id="86432-116">속성 창의 **보안** 그룹에서 속성에 대 한 적절 한 값을 선택 `ProtectionLevel` 합니다.</span><span class="sxs-lookup"><span data-stu-id="86432-116">In the Properties window, in the **Security** group, select the appropriate value for the `ProtectionLevel` property.</span></span>  
  
     <span data-ttu-id="86432-117">암호가 필요한 보호 수준을 선택한 경우 암호를 **PackagePassword** 속성의 값으로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="86432-117">If you select a protection level that requires a password, enter the password as the value of the **PackagePassword** property.</span></span>  
  
6.  <span data-ttu-id="86432-118">**파일** 메뉴에서 **선택한 항목 저장** 을 선택하여 수정한 패키지를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="86432-118">On the **File** menu, select **Save Selected Items** to save the modified package.</span></span>  
  
### <a name="to-set-or-change-the-protection-level-of-packages-at-the-command-prompt"></a><span data-ttu-id="86432-119">명령 프롬프트에서 패키지 보호 수준을 설정하거나 변경하려면</span><span class="sxs-lookup"><span data-stu-id="86432-119">To set or change the protection level of packages at the command prompt</span></span>  
  
1.  <span data-ttu-id="86432-120">항목의 속성에 사용할 수 있는 값을 검토 하 `ProtectionLevel` 고 패키지 [의 보호 수준을 설정](security/access-control-for-sensitive-data-in-packages.md)하 고 패키지에 대 한 적절 한 값을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="86432-120">Review the available values for the `ProtectionLevel` property in the topic, [Setting the Protection Level of Packages](security/access-control-for-sensitive-data-in-packages.md), and determine the appropriate value for your package.</span></span>  
  
2.  <span data-ttu-id="86432-121">`Encrypt` [Dtutil 유틸리티](dtutil-utility.md)항목에서 옵션에 대 한 매핑을 검토 하 고 선택한 속성의 값으로 사용할 적절 한 정수를 결정 합니다 `ProtectionLevel` .</span><span class="sxs-lookup"><span data-stu-id="86432-121">Review the mappings for the `Encrypt` option in the topic, [dtutil Utility](dtutil-utility.md), and determine the appropriate integer to use as the value of the selected `ProtectionLevel` property.</span></span>  
  
3.  <span data-ttu-id="86432-122">명령 프롬프트 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="86432-122">Open a Command Prompt window.</span></span>  
  
4.  <span data-ttu-id="86432-123">명령 프롬프트에서 `ProtectionLevel` 속성을 설정할 패키지가 들어 있는 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="86432-123">At the command prompt, navigate to the folder that contains the package or packages for which you want to set the `ProtectionLevel` property.</span></span>  
  
     <span data-ttu-id="86432-124">다음 단계에 나오는 구문 예에서는 이 폴더가 현재 폴더라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="86432-124">The syntax examples shown in the following step assume that this folder is the current folder.</span></span>  
  
5.  <span data-ttu-id="86432-125">다음 예 중 하나와 비슷한 명령을 사용하여 패키지 보호 수준을 설정하거나 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="86432-125">Set or change the protection level of the package or packages by using a command similar to the one of the following examples:</span></span>  
  
    -   <span data-ttu-id="86432-126">다음 명령은 파일 시스템에 있는 개별 패키지의 `ProtectionLevel` 속성을 수준 2, "암호로 중요한 데이터 암호화"로 설정하고 암호로 "strongpassword"를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="86432-126">The following command sets the `ProtectionLevel` property of an individual package in the file system to level 2, "Encrypt sensitive with password", with the password, "strongpassword":</span></span>  
  
         `dtutil.exe /file "C:\Package.dtsx" /encrypt file;"C:\Package.dtsx";2;strongpassword`  
  
    -   <span data-ttu-id="86432-127">다음 명령은 파일 시스템의 특정 폴더에 있는 모든 패키지의 `ProtectionLevel` 속성을 수준 2, "암호로 중요한 데이터 암호화"로 설정하고 암호로 "strongpassword"를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="86432-127">The following command sets the `ProtectionLevel` property of all packages in a particular folder in the file system to level 2, "Encrypt sensitive with password", with the password, "strongpassword":</span></span>  
  
         `for %f in (*.dtsx) do dtutil.exe /file %f /encrypt file;%f;2;strongpassword`  
  
         <span data-ttu-id="86432-128">배치 파일에서 비슷한 명령을 사용할 경우 배치 파일에 파일 자리 표시자로 "%f" 대신 "%%f"를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="86432-128">If you use a similar command in a batch file, enter the file placeholder, "%f", as "%%f" in the batch file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86432-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="86432-129">See Also</span></span>  
 [<span data-ttu-id="86432-130">dtutil 유틸리티</span><span class="sxs-lookup"><span data-stu-id="86432-130">dtutil Utility</span></span>](dtutil-utility.md)  
  
  
