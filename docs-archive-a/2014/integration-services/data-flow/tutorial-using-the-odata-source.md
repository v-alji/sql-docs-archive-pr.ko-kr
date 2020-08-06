---
title: '자습서: OData 원본 사용 [SSIS] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 2c64cf8b-5edb-48df-8ffe-697096258f71
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a13b04494ed00251774b490b1cc929769a869acb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659543"
---
# <a name="tutorial-using-the-odata-source-ssis"></a><span data-ttu-id="55265-102">자습서: OData 원본 사용 [SSIS]</span><span class="sxs-lookup"><span data-stu-id="55265-102">Tutorial: Using the OData Source [SSIS]</span></span>
  <span data-ttu-id="55265-103">이 자습서에서는 샘플 **Northwind** OData 서비스(http://services.odata.org/V3/Northwind/Northwind.svc/) 에서 **Employees** 컬렉션을 추출한 다음, 플랫 파일로 로드하는 프로세스를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-103">This tutorial walks you through the process to extract the **Employees** collection from the sample **Northwind** OData service (http://services.odata.org/V3/Northwind/Northwind.svc/), and then load it into a flat file.</span></span>  
  
## <a name="1-create-an-integration-services-project"></a><span data-ttu-id="55265-104">1. Integration Services 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="55265-104">1. Create an Integration Services Project</span></span>  
  
1.  <span data-ttu-id="55265-105">**SQL Server Data Tools** 또는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-105">Launch **SQL Server Data Tools** or [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span>  
  
2.  <span data-ttu-id="55265-106">**File**을 클릭하고 **New**를 가리킨 다음 **프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-106">Click **File**, point to **New**, and click **Project**.</span></span>  
  
3.  <span data-ttu-id="55265-107">**새 프로젝트** 대화 상자에서 **설치됨**, **템플릿**, **비즈니스 인텔리전스**를 차례로 확장하고 **Integration Services**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-107">In the **New Project** dialog box, expand **Installed**, expand **Templates**, expand **Business Intelligence**, and click **Integration Services**.</span></span>  
  
4.  <span data-ttu-id="55265-108">프로젝트 유형으로 **Integration Services 프로젝트** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-108">Select **Integration Services Project** for the type of project.</span></span>  
  
5.  <span data-ttu-id="55265-109">**이름** 을 입력하고 프로젝트의 **위치** 를 선택한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-109">Enter a **name** and select a **location** for the project, and click **OK**.</span></span>  
  
## <a name="2-add-and-configure-odata-source-to-the-ssis-package"></a><span data-ttu-id="55265-110">2. OData 원본을 SSIS 패키지에 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="55265-110">2. Add and Configure OData Source to the SSIS Package</span></span>  
  
1.  <span data-ttu-id="55265-111">**데이터 흐름 태스크** 를 **SSIS 도구 상자** 에서 SSIS 패키지의 제어 흐름 디자인 화면에 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="55265-111">Drag-drop a **Data Flow Task** from the **SSIS Toolbox** on to the control flow design surface of your SSIS package.</span></span>  
  
2.  <span data-ttu-id="55265-112">**데이터 흐름** 탭을 클릭하거나 새로 추가된 **데이터 흐름 태스크** 를 두 번 클릭하여 **데이터 흐름 디자인 화면**을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-112">Click the **Data Flow** tab, or double click on the newly added **Data Flow Task** to launch the **Data Flow design surface**.</span></span>  
  
3.  <span data-ttu-id="55265-113">**SSIS 도구 상자** 의 **공통** 그룹에서 **OData 원본**을 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="55265-113">Drag-drop **OData Source** from the **Common** group in the **SSIS Toolbox**.</span></span> <span data-ttu-id="55265-114">**OData 원본** 이 처음 설치되면 **SSIS 도구 상자** 의 **공통**그룹에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="55265-114">When the **OData Source** is first installed, it will appear under the **Common** group in the **SSIS Toolbox**.</span></span>  
  
4.  <span data-ttu-id="55265-115">**OData 원본** 구성 요소를 두 번 클릭해서 **OData 원본 편집기** 대화 상자를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-115">Double click the **OData Source** component to launch the **OData Source Editor** dialog box.</span></span>  
  
5.  <span data-ttu-id="55265-116">**새로 만들기...** 를 클릭하여 새 OData 연결 관리자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-116">Click **New...** to add a new OData Connection Manager.</span></span>  
  
6.  <span data-ttu-id="55265-117">**서비스 문서 위치**에 대해 OData 서비스 URL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-117">Enter the OData service URL for **Service document location**.</span></span> <span data-ttu-id="55265-118">이 URL은 서비스 문서나 특정 피드 또는 엔터티에 대한 URL일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55265-118">This can be the URL to the service document, or to a specific feed or entity.</span></span> <span data-ttu-id="55265-119">이 자습서의 목적을 위해를 입력 [http://services.odata.org/V3/Northwind/Northwind.svc/](http://services.odata.org/V3/Northwind/Northwind.svc/) 합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-119">For the purpose of this tutorial, type [http://services.odata.org/V3/Northwind/Northwind.svc/](http://services.odata.org/V3/Northwind/Northwind.svc/).</span></span>  
  
7.  <span data-ttu-id="55265-120">OData 서비스에 액세스하는 데 사용할 **인증** 으로 **Windows 인증** 이 선택되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-120">Confirm that **Windows Authentication** is selected for the **authentication** to use to access the OData Service.</span></span> <span data-ttu-id="55265-121">기본적으로**Windows 인증** 이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="55265-121">**Windows Authentication** is selected by default.</span></span> <span data-ttu-id="55265-122">기본 인증을 사용하려면 **이 사용자 이름 및 암호 사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-122">To use basic authentication, select **Use this user name and password**.</span></span>  
  
8.  <span data-ttu-id="55265-123">연결에 대해 **연결 테스트** 를 클릭하고 **확인** 을 클릭하여 OData 연결 관리자의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="55265-123">Click **Test Connection** to the connection, and click **OK** to create an instance of OData Connection Manager.</span></span>  
  
9. <span data-ttu-id="55265-124">**OData 원본 편집기** 대화 상자에서 **리소스 경로에 컬렉션 사용** 옵션에 대해 **컬렉션** 이 선택되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-124">In the **OData Source Editor** Dialog Box, confirm that **Collection** is selected for **Use collection on resource path** option.</span></span>  
  
10. <span data-ttu-id="55265-125">**컬렉션** 드롭다운 목록에서 **Employees**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-125">From the **Collection** drop down list, select **Employees**.</span></span>  
  
11. <span data-ttu-id="55265-126">**쿼리 옵션**에 대해 추가 OData 쿼리 옵션 또는 필터를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-126">Enter any additional OData query options or filters for **Query Options**.</span></span> <span data-ttu-id="55265-127">예:</span><span class="sxs-lookup"><span data-stu-id="55265-127">Ex.</span></span> <span data-ttu-id="55265-128">$orderby=CompanyName&$top=100.</span><span class="sxs-lookup"><span data-stu-id="55265-128">$orderby=CompanyName&$top=100.</span></span> <span data-ttu-id="55265-129">이 자습서에서는 **$top=5**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-129">For the purpose of this tutorial, enter **$top=5**.</span></span>  
  
12. <span data-ttu-id="55265-130">**미리 보기** 를 클릭해서 데이터를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="55265-130">Click **Preview** to preview the data.</span></span>  
  
13. <span data-ttu-id="55265-131">왼쪽 탐색 창에서 **열** 을 클릭해서 **열** 페이지로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-131">Click **Columns** in the left navigation pane to switch to the **Columns** page.</span></span>  
  
14. <span data-ttu-id="55265-132">확인란을 선택해서 **사용 가능한 외부 열**에서 **EmployeeID**, **FirstName** 및 **LastName** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-132">Select **EmployeeID**, **FirstName**, and **LastName** from **Available External Columns** by checking the check boxes.</span></span>  
  
15. <span data-ttu-id="55265-133">**확인** 을 클릭해서 **OData 원본 편집기** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="55265-133">Click **OK** to close the **OData Source Editor** dialog box.</span></span>  
  
## <a name="3-add-flat-file-destination-and-test-the-solution"></a><span data-ttu-id="55265-134">3. 플랫 파일 대상 추가 및 솔루션 테스트</span><span class="sxs-lookup"><span data-stu-id="55265-134">3. Add Flat File Destination and Test the Solution</span></span>  
  
1.  <span data-ttu-id="55265-135">이제 **SSIS 도구 상자** 에서 **OData 원본** 구성 요소 아래의 데이터 흐름 디자인 화면으로 **플랫 파일 대상** 을 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="55265-135">Now, drag-drop a **Flat File Destination** from **SSIS Toolbox** to the Data Flow design surface below the **OData Source** component.</span></span>  
  
2.  <span data-ttu-id="55265-136">파란색 화살표를 사용해서 **OData 원본** 구성 요소를 **플랫 파일 대상** 구성 요소와 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-136">Connect **OData Source** component with the **Flat File Destination** component using blue arrow.</span></span>  
  
3.  <span data-ttu-id="55265-137">**플랫 파일 대상**을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-137">Double-click on **Flat File Destination**.</span></span> <span data-ttu-id="55265-138">**플랫 파일 대상 편집기** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="55265-138">You should see the **Flat File Destination Editor** dialog box.</span></span>  
  
4.  <span data-ttu-id="55265-139">**플랫 파일 대상 편집기** 대화 상자에서 **새로 만들기** 를 클릭하여 새 플랫 파일 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="55265-139">In the **Flat File Destination Editor** dialog box, click **New** to create a new flat file connection manager.</span></span>  
  
5.  <span data-ttu-id="55265-140">**플랫 파일 형식** 대화 상자에서 **구분 기호로 분리됨**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-140">In the **Flat File Format** dialog box, select **Delimited**.</span></span> <span data-ttu-id="55265-141">**플랫 파일 연결 관리자 편집기** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="55265-141">You should see the **Flat File Connection Manager Editor** dialog box.</span></span>  
  
6.  <span data-ttu-id="55265-142">**플랫 파일 연결 관리자 편집기** 대화 상자에서 **파일 이름**으로 **c:\Employees.txt**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-142">In the **Flat File Connection Manager Editor** dialog box, for the **File name**, enter **c:\Employees.txt**.</span></span>  
  
7.  <span data-ttu-id="55265-143">왼쪽 탐색 창에서 **열**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-143">In the left navigation pane, click **Columns**.</span></span> <span data-ttu-id="55265-144">이 페이지에서 데이터를 미리 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55265-144">You can preview the data on this page.</span></span>  
  
8.  <span data-ttu-id="55265-145">확인을 클릭하여 **플랫 파일 연결 관리자** 편집기 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="55265-145">Click OK to close the **Flat File Connection Manager** Editor dialog box.</span></span>  
  
9. <span data-ttu-id="55265-146">**플랫 파일 대상 편집기** 대화 상자에서 왼쪽 탐색 창에 있는 **매핑** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-146">In the **Flat File Destination Editor** dialog box, click **Mappings** in the left navigation pane.</span></span> <span data-ttu-id="55265-147">매핑을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-147">Review the mappings.</span></span>  
  
10. <span data-ttu-id="55265-148">확인을 클릭하여 **플랫 파일 대상 편집기** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="55265-148">Click OK to close the **Flat File Destination Editor** dialog box.</span></span>  
  
11. <span data-ttu-id="55265-149">SSIS 패키지를 컴파일하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-149">Compile and execute the SSIS package.</span></span> <span data-ttu-id="55265-150">OData 피드로부터 5명의 직원에 대한 ID, First Name 및 Last Name을 사용해서 출력 파일이 만들어졌는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="55265-150">Verify that the output file is created with ID, First Name, and Last Name for 5 employees from the OData feed.</span></span>  
  
  
