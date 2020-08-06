---
title: 테이블 형식 모델 디자이너 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- SQL12.ASVS.BIDTOOLSET.TOPLEVSEMMODUIENTRY.F1
ms.assetid: 45735c57-2a95-4e45-8994-7242df6c9c5f
author: minewiskan
ms.author: owend
ms.openlocfilehash: ac63826d3e8a93f341c181faeef44714afd92353
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649241"
---
# <a name="tabular-model-designer-ssas-tabular"></a><span data-ttu-id="885a9-102">테이블 형식 모델 디자이너(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="885a9-102">Tabular Model Designer (SSAS Tabular)</span></span>
  <span data-ttu-id="885a9-103">테이블 형식 모델 디자이너는 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]의 일부로 Microsoft [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 2010 이상 환경과 통합되어 있으며, 전문적인 테이블 형식의 모델 솔루션을 개발하기 위한 추가 프로젝트 형식 템플릿이 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-103">The tabular model designer is part of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], integrated with Microsoft [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 2010 or later, with additional project type templates specifically for developing professional tabular model solutions.</span></span>  
  
 <span data-ttu-id="885a9-104">이 항목의 섹션:</span><span class="sxs-lookup"><span data-stu-id="885a9-104">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="885a9-105">이점</span><span class="sxs-lookup"><span data-stu-id="885a9-105">Benefits</span></span>](#bkmk_benefits)  
  
-   [<span data-ttu-id="885a9-106">프로젝트 템플릿</span><span class="sxs-lookup"><span data-stu-id="885a9-106">Project Templates</span></span>](#bkmk_proj_temp)  
  
-   [<span data-ttu-id="885a9-107">창 및 메뉴</span><span class="sxs-lookup"><span data-stu-id="885a9-107">Windows and Menus</span></span>](#bkmk_wind_men)  
  
-   [<span data-ttu-id="885a9-108">Visual Studio 통합</span><span class="sxs-lookup"><span data-stu-id="885a9-108">Visual Studio Integration</span></span>](#bkmk_vsint)  
  
##  <a name="benefits"></a><a name="bkmk_benefits"></a> <span data-ttu-id="885a9-109">이점</span><span class="sxs-lookup"><span data-stu-id="885a9-109">Benefits</span></span>  
 <span data-ttu-id="885a9-110">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]를 설치하면 테이블 형식의 모델을 만들기 위한 새 프로젝트 템플릿이 사용 가능한 프로젝트 형식에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-110">When you install [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], new project templates for creating tabular models are added to the available project types.</span></span> <span data-ttu-id="885a9-111">이 템플릿 중 하나를 사용하여 테이블 형식의 새 모델 프로젝트를 만든 다음 테이블 형식 모델 디자이너 도구와 마법사를 사용하여 모델 제작을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-111">After creating a new tabular model project by using one of the templates, you can begin model authoring by using the tabular model designer tools and wizards.</span></span>  
  
 <span data-ttu-id="885a9-112">[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 환경에서는 전문적인 다차원 및 테이블 형식 모델 솔루션 제작을 위한 새로운 템플릿과 도구뿐만 아니라 디버깅 및 프로젝트 수명 주기 기능을 제공하여 조직에 맞는 가장 강력한 BI 솔루션을 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-112">In addition to new templates and tools for authoring professional multidimensional and tabular model solutions, the [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] environment provides debugging and project lifecycle capabilities that ensure you create the most powerful BI solutions for your organization.</span></span> <span data-ttu-id="885a9-113">[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에 대한 자세한 내용은 [Visual Studio 시작](https://go.microsoft.com/fwlink/?LinkId=206389)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="885a9-113">For more information about [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], see [Getting Started with Visual Studio](https://go.microsoft.com/fwlink/?LinkId=206389).</span></span>  
  
##  <a name="project-templates"></a><a name="bkmk_proj_temp"></a> <span data-ttu-id="885a9-114">프로젝트 템플릿</span><span class="sxs-lookup"><span data-stu-id="885a9-114">Project Templates</span></span>  
 <span data-ttu-id="885a9-115">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]를 설치하면 다음과 같은 테이블 형식 모델 프로젝트 템플릿이 비즈니스 인텔리전스 프로젝트 형식에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-115">When you install [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the following tabular model project templates are added to the Business Intelligence project types:</span></span>  
  
 <span data-ttu-id="885a9-116">**Analysis Services 테이블 형식 프로젝트**</span><span class="sxs-lookup"><span data-stu-id="885a9-116">**Analysis Services Tabular Project**</span></span>  
 <span data-ttu-id="885a9-117">이 템플릿은 비어 있는 새 테이블 형식 모델 프로젝트를 만드는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-117">This template can be used to create a new, blank tabular model project.</span></span>  
  
 <span data-ttu-id="885a9-118">**서버에서 가져오기(테이블 형식)**</span><span class="sxs-lookup"><span data-stu-id="885a9-118">**Import from Server (Tabular)**</span></span>  
 <span data-ttu-id="885a9-119">이 템플릿은 Analysis Services의 기존 테이블 형식 모델에서 메타데이터를 추출하여 새 테이블 형식 모델 프로젝트를 만드는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-119">This template can be used to create a new tabular model project by extracting the metadata from an existing tabular model in Analysis Services.</span></span>  
  
 <span data-ttu-id="885a9-120">**PowerPivot에서 가져오기**</span><span class="sxs-lookup"><span data-stu-id="885a9-120">**Import from PowerPivot**</span></span>  
 <span data-ttu-id="885a9-121">이 템플릿은 [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] 파일에서 메타데이터와 데이터를 추출하여 새 테이블 형식 모델 프로젝트를 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-121">This template is used for creating a new tabular model project by extracting the metadata and data from a [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="885a9-122">테이블 형식 모델 프로젝트를 사용하려면 테이블 형식 모드에서 Analysis Services 서버 인스턴스가 로컬로 실행되거나 네트워크에서 실행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-122">Tabular model projects require an Analysis Services server instance in tabular mode be running locally or on the network.</span></span>  
  
##  <a name="windows-and-menus"></a><a name="bkmk_wind_men"></a><span data-ttu-id="885a9-123">창 및 메뉴</span><span class="sxs-lookup"><span data-stu-id="885a9-123">Windows and Menus</span></span>  
 <span data-ttu-id="885a9-124">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 테이블 형식 모델 제작 환경에는 다음이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-124">The [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] tabular model authoring environment includes the following:</span></span>  
  
### <a name="designer-window"></a><span data-ttu-id="885a9-125">디자이너 창</span><span class="sxs-lookup"><span data-stu-id="885a9-125">Designer Window</span></span>  
 <span data-ttu-id="885a9-126">디자이너 창은 테이블 형식 모델 제작에 사용되며 모델에 대한 시각적 표현을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-126">The designer window is used to author tabular models by providing a visual representation of the model.</span></span> <span data-ttu-id="885a9-127">Model.bim 파일을 열면 디자이너 창에서 모델이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-127">When you open the Model.bim file, the model opens in the designer window.</span></span> <span data-ttu-id="885a9-128">디자이너 창에서 다음과 같은 두 가지 다른 보기 모드를 사용하여 모델을 제작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-128">You can author a model in the designer window by using two different view modes:</span></span>  
  
 <span data-ttu-id="885a9-129">**데이터 뷰**</span><span class="sxs-lookup"><span data-stu-id="885a9-129">**Data View**</span></span>  
 <span data-ttu-id="885a9-130">데이터 뷰는 테이블을 표 형식으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-130">The data view displays tables in a tabular, grid format.</span></span> <span data-ttu-id="885a9-131">데이터 뷰에서만 각 테이블에 표시할 수 있는 측정값 표를 사용하여 측정값을 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-131">You can also define measures by using the measure grid, which can be shown for each table in Data View only.</span></span>  
  
 <span data-ttu-id="885a9-132">**다이어그램 뷰**</span><span class="sxs-lookup"><span data-stu-id="885a9-132">**Diagram View**</span></span>  
 <span data-ttu-id="885a9-133">다이어그램 뷰는 테이블을 그래픽 형식의 관계도와 함께 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-133">The diagram view displays tables, with relationships between them, in a graphical format.</span></span> <span data-ttu-id="885a9-134">열, 측정값, 계층 및 KPI를 필터링할 수 있으며 정의된 큐브 뷰를 사용하여 모델을 표시하도록 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-134">Columns, measures, hierarchies, and KPIs can be filtered, and you can choose to view the model by using a defined perspective.</span></span>  
  
 <span data-ttu-id="885a9-135">대부분의 모델 제작 태스크를 이 두 가지 뷰에서 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-135">Most model authoring tasks can be performed in either view.</span></span>  
  
### <a name="solution-explorer"></a><span data-ttu-id="885a9-136">솔루션 탐색기</span><span class="sxs-lookup"><span data-stu-id="885a9-136">Solution Explorer</span></span>  
 <span data-ttu-id="885a9-137">솔루션 탐색기 창은 활성 솔루션을 테이블 형식 모델 프로젝트 및 해당 프로젝트와 관련된 항목에 대한 논리적 컨테이너로 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-137">The Solution Explorer window presents the active solution as a logical container for a tabular model project and its associated items.</span></span> <span data-ttu-id="885a9-138">모델 프로젝트(.smproj)에는 참조 개체(비어 있음)와 Model.bim 파일만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-138">The model project (.smproj) contains only a References object (empty) and the Model.bim file.</span></span> <span data-ttu-id="885a9-139">이 뷰에서 프로젝트 항목을 열어 수정하고 다른 관리 태스크를 직접 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-139">You can open project items for modification and perform other management tasks directly from this view.</span></span>  
  
 <span data-ttu-id="885a9-140">테이블 형식 모델 솔루션에는 대개 하나의 프로젝트만 포함되지만 한 솔루션에 Integration Services 또는 Reporting Services 프로젝트 등의 다른 여러 프로젝트가 포함될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-140">Tabular model solutions typically contain only one project; however, a solution can contain other projects too, for example, Integration Services or Reporting services project.</span></span> <span data-ttu-id="885a9-141">테이블 형식 모델 프로젝트 파일과 형식이 다르고 빌드 동작 속성이 없음으로 설정되거나 출력 디렉터리로 복사 속성이 복사 안 함으로 설정된 파일은 개수와 관계없이 무제한 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-141">You can add any number of files provided they are not of the same type as tabular model project files and their Build Action property is set to None, or Copy to Output property is set to Do Not Copy.</span></span>  
  
 <span data-ttu-id="885a9-142">솔루션 탐색기를 보려면 **보기** 메뉴를 클릭한 다음 **솔루션 탐색기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-142">To view Solution Explorer, click the **View** menu, and then click **Solution Explorer**.</span></span>  
  
### <a name="properties-window"></a><span data-ttu-id="885a9-143">속성 창</span><span class="sxs-lookup"><span data-stu-id="885a9-143">Properties Window</span></span>  
 <span data-ttu-id="885a9-144">속성 창은 선택된 개체의 속성을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-144">The Properties window lists the properties of the selected object.</span></span> <span data-ttu-id="885a9-145">속성 창에서 다음과 같은 개체의 속성을 보고 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-145">The following objects have properties that can be viewed and edited in the Properties window:</span></span>  
  
-   <span data-ttu-id="885a9-146">Model.bim</span><span class="sxs-lookup"><span data-stu-id="885a9-146">Model.bim</span></span>  
  
-   <span data-ttu-id="885a9-147">표</span><span class="sxs-lookup"><span data-stu-id="885a9-147">Table</span></span>  
  
-   <span data-ttu-id="885a9-148">열</span><span class="sxs-lookup"><span data-stu-id="885a9-148">Column</span></span>  
  
-   <span data-ttu-id="885a9-149">측정값</span><span class="sxs-lookup"><span data-stu-id="885a9-149">Measure</span></span>  
  
 <span data-ttu-id="885a9-150">프로젝트 속성은 속성 창에 프로젝트 이름과 프로젝트 폴더만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-150">Project Properties display only the project name and project folder in the Properties window.</span></span> <span data-ttu-id="885a9-151">프로젝트에는 또한 모달 속성 대화 상자에서 설정할 수 있는 추가 배포 옵션 및 배포 서버 설정이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-151">Projects also have additional deployment Options and deployment server settings that you can set using a modal properties dialog box.</span></span> <span data-ttu-id="885a9-152">이 속성을 보려면 **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-152">To view these properties, in **Solution Explorer**, right click the project, and then click **Properties**.</span></span>  
  
 <span data-ttu-id="885a9-153">속성 창의 필드에는 클릭하면 열리는 컨트롤이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-153">Fields in the Properties window have embedded controls that open when you click them.</span></span> <span data-ttu-id="885a9-154">편집 컨트롤 유형은 특정 속성에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-154">The type of edit control depends on the particular property.</span></span> <span data-ttu-id="885a9-155">컨트롤에는 편집 상자, 드롭다운 목록, 사용자 지정 대화 상자에 대한 링크 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-155">Controls include edit boxes, dropdown lists, and links to custom dialog boxes.</span></span> <span data-ttu-id="885a9-156">흐리게 표시되는 속성은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-156">Properties that are shown as dimmed are read-only.</span></span>  
  
 <span data-ttu-id="885a9-157">**속성** 창을 보려면 **보기** 메뉴를 클릭한 다음 **속성 창**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-157">To view the **Properties** window, click the **View** menu, and then click **Properties Window**.</span></span>  
  
### <a name="error-list"></a><span data-ttu-id="885a9-158">오류 목록</span><span class="sxs-lookup"><span data-stu-id="885a9-158">Error List</span></span>  
 <span data-ttu-id="885a9-159">오류 목록 창에는 다음과 같은 모델 상태에 대한 메시지가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-159">The Error List window contains messages about the model state:</span></span>  
  
-   <span data-ttu-id="885a9-160">최상의 권장 보안 방법에 대한 알림</span><span class="sxs-lookup"><span data-stu-id="885a9-160">Notifications about security best practices.</span></span>  
  
-   <span data-ttu-id="885a9-161">데이터 처리 요구 사항</span><span class="sxs-lookup"><span data-stu-id="885a9-161">Requirements for data processing.</span></span>  
  
-   <span data-ttu-id="885a9-162">계산 열, 측정값 및 역할 행 필터에 대한 의미 체계 오류 정보.</span><span class="sxs-lookup"><span data-stu-id="885a9-162">Semantic error information for calculated columns, measures, and row filters for roles.</span></span> <span data-ttu-id="885a9-163">계산 열에서 오류 메시지를 두 번 클릭하면 오류의 출처가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-163">For calculated columns, you can double-click the error message to navigate to the source of the error.</span></span>  
  
-   <span data-ttu-id="885a9-164">DirectQuery 유효성 검사 오류</span><span class="sxs-lookup"><span data-stu-id="885a9-164">DirectQuery validation errors.</span></span>  
  
 <span data-ttu-id="885a9-165">기본적으로 **오류 목록** 은 오류가 반환되어야만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-165">By default, the **Error List** does not appear unless an error is returned.</span></span> <span data-ttu-id="885a9-166">그러나 **오류 목록** 창은 언제든지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-166">You can, however, view the **Error List** window at any time.</span></span> <span data-ttu-id="885a9-167">**오류 목록** 창을 보려면 **보기** 메뉴를 클릭한 다음 **오류 목록**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-167">To view the **Error List** window, click the **View** menu, and then click **Error List**.</span></span>  
  
### <a name="output"></a><span data-ttu-id="885a9-168">출력</span><span class="sxs-lookup"><span data-stu-id="885a9-168">Output</span></span>  
 <span data-ttu-id="885a9-169">빌드 및 배포 정보가 **출력** 창 및 모달 진행률 대화 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-169">Build and deployment information is displayed in the **Output** Window (in addition to the modal progress dialog).</span></span> <span data-ttu-id="885a9-170">**출력** 창을 보려면 **보기** 메뉴를 클릭한 다음 출력을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-170">To view the **Output** window, click the **View** menu, and then click Output.</span></span>  
  
### <a name="menu-items"></a><span data-ttu-id="885a9-171">메뉴 항목</span><span class="sxs-lookup"><span data-stu-id="885a9-171">Menu Items</span></span>  
 <span data-ttu-id="885a9-172">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]를 설치하면 테이블 형식의 모델을 제작하는 데 사용되는 추가 메뉴 항목이 Visual Studio 메뉴 모음에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-172">When you install [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], additional menu items specifically for authoring tabular models are added to the Visual Studio menu bar.</span></span> <span data-ttu-id="885a9-173">**모델** 메뉴를 사용하여 데이터 가져오기 마법사를 시작하고, 기존 연결을 보고, 작업 영역 데이터를 처리하고, [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel에서 모델 작업 영역을 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-173">The **Model** menu can be used to launch the Data Import Wizard, view existing connections, process workspace data, and browse the model workspace in [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel.</span></span> <span data-ttu-id="885a9-174">**테이블** 메뉴를 사용하여 테이블 간의 관계를 만들고 관리하고, 측정값을 만들고 관리하며, 데이터 테이블 설정을 지정하고, 계산 옵션을 지정하고, 기타 테이블 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-174">The **Table** menu is used to create and manage relationships between tables, create and manage measures, specify data table settings, specify calculation options, and specify other table properties.</span></span> <span data-ttu-id="885a9-175">**열** 메뉴를 사용하여 테이블에서 열을 추가 및 삭제하고, 열을 숨기거나 숨기기를 취소하고, 데이터 형식 및 필터와 같은 기타 열 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-175">With the **Column** menu, you can add and delete columns in a table, hide and unhide columns, and specify other column properties such as data types and filters.</span></span> <span data-ttu-id="885a9-176">**빌드** 메뉴에서 테이블 형식 모델 솔루션을 빌드하고 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-176">You can build and deploy tabular model solutions on the **Build** menu.</span></span> <span data-ttu-id="885a9-177">복사/붙여넣기 기능은 **편집** 메뉴에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-177">Copy/Paste functions are included on the **Edit** menu.</span></span>  
  
 <span data-ttu-id="885a9-178">이러한 새 메뉴 항목 외에도 도구 메뉴 항목의 Analysis Services 옵션에 추가 설정이 추가되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-178">In addition to these menu items, additional settings are added to the Analysis Services options on the Tools menu items.</span></span>  
  
### <a name="toolbar"></a><span data-ttu-id="885a9-179">도구 모음</span><span class="sxs-lookup"><span data-stu-id="885a9-179">Toolbar</span></span>  
 <span data-ttu-id="885a9-180">Analysis Services 도구 모음을 통해 신속하고 간편하게 자주 사용하는 모델 작성 명령에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-180">The Analysis Services toolbar provides quick and easy access to the most frequently used model authoring commands.</span></span>  
  
##  <a name="visual-studio-integration"></a><a name="bkmk_vsint"></a> <span data-ttu-id="885a9-181">Visual Studio 통합</span><span class="sxs-lookup"><span data-stu-id="885a9-181">Visual Studio Integration</span></span>  
 <span data-ttu-id="885a9-182">**소스 제어**</span><span class="sxs-lookup"><span data-stu-id="885a9-182">**Source Control**</span></span>  
 <span data-ttu-id="885a9-183">Analysis Services 프로젝트는 선택한 원본 제어 플러그 인과 통합됩니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-183">Analysis Services projects integrate with the selected source control plug-in.</span></span> <span data-ttu-id="885a9-184">원본 제어를 사용하도록 Visual Studio를 구성하면 솔루션 탐색기에서 체크 인/체크 아웃을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-184">If you have configured Visual Studio to use source control, you can use check in/check out from Solution Explorer.</span></span> <span data-ttu-id="885a9-185">Team Foundation Server를 사용하도록 구성하려면 [Team Foundation 버전 제어로 Visual Studio 구성](https://msdn.microsoft.com/library/ms253064.aspx)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="885a9-185">To configure to use Team Foundation Server, see [Configure Visual Studio with Team Foundation Version Control](https://msdn.microsoft.com/library/ms253064.aspx).</span></span> <span data-ttu-id="885a9-186">그 외 다양한 타사 원본 제어 플러그 인도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-186">Many third-party source control plug-ins are supported as well.</span></span>  
  
 <span data-ttu-id="885a9-187">**글꼴**</span><span class="sxs-lookup"><span data-stu-id="885a9-187">**Fonts**</span></span>  
 <span data-ttu-id="885a9-188">테이블 형식 모델은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 환경의 글꼴을 사용하여 표시되는 글꼴을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-188">Tabular models use the [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] environment font to control the fonts in the display.</span></span> <span data-ttu-id="885a9-189">기본 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 글꼴을 사용하여 해당 언어의 유니코드 문자를 모두 표시할 수 없을 경우 이 글꼴을 변경해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-189">It can be necessary to change this font if the default [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] font does not have all of the Unicode characters you need for your language.</span></span> <span data-ttu-id="885a9-190">글꼴을 변경하려면 **도구** 메뉴를 클릭하고 **옵션**을 클릭한 다음 **글꼴 및 색**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-190">To change fonts, click the **Tools** menu, then click **Options**, and then click **Fonts and Colors**.</span></span>  
  
 <span data-ttu-id="885a9-191">**바로 가기 키**</span><span class="sxs-lookup"><span data-stu-id="885a9-191">**Keyboard Shortcuts**</span></span>  
 <span data-ttu-id="885a9-192">도구->옵션->키보드 대화 상자를 통해 Analysis Services 키보드 바로 가기를 구성하거나 다시 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-192">The Analysis Services keyboard shortcuts can be configured/remapped through the Tools->Options->Keyboard dialog.</span></span> <span data-ttu-id="885a9-193">빌드, 저장, 디버그, 새 프로젝트 등과 같은 전역 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 바로 가기가 테이블 형식 모델 디자이너 컨텍스트에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-193">Some global [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] shortcuts, such as build, save, debug, new project, etc. are supported in the tabular model designer context.</span></span> <span data-ttu-id="885a9-194">그 외 테이블 형식 모델 디자이너용 바로 가기 키는 Analysis Services 컨텍스트에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="885a9-194">Other tabular model designer specific shortcuts are in the Analysis Services context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="885a9-195">참고 항목</span><span class="sxs-lookup"><span data-stu-id="885a9-195">See Also</span></span>  
 <span data-ttu-id="885a9-196">[테이블 형식 모델 프로젝트 &#40;SSAS 테이블 형식&#41;](tabular-models/tabular-model-projects-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="885a9-196">[Tabular Model Projects &#40;SSAS Tabular&#41;](tabular-models/tabular-model-projects-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="885a9-197">속성&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="885a9-197">Properties &#40;SSAS Tabular&#41;</span></span>](tabular-models/properties-ssas-tabular.md)  
  
  
