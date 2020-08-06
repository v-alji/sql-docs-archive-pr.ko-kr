---
title: SQL Server 속성(서비스 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: e4ae0c6b-6fd8-4325-b54e-1758fc659958
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5822a02d5631e0d0e9318b20a1dcee87b8a4ded1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740630"
---
# <a name="sql-server-properties-service-tab"></a><span data-ttu-id="1ab57-102">SQL Server 속성(서비스 탭)</span><span class="sxs-lookup"><span data-stu-id="1ab57-102">SQL Server Properties (Service Tab)</span></span>
  <span data-ttu-id="1ab57-103">**MSSQLSERVER 속성**대화 상자의 **서비스** 탭을 사용하여 다음 옵션을 확인하거나 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ab57-103">Use the **Service**tab on the **MSSQLSERVER Properties** dialog box to view or specify the following options.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1ab57-104">옵션</span><span class="sxs-lookup"><span data-stu-id="1ab57-104">Options</span></span>  
 <span data-ttu-id="1ab57-105">**이진 경로**</span><span class="sxs-lookup"><span data-stu-id="1ab57-105">**Binary Path**</span></span>  
 <span data-ttu-id="1ab57-106">이 서비스에 사용되는 프로그램 파일의 위치를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1ab57-106">Lists the location of the program files used by this service.</span></span>  
  
 <span data-ttu-id="1ab57-107">**오류 제어**</span><span class="sxs-lookup"><span data-stu-id="1ab57-107">**Error Control**</span></span>  
 <span data-ttu-id="1ab57-108">1은 `SERVICE_ERROR_NORMAL`을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1ab57-108">1 indicates `SERVICE_ERROR_NORMAL`.</span></span> <span data-ttu-id="1ab57-109">컴퓨터 시작 중에 서비스를 시작하지 못하면 시작 프로그램은 오류를 기록하고 팝업 메시지 상자를 표시하지만 컴퓨터를 시작하는 작업은 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ab57-109">If the service fails to start during computer start up, the startup program logs the error and displays a pop-up message box but continues the startup operation.</span></span> <span data-ttu-id="1ab57-110">이 값은 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1ab57-110">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="1ab57-111">**종료 코드**</span><span class="sxs-lookup"><span data-stu-id="1ab57-111">**Exit Code**</span></span>  
 <span data-ttu-id="1ab57-112">오류가 발생하면 이 상자에 오류 번호가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1ab57-112">When an error occurs, the error number appears in this box.</span></span> <span data-ttu-id="1ab57-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 기술 자료에서 이 번호를 검색하여 오류를 해결하거나 기술 지원부에 이 번호를 제공하십시오.</span><span class="sxs-lookup"><span data-stu-id="1ab57-113">Use this number to troubleshoot failures by searching for the number in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base or provide the number to your technical support staff.</span></span>  
  
 <span data-ttu-id="1ab57-114">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="1ab57-114">**Host Name**</span></span>  
 <span data-ttu-id="1ab57-115">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스가 실행되는 컴퓨터 또는 클러스터의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1ab57-115">Displays the name of the computer or cluster running the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
 <span data-ttu-id="1ab57-116">**이름**</span><span class="sxs-lookup"><span data-stu-id="1ab57-116">**Name**</span></span>  
 <span data-ttu-id="1ab57-117">서비스의 표시 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1ab57-117">Indicates the display name of the service.</span></span>  
  
 <span data-ttu-id="1ab57-118">**프로세스 ID**</span><span class="sxs-lookup"><span data-stu-id="1ab57-118">**Process ID**</span></span>  
 <span data-ttu-id="1ab57-119">Windows 프로세스 ID를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1ab57-119">Displays the Windows process ID.</span></span>  
  
 <span data-ttu-id="1ab57-120">**서비스 유형**</span><span class="sxs-lookup"><span data-stu-id="1ab57-120">**Service Type**</span></span>  
 <span data-ttu-id="1ab57-121">호출 프로세스에 제공되는 서비스의 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1ab57-121">Displays the type of service provided to calling processes.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1ab57-122">에서는 몇 가지 서비스를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="1ab57-122">installs several services.</span></span>  
  
 <span data-ttu-id="1ab57-123">**시작 모드**</span><span class="sxs-lookup"><span data-stu-id="1ab57-123">**Start Mode**</span></span>  
 <span data-ttu-id="1ab57-124">이 서비스를 다음 옵션으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1ab57-124">Set this service to the following choices:</span></span>  
  
-   <span data-ttu-id="1ab57-125">수동: 컴퓨터가 시작될 때 이 서비스가 자동으로 시작되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1ab57-125">Manual: This service does not automatically start when the computer starts.</span></span> <span data-ttu-id="1ab57-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자나 다른 도구를 사용하여 서비스를 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ab57-126">You must start the service using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or some other tool.</span></span>  
  
-   <span data-ttu-id="1ab57-127">자동: 컴퓨터가 시작될 때 이 서비스가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ab57-127">Automatic: This service attempts to start when this computer starts.</span></span>  
  
-   <span data-ttu-id="1ab57-128">사용 안 함: 이 서비스를 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1ab57-128">Disabled: This service cannot be started.</span></span>  
  
 <span data-ttu-id="1ab57-129">**State**</span><span class="sxs-lookup"><span data-stu-id="1ab57-129">**State**</span></span>  
 <span data-ttu-id="1ab57-130">이 서비스가 실행 중인지, 중지되었는지 또는 비활성화되었는지 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1ab57-130">Indicates whether this service is running, stopped, or disabled.</span></span> <span data-ttu-id="1ab57-131">“ **...** ”는 상태 변경이 보류 중임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1ab57-131">"**...**" indicates a state change is pending.</span></span>  
  
  
