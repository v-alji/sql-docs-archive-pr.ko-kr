---
title: SQL Server 에이전트 속성(서비스 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 452857fb-be1b-4e1e-851c-dd2216640f35
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8d3526026a45af6375f5c881616c476d80737795
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734828"
---
# <a name="sql-server-agent-properties-service-tab"></a><span data-ttu-id="0954b-102">SQL Server 에이전트 속성(서비스 탭)</span><span class="sxs-lookup"><span data-stu-id="0954b-102">SQL Server Agent Properties (Service Tab)</span></span>
  <span data-ttu-id="0954b-103">이 서비스는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="0954b-103">This service is the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span> <span data-ttu-id="0954b-104">밝은 회색으로 표시된 속성 값은 이 애플리케이션을 사용하여 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0954b-104">The property values in light gray cannot be changed using this application.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0954b-105">옵션</span><span class="sxs-lookup"><span data-stu-id="0954b-105">Options</span></span>  
 <span data-ttu-id="0954b-106">**이진 경로**</span><span class="sxs-lookup"><span data-stu-id="0954b-106">**Binary Path**</span></span>  
 <span data-ttu-id="0954b-107">이 서비스에 사용되는 프로그램 파일의 위치를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0954b-107">Displays the location of the program files used by this service.</span></span>  
  
 <span data-ttu-id="0954b-108">**오류 제어**</span><span class="sxs-lookup"><span data-stu-id="0954b-108">**Error Control**</span></span>  
 <span data-ttu-id="0954b-109">1은 `SERVICE_ERROR_NORMAL`을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0954b-109">1 indicates `SERVICE_ERROR_NORMAL`.</span></span> <span data-ttu-id="0954b-110">컴퓨터 시작 중에 서비스를 시작하지 못하면 시작 프로그램은 오류를 기록하고 팝업 메시지 상자를 표시하지만 컴퓨터를 시작하는 작업은 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="0954b-110">If the service fails to start during computer start up, the startup program logs the error and displays a pop-up message box but continues the startup operation.</span></span> <span data-ttu-id="0954b-111">이 값은 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0954b-111">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="0954b-112">**종료 코드**</span><span class="sxs-lookup"><span data-stu-id="0954b-112">**Exit Code**</span></span>  
 <span data-ttu-id="0954b-113">오류가 발생하면 이 상자에 오류 번호가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0954b-113">When an error occurs, the error number appears in this box.</span></span> <span data-ttu-id="0954b-114">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 기술 자료에서 이 번호를 검색하여 오류를 해결하거나 기술 지원부에 이 번호를 제공하십시오.</span><span class="sxs-lookup"><span data-stu-id="0954b-114">Use this number to troubleshoot failures by searching for the number in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base or provide the number to your technical support staff.</span></span>  
  
 <span data-ttu-id="0954b-115">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="0954b-115">**Host Name**</span></span>  
 <span data-ttu-id="0954b-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 실행되는 컴퓨터 또는 클러스터의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0954b-116">Displays the name of the computer or cluster running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
 <span data-ttu-id="0954b-117">**이름**</span><span class="sxs-lookup"><span data-stu-id="0954b-117">**Name**</span></span>  
 <span data-ttu-id="0954b-118">서비스의 표시 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0954b-118">Indicates the display name of the service.</span></span>  
  
 <span data-ttu-id="0954b-119">**프로세스 ID**</span><span class="sxs-lookup"><span data-stu-id="0954b-119">**Process ID**</span></span>  
 <span data-ttu-id="0954b-120">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 프로세스 ID를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0954b-120">Displays the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows process ID.</span></span>  
  
 <span data-ttu-id="0954b-121">**SQL 서비스 유형**</span><span class="sxs-lookup"><span data-stu-id="0954b-121">**SQL Service Type**</span></span>  
 <span data-ttu-id="0954b-122">호출 프로세스에 제공되는 서비스의 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0954b-122">Displays the type of service provided to calling processes.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0954b-123">에서는 몇 가지 서비스를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="0954b-123">installs several services.</span></span>  
  
 <span data-ttu-id="0954b-124">**시작 모드**</span><span class="sxs-lookup"><span data-stu-id="0954b-124">**Start Mode**</span></span>  
 <span data-ttu-id="0954b-125">이 서비스를 다음 옵션으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0954b-125">Set this service to the following choices:</span></span>  
  
-   <span data-ttu-id="0954b-126">수동: 컴퓨터가 시작될 때 이 서비스가 자동으로 시작되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0954b-126">Manual: This service does not automatically start when the computer starts.</span></span> <span data-ttu-id="0954b-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자나 다른 도구를 사용하여 서비스를 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0954b-127">You must start the service using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or some other tool.</span></span>  
  
-   <span data-ttu-id="0954b-128">자동: 컴퓨터가 시작될 때 이 서비스가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="0954b-128">Automatic: This service attempts to start when this computer starts.</span></span>  
  
-   <span data-ttu-id="0954b-129">사용 안 함: 이 서비스를 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0954b-129">Disabled: This service cannot be started.</span></span>  
  
 <span data-ttu-id="0954b-130">**State**</span><span class="sxs-lookup"><span data-stu-id="0954b-130">**State**</span></span>  
 <span data-ttu-id="0954b-131">이 서비스가 실행 중인지, 중지되었는지 또는 비활성화되었는지 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0954b-131">Indicates whether this service is running, stopped, or disabled.</span></span> <span data-ttu-id="0954b-132">“ **...** ”는 상태 변경이 보류 중임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0954b-132">"**...**" indicates a state change is pending.</span></span>  
  
  
