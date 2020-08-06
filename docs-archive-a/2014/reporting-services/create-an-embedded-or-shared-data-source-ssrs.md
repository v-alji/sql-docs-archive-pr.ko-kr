---
title: 포함 된 데이터 원본 또는 공유 데이터 원본 만들기 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], creating
ms.assetid: b111a8d0-a60d-4c8b-b00a-51644b19c34b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 52c5263859ad16ed725065bce4998d08bddaf5f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735100"
---
# <a name="create-an-embedded-or-shared-data-source-ssrs"></a><span data-ttu-id="99838-102">포함된 데이터 원본 또는 공유 데이터 원본 만들기(SSRS)</span><span class="sxs-lookup"><span data-stu-id="99838-102">Create an Embedded or Shared Data Source (SSRS)</span></span>
  <span data-ttu-id="99838-103">보고서 데이터 원본은 이름 및 연결 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="99838-103">A report data source specifies a name and connection information.</span></span> [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<span data-ttu-id="99838-104">는 포함 및 공유의 두 가지 데이터 원본 유형을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="99838-104">supports two types of data sources: embedded and shared.</span></span> <span data-ttu-id="99838-105">포함된 데이터 원본은 보고서 정의에서 정의되고 해당 보고서에서만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="99838-105">An embedded data source is defined in a report definition and used only by that report.</span></span> <span data-ttu-id="99838-106">공유 데이터 원본은 개별 항목으로 정의되고 여러 보고서에서 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99838-106">A shared data source is defined as a separate item and can be used by multiple reports.</span></span> <span data-ttu-id="99838-107">자세한 내용은 [포함 된 데이터 연결 및 공유 데이터 연결 또는 데이터 원본 &#40;보고서 작성기 및 SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="99838-107">For more information, see [Embedded and Shared Data Connections or Data Sources &#40;Report Builder and SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="99838-108">보고서 작성기에서 보고서 서버 또는 SharePoint 사이트를 찾은 다음 포함된 데이터 원본을 만들거나 데이터 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="99838-108">In Report Builder, you browse to the report server or SharePoint site and select data sources or create embedded data sources.</span></span> <span data-ttu-id="99838-109">보고서 작성기에서는 공유 데이터 원본을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="99838-109">You cannot create shared data sources in Report Builder.</span></span>  
  
 <span data-ttu-id="99838-110">보고서 디자이너에서는 공유 데이터 원본 또는 포함된 데이터 원본을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99838-110">In Report Designer, you can create shared or embedded data sources.</span></span> <span data-ttu-id="99838-111">보고서 데이터 창에서 데이터 원본 참조 만들기를 시작 하 고 **새** 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="99838-111">From the Report Data pane, begin to create a data source reference, and then select the **New** option.</span></span> <span data-ttu-id="99838-112">데이터 원본 참조를 만들고 나면 새 공유 데이터 원본은 솔루션 탐색기의 공유 데이터 원본 폴더에 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="99838-112">After you create the data source reference, a new shared data source will automatically be added to Solution Explorer under the Shared Data Sources folder.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="99838-113">공유 데이터 원본을 보고서 서버 또는 SharePoint 사이트에서 직접 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99838-113">You can also create shared data sources directly on a report server or SharePoint site.</span></span> <span data-ttu-id="99838-114">자세한 내용은 [공유 데이터 원본 만들기, 삭제 또는 수정 &#40;보고서 관리자&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md) 또는 [SharePoint 통합 모드 Reporting Services에서 공유 데이터 원본 &#40;&#41;만들기 및 관리 ](../../2014/reporting-services/create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="99838-114">For more information, see [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md) or [Create and Manage Shared Data Sources &#40;Reporting Services in SharePoint Integrated Mode&#41;](../../2014/reporting-services/create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md).</span></span>  
  
### <a name="to-create-an-embedded-or-shared-data-source"></a><span data-ttu-id="99838-115">포함된 데이터 원본 또는 공유 데이터 원본을 만들려면</span><span class="sxs-lookup"><span data-stu-id="99838-115">To create an embedded or shared data source</span></span>  
  
1.  <span data-ttu-id="99838-116">보고서 데이터 창의 도구 모음에서 **새로 만들기** 를 클릭 한 다음 **데이터 원본**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="99838-116">On the toolbar in the Report Data pane, click **New** and then click **Data Source**.</span></span> <span data-ttu-id="99838-117">**데이터 원본 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="99838-117">The **Data Source Properties** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="99838-118">보고서 데이터 창이 표시되지 않는 경우 **보기** 메뉴에서 **보고서 데이터** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="99838-118">If the Report Data pane is not visible, click **Report Data** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="99838-119">**이름** 입력란에 데이터 원본 이름을 입력하거나 기본값을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="99838-119">In the **Name** text box, type a name for the data source or accept the default.</span></span> <span data-ttu-id="99838-120">데이터 원본 이름은 보고서 내부에서만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="99838-120">The data source name is used internally within the report.</span></span> <span data-ttu-id="99838-121">의미를 명확하게 전달하려면 연결 문자열에서 지정된 데이터베이스의 이름을 데이터 원본 이름에 포함하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="99838-121">For clarity, we recommend that the name of the data source contain the name of the database specified in the connection string.</span></span>  
  
3.  <span data-ttu-id="99838-122">포함 된 데이터 원본의 경우 **포함 된 연결** 이 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="99838-122">For an embedded data source, verify that **Embedded connection** is selected.</span></span>  
  
    1.  <span data-ttu-id="99838-123">**유형** 드롭다운 목록에서 데이터 원본 유형(예: **Microsoft SQL Server** 또는 **OLE DB**)을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="99838-123">From the **Type** drop-down list, select a data source type; for example, **Microsoft SQL Server** or **OLE DB**.</span></span>  
  
    2.  <span data-ttu-id="99838-124">다음 대체 방법 중 하나를 사용하여 연결 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="99838-124">Specify a connection string using one of the following alternatives:</span></span>  
  
    -   <span data-ttu-id="99838-125">**연결 문자열** 입력란에 연결 문자열을 직접 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="99838-125">Type the connection string directly in the **Connection string** text box.</span></span> <span data-ttu-id="99838-126">연결 문자열 예제 목록은 Reporting Services의 데이터 [연결, 데이터 원본 및 연결 문자열 보고서 작성기](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md) 또는 [데이터 연결, 데이터 원본 및 연결 문자열](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="99838-126">For a list of example connection strings, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md) or [Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).</span></span>  
  
    -   <span data-ttu-id="99838-127">식 단추(**fx** )를 클릭하여 연결 문자열로 계산되는 식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="99838-127">Click the expression (**fx)** button to create an expression that evaluates to a connection string.</span></span> <span data-ttu-id="99838-128">**식** 대화 상자의 식 창에 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="99838-128">In the **Expression** dialog box, type the expression in the Expression pane.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
    -   <span data-ttu-id="99838-129">2단계에서 선택한 데이터 원본 유형에 대해 **편집** 을 클릭하여 **연결 속성** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="99838-129">Click **Edit** to open the **Connection Properties** dialog box for the data source type you chose in step 2.</span></span>  
  
         <span data-ttu-id="99838-130">**연결 속성** 대화 상자의 필드에 데이터 원본 유형에 대해 적합한 항목을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="99838-130">Fill in the fields in the **Connection Properties** dialog box as appropriate for the data source type.</span></span> <span data-ttu-id="99838-131">연결 속성에는 데이터 원본 유형, 데이터 원본 이름 및 사용할 자격 증명이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="99838-131">Connection properties include the type of data source, the name of the data source, and the credentials to use.</span></span> <span data-ttu-id="99838-132">이 대화 상자에서 값을 지정한 후 **연결 테스트** 를 클릭하여 데이터 원본이 사용 가능한지와 지정한 자격 증명이 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="99838-132">After you specify values in this dialog box, click **Test Connection** to verify that the data source is available and that the credentials you specified are correct.</span></span> <span data-ttu-id="99838-133">특정 데이터 원본 유형에 대한 자세한 내용은 [외부 데이터 원본의 데이터 추가&#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md)의 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99838-133">For more information about specific data source types, see topics in [Add Data from External Data Sources &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md).</span></span>  
  
4.  <span data-ttu-id="99838-134">공유 데이터 원본의 경우 **공유 데이터 원본 참조 사용** 이 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="99838-134">For a shared data source, verify that **Use shared data source reference** is selected.</span></span>  
  
    1.  <span data-ttu-id="99838-135">**새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="99838-135">Click **New**.</span></span> <span data-ttu-id="99838-136">**공유 데이터 원본** 속성 대화 상자에서 2단계 및 3단계를 수행하여 새 데이터 원본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="99838-136">In the **Shared Data Source** properties dialog box, follow steps 2 and 3 to create a new data source.</span></span>  
  
    2.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
         <span data-ttu-id="99838-137">새 공유 데이터 원본이 솔루션 탐색기의 공유 데이터 원본 폴더에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="99838-137">The new shared data source appears in the Shared Data Sources folder in Solution Explorer.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="99838-138">데이터 원본이 보고서 데이터 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="99838-138">The data source appears in the Report Data pane.</span></span> <span data-ttu-id="99838-139">보고서 데이터 창에서 공유 데이터 원본은 데이터 원본 정의를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="99838-139">In the Report Data pane, a shared data source points to the data source definition.</span></span> <span data-ttu-id="99838-140">보고서 작성기에서 데이터 원본 정의는 보고서 서버 또는 SharePoint 사이트에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99838-140">In Report Builder, the data source definition is on a report server or SharePoint site.</span></span> <span data-ttu-id="99838-141">보고서 디자이너에서 데이터 원본 정의는 솔루션 탐색기의 공유 데이터 원본 폴더에 있는 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="99838-141">In Report Designer, the data source definition is a file in Solution Explorer under the Shared Data Sources folder.</span></span>  
  
### <a name="to-import-an-existing-data-source-in-report-designer"></a><span data-ttu-id="99838-142">보고서 디자이너에서 기존 데이터 원본을 가져오려면</span><span class="sxs-lookup"><span data-stu-id="99838-142">To import an existing data source in Report Designer</span></span>  
  
1.  <span data-ttu-id="99838-143">솔루션 탐색기의 보고서 서버 프로젝트에서 **공유 데이터 원본** 폴더를 마우스 오른쪽 단추로 클릭한 다음 **기존 항목 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="99838-143">In Solution Explorer, right-click the **Shared Data Sources** folder in the report server project, and then click **Add Existing Item**.</span></span> <span data-ttu-id="99838-144">**기존 항목 추가** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="99838-144">The **Add Existing Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="99838-145">보고서 정의 공유 데이터 원본 파일(rds)을 탐색한 다음 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="99838-145">Navigate to an existing Report Definition Shared data source (rds) file and then click **Open**.</span></span>  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-convert-an-embedded-data-source-to-a-shared-data-source-in-report-designer"></a><span data-ttu-id="99838-146">보고서 디자이너에서 포함된 데이터 원본을 공유 데이터 원본으로 변환하려면</span><span class="sxs-lookup"><span data-stu-id="99838-146">To convert an embedded data source to a shared data source in Report Designer</span></span>  
  
-   <span data-ttu-id="99838-147">보고서 데이터 창에서 데이터 원본을 마우스 오른쪽 단추로 클릭 한 다음 **공유 데이터 원본으로 변환을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="99838-147">In the Report Data pane, right-click the data source and then click **Convert to Shared Data Source**.</span></span>  
  
### <a name="to-convert-a-shared-data-source-to-an-embedded-data-source-in-report-builder"></a><span data-ttu-id="99838-148">보고서 작성기에서 공유 데이터 원본을 포함된 데이터 원본으로 변환하려면</span><span class="sxs-lookup"><span data-stu-id="99838-148">To convert a shared data source to an embedded data source in Report Builder</span></span>  
  
-   <span data-ttu-id="99838-149">보고서 데이터 창에서 데이터 원본을 마우스 오른쪽 단추로 클릭 하 고 **데이터 원본 속성**을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="99838-149">In the Report Data pane, right-click the data source and open **Data Source Properties**.</span></span>  
  
-   <span data-ttu-id="99838-150">**포함 된 연결** 을 클릭 하 고 앞의 절차에 설명 된 대로 포함 된 데이터 원본 만들기를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="99838-150">Click **Embedded Connection** and finish creating the embedded data source as described in an earlier procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99838-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="99838-151">See Also</span></span>  
 <span data-ttu-id="99838-152">[Reporting Services 데이터 원본에 자격 증명 저장](report-data/store-credentials-in-a-reporting-services-data-source.md) </span><span class="sxs-lookup"><span data-stu-id="99838-152">[Store Credentials in a Reporting Services Data Source](report-data/store-credentials-in-a-reporting-services-data-source.md) </span></span>  
 <span data-ttu-id="99838-153">[포함 된 데이터 연결 및 공유 데이터 연결 또는 데이터 원본 &#40;보고서 작성기 및 SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="99838-153">[Embedded and Shared Data Connections or Data Sources &#40;Report Builder and SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="99838-154">[포함 된 데이터 원본에서 공유 &#40;보고서 작성기 및 SSRS로 변환&#41;](report-data/convert-data-sources-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="99838-154">[Convert a Data Source from Embedded to Shared &#40;Report Builder and SSRS&#41;](report-data/convert-data-sources-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="99838-155">[보고서 또는 모델을 공유 데이터 원본에 바인딩 &#40;SSRS&#41;](report-data/bind-a-report-or-model-to-a-shared-data-source-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="99838-155">[Bind a Report or Model to a Shared Data Source &#40;SSRS&#41;](report-data/bind-a-report-or-model-to-a-shared-data-source-ssrs.md) </span></span>  
 <span data-ttu-id="99838-156">[보고서 &#40;보고서 관리자&#41;에 대 한 데이터 원본 속성 구성](report-data/configure-data-source-properties-for-a-report-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="99838-156">[Configure Data Source Properties for a Report  &#40;Report Manager&#41;](report-data/configure-data-source-properties-for-a-report-report-manager.md) </span></span>  
 [<span data-ttu-id="99838-157">Reporting Services&#40;SSRS&#41;에서 지원하는 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="99838-157">Data Sources Supported by Reporting Services &#40;SSRS&#41;</span></span>](create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
