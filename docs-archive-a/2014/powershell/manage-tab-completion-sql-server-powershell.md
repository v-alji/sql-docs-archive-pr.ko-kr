---
title: 탭 완성 기능 관리(SQL Server PowerShell) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 6296848a-890f-4ad3-8d9f-92ed6a79aa00
author: stevestein
ms.author: sstein
ms.openlocfilehash: 72bcf96245c536d6ea444bc1d7964b7579e793c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661204"
---
# <a name="manage-tab-completion-sql-server-powershell"></a><span data-ttu-id="89b06-102">탭 완성 기능 관리(SQL Server PowerShell)</span><span class="sxs-lookup"><span data-stu-id="89b06-102">Manage Tab Completion (SQL Server PowerShell)</span></span>
  <span data-ttu-id="89b06-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 스냅인에 도입된 3개 시스템 변수(`$SqlServerMaximumTabCompletion`, `$SqlServerMaximumChildItems` 및 `$SqlServerIncludeSystemObjects`)를 사용하여 Windows PowerShell 탭 완성 기능을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b06-103">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell snap-ins introduce three variables (`$SqlServerMaximumTabCompletion`, `$SqlServerMaximumChildItems`, and `$SqlServerIncludeSystemObjects`) to control Windows PowerShell tab completion.</span></span> <span data-ttu-id="89b06-104">탭 완성 기능은 이름이 입력한 문자열로 시작하는 항목의 테이블을 반환하여 사용자 입력을 줄여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="89b06-104">Tab completion reduces the amount of typing you must do by returning tables of items whose names start with the string you are typing.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="89b06-105">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="89b06-105">Before You Begin</span></span>  
 <span data-ttu-id="89b06-106">Windows PowerShell 탭 완성 기능을 사용하는 경우 특정 경로나 cmdlet 이름의 일부를 입력한 후 Tab 키를 누르면 입력한 이름과 일치하는 항목의 목록을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b06-106">With Windows PowerShell tab-completion, when you have typed part of a path or cmdlet name, you can hit the Tab key to get a list of the items whose names match what you have already typed.</span></span> <span data-ttu-id="89b06-107">그런 다음 나머지 이름을 입력하지 않고 목록에서 원하는 항목을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b06-107">You can then select the item you want from the list without having to type the rest of the name.</span></span>  
  
 <span data-ttu-id="89b06-108">개체가 많은 데이터베이스에서 작업 중인 경우에는 탭 완성 목록이 매우 커질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b06-108">If you are working in a database that has a lot of objects, the tab-completion lists can become very large.</span></span> <span data-ttu-id="89b06-109">뷰와 같은 일부 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 개체 유형에도 다수의 시스템 개체가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b06-109">Some [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] object types, such as views, also have large numbers of system objects.</span></span>  
  
 <span data-ttu-id="89b06-110">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 스냅인에 도입된 3개의 시스템 변수를 사용하여 탭 완성 기능 및 **Get-ChildItem**에서 제공하는 정보의 양을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b06-110">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] snap-ins introduces three system variables that you can use to control the amount of information presented by tab-completion and **Get-ChildItem**.</span></span>  
  
 <span data-ttu-id="89b06-111">**$SqlServerMaximumTabCompletion =** *n*</span><span class="sxs-lookup"><span data-stu-id="89b06-111">**$SqlServerMaximumTabCompletion =** *n*</span></span>  
 <span data-ttu-id="89b06-112">탭 완성 목록에 포함할 최대 개체 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="89b06-112">Specifies the maximum number of objects to include in a tab-completion list.</span></span> <span data-ttu-id="89b06-113">개체 수가 *n* 보다 큰 경로 노드에서 Tab 키를 누르면 탭 완성 목록이 *n*개까지 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="89b06-113">If you select Tab at a path node having more than *n* objects, the tab-completion list is truncated at *n*.</span></span> <span data-ttu-id="89b06-114">*n* 은 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="89b06-114">*n* is an integer.</span></span> <span data-ttu-id="89b06-115">0은 기본 설정이며 나열되는 개체 수에 제한이 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="89b06-115">0 is the default setting, and means there is no limit to the number of objects listed.</span></span>  
  
 <span data-ttu-id="89b06-116">**$SqlServerMaximumChildItems =** *n*</span><span class="sxs-lookup"><span data-stu-id="89b06-116">**$SqlServerMaximumChildItems =** *n*</span></span>  
 <span data-ttu-id="89b06-117">**Get-ChildItem**에서 표시하는 최대 개체 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="89b06-117">Specifies the maximum number of objects displayed by **Get-ChildItem**.</span></span> <span data-ttu-id="89b06-118">**Get-ChildItem** 이 개체 수가 *n* 보다 큰 경로 노드에서 실행되는 경우 목록은 *n*개까지 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="89b06-118">If **Get-ChildItem** is run at a path node having more than *n* objects, the list is truncated at *n*.</span></span> <span data-ttu-id="89b06-119">*n* 은 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="89b06-119">*n* is an integer.</span></span> <span data-ttu-id="89b06-120">0은 기본 설정이며 나열되는 개체 수에 제한이 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="89b06-120">0 is the default setting, and means there is no limit to the number of objects listed.</span></span>  
  
 <span data-ttu-id="89b06-121">**$SqlServerIncludeSystemObjects =** { **$True** | **$False** }</span><span class="sxs-lookup"><span data-stu-id="89b06-121">**$SqlServerIncludeSystemObjects =** { **$True** | **$False** }</span></span>  
 <span data-ttu-id="89b06-122">**$True**인 경우 탭 완성 기능 및 **Get-ChildItem**에서 시스템 개체를 표시하고,</span><span class="sxs-lookup"><span data-stu-id="89b06-122">If **$True**, system objects are displayed by tab-completion and **Get-ChildItem**.</span></span> <span data-ttu-id="89b06-123">**$False**인 경우에는 시스템 개체를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="89b06-123">If **$False**, no system objects are displayed.</span></span> <span data-ttu-id="89b06-124">기본 설정은 **$False**입니다.</span><span class="sxs-lookup"><span data-stu-id="89b06-124">The default setting is **$False**.</span></span>  
  
## <a name="set-the-sql-server-tab-completion-variables"></a><span data-ttu-id="89b06-125">SQL Server 탭 완성 변수 설정</span><span class="sxs-lookup"><span data-stu-id="89b06-125">Set the SQL Server Tab Completion Variables</span></span>  
 <span data-ttu-id="89b06-126">변수를 기본값이 아닌 다른 값으로 변경하려면 변수를 새 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="89b06-126">For any of the variables you want to change from the default value, set the variable to the new value.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="89b06-127">예제(PowerShell)</span><span class="sxs-lookup"><span data-stu-id="89b06-127">Example (PowerShell)</span></span>  
 <span data-ttu-id="89b06-128">다음 예에서는 3개 변수를 모두 설정하고 해당 설정을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="89b06-128">The following example sets all three variables and lists their settings:</span></span>  
  
```powershell
$SqlServerMaximumTabCompletion = 20  
$SqlServerMaximumChildItems = 10  
$SqlServerIncludeSystemObjects = $False  
dir variable:sqlserver*  
```  
  
## <a name="see-also"></a><span data-ttu-id="89b06-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="89b06-129">See Also</span></span>  
 [<span data-ttu-id="89b06-130">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="89b06-130">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
