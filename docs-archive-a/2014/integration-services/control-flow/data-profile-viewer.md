---
title: 데이터 프로필 뷰어 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profile Viewer [Integration Services]
- Data Profiling task [Integration Services], output viewer
ms.assetid: b9043428-ce26-45bb-910c-588d07579565
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e82aae19525625d966bdd01334eca07a1c4c68f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651848"
---
# <a name="data-profile-viewer"></a><span data-ttu-id="8eeb7-102">데이터 프로필 뷰어(Data Profile Viewer)</span><span class="sxs-lookup"><span data-stu-id="8eeb7-102">Data Profile Viewer</span></span>
  <span data-ttu-id="8eeb7-103">데이터 프로파일링 프로세스의 다음 단계는 데이터 프로필을 보고 분석하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-103">Viewing and analyzing the data profiles is the next step in the data profiling process.</span></span> <span data-ttu-id="8eeb7-104">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지 내에서 데이터 프로파일링 태스크를 실행하고 데이터 프로필을 계산한 후에 이러한 프로필을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-104">You can view these profiles after you have run the Data Profiling task inside an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package and computed the data profiles.</span></span> <span data-ttu-id="8eeb7-105">데이터 프로파일링 태스크를 설정하고 실행하는 방법은 [데이터 프로파일링 태스크 설정](data-profiling-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-105">For more information about how to set up and run the Data Profiling tasks, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8eeb7-106">출력 파일에는 데이터베이스와 해당 데이터베이스에 포함된 데이터에 대한 중요 데이터가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-106">The output file might contain sensitive data about your database and the data that database contains.</span></span> <span data-ttu-id="8eeb7-107">이 파일을 보다 안전하게 보호하는 방법에 대한 제안 사항은 [패키지에서 사용되는 파일 액세스](../access-to-files-used-by-packages.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-107">For suggestions on how to make this file more secure, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
## <a name="data-profiles"></a><span data-ttu-id="8eeb7-108">데이터 프로필</span><span class="sxs-lookup"><span data-stu-id="8eeb7-108">Data Profiles</span></span>  
 <span data-ttu-id="8eeb7-109">데이터 프로필을 보려면 데이터 프로파일링 태스크를 구성하여 해당 출력을 파일로 보낸 다음 독립 실행형 데이터 프로필 뷰어를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-109">To view the data profiles, you configure the Data Profiling task to send its output to a file, and then you use the stand-alone Data Profile Viewer.</span></span> <span data-ttu-id="8eeb7-110">데이터 프로필 뷰어를 열려면 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-110">To open the Data Profile Viewer, do one of the following.</span></span>  
  
-   <span data-ttu-id="8eeb7-111">**디자이너에서** 데이터 프로파일링 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 태스크를 마우스 오른쪽 단추로 클릭하고 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-111">Right-click the **Data Profiling** task in the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, and then click **Edit**.</span></span> <span data-ttu-id="8eeb7-112">**데이터 프로파일링 태스크 편집기** 의 **일반** 페이지에서 **프로필 뷰어 열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-112">Click **Open Profile Viewer** on the **General** page of the **Data Profiling Task Editor**.</span></span>  
  
-   <span data-ttu-id="8eeb7-113">*\<drive>* :\Program Files (x86) | Program Files\Microsoft SQL Server\110\DTS\Binn 폴더에서 DataProfileViewer.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-113">In the folder, *\<drive>*:\Program Files (x86) | Program Files\Microsoft SQL Server\110\DTS\Binn, run DataProfileViewer.exe.</span></span>  
  
 <span data-ttu-id="8eeb7-114">이 뷰어는 여러 창을 사용하여 선택적 세부 정보 및 드릴다운 기능과 함께 요청한 프로필과 계산된 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-114">The viewer uses multiple panes to display the profiles that you requested and the computed results, with optional details and drilldown capability:</span></span>  
  
 <span data-ttu-id="8eeb7-115">**프로필** 창</span><span class="sxs-lookup"><span data-stu-id="8eeb7-115">**Profiles** pane</span></span>  
 <span data-ttu-id="8eeb7-116">**프로필** 창에는 데이터 프로필 태스크에서 요청된 프로필이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-116">The **Profiles** pane displays the profiles that were requested in the Data Profile task.</span></span> <span data-ttu-id="8eeb7-117">프로필의 계산된 결과를 보려면 **프로필** 창에서 프로필을 선택합니다. 그러면 결과가 뷰어의 다른 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-117">To view the computed results for the profile, select the profile in the **Profiles** pane and the results will appear in the other panes of the viewer.</span></span>  
  
 <span data-ttu-id="8eeb7-118">**결과** 창</span><span class="sxs-lookup"><span data-stu-id="8eeb7-118">**Results** pane</span></span>  
 <span data-ttu-id="8eeb7-119">**결과** 창에는 단일 행을 통해 프로필의 계산된 결과가 요약됩니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-119">The **Results** pane uses a single row to summarize the computed results of the profile.</span></span> <span data-ttu-id="8eeb7-120">예를 들어 **열 길이 분포 프로필**을 요청하면 이 행에 최소 및 최대 길이와 행 수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-120">For example, if you request a **Column Length Distribution Profile**, this row includes the minimum and maximum length, and the row count.</span></span> <span data-ttu-id="8eeb7-121">대부분의 프로필에 대해 **결과** 창에서 이 행을 선택하여 선택적 **세부 정보** 창에서 추가 세부 정보를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-121">For most profiles, you can select this row in the **Results** pane to see additional detail in the optional **Details** pane.</span></span>  
  
 <span data-ttu-id="8eeb7-122">**세부 정보** 창</span><span class="sxs-lookup"><span data-stu-id="8eeb7-122">**Details** pane</span></span>  
 <span data-ttu-id="8eeb7-123">대부분의 프로필 유형에 대해 **세부 정보** 창에는 **결과** 창에서 선택한 프로필 결과에 대한 추가 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-123">For most profile types, the **Details** pane displays additional information about the profile results selected in the **Results** pane.</span></span> <span data-ttu-id="8eeb7-124">예를 들어 **열 길이 분포 프로필**을 요청하면 **세부 정보** 창에 발견된 각 열 길이가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-124">For example, if you request a **Column Length Distribution Profile**, the **Details** pane displays each column length that was found.</span></span> <span data-ttu-id="8eeb7-125">또한 이 창에는 열 값에 해당 열 길이가 지정된 행의 개수 및 비율이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-125">The pane also displays the number and percentage of rows in which the column value has that column length.</span></span>  
  
 <span data-ttu-id="8eeb7-126">둘 이상의 열에 대해 계산되는 세 개의 프로필 유형(후보 키, 함수 종속성 및 값 포함)이 있을 경우 **세부 정보** 창에는 예상 관계 위반이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-126">For the three profile types that are computed against more than one column (Candidate Key, Functional Dependency, and Value Inclusion), the **Details** pane displays violations of the expected relationship.</span></span> <span data-ttu-id="8eeb7-127">예를 들어 후보 키 프로필을 요청하면 세부 정보 창에 후보 키의 고유성을 위반하는 중복 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-127">For example, if you request a Candidate Key Profile, the Details pane displays duplicate values that violate the uniqueness of the candidate key.</span></span>  
  
 <span data-ttu-id="8eeb7-128">프로필을 컴퓨팅하는 데 사용된 데이터 원본을 사용할 수 있는 경우 **세부 정보** 창에서 행을 두 번 클릭하여 **드릴다운** 창에서 일치하는 데이터 행을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-128">If the data source that is used to compute the profile is available, you can double-click a row in the **Details** pane to see the matching rows of data in the **Drilldown** pane.</span></span>  
  
 <span data-ttu-id="8eeb7-129">**드릴다운** 창</span><span class="sxs-lookup"><span data-stu-id="8eeb7-129">**Drilldown** pane</span></span>  
 <span data-ttu-id="8eeb7-130">다음 조건에 해당하는 경우 **세부 정보** 창에서 행을 두 번 클릭하여 **드릴다운** 창에서 일치하는 데이터 행을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-130">You can double-click a row in the **Details** pane to see the matching rows of data in the **Drilldown** pane when the following conditions are true:</span></span>  
  
-   <span data-ttu-id="8eeb7-131">프로필을 컴퓨팅하는 데 사용되는 데이터 원본을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-131">The data source that is used to compute the profile is available.</span></span>  
  
-   <span data-ttu-id="8eeb7-132">데이터를 볼 수 있는 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-132">You have permission to view the data.</span></span>  
  
 <span data-ttu-id="8eeb7-133">데이터 프로필 뷰어에서는 드릴다운 요청에 대한 원본 데이터베이스에 연결하기 위해 Windows 인증과 현재 사용자의 자격 증명을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-133">To connect to the source database for a drilldown request, the Data Profile Viewer uses Windows Authentication and the credentials of the current user.</span></span> <span data-ttu-id="8eeb7-134">데이터 프로필 뷰어에서는 데이터 프로파일링 태스크를 실행한 패키지에 저장된 연결 정보를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-134">The Data Profile Viewer does not use the connection information that is stored in the package that ran the Data Profiling task.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8eeb7-135">데이터 프로필 뷰어에서 사용할 수 있는 드릴다운 기능은 원래 데이터 원본에 라이브 쿼리를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-135">The drilldown capability that is available in the Data Profile Viewer sends live queries to the original data source.</span></span> <span data-ttu-id="8eeb7-136">이러한 쿼리를 사용하면 서버 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-136">These queries may have a negative impact on the performance of the server.</span></span>  
>   
>  <span data-ttu-id="8eeb7-137">최근에 만들어지지 않은 출력 파일에서 드릴다운하는 경우 드릴다운 쿼리에서 원래 출력이 계산된 행 집합과 다른 행 집합을 반환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-137">If you drill down from an output file that was not created recently, the drilldown queries might return a different set of rows than those on which the original output was calculated.</span></span>  
  
 <span data-ttu-id="8eeb7-138">데이터 프로필 뷰어의 사용자 인터페이스에 대한 자세한 내용은 [Data Profile Viewer F1 Help](../data-profile-viewer-f1-help.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-138">For more information about the user interface of the Data Profile Viewer, see [Data Profile Viewer F1 Help](../data-profile-viewer-f1-help.md).</span></span>  
  
  
