---
title: Analysis Server 속성(서비스 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 8dbe4bc5-6aa9-48ee-857e-0b4ea764b9cb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 91200120d87224c8e7733b0ff41ed423d3086c34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741511"
---
# <a name="analysis-server-properties-service-tab"></a><span data-ttu-id="91104-102">분석 서버 속성(서비스 탭)</span><span class="sxs-lookup"><span data-stu-id="91104-102">Analysis Server Properties (Service Tab)</span></span>
  <span data-ttu-id="91104-103">이 서비스는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]입니다.</span><span class="sxs-lookup"><span data-stu-id="91104-103">This service is the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="91104-104">[!INCLUDE[ssAS](../../includes/ssas-md.md)] 가 제대로 작동하려면 이 서비스가 실행되고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91104-104">This service must be running for [!INCLUDE[ssAS](../../includes/ssas-md.md)] to work properly.</span></span> <span data-ttu-id="91104-105">밝은 회색으로 표시된 속성 값은 이 애플리케이션을 사용하여 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="91104-105">The property values in light gray cannot be changed using this application.</span></span>  
  
## <a name="options"></a><span data-ttu-id="91104-106">옵션</span><span class="sxs-lookup"><span data-stu-id="91104-106">Options</span></span>  
 <span data-ttu-id="91104-107">**이진 경로**</span><span class="sxs-lookup"><span data-stu-id="91104-107">**Binary Path**</span></span>  
 <span data-ttu-id="91104-108">이 서비스에 사용되는 프로그램 파일의 위치를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="91104-108">Displays the location of the program files used by this service.</span></span>  
  
 <span data-ttu-id="91104-109">**오류 제어**</span><span class="sxs-lookup"><span data-stu-id="91104-109">**Error Control**</span></span>  
 <span data-ttu-id="91104-110">1은 `SERVICE_ERROR_NORMAL`을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="91104-110">1 indicates `SERVICE_ERROR_NORMAL`.</span></span> <span data-ttu-id="91104-111">컴퓨터 시작 중에 서비스를 시작하지 못하면 시작 프로그램은 오류를 기록하고 팝업 메시지 상자를 표시하지만 컴퓨터를 시작하는 작업은 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="91104-111">If the service fails to start during computer start up, the startup program logs the error and displays a pop-up message box but continues the startup operation.</span></span> <span data-ttu-id="91104-112">이 값은 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="91104-112">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="91104-113">**종료 코드**</span><span class="sxs-lookup"><span data-stu-id="91104-113">**Exit Code**</span></span>  
 <span data-ttu-id="91104-114">오류가 발생하면 이 상자에 오류 번호가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="91104-114">When an error occurs, the error number appears in this box.</span></span> <span data-ttu-id="91104-115">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 기술 자료에서 이 번호를 검색하여 오류를 해결하거나 기술 지원부에 이 번호를 제공하십시오.</span><span class="sxs-lookup"><span data-stu-id="91104-115">Use this number to troubleshoot failures by searching for the number in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base or provide the number to your technical support staff.</span></span>  
  
 <span data-ttu-id="91104-116">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="91104-116">**Host Name**</span></span>  
 <span data-ttu-id="91104-117">[!INCLUDE[ssAS](../../includes/ssas-md.md)]가 실행되는 컴퓨터 또는 클러스터의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="91104-117">Displays the name of the computer or cluster running [!INCLUDE[ssAS](../../includes/ssas-md.md)].</span></span>  
  
 <span data-ttu-id="91104-118">**이름**</span><span class="sxs-lookup"><span data-stu-id="91104-118">**Name**</span></span>  
 <span data-ttu-id="91104-119">서비스의 표시 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="91104-119">Indicates the display name of the service.</span></span>  
  
 <span data-ttu-id="91104-120">**프로세스 ID**</span><span class="sxs-lookup"><span data-stu-id="91104-120">**Process ID**</span></span>  
 <span data-ttu-id="91104-121">이 프로그램의 프로세스를 추적하기 위해 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows에서 사용하는 번호를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="91104-121">Displays the number used by [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows to keep track of this program's processes.</span></span>  
  
 <span data-ttu-id="91104-122">**SQL 서비스 유형**</span><span class="sxs-lookup"><span data-stu-id="91104-122">**SQL Service Type**</span></span>  
 <span data-ttu-id="91104-123">호출 프로세스에 제공되는 서비스의 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="91104-123">Displays the type of service provided to calling processes.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="91104-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 몇 가지 서비스를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="91104-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installs several services.</span></span>  
  
 <span data-ttu-id="91104-125">**시작 모드**</span><span class="sxs-lookup"><span data-stu-id="91104-125">**Start Mode**</span></span>  
 <span data-ttu-id="91104-126">이 서비스를 다음 옵션으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="91104-126">Set this service to the following choices:</span></span>  
  
-   <span data-ttu-id="91104-127">수동: 컴퓨터가 시작될 때 이 서비스가 자동으로 시작되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="91104-127">Manual: This service does not automatically start when the computer starts.</span></span> <span data-ttu-id="91104-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자나 다른 도구를 사용하여 서비스를 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91104-128">You must start the service using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or some other tool.</span></span>  
  
-   <span data-ttu-id="91104-129">자동: 컴퓨터가 시작될 때 이 서비스가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="91104-129">Automatic: This service attempts to start when this computer starts.</span></span>  
  
-   <span data-ttu-id="91104-130">사용 안 함: 이 서비스를 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="91104-130">Disabled: This service cannot be started.</span></span>  
  
 <span data-ttu-id="91104-131">**State**</span><span class="sxs-lookup"><span data-stu-id="91104-131">**State**</span></span>  
 <span data-ttu-id="91104-132">이 서비스가 실행 중인지, 중지되었는지 또는 비활성화되었는지 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="91104-132">Indicates whether this service is running, stopped, or disabled.</span></span>  
  
  
