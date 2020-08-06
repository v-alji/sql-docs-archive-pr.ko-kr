---
title: 생성 방법 선택 (큐브 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubewizard.cubedefinition.f1
ms.assetid: 985d3b5b-7891-465b-862d-f7e75431b342
author: minewiskan
ms.author: owend
ms.openlocfilehash: c8c4d611e00a2b3f5d115ea5749b1e494a44bf57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659659"
---
# <a name="select-creation-method-cube-wizard"></a><span data-ttu-id="2f627-102">생성 방법 선택(큐브 마법사)</span><span class="sxs-lookup"><span data-stu-id="2f627-102">Select Creation Method (Cube Wizard)</span></span>
  <span data-ttu-id="2f627-103">**생성 방법 선택** 페이지를 사용하여 큐브를 만드는 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f627-103">Use the **Select Creation Method** page to specify how to create the cube.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2f627-104">옵션</span><span class="sxs-lookup"><span data-stu-id="2f627-104">Options</span></span>  
 <span data-ttu-id="2f627-105">**기존 테이블 사용**</span><span class="sxs-lookup"><span data-stu-id="2f627-105">**Use existing tables**</span></span>  
 <span data-ttu-id="2f627-106">데이터 원본에 있는 기존 테이블을 사용하여 큐브를 만들려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2f627-106">Select to create a cube by using existing tables in a data source.</span></span> <span data-ttu-id="2f627-107">마법사가 새 큐브를 만들기 위해 기존 테이블을 기반으로 측정값 그룹과 차원을 선택하고 정의하는 과정을 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="2f627-107">The wizard will guide you through the process of selecting and defining measure groups and dimensions based on existing tables to build your new cube.</span></span>  
  
 <span data-ttu-id="2f627-108">**빈 큐브 만들기**</span><span class="sxs-lookup"><span data-stu-id="2f627-108">**Create an empty cube**</span></span>  
 <span data-ttu-id="2f627-109">빈 큐브를 만들려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2f627-109">Select to create an empty cube.</span></span> <span data-ttu-id="2f627-110">이 옵션은 모든 항목을 직접 만들려고 하거나 큐브에 있는 모든 측정값 그룹이 연결된 측정값 그룹인 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="2f627-110">This option is useful when you want to create everything manually, or when all measure groups in the cube are linked measure groups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2f627-111">이 옵션은 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 프로젝트를 사용하여 작업하는 경우에만 사용할 수 있고 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스에 직접 연결하는 경우에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2f627-111">This option is only available when you are working with an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project and not when you are connected directly to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="2f627-112">**데이터 원본에 테이블 생성**</span><span class="sxs-lookup"><span data-stu-id="2f627-112">**Generate tables in the data source**</span></span>  
 <span data-ttu-id="2f627-113">큐브를 먼저 만든 다음 큐브 정의를 기반으로 데이터 원본에서 새 테이블을 생성하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2f627-113">Select to create a cube first and then generate new tables in the data source based on the cube definition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2f627-114">이 옵션을 사용하려면 기본 데이터 원본에 개체를 만들 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f627-114">To use this option, you must have permission to create objects in the underlying data source.</span></span>  
  
 <span data-ttu-id="2f627-115">이 옵션을 선택하면 **템플릿** 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f627-115">Selecting this option will make the **Template** option available.</span></span>  
  
 <span data-ttu-id="2f627-116">**템플릿**</span><span class="sxs-lookup"><span data-stu-id="2f627-116">**Template**</span></span>  
 <span data-ttu-id="2f627-117">큐브를 만드는 데 사용할 템플릿을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2f627-117">Select the template that you want to use to create the cube.</span></span> <span data-ttu-id="2f627-118">템플릿은 특정 비즈니스 용도를 위한 정의 집합을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2f627-118">Templates provide a set of definitions oriented towards a specific business purpose.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2f627-119">이 옵션은 **데이터 원본에 테이블 생성** 옵션을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f627-119">This option is only available when the **Generate tables in the data source** option has been selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f627-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2f627-120">See Also</span></span>  
 <span data-ttu-id="2f627-121">[큐브 개체는 Analysis Services 다차원 데이터를 &#40;&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="2f627-121">[Cube Objects &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="2f627-122">[다차원 모델의 큐브](multidimensional-models/cubes-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="2f627-122">[Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="2f627-123">다차원 모델의 차원</span><span class="sxs-lookup"><span data-stu-id="2f627-123">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
