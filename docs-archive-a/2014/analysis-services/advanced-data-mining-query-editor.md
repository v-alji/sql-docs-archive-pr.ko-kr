---
title: 고급 데이터 마이닝 쿼리 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 27e7fc46-689d-43a4-9647-1c27d182bdd6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2aadf4df75b1ccf6001ad8e97d589ce5666f56ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648236"
---
# <a name="advanced-data-mining-query-editor"></a><span data-ttu-id="b4b99-102">고급 데이터 마이닝 쿼리 편집기</span><span class="sxs-lookup"><span data-stu-id="b4b99-102">Advanced Data Mining Query Editor</span></span>
  <span data-ttu-id="b4b99-103">**데이터 마이닝 쿼리 고급 편집기** 는 사용자 지정 모델과 쿼리를 작성 하는 데 도움이 되는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-103">The **Data Mining Query Advanced Editor** is a tool to help you build custom models and queries.</span></span>  
  
 <span data-ttu-id="b4b99-104">이 편집기는 클릭하여 연결할 수 있는 링크와 함께 템플릿 집합을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-104">The editor provides a set of templates with clickable links.</span></span> <span data-ttu-id="b4b99-105">각 링크를 클릭한 다음 대화 상자를 사용하여 개체 또는 값을 선택하고 복잡한 DMX(Data Mining Extensions) 문을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-105">Just click each link, and use the dialog boxes to select objects or values and build complex Data Mining Extensions (DMX) statements.</span></span> <span data-ttu-id="b4b99-106">뷰를 텍스트 편집 모델로 전환하여 DMX 문을 수동으로 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-106">You can switch the view to text editing model to modify the DMX statement manually.</span></span>  
  
 <span data-ttu-id="b4b99-107">**고급 편집기 데이터 마이닝 쿼리**를 가져오려면 **쿼리** 를 클릭 한 다음 **고급**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-107">To get to the **Data Mining Query Advanced Editor**, click **Query** and then click **Advanced**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="b4b99-108">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="b4b99-108">UI element list</span></span>  
 <span data-ttu-id="b4b99-109">**DMX 쿼리 창**</span><span class="sxs-lookup"><span data-stu-id="b4b99-109">**DMX Query pane**</span></span>  
 <span data-ttu-id="b4b99-110">여기에서 현재 DMX 문을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-110">Here you can see the current DMX statement.</span></span>  
  
 <span data-ttu-id="b4b99-111">현재 DMX 문을 복사하려면 창을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-111">Right-click in the pane to copy the current DMX statement.</span></span>  
  
 <span data-ttu-id="b4b99-112">문의 강조 표시된 부분을 클릭하여 해당 절과 관련된 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-112">You can click any highlighted part of the statement to get options specific to that clause.</span></span> <span data-ttu-id="b4b99-113">예를 들어 출력을 삭제, 추가 또는 편집 하려면 링크를 마우스 오른쪽 단추로 클릭 **\<Output>** 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-113">For example, to delete, add, or edit an output, right-click the **\<Output>** link.</span></span>  
  
 <span data-ttu-id="b4b99-114">**쿼리 편집/쿼리 작성기**</span><span class="sxs-lookup"><span data-stu-id="b4b99-114">**Edit Query/Query Builder**</span></span>  
 <span data-ttu-id="b4b99-115">이 단추를 사용 하 여 직접 DMX 문을 작성할 수 있는 텍스트 편집기 간에 편집기를 전환할 수 있습니다. **쿼리 작성기**은 DMX 문을 작성 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-115">Use this button to switch the editor between a text editor, where you can write DMX statements directly; and the **Query Builder**, which helps you build a DMX statement.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b4b99-116">**경고:** 쿼리를 실행 하기 전에 보기를 전환 하는 경우 일부 변경 내용이 손실 될 수 있다는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-116">**Warning:** If you switch views before the query has been run, a message appears stating that you might lose some changes.</span></span> <span data-ttu-id="b4b99-117">DMX 문이 유효 하면 대부분의 경우 **쿼리 작성기** 이 이러한 변경 내용을 성공적으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-117">If the DMX statement is valid, in many cases the **Query Builder** might successfully convert these changes.</span></span> <span data-ttu-id="b4b99-118">그러나 특히 복잡한 DMX 문을 작성한 경우 뷰를 전환하기 전에 반드시 작업을 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-118">However, if you have built a particularly complex DMX statement, you should definitely save your work before switching views.</span></span>  
  
 <span data-ttu-id="b4b99-119">**DMX 템플릿**</span><span class="sxs-lookup"><span data-stu-id="b4b99-119">**DMX Templates**</span></span>  
 <span data-ttu-id="b4b99-120">DMX 예제가 포함된 템플릿 목록에서 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-120">Click and select from a list of templates that contain DMX examples.</span></span> <span data-ttu-id="b4b99-121">템플릿은 중첩 테이블을 사용하는 쿼리, 모델을 관리하기 위한 DMX 문을 비롯하여 필요할 수 있는 모든 유형의 모델 또는 예측 쿼리에 대한 것을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-121">The templates provide just about every type of model or prediction query that you might need, including queries that use nested tables, and DMX statements to manage models.</span></span> <span data-ttu-id="b4b99-122">DMX를 어느 정도 아는 경우에도 템플릿을 사용하면 올바른 구문을 얻을 수 있으므로 시간을 절약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-122">Even if you know some DMX, the templates can save you time by getting the syntax right.</span></span>  
  
 <span data-ttu-id="b4b99-123">**모델 선택**</span><span class="sxs-lookup"><span data-stu-id="b4b99-123">**Choose Model**</span></span>  
 <span data-ttu-id="b4b99-124">현재 연결에서 사용할 수 있는 데이터 마이닝 모델의 목록을 보려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-124">Click to view a list of data mining models available on the current connection.</span></span>  
  
 <span data-ttu-id="b4b99-125">**Dmx 쿼리** 창의 dmx 문에서 모델 이름을 클릭 하 여 사용할 수 있는 모델의 목록을 표시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-125">You can also display a list of available models by clicking on the model name in the DMX statement in the **DMX Query** pane.</span></span> <span data-ttu-id="b4b99-126">모델 이름은 일반적으로 빨간색으로 강조 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-126">The model name is typically highlighted in red.</span></span>  
  
 <span data-ttu-id="b4b99-127">**입력 선택**</span><span class="sxs-lookup"><span data-stu-id="b4b99-127">**Select Input**</span></span>  
 <span data-ttu-id="b4b99-128">마이닝 모델에 대한 입력으로 사용할 데이터를 선택하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-128">Click to choose the data to use as input to the mining model.</span></span> <span data-ttu-id="b4b99-129">데이터 원본을 지정 하지 않은 경우 **\<Input>** **DMX 쿼리** 창에서 빨간색으로 강조 표시 된 링크를 클릭할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-129">If no data source has been specified, you can also click the **\<Input>** link, which is highlighted in red in the **DMX Query** pane.</span></span>  
  
 <span data-ttu-id="b4b99-130">드롭다운 목록에서 \*\* \@ inputrowset\*\* 을 선택 하 여 **inputrowset 바꾸기** 대화 상자를 열고 기존 입력을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-130">Select **\@InputRowset** from the dropdown list to open the **Replace InputRowset** dialog box and modify an existing input.</span></span>  
  
 <span data-ttu-id="b4b99-131">입력 **추가** 를 선택 하 여 **입력 추가** 대화 상자를 열고 새 데이터 원본을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-131">Select **Add Input** to open the **Add Input** dialog box and specify a new data source.</span></span>  
  
 <span data-ttu-id="b4b99-132">또한 DMX 쿼리 창에서 빨간색으로 강조 표시 된 \*\* \@ inputrowset\*\* 링크를 클릭 하 여 기존 입력을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-132">You can also modify an existing input by clicking the **\@InputRowset** link, which is highlighted in red in the DMX Query pane.</span></span>  
  
 <span data-ttu-id="b4b99-133">**열 매핑**</span><span class="sxs-lookup"><span data-stu-id="b4b99-133">**Map Columns**</span></span>  
 <span data-ttu-id="b4b99-134">마이닝 모델에서 열을 선택한 다음 외부 데이터 원본의 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-134">Select columns from the mining model and then map them to columns in the external data source.</span></span>  
  
 <span data-ttu-id="b4b99-135">DMX 쿼리 창에서 강조 표시 된 링크를 클릭할 수도 있습니다 **\<Mapping>** .</span><span class="sxs-lookup"><span data-stu-id="b4b99-135">You can also click the highlighted **\<Mapping>** link in the DMX Query pane.</span></span>  
  
 <span data-ttu-id="b4b99-136">**출력 추가**</span><span class="sxs-lookup"><span data-stu-id="b4b99-136">**Add Output**</span></span>  
 <span data-ttu-id="b4b99-137">예측 쿼리의 일부로 출력되어야 하는 열을 선택하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-137">Click to choose the columns that should be output as part of a prediction query.</span></span>  
  
 <span data-ttu-id="b4b99-138">DMX 쿼리 창에서 강조 표시 된 링크를 클릭할 수도 있습니다 **\<Add Output>** .</span><span class="sxs-lookup"><span data-stu-id="b4b99-138">You can also click the highlighted **\<Add Output>** link in the DMX Query pane.</span></span>  
  
 <span data-ttu-id="b4b99-139">**모델 열**</span><span class="sxs-lookup"><span data-stu-id="b4b99-139">**Model Columns**</span></span>  
 <span data-ttu-id="b4b99-140">선택한 마이닝 모델 열을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-140">Lists the columns in the selected mining model.</span></span> <span data-ttu-id="b4b99-141">열 이름 옆의 다이아몬드 표시는 열이 예측 가능한 열임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-141">A diamond mark next to the column name indicates that the column is a predictable column.</span></span>  
  
 <span data-ttu-id="b4b99-142">**입력 열**</span><span class="sxs-lookup"><span data-stu-id="b4b99-142">**Input Columns**</span></span>  
 <span data-ttu-id="b4b99-143">입력으로 추가된 외부 데이터 원본으로부터 열을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="b4b99-143">Lists the columns from the external data source that have been added as inputs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4b99-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b4b99-144">See Also</span></span>  
 [<span data-ttu-id="b4b99-145">쿼리 &#40;SQL Server 데이터 마이닝 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="b4b99-145">Query &#40;SQL Server Data Mining Add-ins&#41;</span></span>](query-sql-server-data-mining-add-ins.md)  
  
  
