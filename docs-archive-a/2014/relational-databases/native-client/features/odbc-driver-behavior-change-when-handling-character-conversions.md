---
title: 문자 변환을 처리할 때 ODBC 드라이버 동작 변경 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 682a232a-bf89-4849-88a1-95b2fbac1467
author: rothja
ms.author: jroth
ms.openlocfilehash: 5334b4268559ba155a53b3be655d87f7867779df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730584"
---
# <a name="odbc-driver-behavior-change-when-handling-character-conversions"></a><span data-ttu-id="bafac-102">문자 변환을 처리 시 ODBC 드라이버 동작 변경</span><span class="sxs-lookup"><span data-stu-id="bafac-102">ODBC Driver Behavior Change When Handling Character Conversions</span></span>
  <span data-ttu-id="bafac-103">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]Native CLIENT ODBC 드라이버 (SQLNCLI11.dll)는 SQL_WCHAR \* (NCHAR/nvarchar/nvarchar (max)) 및 SQL_CHAR \* (CHAR/VARCHAR/NARCHAR (max)) 변환의 수행 방법을 변경 했습니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-103">The [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client ODBC Driver (SQLNCLI11.dll) changed how it does of SQL_WCHAR\* (NCHAR/NVARCHAR/NVARCHAR(MAX)) and SQL_CHAR\* (CHAR/VARCHAR/NARCHAR(MAX)) conversions.</span></span> <span data-ttu-id="bafac-104">SQLGetData, SQLBindCol, SQLBindParameter와 같은 ODBC 함수는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 Native Client ODBC 드라이버 사용 시 길이/표시기 매개 변수로 (-4) SQL_NO_TOTAL을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-104">ODBC functions, such as SQLGetData, SQLBindCol, SQLBindParameter, return (-4) SQL_NO_TOTAL as the length/indicator parameter when using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 Native Client ODBC driver.</span></span> <span data-ttu-id="bafac-105">이전 버전의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC 드라이버는 길이 값을 반환했으며 이는 부정확할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-105">Prior versions of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver returned a length value, which can be incorrect.</span></span>  
  
## <a name="sqlgetdata-behavior"></a><span data-ttu-id="bafac-106">SQLGetData 동작</span><span class="sxs-lookup"><span data-stu-id="bafac-106">SQLGetData Behavior</span></span>  
 <span data-ttu-id="bafac-107">여러 가지 Windows 기능을 사용하여 버퍼 크기를 0으로 지정할 수 있고 반환된 길이가 반환된 데이터의 크기가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-107">Many Windows functions let you specify a buffer size of 0 and the returned length is the size of the returned data.</span></span> <span data-ttu-id="bafac-108">다음 패턴은 Windows 프로그래머에 공통적입니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-108">The following pattern is common for Windows programmers:</span></span>  
  
```  
int iSize = 0;  
BYTE * pBuffer = NULL;  
GetMyFavoriteAPI(pBuffer, &iSize);   // Returns needed size in iSize  
pBuffer = new BYTE[iSize];   // Allocate buffer   
GetMyFavoriteAPI(pBuffer, &iSize);   // Retrieve actual data  
```  
  
 <span data-ttu-id="bafac-109">그러나이 시나리오에서는 **SQLGetData** 를 사용 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-109">However, **SQLGetData** should not be used in this scenario.</span></span> <span data-ttu-id="bafac-110">다음 패턴을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-110">The following pattern should not be used:</span></span>  
  
```  
// bad  
int iSize = 0;  
WCHAR * pBuffer = NULL;  
SQLGetData(hstmt, SQL_W_CHAR, ...., (SQLPOINTER*)0x1, 0, &iSize);   // Get storage size needed  
pBuffer = new WCHAR[(iSize/sizeof(WCHAR)) + 1];   // Allocate buffer  
SQLGetData(hstmt, SQL_W_CHAR, ...., (SQLPOINTER*)pBuffer, iSize, &iSize);   // Retrieve data  
```  
  
 <span data-ttu-id="bafac-111">**SQLGetData** 를 호출 하 여 실제 데이터 청크를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-111">**SQLGetData** can only be called to retrieve chunks of actual data.</span></span> <span data-ttu-id="bafac-112">**SQLGetData** 를 사용 하 여 데이터 크기를 가져오는 것은 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-112">Using **SQLGetData** to get the size of data is not unsupported.</span></span>  
  
 <span data-ttu-id="bafac-113">다음은 잘못된 패턴 사용 시 드라이버 변경에 따른 영향을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-113">The following shows the impact of the driver change when you use the incorrect pattern.</span></span> <span data-ttu-id="bafac-114">이 애플리케이션은 `varchar`열 및 바인딩을 유니코드(SQL_UNICODE/SQL_WCHAR)로 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-114">This application queries a `varchar` column and binding as Unicode (SQL_UNICODE/SQL_WCHAR):</span></span>  
  
 <span data-ttu-id="bafac-115">쿼리입니다`select convert(varchar(36), '123')`</span><span class="sxs-lookup"><span data-stu-id="bafac-115">Query:  `select convert(varchar(36), '123')`</span></span>  
  
```  
SQLGetData(hstmt, SQL_WCHAR, ....., (SQLPOINTER*) 0x1, 0 , &iSize);   // Attempting to determine storage size needed  
```  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="bafac-116">Native Client ODBC 드라이버 버전</span><span class="sxs-lookup"><span data-stu-id="bafac-116">Native Client ODBC Driver version</span></span>|<span data-ttu-id="bafac-117">길이 또는 표시기 결과</span><span class="sxs-lookup"><span data-stu-id="bafac-117">Length or Indicator Outcome</span></span>|<span data-ttu-id="bafac-118">설명</span><span class="sxs-lookup"><span data-stu-id="bafac-118">Description</span></span>|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] <span data-ttu-id="bafac-119">Native Client 이하</span><span class="sxs-lookup"><span data-stu-id="bafac-119">Native Client or earlier</span></span>|<span data-ttu-id="bafac-120">6</span><span class="sxs-lookup"><span data-stu-id="bafac-120">6</span></span>|<span data-ttu-id="bafac-121">드라이버는 CHAR를 WCHAR로 변환하면 길이 \* 2로 수행될 수 있다고 잘못 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-121">The driver incorrectly assumed that converting CHAR to WCHAR could be accomplished as length \* 2.</span></span>|  
|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] <span data-ttu-id="bafac-122">Native Client(버전 11.0.2100.60) 이상</span><span class="sxs-lookup"><span data-stu-id="bafac-122">Native Client (version 11.0.2100.60) or later</span></span>|<span data-ttu-id="bafac-123">-4(SQL_NO_TOTAL)</span><span class="sxs-lookup"><span data-stu-id="bafac-123">-4 (SQL_NO_TOTAL)</span></span>|<span data-ttu-id="bafac-124">드라이버는 더 이상 CHAR에서 WCHAR로 또는 WCHAR에서 CHAR로의 변환이 (곱하기) \* 2 또는 (나누기)/2 동작 이라고 가정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-124">The driver no longer assumes that converting from CHAR to WCHAR or WCHAR to CHAR is a (multiply) \*2 or (divide)/2 action.</span></span><br /><br /> <span data-ttu-id="bafac-125">**SQLGetData** 를 호출 하면 더 이상 예상한 변환의 길이가 반환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-125">Calling **SQLGetData** no longer returns the length of the expected conversion.</span></span> <span data-ttu-id="bafac-126">드라이버가 CHAR에서 WCHAR 또는 WCHAR에서 CHAR로 변환을 검색하고 잘못될 수 있는 \*2 또는 /2 동작 대신 (-4) SQL_NO_TOTAL을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-126">The driver detects the conversion to or from CHAR and WCHAR and returns (-4) SQL_NO_TOTAL instead of \*2 or /2 behavior that could be incorrect.</span></span>|  
  
 <span data-ttu-id="bafac-127">**SQLGetData** 를 사용 하 여 데이터 청크를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-127">Use **SQLGetData** to retrieve the chunks of the data.</span></span> <span data-ttu-id="bafac-128">(의사 코드가 다음과 같이 표시됨)</span><span class="sxs-lookup"><span data-stu-id="bafac-128">(Pseudo code shown:)</span></span>  
  
```  
while( (SQL_SUCCESS or SQL_SUCCESS_WITH_INFO) == SQLFetch(...) ) {  
   SQLNumCols(...iTotalCols...)  
   for(int iCol = 1; iCol < iTotalCols; iCol++) {  
      WCHAR* pBufOrig, pBuffer = new WCHAR[100];  
      SQLGetData(.... iCol ... pBuffer, 100, &iSize);   // Get original chunk  
      while(NOT ALL DATA RETREIVED (SQL_NO_TOTAL, ...) ) {  
         pBuffer += 50;   // Advance buffer for data retrieved  
         // May need to realloc the buffer when you reach current size  
         SQLGetData(.... iCol ... pBuffer, 100, &iSize);   // Get next chunk  
      }  
   }  
}  
```  
  
## <a name="sqlbindcol-behavior"></a><span data-ttu-id="bafac-129">SQLBindCol 동작</span><span class="sxs-lookup"><span data-stu-id="bafac-129">SQLBindCol Behavior</span></span>  
 <span data-ttu-id="bafac-130">쿼리입니다`select convert(varchar(36), '1234567890')`</span><span class="sxs-lookup"><span data-stu-id="bafac-130">Query:  `select convert(varchar(36), '1234567890')`</span></span>  
  
```  
SQLBindCol(... SQL_W_CHAR, ...)   // Only bound a buffer of WCHAR[4] - Expecting String Data Right Truncation behavior  
```  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="bafac-131">Native Client ODBC 드라이버 버전</span><span class="sxs-lookup"><span data-stu-id="bafac-131">Native Client ODBC Driver version</span></span>|<span data-ttu-id="bafac-132">길이 또는 표시기 결과</span><span class="sxs-lookup"><span data-stu-id="bafac-132">Length or Indicator Outcome</span></span>|<span data-ttu-id="bafac-133">설명</span><span class="sxs-lookup"><span data-stu-id="bafac-133">Description</span></span>|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] <span data-ttu-id="bafac-134">Native Client 이하</span><span class="sxs-lookup"><span data-stu-id="bafac-134">Native Client or earlier</span></span>|<span data-ttu-id="bafac-135">20</span><span class="sxs-lookup"><span data-stu-id="bafac-135">20</span></span>|<span data-ttu-id="bafac-136">-   **Sqlfetch** 는 데이터 우변에 잘림이 있음을 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-136">-   **SQLFetch** reports that there is a truncation on the right side of the data.</span></span><br /><span data-ttu-id="bafac-137">-Length는 저장 된 데이터가 아니라 반환 되는 데이터의 길이입니다 (문자 모양에 대해 잘못 될 수 있는 \* 2 문자를 WCHAR로 변환 한다고 가정).</span><span class="sxs-lookup"><span data-stu-id="bafac-137">-   Length is the length of the data returned, not what was stored (assumes \*2 CHAR to WCHAR conversion which can be incorrect for glyphs).</span></span><br /><span data-ttu-id="bafac-138">-버퍼에 저장 된 데이터는 123 \ 0입니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-138">-   Data stored in buffer is 123\0.</span></span> <span data-ttu-id="bafac-139">버퍼는 NULL로 끝나지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-139">Buffer is guaranteed to be NULL terminated.</span></span>|  
|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] <span data-ttu-id="bafac-140">Native Client(버전 11.0.2100.60) 이상</span><span class="sxs-lookup"><span data-stu-id="bafac-140">Native Client (version 11.0.2100.60) or later</span></span>|<span data-ttu-id="bafac-141">-4(SQL_NO_TOTAL)</span><span class="sxs-lookup"><span data-stu-id="bafac-141">-4 (SQL_NO_TOTAL)</span></span>|<span data-ttu-id="bafac-142">-   **Sqlfetch** 는 데이터 우변에 잘림이 있음을 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-142">-   **SQLFetch** reports that there is a truncation on the right side of the data.</span></span><br /><span data-ttu-id="bafac-143">-길이는-4 (SQL_NO_TOTAL)를 나타내며 나머지 데이터는 변환 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-143">-   Length indicates -4 (SQL_NO_TOTAL) because the rest of the data was not converted.</span></span><br /><span data-ttu-id="bafac-144">-버퍼에 저장 된 데이터는 123 \ 0입니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-144">-   Data stored in the buffer is 123\0.</span></span> <span data-ttu-id="bafac-145">- 버퍼는 NULL로 끝나지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-145">- Buffer is guaranteed to be NULL terminated.</span></span>|  
  
## <a name="sqlbindparameter-output-parameter-behavior"></a><span data-ttu-id="bafac-146">SQLBindParameter(OUTPUT 매개 변수 동작)</span><span class="sxs-lookup"><span data-stu-id="bafac-146">SQLBindParameter (OUTPUT Parameter Behavior)</span></span>  
 <span data-ttu-id="bafac-147">쿼리입니다`create procedure spTest @p1 varchar(max) OUTPUT`</span><span class="sxs-lookup"><span data-stu-id="bafac-147">Query:  `create procedure spTest @p1 varchar(max) OUTPUT`</span></span>  
  
 `select @p1 = replicate('B', 1234)`  
  
```  
SQLBindParameter(... SQL_W_CHAR, ...)   // Only bind up to first 64 characters  
```  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="bafac-148">Native Client ODBC 드라이버 버전</span><span class="sxs-lookup"><span data-stu-id="bafac-148">Native Client ODBC Driver version</span></span>|<span data-ttu-id="bafac-149">길이 또는 표시기 결과</span><span class="sxs-lookup"><span data-stu-id="bafac-149">Length or Indicator Outcome</span></span>|<span data-ttu-id="bafac-150">설명</span><span class="sxs-lookup"><span data-stu-id="bafac-150">Description</span></span>|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] <span data-ttu-id="bafac-151">Native Client 이하</span><span class="sxs-lookup"><span data-stu-id="bafac-151">Native Client or earlier</span></span>|<span data-ttu-id="bafac-152">2468</span><span class="sxs-lookup"><span data-stu-id="bafac-152">2468</span></span>|<span data-ttu-id="bafac-153">-   **Sqlfetch** 는 더 이상 사용할 수 있는 데이터를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-153">-   **SQLFetch** returns no more data available.</span></span><br /><span data-ttu-id="bafac-154">-   **SQLMoreResults** 는 더 이상 사용할 수 있는 데이터를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-154">-   **SQLMoreResults** returns no more data available.</span></span><br /><span data-ttu-id="bafac-155">-Length는 버퍼에 저장 되지 않고 서버에서 반환 되는 데이터의 크기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-155">-   Length indicates the size of the data returned from server, not stored in buffer.</span></span><br /><span data-ttu-id="bafac-156">-원래 버퍼에는 63 바이트와 NULL 종결자가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-156">-   Original buffer contains 63 bytes and a NULL terminator.</span></span> <span data-ttu-id="bafac-157">버퍼는 NULL로 끝나지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-157">Buffer is guaranteed to be NULL terminated.</span></span>|  
|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] <span data-ttu-id="bafac-158">Native Client(버전 11.0.2100.60) 이상</span><span class="sxs-lookup"><span data-stu-id="bafac-158">Native Client (version 11.0.2100.60) or later</span></span>|<span data-ttu-id="bafac-159">-4(SQL_NO_TOTAL)</span><span class="sxs-lookup"><span data-stu-id="bafac-159">-4 (SQL_NO_TOTAL)</span></span>|<span data-ttu-id="bafac-160">-   **Sqlfetch** 는 더 이상 사용할 수 있는 데이터를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-160">-   **SQLFetch** returns no more data available.</span></span><br /><span data-ttu-id="bafac-161">-   **SQLMoreResults** 는 더 이상 사용할 수 있는 데이터를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-161">-   **SQLMoreResults** returns no more data available.</span></span><br /><span data-ttu-id="bafac-162">-Length는 (-4) SQL_NO_TOTAL의 나머지 데이터가 변환 되지 않았기 때문에이를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-162">-   Length indicates (-4) SQL_NO_TOTAL because the rest of the data was not converted.</span></span><br /><span data-ttu-id="bafac-163">-원래 버퍼에는 63 바이트와 NULL 종결자가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-163">-   Original buffer contains 63 bytes and a NULL terminator.</span></span> <span data-ttu-id="bafac-164">버퍼는 NULL로 끝나지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-164">Buffer is guaranteed to be NULL terminated.</span></span>|  
  
## <a name="performing-char-and-wchar-conversions"></a><span data-ttu-id="bafac-165">CHAR 및 WCHAR 변환 수행</span><span class="sxs-lookup"><span data-stu-id="bafac-165">Performing CHAR and WCHAR Conversions</span></span>  
 <span data-ttu-id="bafac-166">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client ODBC 드라이버는 CHAR 및 WCHAR 변환을 수행하는 여러 가지 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-166">The [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client ODBC driver offers several ways to perform CHAR and WCHAR conversions.</span></span> <span data-ttu-id="bafac-167">논리는 blob (varchar (max), nvarchar (max), ...)을 조작 하는 것과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-167">The logic is similar to manipulating blobs (varchar(max), nvarchar(max), ...):</span></span>  
  
-   <span data-ttu-id="bafac-168">**SQLBindCol** 또는 **SQLBindParameter**를 사용 하 여 바인딩할 때 데이터는 지정 된 버퍼에 저장 되거나 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-168">Data is saved or truncated into the specified buffer when binding with **SQLBindCol** or **SQLBindParameter**.</span></span>  
  
-   <span data-ttu-id="bafac-169">바인딩하지 않으면 **SQLGetData** 및 **sqlparamdata**를 사용 하 여 데이터를 청크로 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bafac-169">If you do not bind, you can retrieve the data in chunks by using **SQLGetData** and **SQLParamData**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bafac-170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bafac-170">See Also</span></span>  
 [<span data-ttu-id="bafac-171">SQL Server Native Client 기능</span><span class="sxs-lookup"><span data-stu-id="bafac-171">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
