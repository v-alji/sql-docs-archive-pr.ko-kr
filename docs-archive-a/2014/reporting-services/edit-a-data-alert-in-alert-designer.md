---
title: 경고 디자이너에서 데이터 경고 편집 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- editing, data alerts
- updating, data alerts
- editing, alerts
- updating, alerts
ms.assetid: dde3664d-90b5-4b12-969e-39152c86e58a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9906b33ae50d51733eaec1bf5c201c9f5b5d120e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735071"
---
# <a name="edit-a-data-alert-in-alert-designer"></a><span data-ttu-id="b1805-102">경고 디자이너에서 데이터 경고 편집</span><span class="sxs-lookup"><span data-stu-id="b1805-102">Edit a Data Alert in Alert Designer</span></span>
  <span data-ttu-id="b1805-103">데이터 경고 관리자에서 편집할 데이터 경고 정의를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b1805-103">You open the data alert definition that you want to edit from Data Alert Manager.</span></span> <span data-ttu-id="b1805-104">경고 정의를 만든 사용자만 해당 정의를 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1805-104">Only the user that created the alert definition can edit it.</span></span> <span data-ttu-id="b1805-105">데이터 경고 관리자를 여는 방법은 [데이터 경고 관리자에서 내 데이터 경고 관리](manage-my-data-alerts-in-data-alert-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b1805-105">For more information about opening Data Alert Manager, see [Manage My Data Alerts in Data Alert Manager](manage-my-data-alerts-in-data-alert-manager.md).</span></span>

 <span data-ttu-id="b1805-106">다음 그림은 데이터 경고 관리자에 있는 데이터 경고의 상황에 맞는 메뉴를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b1805-106">The following picture shows you the context menu on a data alert in Data Alert Manager.</span></span>

 <span data-ttu-id="b1805-107">![편집을 클릭하여 데이터 경고 디자이너 열기](media/rs-alertmanageriwopendesigner.gif "편집을 클릭하여 데이터 경고 디자이너 열기")</span><span class="sxs-lookup"><span data-stu-id="b1805-107">![Open Data Alert Designer by clicking Edit](media/rs-alertmanageriwopendesigner.gif "Open Data Alert Designer by clicking Edit")</span></span>

 <span data-ttu-id="b1805-108">다음 절차에는 데이터 경고 디자이너에서 편집할 경고 정의를 데이터 경고 관리자에서 열기 위한 단계가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1805-108">The following procedure includes the steps to open the alert definition for editing in Data Alert Designer from Data Alert Manager.</span></span>

### <a name="to-edit-a-data-alert-definition-in-data-alert-designer"></a><span data-ttu-id="b1805-109">데이터 경고 디자이너에서 데이터 경고 정의를 편집하려면</span><span class="sxs-lookup"><span data-stu-id="b1805-109">To edit a data alert definition in Data Alert Designer</span></span>

1.  <span data-ttu-id="b1805-110">데이터 경고 관리자에서 편집할 데이터 경고 정의를 마우스 오른쪽 단추로 클릭하고 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b1805-110">In Data Alert Manager, right-click the data alert definition that you want to edit and click **Edit**.</span></span>

     <span data-ttu-id="b1805-111">경고 정의가 데이터 경고 디자이너에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="b1805-111">The alert definition opens in Data Alert Designer.</span></span>

2.  <span data-ttu-id="b1805-112">규칙, 일정 설정 및 전자 메일 설정을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="b1805-112">Update the rules, schedule settings, and email settings.</span></span> <span data-ttu-id="b1805-113">자세한 내용은 [데이터 경고 디자이너](../../2014/reporting-services/data-alert-designer.md) 및 [데이터 경고 디자이너에서 데이터 경고 만들기](create-a-data-alert-in-data-alert-designer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b1805-113">For more information, see [Data Alert Designer](../../2014/reporting-services/data-alert-designer.md) and [Create a Data Alert in Data Alert Designer](create-a-data-alert-in-data-alert-designer.md).</span></span>

    > [!NOTE]
    >  <span data-ttu-id="b1805-114">다른 데이터 피드를 선택할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b1805-114">You cannot choose a different data feed.</span></span> <span data-ttu-id="b1805-115">다른 데이터 피드를 사용하려면 새 데이터 경고 정의를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1805-115">To use a different data feed, you must create a new data alert definition.</span></span>

3.  <span data-ttu-id="b1805-116">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b1805-116">Click **Save**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="b1805-117">보고서가 변경되고 보고서에서 생성된 데이터 피드가 변경된 경우 경고 정의가 더 이상 유효하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1805-117">If the report has changed and the data feeds generated from the report have changed the alert definition might no longer be valid.</span></span> <span data-ttu-id="b1805-118">이러한 예로는 해당 규칙에서 경고 정의가 참조하는 열이 보고서에서 삭제되었거나 데이터 형식을 변경하는 경우 또는 보고서가 삭제 또는 이동되는 경우를 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1805-118">This occurs when a column that the alert definition references in its rules is deleted from the report or changes data type or the report is deleted or moved.</span></span> <span data-ttu-id="b1805-119">유효하지 않은 경고 정의를 열 수는 있지만 정의를 작성할 때 사용한 보고서 데이터 피드의 현재 버전을 기준으로 유효한 경고 정의만 다시 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1805-119">You can open an alert definition that is not valid, but you cannot resave it until it is valid based on the current version of the report data feed that it is built upon.</span></span> <span data-ttu-id="b1805-120">보고서에서 데이터 피드를 생성하는 방법은 [보고서에서 데이터 피드 생성&#40;보고서 작성기 및 SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b1805-120">To learn more about how data feeds are generated from reports, see [Generating Data Feeds from Reports &#40;Report Builder and SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b1805-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b1805-121">See Also</span></span>
 <span data-ttu-id="b1805-122">[경고 담당자를 위한 데이터 경고 관리자](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) [Reporting Services 데이터 경고](../ssms/agent/alerts.md)</span><span class="sxs-lookup"><span data-stu-id="b1805-122">[Data Alert Manager for Alerting Administrators](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) [Reporting Services Data Alerts](../ssms/agent/alerts.md)</span></span>


