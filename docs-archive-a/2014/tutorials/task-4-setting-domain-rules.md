---
title: '작업 4: 도메인 규칙 설정 | Microsoft Docs'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3a7162ba-cf2f-481f-830d-bb6a02823827
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 42bdbd0228fdd3515f68ce830581f445242768e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646736"
---
# <a name="task-4-setting-domain-rules"></a><span data-ttu-id="b7c25-102">태스크 4: 도메인 규칙 설정</span><span class="sxs-lookup"><span data-stu-id="b7c25-102">Task 4: Setting Domain Rules</span></span>
  <span data-ttu-id="b7c25-103">이 작업에서는 **연락처 전자 메일** 도메인에 대 한 규칙을 만들어 전자 메일 주소가 \*\* \@ adventure-works.com\*\*으로 끝나는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7c25-103">In this task, you create a rule for the **Contact Email** domain to verify if the email address ends with **\@adventure-works.com**.</span></span> <span data-ttu-id="b7c25-104">이 페이지에 대한 자세한 내용은 [도메인 규칙 만들기](https://msdn.microsoft.com/library/hh510397.aspx) 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b7c25-104">See [Creating a Domain Rule](https://msdn.microsoft.com/library/hh510397.aspx) topic for more details on the page.</span></span>  
  
1.  <span data-ttu-id="b7c25-105">**도메인 목록** 에서 **Contact Email**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b7c25-105">Click **Contact Email** in the **Domain list**.</span></span>  
  
2.  <span data-ttu-id="b7c25-106">오른쪽 창에서 **도메인 규칙** 으로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="b7c25-106">Switch to the **Domain Rules** tab in the right pane.</span></span>  
  
     <span data-ttu-id="b7c25-107">![새 도메인 규칙 추가 도구 모음 단추](../../2014/tutorials/media/et-settingdomainrules-01.jpg "새 도메인 규칙 추가 도구 모음 단추")</span><span class="sxs-lookup"><span data-stu-id="b7c25-107">![Add a New Domain Rule Toolbar Button](../../2014/tutorials/media/et-settingdomainrules-01.jpg "Add a New Domain Rule Toolbar Button")</span></span>  
  
3.  <span data-ttu-id="b7c25-108">오른쪽 창의 도구 모음에서 **새 도메인 규칙 추가** 단추를 클릭하여 규칙을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b7c25-108">In the right pane, click **Add a new domain rule** button on the toolbar (see the image) to add a rule.</span></span>  
  
4.  <span data-ttu-id="b7c25-109">**규칙 이름** 에 **Email Validation** 을 입력하고 **Enter**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b7c25-109">Type **Email Validation** for the **rule name** and press **ENTER**.</span></span> <span data-ttu-id="b7c25-110">**활성** 확인란은 기본적으로 선택되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7c25-110">The **Active** check box should be checked by default.</span></span> <span data-ttu-id="b7c25-111">이 컨트롤을 사용하면 규칙을 일시적으로 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7c25-111">This control allows you to deactivate a rule temporarily.</span></span>  
  
5.  <span data-ttu-id="b7c25-112">**규칙 작성** 창에서 **아래쪽 화살표**를 클릭하고 **값이 다음으로 종료**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b7c25-112">In the **Build a Rule** pane, click **down arrow**, and select **Value ends with**.</span></span>  
  
6.  <span data-ttu-id="b7c25-113">텍스트 상자에 \*\* \@ adventure-works.com\*\* 를 입력 하 고 **tab**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b7c25-113">Type **\@adventure-works.com** in the text box and press **TAB**.</span></span> <span data-ttu-id="b7c25-114">**규칙 작성** 창에서 **선택한 절에 새 조건 추가** 도구 모음 단추를 클릭하여 조건을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7c25-114">You can add more conditions by clicking **Add a new condition to the selected clause** toolbar button in the **Build a Rule** pane.</span></span>  
  
     <span data-ttu-id="b7c25-115">![전자 메일 유효성 검사 규칙](../../2014/tutorials/media/et-settingdomainrules-02.jpg "전자 메일 유효성 검사 규칙")</span><span class="sxs-lookup"><span data-stu-id="b7c25-115">![Email Validation Rule](../../2014/tutorials/media/et-settingdomainrules-02.jpg "Email Validation Rule")</span></span>  
  
7.  <span data-ttu-id="b7c25-116">오른쪽 창의 도구 모음에서 **테스트 데이터에서 선택한 도메인 규칙 실행** 단추를 클릭하여 예제 데이터로 규칙을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="b7c25-116">Click **Run the selected domain rule on test data** button on the toolbar in the right pane to test the rule against sample data.</span></span>  
  
     <span data-ttu-id="b7c25-117">![테스트 데이터에 대한 도메인 규칙 실행 도구 모음 단추](../../2014/tutorials/media/et-settingdomainrules-03.jpg "테스트 데이터에 대한 도메인 규칙 실행 도구 모음 단추")</span><span class="sxs-lookup"><span data-stu-id="b7c25-117">![Run the Domain Rule on Test Data Toolbar Button](../../2014/tutorials/media/et-settingdomainrules-03.jpg "Run the Domain Rule on Test Data Toolbar Button")</span></span>  
  
8.  <span data-ttu-id="b7c25-118">**도메인 규칙 테스트** 대화 상자의 도구 모음에서 **도메인 규칙에서 새 테스트 용어를 추가합니다.** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b7c25-118">In the **Test Domain Rule** dialog box, click **Adds a new testing term for the domain rule** button on the toolbar.</span></span>  
  
     <span data-ttu-id="b7c25-119">![도메인 규칙 테스트 대화 상자](../../2014/tutorials/media/et-settingdomainrules-04.jpg "도메인 규칙 테스트 대화 상자")</span><span class="sxs-lookup"><span data-stu-id="b7c25-119">![Test Domain Rule Dialog Box](../../2014/tutorials/media/et-settingdomainrules-04.jpg "Test Domain Rule Dialog Box")</span></span>  
  
9. <span data-ttu-id="b7c25-120">**Contact Email** 열에 **frank7 \@ adventure-works.com** (올바른 값)를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7c25-120">Type **frank7\@adventure-works.com** (a valid value) in the **Contact Email** column.</span></span>  
  
10. <span data-ttu-id="b7c25-121">이전 두 단계를 반복 하 여 **joe2 \@ adventure-work.com** (가 없는 잘못 된 값)을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7c25-121">Repeat previous two steps to add **joe2\@adventure-work.com** (an invalid value with no 's').</span></span>  
  
11. <span data-ttu-id="b7c25-122">도구 모음에서 마지막 단추(**모든 용어에 대한 도메인 규칙을 테스트합니다.**)를 클릭하여 규칙에 대해 입력 데이터를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="b7c25-122">Click the last button (**Test the domain rule on all the terms**) on the toolbar to test the input data against the rule.</span></span>  
  
     <span data-ttu-id="b7c25-123">![모든 용어에 대해 도메인 규칙 테스트 도구 모음 단추](../../2014/tutorials/media/et-settingdomainrules-05.jpg "모든 용어에 대해 도메인 규칙 테스트 도구 모음 단추")</span><span class="sxs-lookup"><span data-stu-id="b7c25-123">![Test the Domain Rule on All Terms Toolbar Button](../../2014/tutorials/media/et-settingdomainrules-05.jpg "Test the Domain Rule on All Terms Toolbar Button")</span></span>  
  
12. <span data-ttu-id="b7c25-124">첫 번째 항목은 유효한 항목으로 표시되고 두 번째 항목은 잘못된 항목으로 표시됨을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7c25-124">Notice that the first entry is shown as a valid item and the second one as an invalid item.</span></span>  
  
     <span data-ttu-id="b7c25-125">![도메인 규칙 테스트 결과](../../2014/tutorials/media/et-settingdomainrules-06.jpg "도메인 규칙 테스트 결과")</span><span class="sxs-lookup"><span data-stu-id="b7c25-125">![Test Domain Rule Results](../../2014/tutorials/media/et-settingdomainrules-06.jpg "Test Domain Rule Results")</span></span>  
  
13. <span data-ttu-id="b7c25-126">**닫기** 를 클릭하여 **도메인 규칙 테스트** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="b7c25-126">Click **Close** to close the **Test Domain Rule** dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="b7c25-127">다음 단계</span><span class="sxs-lookup"><span data-stu-id="b7c25-127">Next Step</span></span>  
 [<span data-ttu-id="b7c25-128">태스크 5: 용어 기반 관계 설정</span><span class="sxs-lookup"><span data-stu-id="b7c25-128">Task 5: Setting Term Based Relationships</span></span>](../../2014/tutorials/task-5-setting-term-based-relationships.md)  
  
  
