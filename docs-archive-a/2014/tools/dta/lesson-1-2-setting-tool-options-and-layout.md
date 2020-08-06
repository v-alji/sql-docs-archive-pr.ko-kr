---
title: 도구 옵션 및 레이아웃 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], tutorials
ms.assetid: 43e97ce0-97bc-4a27-9485-5bbeb7190b85
author: stevestein
ms.author: sstein
ms.openlocfilehash: 96d853a85b8ee4d451c55d7ea59af3755887be22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734787"
---
# <a name="setting-tool-options-and-layout"></a><span data-ttu-id="cf464-102">도구 옵션 및 레이아웃 설정</span><span class="sxs-lookup"><span data-stu-id="cf464-102">Setting Tool Options and Layout</span></span>
  <span data-ttu-id="cf464-103">시작할 때 데이터베이스 엔진 튜닝 관리자 GUI(그래픽 사용자 인터페이스)에 표시되는 사항, 사용되는 글꼴 및 인터페이스 사용법을 가장 잘 지원하는 기타 도구 기능을 구성하는 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf464-103">You can set options that configure what the Database Engine Tuning Advisor graphical user interface (GUI) displays on startup, the font it uses, and other tool functionality to best support how you use it.</span></span> <span data-ttu-id="cf464-104">이 페이지의 연습을 통해 사용자가 설정할 수 있는 옵션과 해당 옵션을 설정하는 방법에 익숙해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf464-104">The practices on this page familiarize you with the options you can set, and how to set them.</span></span>  
  
### <a name="set-the-tool-options"></a><span data-ttu-id="cf464-105">도구 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="cf464-105">Set the tool options</span></span>  
  
1.  <span data-ttu-id="cf464-106">데이터베이스 엔진 튜닝 관리자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="cf464-106">Start the Database Engine Tuning Advisor.</span></span> <span data-ttu-id="cf464-107">Windows **시작** 메뉴에서 **모든 프로그램**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **성능 도구**를 차례로 가리킨 다음 **데이터베이스 엔진 튜닝 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf464-107">On the Windows **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Performance Tools**, and click **Database Engine Tuning Advisor**.</span></span>  
  
2.  <span data-ttu-id="cf464-108">**도구** 메뉴에서 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf464-108">On the **Tools** menu, click **Options**.</span></span>  
  
3.  <span data-ttu-id="cf464-109">**옵션** 대화 상자에서 다음 옵션을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="cf464-109">In the **Options** dialog box, view the following options:</span></span>  
  
    -   <span data-ttu-id="cf464-110">**시작 시** 목록을 확장하여 데이터베이스 엔진 튜닝 관리자를 시작할 때 표시될 수 있는 사항을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="cf464-110">Expand the **On startup** list to view what Database Engine Tuning Advisor can display when it is started.</span></span> <span data-ttu-id="cf464-111">기본적으로 **새 세션 표시** 가 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf464-111">By default, **Show a new session** is selected.</span></span>  
  
    -   <span data-ttu-id="cf464-112">**글꼴 변경** 을 클릭 하 여 **일반** 탭의 데이터베이스 및 테이블 목록에 대해 선택할 수 있는 글꼴을 확인 합니다. 이 옵션에 대해 선택한 글꼴은 튜닝을 수행한 후 데이터베이스 엔진 튜닝 관리자 권장 사항 표와 보고서에도 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf464-112">Click **Change Font** to see what fonts you can choose for the lists of databases and tables on the **General** tab. The fonts you choose for this option also are used in Database Engine Tuning Advisor recommendation grids and reports after you have performed tuning.</span></span> <span data-ttu-id="cf464-113">기본적으로 데이터베이스 엔진 튜닝 관리자에서는 시스템 글꼴을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cf464-113">By default, Database Engine Tuning Advisor uses system fonts.</span></span>  
  
    -   <span data-ttu-id="cf464-114">**가장 최근에 사용한 목록의 항목 수** 는 **1** 과 **10**사이에서 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf464-114">The **Number of items in most recently used lists** can be set between **1** and **10**.</span></span> <span data-ttu-id="cf464-115">그러면 **파일** 메뉴에서 **최근에 사용한 세션** 이나 **최근에 사용한 파일** 을 클릭할 때 표시되는 목록의 최대 항목 수가 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf464-115">This sets the maximum number of items in the lists displayed by clicking **Recent Sessions** or **Recent Files** on the **File** menu.</span></span> <span data-ttu-id="cf464-116">기본적으로 이 옵션은 **4**로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf464-116">By default, this option is set to **4**.</span></span>  
  
    -   <span data-ttu-id="cf464-117">**마지막 튜닝 옵션 저장** 을 선택하면 기본적으로 데이터베이스 엔진 튜닝 관리자에서 마지막 튜닝 세션에 대해 지정된 튜닝 옵션을 다음 튜닝 세션에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cf464-117">When **Remember my last tuning options** is checked, by default Database Engine Tuning Advisor uses the tuning options you specified for your last tuning session for the next tuning session.</span></span> <span data-ttu-id="cf464-118">데이터베이스 엔진 튜닝 관리자 옵션 기본값을 사용하려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="cf464-118">Clear this check box to use Database Engine Tuning Advisor tuning option defaults.</span></span> <span data-ttu-id="cf464-119">이 옵션은 기본적으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf464-119">By default, this option is selected.</span></span>  
  
    -   <span data-ttu-id="cf464-120">기본적으로 튜닝 세션을 실수로 삭제하지 않도록 **세션을 영구적으로 삭제하기 전에 확인** 이 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf464-120">By default, **Ask before permanently deleting sessions** is checked to avoid accidentally deleting tuning sessions.</span></span>  
  
    -   <span data-ttu-id="cf464-121">데이터베이스 엔진 튜닝 관리자가 작업 분석을 완료하기 전에 튜닝 세션을 실수로 중지하지 않도록 **세션 분석을 중지하기 전에 확인** 이 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf464-121">By default, **Ask before stopping session analysis** is checked to avoid accidentally stopping a tuning session before Database Engine Tuning Advisor has finished analyzing a workload.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="cf464-122">다음 단원</span><span class="sxs-lookup"><span data-stu-id="cf464-122">Next Lesson</span></span>  
 [<span data-ttu-id="cf464-123">2단원: 데이터베이스 엔진 튜닝 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="cf464-123">Lesson 2: Using Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
