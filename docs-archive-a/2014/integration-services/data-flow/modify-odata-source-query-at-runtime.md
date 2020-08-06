---
title: 런타임에 OData 원본 쿼리 수정 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: bcbba7f4-6e5d-46e6-a73a-3f17d3ff376a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b3dbc4d27f2d11537a9d66980ef6ca59b80811b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741144"
---
# <a name="modify-odata-source-query-at-runtime"></a><span data-ttu-id="0608d-102">런타임에 OData 원본 쿼리 수정</span><span class="sxs-lookup"><span data-stu-id="0608d-102">Modify OData Source Query at Runtime</span></span>
  <span data-ttu-id="0608d-103">데이터 흐름 태스크의 [OData Source].[Query] 속성에 **식**을 추가하여 런타임에 OData 원본 쿼리를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-103">You can modify the OData Source query at runtime by adding an expression to the **[OData Source].[Query]** property of the Data Flow task.</span></span>  
  
 <span data-ttu-id="0608d-104">열은 디자인 타임에 사용된 것과 동일하게 유지되어야 합니다. 그렇지 않으면 패키지가 실행될 때 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-104">Note that the columns must remain the same as what was used at design time; otherwise you will get an error when the package is executed.</span></span> <span data-ttu-id="0608d-105">$select 쿼리 옵션을 사용할 때 동일한 열을 같은 순서로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-105">Be sure to specify the same columns (in the same order) when using the $select query option.</span></span> <span data-ttu-id="0608d-106">$select 옵션을 사용하는 것보다 안전한 방법은 원본 구성 요소 UI에서 직접 원하지 않는 열의 선택을 취소하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-106">A safer alternative to using the $select option is to deselect the columns you don't want directly from the Source Component UI.</span></span>  
  
 <span data-ttu-id="0608d-107">런타임에 쿼리 값을 동적으로 설정하는 몇 가지 다른 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-107">There are a few different ways of dynamically setting the query value at runtime.</span></span> <span data-ttu-id="0608d-108">보다 일반적인 방법 중 몇 가지는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-108">Below are some of the more common methods.</span></span>  
  
## <a name="exposing-the-query-as-a-parameter"></a><span data-ttu-id="0608d-109">쿼리를 매개 변수로 노출</span><span class="sxs-lookup"><span data-stu-id="0608d-109">Exposing the Query as a Parameter</span></span>  
 <span data-ttu-id="0608d-110">다음 절차에는 OData 원본 구성 요소에서 패키지에 대한 매개 변수로 사용하는 쿼리를 노출하는 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-110">The following procedure has steps to expose query used by an OData Source component as a parameter to the package.</span></span>  
  
1.  <span data-ttu-id="0608d-111">**데이터 흐름 태스크**를 마우스 오른쪽 단추로 클릭하고 **매개 변수화...** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-111">Right click on the **Data Flow task** and select the **Parameterize...** option.</span></span>  
  
2.  <span data-ttu-id="0608d-112">**매개 변수화** 대화 상자에서 **속성**에 대한 **[\<Name of the OData Source Component>].[Query]** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-112">In the **Parameterize** dialog, select **[\<Name of the OData Source Component>].[Query]** for **Property**.</span></span>  
  
3.  <span data-ttu-id="0608d-113">**새 매개 변수 만들기** 또는 **기존 매개 변수 사용**중에서 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-113">Choose whether to **create new parameter** or **use an existing parameter**.</span></span>  
  
4.  <span data-ttu-id="0608d-114">**새 매개 변수 만들기**를 선택하는 경우 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-114">If you select **Create new parameter**, do the following:</span></span>  
  
    1.  <span data-ttu-id="0608d-115">매개 변수의 **이름** 및 **설명** 을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-115">Enter **name** and **description** for the parameter.</span></span>  
  
    2.  <span data-ttu-id="0608d-116">매개 변수의 기본 **값** 을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-116">Specify default **value** for the parameter.</span></span>  
  
    3.  <span data-ttu-id="0608d-117">매개 변수의 **범위** (**패키지** 또는 **프로젝트**)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-117">Specify the **scope** (**package** or **project**) for the parameter.</span></span>  
  
    4.  <span data-ttu-id="0608d-118">매개 변수가 **필수** 인지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-118">Specify whether the parameter is **required** or not</span></span>  
  
5.  <span data-ttu-id="0608d-119">**확인** 을 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-119">Click **OK** to close the dialog box.</span></span>  
  
## <a name="using-an-expression"></a><span data-ttu-id="0608d-120">식 사용</span><span class="sxs-lookup"><span data-stu-id="0608d-120">Using an Expression</span></span>  
 <span data-ttu-id="0608d-121">이 방법은 런타임에 쿼리 문자열을 동적으로 생성하려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-121">This method is useful when you want to dynamically construct query string at runtime.</span></span> <span data-ttu-id="0608d-122">이 예에서 MaxRows 변수는 다른 수단(스크립트, 매개 변수 등)을 통해 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-122">In this example, MaxRows variable will be set through other means (script, parameter, etc).</span></span>  
  
1.  <span data-ttu-id="0608d-123">**OData 원본** 이 포함된 **데이터 흐름 태스크**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-123">Select the **Data Flow Task** which contains your **OData Source**.</span></span>  
  
2.  <span data-ttu-id="0608d-124">**속성** 창에서 **Expressions** 속성을 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-124">In the **Properties** window, highlight the **Expressions** property.</span></span>  
  
3.  <span data-ttu-id="0608d-125">...를 클릭 합니다. (줄임표) 단추를 클릭 하 여 **속성 식 편집기**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-125">Click the ... (ellipses) button to bring up the **Property Expressions Editor**.</span></span>  
  
4.  <span data-ttu-id="0608d-126">**[OData Source].[Query]** 속성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-126">Select the **[OData Source].[Query]** property.</span></span>  
  
5.  <span data-ttu-id="0608d-127">...를 클릭 합니다. **식**에 대 한 (줄임표) 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-127">Click the ... (ellipses) button for **Expression**.</span></span>  
  
6.  <span data-ttu-id="0608d-128">**식**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-128">Enter the **expression**.</span></span>  
  
7.  <span data-ttu-id="0608d-129">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-129">Click **OK**.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="0608d-130">이 방법을 사용할 때는 설정된 값이 적절하게 URL로 인코딩되었는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-130">Note that when using this approach you need to ensure that the values set are properly URL encoded.</span></span> <span data-ttu-id="0608d-131">사용자 입력에서 값을 받을 때(예를 들어 매개 변수에서 개별 쿼리 옵션을 설정할 때) 잠재적인 SQL 삽입형 공격을 방지하기 위해 값의 유효성을 검사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0608d-131">When receiving values from user input (for example, setting individual query option values from a parameter), you must ensure that the values are validated to avoid potential SQL injection-type attacks.</span></span>  
  
  
