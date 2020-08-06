---
title: 쿼리 편집기로 SQLCMD 스크립트 편집
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], SQLCMD scripts
- SQLCMD scripts
- modifying scripts
- Query Editor [Database Engine], SQLCMD scripts
- scripts [SQL Server], SQL Server Management Studio
ms.assetid: f77b866d-c330-47c9-9e74-0b8d8dff4b31
author: rothja
ms.author: jroth
ms.openlocfilehash: a3466cfc15ea2f4f0c8de5da42f4a1c24c28a575
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651621"
---
# <a name="edit-sqlcmd-scripts-with-query-editor"></a><span data-ttu-id="d20bd-102">쿼리 편집기로 SQLCMD 스크립트 편집</span><span class="sxs-lookup"><span data-stu-id="d20bd-102">Edit SQLCMD Scripts with Query Editor</span></span>
  <span data-ttu-id="d20bd-103">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 쿼리 편집기를 사용하여 쿼리를 SQLCMD 스크립트로 작성 및 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-103">By using the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] you can write and edit queries as SQLCMD scripts.</span></span> <span data-ttu-id="d20bd-104">같은 스크립트에서 Windows 시스템 명령과 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 처리해야 하는 경우 SQLCMD 스크립트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-104">You use SQLCMD scripts when you have to process Windows System commands and [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the same script.</span></span>  
  
## <a name="sqlcmd-mode"></a><span data-ttu-id="d20bd-105">SQLCMD 모드</span><span class="sxs-lookup"><span data-stu-id="d20bd-105">SQLCMD Mode</span></span>  
 <span data-ttu-id="d20bd-106">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기를 사용하여 SQLCMD 스크립트를 작성하거나 편집하려면 SQLCMD 스크립팅 모드를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-106">To use the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor to write or edit SQLCMD scripts, you must enable the SQLCMD scripting mode.</span></span> <span data-ttu-id="d20bd-107">기본적으로 SQLCMD 모드는 쿼리 편집기에서 설정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-107">By default, SQLCMD mode is not enabled in the Query Editor.</span></span> <span data-ttu-id="d20bd-108">도구 모음에서 **SQLCMD 모드** 아이콘을 클릭하거나 **쿼리** 메뉴에서 **SQLCMD 모드** 를 선택하여 스크립팅 모드를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-108">You can enable scripting mode by clicking the **SQLCMD Mode** icon in the toolbar or by selecting **SQLCMD Mode** from the **Query** menu.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d20bd-109">SQLCMD 모드를 설정하면 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리 편집기에서 IntelliSense 및 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 디버거가 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-109">Enabling SQLCMD mode turns off IntelliSense and the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span>  
  
 <span data-ttu-id="d20bd-110">쿼리 편집기에서 SQLCMD 스크립트는 모든 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트가 사용하는 것과 동일한 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-110">SQLCMD scripts in the Query Editor can use the same features that all [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts use.</span></span> <span data-ttu-id="d20bd-111">이러한 기능에는</span><span class="sxs-lookup"><span data-stu-id="d20bd-111">These features include the following:</span></span>  
  
-   <span data-ttu-id="d20bd-112">색 구분</span><span class="sxs-lookup"><span data-stu-id="d20bd-112">Color Coding</span></span>  
  
-   <span data-ttu-id="d20bd-113">스크립트 실행</span><span class="sxs-lookup"><span data-stu-id="d20bd-113">Executing Scripts</span></span>  
  
-   <span data-ttu-id="d20bd-114">소스 제어</span><span class="sxs-lookup"><span data-stu-id="d20bd-114">Source Control</span></span>  
  
-   <span data-ttu-id="d20bd-115">스크립트 구문 분석</span><span class="sxs-lookup"><span data-stu-id="d20bd-115">Parsing Scripts</span></span>  
  
-   <span data-ttu-id="d20bd-116">Showplan</span><span class="sxs-lookup"><span data-stu-id="d20bd-116">Showplan</span></span>  
  
## <a name="enable-sqlcmd-scripting-in-query-editor"></a><span data-ttu-id="d20bd-117">쿼리 편집기에서 SQLCMD 스크립팅 설정</span><span class="sxs-lookup"><span data-stu-id="d20bd-117">Enable SQLCMD Scripting in Query Editor</span></span>  
 <span data-ttu-id="d20bd-118">활성 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기 창에 대해 SQLCMD 스크립팅을 설정하려면 다음 절차를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-118">To turn SQLCMD scripting on for an active [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window, use the following procedure.</span></span>  
  
#### <a name="to-switch-a-database-engine-query-editor-window-to-sqlcmd-mode"></a><span data-ttu-id="d20bd-119">데이터베이스 엔진 쿼리 편집기 창을 SQLCMD 모드로 전환하려면</span><span class="sxs-lookup"><span data-stu-id="d20bd-119">To switch a Database Engine Query Editor window to SQLCMD mode</span></span>  
  
1.  <span data-ttu-id="d20bd-120">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭한 다음 **새 쿼리[!INCLUDE[ssDE](../../includes/ssde-md.md)]를 클릭하여 새** 쿼리 편집기 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-120">In Object Explorer, right-click the server, and then click **New Query**, to open a new [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window.</span></span>  
  
2.  <span data-ttu-id="d20bd-121">**쿼리** 메뉴에서 **SQLCMD 모드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-121">On the **Query** menu, click **SQLCMD Mode**.</span></span>  
  
     <span data-ttu-id="d20bd-122">쿼리 편집기의 컨텍스트에서 **sqlcmd** 문이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-122">The Query Editor executes **sqlcmd** statements in the context of the Query Editor.</span></span>  
  
3.  <span data-ttu-id="d20bd-123">**SQL 편집기** 도구 모음의 **사용 가능한 데이터베이스** 목록에서 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-123">On the **SQL Editor** toolbar, in the **Available Databases** list, select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span>  
  
4.  <span data-ttu-id="d20bd-124">쿼리 편집기 창에 다음 두 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문과 `!!DIR` **sqlcmd** 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-124">In the Query Editor window, type the following two [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and the `!!DIR` **sqlcmd** statement:</span></span>  
  
    ```  
    SELECT DISTINCT Type FROM Sales.SpecialOffer;  
    GO  
    !!DIR  
    GO  
    SELECT ProductCategoryID, Name FROM Production.ProductCategory;  
    GO  
    ```  
  
5.  <span data-ttu-id="d20bd-125">F5 키를 눌러 혼합된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 및 MS-DOS 문의 전체 섹션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-125">Press F5 to execute the whole section of mixed [!INCLUDE[tsql](../../includes/tsql-md.md)] and MS-DOS statements.</span></span>  
  
     <span data-ttu-id="d20bd-126">첫 번째 문과 세 번째 문에서 생성된 두 SQL 결과 창을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-126">Notice the two SQL result panes from the first and third statements.</span></span>  
  
6.  <span data-ttu-id="d20bd-127">**결과** 창에서 **메시지** 탭을 클릭하여 세 문 모두에서 생성된 메시지를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-127">In the **Results** pane, click the **Messages** tab to see the messages from all three statements:</span></span>  
  
    -   <span data-ttu-id="d20bd-128">(6개 행 적용됨)</span><span class="sxs-lookup"><span data-stu-id="d20bd-128">(6 row(s) affected)</span></span>  
  
    -   \<The directory information>  
  
    -   <span data-ttu-id="d20bd-129">(4개 행 적용됨)</span><span class="sxs-lookup"><span data-stu-id="d20bd-129">(4 row(s) affected)</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d20bd-130">명령줄에서 **sqlcmd** 유틸리티를 실행하면 운영 체제와의 전체 상호 작용이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-130">When executed from the command line, the **sqlcmd** utility permits full interaction with the operating system.</span></span> <span data-ttu-id="d20bd-131">**SQLCMD 모드**에서 쿼리 편집기를 사용할 때는 대화형 문을 실행하지 않도록 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-131">When you use the Query Editor in **SQLCMD Mode**, you must be careful not to execute interactive statements.</span></span> <span data-ttu-id="d20bd-132">쿼리 편집기에는 운영 체제 프롬프트에 응답하는 기능이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-132">The Query Editor cannot respond to operating system prompts.</span></span>  
  
 <span data-ttu-id="d20bd-133">SQLCMD 실행 방법은 [sqlcmd Utility](../../tools/sqlcmd-utility.md)를 참조하거나 SQLCMD 자습서를 따라하십시오.</span><span class="sxs-lookup"><span data-stu-id="d20bd-133">For more information about how to run SQLCMD, see [sqlcmd Utility](../../tools/sqlcmd-utility.md), or take the SQLCMD tutorial.</span></span>  
  
## <a name="enable-sqlcmd-scripting-by-default"></a><span data-ttu-id="d20bd-134">SQLCMD 스크립팅을 기본적으로 설정</span><span class="sxs-lookup"><span data-stu-id="d20bd-134">Enable SQLCMD Scripting by Default</span></span>  
 <span data-ttu-id="d20bd-135">SQLCMD 스크립팅을 기본적으로 설정하려면 **도구** 메뉴에서 **옵션**을 선택하고 **쿼리 실행**, **SQL Server**를 차례로 확장한 다음 **일반** 페이지를 클릭하고 **기본적으로 SQLCMD 모드로 새 쿼리를 엽니다.** 상자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-135">To turn SQLCMD scripting on by default, on the **Tools** menu select **Options**, expand **Query Execution**, and **SQL Server**, click the **General** page, and then check the **By default open new queries in SQLCMD Mode** box.</span></span>  
  
## <a name="writing-and-editing-sqlcmd-scripts"></a><span data-ttu-id="d20bd-136">SQLCMD 스크립트 작성 및 편집</span><span class="sxs-lookup"><span data-stu-id="d20bd-136">Writing and Editing SQLCMD Scripts</span></span>  
 <span data-ttu-id="d20bd-137">스크립팅 모드를 설정한 후 SQLCMD 명령과 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-137">After enabling scripting mode you may write SQLCMD commands and [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="d20bd-138">다음 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-138">The following rules apply:</span></span>  
  
-   <span data-ttu-id="d20bd-139">SQLCMD 명령은 줄에서 첫 번째 문이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-139">SQLCMD commands must be the first statement on a line.</span></span>  
  
-   <span data-ttu-id="d20bd-140">각 줄에서 SQLCMD 명령이 하나만 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-140">Only one SQLCMD command is permitted on each line.</span></span>  
  
-   <span data-ttu-id="d20bd-141">SQLCMD 명령은 주석이나 공백 뒤에 올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-141">SQLCMD commands can be preceded by comments or white space.</span></span>  
  
-   <span data-ttu-id="d20bd-142">주석 문자 내의 SQLCMD 명령은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-142">SQLCMD commands within comment characters are not executed.</span></span>  
  
-   <span data-ttu-id="d20bd-143">단일 줄 주석 문자는 두 개의 하이픈(`--)` 이며 줄의 시작 부분에 표시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-143">Single line comment characters are two hyphens (`--)` and must appear at the beginning of a line.</span></span>  
  
-   <span data-ttu-id="d20bd-144">운영 체제 명령은 두 개의 느낌표(`!!`) 뒤에 와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-144">Operating system commands must be preceded by two exclamation points (`!!`).</span></span> <span data-ttu-id="d20bd-145">이중 느낌표 명령은 느낌표 뒤에 있는 문이 `cmd.exe` 명령 처리기를 사용하여 실행되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-145">The double-exclamation points command causes the statement that follows the exclamation points to be executed using the `cmd.exe` command processor.</span></span> <span data-ttu-id="d20bd-146">`!!` 뒤에 있는 텍스트는 매개 변수로 `cmd.exe`에 전달되므로 최종 명령줄은 `"%SystemRoot%\system32\cmd.exe /c <text after !!>"`로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-146">The text after `!!` is passed in as a parameter to `cmd.exe`, so the final command line will execute as: `"%SystemRoot%\system32\cmd.exe /c <text after !!>"`.</span></span>  
  
-   <span data-ttu-id="d20bd-147">SQLCMD 명령과 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 분명하게 구분하기 위해 모든 SQLCMD 명령 앞에 콜론(`:`) 접두사가 와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-147">To make a clear distinction between SQLCMD commands and [!INCLUDE[tsql](../../includes/tsql-md.md)], all SQLCMD commands, need to be prefixed with a colon (`:`).</span></span>  
  
-   <span data-ttu-id="d20bd-148">`GO` 명령은 접두사 없이 사용하거나 앞에 `!!:`</span><span class="sxs-lookup"><span data-stu-id="d20bd-148">The `GO` command may be used without preface, or preceded by `!!:`</span></span>  
  
-   <span data-ttu-id="d20bd-149">이 올 수 있습니다. [!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기는 SQLCMD 스크립트의 일부로 정의된 환경 변수 및 변수를 지원하지만 기본 제공 SQLCMD 또는 **osql** 변수는 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-149">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor supports environment variables and variables that are defined as part of a SQLCMD script, but does not support built-in SQLCMD or **osql** variables.</span></span> <span data-ttu-id="d20bd-150">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 처리하는 SQLCMD는 변수에 대해 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-150">SQLCMD processing by [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is case sensitive for variables.</span></span> <span data-ttu-id="d20bd-151">예를 들어 PRINT '$(COMPUTERNAME)'는 올바른 결과를 생성하는 반면 PRINT '$(ComputerName)'는 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-151">For example, PRINT '$(COMPUTERNAME)' produces the correct result, but PRINT '$(ComputerName)' returns an error.</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="d20bd-152">는 일반 및 SQLCMD 모드에서의 실행을 위해 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]SqlClient를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-152">uses [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]SqlClient for execution in regular and SQLCMD mode.</span></span> <span data-ttu-id="d20bd-153">명령줄에서 실행할 경우 SQLCMD는 OLE DB 공급자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-153">When run from the command line, SQLCMD uses the OLE DB provider.</span></span> <span data-ttu-id="d20bd-154">다른 기본 옵션이 적용될 수 있으므로 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] SQLCMD 모드 및 SQLCMD 유틸리티에서 동일한 쿼리를 실행하는 동안 다른 동작이 수행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-154">Because different default options may apply, it is possible to get different behavior while executing the same query in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] SQLCMD Mode, and in the SQLCMD utility.</span></span>  
  
## <a name="supported-sqlcmd-syntax"></a><span data-ttu-id="d20bd-155">지원되는 SQLCMD 구문</span><span class="sxs-lookup"><span data-stu-id="d20bd-155">Supported SQLCMD Syntax</span></span>  
 <span data-ttu-id="d20bd-156">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기는 다음 SQLCMD 스크립트 키워드를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-156">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor supports the following SQLCMD script keywords:</span></span>  
  
 `[!!:]GO[count]`  
  
 `!! <command>`  
  
 `:exit(statement)`  
  
 `:Quit`  
  
 `:r <filename>`  
  
 `:setvar <var> <value>`  
  
 `:connect server[\instance] [-l login_timeout] [-U user [-P password]]`  
  
 `:on error [ignore|exit]`  
  
 `:error <filename>|stderr|stdout`  
  
 `:out <filename>|stderr|stdout`  
  
> [!NOTE]  
>  <span data-ttu-id="d20bd-157">`:error` 및 `:out`모두에서 `stderr` 및 `stdout` 은 출력을 메시지 탭으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-157">For both `:error` and `:out`, `stderr` and `stdout` send output to the messages tab.</span></span>  
  
 <span data-ttu-id="d20bd-158">위에 나열되지 않은 SQLCMD 명령은 쿼리 편집기에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-158">SQLCMD commands not listed above are not supported in Query Editor.</span></span> <span data-ttu-id="d20bd-159">지원 되지 않는 SQLCMD 키워드가 포함 된 스크립트가 실행 되 면 쿼리 편집기는 \<ignored command*> 지원 되지 않는 각 키워드의 대상에 "명령 무시 \*" 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-159">When a script containing SQLCMD keywords that are not supported is executed, the Query Editor will send an "Ignoring command \*\<ignored command*>" message to the destination for each unsupported keyword.</span></span> <span data-ttu-id="d20bd-160">스크립트가 성공적으로 실행되지만 지원되지 않은 명령은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-160">The script will execute successfully, but the unsupported commands will be ignored.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="d20bd-161">SQLCMD를 명령줄에서 시작하지 않기 때문에 SQLCMD 모드에서 쿼리 편집기를 실행할 때 몇 가지 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-161">Because you are not starting SQLCMD from the command line, there are some limitations when running Query Editor in SQLCMD Mode.</span></span> <span data-ttu-id="d20bd-162">변수와 같은 명령줄 매개 변수를 전달할 수 없으며, 쿼리 편집기는 운영 체제 프롬프트에 응답하는 기능이 없으므로 대화형 문을 실행하지 않도록 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-162">You cannot pass in command-line parameters such as variables, and, because the Query Editor does not have the ability to respond to operating system prompts, you must be careful not to execute interactive statements.</span></span>  
  
## <a name="color-coding-in-sqlcmd-scripts"></a><span data-ttu-id="d20bd-163">SQLCMD 스크립트에서 코드 색 구분</span><span class="sxs-lookup"><span data-stu-id="d20bd-163">Color Coding in SQLCMD Scripts</span></span>  
 <span data-ttu-id="d20bd-164">SQLCMD 스크립팅이 설정되어 있으면 스크립트의 색이 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-164">With SQLCMD scripting enabled, scripts will be color coded.</span></span> <span data-ttu-id="d20bd-165">[!INCLUDE[tsql](../../includes/tsql-md.md)] 키워드에 대한 색 구분은 동일하게 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-165">The color coding for [!INCLUDE[tsql](../../includes/tsql-md.md)] keywords will remain the same.</span></span> <span data-ttu-id="d20bd-166">SQLCMD 명령은 회색 배경과 함께 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-166">SQLCMD commands are presented with a shaded background.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d20bd-167">예제</span><span class="sxs-lookup"><span data-stu-id="d20bd-167">Example</span></span>  
 <span data-ttu-id="d20bd-168">다음 예에서는 **sqlcmd** 문을 사용하여 testoutput.txt 출력 파일을 만들고 [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT 문 두 개와 운영 체제 명령 하나를 실행해 현재 디렉터리를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-168">The following example uses a **sqlcmd** statement to create an output file called testoutput.txt, executes two [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT statements along with one operating system command (to print out the current directory).</span></span> <span data-ttu-id="d20bd-169">결과 파일에는 `DIR` 문의 메시지 출력과 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문의 결과 출력이 차례로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d20bd-169">The resultant file contains the message output from the `DIR` statement, followed by the results output from the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
```  
:out C:\testoutput.txt  
SELECT @@VERSION As 'Server Version'  
!!DIR  
!!:GO  
SELECT @@SERVERNAME AS 'Server Name'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="d20bd-170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d20bd-170">See Also</span></span>  
 [<span data-ttu-id="d20bd-171">sqlcmd 유틸리티</span><span class="sxs-lookup"><span data-stu-id="d20bd-171">sqlcmd Utility</span></span>](../../tools/sqlcmd-utility.md)  
  
  
