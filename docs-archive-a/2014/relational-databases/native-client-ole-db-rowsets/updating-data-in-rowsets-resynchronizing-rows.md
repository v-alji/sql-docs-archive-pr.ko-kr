---
title: 행 다시 동기화 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- synchronization [OLE DB]
- IRowsetResynch interface
- resynchronizing rows
- data updates [SQL Server], OLE DB
ms.assetid: d2d30505-a878-4aa9-b821-53d8118a45a5
author: rothja
ms.author: jroth
ms.openlocfilehash: 47c628ae583f3e635f422d5146f64508372a1114
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648369"
---
# <a name="resynchronizing-rows"></a><span data-ttu-id="9ea42-102">행 다시 동기화</span><span class="sxs-lookup"><span data-stu-id="9ea42-102">Resynchronizing Rows</span></span>
  <span data-ttu-id="9ea42-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 **IRowsetResynch** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 커서 지원 행 집합에 대해서만 IRowsetResynch을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ea42-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports **IRowsetResynch** on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursor-supported rowsets only.</span></span> <span data-ttu-id="9ea42-104">**IRowsetResynch**는 요청 시 사용할 수 없으며</span><span class="sxs-lookup"><span data-stu-id="9ea42-104">**IRowsetResynch** is not available on demand.</span></span> <span data-ttu-id="9ea42-105">소비자가 행 집합을 열기 전에 이 인터페이스를 요청해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ea42-105">The consumer must request the interface before opening the rowset.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ea42-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9ea42-106">See Also</span></span>  
 [<span data-ttu-id="9ea42-107">행 집합의 데이터 업데이트</span><span class="sxs-lookup"><span data-stu-id="9ea42-107">Updating Data in Rowsets</span></span>](updating-data-in-rowsets.md)  
  
  
