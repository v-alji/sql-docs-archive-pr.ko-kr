---
title: 전체 텍스트 인덱스 대화 상자(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.fulltextindex
ms.assetid: ef45b585-2567-4abe-b421-9fd0994e0146
author: stevestein
ms.author: sstein
ms.openlocfilehash: f98d3bf43707caedd8c9d0a01349f36d5a5bfbcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741504"
---
# <a name="full-text-index-dialog-box-visual-database-tools"></a><span data-ttu-id="199aa-102">전체 텍스트 인덱스 대화 상자(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="199aa-102">Full-Text Index Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="199aa-103">이 대화 상자를 사용하면 전체 텍스트 인덱스를 만들어 데이터베이스 테이블에서 텍스트 기반 열에 대해 전체 텍스트 검색을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-103">This dialog box allows you to create a full-text index, for full-text searches on text-based columns in your database tables.</span></span> <span data-ttu-id="199aa-104">전체 텍스트 인덱스는 일반 인덱스를 기반으로 하므로 먼저 일반 인덱스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-104">A full-text index relies on a regular index, so you must create that first.</span></span> <span data-ttu-id="199aa-105">일반 인덱스는 null이 아닌 단일 열에 대해 작성해야 하며, 값이 큰 열보다 값이 작은 열을 선택하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-105">The regular index must be created on a single, non-null column; it is best to choose a column with small values rather than a column with large ones.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="199aa-106">전체 텍스트 인덱스를 만들려면 우선 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 나 엔터프라이즈 관리자와 같은 외부 도구를 사용하여 데이터베이스의 전체 텍스트 카탈로그를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-106">To create a full-text index, you must first create a full-text catalog for the database using an outside tool, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Enterprise Manager.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="199aa-107">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 일부 버전에서는 전체 텍스트 인덱스 기능을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-107">Full-text index functionality is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="199aa-108">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="199aa-108">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="199aa-109">옵션</span><span class="sxs-lookup"><span data-stu-id="199aa-109">Options</span></span>  
 <span data-ttu-id="199aa-110">**선택한 전체 텍스트 인덱스**</span><span class="sxs-lookup"><span data-stu-id="199aa-110">**Selected Full-Text Index**</span></span>  
 <span data-ttu-id="199aa-111">기존의 전체 텍스트 인덱스를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-111">Lists existing full-text indexes.</span></span> <span data-ttu-id="199aa-112">인덱스를 선택하면 오른쪽 표에 해당 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-112">Select an index to show its properties in the grid to the right.</span></span> <span data-ttu-id="199aa-113">목록이 비어 있는 경우 테이블에 정의된 전체 텍스트 관계가 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-113">If the list is empty, no full-text relationships have been defined for the table.</span></span>  
  
 <span data-ttu-id="199aa-114">**추가**</span><span class="sxs-lookup"><span data-stu-id="199aa-114">**Add**</span></span>  
 <span data-ttu-id="199aa-115">전체 텍스트 인덱스를 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-115">Create a new full-text index.</span></span>  
  
 <span data-ttu-id="199aa-116">**Delete**</span><span class="sxs-lookup"><span data-stu-id="199aa-116">**Delete**</span></span>  
 <span data-ttu-id="199aa-117">**선택한 전체 텍스트 인덱스** 목록에서 선택한 전체 텍스트 인덱스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-117">Delete the full-text index selected in the **Selected Full-Text Index** list.</span></span>  
  
 <span data-ttu-id="199aa-118">**일반 범주**</span><span class="sxs-lookup"><span data-stu-id="199aa-118">**General Category**</span></span>  
 <span data-ttu-id="199aa-119">확장하면 **열** 및 **전체 텍스트 카탈로그 이름**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-119">When expanded, shows **Columns** and **Full-text Catalog Name**.</span></span>  
  
 <span data-ttu-id="199aa-120">**열**</span><span class="sxs-lookup"><span data-stu-id="199aa-120">**Columns**</span></span>  
 <span data-ttu-id="199aa-121">검색 가능한 전체 텍스트 열의 이름 목록을 쉼표로 구분하여 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-121">Displays a comma-separated list of the names of full-text-searchable columns.</span></span> <span data-ttu-id="199aa-122">전체 목록을 보려면 속성 필드의 왼쪽에 있는 줄임표 단추( **...** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-122">To see the complete list, click the ellipsis button (**...**) to the left of the property field.</span></span>  
  
 <span data-ttu-id="199aa-123">**Full-Text Catalog Name**</span><span class="sxs-lookup"><span data-stu-id="199aa-123">**Full-Text Catalog Name**</span></span>  
 <span data-ttu-id="199aa-124">현재 전체 텍스트 인덱스가 저장되어 있는 전체 텍스트 카탈로그의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-124">Displays the name of the full-text catalog on which this full-text index is stored.</span></span> <span data-ttu-id="199aa-125">인덱스를 다른 카탈로그에 저장하려면 카탈로그 이름을 클릭하고 드롭다운 목록에서 다른 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-125">To store the index on a different catalog, click the catalog name and choose another from the drop-down list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="199aa-126">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 나 엔터프라이즈 관리자 같은 외부 도구를 사용하여 카탈로그를 먼저 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-126">The catalog must be created first in an outside tool, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Enterprise Manager.</span></span>  
  
 <span data-ttu-id="199aa-127">**ID 범주**</span><span class="sxs-lookup"><span data-stu-id="199aa-127">**Identity Category**</span></span>  
 <span data-ttu-id="199aa-128">확장하면 현재 인덱스의 이름 필드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-128">When expanded, shows the name field for this index.</span></span>  
  
 <span data-ttu-id="199aa-129">**이름**</span><span class="sxs-lookup"><span data-stu-id="199aa-129">**Name**</span></span>  
 <span data-ttu-id="199aa-130">현재 전체 텍스트 인덱스에 대해 자동으로 지정된 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-130">Displays the system-specified name for this full-text index.</span></span>  
  
 <span data-ttu-id="199aa-131">**테이블 디자이너 범주**</span><span class="sxs-lookup"><span data-stu-id="199aa-131">**Table Designer Category**</span></span>  
 <span data-ttu-id="199aa-132">확장하면 인덱스 수행 방식을 지정하는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-132">When expanded, shows properties that dictate how the index performs.</span></span>  
  
 <span data-ttu-id="199aa-133">**활성**</span><span class="sxs-lookup"><span data-stu-id="199aa-133">**Active**</span></span>  
 <span data-ttu-id="199aa-134">현재 전체 텍스트 인덱스를 사용하여 전체 텍스트 검색을 지금 수행할 수 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-134">Indicates whether you can currently perform a full-text search using this full-text index.</span></span>  
  
 <span data-ttu-id="199aa-135">**추적 설정 변경**</span><span class="sxs-lookup"><span data-stu-id="199aa-135">**Change Tracking Setting**</span></span>  
 <span data-ttu-id="199aa-136">수동, 자동 또는 해제와 같이 이 인덱스의 변경 내용 추적 상태에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-136">Describes the status of change tracking for this index: Manual, Auto, or Off.</span></span>  
  
 <span data-ttu-id="199aa-137">**탐색 완료**</span><span class="sxs-lookup"><span data-stu-id="199aa-137">**Crawl Completed**</span></span>  
 <span data-ttu-id="199aa-138">가장 최근의 탐색이 완료되었는지 여부를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-138">Shows whether the most recent crawl has been completed.</span></span> <span data-ttu-id="199aa-139">이 속성 값이 No이면 탐색이 아직 진행 중임을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-139">If this property value is No, a crawl is currently in progress.</span></span>  
  
 <span data-ttu-id="199aa-140">**현재 또는 마지막 탐색의 종료 날짜 및 시간**</span><span class="sxs-lookup"><span data-stu-id="199aa-140">**End Date And Time Of Current Or Last Crawl**</span></span>  
 <span data-ttu-id="199aa-141">가장 최근 탐색이 종료된 날짜와 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-141">Displays the date and time that the most recent crawl ended.</span></span>  
  
 <span data-ttu-id="199aa-142">**현재 또는 마지막 탐색의 오류**</span><span class="sxs-lookup"><span data-stu-id="199aa-142">**Errors In Current Or Last Crawl**</span></span>  
 <span data-ttu-id="199aa-143">현재 또는 가장 최근 탐색에서 발생한 오류 개수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-143">Displays the number of errors in current or most recent crawl.</span></span>  
  
 <span data-ttu-id="199aa-144">**인덱스 버전**</span><span class="sxs-lookup"><span data-stu-id="199aa-144">**Index Version**</span></span>  
 <span data-ttu-id="199aa-145">탐색을 시작할 당시 테이블의 스키마 버전을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-145">Displays the schema version of table at time the crawl started.</span></span>  
  
 <span data-ttu-id="199aa-146">**현재 또는 마지막 탐색의 행**</span><span class="sxs-lookup"><span data-stu-id="199aa-146">**Rows In Current Or Last Crawl**</span></span>  
 <span data-ttu-id="199aa-147">현재 또는 가장 최근 탐색에서 업데이트된 행 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-147">Displays the number of rows updated in the current or most recent crawl.</span></span>  
  
 <span data-ttu-id="199aa-148">**현재 또는 마지막 탐색의 시작 날짜 및 시간**</span><span class="sxs-lookup"><span data-stu-id="199aa-148">**Start Date And Time Of Current Or Last Crawl**</span></span>  
 <span data-ttu-id="199aa-149">현재 또는 가장 최근 탐색을 시작한 날짜와 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-149">Displays the date and time that the current or most recent crawl started.</span></span>  
  
 <span data-ttu-id="199aa-150">**다음 탐색에 대한 타임스탬프**</span><span class="sxs-lookup"><span data-stu-id="199aa-150">**Time Stamp For Next Crawl**</span></span>  
 <span data-ttu-id="199aa-151">다음 탐색을 시작할 날짜와 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-151">Displays the date and time that the next crawl will start.</span></span>  
  
 <span data-ttu-id="199aa-152">**현재 또는 마지막 탐색의 형식**</span><span class="sxs-lookup"><span data-stu-id="199aa-152">**Type Of Current Or Last Crawl**</span></span>  
 <span data-ttu-id="199aa-153">최대, 증분, 업데이트 또는 자동 전파와 같이 현재 또는 가장 최근 탐색의 형식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-153">Displays the type of the current or most recent crawl: Full, Incremental, Update, or Auto Propagation.</span></span>  
  
 <span data-ttu-id="199aa-154">**고유 인덱스 이름**</span><span class="sxs-lookup"><span data-stu-id="199aa-154">**Unique Index Name**</span></span>  
 <span data-ttu-id="199aa-155">현재 데이터베이스에서 고유한 단일 열 인덱스가 있는 열의 이름에 대한 전체 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-155">Displays a list of all of the names of columns in this database that have unique single-column indexes.</span></span> <span data-ttu-id="199aa-156">이러한 열은 전체 텍스트 인덱스를 만드는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="199aa-156">These columns can be used to create a full-text index.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="199aa-157">참고 항목</span><span class="sxs-lookup"><span data-stu-id="199aa-157">See Also</span></span>  
 <span data-ttu-id="199aa-158">[전체 텍스트 인덱싱 마법사 사용](../../relational-databases/search/use-the-full-text-indexing-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="199aa-158">[Use the Full-Text Indexing Wizard](../../relational-databases/search/use-the-full-text-indexing-wizard.md) </span></span>  
 [<span data-ttu-id="199aa-159">CREATE FULLTEXT INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="199aa-159">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-index-transact-sql)  
  
  
