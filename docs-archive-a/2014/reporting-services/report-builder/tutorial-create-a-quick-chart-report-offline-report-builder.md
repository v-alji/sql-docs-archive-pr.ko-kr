---
title: '자습서: 오프라인에서 빠른 차트 보고서 만들기(보고서 작성기) | Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports, creating
- tutorials, getting started
- creating reports
ms.assetid: 6b1db67a-cf75-494c-b70c-09f1e6a8d414
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 51a9e648550a0108f47e3d93d75267ab0c1c24f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648818"
---
# <a name="tutorial-create-a-quick-chart-report-offline-report-builder"></a><span data-ttu-id="92e53-102">자습서: 오프라인에서 빠른 차트 보고서 만들기(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="92e53-102">Tutorial: Create a Quick Chart Report Offline (Report Builder)</span></span>
  <span data-ttu-id="92e53-103">이 자습서에서는 마법사를 사용하여 원형 차트를 만든 다음 차트를 어떤 식으로 수정할 수 있는지 보여 주기 위해 차트를 조금 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-103">In this tutorial, you'll create a pie chart by using a wizard, and then you'll modify it a little, just to get an idea of what's possible.</span></span> <span data-ttu-id="92e53-104">이 자습서는 다음 두 가지 방법으로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-104">You can do this tutorial two different ways.</span></span> <span data-ttu-id="92e53-105">두 방법 모두 다음 그림에 나와 있는 것과 같은 원형 차트와 동일한 결과를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-105">Both methods have the same outcome-a pie chart like the one in the following illustration:</span></span>

 <span data-ttu-id="92e53-106">![실행 뷰에 표시된 "My First Pie Chart"](../media/rs-my1stpierunview.gif "실행 뷰의 내 첫 번째 원형 차트")</span><span class="sxs-lookup"><span data-stu-id="92e53-106">!["My First Pie Chart" in Run view](../media/rs-my1stpierunview.gif "My First Pie Chart in Run view")</span></span>

## <a name="prerequisites"></a><span data-ttu-id="92e53-107">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="92e53-107">Prerequisites</span></span>
 <span data-ttu-id="92e53-108">XML 데이터나 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 쿼리를 사용하려면 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 보고서 작성기에 대한 액세스 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-108">Whether you use XML data or a [!INCLUDE[tsql](../../../includes/tsql-md.md)] query, you need to have access to [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] Report Builder.</span></span> <span data-ttu-id="92e53-109">보고서 관리자나 SharePoint 사이트에서 사용할 수 있는 ClickOnce 버전 또는 독립 실행형 버전을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-109">You can run the stand-alone version or the ClickOnce version available from Report Manager or a SharePoint site.</span></span> <span data-ttu-id="92e53-110">ClickOnce 버전의 경우 첫 번째 단계, 즉 보고서 작성기를 여는 방법만 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-110">Only the first step, how to open Report Builder, is different for ClickOnce versions.</span></span> <span data-ttu-id="92e53-111">자세한 내용은 [설치, 제거 및 보고서 작성기 지원](../install-uninstall-and-report-builder-support.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="92e53-111">For more information, see [Install, Uninstall, and Report Builder Support](../install-uninstall-and-report-builder-support.md).</span></span>

##  <a name="two-ways-to-do-this-tutorial"></a><a name="TwoWays"></a> <span data-ttu-id="92e53-112">이 자습서에서 수행하는 두 가지 방법</span><span class="sxs-lookup"><span data-stu-id="92e53-112">Two Ways To Do This Tutorial</span></span>

-   [<span data-ttu-id="92e53-113">XML 데이터로 원형 차트 만들기</span><span class="sxs-lookup"><span data-stu-id="92e53-113">Create the pie chart with XML data</span></span>](#CreatePieChartXML)

-   [<span data-ttu-id="92e53-114">데이터를 포함하는 Transact-SQL 쿼리로 원형 차트 만들기</span><span class="sxs-lookup"><span data-stu-id="92e53-114">Create the pie chart with a Transact-SQL query that contains data</span></span>](#CreatePieQueryData)

### <a name="using-xml-data-for-this-tutorial"></a><span data-ttu-id="92e53-115">이 자습서에서 XML 데이터 사용</span><span class="sxs-lookup"><span data-stu-id="92e53-115">Using XML data for this tutorial</span></span>
 <span data-ttu-id="92e53-116">이 항목에서 복사한 XML 데이터를 사용하여 마법사에 붙여 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-116">You can use XML data that you copy from this topic and paste into the wizard.</span></span> <span data-ttu-id="92e53-117">보고서 서버나 SharePoint 통합 모드에 있는 보고서 서버에 연결되어 있지 않아도 되며 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]의 인스턴스에 액세스하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-117">You don't need to be connected to a report server or a report server in SharePoint integrated mode, and you don't need access to an instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>

 [<span data-ttu-id="92e53-118">XML 데이터로 원형 차트 만들기</span><span class="sxs-lookup"><span data-stu-id="92e53-118">Create the pie chart with XML data</span></span>](#CreatePieChartXML)

### <a name="using-a-transact-sql-query-that-contains-data-for-this-tutorial"></a><span data-ttu-id="92e53-119">이 자습서에서 데이터가 포함된 Transact-SQL 쿼리 사용</span><span class="sxs-lookup"><span data-stu-id="92e53-119">Using a Transact-SQL query that contains data for this tutorial</span></span>
 <span data-ttu-id="92e53-120">이 항목에서 데이터가 포함된 쿼리를 복사하여 마법사에 붙여 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-120">You can copy a query with data included in it from this topic and paste it into the wizard.</span></span> <span data-ttu-id="92e53-121">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]의 인스턴스 이름과 모든 데이터베이스에 대한 읽기 전용 액세스 권한이 있는 자격 증명이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-121">You will need the name of an instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] and credentials sufficient for read-only access to any database.</span></span> <span data-ttu-id="92e53-122">자습서의 데이터 세트 쿼리에서는 리터럴 데이터를 사용하지만 쿼리를 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]의 인스턴스에서 처리해야 보고서 데이터 세트에 필요한 메타데이터가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-122">The dataset query in the tutorial uses literal data, but the query must be processed by an instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] to return the metadata that is required for a report dataset.</span></span>

 <span data-ttu-id="92e53-123">[!INCLUDE[tsql](../../../includes/tsql-md.md)] 쿼리를 사용하는 경우 좋은 점은, 다른 모든 보고서 작성기 자습서에서도 같은 방법을 사용하므로 다른 자습서를 사용할 때 수행할 작업을 미리 알게 된다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-123">The advantage of using the [!INCLUDE[tsql](../../../includes/tsql-md.md)] query is that all the other Report Builder tutorials use the same method, so when you do the other tutorials, you will already know what to do.</span></span>

 <span data-ttu-id="92e53-124">[!INCLUDE[tsql](../../../includes/tsql-md.md)] 쿼리를 사용하려면 몇 가지 다른 필수 구성 요소가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-124">The [!INCLUDE[tsql](../../../includes/tsql-md.md)] query does require a few other prerequisites.</span></span> <span data-ttu-id="92e53-125">자세한 내용은 [자습서의 사전 요구 사항 &#40;보고서 작성기&#41;](../report-builder-tutorials.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="92e53-125">For more information, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../report-builder-tutorials.md).</span></span>

 [<span data-ttu-id="92e53-126">데이터를 포함하는 Transact-SQL 쿼리로 원형 차트 만들기</span><span class="sxs-lookup"><span data-stu-id="92e53-126">Create the pie chart with a Transact-SQL query that contains data</span></span>](#CreatePieQueryData)

## <a name="also-in-this-article"></a><span data-ttu-id="92e53-127">문서 내용</span><span class="sxs-lookup"><span data-stu-id="92e53-127">Also in This Article</span></span>
 [<span data-ttu-id="92e53-128">마법사를 실행 한 후</span><span class="sxs-lookup"><span data-stu-id="92e53-128">After You Run the Wizard</span></span>](#AfterWizard)

 [<span data-ttu-id="92e53-129">다음 단계</span><span class="sxs-lookup"><span data-stu-id="92e53-129">What's Next</span></span>](#WhatsNext)

##  <a name="creating-the-pie-chart-with-xml-data"></a><a name="CreatePieChartXML"></a><span data-ttu-id="92e53-130">XML 데이터로 원형 차트 만들기</span><span class="sxs-lookup"><span data-stu-id="92e53-130">Creating the pie chart with XML data</span></span>

#### <a name="to-create-the-pie-chart-with-xml-data"></a><span data-ttu-id="92e53-131">XML 데이터로 원형 차트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="92e53-131">To create the pie chart with XML data</span></span>

1.  <span data-ttu-id="92e53-132">**시작**을 클릭하고 **프로그램**, **Microsoft SQL Server 2012 보고서 작성기**를 차례로 가리킨 다음 **보고서 작성기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-132">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>

     <span data-ttu-id="92e53-133">**시작** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-133">The **Getting Started** dialog box appears.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="92e53-134">**시작** 대화 상자가 나타나지 않으면 **보고서 작성기** 단추에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-134">If the **Getting Started** dialog box does not appear, from the **Report Builder** button, click **New**.</span></span>

2.  <span data-ttu-id="92e53-135">왼쪽 창에서 **보고서** 가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-135">In the left pane, verify that **Report** is selected.</span></span>

3.  <span data-ttu-id="92e53-136">오른쪽 창에서 **차트 마법사**를 클릭한 다음 **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-136">In the right pane, click **Chart Wizard**, and then click **Create**.</span></span>

4.  <span data-ttu-id="92e53-137">**데이터 세트 선택** 페이지에서 **데이터 세트 만들기**를 클릭한 후, **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-137">In the **Choose a dataset** page, click **Create a dataset**, and then click **Next**.</span></span>

5.  <span data-ttu-id="92e53-138">**데이터 원본에 대한 연결 선택** 페이지에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-138">In the **Choose a connection to a data source** page, click **New**.</span></span>

     <span data-ttu-id="92e53-139">**데이터 원본 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-139">The **Data Source Properties** dialog box opens.</span></span>

6.  <span data-ttu-id="92e53-140">데이터 원본 이름으로 원하는 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-140">You can name a data source anything you want.</span></span> <span data-ttu-id="92e53-141">**이름** 상자에 **MyPieChart**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-141">In the **Name** box, type **MyPieChart**.</span></span>

7.  <span data-ttu-id="92e53-142">**연결 유형 선택** 상자에서 XML을 클릭 **합니다.**</span><span class="sxs-lookup"><span data-stu-id="92e53-142">In the **Select connection type** box, click **XML.**</span></span>

8.  <span data-ttu-id="92e53-143">**자격 증명** 탭을 클릭 하 고 **현재 Windows 사용자 사용을 선택 합니다. Kerberos 위임이 필요할 수 있습니다**. 그런 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-143">Click the **Credentials** tab, select **Use current Windows user. Kerberos delegation may be required**, and then click **OK**.</span></span>

9. <span data-ttu-id="92e53-144">**데이터 원본에 대한 연결 선택** 페이지에서 **MyPieChart**를 클릭하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-144">In the **Choose a connection to a data source** page, click **MyPieChart**, and then click **Next**.</span></span>

10. <span data-ttu-id="92e53-145">다음 텍스트를 복사 하 여 **쿼리 디자인** 페이지의 가운데에 있는 크게 상자에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-145">Copy the following text and paste it in the large box in the center of the **Design a query** page.</span></span>

    ```
    <Query>
    <ElementPath>Root /S  {@Sales (Integer)} /C {@FullName} </ElementPath>
    <XmlData>
    <Root>
    <S Sales="150">
      <C FullName="Jae Pak" />
    </S>
    <S Sales="350">
      <C FullName="Jillian  Carson" />
    </S>
    <S Sales="250">
      <C FullName="Linda C Mitchell" />
    </S>
    <S Sales="500">
      <C FullName="Michael Blythe" />
    </S>
    <S Sales="450">
      <C FullName="Ranjit Varkey" />
    </S>
    </Root>
    </XmlData>
    </Query>
    ```

11. <span data-ttu-id="92e53-146">(옵션) 실행 단추(**!**)를 클릭하여 차트의 기반으로 사용될 데이터를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-146">(Optional) Click the Run button (**!**) to see the data your chart will be based on.</span></span>

12. <span data-ttu-id="92e53-147">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-147">Click **Next**.</span></span>

13. <span data-ttu-id="92e53-148">**차트 종류 선택** 페이지에서 **원형**을 클릭하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-148">In the **Choose a chart type** page, click **Pie**, and then click **Next**.</span></span>

14. <span data-ttu-id="92e53-149">**차트 필드 정렬** 페이지의 **사용 가능한 필드** 상자에서 **Sales** 필드를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-149">In the **Arrange chart fields** page, double-click the **Sales** field in the **Available fields** box.</span></span>

     <span data-ttu-id="92e53-150">Sales 필드는 숫자 값이므로 자동으로 **값** 상자로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-150">Note that it automatically moves to the **Values** box, because it is a numerical value.</span></span>

15. <span data-ttu-id="92e53-151">**사용 가능한 필드** 상자에서 **FullName** 필드를 **범주** 상자로 끌어 오거나 FullName 필드를 두 번 클릭하여 **범주** 상자로 이동한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-151">Drag the **FullName** field from the **Available fields** box to the **Categories** box (or double-click it; it will go to the **Categories** box), and then click **Next**.</span></span>

16. <span data-ttu-id="92e53-152">**스타일 선택** 페이지에서 **해양** 는 기본적으로 선택 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-152">In the **Choose a style** page, **Ocean** is selected by default.</span></span> <span data-ttu-id="92e53-153">다른 스타일을 클릭하여 모양을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-153">Click the other styles to see what they look like.</span></span>

17. <span data-ttu-id="92e53-154">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-154">Click **Finish**.</span></span>

     <span data-ttu-id="92e53-155">이제 새 원형 차트 보고서가 디자인 화면에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-155">You're now looking at your new pie chart report on the design surface.</span></span> <span data-ttu-id="92e53-156">이 원형 차트 보고서에는 보고서 내용이 대략적으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-156">What you see is representational.</span></span> <span data-ttu-id="92e53-157">영업 사원 이름 대신 Full Name 1, Full Name 2 등의 범례가 표시되고 원형 차트의 각 조각 크기도 정확하게 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-157">The legend reads Full Name 1, Full Name 2, etc., rather than the salespeople's names, and the size of the slices of pie are not accurate.</span></span> <span data-ttu-id="92e53-158">이 보고서는 단순히 보고서의 대략적인 모양을 보여 주는 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-158">This is just to give you an idea of what your report will look like.</span></span>

18. <span data-ttu-id="92e53-159">실제 원형 차트를 보려면 리본 메뉴의 **홈** 탭에서 **실행** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-159">To see your actual pie chart, click **Run** on the **Home** tab of the Ribbon.</span></span>

 <span data-ttu-id="92e53-160">![맨 위로 이동 링크와 함께 사용 되는 화살표 아이콘](../../2014-toc/media/uparrow16x16.gif "맨 위로 이동 링크와 함께 사용되는 화살표 아이콘") [Back to Top](#TwoWays)</span><span class="sxs-lookup"><span data-stu-id="92e53-160">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#TwoWays)</span></span>

##  <a name="creating-the-pie-chart-with-a-tsql-query"></a><a name="CreatePieQueryData"></a><span data-ttu-id="92e53-161">[!INCLUDE[tsql](../../../includes/tsql-md.md)] 쿼리로 원형 차트 만들기</span><span class="sxs-lookup"><span data-stu-id="92e53-161">Creating the pie chart with a [!INCLUDE[tsql](../../../includes/tsql-md.md)] query</span></span>

#### <a name="to-create-the-pie-chart-with-a-tsql-query-that-contains-data"></a><span data-ttu-id="92e53-162">데이터를 포함하는 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 쿼리로 원형 차트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="92e53-162">To create the pie chart with a [!INCLUDE[tsql](../../../includes/tsql-md.md)] query that contains data</span></span>

1.  <span data-ttu-id="92e53-163">**시작**을 클릭하고 **프로그램**, **Microsoft SQL Server 2012 보고서 작성기**를 차례로 가리킨 다음 **보고서 작성기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-163">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>

2.  <span data-ttu-id="92e53-164">**새 보고서 또는 데이터 집합** 대화 상자의 왼쪽 창에서 **보고서** 가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-164">In the **New report or dataset** dialog box, verify that **Report** is selected in the left pane.</span></span>

3.  <span data-ttu-id="92e53-165">오른쪽 창에서 **차트 마법사**를 클릭한 다음 **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-165">In the right pane, click **Chart Wizard**, and then click **Create**.</span></span>

4.  <span data-ttu-id="92e53-166">**데이터 세트 선택** 페이지에서 **데이터 세트 만들기**를 클릭한 후, **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-166">In the **Choose a dataset** page, click **Create a dataset**, and then click **Next**.</span></span>

5.  <span data-ttu-id="92e53-167">**데이터 원본에 대한 연결 선택** 페이지에서 기존 데이터 원본을 선택하거나 보고서 서버를 찾아 데이터 원본을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-167">In the **Choose a connection to a data source** page, select an existing data source or browse to the report server and select a data source, and then click **Next**.</span></span> <span data-ttu-id="92e53-168">사용자 이름과 암호를 입력해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-168">You may need to enter a user name and password.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="92e53-169">적절한 권한만 가지고 있으면 선택하는 데이터 원본은 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-169">The data source you choose is unimportant, as long as you have adequate permissions.</span></span> <span data-ttu-id="92e53-170">데이터를 데이터 원본에서 가져오는 것은 아니기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-170">You will not be getting data from the data source.</span></span> <span data-ttu-id="92e53-171">자세한 내용은 [자습서의 사전 요구 사항 &#40;보고서 작성기&#41;](../report-builder-tutorials.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="92e53-171">For more information, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../report-builder-tutorials.md).</span></span>

6.  <span data-ttu-id="92e53-172">**쿼리 디자인** 페이지에서 **텍스트로 편집**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-172">On the **Design a Query** page, click **Edit as Text**.</span></span>

7.  <span data-ttu-id="92e53-173">쿼리 창에 다음 쿼리를 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-173">Paste the following query into the query pane:</span></span>

    ```
    SELECT 150 AS Sales, 'Jae Pak' AS FullName 
    UNION SELECT 350 AS Sales, 'Jillian Carson' AS FullName 
    UNION SELECT 250 AS Sales, 'Linda C Mitchell' AS FullName 
    UNION SELECT 500 AS Sales, 'Michael Blythe' AS FullName 
    UNION SELECT 450 AS Sales, 'Ranjit Varkey' AS FullName 
    ```

8.  <span data-ttu-id="92e53-174">(옵션) 실행 단추(**!**)를 클릭하여 차트의 기반으로 사용될 데이터를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-174">(Optional) Click the Run button (**!**) to see the data your chart will be based on.</span></span>

9. <span data-ttu-id="92e53-175">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-175">Click **Next**.</span></span>

10. <span data-ttu-id="92e53-176">**차트 종류 선택** 페이지에서 **원형**을 클릭하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-176">In the **Choose a chart type** page, click **Pie**, and then click **Next**.</span></span>

11. <span data-ttu-id="92e53-177">**차트 필드 정렬** 페이지의 **사용 가능한 필드** 상자에서 **Sales** 필드를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-177">In the **Arrange chart fields** page, double-click the **Sales** field in the **Available fields** box.</span></span>

     <span data-ttu-id="92e53-178">Sales 필드는 숫자 값이므로 자동으로 **값** 상자로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-178">Note that it automatically moves to the **Values** box, because it's a numerical value.</span></span>

12. <span data-ttu-id="92e53-179">**사용 가능한 필드** 상자에서 **FullName** 필드를 **범주** 상자로 끌어 오거나 FullName 필드를 두 번 클릭하여 **범주** 상자로 이동한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-179">Drag the **FullName** field from the **Available fields** box to the **Categories** box (or double-click it; it will go to the **Categories** box), and then click **Next**.</span></span>

13. <span data-ttu-id="92e53-180">**스타일 선택** 페이지에 Ocean이 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-180">In the **Choose a style** page, Ocean is selected by default.</span></span> <span data-ttu-id="92e53-181">다른 스타일을 클릭하여 모양을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-181">Click the other styles to see what they look like.</span></span>

14. <span data-ttu-id="92e53-182">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-182">Click **Finish**.</span></span>

     <span data-ttu-id="92e53-183">이제 새 원형 차트 보고서가 디자인 화면에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-183">You're now looking at your new pie chart report on the design surface.</span></span> <span data-ttu-id="92e53-184">이 원형 차트 보고서에는 보고서 내용이 대략적으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-184">What you see is representational.</span></span> <span data-ttu-id="92e53-185">영업 사원 이름 대신 Full Name 1, Full Name 2 등의 범례가 표시되고 원형 차트의 각 조각 크기도 정확하게 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-185">The legend reads Full Name 1, Full Name 2, etc., rather than the salespeople's names, and the size of the slices of pie are not accurate.</span></span> <span data-ttu-id="92e53-186">이 보고서는 단순히 보고서의 대략적인 모양을 보여 주는 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-186">This is just to give you an idea of what your report will look like.</span></span>

15. <span data-ttu-id="92e53-187">실제 원형 차트를 보려면 리본 메뉴의 **홈** 탭에서 **실행** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-187">To see your actual pie chart, click **Run** on the **Home** tab of the Ribbon.</span></span>

 <span data-ttu-id="92e53-188">![맨 위로 이동 링크와 함께 사용 되는 화살표 아이콘](../../2014-toc/media/uparrow16x16.gif "맨 위로 이동 링크와 함께 사용되는 화살표 아이콘") [Back to Top](#TwoWays)</span><span class="sxs-lookup"><span data-stu-id="92e53-188">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#TwoWays)</span></span>

##  <a name="after-you-run-the-wizard"></a><a name="AfterWizard"></a> <span data-ttu-id="92e53-189">마법사 실행 후 작업</span><span class="sxs-lookup"><span data-stu-id="92e53-189">After You Run the Wizard</span></span>
 <span data-ttu-id="92e53-190">원형 차트 보고서를 만들었으므로 이제 보고서를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-190">Now that you have your pie chart report, you can play with it.</span></span> <span data-ttu-id="92e53-191">리본 메뉴의 **실행** 탭에서 **디자인**을 클릭하면 계속해서 보고서를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-191">On the **Run** tab of the Ribbon, click **Design**, so you can continue modifying it.</span></span>

### <a name="make-the-chart-bigger"></a><span data-ttu-id="92e53-192">차트를 크게 만들기</span><span class="sxs-lookup"><span data-stu-id="92e53-192">Make the chart bigger</span></span>
 <span data-ttu-id="92e53-193">원형 차트를 좀 더 크게 만들어 봅니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-193">You may want the pie chart to be bigger.</span></span> <span data-ttu-id="92e53-194">차트의 요소가 아니라 차트를 클릭하여 선택한 다음 오른쪽 아래 모퉁이를 끌어 크기를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-194">Click the chart, but not on any element in the chart, to select it and drag the lower-right corner to resize it.</span></span>

### <a name="add-a-report-title"></a><span data-ttu-id="92e53-195">보고서 제목 추가</span><span class="sxs-lookup"><span data-stu-id="92e53-195">Add a report title</span></span>
 <span data-ttu-id="92e53-196">차트 위쪽의 **차트 제목** 을 선택하고 **Sales Pie Chart**와 같은 제목을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-196">Select the words **Chart title** at the top of the chart, and then type a title, such as **Sales Pie Chart**.</span></span>

### <a name="add-percentages"></a><span data-ttu-id="92e53-197">백분율 추가</span><span class="sxs-lookup"><span data-stu-id="92e53-197">Add percentages</span></span>

##### <a name="to-display-percentage-values-as-labels-on-a-pie-chart"></a><span data-ttu-id="92e53-198">원형 차트에 레이블로 백분율 값을 표시하려면</span><span class="sxs-lookup"><span data-stu-id="92e53-198">To display percentage values as labels on a pie chart</span></span>

1.  <span data-ttu-id="92e53-199">원형 차트를 마우스 오른쪽 단추로 클릭 하 고 **데이터 레이블 표시**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-199">Right-click on the pie chart and select **Show Data Labels**.</span></span> <span data-ttu-id="92e53-200">원형 차트의 각 조각 내에 데이터 레이블이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-200">The data labels should appear within each slice on the pie chart.</span></span>

2.  <span data-ttu-id="92e53-201">레이블을 마우스 오른쪽 단추로 클릭 하 고 **계열 레이블 속성**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-201">Right-click on the labels and select **Series Label Properties**.</span></span> <span data-ttu-id="92e53-202">**계열 레이블 속성** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-202">The **Series Label Properties** dialog box appears.</span></span>

3.  <span data-ttu-id="92e53-203">`#PERCENT{P0}` **레이블 데이터** 옵션에를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-203">Type `#PERCENT{P0}` for the **Label data** option.</span></span>

     <span data-ttu-id="92e53-204">`{P0}`을 추가하면 백분율이 소수 자릿수 없이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-204">The `{P0}` gives you the percentage without decimal places.</span></span> <span data-ttu-id="92e53-205">`#PERCENT`만 입력하면 숫자가 소수점 두 자리까지 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-205">If you type just `#PERCENT`, your numbers will have two decimal places.</span></span> <span data-ttu-id="92e53-206">`#PERCENT`는 자동으로 계산이나 기능을 수행하는 키워드이며 이외에도 많은 키워드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-206">`#PERCENT` is a keyword that performs a calculation or function for you; there are many others.</span></span>

 <span data-ttu-id="92e53-207">차트 레이블 및 범례를 사용자 지정하는 방법에 대한 자세한 내용은 [원형 차트에서 백분율 값 표시 &#40;보고서 작성기 및 SSRS&#41;](../report-design/display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md) 및 [범례 항목의 텍스트 변경 #40;보고서 작성기 및 SSRS&#41;](../report-design/chart-legend-change-item-text-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="92e53-207">For more information about customizing chart labels and legends, see [Display Percentage Values on a Pie Chart &#40;Report Builder and SSRS&#41;](../report-design/display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md) and [Change the Text of a Legend Item &#40;Report Builder and SSRS&#41;](../report-design/chart-legend-change-item-text-report-builder.md).</span></span>

 <span data-ttu-id="92e53-208">![맨 위로 이동 링크와 함께 사용 되는 화살표 아이콘](../../2014-toc/media/uparrow16x16.gif "맨 위로 이동 링크와 함께 사용되는 화살표 아이콘") [Back to Top](#TwoWays)</span><span class="sxs-lookup"><span data-stu-id="92e53-208">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#TwoWays)</span></span>

##  <a name="whats-next"></a><a name="WhatsNext"></a><span data-ttu-id="92e53-209">다음 단계</span><span class="sxs-lookup"><span data-stu-id="92e53-209">What's Next?</span></span>
 <span data-ttu-id="92e53-210">보고서 작성기에서 첫 번째 보고서를 만들었으므로 이제 다른 자습서를 수행하고 고유의 데이터로 보고서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-210">Now that you have created your first report in Report Builder, you are ready to try the other tutorials and to start creating reports from your own data.</span></span> <span data-ttu-id="92e53-211">보고서 작성기를 실행 하려면 연결 문자열을 사용 하 여 데이터베이스와 같은 데이터 원본에 액세스할 수 있는 권한이 있어야 합니다. *연결 문자열*은 실제로 사용자를 데이터 원본에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-211">To run Report Builder, you need permission to access your data sources, such as databases, with a *connection string*, which actually connects you to the data source.</span></span> <span data-ttu-id="92e53-212">시스템 관리자가 연결 문자열 정보를 가지고 있으며 사용자에 대해 데이터 원본 연결을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-212">Your system administrator will have this information and can set you up.</span></span>

 <span data-ttu-id="92e53-213">다른 자습서를 진행하려면 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]의 인스턴스 이름과 모든 데이터베이스에 대한 읽기 전용 액세스 권한이 있는 자격 증명만 있으면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-213">To work through the other tutorials, you need the name of an instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] and credentials sufficient for read-only access to any database.</span></span> <span data-ttu-id="92e53-214">데이터베이스 액세스 권한은 시스템 관리자가 대신 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-214">Your system administrator can also set that up for you.</span></span>

 <span data-ttu-id="92e53-215">마지막으로, 보고서를 보고서 서버나 보고서 서버와 통합된 SharePoint 사이트에 저장하려면 URL 및 해당 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-215">Finally, to save your reports to a report server or a SharePoint site that is integrated with a report server, you need the URL and permissions.</span></span> <span data-ttu-id="92e53-216">만든 보고서를 사용자의 컴퓨터에서 직접 실행할 수도 있지만 보고서 서버나 SharePoint 사이트에서 실행하면 더 많은 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-216">You can run any report you create directly from your computer, but reports have more functionality when run from the report server or SharePoint site.</span></span> <span data-ttu-id="92e53-217">자신이 만든 보고서나 다른 사용자의 보고서를 보고서가 게시된 보고서 서버나 SharePoint 사이트에서 실행할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-217">You need permissions to run your reports or others from the report server or SharePoint site where they are published.</span></span> <span data-ttu-id="92e53-218">시스템 관리자에게 액세스 권한을 요청하십시오.</span><span class="sxs-lookup"><span data-stu-id="92e53-218">Talk to your system administrator to obtain access.</span></span>

 <span data-ttu-id="92e53-219">시작하기 전에 몇 가지 개념이나 용어에 대해 알아 두면 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-219">It may help to read about some of the concepts and terms before you get started.</span></span> <span data-ttu-id="92e53-220">자세한 내용은 [보고서 제작 개념 &#40;보고서 작성기 및 SSRS&#41;](../report-design/report-authoring-concepts-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="92e53-220">For more information, see [Report Authoring Concepts &#40;Report Builder and SSRS&#41;](../report-design/report-authoring-concepts-report-builder-and-ssrs.md).</span></span> <span data-ttu-id="92e53-221">또한 처음 보고서를 만들 때는 사전에 시간을 들여</span><span class="sxs-lookup"><span data-stu-id="92e53-221">Also, spend some time planning, before you create your first report.</span></span> <span data-ttu-id="92e53-222">계획을 세우는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="92e53-222">It will be time well spent.</span></span> <span data-ttu-id="92e53-223">자세한 내용은 [보고서 계획 &#40;보고서 작성기&#41;](../report-design/planning-a-report-report-builder.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="92e53-223">For more information, see [Planning a Report &#40;Report Builder&#41;](../report-design/planning-a-report-report-builder.md).</span></span>

 <span data-ttu-id="92e53-224">![맨 위로 이동 링크와 함께 사용 되는 화살표 아이콘](../../2014-toc/media/uparrow16x16.gif "맨 위로 이동 링크와 함께 사용되는 화살표 아이콘") [Back to Top](#TwoWays)</span><span class="sxs-lookup"><span data-stu-id="92e53-224">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#TwoWays)</span></span>

## <a name="see-also"></a><span data-ttu-id="92e53-225">참고 항목</span><span class="sxs-lookup"><span data-stu-id="92e53-225">See Also</span></span>
 <span data-ttu-id="92e53-226">[2014 SQL Server의](report-builder-in-sql-server-2016.md) [자습서 &#40;보고서 작성기 보고서 작성기&#41;](../report-builder-tutorials.md)</span><span class="sxs-lookup"><span data-stu-id="92e53-226">[Tutorials &#40;Report Builder&#41;](../report-builder-tutorials.md) [Report Builder in SQL Server 2014](report-builder-in-sql-server-2016.md)</span></span>


