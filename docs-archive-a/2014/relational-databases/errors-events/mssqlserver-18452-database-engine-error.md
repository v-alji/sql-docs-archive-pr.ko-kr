---
title: MSSQLSERVER_18452 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18456 (Database Engine error)
- 18452 (Database Engine error)
ms.assetid: 21da332c-e81d-4dee-a9d2-95598911b3be
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5786d5de4748f6bbf59d2bd4acecd7ca77977f11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652143"
---
# <a name="mssqlserver_18452"></a><span data-ttu-id="adc13-102">MSSQLSERVER_18452</span><span class="sxs-lookup"><span data-stu-id="adc13-102">MSSQLSERVER_18452</span></span>
    
## <a name="details"></a><span data-ttu-id="adc13-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="adc13-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="adc13-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="adc13-104">Product Name</span></span>|<span data-ttu-id="adc13-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="adc13-105">SQL Server</span></span>|  
|<span data-ttu-id="adc13-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="adc13-106">Event ID</span></span>|<span data-ttu-id="adc13-107">18452</span><span class="sxs-lookup"><span data-stu-id="adc13-107">18452</span></span>|  
|<span data-ttu-id="adc13-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="adc13-108">Event Source</span></span>|<span data-ttu-id="adc13-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="adc13-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="adc13-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="adc13-110">Component</span></span>|<span data-ttu-id="adc13-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="adc13-111">SQLEngine</span></span>|  
|<span data-ttu-id="adc13-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="adc13-112">Symbolic Name</span></span>|<span data-ttu-id="adc13-113">LOGON_INVALID_CONNECT</span><span class="sxs-lookup"><span data-stu-id="adc13-113">LOGON_INVALID_CONNECT</span></span>|  
|<span data-ttu-id="adc13-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="adc13-114">Message Text</span></span>|<span data-ttu-id="adc13-115">사용자 '%.\*ls'이(가) 로그인하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="adc13-115">Login failed for user '%.\*ls'.</span></span> <span data-ttu-id="adc13-116">SQL Server 로그인으로 Windows 인증과 함께 사용할 수 없습니다. %.\*ls</span><span class="sxs-lookup"><span data-stu-id="adc13-116">The login is a SQL Server login and cannot be used with Windows Authentication.%.\*ls</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="adc13-117">설명</span><span class="sxs-lookup"><span data-stu-id="adc13-117">Explanation</span></span>  
 <span data-ttu-id="adc13-118">사용자가 유효성을 검사할 수 없는 자격 증명으로 로그인하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="adc13-118">The user attempted to login with credentials that cannot be validated.</span></span> <span data-ttu-id="adc13-119">가능한 원인은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="adc13-119">Possible causes are:</span></span>  
  
-   <span data-ttu-id="adc13-120">로그인이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인일 수 있지만 서버에서 Windows 인증만 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="adc13-120">The login may be a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login but the server only accepts Windows Authentication.</span></span>  
  
-   <span data-ttu-id="adc13-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 연결하려고 하고 있지만 사용된 로그인이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="adc13-121">You are trying to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication but the login used does not exist on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="adc13-122">로그인이 Windows 인증을 사용할 수 있지만 인식할 수 없는 Windows 보안 주체입니다.</span><span class="sxs-lookup"><span data-stu-id="adc13-122">The login may use Windows Authentication but the login is an unrecognized Windows principal.</span></span> <span data-ttu-id="adc13-123">인식할 수 없는 Windows 보안 주체란 로그인을 Windows에서 확인할 수 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="adc13-123">An unrecognized Windows principal means that the login cannot be verified by Windows.</span></span> <span data-ttu-id="adc13-124">이는 Windows 로그인이 트러스트되지 않은 도메인에서 온 것이기 때문일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adc13-124">This could be because the Windows login is from an untrusted domain.</span></span>  
  
 <span data-ttu-id="adc13-125">유사한 문제가 덜 구체적인 오류 18456를 일으킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adc13-125">Similar problems can cause the less-specific error 18456.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="adc13-126">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="adc13-126">User Action</span></span>  
 <span data-ttu-id="adc13-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 연결하려고 하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 혼합 인증 모드로 구성되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="adc13-127">If you are trying to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, verify that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured in Mixed Authentication Mode.</span></span>  
  
 <span data-ttu-id="adc13-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 연결하려고 하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="adc13-128">If you are trying to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, verify that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login exists.</span></span>  
  
 <span data-ttu-id="adc13-129">Windows 인증을 사용하여 연결하려고 하는 경우 올바른 도메인에 제대로 로그인되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="adc13-129">If you are trying to connect using Windows Authentication, verify that you are properly logged into the correct domain.</span></span>  
  
  
