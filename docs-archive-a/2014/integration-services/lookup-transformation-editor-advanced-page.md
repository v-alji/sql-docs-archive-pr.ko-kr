---
title: 조회 변환 편집기 (고급 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.advanced.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: f3395c65-0320-47f9-8d83-daaa082d8713
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 23f235ef0506da7ac808d832db6ac36d53cfa604
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651102"
---
# <a name="lookup-transformation-editor-advanced-page"></a><span data-ttu-id="ebcf4-102">조회 변환 편집기(고급 페이지)</span><span class="sxs-lookup"><span data-stu-id="ebcf4-102">Lookup Transformation Editor (Advanced Page)</span></span>
  <span data-ttu-id="ebcf4-103">**조회 변환 편집기** 대화 상자의 **고급** 페이지를 사용하여 조회 변환의 부분 캐싱을 구성하고 SQL 문을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebcf4-103">Use the **Advanced** page of the **Lookup Transformation Editor** dialog box to configure partial caching and to modify the SQL statement for the Lookup transformation.</span></span>  
  
 <span data-ttu-id="ebcf4-104">조회 변환에 대한 자세한 내용은 [Lookup Transformation](data-flow/transformations/lookup-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ebcf4-104">To learn more about the Lookup transformation, see [Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="ebcf4-105">옵션</span><span class="sxs-lookup"><span data-stu-id="ebcf4-105">Options</span></span>  
 <span data-ttu-id="ebcf4-106">**캐시 크기(32비트)**</span><span class="sxs-lookup"><span data-stu-id="ebcf4-106">**Cache size (32-bit)**</span></span>  
 <span data-ttu-id="ebcf4-107">32비트 컴퓨터의 캐시 크기(MB)를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcf4-107">Adjust the  cache size (in megabytes) for 32-bit computers.</span></span> <span data-ttu-id="ebcf4-108">기본값은 5MB입니다.</span><span class="sxs-lookup"><span data-stu-id="ebcf4-108">The default value is 5 megabytes.</span></span>  
  
 <span data-ttu-id="ebcf4-109">**캐시 크기(64비트)**</span><span class="sxs-lookup"><span data-stu-id="ebcf4-109">**Cache size (64-bit)**</span></span>  
 <span data-ttu-id="ebcf4-110">64비트 컴퓨터의 캐시 크기(MB)를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcf4-110">Adjust the cache size (in megabytes) for 64-bit computers.</span></span> <span data-ttu-id="ebcf4-111">기본값은 5MB입니다.</span><span class="sxs-lookup"><span data-stu-id="ebcf4-111">The default value is 5 megabytes.</span></span>  
  
 <span data-ttu-id="ebcf4-112">**일치하는 항목이 없는 행에 캐시 사용**</span><span class="sxs-lookup"><span data-stu-id="ebcf4-112">**Enable cache for rows with no matching entries**</span></span>  
 <span data-ttu-id="ebcf4-113">참조 데이터 세트에서 일치하는 항목이 없는 행을 캐시합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcf4-113">Cache rows with no matching entries in the reference dataset.</span></span>  
  
 <span data-ttu-id="ebcf4-114">**캐시에서 할당**</span><span class="sxs-lookup"><span data-stu-id="ebcf4-114">**Allocation from cache**</span></span>  
 <span data-ttu-id="ebcf4-115">참조 데이터 세트에서 일치하는 항목이 없는 행에 할당할 캐시 비율을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcf4-115">Specify the percentage of the cache to allocate for rows with no matching entries in the reference dataset.</span></span>  
  
 <span data-ttu-id="ebcf4-116">**SQL 문 수정**</span><span class="sxs-lookup"><span data-stu-id="ebcf4-116">**Modify the SQL statement**</span></span>  
 <span data-ttu-id="ebcf4-117">참조 데이터 세트를 생성하는 데 사용되는 SQL 문을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcf4-117">Modify the SQL statement that is used to generate the reference dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ebcf4-118">이 페이지에서 지정하는 선택적 SQL 문이 **조회 변환 편집기** 의 **연결**페이지에서 지정한 테이블 이름을 재정의하고 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcf4-118">The optional SQL statement that you specify on this page overrides and replaces the table name that you specified on the **Connection** page of the **Lookup Transformation Editor**.</span></span> <span data-ttu-id="ebcf4-119">자세한 내용은 [조회 변환 편집기&#40;연결 페이지&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ebcf4-119">For more information, see [Lookup Transformation Editor &#40;Connection Page&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md).</span></span>  
  
 <span data-ttu-id="ebcf4-120">**매개 변수**</span><span class="sxs-lookup"><span data-stu-id="ebcf4-120">**Set Parameters**</span></span>  
 <span data-ttu-id="ebcf4-121">**쿼리 매개 변수 설정** 대화 상자를 사용하여 입력 열을 매개 변수에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcf4-121">Map input columns to parameters by using the **Set Query Parameters** dialog box.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="ebcf4-122">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="ebcf4-122">External Resources</span></span>  
 <span data-ttu-id="ebcf4-123">blogs.msdn.com의 블로그 항목 - [조회 캐시 모드](https://go.microsoft.com/fwlink/?LinkId=219518)</span><span class="sxs-lookup"><span data-stu-id="ebcf4-123">Blog entry, [Lookup cache modes](https://go.microsoft.com/fwlink/?LinkId=219518) on blogs.msdn.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebcf4-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ebcf4-124">See Also</span></span>  
 <span data-ttu-id="ebcf4-125">[조회 변환 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="ebcf4-125">[Lookup Transformation Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="ebcf4-126">[조회 변환 편집기 &#40;연결 페이지&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md) </span><span class="sxs-lookup"><span data-stu-id="ebcf4-126">[Lookup Transformation Editor &#40;Connection Page&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md) </span></span>  
 <span data-ttu-id="ebcf4-127">[조회 변환 편집기 &#40;열 페이지&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="ebcf4-127">[Lookup Transformation Editor &#40;Columns Page&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md) </span></span>  
 <span data-ttu-id="ebcf4-128">[조회 변환 편집기 &#40;오류 출력 페이지&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="ebcf4-128">[Lookup Transformation Editor &#40;Error Output Page&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="ebcf4-129">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="ebcf4-129">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="ebcf4-130">유사 항목 조회 변환</span><span class="sxs-lookup"><span data-stu-id="ebcf4-130">Fuzzy Lookup Transformation</span></span>](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  
