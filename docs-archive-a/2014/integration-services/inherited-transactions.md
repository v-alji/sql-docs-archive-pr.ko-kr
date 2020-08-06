---
title: 상속 된 트랜잭션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Integration Services], inherited
- child packages
- inherited transactions [Integration Services]
ms.assetid: 90db5564-d41e-4cfe-8c9e-4e68d41eff1c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0ecb480420fe9f2492c29fad37ee3cc6e6501e3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651189"
---
# <a name="inherited-transactions"></a><span data-ttu-id="e550e-102">상속된 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="e550e-102">Inherited Transactions</span></span>
  <span data-ttu-id="e550e-103">패키지 실행 태스크를 사용하면 패키지가 다른 패키지를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e550e-103">A package can run another package by using the Execute Package task.</span></span> <span data-ttu-id="e550e-104">패키지 실행 태스크에서 실행하는 패키지인 자식 패키지는 자체의 패키지 트랜잭션을 만들거나 부모 패키지 트랜잭션을 상속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e550e-104">The child package, which is the package run by the Execute Package task, may create its own package transaction, or it may inherit the parent package transaction.</span></span>  
  
 <span data-ttu-id="e550e-105">다음 두 가지 조건에 모두 해당하면 자식 패키지는 부모 패키지 트랜잭션을 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="e550e-105">A child package inherits the parent package transaction if both of the following are true:</span></span>  
  
-   <span data-ttu-id="e550e-106">패키지 실행 태스크가 패키지를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="e550e-106">The package is invoked by an Execute Package task.</span></span>  
  
-   <span data-ttu-id="e550e-107">패키지를 호출한 패키지 실행 태스크가 부모 패키지 트랜잭션도 조인했습니다.</span><span class="sxs-lookup"><span data-stu-id="e550e-107">The Execute Package task that invoked the package also joined the parent package transaction.</span></span>  
  
 <span data-ttu-id="e550e-108">자식 패키지가 트랜잭션에 조인하지 않으면 자식 패키지 내의 컨테이너 및 태스크가 부모 패키지 트랜잭션에 조인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e550e-108">Containers and tasks in the child package cannot join the parent package transaction unless the child package itself joins the transaction.</span></span>  
  
## <a name="illustration-of-package-transactions"></a><span data-ttu-id="e550e-109">패키지 트랜잭션의 그림</span><span class="sxs-lookup"><span data-stu-id="e550e-109">Illustration of Package Transactions</span></span>  
 <span data-ttu-id="e550e-110">다음 다이어그램에서 트랜잭션을 사용하는 3개의 패키지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e550e-110">In the following diagram, there are three packages that all use transactions.</span></span> <span data-ttu-id="e550e-111">각 패키지는 여러 태스크를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e550e-111">Each package contains multiple tasks.</span></span> <span data-ttu-id="e550e-112">트랜잭션 동작을 강조하기 위해 패키지 실행 태스크만 표시했습니다.</span><span class="sxs-lookup"><span data-stu-id="e550e-112">To emphasize the behavior of the transactions, only the Execute Package tasks are shown.</span></span> <span data-ttu-id="e550e-113">패키지 A는 패키지 B와 C를 실행하고 차례로 패키지 B는 패키지 D와 E를 실행하며 패키지 C는 패키지 F를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e550e-113">Package A runs packages B and C. In turn, package B runs packages D and E, and package C runs package F.</span></span>  
  
 <span data-ttu-id="e550e-114">패키지 및 태스크는 다음 트랜잭션 특성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="e550e-114">Packages and tasks have the following transaction attributes:</span></span>  
  
-   <span data-ttu-id="e550e-115">패키지 A 및 C의**트랜잭션 옵션** 은 **필수** 로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e550e-115">**TransactionOption** is set to **Required** on packages A and C</span></span>  
  
-   <span data-ttu-id="e550e-116">패키지 B 및 D, 패키지 실행 태스크 B, 패키지 실행 D 및 패키지 실행 F의**트랜잭션 옵션** 은 **지원** 으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e550e-116">**TransactionOption** is set to **Supported** on packages B and D, and on the tasks Execute Package B, Execute Package D, and Execute Package F.</span></span>  
  
-   <span data-ttu-id="e550e-117">패키지 E, 패키지 실행 태스크 C 및 패키지 실행 E의**트랜잭션 옵션** 은 **지원되지 않음** 으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e550e-117">**TransactionOption** is set to **NotSupported** on package E, and on the tasks Execute Package C and Execute Package E.</span></span>  
  
 <span data-ttu-id="e550e-118">![상속된 트랜잭션의 흐름](media/mw-dts-executepack.gif "상속된 트랜잭션의 흐름")</span><span class="sxs-lookup"><span data-stu-id="e550e-118">![Flow of inherited transactions](media/mw-dts-executepack.gif "Flow of inherited transactions")</span></span>  
  
 <span data-ttu-id="e550e-119">패키지 B, D 및 F만 부모 패키지에서 트랜잭션을 상속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e550e-119">Only packages B, D, and F can inherit transactions from their parent packages.</span></span>  
  
 <span data-ttu-id="e550e-120">패키지 B 및 D는 패키지 A가 시작한 트랜잭션을 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="e550e-120">Packages B and D inherit the transaction that was started by package A.</span></span>  
  
 <span data-ttu-id="e550e-121">패키지 F는 패키지 C가 시작한 트랜잭션을 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="e550e-121">Package F inherits the transaction that was started by package C.</span></span>  
  
 <span data-ttu-id="e550e-122">패키지 A와 C는 자체 트랜잭션을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="e550e-122">Packages A and C control their own transactions.</span></span>  
  
 <span data-ttu-id="e550e-123">패키지 E는 트랜잭션을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e550e-123">Package E does not use transactions.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="e550e-124">관련 작업</span><span class="sxs-lookup"><span data-stu-id="e550e-124">Related Tasks</span></span>  
 [<span data-ttu-id="e550e-125">트랜잭션을 사용하도록 패키지 구성</span><span class="sxs-lookup"><span data-stu-id="e550e-125">Configure a Package to Use Transactions</span></span>](../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
  
