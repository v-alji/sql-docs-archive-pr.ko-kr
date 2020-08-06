---
title: BLOB 및 OLE 개체 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- BLOBs
- storage object [OLE DB]
- SQL Server Native Client OLE DB provider, BLOBs
- large data, OLE objects
ms.assetid: 767fa2f6-9cd2-436f-add5-e760bed29a58
author: rothja
ms.author: jroth
ms.openlocfilehash: 15f8b4915ba9b05a5be19854a2e27a2e8ff3a346
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741924"
---
# <a name="blobs-and-ole-objects"></a><span data-ttu-id="ea498-102">BLOB 및 OLE 개체</span><span class="sxs-lookup"><span data-stu-id="ea498-102">BLOBs and OLE Objects</span></span>
  <span data-ttu-id="ea498-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ISequentialStream** Native Client OLE DB 공급자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ntext**, **text**, **image**, **varchar (max)**, **nvarchar (max**), **varbinary (max)** 및 xml 데이터 형식에 대 한 소비자 액세스를 blob (binary large object)로 지원 하기 위해 ISequentialStream 인터페이스를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea498-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **ISequentialStream** interface to support consumer access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ntext**, **text**, **image**, **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, and xml data types as binary large objects (BLOBs).</span></span> <span data-ttu-id="ea498-104">**ISequentialStream**에서 **Read** 메서드를 사용하면 소비자가 많은 양의 데이터를 관리하기 쉬운 청크로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea498-104">The **Read** method on **ISequentialStream** lets the consumer retrieve much data in manageable chunks.</span></span>  
  
 <span data-ttu-id="ea498-105">이 기능을 보여주는 샘플을 보려면 [큰 데이터 설정&#40;OLE DB&#41;](../native-client-ole-db-how-to/set-large-data-ole-db.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ea498-105">For a sample demonstrating this feature, see [Set Large Data &#40;OLE DB&#41;](../native-client-ole-db-how-to/set-large-data-ole-db.md).</span></span>  
  
 <span data-ttu-id="ea498-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]소비자가 데이터 수정에 바인딩된 접근자에 인터페이스 포인터를 제공 하는 경우 Native Client OLE DB 공급자는 소비자가 구현한 **IStorage** 인터페이스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea498-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider can use a consumer-implemented **IStorage** interface when the consumer provides the interface pointer in an accessor bound for data modification.</span></span>  
  
 <span data-ttu-id="ea498-107">큰 값 데이터 형식의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 **IROWSET** 및 DDL 인터페이스에서 형식 크기 가정을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea498-107">For large value data types, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider checks for type size assumptions in **IRowset** and DDL interfaces.</span></span> <span data-ttu-id="ea498-108">최대 크기가 무제한으로 설정 된 **varchar**, **nvarchar**및 **varbinary** 데이터 형식의 열은 스키마 행 집합 및 열 데이터 형식을 반환 하는 인터페이스를 통해 islong으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea498-108">Columns with **varchar**, **nvarchar**, and **varbinary** data types with max size set to unlimited will be represented as ISLONG through the schema rowsets and interfaces returning column data types.</span></span>  
  
 <span data-ttu-id="ea498-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 varchar ( **max)**, **varbinary (max)** 및 **nvarchar (max)** 형식을 각각 DBTYPE_STR, DBTYPE_BYTES 및 DBTYPE_WSTR으로 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea498-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **varchar(max)**, **varbinary(max)** and **nvarchar(max)** types as DBTYPE_STR, DBTYPE_BYTES and DBTYPE_WSTR respectively.</span></span>  
  
 <span data-ttu-id="ea498-110">애플리케이션에서 이러한 형식을 사용하기 위해 처리하는 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ea498-110">To work with these types an application has the following options:</span></span>  
  
-   <span data-ttu-id="ea498-111">DBTYPE_STR, DBTYPE_BYTES, DBTYPE_WSTR 형식으로 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="ea498-111">Bind as the type (DBTYPE_STR, DBTYPE_BYTES, DBTYPE_WSTR).</span></span> <span data-ttu-id="ea498-112">버퍼 크기가 충분하지 않으면 이전 릴리스에서 이러한 형식을 처리할 때와 마찬가지로 잘림이 발생합니다(새로운 버전에서는 더 큰 값을 사용할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="ea498-112">If the buffer is not big enough truncation will occur, exactly as for these types in previous releases (although larger values are now available).</span></span>  
  
-   <span data-ttu-id="ea498-113">형식으로 바인딩하고 DBTYPE_BYREF도 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea498-113">Bind as the type and also specify DBTYPE_BYREF.</span></span>  
  
-   <span data-ttu-id="ea498-114">DBTYPE_IUNKNOWN으로 바인딩하고 스트리밍을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ea498-114">Bind as DBTYPE_IUNKNOWN and use streaming.</span></span>  
  
 <span data-ttu-id="ea498-115">DBTYPE_IUNKNOWN으로 바인딩하면 ISequentialStream 스트림 기능이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea498-115">If bound to DBTYPE_IUNKNOWN, ISequentialStream stream functionality is used.</span></span> <span data-ttu-id="ea498-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native client OLE DB 공급자는 출력 매개 변수를 대량 값 데이터 형식에 대 한 DBTYPE_IUNKNOWN로 바인딩하는 데 사용할 수 있습니다 .이 경우 저장 프로시저는 이러한 데이터 형식을 클라이언트에 DBTYPE_IUNKNOWN으로 노출 되는 반환 값으로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea498-116">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports binding output parameters as DBTYPE_IUNKNOWN for large value data types to facilitate scenarios where a stored procedure returns these data types as return values which will be exposed as DBTYPE_IUNKNOWN to the client.</span></span>  
  
## <a name="storage-object-limitations"></a><span data-ttu-id="ea498-117">스토리지 개체 제한 사항</span><span class="sxs-lookup"><span data-stu-id="ea498-117">Storage Object Limitations</span></span>  
  
-   <span data-ttu-id="ea498-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 열려 있는 단일 저장소 개체만 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea498-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider can support only a single open storage object.</span></span> <span data-ttu-id="ea498-119">스토리지 개체를 하나를 초과해 열려고 하면, 즉 하나를 초과하는 **ISequentialStream** 인터페이스 포인터에 대한 참조를 얻으려고 하면 DBSTATUS_E_CANTCREATE가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea498-119">Attempts to open more than one storage object (to get a reference on more than one **ISequentialStream** interface pointer) return DBSTATUS_E_CANTCREATE.</span></span>  
  
-   <span data-ttu-id="ea498-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자에서 DBPROP_BLOCKINGSTORAGEOBJECTS 읽기 전용 속성의 기본값은 VARIANT_TRUE입니다.</span><span class="sxs-lookup"><span data-stu-id="ea498-120">In the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, the default value of the DBPROP_BLOCKINGSTORAGEOBJECTS read-only property is VARIANT_TRUE.</span></span> <span data-ttu-id="ea498-121">이는 스토리지 개체가 활성화되면 스토리지 개체에 있는 메서드를 제외한 일부 메서드가 E_UNEXPECTED 오류와 함께 실패한다는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="ea498-121">This indicates that if a storage object is active, some methods (other than those on the storage objects) will fail with E_UNEXPECTED.</span></span>  
  
-   <span data-ttu-id="ea498-122">소비자가 구현한 저장소 개체에서 제공 하는 데이터의 길이는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 저장소 개체를 참조 하는 행 접근자가 만들어질 때 Native Client OLE DB 공급자에 게 알려 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea498-122">The length of data presented by a consumer-implemented storage object must be made known to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider when the row accessor that references the storage object is created.</span></span> <span data-ttu-id="ea498-123">소비자는 접근자 생성에 사용되는 DBBINDING 구조에 길이 표시자를 바인딩해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea498-123">The consumer must bind a length indicator in the DBBINDING structure used for accessor creation.</span></span>  
  
-   <span data-ttu-id="ea498-124">한 행에 두 개 이상의 대량 데이터 값이 포함 되어 DBPROP_ACCESSORDER DBPROPVAL_AO_RANDOM 되지 않은 경우 소비자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자 커서 지원 행 집합을 사용 하 여 행 데이터를 검색 하거나 다른 행 값을 검색 하기 전에 모든 대량 데이터 값을 처리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea498-124">If a row contains more than a single large data value and DBPROP_ACCESSORDER is not DBPROPVAL_AO_RANDOM, the consumer must either use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider cursor-supported rowset to retrieve row data or process all large data values before retrieving other row values.</span></span> <span data-ttu-id="ea498-125">DBPROP_ACCESSORDER DBPROPVAL_AO_RANDOM 되는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 모든 xml 데이터 형식을 blob (binary large object)로 캐시 하 여 순서에 관계 없이 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea498-125">If DBPROP_ACCESSORDER is DBPROPVAL_AO_RANDOM, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider caches all the xml data types as binary large objects (BLOBs) so that it can be accessed in any order.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ea498-126">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="ea498-126">In This Section</span></span>  
  
-   [<span data-ttu-id="ea498-127">대규모 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="ea498-127">Getting Large Data</span></span>](getting-large-data.md)  
  
-   [<span data-ttu-id="ea498-128">대규모 데이터 설정</span><span class="sxs-lookup"><span data-stu-id="ea498-128">Setting Large Data</span></span>](setting-large-data.md)  
  
-   [<span data-ttu-id="ea498-129">BLOB 출력 매개 변수에 대한 스트리밍 지원</span><span class="sxs-lookup"><span data-stu-id="ea498-129">Streaming Support for BLOB Output Parameters</span></span>](streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a><span data-ttu-id="ea498-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ea498-130">See Also</span></span>  
 <span data-ttu-id="ea498-131">[SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="ea498-131">[SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md) </span></span>  
 [<span data-ttu-id="ea498-132">큰 값 형식 사용</span><span class="sxs-lookup"><span data-stu-id="ea498-132">Using Large Value Types</span></span>](../native-client/features/using-large-value-types.md)  
  
  
