---
title: '3단계: 배포된 패키지 테스트 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9159da3f-c9ca-4015-9e85-3bf4373a1349
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d11ae071d97d9fdadec6ee144813c91519b54ea4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650179"
---
# <a name="step-3-testing-the-deployed-packages"></a><span data-ttu-id="9c38c-102">3단계: 배포된 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="9c38c-102">Step 3: Testing the Deployed Packages</span></span>
  <span data-ttu-id="9c38c-103">이 태스크에서는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스에 배포한 패키지를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-103">In this task, you will test the packages that you deployed to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>

 <span data-ttu-id="9c38c-104">다른 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 자습서에서는 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]디버그 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]메뉴의 **디버깅 시작** 옵션을 사용하여 **용 개발 환경인** 에서 패키지를 실행했습니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-104">In other [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] tutorials, you ran packages in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the development environment for [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], using the **Start Debugging** option on the **Debug** menu.</span></span> <span data-ttu-id="9c38c-105">여기에서는 패키지를 다르게 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-105">This time you will run the packages differently.</span></span>

 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]<span data-ttu-id="9c38c-106">는 테스트 및 프로덕션 환경에서 패키지를 실행하는 데 사용할 수 있는 명령 프롬프트 유틸리티 `dtexec` 및 패키지 실행 유틸리티와 같은 여러 도구를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-106">provides several tools that you can use to run packages in the test and production environment: the command prompt utility `dtexec` and the Execute Package Utility.</span></span> <span data-ttu-id="9c38c-107">패키지 실행 유틸리티는 `dtexec`에서 작성된 그래픽 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-107">The Execute Package Utility is a graphical tool that is built on `dtexec`.</span></span> <span data-ttu-id="9c38c-108">이러한 두 도구는 모두 패키지를 즉시 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-108">Both of these tools execute the package immediately.</span></span> <span data-ttu-id="9c38c-109">또한 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 는 SQL Server 에이전트 작업의 한 단계로 패키지 실행을 예약하기 위해 특별하게 디자인된 SQL Server 에이전트의 하위 시스템을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-109">In addition, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provides a subsystem of SQL Server Agent that is especially designed for scheduling package execution as a step in a SQL Server Agent job.</span></span>

 <span data-ttu-id="9c38c-110">패키지 실행 유틸리티를 사용하여 배포된 패키지를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-110">You will use the Execute Package Utility to run the deployed packages.</span></span> <span data-ttu-id="9c38c-111">패키지는 있는 그대로 사용됩니다. 따라서 대화 상자의 어떠한 페이지에서도 정보를 업데이트할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-111">The packages will be used as is; therefore, you do not have to update information on any pages in the dialog box.</span></span> <span data-ttu-id="9c38c-112">패키지 실행 유틸리티의 첫 번째 페이지인 일반 페이지에서 패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-112">You will run the packages from the General page, which is the first page in the Execute Package Utility.</span></span> <span data-ttu-id="9c38c-113">필요할 경우 다른 페이지를 클릭하여 각 패키지에 대해 포함된 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-113">If you like, you can click the other pages too see the information that they contain for each package.</span></span>

> [!NOTE]
>  <span data-ttu-id="9c38c-114">이 자습서의 컨텍스트에서 패키지가 성공적으로 실행되도록 하려면 어떠한 옵션도 수정해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-114">To ensure that the packages run successfully in the context of this tutorial, you should not modify any options.</span></span>

 <span data-ttu-id="9c38c-115">패키지 실행 유틸리티를 사용하여 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 에서 패키지를 실행하기 전에 Integration Services 서비스가 실행 중인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-115">Before you run packages in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] by using the Execute Package Utility, ensure that the Integration Services service is running.</span></span> <span data-ttu-id="9c38c-116">Integration Services 서비스는 패키지 스토리지 및 실행을 위한 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-116">The Integration Services service provides support for package storage and execution.</span></span> <span data-ttu-id="9c38c-117">이 서비스가 중지된 경우 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에 연결할 수 없으며 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 는 실행할 패키지를 나열하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-117">If the service is stopped, you cannot connect to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] does not list the packages to run.</span></span> <span data-ttu-id="9c38c-118">또한 패키지가 배포된 인스턴스에서 패키지를 실행할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-118">You also must have permissions to run the package on the instance where the package has been deployed.</span></span> <span data-ttu-id="9c38c-119">자세한 내용은 [Integration Services 경로&#40;SSIS Service&#41;](security/integration-services-roles-ssis-service.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9c38c-119">For more information, see [Integration Services Roles &#40;SSIS Service&#41;](security/integration-services-roles-ssis-service.md).</span></span>

 <span data-ttu-id="9c38c-120">저장된 패키지 폴더 내의 최상위 폴더는 Integration Services 서비스가 모니터링하는 사용자 정의 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-120">The top-level folders within the Stored Packages folder are the user-defined folders that Integration Services service monitors.</span></span> <span data-ttu-id="9c38c-121">MsDtsSrvr.ini.xml 파일에서 많거나 적은 폴더를 원하는 대로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-121">You can specify as many or few folders in the MsDtsSrvr.ini.xml file as you want.</span></span> <span data-ttu-id="9c38c-122">이 자습서에서는 기본 MsDtsSrvr.ini.xml 파일이 사용되고 있으며 저장된 패키지 내 최상위 폴더의 이름이 File System 및 MSDB라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-122">This tutorial assumes that you are using the default MsDtsSrvr.ini.xml file, and that the names of the top-level folders within Stored Packages are File System and MSDB.</span></span>

### <a name="to-connect-to-integration-services-in-sql-server-management-studio"></a><span data-ttu-id="9c38c-123">SQL Server Management Studio에서 Integration Services에 연결하려면</span><span class="sxs-lookup"><span data-stu-id="9c38c-123">To connect to Integration Services in SQL Server Management Studio</span></span>

1.  <span data-ttu-id="9c38c-124">**시작**을 클릭하고 **모든 프로그램**, **Microsoft SQL Server**를 차례로 가리킨 다음 **SQL Server Management Studio**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-124">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Management Studio**.</span></span>

2.  <span data-ttu-id="9c38c-125">**서버에 연결** 대화 상자의 **서버 유형** 목록에서 **Integration Services** 를 선택하고 **서버 이름** 상자에 서버 이름을 입력한 다음 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-125">In the **Connect to Server** dialog box, select **Integration Services** in the **Server type** list, provide a server name in the **Server name** box, and click **Connect**.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="9c38c-126">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]에 연결할 수 없으면 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스가 실행되고 있지 않는 것일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-126">If you cannot connect to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is likely not running.</span></span> <span data-ttu-id="9c38c-127">이 서비스의 상태를 확인하려면 **시작**을 클릭하고 **모든 프로그램**, **Microsoft SQL Server**, **구성 도구**를 차례로 가리킨 다음 **SQL Server 구성 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-127">To learn the status of the service, click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span> <span data-ttu-id="9c38c-128">왼쪽 창에서 **SQL Server 서비스**를 클릭하고</span><span class="sxs-lookup"><span data-stu-id="9c38c-128">In the left pane, click **SQL Server Services**.</span></span> <span data-ttu-id="9c38c-129">오른쪽 창에서 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-129">In the right pane, find the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="9c38c-130">서비스가 실행되지 않았으면 서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-130">Start the service if it is not already running.</span></span>

     [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="9c38c-131">가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-131">opens.</span></span> <span data-ttu-id="9c38c-132">기본적으로 개체 탐색기 창이 열리고 Studio의 오른쪽 상단 모서리에 위치합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-132">By default the Object Explorer window is open and placed in the upper right corner of the studio.</span></span> <span data-ttu-id="9c38c-133">개체 탐색기가 열려 있지 않으면 **보기** 메뉴에서 **개체 탐색기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-133">If Object Explorer is not open, click **Object Explorer** on the **View** menu.</span></span>

### <a name="to-run-the-packages-using-the-execute-package-utility"></a><span data-ttu-id="9c38c-134">패키지 실행 유틸리티를 사용하여 패키지를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="9c38c-134">To run the packages using the Execute Package Utility</span></span>

1.  <span data-ttu-id="9c38c-135">개체 탐색기에서 저장된 패키지 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-135">In Object Explorer, expand the Stored Packages folder.</span></span>

2.  <span data-ttu-id="9c38c-136">MSDB 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-136">Expand the MSDB folder.</span></span> <span data-ttu-id="9c38c-137">패키지를 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에 배포했으므로 배포된 모든 패키지는 msdb [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스에 저장되고 MSDB 폴더에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-137">Because you deployed the packages to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], all the deployed packages are stored in the msdb [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database, and all deployed packages appear in the MSDB folder.</span></span> <span data-ttu-id="9c38c-138">패키지를 Deployment Tutorial 외부의 파일 시스템에 배포하지 않은 경우 File System 폴더는 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-138">The File System folder is empty, unless you have deployed packages to the file system outside of the Deployment Tutorial.</span></span>

3.  <span data-ttu-id="9c38c-139">패키지 목록의 맨 위에서 시작하여 DataTransfer를 마우스 오른쪽 단추로 클릭하고 **패키지 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-139">Starting at the top of the package list, right-click DataTransfer, and click **Run Package**.</span></span>

4.  <span data-ttu-id="9c38c-140">**패키지 실행 유틸리티** 대화 상자에서 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-140">In the **Execute Package Utility** dialog box, click **Execute**.</span></span>

5.  <span data-ttu-id="9c38c-141">**패키지 실행 유틸리티** 대화 상자에서 패키지의 진행률과 실행 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-141">In the **Execute Package Utility** dialog box, view the progress and execution results of the package.</span></span> <span data-ttu-id="9c38c-142">**중지** 단추를 사용할 수 없게 되어 패키지가 완료되었다고 표시되면 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-142">When the **Stop** button becomes unavailable, which indicates that the package has completed, click **Close**.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="9c38c-143">패키지가 실행되는 동안 **중지** 를 클릭할 경우 패키지가 완료되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-143">If you click **Stop** while the package is running, the package will not finish.</span></span>

6.  <span data-ttu-id="9c38c-144">**패키지 실행 유틸리티** 대화 상자에서 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-144">In the **Execute Package Utility** dialog box, click **Close**.</span></span>

7.  <span data-ttu-id="9c38c-145">LoadXML 패키지에 대해 3 - 6단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-145">Repeat steps 3 - 6 for the LoadXML package.</span></span>

8.  <span data-ttu-id="9c38c-146">**파일** 메뉴에서 **끝내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-146">On the **File** menu, click **Exit**.</span></span>

### <a name="to-verify-the-results-of-the-datatransfer-package"></a><span data-ttu-id="9c38c-147">DataTransfer 패키지의 결과를 확인하려면</span><span class="sxs-lookup"><span data-stu-id="9c38c-147">To verify the results of the DataTransfer package</span></span>

1.  <span data-ttu-id="9c38c-148">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]의 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-148">On the toolbar in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], click **New Query**.</span></span>

2.  <span data-ttu-id="9c38c-149">**서버에 연결** 대화 상자의 **서버 유형** 목록에서 **데이터베이스 엔진** 을 선택하고 **서버 이름** 상자에 자습서 패키지를 설치한 서버의 이름을 제공하거나 (local)을 입력하고 인증 모드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-149">In the **Connect to Server** dialog box, select **Database Engine** in the **Server type** list, provide the name of the server name on which you installed the tutorial packages or type (local) in the **Server name** box, and select an authentication mode.</span></span> <span data-ttu-id="9c38c-150">SQL Server 인증을 사용하는 경우 사용자 이름과 암호를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-150">If using SQL Server Authentication, provide a user name and password.</span></span>

3.  <span data-ttu-id="9c38c-151">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-151">Click **Connect**.</span></span>

4.  <span data-ttu-id="9c38c-152">쿼리 창에서 다음 SQL 문을 입력하거나 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-152">In the query window, type or paste the following SQL statement:</span></span>

     `USE AdventureWorks`

     `SELECT * FROM HighIncomeCustomers`

5.  <span data-ttu-id="9c38c-153">**F5** 키를 누르거나 도구 모음에서 실행 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-153">Press **F5** or click the Execute icon on the toolbar.</span></span>

     <span data-ttu-id="9c38c-154">쿼리는 31개의 데이터 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-154">The query returns 31 rows of data.</span></span> <span data-ttu-id="9c38c-155">반환 결과에는 YearlyIncome 열의 100000보다 큰 값을 가지는 Customers.txt 텍스트 파일의 모든 행이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-155">The return result contains any rows from the text file, Customers.txt, that have values larger than 100000 in the YearlyIncome column.</span></span>

6.  <span data-ttu-id="9c38c-156">DeploymentTutorial 폴더를 찾아서 로그 XML 파일인 Deployment Tutorial Log를 마우스 오른쪽 단추로 클릭한 다음 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-156">Locate the DeploymentTutorial folder, right-click the log XML file, Deployment Tutorial Log, and then click **Open**.</span></span> <span data-ttu-id="9c38c-157">메모장이나 원하는 텍스트/XML 편집기를 사용하여 파일을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-157">You can open the file by using Notepad or the text/XML editor of choice.</span></span>

### <a name="to-verify-the-results-of-the-loadxmldata-package"></a><span data-ttu-id="9c38c-158">LoadXMLData 패키지의 결과를 확인하려면</span><span class="sxs-lookup"><span data-stu-id="9c38c-158">To verify the results of the LoadXMLData package</span></span>

1.  <span data-ttu-id="9c38c-159">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]의 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-159">On the toolbar in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], click **New Query**.</span></span>

2.  <span data-ttu-id="9c38c-160">연결하라는 메시지가 다시 표시되면 **서버에 연결** 대화 상자의 **서버 유형** 목록에서 **데이터베이스 엔진** 을 선택하고 **서버 이름** 상자에 자습서 패키지를 설치한 서버의 이름을 제공하거나 (local)을 입력하고 인증 모드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-160">If prompted to connect again, in the **Connect to Server** dialog box, select **Database Engine** in the **Server type** list, provide the name of the server on which you installed the tutorial packages or enter (local) in the **Server name** box, and select an authentication mode.</span></span> <span data-ttu-id="9c38c-161">SQL Server 인증을 사용하는 경우 사용자 이름과 암호를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-161">If using SQL Server Authentication, provide a user name and password.</span></span>

3.  <span data-ttu-id="9c38c-162">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-162">Click **Connect**.</span></span>

4.  <span data-ttu-id="9c38c-163">쿼리 창에서 다음 SQL 문을 입력하거나 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-163">In the query window, type or paste the following SQL statement:</span></span>

     `USE AdventureWorks`

     `SELECT * FROM OrderDatesByCountryRegion`

5.  <span data-ttu-id="9c38c-164">**F5** 키를 누르거나 도구 모음에서 실행 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-164">Press **F5** or click the Execute icon on the toolbar.</span></span>

     <span data-ttu-id="9c38c-165">쿼리는 21개의 데이터 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-165">The query returns 21 rows of data.</span></span> <span data-ttu-id="9c38c-166">반환 결과는 XML 데이터 파일 orders.xml의 행으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-166">The return result consists of the rows from the XML data file, orders.xml.</span></span> <span data-ttu-id="9c38c-167">각 행은 국가/지역별 요약이며 각 행에는 국가/지역의 이름, 각 국가/지역의 주문 수, 최신 주문과 가장 오래된 주문의 날짜가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c38c-167">Each row is a summary by country/region; the row lists the name of a country/region, the number of orders for each country/region and the dates of the newest and oldest orders.</span></span>

<span data-ttu-id="9c38c-168">![Integration Services 아이콘 (작은 아이콘)](media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="9c38c-168">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="9c38c-169">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="9c38c-169">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="9c38c-170">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="9c38c-170">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="9c38c-171">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="9c38c-171">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c38c-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9c38c-172">See Also</span></span>
 [<span data-ttu-id="9c38c-173">dtexec 유틸리티</span><span class="sxs-lookup"><span data-stu-id="9c38c-173">dtexec Utility</span></span>](packages/dtexec-utility.md)


