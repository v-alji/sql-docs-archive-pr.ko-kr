---
title: 키 열 대화 상자 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.dataitemCollection.f1
helpviewer_keywords:
- DataItem Collection dialog box
ms.assetid: 585f27f2-d5eb-4516-b29a-2084010b7d51
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8a72a9e137700ddee822e68901bfde971637d07f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647951"
---
# <a name="key-columns-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="95796-102">키 열 대화 상자(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="95796-102">Key Columns Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="95796-103">**키 열** 대화 상자를 사용하여 특성의 **KeyColumns** 속성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95796-103">Use the **Key Columns** dialog box to change the **KeyColumns** property of an attribute.</span></span> <span data-ttu-id="95796-104">자세한 내용은 [특성의 KeyColumn 속성 수정](multidimensional-models/attribute-properties-modify-the-keycolumn-property.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="95796-104">For more information, see [Modify the KeyColumn Property of an Attribute](multidimensional-models/attribute-properties-modify-the-keycolumn-property.md).</span></span>  
  
 <span data-ttu-id="95796-105">**키 열 대화 상자를 표시하려면**</span><span class="sxs-lookup"><span data-stu-id="95796-105">**To display the Key Columns dialog box**</span></span>  
  
-   <span data-ttu-id="95796-106">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 특성을 선택하고 **속성** 창에서 해당 특성의**KeyColumns**속성과 연관된 줄임표 단추( **...** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="95796-106">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], select an attribute, and in the **Properties** window, click the ellipsis button (**...**) associated with the **KeyColumns** property of that attribute.</span></span>  
  
## <a name="options"></a><span data-ttu-id="95796-107">옵션</span><span class="sxs-lookup"><span data-stu-id="95796-107">Options</span></span>  
 <span data-ttu-id="95796-108">**원본 테이블**</span><span class="sxs-lookup"><span data-stu-id="95796-108">**Source table**</span></span>  
 <span data-ttu-id="95796-109">키 열을 선택할 원본 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="95796-109">Select the source table for which you want to select its key columns.</span></span> <span data-ttu-id="95796-110">원본 테이블은 데이터 원본 뷰의 모든 테이블 목록에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95796-110">You can select the source table from a list of all tables in the Data Source View.</span></span>  
  
 <span data-ttu-id="95796-111">**사용 가능한 열**</span><span class="sxs-lookup"><span data-stu-id="95796-111">**Available Columns**</span></span>  
 <span data-ttu-id="95796-112">키 열로 사용할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="95796-112">Select the columns that you want to use as key columns.</span></span> <span data-ttu-id="95796-113">지정된 **원본 테이블** 의 열 목록에서 아직 키 열로 선택하지 않은 열을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95796-113">You can select the columns from a list of columns in the specified **Source table** that have not yet been selected as key columns.</span></span>  
  
 <span data-ttu-id="95796-114">선택한 열을 **키 열** 목록에 추가하려면 **>** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="95796-114">To add the selected columns to the **Key Columns** list, click the **>** button.</span></span>  
  
 <span data-ttu-id="95796-115">**키 열**</span><span class="sxs-lookup"><span data-stu-id="95796-115">**Key Columns**</span></span>  
 <span data-ttu-id="95796-116">선택한 키 열의 순서를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="95796-116">Define the order of the selected key columns.</span></span> <span data-ttu-id="95796-117">키 열의 순서는 올바른 복합 키를 정의하는 데 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="95796-117">The order of the key columns is important in defining the correct composite key.</span></span> <span data-ttu-id="95796-118">키 열의 목록을 정렬하거나 다시 정렬하려면 열을 선택한 다음 **위로** 또는 **아래로** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="95796-118">To order or reorder the list of key columns, select a column, and then click the **Up** or **Down** buttons.</span></span>  
  
 <span data-ttu-id="95796-119">**키 열** 목록에서 열을 제거하려면 열을 선택하고 **\<** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="95796-119">To remove a column from the **Key Columns** list, select the column and click the **\<** button.</span></span>  
  
 <span data-ttu-id="95796-120">**최대**</span><span class="sxs-lookup"><span data-stu-id="95796-120">**Up**</span></span>  
 <span data-ttu-id="95796-121">**키 열** 에서 선택한 열을 한 위치 위로 이동하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="95796-121">Click to move the column selected in **Key Columns** up one position.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95796-122">이 옵션은 목록에 둘 이상의 열이 있고 열을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95796-122">This option is enabled only if the list contains more than one column and a column is selected.</span></span>  
  
 <span data-ttu-id="95796-123">**아래로**</span><span class="sxs-lookup"><span data-stu-id="95796-123">**Down**</span></span>  
 <span data-ttu-id="95796-124">**키 열** 에서 선택한 열을 한 위치 아래로 이동하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="95796-124">Click to move the column selected in **Key Columns** down one position.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95796-125">이 옵션은 목록에 둘 이상의 열이 있고 열을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95796-125">This option is enabled only if the list contains more than one column and a column is selected.</span></span>  
  
 **>**  
 <span data-ttu-id="95796-126">**키 열**에 나열된 열의 끝에 새 열을 추가하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="95796-126">Click to add a new column to the end of the columns listed in **Key Columns**.</span></span>  
  
 **<**  
 <span data-ttu-id="95796-127">선택한 열을 **키 열**에 나열된 열에서 제거하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="95796-127">Click to remove the selected column from the columns listed in **Key Columns**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95796-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="95796-128">See Also</span></span>  
 [<span data-ttu-id="95796-129">Analysis Services 디자이너 및 대화 상자 &#40;다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="95796-129">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
