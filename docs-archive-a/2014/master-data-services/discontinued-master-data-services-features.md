---
title: SQL Server 2014의 지원 되지 않는 MDS(Master Data Services) 기능 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 3236cce0-cfd9-43f8-8be3-e8c8dff8f162
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 595b8bf9829ee57ff0d3bee1a82e527876ecc4f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661685"
---
# <a name="discontinued-master-data-services-features-in-sql-server-2014"></a><span data-ttu-id="8c9b0-102">SQL Server 2014에서 지원되지 않는 MDS(Master Data Services) 기능</span><span class="sxs-lookup"><span data-stu-id="8c9b0-102">Discontinued Master Data Services Features in SQL Server 2014</span></span>
  <span data-ttu-id="8c9b0-103">이 항목에서는 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 에서 더 이상 사용할 수 없는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]기능에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-103">This topic describes [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] features that are no longer available in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="sssql14-discontinued-features"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] <span data-ttu-id="8c9b0-104">지원되지 않는 기능</span><span class="sxs-lookup"><span data-stu-id="8c9b0-104">Discontinued Features</span></span>  
 <span data-ttu-id="8c9b0-105">이 릴리스에서는 지원이 중단된 기능이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-105">There are no discontinued features in this release.</span></span>  
  
## <a name="sssql11-discontinued-features"></a>[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="8c9b0-106">지원되지 않는 기능</span><span class="sxs-lookup"><span data-stu-id="8c9b0-106">Discontinued Features</span></span>  
  
### <a name="security"></a><span data-ttu-id="8c9b0-107">보안</span><span class="sxs-lookup"><span data-stu-id="8c9b0-107">Security</span></span>  
 <span data-ttu-id="8c9b0-108">보안을 보다 쉽게 지정하기 위해 더 이상 파생 계층, 명시적 계층 및 특성 그룹 개체에 모델 개체 권한을 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-108">To make assigning security easier, you can no longer assign model object permissions to the Derived Hierarchy, Explicit Hierarchy, and Attribute Group objects.</span></span>  
  
-   <span data-ttu-id="8c9b0-109">파생 계층 권한은 이제 모델을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-109">Derived hierarchy permissions are now based on the model.</span></span> <span data-ttu-id="8c9b0-110">예를 들어 사용자에 게 파생 계층에 대 한 사용 권한을 부여 하려면 모델 개체에 **업데이트** 를 할당 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-110">For example, if you want a user to have permission to a derived hierarchy, you must assign **Update** to the model object.</span></span> <span data-ttu-id="8c9b0-111">그런 다음 사용자에 게 액세스 권한을 부여 하지 않으려는 엔터티에 대 한 **거부** 액세스를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-111">Then you can assign **Deny** access to any entities you don't want the user to have access to.</span></span>  
  
-   <span data-ttu-id="8c9b0-112">명시적 계층 권한은 이제 엔터티를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-112">Explicit hierarchy permissions are now based on the entity.</span></span> <span data-ttu-id="8c9b0-113">예를 들어 사용자가 계정 엔터티에 대 한 **업데이트** 권한을가지고 있으면 엔터티에 대 한 모든 명시적 계층을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-113">For example, if the user has **Update** permissions to an Account entity, then all explicit hierarchies for the entity will be updateable.</span></span>  
  
-   <span data-ttu-id="8c9b0-114">특성 그룹 권한은 더 이상 **사용자 및 그룹 권한** 기능 영역에서 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-114">Attribute group permissions can no longer be assigned in the **User and Group Permissions** functional area.</span></span> <span data-ttu-id="8c9b0-115">대신 특성 그룹이 생성 되는 **시스템 관리** 기능 영역에서 사용자 및 그룹에 특성 그룹에 대 한 **업데이트** 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-115">Instead, in the **System Administration** functional area where attribute groups are created, users and groups can be given **Update** permission to attribute groups.</span></span> <span data-ttu-id="8c9b0-116">특성 그룹에 대 한 **읽기 전용** 권한을 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-116">**Read-only** permission to attribute groups is no longer available.</span></span>  
  
### <a name="staging-process"></a><span data-ttu-id="8c9b0-117">준비 프로세스</span><span class="sxs-lookup"><span data-stu-id="8c9b0-117">Staging Process</span></span>  
 <span data-ttu-id="8c9b0-118">새 준비 프로세스를 사용하여 다음을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-118">You cannot use the new staging process to:</span></span>  
  
-   <span data-ttu-id="8c9b0-119">컬렉션 만들기 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="8c9b0-119">Create or delete collections.</span></span>  
  
-   <span data-ttu-id="8c9b0-120">컬렉션에 멤버 추가 또는 컬렉션에서 멤버 제거</span><span class="sxs-lookup"><span data-stu-id="8c9b0-120">Add members to or remove members from collections.</span></span>  
  
-   <span data-ttu-id="8c9b0-121">멤버 또는 컬렉션 다시 활성화</span><span class="sxs-lookup"><span data-stu-id="8c9b0-121">Reactivate members and collections.</span></span>  
  
 <span data-ttu-id="8c9b0-122">[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 준비 프로세스를 사용하여 컬렉션 작업을 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-122">You can use the [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] staging process to work with collections.</span></span>  
  
### <a name="model-deployment-wizard"></a><span data-ttu-id="8c9b0-123">모델 배포 마법사</span><span class="sxs-lookup"><span data-stu-id="8c9b0-123">Model Deployment Wizard</span></span>  
 <span data-ttu-id="8c9b0-124">데이터를 포함하는 패키지는 더 이상 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 웹 애플리케이션에서 마법사를 사용하여 만들고 배포할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-124">Packages that contain data can no longer be created and deployed by using the wizard in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application.</span></span> <span data-ttu-id="8c9b0-125">대신 새로운 명령줄 유틸리티를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-125">A new command line utility can be used instead.</span></span> <span data-ttu-id="8c9b0-126">자세한 내용은 [모델 배포&#40;Master Data Services&#41;](deploying-models-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-126">For more information, see [Deploying Models &#40;Master Data Services&#41;](deploying-models-master-data-services.md).</span></span>  
  
 <span data-ttu-id="8c9b0-127">데이터를 포함하지 않는 패키지는 계속해서 마법사를 사용하여 만들고 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-127">The wizard can still be used to create and deploy packages that do not contain data.</span></span>  
  
 <span data-ttu-id="8c9b0-128">또한 패키지는 해당 패키지를 만드는 데 사용한 버전의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에만 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-128">In addition, packages can be deployed to the edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] they were created in only.</span></span> <span data-ttu-id="8c9b0-129">따라서 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 에서 만든 패키지는 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]에 배포할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-129">This means that packages created in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] cannot be deployed to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span> <span data-ttu-id="8c9b0-130">먼저 패키지를 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 환경에 배포한 다음 데이터베이스를 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]로 업그레이드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-130">You must deploy the package to a [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] environment and then upgrade the database to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span>  
  
### <a name="code-generation-business-rules"></a><span data-ttu-id="8c9b0-131">코드 생성 비즈니스 규칙</span><span class="sxs-lookup"><span data-stu-id="8c9b0-131">Code Generation Business Rules</span></span>  
 <span data-ttu-id="8c9b0-132">코드 특성 값을 자동으로 생성하는 비즈니스 규칙이 이제 다르게 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-132">Business rules that automatically generate values for the Code attribute are now administered differently.</span></span> <span data-ttu-id="8c9b0-133">이전에는 코드 특성에 대 한 값을 생성 하기 위해 **비즈니스 규칙**의 **시스템 관리** 기능 영역에서 **생성 된 값 동작에 기본 특성** 을 사용 했습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-133">Previously, to generate values for the Code attribute, you used the **Default attribute to a generated value** action in the **System Administration** functional area under **Business Rules**.</span></span> <span data-ttu-id="8c9b0-134">이제 **시스템 관리**에서 자동으로 생성 된 코드 값을 사용 하도록 엔터티를 편집 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-134">Now, in **System Administration**, you must edit the entity to enable automatically-generated Code values.</span></span> <span data-ttu-id="8c9b0-135">자세한 내용은 [MDS(Master Data Services)&#41;&#40;자동 코드 만들기 ](automatic-code-creation-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-135">For more information, see [Automatic Code Creation &#40;Master Data Services&#41;](automatic-code-creation-master-data-services.md).</span></span>  
  
 <span data-ttu-id="8c9b0-136">이 유형의 규칙을 포함하는 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 모델 배포 패키지가 있는 경우 데이터베이스를 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]로 업그레이드할 때 비즈니스 규칙은 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-136">If you have a [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] model deployment package that contains a rule of this type, when you upgrade the database to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], the business rule will be excluded.</span></span>  
  
### <a name="bulk-updates-and-exporting"></a><span data-ttu-id="8c9b0-137">대량 업데이트 및 내보내기</span><span class="sxs-lookup"><span data-stu-id="8c9b0-137">Bulk Updates and Exporting</span></span>  
 <span data-ttu-id="8c9b0-138">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 웹 애플리케이션에서는 더 이상 여러 멤버에 대한 특성 값을 대량으로 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-138">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application, you can no longer update attribute values for multiple members in bulk.</span></span> <span data-ttu-id="8c9b0-139">대량 업데이트를 수행 하려면 준비 프로세스 또는를 사용 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-139">To do bulk updates, use the staging process or the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].</span></span>  
  
 <span data-ttu-id="8c9b0-140">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 웹 애플리케이션에서는 더 이상 멤버를 Excel로 내보낼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-140">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application, you can no longer export members to Excel.</span></span> <span data-ttu-id="8c9b0-141">Excel에서 멤버로 작업 하려면를 사용 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-141">To work with members in Excel, use the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="8c9b0-142">의</span><span class="sxs-lookup"><span data-stu-id="8c9b0-142">Transactions</span></span>  
 <span data-ttu-id="8c9b0-143">사용자는 **탐색기** 기능 영역에서 더 이상 자신의 트랜잭션을 되돌릴 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-143">In the **Explorer** functional area, users can no longer revert their own transactions.</span></span> <span data-ttu-id="8c9b0-144">이전에는 사용자가 **탐색기**에서 데이터에 대 한 변경 내용을 되돌릴 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-144">Previously, users could revert changes they made to data in **Explorer**.</span></span> <span data-ttu-id="8c9b0-145">관리자는 **버전 관리** 기능 영역에서 모든 사용자에 대 한 트랜잭션을 되돌릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-145">Administrators can still revert transactions for all users in the **Version Management** functional area.</span></span>  
  
 <span data-ttu-id="8c9b0-146">주석은 이제 영구적이며 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-146">Annotations are now permanent and cannot be deleted.</span></span> <span data-ttu-id="8c9b0-147">이전에는 주석이 트랜잭션으로 간주되어 트랜잭션을 되돌리면 삭제할 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-147">Previously, annotations were considered transactions and could be deleted by reverting the transaction.</span></span>  
  
### <a name="web-service"></a><span data-ttu-id="8c9b0-148">웹 서비스</span><span class="sxs-lookup"><span data-stu-id="8c9b0-148">Web Service</span></span>  
 <span data-ttu-id="8c9b0-149">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 웹 서비스는 이제 Silverlight의 요구에 따라 자동으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-149">The [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] web service is now enabled automatically, as required by Silverlight.</span></span> <span data-ttu-id="8c9b0-150">이전에는 웹 서비스를 수동으로 설정해야 했습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-150">Previously, the web service had to be enabled manually.</span></span>  
  
### <a name="powershell-cmdlets"></a><span data-ttu-id="8c9b0-151">PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8c9b0-151">PowerShell Cmdlets</span></span>  
 <span data-ttu-id="8c9b0-152">MDS에는 PowerShell cmdlet이 더 이상 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9b0-152">MDS no longer includes PowerShell cmdlets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c9b0-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8c9b0-153">See Also</span></span>  
 [<span data-ttu-id="8c9b0-154">SQL Server 2014에서 사용되지 않는 MDS(Master Data Services) 기능</span><span class="sxs-lookup"><span data-stu-id="8c9b0-154">Deprecated Master Data Services Features in SQL Server 2014</span></span>](deprecated-master-data-services-features.md)  
  
  
