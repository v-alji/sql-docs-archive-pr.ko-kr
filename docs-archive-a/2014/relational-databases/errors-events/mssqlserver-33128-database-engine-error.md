---
title: MSSQLSERVER_33128 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33128 (Database Engine error)
ms.assetid: 12c1096f-d120-439b-85f3-f794859503c9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 158cc609a18cf3fe7b76708e351b78263cd80a9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650054"
---
# <a name="mssqlserver_33128"></a><span data-ttu-id="a7870-102">MSSQLSERVER_33128</span><span class="sxs-lookup"><span data-stu-id="a7870-102">MSSQLSERVER_33128</span></span>
    
## <a name="details"></a><span data-ttu-id="a7870-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="a7870-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a7870-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="a7870-104">Product Name</span></span>|<span data-ttu-id="a7870-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a7870-105">SQL Server</span></span>|  
|<span data-ttu-id="a7870-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="a7870-106">Event ID</span></span>|<span data-ttu-id="a7870-107">33128</span><span class="sxs-lookup"><span data-stu-id="a7870-107">33128</span></span>|  
|<span data-ttu-id="a7870-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="a7870-108">Event Source</span></span>|<span data-ttu-id="a7870-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a7870-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a7870-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="a7870-110">Component</span></span>|<span data-ttu-id="a7870-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a7870-111">SQLEngine</span></span>|  
|<span data-ttu-id="a7870-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="a7870-112">Symbolic Name</span></span>|<span data-ttu-id="a7870-113">SEC_DEPRECATED_ALGO</span><span class="sxs-lookup"><span data-stu-id="a7870-113">SEC_DEPRECATED_ALGO</span></span>|  
|<span data-ttu-id="a7870-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="a7870-114">Message Text</span></span>|<span data-ttu-id="a7870-115">암호화가 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-115">Encryption failed.</span></span> <span data-ttu-id="a7870-116">키에 사용된 ' %. \* ls 알고리즘은 더 이상 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-116">Key uses deprecated algorithm '%.\*ls' which is no longer supported.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a7870-117">설명</span><span class="sxs-lookup"><span data-stu-id="a7870-117">Explanation</span></span>  
 <span data-ttu-id="a7870-118">이 메시지는 RC4 또는 RC4_128 암호화 알고리즘을 참조할 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-118">This message occurs when referencing the RC4 (or RC4_128) encryption algorithm.</span></span> <span data-ttu-id="a7870-119">RC4 및 RC4_128은 약한 알고리즘이며 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-119">RC4 and RC4_128 are weak algorithms and are deprecated.</span></span> <span data-ttu-id="a7870-120">대신 AES 알고리즘 같은 강력한 알고리즘을 사용하는 것이</span><span class="sxs-lookup"><span data-stu-id="a7870-120">Use a stronger algorithm such as one of the AES algorithms instead.</span></span>  
  
 <span data-ttu-id="a7870-121">데이터베이스 호환성 수준이 90 또는 100인 경우 작업이 성공하고 Deprecation 이벤트가 발생하며 메시지가 링 버퍼에만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-121">When the database compatibility level is 90 or 100, the operation succeeds, the deprecation event is raised, and the message appears only in the ring buffer.</span></span>  
  
 <span data-ttu-id="a7870-122">데이터베이스 호환성 수준이 110 이상인 경우 해독 작업이 성공하고 Deprecation 이벤트가 발생하며 메시지가 링 버퍼에만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-122">When the database compatibility level is 110 or higher, decryption operations succeed, the deprecation event is raised, and the message appears only in the ring buffer.</span></span> <span data-ttu-id="a7870-123">암호화 작업이 실패하고 Deprecation 이벤트가 발생하며 메시지가 사용자에게 표시되고 링 버퍼에도 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-123">Encryption operations will fail, the deprecation event is raised, and the message is displayed for the user, and the message appears in the ring buffer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a7870-124">링 버퍼는 문서화가 완전하게 완료되지 않은 내부 구성 요소이며 고객은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-124">The ring buffer is an internal component which is not fully documented and is not intended to be used by customers.</span></span> <span data-ttu-id="a7870-125">링 버퍼의 메시지는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 고객 지원 서비스에 문의할 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-125">Messages from the ring buffer are useful when contacting [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Support.</span></span> <span data-ttu-id="a7870-126">링 버퍼를 보려면 sys.dm_os_ring_buffers 동적 관리 뷰를 쿼리하세요.</span><span class="sxs-lookup"><span data-stu-id="a7870-126">To view the ring buffer, query the sys.dm_os_ring_buffers dynamic management view.</span></span>  
  
|<span data-ttu-id="a7870-127">시스템 상태</span><span class="sxs-lookup"><span data-stu-id="a7870-127">State</span></span>|<span data-ttu-id="a7870-128">Description</span><span class="sxs-lookup"><span data-stu-id="a7870-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a7870-129">1</span><span class="sxs-lookup"><span data-stu-id="a7870-129">1</span></span>|<span data-ttu-id="a7870-130">RC4 키는 기본 제공 encryptbykey() 함수에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-130">A RC4 key is used in the built-in encryptbykey() function.</span></span> <span data-ttu-id="a7870-131">기본 제공 함수는 NULL을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-131">Built-in function returns NULL.</span></span> <span data-ttu-id="a7870-132">이 메시지는 링 버퍼에만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-132">This message only appears in the ring buffer.</span></span>|  
|<span data-ttu-id="a7870-133">2</span><span class="sxs-lookup"><span data-stu-id="a7870-133">2</span></span>|<span data-ttu-id="a7870-134">RC4 키는 기본 제공 decryptbykey() 함수에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-134">A RC4 key is used in by the built-in decryptbykey() function.</span></span> <span data-ttu-id="a7870-135">이 메시지는 링 버퍼에만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-135">This message only appears in the ring buffer.</span></span>|  
|<span data-ttu-id="a7870-136">3</span><span class="sxs-lookup"><span data-stu-id="a7870-136">3</span></span>|<span data-ttu-id="a7870-137">사용되지 않는 RC4 키가 대칭 키로 암호화되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-137">A deprecated RC4 key is being encrypted by a symmetric key.</span></span> <span data-ttu-id="a7870-138">이 메시지는 사용자에게 표시되고 링 버퍼에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-138">Seen by users and in the ring buffer.</span></span> <span data-ttu-id="a7870-139">사용되지 않는 RC4 대칭 키는 호환성 수준 110에서 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-139">Deprecated RC4 symmetric keys cannot be altered in compatibility level 110.</span></span> <span data-ttu-id="a7870-140">암호화 작업에는 RC4 이외의 키를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="a7870-140">Try to use non-RC4 keys for crypto operations.</span></span> <span data-ttu-id="a7870-141">필요한 경우 이전 버전과의 호환성 수준을 90 또는 100으로 설정하십시오.</span><span class="sxs-lookup"><span data-stu-id="a7870-141">If necessary, set backward compatibility level to a 90 or 100.</span></span>|  
|<span data-ttu-id="a7870-142">4</span><span class="sxs-lookup"><span data-stu-id="a7870-142">4</span></span>|<span data-ttu-id="a7870-143">RC4 이외의 키가 사용되지 않는 RC4 대칭 키로 암호화되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-143">A non-RC4 key is being encrypted by a deprecated RC4 symmetric key.</span></span> <span data-ttu-id="a7870-144">이 메시지는 사용자에게 표시되고 링 버퍼에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-144">Seen by users and in the ring buffer.</span></span> <span data-ttu-id="a7870-145">RC4 이외의 대칭 키를 사용하도록 애플리케이션을 수정하거나 이전 버전과의 호환성 수준을 90 또는 100으로 설정하십시오.</span><span class="sxs-lookup"><span data-stu-id="a7870-145">Modify the application to use non-RC4 symmetric keys or set backward compatibility level to 90 or 100.</span></span>|  
|<span data-ttu-id="a7870-146">5</span><span class="sxs-lookup"><span data-stu-id="a7870-146">5</span></span>|<span data-ttu-id="a7870-147">사용되지 않는 RC4 키가 대칭 키로 해독되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-147">A deprecated RC4 key is being decrypted by a symmetric key.</span></span> <span data-ttu-id="a7870-148">이 메시지는 링 버퍼에만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-148">This message only appears in the ring buffer.</span></span>|  
|<span data-ttu-id="a7870-149">6</span><span class="sxs-lookup"><span data-stu-id="a7870-149">6</span></span>|<span data-ttu-id="a7870-150">RC4 이외의 키가 RC4 대칭 키로 해독되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-150">A non-RC4 key is being decrypted by an RC4 symmetric key.</span></span> <span data-ttu-id="a7870-151">이 메시지는 링 버퍼에만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-151">This message only appears in the ring buffer.</span></span>|  
|<span data-ttu-id="a7870-152">7</span><span class="sxs-lookup"><span data-stu-id="a7870-152">7</span></span>|<span data-ttu-id="a7870-153">RC4 대칭 키가 인증서로 암호화되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-153">A RC4 symmetric key is being encrypted by the certificate.</span></span> <span data-ttu-id="a7870-154">이 메시지는 사용자에게 표시되고 링 버퍼에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-154">Seen by users and in the ring buffer.</span></span>|  
|<span data-ttu-id="a7870-155">8</span><span class="sxs-lookup"><span data-stu-id="a7870-155">8</span></span>|<span data-ttu-id="a7870-156">RC4 대칭 키가 인증서로 해독되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-156">A RC4 symmetric key is being decrypted by the certificate.</span></span> <span data-ttu-id="a7870-157">이 메시지는 링 버퍼에만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-157">This message only appears in the ring buffer.</span></span>|  
|<span data-ttu-id="a7870-158">9</span><span class="sxs-lookup"><span data-stu-id="a7870-158">9</span></span>|<span data-ttu-id="a7870-159">RC4 대칭 키가 EKM 키로 암호화되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-159">A RC4 symmetric key is being encrypted by the EKM key.</span></span>|  
|<span data-ttu-id="a7870-160">10</span><span class="sxs-lookup"><span data-stu-id="a7870-160">10</span></span>|<span data-ttu-id="a7870-161">RC4 대칭 키가 EKM 키로 해독되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-161">A RC4 symmetric key is being decrypted by the EKM key.</span></span> <span data-ttu-id="a7870-162">이 메시지는 링 버퍼에만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-162">This message only appears in the ring buffer.</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="a7870-163">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="a7870-163">User Action</span></span>  
 <span data-ttu-id="a7870-164">대신 AES 알고리즘 같은 강력한 알고리즘을 사용하는 것이</span><span class="sxs-lookup"><span data-stu-id="a7870-164">Use a stronger algorithm such as one of the AES algorithms instead.</span></span> <span data-ttu-id="a7870-165">좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-165">(Recommended)</span></span>  
  
 <span data-ttu-id="a7870-166">ALTER DATABASE SET COMPATIBILITY_LEVEL을 사용하여 데이터베이스 호환성 수준을 100으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-166">Use ALTER DATABASE SET COMPATIBILITY_LEVEL to set the database to compatibility level 100.</span></span> <span data-ttu-id="a7870-167">이 옵션은 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a7870-167">(Not recommended.)</span></span>  
  
  
