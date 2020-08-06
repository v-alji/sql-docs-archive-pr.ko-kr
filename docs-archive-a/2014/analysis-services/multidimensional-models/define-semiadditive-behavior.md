---
title: 반 가산적 동작 정의 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- semiadditive
- Business Intelligence enhancements [Analysis Services], semiadditive behavior
- measures [Analysis Services], semiadditive
ms.assetid: b25726bc-728b-4601-ad87-9015c39dc615
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9c2028c350046fdcc9f98bcd0f0612d6a91ccabb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651379"
---
# <a name="define-semiadditive-behavior"></a><span data-ttu-id="ce1e1-102">반가산적 동작 정의</span><span class="sxs-lookup"><span data-stu-id="ce1e1-102">Define Semiadditive Behavior</span></span>
  <span data-ttu-id="ce1e1-103">다양한 비즈니스 시나리오에서 모든 차원에 대해 균일하게 집계되지 않는 반가산적 측정값이 있는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-103">Semiadditive measures, which do not uniformly aggregate across all dimensions, are very common in many business scenarios.</span></span> <span data-ttu-id="ce1e1-104">시간에 따른 균형에 대한 스냅샷을 기반으로 하는 모든 큐브에서 이 문제가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-104">Every cube that is based on snapshots of balances over time exhibits this problem.</span></span> <span data-ttu-id="ce1e1-105">보안, 잔액, 예산, 인력 관리, 보험 정책, 지불 청구 및 기타 비즈니스 분야를 처리하는 애플리케이션에서 이러한 스냅샷을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-105">You can find these snapshots in applications dealing with securities, account balances, budgeting, human resources, insurance policies and claims, and many other business domains.</span></span>  
  
 <span data-ttu-id="ce1e1-106">큐브에 반가산적 동작을 추가하여 개별 측정값이나 해당 계정 유형 특성의 멤버에 대한 집계 방법을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-106">Add semiadditive behavior to a cube to define an aggregation method for individual measures or members of the account type attribute.</span></span> <span data-ttu-id="ce1e1-107">큐브에 계정 차원이 포함되는 경우 해당 계정 유형 기반의 반가산적 동작을 자동으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-107">If the cube contains an account dimension, you can automatically set semiadditive behavior based on the account type.</span></span>  
  
 <span data-ttu-id="ce1e1-108">반가산적 동작을 추가하려면 큐브 디자이너에서 큐브를 열고 큐브 메뉴에서 **비즈니스 인텔리전스 추가** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-108">To add semiadditive behavior, open a cube in Cube Designer and choose **Add Business Intelligence** from the Cube menu.</span></span> <span data-ttu-id="ce1e1-109">비즈니스 인텔리전스 마법사의 **기능 선택** 페이지에서 **반가산적 동작 정의** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-109">In the Business Intelligence Wizard, select the **Define semiadditive behavior** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="ce1e1-110">그런 다음 마법사의 안내를 따라 반가산적 동작이 있는 측정값을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-110">This wizard then guides you through the steps of identifying which measures have semiadditive behavior.</span></span>  
  
 <span data-ttu-id="ce1e1-111">표준 버전에서 제공되는 LastChild를 제외하고, 반가산적 동작은 비즈니스 인텔리전스 또는 엔터프라이즈 버전에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-111">With the exception of LastChild which is available in the standard edition, semi-additive behaviors are only available in the business intelligence or enterprise editions.</span></span>  
  
## <a name="define-semiadditive-behavior"></a><span data-ttu-id="ce1e1-112">반가산적 동작 정의</span><span class="sxs-lookup"><span data-stu-id="ce1e1-112">Define Semiadditive Behavior</span></span>  
 <span data-ttu-id="ce1e1-113">마법사의 **반가산적 동작 정의** 페이지에서 다음 옵션 중 하나를 선택하여 반가산성을 정의하는 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-113">On the **Define Semiadditive Behavior** page of the wizard, you select how to define semiadditivity by selecting one of the following options:</span></span>  
  
 <span data-ttu-id="ce1e1-114">**반가산적 동작 해제**</span><span class="sxs-lookup"><span data-stu-id="ce1e1-114">**Turn off semiadditive behavior**</span></span>  
 <span data-ttu-id="ce1e1-115">이전에 반가산적 동작이 정의된 큐브에서 반가산적 동작을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-115">Removes semiadditive behavior from a cube in which semiadditive behavior was previously defined.</span></span> <span data-ttu-id="ce1e1-116">측정값이 다음 집계 함수 유형 중 하나로 설정된 경우 이 옵션을 선택하면 측정값이 `SUM`으로 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-116">This selection resets a measure to `SUM` if it is set to any of the following aggregation function types:</span></span>  
  
-   <span data-ttu-id="ce1e1-117">By Account</span><span class="sxs-lookup"><span data-stu-id="ce1e1-117">By Account</span></span>  
  
-   <span data-ttu-id="ce1e1-118">Average of Children</span><span class="sxs-lookup"><span data-stu-id="ce1e1-118">Average of Children</span></span>  
  
-   <span data-ttu-id="ce1e1-119">First Child</span><span class="sxs-lookup"><span data-stu-id="ce1e1-119">First Child</span></span>  
  
-   <span data-ttu-id="ce1e1-120">Last Child</span><span class="sxs-lookup"><span data-stu-id="ce1e1-120">Last Child</span></span>  
  
-   <span data-ttu-id="ce1e1-121">Last Nonempty Child</span><span class="sxs-lookup"><span data-stu-id="ce1e1-121">Last Nonempty Child</span></span>  
  
-   <span data-ttu-id="ce1e1-122">First Nonempty Child</span><span class="sxs-lookup"><span data-stu-id="ce1e1-122">First Nonempty Child</span></span>  
  
-   <span data-ttu-id="ce1e1-123">없음</span><span class="sxs-lookup"><span data-stu-id="ce1e1-123">None</span></span>  
  
 <span data-ttu-id="ce1e1-124">이 옵션은,,, `Sum` 또는 등의 일반 집계 함수로 측정값을 변경 하지 않습니다 `Min` `Max` `Count` `Distinct``Count` .</span><span class="sxs-lookup"><span data-stu-id="ce1e1-124">This option does not change measures with a regular aggregation function: `Sum`, `Min`, `Max`, `Count`, or `Distinct``Count`.</span></span>  
  
 <span data-ttu-id="ce1e1-125">**마법사에서 반 가산적 멤버가 포함 된 ' Account ' 계정 차원을 검색 했습니다. 서버는 각 계정 유형에 지정 된 반 가산적 동작에 따라이 차원의 멤버를 집계 합니다.**</span><span class="sxs-lookup"><span data-stu-id="ce1e1-125">**The wizard has detected the 'Account" account dimension, which contains semiadditive members. The server will aggregate members of this dimension according to the semiadditive behavior specified for each account type.**</span></span>  
 <span data-ttu-id="ce1e1-126">시스템에서 계정 유형 차원별로 차원이 구분된 측정값 그룹의 모든 측정값을 By Account 집계 함수로 설정하도록 하며 서버는 각 계정 유형에 지정된 반가산적 동작에 따라 차원의 멤버를 집계합니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-126">Causes the system to set all measures from a measure group dimensioned by an Account type dimension to the By Account aggregation function and the server will aggregate members of the dimension according to the semiadditive behavior specified for each account type.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ce1e1-127">마법사에서 계정 유형 차원을 찾은 경우 이 옵션이 기본적으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-127">This option is selected by default if the wizard detects an Account type dimension.</span></span>  
  
 <span data-ttu-id="ce1e1-128">**개별 측정값에 대한 반가산적 동작 정의**</span><span class="sxs-lookup"><span data-stu-id="ce1e1-128">**Define semiadditive behavior for individual measures**</span></span>  
 <span data-ttu-id="ce1e1-129">각 측정값의 반가산적 동작을 개별적으로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-129">Selects the semiadditive behavior of each measure individually.</span></span> <span data-ttu-id="ce1e1-130">기본 설정은 `SUM`(완전 가산적)입니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-130">The default setting is `SUM` (fully additive).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ce1e1-131">마법사에서 계정 유형 차원을 찾지 못한 경우 이 옵션이 기본적으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-131">This option is selected by default if the wizard does not detect an Account type dimension.</span></span>  
  
 <span data-ttu-id="ce1e1-132">각 측정값에 대해 다음 표에서 설명하는 유형의 반가산적 함수를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-132">For each measure, you can select from the types of semiadditive functionality described in the following table.</span></span>  
  
|<span data-ttu-id="ce1e1-133">반가산적 함수</span><span class="sxs-lookup"><span data-stu-id="ce1e1-133">Semiadditive function</span></span>|<span data-ttu-id="ce1e1-134">Description</span><span class="sxs-lookup"><span data-stu-id="ce1e1-134">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="ce1e1-135">Average of Children</span><span class="sxs-lookup"><span data-stu-id="ce1e1-135">Average of Children</span></span>|<span data-ttu-id="ce1e1-136">멤버 자식의 평균을 집계합니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-136">The aggregation of a member is the average of its children.</span></span>|  
|<span data-ttu-id="ce1e1-137">ByAccount</span><span class="sxs-lookup"><span data-stu-id="ce1e1-137">ByAccount</span></span>|<span data-ttu-id="ce1e1-138">시스템에서 계정 유형에 지정된 반가산적 동작을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-138">The system reads the semiadditive behavior specified for the account type.</span></span>|  
|<span data-ttu-id="ce1e1-139">개수</span><span class="sxs-lookup"><span data-stu-id="ce1e1-139">Count</span></span>|<span data-ttu-id="ce1e1-140">멤버 개수를 집계합니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-140">The aggregation is a count of members.</span></span>|  
|<span data-ttu-id="ce1e1-141">Distinct Count</span><span class="sxs-lookup"><span data-stu-id="ce1e1-141">Distinct Count</span></span>|<span data-ttu-id="ce1e1-142">고유 멤버의 개수를 집계합니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-142">The aggregation is a count of unique members.</span></span>|  
|<span data-ttu-id="ce1e1-143">First Child</span><span class="sxs-lookup"><span data-stu-id="ce1e1-143">First Child</span></span>|<span data-ttu-id="ce1e1-144">멤버 값이 시간 차원에 따른 첫 번째 자식의 값으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-144">The member value is evaluated as the value of its first child along the time dimension.</span></span>|  
|<span data-ttu-id="ce1e1-145">FirstNonEmpty</span><span class="sxs-lookup"><span data-stu-id="ce1e1-145">FirstNonEmpty</span></span>|<span data-ttu-id="ce1e1-146">멤버 값이 시간 차원에 따른 데이터를 포함하는 첫 번째 자식의 값으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-146">The member value is evaluated as the value of its first child along the time dimension that contains data.</span></span>|  
|<span data-ttu-id="ce1e1-147">LastChild</span><span class="sxs-lookup"><span data-stu-id="ce1e1-147">LastChild</span></span>|<span data-ttu-id="ce1e1-148">멤버 값이 시간 차원에 따른 마지막 자식의 값으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-148">The member value is evaluated as the value of its last child along the time dimension.</span></span>|  
|<span data-ttu-id="ce1e1-149">LastNonEmpty</span><span class="sxs-lookup"><span data-stu-id="ce1e1-149">LastNonEmpty</span></span>|<span data-ttu-id="ce1e1-150">멤버 값이 시간 차원에 따른 데이터를 포함하는 마지막 자식의 값으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-150">The member value is evaluated as the value of its last child along the time dimension that contains data.</span></span>|  
|<span data-ttu-id="ce1e1-151">최대</span><span class="sxs-lookup"><span data-stu-id="ce1e1-151">Max</span></span>|<span data-ttu-id="ce1e1-152">표준 최대 집계 함수가 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-152">The standard maximum aggregation function is applied.</span></span>|  
|<span data-ttu-id="ce1e1-153">최소</span><span class="sxs-lookup"><span data-stu-id="ce1e1-153">Min</span></span>|<span data-ttu-id="ce1e1-154">표준 최소 집계 함수가 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-154">The standard minimum aggregation function is applied.</span></span>|  
|<span data-ttu-id="ce1e1-155">없음</span><span class="sxs-lookup"><span data-stu-id="ce1e1-155">None</span></span>|<span data-ttu-id="ce1e1-156">집계가 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-156">No aggregation is applied.</span></span>|  
|<span data-ttu-id="ce1e1-157">Sum</span><span class="sxs-lookup"><span data-stu-id="ce1e1-157">Sum</span></span>|<span data-ttu-id="ce1e1-158">표준 합계 함수가 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-158">The standard summation function is applied.</span></span>|  
  
 <span data-ttu-id="ce1e1-159">마법사를 완료하면 기존의 모든 반가산적 동작을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="ce1e1-159">Any existing semiadditive behavior is overwritten when you complete the wizard.</span></span>  
  
  
