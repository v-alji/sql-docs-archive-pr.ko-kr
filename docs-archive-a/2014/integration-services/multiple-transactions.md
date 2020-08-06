---
title: 여러 트랜잭션 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Integration Services], multiple
- multiple transactions
ms.assetid: c3664a94-be89-40c0-a3a0-84b74a7fedbe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5ff909c92a23c965047edc0fcf278e17e4c76d94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651094"
---
# <a name="multiple-transactions"></a><span data-ttu-id="164ab-102">여러 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="164ab-102">Multiple Transactions</span></span>
  <span data-ttu-id="164ab-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지 내의 관련 없는 트랜잭션을 한 개의 패키지가 포함하는 것이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="164ab-103">It is possible for a package to include unrelated transactions in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package.</span></span> <span data-ttu-id="164ab-104">중첩 컨테이너 계층 중간의 컨테이너가 트랜잭션을 지원하지 않으면 위 또는 아래에 위치한 컨테이너에서 별도의 트랜잭션을 시작합니다(트랜잭션을 지원하도록 구성된 경우).</span><span class="sxs-lookup"><span data-stu-id="164ab-104">Any time a container in the middle of a nested container hierarchy does not support transactions, the containers above or below it in the hierarchy start separate transactions if they are configured to support transactions.</span></span> <span data-ttu-id="164ab-105">트랜잭션은 중첩 컨테이너 계층의 가장 안쪽 태스크부터 순서대로 패키지에 커밋 또는 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="164ab-105">The transactions commit or roll back in order from the innermost task in the nested container hierarchy to the package.</span></span> <span data-ttu-id="164ab-106">그러나 내부 트랜잭션이 커밋한 후에는 외부 트랜잭션이 중단되더라도 롤백하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="164ab-106">However, after the inner transaction commits, it does not roll back if an outer transaction is aborted.</span></span>

## <a name="illustration-of-multiple-transactions"></a><span data-ttu-id="164ab-107">다중 트랜잭션의 그림</span><span class="sxs-lookup"><span data-stu-id="164ab-107">Illustration of Multiple Transactions</span></span>
 <span data-ttu-id="164ab-108">예를 들어 한 패키지가 두 개의 Foreach 루프 컨테이너를 포함하고 각 컨테이너가 다시 두 개의 SQL 실행 태스크를 포함하는 경우</span><span class="sxs-lookup"><span data-stu-id="164ab-108">For example, a package has a Sequence container that holds two Foreach Loop containers, and each container include two Execute SQL tasks.</span></span> <span data-ttu-id="164ab-109">시퀀스 컨테이너는 트랜잭션을 지원하지만 Foreach 루프 컨테이너는 지원하지 않고 SQL 실행 태스크는 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="164ab-109">The Sequence container supports transactions, the Foreach Loop containers do not, and the Execute SQL tasks do.</span></span> <span data-ttu-id="164ab-110">이 예에서 각 SQL 실행 태스크는 자체 트랜잭션을 시작하며 시퀀스 태스크에서 트랜잭션이 중단된 경우에도 롤백하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="164ab-110">In this example, each Execute SQL task would start its own transaction and would not roll back if the transaction on the Sequence task was aborted.</span></span>

 <span data-ttu-id="164ab-111">시퀀스 컨테이너, Foreach 루프 컨테이너 및 SQL 실행 태스크의 TransactionOption 속성은 다음과 같이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="164ab-111">The TransactionOption properties of the Sequence container, Foreach Loop container and the Execute SQL tasks are set as follows:</span></span>

-   <span data-ttu-id="164ab-112">시퀀스 컨테이너의 TransactionOption 속성은 **Required**로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="164ab-112">The TransactionOption property of the Sequence container is set to **Required**.</span></span>

-   <span data-ttu-id="164ab-113">Foreach 루프 컨테이너의 TransactionOption 속성은 **NotSupported**로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="164ab-113">The TransactionOption properties of the Foreach Loop containers are set to **NotSupported**.</span></span>

-   <span data-ttu-id="164ab-114">SQL 실행 태스크의 TransactionOption 속성은 **Required**로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="164ab-114">The TransactionOption properties of the Execute SQL tasks are set to **Required**.</span></span>

 <span data-ttu-id="164ab-115">다음 다이어그램에서는 패키지 내의 관련 없는 트랜잭션 다섯 개를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="164ab-115">The following diagram shows the five unrelated transactions in the package.</span></span> <span data-ttu-id="164ab-116">한 개의 트랜잭션은 시퀀스 컨테이너에서 시작되며 네 개의 트랜잭션은 SQL 실행 태스크에서 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="164ab-116">One transaction is started by the Sequence container and four transactions are started by the Execute SQL tasks.</span></span>

 <span data-ttu-id="164ab-117">![다중 트랜잭션 구현](media/mw-dts-trans2.gif "다중 트랜잭션 구현")</span><span class="sxs-lookup"><span data-stu-id="164ab-117">![Implementation of multiple transactions](media/mw-dts-trans2.gif "Implementation of multiple transactions")</span></span>

## <a name="related-tasks"></a><span data-ttu-id="164ab-118">관련 작업</span><span class="sxs-lookup"><span data-stu-id="164ab-118">Related Tasks</span></span>
 [<span data-ttu-id="164ab-119">트랜잭션을 사용하도록 패키지 구성</span><span class="sxs-lookup"><span data-stu-id="164ab-119">Configure a Package to Use Transactions</span></span>](../relational-databases/native-client-ole-db-transactions/transactions.md)


