---
title: 데이터 마이닝 모델에서 데이터 검색(DMX)(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- retrieving report data
- datasets [Reporting Services], with DMX queries
- datasets [Reporting Services], Analysis Services
- queries [Reporting Services], data mining prediction
ms.assetid: d9cd3624-1594-4707-8887-55437dd7e07c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a59184524967a9bfe772e41890afc3b900cc9e32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738014"
---
# <a name="retrieve-data-from-a-data-mining-model-dmx-ssrs"></a><span data-ttu-id="f66a7-102">데이터 마이닝 모델에서 데이터 검색(DMX)(SSRS)</span><span class="sxs-lookup"><span data-stu-id="f66a7-102">Retrieve Data from a Data Mining Model (DMX) (SSRS)</span></span>
  <span data-ttu-id="f66a7-103">보고서에 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 데이터 마이닝 모델의 데이터를 사용하려면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 데이터 원본 및 하나 이상의 보고서 데이터 세트를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-103">To use data from a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data mining model in your report, you must define a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source and one or more report datasets.</span></span> <span data-ttu-id="f66a7-104">데이터 원본 정의를 만들 때는 클라이언트 컴퓨터에서 데이터 원본에 액세스할 수 있도록 연결 문자열 및 자격 증명을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-104">When you create the data source definition, you must specify a connection string and credentials so that you can access the data source from your client computer.</span></span>  
  
 <span data-ttu-id="f66a7-105">단일 보고서에 사용할 포함된 데이터 원본 정의를 만들거나 여러 보고서에 사용할 수 있는 공유 데이터 원본 정의를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-105">You can create an embedded data source definition for use by a single report or a shared data source definition that can be used by multiple reports.</span></span> <span data-ttu-id="f66a7-106">이 항목의 절차에서는 포함된 데이터 원본을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-106">The procedures in this topic describe how to create an embedded data source.</span></span> <span data-ttu-id="f66a7-107">공유 데이터 원본에 대한 자세한 내용은 [포함된 데이터 연결 및 공유 데이터 연결 또는 데이터 원본&#40;보고서 작성기 및 SSRS&#41;](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) 및 [공유 데이터 원본 만들기, 수정 및 삭제&#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f66a7-107">For more information about shared data sources, see [Embedded and Shared Data Connections or Data Sources &#40;Report Builder and SSRS&#41;](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) and [Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md).</span></span>  
  
 <span data-ttu-id="f66a7-108">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 데이터 원본을 만든 후에는 하나 이상의 데이터 세트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-108">After you create a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source, you can create one or more datasets.</span></span> <span data-ttu-id="f66a7-109">각 데이터 세트에 대해 DMX(Data Mining Prediction Expression) 쿼리 디자이너를 사용하여 필드 컬렉션을 지정하는 DMX 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-109">For each dataset, you use a Data Mining Prediction Expression (DMX) query designer to create a DMX query that specifies the field collection.</span></span> <span data-ttu-id="f66a7-110">자세한 내용은 [Analysis Services DMX 쿼리 디자이너 사용자 인터페이스](analysis-services-dmx-query-designer-user-interface.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f66a7-110">For more information, see [Analysis Services DMX Query Designer User Interface](analysis-services-dmx-query-designer-user-interface.md).</span></span>  
  
 <span data-ttu-id="f66a7-111">데이터 세트를 만들면 데이터 세트의 이름이 보고서 데이터 창의 해당 데이터 원본 아래에 노드로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-111">After you create a dataset, the name of the dataset appears in the Report Data pane as a node under its data source.</span></span>  
  
 <span data-ttu-id="f66a7-112">보고서를 게시한 후 보고서를 보고서 서버에서 실행할 때 데이터를 검색할 수 있는 권한이 유효하도록 데이터 원본에 대한 자격 증명을 변경해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-112">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
### <a name="to-create-an-embedded-microsoft-sql-server-analysis-services-data-source"></a><span data-ttu-id="f66a7-113">포함된 Microsoft SQL Server Analysis Services 데이터 원본을 만들려면</span><span class="sxs-lookup"><span data-stu-id="f66a7-113">To create an embedded Microsoft SQL Server Analysis Services data source</span></span>  
  
1.  <span data-ttu-id="f66a7-114">보고서 데이터 창의 도구 모음에서 **새로 만들기**, **데이터 원본**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-114">On the toolbar in the Report Data pane, click **New**, and then click **Data Source**.</span></span>  
  
2.  <span data-ttu-id="f66a7-115">**데이터 원본 속성** 대화 상자의 **이름** 입력란에 이름을 입력하거나 기본 이름을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-115">In the **Data Source Properties** dialog box, type a name in the **Name** text box, or accept the default name.</span></span>  
  
3.  <span data-ttu-id="f66a7-116">**포함된 연결** 이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-116">Verify that **Embedded connection** is selected.</span></span>  
  
4.  <span data-ttu-id="f66a7-117">**유형** 드롭다운 목록에서 **Microsoft SQL Server Analysis Services**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-117">From the **Type** drop-down list, select **Microsoft SQL Server Analysis Services**.</span></span>  
  
5.  <span data-ttu-id="f66a7-118">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 데이터 원본에 사용할 연결 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-118">Specify a connection string that works with your [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source.</span></span>  
  
     <span data-ttu-id="f66a7-119">데이터 원본 연결에 사용할 자격 증명 및 연결 정보는 데이터베이스 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="f66a7-119">Contact your database administrator for connection information and for the credentials to use to connect to the data source.</span></span> <span data-ttu-id="f66a7-120">다음 연결 문자열 예에서는 로컬 클라이언트에 있는 [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] 예제 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-120">The following connection string example specifies the sample [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] database on the local client.</span></span>  
  
    ```  
    Data Source=localhost;Initial Catalog=AdventureWorksDW2012  
    ```  
  
6.  <span data-ttu-id="f66a7-121">**자격 증명**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-121">Click **Credentials**.</span></span>  
  
     <span data-ttu-id="f66a7-122">데이터 원본 연결에 사용할 자격 증명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-122">Set the credentials to use to connect to the data source.</span></span> <span data-ttu-id="f66a7-123">자세한 내용은 [보고서 데이터 원본에 대한 자격 증명 및 연결 정보 지정](../../integration-services/connection-manager/data-sources.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f66a7-123">For more information, see [Specify Credential and Connection Information for Report Data Sources](../../integration-services/connection-manager/data-sources.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f66a7-124">데이터 원본 연결을 테스트하려면 **편집**을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="f66a7-124">To test the data source connection, click **Edit**.</span></span> <span data-ttu-id="f66a7-125">그런 다음 **연결 속성** 대화 상자에서 **연결 테스트**를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="f66a7-125">In the **Connection Properties** dialog box, click **Test Connection**.</span></span> <span data-ttu-id="f66a7-126">테스트에 성공한 경우 "연결 테스트에 성공했습니다"라는 정보 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-126">If the test is successful, you will see the information message "Test connection succeeded."</span></span> <span data-ttu-id="f66a7-127">테스트에 실패할 경우에는 테스트에 성공하지 못한 이유에 대한 자세한 정보가 포함된 경고 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-127">If the test fails, you will see a warning message with more information about why the test was not successful.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="f66a7-128">데이터 원본이 보고서 데이터 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-128">The data source appears in the Report Data pane.</span></span>  
  
### <a name="to-create-a-dataset-for-a-microsoft-sql-server-analysis-services"></a><span data-ttu-id="f66a7-129">Microsoft SQL Server Analysis Services에 대한 데이터 세트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="f66a7-129">To create a dataset for a Microsoft SQL Server Analysis Services</span></span>  
  
1.  <span data-ttu-id="f66a7-130">**보고서 데이터** 창에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 데이터 원본에 연결하는 데이터 원본의 이름을 마우스 오른쪽 단추로 클릭한 다음 **데이터 세트 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-130">In the **Report Data** pane, right-click the name of the data source that connects to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source, and then click **Add Dataset**.</span></span>  
  
2.  <span data-ttu-id="f66a7-131">**데이터 세트 속성** 대화 상자에서 **이름** 입력란에 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-131">In the **Dataset Properties** dialog box, type a name in the **Name** text box.</span></span>  
  
3.  <span data-ttu-id="f66a7-132">**데이터 원본**상자에서 이름이 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 데이터 원본에 연결하는 데이터 원본의 이름인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-132">In the **Data source box**, verify that the name is the name of a data source that connects to an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source.</span></span>  
  
4.  <span data-ttu-id="f66a7-133">**쿼리 디자이너** 를 클릭하여 열리는 그래픽 쿼리 디자이너에서 쿼리를 대화형으로 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-133">Click **Query Designer** to open the graphical query designer to build a query interactively.</span></span> <span data-ttu-id="f66a7-134">쿼리 디자이너가 MDX 모드로 열리는 경우 도구 모음에서 **DMX 명령 형식**(![DMX 쿼리 언어 뷰로 변경](../media/rsqdicon-commandtypedmx.gif "DMX 쿼리 언어 뷰로 변경"))을 클릭하여 데이터 마이닝 쿼리 디자이너로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-134">If the query designer opens in MDX mode, click **Command Type DMX** (![Change to DMX query language view](../media/rsqdicon-commandtypedmx.gif "Change to DMX query language view")) on the toolbar to switch to the data mining query designer.</span></span> <span data-ttu-id="f66a7-135">자세한 내용은 [Analysis Services DMX 쿼리 디자이너 사용자 인터페이스](analysis-services-dmx-query-designer-user-interface.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f66a7-135">For more information, see [Analysis Services DMX Query Designer User Interface](analysis-services-dmx-query-designer-user-interface.md).</span></span>  
  
     <span data-ttu-id="f66a7-136">또는 다른 보고서에서 기존 DMX 쿼리를 가져오려면 **가져오기**를 클릭한 다음 DMX 쿼리를 사용하여 .rdl 파일로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-136">Alternatively, to import an existing DMX query from another report, click **Import**, and then navigate to the .rdl file with the DMX query.</span></span> <span data-ttu-id="f66a7-137">.dmx 파일에서 쿼리를 가져올 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-137">Importing a query from an .dmx file is not supported.</span></span>  
  
5.  <span data-ttu-id="f66a7-138">쿼리를 만들고 실행하여 예제 결과를 본 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-138">After you create and run your query to see sample results, click **OK**.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="f66a7-139">데이터 세트 및 해당 필드 컬렉션이 데이터 원본 노드 아래의 보고서 데이터 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f66a7-139">The dataset and its field collection appear in the Report Data pane under the data source node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f66a7-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f66a7-140">See Also</span></span>  
 <span data-ttu-id="f66a7-141">[DMX용 Analysis Services 연결 형식&#40;SSRS&#41;](analysis-services-connection-type-for-dmx-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f66a7-141">[Analysis Services Connection Type for DMX &#40;SSRS&#41;](analysis-services-connection-type-for-dmx-ssrs.md) </span></span>  
 <span data-ttu-id="f66a7-142">[Reporting Services의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="f66a7-142">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 <span data-ttu-id="f66a7-143">[데이터 세트 필드 컬렉션&#40;보고서 작성기 및 SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f66a7-143">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f66a7-144">보고서 포함된 데이터 세트 및 공유 데이터 세트&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f66a7-144">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  
