---
title: 트랜잭션을 사용 하도록 패키지 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Integration Services], configuring packages to use
ms.assetid: 8bf14957-27b4-456b-81d9-e1a0e0ca94b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f469c2439deb2d16ac9046a1628e82c34e39b31d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729720"
---
# <a name="configure-a-package-to-use-transactions"></a><span data-ttu-id="41271-102">트랜잭션을 사용하도록 패키지 구성</span><span class="sxs-lookup"><span data-stu-id="41271-102">Configure a Package to Use Transactions</span></span>
  <span data-ttu-id="41271-103">트랜잭션을 사용하도록 패키지를 구성할 때는 다음과 같은 두 가지 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41271-103">When you configure a package to use transactions, you have two options:</span></span>  
  
-   <span data-ttu-id="41271-104">패키지에서 단일 트랜잭션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-104">Have a single transaction for the package.</span></span> <span data-ttu-id="41271-105">이 경우 패키지 자체에서 이 트랜잭션을 *시작하고* 패키지에 포함된 개별 태스크와 컨테이너는 이 단일 트랜잭션에 참여합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-105">In this case, it is the package itself that *initiates* this transaction, whereas individual tasks and containers in the package participate in this single transaction.</span></span>  
  
-   <span data-ttu-id="41271-106">패키지에서 여러 트랜잭션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-106">Have multiple transactions in the package.</span></span> <span data-ttu-id="41271-107">이 경우 패키지가 트랜잭션을 지원하지만 실제로는 패키지에 포함된 개별 태스크와 컨테이너가 트랜잭션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-107">In this case, the package supports transactions, but individual tasks and containers in the package actually initiate the transactions.</span></span>  
  
 <span data-ttu-id="41271-108">다음 절차에서는 위의 두 옵션을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-108">The following procedures describe how to configure both options.</span></span>  
  
## <a name="configuring-a-single-transaction"></a><span data-ttu-id="41271-109">단일 트랜잭션 구성</span><span class="sxs-lookup"><span data-stu-id="41271-109">Configuring a Single Transaction</span></span>  
 <span data-ttu-id="41271-110">이 옵션에서는 패키지 자체에서 단일 트랜잭션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-110">In this option, the package itself initiates a single transaction.</span></span> <span data-ttu-id="41271-111">패키지의 TransactionOption 속성을로 설정 하 여이 트랜잭션을 시작 하도록 패키지를 구성 합니다 `Required` .</span><span class="sxs-lookup"><span data-stu-id="41271-111">You configure the package to initiate this transaction by setting the TransactionOption property of the package to `Required`.</span></span>  
  
 <span data-ttu-id="41271-112">그런 다음 이 단일 트랜잭션에 특정 태스크와 컨테이너를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-112">Next, you enlist specific tasks and containers in this single transaction.</span></span> <span data-ttu-id="41271-113">트랜잭션에 태스크 또는 컨테이너를 등록 하려면 해당 태스크 또는 컨테이너의 TransactionOption 속성을로 설정 `Supported` 합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-113">To enlist a task or container in a transaction, you set the TransactionOption property of that task or container to `Supported`.</span></span>  
  
#### <a name="to-configure-a-package-to-use-a-single-transaction"></a><span data-ttu-id="41271-114">단일 트랜잭션을 사용하도록 패키지를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="41271-114">To configure a package to use a single transaction</span></span>  
  
1.  <span data-ttu-id="41271-115">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 트랜잭션을 사용하도록 구성할 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="41271-115">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want to configure to use a transaction.</span></span>  
  
2.  <span data-ttu-id="41271-116">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="41271-116">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="41271-117">**제어 흐름** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-117">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="41271-118">제어 흐름 디자인 화면 배경의 아무 위치나 마우스 오른쪽 단추로 클릭한 후 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-118">Right-click anywhere in the background of the control flow design surface, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="41271-119">**속성** 창에서 TransactionOption 속성을로 설정 `Required` 합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-119">In the **Properties** window, set the TransactionOption property to `Required`.</span></span>  
  
6.  <span data-ttu-id="41271-120">**제어 흐름** 탭의 디자인 화면에서 트랜잭션에 등록할 태스크 또는 컨테이너를 마우스 오른쪽 단추로 클릭한 후 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-120">On the design surface of the **ControlFlow** tab, right-click the task or the container that you want to enroll in the transaction, and then click **Properties**.</span></span>  
  
7.  <span data-ttu-id="41271-121">**속성** 창에서 TransactionOption 속성을로 설정 `Supported` 합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-121">In the **Properties** window, set the TransactionOption property to `Supported`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="41271-122">트랜잭션에 연결을 참여시키려면 트랜잭션에서 해당 연결을 사용하는 태스크를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-122">To enlist a connection in a transaction, enroll the tasks that use the connection in the transaction.</span></span> <span data-ttu-id="41271-123">자세한 내용은 [Integration Services&#40;SSIS&#41; 연결](connection-manager/integration-services-ssis-connections.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41271-123">For more information, see [Integration Services &#40;SSIS&#41; Connections](connection-manager/integration-services-ssis-connections.md).</span></span>  
  
8.  <span data-ttu-id="41271-124">트랜잭션에 등록할 각 태스크와 컨테이너에 대해 6-7단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-124">Repeat steps 6 and 7 for each task and container that you want to enroll in the transaction.</span></span>  
  
## <a name="configuring-multiple-transactions"></a><span data-ttu-id="41271-125">여러 트랜잭션 구성</span><span class="sxs-lookup"><span data-stu-id="41271-125">Configuring Multiple Transactions</span></span>  
 <span data-ttu-id="41271-126">이 옵션에서는 패키지 자체에서 트랜잭션을 지원하지만 트랜잭션을 시작하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41271-126">In this option, the package itself supports transactions but does not start a transaction.</span></span> <span data-ttu-id="41271-127">패키지의 TransactionOption 속성을로 설정 하 여 트랜잭션을 지원 하도록 패키지를 구성 `Supported` 합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-127">You configure the package to support transactions by setting the TransactionOption property of the package to `Supported`.</span></span>  
  
 <span data-ttu-id="41271-128">그런 다음 패키지에 포함된 태스크와 컨테이너 중에서 원하는 태스크와 컨테이너를 트랜잭션을 시작하거나 트랜잭션에 참여하도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-128">Next, you configure the desired tasks and containers inside the package to initiate or participate in transactions.</span></span> <span data-ttu-id="41271-129">트랜잭션을 시작 하도록 태스크 나 컨테이너를 구성 하려면 해당 태스크 또는 컨테이너의 TransactionOption 속성을로 설정 `Required` 합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-129">To configure a task or container to initiate a transaction, you set the TransactionOption property of that task or container to `Required`.</span></span>  
  
#### <a name="to-configure-a-package-to-use-multiple-transactions"></a><span data-ttu-id="41271-130">여러 트랜잭션을 사용하도록 패키지를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="41271-130">To configure a package to use multiple transactions</span></span>  
  
1.  <span data-ttu-id="41271-131">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 트랜잭션을 사용하도록 구성할 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="41271-131">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want to configure to use transaction.s</span></span>  
  
2.  <span data-ttu-id="41271-132">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="41271-132">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="41271-133">**제어 흐름** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-133">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="41271-134">제어 흐름 디자인 화면 배경의 아무 위치나 마우스 오른쪽 단추로 클릭한 후 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-134">Right-click anywhere in the background of the control flow design surface, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="41271-135">**속성** 창에서 TransactionOption 속성을로 설정 `Supported` 합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-135">In the **Properties** window, set the TransactionOption property to `Supported`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="41271-136">패키지는 트랜잭션을 지원하지만 트랜잭션은 패키지의 태스크나 컨테이너에 의해 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="41271-136">The package supports transactions, but the transactions are started by task or containers in the package.</span></span>  
  
6.  <span data-ttu-id="41271-137">**제어 흐름** 탭의 디자인 화면에서 트랜잭션을 시작할 패키지에서 태스크 또는 컨테이너를 마우스 오른쪽 단추로 클릭한 후 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-137">On the design surface of the **ControlFlow** tab, right-click the task or the container in the package for which you want to start a transaction, and then click **Properties**.</span></span>  
  
7.  <span data-ttu-id="41271-138">**속성** 창에서 TransactionOption 속성을로 설정 `Required` 합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-138">In the **Properties** window, set the TransactionOption property to `Required`.</span></span>  
  
8.  <span data-ttu-id="41271-139">트랜잭션이 컨테이너에 의해 시작되는 경우 트랜잭션에 등록할 태스크 또는 컨테이너를 마우스 오른쪽 단추로 클릭한 후 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-139">If a transaction is started by a container, right-click the task or the container that you want to enroll in the transaction, and then click **Properties**.</span></span>  
  
9. <span data-ttu-id="41271-140">**속성** 창에서 TransactionOption 속성을로 설정 `Supported` 합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-140">In the **Properties** window, set the TransactionOption property to `Supported`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="41271-141">트랜잭션에 연결을 참여시키려면 트랜잭션에서 해당 연결을 사용하는 태스크를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-141">To enlist a connection in a transaction, enroll the tasks that use the connection in the transaction.</span></span> <span data-ttu-id="41271-142">자세한 내용은 [Integration Services&#40;SSIS&#41; 연결](connection-manager/integration-services-ssis-connections.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41271-142">For more information, see [Integration Services &#40;SSIS&#41; Connections](connection-manager/integration-services-ssis-connections.md).</span></span>  
  
10. <span data-ttu-id="41271-143">트랜잭션을 시작하는 각 태스크와 컨테이너에 대해 6-9단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="41271-143">Repeat steps 6 through 9 for each task and container that starts a transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41271-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="41271-144">See Also</span></span>  
 [<span data-ttu-id="41271-145">Integration Services 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="41271-145">Integration Services Transactions</span></span>](integration-services-transactions.md)  
  
  
