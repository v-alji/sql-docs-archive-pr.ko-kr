---
title: For 루프 컨테이너 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], For Loop
- For Loop containers
ms.assetid: b9cd7ea7-b198-4a35-8b16-6acf09611ca5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9cb33ea5b7f3f59baad3c94f6bc845c281613ec9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647166"
---
# <a name="configure-a-for-loop-container"></a><span data-ttu-id="640be-102">For 루프 컨테이너 구성</span><span class="sxs-lookup"><span data-stu-id="640be-102">Configure a For Loop Container</span></span>
  <span data-ttu-id="640be-103">이 절차에서는 **For 루프 편집기** 대화 상자를 사용하여 For 루프 컨테이너를 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="640be-103">This procedure describes how to configure a For Loop container by using the **For Loop Editor** dialog box.</span></span>  
  
### <a name="to-configure-the-for-loop-container"></a><span data-ttu-id="640be-104">For 루프 컨테이너를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="640be-104">To configure the For Loop container</span></span>  
  
1.  <span data-ttu-id="640be-105">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 For 루프 컨테이너를 두 번 클릭하여 **For 루프 편집기**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="640be-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], double-click the For Loop container to open the **For Loop Editor**.</span></span>  
  
2.  <span data-ttu-id="640be-106">선택적으로 For 루프 컨테이너의 이름과 설명을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="640be-106">Optionally, modify the name and description of the For Loop container.</span></span>  
  
3.  <span data-ttu-id="640be-107">선택적으로 **InitExpression** 입력란에 초기화 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="640be-107">Optionally, type an initialization expression in the **InitExpression** text box.</span></span>  
  
4.  <span data-ttu-id="640be-108">**EvalExpression** 입력란에 계산 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="640be-108">Type an evaluation expression in the **EvalExpression** text box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="640be-109">식은 부울로 계산되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="640be-109">The expression must evaluate to a Boolean.</span></span> <span data-ttu-id="640be-110">식 결과가 `false`이면 루프 실행이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="640be-110">When the expression evaluates to `false`, the loop stops running.</span></span>  
  
5.  <span data-ttu-id="640be-111">선택적으로 **AssignExpression** 입력란에 대입 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="640be-111">Optionally, type an assignment expression in the **AssignExpression** text box.</span></span>  
  
6.  <span data-ttu-id="640be-112">선택적으로 **식** 페이지에서 **Expressions** 를 클릭하고 For 루프 컨테이너의 속성에 대한 속성 식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="640be-112">Optionally, click **Expressions** and, on the **Expressions** page, create property expressions for the properties of the For Loop container.</span></span> <span data-ttu-id="640be-113">자세한 내용은 [속성 식 추가 또는 변경](expressions/add-or-change-a-property-expression.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="640be-113">For more information, see [Add or Change a Property Expression](expressions/add-or-change-a-property-expression.md).</span></span>  
  
7.  <span data-ttu-id="640be-114">**확인** 을 클릭하여 **For 루프 편집기**를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="640be-114">Click **OK** to close the **For Loop Editor**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="640be-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="640be-115">See Also</span></span>  
 <span data-ttu-id="640be-116">[For 루프 컨테이너](control-flow/for-loop-container.md) </span><span class="sxs-lookup"><span data-stu-id="640be-116">[For Loop Container](control-flow/for-loop-container.md) </span></span>  
 <span data-ttu-id="640be-117">[Integration Services &#40;SSIS&#41; 식](expressions/integration-services-ssis-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="640be-117">[Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md) </span></span>  
 [<span data-ttu-id="640be-118">패키지에서 속성 식 사용</span><span class="sxs-lookup"><span data-stu-id="640be-118">Use Property Expressions in Packages</span></span>](expressions/use-property-expressions-in-packages.md)  
  
  
