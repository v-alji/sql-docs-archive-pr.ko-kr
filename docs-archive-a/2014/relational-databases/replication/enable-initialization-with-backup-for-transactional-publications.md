---
title: 트랜잭션 게시에 대 한 백업으로 초기화 사용 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- manual subscription initialization [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], without snapshots
- transactional replication, backup and restore
- backups [SQL Server replication], transactional replication
ms.assetid: 9df00514-aa9d-4ac6-9766-d226c9958175
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f5e22614c8c4f5250db3966e747b686091512774
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646902"
---
# <a name="enable-initialization-with-a-backup-for-transactional-publications-sql-server-management-studio"></a><span data-ttu-id="59a70-102">트랜잭션 게시에 대한 백업으로 초기화 설정(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="59a70-102">Enable Initialization with a Backup for Transactional Publications (SQL Server Management Studio)</span></span>
  <span data-ttu-id="59a70-103">백업에서 트랜잭션 게시에 대한 구독을 초기화하려면 백업에서 초기화할 수 있도록 게시를 설정한 다음 구독을 만들 때 백업 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="59a70-103">To initialize a subscription to a transactional publication from a backup, enable the publication to allow initialization from a backup, and then specify backup information when creating the subscription:</span></span>  
  
-   <span data-ttu-id="59a70-104">**게시 속성 - \<Publication>** 대화 상자의 **구독 옵션** 페이지에서 이 게시를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="59a70-104">Enable the publication on the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="59a70-105">이 대화 상자에 액세스하는 방법은 [게시 속성 보기 및 수정](publish/view-and-modify-publication-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="59a70-105">For more information about accessing this dialog box, see [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md).</span></span>  
  
-   <span data-ttu-id="59a70-106">[sp_addsubscription&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) 저장 프로시저를 사용하여 백업 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="59a70-106">Specify backup information with the stored procedure [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql).</span></span> <span data-ttu-id="59a70-107">**sp_addsubscription**에 필요한 매개 변수에 대한 자세한 내용은 [트랜잭션 구독을 백업에서 초기화&#40;복제 Transact-SQL 프로그래밍&#41;](initialize-a-transactional-subscription-from-a-backup.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="59a70-107">For more information about the parameters required by **sp_addsubscription**, see [Initialize a Transactional Subscription from a Backup &#40;Replication Transact-SQL Programming&#41;](initialize-a-transactional-subscription-from-a-backup.md).</span></span>  
  
### <a name="to-enable-initialization-with-a-backup"></a><span data-ttu-id="59a70-108">백업으로 초기화를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="59a70-108">To enable initialization with a backup</span></span>  
  
1.  <span data-ttu-id="59a70-109">**게시 속성 - \<Publication>** 대화 상자의 **구독 옵션** 페이지에서 **백업 파일에서 초기화 허용** 옵션에 대해 **True** 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="59a70-109">On the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box, select a value of **True** for the **Allow initialization from backup files** option.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59a70-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="59a70-110">See Also</span></span>  
 [<span data-ttu-id="59a70-111">스냅샷 없이 트랜잭션 구독 초기화</span><span class="sxs-lookup"><span data-stu-id="59a70-111">Initialize a Transactional Subscription Without a Snapshot</span></span>](initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  
