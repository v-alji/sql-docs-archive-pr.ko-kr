---
title: 프로젝트 속성 대화 상자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isprojectprop.general.f1
- sql12.ssis.ssms.isprojectprop.permissions.f1
ms.assetid: d5cf52f5-1fe2-438a-98a3-fe117360acf8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 259ad48f2b1f33356243635bbaa5426a5199eccf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731968"
---
# <a name="project-properties-dialog-box"></a><span data-ttu-id="bbb2d-102">프로젝트 속성 대화 상자</span><span class="sxs-lookup"><span data-stu-id="bbb2d-102">Project Properties Dialog Box</span></span>
  <span data-ttu-id="bbb2d-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트는 하나의 배포 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-103">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project is a unit of deployment.</span></span> <span data-ttu-id="bbb2d-104">각 프로젝트는 패키지, 매개 변수 및 환경 참조를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-104">Each project can contain packages, parameters, and environment references.</span></span> <span data-ttu-id="bbb2d-105">프로젝트는 검색 가능한 개체이며 데이터베이스 보안 주체의 사용 권한을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-105">A project is a securable object and can define permissions for database principals.</span></span> <span data-ttu-id="bbb2d-106">프로젝트를 다시 배포하는 경우 이전 버전의 프로젝트를 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 카탈로그에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-106">When a project is re-deployed, the previous version of the project can be stored in the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] catalog.</span></span>  
  
 <span data-ttu-id="bbb2d-107">프로젝트 매개 변수와 패키지 매개 변수는 실행 시 패키지 내의 속성에 값을 할당하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-107">Project parameters and package parameters can be used to assign values to properties within packages at the time of execution.</span></span> <span data-ttu-id="bbb2d-108">일부 매개 변수 값은 패키지를 실행하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-108">Some parameters require values before the package can be executed.</span></span> <span data-ttu-id="bbb2d-109">환경 변수를 참조하는 매개 변수 값이 있는 경우 프로젝트에 해당 환경 참조가 있어야 프로젝트가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-109">Parameter values that reference environment variables require that the project has the corresponding environment reference prior to execution.</span></span>  
  
 <span data-ttu-id="bbb2d-110">**수행 작업**</span><span class="sxs-lookup"><span data-stu-id="bbb2d-110">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="bbb2d-111">프로젝트 속성 대화 상자 열기</span><span class="sxs-lookup"><span data-stu-id="bbb2d-111">Open the Project Properties dialog box</span></span>](#open_dialog)  
  
-   [<span data-ttu-id="bbb2d-112">일반 페이지의 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="bbb2d-112">Set the options on the General page</span></span>](#general)  
  
-   [<span data-ttu-id="bbb2d-113">권한 페이지의 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="bbb2d-113">Set the options on the Permissions page</span></span>](#permissions)  
  
##  <a name="open-the-project-properties-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="bbb2d-114">프로젝트 속성 대화 상자 열기</span><span class="sxs-lookup"><span data-stu-id="bbb2d-114">Open the Project Properties dialog box</span></span>  
  
1.  <span data-ttu-id="bbb2d-115">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-115">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="bbb2d-116">SSISDB 데이터베이스를 호스팅하는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-116">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the SSISDB database.</span></span>  
  
2.  <span data-ttu-id="bbb2d-117">개체 탐색기에서 트리를 확장하여 **Integration Services 카탈로그** 노드를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-117">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="bbb2d-118">**SSISDB** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-118">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="bbb2d-119">속성을 설정할 프로젝트가 포함된 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-119">Expand the folder that contains the project that you want to set properties for.</span></span>  
  
5.  <span data-ttu-id="bbb2d-120">프로젝트를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-120">Right-click the project, and then click **Properties**.</span></span>  
  
##  <a name="set-the-options-on-the-general-page"></a><a name="general"></a> <span data-ttu-id="bbb2d-121">일반 페이지의 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="bbb2d-121">Set the options on the General page</span></span>  
 <span data-ttu-id="bbb2d-122">일반 페이지를 사용하여 프로젝트 속성을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-122">Use the General page to view project properties.</span></span>  
  
 <span data-ttu-id="bbb2d-123">**이름**</span><span class="sxs-lookup"><span data-stu-id="bbb2d-123">**Name**</span></span>  
 <span data-ttu-id="bbb2d-124">프로젝트 이름을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-124">Lists the project name.</span></span>  
  
 <span data-ttu-id="bbb2d-125">**식별자**</span><span class="sxs-lookup"><span data-stu-id="bbb2d-125">**Identifier**</span></span>  
 <span data-ttu-id="bbb2d-126">프로젝트 ID를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-126">Lists the project ID.</span></span>  
  
 <span data-ttu-id="bbb2d-127">**설명**</span><span class="sxs-lookup"><span data-stu-id="bbb2d-127">**Description**</span></span>  
 <span data-ttu-id="bbb2d-128">프로젝트에 대한 설명(옵션)을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-128">Displays the optional description of the project.</span></span>  
  
 <span data-ttu-id="bbb2d-129">**프로젝트 버전**</span><span class="sxs-lookup"><span data-stu-id="bbb2d-129">**Project Version**</span></span>  
 <span data-ttu-id="bbb2d-130">프로젝트 버전을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-130">Lists the project version.</span></span>  
  
 <span data-ttu-id="bbb2d-131">**배포 날짜**</span><span class="sxs-lookup"><span data-stu-id="bbb2d-131">**Deployment Date**</span></span>  
 <span data-ttu-id="bbb2d-132">프로젝트를 마지막으로 배포하거나 다시 배포한 날짜 및 시간을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-132">Lists the date and time the project was deployed or redeployed.</span></span>  
  
##  <a name="set-the-options-on-the-permissions-page"></a><a name="permissions"></a> <span data-ttu-id="bbb2d-133">권한 페이지의 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="bbb2d-133">Set the options on the Permissions page</span></span>  
 <span data-ttu-id="bbb2d-134">**권한** 페이지를 사용하여 프로젝트에 대한 명시적 권한을 보고 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-134">Use the **Permissions** page to view and set explicit permissions for the project.</span></span>  
  
 <span data-ttu-id="bbb2d-135">찾아보기</span><span class="sxs-lookup"><span data-stu-id="bbb2d-135">Browse</span></span>  
 <span data-ttu-id="bbb2d-136">**찾아보기** 를 클릭하여 **모든 보안 주체 찾아보기** 대화 상자를 사용하여 권한을 설정하려는 사용자 및 역할을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-136">Click **Browse** to select users and roles that you want to set permissions for, by using the **Browse All Principals** dialog box.</span></span>  
  
 <span data-ttu-id="bbb2d-137">**이름**</span><span class="sxs-lookup"><span data-stu-id="bbb2d-137">**Name**</span></span>  
 <span data-ttu-id="bbb2d-138">사용자 또는 역할의 이름을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-138">Lists the name of the user or role.</span></span>  
  
 <span data-ttu-id="bbb2d-139">**형식**</span><span class="sxs-lookup"><span data-stu-id="bbb2d-139">**Type**</span></span>  
 <span data-ttu-id="bbb2d-140">사용자 또는 역할의 유형을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-140">Lists the type of user or role.</span></span>  
  
 <span data-ttu-id="bbb2d-141">**사용 권한**</span><span class="sxs-lookup"><span data-stu-id="bbb2d-141">**Permission**</span></span>  
 <span data-ttu-id="bbb2d-142">사용 권한을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-142">Lists the permissions.</span></span>  
  
 <span data-ttu-id="bbb2d-143">**Grantor**</span><span class="sxs-lookup"><span data-stu-id="bbb2d-143">**Grantor**</span></span>  
 <span data-ttu-id="bbb2d-144">사용 권한을 부여하는 사용자 또는 역할을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-144">Lists the user or role that grants the permission.</span></span>  
  
 <span data-ttu-id="bbb2d-145">**허용**</span><span class="sxs-lookup"><span data-stu-id="bbb2d-145">**Grant**</span></span>  
 <span data-ttu-id="bbb2d-146">**권한 부여** 를 선택하면 선택한 사용자 또는 역할에 사용 권한이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-146">When **Grant** is selected, the permission is granted for the selected user or role.</span></span>  
  
 <span data-ttu-id="bbb2d-147">**거부**</span><span class="sxs-lookup"><span data-stu-id="bbb2d-147">**Deny**</span></span>  
 <span data-ttu-id="bbb2d-148">**거부** 를 선택하면 선택한 사용자 또는 역할에 대해 사용 권한이 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2d-148">When **Deny** is selected, the permission is denied for the selected user or role.</span></span>  
  
  
