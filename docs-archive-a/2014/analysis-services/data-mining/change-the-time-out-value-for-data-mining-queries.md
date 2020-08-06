---
title: 데이터 마이닝 쿼리에 대 한 제한 시간 값 변경 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- time-out
ms.assetid: f1add4bc-e882-440a-a98b-333cfa274c3e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9dcdcdcbb6e2aef48dd8725f10f38180c73f5f6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652458"
---
# <a name="change-the-time-out-value-for-data-mining-queries"></a><span data-ttu-id="5ba90-102">데이터 마이닝 쿼리에 대한 제한 시간 값 변경</span><span class="sxs-lookup"><span data-stu-id="5ba90-102">Change the Time-out Value for Data Mining Queries</span></span>
  <span data-ttu-id="5ba90-103">리프트 차트를 작성하거나 예측 쿼리를 실행할 때 예측에 필요한 모든 데이터를 생성하는 데 많은 시간이 소요될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ba90-103">When you build a lift chart or execute a prediction query, sometimes it can take a long time to generate all the data required for the prediction.</span></span> <span data-ttu-id="5ba90-104">쿼리가 제한 시간을 초과하지 않도록 하려면 쿼리를 완료할 때까지 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 서버가 기다리는 시간을 제어하는 값을 변경하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ba90-104">To prevent the query from timing out, you can change the value that controls how long the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server waits to complete a query.</span></span>  
  
 <span data-ttu-id="5ba90-105">기본값은 15이지만 모델이 복잡하거나 데이터 원본이 크면 이 시간이 충분하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ba90-105">The default value is 15; however, if your models are complex or the data source is large, this might not be enough.</span></span> <span data-ttu-id="5ba90-106">필요에 따라 처리 시간이 충분하도록 값을 많이 늘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ba90-106">If necessary, you can increase the value significantly, to enable enough time for processing.</span></span> <span data-ttu-id="5ba90-107">예를 들어 **쿼리 제한 시간** 을 600으로 설정하면 최대 10분 동안 쿼리가 계속 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ba90-107">For example, if you set **Query Timeout** to 600, the query could continue to run for up to 10 minutes.</span></span>  
  
 <span data-ttu-id="5ba90-108">예측 쿼리에 대한 자세한 내용은 [데이터 마이닝 쿼리 태스크 및 방법](data-mining-query-tasks-and-how-tos.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5ba90-108">For more information about prediction queries, see [Data Mining Query Tasks and How-tos](data-mining-query-tasks-and-how-tos.md).</span></span>  
  
### <a name="configure-the-time-out-value-for-data-mining-queries"></a><span data-ttu-id="5ba90-109">데이터 마이닝 쿼리에 대한 제한 시간 값 구성</span><span class="sxs-lookup"><span data-stu-id="5ba90-109">Configure the time-out value for data mining queries</span></span>  
  
1.  <span data-ttu-id="5ba90-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 **도구** 메뉴에서 **옵션**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5ba90-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], from the **Tools** menu, selection **Options**.</span></span>  
  
2.  <span data-ttu-id="5ba90-111">**옵션** 창에서 **비즈니스 인텔리전스 디자이너**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5ba90-111">In the **Options** pane, expand **Business Intelligence Designers**.</span></span>  
  
3.  <span data-ttu-id="5ba90-112">**쿼리 제한 시간** 입력란을 클릭하고 시간(초) 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5ba90-112">Click the **Query Timeout** text box, and type a value for the number of seconds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ba90-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5ba90-113">See Also</span></span>  
 <span data-ttu-id="5ba90-114">[데이터 마이닝 쿼리 태스크 및 방법](data-mining-query-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="5ba90-114">[Data Mining Query Tasks and How-tos](data-mining-query-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="5ba90-115">데이터 마이닝 쿼리</span><span class="sxs-lookup"><span data-stu-id="5ba90-115">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
