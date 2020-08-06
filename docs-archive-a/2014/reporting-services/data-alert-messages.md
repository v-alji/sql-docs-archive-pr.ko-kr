---
title: 데이터 경고 메시지 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6819720c-d848-4b90-9b51-89501b4f4645
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d50c3dd24c0057f695a9318c5eef7ad9e7540a45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652646"
---
# <a name="data-alert-messages"></a><span data-ttu-id="8c44d-102">데이터 경고 메시지</span><span class="sxs-lookup"><span data-stu-id="8c44d-102">Data Alert Messages</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="8c44d-103">데이터 경고는 데이터 경고 결과가 포함된 메시지와 오류 설명이 포함된 메시지의 두 가지 종류의 데이터 경고 메시지를 전자 메일로 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8c44d-103">data alerts deliver two types of data alert messages by email: Messages with data alert results and messages with error descriptions.</span></span> <span data-ttu-id="8c44d-104">결과가 포함된 메시지는 모든 받는 사람에게 유용하고 비즈니스 의사 결정을 내리는 데 중요한 보고서 데이터 변경 사항에 대해 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="8c44d-104">Messages with results keep all recipients informed about changes in report data that is of common interest and important to business decisions.</span></span> <span data-ttu-id="8c44d-105">오류가 발생하여 결과를 사용할 수 없는 경우 오류 메시지를 대신 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8c44d-105">If for some reason an error occurs and the results are not available, the error message is sent instead.</span></span>

 <span data-ttu-id="8c44d-106">또한 데이터 경고 정의 소유자는 데이터 경고 관리자에서 데이터 경고 인스턴스에 대한 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c44d-106">The owner of the data alert definition also can view information about the data alert instance in Data Alert Manager.</span></span> <span data-ttu-id="8c44d-107">자세한 내용은 [Data Alert Manager for SharePoint Users](../../2014/reporting-services/data-alert-manager-for-sharepoint-users.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c44d-107">For more information, see [Data Alert Manager for SharePoint Users](../../2014/reporting-services/data-alert-manager-for-sharepoint-users.md).</span></span>

##  <a name="data-alert-messages"></a><a name="DataAlertMessages"></a><span data-ttu-id="8c44d-108">데이터 경고 메시지</span><span class="sxs-lookup"><span data-stu-id="8c44d-108">Data Alert Messages</span></span>
 <span data-ttu-id="8c44d-109">다음 그림에서는 결과가 포함된 데이터 경고 메시지와 오류 설명이 포함된 경고 메시지를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8c44d-109">The following pictures show a data alert message with results and an alert message with an error description.</span></span>

 <span data-ttu-id="8c44d-110">**결과 메시지**</span><span class="sxs-lookup"><span data-stu-id="8c44d-110">**Results message**</span></span>

 <span data-ttu-id="8c44d-111">![결과가 포함된 데이터 경고 메일 메시지](media/rs-alertmessageresults.gif "결과가 포함된 데이터 경고 메일 메시지")</span><span class="sxs-lookup"><span data-stu-id="8c44d-111">![Data alert e-mail message with results](media/rs-alertmessageresults.gif "Data alert e-mail message with results")</span></span>

 <span data-ttu-id="8c44d-112">**오류 메시지**</span><span class="sxs-lookup"><span data-stu-id="8c44d-112">**Error message**</span></span>

 <span data-ttu-id="8c44d-113">![오류 메시지가 포함된 데이터 경고 메시지](media/rs-alertmessageerrror.gif "오류 메시지가 포함된 데이터 경고 메시지")</span><span class="sxs-lookup"><span data-stu-id="8c44d-113">![Data alert message with error message](media/rs-alertmessageerrror.gif "Data alert message with error message")</span></span>

 <span data-ttu-id="8c44d-114">메시지에는 동일한 유형의 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c44d-114">The messages include the same types of information.</span></span>

1.  <span data-ttu-id="8c44d-115">**다음 사람 대신** 에는 데이터 경고 정의를 만든 사용자의 이름이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c44d-115">**On behalf of** contains the name of the person who created the data alert definition.</span></span>

2.  <span data-ttu-id="8c44d-116">경고 정의에 설명을 지정한 경우 설명이 **다음 사람 대신**아래에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c44d-116">If you provided a description in the alert definition, it displays below **On behalf of**.</span></span>

3.  <span data-ttu-id="8c44d-117">**경고 결과** 는 경고 정의에 지정된 규칙을 만족하는 보고서 데이터 피드의 행을 테이블 형식으로 표시하거나 오류 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8c44d-117">**Alert Results** display the rows in the report data feed that satisfy the rules specified in the alert definition in a tabular format or display an error description.</span></span> <span data-ttu-id="8c44d-118">표시되는 행 수에 대한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8c44d-118">There is no limit on the number of rows that displays.</span></span>

4.  <span data-ttu-id="8c44d-119">**보고서로 이동** 은 경고 정의가 작성되는 보고서에 대한 링크입니다.</span><span class="sxs-lookup"><span data-stu-id="8c44d-119">**Go to report** is a link to the report that the alert definition is built upon.</span></span> <span data-ttu-id="8c44d-120">보고서가 이동되거나 삭제되어 링크가 유효하지 않은 경우 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c44d-120">If the link is not valid because the report was moved or deleted, an error message displays.</span></span>

5.  <span data-ttu-id="8c44d-121">**규칙** 은 경고 정의의 규칙과 절을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8c44d-121">**Rule(s)** lists the rules and clauses in the alert definition.</span></span> <span data-ttu-id="8c44d-122">이 정보를 통해 경고 결과를 확인하여 이해하고 결과를 축소하거나 확대하기 위해 변경할 데이터 경고 정의의 규칙을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c44d-122">This information helps you verify and understand the alert results and identify rules in the data alert definition that you might want to change to narrow or broaden results.</span></span>

6.  <span data-ttu-id="8c44d-123">**보고서 매개 변수** 는 보고서를 실행할 때 사용된 매개 변수와 매개 변수 값을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8c44d-123">**Report parameters** list the parameters and parameter values that were used when the report was run.</span></span> <span data-ttu-id="8c44d-124">매개 변수와 매개 변수 값을 통해 경고 결과를 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c44d-124">Parameters and parameter values help you understand the alert results.</span></span>

7.  <span data-ttu-id="8c44d-125">**컨텍스트 값** 은 보고서 데이터 영역 밖에 있는 보고서 항목의 이름과 값을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8c44d-125">**Contextual values** list the names and values of report items that are outside of the report data regions.</span></span> <span data-ttu-id="8c44d-126">항목은 일반적으로 입력란입니다.</span><span class="sxs-lookup"><span data-stu-id="8c44d-126">The items are typically text boxes.</span></span> <span data-ttu-id="8c44d-127">예: 보고서의 제목 또는 설명과 같은 상수 값을 가진 입력란</span><span class="sxs-lookup"><span data-stu-id="8c44d-127">For example, a text box with a constant value such as the subject or description of a report.</span></span>

 <span data-ttu-id="8c44d-128">두 메시지 형식 간의 유일한 차이점은 항목 5, **경고 결과**입니다.</span><span class="sxs-lookup"><span data-stu-id="8c44d-128">The only difference between the two message types is item 5, **Alert Results**.</span></span> <span data-ttu-id="8c44d-129">데이터 경고 인스턴스 또는 데이터 경고 메시지를 만들 때 오류가 발생한 경우 **경고 결과** 에 문제를 설명하는 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c44d-129">If an error occurs when a data alert instance or data alert message is created, **Alert Results** displays an error message that describes the problem.</span></span> <span data-ttu-id="8c44d-130">모든 받는 사람에게 보낸 오류 메시지를 통해 비즈니스 의사 결정을 내리는 데 필요한 원하는 경고 결과를 사용할 수 없다는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c44d-130">The error message, sent to all recipients, let them know that the alert results that they are expecting and might rely on to make business decisions are not available.</span></span>

 

##  <a name="related-tasks"></a><a name="HowTo"></a> <span data-ttu-id="8c44d-131">관련 작업</span><span class="sxs-lookup"><span data-stu-id="8c44d-131">Related Tasks</span></span>
 <span data-ttu-id="8c44d-132">이 섹션에는 데이터 경고 메시지에 표시되는 많은 정보를 제공하는 데이터 경고 정의를 만들고 편집하는 방법을 보여 주는 절차가 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c44d-132">This section lists procedures that show you how to create and edit the data alert definitions that provide much of the information that you see in data alert messages.</span></span>

-   [<span data-ttu-id="8c44d-133">데이터 경고 디자이너에서 데이터 경고 만들기</span><span class="sxs-lookup"><span data-stu-id="8c44d-133">Create a Data Alert in Data Alert Designer</span></span>](create-a-data-alert-in-data-alert-designer.md)

-   [<span data-ttu-id="8c44d-134">경고 디자이너에서 데이터 경고 편집</span><span class="sxs-lookup"><span data-stu-id="8c44d-134">Edit a Data Alert in Alert Designer</span></span>](edit-a-data-alert-in-alert-designer.md)



## <a name="see-also"></a><span data-ttu-id="8c44d-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8c44d-135">See Also</span></span>
 <span data-ttu-id="8c44d-136">데이터 [경고 디자이너](../../2014/reporting-services/data-alert-designer.md) [Reporting Services 데이터 경고](../ssms/agent/alerts.md)</span><span class="sxs-lookup"><span data-stu-id="8c44d-136">[Data Alert Designer](../../2014/reporting-services/data-alert-designer.md) [Reporting Services Data Alerts](../ssms/agent/alerts.md)</span></span>


