---
title: 외부 도구 대화 상자 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- adding external tools
- external tools [SQL Server Management Studio]
- SQL Server Management Studio [SQL Server], external tools
ms.assetid: ba797203-24d0-4922-9b97-8ab483f1db14
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5789dc150e45c1a0364b7acc0ea7fda443efcf17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733488"
---
# <a name="external-tools-dialog-box"></a><span data-ttu-id="bdfcf-102">외부 도구 대화 상자</span><span class="sxs-lookup"><span data-stu-id="bdfcf-102">External Tools Dialog Box</span></span>
  <span data-ttu-id="bdfcf-103">**외부 도구** 대화 상자를 사용하여 SQLCMD 또는 메모장과 같은 외부 도구를 **도구** 메뉴에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-103">Use the **External Tools** dialog box to add external tools such as SQLCMD or Notepad to the **Tools** menu.</span></span> <span data-ttu-id="bdfcf-104">외부 도구를 추가하면 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 환경에서 작업하는 동안에 다른 애플리케이션을 간편하게 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-104">Adding external tools allows you to easily launch other applications while working in the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] environment.</span></span> <span data-ttu-id="bdfcf-105">도구를 실행할 때 인수 및 작업 디렉터리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-105">You can specify arguments and a working directory when launching the tool.</span></span> <span data-ttu-id="bdfcf-106">또한 일부 도구의 출력을 **출력** 창에 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-106">In addition, the output from some tools can be displayed in the **Output** window.</span></span> <span data-ttu-id="bdfcf-107">**외부 도구** 대화 상자는 **도구** 메뉴에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-107">The **External Tools** dialog box is available on the **Tools** menu.</span></span>  
  
## <a name="options"></a><span data-ttu-id="bdfcf-108">옵션</span><span class="sxs-lookup"><span data-stu-id="bdfcf-108">Options</span></span>  
 <span data-ttu-id="bdfcf-109">**메뉴 내용**</span><span class="sxs-lookup"><span data-stu-id="bdfcf-109">**Menu contents**</span></span>  
 <span data-ttu-id="bdfcf-110">현재 **도구** 메뉴에 추가된 항목의 제목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-110">Lists the titles of the items currently added to the **Tools** menu.</span></span> <span data-ttu-id="bdfcf-111">**위로 이동** 및 **아래로 이동** 화살표를 사용하여 메뉴에 나타나는 항목의 순서를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-111">Use the **Move Up** and **Move Down** arrows to change the order the items that appear on the menu.</span></span> <span data-ttu-id="bdfcf-112">**삭제** 단추를 사용하여 메뉴에서 항목을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-112">Use the **Delete** button to remove an item from the menu.</span></span>  
  
 <span data-ttu-id="bdfcf-113">**위로 이동**</span><span class="sxs-lookup"><span data-stu-id="bdfcf-113">**Move Up**</span></span>  
 <span data-ttu-id="bdfcf-114">선택한 도구를 **도구** 메뉴에 나타나는 도구 목록에서 위로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-114">Move the selected tool higher in the list of tools that appear on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="bdfcf-115">**아래로 이동**</span><span class="sxs-lookup"><span data-stu-id="bdfcf-115">**Move Down**</span></span>  
 <span data-ttu-id="bdfcf-116">선택한 도구를 **도구** 메뉴에 나타나는 도구 목록에서 아래로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-116">Move the selected tool lower in the list of tools that appear on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="bdfcf-117">**추가**</span><span class="sxs-lookup"><span data-stu-id="bdfcf-117">**Add**</span></span>  
 <span data-ttu-id="bdfcf-118">입력란의 내용을 지우고 새 도구를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-118">Clear the text boxes so you can specify a new tool.</span></span>  
  
 <span data-ttu-id="bdfcf-119">**Delete**</span><span class="sxs-lookup"><span data-stu-id="bdfcf-119">**Delete**</span></span>  
 <span data-ttu-id="bdfcf-120">**메뉴 내용** 목록과 **도구** 메뉴에서 도구나 명령을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-120">Remove the tool or command from the **Menu Contents** list as well as from the **Tools** menu.</span></span>  
  
 <span data-ttu-id="bdfcf-121">**제목**</span><span class="sxs-lookup"><span data-stu-id="bdfcf-121">**Title**</span></span>  
 <span data-ttu-id="bdfcf-122">**도구** 메뉴의 **외부 도구** 하위 메뉴에 나타날 도구 또는 명령의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-122">Enter the name of the tool or command that will appear on the **External Tools** submenu of the **Tools** menu.</span></span> <span data-ttu-id="bdfcf-123">특정 문자를 키보드 바로 가기로 지정하려면 도구 이름에서 해당 문자 앞에 앰퍼샌드(&)를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-123">Place an ampersand (&) before a letter in the name of the tool to specify that letter as a keyboard shortcut.</span></span> <span data-ttu-id="bdfcf-124">예를 들어 "&SQLCMD"는 **도구** 메뉴에 SQLCMD를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-124">For example, "&SQLCMD" would display SQLCMD on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="bdfcf-125">**명령**</span><span class="sxs-lookup"><span data-stu-id="bdfcf-125">**Command**</span></span>  
 <span data-ttu-id="bdfcf-126">시작할 파일 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-126">Specify the path to the file to launch.</span></span>  
  
 <span data-ttu-id="bdfcf-127">**인수**</span><span class="sxs-lookup"><span data-stu-id="bdfcf-127">**Arguments**</span></span>  
 <span data-ttu-id="bdfcf-128">메뉴에서 도구를 선택했을 때 도구로 전달되는 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-128">Specify the variables that are passed to the tool when the tool is selected on the menu.</span></span> <span data-ttu-id="bdfcf-129">인수는 도구 또는 명령이 실행될 때 도구 또는 명령에 전달되는 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-129">Arguments can specify values that are passed to the tool or command when it is launched.</span></span> <span data-ttu-id="bdfcf-130">예를 들어 값은 파일 이름 또는 디렉터리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-130">For example, a value can specify a file name or directory.</span></span> <span data-ttu-id="bdfcf-131">화살표 단추를 사용하여 미리 정의된 인수 목록에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-131">Use the arrow button to select from a list of predefined arguments.</span></span> <span data-ttu-id="bdfcf-132">인수를 두 개 이상 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-132">You can add more than one.</span></span> <span data-ttu-id="bdfcf-133">미리 정의된 인수 및 인수 정의의 전체 목록은 [Arguments for External Tools](menu-help/external-tools.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-133">For a complete list of predefined arguments and their definitions, see [Arguments for External Tools](menu-help/external-tools.md).</span></span> <span data-ttu-id="bdfcf-134">사용하는 명령이나 도구에 따라서 명령줄 스위치와 같은 사용자 지정 인수를 입력할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-134">You can also enter custom arguments (for example, command line switches), depending on the command or tool you use.</span></span>  
  
 <span data-ttu-id="bdfcf-135">**출력 창 사용**</span><span class="sxs-lookup"><span data-stu-id="bdfcf-135">**Use Output window**</span></span>  
 <span data-ttu-id="bdfcf-136">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 출력 창을 열어 실행 중인 명령의 출력을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-136">Opens the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] Output window to display output of the command being run.</span></span> <span data-ttu-id="bdfcf-137">모든 도구가 출력 창에 표시되는 형식으로 출력을 제공하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-137">Not all tools present output in a format that can be presented in the Output window.</span></span> <span data-ttu-id="bdfcf-138">자세한 내용은 [출력 창](../relational-databases/scripting/transact-sql-debugger-output-window.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-138">For more information, see [Output Window](../relational-databases/scripting/transact-sql-debugger-output-window.md).</span></span>  
  
 <span data-ttu-id="bdfcf-139">**출력을 유니코드로 처리**</span><span class="sxs-lookup"><span data-stu-id="bdfcf-139">**Treat output as Unicode**</span></span>  
 <span data-ttu-id="bdfcf-140">출력을 유니코드로 해석합니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-140">Interprets the output as Unicode.</span></span>  
  
 <span data-ttu-id="bdfcf-141">**초기 디렉터리**</span><span class="sxs-lookup"><span data-stu-id="bdfcf-141">**Initial directory**</span></span>  
 <span data-ttu-id="bdfcf-142">도구의 작업 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-142">Specify the working directory of the tool.</span></span> <span data-ttu-id="bdfcf-143">화살표 단추를 사용하여 디렉터리를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-143">Use the arrow button to select directories.</span></span> <span data-ttu-id="bdfcf-144">두 개 이상 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-144">You can select more than one.</span></span>  
  
 <span data-ttu-id="bdfcf-145">**인수 확인**</span><span class="sxs-lookup"><span data-stu-id="bdfcf-145">**Prompt for arguments**</span></span>  
 <span data-ttu-id="bdfcf-146">외부 도구를 시작할 때마다 인수의 값을 입력하거나 편집할 수 있도록 **인수** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-146">Display the **Arguments** dialog box to allow you to enter or edit values for the arguments each time you launch the external tool.</span></span>  
  
 <span data-ttu-id="bdfcf-147">**끝낼 때 닫기**</span><span class="sxs-lookup"><span data-stu-id="bdfcf-147">**Close on exit**</span></span>  
 <span data-ttu-id="bdfcf-148">도구를 끝낼 때 도구에 의해 열린 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-148">Close the window opened by the tool when the tool is closed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdfcf-149">예제</span><span class="sxs-lookup"><span data-stu-id="bdfcf-149">Example</span></span>  
 <span data-ttu-id="bdfcf-150">**외부 도구** 대화 상자에 다음 값을 입력하면 "DAC"라는 메뉴 항목이 생성됩니다. 이 메뉴 항목을 선택하면 명령 프롬프트가 열리고 관리자 전용 연결을 사용하여 **sqlcmd** 유틸리티가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-150">Entering the following values in the **External Tools** dialog box will create a menu item labeled "DAC" that when selected, opens a command prompt and runs the **sqlcmd** utility using the dedicated administrator connection.</span></span>  
  
|<span data-ttu-id="bdfcf-151">Box</span><span class="sxs-lookup"><span data-stu-id="bdfcf-151">Box</span></span>|<span data-ttu-id="bdfcf-152">값</span><span class="sxs-lookup"><span data-stu-id="bdfcf-152">Value</span></span>|  
|---------|-----------|  
|<span data-ttu-id="bdfcf-153">**제목**</span><span class="sxs-lookup"><span data-stu-id="bdfcf-153">**Title**</span></span>|<span data-ttu-id="bdfcf-154">DAC</span><span class="sxs-lookup"><span data-stu-id="bdfcf-154">DAC</span></span>|  
|<span data-ttu-id="bdfcf-155">**명령**</span><span class="sxs-lookup"><span data-stu-id="bdfcf-155">**Command**</span></span>|[!INCLUDE[ssInstallPath](../includes/ssinstallpath-md.md)]<span data-ttu-id="bdfcf-156">Tools\Binn\SQLCMD.exe</span><span class="sxs-lookup"><span data-stu-id="bdfcf-156">Tools\Binn\SQLCMD.exe</span></span>|  
|<span data-ttu-id="bdfcf-157">**인수**</span><span class="sxs-lookup"><span data-stu-id="bdfcf-157">**Arguments**</span></span>|<span data-ttu-id="bdfcf-158">-A</span><span class="sxs-lookup"><span data-stu-id="bdfcf-158">-A</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bdfcf-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bdfcf-159">See Also</span></span>  
 <span data-ttu-id="bdfcf-160">[외부 도구에 대 한 인수](menu-help/external-tools.md) </span><span class="sxs-lookup"><span data-stu-id="bdfcf-160">[Arguments for External Tools](menu-help/external-tools.md) </span></span>  
 [<span data-ttu-id="bdfcf-161">일반 사용자 인터페이스 요소</span><span class="sxs-lookup"><span data-stu-id="bdfcf-161">General User Interface Elements</span></span>](general-user-interface-elements.md)  
  
  
