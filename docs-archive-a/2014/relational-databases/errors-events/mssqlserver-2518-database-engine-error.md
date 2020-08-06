---
title: MSSQLSERVER_2518 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2518 (Database Engine error)
ms.assetid: 54a13abc-4c33-43f0-b55d-e2e74a1381c8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5f5517458c1014d7830c4813b95e1120bef452e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649084"
---
# <a name="mssqlserver_2518"></a><span data-ttu-id="a4433-102">MSSQLSERVER_2518</span><span class="sxs-lookup"><span data-stu-id="a4433-102">MSSQLSERVER_2518</span></span>
    
## <a name="details"></a><span data-ttu-id="a4433-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="a4433-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a4433-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="a4433-104">Product Name</span></span>|<span data-ttu-id="a4433-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a4433-105">SQL Server</span></span>|  
|<span data-ttu-id="a4433-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="a4433-106">Event ID</span></span>|<span data-ttu-id="a4433-107">2518</span><span class="sxs-lookup"><span data-stu-id="a4433-107">2518</span></span>|  
|<span data-ttu-id="a4433-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="a4433-108">Event Source</span></span>|<span data-ttu-id="a4433-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a4433-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a4433-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="a4433-110">Component</span></span>|<span data-ttu-id="a4433-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a4433-111">SQLEngine</span></span>|  
|<span data-ttu-id="a4433-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="a4433-112">Symbolic Name</span></span>|<span data-ttu-id="a4433-113">DBCC_NO_EXPRESSION_EVAL_CLR_DISABLED</span><span class="sxs-lookup"><span data-stu-id="a4433-113">DBCC_NO_EXPRESSION_EVAL_CLR_DISABLED</span></span>|  
|<span data-ttu-id="a4433-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="a4433-114">Message Text</span></span>|<span data-ttu-id="a4433-115">개체 ID O_ID(개체 "O_NAME"): CLR(공용 언어 런타임)을 사용할 수 없으므로 이 개체에 대해 계산 열과 사용자 정의 유형을 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a4433-115">Object ID O_ID (object "O_NAME"): Computed columns and user-defined types cannot be checked for this object because the common language runtime (CLR) is disabled.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a4433-116">설명</span><span class="sxs-lookup"><span data-stu-id="a4433-116">Explanation</span></span>  
 <span data-ttu-id="a4433-117">이 정보 메시지는 쿼리 프로세서가 내부 개체와 DBCC를 제공할 수 없어 계산 열과 CLR(공통 언어 런타임) 사용자 정의 유형을 평가할 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a4433-117">This informational message indicates that the query processor could not provide DBCC with an internal object to allow for computed columns and common language runtime (CLR) user-defined types to be evaluated.</span></span> <span data-ttu-id="a4433-118">이 문제는 열 중 하나가 CLR과 관련되어 있으나 CLR을 사용할 수 없으므로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a4433-118">This problem occurred because one of the columns involved the CLR, but the CLR is not enabled.</span></span> <span data-ttu-id="a4433-119">내부 개체는 모든 열을 포함하므로</span><span class="sxs-lookup"><span data-stu-id="a4433-119">The internal object covers all columns.</span></span> <span data-ttu-id="a4433-120">단일 열을 평가할 수 없으면 내부 개체를 생성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a4433-120">Therefore, the inability to evaluate a single column prevents creating the internal object.</span></span> <span data-ttu-id="a4433-121">따라서 계산 열이 올바른지 확인할 수 없으며 DBCC에서 인덱스와 기본 테이블 간의 일관성을 확인할 때 계산 열을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a4433-121">This means that computed columns will not be checked for correctness or be used when DBCC checks the consistency between indexes and base tables.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a4433-122">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="a4433-122">User Action</span></span>  
 <span data-ttu-id="a4433-123">CLR을 사용하고 DBCC 문을 다시 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a4433-123">Enable CLR and rerun the DBCC statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4433-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a4433-124">See Also</span></span>  
 [<span data-ttu-id="a4433-125">CLR 통합 사용</span><span class="sxs-lookup"><span data-stu-id="a4433-125">Enabling CLR Integration</span></span>](../clr-integration/clr-integration-enabling.md)  
  
  
