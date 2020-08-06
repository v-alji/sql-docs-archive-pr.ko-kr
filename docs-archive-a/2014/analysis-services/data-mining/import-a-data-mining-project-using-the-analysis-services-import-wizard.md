---
title: Analysis Services 가져오기 마법사를 사용 하 여 데이터 마이닝 프로젝트 가져오기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 62bc9fc5-c6ff-4517-b598-d92df76743a2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5b39062cc5bc5401a1746f35e98ea643db2d16c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649267"
---
# <a name="import-a-data-mining-project-using-the-analysis-services-import-wizard"></a><span data-ttu-id="91cc0-102">Analysis Services 가져오기 마법사를 사용하여 데이터 마이닝 프로젝트 가져오기</span><span class="sxs-lookup"><span data-stu-id="91cc0-102">Import a Data Mining Project using the Analysis Services Import Wizard</span></span>
  <span data-ttu-id="91cc0-103">이 항목에서는 **의**서버에서 가져오기(다차원 및 데이터 마이닝) 프로젝트 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]템플릿을 사용하여 다른 서버의 기존 데이터 마이닝 프로젝트에서 메타데이터를 가져와 새로운 데이터 마이닝 프로젝트를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-103">This topic describes how to create a new data mining project by importing the metadata from an existing data mining project on another server, using the template, **Import from Server (Multidimensional and Data Mining) Project**, in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="import-data-sources-mining-structures-and-mining-models-from-an-existing-data-mining-project"></a><span data-ttu-id="91cc0-104">기존 데이터 마이닝 프로젝트에서 데이터 원본, 마이닝 구조 및 마이닝 모델 가져오기</span><span class="sxs-lookup"><span data-stu-id="91cc0-104">Import data sources, mining structures, and mining models from an existing data mining project</span></span>  
 <span data-ttu-id="91cc0-105">**서버에서 가져오기 (다차원 및 데이터 마이닝) 프로젝트**템플릿을 사용 하면에서 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 새 데이터 마이닝 프로젝트를 만든 다음 지정 된 데이터 마이닝 프로젝트에서 메타 데이터를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-105">When you use the template, **Import from Server (Multidimensional and Data Mining) Project**, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] creates a new data mining project, and then copies the metadata from the specified data mining project.</span></span> <span data-ttu-id="91cc0-106">새 프로젝트에는 가져온 ssASnoversion 데이터베이스와 동일한 데이터 원본, 데이터 원본 뷰, 마이닝 구조 및 마이닝 모델이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-106">The new project contains the same data sources, data source views, mining structures, and mining models as the ssASnoversion database that you imported from.</span></span> <span data-ttu-id="91cc0-107">그러나 프로젝트를 사용하려면 먼저 아래 설명된 대로 특정 속성을 업데이트하고 개체를 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-107">However, the project cannot be used until you have updated certain properties and processed the objects as described:</span></span>  
  
-   <span data-ttu-id="91cc0-108">데이터 자체가 원본 서버에서 새 데이터 마이닝 프로젝트로 복사 되는 것이 아니라 데이터 원본 및 데이터 원본 뷰의 정의만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-108">The data itself is not copied from the source server to the new data mining project-only the definitions of the data sources and data source views are imported.</span></span> <span data-ttu-id="91cc0-109">따라서 가져오기 프로세스가 완료되고 개체가 만들어진 후 마이닝 구조 및 종속 모델을 학습하여 개체를 데이터로 채워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-109">Therefore, after the import process has completed, and the objects have been created, you must populate the objects with data by training the mining structures and dependent models.</span></span> <span data-ttu-id="91cc0-110">데이터 마이닝 디자이너의 **모두 처리** 명령을 사용하여 모델 및 구조를 학습할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-110">You can use the command **Process All** in Data Mining Designer to train the models and structures.</span></span>  
  
-   <span data-ttu-id="91cc0-111">이전 버전의 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 만들어진 프로젝트를 가져올 경우 데이터 원본에서 프로젝트를 가져올 서버에 설치되지 않은 공급자를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-111">If you are importing a project that was created in a previous version of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the data source might use providers that are not installed on the server to which you are importing the project.</span></span> <span data-ttu-id="91cc0-112">가져온 마이닝 구조를 처리할 때 오류가 발생하면 데이터 원본을 마우스 오른쪽 단추로 클릭하고 **디자이너 열기** 를 선택하여 연결 문자열을 편집하고 공급자 속성을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-112">If you encounter errors when processing the imported mining structures, right-click each data source and select **Open Designer** to edit the connection string and review the provider properties.</span></span>  
  
     <span data-ttu-id="91cc0-113">이때 데이터 마이닝 개체를 처리하거나 데이터 마이닝 모델을 쿼리하는 데 사용한 계정에 데이터 원본에 대한 필요한 사용 권한이 있는지 확인해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-113">At this time, you might also need to verify that the account you are using to process the data mining objects or query data mining models has the necessary permissions on the data source.</span></span>  
  
-   <span data-ttu-id="91cc0-114">기본적으로 프로젝트를 가져올 때 작업 영역 데이터베이스가 localhost로 설정되거나 모든 기본 인스턴스가 **에서** 기본 대상 서버 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-114">By default, when you import a project, the workspace database is set to localhost, or whatever default instance is configured as the **Default Target Server** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="91cc0-115">이 속성을 설정하려면 **옵션** 메뉴에서 **비즈니스 인텔리전스 디자이너**, **Analysis Services**, **일반**을 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-115">To set this property, from the **Options** menu, select **Business Intelligence Designers**, select **Analysis Services**, and then select **General**.</span></span>  
  
     <span data-ttu-id="91cc0-116">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 테이블 형식 모델 프로젝트에 대한 기본 배포 서버를 구성하기 위해 설정할 수 있는 또 다른 별도의 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-116">Note that, in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], there is another, separate option that you can set to configure the default deployment server for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tabular model projects.</span></span> <span data-ttu-id="91cc0-117">**기본 배포 서버**설정은 테이블 형식 프로젝트에 대한 기본 작업 영역 데이터베이스를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-117">The setting, **Default Deployment Server**, determines the default workspace database for tabular model projects.</span></span> <span data-ttu-id="91cc0-118">테이블 형식 모델을 지원하는 인스턴스는 데이터 마이닝 프로젝트에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-118">You cannot use instances that support tabular models for data mining projects</span></span>  
  
     <span data-ttu-id="91cc0-119">다차원 또는 데이터 마이닝 모드로 실행되는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 의 인스턴스를 사용하도록 기본 배포 데이터베이스를 변경할 수 없는 경우 항상 **프로젝트 속성** 대화 상자를 사용하여 배포 데이터베이스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-119">If you cannot change the default deployment database to use an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] running in multidimensional or data mining mode, you can always specify the deployment database by using the **Project Properties** dialog box.</span></span>  
  
#### <a name="to-create-a-new-data-mining-project-by-importing-an-existing-data-mining-project"></a><span data-ttu-id="91cc0-120">기존 데이터 마이닝 프로젝트를 가져와 새 데이터 마이닝 프로젝트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="91cc0-120">To create a new data mining project by importing an existing data mining project</span></span>  
  
1.  <span data-ttu-id="91cc0-121">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]의 **파일** 메뉴에서 **새로 만들기**를 클릭한 다음 **프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-121">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], on the **File** menu, click **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="91cc0-122">**새 프로젝트** 대화 상자의 **설치된 템플릿**에서 **비즈니스 인텔리전스**, **Analysis Services**, **서버에서 가져오기(다차원 및 데이터 마이닝)** 를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-122">In the **New Project** dialog box, under **Installed Templates**, click **Business Intelligence**, click **Analysis Services**, and then click **Import from Server (Multidimensional/Data Mining)**.</span></span>  
  
3.  <span data-ttu-id="91cc0-123">**이름**에 프로젝트의 이름을 입력하고 위치 및 솔루션 이름을 지정한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-123">For **Name**, type a name for the project, then specify a location and solution name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="91cc0-124">**Analysis Services 데이터베이스 가져오기 마법사** 가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-124">The **Import Analysis Services Database wizard** starts.</span></span> <span data-ttu-id="91cc0-125">시작 페이지에서 확인을 클릭하여 계속 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-125">Click OK on the Welcome page to proceed.</span></span>  
  
4.  <span data-ttu-id="91cc0-126">**원본 데이터베이스 선택**페이지의 **서버**에서 가져올 솔루션이 포함된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-126">On the page, **Select Source Database**, for **Server**, specify the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance that contains the solution you want to import.</span></span>  
  
     <span data-ttu-id="91cc0-127">**데이터베이스**에서 가져올 데이터 마이닝 개체가 포함된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-127">For **Database**, choose the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that contains the data mining objects you want to import.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="91cc0-128">가져올 개체는 지정할 수 없습니다. 기존 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스를 선택한 경우 모든 다차원 및 데이터 마이닝 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-128">You cannot specify the objects you want to import; when you choose an existing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, all multidimensional and data mining objects are imported.</span></span>  
  
     <span data-ttu-id="91cc0-129">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-129">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="91cc0-130">**마법사 완료**페이지에 가져오기 작업의 진행률이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-130">The page, **Completing the Wizard**, displays the progress of the import operation.</span></span> <span data-ttu-id="91cc0-131">작업을 취소하거나 가져오는 개체를 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-131">You cannot cancel the operation or change the objects that are being imported.</span></span> <span data-ttu-id="91cc0-132">완료되었으면 **마침** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-132">Click **Finish** when done.</span></span>  
  
     <span data-ttu-id="91cc0-133">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 새 프로젝트가 자동으로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="91cc0-133">The new project is automatically opened using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91cc0-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="91cc0-134">See Also</span></span>  
 [<span data-ttu-id="91cc0-135">프로젝트 속성&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="91cc0-135">Project Properties &#40;SSAS Tabular&#41;</span></span>](../tabular-models/properties-ssas-tabular.md)  
  
  
