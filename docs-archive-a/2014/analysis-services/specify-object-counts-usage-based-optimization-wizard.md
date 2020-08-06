---
title: 개체 수 지정 (사용 빈도 기반 최적화 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.storagedesignwizard.calculatingobjectcounts.f1
ms.assetid: 306c7c25-ae24-4852-ab8c-c82f68a4bc1f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 862be19f12308def815a280dba04f42f0cbe6878
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653547"
---
# <a name="specify-object-counts-usage-based-optimization-wizard"></a><span data-ttu-id="cda86-102">개체 수 지정(사용 빈도 기반 최적화 마법사)</span><span class="sxs-lookup"><span data-stu-id="cda86-102">Specify Object Counts (Usage-Based Optimization Wizard)</span></span>
  <span data-ttu-id="cda86-103">**개체 수 지정** 페이지를 사용하여 큐브의 개체 수를 자동으로 계산하거나 예상 개수를 직접 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cda86-103">Use the **Specify Object Counts** page to automatically calculate the count of objects in the cube or to manually enter estimated counts.</span></span> <span data-ttu-id="cda86-104">사용 빈도 기반 최적화 마법사는 개체 수를 사용하여 스토리지 요구 사항을 예상합니다.</span><span class="sxs-lookup"><span data-stu-id="cda86-104">The Usage-Based Optimization Wizard uses the object counts to estimate storage requirements.</span></span>  
  
## <a name="options"></a><span data-ttu-id="cda86-105">옵션</span><span class="sxs-lookup"><span data-stu-id="cda86-105">Options</span></span>  
 <span data-ttu-id="cda86-106">**큐브 개체**</span><span class="sxs-lookup"><span data-stu-id="cda86-106">**Cube Objects**</span></span>  
 <span data-ttu-id="cda86-107">큐브의 차원 및 특성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cda86-107">Displays the dimensions and attributes in the cube.</span></span> <span data-ttu-id="cda86-108">`AggregationUsage`마법사의 **집계 사용 검토** 페이지에서 해당 속성이 None으로 설정 되지 않은 특성만 표시 됩니다 .이 특성은 개수를 지정 해야 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="cda86-108">Only the attributes that do not have their `AggregationUsage` property set to None in the **Review Aggregation Usage** page of the wizard are shown because those are the only attributes that need counts specified.</span></span>  
  
 <span data-ttu-id="cda86-109">**예상 개수**</span><span class="sxs-lookup"><span data-stu-id="cda86-109">**Estimated count**</span></span>  
 <span data-ttu-id="cda86-110">측정값 그룹의 예상 행 수와 데이터베이스 차원의 예상 특성 멤버 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cda86-110">Displays the estimated number of rows in the measure group and the estimated attribute member counts in the database dimensions.</span></span> <span data-ttu-id="cda86-111">예상 개수로 사용할 값을 입력하거나 예상 개수 값을 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cda86-111">You can type a value to use as the estimated count or you can calculate the estimated count values.</span></span> <span data-ttu-id="cda86-112">개수 값을 계산하려면 필드에 0 을 입력한 다음 **개수**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cda86-112">To calculate the count values, type 0 in the field and then click **Count**.</span></span> <span data-ttu-id="cda86-113">이미 수가 표시된 필드는 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cda86-113">Fields that already display a count are not updated.</span></span>  
  
 <span data-ttu-id="cda86-114">**분할 개수**</span><span class="sxs-lookup"><span data-stu-id="cda86-114">**Partition count**</span></span>  
 <span data-ttu-id="cda86-115">(옵션) 측정값 그룹의 예상 행 수와 파티션의 예상 특성 멤버 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cda86-115">(Optional) Type the estimated number of rows in the measure group and the estimated attribute member counts in the partitions.</span></span>  
  
 <span data-ttu-id="cda86-116">**Count**</span><span class="sxs-lookup"><span data-stu-id="cda86-116">**Count**</span></span>  
 <span data-ttu-id="cda86-117">모든 빈 필드에 대해 **예상 개수** 열의 값을 계산하고 다시 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="cda86-117">Calculates and repopulates the values in the **Estimated count** column for all empty fields.</span></span> <span data-ttu-id="cda86-118">이미 수가 표시된 필드는 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cda86-118">Fields that already display a count are not updated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cda86-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cda86-119">See Also</span></span>  
 <span data-ttu-id="cda86-120">[집계 디자인 마법사 F1 도움말](aggregation-design-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="cda86-120">[Aggregation Design Wizard F1 Help](aggregation-design-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="cda86-121">다차원 데이터를 &#40;마법사 Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="cda86-121">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
