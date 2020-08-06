---
title: SQL Server Browser 속성(서비스 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 98ace9b0-72d5-4b72-9b7b-11fbc490981a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 200e45648b94e26c5e808e9a817cfe01866e6a65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646792"
---
# <a name="sql-server-browser-properties-service-tab"></a><span data-ttu-id="26042-102">SQL Server Browser 속성(서비스 탭)</span><span class="sxs-lookup"><span data-stu-id="26042-102">SQL Server Browser Properties (Service Tab)</span></span>
  <span data-ttu-id="26042-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 프로그램은 서버에서 서비스로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="26042-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser program runs as a service on the server.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="26042-104">Browser는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 리소스에 대해 들어오는 요청을 수신 대기하고 컴퓨터에 설치된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="26042-104">Browser listens for incoming requests for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources and provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances installed on the computer.</span></span>  
  
 <span data-ttu-id="26042-105">**SQL Server Browser 속성** 대화 상자의 **서비스** 탭을 사용하여 다음 옵션을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26042-105">Use the **Service** tab on the **SQL Server Browser Properties** dialog box to view the following options.</span></span> <span data-ttu-id="26042-106">**시작 모드** 를 제외한 모든 속성은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="26042-106">All properties except **Start Mode** are read-only.</span></span>  
  
## <a name="options"></a><span data-ttu-id="26042-107">옵션</span><span class="sxs-lookup"><span data-stu-id="26042-107">Options</span></span>  
 <span data-ttu-id="26042-108">**이진 경로**</span><span class="sxs-lookup"><span data-stu-id="26042-108">**Binary Path**</span></span>  
 <span data-ttu-id="26042-109">이 서비스에 사용되는 프로그램 파일의 위치를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="26042-109">Displays the location of the program files used by this service.</span></span>  
  
 <span data-ttu-id="26042-110">**오류 제어**</span><span class="sxs-lookup"><span data-stu-id="26042-110">**Error Control**</span></span>  
 <span data-ttu-id="26042-111">1은 `SERVICE_ERROR_NORMAL`을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="26042-111">1 indicates `SERVICE_ERROR_NORMAL`.</span></span> <span data-ttu-id="26042-112">컴퓨터 시작 중에 서비스를 시작하지 못하면 시작 프로그램은 오류를 기록하고 팝업 메시지 상자를 표시하지만 컴퓨터를 시작하는 작업은 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="26042-112">If the service fails to start during computer start up, the startup program logs the error and displays a pop-up message box but continues the startup operation.</span></span> <span data-ttu-id="26042-113">이 값은 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="26042-113">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="26042-114">**종료 코드**</span><span class="sxs-lookup"><span data-stu-id="26042-114">**Exit Code**</span></span>  
 <span data-ttu-id="26042-115">오류가 발생하면 이 상자에 오류 번호가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="26042-115">When an error occurs, the error number appears in this box.</span></span> <span data-ttu-id="26042-116">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 기술 자료에서 이 번호를 검색하여 오류를 해결하거나 기술 지원부에 이 번호를 제공하십시오.</span><span class="sxs-lookup"><span data-stu-id="26042-116">Use this number to troubleshoot failures by searching for the number in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base or provide the number to your technical support staff.</span></span>  
  
 <span data-ttu-id="26042-117">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="26042-117">**Host Name**</span></span>  
 <span data-ttu-id="26042-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 서비스가 실행되는 컴퓨터 또는 클러스터의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="26042-118">Displays the name of the computer or cluster running the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span>  
  
 <span data-ttu-id="26042-119">**이름**</span><span class="sxs-lookup"><span data-stu-id="26042-119">**Name**</span></span>  
 <span data-ttu-id="26042-120">서비스의 표시 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="26042-120">Indicates the display name of the service.</span></span>  
  
 <span data-ttu-id="26042-121">**프로세스 ID**</span><span class="sxs-lookup"><span data-stu-id="26042-121">**Process ID**</span></span>  
 <span data-ttu-id="26042-122">Windows 프로세스 ID를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="26042-122">Displays the Windows process ID.</span></span>  
  
 <span data-ttu-id="26042-123">**서비스 유형**</span><span class="sxs-lookup"><span data-stu-id="26042-123">**Service Type**</span></span>  
 <span data-ttu-id="26042-124">호출 프로세스에 제공되는 서비스의 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="26042-124">Displays the type of service provided to calling processes.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="26042-125">에서는 몇 가지 서비스를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="26042-125">installs several services.</span></span>  
  
 <span data-ttu-id="26042-126">**시작 모드**</span><span class="sxs-lookup"><span data-stu-id="26042-126">**Start Mode**</span></span>  
 <span data-ttu-id="26042-127">이 서비스를 다음 옵션으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="26042-127">Set this service to the following choices:</span></span>  
  
-   <span data-ttu-id="26042-128">수동: 컴퓨터가 시작될 때 이 서비스가 자동으로 시작되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="26042-128">Manual: This service does not automatically start when the computer starts.</span></span> <span data-ttu-id="26042-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자나 다른 도구를 사용하여 서비스를 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26042-129">You must start the service using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or some other tool.</span></span>  
  
-   <span data-ttu-id="26042-130">자동: 컴퓨터가 시작될 때 이 서비스가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="26042-130">Automatic: This service attempts to start when this computer starts.</span></span>  
  
-   <span data-ttu-id="26042-131">사용 안 함: 이 서비스를 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="26042-131">Disabled: This service cannot be started.</span></span>  
  
 <span data-ttu-id="26042-132">**State**</span><span class="sxs-lookup"><span data-stu-id="26042-132">**State**</span></span>  
 <span data-ttu-id="26042-133">이 서비스가 실행 중인지, 중지되었는지 또는 비활성화되었는지 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="26042-133">Indicates whether this service is running, stopped, or disabled.</span></span> <span data-ttu-id="26042-134">“ **...** ”는 상태 변경이 보류 중임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="26042-134">"**...**" indicates a state change is pending.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26042-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="26042-135">See Also</span></span>  
 [<span data-ttu-id="26042-136">SQL Server Browser 서비스</span><span class="sxs-lookup"><span data-stu-id="26042-136">SQL Server Browser Service</span></span>](../../../2014/tools/configuration-manager/sql-server-browser-service.md)  
  
  
