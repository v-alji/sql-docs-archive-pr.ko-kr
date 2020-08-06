---
title: Attunity의 Change Data Capture Service for Oracle에 대 한 사용자 역할 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: be0ec384-e03b-4483-96ca-02b289804d6a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e694da0cfd8645fe594b049b6dc2394b55d1bb55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735504"
---
# <a name="user-roles-for-change-data-capture-service-for-oracle-by-attunity"></a><span data-ttu-id="23a75-102">Change Data Capture Service for Oracle by Attunity에 대한 사용자 역할</span><span class="sxs-lookup"><span data-stu-id="23a75-102">User Roles for Change Data Capture Service for Oracle by Attunity</span></span>
  <span data-ttu-id="23a75-103">이 섹션에서는 Attunity Oracle CDC Service의 사용자 역할에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-103">This section describes the user roles for the Change Data Capture Service for Oracle by Attunity.</span></span> <span data-ttu-id="23a75-104">여기서 설명하는 역할은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 역할, Windows 역할 또는 Oracle 데이터베이스 역할입니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-104">The roles described are [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database roles, Windows roles, or Oracle database roles.</span></span>  
  
## <a name="windows-user-roles"></a><span data-ttu-id="23a75-105">Windows 사용자 역할</span><span class="sxs-lookup"><span data-stu-id="23a75-105">Windows User Roles</span></span>  
 <span data-ttu-id="23a75-106">다음에서는 Oracle CDC Service에서 사용하는 Windows 사용자 역할에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-106">The following describes the Windows user roles used by the Oracle CDC Service.</span></span>  
  
### <a name="computer-administrator-oracle-cdc-service"></a><span data-ttu-id="23a75-107">컴퓨터 관리자: Oracle CDC Service</span><span class="sxs-lookup"><span data-stu-id="23a75-107">Computer Administrator: Oracle CDC Service</span></span>  
 <span data-ttu-id="23a75-108">컴퓨터 관리자는 컴퓨터에서 CDC Service를 만들고 유지 관리하는 작업을 담당하는 Windows 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-108">The computer administrator is a Windows user responsible for creating and maintaining the CDC Service on the computer.</span></span> <span data-ttu-id="23a75-109">이 사용자는 로컬 컴퓨터 관리자 그룹에 속해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-109">This user must belong to the group of local machine administrators.</span></span>  
  
 <span data-ttu-id="23a75-110">Oracle CDC Service 컴퓨터 관리자가 수행하는 태스크는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-110">The tasks performed by the Oracle CDC Service Computer Administrator include:</span></span>  
  
-   <span data-ttu-id="23a75-111">Oracle CDC Service 소프트웨어 설치</span><span class="sxs-lookup"><span data-stu-id="23a75-111">Installing the CDC Service for Oracle software</span></span>  
  
-   <span data-ttu-id="23a75-112">Oracle CDC Windows 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="23a75-112">Creating an Oracle CDC Windows service</span></span>  
  
-   <span data-ttu-id="23a75-113">대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대한 CDC Service 연결 설정(연결 문자열 및 자격 증명)</span><span class="sxs-lookup"><span data-stu-id="23a75-113">Setting up the CDC Service connection to the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance (connection string and credentials)</span></span>  
  
-   <span data-ttu-id="23a75-114">Oracle 로그 마이닝 자격 증명을 보호하는 CDC Service 마스터 암호 확인</span><span class="sxs-lookup"><span data-stu-id="23a75-114">Ensuring that the CDC Service Master Password with which Oracle log mining credentials are protected</span></span>  
  
-   <span data-ttu-id="23a75-115">CDC Service Windows 서비스 삭제</span><span class="sxs-lookup"><span data-stu-id="23a75-115">Deleting a CDC Service Windows service</span></span>  
  
-   <span data-ttu-id="23a75-116">Oracle CDC Service 소프트웨어 제거</span><span class="sxs-lookup"><span data-stu-id="23a75-116">Uninstalling the CDC Service for Oracle software</span></span>  
  
-   <span data-ttu-id="23a75-117">Oracle CDC Service 소프트웨어 유지 관리(예: 업데이트 설치)</span><span class="sxs-lookup"><span data-stu-id="23a75-117">Maintaining the CDC Service for Oracle software (for example, installing updates)</span></span>  
  
-   <span data-ttu-id="23a75-118">CDC Service Windows 서비스 시작 및 중지</span><span class="sxs-lookup"><span data-stu-id="23a75-118">Starting and stopping a CDC Service Windows service</span></span>  
  
 <span data-ttu-id="23a75-119">Microsoft 장애 조치(failover) 클러스터와 같은 고가용성 구성에서 작업하는 경우 컴퓨터 관리자에게 다음과 같은 추가 책임과 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-119">When working with high-availability configurations, such as Microsoft failover clusters, the computer administrator must have additional responsibilities and permissions such as:</span></span>  
  
-   <span data-ttu-id="23a75-120">모든 클러스터 노드에서 Oracle CDC Service 소프트웨어 설치 및 유지 관리</span><span class="sxs-lookup"><span data-stu-id="23a75-120">Installation and maintenance of the CDC Service for Oracle software on all cluster nodes.</span></span>  
  
-   <span data-ttu-id="23a75-121">다양한 클러스터 노드에서 CDC Service의 Windows 서비스에 대한 일반 클러스터 서비스 리소스 정의</span><span class="sxs-lookup"><span data-stu-id="23a75-121">Defining generic cluster service resources for the CDC Service' Windows service on the various cluster nodes.</span></span>  
  
-   <span data-ttu-id="23a75-122">Oracle CDC Service가 설치되는 컴퓨터에서 관리자로 승인된 컴퓨터 관리자 역할 수행.</span><span class="sxs-lookup"><span data-stu-id="23a75-122">Acting as the computer administrator authorized as an administrator on the computer where the CDC Service for Oracle is installed.</span></span> <span data-ttu-id="23a75-123">이 관리자는 Oracle CDC Service를 설치하고 CDC Service 구성 콘솔을 사용하여 로컬 컴퓨터에서 Oracle CDC Service를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-123">This person installs the CDC Service for Oracle and uses the CDC Service Configuration Console to configure a CDC Service for Oracle on a local computer.</span></span>  
  
### <a name="service-account-oracle-cdc-service"></a><span data-ttu-id="23a75-124">서비스 계정: Oracle CDC Service</span><span class="sxs-lookup"><span data-stu-id="23a75-124">Service Account: Oracle CDC Service</span></span>  
 <span data-ttu-id="23a75-125">이 Oracle CDC Service Windows 서비스 계정은 Oracle CDC Service를 실행하는 데 사용하는 Windows 계정입니다(서비스 계정).</span><span class="sxs-lookup"><span data-stu-id="23a75-125">This is Oracle CDC Service Windows Service Account is a Windows account used for running the Oracle CDC Service (the Service Account).</span></span>  
  
 <span data-ttu-id="23a75-126">서비스 계정에 필요한 유일한 필수 권한은 Oracle 클라이언트와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 공급자를 사용할 수 있는 권한입니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-126">The only required privilege necessary for the service account is to be able to use the Oracle client and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native client ODBC provider.</span></span> <span data-ttu-id="23a75-127">이 계정은 특정 공급자에 필요하지 않은 한 파일에 액세스할 필요가 없습니다. 예를 들어, Oracle 클라이언트 연결 문자열이 **tnsnames.ora** 파일의 Oracle 데이터베이스 인스턴스를 참조하는 경우 서비스 계정은 해당 파일에 읽기 액세스 가능해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-127">This account does not need to access files unless required by specific providers (for example, if the Oracle client connection string references Oracle database instances in a **tnsnames.ora** file, then that file must be read-accessible to the service account).</span></span>  
  
 <span data-ttu-id="23a75-128">Windows Vista 또는 Windows Server 2008에서 Oracle CDC Service를 만드는 경우 기본 서비스 계정은 NETWORK SERVICE 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-128">When creating an Oracle CDC Service on Windows Vista or Windows Server 2008, the default service account is the NETWORK SERVICE account.</span></span>  
  
 <span data-ttu-id="23a75-129">Windows 7, Windows Server 2008 R2 이상에서 기본 서비스 계정은 NT Service\\<service-name>입니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-129">On Windows 7, Windows Server 2008 R2 and later, the default service account is NT Service\\<service-name>.</span></span>  
  
 <span data-ttu-id="23a75-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 다른 컴퓨터에서 실행되거나 클러스터형 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스이고 여기서 서비스가 Windows 인증을 사용하여 대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결해야 하는 경우 서비스 계정은 도메인 계정이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-130">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] runs on another machine or is a clustered [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance and there the service needs to connect to the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Windows authentication, then the service account should be a domain account.</span></span>  
  
## <a name="sql-server-user-roles"></a><span data-ttu-id="23a75-131">SQL Server 사용자 역할</span><span class="sxs-lookup"><span data-stu-id="23a75-131">SQL Server User Roles</span></span>  
 <span data-ttu-id="23a75-132">다음에서는 Oracle CDC Service에서 사용하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자 역할에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-132">The following describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user roles used by the Oracle CDC Service.</span></span>  
  
### <a name="oracle-cdc-service-administrator"></a><span data-ttu-id="23a75-133">Oracle CDC Service 관리자</span><span class="sxs-lookup"><span data-stu-id="23a75-133">Oracle CDC Service Administrator</span></span>  
 <span data-ttu-id="23a75-134">CDC Service 관리자는 대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 Oracle CDC Service 아티팩트를 완전히 제어할 수 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-134">The CDC Service Administrator is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user with full control over the Oracle CDC Service artifacts in the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="23a75-135">CDC Service 관리자는 Oracle CDC Designer 콘솔을 사용하여 Oracle CDC 인스턴스를 디자인합니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-135">The CDC Service Administrator uses the Oracle CDC Designer Console to design Oracle CDC Instances.</span></span>  
  
 <span data-ttu-id="23a75-136">CDC Service 관리자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 고정 서버 역할 **public** 및 **dbcreator**를 부여받아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-136">The CDC Service Administrator should be granted the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fixed server roles **public** and **dbcreator**.</span></span>  
  
 <span data-ttu-id="23a75-137">CDC Service 관리자가 수행하는 태스크는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-137">The tasks performed by the CDC Service Administrator include:</span></span>  
  
-   <span data-ttu-id="23a75-138">Oracle CDC 인스턴스( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스)를 호스트하기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 준비.</span><span class="sxs-lookup"><span data-stu-id="23a75-138">Preparing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to host Oracle CDC Instances (which are [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases).</span></span> <span data-ttu-id="23a75-139">이 태스크에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 MSXDBCDC라는 특수 데이터베이스가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-139">In this task, a special database called MSXDBCDC is created in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="23a75-140">Oracle CDC 인스턴스 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 만들기.</span><span class="sxs-lookup"><span data-stu-id="23a75-140">Creating an Oracle CDC Instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="23a75-141">태스크에는 새로 만든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스를 CDC에 대해 활성화하는 작업이 포함되며 이 작업에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템 관리자(**sysadmin**)가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-141">Task includes enabling the newly created [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database for CDC, which requires a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator (**sysadmin**).</span></span>  
  
-   <span data-ttu-id="23a75-142">Oracle CDC 인스턴스 디자인.</span><span class="sxs-lookup"><span data-stu-id="23a75-142">Designing an Oracle CDC Instance.</span></span> <span data-ttu-id="23a75-143">이 태스크에는 원본 Oracle 데이터베이스 및 캡처된 테이블에 대한 정보를 제공하는 작업이 포함되며 이 작업에는 Oracle 데이터베이스 관리자가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-143">This task includes providing information about the source Oracle database and captured tables, which requires an Oracle database administrator.</span></span>  
  
-   <span data-ttu-id="23a75-144">캡처 인스턴스 추가/제거 및 구성 업데이트를 비롯하여 시간 경과에 따른 Oracle CDC 인스턴스 유지 관리</span><span class="sxs-lookup"><span data-stu-id="23a75-144">Maintaining the Oracle CDC Instance over time, which includes adding/removing capture instances and updating configuration.</span></span>  
  
-   <span data-ttu-id="23a75-145">Oracle CDC 인스턴스 활성화 또는 비활성화</span><span class="sxs-lookup"><span data-stu-id="23a75-145">Enabling or disabling an Oracle CDC Instance.</span></span>  
  
-   <span data-ttu-id="23a75-146">Oracle CDC 인스턴스의 상태 모니터링</span><span class="sxs-lookup"><span data-stu-id="23a75-146">Monitoring the state of an Oracle CDC Instance.</span></span>  
  
-   <span data-ttu-id="23a75-147">Oracle CDC 인스턴스에 영향을 주는 문제 해결</span><span class="sxs-lookup"><span data-stu-id="23a75-147">Troubleshooting issues that affect the Oracle CDC Instance.</span></span>  
  
 <span data-ttu-id="23a75-148">CDC Service 관리자는 최소한 처음에는 Oracle CDC 인스턴스와 연결된 **CDC 데이터베이스의** db_owner [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 고정 데이터베이스 역할에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-148">The CDC Service Administrator is, at least initially, in the **db_owner** fixed database role for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC database associated with the Oracle CDC Instance.</span></span> <span data-ttu-id="23a75-149">이 역할은 CDC 데이터베이스에 저장된 변경 데이터에 대한 CDC Service 관리자 액세스 권한을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-149">This gives the CDC Service Administrator access to the change data stored in the CDC database.</span></span> <span data-ttu-id="23a75-150">역할을 만든 후에는 **인스턴스 준비 및 다른 Oracle CDC 인스턴스 만들기를 제외하고 위에 나열된 모든 태스크를 수행할 수 있는 다른 사용자에게 CDC 데이터베이스의** db_owner [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 역할을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-150">Once created, the **db_owner** role of the CDC database can be assigned to a different user who can carry out all of the tasks listed above except for preparing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance and creating another Oracle CDC Instance).</span></span>  
  
 <span data-ttu-id="23a75-151">CDC Service 관리자는 Oracle CDC Windows 서비스 생성 시 지정되는 마스터 암호를 알 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-151">The CDC Service Administrator does not need to know the master password specified with the creation of the Oracle CDC Windows service.</span></span>  
  
### <a name="system-administrator"></a><span data-ttu-id="23a75-152">시스템 관리자</span><span class="sxs-lookup"><span data-stu-id="23a75-152">System Administrator</span></span>  
 <span data-ttu-id="23a75-153">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템 관리자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자이며 Oracle CDC Service와 연결된 **인스턴스에서 고정 서버** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 역할을 부여받아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-153">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user and should be granted the fixed server **sysadmin** role on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance associated with the Oracle CDC Service(s).</span></span>  
  
 <span data-ttu-id="23a75-154">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템 관리자가 수행하는 Oracle CDC에 특정한 태스크는 단 하나이며 이 태스크는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC용 Oracle CDC 인스턴스에 대해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스를 활성화하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-154">There is only one Oracle CDC specific task that carried out with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] System Administrator and that is to enable the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database for an Oracle CDC Instance for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC.</span></span> <span data-ttu-id="23a75-155">이 태스크는 새 Oracle CDC 인스턴스를 만들 때 Oracle CDC Designer 콘솔을 사용하여 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-155">This task is performed using the Oracle CDC Designer console when creating a new Oracle CDC Instance.</span></span>  
  
### <a name="oracle-cdc-service-user"></a><span data-ttu-id="23a75-156">Oracle CDC Service 사용자</span><span class="sxs-lookup"><span data-stu-id="23a75-156">Oracle CDC Service User</span></span>  
 <span data-ttu-id="23a75-157">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Service 사용자는 Oracle CDC Service에서 MSXDBCDC 및 이 서비스에서 처리되는 모든 Oracle CDC 인스턴스(CDC 데이터베이스)에 대한 작업을 수행하는 데 사용하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인입니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-157">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Service user is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login which is used by the Oracle CDC Service to perform its work against the MSXDBCDC and all of the Oracle CDC Instances (CDC databases) handled by this service.</span></span>  
  
 <span data-ttu-id="23a75-158">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Service 사용자는 다음을 부여받아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-158">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Service user should be granted the following:</span></span>  
  
-   <span data-ttu-id="23a75-159">서버에서 처리되는 모든 CDC 데이터베이스에 대한 고정 데이터베이스 역할 **db_dlladmin**, **db_datareader**및 **db_datawriter** 의 멤버</span><span class="sxs-lookup"><span data-stu-id="23a75-159">Member of the fixed database roles **db_dlladmin**, **db_datareader**, and **db_datawriter** for all CDC databases handled by the server.</span></span>  
  
-   <span data-ttu-id="23a75-160">MSXDBCDC 데이터베이스에 대한 고정 데이터베이스 역할 **db_datareader** 및 **db_datawriter** 의 멤버</span><span class="sxs-lookup"><span data-stu-id="23a75-160">Member of the fixed database roles **db_datareader** and **db_datawriter** for the MSXDBCDC database.</span></span>  
  
 <span data-ttu-id="23a75-161">Oracle CDC Service는 단일 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 사용하여 모든 CDC 데이터베이스와 MSXDBCDC 데이터베이스에 대해 작업하므로 이러한 모든 데이터베이스에서 이 로그인을 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-161">Because the Oracle CDC Service uses a single [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to work with all CDC databases and the MSXDBCDC database, this login should be mapped in all of these databases.</span></span>  
  
### <a name="oracle-cdc-change-consumer"></a><span data-ttu-id="23a75-162">Oracle CDC 변경 소비자</span><span class="sxs-lookup"><span data-stu-id="23a75-162">Oracle CDC Change Consumer</span></span>  
 <span data-ttu-id="23a75-163">Oracle CDC 변경 소비자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC 인스턴스 데이터베이스의 CDC 테이블에 저장된 변경 내용을 사용하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-163">The Oracle CDC Change Consumer is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user that consumes changes stored in the CDC tables in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Instance database.</span></span>  
  
 <span data-ttu-id="23a75-164">이 사용자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC 인프라에서 생성된 CDC 기능을 통해 각 CDC 테이블에 액세스하는 데 필요한 사용자 역할을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-164">This user determines the user role that is required for accessing each of the CDC tables through the CDC functions generated by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC infrastructure.</span></span> <span data-ttu-id="23a75-165">캡처 인스턴스를 지정할 때 사용자 역할을 지정하지 않으면 변경 내용에 대한 액세스는 CDC 데이터베이스의 **db_owner** 고정 데이터베이스 역할의 멤버로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-165">If no user role is specified when a capture instance is specified, access to the changes is limited to the member of the **db_owner** fixed database role of the CDC database.</span></span>  
  
## <a name="oracle-user-roles"></a><span data-ttu-id="23a75-166">Oracle 사용자 역할</span><span class="sxs-lookup"><span data-stu-id="23a75-166">Oracle User Roles</span></span>  
 <span data-ttu-id="23a75-167">다음에서는 Oracle CDC Service에서 사용하는 Oracle 사용자 역할에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-167">The following describes the Oracle user roles used by the Oracle CDC Service.</span></span>  
  
### <a name="database-administrator-dba"></a><span data-ttu-id="23a75-168">데이터베이스 관리자(DBA)</span><span class="sxs-lookup"><span data-stu-id="23a75-168">Database Administrator (DBA)</span></span>  
 <span data-ttu-id="23a75-169">Oracle 데이터베이스 관리자(DBA)는 Oracle 데이터베이스 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-169">The Oracle database administrator (DBA) is an Oracle database user.</span></span> <span data-ttu-id="23a75-170">Oracle DBA가 수행하는 태스크는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-170">The tasks performed by the Oracle DBA include:</span></span>  
  
-   <span data-ttu-id="23a75-171">ARCHIVELOG 모드에서 작동하도록 원본 Oracle 데이터베이스 설정</span><span class="sxs-lookup"><span data-stu-id="23a75-171">Setting the source Oracle database to work in ARCHIVELOG mode.</span></span>  
  
-   <span data-ttu-id="23a75-172">필요한 권한을 갖춘 로그 마이닝 사용자 설정</span><span class="sxs-lookup"><span data-stu-id="23a75-172">Setting up a log mining user with the required permissions.</span></span>  
  
-   <span data-ttu-id="23a75-173">캡처된 테이블에 대한 보완 로깅 설정</span><span class="sxs-lookup"><span data-stu-id="23a75-173">Setting supplemental logging for captured tables.</span></span>  
  
-   <span data-ttu-id="23a75-174">더 이상 사용할 수 없는 보관된 트랜잭션 로그 파일을 처리할 수 있도록 복원</span><span class="sxs-lookup"><span data-stu-id="23a75-174">Helping to restore archived transaction log files no longer available so they can be processed.</span></span>  
  
 <span data-ttu-id="23a75-175">Oracle 데이터베이스 관리자는 실행해야 할 Oracle SQL 스크립트를 얻을 수 있으므로 스크립트를 실행하기 전에 평가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-175">The Oracle database administrator can get Oracle SQL scripts that need to run so they can be evaluated before running them.</span></span> <span data-ttu-id="23a75-176">Oracle 데이터베이스 관리자는 Oracle CDC Designer 콘솔에서 Oracle SQL 스크립트를 직접 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-176">The Oracle database administrator can also directly run Oracle SQL scripts from the Oracle CDC Designer console.</span></span>  
  
 <span data-ttu-id="23a75-177">Oracle 데이터베이스 관리자가 Oracle CDC Designer 콘솔을 사용할 경우 실제 사용된 컨텍스트(대화 상자)를 제외하고 관리자의 자격 증명이 유지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-177">If the Oracle database administrator chooses to use the Oracle CDC Designer console, administrator's credentials are not kept except for the context (dialog) in which they were used.</span></span>  
  
 <span data-ttu-id="23a75-178">Oracle 데이터베이스 관리자는 Oracle CDC Service 관리자와 협력하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC 인스턴스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-178">The Oracle database administrator works in coordination with the Oracle CDC Service administrator on the configuration of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Instances.</span></span>  
  
### <a name="log-mining-user"></a><span data-ttu-id="23a75-179">로그 마이닝 사용자</span><span class="sxs-lookup"><span data-stu-id="23a75-179">Log Mining User</span></span>  
 <span data-ttu-id="23a75-180">Oracle 로그 마이너 사용자는 Oracle 트랜잭션 로그에 액세스하고 처리하는 데 필요한 권한이 부여된 특수한 Oracle 데이터베이스 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-180">The Oracle Log Miner user is a special Oracle database user that is granted the required privileges for accessing and processing the Oracle transaction logs.</span></span>  
  
 <span data-ttu-id="23a75-181">이 사용자의 자격 증명은 비대칭 키 암호화를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC 인스턴스 데이터베이스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-181">The credentials for this user are stored in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Instance database using asymmetric key encryption.</span></span> <span data-ttu-id="23a75-182">이 자격 증명에는 Oracle CDC Service만 액세스할 수 있으며 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC 인스턴스 데이터베이스 소유자는 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-182">They are accessible only to the Oracle CDC Service but not to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Instance database owner.</span></span>  
  
 <span data-ttu-id="23a75-183">다음 목록에서는 로그 마이닝 사용자에게 부여되어야 할 필수 권한에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-183">The following list describes the required privileges of the log mining user should be granted:</span></span>  
  
-   <span data-ttu-id="23a75-184">\<any-captured-table>에 대한 SELECT 권한</span><span class="sxs-lookup"><span data-stu-id="23a75-184">SELECT on \<any-captured-table></span></span>  
  
-   <span data-ttu-id="23a75-185">SELECT ANY TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="23a75-185">SELECT ANY TRANSACTION</span></span>  
  
-   <span data-ttu-id="23a75-186">DBMS_LOGMNR에 대한 EXECUTE 권한</span><span class="sxs-lookup"><span data-stu-id="23a75-186">EXECUTE on DBMS_LOGMNR</span></span>  
  
-   <span data-ttu-id="23a75-187">V$LOGMNR_CONTENTS에 대한 SELECT 권한</span><span class="sxs-lookup"><span data-stu-id="23a75-187">SELECT on V$LOGMNR_CONTENTS</span></span>  
  
-   <span data-ttu-id="23a75-188">V$ARCHIVED_LOG에 대한 SELECT 권한</span><span class="sxs-lookup"><span data-stu-id="23a75-188">SELECT on V$ARCHIVED_LOG</span></span>  
  
-   <span data-ttu-id="23a75-189">V$LOG에 대한 SELECT 권한</span><span class="sxs-lookup"><span data-stu-id="23a75-189">SELECT on V$LOG</span></span>  
  
-   <span data-ttu-id="23a75-190">V$LOGFILE에 대한 SELECT 권한</span><span class="sxs-lookup"><span data-stu-id="23a75-190">SELECT on V$LOGFILE</span></span>  
  
-   <span data-ttu-id="23a75-191">V$DATABASE에 대한 SELECT 권한</span><span class="sxs-lookup"><span data-stu-id="23a75-191">SELECT on V$DATABASE</span></span>  
  
-   <span data-ttu-id="23a75-192">V$THREAD에 대한 SELECT 권한</span><span class="sxs-lookup"><span data-stu-id="23a75-192">SELECT on V$THREAD</span></span>  
  
-   <span data-ttu-id="23a75-193">V$PARAMETER에 대한 SELECT 권한</span><span class="sxs-lookup"><span data-stu-id="23a75-193">SELECT on V$PARAMETER</span></span>  
  
-   <span data-ttu-id="23a75-194">DBA_REGISTRY에 대한 SELECT 권한</span><span class="sxs-lookup"><span data-stu-id="23a75-194">SELECT on DBA_REGISTRY</span></span>  
  
-   <span data-ttu-id="23a75-195">ALL_INDEXES에 대한 SELECT 권한</span><span class="sxs-lookup"><span data-stu-id="23a75-195">SELECT on ALL_INDEXES</span></span>  
  
-   <span data-ttu-id="23a75-196">ALL_OBJECTS에 대한 SELECT 권한</span><span class="sxs-lookup"><span data-stu-id="23a75-196">SELECT on ALL_OBJECTS</span></span>  
  
-   <span data-ttu-id="23a75-197">DBA_OBJECTS에 대한 SELECT 권한</span><span class="sxs-lookup"><span data-stu-id="23a75-197">SELECT on DBA_OBJECTS</span></span>  
  
-   <span data-ttu-id="23a75-198">ALL_TABLES에 대한 SELECT 권한</span><span class="sxs-lookup"><span data-stu-id="23a75-198">SELECT on ALL_TABLES</span></span>  
  
 <span data-ttu-id="23a75-199">이러한 권한을 V$xxx에 부여할 수 없는 경우 V $xxx에 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-199">If any of these privileges cannot be granted to a V$xxx, then they should be granted to the V $xxx.</span></span>  
  
### <a name="schema-user"></a><span data-ttu-id="23a75-200">스키마 사용자</span><span class="sxs-lookup"><span data-stu-id="23a75-200">Schema User</span></span>  
 <span data-ttu-id="23a75-201">Oracle 스키마 사용자는 캡처할 Oracle 테이블의 스키마에 대해 읽기 액세스 권한이 있는 Oracle 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-201">The Oracle Schema User is an Oracle user with read access to the schema of the Oracle tables to be captured.</span></span> <span data-ttu-id="23a75-202">이 사용자는 Oracle CDC Designer 콘솔에서 작업하면서 Oracle 스키마 목록, 캡처할 테이블과 열, 인덱스 및 키를 검색할 때 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-202">This user is necessary when working with the Oracle CDC Designer console to retrieve the list of Oracle schema, tables to be captured and their columns, indexes and keys.</span></span>  
  
 <span data-ttu-id="23a75-203">이 사용자의 자격 증명은 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-203">The credentials for this user are never stored.</span></span> <span data-ttu-id="23a75-204">CDC Designer 콘솔에서 필요할 때마다 자격 증명을 요청하며 나머지 UI 세션을 위해 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="23a75-204">They are requested by the CDC Designer console each time they are needed and they are kept for the rest of the UI sessions.</span></span>  
  
  
