---
title: 페이지 압축 구현 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- page compression [Database Engine]
- compression [SQL Server], page
ms.assetid: 78c83277-1dbb-4e07-95bd-47b14d2b5cd4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e6edba79d1548d68e60f406d370abd5354a62fcb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659463"
---
# <a name="page-compression-implementation"></a><span data-ttu-id="c92f9-102">페이지 압축 구현</span><span class="sxs-lookup"><span data-stu-id="c92f9-102">Page Compression Implementation</span></span>
  <span data-ttu-id="c92f9-103">이 항목에서는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 이 페이지 압축을 구현하는 방법에 대해 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-103">This topic summarizes how the [!INCLUDE[ssDE](../../includes/ssde-md.md)] implements page compression.</span></span> <span data-ttu-id="c92f9-104">이 요약에서는 사용자의 데이터에 필요한 스토리지 공간을 계획하는 데 도움이 되는 기본 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-104">This summary provides basic information to help you plan the storage space that you need for your data.</span></span>  
  
 <span data-ttu-id="c92f9-105">페이지 압축은 테이블, 테이블 파티션, 인덱스 및 인덱스 파티션에 대한 압축과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-105">Page compression is similar for tables, table partitions, indexes, and index partitions.</span></span> <span data-ttu-id="c92f9-106">테이블에 대한 다음 페이지 압축 설명은 모든 개체 유형에 대한 페이지 압축에 동일하게 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-106">The following description of page compression for a table applies equally to page compression for all object types.</span></span> <span data-ttu-id="c92f9-107">다음 예에서는 문자열을 압축하지만, 접두사 및 사전 압축은 모두 동일한 원칙으로 다른 데이터 형식에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-107">The following examples compress character strings, but both prefix and dictionary compression apply the same principles to other data types.</span></span>  
  
 <span data-ttu-id="c92f9-108">페이지 압축으로 테이블 및 인덱스의 리프 수준을 압축하는 작업은 다음 순서의 세 가지 작업으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-108">Compressing the leaf level of tables and indexes with page compression consists of three operations in the following order:</span></span>  
  
1.  <span data-ttu-id="c92f9-109">행 압축</span><span class="sxs-lookup"><span data-stu-id="c92f9-109">Row compression</span></span>  
  
2.  <span data-ttu-id="c92f9-110">접두사 압축</span><span class="sxs-lookup"><span data-stu-id="c92f9-110">Prefix compression</span></span>  
  
3.  <span data-ttu-id="c92f9-111">사전 압축</span><span class="sxs-lookup"><span data-stu-id="c92f9-111">Dictionary compression</span></span>  
  
 <span data-ttu-id="c92f9-112">페이지 압축을 사용할 경우 인덱스의 리프 수준이 아닌 페이지는 행 압축만 사용하여 압축됩니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-112">When you use page compression, non-leaf-level pages of indexes are compressed by using only row compression.</span></span> <span data-ttu-id="c92f9-113">행 압축에 대한 자세한 내용은 [Row Compression Implementation](../data-compression/row-compression-implementation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c92f9-113">For more information about row compression, see [Row Compression Implementation](../data-compression/row-compression-implementation.md).</span></span>  
  
## <a name="prefix-compression"></a><span data-ttu-id="c92f9-114">접두사 압축</span><span class="sxs-lookup"><span data-stu-id="c92f9-114">Prefix Compression</span></span>  
 <span data-ttu-id="c92f9-115">압축되는 각 페이지에 대해 접두사 압축은 다음 단계를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-115">For each page that is being compressed, prefix compression uses the following steps:</span></span>  
  
1.  <span data-ttu-id="c92f9-116">각 열에서 값은 각 열의 값에 대한 스토리지 공간을 줄이는 데 사용할 수 있는 것으로 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-116">For each column, a value is identified that can be used to reduce the storage space for the values in each column.</span></span>  
  
2.  <span data-ttu-id="c92f9-117">각 열의 접두사 값을 나타내는 행이 CI(압축 정보) 구조에서 페이지 헤더 바로 다음에 만들어지고 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-117">A row that represents the prefix values for each column is created and stored in the compression information (CI) structure that immediately follows the page header.</span></span>  
  
3.  <span data-ttu-id="c92f9-118">열에서 반복되는 접두사 값은 해당 접두사의 참조로 교체됩니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-118">The repeated prefix values in the column are replaced by a reference to the corresponding prefix.</span></span> <span data-ttu-id="c92f9-119">행의 값이 선택한 접두사 값과 정확히 일치하지 않으면 부분 일치로 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-119">If the value in a row does not exactly match the selected prefix value, a partial match can still be indicated.</span></span>  
  
 <span data-ttu-id="c92f9-120">다음 그림에서는 접두사 압축 이전의 간단한 테이블 페이지를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-120">The following illustration shows a sample page of a table before prefix compression.</span></span>  
  
 <span data-ttu-id="c92f9-121">![접두사 압축 이전 페이지](../media/skt-tblcompression1c.gif "접두사 압축 이전 페이지")</span><span class="sxs-lookup"><span data-stu-id="c92f9-121">![Page before prefix compression](../media/skt-tblcompression1c.gif "Page before prefix compression")</span></span>  
  
 <span data-ttu-id="c92f9-122">다음 그림에서는 접두사 압축 다음의 동일한 페이지를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-122">The following illustration shows the same page after prefix compression.</span></span> <span data-ttu-id="c92f9-123">접두사는 헤더로 이동하고 열 값은 접두사의 참조로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-123">The prefix is moved to the header, and the column values are changed to references to the prefix.</span></span>  
  
 <span data-ttu-id="c92f9-124">![접두사 압축 이후 페이지](../media/tblcompression2.gif "접두사 압축 이후 페이지")</span><span class="sxs-lookup"><span data-stu-id="c92f9-124">![Page after prefix compression](../media/tblcompression2.gif "Page after prefix compression")</span></span>  
  
 <span data-ttu-id="c92f9-125">첫 행의 첫 열에서 값 4b는 처음 4자리 접두사(aaab)가 해당 열에 대해 존재함을 나타내며 문자 b도 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-125">In the first column of the first row, the value 4b indicates that the first four characters of the prefix (aaab) are present for that row, and also the character b.</span></span> <span data-ttu-id="c92f9-126">이것은 원래 값인 결과 값 aaabb를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-126">This makes the resultant value aaabb, which is the original value.</span></span>  
  
## <a name="dictionary-compression"></a><span data-ttu-id="c92f9-127">사전 압축</span><span class="sxs-lookup"><span data-stu-id="c92f9-127">Dictionary Compression</span></span>  
 <span data-ttu-id="c92f9-128">접두사 압축이 완료된 후에 사전 압축이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-128">After prefix compression has been completed, dictionary compression is applied.</span></span> <span data-ttu-id="c92f9-129">사전 압축은 페이지에서 반복된 값을 검색하여 CI 영역에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-129">Dictionary compression searches for repeated values anywhere on the page, and stores them in the CI area.</span></span> <span data-ttu-id="c92f9-130">접두사 압축과 달리 사전 압축은 한 개의 열로 제한되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-130">Unlike prefix compression, dictionary compression is not restricted to one column.</span></span> <span data-ttu-id="c92f9-131">사전 압축은 페이지에서 발생하는 반복된 값을 교체할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-131">Dictionary compression can replace repeated values that occur anywhere on a page.</span></span> <span data-ttu-id="c92f9-132">다음 그림에서는 사전 압축 다음의 동일한 페이지를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-132">The following illustration shows the same page after dictionary compression.</span></span>  
  
 <span data-ttu-id="c92f9-133">![사전 압축 이후 페이지](../media/tblcompression3.gif "사전 압축 이후 페이지")</span><span class="sxs-lookup"><span data-stu-id="c92f9-133">![Page after dictionary compression](../media/tblcompression3.gif "Page after dictionary compression")</span></span>  
  
 <span data-ttu-id="c92f9-134">값 4b는 페이지의 다른 열에서 참조되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-134">Note that the value 4b has been referenced from different columns of the page.</span></span>  
  
## <a name="when-page-compression-occurs"></a><span data-ttu-id="c92f9-135">페이지 압축이 발생할 경우</span><span class="sxs-lookup"><span data-stu-id="c92f9-135">When Page Compression Occurs</span></span>  
 <span data-ttu-id="c92f9-136">페이지 압축이 발생한 새 테이블이 만들어지면 압축이 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-136">When a new table is created that has page compression, no compression occurs.</span></span> <span data-ttu-id="c92f9-137">그러나 테이블의 메타데이터는 페이지 압축을 사용해야 한다고 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-137">However, the metadata for the table indicates that page compression should be used.</span></span> <span data-ttu-id="c92f9-138">데이터가 첫 데이터 페이지에 추가되면 데이터의 행이 압축됩니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-138">As data is added to the first data page, data is row-compressed.</span></span> <span data-ttu-id="c92f9-139">페이지가 가득 차지 않았으므로 페이지 압축으로 얻을 수 있는 이점은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-139">Because the page is not full, no benefit is gained from page compression.</span></span> <span data-ttu-id="c92f9-140">페이지가 가득 차면 추가할 다음 행에서 페이지 압축 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-140">When the page is full, the next row to be added initiates the page compression operation.</span></span> <span data-ttu-id="c92f9-141">전체 페이지가 검토됩니다. 즉, 각 열이 접두사 압축에 대해 평가된 후 모든 열이 사전 압축에 대해 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-141">The whole page is reviewed; each column is evaluated for prefix compression, and then all columns are evaluated for dictionary compression.</span></span> <span data-ttu-id="c92f9-142">페이지 압축이 추가 행의 위한 충분한 공간을 페이지에 만들면 행이 추가되고 데이터의 행과 페이지가 모두 압축됩니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-142">If page compression has created enough room on the page for an additional row, the row is added, and the data is both row- and page-compressed.</span></span> <span data-ttu-id="c92f9-143">페이지 압축으로 얻은 공간에서 CI 구조에 필요한 공간을 뺀 값이 크지 않으면 해당 페이지에 대해 페이지 압축이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-143">If the space gained by page compression minus the space that is required for the CI structure is not significant, page compression is not used for that page.</span></span> <span data-ttu-id="c92f9-144">향후 행은 새 페이지에 적합합니다. 만약 적합하지 않을 경우 새 페이지가 테이블에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-144">Future rows either fit onto the new page or, if they do not fit, a new page is added to the table.</span></span> <span data-ttu-id="c92f9-145">첫 페이지와 유사하게 새 페이지는 첫 페이지가 압축되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-145">Similar to the first page, the new page is not at first page-compressed.</span></span>  
  
 <span data-ttu-id="c92f9-146">데이터가 들어 있는 기존 테이블이 페이지 압축으로 변환되면 각 페이지가 다시 작성되고 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-146">When an existing table that contains data is converted to page compression, each page is rebuilt and evaluated.</span></span> <span data-ttu-id="c92f9-147">모든 페이지를 다시 작성하면 테이블, 인덱스 또는 파티션이 다시 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c92f9-147">Rebuilding all the pages causes the rebuilding of the table, index, or partition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c92f9-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c92f9-148">See Also</span></span>  
 <span data-ttu-id="c92f9-149">[데이터 압축](data-compression.md) </span><span class="sxs-lookup"><span data-stu-id="c92f9-149">[Data Compression](data-compression.md) </span></span>  
 [<span data-ttu-id="c92f9-150">행 압축 구현</span><span class="sxs-lookup"><span data-stu-id="c92f9-150">Row Compression Implementation</span></span>](row-compression-implementation.md)  
  
  
