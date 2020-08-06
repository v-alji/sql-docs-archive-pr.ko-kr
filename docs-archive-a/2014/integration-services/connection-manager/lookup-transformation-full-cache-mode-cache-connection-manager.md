---
title: 캐시 연결 관리자를 사용 하 여 전체 캐시 모드에서 조회 변환 구현 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Lookup transformation [Integration Services]
ms.assetid: 58bc7611-5fb5-4113-9742-10959e06b94c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8b8c77f7ecfbe79db00acce09f706468ec0a0055
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659611"
---
# <a name="implement-a-lookup-transformation-in-full-cache-mode-using-the-cache-connection-manager"></a><span data-ttu-id="6f0d1-102">캐시 연결 관리자 변환을 사용하여 전체 캐시 모드에서 조회 변환 구현</span><span class="sxs-lookup"><span data-stu-id="6f0d1-102">Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager</span></span>
  <span data-ttu-id="6f0d1-103">전체 캐시 모드와 캐시 연결 관리자를 사용하도록 조회 변환을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-103">You can configure the Lookup transformation to use full cache mode and a Cache connection manager.</span></span> <span data-ttu-id="6f0d1-104">전체 캐시 모드에서 조회 변환이 실행되기 전에 참조 데이터 세트가 캐시에 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-104">In full cache mode, the reference dataset is loaded into cache before the Lookup transformation runs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f0d1-105">캐시 연결 관리자는 BLOB(Binary Large Object) 데이터 형식 DT_TEXT, DT_NTEXT 및 DT_IMAGE를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-105">The Cache connection manager does not support the Binary Large Object (BLOB) data types DT_TEXT, DT_NTEXT, and DT_IMAGE.</span></span> <span data-ttu-id="6f0d1-106">참조 데이터 세트에 BLOB 데이터 형식이 있으면 패키지를 실행할 때 구성 요소가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-106">If the reference dataset contains a BLOB data type, the component will fail when you run the package.</span></span> <span data-ttu-id="6f0d1-107">**캐시 연결 관리자 편집기** 를 사용하여 열 데이터 형식을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-107">You can use the **Cache Connection Manager Editor** to modify column data types.</span></span> <span data-ttu-id="6f0d1-108">자세한 내용은 [Cache Connection Manager Editor](../cache-connection-manager-editor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-108">For more information, see [Cache Connection Manager Editor](../cache-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="6f0d1-109">조회 변환은 연결된 데이터 원본의 입력 열에 있는 데이터를 참조 데이터 세트의 열과 조인하여 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-109">The Lookup transformation performs lookups by joining data in input columns from a connected data source with columns in a reference dataset.</span></span> <span data-ttu-id="6f0d1-110">자세한 내용은 [Lookup Transformation](../data-flow/transformations/lookup-transformation.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-110">For more information, see [Lookup Transformation](../data-flow/transformations/lookup-transformation.md).</span></span>  
  
 <span data-ttu-id="6f0d1-111">다음 중 하나를 사용하여 참조 데이터 세트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-111">You use one of the following to generate a reference dataset:</span></span>  
  
-   <span data-ttu-id="6f0d1-112">캐시 파일(.caw)</span><span class="sxs-lookup"><span data-stu-id="6f0d1-112">Cache file (.caw)</span></span>  
  
     <span data-ttu-id="6f0d1-113">기존 캐시 파일에서 데이터를 읽도록 캐시 연결 관리자를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-113">You configure the Cache connection manager to read data from an existing cache file.</span></span>  
  
-   <span data-ttu-id="6f0d1-114">데이터 흐름에 있는 연결된 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="6f0d1-114">Connected data source in the data flow</span></span>  
  
     <span data-ttu-id="6f0d1-115">캐시 변환을 사용하여 데이터 흐름에 있는 연결된 데이터 원본의 데이터를 캐시 연결 관리자에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-115">You use a Cache Transform transformation to write data from a connected data source in the data flow to a Cache connection manager.</span></span> <span data-ttu-id="6f0d1-116">데이터는 항상 메모리에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-116">The data is always stored in memory.</span></span>  
  
     <span data-ttu-id="6f0d1-117">조회 변환을 별도의 데이터 흐름에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-117">You must add the Lookup transformation to a separate data flow.</span></span> <span data-ttu-id="6f0d1-118">그러면 조회 변환이 실행되기 전에 캐시 변환이 캐시 연결 관리자를 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-118">This enables the Cache Transform to populate the Cache connection manager before the Lookup transformation is executed.</span></span> <span data-ttu-id="6f0d1-119">데이터 흐름은 같은 패키지나 두 개의 별도 패키지에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-119">The data flows can be in the same package or in two separate packages.</span></span>  
  
     <span data-ttu-id="6f0d1-120">데이터 흐름이 같은 패키지에 있으면 선행 제약 조건을 사용하여 데이터 흐름에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-120">If the data flows are in the same package, use a precedence constraint to connect the data flows.</span></span> <span data-ttu-id="6f0d1-121">그러면 조회 변환이 실행되기 전에 캐시 변환을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-121">This enables the Cache Transform to run before the Lookup transformation runs.</span></span>  
  
     <span data-ttu-id="6f0d1-122">데이터 흐름이 별도의 패키지에 있으면 패키지 실행 태스크를 사용하여 부모 패키지에서 자식 패키지를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-122">If the data flows are in separate packages, you can use the Execute Package task to call the child package from the parent package.</span></span> <span data-ttu-id="6f0d1-123">여러 개의 패키지 실행 태스크를 부모 패키지의 시퀀스 컨테이너 태스크에 추가하여 여러 개의 자식 패키지를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-123">You can call multiple child packages by adding multiple Execute Package tasks to a Sequence Container task in the parent package.</span></span>  
  
 <span data-ttu-id="6f0d1-124">다음 방법 중 하나를 사용하여 여러 개의 조회 변환 간에 캐시에 저장된 참조 데이터 세트를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-124">You can share the reference dataset stored in cache, between multiple Lookup transformations by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="6f0d1-125">같은 캐시 연결 관리자를 사용하도록 단일 패키지에 조회 변환 구성</span><span class="sxs-lookup"><span data-stu-id="6f0d1-125">Configure the Lookup transformations in a single package to use the same Cache connection manager.</span></span>  
  
-   <span data-ttu-id="6f0d1-126">같은 캐시 파일을 사용하도록 다른 패키지에 캐시 연결 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="6f0d1-126">Configure the Cache connection managers in different packages to use the same cache file.</span></span>  
  
 <span data-ttu-id="6f0d1-127">자세한 내용은 아래 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-127">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="6f0d1-128">캐시 변환</span><span class="sxs-lookup"><span data-stu-id="6f0d1-128">Cache Transform</span></span>](../data-flow/transformations/cache-transform.md)  
  
-   [<span data-ttu-id="6f0d1-129">캐시 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="6f0d1-129">Cache Connection Manager</span></span>](cache-connection-manager.md)  
  
-   [<span data-ttu-id="6f0d1-130">선행 제약 조건</span><span class="sxs-lookup"><span data-stu-id="6f0d1-130">Precedence Constraints</span></span>](../control-flow/precedence-constraints.md)  
  
-   [<span data-ttu-id="6f0d1-131">패키지 실행 태스크</span><span class="sxs-lookup"><span data-stu-id="6f0d1-131">Execute Package Task</span></span>](../control-flow/execute-package-task.md)  
  
-   [<span data-ttu-id="6f0d1-132">시퀀스 컨테이너</span><span class="sxs-lookup"><span data-stu-id="6f0d1-132">Sequence Container</span></span>](../control-flow/sequence-container.md)  
  
 <span data-ttu-id="6f0d1-133">캐시 연결 관리자를 사용하여 전체 캐시 모드에서 조회 변환을 구현하는 방법을 보여 주는 비디오는 [방법: 전체 캐시 모드에서 조회 변환 구현(SQL Server 비디오)](https://go.microsoft.com/fwlink/?LinkId=131031)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-133">For a video that demonstrates how to implement a Lookup transformation in Full Cache mode using the Cache connection manager, see [How to: Implement a Lookup Transformation in Full Cache Mode (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=131031).</span></span>  
  
### <a name="to-implement-a-lookup-transformation-in-full-cache-mode-in-one-package-by-using-cache-connection-manager-and-a-data-source-in-the-data-flow"></a><span data-ttu-id="6f0d1-134">데이터 흐름의 데이터 원본과 캐시 연결 관리자를 사용하여 조회 변환을 한 개의 패키지에서 전체 캐시 모드로 구현하려면</span><span class="sxs-lookup"><span data-stu-id="6f0d1-134">To implement a Lookup transformation in full cache mode in one package by using Cache connection manager and a data source in the data flow</span></span>  
  
1.  <span data-ttu-id="6f0d1-135">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 연 다음 하나의 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-135">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open a [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project, and then open a package.</span></span>  
  
2.  <span data-ttu-id="6f0d1-136">**흐름 제어** 탭에서 두 개의 데이터 흐름 태스크를 추가한 다음 녹색 연결선을 사용하여 태스크를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-136">On the **Control Flow** tab, add two Data Flow tasks, and then connect the tasks by using a green connector:</span></span>  
  
3.  <span data-ttu-id="6f0d1-137">첫 번째 데이터 흐름에서 캐시 변환을 추가한 다음 데이터 원본에 변환을 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-137">In the first data flow, add a Cache Transform transformation, and then connect the transformation to a data source.</span></span>  
  
     <span data-ttu-id="6f0d1-138">필요한 경우 데이터 원본을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-138">Configure the data source as needed.</span></span>  
  
4.  <span data-ttu-id="6f0d1-139">캐시 변환을 두 번 클릭한 다음 **캐시 변환 편집기**의 **연결 관리자** 페이지에서 **새로 만들기** 를 클릭하여 새 캐시 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-139">Double-click the Cache Transform, and then in the **Cache Transformation Editor**, on the **Connection Manager** page, click **New** to create a new Cache connection manager.</span></span>  
  
5.  <span data-ttu-id="6f0d1-140">**캐시 연결 관리자 편집기** 대화 상자의 **열** 탭을 클릭한 다음 **인덱스 위치** 옵션을 사용하여 인덱스 열이 되는 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-140">Click the **Columns** tab of the **Cache Connection Manager Editor** dialog box, and then specify which columns are the index columns by using the **Index Position** option.</span></span>  
  
     <span data-ttu-id="6f0d1-141">비인덱스 열의 경우 인덱스 위치는 0입니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-141">For non-index columns, the index position is 0.</span></span> <span data-ttu-id="6f0d1-142">인덱스 열의 경우 인덱스 위치는 일련의 양수입니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-142">For index columns, the index position is a sequential, positive number.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6f0d1-143">조회 변환은 캐시 연결 관리자를 사용하도록 구성된 경우 참조 데이터 세트의 인덱스 열만 입력 열에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-143">When the Lookup transformation is configured to use a Cache connection manager, only index columns in the reference dataset can be mapped to input columns.</span></span> <span data-ttu-id="6f0d1-144">또한 모든 인덱스 열을 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-144">Also, all index columns must be mapped.</span></span> <span data-ttu-id="6f0d1-145">자세한 내용은 [Cache Connection Manager Editor](../cache-connection-manager-editor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-145">For more information, see [Cache Connection Manager Editor](../cache-connection-manager-editor.md).</span></span>  
  
6.  <span data-ttu-id="6f0d1-146">캐시를 파일에 저장하려면 **캐시 연결 관리자 편집기**의 **일반** 탭에서 다음 옵션을 설정하여 캐시 연결 관리자를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-146">To save the cache to a file, in the **Cache Connection Manager Editor**, on the **General** tab, configure the Cache connection manager by setting the following options:</span></span>  
  
    -   <span data-ttu-id="6f0d1-147">**파일 캐시 사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-147">Select **Use file cache**.</span></span>  
  
    -   <span data-ttu-id="6f0d1-148">**파일 이름**에 파일 경로를 입력하거나 **찾아보기** 를 클릭하여 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-148">For **File name**, either type the file path or click **Browse** to select the file.</span></span>  
  
         <span data-ttu-id="6f0d1-149">존재하지 않는 파일의 경로를 입력하면 패키지를 실행할 때 시스템이 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-149">If you type a path for a file that does not exist, the system creates the file when you run the package.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6f0d1-150">패키지의 보호 수준은 캐시 파일에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-150">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="6f0d1-151">캐시 파일에 중요한 정보가 들어 있는 경우 ACL(액세스 제어 목록)을 사용하여 파일 저장 위치 또는 폴더에 대한 액세스를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-151">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="6f0d1-152">특정 계정에 대해서만 액세스를 허용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-152">You should enable access only to certain accounts.</span></span> <span data-ttu-id="6f0d1-153">자세한 내용은 [패키지에서 사용되는 파일 액세스](../access-to-files-used-by-packages.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-153">For more information, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
7.  <span data-ttu-id="6f0d1-154">필요한 경우 캐시 변환을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-154">Configure the Cache Transform as needed.</span></span> <span data-ttu-id="6f0d1-155">자세한 내용은 [캐시 변환 편집기&#40;연결 관리자 페이지&#41;](../cache-transformation-editor-connection-manager-page.md) 및 [캐시 변환 편집기&#40;매핑 페이지&#41;](../cache-transformation-editor-mappings-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-155">For more information, see [Cache Transformation Editor &#40;Connection Manager Page&#41;](../cache-transformation-editor-connection-manager-page.md) and [Cache Transformation Editor &#40;Mappings Page&#41;](../cache-transformation-editor-mappings-page.md).</span></span>  
  
8.  <span data-ttu-id="6f0d1-156">두 번째 데이터 흐름에서 조회 변환을 추가한 후 다음 태스크를 수행하여 변환을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-156">In the second data flow, add a Lookup transformation, and then configure the transformation by doing the following tasks:</span></span>  
  
    1.  <span data-ttu-id="6f0d1-157">원본이나 이전 변환에서 연결선을 조회 변환으로 끌어서 조회 변환을 데이터 흐름에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-157">Connect the Lookup transformation to the data flow by dragging a connector from a source or a previous transformation to the Lookup transformation.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="6f0d1-158">조회 변환이 빈 데이터 필드가 포함된 플랫 파일에 연결되면 이러한 조회 변환의 유효성을 검사하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-158">A Lookup transformation might not validate if that transformation connects to a flat file that contains an empty date field.</span></span> <span data-ttu-id="6f0d1-159">변환의 유효성 검사 여부는 플랫 파일의 연결 관리자가 Null 값을 유지하도록 구성되었는지 여부에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-159">Whether the transformation validates depends on whether the connection manager for the flat file has been configured to retain null values.</span></span> <span data-ttu-id="6f0d1-160">조회 변환의 유효성 검사가 수행되도록 하려면 **플랫 파일 원본 편집기**의 **연결 관리자 페이지**에서 **원본의 Null 값을 데이터 흐름의 Null 값으로 유지** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-160">To ensure that the Lookup transformation validates, in the **Flat File Source Editor**, on the **Connection Manager Page**, select the **Retain null values from the source as null values in the data flow** option.</span></span>  
  
    2.  <span data-ttu-id="6f0d1-161">원본이나 이전 변환을 두 번 클릭하여 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-161">Double-click the source or previous transformation to configure the component.</span></span>  
  
    3.  <span data-ttu-id="6f0d1-162">조회 변환을 두 번 클릭한 다음 **조회 변환 편집기**의 **일반** 페이지에서 **전체 캐시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-162">Double-click the Lookup transformation, and then in the **Lookup Transformation Editor**, on the **General** page, select **Full cache**.</span></span>  
  
    4.  <span data-ttu-id="6f0d1-163">**연결 형식** 영역에서 **캐시 연결 관리자**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-163">In the **Connection type** area, select **Cache connection manager**.</span></span>  
  
    5.  <span data-ttu-id="6f0d1-164">**일치하는 항목이 없는 행 처리 방법 지정** 목록에서 오류 처리 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-164">From the **Specify how to handle rows with no matching entries** list, select an error handling option.</span></span>  
  
    6.  <span data-ttu-id="6f0d1-165">**연결** 페이지의 **캐시 연결 관리자** 목록에서 캐시 연결 관리자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-165">On the **Connection** page, from the **Cache connection manager** list, select a Cache connection manager.</span></span>  
  
    7.  <span data-ttu-id="6f0d1-166">**열** 페이지를 클릭한 다음 **사용 가능한 입력 열** 목록에 있는 하나 이상의 열을 **사용 가능한 조회 열** 목록에 있는 열로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-166">Click the **Columns** page, and then drag at least one column from the **Available Input Columns** list to a column in the **Available Lookup Column** list.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="6f0d1-167">조회 변환은 이름과 데이터 형식이 같은 열을 자동으로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-167">The Lookup transformation automatically maps columns that have the same name and the same data type.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="6f0d1-168">열을 매핑하려면 데이터 형식이 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-168">Columns must have matching data types to be mapped.</span></span> <span data-ttu-id="6f0d1-169">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-169">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
    8.  <span data-ttu-id="6f0d1-170">**사용 가능한 조회 열** 목록에서 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-170">In the **Available Lookup Columns** list, select columns.</span></span> <span data-ttu-id="6f0d1-171">그런 다음 **조회 작업** 목록에서 조회 열의 값으로 입력 열의 값을 교체하거나 새 열에 기록할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-171">Then in the **Lookup Operation** list, specify whether the values from the lookup columns replace values in the input column or are written to a new column.</span></span>  
  
    9. <span data-ttu-id="6f0d1-172">오류 출력을 구성하려면 **오류 출력** 페이지를 클릭하고 오류 처리 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-172">To configure the error output, click the **Error Output** page and set the error handling options.</span></span> <span data-ttu-id="6f0d1-173">자세한 내용은 [조회 변환 편집기&#40;오류 출력 페이지&#41;](../lookup-transformation-editor-error-output-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-173">For more information, see [Lookup Transformation Editor &#40;Error Output Page&#41;](../lookup-transformation-editor-error-output-page.md).</span></span>  
  
    10. <span data-ttu-id="6f0d1-174">변경 내용을 조회 변환에 저장하려면 **확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-174">Click **OK** to save your changes to the Lookup transformation.</span></span>  
  
9. <span data-ttu-id="6f0d1-175">패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-175">Run the package.</span></span>  
  
### <a name="to-implement-a-lookup-transformation-in-full-cache-mode-in-two-packages-by-using-cache-connection-manager-and-a-data-source-in-the-data-flow"></a><span data-ttu-id="6f0d1-176">데이터 흐름의 데이터 원본과 캐시 연결 관리자를 사용하여 조회 변환을 두 개의 패키지에서 전체 캐시 모드로 구현하려면</span><span class="sxs-lookup"><span data-stu-id="6f0d1-176">To implement a Lookup transformation in full cache mode in two packages by using Cache connection manager and a data source in the data flow</span></span>  
  
1.  <span data-ttu-id="6f0d1-177">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 연 다음 두 개의 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-177">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open a [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project, and then open two packages.</span></span>  
  
2.  <span data-ttu-id="6f0d1-178">각 페이지의 제어 흐름 탭에서 데이터 흐름 태스크를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-178">On the Control Flow tab in each package, add a Data Flow task.</span></span>  
  
3.  <span data-ttu-id="6f0d1-179">부모 패키지에서 데이터 흐름에 캐시 변환을 추가한 다음 변환을 데이터 원본에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-179">In the parent package, add a Cache Transform transformation to the data flow, and then connect the transformation to a data source.</span></span>  
  
     <span data-ttu-id="6f0d1-180">필요한 경우 데이터 원본을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-180">Configure the data source as needed.</span></span>  
  
4.  <span data-ttu-id="6f0d1-181">캐시 변환을 두 번 클릭한 다음 **캐시 변환 편집기**의 **연결 관리자** 페이지에서 **새로 만들기** 를 클릭하여 새 캐시 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-181">Double-click the Cache Transform, and then in the **Cache Transformation Editor**, on the **Connection Manager** page, click **New** to create a new Cache connection manager.</span></span>  
  
5.  <span data-ttu-id="6f0d1-182">**캐시 연결 관리자 편집기**의 **일반** 탭에서 다음 옵션을 설정하여 캐시를 저장하도록 캐시 연결 관리자를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-182">In the **Cache Connection Manager Editor**, on the **General** tab, configure the Cache connection manager by setting the following options:</span></span>  
  
    -   <span data-ttu-id="6f0d1-183">**파일 캐시 사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-183">Select **Use file cache**.</span></span>  
  
    -   <span data-ttu-id="6f0d1-184">**파일 이름**에 파일 경로를 입력하거나 **찾아보기** 를 클릭하여 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-184">For **File name**, either type the file path or click **Browse** to select the file.</span></span>  
  
         <span data-ttu-id="6f0d1-185">존재하지 않는 파일의 경로를 입력하면 패키지를 실행할 때 시스템이 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-185">If you type a path for a file that does not exist, the system creates the file when you run the package.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6f0d1-186">패키지의 보호 수준은 캐시 파일에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-186">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="6f0d1-187">캐시 파일에 중요한 정보가 들어 있는 경우 ACL(액세스 제어 목록)을 사용하여 파일 저장 위치 또는 폴더에 대한 액세스를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-187">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="6f0d1-188">특정 계정에 대해서만 액세스를 허용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-188">You should enable access only to certain accounts.</span></span> <span data-ttu-id="6f0d1-189">자세한 내용은 [패키지에서 사용되는 파일 액세스](../access-to-files-used-by-packages.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-189">For more information, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
6.  <span data-ttu-id="6f0d1-190">**열** 탭을 클릭한 다음 **인덱스 위치** 옵션을 사용하여 인덱스 열이 되는 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-190">Click the **Columns** tab, and then specify which columns are the index columns by using the **Index Position** option.</span></span>  
  
     <span data-ttu-id="6f0d1-191">비인덱스 열의 경우 인덱스 위치는 0입니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-191">For non-index columns, the index position is 0.</span></span> <span data-ttu-id="6f0d1-192">인덱스 열의 경우 인덱스 위치는 일련의 양수입니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-192">For index columns, the index position is a sequential, positive number.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6f0d1-193">조회 변환은 캐시 연결 관리자를 사용하도록 구성된 경우 참조 데이터 세트의 인덱스 열만 입력 열에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-193">When the Lookup transformation is configured to use a Cache connection manager, only index columns in the reference dataset can be mapped to input columns.</span></span> <span data-ttu-id="6f0d1-194">또한 모든 인덱스 열을 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-194">Also, all index columns must be mapped.</span></span> <span data-ttu-id="6f0d1-195">자세한 내용은 [Cache Connection Manager Editor](../cache-connection-manager-editor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-195">For more information, see [Cache Connection Manager Editor](../cache-connection-manager-editor.md).</span></span>  
  
7.  <span data-ttu-id="6f0d1-196">필요한 경우 캐시 변환을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-196">Configure the Cache Transform as needed.</span></span> <span data-ttu-id="6f0d1-197">자세한 내용은 [캐시 변환 편집기&#40;연결 관리자 페이지&#41;](../cache-transformation-editor-connection-manager-page.md) 및 [캐시 변환 편집기&#40;매핑 페이지&#41;](../cache-transformation-editor-mappings-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-197">For more information, see [Cache Transformation Editor &#40;Connection Manager Page&#41;](../cache-transformation-editor-connection-manager-page.md) and [Cache Transformation Editor &#40;Mappings Page&#41;](../cache-transformation-editor-mappings-page.md).</span></span>  
  
8.  <span data-ttu-id="6f0d1-198">다음 중 하나를 수행하여 두 번째 패키지에 사용된 캐시 연결 관리자를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-198">Do one of the following to populate the Cache connection manager that is used in the second package:</span></span>  
  
    -   <span data-ttu-id="6f0d1-199">부모 패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-199">Run the parent package.</span></span>  
  
    -   <span data-ttu-id="6f0d1-200">4단계에서 만든 캐시 연결 관리자를 두 번 클릭하고 **열**을 클릭하여 행을 선택한 다음 CTRL+C를 눌러 열 메타데이터를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-200">Double-click the Cache connection manager you created in step 4, click **Columns**, select the rows, and then press CTRL+C to copy the column metadata.</span></span>  
  
9. <span data-ttu-id="6f0d1-201">자식 패키지에서 **연결 관리자** 영역을 마우스 오른쪽 단추로 누르고 **새 연결**을 클릭하여 **SSIS 연결 관리자 추가** 대화 상자에서 **CACHE** 를 선택한 다음 **추가**를 클릭하여 캐시 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-201">In the child package, create a Cache connection manager by right-clicking in the **Connection Managers** area, clicking **New Connection**, selecting **CACHE** in the **Add SSIS Connection Manager** dialog box, and then clicking **Add**.</span></span>  
  
     <span data-ttu-id="6f0d1-202">**연결 관리자** 영역은 **디자이너의**흐름 제어 **,** 데이터 흐름 **및** 이벤트 처리기 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 탭 아래에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-202">The **Connection Managers** area appears on the bottom of the **Control Flow**, **Data Flow**, and **Event Handlers** tabs of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Designer.</span></span>  
  
10. <span data-ttu-id="6f0d1-203">**캐시 연결 관리자 편집기**의 **일반** 탭에서 다음 옵션을 설정하여 캐시 파일의 데이터를 읽도록 캐시 연결 관리자를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-203">In the **Cache Connection Manager Editor**, on the **General** tab, configure the Cache connection manager to read the data from the cache file that you selected by setting the following options:</span></span>  
  
    -   <span data-ttu-id="6f0d1-204">**파일 캐시 사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-204">Select **Use file cache**.</span></span>  
  
    -   <span data-ttu-id="6f0d1-205">**파일 이름**에 파일 경로를 입력하거나 **찾아보기** 를 클릭하여 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-205">For **File name**, either type the file path or click **Browse** to select the file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6f0d1-206">패키지의 보호 수준은 캐시 파일에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-206">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="6f0d1-207">캐시 파일에 중요한 정보가 들어 있는 경우 ACL(액세스 제어 목록)을 사용하여 파일 저장 위치 또는 폴더에 대한 액세스를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-207">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="6f0d1-208">특정 계정에 대해서만 액세스를 허용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-208">You should enable access only to certain accounts.</span></span> <span data-ttu-id="6f0d1-209">자세한 내용은 [패키지에서 사용되는 파일 액세스](../access-to-files-used-by-packages.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-209">For more information, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
11. <span data-ttu-id="6f0d1-210">8단계에서 열 메타데이터를 복사했으면 **열**을 클릭하고 빈 행을 선택한 다음 Ctrl+V를 눌러 열 메타데이터를 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-210">If you copied the column metadata in step 8, click **Columns**, select the empty row, and then press CTRL+V to paste the column metadata.</span></span>  
  
12. <span data-ttu-id="6f0d1-211">조회 변환을 추가한 후 다음을 수행하여 변환을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-211">Add a Lookup transformation, and then configure the transformation by doing the following:</span></span>  
  
    1.  <span data-ttu-id="6f0d1-212">원본이나 이전 변환에서 연결선을 조회 변환으로 끌어서 조회 변환을 데이터 흐름에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-212">Connect the Lookup transformation to the data flow by dragging a connector from a source or a previous transformation to the Lookup transformation.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="6f0d1-213">조회 변환이 빈 데이터 필드가 포함된 플랫 파일에 연결되면 이러한 조회 변환의 유효성을 검사하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-213">A Lookup transformation might not validate if that transformation connects to a flat file that contains an empty date field.</span></span> <span data-ttu-id="6f0d1-214">변환의 유효성 검사 여부는 플랫 파일의 연결 관리자가 Null 값을 유지하도록 구성되었는지 여부에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-214">Whether the transformation validates depends on whether the connection manager for the flat file has been configured to retain null values.</span></span> <span data-ttu-id="6f0d1-215">조회 변환의 유효성 검사가 수행되도록 하려면 **플랫 파일 원본 편집기**의 **연결 관리자 페이지**에서 **원본의 Null 값을 데이터 흐름의 Null 값으로 유지** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-215">To ensure that the Lookup transformation validates, in the **Flat File Source Editor**, on the **Connection Manager Page**, select the **Retain null values from the source as null values in the data flow** option.</span></span>  
  
    2.  <span data-ttu-id="6f0d1-216">원본이나 이전 변환을 두 번 클릭하여 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-216">Double-click the source or previous transformation to configure the component.</span></span>  
  
    3.  <span data-ttu-id="6f0d1-217">조회 변환을 두 번 클릭한 다음 **조회 변환 편집기** 의 **일반** 페이지에서 **전체 캐시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-217">Double-click the Lookup transformation, and then select **Full cache** on the **General** page of the **Lookup Transformation Editor**.</span></span>  
  
    4.  <span data-ttu-id="6f0d1-218">**연결 형식** 영역에서 **캐시 연결 관리자** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-218">Select **Cache connection manager** in the **Connection type** area.</span></span>  
  
    5.  <span data-ttu-id="6f0d1-219">**일치하는 항목이 없는 행 처리 방법 지정** 목록에서 일치하는 항목이 없는 행에 대한 오류 처리 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-219">Select an error handling option for rows without matching entries from the **Specify how to handle rows with no matching entries** list.</span></span>  
  
    6.  <span data-ttu-id="6f0d1-220">**연결** 페이지의 **캐시 연결 관리자** 목록에서 추가한 캐시 연결 관리자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-220">On the **Connection** page, from the **Cache connection manager** list, select the Cache connection manager that you added.</span></span>  
  
    7.  <span data-ttu-id="6f0d1-221">**열** 페이지를 클릭한 다음 **사용 가능한 입력 열** 목록에 있는 하나 이상의 열을 **사용 가능한 조회 열** 목록에 있는 열로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-221">Click the **Columns** page, and then drag at least one column from the **Available Input Columns** list to a column in the **Available Lookup Column** list.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="6f0d1-222">조회 변환은 이름과 데이터 형식이 같은 열을 자동으로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-222">The Lookup transformation automatically maps columns that have the same name and the same data type.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="6f0d1-223">열을 매핑하려면 데이터 형식이 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-223">Columns must have matching data types to be mapped.</span></span> <span data-ttu-id="6f0d1-224">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-224">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
    8.  <span data-ttu-id="6f0d1-225">**사용 가능한 조회 열** 목록에서 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-225">In the **Available Lookup Columns** list, select columns.</span></span> <span data-ttu-id="6f0d1-226">그런 다음 **조회 작업** 목록에서 조회 열의 값으로 입력 열의 값을 교체하거나 새 열에 기록할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-226">Then in the **Lookup Operation** list, specify whether the values from the lookup columns replace values in the input column or are written to a new column.</span></span>  
  
    9. <span data-ttu-id="6f0d1-227">오류 출력을 구성하려면 **오류 출력** 페이지를 클릭하고 오류 처리 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-227">To configure the error output, click the **Error Output** page and set the error handling options.</span></span> <span data-ttu-id="6f0d1-228">자세한 내용은 [조회 변환 편집기&#40;오류 출력 페이지&#41;](../lookup-transformation-editor-error-output-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-228">For more information, see [Lookup Transformation Editor &#40;Error Output Page&#41;](../lookup-transformation-editor-error-output-page.md).</span></span>  
  
    10. <span data-ttu-id="6f0d1-229">변경 내용을 조회 변환에 저장하려면 **확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-229">Click **OK** to save your changes to the Lookup transformation.</span></span>  
  
13. <span data-ttu-id="6f0d1-230">부모 패키지를 열고 제어 흐름에 패키지 실행 태스크를 추가한 다음 자식 패키지를 호출할 태스크를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-230">Open the parent package, add an Execute Package task to the control flow, and then configure the task to call the child package.</span></span> <span data-ttu-id="6f0d1-231">자세한 내용은 [Execute Package Task](../control-flow/execute-package-task.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-231">For more information, see [Execute Package Task](../control-flow/execute-package-task.md).</span></span>  
  
14. <span data-ttu-id="6f0d1-232">패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-232">Run the packages.</span></span>  
  
### <a name="to-implement-a-lookup-transformation-in-full-cache-mode-by-using-cache-connection-manager-and-an-existing-cache-file"></a><span data-ttu-id="6f0d1-233">캐시 연결 관리자와 기존 캐시 파일을 사용하여 전체 캐시 모드에서 조회 변환을 구현하려면</span><span class="sxs-lookup"><span data-stu-id="6f0d1-233">To implement a Lookup transformation in full cache mode by using Cache connection manager and an existing cache file</span></span>  
  
1.  <span data-ttu-id="6f0d1-234">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 연 다음 하나의 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-234">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open a [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project, and then open a package.</span></span>  
  
2.  <span data-ttu-id="6f0d1-235">**연결 관리자** 영역을 마우스 오른쪽 단추로 클릭한 다음 **새 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-235">Right-click in the **Connection Managers** area, and then click **New Connection**.</span></span>  
  
     <span data-ttu-id="6f0d1-236">**연결 관리자** 영역은 **디자이너의**흐름 제어 **,** 데이터 흐름 **및** 이벤트 처리기 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 탭 아래에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-236">The **Connection Managers** area appears on the bottom of the **Control Flow**, **Data Flow**, and **Event Handlers** tabs of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Designer.</span></span>  
  
3.  <span data-ttu-id="6f0d1-237">**SSIS 연결 관리자 추가** 대화 상자에서 **CACHE**를 선택한 다음 **추가** 를 클릭하여 캐시 연결 관리자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-237">In the **Add SSIS Connection Manager** dialog box, select **CACHE**, and then click **Add** to add a Cache connection manager.</span></span>  
  
4.  <span data-ttu-id="6f0d1-238">캐시 연결 관리자를 두 번 클릭하여 **캐시 연결 관리자 편집기**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-238">Double-click the Cache connection manager to open the **Cache Connection Manager Editor**.</span></span>  
  
5.  <span data-ttu-id="6f0d1-239">**캐시 연결 관리자 편집기**의 **일반** 탭에서 다음 옵션을 설정하여 캐시를 저장하도록 캐시 연결 관리자를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-239">In the **Cache Connection Manager Editor**, on the **General** tab, configure the Cache connection manager by setting the following options:</span></span>  
  
    -   <span data-ttu-id="6f0d1-240">**파일 캐시 사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-240">Select **Use file cache**.</span></span>  
  
    -   <span data-ttu-id="6f0d1-241">**파일 이름**에 파일 경로를 입력하거나 **찾아보기** 를 클릭하여 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-241">For **File name**, either type the file path or click **Browse** to select the file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6f0d1-242">패키지의 보호 수준은 캐시 파일에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-242">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="6f0d1-243">캐시 파일에 중요한 정보가 들어 있는 경우 ACL(액세스 제어 목록)을 사용하여 파일 저장 위치 또는 폴더에 대한 액세스를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-243">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="6f0d1-244">특정 계정에 대해서만 액세스를 허용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-244">You should enable access only to certain accounts.</span></span> <span data-ttu-id="6f0d1-245">자세한 내용은 [패키지에서 사용되는 파일 액세스](../access-to-files-used-by-packages.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-245">For more information, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
6.  <span data-ttu-id="6f0d1-246">**열** 탭을 클릭한 다음 **인덱스 위치** 옵션을 사용하여 인덱스 열이 되는 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-246">Click the **Columns** tab, and then specify which columns are the index columns by using the **Index Position** option.</span></span>  
  
     <span data-ttu-id="6f0d1-247">비인덱스 열의 경우 인덱스 위치는 0입니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-247">For non-index columns, the index position is 0.</span></span> <span data-ttu-id="6f0d1-248">인덱스 열의 경우 인덱스 위치는 일련의 양수입니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-248">For index columns, the index position is a sequential, positive number.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6f0d1-249">조회 변환은 캐시 연결 관리자를 사용하도록 구성된 경우 참조 데이터 세트의 인덱스 열만 입력 열에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-249">When the Lookup transformation is configured to use a Cache connection manager, only index columns in the reference dataset can be mapped to input columns.</span></span> <span data-ttu-id="6f0d1-250">또한 모든 인덱스 열을 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-250">Also, all index columns must be mapped.</span></span> <span data-ttu-id="6f0d1-251">자세한 내용은 [Cache Connection Manager Editor](../cache-connection-manager-editor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-251">For more information, see [Cache Connection Manager Editor](../cache-connection-manager-editor.md).</span></span>  
  
7.  <span data-ttu-id="6f0d1-252">**흐름 제어** 탭에서 패키지에 데이터 흐름 태스크를 추가한 다음 데이터 흐름에 조회 변환을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-252">On the **Control Flow** tab, add a Data Flow task to the package, and then add a Lookup transformation to the data flow.</span></span>  
  
8.  <span data-ttu-id="6f0d1-253">다음을 수행하여 조회 변환을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-253">Configure the Lookup transformation by doing the following:</span></span>  
  
    1.  <span data-ttu-id="6f0d1-254">원본이나 이전 변환에서 연결선을 조회 변환으로 끌어서 조회 변환을 데이터 흐름에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-254">Connect the Lookup transformation to the data flow by dragging a connector from a source or a previous transformation to the Lookup transformation.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="6f0d1-255">조회 변환이 빈 데이터 필드가 포함된 플랫 파일에 연결되면 이러한 조회 변환의 유효성을 검사하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-255">A Lookup transformation might not validate if that transformation connects to a flat file that contains an empty date field.</span></span> <span data-ttu-id="6f0d1-256">변환의 유효성 검사 여부는 플랫 파일의 연결 관리자가 Null 값을 유지하도록 구성되었는지 여부에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-256">Whether the transformation validates depends on whether the connection manager for the flat file has been configured to retain null values.</span></span> <span data-ttu-id="6f0d1-257">조회 변환의 유효성 검사가 수행되도록 하려면 **플랫 파일 원본 편집기**의 **연결 관리자 페이지**에서 **원본의 Null 값을 데이터 흐름의 Null 값으로 유지** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-257">To ensure that the Lookup transformation validates, in the **Flat File Source Editor**, on the **Connection Manager Page**, select the **Retain null values from the source as null values in the data flow** option.</span></span>  
  
    2.  <span data-ttu-id="6f0d1-258">원본이나 이전 변환을 두 번 클릭하여 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-258">Double-click the source or previous transformation to configure the component.</span></span>  
  
    3.  <span data-ttu-id="6f0d1-259">조회 변환을 두 번 클릭한 다음 **조회 변환 편집기**의 **일반** 페이지에서 **전체 캐시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-259">Double-click the Lookup transformation, and then in the **Lookup Transformation Editor**, on the **General** page, select **Full cache**.</span></span>  
  
    4.  <span data-ttu-id="6f0d1-260">**연결 형식** 영역에서 **캐시 연결 관리자** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-260">Select **Cache connection manager** in the **Connection type** area.</span></span>  
  
    5.  <span data-ttu-id="6f0d1-261">**일치하는 항목이 없는 행 처리 방법 지정** 목록에서 일치하는 항목이 없는 행에 대한 오류 처리 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-261">Select an error handling option for rows without matching entries from the **Specify how to handle rows with no matching entries** list.</span></span>  
  
    6.  <span data-ttu-id="6f0d1-262">**연결** 페이지의 **캐시 연결 관리자** 목록에서 추가한 캐시 연결 관리자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-262">On the **Connection** page, from the **Cache connection manager** list, select the Cache connection manager that you added.</span></span>  
  
    7.  <span data-ttu-id="6f0d1-263">**열** 페이지를 클릭한 다음 **사용 가능한 입력 열** 목록에 있는 하나 이상의 열을 **사용 가능한 조회 열** 목록에 있는 열로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-263">Click the **Columns** page, and then drag at least one column from the **Available Input Columns** list to a column in the **Available Lookup Column** list.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="6f0d1-264">조회 변환은 이름과 데이터 형식이 같은 열을 자동으로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-264">The Lookup transformation automatically maps columns that have the same name and the same data type.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="6f0d1-265">열을 매핑하려면 데이터 형식이 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-265">Columns must have matching data types to be mapped.</span></span> <span data-ttu-id="6f0d1-266">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-266">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
    8.  <span data-ttu-id="6f0d1-267">**사용 가능한 조회 열** 목록에서 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-267">In the **Available Lookup Columns** list, select columns.</span></span> <span data-ttu-id="6f0d1-268">그런 다음 **조회 작업** 목록에서 조회 열의 값으로 입력 열의 값을 교체하거나 새 열에 기록할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-268">Then in the **Lookup Operation** list, specify whether the values from the lookup columns replace values in the input column or are written to a new column.</span></span>  
  
    9. <span data-ttu-id="6f0d1-269">오류 출력을 구성하려면 **오류 출력** 페이지를 클릭하고 오류 처리 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-269">To configure the error output, click the **Error Output** page and set the error handling options.</span></span> <span data-ttu-id="6f0d1-270">자세한 내용은 [조회 변환 편집기&#40;오류 출력 페이지&#41;](../lookup-transformation-editor-error-output-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-270">For more information, see [Lookup Transformation Editor &#40;Error Output Page&#41;](../lookup-transformation-editor-error-output-page.md).</span></span>  
  
    10. <span data-ttu-id="6f0d1-271">변경 내용을 조회 변환에 저장하려면 **확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-271">Click **OK** to save your changes to the Lookup transformation.</span></span>  
  
9. <span data-ttu-id="6f0d1-272">패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0d1-272">Run the package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f0d1-273">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6f0d1-273">See Also</span></span>  
 <span data-ttu-id="6f0d1-274">[OLE DB 연결 관리자를 사용하여 전체 캐시 모드에서 조회 변환 구현](lookup-transformation-full-cache-mode-ole-db-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="6f0d1-274">[Implement a Lookup Transformation in Full Cache Mode Using the OLE DB Connection Manager](lookup-transformation-full-cache-mode-ole-db-connection-manager.md) </span></span>  
 <span data-ttu-id="6f0d1-275">[캐시 없음 또는 부분 캐시 모드로 조회 구현](../data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md) </span><span class="sxs-lookup"><span data-stu-id="6f0d1-275">[Implement a Lookup in No Cache or Partial Cache Mode](../data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md) </span></span>  
 [<span data-ttu-id="6f0d1-276">Integration Services 변환</span><span class="sxs-lookup"><span data-stu-id="6f0d1-276">Integration Services Transformations</span></span>](../data-flow/transformations/integration-services-transformations.md)  
  
  
