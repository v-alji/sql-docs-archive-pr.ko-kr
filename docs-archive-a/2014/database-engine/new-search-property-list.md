---
title: 새 검색 속성 목록 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.spl.newsearchpropertylist.f1
ms.assetid: ffca78e9-8608-4b15-bd38-b2d78da4247a
author: rothja
ms.author: jroth
ms.openlocfilehash: 48c9e475b380d5f0c7310e33717f261c38acbbd4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660120"
---
# <a name="new-search-property-list"></a><span data-ttu-id="73980-102">새 검색 속성 목록</span><span class="sxs-lookup"><span data-stu-id="73980-102">New Search Property List</span></span>
  <span data-ttu-id="73980-103">이 대화 상자를 사용하여 검색 속성 목록을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73980-103">Use this dialog box to create a search property list.</span></span>  
  
## <a name="options"></a><span data-ttu-id="73980-104">옵션</span><span class="sxs-lookup"><span data-stu-id="73980-104">Options</span></span>  
 <span data-ttu-id="73980-105">**검색 속성 목록 이름**</span><span class="sxs-lookup"><span data-stu-id="73980-105">**Search property list name**</span></span>  
 <span data-ttu-id="73980-106">검색 속성 목록의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="73980-106">Enter the name of the search property list.</span></span>  
  
 <span data-ttu-id="73980-107">**소유자**</span><span class="sxs-lookup"><span data-stu-id="73980-107">**Owner**</span></span>  
 <span data-ttu-id="73980-108">검색 속성 목록의 소유자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="73980-108">Specify the owner of the search property list.</span></span> <span data-ttu-id="73980-109">자기 자신, 즉 현재 사용자에게 소유권을 할당하려면 필드를 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="73980-109">If you want ownership to be assigned to yourself, that is, to the current user, leave this field empty.</span></span> <span data-ttu-id="73980-110">다른 사용자를 지정하려면 찾아보기 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="73980-110">To specify a different user, click the browse button.</span></span>  
  
### <a name="create-search-property-list-options"></a><span data-ttu-id="73980-111">검색 속성 목록 만들기 옵션</span><span class="sxs-lookup"><span data-stu-id="73980-111">Create Search Property List Options</span></span>  
 <span data-ttu-id="73980-112">다음 옵션 중 하나를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="73980-112">Click one of the following options:</span></span>  
  
 <span data-ttu-id="73980-113">**빈 검색 속성 목록 만들기**</span><span class="sxs-lookup"><span data-stu-id="73980-113">**Create an empty search property list**</span></span>  
 <span data-ttu-id="73980-114">속성이 없는 검색 속성 목록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="73980-114">Creates a search property list without any properties.</span></span>  
  
 <span data-ttu-id="73980-115">**기존 검색 속성 목록에서 만들기**</span><span class="sxs-lookup"><span data-stu-id="73980-115">**Create from an existing search property list**</span></span>  
 <span data-ttu-id="73980-116">기존 검색 속성 목록의 속성을 새 속성 목록에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="73980-116">Copies the properties of an existing search property list into the new property list.</span></span> <span data-ttu-id="73980-117">검색 속성 목록은 데이터베이스 개체이므로 복사할 속성 목록이 포함된 데이터베이스를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73980-117">Search property lists are database objects, so you must specify the database that contains the property list that you want to copy.</span></span>  
  
 <span data-ttu-id="73980-118">**원본 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="73980-118">**Source database**</span></span>  
 <span data-ttu-id="73980-119">기존 검색 속성 목록이 속한 데이터베이스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="73980-119">Specify the name of the database to which the existing search property list belongs.</span></span> <span data-ttu-id="73980-120">기본적으로 현재 데이터베이스가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="73980-120">The current database is selected by default.</span></span> <span data-ttu-id="73980-121">현재 연결에 해당 데이터베이스에 있는 사용자 ID가 연결된 경우 필요에 따라 목록 상자를 사용하여 다른 데이터베이스를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73980-121">Optionally, you can use the list box to select another database, if your current connection is associated with a user ID in that database.</span></span>  
  
 <span data-ttu-id="73980-122">**원본 검색 속성 목록**</span><span class="sxs-lookup"><span data-stu-id="73980-122">**Source search property list**</span></span>  
 <span data-ttu-id="73980-123">선택한 데이터베이스에 속한 검색 속성 목록 중 기존 검색 속성 목록의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="73980-123">Select the name of an existing search property list from those belonging to the selected database.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="73980-124">사용 권한</span><span class="sxs-lookup"><span data-stu-id="73980-124">Permissions</span></span>  
 <span data-ttu-id="73980-125">[CREATE SEARCH PROPERTY LIST &#40;transact-sql&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="73980-125">See [CREATE SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql).</span></span>  
  
## <a name="to-use-sql-server-management-studio-to-manage-search-property-lists"></a><span data-ttu-id="73980-126">SQL Server Management Studio를 사용하여 검색 속성 목록을 관리하려면</span><span class="sxs-lookup"><span data-stu-id="73980-126">To Use SQL Server Management Studio to Manage Search Property Lists</span></span>  
 <span data-ttu-id="73980-127">검색 속성 목록을 만들거나, 보거나, 변경하거나, 삭제하는 방법과 속성 검색을 위해 전체 텍스트 인덱스를 구성하는 방법은 [Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="73980-127">For information about how to create, view, change, or delete a search property list, and about how to configure a full-text index for property searching, see [Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73980-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="73980-128">See Also</span></span>  
 <span data-ttu-id="73980-129">[Transact-sql&#41;&#40;검색 속성 목록 만들기](/sql/t-sql/statements/create-search-property-list-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="73980-129">[CREATE SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql) </span></span>  
 <span data-ttu-id="73980-130">[검색 속성 목록을 사용 하 여 문서 속성 검색](../relational-databases/search/search-document-properties-with-search-property-lists.md) </span><span class="sxs-lookup"><span data-stu-id="73980-130">[Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md) </span></span>  
 [<span data-ttu-id="73980-131">sys.registered_search_property_lists&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="73980-131">sys.registered_search_property_lists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql)  
  
  
