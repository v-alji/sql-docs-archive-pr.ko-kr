---
title: 개체 만들기 및 변경 (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [XML for Analysis]
- subordinate objects [XML for Analysis]
- XML for Analysis, objects
- modifying objects
- removing objects
- deleting objects
- XMLA, objects
ms.assetid: a2080867-e130-440c-92eb-f768869f34a8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2390c0b921368e7e06f0e5563a7eb59769d99c17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659703"
---
# <a name="creating-and-altering-objects-xmla"></a><span data-ttu-id="a5080-102">개체 만들기 및 변경(XMLA)</span><span class="sxs-lookup"><span data-stu-id="a5080-102">Creating and Altering Objects (XMLA)</span></span>
  <span data-ttu-id="a5080-103">주요 개체는 독립적으로 만들고 변경하고 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-103">Major objects can be independently created, altered, and deleted.</span></span> <span data-ttu-id="a5080-104">주요 개체에는 다음과 같은 개체가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-104">Major objects include the following objects:</span></span>  
  
-   <span data-ttu-id="a5080-105">서버</span><span class="sxs-lookup"><span data-stu-id="a5080-105">Servers</span></span>  
  
-   <span data-ttu-id="a5080-106">데이터베이스</span><span class="sxs-lookup"><span data-stu-id="a5080-106">Databases</span></span>  
  
-   <span data-ttu-id="a5080-107">차원</span><span class="sxs-lookup"><span data-stu-id="a5080-107">Dimensions</span></span>  
  
-   <span data-ttu-id="a5080-108">큐브</span><span class="sxs-lookup"><span data-stu-id="a5080-108">Cubes</span></span>  
  
-   <span data-ttu-id="a5080-109">측정값 그룹</span><span class="sxs-lookup"><span data-stu-id="a5080-109">Measure groups</span></span>  
  
-   <span data-ttu-id="a5080-110">파티션</span><span class="sxs-lookup"><span data-stu-id="a5080-110">Partitions</span></span>  
  
-   <span data-ttu-id="a5080-111">큐브 뷰</span><span class="sxs-lookup"><span data-stu-id="a5080-111">Perspectives</span></span>  
  
-   <span data-ttu-id="a5080-112">마이닝 모델</span><span class="sxs-lookup"><span data-stu-id="a5080-112">Mining models</span></span>  
  
-   <span data-ttu-id="a5080-113">역할</span><span class="sxs-lookup"><span data-stu-id="a5080-113">Roles</span></span>  
  
-   <span data-ttu-id="a5080-114">서버 또는 데이터베이스에 연결된 명령</span><span class="sxs-lookup"><span data-stu-id="a5080-114">Commands associated with a server or database</span></span>  
  
-   <span data-ttu-id="a5080-115">데이터 원본</span><span class="sxs-lookup"><span data-stu-id="a5080-115">Data sources</span></span>  
  
 <span data-ttu-id="a5080-116">[Create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) 명령을 사용 하면 인스턴스에 주요 개체를 만들고 alter 명령을 사용 하 여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스의 기존 주요 [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) 개체를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-116">You use the [Create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) command to create a major object on an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], and the [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) command to alter an existing major object on an instance.</span></span> <span data-ttu-id="a5080-117">두 명령은 모두 [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) 메서드를 사용 하 여 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-117">Both commands are run using the [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) method.</span></span>  
  
## <a name="creating-objects"></a><span data-ttu-id="a5080-118">개체 만들기</span><span class="sxs-lookup"><span data-stu-id="a5080-118">Creating Objects</span></span>  
 <span data-ttu-id="a5080-119">`Create` 메서드를 사용하여 개체를 만들려면 먼저 만들려는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체가 포함된 부모 개체를 식별해야 하는데,</span><span class="sxs-lookup"><span data-stu-id="a5080-119">When you create objects by using the `Create` method, you must first identify the parent object that contains the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object to be created.</span></span> <span data-ttu-id="a5080-120">명령의 [parentobject](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) 속성에 개체 참조를 제공 하 여 부모 개체를 식별할 수 있습니다 `Create` .</span><span class="sxs-lookup"><span data-stu-id="a5080-120">You identify the parent object by providing an object reference in the [ParentObject](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) property of the `Create` command.</span></span> <span data-ttu-id="a5080-121">각 개체 참조에는 `Create` 명령에 대한 부모 개체를 고유하게 식별하는 데 필요한 개체 식별자가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-121">Each object reference contains the object identifiers needed to uniquely identify the parent object for the `Create` command.</span></span> <span data-ttu-id="a5080-122">개체 참조에 대 한 자세한 내용은 [XMLA&#41;&#40;개체 정의 및 식별 ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a5080-122">For more information about object references, see [Defining and Identifying Objects &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects).</span></span>  
  
 <span data-ttu-id="a5080-123">예를 들어 큐브에 대한 새 측정값 그룹을 만들려면 큐브에 대한 개체 참조를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-123">For example, you must provide an object reference to a cube to create a new measure group for the cube.</span></span> <span data-ttu-id="a5080-124">동일한 큐브 식별자를 다른 데이터베이스에서도 사용할 수 있으므로 `ParentObject` 속성의 큐브에 대한 개체 참조에는 데이터베이스 식별자와 큐브 식별자가 모두 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-124">The object reference for the cube in the `ParentObject` property contains both a database identifier and a cube identifier, as the same cube identifier could potentially be used on a different database.</span></span>  
  
 <span data-ttu-id="a5080-125">[Objectdefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla) 요소는 만들려는 주요 개체를 정의 하는 개체 (Analysis Services Scripting Language) 요소를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-125">The [ObjectDefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla) element contains Analysis Services Scripting Language (ASSL) elements that define the major object to be created.</span></span> <span data-ttu-id="a5080-126">을 사용 하는 방법에 대 한 자세한 내용은 [Analysis Services 스크립팅 언어 &#40;를 사용 하 여 개발&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="a5080-126">For more information about ASSL, see [Developing with Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).</span></span>  
  
 <span data-ttu-id="a5080-127">`AllowOverwrite` 명령의 `Create` 특성을 true로 설정하면 지정된 식별자를 가지고 있는 기존 주요 개체를 덮어쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-127">If you set the `AllowOverwrite` attribute of the `Create` command to true, you can overwrite an existing major object that has the specified identifier.</span></span> <span data-ttu-id="a5080-128">true로 설정하지 않으면 지정된 식별자를 가지고 있는 주요 개체가 부모 개체에 이미 있을 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-128">Otherwise, an error occurs if a major object that has the specified identifier already exists in the parent object.</span></span>  
  
 <span data-ttu-id="a5080-129">명령에 대 한 자세한 내용은 `Create` [Create ELEMENT &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a5080-129">For more information about the `Create` command, see [Create Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla).</span></span>  
  
### <a name="creating-session-objects"></a><span data-ttu-id="a5080-130">세션 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="a5080-130">Creating Session Objects</span></span>  
 <span data-ttu-id="a5080-131">세션 개체는 클라이언트 애플리케이션에서 사용하는 명시적 또는 암시적 세션에만 사용할 수 있는 임시 개체로, 세션이 종료될 때 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-131">Session objects are temporary objects that are available only to the explicit or implicit session used by a client application and are deleted when the session is ended.</span></span> <span data-ttu-id="a5080-132">`Scope`명령의 특성을 `Create` *session*으로 설정 하 여 세션 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-132">You can create session objects by setting the `Scope` attribute of the `Create` command to *Session*.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a5080-133">*Session* 설정을 사용 하는 경우 `ObjectDefinition` 요소는 [Dimension](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl), [Cube](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl)또는 [MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) vall 요소만 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-133">When using the *Session* setting, the `ObjectDefinition` element can only contain [Dimension](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl), [Cube](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl), or [MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) ASSL elements.</span></span>  
  
## <a name="altering-objects"></a><span data-ttu-id="a5080-134">개체 변경</span><span class="sxs-lookup"><span data-stu-id="a5080-134">Altering Objects</span></span>  
 <span data-ttu-id="a5080-135">메서드를 사용 하 여 개체를 수정 하는 경우 `Alter` 먼저 명령의 [object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) 속성에 개체 참조를 제공 하 여 수정할 개체를 식별 해야 합니다 `Alter` .</span><span class="sxs-lookup"><span data-stu-id="a5080-135">When modifying objects by using the `Alter` method, you must first identify the object to be modified by providing an object reference in the [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) property of the `Alter` command.</span></span> <span data-ttu-id="a5080-136">각 개체 참조에는 `Alter` 명령에 대한 개체를 고유하게 식별하는 데 필요한 개체 식별자가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-136">Each object reference contains the object identifiers needed to uniquely identify the object for the `Alter` command.</span></span> <span data-ttu-id="a5080-137">개체 참조에 대 한 자세한 내용은 [XMLA&#41;&#40;개체 정의 및 식별 ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a5080-137">For more information about object references, see [Defining and Identifying Objects &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects).</span></span>  
  
 <span data-ttu-id="a5080-138">예를 들어 큐브의 구조를 수정하려면 큐브에 대한 개체 참조를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-138">For example, you must provide an object reference to a cube in order to modify the structure of a cube.</span></span> <span data-ttu-id="a5080-139">동일한 큐브 식별자를 다른 데이터베이스에서도 사용할 수 있으므로 `Object` 속성의 큐브에 대한 개체 참조에는 데이터베이스 식별자와 큐브 식별자가 모두 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-139">The object reference for the cube in the `Object` property contains both a database identifier and a cube identifier, as the same cube identifier could potentially be used on a different database.</span></span>  
  
 <span data-ttu-id="a5080-140">`ObjectDefinition` 요소는 수정할 주요 개체를 정의하는 ASSL 요소를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-140">The `ObjectDefinition` element contains ASSL elements that define the major object to be modified.</span></span> <span data-ttu-id="a5080-141">을 사용 하는 방법에 대 한 자세한 내용은 [Analysis Services 스크립팅 언어 &#40;를 사용 하 여 개발&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="a5080-141">For more information about ASSL, see [Developing with Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).</span></span>  
  
 <span data-ttu-id="a5080-142">`AllowCreate` 명령의 `Alter` 특성을 true로 설정하면 지정된 주요 개체가 없는 경우 해당 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-142">If you set the `AllowCreate` attribute of the `Alter` command to true, you can create the specified major object if the object does not exist.</span></span> <span data-ttu-id="a5080-143">true로 설정하지 않으면 지정된 주요 개체가 없을 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-143">Otherwise, an error occurs if a specified major object does not already exist.</span></span>  
  
### <a name="using-the-objectexpansion-attribute"></a><span data-ttu-id="a5080-144">ObjectExpansion 특성 사용</span><span class="sxs-lookup"><span data-stu-id="a5080-144">Using the ObjectExpansion Attribute</span></span>  
 <span data-ttu-id="a5080-145">주요 개체의 속성만 변경 하 고 주요 개체에 포함 된 보조 개체를 다시 정의 하지 않는 경우 `ObjectExpansion` `Alter` 명령의 특성을 *objectproperties*로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-145">If you are changing only the properties of the major object and are not redefining minor objects that are contained by the major object, you can set the `ObjectExpansion` attribute of the `Alter` command to *ObjectProperties*.</span></span> <span data-ttu-id="a5080-146">이 경우 `ObjectDefinition` 속성은 주요 개체의 속성에 대한 요소만 포함해야 하며 `Alter` 명령은 주요 개체에 연결된 보조 개체를 그대로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-146">The `ObjectDefinition` property then only has to contain the elements for the properties of the major object, and the `Alter` command leaves minor objects associated with the major object untouched.</span></span>  
  
 <span data-ttu-id="a5080-147">주요 개체의 보조 개체를 다시 정의 하려면 `ObjectExpansion` 특성을 *updateoptions.expandfull* 로 설정 해야 하며, 개체 정의에는 주요 개체에 포함 된 모든 보조 개체가 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-147">To redefine minor objects for a major object, you must set the `ObjectExpansion` attribute to *ExpandFull* and the object definition must include all minor objects that are contained by the major object.</span></span> <span data-ttu-id="a5080-148">주요 개체에 포함된 보조 개체가 `ObjectDefinition` 명령의 `Alter` 속성에 명시적으로 포함되지 않은 경우 포함되지 않은 보조 개체는 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-148">If the `ObjectDefinition` property of the `Alter` command does not explicitly include a minor object that is contained by the major object, the minor object that was not included is deleted.</span></span>  
  
### <a name="altering-session-objects"></a><span data-ttu-id="a5080-149">세션 개체 변경</span><span class="sxs-lookup"><span data-stu-id="a5080-149">Altering Session Objects</span></span>  
 <span data-ttu-id="a5080-150">명령으로 만든 세션 개체를 수정 하려면 `Create` `Scope` 명령의 특성을 `Alter` *session*으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-150">To modify session objects created by the `Create` command, set the `Scope` attribute of the `Alter` command to *Session*.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a5080-151">*Session* 설정을 사용 하는 경우 `ObjectDefinition` 요소는 [Dimension](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl), [Cube](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl)또는 [MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) vall 요소만 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-151">When using the *Session* setting, the `ObjectDefinition` element can only contain [Dimension](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl), [Cube](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl), or [MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) ASSL elements.</span></span>  
  
## <a name="creating-or-altering-subordinate-objects"></a><span data-ttu-id="a5080-152">하위 개체 만들기 또는 변경</span><span class="sxs-lookup"><span data-stu-id="a5080-152">Creating or Altering Subordinate Objects</span></span>  
 <span data-ttu-id="a5080-153">`Create` 또는 `Alter` 명령으로는 최상위의 주요 개체를 한 개만 만들거나 변경할 수 있지만 만들거나 수정하려는 주요 개체는 묶는 `ObjectDefinition` 속성 내에 다른 주요 개체 및 해당 주요 개체에 종속된 보조 개체에 대한 정의를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-153">Although a `Create` or `Alter` command creates or alters only one topmost major object, the major object being created or modified can contain definitions within the enclosing `ObjectDefinition` property for other major and minor objects that are subordinate to it.</span></span> <span data-ttu-id="a5080-154">예를 들어 큐브를 정의하고 `ParentObject`에 부모 데이터베이스를 지정한 경우 `ObjectDefinition`의 큐브 정의 내에서는 큐브에 대한 측정값 그룹을 정의할 수 있으며, 이 측정값 그룹 내에서는 각 측정값 그룹에 대한 파티션을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-154">For example, if you define a cube, you specify the parent database in `ParentObject`, and within the cube definition in `ObjectDefinition` you can define measure groups for the cube, and within the measure groups you can define partitions for each measure group.</span></span> <span data-ttu-id="a5080-155">보조 개체는 자신이 포함된 주요 개체 아래에만 정의될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-155">A minor object can be defined only under the major object that contains it.</span></span> <span data-ttu-id="a5080-156">주 개체 및 보조 개체에 대 한 자세한 내용은 [데이터베이스 개체 &#40;Analysis Services-다차원 데이터&#41;](../multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a5080-156">For more information about major and minor objects, see [Database Objects &#40;Analysis Services - Multidimensional Data&#41;](../multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a5080-157">예</span><span class="sxs-lookup"><span data-stu-id="a5080-157">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="a5080-158">Description</span><span class="sxs-lookup"><span data-stu-id="a5080-158">Description</span></span>  
 <span data-ttu-id="a5080-159">다음 예에서는 예제 데이터베이스를 참조 하는 관계형 데이터 원본을 만듭니다 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a5080-159">The following example creates a relational data source that references the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] sample [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a5080-160">코드</span><span class="sxs-lookup"><span data-stu-id="a5080-160">Code</span></span>  
  
```  
<Create xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    </ParentObject>  
    <ObjectDefinition>  
        <DataSource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RelationalDataSource">  
            <ID>AdventureWorksDW2012</ID>  
            <Name>AdventureWorksDW2012</Name>  
            <ConnectionString>Data Source=localhost;Initial Catalog=AdventureWorksDW2008R2;Integrated Security=True</ConnectionString>  
            <ImpersonationInfo>  
                <ImpersonationMode>ImpersonateServiceAccount</ImpersonationMode>  
            </ImpersonationInfo>  
            <ManagedProvider>System.Data.SqlClient</ManagedProvider>  
            <Timeout>PT0S</Timeout>  
        </DataSource>  
    </ObjectDefinition>  
</Create>  
```  
  
### <a name="description"></a><span data-ttu-id="a5080-161">Description</span><span class="sxs-lookup"><span data-stu-id="a5080-161">Description</span></span>  
 <span data-ttu-id="a5080-162">다음 예제에서는 이전 예제에서 만든 관계형 데이터 원본을 변경하여 데이터 원본에 대한 쿼리 제한 시간을 30초로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-162">The following example alters the relational data source created in the previous example to set the query time-out for the data source to 30 seconds.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a5080-163">코드</span><span class="sxs-lookup"><span data-stu-id="a5080-163">Code</span></span>  
  
```  
<Alter ObjectExpansion="ObjectProperties" xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DataSourceID>AdventureWorksDW2012</DataSourceID>  
    </Object>  
    <ObjectDefinition>  
        <DataSource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RelationalDataSource">  
            <ID>AdventureWorksDW2012</ID>  
            <Name>AdventureWorksDW2012</Name>  
            <ConnectionString>Data Source=fr-dwk-02;Initial Catalog=AdventureWorksDW2008R2;Integrated Security=True</ConnectionString>  
            <ManagedProvider>System.Data.SqlClient</ManagedProvider>  
            <Timeout>PT30S</Timeout>  
        </DataSource>  
    </ObjectDefinition>  
</Alter>  
```  
  
### <a name="comments"></a><span data-ttu-id="a5080-164">주석</span><span class="sxs-lookup"><span data-stu-id="a5080-164">Comments</span></span>  
 <span data-ttu-id="a5080-165">`ObjectExpansion` `Alter` 명령의 특성이 *objectproperties*로 설정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-165">The `ObjectExpansion` attribute of the `Alter` command was set to *ObjectProperties*.</span></span> <span data-ttu-id="a5080-166">이 설정을 사용 하면 보조 개체인 [ImpersonationInfo](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl) 요소를에 정의 된 데이터 원본에서 제외할 수 있습니다 `ObjectDefinition` .</span><span class="sxs-lookup"><span data-stu-id="a5080-166">This setting allows the [ImpersonationInfo](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl) element, a minor object, to be excluded from the data source defined in `ObjectDefinition`.</span></span> <span data-ttu-id="a5080-167">따라서 해당 데이터 원본에 대한 가장 정보가 첫 번째 예제에서 지정한 대로 서비스 계정으로 설정된 채 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5080-167">Therefore, the impersonation information for that data source remains set to the service account, as specified in the first example.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5080-168">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a5080-168">See Also</span></span>  
 <span data-ttu-id="a5080-169">[XMLA&#41;&#40;메서드를 실행 합니다.](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) </span><span class="sxs-lookup"><span data-stu-id="a5080-169">[Execute Method &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) </span></span>  
 <span data-ttu-id="a5080-170">[Analysis Services 스크립팅 언어 &#40;를 사용 하 여 개발&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md) </span><span class="sxs-lookup"><span data-stu-id="a5080-170">[Developing with Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md) </span></span>  
 [<span data-ttu-id="a5080-171">Analysis Services에서 XMLA를 사용하여 개발</span><span class="sxs-lookup"><span data-stu-id="a5080-171">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
