---
title: IBCPSession::BCPWriteFmt(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPWriteFmt (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPWriteFmt method
ms.assetid: add50425-2ed6-411a-a391-4ce63c364892
author: rothja
ms.author: jroth
ms.openlocfilehash: ee4dcb5809c0f0fbb6d3f7aba6f4af5f6991e0e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659966"
---
# <a name="ibcpsessionbcpwritefmt-ole-db"></a><span data-ttu-id="7287e-102">IBCPSession::BCPWriteFmt(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="7287e-102">IBCPSession::BCPWriteFmt (OLE DB)</span></span>
  <span data-ttu-id="7287e-103">각 열에 대한 서식 정보를 서식 파일에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="7287e-103">Writes format information for each column to the format file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7287e-104">구문</span><span class="sxs-lookup"><span data-stu-id="7287e-104">Syntax</span></span>  
  
```  
  
HRESULT BCPWriteFmt(   
const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a><span data-ttu-id="7287e-105">설명</span><span class="sxs-lookup"><span data-stu-id="7287e-105">Remarks</span></span>  
 <span data-ttu-id="7287e-106">서식 파일은 대량 복사를 통해 만들어진 데이터 파일의 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7287e-106">The format file specifies the data format of a data file created by bulk copy.</span></span> <span data-ttu-id="7287e-107">[IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) 및 [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) 메서드를 호출하여 데이터 파일의 형식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7287e-107">Calls to the [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) and [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) methods define the format of the data file.</span></span> <span data-ttu-id="7287e-108">**BCPWriteFmt** 메서드는 이 정의를 pwszFormatFile 인수에서 참조하는 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="7287e-108">The **BCPWriteFmt** method saves this definition in the file referenced by the pwszFormatFile argument.</span></span>  
  
 <span data-ttu-id="7287e-109">**BCPWriteFmt** 메서드는 서식 파일을 xml 또는 text 형식으로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7287e-109">The **BCPWriteFmt** method can save the format files in either xml or text format.</span></span> <span data-ttu-id="7287e-110">[IBCPSession::BCPControl](ibcpsession-bcpcontrol-ole-db.md) 메서드에 BCP_OPTION_XML 제어 옵션을 사용하여 서식 파일의 형식을 나타내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7287e-110">This must be indicated by using the BCP_OPTION_XML control option with the [IBCPSession::BCPControl](ibcpsession-bcpcontrol-ole-db.md) method.</span></span>  
  
 <span data-ttu-id="7287e-111">저장된 서식 파일을 로드하려면 [IBCPSession::BCPReadFmt](ibcpsession-bcpreadfmt-ole-db.md) 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7287e-111">To load a saved format file, use the [IBCPSession::BCPReadFmt](ibcpsession-bcpreadfmt-ole-db.md) method.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="7287e-112">인수</span><span class="sxs-lookup"><span data-stu-id="7287e-112">Arguments</span></span>  
 <span data-ttu-id="7287e-113">*pwszFormatFile*[in]</span><span class="sxs-lookup"><span data-stu-id="7287e-113">*pwszFormatFile*[in]</span></span>  
 <span data-ttu-id="7287e-114">데이터 파일에 대한 형식 값이 포함된 파일의 경로 및 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7287e-114">The path and file name of the file containing the format values for the data file.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="7287e-115">반환 코드 값</span><span class="sxs-lookup"><span data-stu-id="7287e-115">Return Code Values</span></span>  
 <span data-ttu-id="7287e-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="7287e-116">S_OK</span></span>  
 <span data-ttu-id="7287e-117">메서드가 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="7287e-117">The method succeeded.</span></span>  
  
 <span data-ttu-id="7287e-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7287e-118">E_FAIL</span></span>  
 <span data-ttu-id="7287e-119">공급자별 오류가 발생 했습니다. 자세한 내용은 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) 인터페이스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7287e-119">A provider-specific error occurred; for detailed information, use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="7287e-120">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7287e-120">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="7287e-121">메모리 부족 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="7287e-121">Out-of-memory error.</span></span>  
  
 <span data-ttu-id="7287e-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="7287e-122">E_UNEXPECTED</span></span>  
 <span data-ttu-id="7287e-123">예기치 않은 메서드가 호출되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7287e-123">The call to the method was unexpected.</span></span> <span data-ttu-id="7287e-124">예를 들어 이 메서드를 호출하기 전에 [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) 메서드를 호출하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="7287e-124">For example, the [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) method was not called before calling this method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7287e-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7287e-125">See Also</span></span>  
 <span data-ttu-id="7287e-126">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="7287e-126">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span></span>  
 [<span data-ttu-id="7287e-127">대량 복사 작업 수행</span><span class="sxs-lookup"><span data-stu-id="7287e-127">Performing Bulk Copy Operations</span></span>](../native-client/features/performing-bulk-copy-operations.md)  
  
  
