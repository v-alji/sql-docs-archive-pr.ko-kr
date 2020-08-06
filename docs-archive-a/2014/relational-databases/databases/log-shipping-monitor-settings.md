---
title: 로그 전달 모니터 설정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.logshipping.settings.monitor.f1
ms.assetid: 45e2ba7d-b3aa-4643-9451-bcb991572314
author: stevestein
ms.author: sstein
ms.openlocfilehash: 162fdc1b8b0ef850a7e58d1380c533426e16539c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742184"
---
# <a name="log-shipping-monitor-settings"></a><span data-ttu-id="8e3fc-102">로그 전달 모니터 설정</span><span class="sxs-lookup"><span data-stu-id="8e3fc-102">Log Shipping Monitor Settings</span></span>
  <span data-ttu-id="8e3fc-103">이 페이지를 사용하여 로그 전달 모니터 서버의 속성을 구성하고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e3fc-103">Use this page to configure and to modify the properties of the log shipping monitor server.</span></span>  
  
 <span data-ttu-id="8e3fc-104">로그 전달 개념에 대한 설명은 [로그 전달 정보&#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8e3fc-104">For an explanation of log shipping concepts, see [About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="8e3fc-105">옵션</span><span class="sxs-lookup"><span data-stu-id="8e3fc-105">Options</span></span>  
 <span data-ttu-id="8e3fc-106">**모니터 서버 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="8e3fc-106">**Monitor server instance**</span></span>  
 <span data-ttu-id="8e3fc-107">로그 전달 구성을 위한 모니터 서버로 현재 구성되어 있는 서버 인스턴스의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8e3fc-107">Displays the name of the server instance that is currently configured as the monitor server for the log shipping configuration.</span></span>  
  
 <span data-ttu-id="8e3fc-108">**연결**</span><span class="sxs-lookup"><span data-stu-id="8e3fc-108">**Connect**</span></span>  
 <span data-ttu-id="8e3fc-109">모니터 서버로 사용할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 선택하여 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8e3fc-109">Choose and connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to be used as the monitor server.</span></span> <span data-ttu-id="8e3fc-110">연결 시 사용한 계정은 보조 서버 인스턴스에서 sysadmin 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e3fc-110">The account used to connect must be a member of the sysadmin fixed server role on the secondary server instance.</span></span>  
  
 <span data-ttu-id="8e3fc-111">**작업의 프록시 계정 가장**</span><span class="sxs-lookup"><span data-stu-id="8e3fc-111">**By impersonating the proxy account of the job**</span></span>  
 <span data-ttu-id="8e3fc-112">로그 전달에서 모니터 서버 인스턴스에 연결할 때 SQL Server 에이전트 프록시 계정을 가장합니다.</span><span class="sxs-lookup"><span data-stu-id="8e3fc-112">Have log shipping impersonate the SQL Server Agent proxy account when connecting to the monitor server instance.</span></span> <span data-ttu-id="8e3fc-113">백업, 복사 및 복구 프로세스에서 모니터 서버에 연결하여 로그 전달 작업 상태를 업데이트할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e3fc-113">The backup, copy, and restore processes must be able to connect to the monitor server to update the status of log shipping operations.</span></span>  
  
 <span data-ttu-id="8e3fc-114">**다음 SQL Server 로그인 사용**</span><span class="sxs-lookup"><span data-stu-id="8e3fc-114">**Using the following SQL Server login**</span></span>  
 <span data-ttu-id="8e3fc-115">로그 전달에서 모니터 서버 인스턴스에 연결할 때 특정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e3fc-115">Allow log shipping to use a specific [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login when connecting to the monitor server instance.</span></span> <span data-ttu-id="8e3fc-116">백업, 복사 및 복구 프로세스에서 모니터 서버에 연결하여 로그 전달 작업 상태를 업데이트할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e3fc-116">The backup, copy, and restore processes must be able to connect to the monitor server to update the status of log shipping operations.</span></span> <span data-ttu-id="8e3fc-117">로그 전달에서 특정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 사용하려면 이 옵션을 선택한 다음 로그인과 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8e3fc-117">Choose this option if you want log shipping to use a specific [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and then specify the login and password.</span></span>  
  
 <span data-ttu-id="8e3fc-118">**다음 기간 이후에 기록 삭제**</span><span class="sxs-lookup"><span data-stu-id="8e3fc-118">**Delete history after**</span></span>  
 <span data-ttu-id="8e3fc-119">로그 전달 기록 정보를 삭제하기 전에 모니터 서버에서 보관하는 기간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8e3fc-119">Specify the amount of time to retain log shipping history information on the monitor server before it is deleted.</span></span>  
  
 <span data-ttu-id="8e3fc-120">**작업 이름**</span><span class="sxs-lookup"><span data-stu-id="8e3fc-120">**Job name**</span></span>  
 <span data-ttu-id="8e3fc-121">백업 또는 복원 임계값이 초과될 때 로그 전달에서 경고를 발생시키는 데 사용되는 SQL Server 에이전트 경고 작업의 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8e3fc-121">Indicates the name of the SQL Server Agent alert job used by log shipping to raise alerts when backup or restore thresholds have been exceeded.</span></span> <span data-ttu-id="8e3fc-122">처음 이 작업을 만들 때 입력란에 이름을 입력하여 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e3fc-122">When first creating this job, you can change the name by typing in the box.</span></span>  
  
 <span data-ttu-id="8e3fc-123">**일정**</span><span class="sxs-lookup"><span data-stu-id="8e3fc-123">**Schedule**</span></span>  
 <span data-ttu-id="8e3fc-124">SQL Server 에이전트 경고 작업의 현재 일정을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8e3fc-124">Indicates the current schedule of the SQL Server Agent alert job.</span></span>  
  
 <span data-ttu-id="8e3fc-125">**편집**</span><span class="sxs-lookup"><span data-stu-id="8e3fc-125">**Edit**</span></span>  
 <span data-ttu-id="8e3fc-126">SQL Server 에이전트 경고 작업 매개 변수를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="8e3fc-126">Modify the SQL Server Agent alert job parameters.</span></span>  
  
 <span data-ttu-id="8e3fc-127">**이 작업 비활성화**</span><span class="sxs-lookup"><span data-stu-id="8e3fc-127">**Disable this job**</span></span>  
 <span data-ttu-id="8e3fc-128">SQL Server 에이전트 경고 작업을 일시 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="8e3fc-128">Suspend the SQL Server Agent alert job.</span></span>  
  
  
