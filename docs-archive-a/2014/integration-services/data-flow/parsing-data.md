---
title: 데이터 구문 분석 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- parsing [Integration Services]
- data parsing [Integration Services]
ms.assetid: 8893ea9d-634c-4309-b52c-6337222dcb39
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3bd34cd83351e31313ae96ff5709ec999a60f2f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648473"
---
# <a name="parsing-data"></a><span data-ttu-id="8c099-102">데이터 구문 분석</span><span class="sxs-lookup"><span data-stu-id="8c099-102">Parsing Data</span></span>
  <span data-ttu-id="8c099-103">패키지의 데이터 흐름에서는 다양한 표준 및 사용자 지정 데이터 형식이 사용될 수 있는 다른 유형의 데이터 저장소 간의 데이터가 추출 및 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c099-103">Data flows in packages extract and load data between heterogeneous data stores, which may use a variety of standard and custom data types.</span></span> <span data-ttu-id="8c099-104">데이터 흐름에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 원본은 데이터를 추출하고, 문자열 데이터를 구문 분석하고, 데이터를 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 데이터 형식으로 변환하는 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8c099-104">In a data flow, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sources do the work of extracting data, parsing string data, and converting data to an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type.</span></span> <span data-ttu-id="8c099-105">이후의 변환에서는 데이터를 다른 데이터 형식으로 변환하기 위해 데이터를 구문 분석하거나 다른 데이터 형식이 포함된 열 복사본을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c099-105">Subsequent transformations may parse data to convert it to a different data type, or create column copies with different data types.</span></span> <span data-ttu-id="8c099-106">구성 요소에 사용된 식에서는 인수와 피연산자를 다른 데이터 형식으로 캐스팅할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c099-106">Expressions used in components may also cast arguments and operands to different data types.</span></span> <span data-ttu-id="8c099-107">마지막으로, 데이터가 데이터 저장소에 로드될 때 대상에서는 대상에 사용되는 데이터 형식으로 데이터를 변환하기 위해 데이터를 구문 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c099-107">Finally, when the data is loaded into a data store, the destination may parse the data to convert it to a data type that the destination uses.</span></span> <span data-ttu-id="8c099-108">자세한 내용은 [Integration Services Data Types](integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c099-108">For more information, see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
## <a name="types-of-parsing"></a><span data-ttu-id="8c099-109">구문 분석 유형</span><span class="sxs-lookup"><span data-stu-id="8c099-109">Types of Parsing</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="8c099-110">에서는 데이터 변환을 위해 빠른 구문 분석과 표준 구문 분석이라는 두 가지 유형의 구문 분석을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8c099-110">provides two types of parsing for converting data: Fast parse and Standard parse.</span></span>  
  
-   <span data-ttu-id="8c099-111">빠른 구문 분석은 신속하고 간단한 구문 분석 루틴이지만 로캘 특정 데이터 형식 변환을 지원하지 않으며 가장 자주 사용되는 날짜 및 시간 형식만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8c099-111">Fast parse is a fast, simple set of parsing routines that does not support locale-specific data type conversions, and supports only the most frequently used date and time formats.</span></span> <span data-ttu-id="8c099-112">자세한 내용은 [Fast Parse](../fast-parse.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c099-112">For more information, see [Fast Parse](../fast-parse.md).</span></span>  
  
-   <span data-ttu-id="8c099-113">표준 구문 분석은 다양한 기능이 포함된 구문 분석 루틴이며 Oleaut32.dll 및 Ole2dsip.dll에서 사용할 수 있는 자동 데이터 형식 변환 API에 제공되는 모든 데이터 형식 변환을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8c099-113">Standard parse is a rich set of parsing routines that supports all the data type conversions that are provided by the Automation data type conversion APIs available in Oleaut32.dll and Ole2dsip.dll.</span></span> <span data-ttu-id="8c099-114">자세한 내용은 [Standard Parse](../standard-parse.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c099-114">For more information, see [Standard Parse](../standard-parse.md).</span></span>  
  
  
