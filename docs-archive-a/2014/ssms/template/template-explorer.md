---
title: 템플릿 탐색기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.wb.templates.f1
- sql12.swb.templates.explorer.f1
helpviewer_keywords:
- templates [SQL Server]
- SQL Server Management Studio [SQL Server], Template Explorer
- Template Explorer
- templates [Transact-SQL]
- templates [SQL Server], Template Explorer
ms.assetid: b9ee55c5-bb44-4f76-90ac-792d8d83b4c8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 35e7ee1e6261c759580df3a836f9cc4b500a77ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652506"
---
# <a name="template-explorer"></a><span data-ttu-id="f66ff-102">Template Explorer</span><span class="sxs-lookup"><span data-stu-id="f66ff-102">Template Explorer</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f66ff-103">다양한 템플릿을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ff-103">provides a variety of templates.</span></span> <span data-ttu-id="f66ff-104">템플릿은 데이터베이스에서 개체를 만드는 데 유용한 SQL 스크립트를 포함하는 상용구 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="f66ff-104">Templates are boilerplate files containing SQL scripts that help you create objects in a database.</span></span> <span data-ttu-id="f66ff-105">템플릿 탐색기를 처음 열면 AppData\Roaming\Microsoft\SQL Server Management Studio\120\templates 아래에 있는 C:\Users의 사용자 폴더에 템플릿 복사본이 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f66ff-105">The first time the template explorer is opened, a copy of the templates are placed in the user's folder in C:\Users, under AppData\Roaming\Microsoft\SQL Server Management Studio\120\Templates.</span></span>  
  
 <span data-ttu-id="f66ff-106">템플릿 탐색기에서 사용 가능한 템플릿을 찾은 다음 열어서 코드를 코드 편집기 창에 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ff-106">You can browse the available templates in Template Explorer, then open a template to incorporate the code into a code editor window.</span></span> <span data-ttu-id="f66ff-107">사용자 지정 템플릿을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ff-107">You can also create custom templates.</span></span>  
  
## <a name="benefits-of-templates"></a><span data-ttu-id="f66ff-108">템플릿의 이점</span><span class="sxs-lookup"><span data-stu-id="f66ff-108">Benefits of Templates</span></span>  
 <span data-ttu-id="f66ff-109">템플릿은 솔루션, 프로젝트 및 다양한 유형의 코드 편집기에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ff-109">Templates are available for solutions, projects, and various types of code editors.</span></span> <span data-ttu-id="f66ff-110">템플릿은 데이터베이스, 테이블, 뷰, 인덱스, 저장 프로시저, 트리거, 통계, 함수 등의 개체를 만드는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ff-110">Templates are available to create objects like databases, tables, views, indexes, stored procedures, triggers, statistics, and functions.</span></span> <span data-ttu-id="f66ff-111">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에 대한 확장된 속성, 연결된 서버, 로그인, 역할, 사용자, 템플릿을 만들어 서버를 관리하는 데 도움이 되는 템플릿도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ff-111">In addition, there are templates that help you to manage your server by creating extended properties, linked servers, logins, roles, users, and templates for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="f66ff-112">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 가 제공하는 템플릿 스크립트에는 코드를 사용자 지정할 수 있는 매개 변수가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ff-112">The template scripts provided with [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] contain parameters to help you customize the code.</span></span> <span data-ttu-id="f66ff-113">템플릿을 연 후 **템플릿 매개 변수 바꾸기** 대화 상자를 사용하여 스크립트에 값을 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ff-113">When you open a template, Use the **Replace Template Parameters** dialog box to insert values into the script.</span></span>  
  
 <span data-ttu-id="f66ff-114">자주 수행하는 태스크에 대한 사용자 지정 템플릿을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f66ff-114">Create custom templates for tasks you perform frequently.</span></span> <span data-ttu-id="f66ff-115">사용자 지정 스크립트를 기존 폴더로 구성하거나 새 폴더 구조를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f66ff-115">Organize your custom scripts into the existing folders or create a new folder structure.</span></span>  
  
 <span data-ttu-id="f66ff-116">또한 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기는 코드 조각을 지원합니다. 마우스 오른쪽 단추로 원하는 위치를 클릭하여 스크립트의 특정 위치에 코드 조각을 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ff-116">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query editor also supports code snippets, which can be inserted at specific locations in a script by right-clicking at that location.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="f66ff-117">관련 작업</span><span class="sxs-lookup"><span data-stu-id="f66ff-117">Related Tasks</span></span>  
 <span data-ttu-id="f66ff-118">템플릿을 시작하려면 다음 항목을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="f66ff-118">Use the following topics to get started with templates</span></span>  
  
|<span data-ttu-id="f66ff-119">**설명**</span><span class="sxs-lookup"><span data-stu-id="f66ff-119">**Description**</span></span>|<span data-ttu-id="f66ff-120">**항목**</span><span class="sxs-lookup"><span data-stu-id="f66ff-120">**Topic**</span></span>|  
|---------------------|---------------|  
|<span data-ttu-id="f66ff-121">템플릿의 코드를 코드 편집기 창에 통합하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ff-121">Describes how to incorporate the code from a template into a code editor window.</span></span>|[<span data-ttu-id="f66ff-122">템플릿 열기</span><span class="sxs-lookup"><span data-stu-id="f66ff-122">Open a Template</span></span>](open-a-template.md)|  
|<span data-ttu-id="f66ff-123">코드 편집기에서 템플릿을 연 후 템플릿 매개 변수 값을 바꾸는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ff-123">Describes how to replace template parameter values after opening a template in a code editor.</span></span>|[<span data-ttu-id="f66ff-124">템플릿 매개 변수 바꾸기</span><span class="sxs-lookup"><span data-stu-id="f66ff-124">Replace Template Parameters</span></span>](replace-template-parameters.md)|  
  
  
