---
title: 마이닝 모델 배포 및 확장 (Excel 용 데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- manage
ms.assetid: 4c617375-6b01-4a71-9680-de0cbf2cff05
author: minewiskan
ms.author: owend
ms.openlocfilehash: dd2839144d4d1667da09830aaabd1ec3f17a9c21
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653046"
---
# <a name="deploying-and-scaling-mining-models-data-mining-add-ins-for-excel"></a><span data-ttu-id="8d1b8-102">마이닝 모델 배포 및 확장(Excel용 데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="8d1b8-102">Deploying and Scaling Mining Models (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="8d1b8-103">**모델 사용** 및 **관리** 그룹의 도구는 기존 마이닝 모델을 관리 하 고 검색 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d1b8-103">The tools in the **Model Usage** and **Management** group are provided to help you manage and browse existing mining models.</span></span> <span data-ttu-id="8d1b8-104">이러한 도구를 사용 하 여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 추가 기능을 사용 하 여 만든 모델 뿐만 아니라 인스턴스에 저장 된 모든 모델을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d1b8-104">You can use these tools to view any models that are stored on an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], not just those created using the add-ins.</span></span>  
  
 <span data-ttu-id="8d1b8-105">필요한 권한이 있는 경우 Excel을 벗어나지 않고도 기존 마이닝 모델 및 구조를 삭제, 수정, 이름 변경 또는 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d1b8-105">If you have the necessary permissions, you can delete, modify, rename, or process existing mining models and structures without leaving Excel.</span></span>  
  
## <a name="model-usage-toolbar"></a><span data-ttu-id="8d1b8-106">모델 사용 도구 모음</span><span class="sxs-lookup"><span data-stu-id="8d1b8-106">Model Usage Toolbar</span></span>  
  
### <a name="browse"></a><span data-ttu-id="8d1b8-107">찾아보기</span><span class="sxs-lookup"><span data-stu-id="8d1b8-107">Browse</span></span>  
 <span data-ttu-id="8d1b8-108">**찾아보기** 마법사를 사용 하 여 기존 데이터 마이닝 모델을 선택한 다음 여러 그래프 및 도구를 포함 하는 뷰어에서 모델을 보고 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d1b8-108">Use the **Browse** wizard to select an existing data mining model, and then view and explore the model in a viewer that contains multiple graphs and tools.</span></span>  
  
 <span data-ttu-id="8d1b8-109">자세한 내용은 [데이터 마이닝 추가 기능&#41;SQL Server Excel에서 모델 찾아보기 &#40;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8d1b8-109">For more information, see [Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md).</span></span>  
  
### <a name="document-model"></a><span data-ttu-id="8d1b8-110">모델 문서화</span><span class="sxs-lookup"><span data-stu-id="8d1b8-110">Document Model</span></span>  
 <span data-ttu-id="8d1b8-111">**모델 문서화** 를 클릭 하 여 만든 마이닝 구조 및 마이닝 모델에 대 한 보고서를 만드는 마법사를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d1b8-111">Click **Document Model** to start a wizard that creates a report of the mining structures and mining models that you have created.</span></span> <span data-ttu-id="8d1b8-112">기본 또는 고급 보고서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d1b8-112">You can create basic or advanced reports.</span></span> <span data-ttu-id="8d1b8-113">보고서는 열 및 모델 메타 데이터를 포함 하므로 작업을 문서화 하 고 모델의 변경 내용을 추적 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d1b8-113">The reports include column and model metadata, so are useful for documenting your work and tracking changes in models.</span></span>  
  
 <span data-ttu-id="8d1b8-114">자세한 내용은 [Excel 용 데이터 마이닝 추가 기능에 대 한 마이닝 모델 문서화 &#40;&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8d1b8-114">For more information, see [Documenting Mining Models &#40;Data Mining Add-ins for Excel&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md).</span></span>  
  
### <a name="query"></a><span data-ttu-id="8d1b8-115">쿼리</span><span class="sxs-lookup"><span data-stu-id="8d1b8-115">Query</span></span>  
 <span data-ttu-id="8d1b8-116">쿼리 **를 클릭 하** 여 **쿼리** 마법사를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d1b8-116">Click **Query** to start the **Query** wizard.</span></span> <span data-ttu-id="8d1b8-117">이 마법사는 기존 데이터 마이닝 모델에 대 한 예측 쿼리를 만드는 과정을 대화형으로 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d1b8-117">The wizard interactively walks you through the process of creating a prediction query against an existing data mining model.</span></span>  
  
 <span data-ttu-id="8d1b8-118">쿼리를 추가로 사용자 지정 하거나 마법사에 포함 되지 않은 쿼리를 작성 하려면 **고급** 단추를 클릭 하 여 **고급 편집기 데이터 마이닝 쿼리**를 시작 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d1b8-118">To further customize the query, or build queries not included in the wizard, just click the **Advanced** button to start the **Data Mining Query Advanced Editor**.</span></span>  
  
 <span data-ttu-id="8d1b8-119">자세한 내용은 [쿼리 &#40;SQL Server 데이터 마이닝 추가 기능&#41;](query-sql-server-data-mining-add-ins.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8d1b8-119">For more information, see [Query &#40;SQL Server Data Mining Add-ins&#41;](query-sql-server-data-mining-add-ins.md).</span></span>  
  
### <a name="data-mining-advanced-query-editor"></a><span data-ttu-id="8d1b8-120">데이터 마이닝 고급 쿼리 편집기</span><span class="sxs-lookup"><span data-stu-id="8d1b8-120">Data Mining Advanced Query Editor</span></span>  
 <span data-ttu-id="8d1b8-121">이 편집기에서 DMX (데이터 마이닝 확장) 템플릿을 사용 하 여 쿼리를 시작 하 고 입력, 출력, 알고리즘 및 매개 변수를 수정 하 여 사용자 지정 마이닝 모델, 마이닝 구조 또는 예측 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d1b8-121">In this editor, you can use Data Mining Extensions (DMX) templates to jumpstart a query, and then modify the inputs, outputs, algorithms, and parameters to create a custom mining model, mining structure, or prediction query.</span></span>  
  
 <span data-ttu-id="8d1b8-122">자세한 내용은 [고급 데이터 마이닝 쿼리 편집기](advanced-data-mining-query-editor.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="8d1b8-122">For more information, see [Advanced Data Mining Query Editor](advanced-data-mining-query-editor.md).</span></span>  
  
## <a name="management"></a><span data-ttu-id="8d1b8-123">관리</span><span class="sxs-lookup"><span data-stu-id="8d1b8-123">Management</span></span>  
 <span data-ttu-id="8d1b8-124">**모델 관리** 마법사를 사용 하 여 현재 연결의 기존 모델을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d1b8-124">Use the **Manage Models** wizard to view existing models on the current connection.</span></span> <span data-ttu-id="8d1b8-125">마이닝 모델 및 구조를 삭제, 이름 변경, 처리 또는 가져오거나 내보낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d1b8-125">You can also delete, rename, process, or import and export mining models and structures.</span></span>  
  
 <span data-ttu-id="8d1b8-126">자세한 내용은 [모델 관리 &#40;SQL Server 데이터 마이닝 추가 기능&#41;](manage-models-sql-server-data-mining-add-ins.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8d1b8-126">For more information, see [Manage Models &#40;SQL Server Data Mining Add-ins&#41;](manage-models-sql-server-data-mining-add-ins.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d1b8-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8d1b8-127">See Also</span></span>  
 <span data-ttu-id="8d1b8-128">[데이터 마이닝 모델 만들기](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="8d1b8-128">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 [<span data-ttu-id="8d1b8-129">Excel 용 데이터 마이닝 추가 기능에 대 한 예측 &#40;모델 유효성 검사 및 모델 사용&#41;</span><span class="sxs-lookup"><span data-stu-id="8d1b8-129">Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;</span></span>](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
  
