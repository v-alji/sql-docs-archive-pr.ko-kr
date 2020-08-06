---
title: 데이터 가져오기 (MDS(Master Data Services)) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- staging process [Master Data Services], about staging process
- importing data [Master Data Services]
- staging process [Master Data Services]
ms.assetid: 181d1e22-379c-45d1-b03c-e1e22ff14164
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 403eca212611397fb3ba30f8fe12a2aa8b5e83ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646550"
---
# <a name="data-import-master-data-services"></a><span data-ttu-id="34760-102">데이터 가져오기(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="34760-102">Data Import (Master Data Services)</span></span>
  <span data-ttu-id="34760-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 데이터에 대한 모델을 만들면 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스에서 데이터 추가를 시작하고 데이터를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34760-103">Once you've created a model for your data in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can start adding data and make changes to data in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>   <span data-ttu-id="34760-104">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 준비 표, 저장 프로시저 및 마스터 데이터 관리자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34760-104">You use [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] staging tables, stored procedures and Master Data Manager .</span></span>

 <span data-ttu-id="34760-105">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] 를 사용 하 여 데이터를 MDS 리포지토리 (데이터베이스)에 추가할 수도 있습니다 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="34760-105">You can also use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)], to add data to the MDS repository ([!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database).</span></span> <span data-ttu-id="34760-106">자세한 내용은 [Excel용 MDS 추가 기능&#41;&#40;게시 데이터 ](microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34760-106">For more information, see [Publishing Data &#40;MDS Add-in for Excel&#41;](microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md).</span></span>

 <span data-ttu-id="34760-107">데이터를 추가 및 업데이트할 때 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34760-107">When you add and update data, you can do the following.</span></span>

-   <span data-ttu-id="34760-108">멤버 로드 및 업데이트, 특성 값 업데이트</span><span class="sxs-lookup"><span data-stu-id="34760-108">Load and update members, and update attribute values</span></span>

-   <span data-ttu-id="34760-109">멤버 비활성화 및 삭제</span><span class="sxs-lookup"><span data-stu-id="34760-109">Deactivate and delete members</span></span>

-   <span data-ttu-id="34760-110">명시적 계층 멤버 이동</span><span class="sxs-lookup"><span data-stu-id="34760-110">Move explicit hierarchy members</span></span>

 <span data-ttu-id="34760-111">데이터를 추가하고 업데이트하는 절차에는 다음의 주요 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="34760-111">Adding and updating data  includes the following main tasks.</span></span>

1.  <span data-ttu-id="34760-112">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스의 준비 표에 데이터를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="34760-112">Load data into the staging tables in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>

2.  <span data-ttu-id="34760-113">준비 표의 데이터를 적절한 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 표에 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="34760-113">Load the data from the staging tables into the appropriate [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] tables.</span></span>

     <span data-ttu-id="34760-114">준비 저장 프로시저나 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 를 사용하여 데이터를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="34760-114">You use staging stored procedures or [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] to load the data.</span></span>

> [!NOTE]
>  <span data-ttu-id="34760-115">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]에서는 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 준비 프로세스에 대한 지원이 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34760-115">In [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], support for the [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] staging processes is deprecated.</span></span>

## <a name="deactivating-and-deleting-members"></a><span data-ttu-id="34760-116">멤버 비활성화 및 삭제</span><span class="sxs-lookup"><span data-stu-id="34760-116">Deactivating and Deleting Members</span></span>
 <span data-ttu-id="34760-117">비활성화하면 멤버를 다시 활성화할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34760-117">Deactivating means the member can be reactivated.</span></span> <span data-ttu-id="34760-118">멤버를 다시 활성화하는 경우 계층 및 컬렉션에서 해당 특성 및 멤버 자격이 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="34760-118">If you reactivate a member, its attributes and its membership in hierarchies and collections are restored.</span></span> <span data-ttu-id="34760-119">모든 이전 트랜잭션은 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="34760-119">All previous transactions are intact.</span></span> <span data-ttu-id="34760-120">관리자는 마스터 데이터 관리자의 **버전 관리** 기능 영역에서 비활성화 트랜잭션을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34760-120">Deactivation transactions are visible to administrators in the **Version Management** functional area of the Master Data Manager.</span></span>

 <span data-ttu-id="34760-121">삭제는 멤버를 영구적으로 시스템에서 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="34760-121">Deleting means purging the member from the system permanently.</span></span> <span data-ttu-id="34760-122">멤버의 모든 트랜잭션, 모든 관계 및 모든 특성이 영구적으로 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="34760-122">All transactions for the member, all relationships, and all attributes are permanently deleted.</span></span>

> [!NOTE]
>  <span data-ttu-id="34760-123">준비를 사용하여 멤버를 다시 활성화할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34760-123">You cannot use staging to reactivate members.</span></span> <span data-ttu-id="34760-124">마스터 데이터 관리자에서 수동으로 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34760-124">You must do it manually in the Master Data Manager.</span></span> <span data-ttu-id="34760-125">자세한 내용은 [멤버 또는 컬렉션 다시 활성화&#40;Master Data Services&#41;](reactivate-a-member-or-collection-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="34760-125">For more information, see [Reactivate a Member or Collection &#40;Master Data Services&#41;](reactivate-a-member-or-collection-master-data-services.md).</span></span>
> 
>  <span data-ttu-id="34760-126">준비를 사용하여 컬렉션을 삭제하거나 비활성화할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34760-126">You cannot use staging to delete or deactivate collections.</span></span> <span data-ttu-id="34760-127">컬렉션을 수동으로 비활성화하는 방법에 대한 자세한 내용은 [멤버 또는 컬렉션 삭제&#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="34760-127">For more information on manually deactivating collections, see [Delete a Member or Collection &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md).</span></span>

## <a name="moving-explicit-hierarchy-members"></a><span data-ttu-id="34760-128">명시적 계층 멤버 이동</span><span class="sxs-lookup"><span data-stu-id="34760-128">Moving explicit hierarchy members</span></span>
 <span data-ttu-id="34760-129">명시적 계층에서 멤버 위치를 대량으로 이동할 때 다음을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34760-129">When you move the location of members in explicit hierarchies in bulk, you can designate the following.</span></span>

-   <span data-ttu-id="34760-130">통합 멤버의 부모 자격을 가지는 통합 멤버</span><span class="sxs-lookup"><span data-stu-id="34760-130">A consolidated member as a parent of a consolidated member.</span></span>

-   <span data-ttu-id="34760-131">리프 멤버의 부모 자격을 가지는 통합 멤버</span><span class="sxs-lookup"><span data-stu-id="34760-131">A consolidated member as a parent of a leaf member.</span></span>

-   <span data-ttu-id="34760-132">리프 또는 통합 멤버의 형제 자격을 가지는 리프 멤버</span><span class="sxs-lookup"><span data-stu-id="34760-132">A leaf member as a sibling of a leaf or consolidated member.</span></span>

-   <span data-ttu-id="34760-133">리프 또는 통합 멤버의 형제 자격을 가지는 통합 멤버</span><span class="sxs-lookup"><span data-stu-id="34760-133">A consolidated member as a sibling of a leaf or consolidated member.</span></span>

## <a name="staging-tables-and-stored-procedures"></a><span data-ttu-id="34760-134">준비 표 및 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="34760-134">Staging Tables and Stored Procedures</span></span>
 <span data-ttu-id="34760-135">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스에는 보유한 데이터로 채울 수 있는 다음 유형의 준비 표가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34760-135">The [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database includes the following types of staging tables that you can populate with your  data.</span></span>

-   [<span data-ttu-id="34760-136">리프 멤버 준비 테이블&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="34760-136">Leaf Member Staging Table &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/leaf-member-staging-table-master-data-services.md)

-   [<span data-ttu-id="34760-137">통합 멤버 준비 테이블&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="34760-137">Consolidated Member Staging Table &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/consolidated-member-staging-table-master-data-services.md)

-   [<span data-ttu-id="34760-138">관계 준비 테이블&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="34760-138">Relationship Staging Table &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/relationship-staging-table-master-data-services.md)

 <span data-ttu-id="34760-139">모델의 각 엔터티에 대해 준비 표가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34760-139">For each entity in the model, there is a staging table.</span></span> <span data-ttu-id="34760-140">표 이름은 해당 엔터티 및 리프 멤버 등의 엔터티 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="34760-140">The table name indicates the corresponding entity, and the entity type such as leaf member.</span></span> <span data-ttu-id="34760-141">다음 이미지는 통화, 고객 및 제품 엔터티에 대한 준비 표를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="34760-141">The following image shows the staging tables for the currency, customer, and product entities.</span></span>

 <span data-ttu-id="34760-142">![MDS 데이터베이스의 준비 테이블](../../2014/master-data-services/media/mds-stagingtables.png "MDS 데이터베이스의 준비 테이블")</span><span class="sxs-lookup"><span data-stu-id="34760-142">![Staging Tables in MDS database](../../2014/master-data-services/media/mds-stagingtables.png "Staging Tables in MDS database")</span></span>

 <span data-ttu-id="34760-143">표의 이름은 엔터티를 만들 때 지정되며 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34760-143">The name of the  table is specified when an entity is created and cannot be changed.</span></span> <span data-ttu-id="34760-144">준비 테이블 이름에 _1이나 기타 번호가 포함되면 엔터티 작성 시 해당 이름의 다른 테이블이 이미 있는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="34760-144">If the staging table name contains a _1 or other number, another table of that name already existed when the entity was created.</span></span>

 <span data-ttu-id="34760-145">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 는 다음 유형의 준비 저장 프로시저를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="34760-145">The [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] includes the following types of staging stored procedures.</span></span>

-   <span data-ttu-id="34760-146">stg. udp_ \<name> _Leaf</span><span class="sxs-lookup"><span data-stu-id="34760-146">stg.udp_\<name>_Leaf</span></span>

-   <span data-ttu-id="34760-147">stg. udp_ \<name> _Consolidated</span><span class="sxs-lookup"><span data-stu-id="34760-147">stg.udp_\<name>_Consolidated</span></span>

-   <span data-ttu-id="34760-148">stg. udp_ \<name> _Relationship</span><span class="sxs-lookup"><span data-stu-id="34760-148">stg.udp_\<name>_Relationship</span></span>

 <span data-ttu-id="34760-149">모델의 각 엔터티에는 리프 멤버, 통합 멤버 및 관계 준비 표에 해당하는 3개의 저장 프로시저가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34760-149">For each entity in the model, there are three stored procedures that correspond to the leaf member, consolidated member, and relationship staging tables.</span></span>  <span data-ttu-id="34760-150">다음 이미지는 통화, 고객 및 제품 엔터티에 대한 준비 저장 프로시저를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="34760-150">The following image shows the staging stored procedures for the currency, customer, and product entities.</span></span>

 <span data-ttu-id="34760-151">![MDS 데이터베이스의 저장 프로시저를 준비](../../2014/master-data-services/media/mds-stagingstoredprocedures.png "MDS 데이터베이스의 저장 프로시저를 준비")</span><span class="sxs-lookup"><span data-stu-id="34760-151">![Staging Stored Procedures in MDS database](../../2014/master-data-services/media/mds-stagingstoredprocedures.png "Staging Stored Procedures in MDS database")</span></span>

 <span data-ttu-id="34760-152">저장 프로시저에 대한 자세한 내용은 [준비 저장 프로시저&#40;Master Data Services&#41;](../../2014/master-data-services/staging-stored-procedure-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="34760-152">For more information on the stored procedures, see [Staging Stored Procedure &#40;Master Data Services&#41;](../../2014/master-data-services/staging-stored-procedure-master-data-services.md).</span></span>

## <a name="logging-transactions"></a><span data-ttu-id="34760-153">트랜잭션 로깅</span><span class="sxs-lookup"><span data-stu-id="34760-153">Logging Transactions</span></span>
 <span data-ttu-id="34760-154">데이터 또는 관계를 가져오거나 업데이트할 때 발생하는 모든 트랜잭션을 로깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34760-154">All transactions that occur when data or relationships are imported or updated can be logged.</span></span> <span data-ttu-id="34760-155">이러한 로깅은 저장 프로시저 옵션을 통해 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="34760-155">An option in the stored procedure allows this logging.</span></span> <span data-ttu-id="34760-156">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]를 사용하여 준비 프로세스를 시작하는 경우에는 로깅이 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34760-156">If you initiate the staging process using [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], no logging occurs.</span></span>

 <span data-ttu-id="34760-157">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]의 **준비 트랜잭션 기록** 설정은 이 데이터 준비 방법에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34760-157">In [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], the **Log staging transactions** setting does not apply to this method of staging data.</span></span>

## <a name="related-content"></a><span data-ttu-id="34760-158">관련 내용</span><span class="sxs-lookup"><span data-stu-id="34760-158">Related Content</span></span>

-   [<span data-ttu-id="34760-159">유효성 검사&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="34760-159">Validation &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validation-master-data-services.md)

-   [<span data-ttu-id="34760-160">비즈니스 규칙&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="34760-160">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)


