---
title: Oracle 게시자에 대 한 트랜잭션 집합 작업 구성 (복제 Transact-sql 프로그래밍) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_publisherproperty
- Oracle publishing [SQL Server replication], configuring
ms.assetid: beea1a5c-0053-4971-a68f-0da53063fcbb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 43a25ce755a505f0efd7c25243b8969a962ea701
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741891"
---
# <a name="configure-the-transaction-set-job-for-an-oracle-publisher-replication-transact-sql-programming"></a><span data-ttu-id="2d531-102">Oracle 게시자에 대한 트랜잭션 세트 작업 구성(복제 Transact-SQL 프로그래밍)</span><span class="sxs-lookup"><span data-stu-id="2d531-102">Configure the Transaction Set Job for an Oracle Publisher (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="2d531-103">**Xactset** 작업은 로그 판독기 에이전트가 Oracle 게시자에 연결되어 있지 않을 때 해당 게시자에서 트랜잭션 세트를 만들기 위해 실행되는 복제를 통해 만들어지는 Oracle 데이터베이스 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="2d531-103">The **Xactset** job is an Oracle database job created by replication that runs at an Oracle Publisher to create transaction sets when the Log Reader Agent is not connected to the Publisher.</span></span> <span data-ttu-id="2d531-104">배포자에서 복제 저장 프로시저를 사용하여 프로그래밍 방식으로 이 작업을 사용하도록 설정하고 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d531-104">You can enable and configure this job from the Distributor programmatically using replication stored procedures.</span></span> <span data-ttu-id="2d531-105">자세한 내용은 [Oracle 게시자를 위한 성능 튜닝](../non-sql/performance-tuning-for-oracle-publishers.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2d531-105">For more information, see [Performance Tuning for Oracle Publishers](../non-sql/performance-tuning-for-oracle-publishers.md).</span></span>  
  
### <a name="to-enable-the-transaction-set-job"></a><span data-ttu-id="2d531-106">트랜잭션 세트 작업을 사용하도록 설정하려면</span><span class="sxs-lookup"><span data-stu-id="2d531-106">To enable the transaction set job</span></span>  
  
1.  <span data-ttu-id="2d531-107">Oracle 게시자에서 **job_queue_processes** 초기화 매개 변수를 Xactset 작업을 실행하기에 충분한 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2d531-107">At the Oracle Publisher, set the **job_queue_processes** initialization parameter to a sufficient value to allow the Xactset job run.</span></span> <span data-ttu-id="2d531-108">이 매개 변수에 대한 자세한 내용은 Oracle 게시자의 데이터베이스 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2d531-108">For more information about this parameter, see the database documentation for the Oracle Publisher.</span></span>  
  
2.  <span data-ttu-id="2d531-109">배포자에서 [sp_publisherproperty&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2d531-109">At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql).</span></span> <span data-ttu-id="2d531-110">\*\* \@ 게시자**에 대 한 Oracle 게시자의 이름, propertyname의 경우 값 `xactsetbatching` , \*\* \@ \*\* `enabled` \*\* \@ propertyvalue**에 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d531-110">Specify the name of the Oracle Publisher for **\@publisher**, a value of `xactsetbatching` for **\@propertyname**, and a value of `enabled` for **\@propertyvalue**.</span></span>  
  
3.  <span data-ttu-id="2d531-111">배포자에서 [sp_publisherproperty&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2d531-111">At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql).</span></span> <span data-ttu-id="2d531-112">\*\* \@ 게시자**에 대 한 Oracle 게시자의 이름, propertyname의 경우 값 `xactsetjobinterval` , \*\* \@ \*\* \*\* \@ propertyvalue**의 작업 간격 (분)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d531-112">Specify the name of the Oracle Publisher for **\@publisher**, a value of `xactsetjobinterval` for **\@propertyname**, and the job interval, in minutes, for **\@propertyvalue**.</span></span>  
  
4.  <span data-ttu-id="2d531-113">배포자에서 [sp_publisherproperty&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2d531-113">At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql).</span></span> <span data-ttu-id="2d531-114">\*\* \@ 게시자**에 대 한 Oracle 게시자의 이름, propertyname의 경우 값 `xactsetjob` , \*\* \@ \*\* `enabled` \*\* \@ propertyvalue**에 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d531-114">Specify the name of the Oracle Publisher for **\@publisher**, a value of `xactsetjob` for **\@propertyname**, and a value of `enabled` for **\@propertyvalue**.</span></span>  
  
### <a name="to-configure-the-transaction-set-job"></a><span data-ttu-id="2d531-115">트랜잭션 세트 작업을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="2d531-115">To configure the transaction set job</span></span>  
  
1.  <span data-ttu-id="2d531-116">(선택 사항) 배포자에서 [sp_publisherproperty&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2d531-116">(Optional) At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql).</span></span> <span data-ttu-id="2d531-117">**\@publisher**에 대해 Oracle 게시자의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2d531-117">Specify the name of the Oracle Publisher for **\@publisher**.</span></span> <span data-ttu-id="2d531-118">이렇게 하면 게시자에서 **Xactset** 작업의 속성이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d531-118">This returns properties of the **Xactset** job at the Publisher.</span></span>  
  
2.  <span data-ttu-id="2d531-119">배포자에서 [sp_publisherproperty&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2d531-119">At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql).</span></span> <span data-ttu-id="2d531-120">\*\* \@ 게시자**에 대 한 Oracle 게시자의 이름, \*\* \@ propertyname**에 대해 설정할 Xactset 작업 속성의 이름 및 \*\* \@ propertyvalue\*\*의 새 설정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d531-120">Specify the name of the Oracle Publisher for **\@publisher**, the name of the Xactset job property being set for **\@propertyname**, and new setting for **\@propertyvalue**.</span></span>  
  
3.  <span data-ttu-id="2d531-121">(옵션) 설정할 각 Xactset 작업 속성에 대해 2단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="2d531-121">(Optional) Repeat step 2 for each Xactset job property being set.</span></span> <span data-ttu-id="2d531-122">속성을 변경 하는 경우 `xactsetjobinterval` Oracle 게시자의 작업을 다시 시작 해야 새 간격이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d531-122">When changing the `xactsetjobinterval` property, you must restart the job on the Oracle Publisher for the new interval to take effect.</span></span>  
  
### <a name="to-view-properties-of-the-transaction-set-job"></a><span data-ttu-id="2d531-123">트랜잭션 세트 작업의 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="2d531-123">To view properties of the transaction set job</span></span>  
  
1.  <span data-ttu-id="2d531-124">배포자에서 [sp_helpxactsetjob](/sql/relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2d531-124">At the Distributor, execute [sp_helpxactsetjob](/sql/relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql).</span></span> <span data-ttu-id="2d531-125">**\@publisher**에 대해 Oracle 게시자의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2d531-125">Specify the name of the Oracle Publisher for **\@publisher**.</span></span>  
  
### <a name="to-disable-the-transaction-set-job"></a><span data-ttu-id="2d531-126">트랜잭션 세트 작업을 사용하지 않도록 설정하려면</span><span class="sxs-lookup"><span data-stu-id="2d531-126">To disable the transaction set job</span></span>  
  
1.  <span data-ttu-id="2d531-127">배포자에서 [sp_publisherproperty&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2d531-127">At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql).</span></span> <span data-ttu-id="2d531-128">\*\* \@ 게시자**에 대 한 Oracle 게시자의 이름, propertyname의 경우 값 `xactsetjob` , \*\* \@ \*\* `disabled` \*\* \@ propertyvalue**에 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d531-128">Specify the name of the Oracle Publisher for **\@publisher**, a value of `xactsetjob` for **\@propertyname**, and a value of `disabled` for **\@propertyvalue**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d531-129">예제</span><span class="sxs-lookup"><span data-stu-id="2d531-129">Example</span></span>  
 <span data-ttu-id="2d531-130">다음 예제에서는 `Xactset` 작업을 사용하도록 설정하고 실행 간격을 3분으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2d531-130">The following example enables the `Xactset` job and sets an interval of three minutes between runs.</span></span>  
  
 [!code-sql[HowTo#sp_enable_xactsetjob](../../../snippets/tsql/SQL15/replication/howto/tsql/enablexactsetjob.sql#sp_enable_xactsetjob)]  
  
## <a name="see-also"></a><span data-ttu-id="2d531-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2d531-131">See Also</span></span>  
 <span data-ttu-id="2d531-132">[Oracle 게시자를 위한 성능 튜닝](../non-sql/performance-tuning-for-oracle-publishers.md) </span><span class="sxs-lookup"><span data-stu-id="2d531-132">[Performance Tuning for Oracle Publishers](../non-sql/performance-tuning-for-oracle-publishers.md) </span></span>  
 [<span data-ttu-id="2d531-133">Replication System Stored Procedures Concepts</span><span class="sxs-lookup"><span data-stu-id="2d531-133">Replication System Stored Procedures Concepts</span></span>](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
