---
title: '작업 5: 용어 기반 관계 설정 | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6569d512-637d-4f7b-82e1-1e8582278b37
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1589ec5843053baa6c42a0b9b0dec019c887da9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735579"
---
# <a name="task-5-setting-term-based-relationships"></a><span data-ttu-id="736a8-102">태스크 5: 용어 기반 관계 설정</span><span class="sxs-lookup"><span data-stu-id="736a8-102">Task 5: Setting Term Based Relationships</span></span>
  <span data-ttu-id="736a8-103">이 태스크에서는 **공급자 이름** 도메인의 값에 대 한 몇 가지 용어 기반 관계를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="736a8-103">In this task, you define a few term-based relations for values for the **Supplier Name** domain.</span></span> <span data-ttu-id="736a8-104">용어 기반 관계를 사용하면 도메인에서 값의 일부인 용어를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="736a8-104">A term-based relation enables you to make a correction to a term that is part of a value in a domain.</span></span> <span data-ttu-id="736a8-105">이를 통해 공통 부분의 맞춤법을 제외하고 동일한 여러 값을 동일한 동의어로 간주할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="736a8-105">It enables multiple values that are identical except for the spelling of a common part of them to be considered identical synonyms.</span></span> <span data-ttu-id="736a8-106">예를 들어 **i n c.** 는 **통합**되도록 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="736a8-106">For example, **Inc.** can be corrected to **Incorporated**.</span></span> <span data-ttu-id="736a8-107">DQS는 기술 자료 검색, 정리 또는 일치 프로세스에서 이러한 관계를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="736a8-107">DQS uses these relations in the knowledge discovery, cleansing, or matching processes.</span></span> <span data-ttu-id="736a8-108">자세한 내용은 [용어 기반 관계 만들기](https://msdn.microsoft.com/library/hh510404.aspx) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="736a8-108">See [Create Term-based Relations](https://msdn.microsoft.com/library/hh510404.aspx) for more details.</span></span>  
  
1.  <span data-ttu-id="736a8-109">**도메인 목록**에서 **공급자 이름** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="736a8-109">Select **Supplier Name** in the **Domain list**.</span></span>  
  
2.  <span data-ttu-id="736a8-110">오른쪽 창에서 **용어 기반 관계** 탭으로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="736a8-110">Switch to the **Term-Based Relationships** tab in the right pane.</span></span>  
  
3.  <span data-ttu-id="736a8-111">도구 모음에서 **새 관계 추가** 단추를 클릭 하 여 테이블에 대 한 관계를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="736a8-111">Click **Add new relation** button on the toolbar to add a relation to the table.</span></span>  
  
4.  <span data-ttu-id="736a8-112">**값** 필드에 대해 **Co** 를 입력 하 고 다음 **으로 수정** 필드에 **Company** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="736a8-112">Type **Co.** for the **Value** field and **Company** for the **Correct To** field.</span></span>  
  
5.  <span data-ttu-id="736a8-113">다음 값에 대해 위의 두 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="736a8-113">Repeat the previous two steps for the following values:</span></span>  
  
    |<span data-ttu-id="736a8-114">값</span><span class="sxs-lookup"><span data-stu-id="736a8-114">Value</span></span>|<span data-ttu-id="736a8-115">다음으로 수정</span><span class="sxs-lookup"><span data-stu-id="736a8-115">Correct To</span></span>|  
    |-----------|----------------|  
    |<span data-ttu-id="736a8-116">Corp.</span><span class="sxs-lookup"><span data-stu-id="736a8-116">Corp.</span></span>|<span data-ttu-id="736a8-117">Corporation</span><span class="sxs-lookup"><span data-stu-id="736a8-117">Corporation</span></span>|  
    |<span data-ttu-id="736a8-118">Inc.</span><span class="sxs-lookup"><span data-stu-id="736a8-118">Inc.</span></span>|<span data-ttu-id="736a8-119">Incorporated</span><span class="sxs-lookup"><span data-stu-id="736a8-119">Incorporated</span></span>|  
  
     <span data-ttu-id="736a8-120">![용어 기반 관계](../../2014/tutorials/media/et-settingtermbasedrelations.jpg "용어 기반 관계")</span><span class="sxs-lookup"><span data-stu-id="736a8-120">![Term Based Relations](../../2014/tutorials/media/et-settingtermbasedrelations.jpg "Term Based Relations")</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="736a8-121">다음 단계</span><span class="sxs-lookup"><span data-stu-id="736a8-121">Next Step</span></span>  
 [<span data-ttu-id="736a8-122">태스크 6: 동의어 설정</span><span class="sxs-lookup"><span data-stu-id="736a8-122">Task 6: Setting Synonyms</span></span>](../../2014/tutorials/task-6-setting-synonyms.md)  
  
  
