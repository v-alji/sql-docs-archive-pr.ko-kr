---
title: MSSQLSERVER_15404 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15404 (Database Engine error)
ms.assetid: 69677f02-bc81-4e4a-99b8-5c1bd1de36df
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: beb854c866256728574e06f8c9efb50fb354e15a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653944"
---
# <a name="mssqlserver_15404"></a><span data-ttu-id="ca422-102">MSSQLSERVER_15404</span><span class="sxs-lookup"><span data-stu-id="ca422-102">MSSQLSERVER_15404</span></span>
    
## <a name="details"></a><span data-ttu-id="ca422-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="ca422-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ca422-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="ca422-104">Product Name</span></span>|<span data-ttu-id="ca422-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ca422-105">SQL Server</span></span>|  
|<span data-ttu-id="ca422-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="ca422-106">Event ID</span></span>|<span data-ttu-id="ca422-107">15404</span><span class="sxs-lookup"><span data-stu-id="ca422-107">15404</span></span>|  
|<span data-ttu-id="ca422-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="ca422-108">Event Source</span></span>|<span data-ttu-id="ca422-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ca422-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ca422-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="ca422-110">Component</span></span>|<span data-ttu-id="ca422-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ca422-111">SQLEngine</span></span>|  
|<span data-ttu-id="ca422-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="ca422-112">Symbolic Name</span></span>|<span data-ttu-id="ca422-113">SEC_NTGRP_ERROR</span><span class="sxs-lookup"><span data-stu-id="ca422-113">SEC_NTGRP_ERROR</span></span>|  
|<span data-ttu-id="ca422-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="ca422-114">Message Text</span></span>|<span data-ttu-id="ca422-115">Windows NT 그룹/사용자 '*user*'에 대한 정보를 가져올 수 없습니다. 오류 코드 *code*.</span><span class="sxs-lookup"><span data-stu-id="ca422-115">Could not obtain information about Windows NT group/user '*user*', error code *code*.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ca422-116">설명</span><span class="sxs-lookup"><span data-stu-id="ca422-116">Explanation</span></span>  
 <span data-ttu-id="ca422-117">15404는 잘못된 보안 주체가 지정된 경우 인증에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca422-117">15404 is used in authentication when an invalid principal is specified.</span></span> <span data-ttu-id="ca422-118">또는 Windows 계정의 가장은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 계정과 Windows 계정의 도메인 간에 완전 신뢰 관계가 없기 때문에 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="ca422-118">Or, impersonation of a Windows account fails because there is no full trust relationship between the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account and the domain of the Windows account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ca422-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="ca422-119">User Action</span></span>  
 <span data-ttu-id="ca422-120">Windows 보안 주체가 존재하고 철자가 잘못되지 않았는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ca422-120">Check that the Windows principal exists and is not misspelled.</span></span>  
  
 <span data-ttu-id="ca422-121">이 오류가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 계정과 Windows 계정의 도메인 간에 완전 신뢰 관계가 없기 때문에 발생하는 경우 다음 작업 중 하나로 오류를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca422-121">If this error is the result of a lack of a full trust relationship between the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account and the domain of the Windows account, one of the following actions can resolve the error:</span></span>  
  
-   <span data-ttu-id="ca422-122">Windows 사용자와 동일한 도메인에 있는 계정을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ca422-122">Use an account from the same domain as the Windows user for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
-   <span data-ttu-id="ca422-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 네트워크 서비스 또는 로컬 시스템과 같은 시스템 계정을 사용하는 경우 해당 컴퓨터가 Windows 사용자가 포함된 도메인에서 트러스트되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca422-123">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is using a machine account such as Network Service or Local System, the machine must be trusted by the domain containing the Windows User.</span></span>  
  
-   <span data-ttu-id="ca422-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ca422-124">Use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
  
