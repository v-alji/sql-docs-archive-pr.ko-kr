---
title: 변경 스크립트 저장 대화 상자(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.generatechangescript
- vdtsql.chm:65544
ms.assetid: fc9d1639-5efa-44fe-a04f-4d4d0def2833
author: stevestein
ms.author: sstein
ms.openlocfilehash: 19a2bb2ce9a219c195421e2efa203fc115e1ae1b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727724"
---
# <a name="save-change-script-dialog-box-visual-database-tools"></a><span data-ttu-id="1c187-102">변경 스크립트 저장 대화 상자(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="1c187-102">Save Change Script Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="1c187-103">이 대화 상자에는 테이블을 마지막으로 저장한 후에 변경한 내용에 대한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c187-103">This dialog box shows the [!INCLUDE[tsql](../../includes/tsql-md.md)] script for the changes you have made since you last saved the table.</span></span> <span data-ttu-id="1c187-104">이 대화 상자를 사용하여 선택한 위치에 텍스트 파일로 스크립트를 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c187-104">It also allows you to save the script to a text file at a location you choose.</span></span>  
  
 <span data-ttu-id="1c187-105">테이블 디자이너에서 테이블에 대해 변경한 내용을 저장하지 않은 상태에서 이 대화 상자에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c187-105">You can access this dialog box after you have made unsaved changes to a table in Table Designer.</span></span> <span data-ttu-id="1c187-106">**테이블 디자이너** 메뉴에서 **변경 스크립트 생성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1c187-106">On the **Table Designer** menu, click **Generate Change Script**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1c187-107">Visual Database Tools에서 제공된 변경 스크립트에는 오류 처리가 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1c187-107">Change scripts provided by Visual Database Tools contain no error handling.</span></span> <span data-ttu-id="1c187-108">변경 스크립트는 툴이 열린 후에 데이터베이스 개체가 변경되지 않았으므로 변경 관련 문제가 발생하지 않는다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="1c187-108">They assume that database objects have not changed since the tool was opened, and that change-related problems will therefore not occur.</span></span> <span data-ttu-id="1c187-109">변경 스크립트를 실행하기 전에 적절한 오류 처리 문을 포함시켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c187-109">Before running a change script, you should include the appropriate error-handling statements.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1c187-110">옵션</span><span class="sxs-lookup"><span data-stu-id="1c187-110">Options</span></span>  
 <span data-ttu-id="1c187-111">**저장할 때마다 자동으로 변경 스크립트 만들기**</span><span class="sxs-lookup"><span data-stu-id="1c187-111">**Automatically generate change script on every save**</span></span>  
 <span data-ttu-id="1c187-112">이 옵션을 선택하면 테이블에 변경 내용을 저장할 때마다 **변경 스크립트 저장** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1c187-112">If checked, the **Save Change Script** dialog box will appear any time you save changes to a table.</span></span>  
  
 <span data-ttu-id="1c187-113">**예**</span><span class="sxs-lookup"><span data-stu-id="1c187-113">**Yes**</span></span>  
 <span data-ttu-id="1c187-114">텍스트 파일의 위치를 선택할 수 있는 **저장** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1c187-114">Bring up the **Save** dialog box where you can choose the location for the text file.</span></span>  
  
 <span data-ttu-id="1c187-115">**아니요**</span><span class="sxs-lookup"><span data-stu-id="1c187-115">**No**</span></span>  
 <span data-ttu-id="1c187-116">변경 스크립트 작성을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="1c187-116">Cancel the creation of the change script.</span></span>  
  
  
