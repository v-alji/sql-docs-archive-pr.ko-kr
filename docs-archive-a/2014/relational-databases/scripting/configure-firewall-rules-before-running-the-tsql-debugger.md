---
title: Transact-SQL 디버거 구성
ms.custom: seo-lt-2019
ms.date: 10/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- vs.debug.error.sqlde_register_failed
- vs.debug.error.sqlde_accessdenied
- vs.debug.error.sqlde_firewall.remotemachines
helpviewer_keywords:
- Transact-SQL debugger, remote connections
- Windows Firewall [Database Engine], Transact-SQL debugger
- Transact-SQL debugger, Windows Firewall
- Transact-SQL debugger, configuring
- ports [SQL Server], Transact-SQL debugger
- TCP/IP [SQL Server], port numbers
ms.assetid: f50e0b0d-eaf0-4f4a-be83-96f5be63e7ea
author: rothja
ms.author: jroth
ms.openlocfilehash: a320e77e86c933a33d96d708580d5050b0c06de2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653808"
---
# <a name="configure-the-transact-sql-debugger"></a><span data-ttu-id="e33d6-102">Transact-SQL 디버거 구성</span><span class="sxs-lookup"><span data-stu-id="e33d6-102">Configure the Transact-SQL Debugger</span></span>
  <span data-ttu-id="e33d6-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리 편집기와 다른 컴퓨터에서 실행 중인 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결된 경우 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 디버깅을 사용하도록 Windows 방화벽 규칙을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-103">Windows Firewall rules must be configured to enable [!INCLUDE[tsql](../../includes/tsql-md.md)] debugging when connected to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that is running on a different computer than the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span>  
  
## <a name="configuring-the-transact-sql-debugger"></a><span data-ttu-id="e33d6-104">Transact-SQL 디버거 구성</span><span class="sxs-lookup"><span data-stu-id="e33d6-104">Configuring the Transact-SQL Debugger</span></span>  
 <span data-ttu-id="e33d6-105">[!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거는 서버 쪽 구성 요소와 클라이언트 쪽 구성 요소를 모두 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-105">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger includes both server-side and client-side components.</span></span> <span data-ttu-id="e33d6-106">서버 쪽 디버거 구성 요소는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP2(서비스 팩 2) 이상의 각 데이터베이스 엔진 인스턴스와 함께 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-106">The server-side debugger components are installed with each instance of the Database Engine from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 (SP2) or later.</span></span> <span data-ttu-id="e33d6-107">클라이언트 쪽 디버거 구성 요소는 다음과 같은 경우에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-107">The client-side debugger components are included:</span></span>  
  
-   <span data-ttu-id="e33d6-108">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상에서 클라이언트 쪽 도구를 설치할 때</span><span class="sxs-lookup"><span data-stu-id="e33d6-108">When you install the client-side tools from [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later.</span></span>  
  
-   <span data-ttu-id="e33d6-109">Microsoft Visual Studio 2010 이상을 설치할 때</span><span class="sxs-lookup"><span data-stu-id="e33d6-109">When you install Microsoft Visual Studio 2010 or later.</span></span>  
  
-   <span data-ttu-id="e33d6-110">웹 다운로드에서 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 를 설치할 때</span><span class="sxs-lookup"><span data-stu-id="e33d6-110">When you install [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] from the web download.</span></span>  
  
 <span data-ttu-id="e33d6-111">[!INCLUDE[tsql](../../includes/tsql-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 가 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 인스턴스와 같은 컴퓨터에서 실행되는 경우 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]디버거를 실행하기 위한 구성 요구 사항이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-111">There are no configuration requirements to run the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger when [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] is running on the same computer as the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="e33d6-112">그러나 [!INCLUDE[tsql](../../includes/tsql-md.md)] 의 원격 인스턴스에 연결된 경우 [!INCLUDE[ssDE](../../includes/ssde-md.md)]디버거를 실행하려면 두 컴퓨터 모두에서 Windows 방화벽의 프로그램 및 포트 규칙을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-112">However, to run the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger when connected to a remote instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], program and port rules in the Windows Firewall must be enabled on both computers.</span></span> <span data-ttu-id="e33d6-113">이러한 규칙은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 프로그램에서 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-113">These rules may be created by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup.</span></span> <span data-ttu-id="e33d6-114">원격 디버거 세션을 열려고 하는 동안 오류가 발생하면 다음 방화벽 규칙이 컴퓨터에 정의되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-114">If you get errors attempting to open a remote debugging session, ensure the following firewall rules are defined on your computer.</span></span>  
  
 <span data-ttu-id="e33d6-115">**고급 보안이 포함된 Windows 방화벽** 애플리케이션을 사용하여 방화벽 규칙을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-115">Use the **Windows Firewall with Advanced Security** application to manage the firewall rules.</span></span> <span data-ttu-id="e33d6-116">[!INCLUDE[win7](../../includes/win7-md.md)] 및 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]에서 **제어판**, **Windows 방화벽**을 차례로 열고 **고급 설정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-116">In both [!INCLUDE[win7](../../includes/win7-md.md)] and [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)], open **Control Panel**, open **Windows Firewall**, and select **Advanced settings**.</span></span> <span data-ttu-id="e33d6-117">[!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 에서는 **서비스 관리자**를 열고 왼쪽 창에서 **구성** 을 확장한 다음 **고급 보안이 포함된 Windows 방화벽**을 확장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-117">In [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] you can also open **Service Manager**, expand **Configuration** in the left pane, and expand **Windows Firewall with Advanced Security**.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="e33d6-118">Windows 방화벽의 규칙을 사용하도록 설정하면 방화벽에 의해 차단되도록 설계된 컴퓨터가 보안 위협에 노출될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-118">Enabling rules in the Windows Firewall may expose your computer to security threats that the firewall is designed to block.</span></span> <span data-ttu-id="e33d6-119">원격 디버깅에 대한 규칙을 사용하도록 설정하면 이 항목에 나열된 포트와 프로그램이 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-119">Enabling rules for remote debugging unblocks the ports and programs listed in this topic.</span></span>  
  
## <a name="firewall-rules-on-the-server"></a><span data-ttu-id="e33d6-120">서버의 방화벽 규칙</span><span class="sxs-lookup"><span data-stu-id="e33d6-120">Firewall Rules on the Server</span></span>  
 <span data-ttu-id="e33d6-121">[!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스를 실행하는 컴퓨터에서 **고급 보안이 포함된 Windows 방화벽** 을 사용하여 다음 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-121">On the computer that is running the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], use **Windows Firewall with Advanced Security** to specify the following information:</span></span>  
  
-   <span data-ttu-id="e33d6-122">sqlservr.exe에 대한 인바운드 프로그램 규칙을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-122">Add an inbound program rule for sqlservr.exe.</span></span> <span data-ttu-id="e33d6-123">원격 디버깅 세션을 지원해야 하는 인스턴스당 하나의 규칙이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-123">You must have a rule for each instance that needs to support remote debugging sessions.</span></span>  
  
    1.  <span data-ttu-id="e33d6-124">**고급 보안이 포함된 Windows 방화벽**의 왼쪽 창에서 **인바운드 규칙**을 마우스 오른쪽 단추로 클릭한 다음 작업 창에서 **새 규칙** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-124">In **Windows Firewall with Advanced Security**, in the left pane, right-click **Inbound Rules**, and then select **New Rule** in the action pane.</span></span>  
  
    2.  <span data-ttu-id="e33d6-125">**규칙 유형** 대화 상자에서 **프로그램**을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-125">In the **Rule Type** dialog, select **Program**, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="e33d6-126">**프로그램** 대화 상자에서 **다음 프로그램 경로:** 를 선택하고 이 인스턴스에 대한 sqlservr.exe의 전체 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-126">In the **Program** dialog, select **This program path:** and enter the full path to sqlservr.exe for this instance.</span></span> <span data-ttu-id="e33d6-127">기본적으로 sqlservr.exe는 C:\Program Files\Microsoft SQL Server\MSSQL12.에 설치 됩니다. *Instancename*\MSSQL\Binn. 여기서 *instancename* 은 기본 인스턴스의 경우 MSSQLSERVER이 고 명명 된 인스턴스의 경우 인스턴스 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-127">By default, sqlservr.exe is installed in C:\Program Files\Microsoft SQL Server\MSSQL12.*InstanceName*\MSSQL\Binn, where *InstanceName* is MSSQLSERVER for the default instance, and the instance name for any named instance.</span></span>  
  
    4.  <span data-ttu-id="e33d6-128">**동작** 대화 상자에서 **연결 허용**을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-128">In the **Action** dialog, select **Allow the connection**, and click **Next**.</span></span>  
  
    5.  <span data-ttu-id="e33d6-129">**프로필** 대화 상자에서 해당 인스턴스와 함께 디버깅 세션을 열 때의 컴퓨터 연결 환경을 설명하는 프로필을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-129">In the **Profile** dialog, select any profiles that describe the computer connection environment when you want to open a debugging session with the instance, and click **Next**.</span></span>  
  
    6.  <span data-ttu-id="e33d6-130">**이름** 대화 상자에 이 규칙의 이름 및 설명을 입력한 다음 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-130">In the **Name** dialog, type a name and description for this rule and click **Finish**.</span></span>  
  
    7.  <span data-ttu-id="e33d6-131">**인바운드 규칙** 목록에서 방금 만든 규칙을 마우스 오른쪽 단추로 클릭한 다음 동작 창에서 **속성** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-131">In the **Inbound Rules** list, right click the rule you created, and then select **Properties** in the action pane.</span></span>  
  
    8.  <span data-ttu-id="e33d6-132">**프로토콜 및 포트** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-132">Select the **Protocols and Ports** tab.</span></span>  
  
    9. <span data-ttu-id="e33d6-133">**프로토콜 종류:** 상자에서는 **TCP** 를 선택하고 **로컬 포트:** 상자에서는 **RPC 동적 포트** 를 선택한 후에 **적용**, **확인**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-133">Select **TCP** in the **Protocol type:** box, select **RPC Dynamic Ports** in the **Local port:** box, click **Apply**, and then click **OK**.</span></span>  
  
-   <span data-ttu-id="e33d6-134">svchost.exe에 대한 인바운드 프로그램을 추가하여 원격 디버거 세션에서 DCOM 통신을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-134">Add an inbound program rule for svchost.exe to enable DCOM communications from remote debugger sessions.</span></span>  
  
    1.  <span data-ttu-id="e33d6-135">**고급 보안이 포함된 Windows 방화벽**의 왼쪽 창에서 **인바운드 규칙**을 마우스 오른쪽 단추로 클릭한 다음 작업 창에서 **새 규칙** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-135">In **Windows Firewall with Advanced Security**, in the left pane, right-click **Inbound Rules**, and then select **New Rule** in the action pane.</span></span>  
  
    2.  <span data-ttu-id="e33d6-136">**규칙 유형** 대화 상자에서 **프로그램**을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-136">In the **Rule Type** dialog, select **Program**, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="e33d6-137">**프로그램** 대화 상자에서 **다음 프로그램 경로:** 를 선택하고 svchost.exe의 전체 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-137">In the **Program** dialog, select **This program path:** and enter the full path to svchost.exe.</span></span> <span data-ttu-id="e33d6-138">기본적으로 svchost.exe는 %systemroot%\System32\svchost.exe에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-138">By default, svchost.exe is installed in %systemroot%\System32\svchost.exe.</span></span>  
  
    4.  <span data-ttu-id="e33d6-139">**동작** 대화 상자에서 **연결 허용**을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-139">In the **Action** dialog, select **Allow the connection**, and click **Next**.</span></span>  
  
    5.  <span data-ttu-id="e33d6-140">**프로필** 대화 상자에서 해당 인스턴스와 함께 디버깅 세션을 열 때의 컴퓨터 연결 환경을 설명하는 프로필을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-140">In the **Profile** dialog, select any profiles that describe the computer connection environment when you want to open a debugging session with the instance, and click **Next**.</span></span>  
  
    6.  <span data-ttu-id="e33d6-141">**이름** 대화 상자에 이 규칙의 이름 및 설명을 입력한 다음 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-141">In the **Name** dialog, type a name and description for this rule and click **Finish**.</span></span>  
  
    7.  <span data-ttu-id="e33d6-142">**인바운드 규칙** 목록에서 방금 만든 규칙을 마우스 오른쪽 단추로 클릭한 다음 동작 창에서 **속성** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-142">In the **Inbound Rules** list, right click the rule you created, and then select **Properties** in the action pane.</span></span>  
  
    8.  <span data-ttu-id="e33d6-143">**프로토콜 및 포트** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-143">Select the **Protocols and Ports** tab.</span></span>  
  
    9. <span data-ttu-id="e33d6-144">**프로토콜 종류:** 상자에서는 **TCP** 를 선택하고 **로컬 포트:** 상자에서는 **RPC 엔드포인트 매퍼** 를 선택한 후에 **적용**, **확인**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-144">Select **TCP** in the **Protocol type:** box, select **RPC Endpoint Mapper** in the **Local port:** box, click **Apply**, and then click **OK**.</span></span>  
  
-   <span data-ttu-id="e33d6-145">도메인 정책에 따라 IPSec을 통해 네트워크 통신을 수행해야 하는 경우 UDP 포트 4500 및 UDP 포트 500을 여는 인바운드 규칙도 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-145">If the domain policy requires network communications to be done through IPsec, you must also add inbound rules opening UDP port 4500 and UDP port 500.</span></span>  
  
## <a name="firewall-rules-on-the-client"></a><span data-ttu-id="e33d6-146">클라이언트의 방화벽 규칙</span><span class="sxs-lookup"><span data-stu-id="e33d6-146">Firewall Rules on the Client</span></span>  
 <span data-ttu-id="e33d6-147">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기를 실행하는 컴퓨터에서는 SQL Server 설치 프로그램이나 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 설치 프로그램이 원격 디버깅을 허용하도록 Windows 방화벽을 구성했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-147">On the computer that is running the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor, the SQL Server setup or [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] setup may have configured the Windows Firewall to allow remote debugging.</span></span>  
  
 <span data-ttu-id="e33d6-148">원격 디버깅 세션을 열려고 하는 동안 오류가 발생하면 다음과 같이 **고급 보안이 포함된 Windows 방화벽** 을 사용하여 방화벽 규칙을 구성함으로써 수동으로 프로그램 및 포트 예외를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-148">If you get errors attempting to open a remote debugging session, you can manually configure the program and port exceptions by using **Windows Firewall with Advanced Security** to configure firewall rules:</span></span>  
  
-   <span data-ttu-id="e33d6-149">다음과 같이 svchost에 대한 프로그램 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-149">Add a program entry for svchost:</span></span>  
  
    1.  <span data-ttu-id="e33d6-150">**고급 보안이 포함된 Windows 방화벽**의 왼쪽 창에서 **인바운드 규칙**을 마우스 오른쪽 단추로 클릭한 다음 작업 창에서 **새 규칙** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-150">In **Windows Firewall with Advanced Security**, in the left pane, right-click **Inbound Rules**, and then select **New Rule** in the action pane.</span></span>  
  
    2.  <span data-ttu-id="e33d6-151">**규칙 유형** 대화 상자에서 **프로그램**을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-151">In the **Rule Type** dialog, select **Program**, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="e33d6-152">**프로그램** 대화 상자에서 **다음 프로그램 경로:** 를 선택하고 svchost.exe의 전체 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-152">In the **Program** dialog, select **This program path:** and enter the full path to svchost.exe.</span></span> <span data-ttu-id="e33d6-153">기본적으로 svchost.exe는 %systemroot%\System32\svchost.exe에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-153">By default, svchost.exe is installed in %systemroot%\System32\svchost.exe.</span></span>  
  
    4.  <span data-ttu-id="e33d6-154">**동작** 대화 상자에서 **연결 허용**을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-154">In the **Action** dialog, select **Allow the connection**, and click **Next**.</span></span>  
  
    5.  <span data-ttu-id="e33d6-155">**프로필** 대화 상자에서 해당 인스턴스와 함께 디버깅 세션을 열 때의 컴퓨터 연결 환경을 설명하는 프로필을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-155">In the **Profile** dialog, select any profiles that describe the computer connection environment when you want to open a debugging session with the instance, and click **Next**.</span></span>  
  
    6.  <span data-ttu-id="e33d6-156">**이름** 대화 상자에 이 규칙의 이름 및 설명을 입력한 다음 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-156">In the **Name** dialog, type a name and description for this rule and click **Finish**.</span></span>  
  
    7.  <span data-ttu-id="e33d6-157">**인바운드 규칙** 목록에서 방금 만든 규칙을 마우스 오른쪽 단추로 클릭한 다음 동작 창에서 **속성** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-157">In the **Inbound Rules** list, right click the rule you created, and then select **Properties** in the action pane.</span></span>  
  
    8.  <span data-ttu-id="e33d6-158">**프로토콜 및 포트** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-158">Select the **Protocols and Ports** tab.</span></span>  
  
    9. <span data-ttu-id="e33d6-159">**프로토콜 종류:** 상자에서는 **TCP** 를 선택하고 **로컬 포트:** 상자에서는 **RPC 엔드포인트 매퍼** 를 선택한 후에 **적용**, **확인**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-159">Select **TCP** in the **Protocol type:** box, select **RPC Endpoint Mapper** in the **Local port:** box, click **Apply**, and then click **OK**.</span></span>  
  
-   <span data-ttu-id="e33d6-160">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기를 호스팅하는 애플리케이션에 대한 프로그램 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-160">Add a program entry for the application hosting the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span> <span data-ttu-id="e33d6-161">같은 컴퓨터에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 및 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 의 원격 디버깅 세션을 둘 다 열어야 하는 경우 다음과 같이 두 세션 모두에 대한 프로그램 규칙을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-161">If you need to open remote debugging sessions from both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] on the same computer, you must add a program rule for both:</span></span>  
  
    1.  <span data-ttu-id="e33d6-162">**고급 보안이 포함된 Windows 방화벽**의 왼쪽 창에서 **인바운드 규칙**을 마우스 오른쪽 단추로 클릭한 다음 작업 창에서 **새 규칙** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-162">In **Windows Firewall with Advanced Security**, in the left pane, right-click **Inbound Rules**, and then select **New Rule** in the action pane.</span></span>  
  
    2.  <span data-ttu-id="e33d6-163">**규칙 유형** 대화 상자에서 **프로그램**을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-163">In the **Rule Type** dialog, select **Program**, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="e33d6-164">**프로그램** 대화 상자에서 **다음 프로그램 경로:** 를 선택하고 다음 세 값 중 하나를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-164">In the **Program** dialog, select **This program path:** and enter one of these three values.</span></span>  
  
        -   <span data-ttu-id="e33d6-165">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 경우 ssms.exe에 대한 전체 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-165">For [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], enter the full path to ssms.exe.</span></span> <span data-ttu-id="e33d6-166">기본적으로 ssms.exe는 C:\Program Files (x86)\Microsoft SQL Server\120\Tools\Binn\Management Studio에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-166">By default, ssms.exe is installed in C:\Program Files (x86)\Microsoft SQL Server\120\Tools\Binn\Management Studio.</span></span>  
  
        -   <span data-ttu-id="e33d6-167">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 의 경우 devenv.exe의 전체 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-167">For [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] enter the full path to devenv.exe:</span></span>  
  
            1.  <span data-ttu-id="e33d6-168">기본적으로 Visual Studio 2010용 devenv.exe는 C:\Program Files (x86)\Microsoft Visual Studio 10.0\Common7\IDE에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-168">By default, the devenv.exe for Visual Studio 2010 is in C:\Program Files (x86)\Microsoft Visual Studio 10.0\Common7\IDE.</span></span>  
  
            2.  <span data-ttu-id="e33d6-169">기본적으로 Visual Studio 2012용 devenv.exe는 C:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-169">By default, the devenv.exe for Visual Studio 2012 is in C:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE</span></span>  
  
            3.  <span data-ttu-id="e33d6-170">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 시작하기 위해 사용하는 바로 가기에서 ssms.exe에 대한 경로를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-170">You can find the path to ssms.exe from the shortcut you use to launch [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="e33d6-171">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]를 시작하기 위해 사용하는 바로 가기에서 devenv.exe에 대한 경로를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-171">You can find the path to devenv.exe from the shortcut you use to launch [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="e33d6-172">바로 가기를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-172">Right click the shortcut and select **Properties**.</span></span> <span data-ttu-id="e33d6-173">실행 파일과 경로가 **대상** 상자에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-173">The executable and path are listed in the **Target** box.</span></span>  
  
    4.  <span data-ttu-id="e33d6-174">**동작** 대화 상자에서 **연결 허용**을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-174">In the **Action** dialog, select **Allow the connection**, and click **Next**.</span></span>  
  
    5.  <span data-ttu-id="e33d6-175">**프로필** 대화 상자에서 해당 인스턴스와 함께 디버깅 세션을 열 때의 컴퓨터 연결 환경을 설명하는 프로필을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-175">In the **Profile** dialog, select any profiles that describe the computer connection environment when you want to open a debugging session with the instance, and click **Next**.</span></span>  
  
    6.  <span data-ttu-id="e33d6-176">**이름** 대화 상자에 이 규칙의 이름 및 설명을 입력한 다음 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-176">In the **Name** dialog, type a name and description for this rule and click **Finish**.</span></span>  
  
    7.  <span data-ttu-id="e33d6-177">**인바운드 규칙** 목록에서 방금 만든 규칙을 마우스 오른쪽 단추로 클릭한 다음 동작 창에서 **속성** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-177">In the **Inbound Rules** list, right click the rule you created, and then select **Properties** in the action pane.</span></span>  
  
    8.  <span data-ttu-id="e33d6-178">**프로토콜 및 포트** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-178">Select the **Protocols and Ports** tab.</span></span>  
  
    9. <span data-ttu-id="e33d6-179">**프로토콜 종류:** 상자에서는 **TCP** 를 선택하고 **로컬 포트:** 상자에서는 **RPC 동적 포트** 를 선택한 후에 **적용**, **확인**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-179">Select **TCP** in the **Protocol type:** box, select **RPC Dynamic Ports** in the **Local port:** box, click **Apply**, and then click **OK**.</span></span>  
  
## <a name="requirements-for-starting-the-debugger"></a><span data-ttu-id="e33d6-180">디버거 시작을 위한 요구 사항</span><span class="sxs-lookup"><span data-stu-id="e33d6-180">Requirements for Starting the Debugger</span></span>  
 <span data-ttu-id="e33d6-181">다음 요구 사항을 충족해야 [!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-181">All attempts to start the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger must also meet the following requirements:</span></span>  
  
* [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="e33d6-182">또는 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 는 sysadmin 고정 서버 역할의 멤버인 Windows 계정으로 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-182">or [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] must be running under a Windows account that is a member of the sysadmin fixed server roll.</span></span>  
  
* <span data-ttu-id="e33d6-183">sysadmin 고정 서버 역할의 멤버인 Windows 인증 또는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인증 로그인을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 쿼리 편집기 창을 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-183">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window must be connected by using either a Windows Authentication or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication login that is a member of the sysadmin fixed server role.</span></span>  
  
* <span data-ttu-id="e33d6-184">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기 창을 [!INCLUDE[ssDE](../../includes/ssde-md.md)] SP2(서비스 팩 2) 이상의 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 인스턴스에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-184">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window must be connected to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 (SP2) or later.</span></span> <span data-ttu-id="e33d6-185">쿼리 편집기 창이 단일 사용자 모드에 있는 인스턴스에 연결되어 있는 경우에는 디버거를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-185">You cannot run the debugger when the Query Editor window is connected to an instance that is in single-user mode.</span></span>

* <span data-ttu-id="e33d6-186">서버는 RPC를 통해 클라이언트와 다시 통신해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-186">The server needs to communicate back to the client via RPC.</span></span> <span data-ttu-id="e33d6-187">SQL Server 서비스를 실행 하는 계정에는 클라이언트에 대 한 인증 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e33d6-187">The account under which SQL Server service is running should have authenticate permissions to the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e33d6-188">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e33d6-188">See Also</span></span>  
 <span data-ttu-id="e33d6-189">[Transact-sql 디버거](transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="e33d6-189">[Transact-SQL Debugger](transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="e33d6-190">[Transact-sql 디버거 실행](run-the-transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="e33d6-190">[Run the Transact-SQL Debugger](run-the-transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="e33d6-191">[Transact-sql 코드 단계별 실행](step-through-transact-sql-code.md) </span><span class="sxs-lookup"><span data-stu-id="e33d6-191">[Step Through Transact-SQL Code](step-through-transact-sql-code.md) </span></span>  
 <span data-ttu-id="e33d6-192">[Transact-sql 디버거 정보](transact-sql-debugger-information.md) </span><span class="sxs-lookup"><span data-stu-id="e33d6-192">[Transact-SQL Debugger Information](transact-sql-debugger-information.md) </span></span>  
 [<span data-ttu-id="e33d6-193">데이터베이스 엔진 쿼리 편집기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="e33d6-193">Database Engine Query Editor &#40;SQL Server Management Studio&#41;</span></span>](database-engine-query-editor-sql-server-management-studio.md)  
  
  
