---
title: 마이닝 구조의 속성 변경 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], properties
ms.assetid: 03b16897-2e36-42b8-9f7d-db1b9b898401
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2c1e63ad5fada770394e2fc283e0e592319281b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727483"
---
# <a name="change-the-properties-of-a-mining-structure"></a><span data-ttu-id="e8561-102">마이닝 구조 속성 변경</span><span class="sxs-lookup"><span data-stu-id="e8561-102">Change the Properties of a Mining Structure</span></span>
  <span data-ttu-id="e8561-103">마이닝 구조에 대한 속성은 두 가지 종류가 있으며 이 두 가지 속성 모두 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8561-103">There are two kinds of properties on a mining structure, both of which can be modified:</span></span>  
  
-   <span data-ttu-id="e8561-104">마이닝 구조의 속성 중 전체 구조에 영향을 주는 속성</span><span class="sxs-lookup"><span data-stu-id="e8561-104">Properties of the mining structure that affect the entire structure</span></span>  
  
-   <span data-ttu-id="e8561-105">구조의 개별 열에 대한 속성</span><span class="sxs-lookup"><span data-stu-id="e8561-105">Properties on individual columns in the structure</span></span>  
  
 <span data-ttu-id="e8561-106">일부 속성은 다른 속성 설정에 종속됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8561-106">Note that some properties are dependent on other property settings.</span></span> <span data-ttu-id="e8561-107">예를 들어 열의 데이터 형식을 `Discretized`로 설정하기 전에는 범주화 동작을 제어하는 속성(예: <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> 또는 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A>)을 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8561-107">For example, you cannot set properties that control binning behavior (such as <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> or <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A>) until you have set the data type of the column to `Discretized`.</span></span>  
  
 <span data-ttu-id="e8561-108">마이닝 구조 속성에 대한 자세한 내용은 [마이닝 구조 열](mining-structure-columns.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8561-108">For more information about mining structure properties, see [Mining Structure Columns](mining-structure-columns.md).</span></span>  
  
### <a name="to-change-the-properties-of-a-mining-structure"></a><span data-ttu-id="e8561-109">마이닝 구조의 속성을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="e8561-109">To change the properties of a mining structure</span></span>  
  
1.  <span data-ttu-id="e8561-110">데이터 마이닝 디자이너의 **마이닝 구조** 탭에서 마이닝 구조의 한 열이나 마이닝 구조를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e8561-110">On the **Mining Structure** tab in Data Mining Designer, right-click either the mining structure or a column in the mining structure, and then select **Properties**.</span></span>  
  
     <span data-ttu-id="e8561-111">화면 오른쪽에 **속성** 창이 열립니다. 이 창이 이미 열려 있는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8561-111">The **Properties** window opens on the right side of the screen, if it was not already visible.</span></span>  
  
2.  <span data-ttu-id="e8561-112">**속성** 창에서 변경할 속성에 해당하는 값을 선택하고 새 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e8561-112">In the **Properties** window, select the value that corresponds to the property that you want to change, and then enter the new value.</span></span>  
  
     <span data-ttu-id="e8561-113">디자이너에서 다른 요소를 선택하면 새 값이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8561-113">The new value will take effect when you select a different element in the designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8561-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e8561-114">See Also</span></span>  
 [<span data-ttu-id="e8561-115">마이닝 구조 태스크 및 방법</span><span class="sxs-lookup"><span data-stu-id="e8561-115">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
  
