---
title: 전체 텍스트 검색 시작 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text catalogs [SQL Server], creating
- full-text indexes [SQL Server], creating
- full-text search [SQL Server], about
- full-text search [SQL Server], setting up
ms.assetid: 1fa628ba-0ee4-4d8f-b086-c4e52962ca4a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: eec806bffba330ac3ab995c1b3bfd3504589ecfd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730423"
---
# <a name="get-started-with-full-text-search"></a><span data-ttu-id="6597a-102">전체 텍스트 검색 시작</span><span class="sxs-lookup"><span data-stu-id="6597a-102">Get Started with Full-Text Search</span></span>
  <span data-ttu-id="6597a-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 데이터베이스는 기본적으로 전체 텍스트를 사용하도록 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-103">Databases in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are full-text enabled by default.</span></span> <span data-ttu-id="6597a-104">하지만 테이블에서 전체 텍스트 인덱스를 사용하려면 먼저 전체 텍스트 엔진을 사용하여 액세스하려는 테이블 열에 전체 텍스트 인덱싱 기능을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-104">However, to use a full-text index on a table, you must set up full-text indexing capability on the columns of the tables that you want to access using the Full-Text Engine.</span></span>  
  
##  <a name="configuring-a-database-for-full-text-search"></a><a name="configure"></a><span data-ttu-id="6597a-105">전체 텍스트 검색을 위한 데이터베이스 구성</span><span class="sxs-lookup"><span data-stu-id="6597a-105">Configuring a Database for Full-Text Search</span></span>  
 <span data-ttu-id="6597a-106">모든 시나리오에서 데이터베이스 관리자는 다음과 같은 기본 단계를 수행하여 전체 텍스트 검색용 데이터베이스에서 테이블 열을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-106">For any scenario, a database administrator performs the following basic steps to configure table columns in a database for full-text search:</span></span>  
  
1.  <span data-ttu-id="6597a-107">전체 텍스트 카탈로그를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-107">Create a full-text catalog.</span></span>  
  
2.  <span data-ttu-id="6597a-108">검색할 각 테이블에서 다음을 수행하여 전체 텍스트 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-108">On each table that you want to search, create a full-text index by:</span></span>  
  
    1.  <span data-ttu-id="6597a-109">전체 텍스트 인덱스에 포함할 각 텍스트 열을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-109">Identify each text columns that you want to include in the full-text index.</span></span>  
  
    2.  <span data-ttu-id="6597a-110">지정 된 열에 이진 데이터 (또는 데이터)로 저장 된 문서가 포함 되어 있으면 `varbinary(max)` `image` 인덱싱되는 열에 있는 각 문서의 유형을 식별 하는 테이블 열 ( *유형 열*)을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-110">If a given column contains documents stored as binary data (`varbinary(max)`, or `image` data), you must specify a table column (the *type column*) that identifies the type of each document in the column being indexed.</span></span>  
  
    3.  <span data-ttu-id="6597a-111">전체 텍스트 검색에서 열에 있는 문서에 사용할 언어를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-111">Specify the language that you want full-text search to use on the documents in the column.</span></span>  
  
    4.  <span data-ttu-id="6597a-112">기본 테이블과 이 테이블에 속한 열의 변경 내용을 추적하기 위해 전체 텍스트 인덱스에 사용할 변경 내용 추적 메커니즘을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-112">Choose the change-tracking mechanism that you want to use on the full-text index to track changes in the base table and its columns.</span></span>  
  
 <span data-ttu-id="6597a-113">전체 텍스트 검색은 단어 분기기, 형태소 분석기, 중지 단어가 포함된 중지 목록, 동의어 사전 파일 등의 *언어 구성 요소*를 사용하여 여러 언어를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-113">Full-text search supports multiple languages through the use of the following *linguistic components*: word breakers and stemmers, stoplists that contain stopwords (also known as noise words), and thesaurus files.</span></span> <span data-ttu-id="6597a-114">동의어 사전 파일과 경우에 따라서는 중지 목록은 데이터베이스 관리자의 구성이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-114">Thesaurus files and, in some cases, stoplists require configuration by a database administrator.</span></span> <span data-ttu-id="6597a-115">지정된 동의어 사전 파일은 해당 언어를 사용하는 모든 전체 텍스트 인덱스를 지원하고 지정된 중지 목록은 전체 텍스트 인덱스에 원하는 만큼 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-115">A given thesaurus file supports all full-text indexes that use the corresponding language, and a given stoplist can be associated with as many full-text indexes as you want.</span></span>  
  
##  <a name="setting-up-a-full-text-catalog-and-index"></a><a name="setup"></a><span data-ttu-id="6597a-116">전체 텍스트 카탈로그 및 인덱스 설정</span><span class="sxs-lookup"><span data-stu-id="6597a-116">Setting Up a Full-Text Catalog and Index</span></span>  
 <span data-ttu-id="6597a-117">이를 위한 기본 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-117">This involves the following basic steps:</span></span>  
  
1.  <span data-ttu-id="6597a-118">전체 텍스트 인덱스를 저장할 전체 텍스트 카탈로그를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-118">Create a full-text catalog to store full-text indexes.</span></span>  
  
     <span data-ttu-id="6597a-119">각 전체 텍스트 인덱스는 전체 텍스트 카탈로그에 속해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-119">Each full-text index must belong to a full-text catalog.</span></span> <span data-ttu-id="6597a-120">각 전체 텍스트 인덱스에 대해 별도의 텍스트 카탈로그를 만들거나 지정된 카탈로그에 여러 전체 텍스트 인덱스를 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-120">You can create a separate text catalog for each full-text index, or you can associate multiple full-text indexes with a given catalog.</span></span> <span data-ttu-id="6597a-121">전체 텍스트 카탈로그는 가상 개체이며 어떠한 파일 그룹에도 속하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-121">A full-text catalog is a virtual object and does not belong to any filegroup.</span></span> <span data-ttu-id="6597a-122">이 카탈로그는 전체 텍스트 인덱스 그룹을 나타내는 논리적 개념입니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-122">The catalog is a logical concept that refers to a group of full-text indexes.</span></span>  
  
2.  <span data-ttu-id="6597a-123">테이블 또는 인덱싱된 뷰에서 전체 텍스트 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-123">Create a full-text index on the table or indexed view.</span></span>  
  
     <span data-ttu-id="6597a-124">전체 텍스트 인덱스는 전체 텍스트 엔진에서 작성 및 유지 관리하는 특수한 유형의 토큰 기반 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-124">A full-text index is a special type of token-based functional index that is built and maintained by the Full-Text Engine.</span></span> <span data-ttu-id="6597a-125">테이블 또는 뷰에 대한 전체 텍스트 검색을 만들려면 해당 테이블이나 뷰에 Null이 아닌 고유한 단일 열이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-125">To create full-text search on a table or view, it must have a unique, single-column, non-nullable index.</span></span> <span data-ttu-id="6597a-126">테이블의 각 행을 압축할 수 있는 고유 키에 매핑하려면 전체 텍스트 엔진에 이 고유 인덱스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-126">The Full-Text Engine requires this unique index to map each row in the table to a unique, compressible key.</span></span> <span data-ttu-id="6597a-127">전체 텍스트 인덱스는 `char`, `varchar`, `nchar`, `nvarchar`, `text`, `ntext`, `image`, `xml`, `varbinary` 및 `varbinary(max)` 열을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-127">A full-text index can include `char`, `varchar`, `nchar`, `nvarchar`, `text`, `ntext`, `image`, `xml`, `varbinary`, and `varbinary(max)` columns.</span></span> <span data-ttu-id="6597a-128">자세한 내용은 [전체 텍스트 인덱스 만들기 및 관리](create-and-manage-full-text-indexes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6597a-128">For more information, see [Create and Manage Full-Text Indexes](create-and-manage-full-text-indexes.md).</span></span>  
  
 <span data-ttu-id="6597a-129">전체 텍스트 인덱스를 만드는 방법을 알아보기 전에 먼저 전체 텍스트 인덱스와 일반 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인덱스의 차이점을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-129">Before learning about creating full-text indexes, it is important to consider how they differ from regular [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] indexes.</span></span> <span data-ttu-id="6597a-130">다음 표에는 차이점이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-130">The following table lists the differences.</span></span>  
  
|<span data-ttu-id="6597a-131">전체 텍스트 인덱스</span><span class="sxs-lookup"><span data-stu-id="6597a-131">Full-text indexes</span></span>|<span data-ttu-id="6597a-132">일반 SQL Server 인덱스</span><span class="sxs-lookup"><span data-stu-id="6597a-132">Regular SQL Server indexes</span></span>|  
|------------------------|--------------------------------|  
|<span data-ttu-id="6597a-133">테이블당 한 개의 전체 텍스트 인덱스만 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-133">Only one full-text index allowed per table.</span></span>|<span data-ttu-id="6597a-134">테이블당 여러 개의 일반 인덱스를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-134">Several regular indexes allowed per table.</span></span>|  
|<span data-ttu-id="6597a-135">전체 텍스트 인덱스에 데이터를 추가하는 *채우기*는 일정 예약 또는 특정 요청을 통해 수행할 수 있으며 새 데이터를 추가하면 자동으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-135">The addition of data to full-text indexes, called a *population*, can be requested through either a schedule or a specific request, or can occur automatically with the addition of new data.</span></span>|<span data-ttu-id="6597a-136">인덱스의 기초가 되는 데이터가 삽입, 업데이트 또는 삭제되면 인덱스도 자동으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-136">Updated automatically when the data upon which they are based is inserted, updated, or deleted.</span></span>|  
|<span data-ttu-id="6597a-137">같은 데이터베이스 내에서 하나 이상의 전체 텍스트 카탈로그로 그룹화됩니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-137">Grouped within the same database into one or more full-text catalogs.</span></span>|<span data-ttu-id="6597a-138">그룹화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-138">Not grouped.</span></span>|  
  
  
##  <a name="choosing-options-for-a-full-text-index"></a><a name="options"></a><span data-ttu-id="6597a-139">전체 텍스트 인덱스에 대 한 옵션 선택</span><span class="sxs-lookup"><span data-stu-id="6597a-139">Choosing Options for a Full-Text Index</span></span>  
 <span data-ttu-id="6597a-140">이 섹션에서는 다음에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-140">This section covers the following:</span></span>  
  
-   <span data-ttu-id="6597a-141">열 언어 선택</span><span class="sxs-lookup"><span data-stu-id="6597a-141">Choosing the column language</span></span>  
  
-   <span data-ttu-id="6597a-142">전체 텍스트 인덱스의 파일 그룹 선택</span><span class="sxs-lookup"><span data-stu-id="6597a-142">Choosing a filegroup for a full-text index</span></span>  
  
-   <span data-ttu-id="6597a-143">전체 텍스트 카탈로그에 전체 텍스트 인덱스 할당</span><span class="sxs-lookup"><span data-stu-id="6597a-143">Assigning the full-text index to a full-text catalog</span></span>  
  
-   <span data-ttu-id="6597a-144">전체 텍스트 인덱스와 중지 목록 연결</span><span class="sxs-lookup"><span data-stu-id="6597a-144">Associating a stoplist with the full-text index</span></span>  
  
-   <span data-ttu-id="6597a-145">전체 텍스트 인덱스 업데이트</span><span class="sxs-lookup"><span data-stu-id="6597a-145">Updating a full-text index</span></span>  
  
### <a name="choosing-the-column-language"></a><span data-ttu-id="6597a-146">열 언어 선택</span><span class="sxs-lookup"><span data-stu-id="6597a-146">Choosing the Column Language</span></span>  
 <span data-ttu-id="6597a-147">열 언어를 선택할 때 고려할 사항은 [전체 텍스트 인덱스 생성 시 언어 선택](choose-a-language-when-creating-a-full-text-index.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6597a-147">For information about things to consider when you are choosing the column language, see [Choose a Language When Creating a Full-Text Index](choose-a-language-when-creating-a-full-text-index.md).</span></span>  
  
### <a name="choosing-a-filegroup-for-a-full-text-index"></a><span data-ttu-id="6597a-148">전체 텍스트 인덱스의 파일 그룹 선택</span><span class="sxs-lookup"><span data-stu-id="6597a-148">Choosing a Filegroup for a Full-Text Index</span></span>  
 <span data-ttu-id="6597a-149">전체 텍스트 인덱스 구축은 I/O 사용량이 많은 과정입니다. 크게 보았을 때 이는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 데이터를 읽은 후 필터링된 데이터를 전체 텍스트 인덱스로 전파하는 과정으로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-149">The process of building a full-text index is fairly I/O intensive (on a high level, it consists of reading data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and then propagating the filtered data to the full-text index).</span></span> <span data-ttu-id="6597a-150">I/O 성능을 극대화하는 데 가장 적합한 데이터베이스 파일 그룹이나 다른 볼륨의 다른 파일 그룹에서 전체 텍스트 인덱스를 찾아보는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-150">As a best practice, locate a full-text index in the database filegroup that is best for maximizing I/O performance or locate the full-text indexes in a different filegroup on another volume.</span></span>  
  
 <span data-ttu-id="6597a-151">관리 용이성이 중요한 경우 테이블 데이터와 이에 관련된 모든 전체 텍스트 카탈로그를 동일한 파일 그룹에 저장하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-151">When ease of management is important to you, we recommend that you store table data and any affiliated full-text catalogs in the same filegroup.</span></span> <span data-ttu-id="6597a-152">성능상의 이유로 I/O 병렬 처리를 극대화하기 위해 테이블 데이터와 전체 텍스트 인덱스를 서로 다른 볼륨에 있는 별개의 파일 그룹에 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-152">Sometimes, for performance reasons, you might want to have the table data and the full-text index in different filegroups that are stored on different volumes to maximize I/O parallelism.</span></span>  
  
  
### <a name="assigning-the-full-text-index-to-a-full-text-catalog"></a><span data-ttu-id="6597a-153">전체 텍스트 카탈로그에 전체 텍스트 인덱스 할당</span><span class="sxs-lookup"><span data-stu-id="6597a-153">Assigning the Full-Text Index to a Full-Text Catalog</span></span>  
 <span data-ttu-id="6597a-154">테이블의 전체 텍스트 인덱스를 전체 텍스트 카탈로그에 배치할 계획을 세워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-154">It is important to plan the placement of full-text indexes for tables in full-text catalogs.</span></span>  
  
 <span data-ttu-id="6597a-155">동일한 전체 텍스트 카탈로그 내에서 변경 내용이 적거나 많은 테이블 또는 특정 시간에 자주 변경되는 테이블과 같이 업데이트 특징이 동일한 테이블을 함께 연결하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-155">We recommend associating tables with the same update characteristics (such as small number of changes versus large number of changes, or tables that change frequently during a particular time of day) together under the same full-text catalog.</span></span> <span data-ttu-id="6597a-156">전체 텍스트 카탈로그 채우기 일정을 세우면 전체 텍스트 인덱스는 데이터베이스 작업이 많을 때 데이터베이스 서버의 리소스 사용에 부정적인 영향을 주지 않고 테이블과 동기화 상태를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-156">By setting up full-text catalog population schedules, full-text indexes stay synchronous with the tables without adversely affecting the resource usage of the database server during periods of high database activity.</span></span>  
  
 <span data-ttu-id="6597a-157">전체 텍스트 카탈로그에 테이블을 할당할 때는 다음 지침을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="6597a-157">When you assign a table to a full-text catalog, consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="6597a-158">항상 전체 텍스트 고유 키에 사용 가능한 가장 작은 고유 인덱스를 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="6597a-158">Always select the smallest unique index available for your full-text unique key.</span></span> <span data-ttu-id="6597a-159">4 바이트의 정수 기반 인덱스가 적합 합니다. 이렇게 하면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 파일 시스템에서 Search 서비스에 필요한 리소스가 상당히 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-159">(A 4-byte, integer-based index is optimal.) This reduces the resources required by [!INCLUDE[msCoName](../../includes/msconame-md.md)] Search service in the file system significantly.</span></span> <span data-ttu-id="6597a-160">기본 키가 100바이트 이상이면 테이블에서 다른 고유 인덱스를 선택하거나 다른 고유 인덱스를 만들어 전체 텍스트 고유 키로 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="6597a-160">If the primary key is large (over 100 bytes), consider choosing another unique index in the table (or creating another unique index) as the full-text unique key.</span></span> <span data-ttu-id="6597a-161">반대로 전체 텍스트 고유 키의 크기가 허용되는 최대 크기인 900바이트를 초과하면 전체 텍스트 채우기를 계속할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-161">Otherwise, if the full-text unique key size exceeds the maximum size allowed (900 bytes), full-text population will not be able to proceed.</span></span>  
  
-   <span data-ttu-id="6597a-162">수백 만 개의 행을 가진 테이블의 인덱스를 만들 때는 테이블을 자체의 전체 텍스트 카탈로그에 할당하십시오.</span><span class="sxs-lookup"><span data-stu-id="6597a-162">If you are indexing a table that has millions of rows, assign the table to its own full-text catalog.</span></span>  
  
-   <span data-ttu-id="6597a-163">전체 행 수뿐만 아니라 전체 텍스트 인덱싱되는 테이블에서 변경되는 양도 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-163">Consider the amount of changes occurring in the tables being full-text indexed, as well as the total number of rows.</span></span> <span data-ttu-id="6597a-164">변경되는 행 수와 마지막 전체 텍스트 채우기에서 나타난 테이블 행 수가 수백 만 개이면 테이블을 자체의 전체 텍스트 카탈로그에 할당하십시오.</span><span class="sxs-lookup"><span data-stu-id="6597a-164">If the total number of rows being changed, together with the numbers of rows in the table present during the last full-text population, represents millions of rows, assign the table to its own full-text catalog.</span></span>  
  
  
### <a name="associating-a-stoplist-with-the-full-text-index"></a><span data-ttu-id="6597a-165">전체 텍스트 인덱스와 중지 목록 연결</span><span class="sxs-lookup"><span data-stu-id="6597a-165">Associating a Stoplist with the Full-Text Index</span></span>  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]<span data-ttu-id="6597a-166">부터 중지 목록이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-166">introduces stoplists.</span></span> <span data-ttu-id="6597a-167">*중지 목록* 이란 의미 없는 단어라고도 하는 중지 단어의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-167">A *stoplist* is a list of stopwords, also known as noise words.</span></span> <span data-ttu-id="6597a-168">중지 목록은 각 전체 텍스트 인덱스와 연결되며, 중지 목록의 단어는 전체 텍스트 인덱스의 전체 텍스트 쿼리에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-168">A stoplist is associated with each full-text index, and the words in that stoplist are applied to full-text queries on that index.</span></span> <span data-ttu-id="6597a-169">기본적으로 시스템 중지 목록은 새로운 전체 텍스트 인덱스와 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-169">By default, the system stoplist is associated with a new full-text index.</span></span> <span data-ttu-id="6597a-170">그러나 고유한 중지 목록을 직접 만들어 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-170">However, you can create and use your own stoplist instead.</span></span> <span data-ttu-id="6597a-171">자세한 내용은 [전체 텍스트 검색에 사용할 중지 단어와 중지 목록 구성 및 관리](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6597a-171">For more information, see [Configure and Manage Stopwords and Stoplists for Full-Text Search](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).</span></span>  
  
 <span data-ttu-id="6597a-172">예를 들어 다음 [전체 텍스트 중지 목록 만들기](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문은 시스템 중지 목록에서 복사 하 여 myStoplist3 라는 새 전체 텍스트 중지 목록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-172">For example, the following [CREATE FULLTEXT STOPLIST](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement creates a new full-text stoplist named myStoplist3 by copying from the system stoplist:</span></span>  
  
```  
CREATE FULLTEXT STOPLIST myStoplist FROM SYSTEM STOPLIST;  
GO  
```  
  
 <span data-ttu-id="6597a-173">다음 [변경 전체 텍스트 중지 목록](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql) 에서는 [!INCLUDE[tsql](../../../includes/tsql-md.md)] mystoplist 목록 이라는 중지 목록을 변경 하 고, 먼저 스페인어에 대해, 프랑스어의 경우 ' en ' 이라는 단어를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-173">The following [ALTER FULLTEXT STOPLIST](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement alters a stoplist named myStoplist, adding the word 'en', first for Spanish and then for French:</span></span>  
  
```  
ALTER FULLTEXT STOPLIST MyStoplist ADD 'en' LANGUAGE 'Spanish';  
ALTER FULLTEXT STOPLIST MyStoplist ADD 'en' LANGUAGE 'French';  
GO  
```  
  
  
### <a name="updating-a-full-text-index"></a><span data-ttu-id="6597a-174">전체 텍스트 인덱스 업데이트</span><span class="sxs-lookup"><span data-stu-id="6597a-174">Updating a Full-Text Index</span></span>  
 <span data-ttu-id="6597a-175">일반 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인덱스처럼 전체 텍스트 인덱스는 연결된 테이블의 데이터가 수정될 때 자동으로 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-175">Like regular [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] indexes, full-text indexes can be automatically updated as data is modified in the associated tables.</span></span> <span data-ttu-id="6597a-176">기본 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-176">This is the default behavior.</span></span> <span data-ttu-id="6597a-177">또는 전체 텍스트 인덱스를 수동으로 업데이트하거나 예약된 간격으로 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-177">Alternatively, you can keep your full-text indexes up-to-date manually or at specified scheduled intervals.</span></span> <span data-ttu-id="6597a-178">전체 텍스트 인덱스를 채우는 작업은 시간이 오래 걸리고 리소스가 많이 사용될 수 있으므로 인덱스 업데이트는 일반적으로 백그라운드에서 실행되는 비동기 프로세스로 수행되며 기본 테이블을 수정한 다음 전체 텍스트를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-178">Populating a full-text index can be time-consuming and resource-intensive, therefore, index updating is usually performed as an asynchronous process that runs in the background and keeps the full-text index up to date after modifications in the base table.</span></span> <span data-ttu-id="6597a-179">기본 테이블을 변경할 때마다 전체 텍스트 인덱스를 업데이트하면 리소스 사용량이 많아질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-179">Updating a full-text index immediately after each change in the base table can be resource-intensive.</span></span> <span data-ttu-id="6597a-180">따라서 업데이트/삽입/삭제 빈도가 높을 경우 쿼리 성능이 약간 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-180">Therefore, if you have a very high update/insert/delete rate, you might experience some degradation in query performance.</span></span> <span data-ttu-id="6597a-181">이러한 경우에는 리소스 때문에 쿼리 실행에 차질을 빚기보다는 일정한 간격을 두고 여러 변경 내용을 한꺼번에 추적하여 텍스트 인덱스를 업데이트하도록 수동으로 변경 내용 추적 업데이트 일정을 세우는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-181">If this occurs, consider scheduling manual change tracking updates to keep up with the numerous changes from time to time, rather than competing with queries for resources.</span></span>  
  
 <span data-ttu-id="6597a-182">채우기 상태를 모니터링하려면 FULLTEXTCATALOGPROPERTY 또는 OBJECTPROPERTYEX 함수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-182">To monitor the population status, use either the FULLTEXTCATALOGPROPERTY or OBJECTPROPERTYEX functions.</span></span> <span data-ttu-id="6597a-183">카탈로그 채우기 상태를 확인하려면 다음 문을 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="6597a-183">To get the catalog population status, run the following statement:</span></span>  
  
```  
SELECT FULLTEXTCATALOGPROPERTY('AdvWksDocFTCat', 'Populatestatus');  
```  
  
 <span data-ttu-id="6597a-184">일반적으로 전체 채우기가 진행 중이면 반환 결과는 1입니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-184">Typically, if a full population is in progress, the result returned is 1.</span></span>  
  
  
##  <a name="example-setting-up-full-text-search"></a><a name="example"></a><span data-ttu-id="6597a-185">예: 전체 텍스트 검색 설정</span><span class="sxs-lookup"><span data-stu-id="6597a-185">Example: Setting Up Full-Text Search</span></span>  
 <span data-ttu-id="6597a-186">다음 두 부분으로 구성된 예에서는 AdventureWorks 데이터베이스에 `AdvWksDocFTCat`라는 전체 텍스트 카탈로그를 만든 다음 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]의 `Document` 테이블에 전체 텍스트 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-186">The following two-part example creates a full-text catalog named `AdvWksDocFTCat` on the AdventureWorks database and then creates a full-text index on the `Document` table in [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span> <span data-ttu-id="6597a-187">이 문은 설치할 때 지정한 기본 디렉터리에 전체 텍스트 카탈로그를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-187">This statement creates the full-text catalog in the default directory specified during setup.</span></span> <span data-ttu-id="6597a-188">`AdvWksDocFTCat` 폴더는 기본 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-188">The folder named `AdvWksDocFTCat` is in the default directory.</span></span>  
  
1.  <span data-ttu-id="6597a-189">이 예제에서는 `AdvWksDocFTCat`라는 전체 텍스트 카탈로그를 만들기 위해 [CREATE FULLTEXT CATALOG](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-189">To create a full-text catalog named `AdvWksDocFTCat`, the example uses a [CREATE FULLTEXT CATALOG](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) statement:</span></span>  
  
    ```  
    USE AdventureWorks;  
    GO  
    CREATE FULLTEXT CATALOG AdvWksDocFTCat;  
    ```  
  
2.  <span data-ttu-id="6597a-190">Document 테이블에 대한 전체 텍스트 인덱스를 만들려면 먼저 이 테이블에 Null을 허용하지 않는 고유한 단일 열 인덱스가 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-190">Before you can create a full-text index on the Document table, ensure that the table has a unique, single-column, non-nullable index.</span></span> <span data-ttu-id="6597a-191">다음 [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql) 문에서는 Document 테이블의 DocumentID 열에 대한 고유 인덱스 `ui_ukDoc`를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-191">The following [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql) statement creates a unique index, `ui_ukDoc`, on the DocumentID column of the Document table:</span></span>  
  
    ```  
    CREATE UNIQUE INDEX ui_ukDoc ON Production.Document(DocumentID);  
    ```  
  
3.  <span data-ttu-id="6597a-192">고유 키를 만든 후 다음 `Document` CREATE FULLTEXT INDEX [문을 사용하여](/sql/t-sql/statements/create-fulltext-index-transact-sql) 테이블에 대한 전체 텍스트 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-192">After you have a unique key, you can create a full-text index on the `Document` table by using the following [CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) statement.</span></span>  
  
    ```  
    CREATE FULLTEXT INDEX ON Production.Document  
    (  
        Document                         --Full-text index column name   
            TYPE COLUMN FileExtension    --Name of column that contains file type information  
            Language 2057                 --2057 is the LCID for British English  
    )  
    KEY INDEX ui_ukDoc ON AdvWksDocFTCat --Unique index  
    WITH CHANGE_TRACKING AUTO            --Population type;  
    GO  
  
    ```  
  
     <span data-ttu-id="6597a-193">이 예에서 정의된 TYPE COLUMN은 'Document' 열(이진 형식)의 각 행에 있는 문서 유형이 포함된 테이블의 유형 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-193">The TYPE COLUMN defined in this example specifies the type column in the table that contains the type of the document in each row of the column 'Document' (which is of binary type).</span></span> <span data-ttu-id="6597a-194">유형 열은 지정 된 행의 문서에 대 한 사용자 제공 파일 확장명 (".doc", ".xls" 등)을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-194">The type column stores the user-supplied file extension-".doc", ".xls", and so on-of the document in a given row.</span></span> <span data-ttu-id="6597a-195">전체 텍스트 엔진은 지정된 행의 확장명을 사용하여 이러한 행의 데이터를 구문 분석하는 데 적합한 필터를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-195">The Full-Text Engine uses the file extension in a given row to invoke the correct filter to use for parsing the data in that row.</span></span> <span data-ttu-id="6597a-196">필터가 이러한 행의 이진 데이터를 구문 분석하면 지정된 단어 분리기가 내용을 구문 분석합니다. 이 예에서는 영어(영국)에 대한 단어 분리기가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-196">After the filter has parsed the binary data of the row, the specified word breaker will parse the content (in this example, the word breaker for British English is used).</span></span> <span data-ttu-id="6597a-197">필터링 프로세스는 사용자가 기본 테이블에서 열을 삽입 또는 업데이트하는 경우나 인덱싱 단계에서 발생합니다. 단, 전체 텍스트 인덱스에 자동 변경 추적이 사용되는 경우에 한합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-197">Note that the filtering process happens only at indexing time or if a user inserts or updates a column in the base table while automatic change tracking is enabled for the full-text index.</span></span> <span data-ttu-id="6597a-198">자세한 내용은 [고급 분석 확장 구성 및 관리](configure-and-manage-filters-for-search.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6597a-198">For more information, see [Configure and Manage Filters for Search](configure-and-manage-filters-for-search.md).</span></span>  
  
  
##  <a name="common-tasks"></a><a name="tasks"></a><span data-ttu-id="6597a-199">일반 작업</span><span class="sxs-lookup"><span data-stu-id="6597a-199">Common Tasks</span></span>  
  
### <a name="to-create-a-full-text-catalog"></a><span data-ttu-id="6597a-200">전체 텍스트 카탈로그를 만들려면</span><span class="sxs-lookup"><span data-stu-id="6597a-200">To Create a Full-Text Catalog</span></span>  
  
-   [<span data-ttu-id="6597a-201">CREATE FULLTEXT CATALOG&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6597a-201">CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-catalog-transact-sql)  
  
-   [<span data-ttu-id="6597a-202">전체 텍스트 카탈로그 만들기 및 관리</span><span class="sxs-lookup"><span data-stu-id="6597a-202">Create and Manage Full-Text Catalogs</span></span>](create-and-manage-full-text-catalogs.md)  
  
### <a name="to-view-the-indexes-of-a-table-or-view"></a><span data-ttu-id="6597a-203">테이블(또는 뷰)의 인덱스를 보려면</span><span class="sxs-lookup"><span data-stu-id="6597a-203">To View the Indexes of a Table (or View)</span></span>  
  
-   [<span data-ttu-id="6597a-204">sys.indexes&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6597a-204">sys.indexes &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)  
  
### <a name="to-create-a-unique-index"></a><span data-ttu-id="6597a-205">고유 인덱스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="6597a-205">To Create a Unique Index</span></span>  
  
-   [<span data-ttu-id="6597a-206">CREATE INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6597a-206">CREATE INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-index-transact-sql)  
  
-   [<span data-ttu-id="6597a-207">테이블 디자이너 열기&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="6597a-207">Open Table Designer &#40;Visual Database Tools&#41;</span></span>](../../ssms/visual-db-tools/visual-database-tools.md)  
  
### <a name="to-create-a-full-text-index"></a><span data-ttu-id="6597a-208">전체 텍스트 인덱스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="6597a-208">To Create a Full-Text Index</span></span>  
  
-   [<span data-ttu-id="6597a-209">CREATE FULLTEXT INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6597a-209">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-index-transact-sql)  
  
-   [<span data-ttu-id="6597a-210">전체 텍스트 인덱스 만들기 및 관리</span><span class="sxs-lookup"><span data-stu-id="6597a-210">Create and Manage Full-Text Indexes</span></span>](create-and-manage-full-text-indexes.md)  
  
### <a name="to-view-information-about-a-full-text-index"></a><span data-ttu-id="6597a-211">전체 텍스트 인덱스에 대한 정보를 보려면</span><span class="sxs-lookup"><span data-stu-id="6597a-211">To View Information about a Full-Text Index</span></span>  
  
|<span data-ttu-id="6597a-212">카탈로그 뷰 또는 동적 관리 뷰</span><span class="sxs-lookup"><span data-stu-id="6597a-212">Catalog or Dynamic Management View</span></span>|<span data-ttu-id="6597a-213">Description</span><span class="sxs-lookup"><span data-stu-id="6597a-213">Description</span></span>|  
|----------------------------------------|-----------------|  
|[<span data-ttu-id="6597a-214">sys.fulltext_index_catalog_usages&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6597a-214">sys.fulltext_index_catalog_usages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-catalog-usages-transact-sql)|<span data-ttu-id="6597a-215">전체 텍스트 인덱스 참조에 대한 각 전체 텍스트 카탈로그에 대해 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-215">Returns a row for each full-text catalog to full-text index reference.</span></span>|  
|[<span data-ttu-id="6597a-216">sys.fulltext_index_columns&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6597a-216">sys.fulltext_index_columns &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)|<span data-ttu-id="6597a-217">전체 텍스트 인덱스의 일부인 각 열에 대한 행을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-217">Contains a row for each column that is part of a full-text index.</span></span>|  
|[<span data-ttu-id="6597a-218">sys.fulltext_index_fragments&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6597a-218">sys.fulltext_index_fragments &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-fragments-transact-sql)|<span data-ttu-id="6597a-219">전체 텍스트 인덱스는 전체 텍스트 인덱스 조각이라고 하는 내부 테이블을 사용하여 반전된 인덱스 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-219">A fulltext index uses internal tables called full-text index fragments to store the inverted index data.</span></span> <span data-ttu-id="6597a-220">이 뷰를 사용하면 이러한 조각에 대한 메타데이터를 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-220">This view can be used to query the metadata about these fragments.</span></span> <span data-ttu-id="6597a-221">이 뷰에는 전체 텍스트 인덱스를 포함하는 모든 테이블의 각 전체 인덱스 조각에 대한 행이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-221">This view contains a row for each full-text index fragment in every table that contains a full-text index.</span></span>|  
|[<span data-ttu-id="6597a-222">sys.fulltext_indexes&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6597a-222">sys.fulltext_indexes &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql)|<span data-ttu-id="6597a-223">테이블 형식 개체의 각 전체 텍스트 인덱스당 한 개의 행을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-223">Contains a row per full-text index of a tabular object.</span></span>|  
|[<span data-ttu-id="6597a-224">sys.dm_fts_index_keywords&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6597a-224">sys.dm_fts_index_keywords &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql)|<span data-ttu-id="6597a-225">지정된 테이블에 대한 전체 텍스트 인덱스 내용에 관한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-225">Returns information about the content of a full-text index for the specified table.</span></span>|  
|[<span data-ttu-id="6597a-226">sys.dm_fts_index_keywords_by_document&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6597a-226">sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql)|<span data-ttu-id="6597a-227">지정된 테이블에 대한 전체 텍스트 인덱스의 문서 수준 내용에 관한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-227">Returns information about the document-level content of a full-text index for the specified table.</span></span> <span data-ttu-id="6597a-228">지정된 키워드는 여러 문서에 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-228">A given keyword can appear in several documents.</span></span>|  
|[<span data-ttu-id="6597a-229">sys.dm_fts_index_population&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6597a-229">sys.dm_fts_index_population &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql)|<span data-ttu-id="6597a-230">현재 진행 중인 전체 텍스트 인덱스 채우기에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6597a-230">Returns information about the full-text index populations currently in progress.</span></span>|  
  
  
## <a name="see-also"></a><span data-ttu-id="6597a-231">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6597a-231">See Also</span></span>  
 <span data-ttu-id="6597a-232">[CREATE FULLTEXT CATALOG&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6597a-232">[CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) </span></span>  
 <span data-ttu-id="6597a-233">[CREATE FULLTEXT INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6597a-233">[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span></span>  
 <span data-ttu-id="6597a-234">[Transact-sql&#41;&#40;전체 텍스트 중지 목록 만들기](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6597a-234">[CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) </span></span>  
 <span data-ttu-id="6597a-235">[CREATE TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6597a-235">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span></span>  
 <span data-ttu-id="6597a-236">[전체 텍스트 인덱스 채우기](populate-full-text-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="6597a-236">[Populate Full-Text Indexes](populate-full-text-indexes.md) </span></span>  
 <span data-ttu-id="6597a-237">[FULLTEXTCATALOGPROPERTY &#40;Transact-sql&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6597a-237">[FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) </span></span>  
 [<span data-ttu-id="6597a-238">OBJECTPROPERTYEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6597a-238">OBJECTPROPERTYEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/objectproperty-transact-sql)  
  
  
