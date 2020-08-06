---
title: 원본 선택 대화 상자 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.selectsource.f1
ms.assetid: d664c2e5-dd0c-4da8-b27d-aa4ee4fc0ffd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 535d211d6827477fcf029accc27a9000e8c695c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740855"
---
# <a name="select-source-dialog-box"></a><span data-ttu-id="ca8d5-102">원본 선택 대화 상자</span><span class="sxs-lookup"><span data-stu-id="ca8d5-102">Select Source Dialog Box</span></span>
  <span data-ttu-id="ca8d5-103">이 대화 상자를 사용하여 실행할 정책의 원본을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-103">Use this dialog box to select the source of the policies to be run.</span></span> <span data-ttu-id="ca8d5-104">정책이 포함된 하나 이상의 XML 파일을 선택하려면 **파일**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-104">To select one or more XML files that contain policies, select **Files**.</span></span> <span data-ttu-id="ca8d5-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 있는 정책을 실행하려면 **서버**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-105">To run the policies that are found on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], select **Server**.</span></span>  
  
 <span data-ttu-id="ca8d5-106">이 대화 상자는 여러 가지 방법으로 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-106">You can open this dialog box in several ways.</span></span>  
  
 <span data-ttu-id="ca8d5-107">**이 대화 상자를 열려면**</span><span class="sxs-lookup"><span data-stu-id="ca8d5-107">**To open this dialog box**</span></span>  
  
-   <span data-ttu-id="ca8d5-108">등록된 서버에서 **로컬 서버 그룹** , **로컬 서버 그룹**아래 서버 또는 **중앙 관리 서버**아래 서버를 마우스 오른쪽 단추로 클릭하고 **정책 평가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-108">In Registered Servers, right-click **Local Server Groups** or any server under **Local Server Groups**, or any server under **Central Management Servers**, and then select **Evaluate Policies**.</span></span> <span data-ttu-id="ca8d5-109">**정책 평가** 대화 상자에서 **정책 선택** 페이지에서 찾아보기 단추( **...** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-109">In the **Policy Selection** page of the **Evaluate Policies** dialog box, click the Browse (**...**) button.</span></span>  
  
-   <span data-ttu-id="ca8d5-110">개체 탐색기에서 **관리**, **정책 관리**를 차례로 확장한 다음 **정책**을 마우스 오른쪽 단추로 클릭하고 **정책 가져오기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-110">In Object Explorer, expand **Management**, expand **Policy Management**, right-click **Policies**, and select **Import Policy**.</span></span> <span data-ttu-id="ca8d5-111">**가져오기** 대화 상자에서 찾아보기( **...** ) 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-111">In the **Import** dialog box, click the Browse (**...**) button.</span></span>  
  
-   <span data-ttu-id="ca8d5-112">개체 탐색기에서 서버, 데이터베이스 또는 데이터베이스 개체를 마우스 오른쪽 단추로 클릭하고 **정책**을 선택한 다음 **평가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-112">In Object Explorer, right-click a server, database, or database object, select **Policies**, and then select **Evaluate**.</span></span> <span data-ttu-id="ca8d5-113">**정책 평가** 대화 상자에서 **정책 선택** 페이지에서 찾아보기 단추( **...** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-113">In the **Policy Selection** page of the **Evaluate Policies** dialog box, click the Browse (**...**) button.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ca8d5-114">옵션</span><span class="sxs-lookup"><span data-stu-id="ca8d5-114">Options</span></span>  
 <span data-ttu-id="ca8d5-115">**파일**</span><span class="sxs-lookup"><span data-stu-id="ca8d5-115">**Files**</span></span>  
 <span data-ttu-id="ca8d5-116">정책이 포함된 하나 이상의 XML 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-116">Select one or more XML files that contain policies.</span></span>  
  
 <span data-ttu-id="ca8d5-117">**Server**</span><span class="sxs-lookup"><span data-stu-id="ca8d5-117">**Server**</span></span>  
 <span data-ttu-id="ca8d5-118">실행할 정책이 포함된 서버를 선택할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-118">Enables you to select a server that contains the policies that you want to run.</span></span>  
  
 <span data-ttu-id="ca8d5-119">**서버 유형**</span><span class="sxs-lookup"><span data-stu-id="ca8d5-119">**Server type**</span></span>  
 <span data-ttu-id="ca8d5-120">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 서버만 정책을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-120">Only [!INCLUDE[ssDE](../../includes/ssde-md.md)] servers contain policies.</span></span> <span data-ttu-id="ca8d5-121">이 부분은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-121">This box is read-only.</span></span>  
  
 <span data-ttu-id="ca8d5-122">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="ca8d5-122">**Server name**</span></span>  
 <span data-ttu-id="ca8d5-123">연결할 서버 인스턴스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-123">Select the server instance to connect to.</span></span> <span data-ttu-id="ca8d5-124">마지막으로 연결한 서버 인스턴스가 기본적으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-124">By default, the server instance last connected to is displayed.</span></span>  
  
 <span data-ttu-id="ca8d5-125">**인증**</span><span class="sxs-lookup"><span data-stu-id="ca8d5-125">**Authentication**</span></span>  
 <span data-ttu-id="ca8d5-126">[!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결할 때는 두 가지 인증 모드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-126">Two authentication modes are available when you connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="ca8d5-127">**Windows 인증 모드(Windows 인증)**</span><span class="sxs-lookup"><span data-stu-id="ca8d5-127">**Windows Authentication Mode (Windows Authentication)**</span></span>  
 <span data-ttu-id="ca8d5-128">Windows 인증 모드에서는 사용자가 Windows 사용자 계정을 통해 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-128">Windows Authentication mode allows for a user to connect through a Windows user account.</span></span>  
  
 <span data-ttu-id="ca8d5-129">**SQL Server 인증**</span><span class="sxs-lookup"><span data-stu-id="ca8d5-129">**SQL Server Authentication**</span></span>  
 <span data-ttu-id="ca8d5-130">사용자가 지정한 로그인 이름과 암호를 사용하여 트러스트되지 않은 연결로부터 연결하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인 계정이 설정되고 지정한 암호가 전에 기록한 암호와 일치하는지를 확인하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 자체적으로 인증을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-130">When a user connects with a specified login name and password from a nontrusted connection, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs the authentication itself by checking whether a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login account has been set up and whether the specified password matches the one previously recorded.</span></span> <span data-ttu-id="ca8d5-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 로그인 계정이 설정되어 있지 않으면 인증이 실패하고 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-131">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not have a login account set, authentication fails, and the user receives an error message.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ca8d5-132">가능하면 Windows 인증을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-132">When possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="ca8d5-133">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="ca8d5-133">**User name**</span></span>  
 <span data-ttu-id="ca8d5-134">연결에 사용할 사용자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-134">Enter the user name to connect with.</span></span> <span data-ttu-id="ca8d5-135">이 옵션은 Windows 인증을 사용하여 연결하도록 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-135">This option is available only if you have selected to connect by using Windows Authentication.</span></span>  
  
 <span data-ttu-id="ca8d5-136">**로그인**</span><span class="sxs-lookup"><span data-stu-id="ca8d5-136">**Login**</span></span>  
 <span data-ttu-id="ca8d5-137">연결 시 사용할 로그인을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-137">Enter the login to connect with.</span></span> <span data-ttu-id="ca8d5-138">이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 연결하도록 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-138">This option is available only if you have selected to connect by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="ca8d5-139">**암호**</span><span class="sxs-lookup"><span data-stu-id="ca8d5-139">**Password**</span></span>  
 <span data-ttu-id="ca8d5-140">로그인 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-140">Enter the password for the login.</span></span> <span data-ttu-id="ca8d5-141">이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 연결하도록 선택한 경우에만 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca8d5-141">This option is editable only if you have selected to connect by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca8d5-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ca8d5-142">See Also</span></span>  
 <span data-ttu-id="ca8d5-143">[정책 관리 노드&#40;개체 탐색기&#41;](../../ssms/object/object-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="ca8d5-143">[Policy Management Node &#40;Object Explorer&#41;](../../ssms/object/object-explorer.md) </span></span>  
 [<span data-ttu-id="ca8d5-144">정책 기반 관리를 사용하여 서버 관리</span><span class="sxs-lookup"><span data-stu-id="ca8d5-144">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
