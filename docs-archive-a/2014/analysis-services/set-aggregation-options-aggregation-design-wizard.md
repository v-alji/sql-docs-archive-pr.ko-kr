---
title: 집계 옵션 설정 (집계 디자인 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.storagedesignwizard.setaggregateoptions.f1
ms.assetid: 4672d686-10c0-43f8-a53e-a16dfa840c81
author: minewiskan
ms.author: owend
ms.openlocfilehash: c1970e13ca6532ebbeb71e1401a75677bf7a89aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736910"
---
# <a name="set-aggregation-options-aggregation-design-wizard"></a><span data-ttu-id="2c71d-102">집계 옵션 설정(집계 디자인 마법사)</span><span class="sxs-lookup"><span data-stu-id="2c71d-102">Set Aggregation Options (Aggregation Design Wizard)</span></span>
  <span data-ttu-id="2c71d-103">**집계 옵션 설정** 페이지를 사용하여 집계 디자인 프로세스를 시작하고 생성된 집계에 대해 스토리지 또는 성능 제한을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c71d-103">Use the **Set Aggregation Options** page to start the aggregation design process, and specify storage or performance limits for the generated aggregations.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2c71d-104">옵션</span><span class="sxs-lookup"><span data-stu-id="2c71d-104">Options</span></span>  
 <span data-ttu-id="2c71d-105">**다음 예상 스토리지 크기까지**</span><span class="sxs-lookup"><span data-stu-id="2c71d-105">**Estimated storage reaches**</span></span>  
 <span data-ttu-id="2c71d-106">집계를 생성하는 데 사용할 수 있는 최대 메가바이트(MB) 또는 기가바이트(GB) 수를 지정하여 집계 디자인을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="2c71d-106">Limit the aggregation design by indicating the maximum number of megabytes (MB) or gigabytes (GB) that can be used to generate the aggregations.</span></span>  
  
 <span data-ttu-id="2c71d-107">**다음 성능 향상 정도까지**</span><span class="sxs-lookup"><span data-stu-id="2c71d-107">**Performance gain reaches**</span></span>  
 <span data-ttu-id="2c71d-108">집계 디자인에서 제공할 수 있는 최대 예상 성능 향상률을 지정하여 집계 디자인을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="2c71d-108">Limit the aggregation design by indicating the maximum percentage of estimated performance gain that the aggregation design can provided.</span></span>  
  
 <span data-ttu-id="2c71d-109">**[중지]를 클릭할 때까지**</span><span class="sxs-lookup"><span data-stu-id="2c71d-109">**I click Stop**</span></span>  
 <span data-ttu-id="2c71d-110">디자인 프로세스 중에 **중지** 를 클릭하여 집계 디자인을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="2c71d-110">Limit the aggregation design by clicking **Stop** during the design process.</span></span>  
  
 <span data-ttu-id="2c71d-111">**집계 디자인 안 함(0%)**</span><span class="sxs-lookup"><span data-stu-id="2c71d-111">**Do not design aggregations (0%)**</span></span>  
 <span data-ttu-id="2c71d-112">집계 디자인에 집계가 포함되지 않도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2c71d-112">Specify that the aggregation design contains no aggregations.</span></span> <span data-ttu-id="2c71d-113">이 옵션을 사용하여 파티션, 측정값 그룹 또는 큐브에 대한 기존 집계 디자인을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c71d-113">Use this option to clear an existing aggregation design for a partition, measure group, or cube.</span></span>  
  
 <span data-ttu-id="2c71d-114">**시작**</span><span class="sxs-lookup"><span data-stu-id="2c71d-114">**Start**</span></span>  
 <span data-ttu-id="2c71d-115">집계 디자인 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2c71d-115">Starts the aggregation design process.</span></span>  
  
 <span data-ttu-id="2c71d-116">**중지**</span><span class="sxs-lookup"><span data-stu-id="2c71d-116">**Stop**</span></span>  
 <span data-ttu-id="2c71d-117">집계 디자인 프로세스를 끝냅니다.</span><span class="sxs-lookup"><span data-stu-id="2c71d-117">Ends the aggregation design process.</span></span>  
  
 <span data-ttu-id="2c71d-118">**재설정**</span><span class="sxs-lookup"><span data-stu-id="2c71d-118">**Reset**</span></span>  
 <span data-ttu-id="2c71d-119">이 페이지의 모든 집계 옵션을 기본값으로 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2c71d-119">Resets all the aggregation options on this page to their default values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c71d-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2c71d-120">See Also</span></span>  
 <span data-ttu-id="2c71d-121">[집계 디자인 마법사 F1 도움말](aggregation-design-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="2c71d-121">[Aggregation Design Wizard F1 Help](aggregation-design-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="2c71d-122">다차원 데이터를 &#40;마법사 Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="2c71d-122">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
