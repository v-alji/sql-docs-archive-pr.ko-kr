---
title: MSSQLSERVER에 대한 프로토콜 속성(인증서 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.computermgr.cert.general.f1
helpviewer_keywords:
- MSSQLSERVER property protocols
ms.assetid: 776addd6-25f3-4875-9a71-064035787090
author: stevestein
ms.author: sstein
ms.openlocfilehash: 020d33eba7621f877f8622ca89dbd26a071f16a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737299"
---
# <a name="protocols-for-mssqlserver-properties-certificate-tab"></a><span data-ttu-id="c9a18-102">MSSQLSERVER에 대한 프로토콜 속성(인증서 탭)</span><span class="sxs-lookup"><span data-stu-id="c9a18-102">Protocols for MSSQLSERVER Properties (Certificate Tab)</span></span>
  <span data-ttu-id="c9a18-103">**MSSQLSERVER에 대한 프로토콜 속성** 대화 상자의 **인증서** 탭을 사용하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 사용할 인증서를 선택하거나 인증서 속성을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a18-103">Use the **Certificate** tab on the **Protocols for MSSQLSERVER Properties** dialog box to select a certificate for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or to view the properties of a certificate.</span></span> <span data-ttu-id="c9a18-104">인증서를 선택하기 전에는 모든 필드가 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a18-104">All fields are blank until a certificate is selected.</span></span>  
  
 <span data-ttu-id="c9a18-105">인증서는 사용자 컴퓨터에 로컬로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9a18-105">Certificates are stored locally for the users on the computer.</span></span> <span data-ttu-id="c9a18-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 사용할 인증서를 로드하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스와 동일한 사용자 계정으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a18-106">To load a certificate for use by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must be running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager under the same user account as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
## <a name="page-header"></a><span data-ttu-id="c9a18-107">페이지 머리글</span><span class="sxs-lookup"><span data-stu-id="c9a18-107">Page Header</span></span>  
 <span data-ttu-id="c9a18-108">**보기**</span><span class="sxs-lookup"><span data-stu-id="c9a18-108">**View**</span></span>  
 <span data-ttu-id="c9a18-109">인증서의 추가 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a18-109">Provides access to additional details on the certificate.</span></span> <span data-ttu-id="c9a18-110">**인증서** 상자에서 인증서를 선택하기 전까지는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a18-110">Not available until a certificate is selected in the **Certificate** box.</span></span> <span data-ttu-id="c9a18-111">인증서 정보에 대한 자세한 내용은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c9a18-111">For additional information on certificate details, see your [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows documentation.</span></span>  
  
 <span data-ttu-id="c9a18-112">**지우기**</span><span class="sxs-lookup"><span data-stu-id="c9a18-112">**Clear**</span></span>  
 <span data-ttu-id="c9a18-113">선택한 항목을 **인증서** 상자에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a18-113">Removes the selection from the **Certificate** box.</span></span>  
  
 <span data-ttu-id="c9a18-114">**MSSQLSERVER에 대한 프로토콜 속성**</span><span class="sxs-lookup"><span data-stu-id="c9a18-114">**Certificate**</span></span>  
 <span data-ttu-id="c9a18-115">보안 공급자가 결정하는 인증서 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c9a18-115">Name of certificate as determined by security provider.</span></span> <span data-ttu-id="c9a18-116">속성 표에서 세부 정보를 보려면 인증서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a18-116">Select a certificate to see the details in the properties grid.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c9a18-117">옵션</span><span class="sxs-lookup"><span data-stu-id="c9a18-117">Options</span></span>  
 <span data-ttu-id="c9a18-118">만료 날짜</span><span class="sxs-lookup"><span data-stu-id="c9a18-118">Expiration Date</span></span>  
 <span data-ttu-id="c9a18-119">인증서 유효 기간의 마지막 날짜입니다.</span><span class="sxs-lookup"><span data-stu-id="c9a18-119">The final date for the period in which the certificate is valid.</span></span>  
  
 <span data-ttu-id="c9a18-120">친숙한 이름</span><span class="sxs-lookup"><span data-stu-id="c9a18-120">Friendly Name</span></span>  
 <span data-ttu-id="c9a18-121">인증서가 발급된 개인 또는 인증 기관의 이름 또는 일반 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c9a18-121">A friendly or common name for the individual or certification authority to whom the certificate is issued.</span></span>  
  
 <span data-ttu-id="c9a18-122">발급자</span><span class="sxs-lookup"><span data-stu-id="c9a18-122">Issued By</span></span>  
 <span data-ttu-id="c9a18-123">인증서를 발급한 인증 기관에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="c9a18-123">Information regarding the certification authority that issued the certificate.</span></span>  
  
 <span data-ttu-id="c9a18-124">발급 대상</span><span class="sxs-lookup"><span data-stu-id="c9a18-124">Issued To</span></span>  
 <span data-ttu-id="c9a18-125">인증서를 받는 사람에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="c9a18-125">Information regarding the recipient of the certificate.</span></span>  
  
  
