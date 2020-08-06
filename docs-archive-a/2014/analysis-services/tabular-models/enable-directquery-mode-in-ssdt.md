---
title: DirectQuery 디자인 모드 사용 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 71fc7ebd-2e86-4a76-994b-66d3a57bcc9b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8ccd2dc88f447e78f6558565a89accc341eac37c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651914"
---
# <a name="enable-directquery-design-mode-ssas-tabular"></a><span data-ttu-id="2a492-102">DirectQuery 디자인 모드를 사용하도록 설정(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="2a492-102">Enable DirectQuery Design Mode (SSAS Tabular)</span></span>
  <span data-ttu-id="2a492-103">DirectQuery 모드에서 모델을 만들려면 먼저 DirectQuery 모드 사용자를 지원하도록 디자인 타임 환경을 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a492-103">To create a model in DirectQuery mode, you must first change the design-time environment so that it supports the user of DirectQuery mode.</span></span> <span data-ttu-id="2a492-104">이렇게 하면 디자이너에서 다음과 같은 작업이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a492-104">When you do so, the designer will also do the following:</span></span>  
  
-   <span data-ttu-id="2a492-105">DirectQuery 배포 속성을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2a492-105">Enable the use of the DirectQuery deployment properties.</span></span>  
  
-   <span data-ttu-id="2a492-106">작업 영역 데이터베이스를 디자인에 캐시를 사용하는 혼합 모드에서 실행되도록 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="2a492-106">Change the workspace database to run in a hybrid mode that uses the cache for designing.</span></span> <span data-ttu-id="2a492-107">실제로 모델을 배포할 때는 모드가 프로젝트 배포 속성에 지정한 값으로 다시 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a492-107">When you actually deploy the model, the mode will be changed back to whatever value you specified in the project deployment properties.</span></span>  
  
-   <span data-ttu-id="2a492-108">DirectQuery 모드와 호환되지 않는 디자인 기능을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2a492-108">Disable design features that are incompatible with DirectQuery mode.</span></span>  
  
-   <span data-ttu-id="2a492-109">기존 모델의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="2a492-109">Validate the existing model.</span></span>  
  
 <span data-ttu-id="2a492-110">이 절차에서는 디자이너에서 DirectQuery 모드를 사용하도록 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2a492-110">This procedure describes how to enable DirectQuery mode in the designer.</span></span>  
  
### <a name="to-enable-use-of-directquery-in-a-model"></a><span data-ttu-id="2a492-111">모델에서 DirectQuery를 사용하도록 설정하려면</span><span class="sxs-lookup"><span data-stu-id="2a492-111">To enable use of DirectQuery in a model</span></span>  
  
1.  <span data-ttu-id="2a492-112">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 솔루션 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2a492-112">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the solution file.</span></span>  
  
2.  <span data-ttu-id="2a492-113">개체 탐색기에서 Model.bim 파일을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2a492-113">In Object Explorer, double-click the Model.bim file.</span></span>  
  
3.  <span data-ttu-id="2a492-114">**속성** 창에서 **DirectQueryMode**속성을 **On**으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="2a492-114">In the **Properties** pane, change the property, **DirectQueryMode**, to **On**.</span></span>  
  
4.  <span data-ttu-id="2a492-115">오류가 발생하면 Visual Studio에서 **오류 목록** 을 열고 모델을 DirectQuery 모드로 전환할 수 없도록 하는 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="2a492-115">If there are errors, in Visual Studio, open the **Error List** and resolve any problems that would prevent the model from being switched to DirectQuery mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a492-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2a492-116">See Also</span></span>  
 [<span data-ttu-id="2a492-117">DirectQuery 모드&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="2a492-117">DirectQuery Mode &#40;SSAS Tabular&#41;</span></span>](directquery-mode-ssas-tabular.md)  
  
  
