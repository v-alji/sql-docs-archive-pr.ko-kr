---
title: 전체 텍스트 인덱싱 마법사 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextindexingwizard.selecttablecolumns.f1
- sql12.swb.fulltextindexingwizard.welcome.f1
- sql12.swb.fulltextindexingwizard.selectacatalog.f1
- sql12.swb.fulltextindexingwizard.progress.f1
- sql12.swb.fulltextindexingwizard.selectorcreatepopschedules.f1
- sql12.swb.fulltextindexingwizard.selectatableorview.f1
- sql12.swb.fulltextindexingwizard.selectchangetracking.f1
- sql12.swb.fulltextindexingwizard.selectanindex.f1
- sql12.swb.fulltextindexingwizard.summary.f1
helpviewer_keywords:
- Full-Text Indexing Wizard
- full-text search [SQL Server], Full-Text Indexing Wizard
ms.assetid: 3e9d9605-6525-4781-9168-fdaa06db3459
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5ef8a23c4d85cbe47bf6bdb47eb3f45723f1559d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730420"
---
# <a name="use-the-full-text-indexing-wizard"></a><span data-ttu-id="972cd-102">전체 텍스트 인덱싱 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="972cd-102">Use the Full-Text Indexing Wizard</span></span>
  <span data-ttu-id="972cd-103">전체 텍스트 인덱싱 마법사는 전체 텍스트 인덱스를 만드는 과정을 단계별로 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-103">The Full-Text Indexing Wizard walks you through a series of steps designed to help you create a full-text index.</span></span>  
  
#### <a name="to-use-the-full-text-indexing-wizard"></a><span data-ttu-id="972cd-104">전체 텍스트 인덱싱 마법사를 사용하려면</span><span class="sxs-lookup"><span data-stu-id="972cd-104">To use the Full-Text Indexing wizard</span></span>  
  
1.  <span data-ttu-id="972cd-105">개체 탐색기에서 전체 텍스트 인덱스를 만들 대상 테이블을 마우스 오른쪽 단추로 클릭하고 **전체 텍스트 인덱스**를 가리킨 후 **전체 텍스트 인덱스 정의**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-105">In Object Explorer, right-click the table on which you want to create a full-text index, point to **Full-Text index**, and then click **Define Full-Text Index**.</span></span>  
  
     <span data-ttu-id="972cd-106">**고유 인덱스**</span><span class="sxs-lookup"><span data-stu-id="972cd-106">**Unique Index**</span></span>  
     <span data-ttu-id="972cd-107">드롭다운 목록에서 인덱스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-107">Select an index from the drop down list.</span></span> <span data-ttu-id="972cd-108">인덱스는 Null 값을 허용하지 않는 고유한 단일 키 열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-108">The index must be a single-key-column, unique, non-nullable index.</span></span> <span data-ttu-id="972cd-109">전체 텍스트 고유 키에 대해 가장 작은 고유 키 인덱스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-109">Select the smallest unique key index for the full-text unique key.</span></span> <span data-ttu-id="972cd-110">성능 향상을 위해서는 클러스터형 인덱스를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-110">For best performance, a clustered index is recommended.</span></span>  
  
     <span data-ttu-id="972cd-111">**사용 가능한 열**</span><span class="sxs-lookup"><span data-stu-id="972cd-111">**Available Columns**</span></span>  
     <span data-ttu-id="972cd-112">인덱스에 열을 포함하려면 열 이름 옆의 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-112">To include a column in the index, select the check box next to the column name.</span></span> <span data-ttu-id="972cd-113">전체 텍스트 인덱싱에 적합하지 않은 열은 해당 확인란이 비활성화되고 회색으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-113">Columns that are not eligible for full-text indexing appear in grey with their check boxes disabled.</span></span>  
  
     <span data-ttu-id="972cd-114">**단어 분리기 용 언어**</span><span class="sxs-lookup"><span data-stu-id="972cd-114">**Language for Word Breaker**</span></span>  
     <span data-ttu-id="972cd-115">드롭다운 목록에서 언어를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-115">Select a language from the drop-down list.</span></span> <span data-ttu-id="972cd-116">여기에서 선택한 언어는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 인덱스에 올바른 단어 분리기를 식별하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-116">This choice will be used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to identify the correct word breakers for the index.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="972cd-117">에서는 단어 분리기를 사용하여 전체 텍스트 인덱싱된 데이터의 단어 경계를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-117">uses word breakers to identify word boundaries in the full-text indexed data.</span></span>  
  
     <span data-ttu-id="972cd-118">**유형 열**</span><span class="sxs-lookup"><span data-stu-id="972cd-118">**Type Column**</span></span>  
     <span data-ttu-id="972cd-119">전체 텍스트 인덱싱되는 열의 문서 유형을 보관하는 열 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-119">Select the name of the column that holds the document type of column being full-text indexed.</span></span>  
  
     <span data-ttu-id="972cd-120">**유형 열** 은 **사용 가능한 열** 열에 이름이 지정 된 열이 또는 형식인 경우에만 사용할 수 있습니다 `varbinary(max)` `image` .</span><span class="sxs-lookup"><span data-stu-id="972cd-120">The  **Type Column** is only enabled when the column named in the **Available Columns** column is of type `varbinary(max)` or `image`.</span></span>  
  
     <span data-ttu-id="972cd-121">**통계 의미 체계**</span><span class="sxs-lookup"><span data-stu-id="972cd-121">**Statistical Semantics**</span></span>  
     <span data-ttu-id="972cd-122">선택한 열에 대해 의미 체계 인덱싱을 사용하도록 설정할지 여부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-122">Select whether to enable semantic indexing for the selected column.</span></span> <span data-ttu-id="972cd-123">자세한 내용은 [의미 체계 검색&#40;SQL Server&#41;](semantic-search-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="972cd-123">For more information, see [Semantic Search &#40;SQL Server&#41;](semantic-search-sql-server.md).</span></span>  
  
     <span data-ttu-id="972cd-124">**통계 의미 체계** 를 선택하기 전에 **언어**를 선택했으며 선택한 언어에 연결된 의미 체계 언어 모델이 없으면 **통계 의미 체계** 확인란은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-124">If you select a **Language** prior to selecting **Statistical Semantics**, and the selected language does not have an associated Semantic Language Model, then the **Statistical Semantics** checkbox is disabled.</span></span> <span data-ttu-id="972cd-125">**언어** 를 선택하기 전에 **통계 의미 체계**를 선택한 경우 드롭다운 콤보 상자에서 사용할 수 있는 언어가 의미 체계 언어 모델에서 지원하는 언어로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-125">If you select **Statistical Semantics** prior to selecting a **Language**, the languages available in the drop-down combo box will be restricted to those for which there is Semantic Language Model support.</span></span>  
  
2.  <span data-ttu-id="972cd-126">변경 내용 추적 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-126">Select the change tracking options.</span></span>  
  
     <span data-ttu-id="972cd-127">**자동**</span><span class="sxs-lookup"><span data-stu-id="972cd-127">**Automatically**</span></span>  
     <span data-ttu-id="972cd-128">기본 데이터가 변경될 때 자동으로 전체 텍스트 인덱스가 업데이트되도록 하려면 이 라디오 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-128">Select this radio button to have the full-text index updated automatically as changes occur to the underlying data.</span></span>  
  
     <span data-ttu-id="972cd-129">**일일이**</span><span class="sxs-lookup"><span data-stu-id="972cd-129">**Manually**</span></span>  
     <span data-ttu-id="972cd-130">기본 데이터가 변경될 때 자동으로 전체 텍스트 인덱스가 업데이트되지 않도록 하려면 이 라디오 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-130">Select this radio button if you do not want the full-text index to be updated automatically as changes occur to the underlying data.</span></span> <span data-ttu-id="972cd-131">기본 데이터의 변경 내용은 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-131">Changes to the underlying data are maintained.</span></span> <span data-ttu-id="972cd-132">그러나 변경 내용을 전체 텍스트 인덱스에 적용하려면 수동으로 이 프로세스를 시작하거나 일정을 예약해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-132">However, to apply the changes to the full-text index you must start or schedule this process manually.</span></span>  
  
     <span data-ttu-id="972cd-133">**변경 내용 추적 안 함**</span><span class="sxs-lookup"><span data-stu-id="972cd-133">**Do not track changes**</span></span>  
     <span data-ttu-id="972cd-134">기본 데이터의 변경 내용으로 전체 텍스트 인덱스가 업데이트되지 않도록 하려면 이 라디오 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-134">Select this radio button if you do not want the full-text index to be updated with changes to the underlying data.</span></span>  
  
     <span data-ttu-id="972cd-135">**인덱스가 생성될 때 전체 채우기 시작**</span><span class="sxs-lookup"><span data-stu-id="972cd-135">**Start full population when index is created**</span></span>  
     <span data-ttu-id="972cd-136">이 마법사가 성공적으로 완료될 때 전체 채우기를 시작하려면 이 라디오 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-136">Select this radio button to kick off a full population at the successful completion of this wizard.</span></span> <span data-ttu-id="972cd-137">이 과정은 카탈로그에 전체 텍스트 인덱스 구조를 만드는 단계와 이 구조를 전체 텍스트 인덱싱된 데이터로 채우는 단계로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-137">This will consist of creating the full-text index structure in the catalog and populating it with full-text indexed data.</span></span>  
  
3.  <span data-ttu-id="972cd-138">카탈로그, 인덱스 파일 그룹 및 중지 목록을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-138">Select the catalog, index filegroup and stoplist.</span></span>  
  
     <span data-ttu-id="972cd-139">**전체 텍스트 카탈로그 선택**</span><span class="sxs-lookup"><span data-stu-id="972cd-139">**Select full-text catalog**</span></span>  
     <span data-ttu-id="972cd-140">목록에서 전체 텍스트 카탈로그를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-140">Select a full-text catalog from the list.</span></span> <span data-ttu-id="972cd-141">목록에 기본 선택되어 있는 항목이 데이터베이스의 기본 카탈로그가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-141">The default catalog for the database will be the selected item by default in the list.</span></span> <span data-ttu-id="972cd-142">사용 가능한 카탈로그가 없으면 목록이 비활성화되고 **새 카탈로그 만들기** 확인란이 선택된 채로 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-142">If no catalogs are available, the list will be disabled, and the **Create a new catalog** checkbox will be checked and disabled.</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="972cd-143">**새 카탈로그 만들기**</span><span class="sxs-lookup"><span data-stu-id="972cd-143">**Create a new catalog**</span></span>|<span data-ttu-id="972cd-144">전체 텍스트 카탈로그를 새로 만들려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-144">Select to create a new full-text catalog.</span></span>|  
  
     <span data-ttu-id="972cd-145">**이름**</span><span class="sxs-lookup"><span data-stu-id="972cd-145">**Name**</span></span>  
     <span data-ttu-id="972cd-146">새 전체 텍스트 카탈로그에 사용할 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-146">Enter a name for the new full-text catalog.</span></span>  
  
     <span data-ttu-id="972cd-147">**기본 카탈로그로 설정**</span><span class="sxs-lookup"><span data-stu-id="972cd-147">**Set as default catalog**</span></span>  
     <span data-ttu-id="972cd-148">카탈로그를 이 데이터베이스의 기본 카탈로그로 만들려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-148">Select to make the catalog the default for this database.</span></span>  
  
     <span data-ttu-id="972cd-149">**악센트 구분**</span><span class="sxs-lookup"><span data-stu-id="972cd-149">**Accent sensitivity**</span></span>  
     <span data-ttu-id="972cd-150">새 카탈로그의 악센트 구분 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-150">Specify whether the new catalog will be accent-sensitive or accent-insensitive.</span></span> <span data-ttu-id="972cd-151">데이터베이스에서 악센트를 구분하는 경우 **구분**이 기본적으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-151">If the database is accent-sensitive, **Sensitive** will be selected by default.</span></span>  
  
     <span data-ttu-id="972cd-152">**인덱스 파일 그룹 선택**</span><span class="sxs-lookup"><span data-stu-id="972cd-152">**Select index filegroup**</span></span>  
     <span data-ttu-id="972cd-153">전체 텍스트 인덱스를 만들 파일 그룹을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-153">Specify the filegroup on which to create the full-text index.</span></span>  
  
     <span data-ttu-id="972cd-154">다음 값 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-154">Select one of the following values:</span></span>  
  
    |<span data-ttu-id="972cd-155">값</span><span class="sxs-lookup"><span data-stu-id="972cd-155">Value</span></span>|<span data-ttu-id="972cd-156">설명</span><span class="sxs-lookup"><span data-stu-id="972cd-156">Description</span></span>|  
    |-----------|-----------------|  
    |**\<default>**|<span data-ttu-id="972cd-157">테이블이나 뷰가 분할되지 않은 경우 동일한 파일 그룹을 기본 테이블 또는 뷰로 사용하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-157">If the table or view is not partitioned, select to use the same filegroup as the underlying table or view.</span></span> <span data-ttu-id="972cd-158">테이블 또는 뷰가 분할된 경우 기본 파일 그룹이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-158">If the table or view is partitioned, the primary filegroup is used.</span></span>|  
    |<span data-ttu-id="972cd-159">**PRIMARY**</span><span class="sxs-lookup"><span data-stu-id="972cd-159">**PRIMARY**</span></span>|<span data-ttu-id="972cd-160">새 전체 텍스트 인덱스에 주 파일 그룹을 사용하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-160">Select to use the primary filegroup for the new full-text index.</span></span>|  
    |<span data-ttu-id="972cd-161">*사용자가 지정한 기본 파일 그룹*</span><span class="sxs-lookup"><span data-stu-id="972cd-161">*user-specified default filegroup*</span></span>|<span data-ttu-id="972cd-162">사용자 정의 기본 중지 목록이 있으면 이 목록에서 새 전체 텍스트 인덱스에 사용할 파일 그룹의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-162">If a user-defined default stoplist exists, select its name from the list to use that filegroup for the new full-text index.</span></span>|  
  
     <span data-ttu-id="972cd-163">**전체 텍스트 중지 목록 선택**</span><span class="sxs-lookup"><span data-stu-id="972cd-163">**Select full-text stoplist**</span></span>  
     <span data-ttu-id="972cd-164">전체 텍스트 인덱스에 사용할 중지 목록을 지정하거나 중지 목록을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-164">Specify a stoplist to use for the full-text index, or disable stoplist use.</span></span>  
  
     <span data-ttu-id="972cd-165">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 및 이후 버전에서 중지 단어는 데이터베이스에서 중지 목록이라는 개체를 사용하여 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-165">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions, stopwords are managed in databases using objects called stoplists.</span></span> <span data-ttu-id="972cd-166">*중지 목록* 은 전체 텍스트 인덱스와 연결된 경우 해당 인덱스의 전체 텍스트 쿼리에 적용되는 중지 단어 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-166">A *stoplist* is a list of stopwords that, when associated with a full-text index, is applied to full-text queries on that index.</span></span> <span data-ttu-id="972cd-167">자세한 내용은 [전체 텍스트 검색에 사용할 중지 단어와 중지 목록 구성 및 관리](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="972cd-167">For more information, see [Configure and Manage Stopwords and Stoplists for Full-Text Search](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).</span></span>  
  
     <span data-ttu-id="972cd-168">다음 값 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-168">Select one of the following values:</span></span>  
  
    |<span data-ttu-id="972cd-169">값</span><span class="sxs-lookup"><span data-stu-id="972cd-169">Value</span></span>|<span data-ttu-id="972cd-170">설명</span><span class="sxs-lookup"><span data-stu-id="972cd-170">Description</span></span>|  
    |-----------|-----------------|  
    |**\<system>**|<span data-ttu-id="972cd-171">새 전체 텍스트 인덱스에 시스템 중지 목록을 사용하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-171">Select to use the system stoplist on the new full-text index.</span></span> <span data-ttu-id="972cd-172">이것이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-172">This is the default</span></span>|  
    |**\<off>**|<span data-ttu-id="972cd-173">새 전체 텍스트 인덱스에 중지 목록을 사용하지 않으려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-173">Select to disable stoplists for the new full-text index.</span></span>|  
    |<span data-ttu-id="972cd-174">*user-defined-stoplist-name*</span><span class="sxs-lookup"><span data-stu-id="972cd-174">*user-defined-stoplist-name*</span></span>|<span data-ttu-id="972cd-175">이 목록에는 데이터베이스에서 만든 각 사용자 정의 중지 목록의 이름을 표시합니다(있는 경우).</span><span class="sxs-lookup"><span data-stu-id="972cd-175">The list displays the name of each user-defined stoplist, if any, that has been created on the database.</span></span> <span data-ttu-id="972cd-176">새 전체 텍스트 인덱스에 사용할 사용자 정의 중지 목록을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-176">Select any user-defined stoplist to use for the new full-text index.</span></span>|  
  
4.  <span data-ttu-id="972cd-177">선택적으로 채우기 일정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-177">Optionally, define the population schedule.</span></span> <span data-ttu-id="972cd-178">나중에 실행하도록 예약한 경우가 아니면 인덱싱 작업이 바로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-178">Indexing operations will begin immediately unless they have been scheduled for future execution.</span></span> <span data-ttu-id="972cd-179">예약된 시간이 되기 전까지 인덱싱 작업이 실행되지 않더라도 일정은 즉시 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-179">Schedules will be created immediately, although they will not run until their scheduled time.</span></span>  
  
     <span data-ttu-id="972cd-180">**새 테이블 일정**</span><span class="sxs-lookup"><span data-stu-id="972cd-180">**New Table Schedule**</span></span>  
     <span data-ttu-id="972cd-181">테이블의 채우기 일정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-181">Define a population schedule for a table.</span></span>  
  
     <span data-ttu-id="972cd-182">**새 카탈로그 일정**</span><span class="sxs-lookup"><span data-stu-id="972cd-182">**New Catalog Schedule**</span></span>  
     <span data-ttu-id="972cd-183">전체 텍스트 카탈로그의 채우기 일정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-183">Define a population schedule for a full-text catalog.</span></span>  
  
     <span data-ttu-id="972cd-184">**편집**</span><span class="sxs-lookup"><span data-stu-id="972cd-184">**Edit**</span></span>  
     <span data-ttu-id="972cd-185">일정을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-185">Edit a schedule.</span></span>  
  
     <span data-ttu-id="972cd-186">**삭제**</span><span class="sxs-lookup"><span data-stu-id="972cd-186">**Delete**</span></span>  
     <span data-ttu-id="972cd-187">일정을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-187">Delete a schedule.</span></span>  
  
5.  <span data-ttu-id="972cd-188">전체 텍스트 인덱싱 마법사의 진행을 보거나 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-188">View or control the progress of the Full-Text Indexing Wizard.</span></span>  
  
     <span data-ttu-id="972cd-189">**중지**</span><span class="sxs-lookup"><span data-stu-id="972cd-189">**Stop**</span></span>  
     <span data-ttu-id="972cd-190">현재 작업을 중단하고 이 세션 중에는 마법사가 이후의 전체 텍스트 작업을 수행하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-190">Interrupts the current operation and prevents subsequent full-text operations from being performed by the wizard during this session.</span></span>  
  
     <span data-ttu-id="972cd-191">**Report**</span><span class="sxs-lookup"><span data-stu-id="972cd-191">**Report**</span></span>  
     <span data-ttu-id="972cd-192">모든 작업의 실행이 완료되면 이 단추를 클릭하여 수행된 작업에 대한 보고서에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-192">When all of the operations have finished executing, click this button to access a report on the operations performed.</span></span> <span data-ttu-id="972cd-193">보고서를 확인하거나 파일로 인쇄하거나 클립보드에 복사하거나 전자 메일로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="972cd-193">You can view the report, print it to a file, copy it to the clipboard, or e-mail the report.</span></span>  
  
  
