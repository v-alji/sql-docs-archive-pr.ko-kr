---
title: '자습서: 데이터베이스 엔진 튜닝 관리자 | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- Database Engine Tuning Advisor [SQL Server], tutorials
- tutorials [Database Engine Tuning Advisor]
ms.assetid: 3b54cbbe-d8c6-424d-92f1-aa58179f4da8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 68e026cb28b875b834f20c906232285ede8e217b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646787"
---
# <a name="tutorial-database-engine-tuning-advisor"></a><span data-ttu-id="e6afc-102">자습서: Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="e6afc-102">Tutorial: Database Engine Tuning Advisor</span></span>
  <span data-ttu-id="e6afc-103">데이터베이스 엔진 튜닝 관리자 자습서를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e6afc-103">Welcome to the Database Engine Tuning Advisor tutorial.</span></span> <span data-ttu-id="e6afc-104">사용자가 지정한 데이터베이스에서 쿼리를 처리하는 방법을 검사한 다음 인덱스, 인덱싱된 뷰 및 분할과 같은 데이터베이스 구조를 수정하여 쿼리 처리 성능을 높일 수 있는 방법을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="e6afc-104">Database Engine Tuning Advisor examines how queries are processed in the databases you specify, and then recommends how you can improve query processing performance by modifying database structures such as indexes, indexed views, and partitioning.</span></span>  
  
 <span data-ttu-id="e6afc-105">데이터베이스 엔진 튜닝 관리자는 GUI(그래픽 사용자 인터페이스)와 **dta** 명령 프롬프트 유틸리티의 두 가지 사용자 인터페이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e6afc-105">Database Engine Tuning Advisor provides two user interfaces: a graphical user interface (GUI) and the **dta** command prompt utility.</span></span> <span data-ttu-id="e6afc-106">GUI를 사용하면 튜닝 세션의 결과를 빠르게 볼 수 있고 **dta** 유틸리티를 사용하면 데이터베이스 엔진 튜닝 관리자 기능을 스크립트에 쉽게 통합하여 튜닝을 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6afc-106">The GUI makes it easy to quickly view the results of tuning sessions, and the **dta** utility makes it easy to incorporate Database Engine Tuning Advisor functionality into scripts for automated tuning.</span></span> <span data-ttu-id="e6afc-107">또한 데이터베이스 엔진 튜닝 관리자는 XML 입력을 받아들일 수 있고 자세히 튜닝 프로세스를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6afc-107">In addition, Database Engine Tuning Advisor can take XML input, which offers more control over the tuning process.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="e6afc-108">학습 내용</span><span class="sxs-lookup"><span data-stu-id="e6afc-108">What You Will Learn</span></span>  
 <span data-ttu-id="e6afc-109">이 자습서에서는 데이터베이스 엔진 튜닝 관리자 GUI를 탐색하는 방법과 GUI와 **dta** 유틸리티를 모두 사용하여 일부 기본 태스크를 수행하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="e6afc-109">This tutorial will teach you how to navigate the Database Engine Tuning Advisor GUI, and how to perform some basic tasks with both the GUI and the **dta** utility.</span></span> <span data-ttu-id="e6afc-110">다음 단원이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6afc-110">It contains the following lessons:</span></span>  
  
 [<span data-ttu-id="e6afc-111">1단원: 데이터베이스 엔진 튜닝 관리자 기본 탐색</span><span class="sxs-lookup"><span data-stu-id="e6afc-111">Lesson 1: Basic Navigation in Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/database-engine-tuning-advisor.md)  
 <span data-ttu-id="e6afc-112">이 단원에서는 새 데이터베이스 엔진 튜닝 관리자 GUI에 익숙해지고 표시 옵션과 레이아웃을 설정하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="e6afc-112">In this lesson, you will familiarize yourself with the new Database Engine Tuning Advisor GUI and learn how to set display options and layout.</span></span>  
  
 [<span data-ttu-id="e6afc-113">2단원: 데이터베이스 엔진 튜닝 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="e6afc-113">Lesson 2: Using Database Engine Tuning Advisor</span></span>](lesson-2-using-database-engine-tuning-advisor.md)  
 <span data-ttu-id="e6afc-114">이 단원에서는 데이터베이스 엔진 튜닝 관리자 GUI로 기본 튜닝 태스크를 수행하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="e6afc-114">In this lesson, you will learn how to perform basic tuning tasks with the Database Engine Tuning Advisor GUI.</span></span>  
  
 [<span data-ttu-id="e6afc-115">3단원: DTA 명령 프롬프트 유틸리티 사용</span><span class="sxs-lookup"><span data-stu-id="e6afc-115">Lesson 3: Using the dta Command Prompt Utility</span></span>](lesson-3-using-the-dta-command-prompt-utility.md)  
 <span data-ttu-id="e6afc-116">이 단원에서는 **dta** 명령 프롬프트 유틸리티를 시작하는 방법과 일부 단순 튜닝 명령을 실행하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="e6afc-116">In this lesson, you learn how to start the **dta** command prompt utility and how to run some simple tuning commands.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6afc-117">요구 사항</span><span class="sxs-lookup"><span data-stu-id="e6afc-117">Requirements</span></span>  
 <span data-ttu-id="e6afc-118">이 자습서는 데이터베이스 엔진 튜닝 관리자 GUI나 **dta** 명령 프롬프트 유틸리티에는 익숙하지 않지만 데이터베이스 개념과 인덱스 및 인덱싱된 뷰와 같은 구조에는 많은 경험이 있는 데이터베이스 관리자를 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6afc-118">This tutorial is intended for database administrators who are not familiar with the Database Engine Tuning Advisor GUI or the **dta** command prompt utility, but who are experienced with database concepts and structures, such as indexes and indexed views.</span></span>  
  
 <span data-ttu-id="e6afc-119">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 예제 데이터베이스가 포함된 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] (또는 최신 버전)를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6afc-119">You must install [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] (or a later version) with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="e6afc-120">보안을 위해 예제 데이터베이스는 기본적으로 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e6afc-120">To enhance security, the sample databases are not installed by default.</span></span> <span data-ttu-id="e6afc-121">예제 데이터베이스를 설치하려면 [SQL Server 예제 및 예제 데이터베이스](http://sqlserversamples.codeplex.com)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6afc-121">To install the sample databases, see [Installing SQL Server Samples and Sample Databases](http://sqlserversamples.codeplex.com).</span></span>  
  
## <a name="after-you-finish-this-tutorial"></a><span data-ttu-id="e6afc-122">이 자습서를 마친 후</span><span class="sxs-lookup"><span data-stu-id="e6afc-122">After You Finish This Tutorial</span></span>  
 <span data-ttu-id="e6afc-123">이 자습서의 학습을 마친 후에는 다음 항목을 참조하여 데이터베이스 엔진 튜닝 관리자에 대한 자세한 내용을 보십시오.</span><span class="sxs-lookup"><span data-stu-id="e6afc-123">After you finish the lessons in this tutorial, refer to the following topics for more information about Database Engine Tuning Advisor:</span></span>  
  
-   <span data-ttu-id="e6afc-124">[Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md) - 이 도구로 태스크를 수행하는 방법에 대한 설명</span><span class="sxs-lookup"><span data-stu-id="e6afc-124">[Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md) for descriptions of how to perform tasks with this tool.</span></span>  
  
-   <span data-ttu-id="e6afc-125">[dta Utility](dta-utility.md) - 유틸리티 작업을 제어하는 데 사용할 수 있는 명령 프롬프트 유틸리티 및 선택적 XML 파일에 대한 참조 자료</span><span class="sxs-lookup"><span data-stu-id="e6afc-125">[dta Utility](dta-utility.md) for reference material on the command prompt utility and the optional XML file you can use to control the operation of the utility.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="e6afc-126">다음 단원</span><span class="sxs-lookup"><span data-stu-id="e6afc-126">Next Lesson</span></span>  
 [<span data-ttu-id="e6afc-127">1단원: 데이터베이스 엔진 튜닝 관리자 기본 탐색</span><span class="sxs-lookup"><span data-stu-id="e6afc-127">Lesson 1: Basic Navigation in Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
