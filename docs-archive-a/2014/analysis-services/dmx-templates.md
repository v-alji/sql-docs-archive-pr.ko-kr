---
title: DMX 템플릿 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2a577e52-821d-4bd3-ba35-075a6be285c9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 79c8615933baf4fa3d80974daae91b4d1c7fa101
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659719"
---
# <a name="dmx-templates"></a><span data-ttu-id="ed3a4-102">DMX 템플릿</span><span class="sxs-lookup"><span data-stu-id="ed3a4-102">DMX Templates</span></span>
  <span data-ttu-id="ed3a4-103">데이터 마이닝 템플릿을 사용하면 정교한 쿼리를 신속하게 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-103">The data mining templates help you quickly build sophisticated queries.</span></span> <span data-ttu-id="ed3a4-104">DMX 쿼리의 일반 구문이 잘 설명되어 있더라도 템플릿을 사용하면 인수 및 데이터 원본을 클릭하고 가리켜서 쿼리를 보다 쉽게 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-104">Although the general syntax for DMX queries is well documented, using the templates makes it easier to build queries by clicking and pointing to arguments and data sources.</span></span>  
  
## <a name="using-the-templates"></a><span data-ttu-id="ed3a4-105">템플릿 사용</span><span class="sxs-lookup"><span data-stu-id="ed3a4-105">Using the Templates</span></span>  
  
1.  <span data-ttu-id="ed3a4-106">Excel용 데이터 마이닝 클라이언트에서 **쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-106">In the Data Mining Client for Excel, click **Query**.</span></span>  
  
2.  <span data-ttu-id="ed3a4-107">마법사 **시작** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-107">On the wizard **Start** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="ed3a4-108">페이지에서 **모델 선택**을 클릭하고 **고급**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-108">On the page, **Select Model**, click **Advanced**.</span></span>  
  
     <span data-ttu-id="ed3a4-109">**팁:** 모델에서 예측 쿼리를 만들려면 모델을 먼저 선택한 후 **고급**을 클릭하여 템플릿에 모델 이름을 미리 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-109">**Tip:** If you are going to create a prediction query on a model, you can select the model first, and then click **Advanced**, to prepopulate the template with the model name.</span></span>  
  
4.  <span data-ttu-id="ed3a4-110">**데이터 마이닝 고급 쿼리 편집기**에서 **DMX 템플릿**을 클릭하고 템플릿을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-110">In the **Data Mining Advanced Query Editor**, click **DMX Templates**, and select a template.</span></span>  
  
5.  <span data-ttu-id="ed3a4-111">Enter 키를 눌러서 템플릿을 DMX 쿼리 창에 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-111">Press ENTER to load the template into the DMX Query pane.</span></span>  
  
6.  <span data-ttu-id="ed3a4-112">계속해서 템플릿에서 링크를 클릭하고 대화 상자가 표시되면 적합한 출력, 모델 또는 매개 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-112">Continue clicking the links in the template, and as the dialog box appears, select an appropriate output, model, or parameter.</span></span>  
  
     <span data-ttu-id="ed3a4-113">예측 쿼리의 경우 입력 데이터 세트를 먼저 선택한 다음, 열을 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-113">For prediction queries, choose the input dataset first, and then map the columns.</span></span>  
  
7.  <span data-ttu-id="ed3a4-114">**쿼리 편집** 을 클릭해서 텍스트 편집기 보기로 전환하고 쿼리를 수동으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-114">Click **Edit Query** to switch to text editor view and manually change the query.</span></span>  
  
     <span data-ttu-id="ed3a4-115">하지만 쿼리 편집기에서 작업할 때 보기를 전환하면 이전 보기에 있던 정보가 지워지므로 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-115">Be aware, however, that if you switch views when working in the query editor, any information that you had in the previous view will be cleared.</span></span> <span data-ttu-id="ed3a4-116">보기를 변경하기 전에 DMX 문을 복사한 다음 별도의 파일로 붙여 넣어 작업 내용을 저장하십시오.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-116">Before changing views, save your work by copying and pasting the DMX statements to a separate file.</span></span>  
  
8.  <span data-ttu-id="ed3a4-117">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-117">Click **Finish**.</span></span> <span data-ttu-id="ed3a4-118">**대상 선택** 대화 상자에서 결과를 저장하려는 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-118">In the **Choose Destination** dialog  box, specify where you want the result saved.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
> [!NOTE]  
>  <span data-ttu-id="ed3a4-119">문을 성공적으로 실행한 경우 서버로 전송한 DMX 문은 **추적** 창에도 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-119">If you executed a statement successfully, the DMX statement that you sent to the server is also recorded in the **Trace** window.</span></span> <span data-ttu-id="ed3a4-120">추적 기능을 사용 하는 방법에 대 한 자세한 내용은 [추적 &#40;Excel 용 데이터 마이닝 클라이언트&#41;](trace-data-mining-client-for-excel.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-120">For more information about how to use the Trace feature, see [Trace &#40;Data Mining Client for Excel&#41;](trace-data-mining-client-for-excel.md).</span></span>  
  
 <span data-ttu-id="ed3a4-121">데이터 마이닝 고급 쿼리 편집기를 사용 하는 방법에 대 한 자세한 내용은 [쿼리 &#40;SQL Server 데이터 마이닝 추가 기능&#41;](query-sql-server-data-mining-add-ins.md) 및 [고급 데이터 마이닝 쿼리 편집기](advanced-data-mining-query-editor.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-121">For more information about how to use the Data Mining Advanced Query Editor, see [Query &#40;SQL Server Data Mining Add-ins&#41;](query-sql-server-data-mining-add-ins.md) and [Advanced Data Mining Query Editor](advanced-data-mining-query-editor.md).</span></span>  
  
## <a name="list-of-dmx-templates"></a><span data-ttu-id="ed3a4-122">DMX 템플릿 목록</span><span class="sxs-lookup"><span data-stu-id="ed3a4-122">List of DMX Templates</span></span>  
 <span data-ttu-id="ed3a4-123">다음 DMX 템플릿은 Excel용 데이터 마이닝 클라이언트에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-123">The following DMX templates are included in the Data Mining Client for Excel.</span></span>  
  
 <span data-ttu-id="ed3a4-124">**예측**</span><span class="sxs-lookup"><span data-stu-id="ed3a4-124">**Prediction**</span></span>  
  
 <span data-ttu-id="ed3a4-125">이러한 템플릿을 사용하면 중첩된 테이블 또는 외부 데이터 원본을 사용하는 쿼리와 같이 추가 기능의 마법사에서 지원되지 않는 쿼리를 포함해서 고급 예측 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-125">Use these templates to create advanced prediction queries, including queries not supported by the wizards in the add-ins, such as queries that use nested tables or external data sources.</span></span>  
  
-   <span data-ttu-id="ed3a4-126">필터링된 예측</span><span class="sxs-lookup"><span data-stu-id="ed3a4-126">Filtered predictions</span></span>  
  
-   <span data-ttu-id="ed3a4-127">필터링된 중첩 예측</span><span class="sxs-lookup"><span data-stu-id="ed3a4-127">Filtered nested predictions</span></span>  
  
-   <span data-ttu-id="ed3a4-128">중첩된 예측</span><span class="sxs-lookup"><span data-stu-id="ed3a4-128">Nested predictions</span></span>  
  
-   <span data-ttu-id="ed3a4-129">단일 예측</span><span class="sxs-lookup"><span data-stu-id="ed3a4-129">Singleton predictions</span></span>  
  
-   <span data-ttu-id="ed3a4-130">표준 예측</span><span class="sxs-lookup"><span data-stu-id="ed3a4-130">Standard predictions</span></span>  
  
-   <span data-ttu-id="ed3a4-131">시계열 예측</span><span class="sxs-lookup"><span data-stu-id="ed3a4-131">Time series predictions</span></span>  
  
-   <span data-ttu-id="ed3a4-132">상위 예측 쿼리</span><span class="sxs-lookup"><span data-stu-id="ed3a4-132">TOP prediction query</span></span>  
  
-   <span data-ttu-id="ed3a4-133">중첩 테이블의 상위 예측 쿼리</span><span class="sxs-lookup"><span data-stu-id="ed3a4-133">TOP prediction query on nested table</span></span>  
  
 <span data-ttu-id="ed3a4-134">**만들기**</span><span class="sxs-lookup"><span data-stu-id="ed3a4-134">**Create**</span></span>  
  
 <span data-ttu-id="ed3a4-135">이러한 템플릿을 사용하면 사용자 지정 모델 또는 데이터 구조를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-135">Use these templates to build custom models or data structures.</span></span> <span data-ttu-id="ed3a4-136">마법사에서 지 원하는 모델만 사용할 수 있는 것은 아닙니다 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . 플러그 인 알고리즘을 포함 하 여 연결 된 인스턴스에서 지원 되는 데이터 마이닝 알고리즘을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-136">You are not limited to the models supported by the wizards - you can use any data mining algorithm supported by the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you are connected to, including plug-in algorithms.</span></span>  
  
-   <span data-ttu-id="ed3a4-137">마이닝 모델</span><span class="sxs-lookup"><span data-stu-id="ed3a4-137">Mining model</span></span>  
  
-   <span data-ttu-id="ed3a4-138">마이닝 구조</span><span class="sxs-lookup"><span data-stu-id="ed3a4-138">Mining structure</span></span>  
  
-   <span data-ttu-id="ed3a4-139">홀드아웃이 있는 마이닝 구조</span><span class="sxs-lookup"><span data-stu-id="ed3a4-139">Mining structure with holdout</span></span>  
  
-   <span data-ttu-id="ed3a4-140">임시 모델</span><span class="sxs-lookup"><span data-stu-id="ed3a4-140">Temporary model</span></span>  
  
-   <span data-ttu-id="ed3a4-141">임시 구조</span><span class="sxs-lookup"><span data-stu-id="ed3a4-141">Temporary structure</span></span>  
  
 <span data-ttu-id="ed3a4-142">**모델 속성**</span><span class="sxs-lookup"><span data-stu-id="ed3a4-142">**Model Properties**</span></span>  
  
 <span data-ttu-id="ed3a4-143">이러한 템플릿을 사용하면 모델 및 학습 집합에 대한 메타데이터를 가져오는 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-143">Use these templates to create queries that get metadata about the model and the training set.</span></span> <span data-ttu-id="ed3a4-144">또한 모델 콘텐츠에서 세부 정보를 검색하거나 학습 데이터의 통계적 프로필을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-144">You can also retrieve details from the model content, or get a statistical profile of the training data.</span></span>  
  
-   <span data-ttu-id="ed3a4-145">마이닝 모델 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="ed3a4-145">Mining model content</span></span>  
  
-   <span data-ttu-id="ed3a4-146">최소 및 최대 열 값</span><span class="sxs-lookup"><span data-stu-id="ed3a4-146">Minimum and maximum column values</span></span>  
  
-   <span data-ttu-id="ed3a4-147">마이닝 구조 테스트/학습 사례</span><span class="sxs-lookup"><span data-stu-id="ed3a4-147">Mining structure test/training cases</span></span>  
  
-   <span data-ttu-id="ed3a4-148">불연속 열 값</span><span class="sxs-lookup"><span data-stu-id="ed3a4-148">Discrete column values</span></span>  
  
 <span data-ttu-id="ed3a4-149">**관리**</span><span class="sxs-lookup"><span data-stu-id="ed3a4-149">**Management**</span></span>  
  
 <span data-ttu-id="ed3a4-150">이러한 템플릿을 사용하면 모델 가져오기 및 내보내기, 모델 삭제, 모델 또는 데이터 구조 지우기 등 DMX에서 지원되는 모든 관리 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-150">Use these templates to perform any management task supported by DMX, which includes importing and exporting models, deleting models, and clearing models or data structures.</span></span>  
  
-   <span data-ttu-id="ed3a4-151">마이닝 모델 지우기</span><span class="sxs-lookup"><span data-stu-id="ed3a4-151">Clear mining model</span></span>  
  
-   <span data-ttu-id="ed3a4-152">구조 및 모델 지우기</span><span class="sxs-lookup"><span data-stu-id="ed3a4-152">Clear structure and models</span></span>  
  
-   <span data-ttu-id="ed3a4-153">마이닝 구조 지우기</span><span class="sxs-lookup"><span data-stu-id="ed3a4-153">Clear mining structure</span></span>  
  
-   <span data-ttu-id="ed3a4-154">마이닝 모델 삭제</span><span class="sxs-lookup"><span data-stu-id="ed3a4-154">Delete mining model</span></span>  
  
-   <span data-ttu-id="ed3a4-155">마이닝 구조 삭제</span><span class="sxs-lookup"><span data-stu-id="ed3a4-155">Delete mining structure</span></span>  
  
-   <span data-ttu-id="ed3a4-156">마이닝 모델 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="ed3a4-156">Rename mining model</span></span>  
  
-   <span data-ttu-id="ed3a4-157">마이닝 구조 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="ed3a4-157">Rename mining structure</span></span>  
  
-   <span data-ttu-id="ed3a4-158">마이닝 모델 학습</span><span class="sxs-lookup"><span data-stu-id="ed3a4-158">Train mining model</span></span>  
  
-   <span data-ttu-id="ed3a4-159">중첩 마이닝 구조 학습</span><span class="sxs-lookup"><span data-stu-id="ed3a4-159">Train nested mining structure</span></span>  
  
-   <span data-ttu-id="ed3a4-160">마이닝 구조 학습</span><span class="sxs-lookup"><span data-stu-id="ed3a4-160">Train mining structure</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="ed3a4-161">요구 사항</span><span class="sxs-lookup"><span data-stu-id="ed3a4-161">Requirements</span></span>  
 <span data-ttu-id="ed3a4-162">사용하는 템플릿에 따라 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 서버에 액세스하고 쿼리를 실행하는 데 관리 권한이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed3a4-162">Depending on which template you are using, you might need administrative permissions to access the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server and execute the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed3a4-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ed3a4-163">See Also</span></span>  
 [<span data-ttu-id="ed3a4-164">데이터 마이닝 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="ed3a4-164">Creating a Data Mining Model</span></span>](creating-a-data-mining-model.md)  
  
  
