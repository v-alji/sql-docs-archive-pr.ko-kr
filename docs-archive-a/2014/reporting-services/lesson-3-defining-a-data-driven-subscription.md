---
title: '3단원: 데이터 기반 구독 정의 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 89197b9b-7502-4fe2-bea3-ed7943eebf3b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d1bbc25bdd08b369180e31378a6d25a595badbcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742900"
---
# <a name="lesson-3-defining-a-data-driven-subscription"></a><span data-ttu-id="eebf6-102">Lesson 3: Defining a Data-Driven Subscription</span><span class="sxs-lookup"><span data-stu-id="eebf6-102">Lesson 3: Defining a Data-Driven Subscription</span></span>
  <span data-ttu-id="eebf6-103">이 단원에서는 데이터 기반 구독 페이지를 사용하여 구독 데이터 원본에 연결하고 구독 데이터를 검색하는 쿼리를 작성하며 결과 집합을 보고서 및 배달 옵션에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-103">In this lesson, you use the data-driven subscription pages to connect to a subscription data source, build a query that retrieves subscription data, and map the result set to report and delivery options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="eebf6-104">시작하기 전에 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 서비스가 실행 중인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-104">Before you start, verify that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service is running.</span></span> <span data-ttu-id="eebf6-105">이 서비스를 실행하지 않으면 구독을 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-105">If it is not running, you cannot save the subscription.</span></span>  
  
 <span data-ttu-id="eebf6-106">이 단원에서는 1단원 및 2단원을 완료했고 보고서 데이터 원본에서 저장된 자격 증명을 사용한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-106">This lesson assumes you completed Lesson 1 and Lesson 2 and that the report data source uses stored credentials.</span></span>  <span data-ttu-id="eebf6-107">자세한 내용은 [2단원: 보고서 데이터 원본 속성 수정](../reporting-services/lesson-2-modifying-the-report-data-source-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eebf6-107">For more information, see [Lesson 2: Modifying the Report Data Source Properties](../reporting-services/lesson-2-modifying-the-report-data-source-properties.md)</span></span>  
  
 <span data-ttu-id="eebf6-108">이 항목의 내용:</span><span class="sxs-lookup"><span data-stu-id="eebf6-108">In this topic:</span></span>  
  
-   [<span data-ttu-id="eebf6-109">데이터 기반 구독 마법사 시작</span><span class="sxs-lookup"><span data-stu-id="eebf6-109">Start the Data-Driven Subscription Wizard</span></span>](#bkmk_startwizard)  
  
-   [<span data-ttu-id="eebf6-110">1단계 - 설명 정의</span><span class="sxs-lookup"><span data-stu-id="eebf6-110">Step 1 - Define a description</span></span>](#bkmk_definesubscription)  
  
-   [<span data-ttu-id="eebf6-111">2단계 - 구독자 데이터 원본에 대한 연결 정의</span><span class="sxs-lookup"><span data-stu-id="eebf6-111">Step 2 - Define a Connection to the Subscriber Data Source</span></span>](#bkmk_defineconnectiontosubscriber)  
  
-   [<span data-ttu-id="eebf6-112">3단계 - 구독자 데이터를 검색하는 쿼리 정의</span><span class="sxs-lookup"><span data-stu-id="eebf6-112">Step 3 - Define a Query to Retrieve Subscriber data</span></span>](#bkmk_definequery)  
  
-   [<span data-ttu-id="eebf6-113">4단계 - 배달 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="eebf6-113">Step 4 - Set Delivery Options</span></span>](#bkmk_set_deliveryoptions)  
  
-   [<span data-ttu-id="eebf6-114">5단계 - 보고서 출력을 변경하는 매개 변수 값 구성</span><span class="sxs-lookup"><span data-stu-id="eebf6-114">Step 5 - Configure a Parameter Value to Very Report Output</span></span>](#bkmk_configure_parameter)  
  
-   [<span data-ttu-id="eebf6-115">6단계 - 구독을 예약하려면</span><span class="sxs-lookup"><span data-stu-id="eebf6-115">Step 6 - To Schedule a Subscription</span></span>](#bkmk_schedule_subscription)  
  
##  <a name="start-the-data-driven-subscription-wizard"></a><a name="bkmk_startwizard"></a><span data-ttu-id="eebf6-116">데이터 기반 구독 마법사 시작</span><span class="sxs-lookup"><span data-stu-id="eebf6-116">Start the Data-Driven Subscription Wizard</span></span>  
  
1.  <span data-ttu-id="eebf6-117">보고서 관리자에서 **홈**을 클릭하고 **Sales Orders** 보고서가 있는 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-117">In Report Manager, click **Home**, and navigate to the folder containing the **Sales Orders** report.</span></span>  
  
2.  <span data-ttu-id="eebf6-118">보고서의 상황에 맞는 메뉴에서 **관리**를 클릭한 후 **구독** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-118">In the context menu of the report, click **Manage**, and then click the **Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="eebf6-119">**새 데이터 기반 구독**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-119">Click **New Data-driven Subscription**.</span></span> <span data-ttu-id="eebf6-120">이 단추가 표시되지 않는 경우 내용 관리자 권한이 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-120">If you do not see this button, you do not have Content Manager permissions.</span></span>  
  
##  <a name="step-1---define-a-description"></a><a name="bkmk_definesubscription"></a><span data-ttu-id="eebf6-121">1 단계-설명 정의</span><span class="sxs-lookup"><span data-stu-id="eebf6-121">Step 1 - Define a description</span></span>  
  
1.  <span data-ttu-id="eebf6-122">설명에 **Sales Order 배달** 을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-122">Type **Sales Order delivery** in description.</span></span>  
  
2.  <span data-ttu-id="eebf6-123">**받는 사람에게 알림을 보내는 방법 지정** 에서 **Windows 파일 공유**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-123">Select **Windows FileShare** for **Specify how recipients are notified**.</span></span>  
  
3.  <span data-ttu-id="eebf6-124">**이 구독에 대해서만 지정하세요**를 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-124">Select **Specify for this subscription only**, and then click **Next**.</span></span>  
  
##  <a name="step-2---define-a-connection-to-the-subscriber-data-source"></a><a name="bkmk_defineconnectiontosubscriber"></a><span data-ttu-id="eebf6-125">2 단계-구독자 데이터 원본에 대 한 연결 정의</span><span class="sxs-lookup"><span data-stu-id="eebf6-125">Step 2 - Define a Connection to the Subscriber Data Source</span></span>  
  
1.  <span data-ttu-id="eebf6-126">데이터 원본 유형으로 **Microsoft SQL Server** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-126">Select **Microsoft SQL Server** as the data source type.</span></span>  
  
2.  <span data-ttu-id="eebf6-127">연결 문자열에 다음 연결 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-127">In Connection string, type the following connection string:</span></span>  
  
    ```  
    data source=localhost; initial catalog=Subscribers  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="eebf6-128">구독자는 1단원에서 만든 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-128">Subscribers is the database you created in lesson 1.</span></span>  
  
3.  <span data-ttu-id="eebf6-129">**보고서 서버에 안전하게 저장된 자격 증명**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-129">Click **Credentials stored securely in the report server**.</span></span>  
  
4.  <span data-ttu-id="eebf6-130">**사용자 이름** 및 **암호**에 도메인 사용자 이름 및 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-130">In **User Name** and **Password**, type your domain user name and password.</span></span> <span data-ttu-id="eebf6-131">**사용자 이름**을 지정할 때는 도메인 계정과 사용자 계정을 모두 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-131">Include both the domain and user account when specifying **User Name**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eebf6-132">구독자 데이터 원본에 연결하는 데 사용된 자격 증명은 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]로 다시 전달되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-132">Credentials used to connect to a subscriber data source are not passed back to [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="eebf6-133">나중에 구독을 수정할 경우 데이터 원본에 연결하는 데 사용된 암호를 다시 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-133">If you modify the subscription later, you must retype the password used to connect to the data source.</span></span>  
  
5.  <span data-ttu-id="eebf6-134">**데이터 원본에 연결할 때 Windows 자격 증명으로 사용**을 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-134">Select **Use as windows credentials when connecting to the data source**, and then click **Next**.</span></span>  
  
##  <a name="step-3---define-a-query-to-retrieve-subscriber-data"></a><a name="bkmk_definequery"></a><span data-ttu-id="eebf6-135">3 단계-구독자 데이터를 검색 하는 쿼리 정의</span><span class="sxs-lookup"><span data-stu-id="eebf6-135">Step 3 - Define a Query to Retrieve Subscriber data</span></span>  
  
1.  <span data-ttu-id="eebf6-136">쿼리 상자에 다음 쿼리를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-136">In the query box, type the following query:</span></span>  
  
    ```  
    Select * from OrderInfo  
    ```  
  
2.  <span data-ttu-id="eebf6-137">제한 시간을 30초로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-137">Specify a time-out of 30 seconds.</span></span>  
  
3.  <span data-ttu-id="eebf6-138">**유효성 검사**를 클릭하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-138">Click **Validate**, and then click **Next**.</span></span>  
  
##  <a name="step-4---set-delivery-options"></a><a name="bkmk_set_deliveryoptions"></a><span data-ttu-id="eebf6-139">4 단계-배달 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="eebf6-139">Step 4 - Set Delivery Options</span></span>  
  
1.  <span data-ttu-id="eebf6-140">**파일 이름**에 대해 **데이터베이스에서 값 가져오기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-140">For **File name**, select **Get the value from the database**.</span></span> <span data-ttu-id="eebf6-141">**Order**필드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-141">Select the field **Order**.</span></span>  
  
2.  <span data-ttu-id="eebf6-142">**경로**에 대해 **정적 값 지정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-142">For **Path**, select **Specify a static value**.</span></span> <span data-ttu-id="eebf6-143">값 설정에 쓰기 권한이 있는 공용 파일 공유의 이름(예: `\\mycomputer\public\myreports`)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-143">In Setting Value, type the name of a public file share for which you have write permissions (for example, `\\mycomputer\public\myreports`).</span></span>  
  
3.  <span data-ttu-id="eebf6-144">**렌더링 형식**에 대해 **데이터베이스에서 값 가져오기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-144">For **Render Format**, select **Get the value from the database**.</span></span> <span data-ttu-id="eebf6-145">**형식**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-145">Select **Format**.</span></span>  
  
4.  <span data-ttu-id="eebf6-146">**쓰기 모드**에 대해 **정적 값 지정** 을 선택하고 **AutoIncrement**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-146">For **Write mode**, select **Specify a static value** and select **AutoIncrement**.</span></span>  
  
5.  <span data-ttu-id="eebf6-147">**파일 확장명**에 대해 **정적 값 지정** 을 선택하고 **True**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-147">For **File Extension**, select **Specify a static value** and select **True**.</span></span>  
  
6.  <span data-ttu-id="eebf6-148">**사용자 이름**에 대해 **정적 값 지정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-148">For **User name**, select **Specify a static value**.</span></span> <span data-ttu-id="eebf6-149">도메인 사용자 계정을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-149">Type your domain user account.</span></span> <span data-ttu-id="eebf6-150">이 계정을 `<domain>\<account>`형식으로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-150">Enter it in this format: `<domain>\<account>`.</span></span> <span data-ttu-id="eebf6-151">사용자 계정에는 사용자가 이전 단계에서 구성한 경로에 대한 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-151">The user account needs to have permissions to the path you configured in the previous steps.</span></span>  
  
7.  <span data-ttu-id="eebf6-152">**암호**에 대해 **정적 값 지정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-152">For **Password**, select **Specify a static value**.</span></span> <span data-ttu-id="eebf6-153">암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-153">Type your password.</span></span> <span data-ttu-id="eebf6-154">마법사에서는 암호의 유효성을 검사하지 않으므로</span><span class="sxs-lookup"><span data-stu-id="eebf6-154">Be sure that you type the password carefully.</span></span> <span data-ttu-id="eebf6-155">암호 입력 시 주의합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-155">The wizard does not validate the password.</span></span>  
  
8.  <span data-ttu-id="eebf6-156">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-156">Click **Next.**</span></span>  
  
##  <a name="step-5---configure-a-parameter-value-to-very-report-output"></a><a name="bkmk_configure_parameter"></a><span data-ttu-id="eebf6-157">5 단계-보고서 출력에 대 한 매개 변수 값 구성</span><span class="sxs-lookup"><span data-stu-id="eebf6-157">Step 5 - Configure a Parameter Value to Very Report Output</span></span>  
  
1.  <span data-ttu-id="eebf6-158">**OrderNumber**에 대해 **데이터베이스에서 값 가져오기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-158">For **OrderNumber**, select **Get the value from the database**.</span></span> <span data-ttu-id="eebf6-159">값에서 **Order**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-159">In Value, select **Order**.</span></span> <span data-ttu-id="eebf6-160">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-160">Click **Next.**</span></span>  
  
##  <a name="step-6---to-schedule-a-subscription"></a><a name="bkmk_schedule_subscription"></a><span data-ttu-id="eebf6-161">6 단계-구독을 예약 하려면</span><span class="sxs-lookup"><span data-stu-id="eebf6-161">Step 6 - To Schedule a Subscription</span></span>  
  
1.  <span data-ttu-id="eebf6-162">**이 구독에 대해 생성된 일정**을 클릭한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-162">Click **On a schedule created for this subscription**, and then click **Next**.</span></span>  
  
2.  <span data-ttu-id="eebf6-163">**일정 정보**에서 **한 번**을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-163">In **Schedule Details**, click **Once**.</span></span>  
  
3.  <span data-ttu-id="eebf6-164">시작 시간을 현재 시간보다 몇 분 앞당겨 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-164">Specify a start time that is a few minutes ahead of the current time.</span></span>  
  
4.  <span data-ttu-id="eebf6-165">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-165">Click **Finish**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="eebf6-166">다음 단계</span><span class="sxs-lookup"><span data-stu-id="eebf6-166">Next Steps</span></span>  
 <span data-ttu-id="eebf6-167">구독을 실행하면 *Subscribers* 데이터 원본의 각 주문에 대해 하나씩 총 4개의 보고서 파일이 사용자가 지정한 파일 공유로 배달됩니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-167">When the subscription runs, four report files will be delivered to the file share you specified, one for each order in the *Subscribers* data source.</span></span> <span data-ttu-id="eebf6-168">각 배달은 데이터(주문별 데이터여야 함), 렌더링 형식 및 파일 형식에 있어 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-168">Each delivery should be unique in terms of data (the data should be order-specific), rendering format, and file format.</span></span> <span data-ttu-id="eebf6-169">공유 폴더에서 각 보고서를 열어 각 버전이 사용자가 정의한 구독 옵션을 기반으로 사용자 지정되었는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-169">You can open each report from the shared folder to verify that each version is customized based on the subscription options you defined.</span></span>  
  
 <span data-ttu-id="eebf6-170">![구독으로 만드는 파일 목록](../../2014/tutorials/media/ssrs-tutorial-datadriven-subscription-filelist.gif "구독으로 만드는 파일 목록")</span><span class="sxs-lookup"><span data-stu-id="eebf6-170">![List of files created by the subscription](../../2014/tutorials/media/ssrs-tutorial-datadriven-subscription-filelist.gif "List of files created by the subscription")</span></span>  
  
 <span data-ttu-id="eebf6-171">보고서 관리자의 구독 페이지에는 구독의 **마지막 실행** 날짜와 **상태** 가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-171">The subscription page in Report Manager will contain the **Last Run** date and **Status** of the subscription.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="eebf6-172">업데이트된 정보를 보려면 구독을 실행한 후 페이지를 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-172">Refresh the page after the subscription runs to see the updated information.</span></span>  
  
 <span data-ttu-id="eebf6-173">![보고서 관리자의 구독 결과](../../2014/tutorials/media/ssrs-tutorial-datadriven-subscription-status-reportmanager.gif "보고서 관리자의 구독 결과")</span><span class="sxs-lookup"><span data-stu-id="eebf6-173">![Subscription results in Report Manager](../../2014/tutorials/media/ssrs-tutorial-datadriven-subscription-status-reportmanager.gif "Subscription results in Report Manager")</span></span>  
  
 <span data-ttu-id="eebf6-174">이 단계는 "데이터 기반 구독 정의" 자습서의 마지막 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="eebf6-174">This step concludes the tutorial "Defining a Data-Driven Subscription".</span></span> <span data-ttu-id="eebf6-175">다른 자습서에 대 한 자세한 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 내용은 [SSRS&#41;&#40;Reporting Services 자습서 ](../reporting-services/reporting-services-tutorials-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="eebf6-175">To learn more about other [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] tutorials, see [Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eebf6-176">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eebf6-176">See Also</span></span>  
 <span data-ttu-id="eebf6-177">[데이터 기반 구독 만들기&#40;SSRS 자습서&#41;](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="eebf6-177">[Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md) </span></span>  
 <span data-ttu-id="eebf6-178">[구독 및 배달&#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="eebf6-178">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md) </span></span>  
 <span data-ttu-id="eebf6-179">[Data-Driven Subscriptions](subscriptions/data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="eebf6-179">[Data-Driven Subscriptions](subscriptions/data-driven-subscriptions.md) </span></span>  
 <span data-ttu-id="eebf6-180">[데이터 기반 구독 만들기, 수정 및 삭제](subscriptions/create-modify-and-delete-data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="eebf6-180">[Create, Modify, and Delete a Data-Driven Subscription](subscriptions/create-modify-and-delete-data-driven-subscriptions.md) </span></span>  
 [<span data-ttu-id="eebf6-181">구독자 데이터에 외부 데이터 원본 사용&#40;데이터 기반 구독&#41;</span><span class="sxs-lookup"><span data-stu-id="eebf6-181">Use an External Data Source for Subscriber Data &#40;Data-Driven Subscription&#41;</span></span>](subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)  
  
  
