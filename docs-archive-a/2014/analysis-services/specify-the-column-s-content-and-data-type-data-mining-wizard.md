---
title: 열&#39;s 내용 및 데이터 형식 지정 (데이터 마이닝 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.specifycontentdatatype.f1
ms.assetid: 7061f674-e806-46f2-8c15-e260a3c69a17
author: minewiskan
ms.author: owend
ms.openlocfilehash: 66af7280e444036468b9cc33a131993524d3586d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653541"
---
# <a name="specify-the-column39s-content-and-data-type-data-mining-wizard"></a><span data-ttu-id="45262-102">열&#39;s 내용 및 데이터 형식 지정 (데이터 마이닝 마법사)</span><span class="sxs-lookup"><span data-stu-id="45262-102">Specify the Column&#39;s Content and Data Type (Data Mining Wizard)</span></span>
  <span data-ttu-id="45262-103">**열 내용 및 데이터 형식 지정** 페이지를 사용하여 마법사에서 이미 설정한 열 및 내용 유형을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45262-103">Use the **Specify the Column's Content and Data Type** page to modify the column and content types that have already been set by the wizard.</span></span> <span data-ttu-id="45262-104">마법사에서는 원본 열의 데이터 형식 및 선택한 알고리즘의 기능을 사용하여 각 열에 대한 기본 데이터 및 내용 유형을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="45262-104">The wizard uses the data types of the source columns and the capabilities of the selected algorithm to determine the default data and content types for each column.</span></span>  
  
 <span data-ttu-id="45262-105">**자세한 내용:** [데이터 마이닝 마법사&#40;Analysis Services - 데이터 마이닝&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [관계형 마이닝 구조 만들기](data-mining/create-a-relational-mining-structure.md)</span><span class="sxs-lookup"><span data-stu-id="45262-105">**For More Information:** [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="45262-106">옵션</span><span class="sxs-lookup"><span data-stu-id="45262-106">Options</span></span>  
 <span data-ttu-id="45262-107">**열**</span><span class="sxs-lookup"><span data-stu-id="45262-107">**Columns**</span></span>  
 <span data-ttu-id="45262-108">마법사의 **학습 데이터 지정** 페이지에서 정의한 열 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="45262-108">A list of the columns that are defined in the **Specify the Training Data** page of the wizard.</span></span>  
  
 <span data-ttu-id="45262-109">**콘텐츠 형식**</span><span class="sxs-lookup"><span data-stu-id="45262-109">**Content Type**</span></span>  
 <span data-ttu-id="45262-110">각 열에 할당된 내용 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="45262-110">The content type that is assigned to each column.</span></span> <span data-ttu-id="45262-111">내용 유형을 변경하려면 셀 안을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45262-111">Click inside a cell to change the content type.</span></span> <span data-ttu-id="45262-112">콘텐츠 형식에 대한 자세한 내용은 [콘텐츠 형식&#40;데이터 마이닝&#41;](data-mining/content-types-data-mining.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45262-112">For more information about content types, see [Content Types &#40;Data Mining&#41;](data-mining/content-types-data-mining.md).</span></span>  
  
 <span data-ttu-id="45262-113">**데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="45262-113">**Data Type**</span></span>  
 <span data-ttu-id="45262-114">각 열에 할당된 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="45262-114">The data types that are assigned to each column.</span></span> <span data-ttu-id="45262-115">데이터 형식을 변경하려면 셀 안을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45262-115">Click inside a cell to change the data type.</span></span> <span data-ttu-id="45262-116">데이터 형식에 대한 자세한 내용은 [데이터 형식&#40;데이터 마이닝&#41;](data-mining/data-types-data-mining.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45262-116">For more information about data types, see [Data Types &#40;Data Mining&#41;](data-mining/data-types-data-mining.md).</span></span>  
  
 <span data-ttu-id="45262-117">**검색**</span><span class="sxs-lookup"><span data-stu-id="45262-117">**Detect**</span></span>  
 <span data-ttu-id="45262-118">숫자 열에 대한 연속 내용 유형 및 불연속 내용 유형을 자동으로 검색하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45262-118">Click to automatically detect the continuous and discrete content types for numeric column.</span></span> <span data-ttu-id="45262-119">이 옵션은 OLAP 데이터 원본을 기반으로 하는 마이닝 구조에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="45262-119">This does not apply to mining structures that are based on OLAP data sources.</span></span> <span data-ttu-id="45262-120">OLAP 마이닝 구조의 경우 마법사에서는 자동으로 내용 유형을 검색하고 선택한 알고리즘과 호환되는 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="45262-120">For OLAP mining structures, the wizard automatically detects content types and chooses a type that is compatible with the selected algorithm.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45262-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="45262-121">See Also</span></span>  
 <span data-ttu-id="45262-122">[마법사 완료 &#40;데이터 마이닝 마법사&#41;](completing-the-wizard-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="45262-122">[Completing the Wizard &#40;Data Mining Wizard&#41;](completing-the-wizard-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="45262-123">[데이터 마이닝 마법사 F1 도움말 &#40;Analysis Services 데이터 마이닝&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="45262-123">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="45262-124">데이터 마이닝 마법사 &#40;학습 데이터를 지정&#41;</span><span class="sxs-lookup"><span data-stu-id="45262-124">Specify the Training Data &#40;Data Mining Wizard&#41;</span></span>](specify-the-training-data-data-mining-wizard.md)  
  
  
