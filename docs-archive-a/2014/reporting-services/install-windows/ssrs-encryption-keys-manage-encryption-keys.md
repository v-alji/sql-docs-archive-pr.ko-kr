---
title: 암호화 키 구성 및 관리(SSRS 구성 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- encryption keys [Reporting Services]
- private keys [Reporting Services]
- cryptography [Reporting Services]
- symmetric keys [Reporting Services]
- encryption [Reporting Services]
- public keys [Reporting Services]
ms.assetid: 58e61636-88a2-4338-ae5f-3dd210aee887
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: afe9edff22c67b9b27c1fca88c9413f5a9ed98de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742939"
---
# <a name="configure-and-manage-encryption-keys-ssrs-configuration-manager"></a><span data-ttu-id="042a4-102">암호화 키 구성 및 관리(SSRS 구성 관리자)</span><span class="sxs-lookup"><span data-stu-id="042a4-102">Configure and Manage Encryption Keys (SSRS Configuration Manager)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="042a4-103">는 암호화 키를 사용하여 보고서 서버 데이터베이스에 저장된 연결 정보 및 자격 증명을 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="042a4-103">uses encryption keys to secure credentials and connection information that is stored in a report server database.</span></span> <span data-ttu-id="042a4-104">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 암호화는 중요한 데이터를 보호하는 데 사용되는 퍼블릭 키, 프라이빗 키 및 대칭 키의 조합을 통해 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="042a4-104">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], encryption is supported through a combination of public, private, and symmetric keys that are used to protect sensitive data.</span></span> <span data-ttu-id="042a4-105">대칭 키는 보고서 서버의 설치 또는 구성 과정에서 보고서 서버를 초기화하는 동안 생성되며, 보고서 서버에서 이 서버에 저장된 중요한 데이터를 암호화하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="042a4-105">The symmetric key is created during report server initialization when you install or configure the report server, and it is used by the report server to encrypt sensitive data that is stored in the report server.</span></span> <span data-ttu-id="042a4-106">퍼블릭 키 및 프라이빗 키는 운영 체제에서 생성되며 대칭 키를 보호하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="042a4-106">Public and private keys are created by the operating system, and they are used to protect the symmetric key.</span></span> <span data-ttu-id="042a4-107">보고서 서버 데이터베이스의 중요한 데이터를 저장하는 각 보고서 서버 인스턴스당 하나의 퍼블릭 키 및 프라이빗 키 쌍이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="042a4-107">A public and private key pair is created for each report server instance that stores sensitive data in a report server database.</span></span>  
  
 <span data-ttu-id="042a4-108">암호화 키 관리는 대칭 키 백업 복사본을 만들고 키를 복원, 삭제 또는 변경하는 시기와 방법을 이해하는 작업으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="042a4-108">Managing the encryption keys consists of creating a backup copy of the symmetric key, and knowing when and how to restore, delete, or change the keys.</span></span> <span data-ttu-id="042a4-109">보고서 서버 설치를 마이그레이션하거나 수평적 스케일 아웃 배포를 구성하는 경우 새 설치에 적용할 수 있도록 대칭 키의 백업 복사본이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="042a4-109">If you migrate a report server installation or configure a scale-out deployment, you must have a backup copy of the symmetric key so that you can apply it to the new installation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="042a4-110">Reporting Services 암호화 키를 주기적으로 변경하는 것은 최상의 보안 권장 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="042a4-110">Periodically changing the Reporting Services encryption key is a security best practice.</span></span> <span data-ttu-id="042a4-111">Reporting Services의 중요 버전 업그레이드 직후에 키를 변경하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="042a4-111">A recommended time to change the key is immediately following a major version upgrade of Reporting Services.</span></span> <span data-ttu-id="042a4-112">업그레이드 후에 키를 변경하면 업그레이드 주기를 벗어나 Reporting Services 암호화 키를 변경할 경우에 발생하는 추가 서비스 중단이 최소화됩니다.</span><span class="sxs-lookup"><span data-stu-id="042a4-112">Changing the key after an upgrade minimizes additional service interruption caused by changing the Reporting Services encryption key outside of the upgrade cycle.</span></span>  
  
 <span data-ttu-id="042a4-113">대칭 키를 관리하기 위해 Reporting Services 구성 도구나 **rskeymgmt** 유틸리티를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="042a4-113">To manage symmetric keys, you can use the Reporting Services Configuration tool or the **rskeymgmt** utility.</span></span> <span data-ttu-id="042a4-114">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 에 포함된 도구는 대칭 키 관리에만 사용됩니다(퍼블릭 키 및 프라이빗 키는 운영 체제에서 관리됨).</span><span class="sxs-lookup"><span data-stu-id="042a4-114">The tools included in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] are used to manage the symmetric key only (the public and private keys are managed by the operating system).</span></span> <span data-ttu-id="042a4-115">Reporting Services 구성 도구 및 **rskeymgmt** 유틸리티는 모두 다음 태스크를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="042a4-115">Both the Reporting Services Configuration tool and the **rskeymgmt** utility support the following tasks:</span></span>  
  
-   <span data-ttu-id="042a4-116">보고서 서버 설치를 복구하는 데 사용할 수 있도록 또는 계획된 마이그레이션의 일환으로 대칭 키의 복사본을 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="042a4-116">Back up a copy of the symmetric key so that you can use it to recover a report server installation or as part of a planned migration.</span></span>  
  
-   <span data-ttu-id="042a4-117">이전에 저장한 대칭 키를 보고서 서버 데이터베이스로 복원하여 새 보고서 서버 인스턴스가 원래 암호화하지 않았던 기존 데이터에 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="042a4-117">Restore a previously saved symmetric key to a report server database, allowing a new report server instance to access existing data that it did not originally encrypt.</span></span>  
  
-   <span data-ttu-id="042a4-118">암호화된 데이터에 더 이상 액세스할 수 없는 경우에 보고서 서버 데이터베이스에서 암호화된 데이터를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="042a4-118">Delete the encrypted data in a report server database in the unlikely event that you can no longer access encrypted data.</span></span>  
  
-   <span data-ttu-id="042a4-119">대칭 키가 노출되는 경우에 대칭 키를 다시 만들고 데이터를 다시 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="042a4-119">Re-create symmetric keys and re-encrypt data in the unlikely event that the symmetric key is compromised.</span></span> <span data-ttu-id="042a4-120">최상의 보안을 위해 대칭 키를 주기적으로(예: 몇 달에 한 번씩) 다시 만들어 키 해독을 시도하는 사이버 공격으로부터 보고서 서버 데이터베이스를 보호해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="042a4-120">As a security best practice, you should recreate the symmetric key periodically (for example, every few months) to protect the report server database from cyber attacks that attempt to decipher the key.</span></span>  
  
-   <span data-ttu-id="042a4-121">여러 보고서 서버가 단일 보고서 서버 데이터베이스 및 해당 데이터베이스에 대해 해독 가능한 암호화를 제공하는 대칭 키를 공유하는 보고서 서버 스케일 아웃 배포에서 보고서 서버 인스턴스를 추가하거나 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="042a4-121">Add or remove a report server instance from a report server scale-out deployment where multiple report servers share both a single report server database and the symmetric key that provides reversible encryption for that database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="042a4-122">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="042a4-122">In This Section</span></span>  
 [<span data-ttu-id="042a4-123">보고서 서버 초기화&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="042a4-123">Initialize a Report Server &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-initialize-a-report-server.md)  
 <span data-ttu-id="042a4-124">암호화 키의 생성 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="042a4-124">Explains how encryption keys are created.</span></span>  
  
 [<span data-ttu-id="042a4-125">Reporting Services 암호화 키 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="042a4-125">Back Up and Restore Reporting Services Encryption Keys</span></span>](ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)  
 <span data-ttu-id="042a4-126">암호화 키를 백업한 후 복원하여 보고서 서버 설치를 복구 또는 마이그레이션하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="042a4-126">Explains how to back up encryption keys and restore them to recover or migrate a report server installation.</span></span>  
  
 [<span data-ttu-id="042a4-127">암호화된 보고서 서버 데이터 저장&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="042a4-127">Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-store-encrypted-report-server-data.md)  
 <span data-ttu-id="042a4-128">보고서 서버의 암호화에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="042a4-128">Describes encryption on a report server.</span></span>  
  
 [<span data-ttu-id="042a4-129">암호화 키 삭제 및 다시 만들기&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="042a4-129">Delete and Re-create Encryption Keys  &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-delete-and-re-create-encryption-keys.md)  
 <span data-ttu-id="042a4-130">대칭 키를 새 버전으로 바꾸는 방법과 대칭 키의 유효성을 검사할 수 없는 경우 다시 시작하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="042a4-130">Explains how you can replace a symmetric key with a new version, and how to start over if symmetric keys cannot be validated.</span></span>  
  
 [<span data-ttu-id="042a4-131">확장 배포의 암호화 키 추가 및 제거&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="042a4-131">Add and Remove Encryption Keys for Scale-Out Deployment &#40;SSRS Configuration Manager&#41;</span></span>](add-and-remove-encryption-keys-for-scale-out-deployment.md)  
 <span data-ttu-id="042a4-132">암호화 키를 추가 및 제거하여 스케일 아웃 배포에 속하는 보고서 서버를 제어하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="042a4-132">Explains how to add and remove encryption keys to control which report servers are part of a scale-out deployment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="042a4-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="042a4-133">See Also</span></span>  
 [<span data-ttu-id="042a4-134">암호화된 보고서 서버 데이터 저장&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="042a4-134">Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-store-encrypted-report-server-data.md)  
  
  
