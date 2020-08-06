---
title: 매개 변수 정보(IntelliSense)
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Parameter Info option [IntelliSense]
- stored function parameter completion [Intellisense]
- language references [SQL Server]
- IntelliSense [SQL Server], Parameter Info option
ms.assetid: 56c2aac9-c65c-4679-b62c-d9f689876dde
author: rothja
ms.author: jroth
ms.openlocfilehash: b7e5e7496753006808f75378182db0d3cb606d4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659925"
---
# <a name="parameter-info-intellisense"></a><span data-ttu-id="d3e26-102">매개 변수 정보(IntelliSense)</span><span class="sxs-lookup"><span data-stu-id="d3e26-102">Parameter Info (IntelliSense)</span></span>
  <span data-ttu-id="d3e26-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense **매개 변수 정보** 옵션은 함수나 저장 프로시저에 필요한 매개 변수의 개수, 이름 및 유형에 대한 정보를 제공하는 매개 변수 목록을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d3e26-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense **Parameter Info** option opens a parameters list that provides information about the number, names, and types of the parameters that are required by a function or stored procedure.</span></span> <span data-ttu-id="d3e26-104">굵게 표시된 매개 변수는 함수나 시스템 저장 프로시저를 입력할 때 필요한 다음 매개 변수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d3e26-104">The parameter in bold indicates the next parameter that is required as you type a function or stored procedure.</span></span>  
  
 <span data-ttu-id="d3e26-105">또한 중첩 함수에 대한 매개 변수 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3e26-105">The parameter list is also displayed for nested functions.</span></span> <span data-ttu-id="d3e26-106">함수를 다른 함수에 대한 매개 변수로 입력할 경우 내부 함수에 대한 매개 변수가 매개 변수 목록에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3e26-106">If you type a function as a parameter to another function, the parameter list displays the parameters for the inner function.</span></span> <span data-ttu-id="d3e26-107">그런 다음 내부 함수 매개 변수 목록이 완료되면 매개 변수 목록은 외부 함수 매개 변수를 표시하도록 원래대로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="d3e26-107">Then, when the inner function parameter list is complete, the parameter list reverts to displaying the outer function parameters.</span></span>  
  
#### <a name="to-view-parameter-info-for-functions-or-stored-procedures"></a><span data-ttu-id="d3e26-108">함수나 저장 프로시저에 대한 매개 변수 정보를 보려면</span><span class="sxs-lookup"><span data-stu-id="d3e26-108">To view Parameter Info for functions or stored procedures</span></span>  
  
1.  <span data-ttu-id="d3e26-109">함수 이름 뒤에 매개 변수 목록을 열기 위해 일반적으로 사용하는 여는 괄호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e26-109">After the name of a function, type an open parenthesis as you usually type to open the parameters list.</span></span> <span data-ttu-id="d3e26-110">저장 프로시저의 이름을 입력한 후 프로시저 매개 변수에 대한 정보를 가져오기 위해 일반적으로 사용하는 공백을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e26-110">After you type the name of a stored procedure, type a space as you usually type to obtain information about the procedure parameters.</span></span>  
  
     <span data-ttu-id="d3e26-111">IntelliSense는 삽입 지점 바로 아래의 팝업 창에서 함수의 전체 선언이나 저장 프로시저의 매개 변수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e26-111">IntelliSense displays the complete declaration for the function or the parameters for a stored procedure in a pop-up window just under the insertion point.</span></span> <span data-ttu-id="d3e26-112">목록의 첫 번째 매개 변수가 굵게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3e26-112">The first parameter in the list appears in bold.</span></span>  
  
2.  <span data-ttu-id="d3e26-113">매개 변수를 입력하면 입력해야 하는 다음 매개 변수를 나타내도록 굵게 표시가 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3e26-113">As you type the parameters, the bold font changes to reflect the next parameter that you need to enter.</span></span>  
  
3.  <span data-ttu-id="d3e26-114">아무 때나 Esc 키를 눌러 목록을 닫거나 함수를 완성할 때까지 계속 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e26-114">Press ESC at any time to close the list, or continue typing until you have completed the function.</span></span>  
  
     <span data-ttu-id="d3e26-115">함수의 경우 닫는 괄호를 입력하면 매개 변수 목록도 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="d3e26-115">For a function, if you type the closing parenthesis you also close the parameter list.</span></span>  
  
#### <a name="to-manually-start-parameter-info"></a><span data-ttu-id="d3e26-116">수동으로 매개 변수 정보를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="d3e26-116">To manually start Parameter Info</span></span>  
  
1.  <span data-ttu-id="d3e26-117">**편집** 메뉴에서 **IntelliSense** 를 선택한 다음 **매개 변수 정보**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e26-117">On the **Edit** menu, select **IntelliSense** and then select **Parameter Info**.</span></span>  
  
2.  <span data-ttu-id="d3e26-118">바로 가기 키 Ctrl+Shift+스페이스바를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="d3e26-118">Press the CTRL+SHIFT+SPACE keyboard shortcut.</span></span>  
  
 <span data-ttu-id="d3e26-119">자세한 내용은 [IntelliSense 구성&#40;SQL Server Management Studio&#41;](configure-intellisense-sql-server-management-studio.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d3e26-119">For more information, see [Configure IntelliSense &#40;SQL Server Management Studio&#41;](configure-intellisense-sql-server-management-studio.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3e26-120">**매개 변수 정보** 옵션은 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기와 XML 쿼리 편집기에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e26-120">The **Parameter Info** option is available only for the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor and the XML Query Editor.</span></span>  
  
  
