---
title: SQL Server 인덱스 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- CreateIndex function
- constraints [OLE DB]
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
- adding indexes
ms.assetid: 6239d440-2818-4b98-bb79-732dced41952
author: rothja
ms.author: jroth
ms.openlocfilehash: 3693355eec7a290c03658c10db500161aa52062d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739784"
---
# <a name="creating-sql-server-indexes"></a><span data-ttu-id="cbfd0-102">SQL Server 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="cbfd0-102">Creating SQL Server Indexes</span></span>
  <span data-ttu-id="cbfd0-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 소비자가 테이블에 새 인덱스를 정의할 수 있도록 **Iindexdefinition:: createindex** 함수를 제공 합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbfd0-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **IIndexDefinition::CreateIndex** function, allowing consumers to define new indexes on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables.</span></span>  
  
 <span data-ttu-id="cbfd0-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 테이블 인덱스를 인덱스나 제약 조건으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider creates table indexes as either indexes or constraints.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="cbfd0-105">는 테이블 소유자, 데이터베이스 소유자 및 특정 관리 역할이 멤버에게 제약 조건 생성 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-105">gives constraint-creation privilege to the table owner, database owner, and members of certain administrative roles.</span></span> <span data-ttu-id="cbfd0-106">기본적으로 테이블 소유자만 테이블에 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-106">By default, only the table owner can create an index on a table.</span></span> <span data-ttu-id="cbfd0-107">따라서 **CreateIndex**의 성공 또는 실패 여부는 애플리케이션 사용자의 액세스 권한뿐만 아니라 생성되는 인덱스의 유형에 따라서도 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-107">Therefore, the success or failure of **CreateIndex** depends not only on the application user's access rights but also on the type of index created.</span></span>  
  
 <span data-ttu-id="cbfd0-108">소비자는 *pTableID* 매개 변수에서 *uName* 공용 구조체의 *pwszName* 멤버에 테이블 이름을 유니코드 문자열로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-108">Consumers specify the table name as a Unicode character string in the *pwszName* member of the *uName* union in the *pTableID* parameter.</span></span> <span data-ttu-id="cbfd0-109">*pTableID*의 *eKind* 멤버는 DBKIND_NAME이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-109">The *eKind* member of *pTableID* must be DBKIND_NAME.</span></span>  
  
 <span data-ttu-id="cbfd0-110">*Pindexid* 매개 변수는 NULL 일 수 있으며,이 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 인덱스에 대 한 고유한 이름을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-110">The *pIndexID* parameter can be NULL, and if it is, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider creates a unique name for the index.</span></span> <span data-ttu-id="cbfd0-111">소비자는 *ppIndexID* 매개 변수에 DBID에 대한 유효한 포인터를 지정하여 인덱스의 이름을 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-111">The consumer can capture the name of the index by specifying a valid pointer to a DBID in the *ppIndexID* parameter.</span></span>  
  
 <span data-ttu-id="cbfd0-112">소비자는 *pIndexID* 매개 변수의 에서 *uName* 공용 구조체에 있는 *pwszName*멤버에 인덱스 이름을 유니코드 문자열로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-112">The consumer can specify the index name as a Unicode character string in the *pwszName* member of the *uName* union of the *pIndexID* parameter.</span></span> <span data-ttu-id="cbfd0-113">*pIndexID*의 *eKind* 멤버는 DBKIND_NAME이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-113">The *eKind* member of *pIndexID* must be DBKIND_NAME.</span></span>  
  
 <span data-ttu-id="cbfd0-114">소비자는 인덱스에 참여하는 열을 이름으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-114">The consumer specifies the column or columns participating in the index by name.</span></span> <span data-ttu-id="cbfd0-115">**CreateIndex**에 사용된 각 DBINDEXCOLUMNDESC 구조에 대해 *pColumnID*의 *eKind* 멤버는 DBKIND_NAME이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-115">For each DBINDEXCOLUMNDESC structure used in **CreateIndex**, the *eKind* member of the *pColumnID* must be DBKIND_NAME.</span></span> <span data-ttu-id="cbfd0-116">열 이름은 *pColumnID*의 *uName* 공용 구조체에 있는 *pwszName* 멤버에 유니코드 문자열로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-116">The name of the column is specified as a Unicode character string in the *pwszName* member of the *uName* union in the *pColumnID*.</span></span>  
  
 <span data-ttu-id="cbfd0-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인덱스의 값에 대 한 오름차순 순서를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-117">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support ascending order on values in the index.</span></span> <span data-ttu-id="cbfd0-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]소비자가 DBINDEXCOLUMNDESC 구조에서 DBINDEX_COL_ORDER_DESC을 지정 하는 경우 Native Client OLE DB 공급자는 E_INVALIDARG를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns E_INVALIDARG if the consumer specifies DBINDEX_COL_ORDER_DESC in any DBINDEXCOLUMNDESC structure.</span></span>  
  
 <span data-ttu-id="cbfd0-119">**CreateIndex**는 인덱스 속성을 다음과 같이 해석합니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-119">**CreateIndex** interprets index properties as follows.</span></span>  
  
|<span data-ttu-id="cbfd0-120">속성 ID</span><span class="sxs-lookup"><span data-stu-id="cbfd0-120">Property ID</span></span>|<span data-ttu-id="cbfd0-121">Description</span><span class="sxs-lookup"><span data-stu-id="cbfd0-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="cbfd0-122">DBPROP_INDEX_AUTOUPDATE</span><span class="sxs-lookup"><span data-stu-id="cbfd0-122">DBPROP_INDEX_AUTOUPDATE</span></span>|<span data-ttu-id="cbfd0-123">R/W: 읽기/쓰기</span><span class="sxs-lookup"><span data-stu-id="cbfd0-123">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="cbfd0-124">기본값: 없음</span><span class="sxs-lookup"><span data-stu-id="cbfd0-124">Default: None</span></span><br /><br /> <span data-ttu-id="cbfd0-125">설명: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자가이 속성을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-125">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="cbfd0-126">**CreateIndex**에서 속성을 설정하려고 하면 DB_S_ERRORSOCCURRED 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-126">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="cbfd0-127">속성 구조의 *dwStatus* 멤버는 DBPROPSTATUS_BADVALUE를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-127">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="cbfd0-128">DBPROP_INDEX_CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="cbfd0-128">DBPROP_INDEX_CLUSTERED</span></span>|<span data-ttu-id="cbfd0-129">R/W: 읽기/쓰기</span><span class="sxs-lookup"><span data-stu-id="cbfd0-129">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="cbfd0-130">Default: VARIANT_FALSE</span><span class="sxs-lookup"><span data-stu-id="cbfd0-130">Default: VARIANT_FALSE</span></span><br /><br /> <span data-ttu-id="cbfd0-131">설명: 인덱스 클러스터링을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-131">Description: Controls index clustering.</span></span><br /><br /> <span data-ttu-id="cbfd0-132">VARIANT_TRUE: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 테이블에 클러스터형 인덱스를 만들려고 시도 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="cbfd0-132">VARIANT_TRUE: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider attempts to create a clustered index on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="cbfd0-133">는 각 테이블에서 클러스터형 인덱스 한 개만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-133">supports at most one clustered index on any table.</span></span><br /><br /> <span data-ttu-id="cbfd0-134">VARIANT_FALSE: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 테이블에 비클러스터형 인덱스를 만들려고 시도 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="cbfd0-134">VARIANT_FALSE: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider attempts to create a nonclustered index on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>|  
|<span data-ttu-id="cbfd0-135">DBPROP_INDEX_FILLFACTOR</span><span class="sxs-lookup"><span data-stu-id="cbfd0-135">DBPROP_INDEX_FILLFACTOR</span></span>|<span data-ttu-id="cbfd0-136">R/W: 읽기/쓰기</span><span class="sxs-lookup"><span data-stu-id="cbfd0-136">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="cbfd0-137">기본값: 0</span><span class="sxs-lookup"><span data-stu-id="cbfd0-137">Default: 0</span></span><br /><br /> <span data-ttu-id="cbfd0-138">설명: 스토리지에 사용되는 인덱스 페이지의 백분율을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-138">Description: Specifies the percentage of an index page used for storage.</span></span> <span data-ttu-id="cbfd0-139">자세한 내용은 [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-139">For more information, see [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql).</span></span><br /><br /> <span data-ttu-id="cbfd0-140">변형 유형은 VT_I4입니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-140">The type of the variant is VT_I4.</span></span> <span data-ttu-id="cbfd0-141">값은 1 이상 100 이하여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-141">The value must be greater than or equal to 1 and less than or equal to 100.</span></span>|  
|<span data-ttu-id="cbfd0-142">DBPROP_INDEX_INITIALIZE</span><span class="sxs-lookup"><span data-stu-id="cbfd0-142">DBPROP_INDEX_INITIALIZE</span></span>|<span data-ttu-id="cbfd0-143">R/W: 읽기/쓰기</span><span class="sxs-lookup"><span data-stu-id="cbfd0-143">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="cbfd0-144">기본값: 없음</span><span class="sxs-lookup"><span data-stu-id="cbfd0-144">Default: None</span></span><br /><br /> <span data-ttu-id="cbfd0-145">설명: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자가이 속성을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-145">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="cbfd0-146">**CreateIndex**에서 속성을 설정하려고 하면 DB_S_ERRORSOCCURRED 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-146">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="cbfd0-147">속성 구조의 *dwStatus* 멤버는 DBPROPSTATUS_BADVALUE를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-147">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="cbfd0-148">DBPROP_INDEX_NULLCOLLATION</span><span class="sxs-lookup"><span data-stu-id="cbfd0-148">DBPROP_INDEX_NULLCOLLATION</span></span>|<span data-ttu-id="cbfd0-149">R/W: 읽기/쓰기</span><span class="sxs-lookup"><span data-stu-id="cbfd0-149">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="cbfd0-150">기본값: 없음</span><span class="sxs-lookup"><span data-stu-id="cbfd0-150">Default: None</span></span><br /><br /> <span data-ttu-id="cbfd0-151">설명: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자가이 속성을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-151">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="cbfd0-152">**CreateIndex**에서 속성을 설정하려고 하면 DB_S_ERRORSOCCURRED 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-152">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="cbfd0-153">속성 구조의 *dwStatus* 멤버는 DBPROPSTATUS_BADVALUE를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-153">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="cbfd0-154">DBPROP_INDEX_NULLS</span><span class="sxs-lookup"><span data-stu-id="cbfd0-154">DBPROP_INDEX_NULLS</span></span>|<span data-ttu-id="cbfd0-155">R/W: 읽기/쓰기</span><span class="sxs-lookup"><span data-stu-id="cbfd0-155">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="cbfd0-156">기본값: 없음</span><span class="sxs-lookup"><span data-stu-id="cbfd0-156">Default: None</span></span><br /><br /> <span data-ttu-id="cbfd0-157">설명: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자가이 속성을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-157">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="cbfd0-158">**CreateIndex**에서 속성을 설정하려고 하면 DB_S_ERRORSOCCURRED 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-158">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="cbfd0-159">속성 구조의 *dwStatus* 멤버는 DBPROPSTATUS_BADVALUE를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-159">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="cbfd0-160">DBPROP_INDEX_PRIMARYKEY</span><span class="sxs-lookup"><span data-stu-id="cbfd0-160">DBPROP_INDEX_PRIMARYKEY</span></span>|<span data-ttu-id="cbfd0-161">R/W: 읽기/쓰기</span><span class="sxs-lookup"><span data-stu-id="cbfd0-161">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="cbfd0-162">기본값: VARIANT_FALSE Description: 참조 무결성, PRIMARY KEY 제약 조건으로 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-162">Default: VARIANT_FALSE Description: Creates the index as a referential integrity, PRIMARY KEY constraint.</span></span><br /><br /> <span data-ttu-id="cbfd0-163">VARIANT_TRUE: 테이블의 PRIMARY KEY 제약 조건을 지원하기 위해 인덱스가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-163">VARIANT_TRUE: The index is created to support the PRIMARY KEY constraint of the table.</span></span> <span data-ttu-id="cbfd0-164">열은 Null이 아니어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-164">The columns must be nonnullable.</span></span><br /><br /> <span data-ttu-id="cbfd0-165">VARIANT_FALSE: 인덱스가 테이블의 행 값에 대한 PRIMARY KEY 제약 조건으로 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-165">VARIANT_FALSE: The index is not used as a PRIMARY KEY constraint for row values in the table.</span></span>|  
|<span data-ttu-id="cbfd0-166">DBPROP_INDEX_SORTBOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="cbfd0-166">DBPROP_INDEX_SORTBOOKMARKS</span></span>|<span data-ttu-id="cbfd0-167">R/W: 읽기/쓰기</span><span class="sxs-lookup"><span data-stu-id="cbfd0-167">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="cbfd0-168">기본값: 없음</span><span class="sxs-lookup"><span data-stu-id="cbfd0-168">Default: None</span></span><br /><br /> <span data-ttu-id="cbfd0-169">설명: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자가이 속성을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-169">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="cbfd0-170">**CreateIndex**에서 속성을 설정하려고 하면 DB_S_ERRORSOCCURRED 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-170">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="cbfd0-171">속성 구조의 *dwStatus* 멤버는 DBPROPSTATUS_BADVALUE를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-171">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="cbfd0-172">DBPROP_INDEX_TEMPINDEX</span><span class="sxs-lookup"><span data-stu-id="cbfd0-172">DBPROP_INDEX_TEMPINDEX</span></span>|<span data-ttu-id="cbfd0-173">R/W: 읽기/쓰기</span><span class="sxs-lookup"><span data-stu-id="cbfd0-173">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="cbfd0-174">기본값: 없음</span><span class="sxs-lookup"><span data-stu-id="cbfd0-174">Default: None</span></span><br /><br /> <span data-ttu-id="cbfd0-175">설명: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자가이 속성을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-175">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="cbfd0-176">**CreateIndex**에서 속성을 설정하려고 하면 DB_S_ERRORSOCCURRED 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-176">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="cbfd0-177">속성 구조의 *dwStatus* 멤버는 DBPROPSTATUS_BADVALUE를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-177">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="cbfd0-178">DBPROP_INDEX_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbfd0-178">DBPROP_INDEX_TYPE</span></span>|<span data-ttu-id="cbfd0-179">R/W: 읽기/쓰기</span><span class="sxs-lookup"><span data-stu-id="cbfd0-179">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="cbfd0-180">기본값: 없음</span><span class="sxs-lookup"><span data-stu-id="cbfd0-180">Default: None</span></span><br /><br /> <span data-ttu-id="cbfd0-181">설명: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자가이 속성을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-181">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="cbfd0-182">**CreateIndex**에서 속성을 설정하려고 하면 DB_S_ERRORSOCCURRED 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-182">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="cbfd0-183">속성 구조의 *dwStatus* 멤버는 DBPROPSTATUS_BADVALUE를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-183">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="cbfd0-184">DBPROP_INDEX_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="cbfd0-184">DBPROP_INDEX_UNIQUE</span></span>|<span data-ttu-id="cbfd0-185">R/W: 읽기/쓰기</span><span class="sxs-lookup"><span data-stu-id="cbfd0-185">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="cbfd0-186">Default: VARIANT_FALSE</span><span class="sxs-lookup"><span data-stu-id="cbfd0-186">Default: VARIANT_FALSE</span></span><br /><br /> <span data-ttu-id="cbfd0-187">설명: 참여하는 열의 UNIQUE 제약 조건으로 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-187">Description: Creates the index as a UNIQUE constraint on the participating column or columns.</span></span><br /><br /> <span data-ttu-id="cbfd0-188">VARIANT_TRUE: 인덱스를 사용하여 테이블의 행 값을 고유하게 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-188">VARIANT_TRUE: The index is used to uniquely constrain row values in the table.</span></span><br /><br /> <span data-ttu-id="cbfd0-189">VARIANT_FALSE: 인덱스가 행 값을 고유하게 제한하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-189">VARIANT_FALSE: The index does not uniquely constrain row values.</span></span>|  
  
 <span data-ttu-id="cbfd0-190">공급자별 속성 집합 DBPROPSET_SQLSERVERINDEX의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 다음과 같은 데이터 원본 정보 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-190">In the provider-specific property set DBPROPSET_SQLSERVERINDEX, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the following data source information property.</span></span>  
  
|<span data-ttu-id="cbfd0-191">속성 ID</span><span class="sxs-lookup"><span data-stu-id="cbfd0-191">Property ID</span></span>|<span data-ttu-id="cbfd0-192">Description</span><span class="sxs-lookup"><span data-stu-id="cbfd0-192">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="cbfd0-193">SSPROP_INDEX_XML</span><span class="sxs-lookup"><span data-stu-id="cbfd0-193">SSPROP_INDEX_XML</span></span>|<span data-ttu-id="cbfd0-194">형식: VT_BOOL (R/W)</span><span class="sxs-lookup"><span data-stu-id="cbfd0-194">Type: VT_BOOL (R/W)</span></span><br /><br /> <span data-ttu-id="cbfd0-195">Default: VARIANT_FALSE</span><span class="sxs-lookup"><span data-stu-id="cbfd0-195">Default: VARIANT_FALSE</span></span><br /><br /> <span data-ttu-id="cbfd0-196">설명: IIndexDefinition::CreateIndex에 VARIANT_TRUE 값을 사용하여 이 속성을 지정하면 인덱싱되는 열에 해당하는 기본 XML 인덱스가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-196">Description: When this property is specified with a value of VARIANT_TRUE with IIndexDefinition::CreateIndex, it results in a primary xml index being created corresponding to the column being indexed.</span></span> <span data-ttu-id="cbfd0-197">이 속성이 VARIANT_TRUE이면 cIndexColumnDescs는 1이어야 합니다. 그렇지 않으면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-197">If this property is VARIANT_TRUE, cIndexColumnDescs should be 1, otherwise it is an error.</span></span>|  
  
 <span data-ttu-id="cbfd0-198">다음 예에서는 기본 키 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cbfd0-198">This example creates a primary key index:</span></span>  
  
```  
// This CREATE TABLE statement shows the referential integrity and   
// PRIMARY KEY constraint on the OrderDetails table that will be created   
// by the following example code.  
//  
// CREATE TABLE OrderDetails  
// (  
//    OrderID      int      NOT NULL  
//    ProductID   int      NOT NULL  
//        CONSTRAINT PK_OrderDetails  
//        PRIMARY KEY CLUSTERED (OrderID, ProductID),  
//    UnitPrice   money      NOT NULL,  
//    Quantity   int      NOT NULL,  
//    Discount   decimal(2,2)   NOT NULL  
//        DEFAULT 0  
// )  
//  
HRESULT CreatePrimaryKey  
    (  
    IIndexDefinition* pIIndexDefinition  
    )  
    {  
    HRESULT             hr = S_OK;  
  
    DBID                dbidTable;  
    DBID                dbidIndex;  
    const ULONG         nCols = 2;  
    ULONG               nCol;  
    const ULONG         nProps = 2;  
    ULONG               nProp;  
  
    DBINDEXCOLUMNDESC   dbidxcoldesc[nCols];  
    DBPROP              dbpropIndex[nProps];  
    DBPROPSET           dbpropset;  
  
    DBID*               pdbidIndexOut = NULL;  
  
    // Set up identifiers for the table and index.  
    dbidTable.eKind = DBKIND_NAME;  
    dbidTable.uName.pwszName = L"OrderDetails";  
  
    dbidIndex.eKind = DBKIND_NAME;  
    dbidIndex.uName.pwszName = L"PK_OrderDetails";  
  
    // Set up column identifiers.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        dbidxcoldesc[nCol].pColumnID = new DBID;  
        dbidxcoldesc[nCol].pColumnID->eKind = DBKIND_NAME;  
  
        dbidxcoldesc[nCol].eIndexColOrder = DBINDEX_COL_ORDER_ASC;  
        }  
    dbidxcoldesc[0].pColumnID->uName.pwszName = L"OrderID";  
    dbidxcoldesc[1].pColumnID->uName.pwszName = L"ProductID";  
  
    // Set properties for the index. The index is clustered,  
    // PRIMARY KEY.  
    for (nProp = 0; nProp < nProps; nProp++)  
        {  
        dbpropIndex[nProp].dwOptions = DBPROPOPTIONS_REQUIRED;  
        dbpropIndex[nProp].colid = DB_NULLID;  
  
        VariantInit(&(dbpropIndex[nProp].vValue));  
  
        dbpropIndex[nProp].vValue.vt = VT_BOOL;  
        }  
    dbpropIndex[0].dwPropertyID = DBPROP_INDEX_CLUSTERED;  
    dbpropIndex[0].vValue.boolVal = VARIANT_TRUE;  
  
    dbpropIndex[1].dwPropertyID = DBPROP_INDEX_PRIMARYKEY;  
    dbpropIndex[1].vValue.boolVal = VARIANT_TRUE;  
  
    dbpropset.rgProperties = dbpropIndex;  
    dbpropset.cProperties = nProps;  
    dbpropset.guidPropertySet = DBPROPSET_INDEX;  
  
    hr = pIIndexDefinition->CreateIndex(&dbidTable, &dbidIndex, nCols,  
        dbidxcoldesc, 1, &dbpropset, &pdbidIndexOut);  
  
    // Clean up dynamically allocated DBIDs.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        delete dbidxcoldesc[nCol].pColumnID;  
        }  
  
    return (hr);  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="cbfd0-199">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cbfd0-199">See Also</span></span>  
 [<span data-ttu-id="cbfd0-200">테이블 및 인덱스</span><span class="sxs-lookup"><span data-stu-id="cbfd0-200">Tables and Indexes</span></span>](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
  
