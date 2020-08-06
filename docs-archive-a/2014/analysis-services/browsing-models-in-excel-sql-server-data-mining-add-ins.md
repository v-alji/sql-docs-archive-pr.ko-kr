---
title: Excel에서 모델 찾아보기 (SQL Server 데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- browse models
- mining models, viewing
ms.assetid: a8cca1d7-602a-449a-875c-99da564965bc
author: minewiskan
ms.author: owend
ms.openlocfilehash: c992f1f61112478a85276b6596da0137ccd5c9be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648092"
---
# <a name="browsing-models-in-excel-sql-server-data-mining-add-ins"></a><span data-ttu-id="3e2da-102">Excel에서 모델 찾아보기(SQL Server 데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="3e2da-102">Browsing Models in Excel (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="3e2da-103">![데이터 마이닝 리본의 모델 찾아보기 단추](media/dmc-browse.gif "데이터 마이닝 리본의 모델 찾아보기 단추")</span><span class="sxs-lookup"><span data-stu-id="3e2da-103">![Browse Model button in Data Mining ribbon](media/dmc-browse.gif "Browse Model button in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="3e2da-104">모델을 시각적으로 탐색하는 것은 일반적으로 분석을 통해 발견된 규칙과 관계를 가장 빠르고 쉽게 이해할 수 있는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="3e2da-104">Visually exploring the model is usually the fastest and easiest way to get an understanding of the rules and relationships discovered by analysis.</span></span> <span data-ttu-id="3e2da-105">Excel용 데이터 마이닝 클라이언트를 사용하면 현재 Excel 세션 중에 만들어진 임시 모델과 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 저장된 모델을 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e2da-105">By using the Data Mining Client for Excel, you can browse both temporary models created during the current Excel session, and models stored in an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="3e2da-106">모델을 찾아보기 위해 사용 가능한 모델 목록에서 모델 및 관련 구조를 선택하면 추가 기능에 의해 해당 데이터 마이닝 알고리즘에 적합한 뷰어가 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e2da-106">To browse a model, you select a model and its associated structure from a list of available models, and the add-in automatically picks the viewer that is appropriate for that data mining algorithm.</span></span> <span data-ttu-id="3e2da-107">가장 관심 있는 추세를 탐색하고 완성된 데이터 마이닝 모델을 필터링할 수 있으며 그래프와 데이터를 Excel 또는 Visio에 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e2da-107">You can drill into the most interesting trends, filter the completed data mining model, and copy graphs and data to Excel or to Visio.</span></span>  
  
## <a name="using-the-browse-model-wizard"></a><span data-ttu-id="3e2da-108">모델 찾아보기 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="3e2da-108">Using the Browse Model Wizard</span></span>  
  
1.  <span data-ttu-id="3e2da-109">**데이터 마이닝** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e2da-109">Click the **Data Mining** tab.</span></span>  
  
2.  <span data-ttu-id="3e2da-110">**모델 사용** 그룹에서 **찾아보기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e2da-110">In the **Model Usage** group, click **Browse**.</span></span>  
  
3.  <span data-ttu-id="3e2da-111">**모델 선택** 대화 상자의 목록에서 마이닝 모델을 선택 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e2da-111">In the **Select Model** dialog box, choose a mining model from the list, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="3e2da-112">마법사에서 선택한 모델 유형에 적합 한 **찾아보기** 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="3e2da-112">The wizard opens a **Browse** window that is appropriate for the type of model that you selected.</span></span>  
  
## <a name="list-of-data-mining-viewers"></a><span data-ttu-id="3e2da-113">데이터 마이닝 뷰어 목록</span><span class="sxs-lookup"><span data-stu-id="3e2da-113">List of Data Mining Viewers</span></span>  
 <span data-ttu-id="3e2da-114">모델을 만들 때 사용한 데이터 마이닝 알고리즘에 따라 **찾아보기** 창이 약간 다르게 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e2da-114">Depending on the data mining algorithm that you used when you created the model, the **Browse** window will look a bit different.</span></span> <span data-ttu-id="3e2da-115">이 창에는 결과 해석에 도움이 되는 그래프, 추가 정보가 포함된 범례 및 데이터와 상호 작용하기 위한 컨트롤이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e2da-115">It can include graphs to help interpret the results, legends that contain additional detail, and controls for interacting with the data.</span></span>  
  
 <span data-ttu-id="3e2da-116">다음 항목에서는 복잡한 그래프 해석을 위한 팁을 비롯한 각 뷰어 사용 방법과 결과를 변경, 복사 또는 사용하는 방법에 대한 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3e2da-116">The following topics provide guidance in how to use each of the viewers, including tips on interpreting the complex graphs, and how to change, copy, or work with the results.</span></span>  
  
 [<span data-ttu-id="3e2da-117">연결 규칙 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="3e2da-117">Browsing an Association Rules Model</span></span>](browsing-an-association-rules-model.md)  
  
 [<span data-ttu-id="3e2da-118">클러스터링 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="3e2da-118">Browsing a Clustering Model</span></span>](browsing-a-clustering-model.md)  
  
 [<span data-ttu-id="3e2da-119">의사 결정 트리 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="3e2da-119">Browsing a Decision Trees Model</span></span>](browsing-a-decision-trees-model.md)  
  
 [<span data-ttu-id="3e2da-120">예측 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="3e2da-120">Browsing a Forecasting Model</span></span>](browsing-a-forecasting-model.md)  
  
 [<span data-ttu-id="3e2da-121">Naive Bayes 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="3e2da-121">Browsing a Naive Bayes Model</span></span>](browsing-a-naive-bayes-model.md)  
  
 [<span data-ttu-id="3e2da-122">신경망 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="3e2da-122">Browsing a Neural Network Model</span></span>](browsing-a-neural-network-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="3e2da-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3e2da-123">See Also</span></span>  
 <span data-ttu-id="3e2da-124">[Visio에서 데이터 마이닝 모델 보기 &#40;데이터 마이닝 추가 기능&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md) </span><span class="sxs-lookup"><span data-stu-id="3e2da-124">[Viewing Data Mining Models in Visio &#40;Data Mining Add-ins&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md) </span></span>  
 [<span data-ttu-id="3e2da-125">모델 관리 &#40;SQL Server 데이터 마이닝 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="3e2da-125">Manage Models &#40;SQL Server Data Mining Add-ins&#41;</span></span>](manage-models-sql-server-data-mining-add-ins.md)  
  
  
