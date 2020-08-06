---
title: 사용자 데이터베이스의 대칭 키 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3333ab5b-2518-4753-a0a8-57df5e5af74f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ca0fb62ccb32ce244e1087281997dcd9929df89c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648996"
---
# <a name="symmetric-keys-on-user-databases"></a><span data-ttu-id="59e83-102">사용자 데이터베이스의 대칭 키</span><span class="sxs-lookup"><span data-stu-id="59e83-102">Symmetric Keys on User Databases</span></span>
  <span data-ttu-id="59e83-103">이 규칙은 길이가 128바이트 미만인 키에 RC2 또는 RC4 암호화 알고리즘이 사용되지 않는지 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="59e83-103">This rule checks whether keys that have a length of less than 128 bytes do not use the RC2 or RC4 encryption algorithm.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="59e83-104">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="59e83-104">Best Practices Recommendations</span></span>  
 <span data-ttu-id="59e83-105">AES 128비트 이상을 사용하여 데이터 암호화를 위한 대칭 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="59e83-105">Use AES 128 bit or larger to create symmetric keys for data encryption.</span></span> <span data-ttu-id="59e83-106">운영 체제에서 AES를 지원하지 않을 경우 3DES를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="59e83-106">If AES is not supported by your operating system, use 3DES.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="59e83-107">참조 항목</span><span class="sxs-lookup"><span data-stu-id="59e83-107">For More Information</span></span>  
 [<span data-ttu-id="59e83-108">암호화 알고리즘 선택</span><span class="sxs-lookup"><span data-stu-id="59e83-108">Choose an Encryption Algorithm</span></span>](../security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a><span data-ttu-id="59e83-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="59e83-109">See Also</span></span>  
 [<span data-ttu-id="59e83-110">정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용</span><span class="sxs-lookup"><span data-stu-id="59e83-110">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
