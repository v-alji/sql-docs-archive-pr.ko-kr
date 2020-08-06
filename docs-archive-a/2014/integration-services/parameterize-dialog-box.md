---
title: 매개 변수화 대화 상자 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.parameter.f1
ms.assetid: fac02b6d-d247-447a-8940-e8700c7ac350
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8db19844132402740aec092d6e88f3c9e3864d58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651079"
---
# <a name="parameterize-dialog-box"></a><span data-ttu-id="4e5d7-102">Parameterize Dialog Box</span><span class="sxs-lookup"><span data-stu-id="4e5d7-102">Parameterize Dialog Box</span></span>
  <span data-ttu-id="4e5d7-103">**매개 변수화** 대화 상자를 사용하여 새 매개 변수나 기존 매개 변수를 태스크의 속성과 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e5d7-103">The **Parameterize** dialog box enables you to associate a new or an existing parameter with a property of a task.</span></span> <span data-ttu-id="4e5d7-104">태스크나 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너의 제어 흐름 탭을 마우스 오른쪽 단추로 클릭한 다음 **매개 변수화**를 클릭하여 이 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4e5d7-104">You open the dialog box by right-clicking a task or the Control Flow tab in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer and then by clicking **Parameterize**.</span></span> <span data-ttu-id="4e5d7-105">다음 목록에서는 이 대화 상자의 UI 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4e5d7-105">The following list describes UI elements in the dialog box.</span></span> <span data-ttu-id="4e5d7-106">매개 변수에 대한 자세한 내용은 [Integration Services&#40;SSIS&#41; 매개 변수](integration-services-ssis-package-and-project-parameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4e5d7-106">For more information about parameters, see [Integration Services &#40;SSIS&#41; Parameters](integration-services-ssis-package-and-project-parameters.md).</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="4e5d7-107">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="4e5d7-107">UI element list</span></span>  
 <span data-ttu-id="4e5d7-108">**속성**</span><span class="sxs-lookup"><span data-stu-id="4e5d7-108">**Property**</span></span>  
 <span data-ttu-id="4e5d7-109">매개 변수와 연결할 태스크의 속성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4e5d7-109">Select the property of the task that you want to associate with a parameter.</span></span> <span data-ttu-id="4e5d7-110">이 목록은 매개 변수화할 수 있는 모든 속성으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="4e5d7-110">This list is populated with all the properties that can be parameterized.</span></span>  
  
 <span data-ttu-id="4e5d7-111">**기존 매개 변수 사용**</span><span class="sxs-lookup"><span data-stu-id="4e5d7-111">**Use existing parameter**</span></span>  
 <span data-ttu-id="4e5d7-112">이 옵션을 선택하여 태스크의 속성을 기존 매개 변수와 연결한 다음 드롭다운 목록에서 매개 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4e5d7-112">Select this option to associate the property of task with an existing parameter and then select the parameter from drop-down list.</span></span>  
  
 <span data-ttu-id="4e5d7-113">**매개 변수 사용 안 함**</span><span class="sxs-lookup"><span data-stu-id="4e5d7-113">**Do not use parameter**</span></span>  
 <span data-ttu-id="4e5d7-114">매개 변수에 대한 참조를 제거하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4e5d7-114">Select this option to remove a reference to a parameter.</span></span> <span data-ttu-id="4e5d7-115">매개 변수는 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4e5d7-115">The parameter is not deleted.</span></span>  
  
 <span data-ttu-id="4e5d7-116">**새 매개 변수 만들기**</span><span class="sxs-lookup"><span data-stu-id="4e5d7-116">**Create new parameter**</span></span>  
 <span data-ttu-id="4e5d7-117">이 옵션을 선택하여 태스크의 속성과 연결할 새 매개 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4e5d7-117">Select this option to create a new parameter that you want to associate with the property of the task.</span></span>  
  
 <span data-ttu-id="4e5d7-118">**이름**</span><span class="sxs-lookup"><span data-stu-id="4e5d7-118">**Name**</span></span>  
 <span data-ttu-id="4e5d7-119">만들려는 매개 변수의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4e5d7-119">Specify the name of the parameter you want to create.</span></span>  
  
 <span data-ttu-id="4e5d7-120">**설명**</span><span class="sxs-lookup"><span data-stu-id="4e5d7-120">**Description**</span></span>  
 <span data-ttu-id="4e5d7-121">매개 변수에 대한 설명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4e5d7-121">Specify the description for parameter.</span></span>  
  
 <span data-ttu-id="4e5d7-122">**값**</span><span class="sxs-lookup"><span data-stu-id="4e5d7-122">**Value**</span></span>  
 <span data-ttu-id="4e5d7-123">매개 변수의 기본값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4e5d7-123">Specify the default value for the parameter.</span></span> <span data-ttu-id="4e5d7-124">이 값은 디자인 기본값이라고도 하며 나중에 배포할 때 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e5d7-124">This is also known as the design default, which can be overridden later at the deployment time.</span></span>  
  
 <span data-ttu-id="4e5d7-125">**범위**</span><span class="sxs-lookup"><span data-stu-id="4e5d7-125">**Scope**</span></span>  
 <span data-ttu-id="4e5d7-126">**프로젝트** 또는 **패키지** 옵션을 선택하여 매개 변수의 범위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4e5d7-126">Specify the scope of the parameter by selecting either **Project** or **Package** option.</span></span> <span data-ttu-id="4e5d7-127">프로젝트 매개 변수는 프로젝트가 수신하는 외부 입력을 프로젝트 내 하나 이상의 패키지에 제공하기 위해 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e5d7-127">Project parameters are used to supply any external input the project receives to one or more packages in the project.</span></span> <span data-ttu-id="4e5d7-128">패키지 매개 변수를 사용하면 패키지를 편집하여 다시 배포할 필요 없이 패키지 실행을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e5d7-128">Package parameters allow you to modify package execution without having to edit and redeploy the package.</span></span>  
  
 <span data-ttu-id="4e5d7-129">**따른**</span><span class="sxs-lookup"><span data-stu-id="4e5d7-129">**Sensitive**</span></span>  
 <span data-ttu-id="4e5d7-130">확인란을 선택하거나 선택 취소하여 매개 변수가 중요한지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4e5d7-130">Specify whether the parameter is a sensitive by checking or clearing the check box.</span></span> <span data-ttu-id="4e5d7-131">구분 매개 변수 값은 카탈로그에서 암호화되고 Transact-SQL 또는 SQL Server Management Studio를 사용하여 볼 경우 NULL 값으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="4e5d7-131">Sensitive parameter values are encrypted in the catalog and appear as a NULL value when viewed with Transact-SQL or SQL Server Management Studio.</span></span>  
  
 <span data-ttu-id="4e5d7-132">**필수**</span><span class="sxs-lookup"><span data-stu-id="4e5d7-132">**Required**</span></span>  
 <span data-ttu-id="4e5d7-133">매개 변수 사용 시 디자인 기본값 이외의 값을 지정해야 패키지를 실행할 수 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4e5d7-133">Specify whether the parameter requires that a value, other than the design default, is specified before the package can execute.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="4e5d7-134">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="4e5d7-134">UI element list</span></span>  
  
