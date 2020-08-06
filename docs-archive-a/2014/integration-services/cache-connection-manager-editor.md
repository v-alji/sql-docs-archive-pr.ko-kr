---
title: 캐시 연결 관리자 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.cacheconnection.f1
ms.assetid: 0d8f9324-0c35-4eea-b06d-da3cc2426d2c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 38a858217925496d8dd937d684368bdb2e061b14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660099"
---
# <a name="cache-connection-manager-editor"></a><span data-ttu-id="390ec-102">캐시 연결 관리자 편집기</span><span class="sxs-lookup"><span data-stu-id="390ec-102">Cache Connection Manager Editor</span></span>
  <span data-ttu-id="390ec-103">캐시 연결 관리자는 캐시 변환이나 캐시 파일(.caw)에서 참조 데이터 세트를 읽고 데이터를 캐시 파일에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-103">The Cache connection manager reads a reference dataset from the Cache transform or from a cache file (.caw), and can save the data to a cache file.</span></span> <span data-ttu-id="390ec-104">데이터는 항상 메모리에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-104">The data is always stored in memory.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="390ec-105">캐시 연결 관리자는 BLOB(Binary Large Object) 데이터 형식 DT_TEXT, DT_NTEXT 및 DT_IMAGE를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-105">The Cache connection manager does not support the Binary Large Object (BLOB) data types DT_TEXT, DT_NTEXT, and DT_IMAGE.</span></span> <span data-ttu-id="390ec-106">참조 데이터 세트에 BLOB 데이터 형식이 있으면 패키지를 실행할 때 구성 요소가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-106">If the reference dataset contains a BLOB data type, the component will fail when you run the package.</span></span> <span data-ttu-id="390ec-107">**캐시 연결 관리자 편집기** 를 사용하여 열 데이터 형식을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-107">You can use the **Cache Connection Manager Editor** to modify column data types.</span></span>  
  
 <span data-ttu-id="390ec-108">조회 변환은 참조 데이터 세트에 대해 조회를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-108">The Lookup transformation performs lookups on the reference dataset.</span></span>  
  
 <span data-ttu-id="390ec-109">**캐시 연결 관리자 편집기** 대화 상자에는 다음과 같은 탭이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-109">The **Cache Connection ManagerEditor** dialog box includes the following tabs:</span></span>  
  
-   [<span data-ttu-id="390ec-110">일반 탭</span><span class="sxs-lookup"><span data-stu-id="390ec-110">General tab</span></span>](#generaltab)  
  
-   [<span data-ttu-id="390ec-111">열 탭</span><span class="sxs-lookup"><span data-stu-id="390ec-111">Columns tab</span></span>](#columnstab)  
  
 <span data-ttu-id="390ec-112">캐시 연결 관리자에 대 한 자세한 내용은 [Cache Connection manager](connection-manager/cache-connection-manager.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="390ec-112">To learn more about the Cache Connection Manager, see [Cache Connection Manager](connection-manager/cache-connection-manager.md).</span></span>  
  
##  <a name="general-tab"></a><a name="generaltab"></a><span data-ttu-id="390ec-113">일반 탭</span><span class="sxs-lookup"><span data-stu-id="390ec-113">General Tab</span></span>  
 <span data-ttu-id="390ec-114">**캐시 연결 관리자 편집기** 대화 상자의 **일반** 탭을 사용하여 파일에서 캐시를 읽을지 아니면 파일에 캐시를 저장할지 여부를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-114">Use the **General** tab of the **Cache Connection ManagerEditor** dialog box to indicate whether to read the cache from a file or save the cache to a file.</span></span>  
  
### <a name="options"></a><span data-ttu-id="390ec-115">옵션</span><span class="sxs-lookup"><span data-stu-id="390ec-115">Options</span></span>  
 <span data-ttu-id="390ec-116">**연결 관리자 이름**</span><span class="sxs-lookup"><span data-stu-id="390ec-116">**Connection manager name**</span></span>  
 <span data-ttu-id="390ec-117">워크플로의 캐시 연결에 고유한 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-117">Provide a unique name for the cache connection in the workflow.</span></span> <span data-ttu-id="390ec-118">제공한 이름은 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-118">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="390ec-119">**설명**</span><span class="sxs-lookup"><span data-stu-id="390ec-119">**Description**</span></span>  
 <span data-ttu-id="390ec-120">연결에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-120">Describe the connection.</span></span> <span data-ttu-id="390ec-121">해당 연결의 용도를 설명하여 패키지를 이해하기 쉽고 유지 관리하기 편하도록 만드는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-121">As a best practice, describe the connection according to its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="390ec-122">**파일 캐시 사용**</span><span class="sxs-lookup"><span data-stu-id="390ec-122">**Use file cache**</span></span>  
 <span data-ttu-id="390ec-123">캐시 파일을 사용할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-123">Indicate whether to use a cache file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="390ec-124">패키지의 보호 수준은 캐시 파일에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-124">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="390ec-125">캐시 파일에 중요한 정보가 들어 있는 경우 ACL(액세스 제어 목록)을 사용하여 파일 저장 위치 또는 폴더에 대한 액세스를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-125">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="390ec-126">특정 계정에 대해서만 액세스를 허용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-126">You should enable access only to certain accounts.</span></span> <span data-ttu-id="390ec-127">자세한 내용은 [패키지에서 사용되는 파일 액세스](../../2014/integration-services/access-to-files-used-by-packages.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="390ec-127">For more information, see [Access to Files Used by Packages](../../2014/integration-services/access-to-files-used-by-packages.md).</span></span>  
  
 <span data-ttu-id="390ec-128">캐시 파일을 사용하도록 캐시 연결 관리자를 구성하면 연결 관리자는 다음 동작 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-128">If you configure the cache connection manager to use a cache file, the connection manager will do one of the following actions:</span></span>  
  
-   <span data-ttu-id="390ec-129">캐시 변환이 데이터 흐름에 있는 데이터 원본의 데이터를 캐시 연결 관리자에 기록하도록 구성된 경우 데이터를 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-129">Save data to the file when a Cache Transform transformation is configured to write data from a data source in the data flow to the Cache connection manager.</span></span> <span data-ttu-id="390ec-130">자세한 내용은 [Cache Transform](data-flow/transformations/cache-transform.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="390ec-130">For more information, see [Cache Transform](data-flow/transformations/cache-transform.md).</span></span>  
  
-   <span data-ttu-id="390ec-131">캐시 파일에서 데이터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-131">Read data from the cache file.</span></span>  
  
 <span data-ttu-id="390ec-132">**파일 이름**</span><span class="sxs-lookup"><span data-stu-id="390ec-132">**File name**</span></span>  
 <span data-ttu-id="390ec-133">캐시 파일의 경로와 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-133">Type the path and file name of the cache file.</span></span>  
  
 <span data-ttu-id="390ec-134">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="390ec-134">**Browse**</span></span>  
 <span data-ttu-id="390ec-135">캐시 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-135">Locate the cache file.</span></span>  
  
 <span data-ttu-id="390ec-136">**메타데이터 새로 고침**</span><span class="sxs-lookup"><span data-stu-id="390ec-136">**Refresh Metadata**</span></span>  
 <span data-ttu-id="390ec-137">캐시 연결 관리자에서 열 메타데이터를 삭제하고 선택한 캐시 파일의 열 메타데이터로 캐시 연결 관리자를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-137">Delete the column metadata in the Cache connection manager and repopulate the Cache connection manager with column metadata from a selected cache file.</span></span>  
  
##  <a name="columns-tab"></a><a name="columnstab"></a><span data-ttu-id="390ec-138">열 탭</span><span class="sxs-lookup"><span data-stu-id="390ec-138">Columns Tab</span></span>  
 <span data-ttu-id="390ec-139">**캐시 연결 관리자 편집기** 대화 상자의 **열** 탭을 사용하여 캐시에 있는 각 열의 속성을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-139">Use the **Columns** tab of the **Cache Connection Manager Editor** dialog box to configure the properties of each column in the cache.</span></span>  
  
### <a name="options"></a><span data-ttu-id="390ec-140">옵션</span><span class="sxs-lookup"><span data-stu-id="390ec-140">Options</span></span>  
 <span data-ttu-id="390ec-141">**열**</span><span class="sxs-lookup"><span data-stu-id="390ec-141">**Column**</span></span>  
 <span data-ttu-id="390ec-142">열 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-142">Specify the column name.</span></span>  
  
 <span data-ttu-id="390ec-143">**인덱스 위치**</span><span class="sxs-lookup"><span data-stu-id="390ec-143">**Index Position**</span></span>  
 <span data-ttu-id="390ec-144">각 열의 인덱스 위치를 지정하여 인덱스 열이 되는 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-144">Specify which columns are index columns by specifying the index position of each column.</span></span> <span data-ttu-id="390ec-145">인덱스는 하나 이상의 열로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-145">The index is a collection of one or more columns.</span></span>  
  
 <span data-ttu-id="390ec-146">비인덱스 열의 경우 인덱스 위치는 0입니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-146">For non-index columns, the index position is 0.</span></span>  
  
 <span data-ttu-id="390ec-147">인덱스 열의 경우 인덱스 위치는 일련의 양수입니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-147">For index columns, the index position is a sequential, positive number.</span></span> <span data-ttu-id="390ec-148">이 번호는 조회 변환이 참조 데이터 세트의 행을 입력 데이터 원본의 행과 비교하는 순서를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-148">This number indicates the order in which the Lookup transformation compares rows in the reference dataset to rows in the input data source.</span></span> <span data-ttu-id="390ec-149">가장 고유한 값을 포함하는 열의 인덱스 위치는 가장 낮아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-149">The column with the most unique values should have the lowest index position.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="390ec-150">조회 변환은 캐시 연결 관리자를 사용하도록 구성된 경우 참조 데이터 세트의 인덱스 열만 입력 열에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-150">When the Lookup transformation is configured to use a Cache connection manager, only index columns in the reference dataset can be mapped to input columns.</span></span> <span data-ttu-id="390ec-151">또한 모든 인덱스 열을 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-151">Also, all index columns must be mapped.</span></span>  
  
 <span data-ttu-id="390ec-152">**형식**</span><span class="sxs-lookup"><span data-stu-id="390ec-152">**Type**</span></span>  
 <span data-ttu-id="390ec-153">열의 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-153">Specify the data type of the column.</span></span>  
  
 `Length`  
 <span data-ttu-id="390ec-154">열 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-154">Specifies the column data type.</span></span> <span data-ttu-id="390ec-155">데이터 형식에 적용 가능한 경우 `Length`를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-155">If applicable to the data type, you can update `Length`.</span></span>  
  
 `Precision`  
 <span data-ttu-id="390ec-156">특정 열 데이터 형식에 대한 전체 자릿수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-156">Specifies the precision for certain column data types.</span></span> <span data-ttu-id="390ec-157">전체 자릿수는 숫자의 모든 자릿수이고</span><span class="sxs-lookup"><span data-stu-id="390ec-157">Precision is the number of digits in a number.</span></span> <span data-ttu-id="390ec-158">데이터 형식에 적용 가능한 경우 `Precision`를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-158">If applicable to the data type, you can update `Precision`.</span></span>  
  
 `Scale`  
 <span data-ttu-id="390ec-159">특정 열 데이터 형식에 대한 소수 자릿수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-159">Specifies the scale for certain column data types.</span></span> <span data-ttu-id="390ec-160">소수 자릿수는 숫자에서 소수점 오른쪽에 있는 자릿수입니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-160">Scale is the number of digits to the right of the decimal point in a number.</span></span> <span data-ttu-id="390ec-161">데이터 형식에 적용 가능한 경우 `Scale`를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-161">If applicable to the data type, you can update `Scale`.</span></span>  
  
 `Code Page`  
 <span data-ttu-id="390ec-162">열 형식에 대한 코드 페이지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-162">Specifies the code page for the column type.</span></span> <span data-ttu-id="390ec-163">데이터 형식에 적용 가능한 경우 `Code Page`를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="390ec-163">If applicable to the data type, you can update `Code Page`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="390ec-164">참고 항목</span><span class="sxs-lookup"><span data-stu-id="390ec-164">See Also</span></span>  
 [<span data-ttu-id="390ec-165">조회 변환</span><span class="sxs-lookup"><span data-stu-id="390ec-165">Lookup Transformation</span></span>](data-flow/transformations/lookup-transformation.md)  
  
  
