---
title: 서비스 마스터 키 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- service master key [SQL Server]
- service master key [SQL Server], about service master key
ms.assetid: 85f2095d-2590-4f59-8a29-7e100edd02bb
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: baeeffd49ac89ce85cf64932fbfd4982d7243887
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743160"
---
# <a name="service-master-key"></a><span data-ttu-id="d4aa2-102">인스턴스에서 해당 인스턴스를 위해 생성되는 SMK(</span><span class="sxs-lookup"><span data-stu-id="d4aa2-102">Service Master Key</span></span>
  <span data-ttu-id="d4aa2-103">서비스 마스터 키는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 암호화 계층의 루트이며</span><span class="sxs-lookup"><span data-stu-id="d4aa2-103">The Service Master Key is the root of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption hierarchy.</span></span> <span data-ttu-id="d4aa2-104">처음으로 다른 키를 암호화해야 할 때 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4aa2-104">It is generated automatically the first time it is needed to encrypt another key.</span></span> <span data-ttu-id="d4aa2-105">기본적으로 서비스 마스터 키는 Windows 데이터 보호 API 및 로컬 컴퓨터 키를 사용하여 암호화됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4aa2-105">By default, the Service Master Key is encrypted using the Windows data protection API and using the local machine key.</span></span> <span data-ttu-id="d4aa2-106">서비스 마스터 키는 이 키를 만든 Windows 서비스 계정이나 서비스 계정 이름 및 암호에 대한 액세스를 갖고 있는 보안 주체만 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4aa2-106">The Service Master Key can only be opened by the Windows service account under which it was created or by a principal with access to both the service account name and its password.</span></span>  
  
 <span data-ttu-id="d4aa2-107">서비스 마스터 키를 다시 생성하거나 복원하는 과정에는 전체 암호화 계층을 해독하고 다시 암호화하는 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4aa2-107">Regenerating or restoring the Service Master Key involves decrypting and re-encrypting the complete encryption hierarchy.</span></span> <span data-ttu-id="d4aa2-108">키가 손상된 경우가 아니면 이 리소스 중심 작업을 사용량이 낮은 기간 동안에만 수행하도록 예약해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4aa2-108">Unless the key has been compromised, this resource-intensive operation should be scheduled during a period of low demand.</span></span>  
  
 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] <span data-ttu-id="d4aa2-109">에서는 AES 암호화 알고리즘을 사용하여 SMK(서비스 마스터 키) 및 DMK(데이터베이스 마스터 키)를 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="d4aa2-109">uses the AES encryption algorithm to protect the service master key (SMK) and the database master key (DMK).</span></span> <span data-ttu-id="d4aa2-110">AES는 이전 버전에서 사용하는 3DES보다 최신 암호화 알고리즘입니다.</span><span class="sxs-lookup"><span data-stu-id="d4aa2-110">AES is a newer encryption algorithm than 3DES used in earlier versions.</span></span> <span data-ttu-id="d4aa2-111">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] 인스턴스를 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 로 업그레이드한 후 SMK와 DMK를 다시 생성해야 마스터 키가 AES로 업그레이드됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4aa2-111">After upgrading an instance of the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] to [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] the SMK and DMK should be regenerated in order to upgrade the master keys to AES.</span></span> <span data-ttu-id="d4aa2-112">SMK를 다시 생성하는 방법은 [ALTER SERVICE MASTER KEY&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-service-master-key-transact-sql) 및 [ALTER MASTER KEY&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-master-key-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d4aa2-112">For more information about regenerating the SMK, see [ALTER SERVICE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-service-master-key-transact-sql) and [ALTER MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-master-key-transact-sql).</span></span>  
  
## <a name="best-practice"></a><span data-ttu-id="d4aa2-113">모범 사례</span><span class="sxs-lookup"><span data-stu-id="d4aa2-113">Best Practice</span></span>  
 <span data-ttu-id="d4aa2-114">서비스 마스터 키를 백업하고 백업 복사본을 사이트 외부의 안전한 위치에 보관하십시오.</span><span class="sxs-lookup"><span data-stu-id="d4aa2-114">Back up the Service Master Key and store the backed up copy in a secure, off-site location.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="d4aa2-115">관련 작업</span><span class="sxs-lookup"><span data-stu-id="d4aa2-115">Related Tasks</span></span>  
 [<span data-ttu-id="d4aa2-116">BACKUP SERVICE MASTER KEY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d4aa2-116">BACKUP SERVICE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/backup-service-master-key-transact-sql)  
  
 [<span data-ttu-id="d4aa2-117">RESTORE SERVICE MASTER KEY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d4aa2-117">RESTORE SERVICE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-service-master-key-transact-sql)  
  
 [<span data-ttu-id="d4aa2-118">ALTER SERVICE MASTER KEY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d4aa2-118">ALTER SERVICE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-service-master-key-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="d4aa2-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d4aa2-119">See Also</span></span>  
 [<span data-ttu-id="d4aa2-120">암호화 계층</span><span class="sxs-lookup"><span data-stu-id="d4aa2-120">Encryption Hierarchy</span></span>](encryption-hierarchy.md)  
  
  
