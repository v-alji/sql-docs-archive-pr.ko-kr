---
title: 병합 게시에서 데이터를 테이블로 대량 로드 (복제 Transact-sql 프로그래밍) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- bulk load [SQL Server replication]
- merge replication bulk loading [SQL Server replication]
- sp_addtabletocontents
ms.assetid: 16e6498a-b449-4051-aec4-ea814a2ad993
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f669a1f7132aa0f588fd89fb9747a7dc9017fcf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741856"
---
# <a name="bulk-load-data-into-tables-in-a-merge-publication-replication-transact-sql-programming"></a><span data-ttu-id="5bdc5-102">병합 게시에서 데이터를 테이블로 대량 로드(복제 Transact-SQL 프로그래밍)</span><span class="sxs-lookup"><span data-stu-id="5bdc5-102">Bulk-Load Data into Tables in a Merge Publication (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="5bdc5-103">[bcp 유틸리티](../../tools/bcp-utility.md) 또는 [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) 명령을 사용하여 데이터를 테이블로 로드할 경우 기본적으로 [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql) 시스템 테이블의 추적 데이터를 유지 관리하는 병합 복제 트리거가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5bdc5-103">When data is loaded into tables using the [bcp Utility](../../tools/bcp-utility.md) or the [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) command, by default, the merge replication triggers that maintain tracking data in the [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql) system table are not fired.</span></span> <span data-ttu-id="5bdc5-104">데이터가 로드될 때 병합 복제 트리거가 강제로 발생하도록 하거나 복제 저장 프로시저를 사용하여 대량 복사 작업을 수행한 후 생성된 복제 메타데이터를 프로그래밍 방식으로 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bdc5-104">You can either force the merge replication triggers to fire as the data is loaded, or you can insert the generated replication metadata programmatically after the bulk copy operation using replication stored procedures.</span></span>  
  
### <a name="to-bulk-load-data-into-tables-published-by-merge-replication-using-the-bcp-utility"></a><span data-ttu-id="5bdc5-105">bcp 유틸리티를 사용하여 병합 복제를 통해 게시된 테이블로 데이터를 대량으로 로드하려면</span><span class="sxs-lookup"><span data-stu-id="5bdc5-105">To bulk-load data into tables published by merge replication using the bcp utility</span></span>  
  
1.  <span data-ttu-id="5bdc5-106">게시자나 구독자에서 [bcp Utility](../../tools/bcp-utility.md) 또는 [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) 를 실행하여 병합 복제를 통해 게시된 테이블에 데이터를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="5bdc5-106">At either the Publisher or Subscriber, execute the [bcp Utility](../../tools/bcp-utility.md) or [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) to insert data into a table published using merge replication.</span></span>  
  
2.  <span data-ttu-id="5bdc5-107">다음 방법 중 하나를 사용하여 삽입된 데이터에 대한 복제 메타데이터가 생성되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bdc5-107">Use one of the following methods to ensure that replication metadata is generated for the inserted data.</span></span>  
  
    -   <span data-ttu-id="5bdc5-108">FIRE_TRIGGERS 옵션을 사용하여 대량 복사를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5bdc5-108">Execute the bulk copy using the FIRE_TRIGGERS option.</span></span>  
  
    -   <span data-ttu-id="5bdc5-109">데이터가 삽입된 데이터베이스에서 [sp_addtabletocontents&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addtabletocontents-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5bdc5-109">On the database into which data was inserted, execute [sp_addtabletocontents &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addtabletocontents-transact-sql).</span></span> <span data-ttu-id="5bdc5-110">데이터가 삽입 된 테이블 이름을 지정 **@table_name** 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bdc5-110">Specify the table name into which the data was inserted for **@table_name**.</span></span>  
  
  
