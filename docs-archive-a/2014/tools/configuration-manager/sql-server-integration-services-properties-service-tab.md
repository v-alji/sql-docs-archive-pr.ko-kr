---
title: SQL Server Integration Services 속성(서비스 탭) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 37f0acd9-c96f-48fd-9b53-2ca0097af242
author: stevestein
ms.author: sstein
ms.openlocfilehash: a752bdeab3c99ac97445e3281d3165a2d8f79866
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660223"
---
# <a name="sql-server-integration-services-properties-service-tab"></a><span data-ttu-id="64655-102">SQL Server Integration Services 속성(서비스 탭)</span><span class="sxs-lookup"><span data-stu-id="64655-102">SQL Server Integration Services Properties (Service Tab)</span></span>
  <span data-ttu-id="64655-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] **속성** 대화 상자의 **서비스** 탭을 사용하여 다음 옵션을 확인하거나 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64655-103">Use the **Service**tab on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] **Properties** dialog box to view or specify the following options.</span></span>  
  
## <a name="options"></a><span data-ttu-id="64655-104">옵션</span><span class="sxs-lookup"><span data-stu-id="64655-104">Options</span></span>  
 <span data-ttu-id="64655-105">**이진 경로**</span><span class="sxs-lookup"><span data-stu-id="64655-105">**Binary Path**</span></span>  
 <span data-ttu-id="64655-106">이 서비스에 사용되는 프로그램 파일의 위치를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="64655-106">Displays the location of the program files used by this service.</span></span>  
  
 <span data-ttu-id="64655-107">**오류 제어**</span><span class="sxs-lookup"><span data-stu-id="64655-107">**Error Control**</span></span>  
 <span data-ttu-id="64655-108">1은 `SERVICE_ERROR_NORMAL`을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="64655-108">1 indicates `SERVICE_ERROR_NORMAL`.</span></span> <span data-ttu-id="64655-109">컴퓨터 시작 중에 서비스를 시작하지 못하면 시작 프로그램은 오류를 기록하고 팝업 메시지 상자를 표시하지만 컴퓨터를 시작하는 작업은 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="64655-109">If the service fails to start during computer start up, the startup program logs the error and displays a pop-up message box but continues the startup operation.</span></span> <span data-ttu-id="64655-110">이 값은 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="64655-110">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="64655-111">**종료 코드**</span><span class="sxs-lookup"><span data-stu-id="64655-111">**Exit Code**</span></span>  
 <span data-ttu-id="64655-112">서비스를 시작하거나 종료할 때 발생하는 모든 문제를 정의하는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="64655-112">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows error code defining any problems encountered in starting or stopping the service.</span></span> <span data-ttu-id="64655-113">오류가 이 클래스가 나타내는 서비스에 고유한 것이고 **ServiceSpecificExitCode** 속성에서 오류 정보를 사용할 수 있으면 이 속성은 **ERROR_SERVICE_SPECIFIC_ERROR** (1066)로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="64655-113">This property is set to **ERROR_SERVICE_SPECIFIC_ERROR** (1066) when the error is unique to the service represented by this class, and information about the error is available in the **ServiceSpecificExitCode** property.</span></span> <span data-ttu-id="64655-114">서비스는 실행 중일 때와 정상 종료 시 다시 이 값을 NO_ERROR(0)로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="64655-114">The service sets this value to NO_ERROR (0) when running, and again upon normal termination.</span></span>  
  
 <span data-ttu-id="64655-115">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="64655-115">**Host Name**</span></span>  
 <span data-ttu-id="64655-116">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 서비스가 실행되는 컴퓨터 또는 클러스터의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="64655-116">Displays the name of the computer or cluster running the [!INCLUDE[ssIS](../../includes/ssis-md.md)] service.</span></span>  
  
 <span data-ttu-id="64655-117">**이름**</span><span class="sxs-lookup"><span data-stu-id="64655-117">**Name**</span></span>  
 <span data-ttu-id="64655-118">서비스의 표시 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="64655-118">Indicates the display name of the service.</span></span>  
  
 <span data-ttu-id="64655-119">**프로세스 ID**</span><span class="sxs-lookup"><span data-stu-id="64655-119">**Process ID**</span></span>  
 <span data-ttu-id="64655-120">Windows 프로세스 ID를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="64655-120">Displays the Windows process ID.</span></span>  
  
 <span data-ttu-id="64655-121">**SQL 서비스 유형**</span><span class="sxs-lookup"><span data-stu-id="64655-121">**SQL Service Type**</span></span>  
 <span data-ttu-id="64655-122">호출 프로세스에 제공되는 서비스의 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="64655-122">Displays the type of service provided to calling processes.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="64655-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 몇 가지 서비스를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="64655-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installs several services.</span></span>  
  
 <span data-ttu-id="64655-124">**시작 모드**</span><span class="sxs-lookup"><span data-stu-id="64655-124">**Start Mode**</span></span>  
 <span data-ttu-id="64655-125">이 서비스를 다음 옵션으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="64655-125">Set this service to the following choices:</span></span>  
  
-   <span data-ttu-id="64655-126">수동: 이 서비스는 컴퓨터가 시작될 때 자동으로 시작되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="64655-126">Manual: This service does not automatically start when the computer starts.</span></span> <span data-ttu-id="64655-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자나 다른 도구를 사용하여 서비스를 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64655-127">You must start the service using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or some other tool.</span></span>  
  
-   <span data-ttu-id="64655-128">자동: 이 서비스는 컴퓨터가 시작될 때 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="64655-128">Automatic: This service attempts to start when this computer starts.</span></span>  
  
-   <span data-ttu-id="64655-129">사용 안 함: 이 서비스를 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="64655-129">Disabled: This service cannot be started.</span></span>  
  
 <span data-ttu-id="64655-130">**State**</span><span class="sxs-lookup"><span data-stu-id="64655-130">**State**</span></span>  
 <span data-ttu-id="64655-131">이 서비스가 실행 중인지, 중지되었는지 또는 비활성화되었는지 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="64655-131">Indicates whether this service is running, stopped, or disabled.</span></span> <span data-ttu-id="64655-132">“ **...** ”는 상태 변경이 보류 중임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="64655-132">"**...**" indicates a state change is pending.</span></span>  
  
  
