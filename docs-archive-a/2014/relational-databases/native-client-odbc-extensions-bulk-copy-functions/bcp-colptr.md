---
title: bcp_colptr | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_colptr
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_colptr function
ms.assetid: 02ece13e-1da3-4f9d-b860-3177e43d2471
author: rothja
ms.author: jroth
ms.openlocfilehash: 8b725ace58ee1768fbca1a433cdea27e3e0e546e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742012"
---
# <a name="bcp_colptr"></a><span data-ttu-id="0f9cb-102">bcp_colptr</span><span class="sxs-lookup"><span data-stu-id="0f9cb-102">bcp_colptr</span></span>
  <span data-ttu-id="0f9cb-103">현재 복사본의 프로그램 변수 데이터 주소를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0f9cb-103">Sets the program variable data address for the current copy into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f9cb-104">구문</span><span class="sxs-lookup"><span data-stu-id="0f9cb-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_colptr (  
HDBC   
hdbc  
,  
LPCBYTE   
pData  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="0f9cb-105">인수</span><span class="sxs-lookup"><span data-stu-id="0f9cb-105">Arguments</span></span>  
 <span data-ttu-id="0f9cb-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="0f9cb-106">*hdbc*</span></span>  
 <span data-ttu-id="0f9cb-107">대량 복사가 가능한 ODBC 연결 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="0f9cb-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="0f9cb-108">*pData*</span><span class="sxs-lookup"><span data-stu-id="0f9cb-108">*pData*</span></span>  
 <span data-ttu-id="0f9cb-109">복사할 데이터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0f9cb-109">Is a pointer to the data to copy.</span></span> <span data-ttu-id="0f9cb-110">바인딩된 데이터 형식이 대량 값 형식 (예: SQLTEXT 또는 SQLIMAGE) 인 경우 *.pdata* 는 NULL 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f9cb-110">If the bound data type is large value type (such as SQLTEXT or SQLIMAGE), *pData* can be NULL.</span></span> <span data-ttu-id="0f9cb-111">NULL *.pdata* 는 long 데이터 값이 [bcp_moretext](bcp-moretext.md)를 사용 하 여 SQL Server 청크로 전송 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0f9cb-111">A NULL *pData* indicates long data values will be sent to SQL Server in chunks using [bcp_moretext](bcp-moretext.md).</span></span>  
  
 <span data-ttu-id="0f9cb-112">*.Pdata* 가 NULL로 설정 되어 있고 바인딩된 필드에 해당 하는 열이 크기가 크지 않은 경우 **bcp_colptr** 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f9cb-112">If *pData* is set to NULL and the column corresponding to the bound field is not a large value type, **bcp_colptr** fails.</span></span>  
  
 <span data-ttu-id="0f9cb-113">대량 값 형식에 대 한 자세한 내용은 [bcp_bind](bcp-bind.md)를 참조**하세요.**</span><span class="sxs-lookup"><span data-stu-id="0f9cb-113">For more information on large value types, see [bcp_bind](bcp-bind.md)**.**</span></span>  
  
 <span data-ttu-id="0f9cb-114">*idxServerCol*</span><span class="sxs-lookup"><span data-stu-id="0f9cb-114">*idxServerCol*</span></span>  
 <span data-ttu-id="0f9cb-115">데이터 복사 대상인 데이터베이스 테이블 열의 서수 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="0f9cb-115">Is the ordinal position of the column in the database table to which the data is copied.</span></span> <span data-ttu-id="0f9cb-116">테이블의 첫 번째 열은 열 1입니다.</span><span class="sxs-lookup"><span data-stu-id="0f9cb-116">The first column in a table is column 1.</span></span> <span data-ttu-id="0f9cb-117">열의 서수 위치는 [SQLColumns](../native-client-odbc-api/sqlcolumns.md)를 사용하여 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f9cb-117">The ordinal position of a column is reported by [SQLColumns](../native-client-odbc-api/sqlcolumns.md).</span></span>  
  
## <a name="returns"></a><span data-ttu-id="0f9cb-118">반환</span><span class="sxs-lookup"><span data-stu-id="0f9cb-118">Returns</span></span>  
 <span data-ttu-id="0f9cb-119">SUCCEED 또는 FAIL</span><span class="sxs-lookup"><span data-stu-id="0f9cb-119">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f9cb-120">설명</span><span class="sxs-lookup"><span data-stu-id="0f9cb-120">Remarks</span></span>  
 <span data-ttu-id="0f9cb-121">**Bcp_colptr** 함수를 사용 하면 [bcp_sendrow](bcp-sendrow.md)로 SQL Server 데이터를 복사할 때 특정 열의 원본 데이터 주소를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f9cb-121">The **bcp_colptr** function allows you to change the address of source data for a particular column when copying data to SQL Server with [bcp_sendrow](bcp-sendrow.md).</span></span>  
  
 <span data-ttu-id="0f9cb-122">처음에는 사용자 데이터에 대 한 포인터가 **bcp_bind**를 호출 하 여 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f9cb-122">Initially, the pointer to user data is set by a call to **bcp_bind**.</span></span> <span data-ttu-id="0f9cb-123">프로그램 변수 데이터 주소가 **bcp_sendrow**호출 사이에서 변경 되는 경우 **bcp_colptr** 를 호출 하 여 포인터를 데이터에 다시 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f9cb-123">If the program variable data address changes between calls to **bcp_sendrow**, you can call **bcp_colptr** to reset the pointer to the data.</span></span> <span data-ttu-id="0f9cb-124">**Bcp_sendrow** 에 대 한 다음 호출에서는 **bcp_colptr**호출로 주소가 지정 된 데이터를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="0f9cb-124">The next call to **bcp_sendrow** sends the data addressed by the call to **bcp_colptr**.</span></span>  
  
 <span data-ttu-id="0f9cb-125">데이터 주소를 수정 하려는 테이블의 모든 열에 대해 별도의 **bcp_colptr** 호출이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f9cb-125">There must be a separate **bcp_colptr** call for every column in the table whose data address you want to modify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f9cb-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0f9cb-126">See Also</span></span>  
 [<span data-ttu-id="0f9cb-127">Bulk Copy Functions</span><span class="sxs-lookup"><span data-stu-id="0f9cb-127">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
