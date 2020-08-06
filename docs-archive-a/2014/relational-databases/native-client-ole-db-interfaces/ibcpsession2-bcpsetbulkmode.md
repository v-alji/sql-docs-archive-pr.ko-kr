---
title: IBCPSession2::BCPSetBulkMode | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- BCPSetBulkMode function
ms.assetid: babba19f-e67b-450c-b0e6-523a0f9d23ab
author: rothja
ms.author: jroth
ms.openlocfilehash: 9605ff9b8effde1b4a77ba0d8554c719a8a8d1e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659965"
---
# <a name="ibcpsession2bcpsetbulkmode"></a><span data-ttu-id="aebb2-102">IBCPSession2::BCPSetBulkMode</span><span class="sxs-lookup"><span data-stu-id="aebb2-102">IBCPSession2::BCPSetBulkMode</span></span>
  <span data-ttu-id="aebb2-103">IBCPSession2::BCPSetBulkMode는 열 형식을 지정하기 위한 [IBCPSession::BCPColFmt&#40;OLE DB&#41;](ibcpsession-bcpcolfmt-ole-db.md)에 대한 대안을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-103">IBCPSession2::BCPSetBulkMode provides an alternative to [IBCPSession::BCPColFmt &#40;OLE DB&#41;](ibcpsession-bcpcolfmt-ole-db.md) for specifying the column format.</span></span> <span data-ttu-id="aebb2-104">개별 열 형식 특성을 설정하는 IBCPSession::BCPColFmt와 달리, IBCPSession2::BCPSetBulkMode는 모든 특성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-104">Unlike IBCPSession::BCPColFmt, which sets individual column format attributes, IBCPSession2::BCPSetBulkMode sets all attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aebb2-105">구문</span><span class="sxs-lookup"><span data-stu-id="aebb2-105">Syntax</span></span>  
  
```  
  
HRESULT BCPSetBulkMode (  
      int property,  
   void * pField,  
   int cbField,  
   void * pRow,  
   int cbRow  
);  
```  
  
## <a name="arguments"></a><span data-ttu-id="aebb2-106">인수</span><span class="sxs-lookup"><span data-stu-id="aebb2-106">Arguments</span></span>  
 <span data-ttu-id="aebb2-107">*property*</span><span class="sxs-lookup"><span data-stu-id="aebb2-107">*property*</span></span>  
 <span data-ttu-id="aebb2-108">BYTE 유형의 상수입니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-108">A constant of type BYTE.</span></span> <span data-ttu-id="aebb2-109">상수 목록은 주의 섹션의 표를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="aebb2-109">See the table in the Remarks section for a list of the constants.</span></span>  
  
 <span data-ttu-id="aebb2-110">*pField*</span><span class="sxs-lookup"><span data-stu-id="aebb2-110">*pField*</span></span>  
 <span data-ttu-id="aebb2-111">필드 종결자 값에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-111">The pointer to the field terminator value.</span></span>  
  
 <span data-ttu-id="aebb2-112">cbField</span><span class="sxs-lookup"><span data-stu-id="aebb2-112">cbField</span></span>  
 <span data-ttu-id="aebb2-113">필드 종결자 값의 길이(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-113">The length in bytes of the field terminator value.</span></span>  
  
 <span data-ttu-id="aebb2-114">pRow</span><span class="sxs-lookup"><span data-stu-id="aebb2-114">pRow</span></span>  
 <span data-ttu-id="aebb2-115">행 종결자 값에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-115">The pointer to the row terminator value.</span></span>  
  
 <span data-ttu-id="aebb2-116">cbRow</span><span class="sxs-lookup"><span data-stu-id="aebb2-116">cbRow</span></span>  
 <span data-ttu-id="aebb2-117">행 종결자 값의 길이(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-117">The length in bytes of the row terminator value.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="aebb2-118">반환</span><span class="sxs-lookup"><span data-stu-id="aebb2-118">Returns</span></span>  
 <span data-ttu-id="aebb2-119">IBCPSession2::BCPSetBulkMode는 다음 중 하나를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-119">IBCPSession2::BCPSetBulkMode can return one of the following:</span></span>  
  
|||  
|-|-|  
|`S_OK`|<span data-ttu-id="aebb2-120">메서드가 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-120">The method succeeded.</span></span>|  
|`E_FAIL`|<span data-ttu-id="aebb2-121">공급자 관련 오류가 발생했습니다. 자세한 내용을 보려면 ISQLServerErrorInfo 인터페이스를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="aebb2-121">A provider specific error occurred, for detailed information use the ISQLServerErrorInfo interface.</span></span>|  
|`E_UNEXPECTED`|<span data-ttu-id="aebb2-122">예기치 않은 메서드가 호출되었습니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-122">The call to the method was unexpected.</span></span> <span data-ttu-id="aebb2-123">예를 들어 `IBCPSession2::BCPInit` IBCPSession2:: Bcpset대량 모드를 호출 하기 전에 메서드를 호출 하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-123">For example, the `IBCPSession2::BCPInit` method was not called before calling IBCPSession2::BCPSetBulkMode.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="aebb2-124">잘못된 인수입니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-124">The argument was invalid.</span></span>|  
|`E_OUTOFMEMORY`|<span data-ttu-id="aebb2-125">메모리 부족 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-125">Out of memory error.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aebb2-126">설명</span><span class="sxs-lookup"><span data-stu-id="aebb2-126">Remarks</span></span>  
 <span data-ttu-id="aebb2-127">IBCPSession2::BCPSetBulkMode를 사용하여 쿼리 또는 테이블에서 대량 복사를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-127">IBCPSession2::BCPSetBulkMode can be used to bulk copy out of either a query or a table.</span></span> <span data-ttu-id="aebb2-128">쿼리 문을 대량 복사하는 데 사용되는 IBCPSession2::BCPSetBulkMode는 `IBCPSession::BCPControl(BCP_OPTIONS_HINTS, ...)`를 호출하여 쿼리 문을 지정하기 전에 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-128">When IBCPSession2::BCPSetBulkMode is used to bulk copy out of a query statement, it must be called before calling `IBCPSession::BCPControl(BCP_OPTIONS_HINTS, ...)` to specify the query statement.</span></span>  
  
 <span data-ttu-id="aebb2-129">단일 명령 텍스트에서 RPC 호출 구문을 일괄 처리 쿼리 구문(예:`{rpc func};SELECT * from Tbl`)과 결합하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="aebb2-129">You should avoid combining RPC call syntax with batch query syntax (`{rpc func};SELECT * from Tbl`, for example) in a single command text.</span></span>  <span data-ttu-id="aebb2-130">그러면 ICommandPrepare::Prepare에서 오류를 반환하며 메타데이터를 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-130">This will cause ICommandPrepare::Prepare to return an error and prevent you from retrieving metadata.</span></span> <span data-ttu-id="aebb2-131">단일 명령 텍스트에서 저장 프로시저 실행 및 일괄 처리 쿼리를 결합해야 할 경우 ODBC CALL 구문(예:`{call func}; SELECT * from Tbl`)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-131">Use ODBC CALL syntax (`{call func}; SELECT * from Tbl`, for example) if you need to combine stored procedure execution and batch query in a single command text.</span></span>  
  
 <span data-ttu-id="aebb2-132">다음 표에서는 *property* 매개 변수에 대한 상수를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-132">The following table lists the constants for the *property* parameter.</span></span>  
  
|<span data-ttu-id="aebb2-133">속성</span><span class="sxs-lookup"><span data-stu-id="aebb2-133">Property</span></span>|<span data-ttu-id="aebb2-134">Description</span><span class="sxs-lookup"><span data-stu-id="aebb2-134">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="aebb2-135">BCP_OUT_CHARACTER_MODE</span><span class="sxs-lookup"><span data-stu-id="aebb2-135">BCP_OUT_CHARACTER_MODE</span></span>|<span data-ttu-id="aebb2-136">문자 출력 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-136">Specifies character output mode.</span></span><br /><br /> <span data-ttu-id="aebb2-137">는 BCP.EXE의-c 옵션 및 *Euserdatatype* 속성이로 설정 된 IBCPSession:: BCPColFmt에 해당 `BCP_TYPE_SQLCHARACTER` 합니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-137">Corresponds to the -c option in BCP.EXE, and to IBCPSession::BCPColFmt with *eUserDataType* property set to `BCP_TYPE_SQLCHARACTER`.</span></span>|  
|<span data-ttu-id="aebb2-138">BCP_OUT_WIDE_CHARACTER_MODE</span><span class="sxs-lookup"><span data-stu-id="aebb2-138">BCP_OUT_WIDE_CHARACTER_MODE</span></span>|<span data-ttu-id="aebb2-139">유니코드 출력 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-139">Specifies Unicode output mode.</span></span><br /><br /> <span data-ttu-id="aebb2-140">*Euserdatatype* 속성이로 설정 된 BCP.EXE 및 IBCPSession:: BCPColFmt의-w 옵션에 해당 `BCP_TYPE_SQLNCHAR` 합니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-140">Corresponds to the -w option in BCP.EXE and IBCPSession::BCPColFmt with *eUserDataType* property set to `BCP_TYPE_SQLNCHAR`.</span></span>|  
|<span data-ttu-id="aebb2-141">BCP_OUT_NATIVE_TEXT_MODE</span><span class="sxs-lookup"><span data-stu-id="aebb2-141">BCP_OUT_NATIVE_TEXT_MODE</span></span>|<span data-ttu-id="aebb2-142">비문자 유형의 경우 네이티브 유형을 지정하고 문자 유형의 경우 유니코드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-142">Specifies native types for non-character types and Unicode for character types.</span></span><br /><br /> <span data-ttu-id="aebb2-143">열 형식이 문자열이 면이 고, 그렇지 않은 경우에는 IBCPSession:: BCPColFmt with *Euserdatatype* 속성을로 설정 하 여 BCP.EXE 및의-N 옵션에 해당 `BCP_TYPE_SQLNCHAR` `BCP_TYPE_DEFAULT` 합니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-143">Corresponds to the -N option in BCP.EXE and IBCPSession::BCPColFmt with *eUserDataType* property set to `BCP_TYPE_SQLNCHAR` if the column type is a string or `BCP_TYPE_DEFAULT` if not a string.</span></span>|  
|<span data-ttu-id="aebb2-144">BCP_OUT_NATIVE_MODE</span><span class="sxs-lookup"><span data-stu-id="aebb2-144">BCP_OUT_NATIVE_MODE</span></span>|<span data-ttu-id="aebb2-145">네이티브 데이터베이스 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-145">Specifies native database types.</span></span><br /><br /> <span data-ttu-id="aebb2-146">*Euserdatatype* 속성이로 설정 된 BCP.EXE 및 IBCPSession:: BCPColFmt의-n 옵션에 해당 `BCP_TYPE_DEFAULT` 합니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-146">Corresponds to the -n option in BCP.EXE and IBCPSession::BCPColFmt with *eUserDataType* property set to `BCP_TYPE_DEFAULT`.</span></span>|  
  
 <span data-ttu-id="aebb2-147">IBCPSession2::BCPSetBulkMode와 충돌하지 않는 IBCPSession::BCPControl 옵션에 대해 IBCPSession::BCPControl 및 IBCPSession2::BCPSetBulkMode를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-147">You can call IBCPSession::BCPControl and IBCPSession2::BCPSetBulkMode for IBCPSession::BCPControl options that do not conflict with IBCPSession2::BCPSetBulkMode.</span></span> <span data-ttu-id="aebb2-148">예를 들어 `BCP_OPTION_FIRST` 및 IBCPSession2:: Bcpset대량 모드를 사용 하 여 IBCPSession:: BCPControl을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-148">For example, you can call IBCPSession::BCPControl with `BCP_OPTION_FIRST` and IBCPSession2::BCPSetBulkMode.</span></span>  
  
 <span data-ttu-id="aebb2-149">`BCP_OPTION_TEXTFILE`및 IBCPSession2:: BcpsetIBCPSession 모드를 사용 하 여:: BCPControl을 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-149">You cannot call IBCPSession::BCPControl with `BCP_OPTION_TEXTFILE` and IBCPSession2::BCPSetBulkMode.</span></span>  
  
 <span data-ttu-id="aebb2-150">IBCPSession::BCPColFmt, IBCPSession::BCPControl 및 IBCPSession::BCPReadFmt를 포함하는 일련의 함수 호출을 사용하여 IBCPSession2::BCPSetBulkMode를 호출하려고 하면 함수 호출 중 하나가 시퀀스 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-150">If you attempt to call IBCPSession2::BCPSetBulkMode with a sequence of function calls that includes IBCPSession::BCPColFmt, IBCPSession::BCPControl, and IBCPSession::BCPReadFmt, one of the function calls will return a sequence error failure.</span></span> <span data-ttu-id="aebb2-151">이러한 오류를 해결하도록 선택하는 경우 IBCPSession::BCPInit를 호출하여 설정을 재설정하고 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-151">If you choose to correct the failure, call IBCPSession::BCPInit to reset the settings and start over.</span></span>  
  
 <span data-ttu-id="aebb2-152">다음 표에서는 함수 시퀀스 오류를 발생시키는 일부 함수 호출의 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-152">The following table presents some examples of function calls that result in a function sequence error:</span></span>  
  
 <span data-ttu-id="aebb2-153">호출 시퀀스</span><span class="sxs-lookup"><span data-stu-id="aebb2-153">Call sequence</span></span>  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_IN);  
BCPSetBulkMode();  
```  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPSetBulkMode();  
BCPReadFmt();  
```  
  
```  
BCPInit(NULL, "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_HINTS, "select ...");  
BCPSetBulkMode();  
```  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPSetBulkMode();  
BCPColFmt();  
```  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPReadFmt();  
BCPColFmt();  
```  
  
```  
BCPInit(NULL, "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPSetBulkMode();  
BCPControl(BCP_OPTION_HINTS, "select ...");  
BCPReadFmt();  
```  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPColumns();  
```  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPSetColFmt();  
```  
  
## <a name="example"></a><span data-ttu-id="aebb2-154">예제</span><span class="sxs-lookup"><span data-stu-id="aebb2-154">Example</span></span>  
 <span data-ttu-id="aebb2-155">다음 예제에서는 IBCPSession2::BCPSetBulkMode의 서로 다른 설정을 사용하여 4개의 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="aebb2-155">The following sample creates four files using different settings of IBCPSession2::BCPSetBulkMode.</span></span>  
  
```  
  
// compile with: sqlncli11.lib oleaut32.lib ole32.lib  
  
#include <stdio.h>  
#include "sqlncli.h"  
  
IDBInitialize*  g_pIDBInitialize = NULL;  
IBCPSession2 * g_pIBcpSession = NULL;  
class COLEDBPropSet : public DBPROPSET {  
public:  
   COLEDBPropSet() {  
      rgProperties = NULL;  
      cProperties = 0;  
   };  
   COLEDBPropSet(const GUID& guid) {  
      rgProperties = NULL;  
      cProperties = 0;  
      guidPropertySet = guid;  
   };  
   ~COLEDBPropSet() {  
      for ( ULONG i = 0 ; i < cProperties ; i++ )  
         VariantClear(&rgProperties[i].vValue);  
      CoTaskMemFree(rgProperties);  
   }  
   void SetGUID(const GUID& guid) {  
      guidPropertySet = guid;  
   };  
   bool AddProperty(DWORD dwPropertyID, bool bValue) {  
      if (!Add())  
         return false;  
      rgProperties[cProperties].dwPropertyID = dwPropertyID;  
      rgProperties[cProperties].vValue.vt = VT_BOOL;  
      rgProperties[cProperties].vValue.boolVal = (bValue) ? VARIANT_TRUE : VARIANT_FALSE;  
      cProperties++;  
      return true;  
   };  
   bool AddProperty(DWORD dwPropertyID, long nValue) {  
      if (!Add())  
         return false;  
      rgProperties[cProperties].dwPropertyID  = dwPropertyID;  
      rgProperties[cProperties].vValue.vt     = VT_I4;  
      rgProperties[cProperties].vValue.lVal   = nValue;  
      cProperties++;  
      return true;  
   };  
   bool AddProperty(DWORD dwPropertyID,LPCWSTR szValue) {  
      if (!Add())  
         return false;  
      rgProperties[cProperties].dwPropertyID = dwPropertyID;  
      rgProperties[cProperties].vValue.vt = VT_BSTR;  
      rgProperties[cProperties].vValue.bstrVal = SysAllocString(szValue);  
      cProperties++;  
      return true;  
   };  
   bool Add() {  
      DBPROP* p = (DBPROP*)CoTaskMemRealloc(rgProperties, (cProperties + 1) * sizeof(DBPROP));  
      if (p != NULL) {  
         rgProperties = p;  
         rgProperties[cProperties].dwOptions = DBPROPOPTIONS_REQUIRED;  
         rgProperties[cProperties].colid = DB_NULLID;  
         rgProperties[cProperties].vValue.vt = VT_EMPTY;  
         return true;  
      }  
      else  
         return false;  
   };  
};  
  
void OLEDBCleanUp() {  
   if (g_pIDBInitialize) {  
      g_pIDBInitialize->Release();  
      g_pIDBInitialize = NULL;  
   }  
   if (g_pIBcpSession) {  
      g_pIBcpSession->Release();  
      g_pIBcpSession = NULL;  
   }  
}  
  
BOOL MakeOLEDBConnect(LPWSTR  pServer) {  
   BOOL ret = true;  
   IDBProperties * pIDBProperties = NULL;  
   IDBCreateSession * pIDBCreateSession = NULL;  
   COLEDBPropSet PropSet(DBPROPSET_DBINIT);  
   COLEDBPropSet BcpProperty(DBPROPSET_SQLSERVERDATASOURCE);  
   try {  
      HRESULT hr = CoInitializeEx(NULL,COINIT_MULTITHREADED);   
      hr = CoCreateInstance(SQLNCLI_CLSID, NULL, CLSCTX_INPROC_SERVER, IID_IDBInitialize, (LPVOID *)&g_pIDBInitialize);  
      if (FAILED(hr)) {  
         printf("CoCreateInstance failed\n");  
         return false;  
      }  
      PropSet.AddProperty(DBPROP_INIT_DATASOURCE, (LPWSTR)pServer);  
      PropSet.AddProperty(DBPROP_AUTH_INTEGRATED, L"SSPI");  
      hr = g_pIDBInitialize->QueryInterface(IID_IDBProperties, (void**) &pIDBProperties);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->QueryInterface(IID_IDBProperties...) failed\n");  
         throw false;  
      }  
      hr = pIDBProperties->SetProperties(1, &PropSet);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->SetProperties(...) failed\n");  
         throw false;  
      }  
      hr = g_pIDBInitialize->Initialize();  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->Initialize() failed\n");  
         throw false;  
      }  
      BcpProperty.AddProperty(SSPROP_ENABLEFASTLOAD, true);  
      BcpProperty.AddProperty(SSPROP_ENABLEBULKCOPY, true);  
      hr = pIDBProperties->SetProperties(1, &BcpProperty);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->SetProperties() for bcp failed\n");  
         throw false;  
      }  
      hr = g_pIDBInitialize->QueryInterface(IID_IDBCreateSession, (void**) &pIDBCreateSession);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->QueryInterface(IID_IDBCreateSession..) failed\n");  
         throw false;  
      }  
  
      hr = pIDBCreateSession->CreateSession(NULL, IID_IBCPSession2, (IUnknown**) &g_pIBcpSession);  
      if (FAILED(hr)) {  
         printf("g_pIDBCreateSession->CreateSession() failed\n");  
         throw false;  
      }  
   }  
   catch(...) {  
      ret = false;  
   }  
   if (pIDBProperties)  
      pIDBProperties->Release();  
   if (pIDBCreateSession)  
      pIDBCreateSession->Release();  
   return ret;  
}  
  
BOOL BCPSetBulkMode(LPWSTR pszServer, LPTSTR pszQureryOut, char BCPType, LPWSTR pszDataFile) {  
   HRESULThr;  
   if (!MakeOLEDBConnect(pszServer))  
      return false;  
   hr = g_pIBcpSession->BCPInit(NULL, pszDataFile, NULL, BCP_DIRECTION_OUT );   // bcp init for queryout  
   if (FAILED(hr)) {  
      printf("BCP init failed\n");  
      OLEDBCleanUp();  
      return false;  
   }  
   // setbulkmode  
   char ColTerm[] = "\t";  
   char RowTerm[] = "\r\n";  
   wchar_t wColTerm[] = L"\t";  
   wchar_t wRowTerm[] = L"\r\n";  
   BYTE * pColTerm = NULL;  
   int cbColTerm = NULL;  
   BYTE * pRowTerm = 0;  
   int cbRowTerm = 0;  
   int bulkmode = -1;  
  
   if(BCPType == 'c') {   // bcp -c  
      pColTerm = (BYTE*)ColTerm;  
      pRowTerm = (BYTE*)RowTerm;  
      cbColTerm = 1;  
      cbRowTerm = 2;  
      bulkmode = BCP_OUT_CHARACTER_MODE;  
   }  
   else  
      if(BCPType == 'w') {   // bcp -w  
         pColTerm = (BYTE*)wColTerm;  
         pRowTerm = (BYTE*)wRowTerm;  
         cbColTerm = 2;  
         cbRowTerm = 4;  
         bulkmode = BCP_OUT_WIDE_CHARACTER_MODE;  
      }  
      else  
         if (BCPType == 'n')   // bcp -n  
            bulkmode = BCP_OUT_NATIVE_MODE;  
         else  
            if (BCPType == 'N')   // bcp -n  
               bulkmode = BCP_OUT_NATIVE_TEXT_MODE;  
            else {  
               printf("unknown bcp mode\n");  
               OLEDBCleanUp();  
               return false;  
            }  
            hr = g_pIBcpSession->BCPSetBulkMode(bulkmode, pColTerm, cbColTerm, pRowTerm, cbRowTerm);  
            if (FAILED(hr)) {  
               printf("BCPSetBulkMode failed\n");  
               OLEDBCleanUp();  
               return false;  
            }  
  
            // set queryout TSQL statement  
            hr = g_pIBcpSession->BCPControl(BCP_OPTION_HINTS, pszQureryOut);  
            if (FAILED(hr)) {  
               printf("BCPControl failed\n");  
               OLEDBCleanUp();  
               return false;  
            }  
            // bcp copy  
            DBROWCOUNT nRowsInserted = 0;  
            hr = g_pIBcpSession->BCPExec(&nRowsInserted);  
            if (FAILED(hr)) {  
               printf("BCPExec failed\n");  
               OLEDBCleanUp();  
               return false;  
            }  
            printf("bcp done\n");  
            OLEDBCleanUp();  
            return true;  
}  
  
int main() {  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -c test', 1,2") , 'c', L"bcpc.dat");  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -w test', 1,2") , 'w', L"bcpw.dat");  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -c test', 1,2") , 'n', L"bcpn.dat");  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -w test', 1,2") , 'N', L"bcp_N.dat");  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="aebb2-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aebb2-156">See Also</span></span>  
 [<span data-ttu-id="aebb2-157">IBCPSession2&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="aebb2-157">IBCPSession2 &#40;OLE DB&#41;</span></span>](ibcpsession2-ole-db.md)  
  
  
