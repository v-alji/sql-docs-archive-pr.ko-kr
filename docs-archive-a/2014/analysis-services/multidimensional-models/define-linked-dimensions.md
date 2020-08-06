---
title: 연결 된 차원 정의 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], linked
- linked dimensions [Analysis Services]
ms.assetid: d5ad5eae-5dde-46a6-91c3-c8766d016dec
author: minewiskan
ms.author: owend
ms.openlocfilehash: 088dda52042a53c252eed8d759e54af4dee1a029
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728884"
---
# <a name="define-linked-dimensions"></a><span data-ttu-id="9ced8-102">연결된 차원 정의</span><span class="sxs-lookup"><span data-stu-id="9ced8-102">Define Linked Dimensions</span></span>
  <span data-ttu-id="9ced8-103">연결된 차원은 동일한 버전 및 호환성 수준의 다른 Analysis Services 데이터베이스에서 만들어지고 저장된 차원을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-103">A linked dimension is based on a dimension created and stored in another Analysis Services database of the same version and compatibility level.</span></span> <span data-ttu-id="9ced8-104">연결된 차원을 통해 하나의 데이터베이스에 차원을 만들고 저장하고 유지 관리할 수 있으며 이와 동시에 여러 데이터베이스의 사용자가 이 차원을 사용하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-104">By using a linked dimension, you can create, store, and maintain a dimension on one database, while making it available to users of multiple databases.</span></span> <span data-ttu-id="9ced8-105">연결된 차원은 사용자에게 다른 차원과 동일하게 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-105">To users, a linked dimension appears like any other dimension.</span></span>  
  
 <span data-ttu-id="9ced8-106">연결된 차원은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-106">Linked dimensions are read-only.</span></span> <span data-ttu-id="9ced8-107">차원을 수정하거나 새로운 관계를 만들려는 경우 원본 차원을 변경한 다음 연결된 차원 및 해당 관계를 삭제하고 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-107">If you want to modify the dimension or create new relationships, you must change the source dimension, then delete and recreate the linked dimension and its relationships.</span></span> <span data-ttu-id="9ced8-108">연결된 차원을 새로 고쳐서 원본 개체의 변경 내용을 적용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-108">You cannot refresh a linked dimension to pick up changes from the source object.</span></span>  
  
 <span data-ttu-id="9ced8-109">관련된 모든 측정값 그룹 및 차원은 같은 원본 데이터베이스를 기반으로 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-109">All related measure groups and dimensions must come from the same source database.</span></span> <span data-ttu-id="9ced8-110">로컬 측정값 그룹과 큐브를 추가할 연결된 차원 간에는 새로운 관계를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-110">You cannot create new relationships between local measure groups and the linked dimensions you add to your cube.</span></span> <span data-ttu-id="9ced8-111">연결된 차원과 측정값 그룹을 현재 큐브에 추가한 후에는 해당 관계를 원본 데이터베이스에서 유지 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-111">After linked dimensions and measure groups have been added to the current cube, the relationships between them must be maintained in their source database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9ced8-112">새로 고침을 사용할 수 없기 때문에 대부분의 Analysis Services 개발자는 차원을 연결하는 대신 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-112">Because refresh is not available, most Analysis Services developers copy dimensions rather than link them.</span></span> <span data-ttu-id="9ced8-113">동일한 솔루션 내에서 프로젝트 간에 차원을 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-113">You can copy dimensions across projects within the same solution.</span></span> <span data-ttu-id="9ced8-114">자세한 내용은 [SSAS에서 연결된 차원의 새로 고침](http://sqlblog.com/blogs/marco_russo/archive/2006/09/12/refresh-of-a-linked-dimension-in-ssas.aspx)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9ced8-114">For more information, see [Refresh of a linked dimension in SSAS](http://sqlblog.com/blogs/marco_russo/archive/2006/09/12/refresh-of-a-linked-dimension-in-ssas.aspx).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9ced8-115">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="9ced8-115">Prerequisites</span></span>  
 <span data-ttu-id="9ced8-116">차원을 제공하는 원본 데이터베이스와 차원을 사용하는 현재 데이터베이스는 버전 및 호환성 수준이 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-116">The source database that provides the dimension and the current database that uses it must be at the same version and compatibility level.</span></span> <span data-ttu-id="9ced8-117">자세한 내용은 [다차원 데이터베이스의 호환성 수준 설정 &#40;Analysis Services&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ced8-117">For more information, see [Set the Compatibility Level of a Multidimensional Database &#40;Analysis Services&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md).</span></span>  
  
 <span data-ttu-id="9ced8-118">원본 데이터베이스가 배포되고 온라인 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-118">The source database must be deployed and online.</span></span> <span data-ttu-id="9ced8-119">연결된 개체를 게시하거나 사용하는 서버가 작업을 허용하도록 구성되어야 합니다(아래 참조).</span><span class="sxs-lookup"><span data-stu-id="9ced8-119">Servers that publish or consume linked objects must be configured to allow the operation (see below).</span></span>  
  
 <span data-ttu-id="9ced8-120">사용할 차원은 자체적으로 연결된 차원이 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-120">The dimension you want to use cannot itself be a linked dimension.</span></span>  
  
## <a name="configure-server-to-allow-linked-objects"></a><span data-ttu-id="9ced8-121">연결된 개체를 허용하도록 서버 구성</span><span class="sxs-lookup"><span data-stu-id="9ced8-121">Configure server to allow linked objects</span></span>  
  
1.  <span data-ttu-id="9ced8-122">SQL Server Management Studio에서 Analysis Services 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-122">In SQL Server Management Studio, connect to an Analysis Services server.</span></span> <span data-ttu-id="9ced8-123">개체 탐색기에서 서버 이름을 마우스 오른쪽 단추로 클릭한 다음 **패싯**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-123">In Object Explorer, right-click the server name and select **Facets**.</span></span>  
  
2.  <span data-ttu-id="9ced8-124">**LinkedObjectsLinksFromOtherInstancesEnabled** 를 **True** 로 설정하여 서버에서 다른 인스턴스에서 실행 중인 데이터베이스에 있는 연결된 개체에 대한 요청을 실행할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-124">Set **LinkedObjectsLinksFromOtherInstancesEnabled** to **True** to allow the server to issue requests for linked objects that reside in databases running on other instances.</span></span>  
  
3.  <span data-ttu-id="9ced8-125">**LinkedObjectsLinksToOtherInstances** 를 **True** 로 설정하여 서버에서 다른 인스턴스에서 실행 중인 데이터베이스에 있는 연결된 개체에 대한 데이터를 요청할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-125">Set **LinkedObjectsLinksToOtherInstances** to **True** to allow the server to request data for linked on databases running on other instances.</span></span>  
  
## <a name="create-a-linked-dimension-in-sql-server-data-tools"></a><span data-ttu-id="9ced8-126">SQL Server Data Tools에서 연결된 차원 만들기</span><span class="sxs-lookup"><span data-stu-id="9ced8-126">Create a linked dimension in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="9ced8-127">마법사를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-127">Start the wizard.</span></span> <span data-ttu-id="9ced8-128">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 **데이터베이스 또는 프로젝트의** 차원 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 폴더를 마우스 오른쪽 단추로 클릭한 다음 **새 연결된 차원**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-128">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], right-click the **Dimensions** folder in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database or project, and then click **New Linked Dimension**.</span></span>  
  
2.  <span data-ttu-id="9ced8-129">차원을 제공하는 Analysis Services 데이터베이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-129">Connect to the Analysis Services database that provides the dimension.</span></span> <span data-ttu-id="9ced8-130">연결된 개체 마법사의 **데이터 원본 선택** 페이지에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터 원본을 선택하거나 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-130">On the **Select a Data Source** page of the Linked Object Wizard, choose the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data source or create a new one.</span></span>  
  
3.  <span data-ttu-id="9ced8-131">마법사의 **개체 선택** 페이지에서 원격 데이터베이스에 있는 연결할 차원을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-131">On the **Select Objects** page of the wizard, choose the dimensions you want to link to in the remote database.</span></span>  
  
4.  <span data-ttu-id="9ced8-132">**마법사 완료** 페이지에서 연결된 개체를 미리 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-132">On the **Completing the Wizard** page, you can preview the linked objects.</span></span> <span data-ttu-id="9ced8-133">이미 있는 것과 이름이 같은 차원을 연결하면 이름에 서수 번호(중복된 첫 번째 이름의 경우 '1'로 시작)가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-133">If you link a dimension that has the same name as one that already exists, an ordinal number (starting with '1' for the first duplicated name) is appended to the name.</span></span> <span data-ttu-id="9ced8-134">마법사를 완료하면 **차원** 폴더에 차원이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-134">When you complete the wizard, the dimension is added to the **Dimensions** folder.</span></span>  
  
##  <a name="create-a-new-data-source-connection-to-an-analysis-services-database"></a><a name="bkmk_CreateNew"></a> <span data-ttu-id="9ced8-135">Analysis Services 데이터베이스에 대한 새 데이터 원본 연결 만들기</span><span class="sxs-lookup"><span data-stu-id="9ced8-135">Create a New Data Source Connection to an Analysis Services Database</span></span>  
 <span data-ttu-id="9ced8-136">새 데이터 원본 마법사를 사용하여 차원을 제공하는 Analysis Services 데이터베이스에 대한 프로젝트 연결 정보를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-136">Use the New Data Source wizard to add to your project connection information about the Analysis Services database that provides the dimension.</span></span> <span data-ttu-id="9ced8-137">연결된 개체 마법사의 데이터 원본 선택 페이지에서 **새 데이터 원본** 을 클릭하여 마법사를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-137">You can start the wizard by clicking **New Data Source** in the Select a Data Source page of the Linked Objects wizard.</span></span>  
  
1.  <span data-ttu-id="9ced8-138">데이터 원본 마법사 시작의 연결 정의 방법 선택 페이지에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-138">In the Data Source Wizard, on the Select how to define the connection page, click **New**.</span></span>  
  
2.  <span data-ttu-id="9ced8-139">연결 관리자에서 공급자가 **Native OLE DB\Microsoft OLE DB Provider for Analysis Services 11.0**으로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-139">In Connection Manager, verify that the provider is set to **Native OLE DB\Microsoft OLE DB Provider for Analysis Services 11.0**.</span></span>  
  
3.  <span data-ttu-id="9ced8-140">서버 이름 (명명 된 인스턴스에 대해 *servername* \\ *instancename* 사용)을 입력 하거나 **localhost** 를 입력 하 여 같은 컴퓨터에서 실행 되는 Analysis Services 서버에 연결 합니다.<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9ced8-140">Enter the name of the server (use *servername*\\*instancename* for a named instance)<sup>1</sup> or type **localhost** to connect to an Analysis Services server that is running on the same computer.</span></span>  
  
4.  <span data-ttu-id="9ced8-141">연결을 위해 Windows 인증을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-141">Use Windows authentication for the connection.</span></span>  
  
5.  <span data-ttu-id="9ced8-142">**초기 카탈로그**에서 아래쪽 화살표를 클릭하여 이 서버의 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-142">In **Initial catalog**, click the down arrow to select a database on this server.</span></span>  
  
6.  <span data-ttu-id="9ced8-143">데이터 원본 마법사에서 **다음** 을 클릭하여 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-143">On the Data Source Wizard, click **Next** to continue.</span></span>  
  
7.  <span data-ttu-id="9ced8-144">가장 정보 페이지에서 **서비스 계정 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-144">On the Impersonation Information page, click **Use the service account**.</span></span> <span data-ttu-id="9ced8-145">**다음**을 클릭한 다음 마법사를 끝냅니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-145">Click **Next**, and then finish the wizard.</span></span> <span data-ttu-id="9ced8-146">방금 정의한 연결이 연결된 개체 마법사에서 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-146">The connection you just defined will be selected in the Linked Objects Wizard.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9ced8-147">다음 단계</span><span class="sxs-lookup"><span data-stu-id="9ced8-147">Next Steps</span></span>  
 <span data-ttu-id="9ced8-148">연결된 차원의 구조는 변경할 수 없으므로 차원 디자이너의 **차원 구조** 탭에서 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-148">You cannot change the structure of a linked dimension, so you cannot view it with the **Dimension Structure** tab of Dimension Designer.</span></span> <span data-ttu-id="9ced8-149">연결 된 차원을 처리 한 후에는 **브라우저** 탭에서 볼 수 있습니다. 이름을 변경 하 고 이름에 대 한 번역을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ced8-149">After processing the linked dimension, you can view it with the **Browser** tab. You can also change its name and create a translation for the name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ced8-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9ced8-150">See Also</span></span>  
 <span data-ttu-id="9ced8-151">[다차원 데이터베이스 &#40;Analysis Services의 호환성 수준을 설정&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="9ced8-151">[Set the Compatibility Level of a Multidimensional Database &#40;Analysis Services&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md) </span></span>  
 <span data-ttu-id="9ced8-152">[연결 된 측정값 그룹](linked-measure-groups.md) </span><span class="sxs-lookup"><span data-stu-id="9ced8-152">[Linked Measure Groups](linked-measure-groups.md) </span></span>  
 [<span data-ttu-id="9ced8-153">차원 관계</span><span class="sxs-lookup"><span data-stu-id="9ced8-153">Dimension Relationships</span></span>](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)  
  
  
