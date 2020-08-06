---
title: 기술 자료 열기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.kb.openkb.f1
ms.assetid: a5f010a5-b762-41c9-881b-bf0c192dca83
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f727a5ab75a60d29c830403892c56c87fc6d4ebf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736784"
---
# <a name="open-a-knowledge-base"></a><span data-ttu-id="3c9cb-102">기술 자료 열기</span><span class="sxs-lookup"><span data-stu-id="3c9cb-102">Open a Knowledge Base</span></span>
  <span data-ttu-id="3c9cb-103">이 항목에서는 DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] )에서 기존 기술 자료를 열어 도메인 관리, 기술 자료 검색 또는 일치 정책 추가를 수행할 준비를 갖추는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-103">This topic describes how to open an existing knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS), and prepare it for domain management, knowledge discovery, or adding a matching policy.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3c9cb-104">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="3c9cb-104">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="3c9cb-105">필수 조건</span><span class="sxs-lookup"><span data-stu-id="3c9cb-105">Prerequisites</span></span>  
 <span data-ttu-id="3c9cb-106">기술 자료를 열려면 기술 자료가 이미 생성되어 있고 게시되었거나(다른 사람이 생성한 경우) 닫혀 있어야 합니다(본인이 생성한 경우).</span><span class="sxs-lookup"><span data-stu-id="3c9cb-106">To open a knowledge base, the knowledge base must have already been created, and either published (if another person created it) or have been closed (if you created it).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3c9cb-107">보안</span><span class="sxs-lookup"><span data-stu-id="3c9cb-107">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3c9cb-108">권한</span><span class="sxs-lookup"><span data-stu-id="3c9cb-108">Permissions</span></span>  
 <span data-ttu-id="3c9cb-109">기술 자료를 열려면 DQS_MAIN 데이터베이스에 대한 dqs_kb_editor 또는 dqs_administrator 역할이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-109">You must have the dqs_kb_editor role or the dqs_administrator on the DQS_MAIN database to open a knowledge base.</span></span>  
  
##  <a name="open-a-knowledge-base"></a><a name="Open"></a><span data-ttu-id="3c9cb-110">기술 자료 열기</span><span class="sxs-lookup"><span data-stu-id="3c9cb-110">Open a knowledge base</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="3c9cb-111">[Data Quality Client 응용 프로그램을 실행](../../2014/data-quality-services/run-the-data-quality-client-application.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-111">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="3c9cb-112">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면에서 **기술 자료 열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-112">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open knowledge base**.</span></span>  
  
3.  <span data-ttu-id="3c9cb-113">테이블에서 기술 자료를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-113">Select a knowledge base in the table.</span></span> <span data-ttu-id="3c9cb-114">기술 자료의 도메인 및 일치 규칙이 페이지의 오른쪽 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-114">The domains and matching rules in the knowledge base will be displayed in the right-hand pane of the page.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3c9cb-115">테이블에서 기술 자료를 마우스 오른쪽 단추로 클릭하여 기술 자료에 대한 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-115">You can perform operations on a knowledge base by right-clicking it in the table.</span></span> <span data-ttu-id="3c9cb-116">기술 자료를 열거나, 다른 이름으로 저장하거나, 잠금을 해제하거나, 작업을 취소하거나, 이름을 바꾸거나, 속성을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-116">You can open the knowledge base, save it with another name, unlock it, discard the work, rename it, or display its properties.</span></span>  
  
4.  <span data-ttu-id="3c9cb-117">**작업 선택**에서 기술 자료에 대해 수행할 작업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-117">In **Select Activity**, select the activity that you want to perform on the knowledge base:</span></span>  
  
    -   <span data-ttu-id="3c9cb-118">**도메인 관리** 를 선택하여 기술 자료의 도메인을 수정하는 데 사용하는 화면으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-118">Select **Domain Management** to enter the screens that you use to modify the domains in the knowledge base.</span></span>  
  
    -   <span data-ttu-id="3c9cb-119">**기술 자료 검색** 을 선택하여 데이터 샘플을 분석하고 기술 자료의 도메인을 결과로 채우는 데 사용하는 마법사를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-119">Select **Knowledge Discovery** to enter the wizard that you use to analyze a data sample and populate the domains of the knowledge base with the results.</span></span>  
  
    -   <span data-ttu-id="3c9cb-120">**일치 정책** 을 선택하여 일치 정책을 만들고 기술 자료에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-120">Select **Matching Policy** to create a matching policy and add it to the knowledge base.</span></span>  
  
5.  <span data-ttu-id="3c9cb-121">**열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-121">Click **Open**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3c9cb-122">기술 자료를 마우스 오른쪽 단추로 클릭한 다음 열기를 클릭하여 기술 자료를 열 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-122">You can also open the knowledge base by right-clicking it, and then clicking Open.</span></span> <span data-ttu-id="3c9cb-123">상황에 맞는 메뉴의 다른 명령을 사용하여 기술 자료를 다른 이름으로 저장하거나, 잠금을 해제하거나, 작업을 취소하거나, 이름을 바꾸거나, 속성을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-123">Other commands in the context menu enable you to save it with another name, unlock it, discard the work, rename it, or display its properties.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3c9cb-124">기술 자료가 잠겨 있어 열 수 없는 경우 아래 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-124">If you cannot open the knowledge base because it is locked, see the section below.</span></span>  
  
## <a name="open-a-recent-knowledge-base"></a><span data-ttu-id="3c9cb-125">최신 기술 자료 열기</span><span class="sxs-lookup"><span data-stu-id="3c9cb-125">Open a Recent Knowledge Base</span></span>  
 <span data-ttu-id="3c9cb-126">가장 최근에 열어 본 5개 기술 자료가 DQS 홈 페이지의 **최근 기술 자료** 목록에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-126">The five most recently opened knowledge bases are displayed in the **Recent Knowledge Base** list in the DQS home page.</span></span> <span data-ttu-id="3c9cb-127">따라서 **기술 자료 열기** 페이지로 이동하지 않고도 최근에 작업한 기술 자료를 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-127">This enables you to open a knowledge base that you recently worked on without going through the **Open Knowledge Base** page.</span></span>  
  
-   <span data-ttu-id="3c9cb-128">잠겨 있지 않은 최근에 사용한 항목 목록에서 기술 자료를 열려면 기술 자료에 대한 오른쪽 화살표를 클릭한 다음 기술 자료를 열려는 작업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-128">To open a knowledge base in the Recent list that is not locked, click the right arrow for the knowledge base, and then select the activity that you want to open the knowledge base in.</span></span>  
  
-   <span data-ttu-id="3c9cb-129">잠겨 있는 최근에 사용한 항목 목록에서 기술 자료를 열려면 기술 자료를 클릭합니다. 그러면 괄호 안에 표시된 작업 및 페이지에서 기술 자료가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-129">To open a knowledge base in the Recent list that you locked, click the knowledge base and it will open in the activity and page indicated in parentheses.</span></span>  
  
-   <span data-ttu-id="3c9cb-130">다른 사용자가 잠근 최근에 사용한 항목 목록에서 기술 자료를 열려면 해당 사용자에게 연락해 기술 자료의 잠금을 해제하도록 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-130">To open a knowledge base in the Recent list that has been locked by someone else, contact that person and have them unlock the knowledge base.</span></span>  
  
##  <a name="follow-up-after-opening-a-knowledge-base"></a><a name="FollowUp"></a> <span data-ttu-id="3c9cb-131">후속 작업: 기술 자료를 연 후</span><span class="sxs-lookup"><span data-stu-id="3c9cb-131">Follow Up: After Opening a Knowledge Base</span></span>  
 <span data-ttu-id="3c9cb-132">기술 자료를 연 후에는 기술 자료가 기술 자료 테이블의 상태 열에 표시된 상태로 전환됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-132">After you open a knowledge base, the knowledge base is put into the state indicated in the State column of the Knowledge Base table.</span></span> <span data-ttu-id="3c9cb-133">기술 자료 검색 및 일치 정책 작업의 경우 기술 자료가 특정 마법사 페이지에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-133">For the knowledge discovery and matching policy activities, the knowledge base will be opened in a specific wizard page.</span></span> <span data-ttu-id="3c9cb-134">도메인 관리 작업의 경우 기술 자료가 도메인 관리 페이지에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-134">For the domain management activity, the knowledge base will be opened in the domain management page.</span></span> <span data-ttu-id="3c9cb-135">상태에 대한 자세한 내용은 [기술 자료 검색 수행](../../2014/data-quality-services/perform-knowledge-discovery.md), [도메인 관리](../../2014/data-quality-services/managing-a-domain.md) 또는 [일치 정책 만들기](../../2014/data-quality-services/create-a-matching-policy.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-135">For more information about the states, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
##  <a name="if-the-knowledge-base-is-locked"></a><a name="Locked"></a> <span data-ttu-id="3c9cb-136">기술 자료가 잠긴 경우</span><span class="sxs-lookup"><span data-stu-id="3c9cb-136">If the knowledge base is locked</span></span>  
 <span data-ttu-id="3c9cb-137">첫 번째 열의 자물쇠 아이콘이 기술 자료가 잠겨 있는지 여부를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-137">The lock icon in the first column shows whether the knowledge base is locked.</span></span> <span data-ttu-id="3c9cb-138">잠긴 기술 자료의 이름은 빨간색 글꼴로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-138">The name of a locked knowledge base will be in red font.</span></span> <span data-ttu-id="3c9cb-139">특정 사용자가 기술 자료 작업을 통해 수정 중인 기술 자료는 잠금으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-139">A knowledge base that is being modified by a specific user through a knowledge base activity is marked as Locked.</span></span> <span data-ttu-id="3c9cb-140">잠긴 기술 자료에서 다른 사용자가 작업을 수행할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-140">A locked knowledge base cannot be worked on by a second user.</span></span> <span data-ttu-id="3c9cb-141">기술 자료에서 작업하고 있는 사용자는 기술 자료 열기 페이지의 테이블에서 기술 자료를 마우스 오른쪽 단추로 클릭하고 **잠금 해제**를 클릭하거나 기술 자료를 게시하여 기술 자료의 잠금을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-141">The user who is working on the knowledge base can unlock it by right-clicking the knowledge base in the table on the Open Knowledge Base page, and clicking **Unlock**, or by publishing it.</span></span> <span data-ttu-id="3c9cb-142">잠긴 기술 자료에 커서를 두면 해당 기술 자료를 잠근 사용자와 잠근 이유를 나타내는 힌트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-142">When the cursor is positioned on a locked knowledge base, DQS will display a hint showing who locked the knowledge base and when they locked it.</span></span>  
  
##  <a name="state-of-a-knowledge-base"></a><a name="State"></a> <span data-ttu-id="3c9cb-143">기술 자료의 상태</span><span class="sxs-lookup"><span data-stu-id="3c9cb-143">State of a Knowledge Base</span></span>  
 <span data-ttu-id="3c9cb-144">상태 필드는 기술 자료에 대한 현재 작업 단계를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-144">The State field indicates which stage of an activity the knowledge base is at.</span></span> <span data-ttu-id="3c9cb-145">기술 자료를 열면 해당 단계에서 기술 자료가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-145">If you open the knowledge base, it will open to that stage.</span></span>  
  
-   <span data-ttu-id="3c9cb-146">**\<Empty>**: 도메인 관리 작업에서 **게시** 를 클릭 한 다음 **예-기술 자료를 게시 하 고 종료**를 클릭 하 여 기술 자료를 게시 한 경우 기술 자료에 대 한 상태 필드가 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-146">**\<Empty>**: The State field is empty for a knowledge base if the knowledge base has been published by clicking **Publish** in the Domain Management activity, and clicking **Yes - Publish the knowledge base and exit**.</span></span>  
  
-   <span data-ttu-id="3c9cb-147">**작업**중: 도메인 관리 작업에서 **게시** 를 클릭 하 고 **기술 자료에 대 한 작업을 저장 하지 않고 종료**를 클릭 하 여 기술 자료에 대 한 작업을 저장 했습니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-147">**In Work**: Work on the knowledge base has been saved by clicking **Publish** in the Domain Management activity, and clicking **No - Save the work on the knowledge base and exit**.</span></span>  
  
-   <span data-ttu-id="3c9cb-148">**도메인 관리**: 기술 자료의 도메인에 대한 데이터가 입력되었지만 기술 자료가 게시되지 않았고 작업 내용이 도메인 관리 작업에 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-148">**Domain Management**: Data has been entered for a domain in the knowledge base, but the knowledge base has not been published and the work remains in the Domain Management activity.</span></span> <span data-ttu-id="3c9cb-149">기술 자료 검색 작업을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-149">The Knowledge Discovery activity is not available.</span></span> <span data-ttu-id="3c9cb-150">이 현상은 **도메인 관리** 화면에서 **닫기** 를 클릭할 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-150">This occurs when you click **Close** in the **Domain Management** screen.</span></span>  
  
-   <span data-ttu-id="3c9cb-151">**검색 - 매핑**: 기술 자료가 **기술 자료 관리: 매핑** 페이지에서 닫혔습니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-151">**Discovery - Mapping**: The knowledge base was closed on the **Knowledge Base Management: Mapping** page.</span></span> <span data-ttu-id="3c9cb-152">기술 자료가 잠겨 있으며 도메인 관리 및 일치 작업을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-152">The knowledge base is locked, and the Domain Management and Matching activities are not available.</span></span>  
  
-   <span data-ttu-id="3c9cb-153">**검색 - 검색**: 기술 자료가 **기술 자료 관리: 분석** 페이지에서 닫혔습니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-153">**Discovery - Discover**: The knowledge base was closed on the **Knowledge Base Management: Analyze** page.</span></span> <span data-ttu-id="3c9cb-154">기술 자료가 잠겨 있으며 도메인 관리 작업을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-154">The knowledge base is locked, and The Domain Management activity is not available.</span></span>  
  
-   <span data-ttu-id="3c9cb-155">**검색-값 관리**: 기술 자료가 **기술 자료 관리: 도메인 용어 관리** 페이지에서 닫혔습니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-155">**Discovery - Value Management**: The knowledge base was closed on the **Knowledge Base Management: Manage Domain Terms** page.</span></span> <span data-ttu-id="3c9cb-156">기술 자료가 잠겨 있으며 도메인 관리 작업을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-156">The knowledge base is locked, and the Domain Management activity is not available.</span></span>  
  
-   <span data-ttu-id="3c9cb-157">**일치 정책-일치 정책**: 기술 자료가 **일치 정책-일치 정책** 페이지에서 닫혔습니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-157">**Matching Policy - Matching Policy**: The knowledge base was closed on the **Matching Policy - Matching Policy** page.</span></span> <span data-ttu-id="3c9cb-158">기술 자료가 잠겨 있으며 기술 자료 검색 및 도메인 관리 작업을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-158">The knowledge base is locked, and the Knowledge Discovery and Domain Management activities are not available.</span></span>  
  
-   <span data-ttu-id="3c9cb-159">**일치 정책-일치 결과**: 기술 자료가 **일치 정책-일치 결과** 페이지에서 닫혔습니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-159">**Matching Policy - Matching Results**: The knowledge base was closed on the **Matching Policy - Matching Results** page.</span></span> <span data-ttu-id="3c9cb-160">기술 자료가 잠겨 있으며 기술 자료 검색 및 도메인 관리 작업을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3c9cb-160">The knowledge base is locked, and the Knowledge Discovery and Domain Management activities are not available.</span></span>  
  
  
