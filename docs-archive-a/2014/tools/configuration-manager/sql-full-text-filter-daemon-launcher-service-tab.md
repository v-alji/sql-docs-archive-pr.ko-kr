---
title: SQL 전체 텍스트 필터 데몬 시작 관리자(서비스 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 6aad7ebe-c4be-4d37-8536-61502f51faa2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8f0d9c76d7d92947dd17fe2ed6e912e3d6baa6bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660228"
---
# <a name="sql-full-text-filter-daemon-launcher-service-tab"></a><span data-ttu-id="cf275-102">SQL 전체 텍스트 필터 데몬 시작 관리자(서비스 탭)</span><span class="sxs-lookup"><span data-stu-id="cf275-102">SQL Full-text Filter Daemon Launcher (Service Tab)</span></span>
  <span data-ttu-id="cf275-103">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]부터는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 전체 텍스트에서 SQL 전체 텍스트 필터 데몬 시작 관리자(FDHOST Launcher) 서비스가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf275-103">Beginning in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the SQL Full-text Filter Daemon Launcher (FDHOST Launcher) service is used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] full-text.</span></span> <span data-ttu-id="cf275-104">전체 텍스트 검색을 사용할 경우 이 서비스를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf275-104">This service must be running if you use full-text search.</span></span> <span data-ttu-id="cf275-105">필터 데몬 호스트 프로세스에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서의 "전체 텍스트 검색 아키텍처"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="cf275-105">For information about the filter daemon host processes, see "Full-Text Search Architecture" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="cf275-106">**SQL 전체 텍스트 필터 디먼 시작 관리자 속성**대화 상자의 **서비스** 탭을 사용하여 다음 옵션을 보거나 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf275-106">Use the **Service**tab on the **SQL Full-text Filter Daemon LauncherProperties** dialog box to view or specify the following options.</span></span>  
  
## <a name="options"></a><span data-ttu-id="cf275-107">옵션</span><span class="sxs-lookup"><span data-stu-id="cf275-107">Options</span></span>  
 <span data-ttu-id="cf275-108">**이진 경로**</span><span class="sxs-lookup"><span data-stu-id="cf275-108">**Binary Path**</span></span>  
 <span data-ttu-id="cf275-109">이 서비스에 사용되는 프로그램 파일의 위치를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cf275-109">Lists the location of the program files used by this service.</span></span>  
  
 <span data-ttu-id="cf275-110">**오류 제어**</span><span class="sxs-lookup"><span data-stu-id="cf275-110">**Error Control**</span></span>  
 <span data-ttu-id="cf275-111">1은 `SERVICE_ERROR_NORMAL`을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cf275-111">1 indicates `SERVICE_ERROR_NORMAL`.</span></span> <span data-ttu-id="cf275-112">컴퓨터 시작 중에 서비스를 시작하지 못하면 시작 프로그램은 오류를 기록하고 팝업 메시지 상자를 표시하지만 컴퓨터를 시작하는 작업은 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf275-112">If the service fails to start during computer start up, the startup program logs the error and displays a pop-up message box but continues the startup operation.</span></span> <span data-ttu-id="cf275-113">이 값은 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cf275-113">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="cf275-114">**종료 코드**</span><span class="sxs-lookup"><span data-stu-id="cf275-114">**Exit Code**</span></span>  
 <span data-ttu-id="cf275-115">오류가 발생하면 이 상자에 오류 번호가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="cf275-115">When an error occurs, the error number appears in this box.</span></span> <span data-ttu-id="cf275-116">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 기술 자료에서 이 번호를 검색하여 오류를 해결하거나 기술 지원부에 이 번호를 제공하십시오.</span><span class="sxs-lookup"><span data-stu-id="cf275-116">Use this number to troubleshoot failures by searching for the number in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base or provide the number to your technical support staff.</span></span>  
  
 <span data-ttu-id="cf275-117">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="cf275-117">**Host Name**</span></span>  
 <span data-ttu-id="cf275-118">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스가 실행되는 컴퓨터 또는 클러스터의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cf275-118">Displays the name of the computer or cluster running the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
 <span data-ttu-id="cf275-119">**이름**</span><span class="sxs-lookup"><span data-stu-id="cf275-119">**Name**</span></span>  
 <span data-ttu-id="cf275-120">서비스의 표시 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cf275-120">Indicates the display name of the service.</span></span>  
  
 <span data-ttu-id="cf275-121">**프로세스 ID**</span><span class="sxs-lookup"><span data-stu-id="cf275-121">**Process ID**</span></span>  
 <span data-ttu-id="cf275-122">Windows 프로세스 ID를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cf275-122">Displays the Windows process ID.</span></span>  
  
 <span data-ttu-id="cf275-123">**SQL 서비스 유형**</span><span class="sxs-lookup"><span data-stu-id="cf275-123">**SQL Service Type**</span></span>  
 <span data-ttu-id="cf275-124">호출 프로세스에 제공되는 서비스의 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cf275-124">Displays the type of service provided to calling processes.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cf275-125">에서는 몇 가지 서비스를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="cf275-125">installs several services.</span></span>  
  
 <span data-ttu-id="cf275-126">**시작 모드**</span><span class="sxs-lookup"><span data-stu-id="cf275-126">**Start Mode**</span></span>  
 <span data-ttu-id="cf275-127">이 서비스를 다음 옵션으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cf275-127">Set this service to the following choices:</span></span>  
  
-   <span data-ttu-id="cf275-128">수동: 컴퓨터가 시작될 때 이 서비스가 자동으로 시작되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cf275-128">Manual: This service does not automatically start when the computer starts.</span></span> <span data-ttu-id="cf275-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자나 다른 도구를 사용하여 서비스를 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf275-129">You must start the service using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or some other tool.</span></span>  
  
-   <span data-ttu-id="cf275-130">자동: 컴퓨터가 시작될 때 이 서비스가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf275-130">Automatic: This service attempts to start when this computer starts.</span></span>  
  
-   <span data-ttu-id="cf275-131">사용 안 함: 이 서비스를 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cf275-131">Disabled: This service cannot be started.</span></span>  
  
 <span data-ttu-id="cf275-132">**State**</span><span class="sxs-lookup"><span data-stu-id="cf275-132">**State**</span></span>  
 <span data-ttu-id="cf275-133">이 서비스가 실행 중인지, 중지되었는지 또는 비활성화되었는지 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cf275-133">Indicates whether this service is running, stopped, or disabled.</span></span> <span data-ttu-id="cf275-134">“ **...** ”는 상태 변경이 보류 중임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cf275-134">"**...**" indicates a state change is pending.</span></span>  
  
  
