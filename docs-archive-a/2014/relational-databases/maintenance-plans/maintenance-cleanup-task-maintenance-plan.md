---
title: 유지 관리 정리 태스크(유지 관리 계획) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.cleanup.f1
helpviewer_keywords:
- Maintenance Cleanup Task dialog box
ms.assetid: 022b679c-6799-4c13-9185-814224a20412
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9023881ff5cf5ba5ddd8c61aa179c5881162bf44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651673"
---
# <a name="maintenance-cleanup-task-maintenance-plan"></a><span data-ttu-id="ac79a-102">유지 관리 정리 태스크(유지 관리 계획)</span><span class="sxs-lookup"><span data-stu-id="ac79a-102">Maintenance Cleanup Task (Maintenance Plan)</span></span>
  <span data-ttu-id="ac79a-103">**유지 관리 정리 태스크** 를 사용하여 유지 관리 계획에서 만든 텍스트 보고서와 데이터베이스 백업 파일을 포함하여 유지 관리 계획과 관련된 오래된 파일을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-103">Use the **Maintenance Cleanup Task** to remove old files related to maintenance plans, including text reports created by maintenance plans and database backup files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ac79a-104">유지 관리 정리 태스크에서는 지정된 디렉터리의 하위 폴더에 있는 파일을 자동으로 삭제하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-104">The Maintenance Cleanup task does not automatically delete files in the subfolders of the specified directory.</span></span> <span data-ttu-id="ac79a-105">이 기능은 유지 관리 정리 태스크를 사용하여 파일을 삭제하는 악의적 공격의 가능성을 줄여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-105">This feature reduces the possibility of a malicious attack that uses the Maintenance Cleanup task to delete files.</span></span> <span data-ttu-id="ac79a-106">첫 번째 수준의 하위 폴더를 삭제하려는 경우 **첫 번째 수준의 하위 폴더 포함**을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-106">If you want to delete files in first-level subfolders, you must select **Include first-level subfolders**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ac79a-107">옵션</span><span class="sxs-lookup"><span data-stu-id="ac79a-107">Options</span></span>  
 <span data-ttu-id="ac79a-108">**연결**</span><span class="sxs-lookup"><span data-stu-id="ac79a-108">**Connection**</span></span>  
 <span data-ttu-id="ac79a-109">현재 연결을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-109">Displays the current connection.</span></span>  
  
 <span data-ttu-id="ac79a-110">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="ac79a-110">**New**</span></span>  
 <span data-ttu-id="ac79a-111">이 태스크를 수행할 때 사용할 새 서버 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-111">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="ac79a-112">아래에서는 **새 연결** 대화 상자에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-112">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="ac79a-113">**백업 파일**</span><span class="sxs-lookup"><span data-stu-id="ac79a-113">**Backup files**</span></span>  
 <span data-ttu-id="ac79a-114">백업 파일을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-114">Delete backup files.</span></span>  
  
 <span data-ttu-id="ac79a-115">**유지 관리 계획 텍스트 보고서**</span><span class="sxs-lookup"><span data-stu-id="ac79a-115">**Maintenance Plan text reports**</span></span>  
 <span data-ttu-id="ac79a-116">이전에 실행한 유지 관리 계획의 텍스트 보고서를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-116">Delete text reports of previously run maintenance plans.</span></span>  
  
 <span data-ttu-id="ac79a-117">**특정 파일 삭제**</span><span class="sxs-lookup"><span data-stu-id="ac79a-117">**Delete specific file**</span></span>  
 <span data-ttu-id="ac79a-118">**파일 이름** 상자에 표시되는 특정 파일을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-118">Delete the specific file provided in the **File name** box.</span></span>  
  
 <span data-ttu-id="ac79a-119">**파일 이름**</span><span class="sxs-lookup"><span data-stu-id="ac79a-119">**File name**</span></span>  
 <span data-ttu-id="ac79a-120">삭제할 파일의 경로와 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-120">Path and name of the file to be deleted.</span></span>  
  
 <span data-ttu-id="ac79a-121">**확장명에 따라 폴더 검색 및 파일 삭제**</span><span class="sxs-lookup"><span data-stu-id="ac79a-121">**Search folder and delete files based on an extension**</span></span>  
 <span data-ttu-id="ac79a-122">지정한 확장명을 가진 파일을 지정한 폴더에서 모두 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-122">Delete all files with the specified extension in the specified folder.</span></span> <span data-ttu-id="ac79a-123">예를 들어 Tuesday 폴더에서 확장명이 .bak인 백업 파일을 모두 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-123">Use this to delete multiple files at once, such as all backup files with the .bak extension, in the Tuesday folder.</span></span>  
  
 <span data-ttu-id="ac79a-124">**폴더**</span><span class="sxs-lookup"><span data-stu-id="ac79a-124">**Folder**</span></span>  
 <span data-ttu-id="ac79a-125">삭제할 파일이 있는 폴더의 경로와 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-125">Path and name of the folder containing the files to be deleted.</span></span>  
  
 <span data-ttu-id="ac79a-126">**파일 확장명**</span><span class="sxs-lookup"><span data-stu-id="ac79a-126">**File extension**</span></span>  
 <span data-ttu-id="ac79a-127">삭제할 파일의 파일 확장명을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-127">Provide the file extension of the files to be deleted.</span></span>  
  
 <span data-ttu-id="ac79a-128">**첫 번째 수준의 하위 폴더 포함**</span><span class="sxs-lookup"><span data-stu-id="ac79a-128">**Include first-level subfolders**</span></span>  
 <span data-ttu-id="ac79a-129">**폴더** 아래의 첫 번째 하위 폴더에서 **파일 확장명**에 지정된 확장명을 갖는 파일을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-129">Delete files with the extension specified for **File extension** from first-level subfolders under **Folder**.</span></span>  
  
 <span data-ttu-id="ac79a-130">**태스크 런타임에 파일의 보존 기간에 따라 파일 삭제**</span><span class="sxs-lookup"><span data-stu-id="ac79a-130">**Delete files based on the age of the file at task run time**</span></span>  
 <span data-ttu-id="ac79a-131">**다음보다 오래된 파일 삭제** 상자에 숫자와 시간 단위를 제공하여 삭제할 파일의 최소 보존 기간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-131">Specify the minimum age of the files that you want to delete by providing a number, and unit of time in the **Delete files older than the following** box.</span></span>  
  
 <span data-ttu-id="ac79a-132">**다음보다 오래된 파일 삭제**</span><span class="sxs-lookup"><span data-stu-id="ac79a-132">**Delete files older than the following**</span></span>  
 <span data-ttu-id="ac79a-133">숫자와 시간 단위(일, 주, 월 또는 년)를 제공하여 삭제할 파일의 최소 보존 기간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-133">Specify the minimum age of the files that you want to delete by providing a number, and unit of time (Day, Week, Month, or Year).</span></span> <span data-ttu-id="ac79a-134">지정한 시간대 이전의 파일은 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-134">Files older than the time frame specified will be deleted.</span></span>  
  
 <span data-ttu-id="ac79a-135">**T-SQL 보기**</span><span class="sxs-lookup"><span data-stu-id="ac79a-135">**View T-SQL**</span></span>  
 <span data-ttu-id="ac79a-136">선택한 옵션을 기반으로 서버에 대해 수행한 이 태스크의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-136">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ac79a-137">영향을 받은 개체 수가 많은 경우에는 표시하는 데 시간이 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-137">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="ac79a-138">새 연결 대화 상자</span><span class="sxs-lookup"><span data-stu-id="ac79a-138">New Connection Dialog Box</span></span>  
 <span data-ttu-id="ac79a-139">**연결 이름**</span><span class="sxs-lookup"><span data-stu-id="ac79a-139">**Connection name**</span></span>  
 <span data-ttu-id="ac79a-140">새 연결의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-140">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="ac79a-141">**서버 이름 선택 또는 입력**</span><span class="sxs-lookup"><span data-stu-id="ac79a-141">**Select or enter a server name**</span></span>  
 <span data-ttu-id="ac79a-142">이 태스크를 수행할 때 연결할 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-142">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="ac79a-143">**...**</span><span class="sxs-lookup"><span data-stu-id="ac79a-143">**...**</span></span>  
 <span data-ttu-id="ac79a-144">사용 가능한 서버 목록이 보이도록 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-144">Select to view the list of available servers.</span></span>  
  
 <span data-ttu-id="ac79a-145">**서버 로그온 정보 입력**</span><span class="sxs-lookup"><span data-stu-id="ac79a-145">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="ac79a-146">서버에 대한 인증 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-146">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="ac79a-147">**Windows NT 통합 보안 사용**</span><span class="sxs-lookup"><span data-stu-id="ac79a-147">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="ac79a-148">Microsoft Windows 인증을 사용하여 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-148">Connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] with Microsoft Windows Authentication.</span></span>  
  
 <span data-ttu-id="ac79a-149">**특정 사용자 이름 및 암호 사용**</span><span class="sxs-lookup"><span data-stu-id="ac79a-149">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="ac79a-150">SQL Server 인증을 사용하여 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-150">Connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] using SQL Server Authentication.</span></span> <span data-ttu-id="ac79a-151">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-151">This option is not available.</span></span>  
  
 <span data-ttu-id="ac79a-152">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="ac79a-152">**User name**</span></span>  
 <span data-ttu-id="ac79a-153">인증 시 사용할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-153">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="ac79a-154">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-154">This option is not available.</span></span>  
  
 <span data-ttu-id="ac79a-155">**암호**</span><span class="sxs-lookup"><span data-stu-id="ac79a-155">**Password**</span></span>  
 <span data-ttu-id="ac79a-156">인증 시 사용할 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-156">Provide a password to use when authenticating.</span></span> <span data-ttu-id="ac79a-157">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ac79a-157">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac79a-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ac79a-158">See Also</span></span>  
 [<span data-ttu-id="ac79a-159">유지 관리 계획</span><span class="sxs-lookup"><span data-stu-id="ac79a-159">Maintenance Plans</span></span>](maintenance-plans.md)  
  
  
