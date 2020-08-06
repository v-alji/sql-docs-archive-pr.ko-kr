---
title: ISSAsynchStatus(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAsynchStatus (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- ISSAsynchStatus interface
ms.assetid: c643f09f-9ccc-4d8b-9243-3cde86c2bd46
author: rothja
ms.author: jroth
ms.openlocfilehash: 4489f9d1ad576d49d885842f6969f9b61065791c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649037"
---
# <a name="issasynchstatus-ole-db"></a><span data-ttu-id="a6b54-102">ISSAsynchStatus(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="a6b54-102">ISSAsynchStatus (OLE DB)</span></span>
  <span data-ttu-id="a6b54-103">**ISSAsynchStatus** 는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 비동기 작업에 대한 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a6b54-103">**ISSAsynchStatus** exposes support for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] asynchronous operations.</span></span> <span data-ttu-id="a6b54-104">이 인터페이스는 선택적 인터페이스이며 핵심 OLE DB 인터페이스인 **IDBAsynchStatus**에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6b54-104">This is an optional interface that inherits from the core OLE DB interface **IDBAsynchStatus**.</span></span> <span data-ttu-id="a6b54-105">**ISSAsynchStatus** 는 **IDBAsynchStatus** 에서 상속된 **Abort**및 **GetStatus** 메서드 이외에도 비동기 작업이 완료되거나 제한 시간이 초과될 때까지 대기하는 데 사용되는 새 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a6b54-105">In addition to the **Abort** and **GetStatus** methods inherited from **IDBAsynchStatus**, **ISSAsynchStatus** provides one new method that is used to wait until an asynchronous operation has completed or a time-out occurs.</span></span>  
  
|<span data-ttu-id="a6b54-106">방법</span><span class="sxs-lookup"><span data-stu-id="a6b54-106">Method</span></span>|<span data-ttu-id="a6b54-107">Description</span><span class="sxs-lookup"><span data-stu-id="a6b54-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a6b54-108">ISSAsynchStatus::Abort&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="a6b54-108">ISSAsynchStatus::Abort &#40;OLE DB&#41;</span></span>](issasynchstatus-abort-ole-db.md)|<span data-ttu-id="a6b54-109">비동기적으로 실행 중인 작업을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="a6b54-109">Cancels an asynchronously executing operation.</span></span>|  
|[<span data-ttu-id="a6b54-110">ISSAsynchStatus::GetStatus&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="a6b54-110">ISSAsynchStatus::GetStatus &#40;OLE DB&#41;</span></span>](issasynchstatus-getstatus-ole-db.md)|<span data-ttu-id="a6b54-111">비동기적으로 실행 중인 작업의 상태를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a6b54-111">Returns the status of an asynchronously executing operation.</span></span>|  
|[<span data-ttu-id="a6b54-112">ISSAsynchStatus::WaitForAsynchCompletion&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="a6b54-112">ISSAsynchStatus::WaitForAsynchCompletion &#40;OLE DB&#41;</span></span>](issasynchstatus-waitforasynchcompletion-ole-db.md)|<span data-ttu-id="a6b54-113">비동기적으로 실행 중인 작업이 완료되거나 제한 시간이 초과될 때까지 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="a6b54-113">Waits until the asynchronously executing operation is complete or a time-out occurs.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6b54-114">설명</span><span class="sxs-lookup"><span data-stu-id="a6b54-114">Remarks</span></span>  
 <span data-ttu-id="a6b54-115">**ISSAsynchStatus::GetStatus** 메서드의 **ISSAsynchStatus** 구현은 **IDBAsynchStatus::GetStatus** 메서드와 같지만 데이터 원본 개체의 초기화가 중단된 경우 DB_E_CANCELED 대신 E_UNEXPECTED를 반환한다는 점만 다릅니다(단, **ISSAsynchStatus::WaitForAsynchCompletion** 은 DB_E_CANCELED를 반환함).</span><span class="sxs-lookup"><span data-stu-id="a6b54-115">The **ISSAsynchStatus** implementation of the **ISSAsynchStatus::GetStatus** method is the same as the **IDBAsynchStatus::GetStatus** method except that if the initialization of a data source object is aborted, E_UNEXPECTED is returned rather than DB_E_CANCELED (although **ISSAsynchStatus::WaitForAsynchCompletion** returns DB_E_CANCELED).</span></span> <span data-ttu-id="a6b54-116">이는 중단 작업 이후 데이터 원본 개체가 평소의 상태로 유지되지 않아 추가적인 초기화 작업이 시도될 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="a6b54-116">This is because the data source object is not left in the usual state following an abort operation, so that further initialization operations may be attempted.</span></span>  
  
 <span data-ttu-id="a6b54-117">다음 메서드를 사용하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 비동기적인 실행을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6b54-117">The following methods support the use of asynchronous execution in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="a6b54-118">**ICommand::Execute**</span><span class="sxs-lookup"><span data-stu-id="a6b54-118">**ICommand::Execute**</span></span>  
  
-   <span data-ttu-id="a6b54-119">**IOpenRowset::OpenRowset**</span><span class="sxs-lookup"><span data-stu-id="a6b54-119">**IOpenRowset::OpenRowset**</span></span>  
  
-   <span data-ttu-id="a6b54-120">**IMultipleResults::GetResult**</span><span class="sxs-lookup"><span data-stu-id="a6b54-120">**IMultipleResults::GetResult**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6b54-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a6b54-121">See Also</span></span>  
 <span data-ttu-id="a6b54-122">[인터페이스 &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="a6b54-122">[Interfaces &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md) </span></span>  
 [<span data-ttu-id="a6b54-123">비동기 작업 수행</span><span class="sxs-lookup"><span data-stu-id="a6b54-123">Performing Asynchronous Operations</span></span>](../native-client/features/performing-asynchronous-operations.md)  
  
  
