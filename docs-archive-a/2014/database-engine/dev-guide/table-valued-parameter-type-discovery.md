---
title: 테이블 반환 매개 변수 형식 검색 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
ms.assetid: f55818c2-ebb5-4cf6-8c0c-0da41f592560
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ab8d837e4ddf74256e4bae70f772557ec8ff67f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733015"
---
# <a name="table-valued-parameter-type-discovery"></a><span data-ttu-id="17ba3-102">테이블 반환 매개 변수 형식 검색</span><span class="sxs-lookup"><span data-stu-id="17ba3-102">Table-Valued Parameter Type Discovery</span></span>
  <span data-ttu-id="17ba3-103">소비자 즉, Native Client OLE DB 공급자를 사용 하는 클라이언트 응용 프로그램은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 명령 텍스트가 OLE DB 공급자에 지정 된 경우 각 명령 매개 변수의 형식을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17ba3-103">The consumer-that is, the client application using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider-can discover the type of each command parameter if the command text has been given to the OLE DB Provider.</span></span> <span data-ttu-id="17ba3-104">테이블 반환 매개 변수의 형식이 확인되면 소비자가 테이블 반환 매개 변수의 개별 열에 대한 메타데이터 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17ba3-104">After the type of a table-valued parameter is known, the consumer can discover the metadata information for each individual column of the table-valued parameter.</span></span>  
  
 <span data-ttu-id="17ba3-105">프로시저 매개 변수의 형식 정보는 대부분의 매개 변수 형식에서 ICommandWithParameters::GetParameterInfo를 통해 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="17ba3-105">The type information of procedure parameters is supported by ICommandWithParameters::GetParameterInfo for most parameter types.</span></span> <span data-ttu-id="17ba3-106">부터 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 사용자 정의 형식 및 데이터 형식이 도입 됨에 따라 `xml` GetParameterInfo 메서드는 ICommandWithParameters를 통해 사용자 정의 형식 정보 (이름, 스키마 및 카탈로그)를 제공할 수 없기 때문에이 용도로 충분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17ba3-106">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], with the introduction of user-defined types and the `xml` data type, the GetParameterInfo method was not sufficient for this purpose because it was not possible to provide user-defined type information (name, schema, and catalog) through ICommandWithParameters.</span></span> <span data-ttu-id="17ba3-107">따라서 확장된 형식 정보를 제공하기 위해 새로운 인터페이스인 ISSCommandWithParameters가 정의되었습니다.</span><span class="sxs-lookup"><span data-stu-id="17ba3-107">A new interface, ISSCommandWithParameters, was defined to provide extended type information.</span></span>  
  
 <span data-ttu-id="17ba3-108">테이블 반환 매개 변수의 경우 ISSCommandWithParameters 인터페이스를 사용하여 자세한 정보를 검색할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17ba3-108">For table-valued parameters, you also use the ISSCommandWithParameters interface to discover detailed information.</span></span> <span data-ttu-id="17ba3-109">명령 개체를 준비하고 나면 클라이언트가 ISSCommandWithParameters::GetParameterInfo를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="17ba3-109">The client calls ISSCommandWithParameters::GetParameterInfo after preparing the command object.</span></span> <span data-ttu-id="17ba3-110">테이블 반환 매개 변수의 경우 공급자에 의해 DBPARAMINFO 구조의 *wType* 멤버가 DBTYPE_TABLE로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="17ba3-110">For table-valued parameters, the *wType* member of the DBPARAMINFO structure is set to DBTYPE_TABLE by the provider.</span></span> <span data-ttu-id="17ba3-111">DBPARAMINFO 구조의 *ulParamSize* 필드 값은 ~0입니다.</span><span class="sxs-lookup"><span data-stu-id="17ba3-111">The *ulParamSize* field of DBPARAMINFO structure has a value of ~0.</span></span>  
  
 <span data-ttu-id="17ba3-112">그런 다음, 소비자는 ISSCommandWithParameters::GetParameterProperties를 사용하여 추가 속성(테이블 반환 매개 변수 형식 카탈로그 이름, 테이블 반환 매개 변수 형식 스키마 이름, 테이블 반환 매개 변수 형식 이름, 열 순서 및 기본 열)을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="17ba3-112">The consumer would then request additional properties (table-valued parameter type catalog name, table-valued parameter type schema name, table-valued parameter type name, column ordering, and default columns) by using ISSCommandWithParameters::GetParameterProperties.</span></span>  
  
 <span data-ttu-id="17ba3-113">형식 이름이 확인되면 소비자는 IOpenRowset::OpenRowsetor를 호출하거나 테이블 반환 매개 변수 형식 이름을 테이블 이름으로 지정하여 DBSCHEMA_TABLE_TYPE_COLUMNS 행 집합을 가져옴으로써 개별 열 정보를 검색해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17ba3-113">After the type name is known, to retrieve the individual column information the consumer must either call IOpenRowset::OpenRowsetor obtain the DBSCHEMA_TABLE_TYPE_COLUMNS rowset by specifying the table-valued parameter type name as the table name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17ba3-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="17ba3-114">See Also</span></span>  
 <span data-ttu-id="17ba3-115">[테이블 반환 매개 변수 OLE DB &#40;&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="17ba3-115">[Table-Valued Parameters &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md) </span></span>  
 [<span data-ttu-id="17ba3-116">테이블 반환 매개 변수&#40;OLE DB&#41; 사용</span><span class="sxs-lookup"><span data-stu-id="17ba3-116">Use Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
