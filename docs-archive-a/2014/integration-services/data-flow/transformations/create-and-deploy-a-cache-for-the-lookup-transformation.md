---
title: 조회 변환에 대한 캐시 만들기 및 배포 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- creating cache files for Lookup transformation
- deploying cache files for Lookup transformation
- Lookup transformation cache files
ms.assetid: cedf5cad-2fac-42d0-ad91-9461e117d330
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b33b00b84f1f1448c2ee80882aedc3a330ba0a5a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638910"
---
# <a name="create-and-deploy-a-cache-for-the-lookup-transformation"></a><span data-ttu-id="e9570-102">조회 변환에 대한 캐시 만들기 및 배포</span><span class="sxs-lookup"><span data-stu-id="e9570-102">Create and Deploy a Cache for the Lookup Transformation</span></span>
  <span data-ttu-id="e9570-103">조회 변환에 대한 캐시 파일(.caw)을 만들고 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-103">You can create and deploy a cache file (.caw) for the Lookup transformation.</span></span> <span data-ttu-id="e9570-104">참조 데이터 세트는 캐시 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-104">The reference dataset is stored in the cache file.</span></span>  
  
 <span data-ttu-id="e9570-105">조회 변환은 연결된 데이터 원본의 입력 열에 있는 데이터를 참조 데이터 세트의 열과 조인하여 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-105">The Lookup transformation performs lookups by joining data in input columns from a connected data source with columns in the reference dataset.</span></span>  
  
 <span data-ttu-id="e9570-106">캐시 연결 관리자와 캐시 변환을 사용하여 캐시 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-106">You create a cache file by using a Cache connection manager and a Cache Transform transformation.</span></span> <span data-ttu-id="e9570-107">자세한 내용은 [Cache Connection Manager](../../connection-manager/cache-connection-manager.md) 및 [Cache Transform](cache-transform.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e9570-107">For more information, see [Cache Connection Manager](../../connection-manager/cache-connection-manager.md) and [Cache Transform](cache-transform.md).</span></span>  
  
 <span data-ttu-id="e9570-108">조회 변환 및 캐시 파일에 대한 자세한 내용은 [Lookup Transformation](lookup-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e9570-108">To learn more about the Lookup transformation and cache files, see [Lookup Transformation](lookup-transformation.md).</span></span>  
  
### <a name="to-create-a-cache-file"></a><span data-ttu-id="e9570-109">캐시 파일을 만들려면</span><span class="sxs-lookup"><span data-stu-id="e9570-109">To create a cache file</span></span>  
  
1.  <span data-ttu-id="e9570-110">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 프로젝트를 열고 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-110">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want, and then open the package.</span></span>  
  
2.  <span data-ttu-id="e9570-111">**제어 흐름** 탭에서 데이터 흐름 태스크를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-111">On the **Control Flow** tab, add a Data Flow task.</span></span>  
  
3.  <span data-ttu-id="e9570-112">**데이터 흐름** 탭에서 데이터 흐름에 캐시 변환을 추가한 다음 변환을 데이터 원본에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-112">On the **Data Flow** tab, add a Cache Transform transformation to the data flow, and then connect the transformation to a data source.</span></span>  
  
     <span data-ttu-id="e9570-113">필요한 경우 데이터 원본을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-113">Configure the data source as needed.</span></span>  
  
4.  <span data-ttu-id="e9570-114">캐시 변환을 두 번 클릭한 다음 **캐시 변환 편집기**의 **연결 관리자** 페이지에서 **새로 만들기** 를 클릭하여 새 캐시 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-114">Double-click the Cache Transform, and then in the **Cache Transformation Editor**, on the **Connection Manager** page, click **New** to create a new Cache connection manager.</span></span>  
  
5.  <span data-ttu-id="e9570-115">**캐시 연결 관리자 편집기**의 **일반** 탭에서 다음 옵션을 선택하여 캐시를 저장하도록 캐시 연결 관리자를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-115">In the **Cache Connection Manager Editor**, on the **General** tab, configure the Cache connection manager to save the cache by selecting the following options:</span></span>  
  
    1.  <span data-ttu-id="e9570-116">**파일 캐시 사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-116">Select **Use file cache**.</span></span>  
  
    2.  <span data-ttu-id="e9570-117">**파일 이름**에 파일 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-117">For **File name**, type the file path.</span></span>  
  
     <span data-ttu-id="e9570-118">패키지를 실행할 때 시스템이 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-118">The system creates the file when you run the package.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e9570-119">패키지의 보호 수준은 캐시 파일에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-119">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="e9570-120">캐시 파일에 중요한 정보가 들어 있는 경우 ACL(액세스 제어 목록)을 사용하여 파일 저장 위치 또는 폴더에 대한 액세스를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-120">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="e9570-121">특정 계정에 대해서만 액세스를 허용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-121">You should enable access only to certain accounts.</span></span> <span data-ttu-id="e9570-122">자세한 내용은 [패키지에서 사용되는 파일 액세스](../../access-to-files-used-by-packages.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e9570-122">For more information, see [Access to Files Used by Packages](../../access-to-files-used-by-packages.md).</span></span>  
  
6.  <span data-ttu-id="e9570-123">**열** 탭을 클릭한 다음 **인덱스 위치** 옵션을 사용하여 인덱스 열이 되는 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-123">Click the **Columns** tab, and then specify which columns are the index columns by using the **Index Position** option.</span></span>  
  
     <span data-ttu-id="e9570-124">비인덱스 열의 경우 인덱스 위치는 0입니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-124">For non-index columns, the index position is 0.</span></span> <span data-ttu-id="e9570-125">인덱스 열의 경우 인덱스 위치는 일련의 양수입니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-125">For index columns, the index position is a sequential, positive number.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e9570-126">조회 변환은 캐시 연결 관리자를 사용하도록 구성된 경우 참조 데이터 세트의 인덱스 열만 입력 열에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-126">When the Lookup transformation is configured to use a Cache connection manager, only index columns in the reference dataset can be mapped to input columns.</span></span> <span data-ttu-id="e9570-127">또한 모든 인덱스 열을 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-127">Also all index columns must be mapped.</span></span>  
  
     <span data-ttu-id="e9570-128">자세한 내용은 [Cache Connection Manager Editor](../../cache-connection-manager-editor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e9570-128">For more information, see [Cache Connection Manager Editor](../../cache-connection-manager-editor.md).</span></span>  
  
7.  <span data-ttu-id="e9570-129">필요한 경우 캐시 변환을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-129">Configure the Cache Transform as needed.</span></span>  
  
     <span data-ttu-id="e9570-130">자세한 내용은 [캐시 변환 편집기&#40;연결 관리자 페이지&#41;](../../cache-transformation-editor-connection-manager-page.md) 및 [캐시 변환 편집기&#40;매핑 페이지&#41;](../../cache-transformation-editor-mappings-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e9570-130">For more information, see [Cache Transformation Editor &#40;Connection Manager Page&#41;](../../cache-transformation-editor-connection-manager-page.md) and [Cache Transformation Editor &#40;Mappings Page&#41;](../../cache-transformation-editor-mappings-page.md).</span></span>  
  
8.  <span data-ttu-id="e9570-131">패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-131">Run the package.</span></span>  
  
### <a name="to-deploy-a-cache-file"></a><span data-ttu-id="e9570-132">캐시 파일을 배포하려면</span><span class="sxs-lookup"><span data-stu-id="e9570-132">To deploy a cache file</span></span>  
  
1.  <span data-ttu-id="e9570-133">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 프로젝트를 열고 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-133">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want, and then open the package.</span></span>  
  
2.  <span data-ttu-id="e9570-134">필요에 따라 패키지 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-134">Optionally, create a package configuration.</span></span> <span data-ttu-id="e9570-135">자세한 내용은 [패키지 구성 만들기](../../create-package-configurations.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e9570-135">For more information, see [Create Package Configurations](../../create-package-configurations.md).</span></span>  
  
3.  <span data-ttu-id="e9570-136">다음을 수행하여 프로젝트에 캐시 파일을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-136">Add the cache file to the project by doing the following:</span></span>  
  
    1.  <span data-ttu-id="e9570-137">1단계에서 연 프로젝트를 솔루션 탐색기에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-137">In Solution Explorer, select the project you opened in step 1.</span></span>  
  
    2.  <span data-ttu-id="e9570-138">**프로젝트** 메뉴에서 **기존 항목 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-138">On the **Project** menu, click **AddExisting Item**.</span></span>  
  
    3.  <span data-ttu-id="e9570-139">캐시 파일을 선택한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-139">Select the cache file, and then click **Add**.</span></span>  
  
     <span data-ttu-id="e9570-140">솔루션 탐색기의 **기타** 폴더에 파일이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-140">The file appears in the **Miscellaneous** folder in Solution Explorer.</span></span>  
  
4.  <span data-ttu-id="e9570-141">배치 유틸리티를 만들도록 프로젝트를 구성한 다음 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-141">Configure the project to create a deployment utility, and then build the project.</span></span> <span data-ttu-id="e9570-142">자세한 내용은 [Create a Deployment Utility](../../create-a-deployment-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e9570-142">For more information, see [Create a Deployment Utility](../../create-a-deployment-utility.md).</span></span>  
  
     <span data-ttu-id="e9570-143">매니페스트 파일인 \<*project name*>.SSISDeploymentManifest.xml이 만들어집니다. 이 파일은 프로젝트, 패키지 및 패키지 구성에 기타 파일을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-143">A manifest file, \<*project name*>.SSISDeploymentManifest.xml, is created that lists the miscellaneous files in the project, the packages, and the package configurations.</span></span>  
  
5.  <span data-ttu-id="e9570-144">파일 시스템에 패키지를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="e9570-144">Deploy the package to the file system.</span></span> <span data-ttu-id="e9570-145">자세한 내용은 [Deploy Packages by Using the Deployment Utility](../../deploy-packages-by-using-the-deployment-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e9570-145">For more information, see [Deploy Packages by Using the Deployment Utility](../../deploy-packages-by-using-the-deployment-utility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9570-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e9570-146">See Also</span></span>  
 [<span data-ttu-id="e9570-147">배포 유틸리티 만들기</span><span class="sxs-lookup"><span data-stu-id="e9570-147">Create a Deployment Utility</span></span>](../../create-a-deployment-utility.md)  
  
  
