---
title: '작업 8: 복합 도메인 규칙 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: cff3b662-7876-4445-9bdd-96be35b3ca0c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 4766a1206eb09e98bb20d3712a63762126b682b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653684"
---
# <a name="task-8-creating-a-composite-domain-rule"></a><span data-ttu-id="526b6-102">태스크 8: 복합 도메인 규칙 만들기</span><span class="sxs-lookup"><span data-stu-id="526b6-102">Task 8: Creating a Composite Domain Rule</span></span>
  <span data-ttu-id="526b6-103">이 작업에서는 **주소 유효성 검사** 복합 도메인에 대 한 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="526b6-103">In this task, you create a rule for the **Address Validation** composite domain.</span></span> <span data-ttu-id="526b6-104">도메인 간 규칙을 정의 합니다. **city** **가 로스앤젤레스 인 경우**시/ **도는** **CA** 여야 합니다. 여기서 **city** 및 **state** 는 두 개의 도메인입니다.</span><span class="sxs-lookup"><span data-stu-id="526b6-104">You define a cross-domain rule: if **City** is **Los Angeles**, **State** must be **CA** where **City** and **State** are two domains.</span></span>  
  
1.  <span data-ttu-id="526b6-105">오른쪽 창에서 **CD 규칙** 탭으로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="526b6-105">In the right pane, switch to the **CD Rules** tab.</span></span>  
  
2.  <span data-ttu-id="526b6-106">도구 모음에서 **새 도메인 규칙 추가를** 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="526b6-106">Click **Add a new domain rule** from the toolbar.</span></span>  
  
3.  <span data-ttu-id="526b6-107">**이름** 에 **City 상태 규칙** 을 입력 하 고 **enter**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="526b6-107">Type **City-State Rule** for **Name** and press **ENTER**.</span></span>  
  
4.  <span data-ttu-id="526b6-108">**규칙 작성** 창의 도메인 목록에서 **City** 를 선택 하 고 조건 **값이 다음 인** 경우 값에 대해 **로스앤젤레스** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="526b6-108">In the **Build a Rule** pane, select **City** in the domain list, and select condition **Value is equal to** and type **Los Angeles** for the value.</span></span>  
  
5.  <span data-ttu-id="526b6-109">Then 창의 도메인 목록에서 **상태** 를 선택 하 고 **값이 다음을**선택 하 고 값으로 **CA** 를 입력 한 **다음** **tab**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="526b6-109">In the **Then** pane, select **State** in the domain list, and select **Value is equal to**, type **CA** for the value, and press **TAB**.</span></span>  
  
     <span data-ttu-id="526b6-110">![복합 도메인 규칙](../../2014/tutorials/media/et-creatingacompositedomainrule.jpg "복합 도메인 규칙")</span><span class="sxs-lookup"><span data-stu-id="526b6-110">![Composite Domain Rule](../../2014/tutorials/media/et-creatingacompositedomainrule.jpg "Composite Domain Rule")</span></span>  
  
6.  <span data-ttu-id="526b6-111">페이지 맨 아래에 있는 **닫기** 단추를 클릭 하 여 DQS 클라이언트의 기본 페이지로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="526b6-111">Click **Close** button at the bottom of the page to switch to the main page of DQS Client.</span></span> <span data-ttu-id="526b6-112">이 기술 자료는 다음 단원에서 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="526b6-112">You will publish the knowledge base in the next lesson.</span></span> <span data-ttu-id="526b6-113">이 기술 자료는 잠긴 상태(자물쇠 아이콘)입니다.</span><span class="sxs-lookup"><span data-stu-id="526b6-113">Notice that the knowledge base is in locked state (lock icon).</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="526b6-114">다음 단계</span><span class="sxs-lookup"><span data-stu-id="526b6-114">Next Step</span></span>  
 [<span data-ttu-id="526b6-115">태스크 9: 참조 데이터 서비스 구성</span><span class="sxs-lookup"><span data-stu-id="526b6-115">Task 9: Configuring a Reference Data Service</span></span>](../../2014/tutorials/task-9-configuring-a-reference-data-service.md)  
  
  
