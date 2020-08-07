---
title: 기본적으로 해제 된 기능 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a9529edf-337e-4fdd-9a13-99cfe96b4fa1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 87752b8760ffc80e80c87ac1132cae36f2f151b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731064"
---
# <a name="features-off-by-default-analysis-services"></a><span data-ttu-id="999cd-102">기본적으로 해제되어 있는 기능(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="999cd-102">Features off by default (Analysis Services)</span></span>
  <span data-ttu-id="999cd-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스는 기본적으로 보안되도록 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="999cd-103">An instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is designed to be secure by default.</span></span> <span data-ttu-id="999cd-104">따라서 보안을 손상시킬 수 있는 기능은 기본적으로 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="999cd-104">Therefore, features that might compromise security are disabled by default.</span></span> <span data-ttu-id="999cd-105">다음 기능은 기본적으로 비활성화된 상태로 설치되며 이러한 기능을 사용하려면 별도로 활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="999cd-105">The following features are installed in a disabled state and must specifically be enabled if you want to use them.</span></span>  
  
## <a name="feature-list"></a><span data-ttu-id="999cd-106">기능 목록</span><span class="sxs-lookup"><span data-stu-id="999cd-106">Feature List</span></span>  
 <span data-ttu-id="999cd-107">다음 기능을 활성화하려면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="999cd-107">To enable the following features, connect to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="999cd-108">인스턴스 이름을 마우스 오른쪽 단추로 클릭하고 **패싯**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="999cd-108">Right-click the instance name and choose **Facets**.</span></span> <span data-ttu-id="999cd-109">또는 다음 섹션에 설명된 것처럼 서버 속성을 통해 이러한 기능을 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="999cd-109">Alternatively, you can enable these features through server properties, as described in the next section.</span></span>  
  
-   <span data-ttu-id="999cd-110">임시 데이터 마이닝(OpenRowset) 쿼리</span><span class="sxs-lookup"><span data-stu-id="999cd-110">Ad Hoc Data Mining (OpenRowset) Queries</span></span>  
  
-   <span data-ttu-id="999cd-111">연결된 개체(대상)</span><span class="sxs-lookup"><span data-stu-id="999cd-111">Linked Objects (To)</span></span>  
  
-   <span data-ttu-id="999cd-112">연결된 개체(원본)</span><span class="sxs-lookup"><span data-stu-id="999cd-112">Linked Objects (From)</span></span>  
  
-   <span data-ttu-id="999cd-113">로컬 연결에서만 수신</span><span class="sxs-lookup"><span data-stu-id="999cd-113">Listen Only On Local Connections</span></span>  
  
-   <span data-ttu-id="999cd-114">사용자 정의 함수</span><span class="sxs-lookup"><span data-stu-id="999cd-114">User Defined Functions</span></span>  
  
## <a name="server-properties"></a><span data-ttu-id="999cd-115">서버 속성</span><span class="sxs-lookup"><span data-stu-id="999cd-115">Server properties</span></span>  
 <span data-ttu-id="999cd-116">기본적으로 해제되어 있는 추가 기능은 서버 속성을 통해 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="999cd-116">Additional features that are off by default can be enabled through server properties.</span></span> <span data-ttu-id="999cd-117">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="999cd-117">Connect to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="999cd-118">인스턴스 이름을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="999cd-118">Right-click the instance name and choose **Properties**.</span></span> <span data-ttu-id="999cd-119">**일반**을 클릭한 다음 **고급 표시** 를 클릭하여 더 많은 속성 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="999cd-119">Click **General**, and then click **Show Advanced** to display a larger property list.</span></span>  
  
-   <span data-ttu-id="999cd-120">임시 데이터 마이닝(OpenRowset) 쿼리</span><span class="sxs-lookup"><span data-stu-id="999cd-120">Ad Hoc Data Mining (OpenRowset) Queries</span></span>  
  
-   <span data-ttu-id="999cd-121">세션 마이닝 모델 허용(데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="999cd-121">Allow Session Mining Models (Data Mining)</span></span>  
  
-   <span data-ttu-id="999cd-122">연결된 개체(대상)</span><span class="sxs-lookup"><span data-stu-id="999cd-122">Linked Objects (To)</span></span>  
  
-   <span data-ttu-id="999cd-123">연결된 개체(원본)</span><span class="sxs-lookup"><span data-stu-id="999cd-123">Linked Objects (From)</span></span>  
  
-   <span data-ttu-id="999cd-124">COM 기반 사용자 정의 함수</span><span class="sxs-lookup"><span data-stu-id="999cd-124">COM based user-defined functions</span></span>  
  
-   <span data-ttu-id="999cd-125">비행 레코더 추적 정의(템플릿)</span><span class="sxs-lookup"><span data-stu-id="999cd-125">Flight Recorder Trace Definitions (templates).</span></span>  
  
-   <span data-ttu-id="999cd-126">쿼리 로깅</span><span class="sxs-lookup"><span data-stu-id="999cd-126">Query logging</span></span>  
  
-   <span data-ttu-id="999cd-127">로컬 연결에서만 수신</span><span class="sxs-lookup"><span data-stu-id="999cd-127">Listen Only On Local Connections</span></span>  
  
-   <span data-ttu-id="999cd-128">이진 XML</span><span class="sxs-lookup"><span data-stu-id="999cd-128">Binary XML</span></span>  
  
-   <span data-ttu-id="999cd-129">압축</span><span class="sxs-lookup"><span data-stu-id="999cd-129">Compression</span></span>  
  
-   <span data-ttu-id="999cd-130">그룹 선호도.</span><span class="sxs-lookup"><span data-stu-id="999cd-130">Group affinity.</span></span> <span data-ttu-id="999cd-131">자세한 내용은 [Thread Pool Properties](../server-properties/thread-pool-properties.md) 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="999cd-131">See [Thread Pool Properties](../server-properties/thread-pool-properties.md) for details.</span></span>  
  
  
