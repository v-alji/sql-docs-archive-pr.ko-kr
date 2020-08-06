---
title: 개체 바인딩 대화 상자 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.objectbinding.f1
helpviewer_keywords:
- Object Binding dialog box
ms.assetid: 2bb5ad7c-2962-4559-8c95-cf7148bd2e72
author: minewiskan
ms.author: owend
ms.openlocfilehash: a10c91e0222b826066aeede96aa665cc22540637
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652386"
---
# <a name="object-binding-dialog-box"></a><span data-ttu-id="b48d3-102">개체 바인딩 대화 상자</span><span class="sxs-lookup"><span data-stu-id="b48d3-102">Object Binding Dialog Box</span></span>
  <span data-ttu-id="b48d3-103">**의** 개체 바인딩 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 대화 상자를 사용하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체 속성과 데이터 원본 뷰의 테이블 또는 열 속성 간의 바인딩을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b48d3-103">Use the **Object Binding** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to define bindings between the property of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object and a table or column in a data source view.</span></span> <span data-ttu-id="b48d3-104">**의** 속성 **창에서** 개체의 다음 속성 값에 대한 드롭다운 목록에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] (새로 만들기) **를 선택하면** 개체 바인딩 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]대화 상자를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b48d3-104">You can display the **Object Binding** dialog box by selecting **(new)** from the drop-down list for the value of the following properties of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object in the **Properties** window of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]:</span></span>  
  
-   <span data-ttu-id="b48d3-105">NameColumn</span><span class="sxs-lookup"><span data-stu-id="b48d3-105">NameColumn</span></span>  
  
-   <span data-ttu-id="b48d3-106">ValueColumn</span><span class="sxs-lookup"><span data-stu-id="b48d3-106">ValueColumn</span></span>  
  
-   <span data-ttu-id="b48d3-107">CustomRollupColumn</span><span class="sxs-lookup"><span data-stu-id="b48d3-107">CustomRollupColumn</span></span>  
  
-   <span data-ttu-id="b48d3-108">CustomRollupPropertiesColumn</span><span class="sxs-lookup"><span data-stu-id="b48d3-108">CustomRollupPropertiesColumn</span></span>  
  
-   <span data-ttu-id="b48d3-109">UnaryOperatorColumn</span><span class="sxs-lookup"><span data-stu-id="b48d3-109">UnaryOperatorColumn</span></span>  
  
## <a name="options"></a><span data-ttu-id="b48d3-110">옵션</span><span class="sxs-lookup"><span data-stu-id="b48d3-110">Options</span></span>  
 <span data-ttu-id="b48d3-111">**바인딩 유형**</span><span class="sxs-lookup"><span data-stu-id="b48d3-111">**Binding type**</span></span>  
 <span data-ttu-id="b48d3-112">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체에 사용할 바인딩을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b48d3-112">Select the binding to use for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span> <span data-ttu-id="b48d3-113">다음 바인딩 유형을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b48d3-113">The following types of binding can be used:</span></span>  
  
 <span data-ttu-id="b48d3-114">열 바인딩</span><span class="sxs-lookup"><span data-stu-id="b48d3-114">Column binding</span></span>  
 <span data-ttu-id="b48d3-115">개체를 데이터 원본 뷰의 기존 테이블 및 열에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="b48d3-115">Binds the object to an existing table and column within a data source view.</span></span>  
  
 <span data-ttu-id="b48d3-116">열 생성</span><span class="sxs-lookup"><span data-stu-id="b48d3-116">Generate column</span></span>  
 <span data-ttu-id="b48d3-117">데이터 원본 뷰에서 새 열이 정의된 다음 열 바인딩이 이 열과 연결됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b48d3-117">Indicates that a new column is to be defined in the data source view, and a column binding is then associated with it.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b48d3-118">이 옵션을 선택하는 경우 **개체를 배포하기 전에** 스키마 생성 마법사 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b48d3-118">If this option is selected, you must run the **Schema Generation Wizard** before deploying the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span>  
  
 <span data-ttu-id="b48d3-119">행 바인딩</span><span class="sxs-lookup"><span data-stu-id="b48d3-119">Row binding</span></span>  
 <span data-ttu-id="b48d3-120">개체를 팩트 테이블의 행에 바인딩합니다. 팩트 테이블에서 처리된 행 수를 기반으로 카운트 측정을 용이하게 하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b48d3-120">Binds the object to a row in a fact table and is used to facilitate count measures based on the number of rows processed in the fact table.</span></span>  
  
 <span data-ttu-id="b48d3-121">**원본 테이블**</span><span class="sxs-lookup"><span data-stu-id="b48d3-121">**Source table**</span></span>  
 <span data-ttu-id="b48d3-122">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체와 연결된 데이터 원본 뷰의 테이블 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b48d3-122">Displays a list of tables in the data source view associated with the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span>  
  
 <span data-ttu-id="b48d3-123">**원본 열**</span><span class="sxs-lookup"><span data-stu-id="b48d3-123">**Source column**</span></span>  
 <span data-ttu-id="b48d3-124">**원본 테이블**에서 선택한 테이블의 열 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b48d3-124">Displays a list of columns in the table selected in **Source table**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b48d3-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b48d3-125">See Also</span></span>  
 [<span data-ttu-id="b48d3-126">Analysis Services 디자이너 및 대화 상자 &#40;다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="b48d3-126">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
