---
title: '2단계: Foreach 루프 컨테이너 추가 및 구성 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 88a973cc-0f23-4ecf-adb6-5b06279c2df6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: de5e8875c43edda618ccef4839c88c3b84a003cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647114"
---
# <a name="step-2-adding-and-configuring-the-foreach-loop-container"></a><span data-ttu-id="aeca9-102">2단계: Foreach 루프 컨테이너 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="aeca9-102">Step 2: Adding and Configuring the Foreach Loop Container</span></span>
  <span data-ttu-id="aeca9-103">이 태스크에서는 플랫 파일 폴더를 통해 루핑하고 1단원에서 사용한 것과 같은 데이터 흐름 변환을 각 플랫 파일에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-103">In this task, you will add the ability to loop through a folder of flat files and apply the same data flow transformation used in Lesson 1 to each of those flat files.</span></span> <span data-ttu-id="aeca9-104">제어 흐름에 Foreach 루프 컨테이너를 추가하고 구성하여 이 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-104">You do this by adding and configuring a Foreach Loop container to the control flow.</span></span>  
  
 <span data-ttu-id="aeca9-105">추가한 Foreach 루프 컨테이너는 폴더의 각 플랫 파일에 연결할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-105">The Foreach Loop container that you add must be able to connect to each flat file in the folder.</span></span> <span data-ttu-id="aeca9-106">폴더의 파일이 모두 같은 형식이므로 Foreach 루프 컨테이너가 같은 플랫 파일 연결 관리자를 사용하여 이러한 파일에 각각 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-106">Because all the files in the folder have the same format, the Foreach Loop container can use the same Flat File connection manager to connect to each of these files.</span></span> <span data-ttu-id="aeca9-107">컨테이너가 사용할 플랫 파일 연결 관리자는 1단원에서 만든 것과 같은 플랫 파일 연결 관리자입니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-107">The Flat File connection manager that the container will use is the same Flat File connection manager that you created in Lesson 1.</span></span>  
  
 <span data-ttu-id="aeca9-108">현재 1단원에서 만든 플랫 파일 연결 관리자는 특정 플랫 파일 하나에만 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-108">Currently, the Flat File connection manager from Lesson 1 connects to only one, specific flat file.</span></span> <span data-ttu-id="aeca9-109">폴더의 각 플랫 파일에 반복하여 연결하려면 다음과 같이 Foreach 루프 컨테이너와 플랫 파일 연결 관리자를 둘 다 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-109">To iteratively connect to each flat file in the folder, you will have to configure both the Foreach Loop container and the Flat File connection manager as follows:</span></span>  
  
-   <span data-ttu-id="aeca9-110">**Foreach 루프 컨테이너:** 컨테이너의 열거된 값을 사용자 정의 패키지 변수에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-110">**Foreach Loop container:** You will map the enumerated value of the container to a user-defined package variable.</span></span> <span data-ttu-id="aeca9-111">그러면 컨테이너가 이 사용자 정의 변수를 사용하여 플랫 파일 연결 관리자의 `ConnectionString` 속성을 수정하고 폴더의 각 플랫 파일에 반복하여 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-111">The container will then use this user-defined variable to dynamically modify the `ConnectionString` property of the Flat File connection manager and iteratively connect to each flat file in the folder.</span></span>  
  
-   <span data-ttu-id="aeca9-112">**플랫 파일 연결 관리자:** 사용자 정의 변수를 사용 하 여 연결 관리자의 속성을 채워 1 단원에서 만든 연결 관리자를 수정 합니다 `ConnectionString` .</span><span class="sxs-lookup"><span data-stu-id="aeca9-112">**Flat File connection manager:** You will modify the connection manager that was created in Lesson 1 by using a user-defined variable to populate the connection manager's `ConnectionString` property.</span></span>  
  
 <span data-ttu-id="aeca9-113">이 태스크의 절차에서는 Foreach 루프 컨테이너를 만들고 수정하여 사용자 정의 패키지 변수를 사용하고 루프에 데이터 흐름 작업을 추가하는 방법과</span><span class="sxs-lookup"><span data-stu-id="aeca9-113">The procedures in this task show you how to create and modify the Foreach Loop container to use a user-defined package variable and to add the data flow task to the loop.</span></span> <span data-ttu-id="aeca9-114">플랫 파일 연결 관리자를 수정하여 다음 태스크에서 사용자 정의 변수를 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-114">You will learn how to modify the Flat File connection manager to use a user-defined variable in the next task.</span></span>  
  
 <span data-ttu-id="aeca9-115">패키지를 수정한 후 패키지가 실행되면 Foreach 루프 컨테이너가 Sample Data 폴더의 파일 집합 전체에서 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-115">After you have made these modifications to the package, when the package is run, the Foreach Loop Container will iterate through the collection of files in the Sample Data folder.</span></span> <span data-ttu-id="aeca9-116">Foreach 루프 컨테이너는 조건에 맞는 파일을 발견할 때마다 사용자 정의 변수를 파일 이름으로 채우고 Sample Currency Data 플랫 파일 연결 관리자의 `ConnectionString` 속성에 사용자 정의 변수를 매핑한 다음 해당 파일에 대해 데이터 흐름을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-116">Each time a file is found that matches the criteria, the Foreach Loop Container will populate the user-defined variable with the file name, map the user-defined variable to the `ConnectionString` property of the Sample Currency Data Flat File connection manager, and then run the data flow against that file.</span></span> <span data-ttu-id="aeca9-117">따라서 Foreach 루프가 반복될 때마다 데이터 흐름 태스크에서 다른 플랫 파일을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-117">Therefore, in each iteration of the Foreach Loop the Data Flow task will consume a different flat file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aeca9-118">[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서는 흐름 제어를 데이터 흐름과 분리하므로 제어 흐름에 추가한 루핑에서는 데이터 흐름을 수정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-118">Because [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] separates control flow from data flow, any looping that you add to the control flow will not require modification to the data flow.</span></span> <span data-ttu-id="aeca9-119">따라서 1단원에서 만든 데이터 흐름을 변경하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-119">Therefore, the data flow that you created in Lesson 1 does not have to be changed.</span></span>  
  
### <a name="to-add-a-foreach-loop-container"></a><span data-ttu-id="aeca9-120">Foreach 루프 컨테이너를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="aeca9-120">To add a Foreach Loop container</span></span>  
  
1.  <span data-ttu-id="aeca9-121">**SQL Server Data Tools**에서 **제어 흐름** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-121">In **SQL Server Data Tools**, click the **Control Flow** tab.</span></span>  
  
2.  <span data-ttu-id="aeca9-122">**SSIS 도구 상자**에서 **컨테이너**를 확장한 다음 **Foreach 루프 컨테이너** 를 **제어 흐름** 탭의 디자인 화면으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-122">In the **SSIS Toolbox**, expand **Containers**, and then drag a **Foreach Loop Container** onto the design surface of the **Control Flow** tab.</span></span>  
  
3.  <span data-ttu-id="aeca9-123">새로 추가한 **Foreach 루프 컨테이너** 를 마우스 오른쪽 단추로 클릭하고 **편집**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-123">Right-click the newly added **Foreach Loop Container** and select **Edit**.</span></span>  
  
4.  <span data-ttu-id="aeca9-124">**Foreach 루프 편집기** 대화 상자의 **일반** 페이지에서 **이름**에을 입력 `Foreach File in Folder` 합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-124">In the **Foreach Loop Editor** dialog box, on the **General** page, for **Name**, enter `Foreach File in Folder`.</span></span> <span data-ttu-id="aeca9-125">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-125">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="aeca9-126">Foreach 루프 컨테이너를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 클릭 한 다음 속성 창에서 `LocaleID` 속성이 **영어 (미국)** 로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-126">Right-click the Foreach Loop container, click **Properties**, and in the Properties window, verify that the `LocaleID` property is set to **English (United States)**.</span></span>  
  
### <a name="to-configure-the-enumerator-for-the-foreach-loop-container"></a><span data-ttu-id="aeca9-127">Foreach 루프 컨테이너의 열거자를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="aeca9-127">To configure the enumerator for the Foreach Loop container</span></span>  
  
1.  <span data-ttu-id="aeca9-128">Foreach File in Folder를 두 번 클릭하여 **Foreach 루프 편집기**를 다시 엽니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-128">Double-click Foreach File in Folder to reopen the **Foreach Loop Editor**.</span></span>  
  
2.  <span data-ttu-id="aeca9-129">**컬렉션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-129">Click **Collection**.</span></span>  
  
3.  <span data-ttu-id="aeca9-130">**컬렉션** 페이지에서 **Foreach File 열거자**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-130">On the **Collection** page, select **Foreach File Enumerator**.</span></span>  
  
4.  <span data-ttu-id="aeca9-131">**열거자 구성** 그룹에서 **찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-131">In the **Enumerator configuration** group, click **Browse**.</span></span>  
  
5.  <span data-ttu-id="aeca9-132">**폴더 찾아보기** 대화 상자에서 Currency_\*.txt 파일이 들어 있는 컴퓨터의 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-132">In the **Browse for Folder** dialog box, locate the folder on your machine that contains the Currency_\*.txt files.</span></span>  
  
     <span data-ttu-id="aeca9-133">이 예제 데이터는 [!INCLUDE[ssIS](../includes/ssis-md.md)] 단원 패키지에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-133">This sample data is included with the [!INCLUDE[ssIS](../includes/ssis-md.md)] lesson packages.</span></span> <span data-ttu-id="aeca9-134">예제 데이터 및 단원 패키지를 다운로드하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-134">To download the sample data and the lesson packages, do the following.</span></span>  
  
    1.  <span data-ttu-id="aeca9-135">[Integration Services 제품 예제](https://go.microsoft.com/fwlink/?LinkId=275027)로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-135">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="aeca9-136">**다운로드** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-136">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="aeca9-137">" https://msftisprodsamples.codeplex.com/downloads/get/578097 " SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip 파일 하이퍼링크를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-137">Click the  HYPERLINK "https://msftisprodsamples.codeplex.com/downloads/get/578097" SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
6.  <span data-ttu-id="aeca9-138">**파일** 상자에 **Currency_\*.txt**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-138">In the **Files** box, type **Currency_\*.txt**.</span></span>  
  
### <a name="to-map-the-enumerator-to-a-user-defined-variable"></a><span data-ttu-id="aeca9-139">사용자 정의 변수에 열거자를 매핑하려면</span><span class="sxs-lookup"><span data-stu-id="aeca9-139">To map the enumerator to a user-defined variable</span></span>  
  
1.  <span data-ttu-id="aeca9-140">**변수 매핑**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-140">Click **Variable Mappings**.</span></span>  
  
2.  <span data-ttu-id="aeca9-141">**변수 매핑** 페이지의 **변수** 열에서 빈 셀을 클릭 하 고를 선택 **\<New Variable...>** 합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-141">On the **Variable Mappings** page, in the **Variable** column, click the empty cell and select **\<New Variable...>**.</span></span>  
  
3.  <span data-ttu-id="aeca9-142">**변수 추가** 대화 상자에서 **이름**에을 입력 `varFileName` 합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-142">In the **Add Variable** dialog box, for **Name**, type `varFileName`.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="aeca9-143">변수 이름은 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-143">Variable names are case sensitive.</span></span>  
  
4.  <span data-ttu-id="aeca9-144">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-144">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="aeca9-145">**확인** 을 다시 클릭하여 **Foreach 루프 편집기** 대화 상자를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca9-145">Click **OK** again to exit the **Foreach Loop Editor** dialog box.</span></span>  
  
### <a name="to-add-the-data-flow-task-to-the-loop"></a><span data-ttu-id="aeca9-146">루프에 데이터 흐름 태스크를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="aeca9-146">To add the data flow task to the loop</span></span>  
  
-   <span data-ttu-id="aeca9-147">**Extract Sample Currency data** 데이터 흐름 태스크를 지금 이름이 바뀐 Foreach 루프 컨테이너로 끌어 옵니다 `Foreach File in Folder` .</span><span class="sxs-lookup"><span data-stu-id="aeca9-147">Drag the **Extract Sample Currency Data** data flow task onto the Foreach Loop container now renamed `Foreach File in Folder`.</span></span>  
  
## <a name="next-lesson-task"></a><span data-ttu-id="aeca9-148">다음 단원 태스크</span><span class="sxs-lookup"><span data-stu-id="aeca9-148">Next Lesson Task</span></span>  
 [<span data-ttu-id="aeca9-149">3단계: 플랫 파일 연결 관리자 수정</span><span class="sxs-lookup"><span data-stu-id="aeca9-149">Step 3: Modifying the Flat File Connection Manager</span></span>](lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
## <a name="see-also"></a><span data-ttu-id="aeca9-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aeca9-150">See Also</span></span>  
 <span data-ttu-id="aeca9-151">[Foreach 루프 컨테이너 구성](control-flow/foreach-loop-container.md) </span><span class="sxs-lookup"><span data-stu-id="aeca9-151">[Configure a Foreach Loop Container](control-flow/foreach-loop-container.md) </span></span>  
 [<span data-ttu-id="aeca9-152">패키지에서 변수 사용</span><span class="sxs-lookup"><span data-stu-id="aeca9-152">Use Variables in Packages</span></span>](use-variables-in-packages.md)  
  
