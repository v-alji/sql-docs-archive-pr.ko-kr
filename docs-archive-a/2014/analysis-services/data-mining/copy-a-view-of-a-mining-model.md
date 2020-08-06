---
title: 마이닝 모델의 뷰 복사 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- clipboards [data mining]
- Mining Model Viewer [Analysis Services], clipboards
- copying mining models to clipboard
ms.assetid: 768372db-e5b4-4990-b459-03d854fd9a6d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 36d4d372bd235cd1cc0c043ff98151091e242269
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727487"
---
# <a name="copy-a-view-of-a-mining-model"></a><span data-ttu-id="0dbe0-102">마이닝 모델의 뷰 복사</span><span class="sxs-lookup"><span data-stu-id="0dbe0-102">Copy a View of a Mining Model</span></span>
  <span data-ttu-id="0dbe0-103">**데이터 마이닝 디자이너의** 마이닝 모델 뷰어 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 탭에서는 마이닝 모델 유형마다 별도의 뷰어가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0dbe0-103">The **Mining Model Viewer** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] uses a separate viewer for each type of mining model.</span></span> <span data-ttu-id="0dbe0-104">이 중 몇몇 뷰어에는 내용을 클립보드로 복사하고 문서나 이미지 조작 소프트웨어에 붙여넣을 수 있는 구성 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0dbe0-104">Several of the viewers have components from which you can copy the contents to the Clipboard, and from there paste the contents into a document or into image manipulation software.</span></span> <span data-ttu-id="0dbe0-105">다음 구성 요소에서 이 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0dbe0-105">The following components make this functionality available:</span></span>  
  
-   <span data-ttu-id="0dbe0-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 시퀀스 클러스터 뷰어와 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 클러스터 뷰어의 클러스터 다이어그램</span><span class="sxs-lookup"><span data-stu-id="0dbe0-106">Cluster Diagram in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Cluster Viewer</span></span>  
  
-   <span data-ttu-id="0dbe0-107">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 시계열 뷰어와 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 트리 뷰어의 의사 결정 트리</span><span class="sxs-lookup"><span data-stu-id="0dbe0-107">Decision Tree in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tree Viewer and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series Viewer</span></span>  
  
-   <span data-ttu-id="0dbe0-108">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 시퀀스 클러스터 뷰어의 상태 전환</span><span class="sxs-lookup"><span data-stu-id="0dbe0-108">State Transitions in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Cluster Viewer</span></span>  
  
-   <span data-ttu-id="0dbe0-109">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 트리 뷰어, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 뷰어 및 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 연결 규칙 뷰어의 종속성 네트워크</span><span class="sxs-lookup"><span data-stu-id="0dbe0-109">Dependency Network in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules Viewer, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes Viewer, and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tree Viewer</span></span>  
  
-   <span data-ttu-id="0dbe0-110">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 일반 콘텐츠 트리 뷰어의 Node Details 창의 마이닝 모델 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="0dbe0-110">Mining model content, from the Node Details pane of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree Viewer</span></span>  
  
 <span data-ttu-id="0dbe0-111">전체 마이닝 모델 표현을 복사하거나 뷰어에 표시할 일부만 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0dbe0-111">You can copy the complete representation of the mining model, or just the part that is visible in the viewer.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="0dbe0-112">뷰어를 사용하여 모델을 복사할 경우 새 모델 개체가 만들어지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0dbe0-112">When you copy a model using the viewer, it does not create a new model object.</span></span> <span data-ttu-id="0dbe0-113">새 모델을 만들려면 마법사 또는 데이터 마이닝 디자이너를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dbe0-113">To create a new model, you must use either the wizard, or the Data Mining Designer,.</span></span> <span data-ttu-id="0dbe0-114">자세한 내용은 [마이닝 모델 복사본 만들기](make-a-copy-of-a-mining-model.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0dbe0-114">For more information, see [Make a Copy of a Mining Model](make-a-copy-of-a-mining-model.md).</span></span>  
  
### <a name="to-copy-the-complete-model-to-the-clipboard"></a><span data-ttu-id="0dbe0-115">전체 모델을 클립보드로 복사하려면</span><span class="sxs-lookup"><span data-stu-id="0dbe0-115">To copy the complete model to the Clipboard</span></span>  
  
1.  <span data-ttu-id="0dbe0-116">**마이닝 모델 뷰어** 탭의 **마이닝 모델** 목록에서 보려는 마이닝 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0dbe0-116">From the **Mining Model** list on the **Mining Model Viewer** tab, select the mining model that you want to view.</span></span>  
  
2.  <span data-ttu-id="0dbe0-117">**종속성 네트워크** 등의 적절한 탭을 선택하고 해당 탭의 도구 모음에서 **전체 그래프 복사** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0dbe0-117">Select the appropriate tab, such as the **Dependency Network** tab, and then click **Copy Entire Graph** on the toolbar of that tab.</span></span>  
  
### <a name="to-copy-the-visible-piece-of-the-model-to-the-clipboard"></a><span data-ttu-id="0dbe0-118">모델의 표시되는 부분을 클립보드로 복사하려면</span><span class="sxs-lookup"><span data-stu-id="0dbe0-118">To copy the visible piece of the model to the Clipboard</span></span>  
  
1.  <span data-ttu-id="0dbe0-119">**마이닝 모델 뷰어** 탭의 **마이닝 모델** 목록에서 보려는 마이닝 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0dbe0-119">From the **Mining Model** list on the **Mining Model Viewer** tab, select the mining model that you want to view.</span></span>  
  
2.  <span data-ttu-id="0dbe0-120">**종속성 네트워크** 등의 적절한 탭을 선택하고 확대 또는 축소하여 원하는 수준으로 모델을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0dbe0-120">Select the appropriate tab, such as the **Dependency Network** tab, and then zoom in or out to view the model at the level that you want.</span></span>  
  
3.  <span data-ttu-id="0dbe0-121">선택한 탭의 도구 모음에서 **그래프 뷰 복사** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0dbe0-121">Click **Copy Graph View** on the toolbar of the selected tab.</span></span>  
  
### <a name="to-copy-the-mining-model-content-to-the-clipboard"></a><span data-ttu-id="0dbe0-122">마이닝 모델 콘텐츠를 클립보드로 복사하려면</span><span class="sxs-lookup"><span data-stu-id="0dbe0-122">To copy the mining model content to the Clipboard</span></span>  
  
1.  <span data-ttu-id="0dbe0-123">**마이닝 모델 뷰어** 탭의 **마이닝 모델** 목록에서 보려는 마이닝 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0dbe0-123">From the **Mining Model** list on the **Mining Model Viewer** tab, select the mining model that you want to view.</span></span>  
  
2.  <span data-ttu-id="0dbe0-124">**뷰어** 드롭다운 목록에서 **Microsoft 일반 콘텐츠 트리 뷰어**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0dbe0-124">From the **Viewer** drop-down list, select **Microsoft Generic Content Tree Viewer**.</span></span>  
  
3.  <span data-ttu-id="0dbe0-125">**노드 캡션(고유 ID)** 창에서 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0dbe0-125">In the **Node Caption (Unique ID)** pane, click a node.</span></span>  
  
4.  <span data-ttu-id="0dbe0-126">**노드 정보** 창을 마우스 오른쪽 단추로 클릭한 다음 **모두 선택**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0dbe0-126">Right-click the **Node Details** pane and then select **Select All**.</span></span>  
  
5.  <span data-ttu-id="0dbe0-127">**노드 정보** 창을 마우스 오른쪽 단추로 다시 클릭한 다음 **복사**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0dbe0-127">Right-click the **Node Details** pane again and select **Copy**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dbe0-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0dbe0-128">See Also</span></span>  
 [<span data-ttu-id="0dbe0-129">마이닝 모델 뷰어 태스크 및 방법</span><span class="sxs-lookup"><span data-stu-id="0dbe0-129">Mining Model Viewer Tasks and How-tos</span></span>](mining-model-viewer-tasks-and-how-tos.md)  
  
  
