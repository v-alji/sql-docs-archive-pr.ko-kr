---
title: Blob (binary large object)를 읽고 쓰는 UPDATETEXT 문을 수정 합니다. Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- UPDATETEXT statement
- text [SQL Server], UPDATETEXT statements
ms.assetid: b85da6a7-42f6-4707-a25e-3ded8958b94f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 061e7bad0bae5a74d103406265ad79195f79f7db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650467"
---
# <a name="modify-updatetext-statements-that-read-and-write-to-binary-large-objects-blobs"></a><span data-ttu-id="de2a9-102">BLOB(Binary Large Object) 읽기/쓰기를 수행하는 UPDATETEXT 문을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="de2a9-102">Modify UPDATETEXT statements that read and write to binary large objects (BLOBs)</span></span>
  <span data-ttu-id="de2a9-103">업그레이드 관리자가 동일한 텍스트 포인터를 사용하여 동일한 BLOB(Binary Large Object) 읽기/쓰기를 수행하는 UPDATETEXT 문을 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="de2a9-103">Upgrade Advisor detected UPDATETEXT statements that read and write to the same binary large objects (BLOB) by using the same text pointer.</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="de2a9-104">에서는 이러한 방식으로 텍스트 포인터를 사용하는 것을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="de2a9-104">does not support the use of text pointers in this manner.</span></span>  
  
## <a name="component"></a><span data-ttu-id="de2a9-105">구성 요소</span><span class="sxs-lookup"><span data-stu-id="de2a9-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="de2a9-106">수정 동작</span><span class="sxs-lookup"><span data-stu-id="de2a9-106">Corrective Action</span></span>  
 <span data-ttu-id="de2a9-107">BLOB을 임시 테이블 또는 테이블 변수로 복사한 다음 이 값을 다시 원래 열에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="de2a9-107">Copy the BLOB to a temporary table or to a table variable, and then assign the value back to the original column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de2a9-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="de2a9-108">See Also</span></span>  
 <span data-ttu-id="de2a9-109">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="de2a9-109">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="de2a9-110">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="de2a9-110">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
