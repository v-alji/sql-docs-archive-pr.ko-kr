---
title: 차원 쓰기 저장 (Writeback) 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying dimensions
- writeback [Analysis Services], setting up
- dimensions [Analysis Services], Business Intelligence enhancements
- Business Intelligence enhancements [Analysis Services], writeback
- dimensions [Analysis Services], writeback
- writeback [Analysis Services]
- dimensions [Analysis Services], modifying
- manual dimension structure modifications
ms.assetid: a4b5eb5a-366d-4fc8-ad0d-5bdb8e7b4163
author: minewiskan
ms.author: owend
ms.openlocfilehash: cba4a54e8a51d022c6f84a4c81d32f359a95692a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648656"
---
# <a name="enable-dimension-writeback"></a><span data-ttu-id="9995e-102">차원 쓰기 저장(writeback) 설정</span><span class="sxs-lookup"><span data-stu-id="9995e-102">Enable Dimension Writeback</span></span>
  <span data-ttu-id="9995e-103">큐브나 차원에 차원 쓰기 저장 기능을 추가하면 수동으로 차원 구조와 멤버를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9995e-103">Add the dimension writeback enhancement to a cube or dimension to allow users to manually modify the dimension structure and members.</span></span> <span data-ttu-id="9995e-104">쓰기 가능 차원에 대한 업데이트는 차원 테이블에 직접 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="9995e-104">Updates to a write-enabled dimension are recorded directly in the dimension table.</span></span> <span data-ttu-id="9995e-105">이 기능은 차원의 `WriteEnabled` 속성 설정을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="9995e-105">This enhancement changes the `WriteEnabled` property setting for a dimension.</span></span>  
  
 <span data-ttu-id="9995e-106">차원에 쓰기 저장 기능을 추가하려면 비즈니스 인텔리전스 마법사의 **기능 선택** 페이지에서 **차원 쓰기 저장(writeback) 설정** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9995e-106">To add dimension writeback, you use the Business Intelligence Wizard, and select the **Enable dimension writeback** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="9995e-107">그런 다음 마법사의 안내를 따라 차원 쓰기 저장을 적용할 차원을 선택하고 선택한 차원에 대해 이 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9995e-107">This wizard then guides you through the steps of selecting a dimension to which you want to apply dimension writeback and setting this option for the selected dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9995e-108">쓰기 저장은 SQL Server 관계형 데이터베이스 및 데이터 마트에 대해서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="9995e-108">Writeback is supported for SQL Server relational databases and data marts only.</span></span>  
  
## <a name="selecting-a-dimension"></a><span data-ttu-id="9995e-109">차원 선택</span><span class="sxs-lookup"><span data-stu-id="9995e-109">Selecting a Dimension</span></span>  
 <span data-ttu-id="9995e-110">마법사의 첫 번째 **차원 쓰기 저장(writeback) 설정** 페이지에서 차원 쓰기 저장을 적용할 차원을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9995e-110">On the first **Enable Dimension Writeback** page of the wizard, you specify the dimension to which you want to apply dimension writeback.</span></span> <span data-ttu-id="9995e-111">선택한 차원에 차원 쓰기 저장 기능을 추가하면 차원이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="9995e-111">The dimension writeback enhancement added to this selected dimension will result in changes to the dimension.</span></span> <span data-ttu-id="9995e-112">이러한 변경 내용은 선택된 차원을 포함하는 모든 큐브에 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="9995e-112">These changes will be inherited by all cubes that include the selected dimension.</span></span>  
  
## <a name="setting-dimension-writeback-capability"></a><span data-ttu-id="9995e-113">차원 쓰기 저장(Writeback) 기능 설정</span><span class="sxs-lookup"><span data-stu-id="9995e-113">Setting Dimension Writeback Capability</span></span>  
 <span data-ttu-id="9995e-114">마법사의 두 번째 **차원 쓰기 저장(writeback) 설정** 페이지에서 실제로 **차원에 쓰기 저장(writeback) 설정** 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9995e-114">On the second **Enable Dimension Writeback** page of the wizard, you actually set the **Enable writeback in the dimension** option.</span></span> <span data-ttu-id="9995e-115">이 옵션을 선택하면 자동으로 차원의 `WriteEnabled` 속성이 `True`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9995e-115">Selecting this option automatically sets the `WriteEnabled` property of the dimension to `True`.</span></span> <span data-ttu-id="9995e-116">이 옵션의 선택을 취소하면 자동으로 속성이 `False`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9995e-116">Clearing this option automatically sets the property to `False`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9995e-117">설명</span><span class="sxs-lookup"><span data-stu-id="9995e-117">Remarks</span></span>  
 <span data-ttu-id="9995e-118">새 멤버를 만들 때 차원에 모든 특성을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9995e-118">When you create a new member, you must include every attribute in a dimension.</span></span> <span data-ttu-id="9995e-119">차원의 키 특성 값을 지정하지 않고 멤버를 삽입할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9995e-119">You cannot insert a member without specifying a value for the key attribute of the dimension.</span></span> <span data-ttu-id="9995e-120">따라서 멤버를 만들 때는 차원 테이블에 정의된 모든 제약 조건(예: Null이 아닌 키 값)이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9995e-120">Therefore, creating members is subject to any constraints (such as non-null key values) that are defined on the dimension table.</span></span> <span data-ttu-id="9995e-121">`CustomRollupColumn`, `CustomRollupPropertiesColumn` 또는 `UnaryOperatorColumn`과 같은 차원 속성에 의해 선택적으로 지정된 열도 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9995e-121">You should also consider columns optionally specified by dimension properties, such as columns specified in the `CustomRollupColumn`, `CustomRollupPropertiesColumn` or the `UnaryOperatorColumn` dimension properties.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="9995e-122">SQL Azure를 데이터 원본으로 사용하여 Analysis Services에 쓰기 저장(writeback)을 수행할 경우 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="9995e-122">If you use SQL Azure as a data source to perform writeback into an Analysis Services database, the operation fails.</span></span> <span data-ttu-id="9995e-123">MARS(Multiple Active Result Set)를 활성화하는 공급자 옵션이 기본적으로 설정되어 있지 않기 때문에 이 작업이 실패하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9995e-123">This is by design, because the provider option that enables multiple active result sets (MARS) is not turned on by default.</span></span>  
>   
>  <span data-ttu-id="9995e-124">이 문제를 해결하려면 연결 문자열에 MARS를 지원하고 쓰기 저장(writeback)을 활성화하는 다음 설정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9995e-124">The workaround is to add the following setting in the connection string, to support MARS and to enable writeback:</span></span>  
>   
>  `"MultipleActiveResultSets=True"`  
>   
>  <span data-ttu-id="9995e-125">자세한 내용은 [MARS&#41;를 사용 하 여 여러 활성 결과 집합 &#40;사용 ](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9995e-125">For more information see [Using Multiple Active Result Sets &#40;MARS&#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9995e-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9995e-126">See Also</span></span>  
 [<span data-ttu-id="9995e-127">쓰기 가능 차원</span><span class="sxs-lookup"><span data-stu-id="9995e-127">Write-Enabled Dimensions</span></span>](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
