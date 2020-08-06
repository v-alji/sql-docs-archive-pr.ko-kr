---
title: 큐브 차원 추가 대화 상자 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.addcubedimensiondialog.f1
helpviewer_keywords:
- Add Cube Dimension dialog box
ms.assetid: 625a3b1f-183b-445f-9bb7-96945c324767
author: minewiskan
ms.author: owend
ms.openlocfilehash: d0de75c02c39b0690184f35f2b0b6a07d7ed9a4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647340"
---
# <a name="add-cube-dimension-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="576dc-102">큐브 차원 추가 대화 상자(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="576dc-102">Add Cube Dimension Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="576dc-103">**의** 큐브 차원 추가 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 대화 상자를 사용하여 데이터베이스 차원에 대한 참조를 큐브에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="576dc-103">Use the **Add Cube Dimension** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to add a reference to a database dimension to a cube.</span></span> <span data-ttu-id="576dc-104">다음 중 하나를 수행하여 **큐브 차원 추가** 대화 상자를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="576dc-104">You can display the **Add Cube Dimension** dialog box by doing one of the following:</span></span>  
  
-   <span data-ttu-id="576dc-105">큐브 디자이너의 **큐브 구조** 또는 **차원 용도** 탭에 있는 **도구 모음** 창에서 **큐브 차원 추가** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="576dc-105">Click **Add Cube Dimension** in the **Toolbar** pane on the **Cube Structure** or **Dimension Usage** tab in Cube Designer.</span></span>  
  
-   <span data-ttu-id="576dc-106">큐브 디자이너의 **큐브 구조** 탭에서 **차원** 창을 마우스 오른쪽 단추로 클릭한 다음 상황에 맞는 메뉴에서 **큐브 차원 추가** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="576dc-106">Right-click the **Dimensions** pane on the **Cube Structure** tab in Cube Designer and select **Add Cube Dimension** from the context menu.</span></span>  
  
-   <span data-ttu-id="576dc-107">큐브 디자이너의 **차원 용도** 탭에서 **표** 창을 마우스 오른쪽 단추로 클릭한 다음 상황에 맞는 메뉴에서 **큐브 차원 추가** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="576dc-107">Right-click the **Grid** pane on the **Dimension Usage** tab in Cube Designer and select **Add Cube Dimension** from the context menu.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="576dc-108">각 큐브 차원은 측정값 그룹에 대한 관계를 하나만 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="576dc-108">Each cube dimension can have only one relationship to a measure group.</span></span> <span data-ttu-id="576dc-109">그러나 큐브 차원이 기반으로 하는 데이터베이스 차원이 데이터 원본 뷰에서 둘 이상의 관계를 통해 측정값 그룹과 관련된 경우 둘 이상의 큐브 차원을 만들어서 큐브에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="576dc-109">However, you can create more than one cube dimension and add it to the cube, if the database dimension on which the cube dimension is based is related to measure groups through more than one relationship in the data source view.</span></span> <span data-ttu-id="576dc-110">이러한 차원을 롤플레잉 차원이라고 하며 이는 일반적으로 시간 차원에서 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="576dc-110">Such dimensions are referred to as role-playing dimensions and commonly occur with time dimensions.</span></span>  
  
## <a name="options"></a><span data-ttu-id="576dc-111">옵션</span><span class="sxs-lookup"><span data-stu-id="576dc-111">Options</span></span>  
 <span data-ttu-id="576dc-112">**차원 선택**</span><span class="sxs-lookup"><span data-stu-id="576dc-112">**Select dimension**</span></span>  
 <span data-ttu-id="576dc-113">기존 데이터베이스 차원을 선택하여 이에 기반한 큐브 차원을 선택한 큐브에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="576dc-113">Select an existing database dimension to add a cube dimension based on it to the selected cube.</span></span> <span data-ttu-id="576dc-114">동일한 데이터베이스 차원에서 여러 큐브 차원을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="576dc-114">Multiple cube dimensions can be defined from the same database dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="576dc-115">동일한 데이터베이스 차원에 기반한 둘 이상의 큐브 차원을 큐브에 추가하는 경우 추가 큐브 차원을 롤플레잉 차원이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="576dc-115">If more than one cube dimension based on the same database dimension is added to a cube, the additional cube dimensions are called role-playing dimensions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="576dc-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="576dc-116">See Also</span></span>  
 [<span data-ttu-id="576dc-117">Analysis Services 디자이너 및 대화 상자 &#40;다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="576dc-117">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
