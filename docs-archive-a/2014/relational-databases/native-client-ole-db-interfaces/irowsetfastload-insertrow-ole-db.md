---
title: IRowsetFastLoad::InsertRow(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IRowsetFastLoad::InsertRow (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- InsertRow method
ms.assetid: 594d3461-34d2-41e7-8ad4-bd2753601ab6
author: rothja
ms.author: jroth
ms.openlocfilehash: 4e9ea952f27574270ee333919f778814ff3de462
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659950"
---
# <a name="irowsetfastloadinsertrow-ole-db"></a><span data-ttu-id="328d4-102">IRowsetFastLoad::InsertRow(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="328d4-102">IRowsetFastLoad::InsertRow (OLE DB)</span></span>
  <span data-ttu-id="328d4-103">대량 복사 행 집합에 행을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="328d4-103">Adds a row to the bulk copy rowset.</span></span> <span data-ttu-id="328d4-104">샘플은 [IRowsetFastLoad를 사용한 데이터 대량 복사&#40;OLE DB&#41;](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) 및 [IROWSETFASTLOAD와 ISEQUENTIALSTREAM을 사용하여 SQL SERVER로 BLOB 데이터 전송&#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="328d4-104">For samples, see [Bulk Copy Data Using IRowsetFastLoad &#40;OLE DB&#41;](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) and [Send BLOB Data to SQL SERVER Using IROWSETFASTLOAD and ISEQUENTIALSTREAM &#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="328d4-105">구문</span><span class="sxs-lookup"><span data-stu-id="328d4-105">Syntax</span></span>  
  
```  
  
HRESULT InsertRow(  
HACCESSOR  
hAccessor  
,  
void*  
pData  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="328d4-106">인수</span><span class="sxs-lookup"><span data-stu-id="328d4-106">Arguments</span></span>  
 <span data-ttu-id="328d4-107">*hAccessor*[in]</span><span class="sxs-lookup"><span data-stu-id="328d4-107">*hAccessor*[in]</span></span>  
 <span data-ttu-id="328d4-108">대량 복사에 대한 행 데이터를 정의하는 접근자의 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="328d4-108">The handle of the accessor defining the row data for bulk copy.</span></span> <span data-ttu-id="328d4-109">참조되는 접근자는 행 접근자로, 데이터 값이 포함된 소비자가 소유한 메모리를 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="328d4-109">The accessor referenced is a row accessor, binding consumer-owned memory containing data values.</span></span>  
  
 <span data-ttu-id="328d4-110">*pData*[in]</span><span class="sxs-lookup"><span data-stu-id="328d4-110">*pData*[in]</span></span>  
 <span data-ttu-id="328d4-111">데이터 값이 포함된 소비자가 소유한 메모리에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="328d4-111">A pointer to the consumer-owned memory containing data values.</span></span> <span data-ttu-id="328d4-112">자세한 내용은 [DBBINDING 구조](https://go.microsoft.com/fwlink/?LinkId=65955)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="328d4-112">For more information, see [DBBINDING Structures](https://go.microsoft.com/fwlink/?LinkId=65955).</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="328d4-113">반환 코드 값</span><span class="sxs-lookup"><span data-stu-id="328d4-113">Return Code Values</span></span>  
 <span data-ttu-id="328d4-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="328d4-114">S_OK</span></span>  
 <span data-ttu-id="328d4-115">메서드가 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="328d4-115">The method succeeded.</span></span> <span data-ttu-id="328d4-116">모든 열의 바인딩된 상태 값은 DBSTATUS_S_OK 또는 DBSTATUS_S_NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="328d4-116">Any bound status values for all columns have value DBSTATUS_S_OK or DBSTATUS_S_NULL.</span></span>  
  
 <span data-ttu-id="328d4-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="328d4-117">E_FAIL</span></span>  
 <span data-ttu-id="328d4-118">오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="328d4-118">An error occurred.</span></span> <span data-ttu-id="328d4-119">행 집합의 오류 인터페이스에서 오류 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="328d4-119">Error information is available from the rowset's error interfaces.</span></span>  
  
 <span data-ttu-id="328d4-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="328d4-120">E_INVALIDARG</span></span>  
 <span data-ttu-id="328d4-121">*pData* 인수가 NULL 포인터로 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="328d4-121">The *pData* argument was set to a NULL pointer.</span></span>  
  
 <span data-ttu-id="328d4-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="328d4-122">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="328d4-123">SQLNCLI11에서 요청을 완료하기에 충분한 메모리를 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="328d4-123">SQLNCLI11 was unable to allocate sufficient memory to complete the request.</span></span>  
  
 <span data-ttu-id="328d4-124">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="328d4-124">E_UNEXPECTED</span></span>  
 <span data-ttu-id="328d4-125">이전에 [IRowsetFastLoad::Commit](irowsetfastload-commit-ole-db.md) 메서드에 의해 무효화된 대량 복사 행 집합에서 메서드가 호출되었습니다.</span><span class="sxs-lookup"><span data-stu-id="328d4-125">The method was called on a bulk copy rowset previously invalidated by the [IRowsetFastLoad::Commit](irowsetfastload-commit-ole-db.md) method.</span></span>  
  
 <span data-ttu-id="328d4-126">DB_E_BADACCESSORHANDLE</span><span class="sxs-lookup"><span data-stu-id="328d4-126">DB_E_BADACCESSORHANDLE</span></span>  
 <span data-ttu-id="328d4-127">소비자가 제공한 *hAccessor* 인수가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="328d4-127">The *hAccessor* argument provided by the consumer was invalid.</span></span>  
  
 <span data-ttu-id="328d4-128">DB_E_BADACCESSORTYPE</span><span class="sxs-lookup"><span data-stu-id="328d4-128">DB_E_BADACCESSORTYPE</span></span>  
 <span data-ttu-id="328d4-129">지정된 접근자는 행 접근자가 아니거나, 소비자가 소유한 메모리를 지정하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="328d4-129">The specified accessor was not a row accessor or did not specify consumer-owned memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="328d4-130">설명</span><span class="sxs-lookup"><span data-stu-id="328d4-130">Remarks</span></span>  
 <span data-ttu-id="328d4-131">소비자 데이터를 열 데이터 형식으로 변환 하는 동안 오류가 발생 하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자에서 E_FAIL 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="328d4-131">An error converting consumer data to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type for a column causes an E_FAIL return from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span> <span data-ttu-id="328d4-132">모든 **InsertRow** 메서드나 **Commit** 메서드에서만 데이터를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="328d4-132">Data can be transmitted to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on any **InsertRow** method or only on **Commit** method.</span></span> <span data-ttu-id="328d4-133">소비자 애플리케이션은 데이터 형식 변환 오류가 있다는 알림을 받기 전에 오류가 있는 데이터로 **InsertRow** 메서드를 여러 번 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="328d4-133">The consumer application can call the **InsertRow** method many times with erroneous data before it receives notice that a data type conversion error exists.</span></span> <span data-ttu-id="328d4-134">**Commit** 메서드에서 소비자가 모든 데이터를 올바르게 지정했는지 확인하기 때문에 소비자는 필요에 따라 **Commit** 메서드를 적절하게 사용하여 데이터의 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="328d4-134">Because the **Commit** method ensures that all data is correctly specified by the consumer, the consumer can use the **Commit** method appropriately to validate data as necessary.</span></span>  
  
 <span data-ttu-id="328d4-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자 대량 복사 행 집합은 쓰기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="328d4-135">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider bulk copy rowsets are write-only.</span></span> <span data-ttu-id="328d4-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 행 집합의 소비자 쿼리를 허용 하는 메서드를 노출 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="328d4-136">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes no methods allowing consumer query of the rowset.</span></span> <span data-ttu-id="328d4-137">처리를 종료하기 위해 소비자는 **Commit** 메서드를 호출하지 않고 [IRowsetFastLoad](irowsetfastload-ole-db.md) 인터페이스에서 해당 참조를 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="328d4-137">To terminate processing, the consumer can release its reference on the [IRowsetFastLoad](irowsetfastload-ole-db.md) interface without calling the **Commit** method.</span></span> <span data-ttu-id="328d4-138">행 집합에 있는 소비자가 삽입한 행에 액세스하여 해당 값을 변경하거나 행 집합에서 개별적으로 행을 제거하는 기능은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="328d4-138">There are no facilities for accessing a consumer-inserted row in the rowset and changing its values, or removing it individually from the rowset.</span></span>  
  
 <span data-ttu-id="328d4-139">대량 복사된 행은 서버에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 맞게 형식이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="328d4-139">Bulk copied rows are formatted on the server for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="328d4-140">행 형식은 연결이나 세션에 대해 설정된 모든 옵션(예: ANSI_PADDING)의 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="328d4-140">The row format is affected by any options that may have been set for the connection or session such as ANSI_PADDING.</span></span> <span data-ttu-id="328d4-141">이 옵션은 Native Client OLE DB 공급자를 통해 생성 된 모든 연결에 대해 기본적으로 설정 되어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 있습니다.</span><span class="sxs-lookup"><span data-stu-id="328d4-141">This option is set on by default for any connection made through the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="328d4-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="328d4-142">See Also</span></span>  
 [<span data-ttu-id="328d4-143">IRowsetFastLoad &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="328d4-143">IRowsetFastLoad &#40;OLE DB&#41;</span></span>](irowsetfastload-ole-db.md)  
  
  
