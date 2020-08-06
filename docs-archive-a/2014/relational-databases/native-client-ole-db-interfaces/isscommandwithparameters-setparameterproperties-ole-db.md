---
title: ISSCommandWithParameters::SetParameterProperties(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSCommandWithParameters::SetParameterProperties (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- SetParameterProperties method
ms.assetid: 4cd0281a-a2a0-43df-8e46-eb478b64cb4b
author: rothja
ms.author: jroth
ms.openlocfilehash: 4bf8e5cde9885a5d9b55d84c6384b76aecf50b8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729435"
---
# <a name="isscommandwithparameterssetparameterproperties-ole-db"></a><span data-ttu-id="bae83-102">ISSCommandWithParameters::SetParameterProperties(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="bae83-102">ISSCommandWithParameters::SetParameterProperties (OLE DB)</span></span>
  <span data-ttu-id="bae83-103">매개 변수별 서수로 매개 변수 속성을 설정하거나, SSPARAMPROPS 구조의 배열을 지정하여 대량 매개 변수 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-103">Sets the parameter properties on a per parameter basis by ordinal, or sets bulk parameter properties by specifying an array of SSPARAMPROPS structures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bae83-104">구문</span><span class="sxs-lookup"><span data-stu-id="bae83-104">Syntax</span></span>  
  
```  
  
HRESULT SetParameterProperties(  
DB_UPARAMS cParams,   
SSPARAMPROPS rgParamProperties[]);  
```  
  
## <a name="arguments"></a><span data-ttu-id="bae83-105">인수</span><span class="sxs-lookup"><span data-stu-id="bae83-105">Arguments</span></span>  
 <span data-ttu-id="bae83-106">*cParams*[in]</span><span class="sxs-lookup"><span data-stu-id="bae83-106">*cParams*[in]</span></span>  
 <span data-ttu-id="bae83-107">*rgParamProperties* 배열의 SSPARAMPROPS 구조 수입니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-107">The number of SSPARAMPROPS structures in the *rgParamProperties* array.</span></span> <span data-ttu-id="bae83-108">이 숫자가 0 이면는 `ISSCommandWithParameters::SetParameterProperties` 명령의 모든 매개 변수에 대해 지정 되었을 수 있는 모든 속성을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-108">If this number is zero, `ISSCommandWithParameters::SetParameterProperties` will delete all properties that might have been specified for any parameters in the command.</span></span>  
  
 <span data-ttu-id="bae83-109">*rgParamProperties*[in]</span><span class="sxs-lookup"><span data-stu-id="bae83-109">*rgParamProperties*[in]</span></span>  
 <span data-ttu-id="bae83-110">설정할 SSPARAMPROPS 구조의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-110">An array of SSPARAMPROPS structures to be set.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="bae83-111">반환 코드 값</span><span class="sxs-lookup"><span data-stu-id="bae83-111">Return Code Values</span></span>  
 <span data-ttu-id="bae83-112">`ISSCommandWithParameters::SetParameterProperties`메서드는 core OLE DB **ICommandProperties:: SetProperties** 메서드와 동일한 오류 코드를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-112">The `ISSCommandWithParameters::SetParameterProperties` method returns the same error codes as the core OLE DB **ICommandProperties::SetProperties** method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bae83-113">설명</span><span class="sxs-lookup"><span data-stu-id="bae83-113">Remarks</span></span>  
 <span data-ttu-id="bae83-114">이 메서드를 사용 하 여 매개 변수 속성을 설정 하는 것은 매개 변수 별로, 서 수로 설정 하거나, `ISSCommandWithParameters::SetParameterProperties` SSPARAMPROPS가 속성 배열에서 빌드된 후에 한 번 호출 하 여 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-114">Setting parameter properties with this method is allowed on a per parameter basis by ordinal, or with a single `ISSCommandWithParameters::SetParameterProperties` call once the SSPARAMPROPS has been built from the property array.</span></span>  
  
 <span data-ttu-id="bae83-115">메서드를 호출 하기 전에 **SetParameterInfo** 메서드를 호출 해야 합니다 `ISSCommandWithParameters::SetParameterProperties` .</span><span class="sxs-lookup"><span data-stu-id="bae83-115">The **SetParameterInfo** method must be called before calling the `ISSCommandWithParameters::SetParameterProperties` method.</span></span> <span data-ttu-id="bae83-116">`SetParameterProperties(0, NULL)`를 호출하면 지정한 모든 매개 변수 속성이 지워지지만 `SetParameterInfo(0,NULL,NULL)`를 호출하면 매개 변수와 관련이 있을 수 있는 모든 속성을 비롯하여 모든 매개 변수 정보가 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-116">Calling `SetParameterProperties(0, NULL)` clears all specified parameter properties, while calling `SetParameterInfo(0,NULL,NULL)` clears all the parameter info including any properties that might be associated with a parameter.</span></span>  
  
 <span data-ttu-id="bae83-117">`ISSCommandWithParameters::SetParameterProperties`DBTYPE_XML 또는 DBTYPE_UDT 형식이 아닌 매개 변수에 대 한 속성을 지정 하기 위해를 호출 하면 DB_E_ERRORSOCCURRED 또는 DB_S_ERRORSOCCURRED이 반환 되 고 해당 매개 변수에 대 한 SSPARAMPROPS에 포함 된 모든 DBPROPs의 *dwstatus* 필드가 DBPROPSTATUS_NOTSET로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-117">Calling `ISSCommandWithParameters::SetParameterProperties` to specify properties for a parameter which is not of type DBTYPE_XML or DBTYPE_UDT returns DB_E_ERRORSOCCURRED or DB_S_ERRORSOCCURRED and marks the *dwStatus* field of all DBPROPs contained in SSPARAMPROPS for that parameter with DBPROPSTATUS_NOTSET.</span></span> <span data-ttu-id="bae83-118">DB_E_ERRORSOCCURRED 또는 DB_S_ERRORSOCCURRED가 참조하는 매개 변수를 검색하기 위해 SSPARAMPROPS에 포함된 각 DBPROPSET의 DBPROP 배열을 이동해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-118">The DBPROP array of each DBPROPSET contained in SSPARAMPROPS should be traversed to detect which parameter the DB_E_ERRORSOCCURRED or DB_S_ERRORSOCCURRED refers to.</span></span>  
  
 <span data-ttu-id="bae83-119">`ISSCommandWithParameters::SetParameterProperties` **SetParameterInfo**를 사용 하 여 매개 변수 정보가 아직 설정 되지 않은 매개 변수의 속성을 지정 하기 위해가 호출 되는 경우 공급자는 다음과 같은 오류 메시지와 함께 E_UNEXPECTED 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-119">If `ISSCommandWithParameters::SetParameterProperties` is called to specify the properties of parameters whose parameter info have not been set yet with **SetParameterInfo**, the provider returns E_UNEXPECTED with the following error message:</span></span>  
  
 <span data-ttu-id="bae83-120">먼저 SetParameterInfo 메서드를 호출해야만 지정한 매개 변수에 대해 SetParameterProperties 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-120">SetParameterProperties method cannot be called for the specified parameters without first calling SetParameterInfo method.</span></span> <span data-ttu-id="bae83-121">매개 변수 속성을 설정하기 전에 매개 변수 정보를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-121">The parameter information must be set before setting the parameter properties.</span></span>  
  
 <span data-ttu-id="bae83-122">에 대 한 호출에 매개 변수 `ISSCommandWithParameters::SetParameterProperties` 정보가 설정 된 일부 매개 변수가 포함 되어 있고 매개 변수 정보가 설정 되지 않은 일부 매개 변수가 포함 된 경우 SSPARAMPROPS 속성 집합의 DBPROPSET dwStatus 속성은 DBSTATUS_NOTSET로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-122">If the call to `ISSCommandWithParameters::SetParameterProperties` contains some parameters where the parameter info has been set, and some parameters where the parameter info has not been set, the dwStatus properties in the DBPROPSET of the SSPARAMPROPS property set will return with DBSTATUS_NOTSET.</span></span>  
  
 <span data-ttu-id="bae83-123">SSPARAMPROPS 구조는 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-123">The SSPARAMPROPS structure is defined as follows:</span></span>  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
 <span data-ttu-id="bae83-124">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]부터 데이터베이스 엔진의 기능이 향상되어 ISSCommandWithParameters::SetParameterProperties를 통해 예상 결과에 대한 보다 정확한 설명을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-124">Improvements in the database engine starting with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] allow ISSCommandWithParameters::SetParameterProperties to obtain more accurate descriptions of the expected results.</span></span> <span data-ttu-id="bae83-125">보다 정확한 결과는 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 ISSCommandWithParameters::SetParameterProperties가 반환한 값과 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-125">These more accurate results may differ from the values returned by ISSCommandWithParameters::SetParameterProperties in previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bae83-126">자세한 내용은 [메타데이터 검색](../native-client/features/metadata-discovery.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bae83-126">For more information, see [Metadata Discovery](../native-client/features/metadata-discovery.md).</span></span>  
  
|<span data-ttu-id="bae83-127">멤버</span><span class="sxs-lookup"><span data-stu-id="bae83-127">Member</span></span>|<span data-ttu-id="bae83-128">설명</span><span class="sxs-lookup"><span data-stu-id="bae83-128">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="bae83-129">*iOrdinal*</span><span class="sxs-lookup"><span data-stu-id="bae83-129">*iOrdinal*</span></span>|<span data-ttu-id="bae83-130">전달된 매개 변수의 서수입니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-130">The ordinal of the passed parameter.</span></span>|  
|<span data-ttu-id="bae83-131">*cPropertySets*</span><span class="sxs-lookup"><span data-stu-id="bae83-131">*cPropertySets*</span></span>|<span data-ttu-id="bae83-132">*rgPropertySets*에 있는 DBPROPSET 구조의 개수입니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-132">The number of DBPROPSET structures in *rgPropertySets*.</span></span>|  
|<span data-ttu-id="bae83-133">*rgPropertySets*</span><span class="sxs-lookup"><span data-stu-id="bae83-133">*rgPropertySets*</span></span>|<span data-ttu-id="bae83-134">DBPROPSET 구조의 배열을 반환할 메모리에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-134">A pointer to memory in which to return an array of DBPROPSET structures.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bae83-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bae83-135">See Also</span></span>  
 [<span data-ttu-id="bae83-136">ISSCommandWithParameters&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="bae83-136">ISSCommandWithParameters &#40;OLE DB&#41;</span></span>](isscommandwithparameters-ole-db.md)  
  
  
