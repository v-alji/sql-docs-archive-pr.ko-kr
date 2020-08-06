---
title: '작업 6: 정리 공급자 목록 프로젝트에서 값 가져오기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: fec0deef-a729-4ff1-b709-72d2b3f407ac
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b674cfb42ddf31c3b903a465d1be1b04e9a355ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647380"
---
# <a name="task-6-importing-values-from-the-cleanse-supplier-list-project"></a><span data-ttu-id="e3f54-102">태스크 6: Cleanse Supplier List 프로젝트에서 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="e3f54-102">Task 6: Importing Values from the Cleanse Supplier List Project</span></span>
  <span data-ttu-id="e3f54-103">이 작업에서는 정리 프로세스 중에 수집된 데이터 품질 기술 자료를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e3f54-103">In this task, you import the data quality knowledge gathered during the cleansing process.</span></span> <span data-ttu-id="e3f54-104">자세한 내용은 [정리 프로젝트 값을 도메인으로 가져오기](https://msdn.microsoft.com/library/hh479581.aspx) 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e3f54-104">See [Importing Cleansing Project Values into a Domain](https://msdn.microsoft.com/library/hh479581.aspx) topic for more details.</span></span> <span data-ttu-id="e3f54-105">또한 업데이트된 **Suppliers** 기술 자료를 게시하기 전에 기술 자료를 DQS로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e3f54-105">You also export the knowledge base into a DQS file before publishing the updated **Suppliers** knowledge base.</span></span>  
  
1.  <span data-ttu-id="e3f54-106">**DQS 클라이언트**의 기본 페이지에서 **최근 기술 자료** 아래에 있는 **Suppliers** 옆에서 **오른쪽 화살표** 를 클릭하고 **도메인 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f54-106">In the main page of **DQS Client**, click **right-arrow** next to **Suppliers** under **Recent Knowledge Bases** and click **Domain Management**.</span></span>  
  
2.  <span data-ttu-id="e3f54-107">도메인 목록에서 **Contact Email** 을 클릭하고 오른쪽 창에서 **도메인 값** 탭으로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f54-107">Click **Contact Email** in the list of domains, and switch to the **Domain Values** tab in the right pane.</span></span>  
  
3.  <span data-ttu-id="e3f54-108">도구 모음에서 **값 가져오기** 아이콘 옆의 **아래쪽 화살표** 를 클릭하고 **프로젝트 값 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f54-108">Click **down arrow** next to the **Import Values** icon on the toolbar and click **Import Project Values**.</span></span>  
  
     <span data-ttu-id="e3f54-109">![프로젝트 값 가져오기 도구 모음 단추](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-01.jpg "프로젝트 값 가져오기 도구 모음 단추")</span><span class="sxs-lookup"><span data-stu-id="e3f54-109">![Import Project Values Toolbar Button](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-01.jpg "Import Project Values Toolbar Button")</span></span>  
  
4.  <span data-ttu-id="e3f54-110">**프로젝트 값 가져오기** 대화 상자에서 **Cleanse Supplier List** 프로젝트를 선택하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f54-110">In the **Import Project Values** dialog box, select the **Cleanse Supplier List** project, and click **OK**.</span></span>  
  
5.  <span data-ttu-id="e3f54-111">모든 전자 메일은 대화형 정리 중 수행한 두 가지 수정 사항을 거쳐서 가져오기가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3f54-111">Notice that all the emails are imported along with the two corrections you did during interactive cleansing.</span></span> <span data-ttu-id="e3f54-112">두 가지 수정 사항을 보려면 화면을 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f54-112">Scroll to see the two corrections.</span></span>  
  
    |<span data-ttu-id="e3f54-113">값</span><span class="sxs-lookup"><span data-stu-id="e3f54-113">Value</span></span>|<span data-ttu-id="e3f54-114">다음으로 수정</span><span class="sxs-lookup"><span data-stu-id="e3f54-114">Correct To</span></span>|  
    |-----------|----------------|  
    |bobby0@adventure-work.com|bobby0@adventure-works.com|  
    |tad0@adventure-work.com|tad0@adventure-works.com|  
  
6.  <span data-ttu-id="e3f54-115">**Country** 도메인에 대 한 프로젝트 값 가져오기의 이전 단계를 반복 하 고, 미국의 **상태** 를 **대한민국** (')로 수정 하기 위해 새 항목이 추가 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f54-115">Repeat the previous step of importing project values for the **Country** domain and notice that a new entry is added for correcting **United State** to **United States** (with 's').</span></span>  
  
    |<span data-ttu-id="e3f54-116">값</span><span class="sxs-lookup"><span data-stu-id="e3f54-116">Value</span></span>|<span data-ttu-id="e3f54-117">다음으로 수정</span><span class="sxs-lookup"><span data-stu-id="e3f54-117">Correct To</span></span>|  
    |-----------|----------------|  
    |<span data-ttu-id="e3f54-118">United State</span><span class="sxs-lookup"><span data-stu-id="e3f54-118">United State</span></span>|<span data-ttu-id="e3f54-119">미국</span><span class="sxs-lookup"><span data-stu-id="e3f54-119">United States</span></span>|  
  
7.  <span data-ttu-id="e3f54-120">이전 도메인 값을 보려면 **새 항목만 표시** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f54-120">To see the old domain values, clear **Show Only New** checkbox.</span></span>  
  
8.  <span data-ttu-id="e3f54-121">**Supplier Name** 도메인에 대해 이전의 프로젝트 값 가져오기 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f54-121">Repeat the previous step of importing project values for the **Supplier Name** domain.</span></span> <span data-ttu-id="e3f54-122">기본적으로 가져오기를 수행한 후에는 새 값만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3f54-122">By default, after importing, you will only see the new values.</span></span> <span data-ttu-id="e3f54-123">모든 값을 보려면 **새 항목만 표시** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f54-123">To see all the values, clear **Show Only New** check box.</span></span> <span data-ttu-id="e3f54-124">정리 작업에서 배운 내용을 활용해서 **Suppliers** 기술 자료의 데이터가 강화되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e3f54-124">You have enriched the **Suppliers** knowledge base with what you learned from the cleansing activity.</span></span> <span data-ttu-id="e3f54-125">기술 자료가 강력할수록 정리 결과도 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3f54-125">The stronger the knowledge base is, the better the cleansing results are.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e3f54-126">복합 도메인에 대해서는 값을 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e3f54-126">It is not possible import values for a composite domain.</span></span>  
  
9. <span data-ttu-id="e3f54-127">도구 모음에서 **기술 자료 내보내기** 아이콘을 클릭한 후 **기술 자료 내보내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f54-127">Click **Export Knowledge Base** icon on the toolbar and then click **Export Knowledge Base**.</span></span>  
  
     <span data-ttu-id="e3f54-128">![기술 자료 내보내기 메뉴](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-02.jpg "기술 자료 내보내기 메뉴")</span><span class="sxs-lookup"><span data-stu-id="e3f54-128">![Export Knowledge Base Menu](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-02.jpg "Export Knowledge Base Menu")</span></span>  
  
10. <span data-ttu-id="e3f54-129">자습서 폴더로 이동하고 **파일 이름** 으로 **Suppliers.dqs**를 입력하고 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f54-129">Navigate to the Tutorial folder, type **Suppliers.dqs** for the **file name**, and click **Save**.</span></span> <span data-ttu-id="e3f54-130">이 DQS 파일을 기반으로 사용해서 새로운 기술 자료를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3f54-130">You can use this DQS file to create a new knowledge base based on it.</span></span>  
  
11. <span data-ttu-id="e3f54-131">**확인** 을 클릭 하 여 **기술 자료 내보내기-Suppliers** 메시지 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e3f54-131">Click **OK** to close the **Export Knowledge Base - Suppliers** message box.</span></span>  
  
12. <span data-ttu-id="e3f54-132">**마침** 을 클릭하여 작업을 마칩니다.</span><span class="sxs-lookup"><span data-stu-id="e3f54-132">Click **Finish** to finish the activity.</span></span>  
  
13. <span data-ttu-id="e3f54-133">**게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f54-133">Click **Publish**.</span></span>  
  
14. <span data-ttu-id="e3f54-134">메시지 상자에서 **확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f54-134">Click **OK** on the message box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="e3f54-135">다음 단계</span><span class="sxs-lookup"><span data-stu-id="e3f54-135">Next Step</span></span>  
 [<span data-ttu-id="e3f54-136">3단원: 데이터 일치로 공급자 목록에서 중복 항목 제거</span><span class="sxs-lookup"><span data-stu-id="e3f54-136">Lesson 3: Matching Data to Remove Duplicates from Supplier List</span></span>](../../2014/tutorials/lesson-3-matching-data-to-remove-duplicates-from-supplier-list.md)  
  
  
