---
title: UNION ALL 변환을 사용하여 데이터 병합 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- merging datasets [Integration Services]
- merging inputs [Integration Services]
- combining datasets
- Union All transformation
- datasets [Integration Services], merging
ms.assetid: 78304403-a81c-4101-b87e-ec80ddfdac98
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e782a5770ab9936e4c5cc84da706a5472ecd4d36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659559"
---
# <a name="merge-data-by-using-the-union-all-transformation"></a><span data-ttu-id="78f27-102">UNION ALL 변환을 사용하여 데이터 병합</span><span class="sxs-lookup"><span data-stu-id="78f27-102">Merge Data by Using the Union All Transformation</span></span>
  <span data-ttu-id="78f27-103">UNION ALL 변환을 추가 및 구성하려면 패키지에 적어도 하나 이상의 데이터 흐름 태스크와 두 개의 데이터 원본이 이미 들어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78f27-103">To add and configure a Union All transformation, the package must already include at least one Data Flow task and two data sources.</span></span>  
  
 <span data-ttu-id="78f27-104">UNION ALL 변환은 여러 입력을 조합합니다.</span><span class="sxs-lookup"><span data-stu-id="78f27-104">The Union All transformation combines multiple inputs.</span></span> <span data-ttu-id="78f27-105">변환에 연결된 첫 번째 입력은 참조 입력이며 이후에 연결되는 입력은 보조 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="78f27-105">The first input that is connected to the transformation is the reference input, and the inputs connected subsequently are the secondary inputs.</span></span> <span data-ttu-id="78f27-106">출력에는 참조 입력에 있는 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="78f27-106">The output includes the columns in the reference input.</span></span>  
  
### <a name="to-combine-inputs-in-a-data-flow"></a><span data-ttu-id="78f27-107">데이터 흐름에서 입력을 조합하려면</span><span class="sxs-lookup"><span data-stu-id="78f27-107">To combine inputs in a data flow</span></span>  
  
1.  <span data-ttu-id="78f27-108">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]의 솔루션 탐색기에서 패키지를 두 번 클릭하여 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 패키지를 연 후 **데이터 흐름** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="78f27-108">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], double-click the package in Solution Explorer to open the package in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, and then click the **Data Flow** tab.</span></span>  
  
2.  <span data-ttu-id="78f27-109">**도구 상자**에서 UNION ALL 변환을 **데이터 흐름** 탭의 디자인 화면으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="78f27-109">From the **Toolbox**, drag the Union All transformation to the design surface of the **Data Flow** tab.</span></span>  
  
3.  <span data-ttu-id="78f27-110">데이터 원본이나 이전 변환에서 연결선을 UNION ALL 변환으로 끌어서 UNION ALL 변환을 데이터 흐름에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="78f27-110">Connect the Union All transformation to the data flow by dragging a connector from the data source or a previous transformation to the Union All transformation.</span></span>  
  
4.  <span data-ttu-id="78f27-111">UNION ALL 변환을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="78f27-111">Double-click the Union All transformation.</span></span>  
  
5.  <span data-ttu-id="78f27-112">**UNION ALL 변환 편집기**에서 행을 클릭하여 입력의 열을 **출력 열 이름** 목록의 열로 매핑한 후 입력 목록에서 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="78f27-112">In the **Union All Transformation Editor**, map a column from an input to a column in the **Output Column Name** list by clicking a row and then selecting a column in the input list.</span></span> <span data-ttu-id="78f27-113">입력 열 목록에서 **\<ignore>** 를 선택하여 열 매핑을 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="78f27-113">Select **\<ignore>** in the input list to skip mapping the column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="78f27-114">두 열을 매핑하려면 해당 열의 메타데이터가 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78f27-114">The mapping between two columns requires that the metadata of the columns match.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="78f27-115">참조 열로 매핑되지 않은 보조 입력의 열은 출력에서 Null 값으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="78f27-115">Columns in a secondary input that are not mapped to reference columns are set to null values in the output.</span></span>  
  
6.  <span data-ttu-id="78f27-116">선택적으로 **출력 열 이름** 열에서 열의 이름을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="78f27-116">Optionally, modify the names of columns in the **Output Column Name** column.</span></span>  
  
7.  <span data-ttu-id="78f27-117">각 입력에 있는 각 열에 대해 5와 6단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="78f27-117">Repeat steps 5 and 6 for each column in each input.</span></span>  
  
8.  <span data-ttu-id="78f27-118">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="78f27-118">Click **OK**.</span></span>  
  
9. <span data-ttu-id="78f27-119">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="78f27-119">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78f27-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="78f27-120">See Also</span></span>  
 <span data-ttu-id="78f27-121">[UNION ALL 변환](union-all-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="78f27-121">[Union All Transformation](union-all-transformation.md) </span></span>  
 <span data-ttu-id="78f27-122">[Integration Services 변환](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="78f27-122">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="78f27-123">[Integration Services 경로](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="78f27-123">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 [<span data-ttu-id="78f27-124">데이터 흐름 태스크</span><span class="sxs-lookup"><span data-stu-id="78f27-124">Data Flow Task</span></span>](../../control-flow/data-flow-task.md)  
  
  
