---
title: 보안 속성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- security [Analysis Services], properties
- SecurityPackageList property
- BuiltinAdminsAreServerAdmins property
- DisableClientImpersonation property
- ErrorMessageMode property
- RequiredProtectionLevel property
- ServiceAccountIsServerAdmin property
- RequireClientAuthentication property
ms.assetid: 2fc7fe10-0cbb-49ac-aa8c-8ec3f7a7705f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 20133554835803908a340c5369eb66e86b119d72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650300"
---
# <a name="security-properties"></a><span data-ttu-id="31708-102">보안 속성</span><span class="sxs-lookup"><span data-stu-id="31708-102">Security Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="31708-103">에서는 다음 표에 나열된 보안 서버 속성을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="31708-103">supports the security server properties listed in the following table.</span></span> <span data-ttu-id="31708-104">추가 서버 속성 및 해당 속성 설정 방법은 [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31708-104">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="31708-105">**적용 대상:** 다차원 및 테이블 형식 서버 모드</span><span class="sxs-lookup"><span data-stu-id="31708-105">**Applies to:** Multidimensional and Tabular server mode</span></span>  
  
## <a name="properties"></a><span data-ttu-id="31708-106">속성</span><span class="sxs-lookup"><span data-stu-id="31708-106">Properties</span></span>  
 `RequireClientAuthentication`  
 <span data-ttu-id="31708-107">클라이언트 인증이 필요한지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="31708-107">A Boolean property that indicates whether client authentication is required.</span></span>  
  
 <span data-ttu-id="31708-108">이 속성의 기본값은 True이며, 이 경우 클라이언트 인증이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="31708-108">The default value for this property is True, which indicates that client authentication is required.</span></span>  
  
 `SecurityPackageList`  
 <span data-ttu-id="31708-109">클라이언트 인증을 위해 서버에서 사용하는 쉼표로 구분된 SSPI 패키지 목록을 포함하는 문자열 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="31708-109">A string property that contains a comma-separated list of SSPI packages used by server for client authentication.</span></span>  
  
 `DisableClientImpersonation`  
 <span data-ttu-id="31708-110">클라이언트 가장을 해제할지 여부(예: 저장 프로시저에서)를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="31708-110">A Boolean property that indicates whether client impersonation (for example, from stored procedures) is disabled.</span></span>  
  
 <span data-ttu-id="31708-111">이 속성의 기본값은 False이며, 이 경우 클라이언트 가장이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="31708-111">The default value for this property is False, which indicates that client impersonation is enabled.</span></span>  
  
 `BuiltinAdminsAreServerAdmins`  
 <span data-ttu-id="31708-112">로컬 시스템 관리자 그룹의 멤버가 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 관리자인지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="31708-112">A Boolean property that indicates whether members of the local machine administrators group are [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrators.</span></span>  
  
 `ServiceAccountIsServerAdmin`  
 <span data-ttu-id="31708-113">서비스 계정이 서버 관리자인지 여부를 나타내는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="31708-113">A Boolean property that indicates whether the service account is a server administrator.</span></span>  
  
 <span data-ttu-id="31708-114">이 속성의 기본값은 True이며, 이 경우 서비스 계정이 서버 관리자입니다.</span><span class="sxs-lookup"><span data-stu-id="31708-114">The default value for this property is True, which indicates that the service account is a server administrator.</span></span>  
  
 `ErrorMessageMode`  
 <span data-ttu-id="31708-115">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31708-115">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataProtection\ RequiredProtectionLevel`  
 <span data-ttu-id="31708-116">모든 클라이언트 요청에 대해 필요한 보호 수준을 정의하는 부호 있는 32비트 정수 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="31708-116">A signed 32-bit integer property that defines the required protection level for all client requests.</span></span> <span data-ttu-id="31708-117">이 속성은 다음 표에 나열된 값 중 하나를 취합니다.</span><span class="sxs-lookup"><span data-stu-id="31708-117">This property has one of the values listed in the following table.</span></span>  
  
|<span data-ttu-id="31708-118">값</span><span class="sxs-lookup"><span data-stu-id="31708-118">Value</span></span>|<span data-ttu-id="31708-119">Description</span><span class="sxs-lookup"><span data-stu-id="31708-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="31708-120">*0*</span><span class="sxs-lookup"><span data-stu-id="31708-120">*0*</span></span>|<span data-ttu-id="31708-121">없음. 일반 텍스트가 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="31708-121">None, clear text allowed.</span></span>|  
|<span data-ttu-id="31708-122">*1*</span><span class="sxs-lookup"><span data-stu-id="31708-122">*1*</span></span>|<span data-ttu-id="31708-123">(기본값)암호화 필요. 일반 텍스트 로깅은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="31708-123">(Default) Encryption required, no clear-text logging.</span></span>|  
|<span data-ttu-id="31708-124">*2*</span><span class="sxs-lookup"><span data-stu-id="31708-124">*2*</span></span>|<span data-ttu-id="31708-125">일반 텍스트 요청이 허용되지만 반드시 서명이 있어야 합니다(암호화보다 약한 보호 수준).</span><span class="sxs-lookup"><span data-stu-id="31708-125">Clear-text requests allowed but only with signatures (weaker protection than encryption).</span></span>|  
  
 `AdministrativeDataProtection\ RequiredProtectionLevel`  
 <span data-ttu-id="31708-126">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31708-126">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31708-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="31708-127">See Also</span></span>  
 <span data-ttu-id="31708-128">[Analysis Services에서 서버 속성 구성](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="31708-128">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="31708-129">Analysis Services 인스턴스의 서버 모드 확인</span><span class="sxs-lookup"><span data-stu-id="31708-129">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
