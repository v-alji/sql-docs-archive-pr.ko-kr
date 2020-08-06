---
title: 암호화 계층 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], hierarchies
- cryptography [SQL Server], hierarchies
- encryption keys [SQL Server]
- security [SQL Server], encryption
- hierarchies [SQL Server], encryption
ms.assetid: 96c276d5-1bba-4e95-b678-10f059f1fbcf
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: d38bb83c2f6a2487e547c4686be5c65bc012e33e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741692"
---
# <a name="encryption-hierarchy"></a><span data-ttu-id="deca6-102">암호화 계층</span><span class="sxs-lookup"><span data-stu-id="deca6-102">Encryption Hierarchy</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="deca6-103">는 계층적 암호화 및 키 관리 인프라로 데이터를 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-103">encrypts data with a hierarchical encryption and key management infrastructure.</span></span> <span data-ttu-id="deca6-104">각 계층은 인증서, 비대칭 키 및 대칭 키 조합을 사용하여 해당 계층의 하위 계층을 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-104">Each layer encrypts the layer below it by using a combination of certificates, asymmetric keys, and symmetric keys.</span></span> <span data-ttu-id="deca6-105">비대칭 키 및 대칭 키는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 외부의 EKM(확장 가능 키 관리) 모듈에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-105">Asymmetric keys and symmetric keys can be stored outside of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in an Extensible Key Management (EKM) module.</span></span>  
  
 <span data-ttu-id="deca6-106">다음 그림에서는 암호화 계층의 각 계층이 그 아래의 계층을 암호화하는 모습과 가장 일반적인 암호화 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-106">The following illustration shows that each layer of the encryption hierarchy encrypts the layer beneath it, and displays the most common encryption configurations.</span></span> <span data-ttu-id="deca6-107">계층의 시작 부분에 대한 액세스는 일반적으로 암호로 보호됩니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-107">The access to the start of the hierarchy is usually protected by a password.</span></span>  
  
 <span data-ttu-id="deca6-108">![일부 암호화 조합을 스택으로 표시합니다.](../../../database-engine/media/encryption-hierarchy-stack.gif "일부 암호화 조합을 스택으로 표시합니다.")</span><span class="sxs-lookup"><span data-stu-id="deca6-108">![Displays some encryption combinations in a stack.](../../../database-engine/media/encryption-hierarchy-stack.gif "Displays some encryption combinations in a stack.")</span></span>  
  
 <span data-ttu-id="deca6-109">다음과 같은 개념을 염두에 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-109">Keep in mind the following concepts:</span></span>  
  
-   <span data-ttu-id="deca6-110">최상의 성능을 위해 인증서 또는 비대칭 키 대신 대칭 키를 사용하여 데이터를 암호화하십시오.</span><span class="sxs-lookup"><span data-stu-id="deca6-110">For best performance, encrypt data using symmetric keys instead of certificates or asymmetric keys.</span></span>  
  
-   <span data-ttu-id="deca6-111">데이터베이스 마스터 키는 서비스 마스터 키로 보호됩니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-111">Database master keys are protected by the Service Master Key.</span></span> <span data-ttu-id="deca6-112">서비스 마스터 키는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 설치 프로그램에 의해 생성되며 Windows DPAPI(데이터 보호 API)를 사용하여 암호화됩니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-112">The Service Master Key is created by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] setup and is encrypted with the Windows Data Protection API (DPAPI).</span></span>  
  
-   <span data-ttu-id="deca6-113">추가 계층을 쌓는 다른 암호화 계층도 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-113">Other encryption hierarchies stacking additional layers are possible.</span></span>  
  
-   <span data-ttu-id="deca6-114">EKM(확장 가능 키 관리) 모듈은 SQL Server 외부에 대칭 키나 비대칭 키를 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-114">An Extensible Key Management (EKM) module holds symmetric or asymmetric keys outside of SQL Server.</span></span>  
  
-   <span data-ttu-id="deca6-115">TDE(투명한 데이터 암호화)에서는 데이터베이스 암호화 키라는 대칭 키를 사용해야 합니다. 이 키는 master 데이터베이스의 데이터베이스 마스터 키로 보호되는 인증서 또는 EKM에 저장된 비대칭 키로 보호됩니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-115">Transparent Data Encryption (TDE) must use a symmetric key called the database encryption key which is protected by either a certificate protected by the database master key of the master database, or by an asymmetric key stored in an EKM.</span></span>  
  
-   <span data-ttu-id="deca6-116">서비스 마스터 키 및 모든 데이터베이스 마스터 키는 대칭 키입니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-116">The Service Master Key and all Database Master Keys are symmetric keys.</span></span>  
  
 <span data-ttu-id="deca6-117">다음 그림에서는 같은 정보를 서로 다른 방법으로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-117">The following illustration shows the same information in an alternative manner.</span></span>  
  
 <span data-ttu-id="deca6-118">![일부 암호화 조합을 휠로 표시합니다.](../../../database-engine/media/encryption-hierarchy-wheel.gif "일부 암호화 조합을 휠로 표시합니다.")</span><span class="sxs-lookup"><span data-stu-id="deca6-118">![Displays some encryption combinations in a wheel.](../../../database-engine/media/encryption-hierarchy-wheel.gif "Displays some encryption combinations in a wheel.")</span></span>  
  
 <span data-ttu-id="deca6-119">이 다이어그램에서는 다음과 같은 추가 개념을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-119">This diagram illustrates the following additional concepts:</span></span>  
  
-   <span data-ttu-id="deca6-120">이 그림에서 화살표는 일반적인 암호화 계층을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-120">In this illustration, arrows indicate common encryption hierarchies.</span></span>  
  
-   <span data-ttu-id="deca6-121">EKM의 대칭 및 비대칭 키는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 저장된 대칭 키 및 비대칭 키에 대한 액세스를 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-121">Symmetric and asymmetric keys in the EKM can protect access to the symmetric and asymmetric keys stored in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="deca6-122">EKM에 연결된 점선은 EKM의 키가 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 저장된 대칭 키 및 비대칭 키를 대체할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-122">The dotted line associated with EKM indicates that keys in the EKM could replace the symmetric and asymmetric keys stored in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="encryption-mechanisms"></a><span data-ttu-id="deca6-123">암호화 메커니즘</span><span class="sxs-lookup"><span data-stu-id="deca6-123">Encryption Mechanisms</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="deca6-124">는 다음과 같은 암호화 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-124">provides the following mechanisms for encryption:</span></span>  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="deca6-125">함수</span><span class="sxs-lookup"><span data-stu-id="deca6-125">functions</span></span>  
  
-   <span data-ttu-id="deca6-126">비대칭 키</span><span class="sxs-lookup"><span data-stu-id="deca6-126">Asymmetric keys</span></span>  
  
-   <span data-ttu-id="deca6-127">대칭 키</span><span class="sxs-lookup"><span data-stu-id="deca6-127">Symmetric keys</span></span>  
  
-   <span data-ttu-id="deca6-128">인증서</span><span class="sxs-lookup"><span data-stu-id="deca6-128">Certificates</span></span>  
  
-   <span data-ttu-id="deca6-129">투명한 데이터 암호화</span><span class="sxs-lookup"><span data-stu-id="deca6-129">Transparent Data Encryption</span></span>  
  
### <a name="transact-sql-functions"></a><span data-ttu-id="deca6-130">Transact-SQL 함수</span><span class="sxs-lookup"><span data-stu-id="deca6-130">Transact-SQL Functions</span></span>  
 <span data-ttu-id="deca6-131">개별 항목은 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 함수를 사용하여 삽입 또는 업데이트할 때 암호화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-131">Individual items can be encrypted as they are inserted or updated using [!INCLUDE[tsql](../../../includes/tsql-md.md)] functions.</span></span> <span data-ttu-id="deca6-132">자세한 내용은 [ENCRYPTBYPASSPHRASE&#40;Transact-SQL&#41;](/sql/t-sql/functions/encryptbypassphrase-transact-sql) 및 [DECRYPTBYPASSPHRASE&#40;Transact-SQL&#41;](/sql/t-sql/functions/decryptbypassphrase-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="deca6-132">For more information, see [ENCRYPTBYPASSPHRASE &#40;Transact-SQL&#41;](/sql/t-sql/functions/encryptbypassphrase-transact-sql) and [DECRYPTBYPASSPHRASE &#40;Transact-SQL&#41;](/sql/t-sql/functions/decryptbypassphrase-transact-sql).</span></span>  
  
### <a name="certificates"></a><span data-ttu-id="deca6-133">인증서</span><span class="sxs-lookup"><span data-stu-id="deca6-133">Certificates</span></span>  
 <span data-ttu-id="deca6-134">일반적으로 인증서라고도 부르는 퍼블릭 키 인증서는 해당 프라이빗 키를 보유하는 사람, 디바이스 또는 서비스의 ID에 퍼블릭 키 값을 바인딩하는 디지털 서명 문입니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-134">A public key certificate, usually just called a certificate, is a digitally-signed statement that binds the value of a public key to the identity of the person, device, or service that holds the corresponding private key.</span></span> <span data-ttu-id="deca6-135">인증서는 CA(인증 기관)에 의해 발행 및 서명됩니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-135">Certificates are issued and signed by a certification authority (CA).</span></span> <span data-ttu-id="deca6-136">CA로부터 인증서를 받는 엔터티는 해당 인증서의 주체입니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-136">The entity that receives a certificate from a CA is the subject of that certificate.</span></span> <span data-ttu-id="deca6-137">일반적으로 인증서에는 다음과 같은 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-137">Typically, certificates contain the following information.</span></span>  
  
-   <span data-ttu-id="deca6-138">주체의 공개 키</span><span class="sxs-lookup"><span data-stu-id="deca6-138">The public key of the subject.</span></span>  
  
-   <span data-ttu-id="deca6-139">이름 및 전자 메일 주소와 같은 주체에 대한 식별 정보</span><span class="sxs-lookup"><span data-stu-id="deca6-139">The identifier information of the subject, such as the name and e-mail address.</span></span>  
  
-   <span data-ttu-id="deca6-140">유효 기간.</span><span class="sxs-lookup"><span data-stu-id="deca6-140">The validity period.</span></span> <span data-ttu-id="deca6-141">이 값은 인증서가 유효한 것으로 고려되는 기간입니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-141">This is the length of time that the certificate is considered valid.</span></span>  
  
     <span data-ttu-id="deca6-142">인증서는 인증서 내에 지정된 기간 동안만 유효합니다. 모든 인증서에는 **Valid From** 및 **Valid To** 날짜가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-142">A certificate is valid only for the period of time specified within it; every certificate contains **Valid From** and **Valid To** dates.</span></span> <span data-ttu-id="deca6-143">이러한 날짜는 유효 기간의 범위를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-143">These dates set the boundaries of the validity period.</span></span> <span data-ttu-id="deca6-144">인증서의 유효 기간이 지난 경우 만료된 인증서의 주체가 새로운 인증서를 요청해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-144">When the validity period for a certificate has passed, a new certificate must be requested by the subject of the now-expired certificate.</span></span>  
  
-   <span data-ttu-id="deca6-145">발행자 식별자 정보</span><span class="sxs-lookup"><span data-stu-id="deca6-145">Issuer identifier information.</span></span>  
  
-   <span data-ttu-id="deca6-146">발행자의 디지털 서명</span><span class="sxs-lookup"><span data-stu-id="deca6-146">The digital signature of the issuer.</span></span>  
  
     <span data-ttu-id="deca6-147">이 서명은 공개 키와 주체의 식별자 정보 사이의 바인딩에 대한 유효성을 증명합니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-147">This signature attests to the validity of the binding between the public key and the identifier information of the subject.</span></span> <span data-ttu-id="deca6-148">정보를 디지털로 서명하는 프로세스에는 정보뿐만 아니라 발송자가 보유하고 있는 일부 기밀 정보를 서명이라는 태그로 변환하는 과정이 수반됩니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-148">(The process of digitally signing information entails transforming the information, as well as some secret information held by the sender, into a tag called a signature.)</span></span>  
  
 <span data-ttu-id="deca6-149">인증서의 기본 이점은 호스트에서 개별 주체에 대한 일련의 암호를 유지 관리할 필요가 없다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-149">A primary benefit of certificates is that they relieve hosts of the need to maintain a set of passwords for individual subjects.</span></span> <span data-ttu-id="deca6-150">그 대신 호스트가 인증서 발행자에 대한 트러스트를 설정하기만 하면 인증서 발행자는 인증서를 무제한적으로 서명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-150">Instead, the host merely establishes trust in a certificate issuer, which may then sign an unlimited number of certificates.</span></span>  
  
 <span data-ttu-id="deca6-151">보안 웹 서버와 같은 호스트가 발행자를 트러스트된 루트 기관으로 지명하면 발행자가 발행하는 인증서에 대한 바인딩을 구성하는 데 사용된 정책도 호스트에서 암시적으로 트러스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-151">When a host, such as a secure Web server, designates an issuer as a trusted root authority, the host implicitly trusts the policies that the issuer has used to establish the bindings of certificates it issues.</span></span> <span data-ttu-id="deca6-152">실제로 호스트는 발행자가 인증서 주체의 ID를 확인한 것으로 트러스트합니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-152">In effect, the host trusts that the issuer has verified the identity of the certificate subject.</span></span> <span data-ttu-id="deca6-153">호스트는 발행자의 공개 키가 포함된 자체 서명된 발행자의 인증서를 호스트 컴퓨터의 트러스트된 루트 인증 기관 인증서 저장소에 두어 발행자를 트러스트된 루트 기관으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-153">A host designates an issuer as a trusted root authority by putting the self-signed certificate of the issuer, which contains the public key of the issuer, into the trusted root certification authority certificate store of the host computer.</span></span> <span data-ttu-id="deca6-154">중간 또는 종속 인증 기관은 트러스트된 루트 인증 기관으로부터 유효한 인증 경로가 있는 경우에만 트러스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-154">Intermediate or subordinate certification authorities are trusted only if they have a valid certification path from a trusted root certification authority.</span></span>  
  
 <span data-ttu-id="deca6-155">발행자는 인증서가 만료되기 전에 인증서를 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-155">The issuer can revoke a certificate before it expires.</span></span> <span data-ttu-id="deca6-156">인증서를 취소하면 인증서에 삽입된 ID에 대한 공개 키 바인딩이 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-156">Revocation cancels the binding of a public key to an identity that is asserted in the certificate.</span></span> <span data-ttu-id="deca6-157">각 발행자는 특정 인증서의 유효성을 검사할 때 프로그램에서 사용할 수 있는 인증서 취소 목록을 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-157">Each issuer maintains a certificate revocation list that can be used by programs when they are checking the validity of any given certificate.</span></span>  
  
 <span data-ttu-id="deca6-158">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에서 만든 자체 서명된 인증서는 X.509 표준을 따르며 X.509 v1 필드를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-158">The self-signed certificates created by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] follow the X.509 standard and support the X.509 v1 fields.</span></span>  
  
### <a name="asymmetric-keys"></a><span data-ttu-id="deca6-159">비대칭 키</span><span class="sxs-lookup"><span data-stu-id="deca6-159">Asymmetric Keys</span></span>  
 <span data-ttu-id="deca6-160">비대칭 키는 프라이빗 키와 해당 퍼블릭 키로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-160">An asymmetric key is made up of a private key and the corresponding public key.</span></span> <span data-ttu-id="deca6-161">각 키는 다른 사람이 암호화한 데이터를 암호 해독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-161">Each key can decrypt data encrypted by the other.</span></span> <span data-ttu-id="deca6-162">비대칭 암호화 및 암호 해독은 비교적 리소스 소모가 많지만 대칭 암호화보다 높은 보안 수준을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-162">Asymmetric encryption and decryption are relatively resource-intensive, but they provide a higher level of security than symmetric encryption.</span></span> <span data-ttu-id="deca6-163">비대칭 키는 데이터베이스의 스토리지에 대한 대칭 키를 암호화하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-163">An asymmetric key can be used to encrypt a symmetric key for storage in a database.</span></span>  
  
### <a name="symmetric-keys"></a><span data-ttu-id="deca6-164">대칭 키</span><span class="sxs-lookup"><span data-stu-id="deca6-164">Symmetric Keys</span></span>  
 <span data-ttu-id="deca6-165">대칭 키는 암호화 및 암호 해독에 대해 사용되는 하나의 키입니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-165">A symmetric key is one key that is used for both encryption and decryption.</span></span> <span data-ttu-id="deca6-166">대칭 키를 사용하면 암호화 및 암호 해독을 빠르게 수행할 수 있으며 데이터베이스의 중요한 데이터를 일상적으로 사용하는 데 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-166">Encryption and decryption by using a symmetric key is fast, and suitable for routine use with sensitive data in the database.</span></span>  
  
### <a name="transparent-data-encryption"></a><span data-ttu-id="deca6-167">투명한 데이터 암호화</span><span class="sxs-lookup"><span data-stu-id="deca6-167">Transparent Data Encryption</span></span>  
 <span data-ttu-id="deca6-168">TDE(투명한 데이터 암호화)는 대칭 키를 사용한 특수한 암호화 형태입니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-168">Transparent Data Encryption (TDE) is a special case of encryption using a symmetric key.</span></span> <span data-ttu-id="deca6-169">TDE는 데이터베이스 암호화 키라는 대칭 키를 사용하여 전체 데이터베이스를 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-169">TDE encrypts an entire database using that symmetric key called the database encryption key.</span></span> <span data-ttu-id="deca6-170">데이터베이스 암호화 키는 데이터베이스 마스터 키 또는 EKM 모듈에 저장된 비대칭 키로 보호되는 다른 키 또는 인증서로 보호됩니다.</span><span class="sxs-lookup"><span data-stu-id="deca6-170">The database encryption key is protected by other keys or certificates which are protected either by the database master key or by an asymmetric key stored in an EKM module.</span></span> <span data-ttu-id="deca6-171">자세한 내용은 [TDE&#40;투명한 데이터 암호화&#41;](transparent-data-encryption.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="deca6-171">For more information, see [Transparent Data Encryption &#40;TDE&#41;](transparent-data-encryption.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="deca6-172">관련 내용</span><span class="sxs-lookup"><span data-stu-id="deca6-172">Related Content</span></span>  
 [<span data-ttu-id="deca6-173">SQL Server 보안 설정</span><span class="sxs-lookup"><span data-stu-id="deca6-173">Securing SQL Server</span></span>](../securing-sql-server.md)  
  
 [<span data-ttu-id="deca6-174">보안 함수&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="deca6-174">Security Functions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/security-functions-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="deca6-175">참고 항목</span><span class="sxs-lookup"><span data-stu-id="deca6-175">See Also</span></span>  
 <span data-ttu-id="deca6-176">[사용 권한 계층&#40;데이터베이스 엔진&#41;](../permissions-hierarchy-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="deca6-176">[Permissions Hierarchy &#40;Database Engine&#41;](../permissions-hierarchy-database-engine.md) </span></span>  
 [<span data-ttu-id="deca6-177">보안 개체</span><span class="sxs-lookup"><span data-stu-id="deca6-177">Securables</span></span>](../securables.md)  
  
  
