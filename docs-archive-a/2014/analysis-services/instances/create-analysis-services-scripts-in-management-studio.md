---
title: Management Studio에서 Analysis Services 스크립트 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services objects, scripts
- objects [Analysis Services], scripts
- scripts [Analysis Services], objects
ms.assetid: 4f1b965c-9ca6-427b-8f4d-0ce1eea7c0fe
author: minewiskan
ms.author: owend
ms.openlocfilehash: bb380e271510ea5a35860d4850bfaeed3aad8cf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731083"
---
# <a name="create-analysis-services-scripts-in-management-studio"></a><span data-ttu-id="05dfa-102">Management Studio에서 Analysis Services 스크립트 만들기</span><span class="sxs-lookup"><span data-stu-id="05dfa-102">Create Analysis Services Scripts in Management Studio</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="05dfa-103">에는 Analysis Services 개체 및 태스크를 스크립팅하는 데 사용할 수 있는 스크립트 생성 기능, 템플릿 및 편집기가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-103">includes script generation features, templates, and editors that you can use to script Analysis Services objects and tasks.</span></span>  
  
## <a name="script-analysis-services-tasks-in-management-studio"></a><span data-ttu-id="05dfa-104">Management Studio에서 Analysis Services 태스크 스크립팅</span><span class="sxs-lookup"><span data-stu-id="05dfa-104">Script Analysis Services Tasks in Management Studio</span></span>  
 <span data-ttu-id="05dfa-105">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서는 태스크 지향 대화 상자에서 스크립트 옵션 중 하나를 클릭하여 태스크를 스크립팅합니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-105">Scripting tasks in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is accomplished by clicking one of the Script options in a task-oriented dialog box.</span></span> <span data-ttu-id="05dfa-106">데이터베이스 백업 또는 복원, 개체 처리, 집계 디자인과 같은 태스크를 수행하는 데 사용하는 모든 대화 상자에는 맨 위에 스크립트 옵션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-106">All of the dialog boxes that you use to perform tasks such as backup or restore database, process an object, or design an aggregation, include a Script option at the top of the dialog box.</span></span> <span data-ttu-id="05dfa-107">이러한 옵션 중 하나를 선택하면 대화 상자의 정보 및 설정을 기반으로 XMLA 스크립트가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-107">Selecting one of these options generates an XMLA script based on the information and settings in the dialog box.</span></span>  
  
 <span data-ttu-id="05dfa-108">기본적으로 스크립트는 생성된 후 XMLA 쿼리 편집기에 배치되지만 스크립트 옵션 목록을 확장하여 스크립트를 Windows 클립보드 또는 파일로 보낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-108">By default, the script is generated and placed in an XMLA query editor, but you can also expand the Script option list to direct the script to the Windows Clipboard or a file.</span></span>  
  
#### <a name="to-script-an-analysis-services-task"></a><span data-ttu-id="05dfa-109">Analysis Services 태스크를 스크립팅하려면</span><span class="sxs-lookup"><span data-stu-id="05dfa-109">To script an Analysis Services task</span></span>  
  
1.  <span data-ttu-id="05dfa-110">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-110">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="05dfa-111">데이터베이스를 마우스 오른쪽 단추로 클릭하고 **백업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-111">Right-click a database and click **Backup**.</span></span> <span data-ttu-id="05dfa-112">데이터베이스 백업 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-112">This opens the Backup Database dialog box.</span></span> <span data-ttu-id="05dfa-113">백업 파일 이름을 지정하고 이 백업에 사용할 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-113">Specify a backup file name and choose the options you want for this backup.</span></span>  
  
3.  <span data-ttu-id="05dfa-114">대화 상자 맨 위에서 **스크립트** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-114">Click **Script** at the top of the dialog box.</span></span> <span data-ttu-id="05dfa-115">스크립트 기능은 Management Studio에 있는 모든 태스크 기반 대화 상자의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-115">The Script feature is part of all task-based dialog boxes in Management Studio.</span></span> <span data-ttu-id="05dfa-116">쿼리 편집기 창을 여는 **새 쿼리 창 동작 스크립팅** , XMLA 스크립트를 파일로 저장하는 **파일 동작 스크립팅** 또는 XMLA 스크립트를 클립보드로 저장하는 **클립보드 동작 스크립팅** 과 같은 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-116">It has the following options: **Script Action to New Query Window** to open the query editor window, **Script Action to File** to save the XMLA script to a file, or **Script Action to Clipboard** to save the XMLA script to the Clipboard.</span></span>  
  
     <span data-ttu-id="05dfa-117">Management Studio에서 스크립트 옵션으로 표시되는 **작업 동작 스크립팅** 옵션은 Analysis Services 스크립트에 대해서는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-117">Note that the **Script Action to Job** option that is listed as a script option in Management Studio is not supported for Analysis Services scripts.</span></span>  
  
4.  <span data-ttu-id="05dfa-118">기본 옵션인 **새 쿼리 창 동작 스크립팅**을 선택하면 생성된 스크립트가 XMLA 쿼리 창에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-118">If you select the default option, **Script Action to New Query Window**, a generated script is placed in an XMLA query window.</span></span>  
  
     <span data-ttu-id="05dfa-119">이제 데이터베이스 백업 대화 상자를 닫고 XMLA 스크립트를 직접 편집하거나 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-119">You can now close the Backup Database dialog box and edit or run the XMLA script directly.</span></span>  
  
## <a name="script-analysis-services-objects-in-management-studio"></a><span data-ttu-id="05dfa-120">Management Studio에서 Analysis Services 개체 스크립팅</span><span class="sxs-lookup"><span data-stu-id="05dfa-120">Script Analysis Services Objects in Management Studio</span></span>  
 <span data-ttu-id="05dfa-121">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체를 마우스 오른쪽 단추로 클릭하고 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] CREATE **,** ALTER **또는**DELETE **를 선택하여**의 개체를 스크립팅합니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-121">Scripting objects in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is accomplished by right-clicking an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and selecting either **Create to**, **Alter to**, or **Delete to**.</span></span> <span data-ttu-id="05dfa-122">이러한 각 옵션을 창이나 파일로 전송할 수 있지만 스크립트는 전송되는 위치에 관계없이 XMLA 래퍼의 DDL 스크립트 형태를 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-122">Each of these options can be directed to a window or a file, but regardless of where the script is directed to, it will come in the form of a DDL script in an XMLA wrapper.</span></span> <span data-ttu-id="05dfa-123">이러한 스크립트의 가장 큰 장점은 모든 대상 서버에서 스크립트를 실행할 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-123">One great advantage to such scripts is that they can be run against any server you point them at.</span></span> <span data-ttu-id="05dfa-124">또한 스크립트에서 이름을 변경할 수 있고 반복적으로 실행하여 개체를 대량으로 생성, 변경 또는 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-124">Also, names in the scripts can be changed and run on an iterative basis for mass construction, alteration, or deletion of objects.</span></span>  
  
 <span data-ttu-id="05dfa-125">스크립팅할 수 있는 개체에는 데이터 원본, 데이터 원본 뷰, 큐브, 차원, 마이닝 구조 및 역할 등의 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스 요소가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-125">Objects that you can script include the elements of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, including data sources, data source views, cubes, dimensions, mining structures, and roles.</span></span>  
  
 <span data-ttu-id="05dfa-126">사전에 XMLA(XML for Analysis)를 이해하고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-126">Prerequisites include an understanding of XML for Analysis (XMLA).</span></span> <span data-ttu-id="05dfa-127">다행히 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에는 큐브 등의 개체를 만드는 데 필요한 XMLA 스크립트를 자동으로 만드는 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-127">Fortunately, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] has a feature that automatically creates the XMLA script required to create objects, such as cubes.</span></span> <span data-ttu-id="05dfa-128">이 자동화 기능을 이용하면 XMLA를 배우는 데 드는 시간과 노력을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-128">This automation feature helps reduce the learning curve for XMLA.</span></span> <span data-ttu-id="05dfa-129">XMLA를 사용하는 방법에 대한 자세한 내용은 [Analysis Services에서 XMLA를 사용하여 개발](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="05dfa-129">For more information about how to use XMLA, see [Developing with XMLA in Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md).</span></span> <span data-ttu-id="05dfa-130">XMLA를 사용하는 방법에 대한 자세한 내용은 [Analysis Services에서 XMLA를 사용하여 개발](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="05dfa-130">For more information about how to use XMLA, see [Developing with XMLA in Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="05dfa-131">역할 개체를 스크립팅할 때 보안 권한은 연관된 보안 역할이 아니라 해당 권한이 보안을 설정하는 개체에 포함되어 있다는 사실에 유의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-131">When scripting the Role Object, be aware that security permissions are contained by the objects they secure rather than with the security role with which they are associated.</span></span>  
  
#### <a name="to-script-analysis-services-objects"></a><span data-ttu-id="05dfa-132">Analysis Services 개체를 스크립팅하려면</span><span class="sxs-lookup"><span data-stu-id="05dfa-132">To script Analysis Services objects</span></span>  
  
1.  <span data-ttu-id="05dfa-133">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-133">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="05dfa-134">개체 작성, 변경 또는 삭제 스크립트를 만들 개체를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-134">Locate the object for which you want to create a script that either creates, alters, or deletes objects.</span></span>  
  
3.  <span data-ttu-id="05dfa-135">개체를 마우스 오른쪽 단추로 클릭하고 **큐브 스크립팅**, **CREATE**, **ALTER**또는 **DELETE**를 차례로 가리킨 후 다음 옵션 중 하나를 클릭합니다. 쿼리 편집기 창을 열려면 **새 쿼리 편집기 창** , XMLA 스크립트를 파일에 저장하려면 **파일** , XMLA 스크립트를 클립보드에 저장하려면 **클립보드** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-135">Right-click the object, point to **Script Cube as**, point to **CREATE To**, **ALTER To**, or **Delete To**, and then click one of the following options: **New Query Editor Window** to open the query editor window, **File** to save the XMLA script to a file, or **Clipboard** to save the XMLA script to the Clipboard.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="05dfa-136">일반적으로 버전이 다른 파일을 여러 개 만들려면 **파일** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="05dfa-136">Typically, you would select **File** if you want to create multiple different versions of the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05dfa-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="05dfa-137">See Also</span></span>  
 <span data-ttu-id="05dfa-138">[Analysis Services에서 관리 태스크 스크립팅](../script-administrative-tasks-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="05dfa-138">[Script Administrative Tasks in Analysis Services](../script-administrative-tasks-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="05dfa-139">XMLA 쿼리 편집기&#40;Analysis Services - 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="05dfa-139">XMLA Query Editor &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../xmla-query-editor-analysis-services-multidimensional-data.md)  
  
  
