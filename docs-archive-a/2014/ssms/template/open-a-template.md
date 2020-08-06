---
title: 템플릿 열기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- templates [Transact-SQL], opening
- opening templates
ms.assetid: 605b0f4c-5ba1-4249-ad1c-6341df77cd7a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 43b75d68fafea759e4d7873c1fb738d7964dcf57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652511"
---
# <a name="open-a-template"></a><span data-ttu-id="1f69d-102">템플릿 열기</span><span class="sxs-lookup"><span data-stu-id="1f69d-102">Open a Template</span></span>
  <span data-ttu-id="1f69d-103">템플릿 탐색기에서 템플릿을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f69d-103">You can open a template from Template Explorer.</span></span>  
  
## <a name="to-open-a-template-from-template-explorer"></a><span data-ttu-id="1f69d-104">템플릿 탐색기에서 템플릿을 열려면</span><span class="sxs-lookup"><span data-stu-id="1f69d-104">To open a template from Template Explorer</span></span>  
 <span data-ttu-id="1f69d-105">템플릿 탐색기에서 템플릿을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f69d-105">You can open templates from the Template Explorer.</span></span>  
  
1.  <span data-ttu-id="1f69d-106">템플릿 탐색기를 열려면 **보기** 메뉴에서 **템플릿 탐색기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f69d-106">To open Template Explorer, on the **View** menu, click **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="1f69d-107">템플릿 범주 목록에서 열려는 템플릿이 포함된 범주를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1f69d-107">In the list of template categories, expand the category that contains the template you want to open.</span></span>  
  
3.  <span data-ttu-id="1f69d-108">다음 세 가지 방법으로 템플릿을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1f69d-108">There are three ways to open the template:</span></span>  
  
    1.  <span data-ttu-id="1f69d-109">코드 편집기 창에서 열려는 템플릿을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f69d-109">Double-click the template to open it in a code editor window.</span></span>  
  
    2.  <span data-ttu-id="1f69d-110">템플릿을 마우스 오른쪽 단추로 클릭하고 **열기** 를 선택하여 코드 편집기 창에서 템플릿을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1f69d-110">Right-click the template and select **Open** to open it in a code editor window.</span></span>  
  
    3.  <span data-ttu-id="1f69d-111">템플릿을 코드 편집기 창으로 끌어 편집기 창의 내용에 템플릿 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="1f69d-111">Drag the template into a code editor window to add the template code to the contents of the editor window.</span></span>  
  
 <span data-ttu-id="1f69d-112">템플릿을 연 후 **템플릿 매개 변수 바꾸기** 대화 상자에서 템플릿 매개 변수를 원하는 값으로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f69d-112">After the template is open, use the **Replace Template Parameters** dialog box to replace the template parameters with your values.</span></span>  
  
 <span data-ttu-id="1f69d-113">새 편집기 창에서 템플릿을 열 경우 현재 활성 연결의 자격 증명을 사용하여 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="1f69d-113">If opening a template launches a new editor window, the window will open with the credentials of the current active connection.</span></span> <span data-ttu-id="1f69d-114">예를 들어 개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 포커스가 있는 상태에서 CREATE DATABASE 템플릿을 열면 새 편집기 창은 해당 인스턴스에 대한 연결을 사용하여 열립니다.</span><span class="sxs-lookup"><span data-stu-id="1f69d-114">For example, if you are focused on an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] in Object Explorer when you open the CREATE DATABASE template, a new editor window will be opened using a connection to that instance.</span></span> <span data-ttu-id="1f69d-115">활성 연결이 없는 경우에는 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 에서 로그인 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f69d-115">If there is no active connection, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] will present a login dialog.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f69d-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1f69d-116">See Also</span></span>  
 <span data-ttu-id="1f69d-117">[템플릿 탐색기](template-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="1f69d-117">[Template Explorer](template-explorer.md) </span></span>  
 [<span data-ttu-id="1f69d-118">템플릿 매개 변수 바꾸기</span><span class="sxs-lookup"><span data-stu-id="1f69d-118">Replace Template Parameters</span></span>](replace-template-parameters.md)  
  
  
