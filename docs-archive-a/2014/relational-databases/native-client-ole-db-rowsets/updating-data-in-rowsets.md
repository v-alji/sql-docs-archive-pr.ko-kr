---
title: 행 집합의 데이터 업데이트 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- rowsets [OLE DB], updating data
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, updating data
- SQL Server Native Client OLE DB provider, data updates
- data updates [SQL Server], OLE DB
ms.assetid: 37769b1c-c480-419a-8c54-5cc420bf73db
author: rothja
ms.author: jroth
ms.openlocfilehash: 993cfb67d4e6b72eec7cc0537e9b47371e94af10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734035"
---
# <a name="updating-data-in-rowsets"></a><span data-ttu-id="f4063-102">행 집합의 데이터 업데이트</span><span class="sxs-lookup"><span data-stu-id="f4063-102">Updating Data in Rowsets</span></span>
  <span data-ttu-id="f4063-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 소비자가 해당 데이터를 포함 하는 수정 가능한 행 집합을 업데이트할 때 Native Client OLE DB 공급자는 데이터를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4063-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider updates [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data when a consumer updates a modifiable rowset that contains that data.</span></span> <span data-ttu-id="f4063-104">수정할 수 있는 행 집합은 소비자가 **IRowsetChange** 또는 **IRowsetUpdate** 인터페이스에 대한 지원을 요청할 때 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4063-104">A modifiable rowset is created when the consumer requests support for either the **IRowsetChange** or **IRowsetUpdate** interface.</span></span>  
  
 <span data-ttu-id="f4063-105">모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자가 수정할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 수 있는 행 집합은 커서를 사용 하 여 행 집합을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4063-105">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider-modifiable rowsets use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors to support the rowset.</span></span> <span data-ttu-id="f4063-106">행 집합 속성 DBPROP_LOCKMODE는 커서의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 동시성 제어 동작을 변경하고 업데이트할 수 있는 행 집합의 데이터 무결성 오류 생성과 행 집합 행 인출 동작을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="f4063-106">The rowset property DBPROP_LOCKMODE alters [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] concurrency control behavior in cursors and determines the behavior of rowset row fetching and data integrity error generation in updatable rowsets.</span></span>  
  
 <span data-ttu-id="f4063-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 업데이트 전후에 행 동기화를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4063-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports row synchronization before or after an update.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f4063-108">IRowChange::SetColumns를 사용하여 행 개체에 대한 하나 이상의 명명된 열 값을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4063-108">IRowChange::SetColumns is available to set the values of one or more named columns of a row object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f4063-109">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="f4063-109">In This Section</span></span>  
  
-   [<span data-ttu-id="f4063-110">SQL Server 커서의 데이터 업데이트</span><span class="sxs-lookup"><span data-stu-id="f4063-110">Updating Data in SQL Server Cursors</span></span>](updating-data-in-sql-server-cursors.md)  
  
-   [<span data-ttu-id="f4063-111">행 다시 동기화</span><span class="sxs-lookup"><span data-stu-id="f4063-111">Resynchronizing Rows</span></span>](updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a><span data-ttu-id="f4063-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f4063-112">See Also</span></span>  
 [<span data-ttu-id="f4063-113">행 집합</span><span class="sxs-lookup"><span data-stu-id="f4063-113">Rowsets</span></span>](rowsets.md)  
  
  
