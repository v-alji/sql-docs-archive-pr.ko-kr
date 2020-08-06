---
title: MSSQLSERVER_33028 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33028 (Database Engine error)
ms.assetid: c5cec0e4-0bcd-4907-826f-e7d835cfcb37
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 555dcf0220793abc0e8af81b3f56867f9960c5f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650057"
---
# <a name="mssqlserver_33028"></a><span data-ttu-id="ee6a1-102">MSSQLSERVER_33028</span><span class="sxs-lookup"><span data-stu-id="ee6a1-102">MSSQLSERVER_33028</span></span>
    
## <a name="details"></a><span data-ttu-id="ee6a1-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="ee6a1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ee6a1-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="ee6a1-104">Product Name</span></span>|<span data-ttu-id="ee6a1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ee6a1-105">SQL Server</span></span>|  
|<span data-ttu-id="ee6a1-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="ee6a1-106">Event ID</span></span>|<span data-ttu-id="ee6a1-107">33028</span><span class="sxs-lookup"><span data-stu-id="ee6a1-107">33028</span></span>|  
|<span data-ttu-id="ee6a1-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="ee6a1-108">Event Source</span></span>|<span data-ttu-id="ee6a1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ee6a1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ee6a1-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="ee6a1-110">Component</span></span>|<span data-ttu-id="ee6a1-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ee6a1-111">SQLEngine</span></span>|  
|<span data-ttu-id="ee6a1-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="ee6a1-112">Symbolic Name</span></span>|<span data-ttu-id="ee6a1-113">SEC_CRYPTOPROV_CANTOPENSESSION</span><span class="sxs-lookup"><span data-stu-id="ee6a1-113">SEC_CRYPTOPROV_CANTOPENSESSION</span></span>|  
|<span data-ttu-id="ee6a1-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="ee6a1-114">Message Text</span></span>|<span data-ttu-id="ee6a1-115">%S_MSG '%.\*ls'에 대한 세션을 열 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ee6a1-115">Cannot open session for %S_MSG '%.\*ls'.</span></span> <span data-ttu-id="ee6a1-116">공급자 오류 코드: %d.</span><span class="sxs-lookup"><span data-stu-id="ee6a1-116">Provider error code: %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ee6a1-117">설명</span><span class="sxs-lookup"><span data-stu-id="ee6a1-117">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="ee6a1-118">에서 위의 오류 메시지에 나열된 암호화 공급자를 열 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ee6a1-118">was unable to open the cryptographic provider listed in the error message.</span></span> <span data-ttu-id="ee6a1-119">암호화 공급자가 위의 오류 코드를 제공했습니다.</span><span class="sxs-lookup"><span data-stu-id="ee6a1-119">The cryptographic provider supplied the error code listed.</span></span> <span data-ttu-id="ee6a1-120">암호화 공급자에게 오류에 대한 자세한 정보를 문의해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee6a1-120">You may need to contact your cryptographic provider for more information about the error.</span></span>  
  
|<span data-ttu-id="ee6a1-121">오류 코드</span><span class="sxs-lookup"><span data-stu-id="ee6a1-121">Error code</span></span>|<span data-ttu-id="ee6a1-122">Description</span><span class="sxs-lookup"><span data-stu-id="ee6a1-122">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="ee6a1-123">0</span><span class="sxs-lookup"><span data-stu-id="ee6a1-123">0</span></span>|<span data-ttu-id="ee6a1-124">성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="ee6a1-124">Success.</span></span> <span data-ttu-id="ee6a1-125">오류가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ee6a1-125">No error.</span></span>|  
|<span data-ttu-id="ee6a1-126">1</span><span class="sxs-lookup"><span data-stu-id="ee6a1-126">1</span></span>|<span data-ttu-id="ee6a1-127">실패.</span><span class="sxs-lookup"><span data-stu-id="ee6a1-127">Failure.</span></span> <span data-ttu-id="ee6a1-128">지정되지 않았거나 예기치 않은 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="ee6a1-128">An unspecified or unexpected error occurred.</span></span> <span data-ttu-id="ee6a1-129">사용할 수 있는 추가 정보가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ee6a1-129">Additional information is not available.</span></span>|  
|<span data-ttu-id="ee6a1-130">2</span><span class="sxs-lookup"><span data-stu-id="ee6a1-130">2</span></span>|<span data-ttu-id="ee6a1-131">부족한 버퍼.</span><span class="sxs-lookup"><span data-stu-id="ee6a1-131">Insufficient Buffer.</span></span> <span data-ttu-id="ee6a1-132">암호화 공급자가 사용할 공간을 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ee6a1-132">Space could not be allocated for the cryptographic provider.</span></span>|  
|<span data-ttu-id="ee6a1-133">3</span><span class="sxs-lookup"><span data-stu-id="ee6a1-133">3</span></span>|<span data-ttu-id="ee6a1-134">지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ee6a1-134">Not Supported.</span></span> <span data-ttu-id="ee6a1-135">암호화 공급자가 이 릴리스에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ee6a1-135">The cryptographic provider is not supported by this release.</span></span> <span data-ttu-id="ee6a1-136">다른 암호화 공급자를 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="ee6a1-136">Select another cryptographic provider.</span></span>|  
|<span data-ttu-id="ee6a1-137">4</span><span class="sxs-lookup"><span data-stu-id="ee6a1-137">4</span></span>|<span data-ttu-id="ee6a1-138">찾을 수 없음.</span><span class="sxs-lookup"><span data-stu-id="ee6a1-138">Not Found.</span></span> <span data-ttu-id="ee6a1-139">지정된 암호화 공급자가 없거나 해당 파일에 액세스할 수 있는 권한을 가지고 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ee6a1-139">The specified cryptographic provider is not present or you do not have authorization to access the files.</span></span>|  
|<span data-ttu-id="ee6a1-140">5</span><span class="sxs-lookup"><span data-stu-id="ee6a1-140">5</span></span>|<span data-ttu-id="ee6a1-141">권한 부여 실패.</span><span class="sxs-lookup"><span data-stu-id="ee6a1-141">Authorization Failure.</span></span> <span data-ttu-id="ee6a1-142">자격 증명을 만들 때 잘못된 암호나 사용자 이름을 제공할 경우 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee6a1-142">Can result from providing an incorrect password or username when creating the credential.</span></span> <span data-ttu-id="ee6a1-143">또한 자격 증명이 없는 경우에도 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee6a1-143">Can result if the credential does not exist.</span></span>|  
|<span data-ttu-id="ee6a1-144">6</span><span class="sxs-lookup"><span data-stu-id="ee6a1-144">6</span></span>|<span data-ttu-id="ee6a1-145">인수가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ee6a1-145">Invalid Argument.</span></span> <span data-ttu-id="ee6a1-146">암호화 공급자에게 잘못된 인수가 전달되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ee6a1-146">An invalid argument was passed to the cryptographic provider.</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="ee6a1-147">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="ee6a1-147">User Action</span></span>  
 <span data-ttu-id="ee6a1-148">오류를 해결하거나 암호화 공급자에게 자세한 정보를 문의합니다.</span><span class="sxs-lookup"><span data-stu-id="ee6a1-148">Resolve the error, or contact the cryptographic provider for more information.</span></span>  
  
  
