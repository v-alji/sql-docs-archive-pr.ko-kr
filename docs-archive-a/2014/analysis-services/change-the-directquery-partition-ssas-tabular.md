---
title: DirectQuery 파티션 변경 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f9df1e66-dd23-41b4-95eb-af110d10eda4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 43d14785f72d9bfe6406e2b81d3f1b97e9b7cc2e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648704"
---
# <a name="change-the-directquery-partition-ssas-tabular"></a><span data-ttu-id="3fce3-102">DirectQuery 파티션 변경(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="3fce3-102">Change the DirectQuery Partition (SSAS Tabular)</span></span>
  <span data-ttu-id="3fce3-103">테이블의 한 파티션만 DirectQuery 파티션으로 지정할 수 있으므로 기본적으로 Analysis Services에서는 테이블에 첫 번째로 만들어진 파티션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3fce3-103">Because only one partition in a table can be designated as the DirectQuery partition, by default, Analysis Services uses the first partition that was created in the table.</span></span> <span data-ttu-id="3fce3-104">모델 프로젝트 제작 중에 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 파티션 관리자 대화 상자를 사용하여 DirectQuery 파티션을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fce3-104">During model project authoring, you can change the DirectQuery partition by using the Partition Manager dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="3fce3-105">배포된 모델의 경우 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 사용하여 DirectQuery 파티션을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fce3-105">For deployed models, you can change the DirectQuery partition by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
### <a name="change-the-directquery-partition-for-a-tabular-model-project"></a><span data-ttu-id="3fce3-106">테이블 형식 모델 프로젝트에 대한 DirectQuery 파티션 변경</span><span class="sxs-lookup"><span data-stu-id="3fce3-106">Change the DirectQuery partition for a tabular model project</span></span>  
  
1.  <span data-ttu-id="3fce3-107">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]의 모델 디자이너에서 분할된 테이블이 포함된 테이블(탭)을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3fce3-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], in the model designer, click on the table (tab) that contains the partitioned table.</span></span>  
  
2.  <span data-ttu-id="3fce3-108">**테이블** 메뉴를 클릭한 다음 **파티션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3fce3-108">Click on the **Table** menu, and then click **Partitions**.</span></span>  
  
3.  <span data-ttu-id="3fce3-109">**파티션 관리자**에서 현재 직접 쿼리 파티션인 파티션의 파티션 이름에는 **(DirectQuery)** 라는 접두사가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3fce3-109">In **Partition Manager**, the partition that is the current Direct Query partition in indicated by the prefix **(DirectQuery)** on the partition name.</span></span>  
  
     <span data-ttu-id="3fce3-110">**파티션** 목록에서 다른 파티션을 선택하고 **DirectQuery로 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3fce3-110">Select a different partition from the **Partitions** list, and then click **Set as DirectQuery**.</span></span> <span data-ttu-id="3fce3-111">**DirectQuery로 설정** 단추는 현재 DirectQuery 파티션이 선택된 경우에는 사용할 수 없으며 모델이 직접 쿼리 모드용으로 설정되지 않은 경우에는 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3fce3-111">The **Set as DirectQuery** button is not enabled when the current DirectQuery partition is selected, and is not visible if the model has not been enabled for Direct Query mode.</span></span>  
  
4.  <span data-ttu-id="3fce3-112">필요한 경우 처리 옵션을 변경하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3fce3-112">If necessary, change the processing options, and then click **OK**.</span></span>  
  
### <a name="change-the-directquery-partition-for-a-deployed-tabular-model"></a><span data-ttu-id="3fce3-113">배포된 테이블 형식 모델에 대한 DirectQuery 파티션 변경</span><span class="sxs-lookup"><span data-stu-id="3fce3-113">Change the DirectQuery partition for a deployed tabular model</span></span>  
  
1.  <span data-ttu-id="3fce3-114">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]의 개체 탐색기에서 model 데이터베이스를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3fce3-114">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], open the model database in Object Explorer.</span></span>  
  
2.  <span data-ttu-id="3fce3-115">**테이블** 노드를 확장하고 분할된 테이블을 마우스 오른쪽 단추로 클릭한 다음 **파티션**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3fce3-115">Expand the **Tables** node, then right-click the partitioned table, and then select **Partitions**.</span></span>  
  
     <span data-ttu-id="3fce3-116">DirectQuery 모드에서 사용하도록 지정된 파티션은 파티션 이름에 (DirectQuery)라는 접두사가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fce3-116">The partition that is designated for use with DirectQuery mode has the prefix (DirectQuery) on the partition name.</span></span>  
  
3.  <span data-ttu-id="3fce3-117">다른 파티션으로 변경하려면 **직접 쿼리** 도구 모음 아이콘을 클릭하여 **DirectQuery 파티션 설정** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3fce3-117">To change to a different partition, click the **Direct Query** toolbar icon to open the **Set DirectQuery Partition** dialog box.</span></span> <span data-ttu-id="3fce3-118">직접 쿼리용으로 설정되지 않은 모델에서는 DirectQuery 도구 모음 아이콘을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3fce3-118">The DirectQuery toolbar icon is not available on models that have not been enabled for Direct Query.</span></span>  
  
4.  <span data-ttu-id="3fce3-119">**파티션 이름** 드롭다운 목록에서 다른 파티션을 선택한 다음 필요한 경우 파티션에 대한 처리 옵션을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="3fce3-119">Choose a different partition from the **Partition Name** dropdown list, and then change processing options on the partition if necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fce3-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3fce3-120">See Also</span></span>  
 [<span data-ttu-id="3fce3-121">파티션&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="3fce3-121">Partitions &#40;SSAS Tabular&#41;</span></span>](tabular-models/partitions-ssas-tabular.md)  
  
  
