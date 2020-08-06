---
title: Reporting Services 보안 및 보호 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- security [Reporting Services]
- Reporting Services, security
ms.assetid: 270075c5-bf12-4467-a775-abbda3d954a5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0f8c7a4186c5236260fb27d8de107ce8c97bd363
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660330"
---
# <a name="reporting-services-security-and-protection"></a><span data-ttu-id="005fe-102">Reporting Services 보안 및 보호</span><span class="sxs-lookup"><span data-stu-id="005fe-102">Reporting Services Security and Protection</span></span>
  <span data-ttu-id="005fe-103">이 섹션에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 보안 기능에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="005fe-103">You can use information in this section to learn about the security features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="005fe-104">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 지원되는 권한 부여 모델 및 인증 공급자에 대해서도 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="005fe-104">This section also explains the authorization models and authentication providers supported in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
## <a name="extended-protection-for-authentication"></a><span data-ttu-id="005fe-105">인증에 대한 확장된 보호</span><span class="sxs-lookup"><span data-stu-id="005fe-105">Extended Protection for Authentication</span></span>  
 <span data-ttu-id="005fe-106">[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]부터는 인증에 대한 확장된 보호가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="005fe-106">Beginning with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], support for Extended Protection for Authentication is available.</span></span> <span data-ttu-id="005fe-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기능은 채널 바인딩 및 서비스 바인딩을 사용해 인증 보호를 향상시킬 수 있도록 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="005fe-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] feature supports the use of channel binding and service binding to enhance protection of authentication.</span></span> <span data-ttu-id="005fe-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기능은 확장된 보호를 지원하는 운영 체제에서 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="005fe-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features need to be used with an operating system that supports Extended Protection.</span></span> <span data-ttu-id="005fe-109">자세한 내용은 [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="005fe-109">For more information, see [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md).</span></span>  
  
## <a name="authentication-and-authorization"></a><span data-ttu-id="005fe-110">인증 및 권한 부여</span><span class="sxs-lookup"><span data-stu-id="005fe-110">Authentication and Authorization</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="005fe-111">는 보고서 서버에 대해 사용자 및 클라이언트 애플리케이션에 부여할 다양한 인증 유형을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="005fe-111">provides different authentication types for users and client applications to authenticate with the report server.</span></span> <span data-ttu-id="005fe-112">보고서 서버에 맞는 인증 유형을 사용하면 조직에서 요구되는 적합한 수준의 보안을 확보할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="005fe-112">Using the right authentication type for your report server enables your organization to achieve the appropriate level of security required by your organization.</span></span> <span data-ttu-id="005fe-113">자세한 내용은 [Authentication with the Report Server](authentication-with-the-report-server.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="005fe-113">For more information, see [Authentication with the Report Server](authentication-with-the-report-server.md).</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="005fe-114">는 또한 역할 및 권한을 이용하여 보고서 서버 카탈로그 내용에 대한 사용자 액세스 권한을 제어합니다. 즉, 누가 어떤 내용에 액세스할 수 있는지, 액세스하는 방법 등을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="005fe-114">also employs roles and permissions to control user access to content in the report server catalog (in other words, who can access what, and how s/he can access it).</span></span> <span data-ttu-id="005fe-115">자세한 내용은 [역할 및 사용 권한&#40;Reporting Services&#41;](roles-and-permissions-reporting-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="005fe-115">For more information, see [Roles and Permissions &#40;Reporting Services&#41;](roles-and-permissions-reporting-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="005fe-116">관련 작업</span><span class="sxs-lookup"><span data-stu-id="005fe-116">Related Tasks</span></span>  
  
|<span data-ttu-id="005fe-117">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="005fe-117">Task Descriptions</span></span>|<span data-ttu-id="005fe-118">링크</span><span class="sxs-lookup"><span data-stu-id="005fe-118">Links</span></span>|  
|-----------------------|-----------|  
|<span data-ttu-id="005fe-119">SSL(Secure Socket Layer)를 구성하여 클라이언트와 보고서 서버의 연결에 보안을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="005fe-119">Configure the Secure Socket Layer (SSL) to secure client connections to the report server.</span></span>|[<span data-ttu-id="005fe-120">기본 모드 보고서 서버에서 SSL 연결 구성</span><span class="sxs-lookup"><span data-stu-id="005fe-120">Configure SSL Connections on a Native Mode Report Server</span></span>](configure-ssl-connections-on-a-native-mode-report-server.md)|  
  
  
