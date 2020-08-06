---
title: 암호화된 미러 데이터베이스 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- cryptography [SQL Server], database mirroring
- encryption [SQL Server], database mirroring
- database master key [SQL Server], database mirroring
- mirror database [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 7329a575-be29-46e0-abc6-1344db37920c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a5148411792f1ea881bba59e599252284575bbdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733047"
---
# <a name="set-up-an-encrypted-mirror-database"></a><span data-ttu-id="38a14-102">암호화된 미러 데이터베이스 설정</span><span class="sxs-lookup"><span data-stu-id="38a14-102">Set Up an Encrypted Mirror Database</span></span>

<span data-ttu-id="38a14-103">미러 데이터베이스의 데이터베이스 마스터 키에 대한 자동 암호 해독을 사용하려면 마스터 키를 암호화하는 데 사용한 암호를 미러 서버 인스턴스에 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a14-103">To enable automatic decryption of the database master key of a mirror database, you must provide the password used to encrypt the master key to the mirror server instance.</span></span> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="38a14-104">및 이후 버전에는 암호를 전송하는 메커니즘이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="38a14-104">and later versions include mechanisms to transfer the password.</span></span> <span data-ttu-id="38a14-105">데이터베이스 미러링을 시작하기 전에 **sp_control_dbmasterkey_password** 를 사용하여 데이터베이스 마스터 키에 대한 자격 증명을 만드세요.</span><span class="sxs-lookup"><span data-stu-id="38a14-105">Use **sp_control_dbmasterkey_password** to create a credential for the database master key before you start database mirroring.</span></span> <span data-ttu-id="38a14-106">미러되는 모든 데이터베이스에 대해 이 프로세스를 반복해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a14-106">You must repeat this process for every database that will be mirrored.</span></span> <span data-ttu-id="38a14-107">자세한 내용은 [sp_control_dbmasterkey_password&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38a14-107">For more information, see [sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql).</span></span>
  
> [!CAUTION]  
>  <span data-ttu-id="38a14-108">**sa** 및 기타 상위 권한 서버 보안 주체에서 액세스하지 않아야 하는 데이터베이스에 대한 장애 조치(Failover) 암호 해독은 설정하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="38a14-108">Do not enable failover decryption of a database that must remain inaccessible to **sa** and other highly privileged server principals.</span></span> <span data-ttu-id="38a14-109">서비스 마스터 키로 키 계층을 해독할 수 없도록 데이터베이스를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38a14-109">You can configure a database so that its key hierarchy cannot be decrypted by the service master key.</span></span> <span data-ttu-id="38a14-110">이 옵션은 **sa** 또는 기타 상위 권한 서버 보안 주체에서 액세스하지 않아야 하는 정보가 포함된 데이터베이스를 위한 심층 방어로 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="38a14-110">This option is supported as a defense-in-depth for databases that contain information that should not be accessible to **sa** or other highly privileged server principals.</span></span> <span data-ttu-id="38a14-111">이러한 데이터베이스에 대해 장애 조치(failover) 암호 해독을 설정하면 이러한 심층 방어가 제거되어 **sa** 및 기타 상위 권한 서버 보안 주체에서 데이터베이스를 암호 해독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38a14-111">Enabling failover decryption of such a database removes this defense-in-depth, enabling **sa** and other highly privileged server principals to decrypt the database.</span></span>  


<!-- Note: We cannot append '?view=sql-server-2016' to these, even tho in theory we might want to. -->

## <a name="see-also"></a><span data-ttu-id="38a14-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38a14-112">See Also</span></span>

[<span data-ttu-id="38a14-113">sp_control_dbmasterkey_password&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="38a14-113">sp_control_dbmasterkey_password &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql)

[<span data-ttu-id="38a14-114">CREATE MASTER KEY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="38a14-114">CREATE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-master-key-transact-sql)

[<span data-ttu-id="38a14-115">ALTER MASTER KEY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="38a14-115">ALTER MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-master-key-transact-sql)

[<span data-ttu-id="38a14-116">암호화 계층</span><span class="sxs-lookup"><span data-stu-id="38a14-116">Encryption Hierarchy</span></span>](../../relational-databases/security/encryption/encryption-hierarchy.md)

[<span data-ttu-id="38a14-117">데이터베이스 미러링 설정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="38a14-117">Setting Up Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)

