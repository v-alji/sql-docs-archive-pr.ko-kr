---
title: 보고서 작성기의 보고서 파트 및 데이터 세트 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1fe86481-9c41-4535-a4b7-c7c4d780cab6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6ad592561fa8d1ee7a57bc83eb89d9aec1ba6f6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742856"
---
# <a name="report-parts-and-datasets-in-report-builder"></a><span data-ttu-id="03a6a-102">보고서 작성기의 보고서 파트 및 데이터 세트</span><span class="sxs-lookup"><span data-stu-id="03a6a-102">Report Parts and Datasets in Report Builder</span></span>
  <span data-ttu-id="03a6a-103">보고서 작성기에서 보고서에 데이터를 포함하는 가장 쉬운 방법은 보고서 파트 갤러리에서 보고서 파트를 추가하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-103">In Report Builder, the easiest way to include data in a report is to add report parts from the Report Part Gallery.</span></span> <span data-ttu-id="03a6a-104">보고서 파트에는 파트가 종속되는 *종속 데이터 세트*라는 데이터 세트가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-104">Report parts contain the datasets that they depend on, which are known as *dependent datasets*.</span></span> <span data-ttu-id="03a6a-105">종속 데이터 세트는 공유 데이터 원본을 기반으로 하며 포함된 데이터 세트 또는 공유 데이터 세트일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-105">Dependent datasets are based on shared data sources and can be either embedded datasets or shared datasets.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
 <span data-ttu-id="03a6a-106">보고서에 데이터를 포함하는 또 다른 쉬운 방법은 공유 데이터 세트를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-106">Another easy way to include data in a report is to use a shared dataset.</span></span> <span data-ttu-id="03a6a-107">자세한 내용은 [보고서 포함된 데이터 세트 및 공유 데이터 세트&#40;보고서 작성기 및 SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="03a6a-107">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="adding-a-report-part-with-dependent-datasets-to-your-report"></a><a name="Adding"></a><span data-ttu-id="03a6a-108">종속 데이터 집합이 포함 된 보고서 파트를 보고서에 추가</span><span class="sxs-lookup"><span data-stu-id="03a6a-108">Adding a Report Part with Dependent Datasets to Your Report</span></span>  
 <span data-ttu-id="03a6a-109">보고서에 보고서 파트를 추가하면 해당 파트에 포함된 종속 데이터 세트도 보고서에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-109">When you add a report part to your report, the dependent datasets that it contains are also added to your report.</span></span> <span data-ttu-id="03a6a-110">보고서 파트에는 기타 보고서 항목이 다수 들어 있는 사각형을 포함할 수 있으므로 보고서에 종속 데이터 세트가 여러 개 추가될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-110">Because a report part might include a rectangle that contains many other report items, it can add multiple dependent datasets to your report.</span></span> <span data-ttu-id="03a6a-111">각 공유 데이터 세트는 독립 참조이므로 공유 데이터 세트가 종속되는 공유 데이터 원본은 보고서에 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-111">Each shared dataset is an independent reference; the shared data source that it depends on is not added to your report.</span></span> <span data-ttu-id="03a6a-112">각 포함된 데이터 세트 역시 자신이 종속되는 공유 데이터 원본이나 포함된 데이터 원본을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-112">Each embedded dataset also adds the embedded or shared data source that it depends on.</span></span>  
  
 <span data-ttu-id="03a6a-113">포함된 데이터 원본의 자격 증명은 보고서 파트의 일부로 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-113">The credentials for an embedded data source are not saved as part of the report part.</span></span> <span data-ttu-id="03a6a-114">포함된 데이터 원본을 보고서에 추가하는 경우에는 보고서를 실행할 때 자격 증명을 제공하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-114">If an embedded data source is added to your report, you will be prompted for credentials when you run the report.</span></span> <span data-ttu-id="03a6a-115">이 메시지가 표시되지 않도록 하려면 공유 데이터 원본을 기반으로 하며 자격 증명이 저장되어 있는 보고서 파트를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="03a6a-115">To avoid being prompted for credentials, use report parts that are based on shared data sources with stored credentials.</span></span>  
  
 <span data-ttu-id="03a6a-116">보고서에 보고서 파트를 추가한 후에도 추가된 데이터 세트는 사용자가 만드는 공유 데이터 세트 또는 포함된 데이터 세트와 아무런 차이가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-116">After you add a report part to your report, the added datasets are no different than embedded or shared datasets that you create.</span></span> <span data-ttu-id="03a6a-117">보고서 데이터 창에서 추가 데이터 세트를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-117">You can view the additional datasets in the Report Data pane.</span></span> <span data-ttu-id="03a6a-118">포함된 데이터 세트는 해당하는 공유 데이터 원본 아래에, 공유 데이터 세트는 공유 데이터 세트 폴더 아래에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-118">Embedded datasets appear under the corresponding shared data source and shared datasets appear under the Shared Datasets folder.</span></span>  
  
  
##  <a name="customizing-dependent-datasets"></a><a name="Customizing"></a><span data-ttu-id="03a6a-119">종속 데이터 집합 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="03a6a-119">Customizing Dependent Datasets</span></span>  
 <span data-ttu-id="03a6a-120">보고서 파트를 보고서에 추가한 후에는 미리 보기를 통해 데이터 변경 여부를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-120">After you add report parts to your report, you might preview it and decide to make some changes to the data.</span></span> <span data-ttu-id="03a6a-121">변경 가능한 내용은 사용 중인 데이터 세트 유형에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-121">What you can change depends on the type of dataset that you are working with.</span></span>  
  
 <span data-ttu-id="03a6a-122">포함된 데이터 세트의 데이터 및 데이터 옵션을 변경하려면 데이터 세트를 만들었을 때처럼 쿼리를 비롯한 데이터 세트 속성을 편집하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-122">To change data and data options for an embedded dataset, you can edit the dataset properties, including the query, just as if you had created the dataset yourself.</span></span>  
  
 <span data-ttu-id="03a6a-123">공유 데이터 세트의 데이터 및 데이터 옵션을 변경하려면 보고서 서버에서 공유 데이터 세트 정의를 변경하면 됩니다. 단, 이 경우 해당하는 사용 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-123">To change a data and data options for a shared dataset, you can change the shared dataset definition on the report server only you have sufficient permissions.</span></span> <span data-ttu-id="03a6a-124">필터와 계산 필드를 추가하고 대/소문자 구분 등의 데이터 옵션을 변경하여 보고서에서 공유 데이터 세트 인스턴스를 사용자 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-124">You can also customize the instance of the shared dataset in your report by adding filters, adding calculated fields, and changing data options such as case sensitivity.</span></span> <span data-ttu-id="03a6a-125">자세한 내용은 [포함된 데이터 세트 및 공유 데이터 세트&#40;보고서 작성기 및 SSRS&#41;](embedded-and-shared-datasets-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="03a6a-125">For more information, see [Embedded and Shared Datasets &#40;Report Builder and SSRS&#41;](embedded-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="03a6a-126">공유 데이터 세트의 정의를 변경하는 방법 또는 보고서에서 공유 데이터 세트의 최신 데이터 변경 내용을 표시하는 방법에 대한 자세한 내용은 [공유 데이터 세트 또는 포함된 데이터 세트 만들기&#40;보고서 작성기 및 SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) 및 [보고서 데이터 창에서 필드 추가, 편집, 새로 고침&#40;보고서 작성기 및 SSRS&#41;](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="03a6a-126">For more information about how to change the definition of a shared dataset or how to show the latest data changes for a shared dataset in your report, see [Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) and [Add, Edit, Refresh Fields in the Report Data Pane &#40;Report Builder and SSRS&#41;](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md).</span></span>  
  
  
##  <a name="publishing-dependent-datasets-as-shared-datasets"></a><a name="Publishing"></a><span data-ttu-id="03a6a-127">공유 데이터 집합으로 종속 데이터 집합 게시</span><span class="sxs-lookup"><span data-stu-id="03a6a-127">Publishing Dependent Datasets as Shared Datasets</span></span>  
 <span data-ttu-id="03a6a-128">종속 데이터 세트가 포함된 보고서 항목을 게시할 때는 각 데이터 세트를 공유 데이터 세트 또는 포함된 데이터 세트(보고서 항목에 포함된 상태로 유지됨)로 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-128">When you publish a report item that has dependent datasets, you have the option to publish each dataset as a shared dataset or as an embedded dataset that remains embedded in the report item.</span></span>  
  
 <span data-ttu-id="03a6a-129">공유 데이터 세트 옵션을 선택하면 데이터 세트가 공유 데이터 세트 정의로 보고서 서버에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-129">When you select the shared dataset option, the dataset is saved to the report server as a shared dataset definition.</span></span> <span data-ttu-id="03a6a-130">보고서에서 해당 데이터 세트를 사용하는 모든 보고서 항목은 현재 보고서 서버에 있는 공유 데이터 세트를 가리키도록 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-130">In your report, every report item that uses that dataset is updated to point to the shared dataset that is now on the report server.</span></span> <span data-ttu-id="03a6a-131">그러면 다음과 같은 결과가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-131">Two things happen as a result:</span></span>  
  
1.  <span data-ttu-id="03a6a-132">게시 대화 상자에서 게시된 각 공유 데이터 세트가 게시 가능한 항목 목록에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-132">In the Publish dialog box, each shared dataset that has been published is removed from the list of items that are available to publish.</span></span>  
  
2.  <span data-ttu-id="03a6a-133">보고서 작성기를 끝내거나 새 보고서를 시작할 때 보고서를 저장하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-133">When you exit Report Builder or start a new report, you are prompted to save your report.</span></span> <span data-ttu-id="03a6a-134">보고서를 저장하지 않는 경우 다음 번에 해당 보고서를 열어 보고서 항목을 게시할 때 같은 데이터 세트의 새 복사본이 게시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-134">If you do not save your report, the next time you open this report and publish report items, you might publish new copies of the same datasets.</span></span> <span data-ttu-id="03a6a-135">공유 데이터 세트의 여러 복사본이 보고서 서버에 저장되지 않도록 하려면 보고서를 저장하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-135">To prevent saving multiple copies of shared datasets to the report server, we recommend that you save the report.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="03a6a-136">자신과 다른 사용자가 공유 데이터 세트의 데이터를 계속 정상적으로 사용하도록 하려면 보고서 항목 보안 관련 원칙을 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03a6a-136">To ensure that you and others can continue to successfully use data from a shared dataset, you must understand the principles behind securing report items.</span></span> <span data-ttu-id="03a6a-137">자세한 내용은 [공유 데이터 세트 항목 보안 설정](../security/secure-shared-dataset-items.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="03a6a-137">For more information, see [Secure Shared Dataset Items](../security/secure-shared-dataset-items.md).</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="03a6a-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="03a6a-138">See Also</span></span>  
 <span data-ttu-id="03a6a-139">[보고서 디자인 뷰 &#40;보고서 작성기&#41;](../report-builder/report-design-view-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="03a6a-139">[Report Design View &#40;Report Builder&#41;](../report-builder/report-design-view-report-builder.md) </span></span>  
 <span data-ttu-id="03a6a-140">[보안 &#40;보고서 작성기&#41;](../report-builder/security-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="03a6a-140">[Security &#40;Report Builder&#41;](../report-builder/security-report-builder.md) </span></span>  
 <span data-ttu-id="03a6a-141">[보고서 파트 &#40;보고서 작성기 및 SSRS&#41;](../report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="03a6a-141">[Report Parts &#40;Report Builder and SSRS&#41;](../report-parts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="03a6a-142">보고서 포함된 데이터 세트 및 공유 데이터 세트&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="03a6a-142">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  
