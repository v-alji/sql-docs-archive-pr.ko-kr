---
title: MSSQLSERVER_8525 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "8525"
helpviewer_keywords:
- 8525 (Database Engine error)
ms.assetid: 297867c1-691e-4d6b-a3be-a7575015ecfa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 36db48ca2a9afd08dadcd12abc13b9978e227b00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652858"
---
# <a name="mssqlserver_8525"></a><span data-ttu-id="f4b9c-102">MSSQLSERVER_8525</span><span class="sxs-lookup"><span data-stu-id="f4b9c-102">MSSQLSERVER_8525</span></span>
    
## <a name="details"></a><span data-ttu-id="f4b9c-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="f4b9c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f4b9c-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="f4b9c-104">Product Name</span></span>|<span data-ttu-id="f4b9c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f4b9c-105">SQL Server</span></span>|  
|<span data-ttu-id="f4b9c-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="f4b9c-106">Event ID</span></span>|<span data-ttu-id="f4b9c-107">8525</span><span class="sxs-lookup"><span data-stu-id="f4b9c-107">8525</span></span>|  
|<span data-ttu-id="f4b9c-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="f4b9c-108">Event Source</span></span>|<span data-ttu-id="f4b9c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f4b9c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f4b9c-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="f4b9c-110">Component</span></span>|<span data-ttu-id="f4b9c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f4b9c-111">SQLEngine</span></span>|  
|<span data-ttu-id="f4b9c-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="f4b9c-112">Symbolic Name</span></span>||  
|<span data-ttu-id="f4b9c-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="f4b9c-113">Message Text</span></span>|<span data-ttu-id="f4b9c-114">분산 트랜잭션이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f4b9c-114">Distributed transaction completed.</span></span> <span data-ttu-id="f4b9c-115">이 세션을 새 트랜잭션이나 NULL 트랜잭션에 참여하게 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f4b9c-115">Either enlist this session in a new transaction or the NULL transaction.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f4b9c-116">설명</span><span class="sxs-lookup"><span data-stu-id="f4b9c-116">Explanation</span></span>  
 <span data-ttu-id="f4b9c-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 함께 DTC(Distributed Transaction Coordinator)를 사용하기 위한 프로그래밍 모델에서는 애플리케이션을 명시적으로 분산 트랜잭션에 참여시키고 분산 트랜잭션에서 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4b9c-117">The programming model for using the Distributed Transaction Coordinator with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requires applications to explicitly enlist to and defect from a distributed transaction.</span></span>  
  
 <span data-ttu-id="f4b9c-118">이 오류는 다음과 같은 4가지 조건이 만족되면 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f4b9c-118">This error occurs when the following four conditions are met:</span></span>  
  
-   <span data-ttu-id="f4b9c-119">애플리케이션이 분산 트랜잭션에 참여했습니다.</span><span class="sxs-lookup"><span data-stu-id="f4b9c-119">The application has enlisted into a distributed transaction.</span></span>  
  
-   <span data-ttu-id="f4b9c-120">어떤 이유로 인해 트랜잭션이 종료되어 커밋되거나 롤백되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f4b9c-120">The transaction has ended, either committed or rolled back, for any reason.</span></span>  
  
-   <span data-ttu-id="f4b9c-121">사용자 애플리케이션이 명시적으로 분산 트랜잭션에서 제거되지 않았거나 명시적으로 새로운 분산 트랜잭션에 참여하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f4b9c-121">The user application has not explicitly defected from a distributed transaction or explicitly enlisted into a new distributed transaction.</span></span>  
  
-   <span data-ttu-id="f4b9c-122">애플리케이션이 기존 분산 트랜잭션에서 제거하거나 새로운 분산 트랜잭션에 참여하는 작업 이외의 트랜잭션 작업(예: 쿼리 실행 또는 로컬 트랜잭션 시작)을 수행하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4b9c-122">The application tries to do any transactional operation other than defecting from existing distributed transaction or enlisting to a new distributed transaction, such as issuing a query or starting a local transaction.</span></span>  
  
 <span data-ttu-id="f4b9c-123">오류 상태 1은 애플리케이션이 로컬 트랜잭션을 만드는 작업을 수행하는 경우 사용되며 상태 2는 애플리케이션이 바운드 세션에 참여하려고 하는 경우 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4b9c-123">Error state 1 is used when the application performs an operation that creates local transactions, and state 2 is used when application tries to enlist to a bound session.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f4b9c-124">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="f4b9c-124">User Action</span></span>  
 <span data-ttu-id="f4b9c-125">애플리케이션이 분산 트랜잭션에 참여한 다음에는 해당 애플리케이션을 명시적으로 분산 트랜잭션에서 제거하거나 다른 분산 트랜잭션에 참여시켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4b9c-125">After an application has enlisted into a distributed transaction, the application must explicitly defect from the distributed transaction or enlist to another distributed transaction.</span></span> <span data-ttu-id="f4b9c-126">이렇게 하면 응용 프로그램이 이전에 참여한 트랜잭션에서 암시적으로 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4b9c-126">This will implicitly defect from a previous enlisted transaction.</span></span> <span data-ttu-id="f4b9c-127">분산 트랜잭션에서 제거하거나 분산 트랜잭션에 참여시키기 위한 정확한 구문은 애플리케이션에 대한 프로그래밍 인터페이스 매뉴얼을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f4b9c-127">For the exact syntax to defect from or enlist to a distributed transaction, see the programming interface manual for the application.</span></span>  
  
  
