---
title: 문자열 패딩(SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- padding strings [Integration Services]
- expressions [Integration Services], string padding
- string padding
ms.assetid: d3fed73d-e0d4-4c67-9355-fb7083a72dd6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3985fd1b2f29260e2313a761797d2528f5d0e328
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732784"
---
# <a name="string-padding-ssis"></a><span data-ttu-id="173c1-102">문자열 패딩(SSIS)</span><span class="sxs-lookup"><span data-stu-id="173c1-102">String Padding (SSIS)</span></span>
  <span data-ttu-id="173c1-103">식 계산기는 문자열에 선행 및 후행 공백이 포함되어 있는지 확인하지 않으며 문자열을 비교하기 전에 동일한 길이가 되도록 패딩하지도 않습니다.</span><span class="sxs-lookup"><span data-stu-id="173c1-103">The expression evaluator does not check if a string contains leading and trailing spaces, and it does not pad strings to make them the same length before it compares them.</span></span> <span data-ttu-id="173c1-104">식에 문자열 패딩이 필요하면 + 연산자를 사용하여 열 값과 빈 문자열을 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="173c1-104">If expressions requires string padding, you can use the + operator to concatenate column values and blank strings.</span></span> <span data-ttu-id="173c1-105">자세한 내용은 [+&#40;연결&#41;&#40;SSIS 식&#41;](concatenate-ssis-expression.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="173c1-105">For more information, see [+ &#40;Concatenate&#41; &#40;SSIS Expression&#41;](concatenate-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="173c1-106">반면 공백을 제거하려는 경우 식 계산기는 선행 또는 후행 공백이나 둘 다를 제거하는 LTRIM, RTRIM 및 TRIM 함수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="173c1-106">On the other hand, if you want to remove spaces, the expression evaluator provides the LTRIM, RTRIM, and TRIM functions, which remove leading or trailing spaces, or both.</span></span> <span data-ttu-id="173c1-107">자세한 내용은 [LTRIM&#40;SSIS 식&#41;](trim-ssis-expression.md), [RTRIM&#40;SSIS 식&#41;](rtrim-ssis-expression.md) 및 [TRIM&#40;SSIS 식&#41;](trim-ssis-expression.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="173c1-107">For more information, see [LTRIM &#40;SSIS Expression&#41;](trim-ssis-expression.md), [RTRIM &#40;SSIS Expression&#41;](rtrim-ssis-expression.md), and [TRIM &#40;SSIS Expression&#41;](trim-ssis-expression.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="173c1-108">LEN 함수는 선행 및 후행 공백을 개수에 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="173c1-108">The LEN function includes leading and trailing blanks in its count.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="173c1-109">관련 내용</span><span class="sxs-lookup"><span data-stu-id="173c1-109">Related Content</span></span>  
 <span data-ttu-id="173c1-110">pragmaticworks.com의 기술 문서 - [SSIS 식 치트 시트](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet
)</span><span class="sxs-lookup"><span data-stu-id="173c1-110">Technical article, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet
), on pragmaticworks.com</span></span>  
  
  
