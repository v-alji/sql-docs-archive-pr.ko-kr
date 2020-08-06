---
title: 암호화 알고리즘 선택 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- cryptography [SQL Server], algorithms
- encryption [SQL Server], algorithms
- security [SQL Server], encryption
- algorithms [SQL Server encryption]
ms.assetid: 8227028c-a9c9-489d-bd27-fbf8242634ae
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 3b2c5292b4a00a3ad81e53fdbc603bb584130613
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741723"
---
# <a name="choose-an-encryption-algorithm"></a><span data-ttu-id="1e46a-102">암호화 알고리즘 선택</span><span class="sxs-lookup"><span data-stu-id="1e46a-102">Choose an Encryption Algorithm</span></span>
  <span data-ttu-id="1e46a-103">암호화는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 인터페이스를 보호하려는 관리자가 사용할 수 있는 여러 가지 심층 방어 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="1e46a-103">Encryption is one of several defenses-in-depth that are available to the administrator who wants to secure an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="1e46a-104">암호화 알고리즘은 권한이 없는 사용자가 쉽게 바꿀 수 없는 데이터 변환을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="1e46a-104">Encryption algorithms define data transformations that cannot be easily reversed by unauthorized users.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="1e46a-105">를 사용하면 관리자와 개발자가 DES, Triple DES, TRIPLE_DES_3KEY, RC2, RC4, 128비트 RC4, DESX, 128비트 AES, 192비트 AES, 256비트 AES 등의 여러 알고리즘 중에서 원하는 알고리즘을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e46a-105">allows administrators and developers to choose from among several algorithms, including DES, Triple DES, TRIPLE_DES_3KEY, RC2, RC4, 128-bit RC4, DESX, 128-bit AES, 192-bit AES, and 256-bit AES.</span></span>  
  
 <span data-ttu-id="1e46a-106">모든 상황에 맞는 이상적인 단일 알고리즘은 없으며 각 알고리즘의 장점에 대한 내용은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 온라인 설명서에서 다루지 않지만</span><span class="sxs-lookup"><span data-stu-id="1e46a-106">No single algorithm is ideal for all situations, and guidance on the merits of each is beyond the scope of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="1e46a-107">다음과 같은 일반적인 원칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e46a-107">However, the following general principles apply:</span></span>  
  
-   <span data-ttu-id="1e46a-108">강력한 암호화는 일반적으로 약한 암호화보다 더 많은 CPU 리소스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1e46a-108">Strong encryption generally consumes more CPU resources than weak encryption.</span></span>  
  
-   <span data-ttu-id="1e46a-109">일반적으로 짧은 키보다 긴 키가 강력한 암호화를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="1e46a-109">Long keys generally yield stronger encryption than short keys.</span></span>  
  
-   <span data-ttu-id="1e46a-110">동일한 키 길이를 사용하는 대칭 암호화보다 비대칭 암호화가 약하지만 상대적으로 속도가 느립니다.</span><span class="sxs-lookup"><span data-stu-id="1e46a-110">Asymmetric encryption is weaker than symmetric encryption using the same key length, but it is relatively slow.</span></span>  
  
-   <span data-ttu-id="1e46a-111">스트림 암호화보다 긴 키를 사용하는 블록 암호화가 강력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e46a-111">Block ciphers with long keys are stronger than stream ciphers.</span></span>  
  
-   <span data-ttu-id="1e46a-112">짧은 암호보다 길고 복잡한 암호가 강력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e46a-112">Long, complex passwords are stronger than short passwords.</span></span>  
  
-   <span data-ttu-id="1e46a-113">많은 양의 데이터를 암호화하는 경우 대칭 키를 사용하여 데이터를 암호화한 다음 비대칭 키를 사용하여 해당 대칭 키를 암호화하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1e46a-113">If you are encrypting lots of data, you should encrypt the data using a symmetric key, and encrypt the symmetric key with an asymmetric key.</span></span>  
  
-   <span data-ttu-id="1e46a-114">암호화된 데이터는 압축할 수 없지만 압축된 데이터는 암호화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e46a-114">Encrypted data cannot be compressed, but compressed data can be encrypted.</span></span> <span data-ttu-id="1e46a-115">압축을 사용할 경우 데이터를 암호화하기 전에 먼저 압축해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e46a-115">If you use compression, you should compress data before encrypting it.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1e46a-116">RC4 알고리즘은 이전 버전과의 호환성을 위해서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e46a-116">The RC4 algorithm is only supported for backward compatibility.</span></span> <span data-ttu-id="1e46a-117">데이터베이스의 호환성 수준이 90 또는 100인 경우 새 자료는 RC4 또는 RC4_128로만 암호화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e46a-117">New material can only be encrypted using RC4 or RC4_128 when the database is in compatibility level 90 or 100.</span></span> <span data-ttu-id="1e46a-118">이 옵션은 사용하지 않는 것이 좋습니다. 대신 AES 알고리즘 중 하나와 같은 새 알고리즘을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="1e46a-118">(Not recommended.) Use a newer algorithm such as one of the AES algorithms instead.</span></span> <span data-ttu-id="1e46a-119">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 이상에서 RC4 또는 RC4_128을 사용하여 암호화된 자료는 모든 호환성 수준에서 해독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e46a-119">In [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] and higher material encrypted using RC4 or RC4_128 can be decrypted in any compatibility level.</span></span>  
>   
>  <span data-ttu-id="1e46a-120">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에서는 솔트를 자동으로 제공하지 않기 때문에 서로 다른 데이터 블록에서 동일한 RC4 또는 RC4_128 KEY_GUID를 반복해서 사용하면 동일한 RC4 키가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="1e46a-120">Repeated use of the same RC4 or RC4_128 KEY_GUID on different blocks of data will result in the same RC4 key because [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not provide a salt automatically.</span></span> <span data-ttu-id="1e46a-121">동일한 RC4 키를 반복해서 사용하는 것은 암호화를 매우 약하게 만드는 잘 알려진 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="1e46a-121">Using the same RC4 key repeatedly is a well-known error that will result in very weak encryption.</span></span> <span data-ttu-id="1e46a-122">따라서 RC4 및 RC4_128 키워드는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e46a-122">Therefore, we have deprecated the RC4 and RC4_128 keywords.</span></span> [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)]  
  
 <span data-ttu-id="1e46a-123">암호화 알고리즘 및 암호화 기술에 대한 자세한 내용은 MSDN에서 .NET Framework Developer's Guide의 [주요 보안 개념(Key Security Concepts)](https://go.microsoft.com/fwlink/?LinkId=62082) 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1e46a-123">For more information about encryption algorithms and encryption technology, see [Key Security Concepts](https://go.microsoft.com/fwlink/?LinkId=62082) in the .NET Framework Developer's Guide on MSDN.</span></span>  
  
 <span data-ttu-id="1e46a-124">**DES 알고리즘 관련 설명:**</span><span class="sxs-lookup"><span data-stu-id="1e46a-124">**Clarification regarding DES algorithms:**</span></span>  
  
-   <span data-ttu-id="1e46a-125">DESX 이름이 잘못 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1e46a-125">DESX was incorrectly named.</span></span> <span data-ttu-id="1e46a-126">ALGORITHM = DESX를 사용하여 만든 대칭 키에 실제로 192비트 키를 포함하는 TRIPLE DES 암호화가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e46a-126">Symmetric keys created with ALGORITHM = DESX actually use the TRIPLE DES cipher with a 192-bit key.</span></span> <span data-ttu-id="1e46a-127">DESX 알고리즘은 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e46a-127">The DESX algorithm is not provided.</span></span> [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
-   <span data-ttu-id="1e46a-128">ALGORITHM = TRIPLE_DES_3KEY를 사용하여 만든 대칭 키에 192비트 키를 포함하는 TRIPLE DES가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e46a-128">Symmetric keys created with ALGORITHM = TRIPLE_DES_3KEY use TRIPLE DES with a 192-bit key.</span></span>  
  
-   <span data-ttu-id="1e46a-129">ALGORITHM = TRIPLE_DES를 사용하여 만든 대칭 키에 128비트 키를 포함하는 TRIPLE DES가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e46a-129">Symmetric keys created with ALGORITHM = TRIPLE_DES use TRIPLE DES with a 128-bit key.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="1e46a-130">관련 작업</span><span class="sxs-lookup"><span data-stu-id="1e46a-130">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1e46a-131">대칭 키를 사용하여 암호화</span><span class="sxs-lookup"><span data-stu-id="1e46a-131">Encrypting using a symmetric key.</span></span>|[<span data-ttu-id="1e46a-132">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1e46a-132">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-symmetric-key-transact-sql)|  
|<span data-ttu-id="1e46a-133">비대칭 키를 사용하여 암호화</span><span class="sxs-lookup"><span data-stu-id="1e46a-133">Encrypting using an asymmetric key.</span></span>|[<span data-ttu-id="1e46a-134">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1e46a-134">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-asymmetric-key-transact-sql)|  
|<span data-ttu-id="1e46a-135">인증서를 사용하여 암호화</span><span class="sxs-lookup"><span data-stu-id="1e46a-135">Encrypting using a certificate.</span></span>|[<span data-ttu-id="1e46a-136">CREATE CERTIFICATE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1e46a-136">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-certificate-transact-sql)|  
|<span data-ttu-id="1e46a-137">투명한 데이터 암호화를 사용하여 데이터베이스 파일 암호화</span><span class="sxs-lookup"><span data-stu-id="1e46a-137">Encrypting database files using transparent data encryption.</span></span>|[<span data-ttu-id="1e46a-138">투명한 데이터 암호화&#40;TDE&#41;</span><span class="sxs-lookup"><span data-stu-id="1e46a-138">Transparent Data Encryption &#40;TDE&#41;</span></span>](transparent-data-encryption.md)|  
|<span data-ttu-id="1e46a-139">테이블의 한 열을 암호화하는 방법</span><span class="sxs-lookup"><span data-stu-id="1e46a-139">How to encrypt one column of a table.</span></span>|[<span data-ttu-id="1e46a-140">데이터 열 암호화</span><span class="sxs-lookup"><span data-stu-id="1e46a-140">Encrypt a Column of Data</span></span>](encrypt-a-column-of-data.md)|  
  
## <a name="see-also"></a><span data-ttu-id="1e46a-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1e46a-141">See Also</span></span>  
 <span data-ttu-id="1e46a-142">[SQL Server 암호화](sql-server-encryption.md) </span><span class="sxs-lookup"><span data-stu-id="1e46a-142">[SQL Server Encryption](sql-server-encryption.md) </span></span>  
 [<span data-ttu-id="1e46a-143">암호화 계층</span><span class="sxs-lookup"><span data-stu-id="1e46a-143">Encryption Hierarchy</span></span>](encryption-hierarchy.md)  
  
  
