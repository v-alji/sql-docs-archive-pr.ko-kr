---
title: '3 단원: dta 명령 프롬프트 유틸리티 사용 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], tutorials
ms.assetid: 30f27f4d-8852-4b12-ba62-57f63e496f1d
author: stevestein
ms.author: sstein
ms.openlocfilehash: abbde02cd73e01937e6d0669c10f2db28da8a76e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727640"
---
# <a name="lesson-3-using-the-dta-command-prompt-utility"></a><span data-ttu-id="2c92b-102">3단원: dta 명령 프롬프트 유틸리티 사용</span><span class="sxs-lookup"><span data-stu-id="2c92b-102">Lesson 3: Using the dta Command Prompt Utility</span></span>
  <span data-ttu-id="2c92b-103">**dta** 명령 프롬프트 유틸리티는 데이터베이스 엔진 튜닝 관리자에서 제공하는 기능 외에도 많은 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2c92b-103">The **dta** command-prompt utility offers functionality in addition to that provided by the Database Engine Tuning Advisor.</span></span>  
  
 <span data-ttu-id="2c92b-104">자주 사용하는 XML 도구에서 데이터베이스 엔진 튜닝 관리자 XML 스키마를 사용하여 유틸리티의 입력 파일을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c92b-104">You can use your favorite XML tools to create input files for the utility by using the Database Engine Tuning Advisor XML schema.</span></span> <span data-ttu-id="2c92b-105">이 스키마는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 설치할 때 설치되며 C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Binn\schemas\sqlserver\2004\07\dta\dtaschema.xsd에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c92b-105">This schema is installed when you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and can be found at: C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Binn\schemas\sqlserver\2004\07\dta\dtaschema.xsd.</span></span>  
  
 <span data-ttu-id="2c92b-106">데이터베이스 엔진 튜닝 관리자 XML 스키마는 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409)에서 온라인으로도 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c92b-106">The Database Engine Tuning Advisor XML schema is also available online at [this Microsoft Web site](https://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409).</span></span>  
  
 <span data-ttu-id="2c92b-107">데이터베이스 엔진 튜닝 관리자 XML 스키마를 사용하면 튜닝 옵션을 보다 유연하게 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c92b-107">The Database Engine Tuning Advisor XML schema provides more flexibility to set tuning options.</span></span> <span data-ttu-id="2c92b-108">예를 들어 "가정(what-if)" 분석을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c92b-108">For example, it enables you to perform "what-if" analysis.</span></span> <span data-ttu-id="2c92b-109">"가정(what-if)" 분석에는 튜닝하려는 데이터베이스에 대해 일련의 기존 및 가상 물리적 디자인 구조를 지정한 다음 데이터베이스 엔진 튜닝 관리자로 분석하여 이 가상 물리적 디자인으로 쿼리 처리 성능이 개선될지 확인하는 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c92b-109">"What-if" analysis involves specifying a set of existing and hypothetical physical design structures for the database you want to tune, and then analyzing it with the Database Engine Tuning Advisor to find out whether this hypothetical physical design will improve query processing performance.</span></span> <span data-ttu-id="2c92b-110">이 분석 유형은 실제 구현 시 오버헤드를 발생시키지 않고 새 구성을 평가하는 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c92b-110">This type of analysis provides the advantage of evaluating the new configuration without incurring the overhead of actually implementing it.</span></span> <span data-ttu-id="2c92b-111">가상 물리적 디자인으로 원하는 성능 개선이 이루어지지 않으면 필요한 결과를 만드는 구성에 도달할 때까지 해당 디자인을 쉽게 변경하고 다시 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c92b-111">If your hypothetical physical design does not provide the performance improvements you want, it is easy to change it and analyze it again until you reach the configuration that produces the results you need.</span></span>  
  
 <span data-ttu-id="2c92b-112">또한 데이터베이스 엔진 튜닝 관리자 XML 스키마와 **dta** 명령 프롬프트 유틸리티를 사용하면 데이터베이스 엔진 튜닝 관리자 기능을 스크립트에 통합하여 다른 데이터베이스 디자인 도구에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c92b-112">In addition, using the Database Engine Tuning Advisor XML schema and the **dta** command-prompt utility, you can incorporate Database Engine Tuning Advisor functionality into scripts and use it with other database design tools.</span></span>  
  
 <span data-ttu-id="2c92b-113">데이터베이스 엔진 튜닝 관리자의 XML 입력 기능을 사용하는 방법은 이 단원에서 다루지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2c92b-113">Using the XML input functionality of Database Engine Tuning Advisor is beyond the scope of this lesson.</span></span>  
  
 <span data-ttu-id="2c92b-114">이 단원에서는 기본 **dta** 명령 프롬프트 유틸리티 구문을 소개하고 도움말에 액세스하는 방법과 단순 작업을 튜닝하는 데 유용한 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2c92b-114">This lesson provides an introduction to the basic **dta** command-prompt utility syntax, how to access help, and practice for tuning simple workloads.</span></span>  
  
 <span data-ttu-id="2c92b-115">다음 항목이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c92b-115">It contains the following topic:</span></span>  
  
-   <span data-ttu-id="2c92b-116">**Dta** 명령 프롬프트 유틸리티 시작 및 작업 튜닝</span><span class="sxs-lookup"><span data-stu-id="2c92b-116">Starting the **dta** Command Prompt Utility and Tuning a Workload</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="2c92b-117">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="2c92b-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="2c92b-118">dta 명령 프롬프트 유틸리티 시작 및 작업 튜닝</span><span class="sxs-lookup"><span data-stu-id="2c92b-118">Starting the dta Command Prompt Utility and Tuning a Workload</span></span>](lesson-1-1-tuning-a-workload.md)  
  
  
