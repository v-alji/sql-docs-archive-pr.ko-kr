---
title: 캐시 사전 로드(보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- cache [Reporting Services]
- preloading cache
ms.assetid: 152a1051-8aa5-4c01-bc85-f8be8971b0cd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b60b74f7ab5c0c843b848c09ee574fd59a99c682
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732407"
---
# <a name="preload-the-cache-report-manager"></a><span data-ttu-id="870b0-102">캐시 사전 로드(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="870b0-102">Preload the Cache (Report Manager)</span></span>
  <span data-ttu-id="870b0-103">공유 데이터 세트에 대한 캐시 새로 고침 계획을 만들어 공유 데이터 세트에 대한 캐시를 미리 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-103">You can preload the cache for a shared dataset by creating a cache refresh plan for the shared dataset.</span></span>  
  
 <span data-ttu-id="870b0-104">다음과 같은 두 가지 방법으로 보고서에 대한 캐시를 미리 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-104">You can preload the cache for a report in two ways:</span></span>  
  
1.  <span data-ttu-id="870b0-105">보고서에 대한 캐시 새로 고침 계획을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-105">Create a cache refresh plan for the report.</span></span> <span data-ttu-id="870b0-106">이는 선호되는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-106">This is the preferred method.</span></span>  
  
2.  <span data-ttu-id="870b0-107">데이터 기반 구독을 사용하여 매개 변수가 있는 보고서 인스턴스와 함께 캐시를 미리 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-107">Use a data-driven subscription to preload the cache with instances of parameterized reports.</span></span> <span data-ttu-id="870b0-108">이것이 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 이전의 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]버전에서 캐시를 미리 로드할 수 있는 유일한 방법이었습니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-108">This was the only way to preload the cache in versions of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] earlier than [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="870b0-109">자세한 내용은 [보고서 캐시&#40;SSRS&#41;](caching-reports-ssrs.md)버전에서 캐시를 미리 로드할 수 있는 유일한 방법이었습니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-109">For more information, see [Caching Reports &#40;SSRS&#41;](caching-reports-ssrs.md).</span></span>  
  
 <span data-ttu-id="870b0-110">보고서 또는 공유 데이터 세트를 캐시하려면 먼저 다음 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-110">The following conditions must be met before you can cache a report or a shared dataset:</span></span>  
  
-   <span data-ttu-id="870b0-111">공유 데이터 세트 또는 보고서에 캐싱이 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-111">The shared dataset or the report must have caching enabled.</span></span>  
  
-   <span data-ttu-id="870b0-112">공유 데이터 세트 또는 보고서에 대한 공유 데이터 원본이 저장된 자격 증명을 사용하거나 자격 증명을 사용하지 않도록 구성되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-112">The shared data sources for the shared dataset or the report must be configured to use stored credentials or no credentials.</span></span>  
  
-   <span data-ttu-id="870b0-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스가 실행되고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-113">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service must be running.</span></span>  
  
### <a name="to-preload-the-cache-by-creating-a-cache-refresh-plan"></a><span data-ttu-id="870b0-114">캐시 새로 고침 계획을 만들어 캐시를 미리 로드하려면</span><span class="sxs-lookup"><span data-stu-id="870b0-114">To preload the cache by creating a cache refresh plan</span></span>  
  
1.  <span data-ttu-id="870b0-115">[보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md)를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-115">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="870b0-116">보고서 관리자에서 **내용** 페이지로 이동한 다음 캐시할 항목으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-116">In Report Manager, navigate to the **Contents** page, and then navigate to the item that you want to cache.</span></span>  
  
3.  <span data-ttu-id="870b0-117">항목을 마우스로 가리키고 드롭다운 목록을 클릭한 다음 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-117">Hover over the item, click the drop-down list, and then click **Manage**.</span></span>  
  
4.  <span data-ttu-id="870b0-118">**캐시 새로 고침 옵션** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-118">Click the **Cache Refresh Options** tab.</span></span>  
  
5.  <span data-ttu-id="870b0-119">도구 모음에서 **새 캐시 새로 고침 계획**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-119">On the toolbar, click **New Cache Refresh Plan**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="870b0-120">항목에 캐싱이 설정되어 있지 않으면 캐싱을 설정하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-120">If the item does not have caching enabled, you will be prompted to enable caching.</span></span> <span data-ttu-id="870b0-121">캐싱을 설정하려면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-121">To enable caching, click **OK**.</span></span>  
  
     <span data-ttu-id="870b0-122">캐시 새로 고침 계획 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-122">The Cache Refresh Plan page opens.</span></span>  
  
6.  <span data-ttu-id="870b0-123">새로 고침 계획에 대한 설명을 입력할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-123">Optionally type a description for the refresh plan.</span></span>  
  
7.  <span data-ttu-id="870b0-124">공유 일정의 경우 **공유 일정**을 클릭한 다음 사용할 일정의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-124">For a shared schedule, click **Shared schedule**, and then select the name of the schedule to use.</span></span>  
  
     <span data-ttu-id="870b0-125">사용자 지정 일정의 경우 **항목별 일정**을 클릭한 다음 **구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-125">For a custom schedule, click **Item-specific schedule**, and then click **Configure**.</span></span>  
  
8.  <span data-ttu-id="870b0-126">일정 구성</span><span class="sxs-lookup"><span data-stu-id="870b0-126">Configure the schedule</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-preload-the-cache-with-a-user-specific-report-by-using-a-data-driven-subscription"></a><span data-ttu-id="870b0-127">데이터 기반 구독을 사용하여 사용자별 보고서와 함께 캐시를 미리 로드하려면</span><span class="sxs-lookup"><span data-stu-id="870b0-127">To preload the cache with a user-specific report by using a data-driven subscription</span></span>  
  
1.  <span data-ttu-id="870b0-128">[보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md)를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-128">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="870b0-129">보고서 관리자에서 **내용** 페이지로 이동한 후 구독을 만들 보고서로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-129">In Report Manager, navigate to the **Contents** page, and then navigate to the report you want to create a subscription for.</span></span>  
  
3.  <span data-ttu-id="870b0-130">보고서를 클릭하고 **구독** 탭을 클릭한 다음 **새 데이터 기반 구독**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-130">Click the report, click the **Subscriptions** tab, and then click **New Data-Driven Subscription**.</span></span>  
  
4.  <span data-ttu-id="870b0-131">구독에 대한 설명을 입력합니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="870b0-131">Optionally type a description for the subscription.</span></span>  
  
5.  <span data-ttu-id="870b0-132">**받은 사람에게 알림을 보내는 방법 지정** 목록에서 **Null 배달 공급자**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-132">From the **Specify how recipients are notified** list, select **Null Delivery Provider**.</span></span>  
  
6.  <span data-ttu-id="870b0-133">데이터 원본 유형을 지정한 후 **다음** 을 클릭하여 데이터 원본을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-133">Specify a data source type and then click **Next** to configure the data source.</span></span>  
  
7.  <span data-ttu-id="870b0-134">구독자 데이터를 포함하는 데이터 원본에 액세스하기 위한 연결 형식, 연결 문자열 및 자격 증명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-134">Specify the connection type, connection string, and credentials for accessing the data source that contains subscriber data.</span></span> <span data-ttu-id="870b0-135">다음 예에서는 Subscribers라는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 연결하는 데 사용되는 연결 문자열을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-135">The following example illustrates a connection string used to connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database called Subscribers:</span></span>  
  
    ```  
    data source=<servername>; initial catalog=Subscribers  
    ```  
  
8.  <span data-ttu-id="870b0-136">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-136">Click **Next**.</span></span>  
  
9. <span data-ttu-id="870b0-137">구독자 데이터를 검색하는 쿼리나 명령을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-137">Specify the query or command that retrieves subscriber data.</span></span> <span data-ttu-id="870b0-138">처리하는 데 시간이 오래 걸리는 쿼리에 대해 제한 시간 값을 늘립니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="870b0-138">Optionally increase the time-out period for queries that take a long time to process.</span></span> <span data-ttu-id="870b0-139">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="870b0-139">For example:</span></span>  
  
    ```  
    Select * from UserInfo  
    ```  
  
10. <span data-ttu-id="870b0-140">**유효성 검사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-140">Click **Validate**.</span></span> <span data-ttu-id="870b0-141">계속하기 전에 쿼리의 유효성을 검사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-141">The query must be validated before you continue.</span></span> <span data-ttu-id="870b0-142">**쿼리의 유효성을 검사했습니다** 메시지가 나타나면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-142">When the **Query validated successfully** message appears, click **Next**.</span></span>  
  
11. <span data-ttu-id="870b0-143">Null 배달 공급자에 대한 배달 확장 프로그램 설정을 구성할 수 없으므로 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-143">Because you cannot configure delivery extension settings for the null delivery provider, click **Next**.</span></span>  
  
12. <span data-ttu-id="870b0-144">구독에 대해 보고서 매개 변수 값을 지정하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-144">Specify report parameter values for the subscription, and click **Next**.</span></span>  
  
13. <span data-ttu-id="870b0-145">구독 처리 시기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-145">Specify when the subscription is processed.</span></span> <span data-ttu-id="870b0-146">**보고서 서버에서 보고서 데이터가 업데이트될 때**는 선택하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="870b0-146">Do not choose **When the report data is updated on the report server**.</span></span> <span data-ttu-id="870b0-147">이 설정은 스냅샷에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-147">That setting is for snapshots only.</span></span> <span data-ttu-id="870b0-148">기존 일정을 사용하려면 **공유 일정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-148">If want to use a pre-existing schedule, select **On a shared schedule**.</span></span>  
  
     <span data-ttu-id="870b0-149">그렇지 않고 사용자 지정 일정을 만들려면 **이 구독에 대해 생성된 일정** 을 클릭한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-149">Or, to create a custom schedule, click **On a schedule created for this subscription** and then click **Next**.</span></span> <span data-ttu-id="870b0-150">일정을 구성하고 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-150">Configure the schedule and then click **Finish**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="870b0-151">구독자가 최신 보고서를 받도록 하려면 구성하는 일정이 구독자에 대해 정의한 보고서 배달 일정과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-151">In order for the subscribers to receive the newest report, the schedule that you configure should be consistent with the report delivery schedule that you have defined for the subscribers.</span></span> <span data-ttu-id="870b0-152">자세한 내용은 [보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="870b0-152">For more information, see [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
14. <span data-ttu-id="870b0-153">다음과 같이 보고서에 대한 실행 옵션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-153">Configure the Execution options for the report as follows.</span></span> <span data-ttu-id="870b0-154">보고서 페이지에서 **속성** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-154">On the report page, click the **Properties** tab.</span></span>  
  
15. <span data-ttu-id="870b0-155">왼쪽 프레임에서 **실행** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-155">In the left frame, click the **Execution** tab.</span></span>  
  
16. <span data-ttu-id="870b0-156">해당 페이지에서 **가장 최근 데이터로 이 보고서 렌더링**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-156">On the page, select **Render this report with the most recent data**.</span></span>  
  
17. <span data-ttu-id="870b0-157">다음 두 캐시 옵션 중에서 하나를 선택하고 만료 시간을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-157">Choose one of the following two cache options and configure the expiration as follows:</span></span>  
  
    -   <span data-ttu-id="870b0-158">캐시된 복사본이 특정 시간 후에 만료되도록 하려면 **보고서의 임시 복사본을 캐시합니다. 보고서 복사본은 다음 분 후에 만료됩니다.** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-158">To make the cached copy expire after a particular time period, click **Cache a temporary copy of the report. Expire copy of report after a number of minutes.**</span></span> <span data-ttu-id="870b0-159">보고서 만료 시간(분)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-159">Type the number of minutes for report expiration.</span></span>  
  
    -   <span data-ttu-id="870b0-160">일정에 따라 캐시된 복사본이 만료되도록 하려면 **보고서의 임시 복사본을 캐시합니다. 보고서 복사본은 다음 일정으로 만료됩니다.** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-160">To make the cached copy expire on a schedule, click **Cache a temporary copy of the report. Expire copy of report on the following schedule.**</span></span> <span data-ttu-id="870b0-161">를 클릭합니다. **구성**을 클릭하거나 공유 일정을 선택하여 보고서 만료 일정을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-161">Click **Configure**, or select a shared schedule to set a schedule for report expiration.</span></span>  
  
18. <span data-ttu-id="870b0-162">**적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="870b0-162">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="870b0-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="870b0-163">See Also</span></span>  
 <span data-ttu-id="870b0-164">[Data-Driven Subscriptions](../subscriptions/data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="870b0-164">[Data-Driven Subscriptions](../subscriptions/data-driven-subscriptions.md) </span></span>  
 <span data-ttu-id="870b0-165">[데이터 기반 구독 만들기&#40;SSRS 자습서&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="870b0-165">[Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md) </span></span>  
 <span data-ttu-id="870b0-166">[성능, 스냅숏, 캐싱 &#40;Reporting Services&#41;](performance-snapshots-caching-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="870b0-166">[Performance, Snapshots, Caching &#40;Reporting Services&#41;](performance-snapshots-caching-reporting-services.md) </span></span>  
 <span data-ttu-id="870b0-167">[보고서 처리 속성 설정](set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="870b0-167">[Set Report Processing Properties](set-report-processing-properties.md) </span></span>  
 [<span data-ttu-id="870b0-168">보고서 캐시&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="870b0-168">Caching Reports &#40;SSRS&#41;</span></span>](caching-reports-ssrs.md)  
  
  
