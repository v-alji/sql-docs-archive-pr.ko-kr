---
title: MSSQLSERVER_2519 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2519 (Database Engine error)
ms.assetid: 8dc6ad98-5db8-4c88-8dea-6d455e63b839
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c8577b07586553f4b03714cd31451ac755faf824
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646526"
---
# <a name="mssqlserver_2519"></a><span data-ttu-id="48f5f-102">MSSQLSERVER_2519</span><span class="sxs-lookup"><span data-stu-id="48f5f-102">MSSQLSERVER_2519</span></span>
    
## <a name="details"></a><span data-ttu-id="48f5f-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="48f5f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="48f5f-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="48f5f-104">Product Name</span></span>|<span data-ttu-id="48f5f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="48f5f-105">SQL Server</span></span>|  
|<span data-ttu-id="48f5f-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="48f5f-106">Event ID</span></span>|<span data-ttu-id="48f5f-107">2519</span><span class="sxs-lookup"><span data-stu-id="48f5f-107">2519</span></span>|  
|<span data-ttu-id="48f5f-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="48f5f-108">Event Source</span></span>|<span data-ttu-id="48f5f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="48f5f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="48f5f-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="48f5f-110">Component</span></span>|<span data-ttu-id="48f5f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="48f5f-111">SQLEngine</span></span>|  
|<span data-ttu-id="48f5f-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="48f5f-112">Symbolic Name</span></span>|<span data-ttu-id="48f5f-113">DBCC_NO_EXPRESSION_EVALUATOR</span><span class="sxs-lookup"><span data-stu-id="48f5f-113">DBCC_NO_EXPRESSION_EVALUATOR</span></span>|  
|<span data-ttu-id="48f5f-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="48f5f-114">Message Text</span></span>|<span data-ttu-id="48f5f-115">내부 식 계산기를 초기화할 수 없으므로 개체 ID O_ID(개체 "O_NAME")에 대해 계산 열 및 사용자 정의 유형을 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="48f5f-115">Computed columns and user-defined types cannot be checked for object ID O_ID (object "O_NAME") because the internal expression evaluator could not be initialized.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="48f5f-116">설명</span><span class="sxs-lookup"><span data-stu-id="48f5f-116">Explanation</span></span>  
 <span data-ttu-id="48f5f-117">이 정보 메시지는 쿼리 프로세서가 내부 개체와 DBCC를 제공할 수 없어 계산 열과 CLR(공통 언어 런타임) 사용자 정의 유형을 평가할 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="48f5f-117">This informational message indicates that the query processor could not provide DBCC with an internal object to allow for the evaluation of computed columns and common language runtime (CLR) user-defined types.</span></span> <span data-ttu-id="48f5f-118">따라서 계산 열 및 CLR 사용자 정의 형식이 올바른지 확인하거나 DBCC에서 인덱스와 기본 테이블 간의 일관성을 확인할 때 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="48f5f-118">This means that computed columns and CLR user-defined types will not be checked for correctness or be used when DBCC checks the consistency between indexes and base tables.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="48f5f-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="48f5f-119">User Action</span></span>  
 <span data-ttu-id="48f5f-120">None</span><span class="sxs-lookup"><span data-stu-id="48f5f-120">None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48f5f-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="48f5f-121">See Also</span></span>  
 [<span data-ttu-id="48f5f-122">MSSQLSERVER_2518</span><span class="sxs-lookup"><span data-stu-id="48f5f-122">MSSQLSERVER_2518</span></span>](mssqlserver-2518-database-engine-error.md)  
  
  
