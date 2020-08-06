---
title: 도메인 간 규칙 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dm.testcdrule.f1
- sql12.dqs.dm.cdrules.f1
ms.assetid: 0f3f5ba4-cc47-4d66-866e-371a042d1f21
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cddcd9bbd2fc8d95fe8645781de5fe4e936050a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728708"
---
# <a name="create-a-cross-domain-rule"></a><span data-ttu-id="60459-102">도메인 간 규칙 만들기</span><span class="sxs-lookup"><span data-stu-id="60459-102">Create a Cross-Domain Rule</span></span>
  <span data-ttu-id="60459-103">이 항목에서는 DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] )의 기술 자료에서 복합 도메인의 도메인 간 규칙을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-103">This topic describes how to create a cross-domain rule for a composite domain in a knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="60459-104">도메인 간 규칙은 복합 도메인에 포함된 단일 도메인에서 값 사이의 관계를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-104">A cross-domain rule tests the relationship between values in single domains that are included in a composite domain.</span></span> <span data-ttu-id="60459-105">도메인 값이 정확하고 비즈니스 요구 사항에 맞는 것으로 간주되려면 도메인 간 규칙이 복합 도메인 전체에서 유효해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-105">A cross-domain rule must hold true across a composite domain in order for domain values to be considered accurate and conformant to business requirements.</span></span> <span data-ttu-id="60459-106">도메인 간 규칙은 도메인 값의 유효성 검사, 수정 및 표준화에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="60459-106">A cross-domain rule is used to validate, correct, and standardize domain values.</span></span>  
  
 <span data-ttu-id="60459-107">도메인 간 규칙의 If 절과 Then 절은 각각 복합 도메인의 단일 도메인 중 하나에 대해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="60459-107">The If clause and Then clause of a cross-domain rule are each defined for one of the single domains in the composite domain.</span></span> <span data-ttu-id="60459-108">각 절은 서로 다른 단일 도메인에 대해 정의되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-108">Each clause must be defined for a different single domain.</span></span> <span data-ttu-id="60459-109">도메인 간 규칙은 여러 개의 단일 도메인과 관련되어야 합니다. 복합 도메인에 단순 도메인 규칙(단일 도메인 전용)을 정의할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="60459-109">A cross-domain rule must relate to multiple single domains; you cannot define a simple domain rule (for only a single domain) for a composite domain.</span></span> <span data-ttu-id="60459-110">단일 도메인에 도메인 규칙을 정의하여 이 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-110">You would do so by defining a domain rule for a single domain.</span></span> <span data-ttu-id="60459-111">If 절과 Then 절은 각각 하나 이상의 조건을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60459-111">The If clause and the Then clause can each contain one or more conditions.</span></span>  
  
 <span data-ttu-id="60459-112">결정적 조건이 있는 도메인 간 규칙은 조건 값의 동의어와 값 자체에 규칙 논리를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-112">A cross-domain rule that has definitive conditions will apply the rules logic to synonyms of the value in the conditions, as well the values themselves.</span></span> <span data-ttu-id="60459-113">If 절과 Then 절의 결정적 조건은 값이 다음 값과 같음, 값이 다음 값과 같지 않음, 값이 다음에 속함 또는 값이 다음에 포함되지 않음입니다.</span><span class="sxs-lookup"><span data-stu-id="60459-113">The definitive conditions for the If and Then clauses are Value is equal to, Value is not equal to, Value is in, or Value is not in.</span></span> <span data-ttu-id="60459-114">예를 들어 복합 도메인에 대해 다음과 같은 도메인 간 규칙이 있다고 가정합니다. "‘City’ 값이 ‘Los Angeles’이면 ‘State’ 값은 ‘CA’입니다."</span><span class="sxs-lookup"><span data-stu-id="60459-114">For example, suppose that you have the following cross-domain rule for a composite domain: "For 'City', if Value is equal to 'Los Angeles', then for 'State', Value is equal to 'CA'.</span></span> <span data-ttu-id="60459-115">‘Los Angeles’와 ‘LA’가 동의어인 경우 이 규칙은 ‘Los Angeles CA’와 ‘LA CA’에 대해 올바른 결과를, ‘Los Angeles WA’ 및 ‘LA WA’에 대해서는 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-115">"If 'Los Angeles' and 'LA' are synonyms, this rule will return correct for 'Los Angeles CA' and 'LA CA' and in error for 'Los Angeles WA' and 'LA WA'.</span></span>  
  
 <span data-ttu-id="60459-116">도메인 간 규칙 *값이 다음 값과 같음* 에서 결정적 **Then**절은 도메인 간 규칙의 유효성에 대해 알려줄 뿐만 아니라 데이터 정리 작업 시 데이터를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-116">Apart from just letting you know about the validity of a cross-domain rule, the definitive *Then* clause in a cross-domain rule, **Value is equal to**, also corrects the data during the data-cleansing activity.</span></span> <span data-ttu-id="60459-117">자세한 내용은 [Data Correction using Definitive Cross-Domain Rules](../../2014/data-quality-services/cleanse-data-in-a-composite-domain.md#CDCorrection) 에서 [Cleanse Data in a Composite Domain](../../2014/data-quality-services/cleanse-data-in-a-composite-domain.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="60459-117">For more information, see [Data Correction using Definitive Cross-Domain Rules](../../2014/data-quality-services/cleanse-data-in-a-composite-domain.md#CDCorrection) in [Cleanse Data in a Composite Domain](../../2014/data-quality-services/cleanse-data-in-a-composite-domain.md).</span></span>  
  
 <span data-ttu-id="60459-118">단일 도메인에만 영향을 주는 모든 단순한 규칙 뒤에서 도메인 간 규칙을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="60459-118">Cross-domain rules are taken into consideration after all simple rules that affect only a single domain.</span></span> <span data-ttu-id="60459-119">값이 단일 도메인 규칙(존재할 경우)을 전달할 경우에만 도메인 간 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="60459-119">Only if a value passes single domain rules (if they exist) is the cross-domain rule applied.</span></span> <span data-ttu-id="60459-120">먼저 규칙이 실행되는 복합 도메인과 단일 도메인을 모두 정의해야 규칙을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60459-120">The composite domain and the single domains that a rule is run on must all be defined before the rule can be executed.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="60459-121">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="60459-121">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="60459-122">필수 조건</span><span class="sxs-lookup"><span data-stu-id="60459-122">Prerequisites</span></span>  
 <span data-ttu-id="60459-123">도메인 간 규칙을 만들려면 복합 도메인을 만들어 열어 놓아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-123">To create a cross-domain rule, you must have created and opened a composite domain.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="60459-124">보안</span><span class="sxs-lookup"><span data-stu-id="60459-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="60459-125">권한</span><span class="sxs-lookup"><span data-stu-id="60459-125">Permissions</span></span>  
 <span data-ttu-id="60459-126">도메인 간 규칙을 만들려면 DQS_MAIN 데이터베이스의 dqs_kb_editor 또는 dqs_administrator 역할이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-126">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to create a cross-domain rule.</span></span>  
  
##  <a name="create-cross-domain-rules"></a><a name="Create"></a> <span data-ttu-id="60459-127">도메인 간 규칙 만들기</span><span class="sxs-lookup"><span data-stu-id="60459-127">Create Cross-Domain Rules</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="60459-128">[Data Quality Client 응용 프로그램을 실행](../../2014/data-quality-services/run-the-data-quality-client-application.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-128">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="60459-129">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면에서 기술 자료를 열거나 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="60459-129">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open or create a knowledge base.</span></span> <span data-ttu-id="60459-130">**도메인 관리** 를 작업으로 선택한 다음 **열기** 또는 **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-130">Select **Domain Management** as the activity, and then click **Open** or **Create**.</span></span> <span data-ttu-id="60459-131">자세한 내용은 [기술 자료 만들기](../../2014/data-quality-services/create-a-knowledge-base.md) 또는 [기술 자료 열기](../../2014/data-quality-services/open-a-knowledge-base.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="60459-131">For more information, see [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md) or [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="60459-132">도메인 관리는 별도의 도메인 관리 작업을 위한 5개 탭이 포함된 Data Quality Services 클라이언트의 페이지에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="60459-132">Domain management is performed in a page of the Data Quality Service client that contains five tabs for separate domain management operations.</span></span> <span data-ttu-id="60459-133">도메인 관리는 마법사 기반 프로세스가 아닙니다. 모든 관리 작업은 별도로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60459-133">It is not a wizard-driven process; any management operation can be performed separately.</span></span>  
  
3.  <span data-ttu-id="60459-134">**도메인 관리** 페이지의 **도메인 목록** 에서 도메인 규칙을 만들 복합 도메인을 선택하거나 새 복합 도메인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="60459-134">From the **Domain list** on the **Domain Management** page, select the composite domain that you want to create a domain rule for, or create a new composite domain.</span></span> <span data-ttu-id="60459-135">새 도메인을 만들어야 하는 경우 [Create a Composite Domain](../../2014/data-quality-services/create-a-composite-domain.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="60459-135">If you have to create a new domain, see [Create a Composite Domain](../../2014/data-quality-services/create-a-composite-domain.md).</span></span>  
  
4.  <span data-ttu-id="60459-136">**CD 규칙** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-136">Click the **CD Rules** tab.</span></span>  
  
5.  <span data-ttu-id="60459-137">**새 도메인 규칙을 추가합니다.** 를 클릭하고 규칙의 이름과 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-137">Click **Add a new domain rule**, and then enter a name and description for the rule.</span></span>  
  
6.  <span data-ttu-id="60459-138">**활성** 을 선택하여 해당 규칙이 실행되도록 지정하거나(기본값) 선택 취소하여 규칙이 실행되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-138">Select **Active** to specify that the rule will be run (the default), and deselect to prevent the rule from running.</span></span>  
  
7.  <span data-ttu-id="60459-139">다음과 같이 If 절을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="60459-139">Create the If clause as follows:</span></span>  
  
    1.  <span data-ttu-id="60459-140">If 절 창의 도메인 목록에서 복합 도메인에 포함된 단일 도메인 중 하나를 if 절의 주체로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-140">In the domain list in the If clause pane, select one of the single domains included in the composite domain to be the subject of the If clause.</span></span> <span data-ttu-id="60459-141">복합 도메인에서 임의의 단일 도메인을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60459-141">You can select any single domain in the composite domain.</span></span>  
  
    2.  <span data-ttu-id="60459-142">절의 첫째 조건에 대한 드롭다운 목록에서 조건을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-142">Select a condition from the drop-down list for the first condition of the clause.</span></span>  
  
    3.  <span data-ttu-id="60459-143">조건에 값이 필요한 경우 조건과 연결된 입력란에 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-143">If the condition requires a value, enter the value in the text box associated with the condition.</span></span>  
  
    4.  <span data-ttu-id="60459-144">if 절에 다른 조건이 필요한 경우 **선택한 절에 새 조건을 추가합니다.** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-144">If the If clause requires another condition, click **Adds a new condition to the selected clause**.</span></span> <span data-ttu-id="60459-145">연산자를 선택하고 조건을 선택한 후 필요하면 조건의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-145">Select the operator, select a condition, and enter a value for the condition, if necessary.</span></span>  
  
    5.  <span data-ttu-id="60459-146">조건 순서를 변경하려면 조건의 왼쪽을 클릭하여 조건을 선택하고 위쪽 화살표나 아래쪽 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-146">To change the order of the conditions, select a condition by clicking to its left, and then click the up or down arrow.</span></span>  
  
    6.  <span data-ttu-id="60459-147">조건을 숨기려면 도메인 이름 왼쪽의 빼기 기호를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-147">To hide the conditions, click the minus sign to the left of the domain name.</span></span> <span data-ttu-id="60459-148">조건을 표시하려면 더하기 기호를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-148">Click the plus ign to display the conditions.</span></span>  
  
8.  <span data-ttu-id="60459-149">Then 절 창의 도메인 목록에서 if 절의 주체 외에 단일 도메인을 선택하여 Then 절을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="60459-149">Create the Then clause by selecting a single domain, other than the subject of the If clause, in the domain list in the Then clause pane.</span></span> <span data-ttu-id="60459-150">그런 다음 if 절을 만들 때와 동일한 단계를 사용하여 Then 절을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-150">Then build the Then clause using the same steps that you did in building the If clause.</span></span>  
  
9. <span data-ttu-id="60459-151">다음 테스트 절차를 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-151">Proceed to the testing procedure below.</span></span>  
  
##  <a name="test-cross-domain-rules"></a><a name="Test"></a> <span data-ttu-id="60459-152">도메인 간 규칙 테스트</span><span class="sxs-lookup"><span data-stu-id="60459-152">Test Cross-Domain Rules</span></span>  
  
1.  <span data-ttu-id="60459-153">도메인 간 규칙을 다음과 같이 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-153">Test the cross-domain rule as follows:</span></span>  
  
    1.  <span data-ttu-id="60459-154">복합 도메인 창의 오른쪽 위 모퉁이에서 **테스트 데이터에서 선택한 도메인 규칙 실행** 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-154">Click the **Run the selected domain rule on test data to** icon in the upper right-hand corner of the composite domain pane.</span></span>  
  
    2.  <span data-ttu-id="60459-155">**도메인 규칙 테스트** 대화 상자에서 **도메인 규칙에서 새 테스트 용어를 추가합니다.** 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-155">In the **Test Domain Rule** dialog box, click the **Adds a New Testing Term for the Domain Rule** icon.</span></span>  
  
    3.  <span data-ttu-id="60459-156">If 절과 연결된 단일 도메인 및 Then 절과 연결된 단일 도메인에 대해 테스트 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-156">Enter test values for the single domain associated with the If clause and the single domain associated with the Then clause.</span></span> <span data-ttu-id="60459-157">If 절에 입력한 테스트 값은 해당 절의 조건과 일치해야 합니다. 그렇지 않으면 **유효성 검사** 열에 물음표가 입력되어 도메인 간 규칙이 테스트 데이터에 적용되지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="60459-157">The test values entered in the If clause must meet the conditions for that clause, or a question mark will be entered in the **Validity** column indicating that the cross-domain rule does not apply to the test data.</span></span>  
  
    4.  <span data-ttu-id="60459-158">**도메인 규칙에서 새 테스트 용어를 추가합니다.** 아이콘을 다시 클릭하여 다른 테스트 값 집합을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-158">Click the **Adds a new testing term for the domain rule** icon again to add another set of test values.</span></span>  
  
    5.  <span data-ttu-id="60459-159">**모든 용어에 대해 도메인 규칙 테스트** 아이콘을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-159">Click the **Test the Domain Rule on All the Terms** icon.</span></span> <span data-ttu-id="60459-160">테스트 값 집합이 유효하면 행의 **유효성 검사** 열에 확인 표시가 입력되고</span><span class="sxs-lookup"><span data-stu-id="60459-160">If a set of test values is valid, DQS will enter a check in the **Validity** column for the row.</span></span> <span data-ttu-id="60459-161">테스트 값 집합이 유효하지 않으면 행의 유효성 검사 열에 느낌표가 있는 삼각형이 입력됩니다.</span><span class="sxs-lookup"><span data-stu-id="60459-161">If the set of test values is not valid, DQS will enter a triangle with an exclamation point in the Validity column for the row.</span></span>  
  
    6.  <span data-ttu-id="60459-162">테스트 완료 후 **복합 도메인 규칙 테스트** 대화 상자에서 **닫기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-162">After your testing is complete, click **Close** in the **Test Composite Domain Rule** dialog box.</span></span>  
  
2.  <span data-ttu-id="60459-163">도메인 간 규칙을 완성하면 **End the Domain Management Activity** 에서 설명한 대로 [마침](../../2014/data-quality-services/end-the-domain-management-activity.md)을 클릭하여 도메인 관리 작업을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="60459-163">When you have completed your cross-domain rules, click **Finish** to complete the domain management activity, as described in [End the Domain Management Activity](../../2014/data-quality-services/end-the-domain-management-activity.md).</span></span>  
  
##  <a name="follow-up-after-creating-a-cross-domain-rule"></a><a name="FollowUp"></a> <span data-ttu-id="60459-164">후속 작업: 도메인 간 규칙을 만든 후</span><span class="sxs-lookup"><span data-stu-id="60459-164">Follow Up: After Creating a Cross-Domain Rule</span></span>  
 <span data-ttu-id="60459-165">도메인 간 규칙을 만든 후 도메인에 대해 다른 도메인 관리 태스크를 수행하거나, 기술 자료 검색을 수행하여 도메인에 정보를 추가하거나, 도메인에 일치 정책을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60459-165">After you create a cross-down rule, you can perform other domain management tasks on the domain, you can perform knowledge discovery to add knowledge to the domain, or you can add a matching policy to the domain.</span></span> <span data-ttu-id="60459-166">자세한 내용은 [기술 자료 검색 수행](../../2014/data-quality-services/perform-knowledge-discovery.md), [도메인 관리](../../2014/data-quality-services/managing-a-domain.md) 또는 [일치 정책 만들기](../../2014/data-quality-services/create-a-matching-policy.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="60459-166">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
  
