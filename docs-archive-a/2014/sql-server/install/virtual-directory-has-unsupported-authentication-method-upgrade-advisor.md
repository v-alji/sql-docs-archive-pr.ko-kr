---
title: 가상 디렉터리에 지원 되지 않는 인증 방법 있음 (업그레이드 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- virtual directories [Reporting Services]
ms.assetid: 216eca6f-9a66-42e1-aa54-dcf99cec9f7d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 67b1c027b8ed020f65fdea7c093f6d5454f02c5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650403"
---
# <a name="virtual-directory-has-unsupported-authentication-method-upgrade-advisor"></a><span data-ttu-id="ade44-102">가상 디렉터리에 지원되지 않는 인증 방법이 있음(업그레이드 관리자)</span><span class="sxs-lookup"><span data-stu-id="ade44-102">Virtual directory has unsupported authentication method (Upgrade Advisor)</span></span>
  <span data-ttu-id="ade44-103">업그레이드 관리자가 보고서 관리자 또는 보고서 서버 가상 디렉터리에서 지원되지 않는 인증 방법을 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="ade44-103">Upgrade Advisor detected an unsupported authentication method on the Report Manager or report server virtual directory.</span></span> <span data-ttu-id="ade44-104">업그레이드를 지원하지 않는 인증 방법에는 익명, 다이제스트 및 .NET Passport가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ade44-104">Authentication methods that are not supported by upgrade include Anonymous, Digest, and .NET Passport.</span></span>  
  
||  
|-|  
|<span data-ttu-id="ade44-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]기본 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="ade44-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="ade44-106">구성 요소</span><span class="sxs-lookup"><span data-stu-id="ade44-106">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="ade44-107">Description</span><span class="sxs-lookup"><span data-stu-id="ade44-107">Description</span></span>  
 <span data-ttu-id="ade44-108">설치 프로그램은 다음 인증 방법 중 하나를 사용하는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치를 업그레이드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ade44-108">Setup cannot upgrade a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation that uses one of the following authentication methods</span></span>  
  
-   <span data-ttu-id="ade44-109">익명</span><span class="sxs-lookup"><span data-stu-id="ade44-109">Anonymous</span></span>  
  
-   <span data-ttu-id="ade44-110">다이제스트</span><span class="sxs-lookup"><span data-stu-id="ade44-110">Digest</span></span>  
  
-   <span data-ttu-id="ade44-111">.NET Passport</span><span class="sxs-lookup"><span data-stu-id="ade44-111">.NET Passport</span></span>  
  
 <span data-ttu-id="ade44-112">계속하려면 인터넷 정보 서비스(IIS)의 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 가상 디렉터리에 지정된 인증 방법을 수정하거나 설치를 마이그레이션하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ade44-112">To continue, you can either modify the Authentication method that is specified for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] virtual directories in Internet Information Services (IIS), or you can migrate your installation.</span></span> <span data-ttu-id="ade44-113">설치를 마이그레이션하는 방법은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ade44-113">For more information about migrating your installation, see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="ade44-114">수정 동작</span><span class="sxs-lookup"><span data-stu-id="ade44-114">Corrective Action</span></span>  
 <span data-ttu-id="ade44-115">업그레이드를 계속하려면 ReportServer 및 Reports 가상 디렉터리에 대한 IIS의 인증 방법을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="ade44-115">To continue with upgrade, modify the Authentication method in IIS for the ReportServer and Reports virtual directories.</span></span> <span data-ttu-id="ade44-116">인증 방법 수정은 IIS 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ade44-116">For more information about modifying Authentication methods in IIS, see the IIS documentation.</span></span> <span data-ttu-id="ade44-117">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 가상 디렉터리의 인증 방법을 수정한 후에는 업그레이드 관리자를 다시 실행하여 다른 업그레이드 문제가 없는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ade44-117">After you modify the Authentication method for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] virtual directories, re-run Upgrade Advisor to confirm that there are no other upgrade issues.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ade44-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ade44-118">See Also</span></span>  
 [<span data-ttu-id="ade44-119">업그레이드 관리자를 &#40;업그레이드 문제를 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ade44-119">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
