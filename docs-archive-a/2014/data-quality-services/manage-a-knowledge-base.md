---
title: 기술 자료 관리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 27f306f4-d67c-47f5-b35c-4260cc5d36e3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cc5fdd87ddb3ea687db10a29d7001564fd8ff107
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660153"
---
# <a name="manage-a-knowledge-base"></a><span data-ttu-id="6c8b7-102">기술 자료 관리</span><span class="sxs-lookup"><span data-stu-id="6c8b7-102">Manage a Knowledge Base</span></span>
  <span data-ttu-id="6c8b7-103">이 항목에서는 DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] )의 기술 자료에 대해 관리 기능을 수행하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-103">This topic describes how to perform management functions on a knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="6c8b7-104">기술 자료에 대해 삭제, 잠금 해제, 작업 취소, 이름 바꾸기 및 속성 표시 기능을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-104">You can delete a knowledge base, unlock it, discard your work on it, rename it, and display its properties.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6c8b7-105">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="6c8b7-105">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="6c8b7-106">필수 조건</span><span class="sxs-lookup"><span data-stu-id="6c8b7-106">Prerequisites</span></span>  
 <span data-ttu-id="6c8b7-107">기술 자료를 관리하려면 기술 자료가 이미 생성되어 있고 게시되었거나(다른 사람이 생성한 경우) 닫혀 있어야 합니다(본인이 생성한 경우).</span><span class="sxs-lookup"><span data-stu-id="6c8b7-107">To manage a knowledge base, the knowledge base must have already been created, and either published (if another person created it) or have been closed (if you created it).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6c8b7-108">보안</span><span class="sxs-lookup"><span data-stu-id="6c8b7-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6c8b7-109">권한</span><span class="sxs-lookup"><span data-stu-id="6c8b7-109">Permissions</span></span>  
 <span data-ttu-id="6c8b7-110">기술 자료를 열려면 DQS_MAIN 데이터베이스에 대한 dqs_kb_editor 또는 dqs_administrator 역할이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-110">You must have the dqs_kb_editor role or the dqs_administrator on the DQS_MAIN database to open a knowledge base.</span></span>  
  
##  <a name="manage-a-knowledge-base"></a><a name="Manage"></a><span data-ttu-id="6c8b7-111">기술 자료 관리</span><span class="sxs-lookup"><span data-stu-id="6c8b7-111">Manage a Knowledge Base</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="6c8b7-112">[Data Quality Client 응용 프로그램을 실행](../../2014/data-quality-services/run-the-data-quality-client-application.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-112">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="6c8b7-113">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면에서 **기술 자료 열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-113">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open knowledge base**.</span></span>  
  
3.  <span data-ttu-id="6c8b7-114">기술 자료 테이블에서 특정 기술 자료를 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-114">Right-click a knowledge base in the knowledge base table.</span></span>  
  
4.  <span data-ttu-id="6c8b7-115">상황에 맞는 메뉴에서 다음과 같은 작업을 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-115">In the context menu, you can do the following:</span></span>  
  
    1.  <span data-ttu-id="6c8b7-116">**열기**: **작업 선택** 창에서 선택한 작업의 기술 자료를 열려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-116">**Open**: Click to open the knowledge base in the activity selected in the **Select Activity** pane.</span></span>  
  
    2.  <span data-ttu-id="6c8b7-117">**잠금 해제**: 도메인 관리, 기술 자료 검색 및 일치 정책 작업 단계 중 하나에서 기술 자료로 작업 중이었다가 닫은 사용자만 기술 자료의 잠금을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-117">**Unlock**: You can unlock the knowledge base if you are the user who was working on the knowledge base in one of the steps of domain management, knowledge discovery, and the matching policy activity, and closed it.</span></span> <span data-ttu-id="6c8b7-118">기술 자료를 언로드할 경우 다른 사람이 열어서 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-118">If you unload the knowledge base, another person will be able to open it and work on it.</span></span> <span data-ttu-id="6c8b7-119">기술 자료가 작업 상태가 아닌 경우 이 명령을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-119">This command is not available if the knowledge base is not in a state of an activity.</span></span> <span data-ttu-id="6c8b7-120">자세한 내용은 [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-120">For more information, see [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).</span></span>  
  
    3.  <span data-ttu-id="6c8b7-121">**작업 삭제**: 테이블의 상태 필드 항목에 기술 자료가 작업 중인 상태로 표시되는 경우 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-121">**Discard work**: Click when the knowledge base is in a state of being worked on, as shown with an entry in the State field in the table.</span></span> <span data-ttu-id="6c8b7-122">기술 자료가 작업 상태가 아닌 경우, 기술 자료가 잠긴 경우에는 이 명령을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-122">This command is not available if the knowledge base is not in a state of an activity, and it is not available if the knowledge base is locked.</span></span> <span data-ttu-id="6c8b7-123">자세한 내용은 [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-123">For more information, see [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).</span></span>  
  
    4.  <span data-ttu-id="6c8b7-124">**이름 바꾸기**: 마우스 오른쪽 단추로 클릭한 기술 자료에서 테이블의 기술 자료 필드를 편집 가능한 상태로 만들려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-124">**Rename**: Click to make the Knowledge Base field of the table editable for the knowledge base that you right-clicked on.</span></span> <span data-ttu-id="6c8b7-125">이름을 변경한 다음 해당 기술 자료를 클릭하고 필드의 다른 기술 자료를 클릭하여 이름 변경을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-125">Change the name, and then click on that knowledge base and another one in the field to accept the name change.</span></span>  
  
    5.  <span data-ttu-id="6c8b7-126">**삭제**: [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]의 DQS_MAIN 데이터베이스에서 기술 자료를 제거하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-126">**Delete**: Click to remove the knowledge base from the DQS_MAIN database on [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span>  
  
    6.  <span data-ttu-id="6c8b7-127">**속성**: 읽기 전용 화면에서 데이터베이스의 속성을 표시하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-127">**Properties**: Click to display properties for the database in a read-only display.</span></span>  
  
        1.  <span data-ttu-id="6c8b7-128">**원본 기술 자료**: 이 데이터베이스가 기반으로 하는 기술 자료입니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-128">**Source Knowledge Base**: the knowledge base that this database was based on.</span></span> <span data-ttu-id="6c8b7-129">이것은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-129">This is optional.</span></span>  
  
        2.  <span data-ttu-id="6c8b7-130">**상태**: 마지막으로 닫힌 시간을 기준으로 기술 자료가 **작업 중** 이고 특정 기술 자료 관리 작업 상태인지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-130">**State**: Indicates if the knowledge base is **In Work** and if it is in a specific knowledge management activity, as determined when it was last closed.</span></span> <span data-ttu-id="6c8b7-131">상태는 기술 자료가 기술 자료 관리 세션에서 열렸지만 특정 작업 상태가 아닌 **작업 중**상태이거나 기술 자료가 기술 자료 관리 세션에서 열렸고 특정 작업 상태인 **작업 중** 상태에 해당 기술 자료 관리 작업이 함께 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-131">The state can be **In Work**, in which the knowledge base is opened in a knowledge management session, but not in a specific activity, or **In Work** plus a knowledge management activity, in which the knowledge base is opened in a knowledge management session, and in a specific activity.</span></span>  
  
        3.  <span data-ttu-id="6c8b7-132">**잠금 여부**: 기술 자료가 잠겨 있으면 **True** 이고 그렇지 않으면 **False** 입니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-132">**Is Locked**: **True** if the knowledge base was locked, **False** if not</span></span>  
  
        4.  <span data-ttu-id="6c8b7-133">**게시되지 않은 내용 포함**: 기술 자료에 게시를 통해 저장되지 않은 콘텐츠가 포함되어 있으면 True이고 그렇지 않으면 False입니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-133">**Contains unpublished content**: True if the knowledge base contains content that has not been saved by publishing, False if not</span></span>  
  
        5.  <span data-ttu-id="6c8b7-134">**잠근 사람**: 기술 자료를 닫은 후 잠근 사용자의 이름</span><span class="sxs-lookup"><span data-stu-id="6c8b7-134">**Locked By**: the name of the user who closed the knowledge base, locking it</span></span>  
  
        6.  <span data-ttu-id="6c8b7-135">**잠근 날짜**: 잠긴 날짜</span><span class="sxs-lookup"><span data-stu-id="6c8b7-135">**Locked Date**: date when locked</span></span>  
  
        7.  <span data-ttu-id="6c8b7-136">**만든 사람**: 자신이 속한 네트워크를 사용하여 기술 자료를 만든 사용자의 이름</span><span class="sxs-lookup"><span data-stu-id="6c8b7-136">**Created By**: the name of the user who created the knowledge base, with the network that he or she belongs to</span></span>  
  
        8.  <span data-ttu-id="6c8b7-137">**만든 날짜**: 생성된 날짜</span><span class="sxs-lookup"><span data-stu-id="6c8b7-137">**Created Date**: date when created</span></span>  
  
##  <a name="follow-up-after-managing-a-knowledge-base"></a><a name="FollowUp"></a><span data-ttu-id="6c8b7-138">후속 작업: 기술 자료를 관리 한 후</span><span class="sxs-lookup"><span data-stu-id="6c8b7-138">Follow Up: After Managing a Knowledge Base</span></span>  
 <span data-ttu-id="6c8b7-139">기술 자료 관리 후 다음 단계는 기술 자료에 대해 수행한 작업에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-139">After you manage a knowledge base, your next step depends upon the action you took on the knowledge base:</span></span>  
  
-   <span data-ttu-id="6c8b7-140">기술 자료를 연 경우 선택한 작업이 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-140">If you opened the knowledge base, you will continue in the activity that you selected.</span></span>  
  
-   <span data-ttu-id="6c8b7-141">기술 자료의 잠금을 해제한 경우 다른 사람이 지정된 상태에서 열고 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-141">If you unlocked it, it will be available for another person to open and work on, in the state indicated.</span></span>  
  
-   <span data-ttu-id="6c8b7-142">기술 자료에 대한 작업을 취소한 경우 마지막으로 게시된 상태의 기술 자료를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-142">If you discarded the work on it, the knowledge base will be available in its last published state.</span></span>  
  
-   <span data-ttu-id="6c8b7-143">기술 자료의 이름을 바꾼 경우 이름이 바뀐 기술 자료를 열어 작업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-143">If you renamed it, you will have to open the renamed knowledge base to work on it.</span></span>  
  
-   <span data-ttu-id="6c8b7-144">기술 자료를 삭제한 경우 작업할 다른 기술 자료를 선택하거나 새 기술 자료를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-144">If you delete it, you will have to select another knowledge base to work on, or create a new one.</span></span>  
  
  
