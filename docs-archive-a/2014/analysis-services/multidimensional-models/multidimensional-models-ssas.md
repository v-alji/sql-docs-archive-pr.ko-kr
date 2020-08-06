---
title: 다차원 모델링 (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 509df042-fdb3-4e2c-a6b8-86943ce1b0fc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7348a932eccb62f2e00c0b154ca9efc8086fcd1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743571"
---
# <a name="multidimensional-modeling-ssas"></a><span data-ttu-id="4653a-102">다차원 모델링(SSAS)</span><span class="sxs-lookup"><span data-stu-id="4653a-102">Multidimensional Modeling (SSAS)</span></span>
  <span data-ttu-id="4653a-103">Analysis Services 다차원 솔루션은 여러 차원에서 비즈니스 데이터를 분석하기 위해 큐브 구조를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4653a-103">An Analysis Services multidimensional solution uses cube structures for analyzing business data across multiple dimensions.</span></span> <span data-ttu-id="4653a-104">다차원 모드는 Analysis Services의 기본 서버 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="4653a-104">Multidimensional mode is the default server mode of Analysis Services.</span></span> <span data-ttu-id="4653a-105">데이터 확장 요구 사항과 성능의 균형을 맞추기 위한 MOLAP, ROLAP 및 HOLAP 스토리지 모드와 함께 OLAP 데이터의 쿼리 및 계산 엔진을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="4653a-105">It includes a query and calculation engine for OLAP data, with MOLAP, ROLAP, and HOLAP storage modes to balance performance with scalable data requirements.</span></span> <span data-ttu-id="4653a-106">Analysis Services OLAP 엔진은 광범위한 BI 도구와 함께 효과적으로 작동하는 업계 최고의 OLAP 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="4653a-106">The Analysis Services OLAP engine is an industry leading OLAP server that works well with a broad range of BI tools.</span></span> <span data-ttu-id="4653a-107">대부분의 Analysis Services 배포는 기존 OLAP 서버로 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="4653a-107">Most Analysis Services deployments are installed as classic OLAP servers.</span></span>  
  
## <a name="benefits-of-using-multidimensional-solutions"></a><span data-ttu-id="4653a-108">다차원 솔루션 사용 시 이점</span><span class="sxs-lookup"><span data-stu-id="4653a-108">Benefits of Using Multidimensional Solutions</span></span>  
 <span data-ttu-id="4653a-109">Analysis Services 다차원 모델을 작성하는 주된 이유는 비즈니스 데이터에 대한 임시 쿼리를 빠르게 수행하기 위해서입니다.</span><span class="sxs-lookup"><span data-stu-id="4653a-109">The primary reason for building an Analysis Services multidimensional model is to achieve fast performance of ad hoc queries against business data.</span></span> <span data-ttu-id="4653a-110">다차원 모델은 주석을 추가하고 확장하여 복잡한 쿼리 생성을 지원할 수 있는 큐브와 차원으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4653a-110">A multidimensional model is composed of cubes and dimensions that can be annotated and extended to support complex query constructions.</span></span> <span data-ttu-id="4653a-111">BI 개발자는 큐브를 만들어 빠른 응답 시간을 지원하고 비즈니스 보고를 위해 단일 데이터 원본을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4653a-111">BI developers create cubes to support fast response times, and to provide a single data source for business reporting.</span></span> <span data-ttu-id="4653a-112">모든 조직 수준에서 비즈니스 인텔리전스가 점차 중요해지는 경우 분석 데이터의 단일 원본이 있으면 완전히 제거되지 않는 한 불일치가 최소한으로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="4653a-112">Given the growing importance of business intelligence across all levels of an organization, having a single source of analytical data ensures that discrepancies are kept to a minimum, if not eliminated entirely.</span></span>  
  
 <span data-ttu-id="4653a-113">Analysis Services 다차원 데이터베이스를 사용할 경우 또 하나의 중요한 이점은 Excel, Reporting Services 및 PerformancePoint처럼 공통적으로 사용되는 BI 보고 도구는 물론 사용자 지정 애플리케이션 및 타사 솔루션과의 통합이 가능하다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4653a-113">Another important benefit to using Analysis Services multidimensional databases is integration with commonly used BI reporting tools such as Excel, Reporting Services, and PerformancePoint, as well as custom applications and third-party solutions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4653a-114">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="4653a-114">In This Section</span></span>  
 [<span data-ttu-id="4653a-115">다차원 모델 솔루션&#40;SSAS&#41;</span><span class="sxs-lookup"><span data-stu-id="4653a-115">Multidimensional Model Solutions &#40;SSAS&#41;</span></span>](multidimensional-model-solutions-ssas.md)  
  
 [<span data-ttu-id="4653a-116">다차원 model 데이터베이스&#40;SSAS&#41;</span><span class="sxs-lookup"><span data-stu-id="4653a-116">Multidimensional Model Databases &#40;SSAS&#41;</span></span>](multidimensional-model-databases-ssas.md)  
  
 [<span data-ttu-id="4653a-117">다차원 모델 개체 처리</span><span class="sxs-lookup"><span data-stu-id="4653a-117">Multidimensional Model Object Processing</span></span>](processing-a-multidimensional-model-analysis-services.md)  
  
 [<span data-ttu-id="4653a-118">역할 및 권한&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="4653a-118">Roles and Permissions &#40;Analysis Services&#41;</span></span>](roles-and-permissions-analysis-services.md)  
  
 [<span data-ttu-id="4653a-119">다차원 모델용 파워 뷰</span><span class="sxs-lookup"><span data-stu-id="4653a-119">Power View for Multidimensional Models</span></span>](power-view-for-multidimensional-models.md)  
  
 [<span data-ttu-id="4653a-120">다차원 모델 어셈블리 관리</span><span class="sxs-lookup"><span data-stu-id="4653a-120">Multidimensional Model Assemblies Management</span></span>](multidimensional-model-assemblies-management.md)  
  
  
