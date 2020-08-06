---
title: OData 원본 편집기 (연결 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- Sql12.dts.designer.odatasource.connection.f1
ms.assetid: 20bcd347-4547-4fad-b182-9571030101df
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6ecd0d060ea2197ae7174325b654645fefa23505
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652198"
---
# <a name="odata-source-editor-connection-page"></a><span data-ttu-id="fd787-102">OData 원본 편집기(연결 페이지)</span><span class="sxs-lookup"><span data-stu-id="fd787-102">OData Source Editor (Connection Page)</span></span>
  <span data-ttu-id="fd787-103">**OData 원본 편집기** 대화 상자의 **연결** 페이지를 사용하여 OData 원본의 OData 연결 관리자를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd787-103">Use the **Connection** page of the **OData Source Editor** dialog box to select the OData connection manager for the OData source.</span></span> <span data-ttu-id="fd787-104">또한 이 페이지에서 컬렉션 또는 리소스 경로와 쿼리 옵션을 지정하여 OData 원본에서 검색해야 하는 데이터를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd787-104">This page also lets you specify a collection or a resource path and any query options to indicate what data needs to be retrieved from the OData source.</span></span> <span data-ttu-id="fd787-105">OData 원본에 대한 자세한 내용은 [OData Source](data-flow/odata-source.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="fd787-105">To learn more about the OData source, see [OData Source](data-flow/odata-source.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="fd787-106">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="fd787-106">Static Options</span></span>  
 <span data-ttu-id="fd787-107">**OData 연결 관리자**</span><span class="sxs-lookup"><span data-stu-id="fd787-107">**OData connection manager**</span></span>  
 <span data-ttu-id="fd787-108">목록에서 기존 연결 관리자를 선택하거나 **새로 만들기**를 클릭하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fd787-108">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="fd787-109">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="fd787-109">**New**</span></span>  
 <span data-ttu-id="fd787-110">**OData 연결 관리자 편집기** 대화 상자를 사용하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fd787-110">Create a new connection manager by using the **OData Connection Manager Editor** dialog box.</span></span>  
  
 <span data-ttu-id="fd787-111">**컬렉션 또는 리소스 경로 사용**</span><span class="sxs-lookup"><span data-stu-id="fd787-111">**Use collection or resource path**</span></span>  
 <span data-ttu-id="fd787-112">원본에서 데이터를 선택하는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fd787-112">Specify the method for selecting data from the source.</span></span>  
  
|<span data-ttu-id="fd787-113">옵션</span><span class="sxs-lookup"><span data-stu-id="fd787-113">Option</span></span>|<span data-ttu-id="fd787-114">Description</span><span class="sxs-lookup"><span data-stu-id="fd787-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="fd787-115">컬렉션</span><span class="sxs-lookup"><span data-stu-id="fd787-115">Collection</span></span>|<span data-ttu-id="fd787-116">컬렉션 이름을 사용하여 OData 원본에서 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="fd787-116">Retrieve data from the OData source by using a collection name.</span></span>|  
|<span data-ttu-id="fd787-117">리소스 경로</span><span class="sxs-lookup"><span data-stu-id="fd787-117">Resource Path</span></span>|<span data-ttu-id="fd787-118">리소스 경로를 사용하여 OData 원본에서 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="fd787-118">Retrieve data from the OData source by using a resource path.</span></span>|  
  
 <span data-ttu-id="fd787-119">**쿼리 옵션**</span><span class="sxs-lookup"><span data-stu-id="fd787-119">**Query options**</span></span>  
 <span data-ttu-id="fd787-120">쿼리에 대한 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fd787-120">Specify options for the query.</span></span>  <span data-ttu-id="fd787-121">예: $top=5</span><span class="sxs-lookup"><span data-stu-id="fd787-121">For example: $top=5</span></span>  
  
 <span data-ttu-id="fd787-122">**피드 URL**</span><span class="sxs-lookup"><span data-stu-id="fd787-122">**Feed url**</span></span>  
 <span data-ttu-id="fd787-123">이 대화 상자에서 선택한 옵션에 따라 읽기 전용 피드 URL을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fd787-123">Displays the read-only Feed URL based on options you selected on this dialog box.</span></span>  
  
 <span data-ttu-id="fd787-124">**미리 보기**</span><span class="sxs-lookup"><span data-stu-id="fd787-124">**Preview**</span></span>  
 <span data-ttu-id="fd787-125">**미리 보기** 대화 상자를 사용하여 결과를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="fd787-125">Preview results by using the **Preview** dialog box.</span></span> <span data-ttu-id="fd787-126">**미리 보기** 에는 최대 20개의 행이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd787-126">**Preview** can display up to 20 rows.</span></span>  
  
## <a name="dynamic-options"></a><span data-ttu-id="fd787-127">동적 옵션</span><span class="sxs-lookup"><span data-stu-id="fd787-127">Dynamic Options</span></span>  
  
### <a name="use-collection-or-resource-path--collection"></a><span data-ttu-id="fd787-128">컬렉션 또는 리소스 경로 사용 = 컬렉션</span><span class="sxs-lookup"><span data-stu-id="fd787-128">Use collection or resource path = Collection</span></span>  
 <span data-ttu-id="fd787-129">**컬렉션**</span><span class="sxs-lookup"><span data-stu-id="fd787-129">**Collection**</span></span>  
 <span data-ttu-id="fd787-130">드롭다운 목록에서 컬렉션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fd787-130">Select a collection from the drop-down list.</span></span>  
  
### <a name="use-collection-or-resource-path--resource-path"></a><span data-ttu-id="fd787-131">컬렉션 또는 리소스 경로 사용 = 리소스 경로</span><span class="sxs-lookup"><span data-stu-id="fd787-131">Use collection or resource path = Resource Path</span></span>  
 <span data-ttu-id="fd787-132">**Resource path**</span><span class="sxs-lookup"><span data-stu-id="fd787-132">**Resource path**</span></span>  
 <span data-ttu-id="fd787-133">리소스 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fd787-133">Type a resource path.</span></span> <span data-ttu-id="fd787-134">예: Employees</span><span class="sxs-lookup"><span data-stu-id="fd787-134">For example: Employees</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd787-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fd787-135">See Also</span></span>  
 <span data-ttu-id="fd787-136">[OData 원본 편집기 &#40;열 페이지&#41;](../../2014/integration-services/odata-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="fd787-136">[OData Source Editor &#40;Columns Page&#41;](../../2014/integration-services/odata-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="fd787-137">[OData 원본 편집기 &#40;오류 출력 페이지&#41;](../../2014/integration-services/odata-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="fd787-137">[OData Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/odata-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="fd787-138">OData 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="fd787-138">OData Connection Manager</span></span>](connection-manager/odata-connection-manager.md)  
  
  
