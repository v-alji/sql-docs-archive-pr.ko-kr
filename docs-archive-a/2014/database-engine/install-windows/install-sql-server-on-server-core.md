---
title: Server Core에 SQL Server 2014 설치 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 1dd294cc-5b69-4d0c-9005-3e307b75678b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d2614c43bb763757db7db46b1c7a966221da96f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729784"
---
# <a name="install-sql-server-2014-on-server-core"></a><span data-ttu-id="7c6e3-102">Server Core에 SQL Server 2014 설치</span><span class="sxs-lookup"><span data-stu-id="7c6e3-102">Install SQL Server 2014 on Server Core</span></span>
  <span data-ttu-id="7c6e3-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 또는 [!INCLUDE[win8srv](../../includes/win8srv-md.md)]의 Server Core 설치에 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-103">You can install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span> <span data-ttu-id="7c6e3-104">이 항목에서는 Server  Core에 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 를 설치하기 위한 설치 관련 세부 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-104">This topic provides setup-specific details for installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on Server Core.</span></span>  
  
 <span data-ttu-id="7c6e3-105">[!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 또는 [!INCLUDE[win8srv](../../includes/win8srv-md.md)] 운영 체제의 Server  Core  설치 옵션은 특정 서버 역할을 실행하기 위한 최소 환경을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-105">The Server Core installation option for the [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] or [!INCLUDE[win8srv](../../includes/win8srv-md.md)] operating system provides a minimal environment for running specific server roles.</span></span> <span data-ttu-id="7c6e3-106">이렇게 하면 유지 관리 및 관리 요구 사항이 줄어들고 이러한 서버 역할에 대한 공격 노출 영역이 감소합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-106">This helps to reduce maintenance and management requirements and the attack surface for those server roles.</span></span> <span data-ttu-id="7c6e3-107">에서 구현 되는 Server Core에 대 한 자세한 내용은 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] [server Core For Windows Server 2008 R2](https://go.microsoft.com/fwlink/?LinkId=202439) (를 참조 하세요 https://go.microsoft.com/fwlink/?LinkId=202439) .</span><span class="sxs-lookup"><span data-stu-id="7c6e3-107">For more information on Server Core as implemented on [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)], see [Server Core for Windows Server 2008 R2](https://go.microsoft.com/fwlink/?LinkId=202439) (https://go.microsoft.com/fwlink/?LinkId=202439).</span></span> <span data-ttu-id="7c6e3-108">[!INCLUDE[win8srv](../../includes/win8srv-md.md)]에서 구현되는 Server Core에 대한 자세한 내용은 [Windows Server 2012용 Server Core](https://msdn.microsoft.com/library/hh846323\(VS.85\).aspx)(https://msdn.microsoft.com/library/hh846323(VS.85).aspx) 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-108">For more information on Server Core as implemented on [!INCLUDE[win8srv](../../includes/win8srv-md.md)], see [Server Core for Windows Server 2012](https://msdn.microsoft.com/library/hh846323\(VS.85\).aspx) (https://msdn.microsoft.com/library/hh846323(VS.85).aspx).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7c6e3-109">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="7c6e3-109">Prerequisites</span></span>  
  
|<span data-ttu-id="7c6e3-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="7c6e3-110">Requirement</span></span>|<span data-ttu-id="7c6e3-111">설치 방법</span><span class="sxs-lookup"><span data-stu-id="7c6e3-111">How to install</span></span>|  
|-----------------|--------------------|  
|[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <span data-ttu-id="7c6e3-112">2.0 SP2</span><span class="sxs-lookup"><span data-stu-id="7c6e3-112">2.0 SP2</span></span>|<span data-ttu-id="7c6e3-113">[!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1  및 [!INCLUDE[win8srv](../../includes/win8srv-md.md)]의 Server  Core  설치에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-113">Included in Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 and [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span> <span data-ttu-id="7c6e3-114">활성화되어 있지 않은 경우 설치 프로그램이 기본적으로 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-114">If it is not enabled, Setup enables it by default.</span></span><br /><br /> <span data-ttu-id="7c6e3-115">한 컴퓨터에서 2.0, 3.0, 3.5 버전을 함께 실행할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-115">It is not possible to run versions 2.0, 3.0, and 3.5 side by side on a computer.</span></span> <span data-ttu-id="7c6e3-116">.NET  Framework  3.5  SP1을 설치하면 2.0  및 3.0  레이어가 자동으로 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-116">When you install the .NET Framework 3.5 SP1, you get the 2.0 and 3.0 layers automatically.</span></span>|  
|[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <span data-ttu-id="7c6e3-117">3.5  SP1  Full  Profile</span><span class="sxs-lookup"><span data-stu-id="7c6e3-117">3.5 SP1 Full Profile</span></span>|<span data-ttu-id="7c6e3-118">[!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1의 Server  Core  설치에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-118">Included in Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1.</span></span> <span data-ttu-id="7c6e3-119">활성화되어 있지 않은 경우 설치 프로그램이 기본적으로 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-119">If it is not enabled, Setup enables it by default.</span></span><br /><br /> <span data-ttu-id="7c6e3-120">Windows 서버 운영 체제가 설치된 컴퓨터에서 .NET 3.5 SP1에 종속된 구성 요소를 설치하려면 설치 프로그램을 실행하기 전에 .NET Framework 3.5 SP1을 다운로드하고 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-120">On a computer with Windows server operating system you must download and install .NET Framework 3.5 SP1 before you run Setup, to install components dependent on .NET 3.5 SP1.</span></span><br /><br /> <span data-ttu-id="7c6e3-121">에서 .NET Framework 3.5를 가져오고 사용 하는 방법에 대 한 권장 사항 및 지침에 대 한 자세한 내용은 [!INCLUDE[win8srv](../../includes/win8srv-md.md)] [Microsoft .NET Framework 3.5 배포 고려 사항](https://msdn.microsoft.com/library/windows/hardware/hh975396) ()을 참조 하세요 https://msdn.microsoft.com/library/windows/hardware/hh975396) .</span><span class="sxs-lookup"><span data-stu-id="7c6e3-121">For more information about the recommendations and guidance on how to acquire and enable .NET Framework 3.5 in [!INCLUDE[win8srv](../../includes/win8srv-md.md)], see [Microsoft .NET Framework 3.5 Deployment Considerations](https://msdn.microsoft.com/library/windows/hardware/hh975396) (https://msdn.microsoft.com/library/windows/hardware/hh975396).</span></span>|  
|[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <span data-ttu-id="7c6e3-122">4  Server  Core  Profile</span><span class="sxs-lookup"><span data-stu-id="7c6e3-122">4 Server Core Profile</span></span>|<span data-ttu-id="7c6e3-123">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 를 제외한 모든 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]버전의 경우,  설치 프로그램은 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4  Server  Core  Profile을 필수 구성 요소로 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-123">For all editions of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] except [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], Setup installs the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4 Server Core Profile as a prerequisite.</span></span><br /><br /> <span data-ttu-id="7c6e3-124">의 경우, [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] server core [용 Microsoft .NET Framework 4 (독립 실행형 설치 관리자)](https://www.microsoft.com/download/details.aspx?id=17718) 에서 4 server core 프로필을 다운로드 https://www.microsoft.com/download/details.aspx?id=17718) 하 고 설치를 계속 하기 전에 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-124">For [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)], download the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4 Server Core Profile from [Microsoft .NET Framework 4 (Standalone Installer) for Server Core](https://www.microsoft.com/download/details.aspx?id=17718) (https://www.microsoft.com/download/details.aspx?id=17718), and install it before you proceed with the setup.</span></span>|  
|<span data-ttu-id="7c6e3-125">Windows  Installer  4.5</span><span class="sxs-lookup"><span data-stu-id="7c6e3-125">Windows Installer 4.5</span></span>|<span data-ttu-id="7c6e3-126">[!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1  및 [!INCLUDE[win8srv](../../includes/win8srv-md.md)]의 Server  Core  설치와 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-126">Shipped with Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 and [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span>|  
|<span data-ttu-id="7c6e3-127">Windows PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="7c6e3-127">Windows PowerShell 2.0</span></span>|<span data-ttu-id="7c6e3-128">[!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1  및 [!INCLUDE[win8srv](../../includes/win8srv-md.md)]의 Server  Core  설치와 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-128">Shipped with Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 and [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span>|  
  
##  <a name="supported-features"></a><a name="BK_SupportedFeatures"></a> <span data-ttu-id="7c6e3-129">지원되는 기능</span><span class="sxs-lookup"><span data-stu-id="7c6e3-129">Supported Features</span></span>  
 <span data-ttu-id="7c6e3-130">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SP1  및 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server  Core  설치의 [!INCLUDE[win8srv](../../includes/win8srv-md.md)]에서 지원하는 기능을 다음 표에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-130">Use the following table to find which features are supported in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on a Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 and [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span>  
  
|<span data-ttu-id="7c6e3-131">기능</span><span class="sxs-lookup"><span data-stu-id="7c6e3-131">Feature</span></span>|<span data-ttu-id="7c6e3-132">지원됨</span><span class="sxs-lookup"><span data-stu-id="7c6e3-132">Supported</span></span>|  
|-------------|---------------|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="7c6e3-133">서비스</span><span class="sxs-lookup"><span data-stu-id="7c6e3-133">Services</span></span>|<span data-ttu-id="7c6e3-134">예</span><span class="sxs-lookup"><span data-stu-id="7c6e3-134">Yes</span></span>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7c6e3-135">복제</span><span class="sxs-lookup"><span data-stu-id="7c6e3-135">Replication</span></span>|<span data-ttu-id="7c6e3-136">예</span><span class="sxs-lookup"><span data-stu-id="7c6e3-136">Yes</span></span>|  
|<span data-ttu-id="7c6e3-137">전체 텍스트 검색</span><span class="sxs-lookup"><span data-stu-id="7c6e3-137">Full Text Search</span></span>|<span data-ttu-id="7c6e3-138">예</span><span class="sxs-lookup"><span data-stu-id="7c6e3-138">Yes</span></span>|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|<span data-ttu-id="7c6e3-139">예</span><span class="sxs-lookup"><span data-stu-id="7c6e3-139">Yes</span></span>|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|<span data-ttu-id="7c6e3-140">예</span><span class="sxs-lookup"><span data-stu-id="7c6e3-140">No</span></span>|  
|<span data-ttu-id="7c6e3-141">SSDT([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Data Tools)</span><span class="sxs-lookup"><span data-stu-id="7c6e3-141">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Data Tools (SSDT)</span></span>|<span data-ttu-id="7c6e3-142">예</span><span class="sxs-lookup"><span data-stu-id="7c6e3-142">No</span></span>|  
|<span data-ttu-id="7c6e3-143">클라이언트 도구 연결</span><span class="sxs-lookup"><span data-stu-id="7c6e3-143">Client Tools Connectivity</span></span>|<span data-ttu-id="7c6e3-144">예</span><span class="sxs-lookup"><span data-stu-id="7c6e3-144">Yes</span></span>|  
|<span data-ttu-id="7c6e3-145">Integration Services 서버<sup>[1]</sup></span><span class="sxs-lookup"><span data-stu-id="7c6e3-145">Integration Services Server<sup>[1]</sup></span></span>|<span data-ttu-id="7c6e3-146">예</span><span class="sxs-lookup"><span data-stu-id="7c6e3-146">Yes</span></span>|  
|<span data-ttu-id="7c6e3-147">클라이언트 도구 이전 버전과의 호환성</span><span class="sxs-lookup"><span data-stu-id="7c6e3-147">Client Tools Backward Compatibility</span></span>|<span data-ttu-id="7c6e3-148">예</span><span class="sxs-lookup"><span data-stu-id="7c6e3-148">No</span></span>|  
|<span data-ttu-id="7c6e3-149">클라이언트 도구 SDK</span><span class="sxs-lookup"><span data-stu-id="7c6e3-149">Client Tools SDK</span></span>|<span data-ttu-id="7c6e3-150">예</span><span class="sxs-lookup"><span data-stu-id="7c6e3-150">No</span></span>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7c6e3-151">온라인 설명서</span><span class="sxs-lookup"><span data-stu-id="7c6e3-151">Books Online</span></span>|<span data-ttu-id="7c6e3-152">예</span><span class="sxs-lookup"><span data-stu-id="7c6e3-152">No</span></span>|  
|<span data-ttu-id="7c6e3-153">관리 도구 -  기본</span><span class="sxs-lookup"><span data-stu-id="7c6e3-153">Management Tools - Basic</span></span>|<span data-ttu-id="7c6e3-154">원격 전용<sup>[2]</sup></span><span class="sxs-lookup"><span data-stu-id="7c6e3-154">Remote Only<sup>[2]</sup></span></span>|  
|<span data-ttu-id="7c6e3-155">관리 도구 - 전체</span><span class="sxs-lookup"><span data-stu-id="7c6e3-155">Management Tools - Complete</span></span>|<span data-ttu-id="7c6e3-156">원격 전용<sup>[2]</sup></span><span class="sxs-lookup"><span data-stu-id="7c6e3-156">Remote Only<sup>[2]</sup></span></span>|  
|<span data-ttu-id="7c6e3-157">Distributed  Replay  Controller</span><span class="sxs-lookup"><span data-stu-id="7c6e3-157">Distributed Replay Controller</span></span>|<span data-ttu-id="7c6e3-158">예</span><span class="sxs-lookup"><span data-stu-id="7c6e3-158">No</span></span>|  
|<span data-ttu-id="7c6e3-159">Distributed  Replay  Client</span><span class="sxs-lookup"><span data-stu-id="7c6e3-159">Distributed Replay Client</span></span>|<span data-ttu-id="7c6e3-160">원격 전용<sup>[2]</sup></span><span class="sxs-lookup"><span data-stu-id="7c6e3-160">Remote Only<sup>[2]</sup></span></span>|  
|<span data-ttu-id="7c6e3-161">SQL  클라이언트 연결 SDK</span><span class="sxs-lookup"><span data-stu-id="7c6e3-161">SQL Client Connectivity SDK</span></span>|<span data-ttu-id="7c6e3-162">예</span><span class="sxs-lookup"><span data-stu-id="7c6e3-162">Yes</span></span>|  
|<span data-ttu-id="7c6e3-163">Microsoft  Sync  Framework</span><span class="sxs-lookup"><span data-stu-id="7c6e3-163">Microsoft Sync Framework</span></span>|<span data-ttu-id="7c6e3-164">예<sup>[3]</sup></span><span class="sxs-lookup"><span data-stu-id="7c6e3-164">Yes<sup>[3]</sup></span></span>|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]|<span data-ttu-id="7c6e3-165">아니요</span><span class="sxs-lookup"><span data-stu-id="7c6e3-165">No</span></span>|  
|[!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]|<span data-ttu-id="7c6e3-166">아니요</span><span class="sxs-lookup"><span data-stu-id="7c6e3-166">No</span></span>|  
  
 <span data-ttu-id="7c6e3-167"><sup>[1]</sup> 의 새 Integration Services 서버 및 해당 기능에 대 한 자세한 내용은 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [INTEGRATION SERVICES &#40;SSIS&#41; 서버](../../integration-services/catalog/integration-services-ssis-server-and-catalog.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-167"><sup>[1]</sup>For more information about the new Integration Services Server and its features in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], see [Integration Services &#40;SSIS&#41; Server](../../integration-services/catalog/integration-services-ssis-server-and-catalog.md).</span></span>  
  
 <span data-ttu-id="7c6e3-168"><sup>[2]</sup> Server Core에는 이러한 기능을 설치할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-168"><sup>[2]</sup>Installation of these features on Server Core is not supported.</span></span> <span data-ttu-id="7c6e3-169">이러한 구성 요소는 Server Core에 설치된 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 서비스에 연결되어 있는 [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core SP1 또는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Server Core 이외의 서버에 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-169">These components can be installed on a different server that is not [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core, and connected to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] services installed on Server Core.</span></span>  
  
 <span data-ttu-id="7c6e3-170"><sup>[3]</sup> Microsoft Sync Framework는 설치 패키지에 포함 되어 있지 않습니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="7c6e3-170"><sup>[3]</sup>Microsoft Sync Framework is not included in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installation package.</span></span> <span data-ttu-id="7c6e3-171">이 [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/?LinkId=221788) (페이지에서 적절 한 버전의 Sync Framework를 다운로드 https://go.microsoft.com/fwlink/?LinkId=221788) 하 여 SP1 또는의 Server Core 설치를 실행 하는 컴퓨터에 설치할 수 있습니다 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] [!INCLUDE[win8srv](../../includes/win8srv-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="7c6e3-171">You can download the appropriate version of Sync Framework from this [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=221788) (https://go.microsoft.com/fwlink/?LinkId=221788) page and install it on a computer that is running Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span>  
  
## <a name="supported-scenario-matrix"></a><span data-ttu-id="7c6e3-172">지원되는 시나리오 매트릭스</span><span class="sxs-lookup"><span data-stu-id="7c6e3-172">Supported Scenario Matrix</span></span>  
 <span data-ttu-id="7c6e3-173">다음 표에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SP1 및 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 의 Server Core 설치에 [!INCLUDE[win8srv](../../includes/win8srv-md.md)]를 설치할 때 지원되는 시나리오 매트릭스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-173">The following table shows the supported scenario matrix for installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on a Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 and [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span>  
  
|||  
|-|-|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7c6e3-174">버전</span><span class="sxs-lookup"><span data-stu-id="7c6e3-174">editions</span></span>|<span data-ttu-id="7c6e3-175">모든 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 64 비트 버전<sup>[1]</sup></span><span class="sxs-lookup"><span data-stu-id="7c6e3-175">All [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 64-bit editions<sup>[1]</sup></span></span>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7c6e3-176">언어</span><span class="sxs-lookup"><span data-stu-id="7c6e3-176">language</span></span>|<span data-ttu-id="7c6e3-177">모든 언어</span><span class="sxs-lookup"><span data-stu-id="7c6e3-177">All languages</span></span>|  
|<span data-ttu-id="7c6e3-178">OS 언어/로캘에서[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 언어(조합)</span><span class="sxs-lookup"><span data-stu-id="7c6e3-178">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] language on OS language/locale (combination)</span></span>|<span data-ttu-id="7c6e3-179">JPN(일본어) Windows에서 ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c6e3-179">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on JPN (Japanese) Windows</span></span><br /><br /> <span data-ttu-id="7c6e3-180">GER(독일어) Windows에서 ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c6e3-180">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on GER (German) Windows</span></span><br /><br /> <span data-ttu-id="7c6e3-181">CHS(중국어-중국) Windows에서 ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c6e3-181">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on CHS (Chinese-China) Windows</span></span><br /><br /> <span data-ttu-id="7c6e3-182">ARA(아라비아어 (SA)) Windows에서 ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c6e3-182">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on ARA (Arabic (SA)) Windows</span></span><br /><br /> <span data-ttu-id="7c6e3-183">THA(태국) Windows에서 ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c6e3-183">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on THA (Thai) Windows</span></span><br /><br /> <span data-ttu-id="7c6e3-184">TRK(터키어) Windows에서 ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c6e3-184">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on TRK (Turkish) Windows</span></span><br /><br /> <span data-ttu-id="7c6e3-185">pt-PT(포르투갈어 포르투갈) Windows에서 ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c6e3-185">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on pt-PT (Portuguese Portugal) Windows</span></span><br /><br /> <span data-ttu-id="7c6e3-186">ENG(영어) Windows에서 ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c6e3-186">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on ENG (English) Windows</span></span>|  
|<span data-ttu-id="7c6e3-187">Windows  버전</span><span class="sxs-lookup"><span data-stu-id="7c6e3-187">Windows edition</span></span>|[!INCLUDE[win8srv](../../includes/win8srv-md.md)] <span data-ttu-id="7c6e3-188">64비트 x64 Datacenter</span><span class="sxs-lookup"><span data-stu-id="7c6e3-188">64-bit x64 Datacenter</span></span><br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)] <span data-ttu-id="7c6e3-189">64비트 x64 Standard</span><span class="sxs-lookup"><span data-stu-id="7c6e3-189">64-bit x64 Standard</span></span><br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] <span data-ttu-id="7c6e3-190">SP1 64비트 x64 Data Center Server Core</span><span class="sxs-lookup"><span data-stu-id="7c6e3-190">SP1 64-bit x64 Data Center Server Core</span></span><br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] <span data-ttu-id="7c6e3-191">SP1 64비트 x64 Enterprise Server Core</span><span class="sxs-lookup"><span data-stu-id="7c6e3-191">SP1 64-bit x64 Enterprise Server Core</span></span><br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] <span data-ttu-id="7c6e3-192">SP1 64비트 x64 Standard Server Core</span><span class="sxs-lookup"><span data-stu-id="7c6e3-192">SP1 64-bit x64 Standard Server Core</span></span><br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] <span data-ttu-id="7c6e3-193">SP1 64비트 x64 Web Server Core</span><span class="sxs-lookup"><span data-stu-id="7c6e3-193">SP1 64-bit x64 Web Server Core</span></span>|  
  
 <span data-ttu-id="7c6e3-194"><sup>[1]</sup> 32 비트 버전의 버전 설치 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 는 Server Core에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-194"><sup>[1]</sup>Installing the 32-bit version of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] editions is not supported on Server Core.</span></span>  
  
## <a name="upgrading"></a><span data-ttu-id="7c6e3-195">업그레이드 중</span><span class="sxs-lookup"><span data-stu-id="7c6e3-195">Upgrading</span></span>  
 <span data-ttu-id="7c6e3-196">Server Core 설치 시 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 에서 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 로 업그레이드는 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-196">On Server Core installations, upgrading from [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] to [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] is supported.</span></span>  
  
## <a name="installation"></a><span data-ttu-id="7c6e3-197">설치</span><span class="sxs-lookup"><span data-stu-id="7c6e3-197">Installation</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="7c6e3-198">는 Server  Core  운영 체제의 설치 마법사를 사용하는 설치를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-198">does not support setup by using the installation wizard on the Server Core operating system.</span></span> <span data-ttu-id="7c6e3-199">Server Core에 설치할 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치는 /Q 매개 변수를 사용하는 완전 자동 모드 또는 /QS 매개 변수를 사용하는 단순 자동 모드를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-199">When installing on Server Core, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup supports full quiet mode by using the /Q parameter, or Quiet Simple mode by using the /QS parameter.</span></span> <span data-ttu-id="7c6e3-200">자세한 내용은 [명령 프롬프트에서 SQL Server 2014 설치](install-sql-server-from-the-command-prompt.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-200">For more information, see [Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md).</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="7c6e3-201">은 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 또는 [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core를 실행하는 컴퓨터에서 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 함께 설치할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-201">cannot be installed side-by-side with earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a computer that is running [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core.</span></span>  
  
 <span data-ttu-id="7c6e3-202">소프트웨어 사용이 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 볼륨 라이선스 계약 또는 공급 업체와의 ISV  또는 OEM  계약과 같은 별도의 계약에 의해 관리되지 않는 한 설치 방법에 상관없이 개인 또는 업체 대표로서 소프트웨어 사용 조건에 대한 동의를 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-202">Regardless of the installation method, you are required to confirm acceptance of the software license terms as an individual or on behalf of an entity, unless your use of the software is governed by a separate agreement such as a [!INCLUDE[msCoName](../../includes/msconame-md.md)] volume licensing agreement or a third-party agreement with an ISV or OEM.</span></span>  
  
 <span data-ttu-id="7c6e3-203">사용 조건은 검토 및 동의를 위해 설치 프로그램 사용자 인터페이스에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-203">The license terms are displayed for review and acceptance in the Setup user interface.</span></span> <span data-ttu-id="7c6e3-204">/Q 또는 /QS 매개 변수를 사용하는 무인 설치는 /IACCEPTSQLSERVERLICENSETERMS 매개 변수를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-204">Unattended installations (using the /Q or /QS parameters) must include the /IACCEPTSQLSERVERLICENSETERMS parameter.</span></span> <span data-ttu-id="7c6e3-205">[Microsoft 소프트웨어 사용권 계약(Microsoft Software License Terms)](https://go.microsoft.com/fwlink/?LinkId=148209)에서 사용 조건을 별도로 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-205">You can review the license terms separately at [Microsoft Software License Terms](https://go.microsoft.com/fwlink/?LinkId=148209).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7c6e3-206">소프트웨어의 수령 방법(예: [!INCLUDE[msCoName](../../includes/msconame-md.md)] 볼륨 라이선스를 통해 수령)에 따라 사용자의 소프트웨어 사용에 추가 조건이 적용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-206">Depending on how you received the software (for example, through [!INCLUDE[msCoName](../../includes/msconame-md.md)] volume licensing), your use of the software may be subject to additional terms and conditions.</span></span>  
  
 <span data-ttu-id="7c6e3-207">특정 기능을 설치하려면 /FEATURES  매개 변수를 사용하여 부모 기능 또는 기능 값을 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-207">To install specific features, use the /FEATURES parameter and specify the parent feature or feature values.</span></span> <span data-ttu-id="7c6e3-208">기능 매개 변수 및 사용에 대한 자세한 내용은 다음 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-208">For more information about feature parameters and their use, see the following sections.</span></span>  
  
### <a name="feature-parameters"></a><span data-ttu-id="7c6e3-209">기능 매개 변수</span><span class="sxs-lookup"><span data-stu-id="7c6e3-209">Feature Parameters</span></span>  
  
|<span data-ttu-id="7c6e3-210">기능 매개 변수</span><span class="sxs-lookup"><span data-stu-id="7c6e3-210">Feature parameter</span></span>|<span data-ttu-id="7c6e3-211">Description</span><span class="sxs-lookup"><span data-stu-id="7c6e3-211">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="7c6e3-212">SQLENGINE</span><span class="sxs-lookup"><span data-stu-id="7c6e3-212">SQLENGINE</span></span>|<span data-ttu-id="7c6e3-213">[!INCLUDE[ssDE](../../includes/ssde-md.md)]만 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-213">Installs only the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>|  
|<span data-ttu-id="7c6e3-214">복제</span><span class="sxs-lookup"><span data-stu-id="7c6e3-214">REPLICATION</span></span>|<span data-ttu-id="7c6e3-215">[!INCLUDE[ssDE](../../includes/ssde-md.md)]과 함께 복제 구성 요소를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-215">Installs the Replication component along with [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>|  
|<span data-ttu-id="7c6e3-216">FULLTEXT</span><span class="sxs-lookup"><span data-stu-id="7c6e3-216">FULLTEXT</span></span>|<span data-ttu-id="7c6e3-217">[!INCLUDE[ssDE](../../includes/ssde-md.md)]과 함께 전체 텍스트 구성 요소를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-217">Installs the FullText component along with [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>|  
|<span data-ttu-id="7c6e3-218">AS</span><span class="sxs-lookup"><span data-stu-id="7c6e3-218">AS</span></span>|<span data-ttu-id="7c6e3-219">모든 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 구성 요소를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-219">Installs all [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] components.</span></span>|  
|<span data-ttu-id="7c6e3-220">IS</span><span class="sxs-lookup"><span data-stu-id="7c6e3-220">IS</span></span>|<span data-ttu-id="7c6e3-221">모든 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 구성 요소를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-221">Installs all [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components.</span></span>|  
|<span data-ttu-id="7c6e3-222">CONN</span><span class="sxs-lookup"><span data-stu-id="7c6e3-222">CONN</span></span>|<span data-ttu-id="7c6e3-223">연결 구성 요소를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-223">Installs the connectivity components.</span></span>|  
  
 <span data-ttu-id="7c6e3-224">기능 매개 변수에 대한 다음과 같은 사용 예를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-224">See the following examples of the usage of feature parameters:</span></span>  
  
|<span data-ttu-id="7c6e3-225">매개 변수 및 값</span><span class="sxs-lookup"><span data-stu-id="7c6e3-225">Parameter and values</span></span>|<span data-ttu-id="7c6e3-226">Description</span><span class="sxs-lookup"><span data-stu-id="7c6e3-226">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="7c6e3-227">/FEATURES=SQLEngine</span><span class="sxs-lookup"><span data-stu-id="7c6e3-227">/FEATURES=SQLEngine</span></span>|<span data-ttu-id="7c6e3-228">[!INCLUDE[ssDE](../../includes/ssde-md.md)]만 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-228">Installs only the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>|  
|<span data-ttu-id="7c6e3-229">/FEATURES=SQLEngine,FullText</span><span class="sxs-lookup"><span data-stu-id="7c6e3-229">/FEATURES=SQLEngine,FullText</span></span>|<span data-ttu-id="7c6e3-230">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 및 전체 텍스트를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-230">Installs the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and full-text.</span></span>|  
|<span data-ttu-id="7c6e3-231">/FEATURES=SQLEngine,Conn</span><span class="sxs-lookup"><span data-stu-id="7c6e3-231">/FEATURES=SQLEngine,Conn</span></span>|<span data-ttu-id="7c6e3-232">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 및 연결 구성 요소를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-232">Installs the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and the connectivity components.</span></span>|  
|<span data-ttu-id="7c6e3-233">/FEATURES=SQLEngine,AS,IS,Conn</span><span class="sxs-lookup"><span data-stu-id="7c6e3-233">/FEATURES=SQLEngine,AS,IS,Conn</span></span>|<span data-ttu-id="7c6e3-234">[!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]및 연결 구성 요소를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-234">Installs the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], and the connectivity components.</span></span>|  
  
### <a name="installation-options"></a><span data-ttu-id="7c6e3-235">설치 옵션</span><span class="sxs-lookup"><span data-stu-id="7c6e3-235">Installation Options</span></span>  
 <span data-ttu-id="7c6e3-236">설치 프로그램에서는 Server  Core  운영 체제에 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 를 설치할 때 다음과 같은 설치 옵션이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-236">The Setup supports the following installation options while installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on a Server Core operating system:</span></span>  
  
1.  <span data-ttu-id="7c6e3-237">**명령줄에서 설치**</span><span class="sxs-lookup"><span data-stu-id="7c6e3-237">**Installation from Command Line**</span></span>  
  
     <span data-ttu-id="7c6e3-238">명령 프롬프트 설치 옵션을 사용하여 특정 기능을 설치하려면 /FEATURES  매개 변수를 사용하여 부모 기능 또는 기능 값을 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-238">To install specific features using the command prompt installation option, use the /FEATURES parameter and specify the parent feature or feature values.</span></span> <span data-ttu-id="7c6e3-239">다음은 명령줄 매개 변수를 사용한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-239">The following is an example of using the parameters from the command line:</span></span>  
  
    ```cmd
    setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,Replication /INSTANCENAME=MSSQLSERVER /SQLSVCACCOUNT="<DomainName\UserName>" /SQLSVCPASSWORD="<StrongPassword>" /SQLSYSADMINACCOUNTS="<DomainName\UserName>" /AGTSVCACCOUNT="NT AUTHORITY\Network Service" /TCPENABLED=1 /IACCEPTSQLSERVERLICENSETERMS  
    ```  
  
2.  <span data-ttu-id="7c6e3-240">**구성 파일을 사용하여 설치**</span><span class="sxs-lookup"><span data-stu-id="7c6e3-240">**Installation using Configuration File**</span></span>  
  
     <span data-ttu-id="7c6e3-241">구성 파일은 명령 프롬프트에서 설치할 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-241">Setup supports the use of the configuration file only through the command prompt.</span></span> <span data-ttu-id="7c6e3-242">구성 파일은 기본 구조의 매개 변수(이름/값 쌍)  및 설명 주석이 포함된 텍스트 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-242">The configuration file is a text file with the basic structure of a parameter (name/value pair) and a descriptive comment.</span></span> <span data-ttu-id="7c6e3-243">명령 프롬프트에 지정된 구성 파일은 파일 확장명이 .INI여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-243">The configuration file specified at the command prompt should have an .INI file name extension.</span></span> <span data-ttu-id="7c6e3-244">다음 ConfigurationFile.INI에 대한 예를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-244">See the following examples of ConfigurationFile.INI:</span></span>  
  
    -   <span data-ttu-id="7c6e3-245">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 설치</span><span class="sxs-lookup"><span data-stu-id="7c6e3-245">Installing [!INCLUDE[ssDE](../../includes/ssde-md.md)]</span></span>  
  
         <span data-ttu-id="7c6e3-246">다음 예제에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)]을 포함하는 새 독립 실행형 인스턴스를 설치하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-246">The following example shows how to install a new stand-alone instance that includes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)]:</span></span>  
  
        ```  
        ; ssNoVersion Configuration File  
        [OPTIONS]  
  
        ; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE. This is a required parameter.   
  
        ACTION="Install"  
  
        ; Specifies features to install, uninstall, or upgrade. The lists of features include SQLEngine, FullText, Replication, AS, IS, and Conn.   
  
        FEATURES=SQLENGINE  
  
        ; Specify a default or named instance. MSSQLSERVER is the default instance for non-Express editions and SQLExpress for Express editions. This parameter is required when installing the ssNoVersion Database Engine, and Analysis Services (AS).  
  
        INSTANCENAME="MSSQLSERVER"  
  
        ; Specify the Instance ID for the ssNoVersion features you have specified. ssNoVersion directory structure, registry structure, and service names will incorporate the instance ID of the ssNoVersion instance.   
  
        INSTANCEID="MSSQLSERVER"  
  
        ; Account for ssNoVersion service: Domain\User or system account.   
  
        SQLSVCACCOUNT="NT Service\MSSQLSERVER"  
  
        ; Windows account(s) to provision as ssNoVersion system administrators.   
  
        SQLSYSADMINACCOUNTS="<DomainName\UserName>"  
  
        ; Accept the License agreement to continue with Installation  
  
        IAcceptSQLServerLicenseTerms="True"
        ```  
  
    -   <span data-ttu-id="7c6e3-247">연결 구성 요소 설치</span><span class="sxs-lookup"><span data-stu-id="7c6e3-247">Installing connectivity components</span></span>  
  
         <span data-ttu-id="7c6e3-248">다음 예에서는 연결 구성 요소를 설치하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-248">The following example shows how to install the connectivity components:</span></span>  
  
        ```  
        ; ssNoVersion Configuration File  
        [OPTIONS]  
  
        ; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE. This is a required parameter.   
  
        ACTION="Install"  
  
        ; Specifies features to install, uninstall, or upgrade. The lists of features include SQLEngine, FullText, Replication, AS, IS, and Conn.   
  
        FEATURES=Conn  
  
        ; Specifies acceptance of License Terms  
  
        IAcceptSQLServerLicenseTerms="True
        ```  
  
    -   <span data-ttu-id="7c6e3-249">모든 지원 기능 설치</span><span class="sxs-lookup"><span data-stu-id="7c6e3-249">Installing all supported features</span></span>  
  
         <span data-ttu-id="7c6e3-250">다음 예에서는 Server  Core에서 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 의 모든 지원되는 기능을 설치하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-250">The following example shows how to install all supported features of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on Server Core:</span></span>  
  
        ```  
        ; ssNoVersion Configuration File  
        [OPTIONS]  
        ; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE. This is a required parameter.   
  
        ACTION="Install"  
  
        ; Specifies features to install, uninstall, or upgrade. The lists of features include SQLEngine, FullText, Replication, AS, IS, and Conn.   
  
        FEATURES=SQLENGINE,FullText,Replication,AS,IS,Conn  
  
        ; Specify a default or named instance. MSSQLSERVER is the default instance for non-Express editions and SQLExpress for Express editions. This parameter is required when installing the ssNoVersion Database Engine (SQL), or Analysis Services (AS).  
  
        INSTANCENAME="MSSQLSERVER"  
  
        ; Specify the Instance ID for the ssNoVersion features you have specified. ssNoVersion directory structure, registry structure, and service names will incorporate the instance ID of the ssNoVersion instance.   
  
        INSTANCEID="MSSQLSERVER"  
  
        ; Account for ssNoVersion service: Domain\User or system account.   
  
        SQLSVCACCOUNT="NT Service\MSSQLSERVER"  
  
        ; Windows account(s) to provision as ssNoVersion system administrators.   
  
        SQLSYSADMINACCOUNTS="<DomainName\UserName>"  
  
        ; The name of the account that the Analysis Services service runs under.   
  
        ASSVCACCOUNT= "NT Service\MSSQLServerOLAPService"  
  
        ; Specifies the list of administrator accounts that need to be provisioned.   
  
        ASSYSADMINACCOUNTS="<DomainName\UserName>"  
  
        ; Specifies the server mode of the Analysis Services instance. Valid values are MULTIDIMENSIONAL, POWERPIVOT or TABULAR. ASSERVERMODE is case-sensitive. All values must be expressed in upper case.   
  
        ASSERVERMODE="MULTIDIMENSIONAL"  
  
        ; Optional value, which specifies the state of the TCP protocol for the ssNoVersion service. Supported values are: 0 to disable the TCP protocol, and 1 to enable the TCP protocol.  
  
        TCPENABLED=1  
  
        ;Specifies acceptance of License Terms  
  
        IAcceptSQLServerLicenseTerms="True"  
        ```  
  
     <span data-ttu-id="7c6e3-251">다음 예제에서는 구성 파일을 사용하여 설치 프로그램을 시작하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-251">The following examples show how you can launch the Setup using a configuration file.</span></span>  
  
    -   <span data-ttu-id="7c6e3-252">구성 파일</span><span class="sxs-lookup"><span data-stu-id="7c6e3-252">Configuration file</span></span>  
  
         <span data-ttu-id="7c6e3-253">다음은 구성 파일을 사용하는 방법을 보여 주는 예입니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-253">Following are some examples of how to use the configuration file:</span></span>  
  
        -   <span data-ttu-id="7c6e3-254">명령 프롬프트에 구성 파일을 지정하기</span><span class="sxs-lookup"><span data-stu-id="7c6e3-254">To specify the configuration file at the command prompt:</span></span>  
  
        ```cmd
        setup.exe /QS /ConfigurationFile=MyConfigurationFile.INI  
        ```  
  
        -   <span data-ttu-id="7c6e3-255">구성 파일 대신 명령 프롬프트에 암호 지정하기</span><span class="sxs-lookup"><span data-stu-id="7c6e3-255">To specify passwords at the command prompt instead of in the configuration file:</span></span>  
  
        ```cmd
        setup.exe /QS /SQLSVCPASSWORD="************" /ASSVCPASSWORD="************"  /ConfigurationFile=MyConfigurationFile.INI  
        ```  
  
    -   <span data-ttu-id="7c6e3-256">DefaultSetup.ini</span><span class="sxs-lookup"><span data-stu-id="7c6e3-256">DefaultSetup.ini</span></span>  
  
         <span data-ttu-id="7c6e3-257">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 원본 미디어의 루트 수준에서 \x86 및 \x64 폴더에 DefaultSetup.ini 파일이 있는 경우 DefaultSetup.ini 파일을 연 다음 *Features* 매개 변수를 파일에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-257">If you have the DefaultSetup.ini file in the \x86 and \x64 folders at the root level of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source media, open the DefaultSetup.ini file, and then add the *Features* parameter to the file.</span></span>  
  
         <span data-ttu-id="7c6e3-258">DefaultSetup.ini 파일이 없는 경우 파일을 생성하고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 원본 미디어의 루트 레벨에서 \x86 및 \x64 폴더에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-258">If the DefaultSetup.ini file does not exist, you can create it and copy it to the \x86 and \x64 folders at the root level of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source media.</span></span>  
  
## <a name="configuring-remote-access-of-ssnoversion-running-on-server-core"></a><span data-ttu-id="7c6e3-259">Server Core에서 실행하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 원격 액세스 구성</span><span class="sxs-lookup"><span data-stu-id="7c6e3-259">Configuring Remote Access of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Running on Server Core</span></span>  
 <span data-ttu-id="7c6e3-260">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SP1 또는 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 의 Server Core 설치에서 실행되는 [!INCLUDE[win8srv](../../includes/win8srv-md.md)]인스턴스의 원격 액세스를 구성하려면 아래에 설명된 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-260">Perform the actions described below to configure remote access of a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] instance that is running on a Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span>  
  
### <a name="enable-remote-connections-on-the-instance-of-ssnoversion"></a><span data-ttu-id="7c6e3-261">다음 인스턴스에서 원격 연결 설정: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c6e3-261">Enable remote connections on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 <span data-ttu-id="7c6e3-262">원격 연결을 설정하려면 SQLCMD.exe를 로컬로 사용하고 Server Core 인스턴스에 대해 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-262">To enable remote connections, use SQLCMD.exe locally and execute the following statements against the Server Core instance:</span></span>  
  
-   `EXEC sys.sp_configure N'remote access', N'1'`  
  
     `GO`  
  
-   `RECONFIGURE WITH OVERRIDE`  
  
     `GO`  
  
### <a name="enable-and-start-the-ssnoversion-browser-service"></a><span data-ttu-id="7c6e3-263">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 서비스 설정 및 시작</span><span class="sxs-lookup"><span data-stu-id="7c6e3-263">Enable and start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service</span></span>  
 <span data-ttu-id="7c6e3-264">Browser 서비스는 기본적으로 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-264">By default, the Browser service is disabled.</span></span>  <span data-ttu-id="7c6e3-265">Server Core에서 실행 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 해제된 경우 명령 프롬프트에서 다음 명령을 실행하여 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-265">If it is disabled on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on Server Core, run the following command from the command prompt to enable it:</span></span>  
  
 `sc config SQLBROWSER start= auto`  
  
 <span data-ttu-id="7c6e3-266">설정한 후 명령 프롬프트에서 다음 명령을 실행하여 서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-266">After it is enabled, run the following command from the command prompt to start the service:</span></span>  
  
 `net start SQLBROWSER`  
  
### <a name="create-exceptions-in-windows-firewall"></a><span data-ttu-id="7c6e3-267">Windows 방화벽에서 예외 생성</span><span class="sxs-lookup"><span data-stu-id="7c6e3-267">Create exceptions in Windows Firewall</span></span>  
 <span data-ttu-id="7c6e3-268">Windows 방화벽에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 액세스 관련 예외를 만들려면 [SQL Server 액세스를 허용하도록 Windows 방화벽 구성](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)에 지정된 단계를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-268">To create exceptions for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] access in Windows Firewall, follow the steps specified in [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
### <a name="enable-tcpip-on-the-instance-of-ssnoversion"></a><span data-ttu-id="7c6e3-269">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c6e3-269">Enable TCP/IP on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 <span data-ttu-id="7c6e3-270">TCP/IP 프로토콜은 Server Core에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대해 Windows PowerShell을 통해 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-270">The TCP/IP protocol can be enabled through Windows PowerShell for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on Server Core.</span></span> <span data-ttu-id="7c6e3-271">다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-271">Follow these steps:</span></span>  
  
1.  <span data-ttu-id="7c6e3-272">[!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 또는 [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core를 실행하는 컴퓨터에서 작업 관리자를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-272">On the computer that is running [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core, launch Task Manager.</span></span>  
  
2.  <span data-ttu-id="7c6e3-273">**애플리케이션** 탭에서 **새 작업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-273">On the **Applications** tab, click **New Task**.</span></span>  
  
3.  <span data-ttu-id="7c6e3-274">**새 작업 만들기** 대화 상자에서 **열기** 필드에 **sqlps.exe** 를 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-274">In the **Create New Task** dialog box, type **sqlps.exe** in the **Open** field and then click **OK**.</span></span> <span data-ttu-id="7c6e3-275">그러면 \*\* [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell\*\* 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-275">This opens the **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell** window.</span></span>  
  
4.  <span data-ttu-id="7c6e3-276">**Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell** 창에서 다음 스크립트를 실행하여 TCP/IP 프로토콜을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-276">In the **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell** window, run the following script to enable the TCP/IP protocol:</span></span>  
  
```powershell
$smo = 'Microsoft.SqlServer.Management.Smo.'  
$wmi = New-Object ($smo + 'Wmi.ManagedComputer')  
# Enable the TCP protocol on the default instance.  If the instance is named, replace MSSQLSERVER with the instance name in the following line.  
$uri = "ManagedComputer[@Name='" + (get-item env:\computername).Value + "']/ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
$Tcp = $wmi.GetSmoObject($uri)  
$Tcp.IsEnabled = $true  
$Tcp.Alter()  
$Tcp  
```  
  
## <a name="uninstallation"></a><span data-ttu-id="7c6e3-277">제거</span><span class="sxs-lookup"><span data-stu-id="7c6e3-277">Uninstallation</span></span>  
 <span data-ttu-id="7c6e3-278">[!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 또는 [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core를 실행하는 컴퓨터에 로그인하면 관리자 명령 프롬프트를 통한 제한된 데스크톱 환경이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-278">After you log on to a computer that is running [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core, you have a limited desktop environment with an Administrator command prompt.</span></span> <span data-ttu-id="7c6e3-279">이 명령 프롬프트를 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]인스턴스 제거를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-279">You can use this command prompt to initiate uninstallation of an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="7c6e3-280">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]인스턴스를 제거하려면 /Q  매개 변수를 사용하는 완전 자동 모드 또는 /QS  매개 변수를 사용하는 단순 자동 모드로 명령 프롬프트에서 제거를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-280">To uninstall an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], launch the uninstallation from the command prompt in full quiet mode by using the /Q parameter, or quiet simple mode by using the /QS parameter.</span></span> <span data-ttu-id="7c6e3-281">/QS  매개 변수는 UI를 통해 진행률을 표시하지만 입력은 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-281">The /QS parameter shows progress through the UI, but does not accept any input.</span></span> <span data-ttu-id="7c6e3-282">/Q는 사용자 인터페이스 없이 자동 모드로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-282">/Q runs in a quiet mode without any user interface.</span></span>  
  
 <span data-ttu-id="7c6e3-283">기존 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 제거하려면:</span><span class="sxs-lookup"><span data-stu-id="7c6e3-283">To uninstall an existing instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
```cmd
setup.exe /Q /Action=Uninstall /FEATURES=SQLEngine,AS,IS /INSTANCENAME=MSSQLSERVER  
```  
  
 <span data-ttu-id="7c6e3-284">명명된 인스턴스를 제거하려면 앞서 설명한 예에서 "MSSQLSERVER"  대신 인스턴스 이름을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-284">To remove a named instance, specify the name of the instance instead of "MSSQLSERVER" in the preceding example.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="7c6e3-285">실수로 명령 프롬프트를 닫은 경우 다음 단계에 따라 새 명령 프롬프트를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-285">If you accidentally close the command prompt, you can start a new command prompt by following these steps:</span></span>  
> 
>  1.  <span data-ttu-id="7c6e3-286">Ctrl+Shift+Esc를 눌러 작업 관리자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-286">Press Ctrl+Shift+Esc to display Task Manager.</span></span>  
> 2.  <span data-ttu-id="7c6e3-287">**애플리케이션** 탭에서 **새 작업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7c6e3-287">On the **Applications** tab, click **New Task**.</span></span>  
> 3.  <span data-ttu-id="7c6e3-288">**새 태스크 만들기** 대화 상자에서 **열기** 필드에 **cmd** 를 입력한 다음 [!INCLUDE[clickOK](../../includes/clickok-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7c6e3-288">In the **Create New Task** dialog box, type **cmd** in the **Open** field and then [!INCLUDE[clickOK](../../includes/clickok-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c6e3-289">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7c6e3-289">See Also</span></span>  
 <span data-ttu-id="7c6e3-290">[구성 파일을 사용 하 여 SQL Server 2014 설치](install-sql-server-using-a-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="7c6e3-290">[Install SQL Server 2014 Using a Configuration File](install-sql-server-using-a-configuration-file.md) </span></span>  
 <span data-ttu-id="7c6e3-291">[명령 프롬프트에서 SQL Server 2014 설치](install-sql-server-from-the-command-prompt.md) </span><span class="sxs-lookup"><span data-stu-id="7c6e3-291">[Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md) </span></span>  
 <span data-ttu-id="7c6e3-292">[SQL Server 2014 버전에서 지 원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="7c6e3-292">[Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span></span>  
 <span data-ttu-id="7c6e3-293">[Server Core 설치 옵션 시작 가이드](https://go.microsoft.com/fwlink/?LinkId=221422) </span><span class="sxs-lookup"><span data-stu-id="7c6e3-293">[Server Core Installation Option Getting Started Guide](https://go.microsoft.com/fwlink/?LinkId=221422) </span></span>  
 <span data-ttu-id="7c6e3-294">[Server Core 설치 구성: 개요](https://go.microsoft.com/fwlink/?LinkId=221423) </span><span class="sxs-lookup"><span data-stu-id="7c6e3-294">[Configuring a Server Core installation: Overview](https://go.microsoft.com/fwlink/?LinkId=221423) </span></span>  
 <span data-ttu-id="7c6e3-295">[작업 포커스가 나열 된 Windows PowerShell의 장애 조치 (Failover) 클러스터 Cmdlet](https://go.microsoft.com/fwlink/?LinkId=221419) </span><span class="sxs-lookup"><span data-stu-id="7c6e3-295">[Failover Cluster Cmdlets in Windows PowerShell Listed by Task Focus](https://go.microsoft.com/fwlink/?LinkId=221419) </span></span>  
 [<span data-ttu-id="7c6e3-296">Cluster.exe 명령을 장애 조치(failover) 클러스터용 Windows PowerShell Cmdlet에 매핑</span><span class="sxs-lookup"><span data-stu-id="7c6e3-296">Mapping Cluster.exe Commands to Windows PowerShell Cmdlets for Failover Clusters</span></span>](https://go.microsoft.com/fwlink/?LinkId=221421)  
