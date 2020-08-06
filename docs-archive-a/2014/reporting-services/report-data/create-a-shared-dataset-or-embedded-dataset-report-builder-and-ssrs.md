---
title: 공유 데이터 세트 또는 포함된 데이터 세트 만들기(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d1d7bc71-f0e9-4ce5-b3ad-6fee54388a31
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fca74e1ba7965eeef6ce562e79e378af5bb9e145
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729112"
---
# <a name="create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs"></a><span data-ttu-id="a7f9e-102">공유 데이터 세트 또는 포함된 데이터 세트 만들기(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="a7f9e-102">Create a Shared Dataset or Embedded Dataset (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a7f9e-103">단일 보고서에 사용할 포함된 데이터 세트를 만들거나 여러 보고서에 사용하기 위해 보고서 서버에 저장할 공유 데이터 세트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-103">You can create an embedded dataset for use in a single report or a shared dataset to save to a report server, for use by multiple reports.</span></span> <span data-ttu-id="a7f9e-104">데이터 세트를 만들려면 포함된 데이터 원본 또는 공유 데이터 원본이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-104">To create a dataset, you must have an embedded or shared data source.</span></span>

 <span data-ttu-id="a7f9e-105">보고서 작성기를 사용하여 다음 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-105">Use Report Builder to do the following tasks:</span></span>

-   <span data-ttu-id="a7f9e-106">데이터 세트 디자인 뷰에서 공유 데이터 세트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-106">Create a shared dataset in Dataset Design View.</span></span> <span data-ttu-id="a7f9e-107">공유 데이터 세트는 게시된 공유 데이터 원본을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-107">Shared datasets must use published shared data sources.</span></span>

-   <span data-ttu-id="a7f9e-108">보고서 디자인 뷰에서 포함된 데이터 세트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-108">Create an embedded dataset in Report Design View.</span></span>

-   <span data-ttu-id="a7f9e-109">데이터 세트를 보고서 서버 또는 SharePoint 사이트에 직접 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-109">Save the dataset directly to the report server or SharePoint site.</span></span>

 <span data-ttu-id="a7f9e-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 에서 보고서 작성기를 사용하여 다음 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-110">Use Report Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to do the following tasks:</span></span>

1.  <span data-ttu-id="a7f9e-111">솔루션 탐색기에서 공유 데이터 세트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-111">Create a shared dataset in Solution Explorer.</span></span> <span data-ttu-id="a7f9e-112">공유 데이터 세트는 솔루션 탐색기의 공유 데이터 원본 폴더에 있는 데이터 원본을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-112">Shared datasets must use data sources from the Shared Data Sources folder in Solution Explorer.</span></span>

2.  <span data-ttu-id="a7f9e-113">보고서 데이터 창에서 포함된 데이터 세트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-113">Create an embedded dataset in the Report Data pane.</span></span>

3.  <span data-ttu-id="a7f9e-114">필요에 따라 공유 데이터 세트 및 공유 데이터 원본과 보고서를 함께 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-114">Optionally deploy the shared datasets and shared data source with the report.</span></span> <span data-ttu-id="a7f9e-115">각 항목 유형에 대해 프로젝트 속성을 사용하여 보고서 서버나 SharePoint 사이트에 폴더의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-115">For each type of item, use Project Properties to specify paths to folders on the report server or SharePoint site.</span></span>

 <span data-ttu-id="a7f9e-116">자세한 내용은 [보고서 포함된 데이터 세트 및 공유 데이터 세트&#40;보고서 작성기 및 SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-116">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>

> [!NOTE]
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]

### <a name="to-open-report-builder-and-create-a-shared-dataset"></a><span data-ttu-id="a7f9e-117">보고서 작성기를 열고 공유 데이터 세트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="a7f9e-117">To open Report Builder and create a shared dataset</span></span>

1.  <span data-ttu-id="a7f9e-118">보고서 작성기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-118">Open Report Builder.</span></span> <span data-ttu-id="a7f9e-119">다음 그림과 같이 **새 보고서 또는 데이터 세트** 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-119">The **New report or dataset pane** opens, as shown in the following figure:</span></span>

     <span data-ttu-id="a7f9e-120">![rs_NewSharedDataset](../media/rs-newshareddataset.gif "rs_NewSharedDataset")</span><span class="sxs-lookup"><span data-stu-id="a7f9e-120">![rs_NewSharedDataset](../media/rs-newshareddataset.gif "rs_NewSharedDataset")</span></span>

    > [!NOTE]
    >  <span data-ttu-id="a7f9e-121">**새 보고서 또는 데이터 세트** 창이 나타나지 않으면 보고서 작성기 단추에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-121">If the **New report or dataset pane** does not appear, from the Report Builder button, click **New**.</span></span>

2.  <span data-ttu-id="a7f9e-122">왼쪽 창의 **데이터 세트 만들기**에서 **공유 데이터 세트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-122">In the left pane, under **Create a dataset**, click **Shared Dataset**.</span></span>

3.  <span data-ttu-id="a7f9e-123">오른쪽 창에서 **찾아보기** 를 클릭하여 보고서 서버에서 공유 데이터 원본을 선택한 다음 **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-123">In the right pane, click **Browse** to select a shared data source from the report server, and then click **Create**.</span></span> <span data-ttu-id="a7f9e-124">공유 데이터 원본과 연결된 쿼리 디자이너가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-124">The query designer associated with the shared data source opens.</span></span>

4.  <span data-ttu-id="a7f9e-125">쿼리 디자이너에서 데이터 세트에 포함할 필드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-125">In the query designer, specify the fields to include in the dataset.</span></span>

5.  <span data-ttu-id="a7f9e-126">**실행** (**!**)을 클릭 하 여 쿼리를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-126">Click **Run** (**!**) to run the query.</span></span>

6.  <span data-ttu-id="a7f9e-127">**보고서 작성기** 단추에서 **저장** 또는 **다른 이름으로 저장**을 클릭하여 공유 데이터 세트를 보고서 서버에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-127">On the **Report Builder** button, click **Save** or **Save As** to save the shared dataset to the report server.</span></span>

7.  <span data-ttu-id="a7f9e-128">보고서 작성기를 종료하려면 **보고서 작성기**를 클릭한 다음 **보고서 작성기 끝내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-128">To exit Report Builder, click **Report Builder**, and then click **Exit Report Builder**.</span></span> <span data-ttu-id="a7f9e-129">보고서로 작업하려면 **보고서 작성기**를 클릭한 다음 **새로 만들기** 또는 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-129">To work with reports, click **Report Builder**, and then click **New** or **Open**.</span></span>

### <a name="to-set-query-parameter-options"></a><span data-ttu-id="a7f9e-130">쿼리 매개 변수 옵션을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="a7f9e-130">To set query parameter options</span></span>

1.  <span data-ttu-id="a7f9e-131">보고서 작성기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-131">Open Report Builder.</span></span>

2.  <span data-ttu-id="a7f9e-132">**열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-132">Click **Open**.</span></span>

3.  <span data-ttu-id="a7f9e-133">보고서 서버로 이동하여 공유 데이터 원본의 폴더를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-133">Browse to the report server, and select the folder for the shared data source.</span></span>

4.  <span data-ttu-id="a7f9e-134">**항목 유형**의 드롭다운 목록에서 데이터 세트(\*.rsd)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-134">In **Items of type**, click Datasets (\*.rsd) in the drop-down list.</span></span>

5.  <span data-ttu-id="a7f9e-135">공유 데이터 세트를 선택한 다음, **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-135">Select the shared dataset, and then click **Open**.</span></span> <span data-ttu-id="a7f9e-136">연결된 쿼리 디자이너가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-136">The associated query designer opens.</span></span>

6.  <span data-ttu-id="a7f9e-137">리본에서 **데이터 세트 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-137">On the Ribbon, click **Dataset Properties**.</span></span>

7.  <span data-ttu-id="a7f9e-138">**매개 변수**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-138">Click **Parameters**.</span></span> <span data-ttu-id="a7f9e-139">이 페이지에서 기본값을 상수나 식으로 설정하고 매개 변수를 읽기 전용, Null 허용 또는 **쿼리에서 생략**으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-139">On this page, set a default value to a constant or an expression, mark the parameter as read-only, nullable, or **Omit From Query**.</span></span> <span data-ttu-id="a7f9e-140">자세한 내용은 [데이터 세트 속성 대화 상자, 매개 변수&#40;보고서 작성기&#41;](../dataset-properties-dialog-box-parameters-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-140">For more information, see [Dataset Properties Dialog Box, Parameters &#40;Report Builder&#41;](../dataset-properties-dialog-box-parameters-report-builder.md).</span></span>

8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]


### <a name="to-create-a-dataset-from-a-sql-server-relational-database"></a><span data-ttu-id="a7f9e-141">SQL Server 관계형 데이터베이스에서 데이터 세트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="a7f9e-141">To create a dataset from a SQL Server relational database</span></span>

1.  <span data-ttu-id="a7f9e-142">보고서 데이터 창에서 데이터 원본의 이름을 마우스 오른쪽 단추로 클릭한 다음, **데이터 세트 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-142">In the Report Data pane, right-click the name of the data source, and then click **Add Dataset**.</span></span> <span data-ttu-id="a7f9e-143">**데이터 세트 속성** 대화 상자의 **쿼리** 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-143">The **Query** page of the **Dataset Properties** dialog box opens.</span></span>

2.  <span data-ttu-id="a7f9e-144">**이름**에 데이터 세트의 이름을 입력하거나 기본 이름을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-144">In **Name**, type a name for the dataset or accept the default name.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="a7f9e-145">데이터 세트 이름은 보고서 내에서만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-145">The dataset name is used internally within the report.</span></span> <span data-ttu-id="a7f9e-146">의미를 명확하게 전달하기 위해 쿼리에서 반환하는 데이터에 대한 설명이 포함된 데이터 세트 이름을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-146">For clarity, we recommend that the name of the dataset describe the data that the query returns.</span></span>

3.  <span data-ttu-id="a7f9e-147">**데이터 원본**에서 기존 공유 데이터 원본의 이름을 찾아 선택하거나 **새로 만들기** 를 클릭하여 포함된 데이터 원본을 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-147">In **Data source**, browse to and select the name of an existing shared data source, or click **New** to create a new embedded data source.</span></span>

4.  <span data-ttu-id="a7f9e-148">**쿼리 유형** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-148">Select a **Query type** option.</span></span> <span data-ttu-id="a7f9e-149">데이터 원본 유형에 따라 옵션이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-149">Options depend on the data source type.</span></span>

    -   <span data-ttu-id="a7f9e-150">데이터 원본의 쿼리 언어를 사용하여 쿼리를 작성하려면 **Text** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-150">Select **Text** to write a query using the query language of the data source.</span></span>

    -   <span data-ttu-id="a7f9e-151">관계형 데이터베이스 테이블의 모든 필드를 반환하려면 **Table** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-151">Select **Table** to return all the fields in a relational database table.</span></span>

    -   <span data-ttu-id="a7f9e-152">저장 프로시저를 이름으로 실행하려면 **StoredProcedure** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-152">Select **StoredProcedure** to run a stored procedure by name.</span></span>

5.  <span data-ttu-id="a7f9e-153">**쿼리**에 쿼리, 저장 프로시저 또는 테이블 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-153">In **Query**, type the query, stored procedure, or table name.</span></span> <span data-ttu-id="a7f9e-154">또는 **쿼리 디자이너** 를 클릭하여 그래픽 또는 텍스트 기반 쿼리 디자이너 도구를 열거나 **가져오기** 를 클릭하여 기존 보고서에서 쿼리를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-154">Alternatively, click **Query Designer** to open the graphical or text-based query designer tool, or **Import** to import the query from an existing report.</span></span>

     <span data-ttu-id="a7f9e-155">경우에 따라 데이터 원본에서 쿼리를 실행해야만 쿼리로 지정된 필드 컬렉션을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-155">In a few cases, the field collection specified by the query can only be determined by running the query on the data source.</span></span> <span data-ttu-id="a7f9e-156">예를 들어 저장 프로시저는 결과 집합에 가변적 필드 집합을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-156">For example, a stored procedure may return a variable set of fields in the result set.</span></span> <span data-ttu-id="a7f9e-157">**필드 새로 고침**을 클릭하여 데이터 원본에서 쿼리를 실행하고 보고서 데이터 창에서 데이터 세트 필드 컬렉션을 채우는 데 필요한 필드 이름을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-157">Click **Refresh Fields** to run the query on the data source and retrieve the field names that are needed to populate the dataset field collection in the Report Data pane.</span></span> <span data-ttu-id="a7f9e-158">필드 컬렉션은 **데이터 세트 속성** 대화 상자를 닫은 후 데이터 세트 노드 아래에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-158">The field collection appears under the dataset node after you close the **Dataset Properties** dialog box.</span></span>

6.  <span data-ttu-id="a7f9e-159">**제한 시간**에 보고서 서버에서 데이터베이스의 응답을 기다리는 시간(초)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-159">In **Timeout**, type the number of seconds that the report server waits for a response from the database.</span></span> <span data-ttu-id="a7f9e-160">기본값은 0초입니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-160">The default value is 0 seconds.</span></span> <span data-ttu-id="a7f9e-161">제한 시간 값이 0초이면 쿼리 시간이 제한되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-161">When the time out value is 0 seconds, the query does not time out.</span></span>

7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]

     <span data-ttu-id="a7f9e-162">데이터 세트 및 해당 필드 컬렉션이 데이터 원본 노드 아래의 보고서 데이터 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7f9e-162">The dataset and its field collection appear in the Report Data pane under the data source node.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7f9e-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a7f9e-163">See Also</span></span>
 <span data-ttu-id="a7f9e-164">[보고서 포함 된 데이터 집합 및 공유 데이터 집합 &#40;보고서 작성기 및 ssrs&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) 데이터 [집합 필드 컬렉션 &#40;보고서 작성기 및 Ssrs&#41;](dataset-fields-collection-report-builder-and-ssrs.md) [쿼리 디자이너 &#40;](../query-designers-report-builder.md) [보고서 작성기&#41;보고서 작성기](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) &#40;보고서 작성기 [및 Ssrs&#41;](report-datasets-ssrs.md) 보고서 작성기 [포함 된 데이터 집합과 공유 데이터 집합 &#40;보고서 작성기 및 ssrs](embedded-and-shared-datasets-report-builder-and-ssrs.md) [의 연결 문자열](../data-connections-data-sources-and-connection-strings-in-report-builder.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="a7f9e-164">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) [Dataset Fields Collection &#40;Report Builder and SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md) [Query Designers &#40;Report Builder&#41;](../query-designers-report-builder.md) [Report Builder Help for Dialog Boxes, Panes, and Wizards](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) [Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md) [Embedded and Shared Datasets &#40;Report Builder and SSRS&#41;](embedded-and-shared-datasets-report-builder-and-ssrs.md)</span></span>


