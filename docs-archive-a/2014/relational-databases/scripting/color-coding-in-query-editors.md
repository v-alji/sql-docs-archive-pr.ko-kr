---
title: 쿼리 편집기에서 코드 색상 지정
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Query Editor [SQL Server Management Studio], color coding
- color coding [Query Editor]
ms.assetid: 802882dc-c997-4e3f-8a01-994bb43169ae
author: rothja
ms.author: jroth
ms.openlocfilehash: f23b37cec051b52082cdb310a134a4603423b8c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649445"
---
# <a name="color-coding-in-query-editors"></a><span data-ttu-id="71669-102">쿼리 편집기에서 코드 색상 지정</span><span class="sxs-lookup"><span data-stu-id="71669-102">Color Coding in Query Editors</span></span>
  <span data-ttu-id="71669-103">코드 편집기에 입력하는 텍스트에는 범주가 할당되고 각 범주는 색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="71669-103">The text entered in the code editors is assigned a category; each category is identified by a color.</span></span> <span data-ttu-id="71669-104">색을 통해 코드의 텍스트를 빠르게 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71669-104">The colors help you quickly find text in your code.</span></span> <span data-ttu-id="71669-105">예를 들어 주석은 진한 녹색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="71669-105">For example, comments stand out in dark green.</span></span> <span data-ttu-id="71669-106">다음 표에서는 가장 일반적인 색을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="71669-106">The following table lists the most common colors.</span></span> <span data-ttu-id="71669-107">**도구**, **옵션** 메뉴를 사용하여 전체 색 목록과 해당 범주를 볼 수 있으며 사용자 지정 색 구성표를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71669-107">You can view the whole list of colors and their categories, and configure a custom color scheme by using the **Tools**, **Options** menu.</span></span> <span data-ttu-id="71669-108">기본 색을 변경하는 방법은 [Change Font Color, Size, and Style](change-font-color-size-and-style.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="71669-108">For more information about how to change the default colors, see [Change Font Color, Size, and Style](change-font-color-size-and-style.md).</span></span>  
  
## <a name="default-code-colors"></a><span data-ttu-id="71669-109">기본 코드 색</span><span class="sxs-lookup"><span data-stu-id="71669-109">Default Code Colors</span></span>  
  
|<span data-ttu-id="71669-110">색</span><span class="sxs-lookup"><span data-stu-id="71669-110">Color</span></span>|<span data-ttu-id="71669-111">Category</span><span class="sxs-lookup"><span data-stu-id="71669-111">Category</span></span>|  
|-----------|--------------|  
|<span data-ttu-id="71669-112">빨강</span><span class="sxs-lookup"><span data-stu-id="71669-112">Red</span></span>|<span data-ttu-id="71669-113">SQL 문자열</span><span class="sxs-lookup"><span data-stu-id="71669-113">SQL string</span></span>|  
|<span data-ttu-id="71669-114">진한 녹색</span><span class="sxs-lookup"><span data-stu-id="71669-114">Dark green</span></span>|<span data-ttu-id="71669-115">주석</span><span class="sxs-lookup"><span data-stu-id="71669-115">Comment</span></span>|  
|<span data-ttu-id="71669-116">은색 배경에 검정</span><span class="sxs-lookup"><span data-stu-id="71669-116">Black on silver background</span></span>|<span data-ttu-id="71669-117">SQLCMD 명령</span><span class="sxs-lookup"><span data-stu-id="71669-117">SQLCMD command</span></span>|  
|<span data-ttu-id="71669-118">자홍</span><span class="sxs-lookup"><span data-stu-id="71669-118">Magenta</span></span>|<span data-ttu-id="71669-119">시스템 함수</span><span class="sxs-lookup"><span data-stu-id="71669-119">System function</span></span>|  
|<span data-ttu-id="71669-120">녹색</span><span class="sxs-lookup"><span data-stu-id="71669-120">Green</span></span>|<span data-ttu-id="71669-121">시스템 테이블, 뷰 또는 테이블 반환 함수와</span><span class="sxs-lookup"><span data-stu-id="71669-121">System table, view, or table-valued function.</span></span> <span data-ttu-id="71669-122">시스템 스키마 sys 및 INFORMATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71669-122">Also, the system schemas sys and INFORMATION_SCHEMA.</span></span>|  
|<span data-ttu-id="71669-123">파랑</span><span class="sxs-lookup"><span data-stu-id="71669-123">Blue</span></span>|<span data-ttu-id="71669-124">키워드</span><span class="sxs-lookup"><span data-stu-id="71669-124">Keyword</span></span>|  
|<span data-ttu-id="71669-125">청록</span><span class="sxs-lookup"><span data-stu-id="71669-125">Teal</span></span>|<span data-ttu-id="71669-126">줄 번호 또는 템플릿 매개 변수</span><span class="sxs-lookup"><span data-stu-id="71669-126">Line numbers or template parameter</span></span>|  
|<span data-ttu-id="71669-127">적갈색</span><span class="sxs-lookup"><span data-stu-id="71669-127">Maroon</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="71669-128">저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="71669-128">stored procedure</span></span>|  
|<span data-ttu-id="71669-129">진한 회색</span><span class="sxs-lookup"><span data-stu-id="71669-129">Dark gray</span></span>|<span data-ttu-id="71669-130">연산자</span><span class="sxs-lookup"><span data-stu-id="71669-130">Operators</span></span>|  
  
## <a name="status-bar"></a><span data-ttu-id="71669-131">상태 표시줄</span><span class="sxs-lookup"><span data-stu-id="71669-131">Status Bar</span></span>  
 <span data-ttu-id="71669-132">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기 상태 표시줄에 다른 색상을 사용하도록 개체 탐색기에서 등록된 서버 또는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 서버를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71669-132">You can configure registered servers or [!INCLUDE[ssDE](../../includes/ssde-md.md)] servers in Object Explorer to have different colors in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor status bar.</span></span> <span data-ttu-id="71669-133">이렇게 하면 동시에 여러 창이 열려 있을 때 각 편집기 창에 연결된 서버를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71669-133">This helps you identify which server each editor window is connected to when you have many windows open at the same time.</span></span> <span data-ttu-id="71669-134">상태 표시줄 색상 설정에 대한 자세한 내용은 [상태 표시줄&#40;데이터베이스 엔진 쿼리 편집기&#41;](status-bar-database-engine-query-editor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="71669-134">For more information about setting status bar colors, see [Status Bar &#40;Database Engine Query Editor&#41;](status-bar-database-engine-query-editor.md).</span></span>  
  
 <span data-ttu-id="71669-135">일부 유형의 편집기에는 상태 표시줄이 표시되지 않으며 여러 색상이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="71669-135">Some types of editors do not display the status bar, or do not support multiple colors.</span></span>  
  
  
