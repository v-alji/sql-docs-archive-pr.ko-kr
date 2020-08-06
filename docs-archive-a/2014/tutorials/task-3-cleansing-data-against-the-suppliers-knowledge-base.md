---
title: '작업 3: 공급자 기술 자료에 대 한 데이터 정리 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 647c924a-9b91-4294-8d96-e81416e4e90e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 13201a8b904a5fc5232b9fa860710e4e39cce67a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735584"
---
# <a name="task-3-cleansing-data-against-the-suppliers-knowledge-base"></a><span data-ttu-id="1636a-102">태스크 3: 공급자 기술 자료에 대한 데이터 정리</span><span class="sxs-lookup"><span data-stu-id="1636a-102">Task 3: Cleansing Data against the Suppliers Knowledge Base</span></span>
  <span data-ttu-id="1636a-103">이 작업에서는 컴퓨터 기반 정리 프로세스를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1636a-103">In this task, you run the computer-assisted cleansing process.</span></span> <span data-ttu-id="1636a-104">DQS에서는 지정된 임계값을 기반으로 고급 알고리즘 및 신뢰도 수준을 사용하여 선택한 기술 자료에 대해 데이터를 분석한 다음 데이터를 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="1636a-104">DQS uses advanced algorithms and confidence levels based on the threshold values specified to analyze the data against the selected knowledge base, and then cleanse it.</span></span> <span data-ttu-id="1636a-105">자세한 내용은 [DQS(내부) 기술 자료를 사용하여 데이터 정리](https://msdn.microsoft.com/library/hh213061.aspx) 를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1636a-105">See [Cleansing Data Using DQS (Internal) Knowledge](https://msdn.microsoft.com/library/hh213061.aspx) for more details.</span></span>

1.  <span data-ttu-id="1636a-106">**시작** 을 클릭하여 컴퓨터 기반 정리 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="1636a-106">Click **Start** to start the computer-assisted cleansing process.</span></span>

     <span data-ttu-id="1636a-107">![정리 프로세스의 페이지 정리](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-01.jpg "정리 프로세스의 페이지 정리")</span><span class="sxs-lookup"><span data-stu-id="1636a-107">![Cleanse Page of the Cleansing Process](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-01.jpg "Cleanse Page of the Cleansing Process")</span></span>

2.  <span data-ttu-id="1636a-108">정리 프로세스가 완료 되 면 **프로파일러** 탭에서 **통계** 를 검토 합니다. 원본 통계에는 처리 된 레코드 수, 올바른 것으로 발견 된 레코드 수, DQS에서 수정 하는 레코드 수, DQS에서 변경한 내용이 있는 레코드 수 및 잘못 된 레코드 수가 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1636a-108">When the cleansing process is completed, review **statistics** in the **Profiler** tab. The Source Statistics provide the number of records processed, number of records that are found to be correct, number of records that DQS corrects, number of records that have changes suggested by DQS, and the number of records that are invalid.</span></span> <span data-ttu-id="1636a-109">오른쪽 목록 상자에서는 수정된 값, 제안된 값, 정리 프로세스에 포함된 각 도메인의 값에 대한 완결성(데이터가 제공된 정도) 및 정확성(의도한 목적으로 데이터를 사용할 수 있는 정도)을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1636a-109">In the list box to the right, you can see the corrected values, suggested values, and the completeness (the extent to which the data is present) and accuracy (the extent to which the data can be used for intended purposes) of values for each domain involved in the cleansing process.</span></span>

     <span data-ttu-id="1636a-110">![결과 정리](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-02.jpg "결과 정리")</span><span class="sxs-lookup"><span data-stu-id="1636a-110">![Cleansing Results](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-02.jpg "Cleansing Results")</span></span>

3.  <span data-ttu-id="1636a-111">**다음** 을 클릭하여 **결과 관리 및 보기** 페이지로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="1636a-111">Click **Next** to switch to **Manage and View Results** page.</span></span>

## <a name="next-step"></a><span data-ttu-id="1636a-112">다음 단계</span><span class="sxs-lookup"><span data-stu-id="1636a-112">Next Step</span></span>
 [<span data-ttu-id="1636a-113">태스크 4: 결과 관리 및 보기</span><span class="sxs-lookup"><span data-stu-id="1636a-113">Task 4: Manaing and Viewing Results</span></span>](../../2014/tutorials/task-4-manaing-and-viewing-results.md)


