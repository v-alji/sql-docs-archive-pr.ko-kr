---
title: SQLXML 4.0의 Diffgram 소개 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotations [SQLXML]
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: 1902d67f-baf3-46e6-a36c-b24b5ba6f8ea
author: rothja
ms.author: jroth
ms.openlocfilehash: e57d87d064ace47247f342ed002b162b920e627f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651587"
---
# <a name="introduction-to-diffgrams-in-sqlxml-40"></a><span data-ttu-id="f520a-102">SQLXML 4.0의 DiffGrams 소개</span><span class="sxs-lookup"><span data-stu-id="f520a-102">Introduction to DiffGrams in SQLXML 4.0</span></span>
  <span data-ttu-id="f520a-103">이 항목에서는 DiffGrams에 대해 간략하게 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="f520a-103">This topic provides a brief introduction to DiffGrams.</span></span>  
  
## <a name="diffgram-format"></a><span data-ttu-id="f520a-104">DiffGram 형식</span><span class="sxs-lookup"><span data-stu-id="f520a-104">DiffGram Format</span></span>  
 <span data-ttu-id="f520a-105">일반 DiffGram 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f520a-105">This is the general DiffGram format:</span></span>  
  
```  
<?xml version="1.0"?>  
<diffgr:diffgram   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"  
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1"  
         xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
   <DataInstance>  
      ...  
   </DataInstance>  
   [<diffgr:before>  
        ...  
   </diffgr:before>]  
  
   [<diffgr:errors>  
        ...  
   </diffgr:errors>]  
</diffgr:diffgram>  
```  
  
 <span data-ttu-id="f520a-106">DiffGram 형식은 다음과 같은 블록으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f520a-106">The DiffGram format consists of these blocks:</span></span>  
  
 **\<DataInstance>**  
 <span data-ttu-id="f520a-107">이 요소의 이름 **Datainstance**는이 설명서의 설명을 위해 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f520a-107">The name of this element, **DataInstance**, is used for explanation purposes in this documentation.</span></span> <span data-ttu-id="f520a-108">예를 들어 .NET Framework의 데이터 집합에서 DiffGram을 생성 한 경우 데이터 집합의 **이름** 속성 값이이 요소의 이름으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f520a-108">For example, if the DiffGram were generated from a dataset in the .NET Framework, the value of the **Name** property of the dataset would be used as the name of this element.</span></span> <span data-ttu-id="f520a-109">이 블록에는 수정되지 않은 데이터를 포함하여 변경 후의 모든 관련 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f520a-109">This block contains all relevant data after the change, possibly including data that has not been modified.</span></span> <span data-ttu-id="f520a-110">DiffGram 처리 논리는이 블록에서 **diffgr: hasChanges** 특성이 지정 되지 않은 요소를 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f520a-110">The DiffGram processing logic ignores the elements in this block for which the **diffgr:hasChanges** attribute is not specified.</span></span>  
  
 **\<diffgr:before>**  
 <span data-ttu-id="f520a-111">이 선택적 블록에는 업데이트하거나 삭제해야 하는 원래 레코드 인스턴스(요소)가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f520a-111">This optional block contains the original record instances (elements) that must be updated or deleted.</span></span> <span data-ttu-id="f520a-112">DiffGram에서 수정 (업데이트 또는 삭제) 하는 모든 데이터베이스 테이블은 블록에서 최상위 요소로 나타나야 합니다 **\<before>** .</span><span class="sxs-lookup"><span data-stu-id="f520a-112">All the database tables being modified (updated or deleted) by the DiffGram must appear as top-level elements in the **\<before>** block.</span></span>  
  
 **\<diffgr:errors>**  
 <span data-ttu-id="f520a-113">이 선택적 블록은 DiffGram 처리 논리에서 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f520a-113">This optional block is ignored by the DiffGram processing logic.</span></span>  
  
## <a name="diffgram-annotations"></a><span data-ttu-id="f520a-114">DiffGram 주석</span><span class="sxs-lookup"><span data-stu-id="f520a-114">DiffGram Annotations</span></span>  
 <span data-ttu-id="f520a-115">이러한 주석은 DiffGram 네임 스페이스 **"urn: 스키마-microsoft-com: diffgram-01"** 에 정의 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f520a-115">These annotations are defined in the DiffGram namespace **"urn:schemas-microsoft-com:xml-diffgram-01"**:</span></span>  
  
 <span data-ttu-id="f520a-116">**ID**</span><span class="sxs-lookup"><span data-stu-id="f520a-116">**id**</span></span>  
 <span data-ttu-id="f520a-117">이 특성은 및 블록의 요소를 쌍으로 연결 하는 데 사용 됩니다 **\<before>** **\<DataInstance>** .</span><span class="sxs-lookup"><span data-stu-id="f520a-117">This attribute is used to pair the elements in the **\<before>** and the **\<DataInstance>** blocks.</span></span>  
  
 <span data-ttu-id="f520a-118">**hasChanges**</span><span class="sxs-lookup"><span data-stu-id="f520a-118">**hasChanges**</span></span>  
 <span data-ttu-id="f520a-119">삽입 또는 업데이트 작업의 경우 DiffGram은 **삽입** 또는 **수정**된 값을 사용 하 여이 특성을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f520a-119">For an insert or an update operation, the DiffGram must specify this attribute with the value **inserted** or **modified**.</span></span> <span data-ttu-id="f520a-120">이 특성이 없는 경우의 해당 요소는 **\<DataInstance>** 처리 논리에서 무시 되 고 업데이트가 수행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f520a-120">If this attribute is not present, the corresponding element in the **\<DataInstance>** is ignored by the processing logic and no updates are performed.</span></span> <span data-ttu-id="f520a-121">작업 예제는 [DiffGram 예 &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f520a-121">For working samples, see [DiffGram Examples &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="f520a-122">**parentID**</span><span class="sxs-lookup"><span data-stu-id="f520a-122">**parentID**</span></span>  
 <span data-ttu-id="f520a-123">이 특성은 DiffGram에서 요소 간의 부모-자식 관계를 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f520a-123">This attribute is used to specify parent-child relationships among the elements in the DiffGram.</span></span> <span data-ttu-id="f520a-124">이 특성은 블록에만 표시 됩니다 \<before> .</span><span class="sxs-lookup"><span data-stu-id="f520a-124">This attribute appears only in the \<before> block.</span></span> <span data-ttu-id="f520a-125">SQLXML에서 업데이트를 적용할 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f520a-125">It is used by SQLXML when applying updates.</span></span> <span data-ttu-id="f520a-126">부모-자식 관계는 DiffGram에서 요소가 처리되는 순서를 결정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f520a-126">The parent-child relationship is used in determining the order in which the elements in the DiffGram are processed.</span></span>  
  
## <a name="understanding-the-diffgram-processing-logic"></a><span data-ttu-id="f520a-127">DiffGram 처리 논리 이해</span><span class="sxs-lookup"><span data-stu-id="f520a-127">Understanding the DiffGram Processing Logic</span></span>  
 <span data-ttu-id="f520a-128">DiffGram 처리 논리는 특정 규칙에 따라 작업이 삽입, 업데이트 또는 삭제 작업인지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="f520a-128">The DiffGram processing logic uses certain rules to determine whether an operation is an insert, update, or delete operation.</span></span> <span data-ttu-id="f520a-129">다음 표에서는 이러한 규칙에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f520a-129">These rules are described in the following table.</span></span>  
  
|<span data-ttu-id="f520a-130">작업(Operation)</span><span class="sxs-lookup"><span data-stu-id="f520a-130">Operation</span></span>|<span data-ttu-id="f520a-131">Description</span><span class="sxs-lookup"><span data-stu-id="f520a-131">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f520a-132">Insert</span><span class="sxs-lookup"><span data-stu-id="f520a-132">Insert</span></span>|<span data-ttu-id="f520a-133">DiffGram은 요소가 블록에 표시 되 고 **\<DataInstance>** 해당 블록에는 표시 되지 않고 **\<before>** 요소에 대해 **Diffgr: haschanges** 특성이 지정 된 경우 (**diffgr: haschanges = inserted**) 삽입 작업을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f520a-133">A DiffGram indicates an insert operation when an element appears in the **\<DataInstance>** block but not in the corresponding **\<before>** block, and the **diffgr:hasChanges** attribute is specified (**diffgr:hasChanges=inserted**) on the element.</span></span> <span data-ttu-id="f520a-134">이 경우 DiffGram은 블록에 지정 된 레코드 인스턴스를 데이터베이스에 삽입 합니다 **\<DataInstance>** .</span><span class="sxs-lookup"><span data-stu-id="f520a-134">In this case, the DiffGram inserts the record instance that is specified in the **\<DataInstance>** block into the database.</span></span><br /><br /> <span data-ttu-id="f520a-135">**Diffgr: hasChanges** 특성이 지정 되지 않은 경우 요소는 처리 논리에서 무시 되 고 삽입이 수행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f520a-135">If the **diffgr:hasChanges** attribute is not specified, the element is ignored by the processing logic and no insert is performed.</span></span> <span data-ttu-id="f520a-136">작업 예제는 [DiffGram 예 &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f520a-136">For working samples, see [DiffGram Examples &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md).</span></span>|  
|<span data-ttu-id="f520a-137">업데이트</span><span class="sxs-lookup"><span data-stu-id="f520a-137">Update</span></span>|<span data-ttu-id="f520a-138">DiffGram은 블록에 \<before> 해당 요소가 있는 요소 **\<DataInstance>** (즉, 두 요소에 동일한 값이 있는 **diffgr: id** 특성)가 있고, **diffgr: haschanges** 특성이 블록의 요소에서 **수정** 된 값으로 지정 된 경우 업데이트 작업을 나타냅니다 **\<DataInstance>** .</span><span class="sxs-lookup"><span data-stu-id="f520a-138">The DiffGram indicates an update operation when there is an element in the \<before> block for which there is a corresponding element in the **\<DataInstance>** block (that is, both elements have a **diffgr:id** attribute with same value) and the **diffgr:hasChanges** attribute is specified with the value **modified** on the element in the **\<DataInstance>** block.</span></span><br /><br /> <span data-ttu-id="f520a-139">블록의 요소에 대해 **diffgr: hasChanges** 특성이 지정 되지 않은 경우 **\<DataInstance>** 처리 논리에 의해 오류가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f520a-139">If the **diffgr:hasChanges** attribute is not specified on the element in the **\<DataInstance>** block, an error is returned by the processing logic.</span></span> <span data-ttu-id="f520a-140">작업 예제는 [DiffGram 예 &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f520a-140">For working samples, see [DiffGram Examples &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md).</span></span><br /><br /> <span data-ttu-id="f520a-141">블록에 **diffgr: parentID** 이 지정 된 경우 **\<before>** **parentID** 로 지정 된 요소의 부모-자식 관계를 사용 하 여 레코드가 업데이트 되는 순서를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f520a-141">If **diffgr:parentID** is specified in the **\<before>** block, the parent-child relationship of elements that are specified by **parentID** are used in determining the order in which records are updated.</span></span>|  
|<span data-ttu-id="f520a-142">삭제</span><span class="sxs-lookup"><span data-stu-id="f520a-142">Delete</span></span>|<span data-ttu-id="f520a-143">DiffGram은 요소가 블록에는 나타나지만 해당 블록에는 없는 경우 삭제 작업을 나타냅니다 **\<before>** **\<DataInstance>** .</span><span class="sxs-lookup"><span data-stu-id="f520a-143">A DiffGram indicates a delete operation when an element appears in the **\<before>** block but not in the corresponding **\<DataInstance>** block.</span></span> <span data-ttu-id="f520a-144">이 경우 DiffGram은 블록에 지정 된 레코드 인스턴스를 데이터베이스에서 삭제 합니다 **\<before>** .</span><span class="sxs-lookup"><span data-stu-id="f520a-144">In this case, the DiffGram deletes the record instance that is specified in the **\<before>** block from the database.</span></span> <span data-ttu-id="f520a-145">작업 예제는 [DiffGram 예 &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f520a-145">For working samples, see [DiffGram Examples &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md).</span></span><br /><br /> <span data-ttu-id="f520a-146">블록에 **diffgr: parentID** 이 지정 된 경우 **\<before>** **parentID** 에 의해 지정 된 요소의 부모-자식 관계를 사용 하 여 레코드를 삭제 하는 순서를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f520a-146">If **diffgr:parentID** is specified in the **\<before>** block, the parent-child relationship of elements that are specified by **parentID** are used in determining the order in which records are deleted.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="f520a-147">DiffGrams에 매개 변수를 전달할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f520a-147">Parameters cannot be passed to DiffGrams.</span></span>  
  
  
