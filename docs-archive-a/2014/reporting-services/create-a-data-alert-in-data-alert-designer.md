---
title: 데이터 경고 디자이너에서 데이터 경고 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8464ab9d-afe1-4490-955f-9f3319bcbf8d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 19c3001d4663848c009a353baa068f237d4a0b5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735123"
---
# <a name="create-a-data-alert-in-data-alert-designer"></a><span data-ttu-id="f2509-102">데이터 경고 디자이너에서 데이터 경고 만들기</span><span class="sxs-lookup"><span data-stu-id="f2509-102">Create a Data Alert in Data Alert Designer</span></span>
  <span data-ttu-id="f2509-103">데이터 경고 디자이너에서 데이터 경고 정의를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-103">You create data alert definitions in Data Alert Designer.</span></span> <span data-ttu-id="f2509-104">경고 정의를 저장한 후 데이터 경고 디자이너에서 해당 정의를 다시 열어 편집한 후 다시 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-104">After you save the alert definitions, you can reopen, edit, and then resave them in Data Alert Designer.</span></span> <span data-ttu-id="f2509-105">경고 정의 편집에 대한 자세한 내용은 [데이터 경고 관리자에서 내 데이터 경고 관리](manage-my-data-alerts-in-data-alert-manager.md) 및 [경고 디자이너에서 데이터 경고 편집](edit-a-data-alert-in-alert-designer.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f2509-105">For information about editing alert definitions, see [Manage My Data Alerts in Data Alert Manager](manage-my-data-alerts-in-data-alert-manager.md) and [Edit a Data Alert in Alert Designer](edit-a-data-alert-in-alert-designer.md).</span></span>

### <a name="to-create-a-data-alert-definition"></a><span data-ttu-id="f2509-106">데이터 경고 정의를 만들려면</span><span class="sxs-lookup"><span data-stu-id="f2509-106">To create a data alert definition</span></span>

1.  <span data-ttu-id="f2509-107">데이터 경고 정의를 만들 보고서가 포함된 SharePoint 라이브러리를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-107">Locate the SharePoint library that contains the report that you want to create a data alert definition for.</span></span>

2.  <span data-ttu-id="f2509-108">보고서를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-108">Click the report.</span></span>

     <span data-ttu-id="f2509-109">보고서가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-109">The report runs.</span></span> <span data-ttu-id="f2509-110">보고서에 매개 변수가 있으면 경고 메시지를 받을 대상 데이터가 보고서에 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-110">If the report is parameterized, verify that the report shows the data that you want to receive alert messages about.</span></span> <span data-ttu-id="f2509-111">관심이 있는 열 또는 값이 표시되지 않으면 다른 매개 변수 값을 사용하여 보고서를 다시 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-111">If you do not see the columns or values you are interested in, you might want to rerun the report, using different parameter values.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="f2509-112">보고서를 실행하기 위해 선택한 매개 변수 값은 경고 정의에 저장되며 경고 정의 처리 단계의 일환으로 보고서를 다시 실행할 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-112">The parameter values you chose to run the report are saved in the alert definition and will be used when report is rerun as a step in processing the alert definition.</span></span> <span data-ttu-id="f2509-113">다른 매개 변수 값을 사용하려면 새 경고 정의를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-113">To use different parameter values, you must create a new alert definition.</span></span>

3.  <span data-ttu-id="f2509-114">**동작** 메뉴에서 **새 데이터 경고**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-114">On the **Actions** menu, click **New Data Alert**.</span></span>

     <span data-ttu-id="f2509-115">다음 그림에서는 **동작** 메뉴를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-115">The following picture shows the **Actions** menu.</span></span>

     <span data-ttu-id="f2509-116">![SharePoint 라이브러리에서 경고 디자이너 열기](media/rs-openalertdesigneriw.gif "SharePoint 라이브러리에서 경고 디자이너 열기")</span><span class="sxs-lookup"><span data-stu-id="f2509-116">![Open Alert Designer from SharePoint library](media/rs-openalertdesigneriw.gif "Open Alert Designer from SharePoint library")</span></span>

     <span data-ttu-id="f2509-117">데이터 경고 디자이너가 열리고 보고서가 생성하는 첫 번째 데이터 피드의 처음 100개 행이 테이블에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-117">The Data Alert Designer opens, showing the first 100 rows of the first data feed that the report generates in a table.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="f2509-118">**새 데이터 경고** 옵션이 표시되지 않을 경우 경고 서비스가 SharePoint 사이트에 구성되어 있지 않거나 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 버전에 데이터 경고가 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-118">If you do not see the **New Data Alert** option, the alerting service is not configured on the SharePoint site or the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] edition does not include data alerts.</span></span> <span data-ttu-id="f2509-119">자세한 내용은 [Reporting Services SharePoint Service 및 서비스 애플리케이션](../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f2509-119">For more information, see [Reporting Services SharePoint Service and Service Applications](../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md).</span></span>
    > 
    >  <span data-ttu-id="f2509-120">**새 데이터 경고** 옵션이 회색으로 표시될 경우에는 보고서 데이터 원본이 통합 보안 자격 증명을 사용하거나 자격 증명을 요청하도록 구성되어 있는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-120">If the **New Data Alert** option is grayed, the report data source is configured to use integrated security credentials or prompt for credentials.</span></span> <span data-ttu-id="f2509-121">**새 데이터 경고** 옵션을 사용하려면 저장된 자격 증명을 사용하거나 자격 증명을 아예 사용하지 않도록 데이터 원본을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-121">To make the **New Data Alert** option available, you must update the data source to use stored credentials or no credentials.</span></span>

     <span data-ttu-id="f2509-122">데이터 피드의 이름이 **보고서 데이터 이름** 드롭다운 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-122">The name of the data feed appears in **Report data name** drop-down list.</span></span>

4.  <span data-ttu-id="f2509-123">필요한 경우 **보고서 데이터 이름** 드롭다운 목록에서 다른 데이터 피드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-123">Optionally, select a different data feed in the **Report data name** drop-down list.</span></span>

     <span data-ttu-id="f2509-124">보고서에서 데이터 피드가 생성되지 않으면 보고서에 대해 경고 정의를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-124">If no data feed is generated from the report, you cannot create an alert definition for the report.</span></span> <span data-ttu-id="f2509-125">보고서의 레이아웃에 따라 각 데이터 피드의 내용이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-125">The layout of the report determines the content of each data feed.</span></span> <span data-ttu-id="f2509-126">자세한 내용은 [보고서에서 데이터 피드 생성 &#40;보고서 작성기 및 SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f2509-126">For more information see, [Generating Data Feeds from Reports &#40;Report Builder and SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md).</span></span>

5.  <span data-ttu-id="f2509-127">필요에 따라 **경고 이름** 텍스트 상자에서 기본 이름을 보다 의미 있는 이름으로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-127">Optionally, in the **Alert name** text box, update the default name to be more meaningful.</span></span>

     <span data-ttu-id="f2509-128">경고 정의의 기본 이름은 보고서 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-128">The default name of the alert definition is the name of the report.</span></span> <span data-ttu-id="f2509-129">경고 정의 이름을 반드시 고유한 이름으로 지정해야 하는 것은 아니지만 이렇게 하지 않으면 나중에 데이터 경고 관리자에서 경고 목록을 볼 때 경고 정의를 구분하기가 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-129">Alert definition names do not have to be unique, which can make it difficult to tell them apart when you later view the list of your alerts in Data Alert Manager.</span></span> <span data-ttu-id="f2509-130">따라서 경고 정의에 의미 있고 고유한 이름을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-130">It is recommended that you use meaningful and unique names for your alert definitions.</span></span>

6.  <span data-ttu-id="f2509-131">필요에 따라 기본 데이터 옵션을 **데이터 피드의 데이터가 다음을 포함함**에서 **데이터 피드의 데이터가 다음을 포함하지 않음**으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-131">Optionally, change the default data option from **any data in the data feed has** to **no data in the data feed has**.</span></span>

7.  <span data-ttu-id="f2509-132">**규칙 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-132">Click **Add rule**.</span></span>

     <span data-ttu-id="f2509-133">데이터 피드의 열 목록이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-133">A list of the columns in the data feed appears.</span></span>

8.  <span data-ttu-id="f2509-134">목록에서 규칙에 사용할 열을 선택한 다음 비교 연산자를 선택하고 임계값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-134">In the list, select the column that you want to use in the rule, and then select a comparison operator and enter the threshold value.</span></span>

     <span data-ttu-id="f2509-135">선택한 열의 데이터 형식에 따라 다른 비교 연산자가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-135">Depending on the data type of the selected column, different comparison operators are listed.</span></span> <span data-ttu-id="f2509-136">열에 날짜 데이터 형식이 포함된 경우 해당 규칙의 임계값 옆에 달력 아이콘이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-136">If the column has a date data type, a calendar icon displays next to threshold value for the rule.</span></span> <span data-ttu-id="f2509-137">달력에서 날짜를 클릭하거나 날짜를 입력하여 데이터를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-137">You can enter a data by clicking a date in the calendar or typing the date.</span></span>

     <span data-ttu-id="f2509-138">데이터 경고 디자이너는 **값 입력 모드** 및 **필드 선택 모드**의 두 가지 비교 모드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-138">Data Alert Designer provides two comparison modes: **Value Entry Mode** and **Field Selection Mode**.</span></span> <span data-ttu-id="f2509-139">기본 모드는 **값 입력 모드**입니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-139">The default mode is **Value Entry Mode**.</span></span> <span data-ttu-id="f2509-140">**값 입력 모드** 에 있고 **다음인 경우** 비교를 사용하는 경우에만 OR 절을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-140">You can add OR clauses only when you are in **Value Entry Mode** and are using the **is** comparison.</span></span>

9. <span data-ttu-id="f2509-141">OR 절을 추가하려면 아래쪽 화살표를 클릭한 다음 **값 입력 모드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-141">To add an OR clause, click the down-arrow, and then click **Value Entry Mode**.</span></span>

10. <span data-ttu-id="f2509-142">비교 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-142">Type the comparison value.</span></span>

11. <span data-ttu-id="f2509-143">필요에 따라 줄임표 **(...)** 를 다시 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-143">Optionally, click the ellipsis **(...)** again.</span></span>

     <span data-ttu-id="f2509-144">첫 번째 절을 포함 하는 줄에 줄임표 **(...)** 가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-144">The ellipsis **(...)** appears on the line that contains the first clause.</span></span>

     <span data-ttu-id="f2509-145">OR 절은 AND 규칙 아래와 해당 규칙 내에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-145">An OR clause is added below and within the AND rule.</span></span>

12. <span data-ttu-id="f2509-146">필요에 따라 아래쪽 화살표를 클릭하고 **필드 선택 모드**를 선택한 다음 목록에서 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-146">Optionally, click the down-arrow, select **Field Selection Mode**, and then select a column in the list.</span></span>

     <span data-ttu-id="f2509-147">또는 절을 추가 하기 위해 클릭 하는 줄임표 **(...)** 가 사라졌습니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-147">You will notice that the ellipsis **(...)** that you click to add OR clauses has disappeared.</span></span>

13. <span data-ttu-id="f2509-148">필요에 따라 **규칙 추가** 를 다시 클릭하여 규칙을 더 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-148">Optionally, click **Add rule** again to add additional rules.</span></span>

     <span data-ttu-id="f2509-149">규칙은 AND 논리 연산자를 사용하여 결합됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-149">The rules are combined by using the AND logical operator.</span></span>

14. <span data-ttu-id="f2509-150">되풀이 목록에서 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-150">Select an option in the recurrence list.</span></span> <span data-ttu-id="f2509-151">되풀이 유형에 따라 간격을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-151">Depending on the type of recurrence, enter an interval.</span></span>

15. <span data-ttu-id="f2509-152">필요에 따라 **고급**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-152">Optionally, click **Advanced**.</span></span>

16. <span data-ttu-id="f2509-153">필요에 따라 다른 날짜를 입력하거나 달력을 열고 달력에서 날짜를 클릭하여 경고 메시지가 시작될 날짜를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-153">Optionally, change the date that the alert message starts on by typing a different date or opening the calendar, and then clicking a date in the calendar.</span></span>

     <span data-ttu-id="f2509-154">기본 시작 날짜는 현재 날짜입니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-154">The default start date is the current date.</span></span>

17. <span data-ttu-id="f2509-155">필요에 따라 **경고 중지 시간**옆에 있는 확인란을 선택한 다음 경고 메시지를 중지할 날짜를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-155">Optionally, select the checkbox located next to **Stop alert on**, and then choose a date to stop the alert message.</span></span>

     <span data-ttu-id="f2509-156">기본적으로 경고 메시지에는 중지 날짜가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-156">By default, an alert message has no stop date.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="f2509-157">경고 메시지를 중지해도 경고 정의는 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-157">Stopping an alert message does not delete the alert definition.</span></span> <span data-ttu-id="f2509-158">경고 메시지를 중지한 후 시작 날짜와 중지 날짜를 업데이트하여 해당 메시지를 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-158">After you stop an alert message, you can restart it by updating the start and stop dates.</span></span> <span data-ttu-id="f2509-159">경고 정의 삭제에 대한 자세한 내용은 [데이터 경고 관리자에서 내 데이터 경고 관리](manage-my-data-alerts-in-data-alert-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f2509-159">For information about deleting alert definitions, see [Manage My Data Alerts in Data Alert Manager](manage-my-data-alerts-in-data-alert-manager.md).</span></span>

18. <span data-ttu-id="f2509-160">필요에 따라 **결과가 변경될 때만 메시지 보내기** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-160">Optionally, clear the **Send message only if results change** checkbox.</span></span>

     <span data-ttu-id="f2509-161">경고 메시지를 자주 보내는 경우에는 중복된 정보를 방지하기 위해 이 확인란의 선택을 취소하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="f2509-161">If you send alert messages frequently, redundant information might not be welcome and you should not clear this checkbox.</span></span>

19. <span data-ttu-id="f2509-162">경고 메시지를 받는 사람의 전자 메일 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-162">Enter the email addresses of alert message recipients.</span></span> <span data-ttu-id="f2509-163">세미콜론을 사용하여 주소를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-163">Separate addresses with semicolons.</span></span>

     <span data-ttu-id="f2509-164">경고 정의를 만든 사용자의 메일 주소를 사용할 수 있는 경우 **받는 사람** 상자에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-164">If the email address of the person who created the alert definition is available, it is added to the **Recipient(s)** box.</span></span>

20. <span data-ttu-id="f2509-165">필요에 따라 **제목** 입력란에서 경고 메시지의 제목 줄을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-165">Optionally, in the **Subject** text box, update the Subject line of the alert message.</span></span>

     <span data-ttu-id="f2509-166">기본 제목은 \*\*에 대 한 \<data alert name> 데이터 경고 \*\*입니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-166">The default Subject is **Data alert for \<data alert name>**.</span></span>

21. <span data-ttu-id="f2509-167">필요에 따라 **설명** 입력란에 경고 메시지에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-167">Optionally, in the **Description** text box, type a description of the alert message.</span></span>

22. <span data-ttu-id="f2509-168">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f2509-168">Click **Save**.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2509-169">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f2509-169">See Also</span></span>
 <span data-ttu-id="f2509-170">[경고 관리자를 위한](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) 데이터 [경고 디자이너](../../2014/reporting-services/data-alert-designer.md) 데이터 경고 관리자 [Reporting Services 데이터 경고](../ssms/agent/alerts.md)</span><span class="sxs-lookup"><span data-stu-id="f2509-170">[Data Alert Designer](../../2014/reporting-services/data-alert-designer.md) [Data Alert Manager for Alerting Administrators](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) [Reporting Services Data Alerts](../ssms/agent/alerts.md)</span></span>


