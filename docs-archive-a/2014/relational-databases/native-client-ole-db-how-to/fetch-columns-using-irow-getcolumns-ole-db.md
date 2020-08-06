---
title: IRow::GetColumns를 사용하여 열 페치(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- IRow interface
ms.assetid: a4f79906-da0e-42f2-b0e9-812c29f39e48
author: rothja
ms.author: jroth
ms.openlocfilehash: 1e3eb9e2b55ad03ae4b5739850557836589649d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729475"
---
# <a name="fetch-columns-using-irowgetcolumns-ole-db"></a><span data-ttu-id="7ecc6-102">IRow::GetColumns를 사용하여 열 인출(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="7ecc6-102">Fetch Columns Using IRow::GetColumns (OLE DB)</span></span>
  <span data-ttu-id="7ecc6-103">`IRow` 인터페이스를 사용하여 결과 집합에 있는 단일 행의 열에 직접 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-103">The `IRow` interface allows direct access to columns of a single row in the result set.</span></span> <span data-ttu-id="7ecc6-104">따라서 `IRow`는 행이 한 개인 결과 집합에서 열을 검색하는 데 효과적입니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-104">Thus, `IRow` is an efficient way to retrieve columns from a result set with one row.</span></span>  
  
 <span data-ttu-id="7ecc6-105">`IRow`를 사용하여 단일 행을 인출하는 방법을 보여 주는 코드 예제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-105">A code sample is available that showshow to fetch a single row using `IRow`.</span></span> <span data-ttu-id="7ecc6-106">이 예제에서는 행에서 한 번에 한 개의 열이 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-106">In this sample, one column at a time is retrieved from the row.</span></span> <span data-ttu-id="7ecc6-107">이 예제에서는 다음 작업을 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-107">The sample shows:</span></span>  
  
-   <span data-ttu-id="7ecc6-108">열 그룹을 순서대로 인출하는 방법</span><span class="sxs-lookup"><span data-stu-id="7ecc6-108">How to fetch a group of columns (in sequence).</span></span>  
  
-   <span data-ttu-id="7ecc6-109">한 열에 두 번 액세스하는 방법.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-109">How to access a column twice.</span></span> <span data-ttu-id="7ecc6-110">처음에는 실제 열 너비를 가져오고 다음에는 실제 데이터에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-110">The first time the actual column width is obtained, and later the actual data is accessed.</span></span> <span data-ttu-id="7ecc6-111">DBCOLUMNACCESS 구조체에서 **.pdata** 가 NULL이 고 **cbMaxLen** 가 0 인 경우에 대 한 호출은 `IRow` - `>GetColumns()` 실제 열 길이만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-111">In the DBCOLUMNACCESS structure, if **pData** is NULL and **cbMaxLen** is 0, the call to `IRow`-`>GetColumns()` returns only the actual column length.</span></span> <span data-ttu-id="7ecc6-112">이 경우 같은 열에 대해 `IRow->GetColumns()`를 다시 호출하여 실제 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-112">In this case, `IRow->GetColumns()` can be called again on the same column to retrieve the actual data.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7ecc6-113">가능하면 Windows 인증을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-113">When possible, use Windows Authentication.</span></span> <span data-ttu-id="7ecc6-114">Windows 인증을 사용할 수 없으면 런타임에 사용자에게 자격 증명을 입력하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-114">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="7ecc6-115">자격 증명은 파일에 저장하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-115">Avoid storing credentials in a file.</span></span> <span data-ttu-id="7ecc6-116">자격 증명을 유지 해야 하는 경우에는 [Win32 CRYPTO API](https://go.microsoft.com/fwlink/?LinkId=64532)를 사용 하 여 자격 증명을 암호화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-116">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
### <a name="to-fetch-columns-using-irowgetcolumns"></a><span data-ttu-id="7ecc6-117">IRow::GetColumns를 사용하여 열을 인출하려면</span><span class="sxs-lookup"><span data-stu-id="7ecc6-117">To fetch columns using IRow::GetColumns</span></span>  
  
1.  <span data-ttu-id="7ecc6-118">데이터 원본에 대한 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-118">Establish a connection to the data source.</span></span>  
  
2.  <span data-ttu-id="7ecc6-119">명령을 실행합니다. 다음 예에서는 IID_IRow를 사용하여 ICommandExecute::Execute()가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-119">Execute the command (in the following example, ICommandExecute::Execute() is called with IID_IRow).</span></span>  
  
3.  <span data-ttu-id="7ecc6-120">IRow::GetColumns()를 실행하여 결과 행에 있는 하나 이상의 열을 인출합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-120">Execute IRow::GetColumns() to fetch one or more columns in the resulting row.</span></span> <span data-ttu-id="7ecc6-121">데이터를 인출하기 전에 실제 열 크기를 검색하려면 DBCOLUMNACCESS의 pData를 NULL로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-121">If you want to find the actual column size before fetching data, set the pData in DBCOLUMNACCESS to NULL.</span></span> <span data-ttu-id="7ecc6-122">그러면 IRow::GetColumns() 호출에서 열 너비만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-122">The call to IRow::GetColumns() returns only the column width.</span></span> <span data-ttu-id="7ecc6-123">두 번째 IRow::GetColumns() 호출에서는 데이터를 인출합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-123">Another call the IRow::GetColumns() will fetch the data.</span></span>  
  
4.  <span data-ttu-id="7ecc6-124">필요한 모든 열에 액세스할 때까지 IRow::GetColumns()를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-124">Execute IRow::GetColumns() until all the columns you need are accessed.</span></span> <span data-ttu-id="7ecc6-125">순서대로 열에 액세스해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-125">The columns must be accessed in sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ecc6-126">예제</span><span class="sxs-lookup"><span data-stu-id="7ecc6-126">Example</span></span>  
 <span data-ttu-id="7ecc6-127">이 예제에서는 IRow 인터페이스를 사용하여 결과 집합에 있는 단일 행의 열에 직접 액세스를 허용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-127">This sample shows how to use the IRow interface to allow direct access to columns of a single row in the result set.</span></span> <span data-ttu-id="7ecc6-128">예에서는 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-128">The example shows:</span></span>  
  
-   <span data-ttu-id="7ecc6-129">열 그룹을 순서대로 인출하는 방법</span><span class="sxs-lookup"><span data-stu-id="7ecc6-129">How to fetch a group of columns in sequence.</span></span>  
  
-   <span data-ttu-id="7ecc6-130">한 열에 두 번 액세스하는 방법 - 처음에는 실제 열 너비를 가져오고 다음에는 실제 데이터에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-130">How to access a column twice - the first time the actual column width is obtained and then later the actual data is accessed.</span></span>  
  
 <span data-ttu-id="7ecc6-131">DBCOLUMNACCESS 구조에서 pData가 NULL이고 cbMaxLen이 0이면 IRow->GetColumns 호출에서 실제 열 길이만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-131">In the DBCOLUMNACCESS structure, if pData is NULL and cbMaxLen is 0, the call to IRow->GetColumns returns only the actual column length.</span></span> <span data-ttu-id="7ecc6-132">이 경우 같은 열에 대해 IRow->GetColumns를 다시 호출하여 실제 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-132">In this case IRow->GetColumns can be called again on the same column to retrieve the actual data.</span></span> <span data-ttu-id="7ecc6-133">이 예제는 IA64에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-133">This sample is not supported on IA64.</span></span>  
  
 <span data-ttu-id="7ecc6-134">이 예제에는 [Microsoft SQL Server 예제 및 커뮤니티 프로젝트(Microsoft SQL Server Samples and Community Projects)](https://go.microsoft.com/fwlink/?LinkID=85384) 홈 페이지에서 다운로드할 수 있는 AdventureWorks 예제 데이터베이스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-134">This sample requires the AdventureWorks sample database, which you can download from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.</span></span>  
  
 <span data-ttu-id="7ecc6-135">첫 번째([!INCLUDE[tsql](../../includes/tsql-md.md)]) 코드 목록은 예제에서 사용하는 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-135">The first ([!INCLUDE[tsql](../../includes/tsql-md.md)]) code listing creates a table used by the sample.</span></span>  
  
 <span data-ttu-id="7ecc6-136">ole32.lib oleaut32.lib를 사용하여 컴파일하고 두 번째(C++) 코드 목록을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-136">Compile with ole32.lib oleaut32.lib and execute the second (C++) code listing.</span></span> <span data-ttu-id="7ecc6-137">이 애플리케이션은 컴퓨터의 기본 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-137">This application connects to your computer's default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="7ecc6-138">일부 Windows 운영 체제에서는 (localhost) 또는 (local)을 해당 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이름으로 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-138">On some Windows operating systems, you will need to change (localhost) or (local) to the name of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="7ecc6-139">명명된 인스턴스에 연결하려면 연결 문자열을 L"(local)"에서 L"(local)\\\name"으로 변경합니다. 여기서 name은 명명된 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-139">To connect to a named instance, change the connection string from L"(local)" to L"(local)\\\name" , where name is the named instance.</span></span> <span data-ttu-id="7ecc6-140">기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express는 명명된 인스턴스에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-140">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express installs to a named instance.</span></span> <span data-ttu-id="7ecc6-141">INCLUDE 환경 변수에 sqlncli.h가 들어 있는 디렉터리를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-141">Make sure your INCLUDE environment variable includes the directory that contains sqlncli.h.</span></span>  
  
 <span data-ttu-id="7ecc6-142">세 번째([!INCLUDE[tsql](../../includes/tsql-md.md)]) 코드 목록은 예제에서 사용하는 테이블을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-142">The third ([!INCLUDE[tsql](../../includes/tsql-md.md)]) code listing deletes the table used by the sample.</span></span>  
  
```  
use AdventureWorks  
go  
  
if exists (select name from sysobjects where name = 'MyTable')  
     drop table MyTable  
go  
  
create table MyTable  
(  
     col1  int,  
     col2  varchar(50),  
     col3  char(50),  
     col4  datetime,  
     col5  float,  
     col6  money,  
     col7  sql_variant,  
     col8  binary(50),  
     col9  text,  
     col10 image  
)  
go  
insert into MyTable  
values  
(  
     10,  
     'abcdefghijklmnopqrstuvwxyz',  
     'ABCDEFGHIJKLMNOPQRSTUVWXYZ',  
     '11/1/1999 11:52 AM',  
     3.14,  
     99.95,  
     convert(nchar(50), N'AbCdEfGhIjKlMnOpQrStUvWxYz'),  
     0x123456789,  
     replicate('AAAAABBBBB', 500),  
     replicate(0x123456789, 500)  
)  
Go  
```  
  
```  
// compile with: ole32.lib oleaut32.lib  
#define DBINITCONSTANTS  
#define OLEDBVER 0x0250   // to include correct interfaces  
  
#include <stdio.h>  
#include <windows.h>  
#include <iostream>  
#include <oledb.h>  
#include <sqlncli.h>  
  
using namespace std;  
  
int InitializeAndEstablishConnection();  
HRESULT GetColumnSize(IRow* pUnkRow, ULONG iCol);  
ULONG PrintData(ULONG iCols, ULONG iStart, DBCOLUMNINFO* prgInfo, DBCOLUMNACCESS* prgColumns);  
HRESULT GetColumns(IRow* pUnkRow, ULONG iStart, ULONG iEnd);  
  
IDBInitialize*       pIDBInitialize     = NULL;  
IDBProperties*       pIDBProperties     = NULL;  
IDBCreateSession*    pIDBCreateSession  = NULL;  
IDBCreateCommand*    pIDBCreateCommand  = NULL;  
ICommandText*        pICommandText      = NULL;  
IRow   *             pIRow              = NULL;  
DBCOLUMNINFO*        pDBColumnInfo      = NULL;  
IAccessor*           pIAccessor         = NULL;  
DBPROP               InitProperties[4];  
DBPROPSET            rgInitPropSet[1];  
ULONG                i, j;  
HRESULT              hresult;  
DBROWCOUNT           cNumRows = 0;  
ULONG                lNumCols;  
WCHAR*               pStringsBuffer;  
DBBINDING*           pBindings;  
ULONG                ConsumerBufColOffset = 0;  
HACCESSOR            hAccessor;  
ULONG                lNumRowsRetrieved;  
HROW                 hRows[10];  
HROW*                pRows = &hRows[0];  
  
int main() {  
   ULONG iidx = 0;  
   WCHAR* wCmdString = OLESTR(" SELECT * FROM MyTable");  
  
   // Call a function to initialize and establish connection.   
   if (InitializeAndEstablishConnection() == -1) {  
      cout << "Failed to initialize and establish connection.\n";  
      // Insert your code for cleanup and error handling.  
      return -1;  
   }  
  
   // Create a session object.  
   if (FAILED(pIDBInitialize->QueryInterface (   
      IID_IDBCreateSession, (void**) &pIDBCreateSession))) {  
      cout << "Failed to obtain IDBCreateSession interface.\n";  
      // Insert your code for cleanup and error handling.  
      return -1;  
   }  
  
   if (FAILED(pIDBCreateSession->CreateSession( NULL, IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand))) {  
      cout << "pIDBCreateSession->CreateSession failed.\n";  
      // Insert your code for cleanup and error handling.  
      return -1;  
   }  
  
   // Access the ICommandText interface.  
   if (FAILED(pIDBCreateCommand->CreateCommand( NULL, IID_ICommandText, (IUnknown**) &pICommandText))) {  
      cout << "Failed to access ICommand interface.\n";  
      // Insert your code for cleanup and error handling.  
      return -1;  
   }  
  
   // Use SetCommandText() to specify the command text.  
   if (FAILED(pICommandText->SetCommandText(DBGUID_DBSQL, wCmdString))) {  
      cout << "Failed to set command text.\n";  
      // Insert your code for cleanup and error handling.  
      return -1;  
   }  
  
   // Fetch columns 1-5 and then 6-10 and display the contents  
   if (FAILED(hresult = pICommandText->Execute(NULL, IID_IRow, NULL, &cNumRows, (IUnknown **) &pIRow))) {  
      cout << "Failed to execute command.\n";  
      // Insert your code for cleanup and error handling.  
      return -1;  
   }  
  
   hresult = GetColumns(pIRow, 1, 5);  
   hresult = GetColumns(pIRow, 6, 10);  
  
   hresult = pIRow->Release();  
  
   // Execute the command.  
   if (FAILED(hresult = pICommandText->Execute(NULL, IID_IRow, NULL, &cNumRows, (IUnknown **) &pIRow))) {  
      cout << "Failed to execute command.\n";  
      // Insert your code for cleanup and error handling.  
      return -1;  
   }  
  
   // Get columns  
   for ( iidx = 1 ; iidx <= 10 ; iidx++ ) {  
      if (FAILED(hresult = GetColumnSize(pIRow, iidx))) {  
         cout << "Failed to get column size.\n";  
         // Insert your code for cleanup and error handling.     
         return -1;  
      }  
  
      hresult = GetColumns(pIRow, iidx, iidx);  
   }  
  
   pIRow->Release();  
  
   // Release memory.  
   pICommandText->Release();  
   pIDBCreateCommand->Release();  
   pIDBCreateSession->Release();  
  
   if (FAILED(pIDBInitialize->Uninitialize())) {  
      // Uninitialize not required, but fails if an interface has not been released.  Can be used for debugging.  
      cout << "Problem uninitializing.\n";  
   }  
  
   pIDBInitialize->Release();  
  
   // Release the COM library.  
   CoUninitialize();  
  
   return 0;  
};  
  
//--------------------------------------------------------------------  
BOOL InitColumn(DBCOLUMNACCESS* pCol, DBCOLUMNINFO* pInfo) {  
   // If text or image column is being read,in which case the max  possible length of a value is   
   // the column is hugh,we will limit that size to 512 bytes (for illustration purposes).  
   DBLENGTH ulSize = (pInfo->ulColumnSize < 0x7fffffff) ? pInfo->ulColumnSize : 512;  
  
   // Verify dta buffer is large enough.  
   if (pCol->cbMaxLen < (ulSize + 1)) {  
      if (pCol->pData) {  
         delete [] pCol->pData;  
         pCol->pData = NULL;  
      }  
  
      // Allocate data buffer  
      void * p = pCol->pData = new WCHAR[ulSize + 1];  
      if (!(p /* pCol->pData = new WCHAR[ulSize + 1] */ ))  
         return FALSE;  
  
      // set the max length of caller-initialized memory.  
      pCol->cbMaxLen = sizeof(WCHAR) * (ulSize + 1);  
  
      // In the above 2 steps, pData is pointing to memory (it is not NULL) and cbMaxLen has a value   
      // (not 0), so next call to IRow->GetData() will read the data from the column.  
   }  
  
   // Clear memory buffer  
   ZeroMemory((void*) pCol->pData, pCol->cbMaxLen);  
  
   // Set properties.  
   pCol->wType = DBTYPE_WSTR;  
   pCol->columnid = pInfo->columnid;  
   pCol->cbDataLen = 0;  
   pCol->dwStatus = 0;  
   pCol->dwReserved = 0;  
   pCol->bPrecision = 0;  
   pCol->bScale = 0;  
   return TRUE;  
}  
  
//--------------------------------------------------------------------  
HRESULT GetColumns(IRow* pUnkRow, ULONG iStart, ULONG iEnd) {  
// Start and end are same. Thus, get only one column.  
   HRESULT hr;  
   ULONG iidx;   // loop counter  
   DBORDINAL cColumns;   // Count of columns  
   ULONG cUserCols;   // Count of user columns  
  
   DBCOLUMNINFO* prgInfo;   // Column of info. array  
   OLECHAR* pColNames;   // Array of column names  
  
   DBCOLUMNACCESS* prgColumns;   // Ptr to column access structures array  
   DBCOLUMNINFO* pCurrInfo;  
   DBCOLUMNACCESS* pCurrCol;  
  
   IColumnsInfo* pIColumnsInfo = NULL;  
  
   // Initialize  
   cColumns = 0;  
   prgInfo = NULL;  
   pColNames = NULL;  
   prgColumns = NULL;  
  
   printf("Retrieving data\n");  
  
   // Get column info to build column access array  
   hr = pUnkRow->QueryInterface(IID_IColumnsInfo, (void**)&pIColumnsInfo);  
   if (FAILED(hr))  
      goto CLEANUP;  
   hr = pIColumnsInfo->GetColumnInfo(&cColumns, &prgInfo, &pColNames);  
   if (FAILED(hr))  
      goto CLEANUP;  
  
   printf("In GetColumns(), Columns= %d\n", cColumns);  
  
   // Determine no. of columns to retrieve. Since iEnd and iStart is same, this is redundent step.    
   // cUserCols will always be 1.  
   cUserCols = iEnd - iStart + 1;   
  
   // Walk list of columns and setup a DBCOLUMNACCESS structure  
   if (!(prgColumns= new DBCOLUMNACCESS[cUserCols])) {   // cUserCols is only 1  
      hr = E_FAIL;  
      goto CLEANUP;  
   }  
  
   ZeroMemory((void*) prgColumns, sizeof(DBCOLUMNACCESS) * cUserCols);  
  
   for ( iidx = 0 ; iidx < cUserCols ; iidx++ ) {  
      pCurrInfo = prgInfo + iidx + iStart - 1;  
      pCurrCol = prgColumns + iidx;  
  
      // Here the values of DBCOLUMNACCESS elements is set (pData and cbMaxLen)Thus IRow->GetColumns()   
      // will return actual data.  
      if (InitColumn(pCurrCol, pCurrInfo) == FALSE)  
         goto CLEANUP;  
   }  
  
   hr = pUnkRow->GetColumns(cUserCols, prgColumns);   // cUserCols = 1  
   if (FAILED(hr))  
      printf("Error occured\n");  
  
   // Show data.  
   PrintData(cUserCols, iStart, prgInfo, prgColumns);  
  
CLEANUP:  
   if (pIColumnsInfo)  
      pIColumnsInfo->Release();  
   if (prgColumns)  
      delete [] prgColumns;  
  
   return hr;  
}  
  
// This function returns the actual width of the data in the column (not the columnwidth in   
// DBCOLUMNFO structure which is the width of the column)  
HRESULT GetColumnSize(IRow* pUnkRow, ULONG iCol) {  
   HRESULT        hr = NOERROR;  
   DBORDINAL      cColumns = 0;   // Count the columns  
   DBCOLUMNINFO*  prgInfo;   // Column info array  
   OLECHAR*       pColNames;  
   DBCOLUMNACCESS column;  
   DBCOLUMNINFO*  pCurrInfo;  
   IColumnsInfo*  pIColumnsInfo = NULL;  
  
   // Initialize  
   prgInfo = NULL;  
   pColNames = NULL;  
  
   printf("Checking column size\n");  
  
   // Get column info to build column access array  
   hr = pUnkRow->QueryInterface(IID_IColumnsInfo, (void**) &pIColumnsInfo);  
   if (FAILED(hr))  
      goto CLEANUP;  
  
   hr = pIColumnsInfo->GetColumnInfo(&cColumns, &prgInfo, &pColNames);  
   if (FAILED(hr))  
      goto CLEANUP;  
   printf("Value of cColumns is %d\n", cColumns);  
  
   // Setup a DBCOLUMNACCESS structure: Here pData is set to NULL and cbMaxLen is set to 0. Thus   
   // IRow->GetColumns() returns only the actual column length in cbDataLen member of DBCOLUMNACCESS   
   // structure. In this case you can call IRow->GetColumns() again for the same  column to retrieve   
   // actual data in the second call.  
   ZeroMemory((void*) &column, sizeof(DBCOLUMNACCESS));  
   column.pData = NULL;  
  
   pCurrInfo = prgInfo + iCol - 1;  
  
   // Get the column id in DBCOLUMNACCESS structure. It is then used in GetColumn().  
   column.columnid = pCurrInfo->columnid;   
  
   printf("column.columnid value is %d\n", column.columnid);  
   // We know which column to get. The column.columnid gives the column no.  
   hr = pUnkRow->GetColumns(1, &column);   
   if (FAILED(hr))  
      printf("Errors occured\n");  
  
   // Show data  
   PrintData(1, iCol, prgInfo, &column);  
  
CLEANUP:  
   if (pIColumnsInfo)  
      pIColumnsInfo->Release();  
   return hr;  
}  
  
BOOL GetStatus(DWORD dwStatus, WCHAR* pwszStatus) {  
   switch (dwStatus) {  
   case DBSTATUS_S_OK:  
      wcscpy_s(pwszStatus, 255, L"DBSTATUS_S_OK");  
      break;  
   case DBSTATUS_E_UNAVAILABLE:  
      wcscpy_s(pwszStatus, 255, L"DBSTATUS_E_UNAVAILABLE");  
      break;  
   case DBSTATUS_S_TRUNCATED:  
      wcscpy_s(pwszStatus, 255, L"DBSTATUS_S_TRUNCATED");  
      break;  
   }  
   return TRUE;  
}  
  
ULONG PrintData(ULONG iCols, ULONG iStart, DBCOLUMNINFO* prgInfo, DBCOLUMNACCESS* prgColumns) {  
   WCHAR wszStatus[255];  
   DBCOLUMNINFO* pCurrInfo;  
   DBCOLUMNACCESS* pCurrCol;  
   ULONG iidx;  
  
   printf("No. Name       Status     Length  Max  Data\n");  
  
   for ( iidx = 0 ; iidx < iCols ; iidx++ ) {  
      pCurrInfo = prgInfo + iidx + iStart - 1;  
      pCurrCol = prgColumns + iidx;  
  
      GetStatus(pCurrCol->dwStatus, wszStatus);   
      // was the data successfully retrieved?  
      wprintf(L"%-3d %-*s %-20s %-3d %-3d %-20s\n", iStart+iidx,   
                                                    10,   
                                                    pCurrInfo->pwszName,   
                                                    wszStatus,  
                                                    pCurrCol->cbDataLen,  
                                                    pCurrCol->cbMaxLen,  
                                                    (WCHAR*) pCurrCol->pData);  
   }  
  
   wprintf(L"\n");  
   return iidx;  
}  
  
int InitializeAndEstablishConnection() {      
   // Initialize the COM library.  
   CoInitialize(NULL);  
  
   // Obtain access to the SQLNCLI provider.  
   hresult = CoCreateInstance(CLSID_SQLNCLI11,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDBInitialize,  
                              (void **) &pIDBInitialize);  
  
   if (FAILED(hresult)) {  
      printf("Failed to get IDBInitialize interface.\n");  
      // Insert your code for cleanup and error handling.  
      return -1;  
   }  
  
   // Initialize the property values needed to establish the connection.  
   for ( i = 0 ; i < 4 ; i++ )   
      VariantInit(&InitProperties[i].vValue);  
  
   // Server name.  
   InitProperties[0].dwPropertyID  = DBPROP_INIT_DATASOURCE;  
   InitProperties[0].vValue.vt     = VT_BSTR;  
  
   InitProperties[0].vValue.bstrVal= SysAllocString(L"(local)");  
   InitProperties[0].dwOptions     = DBPROPOPTIONS_REQUIRED;  
   InitProperties[0].colid         = DB_NULLID;  
  
   // Database.  
   InitProperties[1].dwPropertyID  = DBPROP_INIT_CATALOG;  
   InitProperties[1].vValue.vt     = VT_BSTR;  
   InitProperties[1].vValue.bstrVal= SysAllocString(L"AdventureWorks");  
   InitProperties[1].dwOptions     = DBPROPOPTIONS_REQUIRED;  
   InitProperties[1].colid         = DB_NULLID;  
  
   InitProperties[2].dwPropertyID  = DBPROP_AUTH_INTEGRATED;  
   InitProperties[2].vValue.vt     = VT_BSTR;  
   InitProperties[2].vValue.bstrVal= SysAllocString(L"SSPI");  
   InitProperties[2].dwOptions     = DBPROPOPTIONS_REQUIRED;  
   InitProperties[2].colid         = DB_NULLID;  
  
   // Now that the properties are set, construct the DBPROPSET structure (rgInitPropSet). The DBPROPSET   
   // structure is used to pass an array of DBPROP structures (InitProperties) to the SetProperties method.  
   rgInitPropSet[0].guidPropertySet= DBPROPSET_DBINIT;  
   rgInitPropSet[0].cProperties    = 4;  
   rgInitPropSet[0].rgProperties   = InitProperties;  
  
   // Set initialization properties.  
   hresult = pIDBInitialize->QueryInterface(IID_IDBProperties, (void **)&pIDBProperties);  
   if (FAILED(hresult)) {  
      cout << "Failed to get IDBProperties interface.\n";  
      // Insert your code for cleanup and error handling.  
      return -1;  
   }  
  
   hresult = pIDBProperties->SetProperties(1, rgInitPropSet);   
   if (FAILED(hresult)) {  
      cout << "Failed to set initialization properties.\n";  
      // Insert your code for cleanup and error handling.  
      return -1;  
   }  
  
   pIDBProperties->Release();  
  
   // Now establish the connection to the data source.  
   if (FAILED(pIDBInitialize->Initialize()))  
      cout << "Problem establishing connection to the data source.\n";  
  
   return 0;  
}  
```  
  
```  
use AdventureWorks  
go  
  
if exists (select name from sysobjects where name = 'MyTable')  
     drop table MyTable  
go  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ecc6-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ecc6-143">See Also</span></span>  
 [<span data-ttu-id="7ecc6-144">OLE DB 방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="7ecc6-144">OLE DB How-to Topics</span></span>](ole-db-how-to-topics.md)  
  
  
