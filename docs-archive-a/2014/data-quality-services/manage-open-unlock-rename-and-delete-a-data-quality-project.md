---
title: 데이터 품질 프로젝트 관리 (열기, 잠금 해제, 이름 바꾸기 및 삭제) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dqproject.opendqproject.f1
helpviewer_keywords:
- data quality project,delete
- data quality project,rename
- data quality project,unlock
- data quality project,open
ms.assetid: de8a2b04-4673-4beb-b4cf-96a28cdf3a93
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 216c95937676954c509890b879abdee8f55b778c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660140"
---
# <a name="manage-open-unlock-rename-and-delete-a-data-quality-project"></a><span data-ttu-id="65b85-102">데이터 품질 프로젝트 관리(열기, 잠금 해제, 이름 바꾸기 및 삭제)</span><span class="sxs-lookup"><span data-stu-id="65b85-102">Manage (Open, Unlock, Rename, and Delete) a Data Quality Project</span></span>
  <span data-ttu-id="65b85-103">이 항목에서는 데이터 품질 프로젝트 열기, 잠금 해제, 이름 바꾸기, 삭제 등 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 를 사용하여 데이터 품질 프로젝트를 관리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-103">This topic describes how to manage a data quality project by using [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] such as open, unlock, rename, and delete a data quality project.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="65b85-104">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="65b85-104">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="65b85-105">제한 사항</span><span class="sxs-lookup"><span data-stu-id="65b85-105">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="65b85-106">다른 사용자가 만든 잠긴 프로젝트는 열 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-106">You cannot open a locked project that is created by another user.</span></span>  
  
-   <span data-ttu-id="65b85-107">다른 사용자가 만든 데이터 품질 프로젝트는 잠금을 해제하거나 이름을 바꾸거나 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-107">You cannot unlock, rename, or delete a data quality project that is created by another user.</span></span>  
  
-   <span data-ttu-id="65b85-108">잠긴 데이터 품질 프로젝트는 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-108">You cannot delete a locked data quality project.</span></span> <span data-ttu-id="65b85-109">삭제하려면 먼저 잠금을 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-109">You must first unlock it to delete.</span></span>  
  
-   <span data-ttu-id="65b85-110">자신이 만든 데이터 품질 프로젝트만 잠금을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-110">You can only unlock a data quality project that is created by you.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="65b85-111">필수 조건</span><span class="sxs-lookup"><span data-stu-id="65b85-111">Prerequisites</span></span>  
 <span data-ttu-id="65b85-112">관리할 데이터 품질 프로젝트가 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-112">You must have at least one data quality project to manage.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="65b85-113">보안</span><span class="sxs-lookup"><span data-stu-id="65b85-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="65b85-114">권한</span><span class="sxs-lookup"><span data-stu-id="65b85-114">Permissions</span></span>  
 <span data-ttu-id="65b85-115">데이터 품질 프로젝트를 관리하려면 DQS_MAIN 데이터베이스에 대한 dqs_kb_editor 또는 dqs_kb_operator 역할이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-115">You must have the dqs_kb_editor or dqs_kb_operator role on the DQS_MAIN database to manage a data quality project.</span></span>  
  
##  <a name="open-a-data-quality-project"></a><a name="Open"></a> <span data-ttu-id="65b85-116">데이터 품질 프로젝트 열기</span><span class="sxs-lookup"><span data-stu-id="65b85-116">Open a Data Quality Project</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="65b85-117">[Data Quality Client 응용 프로그램을 실행](../../2014/data-quality-services/run-the-data-quality-client-application.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-117">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="65b85-118">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면에서 **데이터 품질 프로젝트 열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-118">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open data quality project**.</span></span> <span data-ttu-id="65b85-119">**프로젝트 열기** 화면이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-119">The **Open project** screen appears.</span></span>  
  
     <span data-ttu-id="65b85-120">또는 **최근 데이터 품질 프로젝트** 영역 아래에 나열된 데이터 품질 프로젝트를 클릭하여 바로 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-120">Alternately, you can directly open a data quality project listed under **Recent data quality project** area by clicking it.</span></span>  
  
3.  <span data-ttu-id="65b85-121">**프로젝트 열기** 화면에서 열려는 데이터 품질 프로젝트를 클릭하여 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-121">In the **Open project** screen, click to select the data quality project that you want to open, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="65b85-122">데이터 품질 프로젝트가 마지막으로 닫힌 작업 상태에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-122">The data quality project opens at the same state of the activity where it was last closed.</span></span> <span data-ttu-id="65b85-123">데이터 품질 프로젝트의 상태는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-123">A data quality project has the following states:</span></span>  
  
    -   <span data-ttu-id="65b85-124">**정리** 작업의 경우 데이터 품질 프로젝트의 상태는 **정리 중-매핑**, **정리 중-정리**, **정리-결과 관리 및 보기**, **정리-내보내기**중에서 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-124">For the **Cleansing** activity, a data quality project can have the following states: **Cleansing - Map**, **Cleansing - Cleanse**, **Cleansing - Manage and View Results**, and **Cleansing - Export**.</span></span>  
  
    -   <span data-ttu-id="65b85-125">**일치** 작업의 경우 데이터 품질 프로젝트의 상태는 **일치-매핑**, **일치-** 일치, 일치 **-Survivorship**및 **일치-내보내기**중에서 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-125">For the **Matching** activity, a data quality project can have the following states: **Matching - Map**, **Matching - Matching**, **Matching - Survivorship**, and **Matching - Export**.</span></span>  
  
##  <a name="unlock-a-data-quality-project"></a><a name="Unlock"></a> <span data-ttu-id="65b85-126">데이터 품질 프로젝트 잠금 해제</span><span class="sxs-lookup"><span data-stu-id="65b85-126">Unlock a Data Quality Project</span></span>  
 <span data-ttu-id="65b85-127">데이터 품질 프로젝트를 만드는 경우 다른 사용자가 사용하거나 수정하지 못하도록 프로젝트가 잠긴 상태로 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-127">When you create a data quality project, it is in a locked state to prevent usage or modification by other users.</span></span> <span data-ttu-id="65b85-128">다른 사용자가 데이터 품질 프로젝트에서 작업할 수 있도록 하려면 작업을 완료한 후 데이터 품질 프로젝트의 잠금을 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-128">You must unlock the data quality project after you have completed your work if you want other users to work on your data quality project.</span></span> <span data-ttu-id="65b85-129">잠긴 프로젝트에는 자물쇠 기호가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-129">A lock symbol is displayed for projects that are locked.</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="65b85-130">[Data Quality Client 응용 프로그램을 실행](../../2014/data-quality-services/run-the-data-quality-client-application.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-130">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="65b85-131">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면에서 **데이터 품질 프로젝트 열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-131">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open data quality project**.</span></span> <span data-ttu-id="65b85-132">**프로젝트 열기** 화면이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-132">The **Open project** screen appears.</span></span>  
  
3.  <span data-ttu-id="65b85-133">**프로젝트 열기** 화면에서 자신이 만든 잠긴 데이터 품질 프로젝트를 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **잠금 해제** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-133">In the **Open project** screen, right-click a locked data quality project that is created by you, and then click **Unlock** in the shortcut menu.</span></span> <span data-ttu-id="65b85-134">프로젝트에 잠금이 해제되었음을 나타내는 녹색 확인 표시가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-134">A green check mark is displayed for the project indicating that it is unlocked.</span></span>  
  
##  <a name="rename-a-data-quality-project"></a><a name="Rename"></a> <span data-ttu-id="65b85-135">데이터 품질 프로젝트 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="65b85-135">Rename a Data Quality Project</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="65b85-136">[Data Quality Client 응용 프로그램을 실행](../../2014/data-quality-services/run-the-data-quality-client-application.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-136">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="65b85-137">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면에서 **데이터 품질 프로젝트 열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-137">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open data quality project**.</span></span> <span data-ttu-id="65b85-138">**프로젝트 열기** 화면이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-138">The **Open project** screen appears.</span></span>  
  
3.  <span data-ttu-id="65b85-139">**프로젝트 열기** 화면에서 자신이 만든 데이터 품질 프로젝트를 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **이름 바꾸기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-139">In the **Open project** screen, right-click a data quality project that is created by you, and then click **Rename** in the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="65b85-140">데이터 품질 프로젝트 이름이 **이름** 열에서 편집할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-140">The data quality project name becomes editable in the **Name** column.</span></span> <span data-ttu-id="65b85-141">새 이름을 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-141">Type a new name, and then press Enter.</span></span>  
  
##  <a name="delete-a-data-quality-project"></a><a name="Delete"></a> <span data-ttu-id="65b85-142">데이터 품질 프로젝트 삭제</span><span class="sxs-lookup"><span data-stu-id="65b85-142">Delete a Data Quality Project</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="65b85-143">[Data Quality Client 응용 프로그램을 실행](../../2014/data-quality-services/run-the-data-quality-client-application.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-143">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="65b85-144">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면에서 **데이터 품질 프로젝트 열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-144">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open data quality project**.</span></span> <span data-ttu-id="65b85-145">**프로젝트 열기** 화면이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-145">The **Open project** screen appears.</span></span>  
  
3.  <span data-ttu-id="65b85-146">**프로젝트 열기** 화면에서 자신이 만든 잠겨 있지 않은 데이터 품질 프로젝트를 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **삭제** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-146">In the **Open project** screen, right-click an unlocked data quality project that is created by you, and then click **Delete** in the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="65b85-147">확인 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-147">A confirmation message appears.</span></span> <span data-ttu-id="65b85-148">**예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65b85-148">Click **Yes**.</span></span>  
  
  
