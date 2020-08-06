---
title: '2단계: 패키지 구성 설정 및 구성 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 005218ab-8dd5-48e9-a185-6bc60cd43a7a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a804efcd84ebe563a13f61443fe19096788ca809
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648433"
---
# <a name="step-2-enabling-and-configuring-package-configurations"></a><span data-ttu-id="465a1-102">2단계: 패키지 구성 설정 및 구성</span><span class="sxs-lookup"><span data-stu-id="465a1-102">Step 2: Enabling and Configuring Package Configurations</span></span>
  <span data-ttu-id="465a1-103">이 작업에서는 프로젝트를 패키지 배포 모델로 변환하고 패키지 구성 마법사를 사용하여 패키지 구성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-103">In this task, you will convert the project to the Package Deployment Model and enable package configurations using the Package Configuration Wizard.</span></span> <span data-ttu-id="465a1-104">이 마법사를 사용하여 Foreach 루프 컨테이너의 `Directory` 속성에 대한 구성 설정을 포함하는 XML 구성 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-104">You will use this wizard to generate an XML configuration file that contains configuration settings for the `Directory` property of the Foreach Loop container.</span></span> <span data-ttu-id="465a1-105">런타임에 업데이트할 수 있는 새 패키지 수준 변수에서 Directory 속성 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-105">The value of the Directory property is supplied by a new package-level variable that you can update at run time.</span></span> <span data-ttu-id="465a1-106">또한 테스트하는 동안 사용할 새로운 예제 데이터 폴더를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-106">Additionally, you will populate a new sample data folder to use during testing.</span></span>  
  
### <a name="to-create-a-new-package-level-variable-mapped-to-the-directory-property"></a><span data-ttu-id="465a1-107">Directory 속성에 매핑되는 새 패키지 수준 변수를 만들려면</span><span class="sxs-lookup"><span data-stu-id="465a1-107">To create a new package-level variable mapped to the Directory property</span></span>  
  
1.  <span data-ttu-id="465a1-108">**디자이너에서** 제어 흐름 [!INCLUDE[ssIS](../includes/ssis-md.md)] 탭의 배경을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-108">Click the background of the **Control Flow** tab in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="465a1-109">그러면 패키지에 만들 변수의 범위가 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-109">This sets the scope for the variable you will create to the package.</span></span>  
  
2.  <span data-ttu-id="465a1-110">[!INCLUDE[ssIS](../includes/ssis-md.md)] 메뉴에서 **변수**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-110">On the [!INCLUDE[ssIS](../includes/ssis-md.md)] menu, select **Variables**.</span></span>  
  
3.  <span data-ttu-id="465a1-111">**변수** 창에서 변수 추가 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-111">In the **Variables** window, click the Add Variable icon.</span></span>  
  
4.  <span data-ttu-id="465a1-112">**이름** 상자에 **varFolderName**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-112">In the **Name** box, type **varFolderName**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="465a1-113">변수 이름은 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-113">Variable names are case sensitive.</span></span>  
  
5.  <span data-ttu-id="465a1-114">**범위** 상자에 패키지 이름 Lesson 5가 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-114">Verify that the **Scope** box shows the name of the package, Lesson 5.</span></span>  
  
6.  <span data-ttu-id="465a1-115">**변수의** 데이터 형식 `varFolderName` 상자 값을 **String**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-115">Set the value of the **Data Type** box of the `varFolderName` variable to **String**.</span></span>  
  
7.  <span data-ttu-id="465a1-116">**제어 흐름** 탭으로 돌아가 **Foreach File in Folder** 컨테이너를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-116">Return to the **Control Flow** tab and double-click the **Foreach File in Folder** container.</span></span>  
  
8.  <span data-ttu-id="465a1-117">**Foreach 루프 편집기**의 **컬렉션** 페이지에서 **Expressions**를 클릭한 다음, 줄임표 단추 **(...)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-117">On the **Collection** page of the **Foreach Loop Editor**, click **Expressions**, and then click the ellipsis button **(...)**.</span></span>  
  
9. <span data-ttu-id="465a1-118">**속성 식 편집기**에서 **속성** 목록을 클릭 하 고를 선택 `Directory` 합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-118">In the **Property Expressions Editor**, click in the **Property** list, and select `Directory`.</span></span>  
  
10. <span data-ttu-id="465a1-119">**식** 상자에서 줄임표 단추 **(...)** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-119">In the **Expression** box, click the ellipsis button **(...)**.</span></span>  
  
11. <span data-ttu-id="465a1-120">**식 작성기**에서 변수 폴더를 확장하고 **User::varFolderName** 변수를 **식** 상자로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-120">In the **Expression Builder**, expand the Variables folder, and drag the variable **User::varFolderName** to the **Expression** box.</span></span>  
  
12. <span data-ttu-id="465a1-121">**확인** 을 클릭하여 **식 작성기**를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-121">Click **OK** to exit the **Expression Builder**.</span></span>  
  
13. <span data-ttu-id="465a1-122">**확인** 을 클릭하여 **속성 식 편집기**를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-122">Click **OK** to exit the **Property Expressions Editor**.</span></span>  
  
14. <span data-ttu-id="465a1-123">**확인** 을 클릭하여 **For 루프 편집기**를 끝냅니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-123">Click **OK** to exit the **Foreach Loop Editor**.</span></span>  
  
### <a name="to-enable-package-configurations"></a><span data-ttu-id="465a1-124">패키지 구성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="465a1-124">To enable package configurations</span></span>  
  
1.  <span data-ttu-id="465a1-125">**프로젝트 메뉴**에서 **패키지 배포 모델로 변환**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-125">On the **Project Menu**, click **Convert to Package Deployment Model**.</span></span>  
  
2.  <span data-ttu-id="465a1-126">경고 프롬프트에서 **확인** 을 클릭하고 변환이 완료되면 **패키지 배포 모델로 변환** 대화 상자에서 **확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-126">Click **OK** on the warning prompt and, once the conversion is complete, click **OK** on the **Convert to Package Deployment Model** dialog.</span></span>  
  
3.  <span data-ttu-id="465a1-127">**디자이너에서** 제어 흐름 [!INCLUDE[ssIS](../includes/ssis-md.md)] 탭의 배경을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-127">Click the background of the **Control Flow** tab in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
4.  <span data-ttu-id="465a1-128">**SSIS** 메뉴에서 **패키지 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-128">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
5.  <span data-ttu-id="465a1-129">**패키지 구성 도우미** 대화 상자에서 **패키지 구성 설정**을 선택한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-129">In the **Package Configurations Organizer** dialog box, select **Enable Package Configurations**, and then click **Add**.</span></span>  
  
6.  <span data-ttu-id="465a1-130">패키지 구성 마법사 시작 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-130">On the welcome page of the Package Configuration Wizard, click **Next**.</span></span>  
  
7.  <span data-ttu-id="465a1-131">**구성 유형 선택** 페이지에서 **구성 유형** 이 **XML 구성 파일**로 설정되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-131">On the **Select Configuration Type** page, verify that the **Configuration type** is set to **XML configuration file**.</span></span>  
  
8.  <span data-ttu-id="465a1-132">**구성 유형 선택** 페이지에서 **찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-132">On the **Select Configuration Type** page, click **Browse**.</span></span>  
  
9. <span data-ttu-id="465a1-133">기본적으로 **구성 파일 위치 선택** 대화 상자가 프로젝트 폴더에 대해 열립니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-133">By default, the **Select Configuration File Location** dialog box will open to the project folder.</span></span>  
  
10. <span data-ttu-id="465a1-134">**구성 파일 위치 선택** 대화 상자에서 **파일 이름** 에 **SSISTutorial**을 입력한 다음 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-134">In the **Select Configuration File Location** dialog box, for **File name** type **SSISTutorial**, and then click **Save**.</span></span>  
  
11. <span data-ttu-id="465a1-135">**구성 유형 선택** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-135">On the **Select Configuration Type** page, click **Next.**</span></span>  
  
12. <span data-ttu-id="465a1-136">**내보낼 속성 선택** 페이지의 **개체** 창에서 **변수**, **varFolderName**, **Properties**를 차례로 확장한 다음 **값**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-136">On the **Select Properties to Export** page, in the **Objects** pane, expand **Variables**, expand **varFolderName**, expand **Properties**, and then select **Value**.</span></span>  
  
13. <span data-ttu-id="465a1-137">**내보낼 속성 선택** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-137">On the **Select Properties to Export** page, click **Next**.</span></span>  
  
14. <span data-ttu-id="465a1-138">**마법사 완료** 페이지에서 **SSIS Tutorial Directory configuration**등의 구성 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-138">On the **Completing the Wizard** page, type a configuration name for the configuration, such as **SSIS Tutorial Directory configuration**.</span></span> <span data-ttu-id="465a1-139">이 구성 이름은 **패키지 구성 도우미** 대화 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-139">This is the configuration name that is displayed in the **Package Configuration Organizer** dialog box.</span></span>  
  
15. <span data-ttu-id="465a1-140">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-140">Click **Finish**.</span></span>  
  
16. <span data-ttu-id="465a1-141">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-141">Click **Close**.</span></span>  
  
17. <span data-ttu-id="465a1-142">마법사에서 `value` `Directory` 열거자의 속성을 설정 하는 변수의에 대 한 구성 설정을 포함 하는 ssistutorial 입력 라는 구성 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-142">The wizard creates a configuration file, named SSISTutorial.dtsConfig, that contains configuration settings for the `value` of the variable that in turn sets the `Directory` property of the enumerator.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="465a1-143">일반적으로 구성 파일에는 패키지 속성에 대한 복잡한 정보가 있지만 이 자습서에서는 구성 정보만 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-143">A configuration file typically contains complex information about the package properties, but for this tutorial the only configuration information should be</span></span>  
    > <span data-ttu-id="465a1-144"><Configuration ConfiguredType="Property"</span><span class="sxs-lookup"><span data-stu-id="465a1-144"><Configuration ConfiguredType="Property"</span></span>  
    > <span data-ttu-id="465a1-145">Path = "\Package.Variables [User:: varFolderName]. 속성 [Value] "ValueType =" String "\></span><span class="sxs-lookup"><span data-stu-id="465a1-145">Path="\Package.Variables[User::varFolderName].Properties[Value]" ValueType="String"\></span></span>  
    >  \<ConfiguredValue>\</ConfiguredValue>  
    > <span data-ttu-id="465a1-146">\</Configuration>.</span><span class="sxs-lookup"><span data-stu-id="465a1-146">\</Configuration>.</span></span>  
  
### <a name="to-create-and-populate-a-new-sample-data-folder"></a><span data-ttu-id="465a1-147">새 예제 데이터 폴더를 만들고 채우려면</span><span class="sxs-lookup"><span data-stu-id="465a1-147">To create and populate a new sample data folder</span></span>  
  
1.  <span data-ttu-id="465a1-148">Windows 탐색기의 드라이브 루트 수준 (예: C: \\ )에서 라는 새 폴더를 만듭니다 `New Sample Data` .</span><span class="sxs-lookup"><span data-stu-id="465a1-148">In Windows Explorer, at the root level of your drive (for example, C:\\), create a new folder named `New Sample Data`.</span></span>  
  
2.  <span data-ttu-id="465a1-149">컴퓨터에서 예제 파일을 찾아 폴더에서 3개의 파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-149">Locate the sample files on your computer and copy three of the files from the folder.</span></span>  
  
3.  <span data-ttu-id="465a1-150">폴더에 `New Sample Data` 복사한 파일을 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="465a1-150">In the `New Sample Data` folder, paste the copied files.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="465a1-151">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="465a1-151">Next Task in Lesson</span></span>  
 [<span data-ttu-id="465a1-152">3단계: Directory 속성 구성 값 수정</span><span class="sxs-lookup"><span data-stu-id="465a1-152">Step 3: Modifying the Directory Property Configuration Value</span></span>](lesson-5-3-modifying-the-directory-property-configuration-value.md)  
  
  
