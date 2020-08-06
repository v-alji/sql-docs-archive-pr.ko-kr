---
title: 데이터 마이닝 차원 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], dimensions
ms.assetid: 9f0c39e5-3516-43ab-b203-f3f6dbcff89a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 265cf671bbc825258f0b2bd6627690e8c52f252b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727475"
---
# <a name="create-a-data-mining-dimension"></a><span data-ttu-id="9826c-102">데이터 마이닝 차원 만들기</span><span class="sxs-lookup"><span data-stu-id="9826c-102">Create a Data Mining Dimension</span></span>
  <span data-ttu-id="9826c-103">마이닝 구조가 OLAP 큐브를 기반으로 하는 경우에는 마이닝 모델의 내용을 포함하는 차원을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9826c-103">If your mining structure is based on an OLAP cube, you can create a dimension that contains the content of the mining model.</span></span> <span data-ttu-id="9826c-104">그런 다음 차원을 다시 원본 큐브에 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9826c-104">You can then incorporate the dimension back into the source cube.</span></span>  
  
 <span data-ttu-id="9826c-105">또한 차원을 찾아보거나 차원을 사용하여 모델 결과를 탐색하거나 MDX를 사용하여 차원을 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9826c-105">You can also browse the dimension, use it to explore the model results, or query the dimension using MDX.</span></span>  
  
### <a name="to-create-a-data-mining-dimension"></a><span data-ttu-id="9826c-106">데이터 마이닝 차원을 만들려면</span><span class="sxs-lookup"><span data-stu-id="9826c-106">To create a data mining dimension</span></span>  
  
1.  <span data-ttu-id="9826c-107">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]의 데이터 마이닝 디자이너에서 **마이닝 구조** 탭이나 **마이닝 모델** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9826c-107">In Data Mining Designer in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], select either the **Mining Structure** tab or the **Mining Models** tab.</span></span>  
  
2.  <span data-ttu-id="9826c-108">**마이닝 모델** 메뉴에서 **데이터 마이닝 차원 만들기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9826c-108">From the **Mining Model** menu, select **Create a Data Mining Dimension**.</span></span>  
  
     <span data-ttu-id="9826c-109">**데이터 마이닝 차원 만들기** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="9826c-109">The **Create Data Mining Dimension** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="9826c-110">**데이터 마이닝 차원 만들기** 대화 상자의 **모델 이름** 목록에서 OLAP 마이닝 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9826c-110">In the **Model name** list of the **Create Data Mining Dimension** dialog box, select an OLAP mining model.</span></span>  
  
4.  <span data-ttu-id="9826c-111">**차원 이름** 입력란에 새 데이터 마이닝 차원의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9826c-111">In the **Dimension name** box, enter a name for the new data mining dimension.</span></span>  
  
5.  <span data-ttu-id="9826c-112">새 데이터 마이닝 차원을 포함하는 큐브를 만들려면 **큐브 만들기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9826c-112">If you want to create a cube that includes the new data mining dimension, select **Create cube**.</span></span> <span data-ttu-id="9826c-113">**큐브 만들기**를 선택한 후에는 큐브의 새 이름을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9826c-113">After you select **Create cube**, you can enter a new name for the cube.</span></span>  
  
6.  <span data-ttu-id="9826c-114">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9826c-114">Click **OK**.</span></span>  
  
     <span data-ttu-id="9826c-115">데이터 마이닝 차원이 생성되어 솔루션 탐색기의 **차원** 폴더에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="9826c-115">The data mining dimension is created and is added to the **Dimensions** folder in Solution Explorer.</span></span> <span data-ttu-id="9826c-116">**큐브 만들기**를 선택한 경우에는 새 큐브도 생성되어 **큐브** 폴더에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="9826c-116">If you selected **Create cube**, a new cube is also created and is added to the **Cubes** folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9826c-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9826c-117">See Also</span></span>  
 [<span data-ttu-id="9826c-118">마이닝 구조 태스크 및 방법</span><span class="sxs-lookup"><span data-stu-id="9826c-118">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
  
