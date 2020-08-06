---
title: 이벤트 전달 서버 (SQL Server Management Studio)를 지정 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- event forwarding servers [SQL Server]
- events [SQL Server], forwarding
- alerts [SQL Server], forwarded events
ms.assetid: 81dfcbe4-3000-4e77-99de-bf85fef63a12
author: stevestein
ms.author: sstein
ms.openlocfilehash: bc5f01507bf893d1bffc682f65a01b9ff48ffa9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737455"
---
# <a name="designate-an-events-forwarding-server-sql-server-management-studio"></a><span data-ttu-id="34165-102">Designate an Events Forwarding Server (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="34165-102">Designate an Events Forwarding Server (SQL Server Management Studio)</span></span>
  <span data-ttu-id="34165-103">이 항목에서는를 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용 하 여에서 이벤트를 전달 하는 서버를 지정 하는 방법에 대해 설명 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="34165-103">This topic describes how to designate a server to which [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] forwards events in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .</span></span> <span data-ttu-id="34165-104">이벤트 전달은 서버 간에 전달되는 이벤트에만 적용되고 단일 컴퓨터에서 호스팅되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 간에 전달되는 이벤트에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34165-104">Note that event forwarding applies to events forwarded between servers, not to events forwarded between instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hosted on a single computer.</span></span> <span data-ttu-id="34165-105">또한 전달된 이벤트를 수신하려면 경고 관리 서버가 SQL Server의 기본 인스턴스여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34165-105">Also note that in order to receive forwarded events, the alerts management server must be a default instance of SQL Server.</span></span>  
  
 <span data-ttu-id="34165-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="34165-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="34165-107">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="34165-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="34165-108">보안</span><span class="sxs-lookup"><span data-stu-id="34165-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="34165-109">**다음을 사용하여 이벤트 전달 서버를 지정합니다.**</span><span class="sxs-lookup"><span data-stu-id="34165-109">**To designate an events forwarding server, using:**</span></span>  
  
     [<span data-ttu-id="34165-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="34165-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="34165-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="34165-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="34165-112">보안</span><span class="sxs-lookup"><span data-stu-id="34165-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="34165-113">권한</span><span class="sxs-lookup"><span data-stu-id="34165-113">Permissions</span></span>  
 <span data-ttu-id="34165-114">**sysadmin** 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="34165-114">Requires membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="34165-115">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="34165-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-designate-an-events-forwarding-server"></a><span data-ttu-id="34165-116">이벤트 전달 서버를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="34165-116">To designate an events forwarding server</span></span>  
  
1.  <span data-ttu-id="34165-117">**개체 탐색기** 에서 더하기 기호를 클릭하여 이벤트를 다른 서버로 전달하려는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="34165-117">In **Object Explorer,** click the plus sign to expand the server from which you want to forward events to another server.</span></span>  
  
2.  <span data-ttu-id="34165-118">**SQL Server 에이전트** 를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="34165-118">Right-click **SQL Server Agent** and select **Properties**.</span></span>  

3.  <span data-ttu-id="34165-119">**SQL Server 에이전트 속성 -**_server_name_ 대화 상자의 **페이지 선택** 아래에서 **고급**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="34165-119">In the **SQL Server Agent Properties -**_server_name_ dialog box, under **Select a page**, select **Advanced**.</span></span>  

4.  <span data-ttu-id="34165-120">**SQL Server 이벤트 전달**아래에서 **다른 서버로 이벤트 전달** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="34165-120">Under **SQL Server event forwarding**, select the **Forward events to a different server** check box.</span></span>  
  
5.  <span data-ttu-id="34165-121">**서버** 목록에서 서버를 선택하고 **이벤트**에서 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="34165-121">In the **Server** list, select a server, and then, under **Events**, select one of the following:</span></span>  
  
    -   <span data-ttu-id="34165-122">로컬 경고로 처리되지 않은 이벤트만 전달하려면 **처리되지 않은 이벤트** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="34165-122">Select **Unhandled events** to forward only the events that have not been handled by local alerts.</span></span>  
  
    -   <span data-ttu-id="34165-123">로컬 경고로 처리되었는지 여부에 관계 없이 모든 이벤트를 전달하려면 **모든 이벤트** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="34165-123">Select **All events** to forward all events regardless of whether they have been handled by local alerts.</span></span>  
  
6.  <span data-ttu-id="34165-124">**이벤트의 심각도가 다음 이상인 경우** 목록에서 선택한 서버로 이벤트가 전달되는 심각도 수준을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34165-124">In the **If event has severity at or above** list, click the severity level at which events are forwarded to the selected server.</span></span>  
  
7.  <span data-ttu-id="34165-125">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34165-125">When finished, click **OK**.</span></span>  
  
  
