---
title: PowerPivot에서 가져오기 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.importfromppt.f1
ms.assetid: ac1a6a79-bda3-4122-a717-8b1e2f77da02
author: minewiskan
ms.author: owend
ms.openlocfilehash: 581259d79e5d84bd558ca3f13519fbf4dc0ba52f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728816"
---
# <a name="import-from-powerpivot-ssas-tabular"></a><span data-ttu-id="34ca6-102">PowerPivot에서 가져오기(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="34ca6-102">Import from PowerPivot (SSAS Tabular)</span></span>
  <span data-ttu-id="34ca6-103">이 항목에서는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 PowerPivot에서 가져오기 프로젝트 템플릿을 사용하여 PowerPivot 통합 문서에서 메타데이터와 데이터를 가져와서 새로운 테이블 형식 모델 프로젝트를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="34ca6-103">This topic describes how to create a new tabular model project by importing the metadata and data from a PowerPivot workbook by using the Import from PowerPivot project template in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="create-a-new-tabular-model-from-a-powerpivot-for-excel-file"></a><span data-ttu-id="34ca6-104">Excel 파일용 Powerpivot에서 새 테이블 형식 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="34ca6-104">Create a new Tabular Model from a PowerPivot for Excel file</span></span>  
 <span data-ttu-id="34ca6-105">PowerPivot 통합 문서에서 가져와서 새로운 테이블 형식 모델 프로젝트를 만드는 경우 통합 문서의 구조를 정의하는 메타데이터를 사용하여 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 테이블 형식 모델 프로젝트의 구조를 만들고 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="34ca6-105">When creating a new tabular model project by importing from a PowerPivot workbook, the metadata that defines the structure of the workbook is used to create and define the structure of the tabular model project in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="34ca6-106">테이블, 열, 측정값 및 관계와 같은 개체는 그대로 유지되며 PowerPivot 통합 문서에 표시되는 것과 똑같이 테이블 형식 모델 프로젝트에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="34ca6-106">Objects such as tables, columns, measures, and relationships are retained and will appear in the tabular model project as they are in the PowerPivot workbook.</span></span> <span data-ttu-id="34ca6-107">.xlsx 통합 문서 파일은 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34ca6-107">No changes are made to the .xlsx workbook file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="34ca6-108">테이블 형식 모델은 연결된 테이블을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34ca6-108">Tabular models do not support linked tables.</span></span> <span data-ttu-id="34ca6-109">연결된 테이블이 포함된 PowerPivot 통합 문서에서 가져오는 경우 연결된 테이블 데이터는 복사/붙여 넣은 데이터로 처리되며 Model.bim 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="34ca6-109">When importing from a PowerPivot workbook that contains a linked table, linked table data is treated as copy\pasted data and stored in the Model.bim file.</span></span> <span data-ttu-id="34ca6-110">복사하여 붙여넣은 테이블의 속성을 볼 때 **원본 데이터** 속성은 비활성화되고 **테이블** 메뉴의 **테이블 속성** 대화 상자도 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="34ca6-110">When viewing properties for a copy\pasted table, the **Source Data** property is disabled and the **Table Properties** dialog on the **Table** menu is disabled.</span></span>  
>   
>  <span data-ttu-id="34ca6-111">모델에 포함된 데이터에 추가할 수 있는 행은 최대 10,000개로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="34ca6-111">There is a limit of 10,000 rows that can be added to the data embedded in the model.</span></span> <span data-ttu-id="34ca6-112">PowerPivot에서 모델을 가져오는 경우 "데이터가 잘렸습니다.</span><span class="sxs-lookup"><span data-stu-id="34ca6-112">If you import a model from PowerPivot and see the error, "Data was truncated.</span></span> <span data-ttu-id="34ca6-113">붙여넣은 테이블은 1만 개 이상의 행을 포함할 수 없습니다. "에 포함 된 데이터를 SQL Server의 테이블과 같은 다른 데이터 원본으로 이동한 다음 다시 가져오는 방법으로 PowerPivot 모델을 수정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ca6-113">Pasted tables cannot contain more than 10000 rows" you should revise the PowerPivot model by moving the embedded data into another data source, such as a table in SQL Server, and then re-import.</span></span>  
  
 <span data-ttu-id="34ca6-114">작업 영역 데이터베이스가 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 와 동일한 컴퓨터(로컬)의 Analysis Services 인스턴스에 있는지, 아니면 원격 Analysis Services 인스턴스에 있는지에 따라 특별히 고려해야 할 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34ca6-114">There are special considerations depending on whether or not the workspace database is on an Analysis Services instance on the same computer (local) as [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or is on a remote Analysis Services instance..</span></span>  
  
 <span data-ttu-id="34ca6-115">작업 영역 데이터베이스가 Analysis Services의 로컬 인스턴스에 있는 경우 PowerPivot 통합 문서에서 메타데이터와 데이터를 모두 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34ca6-115">If the workspace database is on a local instance of Analysis Services, you can import both the metadata and data from the PowerPivot workbook.</span></span> <span data-ttu-id="34ca6-116">메타데이터는 통합 문서에서 복사되고 테이블 형식 모델 프로젝트를 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="34ca6-116">The metadata is copied from the workbook and used to create the tabular model project.</span></span> <span data-ttu-id="34ca6-117">그런 다음 데이터는 통합 문서에서 복사 되 고 프로젝트의 작업 영역 데이터베이스에 저장 됩니다 (복사/붙여 넣은 데이터를 제외 하 고 model.bim 파일에 저장 됨).</span><span class="sxs-lookup"><span data-stu-id="34ca6-117">The data is then copied from the workbook and stored in the project's workspace database (except for copy/pasted data, which is stored in the Model.bim file).</span></span>  
  
 <span data-ttu-id="34ca6-118">작업 영역 데이터베이스가 원격 Analysis Services 인스턴스에 있는 경우 PowerPivot for Excel 통합 문서에서 데이터를 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34ca6-118">If the workspace database is on a remote Analysis Services instance, you cannot import data from a PowerPivot for Excel workbook.</span></span> <span data-ttu-id="34ca6-119">통합 문서 메타데이터를 여전히 가져올 수 있지만 이렇게 하면 스크립트가 원격 Analysis Services 인스턴스에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="34ca6-119">You can still import the workbook metadata; however, this will cause a script to be run on the remote Analysis Services instance.</span></span> <span data-ttu-id="34ca6-120">신뢰할 수 있는 PowerPivot 통합 문서에서만 메타데이터를 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ca6-120">You should only import metadata from a trusted PowerPivot workbook.</span></span> <span data-ttu-id="34ca6-121">데이터 원본 연결에 정의된 원본에서 데이터를 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ca6-121">Data must be imported from sources defined in the data source connections.</span></span> <span data-ttu-id="34ca6-122">PowerPivot 통합 문서의 복사/붙여 넣은 테이블 데이터와 연결된 테이블 데이터를 복사하여 테이블 형식 모델 프로젝트에 붙여 넣어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ca6-122">Copy/pasted and linked table data in the PowerPivot workbook must be copied and pasted into the tabular model project.</span></span>  
  
#### <a name="to-create-a-new-tabular-model-project-from-a-powerpivot-for-excel-file"></a><span data-ttu-id="34ca6-123">PowerPivot for Excel 파일에서 새 테이블 형식 모델 프로젝트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="34ca6-123">To create a new tabular model project from a PowerPivot for Excel file</span></span>  
  
1.  <span data-ttu-id="34ca6-124">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]의 **파일** 메뉴에서 **새로 만들기**를 클릭한 다음 **프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34ca6-124">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], on the **File** menu, click **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="34ca6-125">**새 프로젝트** 대화 상자의 **설치 된 템플릿**에서 **비즈니스 인텔리전스**를 클릭 한 다음 **PowerPivot에서 가져오기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ca6-125">In the **New Project** dialog box, under **Installed Templates**, click **Business Intelligence**, and then click **Import from PowerPivot**.</span></span>  
  
3.  <span data-ttu-id="34ca6-126">**이름**에 프로젝트의 이름을 입력 하 고 위치 및 솔루션 이름을 지정한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ca6-126">In  **Name**, type a name for the project, then specify a location and solution name, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="34ca6-127">**열기** 대화 상자에서 가져올 모델 메타데이터 및 데이터가 포함된 [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] 파일을 선택한 다음 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34ca6-127">In the **Open** dialog box, select the [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] file that contains the model metadata and data you want to import, and then click **Open**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34ca6-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="34ca6-128">See Also</span></span>  
 <span data-ttu-id="34ca6-129">[SSAS 테이블 형식&#41;&#40;작업 영역 데이터베이스](workspace-database-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="34ca6-129">[Workspace Database &#40;SSAS Tabular&#41;](workspace-database-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="34ca6-130">데이터 복사 및 붙여넣기&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="34ca6-130">Copy and Paste Data &#40;SSAS Tabular&#41;</span></span>](../copy-and-paste-data-ssas-tabular.md)  
  
  
