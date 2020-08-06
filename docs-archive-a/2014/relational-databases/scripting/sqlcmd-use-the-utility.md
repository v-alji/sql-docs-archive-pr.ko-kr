---
title: sqlcmd 유틸리티 사용
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- Transact-SQL statements, executing
- command prompt utilities [SQL Server], sqlcmd
- statements [SQL Server], executing
- sqlcmd utility, about sqlcmd utility
ms.assetid: 3ec89119-7314-43ef-9e91-12e72bb63d62
author: rothja
ms.author: jroth
ms.openlocfilehash: 922f9915272fb2d7fc63487ec135ce44ee91e88b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653258"
---
# <a name="use-the-sqlcmd-utility"></a><span data-ttu-id="fe9f6-102">sqlcmd 유틸리티 사용</span><span class="sxs-lookup"><span data-stu-id="fe9f6-102">Use the sqlcmd Utility</span></span>
  <span data-ttu-id="fe9f6-103">`sqlcmd` 유틸리티는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문 및 스크립트의 임시 대화형 실행과 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립팅 태스크의 자동화를 위한 명령줄 유틸리티입니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-103">The `sqlcmd` utility is a command-line utility for ad hoc, interactive execution of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and scripts and for automating [!INCLUDE[tsql](../../includes/tsql-md.md)] scripting tasks.</span></span> <span data-ttu-id="fe9f6-104">`sqlcmd`를 대화형으로 사용하거나 `sqlcmd`를 사용하여 실행할 스크립트 파일을 작성하려면 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-104">To use `sqlcmd` interactively, or to build script files to be run using `sqlcmd`, users must understand [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="fe9f6-105">일반적으로 `sqlcmd` 유틸리티는 다음과 같은 방법으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-105">The `sqlcmd` utility is typically used in the following ways:</span></span>  
  
-   <span data-ttu-id="fe9f6-106">명령 프롬프트에서와 비슷한 방법으로 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 대화형으로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-106">Users interactively enter [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in a manner similar to working at the command prompt.</span></span> <span data-ttu-id="fe9f6-107">결과는 명령 프롬프트에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-107">The results are displayed at the command prompt.</span></span> <span data-ttu-id="fe9f6-108">명령 프롬프트 창을 열려면 **시작**, **모든 프로그램**을 차례로 클릭하고 **보조프로그램**을 가리킨 다음 **명령 프롬프트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-108">To open a Command Prompt window, click **Start**, click **All Programs**, point to **Accessories**, and then click **Command Prompt**.</span></span> <span data-ttu-id="fe9f6-109">명령 프롬프트에서 `sqlcmd`를 입력한 뒤 원하는 옵션을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-109">At the command prompt, type `sqlcmd` followed by a list of options that you want.</span></span> <span data-ttu-id="fe9f6-110">에서 지 원하는 옵션의 전체 목록은 `sqlcmd` [sqlcmd 유틸리티](../../tools/sqlcmd-utility.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-110">For a complete list of the options that are supported by `sqlcmd`, see [sqlcmd Utility](../../tools/sqlcmd-utility.md).</span></span>  
  
-   <span data-ttu-id="fe9f6-111">실행할 단일 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 지정하거나 실행할 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문이 포함된 텍스트 파일을 유틸리티에 알려 `sqlcmd` 작업을 제출합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-111">Users submit a `sqlcmd` job either by specifying a single [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to execute, or by pointing the utility to a text file that contains [!INCLUDE[tsql](../../includes/tsql-md.md)] statements to execute.</span></span> <span data-ttu-id="fe9f6-112">결과는 일반적으로 텍스트 파일로 전송되지만 명령 프롬프트에 표시될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-112">The output is usually directed to a text file, but it can also be displayed at the command prompt.</span></span>  
  
-   <span data-ttu-id="fe9f6-113">[쿼리 편집기의](edit-sqlcmd-scripts-with-query-editor.md) SQLCMD 모드 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe9f6-113">[SQLCMD mode](edit-sqlcmd-scripts-with-query-editor.md) in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor.</span></span>  
  
-   <span data-ttu-id="fe9f6-114">SMO(SQL Server 관리 개체)</span><span class="sxs-lookup"><span data-stu-id="fe9f6-114">SQL Server Management Objects (SMO)</span></span>  
  
-   <span data-ttu-id="fe9f6-115">SQL Server 에이전트 CmdExec 작업</span><span class="sxs-lookup"><span data-stu-id="fe9f6-115">SQL Server Agent CmdExec jobs.</span></span>  
  
## <a name="typically-used-sqlcmd-options"></a><span data-ttu-id="fe9f6-116">일반적으로 사용되는 sqlcmd 옵션</span><span class="sxs-lookup"><span data-stu-id="fe9f6-116">Typically Used sqlcmd Options</span></span>  
 <span data-ttu-id="fe9f6-117">가장 일반적으로 사용되는 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-117">The following options are used most frequently:</span></span>  
  
-   <span data-ttu-id="fe9f6-118">가 연결 하는 인스턴스를 식별 하는 서버 옵션 (**-S**)입니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `sqlcmd` .</span><span class="sxs-lookup"><span data-stu-id="fe9f6-118">The server option (**-S**) that identifies the instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to which `sqlcmd` connects.</span></span>  
  
-   <span data-ttu-id="fe9f6-119">에서 인스턴스에 연결 하는 데 사용 하는 자격 증명을 지정 하는 인증 옵션 (**-E**, **-U**및 **-P**) `sqlcmd` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe9f6-119">Authentication options (**-E**, **-U**, and **-P**) that specify the credentials that `sqlcmd` uses to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fe9f6-120">**-E** 옵션은 기본값이므로 따로 지정하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-120">The **-E** option is the default and does not have to be specified.</span></span>  
  
-   <span data-ttu-id="fe9f6-121">입력의 위치를 식별 하는 입력 옵션 (**-q**, **-q**및 **-i**) `sqlcmd`</span><span class="sxs-lookup"><span data-stu-id="fe9f6-121">Input options (**-Q**, **-q**, and **-i**) that identify the location of the input to `sqlcmd`.</span></span>  
  
-   <span data-ttu-id="fe9f6-122">가 출력을 저장할 파일을 지정 하는 출력 옵션 (**-o**)입니다 `sqlcmd` .</span><span class="sxs-lookup"><span data-stu-id="fe9f6-122">The output option (**-o**) that specifies the file in which `sqlcmd` is to put its output.</span></span>  
  
## <a name="connecting-to-the-sqlcmd-utility"></a><span data-ttu-id="fe9f6-123">sqlcmd 유틸리티에 연결</span><span class="sxs-lookup"><span data-stu-id="fe9f6-123">Connecting to the sqlcmd Utility</span></span>  
 <span data-ttu-id="fe9f6-124">`sqlcmd` 유틸리티의 일반적인 용도는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-124">The following are common uses of the `sqlcmd` utility:</span></span>  
  
-   <span data-ttu-id="fe9f6-125">[!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 대화형으로 실행하기 위해 Windows 인증을 사용하여 기본 인스턴스에 연결</span><span class="sxs-lookup"><span data-stu-id="fe9f6-125">Connecting to a default instance by using Windows Authentication to interactively run [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    sqlcmd -S <ComputerName>  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="fe9f6-126">이전 예에서 **-E** 는 기본값 이므로 `sqlcmd` Windows 인증을 사용 하 여 기본 인스턴스에 연결 하므로 지정 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-126">In the previous example, **-E** is not specified because it is the default and `sqlcmd` connects to the default instance by using Windows Authentication.</span></span>  
  
-   <span data-ttu-id="fe9f6-127">[!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 대화형으로 실행하기 위해 Windows 인증을 사용하여 명명된 인스턴스에 연결</span><span class="sxs-lookup"><span data-stu-id="fe9f6-127">Connecting to a named instance by using Windows Authentication to interactively run [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    sqlcmd -S <ComputerName>\<InstanceName>  
    ```  
  
     <span data-ttu-id="fe9f6-128">를 실행하거나</span><span class="sxs-lookup"><span data-stu-id="fe9f6-128">or</span></span>  
  
    ```  
    sqlcmd -S .\<InstanceName>  
    ```  
  
-   <span data-ttu-id="fe9f6-129">Windows 인증을 사용하고 입력 및 출력 파일을 지정하여 명명된 인스턴스에 연결</span><span class="sxs-lookup"><span data-stu-id="fe9f6-129">Connecting to a named instance by using Windows Authentication and specifying input and output files:</span></span>  
  
    ```  
    sqlcmd -S <ComputerName>\<InstanceName> -i <MyScript.sql> -o <MyOutput.rpt>  
    ```  
  
-   <span data-ttu-id="fe9f6-130">Windows 인증을 사용하여 로컬 컴퓨터의 기본 인스턴스에 연결하고 쿼리를 실행한 다음 쿼리 실행이 완료된 후에도 `sqlcmd`가 실행되는 상태로 유지</span><span class="sxs-lookup"><span data-stu-id="fe9f6-130">Connecting to the default instance on the local computer by using Windows Authentication, executing a query, and having `sqlcmd` remain running after the query has finished running:</span></span>  
  
    ```  
    sqlcmd -q "SELECT * FROM AdventureWorks2012.Person.Person"  
    ```  
  
-   <span data-ttu-id="fe9f6-131">Windows 인증을 사용하여 로컬 컴퓨터의 기본 인스턴스에 연결하고 쿼리를 실행한 다음 출력을 파일로 전송하고 쿼리 실행이 완료되면 `sqlcmd` 종료</span><span class="sxs-lookup"><span data-stu-id="fe9f6-131">Connecting to the default instance on the local computer by using Windows Authentication, executing a query, directing the output to a file, and having `sqlcmd` exit after the query has finished running:</span></span>  
  
    ```  
    sqlcmd -Q "SELECT * FROM AdventureWorks2012.Person.Person" -o MyOutput.txt  
    ```  
  
-   <span data-ttu-id="fe9f6-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 문을 대화형으로 실행하기 위해 [!INCLUDE[tsql](../../includes/tsql-md.md)] 인증을 사용하여 명명된 인스턴스에 연결(`sqlcmd`에서 암호를 묻는 메시지 표시)</span><span class="sxs-lookup"><span data-stu-id="fe9f6-132">Connecting to a named instance using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication to interactively run [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, with `sqlcmd` prompting for a password:</span></span>  
  
    ```  
    sqlcmd -U MyLogin -S <ComputerName>\<InstanceName>  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="fe9f6-133">`sqlcmd` 유틸리티에서 지원하는 옵션 목록을 보려면 `sqlcmd -?`를 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-133">To see a list of the options that are supported by the `sqlcmd` utility run: `sqlcmd -?`.</span></span>  
  
## <a name="running-transact-sql-statements-interactively-by-using-sqlcmd"></a><span data-ttu-id="fe9f6-134">sqlcmd를 사용하여 대화형으로 Transact-SQL 문 실행</span><span class="sxs-lookup"><span data-stu-id="fe9f6-134">Running Transact-SQL Statements Interactively by Using sqlcmd</span></span>  
 <span data-ttu-id="fe9f6-135">`sqlcmd` 유틸리티를 대화형으로 사용하여 명령 프롬프트 창에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-135">You can use the `sqlcmd` utility interactively to execute [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in a Command Prompt window.</span></span> <span data-ttu-id="fe9f6-136">를 사용 하 여 문을 대화형으로 실행 하려면 [!INCLUDE[tsql](../../includes/tsql-md.md)] `sqlcmd` 입력 파일이 나 쿼리를 지정 하는 **-q**, **-q**, **-Z**또는 **-i** 옵션을 사용 하지 않고 유틸리티를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-136">To interactively execute [!INCLUDE[tsql](../../includes/tsql-md.md)] statements by using `sqlcmd`, run the utility without using the **-Q**, **-q**, **-Z**, or **-i** options to specify any input files or queries.</span></span> <span data-ttu-id="fe9f6-137">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-137">For example:</span></span>  
  
 `sqlcmd -S <ComputerName>\<InstanceName>`  
  
 <span data-ttu-id="fe9f6-138">입력 파일이나 쿼리 없이 명령을 실행하면 `sqlcmd`가 지정된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결하고 `1>`과 그 뒤에 밑줄이 깜박이는 새 줄을 표시합니다. 이를 `sqlcmd` 프롬프트라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-138">When the command is executed without input files or queries, `sqlcmd` connects to the specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and then displays a new line with a `1>` followed by a blinking underscore that is named the `sqlcmd` prompt.</span></span> <span data-ttu-id="fe9f6-139">`1`은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문의 첫 번째 줄임을 의미하고 `sqlcmd` 프롬프트는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 입력할 때 문이 시작되는 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-139">The `1` signifies that this is the first line of a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, and the `sqlcmd` prompt is the point at which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement will start when you type it in.</span></span>  
  
 <span data-ttu-id="fe9f6-140">`sqlcmd` 프롬프트에서는 `sqlcmd`, `GO` 등과 같이 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문과 `EXIT` 명령을 모두 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-140">At the `sqlcmd` prompt, you can type both [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and `sqlcmd` commands, such as `GO` and `EXIT`.</span></span> <span data-ttu-id="fe9f6-141">각 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 문 캐시를 호출한 버퍼에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-141">Each [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is put in a buffer called the statement cache.</span></span> <span data-ttu-id="fe9f6-142">이러한 문은 `GO` 명령을 입력하고 Enter 키를 누르면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-142">These statements are sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] after you type the `GO` command and press ENTER.</span></span> <span data-ttu-id="fe9f6-143">종료 하려면 `sqlcmd` `EXIT` `QUIT` 새 줄의 시작 부분에 또는를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-143">To exit `sqlcmd`, type `EXIT` or `QUIT` at the start of a new line.</span></span>  
  
 <span data-ttu-id="fe9f6-144">문 캐시를 지우려면 `:RESET`을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-144">To clear the statement cache, type `:RESET`.</span></span> <span data-ttu-id="fe9f6-145">`^C`을 입력 하면이 `sqlcmd` 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-145">Typing `^C` causes `sqlcmd` to exit.</span></span> <span data-ttu-id="fe9f6-146">`^C`는 `GO` 명령을 실행한 후 문 캐시의 실행을 중지하는 데 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-146">`^C` can also be used to stop the execution of the statement cache after a `GO` command has been issued.</span></span>  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]<span data-ttu-id="fe9f6-147">대화형 세션에서 입력 한 문은 **: ED** 명령과 프롬프트를 입력 하 여 편집할 수 있습니다. `sqlcmd`</span><span class="sxs-lookup"><span data-stu-id="fe9f6-147">statements that are entered in an interactive session can edited by entering the **:ED** command and the `sqlcmd` prompt.</span></span> <span data-ttu-id="fe9f6-148">그렇게 하면 편집기가 열리며 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 편집한 후 편집기를 닫으면 수정된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문이 명령 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-148">The editor will open and, after editing the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement and closing the editor, the revised [!INCLUDE[tsql](../../includes/tsql-md.md)] statement will appear in the command window.</span></span> <span data-ttu-id="fe9f6-149">Enter `GO` 를 실행 하 여 therevised [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-149">Enter `GO` to run therevised [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
## <a name="quoted-strings"></a><span data-ttu-id="fe9f6-150">따옴표 붙은 문자열</span><span class="sxs-lookup"><span data-stu-id="fe9f6-150">Quoted Strings</span></span>  
 <span data-ttu-id="fe9f6-151">따옴표 두 개를 연속으로 입력하여 문자열 내에 따옴표를 삽입하는 예외적인 경우를 제외하고 따옴표로 묶인 문자는 추가적인 전처리 없이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-151">Characters that are enclosed in quotation marks are used without any additional preprocessing, except that quotations marks can be inserted into a string by entering two consecutive quotation marks.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="fe9f6-152">에서는 이러한 문자 시퀀스를 하나의 따옴표로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-152">treats this character sequence as one quotation mark.</span></span> <span data-ttu-id="fe9f6-153">변환은 서버에서 발생합니다. 스크립팅 변수 역시 문자열 내에서는 단순한 문자로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-153">(However, the translation occurs in the server.) Scripting variables will not be expanded when they appear within a string.</span></span>  
  
 <span data-ttu-id="fe9f6-154">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-154">For example:</span></span>  
  
 `sqlcmd`  
  
 `PRINT "Length: 5"" 7'";`  
  
 `GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Length: 5" 7'`  
  
## <a name="strings-that-span-multiple-lines"></a><span data-ttu-id="fe9f6-155">여러 줄로 구성된 문자열</span><span class="sxs-lookup"><span data-stu-id="fe9f6-155">Strings That Span Multiple Lines</span></span>  
 <span data-ttu-id="fe9f6-156">`sqlcmd`는 스크립트에서 문자열을 여러 줄로 나누어 입력할 수 있도록 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-156">`sqlcmd` supports scripts that have strings that span multiple lines.</span></span> <span data-ttu-id="fe9f6-157">예를 들어 다음 `SELECT` 문은 여러 줄로 나누어져 있으나 `GO`를 입력한 후 Enter 키를 누르면 단일 문자열로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-157">For example, the following `SELECT` statement spans multiple lines but is a single string executed when you press the ENTER key after typing `GO`.</span></span>  
  
 `SELECT First line`  
  
 `FROM Second line`  
  
 `WHERE Third line;`  
  
 `GO`  
  
## <a name="interactive-sqlcmd-example"></a><span data-ttu-id="fe9f6-158">대화형 sqlcmd 실행 예</span><span class="sxs-lookup"><span data-stu-id="fe9f6-158">Interactive sqlcmd Example</span></span>  
 <span data-ttu-id="fe9f6-159">다음은 `sqlcmd`를 대화형으로 실행할 때 나타나는 내용의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-159">This is an example of what you see when you run `sqlcmd` interactively.</span></span>  
  
 <span data-ttu-id="fe9f6-160">명령 프롬프트 창을 열면 다음과 비슷한 줄 하나가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-160">When you open a Command Prompt window, there is one line similar to:</span></span>  
  
 `C:\> _`  
  
 <span data-ttu-id="fe9f6-161">이는 `C:\` 폴더가 현재 폴더이며 파일 이름을 지정하면 Windows가 해당 폴더에서 파일을 찾을 것이라는 의미입니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-161">This means the folder `C:\` is the current folder, and if you specify a file name, Windows will look for the file in that folder.</span></span>  
  
 <span data-ttu-id="fe9f6-162">`sqlcmd`를 입력하여 로컬 컴퓨터의 기본 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결하면 명령 프롬프트 창에 다음과 같은 내용이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-162">Type `sqlcmd` to connect to the default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the local computer, and the contents of the Command Prompt window will be:</span></span>  
  
 `C:\>sqlcmd`  
  
 `1> _`  
  
 <span data-ttu-id="fe9f6-163">이는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결되어 이제 `sqlcmd` 에 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문과 `sqlcmd` 명령을 입력해도 된다는 의미입니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-163">This means you have connected to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and `sqlcmd` is now ready to accept [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and `sqlcmd` commands.</span></span> <span data-ttu-id="fe9f6-164">`1>` 다음의 깜박이는 밑줄은 입력하는 문과 명령이 표시될 위치를 나타내는 `sqlcmd` 프롬프트입니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-164">The flashing underscore after the `1>` is the `sqlcmd` prompt that marks the location at which the statements and commands you type will be displayed.</span></span> <span data-ttu-id="fe9f6-165">이제를 입력 하 고 enter 키를 누른 다음 enter 키를 누릅니다 `USE AdventureWorks2012` `GO` .</span><span class="sxs-lookup"><span data-stu-id="fe9f6-165">Now, type `USE AdventureWorks2012` and press ENTER, and then type `GO` and press ENTER.</span></span> <span data-ttu-id="fe9f6-166">명령 프롬프트 창에 다음과 같은 내용이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-166">The contents of the Command Prompt window will be:</span></span>  
  
 `sqlcmd`  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Changed database context to 'AdventureWorks2012'.`  
  
 `1> _`  
  
 <span data-ttu-id="fe9f6-167">`USE AdventureWorks2012` 를 입력한 다음 Enter 키를 누르면 `sqlcmd` 가 새 줄을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-167">Pressing ENTER after entering `USE AdventureWorks2012` signaled `sqlcmd` to start a new line.</span></span> <span data-ttu-id="fe9f6-168">`GO,` 를 입력한 다음 Enter 키를 누르면 `sqlcmd` 가 `USE AdventureWorks2012` 문을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-168">Pressing ENTER, after you type `GO,` signaled `sqlcmd` to send the `USE AdventureWorks2012` statement to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="fe9f6-169">`sqlcmd` 는 `USE` 문이 성공적으로 완료되었음을 나타내는 메시지를 반환하고 새 `1>` 프롬프트를 표시하여 새 문이나 명령을 입력하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-169">`sqlcmd` then returned a message to indicate that the `USE` statement completed successfully and displayed a new `1>` prompt as a signal to enter a new statement or command.</span></span>  
  
 <span data-ttu-id="fe9f6-170">다음 예에서는 `SELECT` 문, `GO` 를 실행할 `SELECT`및 `EXIT` 를 종료할 `sqlcmd`를 입력할 경우 명령 프롬프트 창에 나타나는 내용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-170">The following example shows what the Command Prompt window contains if you type a `SELECT` statement, a `GO` to execute the `SELECT`, and an `EXIT` to exit `sqlcmd`:</span></span>  
  
 `sqlcmd`  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 `SELECT TOP (3) BusinessEntityID, FirstName, LastName`  
  
 `FROM Person.Person;`  
  
 `GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `BusinessEntityID   FirstName                 LastName`  
  
 `----------- -------------------------------- -----------`  
  
 `1           Syed                             Abbas`  
  
 `2           Catherine                        Abel`  
  
 `3           Kim                              Abercrombie`  
  
 `(3 rows affected)`  
  
 `1> EXIT`  
  
 `C:\>`  
  
 <span data-ttu-id="fe9f6-171">`3> GO` 줄 다음에 표시된 줄은 `SELECT` 문의 출력입니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-171">The lines after line `3> GO` are the output of a `SELECT` statement.</span></span> <span data-ttu-id="fe9f6-172">출력이 생성된 후 `sqlcmd` 는 `sqlcmd` 프롬프트를 다시 설정하고 `1>`을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-172">After you generate output, `sqlcmd` resets the `sqlcmd` prompt and displays `1>`.</span></span> <span data-ttu-id="fe9f6-173">`EXIT` 줄에 `1>`를 입력하면 명령 프롬프트 창을 처음 열었을 때와 동일한 줄이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-173">After entering `EXIT` at line `1>`, the Command Prompt window displays the same line it did when you first opened it.</span></span> <span data-ttu-id="fe9f6-174">이는 `sqlcmd` 가 해당 세션을 종료했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-174">This indicates that `sqlcmd` has exited its session.</span></span> <span data-ttu-id="fe9f6-175">이제 다시 `EXIT` 명령을 입력하여 명령 프롬프트 창을 닫을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-175">You can now close the Command Prompt window by typing another `EXIT` command.</span></span>  
  
## <a name="running-transact-sql-script-files-by-using-sqlcmd"></a><span data-ttu-id="fe9f6-176">sqlcmd를 사용하여 Transact-SQL 스크립트 파일 실행</span><span class="sxs-lookup"><span data-stu-id="fe9f6-176">Running Transact-SQL Script Files by Using sqlcmd</span></span>  
 <span data-ttu-id="fe9f6-177">`sqlcmd`를 사용하여 데이터베이스 스크립트 파일을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-177">You can use `sqlcmd` to execute database script files.</span></span> <span data-ttu-id="fe9f6-178">스크립트 파일은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문, `sqlcmd` 명령 및 스크립팅 변수를 포함하는 텍스트 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-178">Script files are text files that contain a mix of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, `sqlcmd` commands, and scripting variables.</span></span> <span data-ttu-id="fe9f6-179">변수를 스크립팅하는 방법은 [스크립팅 변수와 함께 sqlcmd 사용](sqlcmd-use-with-scripting-variables.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-179">For more information about how to script variables, see [Use sqlcmd with Scripting Variables](sqlcmd-use-with-scripting-variables.md).</span></span> <span data-ttu-id="fe9f6-180">`sqlcmd`는 대화형으로 입력된 문과 명령을 사용하는 방식과 유사한 방식으로 스크립트 파일의 문, 명령 및 스크립팅 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-180">`sqlcmd` works with the statements, commands, and scripting variables in a script file in a manner similar to how it works with statements and commands that are entered interactively.</span></span> <span data-ttu-id="fe9f6-181">주된 차이점은 `sqlcmd`가 사용자의 문, 명령 및 스크립팅 변수 입력 작업을 기다리지 않고 일시 중지 없이 입력 파일을 읽는다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-181">The main difference is that `sqlcmd` reads through the input file without pause instead of waiting for a user to enter the statements, commands, and scripting variables.</span></span>  
  
 <span data-ttu-id="fe9f6-182">다음과 같이 데이터베이스 스크립트 파일을 만드는 다른 방법도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-182">There are different ways to create database script files:</span></span>  
  
-   <span data-ttu-id="fe9f6-183">[!INCLUDE[tsql](../../includes/tsql-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]문 집합을 대화형으로 작성하고 디버그한 다음 쿼리 창의 내용을 스크립트 파일로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-183">You can interactively build and debug a set of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then save the contents of the Query window as a script file.</span></span>  
  
-   <span data-ttu-id="fe9f6-184">메모장과 같은 텍스트 편집기를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 포함하는 텍스트 파일을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-184">You can create a text file that contains [!INCLUDE[tsql](../../includes/tsql-md.md)] statements by using a text editor, such as Notepad.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="fe9f6-185">예</span><span class="sxs-lookup"><span data-stu-id="fe9f6-185">Examples</span></span>  
  
### <a name="a-running-a-script-by-using-sqlcmd"></a><span data-ttu-id="fe9f6-186">A.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-186">A.</span></span> <span data-ttu-id="fe9f6-187">sqlcmd를 사용하여 스크립트 실행</span><span class="sxs-lookup"><span data-stu-id="fe9f6-187">Running a script by using sqlcmd</span></span>  
 <span data-ttu-id="fe9f6-188">메모장을 시작하고 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-188">Start Notepad, and type the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 `SELECT TOP (3) BusinessEntityID, FirstName, LastName`  
  
 `FROM Person.Person;`  
  
 `GO`  
  
 <span data-ttu-id="fe9f6-189">`MyFolder` 라는 폴더를 만든 다음 스크립트를 `MyScript.sql` 폴더에 `C:\MyFolder`파일로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-189">Create a folder named `MyFolder` and then save the script as the file `MyScript.sql` in the folder `C:\MyFolder`.</span></span> <span data-ttu-id="fe9f6-190">명령 프롬프트에 다음을 입력하여 스크립트를 실행하고 출력을 `MyOutput.txt` 의 `MyFolder`에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-190">Enter the following at the command prompt to run the script and put the output in `MyOutput.txt` in `MyFolder`:</span></span>  
  
 `sqlcmd -i C:\MyFolder\MyScript.sql -o C:\MyFolder\MyOutput.txt`  
  
 <span data-ttu-id="fe9f6-191">메모장에서 `MyOutput.txt` 의 내용을 보면 다음이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-191">When you view the contents of `MyOutput.txt` in Notepad, you will see the following:</span></span>  
  
 `Changed database context to 'AdventureWorks2012'.`  
  
 `BusinessEntityID FirstName   LastName`  
  
 `---------------- ----------- -----------`  
  
 `1                Syed        Abbas`  
  
 `2                Catherine   Abel`  
  
 `3                Kim         Abercrombie`  
  
 `(3 rows affected)`  
  
### <a name="b-using-sqlcmd-with-a-dedicated-administrative-connection"></a><span data-ttu-id="fe9f6-192">B.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-192">B.</span></span> <span data-ttu-id="fe9f6-193">전용 관리 연결에 sqlcmd 사용</span><span class="sxs-lookup"><span data-stu-id="fe9f6-193">Using sqlcmd with a dedicated administrative connection</span></span>  
 <span data-ttu-id="fe9f6-194">다음 예에서 `sqlcmd` 는 DAC(관리자 전용 연결)를 사용하여 차단 문제가 발생한 서버에 연결하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-194">In the following example, `sqlcmd` is used to connect to a server that has a blocking problem by using the dedicated administrator connection (DAC).</span></span>  
  
 `C:\>sqlcmd -S ServerName -A`  
  
 `1> SELECT blocked FROM sys.dm_exec_requests WHERE blocked <> 0;`  
  
 `2> GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `spid   blocked`  
  
 `------ -------`  
  
 `62       64`  
  
 `(1 rows affected)`  
  
 <span data-ttu-id="fe9f6-195">`sqlcmd` 를 사용하여 차단 프로세스를 끝냅니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-195">Use `sqlcmd` to end the blocking process.</span></span>  
  
 `1> KILL 64;`  
  
 `2> GO`  
  
### <a name="c-using-sqlcmd-to-execute-a-stored-procedure"></a><span data-ttu-id="fe9f6-196">C.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-196">C.</span></span> <span data-ttu-id="fe9f6-197">sqlcmd를 사용하여 저장 프로시저 실행</span><span class="sxs-lookup"><span data-stu-id="fe9f6-197">Using sqlcmd to execute a stored procedure</span></span>  
 <span data-ttu-id="fe9f6-198">다음 예에서는 `sqlcmd`를 사용하여 저장 프로시저를 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-198">The following example shows how to execute a stored procedure by using `sqlcmd`.</span></span> <span data-ttu-id="fe9f6-199">다음 저장 프로시저를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-199">Create the following stored procedure.</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `IF OBJECT_ID ( ' dbo.ContactEmailAddress, 'P' ) IS NOT NULL`  
  
 `DROP PROCEDURE dbo.ContactEmailAddress;`  
  
 `GO`  
  
 `CREATE PROCEDURE dbo.ContactEmailAddress`  
  
 `(`  
  
 `@FirstName nvarchar(50)`  
  
 `,@LastName nvarchar(50)`  
  
 `)`  
  
 `AS`  
  
 `SET NOCOUNT ON`  
  
 `SELECT EmailAddress`  
  
 `FROM Person.Person`  
  
 `WHERE FirstName = @FirstName`  
  
 `AND LastName = @LastName;`  
  
 `SET NOCOUNT OFF`  
  
 <span data-ttu-id="fe9f6-200">`sqlcmd` 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-200">At the `sqlcmd` prompt, enter the following:</span></span>  
  
 `C:\sqlcmd`  
  
 `1> :Setvar FirstName Gustavo`  
  
 `1> :Setvar LastName Achong`  
  
 `1> EXEC dbo.ContactEmailAddress $(Gustavo),$(Achong)`  
  
 `2> GO`  
  
 `EmailAddress`  
  
 `-----------------------------`  
  
 `gustavo0@adventure-works.com`  
  
### <a name="d-using-sqlcmd-for-database-maintenance"></a><span data-ttu-id="fe9f6-201">D.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-201">D.</span></span> <span data-ttu-id="fe9f6-202">데이터베이스 유지 관리에 sqlcmd 사용</span><span class="sxs-lookup"><span data-stu-id="fe9f6-202">Using sqlcmd for database maintenance</span></span>  
 <span data-ttu-id="fe9f6-203">다음 예에서는 데이터베이스 유지 관리 태스크에 `sqlcmd` 를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-203">The following example shows how to use `sqlcmd` for a database maintenance task.</span></span> <span data-ttu-id="fe9f6-204">다음 코드로 `C:\BackupTemplate.sql` 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-204">Create `C:\BackupTemplate.sql` with the following code.</span></span>  
  
 `USE master;`  
  
 `BACKUP DATABASE [$(db)] TO DISK='$(bakfile)';`  
  
 <span data-ttu-id="fe9f6-205">`sqlcmd` 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-205">At the `sqlcmd` prompt, enter the following:</span></span>  
  
 `C:\ >sqlcmd`  
  
 `1> :connect <server>`  
  
 `Sqlcmd: Successfully connected to server <server>.`  
  
 `1> :setvar db msdb`  
  
 `1> :setvar bakfile c:\msdb.bak`  
  
 `1> :r c:\BackupTemplate.sql`  
  
 `2> GO`  
  
 `Changed database context to 'master'.`  
  
 `Processed 688 pages for database 'msdb', file 'MSDBData' on file 2.`  
  
 `Processed 5 pages for database 'msdb', file 'MSDBLog' on file 2.`  
  
 `BACKUP DATABASE successfully processed 693 pages in 0.725 seconds (7.830 MB/sec)`  
  
### <a name="e-using-sqlcmd-to-execute-code-on-multiple-instances"></a><span data-ttu-id="fe9f6-206">E.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-206">E.</span></span> <span data-ttu-id="fe9f6-207">sqlcmd를 사용하여 여러 인스턴스의 코드 실행</span><span class="sxs-lookup"><span data-stu-id="fe9f6-207">Using sqlcmd to execute code on multiple instances</span></span>  
 <span data-ttu-id="fe9f6-208">단일 파일에 있는 다음 코드는 두 개의 인스턴스에 연결하는 스크립트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-208">The following code in a file shows a script that connects to two instances.</span></span> <span data-ttu-id="fe9f6-209">두 번째 인스턴스에 대한 연결 전에 `GO` 가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-209">Notice the `GO` before the connection to the second instance.</span></span>  
  
 `:CONNECT <server>\,<instance1>`  
  
 `EXEC dbo.SomeProcedure`  
  
 `GO`  
  
 `:CONNECT <server>\,<instance2>`  
  
 `EXEC dbo.SomeProcedure`  
  
 `GO`  
  
### <a name="e-returning-xml-output"></a><span data-ttu-id="fe9f6-210">E.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-210">E.</span></span> <span data-ttu-id="fe9f6-211">XML 출력 반환</span><span class="sxs-lookup"><span data-stu-id="fe9f6-211">Returning XML output</span></span>  
 <span data-ttu-id="fe9f6-212">다음 예에서는 XML 출력이 서식이 지정되지 않은 연속 스트림으로 반환되는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-212">The following example shows how XML output is returned unformatted, in a continuous stream.</span></span>  
  
 `C:\>sqlcmd -d AdventureWorks2012`  
  
 `1> :XML ON`  
  
 `1> SELECT TOP 3 FirstName + ' ' + LastName + ', '`  
  
 `2> FROM Person.Person`  
  
 `3> GO`  
  
 `Syed Abbas, Catherine Abel, Kim Abercrombie,`  
  
### <a name="f-using-sqlcmd-in-a-windows-script-file"></a><span data-ttu-id="fe9f6-213">F.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-213">F.</span></span> <span data-ttu-id="fe9f6-214">Windows 스크립트 파일에서 sqlcmd 사용</span><span class="sxs-lookup"><span data-stu-id="fe9f6-214">Using sqlcmd in a Windows script file</span></span>  
 <span data-ttu-id="fe9f6-215">`sqlcmd`와 같은 명령은 `sqlcmd -i C:\InputFile.txt -o C:\OutputFile.txt,` VBScript와 함께 .bat 파일에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-215">A `sqlcmd`command such as `sqlcmd -i C:\InputFile.txt -o C:\OutputFile.txt,` can be executed in a .bat file together with VBScript.</span></span> <span data-ttu-id="fe9f6-216">이 경우 대화형 옵션은 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-216">In this case, do not use interactive options.</span></span> <span data-ttu-id="fe9f6-217">`sqlcmd`는 .bat 파일을 실행하는 컴퓨터에 설치되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-217">`sqlcmd` must be installed on the computer that is executing the .bat file.</span></span>  
  
 <span data-ttu-id="fe9f6-218">첫 번째 단계로 다음과 같은 4개의 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-218">First, create the following four files:</span></span>  
  
-   <span data-ttu-id="fe9f6-219">C:\badscript.sql</span><span class="sxs-lookup"><span data-stu-id="fe9f6-219">C:\badscript.sql</span></span>  
  
    ```  
    SELECT batch_1_this_is_an_error  
    GO  
    SELECT 'batch #2'  
    GO  
    ```  
  
-   <span data-ttu-id="fe9f6-220">C:\goodscript.sql</span><span class="sxs-lookup"><span data-stu-id="fe9f6-220">C:\goodscript.sql</span></span>  
  
    ```  
    SELECT 'batch #1'  
    GO  
    SELECT 'batch #2'  
    GO  
    ```  
  
-   <span data-ttu-id="fe9f6-221">C:\returnvalue.sql</span><span class="sxs-lookup"><span data-stu-id="fe9f6-221">C:\returnvalue.sql</span></span>  
  
    ```  
    :exit(select 100)  
    @echo off  
    C:\windowsscript.bat  
    @echo off  
  
    echo Running badscript.sql  
    sqlcmd -i badscript.sql -b -o out.log  
    if not errorlevel 1 goto next1  
    echo == An error occurred   
  
    :next1  
  
    echo Running goodscript.sql  
    sqlcmd -i goodscript.sql -b -o out.log  
    if not errorlevel 1 goto next2  
    echo == An error occurred   
  
    :next2  
    echo Running returnvalue.sql  
    sqlcmd -i returnvalue.sql -o out.log  
    echo SQLCMD returned %errorlevel% to the command shell  
  
    :exit  
    ```  
  
-   <span data-ttu-id="fe9f6-222">C:\windowsscript.bat</span><span class="sxs-lookup"><span data-stu-id="fe9f6-222">C:\windowsscript.bat</span></span>  
  
    ```  
    @echo off  
  
    echo Running badscript.sql  
    sqlcmd -i badscript.sql -b -o out.log  
    if not errorlevel 1 goto next1  
    echo == An error occurred   
  
    :next1  
  
    echo Running goodscript.sql  
    sqlcmd -i goodscript.sql -b -o out.log  
    if not errorlevel 1 goto next2  
    echo == An error occurred   
  
    :next2  
    echo Running returnvalue.sql  
    sqlcmd -i returnvalue.sql -o out.log  
    echo SQLCMD returned %errorlevel% to the command shell  
  
    :exit  
    ```  
  
 <span data-ttu-id="fe9f6-223">그런 다음 명령 프롬프트에서 `C:\windowsscript.bat`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-223">Then, at the command prompt, run `C:\windowsscript.bat`:</span></span>  
  
 `C:\>windowsscript.bat`  
  
 `Running badscript.sql`  
  
 `== An error occurred`  
  
 `Running goodscript.sql`  
  
 `Running returnvalue.sql`  
  
 `SQLCMD returned 100 to the command shell`  
  
### <a name="g-using-sqlcmd-to-set-encryption-on-azure-sql-database"></a><span data-ttu-id="fe9f6-224">G.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-224">G.</span></span> <span data-ttu-id="fe9f6-225">sqlcmd를 사용하여 Azure SQL Database에서 암호화 설정</span><span class="sxs-lookup"><span data-stu-id="fe9f6-225">Using sqlcmd to set encryption on Azure SQL Database</span></span>  
 <span data-ttu-id="fe9f6-226">는 데이터에 대 한 `sqlcmd` 연결에서 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 암호화 및 인증서 신뢰를 지정 하기 위해 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-226">A `sqlcmd`can be executed on a connection to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] data on to specify encryption and certificate trust.</span></span> <span data-ttu-id="fe9f6-227">두 개의 ' sqlcmd ' ' 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-227">Two \`sqlcmd\`\`\`options are available:</span></span>  
  
-   <span data-ttu-id="fe9f6-228">-N 스위치는 클라이언트에서 암호화된 연결을 요청하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-228">The -N switch is used by the client to request an encrypted connection.</span></span> <span data-ttu-id="fe9f6-229">이 옵션은 ADO.net 옵션 `ENCRYPT = true`와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-229">This option is equivalent to the ADO.net option `ENCRYPT = true`.</span></span>  
  
-   <span data-ttu-id="fe9f6-230">–C 스위치는 클라이언트에서 유효성 검사 없이 암시적으로 서버 인증서를 신뢰하도록 구성하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-230">The -C switch is used by the client to configure it to implicitly the trust server certificate and not validate it.</span></span> <span data-ttu-id="fe9f6-231">이 옵션은 ADO.net 옵션 `TRUSTSERVERCERTIFICATE = true`와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-231">This option is equivalent to the ADO.net option `TRUSTSERVERCERTIFICATE = true`.</span></span>  
  
 <span data-ttu-id="fe9f6-232">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] 서비스는 SQL Server 인스턴스에서 사용 가능한 `SET` 옵션 중 일부는 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-232">The [!INCLUDE[ssSDS](../../includes/sssds-md.md)] service does not support all the `SET` options available on a SQL Server instance.</span></span> <span data-ttu-id="fe9f6-233">다음 옵션은 해당하는 `SET` 옵션이 `ON` 또는 `OFF`로 설정되어 있는 경우 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-233">The following options throw an error when the corresponding `SET` option is set to `ON` or `OFF`:</span></span>  
  
-   <span data-ttu-id="fe9f6-234">SET ANSI_DEFAULTS</span><span class="sxs-lookup"><span data-stu-id="fe9f6-234">SET ANSI_DEFAULTS</span></span>  
  
-   <span data-ttu-id="fe9f6-235">SET ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="fe9f6-235">SET ANSI_NULLS</span></span>  
  
-   <span data-ttu-id="fe9f6-236">SET REMOTE_PROC_TRANSACTIONS</span><span class="sxs-lookup"><span data-stu-id="fe9f6-236">SET REMOTE_PROC_TRANSACTIONS</span></span>  
  
-   <span data-ttu-id="fe9f6-237">SET ANSI_NULL_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="fe9f6-237">SET ANSI_NULL_DEFAULT</span></span>  
  
 <span data-ttu-id="fe9f6-238">다음 SET 옵션은 예외를 반환하지 않지만 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-238">The following SET options do not throw exceptions but cannot be used.</span></span> <span data-ttu-id="fe9f6-239">이러한 옵션은 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-239">They are deprecated:</span></span>  
  
-   <span data-ttu-id="fe9f6-240">SET CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="fe9f6-240">SET CONCAT_NULL_YIELDS_NULL</span></span>  
  
-   <span data-ttu-id="fe9f6-241">SET ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="fe9f6-241">SET ANSI_PADDING</span></span>  
  
-   <span data-ttu-id="fe9f6-242">SET QUERY_GOVERNOR_COST_LIMIT</span><span class="sxs-lookup"><span data-stu-id="fe9f6-242">SET QUERY_GOVERNOR_COST_LIMIT</span></span>  
  
#### <a name="syntax"></a><span data-ttu-id="fe9f6-243">구문</span><span class="sxs-lookup"><span data-stu-id="fe9f6-243">Syntax</span></span>  
 <span data-ttu-id="fe9f6-244">다음 예에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 공급자 설정에 포함된 사례를 참조합니다. `ForceProtocolEncryption = False`, `Trust Server Certificate = No`</span><span class="sxs-lookup"><span data-stu-id="fe9f6-244">The following examples refer to cases where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Provider settings include: `ForceProtocolEncryption = False`, `Trust Server Certificate = No`</span></span>  
  
 <span data-ttu-id="fe9f6-245">Windows 자격 증명을 사용한 연결 및 통신 암호화:</span><span class="sxs-lookup"><span data-stu-id="fe9f6-245">Connect using Windows credentials and encrypt communication:</span></span>  
  
```  
SQLCMD -E -N  
  
```  
  
 <span data-ttu-id="fe9f6-246">Windows 자격 증명을 사용한 연결 및 서버 인증서 신뢰:</span><span class="sxs-lookup"><span data-stu-id="fe9f6-246">Connect using Windows credentials and trust server certificate:</span></span>  
  
```  
SQLCMD -E -C  
  
```  
  
 <span data-ttu-id="fe9f6-247">Windows 자격 증명을 사용한 연결, 통신 암호화 및 서버 인증서 신뢰:</span><span class="sxs-lookup"><span data-stu-id="fe9f6-247">Connect using Windows credentials, encrypt communication and trust server certificate:</span></span>  
  
```  
SQLCMD -E -N -C  
  
```  
  
 <span data-ttu-id="fe9f6-248">다음 예에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 공급자 설정에 포함된 사례를 참조합니다. `ForceProtocolEncryption = True`, `TrustServerCertificate = Yes`</span><span class="sxs-lookup"><span data-stu-id="fe9f6-248">The following examples refer to cases where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Provider settings include: `ForceProtocolEncryption = True`, `TrustServerCertificate = Yes`.</span></span>  
  
 <span data-ttu-id="fe9f6-249">Windows 자격 증명을 사용한 연결, 통신 암호화 및 서버 인증서 신뢰:</span><span class="sxs-lookup"><span data-stu-id="fe9f6-249">Connect using Windows credentials, encrypt communication and trust server certificate:</span></span>  
  
```  
SQLCMD -E  
  
```  
  
 <span data-ttu-id="fe9f6-250">Windows 자격 증명을 사용한 연결, 통신 암호화 및 서버 인증서 신뢰:</span><span class="sxs-lookup"><span data-stu-id="fe9f6-250">Connect using Windows credentials, encrypt communication and trust server certificate:</span></span>  
  
```  
SQLCMD -E -N  
  
```  
  
 <span data-ttu-id="fe9f6-251">Windows 자격 증명을 사용한 연결, 통신 암호화 및 서버 인증서 신뢰:</span><span class="sxs-lookup"><span data-stu-id="fe9f6-251">Connect using Windows credentials, encrypt communication and trust server certificate:</span></span>  
  
```  
SQLCMD -E -T  
  
```  
  
 <span data-ttu-id="fe9f6-252">Windows 자격 증명을 사용한 연결, 통신 암호화 및 서버 인증서 신뢰:</span><span class="sxs-lookup"><span data-stu-id="fe9f6-252">Connect using Windows credentials, encrypt communication and trust server certificate:</span></span>  
  
```  
SQLCMD -E -N -C  
  
```  
  
 <span data-ttu-id="fe9f6-253">공급자가 `ForceProtocolEncryption = True` 를 지정하는 경우 연결 문자열에 `Encrypt=No` 가 있어도 암호화가 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe9f6-253">If the provider specifies `ForceProtocolEncryption = True` then encryption is enabled even if `Encrypt=No` in the connection string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe9f6-254">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe9f6-254">See Also</span></span>  
 <span data-ttu-id="fe9f6-255">[sqlcmd 유틸리티](../../tools/sqlcmd-utility.md) </span><span class="sxs-lookup"><span data-stu-id="fe9f6-255">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span></span>  
 <span data-ttu-id="fe9f6-256">[스크립팅 변수와 함께 sqlcmd 사용](sqlcmd-use-with-scripting-variables.md) </span><span class="sxs-lookup"><span data-stu-id="fe9f6-256">[Use sqlcmd with Scripting Variables](sqlcmd-use-with-scripting-variables.md) </span></span>  
 <span data-ttu-id="fe9f6-257">[쿼리 편집기로 SQLCMD 스크립트 편집](edit-sqlcmd-scripts-with-query-editor.md) </span><span class="sxs-lookup"><span data-stu-id="fe9f6-257">[Edit SQLCMD Scripts with Query Editor](edit-sqlcmd-scripts-with-query-editor.md) </span></span>  
 <span data-ttu-id="fe9f6-258">[작업 단계 관리](../../ssms/agent/manage-job-steps.md) </span><span class="sxs-lookup"><span data-stu-id="fe9f6-258">[Manage Job Steps](../../ssms/agent/manage-job-steps.md) </span></span>  
 [<span data-ttu-id="fe9f6-259">CmdExec 작업 단계 만들기</span><span class="sxs-lookup"><span data-stu-id="fe9f6-259">Create a CmdExec Job Step</span></span>](../../ssms/agent/create-a-cmdexec-job-step.md)  
  
  
