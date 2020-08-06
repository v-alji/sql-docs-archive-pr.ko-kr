---
title: 테이블 형식 모델링 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 80027288-c203-4667-a3e1-40fa572b4975
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44f358f0f36e84ad903a0a4fcb0203291019e7aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648606"
---
# <a name="tabular-modeling-ssas-tabular"></a><span data-ttu-id="65142-102">테이블 형식 모델링(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="65142-102">Tabular Modeling (SSAS Tabular)</span></span>
  <span data-ttu-id="65142-103">테이블 형식 모델은 Analysis Services의 인 메모리(in-memory) 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="65142-103">Tabular models are in-memory databases in Analysis Services.</span></span> <span data-ttu-id="65142-104">최첨단 비교 알고리즘과 다중 쿼리 프로세서를 사용하는 xVelocity 메모리 내 분석 엔진(VertiPaq)은 Microsoft Excel 및 Microsoft [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]등의 보고 클라이언트 애플리케이션을 통해 테이블 형식 모델 개체와 데이터에 신속하게 액세스할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="65142-104">Using state-of-the-art compression algorithms and multi-threaded query processor, the xVelocity in-memory analytics engine (VertiPaq) delivers fast access to tabular model objects and data by reporting client applications such as Microsoft Excel and Microsoft [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span>  
  
 <span data-ttu-id="65142-105">테이블 형식 모델은 캐시된 모드와 DirectQuery 모드라는 두 가지 모드를 통해 데이터 액세스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="65142-105">Tabular models support data access through two modes: Cached mode and DirectQuery mode.</span></span> <span data-ttu-id="65142-106">캐시된 모드에서는 관계형 데이터베이스, 데이터 피드 및 일반 텍스트 파일을 포함하여 여러 원본의 데이터를 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65142-106">In cached mode, you can integrate data from multiple sources including relational databases, data feeds, and flat text files.</span></span> <span data-ttu-id="65142-107">DirectQuery 모드에서는 인 메모리 모델을 무시하고 클라이언트 애플리케이션에서 (SQL Server 관계형) 원본에 데이터를 직접 쿼리할 수 있도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="65142-107">In DirectQuery mode, you can bypass the in-memory model, allowing client applications to query data directly at the (SQL Server relational) source.</span></span>  
  
 <span data-ttu-id="65142-108">테이블 형식 모델은 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 에서 새로운 테이블 형식 모델 프로젝트 템플릿을 사용하여 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="65142-108">Tabular models are authored in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] using new tabular model project templates.</span></span> <span data-ttu-id="65142-109">여러 원본에서 데이터를 가져온 다음 관계, 계산 열, 측정값, KPI 및 계층을 추가하여 모델을 보강할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65142-109">You can import data from multiple sources, and then enrich the model by adding relationships, calculated columns, measures, KPIs, and hierarchies.</span></span> <span data-ttu-id="65142-110">그런 다음 클라이언트 보고 애플리케이션에서 연결할 수 있는 Analysis Services 인스턴스에 모델을 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65142-110">Models can then be deployed to an instance of Analysis Services where client reporting applications can connect to them.</span></span> <span data-ttu-id="65142-111">배포된 모델은 SQL Server Management Studio에서 다차원 모델처럼 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65142-111">Deployed models can be managed in SQL Server Management Studio just like multidimensional models.</span></span> <span data-ttu-id="65142-112">이러한 모델을 처리 최적화를 위해 분할하거나, 역할 기반 보안을 사용하여 행 수준 보안을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65142-112">They can also be partitioned for optimized processing and secured to the row-level by using role based security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="65142-113">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="65142-113">In This Section</span></span>  
 [<span data-ttu-id="65142-114">테이블 형식 모델 솔루션&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="65142-114">Tabular Model Solutions &#40;SSAS Tabular&#41;</span></span>](../tabular-model-solutions-ssas-tabular.md)  
  
 [<span data-ttu-id="65142-115">테이블 형식 model 데이터베이스&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="65142-115">Tabular Model Databases &#40;SSAS Tabular&#41;</span></span>](tabular-model-databases-ssas-tabular.md)  
  
 [<span data-ttu-id="65142-116">테이블 형식 모델 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="65142-116">Tabular Model Data Access</span></span>](tabular-model-data-access.md)  
  
  
