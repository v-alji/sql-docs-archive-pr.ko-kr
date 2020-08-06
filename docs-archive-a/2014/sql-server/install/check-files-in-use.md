---
title: 사용 중인 파일 검사 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ccd65867-d4c0-43b2-8361-7fd41c6f79ac
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 51505b0dece146b7f6fcdf982e6f88a5715357e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650509"
---
# <a name="check-files-in-use"></a><span data-ttu-id="8ccae-102">사용 중인 파일 확인</span><span class="sxs-lookup"><span data-stu-id="8ccae-102">Check Files In Use</span></span>
  <span data-ttu-id="8ccae-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 업데이트를 설치한 후 Windows가 다시 시작되지 않도록 하려면 사용 중인 파일 검사 페이지에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 업데이트 설치 프로그램에 필요한 파일을 사용 중인 프로세스를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccae-103">To avoid restarting Windows after you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] updates, use the Check Files in Use page to identify processes that are locking files required by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] update Setup program.</span></span>  
  
 <span data-ttu-id="8ccae-104">업데이트할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결된 애플리케이션 및 서비스를 모두 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccae-104">Stop all applications and services that make connections to the instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are being updated.</span></span> <span data-ttu-id="8ccae-105">이때 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 와 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]도 중지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccae-105">This includes stopping [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="8ccae-106">설치 중에 잠겨 있는 파일이 발견되면 설치가 끝난 후 컴퓨터를 다시 시작해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ccae-106">If Setup determines that files are locked during installation, you might have to restart your computer after installation is completed.</span></span> <span data-ttu-id="8ccae-107">필요한 경우 컴퓨터를 다시 시작하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ccae-107">If necessary, Setup prompts you to restart your computer.</span></span> <span data-ttu-id="8ccae-108">설치 프로그램에서 설치를 진행하는 동안 특정 서비스를 중지해야 했으면 설치를 마친 후 해당 서비스가 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ccae-108">If the Setup program must stop a service during installation, it will restart the service after installation is completed.</span></span>  
  
 <span data-ttu-id="8ccae-109">설치 후 컴퓨터를 다시 시작하지 않아도 되도록 하기 위해 파일을 사용 중인 프로세스의 목록이 설치 프로그램을 통해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ccae-109">To eliminate the requirement to restart your computer after installation, Setup displays a list of processes that are locking files.</span></span> <span data-ttu-id="8ccae-110">목록에 나와 있는 프로세스와 애플리케이션을 중지하거나 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccae-110">Stop or end the processes and applications in the list.</span></span> <span data-ttu-id="8ccae-111">그런 다음 **검사 새로 고침** 을 클릭하여 검사를 다시 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccae-111">Then click **Refresh check** to rerun the check.</span></span> <span data-ttu-id="8ccae-112">실행 중인 검사를 끝내려면 **검사 중지** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccae-112">Click **Stop check** to end a check that is running.</span></span> <span data-ttu-id="8ccae-113">잠겨 있는 파일이 없으면 테이블에 아무 것도 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ccae-113">If locked files are not found, the table is empty.</span></span> <span data-ttu-id="8ccae-114">잠긴 프로세스를 모두 닫거나 중지했으면 **다음** 을 클릭하여 작업을 계속 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccae-114">When all locked processes have been closed or stopped, click **Next** to continue.</span></span>  
  
 <span data-ttu-id="8ccae-115">설치 과정에서 로그 파일에 정보가 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ccae-115">Setup logs the information in the log files.</span></span> <span data-ttu-id="8ccae-116">로그 파일을 보는 방법은 [SQL Server 설치 로그 파일 보기 및 읽기](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md) 및 [방법: SQL Server 설치 로그 파일 읽기](https://go.microsoft.com/fwlink/?LinkID=134490)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ccae-116">For more information about how to view the log files, see [View and Read SQL Server Setup Log Files](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md) and [How to: Read a SQL Server Setup Log File](https://go.microsoft.com/fwlink/?LinkID=134490).</span></span>  
  
 <span data-ttu-id="8ccae-117">로그 파일에는 다음 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ccae-117">The following information is included in the log file:</span></span>  
  
-   <span data-ttu-id="8ccae-118">프로세스 이름</span><span class="sxs-lookup"><span data-stu-id="8ccae-118">Name of the process</span></span>  
  
-   <span data-ttu-id="8ccae-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기능 이름</span><span class="sxs-lookup"><span data-stu-id="8ccae-119">Name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] feature</span></span>  
  
-   <span data-ttu-id="8ccae-120">프로세스 유형</span><span class="sxs-lookup"><span data-stu-id="8ccae-120">Process type</span></span>  
  
-   <span data-ttu-id="8ccae-121">프로세스를 실행하는 데 사용된 계정</span><span class="sxs-lookup"><span data-stu-id="8ccae-121">Account under which the process is running</span></span>  
  
-   <span data-ttu-id="8ccae-122">프로세스 ID</span><span class="sxs-lookup"><span data-stu-id="8ccae-122">Process ID</span></span>  
  
-   <span data-ttu-id="8ccae-123">잠겨 있는 파일 이름</span><span class="sxs-lookup"><span data-stu-id="8ccae-123">Name of the file that is locked</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="8ccae-124">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="8ccae-124">UI element list</span></span>  
  
|<span data-ttu-id="8ccae-125">Name</span><span class="sxs-lookup"><span data-stu-id="8ccae-125">Name</span></span>|<span data-ttu-id="8ccae-126">Description</span><span class="sxs-lookup"><span data-stu-id="8ccae-126">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="8ccae-127">Process</span><span class="sxs-lookup"><span data-stu-id="8ccae-127">Process</span></span>|<span data-ttu-id="8ccae-128">업데이트해야 할 파일을 사용하고 있는 프로세스의 전체 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccae-128">Displays the full name of the process that is using the files to be updated.</span></span>|  
|<span data-ttu-id="8ccae-129">Type</span><span class="sxs-lookup"><span data-stu-id="8ccae-129">Type</span></span>|<span data-ttu-id="8ccae-130">프로세스의 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccae-130">Displays the type of process.</span></span>|  
|<span data-ttu-id="8ccae-131">계정</span><span class="sxs-lookup"><span data-stu-id="8ccae-131">Account</span></span>|<span data-ttu-id="8ccae-132">프로세스를 실행하는 데 사용된 계정을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccae-132">Displays the account under which the process is running.</span></span>|  
|<span data-ttu-id="8ccae-133">프로세스 ID</span><span class="sxs-lookup"><span data-stu-id="8ccae-133">Process ID</span></span>|<span data-ttu-id="8ccae-134">프로세스 ID를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccae-134">Displays the process ID.</span></span>|  
  
  
