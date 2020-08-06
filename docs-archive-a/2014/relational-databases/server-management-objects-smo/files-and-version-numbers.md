---
title: 파일 및 버전 번호 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, versions
- components [SMO]
- files [SMO], components
- SMO [SQL Server], versions
- versions [SMO]
ms.assetid: 510907b6-e7a9-41bd-b892-d6d99a5118e1
author: stevestein
ms.author: sstein
ms.openlocfilehash: f1a7286f15af28f97e488b8b40fd745a0d320108
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650907"
---
# <a name="files-and-version-numbers"></a><span data-ttu-id="b40d6-102">파일 및 버전 번호</span><span class="sxs-lookup"><span data-stu-id="b40d6-102">Files and Version Numbers</span></span>
  <span data-ttu-id="b40d6-103">필요한 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SMO (Management Objects) 구성 요소는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 클라이언트 또는 서버 인스턴스의 일부로 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b40d6-103">All required [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO) components are installed as part of an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client or server.</span></span> <span data-ttu-id="b40d6-104">SMO는 몇 개의 관리되는 어셈블리에 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="b40d6-104">SMO is implemented in several managed assemblies.</span></span> <span data-ttu-id="b40d6-105">클라이언트나 서버에서 SMO 애플리케이션을 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b40d6-105">You can develop SMO applications on either a client or a server.</span></span>  
  
|<span data-ttu-id="b40d6-106">디렉터리</span><span class="sxs-lookup"><span data-stu-id="b40d6-106">Directory</span></span>|<span data-ttu-id="b40d6-107">파일</span><span class="sxs-lookup"><span data-stu-id="b40d6-107">File</span></span>|<span data-ttu-id="b40d6-108">Description</span><span class="sxs-lookup"><span data-stu-id="b40d6-108">Description</span></span>|  
|---------------|----------|-----------------|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|<span data-ttu-id="b40d6-109">Microsoft.SqlServer.ConnectionInfo.dll</span><span class="sxs-lookup"><span data-stu-id="b40d6-109">Microsoft.SqlServer.ConnectionInfo.dll</span></span>|<span data-ttu-id="b40d6-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대한 연결 지원을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="b40d6-110">Contains support for connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|<span data-ttu-id="b40d6-111">Microsoft.SqlServer.ServiceBrokerEnum.dll</span><span class="sxs-lookup"><span data-stu-id="b40d6-111">Microsoft.SqlServer.ServiceBrokerEnum.dll</span></span>|<span data-ttu-id="b40d6-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Service Broker 프로그래밍 지원을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="b40d6-112">Contains support for programming the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service Broker.</span></span> <span data-ttu-id="b40d6-113">이 파일은 Service Broker에 액세스하는 프로그램에만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b40d6-113">This is required only in programs that access the Service Broker.</span></span>|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|<span data-ttu-id="b40d6-114">Microsoft.SqlServer.Smo.dll</span><span class="sxs-lookup"><span data-stu-id="b40d6-114">Microsoft.SqlServer.Smo.dll</span></span>|<span data-ttu-id="b40d6-115">SMO 클래스를 대부분 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="b40d6-115">Contains the most of the SMO classes.</span></span>|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|<span data-ttu-id="b40d6-116">Microsoft.SqlServer.SmoExtended.dll</span><span class="sxs-lookup"><span data-stu-id="b40d6-116">Microsoft.SqlServer.SmoExtended.dll</span></span><br /><br /> <span data-ttu-id="b40d6-117">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span><span class="sxs-lookup"><span data-stu-id="b40d6-117">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span></span><br /><br /> <span data-ttu-id="b40d6-118">Microsoft.SqlServer.SqlEnum.dll</span><span class="sxs-lookup"><span data-stu-id="b40d6-118">Microsoft.SqlServer.SqlEnum.dll</span></span>|<span data-ttu-id="b40d6-119">SMO 클래스 지원을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="b40d6-119">Contains support for the SMO classes.</span></span>|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|<span data-ttu-id="b40d6-120">Microsoft.SqlServer.WmiEnum.dll</span><span class="sxs-lookup"><span data-stu-id="b40d6-120">Microsoft.SqlServer.WmiEnum.dll</span></span>|<span data-ttu-id="b40d6-121">WMI(Windows Management Instrumentation) 공급자 클래스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="b40d6-121">Contains the Windows Management Instrumentation (WMI) Provider classes.</span></span> <span data-ttu-id="b40d6-122">이 파일은 WMI 공급자 클래스를 사용하는 프로그램에만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b40d6-122">This is required only for programs that use the WMI Provider classes.</span></span>|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|<span data-ttu-id="b40d6-123">Microsoft.SqlServer.RegSvrEnum.dll</span><span class="sxs-lookup"><span data-stu-id="b40d6-123">Microsoft.SqlServer.RegSvrEnum.dll</span></span>|<span data-ttu-id="b40d6-124">등록된 서버 클래스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="b40d6-124">Contains the Registered Server classes.</span></span> <span data-ttu-id="b40d6-125">이 파일은 등록된 서버 클래스를 사용하는 프로그램에만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b40d6-125">This is required only for programs that use the Registered Server classes.</span></span>|  
  
  
