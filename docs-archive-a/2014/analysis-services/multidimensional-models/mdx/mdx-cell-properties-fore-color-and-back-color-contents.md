---
title: FORE_COLOR 및 BACK_COLOR 내용 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- FORE_COLOR contents
- backgrounds [MDX]
- cells [MDX]
- colors [MDX]
- storing cell color information
- cell backgrounds
- BACK_COLOR contents
ms.assetid: ff8f40cb-2ac4-4fc2-9761-7f1b14c17c8c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 748754ec3c90bb44392d7acb7de8f815be24086e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737042"
---
# <a name="fore_color-and-back_color-contents-mdx"></a><span data-ttu-id="d9eaa-102">FORE_COLOR 및 BACK_COLOR 내용(MDX)</span><span class="sxs-lookup"><span data-stu-id="d9eaa-102">FORE_COLOR and BACK_COLOR Contents (MDX)</span></span>
  <span data-ttu-id="d9eaa-103">`FORE_COLOR` 및 `BACK_COLOR` 셀 속성은 셀의 텍스트 및 배경의 색 정보를 Microsoft Windows 운영 체제의 빨간색-녹색-파란색(RGB) 형식으로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d9eaa-103">The `FORE_COLOR` and `BACK_COLOR` cell properties store color information for the text and the background of a cell, respectively, in the Microsoft Windows operating system red-green-blue (RGB) format.</span></span>  
  
 <span data-ttu-id="d9eaa-104">일반적인 RGB 색의 유효 범위는 0부터 16,777,215(&H00FFFFFF)까지입니다.</span><span class="sxs-lookup"><span data-stu-id="d9eaa-104">The valid range for an ordinary RGB color is zero (0) to 16,777,215 (&H00FFFFFF).</span></span> <span data-ttu-id="d9eaa-105">이 범위에 속하는 숫자의 상위 바이트는 항상 0이며 최하위부터 최상위에 이르는 하위 3바이트가 빨간색, 녹색, 파란색의 양을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="d9eaa-105">The high byte of a number in this range always equals 0; the lower 3 bytes, from least to most significant byte, determine the amount of red, green, and blue, respectively.</span></span> <span data-ttu-id="d9eaa-106">빨간색, 녹색, 파란색 구성 요소는 각각 0부터 255(&HFF) 사이의 숫자로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9eaa-106">The red, green, and blue components are each represented by a number between 0 and 255 (&HFF).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9eaa-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d9eaa-107">See Also</span></span>  
 [<span data-ttu-id="d9eaa-108">셀 속성 사용&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="d9eaa-108">Using Cell Properties &#40;MDX&#41;</span></span>](mdx-cell-properties-using-cell-properties.md)  
  
  
