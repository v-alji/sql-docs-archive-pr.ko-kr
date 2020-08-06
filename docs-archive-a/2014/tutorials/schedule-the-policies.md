---
title: 정책 예약 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 59417a54-55f1-4468-ba41-368aa852c2d4
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 1bce1b9d650606e9485899c34c72ca6b27a72dae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735608"
---
# <a name="schedule-the-policies"></a><span data-ttu-id="6a7ee-102">정책 예약</span><span class="sxs-lookup"><span data-stu-id="6a7ee-102">Schedule the Policies</span></span>
  <span data-ttu-id="6a7ee-103">이 태스크에서는 이전 태스크에서 가져온 최선의 구현 방법 정책을 예약합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-103">In this task, you will schedule the best practices policies that you imported in the previous task.</span></span>  
  
### <a name="to-schedule-the-best-practices-policies"></a><span data-ttu-id="6a7ee-104">최선의 구현 방법 정책을 예약하려면</span><span class="sxs-lookup"><span data-stu-id="6a7ee-104">To schedule the best practices policies</span></span>  
  
1.  <span data-ttu-id="6a7ee-105">개체 탐색기에서 **관리**, **정책 관리**, **정책을 차례로**확장 하 고 모범 사례 정책을 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-105">In Object Explorer, expand **Management**, expand **Policy Management**, expand **Policies**, right-click a best practices policy, and then click **Properties**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6a7ee-106">또는 모범 사례와 관련 된 정책을 쉽게 확인 하 고 모범 사례 범주를 정렬 하려면 **관리**, **정책 관리**를 차례로 확장 한 다음 **정책**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-106">As an alternative, to easily see which policies are associated with best practices and to sort the best practices categories, expand **Management**, expand **Policy Management**, and then click **Policies**.</span></span> <span data-ttu-id="6a7ee-107">**보기** 메뉴에서 **개체 탐색기 정보**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-107">On the **View** menu, click **Object Explorer Details**.</span></span> <span data-ttu-id="6a7ee-108">**개체 탐색기 세부 정보** 창에서 **범주** 제목을 클릭 하 여 범주별로 정책을 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-108">In the **Object Explorer Details** pane, click the **Category** heading to sort the policies by category.</span></span> <span data-ttu-id="6a7ee-109">최선의 구현 방법 정책에는 **Microsoft 모범 사례**접두사가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-109">The best practices policies have the prefix **Microsoft Best Practices**.</span></span> <span data-ttu-id="6a7ee-110">구성 하려는 정책을 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-110">Right-click the policy that you want to configure, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="6a7ee-111">**정책 열기** 대화 상자의 **일반** 페이지에 있는 **평가 모드** 목록에서 **일정을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-111">On the **General** page of the **Open Policy** dialog box, in the **Evaluation Mode** list, click **On schedule**.</span></span>  
  
3.  <span data-ttu-id="6a7ee-112">**일정** 상자 옆의 **선택** 을 클릭 하 여 기존 일정을 지정 하거나 **새로** 만들기를 클릭 하 여 새 일정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-112">Next to the **Schedule** box, click **Pick** to specify an existing schedule, or click **New** to create a new schedule.</span></span>  
  
4.  <span data-ttu-id="6a7ee-113">일정을 구성한 후 페이지 맨 위 근처에서 **사용** 확인란을 선택 하 여 예약 된 정책을 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-113">After you have configured a schedule, you can select the **Enabled** check box near the top of the page to enable the scheduled policy.</span></span>  
  
5.  <span data-ttu-id="6a7ee-114">예약할 각 정책에 대해 1-4단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-114">Repeats steps 1 through 4 for each policy that you want to schedule.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6a7ee-115">예약된 정책 실행 이후 평가 결과를 보려면 대상 인스턴스에 대한 정책 기록 로그를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-115">To view the evaluation results after a scheduled policy runs, open the Policy History log on the target instance.</span></span> <span data-ttu-id="6a7ee-116">로그를 열려면 **정책 관리**를 마우스 오른쪽 단추로 클릭 한 다음 **기록 보기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-116">To open the log, right-click **Policy Management**, and then click **View History**.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="6a7ee-117">요약</span><span class="sxs-lookup"><span data-stu-id="6a7ee-117">Summary</span></span>  
 <span data-ttu-id="6a7ee-118">예약된 정책을 단일 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에서 실행하도록 구성했습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-118">You configured scheduled policies to run on a single instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6a7ee-119">예약된 정책을 여러 인스턴스에 배포하려면 이 자습서의 다음 태스크를 계속 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-119">If you want to deploy scheduled policies to multiple instances, continue to the next task in this tutorial.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="6a7ee-120">다음 단계</span><span class="sxs-lookup"><span data-stu-id="6a7ee-120">Next Steps</span></span>  
 [<span data-ttu-id="6a7ee-121">여러 인스턴스에 예약된 정책 배포</span><span class="sxs-lookup"><span data-stu-id="6a7ee-121">Deploy Scheduled Policies to Multiple Instances</span></span>](../../2014/tutorials/deploy-scheduled-policies-to-multiple-instances.md)  
  
  
