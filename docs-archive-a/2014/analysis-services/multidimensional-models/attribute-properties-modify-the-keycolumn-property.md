---
title: 특성의 KeyColumn 속성을 수정 합니다. Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- binding attributes [Analysis Services]
- attributes [Analysis Services], binding
- key columns [Analysis Services]
ms.assetid: a2643be4-8123-4cc3-baf9-e5ec54a1669d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3367a7aec84ba59efd118a56745bb76fc5266061
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741432"
---
# <a name="modify-the-keycolumn-property-of-an-attribute"></a><span data-ttu-id="d067f-102">특성의 KeyColumn 속성 수정</span><span class="sxs-lookup"><span data-stu-id="d067f-102">Modify the KeyColumn Property of an Attribute</span></span>
  <span data-ttu-id="d067f-103">특성의 **KeyColumns** 속성을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d067f-103">You can modify the **KeyColumns** property of an attribute.</span></span> <span data-ttu-id="d067f-104">예를 들어 단일 키 대신 복합 키를 특성 키로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d067f-104">For example, you might want to specify a composite key instead of a single key as the key for the attribute.</span></span>  
  
### <a name="to-modify-the-keycolumns-property-of-an-attribute"></a><span data-ttu-id="d067f-105">특성의 KeyColumns 속성을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="d067f-105">To modify the KeyColumns property of an attribute</span></span>  
  
1.  <span data-ttu-id="d067f-106">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 **KeyColumns** 속성을 수정할 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d067f-106">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project in which you want to modify the **KeyColumns** property.</span></span>  
  
2.  <span data-ttu-id="d067f-107">다음 절차 중 하나를 수행하여 차원 디자이너를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d067f-107">Open Dimension Designer by doing one of the following procedures:</span></span>  
  
    -   <span data-ttu-id="d067f-108">**솔루션 탐색기**의 **차원** 폴더에서 차원을 마우스 오른쪽 단추로 클릭한 다음 **열기** 또는 **뷰 디자이너**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d067f-108">In **Solution Explorer**, right-click the dimension in the **Dimensions** folder, and then either click **Open** or **View Designer**.</span></span>  
  
         <span data-ttu-id="d067f-109">또는</span><span class="sxs-lookup"><span data-stu-id="d067f-109">-or-</span></span>  
  
    -   <span data-ttu-id="d067f-110">큐브 디자이너의 **큐브 구조** 탭에 있는 **차원** 창에서 큐브 차원을 확장 하 고 \*\*편집 \<dimension> \*\*을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d067f-110">In Cube Designer, on the **Cube Structure** tab, expand the cube dimension in the **Dimensions** pane and click **Edit \<dimension>**.</span></span>  
  
3.  <span data-ttu-id="d067f-111">**차원 구조** 탭의 **특성** 창에서 수정할 **KeyColumns** 속성이 있는 특성을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d067f-111">On the **Dimension Structure** tab, in the **Attributes** pane, click the attribute whose **KeyColumns** property you want to modify.</span></span>  
  
4.  <span data-ttu-id="d067f-112">**속성** 창에서 **KeyColumns** 속성의 값을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d067f-112">In the **Properties** window, click the value for the **KeyColumns** property.</span></span>  
  
5.  <span data-ttu-id="d067f-113">속성 상자의 값 셀에 나타나는 찾아보기 단추 **(...)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d067f-113">Click the browse **(...)** button that appears in the value cell of the property box.</span></span>  
  
     <span data-ttu-id="d067f-114">**키 열** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="d067f-114">The **Key Columns** dialog box opens.</span></span>  
  
6.  <span data-ttu-id="d067f-115">기존 키 열을 제거하려면 **키 열** 목록에서 열을 선택한 다음 **\<** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d067f-115">To remove an existing key column, in the **Key Columns** list, select the column, and then click the **\<** button.</span></span>  
  
7.  <span data-ttu-id="d067f-116">키 열을 추가하려면 **사용 가능한 열** 목록에서 열을 선택한 다음 **>** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d067f-116">To add a key column, in the **Available Columns** list, select the column, and then click the **>** button.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d067f-117">키 열을 여러 개 정의하는 경우 해당 열이 **키 열** 목록에 표시되는 순서에 따라 표시 순서가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d067f-117">If you define multiple key columns, the order in which those columns appear in the **Key Columns** list affects the display order.</span></span> <span data-ttu-id="d067f-118">예를 들어 월 특성에는 월과 연도라는 두 개의 키 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d067f-118">For example, a month attribute has two key columns: month and year.</span></span> <span data-ttu-id="d067f-119">목록에서 연도 열이 월 열 앞에 표시되는 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서는 연도순으로 정렬한 다음 월순으로 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="d067f-119">If the year column appears in the list before the month column, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will sort by year and then by month.</span></span> <span data-ttu-id="d067f-120">월 열이 연도 열 앞에 표시되는 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서는 월순으로 정렬한 다음 연도순으로 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="d067f-120">If the month column appears before the year column, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will sort by month and then by year.</span></span>  
  
8.  <span data-ttu-id="d067f-121">키 열의 순서를 변경하려면 열을 선택한 다음 **위로** 또는 **아래로** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d067f-121">To change the order of key columns, select a column, and then click the **Up** or **Down** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d067f-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d067f-122">See Also</span></span>  
 [<span data-ttu-id="d067f-123">차원 특성 속성 참조</span><span class="sxs-lookup"><span data-stu-id="d067f-123">Dimension Attribute Properties Reference</span></span>](dimension-attribute-properties-reference.md)  
  
  
