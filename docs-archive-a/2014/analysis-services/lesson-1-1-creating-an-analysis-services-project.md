---
title: Analysis Services 프로젝트 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 065fdc60-1791-4e27-9ed5-51d751b3f8c4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 50640dd7821943dfc3914326f7e8cba32253d307
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639064"
---
# <a name="creating-an-analysis-services-project"></a><span data-ttu-id="baca4-102">Analysis Services 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="baca4-102">Creating an Analysis Services Project</span></span>
  <span data-ttu-id="baca4-103">다음 작업에서는를 사용 하 여 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] `Analysis Services Tutorial` 프로젝트 템플릿을 기반으로 이라는 새 프로젝트를 만듭니다 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="baca4-103">In the following task, you use [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create a new [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project named `Analysis Services Tutorial`, based on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Project template.</span></span> <span data-ttu-id="baca4-104">*프로젝트* 는 관련된 개체의 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="baca4-104">A *project* is a collection of related objects.</span></span> <span data-ttu-id="baca4-105">프로젝트는 솔루션 내에 있으며 솔루션은 하나 이상의 프로젝트를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="baca4-105">Projects exist within a solution, which includes one or more projects.</span></span> <span data-ttu-id="baca4-106">자세한 내용은 [Analysis Services 프로젝트 만들기&#40;SSDT&#41;](multidimensional-models/create-an-analysis-services-project-ssdt.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="baca4-106">For more information, see [Create an Analysis Services Project &#40;SSDT&#41;](multidimensional-models/create-an-analysis-services-project-ssdt.md).</span></span>  
  
### <a name="to-create-a-new-analysis-services-project"></a><span data-ttu-id="baca4-107">새 Analysis Services 프로젝트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="baca4-107">To create a new Analysis Services project</span></span>  
  
1.  <span data-ttu-id="baca4-108">**시작**을 클릭하고 **모든 프로그램**, **Microsoft SQL Server 2012**를 차례로 가리킨 후 **SQL Server Data Tools**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="baca4-108">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2012**, and then click **SQL Server Data Tools**.</span></span>  
  
     <span data-ttu-id="baca4-109">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 개발 환경이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="baca4-109">The [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] development environment opens.</span></span>  
  
2.  <span data-ttu-id="baca4-110">[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]시작 페이지에서 **새 프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="baca4-110">On the Start page of [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], click **New Project**.</span></span>  
  
3.  <span data-ttu-id="baca4-111">**새 프로젝트** 대화 상자의 **설치된 템플릿** 창에서 **비즈니스 인텔리전스**를 확장한 다음 **Analysis Services**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="baca4-111">In the **New Project** dialog box, in the **Installed Templates** pane, expand **Business Intelligence**, and then select **Analysis Services**.</span></span> <span data-ttu-id="baca4-112">**Analysis Services 다차원 및 데이터 마이닝 프로젝트** 템플릿을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="baca4-112">Choose the **Analysis Services Multidimensional and Data Mining Project** template.</span></span>  
  
     <span data-ttu-id="baca4-113">기본 프로젝트 이름, 위치 및 기본 솔루션 이름이 대화 상자의 아래쪽에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="baca4-113">Notice the default project name, location, and the default solution name are generated in the bottom of the dialog box.</span></span> <span data-ttu-id="baca4-114">기본적으로 솔루션의 새 디렉터리가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="baca4-114">By default, a new directory is created for the solution.</span></span>  
  
4.  <span data-ttu-id="baca4-115">프로젝트 이름을로 변경 하 여 `Analysis Services Tutorial` **솔루션 이름** 상자도 변경한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="baca4-115">Change the project Name to `Analysis Services Tutorial`, which also changes the **Solution name** box, and then click **OK**.</span></span>  
  
 <span data-ttu-id="baca4-116">`Analysis Services Tutorial`이라는 새 솔루션 내에서 **Analysis Services 다차원 및 데이터 마이닝 프로젝트** 템플릿을 기반으로 프로젝트를 성공적으로 만들었습니다 `Analysis Services Tutorial` .</span><span class="sxs-lookup"><span data-stu-id="baca4-116">You have successfully created the `Analysis Services Tutorial` project, based on the **Analysis Services Multidimensional and Data Mining Project** template, within a new solution that is also named `Analysis Services Tutorial`.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="baca4-117">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="baca4-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="baca4-118">데이터 원본 정의</span><span class="sxs-lookup"><span data-stu-id="baca4-118">Defining a Data Source</span></span>](lesson-1-2-defining-a-data-source.md)  
  
## <a name="see-also"></a><span data-ttu-id="baca4-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="baca4-119">See Also</span></span>  
 <span data-ttu-id="baca4-120">[SQL Server Data Tools &#40;SSDT&#41;를 사용 하 여 다차원 모델 만들기](multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="baca4-120">[Creating Multidimensional Models Using SQL Server Data Tools &#40;SSDT&#41;](multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt.md) </span></span>  
 [<span data-ttu-id="baca4-121">Analysis Services 프로젝트 만들기&#40;SSDT&#41;</span><span class="sxs-lookup"><span data-stu-id="baca4-121">Create an Analysis Services Project &#40;SSDT&#41;</span></span>](multidimensional-models/create-an-analysis-services-project-ssdt.md)  
  
  
