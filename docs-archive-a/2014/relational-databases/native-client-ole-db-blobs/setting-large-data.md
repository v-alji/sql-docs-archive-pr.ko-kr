---
title: 대규모 데이터 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- IRowsetChange interface
- BLOBs, OLE objects
- pointer passing [OLE DB]
- SQL Server Native Client OLE DB provider, BLOBs
- large data, OLE objects
ms.assetid: 9d0c524b-22b0-475a-9ff5-5a69a6393b46
author: rothja
ms.author: jroth
ms.openlocfilehash: 5d54e605d855f635066cbd160771d61d7f7f7822
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741919"
---
# <a name="setting-large-data"></a><span data-ttu-id="5ef2c-102">대규모 데이터 설정</span><span class="sxs-lookup"><span data-stu-id="5ef2c-102">Setting Large Data</span></span>
  <span data-ttu-id="5ef2c-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자를 사용 하면 소비자 저장소 개체에 대 한 포인터를 전달 하 여 BLOB 데이터를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef2c-103">With the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, you can set BLOB data by passing a pointer to a consumer storage object.</span></span>  
  
 <span data-ttu-id="5ef2c-104">소비자는 이 데이터가 포함된 스토리지 개체를 만들고 이 스토리지 개체에 대한 포인터를 공급자에게 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef2c-104">The consumer creates a storage object that contains the data and passes a pointer to this storage object to the provider.</span></span> <span data-ttu-id="5ef2c-105">그러면 공급자는 소비자 스토리지 개체에서 데이터를 읽고 이를 BLOB 열에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="5ef2c-105">The provider then reads data from the consumer storage object and writes it to the BLOB column.</span></span>  
  
 <span data-ttu-id="5ef2c-106">자체의 스토리지 개체에 대한 포인터를 전달하기 위해 소비자는 BLOB 열의 값을 바인딩하는 접근자를 만든 다음</span><span class="sxs-lookup"><span data-stu-id="5ef2c-106">To pass a pointer to its own storage object, the consumer creates an accessor that binds the value of the BLOB column.</span></span> <span data-ttu-id="5ef2c-107">그런 다음, 소비자는 BLOB 열을 바인딩하는 접근자와 함께 **IRowsetChange::SetData** 또는 **IRowsetChange::InsertRow** 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef2c-107">The consumer then calls the **IRowsetChange::SetData** or **IRowsetChange::InsertRow** method with the accessor that binds the BLOB column.</span></span> <span data-ttu-id="5ef2c-108">그러면 소비자의 스토리지 개체에 스토리지 인터페이스에 대한 포인터가 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ef2c-108">It passes a pointer to a storage interface on the storage object of the consumer.</span></span>  
  
 <span data-ttu-id="5ef2c-109">이 항목에서는 다음 함수와 함께 사용할 수 있는 기능에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef2c-109">This topic refers to functionality available with the following functions:</span></span>  
  
-   <span data-ttu-id="5ef2c-110">IRowset:SetData</span><span class="sxs-lookup"><span data-stu-id="5ef2c-110">IRowset:SetData</span></span>  
  
-   <span data-ttu-id="5ef2c-111">ICommand::Execute</span><span class="sxs-lookup"><span data-stu-id="5ef2c-111">ICommand::Execute</span></span>  
  
-   <span data-ttu-id="5ef2c-112">IRowsetUpdate::Update</span><span class="sxs-lookup"><span data-stu-id="5ef2c-112">IRowsetUpdate::Update</span></span>  
  
## <a name="how-to-set-large-data"></a><span data-ttu-id="5ef2c-113">대규모 데이터를 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="5ef2c-113">How to Set Large Data</span></span>  
 <span data-ttu-id="5ef2c-114">자체의 스토리지 개체에 대한 포인터를 전달하기 위해 소비자는 BLOB 열의 값을 바인딩하는 접근자를 만든 다음 **IRowsetChange::SetData** 또는 **IRowsetChange::InsertRow** 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef2c-114">To pass a pointer to its own storage object, the consumer creates an accessor that binds the value of the BLOB column and then calls the **IRowsetChange::SetData** or **IRowsetChange::InsertRow** methods.</span></span> <span data-ttu-id="5ef2c-115">BLOB 데이터를 설정하려면 다음과 같이 하십시오.</span><span class="sxs-lookup"><span data-stu-id="5ef2c-115">To set BLOB data:</span></span>  
  
1.  <span data-ttu-id="5ef2c-116">BLOB 열에 액세스하는 방법을 설명하는 DBOBJECT 구조를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5ef2c-116">Create a DBOBJECT structure describing how the BLOB column should be accessed.</span></span> <span data-ttu-id="5ef2c-117">DBOBJECT 구조의 *Dwflag* 요소를 STGM_READ 설정 하 고 *iid* 요소를 IID_ISequentialStream (노출할 인터페이스)로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef2c-117">Set the *dwFlag* element of the DBOBJECT structure to STGM_READ and set the *iid* element to IID_ISequentialStream (the interface to be exposed).</span></span>  
  
2.  <span data-ttu-id="5ef2c-118">행 집합 업데이트가 가능하도록 DBPROPSET_ROWSET 속성 그룹의 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef2c-118">Set the properties in the DBPROPSET_ROWSET property group so the rowset is updatable.</span></span>  
  
3.  <span data-ttu-id="5ef2c-119">DBBINDING 구조의 배열을 사용하여 각 열에 대해 하나씩 바인딩 집합을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5ef2c-119">Create a set of bindings (one of each column) by using an array of DBBINDING structures.</span></span> <span data-ttu-id="5ef2c-120">DBBINDING 구조의 *wType* 요소를 DBTYPE_IUNKNOWN으로 설정하고 *pObject* 요소를 앞에서 만든 DBOBJECT 구조를 가리키도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef2c-120">Set the *wType* element in the DBBINDING structure to DBTYPE_IUNKNOWN, and the *pObject* element to point to the DBOBJECT structure you created.</span></span>  
  
4.  <span data-ttu-id="5ef2c-121">구조의 DBBINDINGS 배열에 있는 바인딩 정보를 사용하여 접근자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5ef2c-121">Create an accessor using the binding information in the DBBINDINGS array of structures.</span></span>  
  
5.  <span data-ttu-id="5ef2c-122">**GetNextRows** 를 호출하여 다음 행을 행 집합으로 인출합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef2c-122">Call **GetNextRows** to fetch next rows into the rowset.</span></span> <span data-ttu-id="5ef2c-123">**GetData** 를 호출하여 행 집합에서 데이터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef2c-123">Call **GetData** to read the data from the rowset.</span></span>  
  
6.  <span data-ttu-id="5ef2c-124">데이터 및 길이 표시기가 포함된 스토리지 개체를 만든 다음, 해당 BLOB 열을 바인딩하는 접근자와 함께 **IRowsetChange::SetData**(또는 **IRowsetChange::InsertRow**)를 호출하여 데이터를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef2c-124">Create a storage object containing the data (and also the length indicator), and then call **IRowsetChange::SetData** (or **IRowsetChange::InsertRow**) with the accessor that binds the BLOB column to set the data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ef2c-125">예제</span><span class="sxs-lookup"><span data-stu-id="5ef2c-125">Example</span></span>  
 <span data-ttu-id="5ef2c-126">이 예에서는 BLOB 데이터를 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ef2c-126">This example shows how to set BLOB data.</span></span> <span data-ttu-id="5ef2c-127">이 예에서는 데이터를 만들어 예제 레코드를 추가하고 행 집합에서 해당 레코드를 인출한 다음 BLOB 필드의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef2c-127">The example creates a table, adds a sample record, fetches that record in the rowset, and then sets the value of the BLOB field:</span></span>  
  
```  
#define UNICODE  
#define DBINITCONSTANTS  
#define INITGID  
  
#include <windows.h>  
#include <stdio.h>  
#include <stddef.h>  
#include <iostream.h>  
  
#include <oledb.h>  
#include <oledberr.h>  
  
#include <sqlncli.h>  
  
#define SAFE_RELEASE(pIUnknown) if(pIUnknown) (pIUnknown)->Release();  
HRESULT GetCommandObject(REFIID riid, IUnknown** ppIUnknown);  
HRESULT CreateTable(ICommandText* pICommandText);  
  
class CSeqStream : public ISequentialStream  
{  
public:  
    //Constructors  
    CSeqStream();  
    virtual ~CSeqStream();  
  
    virtual BOOL Seek(ULONG iPos);  
    virtual BOOL Clear();  
    virtual BOOL CompareData(void* pBuffer);  
    virtual ULONG Length()  { return m_cBufSize; };  
  
    virtual operator void* const() { return m_pBuffer; };  
  
    STDMETHODIMP_(ULONG)    AddRef(void);  
    STDMETHODIMP_(ULONG)    Release(void);  
    STDMETHODIMP QueryInterface(REFIID riid, LPVOID *ppv);  
  
    STDMETHODIMP Read(   
            /* [out] */ void __RPC_FAR *pv,  
            /* [in]  */ ULONG cb,  
            /* [out] */ ULONG __RPC_FAR *pcbRead);  
  
    STDMETHODIMP Write(   
            /* [in] */ const void __RPC_FAR *pv,  
            /* [in] */ ULONG cb,  
            /* [out]*/ ULONG __RPC_FAR *pcbWritten);  
  
protected:  
    //Data  
  
private:  
  
    ULONG       m_cRef;         // reference count  
    void*       m_pBuffer;      // buffer  
    ULONG       m_cBufSize;     // buffer size  
    ULONG       m_iPos;         // current index position in the buffer  
};  
  
//class implementation  
  
CSeqStream::CSeqStream()  
{  
    m_iPos         = 0;  
    m_cRef         = 0;  
    m_pBuffer      = NULL;  
    m_cBufSize     = 0;  
  
    //The constructor AddRef's  
    AddRef();  
}  
  
CSeqStream::~CSeqStream()  
{  
    //Shouldn't have any references left  
//    ASSERT(m_cRef == 0);  
    CoTaskMemFree(m_pBuffer);  
}  
  
ULONG    CSeqStream::AddRef(void)  
{  
    return ++m_cRef;  
}  
  
ULONG    CSeqStream::Release(void)  
{  
//    ASSERT(m_cRef);  
  
    if(--m_cRef)  
        return m_cRef;  
  
    delete this;  
    return 0;  
}  
  
HRESULT CSeqStream::QueryInterface(REFIID riid, void** ppv)  
{  
//    ASSERT(ppv);  
    *ppv = NULL;  
  
    if (riid == IID_IUnknown)  
        *ppv = this;  
    if (riid == IID_ISequentialStream)  
        *ppv = this;  
  
    if(*ppv)  
    {  
        ((IUnknown*)*ppv)->AddRef();  
        return S_OK;  
    }  
  
    return E_NOINTERFACE;  
}  
  
BOOL CSeqStream::Seek(ULONG iPos)  
{  
    // Make sure the desired position is within the buffer.  
//    ASSERT(iPos == 0 || iPos < m_cBufSize);  
  
    // Reset the current buffer position.  
    m_iPos = iPos;  
    return TRUE;  
}  
  
BOOL CSeqStream::Clear()  
{  
    //Frees the buffer  
    m_iPos         = 0;  
    m_cBufSize     = 0;  
  
    CoTaskMemFree(m_pBuffer);  
    m_pBuffer = NULL;  
  
    return TRUE;  
}  
  
BOOL CSeqStream::CompareData(void* pBuffer)  
{  
//    ASSERT(pBuffer);  
  
    // Quick and easy way to compare user buffer with the stream.  
    return memcmp(pBuffer, m_pBuffer, m_cBufSize)==0;  
}  
  
HRESULT CSeqStream::Read(void *pv, ULONG cb, ULONG* pcbRead)  
{  
    //Parameter checking  
    if(pcbRead)  
        *pcbRead = 0;  
  
    if(!pv)  
        return STG_E_INVALIDPOINTER;  
  
    if(cb == 0)  
        return S_OK;  
  
    // Actual code.  
    ULONG cBytesLeft = m_cBufSize - m_iPos;  
    ULONG cBytesRead = cb > cBytesLeft ? cBytesLeft : cb;  
  
    // If no more bytes to retrieve return.  
    if(cBytesLeft == 0)  
        return S_FALSE;   
  
    // Copy to users buffer the number of bytes requested or remaining.  
    memcpy_s(pv, sizeof(pv), (void*)((BYTE*)m_pBuffer + m_iPos), cBytesRead);  
    m_iPos += cBytesRead;  
  
    if(pcbRead)  
        *pcbRead = cBytesRead;  
  
    if(cb != cBytesRead)  
        return S_FALSE;   
  
    return S_OK;  
}  
  
HRESULT CSeqStream::Write(const void *pv, ULONG cb, ULONG* pcbWritten)  
{  
    // Parameter checking.  
    if(!pv)  
        return STG_E_INVALIDPOINTER;  
  
    if(pcbWritten)  
        *pcbWritten = 0;  
  
    if(cb == 0)  
        return S_OK;  
  
    // Enlarge the current buffer.  
    m_cBufSize += cb;  
  
    // Need to append to the end of the stream.  
    m_pBuffer = CoTaskMemRealloc(m_pBuffer, m_cBufSize);  
    memcpy_s((void*)((BYTE*)m_pBuffer + m_iPos), sizeof((void*)((BYTE*)m_pBuffer + m_iPos)), pv, cb);  
    // m_iPos += cb;  
  
    if(pcbWritten)  
        *pcbWritten = cb;  
  
    return S_OK;  
}  
//...........................................................  
void main()  
{  
    CoInitialize(NULL);  
  
    DBOBJECT ObjectStruct;  
    ObjectStruct.dwFlags = STGM_READ;  
    ObjectStruct.iid     = IID_ISequentialStream;  
  
    struct BLOBDATA  
    {  
        DBSTATUS            dwStatus;     
        DWORD               dwLength;   
        ISequentialStream*  pISeqStream;  
    };  
  
    BLOBDATA BLOBGetData;  
    BLOBDATA BLOBSetData;  
  
    const ULONG cBindings = 1;  
    DBBINDING rgBindings[cBindings];   
    HRESULT hr = S_OK;  
    IAccessor*          pIAccessor          = NULL;  
    ICommandText*       pICommandText       = NULL;  
    ICommandProperties* pICommandProperties = NULL;  
    IRowsetChange*      pIRowsetChange      = NULL;  
    IRowset*            pIRowset            = NULL;  
    CSeqStream*         pMySeqStream        = NULL;  
    ULONG cRowsObtained = 0;  
    HACCESSOR hAccessor = DB_NULL_HACCESSOR;  
    DBBINDSTATUS rgBindStatus[cBindings];  
    HROW* rghRows = NULL;  
    const ULONG cPropSets = 1;  
    DBPROPSET   rgPropSets[cPropSets];  
    const ULONG cProperties = 1;  
    DBPROP      rgProperties[cProperties];  
    const ULONG cBytes = 10;  
    BYTE        pBuffer[cBytes];  
    ULONG       cBytesRead = 0;  
  
    BYTE pReadData[cBytes];  //read BLOB data in this array  
    memset(pReadData, 0xAA, cBytes);  
  
    BYTE pWriteData[cBytes];  //write BLOB data from this array  
    memset(pWriteData, 'D', cBytes);  
  
    // Get the Command object.  
    hr = GetCommandObject(IID_ICommandText,   
                          (IUnknown**)&pICommandText);  
    if (FAILED(hr))  
    {  
        cout << "Failed to get ICommandText interface.\n";  
        // Release any references and return.  
        goto Exit;  
    } //end if  
  
    // Create table with image column and index.  
    hr = CreateTable(pICommandText);  
    if (FAILED(hr))  
    {  
        cout << "Failed to create table.\n";  
        // Release any references and return.  
        goto Exit;  
    } //end if  
  
    /*  
    Set the DBPROPSET structure.  It is used to pass an array   
    of DBPROP structures to SetProperties().  
    */  
    rgPropSets[0].guidPropertySet = DBPROPSET_ROWSET;  
    rgPropSets[0].cProperties = cProperties;  
    rgPropSets[0].rgProperties = rgProperties;  
  
    // Now set properties in the property group (DBPROPSET_ROWSET).  
    rgPropSets[0].rgProperties[0].dwPropertyID = DBPROP_UPDATABILITY;  
    rgPropSets[0].rgProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
    rgPropSets[0].rgProperties[0].dwStatus = DBPROPSTATUS_OK;  
    rgPropSets[0].rgProperties[0].colid = DB_NULLID;  
    rgPropSets[0].rgProperties[0].vValue.vt = VT_I4;  
    V_I4(&rgPropSets[0].rgProperties[0].vValue) = DBPROPVAL_UP_CHANGE;  
  
    // Set the rowset properties.  
    hr = pICommandText->QueryInterface(IID_ICommandProperties,  
                            (void **)&pICommandProperties);  
    if (FAILED(hr))  
    {  
        cout << "Failed to get ICommandProperties to set rowset properties.\n";  
        // Release any references and return.  
        goto Exit;  
    } //end if  
    hr = pICommandProperties->SetProperties(cPropSets, rgPropSets);  
    if (FAILED(hr))  
    {  
        cout << "Execute failed to set rowset properties.\n";  
        // Release any references and return.  
        goto Exit;  
    } //end if  
  
    // Execute a command (SELECT * FROM TestISeqStream).  
    hr = pICommandText->SetCommandText(DBGUID_DBSQL,  
                                       L"SELECT * FROM TestISeqStream");  
    if (FAILED(hr))  
    {  
        cout << "Failed to set command text SELECT * FROM.\n";  
        // Release any references and return.  
        goto Exit;  
    } //end if  
  
    hr = pICommandText->Execute(NULL, IID_IRowsetChange, NULL, NULL,  
                                (IUnknown**)&pIRowsetChange);  
    if (FAILED(hr))  
    {  
        cout << "Failed to execute the command SELECT * FROM.\n";  
        // Release any references and return.  
        goto Exit;  
    } //end if  
  
    // Fill the DBBINDINGS array.  
    rgBindings[0].iOrdinal = 2; //ordinal position  
    rgBindings[0].obValue = offsetof(BLOBDATA, pISeqStream);  
    rgBindings[0].obLength = offsetof(BLOBDATA, dwLength);  
    rgBindings[0].obStatus = offsetof(BLOBDATA, dwStatus);  
    rgBindings[0].pTypeInfo = NULL;  
    rgBindings[0].pObject = &ObjectStruct;  
    rgBindings[0].pBindExt = NULL;  
    rgBindings[0].dwPart =  DBPART_VALUE | DBPART_STATUS | DBPART_LENGTH;  
    rgBindings[0].dwMemOwner = DBMEMOWNER_CLIENTOWNED;  
    rgBindings[0].eParamIO = DBPARAMIO_NOTPARAM;  
    rgBindings[0].cbMaxLen = 0;   
    rgBindings[0].dwFlags = 0;  
    rgBindings[0].wType = DBTYPE_IUNKNOWN;  
    rgBindings[0].bPrecision = 0;  
    rgBindings[0].bScale = 0;  
  
    // Create an accessor using the binding information.  
    hr = pIRowsetChange->QueryInterface(IID_IAccessor,   
                                        (void**)&pIAccessor);  
    if (FAILED(hr))  
    {  
        cout << "Failed to get IAccessor interface.\n";  
        // Release any references and return.  
        goto Exit;  
    } //end if  
  
    hr = pIAccessor->CreateAccessor(DBACCESSOR_ROWDATA,  
                                    cBindings,  
                                    rgBindings,   
                                    sizeof(BLOBDATA),  
                                    &hAccessor,  
                                    rgBindStatus);  
    if (FAILED(hr))  
    {  
        cout << "Failed to create an accessor.\n";  
        // Release any references and return.  
        goto Exit;  
    } //end if   
  
    // Now get the first row.  
    hr = pIRowsetChange->QueryInterface(IID_IRowset,   
                                        (void **)&pIRowset);  
    if (FAILED(hr))  
    {  
        cout << "Failed to get IRowset interface.\n";  
        // Release any references and return.  
        goto Exit;  
    } //end if  
  
    hr = pIRowset->GetNextRows(NULL,   
                               0,   
                               1,   
                               &cRowsObtained,   
                               &rghRows);  
  
    hr = pIRowset->GetData(rghRows[0],   
                           hAccessor,   
                           &BLOBGetData);  
  
    // Verify the retrieved data, only if data is not null.  
    if (BLOBGetData.dwStatus == DBSTATUS_S_ISNULL)  
    {  
        // Process null data.  
        cout << "Provider returned a null value.\n";  
    } else if(BLOBGetData.dwStatus == DBSTATUS_S_OK)   
      // Provider returned a nonNULL value.  
    {  
        BLOBGetData.pISeqStream->Read(  
                                    pBuffer,   
                                    cBytes,   
                                    &cBytesRead);  
        if(memcmp(pBuffer, pReadData, cBytes) != 0)  
        {  
            //cleanup   
         }  
  
        SAFE_RELEASE(BLOBGetData.pISeqStream);  
    }  
  
    // Set up data for SetData.  
    pMySeqStream = new CSeqStream();  
  
    /*  
    Put data in to the ISequentialStream object   
    for the provider to write.  
    */  
    pMySeqStream->Write(pWriteData,   
                        cBytes,   
                        NULL);  
  
    BLOBSetData.pISeqStream = (ISequentialStream*)pMySeqStream;  
    BLOBSetData.dwStatus    = DBSTATUS_S_OK;  
    BLOBSetData.dwLength    = pMySeqStream->Length();  
  
    // Set the data.  
    hr = pIRowsetChange->SetData(rghRows[0],   
                                 hAccessor,   
                                 &BLOBSetData);  
        if (FAILED(hr))  
    {  
        cout << "Failed to set data.\n";  
        // Release any references and return.  
        goto Exit;  
    } //end if  
  
    hr = pIAccessor->ReleaseAccessor(hAccessor, NULL);  
    if (FAILED(hr))  
    {  
        cout << "Failed to release accessor.\n";  
        // Release any references and return.  
        goto Exit;  
    } //end if  
    hr = pIRowset->ReleaseRows(cRowsObtained,   
                            rghRows,   
                            NULL,   
                            NULL,   
                            NULL);  
    if (FAILED(hr))  
    {  
        cout << "Failed to release rows.\n";  
        // Release any references and return.  
        goto Exit;  
    } //end if  
Exit:  
    // Free up all allocated memory and release interface pointers.  
  
    CoUninitialize();  
} //end main.  
//..........................................................  
HRESULT GetCommandObject(REFIID riid, IUnknown** ppIUnknown)  
{  
    HRESULT hr = S_OK;  
  
    // Local interface pointers, until a connection is made.  
    IDBInitialize* pIDBInitialize = NULL;  
    IDBProperties*  pIDBProperties = NULL;  
    IDBCreateSession* pIDBCreateSession = NULL;  
    IDBCreateCommand* pIDBCreateCommand = NULL;  
  
    const ULONG cPropSets = 1;  
    DBPROPSET rgPropSets[cPropSets];  
  
    const ULONG cProperties = 4;  
    DBPROP rgProperties[cProperties];  
  
    /*  
    Initialize the property values needed to   
    establish the connection.  
    */  
    for(ULONG i = 0; i < 4; i++)  
        VariantInit(&rgProperties[i].vValue);  
  
    // Server name.  
    rgProperties[0].dwPropertyID = DBPROP_INIT_DATASOURCE;  
    rgProperties[0].vValue.vt = VT_BSTR;  
    rgProperties[0].vValue.bstrVal =   
                    SysAllocString(L"server");  
    rgProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
    rgProperties[0].colid = DB_NULLID;  
  
    // Database.  
    rgProperties[1].dwPropertyID = DBPROP_INIT_CATALOG;  
    rgProperties[1].vValue.vt = VT_BSTR;  
    rgProperties[1].vValue.bstrVal =   
                    SysAllocString(L"pubs");  
    rgProperties[1].dwOptions = DBPROPOPTIONS_REQUIRED;  
    rgProperties[1].colid = DB_NULLID;  
  
    // Username (login).  
    rgProperties[2].dwPropertyID = DBPROP_AUTH_USERID;  
    rgProperties[2].vValue.vt = VT_BSTR;  
    rgProperties[2].vValue.bstrVal =   
                    SysAllocString(L"login");  
    rgProperties[2].dwOptions = DBPROPOPTIONS_REQUIRED;  
    rgProperties[2].colid = DB_NULLID;  
  
    // Password.  
    rgProperties[3].dwPropertyID = DBPROP_AUTH_PASSWORD;  
    rgProperties[3].vValue.vt = VT_BSTR;  
    rgProperties[3].vValue.bstrVal =   
                    SysAllocString(L"password");  
    rgProperties[3].dwOptions = DBPROPOPTIONS_REQUIRED;  
    rgProperties[3].colid = DB_NULLID;  
  
    /*  
    Now that the properties are set, construct the DBPROPSET   
    structure (rgInitPropSet).  The DBPROPSET structure is used   
    to pass an array of DBPROP structures (InitProperties) to the   
    SetProperties method.  
    */  
    rgPropSets[0].guidPropertySet   = DBPROPSET_DBINIT;  
    rgPropSets[0].cProperties       = cProperties;  
    rgPropSets[0].rgProperties      = rgProperties;  
  
    // Get the IDBInitialize interface.  
    hr = CoCreateInstance(CLSID_SQLNCLI10,   
                            NULL,   
                            CLSCTX_INPROC_SERVER,  
                            IID_IDBInitialize,   
                            (void**)&pIDBInitialize);  
    if(FAILED(hr))  
    {  
        cout << "Failed to get IDBInitialize interface.\n";  
        // Release any references and return.  
        goto Exit;  
  
    } //end if  
  
    // Set initialization properties.  
    hr = pIDBInitialize->QueryInterface(IID_IDBProperties,  
                                        (void **)&pIDBProperties);  
    if(FAILED(hr))  
    {  
        cout << "Failed to get IDBProperties interface.\n";  
        // Release any references and return.  
        goto Exit;  
    } //end if  
  
    hr = pIDBProperties->SetProperties(cPropSets, rgPropSets);  
     if(FAILED(hr))  
    {  
        cout << "Failed to set properties for DBPROPSET_DBINIT.\n";  
        // Release any references and return.  
        goto Exit;  
    } //end if  
  
     hr = pIDBInitialize->Initialize();  
      if(FAILED(hr))  
    {  
        cout << "Failed to initialize.\n";  
        // Release any references and return.  
        goto Exit;  
    } // end if  
  
    //Create a session object.  
      hr = pIDBInitialize->QueryInterface(  
                                IID_IDBCreateSession,  
                                (void **)&pIDBCreateSession);  
       if(FAILED(hr))  
    {  
        cout << "Failed to get pIDBCreateSession interface.\n";  
        // Release any references and return.  
        goto Exit;  
    } // end if  
  
       hr = pIDBCreateSession->CreateSession(  
                                    NULL,   
                                    IID_IDBCreateCommand,  
                                    (IUnknown**)&pIDBCreateCommand);  
     if(FAILED(hr))  
    {  
        cout << "Failed to create session object.\n";  
        // Release any references and return.  
        goto Exit;  
    } // end if  
  
     // Get the CommandText object.  
     hr = pIDBCreateCommand->CreateCommand(  
                                    NULL,   
                                    riid,   
                                    (IUnknown**)ppIUnknown);  
     if(FAILED(hr))  
    {  
        cout << "Failed to create CommandText object.\n";  
        // Release any references and return.  
        goto Exit;  
    } // end if  
  
     return hr;  
Exit:  
    // Free up all allocated memory and release interface pointers.  
     return hr;  
  
} //end function  
//...............................................................  
HRESULT CreateTable(ICommandText* pICommandText)  
{  
    HRESULT hr = S_OK;  
  
    // Drop the xisting table.  
    hr = pICommandText->SetCommandText(  
                            DBGUID_DBSQL,  
                            L"DROP TABLE TestISeqStream");  
    if(FAILED(hr))  
    {  
        cout << "Failed to set command text DROP TABLE.\n";  
        // Release any references and return.  
        goto Exit;  
  
    } //end if  
  
    hr = pICommandText->Execute(NULL, IID_NULL, NULL, NULL, NULL);  
    if(FAILED(hr))  
    {  
        cout << "Failed to drop the table.\n";  
        // Release any references and return.  
        goto Exit;  
    } // end if  
  
    // Create a new table.  
    hr = pICommandText->SetCommandText(DBGUID_DBSQL,  
         L"CREATE TABLE TestISeqStream (col1 int,col2 image)");  
    if(FAILED(hr))  
    {  
        cout << "Failed to set command text CREATE TABLE.\n";  
        // Release any references and return.  
        goto Exit;  
    } // end if  
  
    hr = pICommandText->Execute(NULL, IID_NULL, NULL, NULL, NULL);  
    if(FAILED(hr))  
    {  
        cout << "Failed to create new table.\n";  
        // Release any references and return.  
        goto Exit;  
    } // end if  
  
    // Insert one row into table.  
    hr = pICommandText->SetCommandText(DBGUID_DBSQL,  
    L"INSERT INTO TestISeqStream(col1,col2) VALUES (1,0xAAAAAAAAAAAAAAAAA)");  
    if(FAILED(hr))  
    {  
        cout << "Failed to set command text INSERT INTO.\n";  
        // Release any references and return.  
        goto Exit;  
    } // end if  
  
    hr = pICommandText->Execute(NULL, IID_NULL, NULL, NULL, NULL);  
    if(FAILED(hr))  
    {  
        cout << "Failed to insert record in the table.\n";  
        // Release any references and return.  
        goto Exit;  
    } // end if  
  
Exit:  
    // Free up all allocated memory and release interface pointers.  
     return hr;  
  
} //end function  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ef2c-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5ef2c-128">See Also</span></span>  
 <span data-ttu-id="5ef2c-129">[Blob 및 OLE 개체](blobs-and-ole-objects.md) </span><span class="sxs-lookup"><span data-stu-id="5ef2c-129">[BLOBs and OLE Objects](blobs-and-ole-objects.md) </span></span>  
 [<span data-ttu-id="5ef2c-130">큰 값 형식 사용</span><span class="sxs-lookup"><span data-stu-id="5ef2c-130">Using Large Value Types</span></span>](../native-client/features/using-large-value-types.md)  
  
  
