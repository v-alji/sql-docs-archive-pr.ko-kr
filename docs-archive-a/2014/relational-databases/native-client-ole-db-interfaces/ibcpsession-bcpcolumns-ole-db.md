---
title: IBCPSession::BCPColumns(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPColumns (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPColumns method
ms.assetid: c338abe8-9e30-4853-a7c6-b1a6c00095e1
author: rothja
ms.author: jroth
ms.openlocfilehash: c842b2a815074c0db7e6ab21e0a85eac68a986a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739820"
---
# <a name="ibcpsessionbcpcolumns-ole-db"></a><span data-ttu-id="c664e-102">IBCPSession::BCPColumns(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="c664e-102">IBCPSession::BCPColumns (OLE DB)</span></span>
  <span data-ttu-id="c664e-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블의 열에 바인딩될 필드의 개수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c664e-103">Sets the number of fields that are to be bound to the columns in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c664e-104">구문</span><span class="sxs-lookup"><span data-stu-id="c664e-104">Syntax</span></span>  
  
```  
  
HRESULT BCPColumns(   
DBCOUNTITEMnColumns);  
```  
  
## <a name="remarks"></a><span data-ttu-id="c664e-105">설명</span><span class="sxs-lookup"><span data-stu-id="c664e-105">Remarks</span></span>  
 <span data-ttu-id="c664e-106">이 메서드는 [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) 를 내부적으로 호출하여 필드 데이터의 기본값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c664e-106">Internally it calls [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) to set the default values for field data.</span></span> <span data-ttu-id="c664e-107">이러한 기본값은 [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md)를 통해 테이블 이름을 지정할 때 공급자가 내부적으로 검색하는 SQL Server 열 정보에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c664e-107">These default values are obtained from the SQL Server column information that the provider internally retrieves when the table name is specified through [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c664e-108"> 이 메서드는 유효한 파일 이름을 사용하여 **BCPInit** 를 호출한 후에만 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c664e-108">This method can be called only after **BCPInit** has been called with a valid file name.</span></span>  
  
 <span data-ttu-id="c664e-109">이 메서드는 기본값과는 다른 사용자 파일 형식을 사용하려는 경우에만 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c664e-109">You should call this method only if you intend to use a user-file format that differs from the default.</span></span> <span data-ttu-id="c664e-110">기본 사용자 파일 형식에 대한 자세한 설명을 보려면 **BCPInit** 메서드를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c664e-110">For more information about a description of the default user-file format, see the **BCPInit** method.</span></span>  
  
 <span data-ttu-id="c664e-111">사용자 정의 파일 형식을 완전하게 정의하려면 **BCPColumns** 메서드를 호출한 후에 사용자 파일의 각 열에 대해 **BCPColFmt** 메서드를 반드시 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c664e-111">After calling the **BCPColumns** method, you must call the **BCPColFmt** method for each column in the user file to completely define a custom file format.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="c664e-112">인수</span><span class="sxs-lookup"><span data-stu-id="c664e-112">Arguments</span></span>  
 <span data-ttu-id="c664e-113">*nColumns*[in]</span><span class="sxs-lookup"><span data-stu-id="c664e-113">*nColumns*[in]</span></span>  
 <span data-ttu-id="c664e-114">사용자 파일에 포함된 총 필드 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c664e-114">The total number of fields in the user file.</span></span> <span data-ttu-id="c664e-115">사용자 파일의 데이터를 SQL Server 테이블에 대량 복사하면서 사용자 파일의 필드 일부만 복사하려는 경우에도 *nColumns* 인수에 사용자 파일 필드의 총 개수를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c664e-115">Even if you are preparing to bulk copy data from the user file to a SQL Server table and do not intend to copy all fields in the user file, you must still set the *nColumns* argument to the total number of user-file fields.</span></span> <span data-ttu-id="c664e-116">이 경우 건너뛴 필드를 **BCPColFmt**를 통해 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c664e-116">The skipped fields can then be specified through **BCPColFmt**.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="c664e-117">반환 코드 값</span><span class="sxs-lookup"><span data-stu-id="c664e-117">Return Code Values</span></span>  
 <span data-ttu-id="c664e-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="c664e-118">S_OK</span></span>  
 <span data-ttu-id="c664e-119">메서드가 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c664e-119">The method succeeded.</span></span>  
  
 <span data-ttu-id="c664e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c664e-120">E_FAIL</span></span>  
 <span data-ttu-id="c664e-121">공급자별 오류가 발생 했습니다. 자세한 내용은 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) 인터페이스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c664e-121">A provider-specific error occurred; for detailed information, use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="c664e-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="c664e-122">E_UNEXPECTED</span></span>  
 <span data-ttu-id="c664e-123">예기치 않은 메서드가 호출되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c664e-123">The call to the method was unexpected.</span></span> <span data-ttu-id="c664e-124">예를 들어 이 메서드를 호출하기 전에 **BCPInit** 메서드를 호출하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c664e-124">For example, the **BCPInit** method was not called before calling this method.</span></span> <span data-ttu-id="c664e-125">대량 복사 작업에 이 메서드를 두 번 이상 호출한 경우에도 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="c664e-125">Also occurs when this method is called more than once for a bulk copy operation.</span></span>  
  
 <span data-ttu-id="c664e-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="c664e-126">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="c664e-127">메모리 부족 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="c664e-127">Out-of-memory error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c664e-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c664e-128">See Also</span></span>  
 <span data-ttu-id="c664e-129">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="c664e-129">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span></span>  
 [<span data-ttu-id="c664e-130">대량 복사 작업 수행</span><span class="sxs-lookup"><span data-stu-id="c664e-130">Performing Bulk Copy Operations</span></span>](../native-client/features/performing-bulk-copy-operations.md)  
  
  
