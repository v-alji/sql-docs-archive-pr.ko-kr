---
title: SSMS를 사용 하 여 역할 관리 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 652faac0-1cfc-438b-8119-2f4b090a2381
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4ee34d5e75d5d4ce3679d46d29af3215852d2bbe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728804"
---
# <a name="manage-roles-by-using-ssms-ssas-tabular"></a><span data-ttu-id="6f06a-102">SSMS를 사용하여 역할 관리(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="6f06a-102">Manage Roles by using SSMS (SSAS Tabular)</span></span>
  <span data-ttu-id="6f06a-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 배포된 테이블 형식 모델에 대한 역할을 생성, 편집 및 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f06a-103">You can create, edit, and manage roles for a deployed tabular model by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="6f06a-104">이 항목의 태스크:</span><span class="sxs-lookup"><span data-stu-id="6f06a-104">Tasks in this topic:</span></span>  
  
-   [<span data-ttu-id="6f06a-105">새 역할을 만들려면</span><span class="sxs-lookup"><span data-stu-id="6f06a-105">To create a new role</span></span>](#bkmk_new_role)  
  
-   [<span data-ttu-id="6f06a-106">역할 복사</span><span class="sxs-lookup"><span data-stu-id="6f06a-106">To copy a role</span></span>](#bkmk_copy_role)  
  
-   [<span data-ttu-id="6f06a-107">역할을 편집 하려면</span><span class="sxs-lookup"><span data-stu-id="6f06a-107">To edit a role</span></span>](#bkmk_edit_role)  
  
-   [<span data-ttu-id="6f06a-108">역할을 삭제 하려면</span><span class="sxs-lookup"><span data-stu-id="6f06a-108">To delete a role</span></span>](#bkmk_deletet_role)  
  
> [!CAUTION]  
>  <span data-ttu-id="6f06a-109">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 에서 역할 관리자를 사용하여 정의한 역할로 테이블 형식 모델 프로젝트를 다시 배포하면 배포된 테이블 형식 모델에 정의된 역할을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="6f06a-109">Re-deploying a tabular model project with roles defined by using Role Manager in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] will overwrite roles defined in a deployed tabular model.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="6f06a-110">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 모델 프로젝트가 열려 있는 동안 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 를 사용하여 테이블 형식 모델 작업 영역 데이터베이스를 관리하면 Model.bim 파일이 손상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f06a-110">Using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to manage a tabular model workspace database while the model project is open in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] may cause the Model.bim file to become corrupted.</span></span> <span data-ttu-id="6f06a-111">테이블 형식 모델 작업 영역 데이터베이스에 대한 역할을 만들고 관리하는 경우 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 역할 관리자를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="6f06a-111">When creating and managing roles for a tabular model workspace database, use Role Manager in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
###  <a name="to-create-a-new-role"></a><a name="bkmk_new_role"></a><span data-ttu-id="6f06a-112">새 역할을 만들려면</span><span class="sxs-lookup"><span data-stu-id="6f06a-112">To create a new role</span></span>  
  
1.  <span data-ttu-id="6f06a-113">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 새 역할을 만들 테이블 형식 model 데이터베이스를 확장하고 **역할**을 마우스 오른쪽 단추로 클릭한 다음 **새 역할**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f06a-113">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the tabular model database for which you want to create a new role, then right click on **Roles**, and then click **New Role**.</span></span>  
  
2.  <span data-ttu-id="6f06a-114">**역할 만들기** 대화 상자의 페이지 선택 창에서 **일반**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f06a-114">In the **Create Role** dialog box, in the Select a page window, click **General**.</span></span>  
  
3.  <span data-ttu-id="6f06a-115">일반 설정 창의 **이름** 필드에 역할의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6f06a-115">In the general settings window, in the **Name** field, type a name for the role.</span></span>  
  
     <span data-ttu-id="6f06a-116">기본적으로 기본 역할의 이름은 새 역할을 만들 때마다 증분식으로 번호가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f06a-116">By default, the name of the default role will be incrementally numbered for each new role.</span></span> <span data-ttu-id="6f06a-117">따라서 재무 관리자 또는 인적 자원 전문가와 같이 멤버 유형을 분명하게 식별하는 이름을 입력하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6f06a-117">It is recommended you type a name that clearly identifies the member type, for example, Finance Managers or Human Resources Specialists.</span></span>  
  
4.  <span data-ttu-id="6f06a-118">**이 역할에 대한 데이터베이스 권한 설정**에서 다음 사용 권한 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f06a-118">In **Set the database permissions for this role**, select one of the following permissions options:</span></span>  
  
    |<span data-ttu-id="6f06a-119">사용 권한</span><span class="sxs-lookup"><span data-stu-id="6f06a-119">Permission</span></span>|<span data-ttu-id="6f06a-120">Description</span><span class="sxs-lookup"><span data-stu-id="6f06a-120">Description</span></span>|  
    |----------------|-----------------|  
    |<span data-ttu-id="6f06a-121">**모든 권한(관리자)**</span><span class="sxs-lookup"><span data-stu-id="6f06a-121">**Full control (Administrator)**</span></span>|<span data-ttu-id="6f06a-122">멤버는 모델 스키마를 수정할 수 있으며 모든 데이터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f06a-122">Members can make modifications to the model schema and can view all data.</span></span>|  
    |<span data-ttu-id="6f06a-123">**Process Database**</span><span class="sxs-lookup"><span data-stu-id="6f06a-123">**Process database**</span></span>|<span data-ttu-id="6f06a-124">멤버는 처리 및 모두 처리 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f06a-124">Members can run Process and Process All operations.</span></span> <span data-ttu-id="6f06a-125">모델 스키마를 수정할 수 없으며 데이터를 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6f06a-125">Cannot modify the model schema and cannot view data.</span></span>|  
    |<span data-ttu-id="6f06a-126">**읽기**</span><span class="sxs-lookup"><span data-stu-id="6f06a-126">**Read**</span></span>|<span data-ttu-id="6f06a-127">멤버는 행 필터를 기반으로 데이터를 볼 수 있지만 모델 스키마를 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6f06a-127">Members are allowed to view data (based on row filters) but cannot make any changes to the model schema.</span></span>|  
  
5.  <span data-ttu-id="6f06a-128">**역할 만들기** 대화 상자의 페이지 선택 창에서 **멤버 자격**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f06a-128">In the **Create Role** dialog box, in the Select a page window, click **Membership**.</span></span>  
  
6.  <span data-ttu-id="6f06a-129">**멤버 자격 설정 창에서 추가**를 클릭한 다음 **사용자 또는 그룹 선택** 대화 상자에서 멤버로 추가할 Windows 사용자 또는 그룹을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6f06a-129">In the membership settings window, click **Add**, and then in the **Select Users or Groups** dialog box, add the Windows users or groups you want to add as members.</span></span>  
  
7.  <span data-ttu-id="6f06a-130">만들고 있는 역할에 읽기 권한이 있는 경우 DAX 수식을 사용하여 테이블에 대한 행 필터를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f06a-130">If the role you are creating has Read permissions, you can add row filters for any table using a DAX formula.</span></span> <span data-ttu-id="6f06a-131">행 필터를 추가 하려면 \*\*역할 속성- \<rolename> \*\* 대화 상자의 **페이지 선택**에서 **행 필터**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f06a-131">To add row filters, in the **Role Properties - \<rolename>** dialog box, in **Select a page**, click on **Row Filters**.</span></span>  
  
8.  <span data-ttu-id="6f06a-132">행 필터 창에서 테이블을 선택한 다음 **Dax 필터** 필드를 클릭 하 고 **dax \<tablename> 필터** 필드에 dax 수식을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f06a-132">In the row filters window, select a table, then click on the **DAX Filter** field, and then in the **DAX Filter - \<tablename>** field, type a DAX formula.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6f06a-133">DAX 필터 필드에는 \<tablename> 자동 완성 쿼리 편집기나 삽입 함수 기능이 포함 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6f06a-133">The DAX Filter - \<tablename> field does not contain an AutoComplete query editor or insert function feature.</span></span> <span data-ttu-id="6f06a-134">DAX 수식을 작성할 때 자동 완성을 사용하려면 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 DAX 수식 편집기를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f06a-134">To use AutoComplete when writing a DAX formula, you must use a DAX formula editor in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
9. <span data-ttu-id="6f06a-135">**확인** 을 클릭 하 여 역할을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f06a-135">Click **Ok** to save the role.</span></span>  
  
###  <a name="to-copy-a-role"></a><a name="bkmk_copy_role"></a><span data-ttu-id="6f06a-136">역할을 복사 하려면</span><span class="sxs-lookup"><span data-stu-id="6f06a-136">To copy a role</span></span>  
  
1.  <span data-ttu-id="6f06a-137">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 복사할 역할을 포함하는 테이블 형식 model 데이터베이스와 **역할**을 차례로 확장하고 역할을 마우스 오른쪽 단추로 클릭한 다음 **중복**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f06a-137">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the tabular model database that contains the role you want to copy, then expand **Roles**, then right click on the role, and then click **Duplicate**.</span></span>  
  
###  <a name="to-edit-a-role"></a><a name="bkmk_edit_role"></a> <span data-ttu-id="6f06a-138">역할 편집</span><span class="sxs-lookup"><span data-stu-id="6f06a-138">To edit a role</span></span>  
  
-   <span data-ttu-id="6f06a-139">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 편집할 역할을 포함하는 테이블 형식 model 데이터베이스와 **역할**을 차례로 확장하고 역할을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f06a-139">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the tabular model database that contains the role you want to edit, then expand **Roles**, then right click on the role, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="6f06a-140">**역할 속성** \<rolename> 대화 상자에서 사용 권한을 변경 하 고, 구성원을 추가 또는 제거 하 고, 행 필터를 추가/편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f06a-140">In the **Role Properties** \<rolename> dialog box, you can change permissions, add or remove members, and add/edit row filters.</span></span>  
  
###  <a name="to-delete-a-role"></a><a name="bkmk_deletet_role"></a> <span data-ttu-id="6f06a-141">역할을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="6f06a-141">To delete a role</span></span>  
  
-   <span data-ttu-id="6f06a-142">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 삭제할 역할을 포함하는 테이블 형식 model 데이터베이스와 **역할**을 차례로 확장하고 역할을 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f06a-142">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the tabular model database that contains the role you want to delete, then expand **Roles**, then right click on the role, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f06a-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6f06a-143">See Also</span></span>  
 [<span data-ttu-id="6f06a-144">역할&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="6f06a-144">Roles &#40;SSAS Tabular&#41;</span></span>](roles-ssas-tabular.md)  
  
  
