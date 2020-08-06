---
title: IBCPSession::BCPReadFmt(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPReadFmt (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPReadFmt method
ms.assetid: e2a12050-94e4-48a3-8a48-b780d646f116
author: rothja
ms.author: jroth
ms.openlocfilehash: ca811dceb8ab6771e3bdd6689a8e11eca6a0e3ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739807"
---
# <a name="ibcpsessionbcpreadfmt-ole-db"></a><span data-ttu-id="3c7c5-102">IBCPSession::BCPReadFmt(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="3c7c5-102">IBCPSession::BCPReadFmt (OLE DB)</span></span>
  <span data-ttu-id="3c7c5-103">서식 파일에서 각 열의 서식 정보를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="3c7c5-103">Reads format information for each column from the format file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c7c5-104">구문</span><span class="sxs-lookup"><span data-stu-id="3c7c5-104">Syntax</span></span>  
  
```  
  
HRESULT BCPReadFmt(   
const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a><span data-ttu-id="3c7c5-105">설명</span><span class="sxs-lookup"><span data-stu-id="3c7c5-105">Remarks</span></span>  
 <span data-ttu-id="3c7c5-106">**BCPReadFmt** 메서드는 데이터 파일의 데이터 형식을 지정하는 서식 파일에서 데이터를 읽을 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c7c5-106">The **BCPReadFmt** method is used for reading data from a format file that specifies the format of data in the data file.</span></span> <span data-ttu-id="3c7c5-107">이 메서드는 서식 파일의 올바른 버전을 검색할 수 있으므로</span><span class="sxs-lookup"><span data-stu-id="3c7c5-107">This method is capable of detecting the correct version of the format file.</span></span> <span data-ttu-id="3c7c5-108">서식 파일이 xml인지 이전 스타일의 텍스트 형식인지 자동으로 검색하여 그에 따라 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7c5-108">It can automatically detect whether the format file is in xml or old style text format and behaves accordingly.</span></span> <span data-ttu-id="3c7c5-109">Native Client OLE DB provider BCP에서 지 원하는 형식 파일 버전은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전 6.0 이상입니다.</span><span class="sxs-lookup"><span data-stu-id="3c7c5-109">The format file versions supported by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider BCP are version 6.0 or newer.</span></span>  
  
 <span data-ttu-id="3c7c5-110">**BCPReadFmt** 메서드는 형식 값을 읽은 후 [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) 및 [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) 메서드를 적절히 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7c5-110">After the **BCPReadFmt** method reads the format values, it makes the appropriate calls to the [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) and [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) methods.</span></span> <span data-ttu-id="3c7c5-111">따라서 사용자가 서식 파일의 구문을 분석하여 메서드를 호출할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3c7c5-111">There is no need for the user to parse a format file and make these calls.</span></span>  
  
 <span data-ttu-id="3c7c5-112">서식 파일을 저장하려면 [IBCPSession::BCPWriteFmt](ibcpsession-bcpwritefmt-ole-db.md) 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7c5-112">To save a format file, call the [IBCPSession::BCPWriteFmt](ibcpsession-bcpwritefmt-ole-db.md) method.</span></span> <span data-ttu-id="3c7c5-113">**BCPReadFmt** 메서드를 호출할 때 저장된 형식을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c7c5-113">Calls to the **BCPReadFmt** method can reference saved formats.</span></span> <span data-ttu-id="3c7c5-114">또한 대량 복사 유틸리티(**bcp**)로 사용자 정의 데이터 형식을 **BCPReadFmt** 메서드가 참조할 수 있는 파일에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c7c5-114">Alternatively, the bulk-copy utility (**bcp**) can save user-defined data formats in files that can be referenced by the **BCPReadFmt** method.</span></span>  
  
 <span data-ttu-id="3c7c5-115">`BCP_OPTION_DELAYREADFMT` [IBCPSession:: BCPControl](ibcpsession-bcpcontrol-ole-db.md) 의 *eoption* 매개 변수 값은 IBCPSession:: bcpreadfmt의 동작을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7c5-115">The `BCP_OPTION_DELAYREADFMT` value of the *eOption* parameter of [IBCPSession::BCPControl](ibcpsession-bcpcontrol-ole-db.md) modifies the behavior of IBCPSession::BCPReadFmt.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="3c7c5-116">인수</span><span class="sxs-lookup"><span data-stu-id="3c7c5-116">Arguments</span></span>  
 <span data-ttu-id="3c7c5-117">*pwszFormatFile*[in]</span><span class="sxs-lookup"><span data-stu-id="3c7c5-117">*pwszFormatFile*[in]</span></span>  
 <span data-ttu-id="3c7c5-118">데이터 파일에 대한 형식 값이 포함된 파일의 경로 및 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="3c7c5-118">The path and file name of the file containing the format values for the data file.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="3c7c5-119">반환 코드 값</span><span class="sxs-lookup"><span data-stu-id="3c7c5-119">Return Code Values</span></span>  
 <span data-ttu-id="3c7c5-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="3c7c5-120">S_OK</span></span>  
 <span data-ttu-id="3c7c5-121">메서드가 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="3c7c5-121">The method succeeded.</span></span>  
  
 <span data-ttu-id="3c7c5-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3c7c5-122">E_FAIL</span></span>  
 <span data-ttu-id="3c7c5-123">공급자 관련 오류가 발생했습니다. 자세한 내용을 보려면 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) 인터페이스를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="3c7c5-123">A provider-specific error occurred, for detailed information use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="3c7c5-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="3c7c5-124">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="3c7c5-125">메모리 부족 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="3c7c5-125">Out of memory error.</span></span>  
  
 <span data-ttu-id="3c7c5-126">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="3c7c5-126">E_UNEXPECTED</span></span>  
 <span data-ttu-id="3c7c5-127">예기치 않은 메서드가 호출되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c7c5-127">The call to the method was unexpected.</span></span> <span data-ttu-id="3c7c5-128">예를 들어 이 메서드를 호출하기 전에 [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) 메서드를 호출하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="3c7c5-128">For example, the [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) method was not called before calling this method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c7c5-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3c7c5-129">See Also</span></span>  
 <span data-ttu-id="3c7c5-130">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="3c7c5-130">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span></span>  
 [<span data-ttu-id="3c7c5-131">대량 복사 작업 수행</span><span class="sxs-lookup"><span data-stu-id="3c7c5-131">Performing Bulk Copy Operations</span></span>](../native-client/features/performing-bulk-copy-operations.md)  
  
  
