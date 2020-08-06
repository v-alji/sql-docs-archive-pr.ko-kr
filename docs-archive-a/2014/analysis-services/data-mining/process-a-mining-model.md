---
title: 마이닝 모델 처리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], processing
ms.assetid: c2204472-c500-47a5-9afa-7ce2ca78b233
author: minewiskan
ms.author: owend
ms.openlocfilehash: c2fed5d72c677dc175f4c9681096d1859b30d829
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734608"
---
# <a name="process-a-mining-model"></a><span data-ttu-id="da174-102">마이닝 모델 처리</span><span class="sxs-lookup"><span data-stu-id="da174-102">Process a Mining Model</span></span>
  <span data-ttu-id="da174-103">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에 있는 데이터 마이닝 디자이너의 마이닝 모델 탭에서는 마이닝 구조와 연관된 특정 마이닝 모델을 처리하거나 구조와 연관된 모든 모델을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da174-103">In the Mining Models tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you can either process a specific mining model that is associated with a mining structure or you can process all the models that are associated with the structure.</span></span>  
  
 <span data-ttu-id="da174-104">다음 도구를 사용하여 마이닝 모델을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da174-104">You can process a mining model by using the following tools:</span></span>  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
 <span data-ttu-id="da174-105">XMLA Process 명령도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da174-105">You can also use an XMLA Process command.</span></span> <span data-ttu-id="da174-106">자세한 내용은 [도구 및 처리 방법 &#40;Analysis Services&#41;](../multidimensional-models/tools-and-approaches-for-processing-analysis-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="da174-106">For more information, see  [Tools and Approaches for Processing &#40;Analysis Services&#41;](../multidimensional-models/tools-and-approaches-for-processing-analysis-services.md).</span></span>  
  
### <a name="process-a-single-mining-model-using-sql-server-data-tools"></a><span data-ttu-id="da174-107">SQL Server Data Tools를 사용하여 단일 마이닝 모델 처리</span><span class="sxs-lookup"><span data-stu-id="da174-107">Process a single mining model using SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="da174-108">데이터 마이닝 디자이너의 **마이닝 모델** 탭에서 표에 있는 하나 이상의 모델 열에서 마이닝 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="da174-108">On the **Mining Models** tab of Data Mining Designer, select a mining model from the one or more columns of models in the grid.</span></span>  
  
2.  <span data-ttu-id="da174-109">**마이닝 모델** 메뉴에서 **모델 처리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="da174-109">On the **Mining Model** menu, select **Process Model**.</span></span>  
  
     <span data-ttu-id="da174-110">마이닝 구조를 변경한 경우 모델을 처리하기 전에 구조를 다시 배포할지 묻는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="da174-110">If you made changes to the mining structure, you will be prompted to redeploy the structure before processing the model.</span></span> <span data-ttu-id="da174-111">**예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da174-111">Click **Yes**.</span></span>  
  
3.  <span data-ttu-id="da174-112">**마이닝 모델 처리 \<model> -** 대화 상자에서 **실행**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="da174-112">In the **Processing Mining Model - \<model>** dialog box, click **Run**.</span></span>  
  
     <span data-ttu-id="da174-113">**처리 진행률** 대화 상자가 열리고 모델 처리 세부 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="da174-113">The **Process Progress** dialog box opens to show the details of model processing.</span></span>  
  
4.  <span data-ttu-id="da174-114">모델이 성공적으로 처리되면 **처리 진행률** 대화 상자에서 **닫기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da174-114">After the model has successfully completed processing, click **Close** in the **Process Progress** dialog box.</span></span>  
  
5.  <span data-ttu-id="da174-115">**마이닝 모델 처리 \<model> -** 대화 상자에서 **닫기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="da174-115">Click **Close** in the **Processing Mining Model - \<model>** dialog box.</span></span>  
  
 <span data-ttu-id="da174-116">마이닝 구조 및 선택한 마이닝 모델만 처리되었습니다.</span><span class="sxs-lookup"><span data-stu-id="da174-116">Only the mining structure and the selected mining model have been processed.</span></span>  
  
### <a name="process-all-mining-models-that-are-associated-with-a-mining-structure"></a><span data-ttu-id="da174-117">마이닝 구조와 연관된 모든 마이닝 모델 처리</span><span class="sxs-lookup"><span data-stu-id="da174-117">Process all mining models that are associated with a mining structure</span></span>  
  
1.  <span data-ttu-id="da174-118">데이터 마이닝 디자이너에 있는 **마이닝 모델** 탭의 **마이닝 모델** 메뉴에서 **마이닝 구조 및 모든 모델 처리** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="da174-118">On the **Mining Models** tab of Data Mining Designer, select **Process Mining Structure and All Models** from the **Mining Model** menu.</span></span>  
  
2.  <span data-ttu-id="da174-119">마이닝 구조를 변경한 경우 모델을 처리하기 전에 구조를 다시 배포할지 묻는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="da174-119">If you made changes to the mining structure, you will be prompted to redeploy the structure before processing the models.</span></span> <span data-ttu-id="da174-120">**예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da174-120">Click **Yes**.</span></span>  
  
3.  <span data-ttu-id="da174-121">**마이닝 구조 처리 \<structure> -** 대화 상자에서 **실행**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="da174-121">In the **Processing Mining Structure - \<structure>** dialog box, click **Run**.</span></span>  
  
4.  <span data-ttu-id="da174-122">**처리 진행률** 대화 상자가 열리고 모델 처리 세부 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="da174-122">The **Process Progress** dialog box opens to show the details of model processing.</span></span>  
  
5.  <span data-ttu-id="da174-123">모델이 성공적으로 처리되면 **처리 진행률** 대화 상자에서 **닫기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da174-123">After the models have successfully completed processing, click **Close** in the **Process Progress** dialog box.</span></span>  
  
6.  <span data-ttu-id="da174-124">\*\*처리 \<model> \*\* 대화 상자에서 **닫기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="da174-124">Click **Close** in the **Processing \<model>** dialog box.</span></span>  
  
 <span data-ttu-id="da174-125">마이닝 구조 및 모든 연관된 마이닝 모델이 처리되었습니다.</span><span class="sxs-lookup"><span data-stu-id="da174-125">The mining structure and all the associated mining models have been processed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da174-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="da174-126">See Also</span></span>  
 [<span data-ttu-id="da174-127">마이닝 모델 태스크 및 방법</span><span class="sxs-lookup"><span data-stu-id="da174-127">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
