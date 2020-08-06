---
title: Finance Name 정책 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 56b2c852-fd69-4cd2-9b5d-977467b94fd9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 44ffff45f126d2ad9b73c5b8410b8f89ad2b0604
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646958"
---
# <a name="create-the-finance-name-policy"></a><span data-ttu-id="dd799-102">Finance Name 정책 만들기</span><span class="sxs-lookup"><span data-stu-id="dd799-102">Create the Finance Name Policy</span></span>
  <span data-ttu-id="dd799-103"> 이 태스크에서는 Finance라는 데이터베이스를 만든 다음 모든 테이블이 **fintbl**로 시작하도록 지정하는 조건을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-103">In this task, you will create a database named Finance, and then create a condition that requires all tables to start with the letters **fintbl**.</span></span> <span data-ttu-id="dd799-104">그런 다음 Finance 데이터베이스의 테이블에 대한 명명 표준을 적용하는 정책 및 정책 범주를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-104">Then, you will create a policy and policy category to enforce a naming standard for tables in the Finance database.</span></span>  
  
### <a name="to-create-the-finance-database"></a><span data-ttu-id="dd799-105">Finance  데이터베이스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="dd799-105">To create the Finance database</span></span>  
  
1.  <span data-ttu-id="dd799-106">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 쿼리 창을 열고 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-106">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], open a query window and execute the following statement:</span></span>  
  
    ```  
    CREATE DATABASE Finance ;  
    GO  
    ```  
  
2.  <span data-ttu-id="dd799-107">개체 탐색기에서 **데이터베이스**를 클릭한 다음 F5 키를 눌러 데이터베이스 목록을 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-107">In Object Explorer, click **Databases**, and then press F5 to refresh the list of databases.</span></span>  
  
### <a name="to-create-the-finance-tables-condition"></a><span data-ttu-id="dd799-108">Finance  Tables  조건을 만들려면</span><span class="sxs-lookup"><span data-stu-id="dd799-108">To create the Finance Tables condition</span></span>  
  
1.  <span data-ttu-id="dd799-109">개체 탐색기에서 **관리**, **정책 관리**를 차례로 확장하고 **조건**을 마우스 오른쪽 단추로 클릭한 다음 **새 조건**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-109">In Object Explorer, expand **Management**, expand **Policy Management**, right-click **Conditions**, and then click **New Condition**.</span></span>  
  
2.  <span data-ttu-id="dd799-110">**새 조건 만들기** 대화 상자의 **이름** 상자에 **Finance Tables**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-110">In the **Create New Condition** dialog box, in the **Name** box, type **Finance Tables**.</span></span>  
  
3.  <span data-ttu-id="dd799-111">**패싯** 목록에서 **여러 부분으로 구성된 이름**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-111">In the **Facet** list, select **Multipart Name**.</span></span>  
  
4.  <span data-ttu-id="dd799-112">**식** 영역의 **필드** 상자에서 \*\* \@ 이름\*\*을 선택 하 고 **연산자** 상자에서 **Like**를 선택한 다음 **값** 상자에 **' fintbl% '** 를 입력 하 여 모든 테이블 이름이 문자 **fintbl**로 시작 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-112">In the **Expression** area, in the **Field** box, select **\@Name**; in the **Operator** box, select **Like**; and in the **Value** box, type **'fintbl%'** to force all table names to start with the letters **fintbl**.</span></span>  
  
5.  <span data-ttu-id="dd799-113">**설명** 페이지에서 **Finance table names must begin with fintbl**을 입력한 다음 **확인** 을 클릭하여 조건을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-113">On the **Description** page, type **Finance table names must begin with fintbl**, and then click **OK** to create the condition.</span></span>  
  
### <a name="to-create-the-finance-name-policy"></a><span data-ttu-id="dd799-114">Finance  Name  정책을 만들려면</span><span class="sxs-lookup"><span data-stu-id="dd799-114">To create the Finance Name policy</span></span>  
  
1.  <span data-ttu-id="dd799-115">개체 탐색기에서 **정책**을 마우스 오른쪽 단추로 클릭한 다음 **새 정책**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-115">In Object Explorer, right-click **Policies**, and then click **New Policy**.</span></span>  
  
2.  <span data-ttu-id="dd799-116">**새 정책 만들기** 대화 상자의 **이름** 상자에 **Finance Name**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-116">In the **Create New Policy** dialog box, in the **Name** box, type **Finance Name**.</span></span>  
  
3.  <span data-ttu-id="dd799-117">**조건 확인** 목록에서 **Finance Tables**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-117">In the **Check condition** list, select **Finance Tables**.</span></span> <span data-ttu-id="dd799-118">이는 **여러 부분으로 구성된 이름** 영역에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-118">This is in the **Multipart Name** area.</span></span>  
  
4.  <span data-ttu-id="dd799-119">**대상** 영역에 이 정책을 적용할 수 있는 데이터베이스 개체의 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-119">In the **Against** area you will see a list of the database objects that could apply this policy.</span></span> <span data-ttu-id="dd799-120">**매 테이블**확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-120">Select the check box for **Every Table**.</span></span>  
  
5.  <span data-ttu-id="dd799-121">**매 데이터베이스** 영역에서 **매**를 확장한 다음 **새 조건**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-121">In the **Every Database** area, expand **Every**, and then click **New condition**.</span></span>  
  
6.  <span data-ttu-id="dd799-122">**새 조건 만들기** 대화 상자의 **이름** 상자에 **Finance Database**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-122">In the **Create New Condition** dialog box, in the **Name** box, type **Finance Database**.</span></span>  
  
7.  <span data-ttu-id="dd799-123">**식** 상자에서 \*\* \@ Name = ' 재무 '\*\* 를 포함 하도록 식을 완성 한 다음 **확인** 을 클릭 하 여 조건 페이지를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-123">In the **Expression** box, complete the expression to include **\@Name = 'Finance'**, and then click **OK** to close the condition page.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dd799-124">**값** 상자에서 Tab 키를 눌러 **확인** 단추를 활성화해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-124">You might have to tab out of the **Value** box to enable the **OK** button.</span></span>  
  
8.  <span data-ttu-id="dd799-125">**평가 모드** 목록에서 **변경 시: 방지**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-125">In the **Evaluation Mode** list, select **On change: prevent**.</span></span> <span data-ttu-id="dd799-126">이렇게 하면 Finance 데이터베이스에 대한 데이터베이스 트리거를 만들어 정책을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-126">This will enforce the policy by creating a database trigger on the Finance database.</span></span>  
  
9. <span data-ttu-id="dd799-127">**사용** 목록을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-127">Select the **Enabled** list.</span></span> <span data-ttu-id="dd799-128">**사용** 상자는 **요청 시** 정책에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-128">(The **Enabled** box does not apply to **On demand** policies.)</span></span>  
  
10. <span data-ttu-id="dd799-129">**서버 제한** 목록에서 **없음**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-129">In the **Server restriction** list, select **None**.</span></span>  
  
11. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-create-the-finance-policy-category"></a><span data-ttu-id="dd799-130">Finance  정책 범주를 만들려면</span><span class="sxs-lookup"><span data-stu-id="dd799-130">To create the Finance policy category</span></span>  
  
1.  <span data-ttu-id="dd799-131">개체 탐색기에서 **관리**를 확장하고 **정책 관리**를 마우스 오른쪽 단추로 클릭한 다음 **범주 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-131">In Object Explorer, expand **Management**, right-click **Policy Management**, and then click **Manage Categories**.</span></span>  
  
2.  <span data-ttu-id="dd799-132">**정책 범주 관리** 대화 상자의 **이름**에서 `Finance` 빈 상자에를 입력 한 다음 **데이터베이스 구독 위임**의 선택을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-132">In the **Manage Policy Categories** dialog box, under **Name**, type `Finance` in the blank box, and then clear **Mandate Database Subscriptions**.</span></span> <span data-ttu-id="dd799-133">**데이터베이스 구독 위임** 을 선택하면 해당 인스턴스에 있는 모든 데이터베이스가 이 정책 범주에 속하는 정책을 구독하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-133">**Mandate Database Subscriptions** will force every database in the instance to subscribe to the policies that belong to this policy category.</span></span> <span data-ttu-id="dd799-134">따라서 Finance 데이터베이스만 Finance Name 정책을 구독해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd799-134">For this lesson, only the Finance database should subscribe to the Finance Name policy.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="dd799-135">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="dd799-135">Next Task in Lesson</span></span>  
 [<span data-ttu-id="dd799-136">Finance Name 정책 구독 및 확인</span><span class="sxs-lookup"><span data-stu-id="dd799-136">Subscribe to and Check the Finance Name Policy</span></span>](lesson-2-2-subscribe-to-and-check-the-finance-name-policy.md)  
  
  
