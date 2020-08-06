---
title: OLE DB 테이블 반환 매개 변수 형식 지원 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (OLE DB)
ms.assetid: 147036a0-260e-4f81-8b3b-89209e023a32
author: rothja
ms.author: jroth
ms.openlocfilehash: 48d5fd780b2eaa2fc18e39071d3b10fde897b82c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649020"
---
# <a name="ole-db-table-valued-parameter-type-support"></a><span data-ttu-id="9317d-102">OLE DB 테이블 반환 매개 변수 형식 지원</span><span class="sxs-lookup"><span data-stu-id="9317d-102">OLE DB Table-Valued Parameter Type Support</span></span>
  <span data-ttu-id="9317d-103">이 항목에서는 테이블 반환 매개 변수에 대한 OLE DB 형식 지원에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-103">This topic describes OLE DB type support for table-value parameters.</span></span>  
  
## <a name="table-valued-parameter-rowset-object"></a><span data-ttu-id="9317d-104">테이블 반환 매개 변수 행 집합 개체</span><span class="sxs-lookup"><span data-stu-id="9317d-104">Table-Valued Parameter Rowset Object</span></span>  
 <span data-ttu-id="9317d-105">테이블 반환 매개 변수에 대한 특수한 행 집합 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-105">You can create a specialized rowset object for table-valued parameters.</span></span> <span data-ttu-id="9317d-106">ITableDefinitionWithConstraints::CreateTableWithConstraints 또는 IOpenRowset::OpenRowset을 사용하여 테이블 반환 매개 변수 행 집합 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-106">You create the table-valued parameter rowset object by using ITableDefinitionWithConstraints::CreateTableWithConstraints or IOpenRowset::OpenRowset.</span></span> <span data-ttu-id="9317d-107">이렇게 하려면 *pTableID* 매개 변수의 *eKind* 멤버를 DBKIND_GUID_NAME으로 설정하고 CLSID_ROWSET_INMEMORY를 *guid* 멤버로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-107">To do this, set the *eKind* member of the *pTableID* parameter to DBKIND_GUID_NAME, and provide the CLSID_ROWSET_INMEMORY as the *guid* member.</span></span> <span data-ttu-id="9317d-108">테이블 반환 매개 변수의 서버 유형 이름은 IOpenRowset::OpenRowset을 사용할 때 *pTableID*의 *pwszName* 멤버에 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-108">The server type name for the table-valued parameter must be specified in the *pwszName* member of *pTableID* when using IOpenRowset::OpenRowset.</span></span> <span data-ttu-id="9317d-109">테이블 반환 매개 변수 행 집합 개체는 일반 SQL Server Native Client OLE DB 공급자 개체처럼 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-109">The table-valued parameter rowset object behaves like a regular SQL Server Native Client OLE DB Provider object.</span></span>  
  
```  
const GUID CLSID_ROWSET_TVP =   
{0xc7ef28d5, 0x7bee, 0x443f, {0x86, 0xda, 0xe3, 0x98, 0x4f, 0xcd, 0x4d, 0xf9}};  
  
CoType RowsetTVP  
{  
[mandatory] interface IAccessor;  
[mandatory] interface IColumnsInfo;  
[mandatory] interface IConvertType;  
[mandatory] interface IRowset;  
[mandatory] interface IRowsetInfo;  
[optional]  interface IColumnsRowset;  
[optional]  interface IRowsetChange;  
[optional]  interface ISupportErrorInfo;  
};  
```  
  
## <a name="dbtype_table"></a><span data-ttu-id="9317d-110">DBTYPE_TABLE</span><span class="sxs-lookup"><span data-stu-id="9317d-110">DBTYPE_TABLE</span></span>  
 <span data-ttu-id="9317d-111">새 형식 DBTYPE_TABLE은 테이블 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-111">A new type, DBTYPE_TABLE, represents a table type.</span></span> <span data-ttu-id="9317d-112">이 형식은 DBTYPE이 필요한 여러 OLE DB 인터페이스에서 테이블 반환 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-112">This type specifies table-valued parameters in various OLE DB interfaces where a DBTYPE is required.</span></span>  
  
```  
#define DBTYPE_TABLE (143)  
```  
  
 <span data-ttu-id="9317d-113">DBTYPE_TABLE은 DBTYPE_IUNKNOWN과 형식이 동일하며</span><span class="sxs-lookup"><span data-stu-id="9317d-113">DBTYPE_TABLE has the same format as DBTYPE_IUNKNOWN.</span></span> <span data-ttu-id="9317d-114">데이터 버퍼의 개체에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-114">It is a pointer to an object in the data buffer.</span></span> <span data-ttu-id="9317d-115">전체 바인딩 지정을 위해 소비자는 DBOBJECT 버퍼를 채우고 *iid*를 행 집합 개체 인터페이스 중 하나(IID_IRowset)로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-115">For complete specification in the bindings, the consumer fills up the DBOBJECT buffer, with *iid* set to one of the rowset object interfaces (IID_IRowset).</span></span> <span data-ttu-id="9317d-116">바인딩에 DBOBJECT를 지정하지 않으면 IID_IRowset으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-116">If no DBOBJECT is specified in the bindings, IID_IRowset will be assumed.</span></span>  
  
 <span data-ttu-id="9317d-117">DBTYPE_TABLE과 다른 형식 간의 변환은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-117">Conversions to and from DBTYPE_TABLE for any other types are not supported.</span></span> <span data-ttu-id="9317d-118">DBTYPE_TABLE에서 DBTYPE_TABLE로의 변환이 아닌 지원되지 않는 변환을 요청하면 IConvertType::CanConvert에서 S_FALSE를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-118">IConvertType::CanConvert will return S_FALSE for unsupported conversion for any request other than DBTYPE_TABLE to DBTYPE_TABLE conversion.</span></span> <span data-ttu-id="9317d-119">이는 명령 개체의 DBCONVERTFLAGS_PARAMETER로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-119">This assumes DBCONVERTFLAGS_PARAMETER on the Command object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9317d-120">메서드</span><span class="sxs-lookup"><span data-stu-id="9317d-120">Methods</span></span>  
 <span data-ttu-id="9317d-121">테이블 반환 매개 변수를 지원하는 OLE DB 메서드에 관한 자세한 내용은 [OLE DB 테이블 반환 매개 변수 형식 지원&#40;메서드&#41;](ole-db-table-valued-parameter-type-support-methods.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9317d-121">For information about OLE DB methods that support table-valued parameters, see [OLE DB Table-Valued Parameter Type Support &#40;Methods&#41;](ole-db-table-valued-parameter-type-support-methods.md).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9317d-122">속성</span><span class="sxs-lookup"><span data-stu-id="9317d-122">Properties</span></span>  
 <span data-ttu-id="9317d-123">테이블 반환 매개 변수를 지원하는 OLE DB 속성에 관한 자세한 내용은 [OLE DB 테이블 반환 매개 변수 형식 지원&#40;속성&#41;](ole-db-table-valued-parameter-type-support-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9317d-123">For information about OLE DB properties that support table-valued parameters, see [OLE DB Table-Valued Parameter Type Support &#40;Properties&#41;](ole-db-table-valued-parameter-type-support-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9317d-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9317d-124">See Also</span></span>  
 <span data-ttu-id="9317d-125">[테이블 반환 매개 변수 OLE DB &#40;&#41;](table-valued-parameters-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="9317d-125">[Table-Valued Parameters &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span></span>  
 [<span data-ttu-id="9317d-126">테이블 반환 매개 변수&#40;OLE DB&#41; 사용</span><span class="sxs-lookup"><span data-stu-id="9317d-126">Use Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
