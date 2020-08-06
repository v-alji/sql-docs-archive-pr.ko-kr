---
title: IBCPSession::BCPExec(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPExec (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPExec method
ms.assetid: 0f4ebb63-cf03-4e53-846e-6c3021cde007
author: rothja
ms.author: jroth
ms.openlocfilehash: 1452888e046b6223c64a6cdf6fe09b074b815702
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729440"
---
# <a name="ibcpsessionbcpexec-ole-db"></a><span data-ttu-id="81867-102">IBCPSession::BCPExec(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="81867-102">IBCPSession::BCPExec (OLE DB)</span></span>
  <span data-ttu-id="81867-103">대량 복사 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="81867-103">Performs the bulk copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81867-104">구문</span><span class="sxs-lookup"><span data-stu-id="81867-104">Syntax</span></span>  
  
```  
  
HRESULT BCPExec(   
DBROWCOUNT *pRowsCopied);  
```  
  
## <a name="remarks"></a><span data-ttu-id="81867-105">설명</span><span class="sxs-lookup"><span data-stu-id="81867-105">Remarks</span></span>  
 <span data-ttu-id="81867-106">**BCPExec** 메서드는 [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) 메서드에 사용된 *eDirection* 매개 변수 값에 따라 데이터를 사용자 파일에서 데이터베이스 테이블로 복사하거나 그 반대로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="81867-106">The **BCPExec** method copies data from a user file to a database table or vice versa, depending on the value of the *eDirection* parameter used with the [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) method.</span></span>  
  
 <span data-ttu-id="81867-107">**BCPExec**를 호출하기 전에 올바른 사용자 파일 이름을 지정하여 **BCPInit** 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="81867-107">Before calling **BCPExec**, call the **BCPInit** method with a valid user file name.</span></span> <span data-ttu-id="81867-108">그렇게 하지 않으면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="81867-108">Failure to do so results in an error.</span></span> <span data-ttu-id="81867-109">단, 쿼리를 대량 복사하기(bulk copy out) 작업에 사용할 경우는 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="81867-109">The only exception is if a query is to be used for a bulk copy out operation.</span></span> <span data-ttu-id="81867-110">이 경우 **BCPInit** 메서드에서 테이블 이름에 NULL을 지정한 다음, BCP_OPTION_HINTS 옵션을 사용하여 쿼리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="81867-110">In that case specify NULL for the table name in the **BCPInit** method and then specify the query using the BCP_OPTION_HINTS option.</span></span>  
  
 <span data-ttu-id="81867-111">**BCPExec** 메서드는 무한정 보류될 수 있는 유일한 대량 복사 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="81867-111">The **BCPExec** method is the only bulk copy method that is likely to be outstanding for any length of time.</span></span> <span data-ttu-id="81867-112">따라서 비동기 모드를 지원하는 유일한 대량 복사 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="81867-112">It is therefore the only bulk copy method that supports asynchronous mode.</span></span> <span data-ttu-id="81867-113">비동기 모드를 사용 하려면 **Bcpexec** 메서드를 호출 하기 전에 공급자별 세션 속성 SSPROP_ASYNCH_BULKCOPY VARIANT_TRUE로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="81867-113">To use asynchronous mode, set the provider specific session property SSPROP_ASYNCH_BULKCOPY to VARIANT_TRUE before calling the **BCPExec** method.</span></span> <span data-ttu-id="81867-114">이 속성은 DBPROPSET_SQLSERVERSESSION 속성 집합에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81867-114">This property is available in the DBPROPSET_SQLSERVERSESSION property set.</span></span> <span data-ttu-id="81867-115">완료를 테스트하려면 같은 매개 변수를 사용하여 **BCPExec**를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="81867-115">To test for completion, call the **BCPExec** method with the same parameters.</span></span> <span data-ttu-id="81867-116">대량 복사가 완료되지 않은 경우 **BCPExec** 메서드는 DB_S_ASYNCHRONOUS를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="81867-116">If the bulk copy has not yet completed, the **BCPExec** method returns DB_S_ASYNCHRONOUS.</span></span> <span data-ttu-id="81867-117">또한 이 메서드는 서버로 전송하거나 서버에서 수신한 행 수에 대한 상태 개수를 *pRowsCopied* 인수에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="81867-117">It also returns in the *pRowsCopied* argument a status count of the number of rows that have been sent to or received from the server.</span></span> <span data-ttu-id="81867-118">서버로 전송된 행은 일괄 처리의 끝에 도달할 때까지 커밋되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="81867-118">Rows sent to the server are not committed until the end of a batch has been reached.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="81867-119">인수</span><span class="sxs-lookup"><span data-stu-id="81867-119">Arguments</span></span>  
 <span data-ttu-id="81867-120">*pRowsCopied*[out]</span><span class="sxs-lookup"><span data-stu-id="81867-120">*pRowsCopied*[out]</span></span>  
 <span data-ttu-id="81867-121">DWORD에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="81867-121">A pointer to a DWORD.</span></span> <span data-ttu-id="81867-122">**BCPExec** 메서드는 성공적으로 복사된 행 수로 DWORD를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="81867-122">The **BCPExec** method fills the DWORD with the number of rows successfully copied.</span></span> <span data-ttu-id="81867-123">*pRowsCopied* 인수를 NULL로 설정하면 **BCPExec** 메서드에서 이 인수를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="81867-123">If the *pRowsCopied* argument is set to NULL, it is ignored by the **BCPExec** method.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="81867-124">반환 코드 값</span><span class="sxs-lookup"><span data-stu-id="81867-124">Return Code Values</span></span>  
 <span data-ttu-id="81867-125">S_OK</span><span class="sxs-lookup"><span data-stu-id="81867-125">S_OK</span></span>  
 <span data-ttu-id="81867-126">메서드가 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="81867-126">The method succeeded.</span></span>  
  
 <span data-ttu-id="81867-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="81867-127">E_FAIL</span></span>  
 <span data-ttu-id="81867-128">공급자별 오류가 발생 했습니다. 자세한 내용은 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) 인터페이스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="81867-128">A provider-specific error occurred; for detailed information, use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="81867-129">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="81867-129">E_UNEXPECTED</span></span>  
 <span data-ttu-id="81867-130">예기치 않은 메서드가 호출되었습니다.</span><span class="sxs-lookup"><span data-stu-id="81867-130">The call to the method was unexpected.</span></span> <span data-ttu-id="81867-131">예를 들어 이 메서드를 호출하기 전에 **BCPInit** 메서드를 호출하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="81867-131">For example, the **BCPInit** method was not called before calling this method.</span></span> <span data-ttu-id="81867-132">BCP_OPTION_ABORT 옵션을 사용하여 작업이 중단된 이후에 **BCPExec** 메서드를 호출한 경우에도 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="81867-132">Also occurs if the operation has been aborted through using the BCP_OPTION_ABORT option, and the **BCPExec** method was called afterwards.</span></span>  
  
 <span data-ttu-id="81867-133">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="81867-133">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="81867-134">메모리 부족 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="81867-134">Out-of-memory error.</span></span>  
  
 <span data-ttu-id="81867-135">DB_S_ENDOFROWSET</span><span class="sxs-lookup"><span data-stu-id="81867-135">DB_S_ENDOFROWSET</span></span>  
 <span data-ttu-id="81867-136">대량 복사 작업이 완료되었고 데이터 전송이 모두 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="81867-136">The bulk copy operation finished, and all the data transfer was completed.</span></span>  
  
 <span data-ttu-id="81867-137">DB_S_ASYNCHRONOUS</span><span class="sxs-lookup"><span data-stu-id="81867-137">DB_S_ASYNCHRONOUS</span></span>  
 <span data-ttu-id="81867-138">행의 현재 일괄 처리가 복사되었습니다.</span><span class="sxs-lookup"><span data-stu-id="81867-138">The current batch of rows has been copied.</span></span> <span data-ttu-id="81867-139">다음 일괄 처리를 전송하려면 **BCPExec** 메서드를 다시 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="81867-139">Call the **BCPExec** method again to transfer the next batch.</span></span>  
  
 <span data-ttu-id="81867-140">DB_S_ERRORSOCCURRED</span><span class="sxs-lookup"><span data-stu-id="81867-140">DB_S_ERRORSOCCURRED</span></span>  
 <span data-ttu-id="81867-141">대량 복사 작업 동안 오류가 발생하여 일부 행이 복사되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="81867-141">Errors occurred during the bulk copy operation, and some rows might not have been copied.</span></span> <span data-ttu-id="81867-142">오류 수는 아직 허용되는 최대 오류 수보다 적습니다.</span><span class="sxs-lookup"><span data-stu-id="81867-142">The number of errors is still less than the maximum errors allowed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81867-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="81867-143">See Also</span></span>  
 <span data-ttu-id="81867-144">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="81867-144">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span></span>  
 [<span data-ttu-id="81867-145">대량 복사 작업 수행</span><span class="sxs-lookup"><span data-stu-id="81867-145">Performing Bulk Copy Operations</span></span>](../native-client/features/performing-bulk-copy-operations.md)  
  
  
