---
title: '작업 6: 마스터 데이터 관리자 |를 사용 하 여 도메인 기반 특성이 생성 되었는지 확인 Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6e90517a-910c-4c33-8f11-92ac3cff4fdc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ea26202ca9e607058b1e385957be3ea3d04038b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639143"
---
# <a name="task-6-verify-that-the-domain-based-attribute-is-created-using-master-data-manager"></a><span data-ttu-id="6c0e4-102">태스크 6: 마스터 데이터 관리자를 사용하여 도메인 기반 특성이 생성되었는지 확인</span><span class="sxs-lookup"><span data-stu-id="6c0e4-102">Task 6: Verify that the Domain-Based Attribute is Created using Master Data Manager</span></span>
  <span data-ttu-id="6c0e4-103">이 작업에서는 **마스터 데이터 관리자** 를 사용해서 **State** 엔터티가 **MDS** 에 만들어졌고 **Supplier** 엔터티의 **State** 특성이 **State**엔터티에 종속된 도메인 기반 특성인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-103">In this task, you verify that the **State** entity is created in **MDS** and the **State** attribute of the **Supplier** entity is a domain-based attribute that depends on the **State** entity by using **Master Data Manager**.</span></span>

1.  <span data-ttu-id="6c0e4-104">**마스터 데이터 관리자** 웹 애플리케이션으로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-104">Switch to the **Master Data Manger** web application.</span></span>

2.  <span data-ttu-id="6c0e4-105">상단에서 **SQL Server 2012 Master Data Services** 를 클릭하여 홈 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-105">Click **SQL Server 2012 Master Data Services** at the top to get to the home page.</span></span>

3.  <span data-ttu-id="6c0e4-106">**Suppliers** 모델이 선택되었는지 확인하고 **탐색기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-106">Ensure that **Suppliers** model is selected and click **Explorer**.</span></span> <span data-ttu-id="6c0e4-107">**탐색기** 가 이미 열려 있으면 페이지를 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-107">You could refresh the page if you already had **Explorer** open.</span></span>

4.  <span data-ttu-id="6c0e4-108">메뉴 모음에서 **엔터티** 위로 마우스를 가져가고 **Supplier** 및 **State**엔터티가 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-108">Hover your mouse over **Entities** on the menu bar and notice that now there are two entities: **Supplier** and **State**.</span></span>

     <span data-ttu-id="6c0e4-109">![상태 및 공급자가 있는 엔터티 메뉴](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-01.jpg "상태 및 공급자가 있는 엔터티 메뉴")</span><span class="sxs-lookup"><span data-stu-id="6c0e4-109">![Entities Menu with State and Supplier](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-01.jpg "Entities Menu with State and Supplier")</span></span>

5.  <span data-ttu-id="6c0e4-110">**State** 엔터티가 아직 열리지 않았으면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-110">Click **State** if the entity is not open already.</span></span>

6.  <span data-ttu-id="6c0e4-111">목록에서 **GA** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-111">Select **GA** from the list.</span></span>

7.  <span data-ttu-id="6c0e4-112">오른쪽 **세부 정보** 창의 **오른쪽 창** 에서 **이름** 을 **Georgia**로 변경하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-112">In the **Details** pane to the right, change the **Name** to **Georgia** in the **right pane**, and click **OK**.</span></span>

8.  <span data-ttu-id="6c0e4-113">다른 지역에 대해서도 위 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-113">Repeat the previous steps for other states.</span></span>

    |<span data-ttu-id="6c0e4-114">코드</span><span class="sxs-lookup"><span data-stu-id="6c0e4-114">Code</span></span>|<span data-ttu-id="6c0e4-115">이름</span><span class="sxs-lookup"><span data-stu-id="6c0e4-115">Name</span></span>|
    |----------|----------|
    |<span data-ttu-id="6c0e4-116">CA</span><span class="sxs-lookup"><span data-stu-id="6c0e4-116">CA</span></span>|<span data-ttu-id="6c0e4-117">캘리포니아</span><span class="sxs-lookup"><span data-stu-id="6c0e4-117">California</span></span>|
    |<span data-ttu-id="6c0e4-118">CO</span><span class="sxs-lookup"><span data-stu-id="6c0e4-118">CO</span></span>|<span data-ttu-id="6c0e4-119">Colorado</span><span class="sxs-lookup"><span data-stu-id="6c0e4-119">Colorado</span></span>|
    |<span data-ttu-id="6c0e4-120">IL</span><span class="sxs-lookup"><span data-stu-id="6c0e4-120">IL</span></span>|<span data-ttu-id="6c0e4-121">일리노이</span><span class="sxs-lookup"><span data-stu-id="6c0e4-121">Illinois</span></span>|
    |<span data-ttu-id="6c0e4-122">DC</span><span class="sxs-lookup"><span data-stu-id="6c0e4-122">DC</span></span>|<span data-ttu-id="6c0e4-123">District of Columbia</span><span class="sxs-lookup"><span data-stu-id="6c0e4-123">District of Columbia</span></span>|
    |<span data-ttu-id="6c0e4-124">FL</span><span class="sxs-lookup"><span data-stu-id="6c0e4-124">FL</span></span>|<span data-ttu-id="6c0e4-125">Florida</span><span class="sxs-lookup"><span data-stu-id="6c0e4-125">Florida</span></span>|
    |<span data-ttu-id="6c0e4-126">AL</span><span class="sxs-lookup"><span data-stu-id="6c0e4-126">AL</span></span>|<span data-ttu-id="6c0e4-127">Alabama</span><span class="sxs-lookup"><span data-stu-id="6c0e4-127">Alabama</span></span>|
    |<span data-ttu-id="6c0e4-128">KY</span><span class="sxs-lookup"><span data-stu-id="6c0e4-128">KY</span></span>|<span data-ttu-id="6c0e4-129">Kentucky</span><span class="sxs-lookup"><span data-stu-id="6c0e4-129">Kentucky</span></span>|
    |<span data-ttu-id="6c0e4-130">MA</span><span class="sxs-lookup"><span data-stu-id="6c0e4-130">MA</span></span>|<span data-ttu-id="6c0e4-131">Massachusetts</span><span class="sxs-lookup"><span data-stu-id="6c0e4-131">Massachusetts</span></span>|
    |<span data-ttu-id="6c0e4-132">AZ</span><span class="sxs-lookup"><span data-stu-id="6c0e4-132">AZ</span></span>|<span data-ttu-id="6c0e4-133">Arizona</span><span class="sxs-lookup"><span data-stu-id="6c0e4-133">Arizona</span></span>|
    |<span data-ttu-id="6c0e4-134">MI</span><span class="sxs-lookup"><span data-stu-id="6c0e4-134">MI</span></span>|<span data-ttu-id="6c0e4-135">Michigan</span><span class="sxs-lookup"><span data-stu-id="6c0e4-135">Michigan</span></span>|
    |<span data-ttu-id="6c0e4-136">MN</span><span class="sxs-lookup"><span data-stu-id="6c0e4-136">MN</span></span>|<span data-ttu-id="6c0e4-137">Minnesota</span><span class="sxs-lookup"><span data-stu-id="6c0e4-137">Minnesota</span></span>|
    |<span data-ttu-id="6c0e4-138">NJ</span><span class="sxs-lookup"><span data-stu-id="6c0e4-138">NJ</span></span>|<span data-ttu-id="6c0e4-139">New Jersey</span><span class="sxs-lookup"><span data-stu-id="6c0e4-139">New Jersey</span></span>|
    |<span data-ttu-id="6c0e4-140">NV</span><span class="sxs-lookup"><span data-stu-id="6c0e4-140">NV</span></span>|<span data-ttu-id="6c0e4-141">Nevada</span><span class="sxs-lookup"><span data-stu-id="6c0e4-141">Nevada</span></span>|
    |<span data-ttu-id="6c0e4-142">NY</span><span class="sxs-lookup"><span data-stu-id="6c0e4-142">NY</span></span>|<span data-ttu-id="6c0e4-143">뉴욕</span><span class="sxs-lookup"><span data-stu-id="6c0e4-143">New York</span></span>|
    |<span data-ttu-id="6c0e4-144">OH</span><span class="sxs-lookup"><span data-stu-id="6c0e4-144">OH</span></span>|<span data-ttu-id="6c0e4-145">Ohio</span><span class="sxs-lookup"><span data-stu-id="6c0e4-145">Ohio</span></span>|
    |<span data-ttu-id="6c0e4-146">정상</span><span class="sxs-lookup"><span data-stu-id="6c0e4-146">OK</span></span>|<span data-ttu-id="6c0e4-147">Oklahoma</span><span class="sxs-lookup"><span data-stu-id="6c0e4-147">Oklahoma</span></span>|
    |<span data-ttu-id="6c0e4-148">또는</span><span class="sxs-lookup"><span data-stu-id="6c0e4-148">OR</span></span>|<span data-ttu-id="6c0e4-149">Oregon</span><span class="sxs-lookup"><span data-stu-id="6c0e4-149">Oregon</span></span>|
    |<span data-ttu-id="6c0e4-150">PA</span><span class="sxs-lookup"><span data-stu-id="6c0e4-150">PA</span></span>|<span data-ttu-id="6c0e4-151">Pennsylvania</span><span class="sxs-lookup"><span data-stu-id="6c0e4-151">Pennsylvania</span></span>|
    |<span data-ttu-id="6c0e4-152">SC</span><span class="sxs-lookup"><span data-stu-id="6c0e4-152">SC</span></span>|<span data-ttu-id="6c0e4-153">South Carolina</span><span class="sxs-lookup"><span data-stu-id="6c0e4-153">South Carolina</span></span>|
    |<span data-ttu-id="6c0e4-154">KS</span><span class="sxs-lookup"><span data-stu-id="6c0e4-154">KS</span></span>|<span data-ttu-id="6c0e4-155">Kansas</span><span class="sxs-lookup"><span data-stu-id="6c0e4-155">Kansas</span></span>|
    |<span data-ttu-id="6c0e4-156">TN</span><span class="sxs-lookup"><span data-stu-id="6c0e4-156">TN</span></span>|<span data-ttu-id="6c0e4-157">Tennessee</span><span class="sxs-lookup"><span data-stu-id="6c0e4-157">Tennessee</span></span>|
    |<span data-ttu-id="6c0e4-158">TX</span><span class="sxs-lookup"><span data-stu-id="6c0e4-158">TX</span></span>|<span data-ttu-id="6c0e4-159">텍사스</span><span class="sxs-lookup"><span data-stu-id="6c0e4-159">Texas</span></span>|
    |<span data-ttu-id="6c0e4-160">UT</span><span class="sxs-lookup"><span data-stu-id="6c0e4-160">UT</span></span>|<span data-ttu-id="6c0e4-161">Utah</span><span class="sxs-lookup"><span data-stu-id="6c0e4-161">Utah</span></span>|
    |<span data-ttu-id="6c0e4-162">VA</span><span class="sxs-lookup"><span data-stu-id="6c0e4-162">VA</span></span>|<span data-ttu-id="6c0e4-163">버지니아</span><span class="sxs-lookup"><span data-stu-id="6c0e4-163">Virginia</span></span>|
    |<span data-ttu-id="6c0e4-164">WA</span><span class="sxs-lookup"><span data-stu-id="6c0e4-164">WA</span></span>|<span data-ttu-id="6c0e4-165">워싱턴</span><span class="sxs-lookup"><span data-stu-id="6c0e4-165">Washington</span></span>|
    |<span data-ttu-id="6c0e4-166">WI</span><span class="sxs-lookup"><span data-stu-id="6c0e4-166">WI</span></span>|<span data-ttu-id="6c0e4-167">Wisconsin</span><span class="sxs-lookup"><span data-stu-id="6c0e4-167">Wisconsin</span></span>|
    |<span data-ttu-id="6c0e4-168">HI</span><span class="sxs-lookup"><span data-stu-id="6c0e4-168">HI</span></span>|<span data-ttu-id="6c0e4-169">Hawaii</span><span class="sxs-lookup"><span data-stu-id="6c0e4-169">Hawaii</span></span>|
    |<span data-ttu-id="6c0e4-170">MD</span><span class="sxs-lookup"><span data-stu-id="6c0e4-170">MD</span></span>|<span data-ttu-id="6c0e4-171">Maryland</span><span class="sxs-lookup"><span data-stu-id="6c0e4-171">Maryland</span></span>|
    |<span data-ttu-id="6c0e4-172">CT</span><span class="sxs-lookup"><span data-stu-id="6c0e4-172">CT</span></span>|<span data-ttu-id="6c0e4-173">Connecticut</span><span class="sxs-lookup"><span data-stu-id="6c0e4-173">Connecticut</span></span>|

9. <span data-ttu-id="6c0e4-174">State 엔터티 중 하나를 선택하고 도구 모음에서 **트랜잭션 보기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-174">Select any of the state entries and click **View Transactions** from the Toolbar.</span></span> <span data-ttu-id="6c0e4-175">방금 만든 업데이트에 대한 트랜잭션이 트랜잭션 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-175">You should see the transaction for the update you just made is in the list of transactions.</span></span>

10. <span data-ttu-id="6c0e4-176">**엔터티** 메뉴 위로 마우스를 가져가고 **Supplier**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-176">Hover the mouse over **Entities** menu and click **Supplier**.</span></span>

11. <span data-ttu-id="6c0e4-177">이제는 **세부 정보** 창에서 드롭 다운 목록을 사용해서 **State** 필드의 값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-177">Now, notice that a value for the **State** field can be changed in the **Details** pane by using the drop-down list.</span></span> <span data-ttu-id="6c0e4-178">또한 왼쪽 목록과 **세부 정보** 창의 드롭 다운 목록에는 코드와 이름이 중괄호로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-178">You can also see that, in the list to the left and in the drop-down list in the **Details** pane, code is displayed first and then the name in curly braces.</span></span> <span data-ttu-id="6c0e4-179">또한 **세부 정보** 창의 다른 값도 모두 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-179">You can also change any other value in the **Details** pane.</span></span>

     <span data-ttu-id="6c0e4-180">![코드 및 이름이 업데이트된 상태 특성](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-02.jpg "코드 및 이름이 업데이트된 상태 특성")</span><span class="sxs-lookup"><span data-stu-id="6c0e4-180">![State Attribute with Updated Code and Names](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-02.jpg "State Attribute with Updated Code and Names")</span></span>

## <a name="next-step"></a><span data-ttu-id="6c0e4-181">다음 단계</span><span class="sxs-lookup"><span data-stu-id="6c0e4-181">Next Step</span></span>
 [<span data-ttu-id="6c0e4-182">태스크 7: Excel에서 마스터 데이터 관리자를 사용하여 수행된 업데이트 보기</span><span class="sxs-lookup"><span data-stu-id="6c0e4-182">Task 7: Viewing Updates Made using Master Data Manager in Excel</span></span>](../../2014/tutorials/task-7-viewing-updates-made-using-master-data-manager-in-excel.md)


