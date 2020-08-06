---
title: 로컬 큐브 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- cubes [Analysis Services], local
ms.assetid: e52e1515-35a7-4dc3-9bbf-736d176ba0c7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 75f02dd54992e9cc4f94d9845e0e25de5ed988f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653593"
---
# <a name="local-cubes-analysis-services---multidimensional-data"></a><span data-ttu-id="efc03-102">로컬 큐브(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="efc03-102">Local Cubes (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="efc03-103">로컬 큐브를 만들거나 업데이트하거나 삭제하려면 ASSL 스크립트나 AMO 프로그램을 작성하여 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-103">To create, update or delete local cubes, you must write and execute either an ASSL script or an AMO program.</span></span>  
  
 <span data-ttu-id="efc03-104">로컬 큐브와 로컬 마이닝 모델을 사용하면 네트워크에 연결되어 있지 않은 클라이언트 워크스테이션을 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-104">Local cubes and local mining models allow analysis on a client workstation while it is disconnected from the network.</span></span> <span data-ttu-id="efc03-105">예를 들어 클라이언트 애플리케이션은 다음 그림과 같이 로컬 큐브 엔진을 로드하여 로컬 큐브를 만들고 쿼리하는 OLAP 9.0 공급자(MSOLAP.3)용 OLE DB를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-105">For example, a client application might call the OLE DB for OLAP 9.0 Provider (MSOLAP.3), which loads the local cube engine to create and query local cubes, as shown in the following illustration:</span></span>  
  
 <span data-ttu-id="efc03-106">![로컬 큐브 및 모델에 대한 클라이언트 아키텍처](../../../analysis-services/dev-guide/media/as-localcubearch9.gif "로컬 큐브 및 모델에 대한 클라이언트 아키텍처")</span><span class="sxs-lookup"><span data-stu-id="efc03-106">![Client architecture for local cubes and models](../../../analysis-services/dev-guide/media/as-localcubearch9.gif "Client architecture for local cubes and models")</span></span>  
  
 <span data-ttu-id="efc03-107">ADMOD.NET 및 AMO(Analysis Management Objects)도 로컬 큐브와 상호 작용할 때 로컬 큐브 엔진을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-107">ADMOD.NET and Analysis Management Objects (AMO) also load the local cube engine when interacting with local cubes.</span></span> <span data-ttu-id="efc03-108">로컬 큐브 엔진은 로컬 큐브에 연결할 때 로컬 큐브 파일을 배타적으로 잠그므로 단일 프로세스에서만 로컬 큐브 파일에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-108">Only a single process can access a local cube file, because the local cube engine exclusively locks a local cube file when it establishes a connection to the local cube.</span></span> <span data-ttu-id="efc03-109">단일 프로세스 내에서는 동시에 5개의 연결이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-109">With a process, up to five simultaneous connections are permitted.</span></span>  
  
 <span data-ttu-id="efc03-110">하나의 .cub 파일에는 두 개 이상의 큐브 또는 데이터 마이닝 모델이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-110">A .cub file may contain more than one cube or data mining model.</span></span> <span data-ttu-id="efc03-111">로컬 큐브 및 데이터 마이닝 모델에 대한 쿼리는 로컬 큐브 엔진에서 처리하므로 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 인스턴스에 연결할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-111">Queries to the local cubes and data mining models are handled by the local cube engine and do not require a connection to an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="efc03-112">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 및 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]를 사용하여 로컬 큐브를 관리할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-112">The use of [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] to manage local cubes is not supported.</span></span>  
  
## <a name="local-cubes"></a><span data-ttu-id="efc03-113">로컬 큐브</span><span class="sxs-lookup"><span data-stu-id="efc03-113">Local Cubes</span></span>  
 <span data-ttu-id="efc03-114">로컬 큐브는 인스턴스의 기존 큐브나 관계형 데이터 원본의 생성 및 채워질 수 있습니다 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="efc03-114">A local cube can be created and populated from either an existing cube in an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance or from a relational data source.</span></span>  
  
|<span data-ttu-id="efc03-115">로컬 큐브 데이터의 원본</span><span class="sxs-lookup"><span data-stu-id="efc03-115">Source for data for local cube</span></span>|<span data-ttu-id="efc03-116">생성 방법</span><span class="sxs-lookup"><span data-stu-id="efc03-116">Creation method</span></span>|  
|------------------------------------|---------------------|  
|<span data-ttu-id="efc03-117">서버 기반 큐브</span><span class="sxs-lookup"><span data-stu-id="efc03-117">Server-based cube</span></span>|<span data-ttu-id="efc03-118">CREATE GLOBAL CUBE 문 또는 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] SCRIPTING l (Scripting Language) 스크립트를 사용 하 여 서버 기반 큐브에서 큐브를 만들고 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-118">You can use either the CREATE GLOBAL CUBE statement or an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Scripting Language (ASSL) script to create and populate a cube from a server-based cube.</span></span> <span data-ttu-id="efc03-119">자세한 내용은 [CREATE GLOBAL CUBE Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube) 또는 [Analysis Services 스크립팅 언어 &#40;&#41; 참조](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="efc03-119">For more information, see [CREATE GLOBAL CUBE Statement  &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube) or [Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla).</span></span>|  
|<span data-ttu-id="efc03-120">관계형 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="efc03-120">Relational data source</span></span>|<span data-ttu-id="efc03-121">ASSL 스크립트를 사용하여 OLE DB 관계형 데이터베이스에서 큐브를 만들고 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-121">You use an ASSL script to create and populate a cube from an OLE DB relational database.</span></span> <span data-ttu-id="efc03-122">ASSL을 사용하여 로컬 큐브를 만들려면 로컬 큐브 파일(\*.cub)에 연결하고 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 인스턴스에 대해 ASSL 스크립트를 실행하는 것과 같은 방식으로 ASSL 스크립트를 실행하여 서버 큐브를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-122">To create a local cube using ASSL, you simply connect to a local cube file (\*.cub) and execute the ASSL script in the same manner as executing an ASSL script against an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance to create a server cube.</span></span> <span data-ttu-id="efc03-123">자세한 내용은 [Analysis Services 스크립팅 언어 &#40;,&#41; 참조](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="efc03-123">For more information, see [Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla).</span></span>|  
  
 <span data-ttu-id="efc03-124">REFRESH CUBE 문을 사용하여 로컬 큐브를 다시 생성하고 해당 데이터를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-124">Use the REFRESH CUBE statement to rebuild a local cube and update its data.</span></span> <span data-ttu-id="efc03-125">자세한 내용은 [CUBE 문 &#40;MDX&#41;새로 고침 ](/sql/mdx/mdx-data-definition-refresh-cube)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="efc03-125">For more information, see [REFRESH CUBE Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-refresh-cube).</span></span>  
  
### <a name="local-cubes-created-from-server-based-cubes"></a><span data-ttu-id="efc03-126">서버 기반 큐브에서 만든 로컬 큐브</span><span class="sxs-lookup"><span data-stu-id="efc03-126">Local Cubes Created from Server-based Cubes</span></span>  
 <span data-ttu-id="efc03-127">서버 기반 큐브에서 로컬 큐브를 만들 때는 다음과 같은 사항을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-127">When creating local cubes created from server-based cubes, the following considerations apply:</span></span>  
  
-   <span data-ttu-id="efc03-128">고유 카운트 측정값이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-128">Distinct count measures are not supported.</span></span>  
  
-   <span data-ttu-id="efc03-129">측정값을 추가할 때 추가할 측정값과 관련된 하나 이상의 차원을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-129">When you add a measure, you must also include at least one dimension that is related to the measure being added.</span></span> <span data-ttu-id="efc03-130">측정값 그룹의 차원 관계에 대 한 자세한 내용은 [차원 관계](../../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="efc03-130">For more information about dimension relationships to measure groups, see [Dimension Relationships](../../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).</span></span>  
  
-   <span data-ttu-id="efc03-131">부모-자식 계층을 추가할 때 부모-자식 계층의 수준과 필터는 무시되고 전체 부모-자식 계층이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-131">When you add a parent-child hierarchy, levels and filters on a parent-child hierarchy are ignored and the entire parent-child hierarchy is included.</span></span>  
  
-   <span data-ttu-id="efc03-132">멤버 속성이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-132">Member properties are not created.</span></span>  
  
-   <span data-ttu-id="efc03-133">반가산적 측정값을 포함할 때 계정 차원 및 시간 차원에 조각이 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-133">When you include a semi-additive measure, no slices are permitted on either the Account or the Time dimension.</span></span>  
  
-   <span data-ttu-id="efc03-134">참조 차원이 항상 구체화됩니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-134">Reference dimensions are always materialized.</span></span>  
  
-   <span data-ttu-id="efc03-135">다 대 다 차원을 포함할 때는 다음과 같은 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-135">When you include a many-to-many dimension, the following rules apply:</span></span>  
  
    -   <span data-ttu-id="efc03-136">다 대 다 차원을 조각화할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-136">You cannot slice the many-to-many dimension.</span></span>  
  
    -   <span data-ttu-id="efc03-137">중간 측정값 그룹에서 측정값을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-137">You must add a measure from the intermediary measure group.</span></span>  
  
    -   <span data-ttu-id="efc03-138">다 대 다 관계에 속한 두 측정값 그룹에 공통된 차원을 조각화할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-138">You cannot slice any of the dimensions common to the two measure groups involved in the many-to-may relationship.</span></span>  
  
-   <span data-ttu-id="efc03-139">로컬 큐브에 추가된 측정값과 차원을 사용하는 계산 멤버, 명명된 집합 및 할당만 로컬 큐브에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-139">Only those calculated members, named sets, and assignments that rely upon measures and dimensions added to the local cube will appear in the local cube.</span></span> <span data-ttu-id="efc03-140">잘못된 계산 멤버, 명명된 집합 및 할당은 자동으로 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-140">Invalid calculated members, named sets, and assignments will be automatically excluded.</span></span>  
  
### <a name="security"></a><span data-ttu-id="efc03-141">보안</span><span class="sxs-lookup"><span data-stu-id="efc03-141">Security</span></span>  
 <span data-ttu-id="efc03-142">사용자가 서버 큐브에서 로컬 큐브를 만들려면 서버 큐브에 대 한 **드릴스루 및 로컬 큐브** 사용 권한을 사용자에 게 부여 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-142">In order for a user to create a local cube from a server cube, the user must be granted **Drillthrough and Local Cube** permissions on the server cube.</span></span> <span data-ttu-id="efc03-143">자세한 내용은 [큐브 또는 모델 권한 부여 &#40;Analysis Services&#41;](../../multidimensional-models/grant-cube-or-model-permissions-analysis-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="efc03-143">For more information, see [Grant cube or model permissions &#40;Analysis Services&#41;](../../multidimensional-models/grant-cube-or-model-permissions-analysis-services.md).</span></span>  
  
 <span data-ttu-id="efc03-144">로컬 큐브는 서버 큐브와 같이 역할을 사용하여 보안이 설정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-144">Local cubes are not secured using roles like server cubes.</span></span> <span data-ttu-id="efc03-145">로컬 큐브 파일에 대한 파일 수준 액세스 권한이 있는 사용자는 누구나 해당 파일에 있는 큐브를 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-145">Anyone with file-level access to a local cube file can query cubes in it.</span></span> <span data-ttu-id="efc03-146">이를 방지하려면 로컬 큐브 파일의 `Encryption Password` 연결 속성을 사용하여 로컬 큐브 파일에 암호를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-146">You can use the `Encryption Password` connection property on a local cube file to set a password on the local cube file.</span></span> <span data-ttu-id="efc03-147">로컬 큐브 파일에 암호를 설정하면 로컬 큐브 파일을 쿼리하기 위해 해당 파일에 연결할 때 항상 이 암호를 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efc03-147">Setting a password on a local cube file requires all future connections to the local cube file to use this password in order to query the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efc03-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="efc03-148">See Also</span></span>  
 <span data-ttu-id="efc03-149">[MDX&#41;&#40;전역 큐브 문 만들기](/sql/mdx/mdx-data-definition-create-global-cube) </span><span class="sxs-lookup"><span data-stu-id="efc03-149">[CREATE GLOBAL CUBE Statement  &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube) </span></span>  
 <span data-ttu-id="efc03-150">[Analysis Services 스크립팅 언어 &#40;를 사용 하 여 개발&#41;](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md) </span><span class="sxs-lookup"><span data-stu-id="efc03-150">[Developing with Analysis Services Scripting Language &#40;ASSL&#41;](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md) </span></span>  
 [<span data-ttu-id="efc03-151">MDX &#40;MDX&#41;새로 고침</span><span class="sxs-lookup"><span data-stu-id="efc03-151">REFRESH CUBE Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-definition-refresh-cube)  
  
  
