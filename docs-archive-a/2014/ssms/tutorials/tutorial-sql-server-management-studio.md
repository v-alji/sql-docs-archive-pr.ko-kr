---
title: '자습서: SQL Server Management Studio | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.tutorialstart.ssms.f1
helpviewer_keywords:
- projects [SQL Server Management Studio], tutorials
- templates [SQL Server], SQL Server Management Studio
- source controls [SQL Server Management Studio], tutorials
- Help [SQL Server], SQL Server Management Studio
- tutorials [SQL Server Management Studio]
- Transact-SQL tutorials
- solutions [SQL Server Management Studio], tutorials
- SQL Server Management Studio [SQL Server], tutorials
- scripts [SQL Server], SQL Server Management Studio
ms.assetid: d2bade70-07cf-4d94-b5d2-88aecb538ed1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8206fea828d6169975dc1d026a22e18e682f71e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660278"
---
# <a name="tutorial-sql-server-management-studio"></a><span data-ttu-id="07a1e-102">자습서: SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="07a1e-102">Tutorial: SQL Server Management Studio</span></span>
  <span data-ttu-id="07a1e-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 자습서에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인프라 관리를 위한 통합 환경을 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="07a1e-103">The [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] tutorial introduces you to the integrated environment for managing your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] infrastructure.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="07a1e-104">는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스 구성, 모니터링 및 관리를 위한 그래픽 인터페이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="07a1e-104">presents a graphical interface for configuring, monitoring, and administering instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="07a1e-105">또한 데이터베이스 및 데이터 웨어하우스 등 애플리케이션에 사용되는 데이터 계층 구성 요소를 배포, 모니터링 및 업그레이드할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a1e-105">It also allows you to deploy, monitor, and upgrade the data-tier components used by your applications, such as databases and data warehouses.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="07a1e-106">는 스크립트 편집 및 디버그를 위한 [!INCLUDE[tsql](../../includes/tsql-md.md)], MDX, DMX 및 XML 언어 편집기도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="07a1e-106">also provides [!INCLUDE[tsql](../../includes/tsql-md.md)], MDX, DMX, and XML language editors for editing and debugging scripts.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="07a1e-107">학습 내용</span><span class="sxs-lookup"><span data-stu-id="07a1e-107">What You Will Learn</span></span>  
 <span data-ttu-id="07a1e-108">이 자습서를 통해 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 의 정보 표시 방식과 기능을 이용하는 방법을 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a1e-108">This tutorial will help you understand the presentation of information in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and how to take advantage of the features.</span></span> <span data-ttu-id="07a1e-109">이 자습서는 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]를 제외한 모든 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 포함된 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]의 전체 설치에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a1e-109">Note that this tutorial applies to the complete installation of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] that is included with all editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] except [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span> <span data-ttu-id="07a1e-110">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]의 기본 설치와 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]와 함께 제공되는 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 설치의 경우 이 자습서에 설명된 것과 기능이 약간 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a1e-110">Functionality for basic installations of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and for [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] installations that ship with [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] is slightly different than what is presented in this tutorial.</span></span>  
  
 <span data-ttu-id="07a1e-111">실습을 통해 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 에 익숙해지는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="07a1e-111">The best way to get acquainted with [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] is through hands-on practice.</span></span> <span data-ttu-id="07a1e-112">이 자습서에서는 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 의 구성 요소를 관리하는 방법과 정기적으로 사용하는 기능을 찾는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="07a1e-112">This tutorial will teach you how to manage the components of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and how to find the features that you use regularly.</span></span>  
  
 <span data-ttu-id="07a1e-113">이 자습서는 다음 3개의 단원으로 이루어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a1e-113">This tutorial is divided into three lessons:</span></span>  
  
 [<span data-ttu-id="07a1e-114">1단원: SQL Server Management Studio의 기본 탐색</span><span class="sxs-lookup"><span data-stu-id="07a1e-114">Lesson 1: Basic Navigation in SQL Server Management Studio</span></span>](lesson-1-basic-navigation-in-sql-server-management-studio.md)  
 <span data-ttu-id="07a1e-115">이 단원에서는 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]의 구성 요소를 사용하는 방법, 환경 레이아웃을 다시 구성하는 방법 및 기본 레이아웃을 복원하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="07a1e-115">In this lesson you will learn how to use the components of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], how to reconfigure the environment layout, and how to restore the default layout.</span></span>  
  
 [<span data-ttu-id="07a1e-116">2단원: Transact-SQL 작성</span><span class="sxs-lookup"><span data-stu-id="07a1e-116">Lesson 2: Writing Transact-SQL</span></span>](lesson-2-writing-transact-sql.md)  
 <span data-ttu-id="07a1e-117">이 단원에서는 쿼리 편집기를 여는 방법, 코드를 관리하는 방법 및 쿼리 편집기의 다른 새로운 기능을 사용하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="07a1e-117">In this lesson, you will learn how to open Query Editor, how to manage code, and how to use the other new features of Query Editor.</span></span>  
  
 [<span data-ttu-id="07a1e-118">3단원: 템플릿, 솔루션 및 스크립트 프로젝트 작업</span><span class="sxs-lookup"><span data-stu-id="07a1e-118">Lesson 3: Working with Templates, Solutions, and Script Projects</span></span>](lesson-3-working-with-templates-solutions-and-script-projects.md)  
 <span data-ttu-id="07a1e-119">이 단원에서는 템플릿을 사용하여 솔루션 및 프로젝트에 스크립트를 구성하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="07a1e-119">In this lesson you will learn how to use templates, and organize scripts into solutions and projects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07a1e-120">요구 사항</span><span class="sxs-lookup"><span data-stu-id="07a1e-120">Requirements</span></span>  
 <span data-ttu-id="07a1e-121">이 자습서는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]에는 익숙하지 않지만 데이터베이스 개념과 [!INCLUDE[tsql](../../includes/tsql-md.md)] 언어에는 익숙한 경험 있는 데이터베이스 관리자와 데이터베이스 개발자를 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="07a1e-121">This tutorial is intended for experienced database administrators and database developers who are not familiar with [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], but who are who are familiar with database concepts and the [!INCLUDE[tsql](../../includes/tsql-md.md)] language.</span></span>  
  
 <span data-ttu-id="07a1e-122">이 자습서를 사용하려면 시스템에 다음 항목이 설치되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07a1e-122">Your system must have the following installed to use this tutorial:</span></span>  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="07a1e-123">이상 버전과 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 샘플 데이터베이스.</span><span class="sxs-lookup"><span data-stu-id="07a1e-123">or a later version with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample databases.</span></span> <span data-ttu-id="07a1e-124">보안을 위해 예제 데이터베이스는 기본적으로 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07a1e-124">To enhance security, the sample databases are not installed by default.</span></span> <span data-ttu-id="07a1e-125">예제 데이터베이스를 설치하려면 [SQL Server 예제 및 예제 데이터베이스](http://sqlserversamples.codeplex.com)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07a1e-125">To install the sample databases, see [Installing SQL Server Samples and Sample Databases](http://sqlserversamples.codeplex.com).</span></span>  
  
-   <span data-ttu-id="07a1e-126">Internet Explorer 9.0 이상</span><span class="sxs-lookup"><span data-stu-id="07a1e-126">Internet Explorer 9.0 or later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07a1e-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="07a1e-127">See Also</span></span>  
 [<span data-ttu-id="07a1e-128">데이터베이스 엔진 자습서</span><span class="sxs-lookup"><span data-stu-id="07a1e-128">Database Engine Tutorials</span></span>](../../relational-databases/database-engine-tutorials.md)  
  
  
