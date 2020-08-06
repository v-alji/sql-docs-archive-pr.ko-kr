---
title: 테이블 반환 매개 변수 (SQL Server Native Client) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, table-valued parameters
- table-valued parameters (SQL Server Native Client)
ms.assetid: 5ee6bdcd-0309-4a20-b5c2-0e6b6839f34f
author: rothja
ms.author: jroth
ms.openlocfilehash: 6af4979b9a77c94f52be5197b01179007a971283
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647656"
---
# <a name="table-valued-parameters-sql-server-native-client"></a><span data-ttu-id="b6b35-102">테이블 반환 매개 변수(SQL Server Native Client)</span><span class="sxs-lookup"><span data-stu-id="b6b35-102">Table-Valued Parameters (SQL Server Native Client)</span></span>
  <span data-ttu-id="b6b35-103">테이블 반환 매개 변수는 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]에서 도입되었으며 여러 개의 데이터 행을 서버로 전달하는 효율적인 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b35-103">Table-valued parameters were introduced in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], and provide an efficient way to pass multiple rows of data to the server.</span></span> <span data-ttu-id="b6b35-104">테이블 반환 매개 변수는 매개 변수 배열과 유사한 기능을 제공하지만 더 유연하며 [!INCLUDE[tsql](../../../includes/tsql-md.md)]과 더 밀접하게 통합될 뿐만 아니라 대체로 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6b35-104">Table-valued parameters provide functionality similar to parameter arrays, but they offer more flexibility and closer integration with [!INCLUDE[tsql](../../../includes/tsql-md.md)], and can frequently improve performance.</span></span> <span data-ttu-id="b6b35-105">또한 테이블 반환 매개 변수는 집합 기반 작업에 참여할 수 있지만 매개 변수 배열은 참여할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b6b35-105">Table-valued parameters can also participate in set-based operations, whereas parameter arrays cannot.</span></span>  
  
 <span data-ttu-id="b6b35-106">테이블 반환 매개 변수 및 ODBC에 대 한 자세한 내용은 [odbc&#41;&#40;테이블 반환 매개 변수 ](../../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b6b35-106">For information about table-valued parameters and ODBC, see [Table-Valued Parameters &#40;ODBC&#41;](../../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
 <span data-ttu-id="b6b35-107">테이블 반환 매개 변수 및 OLE DB에 대한 자세한 내용은 [테이블 반환 매개 변수&#40;OLE DB&#41;](../../native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b6b35-107">For information about table-valued parameters and OLE DB, see [Table-Valued Parameters &#40;OLE DB&#41;](../../native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6b35-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b6b35-108">See Also</span></span>  
 [<span data-ttu-id="b6b35-109">SQL Server Native Client 기능</span><span class="sxs-lookup"><span data-stu-id="b6b35-109">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
