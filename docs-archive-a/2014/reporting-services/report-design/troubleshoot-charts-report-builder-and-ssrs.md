---
title: 차트 문제 해결(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 3a327ffa-3b69-40d6-8015-cc01cfae9161
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b931b50545ba2b8d7c4c06cc5c48d6415a05470a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733607"
---
# <a name="troubleshoot-charts-report-builder-and-ssrs"></a><span data-ttu-id="eeefa-102">차트 문제 해결(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="eeefa-102">Troubleshoot Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="eeefa-103">다음은 차트로 작업할 때 도움이 되는 문제 관련 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="eeefa-103">These issues can be helpful when working with charts.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="why-does-my-chart-count-not-sum-the-values-on-the-value-axis"></a><span data-ttu-id="eeefa-104">차트에서 값 축에 있는 값의 합이 표시되어야 하는데 개수가 표시되는 이유</span><span class="sxs-lookup"><span data-stu-id="eeefa-104">Why does my chart count, not sum, the values on the value axis?</span></span>  
 <span data-ttu-id="eeefa-105">대부분의 차트 종류는 일반적으로 y축인 값 축에 숫자 값이 있어야 올바르게 그려집니다.</span><span class="sxs-lookup"><span data-stu-id="eeefa-105">Most chart types require numeric values along the value axis, which is typically the y-axis, in order to draw correctly.</span></span> <span data-ttu-id="eeefa-106">값 필드의 데이터 형식이 `String`이면 필드에 숫자가 있더라도 차트에서 숫자 값을 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eeefa-106">If the data type of your value field is `String`, the chart cannot display a numeric value, even if there are numerals in the fields.</span></span> <span data-ttu-id="eeefa-107">대신 차트는 해당 필드에 값이 포함되어 있는 행의 총 개수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="eeefa-107">Instead, the chart displays a count of the total number of rows that contain a value in that field.</span></span> <span data-ttu-id="eeefa-108">이러한 현상을 방지하려면 값 계열에 사용하는 필드에 형식이 지정된 문자가 포함된 문자열이 아니라 숫자 데이터 형식이 포함되도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eeefa-108">To avoid this behavior, make sure that the fields that you use for value series have numeric data types, as opposed to strings that contain formatted numbers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeefa-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eeefa-109">See Also</span></span>  
 [<span data-ttu-id="eeefa-110">차트&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="eeefa-110">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
