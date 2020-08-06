---
title: 테이블 반환 매개 변수가 포함된 명령 실행 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, executing commands containing
ms.assetid: 7ecba6f6-fe7a-462a-9aa3-d5115b6d4529
author: rothja
ms.author: jroth
ms.openlocfilehash: e3f616b2b9f95ae558e444bcbdae50eae123fa4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648367"
---
# <a name="executing-commands-containing-table-valued-parameters"></a><span data-ttu-id="24ebb-102">테이블 반환 매개 변수가 포함된 명령 실행</span><span class="sxs-lookup"><span data-stu-id="24ebb-102">Executing Commands Containing Table-Valued Parameters</span></span>
  <span data-ttu-id="24ebb-103">테이블 반환 매개 변수가 포함된 명령을 실행하려면 두 단계가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-103">Executing a command that contains table-valued parameters requires two phases:</span></span>  
  
1.  <span data-ttu-id="24ebb-104">매개 변수 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-104">Specify the parameter types.</span></span>  
  
2.  <span data-ttu-id="24ebb-105">매개 변수 데이터를 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-105">Bind the parameter data.</span></span>  
  
## <a name="table-valued-parameter-specification"></a><span data-ttu-id="24ebb-106">테이블 반환 매개 변수 사양</span><span class="sxs-lookup"><span data-stu-id="24ebb-106">Table-Valued Parameter Specification</span></span>  
 <span data-ttu-id="24ebb-107">소비자는 테이블 반환 매개 변수의 유형을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-107">The consumer can specify the type of the table-valued parameter.</span></span> <span data-ttu-id="24ebb-108">이 정보에는 테이블 반환 매개 변수 유형 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-108">This information includes the table-valued parameter type name.</span></span> <span data-ttu-id="24ebb-109">연결의 현재 기본 스키마에 테이블 반환 매개 변수의 사용자 정의 테이블 형식이 없는 경우에는 스키마 이름도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-109">It also includes the schema name, if the user-defined table type for the table-valued parameter is not in the current default schema for the connection.</span></span> <span data-ttu-id="24ebb-110">서버에서 지원하는 경우 소비자는 열의 순서와 같은 선택적인 메타데이터 정보를 지정할 수 있으며 특정 열의 모든 행이 기본값을 가지도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-110">Depending on server support, the consumer can also specify optional metadata information, such as ordering of columns, and can specify that all rows for particular columns have the default values.</span></span>  
  
 <span data-ttu-id="24ebb-111">테이블 반환 매개 변수를 지정하기 위해 소비자는 ISSCommandWithParameter::SetParameterInfo를 호출하며 ISSCommandWithParameters::SetParameterProperties를 옵션으로 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-111">To specify a table-valued parameter, the consumer calls ISSCommandWithParameter::SetParameterInfo, and optionally calls ISSCommandWithParameters::SetParameterProperties.</span></span> <span data-ttu-id="24ebb-112">테이블 반환 매개 변수에서 DBPARAMBINDINFO 구조의 *pwszDataSourceType* 필드는 DBTYPE_TABLE 값을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-112">For a table-valued parameter, the *pwszDataSourceType* field in the DBPARAMBINDINFO structure has a value of DBTYPE_TABLE.</span></span> <span data-ttu-id="24ebb-113">*ulParamSize* 필드는 길이를 알 수 없음을 나타내기 위해 ~0으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-113">The *ulParamSize* field is set to ~0 to indicate that length is unknown.</span></span> <span data-ttu-id="24ebb-114">스키마 이름, 형식 이름, 열 순서 및 기본 열과 같은 테이블 반환 매개 변수의 특정 속성은 ISSCommandWithParameters::SetParameterProperties를 통해 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-114">Particular properties for table-valued parameters, such as schema name, type name, column order, and default columns, can be set through ISSCommandWithParameters::SetParameterProperties.</span></span>  
  
## <a name="table-valued-parameter-binding"></a><span data-ttu-id="24ebb-115">테이블 반환 매개 변수 바인딩</span><span class="sxs-lookup"><span data-stu-id="24ebb-115">Table-Valued Parameter Binding</span></span>  
 <span data-ttu-id="24ebb-116">테이블 반환 매개 변수는 모든 행 집합 개체가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-116">A table-valued parameter can be any rowset object.</span></span> <span data-ttu-id="24ebb-117">공급자는 실행 중에 서버로 테이블 반환 매개 변수를 보내는 동안 이 개체를 읽어 들입니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-117">The provider reads from this object while sending table-valued parameters to the server during execution.</span></span>  
  
 <span data-ttu-id="24ebb-118">소비자는 테이블 반환 매개 변수를 바인딩하기 위해 IAccessor::CreateAccessor를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-118">To bind the table-valued parameter, the consumer calls IAccessor::CreateAccessor.</span></span> <span data-ttu-id="24ebb-119">테이블 반환 매개 변수의 DBBINDING 구조에 있는 *wType* 필드는 DBTYPE_TABLE로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-119">The *wType* field of the DBBINDING structure for the table-valued parameter is set to DBTYPE_TABLE.</span></span> <span data-ttu-id="24ebb-120">DBBINDING 구조의 *pObject* 멤버는 NULL이 아니며 *pObject*의 *iid* 멤버는 IID_IRowset 또는 다른 테이블 반환 매개 변수 행 집합 개체 인터페이스로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-120">The *pObject* member of the DBBINDING structure is non-NULL, and the *pObject*'s *iid* member is set to IID_IRowset or any other table-valued parameter rowset object interfaces.</span></span> <span data-ttu-id="24ebb-121">DBBINDING 구조의 나머지 필드는 스트림된 BLOB에 설정할 때와 같은 방법으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-121">The remaining fields in the DBBINDING structure should be set the same way they are set for streamed BLOBs.</span></span>  
  
 <span data-ttu-id="24ebb-122">테이블 반환 매개 변수에 대한 바인딩과 테이블 반환 매개 변수와 연결된 행 집합 개체에는 다음과 같은 제한 사항이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-122">In the bindings for the table-valued parameter and the rowset object associated with a table-valued parameter, the following restrictions apply:</span></span>  
  
-   <span data-ttu-id="24ebb-123">테이블 반환 매개 변수 행 집합 열 데이터에는 DBSTATUS_S_ISNULL 및 DBSTATUS_S_OK 상태 값만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-123">The only status values allowed for table-valued parameter rowset column data are DBSTATUS_S_ISNULL and DBSTATUS_S_OK.</span></span> <span data-ttu-id="24ebb-124">DBSTATUS_S_DEFAULT를 사용하면 오류가 발생하며 바인딩된 상태 값은 DBSTATUS_E_BADSTATUS로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-124">DBSTATUS_S_DEFAULT will result in a failure, and the bound status value will be set to DBSTATUS_E_BADSTATUS.</span></span>  
  
-   <span data-ttu-id="24ebb-125">테이블 반환 매개 변수를 DBSTATUS_S_DEFAULT 상태로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-125">A table-valued parameter can be marked with the status DBSTATUS_S_DEFAULT.</span></span> <span data-ttu-id="24ebb-126">유효한 값은 DBSTATUS_S_DEFAULT 및 DBSTATUS_S_OK뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-126">The only valid values are DBSTATUS_S_DEFAULT and DBSTATUS_S_OK.</span></span> <span data-ttu-id="24ebb-127">상태를 DBSTATUS_S_DEFAULT로 설정하면 테이블 반환 매개 변수의 값이 빈 테이블과 같게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-127">When the status is set to DBSTATUS_S_DEFAULT, the value of the table-valued parameter corresponds to an empty table.</span></span>  
  
-   <span data-ttu-id="24ebb-128">테이블 반환 매개 변수의 읽기 전용 열(ID 열 또는 계산 열)은 SSPROP_PARAM_TABLE_DEFAULT_COLUMNS 속성을 사용하여 기본값으로 표시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-128">Read-only columns in table-valued parameters (identity or computed columns) must be marked as default by using the SSPROP_PARAM_TABLE_DEFAULT_COLUMNS property.</span></span> <span data-ttu-id="24ebb-129">기본값을 가지는 열 역시 특정 테이블 반환 매개 변수의 열 데이터 값에 이 기본값이 사용될 수 있도록 SSPROP_PARAM_TABLE_DEFAULT_COLUMNS 속성을 통해 기본값으로 표시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-129">Columns that have a default value must also be marked as default through SSPROP_PARAM_TABLE_DEFAULT_COLUMNS property to allow the default value to be used for the column's data values for a particular table-valued parameter.</span></span> <span data-ttu-id="24ebb-130">공급자는 기본값으로 표시된 열에 바인딩된 데이터 값을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-130">The provider will ignore the data values bound for the columns marked as default.</span></span>  
  
-   <span data-ttu-id="24ebb-131">SSPROP_PARAM_TABLE_DEFAULT를 함께 설정하지 않으면 DBPROP_COL_AUTOINCREMENT 또는 SSPROP_COL_COMPUTED가 포함된 열의 데이터가 서버로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="24ebb-131">Data will be sent to the server for columns with DBPROP_COL_AUTOINCREMENT or SSPROP_COL_COMPUTED, unless SSPROP_PARAM_TABLE_DEFAULT is also set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24ebb-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="24ebb-132">See Also</span></span>  
 <span data-ttu-id="24ebb-133">[테이블 반환 매개 변수 OLE DB &#40;&#41;](table-valued-parameters-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="24ebb-133">[Table-Valued Parameters &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span></span>  
 [<span data-ttu-id="24ebb-134">테이블 반환 매개 변수&#40;OLE DB&#41; 사용</span><span class="sxs-lookup"><span data-stu-id="24ebb-134">Use Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
