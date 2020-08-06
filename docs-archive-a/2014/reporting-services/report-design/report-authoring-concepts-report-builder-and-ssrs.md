---
title: 보고서 제작 개념(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- concepts
- terminology
ms.assetid: 99311b36-5dc5-4039-ac93-4d2826701327
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d6d6293de87aba33a4cc6ee1ac094fe83041ca55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650725"
---
# <a name="report-authoring-concepts-report-builder-and-ssrs"></a><span data-ttu-id="e90e8-102">보고서 제작 개념(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="e90e8-102">Report Authoring Concepts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="e90e8-103">이 섹션에서는 보고서 작성기 및 보고서 디자이너 설명서에 사용된 주요 개념을 간략하게 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e90e8-103">This section briefly defines key concepts used in the Report Builder and Report Designer documentation.</span></span> <span data-ttu-id="e90e8-104">특정 단어 또는 용어에 대한 정의를 보려면 [용어집&#40;보고서 작성기&#41;](../report-builder/glossary-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e90e8-104">For definitions of specific words or terms, see the [Glossary &#40;Report Builder&#41;](../report-builder/glossary-report-builder.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="in-this-section"></a><span data-ttu-id="e90e8-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="e90e8-105">In This Section</span></span>  
 [<span data-ttu-id="e90e8-106">보고서, 보고서 파트 및 보고서 정의&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e90e8-106">Reports, Report Parts, and Report Definitions &#40;Report Builder and SSRS&#41;</span></span>](reports-report-parts-and-report-definitions-report-builder-and-ssrs.md)  
 <span data-ttu-id="e90e8-107">사용자에게 표시되는 초기 정의, 게시된 보고서 및 표시된 보고서를 비롯한 여러 상태의 보고서를 설명하는 데 사용되는 다양한 용어에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e90e8-107">Describes the variety of terms used to describe a report in different states, including the initial definition, the published report, and the viewed report as it appears to the user.</span></span>  
  
 [<span data-ttu-id="e90e8-108">포함된 데이터 연결 및 공유 데이터 연결 또는 데이터 원본&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e90e8-108">Embedded and Shared Data Connections or Data Sources &#40;Report Builder and SSRS&#41;</span></span>](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)  
 <span data-ttu-id="e90e8-109">보고서, 보고서 모델 및 데이터 기반 구독에 사용되는 데이터 원본에 대한 연결을 정의하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e90e8-109">Describes the ways to define connections to the data sources used in reports, report models, and data-driven subscriptions.</span></span>  
  
 [<span data-ttu-id="e90e8-110">포함된 데이터 세트 및 공유 데이터 세트&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e90e8-110">Embedded and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](../report-data/embedded-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="e90e8-111">포함된 데이터 세트를 만들고, 저장하고, 관리하는 방법과 공유 데이터 세트를 만들고, 저장하고, 관리하는 방법의 차이점에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e90e8-111">Explains the differences in creating, storing, and managing embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="e90e8-112">데이터 영역 및 지도&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e90e8-112">Data Regions and Maps &#40;Report Builder and SSRS&#41;</span></span>](maps-report-builder-and-ssrs.md)  
 <span data-ttu-id="e90e8-113">보고서 레이아웃에 추가할 수 있는 데이터 영역 유형에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e90e8-113">Describes the types of data regions that can be added to a report layout.</span></span> <span data-ttu-id="e90e8-114">데이터 영역에 따라 보고서 모양이 테이블 형식, 행렬, 목록 또는 차트 중 하나로 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e90e8-114">Data regions determine the appearance of a report: tabular, matrix, list, or chart.</span></span>  
  
 [<span data-ttu-id="e90e8-115">보고서 매개 변수 개념 &#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e90e8-115">Report Parameters Concept &#40;Report Builder and SSRS&#41;</span></span>](report-parameters-concepts-report-builder-and-ssrs.md)  
 <span data-ttu-id="e90e8-116">보고서 매개 변수를 정의하고 사용하는 방법 및 보고서 서버의 보고서 정의를 통해 보고서 매개 변수를 별도로 관리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e90e8-116">Describes the ways to define and use report parameters, and how they are independently managed from the report definition on the report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e90e8-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e90e8-117">See Also</span></span>  
 [<span data-ttu-id="e90e8-118">SQL Server 2014의 보고서 작성기</span><span class="sxs-lookup"><span data-stu-id="e90e8-118">Report Builder in SQL Server 2014</span></span>](../report-builder/report-builder-in-sql-server-2016.md)  
  
  
