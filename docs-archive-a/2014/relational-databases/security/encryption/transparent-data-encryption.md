---
title: TDE(투명한 데이터 암호화) | Microsoft 문서
ms.custom: ''
ms.date: 11/23/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Transparent Data Encryption
- database encryption key, about
- TDE
- database encryption key
- TDE, about
- Transparent Data Encryption, about
- encryption [SQL Server], transparent data encryption
ms.assetid: c75d0d4b-4008-4e71-9a9d-cee2a566bd3b
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: a8118f0781d7c9e3d839c029c6bdaf8b01e074b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651606"
---
# <a name="transparent-data-encryption-tde"></a><span data-ttu-id="5cf2c-102">TDE(투명한 데이터 암호화)</span><span class="sxs-lookup"><span data-stu-id="5cf2c-102">Transparent Data Encryption (TDE)</span></span>
  <span data-ttu-id="5cf2c-103">*투명한 데이터 암호화* (TDE)는 사용하지 않는 데이터 암호화라고 하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 및 [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] 데이터 파일을 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-103">*Transparent Data Encryption* (TDE) encrypts [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] data files, known as encrypting data at rest.</span></span> <span data-ttu-id="5cf2c-104">보안 시스템 설계, 중요한 자산 암호화 및 데이터베이스 서버 방화벽 구축과 같은 데이터베이스 보호에 도움이 되는 몇 가지 예방 조치를 취할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-104">You can take several precautions to help secure the database such as designing a secure system, encrypting confidential assets, and building a firewall around the database servers.</span></span> <span data-ttu-id="5cf2c-105">그러나 물리적 미디어(예: 드라이브 또는 백업 테이프)가 도난되는 시나리오에서는 악의적인 사용자가 데이터베이스를 단순히 복원하거나 연결하여 데이터를 찾아 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-105">However, in a scenario where the physical media (such as drives or backup tapes) are stolen, a malicious party can just restore or attach the database and browse the data.</span></span> <span data-ttu-id="5cf2c-106">한 가지 해결 방법은 데이터베이스의 중요한 데이터를 암호화하고 인증서와 함께 데이터를 암호화하는 데 사용된 키를 보호하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-106">One solution is to encrypt the sensitive data in the database and protect the keys that are used to encrypt the data with a certificate.</span></span> <span data-ttu-id="5cf2c-107">이 경우 키가 없으면 누구도 데이터를 사용할 수 없지만 이러한 보호 방법은 사전에 계획해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-107">This prevents anyone without the keys from using the data, but this kind of protection must be planned in advance.</span></span>

 <span data-ttu-id="5cf2c-108">TDE는 데이터 및 로그 파일에 대한 실시간 I/O 암호화 및 암호 해독을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-108">TDE performs real-time I/O encryption and decryption of the data and log files.</span></span> <span data-ttu-id="5cf2c-109">암호화에는 복구 중에 사용 가능하도록 데이터베이스 부트 레코드에 저장된 DEK(데이터베이스 암호화 키)가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-109">The encryption uses a database encryption key (DEK), which is stored in the database boot record for availability during recovery.</span></span> <span data-ttu-id="5cf2c-110">DEK는 서버의 master 데이터베이스에 저장된 인증서 또는 EKM 모듈로 보호되는 비대칭 키를 사용하여 보호되는 대칭 키입니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-110">The DEK is a symmetric key secured by using a certificate stored in the master database of the server or an asymmetric key protected by an EKM module.</span></span> <span data-ttu-id="5cf2c-111">TDE는 데이터 및 로그 파일을 의미하는 "유휴" 데이터를 보호하고</span><span class="sxs-lookup"><span data-stu-id="5cf2c-111">TDE protects data "at rest", meaning the data and log files.</span></span> <span data-ttu-id="5cf2c-112">다양한 업계에서 확립된 법, 규정 및 지침에 부합하는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-112">It provides the ability to comply with many laws, regulations, and guidelines established in various industries.</span></span> <span data-ttu-id="5cf2c-113">이를 통해 소프트웨어 개발자는 AES 및 3DES 암호화 알고리즘을 사용하여 기존의 애플리케이션을 변경하지 않고 데이터를 암호화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-113">This enables software developers to encrypt data by using AES and 3DES encryption algorithms without changing existing applications.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="5cf2c-114">TDE에서는 통신 채널을 통한 암호화를 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-114">TDE does not provide encryption across communication channels.</span></span> <span data-ttu-id="5cf2c-115">통신 채널을 통해 데이터를 암호화하는 방법은 [데이터베이스 엔진에 암호화 연결 사용&#40;SQL Server 구성 관리자&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-115">For more information about how to encrypt data across communication channels, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).</span></span>
> 
>  <span data-ttu-id="5cf2c-116">**관련 항목:**</span><span class="sxs-lookup"><span data-stu-id="5cf2c-116">**Related topics:**</span></span>
> 
>  -   [<span data-ttu-id="5cf2c-117">Azure SQL Database를 사용한 투명한 데이터 암호화</span><span class="sxs-lookup"><span data-stu-id="5cf2c-117">Transparent Data Encryption with Azure SQL Database</span></span>](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md)
> -   [<span data-ttu-id="5cf2c-118">다른 SQL Server로 TDE 보호 데이터베이스 이동</span><span class="sxs-lookup"><span data-stu-id="5cf2c-118">Move a TDE Protected Database to Another SQL Server</span></span>](move-a-tde-protected-database-to-another-sql-server.md)
> -   [<span data-ttu-id="5cf2c-119">EKM을 사용 하 여 TDE 사용</span><span class="sxs-lookup"><span data-stu-id="5cf2c-119">Enable TDE Using EKM</span></span>](enable-tde-on-sql-server-using-ekm.md)

## <a name="about-tde"></a><span data-ttu-id="5cf2c-120">TDE 정보</span><span class="sxs-lookup"><span data-stu-id="5cf2c-120">About TDE</span></span>
 <span data-ttu-id="5cf2c-121">데이터베이스 파일의 암호화는 페이지 수준에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-121">Encryption of the database file is performed at the page level.</span></span> <span data-ttu-id="5cf2c-122">암호화된 데이터베이스의 페이지는 암호화된 후 디스크에 작성되고 메모리로 읽어 들일 때 암호가 해독됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-122">The pages in an encrypted database are encrypted before they are written to disk and decrypted when read into memory.</span></span> <span data-ttu-id="5cf2c-123">TDE로 암호화된 데이터베이스의 크기가 증가되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-123">TDE does not increase the size of the encrypted database.</span></span>

 <span data-ttu-id="5cf2c-124">**적용 되는 정보[!INCLUDE[ssSDS](../../../includes/sssds-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="5cf2c-124">**Information applicable to [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]**</span></span>

 <span data-ttu-id="5cf2c-125">[!INCLUDE[sqldbesa](../../../includes/sqldbesa-md.md)] V12 ([일부 지역에서는 미리 보기](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag))에서 TDE를 사용하는 경우, master 데이터베이스에 저장된 서버 수준 인증서가 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]에 의해 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-125">When using TDE with [!INCLUDE[sqldbesa](../../../includes/sqldbesa-md.md)] V12  ([Preview in some regions](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)) the server-level certificate stored in the master database is automatically created for you by [!INCLUDE[ssSDS](../../../includes/sssds-md.md)].</span></span> <span data-ttu-id="5cf2c-126">[!INCLUDE[ssSDS](../../../includes/sssds-md.md)] 의 TDE 데이터베이스를 이동하려면 데이터베이스 암호를 해독하고, 데이터베이스를 이동한 후, 대상 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]에서 TDE를 다시 사용하도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-126">To move a TDE database on [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] you must decrypt the database, move the database, and then re-enable TDE on the destination [!INCLUDE[ssSDS](../../../includes/sssds-md.md)].</span></span> <span data-ttu-id="5cf2c-127">[!INCLUDE[ssSDS](../../../includes/sssds-md.md)]의 TDE에 대한 단계별 지침은 [Transparent Data Encryption with Azure SQL Database](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-127">For step-by-step instructions for TDE on [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], see [Transparent Data Encryption with Azure SQL Database](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md).</span></span>

 <span data-ttu-id="5cf2c-128">TDE 상태 미리보기는 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] 의 버전 제품군 V12가 현재 일반 가용성 상태에 있다고 알려진 지역의 하위 집합에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-128">The preview of status of TDE applies even in the subset of geographic regions where version family V12 of [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] is announced as now being in general availability status.</span></span> <span data-ttu-id="5cf2c-129">[!INCLUDE[ssSDS](../../../includes/sssds-md.md)] 에 대한 TDE는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 이(가) TDE가 미리보기에서 GA로 승격되었음을 알릴 때까지 제품 데이터베이스에서 사용하기 위한 것이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-129">TDE for [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] is not intended for use in production databases until [!INCLUDE[msCoName](../../../includes/msconame-md.md)] announces that TDE is promoted from preview to GA.</span></span> <span data-ttu-id="5cf2c-130">[!INCLUDE[ssSDS](../../../includes/sssds-md.md)] V12에 대한 자세한 내용은 [Azure SQL Database의 새로운 소식](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/)을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-130">For more information about [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] V12, see [What's new in Azure SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/).</span></span>

 <span data-ttu-id="5cf2c-131">**적용 되는 정보[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="5cf2c-131">**Information applicable to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]**</span></span>

 <span data-ttu-id="5cf2c-132">보안이 설정된 후 올바른 인증서를 사용하여 데이터베이스를 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-132">After it is secured, the database can be restored by using the correct certificate.</span></span> <span data-ttu-id="5cf2c-133">인증서에 대한 자세한 내용은 [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-133">For more information about certificates, see [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md).</span></span>

 <span data-ttu-id="5cf2c-134">TDE를 설정할 경우 인증서 및 인증서와 연결된 프라이빗 키를 즉시 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-134">When enabling TDE, you should immediately back up the certificate and the private key associated with the certificate.</span></span> <span data-ttu-id="5cf2c-135">인증서를 사용할 수 없게 되거나 다른 서버에서 데이터베이스를 복원하거나 연결해야 할 경우 인증서와 프라이빗 키의 백업본이 있어야 합니다. 그렇지 않으면 데이터베이스를 열 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-135">If the certificate ever becomes unavailable or if you must restore or attach the database on another server, you must have backups of both the certificate and the private key or you will not be able to open the database.</span></span> <span data-ttu-id="5cf2c-136">데이터베이스에서 TDE를 해제하더라도 인증서 암호화는 그대로 유지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-136">The encrypting certificate should be retained even if TDE is no longer enabled on the database.</span></span> <span data-ttu-id="5cf2c-137">데이터베이스가 암호화되지 않더라도 트랜잭션 로그 부분은 그대로 보호될 수 있으며, 일부 작업의 경우 데이터베이스 전체 백업을 수행할 때까지는 인증서가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-137">Even though the database is not encrypted, parts of the transaction log may still remain protected, and the certificate may be needed for some operations until the full backup of the database is performed.</span></span> <span data-ttu-id="5cf2c-138">만료 날짜가 지난 인증서도 여전히 데이터를 TDE로 암호화하고 해독하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-138">A certificate that has exceeded its expiration date can still be used to encrypt and decrypt data with TDE.</span></span>

 <span data-ttu-id="5cf2c-139">**암호화 계층**</span><span class="sxs-lookup"><span data-stu-id="5cf2c-139">**Encryption Hierarchy**</span></span>

 <span data-ttu-id="5cf2c-140">다음 그림에서는 TDE 암호화의 아키텍처를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-140">The following illustration shows the architecture of TDE encryption.</span></span> <span data-ttu-id="5cf2c-141">데이터베이스 수준 항목만(데이터베이스 암호화 키 및 ALTER DATABASE 부분은 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]에서 TDE를 사용하는 경우 사용자가 구성활 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-141">Only the database level items (the database encryption key and ALTER DATABASE portions are user-configurable when using TDE on [!INCLUDE[ssSDS](../../../includes/sssds-md.md)].</span></span>

 <span data-ttu-id="5cf2c-142">![이 항목에서 설명하는 계층 구조를 표시합니다.](../../../database-engine/media/tde-architecture.gif "이 항목에서 설명하는 계층 구조를 표시합니다.")</span><span class="sxs-lookup"><span data-stu-id="5cf2c-142">![Displays the hierarchy described in the topic.](../../../database-engine/media/tde-architecture.gif "Displays the hierarchy described in the topic.")</span></span>

## <a name="using-transparent-data-encryption"></a><span data-ttu-id="5cf2c-143">투명한 데이터 암호화 사용</span><span class="sxs-lookup"><span data-stu-id="5cf2c-143">Using Transparent Data Encryption</span></span>
 <span data-ttu-id="5cf2c-144">TDE를 사용하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-144">To use TDE, follow these steps.</span></span>

||
|-|
|<span data-ttu-id="5cf2c-145">**적용 대상**: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5cf2c-145">**Applies to**: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>|

-   <span data-ttu-id="5cf2c-146">마스터 키 만들기</span><span class="sxs-lookup"><span data-stu-id="5cf2c-146">Create a master key</span></span>

-   <span data-ttu-id="5cf2c-147">마스터 키로 보호되는 인증서를 만들거나 얻기</span><span class="sxs-lookup"><span data-stu-id="5cf2c-147">Create or obtain a certificate protected by the master key</span></span>

-   <span data-ttu-id="5cf2c-148">데이터베이스 암호화 키를 만들고 인증서로 키 보호</span><span class="sxs-lookup"><span data-stu-id="5cf2c-148">Create a database encryption key and protect it by the certificate</span></span>

-   <span data-ttu-id="5cf2c-149">암호화를 사용하도록 데이터베이스 설정</span><span class="sxs-lookup"><span data-stu-id="5cf2c-149">Set the database to use encryption</span></span>

 <span data-ttu-id="5cf2c-150">다음 예에서는 `AdventureWorks2012` 라는 서버에 설치된 인증서를 사용하여 `MyServerCert`데이터베이스를 암호화하고 암호를 해독하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-150">The following example illustrates encrypting and decrypting the `AdventureWorks2012` database using a certificate installed on the server named `MyServerCert`.</span></span>

```
USE master;
GO
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<UseStrongPasswordHere>';
go
CREATE CERTIFICATE MyServerCert WITH SUBJECT = 'My DEK Certificate';
go
USE AdventureWorks2012;
GO
CREATE DATABASE ENCRYPTION KEY
WITH ALGORITHM = AES_128
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;
GO
ALTER DATABASE AdventureWorks2012
SET ENCRYPTION ON;
GO
```

 <span data-ttu-id="5cf2c-151">암호화 및 암호 해독 작업은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 의해 백그라운드 스레드로 예약됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-151">The encryption and decryption operations are scheduled on background threads by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5cf2c-152">이 항목의 뒷부분에 나오는 카탈로그 뷰 및 동적 관리 뷰를 사용하여 이러한 작업의 상태를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-152">You can view the status of these operations using the catalog views and dynamic management views in the list that appears later in this topic.</span></span>

> [!CAUTION]
>  <span data-ttu-id="5cf2c-153">TDE가 사용된 데이터베이스의 백업 파일도 데이터베이스 암호화 키를 사용하여 암호화됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-153">Backup files of databases that have TDE enabled are also encrypted by using the database encryption key.</span></span> <span data-ttu-id="5cf2c-154">따라서 이러한 백업 파일을 복원하려면 데이터베이스 암호화 키를 보호하는 인증서를 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-154">As a result, when you restore these backups, the certificate protecting the database encryption key must be available.</span></span> <span data-ttu-id="5cf2c-155">즉, 데이터베이스 백업뿐만 아니라 데이터 손실을 방지하기 위해 서버 인증서의 백업도 유지 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-155">This means that in addition to backing up the database, you have to make sure that you maintain backups of the server certificates to prevent data loss.</span></span> <span data-ttu-id="5cf2c-156">인증서를 더 이상 사용할 수 없을 경우 데이터 손실이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-156">Data loss will result if the certificate is no longer available.</span></span> <span data-ttu-id="5cf2c-157">자세한 내용은 [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-157">For more information, see [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md).</span></span>

## <a name="commands-and-functions"></a><span data-ttu-id="5cf2c-158">명령 및 함수</span><span class="sxs-lookup"><span data-stu-id="5cf2c-158">Commands and Functions</span></span>
 <span data-ttu-id="5cf2c-159">TDE 인증서는 다음 문에서 수락된 데이터베이스 마스터 키로 암호화되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-159">The TDE certificates must be encrypted by the database master key to be accepted by the following statements.</span></span> <span data-ttu-id="5cf2c-160">이 인증서가 암호만으로 암호화되면 문에서는 암호기로서 이것을 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-160">If they are encrypted by password only, the statements will reject them as encryptors.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="5cf2c-161">TDE에서 인증서가 사용된 후 암호로 보호되도록 인증서가 변경되면 다시 시작한 다음에는 데이터베이스에 액세스할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-161">Altering the certificates to be password-protected after they are used by TDE will cause the database to become inaccessible after a restart.</span></span>

 <span data-ttu-id="5cf2c-162">다음 표에서는 TDE 명령 및 함수에 대한 링크와 설명을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-162">The following table provides links and explanations of TDE commands and functions.</span></span>

|<span data-ttu-id="5cf2c-163">명령 또는 함수</span><span class="sxs-lookup"><span data-stu-id="5cf2c-163">Command or function</span></span>|<span data-ttu-id="5cf2c-164">목적</span><span class="sxs-lookup"><span data-stu-id="5cf2c-164">Purpose</span></span>|
|-------------------------|-------------|
|[<span data-ttu-id="5cf2c-165">CREATE DATABASE ENCRYPTION KEY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5cf2c-165">CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-encryption-key-transact-sql)|<span data-ttu-id="5cf2c-166">데이터베이스 암호화에 사용할 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-166">Creates a key that is used to encrypt a database.</span></span>|
|[<span data-ttu-id="5cf2c-167">ALTER DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5cf2c-167">ALTER DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-encryption-key-transact-sql)|<span data-ttu-id="5cf2c-168">데이터베이스 암호화에 사용할 키를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-168">Changes the key that is used to encrypt a database.</span></span>|
|[<span data-ttu-id="5cf2c-169">DROP DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5cf2c-169">DROP DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-database-transact-sql)|<span data-ttu-id="5cf2c-170">데이터베이스 암호화에 사용한 키를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-170">Removes the key that was used to encrypt a database.</span></span>|
|[<span data-ttu-id="5cf2c-171">ALTER DATABASE SET 옵션&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5cf2c-171">ALTER DATABASE SET Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-set-options)|<span data-ttu-id="5cf2c-172">TDE를 설정하는 데 사용된 `ALTER DATABASE` 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-172">Explains the `ALTER DATABASE` option that is used to enable TDE.</span></span>|

## <a name="catalog-views-and-dynamic-management-views"></a><span data-ttu-id="5cf2c-173">카탈로그 뷰 및 동적 관리 뷰</span><span class="sxs-lookup"><span data-stu-id="5cf2c-173">Catalog Views and Dynamic Management Views</span></span>
 <span data-ttu-id="5cf2c-174">다음 표에서는 TDE 카탈로그 뷰 및 동적 관리 뷰를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-174">The following table shows TDE catalog views and dynamic management views.</span></span>

|<span data-ttu-id="5cf2c-175">카탈로그 뷰 또는 동적 관리 뷰</span><span class="sxs-lookup"><span data-stu-id="5cf2c-175">Catalog view or dynamic management view</span></span>|<span data-ttu-id="5cf2c-176">목적</span><span class="sxs-lookup"><span data-stu-id="5cf2c-176">Purpose</span></span>|
|---------------------------------------------|-------------|
|[<span data-ttu-id="5cf2c-177">sys.databases&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5cf2c-177">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)|<span data-ttu-id="5cf2c-178">데이터베이스 정보를 보여 주는 카탈로그 뷰입니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-178">Catalog view that displays database information.</span></span>|
|[<span data-ttu-id="5cf2c-179">sys.certificates&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5cf2c-179">sys.certificates &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql)|<span data-ttu-id="5cf2c-180">데이터베이스의 인증서를 보여 주는 카탈로그 뷰입니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-180">Catalog view that shows the certificates in a database.</span></span>|
|[<span data-ttu-id="5cf2c-181">sys.dm_database_encryption_keys&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5cf2c-181">sys.dm_database_encryption_keys &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)|<span data-ttu-id="5cf2c-182">데이터베이스에 사용된 암호화 키 및 데이터베이스 암호화의 상태에 대한 정보를 보여 주는 동적 관리 뷰입니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-182">Dynamic management view that provides information about the encryption keys used in a database, and the state of encryption of a database.</span></span>|

## <a name="permissions"></a><span data-ttu-id="5cf2c-183">사용 권한</span><span class="sxs-lookup"><span data-stu-id="5cf2c-183">Permissions</span></span>
 <span data-ttu-id="5cf2c-184">위에 표시된 표에서 설명한 것처럼 TDE의 기능 및 명령에는 각각의 사용 권한 요구 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-184">Each TDE feature and command has individual permission requirements, described in the tables shown earlier.</span></span>

 <span data-ttu-id="5cf2c-185">TDE와 관련된 메타데이터를 보려면 인증서에 대한 VIEW DEFINITION 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-185">Viewing the metadata involved with TDE requires the VIEW DEFINITION permission on the certificate.</span></span>

## <a name="considerations"></a><span data-ttu-id="5cf2c-186">고려 사항</span><span class="sxs-lookup"><span data-stu-id="5cf2c-186">Considerations</span></span>
 <span data-ttu-id="5cf2c-187">처리 중인 데이터베이스 암호화 작업에 대해 재암호화를 검색하는 동안에는 데이터베이스에 대한 유지 관리 작업이 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-187">While a re-encryption scan for a database encryption operation is in progress, maintenance operations to the database are disabled.</span></span> <span data-ttu-id="5cf2c-188">데이터베이스에 단일 사용자 모드 설정을 사용하여 유지 관리 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-188">You can use the single user mode setting for the database to perform the maintenance operation.</span></span> <span data-ttu-id="5cf2c-189">자세한 내용은 [단일 사용자 모드로 데이터베이스 설정](../../databases/set-a-database-to-single-user-mode.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-189">For more information, see [Set a Database to Single-user Mode](../../databases/set-a-database-to-single-user-mode.md).</span></span>

 <span data-ttu-id="5cf2c-190">sys.dm_database_encryption_keys 동적 관리 뷰를 사용하여 데이터베이스 암호화의 상태를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-190">You can find the state of the database encryption using the sys.dm_database_encryption_keys dynamic management view.</span></span> <span data-ttu-id="5cf2c-191">자세한 내용은 이 항목의 앞부분에 나오는 "카탈로그 뷰 및 동적 관리 뷰" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-191">For more information, see the "Catalog Views and Dynamic Management Views"section earlier in this topic).</span></span>

 <span data-ttu-id="5cf2c-192">TDE에서는 데이터베이스의 모든 파일 및 파일 그룹이 암호화됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-192">In TDE, all files and filegroups in the database are encrypted.</span></span> <span data-ttu-id="5cf2c-193">데이터베이스에 READ ONLY로 표시된 파일 그룹이 있는 경우 데이터베이스 암호화 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-193">If any filegroups in a database are marked READ ONLY, the database encryption operation will fail.</span></span>

 <span data-ttu-id="5cf2c-194">데이터베이스가 데이터베이스 미러링이나 로그 전달에 사용되고 있을 경우 두 데이터베이스 모두 암호화됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-194">If a database is being used in database mirroring or log shipping, both databases will be encrypted.</span></span> <span data-ttu-id="5cf2c-195">로그 트랜잭션은 암호화되어 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-195">The log transactions will be encrypted when sent between them.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="5cf2c-196">새로운 전체 텍스트 인덱스는 데이터베이스에 암호화가 설정될 때 암호화됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-196">Any new full-text indexes will be encrypted when a database is set for encryption.</span></span> <span data-ttu-id="5cf2c-197">이전에 작성된 전체 텍스트 인덱스는 업그레이드 중에 가져올 수 있으며 일단 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 로드된 데이터는 TDE로 암호화됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-197">Previously-created full-text indexes will be imported during upgrade and they will be in TDE after the data is loaded into [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5cf2c-198">한 열의 전체 텍스트 인덱스를 사용하도록 설정하면 전체 텍스트 인덱싱 검색 중에 열 데이터가 디스크에 일반 텍스트로 기록될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-198">Enabling a full-text index on a column can cause that column's data to be written in plain text onto the disk during a full-text indexing scan.</span></span> <span data-ttu-id="5cf2c-199">따라서 암호화된 중요 데이터에 대해서는 전체 텍스트 인덱스를 만들지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-199">We recommend that you do not create a full-text index on sensitive encrypted data.</span></span>

 <span data-ttu-id="5cf2c-200">암호화된 데이터는 암호화되지 않은 데이터보다 압축률이 크게 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-200">Encrypted data compresses significantly less than equivalent unencrypted data.</span></span> <span data-ttu-id="5cf2c-201">TDE를 사용하여 데이터베이스를 암호화하는 경우 백업 압축을 통해 백업 스토리지를 크게 압축하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-201">If TDE is used to encrypt a database, backup compression will not be able to significantly compress the backup storage.</span></span> <span data-ttu-id="5cf2c-202">따라서 TDE와 백업 압축을 함께 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-202">Therefore, using TDE and backup compression together is not recommended.</span></span>

### <a name="restrictions"></a><span data-ttu-id="5cf2c-203">제한 사항</span><span class="sxs-lookup"><span data-stu-id="5cf2c-203">Restrictions</span></span>
 <span data-ttu-id="5cf2c-204">초기 데이터베이스 암호화, 키 변경 또는 데이터베이스 암호 해독 중에는 다음 작업을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-204">The following operations are not allowed during initial database encryption, key change, or database decryption:</span></span>

-   <span data-ttu-id="5cf2c-205">데이터베이스의 파일 그룹에서 파일 삭제</span><span class="sxs-lookup"><span data-stu-id="5cf2c-205">Dropping a file from a filegroup in the database</span></span>

-   <span data-ttu-id="5cf2c-206">데이터베이스 삭제</span><span class="sxs-lookup"><span data-stu-id="5cf2c-206">Dropping the database</span></span>

-   <span data-ttu-id="5cf2c-207">데이터베이스를 오프라인으로 설정</span><span class="sxs-lookup"><span data-stu-id="5cf2c-207">Taking the database offline</span></span>

-   <span data-ttu-id="5cf2c-208">데이터베이스 분리</span><span class="sxs-lookup"><span data-stu-id="5cf2c-208">Detaching a database</span></span>

-   <span data-ttu-id="5cf2c-209">데이터베이스 또는 파일 그룹을 READ ONLY 상태로 전환</span><span class="sxs-lookup"><span data-stu-id="5cf2c-209">Transitioning a database or filegroup into a READ ONLY state</span></span>

 <span data-ttu-id="5cf2c-210">CREATE DATABASE ENCRYPTION KEY, ALTER DATABASE ENCRYPTION KEY, DROP DATABASE ENCRYPTION KEY 또는 ALTER DATABASE...SET ENCRYPTION 문 실행 중에는 다음 작업을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-210">The following operations are not allowed during the CREATE DATABASE ENCRYPTION KEY, ALTER DATABASE ENCRYPTION KEY, DROP DATABASE ENCRYPTION KEY, or ALTER DATABASE...SET ENCRYPTION statements.</span></span>

-   <span data-ttu-id="5cf2c-211">데이터베이스의 파일 그룹에서 파일 삭제</span><span class="sxs-lookup"><span data-stu-id="5cf2c-211">Dropping a file from a filegroup in the database.</span></span>

-   <span data-ttu-id="5cf2c-212">데이터베이스 삭제</span><span class="sxs-lookup"><span data-stu-id="5cf2c-212">Dropping the database.</span></span>

-   <span data-ttu-id="5cf2c-213">데이터베이스를 오프라인으로 설정</span><span class="sxs-lookup"><span data-stu-id="5cf2c-213">Taking the database offline.</span></span>

-   <span data-ttu-id="5cf2c-214">데이터베이스 분리</span><span class="sxs-lookup"><span data-stu-id="5cf2c-214">Detaching a database.</span></span>

-   <span data-ttu-id="5cf2c-215">데이터베이스 또는 파일 그룹을 READ ONLY 상태로 전환</span><span class="sxs-lookup"><span data-stu-id="5cf2c-215">Transitioning a database or filegroup into a READ ONLY state.</span></span>

-   <span data-ttu-id="5cf2c-216">ALTER DATABASE 명령 사용</span><span class="sxs-lookup"><span data-stu-id="5cf2c-216">Using an ALTER DATABASE command.</span></span>

-   <span data-ttu-id="5cf2c-217">데이터베이스 또는 데이터베이스 파일 백업 시작</span><span class="sxs-lookup"><span data-stu-id="5cf2c-217">Starting a database or database file backup.</span></span>

-   <span data-ttu-id="5cf2c-218">데이터베이스 또는 데이터베이스 파일 복원 시작</span><span class="sxs-lookup"><span data-stu-id="5cf2c-218">Starting a database or database file restore.</span></span>

-   <span data-ttu-id="5cf2c-219">스냅샷 만들기</span><span class="sxs-lookup"><span data-stu-id="5cf2c-219">Creating a snapshot.</span></span>

 <span data-ttu-id="5cf2c-220">다음 작업 또는 상태에서는 CREATE DATABASE ENCRYPTION KEY, ALTER DATABASE ENCRYPTION KEY, DROP DATABASE ENCRYPTION KEY 또는 ALTER DATABASE...SET ENCRYPTION 문을 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-220">The following operations or conditions will prevent the CREATE DATABASE ENCRYPTION KEY, ALTER DATABASE ENCRYPTION KEY, DROP DATABASE ENCRYPTION KEY, or ALTER DATABASE...SET ENCRYPTION statements.</span></span>

-   <span data-ttu-id="5cf2c-221">데이터베이스가 읽기 전용이거나 데이터베이스에 읽기 전용 파일 그룹이 포함된 경우</span><span class="sxs-lookup"><span data-stu-id="5cf2c-221">The database is read-only or has any read-only file groups.</span></span>

-   <span data-ttu-id="5cf2c-222">ALTER DATABASE 명령이 실행 중인 경우</span><span class="sxs-lookup"><span data-stu-id="5cf2c-222">An ALTER DATABASE command is executing.</span></span>

-   <span data-ttu-id="5cf2c-223">데이터 백업이 실행 중인 경우</span><span class="sxs-lookup"><span data-stu-id="5cf2c-223">Any data backup is running.</span></span>

-   <span data-ttu-id="5cf2c-224">데이터베이스가 오프라인이거나 복원 상태인 경우</span><span class="sxs-lookup"><span data-stu-id="5cf2c-224">The database is in an offline or restore condition.</span></span>

-   <span data-ttu-id="5cf2c-225">스냅샷이 진행 중인 경우</span><span class="sxs-lookup"><span data-stu-id="5cf2c-225">A snapshot is in progress.</span></span>

-   <span data-ttu-id="5cf2c-226">데이터베이스 유지 관리 태스크</span><span class="sxs-lookup"><span data-stu-id="5cf2c-226">Database maintenance tasks.</span></span>

 <span data-ttu-id="5cf2c-227">데이터베이스 파일을 만들 때 TDE가 사용하도록 설정되어 있으면 즉시 파일 초기화를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-227">When creating database files, instant file initialization is not available when TDE is enabled.</span></span>

 <span data-ttu-id="5cf2c-228">비대칭 키로 데이터베이스 암호화 키를 암호화하려면 비대칭 키가 확장 가능 키 관리 공급자에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-228">In order to encrypt the database encryption key with an asymmetric key, the asymmetric key must reside on an extensible key management provider.</span></span>

### <a name="transparent-data-encryption-and-transaction-logs"></a><span data-ttu-id="5cf2c-229">투명한 데이터 암호화 및 트랜잭션 로그</span><span class="sxs-lookup"><span data-stu-id="5cf2c-229">Transparent Data Encryption and Transaction Logs</span></span>
 <span data-ttu-id="5cf2c-230">TDE를 사용하도록 데이터베이스를 설정하면 가상 트랜잭션 로그의 남은 부분을 비우는 효과가 있어서 다음 가상 트랜잭션 로그를 강제로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-230">Enabling a database to use TDE has the effect of "zeroing out" the remaining part of the virtual transaction log to force the next virtual transaction log.</span></span> <span data-ttu-id="5cf2c-231">이렇게 하면 데이터베이스에 암호화가 설정된 후 트랜잭션 로그에 남아 있는 일반 텍스트가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-231">This guarantees that no clear text is left in the transaction logs after the database is set for encryption.</span></span> <span data-ttu-id="5cf2c-232">이 예에서와 같이 `encryption_state` 뷰의 `sys.dm_database_encryption_keys` 열을 확인하여 로그 파일 암호화의 상태를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-232">You can find the status of the log file encryption by viewing the `encryption_state` column in the `sys.dm_database_encryption_keys` view, as in this example:</span></span>

```
USE AdventureWorks2012;
GO
/* The value 3 represents an encrypted state 
   on the database and transaction logs. */
SELECT *
FROM sys.dm_database_encryption_keys
WHERE encryption_state = 3;
GO
```

 <span data-ttu-id="5cf2c-233">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 로그 파일 아키텍처에 대한 자세한 내용은 [트랜잭션 로그&#40;SQL Server&#41;](../../logs/the-transaction-log-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-233">For more information about the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] log file architecture, see [The Transaction Log &#40;SQL Server&#41;](../../logs/the-transaction-log-sql-server.md).</span></span>

 <span data-ttu-id="5cf2c-234">데이터베이스 암호화 키를 변경하기 전에 트랜잭션 로그에 작성된 모든 데이터는 이전 데이터베이스 암호화 키를 사용하여 암호화됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-234">All data written to the transaction log before a change in the database encryption key will be encrypted by using the previous database encryption key.</span></span>

 <span data-ttu-id="5cf2c-235">데이터베이스 암호화 키를 두 번 수정한 후 다시 데이터베이스 암호화 키를 수정하려면 먼저 로그 백업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-235">After a database encryption key has been modified twice, a log backup must be performed before the database encryption key can be modified again.</span></span>

### <a name="transparent-data-encryption-and-the-tempdb-system-database"></a><span data-ttu-id="5cf2c-236">투명한 데이터 암호화 및 tempdb 시스템 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="5cf2c-236">Transparent Data Encryption and the tempdb System Database</span></span>
 <span data-ttu-id="5cf2c-237">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 TDE를 사용하여 암호화된 다른 데이터베이스가 있으면 tempdb 시스템 데이터베이스가 암호화됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-237">The tempdb system database will be encrypted if any other database on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is encrypted by using TDE.</span></span> <span data-ttu-id="5cf2c-238">이로 인해 동일한 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]인스턴스의 암호화되지 않은 데이터베이스의 성능에 영향을 미칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-238">This might have a performance effect for unencrypted databases on the same instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5cf2c-239">tempdb 시스템 데이터베이스에 대한 자세한 내용은 [tempdb 데이터베이스](../../databases/tempdb-database.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-239">For more information about the tempdb system database, see [tempdb Database](../../databases/tempdb-database.md).</span></span>

### <a name="transparent-data-encryption-and-replication"></a><span data-ttu-id="5cf2c-240">투명한 데이터 암호화 및 복제</span><span class="sxs-lookup"><span data-stu-id="5cf2c-240">Transparent Data Encryption and Replication</span></span>
 <span data-ttu-id="5cf2c-241">복제를 수행해도 암호화된 형식의 TDE 설정 데이터베이스에 있는 데이터는 자동으로 복제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-241">Replication does not automatically replicate data from a TDE-enabled database in an encrypted form.</span></span> <span data-ttu-id="5cf2c-242">배포 및 구독자 데이터베이스를 보호하려면 TDE를 개별적으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-242">You must separately enable TDE if you want to protect the distribution and subscriber databases.</span></span> <span data-ttu-id="5cf2c-243">트랜잭션 및 병합 복제를 위한 데이터의 초기 배포뿐만 아니라 스냅샷 복제도 암호화되지 않은 중간 파일(예: bcp 파일)에 데이터를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-243">Snapshot replication, as well as the initial distribution of data for transactional and merge replication, can store data in unencrypted intermediate files; for example, the bcp files.</span></span>  <span data-ttu-id="5cf2c-244">트랜잭션 또는 병합 복제 중에 통신 채널을 보호하도록 암호화를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-244">During transactional or merge replication, encryption can be enabled to protect the communication channel.</span></span> <span data-ttu-id="5cf2c-245">자세한 내용은 [데이터베이스 엔진에 암호화 연결 사용&#40;SQL Server 구성 관리자&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-245">For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).</span></span>

### <a name="transparent-data-encryption-and-filestream-data"></a><span data-ttu-id="5cf2c-246">투명한 데이터 암호화 및 FILESTREAM 데이터</span><span class="sxs-lookup"><span data-stu-id="5cf2c-246">Transparent Data Encryption and FILESTREAM DATA</span></span>
 <span data-ttu-id="5cf2c-247">TDE를 사용하는 경우에도 FILESTREAM 데이터는 암호화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-247">FILESTREAM data is not encrypted even when TDE is enabled.</span></span>

### <a name="transparent-data-encryption-and-buffer-pool-extension"></a><span data-ttu-id="5cf2c-248">투명한 데이터 암호화 및 버퍼 풀 확장</span><span class="sxs-lookup"><span data-stu-id="5cf2c-248">Transparent Data Encryption and Buffer Pool Extension</span></span>
 <span data-ttu-id="5cf2c-249">TDE를 사용하여 데이터베이스를 암호화한 경우에 BPE(버퍼 풀 확장)와 관련된 파일을 암호화하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-249">Files related to buffer pool extension (BPE) are not encrypted when database is encrypted using TDE.</span></span> <span data-ttu-id="5cf2c-250">Bitlocker와 같은 파일 시스템 수준 암호화 도구 또는 BPE 관련 파일에 대한 EFS를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-250">You must use file system level encryption tools like Bitlocker or EFS for BPE related files.</span></span>

## <a name="transparent-data-encryption-and-in-memory-oltp"></a><span data-ttu-id="5cf2c-251">투명한 데이터 암호화 및 메모리 내 OLTP</span><span class="sxs-lookup"><span data-stu-id="5cf2c-251">Transparent Data Encryption and In-Memory OLTP</span></span>
 <span data-ttu-id="5cf2c-252">TDE는 메모리 내 OLTP 개체가 포함된 데이터베이스에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-252">TDE can be enabled on a database that has In-Memory OLTP objects.</span></span> <span data-ttu-id="5cf2c-253">TDE가 사용하도록 설정된 경우에는 메모리 내 OLTP 로그 레코드가 암호화됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-253">In-Memory OLTP log records are encrypted if TDE is enabled.</span></span> <span data-ttu-id="5cf2c-254">TDE가 설정된 경우에는 MEMORY_OPTIMIZED_DATA 파일 그룹의 데이터가 암호화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf2c-254">Data in a MEMORY_OPTIMIZED_DATA filegroup is not encrypted if TDE is enabled.</span></span>

## <a name="see-also"></a><span data-ttu-id="5cf2c-255">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5cf2c-255">See Also</span></span>
 <span data-ttu-id="5cf2c-256">[TDE로 보호 되는 데이터베이스를 다른 SQL Server로 이동](move-a-tde-protected-database-to-another-sql-server.md) [Azure SQL Database](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md) [SQL Server 암호화](sql-server-encryption.md) [SQL Server 및 데이터베이스 암호화 키](sql-server-and-database-encryption-keys-database-engine.md) 를 [사용 하 여 tde를 사용 하도록 설정](enable-tde-on-sql-server-using-ekm.md) &#40;데이터베이스 엔진 [&#41;Security Center 투명한 데이터 암호화](../security-center-for-sql-server-database-engine-and-azure-sql-database.md) [FILESTREAM SQL Server](../../blob/filestream-sql-server.md) 데이터베이스 엔진 Azure SQL Database</span><span class="sxs-lookup"><span data-stu-id="5cf2c-256">[Move a TDE Protected Database to Another SQL Server](move-a-tde-protected-database-to-another-sql-server.md) [Enable TDE Using EKM](enable-tde-on-sql-server-using-ekm.md) [Transparent Data Encryption with Azure SQL Database](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md) [SQL Server Encryption](sql-server-encryption.md) [SQL Server and Database Encryption Keys &#40;Database Engine&#41;](sql-server-and-database-encryption-keys-database-engine.md) [Security Center for SQL Server Database Engine and Azure SQL Database](../security-center-for-sql-server-database-engine-and-azure-sql-database.md) [FILESTREAM &#40;SQL Server&#41;](../../blob/filestream-sql-server.md)</span></span>


