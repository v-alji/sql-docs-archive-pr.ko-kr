---
title: SQL Server 2005 보고서 서버 웹 서비스 그룹이 검색 됨 (업그레이드 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- deployment [Reporting Services]
ms.assetid: 699d24eb-7756-4b41-9294-ef1a94b2f267
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 70be2b9c4e7abd55daaa752830a73cbe6e222659
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742795"
---
# <a name="sql-server-2005-report-server-web-service-group-detected-upgrade-advisor"></a><span data-ttu-id="682e5-102">SQL Server 2005 보고서 서버 웹 서비스 그룹이 검색됨(업그레이드 관리자)</span><span class="sxs-lookup"><span data-stu-id="682e5-102">SQL Server 2005 Report Server Web Service group detected (Upgrade Advisor)</span></span>
  <span data-ttu-id="682e5-103">업그레이드 관리자가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 보고서 서버 웹 서비스 그룹과 연결 되어 있음을 발견 했습니다.</span><span class="sxs-lookup"><span data-stu-id="682e5-103">Upgrade Advisor detected that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance is associated with a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Report Server Web service group.</span></span>  
  
||  
|-|  
|<span data-ttu-id="682e5-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]기본 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="682e5-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="682e5-105">구성 요소</span><span class="sxs-lookup"><span data-stu-id="682e5-105">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="682e5-106">설명</span><span class="sxs-lookup"><span data-stu-id="682e5-106">Description</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="682e5-107">을 사용 하지 않습니다. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 보고서 서버 웹 서비스 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="682e5-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] does not use the [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Report Server Web service group.</span></span> <span data-ttu-id="682e5-108">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드할 때 이러한 서비스 그룹은 삭제되며 이 그룹 또는 그룹에 속하는 사용자에 대한 사용자 지정 ACL(Access Control 목록)은 업그레이드 중에 보존되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="682e5-108">When you upgrade from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], this service group is deleted and custom Access Control Lists (ACLs) for this group or users who belong to the group are not retained during the upgrade.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="682e5-109">수정 동작</span><span class="sxs-lookup"><span data-stu-id="682e5-109">Corrective Action</span></span>  
 <span data-ttu-id="682e5-110">업그레이드를 시작하기 전에 사용자 지정 ACL이나 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 보고서 서버 웹 서비스 그룹에 속한 사용자를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="682e5-110">Before you upgrade, back up any custom ACLs or users who belong to the [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Report Server Web service group.</span></span> <span data-ttu-id="682e5-111">이렇게 하려면 sp2 이상에서 **Icacls.exe** 명령줄 도구를 사용 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 하거나 sp2 이전 버전의 Windows 운영 체제에서 Cacls.exe 명령줄 도구를 사용할 수 있습니다 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="682e5-111">To do this, you can use the **Icacls.exe** command-line tool in [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] SP2 and later or the Cacls.exe command-line tool in Windows operating systems prior to [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] SP2.</span></span> <span data-ttu-id="682e5-112">이들 도구를 사용하기 위한 구문에 대한 자세한 내용은 Windows 제품 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="682e5-112">For more information about the syntax for these tools, see the Windows product documentation.</span></span> <span data-ttu-id="682e5-113">설치가 성공적으로 완료되면 사용자 지정 ACL이나 사용자를 보고서 서버 인스턴스에 대한 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 보고서 서버 Windows 그룹에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="682e5-113">After setup successfully completes, apply the custom ACLs or users to the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Report Server Windows group for your report server instance.</span></span> <span data-ttu-id="682e5-114">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]보고서 서버 Windows 그룹은 SQLServerReportServerUser $ 형식으로 사용 \<*computer_name*> $ \<*instance_name*> 됩니다.</span><span class="sxs-lookup"><span data-stu-id="682e5-114">The [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Report Server Windows group takes the form of SQLServerReportServerUser$\<*computer_name*>$\<*instance_name*>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="682e5-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="682e5-115">See Also</span></span>  
 [<span data-ttu-id="682e5-116">업그레이드 관리자를 &#40;업그레이드 문제를 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="682e5-116">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
