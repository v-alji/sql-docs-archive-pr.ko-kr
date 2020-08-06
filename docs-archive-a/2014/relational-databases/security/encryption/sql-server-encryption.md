---
title: SQL Server 암호화 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], about encryption
- security [SQL Server], encryption
- cryptography [SQL Server], about cryptography
ms.assetid: ead0150e-4943-4ad5-84c8-36f85c7278f4
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 6fc68e6f3280a8e23d6a1bf4f364aadfffd69f85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743151"
---
# <a name="sql-server-encryption"></a><span data-ttu-id="0b7d0-102">SQL Server 암호화</span><span class="sxs-lookup"><span data-stu-id="0b7d0-102">SQL Server Encryption</span></span>
  <span data-ttu-id="0b7d0-103">암호화는 키 또는 암호를 사용하여 데이터를 난독 처리하는 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-103">Encryption is the process of obfuscating data by the use of a key or password.</span></span> <span data-ttu-id="0b7d0-104">이 경우 해당하는 암호 해독 키 또는 암호가 없으면 데이터를 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-104">This can make the data useless without the corresponding decryption key or password.</span></span> <span data-ttu-id="0b7d0-105">암호화를 통해 액세스 제어 문제를 해결할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-105">Encryption does not solve access control problems.</span></span> <span data-ttu-id="0b7d0-106">그러나 암호화를 사용하면 액세스 제어가 무시되는 경우에도 데이터 손실을 제한하여 보안이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-106">However, it enhances security by limiting data loss even if access controls are bypassed.</span></span> <span data-ttu-id="0b7d0-107">예를 들어 데이터베이스 호스트 컴퓨터가 잘못 구성되어 해커가 중요한 데이터를 얻는 경우 해당 정보가 암호화되어 있으면 해킹한 정보를 사용하지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-107">For example, if the database host computer is misconfigured and a hacker obtains sensitive data, that stolen information might be useless if it is encrypted.</span></span>  
  
 <span data-ttu-id="0b7d0-108">연결, 데이터 및 저장 프로시저에 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 암호화를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-108">You can use encryption in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for connections, data, and stored procedures.</span></span> <span data-ttu-id="0b7d0-109">다음 표에서는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 암호화에 대한 자세한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-109">The following table contains more information about encryption in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0b7d0-110">암호화가 보안을 유지해 주는 유용한 도구지만 모든 데이터나 연결에 대해 고려해야 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-110">Although encryption is a valuable tool to help ensure security, it should not be considered for all data or connections.</span></span> <span data-ttu-id="0b7d0-111">암호화 구현 여부를 결정할 때는 사용자가 데이터에 액세스하는 방법을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-111">When you are deciding whether to implement encryption, consider how users will access data.</span></span> <span data-ttu-id="0b7d0-112">사용자가 공용 네트워크를 통해 데이터에 액세스할 경우 보안을 높이기 위한 데이터 암호화가 필요할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-112">If users access data over a public network, data encryption might be required to increase security.</span></span> <span data-ttu-id="0b7d0-113">그러나 모든 액세스가 보안 인트라넷 구성과 관련된 경우 암호화가 필요하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-113">However, if all access involves a secure intranet configuration, encryption might not be required.</span></span> <span data-ttu-id="0b7d0-114">암호화를 사용하려면 암호, 키 및 인증서에 대한 유지 관리 전략도 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-114">Any use of encryption should also include a maintenance strategy for passwords, keys, and certificates.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0b7d0-115">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="0b7d0-115">In This Section</span></span>  
 [<span data-ttu-id="0b7d0-116">암호화 계층</span><span class="sxs-lookup"><span data-stu-id="0b7d0-116">Encryption Hierarchy</span></span>](encryption-hierarchy.md)  
 <span data-ttu-id="0b7d0-117">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 암호화 계층에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-117">Information about the encryption hierarchy in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="0b7d0-118">암호화 알고리즘 선택</span><span class="sxs-lookup"><span data-stu-id="0b7d0-118">Choose an Encryption Algorithm</span></span>](choose-an-encryption-algorithm.md)  
 <span data-ttu-id="0b7d0-119">효과적인 암호화 알고리즘을 선택하는 방법에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-119">Information about how to select an effective encrypting algorithm.</span></span>  
  
 [<span data-ttu-id="0b7d0-120">투명한 데이터 암호화&#40;TDE&#41;</span><span class="sxs-lookup"><span data-stu-id="0b7d0-120">Transparent Data Encryption &#40;TDE&#41;</span></span>](transparent-data-encryption.md)  
 <span data-ttu-id="0b7d0-121">데이터를 명시적으로 암호화하는 방법에 대한 일반적인 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-121">General information about how to encrypt data transparently.</span></span>  
  
 [<span data-ttu-id="0b7d0-122">SQL Server 및 데이터베이스 암호화 키&#40;데이터베이스 엔진&#41;</span><span class="sxs-lookup"><span data-stu-id="0b7d0-122">SQL Server and Database Encryption Keys &#40;Database Engine&#41;</span></span>](sql-server-and-database-encryption-keys-database-engine.md)  
 <span data-ttu-id="0b7d0-123">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 암호화 키에는 중요한 데이터를 보호하는 데 사용되는 퍼블릭 키, 프라이빗 키 및 대칭 키의 조합이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-123">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], encryption keys include a combination of public, private, and symmetric keys that are used to protect sensitive data.</span></span> <span data-ttu-id="0b7d0-124">이 섹션에서는 암호화 키를 구현하고 관리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-124">This section explains how to implement and manage encryption keys.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="0b7d0-125">관련 내용</span><span class="sxs-lookup"><span data-stu-id="0b7d0-125">Related Content</span></span>  
 [<span data-ttu-id="0b7d0-126">SQL Server 보안 설정</span><span class="sxs-lookup"><span data-stu-id="0b7d0-126">Securing SQL Server</span></span>](../securing-sql-server.md)  
 <span data-ttu-id="0b7d0-127">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 플랫폼에 보안을 설정하는 방법 및 사용자 및 보안 개체 작업을 수행하는 방법에 대한 개요입니다.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-127">Overview of how to help secure the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] platform, and how to work with users and securable objects.</span></span>  
  
 [<span data-ttu-id="0b7d0-128">암호화 함수&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0b7d0-128">Cryptographic Functions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/cryptographic-functions-transact-sql)  
 <span data-ttu-id="0b7d0-129">암호화 함수 구현 방법에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-129">Information about how to implement cryptographic functions.</span></span>  
  
 [<span data-ttu-id="0b7d0-130">ENCRYPTBYPASSPHRASE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0b7d0-130">ENCRYPTBYPASSPHRASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/encryptbypassphrase-transact-sql)  
 <span data-ttu-id="0b7d0-131">데이터를 암호화하기 위해 암호를 사용하는 방법에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-131">Information about how to use a password to encrypt data.</span></span>  
  
 [<span data-ttu-id="0b7d0-132">ENCRYPTBYKEY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0b7d0-132">ENCRYPTBYKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/encryptbykey-transact-sql)  
 <span data-ttu-id="0b7d0-133">데이터를 암호화하기 위해 대칭 키를 사용하는 방법에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-133">Information about how to use a symmetric key to encrypt data.</span></span>  
  
 [<span data-ttu-id="0b7d0-134">ENCRYPTBYASYMKEY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0b7d0-134">ENCRYPTBYASYMKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/encryptbyasymkey-transact-sql)  
 <span data-ttu-id="0b7d0-135">데이터를 암호화하기 위해 비대칭 키를 사용하는 방법에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-135">Information about how to use an asymmetric key to encrypt data.</span></span>  
  
 [<span data-ttu-id="0b7d0-136">ENCRYPTBYCERT&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0b7d0-136">ENCRYPTBYCERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/encryptbycert-transact-sql)  
 <span data-ttu-id="0b7d0-137">데이터를 암호화하기 위해 인증서를 사용하는 방법에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-137">Information about how to use a certificate to encrypt data.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="0b7d0-138">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="0b7d0-138">External Resources</span></span>  
 [<span data-ttu-id="0b7d0-139">SQL Server 2005 보안에 대 한 10 단계</span><span class="sxs-lookup"><span data-stu-id="0b7d0-139">10 Steps to SQL Server 2005 Security</span></span>](https://www.itprotoday.com/sql-server/10-steps-sql-server-2005-security)  
 <span data-ttu-id="0b7d0-140">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 보안에 대한 현재 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-140">Current information about [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b7d0-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0b7d0-141">See Also</span></span>  
 <span data-ttu-id="0b7d0-142">[sys.key_encryptions&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-key-encryptions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0b7d0-142">[sys.key_encryptions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-key-encryptions-transact-sql) </span></span>  
 <span data-ttu-id="0b7d0-143">[SQL Server 및 데이터베이스 암호화 키&#40;데이터베이스 엔진&#41;](sql-server-and-database-encryption-keys-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="0b7d0-143">[SQL Server and Database Encryption Keys &#40;Database Engine&#41;](sql-server-and-database-encryption-keys-database-engine.md) </span></span>  
 [<span data-ttu-id="0b7d0-144">Reporting Services 암호화 키 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="0b7d0-144">Back Up and Restore Reporting Services Encryption Keys</span></span>](../../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)  
  
  
