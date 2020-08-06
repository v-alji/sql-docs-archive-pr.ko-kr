---
title: 테이블 형식 모델 프로그래밍 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 0ceb461e-12c1-44ea-97ac-b99bf308676b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2565ed28a882750ab9b37beadbce698d3a0abb19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743479"
---
# <a name="tabular-model-programming"></a><span data-ttu-id="0e3a2-102">테이블 형식 모델 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="0e3a2-102">Tabular Model Programming</span></span>
  <span data-ttu-id="0e3a2-103">테이블 형식 모델은 분석 및 보고 애플리케이션에서 사용되는 Analysis Services 데이터를 모델링하는 데 관계형 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0e3a2-103">Tabular models use relational constructs to model the Analysis Services data used by analytical and reporting applications.</span></span> <span data-ttu-id="0e3a2-104">이러한 모델은 테이블 형식 모드에 맞게 구성된 Analysis Service 인스턴스에서 실행되며 이때 요청 시 데이터를 집계하고 계산하는 빠른 테이블 검색 및 스토리지용 메모리 내 분석 엔진을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0e3a2-104">These models run on an Analysis Service instance that is configured for tabular mode, using an in-memory analytics engine for storage and fast table scans that aggregate and calculate data as it is requested.</span></span>  
  
 <span data-ttu-id="0e3a2-105">AMO, ADOMD.NET, XMLA 또는 OLE DB에서 사용하는 개체는 테이블 형식 및 다차원 솔루션에 대한 근본적인 프로그래밍 방식이 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="0e3a2-105">Programmatically, the objects you work with in AMO, ADOMD.NET, XMLA, or OLE DB are fundamentally the same for both tabular and multidimensional solutions.</span></span> <span data-ttu-id="0e3a2-106">사용자 지정 BI 솔루션의 요구 사항이 테이블 형식 모델 데이터베이스에서 가장 잘 충족되는 경우 임의의 Analysis Services 클라이언트 라이브러리 및 프로그래밍 인터페이스를 사용하여 Analysis Services 인스턴스의 테이블 형식 모델과 애플리케이션을 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e3a2-106">If the requirements of your custom BI solution are best met by a tabular model database, you can use any of the Analysis Services client libraries and programming interfaces to integrate your application with tabular models on an Analysis Services instance.</span></span> <span data-ttu-id="0e3a2-107">코드에 포함된 MDX 또는 DAX를 사용하여 테이블 형식 모델 데이터를 쿼리하고 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e3a2-107">To query and calculate tabular model data, you can use either embedded MDX or DAX in your code.</span></span>  
  
 <span data-ttu-id="0e3a2-108">이 섹션에서는 프로그래밍 방식으로 테이블 형식 엔터티 및 해당 속성을 사용하여 작업하는 방법에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0e3a2-108">This section provides more information about how you can programmatically work with tabular model entities and their properties.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0e3a2-109">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="0e3a2-109">In This Section</span></span>  
 [<span data-ttu-id="0e3a2-110">비즈니스 인텔리전스에 대한 CSDL 주석&#40;CSDLBI&#41;</span><span class="sxs-lookup"><span data-stu-id="0e3a2-110">CSDL Annotations for Business Intelligence &#40;CSDLBI&#41;</span></span>](/analysis-services/csdlbi/csdl-annotations-for-business-intelligence-csdlbi)  
  
 [<span data-ttu-id="0e3a2-111">테이블 형식 개체 모델 이해</span><span class="sxs-lookup"><span data-stu-id="0e3a2-111">Understanding the Tabular Object Model</span></span>](representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
 [<span data-ttu-id="0e3a2-112">CSDL용 BI 주석에 대한 기술 참조</span><span class="sxs-lookup"><span data-stu-id="0e3a2-112">Technical Reference for BI Annotations to CSDL</span></span>](/analysis-services/csdlbi/technical-reference-for-bi-annotations-to-csdl)  
  
 [<span data-ttu-id="0e3a2-113">IMDEmbedded 인터페이스</span><span class="sxs-lookup"><span data-stu-id="0e3a2-113">IMDEmbedded Interface</span></span>](imdembeddeddata-interface.md)  
  
## <a name="see-also"></a><span data-ttu-id="0e3a2-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0e3a2-114">See Also</span></span>  
 <span data-ttu-id="0e3a2-115">[테이블 형식 모델링 &#40;SSAS 테이블 형식&#41;](../tabular-models/tabular-models-ssas.md) </span><span class="sxs-lookup"><span data-stu-id="0e3a2-115">[Tabular Modeling &#40;SSAS Tabular&#41;](../tabular-models/tabular-models-ssas.md) </span></span>  
 [<span data-ttu-id="0e3a2-116">테이블 형식 모델 디자이너 &#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="0e3a2-116">Tabular Model Designer &#40;SSAS Tabular&#41;</span></span>](../tabular-model-designer-ssas-tabular.md)  
  
  
