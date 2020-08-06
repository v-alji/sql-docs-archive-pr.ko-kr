---
title: MSSQLSERVER_360 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 360 (Database Engine error)
ms.assetid: e2b7c1b2-3679-4206-9b25-6bd55ef96a2c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b30311d7f55231c1e7a6d5969d49c5d1bc07a848
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649573"
---
# <a name="mssqlserver_360"></a><span data-ttu-id="5983d-102">MSSQLSERVER_360</span><span class="sxs-lookup"><span data-stu-id="5983d-102">MSSQLSERVER_360</span></span>
    
## <a name="details"></a><span data-ttu-id="5983d-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="5983d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5983d-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="5983d-104">Product Name</span></span>|<span data-ttu-id="5983d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5983d-105">SQL Server</span></span>|  
|<span data-ttu-id="5983d-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="5983d-106">Event ID</span></span>|<span data-ttu-id="5983d-107">360</span><span class="sxs-lookup"><span data-stu-id="5983d-107">360</span></span>|  
|<span data-ttu-id="5983d-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="5983d-108">Event Source</span></span>|<span data-ttu-id="5983d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5983d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5983d-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="5983d-110">Component</span></span>|<span data-ttu-id="5983d-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5983d-111">SQLEngine</span></span>|  
|<span data-ttu-id="5983d-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="5983d-112">Symbolic Name</span></span>|<span data-ttu-id="5983d-113">DML_UPDATE_SPARSE_AND_COLSET</span><span class="sxs-lookup"><span data-stu-id="5983d-113">DML_UPDATE_SPARSE_AND_COLSET</span></span>|  
|<span data-ttu-id="5983d-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="5983d-114">Message Text</span></span>|<span data-ttu-id="5983d-115">INSERT, UPDATE 또는 MERGE 문의 대상 열 목록은 스파스 열과 스파스 열이 포함된 열 집합을 모두 포함할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5983d-115">The target column list of an INSERT, UPDATE, or MERGE statement cannot contain both a sparse column and the column set that contains the sparse column.</span></span> <span data-ttu-id="5983d-116">스파스 열 또는 열 집합 중 하나만 포함하도록 문을 다시 작성하십시오.</span><span class="sxs-lookup"><span data-stu-id="5983d-116">Rewrite the statement to include either the sparse column or the column set, but not both.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5983d-117">설명</span><span class="sxs-lookup"><span data-stu-id="5983d-117">Explanation</span></span>  
 <span data-ttu-id="5983d-118">열 집합은 일부 테이블 열을 구조화된 출력으로 결합하는 형식화되지 않은 XML 표현입니다.</span><span class="sxs-lookup"><span data-stu-id="5983d-118">A column set is an untyped XML representation that combines some columns of a table into a structured output.</span></span> <span data-ttu-id="5983d-119">열 집합 및 열 집합에 포함된 열을 모두 수정하려고 했습니다. 이로 인해 동일한 열에 대한 참조가 두 개 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="5983d-119">An attempt was made to modify both the column set and a column that is included in the column set, causing two references to the same column.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5983d-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="5983d-120">User Action</span></span>  
 <span data-ttu-id="5983d-121">열 또는 열 집합 중 하나에 대한 참조만 포함하도록 문을 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="5983d-121">Rewrite the statement to include references to either the column or the column set, but do not include both in the statement.</span></span>  
  
  
