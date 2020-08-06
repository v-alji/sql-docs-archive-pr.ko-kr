---
title: 개체 메타 데이터에 대 한 정의 읽기 권한 부여 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- metadata [Analysis Services]
- permissions [Analysis Services], read metadata
- read metadata permissions
ms.assetid: c857e48e-64b0-4ffe-900d-a0a3ddafcefb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1e3b18b913ed4b678baf0969b006f1386ba748e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651933"
---
# <a name="grant-read-definition-permissions-on-object-metadata-analysis-services"></a><span data-ttu-id="d05ce-102">개체 메타데이터에 대한 정의 읽기 권한 부여(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="d05ce-102">Grant read definition permissions on object metadata (Analysis Services)</span></span>
  <span data-ttu-id="d05ce-103">선택한 개체에 대한 개체 정의 또는 메타데이터를 읽을 수 있는 권한을 통해 관리자는 개체 정의를 수정하거나 개체 구조를 수정하거나 개체에 대한 실제 데이터를 볼 수 있는 권한을 부여하지 않고도 개체 정보를 볼 수 있는 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d05ce-103">Permission to read an object definition, or metadata, on selected objects lets an administrator grant permission to view object information, without also granting permission to modify the object's definition, modify the object's structure, or view the actual data for the object.</span></span> <span data-ttu-id="d05ce-104">`Read Definition`사용 권한은 데이터베이스, 데이터 원본, 차원, 마이닝 구조 및 마이닝 모델 수준에서 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d05ce-104">`Read Definition` permissions can be granted at the database, data source, dimension, mining structure, and mining model levels.</span></span> <span data-ttu-id="d05ce-105">`Read Definition`큐브에 대 한 사용 권한이 필요한 경우 데이터베이스에 대해를 사용 하도록 설정 해야 합니다 `Read Definition` . 사용 권한은 누적 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d05ce-105">If you require `Read Definition` permissions for a cube, you must enable `Read Definition` for the database.Remember that permissions are additive.</span></span> <span data-ttu-id="d05ce-106">예를 들어 한 역할이 큐브에 대한 메타데이터를 읽을 수 있는 권한을 부여하고 두 번째 역할은 동일한 사용자에게 차원에 대한 메타데이터를 읽을 수 있는 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="d05ce-106">For example, one role grants permission to read the metadata for a cube, while a second role grants the same user permission to read the metadata for a dimension.</span></span> <span data-ttu-id="d05ce-107">이 경우 두 역할의 사용 권한이 결합하여 사용자는 큐브에 대한 메타데이터와 해당 데이터베이스 내의 차원에 대한 메타데이터를 읽을 수 있는 권한을 동시에 부여받습니다.</span><span class="sxs-lookup"><span data-stu-id="d05ce-107">The permissions from the two different roles combine to give the user permission to both read metadata for the cube and the metadata for the dimension within that database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d05ce-108">데이터베이스의 메타데이터를 읽을 수 있는 권한은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 또는 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 를 사용하여 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]데이터베이스에 연결하는 데 필요한 최소 사용 권한입니다.</span><span class="sxs-lookup"><span data-stu-id="d05ce-108">Permission to read a database's metadata is the minimum permission required to connect to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database using either [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] or [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="d05ce-109">메타데이터를 읽을 권한이 있는 사용자는 DISCOVER_XML_METADATA 스키마 행 집합을 사용하여 개체를 쿼리하고 해당 메타데이터를 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d05ce-109">A user who has permission to read metadata can also use the DISCOVER_XML_METADATA schema rowset to query the object and view its metadata.</span></span> <span data-ttu-id="d05ce-110">자세한 내용은 [DISCOVER_XML_METADATA 행 집합](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-xml-metadata-rowset)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d05ce-110">For more information, see [DISCOVER_XML_METADATA Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-xml-metadata-rowset).</span></span>  
  
## <a name="set-read-definition-permissions-on-a-database"></a><span data-ttu-id="d05ce-111">데이터베이스에 대한 정의 읽기 권한 설정</span><span class="sxs-lookup"><span data-stu-id="d05ce-111">Set read definition permissions on a database</span></span>  
 <span data-ttu-id="d05ce-112">데이터베이스 메타데이터를 읽을 수 있는 권한을 부여하면 데이터베이스 내 모든 개체의 메타데이터를 읽을 수 있는 권한도 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="d05ce-112">Granting permission to read database metadata also grants permission to read the metadata of all objects in the database.</span></span>  
  
 <span data-ttu-id="d05ce-113">`Read Definition`전용 처리를 위해 역할을 설정할 때마다 데이터베이스 수준에서 사용 권한을 포함 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d05ce-113">We suggest that you include the `Read Definition` permission at the database level whenever you are setting up roles for dedicated processing.</span></span> <span data-ttu-id="d05ce-114">를 `Read Definition` 사용 하면 비관리자는에서 모델의 개체 계층을 보고 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 후속 처리를 위해 개별 개체로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d05ce-114">Having `Read Definition` allows non-administrators to view a model's object hierarchy in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and navigate to individual objects for subsequent processing.</span></span>  
  
1.  <span data-ttu-id="d05ce-115">에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 인스턴스에 연결 하 고 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체 탐색기에서 해당 데이터베이스에 대 한 **역할** 을 확장 한 다음 데이터베이스 역할을 클릭 하거나 새 데이터베이스 역할을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d05ce-115">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], expand **Roles** for the appropriate database in Object Explorer, and then click a database role (or create a new database role).</span></span>  
  
2.  <span data-ttu-id="d05ce-116">**일반** 탭에서 옵션을 선택 `Read Definition` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d05ce-116">On the **General** tab, select the `Read Definition` option.</span></span>  
  
3.  <span data-ttu-id="d05ce-117">**멤버 자격** 창에서 이 역할을 사용하여 Analysis Services에 연결하는 Windows 사용자 및 그룹 계정을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d05ce-117">In the **Membership** pane, enter the Windows user and group accounts that connect to Analysis Services using this role.</span></span>  
  
4.  <span data-ttu-id="d05ce-118">**확인** 을 클릭하여 역할 만들기를 마칩니다.</span><span class="sxs-lookup"><span data-stu-id="d05ce-118">Click **OK** to finish creating the role.</span></span>  
  
## <a name="set-read-definition-permissions-on-individual-objects"></a><span data-ttu-id="d05ce-119">개별 개체에 대한 정의 읽기 권한 설정</span><span class="sxs-lookup"><span data-stu-id="d05ce-119">Set read definition permissions on individual objects</span></span>  
  
1.  <span data-ttu-id="d05ce-120">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]인스턴스에 연결하고 **데이터베이스** 폴더를 열고 데이터베이스를 선택하고 개체 탐색기에서 해당 데이터베이스에 대한 **역할** 을 확장한 다음 데이터베이스 역할을 클릭하거나 새 데이터베이스 역할을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d05ce-120">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], open the **Databases** folder, select a database, expand **Roles** for the appropriate database in Object Explorer, and then click a database role (or create a new database role).</span></span>  
  
2.  <span data-ttu-id="d05ce-121">**일반** 창에서에 대 한 데이터베이스 권한을 선택 취소 합니다 `Read Definition` .</span><span class="sxs-lookup"><span data-stu-id="d05ce-121">In the **General** pane, clear the database permission for `Read Definition`.</span></span> <span data-ttu-id="d05ce-122">이 단계는 사용 권한 상속을 제거하므로, 개별 개체에 대한 사용 권한을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d05ce-122">This step removes permission inheritance so that you can set permissions on individual objects.</span></span>  
  
3.  <span data-ttu-id="d05ce-123">속성을 지정 하는 개체를 선택 합니다 `Read Definition` .</span><span class="sxs-lookup"><span data-stu-id="d05ce-123">Select the object for which you are specifying `Read Definition` properties:</span></span>  
  
    -   <span data-ttu-id="d05ce-124">**데이터 원본** 창에서 `Read Definition` 해당 데이터 원본에 대 한 확인란을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d05ce-124">In the **Data Sources** pane, click the `Read Definition` check box for that data source.</span></span> <span data-ttu-id="d05ce-125">역할 구성원은 서버 이름 및 사용자 이름(가능한 경우)을 비롯하여 데이터 원본에 대한 연결 문자열을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d05ce-125">Role members can view the connection string to the data source, including the server name and possibly the user name.</span></span> <span data-ttu-id="d05ce-126">연결 문자열 정보를 제공하려는 경우 연결 문자열을 수정하거나 임의의 기타 개체 정의를 볼 수 있는 권한을 부여하지 않고 이 사용 권한을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d05ce-126">This permission is available in case you want to provide connection string information, without also granting permission to modify the connection string or view the definitions of any other objects.</span></span>  
  
    -   <span data-ttu-id="d05ce-127">**차원** 창에서 `Read Definition` 해당 차원에 대 한 확인란을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d05ce-127">In the **Dimensions** pane, click the `Read Definition` check box for that dimension.</span></span> <span data-ttu-id="d05ce-128">숙련된 분석가 및 개발자는 정의를 수정하거나 다른 개체(예: 다른 차원, 큐브 개체 또는 마이닝 구조 및 모델)의 정의를 볼 수 있는 권한이 없어도 정의를 볼 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d05ce-128">Experienced analysts and developers may need to view the definition without permission to modify it or view the definitions of other objects (such as other dimensions, cube objects, or mining structures and models).</span></span>  
  
    -   <span data-ttu-id="d05ce-129">마이닝 구조 창에서 `Read Definition` 데이터 마이닝 구조 또는 모델에 대 한 확인란을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d05ce-129">In the Mining Structures pane, click the `Read Definition` check box for data mining structures or models.</span></span> <span data-ttu-id="d05ce-130">`Read Definition`는 데이터 모델을 검색 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d05ce-130">`Read Definition` is required for browsing the data model.</span></span> <span data-ttu-id="d05ce-131">자세한 내용은 [데이터 마이닝 구조 및 모델에 대한 권한 부여&#40;Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d05ce-131">See [Grant permissions on data mining structures and models &#40;Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md) for details.</span></span>  
  
4.  <span data-ttu-id="d05ce-132">**멤버 자격** 창에서 이 역할을 사용하여 Analysis Services에 연결하는 Windows 사용자 및 그룹 계정을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d05ce-132">In the **Membership** pane, enter the Windows user and group accounts that connect to Analysis Services using this role.</span></span>  
  
5.  <span data-ttu-id="d05ce-133">**확인** 을 클릭하여 역할 만들기를 마칩니다.</span><span class="sxs-lookup"><span data-stu-id="d05ce-133">Click **OK** to finish creating the role.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d05ce-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d05ce-134">See Also</span></span>  
 <span data-ttu-id="d05ce-135">[Analysis Services&#41;&#40;데이터베이스 사용 권한 부여](grant-database-permissions-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="d05ce-135">[Grant database permissions &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md) </span></span>  
 [<span data-ttu-id="d05ce-136">처리 권한 부여&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d05ce-136">Grant process permissions &#40;Analysis Services&#41;</span></span>](grant-process-permissions-analysis-services.md)  
  
  
