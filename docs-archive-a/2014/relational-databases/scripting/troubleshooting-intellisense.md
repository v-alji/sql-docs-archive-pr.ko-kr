---
title: 문제 해결 IntelliSense
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- unavailable options [IntelliSense]
- IntelliSense [SQL Server], troubleshooting
- IntelliSense [SQL Server], unavailable options
- troubleshooting [IntelliSense]
ms.assetid: 4b72ffc6-aea2-4e11-ab36-fa2de4d7bcc5
author: rothja
ms.author: jroth
ms.openlocfilehash: 087baf616fc215c480ae78621623cbe1ed512b57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733811"
---
# <a name="troubleshooting-intellisense-sql-server-management-studio"></a><span data-ttu-id="db072-102">IntelliSense(SQL Server Management Studio) 문제 해결</span><span class="sxs-lookup"><span data-stu-id="db072-102">Troubleshooting IntelliSense (SQL Server Management Studio)</span></span>
  <span data-ttu-id="db072-103">다음과 같은 몇몇 경우에서는 IntelliSense 옵션이 제대로 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db072-103">There are certain cases when the IntelliSense options might not work as you expect.</span></span>  
  
## <a name="conditions-that-affect-intellisense"></a><span data-ttu-id="db072-104">IntelliSense에 영향을 주는 조건</span><span class="sxs-lookup"><span data-stu-id="db072-104">Conditions That Affect IntelliSense</span></span>  
 <span data-ttu-id="db072-105">IntelliSense 동작에 영향을 줄 수 있는 조건은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="db072-105">The following conditions might affect the behavior of IntelliSense:</span></span>  
  
-   <span data-ttu-id="db072-106">커서 위에 코드 오류가 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="db072-106">There is a code error above the cursor.</span></span>  
  
     <span data-ttu-id="db072-107">삽입 지점 위치 위에 불완전한 문이나 다른 코딩 오류가 있을 경우 IntelliSense는 코드 요소를 구문 분석하지 못할 수 있으며 따라서 작동하지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db072-107">If there is an incomplete statement or other coding error above the location of the insertion point, IntelliSense may be unable to parse the code elements, and therefore will not work.</span></span> <span data-ttu-id="db072-108">해당 코드를 주석으로 처리하여 IntelliSense를 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db072-108">You can comment out the applicable code to enable IntelliSense again.</span></span>  
  
-   <span data-ttu-id="db072-109">삽입 지점이 코드 주석 안에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db072-109">The insertion point is inside a code comment.</span></span>  
  
     <span data-ttu-id="db072-110">원본 파일의 주석 안에 삽입 지점이 있을 경우 IntelliSense 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db072-110">IntelliSense options are not available when the insertion point is within a comment in your source file.</span></span>  
  
-   <span data-ttu-id="db072-111">삽입 지점이 문자열 리터럴 안에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db072-111">The insertion point is inside a string literal.</span></span>  
  
     <span data-ttu-id="db072-112">다음과 같이 문자열 리터럴을 둘러싸는 따옴표 안에 삽입 지점이 있을 경우 IntelliSense 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db072-112">IntelliSense options are not available when the insertion point is inside the quotation marks around a string literal, for example:</span></span>  
  
     `WHERE FirstName LIKE 'Patri%|'`  
  
-   <span data-ttu-id="db072-113">자동 옵션이 해제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="db072-113">The automatic options are turned off.</span></span>  
  
     <span data-ttu-id="db072-114">기본적으로 대부분의 IntelliSense 기능은 자동으로 작동하지만 임의의 기능을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db072-114">Many IntelliSense features work automatically by default, but you can disable any feature.</span></span>  
  
     <span data-ttu-id="db072-115">자동 문 완성이 해제된 경우에도 IntelliSense 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db072-115">Even when automatic statement completion is disabled, you can use an IntelliSense feature.</span></span> <span data-ttu-id="db072-116">자세한 내용은 [IntelliSense 구성&#40;SQL Server Management Studio&#41;](configure-intellisense-sql-server-management-studio.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="db072-116">For more information, see [Configure IntelliSense &#40;SQL Server Management Studio&#41;](configure-intellisense-sql-server-management-studio.md).</span></span>  
  
## <a name="database-engine-query-intellisense"></a><span data-ttu-id="db072-117">데이터베이스 엔진 쿼리 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="db072-117">Database Engine Query IntelliSense</span></span>  
 <span data-ttu-id="db072-118">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 쿼리 편집기에는 다음과 같은 문제가 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="db072-118">The following issues apply to the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] Query Editor:</span></span>  
  
-   <span data-ttu-id="db072-119">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기의 IntelliSense 기능이 일부 [!INCLUDE[tsql](../../includes/tsql-md.md)] 구문 요소를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db072-119">The IntelliSense functionality of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor does not support all [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax elements.</span></span> <span data-ttu-id="db072-120">매개 변수 도움말은 일부 개체에서 확장 저장 프로시저와 같은 매개 변수를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db072-120">Parameter help does not support the parameters in some objects, such as extended stored procedures.</span></span> <span data-ttu-id="db072-121">자세한 내용은 [IntelliSense에서 지원되는 Transact-SQL 구문](transact-sql-syntax-supported-by-intellisense.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="db072-121">For more information, see [Transact-SQL Syntax Supported by IntelliSense](transact-sql-syntax-supported-by-intellisense.md).</span></span>  
  
-   <span data-ttu-id="db072-122">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기가 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 이상의 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 인스턴스에 연결되는 경우에만 IntelliSense를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db072-122">IntelliSense is only available when the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor is connected to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] from [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later.</span></span> <span data-ttu-id="db072-123">쿼리 편집기가 이전 버전의 [!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결되는 경우에는 IntelliSense를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db072-123">IntelliSense is not available when the Query Editor is connected to earlier versions of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="db072-124">SQLCMD 모드를 설정하면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기에서 IntelliSense가 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="db072-124">IntelliSense is turned off in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor when the SQLCMD mode is set on.</span></span>  
  
-   <span data-ttu-id="db072-125">IntelliSense 기능은 편집기 창이 데이터베이스에 연결된 후 다른 연결에서 만든 데이터베이스 개체를 처리하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db072-125">IntelliSense functionality does not cover database objects created by another connection after your editor window connected to the database.</span></span> <span data-ttu-id="db072-126">개체가 완성 목록과 같은 IntelliSense 기능에서 누락되어 있는 경우 다음 세 가지 메커니즘 중 하나를 선택하여 편집기 창의 개체 캐시를 새로 고칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db072-126">If objects are missing from IntelliSense features such as completion lists, you can choose one of these three mechanisms to refresh the cache of objects for your editor window:</span></span>  
  
    -   <span data-ttu-id="db072-127">**편집** 메뉴를 선택하고 **IntelliSense**를 선택한 다음 **로컬 캐시 새로 고침**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="db072-127">Select the **Edit** menu, select **IntelliSense**, then select **Refresh Local Cache**.</span></span>  
  
    -   <span data-ttu-id="db072-128">바로 가기 키 Ctrl+Shift+R을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db072-128">Use the CTRL+Shift+R keyboard shortcut.</span></span>  
  
    -   <span data-ttu-id="db072-129">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에서 편집기 창의 연결을 끊은 후 다시 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="db072-129">Disconnect your editor window from the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and reconnect.</span></span>  
  
-   <span data-ttu-id="db072-130">사용자가 권한을 가지고 있지 않은 데이터베이스 개체는 완성 목록에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db072-130">Completion lists do not include database objects for which you do not have permissions.</span></span> <span data-ttu-id="db072-131">IntelliSense 플래그는 사용자가 권한을 가지고 있는 개체를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="db072-131">IntelliSense flags references to objects for which you do have permissions.</span></span> <span data-ttu-id="db072-132">예를 들어 다른 사용자가 작성한 스크립트를 열면 스크립트 작성한 사용자만 권한을 가지고 있고 사용자 자신은 권한을 가지고 있지 않은 개체에 대한 모든 참조는 올바르지 않은 것으로 플래그가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="db072-132">For example, if you open a script that is written by someone else, any references to objects for which that person has permissions and you do not are flagged as incorrect.</span></span>  
  
-   <span data-ttu-id="db072-133">[!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스와의 연결이 끊어지면 완성 목록이 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db072-133">Completion lists might stop working if you lose the connection to the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="db072-134">인스턴스에 다시 연결하십시오.</span><span class="sxs-lookup"><span data-stu-id="db072-134">Reconnect to the instance.</span></span>  
  
  
