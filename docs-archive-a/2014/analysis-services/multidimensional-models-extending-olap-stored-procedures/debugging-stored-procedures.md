---
title: 저장 프로시저 디버깅 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- debugging stored procedures [Analysis Services]
- stored procedures [Analysis Services], debugging
ms.assetid: 34f51b85-02b3-40dd-bf93-375a9e522385
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4f5971fe611f06a413ca48b2bc91237a8c87ee8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732163"
---
# <a name="debugging-stored-procedures"></a><span data-ttu-id="c3655-102">저장 프로시저 디버깅</span><span class="sxs-lookup"><span data-stu-id="c3655-102">Debugging Stored Procedures</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="c3655-103">저장 프로시저는 실제로 C#이나 다른 CLR 또는 COM 언어로 작성되는 CLR 또는 COM 라이브러리(대개 DLL)입니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-103">stored procedures are actually CLR or COM libraries (normally DLLs) that are written in C# (or any other CLR or COM language).</span></span> <span data-ttu-id="c3655-104">따라서 저장 프로시저를 디버깅하는 것은 Visual Studio 디버깅 환경에서 다른 애플리케이션을 디버깅하는 것과 매우 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-104">Therefore, debugging a stored procedure is much like debugging any other application in the Visual Studio debugging environment.</span></span> <span data-ttu-id="c3655-105">통합된 디버깅 기능을 사용하여 Visual Studio 개발 환경에서 저장 프로시저를 디버깅합니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-105">You debug stored procedures in the Visual Studio development environment using the integrated debugging functions.</span></span> <span data-ttu-id="c3655-106">이를 통해 프로시저 위치에서 중지하고 메모리와 레지스터 값을 검사하고 변수를 변경하고 메시지 트래픽을 관찰하고 코드 작동 방식을 자세히 살펴볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-106">These allow you to stop at procedure locations, inspect memory and register values, change variables, observe message traffic and get a close look at how your code works.</span></span>  
  
### <a name="to-debug-a-stored-procedure"></a><span data-ttu-id="c3655-107">저장 프로시저를 디버깅하려면</span><span class="sxs-lookup"><span data-stu-id="c3655-107">To debug a stored procedure</span></span>  
  
1.  <span data-ttu-id="c3655-108">Visual Studio에서 DLL을 만드는 데 사용되는 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-108">Open the project used to create the DLL in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="c3655-109">디버깅할 프로시저에 해당하는 메서드나 함수에 중단점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-109">Create breakpoints in the method or function corresponding to the procedure you want to debug.</span></span>  
  
3.  <span data-ttu-id="c3655-110">Visual Studio를 사용하여 저장 프로시저 DLL의 디버그 빌드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-110">Use Visual Studio to create a debug build of a stored procedure DLL.</span></span>  
  
4.  <span data-ttu-id="c3655-111">서버에 DLL을 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-111">Deploy the DLL to the server.</span></span> <span data-ttu-id="c3655-112">서버에 DLL을 배포 하는 방법에 대 한 자세한 내용은 [저장 프로시저 만들기](creating-stored-procedures.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3655-112">For more information about deploying the DLL to the server, see [Creating Stored Procedures](creating-stored-procedures.md).</span></span>  
  
5.  <span data-ttu-id="c3655-113">테스트할 저장 프로시저를 호출하는 애플리케이션이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-113">You need an application that calls the stored procedure that you want to test.</span></span> <span data-ttu-id="c3655-114">이러한 응용 프로그램이 없는 경우 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 MDX 쿼리 편집기를 사용하여 테스트할 저장 프로시저를 호출하는 MDX 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-114">If you do not have one ready, you can use the MDX Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to create an MDX query that calls the stored procedure that you want to test.</span></span>  
  
6.  <span data-ttu-id="c3655-115">Visual Studio에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로세스(Msmdsrv.exe)에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-115">In Visual Studio, attach to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] process (Msmdsrv.exe).</span></span>  
  
    1.  <span data-ttu-id="c3655-116">**디버그** 메뉴에서 **연결 toprocess**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-116">From the **Debug** menu, choose **Attatch toProcess**.</span></span>  
  
    2.  <span data-ttu-id="c3655-117">**연결 toProcess** 대화 상자에서 **모든 사용자의 프로세스 표시**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-117">In the **Attatch toProcess** dialog box, select **Show processes from all users**.</span></span>  
  
    3.  <span data-ttu-id="c3655-118">**사용 가능한 프로세스** 목록의 **처리** 열에서 **Msmdsrv.exe**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-118">In the **Available Processes** list, in the **Process** column, click **Msmdsrv.exe**.</span></span> <span data-ttu-id="c3655-119">서버에서 실행 중인 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스가 여러 개인 경우 사용할 인스턴스의 ID로 프로세스를 식별해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-119">If there is more than one instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] running on the server, you need to identify the process by the ID of the instance you want to use.</span></span>  
  
    4.  <span data-ttu-id="c3655-120">**연결 대상** 입력란에서 적절 한 프로그램 유형이 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-120">In the **Attach to** text box, make sure that the appropriate program type is selected.</span></span> <span data-ttu-id="c3655-121">CLR DLL의 경우 **선택**을 클릭 하 고 다음 **코드 형식 디버깅**을 클릭 한 다음 **관리**를 클릭 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-121">For a CLR DLL, click **Select**, then click **Debug these code types**, then click **Managed**, then click **OK**.</span></span> <span data-ttu-id="c3655-122">COM DLL의 경우 **선택**을 클릭 하 고 다음 **코드 형식 디버깅**을 클릭 한 다음 **네이티브**를 클릭 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-122">For a COM DLL, click **Select**, then click **Debug these code types**, then click **Native**, then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="c3655-123">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-123">Click **Attach**.</span></span>  
  
7.  <span data-ttu-id="c3655-124">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 저장 프로시저를 호출하는 MDX 스크립트나 프로그램을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-124">In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], invoke the program or MDX script that calls the stored procedure.</span></span> <span data-ttu-id="c3655-125">중단점이 있는 행에 도달하면 디버거가 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-125">The debugger breaks when it reaches a line containing a breakpoint.</span></span> <span data-ttu-id="c3655-126">조사식 창에서 변수를 평가하고 로컬을 보고 코드를 단계별로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-126">You can evaluate variables in the watch window, view locals, and step through the code.</span></span>  
  
 <span data-ttu-id="c3655-127">라이브러리를 디버깅하는 데 문제가 있는 경우 해당 프로그램 데이터베이스(PDB) 파일이 서버의 배포 위치로 복사되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-127">If you have problems debugging a library, make sure that the corresponding program database (PDB) file was copied to the deployment location on the server.</span></span> <span data-ttu-id="c3655-128">등록이나 배포 과정에서 이 파일이 복사되지 않은 경우에는 DLL과 동일한 위치로 직접 파일을 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-128">If this file was not copied during registration or deployment, you must copy it manually to the same location as the DLL.</span></span> <span data-ttu-id="c3655-129">네이티브 코드(COM DLL)의 경우 PDB 파일은 \debug 하위 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-129">For native code (COM DLL), the PDB file resides in the \debug subdirectory.</span></span> <span data-ttu-id="c3655-130">관리 코드(CLR DLL)의 경우 이 파일은 \WINDEBUG 하위 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3655-130">For managed code (CLR DLL), it resides in the \WINDEBUG subdirectory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3655-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c3655-131">See Also</span></span>  
 <span data-ttu-id="c3655-132">[다차원 모델 어셈블리 관리](../multidimensional-models/multidimensional-model-assemblies-management.md) </span><span class="sxs-lookup"><span data-stu-id="c3655-132">[Multidimensional Model Assemblies Management](../multidimensional-models/multidimensional-model-assemblies-management.md) </span></span>  
 [<span data-ttu-id="c3655-133">저장 프로시저 정의</span><span class="sxs-lookup"><span data-stu-id="c3655-133">Defining Stored Procedures</span></span>](defining-stored-procedures.md)  
  
  
