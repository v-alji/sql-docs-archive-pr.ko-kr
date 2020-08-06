---
title: 쿼리 옵션 실행 (일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.general.f1
ms.assetid: 858a0263-2f04-4692-b8bf-63e93c998ead
author: rothja
ms.author: jroth
ms.openlocfilehash: ce3848b51b81f111333ba0e9ac12c96432dd9863
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659635"
---
# <a name="query-options-execution-general-page"></a><span data-ttu-id="f18bb-102">쿼리 옵션 실행(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="f18bb-102">Query Options Execution (General Page)</span></span>
  <span data-ttu-id="f18bb-103">이 페이지를 사용하여 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 쿼리를 실행하는 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f18bb-103">Use this page to specify the options for running [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries.</span></span> <span data-ttu-id="f18bb-104">이 대화 상자에 액세스하려면 쿼리 편집기 창의 본문을 마우스 오른쪽 단추로 클릭한 다음 **쿼리 옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f18bb-104">To access this dialog box, right-click the body of a Query Editor window, and then click **Query Options**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="f18bb-105">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="f18bb-105">UI element list</span></span>  
 <span data-ttu-id="f18bb-106">**SET ROWCOUNT**</span><span class="sxs-lookup"><span data-stu-id="f18bb-106">**SET ROWCOUNT**</span></span>  
 <span data-ttu-id="f18bb-107">기본값 0은 모든 결과를 받을 때까지 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서 결과를 기다린다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f18bb-107">The default value of 0 indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will wait for results until all results are received.</span></span> <span data-ttu-id="f18bb-108">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서 지정한 행 수를 받은 후 쿼리를 중단하려면 0보다 큰 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f18bb-108">Provide a value greater than 0 if you want [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to halt the query after obtaining the specified number of rows.</span></span> <span data-ttu-id="f18bb-109">모든 행이 반환될 수 있도록 이 옵션을 해제하려면 SET ROWCOUNT 0을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f18bb-109">To turn this option off (so that all rows are returned), specify SET ROWCOUNT 0.</span></span>  
  
 <span data-ttu-id="f18bb-110">**SET TEXTSIZE**</span><span class="sxs-lookup"><span data-stu-id="f18bb-110">**SET TEXTSIZE**</span></span>  
 <span data-ttu-id="f18bb-111">기본값 2,147,483,647바이트는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 `text`, `ntext`, `nvarchar(max)` 및 `varchar(max)` 데이터 필드의 제한까지 전체 데이터 필드를 제공한다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f18bb-111">The default value of 2,147,483,647 bytes indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will provide a complete data field up to the limit of `text`, `ntext`, `nvarchar(max)`, and `varchar(max)` data fields.</span></span> <span data-ttu-id="f18bb-112">XML 데이터 형식에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f18bb-112">It does not affect the XML data type.</span></span> <span data-ttu-id="f18bb-113">값이 클 경우 결과를 제한하려면 보다 작은 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f18bb-113">Provide a smaller number to limit results in the case of large values.</span></span> <span data-ttu-id="f18bb-114">지정한 수보다 많은 열은 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="f18bb-114">Columns greater than the number provided will be truncated.</span></span>  
  
 <span data-ttu-id="f18bb-115">**실행 제한 시간**</span><span class="sxs-lookup"><span data-stu-id="f18bb-115">**Execution time-out**</span></span>  
 <span data-ttu-id="f18bb-116">쿼리를 취소할 때까지 기다리는 시간(초)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f18bb-116">Indicates the number of seconds to wait before canceling the query.</span></span> <span data-ttu-id="f18bb-117">값 0은 무한 대기 또는 제한 시간 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="f18bb-117">A value of 0 indicates an infinite wait, or no time-out.</span></span>  
  
 <span data-ttu-id="f18bb-118">**일괄 처리 구분 기호**</span><span class="sxs-lookup"><span data-stu-id="f18bb-118">**Batch separator**</span></span>  
 <span data-ttu-id="f18bb-119">Transact-SQL 문을 일괄 처리로 구분하는 데 사용할 단어를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f18bb-119">Type a word that you use to separate Transact-SQL statements into batches.</span></span> <span data-ttu-id="f18bb-120">기본값은 GO입니다.</span><span class="sxs-lookup"><span data-stu-id="f18bb-120">The default is GO.</span></span>  
  
 <span data-ttu-id="f18bb-121">**기본적으로 SQLCMD 모드로 새 쿼리를 엽니다.**</span><span class="sxs-lookup"><span data-stu-id="f18bb-121">**By default, open new queries in SQLCMD Mode**</span></span>  
 <span data-ttu-id="f18bb-122">SQLCMD 모드로 새 쿼리를 열려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f18bb-122">Select this check box to open new queries in SQLCMD mode.</span></span> <span data-ttu-id="f18bb-123">이 확인란은 **도구** 메뉴를 통해 대화 상자를 연 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f18bb-123">This check box is visible only when the dialog box is opened through the **Tools** menu.</span></span>  
  
 <span data-ttu-id="f18bb-124">이 옵션을 선택할 경우 다음과 같은 제한 사항에 유의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f18bb-124">When you select this option, be aware of the following limitations:</span></span>  
  
-   <span data-ttu-id="f18bb-125">[!INCLUDE[ssDE](../includes/ssde-md.md)] 쿼리 편집기에서 IntelliSense는 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f18bb-125">IntelliSense in the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor is turned off.</span></span>  
  
-   <span data-ttu-id="f18bb-126">쿼리 편집기를 명령줄에서 실행하지 못하므로 변수와 같은 명령줄 매개 변수를 전달할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f18bb-126">Because Query Editor does not run from the command line, you cannot pass in command-line parameters such as variables.</span></span>  
  
-   <span data-ttu-id="f18bb-127">쿼리 편집기는 운영 체제 프롬프트에 응답할 수 없으므로 대화형 문을 실행하지 않도록 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f18bb-127">Because Query Editor cannot respond to operating-system prompts, you must be careful not to run interactive statements.</span></span>  
  
 <span data-ttu-id="f18bb-128">**기본값으로 다시 설정**</span><span class="sxs-lookup"><span data-stu-id="f18bb-128">**Reset to Default**</span></span>  
 <span data-ttu-id="f18bb-129">이 페이지의 모든 값을 원래 기본값으로 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f18bb-129">Resets all values on this page to the original default values.</span></span>  
  
  
