---
title: 개체 종속성 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.common.objectdependencies.f1
ms.assetid: c63d1160-3f3d-45df-99be-6fe081125fb5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 13d1775f1e4e6885fe56a43ce40c4ac155c5b361
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741539"
---
# <a name="object-dependencies"></a><span data-ttu-id="6bf10-102">개체 종속성</span><span class="sxs-lookup"><span data-stu-id="6bf10-102">Object Dependencies</span></span>
  <span data-ttu-id="6bf10-103">일부 데이터베이스 개체는 다른 데이터베이스 개체에 대해 종속적입니다.</span><span class="sxs-lookup"><span data-stu-id="6bf10-103">Some database objects have dependencies upon other database objects.</span></span> <span data-ttu-id="6bf10-104">예를 들어 뷰와 저장 프로시저는 뷰나 프로시저에서 반환한 데이터가 들어 있는 테이블의 존재 여부에 종속됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bf10-104">For example, views and stored procedures depend upon the existence of tables that contain the data returned by the view or procedure.</span></span> <span data-ttu-id="6bf10-105">현재 개체의 **개체 종속성(일반 페이지)** 에는 해당 개체가 정상적으로 작동하는 데 반드시 필요한 다른 데이터베이스 개체와 선택한 개체에 종속된 개체가 모두 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bf10-105">The **Object Dependencies (General Page)** for the current object lists both the database objects that must be present for the object to function properly and the objects that depend upon the selected object.</span></span> <span data-ttu-id="6bf10-106">정의에서 다른 개체를 참조하고 시스템 카탈로그에 해당 정의가 저장되어 있으면 이 엔터티를 *참조 엔터티*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf10-106">An object that references another object in its definition and that definition is stored in the system catalog is called a *referencing entity*.</span></span> <span data-ttu-id="6bf10-107">다른 개체에 의해 참조되는 개체는 *참조된 엔터티*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf10-107">An object that is referred to by another object is called a *referenced entity*.</span></span>  
  
 <span data-ttu-id="6bf10-108">현재 개체의 **개체 종속성(고급 페이지)** 에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 개체와 해당 개체에 종속된 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 개체가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bf10-108">The **Object Dependencies (Advanced Page)** for the current object lists the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database objects and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] objects that depend on the object.</span></span> <span data-ttu-id="6bf10-109">개체들은 서로 다른 서버에 저장되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bf10-109">The objects may be stored on different servers.</span></span>  
  
 <span data-ttu-id="6bf10-110">선택한 개체를 변경하거나 삭제하기 전에 개체의 종속성을 파악하려면 이 대화 상자를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="6bf10-110">Use this dialog box to understand the dependencies before changing or deleting the selected object.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="6bf10-111">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="6bf10-111">UI element list</span></span>  
 <span data-ttu-id="6bf10-112">**다음에 종속 된 개체**  _\<selected object>_</span><span class="sxs-lookup"><span data-stu-id="6bf10-112">**Objects that depend on**  _\<selected object>_</span></span>  
 <span data-ttu-id="6bf10-113">이 단추를 클릭하면 종속성이 추적되고 선택한 개체에 종속된 개체의 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bf10-113">Clicking this button displays a list of those objects that are dependency-tracked and that depend on the selected object.</span></span>  
  
 <span data-ttu-id="6bf10-114">**개체** _\<selected object>_ **종속**    </span><span class="sxs-lookup"><span data-stu-id="6bf10-114">**Objects on which**  _\<selected object>_  **depends**</span></span>  
 <span data-ttu-id="6bf10-115">이 단추를 클릭하면 종속성이 추적되고 선택한 개체가 종속된 개체의 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bf10-115">Clicking this button displays a list of those objects that are dependency-tracked, on which the selected object depends.</span></span>  
  
 <span data-ttu-id="6bf10-116">**종속성**</span><span class="sxs-lookup"><span data-stu-id="6bf10-116">**Dependencies**</span></span>  
 <span data-ttu-id="6bf10-117">_\<selected object>_ **에 종속된 개체**를 클릭하면 선택한 개체에 종속된 개체의 계층 뷰가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bf10-117">If **Objects that depend on** _\<selected object>_ is clicked, this displays an hierarchical view of objects that depend on the selected object.</span></span> <span data-ttu-id="6bf10-118">_\<selected object>_ **가 종속된** **개체**를 클릭하면 선택한 개체가 종속된 개체의 계층 뷰가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bf10-118">If **Objects on which** _\<selected object>_ **depends** is clicked, this displays an hierarchical view of objects on which the selected object depends.</span></span>  
  
 <span data-ttu-id="6bf10-119">**이름**</span><span class="sxs-lookup"><span data-stu-id="6bf10-119">**Name**</span></span>  
 <span data-ttu-id="6bf10-120">위의 **종속성** 트리 뷰에서 선택한 개체의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf10-120">Displays the name of the object selected in the **Dependencies** tree view above.</span></span>  
  
 <span data-ttu-id="6bf10-121">**형식**</span><span class="sxs-lookup"><span data-stu-id="6bf10-121">**Type**</span></span>  
 <span data-ttu-id="6bf10-122">위의 **종속성** 트리 뷰에서 선택한 개체의 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf10-122">Displays the type of the object selected in the **Dependencies** tree view above.</span></span>  
  
 <span data-ttu-id="6bf10-123">**마지막 동기화 시간**</span><span class="sxs-lookup"><span data-stu-id="6bf10-123">**Last Sync Time**</span></span>  
 > [!NOTE]  
>  <span data-ttu-id="6bf10-124">이 옵션은 **고급** 페이지에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bf10-124">This option is available only on the **Advanced** page.</span></span>  
  
 <span data-ttu-id="6bf10-125">종속성 정보가 마지막으로 업데이트된 날짜 및 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf10-125">Specifies the time and date when the dependency information was last updated.</span></span>  
  
 <span data-ttu-id="6bf10-126">**종속성 유형**</span><span class="sxs-lookup"><span data-stu-id="6bf10-126">**Dependency type**</span></span>  
 > [!NOTE]  
>  <span data-ttu-id="6bf10-127">이 옵션은 **일반** 페이지에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bf10-127">This option is available only on the **General** page.</span></span>  
  
 <span data-ttu-id="6bf10-128">두 개체 간의 종속성 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf10-128">Displays the type of dependency between two objects.</span></span> <span data-ttu-id="6bf10-129">다음 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bf10-129">Can be one of the following:</span></span>  
  
-   <span data-ttu-id="6bf10-130">스키마 바운드 종속성</span><span class="sxs-lookup"><span data-stu-id="6bf10-130">Schema-bound dependency</span></span>  
  
     <span data-ttu-id="6bf10-131">참조 개체가 존재하는 한 참조된 개체가 삭제되거나 수정되지 않도록 방지하는 두 개체 간의 관계입니다.</span><span class="sxs-lookup"><span data-stu-id="6bf10-131">Is a relationship between two objects that prevents the referenced object from being dropped or modified as long as the referencing object exists.</span></span> <span data-ttu-id="6bf10-132">스키마 바운드 종속성은 WITH SCHEMABINDING 절을 사용하여 뷰 또는 사용자 정의 함수를 만들거나 테이블이 CHECK 또는 DEFAULT 제약 조건이나 계산 열의 정의를 통해 다른 개체를 참조하면 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bf10-132">A schema-bound dependency is created when a view or user-defined function is created by using the WITH SCHEMABINDING clause, or when a table references another object through a CHECK or DEFAULT constraint or in the definition of a computed column.</span></span>  
  
-   <span data-ttu-id="6bf10-133">비스키마 바운드 종속성</span><span class="sxs-lookup"><span data-stu-id="6bf10-133">Non-schema-bound dependency</span></span>  
  
     <span data-ttu-id="6bf10-134">참조된 개체가 삭제되거나 수정되지 않도록 방지하지 않는 두 개체 간의 관계입니다.</span><span class="sxs-lookup"><span data-stu-id="6bf10-134">Is a relationship between two objects that does not prevent the referenced object from being dropped or modified.</span></span>  
  
-   <span data-ttu-id="6bf10-135">사용할 수 없거나 확인되지 않은 엔터티</span><span class="sxs-lookup"><span data-stu-id="6bf10-135">Not available or Unresolved Entity</span></span>  
  
     <span data-ttu-id="6bf10-136">종속성 유형을 확인할 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6bf10-136">Indicates the dependency type cannot be determined.</span></span> <span data-ttu-id="6bf10-137">이는 선택한 개체가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이전 버전의 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]인스턴스에 있는 경우에만 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf10-137">This occurs only when the selected object is on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is earlier than [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
  
