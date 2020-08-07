---
title: dta 명령 프롬프트 유틸리티 시작 및 작업 튜닝 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], tutorials
ms.assetid: f34a5acf-1f3b-4484-a770-6470cb925ab0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4b2b1755a2ce8299556ab7d0ae14c89d3b2c8554
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727647"
---
# <a name="starting-the-dta-command-prompt-utility-and-tuning-a-workload"></a><span data-ttu-id="506d0-102">dta 명령 프롬프트 유틸리티 시작 및 작업 튜닝</span><span class="sxs-lookup"><span data-stu-id="506d0-102">Starting the dta Command Prompt Utility and Tuning a Workload</span></span>
  <span data-ttu-id="506d0-103"> 이 태스크에서는 **dta** 유틸리티를 시작하고 도움말을 본 다음, 이 유틸리티를 사용하여 명령 프롬프트에서 작업을 튜닝하는 과정을 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="506d0-103">This task guides you through starting the **dta** utility, viewing its Help, and then using it to tune a workload from the command prompt.</span></span> <span data-ttu-id="506d0-104">이 MyScript 작업을 [튜닝](lesson-1-1-tuning-a-workload.md)하는 GUI (그래픽 사용자 인터페이스)를 데이터베이스 엔진 튜닝 관리자 위해 만든 작업 인를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="506d0-104">It uses the workload, MyScript.sql, which you created for the Database Engine Tuning Advisor graphical user interface (GUI) practice [Tuning a Workload](lesson-1-1-tuning-a-workload.md).</span></span>  
  
 <span data-ttu-id="506d0-105">이 자습서에서는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 예제 데이터베이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="506d0-105">The tutorial uses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="506d0-106">보안을 위해 예제 데이터베이스는 기본적으로 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="506d0-106">For security reasons, the sample databases are not installed by default.</span></span> <span data-ttu-id="506d0-107">예제 데이터베이스를 설치하려면 [SQL Server 예제 및 예제 데이터베이스](http://sqlserversamples.codeplex.com)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="506d0-107">To install the sample databases, see [Installing SQL Server Samples and Sample Databases](http://sqlserversamples.codeplex.com).</span></span>  
  
 <span data-ttu-id="506d0-108">다음 태스크에서는 명령 프롬프트를 열고 **dta** 명령 프롬프트 유틸리티를 시작하고 구문 도움말을 본 다음 [Tuning a Workload](lesson-1-1-tuning-a-workload.md)에서 만든 단순 작업인 MyScript.sql을 튜닝하는 과정을 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="506d0-108">The following tasks guide you through opening a command prompt, starting the **dta** command prompt utility, viewing its syntax Help, and tuning a simple workload, MyScript.sql, which you created in [Tuning a Workload](lesson-1-1-tuning-a-workload.md).</span></span>  
  
### <a name="to-start-the-dta-command-prompt-utility-and-view-help"></a><span data-ttu-id="506d0-109">dta 명령 프롬프트 유틸리티를 시작하고 도움말을 보려면</span><span class="sxs-lookup"><span data-stu-id="506d0-109">To start the dta command prompt utility and view Help</span></span>  
  
1.  <span data-ttu-id="506d0-110">**시작** 메뉴에서 **모든 프로그램**, **보조프로그램**을 차례로 가리킨 다음 **명령 프롬프트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="506d0-110">On the **Start** menu, point to **All Programs**, point to **Accessories**, and then click **Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="506d0-111">명령 프롬프트에 다음을 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="506d0-111">At the command prompt, type the following, and press ENTER:</span></span>  
  
    ```  
    dta -? | more  
    ```  
  
     <span data-ttu-id="506d0-112">이 명령의 `| more` 부분은 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="506d0-112">The `| more` part of this command is optional.</span></span> <span data-ttu-id="506d0-113">그러나 이 부분을 사용하여 유틸리티의 구문 도움말이 표시되는 방식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="506d0-113">However, using it enables you to page through the syntax help for the utility.</span></span> <span data-ttu-id="506d0-114">도움말 텍스트를 한 줄씩 표시하려면 Enter 키를, 한 페이지씩 표시하려면 스페이스바를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="506d0-114">Press ENTER to advance the help text by the line, or press the SPACEBAR to advance it by the page.</span></span>  
  
### <a name="to-tune-a-simple-workload-by-using-the-dta-command-prompt-utility"></a><span data-ttu-id="506d0-115">dta 명령 프롬프트 유틸리티를 사용하여 단순 작업을 튜닝하려면</span><span class="sxs-lookup"><span data-stu-id="506d0-115">To tune a simple workload by using the dta command prompt utility</span></span>  
  
1.  <span data-ttu-id="506d0-116">명령 프롬프트에서 MyScript.sql 파일을 저장한 디렉터리로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="506d0-116">At the command prompt, navigate to the directory where you have stored the MyScript.sql file.</span></span>  
  
2.  <span data-ttu-id="506d0-117">명령 프롬프트에 다음을 입력하고 Enter 키를 눌러 명령을 실행하고 튜닝 세션을 시작합니다. 유틸리티에서 명령 구문을 분석할 때는 대/소문자가 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="506d0-117">At the command prompt, type the following, and press ENTER to run the command and start the tuning session (note that the utility is case-sensitive when it parses commands):</span></span>  
  
    ```  
    dta -S YourServerName\YourSQLServerInstanceName -E -D AdventureWorks2012 -if MyScript.sql -s MySession2 -of MySession2OutputScript.sql -ox MySession2Output.xml -fa IDX_IV -fp NONE -fk NONE  
    ```  
  
     <span data-ttu-id="506d0-118">여기서 `-S` 는 사용 중인 서버 이름과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스가 설치된 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="506d0-118">where `-S` specifies the name of your server and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance where the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database is installed.</span></span> <span data-ttu-id="506d0-119">`-E` 설정은 인스턴스에 대해 트러스트된 연결을 사용하도록 지정하는데 이는 Windows 도메인 계정으로 연결할 경우에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="506d0-119">The setting `-E` specifies that you want to use a trusted connection to the instance, which is appropriate if you are connecting with a Windows domain account.</span></span> <span data-ttu-id="506d0-120">`-D` 설정은 튜닝하려는 데이터베이스를, `-if` 설정은 작업 파일을, `-s` 설정은 세션 이름을, `-of` 설정은 도구에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 권장 구성 스크립트를 작성하려는 파일을, `-ox` 설정은 도구에서 권장 구성을 XML 형식으로 작성하려는 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="506d0-120">The setting `-D` specifies the database that you want to tune, `-if` specifies the workload file, `-s` specifies the session name, `-of` specifies the file to which you want the tool to write the [!INCLUDE[tsql](../../includes/tsql-md.md)] recommendations script, and `-ox` specifies the file to which you want the tool to write the recommendations in XML format.</span></span> <span data-ttu-id="506d0-121">마지막 스위치 세 개는 튜닝 옵션을 지정합니다. 즉, `-fa IDX_IV` 는 데이터베이스 엔진 튜닝 관리자가 인덱스(클러스터형과 비클러스터형 모두)와 인덱싱된 뷰만 추가할 것을 고려하도록 지정하고 `-fp NONE` 은 분석하는 동안 어떠한 분할 전략도 고려하지 않도록 지정하며 `-fk NONE` 은 데이터베이스 엔진 튜닝 관리자가 해당 권장 구성을 만들 때 데이터베이스의 어떠한 기존 물리적 디자인 구조도 유지되지 않도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="506d0-121">The last three switches specify tuning options as follows: `-fa IDX_IV` specifies that Database Engine Tuning Advisor should only consider adding indexes (both clustered and nonclustered) and indexed views; `-fp NONE` specifies that no partition strategy should be considered during analysis; and `-fk NONE` specifies that no existing physical design structures in the database must be kept when Database Engine Tuning Advisor makes its recommendations.</span></span>  
  
3.  <span data-ttu-id="506d0-122">데이터베이스 엔진 튜닝 관리자에서 작업 튜닝을 마치면 튜닝 세션이 완료되었다는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="506d0-122">After Database Engine Tuning Advisor finishes tuning the workload, it displays a message indicating that your tuning session completed successfully.</span></span> <span data-ttu-id="506d0-123">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 로 MySession2OutputScript.sql 및 MySession2Output.xml 파일을 열어서 튜닝 결과를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="506d0-123">You can view the tuning results, by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to open the files MySession2OutputScript.sql and MySession2Output.xml.</span></span> <span data-ttu-id="506d0-124">또는 [Viewing Tuning Recommendations](lesson-1-2-viewing-tuning-recommendations.md) 및 [Viewing Tuning Reports](lesson-1-3-viewing-tuning-reports.md)에서와 같은 방법으로 데이터베이스 엔진 튜닝 관리자 GUI에서 MySession2 튜닝 세션을 열고 해당 권장 구성과 보고서를 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="506d0-124">Alternatively, you can also open the MySession2 tuning session in the Database Engine Tuning Advisor GUI and view its recommendations and reports in the same way that you did in [Viewing Tuning Recommendations](lesson-1-2-viewing-tuning-recommendations.md) and [Viewing Tuning Reports](lesson-1-3-viewing-tuning-reports.md).</span></span>  
  
## <a name="summary"></a><span data-ttu-id="506d0-125">요약</span><span class="sxs-lookup"><span data-stu-id="506d0-125">Summary</span></span>  
 <span data-ttu-id="506d0-126">**dta** 유틸리티를 사용하여 명령 프롬프트에서 단순 작업 튜닝을 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="506d0-126">You have completed tuning a simple workload from the command prompt by using the **dta** utility.</span></span> <span data-ttu-id="506d0-127">이 도구는 다른 많은 튜닝 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="506d0-127">This tool provides many other tuning options.</span></span> <span data-ttu-id="506d0-128">자세한 내용은 도구 도움말(**dta -?**)과 참조 항목 [dta 유틸리티](dta-utility.md) 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="506d0-128">Refer to the tool Help (**dta -?**) and the reference topic [dta Utility](dta-utility.md) for more information.</span></span>  
  
## <a name="after-you-finish-this-tutorial"></a><span data-ttu-id="506d0-129">이 자습서를 마친 후</span><span class="sxs-lookup"><span data-stu-id="506d0-129">After You Finish This Tutorial</span></span>  
 <span data-ttu-id="506d0-130">이 자습서의 학습을 마친 후에는 다음 항목을 참조하여 데이터베이스 엔진 튜닝 관리자에 대한 자세한 내용을 보십시오.</span><span class="sxs-lookup"><span data-stu-id="506d0-130">After you finish the lessons in this tutorial, refer to the following topics for more information about Database Engine Tuning Advisor:</span></span>  
  
-   <span data-ttu-id="506d0-131">[Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md) - 이 도구로 태스크를 수행하는 방법에 대한 설명</span><span class="sxs-lookup"><span data-stu-id="506d0-131">[Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md) for descriptions of how to perform tasks with this tool.</span></span>  
  
-   <span data-ttu-id="506d0-132">[dta Utility](dta-utility.md) - 유틸리티 작업을 제어하는 데 사용할 수 있는 명령 프롬프트 유틸리티 및 선택적 XML 파일에 대한 참조 자료</span><span class="sxs-lookup"><span data-stu-id="506d0-132">[dta Utility](dta-utility.md) for reference material on the command prompt utility and the optional XML file you can use to control the operation of the utility.</span></span>  
  
 <span data-ttu-id="506d0-133">자습서의 시작 부분으로 돌아가려면 [Tutorial: Database Engine Tuning Advisor](tutorial-database-engine-tuning-advisor.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="506d0-133">To return to the start of the tutorial, see [Tutorial: Database Engine Tuning Advisor](tutorial-database-engine-tuning-advisor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="506d0-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="506d0-134">See Also</span></span>  
 [<span data-ttu-id="506d0-135">데이터베이스 엔진 자습서</span><span class="sxs-lookup"><span data-stu-id="506d0-135">Database Engine Tutorials</span></span>](../../relational-databases/database-engine-tutorials.md)  
  
  
