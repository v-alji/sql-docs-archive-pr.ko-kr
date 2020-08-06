---
title: 파워 뷰 보고 속성 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 51205c2d-b6ce-4b92-afd2-58e399a81691
author: minewiskan
ms.author: owend
ms.openlocfilehash: e85d91578e5c3f4b47f56eeb86aa738e37e8f59b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728775"
---
# <a name="power-view-reporting-properties-ssas-tabular"></a><span data-ttu-id="74cf9-102">파워 뷰 보고 속성(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="74cf9-102">Power View Reporting Properties (SSAS Tabular)</span></span>
  [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] <span data-ttu-id="74cf9-103">데이터 분석가, 비즈니스 의사 결정권자 및 정보 근로자와 같은 비즈니스 사용자에게 직관적인 임시 보고 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="74cf9-103">provides intuitive ad-hoc reporting for business users such as data analysts, business decision makers, and information workers.</span></span> <span data-ttu-id="74cf9-104">비즈니스 사용자는 PowerPivot 갤러리에 게시된 PowerPivot 통합 문서를 기반으로 하는 테이블 형식 모델 또는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 를 사용하여 만든 다음 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Analysis Services 인스턴스에 배포된 테이블 형식 모델에서 데이터 뷰를 쉽게 만들고 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74cf9-104">They can easily create and interact with views of data from tabular models based on PowerPivot workbooks published in a PowerPivot Gallery, or tabular models authored by using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and then deployed to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Analysis Services instances.</span></span> [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] <span data-ttu-id="74cf9-105">SharePoint Server 2010 이상에서 실행되는 브라우저 기반 Silverlight 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="74cf9-105">is a browser-based Silverlight application launched from SharePoint Server 2010 or later.</span></span>  
  
 <span data-ttu-id="74cf9-106">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 테이블 형식 모델 프로젝트를 만들 경우 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 보고서에 고유한 특정 보고 속성을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74cf9-106">When authoring tabular model projects in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], you can configure certain reporting properties unique to [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] reports.</span></span> <span data-ttu-id="74cf9-107">이 섹션의 항목에서는 모델을 최적화하여 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]의 보고 환경을 향상시키는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="74cf9-107">Topics in this section describe how to optimize a model to improve the reporting experience in [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="74cf9-108">관련 작업</span><span class="sxs-lookup"><span data-stu-id="74cf9-108">Related Tasks</span></span>  
  
|<span data-ttu-id="74cf9-109">항목</span><span class="sxs-lookup"><span data-stu-id="74cf9-109">Topic</span></span>|<span data-ttu-id="74cf9-110">Description</span><span class="sxs-lookup"><span data-stu-id="74cf9-110">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="74cf9-111">파워 뷰 보고서의 기본 필드 집합 구성&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="74cf9-111">Configure Default Field Set for Power View Reports &#40;SSAS Tabular&#41;</span></span>](power-view-configure-default-field-set-for-reports.md)|<span data-ttu-id="74cf9-112">보고서 필드 목록에서 테이블을 선택할 때 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 보고서 캔버스에 자동으로 추가되는 미리 정의된 열 및 측정값 목록인 기본 필드 집합을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="74cf9-112">Describes how to configure a Default Field Set; a predefined list of columns and measures that are automatically added to a [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] report canvas when the table is selected in the report field list.</span></span>|  
|[<span data-ttu-id="74cf9-113">파워 뷰 보고서의 테이블 동작 속성 구성&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="74cf9-113">Configure Table Behavior Properties for Power View Reports &#40;SSAS Tabular&#41;</span></span>](power-view-configure-table-behavior-properties-for-reports.md)|<span data-ttu-id="74cf9-114">정보 행을 자세히 표시하는 테이블 동작 속성을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="74cf9-114">Describes how to configure table behavior properties that expose detail rows at a more granular level.</span></span> <span data-ttu-id="74cf9-115">테이블 동작 속성을 설정하면 정보 행의 그룹화 동작이 변경되고 바둑판식 배열, 카드 및 차트 레이아웃의 식별 정보의 기본 배치가 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="74cf9-115">Setting table behavior properties changes the grouping behavior of detail rows and produces a better default placement of identifying information in tile, card, and chart layouts.</span></span>|  
  
  
