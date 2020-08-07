---
title: 암호화된 열의 데이터 복제(SQL Server Management Studio) | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], replicating data
- encryption [SQL Server replication]
- publishing [SQL Server replication], encrypted columns
ms.assetid: d1f8f586-e5a3-4a71-9391-11198d42bfa3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2e1528d81faa352fdcdf37abe9ad93fda190445c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732567"
---
# <a name="replicate-data-in-encrypted-columns-sql-server-management-studio"></a><span data-ttu-id="d94f0-102">암호화된 열의 데이터 복제(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="d94f0-102">Replicate Data in Encrypted Columns (SQL Server Management Studio)</span></span>
  <span data-ttu-id="d94f0-103">복제를 사용하여 암호화된 열 데이터를 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-103">Replication enables you to publish encrypted column data.</span></span> <span data-ttu-id="d94f0-104">구독자에서 이 데이터를 해독하고 사용하려면 게시자에서 데이터 암호화에 사용된 키가 구독자에도 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-104">To decrypt and use this data at the Subscriber, the key that was used to encrypt the data at the Publisher must also be present on the Subscriber.</span></span> <span data-ttu-id="d94f0-105">복제에서는 암호화 키를 전송하는 보안 메커니즘을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-105">Replication does not provide a secure mechanism to transport encryption keys.</span></span> <span data-ttu-id="d94f0-106">구독자에서 직접 암호화 키를 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-106">You must manually re-create the encryption key at the Subscriber.</span></span> <span data-ttu-id="d94f0-107">이 항목에서는 게시자에서 열을 암호화하고 구독자에서 암호화 키를 사용할 수 있게 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-107">This topic shows you how to encrypt a column at the Publisher and make sure that the encryption key is available at the Subscriber.</span></span>  
  
 <span data-ttu-id="d94f0-108">기본적인 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-108">The basic steps are as follows:</span></span>  
  
1.  <span data-ttu-id="d94f0-109">게시자에서 대칭 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-109">Create the symmetric key at the Publisher.</span></span>  
  
2.  <span data-ttu-id="d94f0-110">대칭 키를 사용하여 열 데이터를 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-110">Encrypt column data with the symmetric key.</span></span>  
  
3.  <span data-ttu-id="d94f0-111">암호화된 열이 있는 테이블을 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-111">Publish the table with the encrypted column.</span></span>  
  
4.  <span data-ttu-id="d94f0-112">게시를 구독합니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-112">Subscribe to the publication.</span></span>  
  
5.  <span data-ttu-id="d94f0-113">구독을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-113">Initialize the subscription.</span></span>  
  
6.  <span data-ttu-id="d94f0-114">ALGORITHM, KEY_SOURCE 및 IDENTITY_VALUE에 대해 1단계와 동일한 값을 사용하여 구독자에서 대칭 키를 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-114">Recreate the symmetric key at the Subscriber using same values for ALGORITHM, KEY_SOURCE, and IDENTITY_VALUE as in step 1.</span></span>  
  
7.  <span data-ttu-id="d94f0-115">암호화된 열 데이터에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-115">Access the encrypted column data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d94f0-116">대칭 키를 사용하여 열 데이터를 암호화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-116">You should use a symmetric key to encrypt column data.</span></span> <span data-ttu-id="d94f0-117">대칭 키 자체는 게시자와 구독자에서 다른 방법으로 보안을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-117">The symmetric key itself can be secured by different means at the Publisher and Subscriber.</span></span>  
  
### <a name="to-create-and-replicate-encrypted-column-data"></a><span data-ttu-id="d94f0-118">암호화된 열 데이터를 만들고 복제하려면</span><span class="sxs-lookup"><span data-stu-id="d94f0-118">To create and replicate encrypted column data</span></span>  
  
1.  <span data-ttu-id="d94f0-119">게시자에서 [CREATE SYMMETRIC KEY](/sql/t-sql/statements/create-symmetric-key-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-119">At the Publisher, execute [CREATE SYMMETRIC KEY](/sql/t-sql/statements/create-symmetric-key-transact-sql).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d94f0-120">KEY_SOURCE 값은 대칭 키를 다시 만들고 데이터를 해독하는 데 사용할 수 있는 중요한 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-120">The value of KEY_SOURCE is valuable data that can be used to re-create the symmetric key and decrypt data.</span></span> <span data-ttu-id="d94f0-121">KEY_SOURCE는 항상 안전하게 저장하고 전송해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-121">KEY_SOURCE must always be stored and transported securely.</span></span>  
  
2.  <span data-ttu-id="d94f0-122">[OPEN SYMMETRIC KEY](/sql/t-sql/statements/open-symmetric-key-transact-sql) 를 실행하여 새 키를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-122">Execute [OPEN SYMMETRIC KEY](/sql/t-sql/statements/open-symmetric-key-transact-sql) to open the new key.</span></span>  
  
3.  <span data-ttu-id="d94f0-123">[EncryptByKey](/sql/t-sql/functions/encryptbykey-transact-sql) 함수를 사용하여 게시자에서 열 데이터를 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-123">Use the [EncryptByKey](/sql/t-sql/functions/encryptbykey-transact-sql) function to encrypt column data at the Publisher.</span></span>  
  
4.  <span data-ttu-id="d94f0-124">[CLOSE SYMMETRIC KEY](/sql/t-sql/statements/close-symmetric-key-transact-sql) 를 실행하여 키를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-124">Execute [CLOSE SYMMETRIC KEY](/sql/t-sql/statements/close-symmetric-key-transact-sql) to close the key.</span></span>  
  
5.  <span data-ttu-id="d94f0-125">암호화된 열이 있는 테이블을 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-125">Publish the table that contains the encrypted column.</span></span> <span data-ttu-id="d94f0-126">자세한 내용은 [게시 만들기](../publish/create-a-publication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d94f0-126">For more information, see [Create a Publication](../publish/create-a-publication.md).</span></span>  
  
6.  <span data-ttu-id="d94f0-127">게시를 구독합니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-127">Subscribe to the publication.</span></span> <span data-ttu-id="d94f0-128">자세한 내용은 [끌어오기 구독 만들기](../create-a-pull-subscription.md) 또는 [밀어넣기 구독 만들기](../create-a-push-subscription.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d94f0-128">For more information, see [Create a Pull Subscription](../create-a-pull-subscription.md) or [Create a Push Subscription](../create-a-push-subscription.md).</span></span>  
  
7.  <span data-ttu-id="d94f0-129">구독을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-129">Initialize the subscription.</span></span> <span data-ttu-id="d94f0-130">자세한 내용은 [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d94f0-130">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
8.  <span data-ttu-id="d94f0-131">ALGORITHM, KEY_SOURCE 및 IDENTITY_VALUE에 대해 1단계와 동일한 값을 사용하여 구독자에서 [CREATE SYMMETRIC KEY](/sql/t-sql/statements/create-symmetric-key-transact-sql) 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-131">At the Subscriber, execute [CREATE SYMMETRIC KEY](/sql/t-sql/statements/create-symmetric-key-transact-sql) using the same values for ALGORITHM, KEY_SOURCE, and IDENTITY_VALUE as in step 1.</span></span> <span data-ttu-id="d94f0-132">ENCRYPTION BY에는 다른 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-132">You can specify a different value for ENCRYPTION BY.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d94f0-133">KEY_SOURCE 값은 대칭 키를 다시 만들고 데이터를 해독하는 데 사용할 수 있는 중요한 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-133">The value of KEY_SOURCE is valuable data that can be used to re-create the symmetric key and decrypt data.</span></span> <span data-ttu-id="d94f0-134">KEY_SOURCE는 항상 안전하게 저장하고 전송해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-134">KEY_SOURCE must always be stored and transported securely.</span></span>  
  
9. <span data-ttu-id="d94f0-135">[OPEN SYMMETRIC KEY](/sql/t-sql/statements/open-symmetric-key-transact-sql) 를 실행하여 새 키를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-135">Execute [OPEN SYMMETRIC KEY](/sql/t-sql/statements/open-symmetric-key-transact-sql) to open the new key.</span></span>  
  
10. <span data-ttu-id="d94f0-136">구독자에서 [DecryptByKey](/sql/t-sql/functions/decryptbykey-transact-sql) 함수를 사용하여 복제된 데이터를 해독합니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-136">Use the [DecryptByKey](/sql/t-sql/functions/decryptbykey-transact-sql) function to decrypt replicated data at the Subscriber.</span></span>  
  
11. <span data-ttu-id="d94f0-137">[CLOSE SYMMETRIC KEY](/sql/t-sql/statements/close-symmetric-key-transact-sql) 를 실행하여 키를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-137">Execute [CLOSE SYMMETRIC KEY](/sql/t-sql/statements/close-symmetric-key-transact-sql) to close the key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d94f0-138">예제</span><span class="sxs-lookup"><span data-stu-id="d94f0-138">Example</span></span>  
 <span data-ttu-id="d94f0-139">이 예에서는 대칭 키, 대칭 키의 보안 설정에 사용되는 인증서 및 마스터 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-139">This example creates a symmetric key, a certificate that is used to help secure the symmetric key, and a master key.</span></span> <span data-ttu-id="d94f0-140">이러한 키는 게시 데이터베이스에서 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-140">These keys are created in the publication database.</span></span> <span data-ttu-id="d94f0-141">그런 다음 `SalesOrderHeader` 테이블에서 암호화된 열(EncryptedCreditCardApprovalCode)을 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-141">They are then used to create an encrypted column (EncryptedCreditCardApprovalCode) in the `SalesOrderHeader` table.</span></span> <span data-ttu-id="d94f0-142">이 열은 암호화되지 않은 CreditCardApprovalCode 열 대신 AdvWorksSalesOrdersMerge 게시에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-142">This column is published in the AdvWorksSalesOrdersMerge publication instead of the unencrypted CreditCardApprovalCode column.</span></span> <span data-ttu-id="d94f0-143">가능한 경우 런타임 시 사용자에게 보안 자격 증명을 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-143">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="d94f0-144">자격 증명을 스크립트 파일에 저장해야 하는 경우에는 파일에 무단으로 액세스하지 못하도록 보안을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-144">If you must store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
 [!code-sql[HowTo#sp_PublishEncryptedColumn](../../../snippets/tsql/SQL15/replication/howto/tsql/publishencryptedcolumn.sql#sp_publishencryptedcolumn)]  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
## <a name="example"></a><span data-ttu-id="d94f0-145">예제</span><span class="sxs-lookup"><span data-stu-id="d94f0-145">Example</span></span>  
 <span data-ttu-id="d94f0-146">이 예에서는 첫 번째 예의 ALGORITHM, KEY_SOURCE 및 IDENTITY_VALUE에 동일한 값을 사용하여 구독 데이터베이스에서 같은 대칭 키를 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-146">This example recreates the same symmetric key in the subscription database using the same values for ALGORITHM, KEY_SOURCE, and IDENTITY_VALUE from the first example.</span></span> <span data-ttu-id="d94f0-147">암호화된 열을 복제하기 위해 AdvWorksSalesOrdersMerge 게시에 대한 구독을 이미 초기화했다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-147">This example assumes that you have already initialized a subscription to the AdvWorksSalesOrdersMerge publication to replicate the encrypted column.</span></span> <span data-ttu-id="d94f0-148">가능한 경우 런타임 시 사용자에게 보안 자격 증명을 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-148">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="d94f0-149">스크립트 파일에 자격 증명을 저장해야 하는 경우에는 스토리지 및 전송 중에 무단으로 액세스하지 못하도록 파일에 보안을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d94f0-149">If you must store credentials in a script file, you must secure the file during storage and transport to prevent unauthorized access.</span></span>  
  
 [!code-sql[HowTo#sp_SubscriberEncryptedColumn](../../../snippets/tsql/SQL15/replication/howto/tsql/subscriberencryptedcolumn.sql#sp_subscriberencryptedcolumn)]  
  
## <a name="see-also"></a><span data-ttu-id="d94f0-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d94f0-150">See Also</span></span>  
 <span data-ttu-id="d94f0-151">[SQL Server 복제 보안](view-and-modify-replication-security-settings.md) </span><span class="sxs-lookup"><span data-stu-id="d94f0-151">[SQL Server Replication Security](view-and-modify-replication-security-settings.md) </span></span>  
 [<span data-ttu-id="d94f0-152">두 서버에서 동일한 대칭 키 만들기</span><span class="sxs-lookup"><span data-stu-id="d94f0-152">Create Identical Symmetric Keys on Two Servers</span></span>](../../security/encryption/create-identical-symmetric-keys-on-two-servers.md)  
  
  
