---
title: XML 인덱스 대화 상자(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.xmlindexes
ms.assetid: eef38310-4498-4ccc-bb77-5bbd1c7cc477
author: stevestein
ms.author: sstein
ms.openlocfilehash: f1fb23a801a9129611c032fa1d659caf624088aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652484"
---
# <a name="xml-indexes-dialog-box-visual-database-tools"></a><span data-ttu-id="415b6-102">XML 인덱스 대화 상자(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="415b6-102">XML Indexes Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="415b6-103">**XML 인덱스** 대화 상자를 사용하면 **인덱스/키** 대화 상자를 통해 인덱싱할 수 없는 XML 데이터 형식의 열에 대한 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-103">Use the **XML Indexes** dialog box to create indexes for columns of the data type XML, which cannot be indexed using the **Index/Keys** dialog box.</span></span> <span data-ttu-id="415b6-104">각 XML 열에는 두 개 이상의 XML 인덱스가 있을 수 있지만 첫 번째 작성된 인덱스(기본 인덱스)가 나머지 인덱스(보조 인덱스)의 기준으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-104">Each XML column can have more than one XML Index, but the first one created (primary) will be the basis of the others (secondary).</span></span> <span data-ttu-id="415b6-105">기본 XML 인덱스를 삭제하면 보조 인덱스도 함께 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-105">If you delete the primary XML index, the secondary indexes will also be deleted.</span></span>  
  
## <a name="options"></a><span data-ttu-id="415b6-106">옵션</span><span class="sxs-lookup"><span data-stu-id="415b6-106">Options</span></span>  
 <span data-ttu-id="415b6-107">**선택한 XML 인덱스**</span><span class="sxs-lookup"><span data-stu-id="415b6-107">**Selected XML Index**</span></span>  
 <span data-ttu-id="415b6-108">기존 XML 인덱스가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-108">Lists existing XML indexes.</span></span> <span data-ttu-id="415b6-109">인덱스를 선택하면 오른쪽 표에 해당 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-109">Select to show its properties in the grid to the right.</span></span> <span data-ttu-id="415b6-110">목록이 비어 있는 경우 테이블에 정의된 항목이 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-110">If the list is empty, none have been defined for the table.</span></span>  
  
 <span data-ttu-id="415b6-111">**추가**</span><span class="sxs-lookup"><span data-stu-id="415b6-111">**Add**</span></span>  
 <span data-ttu-id="415b6-112">새 XML 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-112">Create a new XML index.</span></span>  
  
 <span data-ttu-id="415b6-113">**Delete**</span><span class="sxs-lookup"><span data-stu-id="415b6-113">**Delete**</span></span>  
 <span data-ttu-id="415b6-114">**선택한 XML 인덱스** 목록에서 선택한 XML 인덱스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-114">Delete XML index selected in the **Selected XML Index** list.</span></span> <span data-ttu-id="415b6-115">기본 XML 인덱스를 삭제하는 경우 보조 인덱스도 모두 함께 삭제된다는 메시지가 표시되고 동작을 계속 진행하거나 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-115">If you delete the primary XML index, you will be notified that this will delete all secondary ones as well, and you can either continue or cancel the action.</span></span>  
  
 <span data-ttu-id="415b6-116">**일반 범주**</span><span class="sxs-lookup"><span data-stu-id="415b6-116">**General Category**</span></span>  
 <span data-ttu-id="415b6-117">확장하면 **열**, **기본**및 **형식**에 대한 속성 필드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-117">When expanded, shows the property fields for **Columns**, **Is Primary**, and **Type**.</span></span>  
  
 <span data-ttu-id="415b6-118">**열**</span><span class="sxs-lookup"><span data-stu-id="415b6-118">**Columns**</span></span>  
 <span data-ttu-id="415b6-119">현재 인덱스를 오름차순으로 정렬하여 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-119">Shows that this index is sorted in ascending order.</span></span>  
  
 <span data-ttu-id="415b6-120">**기본**</span><span class="sxs-lookup"><span data-stu-id="415b6-120">**Is Primary**</span></span>  
 <span data-ttu-id="415b6-121">현재 인덱스가 기본 인덱스인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-121">Indicates whether this is the primary index.</span></span> <span data-ttu-id="415b6-122">열에서 만든 첫 번째 XML 인덱스가 나머지 인덱스의 기본으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-122">The first XML index created on the column will be the basis of the others.</span></span>  
  
 <span data-ttu-id="415b6-123">**기본 참조 이름**</span><span class="sxs-lookup"><span data-stu-id="415b6-123">**Primary reference name**</span></span>  
 <span data-ttu-id="415b6-124">현재 인덱스가 보조 인덱스인 경우 기본 인덱스의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-124">Shows the name of the primary index if this is a secondary index.</span></span> <span data-ttu-id="415b6-125">현재 인덱스가 보조 인덱스인 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-125">Only available if this is a secondary index.</span></span>  
  
 <span data-ttu-id="415b6-126">**보조 형식**</span><span class="sxs-lookup"><span data-stu-id="415b6-126">**Secondary type**</span></span>  
 <span data-ttu-id="415b6-127">보조 인덱스의 형식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-127">Shows the type of secondary index.</span></span> <span data-ttu-id="415b6-128">현재 인덱스가 보조 인덱스인 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-128">Only available if this is a secondary index.</span></span>  
  
 <span data-ttu-id="415b6-129">**형식**</span><span class="sxs-lookup"><span data-stu-id="415b6-129">**Type**</span></span>  
 <span data-ttu-id="415b6-130">현재 인덱스가 XML 인덱스인지 여부를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-130">Shows that this is an XML index.</span></span>  
  
 <span data-ttu-id="415b6-131">**ID 범주**</span><span class="sxs-lookup"><span data-stu-id="415b6-131">**Identity Category**</span></span>  
 <span data-ttu-id="415b6-132">확장하면 **이름** 및 **설명** 속성 필드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-132">When expanded, shows the **Name** and **Description** property fields.</span></span>  
  
 <span data-ttu-id="415b6-133">**이름**</span><span class="sxs-lookup"><span data-stu-id="415b6-133">**Name**</span></span>  
 <span data-ttu-id="415b6-134">XML 인덱스의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-134">Shows the name of the XML index.</span></span> <span data-ttu-id="415b6-135">키나 인덱스를 새로 만들면 테이블 디자이너의 활성 창에 있는 테이블을 기반으로 한 기본 이름이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-135">When a new one is created, it is given a default name based on the table in the active window in Table Designer.</span></span> <span data-ttu-id="415b6-136">언제든지 이름을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-136">You can change the name at any time.</span></span>  
  
 <span data-ttu-id="415b6-137">**설명**</span><span class="sxs-lookup"><span data-stu-id="415b6-137">**Description**</span></span>  
 <span data-ttu-id="415b6-138">인덱스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-138">Describe the index.</span></span> <span data-ttu-id="415b6-139">자세한 설명을 기록하려면 **설명**을 클릭한 다음, 속성 필드의 오른쪽에 있는 줄임표 단추( **...** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-139">To write a more detailed description, click **Description** and then click the ellipsis button (**...**) that appears to the right of the property field.</span></span> <span data-ttu-id="415b6-140">이렇게 하면 텍스트를 쓸 수 있는 더 큰 영역이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-140">This provides a larger area in which to write text.</span></span>  
  
 <span data-ttu-id="415b6-141">**테이블 디자이너 범주**</span><span class="sxs-lookup"><span data-stu-id="415b6-141">**Table Designer Category**</span></span>  
 <span data-ttu-id="415b6-142">확장하면 현재 XML 인덱스의 속성에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-142">When expanded, shows information about the properties of this XML index.</span></span>  
  
 <span data-ttu-id="415b6-143">**채우기 사양**</span><span class="sxs-lookup"><span data-stu-id="415b6-143">**Fill Specification**</span></span>  
 <span data-ttu-id="415b6-144">확장하면 **채우기 비율** 과 **인덱스 패딩**에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-144">When expanded, shows information for **Fill Factor** and **Pad Index**.</span></span>  
  
 <span data-ttu-id="415b6-145">**채우기 비율**</span><span class="sxs-lookup"><span data-stu-id="415b6-145">**Fill Factor**</span></span>  
 <span data-ttu-id="415b6-146">시스템에서 채울 수 있는 인덱스 페이지의 비율을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-146">Specify what percentage of the index page the system can fill.</span></span> <span data-ttu-id="415b6-147">페이지가 가득 찬 경우 새 데이터가 추가되면 시스템에서 페이지를 분할해야 하므로 성능이 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-147">Once a page is full, the system must split the page if new data is added, which impairs performance.</span></span>  
  
-   <span data-ttu-id="415b6-148">값 100을 설정하면 페이지가 가득 차게 되며 스토리지 공간이 최소화되지만 효율성도 최소화됩니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-148">A value of 100 means the pages will be full; this requires the least amount of storage space but is the least efficient.</span></span> <span data-ttu-id="415b6-149">이 설정은 읽기 전용 테이블처럼 데이터를 변경하는 작업이 없을 경우에만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-149">This setting should be used only when there will be no changes to the data, for example, on a read-only table.</span></span>  
  
-   <span data-ttu-id="415b6-150">값이 작을수록 데이터 페이지에 빈 공간이 더 많이 남으므로 인덱스 증가에 따라 데이터 페이지를 분할해야 할 필요성은 줄어들지만</span><span class="sxs-lookup"><span data-stu-id="415b6-150">A lower value leaves more empty space on the data pages, which reduces the need to split data pages as indexes grow.</span></span> <span data-ttu-id="415b6-151">더 많은 스토리지 공간이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-151">However, it requires more storage space.</span></span> <span data-ttu-id="415b6-152">이 설정은 테이블의 데이터를 변경하는 작업이 있는 경우에 더 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-152">This setting is more appropriate when there will be changes to the data in the table.</span></span>  
  
 <span data-ttu-id="415b6-153">**인덱스 패딩**</span><span class="sxs-lookup"><span data-stu-id="415b6-153">**Pad Index**</span></span>  
 <span data-ttu-id="415b6-154">현재 인덱스의 페이지가 **채우기 비율**에 지정된 빈 공간(패딩)과 동일한 비율로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-154">Provide pages in this index the same percentage of empty space (padding) that is specified in **Fill Factor**.</span></span>  
  
 <span data-ttu-id="415b6-155">**비활성화**</span><span class="sxs-lookup"><span data-stu-id="415b6-155">**Is Disabled**</span></span>  
 <span data-ttu-id="415b6-156">현재 인덱스를 비활성화할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-156">Specify whether this index is disabled.</span></span> <span data-ttu-id="415b6-157">비활성화된 인덱스는 검색을 지원하지 않을 뿐더러 테이블에 새 항목이 추가되어도 이러한 인덱스가 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-157">Disabled indexes do not support searches, nor do they get updated when new items are added to the table.</span></span> <span data-ttu-id="415b6-158">인덱스를 비활성화하면 일괄 삽입이나 업데이트 시 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-158">You can improve performance for bulk inserts and updates by disabling an index.</span></span>  
  
 <span data-ttu-id="415b6-159">**페이지 잠금 허용**</span><span class="sxs-lookup"><span data-stu-id="415b6-159">**Page Locks Allowed**</span></span>  
 <span data-ttu-id="415b6-160">현재 인덱스에 대해 페이지 수준의 잠금이 허용되는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-160">Specify whether page-level locking is allowed on this index.</span></span> <span data-ttu-id="415b6-161">페이지 수준의 잠금 허용 여부는 데이터베이스 성능에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-161">Allowing or disallowing page-level locking affects database performance.</span></span>  
  
 <span data-ttu-id="415b6-162">**통계 다시 계산**</span><span class="sxs-lookup"><span data-stu-id="415b6-162">**Re-compute Statistics**</span></span>  
 <span data-ttu-id="415b6-163">인덱스를 만들 때 통계를 새로 컴퓨팅합니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-163">Compute new statistics when the index is created.</span></span> <span data-ttu-id="415b6-164">통계를 다시 계산하면 인덱스 작성 속도가 느려지지만 일반적으로 쿼리 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-164">Re-computing statistics slows the building of indexes but usually improves query performance.</span></span>  
  
 <span data-ttu-id="415b6-165">**행 잠금 허용**</span><span class="sxs-lookup"><span data-stu-id="415b6-165">**Row Locks Allowed**</span></span>  
 <span data-ttu-id="415b6-166">현재 인덱스에 대해 행 수준의 잠금이 허용되는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-166">Specify whether row-level locking is allowed on this index.</span></span> <span data-ttu-id="415b6-167">행 수준의 잠금 허용 여부는 데이터베이스 성능에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="415b6-167">Allowing or disallowing row-level locking affects database performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="415b6-168">참고 항목</span><span class="sxs-lookup"><span data-stu-id="415b6-168">See Also</span></span>  
 [<span data-ttu-id="415b6-169">XML 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="415b6-169">Create XML Indexes</span></span>](../../relational-databases/xml/create-xml-indexes.md)  
  
  
