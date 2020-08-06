---
title: 표준 구문 분석 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- standard parse [Integration Services]
- locales [Integration Services]
ms.assetid: dfe835b1-ea52-4e18-a23a-5188c5b6f013
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7cacff710870d372d6bbf8345e05397857c13a00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734307"
---
# <a name="standard-parse"></a><span data-ttu-id="69a4d-102">Standard Parse</span><span class="sxs-lookup"><span data-stu-id="69a4d-102">Standard Parse</span></span>
  <span data-ttu-id="69a4d-103">표준 구문 분석은 로캘 기반의 구문 분석 루틴이며 Oleaut32.dll 및 Ole2dsip.dll에서 사용할 수 있는 Automation 데이터 형식 변환 API에 제공되는 모든 데이터 형식 변환을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="69a4d-103">Standard parse is a locale-sensitive set of parsing routines that support all the data type conversions provided by the Automation data type conversion APIs that are available in Oleaut32.dll and Ole2dsip.dll.</span></span> <span data-ttu-id="69a4d-104">표준 구문 분석은 API를 구문 분석하는 OLE DB와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="69a4d-104">Standard parse is equivalent to the OLE DB parsing APIs.</span></span>  
  
 <span data-ttu-id="69a4d-105">표준 구문 분석은 국가별 데이터에 대한 데이터 형식 변환을 지원하며 데이터 형식이 빠른 구문 분석에서 지원되지 않는 경우에만 사용되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a4d-105">Standard parse provides support for data type conversion of international data, and it should be used if the data format is not supported by Fast parse.</span></span> <span data-ttu-id="69a4d-106">Automation 데이터 형식 변환 API에 대한 자세한 내용은 [MSDN Library(](https://go.microsoft.com/fwlink/?LinkId=79427))의 "데이터 형식 변환 API(Data Type Conversion APIs)"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="69a4d-106">For more information about the Automation data type conversion API, see "Data Type Conversion APIs" in the [MSDN Library](https://go.microsoft.com/fwlink/?LinkId=79427).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69a4d-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="69a4d-107">See Also</span></span>  
 [<span data-ttu-id="69a4d-108">Fast Parse</span><span class="sxs-lookup"><span data-stu-id="69a4d-108">Fast Parse</span></span>](../../2014/integration-services/fast-parse.md)  
  
  
