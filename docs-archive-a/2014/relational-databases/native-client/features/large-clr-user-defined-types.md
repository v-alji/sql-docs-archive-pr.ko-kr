---
title: 큰 CLR 사용자 정의 형식 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- large CLR user-defined types
ms.assetid: b65eb61d-ccf6-49c0-98e7-9a4ef4b2f790
author: rothja
ms.author: jroth
ms.openlocfilehash: 27f0c13caea8c4aca63d78238509c6d05f1bf7bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730595"
---
# <a name="large-clr-user-defined-types"></a><span data-ttu-id="cce23-102">큰 CLR 사용자 정의 형식</span><span class="sxs-lookup"><span data-stu-id="cce23-102">Large CLR User-Defined Types</span></span>
  <span data-ttu-id="cce23-103">SQL Server 2005에서는 CLR(공용 언어 런타임)에서의 UDT(사용자 정의 형식) 크기가 8,000바이트로 제한되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cce23-103">In SQL Server 2005, user-defined types (UDTs) in the common language runtime (CLR) were restricted to 8,000 bytes in size.</span></span> <span data-ttu-id="cce23-104">[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 이상 버전에서는 이 제한이 더 이상 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cce23-104">This restriction has been lifted in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] and later versions.</span></span> <span data-ttu-id="cce23-105">이제 CLR UDT가 LOB(Large Object) 형식과 비슷하게 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="cce23-105">CLR UDTs are now treated in a similar way to large object (LOB) types.</span></span> <span data-ttu-id="cce23-106">즉, 8,000바이트보다 작거나 같은 UDT는 SQL Server 2005에서와 동일하게 처리되나 이보다 큰 UDT도 지원되며 이 경우 크기가 "제한 없음"으로 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="cce23-106">That is, UDTs less than or equal to 8,000 bytes behave the same way as in SQL Server 2005, but larger UDTs are supported and report their size as "unlimited".</span></span>  
  
 <span data-ttu-id="cce23-107">자세한 내용은 [ODBC&#41;&#40;](../odbc/large-clr-user-defined-types-odbc.md) [&#41;OLE DB &#40;크고](../ole-db/large-clr-user-defined-types-ole-db.md) clr 사용자 정의 형식을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cce23-107">For more information, see [Large CLR User-Defined Types &#40;OLE DB&#41;](../ole-db/large-clr-user-defined-types-ole-db.md) and [Large CLR User-Defined Types &#40;ODBC&#41;](../odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="use-cases"></a><span data-ttu-id="cce23-108">사용 사례</span><span class="sxs-lookup"><span data-stu-id="cce23-108">Use Cases</span></span>  
 <span data-ttu-id="cce23-109">ODBC의 경우 UDT 값을 실행 시 데이터 매개 변수로 조각으로 나누어 보낼 수 있는 기능이 큰 UDT에 대한 지원에 포함되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cce23-109">For ODBC, support for large UDTs includes the ability to send UDT values in pieces as data-at-execution parameters.</span></span> <span data-ttu-id="cce23-110">SQLPutData를 사용 하 여이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="cce23-110">This is done by using SQLPutData.</span></span>  
  
 <span data-ttu-id="cce23-111">OLE DB의 경우 ISequentialStream 바인딩을 통해 UDT 값을 서버로 스트리밍하거나 서버에서 스트리밍하는 기능이 큰 UDT에 대한 지원에 포함되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cce23-111">For OLE DB, support for large UDTs includes the ability to stream UDT values to and from the server by using ISequentialStream binding.</span></span>  
  
 <span data-ttu-id="cce23-112">8,000바이트보다 작거나 같은 UDT는 SQL Server 2005에서와 동일하게 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="cce23-112">UDTs less than or equal to 8,000 bytes will behave as they did in SQL Server 2005.</span></span> <span data-ttu-id="cce23-113">OLE DB의 경우 작은 UDT는 ISequentialStream 바인딩을 사용하여 이전처럼 스트리밍할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cce23-113">For OLE DB, you can still stream small UDTs by using ISequentialStream binding.</span></span>  
  
 <span data-ttu-id="cce23-114">네이티브 코드가 CLR UDT의 내용을 이해해야 하지만 관리되는 개체를 인스턴스화할 필요는 없는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cce23-114">Sometimes native code will have to understand the contents of CLR UDTs, but will not have to instantiate managed objects.</span></span> <span data-ttu-id="cce23-115">이 경우 사용자 지정 직렬화를 사용하여 서버의 UDT 값을 클라이언트의 잘 알려진 형식으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cce23-115">If this is the case, you can use custom serialization to convert UDT values on the server into a well known format for clients.</span></span>  
  
 <span data-ttu-id="cce23-116">데이터 액세스 코드가 이미 있는 애플리케이션의 경우 네이티브 API를 통해 UDT를 검색한 후 이를 혼합 모드 애플리케이션에서 C++ CLI interop을 사용하여 인스턴스화하는 방법으로 클라이언트에서 CLR UDT 동작을 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cce23-116">For applications that have existing data access code, you can exploit CLR UDT behavior on the client by retrieving UDTs through native APIs and instantiating them by using C++ CLI interop in mixed mode applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cce23-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cce23-117">See Also</span></span>  
 [<span data-ttu-id="cce23-118">SQL Server Native Client 기능</span><span class="sxs-lookup"><span data-stu-id="cce23-118">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
