---
title: 역할 만들기 및 관리 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.rolemanager.f1
- sql12.asvs.bidtoolset.roledb.f1
ms.assetid: e23d27a8-e968-4082-9dbe-963fc724b5d9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 335e0e311d97ea452449cd0c5d6550f6dbcca4f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647292"
---
# <a name="create-and-manage-roles-ssas-tabular"></a><span data-ttu-id="b4df3-102">역할 만들기 및 관리(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="b4df3-102">Create and Manage Roles (SSAS Tabular)</span></span>
  <span data-ttu-id="b4df3-103">테이블 형식 모델에서 역할은 모델에 대한 멤버 권한을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-103">Roles, in tabular models, define member permissions for a model.</span></span> <span data-ttu-id="b4df3-104">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 역할 관리자 대화 상자를 사용하여 모델 프로젝트에 대해 역할을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-104">Roles are defined for a model project by using the Role Manager dialog box in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="b4df3-105">모델을 배포할 때 데이터베이스 관리자는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 역할을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-105">When a model is deployed, database administrators can manage roles by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="b4df3-106">이 항목의 태스크에서는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 역할 관리자 대화 상자를 사용하여 모델 제작 중에 역할을 만들고 관리하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-106">The tasks in this topic describe how to create and manage roles during model authoring by using the Role Manager dialog box in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="b4df3-107">배포된 model 데이터베이스에서 역할을 관리하는 방법은 [테이블 형식 모델 역할&#40;SSAS 테이블 형식&#41;](roles-ssas-tabular.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b4df3-107">For information about managing roles in a deployed model database, see [Tabular Model Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="b4df3-108">작업</span><span class="sxs-lookup"><span data-stu-id="b4df3-108">Tasks</span></span>  
 <span data-ttu-id="b4df3-109">역할을 만들고, 편집, 복사 및 삭제하려면 **역할 관리자** 대화 상자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-109">To create, edit, copy, and delete roles, you will use the **Role Manager** dialog box.</span></span> <span data-ttu-id="b4df3-110">**역할 관리자** 대화 상자를 보려면 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 **모델** 메뉴를 클릭한 다음 **역할 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-110">To view the **Role Manager** dialog box, in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Role Manager**.</span></span>  
  
###  <a name="to-create-a-new-role"></a><a name="bkmk_new_role"></a><span data-ttu-id="b4df3-111">새 역할을 만들려면</span><span class="sxs-lookup"><span data-stu-id="b4df3-111">To create a new role</span></span>  
  
1.  <span data-ttu-id="b4df3-112">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 **모델** 메뉴를 클릭한 다음 **역할 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-112">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Role Manager**.</span></span>  
  
2.  <span data-ttu-id="b4df3-113">**역할 관리자** 대화 상자에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-113">In the **Role Manager** dialog box, click **New**.</span></span>  
  
     <span data-ttu-id="b4df3-114">강조 표시된 새 역할이 역할 목록에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-114">A new highlighted role is added to the Roles list.</span></span>  
  
3.  <span data-ttu-id="b4df3-115">**역할** 목록의 **이름** 필드에 역할의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-115">In the **Roles** list, in the **Name** field, type a name for the role.</span></span>  
  
     <span data-ttu-id="b4df3-116">기본적으로 기본 역할의 이름은 새 역할을 만들 때마다 증분식으로 번호가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-116">By default, the name of the default role will be incrementally numbered for each new role.</span></span> <span data-ttu-id="b4df3-117">따라서 재무 관리자 또는 인적 자원 전문가와 같이 멤버 유형을 분명하게 식별하는 이름을 입력하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-117">It is recommended you type a name that clearly identifies the member type, for example, Finance Managers or Human Resources Specialists.</span></span>  
  
4.  <span data-ttu-id="b4df3-118">**사용 권한** 필드에서 아래쪽 화살표를 클릭하고 다음 사용 권한 유형 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-118">In the **Permissions** field, click the down arrow and then select one of the following permission types:</span></span>  
  
    |<span data-ttu-id="b4df3-119">사용 권한</span><span class="sxs-lookup"><span data-stu-id="b4df3-119">Permission</span></span>|<span data-ttu-id="b4df3-120">Description</span><span class="sxs-lookup"><span data-stu-id="b4df3-120">Description</span></span>|  
    |----------------|-----------------|  
    |<span data-ttu-id="b4df3-121">**없음**</span><span class="sxs-lookup"><span data-stu-id="b4df3-121">**None**</span></span>|<span data-ttu-id="b4df3-122">멤버는 모델 스키마를 수정할 수 없으며 데이터를 쿼리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-122">Members cannot make any modifications to the model schema and cannot query data.</span></span>|  
    |<span data-ttu-id="b4df3-123">**읽기**</span><span class="sxs-lookup"><span data-stu-id="b4df3-123">**Read**</span></span>|<span data-ttu-id="b4df3-124">멤버는 행 필터를 기반으로 데이터를 쿼리할 수 있지만 모델 스키마를 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-124">Members are allowed to query data (based on row filters) but cannot make any changes to the model schema.</span></span>|  
    |<span data-ttu-id="b4df3-125">**읽기 및 처리**</span><span class="sxs-lookup"><span data-stu-id="b4df3-125">**Read and Process**</span></span>|<span data-ttu-id="b4df3-126">멤버는 행 수준 필터를 기반으로 데이터를 쿼리하고 처리 및 모두 처리 작업을 실행할 수 있지만 모델 스키마를 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-126">Members are allowed to query data (based on row-level filters) and run Process and Process All operations, but cannot make any changes to the model schema.</span></span>|  
    |<span data-ttu-id="b4df3-127">**Process**</span><span class="sxs-lookup"><span data-stu-id="b4df3-127">**Process**</span></span>|<span data-ttu-id="b4df3-128">멤버는 처리 및 모두 처리 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-128">Members can run Process and Process All operations.</span></span> <span data-ttu-id="b4df3-129">모델 스키마를 수정할 수 없으며 데이터를 쿼리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-129">Cannot modify the model schema and cannot query data.</span></span>|  
    |<span data-ttu-id="b4df3-130">**관리자**</span><span class="sxs-lookup"><span data-stu-id="b4df3-130">**Administrator**</span></span>|<span data-ttu-id="b4df3-131">멤버는 모델 스키마를 수정할 수 있으며 모든 데이터를 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-131">Members can make modifications to the model schema and can query all data.</span></span>|  
  
5.  <span data-ttu-id="b4df3-132">역할에 대한 설명을 입력하려면 **설명** 필드를 클릭한 다음 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-132">To enter a description for the role, click the **Description** field, and then type a description.</span></span>  
  
6.  <span data-ttu-id="b4df3-133">만들고 있는 역할에 읽기 또는 읽기 및 처리 권한이 있는 경우 DAX 수식을 사용하여 행 필터를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-133">If the role you are creating has Read or Read and Process permission, you can add row filters using a DAX formula.</span></span> <span data-ttu-id="b4df3-134">행 필터를 추가하려면 **행 필터** 탭을 클릭하고 테이블을 선택한 다음 **DAX 필터** 필드를 클릭하고 DAX 수식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-134">To add row filters, click the **Row Filters** tab, then select a table, then click the **DAX Filter** field, and then type a DAX formula.</span></span>  
  
7.  <span data-ttu-id="b4df3-135">멤버를 역할에 추가하려면 **멤버** 탭을 클릭한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-135">To add members to the role, click the **Members** tab, and then click **Add**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b4df3-136">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 역할 멤버를 배포된 모델에 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-136">Role members can also be added to a deployed model by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="b4df3-137">자세한 내용은 [SSMS를 사용하여 역할 관리&#40;SSAS 테이블 형식&#41;](manage-roles-by-using-ssms-ssas-tabular.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b4df3-137">For more information, see [Manage Roles by using SSMS &#40;SSAS Tabular&#41;](manage-roles-by-using-ssms-ssas-tabular.md).</span></span>  
  
8.  <span data-ttu-id="b4df3-138">**사용자 또는 그룹 선택** 대화 상자에서 Windows 사용자 또는 Windows 그룹 개체를 멤버로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-138">In the **Select Users or Groups** dialog box, enter Windows user or Windows group objects as members.</span></span>  
  
9. <span data-ttu-id="b4df3-139">**Ok**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4df3-139">Click **Ok**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4df3-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b4df3-140">See Also</span></span>  
 <span data-ttu-id="b4df3-141">[SSAS 테이블 형식&#41;역할 &#40;](roles-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="b4df3-141">[Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md) </span></span>  
 <span data-ttu-id="b4df3-142">[SSAS 테이블 형식&#41;&#40;큐브 뷰](perspectives-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="b4df3-142">[Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md) </span></span>  
 <span data-ttu-id="b4df3-143">[Excel에서 분석 &#40;SSAS 테이블 형식&#41;](analyze-in-excel-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="b4df3-143">[Analyze in Excel &#40;SSAS Tabular&#41;](analyze-in-excel-ssas-tabular.md) </span></span>  
 <span data-ttu-id="b4df3-144">[DAX&#41;&#40;USERNAME 함수](/dax/username-function-dax) </span><span class="sxs-lookup"><span data-stu-id="b4df3-144">[USERNAME Function &#40;DAX&#41;](/dax/username-function-dax) </span></span>  
 [<span data-ttu-id="b4df3-145">CUSTOMDATA 함수 &#40;DAX&#41;</span><span class="sxs-lookup"><span data-stu-id="b4df3-145">CUSTOMDATA Function &#40;DAX&#41;</span></span>](/dax/customdata-function-dax)  
  
  
