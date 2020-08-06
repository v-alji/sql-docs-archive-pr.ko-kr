---
title: 만들기-명명 된 계산 편집 대화 상자 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsveditor.createnamedcalculation.f1
helpviewer_keywords:
- Named Calculation dialog box
ms.assetid: 66fb30ae-f5c5-4bfc-80ca-8c8a3a9bb30d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0b6777feb47a1ce6b601d0190e413b4baae35f1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639115"
---
# <a name="create-edit-named-calculation-dialog-box-analysis-services"></a><span data-ttu-id="8bcd8-102">Create-Edit Named Calculation Dialog Box (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="8bcd8-102">Create-Edit Named Calculation Dialog Box (Analysis Services)</span></span>
  <span data-ttu-id="8bcd8-103">**의** 명명된 계산 만들기/편집 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 대화 상자를 사용하여 데이터 원본 뷰에서 테이블에 대한 명명된 계산을 정의하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bcd8-103">Use the **Create/Edit Named Calculation** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to define or modify a named calculation for a table in a data source view.</span></span> <span data-ttu-id="8bcd8-104">다음과 같은 방법으로 **명명된 계산 만들기/편집** 대화 상자를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bcd8-104">You can display the **Create/Edit Named Calculation** dialog box by:</span></span>  
  
-   <span data-ttu-id="8bcd8-105">**데이터 원본 뷰 디자이너** 의 **도구 모음** 창에서 **새 명명된 계산**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcd8-105">Clicking **New Named Calculation** in the **Toolbar** pane of **Data Source View Designer**.</span></span>  
  
-   <span data-ttu-id="8bcd8-106">**데이터 원본 뷰 디자이너** 의 **테이블** 또는 **다이어그램** 창에서 테이블을 마우스 오른쪽 단추로 클릭한 다음 **새 명명된 계산**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcd8-106">Right-clicking a table in either the **Tables** or **Diagram** pane of **Data Source View Designer** and selecting **New Named Calculation**.</span></span>  
  
-   <span data-ttu-id="8bcd8-107">**데이터 원본 뷰 디자이너** 의 **다이어그램** 창에서 명명된 계산의 이름을 마우스 오른쪽 단추로 클릭한 다음 **명명된 계산 편집**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcd8-107">Right-clicking the name of a named calculation in the **Diagram** pane of **Data Source View Designer** and selecting **Edit Named Calculation**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8bcd8-108">옵션</span><span class="sxs-lookup"><span data-stu-id="8bcd8-108">Options</span></span>  
 <span data-ttu-id="8bcd8-109">**열 이름**</span><span class="sxs-lookup"><span data-stu-id="8bcd8-109">**Column Name**</span></span>  
 <span data-ttu-id="8bcd8-110">명명된 계산의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcd8-110">Type the name of the named calculation.</span></span>  
  
 <span data-ttu-id="8bcd8-111">**설명**</span><span class="sxs-lookup"><span data-stu-id="8bcd8-111">**Description**</span></span>  
 <span data-ttu-id="8bcd8-112">명명된 계산에 대한 선택적 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcd8-112">Type the optional description of the named calculation.</span></span>  
  
 <span data-ttu-id="8bcd8-113">**식**</span><span class="sxs-lookup"><span data-stu-id="8bcd8-113">**Expression**</span></span>  
 <span data-ttu-id="8bcd8-114">스칼라 값을 반환하는 유효한 SQL 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcd8-114">Type a valid SQL expression that returns a scalar value.</span></span> <span data-ttu-id="8bcd8-115">이 식은 공급자에게 전송된 다음 식으로 유효성이 검사됩니다.</span><span class="sxs-lookup"><span data-stu-id="8bcd8-115">The expression is sent to the provider, and validated in the following expression:</span></span>  
  
```  
SELECT <Table Name in Data Source>.* , <Expression> AS <Column Name> FROM <Table Name in Data Source>AS <Table Name in Data Source View>  
```  
  
 <span data-ttu-id="8bcd8-116">위의 식은 하위 SELECT 문을 사용하여 다른 테이블에 대한 참조를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bcd8-116">The expression can contain references to other tables, by means of a sub-select statement.</span></span> <span data-ttu-id="8bcd8-117">If the expression would require parentheses in a SELECT statement, the expression entered must be enclosed between parentheses.</span><span class="sxs-lookup"><span data-stu-id="8bcd8-117">If the expression would require parentheses in a SELECT statement, the expression entered must be enclosed between parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bcd8-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8bcd8-118">See Also</span></span>  
 <span data-ttu-id="8bcd8-119">[Analysis Services 디자이너 및 대화 상자 &#40;다차원 데이터&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="8bcd8-119">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="8bcd8-120">데이터 원본 뷰 디자이너&#40;Analysis Services - 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="8bcd8-120">Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  
