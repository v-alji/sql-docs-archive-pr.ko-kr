---
title: IRowsetFastLoad(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- IRowsetFastLoad interface
ms.assetid: d19a7097-48d9-409a-aff9-277891b7aca7
author: rothja
ms.author: jroth
ms.openlocfilehash: 7ecf72f0015d9ed197b3b7a33d4f9bb3246134b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659949"
---
# <a name="irowsetfastload-ole-db"></a><span data-ttu-id="ff280-102">IRowsetFastLoad(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="ff280-102">IRowsetFastLoad (OLE DB)</span></span>
  <span data-ttu-id="ff280-103">`IRowsetFastLoad`인터페이스는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 메모리 기반 대량 복사 작업에 대 한 지원을 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff280-103">The `IRowsetFastLoad` interface exposes support for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory-based bulk-copy operations.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="ff280-104">Native Client OLE DB 공급자 소비자는 인터페이스를 사용 하 여 기존 테이블에 데이터를 빠르게 추가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff280-104">Native Client OLE DB provider consumers use the interface to rapidly add data to an existing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="ff280-105">세션에 대해 SSPROP_ENABLEFASTLOAD를 VARIANT_TRUE로 설정하면 해당 세션에서 반환된 행 집합의 데이터를 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ff280-105">If you set SSPROP_ENABLEFASTLOAD to VARIANT_TRUE for a session, you cannot read data from rowsets subsequently returned from that session.</span></span> <span data-ttu-id="ff280-106">SSPROP_ENABLEFASTLOAD를 VARIANT_TRUE로 설정하면 세션에서 생성되는 모든 행 집합이 IRowsetFastLoad 형식으로 설정되는데,</span><span class="sxs-lookup"><span data-stu-id="ff280-106">When SSPROP_ENABLEFASTLOAD is set to VARIANT_TRUE, all rowsets created on the session will be of type IRowsetFastLoad.</span></span> <span data-ttu-id="ff280-107">IRowsetFastLoad 행 집합은 행 집합 인출 기능을 지원하지 않기 때문에 이러한 행 집합의 데이터는 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ff280-107">IRowsetFastLoad rowsets do not support rowset fetch functionality; therefore, data from these rowsets cannot be read.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ff280-108">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="ff280-108">In This Section</span></span>  
  
|<span data-ttu-id="ff280-109">방법</span><span class="sxs-lookup"><span data-stu-id="ff280-109">Method</span></span>|<span data-ttu-id="ff280-110">Description</span><span class="sxs-lookup"><span data-stu-id="ff280-110">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ff280-111">IRowsetFastLoad::Commit&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="ff280-111">IRowsetFastLoad::Commit &#40;OLE DB&#41;</span></span>](irowsetfastload-commit-ole-db.md)|<span data-ttu-id="ff280-112">일괄 삽입되는 행의 끝을 표시하고 행을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="ff280-112">Marks the end of a batch of inserted rows and writes the rows to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>|  
|[<span data-ttu-id="ff280-113">IRowsetFastLoad::InsertRow&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="ff280-113">IRowsetFastLoad::InsertRow &#40;OLE DB&#41;</span></span>](irowsetfastload-insertrow-ole-db.md)|<span data-ttu-id="ff280-114">대량 복사 행 집합에 행을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ff280-114">Adds a row to the bulk copy rowset.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff280-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ff280-115">See Also</span></span>  
 <span data-ttu-id="ff280-116">[인터페이스 &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="ff280-116">[Interfaces &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md) </span></span>  
 <span data-ttu-id="ff280-117">[IRowsetFastLoad &#40;OLE DB을 사용 하 여 대량 데이터 복사&#41;](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="ff280-117">[Bulk Copy Data Using IRowsetFastLoad &#40;OLE DB&#41;](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) </span></span>  
 [<span data-ttu-id="ff280-118">IROWSETFASTLOAD 및 ISEQUENTIALSTREAM&#40;OLE DB&#41;을 사용하여 BLOB 데이터를 SQL Server로 보내기</span><span class="sxs-lookup"><span data-stu-id="ff280-118">Send BLOB Data to SQL SERVER Using IROWSETFASTLOAD and ISEQUENTIALSTREAM &#40;OLE DB&#41;</span></span>](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)  
  
  
