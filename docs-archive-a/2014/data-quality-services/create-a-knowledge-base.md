---
title: 기술 자료 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.kb.selectkb.f1
- sql12.dqs.kb.newkb.f1
ms.assetid: 2733a284-975f-4650-abcc-cc2aad074cab
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 281fa663362cc4462cd4e32839c1eaf6908394e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647263"
---
# <a name="create-a-knowledge-base"></a><span data-ttu-id="4db7a-102">기술 자료 만들기</span><span class="sxs-lookup"><span data-stu-id="4db7a-102">Create a Knowledge Base</span></span>
  <span data-ttu-id="4db7a-103">이 항목에서는 DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] )에서 기술 자료를 만들고 도메인 관리, 기술 자료 검색 또는 일치 정책 추가를 수행할 준비를 갖추는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4db7a-103">This topic describes how to create a knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS), and prepare it for domain management, knowledge discovery, or adding a matching policy.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4db7a-104">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="4db7a-104">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="4db7a-105">필수 조건</span><span class="sxs-lookup"><span data-stu-id="4db7a-105">Prerequisites</span></span>  
 <span data-ttu-id="4db7a-106">기술 자료를 만들려면 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 및 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4db7a-106">To create a knowledge base, you must have installed [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] and [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4db7a-107">보안</span><span class="sxs-lookup"><span data-stu-id="4db7a-107">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4db7a-108">권한</span><span class="sxs-lookup"><span data-stu-id="4db7a-108">Permissions</span></span>  
 <span data-ttu-id="4db7a-109">기술 자료를 만들려면 DQS_MAIN 데이터베이스의 dqs_kb_editor 또는 dqs_administrator 역할이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4db7a-109">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to create a knowledge base.</span></span>  
  
##  <a name="create-a-knowledge-base"></a><a name="Createaknowledgebase"></a><span data-ttu-id="4db7a-110">기술 자료 만들기</span><span class="sxs-lookup"><span data-stu-id="4db7a-110">Create a knowledge base</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="4db7a-111">[Data Quality Client 응용 프로그램을 실행](../../2014/data-quality-services/run-the-data-quality-client-application.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="4db7a-111">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="4db7a-112">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면에서 **새 기술 자료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4db7a-112">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **New knowledge base**.</span></span>  
  
3.  <span data-ttu-id="4db7a-113">새 기술 자료의 이름과 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4db7a-113">Enter a name and description for the new knowledge base.</span></span>  
  
4.  <span data-ttu-id="4db7a-114">**기술 자료 만들기**에서 기술 자료의 기반으로 사용할 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4db7a-114">In **Create knowledge base from**, select what to base the knowledge base on:</span></span>  
  
    -   <span data-ttu-id="4db7a-115">기존 기술 자료나 데이터 파일을 기반으로 새 기술 자료를 만들지 않으려면 **없음** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4db7a-115">Select **None** if you do not want to base the new knowledge base on an existing knowledge base or data file.</span></span>  
  
    -   <span data-ttu-id="4db7a-116">이미 **에서 만든 기술 자료나 기본 기술 자료를 기반으로 새 기술 자료를 만들려면** 기존 기술 자료 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4db7a-116">Select **Existing Knowledge Base** to base the new knowledge base on a knowledge base that has already been created on [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], or on the default knowledge base.</span></span> <span data-ttu-id="4db7a-117">**기술 자료 선택** 드롭다운 목록에서 기술 자료를 선택하거나 **찾아보기** 를 클릭하여 **기술 자료 선택** 대화 상자를 표시하고 새 기술 자료의 기반으로 사용할 기존 기술 자료를 선택한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4db7a-117">Select the knowledge base from the **Select Knowledge Base** drop-down list, or click **Browse** to display the **Select a Knowledge Base** dialog box, select an existing knowledge base to base the new knowledge base on, and then click **OK**.</span></span> <span data-ttu-id="4db7a-118">표에서 기술 자료를 선택하면 기술 자료의 도메인과 일치 규칙이 대화 상자 오른쪽 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4db7a-118">When you select a knowledge base from the tablet, the domains and matching rules in the knowledge base will be displayed in the right-hand pane of the dialog box.</span></span> <span data-ttu-id="4db7a-119">즉시 사용 가능한 공통 도메인 및 미국 회사, 주소 및 관계자 관련 기술 자료가 포함된 기본 기술 자료인 **DQS 데이터** 기술 자료를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4db7a-119">You can also select the **DQS Data** knowledge base, which is the default knowledge base that contains common out-of-the-box domains and knowledge related to U.S. company, address, and party data.</span></span>  
  
    -   <span data-ttu-id="4db7a-120">**의 DQS 파일을 새 기술 자료의 기반으로 사용하려면** DQS 파일에서 가져오기 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4db7a-120">Select **Import from DQS File** to base the new knowledge base on a DQS file on [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span> <span data-ttu-id="4db7a-121">**찾아보기**를 클릭하고 확장명이 .dqs인 DQS 데이터 파일을 선택한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4db7a-121">Click **Browse**, select a DQS data file with an extension of .dqs, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="4db7a-122">**작업 선택**에서 새 기술 자료에 대해 수행할 작업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4db7a-122">In **Select Activity**, select the activity that you want to perform on the new knowledge base:</span></span>  
  
    -   <span data-ttu-id="4db7a-123">기술 자료를 만들고 기술 자료의 도메인을 수정하는 데 사용하는 화면으로 이동하려면 **도메인 관리** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4db7a-123">Select **Domain Management** to create the knowledge base and enter the screens that you use to modify the domains in the knowledge base.</span></span>  
  
    -   <span data-ttu-id="4db7a-124">기술 자료를 만들고, 데이터 샘플을 분석하고 기술 자료의 도메인에 결과를 채우는 데 사용하는 마법사를 시작하려면 **기술 자료 검색** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4db7a-124">Select **Knowledge Discovery** to create the knowledge base and enter the wizard that you use to analyze a data sample and populate the domains of the knowledge base with the results.</span></span>  
  
    -   <span data-ttu-id="4db7a-125">**일치 정책** 을 선택하여 일치 정책을 만들고 기술 자료에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4db7a-125">Select **Matching Policy** to create a matching policy and add it to the knowledge base.</span></span>  
  
6.  <span data-ttu-id="4db7a-126">**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4db7a-126">Click **Create**.</span></span>  
  
##  <a name="follow-up-after-creating-a-knowledge-base"></a><a name="FollowUp"></a> <span data-ttu-id="4db7a-127">후속 작업: 기술 자료를 만든 후</span><span class="sxs-lookup"><span data-stu-id="4db7a-127">Follow Up: After Creating a Knowledge Base</span></span>  
 <span data-ttu-id="4db7a-128">기술 자료를 만든 후에는 기술 자료 검색을 수행하는 데 사용할 수 있는 마법사, 일치 정책을 만드는 데 사용하는 마법사 또는 도메인 관리를 수행할 수 있는 페이지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="4db7a-128">After you create a knowledge base, you are presented with a wizard that you can use to perform knowledge discovery, a wizard to create a matching policy, or pages to perform domain management.</span></span> <span data-ttu-id="4db7a-129">기술 자료 검색, 도메인 관리 또는 일치 정책에 대한 자세한 내용은 [기술 자료 검색 수행](../../2014/data-quality-services/perform-knowledge-discovery.md), [도메인 관리](../../2014/data-quality-services/managing-a-domain.md) 또는 [일치 정책 만들기](../../2014/data-quality-services/create-a-matching-policy.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4db7a-129">For more information about the knowledge discovery, domain management, or matching policy, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
  
