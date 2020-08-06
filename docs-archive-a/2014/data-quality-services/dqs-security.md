---
title: DQS 보안 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 921927f5-1b1e-452a-a79e-c691829fd826
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3da3cdbe746b69c5c4cfe7c7c796827dd74a433c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732059"
---
# <a name="dqs-security"></a><span data-ttu-id="90257-102">DQS 보안</span><span class="sxs-lookup"><span data-stu-id="90257-102">DQS Security</span></span>
  <span data-ttu-id="90257-103">DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] ) 보안 인프라는 SQL Server 보안 인프라를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="90257-103">The [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) security infrastructure is based upon the SQL Server security infrastructure.</span></span> <span data-ttu-id="90257-104">데이터베이스 관리자는 사용자와 DQS 역할을 연결하여 사용자에게 사용 권한 집합을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="90257-104">A database administrator grants a user a set of permissions by associating the user with a DQS role.</span></span> <span data-ttu-id="90257-105">이러한 방식으로 사용자가 액세스할 수 있는 DQS 리소스와 사용자가 수행할 수 있는 기능 작업이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="90257-105">Doing so determines the DQS resources that the user has access to and the functional activities that the user is allowed to perform.</span></span>  
  
## <a name="dqs-roles"></a><span data-ttu-id="90257-106">DQS 역할</span><span class="sxs-lookup"><span data-stu-id="90257-106">DQS Roles</span></span>  
 <span data-ttu-id="90257-107">DQS 역할은 4가지입니다.</span><span class="sxs-lookup"><span data-stu-id="90257-107">There are four roles for DQS.</span></span> <span data-ttu-id="90257-108">하나는 주로 제품 설치, 데이터베이스 유지 관리 및 사용자 관리를 다루는 DBA(데이터베이스 관리자)입니다.</span><span class="sxs-lookup"><span data-stu-id="90257-108">One is the database administrator (DBA) who deals primarily with product installation, database maintenance, and user management.</span></span> <span data-ttu-id="90257-109">이 역할은 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 애플리케이션보다는 주로 SQL Server Management Studio를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="90257-109">This role primarily uses the SQL Server Management Studio, rather than within the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application.</span></span> <span data-ttu-id="90257-110">서버 역할은 sysadmin입니다.</span><span class="sxs-lookup"><span data-stu-id="90257-110">Their server role is sysadmin.</span></span>  
  
 <span data-ttu-id="90257-111">나머지 3개 역할은 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 애플리케이션에서 작업하는 방식으로 제품을 직접 사용하는 정보 근로자, 데이터 관리자입니다.</span><span class="sxs-lookup"><span data-stu-id="90257-111">The three other roles are information workers, data stewards who use the product directly by working in the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application.</span></span> <span data-ttu-id="90257-112">이러한 역할은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="90257-112">These roles include the following:</span></span>  
  
-   <span data-ttu-id="90257-113">**DQS 관리자** (dqs_administrator 역할)는 제품 범위 내에서 모든 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90257-113">The **DQS Administrator** (dqs_administrator role) can do everything in the scope of the product.</span></span> <span data-ttu-id="90257-114">DQS 관리자는 프로젝트 편집 및 실행, 기술 자료 생성 및 편집, 작업 종료, 작업 내 프로세스 중지를 수행할 수 있고 구성 및 참조 Data Services 설정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90257-114">The administrator can edit and execute a project, create and edit a knowledge base, terminate an activity, stop a process within an activity, and can change the configuration and Reference Data Services settings.</span></span> <span data-ttu-id="90257-115">그러나 서버를 설치하거나 새 사용자를 추가할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="90257-115">The DQS Administrator cannot, however, install the server or add new users.</span></span> <span data-ttu-id="90257-116">이러한 작업은 데이터베이스 관리자가 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90257-116">The database administrator must do that.</span></span>  
  
-   <span data-ttu-id="90257-117">**DQS KB 편집자** (dqs_kb_editor 역할)는 관리를 제외한 모든 DQS 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90257-117">The **DQS KB Editor** (dqs_kb_editor role) can perform all of the DQS activities, except for administration.</span></span> <span data-ttu-id="90257-118">KB 편집자는 프로젝트를 편집하고 실행할 수 있고, 기술 자료를 만들고 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90257-118">The KB Editor can edit and execute a project, and create and edit a knowledge base.</span></span> <span data-ttu-id="90257-119">작업 모니터링 데이터를 볼 수는 있지만 특정 작업을 종료 또는 중지하거나 관리상의 임무를 수행할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="90257-119">They can see the activity monitoring data, but cannot terminate or stop an activity or perform administrative duties.</span></span>  
  
-   <span data-ttu-id="90257-120">**DQS KB 운영자** (dqs_kb_operator 역할)는 프로젝트를 편집하고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90257-120">The **DQS KB Operator** (dqs_kb_operator role) can edit and execute a project.</span></span> <span data-ttu-id="90257-121">DQS KB 운영자는 어떠한 유형의 기술 자료 관리도 수행할 수 없습니다. 기술 자료를 만들거나 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="90257-121">They cannot perform any kind of knowledge management; they cannot create or change a knowledge base.</span></span> <span data-ttu-id="90257-122">이 운영자는 작업 모니터링 데이터를 볼 수는 있지만 특정 작업을 종료하거나 관리상의 임무를 수행할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="90257-122">They can see the activity monitoring data, but cannot terminate an activity or perform administrative duties.</span></span>  
  
## <a name="user-management"></a><span data-ttu-id="90257-123">사용자 관리</span><span class="sxs-lookup"><span data-stu-id="90257-123">User Management</span></span>  
 <span data-ttu-id="90257-124">데이터베이스 관리자(DBA)는 SQL Server Management Studio에서 DQS 사용자를 만들어 DQS 역할에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="90257-124">The database administrator (DBA) creates DQS users and associates them with DQS roles in SQL Server Management Studio.</span></span> <span data-ttu-id="90257-125">DBA는 SQL 로그인을 DQS_MAIN 데이터베이스의 사용자로 추가하고 각 사용자를 DQS 역할 중 하나에 연결하는 방식으로 사용자의 사용 권한을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="90257-125">The DBA manages their permissions by adding SQL Logins as users of the DQS_MAIN database, and associating each user with one of the DQS roles.</span></span> <span data-ttu-id="90257-126">각 역할에는 DQS_MAIN 데이터베이스의 저장 프로시저 집합에 대한 사용 권한이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="90257-126">Each role is granted permissions to a set of stored procedures on the DQS_MAIN database.</span></span> <span data-ttu-id="90257-127">DQS_PROJECTS 및 DQS_STAGING_DATA 데이터베이스의 경우 이 세 가지 역할을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="90257-127">The three DQS roles are not available for the DQS_PROJECTS and DQS_STAGING_DATA databases.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="90257-128">관련 작업</span><span class="sxs-lookup"><span data-stu-id="90257-128">Related Tasks</span></span>  
  
|<span data-ttu-id="90257-129">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="90257-129">Task Description</span></span>|<span data-ttu-id="90257-130">항목</span><span class="sxs-lookup"><span data-stu-id="90257-130">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="90257-131">SQL Server Management Studio를 사용하여 사용자를 만들고 DQS 역할을 부여하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="90257-131">Describes how to create a user and grant DQS roles using SQL Server Management Studio.</span></span>|[<span data-ttu-id="90257-132">SSMS에서 DQS 사용자 관리</span><span class="sxs-lookup"><span data-stu-id="90257-132">Manage DQS Users in SSMS</span></span>](../../2014/data-quality-services/manage-dqs-users-in-ssms.md)|  
  
  
