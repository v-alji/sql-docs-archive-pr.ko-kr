---
title: 파티션 원본 대화 상자 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionsourcedialog.f1
ms.assetid: c414dabe-9bad-49b7-9a3c-dfca87fef92b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6732e8f00dc0d01e0d3b708794a1d9c497ae4cf5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727387"
---
# <a name="partition-source-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="c09b6-102">파티션 원본 대화 상자(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="c09b6-102">Partition Source Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="c09b6-103">**의** 파티션 원본 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 대화 상자를 사용하여 파티션에 대한 팩트 테이블 데이터의 원본을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c09b6-103">Use the **Partition Source** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to specify the source of fact table data for a partition.</span></span> <span data-ttu-id="c09b6-104">다음을 수행하여 **파티션 원본** 대화 상자를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c09b6-104">You can display the **Partition Source** dialog box by:</span></span>  
  
-   <span data-ttu-id="c09b6-105">큐브 디자이너의 **파티션** 탭에 있는 **측정값 그룹** 창에서 선택한 측정값 그룹의 **파티션** 표에 있는 셀의 **...** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c09b6-105">Clicking the **...** button on a cell from the **Partitions** grid of a selected measure group in the **Measure Groups** pane on the **Partitions** tab in Cube Designer.</span></span>  
  
-   <span data-ttu-id="c09b6-106">**의** 속성 **창에서** Partition **개체의** Source **속성 값에 있는** ... [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c09b6-106">Clicking the **...** button on the **Source** property value of a **Partition** object in the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="c09b6-107">옵션</span><span class="sxs-lookup"><span data-stu-id="c09b6-107">Options</span></span>  
  
|<span data-ttu-id="c09b6-108">옵션</span><span class="sxs-lookup"><span data-stu-id="c09b6-108">Option</span></span>|<span data-ttu-id="c09b6-109">정의</span><span class="sxs-lookup"><span data-stu-id="c09b6-109">Definition</span></span>|  
|------------|----------------|  
|<span data-ttu-id="c09b6-110">**바인딩 유형**</span><span class="sxs-lookup"><span data-stu-id="c09b6-110">**Binding type**</span></span>|<span data-ttu-id="c09b6-111">지정한 파티션의 원본에 사용할 바인딩 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c09b6-111">Select the binding type to use for the source of the specified partition.</span></span> <span data-ttu-id="c09b6-112">다음 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c09b6-112">The following options are available:</span></span><br /><br /> <span data-ttu-id="c09b6-113">**테이블 바인딩**: **테이블 바인딩 세부 정보** 창을 표시 하 고 파티션이 데이터 원본 또는 데이터 원본 뷰의 테이블 내용에 바인딩되어 있음을 나타내려면 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09b6-113">**Table binding**: Select to display the **Table Binding Detail** pane and indicate that the partition is bound to the contents of a table in a data source or data source view.</span></span> <span data-ttu-id="c09b6-114">**테이블 바인딩 세부 정보** 창에 대한 자세한 내용은 [테이블 바인딩 세부 정보&#40;파티션 원본 대화 상자&#41;&#40;Analysis Services - 다차원 데이터&#41;](table-binding-partition-source-dialog-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c09b6-114">For more information about the **Table Binding Detail** pane, see [Table Binding Detail &#40;Partition Source Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](table-binding-partition-source-dialog-analysis-services-multidimensional-data.md).</span></span><br /><br /> <span data-ttu-id="c09b6-115">**세부 정보**: **쿼리 바인딩 세부 정보** 창을 표시 하 고 파티션이 데이터 원본에서 실행 되는 쿼리 내용에 바인딩되어 있음을 나타내려면 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09b6-115">**Detail**: Select to display the **Query Binding Detail** pane and indicate that the partition is bound to the contents of a query executed on a data source.</span></span> <span data-ttu-id="c09b6-116">**쿼리 바인딩 세부 정보** 창에 대한 자세한 내용은 [쿼리 바인딩 세부 정보&#40;파티션 원본 대화 상자&#41;&#40;Analysis Services - 다차원 데이터&#41;](query-binding-partition-source-dialog-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c09b6-116">For more information about the **Query Binding Detail** pane, see [Query Binding Detail &#40;Partition Source Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](query-binding-partition-source-dialog-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="c09b6-117">**세부 정보**</span><span class="sxs-lookup"><span data-stu-id="c09b6-117">**Detail**</span></span>|<span data-ttu-id="c09b6-118">**바인딩 유형** 옵션의 값에 따라 **테이블 바인딩 세부 정보** 대화 상자 또는 **쿼리 바인딩 세부 정보** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c09b6-118">Displays either the **Table Binding Detail** dialog box or the **Query Binding Detail** dialog box, depending on the value of the **Binding type** option.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c09b6-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c09b6-119">See Also</span></span>  
 <span data-ttu-id="c09b6-120">[큐브 디자이너 &#40;파티션&#41; &#40;Analysis Services 다차원 데이터&#41;](partitions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="c09b6-120">[Partitions &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](partitions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="c09b6-121">Analysis Services 디자이너 및 대화 상자 &#40;다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="c09b6-121">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
