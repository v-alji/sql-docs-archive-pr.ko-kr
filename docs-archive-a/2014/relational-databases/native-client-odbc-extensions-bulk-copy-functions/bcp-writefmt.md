---
title: bcp_writefmt | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_writefmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_writefmt function
ms.assetid: cb4c1d37-667d-4bcd-b13c-eb638bcc9b69
author: rothja
ms.author: jroth
ms.openlocfilehash: 13785469e0b02f63f14d28f0db87e77df3a15cfa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652094"
---
# <a name="bcp_writefmt"></a><span data-ttu-id="ef934-102">bcp_writefmt</span><span class="sxs-lookup"><span data-stu-id="ef934-102">bcp_writefmt</span></span>
  <span data-ttu-id="ef934-103">현재 대량 복사 데이터 파일의 서식에 대한 설명이 포함된 서식 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ef934-103">Creates a format file containing a description of the format of the current bulk copy data file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef934-104">구문</span><span class="sxs-lookup"><span data-stu-id="ef934-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_writefmt (  
HDBC   
hdbc  
,  
LPCTSTR   
szFormatFile  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="ef934-105">인수</span><span class="sxs-lookup"><span data-stu-id="ef934-105">Arguments</span></span>  
 <span data-ttu-id="ef934-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="ef934-106">*hdbc*</span></span>  
 <span data-ttu-id="ef934-107">대량 복사가 가능한 ODBC 연결 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="ef934-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="ef934-108">*szFormatFile*</span><span class="sxs-lookup"><span data-stu-id="ef934-108">*szFormatFile*</span></span>  
 <span data-ttu-id="ef934-109">데이터 파일의 형식 값을 받을 사용자 파일의 경로와 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ef934-109">Is the path and file name of the user file to receive format values for the data file.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="ef934-110">반환</span><span class="sxs-lookup"><span data-stu-id="ef934-110">Returns</span></span>  
 <span data-ttu-id="ef934-111">SUCCEED 또는 FAIL</span><span class="sxs-lookup"><span data-stu-id="ef934-111">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef934-112">설명</span><span class="sxs-lookup"><span data-stu-id="ef934-112">Remarks</span></span>  
 <span data-ttu-id="ef934-113">서식 파일은 대량 복사를 통해 만들어진 데이터 파일의 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ef934-113">The format file specifies the data format of a data file created by bulk copy.</span></span> <span data-ttu-id="ef934-114">[Bcp_columns](bcp-columns.md) 및 [bcp_colfmt](bcp-colfmt.md) 를 호출 하 여 데이터 파일의 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef934-114">Calls to [bcp_columns](bcp-columns.md) and [bcp_colfmt](bcp-colfmt.md) define the format of the data file.</span></span> <span data-ttu-id="ef934-115">**bcp_writefmt** 는이 정의를 *szformatfile*에서 참조 하는 파일에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef934-115">**bcp_writefmt** saves this definition in the file referenced by *szFormatFile*.</span></span> <span data-ttu-id="ef934-116">자세한 내용은 [bcp_init](bcp-init.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ef934-116">For more information, see [bcp_init](bcp-init.md).</span></span>  
  
 <span data-ttu-id="ef934-117">**Bcp** 데이터 형식 파일의 구조에 대 한 자세한 내용은 [Bcp 유틸리티를 사용 하 여 대량 데이터 가져오기 및 내보내기 &#40;SQL Server&#41;](../import-export/import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ef934-117">For more information about the structure of **bcp** data format files, see [Import and Export Bulk Data by Using the bcp Utility &#40;SQL Server&#41;](../import-export/import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md).</span></span>  
  
 <span data-ttu-id="ef934-118">저장 된 서식 파일을 로드 하려면 [bcp_readfmt](bcp-readfmt.md)을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef934-118">To load a saved format file, use [bcp_readfmt](bcp-readfmt.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ef934-119">**Bcp_writefmt** 에서 생성 된 서식 파일은 버전 7.0 이상으로 배포 된 **bcp** 유틸리티 버전 에서만 지원 됩니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ef934-119">The format file produced by **bcp_writefmt** is supported only by versions of the **bcp** utility distributed with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef934-120">예제</span><span class="sxs-lookup"><span data-stu-id="ef934-120">Example</span></span>  
  
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
   _T("myErrors"),    DB_OUT) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_columns(hdbc, 3) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
bcp_colfmt(hdbc, 1, SQLCHARACTER, 0, SQL_VARLEN_DATA, '\t', 1, 1);  
bcp_colfmt(hdbc, 2, SQLCHARACTER, 0, SQL_VARLEN_DATA, '\t', 1, 2);  
bcp_colfmt(hdbc, 3, SQLCHARACTER, 0, SQL_VARLEN_DATA, '\t', 1, 3);  
  
if (bcp_writefmt(hdbc, _T("myFmtFile.fmt")) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_exec(hdbc, &nRowsProcessed) == SUCCEED)  
   {  
   printf_s("%ld rows copied from SQL Server\n", nRowsProcessed);  
   }  
  
// Carry on.  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef934-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ef934-121">See Also</span></span>  
 [<span data-ttu-id="ef934-122">Bulk Copy Functions</span><span class="sxs-lookup"><span data-stu-id="ef934-122">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
