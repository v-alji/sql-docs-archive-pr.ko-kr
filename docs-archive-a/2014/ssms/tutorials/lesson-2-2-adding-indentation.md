---
title: 들여쓰기 추가 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 9dce05c1-c52f-455d-8b8d-6f303e242760
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2d0b7ee8819f98df5e5658321a3d950ca31083b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652500"
---
# <a name="adding-indentation"></a><span data-ttu-id="159f2-102">들여쓰기 추가</span><span class="sxs-lookup"><span data-stu-id="159f2-102">Adding Indentation</span></span>
  <span data-ttu-id="159f2-103">쿼리 편집기를 사용하여 한 단계로 여러 코드 섹션을 들여쓸 수 있으며 들여쓰기 크기도 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="159f2-103">Query Editor allows you to indent large sections of code with a single step, and you can change the amount of the indentation.</span></span>  
  
## <a name="indenting-code"></a><span data-ttu-id="159f2-104">코드 들여쓰기</span><span class="sxs-lookup"><span data-stu-id="159f2-104">Indenting Code</span></span>  
  
#### <a name="to-indent-multiple-lines-of-code"></a><span data-ttu-id="159f2-105">여러 줄의 코드를 들여쓰려면</span><span class="sxs-lookup"><span data-stu-id="159f2-105">To indent multiple lines of code</span></span>  
  
1.  <span data-ttu-id="159f2-106">도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="159f2-106">On the toolbar, click **New Query**.</span></span>  
  
2.  <span data-ttu-id="159f2-107">**Person**스키마의 **Person**테이블에서 **BusinessEntityID** , FirstName, **MiddleName** 및 **LastName** 열을 선택하는 두 번째 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="159f2-107">Create a second query that selects the **BusinessEntityID**, FirstName, **MiddleName**, and **LastName** columns from the **Person** table of the **Person** schema.</span></span> <span data-ttu-id="159f2-108">코드가 다음과 같이 되도록 각 열을 별도의 줄에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="159f2-108">Place each column on a separate line so the code looks like this:</span></span>  
  
    ```  
    -- Search for a contact  
    SELECT   
    BusinessEntityID,  
    FirstName,   
    MiddleName,   
    LastName  
    FROM Person.Person  
    WHERE LastName = 'Sanchez';  
    GO  
    ```  
  
3.  <span data-ttu-id="159f2-109">`BusinessEntityID` 에서 `LastName`에 이르는 모든 텍스트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="159f2-109">Select all text from `BusinessEntityID` to `LastName`.</span></span>  
  
4.  <span data-ttu-id="159f2-110">**SQL 편집기** 도구 모음에서 **들여쓰기** 를 클릭하여 한 번에 모든 줄을 들여씁니다.</span><span class="sxs-lookup"><span data-stu-id="159f2-110">On the **SQL Editor** toolbar, click **Increase Indent** to indent all the lines at once.</span></span>  
  
#### <a name="to-change-the-default-indentation"></a><span data-ttu-id="159f2-111">기본 들여쓰기를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="159f2-111">To change the default indentation</span></span>  
  
1.  <span data-ttu-id="159f2-112">**도구** 메뉴에서 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="159f2-112">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="159f2-113">**텍스트 편집기**, **모든 언어**를 차례로 확장하고 **탭** 을 클릭한 다음 들여쓰기 값을 적절히 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="159f2-113">Expand **Text Editor**, expand **All Languages**, and click **Tabs** , and set indentation values as appropriate.</span></span> <span data-ttu-id="159f2-114">들여쓰기 크기뿐 아니라 탭 크기와 탭이 공백으로 변환되는지 여부도 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="159f2-114">Note that you can change the size of the indent as well as the size of tabs, and whether tabs are converted to spaces.</span></span>  
  
     <span data-ttu-id="159f2-115">![탭 대화 상자의 모양](media/tabsdialog.gif "탭 대화 상자의 모양")</span><span class="sxs-lookup"><span data-stu-id="159f2-115">![Appearance of the Tabs dialog box](media/tabsdialog.gif "Appearance of the Tabs dialog box")</span></span>  
  
3.  <span data-ttu-id="159f2-116">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="159f2-116">Click **OK**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="159f2-117">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="159f2-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="159f2-118">쿼리 편집기 화면 크기</span><span class="sxs-lookup"><span data-stu-id="159f2-118">Maximizing Query Editor</span></span>](lesson-2-3-maximizing-query-editor.md)  
  
  
