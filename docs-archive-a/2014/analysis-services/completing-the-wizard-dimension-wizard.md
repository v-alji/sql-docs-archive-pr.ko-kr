---
title: 마법사 완료 (차원 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.finish.f1
ms.assetid: 1137740d-3063-4ab1-9cfe-8319194db937
author: minewiskan
ms.author: owend
ms.openlocfilehash: 61f6bf16ea38ab88995ff06ba31a06feb976d900
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648664"
---
# <a name="completing-the-wizard-dimension-wizard"></a><span data-ttu-id="f0eb2-102">마법사 완료(차원 마법사)</span><span class="sxs-lookup"><span data-stu-id="f0eb2-102">Completing the Wizard (Dimension Wizard)</span></span>
  <span data-ttu-id="f0eb2-103">**마법사 완료** 페이지를 사용하여 다음 절차를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0eb2-103">Use the **Completing the Wizard** page to do the following procedures:</span></span>  
  
-   <span data-ttu-id="f0eb2-104">차원 이름 지정</span><span class="sxs-lookup"><span data-stu-id="f0eb2-104">Name the dimension.</span></span>  
  
-   <span data-ttu-id="f0eb2-105">**마침** 을 클릭할 때 변경되는 내용 검토</span><span class="sxs-lookup"><span data-stu-id="f0eb2-105">Review the changes that will be made when **Finish** is clicked.</span></span>  
  
-   <span data-ttu-id="f0eb2-106">필요한 경우 차원을 지원하는 데 필요한 스키마 생성</span><span class="sxs-lookup"><span data-stu-id="f0eb2-106">If necessary, generate the schema needed to support the dimension.</span></span>  
  
 <span data-ttu-id="f0eb2-107">**차원 마법사를 열려면**</span><span class="sxs-lookup"><span data-stu-id="f0eb2-107">**To open the Dimension Wizard**</span></span>  
  
-   <span data-ttu-id="f0eb2-108">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]의 **솔루션 탐색기**에서 **프로젝트의** 차원 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 폴더를 마우스 오른쪽 단추로 클릭한 다음 **새 차원**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eb2-108">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in **Solution Explorer**, right-click the **Dimensions** folder for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and then click **New Dimension**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f0eb2-109">옵션</span><span class="sxs-lookup"><span data-stu-id="f0eb2-109">Options</span></span>  
 <span data-ttu-id="f0eb2-110">**이름**</span><span class="sxs-lookup"><span data-stu-id="f0eb2-110">**Name**</span></span>  
 <span data-ttu-id="f0eb2-111">새 차원의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eb2-111">Type the name of the new dimension.</span></span>  
  
 <span data-ttu-id="f0eb2-112">**미리 보기**</span><span class="sxs-lookup"><span data-stu-id="f0eb2-112">**Preview**</span></span>  
 <span data-ttu-id="f0eb2-113">새 차원에 대해 생성될 차원 특성과 계층을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eb2-113">Displays the dimension attributes and hierarchies to be created for the new dimension.</span></span>  
  
 <span data-ttu-id="f0eb2-114">**지금 스키마 생성**</span><span class="sxs-lookup"><span data-stu-id="f0eb2-114">**Generate schema now**</span></span>  
 <span data-ttu-id="f0eb2-115">차원을 지원하는 데 필요한 스키마를 생성하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eb2-115">Select to generate the schema needed to support the dimension.</span></span> <span data-ttu-id="f0eb2-116">이 옵션을 선택하면 스키마 생성 마법사가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="f0eb2-116">Selecting this option opens the Schema Generation Wizard.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f0eb2-117">이 옵션은 **생성 방법 선택** 페이지에서 **데이터 원본에 시간 테이블 생성** 또는 **데이터 원본에 시간이 아닌 테이블 생성**을 선택한 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0eb2-117">This option appears only if you selected **Generate a time table in the data source** or **Generate a non-time table in the data source** on the **Select Creation Method** page.</span></span> <span data-ttu-id="f0eb2-118">자세한 내용은 [생성 방법 선택&#40;차원 마법사&#41;](select-creation-method-dimension-wizard.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0eb2-118">For more information, see [Select Creation Method &#40;Dimension Wizard&#41;](select-creation-method-dimension-wizard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0eb2-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f0eb2-119">See Also</span></span>  
 <span data-ttu-id="f0eb2-120">[차원 마법사 F1 도움말](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="f0eb2-120">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="f0eb2-121">[차원 &#40;Analysis Services 다차원 데이터&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="f0eb2-121">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="f0eb2-122">다차원 모델의 차원</span><span class="sxs-lookup"><span data-stu-id="f0eb2-122">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
