---
title: 조회 변환 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptrans.f1
helpviewer_keywords:
- Lookup transformation
- joining columns [Integration Services]
- cache [Integration Services]
- match exactly [Integration Services]
- lookups [Integration Services]
- exact matches [Integration Services]
ms.assetid: de1cc8de-e7af-4727-b5a5-a1f0a739aa09
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 567c5d95c2ee7c15ea5c541f7fe2010d46ba36f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659561"
---
# <a name="lookup-transformation"></a><span data-ttu-id="77b42-102">조회 변환</span><span class="sxs-lookup"><span data-stu-id="77b42-102">Lookup Transformation</span></span>
  <span data-ttu-id="77b42-103">조회 변환은 입력 열의 데이터를 참조 데이터 세트의 열과 조인하여 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-103">The Lookup transformation performs lookups by joining data in input columns with columns in a reference dataset.</span></span> <span data-ttu-id="77b42-104">조회를 사용하면 공통 열의 값을 기반으로 하는 관련 테이블의 추가 정보에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-104">You use the lookup to access additional information in a related table that is based on values in common columns.</span></span>  
  
 <span data-ttu-id="77b42-105">참조 데이터 세트는 캐시 파일, 기존 테이블이나 뷰, 새 테이블 또는 SQL 쿼리의 결과일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-105">The reference dataset can be a cache file, an existing table or view, a new table, or the result of an SQL query.</span></span> <span data-ttu-id="77b42-106">조회 변환은 OLE DB 연결 관리자 또는 캐시 연결 관리자를 사용하여 참조 데이터 세트에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-106">The Lookup transformation uses either an OLE DB connection manager or a Cache connection manager to connect to the reference dataset.</span></span> <span data-ttu-id="77b42-107">자세한 내용은 [OLE DB Connection Manager](../../connection-manager/ole-db-connection-manager.md) 및 [Cache Connection Manager](../../connection-manager/cache-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="77b42-107">For more information, see [OLE DB Connection Manager](../../connection-manager/ole-db-connection-manager.md) and [Cache Connection Manager](../../connection-manager/cache-connection-manager.md)</span></span>  
  
 <span data-ttu-id="77b42-108">다음과 같은 방법으로 조회 변환을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-108">You can configure the Lookup transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="77b42-109">사용하려는 연결 관리자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-109">Select the connection manager that you want to use.</span></span> <span data-ttu-id="77b42-110">데이터베이스에 연결하려면 OLE DB 연결 관리자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-110">If you want to connect to a database, select an OLE DB connection manager.</span></span> <span data-ttu-id="77b42-111">캐시 파일에 연결하려면 캐시 연결 관리자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-111">If you want to connect to a cache file, select a Cache connection manager.</span></span>  
  
-   <span data-ttu-id="77b42-112">참조 데이터 세트가 포함된 테이블 또는 뷰를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-112">Specify the table or view that contains the reference dataset.</span></span>  
  
-   <span data-ttu-id="77b42-113">SQL 문을 지정하여 참조 데이터 세트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-113">Generate a reference dataset by specifying an SQL statement.</span></span>  
  
-   <span data-ttu-id="77b42-114">입력과 참조 데이터 세트 간의 조인을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-114">Specify joins between the input and the reference dataset.</span></span>  
  
-   <span data-ttu-id="77b42-115">참조 데이터 세트의 열을 조회 변환 출력에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-115">Add columns from the reference dataset to the Lookup transformation output.</span></span>  
  
-   <span data-ttu-id="77b42-116">캐싱 옵션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-116">Configure the caching options.</span></span>  
  
 <span data-ttu-id="77b42-117">조회 변환은 OLE DB 연결 관리자에 대해 다음과 같은 데이터베이스 공급자를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-117">The Lookup transformation supports the following database providers for the OLE DB connection manager:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
-   <span data-ttu-id="77b42-118">Oracle</span><span class="sxs-lookup"><span data-stu-id="77b42-118">Oracle</span></span>  
  
-   <span data-ttu-id="77b42-119">DB2</span><span class="sxs-lookup"><span data-stu-id="77b42-119">DB2</span></span>  
  
 <span data-ttu-id="77b42-120">조회 변환은 변환 입력 값과 참조 데이터 세트 값 간에 동등 조인을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-120">The Lookup transformation tries to perform an equi-join between values in the transformation input and values in the reference dataset.</span></span> <span data-ttu-id="77b42-121">(동등 조인을 사용하는 경우 변환 입력의 각 행이 참조 데이터 세트의 행과 하나 이상 일치해야 합니다.) 동등 조인을 사용할 수 없는 경우 조회 변환은 다음 동작 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-121">(An equi-join means that each row in the transformation input must match at least one row from the reference dataset.) If an equi-join is not possible, the Lookup transformation takes one of the following actions:</span></span>  
  
-   <span data-ttu-id="77b42-122">참조 데이터 세트에 일치하는 항목이 없으면 조인이 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-122">If there is no matching entry in the reference dataset, no join occurs.</span></span> <span data-ttu-id="77b42-123">기본적으로 조회 변환은 일치하는 항목이 없는 행을 오류로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-123">By default, the Lookup transformation treats rows without matching entries as errors.</span></span> <span data-ttu-id="77b42-124">하지만 이러한 행을 불일치 항목 출력으로 리디렉션하도록 조회 변환을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-124">However, you can configure the Lookup transformation to redirect such rows to a no match output.</span></span> <span data-ttu-id="77b42-125">자세한 내용은 [조회 변환 편집기&#40;일반 페이지&#41;](../../lookup-transformation-editor-general-page.md) 및 [조회 변환 편집기&#40;오류 출력 페이지&#41;](../../lookup-transformation-editor-error-output-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="77b42-125">For more information, see [Lookup Transformation Editor &#40;General Page&#41;](../../lookup-transformation-editor-general-page.md) and [Lookup Transformation Editor &#40;Error Output Page&#41;](../../lookup-transformation-editor-error-output-page.md).</span></span>  
  
-   <span data-ttu-id="77b42-126">참조 테이블에 일치하는 항목이 여러 개 있을 경우 조회 변환은 조회 쿼리에서 반환된 첫 번째 일치 항목만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-126">If there are multiple matches in the reference table, the Lookup transformation returns only the first match returned by the lookup query.</span></span> <span data-ttu-id="77b42-127">일치하는 항목이 여러 개 발견되면 변환이 모든 참조 데이터 세트를 캐시에 로드하도록 구성된 경우에만 조회 변환에서 오류 또는 경고가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-127">If multiple matches are found, the Lookup transformation generates an error or warning only when the transformation has been configured to load all the reference dataset into the cache.</span></span> <span data-ttu-id="77b42-128">이 경우 변환이 캐시를 채울 때 여러 개의 일치 항목이 발견되면 조회 변환에서 경고가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-128">In this case, the Lookup transformation generates a warning when the transformation detects multiple matches as the transformation fills the cache.</span></span>  
  
 <span data-ttu-id="77b42-129">복합 조인을 사용하면 변환 입력의 여러 열을 참조 데이터 세트의 열에 조인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-129">The join can be a composite join, which means that you can join multiple columns in the transformation input to columns in the reference dataset.</span></span> <span data-ttu-id="77b42-130">이 변환은 DT_R4, DT_R8, DT_TEXT, DT_NTEXT 또는 DT_IMAGE를 제외한 모든 데이터 형식의 조인 열을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-130">The transformation supports join columns with any data type, except for DT_R4, DT_R8, DT_TEXT, DT_NTEXT, or DT_IMAGE.</span></span> <span data-ttu-id="77b42-131">자세한 내용은 [Integration Services Data Types](../integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="77b42-131">For more information, see [Integration Services Data Types](../integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="77b42-132">일반적으로 참조 데이터 세트의 값이 변환 출력에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-132">Typically, values from the reference dataset are added to the transformation output.</span></span> <span data-ttu-id="77b42-133">예를 들어 조회 변환은 입력 열의 값을 사용하여 테이블에서 제품 이름을 추출한 다음 변환 출력에 제품 이름을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-133">For example, the Lookup transformation can extract a product name from a table using a value from an input column, and then add the product name to the transformation output.</span></span> <span data-ttu-id="77b42-134">참조 테이블의 값은 열 값을 대체하거나 새 열에 추가될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-134">The values from the reference table can replace column values or can be added to new columns.</span></span>  
  
 <span data-ttu-id="77b42-135">조회 변환에서 수행하는 조회는 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-135">The lookups performed by the Lookup transformation are case sensitive.</span></span> <span data-ttu-id="77b42-136">데이터의 대/소문자 차이로 인한 조회 오류를 방지하려면 먼저 문자표 변환을 사용하여 데이터를 대문자 또는 소문자로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-136">To avoid lookup failures that are caused by case differences in data, first use the Character Map transformation to convert the data to uppercase or lowercase.</span></span> <span data-ttu-id="77b42-137">그런 다음 참조 테이블을 생성하는 SQL 문에 UPPER 또는 LOWER 함수를 포함시킵니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-137">Then, include the UPPER or LOWER functions in the SQL statement that generates the reference table.</span></span> <span data-ttu-id="77b42-138">자세한 내용은 [문자표 변환](character-map-transformation.md), [UPPER&#40;Transact-SQL&#41;](/sql/t-sql/functions/upper-transact-sql) 및 [LOWER&#40;Transact-SQL&#41;](/sql/t-sql/functions/lower-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="77b42-138">For more information, see [Character Map Transformation](character-map-transformation.md), [UPPER &#40;Transact-SQL&#41;](/sql/t-sql/functions/upper-transact-sql), and [LOWER &#40;Transact-SQL&#41;](/sql/t-sql/functions/lower-transact-sql).</span></span>  
  
 <span data-ttu-id="77b42-139">조회 변환에는 다음과 같은 입력 및 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-139">The Lookup transformation has the following inputs and outputs:</span></span>  
  
-   <span data-ttu-id="77b42-140">입력.</span><span class="sxs-lookup"><span data-stu-id="77b42-140">Input.</span></span>  
  
-   <span data-ttu-id="77b42-141">일치 항목 출력.</span><span class="sxs-lookup"><span data-stu-id="77b42-141">Match output.</span></span> <span data-ttu-id="77b42-142">일치 항목 출력은 참조 데이터 세트와 하나 이상의 항목이 일치하는 변환 입력 행을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-142">The match output handles the rows in the transformation input that match at least one entry in the reference dataset.</span></span>  
  
-   <span data-ttu-id="77b42-143">불일치 항목 출력.</span><span class="sxs-lookup"><span data-stu-id="77b42-143">No Match output.</span></span> <span data-ttu-id="77b42-144">불일치 항목 출력은 참조 데이터 세트와 하나의 항목도 일치하지 않는 입력 행을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-144">The no match output handles rows in the input that do not match at least one entry in the reference dataset.</span></span> <span data-ttu-id="77b42-145">일치하는 항목이 없는 행을 오류로 처리하도록 조회 변환을 구성하면 해당 행이 오류 출력으로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-145">If you configure the Lookup transformation to treat the rows without matching entries as errors, the rows are redirected to the error output.</span></span> <span data-ttu-id="77b42-146">그렇지 않으면 변환이 이러한 행을 불일치 항목 출력으로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-146">Otherwise, the transformation would redirect those rows to the no match output.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="77b42-147">[!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)]에서는 조회 변환에 하나의 출력만 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-147">In [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)], the Lookup transformation had only one output.</span></span> <span data-ttu-id="77b42-148">에서 만든 조회 변환을 실행 하는 방법에 대 한 자세한 내용은 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] [조회 변환 업그레이드](../../../sql-server/install/upgrade-lookup-transformations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="77b42-148">For more information about how to run a Lookup transformation that was created in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], see [Upgrade Lookup Transformations](../../../sql-server/install/upgrade-lookup-transformations.md).</span></span>  
  
-   <span data-ttu-id="77b42-149">오류 출력.</span><span class="sxs-lookup"><span data-stu-id="77b42-149">Error output.</span></span>  
  
## <a name="caching-the-reference-dataset"></a><span data-ttu-id="77b42-150">참조 데이터 세트 캐싱</span><span class="sxs-lookup"><span data-stu-id="77b42-150">Caching the Reference Dataset</span></span>  
 <span data-ttu-id="77b42-151">메모리 내 캐시는 참조 데이터 세트와 이러한 데이터를 인덱싱하는 해시 테이블을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-151">An in-memory cache stores the reference dataset and stores a hash table that indexes the data.</span></span> <span data-ttu-id="77b42-152">캐시는 패키지 실행이 완료될 때까지 메모리에 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-152">The cache remains in memory until the execution of the package is completed.</span></span> <span data-ttu-id="77b42-153">캐시를 캐시 파일(.caw)로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-153">You can persist the cache to a cache file (.caw).</span></span>  
  
 <span data-ttu-id="77b42-154">캐시를 파일로 저장하면 시스템에서 캐시를 더 빠르게 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-154">When you persist the cache to a file, the system loads the cache faster.</span></span> <span data-ttu-id="77b42-155">따라서 조회 변환 및 패키지의 성능도 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-155">This improves the performance of the Lookup transformation and the package.</span></span> <span data-ttu-id="77b42-156">캐시 파일을 사용할 때는 데이터베이스에 있는 현재 데이터가 아닌 다른 데이터를 사용하고 있다는 점을 유념하십시오.</span><span class="sxs-lookup"><span data-stu-id="77b42-156">Remember, that when you use a cache file, you are working with data that is not as current as the data in the database.</span></span>  
  
 <span data-ttu-id="77b42-157">캐시를 파일로 저장할 경우의 추가 이점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-157">The following are additional benefits of persisting the cache to a file:</span></span>  
  
-   <span data-ttu-id="77b42-158">***여러 패키지 간에 캐시 파일을 공유 합니다. 자세한 내용은***[캐시 연결 관리자를 사용 하 여 전체 캐시 모드에서 조회 변환 구현](../../connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md)을 참조 하세요 ***.***    </span><span class="sxs-lookup"><span data-stu-id="77b42-158">***Share the cache file between multiple packages. For more information, see***  [Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager](../../connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md)  ***.***</span></span>  
  
-   <span data-ttu-id="77b42-159">패키지와 함께 캐시 파일을 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-159">Deploy the cache file with a package.</span></span> <span data-ttu-id="77b42-160">***그러면 데이터를 여러 컴퓨터에서 사용할 수 있습니다.***</span><span class="sxs-lookup"><span data-stu-id="77b42-160">***You can then use the data on multiple computers.***</span></span> <span data-ttu-id="77b42-161">자세한 내용은 [조회 변환에 대한 캐시 만들기 및 배포](create-and-deploy-a-cache-for-the-lookup-transformation.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="77b42-161">For more information, see [Create and Deploy a Cache for the Lookup Transformation](create-and-deploy-a-cache-for-the-lookup-transformation.md).</span></span>  
  
-   <span data-ttu-id="77b42-162">원시 파일 원본을 사용하여 캐시 파일에서 데이터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-162">Use the Raw File source to read data from the cache file.</span></span> <span data-ttu-id="77b42-163">그러면 다른 데이터 흐름 구성 요소를 사용하여 데이터를 변환하거나 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-163">You can then use other data flow components to transform or move the data.</span></span> <span data-ttu-id="77b42-164">자세한 내용은 [Raw File Source](../raw-file-source.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="77b42-164">For more information, see [Raw File Source](../raw-file-source.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="77b42-165">캐시 연결 관리자는 원시 파일 대상을 사용하여 캐시 파일을 만들거나 수정하도록 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-165">The Cache connection manager does not support cache files that are created or modified by using the Raw File destination.</span></span>  
  
-   <span data-ttu-id="77b42-166">파일 시스템 태스크를 사용하여 캐시 파일에서 작업을 수행하고 특성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-166">Perform operations and set attributes on the cache file by using the File System task.</span></span> <span data-ttu-id="77b42-167">자세한 내용은 [File System Task](../../control-flow/file-system-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="77b42-167">For more information, see and [File System Task](../../control-flow/file-system-task.md).</span></span>  
  
 <span data-ttu-id="77b42-168">캐싱 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-168">The following are the caching options:</span></span>  
  
-   <span data-ttu-id="77b42-169">조회 변환이 실행되기 전에 테이블, 뷰 또는 SQL 쿼리를 사용하여 참조 데이터 세트가 생성되고 캐시에 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-169">The reference dataset is generated by using a table, view, or SQL query and loaded into cache, before the Lookup transformation runs.</span></span> <span data-ttu-id="77b42-170">OLE DB 연결 관리자를 사용하여 데이터 세트에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-170">You use the OLE DB connection manager to access the dataset.</span></span>  
  
     <span data-ttu-id="77b42-171">이 캐싱 옵션은 [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)]의 조회 변환에서 제공되는 전체 캐싱 옵션과 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-171">This caching option is compatible with the full caching option that is available for the Lookup transformation in [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)].</span></span>  
  
-   <span data-ttu-id="77b42-172">조회 변환이 실행되기 전에 데이터 흐름의 연결된 데이터 원본 또는 캐시 파일로부터 참조 데이터 세트가 생성되고 캐시에 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-172">The reference dataset is generated from a connected data source in the data flow or from a cache file, and is loaded into cache before the Lookup transformation runs.</span></span> <span data-ttu-id="77b42-173">캐시 연결 관리자 및 캐시 변환(선택 사항)을 사용하여 데이터 세트에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-173">You use the Cache connection manager, and, optionally, the Cache transformation, to access the dataset.</span></span> <span data-ttu-id="77b42-174">자세한 내용은 [Cache Connection Manager](../../connection-manager/cache-connection-manager.md) 및 [Cache Transform](cache-transform.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="77b42-174">For more information, see [Cache Connection Manager](../../connection-manager/cache-connection-manager.md) and [Cache Transform](cache-transform.md).</span></span>  
  
-   <span data-ttu-id="77b42-175">조회 변환이 실행되는 동안 테이블, 뷰 또는 SQL 쿼리를 사용하여 참조 데이터 세트가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-175">The reference dataset is generated by using a table, view, or SQL query during the execution of the Lookup transformation.</span></span> <span data-ttu-id="77b42-176">참조 데이터 세트와 일치하는 항목이 있는 행과 일치하는 항목이 없는 행이 캐시에 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-176">The rows with matching entries in the reference dataset and the rows without matching entries in the dataset are loaded into cache.</span></span>  
  
     <span data-ttu-id="77b42-177">캐시의 메모리 크기를 초과하면 조회 변환은 자동으로 캐시에서 가장 사용 빈도가 낮은 행을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-177">When the memory size of the cache is exceeded, the Lookup transformation automatically removes the least frequently used rows from the cache.</span></span>  
  
     <span data-ttu-id="77b42-178">이 캐싱 옵션은 [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)]의 조회 변환에서 제공되는 부분 캐싱 옵션과 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-178">This caching option is compatible with the partial caching option that is available for the Lookup transformation in [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)].</span></span>  
  
-   <span data-ttu-id="77b42-179">조회 변환이 실행되는 동안 테이블, 뷰 또는 SQL 쿼리를 사용하여 참조 데이터 세트가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-179">The reference dataset is generated by using a table, view, or SQL query during the execution of the Lookup transformation.</span></span> <span data-ttu-id="77b42-180">캐시되는 데이터는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-180">No data is cached.</span></span>  
  
     <span data-ttu-id="77b42-181">이 캐싱 옵션은 [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)]의 조회 변환에서 제공되는 캐싱 없음 옵션과 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-181">This caching option is compatible with the no caching option that is available for the Lookup transformation in [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)].</span></span>  
  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="77b42-182">와 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 문자열 비교 방식에는 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-182">and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] differ in the way they compare strings.</span></span> <span data-ttu-id="77b42-183">조회 변환이 실행되기 전에 참조 데이터 세트를 캐시로 로드하도록 조회 변환이 구성된 경우 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]는 캐시에서 조회 비교를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-183">If the Lookup transformation is configured to load the reference dataset into cache before the Lookup transformation runs, [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] does the lookup comparison in the cache.</span></span> <span data-ttu-id="77b42-184">그렇지 않으면 조회 작업에서 매개 변수가 있는 SQL 문을 사용하고 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에서 조회 비교를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-184">Otherwise, the lookup operation uses a parameterized SQL statement and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does the lookup comparison.</span></span> <span data-ttu-id="77b42-185">이는 캐시 유형에 따라 조회 변환이 동일한 조회 테이블에서 다른 개수의 일치하는 항목을 반환할 수 있다는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-185">This means that the Lookup transformation might return a different number of matches from the same lookup table depending on the cache type.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="77b42-186">관련 작업</span><span class="sxs-lookup"><span data-stu-id="77b42-186">Related Tasks</span></span>  
 <span data-ttu-id="77b42-187">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77b42-187">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span> <span data-ttu-id="77b42-188">자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="77b42-188">For more details, see the following topics.</span></span>  
  
-   [<span data-ttu-id="77b42-189">캐시 없음 또는 부분 캐시 모드로 조회 구현</span><span class="sxs-lookup"><span data-stu-id="77b42-189">Implement a Lookup in No Cache or Partial Cache Mode</span></span>](implement-a-lookup-in-no-cache-or-partial-cache-mode.md)  
  
-   [<span data-ttu-id="77b42-190">캐시 연결 관리자 변환을 사용하여 전체 캐시 모드에서 조회 변환 구현</span><span class="sxs-lookup"><span data-stu-id="77b42-190">Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager</span></span>](../../connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md)  
  
-   [<span data-ttu-id="77b42-191">OLE DB 연결 관리자를 사용하여 전체 캐시 모드에서 조회 변환 구현</span><span class="sxs-lookup"><span data-stu-id="77b42-191">Implement a Lookup Transformation in Full Cache Mode Using the OLE DB Connection Manager</span></span>](../../connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md)  
  
-   [<span data-ttu-id="77b42-192">데이터 흐름 구성 요소의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="77b42-192">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a><span data-ttu-id="77b42-193">관련 내용</span><span class="sxs-lookup"><span data-stu-id="77b42-193">Related Content</span></span>  
  
-   <span data-ttu-id="77b42-194">msdn.microsoft.com의 비디오 - [방법: 전체 캐시 모드에서 조회 변환 구현](https://go.microsoft.com/fwlink/?LinkId=131031)</span><span class="sxs-lookup"><span data-stu-id="77b42-194">Video, [How to: Implement a Lookup Transformation in Full Cache Mode](https://go.microsoft.com/fwlink/?LinkId=131031), on msdn.microsoft.com</span></span>  
  
-   <span data-ttu-id="77b42-195">blogs.msdn.com의 블로그 항목 - [조회 변환 캐시 모드를 사용하는 최선의 구현 방법(Best Practices for Using the Lookup Transformation Cache Modes)](https://go.microsoft.com/fwlink/?LinkId=146623)</span><span class="sxs-lookup"><span data-stu-id="77b42-195">Blog entry, [Best Practices for Using the Lookup Transformation Cache Modes](https://go.microsoft.com/fwlink/?LinkId=146623), on blogs.msdn.com</span></span>  
  
-   <span data-ttu-id="77b42-196">blogs.msdn.com의 블로그 항목 - [조회 패턴: 대/소문자 구분 안 함](https://go.microsoft.com/fwlink/?LinkId=157782)</span><span class="sxs-lookup"><span data-stu-id="77b42-196">Blog entry, [Lookup Pattern: Case Insensitive](https://go.microsoft.com/fwlink/?LinkId=157782), on blogs.msdn.com</span></span>  
  
-   <span data-ttu-id="77b42-197">msftisprodsamples.codeplex.com의 예제 - [조회 변환](https://go.microsoft.com/fwlink/?LinkId=267528)</span><span class="sxs-lookup"><span data-stu-id="77b42-197">Sample, [Lookup Transformation](https://go.microsoft.com/fwlink/?LinkId=267528), on msftisprodsamples.codeplex.com.</span></span>  
  
     <span data-ttu-id="77b42-198">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 제품 예제 및 예제 데이터베이스를 설치하는 방법은 [SQL Server Integration Services 제품 예제](https://go.microsoft.com/fwlink/?LinkId=267527)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="77b42-198">For information on installing [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] product samples and sample databases, see [SQL Server Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=267527).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77b42-199">참고 항목</span><span class="sxs-lookup"><span data-stu-id="77b42-199">See Also</span></span>  
 <span data-ttu-id="77b42-200">[유사 항목 조회 변환](fuzzy-lookup-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="77b42-200">[Fuzzy Lookup Transformation](fuzzy-lookup-transformation.md) </span></span>  
 <span data-ttu-id="77b42-201">[용어 조회 변환](term-lookup-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="77b42-201">[Term Lookup Transformation](term-lookup-transformation.md) </span></span>  
 <span data-ttu-id="77b42-202">[데이터 흐름](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="77b42-202">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="77b42-203">Integration Services 변환</span><span class="sxs-lookup"><span data-stu-id="77b42-203">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
