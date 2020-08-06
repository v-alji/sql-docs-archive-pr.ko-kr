---
title: 복제 관리 개체 개념 | Microsoft 문서
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- replication [SQL Server], RMO
- programming interfaces [SQL Server replication]
- replication [SQL Server], how-to topics
- RMO [SQL Server]
- Replication Management Objects
- programming [SQL Server replication], RMO
ms.assetid: 37476d50-fb47-49e3-9504-3b163ac381d8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0dc41416e0fb585db376c6b72f28f7c30cfff052
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650916"
---
# <a name="replication-management-objects-concepts"></a><span data-ttu-id="8b62a-102">Replication Management Objects Concepts</span><span class="sxs-lookup"><span data-stu-id="8b62a-102">Replication Management Objects Concepts</span></span>
  <span data-ttu-id="8b62a-103">RMO(복제 관리 개체)는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 복제 기능을 캡슐화하는 관리 코드 어셈블리로,</span><span class="sxs-lookup"><span data-stu-id="8b62a-103">Replication Management Objects (RMO) is a managed code assembly that encapsulates replication functionalities for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8b62a-104"><xref:Microsoft.SqlServer.Replication> 네임스페이스를 통해 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-104">RMO is implemented by the <xref:Microsoft.SqlServer.Replication> namespace.</span></span>  
  
 <span data-ttu-id="8b62a-105">다음 섹션의 항목에서는 RMO를 사용하여 복제 태스크를 프로그래밍 방식으로 제어하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-105">The topics in the following sections describe how you can use RMO to programmatically control replication tasks:</span></span>  
  
 [<span data-ttu-id="8b62a-106">배포 구성</span><span class="sxs-lookup"><span data-stu-id="8b62a-106">Configure Distribution</span></span>](../configure-distribution.md)  
 <span data-ttu-id="8b62a-107">이 섹션의 항목에서는 RMO를 사용하여 게시 및 배포를 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-107">Topics in this section show how to use RMO to configure publishing and distribution.</span></span>  
  
 [<span data-ttu-id="8b62a-108">게시 만들기</span><span class="sxs-lookup"><span data-stu-id="8b62a-108">Create a Publication</span></span>](../publish/create-a-publication.md)  
 <span data-ttu-id="8b62a-109">이 섹션의 항목에서는 RMO를 사용하여 게시 및 아티클을 작성, 삭제 및 수정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-109">Topics in this section show how to use RMO to create, delete, and modify publications and articles.</span></span>  
  
 [<span data-ttu-id="8b62a-110">게시 구독</span><span class="sxs-lookup"><span data-stu-id="8b62a-110">Subscribe to Publications</span></span>](../subscribe-to-publications.md)  
 <span data-ttu-id="8b62a-111">이 섹션의 항목에서는 RMO를 사용하여 구독을 작성, 삭제 및 수정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-111">Topics in this section show how to use RMO to create, delete, and modify subscriptions.</span></span>  
  
 [<span data-ttu-id="8b62a-112">복제 토폴로지 보안 설정</span><span class="sxs-lookup"><span data-stu-id="8b62a-112">Secure a Replication Topology</span></span>](../security/view-and-modify-replication-security-settings.md)  
 <span data-ttu-id="8b62a-113">이 섹션의 항목에서는 RMO를 사용하여 보안 설정을 보고 수정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-113">Topics in this section show how to use RMO to view and modify security settings.</span></span>  
  
 [<span data-ttu-id="8b62a-114">구독 동기화&#40;복제&#41;</span><span class="sxs-lookup"><span data-stu-id="8b62a-114">Synchronize Subscriptions &#40;Replication&#41;</span></span>](../synchronize-data.md)  
 <span data-ttu-id="8b62a-115">이 섹션의 항목에서는 구독을 동기화하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-115">Topics in this section show how to synchronize subscriptions.</span></span>  
  
 [<span data-ttu-id="8b62a-116">복제 모니터링</span><span class="sxs-lookup"><span data-stu-id="8b62a-116">Monitoring Replication</span></span>](../monitoring-replication.md)  
 <span data-ttu-id="8b62a-117">이 섹션의 항목에서는 프로그래밍 방식으로 복제 토폴로지를 모니터링하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-117">Topics in this section show how to programmatically monitor a replication topology.</span></span>  
  
## <a name="introduction-to-rmo-programming"></a><span data-ttu-id="8b62a-118">RMO 프로그래밍 소개</span><span class="sxs-lookup"><span data-stu-id="8b62a-118">Introduction to RMO Programming</span></span>  
 <span data-ttu-id="8b62a-119">RMO는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 복제의 모든 측면을 프로그래밍하기 위해 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-119">RMO is designed for programming all aspects of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication.</span></span> <span data-ttu-id="8b62a-120">RMO 네임스페이스는 <xref:Microsoft.SqlServer.Replication>이며 이 네임스페이스는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework 어셈블리인 Microsoft.SqlServer.Rmo.dll을 통해 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-120">The RMO namespace is <xref:Microsoft.SqlServer.Replication>, and it is implemented by the Microsoft.SqlServer.Rmo.dll, which is a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework assembly.</span></span> <span data-ttu-id="8b62a-121"><xref:Microsoft.SqlServer.Replication> 네임스페이스에 속하는 Microsoft.SqlServer.Replication.dll 어셈블리는 다양한 복제 에이전트(스냅샷 에이전트, 배포 에이전트 및 병합 에이전트)를 프로그래밍하는 데 필요한 관리되는 코드 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-121">The Microsoft.SqlServer.Replication.dll assembly, which also belongs to the <xref:Microsoft.SqlServer.Replication> namespace, implements a managed code interface for programming the various replication agents (Snapshot Agent, Distribution Agent, and Merge Agent).</span></span> <span data-ttu-id="8b62a-122">이 어셈블리의 클래스는 RMO에서 액세스하여 구독을 동기화하는 데 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-122">Its classes can be accessed from RMO to synchronize subscriptions.</span></span> <span data-ttu-id="8b62a-123">Microsoft.SqlServer.Replication.BusinessLogicSupport.dll 어셈블리를 통해 구현되는 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> 네임스페이스의 클래스는 병합 복제에 대한 사용자 지정 비즈니스 논리를 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-123">Classes in the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> namespace, implemented by the Microsoft.SqlServer.Replication.BusinessLogicSupport.dll assembly, are used to create custom business logic for merge replication.</span></span> <span data-ttu-id="8b62a-124">이 어셈블리는 RMO에 종속되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-124">This assembly is independent from RMO.</span></span>  
  
## <a name="deploying-applications-based-on-rmo"></a><span data-ttu-id="8b62a-125">RMO를 기초로 애플리케이션 배포</span><span class="sxs-lookup"><span data-stu-id="8b62a-125">Deploying Applications Based on RMO</span></span>  
 <span data-ttu-id="8b62a-126">RMO는 SQL Server Compact를 제외한 모든 버전의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 포함된 복제 구성 요소와 클라이언트 연결 구성 요소를 필요로 하기 때문에</span><span class="sxs-lookup"><span data-stu-id="8b62a-126">RMO depends on the replication components and client connectivity components that are included with all versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] except SQL Server Compact.</span></span> <span data-ttu-id="8b62a-127">RMO를 기초로 애플리케이션을 배포하려면 복제 구성 요소와 클라이언트 연결 구성 요소가 포함된 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 버전을 애플리케이션을 실행할 컴퓨터에 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-127">To deploy an application based on RMO, you must install a version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that includes replication components and client connectivity components on the computer on which the application will run.</span></span>  
  
## <a name="getting-started-with-rmo"></a><span data-ttu-id="8b62a-128">RMO 시작</span><span class="sxs-lookup"><span data-stu-id="8b62a-128">Getting Started with RMO</span></span>  
 <span data-ttu-id="8b62a-129">이 섹션에서는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio를 사용하여 간단한 RMO 프로젝트를 시작하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-129">This section describes how to start a simple RMO project using [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio.</span></span>  
  
#### <a name="to-create-a-new-microsoft-visual-c-project"></a><span data-ttu-id="8b62a-130">새 Microsoft Visual C# 프로젝트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="8b62a-130">To create a new Microsoft Visual C# project</span></span>  
  
1.  <span data-ttu-id="8b62a-131">Visual Studio를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-131">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="8b62a-132">**파일** 메뉴에서 **새 프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-132">On the **File** menu, click **NewProject.**</span></span> <span data-ttu-id="8b62a-133">**새 프로젝트** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-133">The **New Project** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="8b62a-134">**프로젝트 형식** 대화 상자에서 **Visual C# 프로젝트**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-134">In the **Project Types** dialog box, select **Visual C# Projects**.</span></span> <span data-ttu-id="8b62a-135">**템플릿** 창에서 **Windows 애플리케이션**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-135">In the **Templates** pane, select **Windows Application**.</span></span>  
  
4.  <span data-ttu-id="8b62a-136">(옵션) **이름**에 새 애플리케이션의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-136">(Optional) In **Name**, type the name of the new application.</span></span>  
  
5.  <span data-ttu-id="8b62a-137">**확인**을 클릭하여 Visual C# Windows 템플릿을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-137">Click **OK** to load the Visual C# Windows template.</span></span>  
  
6.  <span data-ttu-id="8b62a-138">**프로젝트** 메뉴에서 **참조 추가** 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-138">On the **Project** menu, select **Add Reference** item.</span></span> <span data-ttu-id="8b62a-139">**참조 추가** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-139">The **Add Reference** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="8b62a-140">**.NET** 탭의 목록에서 다음과 같은 어셈블리를 선택한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-140">Select the following assemblies from the list on the **.NET** tab, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="8b62a-141">Microsoft.SqlServer.Replication .NET Programming Interface</span><span class="sxs-lookup"><span data-stu-id="8b62a-141">Microsoft.SqlServer.Replication .NET Programming Interface</span></span>  
  
    -   <span data-ttu-id="8b62a-142">Microsoft.SqlServer.ConnectionInfo</span><span class="sxs-lookup"><span data-stu-id="8b62a-142">Microsoft.SqlServer.ConnectionInfo</span></span>  
  
    -   <span data-ttu-id="8b62a-143">Replication Agent Library</span><span class="sxs-lookup"><span data-stu-id="8b62a-143">Replication Agent Library</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8b62a-144">둘 이상의 파일을 선택하려면 Ctrl 키를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-144">Use the CTRL key to select more than one file.</span></span>  
  
8.  <span data-ttu-id="8b62a-145">(옵션) 6단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-145">(Optional) Repeat step 6.</span></span> <span data-ttu-id="8b62a-146">**찾아보기** 탭을 클릭하고 [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM으로 이동한 다음 Microsoft.SqlServer.Replication.BusinessLogicSupport.dll을 선택하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-146">Click the **Browse** tab, navigate to [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM, select Microsoft.SqlServer.Replication.BusinessLogicSupport.dll, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="8b62a-147">**보기** 메뉴에서 **코드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-147">On the **View** menu, click **Code**.</span></span>  
  
10. <span data-ttu-id="8b62a-148">코드에서 RMO 네임스페이스의 형식을 한정하기 위해 네임스페이스 문 앞에 다음 `using` 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-148">In the code, before the namespace statement, type the following `using` statements to qualify the types in the RMO namespaces:</span></span>  
  
    ```  
    // These namespaces are required.  
    using Microsoft.SqlServer.Replication;  
    using Microsoft.SqlServer.Management.Common;  
    // This namespace is only used when creating custom business  
    // logic for merge replication.  
    using Microsoft.SqlServer.Replication.BusinessLogicSupport;   
    ```  
  
#### <a name="to-create-a-new-microsoft-visual-basic-net-project"></a><span data-ttu-id="8b62a-149">새 Microsoft Visual Basic .NET 프로젝트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="8b62a-149">To create a new Microsoft Visual Basic .NET project</span></span>  
  
1.  <span data-ttu-id="8b62a-150">Visual Studio를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-150">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="8b62a-151">**파일** 메뉴에서 **새 프로젝트**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-151">On the **File** menu, select **New Project**.</span></span> <span data-ttu-id="8b62a-152">**새 프로젝트** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-152">The **New Project** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="8b62a-153">프로젝트 형식 창에서 **Visual Basic**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-153">In the Project Types pane, select **Visual Basic**.</span></span> <span data-ttu-id="8b62a-154">템플릿 창에서 **Windows 애플리케이션**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-154">In the Templates pane, select **Windows Application**.</span></span>  
  
4.  <span data-ttu-id="8b62a-155">(옵션) **이름** 상자에 새 애플리케이션의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-155">(Optional) In the **Name** box, type the name of the new application.</span></span>  
  
5.  <span data-ttu-id="8b62a-156">**확인**을 클릭하여 Visual Basic Windows 템플릿을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-156">Click **OK** to load the Visual Basic Windows template.</span></span>  
  
6.  <span data-ttu-id="8b62a-157">**프로젝트** 메뉴에서 **참조 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-157">On the **Project** menu, select **Add Reference**.</span></span> <span data-ttu-id="8b62a-158">**참조 추가** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-158">The **Add Reference** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="8b62a-159">**.NET** 탭의 목록에서 다음과 같은 어셈블리를 선택한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-159">Select the following assemblies from the list on the **.NET** tab, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="8b62a-160">Microsoft.SqlServer.Replication .NET Programming Interface</span><span class="sxs-lookup"><span data-stu-id="8b62a-160">Microsoft.SqlServer.Replication .NET Programming Interface</span></span>  
  
    -   <span data-ttu-id="8b62a-161">Microsoft.SqlServer.ConnectionInfo</span><span class="sxs-lookup"><span data-stu-id="8b62a-161">Microsoft.SqlServer.ConnectionInfo</span></span>  
  
    -   <span data-ttu-id="8b62a-162">Replication Agent Library</span><span class="sxs-lookup"><span data-stu-id="8b62a-162">Replication Agent Library</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8b62a-163">둘 이상의 파일을 선택하려면 Ctrl 키를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-163">Use the CTRL key to select more than one file.</span></span>  
  
8.  <span data-ttu-id="8b62a-164">(옵션) 6단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-164">(Optional) Repeat step 6.</span></span> <span data-ttu-id="8b62a-165">**찾아보기** 탭을 클릭하고 [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM으로 이동한 다음 Microsoft.SqlServer.Replication.BusinessLogicSupport.dll을 선택하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-165">Click the **Browse** tab, navigate to [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM, select Microsoft.SqlServer.Replication.BusinessLogicSupport.dll, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="8b62a-166">**보기** 메뉴에서 **코드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-166">On the **View** menu, click **Code**.</span></span>  
  
10. <span data-ttu-id="8b62a-167">코드에서 RMO 네임스페이스의 형식을 한정하기 위해 모든 선언 앞에 다음 `Imports` 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-167">In the code, before any declarations, type the following `Imports` statements to qualify the types in the RMO namespaces.</span></span>  
  
    ```  
    ' These namespaces are required.  
    Imports Microsoft.SqlServer.Replication  
    Imports Microsoft.SqlServer.Management.Common  
    ' This namespace is only used when creating custom business  
    ' logic for merge replication.  
    Imports Microsoft.SqlServer.Replication.BusinessLogicSupport   
    ```  
  
## <a name="connecting-to-a-replication-server"></a><span data-ttu-id="8b62a-168">복제 서버에 연결</span><span class="sxs-lookup"><span data-stu-id="8b62a-168">Connecting to a Replication Server</span></span>  
 <span data-ttu-id="8b62a-169">RMO 프로그래밍 개체의 경우 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스의 인스턴스를 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 인스턴스에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-169">RMO programming objects require that a connection to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is made by using an instance of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span> <span data-ttu-id="8b62a-170">이 서버 연결은 RMO 프로그래밍 개체와는 독립적으로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-170">This connection to the server is made independently of any RMO programming objects.</span></span> <span data-ttu-id="8b62a-171">그런 다음에는 인스턴스 생성 중에 또는 개체의 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성을 할당하여 연결을 RMO 개체로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-171">It is then passed to the RMO object either during instance creation or by assignment to the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property of the object.</span></span> <span data-ttu-id="8b62a-172">이런 식으로 RMO 프로그래밍 개체와 연결 개체 인스턴스를 별도로 만들고 관리할 수 있으며 여러 RMO 프로그래밍 개체에서 단일 연결 개체를 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-172">In this manner, an RMO programming object and the connection object instances can be created and managed separately, and a single connection object can be reused with multiple RMO programming objects.</span></span> <span data-ttu-id="8b62a-173">복제 서버에 대한 연결에는 다음 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-173">The following rules apply for connections to a replication server:</span></span>  
  
-   <span data-ttu-id="8b62a-174">지정된 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체에 대해 모든 연결 속성을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-174">All properties for the connection are defined for a given <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
-   <span data-ttu-id="8b62a-175">각 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대한 연결에 고유한 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-175">A connection to each instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] must have its own <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
-   <span data-ttu-id="8b62a-176"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체는 서버에서 생성되거나 액세스되는 RMO 프로그래밍 개체의 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-176">The <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object is assigned to the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property of the RMO programming object being created or accessed on the server.</span></span>  
  
-   <span data-ttu-id="8b62a-177"><xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> 메서드는 서버에 대한 연결을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-177">The <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> method opens the connection to the server.</span></span> <span data-ttu-id="8b62a-178">이 메서드는 서버에 액세스하는 다른 모든 메서드를 호출하기 전에 해당 연결을 사용하는 RMO 프로그래밍 개체에 대해 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-178">This method must be called before calling any methods that access the server on any RMO programming objects using the connection.</span></span>  
  
-   <span data-ttu-id="8b62a-179">RMO 및 SMO([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects) 모두 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 연결하기 때문에 RMO와 SMO 개체 모두가 동일한 연결을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-179">Because RMO and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) both use the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class for connections to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the same connection can be used by both RMO and SMO objects.</span></span> <span data-ttu-id="8b62a-180">자세한 내용은 [SQL Server 인스턴스에 연결](../../server-management-objects-smo/create-program/connecting-to-an-instance-of-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8b62a-180">For more information, see [Connecting to an Instance of SQL Server](../../server-management-objects-smo/create-program/connecting-to-an-instance-of-sql-server.md).</span></span>  
  
-   <span data-ttu-id="8b62a-181">서버에 연결하고 성공적으로 로그인하기 위해 모든 인증 정보를 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-181">All authentication information to make the connection and successfully log on to the server is supplied in the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
-   <span data-ttu-id="8b62a-182">Windows 인증이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-182">Windows Authentication is the default.</span></span> <span data-ttu-id="8b62a-183">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증을 사용하려면 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.LoginSecure%2A>를 `false`로 설정하고 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Login%2A> 및 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Password%2A>에 유효한 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 로그인 및 암호를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-183">To use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.LoginSecure%2A> must be set to `false` and <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Login%2A> and <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Password%2A> must be set to a valid [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logon and password.</span></span> <span data-ttu-id="8b62a-184">보안 자격 증명은 항상 안전하게 저장 및 처리되어야 하고 가능하면 런타임에 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-184">Security credentials must always be stored and handled securely, and supplied at run-time whenever possible.</span></span>  
  
-   <span data-ttu-id="8b62a-185">다중 스레드 애플리케이션의 경우 각 스레드에서 별도의 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-185">For multithreaded applications, a separate <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object should be used in each thread.</span></span>  
  
 <span data-ttu-id="8b62a-186">RMO 개체에서 사용하는 활성 서버 연결을 닫으려면 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> 개체에 대해 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-186">Call the <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> method on the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object to close active server connections used by RMO objects.</span></span>  
  
## <a name="setting-rmo-properties"></a><span data-ttu-id="8b62a-187">RMO 속성 설정</span><span class="sxs-lookup"><span data-stu-id="8b62a-187">Setting RMO Properties</span></span>  
 <span data-ttu-id="8b62a-188">RMO 프로그래밍 개체의 속성은 서버에 있는 이러한 복제 개체의 속성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-188">The properties of RMO programming objects represent the properties of these replication objects at the server.</span></span> <span data-ttu-id="8b62a-189">서버에서 새 복제 개체를 만들 경우 이러한 개체는 RMO 속성을 사용하여 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-189">When creating new replication objects at the server, RMO properties are used to define these objects.</span></span> <span data-ttu-id="8b62a-190">기존 개체의 경우 RMO 속성은 기존 개체의 속성을 나타내며, 이러한 속성은 쓰기 또는 설정 가능한 속성에 한해서만 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-190">For existing objects, the RMO properties represent the existing object's properties, which can be modified only for properties that are writable or settable.</span></span> <span data-ttu-id="8b62a-191">새 개체나 기존 개체에 대해 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-191">Properties can be set on new objects or existing objects.</span></span>  
  
### <a name="setting-properties-for-new-replication-objects"></a><span data-ttu-id="8b62a-192">새 복제 개체의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="8b62a-192">Setting Properties for New Replication Objects</span></span>  
 <span data-ttu-id="8b62a-193">서버에서 새 복제 개체를 만들 경우 개체의 `Create` 메서드를 호출하기 전에 모든 필수 속성을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-193">When creating a new replication object at the server, you must specify all required properties before calling the `Create` method of the object.</span></span> <span data-ttu-id="8b62a-194">새 복제 개체의 속성을 설정하는 방법은 [게시 및 배포 구성](../configure-publishing-and-distribution.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8b62a-194">For more information about setting properties for a new replication object, see [Configure Publishing and Distribution](../configure-publishing-and-distribution.md).</span></span>  
  
### <a name="setting-properties-for-existing-replication-objects"></a><span data-ttu-id="8b62a-195">기존 복제 개체의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="8b62a-195">Setting Properties for Existing Replication Objects</span></span>  
 <span data-ttu-id="8b62a-196">서버에 있는 기존 복제 개체의 경우 개체에 따라 RMO에서 해당 개체의 속성 전체 또는 일부의 변경을 지원하는지 여부가 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-196">For replication objects that exist at the server, depending on the object, RMO might support the ability to change some or all of its properties.</span></span> <span data-ttu-id="8b62a-197">쓰기 또는 설정 가능한 속성만 변경 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-197">Only writable or settable properties can be changed.</span></span> <span data-ttu-id="8b62a-198">속성을 변경하려면 먼저 `Load` 또는 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 서버에서 현재 속성을 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-198">Before properties can be changed, either the `Load` or the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method must be called to get the current properties from the server.</span></span> <span data-ttu-id="8b62a-199">이러한 메서드 호출은 기존 개체가 수정됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-199">Calling these methods indicates that an existing object is being modified.</span></span>  
  
 <span data-ttu-id="8b62a-200">기본적으로 RMO는 개체 속성을 변경할 때 현재 사용 중인 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>의 실행 모드에 따라 변경 내용을 서버에 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-200">By default, when changing object properties, RMO commits these changes to the server based on the execution mode of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> being used.</span></span> <span data-ttu-id="8b62a-201"><xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 메서드를 사용하면 개체의 속성을 검색하거나 변경하기 전에 해당 개체가 서버에 있는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-201">The <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> method can be used to verify that an object exists at the server before attempting to retrieve or change its properties.</span></span> <span data-ttu-id="8b62a-202">복제 개체의 속성을 변경하는 방법은 [배포자 및 게시자 속성 보기 및 수정](../view-and-modify-distributor-and-publisher-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8b62a-202">For more information about changing the properties of a replication object, see [View and Modify Distributor and Publisher Properties](../view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8b62a-203">여러 RMO 클라이언트 또는 RMO 프로그래밍 개체의 여러 인스턴스가 서버에 있는 동일한 복제 개체에 액세스할 경우 RMO 개체의 `Refresh` 메서드를 호출하면 서버에 있는 개체의 현재 상태에 따라 속성을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-203">When multiple RMO clients or multiple instances of an RMO programming object are accessing the same replication object at the server, the `Refresh` method of the RMO object can be called to update the properties based on the current state of the object at the server.</span></span>  
  
### <a name="caching-property-changes"></a><span data-ttu-id="8b62a-204">속성 변경 내용 캐시</span><span class="sxs-lookup"><span data-stu-id="8b62a-204">Caching Property Changes</span></span>  
 <span data-ttu-id="8b62a-205"><xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> 속성을 <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes.CaptureSql>로 설정하면 RMO에서 생성한 모든 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문이 캡처됩니다. 이 경우 실행 메서드 중 하나를 사용하여 하나의 일괄 처리에서 문을 수동으로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-205">When the <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> property is set to <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes.CaptureSql> all [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements generated by RMO are captured so that they can be executed manually in a single batch by using one of the execution methods.</span></span> <span data-ttu-id="8b62a-206">RMO를 사용하면 속성 변경 내용을 캐시한 후 개체의 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 메서드를 사용하여 하나의 일괄 처리에서 한 번에 커밋할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-206">RMO lets you cache property changes and commit them together in a single batch by using the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method of the object.</span></span> <span data-ttu-id="8b62a-207">속성 변경 내용을 캐시하려면 개체의 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 속성을 `true`로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-207">To cache property changes, the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> property of the object must be set to `true`.</span></span> <span data-ttu-id="8b62a-208">RMO의 속성 변경 내용을 캐시하는 경우에도 변경 내용이 서버에 전송되는 시점은 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체에 의해 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-208">When caching property changes in RMO, the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object still controls when changes are sent to the server.</span></span> <span data-ttu-id="8b62a-209">복제 개체의 속성 변경 내용을 캐시하는 방법은 [배포자 및 게시자 속성 보기 및 수정](../view-and-modify-distributor-and-publisher-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8b62a-209">For more information about caching property changes for a replication object, see [View and Modify Distributor and Publisher Properties](../view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8b62a-210">속성을 설정할 때 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 트랜잭션을 명시적으로 선언할 수 있지만 이러한 트랜잭션은 내부 복제 트랜잭션을 방해하여 예기치 않은 결과를 초래할 수 있기 때문에 RMO와 함께 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-210">Although the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class supports declaring explicit transactions when setting properties, such transactions may interfere with internal replication transactions, can produce unanticipated results, and should not be used with RMO.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b62a-211">예제</span><span class="sxs-lookup"><span data-stu-id="8b62a-211">Example</span></span>  
 <span data-ttu-id="8b62a-212">이 예에서는 속성 변경 내용을 캐시하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-212">This example demonstrates the caching of property changes.</span></span> <span data-ttu-id="8b62a-213">여기서 트랜잭션 게시의 특성에 대한 변경 내용은 서버에 명시적으로 전송되기 전까지 캐시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b62a-213">Changes made to the attributes of a transactional publication are cached until they are explicitly sent to the server.</span></span>  
  
 [!code-csharp[HowTo#rmo_ChangeTranPub_cached](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_ChangeTranPub_cached)]  
  
## <a name="see-also"></a><span data-ttu-id="8b62a-214">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8b62a-214">See Also</span></span>  
 <span data-ttu-id="8b62a-215">[Replication System Stored Procedures Concepts](replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="8b62a-215">[Replication System Stored Procedures Concepts](replication-system-stored-procedures-concepts.md) </span></span>  
 [<span data-ttu-id="8b62a-216">복제 프로그래밍 개념</span><span class="sxs-lookup"><span data-stu-id="8b62a-216">Replication Programming Concepts</span></span>](replication-programming-concepts.md)  
  
  
