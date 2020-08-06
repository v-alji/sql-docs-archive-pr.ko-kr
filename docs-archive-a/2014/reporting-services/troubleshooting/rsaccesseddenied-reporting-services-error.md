---
title: rsAccessedDenied - Reporting Services 오류 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsAccessDenied error
ms.assetid: 2f76b1bf-96a2-4755-b76b-84e933220efc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 194006c2ef6f22b9bc27e9e8cbe1eebd027ed6b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651455"
---
# <a name="rsaccesseddenied---reporting-services-error"></a><span data-ttu-id="37e8c-102">rsAccessedDenied - Reporting Services 오류</span><span class="sxs-lookup"><span data-stu-id="37e8c-102">rsAccessedDenied - Reporting Services Error</span></span>
  <span data-ttu-id="37e8c-103">사용자가 작업을 수행할 수 있는 권한이 없는 경우 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 오류 **rsAccessedDenied** 가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="37e8c-103">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] error **rsAccessedDenied** occurs when a user does not have permission to perform an action.</span></span> <span data-ttu-id="37e8c-104">예를 들어 보고서를 열 수 있는 역할 할당이 없거나 필요한 사용 권한으로 브라우저를 열지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="37e8c-104">For, example, they do not have a role assignment that allows them to open a report or they did not open their browser with the required permissions.</span></span>  
  
||  
|-|  
|<span data-ttu-id="37e8c-105">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기본 모드 &#124; SharePoint 모드</span><span class="sxs-lookup"><span data-stu-id="37e8c-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode &#124; SharePoint mode</span></span>|  
  
-   <span data-ttu-id="37e8c-106">URL을 통해 보고서 서버에 직접 액세스하는 동안 오류가 발생한 경우 예외가 HTTP 401 오류에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="37e8c-106">If the error occurred while accessing the report server directly through a URL, the exception is mapped to an HTTP 401 error.</span></span>  
  
-   <span data-ttu-id="37e8c-107">보고서 관리자 또는 다른 도구를 사용하는 동안 오류가 발생한 경우 오류가 오류 페이지에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="37e8c-107">If the error occurred while using Report Manager or another tool, the error appears in an error page.</span></span>  
  
-   <span data-ttu-id="37e8c-108">예약된 작업, 구독 또는 배달을 하는 동안 오류가 발생한 경우 오류가 보고서 서버 로그 파일에만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="37e8c-108">If the error occurred during a scheduled operation, subscription, or delivery, the error will appear in the report server log file only.</span></span>  
  
## <a name="details"></a><span data-ttu-id="37e8c-109">세부 정보</span><span class="sxs-lookup"><span data-stu-id="37e8c-109">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="37e8c-110">**제품 이름**</span><span class="sxs-lookup"><span data-stu-id="37e8c-110">**Product Name**</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="37e8c-111">**이벤트 ID**</span><span class="sxs-lookup"><span data-stu-id="37e8c-111">**Event ID**</span></span>|<span data-ttu-id="37e8c-112">rsAccessedDenied</span><span class="sxs-lookup"><span data-stu-id="37e8c-112">rsAccessedDenied</span></span>|  
|<span data-ttu-id="37e8c-113">**이벤트 원본**</span><span class="sxs-lookup"><span data-stu-id="37e8c-113">**Event Source**</span></span>|<span data-ttu-id="37e8c-114">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span><span class="sxs-lookup"><span data-stu-id="37e8c-114">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span></span>|  
|<span data-ttu-id="37e8c-115">**구성 요소**</span><span class="sxs-lookup"><span data-stu-id="37e8c-115">**Component**</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="37e8c-116">**메시지 텍스트**</span><span class="sxs-lookup"><span data-stu-id="37e8c-116">**Message Text**</span></span>|<span data-ttu-id="37e8c-117">'mydomain\myAccount' 사용자에게 부여된 권한으로는 이 작업을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="37e8c-117">The permissions granted to user 'mydomain\myAccount' are insufficient for performing this operation.</span></span> <span data-ttu-id="37e8c-118">(rsAccessDenied) (ReportingServicesLibrary)</span><span class="sxs-lookup"><span data-stu-id="37e8c-118">(rsAccessDenied) (ReportingServicesLibrary)</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="37e8c-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="37e8c-119">User Action</span></span>  
 <span data-ttu-id="37e8c-120">보고서 서버 내용 및 작업에 액세스하는 사용 권한은 역할 할당을 통해 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="37e8c-120">Permission to access report server content and operations are granted through role assignments.</span></span> <span data-ttu-id="37e8c-121">새로 설치하는 경우 로컬 관리자만 보고서 서버에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37e8c-121">On a new installation, only local administrators have access to a report server.</span></span> <span data-ttu-id="37e8c-122">다른 사용자에게 액세스 권한을 부여하려면 로컬 관리자는 도메인 사용자나 그룹 계정을 지정하는 역할 할당, 사용자가 수행할 수 있는 태스크를 정의하는 하나 이상의 역할 그리고 범위(일반적으로 홈 폴더나 보고서 서버 폴더 계층의 루트 노드)를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37e8c-122">To grant access to other users, a local administrator must create a role assignment that specifies a domain user or group account, one or more roles that define the tasks the user can perform, and a scope (usually the Home folder or root node of the report server folder hierarchy).</span></span> <span data-ttu-id="37e8c-123">보고서 관리자를 사용하여 역할 할당을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37e8c-123">You can use Report Manager to create the role assignments.</span></span> <span data-ttu-id="37e8c-124">자세한 내용을 보려면 SQL Server 온라인 설명서에서 "역할 할당"을 검색하세요.</span><span class="sxs-lookup"><span data-stu-id="37e8c-124">For more information, search for "Role Assignments" in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="37e8c-125">또한 이 오류는 보고서 서버의 로컬 관리로 인해서도 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="37e8c-125">This error is also caused by local administration of the report server.</span></span> <span data-ttu-id="37e8c-126">자세한 내용은 [로컬 관리에 대해 기본 모드 보고서 서버 구성&#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="37e8c-126">For more information, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37e8c-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="37e8c-127">See Also</span></span>  
 <span data-ttu-id="37e8c-128">[역할 할당](../security/role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="37e8c-128">[Role Assignments](../security/role-assignments.md) </span></span>  
 <span data-ttu-id="37e8c-129">[기본 모드 보고서 서버에 대한 사용 권한 부여](../security/granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="37e8c-129">[Granting Permissions on a Native Mode Report Server](../security/granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 [<span data-ttu-id="37e8c-130">역할 및 권한&#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="37e8c-130">Roles and Permissions &#40;Reporting Services&#41;</span></span>](../security/roles-and-permissions-reporting-services.md)  
  
  
