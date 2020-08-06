---
title: 패키지 워크플로에 데이터 프로파일링 태스크 포함 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling task [Integration Services], using output in workflow
ms.assetid: 39a51586-6977-4c45-b80b-0157a54ad510
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cd3544586ac99f66b961f7961e4f4af4d9e4a4c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649626"
---
# <a name="incorporate-a-data-profiling-task-in-package-workflow"></a><span data-ttu-id="2431e-102">패키지 워크플로에 데이터 프로파일링 태스크 포함</span><span class="sxs-lookup"><span data-stu-id="2431e-102">Incorporate a Data Profiling Task in Package Workflow</span></span>
  <span data-ttu-id="2431e-103">데이터 프로파일링과 정리는 초기 단계의 자동 처리 대상이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-103">Data profiling and cleanup are not candidates for an automated process in their early stages.</span></span> <span data-ttu-id="2431e-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서 데이터 프로파일링 태스크의 출력을 통해 보고된 위반이 의미 있거나 과도한지 확인하려면 일반적으로 시각적 분석과 사람의 판단이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-104">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], the output of the Data Profiling task usually requires visual analysis and human judgment to determine whether reported violations are meaningful or excessive.</span></span> <span data-ttu-id="2431e-105">데이터 품질 문제를 인지한 이후에도 정리를 위한 최선의 방법을 찾기 위한 신중한 계획이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-105">Even after recognizing data quality problems, there still has to be a carefully thought-out plan that addresses the best approach for cleanup.</span></span>  
  
 <span data-ttu-id="2431e-106">일단 데이터 품질에 대한 조건을 정립하고 나면 데이터 원본에 대한 주기적인 분석과 정리를 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-106">However, after criteria for data quality have been established, you might want to automate a periodic analysis and cleanup of the data source.</span></span> <span data-ttu-id="2431e-107">다음과 같은 시나리오를 고려해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="2431e-107">Consider these scenarios:</span></span>  
  
-   <span data-ttu-id="2431e-108">**증분 로드 전에 데이터 품질 확인**.</span><span class="sxs-lookup"><span data-stu-id="2431e-108">**Checking data quality before an incremental load**.</span></span> <span data-ttu-id="2431e-109">데이터 프로파일링 태스크를 사용하여 Customers 테이블의 CustomerName 열에 사용할 새 데이터의 열 Null 비율 프로필을 컴퓨팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-109">Use the Data Profiling task to compute the Column Null Ratio Profile of new data intended for the CustomerName column in a Customers table.</span></span> <span data-ttu-id="2431e-110">Null 값의 비율이 20%를 초과하면 운영자에게 프로필 출력이 포함된 전자 메일 메시지를 보내고 패키지를 끝냅니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-110">If the percentage of null values is greater than 20%, send an e-mail message that contains the profile output to the operator and end the package.</span></span> <span data-ttu-id="2431e-111">그렇지 않으면 증분 로드를 계속 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-111">Otherwise, continue the incremental load.</span></span>  
  
-   <span data-ttu-id="2431e-112">**지정된 조건이 충족되는 경우 정리 자동화**.</span><span class="sxs-lookup"><span data-stu-id="2431e-112">**Automating cleanup when the specified conditions are met**.</span></span> <span data-ttu-id="2431e-113">데이터 프로파일링 태스크를 사용하여 상태 조회 테이블에 대한 State 열과 우편 번호 조회 테이블에 대한 ZIP Code/Postal Code 열의 값 포함 프로필을 컴퓨팅합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-113">Use the Data Profiling task to compute the Value Inclusion Profile of the State column against a lookup table of states, and of the ZIP Code/Postal Code column against a lookup table of zip codes.</span></span> <span data-ttu-id="2431e-114">상태 값의 포함 수준이 80% 미만인데 ZIP Code/Postal Code 값의 포함 수준이 99%를 초과한다면 이는 두 가지를 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-114">If the inclusion strength of the state values is less than 80%, but the inclusion strength of the ZIP Code/Postal Code values is greater than 99%, this indicates two things.</span></span> <span data-ttu-id="2431e-115">첫째, State 데이터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-115">First, the state data is bad.</span></span> <span data-ttu-id="2431e-116">둘째, ZIP Code/Postal Code 데이터는 올바릅니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-116">Second, the ZIP Code/Postal Code data is good.</span></span> <span data-ttu-id="2431e-117">현재 Zip Code/Postal Code 값에서 올바른 State 값을 조회하여 State 데이터를 정리하는 데이터 흐름 태스크를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-117">Launch a Data Flow task that cleans up the state data by performing a lookup of the correct state value from the current Zip Code/Postal Code value.</span></span>  
  
 <span data-ttu-id="2431e-118">데이터 흐름 태스크를 통합할 수 있는 워크플로를 확보한 후에는 이 태스크를 추가하는 데 필요한 단계를 파악해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-118">After you have a workflow into which you can incorporate the Data Flow task, you have to understand the steps that are required to add this task.</span></span> <span data-ttu-id="2431e-119">다음 섹션에서는 데이터 흐름 태스크를 통합하는 일반적인 프로세스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-119">The next section describes the general process of incorporating the Data Flow task.</span></span> <span data-ttu-id="2431e-120">마지막 두 개의 섹션에서는 데이터 흐름 태스크를 데이터 원본에 직접 연결하거나 데이터 흐름의 변환된 데이터에 연결하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-120">The final two sections describe how to connect the Data Flow task either directly to a data source or to transformed data from the Data Flow.</span></span>  
  
## <a name="defining-a-general-workflow-for-the-data-flow-task"></a><span data-ttu-id="2431e-121">데이터 흐름 태스크의 일반적인 워크플로 정의</span><span class="sxs-lookup"><span data-stu-id="2431e-121">Defining a General Workflow for the Data Flow Task</span></span>  
 <span data-ttu-id="2431e-122">다음 절차에서는 패키지의 워크플로에서 데이터 프로파일링 태스크의 출력을 사용하기 위한 일반적인 방법을 간단히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-122">The following procedure outlines the general approach for using the output of the Data Profiling task in the workflow of a package.</span></span>  
  
#### <a name="to-use-the-output-of-the-data-profiling-task-programmatically-in-a-package"></a><span data-ttu-id="2431e-123">패키지에서 프로그래밍 방식으로 데이터 프로파일링 태스크의 출력을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="2431e-123">To use the output of the Data Profiling task programmatically in a package</span></span>  
  
1.  <span data-ttu-id="2431e-124">패키지에 데이터 프로파일링 태스크를 추가하고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-124">Add and configure the Data Profiling task in a package.</span></span>  
  
2.  <span data-ttu-id="2431e-125">프로필 결과에서 검색하려는 값을 보유하도록 패키지 변수를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-125">Configure package variables to hold the values that you want to retrieve from the profile results.</span></span>  
  
3.  <span data-ttu-id="2431e-126">스크립트 태스크를 추가하고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-126">Add and configure a Script task.</span></span> <span data-ttu-id="2431e-127">데이터 프로파일링 태스크에 스크립트 태스크를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-127">Connect the Script task to the Data Profiling task.</span></span> <span data-ttu-id="2431e-128">스크립트 태스크에서 데이터 프로파일링 태스크의 출력 파일로부터 원하는 값을 읽고 패키지 변수를 채우는 코드를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-128">In the Script task, write code that reads the desired values from the output file of the Data Profiling task and populates the package variables.</span></span>  
  
4.  <span data-ttu-id="2431e-129">워크플로의 다운스트림 분기에 스크립트 태스크를 연결하는 선행 제약 조건에서 변수의 값을 사용하여 워크플로를 제어하는 식을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-129">In the precedence constraints that connect the Script task to downstream branches in the workflow, write expressions that use the values of the variables to direct the workflow.</span></span>  
  
 <span data-ttu-id="2431e-130">데이터 프로파일링 태스크를 패키지의 워크플로에 통합할 때 태스크의 다음 두 가지 특징을 유의하십시오.</span><span class="sxs-lookup"><span data-stu-id="2431e-130">When incorporating the Data Profiling task into the workflow of a package, keep these two features of the task in mind:</span></span>  
  
-   <span data-ttu-id="2431e-131">**태스크 출력**.</span><span class="sxs-lookup"><span data-stu-id="2431e-131">**Task output**.</span></span> <span data-ttu-id="2431e-132">데이터 프로파일링 태스크는 DataProfile.xsd 스키마에 따라 파일 또는 패키지 변수에 XML 형식으로 출력을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-132">The Data Profiling task writes its output to a file or a package variable in XML format according to the DataProfile.xsd schema.</span></span> <span data-ttu-id="2431e-133">따라서 패키지의 조건부 워크플로에서 프로필 결과를 사용하려면 이 XML 출력을 쿼리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-133">Therefore, you have to query the XML output if you want to use the profile results in the conditional workflow of a package.</span></span> <span data-ttu-id="2431e-134">Xpath 쿼리 언어를 사용하면 이 XML 출력을 손쉽게 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-134">You can easily use the Xpath query language to query this XML output.</span></span> <span data-ttu-id="2431e-135">이 XML 출력의 구조를 살펴보려면 예제 출력 파일 또는 스키마 자체를 열면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-135">To study the structure of this XML output, you can open a sample output file or the schema itself.</span></span> <span data-ttu-id="2431e-136">출력 파일 또는 스키마를 열려면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], 다른 XML 편집기 또는 메모장과 같은 텍스트 편집기를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-136">To open the output file or schema, you can use [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], another XML editor, or a text editor, such as Notepad.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2431e-137">데이터 프로필 뷰어에 표시되는 프로필 결과의 일부는 출력에서 직접 찾을 수 없는 계산된 값입니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-137">Some of the profile results that are displayed in the Data Profile Viewer are calculated values that are not directly found in the output.</span></span> <span data-ttu-id="2431e-138">예를 들어 열 Null 비율 프로필에는 전체 행 개수와 Null 값이 있는 행 개수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-138">For example, the output of the Column Null Ratio Profile contains the total number of rows and the number of rows that contain null values.</span></span> <span data-ttu-id="2431e-139">열 Null 비율을 구하려면 이 두 값을 쿼리한 다음 Null 값을 가진 행의 비율을 계산해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-139">You have to query these two values, and then calculate the percentage of rows that contain null values, to obtain the column null ratio.</span></span>  
  
-   <span data-ttu-id="2431e-140">**태스크 입력**.</span><span class="sxs-lookup"><span data-stu-id="2431e-140">**Task input**.</span></span> <span data-ttu-id="2431e-141">데이터 프로파일링 태스크는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에서 입력을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-141">The Data Profiling task reads its input from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables.</span></span> <span data-ttu-id="2431e-142">따라서 이미 로드되어 데이터 흐름에서 변환된 데이터를 프로파일링하려면 메모리에 있는 데이터를 준비 테이블에 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-142">Therefore, you have to save data that is in memory to staging tables if you want to profile data that has already been loaded and transformed in the data flow.</span></span>  
  
 <span data-ttu-id="2431e-143">다음 섹션에서는 외부 데이터 원본으로부터 직접 가져오거나 데이터 흐름 태스크에서 변환된 프로파일링 데이터에 이 일반 워크플로를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-143">The following sections apply this general workflow to profiling data that comes directly from an external data source or that comes transformed from the Data Flow task.</span></span> <span data-ttu-id="2431e-144">또한 데이터 흐름 태스크의 입력 및 출력 요구 사항을 처리하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-144">These sections also show how to handle the input and output requirements of the Data Flow task.</span></span>  
  
## <a name="connecting-the-data-profiling-task-directly-to-an-external-data-source"></a><span data-ttu-id="2431e-145">데이터 프로파일링 태스크를 외부 데이터 원본에 직접 연결</span><span class="sxs-lookup"><span data-stu-id="2431e-145">Connecting the Data Profiling Task Directly to an External Data Source</span></span>  
 <span data-ttu-id="2431e-146">데이터 프로파일링 태스크는 데이터 원본에서 직접 가져온 데이터를 프로파일링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-146">The Data Profiling task can profile data that comes directly from a data source.</span></span>  <span data-ttu-id="2431e-147">다음 예에서는 이 기능을 설명하기 위해 데이터 프로파일링 태스크를 사용하여 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 데이터베이스에 있는 Person.Address 테이블의 열에서 열 Null 비율 프로필을 컴퓨팅합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-147">To illustrate this capability, the following example uses the Data Profiling task to compute a Column Null Ratio Profile on the columns of the Person.Address table in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="2431e-148">그런 다음 스크립트 태스크를 사용하여 출력 파일에서 결과를 검색하고, 워크플로를 제어하는 데 사용할 수 있는 패키지 변수를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-148">Then, this example uses a Script task to retrieve the results from the output file and populate package variables that can be used to direct workflow.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2431e-149">이 간단한 예에서는 Null 값 비율이 높은 AddressLine2 열을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-149">The AddressLine2 column was selected for this simple example because this column contains a high percentage of null values.</span></span>  
  
 <span data-ttu-id="2431e-150">이 예는 다음과 같은 단계로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-150">This example consists of the following steps:</span></span>  
  
-   <span data-ttu-id="2431e-151">프로필 결과를 포함할 출력 파일과 외부 데이터 원본에 연결되는 연결 관리자를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-151">Configuring the connection managers that connect to the external data source and to the output file that will contain the profile results.</span></span>  
  
-   <span data-ttu-id="2431e-152">데이터 프로파일링 태스크에 필요한 값을 보유할 패키지 변수를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-152">Configuring the package variables that will hold the values needed by the Data Profiling task.</span></span>  
  
-   <span data-ttu-id="2431e-153">열 Null 비율 프로필을 컴퓨팅하도록 데이터 프로파일링 태스크를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-153">Configuring the Data Profiling task to compute the Column Null Ratio Profile.</span></span>  
  
-   <span data-ttu-id="2431e-154">데이터 프로파일링 태스크의 XML 출력을 사용하도록 스크립트 태스크를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-154">Configuring the Script task to work the XML output from the Data Profiling task.</span></span>  
  
-   <span data-ttu-id="2431e-155">데이터 프로파일링 태스크의 결과를 바탕으로 실행할 워크플로의 다운스트림 분기를 제어하는 선행 제약 조건을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-155">Configuring the precedence constraints that will control which downstream branches in the workflow are run based on the results of the Data Profiling task.</span></span>  
  
### <a name="configure-the-connection-managers"></a><span data-ttu-id="2431e-156">연결 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="2431e-156">Configure the Connection Managers</span></span>  
 <span data-ttu-id="2431e-157">이 예에서는 다음과 같은 두 개의 연결 관리자가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-157">For this example, there are two connection managers:</span></span>  
  
-   <span data-ttu-id="2431e-158">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 데이터베이스에 연결되는 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="2431e-158">An [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that connects to the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.</span></span>  
  
-   <span data-ttu-id="2431e-159">데이터 프로파일링 태스크의 결과를 보유할 출력 파일을 만드는 파일 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="2431e-159">A File connection manager that creates the output file that will hold the results of the Data Profiling task.</span></span>  
  
##### <a name="to-configure-the-connection-managers"></a><span data-ttu-id="2431e-160">연결 관리자를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="2431e-160">To configure the connection managers</span></span>  
  
1.  <span data-ttu-id="2431e-161">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 새 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-161">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], create a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span>  
  
2.  <span data-ttu-id="2431e-162">패키지에 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 연결 관리자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-162">Add an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to the package.</span></span> <span data-ttu-id="2431e-163">.NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient)를 사용하고, 가용한 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 데이터베이스 인스턴스에 연결하도록 이 연결 관리자를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-163">Configure this connection manager to use the NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) and to connect to an available instance of the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.</span></span>  
  
     <span data-ttu-id="2431e-164">기본적으로 연결 관리자의 이름은 \<server name>.AdventureWorks1입니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-164">By default, the connection manager has the following name: \<server name>.AdventureWorks1.</span></span>  
  
3.  <span data-ttu-id="2431e-165">패키지에 파일 연결 관리자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-165">Add a File connection manager to the package.</span></span> <span data-ttu-id="2431e-166">데이터 프로파일링 태스크를 위한 출력 파일을 만들도록 이 연결 관리자를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-166">Configure this connection manager to create the output file for the Data Profiling task.</span></span>  
  
     <span data-ttu-id="2431e-167">이 예에서는 파일 이름으로 DataProfile1.xml을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-167">This example uses the file name, DataProfile1.xml.</span></span> <span data-ttu-id="2431e-168">기본적으로 연결 관리자의 이름은 파일과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-168">By default, the connection manager has the same name as the file.</span></span>  
  
### <a name="configure-the-package-variables"></a><span data-ttu-id="2431e-169">패키지 변수 구성</span><span class="sxs-lookup"><span data-stu-id="2431e-169">Configure the Package Variables</span></span>  
 <span data-ttu-id="2431e-170">이 예에서는 다음과 같은 두 개의 패키지 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-170">This example uses two package variables:</span></span>  
  
-   <span data-ttu-id="2431e-171">ProfileConnectionName 변수는 파일 연결 관리자의 이름을 스크립트 태스크에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-171">The ProfileConnectionName variable passes the name of the File connection manager to the Script task.</span></span>  
  
-   <span data-ttu-id="2431e-172">AddressLine2NullRatio 변수는 이 열에 대해 계산된 Null 비율을 스크립트 태스크에서 패키지로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-172">The AddressLine2NullRatio variable passes the calculated null ratio for this column out of the Script task to the package.</span></span>  
  
##### <a name="to-configure-the-package-variables-that-will-hold-profile-results"></a><span data-ttu-id="2431e-173">프로필 결과를 보유할 패키지 변수를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="2431e-173">To configure the package variables that will hold profile results</span></span>  
  
-   <span data-ttu-id="2431e-174">**변수** 창에서 다음 두 개의 패키지 변수를 추가하고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-174">In the **Variables** window, add and configure the following two package variables:</span></span>  
  
    -   <span data-ttu-id="2431e-175">`ProfileConnectionName`변수 중 하나에 대해 이름을 입력 하 고이 변수의 유형을 **String**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-175">Enter the name, `ProfileConnectionName`, for one of the variables and set the type of this variable to **String**.</span></span>  
  
    -   <span data-ttu-id="2431e-176">`AddressLine2NullRatio`다른 변수에 대 한 이름을 입력 하 고이 변수의 유형을 **Double**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-176">Enter the name, `AddressLine2NullRatio`, for the other variable and set the type of this variable to **Double**.</span></span>  
  
### <a name="configure-the-data-profiling-task"></a><span data-ttu-id="2431e-177">데이터 프로파일링 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="2431e-177">Configure the Data Profiling Task</span></span>  
 <span data-ttu-id="2431e-178">데이터 프로파일링 태스크는 다음과 같이 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-178">The Data Profiling task has to be configured in the following way:</span></span>  
  
-   <span data-ttu-id="2431e-179">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 연결 관리자가 입력으로 제공하는 데이터를 사용하도록 구성</span><span class="sxs-lookup"><span data-stu-id="2431e-179">To use the data that the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager supplies as input.</span></span>  
  
-   <span data-ttu-id="2431e-180">입력 데이터에 대해 열 Null 비율 프로필을 수행하도록 구성</span><span class="sxs-lookup"><span data-stu-id="2431e-180">To perform a Column Null Ratio profile on the input data.</span></span>  
  
-   <span data-ttu-id="2431e-181">파일 연결 관리자와 연관된 파일에 프로필 결과를 저장하도록 구성</span><span class="sxs-lookup"><span data-stu-id="2431e-181">To save the profile results to the file that is associated with the File connection manager.</span></span>  
  
##### <a name="to-configure-the-data-profiling-task"></a><span data-ttu-id="2431e-182">데이터 프로파일링 태스크를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="2431e-182">To configure the Data Profiling task</span></span>  
  
1.  <span data-ttu-id="2431e-183">제어 흐름에 데이터 프로파일링 태스크를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-183">To the Control Flow, add a Data Profiling task.</span></span>  
  
2.  <span data-ttu-id="2431e-184">**데이터 프로파일링 태스크 편집기** 를 열어 태스크를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-184">Open the **Data Profiling Task Editor** to configure the task.</span></span>  
  
3.  <span data-ttu-id="2431e-185">편집기 **일반** 페이지의 **대상**에서 이전에 구성한 파일 연결 관리자의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-185">On the **General** page of the editor, for **Destination**, select the name of the File connection manager that you have previously configured.</span></span>  
  
4.  <span data-ttu-id="2431e-186">편집기의 **프로필 요청** 페이지에서 새 열 Null 비율 프로필을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-186">On the **Profile Requests** page of the editor, create a new Column Null Ratio Profile.</span></span>  
  
5.  <span data-ttu-id="2431e-187">**요청 속성** 창의 **ConnectionManager**에서 이전에 구성한 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 연결 관리자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-187">In the **Request properties** pane, for **ConnectionManager**, select the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that you have previously configured.</span></span> <span data-ttu-id="2431e-188">그런 다음 **TableOrView**에서 Person.Address를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-188">Then, for **TableOrView**, select Person.Address.</span></span>  
  
6.  <span data-ttu-id="2431e-189">데이터 프로파일링 태스크 편집기를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-189">Close the Data Profiling Task Editor.</span></span>  
  
### <a name="configure-the-script-task"></a><span data-ttu-id="2431e-190">스크립트 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="2431e-190">Configure the Script Task</span></span>  
 <span data-ttu-id="2431e-191">스크립트 태스크는 출력 파일에서 결과를 검색하고 이전에 구성된 패키지 변수를 채우도록 구성되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-191">The Script task has to be configured to retrieve the results from the output file and populate the package variables that were previously configured.</span></span>  
  
##### <a name="to-configure-the-script-task"></a><span data-ttu-id="2431e-192">스크립트 태스크를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="2431e-192">To configure the Script task</span></span>  
  
1.  <span data-ttu-id="2431e-193">제어 흐름에 스크립트 태스크를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-193">To the Control Flow, add a Script task.</span></span>  
  
2.  <span data-ttu-id="2431e-194">데이터 프로파일링 태스크에 스크립트 태스크를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-194">Connect the Script task to the Data Profiling task.</span></span>  
  
3.  <span data-ttu-id="2431e-195">**스크립트 태스크 편집기** 를 열어 태스크를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-195">Open the **Script Task Editor** to configure the task.</span></span>  
  
4.  <span data-ttu-id="2431e-196">**스크립트** 페이지에서 선호하는 프로그래밍 언어를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-196">On the **Script** page, select your preferred programming language.</span></span> <span data-ttu-id="2431e-197">그런 다음 스크립트에서 사용할 수 있는 두 개의 패키지 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-197">Then, make the two package variables available to the script:</span></span>  
  
    1.  <span data-ttu-id="2431e-198">에 대해 `ReadOnlyVariables` 를 선택 `ProfileConnectionName` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-198">For `ReadOnlyVariables`, select `ProfileConnectionName`.</span></span>  
  
    2.  <span data-ttu-id="2431e-199">**ReadWriteVariables**의 경우를 선택 `AddressLine2NullRatio` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-199">For **ReadWriteVariables**, select `AddressLine2NullRatio`.</span></span>  
  
5.  <span data-ttu-id="2431e-200">**스크립트 편집** 을 선택하여 스크립트 개발 환경을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-200">Select **Edit Script** to open the script development environment.</span></span>  
  
6.  <span data-ttu-id="2431e-201">System.Xml 네임스페이스에 대한 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-201">Add a reference to the System.Xml namespace.</span></span>  
  
7.  <span data-ttu-id="2431e-202">선택한 프로그래밍 언어에 해당하는 예제 코드를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-202">Enter the sample code that corresponds to your programming language:</span></span>  
  
    ```vb  
    Imports System  
    Imports Microsoft.SqlServer.Dts.Runtime  
    Imports System.Xml  
  
    Public Class ScriptMain  
  
      Private FILENAME As String = "C:\ TEMP\DataProfile1.xml"  
      Private PROFILE_NAMESPACE_URI As String = "https://schemas.microsoft.com/DataDebugger/"  
      Private NULLCOUNT_XPATH As String = _  
        "/default:DataProfile/default:DataProfileOutput/default:Profiles" & _  
        "/default:ColumnNullRatioProfile[default:Column[@Name='AddressLine2']]/default:NullCount/text()"  
      Private TABLE_XPATH As String = _  
        "/default:DataProfile/default:DataProfileOutput/default:Profiles" & _  
        "/default:ColumnNullRatioProfile[default:Column[@Name='AddressLine2']]/default:Table"  
  
      Public Sub Main()  
  
        Dim profileConnectionName As String  
        Dim profilePath As String  
        Dim profileOutput As New XmlDocument  
        Dim profileNSM As XmlNamespaceManager  
        Dim nullCountNode As XmlNode  
        Dim nullCount As Integer  
        Dim tableNode As XmlNode  
        Dim rowCount As Integer  
        Dim nullRatio As Double  
  
        ' Open output file.  
        profileConnectionName = Dts.Variables("ProfileConnectionName").Value.ToString()  
        profilePath = Dts.Connections(profileConnectionName).ConnectionString  
        profileOutput.Load(profilePath)  
        profileNSM = New XmlNamespaceManager(profileOutput.NameTable)  
        profileNSM.AddNamespace("default", PROFILE_NAMESPACE_URI)  
  
        ' Get null count for column.  
        nullCountNode = profileOutput.SelectSingleNode(NULLCOUNT_XPATH, profileNSM)  
        nullCount = CType(nullCountNode.Value, Integer)  
  
        ' Get row count for table.  
        tableNode = profileOutput.SelectSingleNode(TABLE_XPATH, profileNSM)  
        rowCount = CType(tableNode.Attributes("RowCount").Value, Integer)  
  
        ' Compute and return null ratio.  
        nullRatio = nullCount / rowCount  
        Dts.Variables("AddressLine2NullRatio").Value = nullRatio  
  
        Dts.TaskResult = Dts.Results.Success  
  
      End Sub  
  
    End Class  
    ```  
  
    ```csharp  
    using System;  
    using Microsoft.SqlServer.Dts.Runtime;  
    using System.Xml;  
  
    public class ScriptMain  
    {  
  
      private string FILENAME = "C:\\ TEMP\\DataProfile1.xml";  
      private string PROFILE_NAMESPACE_URI = "https://schemas.microsoft.com/DataDebugger/";  
      private string NULLCOUNT_XPATH = "/default:DataProfile/default:DataProfileOutput/default:Profiles" + "/default:ColumnNullRatioProfile[default:Column[@Name='AddressLine2']]/default:NullCount/text()";  
      private string TABLE_XPATH = "/default:DataProfile/default:DataProfileOutput/default:Profiles" + "/default:ColumnNullRatioProfile[default:Column[@Name='AddressLine2']]/default:Table";  
  
      public void Main()  
      {  
  
        string profileConnectionName;  
        string profilePath;  
        XmlDocument profileOutput = new XmlDocument();  
        XmlNamespaceManager profileNSM;  
        XmlNode nullCountNode;  
        int nullCount;  
        XmlNode tableNode;  
        int rowCount;  
        double nullRatio;  
  
        // Open output file.  
        profileConnectionName = Dts.Variables["ProfileConnectionName"].Value.ToString();  
        profilePath = Dts.Connections[profileConnectionName].ConnectionString;  
        profileOutput.Load(profilePath);  
        profileNSM = new XmlNamespaceManager(profileOutput.NameTable);  
        profileNSM.AddNamespace("default", PROFILE_NAMESPACE_URI);  
  
        // Get null count for column.  
        nullCountNode = profileOutput.SelectSingleNode(NULLCOUNT_XPATH, profileNSM);  
        nullCount = (int)nullCountNode.Value;  
  
        // Get row count for table.  
        tableNode = profileOutput.SelectSingleNode(TABLE_XPATH, profileNSM);  
        rowCount = (int)tableNode.Attributes["RowCount"].Value;  
  
        // Compute and return null ratio.  
        nullRatio = nullCount / rowCount;  
        Dts.Variables["AddressLine2NullRatio"].Value = nullRatio;  
  
        Dts.TaskResult = Dts.Results.Success;  
  
      }  
  
    }  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="2431e-203">이 절차에 사용되는 예제 코드는 파일에서 데이터 프로파일링 태스크의 출력을 로드하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-203">The sample code shown in this procedure demonstrates how to load the output of the Data Profiling task from a file.</span></span> <span data-ttu-id="2431e-204">파일이 아닌 패키지 변수에서 데이터 프로파일링 태스크의 출력을 로드하려면 이 절차 다음에 나오는 대체 예제 코드를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2431e-204">To load the output of the Data Profiling task from a package variable instead, see the alternative sample code that follows this procedure.</span></span>  
  
8.  <span data-ttu-id="2431e-205">스크립트 개발 환경과 스크립트 태스크 편집기를 차례로 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-205">Close the script development environment, and then close the Script Task Editor.</span></span>  
  
#### <a name="alternative-code-reading-the-profile-output-from-a-variable"></a><span data-ttu-id="2431e-206">대체 코드 - 변수에서 프로필 출력 읽기</span><span class="sxs-lookup"><span data-stu-id="2431e-206">Alternative Code-Reading the Profile Output from a Variable</span></span>  
 <span data-ttu-id="2431e-207">앞의 절차는 파일에서 데이터 프로파일링 작업의 출력을 로드하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-207">The previous procedure shows how to load the output of the Data Profiling task from a file.</span></span> <span data-ttu-id="2431e-208">대체 방법을 사용하여 패키지 변수에서 이 출력을 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-208">However, an alternative method would be to load this output from a package variable.</span></span> <span data-ttu-id="2431e-209">변수에서 출력을 로드하려면 예제 코드를 다음과 같이 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-209">To load the output from a variable, you have to make the following changes to the sample code:</span></span>  
  
-   <span data-ttu-id="2431e-210">`LoadXml` 메서드 대신 `XmlDocument` 클래스의 `Load` 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-210">Call the `LoadXml` method of the `XmlDocument` class instead of the `Load` method.</span></span>  
  
-   <span data-ttu-id="2431e-211">스크립트 태스크 편집기에서 프로필 출력이 포함된 패키지 변수의 이름을 태스크의 `ReadOnlyVariables` 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-211">In the Script Task Editor, add the name of the package variable that contains the profile output to the task's `ReadOnlyVariables` list.</span></span>  
  
-   <span data-ttu-id="2431e-212">다음 코드 예와 같이 변수의 문자열 값을 `LoadXML` 메서드에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-212">Pass the string value of the variable to the `LoadXML` method, as shown in the following code example.</span></span> <span data-ttu-id="2431e-213">이 예에서는 프로필 출력이 포함된 패키지 변수의 이름으로 "ProfileOutput"을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-213">(This example uses "ProfileOutput" as the name of the package variable that contains the profile output.)</span></span>  
  
    ```vb  
    Dim outputString As String  
    outputString = Dts.Variables("ProfileOutput").Value.ToString()  
    ...  
    profileOutput.LoadXml(outputString)  
    ```  
  
    ```csharp  
    string outputString;  
    outputString = Dts.Variables["ProfileOutput"].Value.ToString();  
    ...  
    profileOutput.LoadXml(outputString);  
    ```  
  
### <a name="configure-the-precedence-constraints"></a><span data-ttu-id="2431e-214">선행 제약 조건 구성</span><span class="sxs-lookup"><span data-stu-id="2431e-214">Configure the Precedence Constraints</span></span>  
 <span data-ttu-id="2431e-215">선행 제약 조건은 데이터 프로파일링 태스크의 결과를 바탕으로 실행할 워크플로의 다운스트림 분기를 제어하도록 구성되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-215">The precedence constraints have to be configured to control which downstream branches in the workflow are run based on the results of the Data Profiling task.</span></span>  
  
##### <a name="to-configure-the-precedence-constraints"></a><span data-ttu-id="2431e-216">선행 제약 조건을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="2431e-216">To configure the precedence constraints</span></span>  
  
-   <span data-ttu-id="2431e-217">워크플로의 다운스트림 분기에 스크립트 태스크를 연결하는 선행 제약 조건에서 변수의 값을 사용하여 워크플로를 제어하는 식을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-217">In the precedence constraints that connect the Script task to downstream branches in the workflow, write expressions that use the values of the variables to direct the workflow.</span></span>  
  
     <span data-ttu-id="2431e-218">예를 들어 선행 제약 조건의 **식 연산** 을 **식 및 제약 조건**으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-218">For example, you might set the **Evaluation operation** of the precedence constraint to **Expression and Constraint**.</span></span> <span data-ttu-id="2431e-219">그런 다음 `@AddressLine2NullRatio < .90` 을 식의 값으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-219">Then, you might use `@AddressLine2NullRatio < .90` as the value of the expression.</span></span> <span data-ttu-id="2431e-220">이렇게 하면 워크플로는 이전 태스크가 성공한 경우와 선택된 열의 Null 값 비율이 90% 미만인 경우 지정된 경로를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-220">This causes the workflow to follow the selected path when the previous tasks succeed, and when the percentage of null values in the selected column is less than 90%.</span></span>  
  
## <a name="connecting-the-data-profiling-task-to-transformed-data-from-the-data-flow"></a><span data-ttu-id="2431e-221">데이터 흐름의 변환된 데이터에 데이터 프로파일링 태스크 연결</span><span class="sxs-lookup"><span data-stu-id="2431e-221">Connecting the Data Profiling Task to Transformed Data from the Data Flow</span></span>  
 <span data-ttu-id="2431e-222">데이터 원본으로부터 직접 데이터를 프로파일링하는 대신 이미 로드되어 데이터 흐름에서 변환된 데이터를 프로파일링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-222">Instead of profiling data directly from a data source, you can profile data that has already been loaded and transformed in the data flow.</span></span> <span data-ttu-id="2431e-223">단, 데이터 프로파일링 태스크는 영구 데이터에 대해서만 작동하며 메모리 내 데이터에 대해서는 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-223">However, the Data Profiling task works only against persisted data, not against in-memory data.</span></span> <span data-ttu-id="2431e-224">따라서 먼저 대상 구성 요소를 사용하여 준비 테이블에 변환된 데이터를 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-224">Therefore, you must first use a destination component to save the transformed data to a staging table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2431e-225">데이터 프로파일링 태스크를 구성할 때 기존 테이블과 열을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-225">When you configure the Data Profiling task, you have to select existing tables and columns.</span></span> <span data-ttu-id="2431e-226">따라서 태스크를 구성하려면 먼저 디자인 타임에 준비 테이블을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-226">Therefore, you must create the staging table at design time before you can configure the task.</span></span> <span data-ttu-id="2431e-227">즉, 이 시나리오에서는 런타임에 만들어지는 임시 테이블을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-227">In other words, this scenario does not allow you to use a temporary table that is created at run time.</span></span>  
  
 <span data-ttu-id="2431e-228">준비 테이블에 데이터를 저장한 후에는 다음 동작을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-228">After saving the data to a staging table, you can do the following actions:</span></span>  
  
-   <span data-ttu-id="2431e-229">데이터 프로파일링 태스크를 사용하여 데이터 프로파일링</span><span class="sxs-lookup"><span data-stu-id="2431e-229">Use the Data Profiling task to profile the data.</span></span>  
  
-   <span data-ttu-id="2431e-230">이 항목의 앞부분에서 설명한 대로 스크립트 태스크를 사용하여 결과 읽기</span><span class="sxs-lookup"><span data-stu-id="2431e-230">Use a Script task to read the results as described earlier in this topic.</span></span>  
  
-   <span data-ttu-id="2431e-231">이러한 결과를 사용하여 패키지의 후속 워크플로 제어</span><span class="sxs-lookup"><span data-stu-id="2431e-231">Use those results to direct the subsequent workflow of the package.</span></span>  
  
 <span data-ttu-id="2431e-232">다음 절차에서는 데이터 흐름에 의해 변환된 데이터를 데이터 프로파일링 태스크를 사용하여 프로파일링하기 위한 일반적인 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-232">The following procedure provides the general approach for using the Data Profiling task to profile data that has been transformed by the data flow.</span></span> <span data-ttu-id="2431e-233">이 단계는 앞에서 설명한 외부 데이터 원본에서 직접 가져온 데이터를 프로파일링하는 단계와 많이 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-233">Many of these steps are similar to the ones described earlier for profiling data that comes directly from an external data source.</span></span> <span data-ttu-id="2431e-234">다양한 구성 요소를 구성하는 방법은 앞의 단계를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2431e-234">You might want to review those earlier steps for more information about how to configure the various components.</span></span>  
  
#### <a name="to-use-the-data-profiling-task-in-the-data-flow"></a><span data-ttu-id="2431e-235">데이터 흐름에서 데이터 프로파일링 태스크를 사용하려면</span><span class="sxs-lookup"><span data-stu-id="2431e-235">To use the Data Profiling task in the data flow</span></span>  
  
1.  <span data-ttu-id="2431e-236">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 패키지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-236">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], create a package.</span></span>  
  
2.  <span data-ttu-id="2431e-237">데이터 흐름에서 적절한 원본과 변환을 추가, 구성 및 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-237">In the Data Flow, add, configure, and connect the appropriate sources and transformations.</span></span>  
  
3.  <span data-ttu-id="2431e-238">데이터 흐름에서 변환된 데이터를 준비 테이블에 저장하는 대상 구성 요소를 추가, 구성 및 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-238">In the Data Flow, add, configure, and connect a destination component that saves the transformed data to a staging table.</span></span>  
  
4.  <span data-ttu-id="2431e-239">제어 흐름에서 준비 테이블의 변환된 데이터에 대해 원하는 프로파일을 계산하는 데이터 프로파일링 태스크를 추가하고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-239">In the Control Flow, add and configure a Data Profiling task that computes the desired profiles against the transformed data in the staging table.</span></span> <span data-ttu-id="2431e-240">데이터 프로파일링 태스크를 데이터 흐름 태스크에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-240">Connect the Data Profiling task to the Data Flow task.</span></span>  
  
5.  <span data-ttu-id="2431e-241">프로필 결과에서 검색하려는 값을 보유하도록 패키지 변수를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-241">Configure package variables to hold the values that you want to retrieve from the profile results.</span></span>  
  
6.  <span data-ttu-id="2431e-242">스크립트 태스크를 추가하고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-242">Add and configure a Script task.</span></span> <span data-ttu-id="2431e-243">데이터 프로파일링 태스크에 스크립트 태스크를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-243">Connect the Script task to the Data Profiling task.</span></span> <span data-ttu-id="2431e-244">스크립트 태스크에서 데이터 프로파일링 태스크의 출력으로부터 원하는 값을 읽고 패키지 변수를 채우는 코드를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-244">In the Script task, write code that reads the desired values from the output of the Data Profiling task and populates the package variables.</span></span>  
  
7.  <span data-ttu-id="2431e-245">워크플로의 다운스트림 분기에 스크립트 태스크를 연결하는 선행 제약 조건에서 변수의 값을 사용하여 워크플로를 제어하는 식을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="2431e-245">In the precedence constraints that connect the Script task to downstream branches in the workflow, write expressions that use the values of the variables to direct the workflow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2431e-246">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2431e-246">See Also</span></span>  
 <span data-ttu-id="2431e-247">[데이터 프로파일링 태스크 설정](data-profiling-task.md) </span><span class="sxs-lookup"><span data-stu-id="2431e-247">[Setup of the Data Profiling Task](data-profiling-task.md) </span></span>  
 [<span data-ttu-id="2431e-248">데이터 프로필 뷰어</span><span class="sxs-lookup"><span data-stu-id="2431e-248">Data Profile Viewer</span></span>](data-profile-viewer.md)  
  
  
