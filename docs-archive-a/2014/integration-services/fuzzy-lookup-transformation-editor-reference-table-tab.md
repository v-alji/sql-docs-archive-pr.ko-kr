---
title: 유사 항목 조회 변환 편집기 (참조 테이블 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzylookuptransformation.referencetable.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: 451f4e7d-1c8e-4784-b540-df0806509bf1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9ce51dd64c9c5807ab23ac645694cfec29a36d52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647127"
---
# <a name="fuzzy-lookup-transformation-editor-reference-table-tab"></a><span data-ttu-id="c25c6-102">유사 항목 조회 변환 편집기(참조 테이블 탭)</span><span class="sxs-lookup"><span data-stu-id="c25c6-102">Fuzzy Lookup Transformation Editor (Reference Table Tab)</span></span>
  <span data-ttu-id="c25c6-103">**유사 항목 조회 변환 편집기** 대화 상자의 **참조 테이블** 탭을 사용하여 조회 시 사용할 원본 테이블 및 인덱스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c25c6-103">Use the **Reference Table** tab of the **Fuzzy Lookup Transformation Editor** dialog box to specify the source table and the index to use for the lookup.</span></span> <span data-ttu-id="c25c6-104">참조 데이터 원본은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스에 있는 테이블이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c25c6-104">The reference data source must be a table in a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c25c6-105">유사 항목 조회 변환은 참조 테이블의 작업 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c25c6-105">The Fuzzy Lookup transformation creates a working copy of the reference table.</span></span> <span data-ttu-id="c25c6-106">아래에서 설명하는 인덱스는 일반 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인덱스가 아닌 특수 테이블을 사용하여 이 작업 테이블에 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c25c6-106">The indexes described below are created on this working table by using a special table, not an ordinary [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] index.</span></span> <span data-ttu-id="c25c6-107">**저장된 인덱스 유지 관리**를 선택하지 않으면 변환에서 기존 원본 테이블을 수정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c25c6-107">The transformation does not modify the existing source tables unless you select **Maintain stored index**.</span></span> <span data-ttu-id="c25c6-108">이 경우 변환에서는 참조 테이블에 대한 변경 내용을 기반으로 작업 테이블 및 조회 인덱스 테이블을 업데이트하는 트리거를 참조 테이블에 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c25c6-108">In this case, it creates a trigger on the reference table that updates the working table and the lookup index table based on changes to the reference table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c25c6-109">유사 `Exhaustive` `MaxMemoryUsage` 항목 조회 변환의 및 속성은 **유사 항목 조회 변환 편집기**에서 사용할 수 없지만 **고급 편집기**를 사용 하 여 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c25c6-109">The `Exhaustive` and the `MaxMemoryUsage` properties of the Fuzzy Lookup transformation are not available in the **Fuzzy Lookup Transformation Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="c25c6-110">또한에 대 한 100 보다 큰 값은 `MaxOutputMatchesPerInput` **고급 편집기**에서만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c25c6-110">In addition, a value greater than 100 for `MaxOutputMatchesPerInput` can be specified only in the **Advanced Editor**.</span></span> <span data-ttu-id="c25c6-111">이러한 속성에 대한 자세한 내용은 [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md)의 유사 항목 조회 변환 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c25c6-111">For more information on these properties, see the Fuzzy Lookup Transformation section of [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="c25c6-112">유사 항목 조회 변환에 대한 자세한 내용은 [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c25c6-112">To learn more about the Fuzzy Lookup transformation, see [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="c25c6-113">옵션</span><span class="sxs-lookup"><span data-stu-id="c25c6-113">Options</span></span>  
 <span data-ttu-id="c25c6-114">**캐시 없음**</span><span class="sxs-lookup"><span data-stu-id="c25c6-114">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="c25c6-115">목록에서 기존 OLE DB 연결 관리자를 선택하거나 **새로 만들기**를 클릭하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c25c6-115">Select an existing OLE DB connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="c25c6-116">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="c25c6-116">**New**</span></span>  
 <span data-ttu-id="c25c6-117">**OLE DB 연결 관리자 구성** 대화 상자를 사용하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c25c6-117">Create a new connection by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="c25c6-118">**새 인덱스 생성**</span><span class="sxs-lookup"><span data-stu-id="c25c6-118">**Generate new index**</span></span>  
 <span data-ttu-id="c25c6-119">변환에서 조회 시 사용할 새 인덱스를 만들도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c25c6-119">Specify that the transformation should create a new index to use for the lookup.</span></span>  
  
 <span data-ttu-id="c25c6-120">**참조 테이블 이름**</span><span class="sxs-lookup"><span data-stu-id="c25c6-120">**Reference table name**</span></span>  
 <span data-ttu-id="c25c6-121">참조(조회) 테이블로 사용할 기존 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c25c6-121">Select the existing table to use as the reference (lookup) table.</span></span>  
  
 <span data-ttu-id="c25c6-122">**새 인덱스 저장**</span><span class="sxs-lookup"><span data-stu-id="c25c6-122">**Store new index**</span></span>  
 <span data-ttu-id="c25c6-123">새 조회 인덱스를 저장하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c25c6-123">Select this option if you want to save the new lookup index.</span></span>  
  
 <span data-ttu-id="c25c6-124">**새 인덱스 이름**</span><span class="sxs-lookup"><span data-stu-id="c25c6-124">**New index name**</span></span>  
 <span data-ttu-id="c25c6-125">새 조회 인덱스를 저장하도록 선택한 경우 해당 인덱스를 설명하는 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c25c6-125">If you have chosen to save the new lookup index, type a descriptive name for the index.</span></span>  
  
 <span data-ttu-id="c25c6-126">**저장된 인덱스 유지 관리**</span><span class="sxs-lookup"><span data-stu-id="c25c6-126">**Maintain stored index**</span></span>  
 <span data-ttu-id="c25c6-127">새 조회 인덱스를 저장하도록 선택한 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서 해당 인덱스를 유지 관리하도록 할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c25c6-127">If you have chosen to save the new lookup index, specify whether you also want [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to maintain the index.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c25c6-128">**유사 항목 조회 변환 편집기** 의 **참조 테이블** 에서 **저장된 인덱스 유지 관리**를 선택하면 변환은 관리 저장 프로시저를 사용하여 인덱스를 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="c25c6-128">When you select **Maintain stored index** on the **Reference Table** tab of the **Fuzzy Lookup Transformation Editor**, the transformation uses managed stored procedures to maintain the index.</span></span> <span data-ttu-id="c25c6-129">이러한 관리 저장 프로시저는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 CLR(공용 언어 런타임) 통합 기능을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c25c6-129">These managed stored procedures use the common language runtime (CLR) integration feature in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c25c6-130">기본적으로 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 CLR 통합은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c25c6-130">By default, CLR integration in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is not enabled.</span></span> <span data-ttu-id="c25c6-131">**저장된 인덱스 유지 관리** 기능을 사용하려면 CLR 통합을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c25c6-131">To use the **Maintain stored index** functionality, you must enable CLR integration.</span></span> <span data-ttu-id="c25c6-132">자세한 내용은 [Enabling CLR Integration](../relational-databases/clr-integration/clr-integration-enabling.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c25c6-132">For more information, see [Enabling CLR Integration](../relational-databases/clr-integration/clr-integration-enabling.md).</span></span>  
>   
>  <span data-ttu-id="c25c6-133">**저장된 인덱스 유지 관리** 옵션에는 CLR 통합이 필요하므로 CLR 통합이 사용되는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 인스턴스에 있는 참조 테이블을 선택하는 경우에만 이 기능이 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="c25c6-133">Because the **Maintain stored index** option requires CLR integration, this feature works only when you select a reference table on an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] where CLR integration is enabled.</span></span>  
  
 <span data-ttu-id="c25c6-134">**기존 인덱스 사용**</span><span class="sxs-lookup"><span data-stu-id="c25c6-134">**Use existing index**</span></span>  
 <span data-ttu-id="c25c6-135">변환에서 조회 시 기존 인덱스를 사용하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c25c6-135">Specify that the transformation should use an existing index for the lookup.</span></span>  
  
 <span data-ttu-id="c25c6-136">**기존 인덱스의 이름**</span><span class="sxs-lookup"><span data-stu-id="c25c6-136">**Name of an existing index**</span></span>  
 <span data-ttu-id="c25c6-137">목록에서 이전에 만든 조회 인덱스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c25c6-137">Select a previously created lookup index from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c25c6-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c25c6-138">See Also</span></span>  
 <span data-ttu-id="c25c6-139">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="c25c6-139">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="c25c6-140">[유사 항목 조회 변환 편집기 &#40;열 탭&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-columns-tab.md) </span><span class="sxs-lookup"><span data-stu-id="c25c6-140">[Fuzzy Lookup Transformation Editor &#40;Columns Tab&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-columns-tab.md) </span></span>  
 [<span data-ttu-id="c25c6-141">유사 항목 조회 변환 편집기&#40;고급 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="c25c6-141">Fuzzy Lookup Transformation Editor &#40;Advanced Tab&#41;</span></span>](../../2014/integration-services/fuzzy-lookup-transformation-editor-advanced-tab.md)  
  
  
