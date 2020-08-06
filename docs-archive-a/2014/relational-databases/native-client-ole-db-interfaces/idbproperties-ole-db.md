---
title: IDBProperties(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 2e5a4fd8-5164-495a-9986-3477aef8d8a5
author: rothja
ms.author: jroth
ms.openlocfilehash: f42ab47de2471fc413e4c6acf0d6c61cb2b6d77c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659953"
---
# <a name="idbproperties-ole-db"></a><span data-ttu-id="1e601-102">IDBProperties(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="1e601-102">IDBProperties (OLE DB)</span></span>
  <span data-ttu-id="1e601-103">OLE DB 표준 사양을 통해 공급자가 `DBPROPINFO::vValues`에 대해 VT_EMPTY를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e601-103">The OLE DB standard specification allows providers to specify VT_EMPTY for `DBPROPINFO::vValues`.</span></span> <span data-ttu-id="1e601-104">그러나를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 호출 하 여 `IDBProperties::GetPropertyInfo` `DBPROPSET_ROWSETALL` 행 집합 속성을 검색 하는 경우 Native Client OLE DB는 항상 VT_EMPTY를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e601-104">However, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB always returns VT_EMPTY when you call `IDBProperties::GetPropertyInfo` with `DBPROPSET_ROWSETALL` to retrieve rowset properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e601-105">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1e601-105">See Also</span></span>  
 [<span data-ttu-id="1e601-106">인터페이스&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="1e601-106">Interfaces &#40;OLE DB&#41;</span></span>](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
