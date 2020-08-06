---
title: Azure Key Vault를 사용한 확장 가능 키 관리(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- EKM, with key vault
- TDE, EKM and key vault
- Extensible Key Management with key vault
- Key Management with key vault
- Transparent Data Encryption, using EKM and key vault
ms.assetid: 3efdc48a-8064-4ea6-a828-3fbf758ef97c
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 0e4bbc4f0c371c927988e6b91fdbf47307ad9d3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743172"
---
# <a name="extensible-key-management-using-azure-key-vault-sql-server"></a><span data-ttu-id="d55f8-102">Azure 키 자격 증명 모음(SQL Server)을 사용한 확장 가능 키 관리</span><span class="sxs-lookup"><span data-stu-id="d55f8-102">Extensible Key Management Using Azure Key Vault (SQL Server)</span></span>
  <span data-ttu-id="d55f8-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Azure Key Vault 용 커넥터를 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 사용 하 여 암호화를 사용 하면 암호화 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 키를 보호 하기 위해 [EKM&#41;공급자로 확장 가능 키 관리 &#40;](extensible-key-management-ekm.md) Azure Key Vault 서비스를 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-103">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Azure Key Vault enables [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption to leverage the Azure Key Vault service as an [Extensible Key Management &#40;EKM&#41;](extensible-key-management-ekm.md) provider to protect its encryption keys.</span></span>

 <span data-ttu-id="d55f8-104">이 항목의 내용:</span><span class="sxs-lookup"><span data-stu-id="d55f8-104">Included in this topic:</span></span>

-   [<span data-ttu-id="d55f8-105">EKM 사용</span><span class="sxs-lookup"><span data-stu-id="d55f8-105">Uses of EKM</span></span>](#Uses)

-   [<span data-ttu-id="d55f8-106">1단계: SQL Server에서 사용할 수 있도록 키 자격 증명 모음 설정</span><span class="sxs-lookup"><span data-stu-id="d55f8-106">Step 1: Setting up the Key Vault for use by SQL Server</span></span>](#Step1)

-   [<span data-ttu-id="d55f8-107">2단계: SQL Server 커넥터 설치</span><span class="sxs-lookup"><span data-stu-id="d55f8-107">Step 2: Installing the SQL Server Connector</span></span>](#Step2)

-   [<span data-ttu-id="d55f8-108">3단계: 키 자격 증명 모음에 EKM 공급자를 사용하도록 SQL Server 구성</span><span class="sxs-lookup"><span data-stu-id="d55f8-108">Step 3: Configure SQL Server to use an EKM provider for the Key Vault</span></span>](#Step3)

-   [<span data-ttu-id="d55f8-109">예 1: 키 자격 증명 모음에서 비대칭 키를 사용한 투명한 데이터 암호화</span><span class="sxs-lookup"><span data-stu-id="d55f8-109">Example A: Transparent Data Encryption by Using an Asymmetric Key from the Key Vault</span></span>](#ExampleA)

-   [<span data-ttu-id="d55f8-110">예 2: 키 자격 증명 모음에서 비대칭 키를 사용한 백업 암호화</span><span class="sxs-lookup"><span data-stu-id="d55f8-110">Example B: Encrypting Backups by Using an Asymmetric Key from the Key Vault</span></span>](#ExampleB)

-   [<span data-ttu-id="d55f8-111">예 3: 키 자격 증명 모음에서 비대칭 키를 사용한 열 수준 암호화</span><span class="sxs-lookup"><span data-stu-id="d55f8-111">Example C: Column Level Encryption by Using an Asymmetric Key from the Key Vault</span></span>](#ExampleC)

##  <a name="uses-of-ekm"></a><a name="Uses"></a><span data-ttu-id="d55f8-112">EKM 사용</span><span class="sxs-lookup"><span data-stu-id="d55f8-112">Uses of EKM</span></span>
 <span data-ttu-id="d55f8-113">조직에서 중요한 데이터를 보호하기 위해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 암호화를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-113">An organization can use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption to protect sensitive data.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="d55f8-114">암호화에는 [투명한 데이터 암호화 &#40;TDE&#41;](transparent-data-encryption.md), CLE ( [열 수준 암호화](/sql/t-sql/functions/cryptographic-functions-transact-sql) ) 및 [백업 암호화](../../backup-restore/backup-encryption.md)가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-114">encryption includes [Transparent Data Encryption &#40;TDE&#41;](transparent-data-encryption.md), [Column Level Encryption](/sql/t-sql/functions/cryptographic-functions-transact-sql) (CLE), and [Backup Encryption](../../backup-restore/backup-encryption.md).</span></span> <span data-ttu-id="d55f8-115">이 암호화들에서는 모두 데이터가 대칭 데이터 암호화 키를 사용하여 암호화되고,</span><span class="sxs-lookup"><span data-stu-id="d55f8-115">In all of these cases the data is encrypted using a symmetric data encryption key.</span></span> <span data-ttu-id="d55f8-116">이 대칭 데이터 암호화 키는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 저장된 키의 계층 구조로 암호화하여 추가적으로 보호하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-116">The symmetric data encryption key is further protected by encrypting it with a hierarchy of keys stored in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d55f8-117">이렇게 하는 대신, EKM 공급자 아키텍처를 사용하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에서는 외부 암호화 공급자에 있는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 외부에 저장된 비대칭 키를 사용하여 데이터 암호화 키를 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-117">Alternatively, the EKM provider architecture enables [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to protect the data encryption keys by using an asymmetric key stored outside of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in an external cryptographic provider.</span></span> <span data-ttu-id="d55f8-118">EKM 공급자 아키텍처를 사용하면 추가적인 보안 계층이 생기고 조직은 키와 데이터의 관리를 분리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-118">Using EKM provider architecture adds an additional layer of security and allows organizations to separate the management of keys and data.</span></span>

 <span data-ttu-id="d55f8-119">Azure Key Vault용 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 커넥터를 사용하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서는 확장성과 성능이 뛰어난 고가용성 Key Vault 서비스를 암호화 키 보호를 위한 EKM 공급자로 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-119">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector for Azure Key Vault lets [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] leverage the scalable, high performance, and highly available key vault service as an EKM provider for encryption key protection.</span></span> <span data-ttu-id="d55f8-120">키 자격 증명 모음 서비스는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Azure 가상 컴퓨터의 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 설치와 함께 온-프레미스 서버용으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-120">The key vault service can be used with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installations on [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Azure Virtual Machines and for on-premises servers.</span></span> <span data-ttu-id="d55f8-121">키 자격 증명 모음 서비스에서는 더 높은 수준의 비대칭 암호화 키 보호를 위해 세부적인 제어 및 모니터링이 이루어지는 HSM(하드웨어 보안 모듈)을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-121">The key vault service also provides the option to use tightly controlled and monitored Hardware Security Modules (HSMs) for a higher level of protection for asymmetric encryption keys.</span></span> <span data-ttu-id="d55f8-122">Key Vault에 대한 자세한 내용은 [Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521401)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d55f8-122">For more information about the key vault, see [Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521401).</span></span>

 <span data-ttu-id="d55f8-123">다음 이미지에 키 자격 증명 모음을 사용한 EKM의 프로세스 흐름이 요약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-123">The following image summarizes the process flow of EKM using the key vault.</span></span> <span data-ttu-id="d55f8-124">이미지의 프로세스 단계 번호는 이미지에서 설명하는 설정 단계 번호와 일치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-124">The process step numbers in the image are not meant to match the setup step numbers that follow the image.</span></span>

 <span data-ttu-id="d55f8-125">![Azure Key Vault를 사용하는 SQL Server EKM](../../../database-engine/media/ekm-using-azure-key-vault.png "Azure Key Vault를 사용하는 SQL Server EKM")</span><span class="sxs-lookup"><span data-stu-id="d55f8-125">![SQL Server EKM using the Azure Key Vault](../../../database-engine/media/ekm-using-azure-key-vault.png "SQL Server EKM using the Azure Key Vault")</span></span>

##  <a name="step-1-set-up-the-key-vault-for-use-by-sql-server"></a><a name="Step1"></a><span data-ttu-id="d55f8-126">1 단계:에서 사용할 Key Vault 설정 SQL Server</span><span class="sxs-lookup"><span data-stu-id="d55f8-126">Step 1: Set up the Key Vault for use by SQL Server</span></span>
 <span data-ttu-id="d55f8-127">다음 단계를 사용하여 암호화 키 보호를 위해 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] 에 사용할 자격 증명 모음 키를 설정하세요.</span><span class="sxs-lookup"><span data-stu-id="d55f8-127">Use the following steps to set up a key vault for use with the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] for encryption key protection.</span></span> <span data-ttu-id="d55f8-128">자격 증명 모음은 이미 조직에 사용 중일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-128">A vault may already be in use for the organization.</span></span> <span data-ttu-id="d55f8-129">자격 증명 모음이 존재하지 않으면 암호화 키를 관리하도록 지정된 조직 내 Azure 관리자가 자격 증명 모음을 만들고, 이 자격 증명 모음에서 비대칭 키를 생성한 다음 키를 사용할 수 있는 권한을 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-129">When a vault does not exist, the Azure Administrator in your organization that is designated to manage encryption keys can create a vault, generate an asymmetric key in the vault, and then authorize [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to use the key.</span></span> <span data-ttu-id="d55f8-130">Vault 서비스에 대해 이해하려면 [Azure Key Vault 시작](https://go.microsoft.com/fwlink/?LinkId=521402)(영문), 및 PowerShell [Azure Key Vault Cmdlet](https://docs.microsoft.com/powershell/module/azurerm.keyvault)(영문) 참조를 검토하세요.</span><span class="sxs-lookup"><span data-stu-id="d55f8-130">To familiarize yourself with the key vault service review [Get Started with Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402), and the PowerShell [Azure Key Vault Cmdlets](https://docs.microsoft.com/powershell/module/azurerm.keyvault) reference.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="d55f8-131">여러 Azure 구독이 있는 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]가 포함된 구독을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-131">If you have multiple Azure subscriptions, you must use the subscription that contains [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>

1.  <span data-ttu-id="d55f8-132">**Vault 만들기:**[Azure Key Vault 시작](https://go.microsoft.com/fwlink/?LinkId=521402)의 **Key Vault 만들기** 섹션에 있는 지침을 사용하여 Vault를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-132">**Create a vault:** Create a vault by using the instructions in the **Create a key vault** section of [Get Started with Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402).</span></span> <span data-ttu-id="d55f8-133">자격 증명 모음의 이름은 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-133">Record the name of the vault.</span></span> <span data-ttu-id="d55f8-134">이 항목에서는 **ContosoKeyVault** 를 키 자격 증명 모음 이름으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-134">This topic uses **ContosoKeyVault** as the key vault name.</span></span>

2.  <span data-ttu-id="d55f8-135">**자격 증명 모음에서 비대칭 키 생성:** 키 자격 증명 모음에 있는 비대칭 키는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 암호화 키를 보호하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-135">**Generate an asymmetric key in the vault:** The asymmetric key in the key vault is used to protect [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption keys.</span></span> <span data-ttu-id="d55f8-136">비대칭 키의 퍼블릭 부분만 자격 증명 모음을 떠나고 프라이빗 부분은 자격 증명 모음에서 내보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-136">Only the public portion of the asymmetric key ever leaves the vault, the private portion is never exported by the vault.</span></span> <span data-ttu-id="d55f8-137">비대칭 키를 사용하는 모든 암호화 작업은 Azure 키 자격 증명 모음에 위임되며, 키 자격 증명 모음 보안에 의해 보호됩니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-137">All cryptographic operations using the asymmetric key are delegated to the Azure Key Vault, and are protected by the key vault security.</span></span>

     <span data-ttu-id="d55f8-138">비대칭 키를 생성하여 자격 증명 모음에 저장하는 방법에는 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-138">There are several ways that you can generate an asymmetric key and store it in the vault.</span></span> <span data-ttu-id="d55f8-139">외부에서 키를 생성한 다음 해당 키를 자격 증명 모음에 .pfx 파일로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-139">You can externally generate a key, and import the key into the vault as a .pfx file.</span></span> <span data-ttu-id="d55f8-140">또는 키 자격 증명 모음 API를 사용하여 자격 증명 모음에서 키를 직접 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-140">Or create the key directly in the vault by using the key vault APIs.</span></span>

     <span data-ttu-id="d55f8-141">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 커넥터를 사용하려면 비대칭 키가 2048비트 RSA여야 하며, 키 이름에는 문자 "a-z", "A-Z", "0-9" 및 "-"만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-141">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector requires the asymmetric keys to be 2048-bit RSA, and the key name can only use the characters "a-z", "A-Z", "0-9", and "-".</span></span> <span data-ttu-id="d55f8-142">이 문서에서 비대칭 키의 이름은 **ContosoMasterKey**라고 하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-142">In this document the name of the asymmetric key is referred to as **ContosoMasterKey**.</span></span> <span data-ttu-id="d55f8-143">이 이름은 키에 사용하고 싶은 고유 이름으로 대체하세요.</span><span class="sxs-lookup"><span data-stu-id="d55f8-143">Replace this with the unique name you use for the key.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="d55f8-144">비대칭 키를 가져오면 관리자가 키 에스크로 시스템에 키를 위탁할 수 있으므로 비대칭 키를 가져오는 것은 프로덕션 시나리오에 매우 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-144">Importing the asymmetric key is highly recommended for production scenarios because it allows the administrator to escrow the key in a key escrow system.</span></span> <span data-ttu-id="d55f8-145">프라이빗 키는 자격 증명 모음을 벗어날 수 없으므로 비대칭 키를 자격 증명 모음에서 만든 경우에는 키를 위탁할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-145">If the asymmetric key is created in the vault, it cannot be escrowed because the private key can never leave the vault.</span></span> <span data-ttu-id="d55f8-146">중요한 데이터를 보호하는 데 사용되는 키는 위탁해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-146">Keys used to protect critical data should be escrowed.</span></span> <span data-ttu-id="d55f8-147">비대칭 키가 손실되는 경우 데이터를 영구적으로 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-147">The loss of an asymmetric key will result in permanently unrecoverable data.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="d55f8-148">키 자격 증명 모음에서는 여러 버전의 동일한 이름 키를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-148">The key vault supports multiple versions of the same named key.</span></span> <span data-ttu-id="d55f8-149">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 커넥터에서 사용할 키는 버전이 지정되거나 여기저기 사용해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-149">Keys to be used by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector should not be versioned or rolled.</span></span> <span data-ttu-id="d55f8-150">관리자가 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 암호화에 사용된 키를 다른 곳에 사용하려는 경우, 자격 증명 모음에서 다른 이름으로 새 키를 만들어 DEK를 암호화하는 데 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-150">If the administrator wants to roll the key used for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption, a new key with a different name should be created in the vault and used to encrypt the DEK.</span></span>

     <span data-ttu-id="d55f8-151">키를 주요 자격 증명 모음으로 가져오거나 키 자격 증명 모음에 키를 만드는 방법에 대 한 자세한 내용은 [Azure Key Vault 시작](https://go.microsoft.com/fwlink/?LinkId=521402)의 키 **자격 증명 모음에 키 또는 암호 추가** 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d55f8-151">For more information on how to import a key into the key vault or to create a key in the key vault (not recommended for a production environment), see the **Add a key or secret to the key vault** section in [Get Started with Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402).</span></span>

3.  <span data-ttu-id="d55f8-152">**SQL Server에 사용할 Azure Active Directory 서비스 보안 주체 가져오기:** 조직은 Microsoft 클라우드 서비스에 등록할 때 Azure Active Directory를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-152">**Get Azure Active Directory Service Principals to use for SQL Server:** When the organization signs up for a Microsoft cloud service, it gets an Azure Active Directory.</span></span> <span data-ttu-id="d55f8-153">키 자격 증명 모음에 액세스할 때 **에서 사용(Azure Active Directory에 인증받기 위해)할** 서비스 사용자 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 를 Azure Active Directory에서 만드세요.</span><span class="sxs-lookup"><span data-stu-id="d55f8-153">Create **Service Principals** in the Azure Active Directory for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to use (to authenticate itself to Azure Active Directory) while accessing the key vault.</span></span>

    -   <span data-ttu-id="d55f8-154">\*\*\*\* 관리자가 암호화를 사용하기 위해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 를 구성할 때 자격 증명 모음에 액세스하는 데 한 서비스 사용자 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 가 필요하며,</span><span class="sxs-lookup"><span data-stu-id="d55f8-154">One **Service Principal** will be needed by a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] administrator to access the vault while configuring [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to use encryption.</span></span>

    -   <span data-ttu-id="d55f8-155">\*\*\*\* 암호화에 사용된 키의 래핑 해제를 위해 자격 증명 모음에 액세스하기 위해 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] 에서 또 다른 서비스 사용자 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 를 필요로 하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-155">Another **Service Principal** will be needed by the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] to access the vault for unwrapping keys used in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption.</span></span>

     <span data-ttu-id="d55f8-156">애플리케이션을 등록하고 서비스 사용자를 생성하는 방법에 대한 자세한 내용은 [Azure Key Vault 시작](https://go.microsoft.com/fwlink/?LinkId=521402)(영문)의 **Register an Application with Azure Active Directory(Azure Active Directory로 애플리케이션 등록)** 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d55f8-156">For more information about how to register an application and generate a service principal, see the **Register an Application with Azure Active Directory** section in [Get Started with Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402).</span></span> <span data-ttu-id="d55f8-157">등록 프로세스에서는 각 Azure Active Directory **서비스 사용자** 에 대해 **애플리케이션 ID**( **클라이언트 ID** 라고도 함) 및 **인증 키**( **비밀**이라고도 함)를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-157">The registration process returns an **Application ID** (also known as a **CLIENT ID**) and a **Authentication Key** (also known as a **Secret**) for each Azure Active Directory **Service Principal**.</span></span> <span data-ttu-id="d55f8-158">문에서 사용 하는 경우 `CREATE CREDENTIAL` **클라이언트 ID**에서 하이픈을 제거 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-158">When used in the `CREATE CREDENTIAL` statement, the hyphen must be removed from the **CLIENT ID**.</span></span> <span data-ttu-id="d55f8-159">아래의 스크립트에서 사용할 수 있도록 기록해 두세요.</span><span class="sxs-lookup"><span data-stu-id="d55f8-159">Record these for use in the scripts below:</span></span>

    -   <span data-ttu-id="d55f8-160">**sysadmin** 로그인용 **서비스 사용자** : **CLIENTID_sysadmin_login** 및 **SECRET_sysadmin_login**</span><span class="sxs-lookup"><span data-stu-id="d55f8-160">**Service Principal** for a **sysadmin** login: **CLIENTID_sysadmin_login** and **SECRET_sysadmin_login**</span></span>

    -   <span data-ttu-id="d55f8-161">**용** 서비스 사용자 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]: **CLIENTID_DBEngine** 및 **SECRET_DBEngine**.</span><span class="sxs-lookup"><span data-stu-id="d55f8-161">**Service Principal** for the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]: **CLIENTID_DBEngine** and **SECRET_DBEngine**.</span></span>

4.  <span data-ttu-id="d55f8-162">**서비스 사용자가 키 자격 증명 모음에 액세스할 수 있는 권한 부여:\*\*\*\*CLIENTID_sysadmin_login** 및 **CLIENTID_DBEngine서비스 사용자** 는 모두 키 자격 증명 모음에서 **get**, **list**, **wrapKey**, 및 **unwrapKey** 권한을 필요로 합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-162">**Grant Permission for the Service Principals to access the Key Vault:** Both the **CLIENTID_sysadmin_login** and **CLIENTID_DBEngineService Principals** require the **get**, **list**, **wrapKey**, and **unwrapKey** permissions in the key vault.</span></span> <span data-ttu-id="d55f8-163">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 를 통해 키를 생성하려는 경우 키 자격 증명 모음에서 **만들기** 권한도 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-163">If you intend to create keys through [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] you also need to grant the **create** permission in key vault.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="d55f8-164">사용자가 키 자격 증명 모음에 적어도 **wrapKey** 및 **unwrapKey** 작업을 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-164">Users must have at least the **wrapKey** and **unwrapKey** operations for the key vault.</span></span>

     <span data-ttu-id="d55f8-165">Vault에 사용 권한을 부여하는 방법에 대한 자세한 내용은 [Azure Key Vault 시작](https://go.microsoft.com/fwlink/?LinkId=521402)(영문)의 **Authorize the application to use the key or secret(키 또는 암호를 사용할 수 있도록 애플리케이션에 권한 부여)** 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d55f8-165">For more information about granting permissions to the vault, see the **Authorize the application to use the key or secret** section in [Get Started with Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402).</span></span>

     <span data-ttu-id="d55f8-166">Azure 키 자격 증명 모음 설명서 링크</span><span class="sxs-lookup"><span data-stu-id="d55f8-166">Links to Azure Key Vault documentation</span></span>

    -   [<span data-ttu-id="d55f8-167">Azure Key Vault란?</span><span class="sxs-lookup"><span data-stu-id="d55f8-167">What is Azure Key Vault?</span></span>](https://go.microsoft.com/fwlink/?LinkId=521401)

    -   [<span data-ttu-id="d55f8-168">Azure 키 자격 증명 모음 시작</span><span class="sxs-lookup"><span data-stu-id="d55f8-168">Get Started with Azure Key Vault</span></span>](https://go.microsoft.com/fwlink/?LinkId=521402)

    -   <span data-ttu-id="d55f8-169">PowerShell [Azure 주요 자격 증명 모음 Cmdlet](https://docs.microsoft.com/powershell/module/azurerm.keyvault) 참조</span><span class="sxs-lookup"><span data-stu-id="d55f8-169">PowerShell [Azure Key Vault Cmdlets](https://docs.microsoft.com/powershell/module/azurerm.keyvault) reference</span></span>

##  <a name="step-2-install-the-sql-server-connector"></a><a name="Step2"></a><span data-ttu-id="d55f8-170">2 단계: SQL Server 커넥터 설치</span><span class="sxs-lookup"><span data-stu-id="d55f8-170">Step 2: Install the SQL Server Connector</span></span>
 <span data-ttu-id="d55f8-171">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 커넥터는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 컴퓨터의 관리자가 다운로드하여 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-171">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector is downloaded and installed by the administrator of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] computer.</span></span> <span data-ttu-id="d55f8-172">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 커넥터는 [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=521700)에서 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-172">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector is available as a download from the [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=521700).</span></span>  <span data-ttu-id="d55f8-173">**Microsoft Azure Key Vault 용 SQL Server 커넥터**를 검색하고, 세부 정보, 시스템 요구 사항 및 설치 지침을 검토하고, 커넥터를 다운로드하도록 선택하고 **실행**을 사용하여 설치를 시작하세요.</span><span class="sxs-lookup"><span data-stu-id="d55f8-173">Search for **SQL Server Connector for Microsoft Azure Key Vault**, review the details, system requirements and install instructions and choose to download the connector and start the installation using **Run**.</span></span> <span data-ttu-id="d55f8-174">라이선스를 검토한 다음 라이선스를 수락하고 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-174">Review the license and accept the license and continue.</span></span>

 <span data-ttu-id="d55f8-175">기본적으로 커넥터는 **Microsoft Azure Key Vault에 대해 C:\Program Files\SQL Server 커넥터**에 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-175">By default the connector is installed at **C:\Program Files\SQL Server Connector for Microsoft Azure Key Vault**.</span></span> <span data-ttu-id="d55f8-176">이 위치는 설치 중 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-176">This location can be changed during setup.</span></span> <span data-ttu-id="d55f8-177">(변경할 경우 아래의 스크립트를 조정하세요.)</span><span class="sxs-lookup"><span data-stu-id="d55f8-177">(If changed, adjust the scripts below.)</span></span>

 <span data-ttu-id="d55f8-178">설치를 완료하면 다음 항목이 컴퓨터에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-178">On completing the install, the following are installed on the machine:</span></span>

-   <span data-ttu-id="d55f8-179">**Microsoft.AzureKeyVaultService.EKM.dll**: 이것은 CREATE CRYPTOGRAPHIC PROVIDER 문을 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에 등록해야 하는 암호화 EKM 공급자 DLL입니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-179">**Microsoft.AzureKeyVaultService.EKM.dll**: This is the cryptographic EKM provider DLL that needs to be registered with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using the CREATE CRYPTOGRAPHIC PROVIDER statement.</span></span>

-   <span data-ttu-id="d55f8-180">**Azure Key Vault SQL Server 커넥터**: 암호화 EKM 공급자가 키 자격 증명 모음과 통신할 수 있도록 해주는 Windows 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-180">**Azure Key Vault SQL Server Connector**: This is a Windows service that enables the cryptographic EKM provider to communicate with the key vault.</span></span>

 <span data-ttu-id="d55f8-181">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 커넥터를 설치하면 원할 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 암호화를 위한 샘플 스크립트를 다운로드할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-181">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector installation also allows you to optionally download sample scripts for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption.</span></span>

##  <a name="step-3-configure-sql-server-to-use-an-ekm-provider-for-the-key-vault"></a><a name="Step3"></a><span data-ttu-id="d55f8-182">3 단계: Key Vault에 대 한 EKM 공급자를 사용 하도록 SQL Server 구성</span><span class="sxs-lookup"><span data-stu-id="d55f8-182">Step 3: Configure SQL Server to use an EKM provider for the Key Vault</span></span>

###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d55f8-183">권한</span><span class="sxs-lookup"><span data-stu-id="d55f8-183">Permissions</span></span>
 <span data-ttu-id="d55f8-184">이 전체 프로세스를 완료하려면 **sysadmin** 고정 서버 역할에 CONTROL SERVER 권한이나 멤버 자격이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-184">To complete this entire process requires CONTROL SERVER permission or membership in the **sysadmin** fixed server role.</span></span> <span data-ttu-id="d55f8-185">특정 작업에는 다음 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-185">Specific actions require the following permissions:</span></span>

-   <span data-ttu-id="d55f8-186">암호화 공급자를 만들려면 **sysadmin** 고정 서버 역할에 CONTROL SERVER 권한 또는 멤버 자격이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-186">To create a cryptographic provider, requires CONTROL SERVER permission or membership in the **sysadmin** fixed server role.</span></span>

-   <span data-ttu-id="d55f8-187">구성 옵션을 변경하고 RECONFIGURE 문을 실행하려면 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-187">To change a configuration option and run the RECONFIGURE statement, you must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="d55f8-188">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-188">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>

-   <span data-ttu-id="d55f8-189">자격 증명을 만들려면 ALTER ANY CREDENTIAL 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-189">To create a credential, requires ALTER ANY CREDENTIAL permission.</span></span>

-   <span data-ttu-id="d55f8-190">자격 증명을 로그인에 추가하려면 ALTER ANY LOGIN 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-190">To add a credential to a login, requires ALTER ANY LOGIN permission.</span></span>

-   <span data-ttu-id="d55f8-191">비대칭 키를 만들려면 CREATE ASYMMETRIC KEY 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-191">To create an asymmetric key, requires CREATE ASYMMETRIC KEY permission.</span></span>

###  <a name="to-configure-sql-server-to-use-a-cryptographic-provider"></a><a name="TsqlProcedure"></a><span data-ttu-id="d55f8-192">암호화 공급자를 사용 하도록 SQL Server를 구성 하려면</span><span class="sxs-lookup"><span data-stu-id="d55f8-192">To configure SQL Server to use a cryptographic provider</span></span>

1.  <span data-ttu-id="d55f8-193">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] 을 구성하여 EKM을 사용하고 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 암호화 공급자를 등록합니다(만들기).</span><span class="sxs-lookup"><span data-stu-id="d55f8-193">Configure the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] to use EKM, and register (create) the cryptographic provider with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>

    ```sql
    -- Enable advanced options.
    USE master;
    GO

    sp_configure 'show advanced options', 1 ;
    GO
    RECONFIGURE ;
    GO
    -- Enable EKM provider
    sp_configure 'EKM provider enabled', 1 ;
    GO
    RECONFIGURE ;
    GO

    -- Create a cryptographic provider, using the SQL Server Connector
    -- which is an EKM provider for the Azure Key Vault. This example uses 
    -- the name AzureKeyVault_EKM_Prov.

    CREATE CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov 
    FROM FILE = 'C:\Program Files\SQL Server Connector for Microsoft Azure Key Vault\Microsoft.AzureKeyVaultService.EKM.dll';
    GO
    ```

2.  <span data-ttu-id="d55f8-194">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 암호화 시나리오를 설정 및 관리하려면 키 자격 증명 모음을 사용하도록 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 관리자 로그인용 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 자격 증명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-194">Setup a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] credential for a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] administrator login to use the key vault in order to setup and manage [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption scenarios.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="d55f8-195">의 **IDENTITY** 인수에는 `CREATE CREDENTIAL` 키 자격 증명 모음 이름이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-195">The **IDENTITY** argument of `CREATE CREDENTIAL` requires the key vault name.</span></span> <span data-ttu-id="d55f8-196">의 **SECRET** 인수에 `CREATE CREDENTIAL` 는 *\<Client ID>* (하이픈이 없는)와 *\<Secret>* 사이에 공백 없이 함께 전달 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-196">The **SECRET** argument of `CREATE CREDENTIAL` requires the *\<Client ID>* (without hyphens) and *\<Secret>* to be passed together without a space between them.</span></span>

     <span data-ttu-id="d55f8-197">다음 예제에서 **클라이언트 ID** ( `EF5C8E09-4D2A-4A76-9998-D93440D8115D` )는 하이픈을 제거 하 고 문자열로 입력 `EF5C8E094D2A4A769998D93440D8115D` 되며 **암호** 는 *SECRET_sysadmin_login*문자열로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-197">In the following example, the **Client ID** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) is stripped of the hyphens and entered as the string `EF5C8E094D2A4A769998D93440D8115D` and the **Secret** is represented by the string *SECRET_sysadmin_login*.</span></span>

    ```sql
    USE master;
    CREATE CREDENTIAL sysadmin_ekm_cred 
        WITH IDENTITY = 'ContosoKeyVault', 
        SECRET = 'EF5C8E094D2A4A769998D93440D8115DSECRET_sysadmin_login' 
    FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;

    -- Add the credential to the SQL Server administrators domain login 
    ALTER LOGIN [<domain>/<login>]
    ADD CREDENTIAL sysadmin_ekm_cred;
    ```

     <span data-ttu-id="d55f8-198">인수에 대 한 변수를 사용 하 `CREATE CREDENTIAL` 고 클라이언트 ID에서 하이픈을 프로그래밍 방식으로 제거 하는 예는 [CREATE CREDENTIAL &#40;transact-sql&#41;](/sql/t-sql/statements/create-credential-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d55f8-198">For an example of using variables for the `CREATE CREDENTIAL` arguments and programmatically removing the hyphens from the Client ID, see [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql).</span></span>

3.  <span data-ttu-id="d55f8-199">섹션 3 의 1단계에서 설명한 대로 비대칭 키를 가져온 경우, 다음 예제에서 키 이름을 제공하여 키를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-199">If you imported an asymmetric key as described earlier in step 1, section 3, open the key by providing your key name in the following example.</span></span>

    ```sql
    CREATE ASYMMETRIC KEY CONTOSO_KEY 
    FROM PROVIDER [AzureKeyVault_EKM_Prov]
    WITH PROVIDER_KEY_NAME = 'ContosoMasterKey',
    CREATION_DISPOSITION = OPEN_EXISTING;
    ```

     <span data-ttu-id="d55f8-200">(키를 내보낼 수 없으므로)프로덕션 환경에 권장되지는 않지만, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 자격 증명 모음에 바로 비대칭 키를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-200">Though not recommended for production (because the key cannot be exported), it is possible to create an asymmetric key directly in the vault from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d55f8-201">앞에서 키를 가져오지 않았으면 다음 스크립트를 사용하여 테스트용으로 키 자격 증명 모음에 비대칭 키를 만드세요.</span><span class="sxs-lookup"><span data-stu-id="d55f8-201">If you did not import a key earlier, then create an asymmetric key in the key vault for testing by using the following script.</span></span> <span data-ttu-id="d55f8-202">**sysadmin_ekm_cred** 자격 증명으로 프로비저닝된 로그인을 사용하여 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-202">Execute the script, using a login provisioned with the **sysadmin_ekm_cred** credential.</span></span>

    ```sql
    CREATE ASYMMETRIC KEY CONTOSO_KEY 
    FROM PROVIDER [AzureKeyVault_EKM_Prov]
    WITH ALGORITHM = RSA_2048,
    PROVIDER_KEY_NAME = 'ContosoMasterKey';
    ```

> [!TIP]
>  <span data-ttu-id="d55f8-203">나타나는 오류 메시지: **공급자에서 공개 키를 내보낼 수 없습니다. 공급자 오류 코드: 2053.**</span><span class="sxs-lookup"><span data-stu-id="d55f8-203">Users receiving the error **Cannot export public key from the provider. Provider error code: 2053.**</span></span> <span data-ttu-id="d55f8-204">키 자격 증명 모음에서 **get**, CLE( CLE( **list**, CLE( CLE( **wrapKey**, CLE( CLE( and **unwrapKey** 권한을 필요로 합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-204">should check their **get**, **list**, **wrapKey**, and **unwrapKey** permissions in the key vault.</span></span>

 <span data-ttu-id="d55f8-205">자세한 내용은</span><span class="sxs-lookup"><span data-stu-id="d55f8-205">For more information, see the following:</span></span>

-   [<span data-ttu-id="d55f8-206">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d55f8-206">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)

-   [<span data-ttu-id="d55f8-207">CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d55f8-207">CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-cryptographic-provider-transact-sql)

-   [<span data-ttu-id="d55f8-208">CREATE CREDENTIAL &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d55f8-208">CREATE CREDENTIAL &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-credential-transact-sql)

-   [<span data-ttu-id="d55f8-209">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d55f8-209">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-asymmetric-key-transact-sql)

-   [<span data-ttu-id="d55f8-210">CREATE LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d55f8-210">CREATE LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-login-transact-sql)

-   [<span data-ttu-id="d55f8-211">ALTER LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d55f8-211">ALTER LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-login-transact-sql)

## <a name="examples"></a><span data-ttu-id="d55f8-212">예</span><span class="sxs-lookup"><span data-stu-id="d55f8-212">Examples</span></span>

###  <a name="example-a-transparent-data-encryption-by-using-an-asymmetric-key-from-the-key-vault"></a><a name="ExampleA"></a><span data-ttu-id="d55f8-213">예 A: Key Vault에서 비대칭 키를 사용 하 여 투명한 데이터 암호화</span><span class="sxs-lookup"><span data-stu-id="d55f8-213">Example A: Transparent Data Encryption by Using an Asymmetric Key from the Key Vault</span></span>
 <span data-ttu-id="d55f8-214">위의 단계를 완료했으면 자격 증명과 로그인을 만들고, 키 자격 증명 모음에 비대칭 키로 보호되는 데이터베이스 암호화 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-214">After completing the steps above, create a credential and a login, create a database encryption key protected by the asymmetric key in the key vault.</span></span> <span data-ttu-id="d55f8-215">데이터베이스 암호화 키를 사용하여 TDE로 데이터베이스를 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-215">Use the database encryption key to encrypt a database with TDE.</span></span>

 <span data-ttu-id="d55f8-216">데이터베이스를 암호화하려면 데이터베이스에 대한 CONTROL 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-216">To encrypt a database requires CONTROL permission on the database.</span></span>

##### <a name="to-enable-tde-using-ekm-and-the-key-vault"></a><span data-ttu-id="d55f8-217">EKM 및 키 자격 증명 모음을 사용한 TDE 사용 설정</span><span class="sxs-lookup"><span data-stu-id="d55f8-217">To enable TDE using EKM and the Key Vault</span></span>

1.  <span data-ttu-id="d55f8-218">데이터베이스 로드 동안 키 자격 증명 모음 EKM에 액세스할 때 사용할 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 용 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 자격 증명을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-218">Create a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] credential for the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] to use when accessing the key vault EKM during database load.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="d55f8-219">의 **IDENTITY** 인수에는 `CREATE CREDENTIAL` 키 자격 증명 모음 이름이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-219">The **IDENTITY** argument of `CREATE CREDENTIAL` requires the key vault name.</span></span> <span data-ttu-id="d55f8-220">의 **SECRET** 인수에 `CREATE CREDENTIAL` 는 *\<Client ID>* (하이픈이 없는)와 *\<Secret>* 사이에 공백 없이 함께 전달 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-220">The **SECRET** argument of `CREATE CREDENTIAL` requires the *\<Client ID>* (without hyphens) and *\<Secret>* to be passed together without a space between them.</span></span>

     <span data-ttu-id="d55f8-221">다음 예제에서 **클라이언트 ID** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`)는 하이픈이 제거되어 문자열 `EF5C8E094D2A4A769998D93440D8115D` 로 입력되어 있으며 **암호** 는 문자열 *SECRET_DBEngine*으로 표현되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-221">In the following example, the **Client ID** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) is stripped of the hyphens and entered as the string `EF5C8E094D2A4A769998D93440D8115D` and the **Secret** is represented by the string *SECRET_DBEngine*.</span></span>

    ```sql
    USE master;
    CREATE CREDENTIAL Azure_EKM_TDE_cred 
        WITH IDENTITY = 'ContosoKeyVault', 
        SECRET = 'EF5C8E094D2A4A769998D93440D8115DSECRET_DBEngine' 
        FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;
    ```

2.  <span data-ttu-id="d55f8-222">TDE용으로 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에서 사용할 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 로그인을 만들고 여기에 자격 증명을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-222">Create a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login to be used by the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] for TDE, and add the credential to it.</span></span> <span data-ttu-id="d55f8-223">이 예제에서는 위에 있는 [섹션 3의 3단계](#Step3) 에 설명된 대로 master 데이터베이스용으로 이전에 가져왔거나 만든 키 자격 증명 모음에 저장된 CONTOSO_KEY 비대칭 키를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-223">This example uses the CONTOSO_KEY asymmetric key stored in the key vault, which was imported or created earlier for the master database, as described in [Step 3, section 3](#Step3) above.</span></span>

    ```sql
    USE master;
    -- Create a SQL Server login associated with the asymmetric key 
    -- for the Database engine to use when it loads a database 
    -- encrypted by TDE.
    CREATE LOGIN TDE_Login 
    FROM ASYMMETRIC KEY CONTOSO_KEY;
    GO 

    -- Alter the TDE Login to add the credential for use by the 
    -- Database Engine to access the key vault
    ALTER LOGIN TDE_Login 
    ADD CREDENTIAL Azure_EKM_TDE_cred ;
    GO
    ```

3.  <span data-ttu-id="d55f8-224">TDE에 사용할 DEK(데이터베이스 암호화 키)를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-224">Create the database encryption key (DEK) that will be used for TDE.</span></span> <span data-ttu-id="d55f8-225">DEK는 SQL Server에서 지원되는 알고리즘 또는 키 길이를 사용하여 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-225">The DEK can be created using any SQL Server supported algorithm or key length.</span></span> <span data-ttu-id="d55f8-226">DEK는 키 자격 증명 모음에 있는 비대칭 키에 의해 보호됩니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-226">The DEK will be protected by the asymmetric key in the key vault.</span></span>

     <span data-ttu-id="d55f8-227">이 예제에서는 위에 있는 [섹션 3의 3단계](#Step3) 에 설명된 대로 앞에서 가져왔거나 만든 키 자격 증명 모음에 저장된 CONTOSO_KEY 비대칭 키를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-227">This example uses the CONTOSO_KEY asymmetric key stored in the key vault, which was imported or created earlier, as described in [Step 3, section 3](#Step3) above.</span></span>

    ```sql
    USE ContosoDatabase;
    GO

    CREATE DATABASE ENCRYPTION KEY 
    WITH ALGORITHM = AES_128 
    ENCRYPTION BY SERVER ASYMMETRIC KEY CONTOSO_KEY;
    GO

    -- Alter the database to enable transparent data encryption.
    ALTER DATABASE ContosoDatabase 
    SET ENCRYPTION ON ;
    GO
    ```

     <span data-ttu-id="d55f8-228">자세한 내용은</span><span class="sxs-lookup"><span data-stu-id="d55f8-228">For more information, see the following:</span></span>

    -   [<span data-ttu-id="d55f8-229">CREATE DATABASE ENCRYPTION KEY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d55f8-229">CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-encryption-key-transact-sql)

    -   [<span data-ttu-id="d55f8-230">ALTER DATABASE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d55f8-230">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)

###  <a name="example-b-encrypting-backups-by-using-an-asymmetric-key-from-the-key-vault"></a><a name="ExampleB"></a><span data-ttu-id="d55f8-231">예 2: Key Vault에서 비대칭 키를 사용 하 여 백업 암호화</span><span class="sxs-lookup"><span data-stu-id="d55f8-231">Example B: Encrypting Backups by Using an Asymmetric Key from the Key Vault</span></span>
 <span data-ttu-id="d55f8-232">암호화된 백업은 [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]부터 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-232">Encrypted backups are supported starting with [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)].</span></span> <span data-ttu-id="d55f8-233">다음 예제에서는 키 자격 증명 모음에서 비대칭 키로 보호되는 데이터 암호화 키로 암호화된 백업을 만들고 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-233">The following example creates and restores a backup encrypted a data encryption key protected by the asymmetric key in the key vault.</span></span>

```sql
USE master;
BACKUP DATABASE [DATABASE_TO_BACKUP]
TO DISK = N'[PATH TO BACKUP FILE]' 
WITH FORMAT, INIT, SKIP, NOREWIND, NOUNLOAD, 
ENCRYPTION(ALGORITHM = AES_256, SERVER ASYMMETRIC KEY = [CONTOSO_KEY]);
GO
```

 <span data-ttu-id="d55f8-234">샘플 복원 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-234">Sample restore code.</span></span>

```sql
RESTORE DATABASE [DATABASE_TO_BACKUP]
FROM DISK = N'[PATH TO BACKUP FILE]' WITH FILE = 1, NOUNLOAD, REPLACE;
GO
```

 <span data-ttu-id="d55f8-235">백업 옵션에 대 한 자세한 내용은 [backup &#40;transact-sql&#41;](/sql/t-sql/statements/backup-transact-sql)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d55f8-235">For more information about backup options, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>

###  <a name="example-c-column-level-encryption-by-using-an-asymmetric-key-from-the-key-vault"></a><a name="ExampleC"></a><span data-ttu-id="d55f8-236">예 C: Key Vault의 비대칭 키를 사용한 열 수준 암호화</span><span class="sxs-lookup"><span data-stu-id="d55f8-236">Example C: Column Level Encryption by Using an Asymmetric Key from the Key Vault</span></span>
 <span data-ttu-id="d55f8-237">다음 예제에서는 키 자격 증명 모음에 비대칭 키로 보호되는 대칭 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-237">The following example creates a symmetric key protected by the asymmetric key in the key vault.</span></span> <span data-ttu-id="d55f8-238">그런 다음 데이터베이스에서 대칭 키를 사용하여 데이터를 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-238">Then the symmetric key is used to encrypt data in the database.</span></span>

 <span data-ttu-id="d55f8-239">이 예제에서는 위에 있는 [섹션 3의 3단계](#Step3) 에 설명된 대로 앞에서 가져왔거나 만든 키 자격 증명 모음에 저장된 CONTOSO_KEY 비대칭 키를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-239">This example uses the CONTOSO_KEY asymmetric key stored in the key vault, which was imported or created earlier, as described in [Step 3, section 3](#Step3) above.</span></span> <span data-ttu-id="d55f8-240">`ContosoDatabase` 데이터베이스에서 이 비대칭 키를 사용하려면 다시 CREATE ASYMMETRIC KEY 문을 실행하여 `ContosoDatabase` 데이터베이스에 키에 대한 참조를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d55f8-240">To use this asymmetric key in the `ContosoDatabase` database, you must execute the CREATE ASYMMETRIC KEY statement again, to provide the `ContosoDatabase` database with a reference to the key.</span></span>

```sql
USE [ContosoDatabase];
GO

-- Create a reference to the key in the key vault
CREATE ASYMMETRIC KEY CONTOSO_KEY 
FROM PROVIDER [AzureKeyVault_EKM_Prov]
WITH PROVIDER_KEY_NAME = 'ContosoMasterKey',
CREATION_DISPOSITION = OPEN_EXISTING;

-- Create the data encryption key.
-- The data encryption key can be created using any SQL Server 
-- supported algorithm or key length.
-- The DEK will be protected by the asymmetric key in the key vault

CREATE SYMMETRIC KEY DATA_ENCRYPTION_KEY
    WITH ALGORITHM=AES_256
    ENCRYPTION BY ASYMMETRIC KEY CONTOSO_KEY;

DECLARE @DATA VARBINARY(MAX);

--Open the symmetric key for use in this session
OPEN SYMMETRIC KEY DATA_ENCRYPTION_KEY 
DECRYPTION BY ASYMMETRIC KEY CONTOSO_KEY;

--Encrypt syntax
SELECT @DATA = ENCRYPTBYKEY(KEY_GUID('DATA_ENCRYPTION_KEY'), CONVERT(VARBINARY,'Plain text data to encrypt'));

-- Decrypt syntax
SELECT CONVERT(VARCHAR, DECRYPTBYKEY(@DATA));

--Close the symmetric key
CLOSE SYMMETRIC KEY DATA_ENCRYPTION_KEY;
```

## <a name="see-also"></a><span data-ttu-id="d55f8-241">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d55f8-241">See Also</span></span>
 <span data-ttu-id="d55f8-242">[암호화 공급자 &#40;transact-sql&#41;](/sql/t-sql/statements/create-cryptographic-provider-transact-sql) [create CREDENTIAL&#41;&#40;](/sql/t-sql/statements/create-credential-transact-sql) transact-sql &#40;create 대칭 키&#41;transact-sql &#40;create 대칭 키&#41;[transact-sql &#40;create](/sql/t-sql/statements/create-asymmetric-key-transact-sql) [대칭 키](/sql/t-sql/statements/create-symmetric-key-transact-sql)&#41;[확장 가능 키 관리 EKM](extensible-key-management-ekm.md) ekm [백업 암호화](../../backup-restore/backup-encryption.md) 를 [사용 하 여 tde를 사용 하도록 설정](enable-tde-on-sql-server-using-ekm.md) [암호화 된 백업 만들기](../../backup-restore/create-an-encrypted-backup.md)</span><span class="sxs-lookup"><span data-stu-id="d55f8-242">[CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-cryptographic-provider-transact-sql) [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql) [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-symmetric-key-transact-sql) [Extensible Key Management &#40;EKM&#41;](extensible-key-management-ekm.md) [Enable TDE Using EKM](enable-tde-on-sql-server-using-ekm.md) [Backup Encryption](../../backup-restore/backup-encryption.md) [Create an Encrypted Backup](../../backup-restore/create-an-encrypted-backup.md)</span></span>
