---
title: 보고서 프로젝트에 새 보고서 또는 기존 보고서 추가(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], creating
ms.assetid: 8bc0bb53-ad8a-464d-bb6a-7fea5fa62c5c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b66bf8ef0181b549900d984d20b1279f9b5005c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737918"
---
# <a name="add-a-new-or-existing-report-to-a-report-project-ssrs"></a><span data-ttu-id="3d76a-102">보고서 프로젝트에 새 보고서 또는 기존 보고서 추가(SSRS)</span><span class="sxs-lookup"><span data-stu-id="3d76a-102">Add a New or Existing Report to a Report Project (SSRS)</span></span>
  <span data-ttu-id="3d76a-103">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 보고서 마법사를 사용하거나 프로젝트에 새 보고서를 추가하여 새 보고서를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-103">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you can add a new report by using the Report Wizard or by adding a new blank report to your project.</span></span> <span data-ttu-id="3d76a-104">기본 보고서를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-104">You can also add an existing report.</span></span> <span data-ttu-id="3d76a-105">보고서를 추가한 후 프로젝트의 **보고서** 폴더 아래에 나열된 보고서 이름을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-105">After you add a report, you can see the report name listed under the **Reports** folder in your project.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3d76a-106">기존 데이터 원본의 보고서를 미리 보려면 보고서 제작 클라이언트의 데이터 원본에 대한 사용 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-106">To preview a report with existing data sources, you must have permissions to the data source from your report authoring client.</span></span> <span data-ttu-id="3d76a-107">자세한 내용은 [SSRS&#41;&#40;포함 된 데이터 원본 또는 공유 데이터 원본 만들기 ](../create-an-embedded-or-shared-data-source-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3d76a-107">For more information, see [Create an Embedded or Shared Data Source &#40;SSRS&#41;](../create-an-embedded-or-shared-data-source-ssrs.md).</span></span>  
  
 <span data-ttu-id="3d76a-108">보고서를 추가한 후 데이터 원본 및 데이터 세트를 정의하고 보고서 레이아웃을 디자인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-108">After you add a report, you can define data sources, datasets, and design a report layout.</span></span> <span data-ttu-id="3d76a-109">시작하려면 [기본 테이블 보고서 만들기&#40;SSRS 자습서&#41;](../create-a-basic-table-report-ssrs-tutorial.md) 또는 [테이블&#40;보고서 작성기 및 SSRS&#41;](../report-design/tables-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3d76a-109">To get started, see [Create a Basic Table Report &#40;SSRS Tutorial&#41;](../create-a-basic-table-report-ssrs-tutorial.md) or [Tables &#40;Report Builder  and SSRS&#41;](../report-design/tables-report-builder-and-ssrs.md).</span></span>  
  
### <a name="to-add-a-new-report-using-the-report-wizard"></a><span data-ttu-id="3d76a-110">보고서 마법사를 사용하여 새 보고서를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="3d76a-110">To add a new report using the Report Wizard</span></span>  
  
1.  <span data-ttu-id="3d76a-111">솔루션 탐색기에서 보고서 폴더를 마우스 오른쪽 단추로 클릭한 다음 **새 보고서 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-111">In Solution Explorer, right-click the Reports folder, and then click **Add New Report**.</span></span> <span data-ttu-id="3d76a-112">**보고서 마법사** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-112">The **Report Wizard** dialog box opens.</span></span>  
  
     <span data-ttu-id="3d76a-113">마법사는 데이터 원본을 만들고, 쿼리를 사용하여 데이터 세트를 만들고, 그룹을 정의하고, 레이아웃을 지정하고, 색 및 글꼴을 포함하는 스타일을 선택하고, 보고서를 만드는 단계를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-113">The wizard steps you through creating a data source, creating a dataset with a query, defining groups, specifying a layout, choosing a style that includes color and font, and creating the report.</span></span> <span data-ttu-id="3d76a-114">단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-114">The steps include:</span></span>  
  
    -   <span data-ttu-id="3d76a-115">**데이터 원본 선택.**</span><span class="sxs-lookup"><span data-stu-id="3d76a-115">**Select a Data Source.**</span></span> <span data-ttu-id="3d76a-116">보고서를 만드는 첫 번째 단계로 데이터 원본을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-116">The first step in creating a report is to define a data source.</span></span> <span data-ttu-id="3d76a-117">보고서 마법사는 보고서 프로젝트의 전체 공유 데이터 원본 목록뿐만 아니라 새 데이터 원본을 만드는 옵션도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-117">Report Wizard provides a list of all shared data sources in the report project, in addition to an option to create a new data source.</span></span>  
  
    -   <span data-ttu-id="3d76a-118">**쿼리 디자인.**</span><span class="sxs-lookup"><span data-stu-id="3d76a-118">**Design a Query.**</span></span> <span data-ttu-id="3d76a-119">두 번째 단계로 쿼리를 디자인합니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-119">The next step is to design a query.</span></span> <span data-ttu-id="3d76a-120">쿼리 문자열을 직접 입력하거나 쿼리 디자이너를 사용하여 작성하거나 다른 보고서에서 쿼리를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-120">You can type the query string, build it using Query Designer, or import a query from another report.</span></span> <span data-ttu-id="3d76a-121">쿼리 디자이너에 대한 자세한 내용은 [Reporting Services Query Designers](../reporting-services-query-designers.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3d76a-121">For information about Query Designers, see [Reporting Services Query Designers](../reporting-services-query-designers.md).</span></span>  
  
    -   <span data-ttu-id="3d76a-122">**보고서 유형 선택.**</span><span class="sxs-lookup"><span data-stu-id="3d76a-122">**Choose a Report Type.**</span></span> <span data-ttu-id="3d76a-123">세 번째 단계로 원하는 보고서 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-123">The next step is to select the type of report you want.</span></span> <span data-ttu-id="3d76a-124">테이블 형식 보고서나 행렬 보고서를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-124">You can choose a tabular or matrix report.</span></span> <span data-ttu-id="3d76a-125">테이블 형식 보고서의 열 수는 고정되어 있지만</span><span class="sxs-lookup"><span data-stu-id="3d76a-125">A tabular report has a fixed number of columns.</span></span> <span data-ttu-id="3d76a-126">행렬, 즉 크로스탭 보고서는 쿼리 결과에 따라 열 수가 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-126">A matrix, or crosstab, report has a variable number of columns based on the results of the query.</span></span> <span data-ttu-id="3d76a-127">지도 보고서에는 지리적 배경과 함께 분석 데이터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-127">A map report displays analytical against a geographic background.</span></span>  
  
    -   <span data-ttu-id="3d76a-128">**스타일을 선택 합니다.**</span><span class="sxs-lookup"><span data-stu-id="3d76a-128">**Choose a Style.**</span></span> <span data-ttu-id="3d76a-129">다음 단계로 스타일 템플릿을 사용하여 보고서에 스타일을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-129">The next step is to apply a style to the report using a style template.</span></span> <span data-ttu-id="3d76a-130">템플릿을 선택하여 글꼴, 색, 테두리 스타일 등의 스타일을 보고서에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-130">Select a template to apply styles such as font, color, and border style to the report.</span></span> <span data-ttu-id="3d76a-131">보고서 디자이너에서는 Slate, Forest, Corporate, Bold, Ocean 및 Generic 등 여섯 가지 스타일 템플릿을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-131">Report Designer provides six style templates: Slate, Forest, Corporate, Bold, Ocean, and Generic.</span></span> <span data-ttu-id="3d76a-132">다른 스타일 템플릿을 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-132">You can also add additional style templates.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="3d76a-133">Files\Microsoft Visual Studio 10.0 \ Common7\IDE\PrivateAssemblies\Business Intelligence Wizards\Reports\Styles<lang 폴더에서 StyleTemplates.xml 파일을 편집 하 여 기존 템플릿을 변경 하거나 새 템플릿을 추가할 수 있습니다 \\ \> \<lang> . 여기서은 사용 하는 언어입니다. 예를 들어 영어 버전의를 사용 하는 경우 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 폴더 이름은 "EN"입니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-133">You can alter existing templates or add new ones by editing the StyleTemplates.xml file in the \Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\Business Intelligence Wizards\Reports\Styles\\<lang\> folder, where \<lang> is the language you are using (for example, if you are using the English language version of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], the folder name is "EN").</span></span> <span data-ttu-id="3d76a-134">이 폴더는 보고서 디자이너가 설치된 컴퓨터에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-134">This folder is located on the computer on which Report Designer is installed.</span></span> <span data-ttu-id="3d76a-135">StyleTemplates.xml 파일에는 두 개의 복사본이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-135">There are two copies of the StyleTemplates.xml file.</span></span> <span data-ttu-id="3d76a-136">보고서 마법사를 통해 적용되는 스타일을 수정하려면 사용하는 언어에 대해 생성된 폴더에 있는 파일을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-136">To modify the styles that are applied through the Report Wizard, edit the file that is in the folder created for the language you are using.</span></span>  
  
    -   <span data-ttu-id="3d76a-137">**보고서 이름을 지정합니다.**</span><span class="sxs-lookup"><span data-stu-id="3d76a-137">**Name the Report.**</span></span>  <span data-ttu-id="3d76a-138">마지막 단계로 보고서의 이름을 지정하고 보고서에 포함할 필드를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-138">The final step is to name the report and verify the fields that will be included in the report.</span></span> <span data-ttu-id="3d76a-139">모든 단계가 완료되면 보고서 디자이너는 보고서를 만들어 보고서 서버 프로젝트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-139">When all steps are completed, Report Designer creates the report and adds it to the report server project.</span></span>  
  
### <a name="to-add-a-new-blank-report"></a><span data-ttu-id="3d76a-140">새 보고서를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="3d76a-140">To add a new blank report</span></span>  
  
1.  <span data-ttu-id="3d76a-141">**프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-141">From the **Project** menu, click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="3d76a-142">**템플릿**에서 **보고서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-142">In **Templates**, click **Report**.</span></span>  
  
3.  <span data-ttu-id="3d76a-143">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-143">Click **Add**.</span></span>  
  
     <span data-ttu-id="3d76a-144">새 보고서가 프로젝트에 추가되어 디자인 화면에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-144">A new blank report is added to the project and displayed on the design surface.</span></span>  
  
### <a name="to-add-an-existing-report"></a><span data-ttu-id="3d76a-145">기존 보고서를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="3d76a-145">To add an existing report</span></span>  
  
1.  <span data-ttu-id="3d76a-146">**프로젝트** 메뉴에서 **추가**를 클릭 한 다음 **기존 항목**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-146">From the **Project** menu, click **Add**, and then **Existing Item**.</span></span>  
  
2.  <span data-ttu-id="3d76a-147">.rdl 파일의 위치를 찾아서 파일을 선택한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-147">Navigate to the location of the .rdl file, select it, and then click **Add**.</span></span>  
  
     <span data-ttu-id="3d76a-148">보고서가 **보고서** 폴더 아래의 프로젝트에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-148">The report is added to the project under the **Reports** folder.</span></span> <span data-ttu-id="3d76a-149">프로젝트를 닫고 다시 열면 보고서가 사전순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d76a-149">When you close and re-open the project, reports are sorted alphabetically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d76a-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3d76a-150">See Also</span></span>  
 [<span data-ttu-id="3d76a-151">Reporting Services&#40;SSRS&#41; 자습서</span><span class="sxs-lookup"><span data-stu-id="3d76a-151">Reporting Services Tutorials &#40;SSRS&#41;</span></span>](../reporting-services-tutorials-ssrs.md)  
  
  
