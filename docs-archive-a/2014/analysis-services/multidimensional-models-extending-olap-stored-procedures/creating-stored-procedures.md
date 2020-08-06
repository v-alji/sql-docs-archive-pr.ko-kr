---
title: 저장 프로시저 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- registering assemblies
- database assemblies [Analysis Services]
- server assemblies [Analysis Services]
- stored procedures [Analysis Services], creating
- assemblies [Analysis Services]
ms.assetid: a12ff02f-6d0b-4488-9846-3609fc0d0554
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9a997244a2d54cca8732196107dd21927b5f9e2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732167"
---
# <a name="creating-stored-procedures"></a><span data-ttu-id="4aebe-102">저장 프로시저 만들기</span><span class="sxs-lookup"><span data-stu-id="4aebe-102">Creating Stored Procedures</span></span>
  <span data-ttu-id="4aebe-103">모든 저장 프로시저는 CLR(공용 언어 런타임) 또는 COM(구성 요소 개체 모델) 클래스와 연결되어야 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-103">All stored procedures must be associated with a common language runtime (CLR) or Component Object Model (COM) class in order to be used.</span></span> <span data-ttu-id="4aebe-104">이 클래스는 일반적으로 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX® DLL (동적 연결 라이브러리) 형식으로 서버에 설치 되 고 서버나 데이터베이스에 어셈블리로 등록 되어야 합니다 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4aebe-104">The class must be installed on the server - usually in the form of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX® dynamic link library (DLL) - and registered as an assembly on the server or in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="4aebe-105">저장 프로시저는 서버나 데이터베이스에 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-105">Stored procedures are registered on a server or on a database.</span></span> <span data-ttu-id="4aebe-106">서버 저장 프로시저는 모든 쿼리 컨텍스트에서 호출할 수 있지만</span><span class="sxs-lookup"><span data-stu-id="4aebe-106">Server stored procedures can be called from any query context.</span></span> <span data-ttu-id="4aebe-107">데이터베이스 저장 프로시저는 데이터베이스 컨텍스트가 저장 프로시저가 정의되어 있는 데이터베이스인 경우에만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-107">Database stored procedures can only be accessed if the database context is the database under which the stored procedure is defined.</span></span> <span data-ttu-id="4aebe-108">한 어셈블리의 함수에서 다른 어셈블리의 함수를 호출하는 경우 두 어셈블리를 모두 동일한 컨텍스트(서버 또는 데이터베이스)에 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-108">If functions in one assembly call functions in a different assembly, you must register both assemblies in the same context (server or database).</span></span> <span data-ttu-id="4aebe-109">서버 또는 서버에 배포 된 데이터베이스의 경우를 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 사용 하 여 어셈블리를 등록할 수 있습니다 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4aebe-109">For a server or a deployed [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database on a server, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to register an assembly.</span></span> <span data-ttu-id="4aebe-110">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트의 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 디자이너를 사용하여 프로젝트에 어셈블리를 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-110">For an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, you can use [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Designer to register an assembly in the project.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4aebe-111">COM 어셈블리는 보안 위험을 내포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-111">COM assemblies might pose a security risk.</span></span> <span data-ttu-id="4aebe-112">이러한 위험 및 기타 고려 사항으로 인해 COM 어셈블리는 [!INCLUDE[ssASversion10](../../includes/ssasversion10-md.md)]에서 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-112">Due to this risk and other considerations, COM assemblies were deprecated in [!INCLUDE[ssASversion10](../../includes/ssasversion10-md.md)].</span></span> <span data-ttu-id="4aebe-113">COM 어셈블리는 후속 릴리스에서 지원되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-113">COM assemblies might not be supported in future releases.</span></span>  
  
## <a name="registering-a-server-assembly"></a><span data-ttu-id="4aebe-114">서버 어셈블리 등록</span><span class="sxs-lookup"><span data-stu-id="4aebe-114">Registering a Server Assembly</span></span>  
 <span data-ttu-id="4aebe-115">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 개체 탐색기에서 서버 어셈블리는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스 아래의 어셈블리 폴더에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-115">In Object Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], server assemblies are listed in the Assemblies folder under an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="4aebe-116">서버 어셈블리는 .NET(CLR) 어셈블리와 COM 라이브러리를 모두 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-116">Server assemblies can contain both .NET (CLR) assemblies and COM libraries.</span></span>  
  
### <a name="to-create-a-server-assembly"></a><span data-ttu-id="4aebe-117">서버 어셈블리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="4aebe-117">To create a server assembly</span></span>  
  
1.  <span data-ttu-id="4aebe-118">개체 탐색기에서 인스턴스를 확장 하 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 고 **어셈블리** 폴더를 마우스 오른쪽 단추로 클릭 한 다음 **새 어셈블리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-118">Expand the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in Object Explorer, right-click the **Assemblies** folder, and then click **New Assembly**.</span></span> <span data-ttu-id="4aebe-119">그러면 **서버 어셈블리 등록** 대화 상자가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-119">This displays the **Register Server Assembly** dialog box.</span></span>  
  
2.  <span data-ttu-id="4aebe-120">**유형** 에 대해 어셈블리 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-120">For **Type** specify the type of assembly:</span></span>  
  
    -   <span data-ttu-id="4aebe-121">관리 코드(CLR) DLL의 경우 .NET 어셈블리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-121">For a managed code (CLR) DLL, specify .NET Assembly.</span></span>  
  
    -   <span data-ttu-id="4aebe-122">네이티브 코드(COM) DLL의 경우 COM DLL을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-122">For a native code (COM) DLL, specify COM DLL.</span></span>  
  
3.  <span data-ttu-id="4aebe-123">**파일 이름**에 저장 프로시저를 포함 하는 DLL을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-123">For **File name**, specify the DLL containing the stored procedures.</span></span>  
  
4.  <span data-ttu-id="4aebe-124">**어셈블리 이름**에 어셈블리의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-124">For **Assembly name**, specify a name for the assembly.</span></span>  
  
5.  <span data-ttu-id="4aebe-125">저장 프로시저를 디버깅 하는 데 사용 하려는 라이브러리의 디버그 빌드 인 경우 **디버그 정보 포함** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-125">If this is a debug build of the library that you are going to use to debug stored procedures, select the **Include debug information** check box.</span></span> <span data-ttu-id="4aebe-126">저장 프로시저를 디버깅 하는 방법에 대 한 자세한 내용은 [저장 프로시저 디버깅](debugging-stored-procedures.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="4aebe-126">For more information about debugging stored procedures, see [Debugging Stored Procedures](debugging-stored-procedures.md).</span></span>  
  
6.  <span data-ttu-id="4aebe-127">**확인** 을 클릭 하 여 어셈블리를 즉시 등록 하거나 대화 상자 도구 모음에서 **스크립트** 메뉴의 명령을 클릭 하 여 등록 작업을 쿼리 창, 파일 또는 클립보드에 스크립팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-127">You can click **OK** to register the assembly immediately, or on the dialog box toolbar, you can click a command on the **Script** menu to script the registration action to a query window, a file, or the Clipboard.</span></span>  
  
 <span data-ttu-id="4aebe-128">서버 어셈블리를 등록 한 후 개체 탐색기에서 어셈블리를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 하 여 서버 어셈블리를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-128">After you register a server assembly, you can configure it by right-clicking the assembly in Object Explorer and then clicking **Properties**.</span></span>  
  
## <a name="registering-a-database-assembly-on-the-server"></a><span data-ttu-id="4aebe-129">서버에서 데이터베이스 어셈블리 등록</span><span class="sxs-lookup"><span data-stu-id="4aebe-129">Registering a Database Assembly on the Server</span></span>  
 <span data-ttu-id="4aebe-130">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 개체 탐색기에서 데이터베이스 어셈블리는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스 아래의 어셈블리 폴더에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-130">In Object Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], database assemblies are listed in the Assemblies folder under an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="4aebe-131">데이터베이스 어셈블리는 .NET(CLR) 어셈블리와 COM 라이브러리를 모두 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-131">Database assemblies can contain both .NET (CLR) assemblies and COM libraries.</span></span>  
  
### <a name="to-create-a-database-assembly-on-a-server"></a><span data-ttu-id="4aebe-132">서버에서 데이터베이스 어셈블리를 등록하려면</span><span class="sxs-lookup"><span data-stu-id="4aebe-132">To create a database assembly on a server</span></span>  
  
1.  <span data-ttu-id="4aebe-133">개체 탐색기에서 데이터베이스 인스턴스를 확장 하 고 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] **어셈블리** 폴더를 마우스 오른쪽 단추로 클릭 한 다음 **새 어셈블리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-133">Expand the instance the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in Object Explorer, right-click the **Assemblies** folder, and then click **New Assembly**.</span></span> <span data-ttu-id="4aebe-134">**데이터베이스 어셈블리 등록** 대화 상자가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-134">This displays the **Register Database Assembly** dialog box.</span></span>  
  
2.  <span data-ttu-id="4aebe-135">**유형** 에 대해 어셈블리 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-135">For **Type** specify the type of assembly:</span></span>  
  
    -   <span data-ttu-id="4aebe-136">관리 코드(CLR) DLL의 경우 .NET 어셈블리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-136">For a managed code (CLR) DLL, specify .NET Assembly.</span></span>  
  
    -   <span data-ttu-id="4aebe-137">네이티브 코드(COM) DLL의 경우 COM DLL을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-137">For a native code (COM) DLL), specify COM DLL.</span></span>  
  
3.  <span data-ttu-id="4aebe-138">**파일 이름**에 저장 프로시저를 포함 하는 DLL을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-138">For **File name**, specify the DLL containing the stored procedures.</span></span>  
  
4.  <span data-ttu-id="4aebe-139">**어셈블리 이름**에 어셈블리의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-139">For **Assembly name**, specify a name for the assembly.</span></span>  
  
5.  <span data-ttu-id="4aebe-140">저장 프로시저를 디버깅 하는 데 사용 하려는 라이브러리의 디버그 빌드 인 경우 **디버그 정보 포함** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-140">If this is a debug build of the library that you are going to use to debug stored procedures, select the **Include debug information** check box.</span></span> <span data-ttu-id="4aebe-141">저장 프로시저를 디버깅 하는 방법에 대 한 자세한 내용은 [저장 프로시저 디버깅](debugging-stored-procedures.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="4aebe-141">For more information about debugging stored procedures, see [Debugging Stored Procedures](debugging-stored-procedures.md).</span></span>  
  
6.  <span data-ttu-id="4aebe-142">**확인** 을 클릭 하 여 어셈블리를 즉시 등록 하거나 대화 상자 도구 모음에서 **스크립트** 메뉴의 명령을 클릭 하 여 등록 작업을 쿼리 창, 파일 또는 클립보드에 스크립팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-142">You can click **OK** to register the assembly immediately, or on the dialog box toolbar, you can click a command on the **Script** menu to script the registration action to a query window, a file, or the Clipboard.</span></span>  
  
 <span data-ttu-id="4aebe-143">데이터베이스 어셈블리를 등록 한 후 개체 탐색기에서 어셈블리를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 하 여 데이터베이스 어셈블리를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-143">After you register a database assembly, you can configure it by right-clicking the assembly in Object Explorer and then clicking **Properties**.</span></span>  
  
## <a name="registering-a-database-assembly-in-a-project"></a><span data-ttu-id="4aebe-144">프로젝트에 데이터베이스 어셈블리 등록</span><span class="sxs-lookup"><span data-stu-id="4aebe-144">Registering a Database Assembly in a Project</span></span>  
 <span data-ttu-id="4aebe-145">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 솔루션 탐색기에서 데이터베이스 어셈블리는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트 아래의 어셈블리 폴더에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-145">In Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], database assemblies are listed in the Assemblies folder under an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="4aebe-146">데이터베이스 어셈블리는 .NET(CLR) 어셈블리와 COM 라이브러리를 모두 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-146">Database assemblies can contain both .NET (CLR) assemblies and COM libraries.</span></span>  
  
### <a name="to-create-a-database-assembly-in-an-analysis-service-project"></a><span data-ttu-id="4aebe-147">Analysis Service 프로젝트에서 데이터베이스 어셈블리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="4aebe-147">To create a database assembly in an Analysis Service project</span></span>  
  
1.  <span data-ttu-id="4aebe-148">개체 탐색기에서 데이터베이스 인스턴스를 확장 하 고 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] **어셈블리** 폴더를 마우스 오른쪽 단추로 클릭 한 다음 **새 어셈블리 참조**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-148">Expand the instance the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in Object Explorer, right-click the **Assemblies** folder, and then click **New Assembly Reference**.</span></span> <span data-ttu-id="4aebe-149">**참조 추가** 대화 상자가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-149">This displays the **Add Reference** dialog box.</span></span> <span data-ttu-id="4aebe-150">**참조 추가** 대화 상자의 **.net** 탭에는 기존 .net (CLR) 어셈블리가 나열 되 고 **프로젝트** 탭에는 프로젝트가 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-150">The **.NET** tab of the **Add Reference** dialog box lists existing .NET (CLR) assemblies, while the **Projects** tab lists projects.</span></span>  
  
2.  <span data-ttu-id="4aebe-151">기존 구성 요소나 프로젝트를 클릭 한 다음 **추가** 를 클릭 하 여 프로젝트에 추가할 수 있습니다 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4aebe-151">You can click an existing component or project and then click **Add** to add it to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="4aebe-152">COM DLL에 대 한 참조를 추가 하려면 **찾아보기** 탭을 클릭 하 여 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-152">To add a reference to a COM DLL, click the **Browse** tab to find the file.</span></span> <span data-ttu-id="4aebe-153">**선택한 프로젝트 및 구성 요소** 목록에는 프로젝트에 추가할 각 구성 요소의 이름, 유형, 버전 및 위치가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-153">The **Selected projects and components** list shows the name, type, version, and location for each component that you are adding to the project.</span></span>  
  
3.  <span data-ttu-id="4aebe-154">추가할 구성 요소를 모두 선택 했으면 **확인** 을 클릭 하 여 프로젝트에 추가 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-154">When you are finished selecting components to add, click **OK** to add them to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span>  
  
## <a name="script-format-for-an-assembly"></a><span data-ttu-id="4aebe-155">어셈블리 스크립트 형식</span><span class="sxs-lookup"><span data-stu-id="4aebe-155">Script Format For an Assembly</span></span>  
 <span data-ttu-id="4aebe-156">.NET 어셈블리 등록 과정은 매우 단순합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-156">Registering a .NET assembly is fairly simple.</span></span> <span data-ttu-id="4aebe-157">.NET 어셈블리는 다음 형식을 사용하여 이진 형식으로 데이터베이스에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="4aebe-157">A .NET assembly is added to a database in binary format using the following format:</span></span>  
  
```  
<Create>  
   <ObjectDefinition>  
      <Assembly>  
         <Files>  
            <File>  
               <Name>filename</Name>  
               <Type>filetype</Type>  
               <Data>  
                  <Block>binarydatablock</Block>  
                  <Block>binarydatablock</Block>  
                  ...  
               </Data>  
            </File>  
         </Files>  
         <PermissionSet>PermissionSet</PermissionSet>  
      </Assembly>  
   <ObjectDefinition>  
</Create>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4aebe-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4aebe-158">See Also</span></span>  
 <span data-ttu-id="4aebe-159">[다차원 모델 어셈블리 관리](../multidimensional-models/multidimensional-model-assemblies-management.md) </span><span class="sxs-lookup"><span data-stu-id="4aebe-159">[Multidimensional Model Assemblies Management](../multidimensional-models/multidimensional-model-assemblies-management.md) </span></span>  
 [<span data-ttu-id="4aebe-160">저장 프로시저 정의</span><span class="sxs-lookup"><span data-stu-id="4aebe-160">Defining Stored Procedures</span></span>](defining-stored-procedures.md)  
  
  
