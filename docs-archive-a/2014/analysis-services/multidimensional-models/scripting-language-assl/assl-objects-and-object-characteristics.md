---
title: 개체 및 개체 특징 Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- reference exceptions [Analysis Services Scripting Language]
- ASSL, objects
- inheritance [Analysis Services Scripting Language]
- localized names [Analysis Services Scripting Language]
- objects [Analysis Services Scripting Language]
- names [Analysis Services Scripting Language]
- Analysis Services Scripting Language, objects
- expansion [Analysis Services Scripting Language]
ms.assetid: 6e5c28b5-c0bc-4ccd-82e5-e174bbb71386
author: minewiskan
ms.author: owend
ms.openlocfilehash: 76d57bb421a7f486983476a6549a5121ce88ee9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653020"
---
# <a name="assl-objects-and-object-characteristics"></a><span data-ttu-id="33063-102">ASSL 개체 및 개체 특징</span><span class="sxs-lookup"><span data-stu-id="33063-102">ASSL Objects and Object Characteristics</span></span>
  <span data-ttu-id="33063-103">ASSL(Analysis Services Scripting Language)의 개체는 개체 그룹, 상속, 명명, 확장 및 처리에 관한 특정 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="33063-103">Objects in Analysis Services Scripting Language (ASSL) follow specific guidelines in regards to object groups, inheritance, naming, expansion, and processing.</span></span>  
  
## <a name="object-groups"></a><span data-ttu-id="33063-104">개체 그룹</span><span class="sxs-lookup"><span data-stu-id="33063-104">Object Groups</span></span>  
 <span data-ttu-id="33063-105">모든 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 개체에는 XML 표현이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33063-105">All [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] objects have an XML representation.</span></span> <span data-ttu-id="33063-106">개체는 다음과 같은 두 그룹으로 나뉩니다.</span><span class="sxs-lookup"><span data-stu-id="33063-106">The objects are divided into two groups:</span></span>  
  
 <span data-ttu-id="33063-107">**주요 개체**</span><span class="sxs-lookup"><span data-stu-id="33063-107">**Major objects**</span></span>  
 <span data-ttu-id="33063-108">주요 개체는 독립적으로 만들고 변경하고 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33063-108">Major objects can be independently created, altered, and deleted.</span></span> <span data-ttu-id="33063-109">주요 개체는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="33063-109">Major objects include:</span></span>  
  
-   <span data-ttu-id="33063-110">서버</span><span class="sxs-lookup"><span data-stu-id="33063-110">Servers</span></span>  
  
-   <span data-ttu-id="33063-111">데이터베이스</span><span class="sxs-lookup"><span data-stu-id="33063-111">Databases</span></span>  
  
-   <span data-ttu-id="33063-112">차원</span><span class="sxs-lookup"><span data-stu-id="33063-112">Dimensions</span></span>  
  
-   <span data-ttu-id="33063-113">큐브</span><span class="sxs-lookup"><span data-stu-id="33063-113">Cubes</span></span>  
  
-   <span data-ttu-id="33063-114">측정값 그룹</span><span class="sxs-lookup"><span data-stu-id="33063-114">Measure groups</span></span>  
  
-   <span data-ttu-id="33063-115">파티션</span><span class="sxs-lookup"><span data-stu-id="33063-115">Partitions</span></span>  
  
-   <span data-ttu-id="33063-116">큐브 뷰</span><span class="sxs-lookup"><span data-stu-id="33063-116">Perspectives</span></span>  
  
-   <span data-ttu-id="33063-117">마이닝 모델</span><span class="sxs-lookup"><span data-stu-id="33063-117">Mining models</span></span>  
  
-   <span data-ttu-id="33063-118">역할</span><span class="sxs-lookup"><span data-stu-id="33063-118">Roles</span></span>  
  
-   <span data-ttu-id="33063-119">서버 또는 데이터베이스에 연결된 명령</span><span class="sxs-lookup"><span data-stu-id="33063-119">Commands associated with a server or database</span></span>  
  
-   <span data-ttu-id="33063-120">데이터 원본</span><span class="sxs-lookup"><span data-stu-id="33063-120">Data sources</span></span>  
  
 <span data-ttu-id="33063-121">주요 개체에는 기록 및 상태를 추적할 수 있는 다음과 같은 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33063-121">Major objects have the following properties to track their history and status.</span></span>  
  
-   `CreatedTimestamp`  
  
-   `LastSchemaUpdate`  
  
-   <span data-ttu-id="33063-122">`LastProcessed`(필요한 경우)</span><span class="sxs-lookup"><span data-stu-id="33063-122">`LastProcessed` (where appropriate)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="33063-123">개체를 주요 개체로 분류하는 작업은 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 인스턴스와 개체 정의 언어에서 해당 개체가 처리되는 방법에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="33063-123">The classification of an object as a major object affects how an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] treats that object and how that object is handled in the object definition language.</span></span> <span data-ttu-id="33063-124">그러나 이 분류가 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 관리 및 개발 도구에서 이러한 개체를 독립적으로 만들거나 수정하거나 삭제할 수 있다는 것을 보장하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="33063-124">However, this classification does not guarantee that [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] management and development tools will allow the independent creation, modification, or deletion of these objects.</span></span>  
  
 <span data-ttu-id="33063-125">**보조 개체**</span><span class="sxs-lookup"><span data-stu-id="33063-125">**Minor objects**</span></span>  
 <span data-ttu-id="33063-126">보조 개체는 주요 부모 개체를 만들거나 변경하거나 삭제하는 작업의 일부로서만 만들거나 변경하거나 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33063-126">Minor objects can only be created, altered, or deleted as part of creating, altering, or deleting the parent major object.</span></span> <span data-ttu-id="33063-127">보조 개체는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="33063-127">Minor objects include:</span></span>  
  
-   <span data-ttu-id="33063-128">계층 및 수준</span><span class="sxs-lookup"><span data-stu-id="33063-128">Hierarchies and levels</span></span>  
  
-   <span data-ttu-id="33063-129">특성</span><span class="sxs-lookup"><span data-stu-id="33063-129">Attributes</span></span>  
  
-   <span data-ttu-id="33063-130">측정값</span><span class="sxs-lookup"><span data-stu-id="33063-130">Measures</span></span>  
  
-   <span data-ttu-id="33063-131">마이닝 모델 열</span><span class="sxs-lookup"><span data-stu-id="33063-131">Mining model columns</span></span>  
  
-   <span data-ttu-id="33063-132">큐브에 연결된 명령</span><span class="sxs-lookup"><span data-stu-id="33063-132">Commands associated with a cube</span></span>  
  
-   <span data-ttu-id="33063-133">집계</span><span class="sxs-lookup"><span data-stu-id="33063-133">Aggregations</span></span>  
  
## <a name="object-expansion"></a><span data-ttu-id="33063-134">개체 확장</span><span class="sxs-lookup"><span data-stu-id="33063-134">Object Expansion</span></span>  
 <span data-ttu-id="33063-135">`ObjectExpansion` 제한은 서버에서 반환된 ASSL XML의 확장 수준을 제어하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33063-135">The `ObjectExpansion` restriction can be used to control the degree of expansion of ASSL XML returned by the server.</span></span> <span data-ttu-id="33063-136">이 제한에는 다음 표에 나열된 옵션이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="33063-136">This restriction has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="33063-137">열거형 값</span><span class="sxs-lookup"><span data-stu-id="33063-137">Enumeration value</span></span>|<span data-ttu-id="33063-138">허용 된\<Alter></span><span class="sxs-lookup"><span data-stu-id="33063-138">Allowed for \<Alter></span></span>|<span data-ttu-id="33063-139">Description</span><span class="sxs-lookup"><span data-stu-id="33063-139">Description</span></span>|  
|-----------------------|---------------------------|-----------------|  
|<span data-ttu-id="33063-140">*ReferenceOnly*</span><span class="sxs-lookup"><span data-stu-id="33063-140">*ReferenceOnly*</span></span>|<span data-ttu-id="33063-141">no</span><span class="sxs-lookup"><span data-stu-id="33063-141">no</span></span>|<span data-ttu-id="33063-142">요청된 개체와 포함된 모든 주요 개체에 대한 이름, ID 및 타임스탬프만을 재귀적으로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="33063-142">Returns only the name, ID, and timestamp for the requested object and for all contained major objects recursively.</span></span>|  
|<span data-ttu-id="33063-143">*ObjectProperties*</span><span class="sxs-lookup"><span data-stu-id="33063-143">*ObjectProperties*</span></span>|<span data-ttu-id="33063-144">예</span><span class="sxs-lookup"><span data-stu-id="33063-144">yes</span></span>|<span data-ttu-id="33063-145">요청된 개체와 포함된 보조 개체를 확장합니다. 그러나 포함된 주요 개체를 반환하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="33063-145">Expands the requested object and minor contained objects, but does not return major contained objects.</span></span>|  
|<span data-ttu-id="33063-146">*ExpandObject*</span><span class="sxs-lookup"><span data-stu-id="33063-146">*ExpandObject*</span></span>|<span data-ttu-id="33063-147">no</span><span class="sxs-lookup"><span data-stu-id="33063-147">no</span></span>|<span data-ttu-id="33063-148">*ObjectProperties*와 같지만 포함된 주요 개체에 대한 이름, ID 및 타임스탬프도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="33063-148">Same as *ObjectProperties*, but also returns the name, ID, and timestamp for contained major objects.</span></span>|  
|<span data-ttu-id="33063-149">*ExpandFull*</span><span class="sxs-lookup"><span data-stu-id="33063-149">*ExpandFull*</span></span>|<span data-ttu-id="33063-150">예</span><span class="sxs-lookup"><span data-stu-id="33063-150">yes</span></span>|<span data-ttu-id="33063-151">요청된 개체와 포함된 모든 개체를 재귀적으로 완전히 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="33063-151">Fully expands the requested object and all contained objects recursively.</span></span>|  
  
 <span data-ttu-id="33063-152">이 ASSL 참조 섹션에서는 *ExpandFull* 표현에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="33063-152">This ASSL reference section describes the *ExpandFull* representation.</span></span> <span data-ttu-id="33063-153">다른 모든 `ObjectExpansion` 수준은 이 수준에서 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="33063-153">All other `ObjectExpansion` levels are derived from this level.</span></span>  
  
## <a name="object-processing"></a><span data-ttu-id="33063-154">개체 처리</span><span class="sxs-lookup"><span data-stu-id="33063-154">Object Processing</span></span>  
 <span data-ttu-id="33063-155">ASSL에는 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 인스턴스에서 읽을 수 있지만 명령 스크립트가 인스턴스에 제출될 때는 생략되는 읽기 전용 요소 또는 속성이 있습니다(예: `LastProcessed`).</span><span class="sxs-lookup"><span data-stu-id="33063-155">ASSL includes read-only elements or properties (for example, `LastProcessed`) that can be read from the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance, but which are omitted when command scripts are submitted to the instance.</span></span> [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]<span data-ttu-id="33063-156">에서는 경고나 오류 없이 읽기 전용 요소의 수정된 값을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="33063-156">ignores modified values for read-only elements without warning or error.</span></span>  
  
 <span data-ttu-id="33063-157">또한 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]에서는 유효성 검사 오류를 발생시키지 않고 적절하지 않거나 관련이 없는 속성을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="33063-157">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] also ignores inappropriate or irrelevant properties without raising validation errors.</span></span> <span data-ttu-id="33063-158">예를 들어, Y 요소의 값이 특정 값인 경우에만 X 요소가 존재해야 하는 경우</span><span class="sxs-lookup"><span data-stu-id="33063-158">For example, the X element should only be present when the Y element has a particular value.</span></span> <span data-ttu-id="33063-159">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 인스턴스는 Y 요소의 값에 대해 X 요소의 유효성을 검사하는 대신 X 요소를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="33063-159">The [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance ignores the X element instead of validating that element against the value of the Y element.</span></span>  
  
  
