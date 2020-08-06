---
title: 관리 데이터 웨어하우스 구성(SQL Server Management Studio) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dc.datacollection.wizard_finish.f1
- sql12.swb.dc.datacollection.wizard_maploginuser.f1
- sql12.swb.dc.datacollection.wizard_welcome.f1
- sql12.swb.dc.datacollection.wizard_choosemdw.f1
- sql12.swb.dc.datacollection.wizard_completecfg.f1
- sql12.swb.dc.datacollection.wizard_config.f1
- sql12.swb.dc.datacollection.wizard_createmdw.f1
helpviewer_keywords:
- data warehouse [SQL Server], multiple instances
- data warehouse [SQL Server], configuring
- Configure Management Data Warehouse Wizard
- management data warehouse, configuring
ms.assetid: 23a584f3-c5e1-414c-9afe-73cd7efbda4b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1ef4ddd518343a3076c72ecc41f9b15ddf092dc0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661677"
---
# <a name="configure-the-management-data-warehouse-sql-server-management-studio"></a><span data-ttu-id="6f6c8-102">관리 데이터 웨어하우스 구성(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="6f6c8-102">Configure the Management Data Warehouse (SQL Server Management Studio)</span></span>
  <span data-ttu-id="6f6c8-103">이 항목에서는 데이터 수집기를 사용하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 단일 인스턴스 또는 여러 인스턴스에서 데이터 스토리지를 지원하도록 관리 데이터 웨어하우스를 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-103">This topic describes how to configure the management data warehouse to support data storage on a single instance or multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are using the data collector.</span></span> <span data-ttu-id="6f6c8-104">이러한 인스턴스는 같은 서버에 있거나 다른 서버에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-104">These instances can be on the same server or on different servers.</span></span> <span data-ttu-id="6f6c8-105">그리고 [데이터 관리 웨어하우스 구성 마법사](#Wizard) 대화 상자의 사용자 인터페이스에 대해서도 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-105">This topic also provides descriptions of the user interface for the [Configure Data Management Warehouse Wizard](#Wizard) dialog box.</span></span> <span data-ttu-id="6f6c8-106">데이터 수집기 구성에 대한 자세한 내용은 [Configure Properties of a Data Collector](configure-properties-of-a-data-collector.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-106">For information about configuring a data collector, see [Configure Properties of a Data Collector](configure-properties-of-a-data-collector.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f6c8-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 시스템 서비스 계정(로컬 시스템, 네트워크 서비스 또는 로컬 서비스) 중 하나를 사용하여 실행되도록 구성되고 관리 데이터 웨어하우스는 데이터 수집기와 다른 인스턴스에서 생성될 경우 관리 데이터 웨어하우스에 데이터를 업로드하는 데 프록시를 사용하도록 컬렉션 집합을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-107">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is configured to run using one of the System service accounts (Local System, Network Service, or Local Service), and the management data warehouse is created on a different instance from the data collector, you must configure collection sets to use a proxy for uploading data to the management data warehouse.</span></span>  
  
### <a name="configure-the-management-data-warehouse-on-a-single-instance-or-multiple-instances-of-ssnoversion"></a><span data-ttu-id="6f6c8-108">다음 단일 인스턴스 또는 여러 인스턴스에서 관리 데이터 웨어하우스 구성: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f6c8-108">Configure the management data warehouse on a single instance or multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
1.  <span data-ttu-id="6f6c8-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 실행 중인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-109">Ensure that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is running.</span></span>  
  
2.  <span data-ttu-id="6f6c8-110">개체 탐색기에서 **관리** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-110">In Object Explorer, expand the **Management** node.</span></span>  
  
3.  <span data-ttu-id="6f6c8-111">**데이터 컬렉션**을 마우스 오른쪽 단추로 클릭한 다음 **태스크**를 확장하고 **관리 데이터 웨어하우스 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-111">Right-click **Data Collection**, expand **Tasks**, and then click **Configure Management Data Warehouse**.</span></span>  
  
4.  <span data-ttu-id="6f6c8-112">[관리 데이터 웨어하우스 구성 마법사](#Wizard) 를 사용하여 관리 데이터 웨어하우스를 만들고, 로그인을 구성하며, 데이터 컬렉션을 활성화하고, **시스템 데이터 컬렉션 집합**을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-112">Use the [Configure Management Data Warehouse Wizard](#Wizard) to create a management data warehouse, configure logins, enable data collection, and start the **System Data Collection Sets**.</span></span>  
  
     <span data-ttu-id="6f6c8-113">여러 인스턴스를 구성하려면 5단계를 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-113">To configure multiple instances, continue with step 5.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6f6c8-114">데이터 수집기가 동일한 관리 데이터 웨어하우스를 사용하는 여러 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 설치되어 있는 배포 환경에서 프록시를 사용하는 것이 최선의 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-114">It is considered best practice to use proxies in deployments where the data collector is installed on multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are using the same management data warehouse.</span></span>  
  
5.  <span data-ttu-id="6f6c8-115">다른 인스턴스에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 열고 다음 작업 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-115">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] on another instance and do either of the following:</span></span>  
  
    -   <span data-ttu-id="6f6c8-116">구성 관리 데이터 웨어하우스 마법사를 사용하여 기존 관리 데이터 웨어하우스의 데이터 컬렉션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-116">Use the Configure Management Data Warehouse wizard to configure data collection for the existing management data warehouse.</span></span>  
  
    -   <span data-ttu-id="6f6c8-117">**데이터 컬렉션**을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-117">Right-click **Data Collection**, and then click **Properties**.</span></span> <span data-ttu-id="6f6c8-118">**일반** 탭에서 기존 관리 데이터 웨어하우스와 이 관리 데이터 웨어하우스가 설치된 서버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-118">On the **General** tab, specify the existing management data warehouse and the server that it is installed on.</span></span>  
  
6.  <span data-ttu-id="6f6c8-119">데이터 수집기를 사용하는 데이터베이스 인스턴스가 모두 구성되어 공유 관리 데이터 웨어하우스에 데이터를 업로드할 때까지 5단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-119">Repeat step 5 until all the database instances that use the data collector are configured to upload data to the shared management data warehouse.</span></span>  
  
####  <a name="configure-management-data-warehouse-wizard"></a><a name="Wizard"></a> <span data-ttu-id="6f6c8-120">관리 데이터 웨어하우스 구성 마법사</span><span class="sxs-lookup"><span data-stu-id="6f6c8-120">Configure Management Data Warehouse Wizard</span></span>  
 <span data-ttu-id="6f6c8-121">**시작 페이지**</span><span class="sxs-lookup"><span data-stu-id="6f6c8-121">**Welcome Page**</span></span>  
  
 <span data-ttu-id="6f6c8-122">시작 페이지는 데이터 컬렉션 구성 마법사의 첫 페이지입니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-122">The Welcome page is the starting page of the Configure Data Collection Wizard.</span></span> <span data-ttu-id="6f6c8-123">이 페이지의 표시 여부는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-123">Displaying this page is optional.</span></span>  
  
 <span data-ttu-id="6f6c8-124">**이 시작 페이지를 다시 표시 안 함**</span><span class="sxs-lookup"><span data-stu-id="6f6c8-124">**Do not show this starting page again.**</span></span>  
 <span data-ttu-id="6f6c8-125">다음에 데이터 컬렉션 구성 마법사를 시작할 때 이 페이지를 표시하지 않으려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-125">Select to suppress this page the next time you launch the Configure Data Collection Wizard.</span></span>  
  
 <span data-ttu-id="6f6c8-126">**관리 데이터 웨어하우스 스토리지 구성 페이지**</span><span class="sxs-lookup"><span data-stu-id="6f6c8-126">**Configure Management Data Warehouse Storage Page**</span></span>  
  
 <span data-ttu-id="6f6c8-127">이 페이지를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 서버 및 관리 데이터 웨어하우스를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-127">Use this page to select a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database server and management data warehouse.</span></span> <span data-ttu-id="6f6c8-128">관리 데이터 웨어하우스는 수집된 데이터를 보관하는 관계형 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-128">The management data warehouse is a relational database that will store collected data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f6c8-129">서버에 관리 데이터 웨어하우스를 만들려면 적절한 수준의 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-129">You must have the appropriate level of permissions in order to create the management data warehouse on the server.</span></span> <span data-ttu-id="6f6c8-130">자세한 내용은 [CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-130">For more information, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span> <span data-ttu-id="6f6c8-131">또한 관리 데이터 웨어하우스 역할에 대한 로그인을 만들려는 경우에도 적절한 수준의 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-131">You also must have the appropriate level of permissions to create logins for management data warehouse roles.</span></span>  
  
 <span data-ttu-id="6f6c8-132">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="6f6c8-132">**Server name**</span></span>  
 <span data-ttu-id="6f6c8-133">관리 데이터 웨어하우스를 호스팅할 서버의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-133">Specifies the name of the server that will host the management data warehouse.</span></span>  
  
 <span data-ttu-id="6f6c8-134">관리 데이터 웨어하우스를 구성할 때 **서버 이름** 은 항상 로컬 서버의 이름이며 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-134">When configuring a management data warehouse, **Server name** is always the name of the local server and cannot be modified.</span></span>  
  
 <span data-ttu-id="6f6c8-135">**데이터베이스 이름**</span><span class="sxs-lookup"><span data-stu-id="6f6c8-135">**Database name**</span></span>  
 <span data-ttu-id="6f6c8-136">수집된 데이터를 보관할 관계형 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-136">Specifies the relational database that will store collected data.</span></span> <span data-ttu-id="6f6c8-137">목록을 사용하여 기존 데이터베이스를 선택하거나 **새로 만들기** 를 클릭하여 **새 데이터베이스** 대화 상자를 통해 새 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-137">Use the list to select an existing database or click **New** to create a new database using the **New Database** dialog.</span></span>  
  
 <span data-ttu-id="6f6c8-138">**새로 만들기** 옵션은 데이터 컬렉션 집합을 구성할 때만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-138">The **New** option is available only when configuring a data collection set</span></span>  
  
 <span data-ttu-id="6f6c8-139">**로그인 및 사용자 매핑 페이지**</span><span class="sxs-lookup"><span data-stu-id="6f6c8-139">**Map Logins and Users Page**</span></span>  
  
 <span data-ttu-id="6f6c8-140">이 페이지를 사용하여 관리 데이터 웨어하우스에 대한 데이터베이스 사용자 역할에 로그인을 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-140">Use this page to map logins to database user roles for the management data warehouse.</span></span>  
  
 <span data-ttu-id="6f6c8-141">**이 로그인으로 매핑된 사용자**</span><span class="sxs-lookup"><span data-stu-id="6f6c8-141">**Users mapped to this login**</span></span>  
 <span data-ttu-id="6f6c8-142">관리 데이터 웨어하우스를 호스팅할 서버에 있는 기존 로그인을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-142">Displays the existing logins on the server that will host the management data warehouse.</span></span> <span data-ttu-id="6f6c8-143">각 행에는 편집 가능한 **매핑** 확인란, **로그인** 이름 및 로그인 **유형** 이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-143">Each row contains an editable **Map** check box, a **Login** name, and a **Type** of login.</span></span>  
  
 <span data-ttu-id="6f6c8-144">로그인에 대한 **매핑** 확인란을 선택하여 로그인을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-144">Specify a login by selecting the **Map** checkbox for the login.</span></span>  
  
 <span data-ttu-id="6f6c8-145">**데이터베이스 역할 멤버 자격:**  *\<data warehouse name>*</span><span class="sxs-lookup"><span data-stu-id="6f6c8-145">**Database role membership for:**  *\<data warehouse name>*</span></span>  
 <span data-ttu-id="6f6c8-146">다음 중 하나 이상의 옵션 옆에 있는 확인란을 클릭하여 로그인이 매핑되는 관리 데이터 웨어하우스 역할을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-146">Select the management data warehouse role that the login is mapped to by clicking the checkbox by one or more of the following options:</span></span>  
  
-   <span data-ttu-id="6f6c8-147">**mdw_admin**</span><span class="sxs-lookup"><span data-stu-id="6f6c8-147">**mdw_admin**</span></span>  
  
-   <span data-ttu-id="6f6c8-148">**mdw_reader**</span><span class="sxs-lookup"><span data-stu-id="6f6c8-148">**mdw_reader**</span></span>  
  
-   <span data-ttu-id="6f6c8-149">**mdw_writer**</span><span class="sxs-lookup"><span data-stu-id="6f6c8-149">**mdw_writer**</span></span>  
  
 <span data-ttu-id="6f6c8-150">**새 로그인**</span><span class="sxs-lookup"><span data-stu-id="6f6c8-150">**New Login**</span></span>  
 <span data-ttu-id="6f6c8-151">**로그인 - 신규** 대화 상자를 열고 관리 데이터 웨어하우스에 대한 새 로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-151">Open the **Login - New** dialog box and create a new login for the management data warehouse.</span></span>  
  
 <span data-ttu-id="6f6c8-152">**마법사 완료 페이지**</span><span class="sxs-lookup"><span data-stu-id="6f6c8-152">**Complete the Wizard Page**</span></span>  
  
 <span data-ttu-id="6f6c8-153">이 페이지를 사용하여 데이터 컬렉션 구성을 확인하고 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-153">Use this page to verify and complete data collection configuration.</span></span> <span data-ttu-id="6f6c8-154">보기 창에 표시된 트리는 **마침**을 클릭할 때 적용되는 구성과 발생하는 동작을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-154">The tree displayed in the viewing window shows what configurations will applied as well as what actions will take place when you click **Finish**.</span></span>  
  
 <span data-ttu-id="6f6c8-155">**데이터 컬렉션 구성 마법사 진행률 페이지**</span><span class="sxs-lookup"><span data-stu-id="6f6c8-155">**Configure Data Collection Wizard Progress Page**</span></span>  
  
 <span data-ttu-id="6f6c8-156">이 페이지를 사용하여 각 구성 단계의 결과를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-156">Use this page to view the results of each configuration step.</span></span>  
  
 <span data-ttu-id="6f6c8-157">**세부 정보**</span><span class="sxs-lookup"><span data-stu-id="6f6c8-157">**Details**</span></span>  
 <span data-ttu-id="6f6c8-158">각 구성 단계를 **자세히** 표에서 행으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-158">Displays each configuration step as a row in the **Details** grid.</span></span> <span data-ttu-id="6f6c8-159">각 행에는 단계를 설명하는 **동작** 열과 단계의 성공 여부를 나타내는 **상태** 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-159">Each row contains an **Action** column that describes the step, and a **Status** column that indicates the success or failure of the step.</span></span> <span data-ttu-id="6f6c8-160">오류가 있으면 **메시지** 열에 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-160">If there is an error, a message appears in the **Message** column.</span></span>  
  
 <span data-ttu-id="6f6c8-161">**중지**</span><span class="sxs-lookup"><span data-stu-id="6f6c8-161">**Stop**</span></span>  
 <span data-ttu-id="6f6c8-162">마법사 진행을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-162">Stop wizard processing.</span></span>  
  
 <span data-ttu-id="6f6c8-163">**Report**</span><span class="sxs-lookup"><span data-stu-id="6f6c8-163">**Report**</span></span>  
 <span data-ttu-id="6f6c8-164">데이터 컬렉션 구성에 대한 보고서를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-164">View a report of the data collection configuration.</span></span> <span data-ttu-id="6f6c8-165">다음과 같은 보고서 옵션이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-165">The following report options are provided:</span></span>  
  
-   <span data-ttu-id="6f6c8-166">보고서 보기</span><span class="sxs-lookup"><span data-stu-id="6f6c8-166">View Report</span></span>  
  
-   <span data-ttu-id="6f6c8-167">보고서를 파일로 저장</span><span class="sxs-lookup"><span data-stu-id="6f6c8-167">Save Report to File</span></span>  
  
-   <span data-ttu-id="6f6c8-168">클립보드에 보고서 복사</span><span class="sxs-lookup"><span data-stu-id="6f6c8-168">Copy Report to Clipboard</span></span>  
  
-   <span data-ttu-id="6f6c8-169">보고서를 전자 메일로 보내기</span><span class="sxs-lookup"><span data-stu-id="6f6c8-169">Send Report as E-mail</span></span>  
  
 <span data-ttu-id="6f6c8-170">**닫기**</span><span class="sxs-lookup"><span data-stu-id="6f6c8-170">**Close**</span></span>  
 <span data-ttu-id="6f6c8-171">마법사를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6c8-171">Close the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f6c8-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6f6c8-172">See Also</span></span>  
 <span data-ttu-id="6f6c8-173">[sp_syscollector_enable_collector&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6f6c8-173">[sp_syscollector_enable_collector &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql) </span></span>  
 <span data-ttu-id="6f6c8-174">[sp_syscollector_disable_collector&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6f6c8-174">[sp_syscollector_disable_collector &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql) </span></span>  
 <span data-ttu-id="6f6c8-175">[데이터 컬렉션](data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="6f6c8-175">[Data Collection](data-collection.md) </span></span>  
 [<span data-ttu-id="6f6c8-176">데이터 컬렉션 관리</span><span class="sxs-lookup"><span data-stu-id="6f6c8-176">Manage Data Collection</span></span>](manage-data-collection.md)  
  
  
