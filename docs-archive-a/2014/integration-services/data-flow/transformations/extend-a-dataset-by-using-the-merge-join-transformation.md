---
title: 병합 조인 변환을 사용하여 데이터 세트 확장 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Merge Join transformation
- datasets [Integration Services], joining
- datasets [Integration Services], extending
- joining datasets [Integration Services]
ms.assetid: 9e512c3c-f89b-45f3-8281-cdb8f35a2b1f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a387c4ad840eb739d36023be9323c063dcb9a68e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647776"
---
# <a name="extend-a-dataset-by-using-the-merge-join-transformation"></a><span data-ttu-id="71906-102">병합 조인 변환을 사용하여 데이터 세트 확장</span><span class="sxs-lookup"><span data-stu-id="71906-102">Extend a Dataset by Using the Merge Join Transformation</span></span>
  <span data-ttu-id="71906-103">병합 조인 변환을 추가 및 구성하려면 패키지에 적어도 하나 이상의 데이터 흐름 태스크와 병합 조인 변환에 입력을 제공하는 두 개의 데이터 흐름 구성 요소가 이미 들어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71906-103">To add and configure a Merge Join transformation, the package must already include at least one Data Flow task and two data flow components that provide inputs to the Merge Join transformation.</span></span>  
  
 <span data-ttu-id="71906-104">병합 조인 변환에는 두 개의 정렬된 입력이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="71906-104">The Merge Join transformation requires two sorted inputs.</span></span> <span data-ttu-id="71906-105">자세한 내용은 [병합 및 병합 조인 변환을 위한 데이터 정렬](sort-data-for-the-merge-and-merge-join-transformations.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="71906-105">For more information, see [Sort Data for the Merge and Merge Join Transformations](sort-data-for-the-merge-and-merge-join-transformations.md).</span></span>  
  
### <a name="to-extend-a-dataset"></a><span data-ttu-id="71906-106">데이터 세트를 확장하려면</span><span class="sxs-lookup"><span data-stu-id="71906-106">To extend a dataset</span></span>  
  
1.  <span data-ttu-id="71906-107">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="71906-107">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="71906-108">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="71906-108">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="71906-109">**데이터 흐름** 탭을 클릭한 다음 **도구 상자**에서 병합 조인 변환을 디자인 화면으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="71906-109">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the Merge Join transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="71906-110">데이터 원본이나 이전 변환에서 연결선을 병합 조인 변환으로 끌어서 병합 조인 변환을 데이터 흐름에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="71906-110">Connect the Merge Join transformation to the data flow by dragging the connector from a data source or a previous transformation to the Merge Join transformation.</span></span>  
  
5.  <span data-ttu-id="71906-111">병합 조인 변환을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="71906-111">Double-click the Merge Join transformation.</span></span>  
  
6.  <span data-ttu-id="71906-112">**병합 조인 변환 편집기** 대화 상자의 **조인 유형** 목록에서 사용할 조인 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="71906-112">In the **Merge Join Transformation Editor** dialog box, select the type of join to use in the **Join type** list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="71906-113">**왼쪽 우선 외부 조인** 유형을 선택한 경우 **입력 바꾸기** 를 클릭하여 입력을 전환하고 왼쪽 우선 외부 조인을 오른쪽 우선 외부 조인으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71906-113">If you select the **Left outer join** type, you can click **Swap Inputs** to switch the inputs and convert the left outer join to a right outer join.</span></span>  
  
7.  <span data-ttu-id="71906-114">왼쪽 입력의 열을 오른쪽 입력의 열로 끌어서 조인 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="71906-114">Drag columns in the left input to columns in the right input to specify the join columns.</span></span> <span data-ttu-id="71906-115">열 이름이 같은 경우 **조인 키** 확인란을 선택하면 병합 조인 변환이 조인을 자동으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="71906-115">If the columns have the same name, you can select the **Join Key** check box and the Merge Join transformation automatically creates the join.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="71906-116">정렬 위치가 동일한 열 사이에서만 조인을 만들 수 있으며, 정렬 위치에 지정된 순서에 따라 조인을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71906-116">You can create joins only between columns that have the same sort position, and the joins must be created in the order specified by the sort position.</span></span> <span data-ttu-id="71906-117">순서를 다르게 해서 조인을 만들면 **병합 조인 변환 편집기** 에 생략된 정렬 순서 위치에 대한 추가 조인을 만들라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="71906-117">If you attempt to create the joins out of order, the **Merge Join Transformation Editor** prompts you to create additional joins for the skipped sort order positions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="71906-118">기본적으로 출력이 조인 열에서 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="71906-118">By default, the output is sorted on the join columns.</span></span>  
  
8.  <span data-ttu-id="71906-119">왼쪽 및 오른쪽 입력에서 출력에 포함시킬 추가 열의 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="71906-119">In the left and right inputs, select the check boxes of additional columns to include in the output.</span></span> <span data-ttu-id="71906-120">조인 열은 기본적으로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="71906-120">Join columns are included by default.</span></span>  
  
9. <span data-ttu-id="71906-121">필요에 따라 **출력 별칭** 열에서 출력 열의 이름을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="71906-121">Optionally, update the names of output columns in the **Output Alias** column.</span></span>  
  
10. <span data-ttu-id="71906-122">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="71906-122">Click **OK**.</span></span>  
  
11. <span data-ttu-id="71906-123">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="71906-123">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71906-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="71906-124">See Also</span></span>  
 <span data-ttu-id="71906-125">[병합 조인 변환](merge-join-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="71906-125">[Merge Join Transformation](merge-join-transformation.md) </span></span>  
 <span data-ttu-id="71906-126">[Integration Services 변환](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="71906-126">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="71906-127">[Integration Services 경로](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="71906-127">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 [<span data-ttu-id="71906-128">데이터 흐름 태스크</span><span class="sxs-lookup"><span data-stu-id="71906-128">Data Flow Task</span></span>](../../control-flow/data-flow-task.md)  
  
  
