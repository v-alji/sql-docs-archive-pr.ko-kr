---
title: 편집기 구성
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: e7c7a8ef-f561-4258-a7b6-c445dba69f87
author: rothja
ms.author: jroth
ms.openlocfilehash: 7e94cdbcd310814081e146e3fd0dbe75260d1240
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732543"
---
# <a name="configure-editors-sql-server-management-studio"></a><span data-ttu-id="34d2b-102">편집기 구성(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="34d2b-102">Configure Editors (SQL Server Management Studio)</span></span>
  <span data-ttu-id="34d2b-103">각 편집기에 대한 옵션을 구성하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 편집기 작업을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d2b-103">You can customize the operation of the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] editors by configuring the options for each editor.</span></span>  
  
## <a name="settng-editor-options"></a><span data-ttu-id="34d2b-104">편집기 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="34d2b-104">Settng Editor Options</span></span>  
 <span data-ttu-id="34d2b-105">대부분의 편집기 옵션은 **도구** 메뉴에서 **옵션...** 을 선택하여 표시되는 **옵션** 대화 상자에서 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="34d2b-105">Most of the editor options are set by using the **Tools** menu and selecting **Options...** to display an **Options** dialog.</span></span> <span data-ttu-id="34d2b-106">**옵션** 대화 상자의 왼쪽 창에서 **텍스트 편집기** 노드를 열어서 코드 및 텍스트 편집 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="34d2b-106">In the **Options** dialog, open the **Text Editor** node in the left pane to set code and text editing options.</span></span> <span data-ttu-id="34d2b-107">텍스트 편집기 아래의 노드가 특정 편집기에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d2b-107">The nodes under Text Editor apply to specific editors:</span></span>  
  
1.  <span data-ttu-id="34d2b-108">**모든 언어** – 이 노드를 사용하여 설정한 옵션이 모든 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 편집기에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d2b-108">**All Languages** - options set using this node apply to all of the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] editors.</span></span> <span data-ttu-id="34d2b-109">다른 노드를 통해 특정 편집기에 대한 다른 옵션을 설정하여 이러한 설정을 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d2b-109">You can override these settings by using the other nodes to set different options for a specific editor.</span></span>  
  
2.  <span data-ttu-id="34d2b-110">**일반 텍스트** – 이 노드를 사용하여 설정한 옵션은 MDX, DMX 및 텍스트 편집기에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d2b-110">**Plain Text** - options set using this node apply to the MDX, DMX, and text editors.</span></span>  
  
3.  <span data-ttu-id="34d2b-111">**Transact-SQL** - 이 노드를 사용하여 설정한 옵션은 데이터베이스 엔진 쿼리 편집기에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d2b-111">**Transact-SQL** - options set using this node apply to the Database Engine Query Editor.</span></span>  
  
4.  <span data-ttu-id="34d2b-112">**XML** – 이 노드를 사용하여 설정한 옵션은 XML for Analysis 편집기에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d2b-112">**XML** - options set using this node apply to the XML for Analysis editor.</span></span>  
  
 <span data-ttu-id="34d2b-113">**쿼리 실행** 또는 **쿼리 결과** 노드를 열어서 쿼리 실행과 결과 표시 방법을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d2b-113">Open the **Query Execution** or **Query Results** nodes to customize the execution of queries and how the results are displayed.</span></span>  
  
## <a name="editor-configuration-tasks"></a><span data-ttu-id="34d2b-114">편집기 구성 태스크</span><span class="sxs-lookup"><span data-stu-id="34d2b-114">Editor Configuration Tasks</span></span>  
  
|<span data-ttu-id="34d2b-115">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="34d2b-115">Task Description</span></span>|<span data-ttu-id="34d2b-116">항목</span><span class="sxs-lookup"><span data-stu-id="34d2b-116">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="34d2b-117">Windows 탐색기에서 지정된 확장명을 가진 파일을 두 번 클릭하여 편집기를 열도록 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="34d2b-117">Describes how to specify that an editor be opened by double-clicking on a file with a specified extension in Windows Explorer.</span></span>|[<span data-ttu-id="34d2b-118">파일 확장명을 코드 편집기에 연결</span><span class="sxs-lookup"><span data-stu-id="34d2b-118">Associate File Extensions to a Code Editor</span></span>](associate-file-extensions-to-a-code-editor.md)|  
|<span data-ttu-id="34d2b-119">코드와 텍스트를 더 쉽게 읽을 수 있도록 글꼴을 사용자 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="34d2b-119">Describes how to customize fonts to make code and text more readable.</span></span>|[<span data-ttu-id="34d2b-120">글꼴 색상, 크기 및 스타일 변경</span><span class="sxs-lookup"><span data-stu-id="34d2b-120">Change Font Color, Size, and Style</span></span>](change-font-color-size-and-style.md)|  
|<span data-ttu-id="34d2b-121">속성을 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="34d2b-121">Describes how to view properties.</span></span>|[<span data-ttu-id="34d2b-122">Management Studio에서 속성 창 사용</span><span class="sxs-lookup"><span data-stu-id="34d2b-122">Use the Properties Window in Management Studio</span></span>](use-the-properties-window-in-management-studio.md)|  
|<span data-ttu-id="34d2b-123">편집기 옵션 대화 상자의 F1 도움말 페이지 위치</span><span class="sxs-lookup"><span data-stu-id="34d2b-123">Location of the F1 help pages for the editor options dialogs.</span></span>|[<span data-ttu-id="34d2b-124">쿼리 옵션 페이지 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="34d2b-124">Query Options Pages F1 Help</span></span>](../../database-engine/query-options-pages-f1-help.md)|  
  
  
