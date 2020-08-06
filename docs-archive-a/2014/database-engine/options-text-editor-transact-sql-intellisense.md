---
title: 옵션 (텍스트 편집기-Transact-sql-IntelliSense) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.SQL.Advanced
- VS.ToolsOptionsPages.Text_Editor.SQL_Server_Tools.Advanced
dev_langs:
- TSQL
ms.assetid: 1855d916-5bf9-4d94-b0fb-9f9bb05ff950
author: rothja
ms.author: jroth
ms.openlocfilehash: 2d8f9c865516dc5e4c0ddadbdc908a9b4c8ec366
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652989"
---
# <a name="options-text-editor-transact-sql-intellisense"></a><span data-ttu-id="25a27-102">옵션 (텍스트 편집기-Transact-sql-IntelliSense)</span><span class="sxs-lookup"><span data-stu-id="25a27-102">Options (Text Editor-Transact-SQL-IntelliSense)</span></span>
  <span data-ttu-id="25a27-103">**옵션** 대화 상자를 사용하여 [!INCLUDE[ssDE](../includes/ssde-md.md)] 쿼리 편집기에 대한 IntelliSense 설정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25a27-103">The **Options** dialog box lets you change the IntelliSense settings for the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor.</span></span> <span data-ttu-id="25a27-104">이러한 설정은 **도구** 메뉴에서 **옵션**을 클릭하고 **텍스트 편집기** 폴더와 **Transact-SQL** 폴더를 차례로 확장한 다음 **고급**을 클릭하면 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25a27-104">These settings are available when, on the **Tools** menu, you click **Options**, expand the **Text Editor** folder, expand the **Transact-SQL** folder, and then click **Advanced**.</span></span>  
  
## <a name="transact-sql-intellisense-settings"></a><span data-ttu-id="25a27-105">Transact-SQL IntelliSense 설정</span><span class="sxs-lookup"><span data-stu-id="25a27-105">Transact-SQL IntelliSense Settings</span></span>  
 <span data-ttu-id="25a27-106">[!INCLUDE[ssDE](../includes/ssde-md.md)] 쿼리 편집기에 대한 IntelliSense 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="25a27-106">Specifies the IntelliSense options for the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor.</span></span>  
  
### <a name="enable-intellisense"></a><span data-ttu-id="25a27-107">IntelliSense 사용</span><span class="sxs-lookup"><span data-stu-id="25a27-107">Enable IntelliSense</span></span>  
 <span data-ttu-id="25a27-108">IntelliSense 기능을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="25a27-108">Enables the IntelliSense features.</span></span> <span data-ttu-id="25a27-109">이 상자가 선택되어 있지 않으면 특정 IntelliSense 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="25a27-109">When this box is not selected, the specific IntelliSense options are unavailable.</span></span> <span data-ttu-id="25a27-110">이 확인란은 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25a27-110">By default, this check box is selected.</span></span>  
  
 <span data-ttu-id="25a27-111">**오류에 밑줄 표시**</span><span class="sxs-lookup"><span data-stu-id="25a27-111">**Underline errors**</span></span>  
 <span data-ttu-id="25a27-112">쿼리 창에서 [!INCLUDE[tsql](../includes/tsql-md.md)] 문에 있는 구문 및 의미 체계 오류를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="25a27-112">Identifies syntax and semantic errors in [!INCLUDE[tsql](../includes/tsql-md.md)] statements in the query window.</span></span> <span data-ttu-id="25a27-113">모든 오류와 경고는 빨간색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="25a27-113">All errors and warnings appear in red.</span></span> <span data-ttu-id="25a27-114">오류와 경고는 IntelliSense를 구현한 [!INCLUDE[tsql](../includes/tsql-md.md)] 문에 대해서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="25a27-114">Errors and warnings are supported only for the [!INCLUDE[tsql](../includes/tsql-md.md)] statements for which IntelliSense has been implemented.</span></span> <span data-ttu-id="25a27-115">이 확인란은 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25a27-115">By default, this check box is selected.</span></span>  
  
 <span data-ttu-id="25a27-116">**개요 문 표시**</span><span class="sxs-lookup"><span data-stu-id="25a27-116">**Outline statements**</span></span>  
 <span data-ttu-id="25a27-117">파일을 열 때 개요 기능을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="25a27-117">Enables the outlining feature when a file is opened.</span></span> <span data-ttu-id="25a27-118">이렇게 하면 축소 가능한 [!INCLUDE[tsql](../includes/tsql-md.md)] 코드 블록이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="25a27-118">This creates collapsible blocks of [!INCLUDE[tsql](../includes/tsql-md.md)] code.</span></span> <span data-ttu-id="25a27-119">이 확인란은 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25a27-119">By default, this check box is selected.</span></span>  
  
 <span data-ttu-id="25a27-120">**최대 스크립트 크기**</span><span class="sxs-lookup"><span data-stu-id="25a27-120">**Maximum script size**</span></span>  
 <span data-ttu-id="25a27-121">IntelliSense 기능을 사용할 수 없게 하는 크기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="25a27-121">Specifies the size at which IntelliSense functionality is disabled.</span></span> <span data-ttu-id="25a27-122">스크립트가 지정된 크기를 초과하면 경고 메시지가 나타나고</span><span class="sxs-lookup"><span data-stu-id="25a27-122">If a script exceeds the specified size, a warning message is issued.</span></span> <span data-ttu-id="25a27-123">해당 편집기 창에서 색 구분 기능을 제외한 모든 IntelliSense 기능을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="25a27-123">All IntelliSense features, except color coding, are disabled for that editor window.</span></span> <span data-ttu-id="25a27-124">스크립트 크기가 제한 크기 이내로 줄어들도록 텍스트를 충분히 삭제하면 IntelliSense를 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25a27-124">IntelliSense is reenabled when enough text is deleted to reduce the script size to under the limit.</span></span> <span data-ttu-id="25a27-125">IntelliSense를 대용량 스크립트에 사용하면 컴퓨터의 성능이 느려질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25a27-125">Enabling IntelliSense for large script sizes can decrease performance on slow computers.</span></span> <span data-ttu-id="25a27-126">허용되는 크기는 100KB, 500KB, 1MB, 2MB 및 제한 없음입니다.</span><span class="sxs-lookup"><span data-stu-id="25a27-126">The allowed sizes are 100 KB, 500 KB, 1 MB, 2 MB, and Unlimited.</span></span> <span data-ttu-id="25a27-127">기본값은 1MB입니다.</span><span class="sxs-lookup"><span data-stu-id="25a27-127">The default is 1 MB.</span></span>  
  
 <span data-ttu-id="25a27-128">**기본 제공 함수 이름의 대/소문자 구분**</span><span class="sxs-lookup"><span data-stu-id="25a27-128">**Casing for built-in function names**</span></span>  
 <span data-ttu-id="25a27-129">완성 목록에 포함된 기본 제공 [!INCLUDE[tsql](../includes/tsql-md.md)] 함수 이름에서 대문자(예: DATEADD) 또는 소문자(예: dateadd) 중 어떤 문자를 사용할 것인지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="25a27-129">Specifies whether the names of built-in [!INCLUDE[tsql](../includes/tsql-md.md)] functions that are included in completion lists use uppercase letters, such as DATEADD; or lowercase letters, such as dateadd.</span></span> <span data-ttu-id="25a27-130">사용 중인 [!INCLUDE[tsql](../includes/tsql-md.md)] 코딩 규칙에 가장 적합한 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="25a27-130">Select the option that best matches the [!INCLUDE[tsql](../includes/tsql-md.md)] coding conventions that you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25a27-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="25a27-131">See Also</span></span>  
 [<span data-ttu-id="25a27-132">IntelliSense &#40;SQL Server Management Studio&#41;문제 해결</span><span class="sxs-lookup"><span data-stu-id="25a27-132">Troubleshooting IntelliSense &#40;SQL Server Management Studio&#41;</span></span>](../relational-databases/scripting/troubleshooting-intellisense.md)  
  
  
