---
title: 범주별로 분류한 웹 서비스 작업(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: e3f346b5-7e26-481d-9821-1846e2e91289
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0f7dd682f55c16c6dcbff9f0f669593a10486da6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653493"
---
# <a name="categorized-web-service-operations-master-data-services"></a><span data-ttu-id="f5cfa-102">범주별로 분류한 웹 서비스 작업(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f5cfa-102">Categorized Web Service Operations (Master Data Services)</span></span>
  <span data-ttu-id="f5cfa-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 웹 서비스에는 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 가 해당 사용자 인터페이스를 통해 사용하는 모든 기능을 제어하기 위한 코드를 작성할 수 있는 완전한 작업 집합이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-103">The [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web service contains a complete set of operations that let you write code to control all of the features that [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] does through its user interface.</span></span> <span data-ttu-id="f5cfa-104">웹 서비스 작업은 <xref:Microsoft.MasterDataServices.IService> 인터페이스를 통해 정의되며 <xref:Microsoft.MasterDataServices.ServiceClient>에서 메서드로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-104">The web service operations are defined by the <xref:Microsoft.MasterDataServices.IService> interface and are implemented as methods in the <xref:Microsoft.MasterDataServices.ServiceClient> class.</span></span> <span data-ttu-id="f5cfa-105">이 항목에서는 웹 서비스 API를 사용하는 방법을 이해하는 데 도움이 되도록 웹 서비스 작업을 개념적 범주로 그룹화하였습니다.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-105">This topic groups the web service operations into conceptual categories to help you understand how to use the web service API.</span></span>  
  
## <a name="model-operations"></a><span data-ttu-id="f5cfa-106">모델 작업</span><span class="sxs-lookup"><span data-stu-id="f5cfa-106">Model Operations</span></span>  
 <span data-ttu-id="f5cfa-107">이러한 작업은 모델을 만들고, 업데이트하고, 삭제하는 데 사용될 뿐 아니라 모델의 모든 콘텐츠(예: 엔터티, 계층 및 버전)에 대해 작업을 수행하는 데에도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-107">These operations are used to create, update, and delete models, as well as to operate on all the contents of a model, such as entities, hierarchies, and versions.</span></span> <span data-ttu-id="f5cfa-108">자세한 내용은 [모델&#40;Master Data Services&#41;](../models-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-108">For more information, see [Models &#40;Master Data Services&#41;](../models-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.MetadataClone%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.MetadataCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.MetadataDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.MetadataGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.MetadataUpdate%2A>|  
  
## <a name="entity-operations"></a><span data-ttu-id="f5cfa-109">엔터티 작업</span><span class="sxs-lookup"><span data-stu-id="f5cfa-109">Entity Operations</span></span>  
 <span data-ttu-id="f5cfa-110">이러한 작업은 단일 엔터티의 멤버를 만들고, 업데이트하고, 삭제하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-110">These operations are used to create, update, and delete the members of a single entity.</span></span> <span data-ttu-id="f5cfa-111">자세한 내용은 [엔터티&#40;Master Data Services&#41;](../entities-master-data-services.md) 및 [멤버&#40;Master Data Services&#41;](../members-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-111">For more information, see [Entities &#40;Master Data Services&#41;](../entities-master-data-services.md) and [Members &#40;Master Data Services&#41;](../members-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMemberKeyLookup%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersCopy%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersMerge%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersUpdate%2A>|  
  
## <a name="member-operations"></a><span data-ttu-id="f5cfa-112">멤버 작업</span><span class="sxs-lookup"><span data-stu-id="f5cfa-112">Member Operations</span></span>  
 <span data-ttu-id="f5cfa-113">이러한 작업은 멤버를 가져오고, 업데이트하고, 삭제하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-113">These operations are used to get, update, and delete members.</span></span> <span data-ttu-id="f5cfa-114">작업의 대상이 되는 멤버 집합에는 여러 엔터티의 멤버를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-114">The set of members operated on can contain members from multiple entities.</span></span> <span data-ttu-id="f5cfa-115">자세한 내용은 [멤버&#40;Master Data Services&#41;](../members-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-115">For more information, see [Members &#40;Master Data Services&#41;](../members-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ModelMembersBulkDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ModelMembersBulkMerge%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ModelMembersBulkUpdate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ModelMembersGet%2A>|  
  
## <a name="attribute-and-hierarchy-operations"></a><span data-ttu-id="f5cfa-116">특성 및 계층 작업</span><span class="sxs-lookup"><span data-stu-id="f5cfa-116">Attribute and Hierarchy Operations</span></span>  
 <span data-ttu-id="f5cfa-117">이러한 작업은 특성 및 계층 정보를 가져오는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-117">These operations are used to get attribute and hierarchy information.</span></span> <span data-ttu-id="f5cfa-118">특성 및 계층은 <xref:Microsoft.MasterDataServices.ServiceClient.MetadataUpdate%2A>와 같은 모델 작업을 사용하여 수정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-118">Attributes and hierarchies can also be modified by using the model operations, such as <xref:Microsoft.MasterDataServices.ServiceClient.MetadataUpdate%2A>.</span></span> <span data-ttu-id="f5cfa-119">자세한 내용은 [특성&#40;Master Data Services&#41;](../attributes-master-data-services.md) 및 [계층&#40;Master Data Services&#41;](../hierarchies-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-119">For more information, see [Attributes &#40;Master Data Services&#41;](../attributes-master-data-services.md) and [Hierarchies &#40;Master Data Services&#41;](../hierarchies-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMemberAttributesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.HierarchyMembersGet%2A>|  
  
## <a name="business-rule-operations"></a><span data-ttu-id="f5cfa-120">비즈니스 규칙 작업</span><span class="sxs-lookup"><span data-stu-id="f5cfa-120">Business Rule Operations</span></span>  
 <span data-ttu-id="f5cfa-121">이러한 작업은 비즈니스 규칙을 만들고, 업데이트하고, 삭제하고, 게시하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-121">These operations are used to create, update, delete, and publish business rules.</span></span> <span data-ttu-id="f5cfa-122">자세한 내용은 [비즈니스 규칙&#40;Master Data Services&#41;](../business-rules-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-122">For more information, see [Business Rules &#40;Master Data Services&#41;](../business-rules-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesClone%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesPaletteGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesPublish%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesUpdate%2A>|  
  
## <a name="annotation-operations"></a><span data-ttu-id="f5cfa-123">주석 작업</span><span class="sxs-lookup"><span data-stu-id="f5cfa-123">Annotation Operations</span></span>  
 <span data-ttu-id="f5cfa-124">이러한 작업은 주석을 만들고, 업데이트하고, 삭제하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-124">These operations are used to create, update, and delete annotations.</span></span> <span data-ttu-id="f5cfa-125">자세한 내용은 [주석&#40;Master Data Services&#41;](../annotations-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-125">For more information, see [Annotations &#40;Master Data Services&#41;](../annotations-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.AnnotationsDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.AnnotationsUpdate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMemberAnnotationsCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMemberAnnotationsGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.TransactionAnnotationsCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.TransactionAnnotationsGet%2A>|  
  
## <a name="transaction-operations"></a><span data-ttu-id="f5cfa-126">트랜잭션 작업</span><span class="sxs-lookup"><span data-stu-id="f5cfa-126">Transaction Operations</span></span>  
 <span data-ttu-id="f5cfa-127">이러한 작업은 트랜잭션을 가져오고 되돌리는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-127">These operations are used to get and reverse transactions.</span></span> <span data-ttu-id="f5cfa-128">자세한 내용은 [트랜잭션&#40;Master Data Services&#41;](../transactions-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-128">For more information, see [Transactions &#40;Master Data Services&#41;](../transactions-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.TransactionsGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.TransactionsReverse%2A>|  
  
## <a name="version-and-validation-operations"></a><span data-ttu-id="f5cfa-129">버전 및 유효성 검사 작업</span><span class="sxs-lookup"><span data-stu-id="f5cfa-129">Version and Validation Operations</span></span>  
 <span data-ttu-id="f5cfa-130">이러한 작업은 버전을 복사하고 그 유효성을 검사하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-130">These operations are used to copy and validate versions.</span></span> <span data-ttu-id="f5cfa-131">자세한 내용은 [버전&#40;Master Data Services&#41;](../versions-master-data-services.md) 및 [유효성 검사&#40;Master Data Services&#41;](../validation-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-131">For more information, see [Versions &#40;Master Data Services&#41;](../versions-master-data-services.md) and [Validation &#40;Master Data Services&#41;](../validation-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.VersionCopy%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ValidationGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ValidationProcess%2A>|  
  
## <a name="data-quality-operations"></a><span data-ttu-id="f5cfa-132">데이터 품질 작업</span><span class="sxs-lookup"><span data-stu-id="f5cfa-132">Data Quality Operations</span></span>  
 <span data-ttu-id="f5cfa-133">이러한 작업은 데이터 품질 태스크를 수행하고 그 결과를 검토하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-133">These operations are used to perform data quality tasks and to examine their results.</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityCleansingOperationCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityMatchingOperationCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityOperationStart%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityInstalledState%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityKnowledgeBasesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityOperationResultsGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityOperationStatus%2A>|  
  
## <a name="data-import-operations"></a><span data-ttu-id="f5cfa-134">데이터 가져오기 작업</span><span class="sxs-lookup"><span data-stu-id="f5cfa-134">Data Import Operations</span></span>  
 <span data-ttu-id="f5cfa-135">이러한 작업은 데이터를 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 데이터베이스로 가져오는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-135">These operations are used to import data into a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="f5cfa-136">자세한 내용은 [데이터 가져오기&#40;Master Data Services&#41;](../overview-importing-data-from-tables-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-136">For more information, see [Data Import &#40;Master Data Services&#41;](../overview-importing-data-from-tables-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityStagingClear%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityStagingGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityStagingLoad%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityStagingProcess%2A>|  
  
 <span data-ttu-id="f5cfa-137">다음 작업은 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]에 포함된 준비 프로세스를 사용하여 데이터를 가져오는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-137">The following operations are used to import data by using the staging process included in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="f5cfa-138">이러한 작업은 기존 데이터베이스를 지원하는 데에만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-138">These operations should be used only to support existing databases.</span></span> <span data-ttu-id="f5cfa-139">새로운 개발 작업에서는 앞에 나열된 작업을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-139">For new development, use the previously listed operations.</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.StagingClear%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.StagingGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.StagingNameCheck%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.StagingProcess%2A>|  
  
## <a name="data-export-operations"></a><span data-ttu-id="f5cfa-140">데이터 내보내기 작업</span><span class="sxs-lookup"><span data-stu-id="f5cfa-140">Data Export Operations</span></span>  
 <span data-ttu-id="f5cfa-141">이러한 작업은 구독 뷰를 통해 데이터를 내보내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-141">These operations are used to export data through the use of subscription views.</span></span> <span data-ttu-id="f5cfa-142">자세한 내용은 [데이터 내보내기 &#40;MDS(Master Data Services)&#41;](../overview-exporting-data-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-142">For more information, see [Exporting Data &#40;Master Data Services&#41;](../overview-exporting-data-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ExportViewCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ExportViewDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ExportViewListGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ExportViewUpdate%2A>|  
  
## <a name="security-operations"></a><span data-ttu-id="f5cfa-143">보안 운영</span><span class="sxs-lookup"><span data-stu-id="f5cfa-143">Security Operations</span></span>  
 <span data-ttu-id="f5cfa-144">이러한 작업은 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 데이터베이스에 대한 액세스를 제어하는 보안 설정을 수정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-144">These operations are used to modify the security settings that control access to the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="f5cfa-145">자세한 내용은 [보안&#40;Master Data Services&#41;](../security-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-145">For more information, see [Security &#40;Master Data Services&#41;](../security-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrincipalsClone%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrincipalsCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrincipalsDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrincipalsGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrincipalsUpdate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrivilegesClone%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrivilegesCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrivilegesDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrivilegesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrivilegesUpdate%2A>|  
  
## <a name="system-operations"></a><span data-ttu-id="f5cfa-146">시스템 작업</span><span class="sxs-lookup"><span data-stu-id="f5cfa-146">System Operations</span></span>  
 <span data-ttu-id="f5cfa-147">이러한 작업은 시스템 설정 및 사용자 기본 설정을 가져오고 업데이트하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5cfa-147">These operations are used to get and update system settings and user preferences.</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ServiceCheck%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ServiceVersionGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SystemDomainListGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SystemPropertiesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SystemSettingsGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SystemSettingsUpdate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.UserPreferencesDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.UserPreferencesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.UserPreferencesUpdate%2A>|  
  
  
