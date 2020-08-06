---
title: 가용성 그룹 수신기 만들기 또는 구성(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.newaglistener.general.f1
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
- Availability Groups [SQL Server], client connectivity
ms.assetid: 2bc294f6-2312-4b6b-9478-2fb8a656e645
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2c74e92286eab4bc1be8f3f538d83d86f056cf01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743451"
---
# <a name="create-or-configure-an-availability-group-listener-sql-server"></a><span data-ttu-id="26f4d-102">가용성 그룹 수신기 만들기 또는 구성(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="26f4d-102">Create or Configure an Availability Group Listener (SQL Server)</span></span>
  <span data-ttu-id="26f4d-103">이 항목에서는에서, 또는 PowerShell을 사용 하 여 AlwaysOn 가용성 그룹에 대 한 단일 *가용성 그룹 수신기* 를 만들거나 구성 하는 방법에 대해 설명 합니다 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../../includes/tsql-md.md)] [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="26f4d-103">This topic describes how to create or configure a single *availability group listener* for an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="26f4d-104">가용성 그룹에 대한 첫 번째 가용성 그룹 수신기를 만들려면 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]또는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-104">To create the first availability group listener of an availability group, we strongly recommend that you [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell.</span></span> <span data-ttu-id="26f4d-105">추가 수신기를 만들려는 경우처럼 필요한 경우를 제외하고 WSFC 클러스터에서 수신기를 직접 만들지 마세요.</span><span class="sxs-lookup"><span data-stu-id="26f4d-105">Avoid creating a listener directly in the WSFC cluster except when necessary, for example, to create an additional listener.</span></span>  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="26f4d-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="26f4d-106">Before You Begin</span></span>  
  
###  <a name="does-a-listener-exist-for-this-availability-group-already"></a><a name="DoesListenerExist"></a> <span data-ttu-id="26f4d-107">이 가용성 그룹에 대한 수신기가 이미 존재합니까?</span><span class="sxs-lookup"><span data-stu-id="26f4d-107">Does a Listener Exist for this Availability Group Already?</span></span>  
 <span data-ttu-id="26f4d-108">**가용성 그룹에 대한 수신기가 이미 존재하는지 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="26f4d-108">**To determine whether a listener already exists for the availability group**</span></span>  
  
-   [<span data-ttu-id="26f4d-109">가용성 그룹 수신기 속성 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="26f4d-109">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)  
  
> [!NOTE]  
>  <span data-ttu-id="26f4d-110">수신기가 이미 있는 상태에서 추가 수신기를 만들려면 이 항목의 뒷부분에 나오는 [가용성 그룹에 대한 추가 수신기를 만들려면(선택 사항)](#CreateAdditionalListener)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26f4d-110">If a listener already exists and you want to create an additional listener, see [To Create An Additional Listener for an Availability Group (Optional)](#CreateAdditionalListener), later in this topic.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="26f4d-111">제한 사항</span><span class="sxs-lookup"><span data-stu-id="26f4d-111">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="26f4d-112">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]를 통해 가용성 그룹당 수신기를 하나만 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-112">You can create only one listener per availability group through [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="26f4d-113">일반적으로 각 가용성 그룹에는 수신기가 하나만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-113">Typically, each availability group requires only one listener.</span></span> <span data-ttu-id="26f4d-114">그러나 고객 시나리오에 따라 하나의 가용성 그룹에 여러 개의 수신기가 필요한 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-114">However, some customer scenarios require multiple listeners for one availability group.</span></span>   <span data-ttu-id="26f4d-115">SQL Server를 통해 수신기를 만든 후 장애 조치(failover) 클러스터용 Windows PowerShell 또는 WSFC 장애 조치 클러스터 관리자를 사용하여 추가 수신기를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-115">After creating a listener through SQL Server, you can use Windows PowerShell for failover clusters or the WSFC Failover Cluster Manager to create additional listeners.</span></span> <span data-ttu-id="26f4d-116">자세한 내용은 이 항목의 뒷부분에 나오는 [가용성 그룹의 추가 수신기를 만들려면(선택 사항)](#CreateAdditionalListener)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26f4d-116">For more information, see [To Create An Additional Listener for an Availability Group (Optional)](#CreateAdditionalListener), later in this topic.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="26f4d-117">권장 사항</span><span class="sxs-lookup"><span data-stu-id="26f4d-117">Recommendations</span></span>  
 <span data-ttu-id="26f4d-118">필수는 아니지만 여러 서브넷 구성에 대해 고정 IP 주소를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-118">Using a static IP address is recommended, although not required, for multiple subnet configurations.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="26f4d-119">필수 조건</span><span class="sxs-lookup"><span data-stu-id="26f4d-119">Prerequisites</span></span>  
  
-   <span data-ttu-id="26f4d-120">주 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-120">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
-   <span data-ttu-id="26f4d-121">여러 서브넷에 대해 하나의 가용성 그룹 수신기를 설정하고 고정 IP 주소를 사용하려는 경우 수신기를 만들려는 가용성 그룹에 대해 가용성 복제본을 호스팅하는 모든 서브넷의 고정 IP 주소를 얻어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-121">If you are setting up an availability group listener across multiple subnets and plan to use static IP addresses, you need to get the static IP address of every subnet that hosts an availability replica for the availability group for which you are creating the listener.</span></span> <span data-ttu-id="26f4d-122">일반적으로 네트워크 관리자에게 고정 IP 주소를 문의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-122">Usually, you will need to ask your network administrators for the static IP addresses.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="26f4d-123">첫 번째 수신기를 만들기 전에 [AlwaysOn 클라이언트 연결&#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md)을 읽어 보세요.</span><span class="sxs-lookup"><span data-stu-id="26f4d-123">Before you create your first listener, we strongly recommend that you read [AlwaysOn Client Connectivity &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md).</span></span>  
  
###  <a name="requirements-for-the-dns-name-of-an-availability-group-listener"></a><a name="DNSnameReqs"></a> <span data-ttu-id="26f4d-124">가용성 그룹 수신기의 DNS 이름에 대한 요구 사항</span><span class="sxs-lookup"><span data-stu-id="26f4d-124">Requirements for the DNS Name of an Availability Group Listener</span></span>  
 <span data-ttu-id="26f4d-125">각 가용성 그룹 수신기에는 도메인과 NetBIOS에서 고유한 DNS 호스트 이름이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-125">Each availability group listener requires a DNS host name that is unique in the domain and in NetBIOS.</span></span> <span data-ttu-id="26f4d-126">DNS 이름은 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-126">The DNS name is a string value.</span></span> <span data-ttu-id="26f4d-127">이 이름은 순서에 관계없이 영숫자 문자, 대시(-) 및 하이픈(_)만 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-127">This name can contain only alphanumeric characters, dashes (-), and hyphens (_), in any order.</span></span> <span data-ttu-id="26f4d-128">DNS 호스트 이름은 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-128">DNS host names are case insensitive.</span></span> <span data-ttu-id="26f4d-129">최대 길이는 63자이지만 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 지정할 수 있는 최대 길이는 15자입니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-129">The maximum length is 63 characters, however, in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], the maximum length you can specify is 15 characters.</span></span>  
  
 <span data-ttu-id="26f4d-130">의미 있는 문자열을 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-130">We recommend that you specify a meaningful string.</span></span> <span data-ttu-id="26f4d-131">예를 들어, `AG1`이라는 가용성 그룹의 경우 `ag1-listener`와 같은 의미 있는 DNS 호스트 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-131">For example, for an availability group named `AG1`, a meaningful DNS host name would be `ag1-listener`.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="26f4d-132">NetBIOS는 dns_name에서 처음 15자만 인식합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-132">NetBIOS recognizes only the first 15 chars in the dns_name.</span></span> <span data-ttu-id="26f4d-133">두 WSFC 클러스터가 동일한 Active Directory에 의해 제어될 때 15자 이상의 이름과 동일한 15자 접두사를 사용하여 두 클러스터 모두에서 가용성 그룹 수신기를 만들려고 하면Virtual Network 이름 리소스를 온라인으로 전환할 수 없다는 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-133">If you have two WSFC clusters that are controlled by the same Active Directory and you try to create availability group listeners in both of clusters using names with more than 15 characters and an identical 15 character prefix, you will get an error reporting that the Virtual Network Name resource could not be brought online.</span></span> <span data-ttu-id="26f4d-134">DNS 이름의 접두사 명명 규칙에 대한 자세한 내용은 [도메인 이름 할당](https://technet.microsoft.com/library/cc731265\(WS.10\).aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26f4d-134">For information about prefix naming rules for DNS names, see [Assigning Domain Names](https://technet.microsoft.com/library/cc731265\(WS.10\).aspx).</span></span>  
  
###  <a name="windows-permissions"></a><a name="WinPermissions"></a> <span data-ttu-id="26f4d-135">Windows 사용 권한</span><span class="sxs-lookup"><span data-stu-id="26f4d-135">Windows Permissions</span></span>  
  
|<span data-ttu-id="26f4d-136">사용 권한</span><span class="sxs-lookup"><span data-stu-id="26f4d-136">Permissions</span></span>|<span data-ttu-id="26f4d-137">링크</span><span class="sxs-lookup"><span data-stu-id="26f4d-137">Link</span></span>|  
|-----------------|----------|  
|<span data-ttu-id="26f4d-138">가용성 그룹을 호스팅하는 WSFC 클러스터의 CNO(클러스터 개체 이름)에는 **컴퓨터 개체 생성** 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-138">The cluster object name (CNO) of WSFC cluster that is hosting the availability group must have **Create Computer objects** permission.</span></span><br /><br /> <span data-ttu-id="26f4d-139">Active Directory에서 기본적으로 CNO는 명시적으로 **컴퓨터 개체 생성** 권한이 없으며 10개의 VCO(가상 컴퓨터 개체)를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-139">In Active Directory, a CNO by default does not have **Create Computer objects** permission explicitly and can create 10 virtual computer objects (VCOs).</span></span> <span data-ttu-id="26f4d-140">10개의 VCO를 만든 후에는 VCO를 추가로 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-140">After 10 VCOs are created, the creation of additional VCOs will fail.</span></span> <span data-ttu-id="26f4d-141">WSFC 클러스터의 CNO에 대한 권한을 명시적으로 부여하여 이 문제를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-141">You can avoid this by granting the permission explicitly to the WSFC cluster's CNO.</span></span> <span data-ttu-id="26f4d-142">삭제한 가용성 그룹에 대한 VCO는 Active Directory에서 자동으로 삭제되지 않으며 수동으로 삭제하지 않는 한 10개의 VCO 기본 제한 개수에 대해 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-142">Note that VCOs for availability groups that you have deleted are not automatically deleted in Active Directory and count against your 10 VCO default limit unless they are manually deleted.</span></span><br /><br /> <span data-ttu-id="26f4d-143">참고: 일부 조직에서는 보안 정책에 따라 **컴퓨터 개체 생성** 권한을 개별 사용자 계정에 부여하는 작업이 금지됩니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-143">Note: In some organizations, the security policy prohibits granting **Create Computer objects** permission to individual user accounts.</span></span>|<span data-ttu-id="26f4d-144">*클러스터를 설치하는 사람의 계정을 구성하는 단계* - [장애 조치(Failover) 클러스터 단계별 가이드: Active Directory에서 계정 구성](https://technet.microsoft.com/library/cc731002\(WS.10\).aspx#BKMK_steps_installer)</span><span class="sxs-lookup"><span data-stu-id="26f4d-144">*Steps for configuring the account for the person who installs the cluster* in [Failover Cluster Step-by-Step Guide: Configuring Accounts in Active Directory](https://technet.microsoft.com/library/cc731002\(WS.10\).aspx#BKMK_steps_installer)</span></span><br /><br /> <span data-ttu-id="26f4d-145">*클러스터 이름 계정을 미리 준비하는 단계* - [장애 조치(Failover) 클러스터 단계별 가이드: Active Directory에서 계정 구성](https://technet.microsoft.com/library/cc731002\(WS.10\).aspx#BKMK_steps_precreating)</span><span class="sxs-lookup"><span data-stu-id="26f4d-145">*Steps for prestaging the cluster name account* in [Failover Cluster Step-by-Step Guide: Configuring Accounts in Active Directory](https://technet.microsoft.com/library/cc731002\(WS.10\).aspx#BKMK_steps_precreating)</span></span>|  
|<span data-ttu-id="26f4d-146">조직에서 수신기 가상 네트워크 이름에 대한 컴퓨터 계정을 미리 준비해야 하는 경우 **계정 운영자** 그룹의 멤버 자격 또는 도메인 관리자의 지원이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-146">If your organization requires that you prestage the computer account for a listener virtual network name, you will need membership in the **Account Operator** group or your domain administrator's assistance.</span></span><br /><br /> <span data-ttu-id="26f4d-147">팁: 일반적으로 수신기 가상 네트워크 이름에 대한 컴퓨터 계정을 미리 준비하지 않는 것이 가장 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-147">Tip: Generally, it is simplest not to prestage the computer account for a listener virtual network name.</span></span> <span data-ttu-id="26f4d-148">가능하면 WSFC 고가용성 마법사를 실행할 때 계정을 자동으로 만들고 구성하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-148">If you can, let the account to be created and configured automatically when you run the WSFC High Availability wizard.</span></span>|<span data-ttu-id="26f4d-149">*클러스터형 서비스 또는 애플리케이션에 대한 계정을 미리 준비하는 단계* - [장애 조치(Failover) 클러스터 단계별 가이드: Active Directory에서 계정 구성](https://technet.microsoft.com/library/cc731002\(WS.10\).aspx#BKMK_steps_precreating2)</span><span class="sxs-lookup"><span data-stu-id="26f4d-149">*Steps for prestaging an account for a clustered service or application* in [Failover Cluster Step-by-Step Guide: Configuring Accounts in Active Directory](https://technet.microsoft.com/library/cc731002\(WS.10\).aspx#BKMK_steps_precreating2).</span></span>|  
  
###  <a name="sql-server-permissions"></a><a name="SqlPermissions"></a> <span data-ttu-id="26f4d-150">SQL Server 사용 권한</span><span class="sxs-lookup"><span data-stu-id="26f4d-150">SQL Server Permissions</span></span>  
  
|<span data-ttu-id="26f4d-151">Task</span><span class="sxs-lookup"><span data-stu-id="26f4d-151">Task</span></span>|<span data-ttu-id="26f4d-152">사용 권한</span><span class="sxs-lookup"><span data-stu-id="26f4d-152">Permissions</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="26f4d-153">가용성 그룹 수신기를 만들려면</span><span class="sxs-lookup"><span data-stu-id="26f4d-153">To create an availability group listener</span></span>|<span data-ttu-id="26f4d-154">CREATE AVAILABILITY GROUP 서버 권한, ALTER ANY AVAILABILITY GROUP 권한, CONTROL SERVER 권한 중 하나와 **sysadmin** 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-154">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
|<span data-ttu-id="26f4d-155">기존 가용성 그룹 수신기를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="26f4d-155">To modify an existing availability group listener</span></span>|<span data-ttu-id="26f4d-156">가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-156">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="26f4d-157">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="26f4d-157">Using SQL Server Management Studio</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="26f4d-158">[새 가용성 그룹 마법사](use-the-new-availability-group-dialog-box-sql-server-management-studio.md) 는 새 가용성 그룹에 대한 수신기 만들기를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-158">The [New Availability Group wizard](use-the-new-availability-group-dialog-box-sql-server-management-studio.md) supports creation of the listener for a new availability group.</span></span>  
  
 <span data-ttu-id="26f4d-159">**가용성 그룹 수신기를 만들거나 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="26f4d-159">**To create or configure an availability group listener**</span></span>  
  
1.  <span data-ttu-id="26f4d-160">개체 탐색기에서 가용성 그룹의 주 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-160">In Object Explorer, connect to the server instance that hosts the primary replica of the availability group, and click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="26f4d-161">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-161">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="26f4d-162">수신기를 구성할 가용성 그룹을 클릭하고 다음 대체 방법 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-162">Click the availability group whose listener you want to configure, and choose one of the following alternatives:</span></span>  
  
    -   <span data-ttu-id="26f4d-163">수신기를 만들려면 **가용성 그룹 수신기** 노드를 마우스 오른쪽 단추로 클릭하고 **새 수신기** 명령을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-163">To create a listener, right-click the **Availability group Listeners** node, and select the **New Listener** command.</span></span> <span data-ttu-id="26f4d-164">그러면 **새 가용성 그룹 수신기** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-164">This opens the **New Availability Group Listener** dialog box.</span></span> <span data-ttu-id="26f4d-165">자세한 내용은 이 항목의 뒷부분에 나와 있는 [가용성 그룹 수신기 추가(대화 상자)](#AddAgListenerDialog)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26f4d-165">For more information, see [Add Availability Group Listener (Dialog Box)](#AddAgListenerDialog), later in this topic.</span></span>  
  
    -   <span data-ttu-id="26f4d-166">기존 수신기의 포트 수를 변경하려면 **가용성 그룹 수신기** 노드를 확장하고 수신기를 마우스 오른쪽 단추로 클릭한 다음 **속성** 명령을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-166">To change the port number of an existing listener, expand the **Availability group Listeners** node, right-click the listener, and select the **Properties** command.</span></span> <span data-ttu-id="26f4d-167">**포트** 필드에 새 포트 번호를 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-167">Enter the new port number into the **Port** field, and click **OK**.</span></span>  
  
###  <a name="new-availability-group-listener-dialog-box"></a><a name="AddAgListenerDialog"></a> <span data-ttu-id="26f4d-168">새 가용성 그룹 수신기(대화 상자)</span><span class="sxs-lookup"><span data-stu-id="26f4d-168">New Availability Group Listener (Dialog Box)</span></span>  
 <span data-ttu-id="26f4d-169">**수신기 DNS 이름**</span><span class="sxs-lookup"><span data-stu-id="26f4d-169">**Listener DNS Name**</span></span>  
 <span data-ttu-id="26f4d-170">가용성 그룹 수신기의 DNS 호스트 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-170">Specifies the DNS host name of the availability group listener.</span></span> <span data-ttu-id="26f4d-171">DNS 이름은 문자열이며 도메인과 NetBIOS에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-171">The DNS name is a string  must be unique in the domain and in NetBIOS.</span></span> <span data-ttu-id="26f4d-172">이 이름은 순서에 관계없이 영숫자 문자, 대시(-) 및 하이픈(_)만 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-172">This name can contain only alphanumeric characters, dashes (-), and hyphens (_), in any order.</span></span> <span data-ttu-id="26f4d-173">DNS 호스트 이름은 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-173">DNS host names are case insensitive.</span></span> <span data-ttu-id="26f4d-174">최대 길이는 15자입니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-174">The maximum length is 15 characters.</span></span>  
  
 <span data-ttu-id="26f4d-175">자세한 내용은 이 항목의 앞부분에 나오는 [가용성 그룹 수신기의 DNS 이름에 대한 요구 사항](#DNSnameReqs)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26f4d-175">For more information, see [Requirements for the DNS Name of an Availability Group Listener](#DNSnameReqs), earlier in this topic.</span></span>  
  
 <span data-ttu-id="26f4d-176">**포트**</span><span class="sxs-lookup"><span data-stu-id="26f4d-176">**Port**</span></span>  
 <span data-ttu-id="26f4d-177">이 수신기에서 사용되는 TPC 포트입니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-177">The TPC port used by this listener.</span></span>  
  
 <span data-ttu-id="26f4d-178">**네트워크 모드**</span><span class="sxs-lookup"><span data-stu-id="26f4d-178">**Network Mode**</span></span>  
 <span data-ttu-id="26f4d-179">수신기에 사용되는 TCP 프로토콜을 나타내며 다음 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-179">Indicates the TCP protocol used by the listener, one of:</span></span>  
  
 <span data-ttu-id="26f4d-180">**DHCP**</span><span class="sxs-lookup"><span data-stu-id="26f4d-180">**DHCP**</span></span>  
 <span data-ttu-id="26f4d-181">수신기는 DHCP(동적 호스트 구성 프로토콜)를 실행하는 서버에서 할당되는 동적 IP 주소를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-181">The listener will us a dynamic IP address that is assigned by a server running the Dynamic Host Configuration Protocol (DHCP).</span></span> <span data-ttu-id="26f4d-182">DHCP는 단일 서브넷으로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-182">DHCP is limited to a single subnet.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="26f4d-183">프로덕션 환경에서는 DHCP를 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-183">We do not recommend DHCP in production environment.</span></span> <span data-ttu-id="26f4d-184">중단 시간이 있고 DHCP IP 임대가 만료되는 경우 수신기 DNS 이름과 연결되고 클라이언트 연결에 영향을 주는 새 DHCP 네트워크 IP 주소를 등록하기 위해 추가 시간이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-184">If there is a down time and the DHCP IP lease expires, extra time is required to register the new DHCP network IP address that is associated with the listener DNS name and impact the client connectivity.</span></span> <span data-ttu-id="26f4d-185">그러나 가용성 그룹의 기본 기능을 확인하고 애플리케이션과 통합하기 위해 DHCP를 개발 및 테스트 환경에 설정하는 것은 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-185">However, DHCP is good for setting up your development and testing environment to verify basic functions of availability groups and for integration with your applications.</span></span>  
  
 <span data-ttu-id="26f4d-186">**고정 IP**</span><span class="sxs-lookup"><span data-stu-id="26f4d-186">**Static IP**</span></span>  
 <span data-ttu-id="26f4d-187">수신기는 하나 이상의 고정 IP 주소를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-187">The listener will use one or more static IP addresses.</span></span> <span data-ttu-id="26f4d-188">추가 IP 주소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-188">Additional IP addresses are optional.</span></span> <span data-ttu-id="26f4d-189">여러 서브넷 간에 가용성 그룹 수신기를 만들려면 각 서브넷에 대해 수신기 구성에서 고정 IP 주소를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-189">To create an availability group listener across multiple subnets, for each subnet you must specify a static IP address in the listener configuration.</span></span> <span data-ttu-id="26f4d-190">이러한 고정 IP 주소를 얻으려면 네트워크 관리자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="26f4d-190">Contact your network administrator to get these static IP addresses.</span></span>  
  
 <span data-ttu-id="26f4d-191">**고정 IP** 를 선택하면 **네트워크 모드** 필드 아래 서브넷 표가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-191">If you select **Static IP** a subnet grid appears below the **Network Mode** field.</span></span> <span data-ttu-id="26f4d-192">이 표에는 이 가용성 그룹 수신기가 액세스할 수 있는 각 서브넷에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-192">This grid displays information about each subnet that can be accessed by this availability group listener.</span></span> <span data-ttu-id="26f4d-193">**추가**를 클릭하여 고정 IP 주소를 추가할 때까지 이 표는 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-193">This grid is empty until you add a static IP address by clicking **Add**.</span></span>  
  
 <span data-ttu-id="26f4d-194">열은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-194">The columns are as follows:</span></span>  
  
 <span data-ttu-id="26f4d-195">**서브넷**</span><span class="sxs-lookup"><span data-stu-id="26f4d-195">**Subnet**</span></span>  
 <span data-ttu-id="26f4d-196">가용성 그룹 수신기에 추가하는 각 서브넷의 식별자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-196">Displays the identifier of each subnet that you add to the availability group listener.</span></span>  
  
 <span data-ttu-id="26f4d-197">**IP 주소**</span><span class="sxs-lookup"><span data-stu-id="26f4d-197">**IP Address**</span></span>  
 <span data-ttu-id="26f4d-198">지정된 서브넷의 IP 주소를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-198">Displays the IP address of a given subnet.</span></span>  <span data-ttu-id="26f4d-199">지정된 서브넷에 대해 IP 주소는 IPv4 주소 또는 IPv6 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-199">For a given subnet, the IP address is either an IPv4 address or an IPv6 address.</span></span>  
  
 <span data-ttu-id="26f4d-200">**추가**</span><span class="sxs-lookup"><span data-stu-id="26f4d-200">**Add**</span></span>  
 <span data-ttu-id="26f4d-201">선택한 서브넷 또는 이 수신기에 대한 다른 서브넷에 고정 IP 주소를 추가하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-201">Click to add to add a static IP address to a selected subnet or to another subnet for this listener.</span></span> <span data-ttu-id="26f4d-202">그러면 **IP 주소 추가** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-202">This opens the **Add IP Address** dialog box.</span></span> <span data-ttu-id="26f4d-203">자세한 내용은 [IP 주소 추가 대화 상자&#40;SQL Server Management Studio&#41;](add-ip-address-dialog-box-sql-server-management-studio.md) 도움말 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26f4d-203">For more information, see the [Add IP Address Dialog Box &#40;SQL Server Management Studio&#41;](add-ip-address-dialog-box-sql-server-management-studio.md) help topic.</span></span>  
  
 <span data-ttu-id="26f4d-204">**제거**</span><span class="sxs-lookup"><span data-stu-id="26f4d-204">**Remove**</span></span>  
 <span data-ttu-id="26f4d-205">이 수신기에서 선택한 서브넷을 제거하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-205">Click to remove the selected subnet from this listener.</span></span>  
  
 <span data-ttu-id="26f4d-206">**확인**</span><span class="sxs-lookup"><span data-stu-id="26f4d-206">**OK**</span></span>  
 <span data-ttu-id="26f4d-207">지정한 가용성 그룹 수신기를 만들려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-207">Click to create the specified availability group listener.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="26f4d-208">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="26f4d-208">Using Transact-SQL</span></span>  

### <a name="to-create-or-configure-an-availability-group-listener"></a><span data-ttu-id="26f4d-209">가용성 그룹 수신기를 만들거나 구성하려면</span><span class="sxs-lookup"><span data-stu-id="26f4d-209">To create or configure an availability group listener</span></span>
  
1.  <span data-ttu-id="26f4d-210">주 복제본을 호스팅하는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-210">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="26f4d-211">[CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql) 문의 LISTENER 옵션 또는 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 문의 ADD LISTENER 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-211">Use the LISTENER option of the [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql) statement or the ADD LISTENER option of the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement.</span></span>  
  
     <span data-ttu-id="26f4d-212">다음 예에서는 `MyAg2`라는 기존 가용성 그룹에 가용성 그룹 수신기를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-212">The following example adds an availability group listener to an existing availability group named `MyAg2`.</span></span> <span data-ttu-id="26f4d-213">이 수신기에 대해 고유한 DNS 이름인 `MyAg2ListenerIvP6`이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-213">A unique DNS name, `MyAg2ListenerIvP6`, is specified for this listener.</span></span> <span data-ttu-id="26f4d-214">두 복제본이 서로 다른 서브넷에 있으므로 수신기는 고정 IP 주소를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-214">The two replicas are on different subnets, so , as recommended, the listener uses static IP addresses.</span></span> <span data-ttu-id="26f4d-215">두 가용성 복제본 각각에 대해 IPv6 형식을 사용하는 고정 IP 주소인 `2001:4898:f0:f00f::cf3c and 2001:4898:e0:f213::4ce2`를 WITH IP 절이 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-215">For each of the two availability replicas, the WITH IP clause specifies a static IP address, `2001:4898:f0:f00f::cf3c and 2001:4898:e0:f213::4ce2`, which use the IPv6 format.</span></span> <span data-ttu-id="26f4d-216">또한 이 예제에서 PORT 인수(옵션)를 사용하여 포트 `60173` 을 수신기 포트로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-216">This example also specifies uses the optional PORT argument to specify port `60173` as the listener port.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAg2   
          ADD LISTENER 'MyAg2ListenerIvP6' ( WITH IP ( ('2001:db88:f0:f00f::cf3c'),('2001:4898:e0:f213::4ce2') ) , PORT = 60173 );   
    GO  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="26f4d-217">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="26f4d-217">Using PowerShell</span></span>  

### <a name="to-create-or-configure-an-availability-group-listener"></a><span data-ttu-id="26f4d-218">가용성 그룹 수신기를 만들거나 구성하려면</span><span class="sxs-lookup"><span data-stu-id="26f4d-218">To create or configure an availability group listener</span></span> 
  
1.  <span data-ttu-id="26f4d-219">주 복제본을 호스팅하는 서버 인스턴스로 디렉터리를 변경(`cd`)합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-219">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="26f4d-220">가용성 그룹 수신기를 만들거나 수정하려면 다음 cmdlet 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-220">To create or modify an availability group listener use one of the following cmdlets:</span></span>  
  
     `New-SqlAvailabilityGroupListener`  
     <span data-ttu-id="26f4d-221">새 가용성 그룹 수신기를 만들고 기존 가용성 그룹에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-221">Creates a new availability group listener and attaches it to an existing availability group.</span></span>  
  
     <span data-ttu-id="26f4d-222">예를 들어, 다음의 `New-SqlAvailabilityGroupListener` 명령은 가용성 그룹 `MyListener`에 대해 `MyAg`라는 가용성 그룹 수신기를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-222">For example, the following `New-SqlAvailabilityGroupListener` command creates an availability group listener named `MyListener` for the availability group `MyAg`.</span></span> <span data-ttu-id="26f4d-223">이 수신기는 `-StaticIp` 매개 변수에 전달된 IPv4 주소를 가상 IP 주소로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-223">This listener will use the IPv4 address passed to the `-StaticIp` parameter as its virtual IP address.</span></span>  
  
    ```powershell
    New-SqlAvailabilityGroupListener -Name MyListener `
    -StaticIp '192.168.3.1/255.255.252.0' `
    -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg
    ```  
  
     `Set-SqlAvailabilityGroupListener`  
     <span data-ttu-id="26f4d-224">기존 가용성 수신기에서 포트 설정을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-224">Modifies the port setting on an existing availability group listener.</span></span>  
  
     <span data-ttu-id="26f4d-225">예를 들어, 다음의 `Set-SqlAvailabilityGroupListener` 명령은 `MyListener`라는 가용성 그룹 수신기의 포트 번호를 `1535`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-225">For example, the following `Set-SqlAvailabilityGroupListener` command sets the port number for the availability group listener named `MyListener` to `1535`.</span></span> <span data-ttu-id="26f4d-226">이 포트는 수신기에 대한 연결을 수신하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-226">This port is used to listen for connections to the listener.</span></span>  
  
    ```powershell
    Set-SqlAvailabilityGroupListener -Port 1535 `
    -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AGListeners\MyListener  
    ```  
  
     `Add-SqlAGListenerstaticIp`  
     <span data-ttu-id="26f4d-227">기존 가용성 그룹 수신기 구성에 고정 IP 주소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-227">Adds a static IP address to an existing availability group listener configuration.</span></span> <span data-ttu-id="26f4d-228">IP 주소는 서브넷이 있는 IPv4 주소이거나 IPv6 주소일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-228">The IP address can be an IPv4 address with subnet, or an IPv6 address.</span></span>  
  
     <span data-ttu-id="26f4d-229">예를 들어, 다음의 `Add-SqlAGListenerstaticIp` 명령은 가용성 그룹 `MyListener`의 `MyAg` 가용성 그룹 수신기에 고정 IPv4 주소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-229">For example, the following `Add-SqlAGListenerstaticIp` command adds a static IPv4 address to the availability group listener `MyListener` on the availability group `MyAg`.</span></span> <span data-ttu-id="26f4d-230">이 IPv6 주소는 `255.255.252.0`서브넷에서 수신기의 가상 IP 주소로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-230">This IPv6 address serves as the virtual IP address of the listener on the subnet `255.255.252.0`.</span></span> <span data-ttu-id="26f4d-231">가용성 그룹이 복수 서브넷에 있는 경우 각 서브넷에 대한 고정 IP 주소를 수신기에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-231">If the availability group spans multiple subnets, you should add a static IP address for each subnet to the listener.</span></span>  
  
    ```powershell
    $path = "SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AGListeners\ MyListener" `
    Add-SqlAGListenerstaticIp -Path $path `
    -StaticIp "2001:0db8:85a3:0000:0000:8a2e:0370:7334"  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="26f4d-232">Cmdlet의 구문을 보려면 PowerShell 환경에서 **get-help** cmdlet을 사용 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-232">To view the syntax of a cmdlet, use the **Get-Help**  cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="26f4d-233">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26f4d-233">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="26f4d-234">SQL Server PowerShell 공급자를 설정 하 고 사용 하려면 [SQL Server PowerShell 공급자](../../../powershell/sql-server-powershell-provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="26f4d-234">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).</span></span>
  
## <a name="troubleshooting"></a><span data-ttu-id="26f4d-235">문제 해결</span><span class="sxs-lookup"><span data-stu-id="26f4d-235">Troubleshooting</span></span>  
  
###  <a name="failure-to-create-an-availability-group-listener-because-of-active-directory-quotas"></a><a name="ADQuotas"></a><span data-ttu-id="26f4d-236">Active Directory 할당량으로 인해 가용성 그룹 수신기를 만들지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-236">Failure to Create An Availability Group Listener Because of Active Directory Quotas</span></span>  
 <span data-ttu-id="26f4d-237">참여하는 클러스터 노드 컴퓨터 계정에 대한 Active Directory 할당량에 도달하여 새 가용성 그룹 수신기를 만들지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-237">The creation of a new availability group listener may fail upon creation because you have reached an Active Directory quota for the participating cluster node machine account.</span></span>  <span data-ttu-id="26f4d-238">자세한 내용은 다음 아티클을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26f4d-238">For more information, see the following articles:</span></span>  
  
-   [<span data-ttu-id="26f4d-239">HYPERLINK " https://support.microsoft.com/kb/307532 " 컴퓨터 개체 수정 시 클러스터 서비스 계정 문제를 해결 하는 방법</span><span class="sxs-lookup"><span data-stu-id="26f4d-239">HYPERLINK "https://support.microsoft.com/kb/307532" How to Troubleshoot the Cluster Service Account When It Modifies Computer Objects</span></span>](https://support.microsoft.com/kb/307532)  
  
-   <span data-ttu-id="26f4d-240">[HYPERLINK " https://technet.microsoft.com/library/cc904295(WS.10).aspx " Active Directory 할당량](https://technet.microsoft.com/library/cc904295\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="26f4d-240">[HYPERLINK "https://technet.microsoft.com/library/cc904295(WS.10).aspx" Active Directory Quotas](https://technet.microsoft.com/library/cc904295\(WS.10\).aspx)</span></span>  
  
##  <a name="follow-up-after-creating-an-availability-group-listener"></a><a name="FollowUp"></a> <span data-ttu-id="26f4d-241">후속 작업: 가용성 그룹 수신기를 만든 후</span><span class="sxs-lookup"><span data-stu-id="26f4d-241">Follow-up: After Creating an Availability Group Listener</span></span>  
  
###  <a name="multisubnetfailover-keyword-and-associated-features"></a><a name="MultiSubnetFailover"></a><span data-ttu-id="26f4d-242">MultiSubnetFailover 키워드 및 관련 기능</span><span class="sxs-lookup"><span data-stu-id="26f4d-242">MultiSubnetFailover Keyword and Associated Features</span></span>  
 <span data-ttu-id="26f4d-243">`MultiSubnetFailover`는 SQL Server 2012에서 AlwaysOn 가용성 그룹과 AlwaysOn 장애 조치(Failover) 클러스터 인스턴스를 사용하여 보다 빠르게 장애 조치할 수 있도록 하는 데 사용되는 새로운 연결 문자열 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-243">`MultiSubnetFailover` is a new connection string keyword used to enable faster failover with AlwaysOn Availability Groups and AlwaysOn Failover Cluster Instances in SQL Server 2012.</span></span> <span data-ttu-id="26f4d-244">`MultiSubnetFailover=True` 가 연결 문자열에서 설정되면 다음 세 가지 하위 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-244">The following three sub-features are enabled when `MultiSubnetFailover=True` is set in connection string:</span></span>  
  
-   <span data-ttu-id="26f4d-245">AlwaysOn 가용성 그룹 또는 장애 조치(Failover) 클러스터 인스턴스에 대한 다중 서브넷 수신기로 보다 빠른 다중 서브넷 장애 조치</span><span class="sxs-lookup"><span data-stu-id="26f4d-245">Faster multi-subnet failover to a multi-subnet listener for an AlwaysOn Availability Group or Failover Cluster Instances.</span></span>  
  
-   <span data-ttu-id="26f4d-246">AlwaysOn 가용성 그룹 또는 장애 조치(Failover) 클러스터 인스턴스에 대한 단일 서브넷 수신기로 보다 빠른 단일 서브넷 장애 조치</span><span class="sxs-lookup"><span data-stu-id="26f4d-246">Faster single subnet failover to a single subnet listener for an AlwaysOn Availability Group or Failover Cluster Instances.</span></span>  
  
    -   <span data-ttu-id="26f4d-247">이 기능은 단일 서브넷의 단일 IP가 있는 수신기에 연결할 때 사용되며,</span><span class="sxs-lookup"><span data-stu-id="26f4d-247">This feature is used when connecting to a listener that has a single IP in a single subnet.</span></span> <span data-ttu-id="26f4d-248">단일 서브넷 장애 조치(Failover) 속도를 높이기 위해 보다 적극적으로 TCP 연결을 다시 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-248">This performs more aggressive TCP connection retries to speed up single subnet failovers.</span></span>  
  
-   <span data-ttu-id="26f4d-249">다중 서브넷 AlwaysOn 장애 조치(Failover) 클러스터 인스턴스로 명명된 인스턴스 확인</span><span class="sxs-lookup"><span data-stu-id="26f4d-249">Named instance resolution to a multi-subnet AlwaysOn Failover Cluster Instance.</span></span>  
  
    -   <span data-ttu-id="26f4d-250">서브넷 엔드포인트가 여러 개인 AlwaysOn 장애 조치(Failover) 클러스터 인스턴스에 대한 명명된 인스턴스 확인 지원을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-250">This is to add named instance resolution support for an AlwaysOn Failover Cluster Instances with multiple subnet endpoints.</span></span>  
  
 <span data-ttu-id="26f4d-251">**MultiSubnetFailover=True가 .NET Framework 3.5 또는 OLEDB에서 지원되지 않음**</span><span class="sxs-lookup"><span data-stu-id="26f4d-251">**MultiSubnetFailover=True Not Supported by NET Framework 3.5 or OLEDB**</span></span>  
  
 <span data-ttu-id="26f4d-252">**문제:** 가용성 그룹 또는 장애 조치 (Failover) 클러스터 인스턴스에 서로 다른 서브넷의 여러 IP 주소에 따라 수신기 이름 (WSFC 클러스터 관리자에서는 네트워크 이름 또는 클라이언트 액세스 지점 이라고 함)이 있고 .NET Framework 3.5 s p 1을 사용 하는 ADO.NET SQL Native Client 또는 11.0 OLEDB를 사용 하는 경우 가용성 그룹 수신기에 대 한 클라이언트 연결 요청의 잠재적 50%가 연결 제한 시간에 도달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-252">**Issue:** If your Availability Group or Failover Cluster Instance has a listener name (known as the network name or Client Access Point in the WSFC Cluster Manager) depending on multiple IP addresses from different subnets, and you are using either ADO.NET with .NET Framework 3.5SP1 or SQL Native Client 11.0 OLEDB, potentially 50% of your client-connection requests to the availability group listener will hit a connection timeout.</span></span>  
  
 <span data-ttu-id="26f4d-253">**해결 방법:** 다음 작업 중 하나를 수행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-253">**Workarounds:** We recommend that you do one of the following tasks.</span></span>  
  
-   <span data-ttu-id="26f4d-254">클러스터 리소스를 조작할 권한이 없는 경우 연결 제한 시간을 30초로 변경합니다. 이 값은 20초 TCP 제한 시간 기간과 10초 버퍼를 더한 값입니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-254">If do not have the permission to manipulate cluster resources, change your connection timeout to 30 seconds (this value results in a 20-second TCP timeout period plus a 10-second buffer).</span></span>  
  
     <span data-ttu-id="26f4d-255">**장점**: 서브넷 간 장애 조치(Failover)가 발생하는 경우 클라이언트 복구 시간이 짧습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-255">**Pros**: If a cross-subnet failover occurs, client recovery time is short.</span></span>  
  
     <span data-ttu-id="26f4d-256">**단점**: 클라이언트 연결 중 절반이 20초 이상 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-256">**Cons**: Half of the client connections will take more than 20 seconds</span></span>  
  
-   <span data-ttu-id="26f4d-257">클러스터 리소스를 조작할 권한이 있는 경우 더 권장하는 방법은 가용성 그룹 수신기의 네트워크 이름을 `RegisterAllProvidersIP=0`으로 설정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-257">If you have the permission to manipulate cluster resources, the more recommended approach is to set the network name of your availability group listener to `RegisterAllProvidersIP=0`.</span></span> <span data-ttu-id="26f4d-258">자세한 내용은 이 항목의 뒷부분에 나오는 "RegisterAllProvidersIP 설정"을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26f4d-258">For more information, see "RegisterAllProvidersIP Setting" later in this section.</span></span>  
  
     <span data-ttu-id="26f4d-259">**장점:** 클라이언트 연결 제한 시간 값을 증가시키지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-259">**Pros:** You do not need to increase your client-connection timeout value.</span></span>  
  
     <span data-ttu-id="26f4d-260">**단점:** 서브넷 간 장애 조치 (failover)가 발생 하는 경우 클라이언트 복구 시간은 `HostRecordTTL` 설정 및 사이트 간 DNS/AD 복제 일정의 설정에 따라 15 분 이상 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-260">**Cons:** If a cross-subnet failover occurs, the client recovery time could be 15 minutes or longer, depending on your `HostRecordTTL` setting and the setting of your cross-site DNS/AD replication schedule.</span></span>  
  
###  <a name="registerallprovidersip-setting"></a><a name="RegisterAllProvidersIP"></a><span data-ttu-id="26f4d-261">RegisterAllProvidersIP 설정</span><span class="sxs-lookup"><span data-stu-id="26f4d-261">RegisterAllProvidersIP Setting</span></span>  
 <span data-ttu-id="26f4d-262">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] 또는 PowerShell을 사용하여 가용성 그룹 수신기를 만들면 WSFC에서 `RegisterAllProvidersIP` 속성이 1(true)로 설정된 클라이언트 액세스 지점이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-262">When you use [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell to create an availability group listener, the Client Access Point is created in WSFC with the `RegisterAllProvidersIP` property set to 1 (true).</span></span> <span data-ttu-id="26f4d-263">이 속성 값의 효과는 클라이언트 연결 문자열에 따라 다음과 같이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-263">The effect of this property value depends on the client connection string, as follows:</span></span>  
  
-   <span data-ttu-id="26f4d-264">`MultiSubnetFailover`를 true로 설정하는 연결 문자열</span><span class="sxs-lookup"><span data-stu-id="26f4d-264">Connection strings that set `MultiSubnetFailover` to true</span></span>  
  
     [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]<span data-ttu-id="26f4d-265">은 클라이언트 연결 문자열이 권장 사항에 따라 `RegisterAllProvidersIP`를 지정하는 클라이언트에 대한 장애 조치(Failover) 후에 재연결 시간을 줄이기 위해 `MultiSubnetFailover = True` 속성을 1로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-265">sets the  `RegisterAllProvidersIP` property to 1 in order to reduce re-connection time after a failover for clients whose client connection strings specify `MultiSubnetFailover = True`, as recommended.</span></span> <span data-ttu-id="26f4d-266">수신기의 다중 서브넷 기능을 사용하려면 클라이언트에 `MultiSubnetFailover` 키워드를 지원하는 데이터 공급자가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-266">Note that to take advantage of the listener multi-subnet feature, your clients might require a data provider that supports the `MultiSubnetFailover` keyword.</span></span> <span data-ttu-id="26f4d-267">다중 서브넷 장애 조치(failover)의 드라이버 지원에 대한 자세한 내용은 [AlwaysOn 클라이언트 연결&#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26f4d-267">For information about driver support for multi-subnet failover, see [AlwaysOn Client Connectivity &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md).</span></span>  
  
     <span data-ttu-id="26f4d-268">다중 서브넷 클러스터링에 대한 자세한 내용은 [SQL Server 다중 서브넷 클러스터링&#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server.md)를 만들거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-268">For information about multi-subnet clustering, see [SQL Server Multi-Subnet Clustering &#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server.md).</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="26f4d-269">`RegisterAllProvidersIP = 1`일 때 WSFC 클러스터에서 WSFC 구성 유효성 검사 마법사를 실행하면 마법사가 다음과 같은 경고 메시지를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-269">When `RegisterAllProvidersIP = 1`, if you run the WSFC Validate a Configuration Wizard on the WSFC cluster, the wizard generates the following warning message:</span></span>  
    >   
    >  <span data-ttu-id="26f4d-270">“네트워크 이름 'Name:<network_name>'의 RegisterAllProviderIP 속성이 1로 설정되어 있습니다. 현재 클러스터 구성에서는 이 값을 0으로 설정해야 합니다.”</span><span class="sxs-lookup"><span data-stu-id="26f4d-270">"The RegisterAllProviderIP property for network name 'Name:<network_name>' is set to 1 For the current cluster configuration this value should be set to 0."</span></span>  
    >   
    >  <span data-ttu-id="26f4d-271">이 메시지는 무시하세요.</span><span class="sxs-lookup"><span data-stu-id="26f4d-271">Please ignore this message.</span></span>  
  
-   <span data-ttu-id="26f4d-272">`MultiSubnetFailover`를 true로 설정하지 않는 연결 문자열</span><span class="sxs-lookup"><span data-stu-id="26f4d-272">Connection strings that do not set `MultiSubnetFailover` to true</span></span>  
  
     <span data-ttu-id="26f4d-273">`RegisterAllProvidersIP = 1`일 때는 연결 문자열이 `MultiSubnetFailover = True`를 사용하지 않는 클라이언트에서 연결 대기 시간이 길어집니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-273">When `RegisterAllProvidersIP = 1`, any clients whose connection strings do not use `MultiSubnetFailover = True`, will experience high latency connections.</span></span> <span data-ttu-id="26f4d-274">이는 이러한 클라이언트가 모든 IP에 순차적으로 연결을 시도하기 때문에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-274">This occurs because these clients attempt connections to all IPs sequentially.</span></span> <span data-ttu-id="26f4d-275">반면에 `RegisterAllProvidersIP`를 0으로 변경하면 활성 IP 주소가 WSFC 클러스터의 클라이언트 액세스 지점에 등록되기 때문에 레거시 클라이언트에 대한 대기 시간이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-275">In contrast, if `RegisterAllProvidersIP` is changed to 0, the active IP address is registered in the Client Access Point in the WSFC cluster, reducing latency for legacy clients.</span></span> <span data-ttu-id="26f4d-276">따라서 가용성 그룹 수신기에 연결 해야 하는 레거시 클라이언트가 있고 속성을 사용할 수 없는 경우 `MultiSubnetFailover` 0으로 변경 하는 것이 좋습니다 `RegisterAllProvidersIP` .</span><span class="sxs-lookup"><span data-stu-id="26f4d-276">Therefore, if you have legacy clients that need to connect to an availability group listener and cannot use the `MultiSubnetFailover` property, we recommend that you change `RegisterAllProvidersIP` to 0.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="26f4d-277">WSFC 클러스터(장애 조치(Failover) 클러스터 관리자 GUI)를 통해 가용성 그룹 수신기를 만들면 기본적으로 `RegisterAllProvidersIP`는 0(false)으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-277">When you create an availability group listener through the WSFC cluster (Failover Cluster Manager GUI), `RegisterAllProvidersIP` will be 0 (false) by default.</span></span>  
  
###  <a name="hostrecordttl-setting"></a><a name="HostRecordTTL"></a> <span data-ttu-id="26f4d-278">HostRecordTTL 설정</span><span class="sxs-lookup"><span data-stu-id="26f4d-278">HostRecordTTL Setting</span></span>  
 <span data-ttu-id="26f4d-279">기본적으로 클라이언트는 클러스터 DNS 레코드를 20분 동안 캐시합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-279">By default, clients cache cluster DNS records for 20 minutes.</span></span>  <span data-ttu-id="26f4d-280">캐시된 레코드의 TTL(Time to Live)인 `HostRecordTTL`을 줄이면 레거시 클라이언트가 더 빨리 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-280">By reducing `HostRecordTTL`, the Time to Live (TTL), for the cached record, legacy clients may reconnect more quickly.</span></span>  <span data-ttu-id="26f4d-281">하지만 `HostRecordTTL` 설정을 줄이면 DN 서버의 트래픽이 증가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-281">However, reducing the `HostRecordTTL` setting may also result in increased traffic to the DN servers.</span></span>  
  
###  <a name="sample-powershell-script-to-disable-registerallprovidersip-and-reduce-ttl"></a><a name="SampleScript"></a><span data-ttu-id="26f4d-282">RegisterAllProvidersIP를 비활성화 하 고 TTL을 줄이는 샘플 PowerShell 스크립트</span><span class="sxs-lookup"><span data-stu-id="26f4d-282">Sample PowerShell Script to Disable RegisterAllProvidersIP and Reduce TTL</span></span>  
 <span data-ttu-id="26f4d-283">다음 PowerShell 예에서는 수신기 리소스에 대한 `RegisterAllProvidersIP` 및 `HostRecordTTL` 클러스터 매개 변수를 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-283">The following PowerShell example demonstrates how to configure both the `RegisterAllProvidersIP` and `HostRecordTTL` cluster parameters for the listener resource.</span></span>  <span data-ttu-id="26f4d-284">DNS 레코드는 기본 20분이 아닌 5분 동안 캐시됩니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-284">The DNS record will be cached for 5 minutes rather than the default 20 minutes.</span></span>  <span data-ttu-id="26f4d-285">두 클러스터 매개 변수를 모두 수정하면 `MultiSubnetFailover` 매개 변수를 사용할 수 없는 레거시 클라이언트에 대한 장애 조치(Failover) 후 올바른 IP 주소에 연결하는 시간이 줄어들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-285">Modifying both cluster parameters may reduce the time to connect to the correct IP address after a failover for legacy clients that cannot use the `MultiSubnetFailover` parameter.</span></span>  <span data-ttu-id="26f4d-286">`yourListenerName` 을 변경할 수신기의 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-286">Replace `yourListenerName` with the name of the listener that you are changing.</span></span>  
  
```powershell
Import-Module FailoverClusters  
Get-ClusterResource yourListenerName | Set-ClusterParameter RegisterAllProvidersIP 0
Get-ClusterResource yourListenerName|Set-ClusterParameter HostRecordTTL 300  
Stop-ClusterResource yourListenerName  
Start-ClusterResource yourAGResource  
```  
  
 <span data-ttu-id="26f4d-287">장애 조치(Failover) 중 복구 시간에 대한 자세한 내용은 [Client Recovery Latency During Failover](../../../sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server.md#DNS)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26f4d-287">For more information about recovery times during failover, see [Client Recovery Latency During Failover](../../../sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server.md#DNS).</span></span>  
  
###  <a name="follow-up-recommendations"></a><a name="FollowUpRecommendations"></a> <span data-ttu-id="26f4d-288">후속 권장 사항</span><span class="sxs-lookup"><span data-stu-id="26f4d-288">Follow-up Recommendations</span></span>  
 <span data-ttu-id="26f4d-289">가용성 그룹 수신기를 만든 후:</span><span class="sxs-lookup"><span data-stu-id="26f4d-289">After you create an availability group listener:</span></span>  
  
-   <span data-ttu-id="26f4d-290">네트워크 관리자에게 요청하여 수신기의 IP 주소를 배타적으로 사용할 수 있도록 예약합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-290">Ask your network administrator to reserve the listener's IP address for its exclusive use.</span></span>  
  
-   <span data-ttu-id="26f4d-291">이 가용성 그룹에 대한 클라이언트 연결을 요청할 때 연결 문자열에 사용할 수신기의 DNS 호스트 이름을 애플리케이션 개발자에게 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-291">Give the listener's DNS host name to application developers to use in connection strings when requesting client connections to this availability group.</span></span>  
  
-   <span data-ttu-id="26f4d-292">가능한 경우 개발자가 클라이언트 연결 문자열을 업데이트하여 `MultiSubnetFailover = True`를 지정하도록 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-292">Encourage developers to update client connection strings to specify `MultiSubnetFailover = True`, if possible.</span></span> <span data-ttu-id="26f4d-293">다중 서브넷 장애 조치(failover)의 드라이버 지원에 대한 자세한 내용은 [AlwaysOn 클라이언트 연결&#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26f4d-293">For information about driver support for multi-subnet failover, see [AlwaysOn Client Connectivity &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md).</span></span>  
  
###  <a name="create-an-additional-listener-for-an-availability-group-optional"></a><a name="CreateAdditionalListener"></a> <span data-ttu-id="26f4d-294">가용성 그룹의 추가 수신기 만들기(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="26f4d-294">Create an Additional Listener for an Availability Group (Optional)</span></span>  
 <span data-ttu-id="26f4d-295">SQL Server를 통해 수신기를 하나 만든 후 다음과 같이 추가 수신기를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-295">After you create one listener through SQL Server, you can add an additional listener, as follows:</span></span>  
  
1.  <span data-ttu-id="26f4d-296">다음 도구 중 하나를 사용하여 수신기를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-296">Create the listener using either of the following tools:</span></span>  
  
    -   <span data-ttu-id="26f4d-297">**WSFC 장애 조치(Failover) 클러스터 관리자 사용:**</span><span class="sxs-lookup"><span data-stu-id="26f4d-297">**Using WSFC Failover Cluster Manager:**</span></span>  
  
        1.  <span data-ttu-id="26f4d-298">클라이언트 액세스 지점을 추가하고 IP 주소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-298">Add a client access point and configure the IP address.</span></span>  
  
        2.  <span data-ttu-id="26f4d-299">수신기를 온라인 상태로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-299">Bring the listener online.</span></span>  
  
        3.  <span data-ttu-id="26f4d-300">WSFC 가용성 그룹 리소스에 종속성을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-300">Add a dependency to the WSFC availability group resource.</span></span>  
  
         <span data-ttu-id="26f4d-301">장애 조치(Failover) 클러스터 관리자의 대화 상자와 탭에 대한 자세한 내용은 [사용자 인터페이스: 장애 조치(Failover) 클러스터 관리자 스냅인](https://technet.microsoft.com/library/cc772502.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26f4d-301">For information about the dialog boxes and tabs of the Failover Cluster Manager, see [User Interface: The Failover Cluster Manager Snap-In](https://technet.microsoft.com/library/cc772502.aspx).</span></span>  
  
    -   <span data-ttu-id="26f4d-302">**장애 조치(failover) 클러스터용 Windows PowerShell 사용:**</span><span class="sxs-lookup"><span data-stu-id="26f4d-302">**Using Windows PowerShell for failover clusters:**</span></span>  
  
        1.  <span data-ttu-id="26f4d-303">[Add-ClusterResource](https://technet.microsoft.com/library/ee460983.aspx) 를 사용하여 네트워크 이름과 IP 주소 리소스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-303">Use [Add-ClusterResource](https://technet.microsoft.com/library/ee460983.aspx) to create a network name and the IP address resources.</span></span>  
  
        2.  <span data-ttu-id="26f4d-304">[Start-ClusterResource](https://technet.microsoft.com/library/ee461056.aspx) 를 사용하여 네트워크 이름 리소스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-304">Use [Start-ClusterResource](https://technet.microsoft.com/library/ee461056.aspx) to start the network name resource.</span></span>  
  
        3.  <span data-ttu-id="26f4d-305">[Add-ClusterResourceDependency](https://technet.microsoft.com/library/ee461014.aspx) 를 사용하여 네트워크 이름과 기존 SQL Server 가용성 그룹 리소스 간의 종속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-305">Use [Add-ClusterResourceDependency](https://technet.microsoft.com/library/ee461014.aspx) to set the dependency between the network name and the existing SQL Server Availability Group resource.</span></span>  
  
         <span data-ttu-id="26f4d-306">장애 조치(failover) 클러스터용 Windows Powershell에 대한 자세한 내용은 [서버 관리자 명령 개요](https://technet.microsoft.com/library/cc732757.aspx#BKMK_wps)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26f4d-306">For information about using Windows PowerShell for failover clusters, see [Overview of Server Manager Commands](https://technet.microsoft.com/library/cc732757.aspx#BKMK_wps).</span></span>  
  
2.  <span data-ttu-id="26f4d-307">새 수신기에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 수신 대기를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-307">Start [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] listening on the new listener.</span></span> <span data-ttu-id="26f4d-308">추가 수신기를 만든 후 가용성 그룹의 주 복제본을 호스팅하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 인스턴스에 연결하고 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]또는 PowerShell을 사용하여 수신기 포트를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="26f4d-308">After creating the additional listener, connect to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the primary replica of the availability group and use [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell to modify the listener port.</span></span>  
  
 <span data-ttu-id="26f4d-309">자세한 내용은 [How to create multiple listeners for same availability group](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/03/how-to-create-multiple-listeners-for-same-availability-group-goden-yao.aspx)(동일한 가용성 그룹에 대해 여러 수신기를 만드는 방법)(SQL Server AlwaysOn 팀 블로그)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26f4d-309">For more information, see [How to create multiple listeners for same availability group](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/03/how-to-create-multiple-listeners-for-same-availability-group-goden-yao.aspx) (a SQL Server AlwaysOn team blog).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="26f4d-310">관련 작업</span><span class="sxs-lookup"><span data-stu-id="26f4d-310">Related Tasks</span></span>  
  
-   [<span data-ttu-id="26f4d-311">가용성 그룹 수신기 속성 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="26f4d-311">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)  
  
-   [<span data-ttu-id="26f4d-312">가용성 그룹 수신기 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="26f4d-312">Remove an Availability Group Listener &#40;SQL Server&#41;</span></span>](remove-an-availability-group-listener-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="26f4d-313">관련 내용</span><span class="sxs-lookup"><span data-stu-id="26f4d-313">Related Content</span></span>  
  
-   [<span data-ttu-id="26f4d-314">동일한 가용성 그룹에 대해 여러 수신기를 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="26f4d-314">How to create multiple listeners for same availability group</span></span>](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/03/how-to-create-multiple-listeners-for-same-availability-group-goden-yao.aspx)  
  
-   [<span data-ttu-id="26f4d-315">SQL Server AlwaysOn 팀 블로그: 공식 SQL Server AlwaysOn 팀 블로그</span><span class="sxs-lookup"><span data-stu-id="26f4d-315">SQL Server AlwaysOn Team Blog: The official SQL Server AlwaysOn team blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
## <a name="see-also"></a><span data-ttu-id="26f4d-316">참고 항목</span><span class="sxs-lookup"><span data-stu-id="26f4d-316">See Also</span></span>  
 <span data-ttu-id="26f4d-317">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="26f4d-317">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="26f4d-318">[가용성 그룹 수신기, 클라이언트 연결 및 애플리케이션 장애 조치(failover)&#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="26f4d-318">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 [<span data-ttu-id="26f4d-319">SQL Server 다중 서브넷 클러스터링&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="26f4d-319">SQL Server Multi-Subnet Clustering &#40;SQL Server&#41;</span></span>](../../../sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server.md)  
