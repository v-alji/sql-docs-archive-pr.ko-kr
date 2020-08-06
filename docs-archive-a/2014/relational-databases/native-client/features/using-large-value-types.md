---
title: 큰 값 형식 사용 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- large value data types
- SQLNCLI, large value types
- SQL Server Native Client, large value types
- data access [SQL Server Native Client], large value types
- SQL Server Native Client ODBC driver, large value data types
- SQL Server Native Client OLE DB provider, large value data types
ms.assetid: 4a58b05c-8848-44bb-8704-f9f409efa5af
author: rothja
ms.author: jroth
ms.openlocfilehash: 8a2e93ee36eb4bfadf18c5b78f552380d1c94266
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653318"
---
# <a name="using-large-value-types"></a><span data-ttu-id="c0ab1-102">큰 값 형식 사용</span><span class="sxs-lookup"><span data-stu-id="c0ab1-102">Using Large Value Types</span></span>
  <span data-ttu-id="c0ab1-103">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 이전에 큰 값 데이터 형식으로 작업하려면 특별한 처리가 필요했습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-103">Before [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], working with large value data types required special handling.</span></span> <span data-ttu-id="c0ab1-104">큰 값 데이터 형식은 최대 행 크기가 8KB를 초과하는 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-104">Large value data types are those that exceed the maximum row size of 8 KB.</span></span> [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]<span data-ttu-id="c0ab1-105">에서는 **varchar**, **nvarchar** 및 **varbinary** 데이터 형식에 대 한 **max** 지정자를 도입 하 여 값을 2 ^ 31-1 바이트로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-105">introduced a **max** specifier for **varchar**, **nvarchar** and **varbinary** data types to allow storage of values as large as 2^31 -1 bytes.</span></span> <span data-ttu-id="c0ab1-106">테이블 열 및 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 변수는 **varchar (max)**, **nvarchar (max)** 또는 **varbinary (max)** 데이터 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-106">Table columns and [!INCLUDE[tsql](../../../includes/tsql-md.md)] variables may specify **varchar(max)**, **nvarchar(max)** or **varbinary(max)** data types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c0ab1-107">큰 값 데이터 형식은 1-8KB의 최대 크기를 가질 수 있거나 무제한으로 지정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-107">Large value data types can have a maximum size between 1 and 8 KB, or they can be specified as unlimited.</span></span>  
  
 <span data-ttu-id="c0ab1-108">이전에는 **text**, **ntext** 및 **image**와 같은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식만 이러한 길이에 도달할 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-108">Previously, only [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types such as **text**, **ntext** and **image** could attain such lengths.</span></span> <span data-ttu-id="c0ab1-109">**Varchar**, **nvarchar** 및 **varbinary** 의 **max** 지정자는 이러한 데이터 형식을 중복 했습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-109">The **max** specifier for **varchar**, **nvarchar** and **varbinary** made these data types redundant.</span></span> <span data-ttu-id="c0ab1-110">그러나 긴 데이터 형식은 여전히 사용할 수 있으므로, OLE DB 및 ODBC 데이터 액세스 구성 요소에 대한 대부분의 인터페이스는 동일하게 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-110">However, because long data types are still available, most of the interfaces to the OLE DB and ODBC data access components will remain the same.</span></span> <span data-ttu-id="c0ab1-111">이전 릴리스와의 호환성을 위해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native  Client  OLE  DB  공급자의 DBCOLUMNFLAGS_ISLONG  플래그와 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native  Client  ODBC  드라이버의 SQL_LONGVARCHAR는 계속 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-111">For backward compatibility with prior releases, the DBCOLUMNFLAGS_ISLONG flag in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider, and the SQL_LONGVARCHAR in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver remain in use.</span></span> <span data-ttu-id="c0ab1-112">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 이상 버전 대해 작성된 공급자와 드라이버는 무제한 최대 길이로 설정된 경우 새 형식에 대해 계속 이러한 용어를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-112">Providers and drivers written against [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] and later continue to use these terms for the new types when set to unlimited maximum length.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c0ab1-113">저장 프로시저, 함수 반환 형식 또는 [CAST 및 CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql) 함수의 입력 및 출력 매개 변수 형식으로 **varchar(max)**, **nvarchar(max)** 및 **varbinary(max)** 데이터 형식을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-113">You can also specify **varchar(max)**, **nvarchar(max)**, and **varbinary(max)** data types as input and output parameter types of stored procedures, function return types, or in [CAST and CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql) functions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c0ab1-114">데이터를 복제 하는 경우 [최대 텍스트 복제 크기 서버 구성 옵션](../../../database-engine/configure-windows/configure-the-max-text-repl-size-server-configuration-option.md) 을-1로 구성 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-114">If replicating data you may need to configure the [max text repl size server configuration option](../../../database-engine/configure-windows/configure-the-max-text-repl-size-server-configuration-option.md) to -1.</span></span>  
  
## <a name="sql-server-native-client-ole-db-provider"></a><span data-ttu-id="c0ab1-115">SQL Server Native Client OLE DB 공급자</span><span class="sxs-lookup"><span data-stu-id="c0ab1-115">SQL Server Native Client OLE DB Provider</span></span>  
 <span data-ttu-id="c0ab1-116">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 **varchar (max)**, **varbinary (max)** 및 **nvarchar (max)** 형식을 각각 DBTYPE_STR, DBTYPE_BYTES 및 DBTYPE_WSTR으로 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-116">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **varchar(max)**, **varbinary(max)**, and **nvarchar(max)** types as DBTYPE_STR, DBTYPE_BYTES, and DBTYPE_WSTR, respectively.</span></span>  
  
 <span data-ttu-id="c0ab1-117">**max** 크기가 무제한으로 설정된 열의 **varchar(max)**, **varbinary(max)** 및 **nvarchar(max)** 데이터 형식은 열 데이터 형식을 반환하는 핵심 OLE DB 스키마 행 집합과 인터페이스를 통해 ISLONG으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-117">The data types **varchar(max)**, **varbinary(max)**, and **nvarchar(max)** in columns with the **max** size set to unlimited are represented as an ISLONG through the core OLE DB schema rowsets and interfaces returning column data types.</span></span>  
  
 <span data-ttu-id="c0ab1-118">명령 개체의 **IAccessor** 구현이 DBTYPE_IUNKNOWN로 바인딩을 허용 하도록 변경 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-118">The command object's **IAccessor** implementation has been changed to allow binding as DBTYPE_IUNKNOWN.</span></span> <span data-ttu-id="c0ab1-119">소비자가 DBTYPE_IUNKNOWN을 지정하고 *pObject*를 Null로 설정하면 소비자가 출력 변수에서 **varchar(max)**, **nvarchar(max)** 또는 **varbinary(max)** 데이터를 스트리밍할 수 있도록 공급자가 **ISequentialStream** 인터페이스를 소비자에게 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-119">If the consumer specifies DBTYPE_IUNKNOWN and sets *pObject* to null, the provider will return the **ISequentialStream** interface to the consumer so that the consumer can stream **varchar(max)**, **nvarchar(max)**, or **varbinary(max)** data out of output variables.</span></span>  
  
 <span data-ttu-id="c0ab1-120">스트리밍된 출력 매개 변수 값은 결과 행 뒤에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-120">Streamed output parameter values are returned after any result rows.</span></span> <span data-ttu-id="c0ab1-121">애플리케이션이 반환된 모든 출력 매개 변수 값을 사용하지 않고 **IMultipleResults::GetResult**를 호출하여 다음 결과 집합으로 이동하면 DB_E_OBJECTOPEN이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-121">If the application attempts to move on to the next result set by calling **IMultipleResults::GetResult** without consuming all the returned output parameter values, DB_E_OBJECTOPEN will be returned.</span></span>  
  
 <span data-ttu-id="c0ab1-122">스트리밍을 지원 하기 위해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 가변 길이 매개 변수를 순차적인 순서로 액세스 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-122">In order to support streaming, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider requires variable length parameters to be accessed in sequential order.</span></span> <span data-ttu-id="c0ab1-123">즉, **varchar(max)**, **nvarchchar(max)** 또는 **varbinary(max)** 열이나 출력 매개 변수가 DBTYPE_IUNKNOWN에 바인딩되어 있을 때마다 DBPROP_ACCESSORDER를 DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS 또는 DBPROPVAL_AO_SEQUENTIAL로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-123">This means that DBPROP_ACCESSORDER must be set to either DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS or DBPROPVAL_AO_SEQUENTIAL whenever **varchar(max)**, **nvarchchar(max)**, or **varbinary(max)** columns or output parameters are bound to DBTYPE_IUNKNOWN.</span></span> <span data-ttu-id="c0ab1-124">이 액세스 순서 제한을 따르지 않으면 DBSTATUS_E_UNAVAILABLE로 인해 **IRowset::GetData**에 대한 호출이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-124">Calls to **IRowset::GetData** will fail with DBSTATUS_E_UNAVAILABLE if this access order restriction is not adhered to.</span></span> <span data-ttu-id="c0ab1-125">DBTYPE_IUNKNOWN을 사용한 출력 바인딩이 없을 경우에는 이 제한이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-125">This restriction does not apply when there are no output bindings using DBTYPE_IUNKNOWN.</span></span>  
  
 <span data-ttu-id="c0ab1-126">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native client OLE DB 공급자는 또한 대량 값 데이터 형식에 대 한 DBTYPE_IUNKNOWN로 출력 매개 변수를 바인딩할 수 있습니다 .이 경우 저장 프로시저에서 클라이언트에 DBTYPE_IUNKNOWN 표시 되는 반환 값으로 많은 값 형식을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-126">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider also supports binding output parameters as DBTYPE_IUNKNOWN for large value data types to facilitate scenarios where a stored procedure returns large value types as return values that are exposed as DBTYPE_IUNKNOWN to the client.</span></span>  
  
 <span data-ttu-id="c0ab1-127">이러한 형식으로 작업하기 위해 애플리케이션에는 다음 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-127">To work with these types, an application has the following options:</span></span>  
  
-   <span data-ttu-id="c0ab1-128">열의 기본 형식과 지원되는 바인딩이 있는 형식으로 바인딩합니다.  예를 들어 nvarchar(max)의 경우 nvarchar에 바인딩될 수 있는 형식으로 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-128">Bind as a type that has supported bindings with the base type of the column (eg for nvarchar(max), bind as a type that can be bound to nvarchar).</span></span> <span data-ttu-id="c0ab1-129">버퍼가 충분히 크지 않으면 이제 더 큰 값을 사용할 수 있어도 정확하게 기본 형식을 기준으로 잘림이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-129">If the buffer is not big enough truncation will occur, exactly as for the base type, albeit that larger values are now available.</span></span>  
  
-   <span data-ttu-id="c0ab1-130">열의 기본 형식과 지원되는 변환이 있는 형식으로 바인딩하고 DBTYPE_BYREF도 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-130">Bind as a type that has supported conversions with the base type of the column and also specify DBTYPE_BYREF.</span></span>  
  
-   <span data-ttu-id="c0ab1-131">DBTYPE_IUNKNOWN으로 바인딩하고 스트리밍을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-131">Bind as DBTYPE_IUNKNOWN and use streaming.</span></span>  
  
 <span data-ttu-id="c0ab1-132">열의 최대 크기를 보고할 때 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 다음을 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-132">When reporting the maximum size of a column, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider will report:</span></span>  
  
-   <span data-ttu-id="c0ab1-133">예를 들어 **varchar (** 2000 **)** 열에 대해 정의 된 최대 크기는 2000입니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-133">The defined maximum size, which for example, is 2000 for a **varchar(** 2000 **)** column, or</span></span>  
  
-   <span data-ttu-id="c0ab1-134">값 "무제한". **varchar(max)** 열의 경우 0과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-134">The value "unlimited" which in the case of a **varchar(max)** column equals ~0.</span></span> <span data-ttu-id="c0ab1-135">이 값은 DBCOLUMN_COLUMNSIZE 메타데이터 속성에 대해 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-135">This value is set for the DBCOLUMN_COLUMNSIZE metadata property.</span></span>  
  
 <span data-ttu-id="c0ab1-136">표준 변환 규칙이 **varchar(max)** 열에 적용되므로 **varchar(** 2000 **)** 열에 유효한 모든 변환은 **varchar(max)** 열에도 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-136">The standard conversion rules will apply to a **varchar(max)** column, meaning that any conversion that is valid for a **varchar(** 2000 **)** column will also be valid for a **varchar(max)** column.</span></span> <span data-ttu-id="c0ab1-137">**nvarchar(max)** 및 **varbinary(max)** 열의 경우도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-137">The same is true for **nvarchar(max)** and **varbinary(max)** columns.</span></span>  
  
 <span data-ttu-id="c0ab1-138">큰 값 형식을 검색할 때 가장 효과적인 방법은 DBTYPE_IUNKNOWN으로 바인딩하고 행 집합 속성 DBPROP_ACCESSORDER를 DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS로 설정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-138">When retrieving large value types, the most efficient approach is to bind as DBTYPE_IUNKNOWN and set the rowset property DBPROP_ACCESSORDER to DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS.</span></span> <span data-ttu-id="c0ab1-139">이렇게 하면 다음 예와 같이 값이 중간 버퍼링 없이 네트워크에서 직접 스트리밍됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-139">This will cause the value to be streamed directly from the network with no intermediate buffering, as in the following example:</span></span>  
  
```  
#define UNICODE  
#define _UNICODE  
#define DBINITCONSTANTS  
#define INITGUID  
#define OLEDBVER 0x0250  // To include the correct interfaces.  
  
#include <stdio.h>  
#include <tchar.h>  
#include <stddef.h>  
#include <iostream>  
  
using std::cout;  
using std::endl;  
  
#include <windows.h>  
  
#include <oledb.h>  
#include "sqlncli.h"  
#include <oledberr.h>  
  
#define CHKHR_GOTO(hr, errMsg, Label) \  
   if (FAILED(hr)) \  
   { \  
      cout << errMsg << endl; \  
      goto Label; \  
   }  
  
#define MAX_COL_SIZE 8000  
  
// ROUNDUP on all platforms pointers must be aligned properly.  
#define ROUNDUP_AMOUNT 8  
#define ROUNDUP_(size,amount) (((ULONG)(size)+((amount)-1))&~((amount)-1))  
#define ROUNDUP(size) ROUNDUP_(size, ROUNDUP_AMOUNT)  
  
HRESULT InitializeAndEstablishConnection(IDBInitialize** ppIDBInitialize);  
void UnInitializeConnection(IDBInitialize* pIDBInitialize);  
HRESULT CreateAndSetCommand(IDBInitialize* pIDBInitialize, ICommandText** ppICommandText);  
HRESULT ProcessResultSet(IRowset* pIRowset);  
  
void DisplayTime()  
{  
   SYSTEMTIME st;  
   GetSystemTime(&st);  
   cout<< st.wHour << ":" << st.wMinute << ":" << st.wSecond << "." << st.wMilliseconds << endl;  
}  
  
void main()  
{  
   HRESULT hr;  
   IDBInitialize* pIDBInitialize = NULL;  
   ICommandText* pICommandText = NULL;  
   IMultipleResults* pIMultipleResults = NULL;  
   IRowset* pIRowset = NULL;  
  
   hr = InitializeAndEstablishConnection(&pIDBInitialize);  
   CHKHR_GOTO(hr, L"Failed to establish connection.", _ExitMain);  
  
   hr = CreateAndSetCommand(pIDBInitialize, &pICommandText);  
   CHKHR_GOTO(hr, L"Failed to set up command object.", _ExitMain);  
  
   DisplayTime();  
  
   hr = pICommandText->Execute(NULL,   
      IID_IMultipleResults,   
      NULL,   
      NULL,   
     (IUnknown **) &pIMultipleResults);  
  
   CHKHR_GOTO(hr, L"Failed to execute command.", _ExitMain);  
  
   while (1)  
   {  
      hr = pIMultipleResults->GetResult(  
         NULL,   
         DBRESULTFLAG_DEFAULT,   
         IID_IRowset,   
         NULL,   
         (IUnknown**)&pIRowset);  
  
   CHKHR_GOTO(hr, L"Failed to obtain a results from MR object.", _ExitMain);  
  
   if (hr == DB_S_NORESULT)  
      break;  
  
      if (pIRowset)  
      {  
         hr = ProcessResultSet(pIRowset);   
         CHKHR_GOTO(hr, L"Failed to process the current Rowset.", _ExitMain);  
  
         pIRowset->Release();  
         pIRowset = NULL;  
      }  
   }  
  
   DisplayTime();  
  
_ExitMain:  
  
   if (pIRowset)  
   {  
      pIRowset->Release();  
      pIRowset = NULL;  
   }  
  
   if (pIMultipleResults)  
   {  
      pIMultipleResults->Release();  
      pIMultipleResults = NULL;  
   }  
  
   if (pICommandText)  
   {  
      pICommandText->Release();  
      pICommandText = NULL;  
   }  
  
   UnInitializeConnection(pIDBInitialize);  
   return;  
};  
  
HRESULT InitializeAndEstablishConnection(IDBInitialize** ppIDBInitialize)  
{  
   HRESULT hr;  
   IDBInitialize* pIDBInitialize = NULL;  
   IDBProperties* pIDBProperties = NULL;  
  
   const int NUM_DBINIT_PROPS = 3;  
   const wchar_t* const g_wszServer = L".";  
   const wchar_t* const g_wszCatalog = L"AdventureWorks";  
   const wchar_t* const g_wszSecurity = L"SSPI";  
  
   DBPROPSET rgdbPropSetInit[1];  
   DBPROP rgdbPropInit [NUM_DBINIT_PROPS];  
  
   *ppIDBInitialize = NULL;  
   hr = CoInitialize(NULL);  
   CHKHR_GOTO(hr, L"Failed to initialize COM.", _ExitInitialize);  
  
   hr = CoCreateInstance(CLSID_SQLNCLI11,   
      NULL,   
      CLSCTX_INPROC_SERVER,  
      IID_IDBInitialize,   
      (void**)&pIDBInitialize);  
  
   CHKHR_GOTO(hr, L"Failed to create SQLNCLI11 DataSource object.", _ExitInitialize);  
  
   for(int idxProp = 0; idxProp < NUM_DBINIT_PROPS; idxProp++)   
   {  
      VariantInit(&rgdbPropInit[idxProp].vValue);  
   }  
  
   rgdbPropInit[0].dwPropertyID = DBPROP_INIT_DATASOURCE;  
   rgdbPropInit[0].vValue.vt = VT_BSTR;  
   rgdbPropInit[0].vValue.bstrVal= SysAllocString(g_wszServer);  
   rgdbPropInit[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
   rgdbPropInit[0].colid = DB_NULLID;  
  
   if (rgdbPropInit[0].vValue.bstrVal == NULL)  
   {  
      hr = E_OUTOFMEMORY;  
      goto _ExitInitialize;  
   }  
  
   rgdbPropInit[1].dwPropertyID = DBPROP_INIT_CATALOG;  
   rgdbPropInit[1].vValue.vt = VT_BSTR;  
   rgdbPropInit[1].vValue.bstrVal= SysAllocString(g_wszCatalog);  
   rgdbPropInit[1].dwOptions = DBPROPOPTIONS_REQUIRED;  
   rgdbPropInit[1].colid = DB_NULLID;  
  
   if (rgdbPropInit[1].vValue.bstrVal == NULL)  
   {  
      hr = E_OUTOFMEMORY;  
      goto _ExitInitialize;  
   }  
  
   rgdbPropInit[2].dwPropertyID = DBPROP_AUTH_INTEGRATED;  
   rgdbPropInit[2].vValue.vt = VT_BSTR;  
   rgdbPropInit[2].vValue.bstrVal= SysAllocString(g_wszSecurity);  
   rgdbPropInit[2].dwOptions = DBPROPOPTIONS_REQUIRED;  
   rgdbPropInit[2].colid = DB_NULLID;  
  
   if (rgdbPropInit[2].vValue.bstrVal == NULL)  
   {  
      hr = E_OUTOFMEMORY;  
      goto _ExitInitialize;  
   }  
  
   rgdbPropSetInit[0].guidPropertySet = DBPROPSET_DBINIT;  
   rgdbPropSetInit[0].cProperties = NUM_DBINIT_PROPS;  
   rgdbPropSetInit[0].rgProperties = rgdbPropInit;  
  
   hr = pIDBInitialize->QueryInterface(IID_IDBProperties, (void **)&pIDBProperties);  
   CHKHR_GOTO(hr, L"Failed to QI DataSource object for IDBProperties.", _ExitInitialize);  
  
   hr = pIDBProperties->SetProperties(1, rgdbPropSetInit);   
   CHKHR_GOTO(hr, L"Failed to set DataSource object Properties.", _ExitInitialize);  
  
   pIDBProperties->Release();  
   pIDBProperties = NULL;  
  
   hr = pIDBInitialize->Initialize();  
   CHKHR_GOTO(hr, L"Failed to establish connection with the server.", _ExitInitialize);  
  
_ExitInitialize:  
  
   if (pIDBProperties)  
   {  
      pIDBProperties->Release();  
      pIDBProperties = NULL;  
   }  
  
   if (FAILED(hr))  
   {  
      if (pIDBInitialize)  
      {  
         pIDBInitialize->Release();  
         pIDBInitialize = NULL;  
      }  
   }  
  
   *ppIDBInitialize = pIDBInitialize;  
   return hr;  
}  
  
void UnInitializeConnection(IDBInitialize* pIDBInitialize)  
{  
   if (pIDBInitialize)  
   {  
      pIDBInitialize->Uninitialize();  
      pIDBInitialize->Release();  
      pIDBInitialize = NULL;  
   }  
   CoUninitialize();  
}  
  
HRESULT CreateAndSetCommand(IDBInitialize* pIDBInitialize, ICommandText** ppICommandText)  
{  
   HRESULT hr;  
   IDBCreateSession* pIDBCreateSession = NULL;  
   IDBCreateCommand* pIDBCreateCommand = NULL;  
   ICommandText* pICommandText = NULL;  
   ICommandProperties* pICommandProperties = NULL;  
   DBPROPSET rgCmdPropSet[1];  
   DBPROP rgCmdProperties[1];  
  
const wchar_t* const g_wCmdString = L"declare @x xml, @y nvarchar(max); select @x = (SELECT * FROM Sales.SalesOrderHeader FOR XML AUTO); select @x;";  
  
   *ppICommandText = NULL;  
  
   if (!pIDBInitialize)  
   {  
      hr = E_FAIL;  
      goto _ExitCreateAndSetCommand;  
   }  
  
   hr = pIDBInitialize->QueryInterface(IID_IDBCreateSession, (void**) &pIDBCreateSession);  
   CHKHR_GOTO(hr, L"Failed to obtain IDBCreateSession interface from DSO.", _ExitCreateAndSetCommand);  
  
   hr = pIDBCreateSession->CreateSession(  
      NULL,   
      IID_IDBCreateCommand,   
      (IUnknown**) &pIDBCreateCommand);  
  
   CHKHR_GOTO(hr, L"Failed to Create a Session for command execution.", _ExitCreateAndSetCommand);  
  
   hr = pIDBCreateCommand->CreateCommand(  
      NULL,   
      IID_ICommandText,   
      (IUnknown**)&pICommandText);  
  
   CHKHR_GOTO(hr, L"Failed to Create a Command object.", _ExitCreateAndSetCommand);  
  
   hr = pICommandText->SetCommandText(DBGUID_DBSQL, g_wCmdString);  
   CHKHR_GOTO(hr, L"Failed to Set Command Text.", _ExitCreateAndSetCommand);  
  
   hr = pICommandText->QueryInterface(IID_ICommandProperties, (void**) &pICommandProperties);  
   CHKHR_GOTO(hr, L"Failed to obtain ICommandProperties interface from the command object.", _ExitCreateAndSetCommand);  
  
   rgCmdProperties[0].dwPropertyID = DBPROP_ACCESSORDER;  
   rgCmdProperties[0].vValue.vt = VT_I4;  
   rgCmdProperties[0].vValue.lVal = DBPROPVAL_AO_SEQUENTIAL;  
   rgCmdProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
   rgCmdProperties[0].colid = DB_NULLID;  
  
   rgCmdPropSet[0].guidPropertySet = DBPROPSET_ROWSET;  
   rgCmdPropSet[0].cProperties = 1;  
   rgCmdPropSet[0].rgProperties = rgCmdProperties;  
  
   hr = pICommandProperties->SetProperties(1, rgCmdPropSet);   
   CHKHR_GOTO(hr, L"Failed to Set Command object Properties.", _ExitCreateAndSetCommand);  
  
_ExitCreateAndSetCommand:  
  
   if (pICommandProperties)  
   {  
      pICommandProperties->Release();  
      pICommandProperties = NULL;  
   }  
  
   if (pIDBCreateCommand)  
   {  
      pIDBCreateCommand->Release();  
      pIDBCreateCommand = NULL;  
   }  
  
   if (pIDBCreateSession)  
   {  
      pIDBCreateSession->Release();  
      pIDBCreateSession = NULL;  
   }  
  
   if (FAILED(hr))  
   {  
      if (pICommandText)  
      {  
         pICommandText->Release();  
         pICommandText = NULL;  
      }  
   }  
  
   *ppICommandText = pICommandText;  
   return hr;  
}  
  
HRESULT ProcessResultSet(IRowset* pIRowset)  
{  
   HRESULT hr;  
  
   IColumnsInfo* pIColumnsInfo = NULL;  
   DBCOLUMNINFO* pDBColumnInfo = NULL;  
   ULONG lNumCols = 0;  
   wchar_t* pStringsBuffer = NULL;  
  
   DBBINDING* pBindings = NULL;  
   DBOBJECT dbobj;  
   ULONG idxBinding;  
   IAccessor* pIAccessor = NULL;  
   HACCESSOR hAccessor = DB_NULL_HACCESSOR;  
   HROW hRows[1] = {DB_NULL_HROW};  
   HROW* pRow = &hRows[0];  
   BYTE* pBuffer = NULL;  
  
   ULONG lNumRowsRetrieved;  
   DBLENGTH dwOffset = 0;  
  
   hr = pIRowset->QueryInterface(IID_IColumnsInfo, (void **)&pIColumnsInfo);  
   CHKHR_GOTO(hr, L"Failed to QI Rowset for IColumnsInfo.", _ExitProcessResultSet);  
  
   hr = pIColumnsInfo->GetColumnInfo(&lNumCols, &pDBColumnInfo, &pStringsBuffer);  
   CHKHR_GOTO(hr, L"Failed to obtain Column Information.", _ExitProcessResultSet);  
  
   pBindings = new DBBINDING[lNumCols];  
  
   if (!pBindings)  
   {  
      hr = E_OUTOFMEMORY;  
      goto _ExitProcessResultSet;  
   }  
  
   memset(pBindings, 0, sizeof(DBBINDING) * lNumCols);  
  
   dbobj.dwFlags = STGM_READ;  
   dbobj.iid = IID_ISequentialStream;  
  
   for (idxBinding = 0; idxBinding < lNumCols; idxBinding++)   
   {  
      pBindings[idxBinding].iOrdinal = idxBinding + 1;  
      pBindings[idxBinding].obStatus = dwOffset;  
      pBindings[idxBinding].obLength = dwOffset + sizeof(DBSTATUS);  
      pBindings[idxBinding].obValue = dwOffset + sizeof(DBSTATUS) + sizeof(DBLENGTH);  
  
      pBindings[idxBinding].pTypeInfo = NULL;  
      pBindings[idxBinding].pBindExt = NULL;  
      pBindings[idxBinding].dwPart = DBPART_VALUE | DBPART_LENGTH | DBPART_STATUS;  
      pBindings[idxBinding].dwMemOwner = DBMEMOWNER_CLIENTOWNED;  
      pBindings[idxBinding].eParamIO = DBPARAMIO_NOTPARAM;  
      pBindings[idxBinding].bPrecision = pDBColumnInfo[idxBinding].bPrecision;  
      pBindings[idxBinding].bScale = pDBColumnInfo[idxBinding].bScale;  
  
      pBindings[idxBinding].cbMaxLen = 0;  
      pBindings[idxBinding].wType = DBTYPE_WSTR;  
  
   // Determine the maximum number of bytes required in our buffer to  
   // contain the Unicode string representation of the provider's native  
   // data type, including room for the NULL-termination character  
   switch( pDBColumnInfo[idxBinding].wType )  
   {  
      case DBTYPE_NULL:  
      case DBTYPE_EMPTY:  
      case DBTYPE_I1:  
      case DBTYPE_I2:  
      case DBTYPE_I4:  
      case DBTYPE_UI1:  
      case DBTYPE_UI2:  
      case DBTYPE_UI4:  
      case DBTYPE_R4:  
      case DBTYPE_BOOL:  
      case DBTYPE_I8:  
      case DBTYPE_UI8:  
      case DBTYPE_R8:  
      case DBTYPE_CY:  
      case DBTYPE_ERROR:  
      // When the above types are converted to a string, they  
      // will all fit into 25 characters, so use that plus space  
      // for the NULL-terminator.  
  
      pBindings[idxBinding].cbMaxLen = (25 + 1) * sizeof(WCHAR);  
      break;  
  
      case DBTYPE_DECIMAL:  
      case DBTYPE_NUMERIC:  
      case DBTYPE_DATE:  
      case DBTYPE_DBDATE:  
      case DBTYPE_DBTIMESTAMP:  
      case DBTYPE_GUID:  
      // Converted to a string, the above types will all fit into  
      // 50 characters, so use that plus space for the terminator.  
  
      pBindings[idxBinding].cbMaxLen = (50 + 1) * sizeof(WCHAR);  
      break;  
  
      case DBTYPE_BYTES:  
      // In converting DBTYPE_BYTES to a string, each byte  
      // becomes two characters (e.g. 0xFF -> "FF"), so we  
      // will use double the maximum size of the column plus  
      // include space for the NULL-terminator.  
  
      pBindings[idxBinding].cbMaxLen = (pDBColumnInfo[idxBinding].ulColumnSize * 2 + 1) * sizeof(WCHAR);  
      break;  
  
      case DBTYPE_STR:  
      case DBTYPE_WSTR:  
      case DBTYPE_BSTR:  
      // Going from a string to our string representation,  
      // we can just take the maximum size of the column,  
      // a count of characters, and include space for the  
      // terminator, which is not included in the column size.  
  
      pBindings[idxBinding].cbMaxLen = (pDBColumnInfo[idxBinding].ulColumnSize + 1) * sizeof(WCHAR);  
      break;  
  
      default:  
      // For any other type, we will simply use our maximum  
      // column buffer size, since the display size of these  
      // columns may be variable (e.g. DBTYPE_VARIANT) or  
      // unknown (e.g. provider-specific types).  
      pBindings[idxBinding].cbMaxLen = MAX_COL_SIZE;  
      break;  
   }  
  
   // If the provider's native data type for this column is  
   // DBTYPE_IUNKNOWN or this is a BLOB column and the user  
   // has requested that we bind BLOB columns as ISequentialStream  
   // objects, bind this column as an ISequentialStream object if  
   // the provider supports our creating another ISequentialStream  
   // binding.  
   if(pDBColumnInfo[idxBinding].dwFlags & DBCOLUMNFLAGS_ISLONG)  
   {  
      pBindings[idxBinding].wType = DBTYPE_IUNKNOWN;  
  
      pBindings[idxBinding].cbMaxLen = sizeof(ISequentialStream*);  
  
      pBindings[idxBinding].pObject = (DBOBJECT *)CoTaskMemAlloc(sizeof(DBOBJECT));  
  
      if (!pBindings[idxBinding].pObject)  
      {  
         hr = E_OUTOFMEMORY;  
         goto _ExitProcessResultSet;  
      }  
  
      // Direct the provider to create an ISequentialStream  
      // object over the data for this column.  
      pBindings[idxBinding].pObject->iid = IID_ISequentialStream;  
  
      // We want read access on the ISequentialStream  
      // object that the provider will create for us  
      pBindings[idxBinding].pObject->dwFlags = STGM_READ;  
      }  
  
      // Ensure that the bound maximum length is no more than the  
      // maximum column size in bytes that we've defined.  
      pBindings[idxBinding].cbMaxLen = min(pBindings[idxBinding].cbMaxLen, MAX_COL_SIZE);  
  
      // Update the offset past the end of this column's data, so  
      // that the next column will begin in the correct place in  
      // the buffer.  
      dwOffset = pBindings[idxBinding].cbMaxLen + pBindings[idxBinding].obValue;  
  
      // Ensure that the data for the next column will be correctly  
      // aligned for all platforms, or, if we're done with columns,  
      // that if we allocate space for multiple rows that the data  
      // for every row is correctly aligned.  
      dwOffset = ROUNDUP(dwOffset);  
   }  
  
   hr = pIRowset->QueryInterface(IID_IAccessor, (void **) &pIAccessor);  
   CHKHR_GOTO(hr, L"Failed to obtain Accessor interface", _ExitProcessResultSet);  
  
   hr = pIAccessor->CreateAccessor(DBACCESSOR_ROWDATA,  
      lNumCols,  
      pBindings,  
      0,  
      &hAccessor,  
      NULL);  
  
   CHKHR_GOTO(hr, L"Failed to create Accessor", _ExitProcessResultSet);  
   for (idxBinding = 0; idxBinding < lNumCols; idxBinding++)   
   {  
      cout << pDBColumnInfo[idxBinding].pwszName << endl;  
   }  
  
   lNumRowsRetrieved = 0;  
  
   hr = pIRowset->GetNextRows(  
      NULL,  
      0,  
      1,  
      &lNumRowsRetrieved,  
      &pRow);  
  
   CHKHR_GOTO(hr, L"Failed to fetch a row from the rowset", _ExitProcessResultSet);  
  
   pBuffer = new BYTE[sizeof(DBSTATUS) + sizeof(DBLENGTH) + sizeof(IUnknown*)];  
  
   if (!pBuffer)  
   {  
      hr = E_OUTOFMEMORY;  
      goto _ExitProcessResultSet;  
   }  
  
   while(lNumRowsRetrieved && hr != DB_S_ENDOFROWSET)   
   {  
      memset(pBuffer, 0, sizeof(DBSTATUS) + sizeof(DBLENGTH) + sizeof(IUnknown*));  
  
      hr = pIRowset->GetData(hRows[0], hAccessor, pBuffer);  
      CHKHR_GOTO(hr, L"Failed to obtain row data", _ExitProcessResultSet);  
  
      for (idxBinding = 0; idxBinding < lNumCols; idxBinding++)  
      {  
         if (pBindings[idxBinding].wType == DBTYPE_IUNKNOWN)  
         {  
            BYTE pbBuff[3000];  
            ULONG cbNeeded = sizeof(pbBuff)/sizeof(BYTE);  
            ULONG cbRead;  
            ULONG cbReadTotal = 0;  
            ISequentialStream* pISequentialStream = NULL;  
  
            IUnknown* pIUnknown = *((IUnknown**)(pBuffer + pBindings[idxBinding].obValue));  
            pIUnknown->QueryInterface(IID_ISequentialStream, (void**)&pISequentialStream);  
  
            do  
            {  
               hr = pISequentialStream->Read(pbBuff, cbNeeded, &cbRead);  
               cbReadTotal += cbRead;  
            }  
            while (SUCCEEDED(hr) && hr != S_FALSE && cbRead == cbNeeded);  
  
               cout << "Total Bytes Read: " << cbReadTotal << endl;  
  
               pISequentialStream->Release();  
               pISequentialStream = NULL;  
               pIUnknown->Release();  
               pIUnknown = NULL;  
            }  
         }  
  
         pIRowset->ReleaseRows(1, pRow, NULL, NULL, NULL);  
  
         hr = pIRowset->GetNextRows(NULL,  
            0,  
            1,  
            &lNumRowsRetrieved,  
            &pRow);  
  
         CHKHR_GOTO(hr, L"Failed to fetch a row from the rowset.", _ExitProcessResultSet);  
   }  
  
_ExitProcessResultSet:  
  
   pIRowset->ReleaseRows(1, pRow, NULL, NULL, NULL);  
   delete [] pBuffer;  
  
   if (pIAccessor)  
   {  
      if (hAccessor != DB_NULL_HACCESSOR)  
      {  
         pIAccessor->ReleaseAccessor(hAccessor, NULL);  
      }  
  
      pIAccessor->Release();  
      pIAccessor = NULL;  
   }  
  
   if (pBindings)  
   {  
      for (idxBinding = 0; idxBinding < lNumCols; idxBinding++)  
      {  
         if (pBindings[idxBinding].pObject)  
         CoTaskMemFree(pBindings[idxBinding].pObject);  
      }  
   }  
  
   delete [] pBindings;  
  
   CoTaskMemFree(pDBColumnInfo);  
   CoTaskMemFree(pStringsBuffer);  
  
   if (pIColumnsInfo)  
   {  
      pIColumnsInfo->Release();  
      pIColumnsInfo = NULL;  
   }  
  
   return hr;  
}  
```  
  
 <span data-ttu-id="c0ab1-140">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자가 많은 값 데이터 형식을 노출 하는 방법에 대 한 자세한 내용은 [BLOB 및 OLE 개체](../../native-client-ole-db-blobs/blobs-and-ole-objects.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-140">For more information about how the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes large value data types, see [BLOBs and OLE Objects](../../native-client-ole-db-blobs/blobs-and-ole-objects.md).</span></span>  
  
## <a name="sql-server-native-client-odbc-driver"></a><span data-ttu-id="c0ab1-141">SQL Server Native Client ODBC 드라이버</span><span class="sxs-lookup"><span data-stu-id="c0ab1-141">SQL Server Native Client ODBC Driver</span></span>  
 <span data-ttu-id="c0ab1-142">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT odbc 드라이버는 **varchar (max)**, **varbinary (max)** 및 **NVARCHAR (max)** 형식을 odbc API 함수에서 odbc SQL 데이터 형식을 허용 하거나 반환 하는 SQL_VARCHAR, SQL_VARBINARY 및 SQL_WVARCHAR 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-142">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver exposes the **varchar(max)**, **varbinary(max)** and **nvarchar(max)** types as SQL_VARCHAR, SQL_VARBINARY, and SQL_WVARCHAR in ODBC API functions that accept or return ODBC SQL data types.</span></span>  
  
 <span data-ttu-id="c0ab1-143">열의 최대 크기를 보고할 때 드라이버는 다음 중 하나를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-143">When reporting the maximum size of a column, the driver will report either:</span></span>  
  
-   <span data-ttu-id="c0ab1-144">예를 들어 **varchar (2000)** 열에 대해 정의 된 최대 크기는 2000입니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-144">The defined maximum size, which for example, is 2000 for a **varchar(2000)** column, or</span></span>  
  
-   <span data-ttu-id="c0ab1-145">**Varchar (max)** 열의 경우 값이 "제한 없음" 이면 0입니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-145">The value "unlimited" which in the case of a **varchar(max)** column equals 0.</span></span>  
  
 <span data-ttu-id="c0ab1-146">표준 변환 규칙은 varchar ( **max)** 열에 적용 됩니다. 즉 **, varchar (2000\*\*\*\*)** 열에 유효한 모든 변환은 **varchar (max)** 열에도 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-146">The standard conversion rules apply to a **varchar(max)** column, meaning that any conversion that is valid for a **varchar(** 2000 **)** column will also be valid for a **varchar(max)** column.</span></span> <span data-ttu-id="c0ab1-147">**nvarchar(max)** 및 **varbinary(max)** 열의 경우도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-147">The same is true for **nvarchar(max)** and **varbinary(max)** columns.</span></span>  
  
 <span data-ttu-id="c0ab1-148">다음은 큰 값 데이터 형식 작업을 위해 향상된 ODBC  API  함수 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-148">The following is a list of the ODBC API functions that have been enhanced to work with large value data types:</span></span>  
  
-   [<span data-ttu-id="c0ab1-149">SQLBindCol</span><span class="sxs-lookup"><span data-stu-id="c0ab1-149">SQLBindCol</span></span>](../../native-client-odbc-api/sqlbindcol.md)  
  
-   [<span data-ttu-id="c0ab1-150">SQLBindParameter</span><span class="sxs-lookup"><span data-stu-id="c0ab1-150">SQLBindParameter</span></span>](../../native-client-odbc-api/sqlbindparameter.md)  
  
-   [<span data-ttu-id="c0ab1-151">SQLColAttribute</span><span class="sxs-lookup"><span data-stu-id="c0ab1-151">SQLColAttribute</span></span>](../../native-client-odbc-api/sqlcolattribute.md)  
  
-   [<span data-ttu-id="c0ab1-152">SQLColumns</span><span class="sxs-lookup"><span data-stu-id="c0ab1-152">SQLColumns</span></span>](../../native-client-odbc-api/sqlcolumns.md)  
  
-   [<span data-ttu-id="c0ab1-153">SQLDescribeCol</span><span class="sxs-lookup"><span data-stu-id="c0ab1-153">SQLDescribeCol</span></span>](../../native-client-odbc-api/sqldescribecol.md)  
  
-   [<span data-ttu-id="c0ab1-154">SQLDescribeParam</span><span class="sxs-lookup"><span data-stu-id="c0ab1-154">SQLDescribeParam</span></span>](../../native-client-odbc-api/sqldescribeparam.md)  
  
-   [<span data-ttu-id="c0ab1-155">SQLGetData</span><span class="sxs-lookup"><span data-stu-id="c0ab1-155">SQLGetData</span></span>](../../native-client-odbc-api/sqlgetdata.md)  
  
-   [<span data-ttu-id="c0ab1-156">SQLGetTypeInfo</span><span class="sxs-lookup"><span data-stu-id="c0ab1-156">SQLGetTypeInfo</span></span>](../../native-client-odbc-api/sqlgettypeinfo.md)  
  
## <a name="see-also"></a><span data-ttu-id="c0ab1-157">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c0ab1-157">See Also</span></span>  
 [<span data-ttu-id="c0ab1-158">SQL Server Native Client 기능</span><span class="sxs-lookup"><span data-stu-id="c0ab1-158">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
