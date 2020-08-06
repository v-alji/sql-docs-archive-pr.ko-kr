---
title: IRowsetFastLoad::Commit(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IRowsetFastLoad::Commit (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Commit method
ms.assetid: 19de9128-b91a-4626-847f-af721edaa24e
author: rothja
ms.author: jroth
ms.openlocfilehash: cfdf355919f65fd2cedacd09249e2aae59321390
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659954"
---
# <a name="irowsetfastloadcommit-ole-db"></a><span data-ttu-id="d4d8b-102">IRowsetFastLoad::Commit(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="d4d8b-102">IRowsetFastLoad::Commit (OLE DB)</span></span>
  <span data-ttu-id="d4d8b-103">일괄 삽입되는 행의 끝을 표시하고 행을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="d4d8b-103">Marks the end of a batch of inserted rows and writes the rows to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="d4d8b-104">샘플은 [IRowsetFastLoad를 사용한 데이터 대량 복사&#40;OLE DB&#41;](irowsetfastload-ole-db.md) 및 [IROWSETFASTLOAD와 ISEQUENTIALSTREAM을 사용하여 SQL SERVER로 BLOB 데이터 전송&#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d4d8b-104">For samples, see [Bulk Copy Data Using IRowsetFastLoad &#40;OLE DB&#41;](irowsetfastload-ole-db.md) and [Send BLOB Data to SQL SERVER Using IROWSETFASTLOAD and ISEQUENTIALSTREAM &#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4d8b-105">구문</span><span class="sxs-lookup"><span data-stu-id="d4d8b-105">Syntax</span></span>  
  
```  
  
HRESULT Commit(  
BOOL   
fDone  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="d4d8b-106">인수</span><span class="sxs-lookup"><span data-stu-id="d4d8b-106">Arguments</span></span>  
 <span data-ttu-id="d4d8b-107">*fDone*[in]</span><span class="sxs-lookup"><span data-stu-id="d4d8b-107">*fDone*[in]</span></span>  
 <span data-ttu-id="d4d8b-108">FALSE인 경우 행 집합은 계속 유효하며 소비자가 행을 추가로 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4d8b-108">If FALSE, the rowset maintains validity and can be used by the consumer for additional row insertion.</span></span> <span data-ttu-id="d4d8b-109">TRUE인 경우 행 집합은 유효하지 않게 되며 소비자가 행을 추가로 삽입할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d4d8b-109">If TRUE, the rowset loses validity and no further insertion can be done by the consumer.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="d4d8b-110">반환 코드 값</span><span class="sxs-lookup"><span data-stu-id="d4d8b-110">Return Code Values</span></span>  
 <span data-ttu-id="d4d8b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d4d8b-111">S_OK</span></span>  
 <span data-ttu-id="d4d8b-112">메서드가 성공했으며 삽입한 모든 데이터가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에 기록되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d4d8b-112">The method succeeded and all inserted data has been written to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="d4d8b-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d4d8b-113">E_FAIL</span></span>  
 <span data-ttu-id="d4d8b-114">공급자 관련 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="d4d8b-114">A provider-specific error occurred.</span></span> <span data-ttu-id="d4d8b-115">오류 정보에서 공급자 관련 오류 텍스트를 검색하십시오.</span><span class="sxs-lookup"><span data-stu-id="d4d8b-115">Retrieve error information for the specific error text from the provider.</span></span>  
  
 <span data-ttu-id="d4d8b-116">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="d4d8b-116">E_UNEXPECTED</span></span>  
 <span data-ttu-id="d4d8b-117">이전에 **IRowsetFastLoad::Commit** 메서드에 의해 무효화된 대량 복사 행 집합에서 메서드가 호출되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d4d8b-117">The method was called on a bulk copy rowset previously invalidated by the **IRowsetFastLoad::Commit** method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4d8b-118">설명</span><span class="sxs-lookup"><span data-stu-id="d4d8b-118">Remarks</span></span>  
 <span data-ttu-id="d4d8b-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자 대량 복사 행 집합은 지연 업데이트 모드 행 집합으로 동작 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d8b-119">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider bulk copy rowset behaves as a delayed-update mode rowset.</span></span> <span data-ttu-id="d4d8b-120">사용자가 행 집합을 통해 행 데이터를 삽입하면 삽입된 행은 **IRowsetUpdate**를 지원하는 행 집합에서 보류 중인 삽입과 같은 방법으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4d8b-120">As the user inserts row data through the rowset, inserted rows are treated in the same fashion as pending inserts on a rowset supporting **IRowsetUpdate**.</span></span>  
  
 <span data-ttu-id="d4d8b-121">**IRowsetUpdate::Update** 메서드를 사용하여 보류 중인 행을 SQL Server 인스턴스로 전송하는 것과 같은 방법으로 소비자는 대량 복사 행 집합에 대해 **Commit** 메서드를 호출하여 삽입된 행을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에 써야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d8b-121">The consumer must call the **Commit** method on the bulk copy rowset to write inserted rows to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table in the same way as the **IRowsetUpdate::Update** method is used to submit pending rows to an instance of SQL Server.</span></span>  
  
 <span data-ttu-id="d4d8b-122">소비자가 **Commit** 메서드를 호출하지 않고 대량 복사 행 집합에 대한 참조를 해제하면 기존에 쓰지 않은 삽입된 행이 모두 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4d8b-122">If the consumer releases its reference on the bulk copy rowset without calling the **Commit** method, all inserted rows not previously written are lost.</span></span>  
  
 <span data-ttu-id="d4d8b-123">소비자는 *fDone* 인수를 FALSE로 설정하고 **Commit** 메서드를 호출하여 삽입된 행을 일괄 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4d8b-123">The consumer can batch inserted rows by calling the **Commit** method with the *fDone* argument set to FALSE.</span></span> <span data-ttu-id="d4d8b-124">*fDone*을 TRUE로 설정하면 행 집합이 무효화됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4d8b-124">When *fDone*is set to TRUE, the rowset becomes invalid.</span></span> <span data-ttu-id="d4d8b-125">무효화된 대량 복사 행 집합에는 **ISupportErrorInfo** 인터페이스 및 **IRowsetFastLoad::Release** 메서드만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4d8b-125">An invalid bulk copy rowset supports only the **ISupportErrorInfo** interface and **IRowsetFastLoad::Release** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4d8b-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d4d8b-126">See Also</span></span>  
 [<span data-ttu-id="d4d8b-127">IRowsetFastLoad &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="d4d8b-127">IRowsetFastLoad &#40;OLE DB&#41;</span></span>](irowsetfastload-ole-db.md)  
  
  
