---
title: Finance Name 정책 구독 및 확인 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 126b4c4c-2a1c-4701-a0ad-8de23fbd7306
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2bfe6f463d03fe8b95f000dc6f34dc0718a7729f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646388"
---
# <a name="subscribe-to-and-check-the-finance-name-policy"></a><span data-ttu-id="7b313-102">Finance Name 정책 구독 및 확인</span><span class="sxs-lookup"><span data-stu-id="7b313-102">Subscribe to and Check the Finance Name Policy</span></span>
  <span data-ttu-id="7b313-103">이 태스크에서는 Finance 데이터베이스에서 Finance 정책 범주를 구독하도록 구성한 다음</span><span class="sxs-lookup"><span data-stu-id="7b313-103">In this task, you will configure the Finance database to subscribe to the Finance policy category.</span></span> <span data-ttu-id="7b313-104">Finance Name 정책을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="7b313-104">Then, you will test the Finance Name policy.</span></span>  
  
### <a name="to-subscribe-to-the-finance-policy-category"></a><span data-ttu-id="7b313-105">Finance 정책 범주를 구독하려면</span><span class="sxs-lookup"><span data-stu-id="7b313-105">To subscribe to the Finance policy category</span></span>  
  
1.  <span data-ttu-id="7b313-106">개체 탐색기에서 **데이터베이스**를 확장 하 고,를 마우스 오른쪽 단추로 클릭 `Finance` 하 고 **정책**을 가리킨 다음 **범주**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b313-106">In Object Explorer, expand **Databases**, right-click `Finance`, point to **Policies**, and then click **Categories**.</span></span>  
  
2.  <span data-ttu-id="7b313-107">범주에 대 한 **구독** 확인란을 선택 합니다 `Finance` .</span><span class="sxs-lookup"><span data-stu-id="7b313-107">Select the **Subscribed** checkbox for the `Finance` category.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-test-the-enforcement-of-the-finance-name-policy"></a><span data-ttu-id="7b313-108">Finance Name 정책 적용을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="7b313-108">To test the enforcement of the Finance Name policy</span></span>  
  
1.  <span data-ttu-id="7b313-109">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 쿼리 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7b313-109">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], open a query window.</span></span> <span data-ttu-id="7b313-110">**Finance Name** 정책을 위반하는 테이블을 만들려고 하는 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7b313-110">Execute the following statements that try to create a table that violates the **Finance Name** policy.</span></span> <span data-ttu-id="7b313-111">테이블 이름이 **fintbl**로 시작하지 않으므로 해당 테이블이 정책을 위반합니다.</span><span class="sxs-lookup"><span data-stu-id="7b313-111">The table violates the policy because the table name does not begin with the letters **fintbl**.</span></span>  
  
    ```  
    USE Finance ;  
    GO  
    CREATE TABLE NewTable  
    (Col1 int) ;  
    GO  
  
    ```  
  
     <span data-ttu-id="7b313-112">정책에서 테이블 생성을 금지하고 정책 이름을 제공하는 정보 메시지를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7b313-112">Notice that the policy prevents the table from being created and returns an informational message that provides the policy name.</span></span>  
  
2.  <span data-ttu-id="7b313-113">올바른 이름을 제공하려면 다음과 같이 코드를 수정하고 문을 다시 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7b313-113">To provide a valid name, modify the code as follows and run the statement again.</span></span>  
  
    ```  
    USE Finance ;  
    GO  
    CREATE TABLE fintblNewTable  
    (Col1 int) ;  
    GO  
  
    ```  
  
     <span data-ttu-id="7b313-114">이번에는 테이블이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="7b313-114">This time, the table is created.</span></span>  
  
### <a name="to-apply-the-policy-to-the-whole-server"></a><span data-ttu-id="7b313-115">전체 서버에 정책을 적용하려면</span><span class="sxs-lookup"><span data-stu-id="7b313-115">To apply the policy to the whole server</span></span>  
  
1.  <span data-ttu-id="7b313-116">현재 Finance 데이터베이스만 Finance 정책 범주를 구독합니다.</span><span class="sxs-lookup"><span data-stu-id="7b313-116">Currently, only the Finance database subscribes to the Finance policy category.</span></span> <span data-ttu-id="7b313-117">전체 서버에 정책 범주를 적용하는 것이 더 간단한 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="7b313-117">In many cases, it is easier to apply the policy category to the whole server.</span></span> <span data-ttu-id="7b313-118">개체 탐색기에서 **관리**를 확장하고 **정책 관리**를 마우스 오른쪽 단추로 클릭한 다음 **범주 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b313-118">In Object Explorer, expand **Management**, right-click **Policy Management**, and then click **Manage Categories**.</span></span>  
  
2.  <span data-ttu-id="7b313-119">**정책 범주 관리** 대화 상자에서 Finance 범주를 찾고 Finance 범주에 대해 **데이터베이스 구독 위임** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7b313-119">In the **Manage Policy Categories** dialog box, locate the Finance category, and select the **Mandate Database Subscriptions** checkbox for the Finance category.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] <span data-ttu-id="7b313-120">이제 Finance 범주가 모든 데이터베이스에 적용되지만 만든 조건으로 인해 Finance Name 정책이 Finance 데이터베이스로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b313-120">Now the Finance category applies to all databases, but the condition that you have created restricts the Finance Name policy to the Finance database.</span></span> <span data-ttu-id="7b313-121">이는 대상 정책에 대해 복합적으로 연결된 조건을 많은 서버에 올바르게 적용되는 방식으로 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7b313-121">This shows how you can use complex combinations of conditions to target policies in ways that will apply correctly on many servers.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="7b313-122">요약</span><span class="sxs-lookup"><span data-stu-id="7b313-122">Summary</span></span>  
 <span data-ttu-id="7b313-123">이 자습서에서는 정책 기반 관리 조건, 정책 및 정책 그룹을 만드는 방법과 필터를 적용하고 정책 기반 관리 대상의 조건 준수 여부를 검사하는 방법을 살펴보았습니다.</span><span class="sxs-lookup"><span data-stu-id="7b313-123">This tutorial has shown you how to create Policy-Based Management conditions, policies and policy groups, and how to apply filters and check the compliance of Policy-Based Management targets.</span></span>  
  
## <a name="next"></a><span data-ttu-id="7b313-124">다음</span><span class="sxs-lookup"><span data-stu-id="7b313-124">Next</span></span>  
 <span data-ttu-id="7b313-125">이 자습서를 마칩니다.</span><span class="sxs-lookup"><span data-stu-id="7b313-125">This tutorial is finished.</span></span> <span data-ttu-id="7b313-126">시작 부분으로 돌아가려면 [자습서: 정책 기반 관리를 사용하여 서버 관리](tutorial-administering-servers-by-using-policy-based-management.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7b313-126">To return to the start, click [Tutorial: Administering Servers by Using Policy-Based Management](tutorial-administering-servers-by-using-policy-based-management.md).</span></span>  
  
 <span data-ttu-id="7b313-127">자습서 목록은 [SQL Server 2014에 대 한 자습서](../../tutorials/tutorials-for-sql-server-2014.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7b313-127">For a list of tutorials, see [Tutorials for SQL Server 2014](../../tutorials/tutorials-for-sql-server-2014.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b313-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7b313-128">See Also</span></span>  
 [<span data-ttu-id="7b313-129">정책 기반 관리를 사용하여 서버 관리</span><span class="sxs-lookup"><span data-stu-id="7b313-129">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
