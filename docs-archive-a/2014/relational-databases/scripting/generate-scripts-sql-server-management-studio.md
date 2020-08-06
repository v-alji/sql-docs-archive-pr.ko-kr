---
title: 스크립트 생성
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 9711c617-3c68-4e5a-aea3-befc64d51524
author: rothja
ms.author: jroth
ms.openlocfilehash: 199d5e0c98d220861ee0dfb48a44a71675d8ba87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660485"
---
# <a name="generate-scripts-sql-server-management-studio"></a><span data-ttu-id="745f0-102">스크립트 생성(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="745f0-102">Generate Scripts (SQL Server Management Studio)</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="745f0-103">에서는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트를 생성하는 두 가지 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-103">provides two mechanisms for generating [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts.</span></span> <span data-ttu-id="745f0-104">**스크립트 생성 및 게시 마법사**를 사용 하 여 여러 개체에 대 한 스크립트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-104">You can create scripts for multiple objects by using the **Generate and Publish Scripts Wizard.**.</span></span> <span data-ttu-id="745f0-105">또한 **개체 탐색기** 에서 **스크립팅**메뉴를 사용하여 개별 개체 또는 여러 개체에 대한 스크립트를 생성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-105">You can also generate a script for individual objects or multiple objects by using the **Script as** menu in **Object Explorer**.</span></span>  
  
1.  <span data-ttu-id="745f0-106">**방법 선택:**  [스크립트 생성 및 게시 마법사](#GenPubScriptWiz), [개체 탐색기 스크립팅 메뉴](#OEScriptAsMenu)</span><span class="sxs-lookup"><span data-stu-id="745f0-106">**Choose a method:**  [Generate and Publish Scripts Wizard](#GenPubScriptWiz), [Object Explorer Script As Menu](#OEScriptAsMenu)</span></span>  
  
2.  <span data-ttu-id="745f0-107">**스크립트를 메뉴로 사용:**  [단일 개체 스크립팅](#ScriptSingleObject), [개체 탐색기를 사용하여 두 개체 스크립팅](#ScriptTwoObjectsOE), [개체 탐색기 정보를 사용하여 두 개체 스크립팅](#ScriptTwoObjectsOED)</span><span class="sxs-lookup"><span data-stu-id="745f0-107">**To use the Script As menu:**  [Script a Single Object](#ScriptSingleObject), [Script Two Objects Using Object Explorer](#ScriptTwoObjectsOE), [Script Two Objects Using Object Explorer Details](#ScriptTwoObjectsOED)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="745f0-108">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="745f0-108">Before You Begin</span></span>  
 <span data-ttu-id="745f0-109">요구 사항에 가장 적합한 메커니즘을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-109">Choose the mechanism that best meets your requirements.</span></span>  
  
###  <a name="generate-and-publish-scripts-wizard"></a><a name="GenPubScriptWiz"></a> <span data-ttu-id="745f0-110">스크립트 생성 및 게시 마법사</span><span class="sxs-lookup"><span data-stu-id="745f0-110">Generate and Publish Scripts Wizard</span></span>  
 <span data-ttu-id="745f0-111">**스크립트 생성 및 게시 마법사** 를 사용하여 다양한 개체에 대한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-111">Use the **Generate and Publish Scripts Wizard** to create a [!INCLUDE[tsql](../../includes/tsql-md.md)] script for many objects.</span></span> <span data-ttu-id="745f0-112">이 마법사는 데이터베이스의 모든 개체 또는 사용자가 선택한 개체의 하위 집합에 대한 스크립트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-112">The wizard generates a script of all the objects in a database, or a subset of the objects that you select.</span></span> <span data-ttu-id="745f0-113">이 마법사에는 사용 권한, 데이터 정렬, 제약 조건 등을 포함할지 여부와 같은 여러 스크립트 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-113">The wizard has many options for your scripts, such as whether to include permissions, collation, constraints, and so on.</span></span> <span data-ttu-id="745f0-114">마법사를 사용하는 방법은 [Generate and Publish Scripts Wizard](generate-and-publish-scripts-wizard.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="745f0-114">For instructions on using the wizard, see [Generate and Publish Scripts Wizard](generate-and-publish-scripts-wizard.md).</span></span>  
  
###  <a name="object-explorer-script-as-menu"></a><a name="OEScriptAsMenu"></a> <span data-ttu-id="745f0-115">개체 탐색기 스크립팅 메뉴</span><span class="sxs-lookup"><span data-stu-id="745f0-115">Object Explorer Script As Menu</span></span>  
 <span data-ttu-id="745f0-116">**개체 탐색기 스크립팅** 메뉴를 사용하여 단일 개체, 여러 개체 또는 단일 개체에 대한 여러 문을 스크립팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-116">You can use the **Object Explorer Script as** menu to script a single object, script multiple objects, or script multible statements for a single objects.</span></span> <span data-ttu-id="745f0-117">여러 스크립트 유형 중 하나를 선택할 수 있습니다. 예를 들어 개체를 만들거나 변경하거나 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-117">You can choose one of several types of scripts; for example to create, alter, or drop the object.</span></span> <span data-ttu-id="745f0-118">쿼리 편집기 창의 스크립트를 파일이나 클립보드에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-118">You can save the script in a Query Editor window, to a file, or to the Clipboard.</span></span> <span data-ttu-id="745f0-119">스크립트는 유니코드 형식으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-119">The script is created in Unicode format.</span></span>  
  
##  <a name="to-generate-a-script-of-a-single-object"></a><a name="ScriptSingleObject"></a> <span data-ttu-id="745f0-120">단일 개체의 스크립트를 생성하려면</span><span class="sxs-lookup"><span data-stu-id="745f0-120">To generate a script of a single object</span></span>  
 <span data-ttu-id="745f0-121">**단일 개체를 스크립팅하려면**</span><span class="sxs-lookup"><span data-stu-id="745f0-121">**To script a single object**</span></span>  
  
1.  <span data-ttu-id="745f0-122">개체 탐색기에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-122">In Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="745f0-123">**데이터베이스**를 확장한 다음 스크립팅할 개체가 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-123">Expand **Databases**, and then expand the database containing the object to be scripted.</span></span>  
  
3.  <span data-ttu-id="745f0-124">개체의 범주를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-124">Expand the category of the object.</span></span> <span data-ttu-id="745f0-125">예를 들어 **테이블** 또는 **뷰** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-125">For example, expand the **Tables** or **Views** node.</span></span>  
  
4.  <span data-ttu-id="745f0-126">개체를 마우스 오른쪽 단추로 클릭 하 고 \*\*스크립팅 \<object type> \*\*을 가리킵니다. 예를 들어 **테이블 스크립팅**을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-126">Right-click the object, point to **Script \<object type> as**, For example, point to **Script Table as**.</span></span>  
  
5.  <span data-ttu-id="745f0-127">스크립트 유형을 가리킵니다(예: **CREATE** 또는 **ALTER**).</span><span class="sxs-lookup"><span data-stu-id="745f0-127">Point to the script type, such as **Create to** or **Alter to**.</span></span>  
  
6.  <span data-ttu-id="745f0-128">스크립트를 저장할 위치를 선택합니다(예: **새 쿼리 편집기 창** 또는 **클립보드**).</span><span class="sxs-lookup"><span data-stu-id="745f0-128">Select the location to save the script, such as **New Query Editor Window** or **Clipboard**.</span></span>  
  
##  <a name="to-generate-a-script-of-two-objects-using-object-explorer"></a><a name="ScriptTwoObjectsOE"></a><span data-ttu-id="745f0-129">개체 탐색기를 사용 하 여 두 개체의 스크립트를 생성 하려면</span><span class="sxs-lookup"><span data-stu-id="745f0-129">To generate a script of two objects using Object Explorer</span></span>  
 <span data-ttu-id="745f0-130">**개체 탐색기를 사용하여 두 개체를 스크립팅하려면**</span><span class="sxs-lookup"><span data-stu-id="745f0-130">**To script two objects using Object Explorer**</span></span>  
  
 <span data-ttu-id="745f0-131">프로시저를 삭제한 다음 프로시저를 만들거나 테이블을 만든 다음 테이블을 변경하는 등 여러 옵션이 있는 스크립트가 필요한 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-131">Sometimes you may want a script with multiple options, such as drop a procedure and then create a procedure, or create a table and then alter a table.</span></span> <span data-ttu-id="745f0-132">아래의 여러 개체에 대한 스크립트 생성 프로세스는 테이블, 뷰, 저장 프로시저 등 여러 개체 유형을 참조하는 스크립트를 만들어야 하는 경우에도 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-132">The processes below for generating scripts of multiple objects also work if you need to create a script that references different types of objects, such as tables, views, and stored procedures.</span></span>  
  
1.  <span data-ttu-id="745f0-133">개체 탐색기에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-133">In Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="745f0-134">**데이터베이스**를 확장한 다음 스크립팅할 개체가 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-134">Expand **Databases**, and then expand the database containing the objects to be scripted.</span></span>  
  
3.  <span data-ttu-id="745f0-135">스크립팅할 첫 번째 개체를 마우스 오른쪽 단추로 클릭 하 고 \*\*스크립트를 \<object type> \*\*가리킨 다음 다른 **이름으로 저장** 선택 항목에서 **새 쿼리 편집기 창** 을 출력 대상으로 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-135">Right-click the first object to be scripted, point to **Script \<object type> as**, and in the **Save as** selections chooses **New Query Editor Window** as the output destination.</span></span>  
  
4.  <span data-ttu-id="745f0-136">스크립팅할 두 번째 개체를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-136">Navigate to the second object you want to script.</span></span>  
  
5.  <span data-ttu-id="745f0-137">개체를 마우스 오른쪽 단추로 클릭 하 고 \*\*스크립트 \<object type> \*\*를 가리킨 다음 다른 **이름으로 저장** 선택 항목에서 **클립보드** 를 출력 대상으로 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-137">Right-click the object, point to **Script \<object type> as**, and in the **Save as** selections chooses **Clipboard** as the output destination.</span></span>  
  
6.  <span data-ttu-id="745f0-138">첫 번째 개체에 대해 열린 쿼리 편집기 창에서 클립보드에 저장된 두 번째 개체에 대한 스크립트를 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-138">In the Query Editor window opened for the first object, paste the script for the second object from the clipboard.</span></span>  
  
##  <a name="to-generate-a-script-of-two-objects-using-object-explorer-details"></a><a name="ScriptTwoObjectsOED"></a><span data-ttu-id="745f0-139">개체 탐색기 정보를 사용 하 여 두 개체의 스크립트를 생성 하려면</span><span class="sxs-lookup"><span data-stu-id="745f0-139">To generate a script of two objects using Object Explorer Details</span></span>  
 <span data-ttu-id="745f0-140">**개체 탐색기 정보를 사용하여 두 개체를 스크립팅하려면**</span><span class="sxs-lookup"><span data-stu-id="745f0-140">**To script two objects using Object Explorer Details**</span></span>  
  
 <span data-ttu-id="745f0-141">**개체 탐색기 정보** 창을 사용하여 동일한 범주의 여러 개체에 대한 스크립트를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-141">You can use the **Object Explorer Details** pane to generate a script for mutliple objects of the same category.</span></span>  
  
1.  <span data-ttu-id="745f0-142">개체 탐색기에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-142">In Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="745f0-143">**데이터베이스**를 확장한 다음 스크립팅할 개체가 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-143">Expand **Databases**, and then expand the database containing the objects to be scripted.</span></span>  
  
3.  <span data-ttu-id="745f0-144">스크립팅할 개체 유형의 범주 노드(예: **테이블** 노드)로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-144">Expand the category node of the types of object you want to script, such as the **Tables** node.</span></span>  
  
4.  <span data-ttu-id="745f0-145">**F7** 을 선택하거나 **보기**메뉴를 열고 **개체 탐색기 정보** 를 선택하여 **개체 탐색기 정보**창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-145">Open the **Object Explorer Details** pane by either selecting **F7**, or opening the **View** menu and selecting **Object Explorer Details**.</span></span>  
  
5.  <span data-ttu-id="745f0-146">스크립팅할 개체 중 하나를 마우스 왼쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-146">Left-click one of the objects you want to script.</span></span>  
  
6.  <span data-ttu-id="745f0-147">Crtl 키를 누른 채로 스크립팅할 두 번째 개체를 마우스 왼쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-147">Crtl + left-click the second object you want to script.</span></span>  
  
7.  <span data-ttu-id="745f0-148">선택한 개체 중 하나를 마우스 오른쪽 단추로 클릭 하 고 \*\*스크립팅 \<object type> \*\*을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="745f0-148">Right-click one of the selected objects, and select **Script \<object type> as**.</span></span>  
  
  
