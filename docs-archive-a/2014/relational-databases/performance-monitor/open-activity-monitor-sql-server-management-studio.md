---
title: 작업 모니터 열기(SQL Server Management Studio) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Activity Monitor [SQL Server], setting the refresh interval
- refresh interval for Activity Monitor
- Activity Monitor [SQL Server], opening
- opening Activity Monitor
ms.assetid: 0a6eeb16-f02b-479d-9a60-543e40ebf46b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ea74122ad18a0a1ede5eef1e09684606ca0ce073
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739735"
---
# <a name="open-activity-monitor-sql-server-management-studio"></a><span data-ttu-id="0ee19-102">작업 모니터 열기(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="0ee19-102">Open Activity Monitor (SQL Server Management Studio)</span></span>
  <span data-ttu-id="0ee19-103">이 항목에서는 작업 모니터를 열어서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스에 대한 정보 및 이러한 프로세스가 현재 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 미치는 영향에 대한 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ee19-103">This topic describes how to open the Activity Monitor to obtain information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] processes and how these processes affect the current instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0ee19-104">또한 작업 모니터의 새로 고침 간격을 설정하는 방법에 대해서도 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee19-104">It also describes how to set the refresh interval of the Activity Monitor.</span></span>  
  
 <span data-ttu-id="0ee19-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="0ee19-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0ee19-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="0ee19-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0ee19-107">보안</span><span class="sxs-lookup"><span data-stu-id="0ee19-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0ee19-108">**작업 모니터를 열려면**</span><span class="sxs-lookup"><span data-stu-id="0ee19-108">**To open the Activity Monitor using:**</span></span>  
  
     [<span data-ttu-id="0ee19-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0ee19-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   <span data-ttu-id="0ee19-110">**새로 고침 간격 설정에 사용되는 도구:**  [SQL Server Management Studio](#Refresh)</span><span class="sxs-lookup"><span data-stu-id="0ee19-110">**To set the refresh interval using:**  [SQL Server Management Studio](#Refresh)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0ee19-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="0ee19-111">Before You Begin</span></span>  
 <span data-ttu-id="0ee19-112">작업 모니터에서는 모니터링 대상 인스턴스에 대해 쿼리를 실행하여 작업 모니터 표시 창에 대한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0ee19-112">Activity Monitor runs queries on the monitored instance to obtain information for the Activity Monitor display panes.</span></span> <span data-ttu-id="0ee19-113">자동 새로 고침 간격을 10초보다 작게 설정하면 이러한 쿼리를 실행하는 데 사용되는 시간이 서버 성능에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ee19-113">When the refresh interval is set to less than 10 seconds, the time that is used to run these queries can affect server performance</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0ee19-114">보안</span><span class="sxs-lookup"><span data-stu-id="0ee19-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0ee19-115">권한</span><span class="sxs-lookup"><span data-stu-id="0ee19-115">Permissions</span></span>  
 <span data-ttu-id="0ee19-116">작업 모니터를 보려면 사용자에게 VIEW SERVER STATE 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee19-116">To view the Activity Monitor, a user must have VIEW SERVER STATE permission.</span></span> <span data-ttu-id="0ee19-117">작업 모니터의 데이터 파일 I/O 섹션을 보려면 CREATE DATABASE, ALTER ANY DATABASE 또는 VIEW ANY DEFINITION 권한과 VIEW SERVER STATE 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee19-117">To view the Data File I/O section of Activity Monitor, you must have CREATE DATABASE, ALTER ANY DATABASE, or VIEW ANY DEFINITION permission in addition to VIEW SERVER STATE.</span></span>  
  
 <span data-ttu-id="0ee19-118">프로세스를 중단하려면 사용자가 sysadmin 또는 processadmin 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee19-118">To KILL a process, a user must be a member of the sysadmin or processadmin fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0ee19-119">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="0ee19-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-open-activity-monitor-in-sql-server-management-studio"></a><span data-ttu-id="0ee19-120">SQL Server Management Studio에서 작업 모니터를 열려면</span><span class="sxs-lookup"><span data-stu-id="0ee19-120">To open Activity Monitor in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="0ee19-121">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 표준 도구 모음에서 **작업 모니터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee19-121">On the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] standard toolbar, click **Activity Monitor**.</span></span>  
  
2.  <span data-ttu-id="0ee19-122">**서버에 연결** 대화 상자에서 서버 이름과 인증 모드를 선택한 다음 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee19-122">In the **Connect to Server** dialog box, select the server name and authentication mode, and then click **Connect**.</span></span>  
  
 <span data-ttu-id="0ee19-123">또한 Ctrl+Alt+A를 눌러 언제든지 작업 모니터를 열 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ee19-123">You can also open Activity Monitor at any time by pressing CTRL+ALT A.</span></span>  
  
#### <a name="to-open-activity-monitor-in-object-explorer"></a><span data-ttu-id="0ee19-124">개체 탐색기에서 작업 모니터를 열려면</span><span class="sxs-lookup"><span data-stu-id="0ee19-124">To open Activity Monitor in Object Explorer</span></span>  
  
-   <span data-ttu-id="0ee19-125">개체 탐색기에서 인스턴스 이름을 마우스 오른쪽 단추로 클릭 한 다음 **작업 모니터**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee19-125">In Object Explorer, right-click the instance name, and then select **Activity Monitor**.</span></span>  
  
#### <a name="to-open-activity-monitor-when-opening-sql-server-management-studio"></a><span data-ttu-id="0ee19-126">SQL Server Management Studio를 열 때 작업 모니터를 열려면</span><span class="sxs-lookup"><span data-stu-id="0ee19-126">To open Activity Monitor when opening SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="0ee19-127">**도구** 메뉴에서 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee19-127">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="0ee19-128">**옵션** 대화 상자에서 **환경**을 확장한 다음 **일반**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee19-128">In the **Options** dialog box, expand **Environment**, and then select **General**.</span></span>  
  
3.  <span data-ttu-id="0ee19-129">**시작 시** 상자에서 **개체 탐색기 및 작업 모니터 열기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee19-129">In the **At startup** box, select **Open Object Explorer and Activity Monitor**.</span></span>  
  
4.  <span data-ttu-id="0ee19-130">변경 내용을 적용하려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 닫은 다음 다시 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0ee19-130">To activate the changes, close and reopen [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
###  <a name="to-set-the-activity-monitor-refresh-interval"></a><a name="Refresh"></a><span data-ttu-id="0ee19-131">작업 모니터 새로 고침 간격을 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="0ee19-131">To Set the Activity Monitor Refresh Interval</span></span>  
  
-   <span data-ttu-id="0ee19-132">작업 모니터를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0ee19-132">Open the Activity Monitor.</span></span>  
  
-   <span data-ttu-id="0ee19-133">**개요**를 마우스 오른쪽 단추로 클릭하고 **새로 고침 간격**을 선택한 다음 작업 모니터가 새 인스턴스 정보를 가져와야 하는 간격을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee19-133">Right-click **Overview**, select **Refresh Interval**, and then select the interval in which Activity Monitor should obtain new instance information.</span></span>  
  
  
