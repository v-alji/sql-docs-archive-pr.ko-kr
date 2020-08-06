---
title: 세션 속성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- sessions [OLE DB]
- SQL Server Native Client OLE DB provider, sessions
ms.assetid: 2498fbad-b3db-4bea-8fc6-fef5317d3eba
author: rothja
ms.author: jroth
ms.openlocfilehash: 99f2bc6def0f470f653446c87216c3e854b2f819
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646989"
---
# <a name="session-properties"></a><span data-ttu-id="e875d-102">세션 속성</span><span class="sxs-lookup"><span data-stu-id="e875d-102">Session Properties</span></span>
  <span data-ttu-id="e875d-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 OLE DB 세션 속성을 다음과 같이 해석 합니다.</span><span class="sxs-lookup"><span data-stu-id="e875d-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider interprets OLE DB session properties as follows.</span></span>  
  
|<span data-ttu-id="e875d-104">속성 ID</span><span class="sxs-lookup"><span data-stu-id="e875d-104">Property ID</span></span>|<span data-ttu-id="e875d-105">Description</span><span class="sxs-lookup"><span data-stu-id="e875d-105">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="e875d-106">DBPROP_SESS_AUTOCOMMITISOLEVELS</span><span class="sxs-lookup"><span data-stu-id="e875d-106">DBPROP_SESS_AUTOCOMMITISOLEVELS</span></span>|<span data-ttu-id="e875d-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 비정상 수준 DBPROPVAL_TI_CHAOS를 제외 하 고 모든 자동 커밋 트랜잭션 격리 수준을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="e875d-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports all autocommit transaction isolation levels with the exception of the chaos level DBPROPVAL_TI_CHAOS.</span></span>|  
  
 <span data-ttu-id="e875d-108">공급자별 속성 집합 DBPROPSET_SQLSERVERSESSION에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 다음과 같은 추가 세션 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e875d-108">In the provider-specific property set DBPROPSET_SQLSERVERSESSION, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the following additional session property.</span></span>  
  
|<span data-ttu-id="e875d-109">속성 ID</span><span class="sxs-lookup"><span data-stu-id="e875d-109">Property ID</span></span>|<span data-ttu-id="e875d-110">Description</span><span class="sxs-lookup"><span data-stu-id="e875d-110">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="e875d-111">SSPROP_QUOTEDCATALOGNAMES</span><span class="sxs-lookup"><span data-stu-id="e875d-111">SSPROP_QUOTEDCATALOGNAMES</span></span>|<span data-ttu-id="e875d-112">유형: VT_BOOL</span><span class="sxs-lookup"><span data-stu-id="e875d-112">Type: VT_BOOL</span></span><br /><br /> <span data-ttu-id="e875d-113">R/W: 읽기/쓰기</span><span class="sxs-lookup"><span data-stu-id="e875d-113">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="e875d-114">Default: VARIANT_FALSE</span><span class="sxs-lookup"><span data-stu-id="e875d-114">Default: VARIANT_FALSE</span></span><br /><br /> <span data-ttu-id="e875d-115">설명: CATALOG 제한에서 허용되는 따옴표 붙은 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="e875d-115">Description: Quoted identifiers allowed in CATALOG restriction.</span></span><br /><br /> <span data-ttu-id="e875d-116">VARIANT_TRUE: 따옴표 붙은 식별자는 분산 쿼리 지원을 제공하는 스키마 행 집합에 대한 카탈로그 제한에서 인식됩니다.</span><span class="sxs-lookup"><span data-stu-id="e875d-116">VARIANT_TRUE: Quoted identifiers are recognized for a catalog restriction for the schema rowsets that supply distributed query support.</span></span><br /><br /> <span data-ttu-id="e875d-117">VARIANT_FALSE: 따옴표 붙은 식별자는 분산 쿼리 지원을 제공하는 스키마 행 집합에 대한 카탈로그 제한에서 인식되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e875d-117">VARIANT_FALSE: Quoted identifiers are not recognized for a catalog restriction for the schema rowsets that supply distributed query support.</span></span><br /><br /> <span data-ttu-id="e875d-118">분산 쿼리 지원을 제공하는 스키마 행 집합에 대한 자세한 내용은 [스키마 행 집합에서 분산 쿼리 지원](../native-client/ole-db/schema-rowsets-distributed-query-support.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e875d-118">For more information about schema rowsets that supply distributed query support, see [Distributed Query Support in Schema Rowsets](../native-client/ole-db/schema-rowsets-distributed-query-support.md).</span></span>|  
|<span data-ttu-id="e875d-119">SSPROP_ALLOWNATIVEVARIANT</span><span class="sxs-lookup"><span data-stu-id="e875d-119">SSPROP_ALLOWNATIVEVARIANT</span></span>|<span data-ttu-id="e875d-120">유형: VT_BOOL</span><span class="sxs-lookup"><span data-stu-id="e875d-120">Type: VT_BOOL</span></span><br /><br /> <span data-ttu-id="e875d-121">R/W: 읽기/쓰기</span><span class="sxs-lookup"><span data-stu-id="e875d-121">R/W: Read/Write</span></span><br /><br /> <span data-ttu-id="e875d-122">Default: VARIANT_FALSE</span><span class="sxs-lookup"><span data-stu-id="e875d-122">Default: VARIANT_FALSE</span></span><br /><br /> <span data-ttu-id="e875d-123">설명: 데이터가 DBTYPE_VARIANT 또는 DBTYPE_SQLVARIANT로 인출되는지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="e875d-123">Description: Determines if the data fetched in is as DBTYPE_VARIANT or DBTYPE_SQLVARIANT.</span></span><br /><br /> <span data-ttu-id="e875d-124">VARIANT_TRUE: 열 유형이 DBTYPE_SQLVARIANT로 반환되고, 이 경우 버퍼에 SSVARIANT 구조가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e875d-124">VARIANT_TRUE: Column type is returned as DBTYPE_SQLVARIANT in which case the buffer will hold SSVARIANT structure.</span></span><br /><br /> <span data-ttu-id="e875d-125">VARIANT_FALSE: 열 유형이 DBTYPE_VARIANT로 반환되고, 이 경우 버퍼에 VARIANT 구조가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e875d-125">VARIANT_FALSE: Column type is returned as DBTYPE_VARIANT and the buffer will have VARIANT structure.</span></span>|  
|<span data-ttu-id="e875d-126">SSPROP_ASYNCH_BULKCOPY</span><span class="sxs-lookup"><span data-stu-id="e875d-126">SSPROP_ASYNCH_BULKCOPY</span></span>|<span data-ttu-id="e875d-127">비동기 모드를 사용하려면 BCPExec 메서드를 호출하기 전에 공급자별 세션 속성 SSPROP_ASYNCH_BULKCOPY를 VARIANT_TRUE로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e875d-127">To use asynchronous mode, set the provider specific session property SSPROP_ASYNCH_BULKCOPY to VARIANT_TRUE before calling the BCPExec method.</span></span> <span data-ttu-id="e875d-128">이 속성은 DBPROPSET_SQLSERVERSESSION 속성 집합에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e875d-128">This property is available in the DBPROPSET_SQLSERVERSESSION property set.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e875d-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e875d-129">See Also</span></span>  
 [<span data-ttu-id="e875d-130">데이터 원본 개체 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="e875d-130">Data Source Objects &#40;OLE DB&#41;</span></span>](data-source-objects-ole-db.md)  
  
  
