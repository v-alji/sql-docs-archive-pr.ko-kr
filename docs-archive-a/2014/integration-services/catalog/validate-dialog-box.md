---
title: 유효성 검사 대화 상자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.ispackagevalidate.f1
- sql12.ssis.ssms.isprojectvalidate.f1
ms.assetid: 134e14ce-4f8d-4a20-889a-918014c841d8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 69e29d106dc9f4f100bf191911c5c34e0250be8f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647170"
---
# <a name="validate-dialog-box"></a><span data-ttu-id="8a7bb-102">유효성 검사 대화 상자</span><span class="sxs-lookup"><span data-stu-id="8a7bb-102">Validate Dialog Box</span></span>
  <span data-ttu-id="8a7bb-103">**유효성 검사** 대화 상자에서는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트 또는 패키지의 일반적인 문제를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a7bb-103">Use the **Validate** dialog box to check for common problems in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] a project or package.</span></span>  
  
 <span data-ttu-id="8a7bb-104">문제가 있는 경우 대화 상자의 맨 위에 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a7bb-104">If there is a problem, a message is displayed at the top of the dialog box.</span></span> <span data-ttu-id="8a7bb-105">그렇지 않으면 준비가 맨 위에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a7bb-105">Otherwise, the term Ready displays at the top.</span></span>  
  
 <span data-ttu-id="8a7bb-106">**수행 작업**</span><span class="sxs-lookup"><span data-stu-id="8a7bb-106">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="8a7bb-107">유효성 검사 대화 상자 열기</span><span class="sxs-lookup"><span data-stu-id="8a7bb-107">Open the Validate dialog box</span></span>](#open_dialog)  
  
-   [<span data-ttu-id="8a7bb-108">일반 페이지의 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="8a7bb-108">Set the options on the General page</span></span>](#general)  
  
##  <a name="open-the-validate-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="8a7bb-109">유효성 검사 대화 상자 열기</span><span class="sxs-lookup"><span data-stu-id="8a7bb-109">Open the Validate dialog box</span></span>  
  
1.  <span data-ttu-id="8a7bb-110">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8a7bb-110">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="8a7bb-111">SSISDB 데이터베이스를 호스팅하는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8a7bb-111">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the SSISDB database.</span></span>  
  
2.  <span data-ttu-id="8a7bb-112">개체 탐색기에서 트리를 확장하여 **Integration Services 카탈로그** 노드를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8a7bb-112">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="8a7bb-113">**SSISDB** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8a7bb-113">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="8a7bb-114">유효성을 검사하려는 프로젝트 또는 패키지가 포함된 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8a7bb-114">Expand the folder that contains the project or package you want to validate.</span></span>  
  
5.  <span data-ttu-id="8a7bb-115">프로젝트 또는 패키지를 마우스 오른쪽 단추로 클릭하고 **유효성 검사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8a7bb-115">Right-click the package or package, and then click **Validate**.</span></span>  
  
##  <a name="set-the-options-on-the-general-page"></a><a name="general"></a> <span data-ttu-id="8a7bb-116">일반 페이지의 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="8a7bb-116">Set the options on the General page</span></span>  
 <span data-ttu-id="8a7bb-117">**환경**</span><span class="sxs-lookup"><span data-stu-id="8a7bb-117">**Environment**</span></span>  
 <span data-ttu-id="8a7bb-118">프로젝트 또는 패키지의 유효성을 검사하기 위해 사용하려는 환경을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8a7bb-118">Select the environment that you want to use to validate the project or package.</span></span>  
  
 <span data-ttu-id="8a7bb-119">**32비트 런타임**</span><span class="sxs-lookup"><span data-stu-id="8a7bb-119">**32-bit runtime**</span></span>  
 <span data-ttu-id="8a7bb-120">패키지를 실행하기 위해 32비트 런타임을 사용하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8a7bb-120">Select to use a 32-bit runtime to execute a package.</span></span>  
  
 <span data-ttu-id="8a7bb-121">**매개 변수** 탭에는 프로젝트 또는 패키지의 유효성을 검사하기 위해 사용하는 매개 변수 값이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a7bb-121">The **Parameters** tab lists the parameter values that you use to validate the project or package.</span></span> <span data-ttu-id="8a7bb-122">다음은 매개 변수 탭의 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="8a7bb-122">The following are the options on the Parameters tab.</span></span>  
  
 <span data-ttu-id="8a7bb-123">**컨테이너**</span><span class="sxs-lookup"><span data-stu-id="8a7bb-123">**Container**</span></span>  
 <span data-ttu-id="8a7bb-124">매개 변수가 포함된 개체를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8a7bb-124">Lists the object that contains the parameter.</span></span>  
  
 <span data-ttu-id="8a7bb-125">**매개 변수**</span><span class="sxs-lookup"><span data-stu-id="8a7bb-125">**Parameter**</span></span>  
 <span data-ttu-id="8a7bb-126">매개 변수 이름을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8a7bb-126">Lists the name of the parameters</span></span>  
  
 <span data-ttu-id="8a7bb-127">**값**</span><span class="sxs-lookup"><span data-stu-id="8a7bb-127">**Value**</span></span>  
 <span data-ttu-id="8a7bb-128">매개 변수 값을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8a7bb-128">Lists the parameter value.</span></span>  
  
 <span data-ttu-id="8a7bb-129">**연결 관리자** 탭에는 프로젝트 또는 패키지의 유효성 검사를 위해 사용하는 연결 관리자 속성이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a7bb-129">The **Connection Managers** tab lists the connection manager property values that you use to validate the project or package.</span></span>  
  
 <span data-ttu-id="8a7bb-130">다음은 **연결 관리자** 탭의 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="8a7bb-130">The following are the options on the **Connection Managers** tab.</span></span>  
  
 <span data-ttu-id="8a7bb-131">**컨테이너**</span><span class="sxs-lookup"><span data-stu-id="8a7bb-131">**Container**</span></span>  
 <span data-ttu-id="8a7bb-132">연결 관리자 이름이 포함된 개체를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8a7bb-132">Lists the object that contains the connection manager.</span></span>  
  
 <span data-ttu-id="8a7bb-133">**이름**</span><span class="sxs-lookup"><span data-stu-id="8a7bb-133">**Name**</span></span>  
 <span data-ttu-id="8a7bb-134">연결 관리자 이름을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8a7bb-134">Lists the connection manager name.</span></span>  
  
 <span data-ttu-id="8a7bb-135">**속성 이름**</span><span class="sxs-lookup"><span data-stu-id="8a7bb-135">**Property name**</span></span>  
 <span data-ttu-id="8a7bb-136">연결 관리자 속성 이름을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8a7bb-136">Lists the name of the connection manager property.</span></span>  
  
 <span data-ttu-id="8a7bb-137">**값**</span><span class="sxs-lookup"><span data-stu-id="8a7bb-137">**Value**</span></span>  
 <span data-ttu-id="8a7bb-138">연결 관리자 속성에 할당된 값을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8a7bb-138">Lists the value assigned to the connection manager property.</span></span>  
  
  
