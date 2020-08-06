---
title: ISSAsynchStatus::WaitForAsynchCompletion(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- WaitForAsynchCompletion method
ms.assetid: 9f65e9e7-eb93-47a1-bc42-acd4649fbd0e
author: rothja
ms.author: jroth
ms.openlocfilehash: f57211d1c62535828704dc971e345b412c284cf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649036"
---
# <a name="issasynchstatuswaitforasynchcompletion-ole-db"></a><span data-ttu-id="6b873-102">ISSAsynchStatus::WaitForAsynchCompletion(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="6b873-102">ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)</span></span>
  <span data-ttu-id="6b873-103">비동기적으로 실행 중인 작업이 완료되거나 제한 시간이 초과될 때까지 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="6b873-103">Waits until the asynchronously executing operation is complete or until a time-out occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b873-104">구문</span><span class="sxs-lookup"><span data-stu-id="6b873-104">Syntax</span></span>  
  
```  
  
HRESULT WaitForAsynchCompletion(   
  DWORD dwMillisecTimeOut);  
```  
  
## <a name="arguments"></a><span data-ttu-id="6b873-105">인수</span><span class="sxs-lookup"><span data-stu-id="6b873-105">Arguments</span></span>  
 <span data-ttu-id="6b873-106">*dwMillisecTimeOut*[in]</span><span class="sxs-lookup"><span data-stu-id="6b873-106">*dwMillisecTimeOut*[in]</span></span>  
 <span data-ttu-id="6b873-107">제한 시간(밀리초)입니다.</span><span class="sxs-lookup"><span data-stu-id="6b873-107">Time-out in milliseconds.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="6b873-108">반환 코드 값</span><span class="sxs-lookup"><span data-stu-id="6b873-108">Return Code Values</span></span>  
 <span data-ttu-id="6b873-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b873-109">S_OK</span></span>  
 <span data-ttu-id="6b873-110">메서드가 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="6b873-110">The method succeeded.</span></span>  
  
 <span data-ttu-id="6b873-111">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="6b873-111">E_UNEXPECTED</span></span>  
 <span data-ttu-id="6b873-112">**ITransaction::Commit** 또는 **ITransaction::Abort** 가 호출되었거나 행 집합이 초기화 단계 중 취소되었기 때문에 행 집합이 사용되지 않은 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="6b873-112">A rowset is in an unused state because **ITransaction::Commit** or **ITransaction::Abort** has been called or the rowset was cancelled during its initialization phase.</span></span>  
  
 <span data-ttu-id="6b873-113">DB_E_CANCELED</span><span class="sxs-lookup"><span data-stu-id="6b873-113">DB_E_CANCELED</span></span>  
 <span data-ttu-id="6b873-114">행 집합 채우기 또는 데이터 원본 개체 초기화 중 비동기 처리가 취소되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6b873-114">Asynchronous processing was cancelled during rowset population or data source object initialization.</span></span>  
  
 <span data-ttu-id="6b873-115">DB_S_ASYNCHRONOUS</span><span class="sxs-lookup"><span data-stu-id="6b873-115">DB_S_ASYNCHRONOUS</span></span>  
 <span data-ttu-id="6b873-116">지정한 제한 시간에 도달했지만 작업이 완료되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="6b873-116">The operation has not yet completed even though specified time-out has been reached.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6b873-117">위에 나열된 반환 코드 값 외에도 **ISSAsynchStatus::WaitForAsynchCompletion** 메서드는 코어 OLEDB **ICommand::Execute** 및 **IDBInitialize::Initialize** 메서드에서 반환하는 반환 코드 값을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6b873-117">In addition to the return code values listed above, the **ISSAsynchStatus::WaitForAsynchCompletion** method also supports the return code values returned by the core OLEDB **ICommand::Execute** and **IDBInitialize::Initialize** methods.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b873-118">설명</span><span class="sxs-lookup"><span data-stu-id="6b873-118">Remarks</span></span>  
 <span data-ttu-id="6b873-119">**ISSAsynchStatus::WaitForAsynchCompletion** 메서드는 제한 시간 값(밀리초)이 경과하거나 보류 중인 작업이 완료될 때까지 값을 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6b873-119">The **ISSAsynchStatus::WaitForAsynchCompletion** method will not return until the time-out value (in milliseconds) has passed or the pending operation is done.</span></span> <span data-ttu-id="6b873-120">**Command** 개체에는 시간이 초과 되기 전에 쿼리가 실행 되는 시간 (초)을 제어 하는 **CommandTimeout** 속성이 있습니다. **ISSAsynchStatus:: WaitForAsynchCompletion** 메서드와 함께 사용 하는 경우 **CommandTimeout** 속성은 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b873-120">The **Command** object has a **CommandTimeout** property that controls the number of seconds a query will run before timing out. The **CommandTimeout** property will be ignored if used in conjunction with **ISSAsynchStatus::WaitForAsynchCompletion** method.</span></span>  
  
 <span data-ttu-id="6b873-121">비동기 작업의 경우 제한 시간 속성이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b873-121">The time-out property is ignored for asynchronous operations.</span></span> <span data-ttu-id="6b873-122">**ISSAsynchStatus::WaitForAsynchCompletion** 의 제한 시간 매개 변수는 컨트롤이 호출자에게 반환되기 전까지의 최대 경과 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6b873-122">The time-out parameter of **ISSAsynchStatus::WaitForAsynchCompletion** specifies the maximum amount of time that will elapse before control is returned to the caller.</span></span> <span data-ttu-id="6b873-123">제한 시간이 만료되면 DB_S_ASYNCHRONOUS가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b873-123">If this time-out expires, DB_S_ASYNCHRONOUS will be returned.</span></span> <span data-ttu-id="6b873-124">제한 시간을 지정해도 비동기 작업이 취소되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6b873-124">Time-outs never cancel asynchronous operations.</span></span> <span data-ttu-id="6b873-125">애플리케이션이 제한 시간 내에 완료되지 않은 비동기 작업을 취소해야 할 경우 애플리케이션은 제한 시간에 도달할 때까지 기다린 다음 DB_S_ASYNCHRONOUS가 반환되면 작업을 명시적으로 취소해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b873-125">If the application needs to cancel an asynchronous operation that does not complete within a time-out period, it must wait for the time-out and then explicitly cancel the operation if DB_S_ASYNCHRONOUS is returned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6b873-126">OLE DB Service Component를 사용하는 경우 DB_S_ASYNCHRONOUS 대신 S_OK가 반환될 수 있으므로 S_OK 또는 DB_S_ASYNCHRONOUS가 반환되는 경우 애플리케이션은 [ISSAsynchStatus::GetStatus](issasynchstatus-getstatus-ole-db.md) 를 호출하여 완료 여부를 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b873-126">When the OLE DB Service Components are used, S_OK may be returned when DB_S_ASYNCHRONOUS is expected, so applications should call [ISSAsynchStatus::GetStatus](issasynchstatus-getstatus-ole-db.md) to check for completion when S_OK or DB_S_ASYNCHRONOUS is returned.</span></span>  
  
 <span data-ttu-id="6b873-127">*dwMillisecTimeOut* 값이 INFINITE로 설정되면 작업이 완료될 때까지 **ISSAsynchStatus::WaitForAsynchCompletion** 메서드가 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b873-127">If the *dwMillisecTimeOut* value is set to INFINITE, the **ISSAsynchStatus::WaitForAsynchCompletion** method blocks until the operation is done.</span></span> <span data-ttu-id="6b873-128">*dwMillisecTimeOut* 값이 0으로 설정되면 보류 중인 작업의 상태와 함께 메서드가 즉시 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b873-128">If the *dwMillisecTimeOut* value is set to 0, then the method will return immediately with the status of the pending operation.</span></span> <span data-ttu-id="6b873-129">작업이 완료되기 전에 제한 시간이 만료되면 DB_S_ASYNCHRONOUS가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b873-129">If the time-out expires before the operation is complete DB_S_ASYNCHRONOUS will be returned.</span></span>  
  
 <span data-ttu-id="6b873-130">제한 시간이 만료되기 전에 작업이 완료되면 반환되는 HRESULT는 작업이 반환하는 HRESULT(작업이 동기적으로 수행된 경우 반환되는 HRESULT)입니다.</span><span class="sxs-lookup"><span data-stu-id="6b873-130">If the operation completes before the time-out expires, the returned HRESULT will be the HRESULT returned by the operation (the HRESULT that would have been returned had the operation been performed synchronously).</span></span>  
  
 <span data-ttu-id="6b873-131">또한 SSPROP_ISSAsynchStatus 속성이 DBPROPSET_SQLSERVERROWSET 속성 집합에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6b873-131">In addition, the SSPROP_ISSAsynchStatus property has been added to the DBPROPSET_SQLSERVERROWSET property set.</span></span> <span data-ttu-id="6b873-132">[ISSAsynchStatus](issasynchstatus-ole-db.md) 인터페이스를 지원하는 공급자는 VARIANT_TRUE 값을 사용하여 이 속성을 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b873-132">Providers that support the [ISSAsynchStatus](issasynchstatus-ole-db.md) interface must implement this property with a value of VARIANT_TRUE.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b873-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6b873-133">See Also</span></span>  
 <span data-ttu-id="6b873-134">[비동기 작업 수행](../native-client/features/performing-asynchronous-operations.md) </span><span class="sxs-lookup"><span data-stu-id="6b873-134">[Performing Asynchronous Operations](../native-client/features/performing-asynchronous-operations.md) </span></span>  
 [<span data-ttu-id="6b873-135">ISSAsynchStatus&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="6b873-135">ISSAsynchStatus &#40;OLE DB&#41;</span></span>](issasynchstatus-ole-db.md)  
  
  
