---
title: 드릴스루 대화 상자 (마이닝 모델 뷰어) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.drillthrough.f1
ms.assetid: 42b78399-143d-4f44-90e0-b545ffb79e10
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1b00c62017de5a26c4507a04aeaf59aba7522146
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659714"
---
# <a name="drill-through-dialog-box-mining-model-viewer"></a><span data-ttu-id="f3c0a-102">드릴스루 대화 상자(마이닝 모델 뷰어)</span><span class="sxs-lookup"><span data-stu-id="f3c0a-102">Drill Through Dialog Box (Mining Model Viewer)</span></span>
  <span data-ttu-id="f3c0a-103">데이터 마이닝 디자이너의 **마이닝 모델 뷰어** 탭을 사용하여 마이닝 모델을 볼 때 모델에 드릴스루가 사용되도록 설정되어 있으면 사례 데이터에 대한 세부 정보로 드릴스루할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3c0a-103">When you view a mining model by using the **Mining Model Viewer** tab of Data Mining Designer, you can drill through into details about the case data, provided the model has drillthrough enabled.</span></span> <span data-ttu-id="f3c0a-104">또한 기본 마이닝 구조에서도 드릴스루를 사용하도록 설정하면 마이닝 구조에서 마이닝 모델에 포함되지 않은 열도 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3c0a-104">Moreover, if the underlying mining structure has drillthrough enabled, you can also see columns in the mining structure, even if those columns were not included in the mining model.</span></span> <span data-ttu-id="f3c0a-105">열 목록의 구조 열에는 접두사로 "Structure"</span><span class="sxs-lookup"><span data-stu-id="f3c0a-105">In the column list, the structure columns are prefixed by the "Structure."</span></span> <span data-ttu-id="f3c0a-106">레이블이 붙습니다.</span><span class="sxs-lookup"><span data-stu-id="f3c0a-106">label.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3c0a-107">기존 마이닝 구조에서는 드릴스루를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3c0a-107">You cannot enable drillthrough on an existing mining structure.</span></span> <span data-ttu-id="f3c0a-108">대신 마이닝 구조를 다시 만들고 생성 프로세스 동안 드릴스루를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3c0a-108">Instead, you must re-create the mining structure and enable drillthrough during the creation process.</span></span>  
  
 <span data-ttu-id="f3c0a-109">드릴스루를 지 원하는 각 마이닝 모델 뷰어에서 사례 데이터에 액세스 하는 방법에 대 한 자세한 내용은 [마이닝 모델에서 사례 데이터로 드릴스루](data-mining/drill-through-to-case-data-from-a-mining-model.md)를 **참조 하세요** .</span><span class="sxs-lookup"><span data-stu-id="f3c0a-109">For information about how to access case data from each of the mining model viewers that support drillthrough, **see** [Drill Through to Case Data from a Mining Model](data-mining/drill-through-to-case-data-from-a-mining-model.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="f3c0a-110">옵션</span><span class="sxs-lookup"><span data-stu-id="f3c0a-110">Options</span></span>  
 <span data-ttu-id="f3c0a-111">**사례 분류 위치**</span><span class="sxs-lookup"><span data-stu-id="f3c0a-111">**Cases Classified To**</span></span>  
 <span data-ttu-id="f3c0a-112">선택한 노드에 포함되어 있는 규칙, 항목 집합 및 클러스터의 정의를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f3c0a-112">Displays the definition of the rule, itemset, and cluster that are contained in the selected node.</span></span>  
  
 <span data-ttu-id="f3c0a-113">**열 목록**</span><span class="sxs-lookup"><span data-stu-id="f3c0a-113">**Column list**</span></span>  
 <span data-ttu-id="f3c0a-114">모델 열과 구조 열을 차례로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f3c0a-114">Displays the columns in the model, followed by the structure columns.</span></span>  
  
 <span data-ttu-id="f3c0a-115">**참고** 구조 열은 마이닝 구조에서 드릴스루를 사용할 수 있고 **모델 및 구조 열**옵션을 선택한 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3c0a-115">**Note** Structure columns are displayed only if drillthrough is enabled on the mining structure, and if you selected the option, **Model and Structure Columns**.</span></span> <span data-ttu-id="f3c0a-116">또한 마이닝 모델과 마이닝 구조 모두에 대해 열을 볼 수 있는 드릴스루 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3c0a-116">Moreover, you must have drillthrough permissions on both the mining model and the mining structure to view the columns.</span></span>  
  
 <span data-ttu-id="f3c0a-117">모델에 포함 되지 않은 구조 열은 \*\*structure. \<column name> \*\*로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3c0a-117">Structure columns that are not included in the model appear as **Structure.\<column name>**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3c0a-118">표 형태의 창을 아무 곳이나 마우스 오른쪽 단추로 클릭하고 **모두 복사**를 선택하여 드릴스루 데이터를 탭 구분 형식으로 클립보드에 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3c0a-118">You can right-click anywhere in the column grid and select **Copy All** to copy the drillthrough data, in tab-delimited format, to the Clipboard.</span></span> <span data-ttu-id="f3c0a-119">복사된 데이터에는 사례 데이터만 포함되고 노드 정의는 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3c0a-119">The copied data includes only the case data, not the node definition.</span></span>  
  
 <span data-ttu-id="f3c0a-120">**재생**</span><span class="sxs-lookup"><span data-stu-id="f3c0a-120">**Play**</span></span>  
 <span data-ttu-id="f3c0a-121">데이터를 새로 고치려면 녹색 화살표 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f3c0a-121">Click the green arrow button to refresh the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3c0a-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f3c0a-122">See Also</span></span>  
 <span data-ttu-id="f3c0a-123">[드릴스루 쿼리 &#40;데이터 마이닝&#41;](data-mining/drillthrough-queries-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="f3c0a-123">[Drillthrough Queries &#40;Data Mining&#41;](data-mining/drillthrough-queries-data-mining.md) </span></span>  
 <span data-ttu-id="f3c0a-124">[마이닝 모델 뷰어 &#40;데이터 마이닝 모델 디자이너&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="f3c0a-124">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="f3c0a-125">마이닝 모델 뷰어 태스크 및 방법</span><span class="sxs-lookup"><span data-stu-id="f3c0a-125">Mining Model Viewer Tasks and How-tos</span></span>](data-mining/mining-model-viewer-tasks-and-how-tos.md)  
  
  
