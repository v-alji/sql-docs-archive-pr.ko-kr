---
title: '4단계: 6단원 패키지 배포 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b613cef7-7993-4d89-a429-a8251d74d435
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8c5109dc96af138bbd0c8c0087e8b73cf3bac435
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661251"
---
# <a name="step-4-deploying-the-lesson-6-package"></a><span data-ttu-id="5de99-102">4단계: 6단원 패키지 배포</span><span class="sxs-lookup"><span data-stu-id="5de99-102">Step 4: Deploying the Lesson 6 Package</span></span>
  <span data-ttu-id="5de99-103">패키지를 배포하려면 SQL Server 인스턴스의 Integration Services에서 SSISDB 카탈로그에 패키지를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-103">Deploying the package involves adding the package to the SSISDB catalog in Integration Services on an instance of SQL Server.</span></span> <span data-ttu-id="5de99-104">이 단원에서는 6 단원 패키지를 SSISDB 카탈로그에 추가하고, 매개 변수를 설정하 고 패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-104">In this lesson you will add the Lesson 6 package to the SSISDB catalog, set the parameter, and execute the package.</span></span> <span data-ttu-id="5de99-105">이 단원에서 SQL Server Management Studio를 사용하여 SSISDB 카탈로그에 6 단원 패키지를 추가하고 패키지를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-105">For this lesson you will use SQL Server Management Studio to add the Lesson 6 package to the SSISDB catalog, and deploy the package.</span></span> <span data-ttu-id="5de99-106">패키지를 배포한 후 새 위치를 가리키도록 패키지를 수정한 다음 매개 변수를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-106">After deploying the package you will modify the parameter to point to a new location then execute the package.</span></span>  
  
 <span data-ttu-id="5de99-107">이 단원에서는 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-107">In this lesson you will:</span></span>  
  
-   <span data-ttu-id="5de99-108">SQL Server의 SSIS 노드에서 SSISDB 카탈로그에 패키지를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-108">Add the package to the SSISDB catalog in the SSIS node in SQL Server.</span></span>  
  
-   <span data-ttu-id="5de99-109">패키지를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-109">Deploy the package.</span></span>  
  
-   <span data-ttu-id="5de99-110">패키지 매개 변수 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-110">Set the package parameter value.</span></span>  
  
-   <span data-ttu-id="5de99-111">SSMS에서 패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-111">Execute the package in SSMS.</span></span>  
  
### <a name="to-locate-or-add-the-ssisdb-catalog"></a><span data-ttu-id="5de99-112">SSISDB 카탈로그를 찾거나 추가하려면</span><span class="sxs-lookup"><span data-stu-id="5de99-112">To Locate or add the SSISDB catalog</span></span>  
  
1.  <span data-ttu-id="5de99-113">시작, 모든 프로그램, Microsoft SQL Server 2012를 가리킨 다음 SQL Management Studio를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-113">Click Start, point to All Programs, point to Microsoft SQL Server 2012, and then click SQL Management Studio.</span></span>  
  
2.  <span data-ttu-id="5de99-114">서버에 연결 대화 상자에서 기본 설정을 확인한 다음 연결을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-114">On the Connect to Server dialog box, verify the default settings, and then click Connect.</span></span> <span data-ttu-id="5de99-115">연결하려면 서버 이름 상자에 SQL Server가 설치된 컴퓨터의 이름을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-115">To connect, the Server name box must contain the name of the computer where SQL Server is installed.</span></span> <span data-ttu-id="5de99-116">데이터베이스 엔진이 명명된 인스턴스인 경우 서버 이름 상자에 <computer_name>\\<instance_name> 형식으로 인스턴스 이름도 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-116">If the Database Engine is a named instance, the Server name box should also contain the instance name in the format <computer_name>\\<instance_name>.</span></span>  
  
3.  <span data-ttu-id="5de99-117">개체 탐색기에서 Integration Services 카탈로그를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-117">In Object Explorer expand Integration Services Catalogs.</span></span>  
  
4.  <span data-ttu-id="5de99-118">Integration Services 카탈로그 아래에 나열된 카탈로그가 없는 경우에 SSISDB 카탈로그를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-118">If there are no catalogs listed under Integration Services Catalogs then add the SSISDB catalog.</span></span>  
  
5.  <span data-ttu-id="5de99-119">SSISDB 카탈로그를 추가하려면 Integration Services 카탈로그를 마우스 오른쪽 단추로 클릭하고 카탈로그 만들기를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-119">To Add the SSISDB catalog, right-click Integration Services Catalogs and click Create Catalog.</span></span>  
  
6.  <span data-ttu-id="5de99-120">카탈로그 만들기 대화 상자에서 CLR 통합 사용을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-120">On the Create Catalog dialog box select Enable CLR Integration.</span></span>  
  
7.  <span data-ttu-id="5de99-121">암호 상자에 새 암호를 입력한 다음 암호를 다시 입력 상자에 다시 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-121">In the Password box, type a new password then type it again in the Retype Password box.</span></span> <span data-ttu-id="5de99-122">입력한 암호를 기억해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-122">Be sure to remember the password you type.</span></span>  
  
8.  <span data-ttu-id="5de99-123">SSISDB 카탈로그를 추가하려면 확인을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-123">Click OK to add the SSISDB catalog.</span></span>  
  
### <a name="to-add-the-package-to-the-ssisdb-catalog"></a><span data-ttu-id="5de99-124">SSISDB 카탈로그에 패키지를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="5de99-124">To add the package to the SSISDB catalog</span></span>  
  
1.  <span data-ttu-id="5de99-125">개체 탐색기에서 SSISDB를 마우스 오른쪽 단추로 클릭하고 폴더 만들기를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-125">In Object Explorer, right-click SSISDB and click Create Folder.</span></span>  
  
2.  <span data-ttu-id="5de99-126">폴더 만들기 대화 상자에서 폴더 이름 상자에 SSIS 자습서를 입력하고 확인을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-126">In the Create Folder dialog box type SSIS Tutorial in the Folder name box and click OK.</span></span>  
  
3.  <span data-ttu-id="5de99-127">SSIS 자습서 폴더를 확장하고 프로젝트를 마우스 오른쪽 단추로 클릭하고 패키지 가져오기를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-127">Expand the SSIS Tutorial folder, right-click Projects, and click Import Packages.</span></span>  
  
4.  <span data-ttu-id="5de99-128">Integration Services 프로젝트 변환 마법사 소개 페이지에서 다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-128">On the Integration Services Project Conversion Wizard Introduction page click Next.</span></span>  
  
5.  <span data-ttu-id="5de99-129">패키지 찾기 페이지에서 파일 시스템이 원본 목록에서 선택되어 있는지 확인한 다음 찾아보기를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-129">On the Locate Packages page, ensure that File system is selected in the Source list, then click Browse.</span></span>  
  
6.  <span data-ttu-id="5de99-130">폴더 찾아보기 대화 상자에서 SSIS 자습서 프로젝트를 포함하는 폴더를 찾은 다음 확인을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-130">On the Browse For Folder dialog box, browse to the folder containing the SSIS Tutorial project, then click OK.</span></span>  
  
7.  <span data-ttu-id="5de99-131">다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-131">Click Next.</span></span>  
  
8.  <span data-ttu-id="5de99-132">패키지 선택 페이지에서 SSIS 자습서의 패키지 6개가 모두 표시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-132">On the Select Packages page you should see all six packages from the SSIS Tutorial.</span></span> <span data-ttu-id="5de99-133">패키지 목록에서 Lesson 6.dtsx를 선택하고 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-133">In the Packages list, select Lesson 6.dtsx, then click Next.</span></span>  
  
9. <span data-ttu-id="5de99-134">대상 선택 페이지에서 프로젝트 이름 상자에 SSIS 자습서 배포를 입력하고 다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-134">On the Select Destination page, type SSIS Tutorial Deployment in the Project Name box then click Next.</span></span>  
  
10. <span data-ttu-id="5de99-135">검토 페이지에 도달할 때까지 나머지 마법사의 각 페이지에서 다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-135">Click Next on each of the remaining wizard pages until you get to the Review page.</span></span>  
  
11. <span data-ttu-id="5de99-136">검토 페이지에서 변환을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-136">On the Review page, click Convert.</span></span>  
  
12. <span data-ttu-id="5de99-137">변환이 완료되면 닫기를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-137">When the conversion completes, click Close.</span></span>  
  
 <span data-ttu-id="5de99-138">Integration Services 프로젝트 변환 마법사를 닫으면 SSIS가 Integration Services 배포 마법사를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-138">When you close the Integration Services Project Conversion Wizard, SSIS displays the Integration Services Deployment Wizard.</span></span> <span data-ttu-id="5de99-139">6 단원 패키지를 배포하려면 지금 이 마법사를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-139">You will use this wizard now to deploy the Lesson 6 package.</span></span>  
  
1.  <span data-ttu-id="5de99-140">Integration Services 배포 마법사 소개 페이지에서 프로젝트를 배포하기 위한 단계를 검토하고 다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-140">On the Integration Services Deployment Wizard Introduction page, review the steps for deploying the project, then click Next.</span></span>  
  
2.  <span data-ttu-id="5de99-141">대상 선택 페이지에서 서버 이름이 SSISDB 카탈로그를 포함하는 SQL Server의 인스턴스이고 경로에 SSIS 자습서 배포가 표시되는지 확인한 후 다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-141">On the Select Destination page verify that the server name is the instance of SQL Server containing the SSISDB catalog and that the path shows SSIS Tutorial Deployment, then click Next.</span></span>  
  
3.  <span data-ttu-id="5de99-142">검토 페이지에서 요약을 검토한 다음 배포를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-142">On the Review page, review the Summary then click Deploy.</span></span>  
  
4.  <span data-ttu-id="5de99-143">배포가 완료되면 닫기를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-143">When the deployment completes, click Close.</span></span>  
  
5.  <span data-ttu-id="5de99-144">개체 탐색기에서 Integration Services 카탈로그를 마우스 오른쪽 단추로 클릭하고 새로고침을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-144">In Object Explorer, right-click Integration Services Catalogs and click Refresh.</span></span>  
  
6.  <span data-ttu-id="5de99-145">Integration Services 카탈로그를 확장한 다음 SSISDB를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-145">Expand Integration Services Catalogs then expand SSISDB.</span></span> <span data-ttu-id="5de99-146">프로젝트가 완전히 확장될 때까지 SSIS 자습서에서 트리를 계속 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-146">Continue to Expand the tree under SSIS Tutorial until you have completely expanded the project.</span></span> <span data-ttu-id="5de99-147">SSIS 자습서 배포 노드의 패키지 노드 아래에 Lesson 6.dtsx가 표시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-147">You should see Lesson 6.dtsx under the Packages node of the SSIS Tutorial Deployment node.</span></span>  
  
 <span data-ttu-id="5de99-148">패키지가 완료되었는지 확인하려면 Lesson 6.dtsx를 마우스 오른쪽 단추로 클릭하고 구성을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-148">To verify that the package is complete, right-click Lesson 6.dtsx and click Configure.</span></span> <span data-ttu-id="5de99-149">구성 대화 상자에서 매개 변수를 선택하고, 컨테이너에 Lesson 6.dtsx, 이름에 VarFolderName, 값에 새 New Sample Data 경로가 입력되어 있는지 확인한 다음, 닫기를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-149">On the Configure dialog box, select Parameters and verify that there is an entry with Lesson 6.dtsx as the Container, VarFolderName as the Name and the path to New Sample Data as the value, then click Close.</span></span>  
  
 <span data-ttu-id="5de99-150">새 샘플 데이터 폴더 만들기를 진행하기 전에 Sample Data Two라고 이름을 지정하고 원래의 샘플 파일 3개를 여기에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-150">Before continuing create a new sample data folder, name it Sample Data Two, and copy any three of the original sample files into it.</span></span>  
  
### <a name="to-create-and-populate-a-new-sample-data-folder"></a><span data-ttu-id="5de99-151">새 예제 데이터 폴더를 만들고 채우려면</span><span class="sxs-lookup"><span data-stu-id="5de99-151">To create and populate a new sample data folder</span></span>  
  
1.  <span data-ttu-id="5de99-152">Windows 탐색기의 드라이브 루트 수준(예: C:\\)에서 Sample Data Two라는 새 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-152">In Windows Explorer, at the root level of your drive (for example, C:\\), create a new folder named Sample Data Two.</span></span>  
  
2.  <span data-ttu-id="5de99-153">C:\Program Files\Microsoft SQL Server\110\Samples\Integration Services\Tutorial\Creating a Simple ETL Package\Sample Data 폴더를 열고 폴더에서 3개 샘플 파일 중 하나를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-153">Open the c:\Program Files\Microsoft SQL Server\110\Samples\Integration Services\Tutorial\Creating a Simple ETL Package\Sample Data folder and then copy any three of the sample files from the folder.</span></span>  
  
3.  <span data-ttu-id="5de99-154">New Sample Data 폴더에 복사한 파일을 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-154">In the New Sample Data folder, paste the copied files.</span></span>  
  
### <a name="to-change-the-package-parameter-to-point-to-the-new-sample-data"></a><span data-ttu-id="5de99-155">새 샘플 데이터를 가리키도록 패키지 매개 변수를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="5de99-155">To change the package parameter to point to the new sample data</span></span>  
  
1.  <span data-ttu-id="5de99-156">개체 탐색기에서 Lesson 6.dtsx를 마우스 오른쪽 단추로 클릭한 다음 구성을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-156">In Object Explorer, right click Lesson 6.dtsx and click Configure.</span></span>  
  
2.  <span data-ttu-id="5de99-157">구성 대화 상자에서 매개 변수 값을 Sample Data Two 경로로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-157">On the Configure dialog box, change the parameter value to the path to Sample Data Two.</span></span> <span data-ttu-id="5de99-158">예를 들어, C 드라이브의 루트 폴더에 새 폴더를 배치하는 경우 C:\Sample Data Two가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-158">For example C:\Sample Data Two if you placed the new folder in the root folder on the C drive.</span></span>  
  
3.  <span data-ttu-id="5de99-159">확인을 클릭하여 구성 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-159">Click OK to close the Configure dialog box.</span></span>  
  
### <a name="to-test-the-lesson-6-package-deployment"></a><span data-ttu-id="5de99-160">6 단원 패키지 배포를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="5de99-160">To test the Lesson 6 package deployment</span></span>  
  
1.  <span data-ttu-id="5de99-161">개체 탐색기에서 Lesson 6.dtsx를 마우스 오른쪽 단추로 클릭한 다음 실행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-161">In Object Explorer, right click Lesson 6.dtsx and click Execute.</span></span>  
  
2.  <span data-ttu-id="5de99-162">패키지 실행 대화 상자에서 확인을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-162">On the Execute Package dialog box, click OK.</span></span>  
  
3.  <span data-ttu-id="5de99-163">메시지 대화 상자에서 예를 클릭하여 개요 보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-163">On the message dialog box click Yes to open Overview Report.</span></span>  
  
 <span data-ttu-id="5de99-164">패키지에 대한 개요 보고서는 패키지의 이름과 요약 상태를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-164">The Overview report for the package is displayed showing the name of the package and a status summary.</span></span> <span data-ttu-id="5de99-165">실행 개요 섹션은 패키지의 각 작업에서 결과를 보여주고 사용된 매개 변수 섹션은 VarFolderName을 포함하여 패키지 실행에 사용된 모든 매개 변수의 이름과 값을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="5de99-165">The Execution Overview section shows the result from each task in the package and the Parameters Used section shows the names and values of all parameters used in the package execution, including VarFolderName.</span></span>  
  
  
