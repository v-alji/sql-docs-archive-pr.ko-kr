---
title: SQL Server Data Tools |에서 MDX 스크립트를 만들고 실행 합니다. Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], scripts
- scripts [Analysis Services], creating
- scripts [MDX], creating
ms.assetid: aa54b8cc-ff3b-4ef6-a64e-11b9e9d7fa11
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0c1088bd9920364d46117624673f27f09cf38b34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646694"
---
# <a name="create-and-run-an-mdx-script-in-sql-server-data-tools"></a><span data-ttu-id="06e3b-102">SQL Server Data Tools에서 MDX 스크립트 만들기 및 실행</span><span class="sxs-lookup"><span data-stu-id="06e3b-102">Create and Run an MDX Script in SQL Server Data Tools</span></span>
  <span data-ttu-id="06e3b-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 MDX 스크립트를 만들고 실행하려면 큐브를 미리 만들고 편집할 준비가 된 상태로 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06e3b-103">To create and run an MDX Script in  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you need to be in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] with a cube already created and ready for editing.</span></span>  
  
### <a name="to-create-a-multidimensional-expressions-mdx-script"></a><span data-ttu-id="06e3b-104">MDX(Multidimensional Expressions) 스크립트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="06e3b-104">To create a Multidimensional Expressions (MDX) script</span></span>  
  
1.  <span data-ttu-id="06e3b-105">MDX 스크립트를 만들 큐브를 열고 **보기**에서 **계산**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="06e3b-105">Open the cube for which you want to create an MDX script, and under **View**, click **Calculations**.</span></span>  
  
2.  <span data-ttu-id="06e3b-106">**스크립트 보기** 모드가 아닌 경우 **스크립트 보기** 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="06e3b-106">If you are not in **Script View** mode, click the **Script View** icon.</span></span>  
  
3.  <span data-ttu-id="06e3b-107">스크립트 창의 CALCULATE 명령 아래에 MDX 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="06e3b-107">In the script window, under the CALCULATE command, type an MDX expression.</span></span> <span data-ttu-id="06e3b-108">**구문 검사** 아이콘을 클릭하고 식이 구문상 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="06e3b-108">Click the **Check Syntax** icon and verify that the expression is syntactically correct.</span></span>  
  
4.  <span data-ttu-id="06e3b-109">MDX 스크립트를 실행하려면 새 MDX 스크립트 변경 내용이 포함된 큐브를 배포하고 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="06e3b-109">To run the MDX script, deploy and process the cube with the new MDX script changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06e3b-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="06e3b-110">See Also</span></span>  
 <span data-ttu-id="06e3b-111">[MDX &#40;기본 MDX 스크립트&#41;](mdx/the-basic-mdx-script-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="06e3b-111">[The Basic MDX Script &#40;MDX&#41;](mdx/the-basic-mdx-script-mdx.md) </span></span>  
 <span data-ttu-id="06e3b-112">[MDX 스크립팅 기본 사항 &#40;Analysis Services&#41;](mdx/mdx-scripting-fundamentals-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="06e3b-112">[MDX Scripting Fundamentals &#40;Analysis Services&#41;](mdx/mdx-scripting-fundamentals-analysis-services.md) </span></span>  
 [<span data-ttu-id="06e3b-113">MDX 스크립팅 문&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="06e3b-113">MDX Scripting Statements &#40;MDX&#41;</span></span>](/sql/mdx/mdx-scripting-statements-mdx)  
  
  
