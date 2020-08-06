---
title: 서버 환경 만들기 및 매핑 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isenvprop.variables.f1
- sql12.ssis.ssms.iscreateenv.f1
- sql12.ssis.ssms.isenvprop.permissions.f1
- sql12.ssis.ssms.isenvprop.general.f1
ms.assetid: b1cbb697-713f-48e4-b234-b23724d87451
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9331b5078effb562931f45c48bd8ff975c1d1998
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649608"
---
# <a name="create-and-map-a-server-environment"></a><span data-ttu-id="92bc0-102">서버 환경 만들기 및 매핑</span><span class="sxs-lookup"><span data-stu-id="92bc0-102">Create and Map a Server Environment</span></span>
  <span data-ttu-id="92bc0-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서버에 배포한 프로젝트에 포함된 패키지의 런타임 값을 지정하기 위한 서버 환경을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-103">You create a server environment to specify runtime values for packages contained in a project you've deployed to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="92bc0-104">그런 다음 특정 패키지, 진입점 패키지 또는 지정된 프로젝트의 모든 패키지에 대한 매개 변수에 환경 변수를 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-104">You can then map the environment variables to parameters, for a specific package, for entry-point packages, or for all the packages in a given project.</span></span> <span data-ttu-id="92bc0-105">진입점 패키지는 일반적으로 자식 패키지를 실행하는 부모 패키지입니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-105">An entry-point package is typically a parent package that executes a child package.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="92bc0-106">지정된 실행의 경우 패키지는 단일 서버 환경에 포함된 값만으로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-106">For a given execution, a package can execute only with the values contained in a single server environment.</span></span>  
  
 <span data-ttu-id="92bc0-107">서버 환경, 환경 참조 및 환경 변수 목록에 대한 뷰를 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-107">You can query views for a list of server environments, environment references, and environment variables.</span></span> <span data-ttu-id="92bc0-108">저장 프로시저를 호출하여 환경, 환경 참조 및 환경 변수를 추가, 삭제 및 수정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-108">You can also call stored to add, delete, and modify environments, environment references, and environment variables.</span></span> <span data-ttu-id="92bc0-109">자세한 내용은 **SSIS Catalog** 의 [서버 환경, 서버 변수 및 서버 환경 참조](catalog/ssis-catalog.md)섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="92bc0-109">For more information, see the **Server Environments, Server Variables and Server Environment References** section in [SSIS Catalog](catalog/ssis-catalog.md).</span></span>  
  
### <a name="to-create-and-use-a-server-environment"></a><span data-ttu-id="92bc0-110">서버 환경을 만들고 사용하려면</span><span class="sxs-lookup"><span data-stu-id="92bc0-110">To create and use a server environment</span></span>  
  
1.  <span data-ttu-id="92bc0-111">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]의 개체 탐색기에서 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 카탈로그> **SSISDB** 노드를 확장하고 환경을 만들 프로젝트의 **환경** 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-111">In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], expand the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Catalogs> **SSISDB** node in Object Explorer, and locate the **Environments** folder of the project for which you want to create an environment.</span></span>  
  
2.  <span data-ttu-id="92bc0-112">**환경** 폴더를 마우스 오른쪽 단추로 클릭한 다음 **환경 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-112">Right-click the **Environments** folder, and then click **Create Environment**.</span></span>  
  
3.  <span data-ttu-id="92bc0-113">환경의 이름을 입력하고 선택적으로 설명을 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-113">Type a name for the environment and optionally a description, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="92bc0-114">새 환경을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-114">Right-click the new environment and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="92bc0-115">**변수** 페이지에서 다음을 수행하여 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-115">On the **Variables** page, do the following to add a variable.</span></span>  
  
    1.  <span data-ttu-id="92bc0-116">변수의 **유형** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-116">Select the **Type** for the variable.</span></span> <span data-ttu-id="92bc0-117">변수 이름은 변수에 매핑할 프로젝트 매개 변수의 이름과 일치하지 **않아도** 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-117">The name of the variable **does not** need to match the name of the project parameter that you map to the variable.</span></span>  
  
    2.  <span data-ttu-id="92bc0-118">변수에 대한 선택적 **설명** 을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-118">Enter an optional **Description** for the variable.</span></span>  
  
    3.  <span data-ttu-id="92bc0-119">환경 변수의 **값** 을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-119">Enter the **Value** for the environment variable.</span></span>  
  
         <span data-ttu-id="92bc0-120">환경 변수 이름에 대한 규칙은 **SSIS Catalog** 의 [환경 변수](catalog/ssis-catalog.md)섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="92bc0-120">For information about the rules for environment variable names, see the **Environment Variable** section in [SSIS Catalog](catalog/ssis-catalog.md).</span></span>  
  
    4.  <span data-ttu-id="92bc0-121">**중요** 확인란을 선택하거나 선택을 취소하여 변수에 중요한 값이 포함되어 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-121">Indicate whether the variable contains sensitive value, by selecting or clearing the **Sensitive** checkbox.</span></span>  
  
         <span data-ttu-id="92bc0-122">**중요**를 선택하면 변수 값이 **값** 필드에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-122">If you select **Sensitive**, the variable value does not display in the **Value** field.</span></span>  
  
         <span data-ttu-id="92bc0-123">중요한 값은 SSISDB 카탈로그에서 암호화됩니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-123">Sensitive values are encrypted in the SSISDB catalog.</span></span> <span data-ttu-id="92bc0-124">암호화에 대한 자세한 내용은 [SSIS Catalog](catalog/ssis-catalog.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="92bc0-124">For more information about the encryption, see [SSIS Catalog](catalog/ssis-catalog.md).</span></span>  
  
6.  <span data-ttu-id="92bc0-125">**사용 권한** 페이지에서 다음을 수행하여 선택한 사용자 및 역할에 대해 사용 권한을 허용하거나 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-125">On the **Permissions** page, grant or deny permissions for selected users and roles by doing the following.</span></span>  
  
    1.  <span data-ttu-id="92bc0-126">**찾아보기**를 클릭한 다음 **모든 보안 주체 찾아보기** 대화 상자에서 하나 이상의 사용자 및 역할을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-126">Click **Browse**, and then select one or more users and roles in the **Browse All Principals** dialog box.</span></span>  
  
    2.  <span data-ttu-id="92bc0-127">**로그인 또는 역할** 영역에서 사용 권한을 허용하거나 거부할 사용자 또는 역할을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-127">In the **Logins or roles** area, select the user or role that you want to grant or deny permissions for.</span></span>  
  
    3.  <span data-ttu-id="92bc0-128">**명시적** 영역에서 각 사용 권한 옆의 **허용** 또는 **거부** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-128">In the **Explicit** area, click **Grant** or **Deny** next to each permission.</span></span>  
  
7.  <span data-ttu-id="92bc0-129">환경을 스크립팅하려면 **스크립트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-129">To script the environment, click **Script**.</span></span> <span data-ttu-id="92bc0-130">기본적으로 스크립트는 새 쿼리 편집기 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-130">By default, the script displays in a new Query Editor window.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="92bc0-131">변수를 추가하는 등 환경 속성을 하나 이상 변경한 후에 **환경 속성** 대화 상자에서 **확인**을 클릭하기 전에 **스크립트**를 클릭해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-131">You need to click **Script** after you've made one or changes to the environment properties, such as adding a variable, and before you click **OK** in the **Environment Properties** dialog box.</span></span> <span data-ttu-id="92bc0-132">그렇지 않으면 스크립트가 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-132">Otherwise, a script is not generated.</span></span>  
  
8.  <span data-ttu-id="92bc0-133">변경 내용을 환경 속성에 저장하려면 **확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-133">Click **OK** to save your changes to the environment properties.</span></span>  
  
9. <span data-ttu-id="92bc0-134">개체 탐색기의 **SSISDB** 노드에서 **프로젝트** 폴더를 확장하고 프로젝트를 마우스 오른쪽 단추로 클릭한 다음 **구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-134">Under the **SSISDB** node in Object Explorer, expand the **Projects** folder, right-click the project, and then click **Configure**.</span></span>  
  
10. <span data-ttu-id="92bc0-135">**참조** 페이지에서 **추가** 를 클릭하여 환경을 추가한 다음 **확인** 을 클릭하여 참조를 환경에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-135">On the **References** page, click **Add** to add an environment, and then click **OK** to save the reference to the environment.</span></span>  
  
11. <span data-ttu-id="92bc0-136">프로젝트를 다시 마우스 오른쪽 단추로 클릭한 다음 **구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-136">Right-click the project again, and then click **Configure**.</span></span>  
  
12. <span data-ttu-id="92bc0-137">디자인 타임 시 패키지에 추가한 매개 변수 또는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 프로젝트 배포 모델로 변환할 때 생성된 매개 변수에 환경 변수를 매핑하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-137">To map the environment variable to a parameter that you added to the package at design-time or to a parameter that was generated when you converted the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project to the project deployment model, do the following.,</span></span>  
  
    1.  <span data-ttu-id="92bc0-138">**매개 변수** 페이지의 **매개 변수** 탭에서 **값** 필드 옆에 있는 찾아보기 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-138">In the **Parameters** tab on the **Parameters** page, click the browse button next to the **Value** field.</span></span>  
  
    2.  <span data-ttu-id="92bc0-139">**환경 변수 사용**을 클릭한 다음 만든 환경 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-139">Click **Use environment variable**, and then select the environment variable you created.</span></span>  
  
13. <span data-ttu-id="92bc0-140">환경 변수를 연결 관리자 속성에 매핑하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-140">To map the environment variable to a connection manager property, do the following.</span></span> <span data-ttu-id="92bc0-141">연결 관리자 속성에 대한 매개 변수가 SSIS 서버에 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-141">Parameters are automatically generated on the SSIS server for the connection manager properties.</span></span>  
  
    1.  <span data-ttu-id="92bc0-142">**매개 변수** 페이지의 **연결 관리자** 탭에서 **값** 필드 옆에 있는 찾아보기 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-142">In the **Connection Managers** tab on the **Parameters** page, click the browse button next to the **Value** field.</span></span>  
  
    2.  <span data-ttu-id="92bc0-143">**환경 변수 사용**을 클릭한 다음 만든 환경 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-143">Click **Use environment variable**, and then select the environment variable you created.</span></span>  
  
14. <span data-ttu-id="92bc0-144">**확인**을 두 번 클릭하여 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="92bc0-144">Click **OK** twice to save your changes.</span></span>  
  
  
