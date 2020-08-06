---
title: 안전한 개발(Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- development security [Reporting Services]
- security [Reporting Services], development
- security [Reporting Services], strategies
ms.assetid: 12161a6c-b93b-4312-9d27-0c922561eb9b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7ba284b9013c5da6b03cce06ec72deccb045cfad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661533"
---
# <a name="secure-development-reporting-services"></a><span data-ttu-id="e29a6-102">안전한 개발(Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="e29a6-102">Secure Development (Reporting Services)</span></span>
  <span data-ttu-id="e29a6-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]는 엄격한 제약을 받는 관리자 정의 보안 컨텍스트에서 코드를 실행할 수 있는 강력한 보안 시스템을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e29a6-103">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] provides a robust security system that can run code in tightly constrained, administrator-defined security contexts.</span></span> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]<span data-ttu-id="e29a6-104">에서는 코드 액세스 보안 또는 증명 정보 기반 보안이라고 하는 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 보안 시스템을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e29a6-104">uses the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] security system, known as code access security (or evidence-based security).</span></span> <span data-ttu-id="e29a6-105">코드 액세스 보안 하에서는 사용자가 안전하게 리소스에 액세스할 수 있지만 사용자가 실행하는 코드를 신뢰할 수 없는 경우 리소스에 대한 액세스가 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="e29a6-105">Under code access security, a user may be trusted to access a resource, but if the code the user executes is not trusted, access to the resource will be denied.</span></span>  
  
 <span data-ttu-id="e29a6-106">특정 사용자가 아닌 코드 기반의 보안은 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]용으로 개발하는 사용자 지정 어셈블리나 데이터, 전달, 렌더링 및 보안 확장에 대해 보안을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e29a6-106">Security based on code, as opposed to specific users, permits security to be expressed for custom assemblies or data, delivery, rendering, and security extensions that you develop for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="e29a6-107">확장 코드는 여러 명의 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 사용자가 실행할 수 있으며 전체 사용자 수는 개발 시에 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e29a6-107">Your extension code may be executed by any number of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] users, all of whom are unknown at development time.</span></span> <span data-ttu-id="e29a6-108">개발하는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 사용자 지정 어셈블리나 확장에는 특정 보안 정책이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e29a6-108">The custom assemblies or extensions that you develop require specific security policies in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="e29a6-109">이러한 보안 정책은 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]의 유형으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e29a6-109">These security policies are represented as types in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="e29a6-110">코드 액세스 보안에 대한 자세한 내용은 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 설명서에서 "코드 액세스 보안"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e29a6-110">For a more information about code access security, see "Code Access Security" in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] documentation.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e29a6-111">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="e29a6-111">In This Section</span></span>  
 [<span data-ttu-id="e29a6-112">Reporting Services의 코드 액세스 보안</span><span class="sxs-lookup"><span data-stu-id="e29a6-112">Code Access Security in Reporting Services</span></span>](code-access-security-in-reporting-services.md)  
 <span data-ttu-id="e29a6-113">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 사용자 지정 어셈블리 및 확장 프로그램에 대해 코드 액세스 보안 및 정책 구성을 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="e29a6-113">Introduces code access security and policy configuration for custom assemblies and extensions in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="e29a6-114">보안 정책 이해</span><span class="sxs-lookup"><span data-stu-id="e29a6-114">Understanding Security Policies</span></span>](understanding-security-policies.md)  
 <span data-ttu-id="e29a6-115">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 다양한 어셈블리 유형 및 코드 액세스 보안이 코드 사용 권한에 미치는 영향에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e29a6-115">Describes the various assembly types in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] and how code access security affects code permissions.</span></span>  
  
 [<span data-ttu-id="e29a6-116">Reporting Services 보안 정책 파일 사용</span><span class="sxs-lookup"><span data-stu-id="e29a6-116">Using Reporting Services Security Policy Files</span></span>](using-reporting-services-security-policy-files.md)  
 <span data-ttu-id="e29a6-117">여러 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 구성 요소 및 해당 정책 구성 파일에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e29a6-117">Describes the different [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] components and the corresponding policy configuration files.</span></span>  
  
  
