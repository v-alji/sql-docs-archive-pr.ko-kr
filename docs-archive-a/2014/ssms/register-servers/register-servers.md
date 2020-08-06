---
title: 서버 등록
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqlserverregisteredserver.dhelp
helpviewer_keywords:
- connections [SQL Server], registered servers
- registering servers
- servers [SQL Server], registering
- server management [SQL Server], registering servers
- server registration [SQL Server]
ms.assetid: c2a2513e-fa09-419c-99e7-a12d57c5a0db
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f4b23ba127c6b000b0abbe832c4c072ada78c5e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649309"
---
# <a name="register-servers"></a><span data-ttu-id="0fa60-102">서버 등록</span><span class="sxs-lookup"><span data-stu-id="0fa60-102">Register Servers</span></span>
  <span data-ttu-id="0fa60-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에 서버를 등록하면 나중에 연결하기 위한 서버 연결 정보를 저장할 수 있습니다. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에 서버를 등록하는 방법은 3가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fa60-103">Registering a server in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] allows you to store the server connection information for future connections.There are three ways to register a server in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
1.  <span data-ttu-id="0fa60-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 로컬 인스턴스는 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 를 설치한 후 처음 시작할 때 자동으로 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fa60-104">Local instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are automatically registered during the first launch of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] after its installation.</span></span>  
  
2.  <span data-ttu-id="0fa60-105">언제든지 자동 등록 과정을 시작하여 로컬 서버 인스턴스의 등록을 복원할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fa60-105">You can also initiate the automatic registration process at any time, to restore the registration of local server instances.</span></span>  
  
3.  <span data-ttu-id="0fa60-106">마지막으로 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 등록된 서버 도구를 사용하여 서버를 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fa60-106">Lastly, you can register a server using the Registered Servers tool in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="benefits-of-registered-servers"></a><span data-ttu-id="0fa60-107">등록된 서버의 이점</span><span class="sxs-lookup"><span data-stu-id="0fa60-107">Benefits of Registered Servers</span></span>  
 <span data-ttu-id="0fa60-108">등록된 서버를 사용하여 다음 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fa60-108">With Registered Servers you can:</span></span>  
  
-   <span data-ttu-id="0fa60-109">서버를 등록하여 연결 정보를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="0fa60-109">Register servers to preserve the connection information.</span></span>  
  
-   <span data-ttu-id="0fa60-110">등록된 서버가 실행 중인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0fa60-110">Determine if a registered server is running.</span></span>  
  
-   <span data-ttu-id="0fa60-111">개체 탐색기와 쿼리 편집기를 등록된 서버에 쉽게 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0fa60-111">Easily connect Object Explorer and Query Editor to a registered server.</span></span>  
  
-   <span data-ttu-id="0fa60-112">등록된 서버에 대한 등록 정보를 편집하거나 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="0fa60-112">Edit or delete the registration information for a registered server.</span></span>  
  
-   <span data-ttu-id="0fa60-113">서버 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0fa60-113">Create groups of servers.</span></span>  
  
-   <span data-ttu-id="0fa60-114">**서버 이름** 목록과 다른 **등록된 서버 이름** 상자에 값을 제공하여 등록된 서버에 대한 친숙한 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0fa60-114">Provide user-friendly names for registered servers by providing a value in the **Registered server name** box that is different from the **Server name** list.</span></span>  
  
-   <span data-ttu-id="0fa60-115">등록된 서버에 대한 세부적인 설명을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0fa60-115">Provide detailed descriptions for registered servers.</span></span>  
  
-   <span data-ttu-id="0fa60-116">등록된 서버 그룹에 대한 세부적인 설명을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0fa60-116">Provide detailed descriptions of registered server groups.</span></span>  
  
-   <span data-ttu-id="0fa60-117">등록된 서버 그룹을 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="0fa60-117">Export registered server groups.</span></span>  
  
-   <span data-ttu-id="0fa60-118">등록된 서버 그룹을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0fa60-118">Import registered server groups.</span></span>  
  
-   <span data-ttu-id="0fa60-119">온라인 또는 오프라인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로그 파일을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="0fa60-119">View the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files for online or offline instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="0fa60-120">관련 작업</span><span class="sxs-lookup"><span data-stu-id="0fa60-120">Related Tasks</span></span>  
 <span data-ttu-id="0fa60-121">등록된 서버를 시작하려면 다음 항목을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="0fa60-121">Use the following topics to get started with registered servers:</span></span>  
  
|<span data-ttu-id="0fa60-122">**설명**</span><span class="sxs-lookup"><span data-stu-id="0fa60-122">**Description**</span></span>|<span data-ttu-id="0fa60-123">**항목**</span><span class="sxs-lookup"><span data-stu-id="0fa60-123">**Topic**</span></span>|  
|---------------------|---------------|  
|<span data-ttu-id="0fa60-124">로컬 서버 인스턴스 등록</span><span class="sxs-lookup"><span data-stu-id="0fa60-124">Register local server instances</span></span>|[<span data-ttu-id="0fa60-125">연결된 서버 등록&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0fa60-125">Register a Connected Server &#40;SQL Server Management Studio&#41;</span></span>](register-a-connected-server-sql-server-management-studio.md)|  
|<span data-ttu-id="0fa60-126">서버 등록</span><span class="sxs-lookup"><span data-stu-id="0fa60-126">Register a server</span></span>|[<span data-ttu-id="0fa60-127">새 등록된 서버 만들기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0fa60-127">Create a New Registered Server &#40;SQL Server Management Studio&#41;</span></span>](create-a-new-registered-server-sql-server-management-studio.md)|  
|<span data-ttu-id="0fa60-128">등록된 서버 보기</span><span class="sxs-lookup"><span data-stu-id="0fa60-128">View registered servers</span></span>|[<span data-ttu-id="0fa60-129">SQL Server Management Studio에서 등록된 서버 보기</span><span class="sxs-lookup"><span data-stu-id="0fa60-129">View Registered Servers in SQL Server Management Studio</span></span>](view-registered-servers-in-sql-server-management-studio.md)|  
|<span data-ttu-id="0fa60-130">등록된 서버 제거</span><span class="sxs-lookup"><span data-stu-id="0fa60-130">Remove a registered server</span></span>|[<span data-ttu-id="0fa60-131">등록된 서버 제거&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0fa60-131">Remove a Registered Server &#40;SQL Server Management Studio&#41;</span></span>](remove-a-registered-server-sql-server-management-studio.md)|  
|<span data-ttu-id="0fa60-132">서버 등록 변경</span><span class="sxs-lookup"><span data-stu-id="0fa60-132">Change a server's registration</span></span>|[<span data-ttu-id="0fa60-133">서버 등록 변경&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0fa60-133">Change a Server's Registration &#40;SQL Server Management Studio&#41;</span></span>](change-a-server-s-registration-sql-server-management-studio.md)|  
|<span data-ttu-id="0fa60-134">등록된 서버에 연결</span><span class="sxs-lookup"><span data-stu-id="0fa60-134">Connect to a registered server</span></span>|[<span data-ttu-id="0fa60-135">등록된 서버에 연결&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0fa60-135">Connect to a Registered Server &#40;SQL Server Management Studio&#41;</span></span>](connect-to-a-registered-server-sql-server-management-studio.md)|  
|<span data-ttu-id="0fa60-136">등록된 서버에서 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="0fa60-136">Disconnect from a registered server</span></span>|[<span data-ttu-id="0fa60-137">등록된 서버에서 연결 끊기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0fa60-137">Disconnect from a Registered Server &#40;SQL Server Management Studio&#41;</span></span>](disconnect-from-a-registered-server-sql-server-management-studio.md)|  
|<span data-ttu-id="0fa60-138">등록된 서버 또는 서버 그룹 이동</span><span class="sxs-lookup"><span data-stu-id="0fa60-138">Move a registered server or server group</span></span>|[<span data-ttu-id="0fa60-139">등록된 서버 및 등록된 서버 그룹 이동&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0fa60-139">Move a Registered Server or Registered Server Group &#40;SQL Server Management Studio&#41;</span></span>](move-a-registered-server-or-registered-server-group.md)|  
|<span data-ttu-id="0fa60-140">등록된 서버 또는 등록된 서버 그룹 이름 변경</span><span class="sxs-lookup"><span data-stu-id="0fa60-140">Change the name of a registered server or server group</span></span>|[<span data-ttu-id="0fa60-141">등록된 서버 또는 등록된 서버 그룹 이름 변경&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0fa60-141">Change the Name of a Registered Server or Registered Server Group &#40;SQL Server Management Studio&#41;</span></span>](change-the-name-of-registered-server-or-registered-server-group.md)|  
|<span data-ttu-id="0fa60-142">서버 그룹 만들기 또는 편집</span><span class="sxs-lookup"><span data-stu-id="0fa60-142">Create or edit a server group</span></span>|[<span data-ttu-id="0fa60-143">서버 그룹 만들기 또는 편집&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0fa60-143">Create or Edit a Server Group &#40;SQL Server Management Studio&#41;</span></span>](create-or-edit-a-server-group-sql-server-management-studio.md)|  
|<span data-ttu-id="0fa60-144">서버 그룹 제거</span><span class="sxs-lookup"><span data-stu-id="0fa60-144">Remove a server group</span></span>|[<span data-ttu-id="0fa60-145">서버 그룹 제거&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0fa60-145">Remove a Server Group &#40;SQL Server Management Studio&#41;</span></span>](remove-a-server-group-sql-server-management-studio.md)|  
|<span data-ttu-id="0fa60-146">등록된 서버 정보 내보내기</span><span class="sxs-lookup"><span data-stu-id="0fa60-146">Export registered server information</span></span>|[<span data-ttu-id="0fa60-147">등록된 서버 정보 내보내기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0fa60-147">Export Registered Server Information &#40;SQL Server Management Studio&#41;</span></span>](export-registered-server-information-sql-server-management-studio.md)|  
|<span data-ttu-id="0fa60-148">등록된 서버 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="0fa60-148">Import registered server information</span></span>|[<span data-ttu-id="0fa60-149">등록된 서버 정보 가져오기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0fa60-149">Import Registered Server Information &#40;SQL Server Management Studio&#41;</span></span>](import-registered-server-information-sql-server-management-studio.md)|  
|<span data-ttu-id="0fa60-150">중앙 관리 서버 및 서버 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="0fa60-150">Create a Central Management Server and Server Group</span></span>|[<span data-ttu-id="0fa60-151">중앙 관리 서버 및 서버 그룹 만들기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0fa60-151">Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;</span></span>](create-a-central-management-server-and-server-group.md)|  
|<span data-ttu-id="0fa60-152">여러 서버에 대해 동시에 문 실행</span><span class="sxs-lookup"><span data-stu-id="0fa60-152">Execute statements against multiple servers simultaneously</span></span>|[<span data-ttu-id="0fa60-153">여러 서버에 대해 동시에 문 실행&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0fa60-153">Execute Statements Against Multiple Servers Simultaneously &#40;SQL Server Management Studio&#41;</span></span>](execute-statements-against-multiple-servers-simultaneously.md)|  
  
## <a name="see-also"></a><span data-ttu-id="0fa60-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0fa60-154">See Also</span></span>  
 [<span data-ttu-id="0fa60-155">원격 서버</span><span class="sxs-lookup"><span data-stu-id="0fa60-155">Remote Servers</span></span>](../../database-engine/configure-windows/remote-servers.md)  
  
  
