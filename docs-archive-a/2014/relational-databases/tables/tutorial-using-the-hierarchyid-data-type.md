---
title: '자습서: hierarchyid 데이터 형식 사용 | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- tutorials [hierarchyid]
- hierarchyid [Database Engine], tutorial
ms.assetid: 5a7f7cfd-7faf-439f-8085-8fd6bf7db355
author: stevestein
ms.author: sstein
ms.openlocfilehash: a735b4c2b51e1c680c8129647733ce1efd9f9984
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648908"
---
# <a name="tutorial-using-the-hierarchyid-data-type"></a><span data-ttu-id="0e7e8-102">자습서: hierarchyid 데이터 형식 사용</span><span class="sxs-lookup"><span data-stu-id="0e7e8-102">Tutorial: Using the hierarchyid Data Type</span></span>
  <span data-ttu-id="0e7e8-103">이 자습서는 [!INCLUDE[tsql](../../includes/tsql-md.md)]에 대한 경험은 있지만 `hierarchyid` 데이터 형식은 처음 사용하는 사용자를 위해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e7e8-103">This tutorial is intended for users who are experienced with [!INCLUDE[tsql](../../includes/tsql-md.md)], but are new to the `hierarchyid` data type.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="0e7e8-104">학습 내용</span><span class="sxs-lookup"><span data-stu-id="0e7e8-104">What You Will Learn</span></span>  
 <span data-ttu-id="0e7e8-105">이 자습서는 다음 두 단원으로 이루어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e7e8-105">This tutorial is divided into two lessons:</span></span>  
  
 [<span data-ttu-id="0e7e8-106">1단원: 테이블을 계층 구조로 변환</span><span class="sxs-lookup"><span data-stu-id="0e7e8-106">Lesson 1: Converting a Table to a Hierarchical Structure</span></span>](lesson-1-converting-a-table-to-a-hierarchical-structure.md)  
 <span data-ttu-id="0e7e8-107">이 단원에서는 부모/자식 계층으로 구조화된 기존 직원 테이블을 가져와  `hierarchyid` 데이터 형식을 사용하여 계층을 나타내는 새 테이블로 데이터를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0e7e8-107">In this lesson, you take an existing employee table that is structured as a parent/child hierarchy and move the data into a new table that represents the hierarchy by using the `hierarchyid` data type.</span></span> <span data-ttu-id="0e7e8-108">이 단원에는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 예제 데이터베이스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0e7e8-108">This lesson requires the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
 [<span data-ttu-id="0e7e8-109">2단원: 계층적 테이블의 데이터 만들기 및 관리</span><span class="sxs-lookup"><span data-stu-id="0e7e8-109">Lesson 2: Creating and Managing Data in a Hierarchical Table</span></span>](lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
 <span data-ttu-id="0e7e8-110">이 단원에서는 `hierarchyid` 데이터 형식을 사용하여 테이블을 만들어 계층 구조를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0e7e8-110">In this lesson, you create a table by using the `hierarchyid` data type to represent the hierarchy structure.</span></span> <span data-ttu-id="0e7e8-111">그리고 계층 메서드를 사용하여 테이블의 데이터를 조작하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0e7e8-111">Then, you manipulate the data in the table by using the hierarchical methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e7e8-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="0e7e8-112">Requirements</span></span>  
 <span data-ttu-id="0e7e8-113">시스템에는 다음이 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e7e8-113">Your system must have the following installed:</span></span>  
  
-   <span data-ttu-id="0e7e8-114">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상(버전은 관계 없음)</span><span class="sxs-lookup"><span data-stu-id="0e7e8-114">Any edition of [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later.</span></span>  
  
-   <span data-ttu-id="0e7e8-115">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Express</span><span class="sxs-lookup"><span data-stu-id="0e7e8-115">Either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Express.</span></span>  
  
-   <span data-ttu-id="0e7e8-116">Internet Explorer 6 이상 버전</span><span class="sxs-lookup"><span data-stu-id="0e7e8-116">Internet Explorer 6 or a later version.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e7e8-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0e7e8-117">See Also</span></span>  
 <span data-ttu-id="0e7e8-118">[자습서: 데이터베이스 엔진 시작](../tutorial-getting-started-with-the-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="0e7e8-118">[Tutorial: Getting Started with the Database Engine](../tutorial-getting-started-with-the-database-engine.md) </span></span>  
 <span data-ttu-id="0e7e8-119">[자습서: Transact-sql 문 작성](../../t-sql/tutorial-writing-transact-sql-statements.md) </span><span class="sxs-lookup"><span data-stu-id="0e7e8-119">[Tutorial: Writing Transact-SQL Statements](../../t-sql/tutorial-writing-transact-sql-statements.md) </span></span>  
 <span data-ttu-id="0e7e8-120">[hierarchyid 데이터 형식 메서드 참조](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) </span><span class="sxs-lookup"><span data-stu-id="0e7e8-120">[hierarchyid Data Type Method Reference](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) </span></span>  
 <span data-ttu-id="0e7e8-121">[계층적 데이터 &#40;SQL Server&#41;](../hierarchical-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0e7e8-121">[Hierarchical Data &#40;SQL Server&#41;](../hierarchical-data-sql-server.md) </span></span>  
 [<span data-ttu-id="0e7e8-122">hierarchyid&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0e7e8-122">hierarchyid &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/hierarchyid-data-type-method-reference)  
  
  
