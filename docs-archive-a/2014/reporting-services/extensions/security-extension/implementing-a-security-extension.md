---
title: 보안 확장 프로그램 구현 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], extensions
- forms-based authentication [Reporting Services]
- custom authentication [Reporting Services]
- extensions [Reporting Services], custom security
ms.assetid: d2327e7c-0d48-49e3-bcd9-3bba4e67a68b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e5cf1fa6ce0e0a02a52e6a27f693c152d1f97152
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651508"
---
# <a name="implementing-a-security-extension"></a><span data-ttu-id="916f4-102">보안 확장 프로그램 구현</span><span class="sxs-lookup"><span data-stu-id="916f4-102">Implementing a Security Extension</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="916f4-103">Windows 인증은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에서 보고서 보안을 위한 주 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="916f4-103">Windows Authentication is the primary system for securing reports in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="916f4-104">하지만 소속 조직에서 사용자 지정 보안을 충족하기 위해 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 보안 시스템을 확장해야 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="916f4-104">In certain cases, however, you may need to extend the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] security system to accommodate custom security in your enterprise.</span></span> <span data-ttu-id="916f4-105">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] API로 제공되는 개발 플랫폼을 사용하여 이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="916f4-105">You can do this using the development platform provided by the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] API.</span></span> <span data-ttu-id="916f4-106">이 섹션에서는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 보안 확장 프로그램 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="916f4-106">This section will present an overview of security extensions in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="916f4-107">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 보안 확장 프로그램을 구현, 배포, 제거하는 방법은 [SQL Server Reporting Services 제품 예제](https://go.microsoft.com/fwlink/?LinkId=177889)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="916f4-107">For complete details about implementing, deploying, and removing a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] security extension, please see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="916f4-108">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="916f4-108">In This Section</span></span>  
 [<span data-ttu-id="916f4-109">보안 확장 프로그램 개요</span><span class="sxs-lookup"><span data-stu-id="916f4-109">Security Extensions Overview</span></span>](security-extensions-overview.md)  
 <span data-ttu-id="916f4-110">Reporting Services 보안 확장 프로그램의 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="916f4-110">Provides an overview of Reporting Services Security Extensions.</span></span>  
  
 [<span data-ttu-id="916f4-111">Reporting Services의 인증</span><span class="sxs-lookup"><span data-stu-id="916f4-111">Authentication in Reporting Services</span></span>](authentication-in-reporting-services.md)  
 <span data-ttu-id="916f4-112">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 인증에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="916f4-112">Discusses authentication in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="916f4-113">Reporting Services의 권한 부여</span><span class="sxs-lookup"><span data-stu-id="916f4-113">Authorization in Reporting Services</span></span>](authorization-in-reporting-services.md)  
 <span data-ttu-id="916f4-114">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 권한 부여에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="916f4-114">Covers authorization in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="916f4-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="916f4-115">See Also</span></span>  
 <xref:Microsoft.ReportingServices.Interfaces>   
 <span data-ttu-id="916f4-116">[Reporting Services 확장 프로그램](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="916f4-116">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 [<span data-ttu-id="916f4-117">Reporting Services 확장 라이브러리</span><span class="sxs-lookup"><span data-stu-id="916f4-117">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
