---
title: 새 링크 된 보고서 페이지 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fefb46e8-6901-4d50-a3f8-7c49ad72e7b1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 61138e51cfd9bb6e1ee124dd4aa3bc224d8aebcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653235"
---
# <a name="new-linked-report-page-report-manager"></a><span data-ttu-id="ed96c-102">새 링크된 보고서 페이지(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="ed96c-102">New Linked Report Page (Report Manager)</span></span>
  <span data-ttu-id="ed96c-103">새 링크된 보고서 페이지를 사용하여 링크된 보고서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed96c-103">Use the New Linked Report page to create a linked report.</span></span> <span data-ttu-id="ed96c-104">링크된 보고서는 고유한 설정 및 속성은 있지만 다른 보고서의 보고서 정의에 연결되어 있는 보고서입니다.</span><span class="sxs-lookup"><span data-stu-id="ed96c-104">A linked report is a report with settings and properties of its own, but links to the report definition of another report.</span></span> <span data-ttu-id="ed96c-105">링크된 보고서는 특정 그룹이나 사용자에 대해 변경할 기준 보고서가 있는 경우에 유용합니다. 매개 변수로 지정하는 지역 코드에 따라 다른 데이터를 반환하는 지역 보고서를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed96c-105">Linked reports are useful when you have a base report that you want to vary for specific groups or users; for example, a regional report that returns different data based on a regional code that you specify as a parameter.</span></span> <span data-ttu-id="ed96c-106">링크된 보고서는 일반적으로 매개 변수 있는 보고서에서 내용을 변경한 다음 각 보고서 인스턴스에 다른 매개 변수 값을 저장하면 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="ed96c-106">A linked report is typically created from a parameterized report when you want to vary and then save different parameter values with each report instance.</span></span> <span data-ttu-id="ed96c-107">그러나 액세스 가능한 모든 보고서에서 링크된 보고서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed96c-107">However, you can create a linked report from any report to which you have access.</span></span>  
  
 <span data-ttu-id="ed96c-108">링크된 보고서는 자체 이름, 설명, 위치, 매개 변수 속성, 보고서 실행 속성, 보고서 기록 속성, 사용 권한 및 구독을 포함할 수 있지만</span><span class="sxs-lookup"><span data-stu-id="ed96c-108">A linked report can have its own name, description, location, parameter properties, report execution properties, report history properties, permissions, and subscriptions.</span></span> <span data-ttu-id="ed96c-109">보고서 정의를 제공하는 기준 보고서의 데이터 원본 속성 및 레이아웃을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed96c-109">However, a linked report must use the data source properties and layout of the base report that provides the report definition.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="ed96c-110">탐색</span><span class="sxs-lookup"><span data-stu-id="ed96c-110">Navigation</span></span>  
 <span data-ttu-id="ed96c-111">사용자 인터페이스(UI)에서 이 위치를 탐색하려면 다음 절차를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="ed96c-111">Use the following procedures to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-new-linked-report-page-from-the-contents-page"></a><span data-ttu-id="ed96c-112">내용 페이지에서 새 링크된 보고서 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="ed96c-112">To open the New Linked Report page from the Contents page</span></span>  
  
1.  <span data-ttu-id="ed96c-113">보고서 관리자를 열고 링크된 보고서를 만들 보고서를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ed96c-113">Open Report Manager, and locate a report for which you want to create a linked report.</span></span>  
  
2.  <span data-ttu-id="ed96c-114">보고서 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ed96c-114">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="ed96c-115">드롭다운 메뉴에서 **링크된 보고서 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ed96c-115">In the drop-down menu, click **Create Linked Report**.</span></span>  
  
###### <a name="to-open-the-new-linked-report-page-from-the-general-properties-page-of-a-report"></a><span data-ttu-id="ed96c-116">보고서의 일반 속성 페이지에서 새 링크된 보고서 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="ed96c-116">To open the New Linked Report page from the General properties page of a report</span></span>  
  
1.  <span data-ttu-id="ed96c-117">보고서 관리자를 열고 링크된 보고서를 만들 보고서를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ed96c-117">Open Report Manager, and locate a report for which you want to create a linked report.</span></span>  
  
2.  <span data-ttu-id="ed96c-118">보고서 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ed96c-118">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="ed96c-119">드롭다운 메뉴에서 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ed96c-119">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="ed96c-120">보고서의 일반 속성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="ed96c-120">This opens the General properties page for the report.</span></span>  
  
4.  <span data-ttu-id="ed96c-121">항목 도구 모음에서 **링크된 보고서 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ed96c-121">In the item toolbar, click **Create Linked Report**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ed96c-122">옵션</span><span class="sxs-lookup"><span data-stu-id="ed96c-122">Options</span></span>  
 <span data-ttu-id="ed96c-123">**이름**</span><span class="sxs-lookup"><span data-stu-id="ed96c-123">**Name**</span></span>  
 <span data-ttu-id="ed96c-124">링크된 보고서의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ed96c-124">Specify the name of the linked report.</span></span> <span data-ttu-id="ed96c-125">이름은 하나 이상의 영숫자 문자를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed96c-125">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="ed96c-126">공백과 특정 기호도 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed96c-126">It can also include spaces and certain symbols.</span></span> <span data-ttu-id="ed96c-127">그러나 이름을 지정할 때 ; ?</span><span class="sxs-lookup"><span data-stu-id="ed96c-127">However, you must not use the characters ; ?</span></span> <span data-ttu-id="ed96c-128">: \@ & = +, $/\* \< > | "로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed96c-128">: \@ & = + , $ / \* \< > | " or / when specifying a name.</span></span>  
  
 <span data-ttu-id="ed96c-129">**설명**</span><span class="sxs-lookup"><span data-stu-id="ed96c-129">**Description**</span></span>  
 <span data-ttu-id="ed96c-130">보고서 내용에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ed96c-130">Type a description of the report contents.</span></span> <span data-ttu-id="ed96c-131">이 설명은 보고서 액세스 권한이 있는 사용자의 내용 페이지에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed96c-131">This description appears in the Contents page to users who have permission to access the report.</span></span>  
  
 <span data-ttu-id="ed96c-132">**위치**</span><span class="sxs-lookup"><span data-stu-id="ed96c-132">**Location**</span></span>  
 <span data-ttu-id="ed96c-133">보고서를 포함하는 폴더의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ed96c-133">Specify the folder path that contains the report.</span></span> <span data-ttu-id="ed96c-134">기본적으로 링크된 보고서는 기준 보고서의 형제 항목으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="ed96c-134">By default, linked reports are created as siblings to the base report.</span></span> <span data-ttu-id="ed96c-135">링크된 보고서를 다른 폴더에 넣으려면 **위치 변경** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ed96c-135">Click **Change Location** to put the linked report in a different folder.</span></span>  
  
 <span data-ttu-id="ed96c-136">**확인**</span><span class="sxs-lookup"><span data-stu-id="ed96c-136">**OK**</span></span>  
 <span data-ttu-id="ed96c-137">변경 내용을 저장하고 기준 보고서의 일반 속성 페이지로 돌아가려면 **확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ed96c-137">Click **OK** to save your changes and return to the General properties page of the base report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed96c-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ed96c-138">See Also</span></span>  
 <span data-ttu-id="ed96c-139">[링크 된 보고서 만들기](reports/create-a-linked-report.md) </span><span class="sxs-lookup"><span data-stu-id="ed96c-139">[Create a Linked Report](reports/create-a-linked-report.md) </span></span>  
 <span data-ttu-id="ed96c-140">[일반 속성 페이지, 보고서 &#40;보고서 관리자&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="ed96c-140">[General Properties Page, Reports &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span></span>  
 [<span data-ttu-id="ed96c-141">보고서 관리자 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="ed96c-141">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
