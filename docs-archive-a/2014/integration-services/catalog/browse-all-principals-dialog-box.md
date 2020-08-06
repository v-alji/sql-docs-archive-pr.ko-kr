---
title: 모든 보안 주체 찾아보기 대화 상자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.browseprincipals.f1
ms.assetid: f11d2c5e-ee05-45f3-8dc2-0feb99b2f76f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c204411a4daace27745e46269cbcfa0ed33f323f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647182"
---
# <a name="browse-all-principals-dialog-box"></a><span data-ttu-id="370f1-102">모든 보안 주체 찾아보기 대화 상자</span><span class="sxs-lookup"><span data-stu-id="370f1-102">Browse All Principals Dialog Box</span></span>
  <span data-ttu-id="370f1-103">**모든 보안 주체 찾아보기** 대화 상자를 사용하여 데이터베이스 보안 주체를 선택한 후 선택한 프로젝트 또는 선택한 폴더에 포함된 모든 프로젝트에 대해 보안 주체가 가지는 권한을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="370f1-103">Use the **Browse All Principals** dialog box to select a database principal to change the principal's permissions on the selected project or on all projects contained in a selected folder.</span></span>  
  
 <span data-ttu-id="370f1-104">**수행 작업**</span><span class="sxs-lookup"><span data-stu-id="370f1-104">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="370f1-105">모든 보안 주체 찾아보기 대화 상자 열기</span><span class="sxs-lookup"><span data-stu-id="370f1-105">Open the Browse All Principals dialog box</span></span>](#open_dialog)  
  
-   [<span data-ttu-id="370f1-106">옵션 구성</span><span class="sxs-lookup"><span data-stu-id="370f1-106">Configure the Options</span></span>](#options)  
  
##  <a name="open-the-browse-all-principals-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="370f1-107">모든 보안 주체 찾아보기 대화 상자 열기</span><span class="sxs-lookup"><span data-stu-id="370f1-107">Open the Browse All Principals dialog box</span></span>  
  
1.  <span data-ttu-id="370f1-108">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="370f1-108">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="370f1-109">SSISDB 카탈로그를 호스팅하는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="370f1-109">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the SSISDB catalog.</span></span>  
  
2.  <span data-ttu-id="370f1-110">개체 탐색기에서 트리를 확장하여 **Integration Services 카탈로그** 노드를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="370f1-110">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="370f1-111">**SSISDB** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="370f1-111">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="370f1-112">선택한 폴더에 포함된 모든 프로젝트에 대해 보안 주체가 가지는 권한을 변경하려면 폴더를 마우스 오른쪽 단추로 클릭한 다음, **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="370f1-112">To change the principal's permissions on all projects contained in a selected folder, right-click the folder and then click **Properties**.</span></span>  
  
     <span data-ttu-id="370f1-113">선택한 프로젝트에 대해 보안 주체가 가지는 권한을 변경하려면 프로젝트가 포함된 폴더를 확장하고 프로젝트를 마우스 오른쪽 단추로 클릭한 다음, **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="370f1-113">To change the principal's permissions on a selected project, expand the folder that contains the project, right-click the project, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="370f1-114">**사용 권한** 페이지를 선택한 다음 **찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="370f1-114">Select the **Permissions** page, and then click **Browse**.</span></span>  
  
##  <a name="configure-the-options"></a><a name="options"></a> <span data-ttu-id="370f1-115">옵션 구성</span><span class="sxs-lookup"><span data-stu-id="370f1-115">Configure the Options</span></span>  
 <span data-ttu-id="370f1-116">이 페이지에는 SSISDB 데이터베이스의 sys.database_principals 카탈로그 뷰에 있는 보안 주체가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="370f1-116">This page displays the principals from the catalog view, sys.database_principals, of the SSISDB database.</span></span>  
  
 <span data-ttu-id="370f1-117">보안 주체를 선택한 후 **확인** 을 클릭하고 **모든 보안 주체 찾아보기** 대화 상자를 닫으면 선택한 보안 주체가 상위 대화 상자의 **사용 권한** 페이지에 있는 **로그인 또는 역할** 목록에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="370f1-117">Selecting principals adds them to the **Logins or roles** list on the **Permissions** page of the parent dialog box when you click **OK** and close the **Browse All Principals** dialog box.</span></span> <span data-ttu-id="370f1-118">**로그인 또는 역할** 목록에 보안 주체를 추가한 후에는 선택한 프로젝트에 대한 해당 보안 주체의 사용 권한을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="370f1-118">After adding principals to the **Logins or roles** list, you can change their permissions on the selected project.</span></span>  
  
 <span data-ttu-id="370f1-119">**선택 열**</span><span class="sxs-lookup"><span data-stu-id="370f1-119">**Selection column**</span></span>  
 <span data-ttu-id="370f1-120">상위 대화 상자의 **사용 권한** 페이지에 있는 **로그인 또는 역할** 목록에 보안 주체를 추가하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="370f1-120">Select to add the principal to the **Logins or roles** list on the **Permissions** page of the parent dialog box.</span></span>  
  
 <span data-ttu-id="370f1-121">**아이콘 열**</span><span class="sxs-lookup"><span data-stu-id="370f1-121">**Icon column**</span></span>  
 <span data-ttu-id="370f1-122">보안 주체의 **유형** 에 해당하는 아이콘입니다.</span><span class="sxs-lookup"><span data-stu-id="370f1-122">An icon that corresponds to the **Type** of the principal.</span></span>  
  
 <span data-ttu-id="370f1-123">**이름**</span><span class="sxs-lookup"><span data-stu-id="370f1-123">**Name**</span></span>  
 <span data-ttu-id="370f1-124">보안 주체의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="370f1-124">The name of the principal.</span></span>  
  
 <span data-ttu-id="370f1-125">**형식**</span><span class="sxs-lookup"><span data-stu-id="370f1-125">**Type**</span></span>  
 <span data-ttu-id="370f1-126">보안 주체의 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="370f1-126">The type of the principal.</span></span> <span data-ttu-id="370f1-127">일반적인 유형은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="370f1-127">The common types are:</span></span>  
  
-   <span data-ttu-id="370f1-128">SQL 사용자</span><span class="sxs-lookup"><span data-stu-id="370f1-128">SQL User</span></span>  
  
-   <span data-ttu-id="370f1-129">Windows 사용자</span><span class="sxs-lookup"><span data-stu-id="370f1-129">Windows User</span></span>  
  
-   <span data-ttu-id="370f1-130">데이터베이스 역할</span><span class="sxs-lookup"><span data-stu-id="370f1-130">Database Role</span></span>  
  
  
