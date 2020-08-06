---
title: 데이터베이스 속성(트랜잭션 로그 전달 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.logshipping.f1
ms.assetid: 72c4e539-fe11-4d57-b977-65b418d5916f
author: stevestein
ms.author: sstein
ms.openlocfilehash: dd36b3bc56bcd48c53871c9bc1e334d72c80ac78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742227"
---
# <a name="database-properties-transaction-log-shipping-page"></a><span data-ttu-id="f5195-102">데이터베이스 속성(트랜잭션 로그 전달 페이지)</span><span class="sxs-lookup"><span data-stu-id="f5195-102">Database Properties (Transaction Log Shipping Page)</span></span>
  <span data-ttu-id="f5195-103">이 페이지를 사용하여 데이터베이스의 로그 전달 속성을 구성하고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5195-103">Use this page to configure and modify the properties of log shipping for a database.</span></span>  
  
 <span data-ttu-id="f5195-104">로그 전달 개념에 대한 설명은 [로그 전달 정보&#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f5195-104">For an explanation of log shipping concepts, see [About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="f5195-105">옵션</span><span class="sxs-lookup"><span data-stu-id="f5195-105">Options</span></span>  
 <span data-ttu-id="f5195-106">**이 데이터베이스를 로그 전달 구성의 주 데이터베이스로 사용**</span><span class="sxs-lookup"><span data-stu-id="f5195-106">**Enable this as a primary database in a log shipping configuration**</span></span>  
 <span data-ttu-id="f5195-107">이 데이터베이스를 로그 전달 주 데이터베이스로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f5195-107">Enables this database as a log shipping primary database.</span></span> <span data-ttu-id="f5195-108">이 옵션을 선택한 다음 페이지의 나머지 옵션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f5195-108">Select it and then configure the remaining options on this page.</span></span> <span data-ttu-id="f5195-109">이 확인란의 선택을 취소하면 이 데이터베이스의 로그 전달 구성이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5195-109">If you clear this check box, the log shipping configuration will be dropped for this database.</span></span>  
  
 <span data-ttu-id="f5195-110">**백업 설정**</span><span class="sxs-lookup"><span data-stu-id="f5195-110">**Backup Settings**</span></span>  
 <span data-ttu-id="f5195-111">백업 일정, 위치, 경고 및 보관 매개 변수를 구성하려면 **백업 설정** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f5195-111">Click **Backup Settings** to configure backup schedule, location, alert, and archiving parameters.</span></span>  
  
 <span data-ttu-id="f5195-112">**백업 일정**</span><span class="sxs-lookup"><span data-stu-id="f5195-112">**Backup schedule**</span></span>  
 <span data-ttu-id="f5195-113">주 데이터베이스에 대해 현재 선택한 백업 일정을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f5195-113">Shows the currently selected backup schedule for the primary database.</span></span> <span data-ttu-id="f5195-114">이러한 설정을 수정하려면 **백업 설정** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f5195-114">Click **Backup Settings** to modify these settings.</span></span>  
  
 <span data-ttu-id="f5195-115">**마지막으로 백업을 만든 날짜**</span><span class="sxs-lookup"><span data-stu-id="f5195-115">**Last backup created**</span></span>  
 <span data-ttu-id="f5195-116">주 데이터베이스에서 마지막으로 수행된 트랜잭션 로그 백업의 시간과 날짜를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f5195-116">Indicates the time and date of the last transaction log backup of the primary database.</span></span>  
  
 <span data-ttu-id="f5195-117">**보조 서버 인스턴스 및 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="f5195-117">**Secondary server instances and databases**</span></span>  
 <span data-ttu-id="f5195-118">이 주 데이터베이스에 대해 현재 구성된 보조 서버와 데이터베이스를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="f5195-118">Lists the currently configured secondary servers and databases for this primary database.</span></span> <span data-ttu-id="f5195-119">해당 보조 데이터베이스와 연결된 매개 변수를 수정하려면 데이터베이스를 강조 표시한 다음 **...** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f5195-119">Highlight a database, and then click **...** to modify the parameters associated with that secondary database.</span></span>  
  
 <span data-ttu-id="f5195-120">**추가**</span><span class="sxs-lookup"><span data-stu-id="f5195-120">**Add**</span></span>  
 <span data-ttu-id="f5195-121">이 주 데이터베이스의 로그 전달 구성에 보조 데이터베이스를 추가하려면 **추가** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f5195-121">Click **Add** to add a secondary database to the log shipping configuration for this primary database.</span></span>  
  
 <span data-ttu-id="f5195-122">**제거**</span><span class="sxs-lookup"><span data-stu-id="f5195-122">**Remove**</span></span>  
 <span data-ttu-id="f5195-123">이 로그 전달 구성에서 선택한 데이터베이스를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="f5195-123">Removes a selected database from this log shipping configuration.</span></span> <span data-ttu-id="f5195-124">먼저 데이터베이스를 선택한 다음 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f5195-124">Select the database first and then click **Remove**.</span></span>  
  
 <span data-ttu-id="f5195-125">**모니터 서버 인스턴스 사용**</span><span class="sxs-lookup"><span data-stu-id="f5195-125">**Use a monitor server instance**</span></span>  
 <span data-ttu-id="f5195-126">이 로그 전달 구성에 대한 모니터 서버 인스턴스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f5195-126">Sets up a monitor server instance for this log shipping configuration.</span></span> <span data-ttu-id="f5195-127">모니터 서버 인스턴스를 지정하려면 **모니터 서버 인스턴스 사용** 확인란을 선택한 다음 **설정** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f5195-127">Select the **Use a monitor server instance** check box and then click **Settings** to specify the monitor server instance.</span></span>  
  
 <span data-ttu-id="f5195-128">**모니터 서버 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="f5195-128">**Monitor server instance**</span></span>  
 <span data-ttu-id="f5195-129">이 로그 전달 구성에 대해 현재 구성된 모니터 서버 인스턴스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f5195-129">Indicates the currently configured monitor server instance for this log shipping configuration.</span></span>  
  
 <span data-ttu-id="f5195-130">**설정**</span><span class="sxs-lookup"><span data-stu-id="f5195-130">**Settings**</span></span>  
 <span data-ttu-id="f5195-131">로그 전달 구성에 대한 모니터 서버 인스턴스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f5195-131">Configures the monitor server instance for a log shipping configuration.</span></span> <span data-ttu-id="f5195-132">이 모니터 서버 인스턴스를 구성하려면 **설정** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f5195-132">Click **Settings** to configure this monitor server instance.</span></span>  
  
 <span data-ttu-id="f5195-133">**구성 스크립팅**</span><span class="sxs-lookup"><span data-stu-id="f5195-133">**Script Configuration**</span></span>  
 <span data-ttu-id="f5195-134">선택한 매개 변수로 로그 전달을 구성하기 위한 스크립트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f5195-134">Generates a script for configuring log shipping with the parameters you have selected.</span></span> <span data-ttu-id="f5195-135">**구성 스크립팅**을 클릭한 다음 스크립트의 출력 대상을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f5195-135">Click **Script Configuration**, and then choose an output destination for the script.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f5195-136">보조 데이터베이스에 대한 설정을 스크립팅하기 전에 **보조 데이터베이스 설정** 대화 상자를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5195-136">Before scripting settings for a secondary database, you must invoke the **Secondary Database Settings** dialog box.</span></span> <span data-ttu-id="f5195-137">이 대화 상자를 호출하면 보조 서버에 연결되며 스크립트 생성에 필요한 보조 데이터베이스의 현재 설정이 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5195-137">Invoking this dialog box connects you to the secondary server and retrieves the current settings of the secondary database that are needed to generate the script.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5195-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f5195-138">See Also</span></span>  
 <span data-ttu-id="f5195-139">[로그 전달 저장 프로시저&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/log-shipping-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f5195-139">[Log Shipping Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/log-shipping-stored-procedures-transact-sql) </span></span>  
 [<span data-ttu-id="f5195-140">로그 전달 테이블&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f5195-140">Log Shipping Tables &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/log-shipping-tables-transact-sql)  
  
  
