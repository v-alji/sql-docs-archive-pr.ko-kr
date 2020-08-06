---
title: Integration Services 트랜잭션 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], transactions
- transactions [Integration Services], about transactions in packages
- tasks [Integration Services], transactions
- transactions [Integration Services]
ms.assetid: 3c78bb26-ddce-4831-a5f8-09d4f4fd53cc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5c0ee195bbcb7b9779111add4c1f2349816d5441
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651150"
---
# <a name="integration-services-transactions"></a><span data-ttu-id="87c06-102">Integration Services 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="87c06-102">Integration Services Transactions</span></span>
  <span data-ttu-id="87c06-103">패키지는 트랜잭션을 사용하여 태스크가 원자 단위로 수행되는 데이터베이스 동작을 바인딩하며 이를 통해 데이터 무결성을 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="87c06-103">Packages use transactions to bind the database actions that tasks perform into atomic units, and by doing this maintain data integrity.</span></span> <span data-ttu-id="87c06-104">패키지, For Loop, Foreach Loop, Sequence 컨테이너 및 각 작업을 캡슐화하는 태스크 호스트 등의 모든 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 컨테이너 유형은 트랜잭션을 사용하도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87c06-104">All [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] container types-packages, the For Loop, Foreach Loop, and Sequence containers, and the task hosts that encapsulate each task-can be configured to use transactions.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="87c06-105">는 트랜잭션 구성을 위해 **NotSupported**, **Supported**및 **Required**의 세 가지 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="87c06-105">provides three options for configuring transactions: **NotSupported**, **Supported**, and **Required**.</span></span>  
  
-   <span data-ttu-id="87c06-106">**Required** 는 부모 컨테이너가 이미 트랜잭션을 시작한 경우를 제외하고 컨테이너가 트랜잭션을 시작하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="87c06-106">**Required** indicates that the container starts a transaction, unless one is already started by its parent container.</span></span> <span data-ttu-id="87c06-107">트랜잭션이 이미 있는 경우 컨테이너는 해당 트랜잭션에 참여합니다.</span><span class="sxs-lookup"><span data-stu-id="87c06-107">If a transaction already exists, the container joins the transaction.</span></span> <span data-ttu-id="87c06-108">예를 들어 트랜잭션을 지원하도록 구성되지 않은 패키지가 **Required** 옵션을 사용하는 시퀀스 컨테이너를 포함하는 경우 시퀀스 컨테이너가 자체 트랜잭션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="87c06-108">For example, if a package that is not configured to support transactions includes a Sequence container that uses the **Required** option, the Sequence container would start its own transaction.</span></span> <span data-ttu-id="87c06-109">**Required** 옵션을 사용하도록 패키지를 구성한 경우 시퀀스 컨테이너는 패키지 트랜잭션에 참여합니다.</span><span class="sxs-lookup"><span data-stu-id="87c06-109">If the package were configured to use the **Required** option, the Sequence container would join the package transaction.</span></span>  
  
-   <span data-ttu-id="87c06-110">**Supported** 는 컨테이너가 트랜잭션을 시작하지 않고 부모 컨테이너에 의해 시작된 트랜잭션에 참여하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="87c06-110">**Supported** indicates that the container does not start a transaction, but joins any transaction started by its parent container.</span></span> <span data-ttu-id="87c06-111">예를 들어 4개의 SQL 실행 태스크가 있는 패키지가 트랜잭션을 시작하고 4개의 태스크가 모두 **Supported** 옵션을 사용하는 경우 하나의 태스크라도 실패하면 SQL 실행 태스크에 의해 수행되는 데이터베이스 업데이트가 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="87c06-111">For example, if a package with four Execute SQL tasks starts a transaction and all four tasks use the **Supported** option, the database updates performed by the Execute SQL tasks are rolled back if any task fails.</span></span> <span data-ttu-id="87c06-112">패키지가 트랜잭션을 시작하지 않은 경우 4개의 SQL 실행 태스크는 트랜잭션에 의해 바인드되지 않으며 실패한 태스크에 의해 수행된 것을 제외한 어떤 데이터베이스 업데이트도 롤백되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="87c06-112">If the package does not start a transaction, the four Execute SQL tasks are not bound by a transaction, and no database updates except the ones performed by the failed task are rolled back.</span></span>  
  
-   <span data-ttu-id="87c06-113">**NotSupported** 는 컨테이너가 트랜잭션을 시작하거나 기존 트랜잭션에 참여하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="87c06-113">**NotSupported** indicates that the container does not start a transaction or join an existing transaction.</span></span> <span data-ttu-id="87c06-114">부모 컨테이너에 의해 시작된 트랜잭션은 트랜잭션을 지원하지 않도록 구성된 자식 컨테이너에 영향을 미치지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="87c06-114">A transaction started by a parent container does not affect child containers that have been configured to not support transactions.</span></span> <span data-ttu-id="87c06-115">예를 들어 패키지가 트랜잭션을 시작하도록 구성되어 있고 패키지에 있는 For Loop 컨테이너가 **NotSupported** 옵션을 사용하는 경우 For Loop에 있는 모든 태스크는 실패하더라도 롤백될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="87c06-115">For example, if a package is configured to start a transaction and a For Loop container in the package uses the **NotSupported** option, none of the tasks in the For Loop can roll back if they fail.</span></span>  
  
 <span data-ttu-id="87c06-116">컨테이너에서 TransactionOption 속성을 설정하여 트랜잭션을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87c06-116">You configure transactions by setting the TransactionOption property on the container.</span></span> <span data-ttu-id="87c06-117">이 속성은 **의** 속성 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]창을 사용하여 설정하거나 프로그래밍 방식으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87c06-117">You can set this property by using the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], or you can set the property programmatically.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="87c06-118">`TransactionOption` 속성은 컨테이너에서 요청하는 `IsolationLevel` 속성 값의 적용 여부에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="87c06-118">The `TransactionOption` property influences whether or not the value of the `IsolationLevel` property requested by a container is applied.</span></span> <span data-ttu-id="87c06-119">자세한 내용은 `IsolationLevel` [패키지 속성 설정](set-package-properties.md)항목에서 속성에 대 한 설명을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="87c06-119">For more information, see the description of the `IsolationLevel` property in the topic, [Setting Package Properties](set-package-properties.md).</span></span>  
  
### <a name="to-configure-a-package-to-use-transactions"></a><span data-ttu-id="87c06-120">트랜잭션을 사용하도록 패키지를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="87c06-120">To configure a package to use transactions</span></span>  
  
-   [<span data-ttu-id="87c06-121">트랜잭션을 사용하도록 패키지 구성</span><span class="sxs-lookup"><span data-stu-id="87c06-121">Configure a Package to Use Transactions</span></span>](../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
## <a name="external-resources"></a><span data-ttu-id="87c06-122">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="87c06-122">External Resources</span></span>  
  
-   <span data-ttu-id="87c06-123"> www.mssqltips.com 의 블로그 항목 - [SQL Server Integration Services SSIS에서 트랜잭션을 사용하는 방법](https://go.microsoft.com/fwlink/?LinkId=157783)</span><span class="sxs-lookup"><span data-stu-id="87c06-123">Blog entry, [How to Use Transactions in SQL Server Integration Services SSIS](https://go.microsoft.com/fwlink/?LinkId=157783), on www.mssqltips.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87c06-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="87c06-124">See Also</span></span>  
 <span data-ttu-id="87c06-125">[상속 된 트랜잭션](../../2014/integration-services/inherited-transactions.md) </span><span class="sxs-lookup"><span data-stu-id="87c06-125">[Inherited Transactions](../../2014/integration-services/inherited-transactions.md) </span></span>  
 [<span data-ttu-id="87c06-126">여러 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="87c06-126">Multiple Transactions</span></span>](../../2014/integration-services/multiple-transactions.md)  
  
  
