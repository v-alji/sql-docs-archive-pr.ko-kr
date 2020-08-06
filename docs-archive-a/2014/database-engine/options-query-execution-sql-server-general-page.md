---
title: 옵션 (쿼리 실행-SQL Server-일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryExecution.SqlServer.SqlExecutionGeneral
ms.assetid: 3f8d59bc-3f97-4e5d-8b86-5ac670d20780
author: rothja
ms.author: jroth
ms.openlocfilehash: eaa95293636d02674fb720dcd1b8146279f78e72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660109"
---
# <a name="options-query-execution-sql-server-general-page"></a><span data-ttu-id="45406-102">옵션 (쿼리 실행-SQL Server-일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="45406-102">Options (Query Execution-SQL Server-General Page)</span></span>
  <span data-ttu-id="45406-103">이 페이지를 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 쿼리를 실행하는 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45406-103">Use this page to specify the options for running [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries.</span></span> <span data-ttu-id="45406-104">이러한 옵션의 변경 사항은 새로운 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 쿼리에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="45406-104">Changes to these options are only applied to new [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries.</span></span> <span data-ttu-id="45406-105">현재 쿼리에 대한 옵션을 변경하려면 **쿼리** 메뉴에서 **쿼리 옵션** 을 클릭하거나 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 쿼리 창에서 마우스 오른쪽 단추를 클릭한 다음 **쿼리 옵션**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="45406-105">To change the options for a current query, click **Query Options** on the **Query** menu, or in a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Query window right-click and select **Query Options**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="45406-106">옵션</span><span class="sxs-lookup"><span data-stu-id="45406-106">Options</span></span>  
 <span data-ttu-id="45406-107">**SET ROWCOUNT**</span><span class="sxs-lookup"><span data-stu-id="45406-107">**SET ROWCOUNT**</span></span>  
 <span data-ttu-id="45406-108">기본값 0은 모든 결과를 받을 때까지 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서 결과를 기다린다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="45406-108">The default value of 0 indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will wait for results until all results are received.</span></span> <span data-ttu-id="45406-109">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서 지정한 행 수를 받은 후 쿼리를 중단하려면 0보다 큰 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="45406-109">Provide a value greater than 0 if you want [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to halt the query after obtaining the specified number of rows.</span></span> <span data-ttu-id="45406-110">모든 행이 반환될 수 있도록 이 옵션을 해제하려면 SET ROWCOUNT 0을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="45406-110">To turn this option off (so that all rows are returned), specify SET ROWCOUNT 0.</span></span>  
  
 <span data-ttu-id="45406-111">**SET TEXTSIZE**</span><span class="sxs-lookup"><span data-stu-id="45406-111">**SET TEXTSIZE**</span></span>  
 <span data-ttu-id="45406-112">기본값인 2,147,483,647바이트는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 `text` 및 `ntext` 데이터 필드의 상한에 이르는 전체 데이터 필드를 제공한다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="45406-112">The default value of 2,147,483,647 bytes indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will provide complete data fields up to the limit of `text` and `ntext` data fields.</span></span> <span data-ttu-id="45406-113">값이 클 경우 결과를 제한하려면 보다 작은 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="45406-113">Provide a smaller number to limit results in the case of large values.</span></span> <span data-ttu-id="45406-114">지정한 수보다 많은 열은 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="45406-114">Columns greater than the number provided will be truncated.</span></span>  
  
 <span data-ttu-id="45406-115">**실행 제한 시간**</span><span class="sxs-lookup"><span data-stu-id="45406-115">**Execution time-out**</span></span>  
 <span data-ttu-id="45406-116">**새 연결** 대화 상자에서 기본값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="45406-116">Sets the default value in the **New Connection** dialog box.</span></span> <span data-ttu-id="45406-117">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서 쿼리를 취소하기 전에 대기할 시간을 초 단위로 지정하려면 이 스핀 상자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="45406-117">Use this spin box to tell [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] the number of seconds to wait before canceling the query.</span></span> <span data-ttu-id="45406-118">값 0은 무한 대기 또는 제한 시간 없음을 나타냅니다. 새 설치의 경우이 값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="45406-118">A value of 0 indicates an infinite wait, or no time-out. This value is 0 on a new installation.</span></span>  
  
 <span data-ttu-id="45406-119">**일괄 처리 구분 기호**</span><span class="sxs-lookup"><span data-stu-id="45406-119">**Batch separator**</span></span>  
 <span data-ttu-id="45406-120">[!INCLUDE[tsql](../includes/tsql-md.md)] 문을 일괄 처리로 구분하는 데 사용할 단어를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="45406-120">Type a word that you use to separate [!INCLUDE[tsql](../includes/tsql-md.md)] statements into batches.</span></span> <span data-ttu-id="45406-121">기본값은 GO입니다.</span><span class="sxs-lookup"><span data-stu-id="45406-121">The default is GO.</span></span>  
  
 <span data-ttu-id="45406-122">**기본적으로 SQLCMD 모드로 새 쿼리를 엽니다.**</span><span class="sxs-lookup"><span data-stu-id="45406-122">**By default, open new queries in SQLCMD Mode**</span></span>  
 <span data-ttu-id="45406-123">SQLCMD 모드로 새 쿼리를 열려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="45406-123">Select this check box to open new queries in SQLCMD mode.</span></span> <span data-ttu-id="45406-124">SQLCMD 모드에 대한 자세한 내용은 [쿼리 편집기로 SQLCMD 스크립트 편집](../relational-databases/scripting/edit-sqlcmd-scripts-with-query-editor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45406-124">For more information about SQLCMD mode, see [Edit SQLCMD Scripts with Query Editor](../relational-databases/scripting/edit-sqlcmd-scripts-with-query-editor.md).</span></span>  
  
 <span data-ttu-id="45406-125">이 옵션을 선택할 경우 다음과 같은 제한 사항에 유의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45406-125">When you select this option, be aware of the following limitations:</span></span>  
  
-   <span data-ttu-id="45406-126">[!INCLUDE[ssDE](../includes/ssde-md.md)] 쿼리 편집기에서 IntelliSense는 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45406-126">IntelliSense in the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor is turned off.</span></span>  
  
-   <span data-ttu-id="45406-127">쿼리 편집기를 명령줄에서 실행하지 못하므로 변수와 같은 명령줄 매개 변수를 전달할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="45406-127">Because Query Editor does not run from the command line, you cannot pass in command-line parameters such as variables.</span></span>  
  
-   <span data-ttu-id="45406-128">쿼리 편집기는 운영 체제 프롬프트에 응답할 수 없으므로 대화형 문을 실행하지 않도록 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45406-128">Because Query Editor cannot respond to operating-system prompts, you must be careful not to run interactive statements.</span></span>  
  
 <span data-ttu-id="45406-129">**기본값으로 다시 설정**</span><span class="sxs-lookup"><span data-stu-id="45406-129">**Reset to Default**</span></span>  
 <span data-ttu-id="45406-130">이 페이지의 모든 값을 원래 기본값으로 다시 설정하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45406-130">Click to reset all values on this page to the original default values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45406-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="45406-131">See Also</span></span>  
 [<span data-ttu-id="45406-132">sqlcmd 유틸리티</span><span class="sxs-lookup"><span data-stu-id="45406-132">sqlcmd Utility</span></span>](../tools/sqlcmd-utility.md)  
  
  
