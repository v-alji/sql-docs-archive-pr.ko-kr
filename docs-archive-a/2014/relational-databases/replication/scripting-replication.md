---
title: 복제 스크립팅 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server replication], replication objects
- merge replication scripting [SQL Server replication]
- replication [SQL Server], scripting
- snapshot replication [SQL Server], scripting
- scripts [SQL Server replication]
- transactional replication, scripting
ms.assetid: e50fac44-54c0-470c-a4ea-9c111fa4322b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2e865e2664a399bca4738c1fc157bef176f35e96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646311"
---
# <a name="scripting-replication"></a><span data-ttu-id="2305c-102">복제 스크립팅</span><span class="sxs-lookup"><span data-stu-id="2305c-102">Scripting Replication</span></span>
  <span data-ttu-id="2305c-103">토폴로지의 모든 복제 구성 요소는 재해 복구 계획의 일부로 스크립팅되어야 하며 반복 태스크를 자동화하는 데도 스크립트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-103">All replication components in a topology should be scripted as part of a disaster recovery plan, and scripts can also be used to automate repetitive tasks.</span></span> <span data-ttu-id="2305c-104">스크립트에는 게시 또는 구독과 같은 스크립팅된 복제 구성 요소를 구현하는 데 필요한 Transact-SQL 시스템 저장 프로시저가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-104">A script contains the Transact-SQL system stored procedures necessary to implement the replication component(s) scripted, such as a publication or subscription.</span></span> <span data-ttu-id="2305c-105">구성 요소를 만든 후에 마법사(예: 새 게시 마법사) 또는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 스크립트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-105">Scripts can be created in a wizard (such as the New Publication Wizard) or in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] after you create a component.</span></span> <span data-ttu-id="2305c-106">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 **sqlcmd**를 사용하여 스크립트를 확인, 수정 및 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-106">You can view, modify, and run the script using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or **sqlcmd**.</span></span> <span data-ttu-id="2305c-107">백업 파일과 함께 스크립트를 저장하여 복제 토폴로지를 다시 구성할 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-107">Scripts can be stored with backup files to be used in case a replication topology must be reconfigured.</span></span>  
  
 <span data-ttu-id="2305c-108">속성 변경 내용이 적용되면 구성 요소를 다시 스크립팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-108">A component should be re-scripted if any property changes are made.</span></span> <span data-ttu-id="2305c-109">트랜잭션 복제에서 사용자 지정 저장 프로시저를 사용할 경우 각 프로시저의 복사본을 스크립트와 함께 저장해야 합니다. 프로시저가 변경되면 복사본도 업데이트해야 합니다. 일반적으로 프로시저는 스키마가 변경되거나 애플리케이션 요구 사항이 변경될 때 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-109">If you use custom stored procedures with transactional replication, a copy of each procedure should be stored with the scripts; the copy should be updated if the procedure changes (procedures are typically updated due to schema changes or changing application requirements).</span></span> <span data-ttu-id="2305c-110">사용자 지정 프로시저에 대한 자세한 내용은 [트랜잭션 아티클에 대한 변경 내용을 전파하는 방법 지정](transactional/transactional-articles-specify-how-changes-are-propagated.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2305c-110">For more information about custom procedures, see [Specify How Changes Are Propagated for Transactional Articles](transactional/transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
 <span data-ttu-id="2305c-111">매개 변수가 있는 필터를 사용하는 병합 게시의 경우 게시 스크립트에는 데이터 파티션을 만드는 저장 프로시저 호출이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-111">For merge publications that use parameterized filters, publication scripts contain the stored procedure calls to create data partitions.</span></span> <span data-ttu-id="2305c-112">스크립트는 생성된 파티션에 대한 참조와 하나 이상의 파티션을 다시 만드는 방법(필요한 경우)을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-112">The script provides a reference for the partitions created and a way in which to re-create one or more partitions if necessary.</span></span>  
  
## <a name="example-of-automating-a-task-with-scripts"></a><span data-ttu-id="2305c-113">스크립트로 태스크를 자동화하는 예</span><span class="sxs-lookup"><span data-stu-id="2305c-113">Example of Automating a Task with Scripts</span></span>  
 <span data-ttu-id="2305c-114">[!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)]에서 병합 복제를 구현하여 원격 영업 사원에게 데이터를 배포한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-114">Consider [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)], which implements merge replication to distribute data to its remote sales force.</span></span> <span data-ttu-id="2305c-115">판매 담당자는 끌어오기 구독을 사용하여 자신의 지역에 있는 고객과 관련된 모든 데이터를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-115">A sales representative downloads all the data that pertains to the customers in her territory using pull subscriptions.</span></span> <span data-ttu-id="2305c-116">오프라인으로 작업할 때 판매 담당자는 데이터를 업데이트하고 새로운 고객 및 주문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-116">When working offline, the sales representative updates data and enters new customers and orders.</span></span> <span data-ttu-id="2305c-117">[!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] 에는 별개의 지역에 50개 이상의 판매 담당자가 있기 때문에 새 구독 마법사로 각 구독자에 별개의 구독을 만드는 데 많은 시간이 소요됩니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-117">Because [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] has more than fifty sales representatives in different territories, it would be time-consuming to create the different subscriptions at each Subscriber with the New Subscription Wizard.</span></span> <span data-ttu-id="2305c-118">대신 복제 관리자가 다음 단계를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-118">Instead, the replication administrator can follow these steps:</span></span>  
  
1.  <span data-ttu-id="2305c-119">판매 담당자 또는 해당 지역을 기반으로 하여 파티션이 있는 필수 병합 게시를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-119">Set up the necessary merge publications with partitions based on the sales representative or their territory.</span></span>  
  
2.  <span data-ttu-id="2305c-120">하나의 구독자에 대한 끌어오기 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-120">Create a pull subscription for one Subscriber.</span></span>  
  
3.  <span data-ttu-id="2305c-121">해당 끌어오기 구독을 기반으로 하여 스크립트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-121">Generate a script based on that pull subscription.</span></span>  
  
4.  <span data-ttu-id="2305c-122">구독자의 이름과 같은 값을 변경하여 스크립트를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-122">Modify the script, changing such values as the name of the Subscriber.</span></span>  
  
5.  <span data-ttu-id="2305c-123">여러 구독자에서 스크립트를 실행하여 필요한 끌어오기 구독을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-123">Run the script at multiple Subscribers to generate the required pull subscriptions.</span></span>  
  
## <a name="script-replication-objects"></a><span data-ttu-id="2305c-124">복제 개체 스크립팅</span><span class="sxs-lookup"><span data-stu-id="2305c-124">Script Replication Objects</span></span>  
 <span data-ttu-id="2305c-125">복제 마법사 또는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 **복제** 폴더에서 복제 개체를 스크립팅합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-125">Script replication objects from the replication wizards or from the **Replication** folder in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="2305c-126">마법사에서 스크립팅하는 경우 개체를 만들고 스크립팅하거나 스크립팅만 하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-126">If you script from the wizards, you can choose to create objects and script them, or you can choose only to script them.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2305c-127">암호는 모두 NULL로 스크립팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-127">All passwords are scripted as NULL.</span></span> <span data-ttu-id="2305c-128">가능한 경우 런타임 시 사용자에게 보안 자격 증명을 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-128">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="2305c-129">스크립트 파일에 자격 증명을 저장하는 경우에는 무단으로 액세스하지 못하도록 파일에 보안을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-129">If you store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
 <span data-ttu-id="2305c-130">복제 마법사의 사용 방법은 다음을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2305c-130">For more information about using the replication wizards, see:</span></span>  
  
-   [<span data-ttu-id="2305c-131">게시 및 배포 구성</span><span class="sxs-lookup"><span data-stu-id="2305c-131">Configure Publishing and Distribution</span></span>](configure-publishing-and-distribution.md)  
  
-   [<span data-ttu-id="2305c-132">게시 만들기</span><span class="sxs-lookup"><span data-stu-id="2305c-132">Create a Publication</span></span>](publish/create-a-publication.md)  
  
-   [<span data-ttu-id="2305c-133">밀어넣기 구독 만들기</span><span class="sxs-lookup"><span data-stu-id="2305c-133">Create a Push Subscription</span></span>](create-a-push-subscription.md)  
  
-   [<span data-ttu-id="2305c-134">끌어오기 구독 만들기</span><span class="sxs-lookup"><span data-stu-id="2305c-134">Create a Pull Subscription</span></span>](create-a-pull-subscription.md)  
  
#### <a name="to-script-an-object-from-a-replication-wizard"></a><span data-ttu-id="2305c-135">복제 마법사에서 개체를 스크립팅하려면</span><span class="sxs-lookup"><span data-stu-id="2305c-135">To script an object from a replication wizard</span></span>  
  
1.  <span data-ttu-id="2305c-136">마법사의 **마법사 동작** 페이지에서 마법사에 적합한 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-136">On the **Wizard Actions** page of a wizard, select the check box appropriate for the wizard:</span></span>  
  
    -   <span data-ttu-id="2305c-137">**게시 생성 단계를 포함하는 스크립트 파일 생성**</span><span class="sxs-lookup"><span data-stu-id="2305c-137">**Generate a script file with steps to create a publication**</span></span>  
  
    -   <span data-ttu-id="2305c-138">**구독 생성 단계를 포함하는 스크립트 파일 생성**</span><span class="sxs-lookup"><span data-stu-id="2305c-138">**Generate a script file with steps to create the subscription(s)**</span></span>  
  
    -   <span data-ttu-id="2305c-139">**배포 구성 단계를 포함하는 스크립트 파일 생성**</span><span class="sxs-lookup"><span data-stu-id="2305c-139">**Generate a script file with steps to configure distribution**</span></span>  
  
2.  <span data-ttu-id="2305c-140">**스크립트 파일 속성** 페이지에서 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-140">Specify options on the **Script File Properties** page.</span></span>  
  
3.  <span data-ttu-id="2305c-141">마법사를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-141">Complete the wizard.</span></span>  
  
#### <a name="to-script-an-object-from-management-studio"></a><span data-ttu-id="2305c-142">Management Studio에서 개체를 스크립팅하려면</span><span class="sxs-lookup"><span data-stu-id="2305c-142">To script an object from Management Studio</span></span>  
  
1.  <span data-ttu-id="2305c-143">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 배포자, 게시자 또는 구독자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-143">Connect to the Distributor, Publisher, or Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="2305c-144">**복제** 폴더를 확장한 다음 **로컬 게시** 폴더나 **로컬 구독** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-144">Expand the **Replication** folder, and then expand the **Local Publications** folder or the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="2305c-145">게시 또는 구독을 마우스 오른쪽 단추로 클릭한 다음 **스크립트 생성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-145">Right-click a publication or subscription, and then click **Generate Scripts**.</span></span>  
  
4.  <span data-ttu-id="2305c-146">**SQL 스크립트 생성 - \<ReplicationObject>** 대화 상자에서 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-146">Specify options in the **Generate SQL Script - \<ReplicationObject>** dialog box.</span></span>  
  
5.  <span data-ttu-id="2305c-147">**파일로 스크립팅**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-147">Click **Script to File**.</span></span>  
  
6.  <span data-ttu-id="2305c-148">**스크립트 파일 위치** 대화 상자에 파일 이름을 입력한 다음 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-148">Enter a file name in the **Script File Location** dialog box, and then click **Save**.</span></span> <span data-ttu-id="2305c-149">상태 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-149">A status message is displayed.</span></span>  
  
7.  <span data-ttu-id="2305c-150">**확인**을 클릭하고 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-150">Click **OK**, and then click **Close**.</span></span>  
  
#### <a name="to-script-multiple-objects-from-management-studio"></a><span data-ttu-id="2305c-151">Management Studio에서 여러 개체를 스크립팅하려면</span><span class="sxs-lookup"><span data-stu-id="2305c-151">To script multiple objects from Management Studio</span></span>  
  
1.  <span data-ttu-id="2305c-152">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 배포자, 게시자 또는 구독자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-152">Connect to the Distributor, Publisher, or Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="2305c-153">**복제** 폴더를 마우스 오른쪽 단추로 클릭한 다음 **스크립트 생성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-153">Right-click the **Replication** folder, and then click **Generate Scripts**.</span></span>  
  
3.  <span data-ttu-id="2305c-154">**SQL 스크립트 생성** 대화 상자에서 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-154">Specify options in the **Generate SQL Script** dialog box.</span></span>  
  
4.  <span data-ttu-id="2305c-155">**파일로 스크립팅**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-155">Click **Script to File**.</span></span>  
  
5.  <span data-ttu-id="2305c-156">**스크립트 파일 위치** 대화 상자에 파일 이름을 입력한 다음 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-156">Enter a file name in the **Script File Location** dialog box, and then click **Save**.</span></span> <span data-ttu-id="2305c-157">상태 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-157">A status message is displayed.</span></span>  
  
6.  <span data-ttu-id="2305c-158">**확인** 을 클릭한 다음 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2305c-158">Click **OK, and then** click **Close**.</span></span>  
  
  
