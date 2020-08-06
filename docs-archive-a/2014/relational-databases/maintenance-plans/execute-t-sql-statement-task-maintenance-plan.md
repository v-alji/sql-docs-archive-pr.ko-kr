---
title: T-SQL 문 실행 태스크(유지 관리 계획) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.tsql.f1
helpviewer_keywords:
- Execute T-SQL Statement Task dialog box
ms.assetid: fef3e259-0c47-4f6e-ade0-aee95e3d6c1a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 63738758ce228a51ab6c75eb11a681eec3b27352
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653352"
---
# <a name="execute-t-sql-statement-task-maintenance-plan"></a><span data-ttu-id="2f2cb-102">T-SQL 문 실행 태스크(유지 관리 계획)</span><span class="sxs-lookup"><span data-stu-id="2f2cb-102">Execute T-SQL Statement Task (Maintenance Plan)</span></span>
  <span data-ttu-id="2f2cb-103">**T-SQL 문 실행 태스크** 대화 상자를 사용하여 선택한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 유지 관리 계획에 추가하여 유지 관리 계획을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f2cb-103">Use the **Execute T-SQL Statement Task** dialog to customize your maintenance plan by adding [!INCLUDE[tsql](../../includes/tsql-md.md)] statements of your choice to this maintenance plan.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2f2cb-104">옵션</span><span class="sxs-lookup"><span data-stu-id="2f2cb-104">Options</span></span>  
 <span data-ttu-id="2f2cb-105">**연결**</span><span class="sxs-lookup"><span data-stu-id="2f2cb-105">**Connection**</span></span>  
 <span data-ttu-id="2f2cb-106">이 태스크를 수행할 때 사용할 서버 연결을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2f2cb-106">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="2f2cb-107">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="2f2cb-107">**New**</span></span>  
 <span data-ttu-id="2f2cb-108">이 태스크를 수행할 때 사용할 새 서버 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2f2cb-108">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="2f2cb-109">아래에서는 **새 연결** 대화 상자에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2f2cb-109">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="2f2cb-110">**실행 제한 시간**</span><span class="sxs-lookup"><span data-stu-id="2f2cb-110">**Execution time out**</span></span>  
 <span data-ttu-id="2f2cb-111">태스크를 종료하기 전에 태스크가 완료되기를 기다리는 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="2f2cb-111">Time (seconds) to wait for task completion before timing out (terminating task).</span></span>  
  
 <span data-ttu-id="2f2cb-112">**T-SQL 문**</span><span class="sxs-lookup"><span data-stu-id="2f2cb-112">**T-SQL statement**</span></span>  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="2f2cb-113">문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2f2cb-113">statements to execute.</span></span>  
  
 <span data-ttu-id="2f2cb-114">**T-SQL 보기**</span><span class="sxs-lookup"><span data-stu-id="2f2cb-114">**View T-SQL**</span></span>  
 <span data-ttu-id="2f2cb-115">선택한 옵션을 기반으로 서버에 대해 수행한 이 태스크의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2f2cb-115">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2f2cb-116">영향을 받은 개체 수가 많은 경우에는 표시하는 데 시간이 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f2cb-116">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="2f2cb-117">새 연결 대화 상자</span><span class="sxs-lookup"><span data-stu-id="2f2cb-117">New Connection Dialog Box</span></span>  
 <span data-ttu-id="2f2cb-118">**연결 이름**</span><span class="sxs-lookup"><span data-stu-id="2f2cb-118">**Connection name**</span></span>  
 <span data-ttu-id="2f2cb-119">새 연결의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2f2cb-119">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="2f2cb-120">**서버 이름 선택 또는 입력**</span><span class="sxs-lookup"><span data-stu-id="2f2cb-120">**Select or enter a server name**</span></span>  
 <span data-ttu-id="2f2cb-121">이 태스크를 수행할 때 연결할 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2f2cb-121">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="2f2cb-122">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="2f2cb-122">**Refresh**</span></span>  
 <span data-ttu-id="2f2cb-123">사용할 수 있는 서버 목록을 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="2f2cb-123">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="2f2cb-124">**서버 로그온 정보 입력**</span><span class="sxs-lookup"><span data-stu-id="2f2cb-124">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="2f2cb-125">서버에 대한 인증 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f2cb-125">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="2f2cb-126">**Windows NT 통합 보안 사용**</span><span class="sxs-lookup"><span data-stu-id="2f2cb-126">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="2f2cb-127">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 인증을 사용하여 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2f2cb-127">Connect to an instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="2f2cb-128">**특정 사용자 이름 및 암호 사용**</span><span class="sxs-lookup"><span data-stu-id="2f2cb-128">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="2f2cb-129">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인증을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2f2cb-129">Connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="2f2cb-130">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2f2cb-130">This option is not available.</span></span>  
  
 <span data-ttu-id="2f2cb-131">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="2f2cb-131">**User name**</span></span>  
 <span data-ttu-id="2f2cb-132">인증 시 사용할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2f2cb-132">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="2f2cb-133">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2f2cb-133">This option is not available.</span></span>  
  
 <span data-ttu-id="2f2cb-134">**암호**</span><span class="sxs-lookup"><span data-stu-id="2f2cb-134">**Password**</span></span>  
 <span data-ttu-id="2f2cb-135">인증 시 사용할 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2f2cb-135">Provide a password to use when authenticating.</span></span> <span data-ttu-id="2f2cb-136">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2f2cb-136">This option is not available.</span></span>  
  
  
