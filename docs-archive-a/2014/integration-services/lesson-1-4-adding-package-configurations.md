---
title: '4단계: 패키지 구성 추가 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e04a5321-63d5-4ec5-85b9-cb4eaf6c87f6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 416cf17f967a145fccef1341b77f71a02ff3f3b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651129"
---
# <a name="step-4-adding-package-configurations"></a><span data-ttu-id="4dd15-102">4단계: 패키지 구성 추가</span><span class="sxs-lookup"><span data-stu-id="4dd15-102">Step 4: Adding Package Configurations</span></span>
  <span data-ttu-id="4dd15-103">이 태스크에서는 각 패키지에 구성을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-103">In this task, you will add a configuration to each package.</span></span> <span data-ttu-id="4dd15-104">구성은 런타임 시 패키지 속성 및 패키지 개체의 값을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-104">Configurations update the values of package properties and package objects at run time.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="4dd15-105">에서는 다양한 구성 유형이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-105">provides a variety of configuration types.</span></span> <span data-ttu-id="4dd15-106">구성을 환경 변수, 레지스트리 항목, 사용자 정의 변수, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 테이블 및 XML 파일에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-106">You can store configurations in environment variables, registry entries, user-defined variables, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tables, and XML files.</span></span> <span data-ttu-id="4dd15-107">보다 나은 유연성을 위해 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 는 간접 구성 사용을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-107">To provide additional flexibility, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] supports the use of indirect configurations.</span></span> <span data-ttu-id="4dd15-108">이는 실제 값을 지정하는 구성의 위치는 환경 변수를 사용하여 지정한다는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-108">This means that you use an environment variable to specify the location of the configuration, which in turn specifies the actual values.</span></span> <span data-ttu-id="4dd15-109">Deployment Tutorial 프로젝트의 패키지는 XML 구성 파일과 간접 구성의 조합을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-109">The packages in the Deployment Tutorial project use a combination of XML configuration files and indirect configurations.</span></span> <span data-ttu-id="4dd15-110">XML 구성 파일은 여러 속성에 대한 구성을 포함할 수 있으며 가능한 경우 여러 패키지에서 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-110">An XML configuration file can include configurations for multiple properties, and when appropriate, can be referenced by multiple packages.</span></span> <span data-ttu-id="4dd15-111">이 자습서에서는 각 패키지에 대한 별개의 구성 파일을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-111">In this tutorial, you will use a separate configuration file for each package.</span></span>  
  
 <span data-ttu-id="4dd15-112">구성 파일은 연결 문자열과 같은 중요한 정보를 포함하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-112">Configuration files frequently contain sensitive information such as connection strings.</span></span> <span data-ttu-id="4dd15-113">따라서 ACL(액세스 제어 목록)을 사용하여 파일을 저장하는 위치나 폴더에 대한 액세스를 제한하고 패키지 실행이 허용되는 사용자나 계정에만 액세스를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-113">Therefore, you should use an access control list (ACL) to restrict access to the location or folder where you store the files, and give access only to users or accounts that are permitted to run packages.</span></span> <span data-ttu-id="4dd15-114">자세한 내용은 [패키지에서 사용되는 파일 액세스](../../2014/integration-services/access-to-files-used-by-packages.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4dd15-114">For more information, see [Access to Files Used by Packages](../../2014/integration-services/access-to-files-used-by-packages.md).</span></span>  
  
 <span data-ttu-id="4dd15-115">이전 태스크에서 Deployment Tutorial 프로젝트에 추가했던 패키지(DataTransfer 및 LoadXMLData)는 구성을 구현해야 대상 서버에 배포된 후 성공적으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-115">The packages (DataTransfer and LoadXMLData) that you added to the Deployment Tutorial project in the previous task need configurations to run successfully after they are deployed to the target server.</span></span> <span data-ttu-id="4dd15-116">구성을 구현하려면 XML 구성 파일에 대한 간접 구성을 만든 다음 XML 구성 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-116">To implement configurations, you will first create the indirect configurations for the XML configuration files, and then you will create the XML configuration files.</span></span>  
  
 <span data-ttu-id="4dd15-117">구성 파일인 DataTransferConfig.dtsConfig 및 LoadXMLData.dtsConfig를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-117">You will create two configuration files, DataTransferConfig.dtsConfig and LoadXMLData.dtsConfig.</span></span> <span data-ttu-id="4dd15-118">이러한 파일은 패키지에 사용되는 데이터 및 로그 파일의 위치를 지정하는 패키지의 속성을 업데이트하는 이름-값 쌍을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-118">These files contain name-value pairs that update the properties in packages that specify the location of the data and log files used by the package.</span></span> <span data-ttu-id="4dd15-119">나중에 배포 프로세스의 한 단계에서 구성 파일의 값을 업데이트하여 대상 컴퓨터에 있는 파일의 새 위치를 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-119">Later, as a step in the deployment process, you will update the values in the configuration files to reflect the new location of the files on the destination computer.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="4dd15-120">는 DataTransferConfig.dtsConfig 및 LoadXMLData.dtsConfig가 DataTransfer 및 LoadXMLData 패키지의 종속 파일임을 인식하고 구성 파일을 자동으로 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-120">recognizes that the DataTransferConfig.dtsConfig and LoadXMLData.dtsConfig are dependencies of the DataTransfer and LoadXMLData packages, and automatically includes the configuration files when you create the deployment bundle in the next lesson.</span></span>  
  
### <a name="to-create-indirect-configuration-for-the-datatransfer-package"></a><span data-ttu-id="4dd15-121">DataTransfer 패키지에 대한 간접 구성을 만들려면</span><span class="sxs-lookup"><span data-stu-id="4dd15-121">To create indirect configuration for the DataTransfer package</span></span>  
  
1.  <span data-ttu-id="4dd15-122">솔루션 탐색기에서 DataTransfer.dtsx를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-122">In Solution Explorer, double-click DataTransfer.dtsx.</span></span>  
  
2.  <span data-ttu-id="4dd15-123">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 제어 흐름 디자인 화면의 배경을 아무 곳이나 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-123">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click anywhere in the background of the control flow design surface.</span></span>  
  
3.  <span data-ttu-id="4dd15-124">**SSIS** 메뉴에서 **패키지 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-124">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
4.  <span data-ttu-id="4dd15-125">**패키지 구성 도우미**대화 상자에서 아직 선택하지 않은 경우 **패키지 구성 설정** 을 선택하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-125">In the **Package Configuration Organize**r dialog box, select **Enable package configurations** if it is not already selected, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="4dd15-126">패키지 구성 마법사 시작 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-126">On the welcome page of the Package Configuration Wizard, click **Next**.</span></span>  
  
6.  <span data-ttu-id="4dd15-127">구성 유형 선택 페이지의 **구성 유형** 목록에서 **XML 구성 파일** 을 선택 하 고 **구성 위치가 환경 변수에 저장 됨** 옵션을 선택한 다음 `DataTransfer,` 목록에서 **DataTransfer** 환경 변수를 입력 하거나 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-127">On the Select Configuration Type page, select **XML configuration file** in the **Configuration type** list, select the **Configuration location is stored in an environment variable** option, and type `DataTransfer,` or select the **DataTransfer** environment variable in the list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4dd15-128">이 환경 변수를 목록에서 사용할 수 있게 하려면 변수를 추가한 후에 컴퓨터를 다시 시작해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-128">To make the environment variable available in the list, you may have to restart your computer after adding the variable.</span></span> <span data-ttu-id="4dd15-129">컴퓨터를 다시 시작하지 않으려면 환경 변수의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-129">If you do not want to restart the computer, you can type the name of the environment variable.</span></span>  
  
7.  <span data-ttu-id="4dd15-130">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-130">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="4dd15-131">마법사 완료 페이지에서 **구성 이름** 상자에 **DataTransfer EV Configuration** 을 입력하고 **미리 보기** 창에서 구성 내용을 검토한 다음 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-131">On the Completing the Wizard page, type **DataTransfer EV Configuration** in the **Configuration name** box, review the configuration contents in the **Preview** pane, and then click **Finish**.</span></span>  
  
9. <span data-ttu-id="4dd15-132">**패키지 구성 도우미**대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-132">Close the **Package Configuration Organize**r dialog box.</span></span>  
  
### <a name="to-create-the-xml-configuration-for-the-datatransfer-package"></a><span data-ttu-id="4dd15-133">DataTransfer 패키지에 대한 XML 구성을 만들려면</span><span class="sxs-lookup"><span data-stu-id="4dd15-133">To create the XML configuration for the DataTransfer package</span></span>  
  
1.  <span data-ttu-id="4dd15-134">솔루션 탐색기에서 DataTransfer.dtsx를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-134">In Solution Explorer, double-click DataTransfer.dtsx.</span></span>  
  
2.  <span data-ttu-id="4dd15-135">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 제어 흐름 디자인 화면의 배경을 아무 곳이나 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-135">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click anywhere in the background of the control flow design surface.</span></span>  
  
3.  <span data-ttu-id="4dd15-136">**SSIS** 메뉴에서 **패키지 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-136">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
4.  <span data-ttu-id="4dd15-137">패키지 구성 도우미 대화 상자에서 **패키지 구성 설정** 확인란을 선택하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-137">In the Package Configuration Organizer dialog box, select the **Enable Package Configurations** check-box, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="4dd15-138">패키지 구성 마법사 시작 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-138">On the welcome page of the Package Configuration Wizard, click **Next**.</span></span>  
  
6.  <span data-ttu-id="4dd15-139">구성 유형 선택 페이지의 **구성 유형** 목록에서 **XML 구성 파일** 을 선택한 다음 **찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-139">On the Select Configuration Type page, select **XML configuration file** in the **Configuration type** list and then click **Browse**.</span></span>  
  
7.  <span data-ttu-id="4dd15-140">**구성 파일 위치 선택** 대화 상자에서 C:\DeploymentTutorial로 이동한 다음 **파일 이름** 상자에 **DataTransferConfig** 를 입력하고 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-140">In **Select Configuration File Location** dialog box, navigate to C:\DeploymentTutorial and type **DataTransferConfig** in the **File name** box, and then click **Save**.</span></span>  
  
8.  <span data-ttu-id="4dd15-141">구성 유형 선택 페이지에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-141">On the Select Configuration Type page, click **Next**.</span></span>  
  
9. <span data-ttu-id="4dd15-142">내보낼 속성 선택 페이지에서 DataTransfer, 연결 관리자, Deployment Tutorial Log 및 Properties를 확장한 다음 **연결 문자열** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-142">On the Select Properties to Export page, expand DataTransfer, Connection Managers, Deployment Tutorial Log, and Properties, and then select the **Connection String** check-box.</span></span>  
  
10. <span data-ttu-id="4dd15-143">연결 관리자 내에서 NewCustomers를 확장한 다음 **연결 문자열** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-143">Within Connection Managers, expand NewCustomers, and then select the **Connection String** check-box.</span></span>  
  
11. <span data-ttu-id="4dd15-144">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-144">Click **Next**.</span></span>  
  
12. <span data-ttu-id="4dd15-145">마법사 완료 페이지에서 **구성 이름** 상자에 **DataTransfer Configuration** 을 입력하고 구성 내용을 검토한 다음 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-145">On the Completing the Wizard page, type **DataTransfer Configuration** in the **Configuration name** box, review the content of the configuration, and then click **Finish**.</span></span>  
  
13. <span data-ttu-id="4dd15-146">**패키지 구성 도우미** 대화 상자에서 DataTransfer EV Configuration이 먼저 나열된 다음 DataTransfer Configuration이 나열되는지 확인하고 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-146">In the **Package Configuration Organizer** dialog box, verify that DataTransfer EV Configuration is listed first, and DataTransfer Configuration is listed second, and then click **Close**.</span></span>  
  
### <a name="to-create-indirect-configuration-for-the-loadxmldata-package"></a><span data-ttu-id="4dd15-147">LoadXMLData 패키지에 대한 간접 구성을 만들려면</span><span class="sxs-lookup"><span data-stu-id="4dd15-147">To create indirect configuration for the LoadXMLData package</span></span>  
  
1.  <span data-ttu-id="4dd15-148">솔루션 탐색기에서 LoadXMLData.dtsx를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-148">In Solution Explorer, double-click LoadXMLData.dtsx.</span></span>  
  
2.  <span data-ttu-id="4dd15-149">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 제어 흐름 디자인 화면의 배경을 아무 곳이나 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-149">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click anywhere in the background of the control flow design surface.</span></span>  
  
3.  <span data-ttu-id="4dd15-150">**SSIS** 메뉴에서 **패키지 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-150">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
4.  <span data-ttu-id="4dd15-151">**패키지 구성 도우미**대화 상자에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-151">In the **Package Configuration Organize**r dialog box, Click **Add**.</span></span>  
  
5.  <span data-ttu-id="4dd15-152">패키지 구성 마법사 시작 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-152">On the welcome page of the Package Configuration Wizard, click **Next**.</span></span>  
  
6.  <span data-ttu-id="4dd15-153">구성 유형 선택 페이지의 **구성 유형** 목록에서 **XML 구성 파일** 을 선택 하 고 **구성 위치가 환경 변수에 저장 됨** 옵션을 선택한 다음 `LoadXMLData` `LoadXMLData` 목록에서 환경 변수를 입력 하거나 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-153">On the Select Configuration Type page, select **XML configuration file** in the **Configuration type** list, select the **Configuration location is stored in an environment variable** option, type `LoadXMLData` or select the `LoadXMLData` environment variable in the list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4dd15-154">이 환경 변수를 목록에서 사용할 수 있게 하려면 변수를 추가한 후에 컴퓨터를 다시 시작해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-154">To make the environment variable available in the list, you may have to restart your computer after adding the variable.</span></span>  
  
7.  <span data-ttu-id="4dd15-155">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-155">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="4dd15-156">마법사 완료 페이지에서 **구성 이름** 상자에 **LoadXMLData EV Configuration** 을 입력하고 구성 내용을 검토한 다음 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-156">On the Completing the Wizard page, type **LoadXMLData EV Configuration** in the **Configuration name** box, review the content of the configuration, and then click **Finish**.</span></span>  
  
### <a name="to-create-the-xml-configuration-for-the-loadxmldata-package"></a><span data-ttu-id="4dd15-157">LoadXMLData 패키지에 대한 XML 구성을 만들려면</span><span class="sxs-lookup"><span data-stu-id="4dd15-157">To create the XML configuration for the LoadXMLData package</span></span>  
  
1.  <span data-ttu-id="4dd15-158">솔루션 탐색기에서 LoadXMLData.dtsx를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-158">In Solution Explorer, double-click LoadXMLData.dtsx.</span></span>  
  
2.  <span data-ttu-id="4dd15-159">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 제어 흐름 디자인 화면의 배경을 아무 곳이나 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-159">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click anywhere in the background of the control flow design surface.</span></span>  
  
3.  <span data-ttu-id="4dd15-160">**SSIS** 메뉴에서 **패키지 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-160">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
4.  <span data-ttu-id="4dd15-161">패키지 구성 도우미 대화 상자에서 **패키지 구성 설정** 확인란을 선택하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-161">In the Package Configuration Organizer dialog box, select the **Enable Package Configurations** check-box, and click **Add**.</span></span>  
  
5.  <span data-ttu-id="4dd15-162">패키지 구성 마법사 시작 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-162">On the welcome page of the Package Configuration Wizard, click **Next**.</span></span>  
  
6.  <span data-ttu-id="4dd15-163">구성 유형 선택 페이지의 **구성 유형** 목록에서 **XML 구성 파일** 을 선택한 다음 **찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-163">On the Select Configuration Type page, select **XML configuration file** in the **Configuration type** list and click **Browse**.</span></span>  
  
7.  <span data-ttu-id="4dd15-164">**구성 파일 위치 선택** 대화 상자에서 C:\DeploymentTutorial로 이동한 다음 **파일 이름** 상자에 **LoadXMLDataConfig** 를 입력하고 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-164">In **Select Configuration File Location** dialog box, navigate to C:\DeploymentTutorial and type **LoadXMLDataConfig** in the **File name** box, and then click **Save**.</span></span>  
  
8.  <span data-ttu-id="4dd15-165">구성 유형 선택 페이지에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-165">On the Select Configuration Type page, click **Next**.</span></span>  
  
9. <span data-ttu-id="4dd15-166">내보낼 속성 선택 페이지에서 LoadXMLData, 실행 파일, Load XML Data 및 Properties를 확장한 다음 **[XMLSource].[XMLData]** 및 **[XMLSource].[XMLSchemaDefinition]** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-166">On the Select Properties to Export page, expand LoadXMLData, Executables, Load XML Data, and Properties, and then select the **[XMLSource].[XMLData]** and **[XMLSource].[XMLSchemaDefinition]** check boxes.</span></span>  
  
10. <span data-ttu-id="4dd15-167">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-167">Click **Next**.</span></span>  
  
11. <span data-ttu-id="4dd15-168">마법사 완료 페이지에서 **구성 이름** 상자에 **LoadXMLData Configuration** 을 입력하고 구성 내용을 검토한 다음 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-168">On the Completing the Wizard page, type **LoadXMLData Configuration** in the **Configuration name** box, review the content of the configuration, and then click **Finish**.</span></span>  
  
12. <span data-ttu-id="4dd15-169">**패키지 구성 도우미** 대화 상자에서 LoadXMLData EV Configuration이 먼저 나열된 다음 LoadXMLData Configuration이 나열되는지 확인하고 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dd15-169">In the **Package Configuration Organizer** dialog box, verify that the LoadXMLData EV Configuration is listed first, and the LoadXMLData Configuration is listed second, and then click **Close**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="4dd15-170">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="4dd15-170">Next Task in Lesson</span></span>  
 [<span data-ttu-id="4dd15-171">5단계: 업데이트된 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="4dd15-171">Step 5: Testing the Updated Packages</span></span>](../integration-services/lesson-1-5-testing-the-updated-packages.md)  
  
<span data-ttu-id="4dd15-172">![Integration Services 아이콘 (작은 아이콘)](media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="4dd15-172">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="4dd15-173">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="4dd15-173">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="4dd15-174">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="4dd15-174">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="4dd15-175">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="4dd15-175">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dd15-176">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4dd15-176">See Also</span></span>  
 <span data-ttu-id="4dd15-177">[패키지 구성](../../2014/integration-services/package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="4dd15-177">[Package Configurations](../../2014/integration-services/package-configurations.md) </span></span>  
 <span data-ttu-id="4dd15-178">[패키지 구성 만들기](../../2014/integration-services/create-package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="4dd15-178">[Create Package Configurations](../../2014/integration-services/create-package-configurations.md) </span></span>  
 [<span data-ttu-id="4dd15-179">패키지에서 사용되는 파일 액세스</span><span class="sxs-lookup"><span data-stu-id="4dd15-179">Access to Files Used by Packages</span></span>](../../2014/integration-services/access-to-files-used-by-packages.md)  
  
  
