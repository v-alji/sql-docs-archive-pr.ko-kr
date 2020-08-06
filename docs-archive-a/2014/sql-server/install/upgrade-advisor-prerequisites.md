---
title: 업그레이드 관리자 필수 구성 요소 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- requirements [Upgrade Advisor]
- software [Upgrade Advisor]
- system requirements [Upgrade Advisor]
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, prerequisites
- prerequisites [Upgrade Advisor]
- Upgrade Advisor [SQL Server], prerequisites
ms.assetid: d21a39e5-5f81-4096-a7dd-f244e4779992
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 41c97cf585d1768c7aebeec2613ee8744cb220da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650410"
---
# <a name="upgrade-advisor-prerequisites"></a><span data-ttu-id="08457-102">업그레이드 관리자 필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="08457-102">Upgrade Advisor Prerequisites</span></span>
  <span data-ttu-id="08457-103">이 항목에서는 업그레이드 관리자를 위한 소프트웨어 요구 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="08457-103">This topic describes the software requirements for Upgrade Advisor.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="08457-104">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="08457-104">Prerequisites</span></span>  
 <span data-ttu-id="08457-105">업그레이드 관리자 설치 및 실행을 위한 필수 구성 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="08457-105">The prerequisites for installing and running Upgrade Advisor are as follows:</span></span>  
  
-   [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] <span data-ttu-id="08457-106">SP1, [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] SP2, Windows 7 또는 [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] R2</span><span class="sxs-lookup"><span data-stu-id="08457-106">SP1, [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] beginning with SP2, Windows 7, or [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] R2.</span></span>  
  
-   <span data-ttu-id="08457-107">Windows Installer 4.5.</span><span class="sxs-lookup"><span data-stu-id="08457-107">Windows Installer 4.5.</span></span> <span data-ttu-id="08457-108">[Windows Installer 웹 사이트](https://www.microsoft.com/download/details.aspx?id=8483)에서 Windows Installer를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08457-108">You can install Windows Installer from the [Windows Installer Web site](https://www.microsoft.com/download/details.aspx?id=8483).</span></span>  
  
-   <span data-ttu-id="08457-109">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)](.NET Framework 4부터 해당).</span><span class="sxs-lookup"><span data-stu-id="08457-109">The [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], beginning with .NET Framework 4.</span></span> <span data-ttu-id="08457-110">는 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 제품 미디어와 [SDK, 재배포 가능 및 Service Pack 다운로드 웹 사이트](https://go.microsoft.com/fwlink/?LinkId=48882)에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08457-110">The [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] is available on the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] product media, and from the [SDK, redistributable, and service pack download Web site](https://go.microsoft.com/fwlink/?LinkId=48882).</span></span>  
  
    -   <span data-ttu-id="08457-111">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 미디어에서 .NET  Framework  4를 설치하려면 디스크 드라이브의 루트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="08457-111">To install the .NET Framework 4 from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] media, locate the root of the disk drive.</span></span> <span data-ttu-id="08457-112">그런 다음 \redist 폴더와 DotNetFrameworks 폴더를 차례로 두 번 클릭하고 dotNetFx40_Full_x86_x64.exe(32비트 및 64비트 운영 체제 모두의 경우)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="08457-112">Then double-click the \redist folder, double-click the DotNetFrameworks folder, and run dotNetFx40_Full_x86_x64.exe (for both 32-bit and 64-bit operating systems).</span></span>  
  
-   <span data-ttu-id="08457-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] Scriptdom은 업그레이드 관리자 설치를 위한 필수 구성 요소 이며 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 업그레이드 관리자 설치를 통해 설치 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="08457-113">The [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom is a prerequisite for installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor, and is not installed by Upgrade Advisor Setup.</span></span> <span data-ttu-id="08457-114">설치 프로그램을 실행 하려면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 기능 팩에서 scriptdom을 다운로드 하 여 설치 해야 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="08457-114">The Setup requires you to download and install the [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08457-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="08457-115">See Also</span></span>  
 [<span data-ttu-id="08457-116">방법: 업그레이드 관리자 설치</span><span class="sxs-lookup"><span data-stu-id="08457-116">How to: Install Upgrade Advisor</span></span>](../../../2014/sql-server/install/how-to-install-upgrade-advisor.md)  
  
  
