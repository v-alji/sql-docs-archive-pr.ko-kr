---
title: 데이터 연결이 나 데이터 원본 추가 및 확인 (보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1d3b2573-e29d-480d-9dde-d26379c86618
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d86b3e6598c12545f0e24ef1d162eeb1131bd15d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639355"
---
# <a name="add-and-verify-a-data-connection-or-data-source-report-builder-and-ssrs"></a><span data-ttu-id="70e0f-102">데이터 연결이나 데이터 원본 추가 및 확인(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="70e0f-102">Add and Verify a Data Connection or Data Source (Report Builder and SSRS)</span></span>
  <span data-ttu-id="70e0f-103">보고서 작성기에서는 보고서 서버에 있는 공유 데이터 원본을 추가하거나 보고서에 대한 포함된 데이터 원본을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-103">In Report Builder, you can add a shared data source from the report server or create an embedded data source for your report.</span></span> <span data-ttu-id="70e0f-104">보고서 디자이너에서 공유 데이터 원본이나 포함된 데이터 원본을 만들고 보고서 서버에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-104">In Report Designer, you can create a shared data source or an embedded data source and deploy it to a report server.</span></span>  
  
 <span data-ttu-id="70e0f-105">공유 데이터 원본을 보고서에 추가하려면 보고서 서버로 이동하고 공유 데이터 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-105">To add a shared data source to your report, browse to a report server and select a shared data source.</span></span> <span data-ttu-id="70e0f-106">보고서의 공유 데이터 원본은 보고서 서버에 있는 공유 데이터 원본 정의를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-106">The shared data source in your report points to the shared data source definition on the report server.</span></span>  
  
 <span data-ttu-id="70e0f-107">포함된 데이터 원본을 만들려면 데이터의 외부 원본에 대한 연결 정보가 있어야 하고 데이터에 액세스하는 데 필요한 사용 권한을 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-107">To create an embedded data source, you must have connection information to the external source of data and you must know which permissions you need to access the data.</span></span> <span data-ttu-id="70e0f-108">이 정보는 대개 데이터 원본의 소유자가 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-108">This information usually comes from the owner of the data source.</span></span> <span data-ttu-id="70e0f-109">연결을 테스트하여 지정된 자격 증명이 충분한지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-109">You can test the connection to verify that the credentials that are specified are sufficient.</span></span>  
  
 <span data-ttu-id="70e0f-110">자세한 내용은 [보고서 작성기의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-report-builder.md) 을 참조 하 고 [보고서 작성기에서 자격 증명을 지정](../specify-credentials-in-report-builder.md)하세요.</span><span class="sxs-lookup"><span data-stu-id="70e0f-110">For more information, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md) and [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-create-a-reference-to-a-shared-data-source"></a><span data-ttu-id="70e0f-111">공유 데이터 원본에 대한 참조를 만들려면</span><span class="sxs-lookup"><span data-stu-id="70e0f-111">To create a reference to a shared data source</span></span>  
  
1.  <span data-ttu-id="70e0f-112">보고서 데이터 창의 도구 모음에서 **새로 만들기** , **데이터 원본**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-112">On the toolbar in the Report Data pane, click **New,** and then click **Data Source**.</span></span> <span data-ttu-id="70e0f-113">**데이터 원본 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-113">The **Data Source Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="70e0f-114">**이름** 입력란에 데이터 원본의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-114">In the **Name** text box, type a name for the data source.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="70e0f-115">이 이름은 로컬 보고서 정의에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-115">This name is saved in the local report definition.</span></span> <span data-ttu-id="70e0f-116">이 이름은 보고서 서버에 있는 공유 데이터 원본의 이름이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-116">This name is not the name of the shared data source on the report server.</span></span>  
  
3.  <span data-ttu-id="70e0f-117">**공유 연결 또는 보고서 모델 사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-117">Select **Use a shared connection or report model**.</span></span> <span data-ttu-id="70e0f-118">최근에 사용된 공유 데이터 원본과 보고서 모델의 목록이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-118">The list of recently used shared data sources and report models appears.</span></span> <span data-ttu-id="70e0f-119">보고서 서버에서 하나를 선택하려면 **찾아보기** 를 클릭하고 공유 데이터 원본을 사용할 수 있는 보고서 서버의 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-119">To select one from a report server, click **Browse** and browse to the folder on the report server where shared data sources are available.</span></span>  
  
4.  <span data-ttu-id="70e0f-120">공유 데이터 원본을 선택한 다음 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-120">Select the shared data source and then click **Open**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="70e0f-121">데이터 원본이 보고서 데이터 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-121">The data source appears in the Report Data pane.</span></span>  
  
### <a name="to-create-an-embedded-data-source"></a><span data-ttu-id="70e0f-122">포함된 데이터 원본을 만들려면</span><span class="sxs-lookup"><span data-stu-id="70e0f-122">To create an embedded data source</span></span>  
  
1.  <span data-ttu-id="70e0f-123">보고서 데이터 창의 도구 모음에서 **새로 만들기**를 클릭 한 다음 **데이터 원본**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-123">On the toolbar in the Report Data pane, click **New**, and then click **Data Source**.</span></span> <span data-ttu-id="70e0f-124">**데이터 원본 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-124">The **Data Source Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="70e0f-125">**이름** 입력란에 데이터 원본 이름을 입력하거나 기본값을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-125">In the **Name** text box, type a name for the data source or accept the default.</span></span>  
  
3.  <span data-ttu-id="70e0f-126">**내 보고서에 포함된 연결 사용** 이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-126">Verify that **Use a connection embedded in my report** is selected.</span></span>  
  
    1.  <span data-ttu-id="70e0f-127">**연결 형식 선택** 드롭다운 목록에서 데이터 원본 유형(예: **Microsoft SQL Server** 또는 **OLE DB**)을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-127">From the **Select connection type** drop-down list, select a data source type; for example, **Microsoft SQL Server** or **OLE DB**.</span></span>  
  
    2.  <span data-ttu-id="70e0f-128">다음 대체 방법 중 하나를 사용하여 연결 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-128">Specify a connection string by using one of the following alternatives:</span></span>  
  
    -   <span data-ttu-id="70e0f-129">**연결 문자열** 입력란에 연결 문자열을 직접 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-129">Type the connection string directly in the **Connection string** text box.</span></span> <span data-ttu-id="70e0f-130">연결 문자열 예제 목록은 [보고서 작성기의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="70e0f-130">For a list of example connection strings, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
    -   <span data-ttu-id="70e0f-131">식 단추(**fx** )를 클릭하여 연결 문자열로 계산되는 식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-131">Click the expression (**fx)** button to create an expression that evaluates to a connection string.</span></span> <span data-ttu-id="70e0f-132">**식** 대화 상자의 식 창에 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-132">In the **Expression** dialog box, type the expression in the Expression pane.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    -   <span data-ttu-id="70e0f-133">2단계에서 선택한 데이터 원본 유형에 대해 **작성** 을 클릭하여 **연결 속성** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-133">Click **Build** to open the **Connection Properties** dialog box for the data source type that you chose in step 2.</span></span>  
  
         <span data-ttu-id="70e0f-134">**연결 속성** 대화 상자의 필드에 데이터 원본 유형에 대해 적합한 항목을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-134">Fill in the fields in the **Connection Properties** dialog box as appropriate for the data source type.</span></span> <span data-ttu-id="70e0f-135">연결 속성에는 데이터 원본 유형, 데이터 원본 이름 및 사용할 자격 증명이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-135">Connection properties include the type of data source, the name of the data source, and the credentials to use.</span></span> <span data-ttu-id="70e0f-136">이 대화 상자에서 값을 지정한 후 **연결 테스트** 를 클릭하여 데이터 원본이 사용 가능한지와 지정한 자격 증명이 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-136">After you specify values in this dialog box, click **Test Connection** to verify that the data source is available and that the credentials you specified are correct.</span></span>  
  
4.  <span data-ttu-id="70e0f-137">**자격 증명**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-137">Click **Credentials**.</span></span>  
  
     <span data-ttu-id="70e0f-138">이 데이터 원본에 사용할 자격 증명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-138">Specify the credentials to use for this data source.</span></span> <span data-ttu-id="70e0f-139">데이터 원본의 소유자는 지원되는 자격 증명 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-139">The owner of the data source chooses the type of credentials that are supported.</span></span> <span data-ttu-id="70e0f-140">경우에 따라 데이터 원본 소유자가 보고서 서버에 공유 데이터 원본을 유지하고 다른 사용자가 사용할 수 있는 자격 증명으로 해당 데이터 원본을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-140">In some cases, the owner of the data source maintains a shared data source on a report server and configures the data source with credentials that you can use.</span></span> <span data-ttu-id="70e0f-141">이 정보에 대해서는 데이터 원본 소유자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="70e0f-141">Contact the data source owner for this information.</span></span> <span data-ttu-id="70e0f-142">자세한 내용은 [보고서 작성기에 자격 증명 지정](../specify-credentials-in-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="70e0f-142">For more information, see [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="70e0f-143">데이터 원본이 보고서 데이터 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-143">The data source appears in the Report Data pane.</span></span>  
  
### <a name="to-verify-a-data-connection"></a><span data-ttu-id="70e0f-144">데이터 연결을 확인하려면</span><span class="sxs-lookup"><span data-stu-id="70e0f-144">To verify a data connection</span></span>  
  
1.  <span data-ttu-id="70e0f-145">보고서 데이터 창의 도구 모음에서 데이터 원본을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-145">On the toolbar in the Report Data pane, double-click the data source.</span></span> <span data-ttu-id="70e0f-146">**데이터 원본 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-146">The **Data Source Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="70e0f-147">**연결 테스트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-147">Click **Test Connection**.</span></span>  
  
3.  <span data-ttu-id="70e0f-148">연결이 성공적이면 “연결되었습니다.”라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-148">If the connection is successful, the following message appears: "Connection created successfully".</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="70e0f-149">연결이 성공적이지 않으면 "데이터 원본에 연결할 수 없습니다."라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-149">If the connection is not successful, the following message appears: "Unable to connect to the data source."</span></span>  
  
5.  <span data-ttu-id="70e0f-150">**자세히**를 클릭하고 표시되는 정보를 사용하여 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="70e0f-150">Click **Details**, and use the information to correct the issue.</span></span>  
  
     <span data-ttu-id="70e0f-151">자세한 내용은 [보고서 작성기에 자격 증명 지정](../specify-credentials-in-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="70e0f-151">For more information, see [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="70e0f-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="70e0f-152">See Also</span></span>  
 <span data-ttu-id="70e0f-153">[보고서 &#40;보고서 작성기 및 SSRS&#41;에 데이터를 추가 합니다.](report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="70e0f-153">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="70e0f-154">[보고서 포함 된 데이터 집합 및 공유 데이터 집합 &#40;보고서 작성기 및 SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="70e0f-154">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="70e0f-155">[보고서 작성기 및 SSRS &#40;보고서 찾기, 보기 및 관리 &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="70e0f-155">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="70e0f-156">보고서 작성기의 데이터 연결, 데이터 원본 및 연결 문자열</span><span class="sxs-lookup"><span data-stu-id="70e0f-156">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
  
  
