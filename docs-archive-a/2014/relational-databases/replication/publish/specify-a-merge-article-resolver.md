---
title: 병합 아티클 해결 프로그램 지정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
- merge replication conflict resolution [SQL Server replication], merge article resolvers
ms.assetid: a40083b3-4f7b-4a25-a5a3-6ef67bdff440
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ca32ef4936f31ca5c75dfc2df1eb965d17f7b039
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733879"
---
# <a name="specify-a-merge-article-resolver"></a><span data-ttu-id="a48a9-102">병합 아티클 해결 프로그램 지정</span><span class="sxs-lookup"><span data-stu-id="a48a9-102">Specify a Merge Article Resolver</span></span>
  <span data-ttu-id="a48a9-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 병합 아티클 해결 프로그램을 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-103">This topic describes how to specify a merge article resolver in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="a48a9-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="a48a9-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a48a9-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="a48a9-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a48a9-106">권장 사항</span><span class="sxs-lookup"><span data-stu-id="a48a9-106">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="a48a9-107">**다음을 사용하여 병합 아티클 해결 프로그램을 지정하려면**</span><span class="sxs-lookup"><span data-stu-id="a48a9-107">**To specify a merge article resolver, using:**</span></span>  
  
     [<span data-ttu-id="a48a9-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a48a9-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a48a9-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a48a9-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a48a9-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="a48a9-110">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="a48a9-111">권장 사항</span><span class="sxs-lookup"><span data-stu-id="a48a9-111">Recommendations</span></span>  
  
-   <span data-ttu-id="a48a9-112">병합 복제에서 다음 유형의 아티클 해결 프로그램을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-112">Merge replication allows the following types of article resolvers:</span></span>  
  
    -   <span data-ttu-id="a48a9-113">기본 해결 프로그램.</span><span class="sxs-lookup"><span data-stu-id="a48a9-113">The default resolver.</span></span> <span data-ttu-id="a48a9-114">기본 해결 프로그램의 동작은 구독이 클라이언트 구독인지 서버 구독인지에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-114">The behavior of the default resolver depends on whether the subscription is a client subscription or a server subscription.</span></span> <span data-ttu-id="a48a9-115">구독 유형을 지정하는 방법은 [병합 구독 유형 및 충돌 해결 우선 순위 지정&#40;SQL Server Management Studio&#41;](../specify-a-merge-subscription-type-and-conflict-resolution-priority.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a48a9-115">For more information about specifying subscription type, see [Specify a Merge Subscription Type and Conflict Resolution Priority &#40;SQL Server Management Studio&#41;](../specify-a-merge-subscription-type-and-conflict-resolution-priority.md).</span></span>  
  
    -   <span data-ttu-id="a48a9-116">사용자 지정 해결 프로그램 - 관리 코드로 작성된 비즈니스 논리 처리기 또는 사용자 지정 COM 기반 해결 프로그램일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-116">A custom resolver you have written, which can be a business logic handler (written in managed code) or a custom COM-based resolver.</span></span> <span data-ttu-id="a48a9-117">자세한 내용은 [고급 병합 복제 충돌 감지 및 해결](../merge/advanced-merge-replication-conflict-detection-and-resolution.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a48a9-117">For more information, see [Advanced Merge Replication Conflict Detection and Resolution](../merge/advanced-merge-replication-conflict-detection-and-resolution.md).</span></span> <span data-ttu-id="a48a9-118">충돌하는 행뿐만 아니라 각 복제된 행에 대해서도 실행되는 사용자 지정 논리를 구현해야 하는 경우 [병합 아티클에 대한 비즈니스 논리 처리기 구현](../implement-a-business-logic-handler-for-a-merge-article.md)에서 병합 아티클 해결 프로그램을 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-118">If you need to implement custom logic that is executed for each replicated row, not just for conflicting rows, see [Implement a Business Logic Handler for a Merge Article](../implement-a-business-logic-handler-for-a-merge-article.md).</span></span>  
  
    -   <span data-ttu-id="a48a9-119">표준 COM 기반 해결 프로그램 - [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-119">A standard COM-based resolver, which is included with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="a48a9-120">기본 해결 프로그램 이외의 해결 프로그램을 사용하려면 해당 해결 프로그램을 병합 에이전트를 실행하는 컴퓨터로 복사하고 등록해야 합니다. 비즈니스 논리 처리기를 사용하는 경우에는 해당 프로그램을 게시자에서도 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-120">To use a resolver other than the default resolver, you must copy the resolver to the computer on which the Merge Agent runs and register it (if you are using a business logic handler, it must also be registered at the Publisher).</span></span> <span data-ttu-id="a48a9-121">병합 에이전트는 다음에서 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-121">The Merge Agent runs at:</span></span>  
  
    -   <span data-ttu-id="a48a9-122">밀어넣기 구독에 대한 배포자</span><span class="sxs-lookup"><span data-stu-id="a48a9-122">The Distributor for a push subscription</span></span>  
  
    -   <span data-ttu-id="a48a9-123">끌어오기 구독에 대한 구독자</span><span class="sxs-lookup"><span data-stu-id="a48a9-123">The Subscriber for a pull subscription</span></span>  
  
    -   <span data-ttu-id="a48a9-124">웹 동기화를 사용하는 끌어오기 구독에 대한 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 인터넷 정보 서비스(IIS) 서버</span><span class="sxs-lookup"><span data-stu-id="a48a9-124">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Internet Information Services (IIS) server for a pull subscription that uses Web synchronization</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a48a9-125">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="a48a9-125">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="a48a9-126">해결 프로그램이 등록되면 새 게시 마법사의 **아티클 속성 - \<Article>** 대화 상자 및 **게시 속성 - \<Publication>** 대화 상자의 **해결 프로그램** 탭에서 아티클에 해당 해결 프로그램이 사용되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-126">After the resolver is registered, specify that an article should use the resolver on the **Resolver** tab of the **Article Properties - \<Article>** dialog box, which is available in the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="a48a9-127">마법사 사용 및 대화 상자 액세스에 대한 자세한 내용은 [게시 만들기](create-a-publication.md) 및 [게시 속성 보기 및 수정](view-and-modify-publication-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a48a9-127">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-specify-a-resolver"></a><span data-ttu-id="a48a9-128">해결 프로그램을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="a48a9-128">To specify a resolver</span></span>  
  
1.  <span data-ttu-id="a48a9-129">새 게시 마법사의 **아티클** 페이지 또는 **게시 속성 - \<Publication>** 대화 상자에서 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-129">On the **Articles** page of the New Publication Wizard or the **Publication Properties - \<Publication>** dialog box, select a table.</span></span>  
  
2.  <span data-ttu-id="a48a9-130">**아티클 속성**을 클릭한 다음 **선택한 테이블 아티클 속성 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-130">Click **Article Properties**, and then click **Set Properties of Highlighted Table Article**.</span></span>  
  
3.  <span data-ttu-id="a48a9-131">**아티클 속성 - \<Article>** 페이지에서 **해결 프로그램** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-131">On the **Article Properties - \<Article>** page, click the **Resolver** tab.</span></span>  
  
4.  <span data-ttu-id="a48a9-132">**사용자 지정 해결 프로그램 사용(배포자에 등록됨)** 을 선택하고 목록에서 해결 프로그램을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-132">Select **Use a custom resolver (registered at the Distributor)**, and then in the list, click the resolver.</span></span>  
  
5.  <span data-ttu-id="a48a9-133">해결 프로그램에 열 이름과 같은 입력값이 필요하면 **해결 프로그램에 필요한 정보 입력** 입력란에 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-133">If the resolver requires input (such as a column name), specify it in the **Enter information needed by the resolver** text box.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="a48a9-134">이 과정을 해결 프로그램이 필요한 각 아티클에서 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-134">Repeat this process for each article that requires a resolver.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a48a9-135">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="a48a9-135">Using Transact-SQL</span></span>  
  
#### <a name="to-register-a-custom-conflict-resolver"></a><span data-ttu-id="a48a9-136">사용자 지정 충돌 해결 프로그램을 등록하려면</span><span class="sxs-lookup"><span data-stu-id="a48a9-136">To register a custom conflict resolver</span></span>  
  
1.  <span data-ttu-id="a48a9-137">사용자 지정 충돌 해결 프로그램을 등록하려면 다음 유형 중 하나를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-137">If you plan to register your own custom conflict resolver, create one of the following types:</span></span>  
  
    -   <span data-ttu-id="a48a9-138">관리 코드 기반 해결 프로그램(비즈니스 논리 처리기).</span><span class="sxs-lookup"><span data-stu-id="a48a9-138">Managed code-based resolver as a business logic handler.</span></span> <span data-ttu-id="a48a9-139">자세한 내용은 [병합 아티클에 대한 비즈니스 논리 처리기 구현](../implement-a-business-logic-handler-for-a-merge-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a48a9-139">For more information, see [Implement a Business Logic Handler for a Merge Article](../implement-a-business-logic-handler-for-a-merge-article.md).</span></span>  
  
    -   <span data-ttu-id="a48a9-140">저장 프로시저 기반 해결 프로그램 및 COM 기반 해결 프로그램</span><span class="sxs-lookup"><span data-stu-id="a48a9-140">Stored procedure-based resolver and COM-based resolver.</span></span> <span data-ttu-id="a48a9-141">자세한 내용은 [병합 아티클용 사용자 지정 충돌 해결 프로그램 구현](../implement-a-custom-conflict-resolver-for-a-merge-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a48a9-141">For more information, see [Implement a Custom Conflict Resolver for a Merge Article](../implement-a-custom-conflict-resolver-for-a-merge-article.md).</span></span>  
  
2.  <span data-ttu-id="a48a9-142">원하는 해결 프로그램이 이미 등록되어 있는지 확인하려면 모든 데이터베이스의 게시자에서 [sp_enumcustomresolvers&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-142">To determine if the desired resolver is already registered, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) at the Publisher on any database.</span></span> <span data-ttu-id="a48a9-143">그러면 사용자 지정 해결 프로그램에 대한 설명, 배포자에 등록된 각 COM 기반 해결 프로그램의 CLSID(클래스 식별자) 또는 배포자에 등록된 각 비즈니스 논리 처리기의 관리 어셈블리에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-143">This displays a description of the custom resolver as well as the class identifier (CLSID) for each COM-based resolver registered at the Distributor or information on the managed assembly for each business logic handler registered at the Distributor.</span></span>  
  
3.  <span data-ttu-id="a48a9-144">원하는 사용자 지정 해결 프로그램이 아직 등록되지 않은 경우 배포자에서 [sp_registercustomresolver&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-144">If the desired custom resolver is not already registered, execute [sp_registercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql) at the Distributor.</span></span> <span data-ttu-id="a48a9-145">에 대 한 해결 프로그램의 이름을 지정 합니다 **@article_resolver** . 비즈니스 논리 처리기의 경우 어셈블리의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-145">Specify a name for the resolver for **@article_resolver**; for a business logic handler, this is the friendly name of the assembly.</span></span> <span data-ttu-id="a48a9-146">COM 기반 해결 프로그램의 경우에는에 대 한 DLL의 CLSID를 지정 하 고, 비즈니스 논리 처리기의 경우에는의 값,에 **@resolver_clsid** `true` 어셈블리 이름,에 **@is_dotnet_assembly** **@dotnet_assembly_name** 대해 재정의 하는 클래스의 정규화 된 이름을 지정 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> **@dotnet_class_name** 합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-146">For COM-based resolvers, specify the CLSID of the DLL for **@resolver_clsid**, and for a business logic handler, specify a value of `true` for **@is_dotnet_assembly**, the name of the assembly for **@dotnet_assembly_name**, and the fully-qualified name of the class that overrides <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> for **@dotnet_class_name**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a48a9-147">비즈니스 논리 처리기 어셈블리가 병합 에이전트 실행 파일과 동일한 디렉터리에 배포 되지 않은 경우 병합 에이전트를 동기적으로 시작 하는 응용 프로그램과 동일한 디렉터리 또는 GAC (전역 어셈블리 캐시)에서 어셈블리 이름을 사용 하 여 전체 경로를 지정 해야 **@dotnet_assembly_name** 합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-147">If a business logic handler assembly is not deployed in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent, or in the global assembly cache (GAC), you need to specify the full path with the assembly name for **@dotnet_assembly_name**.</span></span>  
  
4.  <span data-ttu-id="a48a9-148">COM 기반 해결 프로그램인 경우:</span><span class="sxs-lookup"><span data-stu-id="a48a9-148">If the resolver is a COM-based resolver:</span></span>  
  
    -   <span data-ttu-id="a48a9-149">밀어넣기 구독에 대한 배포자 또는 끌어오기 구독에 대한 구독자에 사용자 지정 해결 프로그램 DLL을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-149">Copy the custom resolver DLL to the Distributor for push subscriptions or to the Subscriber for pull subscriptions.</span></span>  
  
        > [!NOTE]  
        >  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="a48a9-150">사용자 지정 해결 프로그램은 [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-150">custom resolvers can be found in the [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM directory.</span></span>  
  
    -   <span data-ttu-id="a48a9-151">regsvr32.exe를 사용하여 운영 체제에 사용자 지정 해결 프로그램 DLL을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-151">Use regsvr32.exe to register the custom resolver DLL with the operating system.</span></span> <span data-ttu-id="a48a9-152">예를 들어 명령 프롬프트에서 다음을 실행하면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 가산성 충돌 해결 프로그램이 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-152">For example, executing the following from the command prompt registers the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Additive Conflict Resolver:</span></span>  
  
        ```  
        regsvr32 ssradd.dll  
        ```  
  
5.  <span data-ttu-id="a48a9-153">해결 프로그램이 비즈니스 논리 처리기 인 경우 어셈블리를 병합 에이전트 실행 파일 (replmerg.exe)과 동일한 폴더 또는 병합 에이전트를 호출 하는 응용 프로그램과 같은 폴더에 배포 하거나 **@dotnet_assembly_name** 3 단계에서 매개 변수에 대해 지정 된 폴더에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-153">If the resolver is a business logic handler, deploy the assembly in the same folder as the Merge Agent executable (replmerg.exe), in the same folder as an application that invokes the Merge Agent, or in the folder specified for the **@dotnet_assembly_name** parameter in step 3.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a48a9-154">병합 에이전트 실행 파일의 기본 설치 위치는 [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM입니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-154">The default installation location of the Merge Agent executable is [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM.</span></span>  
  
#### <a name="to-specify-a-custom-resolver-when-defining-a-merge-article"></a><span data-ttu-id="a48a9-155">병합 아티클을 정의할 때 사용자 지정 해결 프로그램을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="a48a9-155">To specify a custom resolver when defining a merge article</span></span>  
  
1.  <span data-ttu-id="a48a9-156">사용자 지정 충돌 해결 프로그램을 사용하려면 위 절차를 사용하여 해결 프로그램을 만들고 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-156">If you plan to use a custom conflict resolver, create and register the resolver using the above procedure.</span></span>  
  
2.  <span data-ttu-id="a48a9-157">게시자에서 [sp_enumcustomresolvers&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql)를 실행하고 결과 집합의 **value** 필드에서 원하는 사용자 지정 해결 프로그램의 이름을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-157">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) and note the name of the desired custom resolver in the **value** field of result set.</span></span>  
  
3.  <span data-ttu-id="a48a9-158">게시 데이터베이스의 게시자에서 [sp_addmergearticle&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-158">At the Publisher on the publication database, execute [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span> <span data-ttu-id="a48a9-159">에 대해 2 단계에서 해결 프로그램의 이름을 지정 하 **@article_resolver** 고 매개 변수를 사용 하 여 사용자 지정 해결 프로그램에 필요한 입력을 지정 **@resolver_info** 합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-159">Specify the name of the resolver from step 2 for **@article_resolver** and any required input to the custom resolver using the **@resolver_info** parameter.</span></span> <span data-ttu-id="a48a9-160">저장 프로시저 기반 사용자 지정 해결 프로그램의 경우 **@resolver_info** 는 저장 프로시저의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-160">For stored procedure-based custom resolvers, **@resolver_info** is the name of the stored procedure.</span></span> <span data-ttu-id="a48a9-161">[!INCLUDE[msCoName](../../../includes/msconame-md.md)]에서 제공하는 해결 프로그램에 필요한 입력에 대한 자세한 내용은 [Microsoft COM 기반 해결 프로그램](../merge/advanced-merge-replication-conflict-com-based-resolvers.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a48a9-161">For more information about required input for resolvers supplied by [!INCLUDE[msCoName](../../../includes/msconame-md.md)], see [Microsoft COM-Based Resolvers](../merge/advanced-merge-replication-conflict-com-based-resolvers.md).</span></span>  
  
#### <a name="to-specify-or-change-a-custom-resolver-for-an-existing-merge-article"></a><span data-ttu-id="a48a9-162">기존 병합 아티클에 대한 사용자 지정 해결 프로그램을 지정하거나 변경하려면</span><span class="sxs-lookup"><span data-stu-id="a48a9-162">To specify or change a custom resolver for an existing merge article</span></span>  
  
1.  <span data-ttu-id="a48a9-163">아티클에 대한 사용자 지정 해결 프로그램이 정의되어 있는지 확인하려면 [sp_helpmergearticle&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-163">To determine if a custom resolver has been defined for an article, or to get the name of the resolver, execute [sp_helpmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql).</span></span> <span data-ttu-id="a48a9-164">아티클에 대해 정의된 사용자 지정 해결 프로그램이 있으면 **article_resolver** 필드에 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-164">If there is a custom resolver defined for the article, its name will be displayed in the **article_resolver** field.</span></span> <span data-ttu-id="a48a9-165">해결 프로그램에 제공되는 입력은 모두 결과 집합의 **resolver_info** 에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-165">Any input supplied to the resolver will be displayed in the **resolver_info** field of the result set.</span></span>  
  
2.  <span data-ttu-id="a48a9-166">게시자에서 [sp_enumcustomresolvers&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql)를 실행하고 결과 집합의 **value** 필드에서 원하는 사용자 지정 해결 프로그램의 이름을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-166">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) and note the name of the desired custom resolver in the **value** field of the result set.</span></span>  
  
3.  <span data-ttu-id="a48a9-167">게시 데이터베이스의 게시자에서 [sp_changemergearticle&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-167">At the Publisher on the publication database, execute [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="a48a9-168">**@property**에 비즈니스 논리 처리기의 전체 경로를 포함하여 **article_resolver** 값을 지정하고, **@value**에는 2단계의 원하는 사용자 지정 해결 프로그램 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-168">Specify a value of **article_resolver**, including the full path for business logic handlers, for **@property**, and the name of the desired custom resolver from step 2 for **@value**.</span></span>  
  
4.  <span data-ttu-id="a48a9-169">사용자 지정 해결 프로그램에 필요한 입력을 변경하려면 [sp_changemergearticle&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)을 다시 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-169">To change any required input for the custom resolver, execute [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) again.</span></span> <span data-ttu-id="a48a9-170">**@property**에 **resolver_info** 값, **@value**에 사용자 지정 해결 프로그램에 필요한 입력을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-170">Specify a value of **resolver_info** for **@property** and any required input to the custom resolver for **@value**.</span></span> <span data-ttu-id="a48a9-171">저장 프로시저 기반 사용자 지정 해결 프로그램의 경우 **@resolver_info** 는 저장 프로시저의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-171">For stored procedure-based custom resolvers, **@resolver_info** is the name of the stored procedure.</span></span> <span data-ttu-id="a48a9-172">필요한 입력에 대한 자세한 내용은 [Microsoft COM 기반 해결 프로그램](../merge/advanced-merge-replication-conflict-com-based-resolvers.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a48a9-172">For more information about required input, see [Microsoft COM-Based Resolvers](../merge/advanced-merge-replication-conflict-com-based-resolvers.md).</span></span>  
  
#### <a name="to-unregister-a-custom-conflict-resolver"></a><span data-ttu-id="a48a9-173">사용자 지정 충돌 해결 프로그램의 등록을 취소하려면</span><span class="sxs-lookup"><span data-stu-id="a48a9-173">To unregister a custom conflict resolver</span></span>  
  
1.  <span data-ttu-id="a48a9-174">게시자에서 [sp_enumcustomresolvers&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql)를 실행하고 결과 집합의 **value** 필드에서 제거할 사용자 지정 해결 프로그램의 이름을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-174">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) and note the name of the custom resolver to remove in the **value** field of the result set.</span></span>  
  
2.  <span data-ttu-id="a48a9-175">배포자에서 [sp_unregistercustomresolver&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-175">Execute [sp_unregistercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql) at the Distributor.</span></span> <span data-ttu-id="a48a9-176">에 대해 1 단계에서 가져온 사용자 지정 해결 프로그램의 전체 이름을 지정 **@article_resolver** 합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-176">Specify the full name of the custom resolver from step 1 for **@article_resolver**.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="a48a9-177">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a48a9-177">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="a48a9-178">이 예에서는 새 아티클을 만들고 충돌이 발생하는 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 평균 충돌 해결 프로그램을 사용하여 **UnitPrice** 열의 평균을 계산하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-178">This example creates a new article and specifies that the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Averaging Conflict Resolver be used to calculate the average of the **UnitPrice** column when conflicts occur.</span></span>  
  
 [!code-sql[HowTo#sp_addmerge_resolver](../../../snippets/tsql/SQL15/replication/howto/tsql/mergearticleresolvers.sql#sp_addmerge_resolver)]  
  
 <span data-ttu-id="a48a9-179">이 예에서는 아티클을 변경하여 충돌이 발생한 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 가산 충돌 해결 프로그램을 사용하여 **UnitsOnOrder** 열의 합을 계산하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a48a9-179">This example changes an article to specify using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Additive Conflict Resolver to calculate the sum of the **UnitsOnOrder** column when conflicts occur.</span></span>  
  
 [!code-sql[HowTo#sp_changemerge_resolver](../../../snippets/tsql/SQL15/replication/howto/tsql/mergearticleresolvers.sql#sp_changemerge_resolver)]  
  
## <a name="see-also"></a><span data-ttu-id="a48a9-180">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a48a9-180">See Also</span></span>  
 <span data-ttu-id="a48a9-181">[Advanced Merge Replication Conflict Detection and Resolution](../merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="a48a9-181">[Advanced Merge Replication Conflict Detection and Resolution](../merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 [<span data-ttu-id="a48a9-182">병합 아티클에 대한 비즈니스 논리 처리기 구현</span><span class="sxs-lookup"><span data-stu-id="a48a9-182">Implement a Business Logic Handler for a Merge Article</span></span>](../implement-a-business-logic-handler-for-a-merge-article.md)  
  
  
