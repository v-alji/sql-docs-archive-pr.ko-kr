---
title: 테이블 유형 지정 (데이터 마이닝 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.specifytabletypes.f1
ms.assetid: 8209a707-faef-4ffc-8991-6c13bb350753
author: minewiskan
ms.author: owend
ms.openlocfilehash: 88c09f26958c37ed0a99efb54a5eb5c08505d16b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653542"
---
# <a name="specify-table-types-data-mining-wizard"></a><span data-ttu-id="e2f63-102">테이블 유형 지정(데이터 마이닝 마법사)</span><span class="sxs-lookup"><span data-stu-id="e2f63-102">Specify Table Types (Data Mining Wizard)</span></span>
  <span data-ttu-id="e2f63-103">**테이블 유형 지정** 페이지를 사용하여 마이닝 구조 정의에 사용할 테이블을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f63-103">Use the **Specify Table Types** page to identify the tables to use to define the mining structure.</span></span> <span data-ttu-id="e2f63-104">선택하지 않은 테이블은 마이닝 구조 정의에 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f63-104">If a table is not selected, it will not be used to define the mining structure.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e2f63-105">나중에 **데이터 마이닝 디자이너**의 **마이닝 구조** 탭에서 테이블을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f63-105">You can add tables later from the **Mining Structure** tab in **Data Mining Designer**.</span></span>  
  
 <span data-ttu-id="e2f63-106">**자세한 내용:** [중첩 테이블&#40;Analysis Services - 데이터 마이닝&#41;](data-mining/nested-tables-analysis-services-data-mining.md), [데이터 마이닝 마법사&#40;Analysis Services - 데이터 마이닝&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [관계형 마이닝 구조 만들기](data-mining/create-a-relational-mining-structure.md)</span><span class="sxs-lookup"><span data-stu-id="e2f63-106">**For More Information:** [Nested Tables &#40;Analysis Services - Data Mining&#41;](data-mining/nested-tables-analysis-services-data-mining.md), [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="e2f63-107">옵션</span><span class="sxs-lookup"><span data-stu-id="e2f63-107">Options</span></span>  
 <span data-ttu-id="e2f63-108">**테이블**</span><span class="sxs-lookup"><span data-stu-id="e2f63-108">**Tables**</span></span>  
 <span data-ttu-id="e2f63-109">마법사의 **데이터 원본 뷰 선택** 페이지에서 선택한 데이터 원본 뷰에 테이블을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f63-109">Displays the tables in the data source view that you selected on the **Select Data Source View** page of the wizard.</span></span>  
  
 <span data-ttu-id="e2f63-110">**경우**</span><span class="sxs-lookup"><span data-stu-id="e2f63-110">**Case**</span></span>  
 <span data-ttu-id="e2f63-111">사례 테이블로 사용할 테이블을 하나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f63-111">Select one table to use as the case table.</span></span>  
  
 <span data-ttu-id="e2f63-112">**중첩됨**</span><span class="sxs-lookup"><span data-stu-id="e2f63-112">**Nested**</span></span>  
 <span data-ttu-id="e2f63-113">중첩 테이블로 사용할 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f63-113">Select the tables to use as nested tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e2f63-114">이러한 테이블은 사례 테이블과 일 대 다 관계가 아닌 다 대 일 관계여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f63-114">These tables must have a many-to-one relationship with the case table, not a one-to-many relationship.</span></span> <span data-ttu-id="e2f63-115">데이터 원본 뷰에 이 관계를 지정해야 테이블을 중첩으로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f63-115">You must specify this relationship in the data source view before you can select the table as nested.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2f63-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e2f63-116">See Also</span></span>  
 <span data-ttu-id="e2f63-117">[데이터 마이닝 마법사 F1 도움말 &#40;Analysis Services 데이터 마이닝&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="e2f63-117">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="e2f63-118">[데이터 마이닝 마법사 &#40;데이터 원본 뷰를 선택&#41;](select-data-source-view-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="e2f63-118">[Select Data Source View &#40;Data Mining Wizard&#41;](select-data-source-view-data-mining-wizard.md) </span></span>  
 [<span data-ttu-id="e2f63-119">데이터 마이닝 마법사 &#40;학습 데이터를 지정&#41;</span><span class="sxs-lookup"><span data-stu-id="e2f63-119">Specify the Training Data &#40;Data Mining Wizard&#41;</span></span>](specify-the-training-data-data-mining-wizard.md)  
  
  
