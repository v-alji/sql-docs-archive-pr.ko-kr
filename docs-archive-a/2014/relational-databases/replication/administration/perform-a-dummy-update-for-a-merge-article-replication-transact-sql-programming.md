---
title: 병합 아티클에 대해 더미 업데이트 수행 (복제 Transact-sql 프로그래밍) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_mergedummyupdate
- dummy updates [SQL Server replication]
ms.assetid: 2f339210-4d85-4843-bd94-e86f7100d3ef
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 07fa0f868b2c3f98496046b138424d7d3a2fa2fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736273"
---
# <a name="perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming"></a><span data-ttu-id="337e0-102">병합 아티클에 대해 더미 업데이트 수행(복제 Transact-SQL 프로그래밍)</span><span class="sxs-lookup"><span data-stu-id="337e0-102">Perform a Dummy Update for a Merge Article (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="337e0-103">병합 복제에서는 복제 프로세스의 일부로 트리거가 사용됩니다. 게시된 테이블이 업데이트될 경우 업데이트 트리거가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="337e0-103">Merge replication uses triggers as part of the replication process; when an update is made to published table, an update trigger fires.</span></span> <span data-ttu-id="337e0-104">WRITETEXT 및 UPDATETEXT 작업을 수행할 때와 같은 일부 경우에는 트리거를 발생시키지 않고 데이터를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="337e0-104">In some cases, data can be updated without the trigger firing, such as during the WRITETEXT and UPDATETEXT operations.</span></span> <span data-ttu-id="337e0-105">이러한 경우 변경 내용을 명시적으로 복제하려면 더미 UPDATE 문을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="337e0-105">In these cases, you need to add a dummy UPDATE statement explicitly to replicate the change.</span></span> <span data-ttu-id="337e0-106">복제 저장 프로시저를 사용하여 더미 UPDATE 문을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="337e0-106">You can add a dummy UPDATE statement using replication stored procedures.</span></span>  
  
### <a name="to-add-a-dummy-update-statement"></a><span data-ttu-id="337e0-107">더미 UPDATE 문을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="337e0-107">To add a dummy UPDATE statement</span></span>  
  
1.  <span data-ttu-id="337e0-108">더미 업데이트가 필요한 병합 게시된 테이블의 행에 대해 UPDATETEXT와 같은 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="337e0-108">Execute the operation (for example, UPDATETEXT) on a row in a merge published table  that requires a dummy update.</span></span>  
  
2.  <span data-ttu-id="337e0-109">변경된 데이터베이스의 서버(게시자 또는 구독자)에서 [sp_mergedummyupdate&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergedummyupdate-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="337e0-109">At the server (Publisher or Subscriber) on the database where the change was made, execute [sp_mergedummyupdate &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergedummyupdate-transact-sql).</span></span> <span data-ttu-id="337e0-110">에 대해 변경 된 테이블을 지정 **@source_object** 하 고에 대해 변경 된 행의 고유 식별자를 지정 합니다 **@rowguid** .</span><span class="sxs-lookup"><span data-stu-id="337e0-110">Specify the table on which the change was made for **@source_object**, and the unique identifier of the changed row for **@rowguid**.</span></span>  
  
3.  <span data-ttu-id="337e0-111">구독을 동기화하여 변경된 행을 복제합니다.</span><span class="sxs-lookup"><span data-stu-id="337e0-111">Synchronize the subscription to replicate the changed row.</span></span>  
  
  
