---
title: SQL Server 관리 도구 | 설치 Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Tools
ms.assetid: af68d59a-a04d-4f23-9967-ad4ee2e63381
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 39a7ed6d859c6bbbb63e938cc7127958082737dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653162"
---
# <a name="install-sql-server-management-tools"></a><span data-ttu-id="ea8a3-102">SQL Server 관리 도구 설치</span><span class="sxs-lookup"><span data-stu-id="ea8a3-102">Install SQL Server Management Tools</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ea8a3-103">관리 도구에는 다음과 같은 구성 요소가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea8a3-103">Management tools include the following components:</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ea8a3-104">데이터베이스 튜닝 관리자</span><span class="sxs-lookup"><span data-stu-id="ea8a3-104">Database Tuning Advisor</span></span>  
  
-   <span data-ttu-id="ea8a3-105">sqlcmd.exe 및 osql.exe와 같은 명령 프롬프트 도구</span><span class="sxs-lookup"><span data-stu-id="ea8a3-105">Command prompt tools, such as sqlcmd.exe and osql.exe.</span></span>  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="ea8a3-106">추가 기능 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea8a3-106">add-ins to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]</span></span>  
  
 <span data-ttu-id="ea8a3-107">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 설치하는 동안 사용할 수 있는 별도의 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="ea8a3-107">Note that [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] is a separate option during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span>  
  
 <span data-ttu-id="ea8a3-108">컴퓨터에 설치된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]또는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인스턴스의 수에 관계없이 하나의 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 관리 도구 복사본만 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea8a3-108">Regardless of how many instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], or [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] are installed on a computer, only one copy of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Management Tools will be installed.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="ea8a3-109">관리 도구는 이전 버전의 관리 도구와 동일한 컴퓨터에서 함께 실행할 수 있습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ea8a3-109">Management Tools can run side-by-side on the same computer with earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Tools.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea8a3-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ea8a3-110">See Also</span></span>  
 <span data-ttu-id="ea8a3-111">[SQL Server 2014 버전에서 지 원하는 기능](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="ea8a3-111">[Features Supported by the Editions of SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span></span>  
 <span data-ttu-id="ea8a3-112">[SQL Server 2014의 버전 및 구성 요소](../editions-and-components-of-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="ea8a3-112">[Editions and Components of SQL Server 2014](../editions-and-components-of-sql-server-2016.md) </span></span>  
 <span data-ttu-id="ea8a3-113">[설치 마법사 &#40;설치 프로그램에서 SQL Server 2014을 설치&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) </span><span class="sxs-lookup"><span data-stu-id="ea8a3-113">[Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) </span></span>  
 [<span data-ttu-id="ea8a3-114">설치 마법사 &#40;사용 하 여 SQL Server 2014로 업그레이드&#41;</span><span class="sxs-lookup"><span data-stu-id="ea8a3-114">Upgrade to SQL Server 2014 Using the Installation Wizard &#40;Setup&#41;</span></span>](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  
