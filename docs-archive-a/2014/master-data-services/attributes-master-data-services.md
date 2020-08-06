---
title: 특성(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- free-form attributes [Master Data Services]
- attributes [Master Data Services], about attributes
- attributes [Master Data Services], file attributes
- file attributes [Master Data Services]
- attributes [Master Data Services], free-form attributes
- attributes [Master Data Services]
ms.assetid: 95ecb75f-c559-41c3-933c-40ae60a4c2fd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 5a6fb01b47658f39e14c599ae88aa7ad3d29c69a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659516"
---
# <a name="attributes-master-data-services"></a><span data-ttu-id="1ecbb-102">특성(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1ecbb-102">Attributes (Master Data Services)</span></span>
  <span data-ttu-id="1ecbb-103">특성은 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 엔터티에 포함된 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-103">Attributes are objects that are contained in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] entities.</span></span> <span data-ttu-id="1ecbb-104">특성 값은 엔터티 멤버를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-104">Attribute values describe the members of the entity.</span></span> <span data-ttu-id="1ecbb-105">특성을 사용하여 리프 멤버, 통합 멤버 또는 컬렉션을 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-105">An attribute can be used to describe a leaf member, a consolidated member, or a collection.</span></span>  
  
## <a name="how-attributes-relate-to-other-model-objects"></a><span data-ttu-id="1ecbb-106">다른 모델 개체와 특성의 관계</span><span class="sxs-lookup"><span data-stu-id="1ecbb-106">How Attributes Relate to Other Model Objects</span></span>  
 <span data-ttu-id="1ecbb-107">특성은 엔터티 테이블의 열로 생각할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-107">You can think of an attribute as a column in an entity table.</span></span> <span data-ttu-id="1ecbb-108">특성 값은 특정 멤버를 설명하는 데 사용되는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-108">An attribute value is the value used to describe a specific member.</span></span>  
  
 <span data-ttu-id="1ecbb-109">![테이블로 표시된 MDS(Master Data Services) 엔터티](../../2014/master-data-services/media/mds-conc-entity-table.gif "테이블로 표시된 MDS(Master Data Services) 엔터티")</span><span class="sxs-lookup"><span data-stu-id="1ecbb-109">![Master Data Services Entity Represented as Table](../../2014/master-data-services/media/mds-conc-entity-table.gif "Master Data Services Entity Represented as Table")</span></span>  
  
 <span data-ttu-id="1ecbb-110">다수의 특성이 포함된 엔터티를 만들 때는 특성을 특성 그룹으로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-110">When you create an entity that contains many attributes, you can organize the attributes into attribute groups.</span></span> <span data-ttu-id="1ecbb-111">자세한 내용은 [특성 그룹&#40;Master Data Services&#41;](attribute-groups-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-111">For more information, see [Attribute Groups &#40;Master Data Services&#41;](attribute-groups-master-data-services.md).</span></span>  
  
## <a name="required-attributes"></a><span data-ttu-id="1ecbb-112">필수 특성</span><span class="sxs-lookup"><span data-stu-id="1ecbb-112">Required Attributes</span></span>  
 <span data-ttu-id="1ecbb-113">엔터티를 만들면 Name 및 Code 특성이 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-113">When you create an entity, the Name and Code attributes are automatically created.</span></span> <span data-ttu-id="1ecbb-114">Code는 값이 있어야 하고 엔터티 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-114">Code requires a value and must be unique within the entity.</span></span> <span data-ttu-id="1ecbb-115">Name 및 Code 특성은 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-115">You cannot remove the Name and Code attributes.</span></span>  
  
## <a name="attribute-types"></a><span data-ttu-id="1ecbb-116">특성 유형</span><span class="sxs-lookup"><span data-stu-id="1ecbb-116">Attribute Types</span></span>  
 <span data-ttu-id="1ecbb-117">특성에는 다음 세 가지 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-117">There are three types of attributes:</span></span>  
  
-   <span data-ttu-id="1ecbb-118">자유 형식 특성 - 텍스트, 숫자, 날짜 또는 링크에 대한 자유 형식 입력이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-118">Free-form attributes, which allow free-form input for text, numbers, dates, or links.</span></span>  
  
-   <span data-ttu-id="1ecbb-119">도메인 기반 특성 - 엔터티로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-119">Domain-based attributes, which are populated by entities.</span></span> <span data-ttu-id="1ecbb-120">자세한 내용은 [도메인 기반 특성&#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-120">For more information, see [Domain-Based Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="1ecbb-121">파일 특성 - 파일, 문서 또는 이미지를 저장하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-121">File attributes, which are used to store files, documents, or images.</span></span> <span data-ttu-id="1ecbb-122">파일 특성은 파일에 특정 확장명을 사용하도록 요구하여 데이터 일관성에 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-122">File attributes are intended to help with the consistency of your data by requiring files to have a specific extension.</span></span> <span data-ttu-id="1ecbb-123">파일 특성을 사용해도 악의적인 사용자가 다른 형식의 파일을 업로드하는 것이 방지되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-123">File attributes cannot be guaranteed to prevent a malicious user from uploading a file of a different type.</span></span>  
  
### <a name="numeric-free-form-attributes"></a><span data-ttu-id="1ecbb-124">숫자 자유 형식 특성</span><span class="sxs-lookup"><span data-stu-id="1ecbb-124">Numeric Free-Form Attributes</span></span>  
 <span data-ttu-id="1ecbb-125">숫자 자유 형식 특성 값은 **SqlDouble** 값 형식으로 제한되기 때문에 숫자 자유 형식 특성은 특별히 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-125">Numeric free-form attributes require special handling, because numeric free-form attribute values are limited to the **SqlDouble** value type.</span></span>  
  
 <span data-ttu-id="1ecbb-126">내부적으로 최대 17자리가 유지되지만 **SqlDouble** 값의 전체 자릿수는 기본적으로 15자리입니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-126">By default, a **SqlDouble** value contains 15 decimal digits of precision, although a maximum of 17 digits is maintained internally.</span></span> <span data-ttu-id="1ecbb-127">부동 소수점 숫자의 전체 자릿수는 여러 결과를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-127">The precision of a floating-point number has several consequences:</span></span>  
  
-   <span data-ttu-id="1ecbb-128">특정 전체 자릿수에서 동일하게 나타나는 두 개의 부동 소수점 숫자는 최소 유효 자릿수가 다르므로 동일하게 비교되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-128">Two floating-point numbers that appear equal for a particular precision might not compare equal because their least significant digits are different.</span></span>  
  
-   <span data-ttu-id="1ecbb-129">부동 소수점 숫자가 10진수를 정확하게 추정하지 않을 수 있으므로 10진수가 사용될 경우 부동 소수점 숫자를 사용하는 수치 또는 비교 연산은 결과가 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-129">A mathematical or comparison operation that uses a floating-point number might not yield the same result if a decimal number is used because the floating-point number might not exactly approximate the decimal number.</span></span>  
  
-   <span data-ttu-id="1ecbb-130">부동 소수점 숫자가 포함된 경우 값은 *왕복* 이 아닐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-130">A value might not *roundtrip* if a floating-point number is involved.</span></span> <span data-ttu-id="1ecbb-131">작업이 원래 부동 소수점 숫자를 다른 형식으로 변환하고 역 작업이 변환된 형식을 부동 소수점 숫자로 다시 변환한 다음 최종 부동 소수점 숫자가 원래 부동 소수점 숫자와 같을 경우 값을 왕복이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-131">A value is said to roundtrip if an operation converts an original floating-point number to another form, an inverse operation transforms the converted form back to a floating-point number, and the final floating-point number is equal to the original floating-point number.</span></span> <span data-ttu-id="1ecbb-132">하나 이상의 최소 유효 자릿수가 변환 중에 손실되거나 변경되어 왕복이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-132">The roundtrip might fail because one or more least significant digits are lost or changed in a conversion.</span></span>  
  
## <a name="attribute-examples"></a><span data-ttu-id="1ecbb-133">특성 예</span><span class="sxs-lookup"><span data-stu-id="1ecbb-133">Attribute Examples</span></span>  
 <span data-ttu-id="1ecbb-134">다음 예의 엔터티에는 멤버를 설명하는 Name, Code, Subcategory, StandardCost, ListPrice 및 FilePhoto 특성이</span><span class="sxs-lookup"><span data-stu-id="1ecbb-134">In the following example, the entity has the attributes: Name, Code, Subcategory, StandardCost, ListPrice, and FilePhoto.</span></span> <span data-ttu-id="1ecbb-135">있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-135">These attributes describe the members.</span></span> <span data-ttu-id="1ecbb-136">각 멤버는 단일 특성 값 행으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-136">Each member is represented by a single row of attribute values.</span></span>  
  
 <span data-ttu-id="1ecbb-137">![Bike 제품 엔터티 테이블](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "Bike 제품 엔터티 테이블")</span><span class="sxs-lookup"><span data-stu-id="1ecbb-137">![Bike Product Entity Table](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "Bike Product Entity Table")</span></span>  
  
 <span data-ttu-id="1ecbb-138">다음 예에서 Product 엔터티는 다음을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-138">In the following example, the Product entity contains:</span></span>  
  
-   <span data-ttu-id="1ecbb-139">Name, Code, StandardCost 및 ListPrice의 자유 형식 특성</span><span class="sxs-lookup"><span data-stu-id="1ecbb-139">The free-form attributes of Name, Code, StandardCost and ListPrice.</span></span>  
  
-   <span data-ttu-id="1ecbb-140">Subcategory의 도메인 기반 특성</span><span class="sxs-lookup"><span data-stu-id="1ecbb-140">The domain-based attribute of Subcategory.</span></span>  
  
-   <span data-ttu-id="1ecbb-141">FilePhoto의 파일 특성</span><span class="sxs-lookup"><span data-stu-id="1ecbb-141">The file attribute of FilePhoto.</span></span>  
  
 <span data-ttu-id="1ecbb-142">Subcategory는 Product의 도메인 기반 특성으로 사용되는 엔터티입니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-142">Subcategory is an entity that is used as a domain-based attribute of Product.</span></span> <span data-ttu-id="1ecbb-143">Category는 Subcategory의 도메인 기반 특성으로 사용되는 엔터티입니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-143">Category is an entity that is used as a domain-based attribute of Subcategory.</span></span> <span data-ttu-id="1ecbb-144">Product 엔터티와 마찬가지로 Category 및 Subcategory 엔터티는 각각 기본 Name 및 Code 특성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-144">Like the Product entity, the Category and Subcategory entities each contain the default Name and Code attributes.</span></span>  
  
 <span data-ttu-id="1ecbb-145">![제품 엔터티 트리 구조](../../2014/master-data-services/media/mds-conc-entity-ui.gif "제품 엔터티 트리 구조")</span><span class="sxs-lookup"><span data-stu-id="1ecbb-145">![Product Entity Tree Structure](../../2014/master-data-services/media/mds-conc-entity-ui.gif "Product Entity Tree Structure")</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="1ecbb-146">관련 작업</span><span class="sxs-lookup"><span data-stu-id="1ecbb-146">Related Tasks</span></span>  
  
|<span data-ttu-id="1ecbb-147">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="1ecbb-147">Task Description</span></span>|<span data-ttu-id="1ecbb-148">항목</span><span class="sxs-lookup"><span data-stu-id="1ecbb-148">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="1ecbb-149">새 자유 형식 텍스트 특성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-149">Create a new free-form text attribute.</span></span>|[<span data-ttu-id="1ecbb-150">텍스트 특성 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1ecbb-150">Create a Text Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)|  
|<span data-ttu-id="1ecbb-151">새 자유 형식 숫자 특성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-151">Create a new free-form numeric attribute.</span></span>|[<span data-ttu-id="1ecbb-152">숫자 특성 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1ecbb-152">Create a Numeric Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-numeric-attribute-master-data-services.md)|  
|<span data-ttu-id="1ecbb-153">새 자유 형식 링크 특성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-153">Create a new free-form link attribute.</span></span>|[<span data-ttu-id="1ecbb-154">링크 특성 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1ecbb-154">Create a Link Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-link-attribute-master-data-services.md)|  
|<span data-ttu-id="1ecbb-155">새 파일 특성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-155">Create a new file attribute.</span></span>|[<span data-ttu-id="1ecbb-156">파일 특성 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1ecbb-156">Create a File Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)|  
|<span data-ttu-id="1ecbb-157">새 도메인 기반 특성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-157">Create a new domain-based attribute.</span></span>|[<span data-ttu-id="1ecbb-158">도메인 기반 특성 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1ecbb-158">Create a Domain-Based Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)|  
|<span data-ttu-id="1ecbb-159">기존 특성의 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-159">Change the name of an existing attribute.</span></span>|[<span data-ttu-id="1ecbb-160">특성 이름을 MDS(Master Data Services) &#40;변경&#41;</span><span class="sxs-lookup"><span data-stu-id="1ecbb-160">Change an Attribute Name &#40;Master Data Services&#41;</span></span>](change-an-attribute-name-and-data-type-master-data-services.md)|  
|<span data-ttu-id="1ecbb-161">추적 그룹을 변경하는 기존 특성을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-161">Add existing attributes to a change tracking group.</span></span>|[<span data-ttu-id="1ecbb-162">변경 내용 추적 그룹에 특성 추가&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1ecbb-162">Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|<span data-ttu-id="1ecbb-163">기존 특성을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-163">Delete an existing attribute.</span></span>|[<span data-ttu-id="1ecbb-164">특성 삭제&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1ecbb-164">Delete an Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-attribute-master-data-services.md)|  
|<span data-ttu-id="1ecbb-165">특성 순서를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1ecbb-165">Change the order of attributes.</span></span>|[<span data-ttu-id="1ecbb-166">특성 순서 변경</span><span class="sxs-lookup"><span data-stu-id="1ecbb-166">Change the Order of Attributes</span></span>](../../2014/master-data-services/change-the-order-of-attributes.md)|  
  
## <a name="related-content"></a><span data-ttu-id="1ecbb-167">관련 내용</span><span class="sxs-lookup"><span data-stu-id="1ecbb-167">Related Content</span></span>  
  
-   [<span data-ttu-id="1ecbb-168">도메인 기반 특성&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1ecbb-168">Domain-Based Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/domain-based-attributes-master-data-services.md)  
  
-   [<span data-ttu-id="1ecbb-169">특성 그룹&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1ecbb-169">Attribute Groups &#40;Master Data Services&#41;</span></span>](attribute-groups-master-data-services.md)  
  
-   [<span data-ttu-id="1ecbb-170">멤버&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1ecbb-170">Members &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/members-master-data-services.md)  
  
-   [<span data-ttu-id="1ecbb-171">리프 권한&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1ecbb-171">Leaf Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/leaf-permissions-master-data-services.md)  
  
-   [<span data-ttu-id="1ecbb-172">MDS(Master Data Services)&#41;&#40;통합 된 사용 권한</span><span class="sxs-lookup"><span data-stu-id="1ecbb-172">Consolidated Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/consolidated-permissions-master-data-services.md)  
  
  
