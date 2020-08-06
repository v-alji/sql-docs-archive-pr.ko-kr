---
title: 관계 만들기 또는 편집 대화 상자 (다차원 데이터 Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.createrelationship.f1
helpviewer_keywords:
- Create Relationship dialog box
ms.assetid: da3c7074-623e-4ddf-a707-d3276a47cf1c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4edae3f78ac6b764d91e1be97787fe59d49421db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649274"
---
# <a name="create-or-edit-relationship-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="08caf-102">관계 만들기 또는 편집 대화 상자(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="08caf-102">Create or Edit Relationship Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="08caf-103">**의** 관계 만들기/편집 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 대화 상자를 사용하여 데이터 원본 뷰에서 관계를 정의하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08caf-103">Use the **Create/Edit Relationship** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to define or modify a relationship in a data source view.</span></span> <span data-ttu-id="08caf-104">다음과 같은 방법으로 **관계 만들기/편집** 대화 상자를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08caf-104">You can display the **Create/Edit Relationship** dialog box by:</span></span>  
  
-   <span data-ttu-id="08caf-105">**데이터 원본 뷰 디자이너** 의 **도구 모음** 창에서 **새 관계**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="08caf-105">Clicking **New Relationship** in the **Toolbar** pane of **Data Source View Designer**.</span></span>  
  
-   <span data-ttu-id="08caf-106">**데이터 원본 뷰 디자이너** 의 **테이블** 또는 **다이어그램** 창에서 테이블을 마우스 오른쪽 단추로 클릭한 다음 **새 관계**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="08caf-106">Right-clicking a table in either the **Tables** or **Diagram** pane of **Data Source View Designer** and selecting **New Relationship**.</span></span>  
  
-   <span data-ttu-id="08caf-107">**데이터 원본 뷰 디자이너** 의 **다이어그램** 창에서 관계를 마우스 오른쪽 단추로 클릭한 다음 **관계 편집**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="08caf-107">Right-clicking a relationship in the **Diagram** pane of **Data Source View Designer** and selecting **Edit Relationship**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="08caf-108">**데이터 원본 뷰 디자이너** 에서 기본 데이터 원본에 없는 관계를 만들고 기본 데이터 원본에 있는 기존 외래 키 관계에서 **데이터 원본 뷰 디자이너** 로 만든 관계를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08caf-108">You can create relationships in **Data Source View Designer** that do not exist in the underlying data source, and remove relationships created by **Data Source View Designer** from existing foreign key relationships in the underlying data source.</span></span>  
  
## <a name="options"></a><span data-ttu-id="08caf-109">옵션</span><span class="sxs-lookup"><span data-stu-id="08caf-109">Options</span></span>  
 <span data-ttu-id="08caf-110">**원본(외래 키) 테이블**</span><span class="sxs-lookup"><span data-stu-id="08caf-110">**Source (foreign key) table**</span></span>  
 <span data-ttu-id="08caf-111">대상 테이블에 있는 하나 이상의 열에 대한 참조를 포함하는 테이블 또는 명명된 쿼리를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="08caf-111">Select the table or named query that contains the reference to one or more columns in the destination table.</span></span>  
  
 <span data-ttu-id="08caf-112">**대상(기본 키) 테이블**</span><span class="sxs-lookup"><span data-stu-id="08caf-112">**Destination (primary key) table**</span></span>  
 <span data-ttu-id="08caf-113">원본 테이블에서 참조하는 하나 이상의 열을 포함하는 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="08caf-113">Select the table that contains one or more columns referenced by the source table.</span></span> <span data-ttu-id="08caf-114">셀프 조인하려면 **원본(외래 키) 테이블**에서 선택한 것과 같은 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="08caf-114">For self-joins, select the same table selected in **Source (foreign key) table**.</span></span>  
  
 <span data-ttu-id="08caf-115">**원본 열**</span><span class="sxs-lookup"><span data-stu-id="08caf-115">**Source columns**</span></span>  
 <span data-ttu-id="08caf-116">대상 테이블에 있는 열을 참조하는 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="08caf-116">Select the columns that reference columns in the destination table.</span></span>  
  
 <span data-ttu-id="08caf-117">**대상 열**</span><span class="sxs-lookup"><span data-stu-id="08caf-117">**Destination columns**</span></span>  
 <span data-ttu-id="08caf-118">원본 테이블에 있는 열에서 참조하는 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="08caf-118">Select the columns that are referenced by columns in the source table.</span></span>  
  
 <span data-ttu-id="08caf-119">**되돌립니다**</span><span class="sxs-lookup"><span data-stu-id="08caf-119">**Reverse**</span></span>  
 <span data-ttu-id="08caf-120">관계를 뒤집으려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="08caf-120">Click to reverse the direction of the relationship.</span></span>  
  
 <span data-ttu-id="08caf-121">**설명**</span><span class="sxs-lookup"><span data-stu-id="08caf-121">**Description**</span></span>  
 <span data-ttu-id="08caf-122">관계에 대한 선택적 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="08caf-122">Type an optional description for the relationship.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08caf-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="08caf-123">See Also</span></span>  
 <span data-ttu-id="08caf-124">[Analysis Services 디자이너 및 대화 상자 &#40;다차원 데이터&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="08caf-124">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="08caf-125">데이터 원본 뷰 디자이너&#40;Analysis Services - 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="08caf-125">Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  
