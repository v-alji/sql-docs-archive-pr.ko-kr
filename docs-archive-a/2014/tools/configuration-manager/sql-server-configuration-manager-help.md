---
title: SQL Server 구성 관리자 도움말 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Configuration Manager, help
ms.assetid: 6e909911-39a6-469b-b22a-3afdfd08a30b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 10a6d6052fe109892f975774a1ed65b818ef0581
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737300"
---
# <a name="sql-server-configuration-manager-help"></a><span data-ttu-id="6725a-102">SQL Server 구성 관리자 도움말</span><span class="sxs-lookup"><span data-stu-id="6725a-102">SQL Server Configuration Manager Help</span></span>
  <span data-ttu-id="6725a-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스와 네트워크 연결을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6725a-103">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services and configure network connectivity.</span></span> <span data-ttu-id="6725a-104">[!INCLUDE[tsql](../../includes/tsql-md.md)] 를 사용하면 데이터베이스 개체를 만들거나 관리하고, 보안을 구성하고, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6725a-104">To create or manage database objects, configure security, and write [!INCLUDE[tsql](../../includes/tsql-md.md)] queries, use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="6725a-105">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6725a-105">For more information about [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="6725a-106">이 섹션에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자의 대화 상자에 대한 F1 도움말 항목을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6725a-106">This section contains the F1 Help topics for the dialogs in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="6725a-107">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자로 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6725a-107">Configuration Manager cannot configure versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] earlier than [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
## <a name="services"></a><span data-ttu-id="6725a-108">Services</span><span class="sxs-lookup"><span data-stu-id="6725a-108">Services</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6725a-109">구성 관리자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 관련된 서비스를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="6725a-109">Configuration Manager manages services that are related to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6725a-110">이러한 태스크의 대부분은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 서비스 대화 상자를 사용하여 수행할 수도 있지만 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자는 자신이 관리하는 서비스에 대해 서비스 계정 변경 시 올바른 권한을 적용하는 등 Windows 서비스 대화 상자에서는 지원하지 않는 작업을 추가로 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6725a-110">Although many of these tasks can be accomplished using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Services dialog, is important to note that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager performs additional operations on the services it manages, such as applying the correct permissions when the service account is changed.</span></span> <span data-ttu-id="6725a-111">일반 Windows 서비스 대화 상자를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 구성할 경우 서비스가 작동하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6725a-111">Using the normal Windows Services dialog to configure any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services might cause the service to malfunction.</span></span>  
  
 <span data-ttu-id="6725a-112">다음 태스크에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6725a-112">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager for the following tasks for services:</span></span>  
  
-   <span data-ttu-id="6725a-113">서비스 시작, 중지 및 일시 중지</span><span class="sxs-lookup"><span data-stu-id="6725a-113">Start, stop, and pause services</span></span>  
  
-   <span data-ttu-id="6725a-114">자동 또는 수동으로 시작하도록 서비스 구성, 서비스 비활성화 또는 기타 서비스 설정 변경</span><span class="sxs-lookup"><span data-stu-id="6725a-114">Configure services to start automatically or manually, disable the services, or change other service settings</span></span>  
  
-   <span data-ttu-id="6725a-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스에 사용되는 계정의 암호 변경</span><span class="sxs-lookup"><span data-stu-id="6725a-115">Change the passwords for the accounts used by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services</span></span>  
  
-   <span data-ttu-id="6725a-116">추적 플래그(명령줄 매개 변수)를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시작</span><span class="sxs-lookup"><span data-stu-id="6725a-116">Start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using trace flags (command line parameters)</span></span>  
  
-   <span data-ttu-id="6725a-117">서비스 속성 보기</span><span class="sxs-lookup"><span data-stu-id="6725a-117">View the properties of services</span></span>  
  
## <a name="sql-server-network-configuration"></a><span data-ttu-id="6725a-118">SQL Server 네트워크 구성</span><span class="sxs-lookup"><span data-stu-id="6725a-118">SQL Server Network Configuration</span></span>  
 <span data-ttu-id="6725a-119">이 컴퓨터의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스와 관련된 다음 태스크에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="6725a-119">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager for the following tasks related to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services on this computer:</span></span>  
  
-   <span data-ttu-id="6725a-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 네트워크 프로토콜 사용 또는 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="6725a-120">Enable or disable a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] network protocol</span></span>  
  
-   <span data-ttu-id="6725a-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 네트워크 프로토콜 구성</span><span class="sxs-lookup"><span data-stu-id="6725a-121">Configure a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] network protocol</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6725a-122">프로토콜을 구성하고 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]에 연결하는 방법에 대한 간략한 자습서는 [자습서: 데이터베이스 엔진 시작](../../relational-databases/tutorial-getting-started-with-the-database-engine.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6725a-122">For a short tutorial about how to configure protocols and connect to the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], see [Tutorial: Getting Started with the Database Engine](../../relational-databases/tutorial-getting-started-with-the-database-engine.md).</span></span>  
  
## <a name="sql-server-native-client-configuration"></a><span data-ttu-id="6725a-123">SQL Server Native Client 구성</span><span class="sxs-lookup"><span data-stu-id="6725a-123">SQL Server Native Client Configuration</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6725a-124">클라이언트는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 네트워크 라이브러리를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6725a-124">clients connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client network library.</span></span> <span data-ttu-id="6725a-125">이 컴퓨터의 클라이언트 애플리케이션과 관련된 다음 태스크에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="6725a-125">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager for the following tasks related to client applications on this computer:</span></span>  
  
-   <span data-ttu-id="6725a-126">이 컴퓨터의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 클라이언트 애플리케이션의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결할 때 프로토콜 순서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6725a-126">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client applications on this computer, specify the protocol order, when connecting to instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="6725a-127">클라이언트 연결 프로토콜을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6725a-127">Configure client connection protocols.</span></span>  
  
-   <span data-ttu-id="6725a-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 클라이언트 애플리케이션의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 대한 별칭을 만들어 클라이언트가 사용자 지정 연결 문자열을 사용하여 연결할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="6725a-128">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client applications, create aliases for instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], so that clients can connect using a custom connection string.</span></span>  
  
 <span data-ttu-id="6725a-129">각 태스크에 대한 자세한 내용은 F1 도움말을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6725a-129">For more information about each of these tasks, see F1 help for each task.</span></span>  
  
#### <a name="to-open-sql-server-configuration-manager"></a><span data-ttu-id="6725a-130">SQL Server 구성 관리자를 열려면</span><span class="sxs-lookup"><span data-stu-id="6725a-130">To open SQL Server Configuration Manager</span></span>  
  
-   <span data-ttu-id="6725a-131">**시작** 메뉴에서 **모든 프로그램**, **Microsoft SQL Server** (버전), **구성 도구**를 차례로 가리킨 다음 **SQL Server 구성 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6725a-131">On the **Start** menu, point to **All Programs**, point to **Microsoft SQL Server** (version), point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6725a-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6725a-132">See Also</span></span>  
 <span data-ttu-id="6725a-133">[SQL Server 서비스](../../../2014/tools/configuration-manager/sql-server-services.md) </span><span class="sxs-lookup"><span data-stu-id="6725a-133">[SQL Server Services](../../../2014/tools/configuration-manager/sql-server-services.md) </span></span>  
 <span data-ttu-id="6725a-134">[네트워크 구성 SQL Server](sql-server-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="6725a-134">[SQL Server Network Configuration](sql-server-network-configuration.md) </span></span>  
 <span data-ttu-id="6725a-135">[SQL Native Client 11.0 구성](../../../2014/tools/configuration-manager/sql-native-client-11-0-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="6725a-135">[SQL Native Client 11.0 Configuration](../../../2014/tools/configuration-manager/sql-native-client-11-0-configuration.md) </span></span>  
 [<span data-ttu-id="6725a-136">네트워크 프로토콜 선택</span><span class="sxs-lookup"><span data-stu-id="6725a-136">Choosing a Network Protocol</span></span>](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
