---
title: DML 트리거 내에서 inserted 및 deleted 테이블에 대 한 DDL 작업 제거 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- data definition language [SQL Server]
- DDL statements [SQL Server]
- DML triggers, removing DDL operations
ms.assetid: e49ba7d5-787f-4052-b985-b699195d982b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 61f7ab78b5ab6251b7f27401d36423ec27141c4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735912"
---
# <a name="remove-ddl-operations-on-the-inserted-and-deleted-tables-inside-dml-triggers"></a><span data-ttu-id="1ba53-102">DML 트리거 내부의 inserted 및 deleted 테이블에 대한 DDL 작업을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba53-102">Remove DDL operations on the inserted and deleted tables inside DML triggers</span></span>
  <span data-ttu-id="1ba53-103">CREATE INDEX와 같은 DDL (데이터 정의 언어) 문은 DML 트리거 내부의 inserted 및 deleted 테이블에서 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba53-103">Data definition language (DDL) statements, such as CREATE INDEX, cannot be performed on the inserted and deleted tables inside DML triggers.</span></span> <span data-ttu-id="1ba53-104">그러나 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 inserted 및 deleted 테이블에 대해 일부 DDL 문이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba53-104">Some DDL statements on the inserted and deleted tables are permitted in earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1ba53-105">자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 "inserted 및 deleted 테이블 사용"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1ba53-105">For more information, see "Using the inserted and deleted Tables" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="component"></a><span data-ttu-id="1ba53-106">구성 요소</span><span class="sxs-lookup"><span data-stu-id="1ba53-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="1ba53-107">수정 동작</span><span class="sxs-lookup"><span data-stu-id="1ba53-107">Corrective Action</span></span>  
 <span data-ttu-id="1ba53-108">DML 트리거 내에서 inserted 및 deleted 테이블에 대해 수행되는 DDL 작업을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba53-108">Remove any DDL operations that are performed on the inserted and deleted tables inside DML triggers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ba53-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1ba53-109">See Also</span></span>  
 <span data-ttu-id="1ba53-110">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="1ba53-110">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="1ba53-111">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="1ba53-111">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
