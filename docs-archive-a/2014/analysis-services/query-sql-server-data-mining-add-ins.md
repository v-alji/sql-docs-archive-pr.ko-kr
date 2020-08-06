---
title: 쿼리 (SQL Server 데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- queries [data mining]
- Data Mining Query Advanced Editor
- query builder [data mining]
- DMX
ms.assetid: 16af4a6f-18d4-496a-a304-7a13aa32ee76
author: minewiskan
ms.author: owend
ms.openlocfilehash: 90794aae8a3d664d47ab251ffdd954f22d48f992
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738920"
---
# <a name="query-sql-server-data-mining-add-ins"></a><span data-ttu-id="699f5-102">쿼리(SQL Server 데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="699f5-102">Query (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="699f5-103">![데이터 마이닝 리본, 모델 쿼리 단추](media/dmc-query.gif "데이터 마이닝 리본, 모델 쿼리 단추")</span><span class="sxs-lookup"><span data-stu-id="699f5-103">![Query Model button, Data Mining ribbon](media/dmc-query.gif "Query Model button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="699f5-104">**쿼리** 마법사를 사용하여 기존 마이닝 모델과의 상호 작용을 통해 Excel 테이블, Excel 범위 또는 다른 데이터 원본에 있는 데이터를 기반으로 예측을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="699f5-104">The **Query** wizard helps you interact with existing mining models to make predictions based on data in an Excel table, an Excel range, or another data source.</span></span> <span data-ttu-id="699f5-105">추세 예측을 위해 새 데이터를 기존 모델에 적용하는 프로세스를 *예측 쿼리*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="699f5-105">The process of applying new data to an existing model to predict trends is called a *prediction query*.</span></span>  
  
 <span data-ttu-id="699f5-106">또한 **쿼리** 마법사는 데이터 마이닝 모델 만들기 또는 수정, 사용자 지정 쿼리 생성, 다른 도구에서 지원되지 않는 구조(예: 중첩된 데이터 세트) 사용을 위한 고급 편집기를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="699f5-106">The **Query** wizard also provides an advanced editor for creating or modifying data mining models, for generating custom queries, or for working with structures not supported in the other tools, such as nested datasets.</span></span>  
  
-   <span data-ttu-id="699f5-107">텍스트 편집기를 사용 하 여 다른 곳에서 만든 DMX (Data 마이닝 확장) 문에 입력 하거나 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="699f5-107">Use the text editor to type or paste in the Data Mining Extensions (DMX) statements you've created elsewhere.</span></span>  
  
-   <span data-ttu-id="699f5-108">대화형 쿼리 작성기를 사용하여 템플릿과 대화 상자를 통해 사용자 지정 DMX 문을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="699f5-108">Use the interactive Query Builder to compose a custom DMX statement with the help of templates and dialog boxes.</span></span>  
  
-   <span data-ttu-id="699f5-109">DMX 문을 만들어 마이닝 모델과 구조를 관리하거나 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="699f5-109">Create DMX statements to manage or back up mining models and structures.</span></span>  
  
## <a name="using-the-query-wizard"></a><span data-ttu-id="699f5-110">쿼리 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="699f5-110">Using the Query Wizard</span></span>  
  
1.  <span data-ttu-id="699f5-111">먼저 입력으로 사용할 데이터 원본을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="699f5-111">First, you must specify a source for the data to use as input.</span></span> <span data-ttu-id="699f5-112">기존 Excel 테이블 또는 범위에 있는 데이터를 사용하거나 SQL 문을 지정하여 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="699f5-112">You can use data in an existing Excel table or range, or you can specify a SQL statement to retrieve the data.</span></span>  
  
2.  <span data-ttu-id="699f5-113">그러면 마법사는 연결된 서버에 있는 데이터 마이닝 모델 목록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="699f5-113">Next, the wizard presents a list of data mining models on the server to which you are connected.</span></span> <span data-ttu-id="699f5-114">원하는 모델을 알고 있고 데이터 마이닝에 익숙하다면 **고급** 을 클릭하여 **데이터 마이닝 고급 쿼리 편집기**를 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="699f5-114">If you know the model you want and are familiar with data mining, you can also click **Advanced** to open the **Data Mining Advanced Query Editor**.</span></span>  
  
3.  <span data-ttu-id="699f5-115">선택한 모델 유형에 따라 평가할 데이터가 포함된 열을 지정하고 입력 데이터 열과 모델 열 간의 매핑을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="699f5-115">Depending on the type of model that you choose, you must specify the column that contains the data to be evaluated, and define mappings between the input data columns and the model columns.</span></span> <span data-ttu-id="699f5-116">선택한 알고리즘에 따라 모델의 다른 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="699f5-116">Depending on the algorithm you choose, you can set other properties on the model.</span></span>  
  
4.  <span data-ttu-id="699f5-117">마지막으로 마법사는 하나 이상의 예측을 선택하고 결과를 저장할 대상을 지정하는 능력을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="699f5-117">Finally, the wizard also gives you the ability to choose one or more predictions, and specify a destination in which to store the results.</span></span>  
  
 <span data-ttu-id="699f5-118">언제든지 **고급** 을 클릭하여 DMX 문의 각 부분을 더 세부적으로 제어할 수 있는 **데이터 마이닝 고급 쿼리 편집기**로 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="699f5-118">At any time, you can click **Advanced** to switch to the **Data Mining Advanced Query Editor**, which gives you more control over each part of the DMX statement.</span></span> <span data-ttu-id="699f5-119">고급 쿼리 편집 도구를 사용 하는 방법에 대 한 자세한 내용은 [고급 데이터 마이닝 쿼리 편집기](advanced-data-mining-query-editor.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="699f5-119">For more information about how to use the advanced query editing tools, see [Advanced Data Mining Query Editor](advanced-data-mining-query-editor.md).</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="699f5-120">요구 사항</span><span class="sxs-lookup"><span data-stu-id="699f5-120">Requirements</span></span>  
 <span data-ttu-id="699f5-121">**쿼리** 마법사를 사용하려면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="699f5-121">To use the **Query** wizard, you must be connected to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="699f5-122">또한 서버에는 적절한 유형의 데이터 마이닝 모델이 최소 한 개 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="699f5-122">Moreover, the server must contain at least one data mining model of an appropriate type.</span></span> <span data-ttu-id="699f5-123">사용할 수 있는 마이닝 모델이 없는 경우 Excel용 데이터 마이닝 클라이언트에서 제공하는 마법사를 사용하여 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="699f5-123">If no mining models are available, you can create one by using the wizards provided in the Data Mining Client for Excel.</span></span> <span data-ttu-id="699f5-124">마법사를 사용 하 여 새 마이닝 모드를 만드는 방법에 대 한 자세한 내용은 [데이터 마이닝 모델 만들기](creating-a-data-mining-model.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="699f5-124">For information about how to create a new mining mode by using a wizard, see [Creating a Data Mining Model](creating-a-data-mining-model.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="699f5-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="699f5-125">See Also</span></span>  
 <span data-ttu-id="699f5-126">[Excel 용 데이터 마이닝 추가 기능 &#40;마이닝 모델 배포 및 확장&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="699f5-126">[Deploying and Scaling Mining Models &#40;Data Mining Add-ins for Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md) </span></span>  
 [<span data-ttu-id="699f5-127">Excel 용 데이터 마이닝 클라이언트 &#40;SQL Server 데이터 마이닝 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="699f5-127">Data Mining Client for Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](data-mining-client-for-excel-sql-server-data-mining-add-ins.md)  
  
  
