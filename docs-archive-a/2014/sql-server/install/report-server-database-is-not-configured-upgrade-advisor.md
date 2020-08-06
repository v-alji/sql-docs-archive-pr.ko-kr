---
title: 보고서 서버 데이터베이스가 구성 되지 않음 (업그레이드 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: b964300c-b220-4244-9fa6-c0c6a57760f6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 072e689da3f43222396f071e607214a2ec494749
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639251"
---
# <a name="report-server-database-is-not-configured-upgrade-advisor"></a><span data-ttu-id="0fc39-102">보고서 서버 데이터베이스가 올바르게 구성되지 않음(업그레이드 관리자)</span><span class="sxs-lookup"><span data-stu-id="0fc39-102">Report server database is not configured (Upgrade Advisor)</span></span>
  <span data-ttu-id="0fc39-103">보고서 서버 구성이 완료되지 않아 업그레이드가 차단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0fc39-103">Upgrade is blocked due to an incomplete report server configuration.</span></span> <span data-ttu-id="0fc39-104">보고서 서버 데이터베이스가 구성되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0fc39-104">The report server database is not configured.</span></span>  
  
||  
|-|  
|<span data-ttu-id="0fc39-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기본 모드 &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드.</span><span class="sxs-lookup"><span data-stu-id="0fc39-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="0fc39-106">구성 요소</span><span class="sxs-lookup"><span data-stu-id="0fc39-106">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="0fc39-107">Description</span><span class="sxs-lookup"><span data-stu-id="0fc39-107">Description</span></span>  
 <span data-ttu-id="0fc39-108">설치 프로그램은 완전하게 구성된 보고서 서버 인스턴스만 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fc39-108">Setup can only upgrade a fully configured report server instance.</span></span> <span data-ttu-id="0fc39-109">계속하려면 보고서 서버 데이터베이스를 구성하거나 Microsoft Windows **제어판** 을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치에서 보고서 서버 기능을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="0fc39-109">To continue, you must either configure the report server database, or use Microsoft Windows **Control Panel** to remove the report server feature from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span> <span data-ttu-id="0fc39-110">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]를 제거한 후에는 다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소를 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fc39-110">After you remove [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can upgrade other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="0fc39-111">수정 동작</span><span class="sxs-lookup"><span data-stu-id="0fc39-111">Corrective Action</span></span>  
 <span data-ttu-id="0fc39-112">보고서 서버 데이터베이스를 구성하지 않은 경우 보고서 서버가 작동하지 않으므로 업그레이드하기 전에 보고서 서버를 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fc39-112">If you did not configure the report server database, the report server is not operational and should be removed prior to upgrade.</span></span>  
  
 <span data-ttu-id="0fc39-113">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 제거에 대한 자세한 내용은 [Reporting Services 2012 제거](https://technet.microsoft.com/library/hh479745.aspx\(v=sql.11\))를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0fc39-113">For additional information on uninstalling [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , see [Uninstall Reporting Services 2012](https://technet.microsoft.com/library/hh479745.aspx\(v=sql.11\)).</span></span> <span data-ttu-id="0fc39-114">이 항목에서는 특정 버전을 제거하는 방법에 대해 설명하며, 절차는 이전 버전과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="0fc39-114">the topic describes how to uninstall a specific version and the procedures are similar for previous versions as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fc39-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0fc39-115">See Also</span></span>  
 [<span data-ttu-id="0fc39-116">업그레이드 관리자를 &#40;업그레이드 문제를 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0fc39-116">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
