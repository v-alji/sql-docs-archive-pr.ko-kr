---
title: '3단계: 패키지 및 기타 파일 추가 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a7e6ec9c-d31d-4613-9525-8947a7b358f7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d5ddcb6315576558161119a8774bccbd63fa5844
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651138"
---
# <a name="step-3-adding-packages-and-other-files"></a><span data-ttu-id="cb3e0-102">3단계: 패키지 및 기타 파일 추가</span><span class="sxs-lookup"><span data-stu-id="cb3e0-102">Step 3: Adding Packages and Other Files</span></span>
  <span data-ttu-id="cb3e0-103">이 태스크에서는 기존 패키지, 개별 패키지를 지원하는 보조 파일 및 추가 정보를 이전 태스크에서 만든 Deployment Tutorial 프로젝트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-103">In this task, you will add existing packages, ancillary files that support individual packages, and a Readme to the Deployment Tutorial project that you created in the previous task.</span></span> <span data-ttu-id="cb3e0-104">예를 들어 패키지에 대한 데이터가 포함된 XML 데이터 파일과 프로젝트의 모든 패키지에 대한 추가 정보를 제공하는 텍스트 파일을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-104">For example, you will add an XML data file that contains the data for a package and a text file that provides Readme information about all the packages in the project.</span></span>  
  
 <span data-ttu-id="cb3e0-105">패키지를 테스트 또는 프로덕션 환경에 배포할 경우 일반적으로 데이터 파일을 배포에 포함하는 대신에 데이터 파일 또는 데이터베이스의 테스트 또는 프로덕션 버전에 액세스하도록 구성을 사용하여 데이터 원본의 경로를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-105">When you deploy packages to a test or production environment, you typically do not include the data files in the deployment, but instead use configurations to update the paths of the data sources to access test or production versions of the data files or databases.</span></span> <span data-ttu-id="cb3e0-106">지침을 제공하기 위해 이 자습서에는 패키지 배포에 데이터 파일이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-106">For instructional purposes, this tutorial includes data files in the package deployment.</span></span>  
  
 <span data-ttu-id="cb3e0-107">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 예제를 설치하면 패키지 및 패키지가 사용하는 예제 데이터가 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-107">The packages and the sample data that the packages use are installed when you install the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] samples.</span></span> <span data-ttu-id="cb3e0-108">다음 패키지를 Deployment Tutorial 프로젝트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-108">You will add the following packages to the Deployment Tutorial project:</span></span>  
  
-   <span data-ttu-id="cb3e0-109">**DataTransfer.**</span><span class="sxs-lookup"><span data-stu-id="cb3e0-109">**DataTransfer.**</span></span> <span data-ttu-id="cb3e0-110">플랫 파일에서 데이터를 추출하고 데이터 세트의 행을 조건부로 유지하기 위해 열 값을 평가하며 AdventureWorks 데이터베이스의 테이블에 데이터를 로드하는 기본 패키지입니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-110">Basic package that extracts data from a flat file, evaluates column values to conditionally keep rows in the dataset, and loads data into a table in the AdventureWorks database.</span></span>  
  
-   <span data-ttu-id="cb3e0-111">**LoadXMLData.**</span><span class="sxs-lookup"><span data-stu-id="cb3e0-111">**LoadXMLData.**</span></span> <span data-ttu-id="cb3e0-112">XML 데이터 파일에서 데이터를 추출하고 열 값을 평가 및 집계하며 AdventureWorks 데이터베이스의 테이블에 데이터를 로드하는 데이터 전송 패키지입니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-112">Data-transfer package that extracts data from an XML data file, evaluates and aggregates column values, and loads data into a table in the AdventureWorks database.</span></span>  
  
 <span data-ttu-id="cb3e0-113">이러한 패키지의 배포를 지원하기 위해 다음 보조 파일을 Deployment Tutorial 프로젝트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-113">To support the deployment of these packages, you will add the following ancillary files to the Deployment Tutorial project.</span></span>  
  
|<span data-ttu-id="cb3e0-114">패키지</span><span class="sxs-lookup"><span data-stu-id="cb3e0-114">Package</span></span>|<span data-ttu-id="cb3e0-115">파일</span><span class="sxs-lookup"><span data-stu-id="cb3e0-115">File</span></span>|  
|-------------|----------|  
|<span data-ttu-id="cb3e0-116">DataTransfer</span><span class="sxs-lookup"><span data-stu-id="cb3e0-116">DataTransfer</span></span>|<span data-ttu-id="cb3e0-117">NewCustomers.txt</span><span class="sxs-lookup"><span data-stu-id="cb3e0-117">NewCustomers.txt</span></span>|  
|<span data-ttu-id="cb3e0-118">LoadXMLData</span><span class="sxs-lookup"><span data-stu-id="cb3e0-118">LoadXMLData</span></span>|<span data-ttu-id="cb3e0-119">orders.xml 및 orders.xsd</span><span class="sxs-lookup"><span data-stu-id="cb3e0-119">orders.xml and orders.xsd</span></span>|  
  
 <span data-ttu-id="cb3e0-120">또한 Deployment Tutorial 프로젝트에 대한 정보를 제공하는 텍스트 파일인 추가 정보 파일을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-120">You will also add a Readme, which is a text file that provides information about the Deployment Tutorial project.</span></span>  
  
 <span data-ttu-id="cb3e0-121">다음 절차에 사용되는 경로에서는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 예제가 기본 위치인 [!INCLUDE[ssSampPathIS](../includes/sssamppathis-md.md)]에 설치되었다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-121">The paths used in the following procedures assume that the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] samples were installed in the default location, [!INCLUDE[ssSampPathIS](../includes/sssamppathis-md.md)].</span></span> <span data-ttu-id="cb3e0-122">예제를 다른 위치에 설치한 경우 절차에서 해당 위치를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-122">If you installed the samples to a different location, you should use that location instead in the procedures.</span></span>  
  
 <span data-ttu-id="cb3e0-123">다음 태스크에서는 DataTransfer 및 LoadXMLData 패키지에 구성을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-123">In the next task, you will add configurations to the DataTransfer and LoadXMLData packages.</span></span> <span data-ttu-id="cb3e0-124">모든 구성은 XML 파일에 저장되며 시스템 환경 변수를 사용하여 파일의 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-124">All configurations are stored in XML files, and you will use a system environment variable to specify the location of the files.</span></span> <span data-ttu-id="cb3e0-125">구성 파일을 만든 후에 프로젝트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-125">After you create the configuration files, you will add them to the project.</span></span>  
  
### <a name="to-add-packages-to-the-deployment-tutorial-project"></a><span data-ttu-id="cb3e0-126">Deployment Tutorial 프로젝트에 패키지를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="cb3e0-126">To add packages to the Deployment Tutorial project</span></span>  
  
1.  <span data-ttu-id="cb3e0-127">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 를 아직 열지 않은 경우 **시작**을 클릭하고 **모든 프로그램**, **Microsoft SQL Server**를 차례로 가리킨 다음 **SQL Server Data Tools**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-127">If [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] is not already open, click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Data Tools**.</span></span>  
  
2.  <span data-ttu-id="cb3e0-128">**파일** 메뉴에서 **열기**, **프로젝트/솔루션**, **Deployment Tutorial** 폴더, **열기**를 차례로 클릭한 다음 **Deployment Tutorial.sln**을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-128">On the **File** menu, click **Open**, click **Project/Solution**, click the **Deployment Tutorial** folder and click **Open**, and then double-click **Deployment Tutorial.sln**.</span></span>  
  
3.  <span data-ttu-id="cb3e0-129">솔루션 탐색기에서 Deployment Tutorial을 마우스 오른쪽 단추로 클릭하고 **추가**를 클릭한 다음 **기존 패키지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-129">In Solution Explorer, right-click Deployment Tutorial, click **Add**, and then click **Existing Package**.</span></span>  
  
4.  <span data-ttu-id="cb3e0-130">**기존 패키지의 복사본 추가** 대화 상자의 **패키지 위치**에서 **파일 시스템**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-130">In the **Add Copy of Existing Package** dialog box, in **Package location**, select **File System**.</span></span>  
  
5.  <span data-ttu-id="cb3e0-131">찾아보기 단추 **(...)** 를 클릭하고 C:\Program Files\Microsoft SQL Server\100\Samples\Integration ServicesTutorial\Deploying Packages\Completed Packages로 이동하여 **DataTransfer.dtsx**를 선택한 다음, **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-131">Click the browse **(...)** button, navigate to C:\Program Files\Microsoft SQL Server\100\Samples\Integration ServicesTutorial\Deploying Packages\Completed Packages, select **DataTransfer.dtsx**, and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="cb3e0-132">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-132">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="cb3e0-133">3-6단계를 반복하되 이번에는 C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Completed Packages에 있는 LoadXMLData.dtsx를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-133">Repeat steps 3 - 6, and this time add LoadXMLData.dtsx, which is found in C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Completed Packages.</span></span>  
  
### <a name="to-add-ancillary-files-to-the-deployment-tutorial-project"></a><span data-ttu-id="cb3e0-134">Deployment Tutorial 프로젝트에 보조 파일을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="cb3e0-134">To add ancillary files to the Deployment Tutorial project</span></span>  
  
1.  <span data-ttu-id="cb3e0-135">솔루션 탐색기에서 Deployment Tutorial을 마우스 오른쪽 단추로 클릭하고 **추가**를 클릭한 다음 **기존 항목**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-135">In Solution Explorer, right-click Deployment Tutorial, click **Add**, and then click **Existing Item**.</span></span>  
  
2.  <span data-ttu-id="cb3e0-136">**기존 항목 추가 - Deployment Tutorial** 대화 상자에서 C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deployment Packages\Sample Data로 이동하여 orders.xml, orders.xsd 및 NewCustomers.txt를 선택한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-136">In the **Add Existing Item - Deployment Tutorial** dialog box, navigate to C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deployment Packages\Sample Data, select orders.xml, orders.xsd, and NewCustomers.txt, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="cb3e0-137">**기존 항목 추가 - Deployment Tutorial** 대화 상자에서 C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deployment Packages\\로 이동하여 Readme.txt를 선택한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-137">In the **Add Existing Item - Deployment Tutorial** dialog box, navigate to C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deployment Packages\\, select Readme.txt and click **Add**.</span></span>  
  
4.  <span data-ttu-id="cb3e0-138">파일 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-138">On the File menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="cb3e0-139">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="cb3e0-139">Next Task in Lesson</span></span>  
 [<span data-ttu-id="cb3e0-140">4단계: 패키지 구성 추가</span><span class="sxs-lookup"><span data-stu-id="cb3e0-140">Step 4: Adding Package Configurations</span></span>](../integration-services/lesson-1-4-adding-package-configurations.md)  
  
<span data-ttu-id="cb3e0-141">![Integration Services 아이콘 (작은 아이콘)](media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="cb3e0-141">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="cb3e0-142">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-142">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="cb3e0-143">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-143">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="cb3e0-144">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="cb3e0-144">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
