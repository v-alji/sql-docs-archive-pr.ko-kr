---
title: SQL Server 데이터베이스 경고 설정(Windows) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- alerts [SQL Server], creating
ms.assetid: 65d2c5c1-921f-4eff-9ef7-149170ab61e8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 090eeda2c134857df18d083ce06d460214aa4dfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661071"
---
# <a name="set-up-a-sql-server-database-alert-windows"></a><span data-ttu-id="4a73a-102">SQL Server 데이터베이스 경고 설정(Windows)</span><span class="sxs-lookup"><span data-stu-id="4a73a-102">Set Up a SQL Server Database Alert (Windows)</span></span>
  <span data-ttu-id="4a73a-103">시스템 모니터를 사용하여 시스템 모니터 카운터에 대한 임계값에 도달했을 때 경고를 발생시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a73a-103">Using System Monitor, you can create an alert to be raised when a threshold value for a System Monitor counter has been reached.</span></span> <span data-ttu-id="4a73a-104">시스템 모니터는 경고에 대한 응답으로 경고 조건을 처리하기 위해 쓰여진 사용자 지정 애플리케이션과 같은 애플리케이션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="4a73a-104">In response to the alert, System Monitor can launch an application, such as a custom application written to handle the alert condition.</span></span> <span data-ttu-id="4a73a-105">예를 들어 교착 상태의 횟수가 지정한 값을 넘어설 때 경고를 발생시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a73a-105">For example, you can create an alert that is raised when the number of deadlocks exceeds a specific value.</span></span>  
  
 <span data-ttu-id="4a73a-106">Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 사용하여 경고를 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a73a-106">Alerts also can be defined using Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="4a73a-107">자세한 내용은 [경고](../../ssms/agent/alerts.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4a73a-107">For more information, see [Alerts](../../ssms/agent/alerts.md).</span></span>  
  
### <a name="to-set-up-a-sql-server-database-alert"></a><span data-ttu-id="4a73a-108">SQL Server 데이터베이스 경고를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="4a73a-108">To set up a SQL Server database alert</span></span>  
  
1.  <span data-ttu-id="4a73a-109">성능 창의 탐색 트리에서 **성능 로그 및 경고**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="4a73a-109">On the navigation tree of the Performance window, expand **Performance Logs and Alerts**.</span></span>  
  
2.  <span data-ttu-id="4a73a-110">**경고**를 마우스 오른쪽 단추로 클릭한 다음 **새 경고 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4a73a-110">Right-click **Alerts**, and then click **New Alert Settings**.</span></span>  
  
3.  <span data-ttu-id="4a73a-111">**새 경고 설정** 대화 상자에서 새 경고의 이름을 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4a73a-111">In the **New Alert Settings** dialog box, type a name for the new alert, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="4a73a-112">새 경고에 대한 대화 상자의 **일반** 탭에서 **설명**을 추가하고 **추가** 를 클릭하여 카운터를 경고에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4a73a-112">On the **General** tab of the dialog box for the new alert, add a **Comment**, and click **Add** to add a counter to the alert.</span></span>  
  
     <span data-ttu-id="4a73a-113">모든 경고에는 적어도 하나의 카운터가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a73a-113">All alerts must have at least one counter.</span></span>  
  
5.  <span data-ttu-id="4a73a-114">카운터 추가 대화 상자의 **성능 개체** 목록에서 SQL Server 개체를 선택하고 **목록에서 카운터 선택**에서 카운터를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4a73a-114">In the Add Counters dialog box, select a SQL Server object from the **Performance Object** list, and then select a counter from the **Select counters from list**.</span></span>  
  
6.  <span data-ttu-id="4a73a-115">카운터를 경고에 추가하려면 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4a73a-115">To add the counter to the alert, click **Add**.</span></span> <span data-ttu-id="4a73a-116">카운터를 계속 추가하거나 새 경고를 위해 대화 상자로 돌아가려면 **닫기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4a73a-116">You can continue to add counters, or you can click **Close** to return to the dialog box for the new alert.</span></span>  
  
7.  <span data-ttu-id="4a73a-117">새 경고 대화 상자에서 **값이 다음일 때 경고 표시** 에서 **초과**또는 **미만** 을 클릭하거나 **제한**에 임계값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4a73a-117">In the new alert dialog box, click either **Over** or **Under**in the **Alert when the value is** list, and then enter a threshold value in **Limit**.</span></span>  
  
     <span data-ttu-id="4a73a-118">카운터의 값이 이 임계값보다 크거나 작으면 **초과** 또는 **미만**선택 여부에 따라 경고가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a73a-118">The alert is generated when the value for the counter is more than or less than the threshold value (depending on whether you clicked **Over** or **Under**).</span></span>  
  
8.  <span data-ttu-id="4a73a-119">**데이터 샘플 간격** 상자에서 샘플 빈도를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a73a-119">In the **Sample data every** boxes, set the sampling frequency.</span></span>  
  
9. <span data-ttu-id="4a73a-120">**동작** 탭에서 경고가 트리거될 때마다 일어날 동작을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a73a-120">On the **Action** tab, set actions to occur every time the alert is triggered.</span></span>  
  
10. <span data-ttu-id="4a73a-121">**일정** 탭에서 경고 검사의 시작 및 중지 예약을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a73a-121">On the **Schedule** tab, set the start and stop schedule for the alert scan.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a73a-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4a73a-122">See Also</span></span>  
 [<span data-ttu-id="4a73a-123">SQL Server 데이터베이스 경고 만들기</span><span class="sxs-lookup"><span data-stu-id="4a73a-123">Create a SQL Server Database Alert</span></span>](../performance-monitor/create-a-sql-server-database-alert.md)  
  
  
