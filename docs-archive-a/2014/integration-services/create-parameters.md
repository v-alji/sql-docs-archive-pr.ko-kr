---
title: 매개 변수 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.parameterwindow.f1
ms.assetid: cd5d675b-dd5d-49cc-8b1f-dc717a973f99
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a26ae08c08a32b0593be8c9a2777b7cfe9c884fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647786"
---
# <a name="create-parameters"></a><span data-ttu-id="98971-102">Create Parameters</span><span class="sxs-lookup"><span data-stu-id="98971-102">Create Parameters</span></span>
  <span data-ttu-id="98971-103">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 를 사용하여 프로젝트 매개 변수 및 패키지 매개 변수를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98971-103">You use [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create project parameters and package parameters.</span></span> <span data-ttu-id="98971-104">다음 절차에서는 패키지/프로젝트 매개 변수를 만드는 단계별 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="98971-104">The following procedures provide step-by-step instructions for creating package/project parameters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98971-105">이전 버전의 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 를 사용하여 만든 프로젝트를 프로젝트 배포 모델로 변환하는 경우 **Integration Services 프로젝트 변환 마법사** 를 사용하여 구성에 따라 매개 변수를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98971-105">If you are converting a project that you created using an earlier version of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] to the project deployment model, you can use the **Integration Services Project Conversion Wizard** to create parameters based on configurations.</span></span> <span data-ttu-id="98971-106">자세한 내용은 [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="98971-106">For more information, see [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md).</span></span>  
  
### <a name="to-create-package-parameters"></a><span data-ttu-id="98971-107">패키지 매개 변수를 만들려면</span><span class="sxs-lookup"><span data-stu-id="98971-107">To create package parameters</span></span>  
  
1.  <span data-ttu-id="98971-108">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 패키지를 열고 SSIS 디자이너에서 **매개 변수** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98971-108">Open the package in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], and then click the **Parameters** tab in the SSIS Designer.</span></span>  
  
     <span data-ttu-id="98971-109">![패키지 매개 변수 탭](media/denali-package-parameters.gif "패키지 매개 변수 탭")</span><span class="sxs-lookup"><span data-stu-id="98971-109">![Package Parameters Tab](media/denali-package-parameters.gif "Package Parameters Tab")</span></span>  
  
2.  <span data-ttu-id="98971-110">도구 모음에서 **매개 변수 추가** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98971-110">Click the **Add Parameter** button on the toolbar.</span></span>  
  
     <span data-ttu-id="98971-111">![도구 모음 단추 추가](media/denali-parameter-add.gif "추가 도구 모음 단추")</span><span class="sxs-lookup"><span data-stu-id="98971-111">![Add Toolbar Button](media/denali-parameter-add.gif "Add Toolbar Button")</span></span>  
  
3.  <span data-ttu-id="98971-112">목록 자체에서 또는 **속성**창에서 **이름**, **데이터 형식**, **값**, **구분** 및 **필수** 속성의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="98971-112">Enter values for the **Name**, **Data Type**, **Value**, **Sensitive**, and **Required** properties in the list itself or in the **Properties** window.</span></span> <span data-ttu-id="98971-113">다음 표에서는 이러한 속성을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="98971-113">The following table describes these properties.</span></span>  
  
    |<span data-ttu-id="98971-114">속성</span><span class="sxs-lookup"><span data-stu-id="98971-114">Property</span></span>|<span data-ttu-id="98971-115">Description</span><span class="sxs-lookup"><span data-stu-id="98971-115">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="98971-116">Name</span><span class="sxs-lookup"><span data-stu-id="98971-116">Name</span></span>|<span data-ttu-id="98971-117">매개 변수의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="98971-117">The name of the parameter.</span></span>|  
    |<span data-ttu-id="98971-118">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="98971-118">Data type</span></span>|<span data-ttu-id="98971-119">매개 변수의 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="98971-119">The data type of the parameter.</span></span>|  
    |<span data-ttu-id="98971-120">기본값</span><span class="sxs-lookup"><span data-stu-id="98971-120">Default value</span></span>|<span data-ttu-id="98971-121">디자인 타임에 할당되는 매개 변수의 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="98971-121">The default value for the parameter assigned at design time.</span></span> <span data-ttu-id="98971-122">디자인 기본값이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="98971-122">This is also known as the design default.</span></span>|  
    |<span data-ttu-id="98971-123">중요</span><span class="sxs-lookup"><span data-stu-id="98971-123">Sensitive</span></span>|<span data-ttu-id="98971-124">구분 매개 변수 값은 카탈로그에서 암호화되고 Transact-SQL 또는 SQL Server Management Studio를 사용하여 볼 경우 NULL 값으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="98971-124">Sensitive parameter values are encrypted in the catalog and appear as a NULL value when viewed with Transact-SQL or SQL Server Management Studio.</span></span>|  
    |<span data-ttu-id="98971-125">필수</span><span class="sxs-lookup"><span data-stu-id="98971-125">Required</span></span>|<span data-ttu-id="98971-126">패키지를 실행하기 전에 반드시 지정해야 하는 디자인 기본값 이외의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="98971-126">Requires that a value, other than the design default, is specified before the package can execute.</span></span>|  
    |<span data-ttu-id="98971-127">Description</span><span class="sxs-lookup"><span data-stu-id="98971-127">Description</span></span>|<span data-ttu-id="98971-128">유지 관리의 편의를 위한 매개 변수 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="98971-128">For maintainability, the description of the parameter.</span></span> <span data-ttu-id="98971-129">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]의 경우 Visual Studio 속성 창의 해당 매개 변수 창에서 매개 변수를 선택할 때 매개 변수 설명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="98971-129">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], set the parameter description in the Visual Studio Properties window when the parameter is selected in the applicable parameters window.</span></span>|  
  
    > [!NOTE]  
    >  <span data-ttu-id="98971-130">프로젝트를 카탈로그에 배포하면 몇 가지 추가 속성이 프로젝트와 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="98971-130">When you deploy a project to the catalog, several more properties become associated with the project.</span></span> <span data-ttu-id="98971-131">카탈로그의 모든 매개 변수에 대한 모든 속성을 보려면 [catalog.object_parameters&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database) 뷰를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="98971-131">To see all properties for all parameters in the catalog, use the [catalog.object_parameters &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database) view.</span></span>  
  
4.  <span data-ttu-id="98971-132">프로젝트를 저장하여 매개 변수 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="98971-132">Save the project to save changes to parameters.</span></span> <span data-ttu-id="98971-133">매개 변수 값은 프로젝트 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="98971-133">Parameter values are stored in the project file.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="98971-134">목록에서 직접 편집하거나 **속성** 창을 사용하여 매개 변수 속성의 값을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98971-134">You can in-place edit in the list or use the **Properties** window to modify the values of parameter properties.</span></span> <span data-ttu-id="98971-135">**삭제(X)** 도구 모음 단추를 사용하여 매개 변수를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98971-135">You can delete a parameter by using the **Delete (X)** toolbar button.</span></span> <span data-ttu-id="98971-136">마지막 도구 모음 단추를 사용하면 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 패키지를 실행할 때만 사용되는 매개 변수의 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98971-136">Using the last toolbar button, you can specify a value for a parameter that is used only when you execute the package in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="98971-137">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 프로젝트를 열지 않고 패키지 파일을 다시 열면 **매개 변수** 탭이 비어 있고 비활성화된 상태로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="98971-137">If you re-open the package file without opening the project in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], the **Parameters** tab will be empty and disabled.</span></span>  
  
### <a name="to-create-project-parameters"></a><span data-ttu-id="98971-138">프로젝트 매개 변수를 만들려면</span><span class="sxs-lookup"><span data-stu-id="98971-138">To create project parameters</span></span>  
  
1.  <span data-ttu-id="98971-139">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="98971-139">Open the project in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="98971-140">솔루션 탐색기에서 **Project.params**를 마우스 오른쪽 단추로 클릭한 다음 **열기**를 클릭하거나 **Project.params**를 두 번 클릭하여 이 항목을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="98971-140">Right-click **Project.params** in Solution Explorer, and then click **Open** (OR) double-click **Project.params** to open it.</span></span>  
  
     <span data-ttu-id="98971-141">![프로젝트 매개 변수 창](media/denali-project-parameters.gif "프로젝트 매개 변수 창")</span><span class="sxs-lookup"><span data-stu-id="98971-141">![Project Parameters Window](media/denali-project-parameters.gif "Project Parameters Window")</span></span>  
  
3.  <span data-ttu-id="98971-142">도구 모음에서 **매개 변수 추가** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98971-142">Click the **Add Parameter** button on the toolbar.</span></span>  
  
     <span data-ttu-id="98971-143">![도구 모음 단추 추가](media/denali-parameter-add.gif "추가 도구 모음 단추")</span><span class="sxs-lookup"><span data-stu-id="98971-143">![Add Toolbar Button](media/denali-parameter-add.gif "Add Toolbar Button")</span></span>  
  
4.  <span data-ttu-id="98971-144">**이름**, **데이터 형식**, **값**, **구분**및 **필수** 속성의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="98971-144">Enter values for the **Name**, **Data Type**, **Value**, **Sensitive**, and **Required** properties.</span></span>  
  
    |<span data-ttu-id="98971-145">속성</span><span class="sxs-lookup"><span data-stu-id="98971-145">Property</span></span>|<span data-ttu-id="98971-146">Description</span><span class="sxs-lookup"><span data-stu-id="98971-146">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="98971-147">Name</span><span class="sxs-lookup"><span data-stu-id="98971-147">Name</span></span>|<span data-ttu-id="98971-148">매개 변수의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="98971-148">The name of the parameter.</span></span>|  
    |<span data-ttu-id="98971-149">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="98971-149">Data type</span></span>|<span data-ttu-id="98971-150">매개 변수의 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="98971-150">The data type of the parameter.</span></span>|  
    |<span data-ttu-id="98971-151">기본값</span><span class="sxs-lookup"><span data-stu-id="98971-151">Default value</span></span>|<span data-ttu-id="98971-152">디자인 타임에 할당되는 매개 변수의 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="98971-152">The default value for the parameter assigned at design time.</span></span> <span data-ttu-id="98971-153">디자인 기본값이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="98971-153">This is also known as the design default.</span></span>|  
    |<span data-ttu-id="98971-154">중요</span><span class="sxs-lookup"><span data-stu-id="98971-154">Sensitive</span></span>|<span data-ttu-id="98971-155">구분 매개 변수 값은 카탈로그에서 암호화되고 Transact-SQL 또는 SQL Server Management Studio를 사용하여 볼 경우 NULL 값으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="98971-155">Sensitive parameter values are encrypted in the catalog and appear as a NULL value when viewed with Transact-SQL or SQL Server Management Studio.</span></span>|  
    |<span data-ttu-id="98971-156">필수</span><span class="sxs-lookup"><span data-stu-id="98971-156">Required</span></span>|<span data-ttu-id="98971-157">패키지를 실행하기 전에 반드시 지정해야 하는 디자인 기본값 이외의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="98971-157">Requires that a value, other than the design default, is specified before the package can execute.</span></span>|  
    |<span data-ttu-id="98971-158">Description</span><span class="sxs-lookup"><span data-stu-id="98971-158">Description</span></span>|<span data-ttu-id="98971-159">유지 관리의 편의를 위한 매개 변수 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="98971-159">For maintainability, the description of the parameter.</span></span> <span data-ttu-id="98971-160">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]의 경우 Visual Studio 속성 창의 해당 매개 변수 창에서 매개 변수를 선택할 때 매개 변수 설명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="98971-160">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], set the parameter description in the Visual Studio Properties window when the parameter is selected in the applicable parameters window.</span></span>|  
  
5.  <span data-ttu-id="98971-161">프로젝트를 저장하여 매개 변수 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="98971-161">Save the project to save changes to parameters.</span></span> <span data-ttu-id="98971-162">매개 변수 값은 프로젝트 파일의 구성에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="98971-162">Parameter values are stored in configurations in the project file.</span></span> <span data-ttu-id="98971-163">매개 변수 값의 모든 변경 사항을 디스크에 커밋하려면 프로젝트 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="98971-163">Save the project file to commit to disk any changes in the parameter values.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="98971-164">목록에서 직접 편집하거나 **속성** 창을 사용하여 매개 변수 속성의 값을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98971-164">You can in-place edit in the list or use the **Properties** window to modify the values of parameter properties.</span></span> <span data-ttu-id="98971-165">**삭제(X)** 도구 모음 단추를 사용하여 매개 변수를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98971-165">You can delete a parameter by using the **Delete (X)** toolbar button.</span></span> <span data-ttu-id="98971-166">마지막 도구 모음 단추를 사용하여 **매개 변수 값 관리** 대화 상자를 열면 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 패키지를 실행할 때만 사용되는 매개 변수의 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98971-166">Using the last toolbar button to open the **Manage Parameter Values** dialog box, you can specify a value for a parameter that is used only when you execute the package in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98971-167">참고 항목</span><span class="sxs-lookup"><span data-stu-id="98971-167">See Also</span></span>  
 [<span data-ttu-id="98971-168">SSIS&#41; 매개 변수 &#40;Integration Services</span><span class="sxs-lookup"><span data-stu-id="98971-168">Integration Services &#40;SSIS&#41; Parameters</span></span>](integration-services-ssis-package-and-project-parameters.md)  
  
  
