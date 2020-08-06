---
title: 멤버 필터 대화 상자 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.filtermembers.f1
helpviewer_keywords:
- Filter Members dialog box
ms.assetid: 52c6da1d-9fb5-4dbc-bffa-248d11cd337c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 66980b1afe9d4eed353ae18c37ed1fdd052e62b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639067"
---
# <a name="filter-members-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="27d35-102">멤버 필터 대화 상자(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="27d35-102">Filter Members Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="27d35-103">**의** 멤버 필터 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 대화 상자를 사용하면 **차원 디자이너** 의 **브라우저**탭에서 차원을 찾아보는 동안 현재 수준에 대한 값 열 값, 키 열 값, 멤버 고유 이름, 멤버 이름 또는 멤버 캡션별로 차원 멤버를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27d35-103">Use the **Filter Members** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to filter dimension members by member caption, member name, member unique name, key column value, or value column value for the current level while browsing a dimension in the **Browser** tab of **Dimension Designer**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="27d35-104">옵션</span><span class="sxs-lookup"><span data-stu-id="27d35-104">Options</span></span>  
  
|<span data-ttu-id="27d35-105">용어</span><span class="sxs-lookup"><span data-stu-id="27d35-105">Term</span></span>|<span data-ttu-id="27d35-106">정의</span><span class="sxs-lookup"><span data-stu-id="27d35-106">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="27d35-107">**필터 식**</span><span class="sxs-lookup"><span data-stu-id="27d35-107">**Filter expression**</span></span>|<span data-ttu-id="27d35-108">필터 식을 작성하는 데 사용되는 속성, 연산자 및 값이 포함된 표를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="27d35-108">Displays a grid of properties, operators, and values used to construct a filter expression.</span></span> <span data-ttu-id="27d35-109">행을 추가한 다음에는 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="27d35-109">Note that after a row is added, it cannot be removed.</span></span> <span data-ttu-id="27d35-110">새 필터 식을 지정하려면 대화 상자를 닫았다가 다시 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27d35-110">You must close and reopen the dialog box to specify a new filter expression.</span></span> <span data-ttu-id="27d35-111">표에는 다음 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27d35-111">The grid contains the following columns:</span></span><br /><br /> <span data-ttu-id="27d35-112">**속성**: 필터 식에 사용할 멤버의 속성을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="27d35-112">**Property**: Select the property of the member to use for the filter expression.</span></span><br /><br /> <span data-ttu-id="27d35-113">**연산자**: 필터 식에 사용할 연산자를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="27d35-113">**Operator**: Select the operator to use for the filter expression.</span></span><br /><br /> <span data-ttu-id="27d35-114">**값**: **연산자**에 지정 된 연산자를 사용 하 여 평가 하기 위해 **속성** 에서 선택한 속성의 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="27d35-114">**Value**: Type the value of the property selected in **Property** to evaluate using the operator specified in **Operator**.</span></span>|  
|<span data-ttu-id="27d35-115">**테스트 창**</span><span class="sxs-lookup"><span data-stu-id="27d35-115">**Test pane**</span></span>|<span data-ttu-id="27d35-116">**테스트** 를 클릭하면 이 창에 필터 식에서 반환한 멤버가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="27d35-116">When **Test** is clicked, this pane displays the members returned by the filter expression.</span></span> <span data-ttu-id="27d35-117">**필터 식**에서 지정한 조건을 사용하여 반환되는 멤버가 없으면 경고가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="27d35-117">If no members are returned using the criteria specified in **Filter expression**, a warning is displayed.</span></span>|  
|<span data-ttu-id="27d35-118">**Test**</span><span class="sxs-lookup"><span data-stu-id="27d35-118">**Test**</span></span>|<span data-ttu-id="27d35-119">**필터 식**에서 지정한 조건을 테스트하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="27d35-119">Click to test the criteria specified in **Filter expression**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="27d35-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="27d35-120">See Also</span></span>  
 <span data-ttu-id="27d35-121">[Analysis Services 디자이너 및 대화 상자 &#40;다차원 데이터&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="27d35-121">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="27d35-122">브라우저 &#40;차원 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="27d35-122">Browser &#40;Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](browser-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
