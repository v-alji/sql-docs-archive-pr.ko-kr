---
title: ISSAsynchStatus::Abort(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAsynchStatus::Abort (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Abort method
ms.assetid: 2a4bd312-839a-45a8-a299-fc8609be9a2a
author: rothja
ms.author: jroth
ms.openlocfilehash: 0fb352b6541240126dcd4c60521b93d57d6839f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734051"
---
# <a name="issasynchstatusabort-ole-db"></a><span data-ttu-id="24f4e-102">ISSAsynchStatus::Abort(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="24f4e-102">ISSAsynchStatus::Abort (OLE DB)</span></span>
  <span data-ttu-id="24f4e-103">비동기적으로 실행 중인 작업을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="24f4e-103">Cancels an asynchronously executing operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24f4e-104">구문</span><span class="sxs-lookup"><span data-stu-id="24f4e-104">Syntax</span></span>  
  
```  
  
HRESULT Abort(  
  HCHAPTER hChapter,  
  DBASYNCHOP eOperation);  
```  
  
## <a name="arguments"></a><span data-ttu-id="24f4e-105">인수</span><span class="sxs-lookup"><span data-stu-id="24f4e-105">Arguments</span></span>  
 <span data-ttu-id="24f4e-106">*hChapter*[in]</span><span class="sxs-lookup"><span data-stu-id="24f4e-106">*hChapter*[in]</span></span>  
 <span data-ttu-id="24f4e-107">작업을 중단할 장의 처리기입니다.</span><span class="sxs-lookup"><span data-stu-id="24f4e-107">The handle of the chapter for which to abort the operation.</span></span> <span data-ttu-id="24f4e-108">호출되는 개체가 행 집합 개체가 아니거나 작업이 장에 적용되지 않는 경우 호출자가 *hChapter* 를 DB_NULL_HCHAPTER로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24f4e-108">If the object being called is not a rowset object or the operation does not apply to a chapter, the caller must set *hChapter* to DB_NULL_HCHAPTER.</span></span>  
  
 <span data-ttu-id="24f4e-109">*eOperation*[in]</span><span class="sxs-lookup"><span data-stu-id="24f4e-109">*eOperation*[in]</span></span>  
 <span data-ttu-id="24f4e-110">중단할 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="24f4e-110">The operation to abort.</span></span> <span data-ttu-id="24f4e-111">값은 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24f4e-111">This should be the following value:</span></span>  
  
 <span data-ttu-id="24f4e-112">DBASYNCHOP_OPEN - 취소 요청이 행 세트의 비동기 열기 또는 채우기나 데이터 원본 개체의 비동기 초기화에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="24f4e-112">DBASYNCHOP_OPEN-The request to cancel applies to the asynchronous opening or population of a rowset or to the asynchronous initialization of a data source object.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="24f4e-113">반환 코드 값</span><span class="sxs-lookup"><span data-stu-id="24f4e-113">Return Code Values</span></span>  
 <span data-ttu-id="24f4e-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="24f4e-114">S_OK</span></span>  
 <span data-ttu-id="24f4e-115">비동기 작업 취소 요청이 처리되었습니다.</span><span class="sxs-lookup"><span data-stu-id="24f4e-115">The request to cancel the asynchronous operation was processed.</span></span> <span data-ttu-id="24f4e-116">작업 자체가 취소된 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="24f4e-116">This does not guarantee that the operation itself was canceled.</span></span> <span data-ttu-id="24f4e-117">작업이 취소되었는지 확인하려면 소비자가 [ISSAsynchStatus::GetStatus](issasynchstatus-getstatus-ole-db.md) 를 호출하고 DB_E_CANCELED를 확인해야 합니다. 하지만 바로 다음 호출에서 이 값이 반환되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24f4e-117">To determine whether the operation was canceled, the consumer should call [ISSAsynchStatus::GetStatus](issasynchstatus-getstatus-ole-db.md) and check for DB_E_CANCELED; however, it might not be returned in the very next call.</span></span>  
  
 <span data-ttu-id="24f4e-118">DB_E_CANTCANCEL</span><span class="sxs-lookup"><span data-stu-id="24f4e-118">DB_E_CANTCANCEL</span></span>  
 <span data-ttu-id="24f4e-119">비동기 작업을 취소할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="24f4e-119">The asynchronous operation cannot be canceled.</span></span>  
  
 <span data-ttu-id="24f4e-120">DB_E_CANCELED</span><span class="sxs-lookup"><span data-stu-id="24f4e-120">DB_E_CANCELED</span></span>  
 <span data-ttu-id="24f4e-121">알림 중에 비동기 작업 중단 요청이 취소되었습니다.</span><span class="sxs-lookup"><span data-stu-id="24f4e-121">The request to abort the asynchronous operation was canceled during notifications.</span></span> <span data-ttu-id="24f4e-122">작업이 여전히 비동기적으로 실행되고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24f4e-122">The operation is still being executed asynchronously.</span></span>  
  
 <span data-ttu-id="24f4e-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="24f4e-123">E_FAIL</span></span>  
 <span data-ttu-id="24f4e-124">공급자 관련 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="24f4e-124">A provider-specific error occurred.</span></span>  
  
 <span data-ttu-id="24f4e-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="24f4e-125">E_INVALIDARG</span></span>  
 <span data-ttu-id="24f4e-126">*hChapter* 매개 변수가 DB_NULL_HCHAPTER가 아니거나 *eOperation* 이 DBASYNCH_OPEN이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="24f4e-126">The *hChapter* parameter is not DB_NULL_HCHAPTER or *eOperation* is not DBASYNCH_OPEN.</span></span>  
  
 <span data-ttu-id="24f4e-127">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="24f4e-127">E_UNEXPECTED</span></span>  
 <span data-ttu-id="24f4e-128">**IDBInitialize::Initialize** 가 취소되지 않은 데이터 원본 개체에서 **ISSAsynchStatus::Abort** 가 호출되었거나 호출이 완료되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="24f4e-128">**ISSAsynchStatus::Abort** was called on a data source object on which **IDBInitialize::Initialize** has not been called, or has not completed.</span></span>  
  
 <span data-ttu-id="24f4e-129">**IDBInitialize:: Initialize** 가 호출 되었지만 이후에 초기화 되기 전에 취소 되었거나 시간이 초과 된 데이터 원본 개체에 대해 **ISSAsynchStatus:: Abort** 가 호출 되었습니다. 데이터 원본 개체가 아직 초기화 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="24f4e-129">**ISSAsynchStatus::Abort** was called on a data source object on which **IDBInitialize::Initialize** was called but subsequently canceled before initialization, or has timed out. The data source object is still uninitialized.</span></span>  
  
 <span data-ttu-id="24f4e-130">이전에**ITransaction::Ab가 호출된 행 집합에서t** 또는 **ITransaction::Ab가 호출된 행 집합에서t** 가 호출된 행 집합에서 **ITransaction::Ab가 호출된 행 집합에서t** was previously called, and the rowset did not survive the commit 가 호출된 행 집합에서 ab가 호출된 행 집합에서t and is in a zombie state.</span><span class="sxs-lookup"><span data-stu-id="24f4e-130">**ISSAsynchStatus::Abort** was called on a rowset on which **ITransaction::Commit** or **ITransaction::Abort** was previously called, and the rowset did not survive the commit or abort and is in a zombie state.</span></span>  
  
 <span data-ttu-id="24f4e-131">초기화 단계에서 비동기적으로 취소된 행 집합에서**ISSAsynchStatus::Abort** 가 취소되었습니다.</span><span class="sxs-lookup"><span data-stu-id="24f4e-131">**ISSAsynchStatus::Abort** was called on a rowset that was asynchronously canceled in its initialization phase.</span></span> <span data-ttu-id="24f4e-132">행 집합이 좀비 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24f4e-132">The rowset is in a zombie state.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24f4e-133">설명</span><span class="sxs-lookup"><span data-stu-id="24f4e-133">Remarks</span></span>  
 <span data-ttu-id="24f4e-134">행 집합이나 데이터 원본 개체의 초기화를 중단하면 행 집합이나 데이터 원본 개체가 좀비 상태로 유지되어 **IUnknown** 메서드가 아닌 모든 메서드에서 E_UNEXPECTED를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24f4e-134">Aborting the initialization of a rowset or data source object might leave the rowset or data source object in a zombie state, such that all methods other than **IUnknown** methods return E_UNEXPECTED.</span></span> <span data-ttu-id="24f4e-135">이 경우 소비자가 사용할 수 있는 유일한 동작은 행 집합이나 데이터 원본 개체를 해제하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="24f4e-135">When this happens, the only possible action for the consumer is to release the rowset or data source object.</span></span>  
  
 <span data-ttu-id="24f4e-136">**ISSAsynchStatus::Abort** 를 호출하고 DBASYNCHOP_OPEN이 아닌 *eOperation* 값을 전달하면 S_OK가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="24f4e-136">Calling **ISSAsynchStatus::Abort** and passing a value for *eOperation* other than DBASYNCHOP_OPEN returns S_OK.</span></span> <span data-ttu-id="24f4e-137">작업이 완료 또는 취소된 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="24f4e-137">This does not imply that the operation completed or was canceled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24f4e-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="24f4e-138">See Also</span></span>  
 [<span data-ttu-id="24f4e-139">비동기 작업 수행</span><span class="sxs-lookup"><span data-stu-id="24f4e-139">Performing Asynchronous Operations</span></span>](../native-client/features/performing-asynchronous-operations.md)  
  
  
