---
title: 기본 모드 보고서 서버에 연결 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.connectiondialog.F1
helpviewer_keywords:
- report servers [Reporting Services], configuring
ms.assetid: 8b9ea8d3-827c-4011-9e02-be2eac3bb364
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9952b81ab95f002587f8b9b7ef67810822016372
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648781"
---
# <a name="connect-to-a-native-mode-report-server"></a><span data-ttu-id="5eaf1-102">기본 모드 보고서 서버에 연결</span><span class="sxs-lookup"><span data-stu-id="5eaf1-102">Connect to a Native Mode Report Server</span></span>
  <span data-ttu-id="5eaf1-103">이 대화 상자에서는 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상의 로컬 또는 원격 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서 서버 인스턴스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eaf1-103">Use this dialog box to connect to a local or remote [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server instance.</span></span> <span data-ttu-id="5eaf1-104">이 도구를 사용하여 이전 버전의 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서 서버에 연결할 수는 없으며</span><span class="sxs-lookup"><span data-stu-id="5eaf1-104">You cannot use this tool to connect to earlier versions of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report servers.</span></span> <span data-ttu-id="5eaf1-105">한 번에 하나의 인스턴스에만 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eaf1-105">You can only connect to one instance at a time.</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="5eaf1-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]기본 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="5eaf1-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5eaf1-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자는 더 이상 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드를 구성 및 관리하는 데 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5eaf1-107">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager is not used to configure and administer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span> <span data-ttu-id="5eaf1-108">SharePoint 중앙 관리 및 PowerShell 스크립트를 사용하여 SharePoint 모드에서 보고서 서버를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="5eaf1-108">You Use SharePoint Central Administration and PowerShell scripts to configure a report server in SharePoint mode.</span></span> <span data-ttu-id="5eaf1-109">자세한 내용은 [SharePoint 2010용 Reporting Services SharePoint 모드 설치](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5eaf1-109">For more information, see [Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="5eaf1-110">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Configuration Manager (RSConfigTool.exe)는 "highestAvailable" 권한 수준으로 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eaf1-110">The[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager (RSConfigTool.exe) is installed with a privilege level of "highestAvailable".</span></span> <span data-ttu-id="5eaf1-111">이 동작은 의도된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5eaf1-111">This behavior is by design.</span></span> <span data-ttu-id="5eaf1-112">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI API와의 통신이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5eaf1-112">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager requires communication with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI APIs.</span></span> <span data-ttu-id="5eaf1-113">일부 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI 통신에는 더 높은 수준 또는 관리자 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5eaf1-113">Some of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI communication requires a higher level or administrative of privileges.</span></span>  
  
-   <span data-ttu-id="5eaf1-114">로컬 보고서 서버 인스턴스에 연결하려면 기본값을 사용하고 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5eaf1-114">To connect to a local report server instance, use the default values and click **Connect**.</span></span> <span data-ttu-id="5eaf1-115">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자가 로컬 서버 이름을 제공하여 기본 인스턴스를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="5eaf1-115">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager provides the local server name and detects the default instance.</span></span> <span data-ttu-id="5eaf1-116">대부분의 경우 값을 변경할 필요 없이 **연결** 을 클릭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eaf1-116">In most cases, you can click **Connect** without having to change the values.</span></span> <span data-ttu-id="5eaf1-117">인스턴스를 여러 개 설치한 경우 사용할 인스턴스를 선택합니다.,</span><span class="sxs-lookup"><span data-stu-id="5eaf1-117">If you installed more than one instance, you must select the one that you want to use.</span></span>  
  
-   <span data-ttu-id="5eaf1-118">원격 보고서 서버 인스턴스에 연결하려면 서버 이름을 입력하고 **찾기**를 클릭한 다음 인스턴스를 선택하고 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5eaf1-118">To connect to a remote report server instance, type the server name, click **Find**, select the instance, and then click **Connect**.</span></span>  
  
 <span data-ttu-id="5eaf1-119">이 대화 상자를 열려면 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자를 시작하십시오.</span><span class="sxs-lookup"><span data-stu-id="5eaf1-119">To open this dialog box, start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="5eaf1-120">이 대화 상자는 구성 도구를 시작하면 바로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eaf1-120">This dialog box appears immediately when you start the tool.</span></span> <span data-ttu-id="5eaf1-121">자세한 내용은 [Reporting Services 구성 관리자&#40;기본 모드&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5eaf1-121">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="5eaf1-122">옵션</span><span class="sxs-lookup"><span data-stu-id="5eaf1-122">Options</span></span>  
 <span data-ttu-id="5eaf1-123">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="5eaf1-123">**Server Name**</span></span>  
 <span data-ttu-id="5eaf1-124">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 가 설치된 컴퓨터의 네트워크 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5eaf1-124">Enter the network name of the computer on which [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is installed.</span></span> <span data-ttu-id="5eaf1-125">이때 컴퓨터 이름만 입력하고 접두사나 슬래시를 포함시키지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="5eaf1-125">Type just the computer name; do not include a prefix or slashes.</span></span>  
  
 <span data-ttu-id="5eaf1-126">**찾아낼**</span><span class="sxs-lookup"><span data-stu-id="5eaf1-126">**Find**</span></span>  
 <span data-ttu-id="5eaf1-127">**서버 이름**에 지정된 컴퓨터를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5eaf1-127">Find the computer specified in **Server Name**.</span></span>  
  
 <span data-ttu-id="5eaf1-128">**보고서 서버 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="5eaf1-128">**Report Server Instance**</span></span>  
 <span data-ttu-id="5eaf1-129">보고서 서버 인스턴스가 여러 개 설치된 경우 연결할 구성 요소를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5eaf1-129">Select which instance to connect to if multiple report server instances are installed.</span></span> <span data-ttu-id="5eaf1-130">유효한 인스턴스만 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eaf1-130">Only valid instances are available for selection.</span></span> <span data-ttu-id="5eaf1-131">이전 버전의 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 함께 실행하고 있는 경우 이러한 인스턴스는 목록에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5eaf1-131">If you are running older versions of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] side-by-side a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, those instances will not appear in the list.</span></span>  
  
 <span data-ttu-id="5eaf1-132">**연결**</span><span class="sxs-lookup"><span data-stu-id="5eaf1-132">**Connect**</span></span>  
 <span data-ttu-id="5eaf1-133">지정된 서버와 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5eaf1-133">Connect to the server and instance you specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5eaf1-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5eaf1-134">See Also</span></span>  
 [<span data-ttu-id="5eaf1-135">Reporting Services 구성 관리자&#40;기본 모드&#41;</span><span class="sxs-lookup"><span data-stu-id="5eaf1-135">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
