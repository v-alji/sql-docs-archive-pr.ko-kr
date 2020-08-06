---
title: 비클러스터형 Columnstore 인덱스 사용 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: 4c341fb8-7cb1-4cab-921b-e80b751d6c19
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: c876eb6fdd466349ac369dcff8e292bc0839c669
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732003"
---
# <a name="using-nonclustered-columnstore-indexes"></a><span data-ttu-id="c4d95-102">비클러스터형 columnstore 인덱스 사용</span><span class="sxs-lookup"><span data-stu-id="c4d95-102">Using Nonclustered Columnstore Indexes</span></span>
  <span data-ttu-id="c4d95-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 테이블에서 비클러스터형 columnstore 인덱스를 사용하기 위한 주요 태스크를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d95-103">Describes key tasks for using a nonclustered columnstore index on a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] table.</span></span>

 <span data-ttu-id="c4d95-104">columnstore 인덱스에 대한 개요는 [Columnstore Indexes Described](../relational-databases/indexes/columnstore-indexes-described.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c4d95-104">For an overview of columnstore indexes, see [Columnstore Indexes Described](../relational-databases/indexes/columnstore-indexes-described.md).</span></span>

 <span data-ttu-id="c4d95-105">클러스터형 columnstore 인덱스에 대한 자세한 내용은 [Using Clustered Columnstore Indexes](../relational-databases/indexes/indexes.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c4d95-105">For information about clustered columnstore indexes, see [Using Clustered Columnstore Indexes](../relational-databases/indexes/indexes.md).</span></span>

## <a name="contents"></a><span data-ttu-id="c4d95-106">콘텐츠</span><span class="sxs-lookup"><span data-stu-id="c4d95-106">Contents</span></span>

-   [<span data-ttu-id="c4d95-107">비클러스터형 Columnstore 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="c4d95-107">Create a Nonclustered Columnstore Index</span></span>](../../2014/database-engine/using-nonclustered-columnstore-indexes.md#load)

-   [<span data-ttu-id="c4d95-108">비클러스터형 Columnstore 인덱스의 데이터 변경</span><span class="sxs-lookup"><span data-stu-id="c4d95-108">Change the Data in a Nonclustered Columnstore Index</span></span>](../../2014/database-engine/using-nonclustered-columnstore-indexes.md#change)

##  <a name="create-a-nonclustered-columnstore-index"></a><a name="load"></a><span data-ttu-id="c4d95-109">비클러스터형 Columnstore 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="c4d95-109">Create a Nonclustered Columnstore Index</span></span>
 <span data-ttu-id="c4d95-110">비클러스터형 columnstore 인덱스로 데이터를 로드 하려면 먼저 힙 또는 클러스터형 인덱스로 저장 된 기존의 rowstore 테이블로 데이터를 로드 한 다음 [CREATE COLUMNSTORE index &#40;transact-sql&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql) 를 사용 하 여 columnstore 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c4d95-110">To load data into a nonclustered columnstore index, first load data into a traditional rowstore table stored as a heap or clustered index, and then use [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql) to create a columnstore index.</span></span>

 <span data-ttu-id="c4d95-111">![데이터를 columnstore 인덱스로 로드](../../2014/database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "데이터를 columnstore 인덱스로 로드")</span><span class="sxs-lookup"><span data-stu-id="c4d95-111">![Loading data into a columnstore index](../../2014/database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "Loading data into a columnstore index")</span></span>

##  <a name="change-the-data-in-a-nonclustered-columnstore-index"></a><a name="change"></a><span data-ttu-id="c4d95-112">비클러스터형 Columnstore 인덱스의 데이터 변경</span><span class="sxs-lookup"><span data-stu-id="c4d95-112">Change the Data in a Nonclustered Columnstore Index</span></span>
 <span data-ttu-id="c4d95-113">테이블에 비클러스터형 columnstore 인덱스를 만든 후에는 해당 테이블에서 데이터를 직접 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c4d95-113">Once you create a nonclustered columnstore index on a table, you cannot directly modify the data in that table.</span></span> <span data-ttu-id="c4d95-114">INSERT, UPDATE, DELETE 또는 MERGE를 사용한 쿼리는 실패하며 오류 메시지를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d95-114">A query with INSERT, UPDATE, DELETE, or MERGE will fail and return an error message.</span></span> <span data-ttu-id="c4d95-115">테이블에서 데이터를 추가하거나 수정하려면 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d95-115">To add or modify the data in the table, you can do one of the following:</span></span>

-   <span data-ttu-id="c4d95-116">Columnstore 인덱스를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d95-116">Disable the columnstore index.</span></span> <span data-ttu-id="c4d95-117">그런 다음 테이블에서 데이터를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4d95-117">You can then update the data in the table.</span></span> <span data-ttu-id="c4d95-118">columnstore 인덱스를 사용하지 않도록 설정하는 경우 데이터 업데이트를 완료할 때 columnstore 인덱스를 다시 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4d95-118">If you disable the columnstore index, you can rebuild the columnstore index when you finish updating the data.</span></span> <span data-ttu-id="c4d95-119">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c4d95-119">For example:</span></span>

    ```
    ALTER INDEX mycolumnstoreindex ON mytable DISABLE;
    -- update mytable --
    ALTER INDEX mycolumnstoreindex on mytable REBUILD
    ```

-   <span data-ttu-id="c4d95-120">Columnstore 인덱스를 삭제 하 고 테이블을 업데이트 한 다음 CREATE COLUMNSTORE INDEX를 사용 하 여 columnstore 인덱스를 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c4d95-120">Drop the columnstore index, update the table, and then re-create the columnstore index with CREATE COLUMNSTORE INDEX.</span></span> <span data-ttu-id="c4d95-121">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c4d95-121">For example:</span></span>

    ```
    DROP INDEX mycolumnstoreindex ON mytable
    -- update mytable --
    CREATE NONCLUSTERED COLUMNSTORE INDEX mycolumnstoreindex ON mytable;

    ```

-   <span data-ttu-id="c4d95-122">columnstore 인덱스가 없는 준비 테이블에 데이터를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d95-122">Load data into a staging table that does not have a columnstore index.</span></span> <span data-ttu-id="c4d95-123">준비 테이블에서 columnstore 인덱스를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d95-123">Build a columnstore index on the staging table.</span></span> <span data-ttu-id="c4d95-124">준비 테이블을 주 테이블의 빈 파티션으로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d95-124">Switch the staging table into an empty partition of the main table.</span></span>

-   <span data-ttu-id="c4d95-125">columnstore 인덱스가 있는 테이블에서 빈 준비 테이블로 파티션을 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d95-125">Switch a partition from the table with the columnstore index into an empty staging table.</span></span> <span data-ttu-id="c4d95-126">준비 테이블에 columnstore 인덱스가 있는 경우 columnstore 인덱스를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d95-126">If there is a columnstore index on the staging table, disable the columnstore index.</span></span> <span data-ttu-id="c4d95-127">업데이트를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d95-127">Perform any updates.</span></span> <span data-ttu-id="c4d95-128">columnstore 인덱스를 작성 또는 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d95-128">Build (or rebuild) the columnstore index.</span></span> <span data-ttu-id="c4d95-129">준비 테이블을 주 테이블의 파티션(현재 비어 있음)으로 다시 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d95-129">Switch the staging table back into the (now empty) partition of the main table.</span></span>




