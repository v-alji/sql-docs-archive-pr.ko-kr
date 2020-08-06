---
title: 원본 정보 지정 (차원 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionmaintable.f1
ms.assetid: 0538b490-5185-49e1-a783-4ce3539a0de5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 99bbaac0bdf24a18dcde455e779f056b98106dc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653545"
---
# <a name="specify-source-information-dimension-wizard"></a><span data-ttu-id="869ad-102">원본 정보 지정(차원 마법사)</span><span class="sxs-lookup"><span data-stu-id="869ad-102">Specify Source Information (Dimension Wizard)</span></span>
  <span data-ttu-id="869ad-103">**주 차원 테이블 선택** 페이지를 사용하여 생성될 차원의 데이터 원본 뷰, 주 차원 테이블, 키 열 및 멤버 이름 열을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="869ad-103">Use the **Select the Main Dimension Table** page to select the data source view, main dimension table, key columns, and member name column for the dimension to be created.</span></span>  
  
 <span data-ttu-id="869ad-104">**차원 마법사를 열려면**</span><span class="sxs-lookup"><span data-stu-id="869ad-104">**To open the Dimension Wizard**</span></span>  
  
-   <span data-ttu-id="869ad-105">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]의 **솔루션 탐색기**에서 **프로젝트의** 차원 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 폴더를 마우스 오른쪽 단추로 클릭한 다음 **새 차원**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="869ad-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in **Solution Explorer**, right-click the **Dimensions** folder for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and then click **New Dimension**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="869ad-106">옵션</span><span class="sxs-lookup"><span data-stu-id="869ad-106">Options</span></span>  
 <span data-ttu-id="869ad-107">**데이터 원본 뷰**</span><span class="sxs-lookup"><span data-stu-id="869ad-107">**Data source view**</span></span>  
 <span data-ttu-id="869ad-108">데이터 원본 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="869ad-108">Select a data source view.</span></span>  
  
 <span data-ttu-id="869ad-109">**주 테이블**</span><span class="sxs-lookup"><span data-stu-id="869ad-109">**Main table**</span></span>  
 <span data-ttu-id="869ad-110">선택한 데이터 원본 뷰에서 차원의 주 테이블로 사용할 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="869ad-110">Select a table from the selected data source view to use as the main table for the dimension.</span></span>  
  
 <span data-ttu-id="869ad-111">**키 열**</span><span class="sxs-lookup"><span data-stu-id="869ad-111">**Key columns**</span></span>  
 <span data-ttu-id="869ad-112">**주 테이블** 에 지정된 테이블에서 차원의 키 특성에 대한 키 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="869ad-112">Select the key columns from the table specified in **Main table** for the key attribute of the dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="869ad-113">둘 이상의 열을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="869ad-113">More than one column can be selected.</span></span> <span data-ttu-id="869ad-114">테이블에 복합 기본 키가 있으면 복합 기본 키에 포함된 열을 모두 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="869ad-114">If the table contains a composite primary key, select all the columns included in the composite primary key.</span></span> <span data-ttu-id="869ad-115">키 열의 순서는 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="869ad-115">The order of the key columns is important.</span></span>  
  
 <span data-ttu-id="869ad-116">**이름 열**</span><span class="sxs-lookup"><span data-stu-id="869ad-116">**Name column**</span></span>  
 <span data-ttu-id="869ad-117">**주 테이블** 에 지정된 테이블에서 차원의 멤버 이름을 제공하는 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="869ad-117">Select the column from the table specified in **Main table** that provides the member names for the dimension.</span></span> <span data-ttu-id="869ad-118">복합 키를 사용하는 경우 이름 열을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="869ad-118">A name column must be specified when a composite key is used.</span></span> <span data-ttu-id="869ad-119">복합 키에 대한 이름 열을 만들려면 데이터 원본 뷰에 지정된 키 열을 연결하는 명명된 계산을 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="869ad-119">To create a name column for a composite key, we recommend that you create a named calculation in the data source view that concatenates the specified key columns.</span></span> <span data-ttu-id="869ad-120">단일 키를 사용하는 경우 이름 열은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="869ad-120">When a single key is used, the name column is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="869ad-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="869ad-121">See Also</span></span>  
 <span data-ttu-id="869ad-122">[차원 마법사 F1 도움말](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="869ad-122">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="869ad-123">[차원 &#40;Analysis Services 다차원 데이터&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="869ad-123">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="869ad-124">다차원 모델의 차원</span><span class="sxs-lookup"><span data-stu-id="869ad-124">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
