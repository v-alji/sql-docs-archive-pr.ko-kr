---
title: '1단원: 테이블을 계층 구조로 변환 | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 5ee6f19a-6dd7-4730-a91c-bbed1bd77e0b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 196a546093786f9be4b88536763b3150ae750f97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740795"
---
# <a name="lesson-1-converting-a-table-to-a-hierarchical-structure"></a><span data-ttu-id="58a6d-102">1단원: 테이블을 계층 구조로 변환</span><span class="sxs-lookup"><span data-stu-id="58a6d-102">Lesson 1: Converting a Table to a Hierarchical Structure</span></span>
  <span data-ttu-id="58a6d-103">자체 조인을 사용하여 계층 관계를 나타내는 테이블을 보유하고 있는 경우 이 단원의 내용을 참조하여 해당 테이블을 계층 구조로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58a6d-103">Customers who have tables using self joins to express hierarchical relationships can convert their tables to a hierarchical structure using this lesson as a guide.</span></span> <span data-ttu-id="58a6d-104">이 표현을 `hierarchyid`를 사용하는 표현으로 마이그레이션하는 작업은 비교적 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="58a6d-104">It is relatively easy to migrate from this representation to one using `hierarchyid`.</span></span> <span data-ttu-id="58a6d-105">마이그레이션하면 간단하고 이해하기 쉬운 계층적 표현이 완성되며 효율적인 쿼리를 위해 여러 가지 방법으로 인덱싱할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58a6d-105">After migration, users will have a compact and easy to understand hierarchical representation, which can be indexed in several ways for efficient queries.</span></span>  
  
 <span data-ttu-id="58a6d-106">이 단원에서는 기존 테이블을 검토하고, `hierarchyid` 열이 포함된 새 테이블을 만들고, 원본 테이블의 데이터로 이 테이블을 채운 다음 인덱싱 방법 3가지를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="58a6d-106">This lesson, examines an existing table, creates a new table containing a `hierarchyid` column, populates the table with the data from the source table, and then demonstrates three indexing strategies.</span></span> <span data-ttu-id="58a6d-107">이 단원에서는 다음 항목을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="58a6d-107">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="58a6d-108">Employee 테이블의 현재 구조 검사</span><span class="sxs-lookup"><span data-stu-id="58a6d-108">Examining the Current Structure of the Employee Table</span></span>](lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
-   [<span data-ttu-id="58a6d-109">기존 계층적 데이터로 테이블 채우기</span><span class="sxs-lookup"><span data-stu-id="58a6d-109">Populating a Table with Existing Hierarchical Data</span></span>](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
-   [<span data-ttu-id="58a6d-110">NewOrg 테이블 최적화</span><span class="sxs-lookup"><span data-stu-id="58a6d-110">Optimizing the NewOrg Table</span></span>](lesson-1-3-optimizing-the-neworg-table.md)  
  
-   [<span data-ttu-id="58a6d-111">요약: 테이블을 계층 구조로 변환</span><span class="sxs-lookup"><span data-stu-id="58a6d-111">Summary: Converting a Table to a Hierarchical Structure</span></span>](lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
## <a name="prerequisites"></a><span data-ttu-id="58a6d-112">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="58a6d-112">Prerequisites</span></span>  
 <span data-ttu-id="58a6d-113">이 단원에는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 예제 데이터베이스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="58a6d-113">This lesson requires the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="58a6d-114">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="58a6d-114">Next Task in Lesson</span></span>  
 [<span data-ttu-id="58a6d-115">Employee 테이블의 현재 구조 검사</span><span class="sxs-lookup"><span data-stu-id="58a6d-115">Examining the Current Structure of the Employee Table</span></span>](lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="58a6d-116">다음 단원</span><span class="sxs-lookup"><span data-stu-id="58a6d-116">Next Lesson</span></span>  
 [<span data-ttu-id="58a6d-117">2단원: 계층적 테이블의 데이터 만들기 및 관리</span><span class="sxs-lookup"><span data-stu-id="58a6d-117">Lesson 2: Creating and Managing Data in a Hierarchical Table</span></span>](lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
  
  
