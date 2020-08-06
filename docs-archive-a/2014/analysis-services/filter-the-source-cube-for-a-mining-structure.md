---
title: 마이닝 구조에 대 한 원본 큐브 필터링 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- slice cubes [Analysis Services]
- mining structures [Analysis Services], filtering source cube
- cubes [Analysis Services], slicing
- filtering data [Analysis Services]
ms.assetid: 05dce7e1-2fe5-4500-bacf-c1a8a76e1424
author: minewiskan
ms.author: owend
ms.openlocfilehash: 61409b4803f43d3ff2634daaba65a92bc343db36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647983"
---
# <a name="filter-the-source-cube-for-a-mining-structure"></a><span data-ttu-id="2d69d-102">마이닝 구조에 대한 원본 큐브 필터링</span><span class="sxs-lookup"><span data-stu-id="2d69d-102">Filter the Source Cube for a Mining Structure</span></span>
  <span data-ttu-id="2d69d-103">다차원 모델 (OLAP 큐브)의 데이터를 기반으로 하는 마이닝 구조를 만드는 경우 마이닝 구조의 기반이 되는 큐브를 *분할할* 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d69d-103">When you create a mining structure that is based on data in a multidimensional model (an OLAP cube), you can *slice* the cube that the mining structure is based on.</span></span> <span data-ttu-id="2d69d-104">조각화하면 마이닝 모델 학습에 사용되는 데이터에 대한 일종의 필터로 데이터 하위 집합을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d69d-104">Slicing lets you create subsets of data, as a kind of filter on the data that is used to train the mining model.</span></span>  
  
### <a name="to-slice-a-cube"></a><span data-ttu-id="2d69d-105">큐브를 조각화하려면</span><span class="sxs-lookup"><span data-stu-id="2d69d-105">To slice a cube</span></span>  
  
1.  <span data-ttu-id="2d69d-106">의 데이터 마이닝 디자이너에서 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] **마이닝 구조** 탭 이나 **마이닝 모델** 탭을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d69d-106">In Data Mining Designer in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], select the **Mining Structure** tab or the **Mining Models** tab.</span></span>  
  
2.  <span data-ttu-id="2d69d-107">**마이닝 모델** 메뉴에서 **마이닝 구조 큐브 조각 정의**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d69d-107">On the **Mining Model** menu, select **Define Mining Structure Cube Slice**.</span></span>  
  
     <span data-ttu-id="2d69d-108">**큐브 조각화** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="2d69d-108">The **Slice Cube** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="2d69d-109">**큐브 조각화** 대화 상자의 **차원** 열에서 필터링 할 차원을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d69d-109">In the **Dimension** column of the **Slice Cube** dialog box, select the dimension that you want to filter.</span></span>  
  
4.  <span data-ttu-id="2d69d-110">**계층 열의 목록을** 사용 하 여 계층의 수준을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d69d-110">Select a level of a hierarchy, using the list in the **Hierarchy** column.</span></span>  
  
5.  <span data-ttu-id="2d69d-111">**연산자** 열의 목록에서 필터 조건을 만드는 데 사용할 연산자를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d69d-111">Select an operator from the list in the **Operator** column, to use in building the filter condition.</span></span>  
  
6.  <span data-ttu-id="2d69d-112">**필터** 열에서 상자를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d69d-112">Click the box in the **Filter** column.</span></span>  
  
     <span data-ttu-id="2d69d-113">지정한 계층 수준의 모든 멤버가 포함된 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="2d69d-113">A dialog box opens that contains all the members at the specified level of the hierarchy.</span></span>  
  
7.  <span data-ttu-id="2d69d-114">필터를 적용할 멤버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2d69d-114">Select the member or members on which you want to filter.</span></span>  
  
8.  <span data-ttu-id="2d69d-115">멤버 대화 상자에서 **확인을** 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d69d-115">Click **OK** in the member dialog box.</span></span>  
  
9. <span data-ttu-id="2d69d-116">**큐브 조각화** 대화 상자에서 **확인을** 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d69d-116">Click **OK** in the **Slice Cube** dialog box.</span></span>  
  
     <span data-ttu-id="2d69d-117">이렇게 하면 큐브 조각에서 정의한 대로 원본 큐브가 필터링됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d69d-117">The source cube is now filtered as defined by the cube slice.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d69d-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2d69d-118">See Also</span></span>  
 <span data-ttu-id="2d69d-119">[마이닝 구조 태스크 및 방법](data-mining/mining-structure-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="2d69d-119">[Mining Structure Tasks and How-tos](data-mining/mining-structure-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="2d69d-120">새 OLAP 마이닝 구조 만들기</span><span class="sxs-lookup"><span data-stu-id="2d69d-120">Create a New OLAP Mining Structure</span></span>](data-mining/create-a-new-olap-mining-structure.md)  
  
  
