---
title: 플러그 인 알고리즘 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- third-party algorithms [Analysis Services]
- algorithms [data mining], creating
- plugin algorithms [Analysis Services]
ms.assetid: fe364ddc-576e-42fc-9ced-baa399992f92
author: minewiskan
ms.author: owend
ms.openlocfilehash: ebc5e007dcc6de7fb25d59547e21f1e892100570
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734624"
---
# <a name="plugin-algorithms"></a><span data-ttu-id="af59c-102">플러그 인 알고리즘</span><span class="sxs-lookup"><span data-stu-id="af59c-102">Plugin Algorithms</span></span>
  <span data-ttu-id="af59c-103">에서 제공 하는 알고리즘 외에도 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 다양 한 알고리즘을 사용 하 여 데이터 마이닝을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af59c-103">In addition to the algorithms that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides, there are many other algorithms that you can use for data mining.</span></span> <span data-ttu-id="af59c-104">따라서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서는 타사에서 만든 알고리즘을 "연결"하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="af59c-104">Accordingly, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides a mechanism for "plugging in" algorithms that are created by third parties.</span></span> <span data-ttu-id="af59c-105">특정 표준을 따르는 알고리즘은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 내에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 알고리즘을 사용하듯이 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af59c-105">As long as the algorithms follow certain standards, you can use them within [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] just as you use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms.</span></span> <span data-ttu-id="af59c-106">플러그 인 알고리즘에는에서 제공 하는 알고리즘의 모든 기능이 있습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="af59c-106">Plugin algorithms have all the capabilities of algorithms that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides.</span></span>  
  
 <span data-ttu-id="af59c-107">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 플러그 인 알고리즘과 통신하는 데 사용하는 인터페이스에 대한 전체 설명을 보려면 [CodePlex](https://go.microsoft.com/fwlink/?LinkID=87843) 웹 사이트에 게시된 사용자 지정 알고리즘 및 사용자 지정 모델 뷰어를 만드는 예제를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="af59c-107">For a full description of the interfaces that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses to communicate with plugin algorithms, see the samples for creating a custom algorithm and custom model viewer that are published on [CodePlex](https://go.microsoft.com/fwlink/?LinkID=87843) Web site.</span></span>  
  
## <a name="algorithm-requirements"></a><span data-ttu-id="af59c-108">알고리즘 요구 사항</span><span class="sxs-lookup"><span data-stu-id="af59c-108">Algorithm Requirements</span></span>  
 <span data-ttu-id="af59c-109">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에 알고리즘을 연결하려면 다음 COM 인터페이스를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af59c-109">To plug an algorithm into [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you must implement the following COM interfaces:</span></span>  
  
 `IDMAlgorithm`  
 <span data-ttu-id="af59c-110">모델을 생성하는 알고리즘을 구현하고 결과 모델의 예측 작업을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="af59c-110">Implements an algorithm that produces models, and implements the prediction operations of the resulting models.</span></span>  
  
 `IDMAlgorithmNavigation`  
 <span data-ttu-id="af59c-111">브라우저에서 모델의 내용에 액세스할 수 있도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="af59c-111">Enables browsers to access the content of the models.</span></span>  
  
 `IDMPersist`  
 <span data-ttu-id="af59c-112">알고리즘에서 학습하는 모델을 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 저장 및 로드할 수 있도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="af59c-112">Enables the models that the algorithm trains to be saved and loaded by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 `IDMAlgorithmMetadata`  
 <span data-ttu-id="af59c-113">알고리즘의 기능 및 입력 매개 변수를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="af59c-113">Describes the capabilities and input parameters of the algorithm.</span></span>  
  
 `IDMAlgorithmFactory`  
 <span data-ttu-id="af59c-114">알고리즘 인터페이스를 구현하는 개체의 인스턴스를 만들고 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 알고리즘-메타데이터 인터페이스에 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="af59c-114">Creates instances of the objects that implement the algorithm interface, and provides [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] with access to the algorithm-metadata interface.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="af59c-115">에서는 이러한 COM 인터페이스를 사용하여 플러그 인 알고리즘과 통신합니다.</span><span class="sxs-lookup"><span data-stu-id="af59c-115">uses these COM interfaces to communicate with plugin algorithms.</span></span> <span data-ttu-id="af59c-116">사용하는 플러그 인 알고리즘이 데이터 마이닝용 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB 사양을 지원해야 하지만 사양의 데이터 마이닝 옵션을 모두 지원하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af59c-116">Although plugin algorithms that you use must support the [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB for Data Mining specification, they do not have to support all the data mining options in the specification.</span></span> <span data-ttu-id="af59c-117">[MINING_SERVICES](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset) 스키마 행 집합을 사용하여 알고리즘의 기능을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af59c-117">You can use the [MINING_SERVICES](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset) schema rowset to determine the capabilities of an algorithm.</span></span> <span data-ttu-id="af59c-118">이러한 스키마 행 집합은 각 플러그 인 알고리즘 공급자에 대한 데이터 마이닝 지원 옵션을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="af59c-118">This schema rowset lists the data mining support options for each plugin algorithm provider.</span></span>  
  
 <span data-ttu-id="af59c-119">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 새 알고리즘을 사용하려면 먼저 해당 알고리즘을 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af59c-119">You must register new algorithms before you use them with [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="af59c-120">알고리즘을 등록하려면 알고리즘을 포함할 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스의 .ini 파일에 다음 정보를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="af59c-120">To register an algorithm, include the following information in the .ini file of the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] on which you want to include the algorithms:</span></span>  
  
-   <span data-ttu-id="af59c-121">알고리즘 이름</span><span class="sxs-lookup"><span data-stu-id="af59c-121">The algorithm name</span></span>  
  
-   <span data-ttu-id="af59c-122">ProgID - 선택적 정보이며 플러그 인 알고리즘의 경우에만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="af59c-122">ProgID (this is optional and will only be included for plugin algorithms)</span></span>  
  
-   <span data-ttu-id="af59c-123">알고리즘 설정 여부를 나타내는 플래그</span><span class="sxs-lookup"><span data-stu-id="af59c-123">A flag that indicates whether the algorithm is enabled or not</span></span>  
  
 <span data-ttu-id="af59c-124">다음 코드 예제에서는 새 알고리즘을 등록하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="af59c-124">The following code sample illustrates how to register a new algorithm:</span></span>  
  
 `<ConfigurationSettings>`  
  
 `...`  
  
 `<DataMining>`  
  
 `...`  
  
 `<Algorithms>`  
  
 `...`  
  
 `<Sample_Plugin_Algorithm>`  
  
 `<Enabled>1</Enabled>`  
  
 `<ProgID>Microsoft.DataMining.SamplePlugInAlgorithm.Factory</ProgID>`  
  
 `</Sample_PlugIn_Algorithm>`  
  
 `...`  
  
 `</Algorithms>`  
  
 `...`  
  
 `</DataMining>`  
  
 `...`  
  
 `</ConfigurationSettings>`  
  
## <a name="see-also"></a><span data-ttu-id="af59c-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="af59c-125">See Also</span></span>  
 <span data-ttu-id="af59c-126">[데이터 마이닝 알고리즘 &#40;Analysis Services 데이터 마이닝&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="af59c-126">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="af59c-127">DMSCHEMA_MINING_SERVICES 행 집합</span><span class="sxs-lookup"><span data-stu-id="af59c-127">DMSCHEMA_MINING_SERVICES Rowset</span></span>](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset)  
  
  
