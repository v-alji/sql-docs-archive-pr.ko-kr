---
title: 데이터 컬렉션 매개 변수 구성(Transact-SQL) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collection [SQL Server]
ms.assetid: 850905b6-35d2-4ed1-ab51-de64daa832b2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a8333b47612b4fbd933ef132e886b8125ffb58a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734151"
---
# <a name="configure-data-collection-parameters-transact-sql"></a><span data-ttu-id="ae4b3-102">데이터 컬렉션 매개 변수 구성(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ae4b3-102">Configure Data Collection Parameters (Transact-SQL)</span></span>
  <span data-ttu-id="ae4b3-103">사용자 지정 컬렉션 집합을 만들기 전에 먼저 데이터 컬렉션 매개 변수를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae4b3-103">Before you create a custom collection set, you must first configure data collection parameters.</span></span> <span data-ttu-id="ae4b3-104">데이터 수집기에서 제공하는 저장 프로시저를 사용하여 이를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae4b3-104">You can do this by using the stored procedures that are provided with the data collector.</span></span> <span data-ttu-id="ae4b3-105">이 태스크를 수행하려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 쿼리 편집기를 사용하여 다음 절차를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae4b3-105">Accomplishing this task involves using Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to carry out the following procedure.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ae4b3-106">데이터 컬렉션 매개 변수는 한 번만 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="ae4b3-106">You only configure data collection parameters once.</span></span> <span data-ttu-id="ae4b3-107">구성 후 이러한 매개 변수는 생성된 추가 컬렉션 집합에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae4b3-107">After configuration, these parameters are used for any additional collection sets that you create.</span></span>  
  
### <a name="configure-data-collection-parameters"></a><span data-ttu-id="ae4b3-108">데이터 컬렉션 매개 변수 구성</span><span class="sxs-lookup"><span data-stu-id="ae4b3-108">Configure data collection parameters</span></span>  
  
1.  <span data-ttu-id="ae4b3-109">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 사용자 지정 컬렉션 집합을 만들 데이터베이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ae4b3-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the database where you want to create a custom collection set.</span></span>  
  
2.  <span data-ttu-id="ae4b3-110">쿼리 편집기에서 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ae4b3-110">In Query Editor, issue the following statements.</span></span>  
  
    ```sql  
    USE msdb;  
    EXEC sp_syscollector_set_warehouse_instance_name N'INSTANCE_NAME';-- where instance name is the name of the SQL Server instance  
    EXEC sp_syscollector_set_warehouse_database_name N'MDW';  
    EXEC sp_syscollector_set_cache_directory N'D:\tempdata';  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ae4b3-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ae4b3-111">See Also</span></span>  
 <span data-ttu-id="ae4b3-112">[데이터 컬렉션](data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="ae4b3-112">[Data Collection](data-collection.md) </span></span>  
 [<span data-ttu-id="ae4b3-113">데이터 수집기 저장 프로시저&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ae4b3-113">Data Collector Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql)  
  
  
