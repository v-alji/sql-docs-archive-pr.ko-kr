---
title: 역할 및 사용 권한 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- security [Analysis Services], about security
- security [Analysis Services - multidimensional data], about security
ms.assetid: bb885447-868b-4686-853c-8241f63d4370
author: minewiskan
ms.author: owend
ms.openlocfilehash: d6595d931b2c2760e5fd3013ff6bec88f85106d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743543"
---
# <a name="roles-and-permissions-analysis-services"></a><span data-ttu-id="e9c53-102">역할 및 권한(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="e9c53-102">Roles and Permissions (Analysis Services)</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="e9c53-103">는 작업, 개체 및 데이터에 대한 액세스 권한을 부여하는 역할 기준 권한 부여 모델을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e9c53-103">provides a role-based authorization model that grants access to operations, objects, and data.</span></span> <span data-ttu-id="e9c53-104">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스 또는 데이터베이스에 액세스하는 모든 사용자는 역할 컨텍스트 내에서 이를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9c53-104">All users who access an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance or database must do so within the context of a role.</span></span>  
  
 <span data-ttu-id="e9c53-105">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 시스템 관리자는 **서버 관리자 역할** 에 서버의 작업에 무제한 액세스할 수 있는 멤버 자격을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9c53-105">As an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] system administrator, you are in charge of granting membership to the **server administrator role** that conveys unrestricted access to operations on the server.</span></span> <span data-ttu-id="e9c53-106">이 역할은 사용 권한이 고정되며 사용자 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e9c53-106">This role has fixed permissions and cannot be customized.</span></span> <span data-ttu-id="e9c53-107">기본적으로 로컬 관리자 그룹의 멤버는 자동으로 Analysis Services 시스템 관리자가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9c53-107">By default, members of the local Administrators group are automatically Analysis Services system administrators.</span></span>  
  
 <span data-ttu-id="e9c53-108">데이터를 쿼리하거나 처리하는 관리 권한이 없는 사용자에게는 **데이터베이스 역할**을 통한 액세스 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="e9c53-108">Non-administrative users who query or process data are granted access through **database roles**.</span></span> <span data-ttu-id="e9c53-109">시스템 관리자 및 데이터베이스 관리자는 특정 데이터베이스 내에 서로 다른 수준의 액세스를 나타내는 역할을 만든 다음 액세스가 필요한 모든 사용자에게 멤버 자격을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9c53-109">Both system administrators and database administrators can create the roles that describe different levels of access within a given database, and then assign membership to every user who requires access.</span></span> <span data-ttu-id="e9c53-110">각 역할에는 특정 데이터베이스 내의 개체 및 작업에 액세스할 수 있는 사용자 지정된 권한 집합을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="e9c53-110">Each role has a customized set of permissions for accessing objects and operations within a particular database.</span></span> <span data-ttu-id="e9c53-111">데이터베이스, 큐브 및 차원(큐브 뷰 제외)과 같은 내부 개체, 행 수준에서 사용 권한을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9c53-111">You can assign permissions at these levels: database, interior objects such as cubes and dimensions (but not perspectives), and rows.</span></span>  
  
 <span data-ttu-id="e9c53-112">역할을 만들고 별도 작업으로 멤버 자격을 지정하는 것이 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="e9c53-112">It is common practice to create roles and assign membership as separate operations.</span></span> <span data-ttu-id="e9c53-113">대부분의 경우 모델 디자이너는 디자인 단계에서 역할을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e9c53-113">Often, the model designer adds roles during the design phase.</span></span> <span data-ttu-id="e9c53-114">이렇게 하면 모든 역할 정의가 모델을 정의하는 프로젝트 파일에 반영됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9c53-114">This way, all role definitions are reflected in the project files that define the model.</span></span> <span data-ttu-id="e9c53-115">일반적으로 데이터베이스는, 독립적인 작업으로 개발, 테스트, 실행할 수 있는 스크립트를 만드는 데이터베이스 관리자가 프로덕션 환경으로 전환하기 때문에 역할 멤버 자격은 나중에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9c53-115">Role membership is typically rolled out later as the database moves into production, usually by database administrators who create scripts that can be developed, tested, and run as an independent operation.</span></span>  
  
 <span data-ttu-id="e9c53-116">모든 권한 부여는 유효한 Windows 사용자 ID를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9c53-116">All authorization is predicated on a valid Windows user identity.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="e9c53-117">는 Windows 인증만을 사용하여 사용자 ID를 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="e9c53-117">uses Windows authentication exclusively to authenticate user identities.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="e9c53-118">는 독점적인 인증 방법을 제공 하지 않습니다. [Analysis Services에서 지 원하는 인증 방법](../instances/authentication-methodologies-supported-by-analysis-services.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e9c53-118">provides no proprietary authentication method.See [Authentication methodologies supported by Analysis Services](../instances/authentication-methodologies-supported-by-analysis-services.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e9c53-119">데이터베이스의 모든 역할에서 각 Windows 사용자 및 그룹에 대해 권한은 부가적입니다.</span><span class="sxs-lookup"><span data-stu-id="e9c53-119">Permissions are additive for each Windows user or group, across all roles in the database.</span></span> <span data-ttu-id="e9c53-120">한 역할은 사용자나 그룹에게 특정 태스크를 수행하거나 데이터를 볼 수 있는 사용 권한을 부여하지 않지만 다른 역할이 이 사용자나 그룹에게 이러한 사용 권한을 부여하는 경우 해당 사용자나 그룹은 작업을 수행하거나 데이터를 볼 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9c53-120">If one role denies a user or group permission to perform certain tasks or view certain data, but another role grants this permission to that user or group, the user or group will have permission to perform the task or view the data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e9c53-121">단원 내용</span><span class="sxs-lookup"><span data-stu-id="e9c53-121">In this section</span></span>  
  
-   [<span data-ttu-id="e9c53-122">개체 및 작업에 대한 액세스 승인&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e9c53-122">Authorizing access to objects and operations &#40;Analysis Services&#41;</span></span>](authorizing-access-to-objects-and-operations-analysis-services.md)  
  
-   [<span data-ttu-id="e9c53-123">데이터베이스 권한 부여&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e9c53-123">Grant database permissions &#40;Analysis Services&#41;</span></span>](grant-database-permissions-analysis-services.md)  
  
-   [<span data-ttu-id="e9c53-124">큐브 또는 모델 권한 부여&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e9c53-124">Grant cube or model permissions &#40;Analysis Services&#41;</span></span>](grant-cube-or-model-permissions-analysis-services.md)  
  
-   [<span data-ttu-id="e9c53-125">처리 권한 부여&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e9c53-125">Grant process permissions &#40;Analysis Services&#41;</span></span>](grant-process-permissions-analysis-services.md)  
  
-   [<span data-ttu-id="e9c53-126">개체 메타데이터에 대한 정의 읽기 권한 부여&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e9c53-126">Grant read definition permissions on object metadata &#40;Analysis Services&#41;</span></span>](grant-read-definition-permissions-on-object-metadata-analysis-services.md)  
  
-   [<span data-ttu-id="e9c53-127">데이터 원본 개체에 대한 권한 부여&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e9c53-127">Grant permissions on a data source object &#40;Analysis Services&#41;</span></span>](grant-permissions-on-a-data-source-object-analysis-services.md)  
  
-   [<span data-ttu-id="e9c53-128">데이터 마이닝 구조 및 모델에 대한 권한 부여&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e9c53-128">Grant permissions on data mining structures and models &#40;Analysis Services&#41;</span></span>](grant-permissions-on-data-mining-structures-and-models-analysis-services.md)  
  
-   [<span data-ttu-id="e9c53-129">차원에 대한 권한 부여&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e9c53-129">Grant permissions on a dimension &#40;Analysis Services&#41;</span></span>](grant-permissions-on-a-dimension-analysis-services.md)  
  
-   [<span data-ttu-id="e9c53-130">차원 데이터에 대한 사용자 지정 액세스 권한 부여&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e9c53-130">Grant custom access to dimension data &#40;Analysis Services&#41;</span></span>](grant-custom-access-to-dimension-data-analysis-services.md)  
  
-   [<span data-ttu-id="e9c53-131">셀 데이터에 대한 사용자 지정 액세스 권한 부여&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e9c53-131">Grant custom access to cell data &#40;Analysis Services&#41;</span></span>](grant-custom-access-to-cell-data-analysis-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="e9c53-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e9c53-132">See Also</span></span>  
 [<span data-ttu-id="e9c53-133">역할 만들기 및 관리&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="e9c53-133">Create and Manage Roles &#40;SSAS Tabular&#41;</span></span>](../tabular-models/roles-ssas-tabular.md)  
  
  
