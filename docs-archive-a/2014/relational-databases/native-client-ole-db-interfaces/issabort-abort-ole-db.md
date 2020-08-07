---
title: ISSAbort::Abort(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAbort::Abort (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Abort method
ms.assetid: a5bca169-694b-4895-84ac-e8fba491e479
author: rothja
ms.author: jroth
ms.openlocfilehash: 3daad53087c876af8dc46bccc9c4bf7952976067
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734055"
---
# <a name="issabortabort-ole-db"></a><span data-ttu-id="bcfea-102">ISSAbort::Abort(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="bcfea-102">ISSAbort::Abort (OLE DB)</span></span>
  <span data-ttu-id="bcfea-103">현재 행 집합 및 현재 명령과 연결된 일괄 처리되는 명령을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="bcfea-103">Cancels the current rowset plus any batched commands associated with the current command.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcfea-104">구문</span><span class="sxs-lookup"><span data-stu-id="bcfea-104">Syntax</span></span>  
  
```  
  
HRESULT Abort(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="bcfea-105">설명</span><span class="sxs-lookup"><span data-stu-id="bcfea-105">Remarks</span></span>  
 <span data-ttu-id="bcfea-106">중단할 명령이 저장 프로시저에 있으면 저장 프로시저 및 해당 프로시저를 호출한 프로시저의 실행 및 저장 프로시저 호출이 포함된 명령 일괄 처리가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="bcfea-106">If the command being aborted is in a stored procedure, execution of the stored procedure (and any procedures which had called that procedure) will be terminated as well as the command batch which contains the stored procedure call.</span></span> <span data-ttu-id="bcfea-107">서버에서 결과 집합을 클라이언트로 전송 중이면 전송이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="bcfea-107">If the server is in the process of transferring a result set to the client, this will be stopped.</span></span> <span data-ttu-id="bcfea-108">클라이언트가 결과 집합을 사용하지 않으려는 경우 행 집합을 해제하기 전에 **ISSAbort::Abort**를 호출하면 행 집합을 신속하게 해제할 수 있습니다. 그러나 열려 있는 트랜잭션이 있고 XACT_ABORT가 ON인 경우 **ISSAbort::Abort**를 호출하면 트랜잭션이 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="bcfea-108">If the client does not want to consume a result set, calling **ISSAbort::Abort** before releasing the rowset will speed up the rowset release, but if there is an open transaction and XACT_ABORT is ON, the transaction will be rolled back when **ISSAbort::Abort** is called</span></span>  
  
 <span data-ttu-id="bcfea-109">**ISSAbort:: Abort** 가 S_OK를 반환 하면 연결 된 **IMultipleResults** 인터페이스가 사용할 수 없는 상태로 전환 되 고 해제 될 때까지 모든 메서드 호출 ( **IUnknown** 인터페이스에 의해 정의 된 메서드 제외)에 DB_E_CANCELED 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bcfea-109">After **ISSAbort::Abort** returns S_OK, the associated **IMultipleResults** interface enters a unusable state and returns DB_E_CANCELED to all method calls (except for methods defined by the **IUnknown** interface) until it is released.</span></span> <span data-ttu-id="bcfea-110">**Abort**를 호출하기 전에 **IMultipleResults**에서 **IRowset**을 가져온 경우에도 **ISSAbort::Abort** 호출 후 인터페이스가 사용할 수 없는 상태로 전환되어 해제될 때까지 모든 메서드 호출(**IUnknown** 인터페이스 및 **IRowset::ReleaseRows**로 정의된 메서드는 제외)에 대해 DB_E_CANCELED를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bcfea-110">If an **IRowset** had been obtained from **IMultipleResults** prior to a call to **Abort**, it also enters an unusable state and returns DB_E_CANCELED to all method calls (except for methods defined by the **IUnknown** interface and **IRowset::ReleaseRows**) until it is released after a successful call to **ISSAbort::Abort**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bcfea-111">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]부터는 서버 XACT_ABORT 상태가 ON일 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 연결되어 있을 때 **ISSAbort::Abort**를 실행하면 현재의 암시적 또는 명시적 트랜잭션이 종료되고 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="bcfea-111">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], if the server XACT_ABORT state is ON, executing **ISSAbort::Abort** will terminate and roll back any current implicit or explicit transaction when connected to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bcfea-112">이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 현재 트랜잭션이 중단되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bcfea-112">Earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will not abort the current transaction.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="bcfea-113">인수</span><span class="sxs-lookup"><span data-stu-id="bcfea-113">Arguments</span></span>  
 <span data-ttu-id="bcfea-114">없음</span><span class="sxs-lookup"><span data-stu-id="bcfea-114">None.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="bcfea-115">반환 코드 값</span><span class="sxs-lookup"><span data-stu-id="bcfea-115">Return Code Values</span></span>  
 <span data-ttu-id="bcfea-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="bcfea-116">S_OK</span></span>  
 <span data-ttu-id="bcfea-117">일괄 처리가 취소되었으면 **ISSAbort::Abort** 메서드가 S_OK를 반환하고, 그렇지 않으면 DB_E_CANTCANCEL을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bcfea-117">The **ISSAbort::Abort** method returns S_OK if the batch was canceled and DB_E_CANTCANCEL otherwise.</span></span> <span data-ttu-id="bcfea-118">일괄 처리가 이미 취소되었으면 DB_E_CANCELED가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="bcfea-118">If the batch has already been canceled, DB_E_CANCELED is returned.</span></span>  
  
 <span data-ttu-id="bcfea-119">DB_E_CANCELED</span><span class="sxs-lookup"><span data-stu-id="bcfea-119">DB_E_CANCELED</span></span>  
 <span data-ttu-id="bcfea-120">일괄 처리가 이미 취소되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bcfea-120">The batch has already been canceled.</span></span>  
  
 <span data-ttu-id="bcfea-121">DB_E_CANTCANCEL</span><span class="sxs-lookup"><span data-stu-id="bcfea-121">DB_E_CANTCANCEL</span></span>  
 <span data-ttu-id="bcfea-122">일괄 처리가 취소되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="bcfea-122">The batch was not canceled.</span></span>  
  
 <span data-ttu-id="bcfea-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bcfea-123">E_FAIL</span></span>  
 <span data-ttu-id="bcfea-124">공급자별 오류가 발생 했습니다. 자세한 내용은 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) 인터페이스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bcfea-124">A provider specific error occurred; for detailed information, use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="bcfea-125">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="bcfea-125">E_UNEXPECTED</span></span>  
 <span data-ttu-id="bcfea-126">예기치 않은 메서드가 호출되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bcfea-126">The call to the method was unexpected.</span></span> <span data-ttu-id="bcfea-127">**ISSAbort::Abort**가 이미 호출되어 개체가 좀비 상태에 있는 경우를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bcfea-127">For example, the object is in a zombie state because **ISSAbort::Abort** has already been called.</span></span>  
  
 <span data-ttu-id="bcfea-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="bcfea-128">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="bcfea-129">메모리 부족 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="bcfea-129">Out of memory error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcfea-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bcfea-130">See Also</span></span>  
 [<span data-ttu-id="bcfea-131">ISSAbort &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="bcfea-131">ISSAbort &#40;OLE DB&#41;</span></span>](../../database-engine/dev-guide/issabort-ole-db.md)  
  
  
