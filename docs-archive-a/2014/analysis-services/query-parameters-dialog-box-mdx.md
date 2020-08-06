---
title: 쿼리 매개 변수 대화 상자 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.queryparameters.mdx.f1
ms.assetid: e69b9542-7b54-42bf-b2de-c091e81af7ee
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1eee07ffefc0b2d7c6115245e12d09c5ac6eb4a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738931"
---
# <a name="query-parameters-dialog-box-mdx"></a><span data-ttu-id="2889d-102">쿼리 매개 변수 대화 상자(MDX)</span><span class="sxs-lookup"><span data-stu-id="2889d-102">Query Parameters Dialog Box (MDX)</span></span>
  <span data-ttu-id="2889d-103">**및** 에서 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 쿼리 매개 변수 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 대화 상자를 사용하여 집합, 차원 및 하위 큐브를 정의하는 데 사용되는 MDX 쿼리에 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2889d-103">Use the **Query Parameters** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to add parameters to MDX queries that are used to define sets, dimensions, and subcubes.</span></span> <span data-ttu-id="2889d-104">**MDX 쿼리 작성기** 대화 상자에서 **매개 변수** 아이콘을 클릭하여 **쿼리 매개 변수** 대화 상자를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2889d-104">You can display the **Query Parameters** dialog box by clicking the **Parameters** icon in the **MDX query builder** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2889d-105">옵션</span><span class="sxs-lookup"><span data-stu-id="2889d-105">Options</span></span>  
 <span data-ttu-id="2889d-106">**매개 변수**</span><span class="sxs-lookup"><span data-stu-id="2889d-106">**Parameter**</span></span>  
 <span data-ttu-id="2889d-107">매개 변수 이름을 입력하여 새 매개 변수를 만들거나 기존 매개 변수의 이름을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="2889d-107">Type a parameter name to begin creating a new parameter, or edit the name of an existing parameter.</span></span>  
  
 <span data-ttu-id="2889d-108">**크기**</span><span class="sxs-lookup"><span data-stu-id="2889d-108">**Dimension**</span></span>  
 <span data-ttu-id="2889d-109">목록에서 기존 차원을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2889d-109">Choose an existing dimension from the list.</span></span>  
  
 <span data-ttu-id="2889d-110">**계층**</span><span class="sxs-lookup"><span data-stu-id="2889d-110">**Hierarchy**</span></span>  
 <span data-ttu-id="2889d-111">매개 변수가 특정 계층에 적용된 경우 목록에서 계층을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2889d-111">Choose a hierarchy from the list, if the parameter is applied to a specific hierarchy.</span></span>  
  
 <span data-ttu-id="2889d-112">**다중 값**</span><span class="sxs-lookup"><span data-stu-id="2889d-112">**Multiple values**</span></span>  
 <span data-ttu-id="2889d-113">Description</span><span class="sxs-lookup"><span data-stu-id="2889d-113">Description</span></span>  
  
 <span data-ttu-id="2889d-114">**기본값**</span><span class="sxs-lookup"><span data-stu-id="2889d-114">**Default**</span></span>  
 <span data-ttu-id="2889d-115">필요에 따라 매개 변수에 대한 기본값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2889d-115">Indicate the default value for the parameter, if any.</span></span> <span data-ttu-id="2889d-116">기본적으로 값이 지정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2889d-116">By default, no value is assigned.</span></span>  
  
 <span data-ttu-id="2889d-117">**기타**</span><span class="sxs-lookup"><span data-stu-id="2889d-117">**Other**</span></span>  
 <span data-ttu-id="2889d-118">더 이상 사용하지 않는 매개 변수를 제거하려면 Delete 키 또는 X 단추를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2889d-118">Use the Delete key or X button to remove parameters you no long use.</span></span> <span data-ttu-id="2889d-119">강조 표시된 매개 변수를 목록에서 위 또는 아래로 이동하려면 화살표 키를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2889d-119">Use the arrow keys to move the highlighted parameter up or down in the list.</span></span> <span data-ttu-id="2889d-120">다음 규칙은 매개 변수 순서에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2889d-120">The following rules apply to ordering of parameters:</span></span>  
  
-   <span data-ttu-id="2889d-121">매개 변수 범위 지정</span><span class="sxs-lookup"><span data-stu-id="2889d-121">Parameter scoping.</span></span>  
  
-   <span data-ttu-id="2889d-122">매개 변수 순서</span><span class="sxs-lookup"><span data-stu-id="2889d-122">Parameter order.</span></span>  
  
  
