---
title: 데이터 흐름 성능 카운터에 대 한 로그 추가 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- performance counters [Integration Services]
- counters [Integration Services]
- logs [Integration Services], data flow counters
ms.assetid: b500d166-33ba-4b82-a92d-b0a333924e8d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 489bde1b0e5769f05d1063eb0af2376b659574de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736676"
---
# <a name="add-a-log-for-data-flow-performance-counters"></a><span data-ttu-id="c2880-102">데이터 흐름 성능 카운터에 대한 로그 추가</span><span class="sxs-lookup"><span data-stu-id="c2880-102">Add a Log for Data Flow Performance Counters</span></span>
  <span data-ttu-id="c2880-103">이 절차에서는 데이터 엔진에서 제공하는 성능 카운터에 대한 로그를 추가하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c2880-103">This procedure describes how to add a log for the performance counters that the data flow engine provides.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c2880-104">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 을 실행하는 컴퓨터에 [!INCLUDE[winxpsvr](../includes/winxpsvr-md.md)]를 설치한 다음 해당 컴퓨터를 [!INCLUDE[firstref_longhorn](../includes/firstref-longhorn-md.md)]로 업그레이드하는 경우 업그레이드 프로세스는 컴퓨터에서 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 성능 카운터를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="c2880-104">If you install [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] on a computer that is running [!INCLUDE[winxpsvr](../includes/winxpsvr-md.md)], and then upgrade that computer to [!INCLUDE[firstref_longhorn](../includes/firstref-longhorn-md.md)], the upgrade process removes the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] performance counters from the computer.</span></span> <span data-ttu-id="c2880-105">컴퓨터에 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 성능 카운터를 복원하려면 복원 모드에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 설치 프로그램을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c2880-105">To restore the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] performance counters on the computer, run [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Setup in repair mode.</span></span>  
  
### <a name="to-add-logging-of-performance-counters"></a><span data-ttu-id="c2880-106">성능 카운터 로깅을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="c2880-106">To add logging of performance counters</span></span>  
  
1.  <span data-ttu-id="c2880-107">클래식 보기를 사용하는 경우 **제어판**에서 **관리 도구**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2880-107">In **Control Panel**, if you are using Classic view, click **Administrative Tools**.</span></span> <span data-ttu-id="c2880-108">종류별 보기를 사용하는 경우 **성능 및 유지 관리** 를 클릭한 다음 **관리 도구**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2880-108">If you are using Category view, click **Performance and Maintenance** and then click **Administrative Tools**.</span></span>  
  
2.  <span data-ttu-id="c2880-109">**성능**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2880-109">Click **Performance**.</span></span>  
  
3.  <span data-ttu-id="c2880-110">**성능** 대화 상자에서 **성능 로그 및 경고**를 확장하고 **카운터 로그**를 마우스 오른쪽 단추로 클릭한 다음 **새 로그 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2880-110">In the **Performance** dialog box, expand **Performance Logs and Alerts**, right-click **Counter Logs**, and then click **New Log Settings**.</span></span> <span data-ttu-id="c2880-111">로그 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c2880-111">Type the name of the log.</span></span> <span data-ttu-id="c2880-112">예를 들어 **MyLog**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c2880-112">For example, type **MyLog**.</span></span>  
  
4.  <span data-ttu-id="c2880-113">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2880-113">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="c2880-114">**MyLog** 대화 상자에서 **카운터 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2880-114">In the **MyLog** dialog box, click **Add Counters**.</span></span>  
  
6.  <span data-ttu-id="c2880-115">**로컬 컴퓨터 카운터 사용** 을 클릭하여 로컬 컴퓨터에 성능 카운터를 로그하거나 **다음 컴퓨터에서 카운터 선택** 을 클릭하고 목록에서 컴퓨터를 선택하여 지정된 컴퓨터에서 성능 카운터를 로그합니다.</span><span class="sxs-lookup"><span data-stu-id="c2880-115">Click **Use local computer counters** to log performance counters on the local computer, or click **Select counters from computer** and then select a computer from the list to log performance counters on the specified computer.</span></span>  
  
7.  <span data-ttu-id="c2880-116">**카운터 추가** 대화 상자의 **성능 개체** 목록에서 **SQL Server:SSIS Pipeline** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c2880-116">In the **Add Counters** dialog box, select **SQL Server:SSIS Pipeline** in the **Performance object** list.</span></span>  
  
8.  <span data-ttu-id="c2880-117">다음 중 하나를 수행하여 성능 카운터를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c2880-117">To select performance counters, do one of the following:</span></span>  
  
    -   <span data-ttu-id="c2880-118">**모든 카운터** 를 선택하여 모든 성능 카운터를 로그합니다.</span><span class="sxs-lookup"><span data-stu-id="c2880-118">Select **All Counters** to log all performance counters.</span></span>  
  
    -   <span data-ttu-id="c2880-119">**목록에서 카운터 선택** 을 선택하고 사용할 성능 카운터를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c2880-119">Select **Select counters in list** and select the performance counters to use.</span></span>  
  
9. <span data-ttu-id="c2880-120">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2880-120">Click **Add**.</span></span>  
  
10. <span data-ttu-id="c2880-121">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2880-121">Click **Close**.</span></span>  
  
11. <span data-ttu-id="c2880-122">**MyLog** 대화 상자의 **카운터** 목록에서 로깅 성능 카운터 목록을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="c2880-122">In the **MyLog** dialog box, review the list of logging performance counters in the **Counters** list.</span></span>  
  
12. <span data-ttu-id="c2880-123">추가 카운터를 추가하려면 5단계~10단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="c2880-123">To add additional counters, repeat steps 5 through 10.</span></span>  
  
13. <span data-ttu-id="c2880-124">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2880-124">Click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c2880-125">Administrators 그룹의 멤버인 로컬 계정 또는 도메인 계정을 사용하여 성능 로그 및 경고 서비스를 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2880-125">You must start the Performance Logs and Alerts service using a local account or a domain account that is a member of the Administrators group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2880-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c2880-126">See Also</span></span>  
 <span data-ttu-id="c2880-127">[성능 카운터](performance/performance-counters.md) </span><span class="sxs-lookup"><span data-stu-id="c2880-127">[Performance Counters](performance/performance-counters.md) </span></span>  
 [<span data-ttu-id="c2880-128">이벤트 로그 창에서 로그 항목 보기</span><span class="sxs-lookup"><span data-stu-id="c2880-128">View Log Entries in the Log Events Window</span></span>](../../2014/integration-services/view-log-entries-in-the-log-events-window.md)  
  
  
