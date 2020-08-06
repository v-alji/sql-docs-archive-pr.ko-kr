---
title: 느린 변경 차원 열(느린 변경 차원 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.scdsupport.f1
ms.assetid: 36de99d5-5368-48e0-b876-17e9c6862c6c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6283887cbddb9844e0ac769281184f588dc2a94d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728508"
---
# <a name="slowly-changing-dimension-columns-slowly-changing-dimension-wizard"></a><span data-ttu-id="738d4-102">느린 변경 차원 열(느린 변경 차원 마법사)</span><span class="sxs-lookup"><span data-stu-id="738d4-102">Slowly Changing Dimension Columns (Slowly Changing Dimension Wizard)</span></span>
  <span data-ttu-id="738d4-103">**느린 변경 차원 열** 대화 상자를 사용하여 각 느린 변경 차원 열의 변경 유형을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="738d4-103">Use the **Slowly Changing Dimensions Columns** dialog box to select a change type for each slowly changing dimension column.</span></span>  
  
 <span data-ttu-id="738d4-104">이 마법사에 대한 자세한 내용은 [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="738d4-104">To learn more about this wizard, see [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="738d4-105">옵션</span><span class="sxs-lookup"><span data-stu-id="738d4-105">Options</span></span>  
 <span data-ttu-id="738d4-106">**차원 열**</span><span class="sxs-lookup"><span data-stu-id="738d4-106">**Dimension Columns**</span></span>  
 <span data-ttu-id="738d4-107">목록에서 차원 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="738d4-107">Select a dimension column from the list.</span></span>  
  
 <span data-ttu-id="738d4-108">**변경 유형**</span><span class="sxs-lookup"><span data-stu-id="738d4-108">**Change Type**</span></span>  
 <span data-ttu-id="738d4-109">**고정 특성**을 선택하거나 두 변경 특성 유형 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="738d4-109">Select a **Fixed Attribute**, or select one of the two types of changing attributes.</span></span> <span data-ttu-id="738d4-110">열 값이 변경되지 않을 경우에는 **고정 특성** 을 사용합니다. 이렇게 하면 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 에서 변경 내용을 오류로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="738d4-110">Use **Fixed Attribute** when the value in a column should not change; [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] then treats changes as errors.</span></span> <span data-ttu-id="738d4-111">변경된 값으로 기존 값을 덮어쓰려면 **변경 특성** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="738d4-111">Use **Changing Attribute** to overwrite existing values with changed values.</span></span> <span data-ttu-id="738d4-112">변경된 값을 새 레코드에 저장하고 이전 레코드는 오래된 레코드로 표시하려면 **기록 특성** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="738d4-112">Use **Historical Attribute** to save changed values in new records, while marking previous records as outdated.</span></span>  
  
 <span data-ttu-id="738d4-113">**제거**</span><span class="sxs-lookup"><span data-stu-id="738d4-113">**Remove**</span></span>  
 <span data-ttu-id="738d4-114">매핑된 열 목록에서 차원 열을 제거하려면 열을 선택한 후 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="738d4-114">Select a dimension column, and remove it from the list of mapped columns by clicking **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="738d4-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="738d4-115">See Also</span></span>  
 [<span data-ttu-id="738d4-116">느린 변경 차원 마법사를 사용하여 출력 구성</span><span class="sxs-lookup"><span data-stu-id="738d4-116">Configure Outputs Using the Slowly Changing Dimension Wizard</span></span>](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
