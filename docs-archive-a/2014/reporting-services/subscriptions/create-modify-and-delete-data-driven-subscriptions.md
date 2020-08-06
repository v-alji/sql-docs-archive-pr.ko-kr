---
title: 데이터 기반 구독 만들기, 수정 및 삭제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- query-based subscriptions [Reporting Services]
- queries [Reporting Services], data-driven subscriptions
- subscriptions [Reporting Services], data-driven
- data-driven subscriptions
ms.assetid: 0ba2093e-9393-4eb6-af06-9da10988cfaf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0ec7fad729e5a7bd0f75d7a524ba315b4511a7a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653727"
---
# <a name="create-modify-and-delete-a-data-driven-subscription"></a><span data-ttu-id="cb491-102">Create, Modify, and Delete a Data-Driven Subscription</span><span class="sxs-lookup"><span data-stu-id="cb491-102">Create, Modify, and Delete a Data-Driven Subscription</span></span>
  <span data-ttu-id="cb491-103">데이터 기반 구독은 런타임에 구독을 처리하는 데 사용하는 데이터 값을 가져오는 쿼리 기반 구독입니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-103">A data-driven subscription is a query-based subscription that gets the data values used for processing the subscription at run time.</span></span> <span data-ttu-id="cb491-104">구독이 실행될 때 받는 사람, 보고서 배달 옵션, 렌더링 형식 및 매개 변수 설정에 대한 최신 정보를 가져오기 위한 쿼리가 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-104">When the subscription is triggered, a query is processed to get up-to-date information about recipients, report delivery options, rendering formats, and parameter settings.</span></span> <span data-ttu-id="cb491-105">쿼리 결과가 구독 정의에 조합되어 직원 데이터베이스, 고객 데이터베이스 또는 구독자 데이터로 사용할 수 있는 정보가 포함된 기타 데이터베이스에서 이미 유지 관리되고 있는 데이터를 사용하는 동적 구독을 형성합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-105">The query results are combined with the subscription definition to create a dynamic subscription that uses data you already maintain in an employee database, a customer database, or any other database that contains information that can be used as subscriber data.</span></span>  
  
||  
|-|  
|<span data-ttu-id="cb491-106">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기본 모드 &#124; SharePoint 모드</span><span class="sxs-lookup"><span data-stu-id="cb491-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode &#124; SharePoint mode</span></span>|  
  
 <span data-ttu-id="cb491-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="cb491-107">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="cb491-108">데이터 기반 구독 만들기 및 수정</span><span class="sxs-lookup"><span data-stu-id="cb491-108">Create and Modify a Data-Driven Subscription</span></span>](#bkmk_create_and_modify)  
  
-   [<span data-ttu-id="cb491-109">구독 정보를 검색하는 쿼리 정의</span><span class="sxs-lookup"><span data-stu-id="cb491-109">Define a query that retrieves subscription information</span></span>](#bkmk_define_query)  
  
-   [<span data-ttu-id="cb491-110">구독 실행</span><span class="sxs-lookup"><span data-stu-id="cb491-110">Run a subscription</span></span>](#bkmk_run_subscription)  
  
-   [<span data-ttu-id="cb491-111">데이터 기반 구독 관리 및 삭제</span><span class="sxs-lookup"><span data-stu-id="cb491-111">Manage and delete a data-driven subscription</span></span>](#bkmk_manage_and_delete)  
  
##  <a name="create-and-modify-a-data-driven-subscription"></a><a name="bkmk_create_and_modify"></a><span data-ttu-id="cb491-112">데이터 기반 구독 만들기 및 수정</span><span class="sxs-lookup"><span data-stu-id="cb491-112">Create and Modify a Data-Driven Subscription</span></span>  
 <span data-ttu-id="cb491-113">새 데이터 기반 구독을 만들거나 기존 구독을 수정하려면 보고서 관리자의 데이터 기반 구독 만들기 페이지를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="cb491-113">To create a new data-driven subscription or modify an existing subscription, use the Create Data-Driven Subscription pages in Report Manager.</span></span> <span data-ttu-id="cb491-114">이 페이지에서는 구독을 만들거나 수정하는 각 단계를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-114">These pages walk you through each step of creating or modifying a subscription.</span></span> <span data-ttu-id="cb491-115">구독을 만든 다음 액세스하려면 내 구독 페이지와 보고서의 구독 목록을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-115">To access a subscription after it is created, use the My Subscriptions page and the Subscriptions list of a report.</span></span> <span data-ttu-id="cb491-116">데이터 기반 구독을 만드는 방법에 대한 자세한 내용은 [데이터 기반 구독 만들기&#40;SSRS 자습서&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb491-116">To learn how to create a data-driven subscription, see [Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md).</span></span>  
  
 <span data-ttu-id="cb491-117">데이터 기반 구독을 만들려면 저장된 자격 증명을 사용하거나 자격 증명을 사용하지 않는 보고서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-117">To create a data-driven subscription, select a report that uses stored credentials or no credentials.</span></span> <span data-ttu-id="cb491-118">데이터 기반 구독을 만들 때는 표준 구독과 데이터 기반 구독을 쉽게 구분할 수 있도록 설명 필드에 명명 규칙을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-118">When you create the data-driven subscription, consider using a naming convention for the description field so you can easily differentiate standard subscriptions from data-driven subscriptions.</span></span>  
  
#### <a name="to-create-a-data-driven-subscription-native-mode"></a><span data-ttu-id="cb491-119">데이터 기반 구독을 만들려면(기본 모드)</span><span class="sxs-lookup"><span data-stu-id="cb491-119">To create a data-driven subscription (Native Mode)</span></span>  
  
1.  <span data-ttu-id="cb491-120">보고서 관리자에서 보고서가 포함 된 폴더로 이동 하 고, 보고서 위로 마우스를 이동 하 고, 옵션 메뉴를 열고 관리를 클릭 **합니다.**</span><span class="sxs-lookup"><span data-stu-id="cb491-120">In Report Manager navigate to the folder containing the report, hover over the report, open the options menu and Click the **Manage.**</span></span>  
  
2.  <span data-ttu-id="cb491-121">**구독** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-121">Click the **Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="cb491-122">**새 데이터 기반 구독** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-122">Click the **New Data-Driven Subscription** button.</span></span>  
  
#### <a name="to-create-a-data-driven-subscription-sharepoint-mode"></a><span data-ttu-id="cb491-123">데이터 기반 구독을 만들려면(SharePoint 모드)</span><span class="sxs-lookup"><span data-stu-id="cb491-123">To create a data-driven subscription (SharePoint Mode)</span></span>  
  
1.  <span data-ttu-id="cb491-124">SharePoint 문서 라이브러리에서 해당 보고서에 마우스 포인터를 놓고 옵션 메뉴를 연 다음 **구독 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-124">In the SharePoint document library, hover over the report, open the options menu and Click **Manage Subscriptions**.</span></span>  
  
2.  <span data-ttu-id="cb491-125">**데이터 기반 구독 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-125">Click **Add Data-Driven Subscription**.</span></span>  
  
#### <a name="to-modify-an-existing-data-driven-subscription-native-mode"></a><span data-ttu-id="cb491-126">기존 데이터 기반 구독을 수정하려면(기본 모드)</span><span class="sxs-lookup"><span data-stu-id="cb491-126">To modify an existing data-driven subscription (Native Mode)</span></span>  
  
1.  <span data-ttu-id="cb491-127">보고서 관리자에서 보고서가 있는 폴더로 이동한 후 해당 보고서에 마우스 포인터를 놓고 옵션 메뉴를 연 다음 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-127">In Report Manager navigate to the folder containing the report, hover over the report, open the options menu and Click the **Manage**.</span></span>  
  
2.  <span data-ttu-id="cb491-128">**구독** 탭을 클릭 합니다. 또는 보고서 관리자의 맨 위에서 **내 구독** 링크를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-128">Click the **Subscriptions** tab. Alternatively click the **My Subscriptions** link on at the tope of report manager</span></span>  
  
3.  <span data-ttu-id="cb491-129">수정할 구독을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-129">Select the subscription you want to modify.</span></span> <span data-ttu-id="cb491-130">다음 아이콘은 데이터 기반 구독을 나타냅니다. ![데이터 기반 구독 아이콘](../media/hlp-16subscriptiondd.gif "데이터 기반 구독 아이콘")</span><span class="sxs-lookup"><span data-stu-id="cb491-130">The following icon indicates a data-driven subscription: ![Data-driven subscription icon](../media/hlp-16subscriptiondd.gif "Data-driven subscription icon")</span></span>  
  
#### <a name="to-modify-an-existing-data-driven-subscription-sharepoint-mode"></a><span data-ttu-id="cb491-131">기존 데이터 기반 구독을 수정하려면(SharePoint 모드)</span><span class="sxs-lookup"><span data-stu-id="cb491-131">To modify an existing data-driven subscription (SharePoint Mode)</span></span>  
  
1.  <span data-ttu-id="cb491-132">SharePoint 문서 라이브러리에서 해당 보고서에 마우스 포인터를 놓고 옵션 메뉴를 연 다음 **구독 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-132">In the SharePoint document library, hover over the report, open the options menu and Click **Manage Subscriptions**.</span></span>  
  
2.  <span data-ttu-id="cb491-133">수정할 구독을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-133">Select the subscription you want to modify.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cb491-134">이미 지정된 값을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-134">You can modify any value that is already specified.</span></span> <span data-ttu-id="cb491-135">구독자 데이터 저장소에 액세스하는 데 사용되는 암호를 제외한 모든 값은 처음에 만든 대로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-135">All values are presented as they were first created, except for the password that is used to access the subscriber data store.</span></span> <span data-ttu-id="cb491-136">두 번째 페이지나 다음 페이지에서 값을 수정할 때마다 암호를 다시 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-136">You must retype the password every time you modify values on the second page or any subsequent page.</span></span>  
  
 <span data-ttu-id="cb491-137">데이터 기반 구독을 만들려면 먼저 다음 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-137">Before you can create a data-driven subscription, ensure that you satisfy the following requirements:</span></span>  
  
-   <span data-ttu-id="cb491-138">**보고서 요구 사항**.</span><span class="sxs-lookup"><span data-stu-id="cb491-138">**Report requirements**.</span></span> <span data-ttu-id="cb491-139">보고서는 런타임에 데이터를 검색하기 위해 저장된 자격 증명을 사용하거나 자격 증명을 사용하지 말아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-139">The report must use stored credentials or no credentials to retrieve data at run time.</span></span> <span data-ttu-id="cb491-140">가장 또는 위임된 자격 증명을 사용하여 외부 데이터 원본에 연결하는 보고서는 구독할 수 없습니다. 구독을 만들거나 소유하는 사용자의 자격 증명은 구독이 처리될 때 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-140">You cannot subscribe to a report that uses impersonated or delegated credentials to connect to an external data source; the credentials of the user who creates or owns the subscription will not be available when the subscription is processed.</span></span> <span data-ttu-id="cb491-141">저장된 자격 증명은 Windows 계정이거나 데이터베이스 사용자 계정일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-141">The stored credentials can be a Windows account or a database user account.</span></span> <span data-ttu-id="cb491-142">자세한 내용은 [보고서 데이터 원본에 대한 자격 증명 및 연결 정보 지정](../report-data/specify-credential-and-connection-information-for-report-data-sources.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb491-142">For more information, see [Specify Credential and Connection Information for Report Data Sources](../report-data/specify-credential-and-connection-information-for-report-data-sources.md).</span></span>  
  
     <span data-ttu-id="cb491-143">모델을 데이터 원본으로 사용하고 모델에 모델 항목 보안 설정이 포함된 경우 보고서 작성기 보고서를 구독할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-143">You cannot subscribe to a Report Builder report that uses a model as a data source and the model contains model item security settings.</span></span> <span data-ttu-id="cb491-144">모델 항목 보안을 사용하는 보고서만 이러한 제한을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-144">Only reports that use model item security are included in this restriction.</span></span>  
  
     <span data-ttu-id="cb491-145">`User!UserID` 식이 포함된 보고서에서 데이터 기반 구독을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-145">You cannot create a data-driven subscription on a report that contains the `User!UserID` expression.</span></span>  
  
-   <span data-ttu-id="cb491-146">**데이터 요구 사항**.</span><span class="sxs-lookup"><span data-stu-id="cb491-146">**Data requirements**.</span></span> <span data-ttu-id="cb491-147">구독자 데이터를 포함하는 액세스 가능한 외부 데이터 원본이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-147">You must have an accessible external data source that contains subscriber data.</span></span>  
  
-   <span data-ttu-id="cb491-148">**사용자 요구 사항**.</span><span class="sxs-lookup"><span data-stu-id="cb491-148">**User requirements**.</span></span> <span data-ttu-id="cb491-149">구독 작성자는 "보고서 관리" 및 "모든 구독 관리"의 권한을 갖고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-149">The author of the subscription must have permission to "Manage reports" and "Manage all subscriptions."</span></span> <span data-ttu-id="cb491-150">항목 수준의 태스크 사용 권한에 대한 자세한 내용은 [태스크 및 사용 권한](../security/tasks-and-permissions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb491-150">For more information about item-level task permissions, see [Tasks and Permissions](../security/tasks-and-permissions.md).</span></span> <span data-ttu-id="cb491-151">또한 작성자는 구독자 데이터가 포함된 외부 데이터 원본 액세스를 위해 필요한 자격 증명도 갖고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-151">The author must also have the necessary credentials to access the external data source that contains subscriber data.</span></span>  
  
##  <a name="define-a-query-that-retrieves-subscription-information"></a><a name="bkmk_define_query"></a><span data-ttu-id="cb491-152">구독 정보를 검색 하는 쿼리 정의</span><span class="sxs-lookup"><span data-stu-id="cb491-152">Define a query that retrieves subscription information</span></span>  
 <span data-ttu-id="cb491-153">데이터 기반 구독은 구독자 데이터를 검색하는 쿼리나 명령을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-153">A data-driven subscription must specify a query or command that retrieves subscriber data.</span></span> <span data-ttu-id="cb491-154">쿼리는 구독자마다 하나의 행을 생성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-154">The query should produce one row for each subscriber.</span></span> <span data-ttu-id="cb491-155">전자 메일 배달 확장 프로그램을 사용하는 경우 쿼리는 각 구독자에 대한 유효한 전자 메일 별칭을 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-155">If you are using the e-mail delivery extension, the query should return a valid e-mail alias for each subscriber.</span></span> <span data-ttu-id="cb491-156">생성되는 배달 수는 쿼리에서 반환하는 행 수에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-156">The number of deliveries that are made is based on the number of rows returned by the query.</span></span> <span data-ttu-id="cb491-157">행 집합이 10,000개의 행으로 구성되는 경우 구독은 10,000개의 보고서를 배달합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-157">If the row set consists of 10,000 rows, the subscription delivers 10,000 reports.</span></span>  
  
 <span data-ttu-id="cb491-158">쿼리를 실행하는 데 시간이 많이 걸리는 경우 추가 처리를 수행할 수 있도록 시간 제한 값을 늘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-158">If executing the query is time-consuming, you can increase the time-out value to accommodate additional processing.</span></span>  
  
 <span data-ttu-id="cb491-159">이 단계를 계속하려면 먼저 쿼리의 유효성을 검사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-159">For this step, the query must be validated before you continue.</span></span> <span data-ttu-id="cb491-160">유효성 검사에서는 쿼리를 처리하지 않지만 다음 선택에서 열을 참조할 수 있도록 행 집합에 있는 모든 열 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-160">Validation does not process the query, but it does return a list of all columns that are in the row set so that you can reference the columns in subsequent selections.</span></span> <span data-ttu-id="cb491-161">쿼리 유효성 검사에 실패하면 작업을 계속할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-161">If the query fails to validate, you cannot continue.</span></span> <span data-ttu-id="cb491-162">쿼리 구문이 올바르지 않거나 데이터 원본에 대한 연결이 유효하지 않으면 쿼리의 유효성을 검사하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-162">A query fails to validate if the query syntax is incorrect or if the connection to the data source is not valid.</span></span> <span data-ttu-id="cb491-163">데이터 원본을 수정하려면 **뒤로** 단추를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-163">Use the **Back** button to make corrections to the data source.</span></span>  
  
##  <a name="run-a-subscription"></a><a name="bkmk_run_subscription"></a><span data-ttu-id="cb491-164">구독 실행</span><span class="sxs-lookup"><span data-stu-id="cb491-164">Run a subscription</span></span>  
 <span data-ttu-id="cb491-165">구독 처리 조건을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-165">You configure the conditions for subscription processing.</span></span> <span data-ttu-id="cb491-166">일정을 구성하거나 보고서 실행 스냅샷 업데이트에 맞춰 구독을 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-166">You can configure a schedule, or you can trigger the subscription to coincide with updates to a report execution snapshot.</span></span>  
  
 <span data-ttu-id="cb491-167">![참고](../media/rs-fyinote.png "참고") 사용자 인터페이스에는 즉시 구독을 실행 하는 데 사용할 수 있는 기능이 없지만 간단한 Windows PowerShell 스크립트를 사용 하 여 실행할 구독을 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-167">![note](../media/rs-fyinote.png "note") While there is no feature in the user interface that you can use to immediately run a subscription, you can use a simple Windows PowerShell script to trigger a subscription to run.</span></span> <span data-ttu-id="cb491-168">자세한 내용은 [PowerShell을 사용 하 여 Reporting Services 구독 소유자 변경 및 나열 및 구독 실행](manage-subscription-owners-and-run-subscription-powershell.md)의 "스크립트: 단일 구독 실행" 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cb491-168">For more information, see the "Script: Run (fire) a single subscription" section of [Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](manage-subscription-owners-and-run-subscription-powershell.md).</span></span>  
  
 <span data-ttu-id="cb491-169">데이터 기반 구독 실행에 대한 일정 및 조건은 표준 구독 처리에 대한 일정 및 조건과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-169">Schedule and conditions for running a data-driven subscriptions is the same as processing for standard subscriptions.</span></span>  
  
##  <a name="manage-and-delete-a-data-driven-subscription"></a><a name="bkmk_manage_and_delete"></a><span data-ttu-id="cb491-170">데이터 기반 구독 관리 및 삭제</span><span class="sxs-lookup"><span data-stu-id="cb491-170">Manage and delete a data-driven subscription</span></span>  
 <span data-ttu-id="cb491-171">진행 중인 데이터 기반 구독은 보고서 관리자의 작업 관리 페이지를 통해 중지하거나 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-171">A data-driven subscription that is in progress cannot be stopped or deleted through the Manage Jobs page of Report Manager.</span></span> <span data-ttu-id="cb491-172">그러므로 공유 일정을 사용하여 데이터 기반 구독을 트리거하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-172">For this reason, it is advantageous to use a shared schedule to trigger data-driven subscription.</span></span> <span data-ttu-id="cb491-173">구독이 일시적으로 처리되지 않도록 하려는 경우 이 방법을 사용하면 구독을 트리거하는 일정을 일시 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-173">That way, if you want to temporarily prevent a subscription from processing, you can pause the schedule that triggers the subscription.</span></span> <span data-ttu-id="cb491-174">자세한 내용은 [기본 모드 보고서 서버 구독 만들기 및 관리](../create-manage-subscriptions-native-mode-report-servers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb491-174">For more information, see [Create and Manage Subscriptions for Native Mode Report Servers](../create-manage-subscriptions-native-mode-report-servers.md).</span></span>  
  
 <span data-ttu-id="cb491-175">데이터 기반 구독을 삭제하려면 내 구독 페이지 또는 보고서의 구독 페이지에서 데이터 기반 구독을 선택한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb491-175">To delete a data-driven subscription, select it from the My Subscriptions page or the Subscriptions page of a report and then click **Delete**.</span></span>  
  
 <span data-ttu-id="cb491-176">데이터 기반 구독을 취소하는 방법에 대한 자세한 내용은 [실행 중인 프로세스 관리](manage-a-running-process.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb491-176">For instructions on how to cancel a data-driven subscription, see [Manage a Running Process](manage-a-running-process.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb491-177">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cb491-177">See Also</span></span>  
 <span data-ttu-id="cb491-178">[기본 모드에서 표준 구독을 만들고, 수정 하 고, 삭제 &#40;Reporting Services&#41;](create-and-manage-subscriptions-for-native-mode-report-servers.md) </span><span class="sxs-lookup"><span data-stu-id="cb491-178">[Create, Modify, and Delete Standard Subscriptions &#40;Reporting Services in Native Mode&#41;](create-and-manage-subscriptions-for-native-mode-report-servers.md) </span></span>  
 <span data-ttu-id="cb491-179">[구독 및 배달&#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="cb491-179">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span></span>  
 <span data-ttu-id="cb491-180">[보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="cb491-180">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="cb491-181">[기본 모드 보고서 서버 구독 만들기 및 관리](../create-manage-subscriptions-native-mode-report-servers.md) </span><span class="sxs-lookup"><span data-stu-id="cb491-181">[Create and Manage Subscriptions for Native Mode Report Servers](../create-manage-subscriptions-native-mode-report-servers.md) </span></span>  
 <span data-ttu-id="cb491-182">[구독 페이지 &#40;보고서 관리자&#41;](../subscriptions-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="cb491-182">[Subscriptions Page &#40;Report Manager&#41;](../subscriptions-page-report-manager.md) </span></span>  
 [<span data-ttu-id="cb491-183">내 구독 페이지&#40;보고서 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="cb491-183">My Subscriptions Page &#40;Report Manager&#41;</span></span>](../my-subscriptions-page-report-manager.md)  
  
  
