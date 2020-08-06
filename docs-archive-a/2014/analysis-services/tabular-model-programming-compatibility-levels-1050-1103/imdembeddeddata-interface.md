---
title: IMDEmbedded 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 9dba8c68-4bef-4c2b-815c-c286f1a1939b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 331f8c33f7748e6591acd6d6ecda7a03ef7d8137
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649229"
---
# <a name="imdembedded-interface"></a><span data-ttu-id="9b1f1-102">IMDEmbedded 인터페이스</span><span class="sxs-lookup"><span data-stu-id="9b1f1-102">IMDEmbedded Interface</span></span>
  <span data-ttu-id="9b1f1-103">IMDEmbedded 인터페이스는 포함된 PowerPivot 데이터베이스 또는 테이블 형식 model 데이터베이스를 관리하는 데 사용되는 공용 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-103">The IMDEmbedded interface is a public interface used to manage an embedded PowerPivot database or a tabular model database.</span></span> <span data-ttu-id="9b1f1-104">이 인터페이스는 `IPersistStream` 인터페이스에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-104">The interface inherits from the `IPersistStream` interface.</span></span> <span data-ttu-id="9b1f1-105">이 인터페이스에서는 다음 작업이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-105">The interface allows for the following operations:</span></span>  
  
-   <span data-ttu-id="9b1f1-106">컨테이너 문서의 포함된 스트림에 대한 식별자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-106">Get an identifier to the embedded stream in the container document.</span></span>  
  
-   <span data-ttu-id="9b1f1-107">포함하는 문서의 URL을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-107">Set the URL of the containing document.</span></span>  
  
-   <span data-ttu-id="9b1f1-108">포함하는 애플리케이션이 호스팅된 환경에 있는지 여부를 나타내는 플래그를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-108">Set a flag to indicate if the embedding application is in a hosted environment.</span></span>  
  
-   <span data-ttu-id="9b1f1-109">포함하는 애플리케이션에 사용되는 임시 파일에 대한 경로를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-109">Set the path to temporary files used by the embedding application.</span></span>  
  
-   <span data-ttu-id="9b1f1-110">현재 포함된 작업을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-110">Cancel the current embedded operation.</span></span>  
  
-   <span data-ttu-id="9b1f1-111">포함된 개체를 저장하기 위해 스트림의 예상 크기(바이트)를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-111">Get the estimated size (in bytes) of the stream to save the embedded object.</span></span> <span data-ttu-id="9b1f1-112">`IPersistStream`에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-112">Inherited from `IPersistStream`.</span></span>  
  
-   <span data-ttu-id="9b1f1-113">포함된 데이터베이스가 마지막으로 저장된 후에 변경되었는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-113">Verify if the embedded database has changed since it was last saved.</span></span> <span data-ttu-id="9b1f1-114">`IPersistStream`에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-114">Inherited from `IPersistStream`.</span></span>  
  
-   <span data-ttu-id="9b1f1-115">포함된 데이터베이스를 로컬 또는 in-process 엔진에 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-115">Load the embedded database to the local or in-process engine.</span></span> <span data-ttu-id="9b1f1-116">`IPersistStream`에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-116">Inherited from `IPersistStream`.</span></span>  
  
-   <span data-ttu-id="9b1f1-117">로컬 또는 in-process 데이터베이스를 컨테이너 문서의 포함된 스트림에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-117">Save the local or in-process database to the embedded stream in the container document.</span></span> <span data-ttu-id="9b1f1-118">`IPersistStream`에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-118">Inherited from `IPersistStream`.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9b1f1-119">참조</span><span class="sxs-lookup"><span data-stu-id="9b1f1-119">Reference</span></span>  
 <span data-ttu-id="9b1f1-120">다음 참조는 `IMDEmbedded` **상수가 msmd.h** 헤더 파일에 표시 된 인터페이스를 문서화 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-120">The following reference documents the `IMDEmbedded` interface as presented in **msmd.h** header file.</span></span>  
  
### <a name="source-file-pxoembeddeddataidl"></a><span data-ttu-id="9b1f1-121">원본 파일: PXOEmbeddedData.idl</span><span class="sxs-lookup"><span data-stu-id="9b1f1-121">Source file: PXOEmbeddedData.idl</span></span>  
  
```  
[  
  local,                            
  object,                           
  uuid(6B6691CF-5453-41c2-ADD9-4F320B7FD421),                       
  pointer_default(unique)           
]  
interface IMDEmbeddedData : IPersistStream  
{  
 [id(1), helpstring("Set flag indicating if the application is in a hosted environment")]   
 HRESULT SetHosted(  
  [in] BOOL in_fIsHosted);  
  
 [id(2), helpstring("Set the URL for the document containing the embedded stream")]   
 HRESULT SetContainerURL(  
  [in] BSTR in_bstrURL);  
  
 [id(3), helpstring("Get identifier used to look up embedded stream in container document")]   
 HRESULT GetStreamIdentifier(  
  [out, retval] BSTR* out_pbstrStreamId);  
  
 [id(4), helpstring("Set the path used by the embedding application for temporary files")]   
 HRESULT SetTempDirPath(  
  [in]  BSTR in_bstrPath);  
  
 [id(5), helpstring("Cancel the current operation")]   
 HRESULT Cancel();  
};  
```  
  
### <a name="imdembeddeddatagetstreamidentifier"></a><span data-ttu-id="9b1f1-122">IMDEmbeddedData::GetStreamIdentifier</span><span class="sxs-lookup"><span data-stu-id="9b1f1-122">IMDEmbeddedData::GetStreamIdentifier</span></span>  
  
```  
HRESULT GetStreamIdentifier (  
    [out, retval] BSTR * out_pbstrStreamId  
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="9b1f1-123">Description</span><span class="sxs-lookup"><span data-stu-id="9b1f1-123">Description</span></span>  
 <span data-ttu-id="9b1f1-124">호스트 애플리케이션에 사용되는 식별자를 컨테이너 문서의 포함된 스트림에 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-124">Gets the identifier used by the host application to the embedded stream in the container document.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="9b1f1-125">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9b1f1-125">Parameters</span></span>  
 <span data-ttu-id="9b1f1-126">*out_pbstrStreamId*</span><span class="sxs-lookup"><span data-stu-id="9b1f1-126">*out_pbstrStreamId*</span></span>  
 <span data-ttu-id="9b1f1-127">스트림 식별자의 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-127">Specifies the location of the stream identifier.</span></span>  
  
#### <a name="return-value"></a><span data-ttu-id="9b1f1-128">Return Value</span><span class="sxs-lookup"><span data-stu-id="9b1f1-128">Return Value</span></span>  
 `S_OK`  
 <span data-ttu-id="9b1f1-129">스트림 식별자가 반환되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-129">The stream identifier was successfully returned.</span></span>  
  
 `S_FALSE`  
 <span data-ttu-id="9b1f1-130">스트림 식별자가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-130">There is no stream identifier.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="9b1f1-131">스트림 식별자에 액세스하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-131">An error occurred accessing the stream identifier.</span></span>  
  
#### <a name="remarks"></a><span data-ttu-id="9b1f1-132">설명</span><span class="sxs-lookup"><span data-stu-id="9b1f1-132">Remarks</span></span>  
 <span data-ttu-id="9b1f1-133">현재 연결에 포함된 데이터베이스가 포함되어 있는지 확인하려면 OLE DB 연결 속성에서 DBPROP_MSMD_EMBEDDED_DATA 속성 값을 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-133">To verify if the current connection contains an embedded database, the user should check the value of the DBPROP_MSMD_EMBEDDED_DATA property from the OLE DB connection properties.</span></span>  
  
 <span data-ttu-id="9b1f1-134">DBPROP_MSMD_EMBEDDED_DATA의 가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-134">The possible values for DBPROP_MSMD_EMBEDDED_DATA are:</span></span>  
  
|<span data-ttu-id="9b1f1-135">Name</span><span class="sxs-lookup"><span data-stu-id="9b1f1-135">Name</span></span>|<span data-ttu-id="9b1f1-136">값</span><span class="sxs-lookup"><span data-stu-id="9b1f1-136">Value</span></span>|<span data-ttu-id="9b1f1-137">정의</span><span class="sxs-lookup"><span data-stu-id="9b1f1-137">Definition</span></span>|  
|----------|-----------|----------------|  
|<span data-ttu-id="9b1f1-138">DBPROPVAL_EMBED_NONE</span><span class="sxs-lookup"><span data-stu-id="9b1f1-138">DBPROPVAL_EMBED_NONE</span></span>|<span data-ttu-id="9b1f1-139">0x00</span><span class="sxs-lookup"><span data-stu-id="9b1f1-139">0x00</span></span>|<span data-ttu-id="9b1f1-140">포함된 데이터베이스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-140">No embedded database available</span></span>|  
|<span data-ttu-id="9b1f1-141">DBPROPVAL_EMBED_EMBEDDED</span><span class="sxs-lookup"><span data-stu-id="9b1f1-141">DBPROPVAL_EMBED_EMBEDDED</span></span>|<span data-ttu-id="9b1f1-142">0x01</span><span class="sxs-lookup"><span data-stu-id="9b1f1-142">0x01</span></span>|<span data-ttu-id="9b1f1-143">현재 애플리케이션에 포함된 데이터베이스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-143">The current application contains the embedded database</span></span>|  
|<span data-ttu-id="9b1f1-144">DBPROPVAL_EMBED_LINKED</span><span class="sxs-lookup"><span data-stu-id="9b1f1-144">DBPROPVAL_EMBED_LINKED</span></span>|<span data-ttu-id="9b1f1-145">0x02</span><span class="sxs-lookup"><span data-stu-id="9b1f1-145">0x02</span></span>|<span data-ttu-id="9b1f1-146">포함된 데이터베이스가 원격 애플리케이션(예: SharePoint Server)에서 호스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-146">The embedded database is hosted in a remote application (i.e. SharePoint Server)</span></span>|  
  
#### <a name="source"></a><span data-ttu-id="9b1f1-147">원본</span><span class="sxs-lookup"><span data-stu-id="9b1f1-147">Source</span></span>  
  
```  
[id(1), helpstring("Get identifier used to look up embedded stream in container document")]   
 HRESULT GetStreamIdentifier(  
  [out, retval] BSTR* out_pbstrStreamId);  
```  
  
### <a name="imdembeddeddatasetcontainerurl"></a><span data-ttu-id="9b1f1-148">IMDEmbeddedData::SetContainerURL</span><span class="sxs-lookup"><span data-stu-id="9b1f1-148">IMDEmbeddedData::SetContainerURL</span></span>  
  
```  
HRESULT SetContainerURL (  
    [in] BSTR in_bstrURL  
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="9b1f1-149">Description</span><span class="sxs-lookup"><span data-stu-id="9b1f1-149">Description</span></span>  
 <span data-ttu-id="9b1f1-150">포함된 스트림을 포함하는 파일의 URL을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-150">Sets the URL for the file containing the embedded stream.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="9b1f1-151">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9b1f1-151">Parameters</span></span>  
 <span data-ttu-id="9b1f1-152">*in_bstrURL*</span><span class="sxs-lookup"><span data-stu-id="9b1f1-152">*in_bstrURL*</span></span>  
 <span data-ttu-id="9b1f1-153">포함하는 문서의 URL을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-153">Specifies the URL for the containing document.</span></span>  
  
#### <a name="return-value"></a><span data-ttu-id="9b1f1-154">Return Value</span><span class="sxs-lookup"><span data-stu-id="9b1f1-154">Return Value</span></span>  
 `S_OK`  
 <span data-ttu-id="9b1f1-155">컨테이너 URL을 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-155">The container URL was successfully set.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="9b1f1-156">컨테이너 URL을 설정하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-156">An error occurred while setting the container URL.</span></span>  
  
#### <a name="source"></a><span data-ttu-id="9b1f1-157">원본</span><span class="sxs-lookup"><span data-stu-id="9b1f1-157">Source</span></span>  
  
```  
[id(2), helpstring("Set the URL for the document containing the embedded stream")]   
 HRESULT SetContainerURL(  
  [in] BSTR in_bstrURL);  
```  
  
### <a name="imdembeddeddatasethosted"></a><span data-ttu-id="9b1f1-158">IMDEmbeddedData::SetHosted</span><span class="sxs-lookup"><span data-stu-id="9b1f1-158">IMDEmbeddedData::SetHosted</span></span>  
  
```  
HRESULT SetHosted (  
    [in] BOOL in_fIsHosted  
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="9b1f1-159">Description</span><span class="sxs-lookup"><span data-stu-id="9b1f1-159">Description</span></span>  
 <span data-ttu-id="9b1f1-160">포함하는 애플리케이션이 호스팅된 환경에 있는지 여부를 나타내는 플래그를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-160">Set a flag to indicate if the embedding application is in a hosted environment.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="9b1f1-161">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9b1f1-161">Parameters</span></span>  
 <span data-ttu-id="9b1f1-162">*in_ftHosted*</span><span class="sxs-lookup"><span data-stu-id="9b1f1-162">*in_ftHosted*</span></span>  
 <span data-ttu-id="9b1f1-163">호출자가 서비스 애플리케이션(예: IIS)의 호스팅된 환경에 있으면 TRUE입니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-163">TRUE if caller is in a hosted in a service application (like IIS).</span></span>  
  
#### <a name="return-value"></a><span data-ttu-id="9b1f1-164">Return Value</span><span class="sxs-lookup"><span data-stu-id="9b1f1-164">Return Value</span></span>  
 `S_OK`  
 <span data-ttu-id="9b1f1-165">플래그를 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-165">The flag was successfully set.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="9b1f1-166">플래그를 설정하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-166">An error occurred while setting the flag.</span></span>  
  
#### <a name="source"></a><span data-ttu-id="9b1f1-167">원본</span><span class="sxs-lookup"><span data-stu-id="9b1f1-167">Source</span></span>  
  
```  
[id(5), helpstring("Set flag indicating if the application is in a hosted environment")]   
 HRESULT SetHosted(  
  [in]  BOOL in_fIsHosted);  
```  
  
### <a name="imdembeddeddatasettempdirpath"></a><span data-ttu-id="9b1f1-168">IMDEmbeddedData::SetTempDirPath</span><span class="sxs-lookup"><span data-stu-id="9b1f1-168">IMDEmbeddedData::SetTempDirPath</span></span>  
  
```  
HRESULT SetTempDirPath (  
    [in] BSTR in_bstrPath  
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="9b1f1-169">Description</span><span class="sxs-lookup"><span data-stu-id="9b1f1-169">Description</span></span>  
 <span data-ttu-id="9b1f1-170">포함하는 애플리케이션에 사용되는 임시 파일에 대한 경로를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-170">Set the path to temporary files used by the embedding application.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="9b1f1-171">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9b1f1-171">Parameters</span></span>  
 <span data-ttu-id="9b1f1-172">*in_bstrPath*</span><span class="sxs-lookup"><span data-stu-id="9b1f1-172">*in_bstrPath*</span></span>  
 <span data-ttu-id="9b1f1-173">임시 파일에 대한 호스트 애플리케이션에서 사용하는 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-173">The path used by the host application for temporary files.</span></span>  
  
#### <a name="return-value"></a><span data-ttu-id="9b1f1-174">Return Value</span><span class="sxs-lookup"><span data-stu-id="9b1f1-174">Return Value</span></span>  
 `S_OK`  
 <span data-ttu-id="9b1f1-175">임시 파일 디렉터리를 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-175">The temporary file directory was successfully set.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="9b1f1-176">경로를 설정하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-176">An error occurred while setting the path.</span></span>  
  
#### <a name="source"></a><span data-ttu-id="9b1f1-177">원본</span><span class="sxs-lookup"><span data-stu-id="9b1f1-177">Source</span></span>  
  
```  
[id(4), helpstring("Set the path used by the host application for temporary files")]   
 HRESULT SetTempDirPath(  
  [in]  BSTR in_bstrPath);  
```  
  
### <a name="imdembeddeddatacancel"></a><span data-ttu-id="9b1f1-178">IMDEmbeddedData::Cancel</span><span class="sxs-lookup"><span data-stu-id="9b1f1-178">IMDEmbeddedData::Cancel</span></span>  
  
```  
HRESULT Cancel ( void )  
```  
  
#### <a name="description"></a><span data-ttu-id="9b1f1-179">Description</span><span class="sxs-lookup"><span data-stu-id="9b1f1-179">Description</span></span>  
 <span data-ttu-id="9b1f1-180">현재 포함된 데이터베이스 작업을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-180">Cancels the current embedded database operation</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="9b1f1-181">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9b1f1-181">Parameters</span></span>  
 <span data-ttu-id="9b1f1-182">없음</span><span class="sxs-lookup"><span data-stu-id="9b1f1-182">None.</span></span>  
  
#### <a name="return-value"></a><span data-ttu-id="9b1f1-183">Return Value</span><span class="sxs-lookup"><span data-stu-id="9b1f1-183">Return Value</span></span>  
 `S_OK`  
 <span data-ttu-id="9b1f1-184">작업을 취소했습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-184">The operation was successfully cancelled.</span></span>  
  
 `DB_E_CANTCANCEL`  
 <span data-ttu-id="9b1f1-185">취소할 수 없는 작업이 현재 진행 중입니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-185">No cancellable operation is currently in progress.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="9b1f1-186">포함된 작업을 취소하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-186">An error occurred while cancelling the embedded operation.</span></span>  
  
#### <a name="source"></a><span data-ttu-id="9b1f1-187">원본</span><span class="sxs-lookup"><span data-stu-id="9b1f1-187">Source</span></span>  
  
```  
[id(5), helpstring("Cancel the current operation")]   
 HRESULT Cancel();  
```  
  
### <a name="imdembeddeddatagetsizemax-ipersiststreamgetsizemax"></a><span data-ttu-id="9b1f1-188">IMDEmbeddedData::GetSizeMax (IPersistStream::GetSizeMax)</span><span class="sxs-lookup"><span data-stu-id="9b1f1-188">IMDEmbeddedData::GetSizeMax (IPersistStream::GetSizeMax)</span></span>  
  
```  
HRESULT GetSizeMax (  
    [out] ULARGE_INTEGER * out_pcbSize  
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="9b1f1-189">Description</span><span class="sxs-lookup"><span data-stu-id="9b1f1-189">Description</span></span>  
 <span data-ttu-id="9b1f1-190">포함된 개체를 저장하기 위해 스트림의 예상 크기(바이트)를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-190">Gets the estimated size (in bytes) of the stream to save the embedded object.</span></span> <span data-ttu-id="9b1f1-191">`IPersistStream`에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-191">Inherited from `IPersistStream`.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="9b1f1-192">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9b1f1-192">Parameters</span></span>  
 <span data-ttu-id="9b1f1-193">*in_bstrPath*</span><span class="sxs-lookup"><span data-stu-id="9b1f1-193">*in_bstrPath*</span></span>  
 <span data-ttu-id="9b1f1-194">포함된 데이터베이스 이미지의 예상 크기(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-194">The estimated size (in bytes) of the embedded database image.</span></span>  
  
#### <a name="return-value"></a><span data-ttu-id="9b1f1-195">Return Value</span><span class="sxs-lookup"><span data-stu-id="9b1f1-195">Return Value</span></span>  
 `S_OK`  
 <span data-ttu-id="9b1f1-196">크기를 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-196">The size was successfully obtained.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="9b1f1-197">크기를 가져오는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-197">An error occurred while obtaining the size.</span></span>  
  
### <a name="imdembeddeddataisdirty-ipersiststreamisdirty"></a><span data-ttu-id="9b1f1-198">IMDEmbeddedData::IsDirty (IPersistStream::IsDirty)</span><span class="sxs-lookup"><span data-stu-id="9b1f1-198">IMDEmbeddedData::IsDirty (IPersistStream::IsDirty)</span></span>  
  
```  
HRESULT IsDirty ( void )  
```  
  
#### <a name="description"></a><span data-ttu-id="9b1f1-199">Description</span><span class="sxs-lookup"><span data-stu-id="9b1f1-199">Description</span></span>  
 <span data-ttu-id="9b1f1-200">포함된 데이터베이스가 마지막으로 저장된 후에 변경되었는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-200">Verifies if the embedded database has changed since it was last saved.</span></span> <span data-ttu-id="9b1f1-201">`IPersistStream`에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-201">Inherited from `IPersistStream`.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="9b1f1-202">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9b1f1-202">Parameters</span></span>  
 <span data-ttu-id="9b1f1-203">none</span><span class="sxs-lookup"><span data-stu-id="9b1f1-203">none</span></span>  
  
#### <a name="return-values"></a><span data-ttu-id="9b1f1-204">반환 값</span><span class="sxs-lookup"><span data-stu-id="9b1f1-204">Return Value(s)</span></span>  
 `S_OK`  
 <span data-ttu-id="9b1f1-205">데이터베이스가 마지막으로 저장된 후에 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-205">The database has changed since it was last saved.</span></span>  
  
 `S_FALSE`  
 <span data-ttu-id="9b1f1-206">데이터베이스가 마지막으로 저장된 후에 변경되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-206">The database has not changed since it was last saved.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="9b1f1-207">데이터베이스 상태를 가져오는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-207">An error occurred while obtaining the database state.</span></span>  
  
### <a name="imdembeddeddataload-ipersiststreamload"></a><span data-ttu-id="9b1f1-208">IMDEmbeddedData::Load (IPersistStream::Load)</span><span class="sxs-lookup"><span data-stu-id="9b1f1-208">IMDEmbeddedData::Load (IPersistStream::Load)</span></span>  
  
```  
HRESULT Load (   
    [in] IStream * in_pStm   
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="9b1f1-209">Description</span><span class="sxs-lookup"><span data-stu-id="9b1f1-209">Description</span></span>  
 <span data-ttu-id="9b1f1-210">포함된 데이터베이스를 로컬 또는 in-process 엔진에 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-210">Loads the embedded database to the local or in-process engine.</span></span> <span data-ttu-id="9b1f1-211">`IPersistStream`에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-211">Inherited from `IPersistStream`.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="9b1f1-212">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9b1f1-212">Parameters</span></span>  
 <span data-ttu-id="9b1f1-213">*in_pStm*</span><span class="sxs-lookup"><span data-stu-id="9b1f1-213">*in_pStm*</span></span>  
 <span data-ttu-id="9b1f1-214">포함된 데이터베이스를 로드할 스트림 인터페이스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-214">A pointer to a stream interface from where to load the embedded database.</span></span>  
  
#### <a name="return-values"></a><span data-ttu-id="9b1f1-215">반환 값</span><span class="sxs-lookup"><span data-stu-id="9b1f1-215">Return Value(s)</span></span>  
 `S_OK`  
 <span data-ttu-id="9b1f1-216">데이터베이스를 로드했습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-216">The database was successfully loaded.</span></span>  
  
 `E_OUTOFMEMORY`  
 <span data-ttu-id="9b1f1-217">메모리가 부족하여 데이터베이스를 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-217">Not enough memory to load the database.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="9b1f1-218">데이터베이스를 로드하는 동안 오류가 발생했습니다. `E_OUTOFMEMORY`와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-218">An error occurred while loading the database, different than `E_OUTOFMEMORY`.</span></span>  
  
### <a name="imdembeddeddatasave-ipersiststreamsave"></a><span data-ttu-id="9b1f1-219">IMDEmbeddedData::Save (IPersistStream::Save)</span><span class="sxs-lookup"><span data-stu-id="9b1f1-219">IMDEmbeddedData::Save (IPersistStream::Save)</span></span>  
  
```  
HRESULT Save (   
    [in] IStream * in_pStm,  
    [in] BOOL in_fClearDirty  
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="9b1f1-220">Description</span><span class="sxs-lookup"><span data-stu-id="9b1f1-220">Description</span></span>  
 <span data-ttu-id="9b1f1-221">로컬 또는 in-process 데이터베이스를 컨테이너 문서의 포함된 스트림에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-221">Saves the local or in-process database to the embedded stream in the container document.</span></span> <span data-ttu-id="9b1f1-222">`IPersistStream`에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-222">Inherited from `IPersistStream`.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="9b1f1-223">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9b1f1-223">Parameters</span></span>  
 <span data-ttu-id="9b1f1-224">*in_pStm*</span><span class="sxs-lookup"><span data-stu-id="9b1f1-224">*in_pStm*</span></span>  
 <span data-ttu-id="9b1f1-225">포함된 데이터베이스를 저장할 스트림 인터페이스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-225">A pointer to a stream interface to where to save the embedded database.</span></span>  
  
 <span data-ttu-id="9b1f1-226">*in_fClearDirty*</span><span class="sxs-lookup"><span data-stu-id="9b1f1-226">*in_fClearDirty*</span></span>  
 <span data-ttu-id="9b1f1-227">이 작업 후에 변경 플래그를 지워야 하는지 여부를 나타내는 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-227">A flag that indicates whether the dirty flag should be cleared after this operation.</span></span>  
  
#### <a name="return-values"></a><span data-ttu-id="9b1f1-228">반환 값</span><span class="sxs-lookup"><span data-stu-id="9b1f1-228">Return Value(s)</span></span>  
 `S_OK`  
 <span data-ttu-id="9b1f1-229">데이터베이스를 저장했습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-229">The database was successfully saved.</span></span>  
  
 `STG_E_CANTSAVE`  
 <span data-ttu-id="9b1f1-230">데이터베이스를 저장하는 동안 오류가 발생했습니다. `STG_E_MEDIUMFULL`과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-230">An error occurred while saving the database, different than `STG_E_MEDIUMFULL`.</span></span>  
  
 `STG_E_MEDIUMFULL`  
 <span data-ttu-id="9b1f1-231">스토리지 디바이스에 남아 있는 공간이 없으므로 데이터베이스를 스토리지할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1f1-231">The database could not be saved because there is no space left on the storage device.</span></span>  
  
  
