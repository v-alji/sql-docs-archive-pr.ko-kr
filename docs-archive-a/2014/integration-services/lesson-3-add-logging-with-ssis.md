---
title: '3 단원: 로깅 추가 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 64cd24cc-ba8e-4bd7-b10b-6b80d8b04af6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 58fcc29759f19ad215a76a1b9ed9bf313b4c869c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650176"
---
# <a name="lesson-3-adding-logging"></a><span data-ttu-id="ac878-102">3단원: 로깅 추가</span><span class="sxs-lookup"><span data-stu-id="ac878-102">Lesson 3: Adding Logging</span></span>
  [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="ac878-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]에는 태스크 및 컨테이너 이벤트 추적을 제공하여 패키지 실행을 모니터링하고 문제를 해결할 수 있는 로깅 기능이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac878-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] includes logging features that let you troubleshoot and monitor package execution by providing a trace of task and container events.</span></span> <span data-ttu-id="ac878-104">로깅 기능은 융통성이 있으므로 패키지 수준 또는 패키지 내의 개별 태스크와 컨테이너에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac878-104">The logging features are flexible, and can be enabled at the package level or on individual tasks and containers within the package.</span></span> <span data-ttu-id="ac878-105">로깅하려는 이벤트를 선택하고 단일 패키지에 대해 여러 개의 로그를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac878-105">You can select which events you want to log, and create multiple logs against a single package.</span></span>  
  
 <span data-ttu-id="ac878-106">로깅은 로그 공급자가 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ac878-106">Logging is provided by a log provider.</span></span> <span data-ttu-id="ac878-107">각 로그 공급자는 다양한 형식과 대상 유형으로 로깅 정보를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac878-107">Each log provider can write logging information to different formats and destination types.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="ac878-108">에서는 다음 로그 공급자를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ac878-108">provides the following log providers:</span></span>  
  
-   <span data-ttu-id="ac878-109">텍스트 파일</span><span class="sxs-lookup"><span data-stu-id="ac878-109">Text file</span></span>  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]  
  
-   <span data-ttu-id="ac878-110">Windows 이벤트 로그</span><span class="sxs-lookup"><span data-stu-id="ac878-110">Windows Event log</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   <span data-ttu-id="ac878-111">XML 파일</span><span class="sxs-lookup"><span data-stu-id="ac878-111">XML file</span></span>  
  
 <span data-ttu-id="ac878-112">이 단원에서는 [Lesson 2: Adding Looping](lesson-2-adding-looping-with-ssis.md)에서 만든 패키지의 복사본을 만든 다음</span><span class="sxs-lookup"><span data-stu-id="ac878-112">In this lesson, you will create a copy of the package that you created in [Lesson 2: Adding Looping](lesson-2-adding-looping-with-ssis.md).</span></span> <span data-ttu-id="ac878-113">이 새 패키지 작업에서 패키지 실행 중에 특정 이벤트를 모니터링하도록 로깅을 추가하고 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ac878-113">Working with this new package, you will then add and configure logging to monitor specific events during package execution.</span></span> <span data-ttu-id="ac878-114">이전 단원 중 완료한 단원이 없는 경우 완성된 상태로 포함된 2단원 패키지를 복사할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac878-114">If you have not completed any of the previous lessons, you can also copy the completed Lesson 2 package that is included with the tutorial.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ac878-115">이 자습서를 실행하려면 **AdventureWorksDW2012** 예제 데이터베이스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ac878-115">This tutorial requires the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="ac878-116">**AdventureWorksDW2012**를 설치 및 배포 하는 방법에 대 한 자세한 내용은 [GitHub의 제품 샘플을 Reporting Services](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)하세요.</span><span class="sxs-lookup"><span data-stu-id="ac878-116">For more information about how to install and deploy **AdventureWorksDW2012**, [Reporting Services Product Samples on GitHub](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="ac878-117">단원 태스크</span><span class="sxs-lookup"><span data-stu-id="ac878-117">Lesson Tasks</span></span>  
 <span data-ttu-id="ac878-118">이 단원에서는 다음 태스크를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="ac878-118">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="ac878-119">1단계: 2단원 패키지 복사</span><span class="sxs-lookup"><span data-stu-id="ac878-119">Step 1: Copying the Lesson 2 Package</span></span>](lesson-3-1-copying-the-lesson-2-package.md)  
  
-   [<span data-ttu-id="ac878-120">2단계: 로깅 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="ac878-120">Step 2: Adding and Configuring Logging</span></span>](lesson-3-2-adding-and-configuring-logging.md)  
  
-   [<span data-ttu-id="ac878-121">3단계: 3단원 자습서 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="ac878-121">Step 3: Testing the Lesson 3 Tutorial Package</span></span>](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="ac878-122">단원 시작</span><span class="sxs-lookup"><span data-stu-id="ac878-122">Start the Lesson</span></span>  
 [<span data-ttu-id="ac878-123">1단계: 2단원 패키지 복사</span><span class="sxs-lookup"><span data-stu-id="ac878-123">Step 1: Copying the Lesson 2 Package</span></span>](lesson-3-1-copying-the-lesson-2-package.md)  
  
  
