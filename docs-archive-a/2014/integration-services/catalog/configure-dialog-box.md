---
title: 구성 대화 상자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.SSIS.SSMS.ISPROJECTPROP.PARAMETERS.F1
- SQL12.SSIS.SSMS.ISPROJECTPROP.REFERENCES.F1
- sql12.dts.designer.configure.f1
ms.assetid: 10183c8d-b1be-420f-972a-96ea97d4f4d8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 857baf3421f2744144e10b0df0b770538f533192
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652286"
---
# <a name="configure-dialog-box"></a><span data-ttu-id="1f7a0-102">구성 대화 상자</span><span class="sxs-lookup"><span data-stu-id="1f7a0-102">Configure Dialog Box</span></span>
  <span data-ttu-id="1f7a0-103">**구성** 대화 상자를 사용하여 패키지 및 프로젝트에 대한 매개 변수, 연결 관리자, 환경 참조 등을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-103">Use the **Configure** dialog box to configure parameters, connection managers, and references to environments, for packages and projects.</span></span>  
  
 <span data-ttu-id="1f7a0-104">**수행 작업**</span><span class="sxs-lookup"><span data-stu-id="1f7a0-104">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="1f7a0-105">구성 대화 상자 열기</span><span class="sxs-lookup"><span data-stu-id="1f7a0-105">Open the Configure Dialog Box</span></span>](#open_dialog)  
  
-   [<span data-ttu-id="1f7a0-106">매개 변수 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="1f7a0-106">Set the options on the Parameters page</span></span>](#parameter)  
  
-   [<span data-ttu-id="1f7a0-107">참조 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="1f7a0-107">Set the options on the References page</span></span>](#references)  
  
##  <a name="open-the-configure-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="1f7a0-108">구성 대화 상자 열기</span><span class="sxs-lookup"><span data-stu-id="1f7a0-108">Open the Configure Dialog Box</span></span>  
  
1.  <span data-ttu-id="1f7a0-109">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="1f7a0-110">SSISDB 데이터베이스를 호스팅하는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-110">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the SSISDB database.</span></span>  
  
2.  <span data-ttu-id="1f7a0-111">개체 탐색기에서 트리를 확장하여 **Integration Services 카탈로그** 노드를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-111">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="1f7a0-112">**SSISDB** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-112">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="1f7a0-113">구성할 패키지 또는 프로젝트가 포함된 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-113">Expand the folder that contains the package or project that you want to configure.</span></span>  
  
5.  <span data-ttu-id="1f7a0-114">패키지 또는 프로젝트를 다시 마우스 오른쪽 단추로 클릭한 다음 **구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-114">Right-click the package or project, and then click **Configure**.</span></span>  
  
##  <a name="set-the-options-on-the-parameters-page"></a><a name="parameter"></a> <span data-ttu-id="1f7a0-115">매개 변수 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="1f7a0-115">Set the options on the Parameters page</span></span>  
 <span data-ttu-id="1f7a0-116">**매개 변수** 페이지를 사용하여 매개 변수 이름 및 값을 확인한 후 값을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-116">Use the **Parameters** page to view parameter names and values, and to modify the values.</span></span>  
  
 <span data-ttu-id="1f7a0-117">**범위** 드롭다운 목록에서 **매개 변수** 및 **연결 관리자** 탭에 표시된 매개 변수의 범위를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-117">Select the scope of the parameters displayed in the **Parameters** and **Connection Managers** tabs, in the **Scope** drop-down list.</span></span>  
  
 <span data-ttu-id="1f7a0-118">다음은 **매개 변수** 탭의 옵션 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-118">The following is a list of the options in the **Parameters** tab.</span></span>  
  
 <span data-ttu-id="1f7a0-119">**컨테이너**</span><span class="sxs-lookup"><span data-stu-id="1f7a0-119">**Container**</span></span>  
 <span data-ttu-id="1f7a0-120">매개 변수가 포함된 개체를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-120">Lists the object that contains the parameter.</span></span>  
  
 <span data-ttu-id="1f7a0-121">**이름**</span><span class="sxs-lookup"><span data-stu-id="1f7a0-121">**Name**</span></span>  
 <span data-ttu-id="1f7a0-122">매개 변수 이름을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-122">Lists the parameter name.</span></span>  
  
 <span data-ttu-id="1f7a0-123">**값**</span><span class="sxs-lookup"><span data-stu-id="1f7a0-123">**Value**</span></span>  
 <span data-ttu-id="1f7a0-124">매개 변수 값을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-124">Lists the parameter value.</span></span> <span data-ttu-id="1f7a0-125">줄임표 단추를 클릭하여 **매개 변수 값 설정** 대화 상자의 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-125">Click the ellipsis button to change the value in the **Set Parameter Value** dialog box.</span></span>  
  
 <span data-ttu-id="1f7a0-126">다음은 **연결 관리자** 탭의 옵션 목록입니다. 연결 관리자 속성 값을 변경하려면 이 탭을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-126">The following is a list of the options in the **Connection Managers** tab. You use this tab to change values for connection manager properties.</span></span> <span data-ttu-id="1f7a0-127">속성에 대한 매개 변수가 SSIS 서버에 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-127">Parameters are automatically generated on the SSIS server for the properties.</span></span>  
  
 <span data-ttu-id="1f7a0-128">**컨테이너**</span><span class="sxs-lookup"><span data-stu-id="1f7a0-128">**Container**</span></span>  
 <span data-ttu-id="1f7a0-129">연결 관리자 이름이 포함된 개체를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-129">Lists the object that contains the connection manager.</span></span>  
  
 <span data-ttu-id="1f7a0-130">**이름**</span><span class="sxs-lookup"><span data-stu-id="1f7a0-130">**Name**</span></span>  
 <span data-ttu-id="1f7a0-131">연결 관리자 이름을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-131">Lists the connection manager name.</span></span>  
  
 <span data-ttu-id="1f7a0-132">**속성 이름**</span><span class="sxs-lookup"><span data-stu-id="1f7a0-132">**Property name**</span></span>  
 <span data-ttu-id="1f7a0-133">연결 관리자 속성 이름을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-133">Lists the name of the connection manager property.</span></span>  
  
 <span data-ttu-id="1f7a0-134">**값**</span><span class="sxs-lookup"><span data-stu-id="1f7a0-134">**Value**</span></span>  
 <span data-ttu-id="1f7a0-135">연결 관리자 속성에 할당된 값을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-135">Lists the value assigned to the connection manager property.</span></span> <span data-ttu-id="1f7a0-136">줄임표 단추를 클릭하여 **매개 변수 값 설정** 대화 상자의 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-136">Click the ellipsis button to change the value in the **Set Parameter Value** dialog box.</span></span> <span data-ttu-id="1f7a0-137">리터럴 값을 입력하거나 사용하려는 값이 포함된 환경 변수를 매핑하거나, 패키지의 기본값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-137">You can enter a literal value, map an environment variable that contains the value you want to use, or use the default value from the package.</span></span>  
  
##  <a name="set-the-options-on-the-references-page"></a><a name="references"></a> <span data-ttu-id="1f7a0-138">참조 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="1f7a0-138">Set the options on the References page</span></span>  
 <span data-ttu-id="1f7a0-139">**참조** 페이지를 사용하여 환경에 대한 참조를 추가 및 제거하고 환경 속성에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-139">Use the **References** page to add and remove references to environments, and to access environment properties.</span></span>  
  
 <span data-ttu-id="1f7a0-140">환경에서는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 배포한 프로젝트에 포함된 패키지의 런타임 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-140">An environment specifies runtime values for packages contained in the projects you've deployed to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
 <span data-ttu-id="1f7a0-141">**환경**</span><span class="sxs-lookup"><span data-stu-id="1f7a0-141">**Environment**</span></span>  
 <span data-ttu-id="1f7a0-142">환경을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-142">Lists the environment.</span></span>  
  
 <span data-ttu-id="1f7a0-143">**환경 폴더**</span><span class="sxs-lookup"><span data-stu-id="1f7a0-143">**Environment Folder**</span></span>  
 <span data-ttu-id="1f7a0-144">환경이 포함된 폴더를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-144">Lists the folder that contains the environment.</span></span>  
  
 <span data-ttu-id="1f7a0-145">**열기**</span><span class="sxs-lookup"><span data-stu-id="1f7a0-145">**Open**</span></span>  
 <span data-ttu-id="1f7a0-146">**환경 속성** 대화 상자를 열려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-146">Click to open the **Environment Properties** dialog box.</span></span>  
  
 <span data-ttu-id="1f7a0-147">**추가**</span><span class="sxs-lookup"><span data-stu-id="1f7a0-147">**Add**</span></span>  
 <span data-ttu-id="1f7a0-148">환경에 대한 참조를 추가하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-148">Click to add a reference to an environment.</span></span> <span data-ttu-id="1f7a0-149">**환경 찾아보기** 대화 상자에서 환경을 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-149">In the **Browse Environments** dialog box click an environment and then click **OK**.</span></span>  
  
 <span data-ttu-id="1f7a0-150">**SSISDB** 노드 아래의 모든 프로젝트 폴더에 포함된 환경을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-150">You can select an environment contained in any project folder under the **SSISDB** node.</span></span>  
  
 <span data-ttu-id="1f7a0-151">**제거**</span><span class="sxs-lookup"><span data-stu-id="1f7a0-151">**Remove**</span></span>  
 <span data-ttu-id="1f7a0-152">**참조** 영역에 나열된 환경을 클릭한 다음 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7a0-152">Click an environment listed in the **References** area, and then click **Remove**.</span></span>  
  
  
