---
title: bcp_readfmt | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_readfmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_readfmt function
ms.assetid: 654001c8-ae9f-425c-b820-f0191bf89367
author: rothja
ms.author: jroth
ms.openlocfilehash: 37032ec276be8b914d73e834453cc5d87cdedbbe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649051"
---
# <a name="bcp_readfmt"></a><span data-ttu-id="a84c7-102">bcp_readfmt</span><span class="sxs-lookup"><span data-stu-id="a84c7-102">bcp_readfmt</span></span>
  <span data-ttu-id="a84c7-103">지정한 형식 파일에서 데이터 파일 형식 정의를 읽어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="a84c7-103">Reads a data file format definition from the specified format file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a84c7-104">구문</span><span class="sxs-lookup"><span data-stu-id="a84c7-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_readfmt (  
HDBC   
hdbc  
,  
LPCTSTR   
szFormatFile  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="a84c7-105">인수</span><span class="sxs-lookup"><span data-stu-id="a84c7-105">Arguments</span></span>  
 <span data-ttu-id="a84c7-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="a84c7-106">*hdbc*</span></span>  
 <span data-ttu-id="a84c7-107">대량 복사가 가능한 ODBC 연결 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="a84c7-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="a84c7-108">*szFormatFile*</span><span class="sxs-lookup"><span data-stu-id="a84c7-108">*szFormatFile*</span></span>  
 <span data-ttu-id="a84c7-109">데이터 파일에 대한 서식 값이 포함된 파일의 경로 및 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="a84c7-109">Is the path and file name of the file containing the format values for the data file.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="a84c7-110">반환</span><span class="sxs-lookup"><span data-stu-id="a84c7-110">Returns</span></span>  
 <span data-ttu-id="a84c7-111">SUCCEED 또는 FAIL</span><span class="sxs-lookup"><span data-stu-id="a84c7-111">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a84c7-112">설명</span><span class="sxs-lookup"><span data-stu-id="a84c7-112">Remarks</span></span>  
 <span data-ttu-id="a84c7-113">는 `bcp_readfmt` 형식 값을 읽은 후 [bcp_columns](bcp-columns.md) 및 [bcp_colfmt](bcp-colfmt.md)에 대 한 적절 한 호출을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84c7-113">After `bcp_readfmt` reads the format values, it makes the appropriate calls to [bcp_columns](bcp-columns.md) and [bcp_colfmt](bcp-colfmt.md).</span></span> <span data-ttu-id="a84c7-114">형식 파일의 구문을 분석하여 이러한 호출을 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a84c7-114">There is no need for you to parse a format file and make these calls.</span></span>  
  
 <span data-ttu-id="a84c7-115">형식 파일을 저장하려면 [bcp_writefmt](bcp-writefmt.md)를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="a84c7-115">To persist a format file, call [bcp_writefmt](bcp-writefmt.md).</span></span> <span data-ttu-id="a84c7-116">에 대 한 호출은 `bcp_readfmt` 저장 된 형식을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a84c7-116">Calls to `bcp_readfmt` can reference saved formats.</span></span> <span data-ttu-id="a84c7-117">자세한 내용은 [bcp_init](bcp-init.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a84c7-117">For more information, see [bcp_init](bcp-init.md).</span></span>  
  
 <span data-ttu-id="a84c7-118">또는**bcp**(대량 복사 유틸리티)는에서 참조할 수 있는 파일에 사용자 정의 데이터 형식을 저장할 수 있습니다 `bcp_readfmt` .</span><span class="sxs-lookup"><span data-stu-id="a84c7-118">Alternately, the bulk-copy utility (**bcp**) can save user-defined data formats in files that can be referenced by `bcp_readfmt`.</span></span> <span data-ttu-id="a84c7-119">**Bcp 유틸리티와** **bcp** 데이터 형식 파일의 구조에 대 한 자세한 내용은 [데이터 대량 가져오기 및 내보내기 &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a84c7-119">For more information about the **bcp** utility and the structure of **bcp** data format files, see [Bulk Import and Export of Data &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="a84c7-120">`BCPDELAYREADFMT` [Bcp_control](bcp-control.md) *eoption* 매개 변수의 값은 bcp_readfmt 동작을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84c7-120">The `BCPDELAYREADFMT` value of the *eOption* parameter of [bcp_control](bcp-control.md) modifies the behavior of bcp_readfmt.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a84c7-121">형식 파일은 **bcp** 유틸리티 4.2 이상 버전에서 생성된 파일이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84c7-121">The format file must have been produced by version 4.2 or later of the **bcp** utility.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a84c7-122">예제</span><span class="sxs-lookup"><span data-stu-id="a84c7-122">Example</span></span>  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, _T("myTable"), _T("myData.csv"),  
   _T("myErrors"),    DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_readfmt(hdbc, _T("myFmtFile.fmt")) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_exec(hdbc, &nRowsProcessed) == SUCCEED)  
   {  
   cout << nRowsProcessed << " rows copied to SQL Server\n";  
   }  
  
// Carry on.  
```  
  
## <a name="see-also"></a><span data-ttu-id="a84c7-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a84c7-123">See Also</span></span>  
 [<span data-ttu-id="a84c7-124">Bulk Copy Functions</span><span class="sxs-lookup"><span data-stu-id="a84c7-124">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
