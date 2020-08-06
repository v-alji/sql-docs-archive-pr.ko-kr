---
title: 미러된 데이터베이스 등록 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dbmmonitor.registermirroreddb.f1
ms.assetid: 6acd02b9-2311-49b0-a5f8-3852beecb4b0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 24732f82c971959ed202358613ef98c5ccc714d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733084"
---
# <a name="register-mirrored-database"></a><span data-ttu-id="14656-102">미러된 데이터베이스 등록</span><span class="sxs-lookup"><span data-stu-id="14656-102">Register Mirrored Database</span></span>
  <span data-ttu-id="14656-103">이 대화 상자를 사용하면 데이터베이스 미러링 모니터에 데이터베이스를 추가하여 지정된 서버 인스턴스에서 하나 이상의 미러된 데이터베이스를 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14656-103">Use this dialog box to register one or more mirrored databases on a given server instance by adding the database or databases to the Database Mirroring Monitor.</span></span> <span data-ttu-id="14656-104">데이터베이스가 추가되면 데이터베이스 미러링 모니터는 데이터베이스, 해당 파트너, 파트너에 연결되는 방법 등에 대한 정보를 로컬로 캐시합니다.</span><span class="sxs-lookup"><span data-stu-id="14656-104">When a database is added, Database Mirroring Monitor locally caches information about the database, its partners, and how to connect to the partners.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="14656-105">주 서버 인스턴스에서 **sysadmin** 고정 서버 역할의 멤버이지만 미러 서버 인스턴스에서는 이 역할의 멤버가 아닌 경우 주 서버 인스턴스에 대한 상태만 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14656-105">If you are a member of the **sysadmin** fixed server role on the principal server instance but not on the mirror server instance, you can only see status on the principal server instance.</span></span>  
  
 <span data-ttu-id="14656-106">**SQL Server Management Studio를 사용하여 데이터베이스 미러링을 모니터링하려면**</span><span class="sxs-lookup"><span data-stu-id="14656-106">**To use SQL Server Management Studio to monitor database mirroring**</span></span>  
  
-   [<span data-ttu-id="14656-107">데이터베이스 미러링 모니터 시작&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="14656-107">Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="options"></a><span data-ttu-id="14656-108">옵션</span><span class="sxs-lookup"><span data-stu-id="14656-108">Options</span></span>  
 <span data-ttu-id="14656-109">**서버 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="14656-109">**Server instance**</span></span>  
 <span data-ttu-id="14656-110">데이터베이스 미러링 모니터에 이미 저장된 연결이 있는 서버 인스턴스가 포함된 목록에서 서버 인스턴스를 선택하거나 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="14656-110">Select a server instance from the list, which contains server instances to which Database Mirroring Monitor already has a connection stored, or click **Connect**.</span></span> <span data-ttu-id="14656-111">나열된 서버 인스턴스에 대해 새 자격 증명을 지정하려면 **연결** 을 클릭하고 새 자격 증명을 사용하여 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="14656-111">To specify new credentials for a listed server instance, click **Connect** and connect using the new credentials.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="14656-112">여러 서버 인스턴스에서 데이터베이스를 등록하려면 한 서버 인스턴스에 대해 원하는 데이터베이스의 검사를 완료한 후에 **적용**을 클릭하고 다른 서버 인스턴스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14656-112">To register databases on multiple server instances, after you finish checking the desired databases for one server instance, click **Apply**, and then select another server instance.</span></span>  
  
 <span data-ttu-id="14656-113">**연결**</span><span class="sxs-lookup"><span data-stu-id="14656-113">**Connect**</span></span>  
 <span data-ttu-id="14656-114">서버 인스턴스에 대한 새 자격 증명을 지정하려면 **연결** 을 클릭하고 새 자격 증명을 사용하여 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="14656-114">To specify new credentials for the server instance, click **Connect** and connect using the new credentials.</span></span> <span data-ttu-id="14656-115">서버 인스턴스에 연결되어 있는 동안 데이터베이스 미러링 모니터는 **데이터를 기다리는 중**을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="14656-115">While connecting to a server instance, Database Mirroring Monitor displays **Waiting for data**.</span></span>  
  
 <span data-ttu-id="14656-116">**미러된 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="14656-116">**Mirrored databases**</span></span>  
 <span data-ttu-id="14656-117">**미러된 데이터베이스** 표에는 서버 인스턴스의 미러된 데이터베이스가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="14656-117">The **Mirrored databases** grid lists the mirrored databases on the server instance.</span></span>  
  
 <span data-ttu-id="14656-118">표에는 다음 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14656-118">The grid contains the following columns:</span></span>  
  
|<span data-ttu-id="14656-119">열 이름</span><span class="sxs-lookup"><span data-stu-id="14656-119">Column name</span></span>|<span data-ttu-id="14656-120">Description</span><span class="sxs-lookup"><span data-stu-id="14656-120">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="14656-121">**등록**</span><span class="sxs-lookup"><span data-stu-id="14656-121">**Register**</span></span>|<span data-ttu-id="14656-122">등록할 각 데이터베이스를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="14656-122">Check each of the databases that you want to register.</span></span> <span data-ttu-id="14656-123">데이터베이스가 현재 모니터링되고 있는 경우 해당 확인란은 선택된 상태로 비활성화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14656-123">If a database is currently monitored, its check box is checked and is disabled.</span></span><br /><br /> <span data-ttu-id="14656-124">참고: 데이터베이스 등록을 취소하려면 **미러된 데이터베이스 등록** 대화 상자를 닫고 탐색 트리에서 데이터베이스를 선택하고 **동작** 메뉴에서 **등록 취소**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14656-124">Note: To unregister a database, close the **Registered Mirrored Database** dialog box, select the database in the navigation tree, and select **Unregister** from the **Action** menu.</span></span>|  
|<span data-ttu-id="14656-125">**Database**</span><span class="sxs-lookup"><span data-stu-id="14656-125">**Database**</span></span>|<span data-ttu-id="14656-126">선택한 서버 인스턴스에 있는 미러된 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="14656-126">The name of a mirrored database on the selected server instance.</span></span>|  
|<span data-ttu-id="14656-127">**현재 역할**</span><span class="sxs-lookup"><span data-stu-id="14656-127">**Current Role**</span></span>|<span data-ttu-id="14656-128">선택한 서버 인스턴스에 있는 데이터베이스의 현재 미러링 역할(주 서버 또는 미러 서버)입니다.</span><span class="sxs-lookup"><span data-stu-id="14656-128">The current mirroring role of the database, either Principal or Mirror, on the selected server instance.</span></span>|  
|<span data-ttu-id="14656-129">**파트너(연결 대상)**</span><span class="sxs-lookup"><span data-stu-id="14656-129">**Partner (Connect as)**</span></span>|<span data-ttu-id="14656-130">데이터베이스에 대한 장애 조치(Failover) 파트너의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="14656-130">The name of the failover partner for the database.</span></span> <span data-ttu-id="14656-131">**콘솔 사용자의 Windows 인증** 또는  **login '***\<login name>***'** 의 SQL Server 인증이 괄호 안에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="14656-131">Either **Windows Authentication of console user** or **SQL Server Authentication of login '***\<login name>***'** is displayed within the parentheses.</span></span> <span data-ttu-id="14656-132">이것은 인스턴스가 이전에 추가된 경우에는 현재 사용되는 인증 정보이고 인스턴스가 모니터에 추가되지 않은 경우에는 사용될 인증 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="14656-132">This is the authentication information currently used, if the instance has been added before, or that will be used, if this instance has not been added to the monitor.</span></span>|  
  
 <span data-ttu-id="14656-133">**[확인]을 클릭할 때 [서버 연결 관리] 대화 상자 표시**</span><span class="sxs-lookup"><span data-stu-id="14656-133">**Show the Manage Server Connections dialog box when I click OK.**</span></span>  
 <span data-ttu-id="14656-134">기본적으로 데이터베이스 미러링 모니터는 이전에 자격 증명이 제공되지 않은 파트너 서버 인스턴스에 대해 Windows 인증 자격 증명을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="14656-134">By default, Database Mirroring Monitor uses Windows Authentication credentials for partner server instances for which credentials have not been previously given.</span></span> <span data-ttu-id="14656-135">데이터베이스 등록을 완료할 때 하나 이상의 서버 인스턴스에 대한 자격 증명을 변경하려면 이 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="14656-135">Enable this option to change the credentials for one or more server instances when you finish registering databases.</span></span>  
  
 <span data-ttu-id="14656-136">이 옵션을 설정할 경우 **확인**을 클릭하면 **서버 연결 관리** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="14656-136">If this option is enabled, when you click **OK**, the **Manage Server Connections** dialog box opens.</span></span> <span data-ttu-id="14656-137">이 대화 상자에서 지정된 장애 조치 파트너에 연결할 때 사용할 모니터에 대한 자격 증명을 지정할 서버 인스턴스를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14656-137">There, you can choose a server instance for which you want to specify credentials for the monitor to use when connecting to a given failover partner.</span></span>  
  
 <span data-ttu-id="14656-138">파트너에 대한 자격 증명을 편집하려면 **서버 인스턴스** 표에서 항목을 찾은 다음 해당 행에서 **편집** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="14656-138">To edit the credentials for a partner, locate its entry in the **Server instances** grid, and click **Edit** on that row.</span></span> <span data-ttu-id="14656-139">이렇게 하면 자격 증명 컨트롤이 현재 캐시된 값으로 초기화된 상태에서 해당 서버 인스턴스 이름의 **서버에 연결** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="14656-139">This opens the **Connect to Server** dialog box for that server instance name, with the credential controls initialized to the current cached value.</span></span> <span data-ttu-id="14656-140">필요에 따라 자격 증명을 변경하고 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="14656-140">Change the credentials as necessary and click **Connect**.</span></span> <span data-ttu-id="14656-141">자격 증명에 충분한 권한이 있는 경우 **연결 방법** 열이 새 자격 증명으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="14656-141">If the credentials have sufficient privileges, the **Connect Using** column is updated with the new credentials.</span></span>  
  
 <span data-ttu-id="14656-142">**적용**</span><span class="sxs-lookup"><span data-stu-id="14656-142">**Apply**</span></span>  
 <span data-ttu-id="14656-143">대화 상자를 열어 둔 상태에서 선택한 데이터베이스를 등록하고 파트너 서버 인스턴스의 자격 증명을 저장하려면 이 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="14656-143">Click this button to register the selected databases (and save credentials for the partner server instances) while keeping the dialog box open.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14656-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="14656-144">See Also</span></span>  
 <span data-ttu-id="14656-145">[데이터베이스 미러링 모니터 시작&#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="14656-145">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="14656-146">[데이터베이스 미러링 모니터링&#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="14656-146">[Monitoring Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="14656-147">데이터베이스 미러링 보안 구성 마법사 시작&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="14656-147">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
  
