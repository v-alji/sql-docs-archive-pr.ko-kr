---
title: 검색 속성 목록 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.spl.searchpropertylisteditor.f1
ms.assetid: 0f3ced6e-0dfd-49fc-b175-82378c3d668e
author: rothja
ms.author: jroth
ms.openlocfilehash: 6c68ec986e2c6f4f53dfec7f188ba2a120532ae4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649666"
---
# <a name="search-property-list-editor"></a><span data-ttu-id="bca98-102">검색 속성 목록 편집기</span><span class="sxs-lookup"><span data-stu-id="bca98-102">Search Property List Editor</span></span>
  <span data-ttu-id="bca98-103">이 대화 상자를 사용하여 검색 속성 목록에서 검색 속성을 추가하거나 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bca98-103">Use this dialog box to add or delete search properties in a search property list.</span></span>  
  
## <a name="to-use-sql-server-management-studio-to-manage-search-property-lists"></a><span data-ttu-id="bca98-104">SQL Server Management Studio를 사용하여 검색 속성 목록을 관리하려면</span><span class="sxs-lookup"><span data-stu-id="bca98-104">To Use SQL Server Management Studio to Manage Search Property Lists</span></span>  
 <span data-ttu-id="bca98-105">검색 속성 목록을 만들거나, 보거나, 삭제 하는 방법과 속성 검색을 위해 전체 텍스트 인덱스를 구성 하는 방법에 대 한 자세한 내용은 [검색 속성 목록을 사용 하 여 문서 속성 검색](../relational-databases/search/search-document-properties-with-search-property-lists.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bca98-105">For information about how to create, view, or delete a search property list, and about how to configure a full-text index for property searching, see [Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="bca98-106">옵션</span><span class="sxs-lookup"><span data-stu-id="bca98-106">Options</span></span>  
 <span data-ttu-id="bca98-107">**속성 이름**</span><span class="sxs-lookup"><span data-stu-id="bca98-107">**Property Name**</span></span>  
 <span data-ttu-id="bca98-108">전체 텍스트 쿼리에서 속성을 식별하는 데 사용할 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bca98-108">Specify the name to be used to identify the property in full-text queries.</span></span> <span data-ttu-id="bca98-109">속성 이름은 내부에 공백을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bca98-109">A property name can contain internal spaces.</span></span> <span data-ttu-id="bca98-110">**속성 이름** 의 최대 길이는 255자입니다.</span><span class="sxs-lookup"><span data-stu-id="bca98-110">The maximum length of **Property Name** is 256 characters.</span></span> <span data-ttu-id="bca98-111">"작성자"나 "집 주소"와 같은 친숙한 단어 또는 `System.Author`나 `System.Contact.HomeAddress`와 같은 Windows 정식 속성 이름을 이 이름에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bca98-111">This name can be a user-friendly name, such as "Author" or "Home Address", or it can be the Windows canonical name of the property, such as `System.Author` or `System.Contact.HomeAddress`.</span></span> <span data-ttu-id="bca98-112">**속성 이름** 은 속성 집합 내에서 해당 속성을 고유하게 식별해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bca98-112">**Property Name** must uniquely identify the property within the property set.</span></span>  
  
 <span data-ttu-id="bca98-113">개발자는 속성 이름을 사용하여 [CONTAINS](/sql/t-sql/queries/contains-transact-sql) 조건자에 있는 속성을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="bca98-113">Developers use the property name to identify the property in the [CONTAINS](/sql/t-sql/queries/contains-transact-sql) predicate.</span></span> <span data-ttu-id="bca98-114">따라서 속성을 추가할 때는 속성을 의미 있게 나타내는 값을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bca98-114">Therefore, when adding a property it is important to specify a value that meaningfully represents the property.</span></span>  
  
 <span data-ttu-id="bca98-115">**속성 집합 GUID**</span><span class="sxs-lookup"><span data-stu-id="bca98-115">**Property Set GUID**</span></span>  
 <span data-ttu-id="bca98-116">속성이 속한 속성 집합의 식별자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bca98-116">Specify the identifier of the property set to which the property belongs.</span></span> <span data-ttu-id="bca98-117">이 식별자는 GUID(Globally Unique Identifier)입니다.</span><span class="sxs-lookup"><span data-stu-id="bca98-117">This is a globally unique identifier (GUID).</span></span> <span data-ttu-id="bca98-118">속성 집합은 논리적으로 관련이 있는 속성의 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="bca98-118">A property set is a group of logically related properties.</span></span> <span data-ttu-id="bca98-119">이 값을 가져오는 방법은 이 항목의 뒷부분에 나오는 "주의"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bca98-119">For information about obtaining this value, see "Remarks," later in this topic.</span></span>  
  
 <span data-ttu-id="bca98-120">**속성 정수 ID**</span><span class="sxs-lookup"><span data-stu-id="bca98-120">**Property Int ID**</span></span>  
 <span data-ttu-id="bca98-121">속성의 속성 정수 식별자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bca98-121">Specify the property integer identifier of the property.</span></span> <span data-ttu-id="bca98-122">미리 할당되는 이 값은 속성 집합 내에서 고유한 양의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="bca98-122">This pre-assigned value is a positive integer that is unique within the property set.</span></span> <span data-ttu-id="bca98-123">이 값을 가져오는 방법은 이 항목의 뒷부분에 나오는 "주의"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bca98-123">For information about obtaining this value, see "Remarks," later in this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bca98-124">문자열 식별자를 사용하는 문서 속성은 전체 텍스트 검색에 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bca98-124">Document properties that use string identifiers are not supported by full-text search.</span></span>  
  
 <span data-ttu-id="bca98-125">**속성 설명**</span><span class="sxs-lookup"><span data-stu-id="bca98-125">**Property Description**</span></span>  
 <span data-ttu-id="bca98-126">필요에 따라 속성에 대한 설명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bca98-126">Optionally, specify a description of the property.</span></span> <span data-ttu-id="bca98-127">속성 설명은 최대 512자의 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="bca98-127">This is a string of up to 512 characters.</span></span> <span data-ttu-id="bca98-128">예를 들어 이름만으로는 명확하지 않은 속성에 대한 정보나 속성의 속성 집합에 대한 정보를 설명에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bca98-128">For example, a description could contain information about the property set of the property or information about a property that is not evident from its name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bca98-129">설명</span><span class="sxs-lookup"><span data-stu-id="bca98-129">Remarks</span></span>  
 <span data-ttu-id="bca98-130">검색 속성 목록에 검색 속성을 추가하려면 속성이 속한 속성 집합의 GUID(Globally Unique Identifier) 및 속성의 속성 정수 식별자를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bca98-130">To add a search property to a search property list, you must specify the globally unique identifier (GUID) of the property set to which the property belongs and the property integer identifier of the property.</span></span> <span data-ttu-id="bca98-131">이러한 값의 조합은 한 검색 속성 목록 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bca98-131">A given combination of these must be unique in a given search property list.</span></span> <span data-ttu-id="bca98-132">기존의 조합을 추가하려고 하면 작업이 실패하고 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="bca98-132">If you try to add an existing combination, the operation fails and issues an error.</span></span> <span data-ttu-id="bca98-133">즉, 지정된 속성에 대해 이름을 한 개만 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bca98-133">This means that you can configure only one name for a given property.</span></span>  
  
 <span data-ttu-id="bca98-134">속성 설명은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="bca98-134">The property description is optional.</span></span>  
  
 <span data-ttu-id="bca98-135">**전체 텍스트 인덱스용 검색 속성 목록을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="bca98-135">**To configure a search property list for a full-text index**</span></span>  
  
-   [<span data-ttu-id="bca98-136">검색 속성 목록을 사용하여 문서 속성 검색</span><span class="sxs-lookup"><span data-stu-id="bca98-136">Search Document Properties with Search Property Lists</span></span>](../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
## <a name="permissions"></a><span data-ttu-id="bca98-137">사용 권한</span><span class="sxs-lookup"><span data-stu-id="bca98-137">Permissions</span></span>  
 <span data-ttu-id="bca98-138">[ALTER SEARCH PROPERTY LIST &#40;transact-sql&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bca98-138">See [ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca98-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bca98-139">See Also</span></span>  
 <span data-ttu-id="bca98-140">[ALTER SEARCH PROPERTY LIST &#40;Transact-sql&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bca98-140">[ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql) </span></span>  
 <span data-ttu-id="bca98-141">[검색 속성 목록을 사용 하 여 문서 속성 검색](../relational-databases/search/search-document-properties-with-search-property-lists.md) </span><span class="sxs-lookup"><span data-stu-id="bca98-141">[Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md) </span></span>  
 [<span data-ttu-id="bca98-142">sys.registered_search_property_lists&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bca98-142">sys.registered_search_property_lists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql)  
  
  
