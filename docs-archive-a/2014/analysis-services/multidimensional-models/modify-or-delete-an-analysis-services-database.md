---
title: Analysis Services 데이터베이스 수정 또는 삭제 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], modifying
- removing databases
- deleting databases
- dropping databases
- databases [Analysis Services], deleting
- modifying databases
ms.assetid: e48e3988-c091-4379-aabc-4da62f709a7e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6182e91bd95754fe639e8a48548b5cab1835bdc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740552"
---
# <a name="modify-or-delete-an-analysis-services-database"></a><span data-ttu-id="ba7e1-102">Analysis Services 데이터베이스 수정 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="ba7e1-102">Modify or Delete an Analysis Services Database</span></span>
  <span data-ttu-id="ba7e1-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에 배포하기 전에 그리고 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 에 배포한 후에 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]데이터베이스의 이름과 설명을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba7e1-103">You can change the name and description of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database before deployment in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and after deployment in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="ba7e1-104">또한 환경에 따라 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스의 추가 설정을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba7e1-104">You can also adjust additional settings on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, depending on the environment.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ba7e1-105">온라인 모드에서 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 를 사용하여 데이터베이스 속성을 변경할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ba7e1-105">You cannot change database properties using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in online mode.</span></span>  
  
## <a name="modifying-databases-using-sql-server-management-studio"></a><span data-ttu-id="ba7e1-106">SQL Server Management Studio를 사용하여 데이터베이스 수정</span><span class="sxs-lookup"><span data-stu-id="ba7e1-106">Modifying Databases Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="ba7e1-107">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스를 배포한 후에는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 사용하여 데이터베이스에 포함된 데이터 원본에 연결할 때 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 사용하는 가장 모드를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba7e1-107">Once an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database is deployed, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to change the impersonation mode used by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] when connecting to data sources contained by the database.</span></span> <span data-ttu-id="ba7e1-108">가장 모드를 사용하면 처리, 검색 또는 드릴스루를 위해 데이터 원본에 연결을 시도할 때 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 사용하는 보안 컨텍스트를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba7e1-108">The impersonation mode allows you to specify the security context used by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] when attempting to connect to a data source for processing, browsing, or drillthrough purposes.</span></span>  
  
## <a name="modifying-databases-using-sql-server-data-tools"></a><span data-ttu-id="ba7e1-109">SQL Server Data Tools를 사용하여 데이터베이스 수정</span><span class="sxs-lookup"><span data-stu-id="ba7e1-109">Modifying Databases Using SQL Server Data Tools</span></span>  
 <span data-ttu-id="ba7e1-110">프로젝트 모드에서 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 를 사용하여 데이터베이스 정의에 사용되는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트의 캡션 및 설명에 대한 번역을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba7e1-110">You can use [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in project mode to modify the translations for the caption and description of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project used to define a database.</span></span> <span data-ttu-id="ba7e1-111">데이터베이스에서 번역을 사용 하는 방법에 대 한 자세한 내용은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [Analysis Services Multiidimensional 세계화 시나리오](../globalization-scenarios-for-analysis-services-multiidimensional.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ba7e1-111">For more information about using translations in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, see [Globalization scenarios for Analysis Services Multiidimensional](../globalization-scenarios-for-analysis-services-multiidimensional.md).</span></span>  
  
 <span data-ttu-id="ba7e1-112">또한 데이터베이스에 포함된 차원의 계정 특성에서 사용하는 계정 유형과 연결된 별칭 및 집계 함수를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba7e1-112">You can also set the aliases and aggregation functions associated with account types used by account attributes in dimensions contained by the database.</span></span> <span data-ttu-id="ba7e1-113">별칭을 사용하면 계정 차트의 계정 유형에 대해 조직에서 사용하는 비즈니스 관련 용어를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba7e1-113">Aliases allow you to select the business-specific terminology used by your organization for the account types in a chart of accounts.</span></span> <span data-ttu-id="ba7e1-114">계정 유형은 데이터베이스에 포함된 각 계정 유형에 대해 지정된 집계 함수를 사용하여 각 멤버에 대해 측정값을 집계하는 방법을 나타내기 위해 계정 특성의 멤버에서 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ba7e1-114">The account types are used by members of an account attribute to indicate how to aggregate measures over each member by using the aggregation functions specified for each account type contained in the database.</span></span> <span data-ttu-id="ba7e1-115">계정 특성에 대한 자세한 내용은 [특성 및 특성 계층](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ba7e1-115">For more information about account attributes, see [Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md).</span></span>  
  
## <a name="deleting-databases"></a><span data-ttu-id="ba7e1-116">데이터베이스 삭제</span><span class="sxs-lookup"><span data-stu-id="ba7e1-116">Deleting Databases</span></span>  
 <span data-ttu-id="ba7e1-117">기존 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스를 삭제하면 데이터베이스 및 해당 데이터베이스에 있는 모든 큐브, 차원 및 마이닝 모델도 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba7e1-117">Deleting an existing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database deletes the database and all cubes, dimensions, and mining models in the database.</span></span> <span data-ttu-id="ba7e1-118">기존 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서만 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba7e1-118">You can only delete an existing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-delete-an-analysis-services-database"></a><span data-ttu-id="ba7e1-119">Analysis Services 데이터베이스를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="ba7e1-119">To delete an Analysis Services database</span></span>  
  
1.  <span data-ttu-id="ba7e1-120">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ba7e1-120">Connect to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
2.  <span data-ttu-id="ba7e1-121">**개체 탐색기**에서 연결된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스의 노드를 확장한 다음 삭제할 개체가 표시되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ba7e1-121">In **Object Explorer**, expand the node for the connected [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and ensure that the object to be deleted is visible.</span></span>  
  
3.  <span data-ttu-id="ba7e1-122">삭제할 개체를 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ba7e1-122">Right-click the object to be deleted and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="ba7e1-123">**개체 삭제** 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ba7e1-123">In the **Delete Object** dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba7e1-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ba7e1-124">See Also</span></span>  
 [<span data-ttu-id="ba7e1-125">Analysis Services 데이터베이스 문서화 및 스크립트</span><span class="sxs-lookup"><span data-stu-id="ba7e1-125">Document and Script an Analysis Services Database</span></span>](document-and-script-an-analysis-services-database.md)  
  
  
