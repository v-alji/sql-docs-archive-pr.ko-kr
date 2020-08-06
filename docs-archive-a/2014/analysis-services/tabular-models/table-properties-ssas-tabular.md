---
title: 테이블 속성 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.tableprop.f1
ms.assetid: 16d3347b-7e43-4a6b-9956-fdd6ede092e6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9613609c42de8fd3a4aab7aec3208dfe3d31be4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738817"
---
# <a name="table-properties-ssas-tabular"></a><span data-ttu-id="178e8-102">테이블 속성(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="178e8-102">Table Properties (SSAS Tabular)</span></span>
  <span data-ttu-id="178e8-103">이 항목에서는 테이블 형식 모델 테이블 속성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="178e8-103">This topic describes tabular model table properties.</span></span> <span data-ttu-id="178e8-104">여기에서 설명하는 테이블 속성은 원본에서 가져올 열을 지정할 수 있도록 하는 테이블 속성 편집 대화 상자의 테이블 속성과는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="178e8-104">The properties described here are different from those in the Edit Table Properties dialog box, which define which columns from the source are imported.</span></span>  
  
 <span data-ttu-id="178e8-105">이 항목의 섹션:</span><span class="sxs-lookup"><span data-stu-id="178e8-105">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="178e8-106">테이블 속성</span><span class="sxs-lookup"><span data-stu-id="178e8-106">Table Properties</span></span>](#bkmk_properties)  
  
-   [<span data-ttu-id="178e8-107">테이블 속성 설정을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="178e8-107">To configure table property settings</span></span>](#bkmk_config_prop)  
  
##  <a name="table-properties"></a><a name="bkmk_properties"></a><span data-ttu-id="178e8-108">테이블 속성</span><span class="sxs-lookup"><span data-stu-id="178e8-108">Table Properties</span></span>  
 <span data-ttu-id="178e8-109">**기본**</span><span class="sxs-lookup"><span data-stu-id="178e8-109">**Basic**</span></span>  
  
|<span data-ttu-id="178e8-110">속성</span><span class="sxs-lookup"><span data-stu-id="178e8-110">Property</span></span>|<span data-ttu-id="178e8-111">기본 설정</span><span class="sxs-lookup"><span data-stu-id="178e8-111">Default Setting</span></span>|<span data-ttu-id="178e8-112">설명</span><span class="sxs-lookup"><span data-stu-id="178e8-112">Description</span></span>|  
|--------------|---------------------|-----------------|  
|<span data-ttu-id="178e8-113">**연결 이름**</span><span class="sxs-lookup"><span data-stu-id="178e8-113">**Connection Name**</span></span>|\<connection name>|<span data-ttu-id="178e8-114">테이블의 데이터 원본에 대 한 연결의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="178e8-114">The name of the connection to the table's data source.</span></span><br /><br /> <span data-ttu-id="178e8-115">연결을 편집하려면 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="178e8-115">To edit the connection, click the button.</span></span>|  
|<span data-ttu-id="178e8-116">**숨김**</span><span class="sxs-lookup"><span data-stu-id="178e8-116">**Hidden**</span></span>|<span data-ttu-id="178e8-117">거짓</span><span class="sxs-lookup"><span data-stu-id="178e8-117">False</span></span>|<span data-ttu-id="178e8-118">보고 클라이언트 필드 목록에서 테이블이 숨겨지는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="178e8-118">Specifies whether the table is hidden from reporting client field lists.</span></span>|  
|<span data-ttu-id="178e8-119">**파티션**</span><span class="sxs-lookup"><span data-stu-id="178e8-119">**Partitions**</span></span>||<span data-ttu-id="178e8-120">**속성** 창에 표시될 수 없는 테이블의 파티션입니다.</span><span class="sxs-lookup"><span data-stu-id="178e8-120">Partitions for the table cannot be displayed in the **Properties** window.</span></span> <span data-ttu-id="178e8-121">파티션을 보거나 만들거나 편집하려면 단추를 클릭하여 파티션 관리자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="178e8-121">To view, create, or edit partitions, click the button to open the Partition Manager.</span></span>|  
|<span data-ttu-id="178e8-122">**원본 데이터**</span><span class="sxs-lookup"><span data-stu-id="178e8-122">**Source Data**</span></span>||<span data-ttu-id="178e8-123">**속성** 창에 표시될 수 없는 테이블의 원본 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="178e8-123">Source data for the table cannot be displayed in the **Properties** window.</span></span> <span data-ttu-id="178e8-124">원본 데이터를 보거나 편집하려면 단추를 클릭하여 테이블 속성 편집 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="178e8-124">To view or edit the source data, click the button to open the Edit Table Properties dialog box.</span></span>|  
|<span data-ttu-id="178e8-125">**테이블 속성 설명**</span><span class="sxs-lookup"><span data-stu-id="178e8-125">**Table Description**</span></span>||<span data-ttu-id="178e8-126">테이블에 대한 텍스트 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="178e8-126">A text description for the table.</span></span><br /><br /> <span data-ttu-id="178e8-127">[!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)]에서 최종 사용자가 필드 목록의 이 테이블 위에 커서를 두면 설명이 도구 설명으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="178e8-127">In [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)], if an end-user places the cursor over this table in the field list, the description appears as a tooltip.</span></span>|  
|<span data-ttu-id="178e8-128">**Table Name**</span><span class="sxs-lookup"><span data-stu-id="178e8-128">**Table Name**</span></span>|\<friendly name>|<span data-ttu-id="178e8-129">테이블의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="178e8-129">Specifies the table's friendly name.</span></span> <span data-ttu-id="178e8-130">테이블 이름은 테이블 가져오기 마법사를 사용하여 테이블을 가져올 때 지정하거나 테이블을 가져온 후 언제든지 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="178e8-130">The table name can be specified when a table is imported using the Table Import Wizard or at any time after import.</span></span> <span data-ttu-id="178e8-131">모델의 테이블 이름을 관련된 원본 테이블 이름과 다르게 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="178e8-131">The table name in the model can be different from the associated table at the source.</span></span> <span data-ttu-id="178e8-132">테이블 이름은 보고 클라이언트 애플리케이션 필드 목록과 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 모델 데이터베이스에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="178e8-132">The table friendly name appears in the reporting client application field list as well as in the model database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>|  
  
 <span data-ttu-id="178e8-133">**보고 속성**</span><span class="sxs-lookup"><span data-stu-id="178e8-133">**Reporting Properties**</span></span>  
  
 <span data-ttu-id="178e8-134">보고 속성에 대한 자세한 설명 및 구성 정보는 [파워 뷰 보고 속성&#40;SSAS 테이블 형식&#41;](properties-ssas-tabular.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="178e8-134">For detailed descriptions and configuration information for reporting properties, see [Power View Reporting Properties &#40;SSAS Tabular&#41;](properties-ssas-tabular.md).</span></span>  
  
|<span data-ttu-id="178e8-135">속성</span><span class="sxs-lookup"><span data-stu-id="178e8-135">Property</span></span>|<span data-ttu-id="178e8-136">기본 설정</span><span class="sxs-lookup"><span data-stu-id="178e8-136">Default Setting</span></span>|<span data-ttu-id="178e8-137">설명</span><span class="sxs-lookup"><span data-stu-id="178e8-137">Description</span></span>|  
|--------------|---------------------|-----------------|  
|<span data-ttu-id="178e8-138">**기본 필드 집합**</span><span class="sxs-lookup"><span data-stu-id="178e8-138">**Default Field Set**</span></span>|||  
|<span data-ttu-id="178e8-139">테이블 동작</span><span class="sxs-lookup"><span data-stu-id="178e8-139">Table Behavior</span></span>|||  
  
###  <a name="to-configure-table-property-settings"></a><a name="bkmk_config_prop"></a><span data-ttu-id="178e8-140">테이블 속성 설정을 구성 하려면</span><span class="sxs-lookup"><span data-stu-id="178e8-140">To configure table property settings</span></span>  
  
1.  <span data-ttu-id="178e8-141">모델 디자이너의 데이터 뷰에서 테이블(탭)을 클릭하거나 다이어그램 뷰에서 테이블 머리글을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="178e8-141">In the model designer, in Data View, click a table (tab), or, in Diagram View, click a table header.</span></span>  
  
2.  <span data-ttu-id="178e8-142">**속성** 창에서 속성을 클릭한 다음 값을 입력하거나 추가 구성 옵션을 표시하는 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="178e8-142">In the **Properties** window, click on a property, and then type a value or click the button for additional configuration options.</span></span>  
  
  
