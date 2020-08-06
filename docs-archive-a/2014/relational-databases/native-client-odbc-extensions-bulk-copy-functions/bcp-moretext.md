---
title: bcp_moretext | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_moretext
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_moretext function
ms.assetid: 23e98015-a8e4-4434-9b3f-9c7350cf965f
author: rothja
ms.author: jroth
ms.openlocfilehash: 00c0eb1c8739e94380b12034cebc70d8e22b79c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649054"
---
# <a name="bcp_moretext"></a><span data-ttu-id="a0b02-102">bcp_moretext</span><span class="sxs-lookup"><span data-stu-id="a0b02-102">bcp_moretext</span></span>
  <span data-ttu-id="a0b02-103">긴 가변 길이 데이터 형식 값의 일부를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="a0b02-103">Sends part of a long, variable-length data type value to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0b02-104">구문</span><span class="sxs-lookup"><span data-stu-id="a0b02-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_moretext (  
HDBC   
hdbc  
,  
DBINT   
cbData  
,  
LPCBYTE   
pData  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="a0b02-105">인수</span><span class="sxs-lookup"><span data-stu-id="a0b02-105">Arguments</span></span>  
 <span data-ttu-id="a0b02-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="a0b02-106">*hdbc*</span></span>  
 <span data-ttu-id="a0b02-107">대량 복사가 가능한 ODBC 연결 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="a0b02-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="a0b02-108">*cbData*</span><span class="sxs-lookup"><span data-stu-id="a0b02-108">*cbData*</span></span>  
 <span data-ttu-id="a0b02-109">*.Pdata*에서 참조 하는 데이터 SQL Server에 복사 되는 데이터의 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="a0b02-109">Is the number of bytes of data being copied to SQL Server from the data referenced by *pData*.</span></span> <span data-ttu-id="a0b02-110">SQL_NULL_DATA 값은 NULL을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a0b02-110">A value of SQL_NULL_DATA indicates NULL.</span></span>  
  
 <span data-ttu-id="a0b02-111">*pData*</span><span class="sxs-lookup"><span data-stu-id="a0b02-111">*pData*</span></span>  
 <span data-ttu-id="a0b02-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 보낼 지원되는 긴 가변 길이 데이터 청크에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a0b02-112">Is a pointer to the supported, long, variable-length data chunk to be sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="returns"></a><span data-ttu-id="a0b02-113">반환</span><span class="sxs-lookup"><span data-stu-id="a0b02-113">Returns</span></span>  
 <span data-ttu-id="a0b02-114">SUCCEED 또는 FAIL</span><span class="sxs-lookup"><span data-stu-id="a0b02-114">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0b02-115">설명</span><span class="sxs-lookup"><span data-stu-id="a0b02-115">Remarks</span></span>  
 <span data-ttu-id="a0b02-116">이 함수는 [bcp_bind](bcp-bind.md) 및 [bcp_sendrow](bcp-sendrow.md) 와 함께 사용 하 여 긴 가변 길이 데이터 값을 여러 개의 작은 청크로 SQL Server 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0b02-116">This function can be used in conjunction with [bcp_bind](bcp-bind.md) and [bcp_sendrow](bcp-sendrow.md) to copy long, variable-length data values to SQL Server in a number of smaller chunks.</span></span> <span data-ttu-id="a0b02-117">**bcp_moretext** 는 `text` , `ntext` ,,,, `image` `varchar(max)` `nvarchar(max)` `varbinary(max)` , UDT (사용자 정의 형식) 및 XML과 같은 SQL Server 데이터 형식이 있는 열과 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0b02-117">**bcp_moretext** can be used with columns that have the following SQL Server data types: `text`, `ntext`, `image`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, user-defined type (UDT), and XML.</span></span> <span data-ttu-id="a0b02-118">**bcp_moretext** 데이터 변환을 지원 하지 않으므로 제공 된 데이터가 대상 열의 데이터 형식과 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0b02-118">**bcp_moretext** does not support data conversions, the data supplied must match the data type of the target column.</span></span>  
  
 <span data-ttu-id="a0b02-119">**Bcp_moretext**에서 지원 되는 데이터 형식에 대해 Null이 아닌 *.pdata* 매개 변수를 사용 하 여 **bcp_bind** 를 호출 하는 경우는 `bcp_sendrow` 길이에 관계 없이 전체 데이터 값을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="a0b02-119">If **bcp_bind** is called with a nonNULL *pData* parameter for data types that are supported by **bcp_moretext**, `bcp_sendrow` sends the entire data value, regardless of length.</span></span> <span data-ttu-id="a0b02-120">그러나 **bcp_bind** 지원 되는 데이터 형식에 대 한 NULL *.pdata* 매개 변수를 포함 하는 경우 데이터가 있는 **bcp_moretext** `bcp_sendrow` 바인딩된 모든 열이 처리 되었음을 나타내는에서 성공적으로 반환 된 후 즉시 데이터를 복사 하는 데 bcp_moretext 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0b02-120">If, however, **bcp_bind** has a NULL *pData* parameter for supported data types, **bcp_moretext** can be used to copy data immediately after a successful return from `bcp_sendrow` indicating that any bound columns with data present have been processed.</span></span>  
  
 <span data-ttu-id="a0b02-121">**Bcp_moretext** 를 사용 하 여 지원 되는 데이터 형식 열을 하나의 행에 보내려면이 열을 사용 하 여 행에서 지원 되는 다른 데이터 형식 열을 모두 전송 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0b02-121">If you use **bcp_moretext** to send one supported data type column in a row, you must also use it to send all other supported data type columns in the row.</span></span> <span data-ttu-id="a0b02-122">열을 건너뛸 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a0b02-122">No columns may be skipped.</span></span> <span data-ttu-id="a0b02-123">지원되는 데이터 형식은 SQLTEXT, SQLNTEXT, SQLIMAGE, SQLUDT 및 SQLXML입니다.</span><span class="sxs-lookup"><span data-stu-id="a0b02-123">Supported data types are SQLTEXT, SQLNTEXT, SQLIMAGE, SQLUDT and SQLXML.</span></span> <span data-ttu-id="a0b02-124">열이 각각 varchar(max), nvarchar(max) 또는 varbinary(max)인 경우 SQLCHARACTER, SQLVARCHAR, SQNCHAR, SQLBINARY 및 SQLVARBINARY도 이 범주에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="a0b02-124">SQLCHARACTER, SQLVARCHAR, SQNCHAR, SQLBINARY and SQLVARBINARY also fall into this category if the column is a varchar(max), nvarchar(max) or varbinary(max), respectively.</span></span>  
  
 <span data-ttu-id="a0b02-125">**Bcp_bind** 또는 [bcp_collen](bcp-collen.md) 를 호출 하면 SQL Server 열에 복사 되는 모든 데이터 부분의 총 길이가 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0b02-125">Calling either **bcp_bind** or [bcp_collen](bcp-collen.md) sets the total length of all data parts to be copied to the SQL Server column.</span></span> <span data-ttu-id="a0b02-126">**Bcp_bind** 에 대 한 호출에 지정 된 것 보다 더 많은 바이트 SQL Server 보내려는 시도는 `bcp_collen` 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0b02-126">An attempt to send SQL Server more bytes than specified in the call to **bcp_bind** or `bcp_collen` generates an error.</span></span> <span data-ttu-id="a0b02-127">예를 들어이 오류는 `bcp_collen` SQL Server 열에 사용 가능한 데이터의 길이를 4500로 설정 하는 데 사용 되는 응용 프로그램에서 `text` 데이터 버퍼 길이가 1000 바이트 였는 각 호출을 나타내는 동안 **bcp_moretext** 를 5 번 호출 하는 경우에 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0b02-127">This error would arise, for example, in an application which used `bcp_collen` to set the length of available data for an SQL Server `text` column to 4500, then called **bcp_moretext** five times while indicating on each call that the data buffer length was 1000 bytes long.</span></span>  
  
 <span data-ttu-id="a0b02-128">복사 된 행에 두 개 이상의 long 가변 길이 열이 포함 된 경우 **bcp_moretext** 는 먼저 가장 낮은 서 수로 번호 열에 데이터를 보내고 그 다음에 가장 낮은 서 수로 번호 열을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0b02-128">If a copied row contains more than one long, variable-length column, **bcp_moretext** first sends its data to the lowest ordinally numbered column, followed by the next lowest ordinally numbered column, and so on.</span></span> <span data-ttu-id="a0b02-129">필요한 데이터의 총 길이를 올바르게 설정하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="a0b02-129">Correct setting of the total length of expected data is important.</span></span> <span data-ttu-id="a0b02-130">길이 설정 외에는 대량 복사에서 열의 모든 데이터가 수신되었음을 나타낼 방법이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a0b02-130">There is no way to signal, outside of the length setting, that all data for a column has been received by bulk copy.</span></span>  
  
 <span data-ttu-id="a0b02-131">`var(max)`Bcp_sendrow 및 bcp_moretext를 사용 하 여 값을 서버로 보내는 경우에는 bcp_collen를 호출 하 여 열 길이를 설정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a0b02-131">When `var(max)` values are sent to the server using bcp_sendrow and bcp_moretext, it is not necessary to call bcp_collen to set the column length.</span></span> <span data-ttu-id="a0b02-132">대신 이러한 형식에 대해서만 값이 0 인 bcp_sendrow를 호출 하 여 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0b02-132">Instead, for these types only, the value is terminated by calling bcp_sendrow with a length of zero.</span></span>  
  
 <span data-ttu-id="a0b02-133">응용 프로그램은 일반적으로 `bcp_sendrow` 루프 내에서를 호출 하 고 **bcp_moretext** 하 여 많은 데이터 행을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="a0b02-133">An application normally calls `bcp_sendrow` and **bcp_moretext** within loops to send a number of rows of data.</span></span> <span data-ttu-id="a0b02-134">다음은 두 개의 열이 포함 된 테이블에 대해이 작업을 수행 하는 방법에 대 한 개요입니다 `text` .</span><span class="sxs-lookup"><span data-stu-id="a0b02-134">Here's an outline of how to do this for a table containing two `text` columns:</span></span>  
  
```  
while (there are still rows to send)  
{  
bcp_sendrow(...);  
  
for (all the data in the first varbinary(max) column)  
bcp_moretext(...);  
bcp_moretext(hdbc, 0, NULL);  
  
for (all the data in the second varbinary(max) column)  
bcp_moretext(...);  
bcp_moretext(hdbc, 0, NULL);  
  
}  
  
```  
  
## <a name="example"></a><span data-ttu-id="a0b02-135">예제</span><span class="sxs-lookup"><span data-stu-id="a0b02-135">Example</span></span>  
 <span data-ttu-id="a0b02-136">이 예제에서는 **bcp_bind** 와 함께 **bcp_moretext** 를 사용 하는 방법을 보여 줍니다 `bcp_sendrow` .</span><span class="sxs-lookup"><span data-stu-id="a0b02-136">This example shows how to use **bcp_moretext** with **bcp_bind** and `bcp_sendrow`:</span></span>  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
DBINT      idRow = 5;  
char*      pPart1 = "This text value isn't very long,";  
char*      pPart2 = " but it's broken into three parts";  
char*      pPart3 = " anyhow.";  
DBINT      cbAllParts;  
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
if (bcp_init(hdbc, "comdb..articles", NULL, NULL, DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Bind program variables to table columns.   
if (bcp_bind(hdbc, (LPCBYTE) &idRow, 0, SQL_VARLEN_DATA, NULL, 0,  
   SQLINT4, 1)    == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
cbAllParts = (DBINT) (strnlen(pPart1, sizeof(pPart1) + 1) + strnlen(pPart2, sizeof(pPart2) + 1) + strnlen(pPart3, sizeof(pPart3) + 1));  
if (bcp_bind(hdbc, NULL, 0, cbAllParts, NULL, 0, SQLTEXT, 2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Send this row, with the text value broken into three chunks.   
if (bcp_sendrow(hdbc) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart1, sizeof(pPart1) + 1), pPart1) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart2, sizeof(pPart2) + 1), pPart2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart3, sizeof(pPart3) + 1), pPart3) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// All done. Get the number of rows processed (should be one).  
nRowsProcessed = bcp_done(hdbc);  
  
// Carry on.  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0b02-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a0b02-137">See Also</span></span>  
 [<span data-ttu-id="a0b02-138">Bulk Copy Functions</span><span class="sxs-lookup"><span data-stu-id="a0b02-138">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
