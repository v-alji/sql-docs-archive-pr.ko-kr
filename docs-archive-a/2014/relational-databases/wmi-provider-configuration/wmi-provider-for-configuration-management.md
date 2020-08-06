---
title: 구성 관리용 WMI 공급자 개념 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Configuration Management
- SQL Server WMI Provider
- configuration management [WMI]
- WMI Provider for Configuration Management, about WMI Provider for Configuration Management
ms.assetid: 7e41db24-b915-4eb8-a1d6-e6948ee915b7
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: be0682e7d6de5cb8c3d67a2f300bb89122213652
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648868"
---
# <a name="wmi-provider-for-configuration-management-concepts"></a><span data-ttu-id="dff98-102">구성 관리용 WMI 공급자 개념</span><span class="sxs-lookup"><span data-stu-id="dff98-102">WMI Provider for Configuration Management Concepts</span></span>
  <span data-ttu-id="dff98-103">WMI 공급자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] MMC (Management Console) 및 Configuration Manager에 대 한 Configuration Manager 스냅인과 함께 사용 되는 게시 된 계층입니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="dff98-103">The WMI provider is a published layer that is used with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager snap-in for [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console (MMC) and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="dff98-104">이 계층은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자에서 요청하는 레지스트리 작업을 관리하는 통합 API 호출 상호 작용 방법과 선택한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스에 대한 향상된 제어 및 조작을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dff98-104">It provides a unified way for interfacing with the API calls that manage the registry operations requested by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager and provides enhanced control and manipulation over the selected [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services.</span></span>  
  
 <span data-ttu-id="dff98-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI 공급자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 프로그램에 의해 자동으로 컴파일되는 DLL 및 MOF 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="dff98-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI Provider is a DLL and a MOF file, which are compiled automatically by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span>  
  
 <span data-ttu-id="dff98-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI 공급자에는 다음과 같은 방법으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 제어하는 데 사용되는 개체 클래스 집합이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dff98-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI Provider contains a set of object classes used to control the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services using the following methods:</span></span>  
  
-   <span data-ttu-id="dff98-107">WQL(Windows 쿼리 언어)을 포함할 수 있는 VBScript, [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] 또는 Perl과 같은 스크립트 언어</span><span class="sxs-lookup"><span data-stu-id="dff98-107">A script language such as VBScript, [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)], or Perl, in which Windows Query Language (WQL) can be embedded.</span></span>  
  
-   <span data-ttu-id="dff98-108">SMO 관리 코드 프로그램의 <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> 개체</span><span class="sxs-lookup"><span data-stu-id="dff98-108">The <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> object in an SMO managed code program.</span></span>  
  
-   <span data-ttu-id="dff98-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI 공급자 스냅인이 포함된 MMC</span><span class="sxs-lookup"><span data-stu-id="dff98-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager or MMC with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI provider snap-in.</span></span>  
  
## <a name="using-a-script-language"></a><span data-ttu-id="dff98-110">스크립트 언어 사용</span><span class="sxs-lookup"><span data-stu-id="dff98-110">Using a Script Language</span></span>  
 <span data-ttu-id="dff98-111">스크립트 언어를 사용하면 다음과 같은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dff98-111">The advantages of using a script language include the following:</span></span>  
  
-   <span data-ttu-id="dff98-112">개발 환경이 필요 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dff98-112">A development environment is not required.</span></span>  
  
-   <span data-ttu-id="dff98-113">스크립트 언어를 지원하는 파일을 구하기 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="dff98-113">The files that support the script language are widely available.</span></span>  
  
 <span data-ttu-id="dff98-114">스크립트는 또한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI 공급자 외에 다른 WMI 공급자에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dff98-114">The script can also work with other WMI Providers in addition to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI Provider.</span></span> <span data-ttu-id="dff98-115">도메인 관리자는 스크립트를 사용하여 네트워크의 여러 컴퓨터에서 서비스, 네트워크 설정 및 별칭 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dff98-115">A domain administrator can use a script to set up the services, network settings, and alias settings on multiple computers on a network.</span></span>  
  
 <span data-ttu-id="dff98-116">이 섹션에서는 스크립트에서 구성 관리용 WMI 공급자에 액세스하는 방법을 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dff98-116">This section deals with accessing the WMI Provider for Configuration Management from scripts in further detail.</span></span>  
  
## <a name="using-the-smo-managedcomputer-object"></a><span data-ttu-id="dff98-117">SMO ManagedComputer 개체 사용</span><span class="sxs-lookup"><span data-stu-id="dff98-117">Using the SMO ManagedComputer Object</span></span>  
 <span data-ttu-id="dff98-118"><xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> 개체는 구성 관리용 WMI 공급자에 대한 액세스를 제공하는 관리되는 SMO 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="dff98-118">The <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> object is a managed SMO object that provides access to the WMI Provider for Configuration Management.</span></span> <span data-ttu-id="dff98-119">SMO 프로그램을 사용하면 <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> 개체를 통해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스, 네트워크 설정 및 별칭 설정을 보고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dff98-119">By using an SMO program, the <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> object can be used to view and modify [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services, network settings, and alias settings.</span></span> <span data-ttu-id="dff98-120">자세한 내용은 [WMI 공급자를 사용 하 여 서비스 및 네트워크 설정 관리](../server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dff98-120">For more information, see [Managing Services and Network Settings by Using WMI Provider](../server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md).</span></span>  
  
## <a name="using-the-microsoft-management-console-or-sql-server-configuration-manager"></a><span data-ttu-id="dff98-121">MMC 또는 SQL Server 구성 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="dff98-121">Using the Microsoft Management Console or SQL Server Configuration Manager</span></span>  
 <span data-ttu-id="dff98-122">MMC(Microsoft Management Console)는 스크립팅 언어나 관리 코드 프로그램과는 달리 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 관리하기 위한 인터페이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dff98-122">Microsoft Management Console (MMC) provides an interface to manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services, as opposed to a scripting language or managed code program.</span></span> <span data-ttu-id="dff98-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관리 MMC 스냅인을 사용하여 서비스를 중지 및 시작하고 서비스 계정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dff98-123">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management MMC snap-in can be used to stop and start services, and to change service accounts.</span></span>  
  
 <span data-ttu-id="dff98-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스, 클라이언트 프로토콜, 서버 프로토콜 및 서버 별칭을 관리하는 데도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dff98-124">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager can also be used to manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services, client and server protocols, and server aliases</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dff98-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dff98-125">See Also</span></span>  
 <span data-ttu-id="dff98-126">[구성 관리용 WMI 공급자 이해](understanding-the-wmi-provider-for-configuration-management.md) </span><span class="sxs-lookup"><span data-stu-id="dff98-126">[Understanding the WMI Provider for Configuration Management](understanding-the-wmi-provider-for-configuration-management.md) </span></span>  
 <span data-ttu-id="dff98-127">[구성 관리용 WMI 공급자 작업](working-with-the-wmi-provider-for-configuration-management.md) </span><span class="sxs-lookup"><span data-stu-id="dff98-127">[Working with the WMI Provider for Configuration Management](working-with-the-wmi-provider-for-configuration-management.md) </span></span>  
 [<span data-ttu-id="dff98-128">구성 관리용 WMI 공급자에 WQL 및 스크립트 언어 사용</span><span class="sxs-lookup"><span data-stu-id="dff98-128">Using WQL and Scripting Languages with the WMI Provider for Configuration Management</span></span>](using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  
